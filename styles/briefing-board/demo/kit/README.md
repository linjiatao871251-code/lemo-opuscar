<a id="briefing-board-kit"></a>
# 简报板套件

一个用于工程简报板外观的小型数据驱动套件：一面真实的白板墙，已拍摄，
上面贴有剪下来的照片、磁性标签、磁铁、钢尺、橡皮图章和
自行绘制的标记墨水。一台渲染器即可制作影片、剧照、缩略图和社交卡。
一切都是与深度（视差、阴影、景深、运动模糊）合成的 2D 图层。

```
kit/
  board.js        renderer: board surface and light, camera (overlapping eased moves, impact shakes,
                  hand-held breath), prints, tags, magnets, ruler, card, stamp, ink, erasing,
                  bilingual subtitles; TEXTS for the reading check, SUBCHECK for one-line subtitles,
                  RESCHECK (source px per screen px of every print at time t)
  batch.mjs       scene JSON → PNG/JPG, many at once, any size
  objects/        the object library: <id>.png (cut-out) + <id>.json (size, anchors, credit, how it was cut)
  fonts/          LXGW Marker Gothic + Noto Sans SC (subsets), Archivo, IBM Plex Mono — all OFL, fetched by tools/fetch_fonts.py
  tools/
    kit_env.sh      the cut-out tools' private venv (demo/.venv: numpy, scipy, Pillow, onnxruntime) and the BiRefNet model
    fetch_sources.py the source photos listed as used in sources/candidates/candidates.json (Commons URLs, licences)
    prep_object.py  photo → cut-out object (BiRefNet ONNX mask, or a polygon / mask image without it; sky key, clean edge, shared grade)
    sky_key.py      a mask for thin things shot against a clear sky (cables, stays), to add to BiRefNet's
    redraw_stays.py      stay cables measured from the sky key and redrawn as clean lines (pylon stays in front)
    redraw_suspension.py main cables (fitted parabolas) and hangers (measured) redrawn as clean lines
    repair_hangers.py    hangers lost against a busy background continued down to the deck
    mirror_span.py / stretch_span.py   one pylon + fan mirrored into a main span / a main span stretched
    clean_lettering.py   median-filter wipe of names and logos inside rectangles (before cutting)
    make_print.py        an uncut photo on white photo paper, for pinned prints
    ship_anchors.py      bow / stern / waterline anchors of a side-view ship
    fetch_fonts.py  subset the Chinese fonts to the characters a scene uses (network)
    rebuild_objects.sh  rebuilds every object in objects/ from sources/, exactly as used
```

<a id="make-frames"></a>
## 制作框架

```sh
node kit/batch.mjs scenes/stills/*.json --out stills
```

A仍然重用一个世界并设置自己的摄影机和时间：

```json
{ "extends": "scenes/film.json", "out": "thumb.jpg", "size": [1280, 720], "t": 35, "hand": 0,
  "cam": { "x": 2800, "y": 1780, "z": 0.22, "roll": 0, "moves": [] } }
```

新的影片是一个新世界：复制`scenes/_gen_film.py`，更改布局、时间线和
对象。渲染器附带外观（板、灯光、墨水、标签、磁铁、摄影机行为）。

<a id="the-world-scene-json"></a>
## 世界（场景 JSON）

|钥匙|意义|
|---|---|
|`board`|`{w, h, seed, texScale, ghosts}`（以板像素为单位）（缩放 1 显示 1,920 板像素）。珐琅、擦掉的记号笔残影、污迹和框架来自 `seed`|
|`light`|`{x, y, r, min}`：窗口光来自哪里以及距离窗口多远电路板变暗|
|`cam`|`{x, y, z, roll, moves, shakes}`。每一步 `{t, d, dx, dy, dl (Δ ln zoom), dr, a, b}` 都会增加一个缓和的增量；动作可能会重叠。缓动的速度为 ∝ u^a (1−u)^b，因此速度和加速度保持连续； `a < b` 启动快，稳定长（惯性）。 `shakes`：`{t, amp, f, k, dir}` 用于冲击|
|`hand`|手持式呼吸幅度（px）； 0 为剧照|
|`elements`|印刷品、标签、磁铁、尺子、卡片、邮票、墨水（下）|
|`subs`|`[{t0, t1, zh, en, speech}]`：内置双语字幕，每种语言一行|
|`tray`|托盘中的记号笔和橡皮擦|
|`mb`|`[{t0, t1, n}]` 物体快速移动时额外的运动模糊样本|
|`ev`|混音的声音事件（`events.mjs` 导出它们）|

<a id="elements"></a>
### 元素

|类型|什么|关键领域|
|---|---|---|
|`print`|剪下来的照片安装在板上（真实阴影，视差）|`src`、`xy`（中心）、`w` 或 `h`、`z`、`rot`、`arrive {t, kind: drop/slide/fade, d, lift, land}`、`moves`（轻松行程）、 `leave`|
|`tag`|磁性标签|`text`、`xy`（磁铁）、`size`、`rot`、`color`、`magnetColor`、`arrive {kind: swing/snap}`、`strike {t, d, color}`|
|`magnet`|圆形磁铁|`xy`、`r`、`color`（石墨、红、蓝、白）、`arrive {kind: snap}`、`leave {kind: pop}`|
|`ruler`|两个磁铁上的钢尺|`from`、`to`、`w`、`arrive`|
|`card`|用磁铁固定的印刷卡|`xy`、`w`、`h`、`rot`、`lines [{text, font: sc/mono/sans/marker, size, x, y, color}]`、`magnets`|
|`stamp`|橡皮图章印象|`text`、`xy`、`size`、`rot`、`t`|
|`ink` · `line`|标记线、可选箭头、破折号|`points`（像素或 `"objectId.anchor"`）、`lw`、`color`、`t`、`d`、`dash`、`arrow`、 `ea`/`eb`|
|`ink` · `dim`|带箭头和延长线的尺寸|`from`、`to`、`ext [[x, y0, y1]]`|
|`ink` · `write`|标记刻字（LXGW Marker Gothic），用轻微的手逐个字形显示|`text`、`xy`（基线）、`size`、`align`、`rot`|
|`ink` · `hatch`|许多短划都有自己的时间（水、陆孵化）|`strokes [{points, t, d}]`|
|`ink` · `ring`|手绘戒指|`c`、`r`（或 `[rx, ry]`）|
|`ink` · `wake`|移动印刷品后面的尾迹|`follow`、`len`； `dir: 'side'` + `y`（水线），用于从侧面看到的船舶|

每个墨水元素都绘制在`t … t + d`上； `erase {t, d}` 抹成鬼了； `out` 使其褪色。

<a id="add-an-object"></a>
## 添加对象

```sh
$LIB/.venv/bin/python kit/tools/prep_object.py <photo> <id> --keep-largest [--crop …] [--poly …] --anchor L=0.12,0.86 --anchor R=0.88,0.86
```

锚点位于输出的标准化坐标中。桥梁承载`L`和`R`（主跨支撑在
水线），以便场景可以将它们缩放到跨度；该船载有`bow`和`stern`。
按照照片自己的分辨率进行剪切（`--max` 不小于裁剪）：`tools/rescheck.mjs` 构建失败（如果有）
帧显示每个屏幕像素少于一个源像素的打印。列出 `CREDITS` 中的每个图像及其来源和许可证。

<a id="the-look-as-rules"></a>
## 外观，按照规则

- **无幻灯片镶边。** 无页眉、页边距、数字块或居中布局。文字写在黑板上或钉在黑板上。
- **事物是物理的，标记是绘制的。** 印刷品、标签和磁铁投射阴影并带着重量到达；墨水平铺在板上，用笔尖进行绘制。
- **三种墨水颜色，一种含义。** 石墨 = 名称和规则。蓝色=水和测量。红色=决定。
- **一堵墙。** 影片永远不会切到一页； 摄影机行驶。整堵墙在最后一次被看到。
- **可读。** 每节拍一个想法；每个文本都保留其阅读时间（`readcheck.mjs`）。
