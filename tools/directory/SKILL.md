---
name: lemo-opuscar
description: 直接并制作一个完全用代码制作的短影片，采用Lemo-Opuscar库的风格之一（例如Impasto Oil Painting 油画厚涂、Watercolor Brush 水彩笔刷、Ukiyo-e 浮世绘、Satellite Briefing 卫星简报、Exploded Teardown 产品拆解）。当用户请求指定风格的视频、影片、短片、宣传片、解释器或动画（视频、短片、动画、宣传片）时使用，包括由卫星图像、激光扫描、CAD 文件或档案扫描等真实材料构建的解释器（数据解说、科普、产品拆解），以及从真实档案片段和文档剪切的新影片（剪辑与纪实，例如使用档案影像剪成新闻片）；当他们想要关于自己主题的影片且尚未选择风格时（帮助他们选择）；当他们想要将一种风格改为自己的风格时，从空白页面制作自己的风格，或者使用他们保存的风格（改风格、从空白开始、我的风格）；当他们在没有说出自己想要什么的情况下开始技能时；或者当他们询问影片有哪些风格时。不适用于普通编辑、修剪或转换用户现有的视频文件。
---

<a id="lemo-opuscar"></a>
# 莱莫-奥普斯卡

风格、指南和工具随此插件一起提供，位于此文件旁边的 `library/` 中。不会下载任何内容来告诉您要做什么。

1. **准备好库。** 运行`sh "<skill base directory>/scripts/setup.sh"`。它将捆绑的库复制到其工作文件夹（默认为 `~/.lemo-opuscar`，因此安装的软件包在插件更新后仍然存在）并在最后一行打印 `LIB=<path>`。
2. **尽早安装核心工具。** 立即启动 `sh "<skill base directory>/scripts/setup.sh" deps`，如果可以的话在后台启动：第一次需要几分钟。仅当影片需要时才添加 `deps voice` 或 `deps music`（`$LIB/TECHNIQUE.md` §1）。报告一轮问题中缺少的系统工具（Node、ffmpeg、Python）；不要自己安装系统软件。将您自己安装的风格需求（其 `STYLE.md` 列出）打包到项目文件夹中。
3. **按照库进行操作。**阅读 `$LIB/AGENTS.md` 并按照其说明进行操作，从**开始** 开始（`~/lemo-my-styles/` 中用户自己的风格；当他们不写任何内容开始技能时，先是语言问题，然后是方法）：找风格或者自己制作，一轮提问，创作方案，生产发货。

技能模式有哪些变化：

| | |
|---|---|
|项目文件夹|用户启动的文件夹中的 `<name>/`（小写字母、数字、连字符；避免路径中的 `#` 和 `?`）。无论指南中提到 `films/<name>/`，请阅读此文件夹|
|运行工具|来自`$LIB`，项目的绝对路径：`cd "$LIB" && node core/render/still.mjs "<project>" 1.5 3`。 `sh tools/setup.sh` 和 `sh tools/fetch.sh` 也从 `$LIB` 运行|
|页面中的库文件|绝对 URL：`/core/lib.js`、`/node_modules/three/…`（该项目在 `/@film/` 上提供服务）|
|脚本和`build.sh`中的库文件|`$LIB/…`，`LIB=<path>`位于`build.sh`的顶部；从来没有 `../..`|
|示范影片|此版本中没有：没有 `demo/` 源代码，也没有 `poster.jpg`。每个风格的`DEMO.md`（其示范是如何制作的）都在那里；正如指南所说，只有在写入 `TREATMENT.md` 后才阅读它。剪辑与纪实风格需要创作方案之前的材料：您自己查找并记录它，如其 `STYLE.md` 所描述的那样（它命名的 `demo/tools/` 不在本版本中）。 影片在画廊中，如果用户想观看 https://lemomo-ai.github.io/lemo-opuscar/,|
|中文解说|默认Kokoro中文语音（离线）。 edge-tts (`core/tts/tts_zh.py`) 听起来更好，但会将旁白文本发送到 Microsoft 的语音服务：在一轮问题中提供它，并且仅在用户同意的情况下使用它|
|下载量大|仅影片需要的内容，来自 `$LIB/TECHNIQUE.md` §1 列表（npm、PyPI、Playwright 的浏览器、该库的 GitHub 版本、用于语音检查的 Hugging Face）。第一次在一轮问题中说出它们的名字|

提供项目文件夹中 `$LIB/DIRECTOR.md` §11 列出的内容，并告诉用户它在哪里。
