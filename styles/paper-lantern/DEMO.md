<a id="paper-cut-lightbox--our-demo"></a>
# 剪纸灯箱——我们的示范

众多例子中的一个。请勿重复使用其故事、弧线、镜头、道具或时间安排。

示范：*一个月饼的相思·月饼的向往*（121.8秒）·`paper-lantern.mp4`·来源在[`demo/`](demo/)·引擎：three.js 0.170（WebGL，SSAA 2×，VSM软阴影，自定义 DoF + 布隆合成器）、Canvas2D 绘制的纸层、无头 Chrome 帧捕获。


**示范旁白为普通话** (edge-tts `zh-CN-XiaoxiaoNeural`)，配有中文字幕。库默认为英文Kokoro（`core/tts/`）； “配乐结构”和“引擎参考”显示了如何切换。 示范运行2分钟； 45-120秒都适合这种风格。

**语音许可异常。**示范的旁白是用微软的Edge神经TTS（通过开源`edge-tts`客户端）生成的，其重新分配音频的条款尚不清楚，因此`paper-lantern.mp4`的语音轨道是**不在风格库的 CC BY 4.0 许可证**（针对示范影片）的范围内。我们计划用 Kokoro 重新配音。在您自己的影片中，使用Kokoro（`core/tts/`）或您有权使用的声音；仅保留 `tts.py` 作为时序草图。

<a id="story--structure"></a>
## 故事与结构

影片在桌子上的真实灯箱上打开并推入其中。箱腔为**0.56×0.33 m，深0.16 m**。 影片的结尾是 **现实世界**：黑暗房间里的一张胡桃木桌、木制框架中的发光灯箱、一套茶具和一盘由盒子溢出的灯光照亮的真正月饼。第一个镜头从房间推入盒子；最后一个拉回来。

示范如何使用表现媒介的力量：

|原生电源|故事运用|
|---|---|
|**灯亮**|开口实际上就是打开灯：月亮，然后是远处的层，然后窗户一一亮起来。 “灯亮了”=一个故事的开始，一个家，有人在等待。|
|**深度 = 距离**|层层叠叠的山川、河流、城市让“距离”可见。旅程、渴望、“远方”的故事都是本土的。|
|**剪影**|人物是带有一些关节部分（手臂、袖子）的黑色剪纸。不露面的人物与每个人一样阅读——适合民间故事、家庭、节日。|
|**视窗**|明亮的窗户，里面有剪影，是这种风格最强烈的形象。两扇明亮的窗户共享一个月亮是示范的论文镜头。|
|**纸质文字**|标题、信件和诗歌也是纸质的：在切条上竖写毛笔书法，一栏一栏地显示，并盖有红色印章。|
|**盒子本身**|最后拉到真正的桌子上说“这是一个纪念品/一个在家里讲述的故事”。|

**故事形态（在示范中得到证明）：**房间→灯亮→推入盒子，标题→起源（奶奶的厨房，压月饼）→一点文化（明代卷轴）→缺席（一个空座位）→旅程（火车穿越层层山脉，途中讲述一个神话，一个盒子经过另一条路） → 到达远城 → 信 → **转折：另一个盒子走向另一条路**（相互渴望——两窗一月） → 一首古典诗 → 从盒子里拿出“中秋快乐”。

适应任何主题：找到**两个地方**和**一盏灯**他们共享（一个月亮，一座灯塔，一扇窗户）。将每个地方构建为层堆栈；在它们之间构建一个旅行序列；结束时两者同时点亮。

<a id="shots"></a>
## 镜头

|打|摄影机|
|---|---|
|开幕|暗箱上的房间宽 (z 1.45) → 灯亮 → 7 秒缓入出将框架推至 z ≈ 0.56，然后继续爬入。焦点从前层拉到村庄。|
|箱内镜头|近正面、慢速移动车 in/out (`aim(cam, [px,py,pz, tx,ty,tz], t)`)、手持式微漂移 `hand ≈ .0006 m`。光圈 12-26（在 `post()` 中），聚焦于故事层，使前景芦苇和后山柔化。|
|自上而下插入|月饼压榨机和打开的礼品盒为镜头，为平面自上而下的叠层（相同的引擎，不同的设置）。|
|火车|横向移动：图层以与深度（视差）成比例的速度滚动。|
|结束|推入盒子内，然后拉回桌子上（z 0.5 → 1.08），茶具进入画面，标题“中秋快乐”淡入盒子内，其下方有字幕，1.2 秒淡为黑色。|

示范中内置的运动：

- **一切都像纸一样移动**：层滑动（x/y），围绕枢轴旋转（`ax/ay`锚点=关节），沿着一个轴从0开始缩放（“写出”），或者点亮。没有挤压和拉伸，没有变形。
- **关节人物**：身体片+固定在肩部的独立手臂片（`GRAN_SHOULDER`、`GIRL_SHOULDER`、`people.js`中的`SUSHI_SHOULDER`）；仅动画 `rotation.z`。
- **灯光线索是大动作**：S01中的灯亮顺序——月亮（0.5–3.2秒）→天空→每层半透明度交错0.42秒→主光→窗户→灯笼闪烁（`1 + .06·sin(7.3t)·sin(3.1t)`）。
- **文本显示**：纸条从其锚定边缘生长（`s13_note.js`中的`reveal()`缩放网格*和*纹理重复，因此字形不会被压扁），与口语同步。
- **硬动作击中低语单词时间**：木模猛击「啪」(`E.word('L04', 13)`)，「圆」字在其上闪烁，光弧从「互」长出。
- **过渡**：0.5–1.2 s 在镜头 (`in: { type: 'dissolve', dur }`) 之间溶解，存在 `iris` 模式（从 `center` 开始的圆形擦除）。标志性过渡是 **n 近平面吉祥云幕**（`s17_sushi.js` 中的 `cloudCurtain()`）在镜头的最后 1.2 秒内关闭并在下一个时打开 - 两半必须在其前边缘完全相遇。

<a id="score-structure"></a>
## 配乐结构

**语音（示范，普通话）：**`edge-tts`，语音`zh-CN-XiaoxiaoNeural`，速率`+10%`，音高`-2Hz`（`demo/tts.py`）；每行`rate`覆盖`script.json`（L01 `+5%`，引用字母`+2%`，诗L23**`-12%`**，结束行`-6%`）。输出修剪为峰值的 2%（20 ms 前滚，120 ms 尾部）→ 48 kHz 单声道 `vo/<id>.wav` + `vo/dur.json`。
- **多音字符**：通过`say`字段输入TTS同音字，并保留字幕的真实文本：「相思的"相"」→ `say: 原来，相思的香，是互相的香。`（TTS否则读xiàng）。
- **证明**：`demo/asr.py`（faster-whisper**中等的**，zh）每行打印OK/DIFF；同音异义词或数字的 DIFF（八月十五→8月15，她→他）很好——听其余的。
- **字计时**：`demo/words.py <ids…>` → `vo/words.json`（耳语字时间戳）。 镜头通过 `E.word(id, k)` 读取它们； **k 是一个耳语标记索引，而不是字符索引**（耳语组“我们”作为一个标记）——打印列表并计数。

**Voice（英文，库默认）：** 用 `{id, text, voice, speed}` 写入 `lines.json`，运行 `core/tts/tts.py`（Kokoro，例如 `bf_emma` / `af_heart`，速度 ≈ .9）进入`demo/vo/`，然后是 `core/tts/asr_check.py`，其中写入 `vo/dur.json` 和兼容的 `vo/words.json`（英文单词索引）。将相同的ids/text放入`script.json`中。有关字幕分割更改，请参阅引擎参考下的“切换到英语”。

**音乐：**Kevin MacLeod —**“涟漪”**（古筝，0→~37秒）移交给**“女笛”**（笛子+弦乐） 4.5 秒交叉淡入淡出；均为 CC BY 4.0 (incompetech.com)。交接是向后解决的，因此女笛自己的 70 年代浪潮落在了这首诗上：`T_FLU = C.L23.at − 70 + .3`。 Nu 长笛相对 -3.3 dB。 2 秒淡入，3 秒淡出。为什么是这些：五声音阶，无鼓（打击乐能量 < 0.02）——librosa 编号为 `demo/music/analysis.json`。

**Mix (`demo/mix.py`)：**语音 → 下采样包络压缩器 (−22 dB, 3:1) → HP 70 Hz → RMS −18 dB；语音下音乐 RMS −27.5 dB，**5.5 dB 闪避 **（0.25 s 平滑包络）；程序拟音在−24…−34 dB：开关点击+闪烁上升（灯亮）、木模撞击声+噼啪声、揭开钟声、纸张沙沙声、盖子撞击声、火车床（隆隆声+0.62秒“咔哒声”）、驶过的火车和云幕的嗖嗖声、城市的嗡嗡声、咬碎的嘎吱声。所有内容均从 `out/timeline.json`（行开始）和 `vo/words.json` 放置。峰值限制为−1 dBFS；最终的复用器归一化为 **−14 LUFS**（`core/render/mux.sh` 中的两通响度范数）。

<a id="palette--props"></a>
## 调色板和道具

**单位和布局。** 一切都以米为单位，向上。盒腔`BOX = { w: .56, h: .33, d: .16 }`（`src/room.js`）。各层位于z处，从**−0.14（天空）到0（前面）**；盒内摄影机，z ≈ 0.3–0.56，视场角 26°。盒子内的全出血层是 `.558 × .328` — **，永远不会大于腔体**，或者它们会刺穿房间镜头中的木框架。

**夜间外观层堆叠（S01）：**
|z|层|颜色|背光`trans`|
|---|---|---|---|
|−.135|天空渐变（未点亮，`skyPanel`）+星星|`#0a1330 → #172a58 → #2e4478 → #43598a`|—|
|−.125|月盘+附加光环|`#fffaf0 / #fff0cf / #f7dca4`|—|
|−.112|祥云|`#c3cbe8`|.9|
|−.098|远处喀斯特山脉，雕刻轮廓缝隙|`#6a86c2`|.7|
|−.080|中山|`#3f5a92`|.45|
|−.062|村庄（江南房屋）+自发光窗|`#5a70a6` 墙壁 / `#1b284f` 屋顶，发光 `#ffb862`|.25|
|−.046|河流+月亮轨迹（发射）|`#22325e`，踪迹 `#e9cf96`|.3|
|−.030|桂花树+小桥，发光的花朵|`#17224a`，鲜花`#d9a24a`|.12|
|−.014|前景岸+芦苇|`#0e1532`|.05|
|+.004|悬挂灯笼（发光）|`#0d1328`，发光`#ff8a48`|.05|

规则：**后层亮+半透明，前层暗+不透明**。室内使用相同的暖棕色梯子（厨房墙`#b08058`，道具`#6e3b1f`，人物`#2e170d`，灯发光`#ffc878`）；远城使用紫罗兰（`#2a2456`，Windows `#e8cc90`）。

**强调：**印章红色`#b3302a`，金色标题纸`#f1dbac` / `#f3d998`，盒子红色`#9e2a20`，单个蓝色盒子`#2a4f7a`用于孙女的回复。

**纸张表面处理**（`src/paper.js`中的`finish()`）：平铺纤维纹理（`GRAIN`，512²，α .9，`source-atop`），顶部边缘带`rgba(255,236,200,.35)`移动3 px，底部阴影 `rgba(0,0,0,.28)` 移动 3 px。画布分辨率 `PPM = 5200` px/m.

**背光着色器** (`paperMat()`)：`emissive += albedo × lightCol × trans × uLit × fall × (.35 + 1.3·cloud)`、`fall = mix(.22, 1, exp(−d²/R²))`围绕每个镜头光点`uLight`（通常是月亮）。 `cloud` 是一种平铺的纸浆斑纹纹理 (`CLOUD()`)。发射窗口来自第二个画布（`glowDraw`，白色 = 光），由 `glow` 缩放并由 `uGlowLit` 门控（0→1 到“打开”）。

**字体**（`demo/fonts/`，OFL）：马山正`FONT.brush`为titles/poems，纸芒行`FONT.xing`为行书，龙苍`FONT.hand`为孩子手写体，Noto Serif SC `FONT.song` 用于字幕和制作人员名单。

**真实套装**（`src/room.js`中的`lightbox()`）：挤压胡桃木框架（Poly Haven `american_walnut_veneer`，色调`#8a6a52`），黑色纸内衬，胡桃木桌子，深色径向墙`#2a2018 → #0a0806`、盒口处的 `RectAreaLight` 溢出物 `#ffc98a`（强度 6-7）、半球填充 `.25`、Poly Haven `tea_set_01`（茶壶、杯子、碟子、盘子）和两个程序 3D 月饼（圆柱体 + 凹凸贴图面，来自`cakeFace`）。

<a id="titles-subtitles--end-card"></a>
## 标题、字幕 & 片尾卡

- 内置 DOM 字幕（`index.html` 中的 `#sub`）：Noto Serif SC 500、40 px、`#fbf3e4`、字母间距 0.06em、距底部 74 px、柔和的黑色阴影；行前 0.15 秒淡入，行后 0.3 秒淡出。长度超过 21 个字符的行在最靠近中间的逗号处分割；尾随标点符号被删除，内部 `，。：` 变为全角空格。
- **图中出现为纸的线条没有副标题**（`script.json` 中的`"sub": false`）：奶奶的信（L17）和诗（L23）。不要两次显示相同的单词。
- 标题：盒子内的纸条上有竖马山正（「一个月饼/的相思」），盖有红色印章「中秋」，第二行后逐渐淡出。
- 片尾卡：盒内纸题“中秋快乐”+红印章“团圆”；字幕块（`#credit`，19 像素，两行：音乐/资源/字体）在最后一行后 0.6 秒内淡出。
- **签核（仅此库的示范）：**，我们的示范的片尾卡携带**“LemoLab × Claude Opus 5.5”**作为**灯箱内的剪纸条**，不作为覆盖文本：`src/shots/s18_finale.js`中的`sign`表 - `w .26, h .02`，以深色前景银行上的`y −.1515`为中心，`z −.024`（在堤岸层，靠近最终焦平面），`text(…, .0115, FONT.song, { fill: '#f3d998', weight: 600 })`、`trans .3`、`shadow/recv: false`。它在 `tT + 1.0 → tT + 2.0`（《中秋快乐》开始后 1 秒，约 116.6–117.6 秒）内淡入并保持到最后，因此当信用块位于下面的桌子上时，它会作为灯的一部分读取。它属于风格库自己的示范：用​​户的影片没有 LemoLab 署名，没有这样的条带，也没有该片尾卡的副本。
- `paper-lantern.srt` 保留了全部 25 行（包括图中的两行）的说话时间。

<a id="pitfalls-we-hit-demo-record"></a>
## 我们遇到的陷阱（示范记录）

- **`destination-out` 切口需要不透明填充风格**：在打孔之前设置 `x.fillStyle = '#000'`（或任何不透明颜色）；透明或亮白色的填充物使孔呈半切状。 `props.js` `cut(x, fn)` 为您做到这一点。
- **VSM阴影漏光渗色/自阴影光晕**：不得参与的图层（标题、前面的灯笼、光弧、窗帘）需要**两个都**`shadow: false`**和** `recv: false`。
- **添加剂发光**：透明径向渐变`CanvasTexture`显示可见的方形边缘。使用解析 `ShaderMaterial` 衰减（`paper.js` 中的 `burst()`）来处理从打开的盒子溢出的光。
- **近平面云幕**：计算关闭位置，以便两个窗帘的**前边缘**接触（`±.035`在`s16_mutual.js`中的偏移），否则旧镜头的狭缝显示通过。
- **比空腔大的层**穿过房间镜头的木框架——保持全出血床单≤`.558 × .328`。
- **年级制服不得粘**：如果`Pipe.final()`仅在镜头的`grade()`返回时写入`lift`/`gain`，则没有它们的镜头会继承之前的镜头的值，结果取决于渲染工作器在哪个帧上启动（工作器边界处的可见等级弹出，例如 60.9 s / S09 和 101.5 s / S16）。因此，每个缺失的等级键都会回落到 `GRADE0`（`post.js`：提升 `[0, .005, .018]` 凉爽之夜默认值，增益 `[1.03, 1, .95]`），并且对于任何工人数量，渲染都是相同的。夜间外观依赖于默认值；内饰必须明确返回其温暖的 `lift`（如 S08 所做的那样）。
- 私语表现媒介听错中文同音字（八月→8月，她→他，婵娟→禅绢）；通过耳朵判断 DIFF，而不是通过字符串匹配。
- Headless Chrome 必须使用 GPU 标志运行（`--use-angle=gl --enable-gpu --ignore-gpu-blocklist`、`render/browser.mjs`）； SwiftShader 速度慢约 6 倍。

<a id="build-notes"></a>
## 构建笔记

```
styles/paper-lantern/demo/
  index.html        page: canvas + #sub + #credit, importmap → /node_modules/three (repo root is the static server root)
  script.json       lines: {id, text, rate?, say?, sub?}
  tts.py asr.py words.py   edge-tts → vo/*.wav + dur.json; whisper proof; word timings → vo/words.json
  src/main.js       timeline (GAP table), shot scheduler (lazy build / dispose), dissolves, subtitles, credits, window.render(t)
  src/shots/index.js   shot list, each start anchored to a line: start: L('L06') - .5
  src/shots/sNN_*.js   one module per shot: build(E) → { S, update(t), post(t), grade(t) }
  src/paper.js stage.js post.js room.js art.js people.js props.js lib.js   engine (see Engine reference)
  render/still.mjs video.mjs cues.mjs   stills, parallel video render, export out/timeline.json
  mix.py            voice + music + foley → out/mix.wav
  music/            analysis.json (librosa numbers); km_Ripples.mp3 + km_Nu_Flute.mp3 (incompetech, git-ignored)
```

来自存储库根 (`lemo-opuscar/`) 的所有命令。 Python = `.venv/bin/python`; `edge-tts` 必须位于 `PATH` 上（用户级 `pip install edge-tts`；它不在 `.venv` 中）。

```sh
D=styles/paper-lantern/demo
# 1. voice (Mandarin demo) — delete vo/<id>.mp3 or set "redo": true to regenerate a line
python3 $D/tts.py                          # → $D/vo/<id>.wav, $D/vo/dur.json
.venv/bin/python $D/asr.py                 # OK / DIFF per line (≈1.5 min, whisper medium, CPU)
.venv/bin/python $D/words.py L01 L02 … L25 # → $D/vo/words.json (pass ALL ids: it rewrites the file)
#    English instead: .venv/bin/python core/tts/tts.py $D/lines_en.json $D/vo && .venv/bin/python core/tts/asr_check.py $D/lines_en.json $D/vo

# 2. timeline + review stills (any number of times, seconds)
node $D/render/cues.mjs                    # → $D/out/timeline.json (DUR, line cues C, shot plan P)
node $D/render/still.mjs 5 12.5 62.5 116 --out $D/out/review          # add --q '?ssaa=1' for fast previews
#    core renderer works too: node core/render/still.mjs $D 12.5 --out $D/out/review
#    debug: ?sheet (character sheet), ?nolit=1 (backlight off), ?hide=clouds,far (S01 layers)

# 3. mix
.venv/bin/python $D/mix.py                 # → $D/out/mix.wav   (optional arg: other output path)

# 4. render video (≈90 s for 3653 frames with 6 workers on an M-series Mac; ≈3 min with 2)
node $D/render/video.mjs --workers 6       # → $D/out/video.mp4 (segments written next to the output; any worker count gives the same frames)

# 5. mux: two-pass loudnorm −14 LUFS, 30 fps, no grain
sh core/render/mux.sh $D/out/video.mp4 $D/out/mix.wav styles/paper-lantern/paper-lantern.mp4 30 0
```

审查循环：每个镜头在其关键字时间的剧照 → 表 (`ffmpeg … tile=6x5`) → 修复 → 然后完整渲染。以全SSAA检查房间镜头（前10秒，后8秒）；他们带有“这是一个真实的物体”的错觉。

<a id="engine-reference"></a>
## 发动机参考

**页面合约** (`src/main.js`)：公开`window.READY`、`window.DUR`、`window.render(t)`（每帧确定性）、`window.CUES`（线条提示）、 `window.PLAN`（镜头表）。查询`?ssaa=N`（默认2）。

**时间轴**：行从 2.6 秒开始；每行持续其 `dur.json` 长度，后跟 `GAP[id]` 秒（`main.js` 中的 `GAP` 表，例如 `L02: 4.2` 表示标题节拍，`L25: 5.0` 表示结尾）。 镜头锚定到 `src/shots/index.js` 中的线；更改语音线路会自动重新计时。

**Shot 上下文 `E`**（传递到 `build`）：`dur`、`T0`、`C`（所有线索）、`env`（PMREM 房间） env 映射）、`W`（单词）、`cue(id)` / `cueEnd(id)`（镜头中的 start/end 行 - 本地秒）、`word(id, k)`（镜头 - 耳语令牌 k 的本地开始）。

|模块|关键API|笔记|
|---|---|---|
|`paper.js`|`sheet({ U, w, h, draw, glowDraw?, glow, glowCol, trans, z, x, y, ax, ay, shadow, recv, finish, ppm, bumpDraw? })`|一层纸。 `draw(x, k)` 以米为单位绘制（原点中心，y 向上）。 `glowDraw` 绘制发射贴图（白色 = 光，黑色 = 遮罩）。 `trans` = 背光半透明。 `ax/ay` = 枢轴。返回一个网格； `m.material.userData.u`有`uTrans`、`uGlowLit`、`uClip`（圆夹`[cx, cy, r, inside?]`）。|
| |`skyPanel({ w, h, z, stops, stars, starMinY, gain })`|不发光的渐变背板。|
| |`moon({ x, y, z, r, gain, halo, haloGain, art? })`、`setMoon(m, k)`|圆盘+附加光环； `k` = 亮度 0…1+。|
| |`text(x, s, px, py, size, font, o)`、`vtext(…)`|米空间中的文本（`vtext` 为垂直）。|
| |`burst(w, h, col)` → `m.userData.set(k)`|分析添加剂发光。|
| |`paint(w, h, draw, ppm)`、`finish(c, o)`、`tex(c)`、`PPM`、`GRAIN`、`CLOUD()`|低级画布助手。|
|`stage.js`|`stage({ light, lightR, lightCol, key, keyCol, keyPos, keyTarget, keyAngle, amb, ambCol, shadowR, fov, bg })` → `{ scene, U, cam, key, amb, add(...) }`|场景 + 顶部 LED 聚光灯（VSM，2048²，半径 10）+ 环境光 + 背光制服 `U`。|
| |`aim(cam, [px,py,pz, tx,ty,tz], t, { hand, handF, roll, fov })`|摄影机带手持漂移。|
| |`dispose(scene)`|当镜头离开时由调度程序调用。|
|`post.js`|`Pipe.shot(scene, cam, { focus, aper, maxCoc, bloom: { strength, radius, threshold } }, target)`|MSAA4 半浮点 → CoC → 96 点收集 DoF → UnrealBloom。 `focus` = 距离（以米为单位）。|
| |`Pipe.final({ mixB, mode, center, expo, fade, vig, sat, contrast, lift, gain })`|溶解/虹膜、等级、晕影、中性色调贴图、sRGB。 镜头的关键帧每帧都会忽略回退到 `GRADE0`。|
|`room.js`|`await lightbox(S, E, { spill, spillCol })` → `{ g, frame, spill, table, props }`, `BOX`|现实世界的盒子、桌子、茶具、月饼。纹理从 `/core/assets/polyhaven/` 加载。|
|`art.js`|`karst`、`ridge`、`xiangyun`、`waves`、`waterTop`、`osmanthus`、`pine`、`willow`、`reeds`、 `jiangnanHouse(x, o, g)`、`pavilion`、`lantern(x, o, g)`、`mooncake`、`FONT`|剪纸图案；使用 `g` 的函数将窗口绘制到发光画布中。|
|`people.js`|`grannyStand/Sit`、`girlStand/Sit`、`childStand`、`sushi`、`change`（嫦娥）、`rabbit`、`arm(x, s, a, b)`、`spline`、 `ribbon`, `*_SHOULDER`|剪影人物，比例 `s` = 高度（米）。|
|`props.js`|`cut(x, fn)`、`roundWindow`、`steamers`、`stove`、`jar`、`bowl`、`teapot`、`pendant`、`calendar`、 `table`、`chair`、`boxFront`、`label`、`cake3q`|室内道具。|
|`lib.js`|`ss`、`seg`、`eio`、`eo`、`ei`、`back`、`spring`、`lerp`、`clamp`、 `mulberry`、`vnoise`、`track`、`env`|确定性助手。|

**最小镜头**（月光下的小山，有一个被照亮的窗户；将其添加到`SHOTS()`作为`{ id: 'S99', start: L('L05') - .3, in: { type: 'dissolve', dur: .8 }, build: s99.build }`）：

```js
import { sheet, skyPanel, moon, setMoon } from '../paper.js';
import { karst, jiangnanHouse } from '../art.js';
import { stage, aim } from '../stage.js';
import { seg, ss, eio, lerp } from '../lib.js';

export function build(E) {
  const MN = [.08, .07, -.13];
  const S = stage({ light: MN, lightR: .15, lightCol: '#ffe2ae', key: 1.0, amb: .3, ambCol: '#7d90c8', keyCol: '#d6dcff' });
  const { U } = S;
  S.add(skyPanel({ w: .56, h: .33, z: -.14, stops: [[0, '#0a1330'], [1, '#43598a']], stars: 200 }));
  const mn = S.add(moon({ x: MN[0], y: MN[1], z: MN[2], r: .035 }));
  S.add(sheet({ U, w: .558, h: .328, z: -.1, trans: .7, draw: x => { x.fillStyle = '#6a86c2';
    karst(x, { x0: -.28, x1: .28, base: -.03, peaks: [[-.15, .06, .03], [.1, .05, .025]], carve: .0005 }); } }));
  const house = { cx: -.05, by: -.09, w: .06, h: .03, windows: [[.012, .01, .01, .01]], wall: '#5a70a6', tile: '#1b284f' };
  const town = S.add(sheet({ U, w: .558, h: .328, z: -.06, trans: .25, glow: 2.2, glowCol: '#ffb862',
    draw: x => jiangnanHouse(x, house), glowDraw: g => jiangnanHouse(null, house, g) }));
  S.add(sheet({ U, w: .558, h: .328, z: -.02, trans: .05, draw: x => { x.fillStyle = '#0e1532'; x.fillRect(-.28, -.165, .56, .075); } }));
  const tOn = E.word('L05', 2);                        // light the window on the 3rd spoken token
  return {
    S,
    update(t) {
      setMoon(mn, ss(seg(t, 0, 1.5)));
      town.material.userData.u.uGlowLit.value = ss(seg(t, tOn, tOn + .6));
      aim(S.cam, [0, 0, lerp(.56, .48, eio(t / E.dur)), 0, 0, -.07], t);
    },
    post() { return { focus: S.cam.position.z + .06, aper: 14, maxCoc: 14, bloom: { strength: .35, radius: .6, threshold: 1.15 } }; },
    grade() { return { expo: 1.05, vig: .42, sat: 1.05, contrast: .1 }; },   // missing lift/gain → GRADE0 (cool night); interiors add lift: [.012, .006, 0]
  };
}
```

**切换到英文**：在`main.js`中，字幕分割器假定为中文（`st.length > 21`，在`[，。：]`上分割，标点→全角空格）。对于英语，当长度超过 42 个字符时，将其更改为在最靠近中间的 `, ` 处拆分，并保留标点符号；将 `#sub` 设置为拉丁衬线（例如，添加 OFL 字体，如 Cormorant 到 `fonts/`），约为 38 像素。 `E.word(id, k)` 然后计算英语单词数。其他一切（时间轴、混合、渲染）都是与语言无关的。
