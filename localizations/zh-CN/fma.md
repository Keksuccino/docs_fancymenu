---
title: 动画（FMA/AFMA）
description: 如何制作和使用 FancyMenu 动画文件。
---

# 动画

AFMA/FMA 文件是专为 FancyMenu 创建的特殊动画纹理文件。
它们和 APNG 非常相似，但对 FancyMenu 的优化要好得多。

# AFMA 文件

FancyMenu 3.9.0 新增了 **AFMA**（Advanced FancyMenu Animation，高级 FancyMenu 动画），它是经典 FMA 文件的继任者。

AFMA 文件不再是 ZIP 文件。它们使用 FancyMenu 更新的动画格式，文件更小、内存占用更低，性能也更好。

对于新的大型或复杂动画纹理，请使用 **AFMA**，而不是经典 FMA。

创建 AFMA 文件的方法如下：

1. 打开 FancyMenu 的菜单栏。
2. 进入 **Tools -> AFMA Creator**。
3. 使用创建器导入/转换你的帧。

> [!IMPORTANT]
> AFMA 文件不能像经典 FMA 文件那样手动打包。你需要使用 **AFMA Creator** 来打包/创建它们。

经典 FMA 文件仍然受支持，并且在 FancyMenu 3.9.0 中也经过了优化，因此现有布局不需要立即转换。

# 经典 FMA 文件

## 制作 FMA

制作 FMA 文件和创建 ZIP 文件一样简单！当然，这主要是因为它本质上就是一个 ZIP 文件。

### 文件扩展名

你需要能看到文件扩展名才能按照本文档操作，所以在开始之前请确保先**启用文件扩展名**。

在 Windows 上，可以先打开任意文件夹，然后点击右上角的箭头展开下方菜单。

接着进入 **查看** 选项卡，并启用 **文件扩展名**。

<br>
<img width="764" alt="Screenshot_9" src="https://gist.github.com/assets/35544624/1f0a0864-1ad8-4f63-be3a-ab18385539e6"> 

### 准备工作

先为 FMA 文件内容创建一个新文件夹。
在这个示例中，我们将文件夹命名为 `fancymenu_animation`。

在这个文件夹中，再创建两个文件夹。第一个文件夹**必须**命名为 `frames`，第二个文件夹**必须**命名为 `intro_frames`。

然后在同一文件夹中创建一个新的 TXT 文件，并将其重命名为 `metadata.json`。
请确保它不再只是一个 TXT 文件。你**必须**把文件扩展名改成 `json`。

现在你应该有一个名为 `fancymenu_animation` 的文件夹，其中包含一个名为 `frames` 的文件夹、一个名为 `intro_frames` 的文件夹，以及一个名为 `metadata.json` 的 JSON 文件。

<br>
<img width="700" alt="Screenshot_3" src="https://gist.github.com/assets/35544624/e29f6666-ee4a-4d79-b7e2-1b640f40ce78">

### 元数据 JSON

这个文件用于告诉 FancyMenu 应该如何处理你的 FMA 纹理。
它包含帧时间（每一帧显示多久）和循环次数等信息。

请用文本编辑器打开 `metadata.json` 文件。

将以下文本复制到文件中：

```json
{
  "loop_count": 0,
  "frame_time": 41,
  "frame_time_intro": 41,
  "custom_frame_times": {
  },
  "custom_frame_times_intro": {
  }
}
```

这是文件应有的基本模板。
现在你可以按自己的喜好进行自定义。

#### `loop_count`

这个参数用于控制纹理循环（重新开始动画）的次数。

将其设为 `0` 表示无限循环。它将*永远不会停止*。

大于 `0` 的值表示纹理播放的次数。例如，将其设为 `1` 表示纹理只播放一次，然后停在最后一帧；`2` 表示它会播放两次，然后停在最后一帧，*依此类推*。

#### `frame_time`

这是动画纹理帧的通用帧时间，单位为**毫秒**。
帧时间表示在动画切换到下一帧之前，该帧可见的时长。

#### `frame_time_intro`

这基本上和 `frame_time` 一样，但适用于动画纹理的**引导（intro）**帧。
引导帧是**可选**的，后面会详细介绍。

#### `custom_frame_times`

这是**可选**项，可用于覆盖某些（非引导）帧的帧时间。
例如，你希望所有帧都显示 `41` 毫秒，所以把 `frame_time` 设为 `41`，但你又希望第一帧和第二帧显示 `5000` 毫秒。

在这种情况下，你可以这样写：

```json
{
  "loop_count": 0,
  "frame_time": 41,
  "frame_time_intro": 41,
  "custom_frame_times": {
    0: 5000,
    1: 5000
  },
  "custom_frame_times_intro": {
  }
}
```

帧编号从 0 开始，这意味着动画的第一帧是 `0`，第二帧是 `1`，以此类推。

每个自定义帧时间条目末尾都需要有一个**逗号**，**最后一项除外**！

#### `custom_frame_times_intro`

这和 `custom_frame_times` 完全相同，但在这里是针对**引导**帧的。引导帧是**可选**的，后面会详细介绍。

`metadata.json` 文件就到这里。现在保存并关闭文本编辑器。

### 帧文件

> 建议每个动画最多使用**200 帧**，并且**最大分辨率为 1080p**，因为动画会占用大量内存，而且它们不是视频。它们适合用于短循环动画，而不是用 24 FPS 播放完整视频。
{.is-danger}

动画纹理的帧应放入 `frames` 文件夹中。

帧文件必须是**PNG 文件**！**不支持 JPEG 和其他格式**！

每一帧**必须**只用帧编号和文件扩展名命名。
第一帧应命名为 `0.png`，第二帧为 `1.png`，第三帧为 `2.png`，以此类推。
如果帧文件名无效，纹理将**无法工作**！

如需**从视频中提取帧**，请查看[这篇文档页面](/ffmpeg-frames)。

<br>
<img width="574" alt="Screenshot_4" src="https://gist.github.com/assets/35544624/eac54695-b57a-4919-8740-4e5c8aad649c">

### 引导（Intro）

此功能是**可选**的。

FMA 文件的**引导**功能是一种特殊方式，可以在 `frames` 文件夹中的实际帧开始播放**之前**先播放一些帧。 

引导部分**永远不会循环**，并且只会在动画第一次播放时执行，这样你就可以在实际动画开始循环前播放类似淡入的过渡动画。

引导帧应放入 `intro_frames` 文件夹中，其规则与普通帧相同：

帧文件必须是**PNG 文件**！**不支持 JPEG 和其他格式**！

每一帧**必须**只用帧编号和文件扩展名命名。
第一帧应命名为 `0.png`，第二帧为 `1.png`，第三帧为 `2.png`，以此类推。
如果帧文件名无效，纹理将**无法工作**！

### 打包 FMA 文件

现在 `fancymenu_animation` 文件夹中已经包含所有重要内容，所以你现在可以打包你的 FMA 文件了！

打包 FMA 文件其实就是把文件夹内容打包成 ZIP 文件。
内容必须位于 ZIP 文件的**根目录**，也就是说不能在 ZIP 内多套一层文件夹。

在 Windows 上，最简单的方式是先选中 `fancymenu_animation` 文件夹中的所有内容，然后**右键单击** `metadata.json` 文件。在弹出的上下文菜单中，点击 **发送到 -> 压缩 ZIP 文件夹**。

<br>
<img width="752" alt="Screenshot_6" src="https://gist.github.com/assets/35544624/5b7e7670-5403-410e-943c-283bfe6d585c">

现在 `fancymenu_animation` 文件夹中应该会出现一个新的 ZIP 文件，名为 `metadata.zip`、`frames.zip` 或 `intro_frames.zip`。

<br>
<img width="700" alt="Screenshot_7" src="https://gist.github.com/assets/35544624/987f7989-dff7-43b4-a54c-0898969827f5">

打开这个文件后，其内容应如下所示：

<img width="700" alt="Screenshot_8" src="https://gist.github.com/assets/35544624/f1642a39-e14c-47a7-90f6-8a737e8ec75f">

现在你需要将文件重命名为 `fancymenu_animation.fma`。请确保把 `.zip` **替换**成 `.fma`，这样它就不再是 ZIP 文件了。

当然，你可以把 `fancymenu_animation` 这一部分改成任何你想要的名字，但请确保它仍然是 `.fma` 文件！

就这样！现在你已经拥有一个（希望是）可用的 FMA 文件了！

# 在 FancyMenu 中使用 AFMA 和 FMA 文件

> [!IMPORTANT]
> AFMA/FMA 文件被视为**动画纹理**，因此你需要通过**图像**输入来添加它们。几乎所有接受图像（PNG、JPEG、GIF 等）的地方，也都可以接受 FMA 和 AFMA 文件。

你可以像使用其他动画纹理/图像格式一样使用 AFMA/FMA 文件。FancyMenu 会把它当作普通图像，因此你可以在任何可以设置纹理的地方使用它，比如**图像元素**或**图像菜单背景**。

请确保 AFMA/FMA 文件位于 `/config/fancymenu/assets/` 文件夹中，因为 FancyMenu 只能从其 `assets` 文件夹中选择纹理和其他资源。
