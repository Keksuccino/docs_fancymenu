---
title: Modpacks
description: How to include layouts in a modpack.
published: true
date: 2025-05-07T05:11:28.393Z
tags: 
editor: markdown
dateCreated: 2025-04-14T20:15:20.891Z
---

# FancyMenu in Modpacks

Including your FancyMenu setup in a modpack is very easy and only takes some simple steps.

> [!CAUTION]
> FancyMenu setups can run actions. Import them only from sources you trust.

> [!WARNING]
> This page is **ONLY** for FancyMenu setups made completely in **FancyMenu v3+**, so if you use a legacy setup (made in v2 and converted to v3), some steps could be different.

# Including the FancyMenu Setup in Your Modpack

The main thing you need to do is copy one special folder that FancyMenu uses to save all your designs.

## What you'll need to find

1. **Your "Minecraft Instance" Folder:** This is the main folder on your computer where all the files for a specific Minecraft setup (like the one where you designed your menus) are stored. Launchers like CurseForge and Modrinth call these "instances" or "profiles."
2. **The `config` Folder:** Inside your Minecraft instance folder, there's usually a folder named `config`. This is where many mods store their settings.
3. **The `fancymenu` Folder:** Inside that `config` folder, FancyMenu creates its own folder called `fancymenu`. This is the golden folder we need!

## How to Find the Instance Save Location

### If you use the CurseForge App

1. Open CurseForge.
2. Find your Minecraft profile/instance in the list and open it.
3. Click the three dots.
4. Choose "Open Folder." This will open the main folder for that Minecraft instance.

<img width="630" alt="Screenshot_1" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/curseforge_launcher_instance.png">

### If you use the Modrinth App

1. Open the Modrinth App.
2. Find your Minecraft profile/instance in the list and open it.
3. Click the three dots.
4. Choose "Open Folder." This will open the main folder for that Minecraft instance.

<img width="630" alt="Screenshot_1" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/modrinth_launcher_instance.png">

### For other launchers

Look for a similar "Open Folder," "Open Instance Folder," or "View Files" option for your specific Minecraft setup.

## Copying the FancyMenu Setup

1. Navigate to the `config` folder of your MODPACK instance (the one you want to copy your setup to).
2. If there is a `fancymenu` folder inside, DELETE it.
3. Open the `config` folder of the SOURCE instance (the one you want to use the setup from).
4. Copy the `fancymenu` folder inside the `config` folder of your SOURCE instance to the `config` folder of your MODPACK instance.
5. Done. That's it. Restart your modpack instance now and you should see the setup load.

> [!CAUTION]
> Please keep in mind that old legacy setups made in FancyMenu v2 (even if converted to v3) allowed you to store layout assets outside FancyMenu's `<game-directory>/config/fancymenu/assets/` folder, so in that case you need to make sure you also include all of your assets in the modpack.

# Disabling the Menu Bar and Hotkeys

You surely don't want to keep FancyMenu's menu bar visible in your modpack, so you should disable it. But since people can still press the hotkey to make it visible again, let's do something a little bit more *aggressive*.

Navigate to `<game-directory>/config/fancymenu/options.txt` and open the file in a text editor.

Now set `modpack_mode` to `true` and save the file.
This will completely disable all overlays and hotkeys.

To be able to edit your layouts again, set the config option back to `false`.

# Disabling the Welcome Screen

This shouldn't be needed in most cases, but if you didn't close the Welcome screen yet (the screen that tells you to read the documentation), make sure to set `show_welcome_screen` to `false` in `<game-directory>/config/fancymenu/options.txt`.

The screen only shows once and disables itself when clicking on the **Open Documentation** button, so again, doing this manually shouldn't be needed in most cases.

<br>
<img width="630" alt="Screenshot_1" src="https://github.com/user-attachments/assets/4383b39f-f55a-4eb8-8142-34a425474bb3">
