---
title: 动画（FMA/AFMA）
description: 如何制作和使用 FancyMenu 动画文件。
---
# 动画

AFMA 和 FMA 文件是为 FancyMenu 创建的动画纹理格式。

# AFMA 文件

**AFMA**（Advanced FancyMenu Animation，高级 FancyMenu 动画）是经典 FMA 文件的后继格式。

AFMA 使用非 ZIP 格式，文件更小、内存占用更低，性能也比经典 FMA 更好。

对于大型或复杂的动画纹理，请使用 **AFMA**，不要使用经典 FMA。

使用内置创建器创建 AFMA 文件：

1. 打开 FancyMenu 的菜单栏。
2. 前往 **Tools -> AFMA Creator**。
3. 使用创建器导入/转换你的帧。

> [!IMPORTANT]
> AFMA 文件不能手动打包。请使用 **Tools -> AFMA Creator**。

经典 FMA 文件仍然受支持，因此现有布局不需要立即转换。

# 经典 FMA 文件

## 制作 FMA

经典 FMA 文件是一个带有 `.fma` 扩展名的 ZIP 压缩包。

### 文件扩展名

在创建或重命名下面的文件之前，请先在文件管理器中启用文件扩展名显示。

在 Windows 上，打开文件资源管理器并启用 **View -> File name extensions**。

<br>
<img width="764" alt="Screenshot_9" src="https://gist.github.com/assets/35544624/1f0a0864-1ad8-4f63-be3a-ab18385539e6"> 

### 准备工作

创建一个名为 `fancymenu_animation` 的文件夹，用于存放压缩包内容。

在其中创建一个必需的 `frames` 目录，以及一个可选的 `intro_frames` 目录。

在同一文件夹中创建 `metadata.json`。请确保它的文件扩展名是 `.json`，不是 `.txt`。

现在文件夹中应包含 `frames/`、`intro_frames/` 和 `metadata.json`。

<br>
<img width="700" alt="Screenshot_3" src="https://gist.github.com/assets/35544624/e29f6666-ee4a-4d79-b7e2-1b640f40ce78">

### 元数据 JSON

用文本编辑器打开 `metadata.json`，并使用以下模板：

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

按需要编辑这些值。

#### `loop_count`

控制动画播放的次数。使用 `0` 可无限循环。正数表示播放对应次数，然后停留在最后一帧。

#### `frame_time`

设置每个普通帧的显示时长，单位为毫秒。

#### `frame_time_intro`

设置可选 **intro** 帧的帧时长。

#### `custom_frame_times`

可选地覆盖单个普通帧的持续时间。下面的示例会让帧 `0` 和 `1` 显示 `5000` 毫秒，而其他帧使用 `frame_time`：

```json
{
  "loop_count": 0,
  "frame_time": 41,
  "frame_time_intro": 41,
  "custom_frame_times": {
    "0": 5000,
    "1": 5000
  },
  "custom_frame_times_intro": {
  }
}
```

帧索引从 0 开始：第一帧是 `0`，第二帧是 `1`，依此类推。

除了最后一项之外，每个自定义帧时长条目后都要加一个逗号。

#### `custom_frame_times_intro`

格式与 `custom_frame_times` 相同，但用于可选的 intro 帧。

保存 `metadata.json`。

### 帧文件

> [!CAUTION]
> 请将经典 FMA 动画控制在 200 帧以内，并保持在 1080p 及以下。对于较长或高帧率内容，请使用 [Video](./video)。

将普通帧放入 `frames/`。它们必须是按顺序命名的 PNG 文件，从 `0.png` 开始，例如 `0.png`、`1.png`、`2.png`。不支持其他格式和名称。

如果要从视频中提取帧，请参阅 [使用 FFmpeg 提取帧](./ffmpeg-frames)。

<br>
<img width="574" alt="Screenshot_4" src="https://gist.github.com/assets/35544624/eac54695-b57a-4919-8740-4e5c8aad649c">

### Intro

将可选的 intro 帧放入 `intro_frames/`。它们遵循与普通帧相同的 PNG 命名规则，在普通序列之前播放一次，并且不会循环。

### 打包 FMA 文件

创建一个包含该文件夹内容的 ZIP。`metadata.json`、`frames/` 以及可选的 `intro_frames/` 目录都必须位于 ZIP 根目录下，而不是另一个目录中。

在 Windows 上，选中 `fancymenu_animation` 的内容，右键单击所选内容，然后选择 **Send to -> Compressed (zipped) folder**。

<br>
<img width="752" alt="Screenshot_6" src="https://gist.github.com/assets/35544624/5b7e7670-5403-410e-943c-283bfe6d585c">

找到生成的 ZIP 文件。

<br>
<img width="700" alt="Screenshot_7" src="https://gist.github.com/assets/35544624/987f7989-dff7-43b4-a54c-0898969827f5">

其根目录内容应如下所示：

<img width="700" alt="Screenshot_8" src="https://gist.github.com/assets/35544624/f1642a39-e14c-47a7-90f6-8a737e8ec75f">

将文件重命名为 `fancymenu_animation.fma`，把 `.zip` 扩展名替换掉。基础文件名可以修改，但必须保留 `.fma` 扩展名。

现在，这个重命名后的压缩包就可以作为 FMA 文件使用了。

# 在 FancyMenu 中使用 AFMA 和 FMA 文件

> [!IMPORTANT]
> AFMA/FMA 文件是动画纹理，因此请通过 [**Image** 输入](./elements#image) 来添加。几乎所有接受图片的地方也都接受 AFMA 和 FMA 文件。

AFMA/FMA 文件可用于任何接受图片的地方，包括 [Image 元素](./elements#image) 和 [Image 菜单背景](./menu-backgrounds)。

将 AFMA/FMA 文件存放在 `<game-directory>/config/fancymenu/assets/` 中，这样它就会出现在 FancyMenu 的本地资源选择器里。
