---
title: 从视频中获取帧
description: 使用 FFmpeg 从视频中提取 PNG 帧。
---
# 使用 FFmpeg 提取视频帧

1. 安装 [FFmpeg](https://ffmpeg.org/download.html)，并确保 `ffmpeg` 命令可用。
2. 在包含你视频文件的目录中打开终端。
3. 创建输出目录：

   ```bash
   mkdir output_frames
   ```

4. 运行与你需要的帧类型相匹配的命令。将 `input.mp4` 替换为你的视频文件名。

## 提取每一帧

```bash
ffmpeg -i input.mp4 output_frames/frame_%04d.png
```

## 按固定帧率提取

此示例每秒创建 10 帧。请根据需要修改 `10`。

```bash
ffmpeg -i input.mp4 -vf "fps=10" output_frames/frame_%04d.png
```

## 调整提取帧的大小

此示例将每一帧缩放到 `1280×720`。

```bash
ffmpeg -i input.mp4 -vf "scale=1280:720" output_frames/frame_%04d.png
```

`output_frames` 中带编号的 PNG 文件可用于创建 [AFMA 或经典 FMA 动画](./fma)。帧数更少、尺寸更小可以减小文件大小并降低内存使用。
