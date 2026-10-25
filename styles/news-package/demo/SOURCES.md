<a id="sources--broadcast-news-package-demo"></a>
# 来源·广播新闻包示范

此影片不使用第三方镜头或照片。屏幕上的所有内容都是用代码绘制的，除了为早期剪辑生成的两个图板之外。事实及其来源，以及引用的措辞，位于[`FACTS.md`](FACTS.md)。

<a id="data-and-documents-facts-not-creative-works"></a>
## 数据和文件（事实，而非创造性作品）

|什么|在哪里|许可证/状态|用于|
|---|---|---|---|
|KOSPI 每日收市，2026 年 5 月 8 日至 10 月 20 日|韩国交易所指数数据来自 Naver Finance 图表 API，https://api.stock.naver.com/chart/domestic/index/KOSPI?periodType=dayCandle（原始：`data/kospi_raw_naver_api.json`、`data/kospi_raw_naver_mobile.json`；表格：`data/kospi_daily.csv`）|市场数据（事实）；屏幕上注明来源（“KRX DATA VIA NAVER”）|折线图，9月15日至10月15日（19日收盘）|
|Gemini API 变更日志； Gemini最新型号页面； blog.google“双子座 4 氩”|ai.google.dev、博客.google|仅引用事实；未使用任何图像或徽标|故事①|
|韩国先驱报、韩国时报、彭博社（标题 + 摘要）|参见 FACTS.md|仅引用事实|故事②|
|Meta AI 研究博客“Muse Spark Open”（2026 年 10 月 15 日）|研究.meta.ai|仅引用事实|故事④|
|Euronews（Luca Bertuzzi，2026 年 10 月 14 日），仅针对向两家公司提出的请求；欧盟委员会新闻角演讲_26_2150（2026 年 10 月 14 日）|参见 FACTS.md|引用事实；报价卡以字体形式设置了委员会讲话的 7 个单词|故事③|

<a id="picture"></a>
## 图片

|资产|来源|执照|笔记|
|---|---|---|---|
|国家概况（欧洲）|Natural Earth 1:50m Admin 0，来自 world-atlas 2.0.2 `countries-50m.json` (https://cdn.jsdelivr.net/npm/world-atlas@2.0.2/countries-50m.json)，投影为 `tools/prep.py`|公共领域（自然地球）；世界地图集包 ISC|`assets/europe.json`|
|`assets/plates/plate_datacenter.jpg`、`assets/plates/plate_wafer.jpg`（已提交）|Codex CLI image_gen，`tools/gen_plates.sh` 中提示（2026-10-19 生成，保存为 JPEG q88）|AI生成的插图；没有文字、标志、人物或真实地点|由 `tools/prep.py` 将双色调分级为 `assets/plate_*.jpg`（构建输出）；每当屏幕上出现时，都会标记为“ILLUSTRATION / 截图·AI生成画面”。还制作了一个生成的会议厅并省略了：它将被解读为都柏林场地|
|图表、地图、文档、报价卡、规格卡、邮票、LEMO 板|绘制于 `main.js`|—|LEMO AI NEWS是LemoLab的自有品牌|

<a id="sound"></a>
## 声音

|资产|来源|执照|
|---|---|---|
|管弦乐样本|VS 室内乐团：社区版，Versilian Studios / Sam Gossner (github.com/sgossner/VSCO-2-CE)|CC0 1.0|
|打击乐和钟琴样本|Versilian 社区采样音色库 (github.com/sgossner/VCSL)|CC0 1.0|
|拟音|在代码中合成（`core/audio/sfx.py`）|—|
|嗓音|豆宝 TTS 2.0 (Volcengine Seed-tts-2.0)，语音解说小明 2.0 `zh_male_jieshuoxiaoming_uranus_bigtts`，来自 `tools/tts_doubao.py`（您自己的 API 密钥）|Volcengine 服务条款|

<a id="fonts"></a>
## 字体

Noto Sans SC 900/700、Barlow Condensed 800/600/600 斜体、IBM Plex Mono 500 — SIL 开放字体许可证 1.1，来自 `tools/fonts.sh` 的 Google 字体的子集。

<a id="finding-footage-for-your-own-film"></a>
## 为您自己的影片寻找素材

`tools/footage.py`（与其他剪辑与纪实示范中的工具相同）搜索维基共享资源、互联网档案馆和 NASA、下载并将许可证、作者、页面和使用的秒数记录到 `SOURCES.jsonl` / `SOURCES.md` 中。这个示范不需要它；参见 STYLE.md §10。
