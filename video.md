---
title: Videos (MP4)
description: What to know about using videos in FancyMenu.
published: true
date: 2026-05-03T11:01:52.000Z
tags: 
editor: markdown
dateCreated: 2025-06-30T21:24:26.869Z
---

# Videos

FancyMenu supports playing MP4 videos as elements, menu backgrounds and Game Intro content.

FancyMenu 3.9.0 adds a new native **Video** element and **Video** menu background powered by Watermedia V3. The old **Video [MCEF]** element/background type is deprecated and should only be kept for old layouts that still need it.

There are also the following **actions** to control video backgrounds and elements:

- **Set Video Element Volume** to set the volume of a Video element
- **Set Video Element Play Time** to seek a Video element to a millisecond timestamp
- **Toggle Video Element Paused State** to toggle the paused state of a Video element
- **Set Video Background Volume** to set the volume of a Video menu background
- **Set Video Background Play Time** to seek a Video menu background to a millisecond timestamp
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

The duration and play-time placeholders return `MM:SS` by default. Set `output_as_timestamp` to `true` when you need millisecond timestamps. Play-time placeholders can still use `show_percentage` for 0-100 progress values.

FancyMenu 3.9.0 also adds the **On Video Playback Status Changed** listener, which can react to `PLAYING`, `PAUSED`, `STOPPED` and `FINISHED`.

## Requirements

To use the new native Video element and menu background type, you need to install:

- **Watermedia V3**
- **Watermedia Binaries V3**

These are optional dependencies, so they must be added to the instance manually if you want video support.

The deprecated **Video [MCEF]** type still uses MCEF. For new layouts, use the native Watermedia-powered Video type instead.

## Videos in Loading Screens

Video support does NOT work in loading screens (game/resource loading screen & world loading screen).

This also means that you should NOT add videos to the game loading screen via **Drippy Loading Screen**, since it will not work in most cases.

You should use short, simple AFMA/FMA files in loading screens instead, since users don't notice them getting reloaded in most cases when the animation is simple and short enough.

## Troubleshooting

If you have issues with native video support, first confirm that both Watermedia V3 and Watermedia Binaries V3 are installed and match your Minecraft/modloader version.
