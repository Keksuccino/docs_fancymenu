---
title: 幻灯片放映
description: 如何制作和使用幻灯片放映。
---

# 幻灯片放映

FancyMenu 允许你添加幻灯片放映，并将其显示在菜单中以及作为菜单背景。

> **重要**：如果你使用的是 Windows，别忘了开启[文件扩展名](https://vtcri.kayako.com/article/296-view-file-extensions-windows-10)，否则你以后将无法看到文件名中的重要部分！
{.is-warning}

# 制作幻灯片放映

每个幻灯片放映都必须放在位于 `/config/fancymenu/slideshows/` 的 slideshows 目录**内部**的各自文件夹中。

![1](https://user-images.githubusercontent.com/35544624/105209961-b823e600-5b4a-11eb-8ed2-1016d3b05815.png)

要让系统识别一个幻灯片放映，它的幻灯片文件夹中需要有一个属性文件。所以如果你把幻灯片文件夹命名为 `myslideshow`，那么属性文件应位于 `/config/fancymenu/slideshows/myslideshow/properties.txt`。

**这个文件始终必须命名为 `properties.txt`！**
目前先只创建一个**空的**属性文件，然后继续下一步。

![2](https://user-images.githubusercontent.com/35544624/105210016-cbcf4c80-5b4a-11eb-84ad-9aa735340287.png)

## 添加图片

幻灯片放映需要图片（显而易见），所以我们来添加一些！

> 你的幻灯片图片必须是 **PNG** 文件！不能是 JPEG、GIF、APNG 或 FMA！
{.is-danger}

幻灯片放映的所有图片都放在幻灯片文件夹（上例中的 `myslideshow`）**内部**的一个额外文件夹中。
这个文件夹的名称必须是 `images`。

![3](https://user-images.githubusercontent.com/35544624/105210833-d9d19d00-5b4b-11eb-8ae7-528ad156e27a.png)

现在把所有幻灯片图片放进 `images` 文件夹。
它们会按字母顺序排列（会考虑数字），所以只要把它们命名为类似 `image_1.png`、`image_2.png` 之类即可。
在我的示例中，`image_1.png` 会最先显示，之后是 `image_2.png`。

<br>
<img width="548" alt="Screenshot_2" src="https://github.com/user-attachments/assets/f58ecbfa-affa-4071-8a84-18ed27a6cfee">

## 向属性文件添加内容

一开始你已经在幻灯片文件夹中创建了一个空的 `properties.txt` 文件。
现在需要在这个文件里填入一些重要内容。

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
只有 `slideshow-meta` 部分中的变量可以修改！

### name

这是你的幻灯片放映的名称，或者更准确地说，是标识符。
幻灯片名称必须是**唯一**的，因此不可能存在两个同名幻灯片！

### width | height

你的幻灯片放映的基础 `width` 和基础 `height`。
FancyMenu 使用它们来计算宽高比。

### x | y

你的幻灯片放映的 `x` 和 `y` 位置。
更多用于调试，所以直接都设为 `0` 即可。

### duration

每张图片在切换到下一张之前显示的时长，单位为**秒**。
支持小数值！

### fadespeed

切换到下一张图片时淡入淡出动画的速度。
这个值是速度倍率。例如，`1.0` 是默认速度，`2.0` 表示速度加倍，`0.5` 表示速度减半。
不支持负值。

### randomize

幻灯片图片是否按随机顺序播放（`true`）或不按随机顺序播放（`false`）。

# 使用幻灯片放映

所有重要步骤都已完成，你的幻灯片放映现在应该已经准备好了，那就来测试一下吧！

要将你新的（或已编辑的）幻灯片放映加载到 FancyMenu 中，请通过 **Customization -> Reload FancyMenu** 重新加载模组。

现在你可以在 **Slideshow** 元素中使用你的幻灯片放映，或者将其作为菜单背景使用（右键布局编辑器背景 -> **Menu Background**）。
