<a id="chinese-ink-wash--our-demo"></a>
# 中国墨水水彩晕染 — 我们的示范

众多例子中的一个。请勿重复使用其故事、弧线、镜头、道具或时间安排。

示范：*剑客与河流*（48秒）·`ink-wash.mp4`·来源于[`demo/`](demo/)


<a id="story--structure"></a>
## 故事与结构

剑客水上渡江，一剑劈出滔天巨浪。一个角色，一个目标，一个回合。笔本身就是事件：划破波浪的笔画，也是写在空中的“水”字。

弧线（48秒）：虚无→一滴墨（创作）→浩瀚空间中的一个小人物→轻盈愉悦（轻功过水）→画成压倒性的障碍物（湿漉漉的墨迹变成波浪）→沉默→果断的一笔→释放→尺度显露（人物是全画中的一个微小标记）→印章。结尾的台词是哲学性的，而不是胜利的（“用剑斩水，水只会流下去”）。

风格特有表现手法花：一笔就是一切（开头的水滴），毛笔=手势（写下的水），飞白（完全沉默后的剪切），劈开一团（波浪），手卷（最后的拉回和密封）。

<a id="shots"></a>
## 镜头

|打|摄影机|
|---|---|
|开幕|空白纸的锁定框架；水滴落入其中。|
|建立|缓慢地从右向左平移（滚动展开），结束于 **高宽** 框架：人物高 150–180 像素，河流是一个巨大的空白。|
|旅行|横向跟踪，人物位于画面的 60% 左右，前方有空间；远山视差非常慢；偶尔有黑色的芦苇从最底部经过。|
|威胁|**低角度**，地平线低，波浪高耸，角落里的身影渺小；缓慢推入并伴随着越来越大的震动。|
|沉默|硬剪到极端特写（帽檐，没有眼睛）；然后一个**过肩式**框架将图形、书写字符和波浪放在一个轴上。|
|发布|回到与建立镜头相同的高宽比例。|
|结束|从人物到整个手卷在丝质底座上的连续拉回；海豹; 片尾卡滚动下方。|

为什么这条路线，对于这个故事：锁着的白纸在“某物”之前放置了“无”；卷盘末端又高又宽，使人物显得很小。寂静中的极端特写是影片唯一的硬剪辑；发行版恢复到既定规模，因此押韵显示了发生了什么变化；拉回装好的卷轴将整个旅程变成了一幅画。其中每一个都是 STYLE.md §6 中的一个选择，而不是该风格的默认开头或结尾。

击球前的保持是缓慢的 5% 推入；然后，笔划在大约 4 帧内穿过帧，并且波仅在其之后开始分裂。

<a id="score-structure"></a>
## 配乐结构

原版古琴配乐 (`demo/music/score.py`)，F 锣五声音阶 (F G A C D)，按节提示而不是循环。空闲时间开场，风景 60 BPM，旅行 90 BPM（节拍上的脚步声），鼓声表示威胁，**数字静音**，三个笔画的三个玻璃泛音，再次静音，然后是鼓 + 七弦扫频；主题回归发布；最后一个注释=密封。

拟音具体到本次影片：拔剑（刀鞘刮+细长金属环，斩前秒沉默），斩（撕裂空气+河流咆哮+低轰）。寂静之中，只有剑声和滴水声。气氛硬生生地打破了最初的寂静。

声音：平静的英国旁白，Kokoro `bm_george`，lang `en-gb`，速度0.82–.86，4–6行。音乐在声音下降低了约 8 分贝，氛围也降低了：线路下的河流咆哮使耳语将“Halfway”听成“This way”。在最终混音上再次用Whisper 语音检查每条线路。

<a id="palette--props"></a>
## 调色板和道具

- 纸张：基础 `#F2ECDE`–`#F3EBDD` (rgb .95/.925/.87)，云斑 ±7 %，三个纤维方向（+1.8 % 光），晕影 ~.22。墨水从冷灰色`rgb(.52,.55,.58)`到暖黑色`rgb(.075,.068,.062)`。朱红`#B02E22`：封印和英雄的**剑流苏**，在宽镜头中找到他并与最终封印押韵。
- 合成器编号：湿出血是 1:1 时约 5 像素的 12 次噪声泊松模糊；边缘颜料=小模糊-大模糊。
- 所用墨色：书墨、剑墨、帽沿线、苔点；轮廓和帽子较厚；折叠和刀鞘很重；山体及袍灯水彩晕染；清晰可见远山、脸庞、薄雾。
- `ink.js` 中的行程轮廓：`brush`、`tip`、`nail`、`lens`、`fan`、`rise`、`robe`、 `even`+每点压力；加载笔画使用`darkDir`、`side`、`brWet`（它们的刷毛进入湿层）；身体填充褪色为 `(1-dry)^1.6`； `dry` .3 = 有纹理，.6+ = 飞白。
- 山脉 (`land.js`)：每像素一次并缓存，具有 3 倍频程粗糙度的尖指数峰值；远距离音调 0.12–.16 无纹理，近音 0.4–.5 有纹理；范围末端使用水平 alpha 遮罩进行淡化，而不是通过倾斜山脊（它穿过河流）来淡化。松树：一根弯曲的负载树干，几根尖枝，扇形针簇。芦苇：长笔尖+镜头叶子，仅前景。
- 水：每一步都有墨环，一笔为 1.86π，有一个开放的间隙，r ∝ 年龄^0.6，在约 2.4 秒内褪色。
- 波浪：苍白湿润的身体+ 4-5个在波峰处卷曲的巨大负载笔画+几条细波浪线+喷雾作为不规则的印迹。
- 英雄（`hero.js`）：100个单位骨骼绑定结构（臀部、胸部、头部、手臂、腿部、下摆点、喇叭形、护套、丝带）。帽子=一团湿物+两条干脊线+一条烧焦的帽檐线；长袍 = 一团苍白 + 两笔负载；腿和剑都沾满了烧焦的墨水；风中的一根丝带。脸留在帽子下面；特征仅出现一次（剑眉、凤眼睑、一条鼻线、下垂的小胡子）。
- **清宫跃**：身体前倾约30°，一膝内收，另一腿拖后，袍子向后拉成一大块苍白的大团，后缘深色，袖子飘逸。步进循环：触摸（14%）→上升→滑行（45%）→下降；高度 `sin(π·phase)`；每次触摸一个墨环。
- 所写的水：取自马山正，`solid: true`，干度0.17，出口锥度至0.12-0.18，45°隐藏尖端导入。
- 稳定行程：`gapLen`固定参考长度；以 5 次拉伸循环煮沸。
- 分裂波：上半部上升并旋转，下半部塌陷并挤压，撕裂边缘有卷曲的波峰，苍白的水彩晕染块；飞溅物借助重力沿着剑的方向飞射。
- 墨水绽放：掩模`d·(0.62 + 0.8·fbm)`； element blooms 使用 1/4-res 掩码和 `destination-in`。

<a id="end-card"></a>
## 端卡

标题：卷轴本身写有两个垂直栏（英文字母旋转 90°，Cormorant SC 600，宽跟踪）+ 印章；当锅启动时，它会在湿→干中褪色并蒸发。字幕：Cormorant Garamond 斜体 500、46 像素、1 像素跟踪，干燥时间约为 0.35 秒。

片尾卡：整个卷轴放在深色桌子上，有丝绸边框和滚筒； “CHINESE INK 水彩晕染”（Cormorant SC 600、44 px、14 px 跟踪）和下面浅纸色的出处（斜体 30 px）。 “LemoLab × Claude Opus 5.5”签名仅属于该库的示范；用户的影片没有 LemoLab 积分，也没有该卡的副本。

<a id="build-notes"></a>
## 构建笔记

```
styles/ink-wash/demo/
  ink.js     brush engine (strokes, bristles, masses, blots)   comp.js    WebGL rice-paper compositor (bleed, edge, paper, bloom)
  hero.js    xieyi figure rig + poses                           face.js    close-up face (one use)
  land.js    mountains, cun, cliffs, pine, reeds, ripples       wave.js    gestural wave
  glyph.js   "水" traced from Ma Shan Zheng + the cut stroke    seal.js    vermilion seal
  world.js   the handscroll world, reveals, shots 1–2           cross.js   crossing + rising (shots 3–4)
  climax.js  silence, writing, the cut (5–6)                    passage.js parted river, bow, scroll, end card (7–8)
  story.js   timeline (single source of truth)                  shots.js   dispatcher, transitions, subtitle spots, sound events
  subs.js    inscription subtitles   music/score.py  original guqin score   mix.py  foley + voice + music   build.sh
```

1. 首先写入 `story.js` 次（语音持续时间来自 `core/tts/tts.py`），然后用相同的数字向配乐通报（作曲家可以并行运行）。
2. `node core/render/still.mjs styles/ink-wash/demo --range a:b:1` + `core/render/sheet.py` 用于概览表； `?test=sheet|pose|shui|frame` 设计工作页面； `?nosub=1`、`?poster=1`。
3. `node core/render/events.mjs` → `mix.py` → `video.mjs --fps 24 --workers 3`（1152 帧 ≈ 60–130 秒）→ `mux.sh … 24 0`（颗粒 0：纸张位于着色器中）。
4. 或者简单地称为 `sh styles/ink-wash/demo/build.sh`。

与示范的道具相关的陷阱：
- 字幕继承了平移镜头中的世界摄影机变换并滑出屏幕。
- 用`flip=-1`绘制的悬崖将人物置于半空中；悬崖多边形的背面呈现出笔直的垂直边缘；岩石的底部被图层画布底部切割→翻转后计算屏幕范围，倾斜背面，使用 `destination-in` 渐变淡化图层底部。
- 当笔划仍在穿过框架时，切口开始分裂波浪。
- 具有罕见且重的每像素步长的场景可能会超过 Playwright 的默认屏幕截图超时；只需重试静态渲染（帧本身是确定性的）。
