---
title: Animations
description: How to use animated images in FancyMenu, and how to make them.
---
# Animations

FancyMenu plays animated images almost everywhere you can use an image: in [Image elements](./elements#image), [image menu backgrounds](./menu-backgrounds), button and slider textures, the [Game Intro](./game-intro) and more.

Use **APNG** or **GIF** files for your animations:

- **APNG** (animated PNG) gives the better quality: all colors of a normal PNG, and proper transparency with soft edges. It's the best pick for logos, backgrounds and everything with transparency.
- **GIF** is more common, so there are more tools for making and editing GIFs. But a GIF only has 256 colors per frame, and its pixels are either fully see-through or not at all.

> [!NOTE]
> FancyMenu's own animation formats, FMA and AFMA, are deprecated. Your existing files still work, but use APNG or GIF for new animations. See [FMA and AFMA](#fma-and-afma).

# Using Animations

1. Put the file into `<game-directory>/config/fancymenu/assets/`, so it shows up in FancyMenu's file chooser. Web URLs and resource pack files work too, see [Resources](./resources).
2. Pick it like any other image, for example with **Image Source** of an Image element.

> [!WARNING]
> APNG files have to end with `.apng`. Many tools save APNGs as `.png`, so rename the file, or FancyMenu shows it as a still image. The same goes for web URLs: they need to end with `.apng`.

## How Animations Play

- An animation plays as often as its file says, then stays on its last frame. You set how often it loops when you make the file.
- Animations only play while they're on screen. When they show up again, they continue where they stopped.
- **Restart Animated Textures When Opening Screen** makes Image elements and image menu backgrounds start their animation over every time the screen opens.
- **Restart Animated Textures On Hover** makes the textures of buttons and sliders start over every time the mouse moves onto them.
- The [**Animated Texture Started Playing**](./listeners#on-animated-texture-started-playing-animated_texture_started_playing) and [**Animated Texture Finished Playing**](./listeners#on-animated-texture-finished-playing-animated_texture_finished_playing) listeners run actions when an animation starts or ends.

## Performance

FancyMenu decodes APNGs and GIFs while they play, only a few frames ahead, so even long animations need little memory.

Big frames and high frame rates still cost performance. Make your frames about as big as they show up on screen, see [Optimizing Textures](./optimizing-textures). For long clips with sound, use a [Video](./video) instead.

# Making Animations

These free tools make APNGs and GIFs from single frames or videos:

- [ScreenToGif](https://www.screentogif.com/) (Windows): Click **Editor**, drop your PNG frames into it, set the frame delay and save the animation as APNG or GIF. You can set the looping in the save menu.
- [ezgif](https://ezgif.com/) (online, no download): Make a [GIF](https://ezgif.com/maker) or an [APNG](https://ezgif.com/apng-maker) from images, turn a video into a [GIF](https://ezgif.com/video-to-gif) or an [APNG](https://ezgif.com/video-to-apng), or convert [GIF to APNG](https://ezgif.com/gif-to-apng) and [APNG to GIF](https://ezgif.com/apng-to-gif).
- [FFmpeg](https://ffmpeg.org/download.html) (command line): see below.

## With FFmpeg

Turn numbered PNG frames, like `frame_0001.png`, `frame_0002.png` and so on, into an APNG that loops forever. `-framerate 20` plays 20 frames per second:

```bash
ffmpeg -framerate 20 -i frame_%04d.png -plays 0 animation.apng
```

Turn a video into an APNG. `fps=20` keeps 20 frames per second, and `scale=960:-1` makes it 960 pixels wide:

```bash
ffmpeg -i trailer.mp4 -vf "fps=20,scale=960:-1" -plays 0 trailer.apng
```

Turn a video into a GIF that loops forever. The `palettegen` part picks the best 256 colors for it:

```bash
ffmpeg -i trailer.mp4 -vf "fps=15,scale=640:-1:flags=lanczos,split[a][b];[a]palettegen[p];[b][p]paletteuse" -loop 0 trailer.gif
```

Turn a GIF into an APNG:

```bash
ffmpeg -i logo.gif -plays 0 logo.apng
```

To get single frames out of a video, see [Get Frames from Videos](./ffmpeg-frames).

# FMA and AFMA

FMA and AFMA are FancyMenu's own animation formats. Both are deprecated: they still play, but APNG and GIF are the better choice for new animations.

To make an AFMA anyway:

1. Put your frames as PNG files into one folder. They play in the order of their names, like `frame_1.png`, `frame_2.png`, ..., `frame_10.png`.
2. Open **menu bar -> Tools -> AFMA Creator**.
3. Set **Main Frames Directory** to the folder. Frames in **Intro Frames Directory** play once before the main frames.
4. Set **Main Frame Time (ms)** and **Loop Count**. A loop count of `0` loops forever.
5. Set **Output AFMA File** and click **Export**.
