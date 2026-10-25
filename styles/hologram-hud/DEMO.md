<a id="sci-fi-hologram-hud--our-demo"></a>
# 科幻全息平视显示器 — 我们的示范

众多例子中的一个。请勿重复使用其故事、弧线、镜头、道具或时间安排。

示范：*伏特·规格扫描*（39 秒：34 秒场景加 5 秒片尾卡）·`hologram-hud.mp4`·源位于 [`demo/`](demo/)


<a id="story--structure"></a>
## 故事与结构

虚构城市电动自行车的规格演练，STYLE.md §11 的第一个用例：硬件产品被扫描到发光的线框中，三个部件一次锁定一个（电池、电机、制动器），最后线框点亮为实心全息图，并放入可以用作海报的规格表中。

镜头结构：扫描输入→标题→3×（锁定→摄影机运动→局部爆炸→引导→值）→重新组合→实体全息图转动→规格表锁定→片尾卡。第 1 部分有 3 个小节，其他部分各有 2 个小节。每个值在大卡上停留 ≥ 2.5 秒，然后停靠在左导轨中直至结束，因此每个规格在屏幕上显示 10-25 秒。

**签名照**：第1部分为一招。锁定，推动，盖子滑动，电池发光，引导​​线拉出，“80公里”滚动琥珀色。

<a id="shots"></a>
## 镜头

|打|摄影机|为什么|
|---|---|---|
|挂机（0–2.6 秒）|3/4 前部，俯仰 14°，慢速 **轨道**偏航 57° → 24°**起重机向下**|从上方看，扫描平面呈上升的椭圆形。然后它下降到接近视线水平，并为左侧的标题留出空间。第 1 帧已显示车轮高度处的平面|
|第 1 部分（慢速）|**推入** 2.85→1.6（1.5秒缓出），然后漂移|第一个规格占用的时间最多|
|第2部分|**鞭**（跟随盒子）+**轨道**绕轮毂轴，偏航−11°→46°|轴向爆炸仅在绕轴旋转时读取|
|第 3 部分（快速）|**拉回**至满+**放大镜**（×4.3，其自身的反轨道）|刹车很小：屏幕上同时显示两个刻度|
|重组|**回拉+起重机下降**至俯仰0|低角度使物体在点亮前直立|
|高点|**转台 360°**+**起重机上升** 0 → 13° + 轻微推动|观众看到每一面的唯一时刻|
|锁仓|接近静态，缓慢 **多莉** 3.5 → 3.4|观众读到|
|结尾|**扫描-擦除**自上而下，然后是片尾卡|镜像钩子|

对于该产品，为什么选择这条路线：钩子的轨道向下延伸，使上升的扫描平面显示为椭圆形；重新组合后拉回并伸长到视线水平，以便自行车在灯光亮起之前站起来；转盘是双方唯一展示的时刻；结尾的扫描从上到下擦除以反映钩子。每个都是 STYLE.md §6 中的一个选择，而不是该风格的默认开头或结尾。标题在扫描后滚动并返回到最终锁定的同一位置；三帧故障是在点火时发生的。

帧数：fov 0.6。大卡片位于 x ≥ 1240，导轨位于 x 110–470，字幕固定在底部中心（基线 y 962），放大镜位于 y 580 上方。在宽放大镜镜头中，目标位于框架的 x 0.49 → 0.475 处。

运动数：目标框从 1.9 倍静止姿势边界框开始，30% alpha，在 0.22 秒内捕捉；标签 `TGT 0N · LOCK`。爆炸：电池盖*沿着下管*滑动，而电池停留并变热；电机轴向剖分（盖/转子/定子/盖），而转子和定子反向旋转；制动卡钳将转子两侧的部分分成两部分，活塞的分离“小于”主体，因此它们看起来是延伸的。打开超过 1 节拍（第 1 部分：2 节拍），关闭超过 0.5 秒。滚动值：0.5 秒（第 1 部分：1 秒）。芯片底座：卡片淡入0.35秒，芯片滑动x 140 → 110；导轨台阶 `min(112, 410 / (n − 1))` px，因此适合 5 个芯片。 Whip：0.5 s 立方进出，在下一次锁定前 0.45 s 开始； 1/48 上有 5 个子帧。

<a id="score-structure"></a>
## 配乐结构

- 配乐弧线：第一个规格上稀疏，每个部分添加一层，高点前减速，真正静音的一拍，点火时的下降（最响亮的时刻），锁定下的半场时间。
- 120 BPM（1 巴 = 2 秒）； `tools/cuecheck.py` 根据 `music/score.json` 检查每个关键事件（全部在 1/16 网格上，0 毫秒偏移）。
- 原始 numpy 合成，D 小调，多里安色彩；和弦 Dm9 → B♭maj7 → Fmaj9 → G6。四分之一的 D1 方波脉冲。
- 第 1 部分没有鼓，第 2 部分 + 帽子，第 3 部分 + 拍手和琶音上升一个八度。重新组合减速（第 16 分 → 第 8 分 → 四分之一滑行）。一拍真正的寂静。点火时下降（808式正弦滑音+7音宽锯齿和弦）。半场暂停。 片尾卡下的琶音被逐个音符删除。
- 静音：第一个锁之前的半拍（只剩下房间的嗡嗡声；锁敲击是它之后的第一个声音）和点火前的真零完整节拍。
- 检测光点 D–F–A；琥珀色确认 = D6 + A6 + E7。 J/L-cuts：鞭子落在电机上之前0.4秒开始电机呜呜声，制动锁之前0.4秒开始液压嘶嘶声；嗡嗡声和弦尾将扫描擦除转移到片尾卡中。
- 声音：Kokoro `af_heart`，速度 1.0（`af_nicole` 呼吸声太大且缓慢：同一条线路为 7.0 秒，而为 4.4 秒）。音乐在声音下降低了−16.5 dB，拟音 −15 dB，最大滤波器保持时间为 0.5 秒；仅锁定/确认的前 0.2 秒命中了转义。

<a id="palette--props"></a>
## 调色板和道具

- 具有径向升降 `hsl(hue+6, 65%, 7%)` 的平台 `hsl(hue+12, 70%, 2.4%)`； 48 px 点网格（视差 0.2）；小插图 0.5。
- r = 0.7 / 1.05（亮）/ 1.12（虚线）/ 1.45 / 2.1 处的焊盘环，120 个刻度（每 10 个长），24 条径向射线，旋转 0.12 rad/s.
- 线框：`lighter` 在 7 个 alpha 级别中描画 1.3 像素；发光 1/4 分辨率模糊 3 px ×0.85 和 ⅛ 分辨率模糊 4 px ×0.7；颜色`hsla(hue, 100%, 50–80%, a)`;热边缘 `hsla(hue, 70%, 92%)`，扫描前端下方 7 厘米。
- 实心：菲涅耳 `0.3 + 0.7·(1 − facing)^1.6`（面 = 投影面积 / 边缘积），隔行扫描 2 px 全/2 px，38 % 滚动每帧 1 px；点火时线宽 ×1.5 缓动至 ×1.12；点火时和弦变化时光波±7 cm。光束梯度 10 % → 0、26 条射线、70 个尘埃。
- 颜色：`hue` 188（青色）、`accent` 38（琥珀色）；替代内容使用 204 / 18（蓝色/橙色）。
- 类型：Rajdhani 300 用于大数字和产品名称（26 像素跟踪），500/600 标签（2–3 像素跟踪）；共享技术单色 20–22 像素。板 `rgba(1,8,12,.72)`，边框 28 %，10 px 角刻度（hud.js 中的 `plate()`）。
- HUD：46 px 角括号距边缘 44 px；标尺每 24 像素刻度一次（每 5 个长）。左上：产品//规格扫描。状态：扫描 042% → 扫描完成 · 3 个系统 → 目标 2/3 · 电机 → HOLO SOLID · 360° → 规格表 · 准备就绪。
- 字幕：板 `rgba(1,8,12,.62)`，两个对角青色括号，四个声纹条，Rajdhani 表现媒介 38 px，换行 1180 px；在语音之前 0.1 秒，在下一行之前 0.12 秒。
- 电动自行车模型：管架、带轮胎的车轮（3环+十字肋）、轮圈、辐条和轮毂；电池位于下管中；轮毂电机；带卡钳的盘式制动器。卡钳需要一个紧贴转子边缘的弧形主体、圆形活塞面、遵循转子曲线的衬垫以及转子上的通风孔。

<a id="end-card"></a>
## 端卡

锁定后：影片标题、SCI-FI HOLOGRAM HUD、Lemo-Opuscar、LemoLab × Claude Opus 5.5 和制作人员，每行滚入。LemoLab 签核仅属于该库的示范；用户的影片没有 LemoLab 积分，也没有该卡的副本。

<a id="build-notes"></a>
## 构建笔记

```
styles/hologram-hud/demo/
  content.json          all text, numbers, colours, model path, voice lines   content_alt.json   the swap test (drone)
  engine/holo.js        wireframe engine (projection, scan, explode, Fresnel faces, glow, pad, scan plane, normalise, modelFromPath)
  engine/hud.js         HUD layer (target box, leader, rolling text, spec card, chip, marker, beam, subtitle, chrome, glitch)
  models/mkmodel.mjs    primitive builder (tube, ring, disc, box, saddle, fender, wheel, cells, stator, rotor, caliper…)
  models/gen_volt.mjs   the e-bike    models/gen_kite.mjs   the drone
  film.js               timeline + cameras + states (only calls the engine)    frames.js   engine demo scene (?scene=star)
  music/score.py        original score from timeline.json    mix.py   UI + mechanical foley + ambience + voice + ducking
  tools/                make_lines.mjs export.mjs cuecheck.py final_asr.py
```
1. 编写模型生成器（零件→带有爆炸向量的零件；`internal`、`hot`、`box:false`、`anchor`、`center`、`tagDir`），然后编写`content.json`。
2. `tools/export.mjs` 转储 `events.json` / `timeline.json` / 字幕。在制作动画时，将 `timeline.json` 和音画节拍对照表交给音乐子代理。
3. 查看剧照 (`node core/render/still.mjs <demo> t… [--q content=…]`) 和 1 秒接触表，两次，以及每个锁、鞭子、静音和点火周围的条带。
4. `sh demo/build.sh` 重建一切：模型 → TTS → Whisper 语音识别 → 导出 → 配乐 → 提示检查 → 混合 → srt → 渲染（2 个工作人员的 936 帧约 45 秒；鞭帧成本 5×）→ 复用器（−14 LUFS，颗粒 0）→ 最终Whisper 语音检查。

此构建中遇到的陷阱：
- 使用 `setTransform(…, offset)` 滚动交错，然后使用 `destination-in` 清除移动矩形 → `offset % patternHeight` 之外的所有内容，或者填充在第一秒后消失。
- 制动软管给目标箱充气 → `box:false`。
- 长对角引线上的热点标签读作指向错误的零件→零件主体上的环，旁边的芯片，闪烁零件。
- 写在下一段内的鞭子作为硬剪辑播放 → 在上一段中开始并检查 0.1 秒的帧条带。
- 无支架灯、无夹子鞍座；在交换模型中，无人机的着陆腿从船体外部开始（腹部安装座和臂根处的折叠铰链将其固定）。
- 两个平行的盒子（盖子和电池都移动了）没有被解读为爆炸。
- 带内 (300–4 kHz)、滚转、舵机和确认和弦仅比声音低 3 dB。
- 从不同形状绘制的光束产生暗楔形或双亮接缝→一条路径具有三个子路径，非零缠绕。
- 扫描擦除首先仅剪切边缘，半透明的面仍然存在。

<a id="contentjson-fields"></a>
## content.json 字段

每个单词、数字、颜色和型号均来自`demo/content.json`;该代码不包含任何复制文本。交换它可以重新排列时间线、音乐、提示和轨道间距，这使其成为一个很好的选择**技术检查**发动机的。这不是用户的方式影片是由：用户的影片拥有自己的创作方案， 命令，摄影机路径和时间线（STYLE.md §11).

|场地|类型|允许|如果超出范围|
|---|---|---|---|
|`product`|细绳|1–10 个字符|较长的名称仍然滚动，但 176 px 类型将溢出 410 px 列：保持较短或减小 `titleBlock` 中的尺寸|
|`model_code`、`category`|细绳|≤ 30 个字符|以单行 22 像素显示|
|`tagline`|细绳|≤ 60 个字符|以 420 像素自动换行并缩小至 20 像素|
|`model`|小路|JSON 模型（如下）|任何尺寸：它是标准化的。 `callouts[].part` 中命名的部件必须存在|
|`hue`、`accent`|0–360|任何|整个影片重新主题|
|`voice`|`{id, speed}`|心的声音|用Whisper 语音检查|
|`intro_vo`、`outro_vo`、`callouts[].vo`|细绳|介绍 ≤ 5 秒；第 1 部分 ≤ 4.8 秒；其他部分≤3.5秒|字幕被夹在下一行；较长的线与下一个锁重叠|
|`*_vo_asr` / `callouts[].vo_asr`|细绳|选修的|应该听到什么耳语（数字等）|
|`callouts[]`|大批|**2–5** 项目：`part`、`label`（≤ 24 个字符）、`value`（≤ 6 个字符）、`unit`（≤ 4）、`detail`（≤ 40，可选），`vo`|第 1 部分有 3 个小节，其他部分各有 2 个小节。超过 5 个将无法安装在导轨上|
|`footer.weight`、`footer.price`|`{label, value, unit}`|值 ≤ 7 个字符|自动调整至 40 像素|
|`footer.cta`|细绳|≤ 34 个字符|自动调整至 14 像素|
|`film_title`、`credits[]`|字符串| |片尾卡|

模型中的零件可以设置 `tagDir: -1`，因此锁定热点芯片位于其环的左侧。

检查，来自存储库根（语音、Whisper 语音检查、配乐、提示检查、混合、字幕、渲染和其他内容的复用器）：
```
CONTENT=content_alt.json NAME=kite sh styles/hologram-hud/demo/build.sh
```
输出转到 `demo/out/kite/`（`kite.mp4`、`kite.srt`、`poster.jpg`）。交换测试（蓝色/橙色的四部分折叠无人机）在 43 秒、4 个部分、-14.0 LUFS、0 个提示不匹配时得出；剧照 `demo/stills/alt_title.jpg`、`alt_signature.jpg`、`alt_lockup.jpg`。无需构建即可预览内容：`node core/render/still.mjs styles/hologram-hud/demo 12 --q content=<file>.json`。

最小内容示例（两部分）：
```json
{ "product": "ORBIT", "model_code": "S1", "category": "Smart speaker", "tagline": "Room-filling sound.",
  "model": "models/orbit.json", "hue": 170, "accent": 40,
  "voice": { "id": "af_heart", "speed": 1.0 }, "intro_vo": "This is Orbit.",
  "callouts": [
    { "part": "driver", "label": "Woofer", "value": "4", "unit": "in", "vo": "A four inch woofer." },
    { "part": "mics", "label": "Far-field mics", "value": "6", "unit": "", "vo": "Six microphones hear you across the room." } ],
  "footer": { "weight": { "label": "Weight", "value": "1.2", "unit": "kg" }, "price": { "label": "From", "value": "199", "unit": "USD" }, "cta": "Available now" },
  "outro_vo": "Orbit. Available now.", "film_title": "Orbit · Spec Scan", "credits": ["…"] }
```

<a id="engine-reference"></a>
## 发动机参考

发动机以这种风格绘制了**any形状**。为其提供一个线框（顶点、边、可选的四边形），或使用 `modelFromPath` 从 2D 路径构建一个线框。对于您自己的对象，请使用 `models/mkmodel.mjs` 中的基元编写生成器（或将 CAD 导出转换为以下格式）。

**`engine/holo.js`**
|功能|目的|
|---|---|
| `loadModel(url, {normalize=true, diag=2.3117})` |加载模型 JSON，准备类型化数组，以及**正常化**它适合舞台尺寸（边界框对角线），因此相机适用于任何产品|
|`prepModel(json)` / `normalizeModel(m, diag)`|内存模型也是如此|
|`modelFromPath(pts2d, {depth, id, slices, explode})`|将任何封闭的 2D 路径挤出到具有侧面的线框体中|
|`makeCamera(cam, W, H)`|`{project(x,y,z,out)}` 用于凸轮 `{target, yaw, pitch, dist, fov, cx, cy, roll}`|
|`new Holo(W,H).draw(ctx, model, cam, opts)`|用发光来绘制。选择：`hue`、`spin`（转盘）、`scan:{y,band}`（向上增长到y）、`scanDown:{y}`（向下擦除到y）、`explode:{partOrPiece:0–1}`、`angle:{piece:rad}`（绕片轴旋转）、 `solid:0–1`、`wave:{y,w}`、`focus`+`dim`、`flash:{part:0–1}`、`keep:{piece:'#hex'}`（**单色例外**）、 `lineWidth`、`gain`、`glow`、`only`。返回 `{bbox:{part:[x0,y0,x1,y1]}, anchor:{part:[sx,sy,z]}}`|
|`drawPad(ctx, cam, W, H, {hue, rot, alpha})` / `drawScanPlane(ctx, cam, W, H, y, {hue, r, rot, alpha})`|投影仪垫和扫描平面|

**`engine/hud.js`**：`theme(hue, accent)`、`background`、`vignette`、`chrome`、`plate(ctx,T,x,y,w,h,a)`（深色文字板）、 `targetBox(ctx,T,bbox,k,{flash,tag,lockK})`、`leader(ctx,T,from,elbow,to,prog,{pulse})`、`rollText(str,k,frame)`、`monoText`、`specCard(ctx,T,x,y,{label,value,unit,detail},{reveal,roll,detail,frame,flash})`、`chip`、`marker(ctx,T,p,label,a,pulse,dir)`、`beam(ctx,T,project,a,t,{y1})`、`subtitle`、 `glitch`、`fitFont`、`wrap`。

最小示例：带有光标尾部的暖橙色 `#D97757` 四点星形，扫描然后锁定（`demo/frames.js`、`?scene=star`）：
```js
import { Holo, modelFromPath, normalizeModel } from './engine/holo.js';
import * as U from './engine/hud.js';
const P = []; for (let i = 0; i < 8; i++) { const a = Math.PI/2 + i*Math.PI/4, r = i % 2 ? .16 : .5; P.push([Math.cos(a)*r, Math.sin(a)*r + .6]); }
const star = modelFromPath(P, { depth: .12, id: 'star' });
const tail = modelFromPath([[.62,.1],[.7,.1],[.7,.55],[.62,.55]], { depth: .06, id: 'caret' });
const m = { parts: [...star.parts, ...tail.parts] }; m.byId = Object.fromEntries(m.parts.map(p => [p.id, p])); normalizeModel(m, 1.6);
const T = U.theme(188, 38), cam = { target:[0,.55,0], yaw:.6, pitch:.18, dist:2.6, fov:.6, cx:960, cy:540 };
const info = new Holo(1920,1080).draw(ctx, m, cam, { hue: T.hue, scan: { y: .8 }, keep: { star: '#D97757' } });
U.targetBox(ctx, T, info.bbox.star, 1, { tag: 'TGT 01 · LOCK' });
```

**模型数据格式**（一个JSON文件，米，**y up**，x =产品的正面，z =朝向观察者的一侧；任何比例都可以，因为它在负载上标准化）：
```json
{ "name": "VOLT CE-01",
  "parts": [                                   // part = one thing a callout can target (battery, motor, brakes…)
    { "id": "brakes",                          // referenced by content.json callouts[].part
      "anchor": [0.527, 0.416, 0.09],          // hotspot: where leader lines and the lockup ring land (ON the part's surface)
      "center": [0.524, 0.428, 0.08],          // optional: what the close-up / loupe camera looks at (defaults to anchor)
      "tagDir": -1,                            // optional: lockup number chip left (-1) or right (1) of the ring
      "pieces": [                              // piece = a rigid sub-assembly that moves on its own in the explode
        { "id": "brake-caliperA",
          "v": [x0,y0,z0, x1,y1,z1, …],        // vertices, flat
          "e": [0,1, 1,2, …],                  // edges: index pairs into v (the wireframe lines)
          "q": [0,1,5,4, …],                   // optional quads: 4 indices each (the translucent solid-hologram faces + Fresnel)
          "explode": [0, 0, 0.10],             // offset at explode = 1, along the assembly axis
          "axis": { "c": [x,y,z], "d": [0,0,1] }, // optional spin axis (rotors, fans)
          "internal": true,                    // optional: hidden until the part opens (cells, stator)
          "hot": true,                         // optional: glows near-white while open (the thing that makes the number true)
          "box": false }                       // optional: excluded from the target-box bounds (long hoses, cables)
      ] } ] }
```
规则：每块棋子必须与相邻棋子物理接触。管子是环形加纵向线。将总数保持在 5k 个顶点/6k 个边左右，以实现快速渲染。为带有钥匙编号的部件提供 `hot` 内部部件和*沿其自身轴*滑动的外壳。
