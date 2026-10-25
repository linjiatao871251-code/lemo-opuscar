---
name: lemo-opuscar
description: 围绕用户主题，使用 Lemo-Opuscar 风格库中的风格，执导并制作以代码绘制和渲染的短片，例如油画厚涂、水彩笔刷、浮世绘、卫星简报或产品拆解。适用于视频、短片、宣传片、解说与动画制作；也适用于基于卫星影像、激光扫描、CAD、档案扫描、真实影像和文件的实证影像或剪辑与纪实影片。用户尚未选定风格时帮助选择；用户想改编风格、从零设计风格、使用已保存风格、查询风格列表或仅启动技能时也适用。不用于对用户现有视频进行普通剪辑、裁切或格式转换。
---

# Lemo-Opuscar：代码短片制作

风格、指南与工具位于 Lemo-Opuscar 库（github.com/lemomo-ai/lemo-opuscar）。本技能负责获取该库，再按库中的指南执行制作流程。

本分支提供中文文档。使用本分支时，先设置 `LEMO_OPUSCAR_REPO=https://github.com/linjiatao871251-code/lemo-opuscar.git`，再执行下列安装命令，确保获取的是中文工具库。

1. **获取工具库。** 运行 `sh "<skill base directory>/scripts/setup.sh"`。脚本会克隆或更新工具库，默认位置为 `~/lemo-opuscar`；如果用户当前已位于一个克隆中，则直接使用它。脚本最后一行输出 `LIB=<path>`。
2. **尽早安装核心依赖。** 立即运行 `sh "<skill base directory>/scripts/setup.sh" deps`，条件允许时放到后台；首次安装需要几分钟。只有影片需要配音或配乐时，才追加 `deps voice` 或 `deps music`（见 `$LIB/TECHNIQUE.md` §1）。把缺少的系统工具（Node、ffmpeg、Python）列入唯一一轮需求提问，不自行安装系统软件。风格专用依赖见其 `STYLE.md`，由你安装到项目文件夹中。
3. **遵循工具库指南。** 阅读 `$LIB/AGENTS.md`，从“开始”一节执行：先查 `~/lemo-my-styles/` 中的自有风格；用户仅启动技能时，先问语言，再介绍入口。随后选择或创建风格，一次性确认需求，编写创作方案，完成制作与交付。

技能模式下的路径与操作规则：

| 项目 | 规则 |
|---|---|
| 项目文件夹 | 在用户启动技能的文件夹中创建 `<name>/`。名称仅使用小写字母、数字和连字符，路径避免 `#`、`?`。指南中的 `films/<name>/` 均指此文件夹。 |
| 运行工具 | 在 `$LIB` 下运行，并传入项目绝对路径，例如 `cd "$LIB" && node core/render/still.mjs "<project>" 1.5 3`。 |
| 页面引用库文件 | 使用绝对 URL，例如 `/core/lib.js`、`/node_modules/three/…`；项目通过 `/@film/` 提供访问。 |
| 脚本和 `build.sh` 引用库文件 | 使用 `$LIB/…`，在 `build.sh` 顶部设置 `LIB=<path>`；不得使用 `../..`。 |
| 示范源码 | 默认不下载。先完成 `TREATMENT.md`，再运行 `sh "<skill base directory>/scripts/setup.sh" demo <slug>` 获取源码，仅用于学习技术，不用于直接渲染交付。剪辑与纪实类是例外：可在创作方案之前获取其素材工具，按 `STYLE.md` 指定使用 `demo/tools/`；详见 `$LIB/AGENTS.md` 的“先写创作方案，再看示范”。 |

按 `$LIB/DIRECTOR.md` §11 的要求，将交付内容放在项目文件夹中，并告知用户位置。
