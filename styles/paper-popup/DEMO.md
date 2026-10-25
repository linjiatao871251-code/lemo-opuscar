<a id="paper-pop-up-book--our-demo"></a>
# 纸质立体书 — 我们的示范

众多例子中的一个。请勿重复使用其故事、弧线、镜头、道具或时间安排。

示范：*小精灵的冒险*（*皮普的纸冒险*，小精灵冒险记）（133.0 s，1920×1080，60 fps）·`paper-popup.mp4`·来源在[`demo/`](demo/)·引擎： three.js r170 (WebGL2) 在无头 Chrome 中逐帧渲染，Canvas2D 用于所有纸质艺术，Python 用于配乐编辑和混合


<a id="story--structure"></a>
## 故事与结构

一本故事书在一张真正的木桌上打开，变成了一个舞台；最后，英雄从书页跳入真实的房间。

示范如何使用风格特有表现手法：

|原生电源|示范中的故事使用|
|---|---|
|**本书打开**|打开是一种物理仪式：一本合上的书，吱吱作响，封面打开，世界一点一点地闪现出来。这就是“从前”。|
|**翻页=场景变更**|每一章都是一个展开。过渡是真正的翻页：一张弯曲的纸，正面是旧的地面，背面是新的天空，而旧的弹出窗口向下折叠，新的弹出窗口弹出。书内无删减。|
|**纸机构**|拉环魔术是故事节拍：一根棍子上的太阳从山后升起，黄昏时下沉，一扇铰链上的门，一条由三个滑动的波浪条组成的河流，**的天空，四个从白天到黑夜翻转的板条**像一个三边广告牌，月亮和星星挂在绳子上。|
|**纸质**|一个皱巴巴的脾气暴躁的人（Crumple）被**抚平了**，然后扑进了一架折叠纸飞机（Fold），它成为了朋友，后来又变成了交通工具。|
|**页边**|最后一页未完成（铅笔草图，“结束”印在地上）；英雄向边缘看去，跳跃并落在真实灯下的真实桌子上。|
|**真正的光一直在那里**|黄昏时，“另一盏灯亮了”是实际的台灯在页面上变亮。回报：“一盏阅读灯……和一个人一起读书。”|

故事形状：真实的桌子建立（10秒）→书打开→第一章家园和英雄的愿望（书页之外的光）→第二章一个障碍角色，被跺脚击败，然后“帮助”（平滑），变成一个同伴→第三章一段有堵嘴的旅程（鲸鱼喷出五彩纸屑）和白天→夜晚翻转→最后一章：空白的最后一页，恐惧，“这里走了！” → 同伴抓住了英雄，他们飞出了桌子 → 着陆，显示，“你好，大世界！” → 在桌子上以“结束？”结束标题。

我们当时建议如何对其进行修改（保留在历史中；STYLE.md §11 现在给出了范围）：将主题世界变成书中所展开的（3-4 章，每一章都有一个纸质机制），给英雄一个指向书本*之外*的愿望，最后穿越到真实的房间。

<a id="shots"></a>
## 镜头

单个虚拟宏摄影机，视场 30（反向镜头为 56），在 `main.js SH` 中键入为 `[t, pos xyz, target xyz, fov, aperture, focus]`，并使用单调三次插值 (`track`)。每个内表都是一个连续的镜头；一份新的清单=一次艰难的削减。

|打|摄影机|
|---|---|
|建立|在桌子上方（1.1 m 远），小车缓慢下降至合上的书；光束中的灯尘微粒。|
|书打开|当封面竖起时，在页面上处于较低且正面的位置；火花升起。|
|书中|眼睛与纸演员的高度：摄影机页面上方 5-10 厘米，后面 30-45 厘米，聚焦在演员上（光圈 2.2-2.5，浅）。步行后缓慢的横向移动。|
|翻页|向上拉回整个跨页的 3/4 视图（光圈 1.8-2，更深），以便翻页阅读，然后落入新世界。|
|情感接近|推入面部 28 厘米（孔径 2.5）。|
|页面边缘|**反向拍摄**：摄影机在Pip（视场56，焦点11厘米）后面，透过页面边缘看到真实的、模糊的房间和巨大的灯。我们唯一一次看到“外面”。|
|航班起飞|切换到办公桌的宽前视图（1 m，视场 32）；跟随飞机穿过桌子，然后摄影机落在木头上 Pip 的高度处（孔径 4，焦点 ~0.52 m）。|
|结尾|慢慢地向后拉，向上拉，露出整个桌子，后面是打开的书，作为最后的标题。|

景深 (`post.js`)：CoC（以像素为单位），最大 14、64 抽头黄金角螺旋聚集。

<a id="motion-numbers"></a>
## 运动编号

- 弹出窗口：`back(seg(t, t0, t0+.55), 1.7)`；每个片段的延迟是其传播时间 `RISE` 后的 `(.3 − z) × 1.2` 秒；靠近背部的棋子向后躺着（`dir −1`），其他棋子面朝下向前倒下（`dir +1`）。
- 摇摆：`sin(1.6t + phase) × sway` 围绕底座（0.01–0.08 rad）。
- 角色：姿势量化为1/40；眼睛 `open/happy/wide/closed/dizzy`，嘴 `smile/open/o/grin/worried/determined`，每 3.7 秒眨眼一次。行走=双腿摆动`sin(phase)`，弹跳`|sin(phase)| × 1.2 mm`，手臂反摆；相位每半步前进 1.8 厘米。转动：`S.face = cos(...)` 对 `scale.x` 翻转进行动画处理（FrontSide 正面图、BackSide 后脑图）。
- 跳跃：`arc(t, t0, t1, a, b, h)` + 起飞和着陆时挤压（`land`、`pipState` 中的 `crouch`）+ 纸泡云。
- 翻页 (`book.setLeaf(u)`)：40 段条带，`φ = θ·(1 − L·(s − ½))`，弯曲 `L = .55·sin(πu)`，使用 `eio` 在 2.3 秒内缓解。
- 机构：四个天板条翻转间隔0.28秒；门以 `back()` 摆动；叙述的每一次“嗖嗖”，河流带都会滑动 ±12 毫米。

<a id="score-structure"></a>
## 配乐结构

- **旁白**：一位温暖的讲故事者，Kokoro `af_bella`，速度0.9，en-us； 15 行短行（2-9 秒），写得像一本图画书（“纸板山。木棍上的纸太阳。”）。各行的发音与 `tts/lines.json` 中的实际显示方式不同（例如，“Swish Swash Sea”没有连字符；“...”而不是“...”）；显示的文本位于 `story.js VO` 中。在峰值的 1% 处修剪静音（+10 毫秒头部，+100 毫秒尾部）。每行都用Whisper 语音检查（`asr.py`、`words.py` 的字时间来同步搞笑）。
- **字符 blips**：30 chars/s 处的气泡类型，每隔一个字母一个 blip； Pip = 方波，明亮的音调（C6-ish），Crumple = 低 180–240 Hz，Fold = 三角波。
- **音乐**：三首 Kevin MacLeod 曲目 (CC BY 4.0)，在 `music/edit.py` 中编辑：*梦幻闪回*（0–16.2 秒，淡出 1.6 秒）用于真实桌面； *Jaunty Gumption* 从 15.4 秒开始，适用于整个纸质世界，采用 **one bar 对齐内部跳切**（73.21 秒 → 102.79 秒轨道，0.42 秒交叉淡入淡出），由 `music/jump.py`/`jump2.py` 选择（节拍同步色度 + MFCC 自相似性，将长度缩短为 4 节拍的倍数），以便歌曲的真正结局落在 104.22 秒 - Pip 跳出页面的那一刻； *暖心*现实世界和片尾卡的 39.38 秒为 104.8 秒 (×1.15)。
- **音效**，全部从`events.json`在`mix.py`中合成（`render.mjs events`导出的250个事件）：书本吱吱声+重击声，弹出弹出声（正弦扫频+纸张皱褶），翻页声，门吱吱声，嗡嗡声，跳跃、脚步声（微小的敲击声+每次行走半周期的皱纹）、纸卷、“！”砰、跺脚、NICE/GREAT 琶音、闪光（铃声）、噗、折纸、嗖嗖、飞溅、鲸鱼喷水、板条咔哒声、星星叮当声、灯开关+温暖和弦、着陆打滑。 `G` 表中每种类型的增益。
- **氛围床**每页：房间音+桌子上的时钟滴答声，鸟儿+山谷里的河流，黄昏时的蟋蟀，鸟儿+森林里树叶的沙沙声，海上的波浪，最后一页和现实世界中的房间音。
- **混音**：语音高通90 Hz，压缩（−24 dB，3:1），有限，在语音区域设置高于音乐8.5 dB；音乐在语音下降低了 40%（300 毫秒平滑）；声音混响 7%；每个通道的 SFX 限制为 0.5；氛围×2。标准化为 0.89 峰值，然后 `mux.sh` 应用 `loudnorm I=−14 TP=−1.2 LRA=11`。

<a id="palette--props"></a>
## 调色板和道具

**比例（米）：**书页0.44×0.30（`BW`、`BD`），页块高度`PG` = 0.0175。 Pip 高为 `H = 0.036`，Crumple 0.042，纸飞机长 0.052，鲸鱼宽 0.10，船 0.062。山丘 0.2–0.26 宽，树木 0.05–0.16 高。 摄影机近平面 0.004 m。

**书桌：**胡桃木桌、台灯、茶杯、闹钟、铅笔、盆栽（Poly Haven CC0）； `lythwood_lounge_2k.hdr` 作为环境和背景（模糊度 0.22，偏航 2.3），胡桃木贴面（`#c9a88a` 色调，环境 0.8），程序铅笔。本书：精装本，44 × 30 厘米，书脊在远侧，封面旋转 90°，站在书页后面，就像一幅彩绘的天空。

**剪纸饰面** (`paper.js finishCut(art, border, o)`)，三个环上16+角度(r、.66r、.33r)：灰色纸板边缘`#b9ad9c`，边框+ 2.5 px，向下偏移1.5 px；灰白色边框 `#fffdf7`，12–16 像素（静态道具 14 像素，5200 px/m，字符 16 像素）； 512 像素颗粒纹理，alpha 0.5–0.85。

**绘画** (`art.js`)：墨水 `#3a2a24`，轮廓 9 像素 (`LW`)，细节 5 像素 (`LW2`)； `crescent(x, path, shade, dx, dy, base)`; `blob`、`smoothClosed` 具有 3 次谐波噪声。脸：黑色的椭圆形大眼睛，有两个白色亮点，弯嘴，粉红色的脸颊。

|使用|颜色|
|---|---|
|家谷|草`#86c763`→`#9fd57a`，丘陵`#b5e39a` `#a9dd8c` `#8fd06e`（阴影`#6fb553`），路径`#ecd49a`，天空`#7cc6ef`→`#c9ecf7`|
|森林|地面`#4f8f46`→`#62a653`，后松`#8cc9a0`，前松`#3f9a5c`，天空`#a8e0cf`带光轴|
|海|波光→暗`#9ad8f5` `#79c3ee` `#58ade3` `#3f95d6` `#2f7fc4`，天`#4fb3ea`，夜`#131d44`→`#4a5a94`|
|最后一页|奶油纸`#f5eedc`，石墨铅笔线`rgba(70,72,82,.45)`，IM Fell英文“The End”|
|英雄皮普|皮肤`#ffe2bd`（阴影`#f3c393`），叶帽`#62c24c`/`#3e9a34`，外衣`#3fa1de`/`#2a78b3`，靴子`#8a5530`，翅膀`#d4f3ff`|
|口音|蘑菇屋红`#e8413a`，太阳`#ffd766`，sign/banner金色`#ffcf3f`，丝带红`#d8423a`|
|书|布料`#1f5566`，金箔`#e0b456`（金属度图），页面边缘`#efe6d2`有细线|

**弹出件** (`cutmesh.js cutMesh`)：背面颜色`#efe8da`（或门的`#8a5a34`）通过`onBeforeCompile`； `alphaTest .5` + `alphaToCoverage`； `customDepthMaterial`。船=后面的帆卡+前面的船体卡；折叠 = 四个三角形铰接在龙骨上。

**字体：** Fredoka 500/600/700（字幕，气泡，标志），Lilita One（封面，章节横幅，动作词，结束标题），IM Fell English（封面标语，“The End”，“The End？”），ZCOOL KuaiLe（中文）。所有OFL，由`fetch_fonts.mjs`下载到`demo/fonts/`（中文子集=仅源文件中的字符）。

**内置标题和字幕：**
- 旁白字幕（`hud.js drawSubs`）：英文Fredoka 500 40 px，奶油色`#fffaf0`，8 px深棕色轮廓，柔和阴影，1720 px换行；中文在ZCOOL快乐32px以下。行前淡入 0.3 秒，保持到音频后 0.25 秒，淡出 0.3 秒。
- 语音气泡 (`drawBubbles`)：半径 44、6 px 墨水轮廓、柔和的阴影、每帧从 3D 投影的尾部、以 `back()` 弹出，英文位于 30 chars/s (Fredoka 600 46 px)，然后是中文 (ZCOOL KuaiLe 32 px， `#7a5e4c`）和一个摆动的红色“下一个”三角形。
- 章节横幅 (`drawChapter`)：两根绳子上悬挂的纸板标志，红丝带“第 N 章”，标题为 Lilita One 84 px 金色 `#ffcf3f`，带有 12 px 墨迹笔画，下​​方有中文。
- 动作词（`drawAction`、`drawBang`）：“很好！” / “伟大的！”斜体 Lilita One 120 px，渐变填充，白色 + 墨水双描边，射线；一个红色的“！”越过受惊的英雄。
- 标题：书的封面（布质+金箔《小精灵的冒险～纸上的故事～》，附有roughness/metalness地图，以及圆形Pip插图）。
- 由`story.js`（`make_srt.mjs`）生成双语`.srt`：旁白+气泡，英文行然后中文行。

<a id="end-card"></a>
## 端卡

`drawEnd`，从 123.4 秒开始，在直播台上镜头：Lilita One 96 px 金色标题（y 170），中文标题（y 262），斜体“The End？”弹出 (y 350)，然后从 127.6 秒开始，签核和资产积分 (22 px, y 960/998/1036；中文行使用 `'"ZCOOL KuaiLe", Fredoka'`) 一起淡入；在最后 1.5 秒内褪色为黑色。

签核 **"LemoLab × Claude Opus 5.5"** (× = U+00D7) 仅属于本库的示范；用户的影片没有 LemoLab 积分，也没有该卡的副本。在示范中，它位于“The End?”下方的中心位置。在 y 430：Fredoka 600 36 px，奶油色 `#fffaf0` 填充 7 px `rgba(30,20,14,.75)` 轮廓（它位于奶油色背景页上，因此轮廓是让它读取的原因），在 127.6 秒处随着资产信用淡入，从不覆盖角色。

<a id="pitfalls-tied-to-this-demo"></a>
## 与示范相关的陷阱

- **一艘单翼船隐藏了坐在里面的角色**：分成帆（后面，z −3 毫米）和船体（前面，z +2 毫米），中间有 Pip。
- **前景模糊**：森林蕨类植物和灌木丛在20.9秒时充满了镜头附近的画面。
- **混音器错误**：将立体声 (N×2) 阵列传递到 1-D 限制器，默默地将所有 SFX 压碎至 −96 dB。分别限制每个通道。
- **有效的阴影设置**：点阴影贴图4096²，偏差-6e-5，正常偏差4e-4。叶子材质：自发光贴图 = 颜色贴图，自发光 0.42。
- **Headless WebGL 速度**：默认 Chrome 使用 SwiftShader (~620 ms/frame)； `--use-angle=gl --enable-gpu --ignore-gpu-blocklist` 在 Apple Silicon 上每帧提供数十毫秒的时间。通过 HTTP 提供服务（`serve.mjs`，在 `render.mjs` 内部启动）。
- **Poly Haven API**：Python `urllib` 获得 403；使用 `curl` 下载。
- **字体子集**：`fetch_fonts.mjs`仅包括下载时`story.js/hud.js/main.js/art.js`中存在的字符。智酷快乐子集没有拉丁字形，因此中文学分行中的拉丁字回落到系统衬线；使用 `'"ZCOOL KuaiLe", Fredoka'`。
- **重画成本**：仅当姿势（量化为1/40）改变时，Pip的画布才会重画。

<a id="build-notes"></a>
## 构建笔记

```
styles/paper-popup/demo/
  index.html  importmap (three from demo/node_modules) + fonts.css + main.js
  main.js     scene: renderer, HDRI, desk & props, book, particles, choreography (pipState/crumpleState/foldState),
              camera keys SH, lightsAt(t), sound-event list EV, window.render(t)
  story.js    timeline (single source of truth): DUR, VO narration, BUB bubbles, CHAPTERS, CREDITS, OPEN, TURNS
  book.js     the book (cover, spine, page blocks, ground/back pages, curling leaf), texOf()
  sets.js     page art per spread (pages()), pop-up pieces (buildSets), sky slats, updatePops/riseOf, RISE/FOLD
  art.js      all Canvas2D drawings: drawPip/drawPipBack, drawCrumple, drawWhale, props (hill, pine, mushHouse, …)
  paper.js    canvas helpers: finishCut (white border + card edge + grain), paperFill, crescent, blob, sh
  cutmesh.js  cutMesh (front art / back paper / cut-out shadow), blobShadow, thread, particles (InstancedMesh)
  actors.js   makePip, makeCrumple, makeFold (foldable paper plane), makeWhale, makeBoat
  post.js     DOF pass (CoC + 64-tap gather) → bloom → vignette/warmth → output
  hud.js      2D overlay: subtitles, bubbles, chapter banners, NICE/GREAT, "!", end card, blip times
  render.mjs  stills / events / video (N workers → out/seg_*.mp4)    serve.mjs  static server
  tts/        lines.json + gen.py (all lines) / gen1.py (selected lines) → voices/*.wav + dur.json
  asr.py words.py   whisper check / word timestamps      music/edit.py  score.wav    mix.py  mix.wav
  mux.sh      segments + mix → ../paper-popup.mp4        make_srt.mjs  → ../paper-popup.srt
```

所有命令都可以从存储库根目录运行。 Python = 存储库 `.venv`（其中安装了 numpy、scipy、soundfile、librosa、kokoro-onnx、faster-whisper）。

```sh
D=styles/paper-popup/demo; PY=.venv/bin/python
# 0. once: fonts (re-run after changing Chinese text) and music
(cd $D && node fetch_fonts.mjs)
#    download the three MP3s from incompetech.com into $D/music/, then convert to 48 kHz WAV:
for f in Dreamy_Flashback Jaunty_Gumption Heartwarming; do ffmpeg -y -i $D/music/$f.mp3 -ar 48000 -ac 2 $D/music/$f.wav; done
# 1. voice (Kokoro model is shared from core/tts/): all lines, or only some
$PY $D/tts/gen.py af_bella            # → voices/v01..v15.wav + voices/dur.json
$PY $D/tts/gen1.py v04 v07            # regenerate selected lines
# 2. proof-listen
$PY $D/asr.py; $PY $D/words.py        # whisper transcript / word timestamps for gag sync
# 3. timeline: edit story.js (VO start times use voices/dur.json), then check stills
node $D/render.mjs stills 6.5 30 61.8 82.6 118     # → demo/stills/t_*.jpg (STILLS_DIR=out/x to redirect)
# 4. score (only when the edit points change)
$PY $D/music/edit.py                  # → music/score.wav (jump-cut search: music/jump.py, jump2.py)
# 5. sound events + mix
node $D/render.mjs events             # → events.json (250 events)
$PY $D/mix.py                         # → mix.wav (argument = other output path)
# 6. video: 7980 frames, N workers (8 used for the demo ≈ 2.5 min; use 2 when other jobs share the GPU)
node $D/render.mjs video 8            # → out/seg_0..7.mp4 + out/list.txt
# 7. mux (+ film grain noise=c0s=2, loudnorm −14 LUFS) and subtitles
zsh $D/mux.sh                         # → styles/paper-popup/paper-popup.mp4 (OUT=... to write elsewhere)
node $D/make_srt.mjs                  # → styles/paper-popup/paper-popup.srt
```
助手：`shot.mjs page.html out.png`（对任何页面进行屏幕截图，例如 `sheet.html` = 角色和道具角色设定表）、`probe.mjs '<js expr>'`（在加载的场景内进行评估；`window.DBG` 公开 pip/boat/fold/whale/book/cam）、`gltest.mjs` （GPU 标志基准）、`tile.py`（剧照联系表）、`music/survey.py`（tempo/loudness 候选曲目调查）。通用 `node core/render/still.mjs styles/paper-popup/demo 30` 也可以使用（该页面仅使用相对 URL）。

<a id="engine-reference"></a>
## 发动机参考

**坐标.** 世界 = 米，y 向上；桌面相对于页面的 y = −PG 位置。 `book.stage` 是页框：x ∈ [−0.22, 0.22] 左→右，z ∈ [0, 0.30] 从书脊（远）到读者（近），y 从页面向上。 `book.sky` 为立式背景框（盖子打开后）：x 如上，y ∈ [0, 0.30] 位于背景上方，小 +z = 位于其前面。字符进入`book.stage`；挂clouds/moon/stars进去`book.sky`。

|模块|关键API|笔记|
|---|---|---|
|`lib.js`|`seg(t,a,b)`、`ss`、`eio`、`eo`、`ei`、`back(t,s)`、`spring(t,k,z)`、`env(t,a,b,fi,fo)`、`mulberry(seed)`、 `track([[t,[…]],…])`|所有动画均为 `f(t)`； `track` = 单调立方关键帧（摄影机，飞行路径）|
|`paper.js`|`cv(w,h)`、`finishCut(art, border=14, {paper, edge, grain, grainA})`、`paperFill(x,w,h,col,seed,mott)`、`crescent(x,pathFn,shade,dx,dy,base)`、`blob(x,cx,cy,rx,ry,wob,seed)`、`sh(x,fill,lw,stroke)`、`smoothClosed/smoothOpen`、`GRAIN`、`INK`|适用于任何纸张的 Canvas2D 工具包|
|`art.js`|`cut(wm,hm,draw,{pad,border,ax,ay,raw})`→`{c,w,h,ax,ay}`，`PPM`=5200 px/m；道具 `hill(w,h,col,shade,seed,{bumps,dots})`、`lolliTree(h,col,shade,seed)`、`pine`、`bush`、`flower(h,petal,seed)`、`mushHouse(h)`、`door`、`windowGlow`、 `sunOnStick(r,stick)`、`cloud(w,seed)`、`sign(w,text)`、`fence(w,h)`、`waveStrip(w,h,col,dark,seed,n)`、`boat(w,'sail'|'hull')`、`moon`、`star`、`island`、 `mushroom`、`log`、`fern`、`sketchTree`、`sketchHouse`、`leafBit`、`bang`；字符 `drawPip(x,pose)`、`drawPipBack`、`drawCrumple(x,{mood,blink,mouthOpen})`、`drawWhale(x,{happy})`|每个道具都会返回一个 `cutMesh` 的项目；默认情况下，anchor (ax, ay) = 底部中心|
|`cutmesh.js`|`cutMesh(item,{s,backCol,shadow,tex})` → 组（原点 = 锚点）、`blobShadow(r,a)`、`thread(len)`、`particles(geo,mat,n,(i,t)=>({x,y,z,rx,ry,rz,s,col})|null)` → 带有 `.userData.update(t)` 的实例化网格体|剪裁阴影，纸色背面|
|`book.js`|`coverCanvases(drawIcon)` → `{c,m}`; `makeBook(cover)` → `{root, stage, sky, groundMat, backMat, leafFront, leafBack, setOpen(θ), setLeaf(u), coverMat}`; `texOf(canvas,{linear})`； `BW BD PG`|`setOpen(π/2)` = 全开；每个价差设置 `groundMat.map`/`backMat.map`； `setLeaf(0..1)` = 翻页（0/1 隐藏叶子）|
|`sets.js`|`pages()` → 画布 `sky0 ground0 sky1 ground1 sky2day sky2night ground2 sky3 ground3`（2048 × 1396、`gx(x)`/`gz(z)` 将米映射到像素）； `buildSets(book)` → `{L, ex}`; `updatePops(L,t)`； `RISE[spread]`，`FOLD[spread]`；内部 `popper(list, spread, parent, item, x, y, z, {d, dir, sway, ph, pop, ry})`|添加价差 = 页面艺术 + 具有新价差索引的 `popper` 调用块，并扩展 `RISE/FOLD/TURNS`|
|`actors.js`|`makePip(H)` → `{root, body, shadow, pose(p), head()}`; `makeCrumple(D)`； `makeFold(L,S,KD)` → `{fold(f 0..1), drawFace(mood,blink)}`; `makeWhale(w)` → `{setHappy}`; `makeBoat(w)`|姿势 `p` = `{walk, stride, armL, armR, flap, eyes, mouth, look:[x,y], blink, lean}`|
|`post.js`|`makePost(renderer, scene, cam, w, h)` → `{composer, dof:{focus, aper, maxCoc}, bloom, vig:{uniforms:{amt,fade,warm}}}`|调用 `post.composer.render()` 而不是 `renderer.render`|
|`hud.js`|`drawSubs(ctx,t,dur)`、`drawBubbles(ctx,t,{who:[sx,sy]})`、`drawChapter`、`drawAction(ctx,t,[{t0,text,p,col}])`、`drawBang`、`drawEnd`、`blipTimes()`|全部读取`story.js`；在 1920×1080 `#ov` 画布上绘画|

**页面合约**（`render.mjs`需要的）：资产加载后的`window.READY = true`； `window.render(t)`确定性地抽取第二个`t`； `window.DUR`; `window.EV = [{t, type, …}]` 为 `mix.py`（“配乐结构”中列出的类型；在 `mix.py` 中为新类型添加新分支）。

**最小示例**——一个新的跨页，有一个弹出的小山，一个英雄在上面行走，还有一个翻页摄影机，在`main.js`风格的代码中：

```js
import * as THREE from 'three';
import { makeBook, coverCanvases, texOf, BW, BD } from './book.js';
import { cutMesh } from './cutmesh.js';
import { makePip } from './actors.js';
import { makePost } from './post.js';
import * as A from './art.js';
import { cv, paperFill } from './paper.js';
import { seg, back, eio, track } from './lib.js';

const renderer = new THREE.WebGLRenderer({ antialias: false, preserveDrawingBuffer: true });
renderer.setSize(1920, 1080); renderer.shadowMap.enabled = true; renderer.shadowMap.type = THREE.PCFSoftShadowMap;
renderer.toneMapping = THREE.NeutralToneMapping; renderer.outputColorSpace = THREE.SRGBColorSpace;
document.getElementById('stage').appendChild(renderer.domElement);
const scene = new THREE.Scene(), cam = new THREE.PerspectiveCamera(30, 16 / 9, .004, 30);
const post = makePost(renderer, scene, cam, 1920, 1080);
// (load the HDRI + desk exactly as main.js lines 34–43)

const book = makeBook(coverCanvases((x, px, py, w, h) => { /* draw the cover medallion */ }));
scene.add(book.root);
const ground = cv(2048, 1396); paperFill(ground.getContext('2d'), 2048, 1396, '#9fd57a', 2);
book.groundMat.map = texOf(ground);

// a pop-up hill: lies flat (rotation.x = −π/2 · (1−k)) and springs up around its bottom edge
const hill = new THREE.Group(); hill.add(cutMesh(A.hill(.24, .075, '#b5e39a', '#93cc78', 11)));
hill.position.set(0, 0, .04); book.stage.add(hill);

const pip = makePip(); book.stage.add(pip.root, pip.shadow);
const camKeys = track([[0, [.0, .27, .78, 0, .1, .1]], [4, [0, .06, .38, 0, .04, .13]]]);
const sun = new THREE.DirectionalLight('#fff3e0', 2.6); sun.position.set(-.35, .55, .75); sun.castShadow = true;
Object.assign(sun.shadow.camera, { left: -.3, right: .3, top: .3, bottom: -.3 }); scene.add(sun);

window.render = t => {
  book.setOpen(Math.PI / 2 * eio(seg(t, .5, 3.1)));                     // cover swings up into the backdrop
  const k = back(seg(t, 3.0, 3.55), 1.7);                               // pop-up with overshoot
  hill.visible = k > .002; hill.rotation.x = -(Math.PI / 2) * (1 - k);
  const w = seg(t, 4, 7), ph = w * .15 / .018 * Math.PI * 2;            // walk 15 cm, phase from distance
  pip.pose({ walk: ph, stride: w > 0 && w < 1 ? 1 : 0, armL: .25 + Math.sin(ph) * .5, armR: .25 - Math.sin(ph) * .5 });
  pip.root.position.set(-.1 + .15 * w, Math.abs(Math.sin(ph)) * .0012, .15);
  pip.shadow.position.set(pip.root.position.x, .0004, .15);
  const c = camKeys(t); cam.position.set(c[0], c[1], c[2]); cam.lookAt(c[3], c[4], c[5]); cam.updateProjectionMatrix();
  post.dof.focus = cam.position.distanceTo(new THREE.Vector3(c[3], c[4], c[5])); post.dof.aper = 2.3;
  scene.updateMatrixWorld(true); post.composer.render();
};
window.DUR = 8; window.EV = [{ t: .5, type: 'creak' }, { t: 3.1, type: 'pop' }];
window.READY = true;
```

要将引擎重复用于不同的影片（您自己的故事，而不是这个），请复制引擎文件，编写新的 `story.js`（线条、气泡、章节、`OPEN`、`TURNS`、`DUR`），替换 `sets.js` 中的跨页（`pages()` + `buildSets`），重画`art.js`中的字符，然后重新键入`pipState`，摄影机在`main.js`中列出`SH`和`lightsAt`。保持 book/paper/cutmesh/post/render/mix 不变。
