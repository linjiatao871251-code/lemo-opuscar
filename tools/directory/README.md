<a id="lemo-opuscar"></a>
# 莱莫-奥普斯卡

**{STYLES} 影片风格，每个风格都有一个完全由代码制成的短影片。**<br>
{STYLES}一种影片风格，多数都配了一批完全用代码制作来的短片。

选择一种风格，带来您自己的故事，然后让 Claude 执导影片。 Claude 编写创作方案，用代码绘制每一帧，编写原始配乐，混合声音并渲染完成的 MP4。没有视频模型，没有素材库。

这是插件目录版本（版本{VERSION}）：指南，{STYLES}风格提示和渲染工具，没有示范影片。 **影片、图库和最新风格位于主存储库中： [github.com/lemomo-ai/lemo-opuscar](https://github.com/lemomo-ai/lemo-opuscar).** 观看每个示范影片 [图库](https://lemomo-ai.github.io/lemo-opuscar/)。

<a id="try-it"></a>
## 尝试一下

从 Claude 插件目录安装插件。 （带有示范源的完整版本从主存储库安装：`claude plugin marketplace add lemomo-ai/lemo-opuscar`，然后是 `claude plugin install lemo-opuscar@lemolab`。使用其中之一。）

在影片的文件夹中打开 Claude Code，然后询问：

> 制作一个关于我家咖啡农场的 45 秒水彩画影片。温暖的女解说。

> 根据公共激光扫描数据，对我们镇后面的旧采石场进行 40 秒激光雷达测量影片。

> 制作一个 30 秒的白板解释，介绍疫苗如何训练免疫系统。

> 影片有哪些风格？我想要一些用于产品发布会的东西。

> 我想将浮世绘风格改为我自己的版本。

> 我想从头开始创造自己的风格：黑板上的粉笔，温暖而缓慢。

用英语或中文命名一种风格，或者描述您的主题，然后让克劳德建议两种或三种。克劳德预先问你一次：关于你的主题的任何事情它都无法决定，你是否有自己的声音、音乐或照片，以及你是否想先看故事板。然后它会在您开始的项目文件夹中生成影片 。

要创建自己的风格，请更改库风格或从空白页开始：Claude 一次与您计划一个问题（每个问题都有一个推荐答案），向您展示风格定帧，制作 15-30 秒的示范影片，并保留风格，以及影片的源代码， `~/lemo-my-styles/<name>/`（在插件之外，因此更新永远不会触及它）。之后，像其他风格一样命名您的风格；无需请求即可启动技能，并且首先列出您自己的风格。

<a id="before-you-start"></a>
## 开始之前

- **Claude 在您自己的计算机上编写代码。** 该插件使用本地工具渲染视频，因此它需要一个 shell：它不在 claude.ai 聊天中运行。
- **Node 20+、ffmpeg 和 Python 3.11+**（或 [uv](https://docs.astral.sh/uv/)）。你安装这些；如果有人失踪，克劳德会告诉你。
- 影片大约需要 30-60 分钟和相当数量的代币。默认输出1920×1080，24帧；其他尺寸可按要求提供。
- 风格针对 Claude Opus 5.5 进行了调整；其他型号可能无法重现它们。

<a id="what-it-downloads"></a>
## 它下载什么

该库包含在插件内。第一次使用时，它会被复制到 `~/.lemo-opuscar`（将 `LEMO_OPUSCAR_HOME` 设置为另一个文件夹），并且软件包安装在那里，因此它们可以在插件更新中生存。系统范围内没有安装任何内容。 Claude 仅下载您的影片需要的内容：

|什么|从|什么时候|尺寸|
|---|---|---|---|
|节点包：`playwright-core`、`three`|新项目管理|第一个影片|〜10MB|
|用于逐帧渲染的 Headless Chromium|剧作家的下载服务器（微软）|第一个影片|约 100–200 MB|
|Python 包：numpy、scipy、soundfile、soxr、pillow|皮伊|第一个影片|〜150MB|
|语音层：kokoro-onnx、edge-tts、faster-whisper|皮伊|仅适用于带旁白的影片|约200MB|
|Kokoro语音模型（离线TTS）|该项目的[GitHub发布](https://github.com/lemomo-ai/lemo-opuscar/releases/tag/assets)|仅适用于带旁白的影片|354MB|
|用于语音检查的 Whisper 模型|拥抱脸（或者你在`HF_ENDPOINT`中设置的镜子）|第一次叙述检查|~145 MB（英文），~480 MB（中文）|
|numba，用于拨弦|皮伊|仅当配乐使用它们时|〜140MB|
|仪器采样音色库（VSCO 2 CE、VCSL、FreePats、Karoryfer、Salamander）|该项目的 GitHub 版本|仅配乐使用的库|每个 70–400 MB|
|适用于 3D 风格的 HDRI（Poly Haven、CC0）|该项目的 GitHub 版本|仅适用于 3D 风格|12MB|
|胡桃木贴面纹理（Poly Haven，CC0）|该项目的 GitHub 版本|仅适用于数据物理化风格|7MB|
|按风格命名的字体（Google Fonts、OFL）|谷歌字体|当风格需要它们时|小的|
|在其 `STYLE.md` 中打包风格列表（例如 LiDAR 读取器）|npm 或 PyPI，进入您的项目文件夹|只适合那种风格|各不相同|
|证据影片风格的公共数据（卫星图像、激光扫描、开放城市数据）|克劳德为您的主题找到的开放数据源；它会告诉您每个来源和许可证|仅当您要求这样的影片时|各不相同|

<a id="privacy-and-outside-services"></a>
## 隐私和外部服务

- 您的主题、您的文件和影片保留在您的计算机上。该插件不收集任何内容，也不向我们发送任何内容。
- **中文旁白：**默认离线心语音。更好的中文声音来自微软的在线语音服务（edge-tts），该服务接收旁白文本；克劳德在使用前会询问并只有在您同意的情况下才使用。英语旁白始终离线（Kokoro）。
- 以上下载仅请求文件；他们不会发送您的内容。 影片中的每个第三方资产（字体、样本、数据）均在影片的 `CREDITS` 中列出其许可证。

<a id="licence"></a>
## 执照

麻省理工学院。 `core/fonts/` 中的字体为 OFL； 采样音色库和 HDRI 保留自己的许可证（在 `core/audio/INSTRUMENTS.md` 和 `core/assets/polyhaven/SOURCES.md` 中列出）。您对放入影片中的材料负责。

由 LemoLab·Lemomo ([@lemomo_ai](https://x.com/lemomo_ai)) 制作。问题或想法：​​[open an issues](https://github.com/lemomo-ai/lemo-opuscar/issues) 在主存储库中。
