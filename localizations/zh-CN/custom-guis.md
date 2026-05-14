---
title: 自定义 GUI
description: 如何向游戏中添加一个新的 GUI 屏幕。
---

# 自定义 GUI

FancyMenu 允许你自定义已有的 GUI 屏幕，同时也允许你添加全新的屏幕并为其填充元素。

# 添加新屏幕

要添加一个新屏幕，请前往 **Customization -> Custom GUIs -> Manage Custom GUIs**。

![custom_gui_1](https://github.com/Keksuccino/FancyMenu/assets/35544624/23e704ee-ccb5-434d-b75f-f4418399d9b7)

在下一个菜单中，点击 **New GUI**。

![custom_gui_2](https://github.com/Keksuccino/FancyMenu/assets/35544624/035454e8-b089-4b9a-9092-89a193c0eacd)

在这里，你需要为新的 GUI 提供一个唯一的标识符，并且你还可以自定义基础屏幕行为的其他部分。
当你完成后，按下 **Done**。

![custom_gui_3](https://github.com/Keksuccino/FancyMenu/assets/35544624/1fbed3f9-9c81-4c73-85c7-d152146c55d8)

现在你已经拥有了一个新的空白 GUI。要打开它，请在 **Manage Custom GUIs** 菜单中选中该 GUI，然后点击 **Open GUI**。

![custom_gui_4](https://github.com/Keksuccino/FancyMenu/assets/35544624/b2e6a4b7-540d-4bf2-9dce-09bfff11ae7e)

这将打开一个仍然相当空的 GUI 屏幕。要让它不那么空，只需像为其他屏幕一样为它创建一个新的布局即可。

![custom_gui_5](https://github.com/Keksuccino/FancyMenu/assets/35544624/e7e06a5f-46b3-48f1-9ad9-96a7565c97a9)

# 通过动作打开 GUI

最后一步是让普通用户能够访问你的 GUI。最简单的方法是使用带有按钮、滑块或 ticker 的 **Open Screen or Custom GUI** 动作。

![custom_gui_6](https://github.com/Keksuccino/FancyMenu/assets/35544624/b5cc6518-3fc4-4715-96d4-44b65ab7831d)

# 通过命令打开 GUI

你也可以通过[in-game command](./commands#openguiscreen) 打开你的自定义 GUI。
这甚至允许你远程为其他用户打开该 GUI！

# 弹出模式

从 FancyMenu v3.8.0 开始，自定义 GUI 支持“Popup Mode”，它会让它们看起来像是在另一个屏幕之上弹出的窗口（即自定义 GUI 打开时所来自的上一个屏幕）。你可以在每个自定义 GUI 的设置中分别切换此选项。

FancyMenu 3.9.0 还增加了一个选项：当在世界中时，可为自定义 GUI 切换屏幕背景遮罩。需要时可用它来禁用或保留在游戏过程中打开的自定义 GUI 背后的模糊/暗色遮罩。
