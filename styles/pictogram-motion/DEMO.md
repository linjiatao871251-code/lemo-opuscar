<a id="pictogram-motion--our-demo"></a>
# 象形图运动 — 我们的示范

众多例子中的一个。请勿重复使用其故事、弧线、镜头、道具或时间安排。

示范：*爱知-名古屋 2026 — 所有 43 项运动*（EN-JP 版本，163.6 秒，1920×1080 @ 60 fps，150 BPM，70 张运动卡，无旁白） · `pictogram-motion.mp4` · 来源[`demo/`](demo/) · 引擎：Canvas2D (`engine.js` + `scenes.js` + `poses/*.js`)，无头 Chrome 帧捕获，numpy 合成的配乐。


> **版权说明。**示范是为真实赛事（2026 年第 20 届爱知-名古屋亚运会）非官方粉丝制作的宣传片；爱知名古屋亚运会组委会和亚洲奥林匹克理事会并未制定或认可该决议。红日环标志是模仿官方徽章用代码绘制的，标语是官方标语，引用；我们的也不能重复使用。在您自己的影片中，将两者替换为原始的。赛事名称（AICHI-NAGOYA 2026 / THE 20TH ASIAN GAMES）、口号（IMAGINE ONE ASIA / ここで、ひとつに。）、用代码绘制的像会徽一样的红太阳和五环标记、五色调色板及其颜色名称、网格图案语言都遵循组织者的身份。它们隶属于主办方（爱知名古屋亚运会组委会/亚洲奥林匹克理事会）。 `demo/ref/`持有从奥运会网站下载的官方图片，仅供参考。它们永远不会被纳入影片中，也不得重新分发。**由该代码生成的任何其他影片必须替换所有特定于事件的元素**（请参阅[替换事件元素](#replacing-the-event-elements)）。

<a id="story--structure"></a>
## 故事与结构

球迷宣传片列出了多项运动比赛中的每一项运动，每项运动一张卡，随节奏。 示范如何使用该风格的固有能力：

|原生电源|故事运用|
|---|---|
|**一张卡=一件物品**|任何 20-80 件事的列表：游戏的每个事件、套件中的每个工具、流程的每个站。计数就是钩子（“ALL 43 SPORTS”）。|
|**章节 = 颜色**|将列表分为 5-7 个系列。每个家庭都有一个调色板色调，因此观看者总是知道他们在哪里。|
|**象形图动作**|每个项目都需要一个需要 1.6 秒读完的*动词*（投掷、跳跃、摆动、踏板）。如果一个物品没有身体动作，请给它一个支撑动作（齿轮转动，杯子倒出）。|
|**步梯**|普通卡为 4 节拍（1.6 秒）。子系列变为 2 节拍快速跑（4 个游泳泳姿、4 个自行车项目、球拍运动），这为影片提供了第二个节奏，而无需更改 BPM。|
|**长拍**|第一个也是最大的一章是摄影机运动沿着轨道的横向：14 个电台一个屏幕相隔，每个节拍上都有一个鞭子。将其用于“英雄”家庭。|
|**大结局网格**|所有项目都以 9×5 图标墙的形式返回，翻转，变成一种颜色，折叠成一个太阳，然后是口号和片尾卡。|

**故事形状（示范）：**心跳冷开（墨水上跳动的红点，周围画着圆圈）→标题猛击全五色图案→三个计数（43个体育/469个事件/16天）→“ON YOUR MARKS…SET…”半拍的沉默 → 7 个章节，70 张卡片 → 图标墙结局 → 口号 → 片尾卡 → 随着音乐的响起淡入黑色。

调整主题：列出项目；将它们分为 5-7 章；给每个项目一个单拍动词；选择一章作为长镜头；选择哪些跑步是 2 拍；为结局写一个两行口号。

<a id="the-demos-look-as-built"></a>
### 示范的外观

**目录影片**：一组N个项目（体育、产品、特色、菜肴、步骤）一次显示一张卡片，快速、按节拍。每张卡片 = **one 象形图执行一个动作 + 巨大的标题 + 第二语言行 + 单声道索引“07 / 43”**。卡片分为章节。每章都拥有五色调色板中的一种颜色。每个组都会打开带有全出血图案的章节卡。

可识别的成分有：
1. **网格图案**（“核心图形”）：180像素的方形网格。大圆盘和半圆盘跨越细胞。大约一半的细胞带有小图案（鱼鳞波浪、点鳞、三角鳞、条纹日落、gear/sun 轮、新月、同心弧、方格、梯度四分之一圆盘……）。该图案使用 **一种色调的 5 个色调**，并且 **整行被剪切并横向移动**。行移是标志：它驱动背景、章节节拍和主要过渡。
2. **象形运动员**：扁平，无脸，由带有圆盘头的圆棒制成。近侧肢体以前景色绘制，远侧肢体以 42% 与背景混合的颜色绘制。道具也是几何形状的：圆盘、圆环、胶囊、直线。
3. **类型为架构**：一个 900 粗细的 grotesk 标题 (Inter Tight) 设置为 150–330 像素高，其下方有一条粗 CJK 线 (Noto Sans JP)。小型 DM Mono 元文本位于角落，就像广播 HUD 上一样。

气氛是优质体育广播的标识：平坦的颜色，除了一次柔和的光扫描之外没有渐变，没有轮廓，除了非常浅的影片颗粒之外没有纹理。

<a id="shots"></a>
## 镜头

|#|部分|摄影机 / 图片|风格特有表现手法/注|
|---|---|---|---|
|1|冷开|锁定的框架：一个红点在墨水上像心跳一样跳动，周围有环|唯一 `oBack` 轻松|
|2|标题|猛击全五色图案；行过渡出|行移位显示|
|3|计数|43 项体育运动/469 项赛事/16 天，每项一栏|计数满贯|
|4|“各就各位……准备……”|已锁定；第一章前半拍的沉默|大打击前的沉默|
|5|田径（第一章）|长镜头：14 个站点相隔一个屏幕，每个剪辑都精雕细琢|长记下一条轨道|
|6|第 2-7 章|锁定卡片，布局 A/B/C/M 每章轮换，游泳、骑自行车和球拍的 2 节拍运行|章节=颜色；步速阶梯|
|7|结局|9×5图标墙翻转，变成一种颜色，放大到0.9，瓷砖塌陷成一个红太阳|图标墙；许多合而为一|
|8|标语+片尾卡|太阳和光环升起又收缩；口号、标题、日期、彩条、信用额度；在铃声结束时淡入黑色|参见片尾卡|

摄影机仅存在于 **长镜头** (`trackScene`) 中。那里有 14 个站点，间隔一屏幕宽度。 摄影机以 42 px/s 漂移，并且每次剪切都会鞭打一个全屏（`E.ioExp` 从节拍前 0.14 秒到节拍后 0.24 秒）。两行 360 像素图案单元的背景行以视差 0.28 和 0.42 滚动。深红色赛道 (y 780) 具有奶油色车道线，跑步比赛中划线滚动得更快（`RUNNING` 速度）。赛道上绘制了赛事规格（`100M`、`4×100M`、`7.26 KG`…），剪切力为 -0.35，奶油含量为 12%。其他地方的框架都是锁定且平坦的；能量来自行的移动、转换和图形动作。

简介和结局“摄影机”：结局墙放大到 0.9，带有 10 px 排水沟，然后每个瓷砖都塌陷到中心，并从中长出一个红色的太阳。 片尾卡的太阳和光环从中心上升到 y 330，同时缩小到 0.62×。

<a id="score-structure"></a>
## 配乐结构

- **无旁白。** 影片由文字和音乐承载。字幕文件只是标题卡轨道（请参阅片尾卡）。
- **配乐**：原始的，在`demo/music/music.py`中完全合成（numpy + scipy；无样本）。 “和太鼓 × 电子”，150 BPM 4/4，D *miyako-bushi* (D Eb G A Bb) 在 D 小调和声之上，101 小节 = 161.6 秒加上 2 秒响铃。合成乐器：odaiko / nagado / shime taiko，*ka* 边缘咔哒声，踢，拍手，军鼓，帽子，震动器，碰撞，加上拟音类似的敲击声（飞溅，掉落，戳，叮当声，裂纹）。三味线和古筝是 Karplus-Strong 拨弦（`ks_render`，带有弯音的古筝）；还有合成贝司、打击垫、失谐锯齿和弦、立管和无人机。
- **图片由数据**锁定：`music.py`读取`music/timeline.json`（从`edl.js`导出）。每个镜头开头都有按章节选择的重音（`card_accent`：用​​于水上运动的飞溅，用于球拍的 *pok*，用于战斗的 odaiko + 刺，用于力量的 clang...）。章节和结局开始时为 `big_hit`、**，之后是半拍的静音**（鼓和贝斯静音）。该报告将 79 个镜头起始点中的每一个起始点检查在 ±15 ms 之内（示范：79/79 通过，偏移 ≤ 0.2 ms）。
- **掌握**: 分轨音频 `music_bed.wav` + `sfx.wav`，2:1 胶水压缩器和限制器，集成 −14 LUFS 且 ≤ −1 dBTP (示范: −14.11 LUFS, −1.12 dBTP）。 `music/report.txt` 保存响度、频带能量、起始点和间隙检查。渲染时间约为 30 秒。
- **部分布局硬编码为`compose()`中的**（条形中的`EXPECTED = dict(intro=0, ath=12, …, finale=89)`）。如果 EDL 更改，则会触发断言。对于新的影片，为新的章节条重新编写`compose()`（将其交给带有`timeline.json`和此部分的音乐子代理）并保持`card_accent`、`big_hit`和报告不变。

<a id="palette--props"></a>
## 调色板和道具

**帆布**：1920×1080，网格`G.CELL = 180`（10.7列×6行）。一切都与该网格对齐：章节带高 2 行，过渡由 180 像素行或 240 像素列切割，最后的墙为 9×5。

**调色板**（`engine.js` → `G.PAL`；每个色调有五个色调 `t[0]` 最暗 → `t[4]` 最亮；`t[2]` 为基础）。 示范的值取自官方核心图：

|钥匙|示范名称|t[0]|t[1]|**t[2] 底座**|t[3]|t[4]|fg（类型和图形）|
|---|---|---|---|---|---|---|---|
|红色的|中越红|`#c21d15`|`#d22419`|**`#e83220`**|`#ec5a26`|`#f07a45`|奶油`#fbf6ec`|
|紫色的|杜鹃紫|`#231a6e`|`#2c2084`|**`#4e3a93`**|`#644d9d`|`#7a62a9`|奶油|
|绿色的|森林绿|`#006d35`|`#008440`|**`#079a3e`**|`#2da547`|`#68b15d`|奶油|
|金子|金鯱金|`#b48900`|`#c69b00`|**`#d5b102`**|`#debc2f`|`#e7d16c`|深色 `#211904`|
|赭石|丹托赭色|`#946a2e`|`#ac7d38`|**`#c18e46`**|`#d2a55c`|`#e0bf84`|深色 `#1e1409`|
|墨水|须弥|`#0f0c15`|`#16121d`|**`#1e1a27`**|`#2a2535`|`#3a3447`|奶油色、口音=金色|

膏霜`G.CREAM = #fbf6ec`，墨水`G.INK = #15111c`。 **金色和赭色采取深色字体和深色数字**；其他人则服用奶油。 `G.CYCLE = ['red','purple','green','gold','ochre']` 是多色章节和介绍图案使用的旋转。在卡片上，图案绘制在 `spread 0.42`（低对比度，因此可以读取字体），而在章节卡片上则绘制在 `spread 0.95`（全对比度）。

**图案**（`G.pattern(palKey, seed, {spread, density})`）：填充为`t[1]`。在每个网格节点上，34％的时间以随机音调放置半径为 `CELL` 的圆盘，16％的时间放置 `t[3]` 圆盘，其中包含 `t[0]` 半半径圆盘。然后，一小部分 `density` 细胞获得 14 个图案之一（`G.motif` 种类 0-13）：四分之一圆盘、半圆盘、圆盘 + 点、条纹日落、*seigaiha* 鱼鳞波、点鳞圆盘、三角形鳞片、同心弧、太阳轮/齿轮、方格、新月、S 波、梯度四分之一圆盘、褪色酒吧。每个图案随机旋转 90° 倍数。画布比屏幕宽 3 个单元格，因此任何行都可以移动 ±1 个单元格。 **所有图案均为通用几何形状。** 请勿将活动吉祥物、地标或产品绘制到单元格中。

**象形图**（`G.joints` + `G.drawFigure`）：单位为身高=1，原点为臀围。节段长度为躯干 0.30、颈部 0.045、头部半径 0.082、上臂 0.16、前臂 0.15、大腿和胫骨 0.225。宽度为躯干 0.145、手臂 0.076、腿部 0.094，均带有圆帽。绘制顺序是远腿、远手臂（颜色 `far` = fg 向背景混合 42%），然后是躯干、近腿、近手臂、头部 (fg)。在 `far2`（60% 混合）中，第二个人（对手或伙伴）落后。在卡片中，人物站在 **sun 圆盘** 上（r 360–380 像素，浅色色调为 `t[1]`，`t[4]` 为 gold/ochre，`t[3]` 为墨水），带有慢速 9 % 白色光线扫过它。

**卡片布局**（`layoutOf(s)`，通过订单字符串（例如`ball: 'ACBAB'`）每章轮换）：
- **A**：左侧文本块（x 130，基线 610）；圆盘和右图（中心 1290，或水平游泳者 1370）；右下角 300 像素的轮廓索引号，不透明度为 20%。
- **M**：A 的镜像（图在 640 处左对齐，文本在 1800 处右对齐）。
- **B**：标题**填充框架**（330像素，颜色`t[1]`/`t[4]`“幽灵”色调，单行适合1760像素）。光盘和人物位于标题“上方”。底部信息栏的 JP 名称为 80 像素，EN 名称为 44 像素，单声道元右对齐。 2 拍球拍运行始终使用 B。
- **C**：一个可擦除的 820 px 实心左面板（`t[0]` 或 `t[4]`），带有 10 % 的 90 px 细线网格及其上的文本块；图案、圆盘和图形位于右侧 (1370)。

**类型**（`demo/fonts/`，全部OFL）：
- 标题：Inter Tight 900，170 px（C 中 150，赛道上 160），字母间距 −0.02 em，使用 `G.fitFont` 自动调整为 820 px。
- 第二语言：Noto Sans JP 900，92 像素 (EN-JP) 或 Noto Sans SC 900（ZH 版本，在 28 px/500 处有一条额外的 JP 行）。
- 元：DM Mono 500 22 px，字母间距 3 px，例如`ATHLETICS   01 / 43`。标签：单芯片（`5×5 · 3×3`、`NEW` 为红色）。
- HUD（每张卡片和章节）：所有四个角均为 DM Mono 17 px（事件线左上角，章节右上角），底部有 **43 刻度进度条**。当前项目是一个高 4 px 的刻度；已完成项目占 75%，其余项目占 28%。

**粮食**：仅在复用时间添加（`noise=c0s=4:c0f=t+u`）。画布本身是干净的。

<a id="motion-as-built"></a>
### 运动，竣工时

- **时间网格**：150 BPM，1 节拍 = 0.4 秒，1 小节 = 1.6 秒。每个镜头都以节拍 (`edl.js`) 开始，姿势中的每个关键动作都落在整数节拍 `u` 上（释放、接触、着陆）。
- **宽松**：`E.oExp`（指数缓出）几乎适用于每个入口； `E.ioExp` 用于鞭盘和擦拭巾； `E.o5`/`E.o3` 用于面板和盘； `E.oBack` 仅用于介绍的第一个点。
- **类型入口**：`G.maskText`将每行从剪辑矩形下方向上滑动（标题超过0–0.5秒，JP行在+0.08秒处，标签在+0.2秒处）。元行类型为（`G.typeText`，无插入符号）。 2-beat 卡将所有计时压缩 0.7。
- **图形组件**：对于前0.42秒（2拍卡上为0.28秒），图形图层被切割成54像素水平带，开始左右交替偏移90-250像素并滑入套准（`stageFigure(..., asm)`）。这与模式的行移位相呼应。
- **背景呼吸**：奇数行向右漂移，偶数行向左漂移26 px/s，加上每行固定的正弦偏移。在章节卡上，每一行 **在第二小节**（节拍 4-7）的每个节拍上跳跃四分之一单元，与鼓同步。
- **章卡**：2行实心带从中心生长（`E.o5`）。一个 330 像素的轮廓章节数字升入其中，标题和 JP 行向上滑动。发际线位于发带的上方和下方。
- **过渡**（`transType`，剪切前 0.12 秒到剪切后 0.26 秒的窗口）：`rows`（6 行交替滑动，用于每章和引言之外），`cols`（8 列下降或上升，在章节后使用）卡片和 2 拍运行）、`slide`（球拍运行：带有薄阴影边缘的推动）、`quarter`（四分之一圆盘从单元角生长，用于结局）、`iris`（从前一张卡片的图形中心打开一个圆圈，带有缩小的环）、`flip`（11×6瓷砖网格翻转）。普通卡旋转 `['quarter','rows','iris','flip','cols'][ci % 5]`。在田径长镜头中，有 **no** 过渡：摄影机鞭子代替。
- **仅在移动的地方进行运动模糊**：`isFast(t)`在过渡窗口中为真，然后`G.renderFrame`在0.5/60的快门上平均5个子帧。静态卡帧渲染一次。

<a id="end-card"></a>
## 端卡

- 卡片上的类型*是*文本层；没有任何多余的东西被烧毁。`pictogram-motion.srt`列出标题卡（介绍行、章节标题、每张卡“01/43田径 — SPRINT / 短距离”，口号，片尾卡），由 EDL 生成`demo/srt.cjs`.
- **双语规则**：EN始终是大标题。第二语言由`?lang=`选择：`ej`将日语放在大第二行（`s.jpBig || s.jp`）中，并删除小JP行；没有`?lang=ej`（页面自己的后备，`scenes.js`）中文大而日文小。除非 `LANGQ=zh`，渲染和静态脚本都会通过 `?lang=ej`，因此发布的影片是 EN-JP 版本。
- **结束序列(示范)**：奶油色片尾卡、红太阳+五色环→**想象一个亚洲/ここで、ひとつに。**（官方口号）→**AICHI-NAGOYA 2026**、日期、五个彩条和片尾字幕→淡入黑色（最后1.3秒）→2秒黑尾音乐响起。
- **信用额度**：我们风格库的示范以“LemoLab × Claude Opus 5.5”结尾。它位于片尾卡上，在五个颜色条下方居中：`finaleScene` 中的 `G.maskText(ctx, 'LemoLab × Claude Opus 5.5', W / 2, 1000, F.mono(24), rgba(G.INK, 0.6), inv(0.6, 1.2, l), { ls: '4px', align: 'center' })`（就在颜色条循环之后）。 片尾卡落地后（就在条形之后）向上滑动 0.6 秒，保持约 3.5 秒并随卡一起淡出。它比日期变更线更安静，因此它永远不会与标题竞争。此签核仅属于本库的示范；用户的影片没有 LemoLab 积分，也没有该卡的副本（当您调整代码时，请从 `finaleScene` 中取出该线）。

<a id="build-notes"></a>
## 构建笔记

```
styles/pictogram-motion/demo/
  index.html      loads fonts + edl.js + engine.js + poses/*.js + scenes.js; exposes window.render(t), DUR, READY
  edl.js          edit decision list: every intro/chapter/card/finale shot with beats, names (EN/ZH/JP), pose, flags
  engine.js       G: easing, rng, palette, grid pattern + motifs, pictogram skeleton, text helpers
  poses/          base.js (pose API + props G.P) + one file per chapter: ath aqua ball combat power nature asia (70 poses)
  scenes.js       intro, chapter card, card layouts A/B/C/M, athletics long take, finale, HUD, transitions, motion blur
  render.mjs      headless-Chrome frame renderer (stills / video, N workers → seg_*.mp4 + list.txt)
  shot.mjs        quick JPEG stills (+ --sheet contact sheet via sheet.py)
  lab.mjs lab.html   pose check sheets; lab.mjs also screenshots cover.html / cover34.html (4:3 and 3:4 posters)
  mux.sh          concat segments → 2 s tail → grain → + music.wav → mp4
  srt.cjs         title-card .srt from the EDL
  music/          music.py (score), export_timeline.cjs (EDL → timeline.json), timeline.json, report.txt
  fonts/          Inter Tight, Noto Sans SC, Noto Sans JP, DM Mono (OFL)
  ref/            official reference images (NOT used by the film, do not publish)
```

所有命令都从 `styles/pictogram-motion/demo/` 运行。 Node 使用存储库的 `node_modules/playwright-core`，Chrome 通过 `core/render/browser.mjs`（剧作家无头 shell 或 `PLAYWRIGHT_CHROME`）找到。 **脚本默认为EN-JP**（`LANGQ=ej`）；设置 `LANGQ=zh` 为中文版本。

```sh
cd styles/pictogram-motion/demo

# 1. Edit → timeline for the music (re-run after every change to edl.js)
node music/export_timeline.cjs                       # → music/timeline.json

# 2. Score (≈30 s; writes music/music_bed.wav, sfx.wav, music.wav, report.txt)
../../../.venv/bin/python music/music.py
grep "shots pass" music/report.txt                  # expect 79/79

# 3. Pose check sheets and stills while working
node lab.mjs stills/lab_ath.png "p=sprint,hurdles,relay&n=8&beats=4"
node shot.mjs 24.8 63.2 104.9 153 --sheet            # EN-JP stills → stills/t_*.jpg + stills/sheet.jpg
LANGQ=zh node shot.mjs 63.2                          # Chinese version still

# 4a. Render — EN-JP (default): 9696 frames → out_ej/seg_*.mp4
node render.mjs video 12                             # 12 workers ≈ 2 min on an M-series Mac; use 2–3 when sharing the machine
./mux.sh                                             # → ../pictogram-motion.mp4 (163.6 s, 9816 frames)

# 4b. Render — Chinese version
LANGQ=zh node render.mjs video 12                    # → out/seg_*.mp4
OUTDIR=out ./mux.sh                                  # → out/pictogram-motion_zh.mp4

# Partial re-render (e.g. only the ending): START/END in seconds, into a separate folder
START=148.1333 END=161.6 OUTDIR=out_tail node render.mjs video 2

# 5. Subtitles and posters
node srt.cjs                                         # → ../pictogram-motion.srt
node lab.mjs stills/cover_ej.png "lang=ej" cover.html      # 2880×2160 poster
node lab.mjs stills/cover34_ej.png "lang=ej" cover34.html  # 2160×2880 poster
```

两种语言版本有何不同：唯一的开关是 URL 查询 `?lang=ej`。 `render.mjs`和`shot.mjs`从`LANGQ`添加（默认`ej`）； `scenes.js` 将其读入 `G.EJ` 并更改第二语言行（介绍标题、计数标签、ON YOUR MARKS、卡片、章节卡、片尾卡）。 `render.mjs` 将 EN-JP 段写入 `out_ej/`，将 ZH 写入 `out/`； `mux.sh` 读取为 `OUTDIR`（默认为 `out_ej`）。画面时间和音乐是相同的。

`render.mjs` 将 JPEG-100 屏幕截图传输到每个工作人员的 ffmpeg (`libx264 -crf 12`) 中； `mux.sh` 以 `-preset slow -crf 14`、60 fps、GOP 120、AAC 320k 重新编码加入的影片，并带有 2 s 克隆尾部，因此音乐的铃声在黑色上播放。

我们遇到的陷阱（有几个与示范的道具有关）：

- **图形环境吃掉了类型。** 水面、坡道、栅栏和网属于图形层并扩散到文本栏中。修复：`stageFigure` 渲染到自己的缓冲区中，并应用 `destination-in` 渐变蒙版 (`{x0|x1|y1, f}`)，将图层在文本区域之前 90–120 像素处淡入零。
- **金色和赭色需要深色字体和深色数字**（`fg #211904 / #1e1409`），并且它们的盘是“较浅”色调的`t[4]`。金色上的奶油色无法形成对比。
- **墨章的光盘在`t[1]`处消失了**。使用`t[3]`作为油墨上的太阳盘。
- **图案画布为大**（每张2520×1260，每张卡都使用一个新种子）。缓存它们，但限制缓存：`G.pattern` 保留大约 10 个条目的 LRU。当 12 个浏览器同时渲染时，无界缓存会快速消耗内存。
- **zsh 循环**：在 `while read line` 循环中，变量不进行字分割。将时间列表传递给 `node shot.mjs` 时使用 `${=line}`。
- **H水平姿势**（游泳）需要将舞台向右移动（`wide`：圆盘位于1370，文本最大宽度700）或手臂交叉标题。
- **官方身份**：示范紧密模仿真实事件的身份。这只有在非官方的同人作品中才可以容忍。由该代码生成的影片必须替换它，请参阅[替换事件元素](#replacing-the-event-elements)。

<a id="engine-reference"></a>
## 发动机参考

<a id="enginejs-windowg"></a>
### `engine.js`（窗口.G）

|应用程序编程接口|它的作用|
|---|---|
|`G.E.{lin,io,o2,o3,i3,io3,oExp,iExp,ioExp,oBack,o5}`|缓动（输入钳位 0..1）|
|`G.clamp, G.lerp, G.inv(a,b,x)`|`inv` = a 和 b 之间 x 的归一化进度，已钳制；用于每个时间|
|`G.rng(seed)`|确定性桑树式 RNG|
|`G.PAL[key]`、`G.CYCLE`、`G.CREAM`、`G.INK`、`G.mix(a,b,t)`、`G.rgba(hex,a)`|调色板和颜色助手|
|`G.pattern(pk, seed, {spread=1, density=0.5, cell=180})`|返回缓存的图案画布（比屏幕宽 3 个单元格）|
|`G.drawPattern(ctx, pat, offs(row)→px, {oy})`|使用每行水平偏移绘制图案（固定 ±1 个单元格）|
|`G.motif(ctx, kind 0–13, x, y, size, [bg, main, sub, accent], rng)`|一个图案化的细胞|
|`G.joints(pose)` → `{hip, neck, sho, head, up, aL, aR, lL, lR}`|来自姿势对象的骨架|
|`G.drawFigure(ctx, J, nearCol, farCol)`|绘制象形图（单位=身高）|
|`G.keyPose(keys, u, loop?)`、`G.lerpPose(a,b,t)`|节拍中的关键帧姿势；各键 `{b, ...angles, e:'easing'}`|
|`G.runCycle(phase, k, {lean})`、`G.walkCycle(phase, k)`|程序步态（循环阶段）|
|`G.fitFont(ctx, text, 'en'/'zh'/'jp', weight, px, maxW, ls)`|缩小字体大小以适应|
|`G.maskText(ctx, text, x, y, font, col, p, {align, ls, dir})`|掩模上滑入口，p 0→1|
|`G.typeText(ctx, text, x, y, font, col, p, {align, ls, caret})`|打字机|
|`G.hair(ctx, x, y, w, col, p, lw)`|发际线擦拭|

**姿势角度约定**：`rot`=全身（正=前倾）； `torso` = 上半身倾斜； `head` = 点头。肢体从“直线向下= 0°”开始测量，向前= 90°，头顶= 180°，向后为负。手臂位于躯干空间，腿部位于身体空间。 `aR2`和`lR2`（前臂、胫骨）绝对在同一帧中，不相对于上段。 R = 近侧（亮），L = 远侧（暗）。 `x, y` 移动臀部。

<a id="pose-definitions-posesjs-contract-in-posesbasejs"></a>
### 姿势定义（`poses/*.js`，`poses/base.js` 中的合同）

```js
POSES.name = {
  pose: (u) => ({...}),            // or keys: [...] + loop: beats   (u = beats since the card started)
  back:  (ctx, J, u, C) => {},      // props/environment behind the figure (unit = body height, origin = hip)
  front: (ctx, J, u, C) => {},      // props in front (ball, racket, bow)
  second: (u) => ({...}), secondX: [dx, dy], secondFace: -1,   // opponent / partner, drawn in C.far2
  fig: { s, x, y },                 // scale/offset inside the stage
  iconU: 0.6,                       // which beat to freeze for the finale icon wall
};
// C = { fg, far, far2, acc, bg, line } from G.colorsFor(pk, discColour)
// props: G.P.ball, G.P.racket, G.P.stick, G.P.ground, G.P.speed (speed lines), G.P.arc (flight arc)
```
使用 `node lab.mjs out.png "p=a,b,c&n=8&beats=4&pal=red"` 检查姿势：每一行是在 `beats` 上 n 个时刻采样的一个姿势。

<a id="edljs"></a>
### `edl.js`

`chapter(id, no, en, zh, jp, palKey)`增加8拍章节卡。 `card(n, en, zh, jp, pose, {beats=4, sub, fam, jpBig, track, water, racket, family})` 添加一项。 `fam: true` 表示大标题是 `sub`，而 `en` 则成为小家族线。 `track: true` 将一张卡放入长镜头中（所有轨道卡必须是连续的）。 `racket: true` 提供带有幻灯片过渡的 2 节拍 B 布局卡。 `palKey 'multi'` 每张卡轮换 `G.CYCLE`。前奏和结局是 `{kind:'intro'|'finale', beats: 48}`。该脚本计算 `b0, t0, dur`，则 `EDL.DUR` = 总节拍 × 0.4 s。

<a id="scenesjs"></a>
### `scenes.js`

`G.renderFrame(ctx, t)` → `frame()` 通过二分查找找到镜头，判断 t 是否在过渡窗口内，将 A 和 B 渲染到离屏缓冲区中并合成，然后绘制 HUD。主要功能：`cardScene`（通过`layoutOf`布局）、`chapterScene`、`trackScene`（`trackCam`、`stationX`、`SPEC`、`RUNNING`）、 `introScene`、`finaleScene`（`GRID 9×5`、`rings()`）、`hud`、`transType` / `composite`、`stageFigure(ctx, poseName, u, C, x, y, scalePx, asm, mask)`、`patBg`、 `multiBg`、`textBlock`、`sun`、`bigNumber`。

<a id="minimal-example--a-new-card-and-a-new-pose"></a>
### 最简单的例子——一张新卡和一个新姿势

```js
// poses/nature.js (or a new poses/xxx.js added to index.html)
POSES.kite = {
  iconU: 1,
  keys: [
    { b: 0, torso: -6, aR1: 150, aR2: 160, aL1: 20, aL2: 40, lR1: 10, lL1: -12 },
    { b: 1, torso: -12, aR1: 170, aR2: 175, aL1: 30, aL2: 60, lR1: 18, lL1: -20, e: 'oExp' }, // tug on the beat
  ],
  loop: 2,
  front: (ctx, J, u, C) => {                     // string + diamond kite, all geometry
    const h = J.aR[2], k = [h[0] + 0.55, h[1] - 0.75 + 0.04 * Math.sin(u * Math.PI)];
    G.seg(ctx, h, k, 0.01, C.line);
    G.poly(ctx, [[k[0], k[1] - 0.12], [k[0] + 0.08, k[1]], [k[0], k[1] + 0.12], [k[0] - 0.08, k[1]]], C.acc);
  },
};
// edl.js, inside a chapter
card(44, 'KITE FLYING', '放风筝', '凧揚げ', 'kite', { sub: 'NEW' });   // n = index shown as "44 / N"; update the total (see below)
```
然后：`node lab.mjs stills/lab_kite.png "p=kite&n=8&beats=4"` → `node music/export_timeline.cjs` →（如果章节移动则更新 `compose()`）→ `node shot.mjs <t>` → 渲染。

<a id="replacing-the-event-elements"></a>
### 替换事件元素

|什么|在哪里|替换为|
|---|---|---|
|活动名称、版本、主办城市、日期|`scenes.js` 372–373、398–407、417、539–541、562–566； `cover.html` 94–114； `cover34.html` 90–113|你自己的标题和日期线|
|口号“IMAGINE ONE ASIA / ここで、ひとつに。/在这里，合而为一”|`scenes.js` 534–536；封面|你自己的两行口号|
|徽章状标记（红太阳+五环，`rings()`，`RINGS`）|`scenes.js` 341–352，前奏 356–375，结局 509–531|原始标记，例如用网格图案构建你自己的形状|
|调色板名称（Jonetsu Red、Kakitsubata Purple、Shinrin Green、Kinshachi Gold、Dento Ocher）和十六进制|`engine.js` `PAL`（第 45-51 行）；名称印在章卡上 (`scenes.js` 246)|定制的五色调集，每个色调有 5 个色调；保持浅色调的 dark-fg 规则|
|项目列表，计数“/ 43”，43 个 HUD 刻度，“469 个事件/16 天”，结局“2026”图块|`edl.js`； `scenes.js` 118, 184, 414–418, 512, 570|您的列表和数字（源自 `CARDS`，而不是硬编码 43）|
|配乐中的章节布局|`music/music.py` `EXPECTED` + `compose()`|重新组合的部分|
|官方参考图片|`demo/ref/`|绝不发货；收集您自己的参考资料|

保持语法：带有行移的网格图案、象形图运动员、双语蒙版幻灯片类型、带有索引和进度的 HUD、带有节奏阶梯的节拍锁定卡、一个长镜头以及图标墙结局。
