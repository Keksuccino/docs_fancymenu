---
title: 命令
description: FancyMenu 的命令及其使用方法。
---

# 命令

FancyMenu 为游戏添加了一些命令，在与 FTB Quests 等其他模组配合使用时非常有用。

> 在多人游戏中使用命令时，FancyMenu 需要同时安装在 **服务器**（以及客户端）上！
{.is-warning}

## /openguiscreen

`/openguiscreen` 命令可让你打开一个 GUI（原版/模组和自定义 GUI）。
当 FancyMenu 同时安装在服务器和客户端上时，它甚至可以远程为其他玩家打开 GUI。

有关此命令更详细的说明，请查看 [通过命令打开 GUI](/opengui-command) 页面。

该命令并不适用于每一个界面，尤其是模组界面。如果命令无法打开某个界面，它会显示错误。在这种情况下，你能做的并不多，因为那个界面很可能过于复杂，FancyMenu 无法自动打开。

我也不会再手动为模组界面添加兼容性了，因为要为现存的所有模组添加兼容支持会花掉我太多时间，抱歉。

**用法：** `/openguiscreen <screen_identifier> <target_player>`

## /closeguiscreen

`/closeguiscreen` 命令可让你关闭当前 GUI。

嗯？你说这完全没用？

确实是，但其实也不是。

当你使用会在特定操作时触发命令的模组时，这个命令就很有用。
所以，是的，如果不配合其他模组，这个命令确实完全没用；但如果你安装了合适的模组，它就会非常实用！

**用法：** `/closeguiscreen <target_player>`

## /fmvariable

`/fmvariable` 命令允许你设置和获取 FancyMenu 变量。

要在服务器上以另一个玩家的身份执行此命令，你可以使用原版的 `/execute as` 命令。
比如说，你想以玩家 `ExamplePlayer` 的身份执行 `/fmvariable` 命令。在这种情况下，你应输入：
`/execute as ExamplePlayer run fmvariable...`。

**用法：** `/fmvariable <get_or_set> <variable_name> [<set_to_value>] [<send_chat_feedback>]`

### 获取
要**获取变量值**，请使用 `get` 子命令，例如：
`/fmvariable get some_variable`

然后，这个变量的值会输出到你的聊天栏中。

### 设置
要**设置变量**，请使用 `set` 子命令，例如：
`/fmvariable set some_variable new_value true`

这里的最后一个参数用于设置是否接收聊天反馈，也就是是否希望该命令将消息输出到你的聊天栏中。
