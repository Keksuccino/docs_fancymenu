---
title: 不兼容列表
description: 已知与 FancyMenu 不兼容的模组列表。
---

# 不兼容模组列表

以下模组已知在某些方面与 FancyMenu 不兼容。

其中一些模组可以通过变通方法与 FancyMenu 配合使用。
如果是这种情况，会在下面列表中的模组名称后注明。

**如果你发现了一个尚未收录在此列表中的不兼容模组，请在 GitHub 上提交 issue！非常感谢！**

* [Animated Loading Screen](https://modrinth.com/mod/animated-loading-screen)（会让菜单看起来像是出现了 bug）
* [Animated Mojang Logo](https://www.curseforge.com/minecraft/mc-mods/animated-mojang-logo)（布局有时不会加载；还会破坏 Drippy Loading Screen）
* [Bedrockify](https://www.curseforge.com/minecraft/mc-mods/bedrockify)（如果你在该模组中禁用所有菜单修改功能，则兼容；至少对你想自定义的那些菜单是这样）
* [BetterFPS](https://www.curseforge.com/minecraft/mc-mods/betterfps)（该模组的按钮和菜单无法自定义）
* [Chat Colors](https://www.curseforge.com/minecraft/mc-mods/chat-colours)（启动时崩溃）
* [Chloride](https://modrinth.com/mod/chloride)（安装此模组后，FPS 占位符无法工作）
* [Colormatic](https://www.curseforge.com/minecraft/mc-mods/colormatic)（启动 MC 时会严重卡顿，并且会破坏 FM 的音频功能）
* [Controllable](https://www.curseforge.com/minecraft/mc-mods/controllable)（通过 Controllable 的“虚拟鼠标”功能无法点击 FancyMenu 添加到菜单中的自定义按钮）
* [Controlify](https://modrinth.com/mod/controlify)（似乎会导致游戏崩溃，但我这边无法修复——更多背景请参见[此 issue](https://github.com/Keksuccino/FancyMenu/issues/1144)）
* [Crash To Main Menu](https://www.curseforge.com/minecraft/mc-mods/crash-to-main-menu)
* [Custom Loading Screen](https://www.curseforge.com/minecraft/mc-mods/better-loading-screen)
* [Custom Main Menu](https://www.curseforge.com/minecraft/mc-mods/custom-main-menu)
* [Debugify](https://www.curseforge.com/minecraft/mc-mods/debugify)（请改用 [Modern Debugify](https://www.curseforge.com/minecraft/mc-mods/modern-debugify)）
* [Dynamic Surroundings](https://www.curseforge.com/minecraft/mc-mods/dynamic-surroundings)（会破坏 FancyMenu 的音频元素，但其他内容应该仍能正常工作）
* [EnhancedVisuals](https://www.curseforge.com/minecraft/mc-mods/enhancedvisuals)（似乎会破坏动画，使背景变为半透明，可能还有更多问题）
* [Entity Model Features](https://modrinth.com/mod/entity-model-features)（会导致游戏崩溃，但我这边无法修复——更多背景请参见[此 issue](https://github.com/Keksuccino/FancyMenu/issues/1115)）
* [Fossils and Archeology Revival](https://www.curseforge.com/minecraft/mc-mods/fossils)（游戏内可正常使用，但不支持自定义主菜单——可在其配置中禁用）
* [Holographic Renderers](https://www.curseforge.com/minecraft/mc-mods/holographic-renderers)（启动时崩溃）
* [Ice and Fire](https://www.curseforge.com/minecraft/mc-mods/ice-and-fire-dragons)（如果在配置中禁用自定义主菜单，则可正常使用）
* [Jurassicraft](https://www.curseforge.com/minecraft/mc-mods/jurassicraft)（在为其 GUI 启用自定义时，启动会崩溃——请从 `config/fancymenu/customizablemenus.txt` 中删除它们）
* [Legacy4J](https://www.curseforge.com/minecraft/mc-mods/legacy-minecraft)（会导致游戏崩溃）
* [MalisisCore](https://www.curseforge.com/minecraft/mc-mods/malisiscore)（会破坏主菜单自定义）
* [Main Menu Scale Mod](https://www.curseforge.com/minecraft/mc-mods/main-menu-scale)
* [MCA Reborn](https://www.curseforge.com/minecraft/mc-mods/minecraft-comes-alive-reborn)（可用，但它的一些菜单会破坏 FM 的菜单栏和/或无法自定义）
* [Minecraft Comes Alive](https://www.curseforge.com/minecraft/mc-mods/minecraft-comes-alive-mca)（运行正常，但它的菜单无法自定义）
* [MineTogether](https://www.curseforge.com/minecraft/mc-mods/creeperhost-minetogether)（当 GUI 缩放 > 2 时似乎会破坏布局）
* [Mod Menu](https://www.curseforge.com/minecraft/mc-mods/modmenu)（大多数情况下**完全正常**，但如果你遇到 Mods 按钮重复或无法自定义的问题，请将 Mod Menu 的按钮设置改为“Adjacent”：Main Menu > Mods > Mod Menu > Mods Button: Adjacent）
* [Modern Online Picture Frames](https://www.curseforge.com/minecraft/mc-mods/online-picture-frame)（崩溃——参见[此 issue](https://github.com/Keksuccino/FancyMenu/issues/776)）
* [Not Enough Animations](https://www.curseforge.com/minecraft/mc-mods/not-enough-animations)（在 1.16+ 中运行正常，但会破坏 1.12）
* **OptiFine**（会破坏该模组！请改用[这些替代方案](./optifine-alternatives)）
* [Optiscale](https://www.curseforge.com/minecraft/mc-mods/optiscale)（会破坏 FancyMenu 的 UI；按钮无法点击）
* [Pack Menu](https://www.curseforge.com/minecraft/mc-mods/packmenu)
* [Panorama Screens](https://modrinth.com/mod/panorama-screens)（无法正常工作并会引发问题，因为叠加多个菜单自定义模组从来都不是好主意）
* [QuestCraft](https://github.com/QuestCraftPlusPlus/QuestCraft)（游戏无法加载）
* [RandomPatches](https://www.curseforge.com/minecraft/mc-mods/randompatches-forge)（如果在配置中将 `patchMinecraftClass = false`，则可正常使用）
* [Remove Reloading Screen](https://www.curseforge.com/minecraft/mc-mods/rrls)（会破坏 FM 和 Drippy。不要使用这个模组。）
* [Replay Mod](https://www.replaymod.com/download/)（如果在 `.minecraft/config/replaymod.json` 中将 `mainMenuButton` 设置为 **BIG**，则可正常使用）
* [Seamless Loading Screen](https://www.curseforge.com/minecraft/mc-mods/seamless-loading-screen)（会导致游戏崩溃）
* [Slight Gui Modifications](https://www.curseforge.com/minecraft/mc-mods/slight-gui-modifications)
* [Skin Layers 3D](https://www.curseforge.com/minecraft/mc-mods/skin-layers-3d)（在 1.16+ 中运行正常，但会破坏 1.12）
* [Smooth Scrolling Everywhere](https://www.curseforge.com/minecraft/mc-mods/smooth-scrolling-everywhere)
* [Sound Filters](https://www.curseforge.com/minecraft/mc-mods/sound-filters)（安装此模组后，音频扩展将无法工作）
* [Sound Physics Remastered](https://www.curseforge.com/minecraft/mc-mods/sound-physics-remastered)（安装此模组后，音频扩展将无法工作）
* [Stylish Effects](https://www.curseforge.com/minecraft/mc-mods/stylish-effects)（主菜单首次显示时无法加载布局）
* [Supplementaries](https://www.curseforge.com/minecraft/mc-mods/supplementaries)（在自定义其配置界面时会随机崩溃；请从 `.minecraft/config/fancymenu/customization` 中删除有问题的布局）
* [Terraria Craft](https://www.curseforge.com/minecraft/mc-mods/terraria-craft)
* [The Dalek Mod](https://www.curseforge.com/minecraft/mc-mods/the-dalek-mod)（如果在配置中禁用其自定义主菜单，则可正常使用）
* [ThonkUtil](https://www.curseforge.com/minecraft/mc-mods/thonkutil)（可正常使用，但目前会在主菜单中添加一段无法移除的文字）
* [Trade Uses](https://modrinth.com/mod/trade-uses)（会导致村民交易菜单崩溃——可能只有在同时安装了 “Easy Villagers” 时才会这样）
* [VanillaFix](https://www.curseforge.com/minecraft/mc-mods/vanillafix)（可使用，但有些用户报告 VanillaFix 崩溃界面存在问题）
* [FireplaceMode](https://www.curseforge.com/minecraft/mc-mods/fireplacemode)（安装此模组后，暂停界面有时会重置其自定义内容）
* [Respackopts](https://www.curseforge.com/minecraft/mc-mods/respackopts)（可正常使用，但前提是你禁用资源包界面的自定义）
* [Bind Pizzeria](https://modrinth.com/mod/jjpizza)（会破坏 FancyMenu 上下文菜单中的文本渲染）
* [EnhancedTooltips](https://www.curseforge.com/minecraft/mc-mods/enhancedtooltips)（会破坏 FancyMenu 的工具提示）
