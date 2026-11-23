# AGENTS.local

本仓库维护运行时 Atlas 聚合包。中文界面标题是「运行时模块化改良计划」，英文是 `Runtime Modular Improvement Plan`。
卡片元数据同步维护八种语言。

[聚合清单](aggregate.yml)记录成员的固定 npm 版本。
[scripts/aggregate/](scripts/aggregate/) 由默认工作区的 `tools/dsh-aggregate` 同步。
生成器更新依赖字段与 patch，保留源插件的行 ID 和配置。
成员行为在各自的源码仓库维护。保留成员的独立安装方式，同一 profile 选择一种加载方式。

[用户说明](README.md)与[中文说明](README.zh.md)保持简短。
[项目文档](docs/README.md)记录安装、维护和验证。
变更清单后运行 `npm test` 与工作区脚手架的 `--check`，在一次性 profile 验证整包和成员行启停。
使用 `docs/scripts/reflow md <path>` 重排 Markdown。
保持生成的 [AGENTS.md](AGENTS.md) 与工作区模板一致。
