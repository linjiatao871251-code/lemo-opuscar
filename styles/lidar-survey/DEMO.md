<a id="lidar-survey--our-demo"></a>
# LiDAR 测量 — 我们的示范

众多例子中的一个。请勿重复使用其故事、弧线、镜头、道具或时间安排。

示范：*森林下的田地*《林下的田》（40.0秒）·`lidar-survey.mp4`·来源于[`demo/`](demo/)

从空中看，康涅狄格州阿什福德的一小片地方只是森林。激光测量将照片变成点，切割机将树冠层层剥离，剩下的地面凝结成一个有石墙的表面：这里的农场田野系统，在 0.74 平方公里的土地上追踪了 3.4 公里的墙。一堵墙被切割并测量；该镇的历史有两个方面：森林在墙外重新生长。中文屏幕，英文旁白，双语字幕（中文上行，英文下行）。这是由公共领域调查数据和图像制作的非官方影片；美国地质调查局、美国农业部和阿什福德镇并未制定或认可该计划。

<a id="story--structure"></a>
## 故事与结构

梗概：从空中看，这只是森林；除去击中树木的每一次回击，地面仍然保留着田野的墙壁。

弧线：索赔（2016 年 7 月的航拍照片，除了树冠）→ 表现媒介变化（扫描线将照片变成 2016 年春季激光雷达云；27.6% 的回波到达地面）→ 果皮（水平面按节拍下降 30 → 0 m，返回到其上方升起并发光，带有树冠高度直方图的标尺跟踪它）→ 近乎沉默裸露地面返回→转弯（第二次扫描将地面返回到倾斜照明的表面；撞击）→随着摄影机的上升，墙壁相继亮起→测量（追踪3.4公里；从1,451个原始地面返回穿过一堵墙的部分：0.56 m高，半高2.5 m宽）→历史（Ashford 1870：清除67.3 km²农田；2006 年：80.2 平方公里森林）→ 森林在发光的墙壁上像幽灵一样重新生长； 片尾卡。

风格特有表现手法花费：*开场时拍照打分*； *冠层皮*为标志性镜头； *转弯时积分凝聚*； *详细信息部分*； *窗户*（作为暗淡、未剥落的云层内的舞台的调查区域）贯穿始终； *再生*作为结局。

每个数字及其来源都在[`demo/FACTS.md`](demo/FACTS.md)中；测量值在屏幕上标记为测量值或追踪值。

<a id="shots"></a>
## 镜头

一个连续的摄影机（目标、距离、航向、俯仰随时间变化的 C1 样条线）。时间以秒为单位。

|#|时间|镜头|摄影机|风格特有表现手法/注|
|---|---|---|---|---|
|1|0.0–3.75|NAIP 2016 年 7 月在树冠表面拍摄的照片，北向上； label 2016年7月·夏季航拍|最低点，推 480 → 395 m，转 6°|索赔，保持足够静止，可以作为照片阅读|
|2|3.75–6.9|扫描线从左→右交叉；照片后面是点云（颜色=离地高度）|起重机向下，倾斜最低点 → 44°|照片到点；在线上噼啪作响|
|3|6.9–10.0|云；阅读打到地面的回波 27.6 % (land 7.5)|起重机向下倾斜，105 m，15° 俯仰|冠层作为地面以上的一层返回|
|4|10.0–13.1|**签名**：30、24、18、12、6、0 m处的切割平面，每拍一步；返回上方升空并发光；标尺 + 右边缘的直方图|慢轨道 +12°, 92–105 m|树冠皮；刻度线划分，每层一个下降的光点|
|5|13.1–14.4|仅留下地面返回，扫描图案的灰色条纹|轨道继续|接近沉默|
|6|14.4–15.9|第二次扫描将地面返回的图像凝结到地表（局部地形×2，从西北方向掠过太阳）|向后拉 100 → 170 m|点凝结；影响|
|7|15.6–20.0|22 面追踪墙沿网络依次亮起，波峰上有琥珀色的发际线|上升回拉至 480 m, 48°|现场系统规模揭示|
|8|20.0–24.4|阅读已描出的石墙 3.4 km (rolls 20.0–20.6), 22 段|漂移，航向 12° → −12°|保持 3.75 秒|
|9|24.4–28.75|推向墙C；一条剖面线在其上发光； 1,451 个原始地面回波的图表（垂直 ×5），中值轮廓和尺寸为 0.56 m / 2.5 m|推力 230 → 88 m，俯仰角 34° → 21°，蠕变|该部分|
|10|28.75–35.6|吊起；卡 1870 · 67.3 km² 开垦为农田 (29.4)，卡 2006 · 80.2 km² 为森林 (32.5)，禁止城镇约 100 km²|起重机向上和返回 470 m，56°|卡片下方的表面稍微变暗|
|11|33.75–40.0|树冠从地面重新生长为微弱的附加幽灵；墙壁会发光； 片尾卡 35.9起|缓慢上升 470 → 560 m|再生|

<a id="score-structure"></a>
## 配乐结构

96 BPM，4/4（节拍 0.625 秒）；每个图片提示为一个节拍或半节拍（`demo/tools/cuecheck.py`：17 个提示为 0 毫秒）。 D小调干上半场，F大调起转。

|部分|时间|调色板|笔记|
|---|---|---|---|
|天篷|0–3.75|森林床（过滤树叶中的风、阵风、合成的两音鸟叫声）、Dm 垫| |
|激光|3.75–10|FM 在 8 分频处闪烁 (D5 A5 F5 A5 …)，扫描频率 700 → 3800 Hz，带有细裂纹，脉冲低音 D2/C2 从 5.0 到 8 分频|森林床淡出 5.2|
|果皮|10–13.1|滴答声第 8 秒→第 16 秒→第 32 秒，每层 1 个 FM ping D6 A5 F5 D5 A4，向上闪烁扫描|细分加速|
|沉默|13.1–14.4|仅气床（低于计划中值−22 dB），与 13.4 相比噪音激增相反| |
|转动|14.4|低音鼓 + Gran cassa + 定音鼓 F2，沉稳的扫频；弓电颤琴 A4/E5|-16 dB 下降后，最大声时刻下为 -1.9 dB|
|墙壁|15.6–20|F大调五声音阶半拍马林巴琴；打击垫 F–Dm–B♭–C，脉冲低音返回|单一的木质音色|
|措施|20–28.75|3.4 滚动时棘轮发出咔嗒声，着陆时对 C6 发出 ping 声；吸出 24.1–24.4，扫频 + 定音鼓 D2 + 低音鼓切入，Ping A5 读数| |
|历史|28.75–35.6|每个小节上升正弦滑行，马林巴琴落地| |
|结尾|33.75–40|用于再生的谷物；林床 J 形切割从 34.4 开始； F大调和弦（马林巴、打击垫、弓弦颤音器、软定音鼓）| |

混音（在 `mix.py` 中）：音乐在声音下方 −10 dB，在说话、脉冲、拟音和下面的床时降低约 5 dB；仅对音乐、脉冲、拟音和床进行总线压缩；低音高通频率为 38 Hz（命中时为 46 Hz），低于 62 Hz 的范围为 -5 dB；主级至-14.4 LUFS，并具有-4.6 dBTP 的真实峰值限制器，因此 `mux.sh` 保持线性。 影片的测量结果为 −14.0 LUFS，峰值为 −3.9 dBFS，LRA 2.4 LU（`demo/tools/audiocheck.py` 用于冲击和静音）。

<a id="palette--props"></a>
## 调色板和道具

- 背景#05080A；冠层坡道 #1F3F35 → #5C9A7A → #E2F3DC 按离地高度 (0–28 m)、强度值；地面返回#C8B38C；表面 #BDB5A6 从方位角 315°、向上 26° 照亮；前线#D4FFF0；口音#FFB347（墙壁、阅读材料、部分）；绿色图表#83C495。
- 道具：2016 年 NAIP 照片，覆盖在 1 m 的天篷表面； 4,789,797 次退货； 0.5 m 地面模型； 22 堵墙在当地浮雕模型上手工绘制并捕捉到顶部（`demo/data/walls_traced.json` → `walls.json`）；墙 C 的横截面 (`data/profile_C.json`)。
- 调查窗口：x < 235 m（其东边是碎石巷和房屋，保留为暗淡未剥皮点）。
- 旁白：Kokoro `bm_george`，速度1.0。

<a id="end-card"></a>
## 端卡

当树冠重新生长时，在昏暗的田野系统上留下第三个：林下的田（Noto Sans SC 500），*森林下的田野*，短琥珀尺，`LIDAR SURVEY · 点云测绘`，`LemoLab × Claude Opus 5.5`。 4.1 秒。 “LemoLab × Claude Opus 5.5”签名仅属于该库的示范；用户的影片没有 LemoLab 积分，也没有该卡的副本。

<a id="build-notes"></a>
## 构建笔记

```
demo/
  build.sh          one command: (data) → voice → speech check → cues → events → video → mix → master → .srt → checks → poster
  index.html        two canvases (WebGL scene, 2D overlay), fonts
  film.js           render(t): points / surface / photo shaders, camera spline, fronts, cutting plane, overlay, subtitles, EV
  timeline.js       beats, cues, peel steps, narration, camera keys (single source; tools/export.mjs → timeline.json, cues.json, voice/lines.json)
  mix.py            score, foley, beds, voice, mix → out/mix.wav + out/stems/
  data/             walls_traced.json (hand tracing), walls.json, profile_C.json, facts.json (all on-screen numbers)
  tools/            fetch_ept.py, terrain.py, load.py, walls.py, trace.py, profile.py, build_data.py, fetch_naip.py, fonts.py,
                    scout_dem.py (finding the site); export.mjs (voice/cues); cuecheck.py, subcheck.mjs, audiocheck.py, motioncheck.py (checks)
  assets/raw/       ept/ (EPT nodes), work/ (DTM, relief), build/ (points.bin, ground.bin, canopy.bin, naip.jpg), fonts/, .venv (laspy, lazrs, scikit-image)
  FACTS.md, CREDITS, stills/styleframe.jpg
```

- `sh demo/build.sh` 在 Apple 芯片上大约需要 5 分钟（图像在 3 名工作人员的情况下在大约 30 秒内渲染；Kokoro 和 Whisper 检查占用了剩下的大部分时间）。在没有数据或 `FETCH=1` 的情况下，它首先获取并构建数据（约 3 分钟，`assets/raw/` 中约 350 MB）。
- 字体（Barlow Condensed、IBM Plex Mono、Noto Sans SC）不在 git 中：`tools/fonts.py` 在丢失时从 github.com/google/fonts 获取它们，并对 CJK 字体进行子集化。数据工具在 build.sh 创建的私有 venv（`assets/raw/.venv`：laspy、lazrs、scikit-image、fonttools）中运行。
- 检查其运行情况：`asr_check.py` 与 `small.en`（0 个不匹配）、真实语音持续时间的提示重叠、提示网格、字幕单行宽度与真实字体（最宽 595 像素对 1100 像素）、`readcheck.mjs`、每秒运动（没有平坦拉伸 > 1 秒，没有类似剪切的跳跃）。
- 资料说明：EPT副本为Web Mercator；所有内容均转换为北纬 41.8875°、西经 72.1960° 附近的本地公制框架。提供商的 1 类混合了植被和建筑物；地面上方的低矮植被在 0 m 处的切割中仍能幸存，因此平面在 -6 m 处结束。地面模型是在 0.5 m 处从 2 级回波 (1.3 M) 进行三角测量。
- 示范特有的陷阱：从超过 ~150 m 处看去的落叶冠层就像是平坦的地毯，因此果皮镜头低且紧密；东北的池塘没有回报（窗外的黑洞）；地面回波的规则扫描线条纹在掠射角处最强；第二次扫描必须在帧外开始，否则第一帧会跳转。
