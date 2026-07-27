---
title: 自定义光标
description: 如何让菜单使用自定义鼠标光标。
---

# 自定义鼠标光标

向布局中添加一个 [**Cursor** 元素](./elements#cursor)，即可替换该屏幕上的系统光标：

1. 选择 **New Element -> Cursor**。
2. 设置一个带 RGBA 颜色的 PNG 纹理。
3. 将 **Hotspot X** 和 **Hotspot Y** 设置为纹理中应发生点击的位置像素。
4. 在编辑时需要检查光标效果时，启用编辑器预览。
5. 如果同一个光标需要在多个受支持的屏幕上显示，请使用 [Universal Layout](./universal-layouts)。

建议使用较小的光标纹理，例如 `32×32` 或 `64×64`。光标的外观和行为可能因操作系统而异。
