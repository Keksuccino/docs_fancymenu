---
title: Global Customizations
description: Apply global FancyMenu tweaks that affect all screens.
published: true
date: 2026-05-03T11:01:52.000Z
tags:
editor: markdown
dateCreated: 2026-05-03T11:01:52.000Z
---

# Global Customizations

Global Customizations apply shared UI and startup settings without editing each screen layout. They work even when normal screen customization is disabled.

Common examples:

- Use one shared button and slider style for all screens.
- Replace menu background, panorama, and menu music globally.
- Apply global startup/window behavior (GUI scale, fullscreen, window title/icon).
- Replace vanilla button textures globally without a resource pack.
- Replace vanilla menu music globally without a resource pack.

# Where To Find Them

Open FancyMenu's **menu bar** while **not** in the layout editor, then **Customization -> Global Customizations**.

# What You Can Customize

## Global behavior and startup

- [**Game Intro**](./game-intro) (an intro video or animation that plays before the Title screen)
- **Singleplayer Screen World Icons**
- **Multiplayer Screen Server Icons**
- [**Seamless World Loading**](./seamless-world-loading) (uses a recent world screenshot as the loading-screen background)
- [**Custom Window Icon**](./window-customization#custom-icon)
- [**Custom Window Title**](./window-customization#custom-title)
- **Default GUI Scale**
- **Force Fullscreen on Launch**

## Button visuals

- **Custom Button Textures** (Normal/Hover/Inactive states, transparent mode, [nine-slice](./nine-slicing-and-tiling) + border sizes)
- **Button Labels** (underline-on-hover, base/hover color, scale, shadow)

## Slider visuals

- **Custom Slider Textures**
- **Slider Background Texture** (texture, transparent mode, [nine-slice](./nine-slicing-and-tiling) + border sizes)
- **Slider Handle Textures** (Normal/Hover/Inactive states, [nine-slice](./nine-slicing-and-tiling) + border sizes)
- **Slider Labels** (underline-on-hover, base/hover color, scale, shadow)

## Menu visuals and audio

- [**Custom Menu Background Texture**](./menu-backgrounds)
- [**Custom Menu Background Panorama**](./panoramas)
- **Play Vanilla Menu Music** (enable/disable playing Vanilla menu music)
- [**Custom Menu Music Tracks**](./background-music)
- **Custom Button/Slider Click Sound**

# Custom Menu Music Tracks

Use **Custom Menu Music Tracks** to build a randomized track list for menus.

> [!IMPORTANT]
> Global custom menu tracks play only when no world is loaded, such as on the Title screen. Use an [**Audio** element](./elements#audio) for in-world menu audio.

Configured tracks use the Music sound channel and replace Vanilla menu music in supported non-world menus.

- The first track starts after about five seconds.
- Later tracks start after a random delay of about one to thirty seconds.
- Tracks are selected randomly.
- With multiple tracks, the previous track is not selected twice in a row.

Manage the track list from **Custom Menu Music Tracks**:

- Open **Custom Menu Music Tracks** to open **Manage Menu Music Tracks**.
- Use **Add Track** to add audio sources.
- Use **Remove Track** to remove one entry.
- Use **Clear Tracks** to remove all entries.
