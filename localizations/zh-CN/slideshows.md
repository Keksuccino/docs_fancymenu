---
title: 幻灯片
description: 如何制作和使用幻灯片。
---
# 幻灯片

FancyMenu 允许你添加幻灯片，并将它们显示在菜单中以及作为菜单背景。

> **重要**：如果你使用的是 Windows，别忘了开启 [文件扩展名](https://vtcri.kayako.com/article/296-view-file-extensions-windows-10)，否则以后你将无法看到文件名的重要部分！
{.is-warning}

# 制作幻灯片

每个幻灯片都必须放在 `<game-directory>/config/fancymenu/slideshows/` 下自己独立的文件夹中。

`<game-directory>` 指的是当前启动器实例，它不一定是默认的 `.minecraft` 目录。

![1](https://user-images.githubusercontent.com/35544624/105209961-b823e600-5b4a-11eb-8ed2-1016d3b05815.png)

要让幻灯片被识别，它所在的文件夹中需要有一个属性文件。如果幻灯片文件夹名为 `myslideshow`，那么该文件应放在 `<game-directory>/config/fancymenu/slideshows/myslideshow/properties.txt`。

**这个文件始终必须命名为 `properties.txt`！**
目前先只创建一个**空的**属性文件，然后继续下一步。

![2](https://user-images.githubusercontent.com/35544624/105210016-cbcf4c80-5b4a-11eb-84ad-9aa735340287.png)

## 添加图片

幻灯片需要图片，所以我们来添加一些。

幻灯片图片必须使用 `.png` 或 `.jpg`。其他图片扩展名，包括 `.jpeg`，都会被忽略。

幻灯片的所有图片都放在幻灯片文件夹（上例中的 `myslideshow`）里面的一个额外文件夹中。
这个文件夹的名称必须是 `images`。

![3](https://user-images.githubusercontent.com/35544624/105210833-d9d19d00-5b4b-11eb-8ae7-528ad156e27a.png)

现在把所有幻灯片图片放入 `images` 文件夹。

当 `randomize = false` 时，图片会按文件名的字母顺序播放。`image_10.png` 会排在 `image_2.png` 前面，所以请使用诸如 `image_01.png`、`image_02.png` 和 `image_10.png` 这样的命名。

<br>
<img width="548" alt="Screenshot_2" src="https://github.com/user-attachments/assets/f58ecbfa-affa-4071-8a84-18ed27a6cfee">

## 向属性文件添加内容

一开始，你已经在幻灯片文件夹中创建了一个空的 `properties.txt` 文件。
现在这个文件需要填入一些重要内容。

完整的目录结构应如下所示：

```text
<game-directory>/config/fancymenu/slideshows/
└── myslideshow/
    ├── properties.txt
    ├── overlay.png          # 可选
    └── images/
        ├── image_01.png
        └── image_02.jpg
```

每个幻灯片的属性文件都应如下所示：

```
type = slideshow

slideshow-meta {
   name = cool_slideshow
   width = 1920
   height = 1080
   x = 0
   y = 0
   duration = 5.0
   fadespeed = 12.0
   randomize = false
}
```
请保留 `type = slideshow` 这一行和 `slideshow-meta` 部分。请编辑列出的值，而不是结构行。

### name

这是用于选择该幻灯片的区分大小写的标识符。它是必需的，并且必须唯一；如果名称重复，只会有一个幻灯片可用。

### width | height

以 GUI 缩放像素为单位的基础宽度和高度。FancyMenu 也会使用它们来计算宽高比。

### x | y

以 GUI 缩放像素为单位的基础左上角位置。标准幻灯片元素和菜单背景会使用它们自己的位置，因此请将这两个值都保持为 `0`。

### duration

在切换到下一张之前，一张图片保持可见的秒数。小数点使用英文句点，例如 `5.5`。请使用大于 `0` 的值。

### fadespeed

淡入淡出速度的倍率。`1.0` 为默认值，`2.0` 表示快两倍，`0.5` 表示慢一半。请使用大于 `0` 的值。

### randomize

将其设为 `true` 表示随机顺序，设为 `false` 表示按文件名顺序。随机模式会避免连续显示同一张图片。

# 使用幻灯片

所有重要步骤都已完成，你的幻灯片现在应该已经准备好了，来测试一下吧！

要将新的或已编辑的幻灯片加载到 FancyMenu 中，请使用 **Customization -> Reload FancyMenu**，或者重启客户端。

现在你可以在 **Slideshow** 元素中使用你的幻灯片，或者将其用作菜单背景（在布局编辑器背景上右键 -> **Menu Background**）。
