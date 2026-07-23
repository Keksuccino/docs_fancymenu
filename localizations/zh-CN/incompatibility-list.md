---
title: 不兼容列表
description: FancyMenu 阻止的界面以及社区报告的不兼容项。
---
# 不兼容项

# 有意禁用自定义的界面

FancyMenu 会阻止匹配某些模组包路径的界面，以防止崩溃或异常行为。与这些界面匹配时，自定义开关、覆盖层和布局都不可用。

这些阻止规则使用的是界面类的 Java 包名，而不是逐个手动列出的界面。因此，一条规则可能会影响同一模组或相关包中的多个界面。

被阻止的界面组包括：

- Create
- Panoramica
- Alex's Mobs
- Screenshot Viewer
- Twilight Forest
- Supplementaries
- OptiFine；请使用 [OptiFine Alternatives](./optifine-alternatives)
- SlimeKnights 和 Tinkers' Construct
- MidnightDust 模组
- SkinSwapper
- FancyMenu 自身的配置界面；[Custom GUIs](./custom-guis) 不受影响
- Immersive Engineering
- Dungeonz
- RPG-Hud
- Cobblemon 以及部分与 Cobblemon 相关的界面
- Applied Energistics 2
- Xaero 的地图模组

# 社区报告的不兼容项

下面的条目来自社区报告，并不是 FancyMenu 自身阻止的界面。兼容性可能会随着整合包中的 FancyMenu、Minecraft、加载器和模组版本而变化。

* [Animated Loading Screen](https://modrinth.com/mod/animated-loading-screen)（会让菜单看起来有 bug）
* [Animated Mojang Logo](https://www.curseforge.com/minecraft/mc-mods/animated-mojang-logo)（布局有时不会加载；同时也会破坏 Drippy Loading Screen）
* [Bedrockify](https://www.curseforge.com/minecraft/mc-mods/bedrockify)（当你禁用该模组的所有菜单修改后兼容，至少对于你想自定义的菜单是这样）
* [BetterFPS](https://www.curseforge.com/minecraft/mc-mods/betterfps)（该模组的按钮和菜单不可自定义）
* [Chat Colors](https://www.curseforge.com/minecraft/mc-mods/chat-colours)（启动时崩溃）
* [Chloride](https://modrinth.com/mod/chloride)（安装此模组时，FPS 占位符无法工作）
* [Colormatic](https://www.curseforge.com/minecraft/mc-mods/colormatic)（启动 MC 时严重卡顿，并会破坏 FM 的音频相关功能）
* [Controllable](https://www.curseforge.com/minecraft/mc-mods/controllable)（通过 FancyMenu 添加到菜单中的自定义按钮，无法通过 Controllable 的“虚拟鼠标”功能点击）
* [Controlify](https://modrinth.com/mod/controlify)（据报会崩溃；见 [issue #1144](https://github.com/Keksuccino/FancyMenu/issues/1144)）
* [Crash To Main Menu](https://www.curseforge.com/minecraft/mc-mods/crash-to-main-menu)
* [Custom Loading Screen](https://www.curseforge.com/minecraft/mc-mods/better-loading-screen)
* [Custom Main Menu](https://www.curseforge.com/minecraft/mc-mods/custom-main-menu)
* [Debugify](https://www.curseforge.com/minecraft/mc-mods/debugify)（请改用 [Modern Debugify](https://www.curseforge.com/minecraft/mc-mods/modern-debugify)）
* [Dynamic Surroundings](https://www.curseforge.com/minecraft/mc-mods/dynamic-surroundings)（据报会破坏音频元素）
* [EnhancedVisuals](https://www.curseforge.com/minecraft/mc-mods/enhancedvisuals)（据报存在动画和半透明背景问题）
* [Entity Model Features](https://modrinth.com/mod/entity-model-features)（据报会崩溃；见 [issue #1115](https://github.com/Keksuccino/FancyMenu/issues/1115)）
* [Fossils and Archeology Revival](https://www.curseforge.com/minecraft/mc-mods/fossils)（游戏内可用，但不支持自定义主菜单——可在其配置中禁用）
* [Holographic Renderers](https://www.curseforge.com/minecraft/mc-mods/holographic-renderers)（启动时崩溃）
* [Ice and Fire](https://www.curseforge.com/minecraft/mc-mods/ice-and-fire-dragons)（如果在配置中禁用自定义主菜单则可用）
* [Jurassicraft](https://www.curseforge.com/minecraft/mc-mods/jurassicraft)（为其 GUI 启用自定义后，启动时崩溃——请从 `<game-directory>/config/fancymenu/customizablemenus.txt` 中删除它们）
* [Legacy4J](https://www.curseforge.com/minecraft/mc-mods/legacy-minecraft)（会使游戏崩溃）
* [MalisisCore](https://www.curseforge.com/minecraft/mc-mods/malisiscore)（会破坏主菜单自定义）
* [Main Menu Scale Mod](https://www.curseforge.com/minecraft/mc-mods/main-menu-scale)
* [MCA Reborn](https://www.curseforge.com/minecraft/mc-mods/minecraft-comes-alive-reborn)（可用，但它的一些菜单会破坏 FM 的菜单栏和/或不可自定义）
* [Minecraft Comes Alive](https://www.curseforge.com/minecraft/mc-mods/minecraft-comes-alive-mca)（据报兼容，但它的菜单不可自定义）
* [MineTogether](https://www.curseforge.com/minecraft/mc-mods/creeperhost-minetogether)（据报在 GUI 缩放高于 2 时会出现布局问题）
* [Mod Menu](https://www.curseforge.com/minecraft/mc-mods/modmenu)（通常兼容；如果出现重复或不可自定义的 Mods 按钮，请将 **Main Menu -> Mods -> Mod Menu -> Mods Button** 设为 **Adjacent**）
* [Modern Online Picture Frames](https://www.curseforge.com/minecraft/mc-mods/online-picture-frame)（崩溃——见 [此 issue](https://github.com/Keksuccino/FancyMenu/issues/776)）
* [Not Enough Animations](https://www.curseforge.com/minecraft/mc-mods/not-enough-animations)（据报在 1.16+ 兼容，在 1.12 不兼容）
* [Optiscale](https://www.curseforge.com/minecraft/mc-mods/optiscale)（会破坏 FancyMenu 的 UI；按钮无法点击）
* [Pack Menu](https://www.curseforge.com/minecraft/mc-mods/packmenu)
* [Panorama Screens](https://modrinth.com/mod/panorama-screens)（据报两套菜单自定义系统存在冲突）
* [QuestCraft](https://github.com/QuestCraftPlusPlus/QuestCraft)（游戏无法加载）
* [RandomPatches](https://www.curseforge.com/minecraft/mc-mods/randompatches-forge)（如果在配置中将 `patchMinecraftClass = false` 则可用）
* [Remove Reloading Screen](https://www.curseforge.com/minecraft/mc-mods/rrls)（据报会破坏 FancyMenu 和 Drippy Loading Screen）
* [Replay Mod](https://www.replaymod.com/download/)（如果在 `<game-directory>/config/replaymod.json` 中将 `mainMenuButton` 设为 **BIG** 则可用）
* [Seamless Loading Screen](https://www.curseforge.com/minecraft/mc-mods/seamless-loading-screen)（会使游戏崩溃）
* [Slight Gui Modifications](https://www.curseforge.com/minecraft/mc-mods/slight-gui-modifications)
* [Skin Layers 3D](https://www.curseforge.com/minecraft/mc-mods/skin-layers-3d)（据报在 1.16+ 兼容，在 1.12 不兼容）
* [Smooth Scrolling Everywhere](https://www.curseforge.com/minecraft/mc-mods/smooth-scrolling-everywhere)
* [Sound Filters](https://www.curseforge.com/minecraft/mc-mods/sound-filters)（安装此模组后，音频扩展将无法工作）
* [Sound Physics Remastered](https://www.curseforge.com/minecraft/mc-mods/sound-physics-remastered)（安装此模组后，音频扩展将无法工作）
* [Stylish Effects](https://www.curseforge.com/minecraft/mc-mods/stylish-effects)（主菜单首次显示时无法加载布局）
* [Supplementaries](https://www.curseforge.com/minecraft/mc-mods/supplementaries)（自定义其配置界面时会随机崩溃；请从 `<game-directory>/config/fancymenu/customization/` 中删除有问题的布局）
* [Terraria Craft](https://www.curseforge.com/minecraft/mc-mods/terraria-craft)
* [The Dalek Mod](https://www.curseforge.com/minecraft/mc-mods/the-dalek-mod)（如果在配置中禁用其自定义主菜单则可用）
* [ThonkUtil](https://www.curseforge.com/minecraft/mc-mods/thonkutil)（可用，但目前会在主菜单中添加一段无法移除的文字）
* [Trade Uses](https://modrinth.com/mod/trade-uses)（会导致村民交易菜单崩溃——可能只在同时安装了 “Easy Villagers” 时发生）
* [VanillaFix](https://www.curseforge.com/minecraft/mc-mods/vanillafix)（可用，但有些用户报告 VanillaFix 崩溃界面存在问题）
* [FireplaceMode](https://www.curseforge.com/minecraft/mc-mods/fireplacemode)（安装此模组后，暂停界面有时会重置其自定义内容）
* [Respackopts](https://www.curseforge.com/minecraft/mc-mods/respackopts)（可用，但前提是你禁用资源包界面的自定义）
* [Bind Pizzeria](https://modrinth.com/mod/jjpizza)（会破坏 FancyMenu 上下文菜单中的文本渲染）
* [EnhancedTooltips](https://www.curseforge.com/minecraft/mc-mods/enhancedtooltips)（会破坏 FancyMenu 的工具提示）
* [Skin Shuffle](https://modrinth.com/mod/skinshuffle)（该模组添加到菜单中的玩家实体无法通过 FancyMenu 自定义）
