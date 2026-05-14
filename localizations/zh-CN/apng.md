---
title: APNG
description: 如何制作与 FancyMenu 兼容的 APNG 图片。
---

# 动态 PNG 图片

> 对于新的大型或复杂动画，建议优先使用 [AFMA/FMA 文件](/fma)。当可用时，FancyMenu 3.9.0 可以使用 Watermedia V3 + Watermedia Binaries V3 以更快地解码 APNG/GIF，但 AFMA 仍然是 FancyMenu 首选的动画格式。
{.is-info}


APNG 是 PNG 图片的动画版本，因此它可以像 GIF 一样实现动画效果，但保留 PNG 的完整无损画质！

FancyMenu 内置了 APNG 支持，但它对可支持的 APNG 有些挑剔。
它需要**未压缩**且**非隔行扫描**的 APNG。

# 制作 APNG 动画

你可能会惊讶，找到一款好用的 APNG 编辑器有多难，尤其是还要能关闭压缩和隔行扫描。

一个很不错的编辑器选择是 [ScreenToGif](https://www.screentogif.com/)，它实际上是一款用于录制屏幕 GIF 和 APNG 的工具，不过你也可以跳过录制部分，直接在编辑器里导入素材，从而轻松制作普通的 APNG！

## 打开编辑器

打开 [ScreenToGif](https://www.screentogif.com/) 后，首先会看到这个界面。点击这里的 **Editor**。

![screentogif_2](https://github.com/Keksuccino/FancyMenu/assets/35544624/a8d34313-b841-4fb6-bf3a-ff02c39792cb)

## 加载帧

现在你需要准备好 PNG 帧。将它们拖放到编辑器中。

![screentogif_dragndrop](https://github.com/Keksuccino/FancyMenu/assets/35544624/ba4ad4a5-484e-46f1-8efd-90ba764462d8)

## 帧延迟

要设置帧与帧之间的延迟，请选择你要编辑的帧，然后切换到 **Edit** 选项卡，在 **Delay (Duration)** 区域中点击 **Override**。

![screentogif_delay](https://github.com/Keksuccino/FancyMenu/assets/35544624/a5d93139-3192-4090-b243-e5c0fe299963)

## 循环播放

循环播放行为可以在 **Save As** 菜单中配置。下一步会介绍如何打开这个菜单。

## 导出 APNG

现在你可以再次切换到 **File** 选项卡，然后点击 **Save As**。

在保存菜单中，请确保：
- 将文件类型设置为 **APNG**（第一个设置项，你可能需要先滚动到菜单顶部）
- 禁用 **Detect Unchanged Pixels**

> 你也可以在那个菜单中配置**循环行为**！禁用 **Looped Apng** 会使 APNG 完全不循环；启用后，你可以选择循环次数或无限循环。
{.is-info}

![screentogif_save](https://github.com/Keksuccino/FancyMenu/assets/35544624/954353da-45ed-4df8-9f06-c78a0a469fc8)

## 在 FancyMenu 中使用 APNG

现在你可以将 APNG 文件复制到 `/config/fancymenu/assets/`。之后，几乎所有接受图片的地方都可以使用它。

> 这个 APNG 文件名**非常重要**，必须以 `.apng` 结尾！
> 如果不是以 `.apng` 结尾，FancyMenu 将无法将该图片识别为 APNG。
{.is-warning}

![screentogif_use_apng](https://github.com/Keksuccino/FancyMenu/assets/35544624/2322da62-4013-451e-9a8b-3df0bf92df54)
