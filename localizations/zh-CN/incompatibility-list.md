---
title: 不兼容列表
description: FancyMenu 屏蔽的界面，以及社区报告的不兼容情况。
sourceBlobSha: f5f938751a166796106f5074dc55137bcd40f203
---
# 有意禁用自定义功能的界面

FancyMenu 会屏蔽与特定模组包路径匹配的界面，以防止崩溃或行为异常。在匹配的界面上，自定义开关、覆盖层和布局均不可用。

这些屏蔽规则使用界面类的 Java 包路径，而不是逐一列出特定界面。因此，一条规则可能会影响同一模组或相关包中的多个界面。

被屏蔽的界面组包括：

- Create
- Panoramica
- Alex's Mobs
- Screenshot Viewer
- Twilight Forest
- Supplementaries
- OptiFine；请使用 [OptiFine 替代方案](./optifine-alternatives)
- SlimeKnights 和 Tinkers' Construct
- MidnightDust 模组
- SkinSwapper
- Immersive Engineering
- Dungeonz
- RPG-Hud
- Cobblemon 及部分与 Cobblemon 相关的界面
- Applied Energistics 2
- Xaero's 地图模组

# 社区报告的不兼容情况

以下条目来自社区报告，并不是 FancyMenu 自身屏蔽的界面。在整合包中，兼容性可能会随着 FancyMenu、Minecraft、加载器和模组版本的变化而改变。

* [Animated Loading Screen](https://modrinth.com/mod/animated-loading-screen)（会导致菜单显示异常）
* [Animated Mojang Logo](https://www.curseforge.com/minecraft/mc-mods/animated-mojang-logo)（布局有时无法加载；也会破坏 Drippy Loading Screen）
* [Bedrockify](https://www.curseforge.com/minecraft/mc-mods/bedrockify)（禁用该模组的所有菜单修改后兼容，至少要对你想要自定义的菜单禁用）
* [BetterFPS](https://www.curseforge.com/minecraft/mc-mods/betterfps)（该模组的按钮和菜单无法自定义）
* [Chat Colors](https://www.curseforge.com/minecraft/mc-mods/chat-colours)（启动时崩溃）
* [Chloride](https://modrinth.com/mod/chloride)（安装此模组后，FPS 占位符无法正常工作）
* [Colormatic](https://www.curseforge.com/minecraft/mc-mods/colormatic)（启动 Minecraft 时出现严重卡顿，并会破坏 FM 的音频功能）
* [Controllable](https://www.curseforge.com/minecraft/mc-mods/controllable)（使用 FancyMenu 添加到菜单中的自定义按钮无法通过 Controllable 的“虚拟鼠标”功能点击）
* [Controlify](https://modrinth.com/mod/controlify)（有崩溃报告；请参阅 [问题 #1144](https://github.com/Keksuccino/FancyMenu/issues/1144)）
* [Crash To Main Menu](https://www.curseforge.com/minecraft/mc-mods/crash-to-main-menu)
* [Custom Loading Screen](https://www.curseforge.com/minecraft/mc-mods/better-loading-screen)
* [Custom Main Menu](https://www.curseforge.com/minecraft/mc-mods/custom-main-menu)
* [Debugify](https://www.curseforge.com/minecraft/mc-mods/debugify)（请改用 [Modern Debugify](https://www.curseforge.com/minecraft/mc-mods/modern-debugify)）
* [Dynamic Surroundings](https://www.curseforge.com/minecraft/mc-mods/dynamic-surroundings)（据报告会破坏音频元素）
* [EnhancedVisuals](https://www.curseforge.com/minecraft/mc-mods/enhancedvisuals)（据报告会导致动画和半透明背景出现问题）
* [Entity Model Features](https://modrinth.com/mod/entity-model-features)（有崩溃报告；请参阅 [问题 #1115](https://github.com/Keksuccino/FancyMenu/issues/1115)）
* [Fossils and Archeology Revival](https://www.curseforge.com/minecraft/mc-mods/fossils)（游戏内可正常运行，但不支持自定义主菜单；可以在其配置中禁用）
* [Holographic Renderers](https://www.curseforge.com/minecraft/mc-mods/holographic-renderers)（启动时崩溃）
* [Ice and Fire](https://www.curseforge.com/minecraft/mc-mods/ice-and-fire-dragons)（在其配置中禁用自定义主菜单后可以正常运行）
* [Jurassicraft](https://www.curseforge.com/minecraft/mc-mods/jurassicraft)（为其 GUI 启用自定义功能时会在启动时崩溃——请从 `<game-directory>/config/fancymenu/customizablemenus.txt` 中删除这些界面）
* [Legacy4J](https://www.curseforge.com/minecraft/mc-mods/legacy-minecraft)（会导致游戏崩溃）
* [MalisisCore](https://www.curseforge.com/minecraft/mc-mods/malisiscore)（会破坏主菜单自定义功能）
* [Main Menu Scale Mod](https://www.curseforge.com/minecraft/mc-mods/main-menu-scale)
* [MCA Reborn](https://www.curseforge.com/minecraft/mc-mods/minecraft-comes-alive-reborn)（可以运行，但其部分菜单会破坏 FM 的菜单栏，和/或无法自定义）
* [Minecraft Comes Alive](https://www.curseforge.com/minecraft/mc-mods/minecraft-comes-alive-mca)（据报告兼容，但其菜单无法自定义）
* [MineTogether](https://www.curseforge.com/minecraft/mc-mods/creeperhost-minetogether)（GUI 缩放大于 2 时据报告会出现布局问题）
* [Mod Menu](https://www.curseforge.com/minecraft/mc-mods/modmenu)（通常兼容；如果 Mods 按钮重复或无法自定义，请将 **主菜单 -> Mods -> Mod Menu -> Mods Button** 设置为 **Adjacent**）
* [Modern Online Picture Frames](https://www.curseforge.com/minecraft/mc-mods/online-picture-frame)（会崩溃——请参阅[此问题](https://github.com/Keksuccino/FancyMenu/issues/776)）
* [Not Enough Animations](https://www.curseforge.com/minecraft/mc-mods/not-enough-animations)（据报告在 1.16 及更高版本兼容，在 1.12 中不兼容）
* [Optiscale](https://www.curseforge.com/minecraft/mc-mods/optiscale)（会破坏 FancyMenu 的界面；按钮无法点击）
* [Pack Menu](https://www.curseforge.com/minecraft/mc-mods/packmenu)
* [Panorama Screens](https://modrinth.com/mod/panorama-screens)（据报告与菜单自定义系统之间存在冲突）
* [QuestCraft](https://github.com/QuestCraftPlusPlus/QuestCraft)（游戏无法加载）
* [RandomPatches](https://www.curseforge.com/minecraft/mc-mods/randompatches-forge)（在其配置中将 `patchMinecraftClass = false` 设置为 false 后可以运行）
* [Remove Reloading Screen](https://www.curseforge.com/minecraft/mc-mods/rrls)（据报告会破坏 FancyMenu 和 Drippy Loading Screen）
* [Replay Mod](https://www.replaymod.com/download/)（将 `<game-directory>/config/replaymod.json` 中的 `mainMenuButton` 设置为 **BIG** 后可以运行）
* [Seamless Loading Screen](https://www.curseforge.com/minecraft/mc-mods/seamless-loading-screen)（会导致游戏崩溃）
* [Slight Gui Modifications](https://www.curseforge.com/minecraft/mc-mods/slight-gui-modifications)
* [Skin Layers 3D](https://www.curseforge.com/minecraft/mc-mods/skin-layers-3d)（据报告在 1.16 及更高版本兼容，在 1.12 中不兼容）
* [Smooth Scrolling Everywhere](https://www.curseforge.com/minecraft/mc-mods/smooth-scrolling-everywhere)
* [Sound Filters](https://www.curseforge.com/minecraft/mc-mods/sound-filters)（安装此模组后，音频扩展将无法运行）
* [Sound Physics Remastered](https://www.curseforge.com/minecraft/mc-mods/sound-physics-remastered)（安装此模组后，音频扩展将无法运行）
* [Stylish Effects](https://www.curseforge.com/minecraft/mc-mods/stylish-effects)（主菜单首次显示时无法加载布局）
* [Supplementaries](https://www.curseforge.com/minecraft/mc-mods/supplementaries)（自定义其配置界面时会随机崩溃；请从 `<game-directory>/config/fancymenu/customization/` 中删除有问题的布局）
* [Terraria Craft](https://www.curseforge.com/minecraft/mc-mods/terraria-craft)
* [The Dalek Mod](https://www.curseforge.com/minecraft/mc-mods/the-dalek-mod)（在配置中禁用其自定义主菜单后可以运行）
* [ThonkUtil](https://www.curseforge.com/minecraft/mc-mods/thonkutil)（可以运行，但目前会在主菜单中添加无法移除的文本）
* [Trade Uses](https://modrinth.com/mod/trade-uses)（会导致村民交易菜单崩溃——可能只有在同时安装“Easy Villagers”时才会发生）
* [VanillaFix](https://www.curseforge.com/minecraft/mc-mods/vanillafix)（可以使用，但部分用户报告 VanillaFix 崩溃界面存在问题）
* [FireplaceMode](https://www.curseforge.com/minecraft/mc-mods/fireplacemode)（安装此模组后，暂停界面有时会重置其自定义内容）
* [Respackopts](https://www.curseforge.com/minecraft/mc-mods/respackopts)（可以运行，但必须禁用资源包界面的自定义功能）
* [Bind Pizzeria](https://modrinth.com/mod/jjpizza)（会破坏 FancyMenu 上下文菜单中的文本渲染）
* [EnhancedTooltips](https://www.curseforge.com/minecraft/mc-mods/enhancedtooltips)（会破坏 FancyMenu 的工具提示）
* [Skin Shuffle](https://modrinth.com/mod/skinshuffle)（该模组添加到菜单中的玩家实体无法通过 FancyMenu 自定义）
* [Wakes](https://modrinth.com/mod/wakes)（由于 `IncompatibleClassChangeError`，游戏会在启动时崩溃——它无法覆盖最终方法 `AbstractSliderButton.getSprite()`。该方法之所以为 final，是因为 Wakes 修改了其可见性；更多信息请参阅 GitHub 问题：[Goby56/wakes #215](https://github.com/Goby56/wakes/issues/215)、[Keksuccino/FancyMenu #1733](https://github.com/Keksuccino/FancyMenu/issues/1733)）
* [Essential](https://www.curseforge.com/minecraft/mc-mods/essential-mod)（更多信息请查看[此页面](/essential)）
