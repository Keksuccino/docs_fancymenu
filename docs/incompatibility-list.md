---
title: Incompatibility List
description: Screens blocked by FancyMenu and community-reported incompatibilities.
---
# Screens Where Customization Is Intentionally Disabled

FancyMenu blocks screens matching certain mod package paths to prevent crashes or broken behavior. The customization toggle, overlay, and layouts are unavailable on matching screens.

These blocks use the screen class's Java package rather than a hand-picked list of individual screens. One rule can therefore affect several screens from the same mod or related packages.

Blocked screen groups include:

- Create
- Panoramica
- Alex's Mobs
- Screenshot Viewer
- Twilight Forest
- Supplementaries
- OptiFine; use [OptiFine Alternatives](./optifine-alternatives)
- SlimeKnights and Tinkers' Construct
- MidnightDust mods
- SkinSwapper
- Immersive Engineering
- Dungeonz
- RPG-Hud
- Cobblemon and some Cobblemon-related screens
- Applied Energistics 2
- Xaero's map mods

# Community-Reported Incompatibilities

The entries below are community reports, not screens blocked by FancyMenu itself. Compatibility can change with the FancyMenu, Minecraft, loader, and mod versions in a pack.

* [Animated Loading Screen](https://modrinth.com/mod/animated-loading-screen) (Makes menus look bugged)
* [Animated Mojang Logo](https://www.curseforge.com/minecraft/mc-mods/animated-mojang-logo) (Layouts will sometimes not load; Also breaks Drippy Loading Screen)
* [Bedrockify](https://www.curseforge.com/minecraft/mc-mods/bedrockify) (Compatible when you disable all menu modifications of the mod, at least for the menus you want to customize)
* [BetterFPS](https://www.curseforge.com/minecraft/mc-mods/betterfps) (Buttons and menus of this mod aren't customizable)
* [Chat Colors](https://www.curseforge.com/minecraft/mc-mods/chat-colours) (Crash on startup)
* [Chloride](https://modrinth.com/mod/chloride) (FPS placeholder does not work when this mod is installed)
* [Colormatic](https://www.curseforge.com/minecraft/mc-mods/colormatic) (Huge lag when starting MC and breaks FM's audio stuff)
* [Controllable](https://www.curseforge.com/minecraft/mc-mods/controllable) (Custom buttons added to menus with FancyMenu aren't clickable via Controllable's “Virtual Mouse” feature)
* [Controlify](https://modrinth.com/mod/controlify) (Reported crash; see [issue #1144](https://github.com/Keksuccino/FancyMenu/issues/1144))
* [Crash To Main Menu](https://www.curseforge.com/minecraft/mc-mods/crash-to-main-menu)
* [Custom Loading Screen](https://www.curseforge.com/minecraft/mc-mods/better-loading-screen)
* [Custom Main Menu](https://www.curseforge.com/minecraft/mc-mods/custom-main-menu)
* [Debugify](https://www.curseforge.com/minecraft/mc-mods/debugify) (Use [Modern Debugify](https://www.curseforge.com/minecraft/mc-mods/modern-debugify) instead)
* [Dynamic Surroundings](https://www.curseforge.com/minecraft/mc-mods/dynamic-surroundings) (Reported to break Audio elements)
* [EnhancedVisuals](https://www.curseforge.com/minecraft/mc-mods/enhancedvisuals) (Reported animation and translucent-background problems)
* [Entity Model Features](https://modrinth.com/mod/entity-model-features) (Reported crash; see [issue #1115](https://github.com/Keksuccino/FancyMenu/issues/1115))
* [Fossils and Archeology Revival](https://www.curseforge.com/minecraft/mc-mods/fossils) (Works ingame, but the custom main menu isn’t supported—can be disabled in its config)
* [Holographic Renderers](https://www.curseforge.com/minecraft/mc-mods/holographic-renderers) (Crash on startup)
* [Ice and Fire](https://www.curseforge.com/minecraft/mc-mods/ice-and-fire-dragons) (Works if the custom main menu is disabled in its config)
* [Jurassicraft](https://www.curseforge.com/minecraft/mc-mods/jurassicraft) (Crashes on start when enabling customizations for its GUIs—delete them from `<game-directory>/config/fancymenu/customizablemenus.txt`)
* [Legacy4J](https://www.curseforge.com/minecraft/mc-mods/legacy-minecraft) (Crashes the game)
* [MalisisCore](https://www.curseforge.com/minecraft/mc-mods/malisiscore) (Breaks main-menu customization)
* [Main Menu Scale Mod](https://www.curseforge.com/minecraft/mc-mods/main-menu-scale)
* [MCA Reborn](https://www.curseforge.com/minecraft/mc-mods/minecraft-comes-alive-reborn) (Works, but some of its menus break FM's menu bar and/or are not customizable)
* [Minecraft Comes Alive](https://www.curseforge.com/minecraft/mc-mods/minecraft-comes-alive-mca) (Reported compatible, but its menus are not customizable)
* [MineTogether](https://www.curseforge.com/minecraft/mc-mods/creeperhost-minetogether) (Reported layout problems above GUI scale 2)
* [Mod Menu](https://www.curseforge.com/minecraft/mc-mods/modmenu) (Usually compatible; for a duplicated or uncustomizable Mods button, set **Main Menu -> Mods -> Mod Menu -> Mods Button** to **Adjacent**)
* [Modern Online Picture Frames](https://www.curseforge.com/minecraft/mc-mods/online-picture-frame) (Crash—see [this issue](https://github.com/Keksuccino/FancyMenu/issues/776))
* [Not Enough Animations](https://www.curseforge.com/minecraft/mc-mods/not-enough-animations) (Reported compatible on 1.16+ and incompatible on 1.12)
* [Optiscale](https://www.curseforge.com/minecraft/mc-mods/optiscale) (Breaks FancyMenu's UI; buttons aren’t clickable)
* [Pack Menu](https://www.curseforge.com/minecraft/mc-mods/packmenu)
* [Panorama Screens](https://modrinth.com/mod/panorama-screens) (Reported conflict between menu customization systems)
* [QuestCraft](https://github.com/QuestCraftPlusPlus/QuestCraft) (Game fails to load)
* [RandomPatches](https://www.curseforge.com/minecraft/mc-mods/randompatches-forge) (Works if `patchMinecraftClass = false` in its config)
* [Remove Reloading Screen](https://www.curseforge.com/minecraft/mc-mods/rrls) (Reported to break FancyMenu and Drippy Loading Screen)
* [Replay Mod](https://www.replaymod.com/download/) (Works when you set `mainMenuButton` to **BIG** in `<game-directory>/config/replaymod.json`)
* [Seamless Loading Screen](https://www.curseforge.com/minecraft/mc-mods/seamless-loading-screen) (Crashes the game)
* [Slight Gui Modifications](https://www.curseforge.com/minecraft/mc-mods/slight-gui-modifications)
* [Skin Layers 3D](https://www.curseforge.com/minecraft/mc-mods/skin-layers-3d) (Reported compatible on 1.16+ and incompatible on 1.12)
* [Smooth Scrolling Everywhere](https://www.curseforge.com/minecraft/mc-mods/smooth-scrolling-everywhere)
* [Sound Filters](https://www.curseforge.com/minecraft/mc-mods/sound-filters) (The audio extension will not work with this installed)
* [Sound Physics Remastered](https://www.curseforge.com/minecraft/mc-mods/sound-physics-remastered) (The audio extension will not work with this installed)
* [Stylish Effects](https://www.curseforge.com/minecraft/mc-mods/stylish-effects) (Main menu fails to load layouts the first time it’s shown)
* [Supplementaries](https://www.curseforge.com/minecraft/mc-mods/supplementaries) (Randomly crashes when customizing its config screen; delete the problematic layout from `<game-directory>/config/fancymenu/customization/`)
* [Terraria Craft](https://www.curseforge.com/minecraft/mc-mods/terraria-craft)
* [The Dalek Mod](https://www.curseforge.com/minecraft/mc-mods/the-dalek-mod) (Works if its custom main menu is disabled in the config)
* [ThonkUtil](https://www.curseforge.com/minecraft/mc-mods/thonkutil) (Works, but currently adds an unremovable text to the main menu)
* [Trade Uses](https://modrinth.com/mod/trade-uses) (Causes crashes in villager trade menu—possibly only when “Easy Villagers” is also installed)
* [VanillaFix](https://www.curseforge.com/minecraft/mc-mods/vanillafix) (Usable, but some users report issues with the VanillaFix crash screen)
* [FireplaceMode](https://www.curseforge.com/minecraft/mc-mods/fireplacemode) (The Pause screen resets its customizations sometimes with this mod installed)
* [Respackopts](https://www.curseforge.com/minecraft/mc-mods/respackopts) (Works, but only if you disable customizations for the Resource Pack screen)
* [Bind Pizzeria](https://modrinth.com/mod/jjpizza) (Breaks text rendering in FancyMenu's context menus)
* [EnhancedTooltips](https://www.curseforge.com/minecraft/mc-mods/enhancedtooltips) (Breaks FancyMenu's tooltips)
* [Skin Shuffle](https://modrinth.com/mod/skinshuffle) (The player entity added to menus by that mod is not customizable via FancyMenu
* [Wakes](https://modrinth.com/mod/wakes) (Crashes the game on launch because of an `IncompatibleClassChangeError` -- it fails to override a final method `AbstractSliderButton.getSprite()`, which is only final because of Wakes' modifying its visibility; See GitHub issues for more information: [Goby56/wakes #215](https://github.com/Goby56/wakes/issues/215), [Keksuccino/FancyMenu #1733](https://github.com/Keksuccino/FancyMenu/issues/1733))
