<a id="copperplate-engraving--our-demo"></a>
# 铜板雕刻 — 我们的示范

众多例子中的一个。请勿重复使用其故事、弧线、镜头、道具或时间安排。

示范：*蜜蜂，第七版* (40.0 s) · `engraving.mp4` · 来源在 [`demo/`](demo/) · 所有单词均来自 [`demo/content.json`](demo/content.json)


<a id="story--structure"></a>
## 故事与结构

场景示范，不是故事：案例旁边的屏幕上有 **博物馆对象标签**。一个物体（蜜蜂）、它的名字、关于它你不知道的三件事，以及在哪里可以看到真实的物体（“在画廊 4 中看到活的蜂巢”）。

结构（40秒）：铜ECU→防拉→拉出板→三个放大的细节（眼睛、hamuli、corbicula），每个细节都飞到其插槽→沉默→手工着色→锁定最终板→组织防护片尾卡。

风格特有表现手法如何在此示范中提供信息：

- *切口本身*是钩子：第一帧是铜刻刀的中线，铜的卷曲在尖端之前升起。屏幕上没有其他内容，因此眼睛可以去一处。
- *构建*（轮廓 → 第一次孵化 → 交叉孵化 → 深色和头发）是“这是一个严肃的、制作的东西”节拍，保持在 5 秒以内并在标题下。
- *放大圆环*是信息载体：在零件周围划出一个环，内部被抛光干净并在放大倍率下重新雕刻，并且圆环飞到其槽中，拖着引导线。观看者只需一步就能看到细节“在哪里”以及它“是什么样子”。它的标签（罗马大写字母、斜体术语、脚本注释）在落地时被刻上。
- *手工着色*是高潮，在真正的沉默之后，所有信息都在盘子上，所以它读作奖励，而不是新信息。
- *最后一张图*是海报：每个标签、号召性用语和雕刻师的致谢信息都被锁定。

首次为此示范编写的用例表，以及我们为每个用例考虑的镜头结构（示例，而不是配方）：

|使用|镜头结构|
|---|---|
|博物馆物品标签（示范）|铜ECU→验证拉出→拉出到板→1-4个放大的细节，每个细节都飞到其插槽→沉默→手工着色→锁定最终板|
|“一分钟……”|同样，叙述者带着笔记；结束在盘子上作为缩略图|
|教科书图|无铜孔；从1×开始在纸上雕刻图形，然后将零件一一标记为引线；无颜色或仅在正在教授的部分上有颜色|
|工艺遗产（手表、小提琴、刀）|雕刻刀的 ECU 在物体轮廓上 → 构建 → 机构上的圆形 → 仅对重要的材料进行着色（金色、清漆）|
|地图或场地平面图|雕刻海岸线或平面图，圆环成为插图（建筑物，港口）|

<a id="shots"></a>
## 镜头

摄影机是板上的放大镜。 示范中的节拍：

|打|摄影机|为什么|
|---|---|---|
|挂机（0–2.5 秒）|4.2× 在铜上，**跟随** 刻刀尖端，3° 滚动|一个注意点；切口就是钩子|
|验证拉 (2.5–3.2)|当纸张剥落时锁定|表现媒介自己的过渡|
|构建 (3.2–6.2)|**拉出** 4× → 1×，对数缩放，具有屏幕线性移动感觉|尺度揭示：曲线是蜜蜂的腹部|
|细节 1 (9.4–15.0)|**将**推到眼睛上的4.3倍； **与圆形** 一起骑行，当它升空并飞到其插槽时，缓动飞向 1.45× 阅读框|签名一镜到底：哪里→什么→标签|
|细节 2 (15.0–19.4)|**从左上到左下以1.45×的角度向下倾斜**，将细节1的注释保留在框架中|更快，相同的语法|
|细节 3 (19.4–23.75)|**在圆形飞行时将**拉回到全盘，然后**推入**进行读取（在细节2的注释已经完成之后）|加速度；尊重阅读时间|
|聚集、沉默、色彩|全盘；着色期间 2% 的呼吸推动|颜色移动，而不是摄影机|
|最终盘|锁定|海报|

示范中的运动时序：第一行是一个笔划，然后是摄影机，长 5.4 秒，因此在第 0 帧时它已经是第三次剪切；一次进行 6-90 次划水； roundels 在飞行途中提升 30 px 并增长到半径 120；每个颜色区域的绽放时间为 1.25-1.6 秒，开始间隔 0.42 秒。

<a id="score-structure"></a>
## 配乐结构

三层：房间色调（一个安静的工作室，铜制时钟上有微弱的时钟；之后是纸质房间），以图片事件为主的拟音，以及巴洛克风格的房间配乐。

- **配乐**：大键琴+弦乐四重奏，96 BPM，D大调。 `music/score.py` 读取为 `events.json`：每个细节部分（A 长/B 倾斜/C 回拉）写入一次并放置在影片放置的位置；结尾随着细节的结束而变化，因此任何数量的细节都会得到匹配的配乐。在旁白下，旋律在声音的频带之外高出一个八度。雕刻断面为**all拨奏**（刻刀的小精切），密度逐级递增；每个圆环 = 当环被刻划时发出高的“叮”声，当它飞翔时发出一条上升的线，当它着陆时发出一个低的嘶嘶声。颜色之前：停止运行，然后**真正的沉默**（1.25秒）。颜色是琴弦第一次使用弓。最后一块板以 V-I 节奏降落。
- **沉默**：2.0–2.5 秒（刻刀抬起，在压力重击和重击之前）和 25.0–26.25 秒（在第一滴水之前）。
- **Foley 内置**：雕刻刀 = 带通嘶嘶声 (2.6–9 kHz)，带有颤动咔嗒声和微弱的板共振 (1.18/2.31/3.47 kHz)； swarf = 微小的 5-9 kHz ping；升力=金属蜱；按下 = 低滚轮隆隆声（提前 0.35 秒进行 J 切割）和重击声；剥离=密集的纸裂纹；孵化=颗粒状微划痕，其密度随着每次通过而增加；环=圆形划线器；抛光=轻柔摩擦；圆形飞行=纸嗖嗖；着陆=纸水龙头；字母 = 点状刻度线；笔记 = 笔划以约 4 Hz 的笔画；颜色 = 落下的水“噼啪”，然后用湿笔刷刷每个区域； 片尾卡 = 组织沙沙声（J 形切割）。
- **旁白**：心`bm_fable`（en-gb），速度0.92，温柔的自然主义者；音乐在他的控制下减弱了约 50%（弓弦的减弱幅度最小）。

<a id="score-form-bar-by-bar"></a>
### 配乐形式，逐条

原始，用代码编写（`music/score.py`，确定性：重建给出字节相同的 `score.wav`）；没有现有或公共领域的曲调。 D 大调，4/4 中的 96 BPM（节拍 0.625 秒，小节 2.5 秒，16 小节 = 40.0 秒）。力量：羽管键琴（连奏和独奏）和弦乐四重奏（小提琴独奏 I、合奏小提琴 II、中提琴、大提琴、低音提琴）；弦乐拨奏长达 25.0 秒，并且仅从 26.25 秒开始使用弓。使用 `.venv/bin/python styles/engraving/demo/music/score.py` 从存储库根重建（大约 5 秒；写入 `score.wav`、`stems/`、`cues.json`、`CREDITS_music.txt`）。电平 −18.0 LUFS 集成 (BS.1770)，峰值 −1.2 dBFS，48 kHz 立体声 24 位。 分轨音频 `harpsichord.wav`、`pizz.wav`、`bowed.wav`（各 40.0 秒，与混音增益相同，因此它们在限制器之前加到混音上，两次点击的峰值限制约为 1 dB）。

其形式是三重奏鸣曲的结构：雕刻的语法，然后是色彩。时间为示范的三个细节。

|酒吧/时间|和谐|会发生什么|
|---|---|---|
|1 (0–2.5)|—|雕刻刀静音拟音。 **1.875 / 2.1875** 羽管键琴拾音器 A4 → C#5，阻尼短路（低于 −28 dBFS 2.3）。|
|2 (2.5)|D、A/C#|**打印拉：** 合奏强拍重音（大键琴 D 和弦、大提琴、低音提琴和中提琴 pizz）。大提琴行走贝司和中提琴演奏八度音。|
|3 (5.0)|BM、G、A7|**5.0**小提琴 II 进入第 16 音，断和弦“交叉影线”。**6.25**羽管键琴第 32 音符琶音繁荣（G，然后 A7）上升为**7.5**。|
|4 (7.5)|德、格|质感十足。 **9.375** 它精简为大提琴皮兹 A 踏板加上高音羽管键琴第八音（占主导地位，“好奇”）。|
|5 (10.0)|一个踏板|**10.425**环“ting”：独奏小提琴皮兹 A6 与羽管键琴 A5。**11.275–12.5875**上升皮兹和羽管键琴音阶 A4 → A5（8 个音符，间隔 0.1875 秒）。**12.775** 降落在低 D（大提琴、低音提琴和羽管键琴 D）。|
|6 (12.5)|D、Bm|披萨纹理变淡了（在 13.125 重新开始）。|
|7 (15.0)|Em7、A7、D|**15.0**Em7 悲观。**15.5**婷(B6)。 **15.8–16.66**上升较快（7 个音符，1/7 分开）。**16.8** 登陆D。|
|8 (17.5)|Bm、G、A|质感更饱满。 **19.375**变薄为 A 踏板（第三个细节）。**19.875** 婷(A6)。|
|9 (20.0)|德、格|**20.0**小提琴I匹兹旋律，最优美的时刻：A5 F#5 D6 · B5 G5-A5 B5 C#6-D6 · E6 G5 F#5。**21.475**在低 G 处着陆。**22.19** 升力：小提琴 II 第 16 渐强加上大键琴卷音。|
|10 (22.5)|嗯，A7|**23.75** 羽管键琴降序第 16 乐段 A5 → A4（八度），以属音结束。最后一个音符长 90 毫秒，一切都在 25.0 处被门控为零。预期的补品永远不会到来，这是个笑话。|
|11 (25.0–26.25)|—|**总数字静音**（−inf dBFS，包括混响尾音）。|
|11b–13 (26.25)|D、Bm、G、Em7、A7 → **D**|**26.25**影片的第一个弓弦音符。大提琴、中提琴和小提琴在 D 上进入 pp，并以 27.6 膨胀至 mp。女高音线 A5 B5 · D6 C#6 → D6，低音线降三度 D-B-G-E 然后 A → D。羽管键琴稀疏而高：缓慢的分解和弦位于 27.5、28.75 和 30.0。**31.25** 完美节奏 V7 → I：低音羽管键琴 D（未滚动），上弦在其后滚动，低音提琴和弓形 D 和弦。然后补品响起。|
|14 (32.5)|D|**33.75** wink：一首柔和的小提琴独奏 pizz D6。|
|15–16 (35.0–40.0)|D|**35.625** 非常柔软的羽管键琴 D-A-D 卷轴，适用于片尾卡。淡出从 36.6 到 38.9 为零。数字静音从 39.0 到 40.0。|

**旁白窗口。** 在 6.4–9.6、9.8–14.9、15.3–19.2 和 19.7–23.3 内部，嘶嘶声短而干，使 300 Hz–3 kHz 保持瞬态而不是持续。在 26.9–30.9 期间，弓弦和弦主要位于低音（300 Hz 以下的大提琴和低音提琴）和 900 Hz 以上（A5–D6 的小提琴），第 pp 声带中只有中提琴和小提琴 II。羽管键琴仅演奏四个柔和的分解和弦。

**混响。** `S.room` 每个茎，在静音门之前应用，因此尾部不会泄漏到 25.0–26.25：羽管键琴尺寸 0.28 / 混合 0.16，pizz 0.30 / .18，弓弦 0.42 / 0.24。每个茎上都有 35 Hz 高通。

**定时检查。** `music/cues.json`中的每个重音在混响后在其自己的渲染词干上测量：在[t − 60 ms，t + 120 ms]内从局部波谷到局部波峰的第一个30％上升；低着陆测量频率低于 300 Hz，频率高于 2 kHz；容差 ±42 ms（24 fps 下的一帧）。对于弓形入口，第一个弓形样本高于-100 dBFS。

<a id="palette--props"></a>
## 调色板和道具

**纸张**：1920×1080世界单位，直纹纸`#f1e8d2`，世界空间纸张纹理（纤维，直纹线，稀疏的狐狸`#9a6a34`）。 (70, 44)–(1850, 1036) 处的板标记（压制的斜角矩形）：板色调 `#e8ddc2` 位于 55 % 内部； top/left 墙上的斜角为深色，bottom/right 为浅色（来自左上方的光线）。直纹边框：2.4 px 直纹 + 0.8 px 发际线 9 px 内部，(100, 72)–(1820, 1008)。

**墨色**：`#1c1510`。 1 倍变焦时的世界线宽度：轮廓 1.8–2.4（膨胀 ×0.45–1.35）、第一阴影线 0.18–2.0、交叉阴影线 ×0.78、第三家庭 ×0.6、头发和点画 0.6–0.9。 600 像素图形上的剖面线间距：3.1–3.7 像素（第一）、×1.1（十字）、×1.25（第三）。 0-1 音调上的孵化阈值：第一个家庭为 0.14，交叉为 0.46-0.5，第三个家庭为 0.74-0.78。

**光**：`{x: −0.55, y: −0.62, z: 0.56}`。

**刻字**：Bodoni Moda（标题 50 像素，跟踪 0.16；标签 17 像素，跟踪 0.14），拉丁斜体（20–24 像素），注释 Pinyon 脚本（29 像素）。字幕：Pinyon Script 38 px，`#2b1e14`，位于底部中心的装饰纸条（`#f4eddb`，软阴影）上，最大宽度 860，最多两行；行前 0.1 秒亮，行后 0.6 秒灭；永远不要忽视行动号召。

**圆形**：半径120，双线（2 px + 0.75 px，内4 px），每11个局部单位水平线的直纹地面；针对 500 单位半径绘制并按比例缩放的内容。插槽按顺序：左上 (300, 300)、左下 (300, 700)、右下 (1620, 700)、右上 (1620, 300)。未使用的槽显示了 **自然尺寸** 的标本（板 ≈ 20 厘米宽，因此 13 毫米蜜蜂是主图的 0.19 倍）。

**领导者**：0.95 px，从零件上的一个点到圆形边缘，围绕机翼和身体布线，间隙≥ 34 px（一个路径点），靠近根部的一个小斜体数字。

**和着色**：腹部琥珀色`#d9962a`，胸部赭色`#a8743e`，头部`#8a6242`，眼睛`#6e4a3c`，翅膀浅蓝灰色`#a9c3cf`（alpha 0.5），腿 `#7a5a3c`，花粉 `#eaa21a`（alpha 0.95）。在纸上乘法； 3.5 px 溢出、2/1.5 px 套准不准、湿边潮线、低频密度提升 (0.55)、大区域 1-2 次逆流、颗粒化。

**铜（仅开口）**：底座`#5e2a12 → #94502c → #4e220e`，抛光发丝的漩涡（覆盖），反射在板上的柔软工作室窗口（四个窗格，模糊14像素，超过90像素的房间发光），朝向框架边缘的暗室。凹槽：暗槽 `#240c05`，明亮的毛刺 `rgba(255,226,186)` 向光偏移，远处墙壁上有温暖的闪光。雕刻刀：亮面`#d9e0e6`，暗面`#262b30`，尖脊高光，黄铜套圈，带纹理的蘑菇形木柄；转动 0.22 rad (≤ 15°)；切屑不规则卷曲的细而窄的铜带（随着生长而张开，偶尔扭曲）。

**受试者**：蜜蜂（`subjects/bee.js`）具有三个放大倍数——复眼、hamuli（翼钩）、corbicula（花粉篮）——在`subjects/details.js`中；第二个内置主题，大扇贝 (`subjects/scallop.js`)，由 `content_alt.json` 使用。

<a id="end-card"></a>
## 端卡

标题是铭牌的一部分（刻在上面，而不是单独的卡片）。 片尾卡：半透明组织防护罩落在板上；其上刻有：影片标题、风格名称、`LEMO-OPUSCAR`、`LemoLab × Claude Opus 5.5`、三行署名线。 “LemoLab × Claude Opus 5.5”签名仅属于该库的示范；用户的影片没有 LemoLab 积分，也没有该卡的副本。

<a id="build-notes"></a>
## 构建笔记

```
sh styles/engraving/demo/build.sh              # voice → check → score → events → mix → cue check → srt → frames → mux → stills
```
- `demo/engine/`：`burin.js`（线条）、`plate.js`（板材、刻字、圆形）、`wash.js`（颜色）、`copper.js`（铜、刻刀、切屑）、`index.js`（公共条目+ `engraveShape`）。
- `demo/subjects/`：`bee.js`、`details.js`（眼睛、hamuli、corbicula roundel绘图）、`scallop.js`（第二个内置主题）。
- `demo/film.js`：时间线（96 BPM 网格），摄影机，渲染；读取为 `content.json`。 `demo/mix.py`：拟音 + 语音 + 闪避分轨音频。 `demo/music/score.py`：配乐，针对图片事件的音画节拍对照表编写（配乐结构下的逐条形式）。 `demo/tools/cuecheck.py`：配乐重音与图片事件（全部在 1 帧内）和静音级别。
- 使用 `core/render/video.mjs --workers 2` 渲染；帧需要 60–500 毫秒（铜色和彩色帧最慢）。

与示范的道具相关的陷阱：

- **翼静脉必须关闭其细胞。** 随机静脉笔划看起来很假；将长静脉定义为曲线并将交叉静脉捕捉到其上（`bee.js`、`FX`）。
- **绘制为完整胶囊的腿部关节看起来像珠子。** 排除前一段，因此仅显示远端帽。
- **相同的两个渲染示范文件夹碰撞**: `video.mjs`将其段写入`<demo>/out/`，所以渲染 main 和 alt影片一个接一个。
- **刻刀歪斜**：30°读作在线旁边戳； 0.22 rad 修复了它。
- **领导者** 拥抱机翼解读为穿过它，直到以 ≥ 34 px 间隙布线。
- “Apis mellifera”：Kokoro 说得可以，但耳语无法转录；该行使用 `asr` 字段。

<a id="contentjson-fields"></a>
## content.json 字段

`demo/content.json` 驱动每个单词、数字和颜色。

|场地|类型|范围|如果超出范围|
|---|---|---|---|
|`title`|细绳|≤ 22 个字符|较长的标题超出了拉丁线的宽度；在 `film.js` 中缩短或降至 44 px|
|`latin`|细绳|≤ 30 个字符|读取时间增长（chars/12 + 1 秒必须在第一次推送之前适合 9.4 秒）|
|`plate_no`、`series`|细绳|≤ 10 / ≤ 48 个字符|系列与上面的标题冲突~48个字符|
|`subject`|`"bee"` \|`"scallop"`|内置科目|未知 → `bee`；新主题是一个返回 `{ink, regions, focus}` 且第一笔画为 `ol0` 的模块（请参阅 `subjects/scallop.js`）|
|`details[]`|`{name, latin, note, focus}` 数组|1-4|>4 被忽略；较少的叶子槽→第一个空的显示自然尺寸的图形；时间线重新流动（前 9 节拍，其他各 7 节拍）|
|`details[].focus`|细绳|蜜蜂：`eye`、`hamuli`、`corbicula`（放大倍数绘制）；任何主题：其 `focus` 密钥|没有绘制放大倍数的按键可以获得图形本身的实时放大倍数|
|`details[].note`|细绳|≤ 60 个字符（2 行，29 像素）|第三行开始与下一轮相遇|
|`colors[]`|`{region, color}`|对象的区域（蜜蜂：腹部、胸部、头部、眼睛、翅膀、腿、花粉；扇贝：贝壳、带子、耳朵）|跳过未知区域；顺序=着色顺序|
|`caption`|细绳|≤ 50 个字符|必须在 4.4 秒最终板内保持可读 ≥ chars/12 + 1 秒|
|`signature.left/right`|细绳|短的|—|
|`nat_size_label`|细绳|≤ 16 个字符|—|
|`voice.voice`、`voice.speed`、`voice.lines[]`|心声，0.8–1.0，`{id, text, asr?}`|ID：`title`、`d1`…`dN`、`close`|比其截面长的线与下一条线重叠；保持 d 线 ≤ 4.5 s|
|`end.film_title`、`end.style_name`、`end.credits[]`|字符串|学分 ≤ 3 行 ≤ 35 个字符|较长的行会破坏片尾卡的读取时间|

步骤：编辑（或复制）JSON → `sh styles/engraving/demo/build.sh my_content.json`（TTS + Whisper 语音检查、事件、从事件重新放置的配乐、混音、提示检查、字幕、帧）。为了保持主影片不变，`sh styles/engraving/demo/tools/build_alt.sh my_content.json` 在 `demo/out/alt/` 中构建所有内容（示范的 `content_alt.json`，2 个细节，35.6 秒，通过提示检查）。

最小的例子：

```json
{
  "title": "The Great Scallop", "latin": "Pecten maximus", "plate_no": "Pl. XII",
  "series": "Shore Gallery · Shells of the Atlantic Coast", "subject": "scallop",
  "details": [ { "name": "Hinge", "latin": "umbo", "note": "The oldest part of the shell.", "focus": "umbo" } ],
  "colors": [ { "region": "shell", "color": "#d98a5c" }, { "region": "bands", "color": "#a8423a" } ],
  "caption": "Hold a real shell at the Discovery Table",
  "voice": { "voice": "bm_fable", "speed": 0.92, "lines": [ { "id": "title", "text": "Plate twelve. The great scallop." } ] }
}
```

交换此文件并运行 `build.sh` 检查引擎是否重新流动；用户的影片不是这样制作的。

<a id="engine-reference"></a>
## 发动机参考

```js
import { B, engraveShape, Wash, drawSheet, engraveText } from './engine/index.js';

// 1. any shape + a light direction → an engraved figure (contour lines follow the form), cut in order
const { ink, shape: spark } = engraveShape(
  'M0 -120 C12 -40 40 -12 120 0 C40 12 12 40 0 120 C-12 40 -40 12 -120 0 C-40 -12 -12 -40 0 -120 Z',  // a four-pointed spark
  { at: B.xf(860, 560, 1.9), light: [-0.6, -0.7], spacing: 4.2, style: 'contour' });               // or style: 'hatch'
engraveShape('M0 0 H150 V26 H0 Z', { at: B.xf(1140, 740, 1), ink, g: 't' });                        // its cursor tail, same ink
ink.schedule(['ol', 'tol'], 0, 1.1, { conc: 2 }); ink.schedule(['h1', 'th1'], 0.8, 2.2, { conc: 40 });
ink.schedule(['h2', 'th2'], 1.6, 2.7, { conc: 40 }); ink.schedule(['h3', 'th3'], 2.2, 3.0, { conc: 40 }); ink.build();

// 2. the "only colour": hand-colour one element and leave everything else in black ink
const w = new Wash({ scale: 1.5 });
w.add({ path: spark.path, polys: spark.polys, color: '#D97757', origin: [860, 560], t0: 3.0, dur: 1.2, alpha: 0.85 });

window.render = t => {
  drawSheet(ctx);                 // paper, plate tone, plate mark
  w.draw(ctx, t);                 // colour under the ink (omit for pure black-and-white)
  ink.draw(ctx, t);               // everything cut by time t; lines being cut grow
  engraveText(ctx, 'THE SPARK.', 960, 170, { size: 50, weight: 600, track: 0.16, p: t - 1.5 });
};
```
可运行为 `demo/example/index.html` (`node core/render/still.mjs styles/engraving/demo/example 4.5`)，输出为 `demo/stills/engine_example.jpg`。

主要功能：

|功能|它的作用|关键参数|
|---|---|---|
|`B.shape(d, xf)`|SVG 路径 → 世界环 + Path2D|`xf(x, y, scale, rot, flip)`|
|`B.Ink`|有序、宽度桶笔画存储|`group(name)`、`schedule(group, t0, t1, {conc})`、`instant(group)`、`draw(ctx, t, {color, wScale, dx, dy})` → 刀尖被切割|
|`B.hatch(ink, polys, o)`|一系列弯曲成形状的肿胀线|`angle, spacing, bend, tone(x,y), thr, wMin, wMax, swell, excl`|
|`B.engraveTone(ink, polys, o)`|雕刻师的三道工序|`angle, cross, third, t2, t3, g`|
|`B.formTone(polys, {light})`|任何形状 → 枕形照明音场（+ `.df` 距离）|`light, lz, base, radius, rim`|
|`B.contourHatch(ink, polys, o)`|遵循形状的线（等距轮廓）|`spacing, tone, thr, wMax`|
|`B.outline / B.stroke`|肿胀轮廓/开刀行程|`w, light, vary, run, pinch, swell, excl`|
|`B.stipple`、`B.fur`|按音调点；梳理的头发轻拂|`density, r, tone` / `len, dir(x,y), curl`|
|`B.sphereTone`、`B.cylTone`、`B.linTone`、`B.blobTone`|分析音域|来自 `B.LIGHT` 的光|
|`Wash`|手工着色，按区域缓存|`add({path, polys, color, alpha, origin, t0, dur, spill, offset, lift, pool})`, `draw(ctx, t)`|
|`drawSheet`、`borderInk`|纸张、板色调、斜角；墨迹般的规则边框|`plate: [x0, y0, x1, y1]`|
|`engraveText`、`writeScript`、`wrapLines`|切割罗马字；书面脚本；固定尺寸平衡包裹|`size, weight, italic, track, align, p`|
|`roundelFrame`|`p` 划出的双规圆|`x, y, r, p, w`|
|`Copper.drawCopper / copperLight / drawGrooves / drawBurin / drawSwarf`|铜特写|`zoom, lift, skew, s`|

整个事情的一个最小的可运行示例是 `demo/film.js` 和 `content_alt.json` （不同的主题，两个细节）。
