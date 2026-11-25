---
title: 高级定位与尺寸
description: 如何使用元素的高级定位与尺寸功能。
sourceBlobSha: 205b887e844f770856bfd4836ea791e0acdca4b8
---
# 高级定位与尺寸

高级定位与尺寸功能可让你直接控制元素的坐标和尺寸。

> [!WARNING]
> 若要适配不同 GUI 缩放比例，请先尝试对整个布局启用 **自动缩放**。右键单击编辑器背景，强制设置 GUI 缩放比例，然后在同一菜单中启用 **自动缩放**。


# 切换高级定位/尺寸模式

若要为元素启用高级定位或尺寸功能，请**右键单击**该元素，然后选择 **高级定位** 或 **高级尺寸**。
设置高级位置或尺寸值后，元素会自动切换到高级模式。

若要**禁用**高级模式并切回普通定位/尺寸模式，请**清除所有定位/尺寸值**。

> [!WARNING]
> 当元素处于高级尺寸/定位模式时，可能无法调整元素大小和/或移动元素，或这些操作会受到限制。

# 计算位置/尺寸

高级位置和尺寸值支持[占位符](/placeholders)。

因此，你可以将[**计算器**](/placeholders#calculator)占位符与 GUI 占位符结合使用，例如[**屏幕宽度**](/placeholders#screen-width)、[**GUI 缩放比例**](/placeholders#gui-scale)和[**元素宽度**](/placeholders#element-width)。

> [!NOTE]
> 点击文本编辑器右上角的 **占位符** 按钮即可添加占位符。如果看不到此按钮，说明你要编辑的内容**不支持**占位符。

若要使用[**计算器**占位符](/placeholders#calculator)进行计算，请将示例表达式替换为你自己的表达式。嵌套占位符可用于提供屏幕或元素尺寸。

此示例返回 `2`：

`{"placeholder":"calc","values":{"expression":"1 + 1","decimal":"false"}}`

进行整像素位置和尺寸计算时，请将 `decimal` 设为 `false`。

以下计算器示例使用[**屏幕宽度**占位符](/placeholders#screen-width)，并将其除以 `2`：

`{"placeholder":"calc","values":{"expression":"{"placeholder":"guiwidth"} / 2","decimal":"false"}}`

> [!IMPORTANT]
> **高级定位**会忽略元素锚点，并以屏幕左上角（`X0 Y0`）为原点。**保持在屏幕内**仍然有效。
