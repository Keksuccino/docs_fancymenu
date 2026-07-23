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

In some scenarios it is recommended to pre-load resources.
This is mostly needed for high resolution images, audio files and web resources in general.

Pre-loading resources can help to remove possible image flickering or audio files not starting fast enough.

It is also recommended to pre-load animations (AFMA/FMA files) to make them play smoothly and not lag or show a black screen when first loaded.

# Add Resources to the Pre-Loader

To add a resource to FancyMenu's resource pre-loader, just click on **Pre-Load Resources** in **Customization**.

<br>

<img width="350" alt="Screenshot_1" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/3265da80-1bbc-4634-bd94-ba2795d7e3f2">

This will open a menu that lets you add local resources, web resources and resource pack resources to a list.

Resources in this list are loaded during startup and Minecraft resource reloads. This increases loading time and memory use, so only add resources that must appear immediately.

<br>

<img width="731" alt="Screenshot_2" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/04632d52-c2a9-4f70-9d0a-e88c4cacc4c1">

# Pre-Loading Slideshows & Panoramas

Adding a slideshow loads all of its images and optional overlay. Adding a panorama loads all six faces and its optional overlay.

**Customization -> Reload FancyMenu** does not run the pre-loader. Use a Minecraft resource reload or restart the game after changing the preload list.
