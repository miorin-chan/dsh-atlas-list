# AGENTS.local

本仓库维护列表 Atlas 聚合包。中文界面标题是「列表模块化改良计划」，英文是 `List Modular Improvement Plan`。
卡片元数据同步维护八种语言。

[聚合清单](aggregate.yml)记录成员来源。
列表三态、常驻会话和后台任务侧栏链接到同工作区内的源码，保留本地已在使用的构建。
会话草稿固定 npm 版本。本包使用默认工作区的 `tools/dsh-aggregate` 生成依赖、契约、
`cordis.patch.yml` 与独立运行时入口（`index.js`、`client.js`）。
生成器更新依赖字段与 patch，保留源插件的行 ID 和配置。
成员行为在各自的源码仓库维护。保留成员的独立安装方式，同一 profile 选择一种加载方式。

[用户说明](README.md)与[中文说明](README.zh.md)保持简短。
[项目文档](docs/README.md)记录安装、维护和验证。
变更清单后运行 `npm test` 与工作区脚手架的 `--check`，在一次性 profile 验证整包和成员行启停。
使用 `docs/scripts/reflow md <path>` 重排 Markdown。
保持生成的 [AGENTS.md](AGENTS.md) 与工作区模板一致。
