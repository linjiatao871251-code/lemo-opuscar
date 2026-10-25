<a id="watercolor-brush--our-demo"></a>
# 水彩笔 — 我们的示范

众多例子中的一个。请勿重复使用其故事、弧线、镜头、道具或时间安排。

示范：*Follow the Rain*（113.6 s，1920×1080，60 fps）·`watercolor.mp4`·来源在[`demo/`](demo/)·引擎：Canvas2D行程引擎（`engine.js`） `mk`/`drawS`、可变宽度功能区 + 虚线刷毛轨迹)、程序植物生成器、每植物精灵缓存、无头 Chrome 帧捕获。


示范是一本博物学家的田野日记：沿着降雨梯度、手写笔记和安静的降雨量计，在澳大利亚风景中长长地横向漫步，然后拉出一张穿越深邃时间的彩绘地图。

<a id="story--structure"></a>
## 故事与结构

A 影片看起来就像一本手绘的野外日记画在你面前。所有东西都放在一张温暖的纤维纸上（`#f1e9da`）。每一个物体——三齿稃丘、橡胶树、袋鼠、云、地平线、海岸线——都是由**单独的笔触**：以部分不透明度放置的可变宽度丝带，加上 3-9 的薄层**鬃毛轨道**分成破折号（干刷*飞白*）。笔画重叠并在交叉处变暗，就像真正的透明颜料一样。没有什么东西有矢量轮廓；树干上较暗的边缘描边（`edgeOf`）是唯一的“线”。

事物**在进入画面时将自己画在**中：一笔一笔地画，先是树干，然后是树枝，最后是叶子。完成后，植物会被缓存为精灵并且只会摇摆。景观是摄影机走过的一个长长的绘画世界，位于水彩晕染和植物的四个视差层中，而 **annotation 层**（带有钢笔引导线的手写警告标签、单一类型的降雨量计、鸬鹚 Garamond 的生物群系标题）解释了我们所看到的内容。 《影片》的结尾是用纸色的雾气冲走风景，将整个大陆绘制成一幅彩绘地图。

语气：平静、好奇、精确。这是一部纪录片，而不是童话故事：数字是真实的，标签是拉丁名称，调色板遵循数据。

示范如何使用表现媒介：

|原生电源|故事运用|
|---|---|
|**A 沿一个梯度行走**|将一个可测量的量映射到水平距离并对其进行遍历：降雨量 (示范)、山上的海拔、礁壁下的深度、距市中心的距离、从赤道到极点的纬度、沿河的时间。 摄影机运动 *是*参数。|
|**绘画展示**|每个新区域在到达时都被逐一绘制——观众会看到一种新的生活被一笔一笔地出现。使用`burst`使整个区域立即爆发为高潮区域（雨林）。|
|**区域调色板**|颜色携带数据：红赭色沙漠→鼠尾草→稻草林地→蓝灰色湿森林→深绿色雨林。天空、地面、山丘和远处的树木都按区域融合在一起。|
|**标本+备注**|每个区域一个英雄样本，手工标记有引导线（`spinifex · Triodia`、`mountain ash · Eucalyptus regnans`）。每个区域都有一只小动物赋予生命和规模（袋鼠、虎皮鹦鹉、考拉、食火鸡、一个小型人类）。|
|**每个区域一个事件**|每个区域都会有一个小型示范事件：雨水顺着穆加树枝流到根部、火锋和表皮再生、倾斜测量一棵 100 m 的树、雨林的分层图。|
|**拉出至地图**|走完后，水彩晕染把风景带走并画出地图；在上面画上“我们的脚步”。然后，地图可以在 **时间**（50 Ma → 今天）内移动，从而将空间漫步变成历史漫步。|

**故事形状（在示范中得到证明）：**冷纸→地平线刷入→朱红色的太阳像印章一样“印记”→标题→用刷子边缘擦拭显示的风景→5个区域（每个区域约10-18秒），带有上升的仪表→雾水彩晕染一切都回到纸上→海岸线绘制→地图填充→“我们的行走”箭头→倒回5000万年前（全绿色）→漂流并干燥回到今天（干燥的心，绿色边缘）→褪色地图上的结束标题+制作人员名单。

调整主题：选择渐变；列出 4-6 个区域，每个边界都有实际值；为每个区域提供一个调色板、一个英雄标本、一只小动物和一个事件；以地图或图表结束步行（在空间上，然后在时间上）。

<a id="shots"></a>
## 镜头

|打|摄影机|
|---|---|
|标题（0–10.9 秒）|白纸上的静电；地平线掠过，太阳印记（1.6 秒），标题被抹去。|
|步行（10.3–73 秒）|一台连续的侧向小车：`camXf = monotone([[0,700],[10.3,700],[16,1400],…,[66,9300],[73,9800]])`（世界像素）；在区域之间加速并在发生事件（火灾、白蜡树）时减慢速度。四个视差层 + 0.2 的云。|
|高大的树|垂直倾斜 `camYf`：沿着山梣在 54.2–57.8 秒内向上移动 980 像素，尺寸线绘制为“≈ 100 m”，然后向下移动 58.4–60.9 秒。|
|薄雾|70.3–73.6 秒：两层波浪纸从底部升起并抹去世界（无剪切）。|
|地图|静态、居中大陆（等距矩形、cos 26° 校正、24 像素/°），及时倒带时垂直方向轻微沉降 90 像素。|
|结尾|地图淡入 30%，标题栏返回到其上方。|

任何地方都没有切口：整个影片是一张涂漆的板材。

- **绘画在**：`plantP` — 植物的进度是`(REV(t) − screenX) / (span × max(.55, parallax))`。 `REV` 在显示期间从 -300 像素扫描到 1650 像素（10.2–13.4 秒）；之后，从右侧进入的所有内容都会绘制在约 380 像素的行程上。 `drawList` 按顺序画 N 笔，每笔画 `clamp(4/N, .12, .5)` 的进度，因此树干在先，叶丛在后。
- **摇摆**：水平倾斜 `sway × (sin(1.15t+φ) + .4 sin(2.7t+2φ))`，树木为 0.006，草和蕨类植物为 0.01–0.03。
- **刷边擦拭**：整个景观通过垂直的波浪形剪辑（`drawStripAt(..., reveal)`）显示，地平线通过从左到右的`drawS`进度显示，海岸线分段，标签通过从左到右打开的矩形剪辑（`hand`）显示，引导线通过增加点数 (`leader`)。
- **音乐锁定动画**：袋鼠跳跃按照配乐的节拍网格进行分阶段（`BEAT0 = 11.865`、`BEAT = .5805`，每2个节拍跳一跳），因此每次着陆都会打一个节拍。
- **活动**：雨滴落到水生植物顶端并沿着分轨音频滑落（14 滴，间隔 0.36 秒），同时湿斑和虚线主根蔓延；火锋在 3 秒内席卷 5650→6900 世界像素，树木交叉淡入淡出为 `#2a2320` 烧焦的精灵，灰带使地面变暗，然后绿色的表皮芽 `drawList` 回来；雨林 `burst` 在 0.9 秒内绘制每一个可见的雨林植物。
- **地图**：降雨场是根据带有时间乘数（`mapTau`）的站点值每帧重新计算的，因此50 Ma→今天是带有径向填充显示的连续“干燥”；干燥时火焰在 500-900 毫米波段闪烁。
- 缓动功能：`engine.js` 中的 `ss`、`eio`、`eo`、`ei`；一切都是 `t` 的纯函数。

<a id="score-structure"></a>
## 配乐结构

- **嗓音**：Kokoro（`kokoro-onnx`，型号`core/tts/kokoro-v1.0.onnx`），语音**`af_heart`**，**speed 0.93**、`lang en-us`——温暖、从容的纪录片阅读。修剪至峰值的 1%，头为 10 ms/尾为 100 ms。数字在 TTS 文本中拼写出来（“两百五十毫米”），并在字幕中写为数字。 13 行，故事每节一行，每行 1.7-7.4 秒。
- **查看**：`asr.py` 用faster-whisper `base.en` 转录每一行；所有 13 个都正确读回（仅拼写变体：“毫米”、“红色中心”、“1%”）。
- **音乐**：斯科特·巴克利 — *野花*（CC BY 4.0）。 322 秒赛道被削减至 117.8 秒**一拍对齐跳跃**: `analyze.py`（librosa 节拍轨道，103.4 BPM，502 节拍；色度 + MFCC 节拍同步自相似性）→`jump.py`对结果落在 100-128 秒的跳跃对进行排名→所选对节拍 85（61.23 秒）→节拍 437（265.61 秒），色度相似度 0.915，4 节拍相位对齐，从节拍前 60 毫秒开始 0.18 秒等功率交叉淡入淡出（`edit.py`）。图片的节拍常数来自同一个`wf_beats.json`.
- **SFX**：全部在 `mix.py` (numpy/scipy) 中合成：纸刷沙沙声（带通噪声、9 Hz 震音、平移扫频）、太阳印记的重击声、沙漠风、46 虎皮鹦鹉的鸣叫声、14 声与时间同步的雨滴叮当声水滴、火焰咆哮+噼啪声、不断上升的雨、两声东方鞭鸟的叫声、浓雾膨胀和安静的地图火焰噼啪声。来自过滤噪声 IR 的短卷积混响。
- **混音**(`mix.py`)：语音 → 48 kHz、90 Hz 高通、RMS 压缩器（−24 dB、3:1）。**Kokoro 的峰值至 RMS 约为 17 dB**，因此 **5 ms 前瞻峰值限制器**（上限 = 语音 RMS + 11 dB）*在*电平匹配之前运行；那么语音RMS = 音乐RMS + 语音时的8 dB；在具有 0.3 s 平滑包络的语音下，音乐鸭子 ×0.62 (≈ −4 dB)；混合归一化至 0.89 峰值。 `mux.sh` 中的最终响度：单通道 `loudnorm=I=-14:TP=-1` → −14.2 LUFS，−1.0 dBFS 峰值。

<a id="palette--props"></a>
## 调色板和道具

**论文**：`demo/paper.jpg`，由`paper.py`生成 - 基础`#f1e9da`，三个八度的平滑噪声（±3.5％），2,600短弯曲纤维（±3.5％light/dark），精细颗粒，5% 晕影。它是每一帧首先绘制的，也是抹去风景的薄雾（`drawMist` 用波浪形上升边缘剪辑 `PAPER_IMG`）。

**墨色**：`INK #2b2520`（线条、文本、主干边缘）、`INK2 #3d3129`（分支、分轨音频）。口音：朱红色太阳`#cf4f2c`，带有7根水平`#b8401f`干刷条（读作印章）；雨蓝`#3f7fa8`（水滴，仪表填充）。

**区域调色板**（`scene.js` `ZCOL`，按摄影机位置与`mixZone`/`zoneGrad`混合）：

|区|天空|远山|中间地带|主要地面|
|---|---|---|---|---|
|沙漠|`#f0d6b8`|`#dcae8e`|`#dba47e`|`#dda27a`|
|穆尔加|`#efdcc6`|`#c89b8c`|`#d0ae80`|`#dbb584`|
|木头|`#ece2cd`|`#bdb99c`|`#cbc28f`|`#dccb92`|
|湿的|`#dfe3dc`|`#9fb1b8`|`#98aa8a`|`#a7b48e`|
|雨|`#dbe3d8`|`#9ab19f`|`#6f8d6d`|`#6e8b69`|

植物颜色套装位于 `plants.js` `COL`（稻草、mulga、盐、树胶、金、灰、蕨类植物、雨、rainLite、棕榈、金合欢）。地图降雨坡道 (`main.js` `MSTOP`)：150 毫米 `#cf7c4f` → 300 `#cda35f` → 650 `#b3b07a` → 1150 `#7f9a6c` → 2000 `#46705a` → 4000 `#2f5a45`，在地图上量化为 5 个波段。

**行程材料** (`engine.js`)：宽度遵循轮廓的色带(`brush`、`leaf`、`even`、`tip`、`trunk`)， ±22 % 值噪声粗糙度，以 `a × rib` 填充（当存在刷毛时，约为 0.57，因此主体是薄水彩晕染）加上 `nb` 刷毛轨迹，不透明度为 30–85 %，每个都具有随机的虚线图案（长线18–90 px，间隙高达 w/2）和随机的早期结束 - 即飞白。 水彩晕染 (`washPoly`) 是同一多边形的 3 个通道，其顶点位于 `a/3 × 1.6`，因此通道不一致的地方边缘会变暗，就像合并的水彩边缘一样。

**层数** (`LAY`)：远（视差 0.25，地面 y 640，比例 0.38，alpha 0.5）·中（0.55、690、0.62、0.78）·主（1.0、745、1.0、 1.0) · fg (1.55, 1115, 1.75, 0.95)。距离=更小、更轻、更不饱和；两个雾带（`mistBand`）位于潮湿区域的各层之间。

**字体排版**：鸬鹚Garamond（生物群落标题500 52像素，字幕斜体500 36像素，标题斜体124像素，地图年份150像素/“今天”斜体104像素），警告500/600（手记， 26–42 像素，在纸色 12 像素阴影光环上绘制两次）、IBM Plex Mono 400（`ANNUAL RAINFALL`、`01 / 05` 等标签，3 像素字母间距）、Noto Serif SC 400（中文字幕行）。通过 `fetch_fonts.mjs` 自托管于 `demo/fonts/`； Noto Serif SC 是 **中出现的 CJK 字符的子集 `scene.js` + `main.js`**。

<a id="titles-subtitles--end-card"></a>
## 标题、字幕 & 片尾卡

- **烧录，双语**，底部居中：英文斜体Cormorant Garamond 36 px（自动换行为2条平衡线，1400 px，基线1000或962/1000）+中文Noto Serif SC 24 px，1042， `INK` 为 78%，均位于 18 像素的纸色阴影光环上，为密度绘制了两次。从 `start − .15` 到 `start + dur + .45` 可见，0.25/0.35 s 淡入淡出。同一张表（`scene.js` 中的 `VO`）驱动混合和 `watercolor.srt`。
- **Biome 卡**（左上）：短彩绘色样，`01 / 05` 单色，鸬鹚名称 52 像素，斜体字幕。 **测量**（右上角）：`ANNUAL RAINFALL`，鸬鹚值 54 像素（`< 250 mm`、`≈ 1,600 mm`），对数刻度条 100–4,000 毫米，带有蓝色水滴标记。
- **标题**：“Follow the Rain”斜体鸬鹚124像素擦拭，然后是空格大写字幕和中文行。
- **结束卡**：褪色地图上的标题栏+IBM Plex Mono 15 px中的制作人员（带有许可证的音乐，语音，海岸线源，“降雨带是示意性的”），其下方是签名**“LemoLab × Claude Opus 5.5”**斜体 Cormorant Garamond 30 px，`INK` 85 %，以 y 1010 为中心，随着制作人员名单 (105–106.2 s) 淡入 — 衬线斜体线，因此它读作影片的签名，而不是另一个资产制作人员。使其远离地图（塔斯马尼亚位于 y ≈ 845–915）。此签核仅属于该库的示范：用​​户的影片不带有 LemoLab 署名，也没有该片尾卡的副本。

<a id="pitfalls-we-hit-demo-record"></a>
## 我们遇到的陷阱（示范记录）

- **条带画布太短，使山丘变平**：far/mid 水彩晕染被预先绘制成长的屏幕外条带。如果条带的 `yTop` 太低，则高脊和雨林树冠墙会被切割成平顶，并且 980 像素向上倾斜会暴露切口。远带跨越 y 150–1500，从世界 x −6000 开始；中间带跨度为 200-1500。
- **半透明条形底部显示硬边**：当在其上绘制半透明层时，停在画布底部的水彩晕染会留下可见的水平接缝。将框架下方的每个条带延伸（至 1500 像素），并使用垂直渐变将主地面淡化到纸上，而不是停止它。
- **顶级 `const` 顺序 → `READY` 从未设置**：所有五个脚本共享一个全局范围。如果初始化在声明之前触及 `const`（例如 `CLOUDS`、`PAPER_IMG`），则异步 init 会抛出异常，`window.READY` 保持 false，并且每个屏幕截图都会在 60 秒后超时。在 `main.js` 中的 async init 内进行所有构建，并读取渲染日志中的 `[pageerror]` 行。
- **决定论**：`mk()`消耗全局RNG。在 `render(t)` 内创建的任何笔画必须包裹在 `withSeed(seed, …)` 中（太阳、HUD 样本、动物、火焰、图例行）或在 `build()` 中预先构建；否则帧取决于渲染历史并且并行工作人员不同意。
- **性能**：每帧绘制数千笔画太慢。将每个成品植物缓存为精灵（`sprite()`）；只有进度< 1（正在绘制）或燃烧的植物才会被一笔一划地绘制。
- **Kokoro 声音非常尖峰**（~17 dB 峰值到 RMS）：单独匹配 RMS 要么埋没声音，要么削波——先限制，然后匹配。
- **节拍锁定动画**：保留配乐的节拍网格（`wf_beats.json`）作为`BEAT0`/`BEAT`的源；如果音乐编辑发生变化，请重新导出它们。
- **CJK 子集**：新的中文字幕字符以后备字体呈现，直到您重新运行 `node fetch_fonts.mjs`（它将 Noto Serif SC 子集为 `scene.js` + `main.js` 中的字符）。
- **`mix.py` 使用正则表达式 `\['(v\d\d)', ([\d.]+),` 解析 `scene.js`** 来放置语音线路 - 保持 `VO` 行完全相同的形式。
- `playwright-core` 从存储库根解析（`demo/` 中没有 `node_modules`）。 zsh 不进行分词 `$TS`；当传递许多时间戳时使用 `${=TS}`。

<a id="build-notes"></a>
## 构建笔记

```
styles/watercolor/demo/
  index.html      loads fonts.css + aus.js, engine.js, plants.js, scene.js, main.js (classic scripts, one global scope)
  engine.js       RNG/easing/noise, monotone spline, colours, the stroke engine (mk, drawS, drawList, sprite, clump, edgeOf)
  plants.js       plant & prop generators (spinifex, desertOak, mulga, saltbush, wattle, tussock, gum, ash, treeFern,
                  groundFern, rfTree, fanPalm, vine, farTree, uluru, cloud, shrub)
  scene.js        VO table, layers, zones, camera, world build, wash strips, landscape drawing, animals, fire, rain, notes
  main.js         canvas, map (deep time), mist, HUD, subtitles, title/end card, render(t), async init → READY
  aus.js          coastline rings (from extract_aus.mjs + vendor/)   paper.jpg (paper.py)   fonts/ + fonts.css (fetch_fonts.mjs)
  tts/lines.json  voice script   tts/gen.py  Kokoro   asr.py  whisper check   voices/  v01–v13.wav + dur.json
  music/          prep.sh (source files) · analyze.py · lag.py · jump.py · edit.py → score.wav
  mix.py          SFX + voice + music → mix.wav      render.mjs  stills / video / part     mux.sh  → ../watercolor.mp4
```

来自存储库根目录的所有命令，Python = `.venv/bin/python`：

```sh
D=styles/watercolor/demo
# 1. voice (13 lines, ~10 s) and whisper check
.venv/bin/python $D/tts/gen.py                 # → $D/voices/v01..v13.wav + dur.json  (OUT=dir to write elsewhere)
.venv/bin/python $D/asr.py                     # prints each transcript; compare with tts/lines.json
#    copy the durations into the VO table in scene.js (id, start, dur, en, zh) and set the start times
# 2. music
sh $D/music/prep.sh                            # Wildflowers.mp3 → Wildflowers.wav (22.05k mono) + wf48.wav (48k)
.venv/bin/python $D/music/analyze.py           # → wf_beats.json (plot skipped: no matplotlib in .venv)
.venv/bin/python $D/music/jump.py              # ranked jump candidates; pick one, put its beat indices in edit.py
.venv/bin/python $D/music/edit.py              # → score.wav, score_beats.json
# 3. look at frames while building (≈0.35 s/frame as PNG)
OUT=$D/out/review node $D/render.mjs stills 5 20 43 66 90 106
.venv/bin/python core/render/sheet.py $D/out/review/sheet.jpg $D/out/review/t_*.png --cols 3 --w 640
# 4. mix (4 s) — writes $D/mix.wav, or pass a path
.venv/bin/python $D/mix.py
# 5. video: 6816 frames at 60 fps, ~50 ms/frame/worker (8 workers ≈ 2 min; keep 2–3 when other jobs run)
node $D/render.mjs video 8                     # → $D/out/seg_0..7.mp4 + out/list.txt  (x264 crf 12 intermediates)
# 6. mux (≈70 s): concat + x264 slow crf 16 g 120 + loudnorm −14 → styles/watercolor/watercolor.mp4
sh $D/mux.sh                                   # or: sh $D/mux.sh path/to/test.mp4
# 7. subtitles: VO table → srt
#    ($D/out/srt_cues.json = VO rows as {t0: s-.15, t1: s+dur+.45, text: "en\nzh"}, dumped from scene.js with a 5-line node script)
.venv/bin/python core/render/srt.py $D/out/srt_cues.json styles/watercolor/watercolor.srt
```

部分重新渲染（用于最终卡签核）：`node $D/render.mjs part 99.4 113.6 $D/out/seg_7.mp4` 准确地重新创建最后一个 8 工作线程段（帧 5964-6815），然后是 `sh $D/mux.sh`。
一次性资源脚本（已运行）：`node $D/extract_aus.mjs`（海岸线）、`cd $D && ../../../.venv/bin/python paper.py`（纸质）、`node $D/fetch_fonts.mjs`（字体，需要网络）。

<a id="engine-reference"></a>
## 发动机参考

**页面合约**（`render.mjs`依赖它）：`window.DUR`（秒）、`window.render(t)`（t的纯函数，绘制整个框架）、`window.READY = true`经过字体、纸张和`build()` 完成。画布 1920×1080，`ctx` 全局，来自 `main.js`。

**冲程发动机 — `engine.js`**

|功能|用途/参数|
|---|---|
| `mk(pts, w, col, o)` |从中心线开始划线`[[x,y],…]`, 底宽`w`px，十六进制颜色。`o.prof`: `'brush'`（默认：粗开始，逐渐变细），`'leaf'`（罪恶膨胀），`'even'`（扁平、短锥度）、`'tip'`（粗根→细尖），`'trunk'`（展开的底部，-62% 到顶部）。`o.nb`: 刷毛轨迹（默认`clamp(round(w/3.2), 3, 9)`什么时候`w ≥ 6`，否则 0)。`o.a`：不透明度（0.92）。`o.rib`：身体不透明度系数（0.62刷毛，0.92 无）。`o.rough`：宽度噪声 (0.22)。消耗RNG。|
|`drawS(c, s, p=1, col, am=1)`|上下文 `c` 上的绘画描边 `s` 高达其长度的分数 `p`（移动画笔笔尖），可选颜色覆盖和 Alpha 乘数。|
|`drawList(c, L, p)`|按顺序绘制笔划列表； `p ∈ [0,1]` 为整个列表。|
|`sprite(L, col)`|将笔划列表光栅化到屏幕外画布 → `{cv, x0, y0, x1, y1}`（以本地坐标在 `x0,y0` 处绘制）。 `col` 以一种颜色重新绘制所有笔画（烧焦的轮廓）。|
|`qcurve(x0,y0,x1,y1,bend,n)`、`qctrl(...)`、`polar(x,y,ang,len,bend,n)`|中心线辅助对象（二次曲线；`bend` 是控制点的横向偏移）。|
|`clump(S, cx, cy, r, n, cols, o)`|将 `n` 叶点推入椭圆形（`o.sx`、`o.sy`），可选方向 `o.dir ± o.spread`、长度 `o.l0–l1`、宽度 `o.w0–w1`、alpha `o.a0–a1`。|
|`edgeOf(s, side, w, col, a)`|Shadow/ink 边缘沿着笔画的一侧运行（躯干、四肢）。|
|`withSeed(seed, fn)`|使用固定 RNG 运行 `fn` — **必需的** 对于 `render` 内部构建的任何内容。|
|`monotone([[t,v],…])`|单调立方关键帧轨道（摄影机路径）。|
|`ss eio eo ei seg clamp lerp vnoise fbm hash mixc rgba`|缓动，范围，噪音，颜色助手。|

**Plants — `plants.js`**：每个生成器都采用比例 `sc` （和可选参数），在本地坐标中工作，根位于 (0,0) 且 y up = 负，并返回 `{ S: strokes, … }` （`gum` 也返回`woody`、`leaves`、`shoots`、`fork`；`mulga` 返回 `stems`；`ash`/`rfTree` 返回 `top`）。

**World — `scene.js`**：`add(layer, worldX, generator, scale, {dy, span, sway, args, extra})` 将植物放入 `PL[layer]` 并缓存其精灵； `build()` 通过使用 `zoneJit` 行走世界 x 来填充区域； `buildStrips()` 预涂 hill/ground 水彩晕染和 `washPoly(c, pts, fill, alpha, passes, jitter)`； `drawLandscape(t)`画天空→远strip/plants→薄雾→中→地面→地平线→主要植物（英雄事件有挂钩）→动物→火→前景→雨。注释：`hand(txt, x, y, p, {size, w, align, col})`、`leader(x0,y0,x1,y1,p,bend)`、`note(t, t0, t1, anchorX, anchorY, labelX, labelY, txt, o)`； `scr(plant, dx, dy, t)` 将工厂本地点转换为标签的屏幕空间。

**最小示例** - 替换 `scene.js` + `main.js` 以获得一棵胶树画在纸上（保留 `index.html`、`engine.js`、`plants.js`、 `paper.jpg`，字体）：

```js
const cv = document.getElementById('c'), ctx = cv.getContext('2d');
window.DUR = 6; let PAPER_IMG, tree, horizon;
function render(t) {
  ctx.setTransform(1, 0, 0, 1, 0, 0); ctx.globalAlpha = 1; ctx.drawImage(PAPER_IMG, 0, 0);
  drawS(ctx, horizon, seg(t, .2, 1.6));                                   // horizon brushed across
  const p = seg(t, 1, 4.5), sk = .006 * Math.sin(t * 1.15);                // paint-in progress + sway
  ctx.setTransform(1, 0, sk, 1, 960, 820);
  if (p < 1) drawList(ctx, tree.S, p); else ctx.drawImage(tree.spr.cv, tree.spr.x0, tree.spr.y0);
  ctx.setTransform(1, 0, 0, 1, 0, 0);
  withSeed(7, () => drawS(ctx, mk(qcurve(80, 90, 120, 90, 0, 5), 9, '#b3b07a', { prof: 'even', nb: 3 }), seg(t, 4.5, 5)));
  ctx.font = '500 52px "Cormorant Garamond"'; ctx.fillStyle = rgba(INK, ss(seg(t, 4.6, 5.2))); ctx.fillText('Eucalypt woodland', 76, 150);
}
window.render = render;
(async () => {
  PAPER_IMG = new Image(); PAPER_IMG.src = 'paper.jpg'; await PAPER_IMG.decode();
  await document.fonts.load('500 52px "Cormorant Garamond"');
  tree = withSeed(1, () => gum(1.2)); tree.spr = sprite(tree.S);
  horizon = withSeed(2, () => mk(qcurve(120, 822, 1800, 822, -4, 40), 5.2, INK2, { prof: 'even', nb: 5, a: .88, rough: .3 }));
  window.READY = true;
})();
```

对于完整的影片：保留`engine.js`/`plants.js`（为您的样本添加相同风格的生成器），重写`VO`、`LAY`、`ZONES`、`RAINK`风格值表， `camXf`、`ZCOL` 和 `build()` 位于 `scene.js`，地图/HUD/标题位于 `main.js`。
