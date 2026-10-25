<a id="data-storytelling--our-demo"></a>
# 数据讲故事——我们的示范

众多例子中的一个。请勿重复使用其故事、弧线、镜头、道具或时间安排。

示范：*一百个夏天*（50.0 s）·`dataviz.mp4`·来源在[`demo/`](demo/)


一百零一个夏天的真实全球温度（NASA GISTEMP v4，6 月至 8 月），讲述了 1926 年至 2026 年一位女性的生活。

<a id="story--structure"></a>
## 故事与结构

我们的数据是一个时间序列，因此它被绘制为点和一条变成条纹的线。这是一个数据集的一种选择。

形状：一点冷开。嫩，早点稀疏。稳定的中间。加速：笔记变得更密，铅笔变得更快。框架破裂了，铅笔退缩并翻转到红色的一端。一阵匆忙。 **一切提前停止半拍；这是影片中唯一的剪辑，陷入沉默。** 然后是最后一个数据点，单独的，随后是整个系列的一个视图。接下来是条纹的变形，然后是较长的记录，然后是下一个值的空单元格（“下一个夏天？”）。 片尾卡位于该空单元格内。

它如何与数据拟合：101 个点（一系列 60-150 个点适合这种形状）； 3 个人类音符固定在第一个蓝色标记上（“1926 — 她出生了。”），2 个唱片音符固定在最后一个红色标记上；数据中发现一个打破帧的时刻；最后一点给出了自己的沉默。

<a id="shots"></a>
## 镜头

|打|摄影机|
|---|---|
|冷开|第一个点的极端特写 (≈4×)。写笔记时向上倾斜以跟随引导者。|
|标题|拉回到 1.55×。下降线成为x轴；上面的标题排版。|
|早期生活|推回，然后跟踪铅笔，最新点位于框架宽度的 ~62% 处。随着时间加速缓慢拉出 (2.3 → 1.7×)。|
|爬|随着荷兰角逐渐进入 (0 → -1.5°)，基座随着上升曲线而上升。|
|断帧|插入 2 帧 (1.22 → 1.42×) 加上衰减抖动。重新缩放时有一个小震动。|
|匆忙|快速拉出至 1.0×，滚动至 −3°，持续 2 px 震颤。|
|**剪裁**|硬切入空槽的特写：虚线柱、`2026` 标签、水平地平线。当它落地时，将焦点从散焦的前景铅笔转移到其笔尖。|
|揭示|写下注释时按住最后一点，然后拉回到完整视图 (1.06×)。轴重新缩放以适应一切。|
|变形|锁定。|
|规模|拉动并平移 (→ 0.72×) 以添加较早的记录。|
|回声|推入空单元格；它加宽为片尾卡（框架内框架）。|

主体帧高≥1/3的关键时刻：第一个点加注释、世纪图、条纹带。

为什么这条路线，对于这个数据：第一个事实得到了极端的特写，因为一个女人的出生是人类的尺度；随着该单位的首次命名，轴不断增长；追踪将过去抛在脑后，展望未来；升级、惊喜和仓促来自于数据本身；变形被锁定，因为变形就是运动；由于下一个值未知，因此结局被推入空的下一个单元格。每个都是 STYLE.md §6 中的一种选择，而不是该风格的默认值。

运动数：90 BPM（选择该值是因为 1/32 音符在 24 fps 下正好是 2 帧）；四分音符 7 个点 → 八分之一 24 个 → 十六分之一 40 个 → 三十秒 27 个（每 2 帧一个点）。重新调整音阶：1/32 音符上有四个音阶，每个音阶缓和超过 0.09 拍；在清晰度阶段的第二次重新调整是顺利的。退缩：冻结半拍，然后 0.5 秒左右翻转至红色领先位置。 Morph：扫过0.85节拍；每个标记落至条带中心（前 45%），然后拉伸至完整条带（缓出）并失去其环；线段随着左边的点开始变形而消失；注释以带子上方的小铅笔标记形式返回。

<a id="score-structure"></a>
## 配乐结构

- 氛围：房间音→傍晚的蟋蟀→大海（《1933》前J-cut，L-cut后）→随着热度越来越大、越来越密的蝉声（攀登前J-cut）→寂静后的开放风→房间音。
- 可听化（`music/score.py`）：`midi = 62 + (v + 0.4) × 17`；低于中心的值会对齐到 D 大调五声音阶。仅在最后约 15 个点（5 → 45 音分）失谐。静音之前的音符是最不和谐的（最大失谐加上小二度阴影）；沉默之后的最后一点是最干净、最高的音符。
- 床：垫 Dmaj9 → G/D → D–Bm–G–A → Bb/D–Dm → 半音簇；帽子在 9.5 kHz 处低通。沉默之后：D开五度（没有第三个，没有答案），在变形过程中重播所有101点的滑奏，Gmaj7#11在D之上，音阶镜头，**第一点的音符在片尾卡下再次**。
- 配乐弧线：稀疏、温柔的早期点→稳定的中间→随着音符的密集而加速细分→急促→沉默→最后一个点单独→整体→变形→再次第一个音符。
- 静音：最后一点（所有层）之前 1.0 秒真正的数字静音；空单元前 0.67 秒近乎寂静。在它们之后发出第一个声音：最后一次敲击加上它的音符，然后是空单元格的第一次敲击。
- 混音：人声下音乐-11 dB、蝉声-6 dB； 300–4000 Hz 频段内的旁白 SNR 8.6–16 dB； −14 LUFS，颗粒 0。
- 声音：Kokoro `af_alloy`，速度0.92，5行，永远不会超过冲刺、沉默或变形。 Whisper 将数字写为数字：`asr` 设置为“For 50 years…”和“…turned 100…”。
- 婴儿的笑声被音乐盒般的音符所取代。

<a id="palette--props"></a>
## 调色板和道具

- 纸`#F6F3EC`；点网格 24 像素 `#E4DDCF`。墨水 `#2B2723`：轴 1.4–1.6 像素，系列线 2.4 像素，网格线 `#DDD6C9` 1 像素，零线 `#BDB4A5` 1.3 像素。刻度编号 IBM Plex Mono 17–20 px `#6E665C`。
- 点 r = 6 px，带有 1.5 px 墨环；着陆弹出 0.25 秒（×1.55）。
- 斜坡，u =（v − 中心）/一半：`#2166AC` → `#4393C3` → `#92C5DE` → `#D1E5F0` → `#F2EEE8`（中心）→ `#FDDBC7` → `#F4A582` → `#D6604D`→`#B2182B`→`#7A0F1E`（超过+1）。中心 = 1971–2000 平均值 0.22 °C，半跨度 0.85 °C。
- 手写警告 30 px 世界大小，蓝色铅笔 `#2F5D8A` / 红色铅笔 `#A8283A`，每个字形 ±1.7° 旋转和 ±2.5 % 基线，16 % 的像素因颗粒而被剔除。涂鸦：三卷波浪，一颗心。
- 铅笔木锥体 `#E3C79C`，进入角度为 35–58°。
- 世界空间中的绘图框 1500 × 520；第一个音符位于其标记上方，最后的音符位于其点的左上方；底部 150 像素为标题。标题新闻阅读器 66 像素。
- 说明文字：新闻阅读器 42 px，x = 180，基线 y ≈ 985，踢球 `1926–1958`，3 帧升淡，离开时向上翻转；保持规则在 `tools/subs.py` 中声明。
- 发动机展示使用 `#D97757` 强调火花。

<a id="end-card"></a>
## 端卡

在虚线“下一个单元格”内：标题，`DATA STORYTELLING`，条纹的缩影加上一个空的虚线单元格，`Lemo-Opuscar · LemoLab × Claude Opus 5.5`，数据，字体，语音和音乐制作人员（包括“2026年价值初步，检索于2026年9月26日”），以及手写的“她的故事是虚构的。每个数字都是真实的。” LemoLab 签核仅属于该库的示范；用户的影片没有 LemoLab 积分，也没有该卡的副本。

<a id="build-notes"></a>
## 构建笔记

```
styles/dataviz/demo/
  data/        GLB.Ts+dSST.csv (as downloaded) + jja.json      tools/extract_data.py  column → json + story facts
  timeline.js  90 BPM grid, year → beat map, every key beat, chart geometry (single source of truth)
  engine.js    the style: paper, camera, pencil strokes, handwriting, dots, stripes, morph, pencil, caption, shapes
  film.js      the story: annotations, camera path, pencil activities, chart layers, end card, events for the mix
  music/score.py   sonification + modular bed (reads events.json)      mix.py   ambience + foley + narration + ducking
  tools/       words.py subs.py cuecheck.py final_asr.py
```
1. 下载数据集并编写提取器。打印出叙述中声称的每一个事实。
2. 在任何绘图之前写上`timeline.js`（网格加年份→节拍图）。
3. 构建 `engine.js`，然后构建 `film.js`，并从真实引擎 (`node core/render/still.mjs … --range`) 渲染门帧。
4. `sh demo/build.sh` 在大约 2 分钟内从头开始重建所有内容：提取 → TTS → Whisper 语音识别 → 单词 → 事件 → 配乐 → 提示检查（107 个提示，最长 0.03 毫秒）→ 混合 → 字幕 → 渲染（1200 帧，约 30 秒，2 个工作人员）→ 复用器（−14 LUFS，颗粒 0）→ 风格定帧和海报。
5. 回顾：两次最终 mp4 的 1 秒接触表（偏移 0.25 秒）、0.1 秒的中断、剪切和变形片段、最终混音上的每行耳语以及样本精确的静音检查。

与此示范相关的陷阱：GISTEMP 在季节性列之前有 J-D 和 D-N，因此按标题名称 (`JJA`) 选择该列。 0.17 秒后重新缩放的帧中断是不可见的。右对齐笔记：铅笔跳占文本阶段的 16%。 `pencilStroke`、`dashedCell` 和 `dataDot` 自行设置 `globalAlpha`。在跟踪镜头时，世界空间标题被框架边缘切断。在第 32 个音符的密度下，铅笔主体位于新的圆点上。

<a id="engine-reference"></a>
## 发动机参考

`demo/engine.js`（ES模块，Canvas 2D，1920×1080；进口`/core/lib.js`）。世界单位是缩放 1 时的图表像素。在绘制任何世界空间之前调用 `applyCam(g, cam)`。

|功能|它的作用|关键参数|
|---|---|---|
|`drawPaper(g, cam, {dots})`|奶油色纸、纤维噪声和点网格，固定在世界空间中|`dots` 0–1 网格阿尔法|
|`applyCam(g, cam)` / `w2s` / `s2w` / `viewRect`|2D 摄影机变换和转换|`cam = {x, y, zoom, roll, sx, sy}`（sx/sy = 像素抖动）|
|`valueColor(v, {center, half, alpha})` / `rampRGB(u)`|发散条纹坡道|参考平均值 `center`，对称 `half`|
|`pencilStroke(g, pts, o)`|**用铅笔绘制任意多段线**：摆动、锥度、石墨颗粒、书写；返回小费|`color, width, progress, seed, wobble, passes, grain`|
|`inkShape(g, path, o)`|**any 封闭形状** 作为铅笔注释标记：平面填充 + 剖面线 + 手工轮廓|`fill`（重音）或 `value`（斜坡）、`hatch, progress`|
|`plotShape(g, path, o)`|将任意路径采样为点线数据系列|`n, r, values, accent, progress`|
|`stripesFill(g, path, values, o)`|用温暖的条纹填充任何封闭的形状|斜坡选项，`accent` + `accentIndex`|
|`dotTrail(g, pts, o)`|逐渐变细的点轨迹（光标尾部/彗星）|`color, r0, r1`|
|`handText(g, text, x, y, o)`|字迹有纹路，左→右显露；返回 `{tip, w}`|`size, color, progress, align, zoom`|
|`setType(g, text, x, y, o)`|印刷式，逐字排版|`size, font, weight, progress, rise, track`|
|`dataDot(g, x, y, r, fill, o)`|带有着陆爆裂声和波纹的数据点|`fresh`（着陆后的时间），`ripple, accent, alpha`|
|`inkLine`、`stripe`、`morphMark(g, u, dot, box, fill)`|系列线、一条条纹、点→条纹变形为 0..1| |
|`leader`、`ringPath`、`wavePath`、`heartPath`、`bracketPath`、`sparklePath`、`quadPath`|注释几何| |
|`dashedCell(g, x0, y0, x1, y1, o)`|虚线的“下一个值”单元格，绘制在|`progress, color, dash, gap`|
|`drawPencil(g, o)`|红蓝铅笔（屏幕空间）|`tip [sx,sy], s, lift 0–1.2, flip 0–1 (blue→red), blur, focus, ang`|
|`caption(g, words, t, o)`|带定时文字的图形标题字幕|`t0, t1, kicker, x, y, size`|

最小示例：带有光标尾部的暖橙色 `#D97757` 四点火花，以这种风格绘制（完整版本：`?engine=1` → `demo/stills/engine_demo.jpg`）。

```js
import * as E from './engine.js';
const g = canvas.getContext('2d'), cam = { x: 0, y: 0, zoom: 1, roll: 0 };
E.drawPaper(g, cam); E.applyCam(g, cam);
E.dotTrail(g, Array.from({ length: 9 }, (_, i) => [-300 + i * 26, 170 - i * 14]), { color: '#D97757', r0: 9, r1: 2 });
E.inkShape(g, E.sparklePath(0, 0, 150), { fill: '#D97757' });            // accent bypasses the ramp
E.leader(g, [110, -200], [40, -110], { color: E.P.blue });
E.handText(g, 'the spark, in pencil', 120, -210, { size: 34, color: E.P.blue });
const tip = E.w2s(cam, 150, 0);
E.drawPencil(g, { tip, s: .8, lift: .2, flip: 0 });                        // flip: 1 = red end
```
