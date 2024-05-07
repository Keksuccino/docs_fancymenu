---
title: Animations (FMA)
description: How to make and use FMA (FancyMenu Animation) files.
published: true
date: 2024-05-07T04:47:51.393Z
tags: 
editor: markdown
dateCreated: 2024-05-04T08:44:18.533Z
---

# Animations

FMA files are special animated texture files created for FancyMenu.
They are pretty much the same as APNGs, but way more optimized for FancyMenu.

> This feature only exists in FancyMenu v3.2.0+!
{.is-warning}

# Making an FMA

Making an FMA file is as easy as creating a ZIP file! Well, that's mostly because it _is_ a ZIP file under the hood.

## File Extensions

You need to see file extensions to be able to follow this documentation, so make sure to **ENABLE FILE EXTENSIONS** before you start.

On Windows, this works by opening a random folder and then clicking on the arrow on the top-right side to extend the menu below.

Then go to the **View** tab and enable **File Name Extensions**.

<br>
<img width="764" alt="Screenshot_9" src="https://gist.github.com/assets/35544624/1f0a0864-1ad8-4f63-be3a-ab18385539e6"> 

## Preparation

Lets start with creating a new folder for the content of the FMA file.
In this example, lets call the folder `fancymenu_animation`.

In this folder, create two more folders. The first folder **has** to be called `frames` and the second folder **has** to be called `intro_frames`.

Now in the same folder, create a new TXT file and rename it to `metadata.json`.
Please make sure the file is not still a TXT file. You **have to** change the file extension to `json`.

Now you should have a folder called `fancymenu_animation` and in this folder are a folder called `frames`, a folder called `intro_frames` and a JSON file called `metadata.json`.

<br>
<img width="700" alt="Screenshot_3" src="https://gist.github.com/assets/35544624/e29f6666-ee4a-4d79-b7e2-1b640f40ce78">

## The Metadata JSON

This is the file that tells FancyMenu how it should handle your FMA texture.
It contains information such as the frame times (how long a frame is visible) and the loop count.

Please open the `metadata.json` file with a text editor.

Copy this text to the file:

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

This is the basic template of how the file should look like.
Now you can customize it to your liking.

### `loop_count`

This is to control how many times the texture should loop (restart it's animation).

Setting this to `0` means it will loop indefinitely. It will *never stop*.

Everything bigger than `0` means how many times the texture plays. So for example, setting the value to `1` means the texture will only play once, then stops at the last frame, `2` means it will play two times, then stop at the last frame *and so on*.

### `frame_time`

This is the universal frame time in **milliseconds** for the frames of the animated texture.
Frame time means how long the frame is visible before the animation goes to the next frame.

### `frame_time_intro`

This is basically the same as `frame_time`, but for the **intro** frames of your animated texture.
Intro frames are **optional** and you will learn more about them later.

### `custom_frame_times`

This is **optional** and can be used for overriding the frame time for specific (non-intro) frames.
For example, you want all your frames to show for `41` milliseconds, so you set `frame_time` to `41`, but you want the first and second frames to show for `5000` milliseconds.

In that case, you would do this:

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

Frames are zero-based, which means the first frame of the animation is `0`, the second one is `1` and so on.

There needs to be a **comma** at the end of every custom frame time entry, **except** of the last one!

### `custom_frame_times_intro`

This is exactly the same as `custom_frame_times`, but in this case for the **intro** frames. Intro frames are **optional** and you will learn more about them later.

That's it for the `metadata.json` file. Save it now and close the text editor.

## The Frames

The frames of your animated texture go into the `frames` folder.

Frames need to be **PNG FILES**! There is **NO SUPPORT FOR JPEG AND OTHER FORMATS**!

Every frame **has to** be called just the number of the frame and the file extension.
The first frame should be called `0.png`, the second one `1.png`, the third one `2.png` and so on.
The texture will **NOT WORK** if the frames have invalid file names!

<br>
<img width="574" alt="Screenshot_4" src="https://gist.github.com/assets/35544624/eac54695-b57a-4919-8740-4e5c8aad649c">

## The Intro

This feature is **OPTIONAL**.

The **intro** feature of FMA files is a special way to play some frames **before** the actual frames of the `frames` folder start playing. 

The intro will **never loop** and only plays the very first time the animation plays, which allows you to play something like a fade-in animation before the actual animation starts playing in a loop.

Intro frames go into the `intro_frames` folder and work the same as normal frames:

Frames need to be **PNG FILES**! There is **NO SUPPORT FOR JPEG AND OTHER FORMATS**!

Every frame **has to** be called just the number of the frame and the file extension.
The first frame should be called `0.png`, the second one `1.png`, the third one `2.png` and so on.
The texture will **NOT WORK** if the frames have invalid file names!

## Packing the FMA File

Now everything important is in the `fancymenu_animation` folder, so you can pack your FMA file now!

Packing the FMA file basically just means to pack the folder content to a ZIP file.
The content needs to be in the **ROOT of the ZIP** file, so it can't be in an extra folder inside the ZIP.

On Windows, the easiest way to pack your FMA content to a ZIP file is by selecting everything in the `fancymenu_animation` folder and then **right-clicking** the `metadata.json` file. In the context menu that opens, click on **Send To -> Compressed ZIP Folder**.

<br>
<img width="752" alt="Screenshot_6" src="https://gist.github.com/assets/35544624/5b7e7670-5403-410e-943c-283bfe6d585c">

Now there should be a new ZIP file in the `fancymenu_animation` folder called `metadata.zip`, `frames.zip` or `intro_frames.zip`.

<br>
<img width="700" alt="Screenshot_7" src="https://gist.github.com/assets/35544624/987f7989-dff7-43b4-a54c-0898969827f5">

When you open this file, its content should look like this:

<img width="700" alt="Screenshot_8" src="https://gist.github.com/assets/35544624/f1642a39-e14c-47a7-90f6-8a737e8ec75f">

Now you need to rename the file to `fancymenu_animation.fma`. Make sure to REPLACE the `.zip` with `.fma`, so it's not a ZIP anymore.

Of course you can change the `fancymenu_animation` part to whatever you want, but make sure it stays a `.fma` file!

That's it! You now have a (hopefully) working FMA file!

# Using FMA Files in FancyMenu

> **IMPORTANT**: FMA files are **NOT the same** as the **deprecated Animations** menu background type! FMA files are an animated **texture** format, so you add them as an Image/Texture files, just like you do with PNGs, JPEGs, GIFs and APNGs.
{.is-warning}

You can use FMA files like any other animated texture format. FancyMenu sees it as normal texture/image, so you can use it everywhere you can set a texture to something.

Make sure the FMA file is in the `/config/fancymenu/assets/` folder, because FancyMenu can only pick textures and other resources from its `assets` folder.