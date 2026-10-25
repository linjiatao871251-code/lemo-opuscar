<a id="1930s-rubber-hose-cartoon--our-demo"></a>
# 1930 年代橡胶软管卡通 — 我们的示范

众多例子中的一个。请勿重复使用其故事、弧线、镜头、道具或时间安排。

示范：*咖啡杯追逐*（50秒）·`rubber-hose.mp4`·来源在[`demo/`](demo/)


<a id="story--structure"></a>
## 故事与结构

刚醒来的餐杯本身就有味道：苦！它在厨房（柜台、瓷器柜、水槽）周围追逐失控的方糖。当立方体即将被吸进下水道时，马克杯将其橡胶软管臂伸到漩涡周围，将其捞出，然后悲伤地将其放走；立方体自己跳进杯子里。咖啡变甜了，整个厨房都随着乐队一起跳舞。一位 20 世纪 30 年代的广播体育播音员称这场追逐就像一场赛马（“他们出发了！”）。

弧线（40-55秒）：勾住第一帧（跳动的标题字母，乐队的打击）→一个小小的愿望→在3个不断升级的场景中进行追逐，每个片段一个视觉笑点→危险→伸展→死一般的寂静→安静、友善的转身→释放：整个世界都在跳舞→虹膜随着笑点而消失。一位英雄，一个目标，一回合。

老导游要求至少有四种原生能力中最强的三种，并建议将任何主题改编为**追逐或在一个热闹的地点**（厨房、办公室、玩具店、工厂）进行表演，配角由5-8个活体物体组成。这就是示范的形状，不是风格的规则。

风格特有表现手法花费：
- **一切都在节奏中呼吸**：厨房是一个角色；在高潮时，整个世界同步跳舞，包括墙壁（回报镜头）。
- **米老鼠**：板楼梯是木琴；小人物用上升的木琴八度攀爬，大人物则用大号四分音符攀登。
- **胶管拉伸**：转折点；马克杯的手臂围绕着漩涡延伸，并在一个完整的镜头中落入下水道。
- **影片是一个物理对象**：标题卡像窗帘一样卷起来；角色的手套拉动虹膜关闭。

<a id="shots"></a>
## 镜头

|打|摄影机|
|---|---|
|开幕|带有旋转旭日纹的标题卡；字母每次跳动都会跳成波浪状；卡片像窗帘一样卷起，露出套装|
|建立|**全舞台，锁定**，视线水平。布景看起来就像一个舞台；柜台上排列着道具|
|反应搞笑|硬切到脸部特写（早期唯一的大脸镜头）|
|追赶|**运货盘**与跑步者并肩，轻松起停；目标道具在搞笑之前进入画面|
|垂直固定件|不是远处的整个场景：每个登山者都以 **中景** 跟随（角色 ≈ 1/4–1/3 的框架高度），因此每个音乐步骤和板的弹跳都读取；在登山者之间切换；然后随着坠落而向下倾斜|
|危险|角度稍高，危险一目了然；**一枪未断**通过大延伸|
|安静转弯|表现媒介两个-镜头，然后英雄的 **后退** 在背景中走开，而另一个角色在前景中很大（在前景柜台上）|
|高潮|从特写镜头拉回 **中满** 镜头（不是很宽：脸部必须阅读）：英雄在中间，活体道具在后面的柜台上，**前景一排较大的舞者** 在较近的柜台上。按杠铃移动 2-3 步（摇摆 → 踢腿 → 集体下蹲和弹跳），然后 **每个人在最后一个节拍上保持 ta-da 姿势** 并保持在虹膜上|
|结束|艾里斯接近英雄；角色的手套将其关闭|

跳跃前的犹豫节拍，就像定格动作一样：蹲下（按住）→眼睛看着另一个角色的背部（按住）→眼睛向上看向目标（按住）→背部→向上+微笑→小跳→跳跃。每扫一眼八分音符，都会伴随着木刻的滴答声，而摄影机会慢慢推入。音乐因“锁定眼睛”的节拍而停止，一切都冻结了，包括背景呼吸。

<a id="score-structure"></a>
## 配乐结构

原始大频段配乐（`demo/music/score.py`、VSCO 2 CE / VCSL 样本来自 `core/audio/sampler.py`、班卓琴来自 `pluck.py`）。 **144 BPM，4/4 → 1 节拍 = 10 帧**，1 小节 = 1.667 秒，28 小节。一首原创的 4 小节切分音主题，为标题、追逐、一段缓慢的单簧管独奏版本带来温柔的节拍，以及一段调性变化的全乐队副歌为高潮。

在锁眼节拍、堵嘴前的悬念处以及伸展后立即停止整整 2 个节拍的停顿（包括混响尾音）；每一个恶作剧都充满了刺痛；每次伸展/滑动/下降时都会发出滑动哨子；木琴*就是*板。投影仪的咔嗒声是寂静中唯一的声音。

拟音特定于此影片（全部合成）：瓷器 = 硬非和谐分音 (~2.7 / 4.2 / 6.3 kHz) + 微小瞬态；厚杯子 = 较低、较暗淡的部分；糖=高木版+稀疏的嘎吱声；时钟 = 18 Hz 锤子上的两个铃；烤面包机 = 咔哒声、八分音符滴答声、铃声 + 弹簧“boing”；水 = 过滤噪音 + 上升的尖峰、排水水滴、气泡床；橡胶 = 通过带通的锯齿嘎吱声。

声音：一位老广播播音员将这一行动称为赛马（Kokoro `bm_lewis`，速度 1.0），7 句简短的台词（“早上七点，朋友们！”……“晚安，朋友们！”）。链：HP 260 Hz / LP 4.6 kHz，tanh 饱和度，短空间，压缩。音乐在声音下降低了约 8 分贝。光通：带限 110 Hz–6.2 kHz，wow 0.6 Hz，颤振 7 Hz。

<a id="palette--props"></a>
## 调色板和道具

- 灰色渐变：纸`#F1EEE6`·浅`#C8C5BC`·中`#9A978F`·暗中`#6B6963`·暗`#3B3A37`·墨水`#0E0D0C`·字符白`#FCFBF7`。
- 对比修复（第一个风格定帧太平坦）：墙壁`#8C8981`，瓷砖`#A29F97`，橱柜`#66635D`–`#7C7972`；最终复合材料中的 `contrast(1.14)`。
- 墨水轮廓在屏幕空间中 6 像素； 280 px 角色上的四肢 13 px； 影片损坏：门编织 ±1.2 px，罕见的 3-6 px 跳跃，晕影 0 → 62 % 拐角黑色，每次切割 3 px 垂直跳跃，0.55 px 模糊；鲍勃步行 10 像素（悲伤步行：第 34 步，鲍勃 4），倾斜跑步 0.24 rad。
- **马克杯**（英雄）：一个矮胖的餐杯，白色瓷质，边缘有两个黑色细环，里面装满了黑咖啡（黑色椭圆+白色新月突出）；脸在身上，大眼睛，小黑鼻子，大嘴巴；后面有一个手柄，像一条小尾巴。它的**蒸汽**承载着这样的心情：慵懒的波浪/苦涩的锯齿/直线上升的警报/枯萎的下垂/心。
- **方糖**：一个真实的投影3D立方体，具有轻微的自上而下视图（仰角约0.26弧度），面通过仿射变换映射到正面。
- **厨房铸件**（生活道具，全都喘气相）：锅、钟、烤面包机、盘子、窗帘。背景图案：带有小钻石的条纹壁纸、方形瓷砖、镶板橱柜、黑白格子地板、吊灯。两个缓存背景：厨房；橱柜+水槽。
- 故意不从参考文献中学习：没有现有的角色（猫、女孩、小丑），没有标题卡或主题副本，没有时代种族漫画；杯子的整个主体就是杯子（没有人体躯干，没有吸管，没有短裤），与*Cuphead*的设计不同。

<a id="titles--subtitles"></a>
## 标题和副标题

- 字幕：“播音员的标题卡”：铭牌 `rgba(12,11,10,.92)`、白色双线边框、点环角饰和 1930 年代带状麦克风的小图标； IM Fell English SC 36 px，纸白色；默认情况下，底部位于 y ≈ 986，当动作较低时，顶部。每张卡≥语音+0.6秒。
- 标题：Shrikhand，白脸，14% 墨水轮廓，右下墨滴阴影，字母在旋转旭日的节拍上以行波跳跃； Limelight 帽子中的子线。

<a id="end-card"></a>
## 端卡

同样的太阳纹，波浪边标志，写着“The End”，风格名称，`LemoLab × Claude Opus 5.5`，底部有小信用线；它以黑色虹膜打开。 “LemoLab × Claude Opus 5.5”签名仅属于该库的示范；用户的影片没有 LemoLab 积分，也没有该卡的副本。

<a id="build-notes"></a>
## 构建笔记

```
styles/rubber-hose/demo/
  toon.js    constant-width ink + line boil + affine stack      film.js   4:3 gate, weave, flicker, scratches, vignette
  chars.js   mug & cube rigs, pie eyes, gloves, shoes, steam     cast.js   living kitchen props (all take a breath phase)
  bg.js      cached watercolor backgrounds (kitchen, cupboard+sink)
  story.js   144 BPM bar grid, VO times, subtitle cards, shots, key moments, music cues  (single source of truth)
  scenes.js  every shot: camera, props, acting            events.js  foley event list → events.json
  ui.js      title lettering, announcer title card        sheet.js   model sheets (?mode=sheet / ?mode=kitchen)
  music/score.py  original big-band score (VSCO 2 CE / VCSL samples via core/audio/sampler.py, banjo via pluck.py)
  mix.py     foley synthesis + radio-voice chain + ducking + optical-track aging
  build.sh   one-command rebuild (≈9 min, mostly TTS/whisper/sample loading; frames render in ~50 s)
```

1. 先写条形网格（`story.js`），然后写音画节拍对照表； 配乐到它（分叉子代理可以从 `story.js` + 提示列表并行写入 `music/score.py`）。
2. Model sheets: `node demo/tools/still.mjs demo 0 --q 'mode=sheet&w=2880&h=1620' --w 2880 --h 1620`.
3. `core/tts/tts.py lines.json voices` → `core/tts/asr_check.py`.
4. 评论：`core/render/still.mjs demo --range a:b:1` + `core/render/sheet.py`（两个完整通道），以及 1/12 的关键动作节拍上的框架条。
5. `node core/render/events.mjs demo` → `python music/score.py` → `python mix.py`.
6. `node core/render/video.mjs demo --fps 24 --workers 3` → `sh core/render/mux.sh out/video24.mp4 mix.wav rubber-hose.mp4 24 3` → `python demo/tools/final_asr.py rubber-hose.mp4`.

或者简单地称为 `sh styles/rubber-hose/demo/build.sh`。

与示范相关的陷阱：
- **Kokoro 在省略号后将“苦”听成“更好”** (`is... bitter!`)。 “天哪，这咖啡苦吗？”通过。轻声检查每一行；还要检查最终的 mp4（耳语写“7am”/“他们是”：比较之前进行标准化）。
- 立方体在纯正视图中读作一个高盒子：标高~0.26，并有轻微的 3/4 旋转表达。
- 板木琴和舞蹈高潮的远距离镜头杀死了两个笑点：将它们表现媒介 / 表现媒介射满。
- 一条踢腿被拉到杯身后面，被把手隐藏起来：向外踢过剪影。
- 在摄影机的一个位置，杯子的头部“长”出一个罐子：检查每个镜头的最终帧。
- 过高的跳跃弧线离开了框架；在摄影机变焦时将弧线保持在门内。
- `sfx` 风格的不同长度的剪辑 → numpy 广播错误。将剪辑放入固定长度缓冲区（`mix.py` 中的 `seq()`）。
- zsh：`echo =====` 失败（`=word` 扩展）并且 `timeout` 在 macOS 上不存在。
- JS: `-x ** 6` 是语法错误；写`-(x ** 6)`。
