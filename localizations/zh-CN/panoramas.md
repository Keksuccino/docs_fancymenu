---
title: 全景图
description: 如何制作和使用自定义背景全景图。
---

# 立方全景图

FancyMenu 支持加载自定义的 6 张图片全景立方体，作为菜单背景。

这些全景图是一种特殊的立方全景格式，Minecraft 在标题界面中将其用作背景，它由 6 张图片（各个面）组成，并以立方体（更准确地说，是天空盒）形式渲染。

> **重要**：如果你使用的是 Windows，别忘了开启 [文件扩展名](https://cdn.discordapp.com/attachments/795308330746511390/801561308012347482/unknown.png)，否则你之后将无法看到文件名中重要的部分！
{.is-warning}

# 制作全景图

如果你不知道 Minecraft 是如何处理背景全景图以及如何创建它们，可以看看 [这个视频](https://www.youtube.com/watch?v=F7jMd3zsjZQ&t)。
它会让你很好地理解 Minecraft 的全景图是如何工作的，以及如何制作一个！

看完视频后，你会发现制作这些全景图可能有点耗时。
为了帮你节省一些时间，也许可以考虑使用一个能自动生成全景图的模组。
你可以通过搜索 `minecraft panorama mod` 找到一些，其中一个是 [Panoramica](https://www.curseforge.com/minecraft/mc-mods/panoramica)（由我制作）。

# 准备全景图

在你拿到 6 张全景图片后，需要把它们移动到正确的位置！

FancyMenu 的全景图目录位于 `.minecraft/config/fancymenu/panoramas`。
这是你想在模组中使用的所有全景图所在的目录。

## 全景图文件夹

每个全景图都有自己独立的文件夹。
如果你想添加一个新的全景图，需要在 `.minecraft/config/fancymenu/panoramas` 中创建一个新文件夹。
在我的示例中，我会把文件夹命名为 `mypanorama`。

![1](https://user-images.githubusercontent.com/35544624/100791916-2802d380-341a-11eb-8e32-f9913e93a38c.png)

## 文件夹内容

创建文件夹后，你需要往里面填充内容。

### 属性文件
每个全景图都需要一个属性文件才能工作。
这个文件必须始终命名为 `properties.txt`，并且需要写入一些重要信息。

全景图属性文件的内容应始终如下所示：
```
type = panorama

panorama-meta {
  name = name_of_your_panorama
  speed = 1.0
  fov = 85.0
  angle = 25.0
  start_rotation = 0
}
```
只有 `panorama-meta` 部分中的变量可以修改！

#### name
这必须是你的全景图**唯一**的名称。
不能加载两个同名的全景图！
你之后会用这个名称来识别你的全景图。

#### speed
全景图旋转的速度。
这个值是一个速度倍数。例如，`1.0` 是默认速度，`2.0` 是两倍速度，`0.5` 是一半速度。
不支持负值；如果要降低速度，请使用小数值。

#### fov
视野范围（FOV）。
默认 FOV 为 `85.0`。
这里使用过大或过小的值都会破坏全景图。你可以自行调整，找到想要的 FOV。

#### angle
查看全景图时的垂直角度。
默认角度为 `25.0`。

#### start_rotation
全景图开始时的旋转角度（水平）。取值范围为 0 到 360。

<br>

### 全景图片文件夹

你的全景图文件夹还需要另一个必需内容：存放全景图片的实际图片文件夹。

这个文件夹的名称必须是 `panorama`。

把所有全景图片放进去，但别忘了像上面的 [视频](https://www.youtube.com/watch?v=F7jMd3zsjZQ&t) 中展示的那样正确命名它们！

![3](https://user-images.githubusercontent.com/35544624/100791922-29340080-341a-11eb-8174-874a180d0485.png)

> 全景图仅支持 PNG 格式！
{.is-warning}

### 全景图覆盖层

最后一步是**可选**的，如果你不想在全景图上方添加覆盖层，可以跳过。

如果你想为全景图添加暗角或其他类型的覆盖层，可以添加一个名为 `overlay.png` 的文件。
请注意，覆盖层只支持 PNG 格式，并且文件名必须始终是 `overlay.png`！

### 再次检查一遍

现在你应该已经在 `.minecraft/config/fancymenu/panoramas` 中有了一个文件夹，其中包含一个 `properties.txt` 文件、另一个名为 `panorama` 的文件夹，以及可能还有一个名为 `overlay.png` 的覆盖层。

![2](https://user-images.githubusercontent.com/35544624/100791920-29340080-341a-11eb-8e26-98a7fd2ad7eb.png)

# 使用全景图

在（重新）启动游戏，或者通过 **Customization -> Reload FancyMenu** 重新加载 FancyMenu 后，你现在应该可以将你的全景图设置为菜单背景了。要这样做，请在布局编辑器背景上右键单击，然后点击 **Menu Background**。
