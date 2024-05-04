---
title: Modpacks
description: How to include layouts in a modpack.
published: true
date: 2024-05-04T10:30:53.642Z
tags: 
editor: markdown
dateCreated: 2023-12-22T05:28:46.511Z
---

# FancyMenu in Modpacks

Including your FancyMenu setup in a modpack is very easy and only takes some simple steps.

> This page is **ONLY** for FancyMenu setups made completely in **FancyMenu v3+**, so if you use a legacy setup (made in v2 and converted to v3), some steps could be different.
{.is-warning}

# Copy-Pasting the Setup

Including a FancyMenu setup in a modpack is nothing more than copying a config folder.

All you need to do is copy the `/config/fancymenu/` folder from your Minecraft instance to the `config` directory of your modpack, so in other words you simply include FancyMenu's config folder, which is something almost all modpack systems can do by default, so just google how to include mod configs in your modpack system (CurseForge, Modrinth, etc.).

That's it. Nothing more you need to do.

But please keep in mind that old legacy setups made in FancyMenu v2 (even if converted to v3) allowed you to store layout assets outside of FancyMenu's `/config/fancymenu/assets/` folder, so in that case you need to make sure you also include all of your assets.

# Disabling the Menu Bar and Hotkeys

You surely don't want to keep FancyMenu's menu bar visible in your modpack, so you should disable it. But since people can still press the hotkey to make it visible again, let's do something a little bit more *aggressive*.

Navigate to `/config/fancymenu/options.txt` and open the file in a text editor.

Now set `modpack_mode` to `true` and save the file.
This will completely disable all overlays and hotkeys.

To be able to edit your layouts again, set the config option back to `false`.

