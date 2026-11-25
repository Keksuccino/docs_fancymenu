---
title: 图像
description: FancyMenu 支持哪些图像文件，以及如何转换其他格式。
sourceBlobSha: 382f9ed2d99b0df29018dc4abf0b9b842ff01dec
---
# 图像

FancyMenu 可在许多地方显示图像，例如图像元素、菜单背景和按钮纹理。它支持以下文件：

- PNG（`.png`）：静态图像的最佳选择，支持透明度。
- JPEG（`.jpg` 或 `.jpeg`）：文件较小，适合照片，但不支持透明度。
- APNG（`.apng`）和 GIF（`.gif`）：动态图像。请参阅[动画](/animations)。

FancyMenu 会根据文件扩展名识别图像类型，因此文件名必须以正确的扩展名结尾。

> [!TIP]
> FancyMenu 会按照图像原样使用它们。若要保持图像清晰并提升加载速度，请参阅[优化纹理](/optimizing-textures)。

# 转换图像

FancyMenu 不支持 WebP 等其他格式。请先转换这些文件，例如使用在线工具：

- [WebP 转 PNG](https://convertio.co/webp-png/)
- [JPEG 转 PNG](https://jpg2png.com/)
- [PNG 转 JPEG](https://www.freeconvert.com/png-to-jpeg)：可缩小较大的图像文件，但会移除透明度。

若要制作或转换动画，请参阅[制作动画](/animations#making-animations)。
