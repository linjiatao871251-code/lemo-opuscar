<a id="sources"></a>
# 来源

由 `footage.py md` 从 SOURCES.jsonl 生成。这里列出了影片中使用的每一段素材。

|姓名|标题/作者/日期|执照|源页面|规格|使用秒数|
|---|---|---|---|---|---|
|大学|特别发行 - 齐柏林飞艇爆炸导致死亡，1937/05/10 / 1937|http://creativecommons.org/licenses/publicdomain/|https://archive.org/details/1937-05-10_Special_Release_Zeppelin_Explodes|720×480 180.0秒|src 38.0–41.6 秒纽约上空 → 开放 2.4–6.3 秒； src 59.4–67.1 s 进场镜头 → 位置 14.6–18.6 s； src 78.6–104.4 s 连续开火镜头 → 冷开倒带 2.0–2.4 s，32 秒 33.6–36.5 s（以约 9 倍擦洗）； src 80.2 freeze → 0.0–2.0 s，燃点 24.4–31.8 s，结论图，片尾卡； src 103.6 冻结 → 36.5–38.6 秒；源音频 src 78.10–81.56 → 24.4–27.9 秒，src 40.38–44.72 → 46.0–50.3 秒|
|联邦调查局01|兴登堡/联邦调查局|http://creativecommons.org/publicdomain/mark/1.0/|https://archive.org/details/HindenburgFBI|×|p.39（Tyler 中尉的声明）→ 冷开 0.6–2.4 秒，点火点 24.0–31.8 秒，结论图，片尾卡；第13页（电传1937-05-08）→调查38.6–45.6秒|
|NH57973|美国海军/海军历史和遗产司令部 NH 57973|公共领域（美国海军，NHHC NH 57973）|https://commons.wikimedia.org/wiki/File:NH_57973_Airship_HINDENBURG_Disaster,_6_May_1937.png|3840×3093|32秒（≈T+26秒，与新闻片中船舶的姿态相匹配）|
|帕斯克|格斯·帕斯夸雷拉 (Gus Pasquarella)，美国海军，莱克赫斯特海军航空站，1937 年 5 月 6 日|公共领域（美国海军照片）|https://commons.wikimedia.org/wiki/File:Hindenburg_burning,_1937.jpg|3840×2899 0.0秒|冷开0.9-2.4秒；燃点24.8-31.8秒；三十二秒（≈T+2秒）；结论图； 片尾卡|
|奈良518856|美国海军莱克赫斯特海军航空站；国家档案馆 (NAID 518856)|公共领域（美国海军/NARA 518856，美国联邦政府工作）|https://commons.wikimedia.org/wiki/File:German_airship_%22Hindenburg%22_at_Lakehurst,_New_Jersey._-_NARA_-_518856.jpg|2948×2327 0.0秒|位置 13.0–18.6 s（仅船头和系泊桅杆）|
|美国地质勘探局1947|美国地质调查局，新泽西州莱克赫斯特 1:24,000 四边形，1947 年|公共领域（USGS、美国联邦政府工作）|https://ngmdb.usgs.gov/topoview/|×|位置 12.3–14.8 秒（地图推入），平面图定位器插图 14.8–18.6 秒，最终卡缩略图|

USGS四边形下载地址：https://prd-tnm.s3.amazonaws.com/StagedProducts/Maps/HistoricalTopo/PDF/NJ/24000/NJ_Lakehurst_254519_1947_24000_geo.pdf（国家地图历史地形图，四边形ID 254519）。
国家档案馆目录条目 NARA 518856：https://catalog.archives.gov/id/518856。 Commons 给出的日期为 1937 年 1 月 25 日，这一天兴登堡号不在美国； 影片没有给出日期，只标记为“彼此一次停靠”（“较早的停泊处”）。

<a id="quoted-text-no-file-downloaded"></a>
## 引用的文本（未下载文件）

|什么|来源|执照|用于|
|---|---|---|---|
|美国商务部，《飞艇“兴登堡”号事故调查报告》，航空商务公报第 1 卷。 9 没有。 1937 年 8 月 15 日 2 日（由 South Trimble Jr.、R. W. Schroeder、Denis Mulligan 签名）|文字转录：https://www.airships.net/?p=2041； LibriVox阅读（同文）https://librivox.org/report-of-the-airship-hindenburg-accident-investigation-by-united-states-department-of-commerce|美国联邦政府工作，公共领域|四条无线电消息的措辞和时间、雷暴和地面风、18:15 接近/18:21 绳索掉落/30°/≥700 英尺、沃德的证词、点火点、32 秒、原因和“刷状放电最有可能”、没有破坏证据、伤亡数字|

<a id="material-not-downloaded"></a>
## 材料未下载

|什么|来源|执照|
|---|---|---|
|字体 Noto Sans SC、Noto Serif SC、IBM Plex Mono、Source Serif 4|Google 字体，影片 (tools/fonts.py) 中使用的字符的子集|SIL OFL 1.1|
|英语旁白|Kokoro-82M（core/tts/tts.py，声音 am_michael）|阿帕奇-2.0|
|配乐样品|VS 室内乐团：社区版，Versilian 社区采样音色库 (core/audio/sampler.py)|CC0 1.0|
|音效|在 numpy 中合成（audio/mix.py）|专为这款影片打造|

已检查但未使用：赫斯特每日新闻（NARA 342-USAF-18247，商业新闻片，许可不清楚）、英国百代和各种 YouTube/stock 镜像、Periscope 影片、Prelinger 的《兴登堡爆炸》（制作者未知）、美联社 / INS / Wide World 机构照片（Commons 将它们标记为 PD，但以“未更新”为由，这是不确定），Herb Morrison 的 WLS 无线电录音（录音版权不明）。
