---
title: 通过命令打开 GUI
description: 如何通过命令打开原版和自定义 GUI。
---

# 通过命令打开 GUI

FancyMenu 自带了一个命令，可以让你通过命令打开原版和自定义 GUI。
当你在服务器和客户端都安装了 FancyMenu 时，你甚至可以为**其他玩家**远程打开 GUI。

要打开一个 GUI，只需使用命令 `/openguiscreen <screen_identifier> <target_player>`。

将 `<screen_identifier>` 替换为你想要打开的 GUI 的实际菜单标识符。
它可以是你使用 FancyMenu 制作的自定义 GUI 的标识符，也可以是原版/模组 GUI 的普通菜单标识符。

要获取**原版/模组 GUI 的菜单标识符**，打开你想查看标识符的菜单，并通过 **Customization -> Debug Overlay** 启用 FancyMenu 的**调试覆盖层**，然后你可以点击第一行显示的标识符，将其复制到剪贴板。

![copy_identifier](https://github.com/Keksuccino/FancyMenu/assets/35544624/dd6c53d9-d2bd-4810-be03-3741e326bd5a)

将 `<target_player>` 参数留空可为你的客户端打开 GUI，或者选择一个玩家（或多个玩家）来打开 GUI。
请注意，其他玩家的客户端也需要安装 FancyMenu。

这个命令并不适用于所有界面，尤其是模组界面。如果命令无法打开某个界面，它会显示错误。在这种情况下你能做的不多，因为那很可能是一个过于复杂、无法被 FancyMenu 自动打开的界面。

我也不会再手动为模组界面添加兼容性了，因为要为所有这些模组添加兼容性会花费我太多时间，抱歉。

# 通过命令关闭 GUI

在极少数情况下，如果你需要，还可以使用 `/closeguiscreen <target_player>` 命令来关闭当前界面。
