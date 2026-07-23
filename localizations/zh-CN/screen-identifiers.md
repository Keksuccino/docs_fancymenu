---
title: 屏幕标识符
description: 关于屏幕标识符以及如何查找某个屏幕的标识符。
---
# 屏幕标识符

FancyMenu 会为布局、原版小部件、[屏幕操作](./action-scripts#open-screen-or-custom-gui-opengui)以及[自定义 GUI 覆盖](./custom-guis#overriding-an-existing-screen)使用屏幕标识符。标识符区分大小写，因此请务必从调试覆盖层中准确复制。

内置屏幕通常使用类似 `title_screen` 这样的简短通用标识符。其他模组的屏幕可能会使用它们的 Java 类名。自定义 GUI 使用在其管理器中输入的标识符。这些都是 FancyMenu 的屏幕标识符，而不是 Minecraft 资源位置。

# 查找屏幕的标识符

你可以使用**调试覆盖层**查看当前活动菜单的标识符。
它包含当前屏幕的标识符，并且你可以通过左键单击将其复制到剪贴板。

>[!TIP]
>你可以在**不**处于布局编辑器中时，按下 **CTRL + ALT + D** 来启用**调试覆盖层**。

<br>

<img width="553" alt="Screenshot_3" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/1800351e-f042-4826-8eed-7725b78bc84d">

<br>

<img width="579" alt="Screenshot_4" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/9e0d1e61-7f2d-4817-9be1-b63ee61978dd">

# 打开屏幕

[**打开屏幕或自定义 GUI** 操作](./action-scripts#open-screen-or-custom-gui-opengui)只能打开 FancyMenu 能在当前游戏状态下构造的屏幕。有些屏幕需要已加载世界、已连接、玩家，或原始父屏幕。

如果 FancyMenu 无法根据标识符构造该屏幕，它会显示错误。请在通常用于打开该屏幕的小部件上使用[**模拟原版/模组按钮**](./action-scripts#mimic-vanillamod-button-mimicbutton)。
