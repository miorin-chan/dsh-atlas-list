# 本地安装和验证

## 准备

使用 DeepSeek Harness `0.2.2-rc.5` 的桌面端或 Web 客户端。
准备源码需要 Node.js 22.18 或更新版本、npm 和 pnpm。
聚合包与[后台任务侧栏](../../dsh-background-jobs-sidebar/README.zh.md)的源码目录在默认工作区的 `plugins/` 下相邻。
在工作区根目录运行以下命令。准备工具先构建链接的成员，再生成聚合包。

```sh
pnpm --dir tools/dsh-aggregate install --frozen-lockfile --ignore-scripts
node tools/dsh-plugin-ts/prepare.mts plugins/dsh-atlas-runtime
```

从 **插件 → 添加插件** 选择准备工具输出的 `dsh-atlas-runtime` 目录。
打开「运行时模块化改良计划」卡片，可单独启停「后台任务侧栏」。
若同一 profile 已启用独立的后台任务侧栏，先停用独立 bundle，再添加聚合包。
两种安装方式共用行 ID。

## 维护

[聚合清单](../aggregate.yml)指向同级源码目录。
工作区生成器复制源插件的 patch，并把链接依赖写入包清单。
在聚合包目录运行 `npm test` 重新生成并校验。`npm run check` 只读检查生成物是否与源清单一致。
从工作区根目录再运行脚手架校验。

```sh
node tools/new-dsh-plugin/cli.mts --check plugins/dsh-atlas-runtime
```

## 一次性 profile 实测

2026-11-23，用 DSH `0.2.2-rc.5` Web 和 Chrome 验证了工作区中的本地链接。
Web profile 只添加聚合包，合成配置通过该包加载一条 `dsh-background-jobs-sidebar`。
在原生详情页逐项和整包启停，核对任务区及其 Host 路由的移除与恢复，整包重开后保留成员开关。
用本地模型和限时任务夹具确认会话任务与共享任务的计数从 0 到 2 再到 0，点击会话任务可回到所属会话。
另核对了中文深色、英文浅色、390 px 宽度的详情布局，以及 8 种语言各自可读的详情文件。

[实测记录与截图](../../../archive/tasks/2026/2026-11-23-atlas-runtime/README.md)

## Local installation

Use DSH `0.2.2-rc.5`, Node.js 22.18 or newer, npm, and pnpm.
Keep this checkout next to the background jobs sidebar.
Run the [preparation commands](#准备) from the workspace root,
then choose the printed `dsh-atlas-runtime` path in **Plugins → Add plugin**.
If the standalone sidebar is enabled in that profile, turn it off before adding this bundle.
