<a id="80s-cel-anime--our-demo"></a>
# 80 年代 Cel 动漫 — 我们的示范

众多例子中的一个。请勿重复使用其故事、弧线、镜头、道具或时间安排。

示范：*城市之光，1987*（59 秒）·`cel-anime-80s.mp4`·来源 [`demo/`](demo/)


<a id="story--structure"></a>
## 故事与结构

雨后，绰号“夜鸟”的快递员骑着白色摩托车穿过霓虹灯城市，在黎明火箭发射前将飞行员遗忘的磁带送到发射台。一位英雄，一个目标，一个截止日期（日出）。

弧线（59秒）：有最后期限的冷开场→英雄出发（标题命中）→欢乐的动力蒙太奇→障碍（一座吊桥升起）→一个决定性的举动（跳跃；山顶*冻结*）→释放到新的光芒（夜晚变成黎明）→片尾卡。磁带上的歌曲就是配乐本身：当磁带在船上播放时，配乐就变成了叙事。

旧指南如何表述这个故事的改编想法（仅作为一个例子，而不是规则）：将主题转变为交付，与截止日期的竞赛或发布；尽早设定目标（地平线上的火箭），在第二幕中阻止它，在最后在光线中揭示它。它还列出了其他改编：以快递员将产品推上舞台的方式发布产品；两道光穿过沉睡的城市的爱情故事；作为一名飞行员飞越被绘制为背景的时代的历史课。

所花费的原生能力：彩绘城市与平面赛璐珞（霓虹灯城市、潮湿的沥青、黎明的天空）、有限的动画（特写镜头、跳跃作为彩绘静止）、背光（标志、尾灯、仪表、标题）、速度语法（视差、速度线、冲击帧）、作为情节对象的主题曲（磁带）。

<a id="shots"></a>
## 镜头

|打|摄影机|
|---|---|
|冷开|**多平面起重机下降**在高大的彩绘板上（天空→屋顶→霓虹灯→街道），前景层速度更快；雨天无线电调度|
|重要的对象|紧紧插入拿着录像带的戴手套的手上，​​后面有柔和的散景，亮点在其塑料上滑动|
|解决|眼睛的极端特写；他们以三张 8 fps 的图画开头，内容是“复制。我会打败太阳。”|
|标题|背光标题卡，字母以 12 fps 的速度闪烁，灯条扫过，星星闪烁，在黄铜打击上|
|势头|4层视差侧向追踪+尾灯轨迹；霓虹灯峡谷的后视图（伪 3D）；带有霓虹灯带的半身像；车轮插入水坑；一条宽阔的高架公路镜头，**种植的目标**（穿过海湾的火箭）|
|障碍|以第一人称视角接近上升的吊桥；手套在极端特写中扭转油门和转速表，切割速度更快|
|顶峰|径向速度线的低前视图 → 一拍定格 + 白色闪光 → 冲击框架 → 带有缓慢平移的机载自行车的“和谐”静止画面 → 冲击框架 → 着陆时产生火花和摄影机摇晃|
|发布|和夜骑一样的侧轨构图，黎明时分在海边重绘，天空开阔|
|交出|两只手穿过栅栏传递胶带；用手指按下驾驶舱卡座上的“PLAY”|
|结束|火箭升空（倾斜、延迟）；温暖的特写镜头回答了开场白（“告诉你我会打败太阳。”），然后是片尾卡|

骑手的前视图隐藏在有色挡风玻璃后面，因此只能看到护目镜和头发，让前灯耀斑携带镜头。剪切落在条上（116 BPM，条 = 2.069 秒）。

<a id="score-structure"></a>
## 配乐结构

原创城市流行/合成放克“动漫开场”，用 numpy (`demo/music/score.py`) 合成：116 BPM、E♭ 大调、maj7/9 和弦、J-pop“皇家之路”进行 (IVM7–V7–iii7–vi7)。 FM 电钢琴（DX7 风格 1:1 载波 + 14:1 铃声瞬变）、拍击贝斯（拇指 + 八度流行音）、门控混响军鼓、合成铜管乐器、合唱 16 分音符吉他唱头、弦垫、可唱歌的主钩、FM 铃声和 **键，可改变半音**最后的合唱。

写在剪辑上：冷开场下的前奏、带有发动机转速空间的填充栏、铜管乐打击上的标题、蒙太奇下的主歌、合唱前的构建、跳跃前的 **one 真正沉默的节拍**、静止画面上的合唱、着陆上的重音以及片尾卡上的最终和弦。叙事扭曲：当磁带在驾驶舱中播放时，配乐会通过带通到盒式磁带声音中的一个小节，然后随着火箭升空而随着调性变化而打开至全音域。

拟音：来自 RPM 曲线的发动机（谐波锯堆栈 + 点火抖动 + 带通排气脉冲，空中低通）、雨床 + 随机掉落、湿滑路面上的轮胎嘶嘶声、风、桥铃声、无线电静噪咔哒声、冲击臂、金属刮擦和火花、盒式咔哒声、按钮 + 电机、火箭点火和轰鸣声。

声音：英语配音的感觉，8 句短台词：女主角（Kokoro `af_bella`）和无线电调度员（Kokoro `am_michael` 通过带通 380-2800 Hz + 饱和度 + 静噪）。 Whisper听错了“发射是在黎明”，所以变成了“发射是在黎明”。混音：声音通过 RMS 平衡，比回避音乐高约 10 dB，音乐在台词下回避约 9 dB，引擎和氛围回避 3 dB，合唱比前奏响度 4-6 dB，两次通过响度范数为 −14 LUFS。

<a id="palette--props"></a>
## 调色板和道具

- 夜晚：靛蓝/深紫罗兰/霓虹洋红/青色/暖窗金。黎明色：长春花色/玫瑰色/桃色/淡金色。英雄的口音：**珊瑚围巾**，两种语言都可读。
- 使用的颜色模型乘数：夜间照明×[.78,.74,1.0]，阴影×[.58,.52,.92]；黎明亮起×[1.04,.9,.84];用于跳跃的背光剪影套装（深紫色，橙色边缘）。皮肤线 ≈ `#5a2e2e`。
- 道具：白色摩托车、标有“SIDE A·CITY LIGHTS”的卡带、耳机和护目镜（接近黑色、较粗的线条）、紧握手套、转速表、带红色警示灯的吊桥、横跨海湾的泛光灯垫上的火箭、带背光水平仪的驾驶舱卡带甲板。招牌：BAR、CAFE、吃茶、ホテル、カラオケ。
- `head80.js`中的女主角：眼睛位于头部垂直中部，嘴巴位于鼻根和下巴之间的上三分之一处；虹膜分层上暗带→深色上半部→主色→亮下月牙，一大一小亮点；轻弹 2-3 根单独的睫毛；嘴巴闭合/定型/说话/“哦”/喘气/微笑/张开微笑，内部呈深红色，下唇有淡淡的描边；侧面有一个小后脑勺，小而微翘的鼻子，脖子前倾。眨眼将关闭的绘图保持 2-3 帧；眉毛代表决心与疲惫；气喘吁吁时肩膀抬起；眼睛里闪烁的星星凸显出音乐的口音。
- 使用的 CRT 数字：色度模糊 ~7 px，Cr 偏移 ~2 px；扫描线 3 px 周期，强度 0.18，间隙 `1 − a·ph·(1 − 0.6·L)`；格栅±0.06；荧光粉发光0.35；角 `1 − 0.28·(2u²v² + 0.25(u²+v²))`。莫尔条纹检查：在 720p 下，3 像素扫描线变成干净的 2 行交替； 900p 显示微弱的 5 行图案；低于 480p 它会消失。仅影片的伪影（门纹、灰尘、划痕、套准不准）在创作方案中进行了尝试并被删除：它们与磁带自负相矛盾。上电打开影片有咚咚+线呜呜声；跟踪噪声用短 hiss/warble. 标记磁带节拍

<a id="end-card"></a>
## 端卡

黑暗的最终黎明背景、标题、风格名称“80s Cel Anime”、“LemoLab × Claude Opus 5.5”、一行原创注释和制作人员名单。 “LemoLab × Claude Opus 5.5”签名仅属于该库的示范；用户的影片不带有 LemoLab 积分，也没有该卡的副本。

使用的标题卡：“CITY LIGHTS”，采用粗斜体镀铬，上面带有 shiti・raitsu（Dela Gothic One）、红色“1987”和间隔的标语。字幕：Barlow Semi Condensed 600、54 px、奶油黄色 `#fff0a0`、9 px 深色轮廓、底部上方 96 px；无线电线路青色 `#8ff4ff`，带有盒装“● BASE”标签；每个队列最长（持续时间 + 0.6 秒，1.9 秒）。

<a id="rights--credits"></a>
## 权利与积分

- 原始配乐、声音设计、动画和所有绘图：由此文件夹中的代码生成（numpy、Canvas 2D、WebGL）。没有样品，没有库存艺术品。
- 声音：Kokoro TTS (Apache 2.0)、声音 `af_bella`、`am_michael`。
- 字体（SIL 开放字体许可证 1.1，`demo/fonts/` 中的许可证文件）：Dela Gothic One (artakana)、Kanit (Cadson Demak)、Barlow Semi Condensed (Jeremy Tribby)。
- 受到 20 世纪 80 年代日本赛璐珞动画的启发；所有人物、车辆、地点和故事都是原创的。

<a id="build-notes"></a>
## 构建笔记

```
styles/cel-anime-80s/demo/
  cel.js     path / cel / ribbon / flutter helpers      pal.js   color models (day → night / dawn / backlit)
  rider.js   side-view bike + rider, limbs, wheels      head80.js  80s heroine head: 3 views × expressions, body/collar/scarf
  hands.js   pinch-grip gloves                          bg.js    painted plates (street, skyline, tall crane plates, reflections)
  fx.js      rain, splashes, speed lines, flares, lamps, light trails
  post.js    WebGL videotape + CRT pass (bloom, grade, chroma bleed, subtitles, scanlines, grille, glow, power-on, tracking noise)
  shots.js + scenes1–4.js   one function per shot     story.js  bar-aligned timeline, lines, credits
  hud.js     VHS-style subtitles     main.js  plates, shot dispatch, sound events
  lines.json voices   mix.py   music/score.py (original score)   tools/ (still, sheet, srt, mux)
```

1. 创作方案 → `story.js`（116 BPM 小节网格，镜头，线条）。
2. `node styles/cel-anime-80s/demo/tools/still.mjs styles/cel-anime-80s/demo --range 0.5:58.5:1 --out /tmp/cs` → `tools/sheet.py` 联系表 → 查看 → 修复。 `?test=model|close|side` 渲染角色设定表/头部特写/骑手； `?raw=1` 绕过CRT通行证； `?nosub=1` 隐藏字幕。
3. `.venv/bin/python core/tts/tts.py demo/lines.json demo/voices` → `core/tts/asr_check.py`.
4. `.venv/bin/python demo/music/score.py`（配乐 + 分轨音频 + 提示时间）。
5. `node core/render/events.mjs demo` → `.venv/bin/python demo/mix.py`.
6. `node core/render/video.mjs demo --fps 24 --workers 4 --out demo/out/video24.mp4`（在 M 系列 Mac 上，1416 帧 ≈ 36 秒）。
7. `sh demo/tools/mux.sh demo/out/video24.mp4 demo/mix.wav cel-anime-80s.mp4 24`, `python demo/tools/srt.py`.

编码数：CRF 22 处的 ffmpeg 颗粒亮度 4 + 色度 1 给出 ~32 MB/min； CRF 18 处的亮度 5 + 色度 2 为 270 MB； CRT 通过时，CRF 22 超过 35 MB/min，仅亮度噪声 2 的 CRF 23 降至约 31 MB。单通道响度落在 -13.5 LUFS； `linear=true` 的两次通过落在 -14.0。热限制器将合唱压缩到前奏的响度：标准化到 99.99%，只让罕见的峰值达到限制器。

与示范的道具相关的陷阱：
- 彩色画布上的绽放阈值将白色自行车和夹克变成了粉红色。
- S 曲线在前灯中形成了一个黑洞（首先夹住）。
- 6-8 px 的边缘偏移使细发带完全变成粉红色。
- 第一个头发版本看起来像触手；眼睛上方的刘海遮住了睫毛线。
- 第一张脸是一张纸面具：3/4身体，前脸扁平（平等的眼睛，没有颧骨转弯，V下巴，细长的脖子）。
- 夜晚的脸因夜间色调+洋红色边缘+粉色光扫而变成粉红色；前额的斑块在刘海之间显露出来。
- 在后峡谷镜头中，摄影机后面的点翻转到天空中。
- 火箭离开框架：以延迟倾斜和较慢（二次）爬升的方式跟随它。
