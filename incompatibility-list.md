---
title: Incompatibility List
description: A list of mods that are known to be incompatible with FancyMenu.
published: true
date: 2025-07-31T18:24:23.684Z
tags: 
editor: markdown
dateCreated: 2025-04-14T20:15:03.963Z
---

# List of Incompatible Mods

The following mods are known to be incompatible with FancyMenu in some way.

Some of the mods have workarounds to make them work with FancyMenu.
If that's the case, it's written after the mod name in the list below.

**In case you found an incompatible mod that isn't part of this list already, please open an issue on GitHub! Thank you very much!**

* [Animated Loading Screen](https://modrinth.com/mod/animated-loading-screen) (Makes menus look bugged)
* [Bedrockify](https://www.curseforge.com/minecraft/mc-mods/bedrockify) (Compatible when you disable all menu modifications of the mod, at least for the menus you want to customize)
* [BetterFPS](https://www.curseforge.com/minecraft/mc-mods/betterfps) (Buttons and menus of this mod aren't customizable)
* [Chat Colors](https://www.curseforge.com/minecraft/mc-mods/chat-colours) (Crash on startup)
* [Chloride](https://modrinth.com/mod/chloride) (FPS placeholder does not work when this mod is installed)
* [Colormatic](https://www.curseforge.com/minecraft/mc-mods/colormatic) (Huge lag when starting MC and breaks FM's audio stuff)
* [Controllable](https://www.curseforge.com/minecraft/mc-mods/controllable) (Custom buttons added to menus with FancyMenu aren't clickable via Controllable's “Virtual Mouse” feature)
* [Controlify](https://modrinth.com/mod/controlify) (Seems to crash the game, but I can't fix that on my end - see [this issue](https://github.com/Keksuccino/FancyMenu/issues/1144) for more context)
* [Crash To Main Menu](https://www.curseforge.com/minecraft/mc-mods/crash-to-main-menu)
* [Custom Loading Screen](https://www.curseforge.com/minecraft/mc-mods/better-loading-screen)
* [Custom Main Menu](https://www.curseforge.com/minecraft/mc-mods/custom-main-menu)
* [Debugify](https://www.curseforge.com/minecraft/mc-mods/debugify) (Use [Modern Debugify](https://www.curseforge.com/minecraft/mc-mods/modern-debugify) instead)
* [Dynamic Surroundings](https://www.curseforge.com/minecraft/mc-mods/dynamic-surroundings) (Breaks FancyMenu's Audio elements, but anything else should work fine)
* [EnhancedVisuals](https://www.curseforge.com/minecraft/mc-mods/enhancedvisuals) (Seems to break animations, makes backgrounds translucent and probably more)
* [Entity Model Features](https://modrinth.com/mod/entity-model-features) (Crashes the game, but I can't fix it on my end - see [this issue](https://github.com/Keksuccino/FancyMenu/issues/1115) for more context)
* [Fossils and Archeology Revival](https://www.curseforge.com/minecraft/mc-mods/fossils) (Works ingame, but the custom main menu isn’t supported—can be disabled in its config)
* [Holographic Renderers](https://www.curseforge.com/minecraft/mc-mods/holographic-renderers) (Crash on startup)
* [Ice and Fire](https://www.curseforge.com/minecraft/mc-mods/ice-and-fire-dragons) (Works if the custom main menu is disabled in its config)
* [Jurassicraft](https://www.curseforge.com/minecraft/mc-mods/jurassicraft) (Crashes on start when enabling customizations for its GUIs—delete them from `config/fancymenu/customizablemenus.txt`)
* [Legacy4J](https://www.curseforge.com/minecraft/mc-mods/legacy-minecraft) (Crashes the game)
* [MalisisCore](https://www.curseforge.com/minecraft/mc-mods/malisiscore) (Breaks main-menu customization)
* [Main Menu Scale Mod](https://www.curseforge.com/minecraft/mc-mods/main-menu-scale)
* [MCA Reborn](https://www.curseforge.com/minecraft/mc-mods/minecraft-comes-alive-reborn) (Works, but some of its menus break FM's menu bar and/or are not customizable)
* [Minecraft Comes Alive](https://www.curseforge.com/minecraft/mc-mods/minecraft-comes-alive-mca) (Works fine, but its menus aren’t customizable)
* [MineTogether](https://www.curseforge.com/minecraft/mc-mods/creeperhost-minetogether) (Seems to break layouts when GUI scale > 2)
* [Mod Menu](https://www.curseforge.com/minecraft/mc-mods/modmenu) (**WORKS FINE** in most cases, but if you experience a duplicated or uncustomizable Mods button, change your Mod Menu button settings to "Adjacent": Main Menu > Mods > Mod Menu > Mods Button: Adjacent)
* [Modern Online Picture Frames](https://www.curseforge.com/minecraft/mc-mods/online-picture-frame) (Crash—see [this issue](https://github.com/Keksuccino/FancyMenu/issues/776))
* [Not Enough Animations](https://www.curseforge.com/minecraft/mc-mods/not-enough-animations) (Works fine in 1.16+, but breaks 1.12)
* **OptiFine** (Breaks the mod! Use [these alternatives](./optifine-alternatives) instead)
* [Optiscale](https://www.curseforge.com/minecraft/mc-mods/optiscale) (Breaks FancyMenu's UI; buttons aren’t clickable)
* [Pack Menu](https://www.curseforge.com/minecraft/mc-mods/packmenu)
* [Panorama Screens](https://modrinth.com/mod/panorama-screens) (Will not work and cause problems, because stacking menu customization mods is never a good idea)
* [QuestCraft](https://github.com/QuestCraftPlusPlus/QuestCraft) (Game fails to load)
* [RandomPatches](https://www.curseforge.com/minecraft/mc-mods/randompatches-forge) (Works if `patchMinecraftClass = false` in its config)
* [Remove Reloading Screen](https://www.curseforge.com/minecraft/mc-mods/rrls) (Breaks FM and Drippy. Don't use that mod.)
* [Replay Mod](https://www.replaymod.com/download/) (Works when you set `mainMenuButton` to **BIG** in `.minecraft/config/replaymod.json`)
* [Seamless Loading Screen](https://www.curseforge.com/minecraft/mc-mods/seamless-loading-screen) (Crashes the game)
* [Slight Gui Modifications](https://www.curseforge.com/minecraft/mc-mods/slight-gui-modifications)
* [Skin Layers 3D](https://www.curseforge.com/minecraft/mc-mods/skin-layers-3d) (Works fine in 1.16+, but breaks 1.12)
* [Smooth Scrolling Everywhere](https://www.curseforge.com/minecraft/mc-mods/smooth-scrolling-everywhere)
* [Sound Filters](https://www.curseforge.com/minecraft/mc-mods/sound-filters) (The audio extension will not work with this installed)
* [Sound Physics Remastered](https://www.curseforge.com/minecraft/mc-mods/sound-physics-remastered) (The audio extension will not work with this installed)
* [Stylish Effects](https://www.curseforge.com/minecraft/mc-mods/stylish-effects) (Main menu fails to load layouts the first time it’s shown)
* [Supplementaries](https://www.curseforge.com/minecraft/mc-mods/supplementaries) (Randomly crashes when customizing its config screen; delete the problematic layout from `.minecraft/config/fancymenu/customization`)
* [Terraria Craft](https://www.curseforge.com/minecraft/mc-mods/terraria-craft)
* [The Dalek Mod](https://www.curseforge.com/minecraft/mc-mods/the-dalek-mod) (Works if its custom main menu is disabled in the config)
* [ThonkUtil](https://www.curseforge.com/minecraft/mc-mods/thonkutil) (Works, but currently adds an unremovable text to the main menu)
* [Trade Uses](https://modrinth.com/mod/trade-uses) (Causes crashes in villager trade menu—possibly only when “Easy Villagers” is also installed)
* [VanillaFix](https://www.curseforge.com/minecraft/mc-mods/vanillafix) (Usable, but some users report issues with the VanillaFix crash screen)
* [FireplaceMode](https://www.curseforge.com/minecraft/mc-mods/fireplacemode) (The Pause screen resets its customizations sometimes with this mod installed)