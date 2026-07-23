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

FancyMenu supports playing MP4 videos as [elements](./elements#video), [menu backgrounds](./menu-backgrounds), and [Game Intro](./game-intro) content.

The native [**Video** element](./elements#video) and **Video** menu background use Watermedia V3. The old **Video [MCEF]** types are deprecated and should only remain in layouts that still need them.

There are also the following **actions** to control video backgrounds and elements:

- [**Set Video Element Volume**](./action-scripts#set-video-element-volume-set_video_element_volume) sets the volume of a Video element.
- [**Set Video Element Play Time**](./action-scripts#set-video-element-play-time-set_video_element_play_time) seeks a Video element to a millisecond timestamp.
- [**Toggle Video Element Paused State**](./action-scripts#toggle-video-element-paused-state-toggle_video_element_pause_state) toggles a Video element's paused state.
- [**Set Video Background Volume**](./action-scripts#set-video-background-volume-set_video_menu_background_volume) sets a Video menu background's volume.
- [**Set Video Background Play Time**](./action-scripts#set-video-background-play-time-set_video_menu_background_play_time) seeks a Video menu background to a millisecond timestamp.
- [**Toggle Video Background Paused State**](./action-scripts#toggle-video-background-paused-state-toggle_video_menu_background_pause_state) toggles a Video menu background's paused state.

And the following **placeholders** to get information about video backgrounds and elements:

- [**Video Element Volume**](./placeholders#video-element-volume-video_element_vol) returns a Video element's volume.
- [**Video Element Duration**](./placeholders#video-element-duration-video_element_duration) returns a Video element's duration.
- [**Video Element Play Time**](./placeholders#video-element-play-time-video_element_playtime) returns a Video element's current progress.
- [**Video Element Paused State**](./placeholders#video-element-paused-state-video_element_paused_state) returns whether a Video element is paused.
- [**Video Background Volume**](./placeholders#video-background-volume-video_background_vol) returns a Video menu background's volume.
- [**Video Background Duration**](./placeholders#video-background-duration-video_background_duration) returns a Video menu background's duration.
- [**Video Background Play Time**](./placeholders#video-background-play-time-video_background_playtime) returns a Video menu background's current progress.
- [**Video Background Paused State**](./placeholders#video-background-paused-state-video_background_paused_state) returns whether a Video menu background is paused.

The duration and play-time placeholders return `MM:SS` by default. Set `output_as_timestamp` to `true` when you need millisecond timestamps. Play-time placeholders can still use `show_percentage` for 0-100 progress values.

Volume and paused-state values are controller metadata associated with the identifier. Duration and play-time values require the matching Video element or background to be active and ready on the current screen.

The [**On Video Playback Status Changed** listener](./listeners#on-video-playback-status-changed-video_playback_status_changed) can react to `PLAYING`, `PAUSED`, `STOPPED`, and `FINISHED`.

## Requirements

To use the new native Video element and menu background type, you need to install:

- **Watermedia V3**
- **Watermedia Binaries V3**

These are optional dependencies, so they must be added to the instance manually if you want video support.

Native video playback also requires an OpenGL renderer. Watermedia playback is unavailable while Minecraft uses Vulkan; switch to OpenGL to use Video elements, Video menu backgrounds, and [video Game Intros](./game-intro).

The deprecated **Video [MCEF]** type still uses MCEF. For new layouts, use the native Watermedia-powered Video type instead.

## Videos in Loading Screens

Video support does NOT work in loading screens (game/resource loading screen & world loading screen).

This also means that you should NOT add videos to the game loading screen via **Drippy Loading Screen**, since it will not work in most cases.

Use short, simple [AFMA/FMA animations](./fma) in loading screens instead.

## Troubleshooting

If native video does not play, confirm that Watermedia V3 and Watermedia Binaries V3 match your Minecraft/modloader version and that Minecraft is using OpenGL instead of Vulkan.
