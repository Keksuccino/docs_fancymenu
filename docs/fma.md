---
title: Animations (FMA/AFMA)
description: How to make and use FancyMenu animation files.
---

# Animations

AFMA and FMA files are animated texture formats created for FancyMenu.

# AFMA Files

**AFMA** (Advanced FancyMenu Animation) is the successor to classic FMA files.

AFMA uses a non-ZIP format with smaller files, lower memory use, and better performance than classic FMA.

For large or complex animated textures, use **AFMA** instead of classic FMA.

Create AFMA files with the built-in creator:

1. Open FancyMenu's menu bar.
2. Go to **Tools -> AFMA Creator**.
3. Import/convert your frames with the creator.

> [!IMPORTANT]
> AFMA files cannot be packed manually. Use **Tools -> AFMA Creator**.

Classic FMA files remain supported, so existing layouts do not need to be converted immediately.

# Classic FMA Files

## Making an FMA

A classic FMA file is a ZIP archive with a `.fma` extension.

### File Extensions

Enable file extensions in your file manager before creating or renaming the files below.

On Windows, open File Explorer and enable **View -> File name extensions**.

<br>
<img width="764" alt="Screenshot_9" src="https://gist.github.com/assets/35544624/1f0a0864-1ad8-4f63-be3a-ab18385539e6"> 

### Preparation

Create a folder named `fancymenu_animation` for the archive contents.

Create a required `frames` directory and an optional `intro_frames` directory inside it.

In the same folder, create `metadata.json`. Make sure its file extension is `.json`, not `.txt`.

The folder must now contain `frames/`, `intro_frames/`, and `metadata.json`.

<br>
<img width="700" alt="Screenshot_3" src="https://gist.github.com/assets/35544624/e29f6666-ee4a-4d79-b7e2-1b640f40ce78">

### The Metadata JSON

Open `metadata.json` in a text editor and use this template:

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

Edit the values as needed.

#### `loop_count`

Controls how many times the animation plays. Use `0` to loop indefinitely. A positive value plays that many times, then holds the last frame.

#### `frame_time`

Sets how long each normal frame remains visible, in milliseconds.

#### `frame_time_intro`

Sets the frame time for optional **intro** frames.

#### `custom_frame_times`

Optionally overrides the duration of individual normal frames. This example keeps frames `0` and `1` visible for `5000` milliseconds while other frames use `frame_time`:

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

Frame indexes are zero-based: the first frame is `0`, the second is `1`, and so on.

Add a comma after every custom frame-time entry except the last one.

#### `custom_frame_times_intro`

Uses the same format as `custom_frame_times`, but applies to optional intro frames.

Save `metadata.json`.

### The Frames

> [!CAUTION]
> Keep classic FMA animations at or below 200 frames and 1080p. Use [Video](./video) for long or high-frame-rate content.

Place normal frames in `frames/`. They must be PNG files named sequentially from `0.png`, such as `0.png`, `1.png`, and `2.png`. Other formats and names are not supported.

To extract frames from a video, see [Extracting Frames with FFmpeg](./ffmpeg-frames).

<br>
<img width="574" alt="Screenshot_4" src="https://gist.github.com/assets/35544624/eac54695-b57a-4919-8740-4e5c8aad649c">

### The Intro

Place optional intro frames in `intro_frames/`. They follow the same PNG naming rules as normal frames, play once before the normal sequence, and do not loop.

### Packing the FMA File

Create a ZIP containing the folder's contents. `metadata.json`, `frames/`, and the optional `intro_frames/` directory must be at the ZIP root, not inside another directory.

On Windows, select the contents of `fancymenu_animation`, right-click the selection, and choose **Send to -> Compressed (zipped) folder**.

<br>
<img width="752" alt="Screenshot_6" src="https://gist.github.com/assets/35544624/5b7e7670-5403-410e-943c-283bfe6d585c">

Locate the resulting ZIP file.

<br>
<img width="700" alt="Screenshot_7" src="https://gist.github.com/assets/35544624/987f7989-dff7-43b4-a54c-0898969827f5">

Its root contents should look like this:

<img width="700" alt="Screenshot_8" src="https://gist.github.com/assets/35544624/f1642a39-e14c-47a7-90f6-8a737e8ec75f">

Rename the file to `fancymenu_animation.fma`, replacing the `.zip` extension. The base filename can be changed, but the `.fma` extension is required.

The renamed archive is now ready to use as an FMA file.

# Using AFMA & FMA Files in FancyMenu

> [!IMPORTANT]
> AFMA/FMA files are animated textures, so add them through [**Image** inputs](./elements#image). Almost everything that accepts images also accepts AFMA and FMA files.

Use AFMA/FMA files anywhere that accepts an image, including [Image elements](./elements#image) and [Image menu backgrounds](./menu-backgrounds).

Store the AFMA/FMA file in `<game-directory>/config/fancymenu/assets/` so it appears in FancyMenu's local resource chooser.
