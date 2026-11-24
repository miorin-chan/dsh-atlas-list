# 项目文档

## 使用

- [左侧栏列表三态切换](../../dsh-workspace-list-toggle/README.zh.md)。
  点击列表标题旁的箭头，在「全部」「收起」和「需关注」之间切换。
- [会话草稿](../../dsh-session-draft/README.zh.md)。
  有未发送草稿的空闲会话旁会显示铅笔。
  启用三态切换后，这些会话也会出现在「需关注」视图中。
- [常驻会话](../../dsh-watched-sessions/README.zh.md)。
  把会话拖到列表顶部的常驻区，可重新排序或只看需关注的会话。
- [后台任务侧栏](../../dsh-background-jobs-sidebar/README.zh.md)。
  在账号控件上方查看运行中的任务，点击有归属会话的任务即可打开对话。
- [峰谷时间](../../dsh-peak-pricing-sidebar/README.zh.md)。
  在账号控件上方查看 DeepSeek 峰时、谷时和节假日时段，圆点标记当前时间。
  在聚合包详情页可开启倒计时并调整格式。

## 兼容条件

需要 DeepSeek Harness `0.2.2-rc.5` 的 Web 客户端，桌面版也适用。
本地构建需要 Node.js 22.18 或更新版本。

## 安装

在[聚合清单](../aggregate.yml)中查看使用 `link:` 的成员。
在各成员的源码目录运行 `npm ci`，再在聚合包目录运行 `pnpm install --frozen-lockfile`。

在 **插件 → 添加插件** 中选择 `dsh-atlas-list` 目录。
每个成员在「列表模块化改良计划」详情页都有独立开关。

## 维护

[聚合清单](../aggregate.yml)声明成员及顺序。
修改后运行 `npm test` 重新生成，运行 `npm run check` 核对生成结果。
发布前用 `npm run prepublishOnly` 检查成员的固定 npm 版本。

## Usage

- [Sidebar list toggle](../../dsh-workspace-list-toggle/README.md).
  Click the arrow next to the list heading to cycle through **All**, **Collapsed**, and **Needs attention**.
- [Session drafts](../../dsh-session-draft/README.md).
  A pencil marks idle sessions with unsent drafts.
  The sidebar list toggle keeps those sessions visible in **Needs attention**.
- [Watched sessions](../../dsh-watched-sessions/README.md).
  Drag a session to the watched section at the top, where you can reorder sessions or filter
  for those needing attention.
- [Background jobs sidebar](../../dsh-background-jobs-sidebar/README.md).
  See active jobs above the account control.
  Select a job linked to a session to open its conversation.
- [Peak pricing timeline](../../dsh-peak-pricing-sidebar/README.md).
  See DeepSeek peak, off-peak, and holiday hours above the account control.
  Use the bundle details to turn on the countdown or change its format.

## Compatibility and installation

Requires the Web client on DeepSeek Harness `0.2.2-rc.5`, including Desktop.
With Node.js 22.18 or newer, run `npm ci` in each checkout listed with `link:`
in the [aggregate manifest](../aggregate.yml).
Run `pnpm install --frozen-lockfile` in the bundle directory, then select that directory in **Plugins → Add plugin**.
Each feature has its own switch in the bundle details.
