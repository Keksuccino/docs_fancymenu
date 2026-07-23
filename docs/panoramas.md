---
title: Panoramas
description: How to make and use custom background panoramas.
published: true
date: 2025-04-14T20:15:36.113Z
tags: 
editor: markdown
dateCreated: 2025-04-14T20:15:33.094Z
---

# Cubic Panoramas

FancyMenu supports loading custom 6-image panorama cubes as background for menus.

These panoramas are a special cubic panorama format used by Minecraft as background in the Title screen and is built out of 6 images (sides) that get rendered as cube (or skybox, to be more specific).

> **IMPORTANT**: If you're on Windows, don't forget to turn on [file extensions](https://cdn.discordapp.com/attachments/795308330746511390/801561308012347482/unknown.png), because otherwise you will not be able to see important parts of file names later!
{.is-warning}

# Making a Panorama

If you don't know how Minecraft handles their background panoramas and how to create these, you should check out [this video](https://www.youtube.com/watch?v=F7jMd3zsjZQ&t).
It will give you a very good understanding of how Minecraft's panoramas work and how to make one!

After watching the video, you will notice that creating these panoramas can be a bit time-consuming.
To save you some time, maybe think about using a mod that creates them for you.
You can find some of them by searching for `minecraft panorama mod`, but one of them is [Panoramica](https://www.curseforge.com/minecraft/mc-mods/panoramica) (made by me).

# Preparing the Panorama

After you got your 6 panorama images, you'll need to move them to the right place!

FancyMenu's panorama directory is `<game-directory>/config/fancymenu/panoramas/`.

`<game-directory>` is the active launcher instance, which is not always the default `.minecraft` directory.

## The Panorama Folder

Every panorama has its own folder.
Create a new folder in `<game-directory>/config/fancymenu/panoramas/` for every panorama.
In my example, I will name the folder `mypanorama`.

![1](https://user-images.githubusercontent.com/35544624/100791916-2802d380-341a-11eb-8e32-f9913e93a38c.png)

## Folder Content

After creating the folder, you will need to fill it.

### Properties File
Every panorama needs a properties file to work.
This file always needs to be named `properties.txt` and needs some important things written to it.

The content of a panorama properties file should always look like this:
```
type = panorama

panorama-meta {
  name = name_of_your_panorama
  speed = 1.0
  fov = 85.0
  angle = 25.0
  start_rotation = 0
}
```
Keep the `type = panorama` line and the `panorama-meta` section. Edit the listed values rather than the structural lines.

#### name
This is the case-sensitive identifier used to select the panorama. It is required and must be unique; duplicate names make only one panorama available.

#### speed
The rotation-speed multiplier. `1.0` is the default, `2.0` is twice as fast, and `0.5` is half as fast. Use a value greater than `0`.

#### fov
The field of view in degrees. The default is `85.0`.

#### angle
The vertical viewing angle in degrees. The default is `25.0`.

#### start_rotation
The initial horizontal rotation in degrees, from `0` to `360`.

<br>

### Panorama Image Folder

The second mandatory thing your panorama folder needs is the actual image folder containing your panorama images.

This folder's name needs to be `panorama`.

Put exactly six panorama images in it, named `panorama_0.png` through `panorama_5.png`. These names are exact and can be case-sensitive depending on the filesystem.

![3](https://user-images.githubusercontent.com/35544624/100791922-29340080-341a-11eb-8174-874a180d0485.png)

> Only PNGs are supported as panorama images!
{.is-warning}

### Panorama Overlay

The last step is **optional** and can be skipped if you don't want an overlay over your panorama.

If you want to add a vignette or another overlay, add a PNG named exactly `overlay.png` next to `properties.txt`.

### Checking Everything Again

You should now have this structure. The files belong inside the individual `mypanorama` directory, not directly in the shared `panoramas` directory.

```text
<game-directory>/config/fancymenu/panoramas/
└── mypanorama/
    ├── properties.txt
    ├── overlay.png          # optional
    └── panorama/
        ├── panorama_0.png
        ├── panorama_1.png
        ├── panorama_2.png
        ├── panorama_3.png
        ├── panorama_4.png
        └── panorama_5.png
```

![2](https://user-images.githubusercontent.com/35544624/100791920-29340080-341a-11eb-8e26-98a7fd2ad7eb.png)

# Using the Panorama

After (re)starting the game or reloading FancyMenu via **Customization -> Reload FancyMenu**, you should now be able to set your panorama as menu background. To do this, right-click the layout editor background and click on **Menu Background**.
