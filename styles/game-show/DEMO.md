<a id="game-show-flat--our-demo"></a>
# 游戏展公寓 — 我们的示范

众多例子中的一个。请勿重复使用其故事、弧线、镜头、道具或时间安排。

示范: *AI进化节拍 · AI 的节奏 1997 → 2026* (148.8 s, 1920×1080, 30 fps) · `game-show.mp4` · 来源在 [`demo/`](demo/) · 引擎：带有纯 SVG DOM `render(t)`，由 Playwright + Chrome Headless Shell 截图；原始配乐从图片自己的`events.json`在numpy中合成。


**语言注释.**示范中的所有屏幕文本为**中文**（级别名称、年份横幅、标签、成绩单、信用卡）。唯一的音频单词是简短的 **英语喊声**（“将死。”、“嘿！”、“问题！”）。有**无旁白**。要制作英文版本，请参阅下面的“将文本切换为英文”。

<a id="story--structure"></a>
## 故事与结构

从1997年到2026年的人工智能历史**由节奏关卡组成的游戏节目**。这影片以标题集开头，全体演员都跟着节拍数着“一！二！三！四！”。然后是一连串**级别**。每个级别都是**一栏标题卡**（游戏 N + 名字 + 年份，在铜管叮当声中飞翔）随后是**八小节的演奏**：在上半场建立一个模式，在下半场回答或升级，最后一个节拍（第 7 小节，第 3 节拍）是**猛击+“完美！”**判断。一个**混音**接近结尾处的关卡将最近发生的所有事件都堆放在一组中，顶部有一个月的时间线，底部是每个已完成部分的缩小缩略图。结局从蛋中孵化出一个新角色，打出一个**报告卡**(《AI进化史·成绩单》) 非常棒！星，并以**信用卡**.

这是一篇关于人工智能历史的非官方粉丝文章。屏幕上列出的公司和产品（其中包括 OpenAI、Google、Anthropic、Meta、DeepSeek、xAI、Mistral、IBM、阿里巴巴的 Qwen、Moonshot 的 Kimi 和 Midjourney）并未制造或认可它。其声称的2026产品没有源文件；关于真实产品的影片需要检查和采购每一个事实。

示范如何使用风格特有表现手法：

|原生电源|示范用途|
|---|---|
|**年份水平**|象棋围棋（1997-2016）、智力问答节目（2011）、注意力工厂（2017-2020）、AI艺术工作室（2021-2024）、聊天合唱（2022-2023）、思考+价格战（2024-2025）、经纪人制作流程（2025）、然后是2026混音。|
|**呼叫和响应**|人类走法/机器走法（国际象棋），问题/蜂鸣器（测验），引导“嘿！” /人群“嘿！” （合唱），任务掉落/标记完成（特工）。在四分音符下国际象棋之后，用八分音符去石头。|
|**判断词**|“完美！”、“第37手！”、“首超！”、价格标签被锤击、“9.9✓”思想泡泡。|
|**统计为游戏 UI**|登上领奖台的美元分数、用户计数器赛车至 1,000,000、参数计数、价格标签（60 美元 → 2.19 美元）、按节拍增长的条形图。|
|**混音/缩略图**|一套，一个月丝带，每个项目在中心舞台有 2 个条，然后收缩（×0.27）到底部的一个槽中。在结局中，所有缩略图都在一个巨大的年份下弹跳在一起。|
|**Egg→成绩单→信用**|一个“下一个级别”的戏弄（下一个蛋孵化出一个“???”婴儿机器人），然后是打字机重述三行，然后是信用卡。|

**演示形状：** 演员冷开 + 预拍（4 小节）→ 7 个 9 小节级别（卡 + 8）→ 1 小节 REMIX 卡 → 16 小节混音（7 项 × 2 小节 + 2 小节结局）→ 9 小节结尾（鸡蛋 2 小节，“嗨！” 1 小节，成绩单 3 小节，信用 3 小节包括 0.8 秒褪色）。总共 93 条 = 148.8 秒。

我们如何调整主题：我们列出了各个阶段，给每个阶段*一个可以在节拍上重复的动词*（放置、嗡嗡声、泵、拍打、唱歌、锤子、印章）、年份范围和设定颜色，并选择一个“完美！”每个级别的时刻。这个话题有很多人（很多公司和产品），所以他们成为了豆子参赛者，每节都会掉落一个名字标签。

<a id="shots"></a>
## 镜头

摄影机不会在示范中的任何地方移动：整个正面、对称的舞台。节奏 `BPM = 150`、`B = 0.4 s`、`BARL = 1.6 s`。

|部分|酒吧|摄影机/切|笔记|
|---|---|---|---|
|冷开+标题|0–3|锁定宽度，每次计数时出拳|“AI进化节拍”200 px，白色，墨迹笔画 26 px，字形弹出间隔 0.06 秒；副标题“RHYTHM OF AI·1997 → 2026”，弗雷多卡；演员每半拍落在其后面一个，每个都有一个音调点|
|1-7 级|4–66|硬切+每个卡条上0.08秒白闪；出拳 0.008（滴答声）、0.02（击打）、0.03–0.05（猛击）|卡条，然后打8条，猛击+“完美！”第 7 小节拍 3|
|REMIX 卡 + 混音|67–83|锁定宽，缩略图收缩到底部插槽中|月份丝带横跨顶部|
|结束|84–92|条形线上的硬切割；唯一的褪色：最后 0.8 秒变为海军蓝|鸡蛋→“嗨！” → 成绩单（打字机，每 1/8 跳动一个字符，每敲击 2 个字符） → 信用卡|

<a id="score-structure"></a>
## 配乐结构

- **Score (`music.py` + `synth_lib.py`)**：150 BPM，四和弦循环 F–G–Em–Am（J-pop“王道”，每小节一个和弦，`CH`），两个 8 音符旋律`MA` / `MB`。乐器：tanh 形正弦底鼓、带通噪声军鼓和拍手、镲帽、拍击贝斯（`slap`、模式 funk/drive/pump/soft）、失谐锯 **带闭音滤波器的铜管乐器**、带颤音的方弦、弹拨（马林巴）、铃（音乐盒）、三角垫、方形琶音、牛铃。
- 每个栏都有一个 `PLAN` 模式（`main`、`count`、`funk`、`quiz`、`electro`、`dream`、`film`、 `pop`、`popBig`、`think`、`heavy`、`agent`、`agentFast`、`fill`、`future`、`futureBig`、 `egg`、`calm`、`fanfare`、`end`），每级一种口味。关卡获得 **叮当**（撞击 + 踢 + 上升铜管琶音 + 小军鼓滚入关卡）。 2026 年混音版移调了 2 个半音。
- **事件驱动的SFX**：`node render.mjs events`将图片中的每个`ev()`导出到`events.json`（示范中的474个事件）。 `music.py` 将每个事件名称映射到声音：`tock`/`bleep`（国际象棋）、`stone`（围棋）、`ding`/`boop`/`buzz`（测验）、 `land`（扑通 + 轰鸣）、`pip`（高音爆音，使用 `f`）、`slam`/`bigslam`、`stamp`、`type`、 `crack`/`hatch`、`servo`、`liftoff`、`swish`、`clap`、`drop`、`blip`、`kickhit`、 `splat`、`denoise`、`cheer`。未知的名字会被默默地忽略。
- **喊叫声**：`v:<name>` 事件播放 `voices/<name>.wav`。声音为 macOS `say` 系统声音（Samantha、Fred、Zarvox、Junior、Kathy、Ralph、Superstar），速率为 170–220，音调上升 ×1.0–1.35，而不改变长度（`asetrate` + `atempo`，请参阅 `make_voices.sh`）。 Zarvox（机器人）说机器线（“将死。”，“移动三十七。”，“注意！”）； Samantha/Fred 是主机。众人“嘿嘿！”六个不同的声音以 5–6 ms 的间隔堆叠并平移 −0.6…+0.6 (`v:crowd`、`v:heyAll`、`v:heyBig`)； `v:heyVar` 为每位参赛者选择一种声音。喊叫声放置在节拍*之前* 20–30 毫秒。
- **混音**：声音+SFX走自己的总线；音乐从该总线的 12 Hz 包络中降低了高达 40%；最后 0.8 秒消失；峰值归一化为 1.5，然后 `tanh` 软剪辑 ×0.9 → `music.wav` (44.1 kHz)。然后，`finish.sh` 对 **−14 LUFS / TP −1.2** 应用两遍响度范数，并重新采样至 48 kHz AAC 256k。

<a id="palette--props"></a>
## 调色板和道具

**画布和线条：** 1920×1080 SVG。轮廓 `K.ol = #1B1B1B`，宽度 `OW = 8` px（`SO` 展开：描边，8 px，圆形连接和帽）；小部件上 5–7 px。硬偏移阴影 +10 px（横幅）或 +14 px（关卡）。

**调色板（`main_v1.js`/`main.js`中的`K`）：**
|角色|颜色|
|---|---|
|墨水/纸张|`ol #1B1B1B`、`white #FFFFFF`、`cream #FFF6E5`（卡片、成绩单）|
|糖果初选|`yellow #FFD23F`、`orange #FF8C42`、`red #FF5A5F`、`pink #FF8FB1`、`green #5BD68A`、`lime #C6F16D`、`sky #8ED1FC`、`blue #4D7CFE`|
|深组|`purple #6B4FBB` / `purpleD #46318F`、`teal #3FB8AF` / `tealD #2B8F88`、`navy #26264A` （结束）|
|道具|`wood #C98A52` / `woodD #8E5530`、`gray #C3CAD9`、`chalk #2F5D50`、`skin #FFD1A8`|
|人物色调|`gpt #19B388`、`claude #D97757`、`gem1 #4E7CF6` / `gem2 #9B6CF0`、`llama #F4E9D8`、`whale #4D6BFE`、`dblue #2B59C3`|

套装使用 `stripes()`（对角带，通常缓慢滚动）、`dots()`（18-25% 白色的偏移圆点）或 `raysEl()`（旋转旭日形）。 y = 860–900 处的地板带，顶部有 8 像素墨线。

**类型：**中文 =**Noto Sans SC 900**(`F.sans`) 随处可见；拉丁文显示 =**Fredoka 700**（`F.round`：游戏 N、年份、“完美！”、姓名标签、数字）； **ZCOOL KuaiLe** (`F.cute`) 仅限手写道具。大字使用`gtext()`；标题文本使用 `chars()`。

**角色（`main_b.js`中的`bean()`）：**，圆豆身体（160像素宽，172像素高，比例1），两只粗短的手臂，戴着白色手套的手，两只脚呈椭圆形，椭圆形的眼睛带有白色的反光，粉红色的腮红，小弯嘴变成张开的红嘴。身份=身体颜色+腹部补丁+**one**头部标记（天线球，心，“？”，月亮，螺栓，云，芽，刷子，贝雷帽，船长帽，骆驼毛，鲸鱼嘴）+脚下的墨水名牌药丸。双子座是两颗半号豆（`twins()`）。人类（`human()`）有一件衬衫、一个圆头、一个发帽、可选的眼镜和一个汗滴。 1990 年代至 2010 年代的机器是方形机器人（`robotDB`、`robotAG`、`robotT`、`robotW`）。

**重复用户界面：**
- **关卡**（`card()`）：全出血设置颜色+滚动条纹，奶油色面板（1240×460，r 50，10像素轮廓，14像素阴影），药丸标签“GAME N”，自动调整为720像素的关卡名称，设置颜色中的年份，一个图标在左侧跳跃。
- **年份横幅** (`banner()`)：左上角贴纸：弗雷多卡年份+姓名+单行副标题，从左侧滑入并向上弹出。
- **判断** (`judge()`)：120 px Fredoka 字，pink/yellow 具有 18 px 墨迹笔划，弹出角度为 -6°。
- **爆裂**（`burst()`）：8点星+扩展白环+8条墨速线，0.3秒。

运动编号：`hopY(t, h)` h 8–30 px； `hitSq` 30 rad/s 0.35 秒；悲观南瓜 `1 - 0.1*exp(-frac(t)*16)`； `dropY` 下降 500–900 像素； `heyAt` 0.24 秒。

**字幕和标题。** 无内置字幕：屏幕上的文字就是字幕本身（横幅字幕上 ≤ 20 个 CJK 字符，盘子上 ≤ 12 个）。 `game-show.srt`（由 `make_srt.py` 从 `events.json` + `voices/lines*.txt` 生成）仅列出英语喊叫，每次喊叫一个提示，重复人群“嘿！”合并。

<a id="end-card"></a>
## 端卡

示范的最后一张卡带有**“LemoLab × Claude Opus 5.5”**（×是U+00D7）。这是信用卡的第一行，在第 90 条（144.0 秒）处弹出：一张奶油色 1440×360 卡（r 40，8 px 墨水轮廓，−1.5° 倾斜，后缓弹出超过 0.3 秒），具有三条居中线：`LemoLab × Claude Opus 5.5` in Fredoka 700 66 px 墨水（y −80）， `本片由 Claude Opus 5.5 全程代码生成` 采用 Noto Sans SC 900 60 像素（y 30），`下一关：正在训练中……` 50 像素采用 `K.claude`（y 118）。它可容纳 4 秒，并随着影片褪色为海军蓝。代码：`main_b.js`结尾场景中的`credit`块。此签核仅属于本库的示范；用户的影片不带有 LemoLab 积分，也没有该卡的副本（重复使用代码时请取出 `credit` 块）。

<a id="rights--facts"></a>
## 权利与事实

- **这些喊叫超出了CC BY 4.0许可证。**它们是macOS系统声音（`say`），Apple根据macOS许可证授权其用于个人、非商业用途，因此`game-show.mp4`和`demo/voices/*.wav`的语音轨道不被覆盖通过风格库的示范影片的 CC BY 4.0 许可证。我们计划用 Kokoro (`core/tts/`) 重新配音。在您自己的影片中，使用Kokoro或您有权使用的声音； `make_voices.sh` 只是绘制时序草图的快速方法。
- **真实品牌：** 参赛者代表真正的人工智能产品（GPT、Claude、Gemini、DeepSeek、Kimi、Grok、Midjourney...）：名称仅出现在名牌上、原创吉祥物、宽松的彩色点头；绝不是官方徽标、文字标记或产品用户界面。真实的人（卡斯帕罗夫、李世石、KEN / BRAD 领奖台）仅以普通卡通替身形式出现在事实横幅中。
- **事实日期很快。** 2026 年混音版（默认为 Sonnet 5、WAIC 2026、DeepSeek V4-Pro、“GPT-6 Astra”、代币数量数字）在制作时被写为当前新闻。在重复使用任何图形和名称之前，请重新检查它们。
- 屏幕上的 G7 任务说明字面意思是“做一个节奏天国风格的视频”（命名一个真正的游戏系列）。在新的影片中描述类型，而不是命名它。

<a id="switching-the-text-to-english"></a>
## 将文本切换为英文

`main_b.js` 中的所有字符串都是文字（`main_v1.js` 中的三个字符串）：
1. 等级卡：`card(SECT.gN, 'GAME N', '<name>', '<years>', …)`；名称自动缩小到 720 像素。
2. 年份横幅：`banner(g, '<year>', '<name>', '<subtitle>', col)`；宽度自动测量。
3. 混音：`item(i, m0, m1, '<label>', …)`、`plate(p, '<text>')`、月份丝带 `` `${m}月` `` 和结局标签 `'2026 · 未完待续'`、`'还没唱完 →'`。
4. 道具：测验 `QA` 对、Watson 标志、“9.11 和 9.9”黑板、任务注释、用户计数器标签 `'用户'`、成绩单标题 + `lines`、信用文本、标题 `chars()` 字符串。在`main_v1.js`中：机器人箱子标签`'注意力'`（`robotT`）和G3中的句子标记。
5. 首选 `F.round` (Fredoka) 作为拉丁语标题，并保留 `F.sans` 作为正文； `init()` 从页面自己的文本中预加载字体，因此不需要更改字体列表。英语比中文宽约 1.6 倍：检查横幅和带有剧照的盘子。
6. 如果喊话改变，重新运行`make_srt.py`；喊声已经是英语了。

<a id="build-notes"></a>
## 构建笔记

```
styles/game-show/demo/
  main_v1.js     base source: palette K, tempo (at/ev/punch), hop/squash helpers, stripes/dots/rays, burst, judge, banner, 1990s robots, chess board
  main_b.js      main source: bean characters + CAST, human, podium, stage (scene/card), props, ALL scenes (buildAll), render(t), init()
  assemble.py    main_v1.js[0:109] (BPM→150, END_BAR→93) + main_v1 robotDB…stage + main_b.js  →  main.js
  frame_head.html  HTML/SVG frame + base helpers (el, txt, tf, op, E, chars, charsPop, measure, bg …)
  build.py       frame_head.html + main.js  →  index.html
  render.mjs     events | stills | video (Playwright + Chrome Headless Shell, PNG → ffmpeg x264 crf 12 per worker)
  music.py       score + events.json → SFX + shouts → ducked mix → music.wav      synth_lib.py  instruments & SFX
  voices/        40 shout wavs + lines*.txt (name|voice|rate|pitch|text)          make_voices.sh  regenerate them (macOS)
  finish.sh      concat segments + loudnorm −14 LUFS + mux → ../game-show.mp4       make_srt.py  → ../game-show.srt
  fonts/ fonts.css   Noto Sans SC, Fredoka, ZCOOL KuaiLe (woff2 subsets)
  main.js        generated (do not edit by hand)
```

来自 `styles/game-show/demo/` 的所有命令（脚本本身也有 `chdir`）。 `PY=../../../.venv/bin/python`。

1. **在网格上规划。** 在`main_b.js`中填充`SECT`（每个级别卡的第一个栏），通过`assemble.py`中的替换设置`END_BAR`，将卡栏添加到`CUTS`，并编写提示列表：哪个节拍获得哪个 `ev()`。
2. **喊叫声：** 将行添加到 `voices/lines3.txt`，然后 `sh make_voices.sh out/voices_new`（macOS `say` + ffmpeg），监听，将守护者复制到 `voices/`，将名称添加到 `VO` `music.py`。
3. **构建页面：** `$PY assemble.py && $PY build.py`。
4. **看一下：** `STILLS_DIR=out/check node render.mjs stills 5.5 20.4 45 78.3 116.5 145`（六帧约1秒）。或者在浏览器中打开`index.html?t=78.3`。
5. **事件：** `node render.mjs events` → `events.json`（示范：474 个事件，`dur 148.80`）。
6. **分数 + 混合：** `$PY music.py` → `music.wav`（≈2 s；确定性，种子 7）。 `$PY music.py out/test.wav` 在别处写道。
7. **渲染：** `node render.mjs video 2` → `out/seg_0..1.mp4` + `out/list.txt`。 示范使用了6名工人（总共120人）；在共享计算机上保持 2（约 3–4 分钟）。 `SEGS=5 node render.mjs video 6` 仅重新渲染 6 个相等段之一。
8. **完成：**`sh finish.sh out/test.mp4`（concat→loudnorm→x264 Slow crf 16 + AAC 256k 48 kHz）。如果没有参数，它会写入 `../game-show.mp4`，而**会覆盖库影片**（首先将其备份）。 `AUDIO_FROM=old.mp4 sh finish.sh …` 跳过混音并原封不动地复制旧影片的音轨（用于签核重新渲染）。
9. **字幕：** `$PY make_srt.py` → `../game-show.srt`。
10. **评论：** `ffmpeg -i out/test.mp4 -vf fps=1/4,scale=384:-1,tile=6x7 -frames:v 1 out/sheet.jpg` 加上每个大满贯的剧照。

<a id="pitfalls-we-hit"></a>
### 我们遇到的陷阱

- **`render(t)` 必须是 `t`.** 的纯函数。混音缩略图仅在 `t < t1 + 0.01` 时更新，因此它们的最终姿势取决于之前渲染的帧。 6 个工作人员渲染在 124.0 秒处冷启动工作人员 5，在发布的 v3 影片中，底部缩略图（机器人手臂堆栈、跳舞机器人、条形图、Gemini 卡）显示其从 124.0 秒到 131.2 秒的“初始”状态。导入期间在 `main_b.js` 中修复（缩略图在每帧 `t1 − 0.001` 处重新计算），并且通过修复重新渲染影片的最后一段（124.0–148.8 秒）。
- 生成 **`main.js` 和 `index.html`。** 编辑 `main_v1.js`（调色板、节拍助手、banner/judge/burst、1990 年代机器人）或 `main_b.js`（角色 v2、舞台、所有场景，render/init），然后运行 `assemble.py` → `build.py`。直接对 `main.js` 进行的编辑将被覆盖。
- **`BPM`和`END_BAR`通过`assemble.py`中的字符串replace**进行修补（`'const BPM = 140,'`→150，`'const END_BAR = 61;'`→93）。如果您在 `main_v1.js` 中编辑这些行，则替换会静默停止匹配。改为更改替换目标。
- **在三个地方添加每个新的喊叫**：`voices/`中的`.wav`，`voices/lines*.txt`中的一行（因此可以重新生成），以及`music.py`顶部的`VO`列表（否则） `KeyError`）。
- **等级卡条还必须列在`CUTS`中的**（`main_b.js`中的`init()`：闪存）和`jingle()`循环+`PLAN`跨度中`music.py`。它们是三个单独的列表。
- `synth_lib.py` 分配固定的 `DUR = 150.0` 缓冲区。较长的影片需要更大的 `DUR`，否则尾部会被切断。
- 字体：`measure()` 使用画布，因此在加载网络字体之前，字形宽度是错误的。 `init()` 在 `buildAll()` 之前加载页面文本的每个系列，并再次加载构建的舞台文本。添加文本时保留这一点。
- `say` 发音：写“A. I.”、“G P T one”、“九点十一点”、“移动三十七”——拼写形式。
- 框架模板（`frame_head.html`，从早期的影片继承）仍然声明 `#paper`/`#fx` 画布和 ink/boil 滤镜； `init()` 隐藏画布，并且风格不使用滤镜。不要理会它们，或者将它们一起删除。
- zsh 不进行分词 `$TS`；将时间戳作为数组 (`TS=(1 2 3); … $TS`) 或字面意思传递。

<a id="engine-reference"></a>
## 发动机参考

**合同。** `buildAll()` 每组调用一次 `scene(t0, t1, build)`。 `build(g, s)` 创建一次 `g` 组内的所有 SVG 节点并返回 `update(t)`，仅设置属性。 `render(t)` 使用 `t0 ≤ t < t1` 显示场景，调用其 `update(t)`，然后应用摄影机打孔、剪切闪光和最终淡入淡出。 `update(t)` 必须仅依赖于 `t`。

|模块|功能|它的作用/关键参数|
|---|---|---|
|框架头|`el(tag, attrs, parent)`、`txt(parent, str, attrs)`|创建 SVG 节点|
| |`tf(e, x, y, s=1, r=0, sy)` · `op(e, o)` · `show(e, bool)`|变换/不透明度/显示|
| |`seg(t, a, b)` · `lerp` · `clamp` · `E.out/in/io/back/elastic` · `rng(seed)`|计时 + 缓动，种子随机|
| |`chars(parent, str, {x, y, size, family, weight, fill, anchor, ls, stroke, sw})` + `charsPop(c, t, t0, stagger, d, from)`|每个字形的弹出标题|
| |`measure(str, size, family, weight)` · `bg(parent, color)`|文本宽度，全框矩形|
|主_v1|`at(bar, beat)` · `B` · `BARL` · `frac(t)`|节奏网格 (150 BPM)|
| |`ev(t, name, {f, i})` · `punch(t, amount)`|注册声音事件/摄影机打孔|
| |`hopY(t, h)` · `hitSq(t, t0, amt)` · `near(t, t0)`|节拍跳跃、击球|
| |`gtext(parent, s, x, y, size, {family, weight, fill, stroke, sw, anchor})`|概述的字幕文本|
| |`stripes(p, col, w, angle)` · `dots(p, col, step, r)` · `raysEl(p, n, col)` · `starPath(n, r1, r2)`|设置图案（在`update`中旋转光线）|
| |`burst(p, x, y, t0, col, size)` · `judge(p, word, x, y, t0, col, dur)`|返回`f(t)`；推入`s.fx`并调用每一帧|
| |`banner(p, year, name, sub, col)` + `bannerAnim(b, t, t0, t1, x=56, y=44)`|年贴纸|
| |`robotDB/robotAG/robotT(p)` · `quad(u, v)` · `pawn(p, col, king)`|时代机器人，透视板|
|主_b|`bean(p, {color, belly, antenna, name, kind, eyeFill, acc, ant, tagCol})`|参赛者； `kind` bot/llama/whale; `acc` noise/mask/beret/captain/mustache; `ant` q/bolt/moon/heart/cloud/sprout/brush|
| |`pose(c, {hey 0..1, open, sq, lean, face 'x'/'up', blink, armsL, armsR})` · `poseAny(c, o)`|摆出任何豆子或双胞胎的姿势|
| |`CAST.<key>(p, name?)` · `ALL`|16 名准备好的参赛者（gpt、claude、gemini、llama、deepseek、ernie、qwen、mistral、kimi、grok、bert、dalle、mj、sd、sora、baby）|
| |`human(p, shirt, glasses, hair)` + `humanFace(h, open, sweat)` + `setArm(arm, x1, y1, x2, y2)`|卡通人物|
| |`podium(p, col, label)` · `taskIcon(p, kind)` · `smallBot(p, col)`|道具|
| |`dropY(t, t0, y, h, d)` · `heyAt(times, t, w)` · `nearestIn(times, t)`|一进门，“喂！”视窗|
| |`scene(t0, t1, build)` · `card(bar0, num, name, years, col, col2, icon)`|一套，一张 1 格等级卡|
|music.py|`PLAN[bar] = mode`、`span(a, b, mode)`、`jingle(at(bar))`|逐条排列|
| |事件循环 `if s == '<name>': addv(sound, t, gain, pan)`|将图片事件映射到声音|

**最小新关卡**（在`main_b.js`中的`buildAll()`内；将`g8: 67`添加到`SECT`并移动后面的部分，将第67小节添加到`CUTS`， `jingle(at(67))` + `music.py` 中的 `span(68, 75, 'funk')`，并提高 `END_BAR`）：

```js
{ const b0 = SECT.g8 + 1, T = (bar, bt = 0) => at(b0 + bar, bt);
  card(SECT.g8, 'GAME 8', '开源接力', '2026', K.orange, '#FF9E5E',
       (p) => { const w = el('g', { transform: 'scale(2)' }, p); pawn(w, K.white); });
  scene(T(0), T(8), (g, s) => {
    bg(g, '#FFB870'); stripes(g, '#FFA85A', 50, -20);
    el('rect', { x: 0, y: 880, width: 1920, height: 200, fill: '#E08A4A' }, g);
    const w = el('g', {}, g); const c = CAST.claude(w);
    const calls = [T(0, 0), T(0, 1), T(1, 0), T(1, 1)], answers = [T(0, 2), T(0, 3), T(1, 2), T(1, 3)];
    calls.forEach(t0 => { ev(t0, 'v:hey'); punch(t0, 0.015); });
    answers.forEach(t0 => { ev(t0, 'pop', { f: 900 }); s.fx.push(burst(g, 960, 420, t0, K.yellow, 0.8)); });
    const b1 = banner(g, '2026', '开源接力', '一拍一棒，接住就赢', K.orange);
    s.fx.push(judge(g, 'Perfect!', 960, 300, T(7, 3), K.pink, 0.8));
    ev(T(7, 3), 'slam'); punch(T(7, 3), 0.05);
    return (t) => {
      tf(w, 960, 880 + hopY(t, 20), 1);
      poseAny(c, { hey: heyAt(answers, t) ? 1 : 0, open: heyAt(calls, t), sq: hitSq(t, nearestIn(answers, t) ?? -9) });
      bannerAnim(b1, t, T(0), T(8));
      s.fx.forEach(f => f(t));
    };
  });
}
```

然后是`assemble.py → build.py → stills → events → music.py → video → finish.sh`。
