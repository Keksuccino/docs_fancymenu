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

# Bringing Your Setup Into the Modpack

The easiest way to move your setup from the instance you designed it in to your modpack instance is a [profile](./profiles):

1. In the instance with your setup, open **menu bar -> Customization -> Profiles**, select your setup, and [export](./profiles#exporting) it as `.fmp` file.
2. In your modpack instance, open the Profiles window and [import](./profiles#importing) the `.fmp` file, for example by dragging it onto the window.
3. Select the imported profile and click **Load Profile**.

The FancyMenu setup the modpack instance had before doesn't get lost. It stays available as its own profile, so you can always switch back.

# Shipping the Setup With Your Modpack

The loaded profile is the content of `<game-directory>/config/fancymenu/`, so it ships with your modpack's `config` folder, like the configs of other mods.

All other profiles of the instance are stored in `<game-directory>/config/fancymenu/profiles/`. Delete the profiles players shouldn't get before exporting your modpack, or leave the `profiles` folder out of the modpack export.

> [!CAUTION]
> Please keep in mind that old legacy setups made in FancyMenu v2 (even if converted to v3) allowed you to store layout assets outside FancyMenu's `<game-directory>/config/fancymenu/assets/` folder. Profiles only contain FancyMenu's config folder, so in that case you need to make sure you also include all of your assets in the modpack.

## How to Find the Instance Folder

The instance folder is the main folder on your computer where all the files of a specific Minecraft setup are stored. Launchers like CurseForge and Modrinth call these "instances" or "profiles" (not to be confused with FancyMenu's profiles).

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
