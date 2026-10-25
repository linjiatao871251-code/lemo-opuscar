<a id="exploded-teardown--our-demo"></a>
# 拆解爆炸——我们的示范

众多例子中的一个。请勿重复使用其故事、弧线、镜头、道具或时间安排。

示范：*21键，已打开*《二十一键》（38.75秒）·`teardown.mp4`·来源在[`demo/`](demo/)

开源 Corne v4 分体式键盘的一半（foostan/crkbd，CC BY 4.0 / MIT），由项目自己的 KiCad 板、开关板文件、案例 STEP、物料清单和构建指南构建而成。中文屏幕，英文旁白，双语字幕（中行在上，英文在下）。屏幕上和声音中的每个数字都在 [`demo/FACTS.md`](demo/FACTS.md) 中。图中未显示项目名称和标志（仅在端卡信用额度中）；芯片和部件号是 BOM 中的组件名称，封装顶部没有标记。这是根据项目发布的文件制作的非官方影片； Corne 项目及其作者 (foostan) 并未制作或认可它。

<a id="story--structure"></a>
## 故事与结构

梗概：二十一把钥匙看起来就像一个物体；打开后，它们是在公共文件中绘制的六层，一直到芯片、灯和插座；再次关闭，上面的每一个尺寸都是公布的数字。

弧线：触摸（在键帽上掠过宏，一次真正的击键）→ 开口（一个轨道，层首先抬起顶部，按键呈波浪形，六个标签）→ 内部（潜入板和外壳之间的空间，向上看板的背面：RP2040，闪光灯，反向安装的 LED；然后穿过板上升到开关引脚）→ 回到一起（快速拉回，底部先关闭，按键随行程落地）→ 上的数字对象（关键间距、宽度、深度、高度作为尺寸线）→ 片尾卡。

风格特有表现手法花费：*一次真正的按键*在开场； *分离处的波升力*； *在间隙内*和*落在该零件上的领导者*三站； *内部 LED 灯亮起； *卡片前面的物体*上绘制的尺寸。

<a id="shots"></a>
## 镜头

连续一张摄影机。时间以秒为单位； 96 BPM，条 = 2.5 秒。

|#|时间|镜头|摄影机|风格特有表现手法/注|
|---|---|---|---|---|
|1|0.0–2.5|键帽顶部，前景为橙色 1.5u 键，柔和的光线滑过|放牧微距移动车，眼睛距地面 33 毫米，镜头 30°|挂钩：材质，轻扫|
|2|2.5–4.4|橙色键在 3.13 处移动 4 毫米行程并返回；拉至整半|移动车 → 四分之三英雄，330 毫米|一次真正的按键|
|3|4.4–5.0|握住|轨道继续|沉默1（室内音调，上升的吸音）|
|4|5.0–7.5|按键从左后角呈波浪状升起，然后是开关、板、板、垫片、外壳；脚留在地板上|轨道 −31° → −9°，拉回到 432 mm，模型向左滑动（视图偏移 170 px）|波浪升力；达到5.0|
|5|6.9–11.9|右栏下方画有六个标签：按键帽 1u ×20 · 1.5u ×1、机械轴体十字轴 ×21、定位板 FR-4 1.6 mm、电路板宽度 1.6 mm、铜柱 M2 × 7.5 mm ×4、外壳底厚 2.0 mm|慢速轨道至+18°；在 10.0 时，木板和上面的所有东西都会上升 30 毫米以上|9.75处的签名框（海报）|
|6|12.5–15.0|向下穿过板和板边缘进入间隙；箱子内部亮起|俯冲，452 mm → 30 mm，向上倾斜|潜水旋风提前 0.35 秒开始|
|7|15.0–18.1|板背面：RP2040 (7 × 7 mm)、闪存 (16 MB)、晶体、0402 零件、插座，全部位于封装位置|手持微距，眼距板下24毫米，慢速漂移|领先者登陆芯片|
|8|18.1–21.3|滑动至LED10：反向安装的LED；顶部的灯亮了|9 毫米微距滑轨|里面亮着灯|
|9|21.3–22.3|从板下面出来，越过板|通过堆栈上升|过渡|
|10|22.3–25.0|从下面看拇指排开关：热插拔孔上的引脚；标签热插拔 ×21|将宏保持在引脚高度，开关进一步提升 16 毫米|24.6–25.0 沉默 2|
|11|25.0–27.6|快速拉回；箱子出来了，板子，板子，开关；按键最后落在一波中，每个按键都有其敲击声|拉至 380 毫米，四分之三高|最响亮的时刻（26.6）|
|12|27.5–33.7|封闭半部尺寸线：键距 19.05 mm、138.4 mm、97.6 mm、11.1 mm|高四分之三漂移，z 20° → 40°，374 → 336 mm|在物体上绘制的尺寸|
|13|33.75–38.75|左边为片尾卡，右边为键盘转动|漂移方位角 40° → 59°，视图偏移 −230 px| |

<a id="score-structure"></a>
## 配乐结构

96 BPM，4/4，D（每小节 Dm9 – B♭maj7 – F – C/E），卡上为 D 大调。每一次点击都位于 `src/timeline.js` 的一个节拍或半节拍上。

|部分|时间|调色板|笔记|
|---|---|---|---|
|触碰|0–4.4|八度马林巴琴（柔和）、弓弦颤音琴、房间音|击键：开关点击+低音敲击+返回咔嗒声|
|沉默1|4.4–5.0|房间音调，过滤噪音| |
|开幕|5.0–12.5|马林巴 16 度、电贝司、1 和 3 上的合成器底鼓、2 和 4 上的拍号、闭合踩镲 16 度|波浪中 21 个塑料刻度，每层 swooshes，黄铜环，外壳敲击声，每个标签一个刻度|
|里面|12.5–24.4|弓形电颤琴和弦、玻璃图案、八度踏板踩镲、小节次踢|钟琴在每一站（A5、D6、E6）响起，灯光的琶音|
|沉默2|24.6–25.0|仅房间音| |
|闭幕式|25.0–33.75|凹槽返回，四个在地板上|21 次按键着陆（咔哒声+咔哒声）、木板敲击声、箱子重击声；每个维度都会发出钢笔的嘶嘶声|
|卡片|33.75–38.75|D 大调马林巴卷音、弓弦颤音琴 D–F♯–A、低音 D、钟琴答案|长尾|

混音 (`demo/mix.py`)：语音压缩，说话时音乐比音乐低约 8-10 dB（音乐在语音包络上降低 55%），音乐在 44 Hz 处高通，拟音在 36 Hz 处；声音最大的时刻依次为：落地（26.6）、卡牌、拉回（25.0）、开局击球（5.0）。 影片集成测量为 −14.2 LUFS，LRA 4.9 LU，真实峰值约为 −1 dBTP； 20–60 Hz 比全频段低 12.5 dB。

<a id="palette--props"></a>
## 调色板和道具

- 地面 #34363a → #0d0e10;墨水#f1efe9；重音#ff6b3d（标签索引、尺寸线、1.5u 键、开关分轨音频）。
- 键帽：灰白色#d9d4c9，外柱和拇指上灰色#686c73，1.5u拇指键橙色；用代码绘制的高度一致的雕刻轮廓。开关：通用十字杆（底部 14 毫米，顶部外壳 15.6 毫米），以代码绘制。板黑色 FR-4，核心边缘温暖；板绿色掩模，金焊盘；黄铜六角垫片；深色螺丝；阳极氧化外观案例（文件未命名材质；外观是渲染选择）。
- 旁白：Kokoro `am_michael`，速度0.95。

<a id="end-card"></a>
## 端卡

二十一键 (Noto Sans SC 500)，*21 键，打开* (Inter Light)，`产品拆解 · EXPLODED TEARDOWN`，`CAD：foostan/crkbd · CC BY 4.0`，`LemoLab × Claude Opus 5.5`，橙色规则；关闭的键盘在右侧漂移。 5秒。 “LemoLab × Claude Opus 5.5”签名仅属于该库的示范；用户的影片不带有 LemoLab 积分，也没有该卡的副本。

<a id="build-notes"></a>
## 构建笔记

```
demo/
  build.sh          one command: voice → speech check → cues → events → video → mix → master → .srt → checks → poster
  index.html        WebGL canvas + 2D marks canvas, fonts
  src/timeline.js   the single timeline: beats, layer timings, gaps, narration, label windows, camera keys
  src/main.js       scene, layers, explode/gap, camera (monotone keys), lights, render(t), window.EV
  src/parts.js      keycap, switch, outline extrusion, spacer, screw geometry
  src/pcbtex.js     board textures painted from the KiCad data
  src/comps.js      back-side parts at footprint positions
  src/overlay.js    labels, dimensions, subtitles, end card, readcheck texts, subtitle width check
  mix.py            score (sampler), foley (synthesised), voice, mix → out/mix.wav + out/stems/
  tools/            extract_pcb.py, kicad_geom.py, sexp.py, step2mesh.mjs, fetch_cad.sh (data); fetch_fonts.py;
                    export.mjs (voice lines, cues, timeline.json); subcheck.mjs, motioncheck.py (checks)
  data/             pcb.json (left half, extracted), case.bin (case mesh)
  FACTS.md, CREDITS, stills/styleframe.jpg
```

- `sh demo/build.sh` 在 Apple 芯片上大约需要 3 分钟（假设 4 个工作人员大约需要 60 秒）。在干净的克隆中，它首先重建 git 不包含的内容：来自 CAD 固定提交（网络和临时 occt-import-js 的 npm）的 `data/case.bin` 和 `data/pcb.json`、来自 Google Fonts 的字体以及任何缺失的库包（HDRI、Kokoro、vcsl / freepats / vsco2ce 示例）。 `FETCH=1` 强制CAD和字体。
- 检查它是否运行：`asr_check.py` 和 `small.en`（两行带有 Whisper 写下的文字：“RP 2040”，“19.05 毫米”），带有真实字体的字幕单行宽度（最宽 552 像素对 1500），`readcheck.mjs`（所有 19 个文本都通过）， `motioncheck.py`（无一帧黑色图块；每秒运动次数）。
- 示范特定的缺陷：v4 板文件是带有分离标签的面板，因此板轮廓是插入 0.4 毫米的 3x6 板轮廓（板的 21 个切口距离开关封装 0.4 毫米，经过测量和校正）； STEP 的情况是 y 朝上，必须翻转并转移到板上（偏移量为 `tools/step2mesh.mjs`），通过四个螺丝孔进行检查；提取时会跳过项目徽标足迹； Kokoro 的声音读起来“RP2040”很糟糕，所以口语文本是“RP 二十四十”。
