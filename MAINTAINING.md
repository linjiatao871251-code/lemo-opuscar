<a id="maintaining-the-library"></a>
# 维护库

**仅适用于存储库所有者。** 如果您正在为用户制作影片，请返回到 [`AGENTS.md`](AGENTS.md)：此处不适用。

<a id="add-a-style"></a>
## 添加风格

使用 `styles/<slug>/`（小写字母、数字、连字符；唯一）。从 `styles/_template/` 中的模板开始。

|文件|它包含什么|
|---|---|
|`style.json`|唯一的元数据源：`slug`、`num`、`en`、`cn`、`category_en`、`category_cn`、`film`、`line`、 `line_cn`、`uses`、`frame_sec`、`dur`|
|`STYLE.md`|仅限该风格的固定约束：外观、材料和渲染、颜色逻辑、类型、运动、镜头语言、声音体系、表现媒介的陷阱、风格特有表现手法、变化范围。没有故事、弧线、节拍表、持续时间或片尾卡。以 `DEMO.md` 的链接结束|
|`DEMO.md`|以“众多例子中的一个为例。不要重复使用它的故事、弧线、镜头、道具或时间安排。”然后是示范的故事和结构、镜头列表、配乐结构、调色板和道具、片尾卡（“LemoLab × Claude Opus 5.5”签名仅存在于此，与库示范一样）、构建注释和代码入口点，以及`content.json` 字段的场景风格|
|`demo/`|源中，提交了一条命令 `build.sh` 和 `CREDITS`，以供代理读取。 `TREATMENT.md`、`PRODUCTION_LOG.md`、字体、音频、纹理和模型保留本地（gitignored）； `CREDITS` 命名每个资产，以便可以再次找到它|
|`demo/stills/`|静态文档链接（`styleframe.jpg` 是图库卡）|
|`<slug>.mp4`、`<slug>.srt`、`poster.jpg`|1080p 影片，其说话时的字幕​​，其海报|

资产仅限 CC0、CC BY 或 OFL，均位于 `demo/CREDITS` 中。 影片上没有水印。真实的人物、品牌和事件仅出现在非官方粉丝影片中；它的 `DEMO.md` 是这么说的。

仅适用于库示范的规则（用户的影片遵循 `DIRECTOR.md`，而不是这些）：

- **双语字幕，每种语言各一行。** 每个cue有中文一行和英文一行，不换行。当一行太长时，将其分成两个提示。
- **比较在判决前保持不变。** 当影片比较选项（四座桥梁，三个平面图）时，每个选项都完全在框架中，并在判断之前保持至少 2.5 秒，以便观看者可以阅读。

<a id="register"></a>
## 登记

1. **编号。** `style.json` 中的 `num` 是 `styles/*/style.json` 中最高值之后的下一个空闲号码（两个数字作为字符串，例如 `"55"`）；它对画廊进行排序。
2. `python3 styleboard/build.py` 读取每个 `styles/*/style.json` 并重写 `README.md`（英文）和 `README.zh-CN.md`（中文）中的图库数据、网格和计数、`styles/README.md` 以及 `AGENTS.md` 中的风格列表。切勿手动编辑这些生成的部分。两个自述文件的其余部分是手写的：一起更改两者（例如 **新的** 行）。然后是 `python3 styleboard/build.py --frames <slug>`（`frame_sec` 的自述文件网格框架）和 `sh styleboard/frames.sh <slug>`（`demo/stills/styleframe.jpg` 的图库卡）。
3. `sh tools/web_cuts.sh` 在 `.release/web/` 中进行 720p 卷筒纸剪切（仅适用于新的或更改的影片）。

<a id="gates"></a>
## 检查关卡

- **人：**在生产前批准风格定帧，以及成品影片。
- **机器：** `asr_check.py`在每条线上通过； `mux.sh` 报告大约 -14 LUFS 并且没有警告； `readcheck.mjs` 通过； `python3 tools/release.py check --strict <slug>` 是干净的（它需要上面的注册步骤）。它还会停止 `styles/` 下没有提交文件名（按名称或模式）的图像、从风格条目（STYLE.md、DEMO.md、build.sh、index.html…）加载的示范文件，并处理措辞（`PRODUCTION_LOG`，审阅注释；脚本中的列表为 `PROCESS_WORDS`）在任何提交的文本中。
- **真实事件和产品：** 屏幕上和画外音中的每个事实均来自官方来源，保存在 `demo/FACTS.md` 中（声明、URL、引用的措辞）；在最后一次渲染之前检查最终脚本。

<a id="publish"></a>
## 发布

1. `sh tools/publish.sh` 上传完整的影片（`films` 版本）和 720p 网络剪辑（`web` 版本，由画廊使用），然后验证它们。 Per-示范资源包不再发布。
2. `git status --short`、`git add -A`，提交。
3. 推送 `main`，然后观看 CI (`gh run watch`)：当卡片链接不在 `web` 版本上的影片时，图库构建会失败。

页面构建 (`build.py --site`) 还写入 OPUSCAR 98 页面（`opuscar98/`，来自 `styleboard/opuscar98.html`）、`llms.txt` 和 `sitemap.xml`，并将规范链接、共享卡标签和 JSON-LD（上游存储库和作者）放入每个页面的头部。他们自己挑选风格数量； 影片的运行时间是 `build.py` 中的 `FEATURE['dur']`。

在上传完成之前不要推送，并且不要从失败的运行中提交 `tools/assets.json`。

<a id="revise-a-style"></a>
## 修改风格

首先备份（旧版本移出存储库，而不是移入 git）。重新渲染，替换 `<slug>.mp4`，然后运行 ​​`sh tools/publish.sh`：它会重新上传影片并刷新其网页剪切。

<a id="directory-edition"></a>
## 目录版

Claude 插件目录列出了孤立分支 `directory` 上插件的独立构建（提交跟踪该分支；`main` 保留访问者看到的内容）。它携带指南，每个 `STYLE.md` / `style.json` / `DEMO.md`、`core/`（不含 Poly Haven 型号，仅示范代码使用）及其自己的 `README.md`、`SECURITY.md` 和`SKILL.md`：不会克隆或获取任何内容来告诉代理要做什么，没有示范源，并且仅在用户同意的情况下才使用中文边缘 tts 旁白。仅插件文件的来源位于 `tools/directory/` 中；构建及其检查（文件大小、个人信息）位于 `tools/directory.py` 中。

在 `main` 上发布后（新风格、更改的指南或工具）：

1. `git worktree add ../lemo-opuscar-directory directory`（一次；之后重复使用）。
2. `python3 tools/directory.py <version> --into ../lemo-opuscar-directory`，其版本高于分支当前的 `.claude-plugin/plugin.json`（新风格或功能：1.1.0；仅修复：1.0.1）。该目录将每个版本号视为一个版本，因此脚本拒绝相同或较低的版本； `--same-version` 仅用于修复从未发布的版本。当指南更改太多以至于其中一项编辑不再适用时，它也会停止：更新脚本中的 `EDITS`。
3. `claude plugin validate ../lemo-opuscar-directory`，然后在那里提交（`Lemo-Opuscar <version>, plugin directory edition`）并推送`directory`。该目录扫描每个推送并发布新版本。
