---
title: Videos (MP4)
description: What to know about using videos in FancyMenu.
published: true
date: 2025-07-12T15:55:00.928Z
tags: 
editor: markdown
dateCreated: 2025-06-30T21:24:26.869Z
---

# Videos

Since FancyMenu v3.6.0, the mod has support for playing MP4 videos!

There is a Video **element** and a **menu background type** that lets you play videos.

There are also the following **actions** to control video backgrounds and elements:

- **Set Video Element Volume"** to set the volume of a Video element
- **Toggle Video Element Paused State** to toggle the paused state of a Video element
- **Set Video Background Volume** to set the volume of a Video menu background
- **Toggle Video Background Paused State** to toggle the paused state of a Video menu background

And the following **placeholders** to get information about video backgrounds and elements:

- **Video Element Volume** to get the volume of a Video element
- **Video Element Duration** to get the duration of a Video element
- **Video Element Play Time** to get the current play time (progress) of a Video element
- **Video Element Paused State** to get the paused state (true/false) of a Video element
- **Video Background Volume** to get the volume of a Video menu background
- **Video Background Duration** to get the duration of a Video menu background
- **Video Background Play Time** to get the current play time (progress) of a Video menu background
- **Video Background Paused State** to get the paused state (true/false) of a Video menu background

## Requirements

To use the Video element and menu background type, you need to have the **MCEF** mod installed, which is used as backend for video support.

You can download MCEF from [CurseForge](https://www.curseforge.com/minecraft/mc-mods/mcef)¹ and [Modrinth](https://modrinth.com/mod/mcef)².

## Element and Background Shows as Pure Black Instead Of Video

When you see only black instead of the video playing, it is most likely not related to FancyMenu, but MCEF. MCEF probably failed to load correctly, so FancyMenu can't use it.

In this case you should better reach out to the MCEF devs and ask them for help in their Discord: https://discord.gg/rNrh5kW8Ty

The same can happen with the Browser element when MCEF fails to load correctly.

---

¹ https://www.curseforge.com/minecraft/mc-mods/mcef
² https://modrinth.com/mod/mcef