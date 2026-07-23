---
title: Get Frames from Videos
description: Extract PNG frames from a video with FFmpeg.
published: true
date: 2025-04-16T19:18:14.899Z
tags: ffmpeg, mp4, mkv, video, frame, frames
editor: markdown
dateCreated: 2025-04-14T20:14:40.022Z
---

# Extract Video Frames with FFmpeg

1. Install [FFmpeg](https://ffmpeg.org/download.html) and make sure the `ffmpeg` command is available.
2. Open a terminal in the directory containing your video.
3. Create the output directory:

   ```bash
   mkdir output_frames
   ```

4. Run the command that matches the frames you need. Replace `input.mp4` with your video's filename.

## Extract Every Frame

```bash
ffmpeg -i input.mp4 output_frames/frame_%04d.png
```

## Extract at a Fixed Frame Rate

This example creates 10 frames per second. Change `10` as needed.

```bash
ffmpeg -i input.mp4 -vf "fps=10" output_frames/frame_%04d.png
```

## Resize Extracted Frames

This example scales every frame to `1280×720`.

```bash
ffmpeg -i input.mp4 -vf "scale=1280:720" output_frames/frame_%04d.png
```

The numbered PNG files in `output_frames` can be used to create an [AFMA or classic FMA animation](./fma). Fewer frames and smaller dimensions reduce file size and memory use.
