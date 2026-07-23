---
title: 命令
description: FancyMenu 的命令以及如何使用它们。
---
# 命令

FancyMenu 为游戏添加了一些命令，在与 FTB Quests 等其他模组配合使用时非常有用。

> [!WARNING]
> 在多人游戏中使用命令时，FancyMenu 必须安装在 **服务器**（以及客户端）上！

## 目标玩家与权限

`/openguiscreen`、`/closeguiscreen` 和 `/fmlayout` 的目标玩家参数是可选的。玩家省略该参数时，命令会作用于该玩家本身。指定目标时，可以使用普通玩家名以及 `@a` 之类的选择器。

- 为 `/openguiscreen` 或 `/closeguiscreen` 提供目标参数需要 **权限等级 2**（游戏管理员 / OP 2 级），即使目标是命令来源本身也是如此。
- 为 `/fmlayout` 提供目标参数需要 **权限等级 3**（管理员 / OP 3 级），即使目标是命令来源本身也是如此。
- 每个 `/fmdata` 子命令都需要 **权限等级 2**（游戏管理员 / OP 2 级）。

对于这三个带可选目标的命令，只有当命令来源是玩家时，省略目标参数才可用。服务器控制台必须提供目标，并满足目标参数所需的权限要求。

## /openguiscreen

`/openguiscreen` 命令会打开原版、模组或 [自定义 GUI](./custom-guis)。当 FancyMenu 安装在服务器和客户端上时，它可以指定其他玩家作为目标。

请参阅 [通过命令打开 GUI](./opengui-command) 和 [屏幕标识符](./screen-identifiers)。

并非所有模组界面都能直接创建。如果目标屏幕不受支持，FancyMenu 会显示错误。在本地布局中，请在通常用于打开它的控件上使用 [**模拟原版/模组按钮**](./action-scripts#mimic-vanillamod-button-mimicbutton)。

**用法：** `/openguiscreen <screen_identifier> [<target_players>]`

## /closeguiscreen

`/closeguiscreen` 命令会为命令来源或选中的玩家关闭当前界面。它与能够运行命令的任务、事件或自动化模组配合使用时非常有用。

**用法：** `/closeguiscreen [<target_players>]`

## /fmlayout

`/fmlayout` 命令用于设置一个或多个客户端上的布局是否启用。请准确使用该布局在 FancyMenu 中显示的名称，包含空格的名称需要用引号括起来。

**用法：** `/fmlayout <layout_name> <true|false> [<target_players>]`

示例：

- `/fmlayout quest_complete true` 会为运行该命令的玩家启用 `quest_complete`。
- `/fmlayout quest_complete false @a` 会为所有在线玩家禁用它。提供目标参数需要权限等级 3。

## /fmvariable

`/fmvariable` 命令用于设置和读取 [FancyMenu 变量](./variables)。

要以其他玩家身份执行此命令，请使用原版的 `/execute as` 命令：
`/execute as ExamplePlayer run fmvariable ...`

**用法：**

- `/fmvariable get <variable_name>`
- `/fmvariable set <variable_name> <send_chat_feedback> <set_to_value>`

### 获取

要**获取变量值**，请使用 `get` 子命令，如下所示：
`/fmvariable get some_variable`

然后该变量的值会打印到你的聊天栏中。

### 设置

要**设置变量**，请在新值前面放上聊天反馈布尔值：
`/fmvariable set some_variable true new_value`

`send_chat_feedback` 参数控制 FancyMenu 是否在聊天中确认更改。`set_to_value` 参数会消耗命令剩余的所有内容，因此值中可以包含空格。例如，`/fmvariable set greeting false Hello from FancyMenu` 会存储 `Hello from FancyMenu`，而不会发送成功反馈。

## /fmdata

`/fmdata` 命令用于在服务器与 FancyMenu 客户端之间发送自定义数据，管理服务器端监听器，并配置玩家加入时发送的数据。每个 `/fmdata` 子命令都需要权限等级 2。

有关所有子命令、语法和示例，请参阅 [FM 数据](./fm-data)。
