---
title: Animations
description: How to make and use FMA (FancyMenu Animation) files.
published: true
date: 2024-05-04T09:38:00.919Z
tags: 
editor: markdown
dateCreated: 2024-05-04T08:44:18.533Z
---

# WIP !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

<br>
<br>
<br>
<br>


# Animations

FMA files are special animated texture files created for FancyMenu.
They are pretty much the same as APNGs, but way more optimized for FancyMenu.

# Making an FMA

Making an FMA file is as easy as creating a ZIP file! Well, that's mostly because it _is_ a ZIP file under the hood.

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

On Windows, the easiest way to create a new (empty) ZIP file is by right-clicking some random icon on your desktop, then **Send To -> Compressed ZIP Folder**.

Now open this ZIP file and move all the content of your `fancymenu_animation` folder into the ZIP file like that:


