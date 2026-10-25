<a id="halftone-dossier--our-demo"></a>
# 半色调档案 — 我们的示范

众多例子中的一个。请勿重复使用其故事、弧线、镜头、道具或时间安排。

示范：*胖橘案卷案例文件：Chubby*（30.0秒）·`halftone-dossier.mp4`·来源在[`demo/`](demo/)·引擎：一个独立的`demo/index.html`（SVG场景图+两个Canvas 2D覆盖），逐帧渲染剧作家无头 Chromium，1920×1080 / 30 fps； 配乐和 `demo/music.py` 中合成的 SFX。


**示范的屏幕文本为中文**（标题卡、说明文字、图章）。没有旁白。请参阅下面的“制作英文版本”。

<a id="story--structure"></a>
## 故事与结构

对一只胖乎乎的橙色猫的模拟调查。结构是一份卷宗：**标题→指控→嫌疑人简介（照片）→计数01 / 02 / 03→“摘要”→判决印章→原因→结案**。角落里的案例编号 HUD 和章节芯片（“罪状 01 · 测试重力”）让观看者保持导向。这个笑话是官僚主义的严肃性（案件编号、身高表、邮票、“计数 01”）与琐碎、可爱的主题之间的差距。

它响亮但可读：每 2-4 秒卡片一个想法，一个大标题，一个视觉笑话，一条标题行。

示范如何使用风格特有表现手法：

|原生电源|示范如何使用它|
|---|---|
|**指控框架**|任何主题都会成为“针对 X 的案件”。一种产品、一种习惯、一只宠物、一位同事、一个历史人物——列出它的“罪行”。|
|**编号计数**|每个节拍都是计数 01/02/03，后面有一个巨大的半色调数字。 3 秒是 30 秒的最佳时间；五次，持续 60 秒。|
|**邮票**|每一个判决都是一个物理印记：惯犯（累犯）、无罪释放（无罪释放）、结案（结案）。邮票是影片的标点符号。|
|**照片**|正面拍摄对象位于带有铭牌和闪光灯的高度表前。非常适合介绍任何“嫌疑人”。|
|**展品卡**|“总结”节拍：计数结果显示为三张带有图标的固定证据卡，然后摇晃。|
|**点密度=情感**|圆点在英雄周围膨胀成光环，在画面边缘堆积以产生紧张感，放射状绽放以带来欢乐。|

我们如何塑造这个主题：一个 **可爱的罪犯** 和三个 **特定的、视觉的** 不当行为（一个杯子掉落，04:00 的时钟，一个充满垃圾的文件）。我们的转折是一个与证据相矛盾的判决（“每项罪名都有罪 → 无罪释放：太可爱了”）。

**演示弧（30秒，120 BPM，一小节= 2秒）**：标题（1小节）→指控+第一个印记（1小节）→照片（2小节）→计数01（2）→计数02（2，调色板的“夜晚”变化）→计数03（2）→总结+构建（1）→判决掉落的印章 (1) → 原因 (1) → 案件已结 + 信用 (2)。每个切口都位于小节线上。

<a id="shots"></a>
## 镜头

摄影机是一个 2D 组 (`#cam`)；没有3D。

|打|摄影机|
|---|---|
|标题/指控|锁定，正面，每个节拍都有 0.6 % **beat 脉冲**（`pulse`，仅在“凹槽”部分）。|
|面部照片，摘要|场景组中的缓慢推入：1 → 1.05 超过 4 秒（照片），1 → 1.08 缓入超过 2 秒（摘要，紧张感上升）。|
|影响|`SHAKES = [t0, amplitude px, duration]`：第一个标记处为 16 px，杯子碰撞处为 14 px，判决处为 26 px / 0.45 s，小着陆时为 5–7 px；二次衰减，x/y. 上的不同 sin/cos 频率|
|面部照片闪光灯|两个摄影机闪光帧（0.3 秒内白色叠加 0.95 → 0），吉祥物眯着眼睛。|
|结束|在 29.25–29.95 秒内褪色为海军蓝 `#1D2340`。|

像打印页面一样平面和正面构图：标题位于左上角，英雄位于右中心，标题栏位于底部中心（y = 980），HUD 位于角落。

示范运动数字：CHUBBY 字母在 0.2 秒内下降 700 像素，间隔 0.25 秒（每 8 个音符一个），然后用阻尼 `cos` 摆动挤压。标记猛击 (`stampAnim`) 0.09 秒从 2.6× 到 1×，并在 23.0 秒时出现白色闪光。壁球落地：大曲度为 17.45，卷曲度为 26.6 (`sq = 1 − k·e^(−a·7)·cos(a·20…22)`)。运行周期 (`runCycle`)：4 个胶囊腿以 30 rad/s 摆动 ±50°，身体摆动 `|sin(28t)|·12`，拉伸 `scaleX 1 + 0.35·speed`，4 条速度线。点擦拭 (`wipeUpdate`)：80 px 网格，r → 62，以每次切割为中心 0.44 s； 22点和24点的削减是下降的硬削减。原始“动作语言”部分完整内容：

- **一切都以过冲**进入：`E.back`（过冲1.9）超过0.3–0.45秒。对象从框架下方升起 (`lerp(1200, 470, E.back(...))`) 或从 0 开始缩放 (`pop()`)。
- **每个角色的流行** (`charsPop`)：每个字形下降 30–100 px，并通过挤压和拉伸进行缩放，错开 0.05–0.08 秒（小字幕为 0.02 秒）。头条新闻总是这样构建的；永远不要淡入文本。
- **标题字母下降并挤压**：CHUBBY字母在0.2秒内下降700像素，间隔0.25秒（每八分之一音符），然后用阻尼`cos`摆动挤压。
- **邮票大满贯** (`stampAnim`)：0.09 秒从 2.6× 到 1× (`E.in`)，然后是 5 % 阻尼弹跳；在同一瞬间，摄影机震动 (`SHAKES`)、白色闪光 (23.0 秒) 和印记 SFX。
- **挤压着陆**：着陆的角色（在17.45处徘徊，在26.6处卷曲）使用`sq = 1 − k·e^(−a·7)·cos(a·20…22)`和`scale(1/sq, sq)`，因此体积被保留。
- **空闲寿命**：呼吸（±2％y轴刻度），尾巴摇摆，耳朵抽搐，在脚本时间眨眼（`blinkAt`），hearts/Zz循环，星星闪烁，REC点以1 Hz闪烁，时钟冒号闪烁。
- **运行循环** (`runCycle`)：4个胶囊腿在30 rad/s处摆动±50°，身体鲍勃`|sin(28t)|·12`，加上拉伸`scaleX 1 + 0.35·speed`和后面的4条速度线。
- **线沸腾速度为 10 fps**在角色上，当他们的变换以 30 fps 的速度移动时——手绘的感觉，没有位置抖动。
- **Transitions 是一个点擦除** (`wipeUpdate`)：80 px 的圆网格增长到 r = 62（全覆盖），并以每次剪切为中心在 0.44 秒内收缩，有对角线延迟；每个切口都有自己的擦拭颜色 (`WIPES`)。场景切换发生在画面被完全覆盖时。一些切口（22、24）是为了对比而在水滴上进行硬切口。

<a id="score-structure"></a>
## 配乐结构

- **无声音。** 影片由卡片和音乐携带；如果某个主题需要旁白，请添加旁白，但将字幕保留为主要频道。
- **配乐**（`music.py`，44.1 kHz 立体声，完全合成，种子 RNG → 位相同输出）：120 BPM，小节 = 2 秒，C 大调，每小节一个和弦（`PLAN`，15 小节）。乐器：合成器 kick/snare/clap/hat、八分音符模式上的方形低音、三角垫、**马林巴式 `pluck`** 旋律（基本音 + 3.99 × 部分音），带有安静的八度回声、`pizz` 拨奏和手指潜行夜间部分的捕捉（第 6-7 小节 = 计数 02），**建造**的军鼓滚动 + 上升正弦扫频（第 10 小节 =“总结”），**降低** 使第 11 小节的前半部分为空，因此判决标记单独落在23.0，然后是音乐盒 `bell` 尾奏和最后的铃声琶音。
- **SFX跟随图片**（`music.py`末尾的SFX表，从`index.html`复制的时间）：每个标题字母都会弹出，头部偷看的boing，`stamp()`（音调下降的繁荣+点击；`big=True`添加每张邮票都会发出一声噼啪声，`shutter()` 代表照片闪光，合成 `meow()`（共振峰扫频 /i/→/a/→/u/），`clink` 代表杯子轻推，`crash_glass()` 在休息时，每次擦拭前发出嘶嘶声，`plop` + 一系列`key_click`代表趴在键盘上的猫，`sparkle`代表“太可爱了”。
- **掌握**：峰值归一化 ×1.6 → `tanh` 软剪辑 ×0.9 → 1.2 s 淡出。在多路复用器下，−1.6 dB 和 AAC 256 k / 48 kHz → 示范测量 −14.5 LUFS 集成值，−1.2 dBTP。
- 对于新的影片：保留条形网格，重写 `PLAN`（该条形为 intro/full/sneak/build/drop/outro/end）并将 SFX 列表重新计时到新的场景时间。保持一个声音“邮票前的沉默”。

<a id="palette--props"></a>
## 调色板和道具

**调色板**（`index.html` 第 56–60 行中的 `C`） — 仅使用这些：

|代币|十六进制|使用|
|---|---|---|
|`paper`|`#F4ECDD`|灯光场景背景|
|`navy`|`#1D2340`|所有轮廓、正文、标题栏、淡出颜色|
|`blue`|`#2E55D6`|标题背景、光晕点、表格、一层墨迹|
|`pink`|`#FF5A87`|重音、重合失调阴影、标题偏移、判决印记|
|`yellow`|`#FFC628`|突出显示单词、数字、星爆、文件夹|
|`orange` / `ored`|`#F58A34` / `#D9621E`|吉祥物的毛皮/条纹|
|`cream`|`#FFF4E2`|腹部，爪子，黑暗中的文字|
|`red`|`#E8384F`|邮票、“17”、REC 点|
|`night` / `night2`|`#18203F` / `#2A3568`|夜景背景/点|
|`mint`、`skin`|`#56C29E`, `#F7C9A1`|仅微小的口音|

**H半色调** (`halftone()`)：单个 SVG 路径中的旋转圆网格。 `step` 20–26 px，屏幕 `angle` 每层不同 (15°/20°/25°/30°/45°/60°/70°)，点半径 = `density × step × maxK` 和 `maxK` 0.6–0.72（约 0.7 个点在以下位置合并为固体墨水）全密度）。密度字段：`radial(cx, cy, R, pw)`（用于 halos/blooms/corner 发光）、`edge(R, pw)`（用于填充帧边缘的小插图）或线性斜坡 `(x,y) => 0.25 + 0.75*clamp((y-250)/650)`（用于“从上方照亮”填充）。将第二层放入 `class="mul"`（混合混合乘法）中，以便墨水叠印。

**H半色调填充数字**：巨大的 Bagel Fat One 数字（700–760 px）从右边缘渗出，填充平整（`yellow` / `#FFD3DF`），然后用剪裁到字形的较暗半色调套印（`<clipPath>`相同的 `<text>`）。第 513-518 行和 709-714 行。

**纸张**（`buildPaper()`、`#paper`画布，乘以所有内容，构建一次）：96×54随机图块升级（242–255灰色）用于斑点+每像素噪声±13，带有-4蓝色偏差（温暖）+径向晕影`rgba(120,100,80,.35)` + x = 960 处的微弱折叠线。黑暗场景也会成倍增加，这使它们保持“打印”状态，而不是发光。

**粮食**（`drawFx(frame)`、`#fx` 画布，每帧）：520 个奶油色斑点（r 0.6–2.4，α .75）+ 90 个海军蓝斑点，每 2 帧重新播种 — 印刷品上有灰尘，而不是影片谷物。

**线沸腾**（`#boil` SVG过滤器）：`feTurbulence` 0.022→`feDisplacementMap`规模5，每0.1秒重新播种（`render()`设置`boilT`种子， 40 种子周期），加上细墨粒遮罩（0.75 频率），每次填充都会吃一点。仅将其应用于角色和手绘道具，切勿应用于文本、半色调、HUD 或标题。

**角色**：厚实的卡哇伊形状，带有**7像素海军蓝轮廓**（`LW`），扁平填充，奶油色belly/paws，粉红色的耳朵内侧和脸颊，深橙色条纹为圆头笔划。闪亮的大眼睛（海军蓝椭圆形 + 两个奶油色高光）可以眯起、闭上成快乐的弧线（`happy`）或眨眼。每个身体姿势共享一个头部 (`catHead`)。

**版式**（`F` 第 61-64 行；所有 Google 字体，OFL）：
- 标题：**Noto Serif SC 900**，100–230 像素，在 x ≈ 120–170 处左对齐，带有 **重合失调阴影**（`chars(..., {shadow:{fill: pink|yellow, dx: 8, dy: 8}})`，多重绘制）。
- 显示/数字：**Bagel Fat One**（CHUBBY 330 px、01/03 700+ px、99+、17、18:00、Zz）。
- 可爱感叹词：**ZCOOL KuaiLe**（喵。呼噜～啪！太可爱了）。 《太可爱了》使用了奶油色填充+16px海军蓝描边+蓝色偏移阴影。
- 数据/HUD：**JetBrains Mono 800**（案例编号，“PANG JU，O.”，时钟 04:00，厘米标尺，文件名）。
- 说明文字和图章：**Noto Sans SC 900**。

**邮票**（`stampEl`）：双圆角矩形（外边框10–14 px，内0.35×）+ 120–210 px文字，全部经过`#stampInk`（位移7+粗墨粒遮罩），因此墨水斑驳，边缘很粗糙。不透明度 0.93，倾斜 −10° … +12°。

**道具和噱头**：星爆（24点星星，黄色+海军蓝笔划，红色“啪！”），对话气泡（奶油色，海军蓝6像素笔划，尾部补丁），心形（`heartPath`），五彩纸屑（5色矩形，翻转`scaleY`），放射状射线（28 个交替楔形物，旋转 12°/s）、爪印、便利贴、带有打字垃圾的笔记本电脑、数字时钟。所有平面填充+海军蓝轮廓。

<a id="titles--subtitles"></a>
## 标题和副标题

- **卡片是字幕。** 每个节拍都有一个标题（衬线 900，每个字符流行），并且用于计数，一个 **标题栏** (`caption`)：海军蓝圆形药丸 (r 14)，带有粉红色偏移阴影（+8/+8，乘法），Noto Sans SC 900 46 px 奶油色，**关键字为黄色或粉色** 通过 tspans。它在标题后约 1 秒突然出现（0.4 秒，轻微 -1.2° 倾斜），并保持到场景结束（≥ 1.8 秒）。
- **HUD** (`hudUpdate`)：芯片上方左上角的案例编号（`案卷 No.2026-CAT-001`、JetBrains Mono 22），带有部分 + 标题 (`罪状 01 | 测试重力`)；右上角的 REC 点 + 日期。黑暗场景中颜色反转。隐藏在标题卡上，标题卡有自己的角标签。
- **标题卡**：蓝色背景，奶油色大百吉饼胖一字（对象的昵称），带有海军蓝偏移阴影，字幕线在下面，吉祥物从字母后面偷看，爪子在上面。
- `halftone-dossier.srt`列出卡片（中文+英文光泽）；没有语音可转录。

<a id="end-card"></a>
## 端卡

**尾卡**：带有文件标签的案件文件夹、沉睡的吉祥物、结案印章以及带有结束笑话的对话气泡（「本片由克劳德用代码一帧一帧画完。胖橘表示：全程没有配合。」）。我们的示范以“LemoLab × Claude Opus 5.5”结尾（× = U+00D7）。此签核仅属于本库的示范；用户的影片没有 LemoLab 积分，也没有这张卡或其结尾笑话的副本。在示范中，它是片尾卡底部的一条中心线（2026-09-26 添加，`index.html` S10）：`txt(g, 'LemoLab × Claude Opus 5.5', {x: 960, y: 1040, 'font-size': 30, 'font-family': F.mono, 'font-weight': 800, fill: C.navy, 'text-anchor': 'middle', 'letter-spacing': 3})`，在 27.6–27.9 秒（气泡后 0.3 秒）内以 12 像素上升淡入流行音乐）并保持直到海军蓝褪色。放在文件夹下的空带里；切勿遮盖吉祥物或邮票。按字面意思在源中写入字符串，以便 `init()` 预加载其字形。

<a id="making-an-english-version"></a>
## 制作英文版

**制作英文版**（全部在`index.html`中）：替换每个`scene()`中的字符串文字（`chars()`中的标题，`caption()`部分，`stampEl()`单词中， plate/profile/folder 文本，第 905-907 行结束气泡）、HUD `chips` 数组（第 948-951 行）和 `txt(... 'CASE FILE · 2026')`；将 `F.serif`/`F.cute`/`F.sans` 交换为拉丁显示面（例如，黑色平板或 Bagel Fat One 用于标题，圆形显示面用于感叹词），将它们添加到 `fetch_fonts.mjs` 中的 `fams` 和预加载列表中`init()`（第1069行）；设置 `lang="en"`。宽度是在构建时测量的 (`measure()`)，因此条形图和图章会自行调整大小，但英语的运行时间要长 2-3 倍：降低标题大小 (230 px → ~​​130 px)，将图章缩短为 1-2 个单词（有罪、无罪、结案），并使用较小的 `charsPop` 交错（0.02-0.03 秒）。

<a id="build-notes"></a>
## 构建笔记

```
styles/halftone-dossier/demo/
  index.html        the whole film: helpers, halftone, paper, cat rig, 10 scenes, HUD, wipes, render(t)
  render.mjs        Playwright renderer: stills | video [workers] | mux [out.mp4]
  music.py          score + SFX + master → music.wav (seeded, deterministic)
  fetch_fonts.mjs   downloads the 5 Google Fonts families → fonts/*.woff2 + fonts.css
  fonts/ fonts.css  local font slices (OFL)       CREDITS   licences
  stills/           styleframe.jpg                   out/     intermediates (gitignored)
```
从存储库根目录运行（`lemo-opuscar/`）；脚本内的所有路径都相对于 `demo/`。

1. （仅在更改字体时） `cd styles/halftone-dossier/demo && node fetch_fonts.mjs` — 需要网络；重写 `fonts/` + `fonts.css`。
2. Voice/TTS：没有这种风格（跳过）。如果添加旁白，请先添加时间场景。
3. 音乐：`.venv/bin/python styles/halftone-dossier/demo/music.py`→`demo/music.wav`（约1秒）。传递一个路径到别处写入。
4. 评论：在 Chrome 中打开 `demo/index.html?t=11.2`，或 `node styles/halftone-dossier/demo/render.mjs stills 3.3 7.2 11.25 23.3 27.8 --dir out/review`（每帧约 0.25 秒）→ `demo/out/review/t_*.png`。
5. 渲染：`node styles/halftone-dossier/demo/render.mjs video 2` → `demo/out/seg_*.mp4` + `demo/out/video_noaudio.mp4`（CRF 12 主控）。 900 帧 ≈ 0.24 s/frame/worker → 2 个工作人员在一台空闲机器上大约需要 2 分钟（在其他 6 个渲染共享 CPU 时测得 5.6 分钟）。
6. 复用器：`node styles/halftone-dossier/demo/render.mjs mux` → `styles/halftone-dossier/halftone-dossier.mp4`（x264 CRF 16 + −1.6 dB 的音乐，AAC 256 k/48 kHz；约 15 秒；从同一母版逐位再现已发布的视频流）。通过另一条路径以避免覆盖已发布的影片。

<a id="pitfalls-we-hit"></a>
### 我们遇到的陷阱

- **Fonts必须在`buildAll()`**之前加载：布局使用canvas `measureText`；如果尚未加载 Google-Fonts unicode-range 切片，则使用后备字体和字形重叠来计算每个字符的位置。 `init()` 针对 **整个页面源** 预加载每个系列（`documentElement.innerHTML` 包括脚本，因此代码中的每个字符串文字都被覆盖），然后再次针对构建的 SVG 文本。您在运行时生成的任何字符串必须仅包含也确实出现在文件中某处的字符（或 ASCII）。
- 使用 `font-display: block`（已在 `fonts.css` 中）— `swap` 在第一个渲染帧中显示后备字形。
- `<clipPath>`id 是全局的：每个剪辑numeral/table需要一个唯一的 ID (`num01`, `num03`, `tclip`).
- 保持煮沸过滤器远离文本和半色调：20 px 点上的位移会将它们变成糊状，并使文本难以辨认地摆动。
- 按时间窗口划分的场景为shown/hidden；场景的更新仅在其打开时运行，因此任何在其提示之前必须不可见的元素都需要一个用于 `t < t0` 的显式 `op(…, 0)`（请参阅 `charsPop`、`stampAnim`）。
- 点擦除必须在剪切时达到完全覆盖（80 px 网格上的 r 62），否则硬场景切换会显示出来。
- 100% 白色闪光读取为丢帧；判决闪光上限为 0.5。
- `index.html` 中未使用的剩余部分：`#ink` 过滤器、`charsIdle()`、`E.elastic` — 已定义，从未调用。

<a id="engine-reference"></a>
## 发动机参考

一切都在 `demo/index.html` 中。它被设计为一个文件；要启动新的影片，**将`demo/`复制到新文件夹并重写`buildAll()`**。可重复使用的部件，按生产线范围：

|线路|堵塞|重用什么|
|---|---|---|
|8–13, 16–49|页面+SVG骨架|1920×1080机身； `<svg id="stage">` 带滤波器 `boil`、`stampInk`；图层顺序 `#cam > #world`（场景）、`#hud`、`#wipe`、`#flash`、`#fade`；然后是 `<canvas id="paper">`（乘法）和 `<canvas id="fx">`。逐字复制。|
|55–94|核心帮手|`C` 调色板、`F` 字体、`el(tag, attrs, parent)`、`txt`、`tf(e, x, y, s, rot, sy)`、`op`、`show`、`clamp`、 `seg(t,a,b)`（0..1 进度）、`lerp`、缓动 `E.out/in/io/back`、`pop(t, t0, d)`、种子 `rng(seed)`、`measure(str, size, family, weight)`。|
|97–132|每个字符的文本|`chars(parent, str, {x, y, size, family, weight, fill, anchor, ls, shadow:{fill,dx,dy}, stroke, sw})` → `{g, items}`;使用 `charsPop(c, t, t0, stagger, d, from)` 制作动画。|
|135–150|**H半色调**|`halftone(parent, {x0, y0, w, h, step, angle, color, f, maxK})` 返回一个 `<path>`；密度场 `radial(cx, cy, R, pw)`、`edge(R, pw)`；添加 `.setAttribute('class','mul')` 进行套印。|
|152–171|背景+标题栏|`bg(parent, color)`； `caption(parent, [[text, colour?], …], {x, y, size})` + `captionAnim(c, t, t0)`。|
|174–190|**邮票**|`stampEl(parent, str, {size, color, family, padX, padY, border})` + `stampAnim(s, t, t0, x, y, rot)`。与 `SHAKES` 条目和 `stamp()` SFX 配对（位于 `t0`）。|
|192–194|心|`heartPath(scale)` → 路径 d 字符串。|
|199–337|**吉祥物装备**|`catHead`（耳朵、条纹、眼睛、嘴巴、胡须）+ `setFace(cat, {open, lookX, lookY, mouthOpen, earL, earR, happy})` + `blinkAt(t, [times])`；身体`catSit`（正面），`catRun`（侧面，+ `runCycle(c, t, speed, amp)`），`catLoaf`（躺着），`catCurl`（睡觉）； `tailEl(parent, d, width)` = 带条纹破折号的轮廓笔划尾部。要制作不同的吉祥物，请保留配方（7 px 海军蓝轮廓、扁平填充、奶油色腹部、`boil` 滤镜）并重新绘制路径；保留`setFace`接口。|
|349–355|时间轴|`scene(t0, t1, build)`：`build(g, s)`创建一次场景元素并返回`update(t)`； `render()` 仅显示 `t0 ≤ t < t1` 的场景，并使用 **绝对** 时间调用 `update`。|
|358–935|10个场景|工作示例：带有下落字母的标题 (359–403)、标题 + 印章 + 爪印 (406–435)、带有高度图、盘子、闪光、心形和气泡的照片 (438–508)、半色调数字 + 杯子物理 + 星爆 (511–625)、带有月亮、星星、床、速度线的夜跑 (628–704)、笔记本电脑打字堵嘴 + 面包(707–782)、展示卡 + 摇动 (785–819)、判决光线 + 五彩纸屑 (822–849)、原因特写 + 心爆 (852–882)、文件夹 + 卷曲 + 末端气泡 + 信用线 (885–935)。|
|937–967|平视显示器|案例编号 + `chips` 表 `[t0, t1, section, title]` 中的章节芯片；自动宽度；在黑暗场景中反转（编辑 `dark` 测试）。|
|969–988|点擦拭|`WIPES = [[cutTime, colour], …]`，80 px 网格，0.44 s 窗口。|
|995–1032|纸+木纹|`buildPaper()` 一次； `drawFx(frame)` 每帧。|
|1037–1064|`render(t)`|煮沸重新播种、场景切换、`SHAKES` + 节拍脉冲（`inGroove` 窗口）、闪光次数、最终淡出窗口、HUD、擦拭、颗粒。|
|1066–1084|`init()`|字体预加载（两遍）→ `buildPaper()` → `buildAll()` → `window.READY = true`； `?t=` 查询在普通浏览器中呈现给定时间。|

与`render.mjs`的合约只有`window.READY`和`window.render(t)`；将两个文件中的 `FPS`/`DUR` 更改为不同的长度。

**最小新场景**（粘贴到`buildAll()`内部，然后将其剪切添加到`WIPES`，`chips`行，`SHAKES`作为印章，以及`music.py`中的SFX时间）：

```js
scene(8, 12, (g) => {
  bg(g, C.paper);
  halftone(g, { color: C.yellow, step: 22, angle: 15, f: radial(1500, 520, 700, 1.0), maxK: 0.68 });
  halftone(g, { color: C.pink, step: 22, angle: 70, f: radial(0, 1080, 520, 1.2), maxK: 0.6 }).setAttribute('class', 'mul');
  const h1 = chars(g, '罪状 01', { x: 120, y: 330, size: 150, family: F.serif, fill: C.navy, shadow: { fill: C.yellow, dx: 8, dy: 8 } });
  const catG = el('g', {}, g); const cat = catSit(catG);
  const st = stampEl(g, '属实', { size: 160, color: C.red });
  const cap = caption(g, [['证据确凿，'], ['当场抓获', C.yellow], ['。']]);
  return (t) => {
    charsPop(h1, t, 8.05, 0.06);
    tf(catG, 960, lerp(1200, 470, E.back(seg(t, 8.2, 8.6))), 1.1);
    setFace(cat.head, { open: blinkAt(t, [9.4, 11.2]), lookX: Math.sin(t) * 4 });
    cat.tail.setAttribute('transform', `translate(90 285) rotate(${Math.sin(t * 2.4) * 10})`);
    stampAnim(st, t, 10.0, 1450, 640, -8);
    captionAnim(cap, t, 9.0);
  };
});
```
