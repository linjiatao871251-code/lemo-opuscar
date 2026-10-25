<a id="technique-how-the-films-are-built"></a>
# 技术：影片的构建方式

这里的每个影片都是由代码制成的：没有视频生成，没有库存素材。本页介绍了制作流程，可以使用我们在 `core/` 或您自己的堆栈中的工具进行重现。与 [`DIRECTOR.md`](DIRECTOR.md) 和一个 `styles/<slug>/STYLE.md` 配对。每个命令和标志都在[`core/README.md`](core/README.md)中。

```
timeline (single source of truth)
   ├─► picture:  web page with render(t) ──► headless Chrome, frame by frame ──► video.mp4
   ├─► voice:    TTS per line ──► speech-to-text check ──► word timings
   ├─► music:    score from the same timeline (samples + synthesis) ──► stems
   ├─► sound:    procedural foley at event times
   └─► subtitles: .srt + burned-in captions
mix (duck, compress, balance) ──► mux with ffmpeg, two-pass loudnorm −14 LUFS ──► film.mp4
```

<a id="1-requirements-and-install"></a>
## 1. 要求及安装

用户安装的系统工具：**Node 20+**、**ffmpeg**、**Python 3.11+**或[uv](https://docs.astral.sh/uv/)。在 macOS（Apple 芯片）上开发； Linux 应该可以工作；在 Windows 上使用 WSL。 3D 和着色器密集型风格需要 GPU。

其他所有内容都从库根目录（技能模式下为 `$LIB`）开始分层安装。仅当影片需要时才安装层：

|命令|添加|尺寸|
|---|---|---|
|`sh plugin/skills/lemo-opuscar/scripts/setup.sh deps`|核心：npm 包、无头浏览器、Python `.venv`（numpy、scipy、soundfile、soxr、pillow）：渲染、合成声音、mux|〜350MB|
|`… setup.sh deps voice`|Kokoro + model（英语，离线），edge-tts（中文，在线），faster-whisper（语音检查）|约 0.55 GB + 首次检查时有一个 Whisper 模型（英语约 145 MB，中文约 480 MB）|
|`… setup.sh deps music`|numba，用于拨弦 (`pluck.py`)；采样器本身只需要核心|〜140MB|
|`sh tools/fetch.sh instruments <lib>`|a 采样音色库：`freepats`、`karoryfer`、`salamander`、`vcsl`、`vsco2ce` 或 `all`|每个 70–400 MB|
|`sh tools/fetch.sh hdri`|3D 风格的 HDRI|12MB|

有些风格需要自己的软件包（LiDAR 读取器、滑动扫描解码器、CAD 导入器）；风格的 `STYLE.md` 列出了它们。它们是软件包，而不是系统工具：您自己将它们安装到项目文件夹中的私有 venv 或 `node_modules` 中，而不是安装到 `$LIB/.venv` 中。

合成的配乐不需要大量下载； `sampler.py` 指定仪器丢失时要获取的库。一个包装在打开包装时需要大约两倍的空间。下载来自 npm、PyPI、GitHub Releases 和 Hugging Face（`HF_ENDPOINT` 设置镜像）。

<a id="2-the-picture-is-a-function-of-time"></a>
## 2. 图片是时间的函数

每个影片都是一个带有 `index.html`（命令中的 `<demo>`）的文件夹，该文件夹公开：

```js
window.DUR = 54.2;                 // seconds
window.render = (t) => { ... };    // draw the frame at time t, deterministic
window.READY = true;               // set once fonts and images are loaded
window.EV = [{t, type, ...}];      // optional: sound / cue events for the mixer
window.TEXTS = (t) => [{id, text, x0, y0, x1, y1}];   // optional: every text visible at t, for readcheck
```

**路径：**页面到达具有绝对URL的库文件（`/core/lib.js`、`/node_modules/three/build/three.module.js`）；脚本和 `build.sh` 使用 `$LIB`。从来没有 `../..`。

可以在两种模式下工作的 `build.sh`（在技能模式下，将 `LIB=<path setup.sh printed>` 放在顶部）：

```sh
#!/bin/sh
set -e
HERE=$(cd "$(dirname "$0")" && pwd)
LIB=${LIB:-$(cd "$HERE/../.." && pwd)}          # clone mode: <repo>/films/<name>/
export LIB
[ -f "$LIB/core/render/video.mjs" ] || { echo "set LIB to the library folder"; exit 1; }
cd "$LIB"
node core/render/events.mjs "$HERE"
node core/render/video.mjs "$HERE" --fps 24 --out "$HERE/out/video.mp4"
"$LIB/.venv/bin/python" "$HERE/mix.py"                               # score, foley, voice → out/mix.wav
sh core/render/mux.sh "$HERE/out/video.mp4" "$HERE/out/mix.wav" "$HERE/<name>.mp4" 24
```

保持其可靠性的规则：

- **确定性的。** 没有 `Date.now()`，没有没有种子的 `Math.random()`（`core/lib.js` 有 `mulberry` 和 `hash`），没有从前一帧携带的状态。任何帧都可以由任何工作人员以任何顺序单独渲染。
- **Canvas 2D**适用于大多数 2D 风格；**three.js**用于 3D (§9)；**WebGL2** 用于后期通道的着色器（影片损坏、CRT、墨水重绘）。
- **在风格需要的地方进行动画处理**（12 fps 步进，用于定格动画、像素或 cel 外观），但保持摄影机和光线每帧都平滑。阶梯式摄影机读作滞后。
- **一个世界 → 屏幕功能。** 任何跟随主体的效果（光圈、变焦、聚光灯）都会通过它。切勿手动输入屏幕坐标。
- **为您渲染的帧绘制。** 默认为1920×1080；对于其他尺寸，将 `--size WxH`（例如 `1080x1920`）传递给每个渲染工具，并从 `innerWidth` × `innerHeight` 布局页面。

捕获（`core/render/`）：

```sh
node core/render/still.mjs <demo> 1.5 12 --range 0:50:2   # review stills; exits on page errors
node core/render/video.mjs <demo> --fps 24 --workers 3     # all frames → <demo>/out/video.mp4
node core/render/events.mjs <demo>                         # export DUR + EV → events.json
node core/render/readcheck.mjs <demo>                      # every on-screen text stays long enough to read
```

要使用其他内容呈现第二个版本，请将其传递到页面并为其提供自己的输出：`--q 'content=content_alt.json' --out …/alt.mp4`（与 `events.mjs` 相同）。

捕获速度很快，因为**JPEG 屏幕截图**, **每个工人一个浏览器**和**ffmpeg中添加的grain**：页面中绘制的颗粒使每一帧都不可压缩且缓慢。

<a id="3-one-timeline-drives-everything"></a>
## 3. 一条时间线驱动一切

将章节、节奏、节拍和击中点保存在一个文件中 (`timeline.js`)。将其导出为 JSON 并让配乐、混音器、字幕和检查读取相同的数字：

```js
export const SECS = [{ id: 'chase', t: 12.0, bpm: 144, beats: 12 }, ...];
export const HIT  = { pratfall: ['chase', 6], ... };   // section + beat
```

一个小脚本（`cuecheck.py`，在几个示范中的 `styles/<slug>/demo/tools/` 中）将每个视觉效果与其应该出现的音乐提示进行比较。目标是 0 毫秒。

<a id="4-voice"></a>
## 4. 语音

- **TTS 仅是默认值。** 如果用户带来录音或命名语音，请使用它。否则：
  - **英语**：[Kokoro](https://github.com/thewh1teagle/kokoro-onnx)，本地，许多声音（未知的 `voice` 名字使 `tts.py` 打印完整列表；`af_` / `am_` 是美国人， `bf_` / `bm_` 英国；为这个影片配上旁白，而不是示范的）。 `core/tts/tts.py lines.json out/` 每行写入一个 WAV 和一个持续时间文件。它的中文语音（`"lang": "cmn"`）可以离线工作，但听起来很普通。
  - **中国人**：`core/tts/tts_zh.py lines.json out/` 使用 [edge-tts](https://github.com/rany2/edge-tts) 和 Microsoft 的神经语音（`zh-CN-XiaoxiaoNeural`、`zh-CN-YunxiNeural`…），具有与 `tts.py` 相同的输出、每行速率和沉默渐渐平息。 **需要网络连接。**
- 在 TTS 文本中拼写出数字，并将其以数字形式写在字幕中。
- **检查每一行**：`core/tts/asr_check.py`用faster-whisper转录每个WAV并与脚本进行比较（`--lang zh`：逐个字符）；重新生成，直到退出 0。 在短中文行中听错字符是正常的：听，如果正确，则将模型听到的内容放入该行的 `asr` 字段中。它还会写入用于放置台词和字幕的单词时间戳。
- **混合前**：TTS具有较高的峰均比。先压缩声音，然后用RMS进行平衡：声音比音乐高出大约10 dB。

<a id="5-music"></a>
## 5. 音乐

在风格声音体系的乐器中，从音画节拍对照表编写原始配乐；没有通用的钢琴和弦乐。

- **样品**：`core/audio/sampler.py` 可以演奏来自免费库的真实乐器（VSCO 2 CE、VCSL、FreePats、Karoryfer、Salamander 大钢琴；`core/audio/INSTRUMENTS.md` 中的列表和许可证）。 Write the 配乐 as events `(time, instrument, pitch, duration, velocity, pan)`.长音符可以无缝延伸，循环赛可以避免机枪效应。
- **弹拨和民谣弦乐**（古琴、琵琶、三味线、班卓琴……）：`core/audio/pluck.py`，物理造型（Karplus-Strong），带有拉弦和颤音。
- **合成** 与 numpy 用于芯片曲调、无人机和效果；无需下载。
- **平衡低频。** 合成乐谱很快就会变得重低音。测量混合后每个频带的能量；相对于其余部分，将 20–120 Hz 保持在 −3 dB 左右，跳过 MIDI 48 以下的打击垫音符，并为低音提供一些第二和第三谐波，以便它在小扬声器上说话。

<a id="6-sound-effects-and-mix"></a>
## 6.音效与混音

- `core/audio/sfx.py` 通过滤波器、包络和 `add(buffer, sound, at, gain, pan)` 以程序方式合成拟音（点击、嗖嗖、重击、叮当、纸张、噪音床……）。从 `window.EV` 驱动它，因此每个声音都准确地位于其框架上。
- **掌握**：`sh core/render/mux.sh video.mp4 mix.wav out.mp4 24 [grain]` 复用器，运行两遍响度范数至 −14 LUFS，具有真实峰值限制，在 ffmpeg 中添加颗粒并打印测量的响度；任何失败时它都会以非零值退出。在浅色背景上使用较少的颗粒；对于像素和矢量风格，没有。
- 影片有颗粒的烤进图片压缩严重；使用 `-tune grain` 和更高的 CRF 重新编码。

<a id="7-subtitles"></a>
## 7. 字幕

- 使用 `.srt` 导出 `core/render/srt.py cues.json out.srt`（提示 = `[{t0, t1, text}]`），并将风格化的标题刻录到页面本身中：标题设计是风格的一部分。
- 时序规则参见 DIRECTOR.md §7。

<a id="8-review-loop"></a>
## 8. 审查循环

1. 接触表：每 1-2 秒一帧，带有 `still.mjs --range`，平铺为 `core/render/sheet.py`。至少两次完整通过。
2. 每个关键动作的帧间隔为 0.2 秒：交接、摔倒、击打。
3. 在最终文件上：`ffmpeg -af ebur128`（响度）、`blackdetect`（空白帧），如果最终混音有声音，请再次对它低语。
4. 全速、有声地观看一次。

<a id="9-3d-notes"></a>
## 9. 3D笔记

- three.js r170 通过 GPU 上的 WebGL2 进行无头渲染；来自 `core/three/post.js` 的物理景深和 GTAO，以 2 倍渲染并下采样。
- 照明：柔和的区域灯加上低强度的 Poly Haven HDRI 比明亮的环境光看起来更“真实”。
- `core/three/post.js` 是为透视图摄影机编写的。对于正交摄影机，在其深度通道中将 `perspectiveDepthToViewZ` 替换为 `orthographicDepthToViewZ`，否则景深会悄然中断。

<a id="10-characters-drawn-in-code"></a>
## 10. 代码中绘制的字符

- 2.5D 骨骼绑定结构（每帧解析的躯干、头部、四肢）足以制作哑剧。
- 肩部旋转顺序为先外展，后屈曲；相反的顺序是举起手臂交叉成X。
- 当手臂抬起时，让肩胛带上升并向前移动，不要勾画出手臂与躯干重叠的部分：这条线使关节看起来像木偶接缝。

<a id="11-assets-credits-and-fonts"></a>
## 11. 资源、制作人员和字体

仅 CC0、CC BY 或 OFL 材料，每种材料均列在影片的 `CREDITS` 中及其来源和许可证； `core/audio/sampler.py credits(names)` 为您使用的仪器写入行。公共领域作品计为 CC0； “没有已知的限制”则不然。仅在您向用户指定许可证及其条款（归属、类似共享）并且他们同意后，才能使用其他开放许可证（ODbL、CC BY-SA、开放硬件许可证）下的数据或图像。用户自己的材料就可以了。

陈述事实的影片（证据影片风格）在项目文件夹中保留 `FACTS.md`：每个声明及其源 URL 和引用的措辞，或产生它的测量。

字体：Google Fonts (OFL)，在项目中自行托管。 `STYLE.md` 名称的字体不在库中；将它们（`https://github.com/google/fonts/tree/main/ofl/<family>`）下载到项目的`fonts/`中。 `core/fonts/` 包含一些拉丁显示字体和一个中文显示字体，只有大约 200 个字形，不足以运行中文文本。对于中文，将 CJK 字体子集化为您使用的字符：带有 `&text=` 的 Google Fonts CSS API 仅返回这些字形 (`https://fonts.googleapis.com/css2?family=Noto+Sans+SC:wght@700&text=<URL-encoded characters>`)。将其指向的字体文件下载到项目的`fonts/`中，并用`@font-face`加载；不要在渲染时链接 Google Fonts。

<a id="12-where-to-look-in-our-demos"></a>
## 12. 在我们的示范中哪里可以看到

|如果您需要……|看看|
|---|---|
|2D 角色动画和口型同步|`styles/scifi-toon/`、`styles/cel-anime-80s/`|
|具有提示检查功能的时间线驱动的配乐|`styles/microgame/`、`styles/silent-film/`|
|图像到墨水重画和影片损坏后通道|`styles/silent-film/demo/engine/`|
|刷式或冲程引擎|`styles/watercolor/`、`styles/ink-wash/`、`styles/impasto/`|
|具有景深和真实材质的 3D|`styles/brick-toy/`、`styles/paper-popup/`|
|CRT 或 VHS 外观|`core/post/crt.js`、`styles/ascii-crt/`、`styles/backrooms/`|

每种风格的 `DEMO.md` 都说明了其示范的构建方式。只有在你的创作方案存在之后才打开它和代码，学习技术，永远不要重建我们的影片（`demo/tools/`中的剪辑与纪实风格的素材工具首先：AGENTS.md，“创作方案第一”）。在技​​能模式下，通过`sh <skill folder>/scripts/setup.sh demo <slug>`获取源。复制的示范代码通常会以 `../..` 的形式到达库：将其替换为 `$LIB` 或绝对 URL。
