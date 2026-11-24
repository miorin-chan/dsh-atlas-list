# 列表 Atlas 开发与迁移

[中文使用说明](../README.zh.md) · [English guide](#local-development)

## 安装

适用于 DeepSeek Harness `0.2.2-rc.5`。用 Node.js 22.18 或更新版本准备与列表 Atlas 同级的常驻会话源码，再构建聚合包。

```sh
npm --prefix plugins/dsh-watched-sessions ci
pnpm --dir plugins/dsh-atlas-list install --frozen-lockfile
```

从「插件 → 添加插件」选择 `dsh-atlas-list` 目录。左侧栏列表三态切换、会话草稿、常驻会话和后台任务侧栏各有一个开关。
列表 Atlas 已安装时，也可用总管理卡上的第三个开关启停整包。

## 从运行时 Atlas 迁移

1. 记下工作区和运行时 Atlas 的整包及成员开关，以及激进侧边栏的展开模式。
2. 停用旧运行时 Atlas、旧工作区 Atlas，以及已单独启用的列表成员。更新工作区 Atlas，确认它只剩四个工作区成员。
3. 安装列表 Atlas，按之前的状态启用所需成员。四个成员沿用原行 ID，逐项核对开关。
4. 若原来启用了激进侧边栏，独立安装并启用，然后核对展开模式。确认迁移完成后可移除已停用的旧运行时包。

DSH 在同一 profile 内只能加载一份同 ID 的插件行。框架若提示重启，重启后再核对实际加载的行。

## 构建与发布

[聚合清单](../aggregate.yml)按顺序声明成员。修改后运行 `npm test`、`npm run check` 和工作区的插件骨架校验，
同步提交依赖清单、锁文件和生成的 patch。

目前常驻会话使用工作区内的 `link:` 依赖。公开 npm 发布前需要一个可从 npm 安装的固定成员版本。
`npm run prepublishOnly` 会检查发布依赖。

## Local development

Use Node.js 22.18 or newer. Run `npm ci` in the sibling `dsh-watched-sessions` checkout,
then `pnpm install --frozen-lockfile` in this checkout. Select this directory in **Plugins → Add plugin**.

Before migrating, record the bundle switches, individual plugin switches, and Aggressive sidebar’s opening mode.
Disable the old Runtime and Workspace bundles and any enabled standalone List members. Upgrade Workspace Atlas,
then install List Atlas. Verify the original row switches and reinstall Aggressive sidebar separately if needed.
