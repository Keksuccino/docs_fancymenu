---
title: 玩家头颅
description: 如何在菜单中将玩家头颅显示为 2D 或 3D 图像。
---

# 菜单中的玩家头颅

要使用图像元素将玩家头颅显示为 2D 或 3D 图像，你可以使用一个名为“Minotar”的第三方 Web API。

## 2D 图像

### 1. 添加一个图像元素

在 FancyMenu 编辑器中，右键单击背景，选择“New Element”，然后选择“Image”（或“Picture”）。

### 2. 设置网页来源

右键单击图像元素以打开其属性。对于来源类型，选择“Web”。

### 3. 使用正确的占位符构建 URL

在“Source”字段中，输入以下 URL：
`https://minotar.net/avatar/{"placeholder":"playername"}.png`

FancyMenu 会使用 `{"placeholder":"playername"}` 动态将当前玩家的用户名插入到 URL 中，从而让图像元素从 Minotar 获取并显示他们的头颅。

## 3D 图像

这个和 2D 版本很相似，但这里需要使用不同的 URL：

`https://minotar.net/cube/{"placeholder":"playername"}/200.png`

这里的 `200` 是像素大小，因此如果你想要更小的版本，只需将它替换为例如 `100`；或者如果想要更大的版本，则使用 `300`，以此类推。
