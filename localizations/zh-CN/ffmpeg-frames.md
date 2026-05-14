---
title: 从视频中获取帧
description: 如何从视频文件中提取帧。
---

# 如何使用 FFmpeg 从视频中提取帧

*本页面部分由 ChatGPT AI 生成。*

FFmpeg 是一个免费的工具，可帮助你处理视频和音频文件。它的一个很酷的功能是可以从视频中提取图片（帧），例如 MP4 文件。下面将一步一步教你如何做到这一点。

以下命令中将使用 MP4，但 FFmpeg 也支持其他视频格式，如 AVI、MOV、MKV 和 MPEG。

# 你需要准备什么

在开始之前，请确保你已经准备好以下内容：

1. **已安装 FFmpeg**：

   - 从官方 [FFmpeg 网站](https://ffmpeg.org/download.html) 下载 FFmpeg。请务必下载 “full” 版本。
   - 按照适用于你电脑的安装说明进行设置。

2. **命令行访问权限**：

   - 使用终端（Linux/macOS）或命令提示符（Windows）运行 FFmpeg 命令。

3. **视频文件**：

    - 准备一个 MP4、AVI、MOV、MKV 或 MPEG 视频文件。

# 开始之前

在运行任何命令之前，请先准备以下内容：

## 启用文件扩展名显示

  - 在重命名视频文件时，能够看到 `.mp4` 或 `.avi` 之类的文件扩展名非常重要。

    - **在 Windows 上**：

      - 打开文件资源管理器。
      - 点击顶部的“查看”选项卡。
      - 勾选“文件扩展名”复选框。

    - **在 macOS 上**：

      - 打开 Finder。
      - 在菜单栏中点击“Finder”，然后选择“偏好设置”。
      - 进入“高级”选项卡，并勾选“显示所有文件扩展名”。

## 创建输出文件夹

- 在 FFmpeg 可执行文件所在的目录中创建一个名为 `output_frames` 的文件夹。提取出的帧将保存在这里。

## 准备你的视频文件

- 将你要提取帧的视频文件放到与 FFmpeg 可执行文件相同的目录中。
- 将视频文件重命名为 `input` 加上其文件扩展名（例如 `input.mp4`、`input.avi` 等）。这样可以确保下面的命令无需修改即可运行。

<br>
<img width="579" alt="Screenshot_4" src="https://gist.github.com/user-attachments/assets/1cb4ddf9-a17a-4219-b7d4-aa344adaa87c" />

# 如何打开 FFmpeg

在使用 FFmpeg 之前，需要通过命令行打开它。下面将介绍如何在 Windows 和 macOS 上一步一步操作。

## 在 Windows 上：

1. **打开命令提示符**：
   - 同时按下 `Windows` 键和 `R` 键，打开“运行”窗口。
   - 输入 `cmd` 并按回车。这会打开命令提示符。

2. **进入 FFmpeg 文件夹**：
   - 你需要告诉电脑 FFmpeg 位于哪里。使用 `cd` 命令切换到你保存 FFmpeg 的文件夹。
   - 例如，如果 FFmpeg 位于桌面上名为 `ffmpeg-2024\bin` 的文件夹中，请输入：
     ```bash
     cd C:\Users\YourUsername\Desktop\ffmpeg-2024\bin
     ```
     （请将“YourUsername”替换为你电脑上的实际用户名。）

3. **检查 FFmpeg 是否可用**：
   - 为了确认 FFmpeg 正常工作，请输入以下命令：
     ```bash
     ffmpeg -version
     ```
   - 如果一切正常，屏幕上会显示 FFmpeg 的信息。

## 在 macOS 上：

1. **打开终端**：
   - 同时按下 `Command` 和 `Space`，打开聚焦搜索。
   - 输入 `Terminal` 并按回车打开它。

2. **进入 FFmpeg 文件夹**：
   - 使用 `cd` 命令切换到你保存 FFmpeg 的文件夹。
   - 例如，如果 FFmpeg 位于你的 `Downloads` 文件夹中，请输入：
     ```bash
     cd ~/Downloads/ffmpeg-2024/bin
     ```

3. **检查 FFmpeg 是否可用**：
   - 为了确认 FFmpeg 已准备就绪，请输入以下命令：
     ```bash
     ./ffmpeg -version
     ```
   - 如果 FFmpeg 正常工作，屏幕上会显示相关信息。

# 如何保存所有帧

要保存视频中的所有帧，请使用以下命令：

```bash
ffmpeg -i input.mp4 output_frames/%d.png
```

## 这是什么意思：

- `-i input.mp4`：这是你的输入视频文件。它应与 FFmpeg 可执行文件位于同一目录中。请务必将 `input.mp4` 改为正确的文件名和扩展名。
- `output_frames/frame_%04d.png`：这表示帧的保存方式：
- `output_frames/`：将所有帧保存在名为 `output_frames` 的文件夹中。
- `%d.png`：帧将按数字命名，例如 `1.png`、`2.png` 等，保持顺序。

# 在特定时间保存帧

如果你不想保存所有帧，可以每秒保存一帧（或按其他间隔保存）。使用以下命令：

```bash
ffmpeg -i input.mp4 -vf "fps=1" output_frames/%d.png
```

## 这是什么意思：

- `-i input.mp4`：这是你的输入视频文件。它应与 FFmpeg 可执行文件位于同一目录中。请务必将 `input.mp4` 改为正确的文件名和扩展名。
- `-vf "fps=1"`：这表示每秒保存一帧。如果你希望保存帧的频率更高或更低，可以修改 `1` 这个数值（例如，`fps=0.5` 表示每两秒保存一帧，`fps=2` 表示每秒保存两帧）。
- `output_frames/%d.png`：将帧保存在名为 `output_frames` 的文件夹中，文件名类似 `1.png`、`2.png` 等。

# 更改帧的大小和质量

你还可以调整保存帧的大小和质量。方法如下：

```bash
ffmpeg -i input.mp4 -vf "scale=1280:720" -q:v 2 output_frames/%d.png
```

## 这是什么意思：

- `-i input.mp4`：这是你的输入视频文件。它应与 FFmpeg 可执行文件位于同一目录中。请务必将 `input.mp4` 改为正确的文件名和扩展名。
- `-vf "scale=1280:720"`：将帧大小更改为 1280x720 像素。
- `-q:v 2`：设置图片质量（1 为最佳，数值越大质量越低）。
- `output_frames/%d.png`：将帧保存在名为 `output_frames` 的文件夹中，文件名类似 `1.png`、`2.png` 等。

# 保存帧的小贴士

1. **节省空间**：

   - 如果视频很长，你可以按间隔保存帧，而不是保存每一帧。这在将其用作 FancyMenu 中的 FMA 动画帧时尤其有用。

2. **了解更多**：

   - 在终端中运行 `ffmpeg -h`，查看 FFmpeg 还能做的更多有趣功能。

<br>
现在你已经可以使用 FFmpeg 从视频中保存帧了！&#x20;

