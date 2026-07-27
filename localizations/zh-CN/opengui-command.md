---
title: 通过命令打开 GUI
description: 如何通过命令打开原版和自定义 GUI。
---

# 通过命令打开 GUI

`/openguiscreen` 命令可打开原版、模组和 [自定义 GUI](./custom-guis)。当服务器和客户端都安装了 FancyMenu 时，它还可以针对其他玩家生效。

要打开一个 GUI，请使用 `/openguiscreen <screen_identifier> [<target_players>]`。

将 `<screen_identifier>` 替换为自定义 GUI 或原版/模组界面的准确标识符，且区分大小写。

要查找标识符，请打开目标界面，并使用 **CTRL + ALT + D** 启用调试覆盖层。选择第一行上的标识符即可复制它。详见 [Screen Identifiers](./screen-identifiers)。

![copy_identifier](https://github.com/Keksuccino/FancyMenu/assets/35544624/dd6c53d9-d2bd-4810-be03-3741e326bd5a)

省略 `[<target_players>]` 可为自己打开该 GUI，或者使用玩家名或选择器（例如 `@a`）为一个或多个玩家打开它。提供目标参数需要 2 级权限（游戏管理员 / OP 2 级），即使目标是你自己也一样，而且每个目标玩家的客户端都必须安装了 FancyMenu。

并非每个模组界面都能直接创建。当目标界面不受支持时，FancyMenu 会显示错误。在本地布局中，请在通常用于打开它的组件上使用 [**模仿原版/模组按钮**](./action-scripts#mimic-vanillamod-button-mimicbutton)。

# 通过命令关闭 GUI

在极少数需要时，`/closeguiscreen [<target_players>]` 会关闭当前界面。省略目标参数时，它会作用于你自己；提供目标参数需要 2 级权限。
