<a id="brick-toy--our-demo"></a>
# 积木玩具 — 我们的示范

众多例子中的一个。请勿重复使用其故事、弧线、镜头、道具或时间安排。

示范：*来自备件的火箭*（54秒）·`brick-toy.mp4`·来源在[`demo/`](demo/)·资产积分[`demo/CREDITS`](demo/CREDITS)

<a id="story--structure"></a>
## 故事与结构

一名砖块宇航员建造了一枚火箭；它崩溃了；他用掉落的部件重建了它，然后飞向“月亮”（一堆书）。失败并不是结束，它只是备件。一个角色，一个目标。

老指南告诉特工“把话题变成正在建造的东西”，并使用四种原生能力中的至少三种； 示范使用了全部四种：拼合建筑（在一块砖上打开，在一块砖上结束），无伤害地破坏（倒塌成为更好的火箭的零件），真实桌子上的玩具（茶壶是一座山，一摞书是月亮，灯是太阳），手工制作的定格动画（12 fps，甚至火焰和烟雾都是砖块）。旧指南还列出了改编示例：产品发布→产品一砖一瓦组装；一个爱情故事 → 两个角色在两本书之间架起一座桥梁；历史课 → 一个时代被建立、衰落、重建。

弧线（45-60秒，为本影片所写）：好奇→兴奋→挫折（崩溃）→安静的节拍→重建→高潮→温暖的规模揭示。幕：开场 0:00–0:06（一块红砖，第一声响），第一幕 0:06–0:18（快速搭建，骄傲），第二幕 0:18–0:30（倒塌，沉默，捡起零件），第三幕 0:30–0:50（倒计时，点火，发射，登陆月球），片尾卡之后。

<a id="shots"></a>
## 镜头

|打|摄影机|
|---|---|
|开幕|一块砖上的极端宏观，缓慢推动，背景模糊到真实的道具|
|建筑|低角度让微小的人物充满英雄气概；切掉每一根条|
|挫折|手持摇一摇就塌了，然后**低，宽，孤独**框架与字符小|
|情感节拍|正面特写，人物的手和砖块处于焦点|
|高潮|低角度向上跟随；然后是 **跟踪镜头** 与火箭并肩，前方可见月球（书籍）|
|结束|整个办公桌缓慢拉回高宽镜头：尺度显露|

其中每一个都是 STYLE.md §6 中为本故事制作的一个选择，而不是该风格的默认开头或结尾。

使用的镜头设置：特写镜头光圈 ~500–700，中景光圈 ~800，最终广角光圈 ~400。捕捉超调 0.35 螺柱 → 0 在 ~0.17 秒内。塌陷重力~420 studs/s²（真实值为1225），恢复~0.3。

<a id="score-structure"></a>
## 配乐结构

两首 Kevin MacLeod 曲目（CC BY 4.0），由 `demo/music/edit.py` 编辑至图片：用于构建的“Monkeys Spinning Monkeys”（俏皮，在小节上剪切），相同的主题在重建时悄然回归，“英雄时代”作为管弦乐的高潮。编辑使高潮命中落在点火处，最后和弦落在片尾卡上（小节对齐跳跃，连接处的色度相似）。 `story.js` 时间与音乐条对齐。

寂静：音乐在倒塌时停止，留下房间的音调和滴答作响的时钟；音乐再次拉至高潮前，倒计时下有低沉的心跳鼓声。

拟音具体到这个影片：点火轰鸣和火箭轰鸣声；带有奎因达嘟嘟声的无线电喋喋不休。

声音：温暖的英国说书人，Kokoro `bm_george`，速度~0.9，4-6句短台词；任务控制是 `am_adam` 通过无线电滤波器（带通 380–2800 Hz + 软饱和）并发出 Quindar 蜂鸣声。每一行都用耳语验证。语音压缩，音乐在语音下闪避约 40%，-14 LUFS。

<a id="palette--props"></a>
## 调色板和道具

- 经典砖调色板：红色`#c91a09`，蓝色`#0055bf`，黄色`#f2cd37`，绿色`#237841`，白色`#f2f2ee`，黑色`#1b2a34`，加上橙色，light/dark灰色，棕褐色，天蓝色。斜角半径0.06；底板哑光绿色（全透明涂层变成青色）。
- 套装：胡桃木书桌（聚港`american_walnut_veneer`）、`photo_studio_loft_hall` HDRI、茶具（茶壶山、茶杯）、铅笔、书籍（月亮）、台灯（太阳）。左上方主灯`#fff4e8`；柔光箱主键位于左前，冷框位于后面，最后一组上方有一个。 GTAO 半径 ~3.5 螺柱，比例 2.5。等级：对比度+0.26，饱和度×1.1，微凉。
- 宇航员：腿部为 1×1 柱，躯干为 2×2 砖，手臂为圆形砖，带有弯曲遮阳板的圆形 2×2 头盔。
- 火箭、火（半透明的 orange/yellow 圆板每帧都在抖动）、烟雾（向外生长和滚动的白色圆砖）、月亮（带有火山口瓷砖的灰色圆板）。
- 字幕：一个深色圆形药丸 `rgba(18,20,26,.62)` 位于底部上方 150 px 处，Fredoka 600 46 px 白色，左侧有一个黄色的 2×1 砖块小图标。无线电线路有一个红砖图标和一个“任务控制”标签。
- 标题：“备件火箭”，Fredoka 700，以 12 fps 的速度弹出，带有黄色子线“A BRICK TOY 影片”。

<a id="end-card"></a>
## 端卡

变暗的最终宽幅、标题（Fredoka 700）、砖块图标、黄色“BRICK TOY·LEMO-OPUSCAR”、“LemoLab × Claude Opus 5.5”行和资产积分。该签核仅属于该库的示范；用户的影片不带有 LemoLab 积分，也没有该卡的副本（如果您进行修改，请删除 `main.js` 中绘制的线）。

<a id="build-notes"></a>
## 构建笔记

```
styles/brick-toy/demo/
  bricks.js   geometry + plastic materials        rockets.js  props, physics, fx
  actors.js   brick-built character rig            set.js      desk, HDRI, real props, moon
  story.js    timeline aligned to music bars        main.js     acting, cameras, subtitles, events
  lines.json  voice script    mix.py  foley+voice+music    music/edit.py  score edit
```

1. `node core/render/still.mjs styles/brick-toy/demo <t…>`：回顾剧照，迭代。
2. `.venv/bin/python core/tts/tts.py lines.json voices` → `core/tts/asr_check.py` 进行验证。
3. `node core/render/events.mjs styles/brick-toy/demo` → `python music/edit.py` → `python mix.py`.
4. `node core/render/video.mjs styles/brick-toy/demo --fps 24`（M4 Pro 上 1296 帧，2× SSAA + GTAO ≈ 65 秒）。
5. `core/render/mux.sh out/video24.mp4 mix.wav brick-toy.mp4 24`.

与示范的道具相关的陷阱：
- 由球体部分制成的头盔护目镜消失在圆筒头盔内；一个弯曲的开放式圆柱面板将其固定。
- 火箭只是向上加速，变成了空白墙上的一个点；瞄准月球的追踪器镜头修复了这个问题。
- 台灯放置在后来的镜头的摄影机轴上，一直潜入背景。
- 也尝试过以 12 fps 步进摄影机，但看起来不流畅； 摄影机移至 1。
- 成堆的备件一直挡住画面边缘的镜片。
