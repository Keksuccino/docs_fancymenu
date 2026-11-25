---
title: 屏幕标识符
description: 了解屏幕标识符，以及如何查找屏幕的标识符。
sourceBlobSha: 64414e10bf5f532e075373a6a753e2f667448ceb
---
# 屏幕标识符

FancyMenu 使用屏幕标识符来处理布局、原版控件、[屏幕操作](/action-scripts#open-screen-or-custom-gui)和[自定义 GUI 覆盖](/custom-guis#overriding-an-existing-screen)。标识符区分大小写，请从调试叠加层中准确复制。

内置屏幕通常使用简短的通用标识符，例如 `title_screen`。其他模组的屏幕可能使用其 Java 类名。自定义 GUI 使用在其管理器中输入的标识符。这些是 FancyMenu 的屏幕标识符，并非 Minecraft 资源位置。

# 查找屏幕的标识符

你可以通过**调试叠加层**查看当前活动菜单的标识符。
其中会显示当前屏幕的标识符，左键单击即可将其复制到剪贴板。

>[!TIP]
>在**不处于**布局编辑器中时，按 **CTRL + ALT + D** 即可启用**调试叠加层**。

<br>

<img width="553" alt="Screenshot_3" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/1800351e-f042-4826-8eed-7725b78bc84d">

<br>

<img width="579" alt="Screenshot_4" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/9e0d1e61-7f2d-4817-9be1-b63ee61978dd">

# 打开屏幕

[**打开屏幕或自定义 GUI**操作](/action-scripts#open-screen-or-custom-gui)只能打开 FancyMenu 能在当前游戏状态下构建的屏幕。有些屏幕需要已加载的世界、连接、玩家或原始父屏幕。

如果 FancyMenu 无法构建该标识符，就会显示错误。请对通常用于打开该屏幕的控件使用[**模拟原版/模组按钮**](/action-scripts#mimic-vanillamod-button)。
