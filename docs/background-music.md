---
title: Menu Background Music
description: Customize music played in menus.
published: true
date: 2026-05-03T11:01:52.000Z
tags:
editor: markdown
dateCreated: 2025-04-14T20:14:14.268Z
---

# Menu Background Music

FancyMenu can disable Vanilla menu music, play a global track list, or use [Audio elements](./elements#audio) for layout-specific music.

# Global Menu Music

Open [**Global Customizations**](./global-customizations) through **Customization -> Global Customizations** outside the layout editor.

Use these settings:

- **Play Vanilla Menu Music** enables or disables Vanilla menu music globally.
- **Custom Menu Music Tracks** manages the global replacement track list.

> [!IMPORTANT]
> Global custom menu tracks play only when no world is loaded, such as on the Title screen. Use an [**Audio** element](./elements#audio) for in-world menu audio.

Global tracks use the Music sound channel. The first track starts after about five seconds; later tracks use a random delay of about one to thirty seconds. Selection is random and avoids immediately repeating the previous track when more than one track is configured.

# Per-Screen Music Control

Add a [**Music Controller** element](./elements#music-controller) to a layout to control Vanilla music for that screen:

1. Right-click the editor background.
2. Select **New Element -> Music Controller**.
3. Configure Menu Music and World Music separately.

The element supports [loading requirements](./conditions).

Disabling menu music with a Music Controller also prevents the global custom menu track list from playing on that screen.

# Custom Music with Audio Elements

Use an [**Audio** element](./elements#audio) when you need:

- Different music on different screens.
- Music in in-world screens.
- Layout requirements, ordered playlists, shuffle settings, volume, or channel control.

Place an [Audio element](./elements#audio) in a [Universal Layout](./universal-layouts) to keep the same player active across supported screens that load that layout. Screen customization must be enabled on each ordinary screen where the universal layout should apply.
