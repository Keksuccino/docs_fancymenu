---
title: 高级定位与尺寸
description: 如何使用元素的高级定位和尺寸设置。
---
# 高级定位与尺寸

高级定位和尺寸可让你直接控制元素的坐标和尺寸。

> [!WARNING]
> 对于 GUI 缩放适配，建议先尝试整套布局的 **自动缩放**。右键单击编辑器背景，强制设置一个 GUI 缩放，然后在同一菜单中启用 **自动缩放**。


# 切换高级定位/尺寸模式

要为某个元素启用高级定位或尺寸设置，请**右键单击**该元素，然后选择 **高级定位** 或 **高级尺寸**。
当你设置了高级位置或尺寸值时，元素会自动切换到高级模式。

要**禁用**它并切回普通定位/尺寸，请**清除所有定位/尺寸值**。

> [!WARNING]
> 当元素处于高级尺寸/定位模式时，可能会禁用或限制对该元素的缩放和/或移动。

# 计算位置/尺寸

高级位置和尺寸值支持 [占位符](./placeholders)。

这使你可以将 [**计算器**](./placeholders#calculator-calc) 占位符与 GUI 占位符结合使用，例如 [**屏幕宽度**](./placeholders#screen-width-guiwidth)、[**GUI 缩放**](./placeholders#gui-scale-guiscale) 和 [**元素宽度**](./placeholders#element-width-elementwidth)。

> [!NOTE]
> 你可以通过点击文本编辑器右上角的 **占位符** 按钮来添加占位符。如果你看不到这个按钮，则你要编辑的内容**不支持**占位符。

要使用 [**计算器占位符**](./placeholders#calculator-calc) 进行计算，请将示例表达式替换为你自己的表达式。嵌套占位符可以提供屏幕或元素尺寸。

此示例返回 `2`：

`{"placeholder":"calc","values":{"expression":"1 + 1","decimal":"false"}}`

对于整数像素的位置和尺寸计算，请将 `decimal` 保持为 `false`。

下面的计算器使用了 [**屏幕宽度**占位符](./placeholders#screen-width-guiwidth)，并将其除以 `2`：

`{"placeholder":"calc","values":{"expression":"{"placeholder":"guiwidth"} / 2","decimal":"false"}}`

> [!IMPORTANT]
> **高级定位**会忽略元素锚点，并使用屏幕左上角（`X0 Y0`）作为原点。**保持在屏幕内**仍然生效。
