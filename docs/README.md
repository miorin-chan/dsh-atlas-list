# 运行时 Atlas 开发与验证

[中文使用说明](../README.zh.md) · [English guide](../README.md)

## 安装与启停

本包适用于 DeepSeek Harness `0.2.2-rc.5`。
通过总 Atlas 开启运行时成员后，「运行时模块化改良计划」卡片会出现「后台任务侧栏」的独立开关。
在左侧边栏展开时，任务区位于账号控件上方。

独立的后台任务侧栏与本包共用 `dsh-background-jobs-sidebar` 行 ID。
切换到运行时 Atlas 前，先停用独立 bundle。

## 生成与发布

[聚合清单](../aggregate.yml)固定成员的 npm 版本。
包内生成器从该版本读取 patch，更新 `package.json` 的聚合字段与 `cordis.patch.yml`。
从干净检出用 Node.js 22.18 或更新版本运行：

```sh
pnpm install --frozen-lockfile
npm test
npm run check
npm run prepublishOnly
npm pack --dry-run --json
```

更新成员时先发布源插件，编辑 `aggregate.yml`，安装其固定版本并运行 `npm run build`。
提交锁文件与生成结果。`prepublishOnly` 核对本次安装的依赖来自检出目录内的注册表依赖树。

在默认工作区还可运行脚手架校验：

```sh
node tools/new-dsh-plugin/cli.mts --check plugins/dsh-atlas-runtime
```

## 一次性 profile 验证

在一次性 profile 安装 npm 包，检查合成配置中只有一条 `dsh-background-jobs-sidebar`。
在插件页启停整包和成员行，观察侧栏任务区的出现与消失。
如果成员处于停用状态，循环启停整包后该成员应保持停用。
用一个会话任务和一个共享任务检查计数变化，并点击会话任务返回所属会话。

## Local development

Use Node.js 22.18 or newer and run `pnpm install --frozen-lockfile`, `npm test`, and `npm run check` from this checkout.
For local UI testing, choose the prepared directory in **Plugins → Add plugin** in a disposable profile.
If the standalone sidebar is enabled, switch it off before enabling this bundle because they share a plugin row.
