<a id="core-the-shared-production-tools"></a>
# core/: 共享生产工具

`core/` 和 `tools/` 的命令参考。这些部分如何组合在一起在[`TECHNIQUE.md`](../TECHNIQUE.md)中。从库根运行命令（技能模式下为`$LIB`）； Python 是该库的 `.venv/bin/python`。 `<demo>` 是带有 `index.html` 的任何文件夹。

<a id="install"></a>
## 安装

|命令|它的作用|
|---|---|
|`sh plugin/skills/lemo-opuscar/scripts/setup.sh`|查找、克隆或更新库；打印 `LIB=<path>`|
|`… setup.sh deps`|核心层：npm 包、无头浏览器、来自 `requirements.txt` 的 `.venv`|
|`… setup.sh deps voice`|添加了 `requirements-voice.txt`（kokoro-onnx、edge-tts、faster-whisper）和 Kokoro 模型|
|`… setup.sh deps music`|添加 `requirements-music.txt`（numba，对于 `pluck.py`；`sampler.py` 仅需要核心）|
|`… setup.sh demo <slug>`|添加一种风格的示范源和海报（用于阅读，而不是渲染）|
|`sh tools/fetch.sh voice` \|`hdri` \|`instruments <lib>` \|`instruments all`|Kokoro 模型·HDRI·a 采样音色库（`freepats`、`karoryfer`、`salamander`、`vcsl`、`vsco2ce`）|

尺寸为 TECHNIQUE.md §1。

<a id="the-page-contract"></a>
## 页面合约

|全球的|必需的|意义|
|---|---|---|
|`window.READY = true`|是的|加载字体和图像后设置|
|`window.render(t)`|是的|在第二个`t`处绘制框架；确定性的|
|`window.DUR`|视频、事件、阅读检查|影片长度（以秒为单位）|
|`window.EV = [{t, type, …}]`|不|声音和提示事件，由 `events.mjs` 导出|
|`window.TEXTS(t)`|读检查|`[{id, text, x0, y0, x1, y1}]`：`t` 上可见的每个屏幕文本，其框以像素为单位。从第一个可见帧报告元素的 **满的** 文本（仅报告键入字母的打字机未通过检查）|

设备比例 1 时的视口为 1920×1080，或 `--size WxH`。 `--q 'k=v&…'` 到达的页面为 `location.search`。页面错误或脚本、模块或页面上的 HTTP 错误会停止该工具（出口 1）。其他丢失的文件（获取、图像、字体）打印 `optional file missing: <URL>` 并且该工具继续运行。对于 `window.READY`，这些工具最多等待 180 秒。

<a id="render"></a>
## 使成为

|命令|它的作用|
|---|---|
|`node core/render/still.mjs <demo> <t> [<t> …] [--range a:b:step] [--prefix t_] [--out dir]`|查看 JPEG 格式的静止图像（默认 `<demo>/stills/t_<t>.jpg`）|
|`node core/render/video.mjs <demo> [--fps 24] [--workers 3] [--out <demo>/out/video.mp4]`|视频的每一帧；一次渲染最多 6 个工作人员。每个并行版本都需要自己的`--out`|
|`node core/render/events.mjs <demo> [--out <file>]`|导出 `{dur, ev}` 到 `<demo>/events.json`|
|`node core/render/readcheck.mjs <demo> [--step 0.04] [--latin-cps 15] [--cjk-cps 4.5] [--pad 1.5] [--min 1.5]`|阅读时间检查（下）|
|`.venv/bin/python core/render/sheet.py out.jpg img… [--cols 4] [--w 480]`|联系表|
|`.venv/bin/python core/render/srt.py cues.json out.srt`|字幕来自 `[{t0, t1, text}]`|
|`sh core/render/mux.sh video.mp4 mix.wav out.mp4 [fps=24] [grain=2]`|复用器和主控器（下）|

所有四个页面工具均采用 `--size WxH`（默认 `1920x1080`，偶数）和 `--q 'k=v'`。

**读检查** 在每一步都会向页面询问 `window.TEXTS(t)`。每个文本必须完全保持在框架内，保持不变，至少 CJK 字符 ÷ 4.5 + 其他非空格字符 ÷ 15 + 1.5 秒，且不得少于 `--min`。同一`id`下的新`text`开始了新的作品。字幕是通过他们的`.srt`检查的，不是这里。

**复用器** 运行两通道 `loudnorm` 至 −14 LUFS / 真实峰值 −1.2 dB，添加影片颗粒（`grain` 0 = 无）并打印测量的响度。静默音频保持在其水平并带有警告；短音频被填充，长音频在画面末尾被剪切；丢失、损坏或截断的音频将被拒绝。它永远不会留下部分文件。

<a id="audio"></a>
## 声音的

|命令|它的作用|
|---|---|
|`.venv/bin/python core/tts/tts.py lines.json out_dir`|心，离线。 `lines.json` = `[{id, text, voice?, speed?, lang?}]`（默认为 `af_bella`、`0.92`、`en-us`；中文：`"lang": "cmn"`，`zf_*`/`zm_*` 语音）。写入 `<id>.wav`（24 kHz，已调整）和 `dur.json`。需要 160 字节以下的库路径 (espeak-ng)；它检查|
|`.venv/bin/python core/tts/tts_zh.py lines.json out_dir [--voice zh-CN-XiaoxiaoNeural] [--rate +0%] [--pitch +0Hz]`|edge-tts（微软），在线；与 `tts.py` 相同的输出。每行：`voice`、`rate`、`pitch`、`say`（与 `text` 不同时所说的内容）。缓存在 `out_dir/.cache/` 中。声音：`.venv/bin/python -m edge_tts --list-voices`|
|`.venv/bin/python core/tts/asr_check.py lines.json voices_dir [--lang en\|zh\|auto] [--threshold 0.92] [--model base]`|每个 `<id>.wav` 的语音到文本检查；写入 `words.json`（字时间戳）。英语必须逐字匹配（0-999 与他们的单词相同）；中文、日文、韩文字符相似度比较≥`--threshold`。一行中的 `asr` 字段会覆盖预期的文本（名称、小数、时间：像 Whisper 那样写入）|
|`core/audio/sfx.py`|程序拟音和混合助手：滤波器、包络、`click`、`whoosh`、`thump`、`ding`…、`compress`、`limit`、`add(buf, sound, at, gain, pan)`|
|`core/audio/sampler.py`、`core/audio/pluck.py`|采样乐器和拨弦建模（[`audio/INSTRUMENTS.md`](audio/INSTRUMENTS.md)）。错误中使用 `fetch.sh instruments <lib>` 命令命名了缺失的库。 `credits(names)` 写入 CREDITS 行|

<a id="picture-helpers"></a>
## 图片助手

|文件|它是什么|
|---|---|
|`core/lib.js`|种子随机 `mulberry`、`hash`、`vnoise`、`clamp(x,a,b)`、`lerp(a,b,t)`、`seg(t,a,b)`（a 和 b 之间 0→1）、缓动在 0–1 上(`ss(t)`、`eio(t)`、`eo(t)`、`ei(t)`、`back(t,s)`、`spring(t,k,z)`)、`monotone`/`track` 插值、包络`env`|
|`core/three/post.js`|three.js 后：物理景深、GTAO、光晕、颜色等级、2× 超级采样|
|`core/post/crt.js`|WebGL2 CRT / VHS 通过 2D 画布|
|`core/fonts/`|Fredoka、Lilita One、IM Fell English、ZCOOL KuaiLe (OFL、[`fonts/OFL.md`](fonts/OFL.md)) 作为子集； ZCOOL 仅容纳约 200 个字符|
|`core/assets/polyhaven/`|CC0 HDRI 和型号 (`SOURCES.md`)|

<a id="environment-variables"></a>
## 环境变量

|多变的|意义|
|---|---|
|`LEMO_OPUSCAR_HOME`|`setup.sh` 保存库的位置（默认 `~/lemo-opuscar`）|
|`PLAYWRIGHT_CHROME`|Chrome / headless-shell 可执行文件而不是 Playwright 的|
|`LEMO_ANGLE`|WebGL 后端（macOS 上默认为 `metal`；`default` 不通过）|
|`RENDER_SLOTS`|选修的;限制跨进程的并发完整渲染|
|`LEMO_COLOR=bt709`|`mux.sh` 写入有限范围 BT.709，而不是默认的全范围输出|
|`WHISPER_MODEL`|`asr_check.py` 的 Whisper 型号名称或本地文件夹（与 `--model` 相同；英文默认 `base.en`，中文默认 `small`，其他默认 `base`）|
|`HF_ENDPOINT`|Whisper 的拥抱面镜下载|

<a id="exit-codes"></a>
## 退出代码

|工具|0|1|2|
|---|---|---|---|
|渲染工具|完毕|页面错误、缺少所需文件、ffmpeg 失败|用法，没有 `index.html`、`--out` 已被写入|
|`readcheck.mjs`|所有文本足够长|有些太短或永远不完全可见|无法检查（无 `TEXTS`）|
|`mux.sh`|影片写|任何失败|–|
|`tts.py`、`srt.py`|完毕|输入错误、模型丢失、路径太长|用法|
|`tts_zh.py`|完毕|输入错误|网络不可达|
|`asr_check.py`|所有线路均通过|不匹配|模型加载失败|
