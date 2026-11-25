---
title: 动画
description: 了解如何在 FancyMenu 中使用动画图片，以及如何制作动画图片。
sourceBlobSha: 76227b0d592e15bf10929c35d6a78e1eea6ee85a
---
# 动画

FancyMenu 几乎可以在所有能使用图片的地方播放动画图片，例如[图片元素](/elements#image)、[图片菜单背景](/menu-backgrounds#image)、按钮和滑块纹理、[游戏开场画面](/game-intro)等。

动画请使用 **APNG** 或 **GIF** 文件：

- **APNG**（动画 PNG）画质更好：拥有普通 PNG 的全部颜色，并支持边缘平滑的透明效果。它最适合用于徽标、背景以及任何需要透明效果的内容。
- **GIF** 更为常见，因此制作和编辑 GIF 的工具也更多。不过，GIF 每帧最多只有 256 种颜色，像素也只能完全透明或完全不透明。

> [!NOTE]
> FancyMenu 自有的动画格式 FMA 和 AFMA 已弃用。现有文件仍可使用，但制作新动画时请使用 APNG 或 GIF。请参阅 [FMA 和 AFMA](#fma-and-afma)。

# 使用动画

1. 将文件放入 `<game-directory>/config/fancymenu/assets/`，这样它就会显示在 FancyMenu 的文件选择器中。也可以使用网页 URL 和资源包文件，详见[资源](/resources)。
2. 像选择其他图片一样选择该文件，例如在图片元素的**图片来源**中选择它。

> [!WARNING]
> APNG 文件必须以 `.apng` 结尾。许多工具会将 APNG 保存为 `.png`，因此请重命名文件，否则 FancyMenu 会将其显示为静态图片。网页 URL 也一样，必须以 `.apng` 结尾。

## 动画的播放方式

- 动画会按照文件中设置的次数播放，然后停留在最后一帧。制作文件时可以设置循环次数。
- 动画只会在屏幕上显示时播放。再次显示时，会从停止的位置继续播放。
- **打开屏幕时重启动画纹理**会让图片元素和图片菜单背景在屏幕每次打开时都从头播放动画。
- **鼠标悬停时重启动画纹理**会让按钮和滑块的纹理在鼠标每次移到其上方时都从头播放。
- [**动画纹理开始播放**](/listeners#animated-texture-started-playing)和[**动画纹理播放完毕**](/listeners#animated-texture-finished-playing)监听器会在动画开始或结束时执行操作。

## 性能

FancyMenu 会在 APNG 和 GIF 播放期间进行解码，并且只提前解码少量帧，因此即使是很长的动画也只占用少量内存。

不过，帧尺寸过大或帧率过高仍会影响性能。帧的尺寸应与其在屏幕上的显示尺寸大致相同，详见[优化纹理](/optimizing-textures)。如果是带声音的长片段，请改用[视频](/video)。

# 制作动画

以下免费工具可以将单帧图片或视频制作为 APNG 和 GIF：

- [ScreenToGif](https://www.screentogif.com/)（Windows）：点击**编辑器**，将 PNG 帧拖入其中，设置帧间隔，然后将动画保存为 APNG 或 GIF。可以在保存菜单中设置循环方式。
- [ezgif](https://ezgif.com/)（在线，无需下载）：可以用图片制作 [GIF](https://ezgif.com/maker) 或 [APNG](https://ezgif.com/apng-maker)，将视频转换为 [GIF](https://ezgif.com/video-to-gif) 或 [APNG](https://ezgif.com/video-to-apng)，也可以将 [GIF 转换为 APNG](https://ezgif.com/gif-to-apng) 或将 [APNG 转换为 GIF](https://ezgif.com/apng-to-gif)。
- [FFmpeg](https://ffmpeg.org/download.html)（命令行工具）：请参阅下文。

## 使用 FFmpeg

将编号的 PNG 帧（例如 `frame_0001.png`、`frame_0002.png` 等）转换为无限循环的 APNG。`-framerate 20` 表示每秒播放 20 帧：

```bash
ffmpeg -framerate 20 -i frame_%04d.png -plays 0 animation.apng
```

将视频转换为 APNG。`fps=20` 表示每秒保留 20 帧，`scale=960:-1` 表示将宽度设为 960 像素：

```bash
ffmpeg -i trailer.mp4 -vf "fps=20,scale=960:-1" -plays 0 trailer.apng
```

将视频转换为无限循环的 GIF。`palettegen` 部分会为视频选出最合适的 256 种颜色：

```bash
ffmpeg -i trailer.mp4 -vf "fps=15,scale=640:-1:flags=lanczos,split[a][b];[a]palettegen[p];[b][p]paletteuse" -loop 0 trailer.gif
```

将 GIF 转换为 APNG：

```bash
ffmpeg -i logo.gif -plays 0 logo.apng
```

# FMA 和 AFMA

FMA 和 AFMA 是 FancyMenu 自有的动画格式。两者均已弃用：仍可播放，但制作新动画时，APNG 和 GIF 是更好的选择。

如果仍要制作 AFMA，请按以下步骤操作：

1. 将帧保存为 PNG 文件并放入同一个文件夹。帧会按照文件名顺序播放，例如 `frame_1.png`、`frame_2.png`……`frame_10.png`。
2. 打开**菜单栏 -> 工具 -> AFMA 创建器**。
3. 将**主帧目录**设为该文件夹。**开场帧目录**中的帧会在主帧之前播放一次。
4. 设置**主帧时间（毫秒）**和**循环次数**。循环次数设为 `0` 表示无限循环。
5. 设置**输出 AFMA 文件**，然后点击**导出**。
