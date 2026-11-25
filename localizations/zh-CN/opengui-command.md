---
title: 通过命令打开 GUI
description: 介绍如何通过命令打开原版和自定义 GUI。
sourceBlobSha: 9d0c8fbc3fa1d1cb15dc19e94f1f0fc1ba37ae05
---

# 通过命令打开 GUI

`/openguiscreen` 命令可打开原版、模组和[自定义 GUI](/custom-guis)。如果服务器和目标玩家的客户端都安装了 FancyMenu，该命令还可以指定其他玩家。

要打开 GUI，请使用 `/openguiscreen <screen_identifier> [<target_players>]`。

将 `<screen_identifier>` 替换为自定义 GUI 或原版/模组界面的准确标识符（区分大小写）。

要查找标识符，请打开目标界面，然后按 **CTRL + ALT + D** 启用调试覆盖层。选择第一行中的标识符即可复制。请参阅[界面标识符](/screen-identifiers)。

![copy_identifier](https://github.com/Keksuccino/FancyMenu/assets/35544624/dd6c53d9-d2bd-4810-be03-3741e326bd5a)

省略 `[<target_players>]` 可为自己打开 GUI；也可以使用玩家名称或 `@a` 之类的选择器，为一名或多名玩家打开 GUI。提供目标参数需要权限等级 2（游戏管理员 / OP 等级 2），即使目标是你自己也不例外；而且每位目标玩家的客户端都必须安装 FancyMenu。

并非所有模组界面都能直接创建。如果目标界面不受支持，FancyMenu 会显示错误。在本地布局中，请在通常用于打开该界面的控件上使用[**模拟原版/模组按钮**](/action-scripts#mimic-vanillamod-button)。

# 通过命令关闭 GUI

在少数需要的情况下，可以使用 `/closeguiscreen [<target_players>]` 关闭当前界面。省略目标时，此命令会影响你自己；提供目标参数则需要权限等级 2。
