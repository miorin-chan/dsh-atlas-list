# 运行时 Atlas 开发与验证

[中文使用说明](../README.zh.md) · [English guide](../README.md)

## 安装与启停

本包适用于 DeepSeek Harness `0.2.2-rc.5`。
在同一工作区使用 Node.js 22.18 或更新版本准备成员和运行时 Atlas。
从默认工作区根目录执行下列命令，再从「插件 → 添加插件」选择运行时 Atlas 的目录。

```sh
npm --prefix plugins/dsh-undo-unsent ci
pnpm --dir plugins/dsh-aggressive-sidebar install --frozen-lockfile
pnpm --dir plugins/dsh-atlas-runtime install --frozen-lockfile
```

「后台任务侧栏」「君子未言」「激进侧边栏」各有开关。
启用激进侧边栏后，同一详情页显示「展开模式」。
成员共用之前独立安装的条目 ID，迁移时先停用独立 bundle，再启用聚合版，以便沿用逐项开关和已保存的模式。
移除独立安装可以从插件页收起原先的卡片。

## 生成与发布

[聚合清单](../aggregate.yml)固定后台任务侧栏的 npm 版本，用本地 `link:` 引入君子未言和激进侧边栏。
包内生成器读取成员 patch，更新 `package.json` 的聚合字段与 `cordis.patch.yml`。
更新清单后安装依赖，再运行 `npm test` 和 `npm run check`。
提交锁文件与生成结果。

发布版需要将两个本地成员改为可从 npm 安装的固定版本。
`npm run prepublishOnly` 核对这项要求和已安装依赖，通过后可用 `npm pack --dry-run --json` 核对包内文件。

在默认工作区还可运行脚手架校验：

```sh
node tools/new-dsh-plugin/cli.mts --check plugins/dsh-atlas-runtime
```

## 一次性 profile 验证

在一次性 profile 安装聚合包，检查三个成员的条目各出现一次。
在插件页逐项启停，确认其他成员仍可用。在详情页改变展开模式，刷新后检查保存的值。
单独停用激进侧边栏时，页面应收起模式选择。从独立版迁入后检查展开模式是否沿用。
关闭再开启整包时，成员开关应沿用之前的状态。

测试后台任务时，用一个会话任务和一个共享任务检查计数变化，并点击会话任务返回所属会话。

2026-11-23 用 DSH `0.2.2-rc.5` 和 Chrome 验证了迁移。
独立安装时选择「全屏」，刷新确认保存后移除独立 bundle，再安装运行时 Atlas。
聚合详情页只显示一个模式控件，保留「全屏」。分别启停两个新成员时，后台任务侧栏保持启用。
关闭激进侧边栏时控件消失，重新开启后仍为「全屏」。
在聚合详情页改回「展开到左边栏」，刷新后选择仍有效。

## Local development

Use Node.js 22.18 or newer. Build the two linked members with the commands in the installation section,
then run `pnpm install --frozen-lockfile`, `npm test`, and `npm run check` from this checkout.
Disable any standalone copies of the three members before enabling the bundle.
Choose the prepared directory in **Plugins → Add plugin** for local UI testing.
