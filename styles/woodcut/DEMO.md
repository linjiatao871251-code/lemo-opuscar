<a id="woodcut-print--our-demo"></a>
# 木刻印刷 — 我们的示范

众多例子中的一个。请勿重复使用其故事、弧线、镜头、道具或时间安排。

示范：*贝尔创始人* (58.5 s) · `woodcut.mp4` · 来源在 [`demo/`](demo/)


简而言之，示范的用途是：木刻印刷风格的 40-60 秒影片。

<a id="story--structure"></a>
## 故事与结构

一座钟楼空荡荡的村庄；创始人敲响了第一口钟，失败了，牺牲了自己的一些东西，然后成功了。这个故事中如何使用原生能力：

|原生电源|故事运用|
|---|---|
|**光雕**|关于火、黎明、发现、一盏灯被点亮的故事：光的瞬间实际上可以是“放射状切割的爆发”。|
|**雕刻=时间**|屏幕上的画面一点一点地生长是耐心的工作。它适合手艺、劳动、毅力和第一次。|
|**镜像块→真实打印**|揭示或改变心意：观众读一个倒着的单词，拉动纸张，读起来是真实的。|
|**雪=刺伤**|白点是木头上的伤口。它们可以冻结在半空中，或者被“重新吸回”，直到天空变得干净。这就是表现媒介没有的结局。|
|**单色盘**|把它留给重要的事情（熔融金属、一颗心、一团火焰）。让它在高潮时蔓延，然后收缩到一个亮点。|
|**无字小说排序**|最多四五句口语。盘子承载着故事；失败后的差距可以完全无声。|

**影片的故事形状：**在黑暗中的第一刀（地平线）→雕刻的世界→拉出的第一张印刷品（镜子→真实）→手的长特写→小祭品的快速蒙太奇→**失败的第一次尝试特写**→一块无声的盘子→个人的牺牲→第二次尝试，彩色盘子淹没画面→最长的沉默→回报的声音→颜色退到一个亮点→白色标记被重新涂上→最后一个切口再次是地平线。

我们如何调整主题：找到应该*发光*的一件事（彩色板：熔化的铜），*手工制作*的一件事（长特写：创始人的手），以及最后应该*消失*的一件事（刺切纹理：雪）。这是对这个故事的一次解读；其他主题找到其他答案或没有答案。

<a id="shots"></a>
## 镜头

“这把刀是摄影机”：刀尖，或者后来最亮的切口，始终是焦点。

|打|摄影机|
|---|---|
|挂机（0–3 秒）|黑色块的极端特写；用刀跟踪它切割一条白线（地平线）。|
|世界|向后拉3.5×→1×，山峦、屋顶、空塔被雕刻：一条线变成一个世界。|
|第一次打印|对油墨/纸张/裸露/剥离进行锁定；然后向下倾斜并推入空钟楼。|
|气息|创始人手上的4s近静态宏（慢推1.0→1.13）。|
|剪辑|每个节拍都有硬切，加速（1 / 1 / 1 / .5 / .5 / .25 / .25 秒），每次落地都会有震动。|
|第一种颜色|当铜变成橙色时，推入坩埚，第一种颜色会出现在特写镜头中。|
|失败|将变焦（0.2 秒）捕捉到钟壁并在裂缝爬升时保持 1.3 秒。|
|沉默|框架中的框架：车间门口，外面的村民，创始人的背影，锤子缓缓落下。除了雪，什么都没有动。|
|高潮|仅从流开始（z 2.4），径向切口从模具中爆出，然后向上并伸出以显示两个面都被照亮。|
|签名|钟声响起时，8×→1×从钟壁到整个山谷的连续拉回：声音传到摄影机最远的地方。|

为什么选择这条路线，对于这个故事：用刀划出的地平线既是第一次也是最后一次切割，所以影片闭合了一个圆；敲响的铃声和拉回的距离必须相同。其中每一个都是 STYLE.md §6 中的一个选择，而不是该风格的默认开头或结尾。

示范动作时序：锤子后仰4帧→击打2帧→落定+摄影机摇动3帧；风箱用全身推动；投掷是离合→松开→手握在空中。印象震动：[5,−3] 然后 [−2,1] px。

<a id="score-structure"></a>
## 配乐结构

- **Grid 首先**：60 BPM，通过 3:2 公制调制（60 的三连音八分之一 = 90 的八分之一）切换到 90 BPM 进行锻造。 `timeline.json` 是单一事实来源。 `tools/cuecheck.py` 根据图片事件和两种静音检查配乐提示（示范：25 个提示，最大偏移 0 毫秒）。
- **配乐**：仅低音弦（低音大提琴、大提琴、留笛、皮兹；仅在钟声后演奏中提琴）+ 木材和皮肤（原木鼓、木版、框鼓）+ Gran cassa / 定音鼓 + 1 个 tam-tam + 1 个 **合成anvil**（模态 numpy：3-5 个不和谐分音 + 锤瞬态）。 **铃声响起之前任何地方都没有铃声**：村庄“没有声音”，所以第一声钟声就是高潮。 D小调，在钟声的衰变中转向D大调。
- **本片的Foley**，全部综合：刀入木头、碎片、布雷尔钉、纸空气、裸锉刀、湿剥离；黄铜按尺寸分类（锅=低、宽；钥匙和环=高、纯净）；粘土刮擦和粉碎；风箱皮革+空气；熔化的气泡，轰鸣，嘶嘶地倒入模具中；铃声作为模态模型（嗡嗡声 0.5、素数 1、三阶 1.2、五阶 1.5、标称 2、2.5、3、4，具有自己的衰减和跳动）+ 两个山谷回声。
- **两个真正的静音**：29.7–32.3 s（仅−40 dB远风；之后的第一个声音是罗盘盖的*咔哒*）和44.3–47.3 s（**数字静音**，测量为−91 dB；第一个声音响铃后的声音，最响的时刻是影片）。
- **J/L 斩**：火爆裂声进入手镜头之前；室外风传入车间闷闷不乐；风把果皮引入钟楼；钟尾位于片尾卡下方。
- **混音**：音乐在人声下减弱约 8 dB（铃声后 6 dB），在拟音琴键下减弱 4 dB。 **Foley 也回避了**（在与金属打击乐共享节拍的线路下−5 dB、−9 dB）。旁白：Kokoro `am_onyx`，0.88，4 行。

<a id="palette--props"></a>
## 调色板和道具

- **调色板**：油墨`#111111`·纸张`#EFE8D8`·木块本身`#D8C29C`（仅在显示块的镜头中）·一张色板“铜”`#C8502A`。
- **打印框**：1920×1080，打印图像区域`36, 36, 1848×912`。底部纸张边距（132 像素）包含标题。修复了 3 px 色板重合失调问题。
- **道具和演员**：创始人和他的徒弟（零件骨骼绑定结构、姿势、表情）、山谷（山、村庄、空塔、雪）、作坊、坩埚、倾倒、火花和模具、钟、风箱、村民的黄铜礼物、指南针、音响。 示范的指针、指南针和滤镜仍然采用高度场雕刻+`woodcutFilter`制成。
- 说明文字：IM Fell 英语 42 像素，墨迹 `#111`。

<a id="end-card"></a>
## 端卡

标题被“镜像”到区块中（IM Fell English SC），只有在拉出第一个印刷品后才可读。 片尾卡：新鲜的印刷品：用黑色面板雕刻出的标题，一个小铃铛保留了影片最后的铜色亮点，然后是*木刻版画*、Lemo-Opuscar、LemoLab × Claude Opus 5.5 和凸版印刷的制作人员名单。标题下的最后一刀与影片的第一个声音相呼应。 “LemoLab × Claude Opus 5.5”签名仅属于该库的示范；用户的影片不带有 LemoLab 积分，也没有该卡的副本。

<a id="build-notes"></a>
## 构建笔记

```
styles/woodcut/demo/
  engine/        index.js (shape, cutAlong, flecks, rays, plate…), knife.js (strokes), hatch.js (regions, streamline hatching),
                 print.js (WebGL2 print/block compositor), filter.js (image → woodcut)
  stage.js       print frame, camera, caption          world.js   the valley (mountains, village, tower, snow)
  chars.js rig.js views.js   founder & apprentice (parts rig, poses, expressions)   hands.js   height-field sculpts → filter
  interior.js fx.js          workshop, crucible, pour, sparks, mould; bell, bellows, gifts, villagers, sound rings
  trans.js       paper curl / peel        shots.js shots2.js   the 17 shots        film.js main.js   assembly, captions, events
  timeline.json  tempo grid + every cue   music/score.py   original score   mix.py   foley + ambience + voice + ducking + bell
  tools/         cuecheck.py subs.py final_asr.py mux.sh      test.js   ?test=char|hands|pour|village|sheetA|sheetB|filter|spark
```
1. 先写入`timeline.json`（网格+cue键）和cue表；将它们交给音乐分代理；平行绘制。
2. 在任何故事之前构建引擎和一个风格定帧。在静止图像上获得正确的雕刻+印刷效果。
3. `sh demo/build.sh` 重建一切：TTS → Whisper 语音识别 → 配乐 → 事件 → 提示检查 → 混合 → srt → 渲染（4 个工作人员 ≈ 45 秒，1404 帧）→ 复用器（−14 LUFS，颗粒 6，CRF 28）→ 影片上的耳语 → 风格定帧 / 海报 /发动机示例。
4. 使用影片本身的 1–2 fps 接触表以及每个关键动作的全尺寸帧（剥离、粉碎、破裂、射线、钟形回拉、片尾卡）查看两次。

与示范的道具相关的陷阱：

- **白雪上的雪是看不见的。** 添加黑色雪堆和风刻地面；天空和黑暗物质上的雪花。
- **第一个钟**从带有音调正弦摆动的短舱口部分变成锯齿形V形；修复了长剪辑和一条宽高光带。
- **从模具中流出的蒸汽**在顶部绘制为火焰；移到了主题后面。
- **延迟缓存笔划** (`X.coatFolds || []`) 打破了渲染工作人员之间的确定性。
- **金属礼物点击掩盖了叙述者**（低声听到“is had”代表“it had”）。 拟音也必须躲避声音。将违规击球移至远离中心的位置。
- **文件大小**：精细阴影+每印象墨水噪声+颗粒6在CRF 19上制作了58秒的影片 326 MB。使用`-tune grain`在CRF 28上重新编码：93 MB，并且在1:1裁剪下没有明显差异。
- 结构张量 NaN 来自盒子模糊，在平坦区域留下微小的负和。
- 当许多渲染同时运行时，`still.mjs` 可能会失败。最多重试 3 次。

<a id="engine-reference"></a>
## 发动机参考


`demo/engine/index.js` 是独立的（仅导入 `/core/lib.js`）。它绘制 **any 路径或形状**作为雕刻浮雕并打印它。您始终在两块画布上工作：**面具**（填充黑色=未切割的块；绘制白色=切割掉）和可选的**色板**（alpha=印版密度），然后调用打印机。

|功能|它的作用|关键选项|
|---|---|---|
| `canvas(w=1920, h=1080)` | → `[canvas, ctx]` | |
|`shape(polys, o)`|雕刻实体：黑色剪影 + 白色光环 + 由 `light` 照亮的形状跟随阴影。返回 `{ draw(g, t), strokes, halo, reg, tone }`。|`light` (`light(x,y,z)`)、`sp` 间距、`wmax`、`lo/hi` 音调范围、`dir` (`'contour'` / 角度 / `dirRing(cx,cy,sy)` / `dirRadial(cx,cy)` / fn)、`halo` px、`white`（带黑色切口的白色部分）、`tone(reg)→(x,y)=>0..1` 覆盖、`seg`、`gap`、`reveal:{t0,t1,key,speed}`|
|`cutAlong(path, o)`|将路径分解为手工切割的刀划（轮廓、规则、绳索、裂缝）。|`w`（编号或 `(u,pt)=>w`）、`kind` `'k'|'v'|'u'`、`closed`、`seg:[a,b]`、`gap:[a,b]`、`reveal:{t0,t1,speed}`|
|`hatch(region, o)`|简化任何 `Region` 的剖面线（均匀间隔、方向和宽度字段）。|`dir(x,y)`、`tone(x,y)`、`sp`、`wmax`、`seg`、`gap`、`kind`、`reveal`|
|`flecks(pts, o)`|刺伤（雪、火花、碎片）。 `pts = [[x,y,r],…]`|`angle`、`seed`|
|`rays(cx, cy, o)`|一阵雕刻光芒。|`n`、`r0`、`r1:[a,b]`、`w`、`jit`、`bend`、`a0/a1`、`reveal:{t0,t1,jit}`|
|`drawStrokes(g, strokes, {t, color})`|在时间 `t` 上在蒙版上绘制笔划（逐步雕刻显示定时笔划，刀尖等）。 `color:'#000'` 重新墨水。| |
|`plate(c, polys, a)`|对 **一种颜色** 板进行涂漆。它仅显示掩模被剪成白色的位置。| |
|`woodcutFilter(img, o)`|**图像/视频帧→木刻。** 亮度设置切割宽度，结构张量设置切割方向；返回带显示时间的笔画。|`rect:[x,y,w,h]`、`sp`、`black/white/gamma` 级别、`res`、`region`、`reveal:{t0,t1,mode:'light'|'radial'|'down'|fn,speed}`|
|`makePrinter(W,H).render(mask, plate, o)`|WebGL2 合成器 → 画布。|`mode:'print'|'block'`、`seed`（纸张）、`inkSeed`（每次印张）、`plate:'#hex'`（单色）、`ink`、`paper`、`reg:[dx,dy]`套准不准、 `edge` 毛刺、`sheen`、`wetX`|
|`light(x,y,z)`、`Region(polys | drawFn, {res,bbox})`、`mkStroke`、`spline`、`offsetPoly`、`ellipse`、`rect`|帮手| |

示范级，可重复使用：`demo/trans.js` `curl(g, front, back, xf, r)` + `peelState(u)`（纸剥离）； `demo/hands.js` `Sculpt`（胶囊/斑点/木板/折痕→ `shade(light)`）用于特写。

**最小示例**：暖橙色`#D97757`四点火花，带有光标尾部，雕刻并保持其自己的颜色。正是`demo/test.js`中的`?test=spark`；结果是 `demo/stills/engine_example.jpg`。

```js
import * as WC from './engine/index.js';
const [mask, m] = WC.canvas(), [plate, c] = WC.canvas(), P = WC.makePrinter();
const star = []; for (let i = 0; i < 8; i++) { const a = i / 8 * Math.PI * 2 - Math.PI / 2, r = i % 2 ? 70 : 260; star.push([960 + Math.cos(a) * r, 500 + Math.sin(a) * r]); }
const spark = WC.shape([star], { light: WC.light(.5, -.6, .6), sp: 9, halo: 8,
  reveal: { t0: 0, t1: .8, key: (x, y) => Math.hypot(x - 960, y - 500) / 300 } });        // carved from the centre out
const tail = WC.cutAlong([[1030, 590], [1090, 680], [1110, 770]], { w: 24, kind: 'u', seg: [300, 400], reveal: { t0: .8, t1: 1.1, speed: 900 } });

function frame(g, t) {
  m.fillStyle = '#000'; m.fillRect(0, 0, 1920, 1080);                                       // the uncut block
  c.clearRect(0, 0, 1920, 1080);
  WC.drawStrokes(m, WC.rays(960, 500, { n: 36, r0: 300, r1: [420, 640], w: 10, seed: 2, reveal: { t0: .5, t1: 1.0 } }), { t });
  spark.draw(m, t);
  WC.drawStrokes(m, tail, { t });
  WC.plate(c, [star], t > .8 ? 1 : 0);                                                      // the one colour
  g.drawImage(P.render(mask, plate, { seed: 4, plate: '#D97757' }), 0, 0);
}
```

**对照片或影片框架进行过滤**（用于重新绘制素材）：`const F = WC.woodcutFilter(video, { rect: [36, 36, 1848, 912], sp: 5, reveal: { t0, t1, mode: 'light' } }); m.fillStyle = '#000'; m.fillRect(…); WC.drawStrokes(m, F.strokes, { t });` 然后打印。 1080p 帧大约有 1,900 次剪切和 140 毫秒。请参见 `demo/stills/frame_filter.jpg` 和 `?test=filter&img=…`。对于移动的镜头，请使用相同的 `seed` 重新运行两次 (12 fps)，以便剪切在图像的位置保持稳定。
