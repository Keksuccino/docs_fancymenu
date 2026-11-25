---
title: 命令
description: FancyMenu 的命令及其用法。
sourceBlobSha: 265258e46a219a12892146238e379af513ff0848
---

# 命令

FancyMenu 为游戏添加了一些命令。将这些命令与 FTB Quests 等其他模组配合使用时，会非常实用。

> [!WARNING]
> 要在多人游戏中使用命令，FancyMenu 必须安装在**服务器端**（以及客户端）！

## 目标玩家和权限

`/openguiscreen`、`/closeguiscreen` 和 `/fmlayout` 命令中的目标玩家参数为可选参数。玩家省略该参数时，命令会作用于该玩家。指定目标时，可以使用普通玩家名称和 `@a` 等选择器。

- 为 `/openguiscreen` 或 `/closeguiscreen` 指定目标参数需要**权限等级 2**（游戏管理员 / OP 等级 2），即使目标是命令执行者本人也是如此。
- 为 `/fmlayout` 指定目标参数需要**权限等级 3**（管理员 / OP 等级 3），即使目标是命令执行者本人也是如此。
- `/fmdata` 的每个子命令都需要**权限等级 2**（游戏管理员 / OP 等级 2）。

对于这三个带有可选目标参数的命令，只有命令执行者是玩家时，才能省略目标参数。服务器控制台必须指定目标，并满足目标参数对应的权限要求。

## /openguiscreen

`/openguiscreen` 命令可打开原版、模组或[自定义 GUI](/custom-guis)。如果服务器和目标玩家的客户端都安装了 FancyMenu，该命令也可以作用于其他玩家。

请参阅[通过命令打开 GUI](/opengui-command)和[屏幕标识符](/screen-identifiers)。

并非所有模组屏幕都能直接创建。如果目标屏幕不受支持，FancyMenu 会显示错误。在本地布局中，请在通常用于打开该屏幕的控件上使用[**模仿原版/模组按钮**](/action-scripts#mimic-vanillamod-button)。

**用法：** `/openguiscreen <screen_identifier> [<target_players>]`

## /closeguiscreen

`/closeguiscreen` 命令会关闭命令执行者或所选玩家当前打开的屏幕。它适用于能够执行命令的任务、事件或自动化模组。

**用法：** `/closeguiscreen [<target_players>]`

## /fmlayout

`/fmlayout` 命令用于设置一个或多个客户端上的布局是否启用。请使用 FancyMenu 中显示的布局名称；名称中包含空格时，请用引号括起来。

**用法：** `/fmlayout <layout_name> <true|false> [<target_players>]`

示例：

- `/fmlayout quest_complete true` 会为执行命令的玩家启用 `quest_complete`。
- `/fmlayout quest_complete false @a` 会为所有在线玩家禁用该布局。指定目标参数需要权限等级 3。

## /fmvariable

`/fmvariable` 命令用于设置和读取 [FancyMenu 变量](/variables)。

若要以其他玩家的身份执行此命令，请使用原版的 `/execute as` 命令：
`/execute as ExamplePlayer run fmvariable ...`

**用法：**

- `/fmvariable get <variable_name>`
- `/fmvariable set <variable_name> <send_chat_feedback> <set_to_value>`

### 获取

若要**获取变量值**，请使用 `get` 子命令，如下所示：
`/fmvariable get some_variable`

随后，该变量的值会显示在聊天栏中。

### 设置

若要**设置变量**，请将聊天反馈布尔值放在新值之前：
`/fmvariable set some_variable true new_value`

`send_chat_feedback` 参数用于控制 FancyMenu 是否在聊天栏中确认更改。`set_to_value` 参数会接收命令剩余的所有内容，因此变量值可以包含空格。例如，`/fmvariable set greeting false Hello from FancyMenu` 会存储 `Hello from FancyMenu`，且不发送成功反馈。

## /fmdata

`/fmdata` 命令用于在服务器与 FancyMenu 客户端之间传输自定义数据、管理服务器端监听器、配置玩家加入时发送的数据，并导出此配置以用于 [AI 聊天](/export-for-ai#servers)。`/fmdata` 的每个子命令都需要权限等级 2。

所有子命令、语法和示例，请参阅 [FM Data](/fm-data)。
