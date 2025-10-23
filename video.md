---
title: Videos (MP4)
description: What to know about using videos in FancyMenu.
published: true
date: 2025-10-23T07:58:38.201Z
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

You can download MCEF from the official project pages on [CurseForge](https://www.curseforge.com/minecraft/mc-mods/mcef) and [Modrinth](https://modrinth.com/mod/mcef).

For newer Minecraft versions (1.21.5+), the official MCEF projects do not provide builds, but there is a fork with builds for latest Minecraft versions, which can be found [here](https://www.curseforge.com/minecraft/mc-mods/mcef-keksuccino) (CurseForge) and [here](https://modrinth.com/mod/mcef-keksuccino) (Modrinth). This fork is maintained by Keksuccino, to get builds for latest Minecraft versions out as fast as possible.

## Videos in Loading Screens

Video support does NOT work in loading screens (game/resource loading screen & world loading screen).

This also means that you should NOT add videos to the game loading screen via **Drippy Loading Screen**, since it will not work in most cases.

You should use short, simple FMA files in loading screens instead, since users don't notice it getting reloaded in most cases when the animation is simple and short enough (it will still be stuck for a moment or flicker, but better than having a long animation start from the beginning again after reload).

## Troubleshooting

If you have issues with video support, make sure to ask in FancyMenu's Discord server for help instead of asking in the MCEF Discord server, since many issues come from FancyMenu's side and not MCEF.