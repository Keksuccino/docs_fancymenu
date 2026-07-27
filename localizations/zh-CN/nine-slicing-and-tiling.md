---
title: 九宫切片与平铺
description: 缩放带边框的纹理或重复无缝纹理。
---

# 九宫切片与平铺

九宫切片会在拉伸中心区域的同时保留纹理的角和边框。平铺则会重复纹理，而不是将其拉伸。

<img src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/nine_slicing_example.png" alt="九宫切片区域" style="max-width:500px;height:auto;" />

# 九宫切片支持

| 区域 | 支持的目标 |
|---|---|
| 小部件 | [按钮](./elements#button) 和 [滑块](./elements#slider) 纹理；[全局按钮和滑块样式](./global-customizations#button-visuals) |
| 图片和面板 | [图片元素](./elements#image) |
| 进度条 | [填充和背景纹理](./elements#progress-bar) |
| 提示框 | [自定义背景纹理](./elements#tooltip) |

# 配置九宫切片

1. 设置目标纹理。
2. 启用其 **九宫切片** 选项。
3. 设置边框尺寸，使其与源纹理中固定的边缘区域相匹配。
4. 调整元素大小，并在角落或边缘出现变形时修改边框值。

按钮和图片设置使用 X/Y 边框尺寸。进度条和提示框在需要时会提供独立的边缘值。

# 平铺支持

以下项目可使用重复纹理：

- [图片元素](./elements#image)。
- [图片菜单背景](./menu-backgrounds)。
- [可滚动列表的标题和页脚纹理](./customizing-scrollable-screens)。

在图片元素或图片背景上启用 **重复纹理**。对于可滚动界面，请使用标题/页脚自定义菜单中的重复选项。

请使用无缝源纹理；不匹配的边缘会在平铺之间产生可见线条。

九宫切片和平铺是两种独立模式。如果某个目标同时显示这两个选项，请选择与预期缩放行为相符的那个。
