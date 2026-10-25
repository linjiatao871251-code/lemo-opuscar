<a id="hd-2d--our-demo"></a>
# HD-2D — 我们的示范

众多例子中的一个。请勿重复使用其故事、弧线、镜头、道具或时间安排。

示范：*灯笼*（76.5秒，1920×1080，60 fps）·`hd-2d.mp4`（**移轴剪切**）·源[`demo/`](demo/) · 引擎：three.js r170 场景 + 程序像素纹理 + 自定义物理 DOF / 移轴柱 (`demo/post_ts.js`) + Canvas2D 叠加 UI，使用 `core/render/video.mjs` 逐帧渲染。


<a id="story--structure"></a>
## 故事与结构

港口小镇的灯塔熄灭了；老守护者将最后的火焰交给了他的孙女雷恩，她提着灯笼穿过夜间的森林，爬上饱受风暴摧残的悬崖楼梯，重新点燃灯塔，这样海上的船只就能找到回家的路。标语：*每条路都从一盏灯开始。*

示范如何使用该风格的原生能力：

|原生电源|故事运用|
|---|---|
|**A 轻英雄携带**|灯笼既是关键光源，又是情节：雷恩携带一盏必须到达灯塔的小灯。它的亮度是情感计量表：明亮→暗淡→几乎熄灭→重新点燃。|
|**桌面世界**|读作“地图”的地方：港口小镇、森林小路、悬崖楼梯、塔顶。每章一个位置，每个位置都有自己的灯光键。片头在最后返回以显示变化（港口：灯塔黑暗→点亮，船灯出现）。|
|**RPG语法**|“第一章”卡牌、在对话框中交出任务的指定 NPC、穿越两个生物群落的旅程、地标处的高潮、标题卡。|
|**精灵阴影**|第一个照明（火盆锥体 → 灯笼）发生在屏幕上，靠近两个角色，因此两个阴影都会跳到木板上。|
|**移轴**|超宽焦距镜头，聚焦带聚焦在单个微小物体（灯塔、船）上。|

**我们的故事形状：**冷章卡→广泛建立镜头，其中地标灯**失败**→在对话框中移交任务（光通过）→穿越较黑暗的生物群系（森林）→磨难（暴风雨；光几乎消失；音乐消失）→ 灯光继续存在→ 地标重新点亮（音乐悲观的高潮）→ 开场布景，转变→ 标题和口号。

我们将其保留为 6 个镜头，每 1-2 个镜头一套，7 条叙述线 + 1 条对话线。 “一盏小灯”是灯笼；在另一个影片中，它可能是第一次提交、种子、字母、信号，或者根本没有携带光。

<a id="shots"></a>
## 镜头

| Shot | Camera |
|---|---|
|建立（全港，5.5–15）|很高很远（`[-17,15,38] → [-13,12,31]`，视场角36），缓慢推动。焦距44 m，光圈520；倾斜带固定在 34% 屏幕高度（没有要跟踪的字符）。|
|对话（码头，15–25.5）|表现媒介-高 3/4（向上约 5 m，距离 8–10 m，视场角 30），几乎静态漂移。每一帧都聚焦于主角，光圈300。|
|旅行（森林，25.5–35.5）|**横向跟踪**、摄影机稍微领先步行者（`monotone`前视），视场30，向上6.3 m；镜头前的蕨类植物附近模糊成黑色的形状；她走在最后一个前景树干后面。光圈380。|
|考验（风暴楼梯，35.5–49.5）|开始时是悬崖的巨大建立视图，逐渐进入跟随凸轮（37-39 秒），然后 **在她跪下时低下并关闭**（摄影机向上约 2.2 m，距离 6 m），并在她爬上时向后拉。光圈 140–170（更近 = 更少模糊）。|
|高潮（灯室，49.5–58）|表现媒介镜头上的英雄；点火后，上升拉回至塔广角（视场 30 → 40，光圈 150 → 320），焦点从英雄切换到镜头。|
|决议（港口末端+标题，58–76.5）|镜子的开口但更宽更高（`[-22,26,44] → [-27,33,55]`，视场42），焦点70，光圈380，倾斜带36％。|

规则：永远“俯视”世界（永远不要平视）；每个摄影机路径都是 2-7 个键的 `track()`（单调三次，无超调）；从摄影机到英雄 (`post.dof.focus = cam.position.distanceTo(hero + (0,.7,0))`) 的每帧焦距都会重新计算；在倾斜剪切中，锐带遵循英雄的投影屏幕高度（`tiltCenter`，夹紧 0.2–.8）。

<a id="score-structure"></a>
## 配乐结构

- **Voices（Kokoro，来自 `core/tts/tts.py`）**：旁白 `af_heart`，速度 0.82–.90（慢速，故事书）；任务给予者 `bm_george`，速度 0.84，在混音中以 7 kHz 低通，因此他位于“世界中”。 7 条叙述线 + 1 条对话线，每条 1-5.4 秒。检查`core/tts/asr_check.py`；将发明的名称放入 `asr` 字段（`Graywater`、`Ren`、`whisper would`），否则会悄悄标记它们。
- **音乐**：一首授权曲目，编辑为图片：Scott Buckley，*Precipice* (CC BY 4.0)，由 `music/edit.py` 剪切成五个部分（介绍垫 → **0.8 灯塔消亡时的呼吸**→ 连续构建森林和风暴 →**当火焰几乎熄灭时，在 42.0 处硬停止进入混响尾部**，只有其下的前奏垫 → 作曲家自己的构建 → **its D→G♭ 调性强拍放置在 53.500 s = 点火**，由最陡 < 250 Hz 开始（误差 < 5 ms）→ 跳转到标题的最终 E♭ 到达）。所有切割点均位于 `music/CUES.md` 中。选择一件与故事情节相符的作品；切入其中而不是缝合轨道。
- **Ambience 和拟音（`mix.py`，与 `core/audio/sfx.py` 合成）**：具有交叉渐变增益曲线的预设床（海港波浪 + 绳索吱吱声、火盆爆裂声、森林蟋蟀 + 树叶、暴雨 + 阵风），以及事件：灯灭“fwoomp”12.3，火柴罢工16.15，对话框上的UI提示音17.3，来自`sfx_events.json`的脚步声（木头/泥土/石头），每次闪光后0.25秒的雷声，阵风呼啸，寂静中的两次心跳，53.5的点火轰隆声（42 Hz下降+空气+高闪光），六个小铃声船亮了。
- **混音**：每条语音线路经过压缩并进行RMS匹配；总线调至语音−17、音乐−21、氛围−30、拟音 −27 dB RMS；音乐在语音下闪避约 2.2 dB，然后 **每行自动闪避** 将音乐 + 氛围在每行下方拉至约 10 dB（仅向下，从不向上；脚本打印每行实现的间隙，在示范中为 7-14 dB）； `tanh`软夹；最终响度为 `core/render/mux.sh`（两次通过响度范数 −14 LUFS，TP −1.2）。

<a id="palette--props"></a>
## 调色板和道具

示范是夜晚的影片：冷蓝色与温暖的琥珀色火焰的对比，强烈的绽放，沉重的晕影。

**分辨率和像素。**场景纹理在小画布上按像素绘制（`PX` 类、`px.js`）并使用 `NearestFilter` 上传；世界空间 UV（`worldUV`、`kit.js`）在每个表面上保留**24 px/m**。字符为 34×50 像素帧，每像素 `SPX = 1/30` 米（约 1.67 米高）。颜色来自 **坡道**（3-6 个样本），通过 4×4 Bayer 抖动的亮度进行选择；抖动带 `dz` 必须窄：字符为 **.22，纹理**为 0.45（更宽 = 到处都是棋盘噪声）。精灵获得自动 1 像素**塞劳特** 轮廓（`PX.outline(.3)`：精灵旁边的透明像素成为邻近颜色，向 `#16 0e 1e` 变暗）。

**调色板(夜晚).** 天空`#050818 → #101d3e → #2c4262`(地平线)、雾`#16223a`(港口)/`#152a48`(森林)/`#1c2334`(风暴)、月光`#8fa8e0`、半球 `#3a4c7a / #0a0a12`。防火窗`#ff9d4a`、`#ffae55`、`#ff8c3a`、灯笼`#ffb050`、灯塔`#fff0c8`。酷字填充`#9fb2e8`。英雄斗篷坡道`#2e0b14 … #c9503f`（深红色），围巾金色`#b08424`；守门员外套海军蓝 `#10131f … #5a6c98`，胡须灰色。墨水 `#1a1016`。

**材料。**仅盒子和圆柱体：带有石膏+木梁的房屋（`plaster`），木瓦屋顶（`shingles`），带钉点的木板（`woodPlanks`），沃利鹅卵石(`cobbles`)、层状岩石(`rock`)、bark/canopy/fern/grass/mushroom 精灵(`forest_art.js`)。树叶、草、蕨类植物、蘑菇、远处的船只和山脊是**广告牌**（实例很多）。窗口是发射像素窗格（`windowMat`，发射2.2）。 Fire 是 10 fps 的 6 帧像素图集广告牌 (`fire`)。 Sea 是一个自定义着色器：量化像素波纹、波峰带、向摄影机延伸的光反射柱、闪烁。

**Light 骨骼绑定结构每套。**一个昏暗的阴影投射月亮（DirectionalLight 1.1–1.2，2048地图）+半球填充+**实用点灯**（窗户8，路灯12–14，火盆 16 带阴影，灯笼 2.6–14 带阴影）+ **酷前填充**（`#9fb2e8`/`#8fa6e0`，1.2–1.8，范围 6–8 m）放置在英雄前方约 2 m 处。添加剂 `glow` 精灵位于每个光源上，因此绽放有东西可以抓住。

**后链**（`post_ts.js`、`makePost(renderer, scene, camera, 1920, 1080, { ssaa: 2 })`）：使用MSAA以2×（3840×2160内部）渲染→物理DOF（CoC = `aper × (1/focus − 1/z)` px，96抽头螺旋聚集，远样本不能在尖锐处渗漏）前景）**+ 倾斜移位** → UnrealBloom（强度 0.55，半径 0.75，阈值 0.85）→ vignette/grade（amt 0.62，暖色 0.1，对比度 0.2，饱和度 1.05）→ ACES 胶片，曝光 1.15。移轴剪切添加：`tiltAmt 17`、频带半宽 `tiltW .075`、羽化 `tiltF .3`（屏幕高度的分数）、`maxCoc ≥ 24`、饱和度 ×1.16、对比度 0.28。

**类型。** Cinzel 500/700（章节标签、标题）、Cormorant Garamond 斜体 500（字幕、口号）、Cormorant 500/600（对话文本、铭牌）。金色 `#d8c28e / #e2c989 / #c9a863`，羊皮纸白色 `#f3ead6 / #f6f0e2`。

运动建成：

- **精灵步，其他一切都在滑动。**步行循环使用 4 帧，每秒 6-10 帧 (`['w0','w1','w2','w3'][Math.floor(t*9)%4]`)，空闲时以 ~1.4 Hz 交替两帧，每隔几秒闪烁一次，姿势立即交换 (`upE → up → idle`)。 摄影机，灯光、粒子、光束和焦点以 60 fps 的速度每帧更新。
- **姿势是数据**：框架是由`drawWren` / `drawKeeper`绘制的参数对象（`{ step, arm:'low'|'fwd'|'up'|'hug'|'pour', kneel, lit, bob, hem, scarf, blink, closed, look }`）。通过添加表条目来添加姿势（或将 `extra` 传递到 `makeChar`）。
- **灯光在每个火焰上呼吸**：`flick(t, seed)`（三个正弦之和，±20％）；灯笼的 `lit` 值 (0–1) 重新绘制精灵中的火焰大小*并*驱动点光源 (`intensity ∝ lit^1.3`)、辉光不透明度和比例。
- **事件是`story.js` `T`中的时间戳**（灯塔闪烁11.5→熄灭12.35，锥度16.2，阵风40.6，昏暗41.3，黑暗42.0，重新点亮45.6，站立47.6，倾倒 52.6，点燃 53.5，梁 54.4，船舶 59.2）。场景与 `ss(seg(t,a,b))` 融合。
- **签名节拍：**灯塔闪烁两次并熄灭；火盆锥点燃了灯笼，两个精灵的影子跳到了木板上；阵风将火焰收缩成余烬（精灵`lit .27`），世界几乎变黑，然后火焰重新生长；镜头以曝光爆发（`exp(-(t-53.5)/.22)`）点燃，并且两个光束卡开始扫描；船上的灯每 0.7 秒就会亮起一盏，并向港口漂去。
- **天气是程序化的**：雨=风倾斜的线段（`rain`），闪电=脚本化的闪光曲线（`flash(t)`：150毫秒的袭击，下降，60毫秒的再次袭击，exp衰减），增强半球，“闪电”光，天空，云，海并一起曝光。

<a id="end-card"></a>
## 端卡

- **旁白字幕**：Cormorant Garamond 斜体 500、50 像素，`#f6f0e2`，以 y = H − 88 为中心，在柔和的水平暗带上（渐变，最大 0.38 alpha），阴影 10 像素。声音前 0.35 秒淡入，结束后 0.45–0.8 秒淡出。每个语音剪辑一行。
- **对话框**（用于在屏幕上说话的角色，而不是字幕）：1180×210像素，底部居中，海军蓝渐变`rgba(14,18,34,.86) → rgba(6,8,18,.9)`，2像素金色边框`rgba(214,190,130,.9)` +内部1像素线，金色菱形角；铭牌（Cormorant 600 34 px）与左上角重叠；身体 Cormorant 500 44 px，**打出超过 92% 的语音持续时间**；完成后闪烁金色 ▼ 插入符号；输入时向上滑动 14 px。一声轻柔的铃声标志着它。
- **章节卡**（0–5.5秒）：径向海军蓝背景`#11172a → #020308`，`CHAPTER  I`（Cinzel 500 34像素，10像素跟踪，`#d8c28e`）在带有钻石的金色装饰线上，然后是Cormorant的章节名称斜体 78 px，带有温暖的光芒；一个像素的余烬飘过。
- **标题**（67.4–76.4 秒）：屏幕调暗 50 %，`THE LAMPBEARER` 采用 Cinzel 700 118 像素，14 像素跟踪，垂直金色渐变 `#fff3cf → #e2c27c → #a8803e` 带发光；装饰品;标语为鸬鹚斜体 50 px； music/voice 信用在底部（24 像素，75% Alpha）。
- **结束信用额度（仅限本库的示范）**：我们的示范以**“LemoLab × Claude Opus 5.5”**结尾。它是标题卡的一部分（`ui.js` `title()`，默认情况下处于打开状态）：Cinzel 500 30 px，`#d8c28e` 为 85 % alpha，4 px 跟踪，以 y = 668 为中心，在标语和音乐制作人员之间在 70.6–71.6 秒内淡入淡出，它是不取代。 `?nocredit=1` 隐藏它。此签核仅属于本库的示范；用户的影片不带有 LemoLab 署名额度，也没有该卡的副本 — 当您调整 `ui.js` 时，请删除信用额度。
- 从相同数据导出 `.srt`（`tools/srt.py`：story.js `VO` + `voices/dur.json`，+0.5 秒保持，对话前缀 `OLD KEEPER:`）。


<a id="build-notes"></a>
## 构建笔记

```
styles/hd-2d/demo/
  index.html  main.js     page, renderer (ACES, PCF soft shadows), shot → set routing, tilt-shift driver (?tilt=1)
  story.js                DUR, SHOTS, event times T, VO lines (single source of truth)
  px.js                   PX pixel canvas, ramps + Bayer, surface textures, billboard / glow / blob
  kit.js                  worldUV, mat/mesh/box, cached materials, house, crate, barrel, pixel fire, windows, ridges
  fx.js                   sky, stars, pixel sea shader, particles, rain, shaft, beamCard, flick
  chars.js                procedural pixel characters (Wren, Old Keeper), pose tables, atlas, makeChar
  harbor.js forest.js(+forest_art.js) cliff.js   the three sets; each exports build*() → { scene, update }
  ui.js                   Canvas2D overlay: chapter card, dialogue box, subtitles, title, fades, credits
  post_ts.js              makePost: DOF + tilt-shift + bloom + grade (local copy of core/three/post.js)
  lines.json vo_times.json sfx_events.json   TTS lines, voice start times, foley timestamps
  music/edit.py src/      score edit of "Precipice" → music/score.wav, CUES.md, measure.json
  mix.py                  ambience + foley + voices + ducking → mix.wav
  tools/srt.py  tools/render_range.mjs  tools/sheet/index.html   srt export, partial re-render, sprite sheet page
```

来自存储库根目录的所有命令。 `.venv` 是共享的 Python 环境（kokoro-onnx、faster-whisper、librosa）。

```sh
PY=.venv/bin/python; D=styles/hd-2d/demo

# 0. fresh clone: voices/*.wav, music/score.wav and mix.wav are git-ignored (rebuilt below); if music/src/ is empty, fetch the source
curl -L -o $D/music/src/sb_precipice.mp3 https://www.scottbuckley.com.au/library/wp-content/uploads/2021/01/sb_precipice.mp3

# 1. voices (Kokoro) + whisper check → voices/*.wav, dur.json, words.json
$PY core/tts/tts.py $D/lines.json $D/voices
$PY core/tts/asr_check.py $D/lines.json $D/voices      # demo: 1 expected DIFF (n1 "Graywater" → "gray water")

# 2. score edit → music/score.wav (+ CUES.md, measure.json); set OUT_DIR=... to write elsewhere
(cd $D/music && ../../../../.venv/bin/python edit.py)

# 3. mix → demo/mix.wav (optional arg: another output path)
$PY $D/mix.py

# 4. subtitles → styles/hd-2d/hd-2d.srt
$PY $D/tools/srt.py

# 5. review stills of the tilt-shift cut (≈0.1–0.2 s per frame)
node core/render/still.mjs $D 8 16.9 30.5 42.8 53.8 62 71 --q tilt=1 --out $D/out/review

# 6. render the TILT-SHIFT CUT (the version in the library): 4590 frames at 60 fps
#    measured 26–37 fps with 2 workers (≈2.5 min); the shipped file used 6 workers
node core/render/video.mjs $D --fps 60 --workers 2 --q tilt=1 --out $D/out/video_tilt.mp4

# 7. mux: loudnorm −14 LUFS, grain 0 (pixel art: no film grain)
sh core/render/mux.sh $D/out/video_tilt.mp4 $D/mix.wav styles/hd-2d/hd-2d.mp4 60 0
```

`?tilt=1` 是进行移轴剪辑的原因：它是 `post_ts.js` 内的 **渲染时后期效果**（不是对完成的视频进行第二次处理）。如果没有它，您将获得纯 DOF 版本。其他页面切换：`ss=1`（无超级采样，预览速度更快）、`only=harbor|forest|cliff`（构建一套）、`nobloom`、`nodof`、`noglow`、`nocredit=1`（隐藏结尾信用线）。

**部分重新渲染**（例如，更改标题卡后；这就是将片尾字幕添加到已发货的影片的方式）：仅渲染尾部并将其拼接到现有的`out/video_tilt.mp4`上（帧0-4019不受标题卡更改影响），然后再次复用。首先备份当前的影片（`hd-2d_v1.mp4`）。音频未受影响（相同的 `mix.wav` → 位相同的解码音频）。
```sh
node $D/tools/render_range.mjs 67 76.5 --workers 2 --q tilt=1 --out $D/out/tail.mp4          # 570 frames ≈ 15 s
ffmpeg -y -i $D/out/video_tilt.mp4 -i $D/out/tail.mp4 -filter_complex \
  "[0:v]trim=end_frame=4020,setpts=PTS-STARTPTS[a];[1:v]setpts=PTS-STARTPTS[b];[a][b]concat=n=2:v=1:a=0[v]" \
  -map "[v]" -c:v libx264 -preset medium -crf 14 -pix_fmt yuv420p $D/out/video_tilt_new.mp4   # 25–150 s (CPU-bound, slower when other renders run)
sh core/render/mux.sh $D/out/video_tilt_new.mp4 $D/mix.wav styles/hd-2d/hd-2d.mp4 60 0          # 35–245 s, same caveat
```

当您更改故事时：首先编辑 `story.js`，然后将语音开始时间复制到 `vo_times.json`（mix.py 读取该文件，而不是 story.js），使 `sfx_events.json` 足迹与场景的行走帧保持同步，并将提示常量移动到场景顶部`music/edit.py`（`T_CAESURA`、`T_SILENCE`、`T_HIT`、`NARRATION`）。

我们使用示范的道具和数字遇到的陷阱：

- **到处都是棋盘**：斜坡上的宽抖动带。在精灵上保持 `dz` ≈ .22，在纹理上保持 ≈ .45。
- **灯笼吹出了精灵**：位于广告牌平面上的点光源使其饱和。将灯光 **0.42–0.45 m 从灯笼射向相机** (`lp + toCam * .45`)，并在着色器中的森林帽精灵照明中（`outgoingLight = min(outgoingLight, diffuseColor.rgb * 1.35 + emissive)` 通过 `onBeforeCompile`）。
- **广告牌后面的灯不会照亮它**（它只有正面法线）。始终在英雄前方约 2 m 处添加一个很酷的前补光灯。
- **面向摄影机的圆柱光束产生NaN**；布卢姆将它们分散成黑色的大块。使用 `beamCard`（轴对齐的广告牌条，当转向摄影机时会逐渐消失）并让发光精灵接管（`face` 因子会放大灯塔发光）。
- **海反射柱除零**：用​​`max(.35, …)`夹紧宽度。
- **风暴太暗，无法在第一遍中读取**。在故事黑暗节拍之外添加“可读性”填充：半球+1.0，太阳+1.3，天空+.35（`cliff.js`中的`ext`术语），即环境中间色调上大约×2-2.5，并且仅在火焰几乎熄灭的节拍期间让它降至零。
- **远处的船被 fog/geometry** 隐藏：`depthTest = false` + `renderOrder 5` 在那些发光精灵上。
- **镜头上的倾斜移位，无字符**：跟踪器无任何可跟随；根据镜头 (`TILT_C`) 使用固定的带高度。
- **倾斜移位和遮挡**：倾斜模糊被折叠到与深度DOF相同的符号CoC中（带上方=远，下方=近），因此聚集保持“远不能在锐利近处渗出”规则；不要将其添加为单独的模糊通道。
- **几乎相同的帧在闪光灯周围发散**：点火爆发以0.22秒的时间常数衰减，因此53.8秒的静止图像与邻近的60fps帧明显不同。这是预期的，不是错误。
- **Node 渲染脚本可能不会在 `done` 之后退出 **，因为静态服务器保持连接处于活动状态（因此 `demo/tools/render_range.mjs` 以 `process.exit(0)` 结尾）。打印 `done` 后，输出文件即完成。

<a id="engine-reference"></a>
## 发动机参考

<a id="page-contract-mainjs"></a>
### 页面合约（`main.js`）
`window.render(t)` 选择镜头 (`shotAt(t)`)，将其映射到集合 (`SET_OF`)，将 DOF 通道指向该集合的场景，重置后期默认值（bloom .55/.85、曝光 1.15、暖色 0.1、饱和度 1.05、 vignette .62)，调用 `set.update(t, shot, camera, post, renderer)`，如果是 `?tilt`，则应用倾斜移位，渲染作曲家，然后绘制叠加层 (`drawOverlay(t, shot)`)。所有机组共用一台`PerspectiveCamera(32, 16/9, .3, 2000)`；每组每帧设置 fov/position/lookAt。

<a id="modules-and-key-functions"></a>
### 模块及关键功能
|模块|功能|什么/关键参数|
|---|---|---|
|`px.js`|`new PX(w,h)`|`.set/.get/.rect/.fill(f)/.ellipse/.poly/.line/.outline(k,tint)/.done()` → 帆布|
| |`ramp(cols, dz=.45)`|`(v,x,y) → rgb` 带拜耳抖动； `dz` = 抖动带宽|
| |`texOf(canvas, {repeat, mip, linear})`|最近的滤镜纹理|
| |`woodPlanks / cobbles / rock / plaster / shingles / ground(w,h,o)`|程序表面画布（`seed`、`cols`、`pw`、`len`、`cell`、`beams`、`snow`）|
| |`billboard(tex, wM, hM, {ax, ay, em, emCol, emI, shadow, receive})`|直立照亮的精灵平面（Lambert + alphaTest .5），带有自定义 depth/distance 材质，因此可以投射剪切阴影|
| |`glow(col, size, i)` · `blob(r, a)` · `radialTex`|添加光环精灵 · 地面接触阴影|
|`kit.js`|`worldUV(geo, tile)` · `mat(canvas, o)` · `mesh(geo, m)` · `box(w,h,d,m)`|平面 UV 为法线，因此纹素密度是恒定的 (`tile = canvas.width / 24` m)|
| |`mats()`|缓存 `plank, plankDark, beam, wall, wall2, wall3, roof, roof2, roof3`|
| |`house({x,z,w,d,h,wall,roof,door,windows,upper,side,chimney,ry})`|带发射窗的木屋 (`g.userData.windows`)|
| |`crate(s)` · `barrel(r,h)` · `fire(size,{seed,i})` · `windowQuad` · `ridge(wM,hM,col,seed)`|道具； `fire.userData.update(t, cam, scale)`|
|`fx.js`|`sky({top,mid,hor,moonDir,moonCol})` → `{mesh,u}`|渐变穹顶+月晕； `u.k` = 亮度|
| |`stars(n, seed)` · `sea(size,{ppm,deep,shallow,crest})` → `{mesh,u,setLights([{p,c,i}])}`|每帧设置 `u.t`、`u.camPos`、雾服、`u.bright`、`u.calm`|
| |`particles(n, fn(i,t,o), {soft, blend})`|确定性CPU粒子； `fn` 填充 `o.x,y,z,a,s,r,g,b`；致电 `.userData.update(t)`|
| |`rain(n, box, {speed,len,opacity})` · `.userData.update(t, [windX,0])`|倾斜条纹|
| |`beamCard(len, w0, w1, col, {k, fall})` · `.userData.aim(origin, dir, cam)` → 侧面因素|永不露出边缘的光束|
| |`flick(t, seed)`|火焰闪烁倍数 ≈ 1 ± .2|
|`chars.js`|`makeChar('wren'|'keeper', extraPoses)` → `{root, mesh, frame(name), face(cam, flip), lanternPos(name, flip)}`|34×50 px 图集 + 发光图集（灯笼玻璃）； `root.userData.char` 是倾斜跟踪器所寻找的|
| `post_ts.js` | `makePost(renderer, scene, cam, w, h, {ssaa, ao})` → `{composer, dof, bloom, vig}` | `dof.focus` (m), `dof.aper` (px·m), `dof.maxCoc` (px), `dof.tiltAmt/tiltC/tiltW/tiltF`; `vig.uniforms.amt/warm/sat/contrast/fade` |
|`ui.js`|`drawOverlay(t, shot)` · `overlayReady()`|读取 `story.js` `VO` 和 `voices/dur.json`|
|`/core/lib.js`|`track(keys)` · `monotone` · `seg` · `ss` · `eio` · `eo` · `lerp` · `clamp`|摄影机路径和缓动|

<a id="minimal-new-set"></a>
### 最小新套装
```js
// myset.js — a lantern-lit alley; register in main.js: sets.alley = buildAlley(); SET_OF.alley = 'alley'; add { id:'alley', a, b } to story.js SHOTS
import * as THREE from 'three';
import { cobbles, glow } from './px.js';
import { mat, mesh, house } from './kit.js';
import { sky, particles, flick } from './fx.js';
import { makeChar } from './chars.js';
import { track, seg, ss } from '/core/lib.js';

export function buildAlley() {
  const scene = new THREE.Scene(); scene.fog = new THREE.FogExp2('#16223a', .03);
  const SK = sky(); scene.add(SK.mesh);
  const moon = new THREE.DirectionalLight('#8fa8e0', 1.1); moon.position.set(-20, 30, -20); moon.castShadow = true; moon.shadow.mapSize.set(2048, 2048);
  scene.add(moon, new THREE.HemisphereLight('#3a4c7a', '#0a0a12', .9));
  scene.add(mesh(new THREE.BoxGeometry(30, .4, 12).translate(0, -.2, 0), mat(cobbles(96, 96))));
  scene.add(house({ x: -4, z: -5, w: 6, d: 5, h: 4.5, door: 1.2 }), house({ x: 4, z: -5, w: 5, d: 5, h: 5, wall: 'wall3', roof: 'roof2' }));
  const hero = makeChar('wren'); scene.add(hero.root);
  const lamp = new THREE.PointLight('#ffb050', 3, 10, 2); lamp.castShadow = true; lamp.shadow.bias = -.004; scene.add(lamp);
  const halo = glow('#ffc070', 1.1, 1.2); scene.add(halo);
  const fill = new THREE.PointLight('#9fb2e8', 1.5, 7, 2); scene.add(fill);                 // cool front fill: never skip
  const dust = particles(80, (i, t, o) => { o.x = (i * 7.3 % 20) - 10 + t * .1; o.y = (i * 3.1 % 4); o.z = (i * 5.7 % 6) - 3; o.a = .3; o.s = .05; o.r = .7; o.g = .8; o.b = 1; }, { soft: 1 });
  scene.add(dust);
  const camP = track([[0, [-2, 5.5, 10]], [8, [2, 5, 9]]]), camL = track([[0, [-1, .8, 0]], [8, [2, .8, 0]]]);

  function update(t, shot, cam, post) {
    const lt = t - shot.a;
    cam.position.set(...camP(lt)); cam.fov = 30; cam.updateProjectionMatrix(); cam.lookAt(...camL(lt));
    const x = -3 + ss(seg(lt, .5, 7.5)) * 6, walking = lt > .5 && lt < 7.5;
    hero.root.position.set(x, 0, 0); hero.frame(walking ? ['w0', 'w1', 'w2', 'w3'][Math.floor(t * 9) % 4] : 'idle0'); hero.face(cam);
    const lp = hero.lanternPos('w0'), toCam = cam.position.clone().sub(lp).setY(0).normalize();
    lamp.position.copy(lp).addScaledVector(toCam, .45); lamp.intensity = 2.6 * flick(t, 3); halo.position.copy(lp);   // light 0.45 m toward the lens
    fill.position.set(x + .4, 1.6, 2.2);
    dust.userData.update(t);
    post.dof.focus = cam.position.distanceTo(hero.root.position.clone().setY(.7)); post.dof.aper = 350; post.dof.maxCoc = 22;
  }
  return { scene, update };
}
```
然后用`node core/render/still.mjs styles/hd-2d/demo <t> --q 'tilt=1&only=alley'`检查（将`alley`添加到`main.js`中的`ONLY`开关）。
