---
title: 图像
description: FancyMenu 中图像资源相关的所有重要信息。
---
# 图像

FancyMenu 支持在许多地方使用图像资源，例如菜单背景、按钮纹理等。

FancyMenu 支持 PNG、JPEG、GIF 和 APNG 图像文件，但对于静态图像，建议尽可能使用 PNG。对于动画，与其使用 GIF 和 APNG，不如使用 [AFMA 文件](/fma)。AFMA 是 FancyMenu 自有的动画图像格式，相比 GIF/APNG，它的优化程度更高，占用的 RAM 更少，对性能的影响也更小。

# 将图像转换为受支持的格式

当你需要将图像转换为 FancyMenu 支持的格式，或者出于各种原因想要在不同的受支持格式之间进行转换时，可以参考下面这份在线图像转换网站列表。这些网站使用方便，无需下载任何软件。

## GIF 转 APNG
要将 GIF 图像转换为 APNG，请使用：https://ezgif.com/gif-to-apng。

## APNG 转 GIF
要将 APNG 转换为 GIF，请使用：https://ezgif.com/apng-to-gif。

## MP4 转 APNG
如果你需要将一小段视频转换为 APNG，可以试试这个：https://ezgif.com/video-to-apng

## PNG 转 JPEG
有时使用 JPEG 可以减小资源体积，因此在这种情况下，使用 JPEG 替代 PNG 可能是个不错的选择：https://www.freeconvert.com/png-to-jpeg。请注意，JPEG 不支持透明度。

## JPEG 转 PNG
对于常见的 JPEG 转 PNG 场景，可以试试：https://jpg2png.com/

## WebP 转 PNG
FancyMenu 不支持 WebP 文件，因此你需要将其转换为 PNG：https://convertio.co/webp-png/

# 动画纹理的限制

FancyMenu 使用自有的 [AFMA 格式](/fma) 来实现优化的动画，使 [AFMA 文件](/fma) 能够以高分辨率包含大量帧。但对于 GIF 和 APNG 等旧式动画文件格式，为避免过度占用 RAM 或对游戏性能造成太大影响，请遵守以下建议限制：

- 每个动画最多使用 **200 帧**。
- 每帧的分辨率最高为 **1080p**。
- 所有动画合计不应超过 **1000 帧**。即使每个动画只使用 200 帧，所有帧仍会被加载到内存中，因此同时使用过多动画仍会占满 RAM。

> [!IMPORTANT]
> 这些限制不适用于 [AFMA 文件](/fma)，因为 AFMA 不会将所有帧加载到内存中，而且优化程度高得多，因此相比旧式动画格式，它们对性能的影响要小得多。
