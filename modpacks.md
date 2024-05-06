---
title: Modpacks
description: How to include layouts in a modpack.
published: true
date: 2024-05-06T06:21:40.675Z
tags: 
editor: markdown
dateCreated: 2023-12-22T05:28:46.511Z
---

# Integrating FancyMenu into Modpacks

This page is specifically about integrating FancyMenu setups created with FancyMenu v3 or later into your modpacks. If your setup was originally created in v2 and later converted to v3, please note that some steps might differ.

## How to Include a FancyMenu Setup in Your Modpack

To include a FancyMenu setup with all its layouts and settings into your modpack, you simply need to include its `config` folder.

1. **Locate the Config Folder:**
   - Navigate to the root directory of the Minecraft instance where you made your FancyMenu layouts in.
   - Open the `config` folder.

2. **Copy the FancyMenu Folder:**
   - Inside the `config` folder, find and copy the `fancymenu` folder to a temporary location like your desktop.

3. **Prepare the Modpack Config Folder:**
   - Go to the `config` folder of your modpack's Minecraft instance.
   - If a `fancymenu` folder already exists here, delete it.

4. **Transfer the FancyMenu Folder:**
   - Move the `fancymenu` folder from your temporary location to the `config` folder of the modpack instance.

And that's it! Your modpack is now *fancy*!

> Legacy layouts made with FancyMenu v2 (even if converted to v3) may have layout assets stored outside the default `/config/fancymenu/assets/` directory. Ensure that all necessary assets are included in your modpack.
{.is-warning}

# Disabling Menu Bar and Hotkeys

When using FancyMenu in a modpack it's recommended to disable FancyMenu's hotkeys and overlays, so people have a harder time messing with your menu designs.

1. **Find and Open FancyMenu's Options File:**
   - Navigate to `/config/fancymenu/options.txt`.
   - Open this file in a text editor.

2. **Enable the Modpack Mode:**
   - Change the value of `modpack_mode` to `true` and save the file. This disables all FancyMenu overlays and hotkeys.

## Re-enabling Editing

Should you need to adjust layouts in the future, simply set `modpack_mode` back to `false`.
