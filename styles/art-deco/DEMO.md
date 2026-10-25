<a id="art-deco--our-demo"></a>
# 装饰艺术 — 我们的示范

众多例子中的一个。请勿重复使用其故事、弧线、镜头、道具或时间安排。

示范：*星光酒店的午夜*（58.4 秒）·`art-deco.mp4`·来源[`demo/`](demo/)


示范的原始简介：装饰艺术风格的 40-60 秒影片；导演决定故事、镜头、配乐、声音和标题。

<a id="story--structure"></a>
## 故事与结构

1930 年除夕夜，行李员皮普必须在午夜之前将一封密封的信件送到屋顶。这是在一个宏伟的地方执行的一项小而紧急的差事。机械障碍（电梯故障）将恐慌转变为决心。节奏变化的上升中音（楼梯=查尔斯顿）。高潮前真正的寂静（时钟敲响十二点，乐队停止，字母翻滚）。高潮是数光：午夜的十二下=星光的十二个字母一一点亮。

**音乐就是剧情：**信里拿着乐队的新歌；在指挥打开之前，只能听到主题的片段，第 13 拍是第一个完整的陈述。最后的回声：抬头看着黑暗标志的英雄现在站在亮着的标志里面；一个按钮堵住了循环（电梯在运行中发出叮当声——太晚了）。

这种风格的固有力量是如何在这个故事中发挥作用的：

|原生电源|示范用途|
|---|---|
|中心轴|每个过渡都是一扇门：标题拱门裂开，楼梯门爆裂，厨房旋转门砰地一声，电梯门关闭到片尾卡。|
|计数光|灯泡标志一个字母一个字母地亮，每个铃一个字母。|
|机器对称性|头顶上是巴斯比伯克利分校：扇形从八分音符开始变成旭日形，然后锁定在钟面上。用作高潮后的释放。|
|拨号盘和数字|楼层指示器、钟面、楼层徽章、年份徽章：1930 年 11 点 55 分，第 30 层，讲述了没有旁白的情节。|
|时代电台|播音员作为旁白，在声学空间（街道喇叭→桌上收音机→楼梯间扩音器→现场麦克风）中移动，以便观众听到英雄越来越接近声源。|

我们用来调整它的方法（对于这个示范）：找到门槛（门），截止日期（时钟），计数的显示（标志，楼层数字），以及结局解锁的东西（一首歌）。

<a id="shots"></a>
## 镜头

|打|摄影机|
|---|---|
|开口（3S钩）|单个金点爆炸成射线和阶梯式拱门；缓慢 6% 推动。标题栏在管弦乐队的热门歌曲中绽放。|
|过渡语法|**对称分体**：输出框架成为两个门扇，铰接在从接缝处摆动打开的边缘（拱门、楼梯门、厨房门）。旋转门是它的旋转门（玻璃翼擦拭）。 影片关闭时，电梯门在带电的镜头上滑动关闭。|
|建立|极度低角度的卡桑德尔倾斜，从塔顶的黑暗标志向下倾斜到街上的小英雄：目标、难度和黑暗标志（结局的设置）一举两得。|
|障碍|表现媒介上牌匾掉落；沉默中，他拉直帽子，缓慢地推了一下他的脸。|
|签名1|楼梯间是**建筑剖面**：和他一起上升，拉出直到整个塔是一个剖面图，他是一个带有速度线的红点，推回“30”地板奖章，匹配切割到厨房里旋转的银托盘。|
|沉默|塔钟分针插入 XII；这封信以慢动作翻滚着，越过黑色的字母。|
|高潮|十二个铃：接住（ECU手套）→指挥（撕开封条，插入配乐，警棍向上）→标志的低斜线，字母每次敲击一个灯→特写，英雄身后最后一个T灯，金光掠过他的脸。|
|签名2|**Busby Berkeley**：8个舞者以八分之一音符打开扇子时的倾斜高角度，然后笔直在头顶上，8向镜像并缓慢旋转；球迷们锁定在十二号处有两只金色指针的钟面。|
|规模揭示|从标牌拉回整个塔楼、城市和烟火（呼应开场倾斜）。|
|结束|电梯门滑关过带电镜头； 片尾卡牌匾位于紧闭的门上。|

表演节拍：电梯按钮按三下（一次、两次、混搭）；投掷有一个卷起、释放和险些跌倒在栏杆上的过程；一小节后，被托盘撞落的帽子又落在了他的头上，而他甚至没有看。在开头，金线以单簧管滑奏的速度增长（慢→快），落在悲观的打击上。所有字母点亮后，16 分音符追逐贯穿整个标志。

<a id="score-structure"></a>
## 配乐结构

- **得分第一**：`timeline.js`是唯一的事实来源（116 BPM狐步→16节拍加速到138 BPM Charleston→停止→116网格上的12个铃声→D♭中的歌曲）。 `tools/cuecheck.py` 对照 `music/score.json` 检查 53 个图像同步点（最大偏移 0.5 ms）。
- **使用的编曲**：钢琴主音（火蜥蜴），单簧管（低音颤音+两个八度的滑奏拉开帷幕），弦乐（颤音床，向上冲），静音小号注释（匾额上的“哇哇”），查尔斯顿的画笔→木棍，行走的比兹贝斯，管钟(B♭) 午夜，harp/piano 滑音为每位乐迷，长号+萨克斯为最后的副歌。
- **种植主题**：标题=钢琴小节1； street = 静音小号尝试了两个小节并被切断；厨房=英雄吹响了前四个音符；结局=完整歌曲。
- **远程自动化**：乐队在30楼演奏，因此在街道上为2.5 kHz低通，在大厅为1.2 kHz（穿过地板），在他爬上时开放，在屋顶上为全频和干燥。
- **五个空间的播音员** (Kokoro `bm_fable`)：街道喇叭（带通 320–3.8 kHz、软驱动、拍击回声）→ 桌面收音机→ 楼梯间 PA（长混响）→ 厨房收音机→ 现场麦克风（全频）。严重的喇叭失真使完整混音中的“距午夜五分钟”变得难以理解，因此驱动器被降低。
- **Foley使用**：黄铜按钮点击声，青铜牌匾叮当声+链子嘎嘎声，八分音符上的铁楼梯踏板，大理石脚跟，银色托盘，木制平开门+弹簧声，纸颤动，手套拍打，刀开关“块”+每个字母的细丝嗡嗡声，追逐的继电器滴答声，烟花哨声。
- **段落**：在“故障？！”之后只有大厅的时钟滴答两声（下一个声音：查尔斯顿军鼓）；塔钟敲响十二后，只有风声和飘动的字母（下一个声音：第一个钟声，影片中最重要的声音）；十二点钟后屏住呼吸一拍（下一个：合奏）。
- **J/L 切割**：拱门打开前的无线电调谐噪音； “出了故障？！”的回声。滚上楼梯间；厨房收音机在楼梯间启动；屋顶风从厨房门前进入酒吧；铃 12 的尾部响起合奏。
- 混音：人声下的音乐回避 ≈ −9 dB（现场播音员下的 −6 dB），床位 −6 dB； −14 LUFS，颗粒 3。

<a id="palette--props"></a>
## 调色板和道具

- 地面：暖黑`#0d0b09`，亮漆`#060504`；夜空`#0a0e16`→地平线翡翠`#10231f`。
- 金色：`#6F5220`（阴影）→ `#C9A24B`（基础）→ `#F3D98B`（光）→ `#FFF4D2`（镜面）。
- 口音：酒红色`#8E1B2E`（英雄制服，唯一大饱和区域），翠绿`#1D6B57`（风扇，门板，夜晚），象牙色`#F2E8D5`（字母，手套，地毯）。
- 场景：7楼单点透视大堂；从下面看两点透视的屋顶标志，有一个小针孔摄影机。
- 笔尖：7头高，锥体流线型，刻面漆面；剪影标志：倾斜的药盒帽+下巴带，V形黄铜纽扣，密封的信始终在手中。
- 其他道具：“OUT OF ORDER”牌匾、塔钟、灯泡标志“星光”、售票员和配乐、拿着银托盘的服务员、8 个拿着翡翠扇子的舞者、烟花。
- 参考剧照（由 `build.sh` 重建，与影片相同的渲染器）：[`demo/stills/modelsheet_v2.jpg`](demo/stills/modelsheet_v2.jpg)、Pip 的角色设定表（7 头比例上的角色转面图、轮廓检查、六个表情、关键姿势、调色板样本、信件）； [`demo/stills/kit_v2.jpg`](demo/stills/kit_v2.jpg)，组件套件（标题栏、数字和时钟、旭日、拱形框架、图案、灯泡选框、字幕卡），每个都标有其引擎调用； 风格定帧 [`demo/stills/frame_v2_lobby.jpg`](demo/stills/frame_v2_lobby.jpg)（模式7层的一点大厅）和[`demo/stills/frame_v2_roof.jpg`](demo/stills/frame_v2_roof.jpg)（两点视角下方的灯泡标志）。

<a id="titles--end-card"></a>
## 标题 & 片尾卡

- 字幕卡扬声器图标：播音员的金丝带麦克风，英雄的酒红色药盒帽。
- 标题：《午夜/星光酒店》，位于阶梯拱门上方的金色标题栏、1930 年钻石年徽章、新年前夜标签。
- 片尾卡：关闭的电梯门上的漆牌：标题、装饰艺术、LEMO-OPUSCAR、“LemoLab × Claude Opus 5.5”、资产积分。此签核仅属于本库的示范；用户的影片没有 LemoLab 积分，也没有该卡的副本。

<a id="build-notes"></a>
## 构建笔记

```
styles/art-deco/demo/
  timeline.js      tempo grid + all sync points (single source of truth) → tools/dump_timeline.mjs → timeline.json
  engine/          deco.js (palette, gold, gline, airbrush, motifs, drawShape) · type.js (title bar, digits, badges, dial, clock, subtitle card)
                   bulbs.js (any text → bulb sign, lighting patterns) · cam.js (pinhole camera + card transforms)
  chars.js         Pip (FK rig, 4 views, 8 faces, pose library, run cycles), conductor, waiters, dancers, the letter
  scenes/          lobby.js (one-point + mode-7 floor, doors, plaque) · roof.js (two-point sign) · tower.js · stairs.js
  shots_*.js       one function per shot: shot(g, t)       film.js   shot list, transitions (split / revolve / close), subtitles
  frames.js        model sheet, component kit, style frames, ?scene=frames.shotTest&shot=<name>
  music/score.py   original score → score.wav + stems + score.json      mix.py   voices in 5 spaces + foley + beds + ducking
  tools/           cuecheck.py · subs.py · pitch.py · dump_timeline.mjs
```
1. 先写出节奏网格和cue表；将它们交给音乐分代理并并行绘制。
2. 构建引擎和英雄角色设定表，然后每个位置一个场景，然后每个镜头一个函数。使用 `?scene=frames.shotTest&shot=<name>` 查看单个镜头。
3. `sh demo/build.sh` 重建一切：时间轴 → TTS → 音调 → Whisper 语音识别 → 配乐 → 提示检查 → 混合 → srt → 渲染（约 15 秒，4 个工作人员处理 1401 帧）→ 复用器（−14 LUFS，颗粒 3）→ 剧照。
4. 使用 `still.mjs --range 0:58:1` + `sheet.py` 以 1 秒的间隔进行查看，然后以 0.15–0.2 秒的速度对每个关键操作进行帧条带。

与示范的道具相关的陷阱：
- 向片尾卡的第一次过渡是将电梯门滑入平坦的棕色“内部”，其读作是一个空白框架；现在只画了叶子，结束了现场镜头。
- 开局（黑底金点）绊倒了`blackdetect`；背景旭日楔形和辉光被提升。
- 钟镜头中 1/4 帧高度处的点对于情绪峰值来说太小；最后一个钟声有一个特写。
- 三位数的十六进制将翡翠扇子变成了蓝紫色。

<a id="engine-reference"></a>
## 发动机参考

所有绘图都是Canvas2D，在`t`中是确定性的。从 `demo/engine/` 导入。

**deco.js**
|功能|目的|
|---|---|
|`C`|调色板 (`ink black night gold0 gold1 gold2 goldHi ivory emerald burg plum skin bulb…`)|
|`goldGrad(g, x0,y0,x1,y1, {sheen, hot, tint})`|带状金属梯度；动画 `sheen` −0.2→1.2 进行轻扫|
|`gline(g, pts, {w, part, closed, glow, double, sheen, alpha, color})`|雕刻的金色钥匙线； `part` 0→1 取上； `color` = 单色例外的任意十六进制|
|`airbrush(g, pts|Path2D, {base, dark, light, dir, rim})`|硬边喷枪填充|
|`sunburst(g, cx, cy, {rays, r0, r1, mode:'lines'|'wedges', a0, a1, rot, part})`|放射状背景|
|`stepArchPts(cx, base, w, h, {steps, crown})` / `archFrame(g, cx, base, w, h, {rings, gap, fill, burst, part})`|金字形神塔拱门和拱门框架|
|`fan`、`fishScale`、`chevrons`、`sparkle`、`speedLines`、`glow`、`beam`、`vignette`|主题库|
|`drawShape(g, pts, {color, halo, trail, glints, part})`|**any 装饰风格路径**：喷绘金色（或 `color`）填充 + 金色键线 + 可选的旭日光环、速度线轨迹和闪光|
|`starPts(cx, cy, r, k, rot, n)`|四点星轨|

**type.js**：`goldText(g, text, x, y, {size, font, track, sheen})`·`titleBar(g, text, cx, cy, {p, out, size, sub, wings})`（动画in/out）·`decoDigits(g, '11:59', x, y, size)`·`yearBadge(g, '1930', cx, cy, r, {p})`· `floorMedallion(g, '30', cx, cy, r, {sub})` · `dial(g, cx, cy, r, value, {labels})`（半圆楼层指示器，值0..1） · `clockFace(g, cx, cy, r, {h, m, s, roman})` · `subtitleCard(g, text, {p, out, speaker:'radio'|'boy'})`。

**bulbs.js**：`buildSign(text, {font, size, spacing})`（任何文本→字形骨架→均匀间隔的灯泡，缓存）·`drawSign(g, sign, x, y, scale, {lit, channel, color})`·`litAll(v)`·`litSequence(t, times[], {flash, chaseFrom, chaseSpeed})`（字母i在`times[i]`，然后追击）。

**cam.js**：`makeCam({x, y, z, f, yaw, pitch, roll})` → `{P(X,Y,Z), scaleAt(X,Y,Z)}` · `cardTransform(g, cam, TL, TR, BL, w, h)`（将平面卡映射到 3D 四边形上）。

**chars.js**（示范字符）：`drawFigure(g, {x, y, s, view:'side'|'q'|'front'|'back', face, ...pose})`·`POSES`、`FRONT_POSES`、`lerpPose`、`runCycle(phase)`、 `runFront(phase)`·`drawDancer`、`drawDancerTop`、`envelope`、`clef`。

**一种颜色。** 要使一个元素保持其自己的颜色，请传递 `color` — 它用于填充、键线和发光，而其他所有内容都保持金色：

```js
import * as D from './engine/deco.js';
import * as B from './engine/bulbs.js';

// a warm-orange four-point light with a short cursor tail, drawn the Art Deco way
D.sunburst(g, 960, 540, { rays: 72, r1: 1400, mode: 'wedges' });
D.drawShape(g, D.starPts(960, 540, 120, .22), { color: '#D97757', halo: 1, trail: { ang: Math.PI, len: 420, n: 4 } });

// a bulb sign that lights letter by letter, in the same orange
const sign = B.buildSign('LEMO', { size: 260, spacing: 20 });
B.drawSign(g, sign, 560, 700, 1, { lit: B.litSequence(t, [0, .5, 1, 1.5], { chaseFrom: 2.5 }), color: '#D97757' });
```
