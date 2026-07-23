---
title: Pre-Load Resources
description: How to pre-load resources so they're ready-to-use once the game finishes loading.
published: true
date: 2026-05-03T11:01:52.000Z
tags: 
editor: markdown
dateCreated: 2025-04-14T20:15:46.512Z
---

# Pre-Load Resources

Pre-loading prepares selected resources before a menu needs them. Use it for resources that otherwise flicker, show a black first frame, or start late.

# Add Resources to the Pre-Loader

Open **Customization -> Pre-Load Resources**.

<br>

<img width="350" alt="Screenshot_1" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/3265da80-1bbc-4634-bd94-ba2795d7e3f2">

The list accepts supported image, animation, audio, video, and text resources from local files, web URLs, or resource packs. It does not preload a live [Browser](./elements#browser) page.

The pre-loader starts during game startup and Minecraft resource reloads. It waits for each entry to finish or fail before continuing, with a limit of two minutes per entry.

Loaded resources remain cached until FancyMenu releases resources during a reload or client shutdown. **Customization -> Reload FancyMenu** releases the cache but does not run the pre-loader again.

Pre-loading increases loading time and RAM/VRAM use. Add only resources that must be ready immediately; remove large entries if the client runs out of memory.

<br>

<img width="731" alt="Screenshot_2" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/04632d52-c2a9-4f70-9d0a-e88c4cacc4c1">

# Pre-Loading Slideshows & Panoramas

Adding a [slideshow](./slideshows) loads all of its images and optional overlay. Adding a [panorama](./panoramas) loads all six faces and its optional overlay.

**Customization -> Reload FancyMenu** does not run the pre-loader. Use a Minecraft resource reload or restart the game after changing the preload list.
