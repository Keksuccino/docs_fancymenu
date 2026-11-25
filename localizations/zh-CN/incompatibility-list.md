---
title: 不兼容列表
description: FancyMenu 屏蔽的界面，以及社区报告的不兼容情况。
sourceBlobSha: 2f89775eade27d0a90dd3805b5c58d779676bdbd
---
# 有意禁用自定义功能的界面

FancyMenu 会屏蔽与某些模组包路径匹配的界面，以避免崩溃或行为异常。在匹配的界面中，自定义开关、叠加层和布局均不可用。

这些屏蔽规则依据界面类的 Java 包路径，而非针对单个界面手动列出的清单。因此，一条规则可能会影响同一模组或相关包中的多个界面。

被屏蔽的界面组包括：

- Create
- Panoramica
- Alex's Mobs
- Screenshot Viewer
- Twilight Forest
- Supplementaries
- OptiFine；请使用 [OptiFine 替代方案](/optifine-alternatives)
- SlimeKnights 和 Tinkers' Construct
- MidnightDust 系列模组
- SkinSwapper
- Immersive Engineering
- Dungeonz
- RPG-Hud
- Cobblemon 及部分 Cobblemon 相关界面
- Applied Energistics 2
- Xaero's 地图模组

# 社区报告的不兼容情况

以下内容为社区报告，并非 FancyMenu 本身屏蔽的界面。兼容性可能会随整合包中 FancyMenu、Minecraft、加载器和模组的版本而变化。

* [Animated Loading Screen](https://modrinth.com/mod/animated-loading-screen)（会导致菜单显示异常）
* [Animated Mojang Logo](https://www.curseforge.com/minecraft/mc-mods/animated-mojang-logo)（布局有时无法加载；还会导致 Drippy Loading Screen 出现问题）
* [Bedrockify](https://www.curseforge.com/minecraft/mc-mods/bedrockify)（禁用该模组的所有菜单修改后即可兼容，至少要对你想自定义的菜单禁用这些修改）
* [BetterFPS](https://www.curseforge.com/minecraft/mc-mods/betterfps)（该模组添加的按钮和菜单无法自定义）
* [Chat Colors](https://www.curseforge.com/minecraft/mc-mods/chat-colours)（启动时崩溃）
* [Chloride](https://modrinth.com/mod/chloride)（安装此模组后，FPS 占位符无法使用）
* [Colormatic](https://www.curseforge.com/minecraft/mc-mods/colormatic)（启动 MC 时会严重卡顿，并导致 FM 的音频功能失效）
* [Controllable](https://www.curseforge.com/minecraft/mc-mods/controllable)（通过 FancyMenu 添加到菜单中的自定义按钮，无法使用 Controllable 的“虚拟鼠标”功能点击）
* [Controlify](https://modrinth.com/mod/controlify)（有崩溃报告；请参阅[问题 #1144](https://github.com/Keksuccino/FancyMenu/issues/1144)）
* [Crash To Main Menu](https://www.curseforge.com/minecraft/mc-mods/crash-to-main-menu)
* [Custom Loading Screen](https://www.curseforge.com/minecraft/mc-mods/better-loading-screen)
* [Custom Main Menu](https://www.curseforge.com/minecraft/mc-mods/custom-main-menu)
* [Debugify](https://www.curseforge.com/minecraft/mc-mods/debugify)（请改用 [Modern Debugify](https://www.curseforge.com/minecraft/mc-mods/modern-debugify)）
* [Dynamic Surroundings](https://www.curseforge.com/minecraft/mc-mods/dynamic-surroundings)（有报告称会导致音频元素失效）
* [EnhancedVisuals](https://www.curseforge.com/minecraft/mc-mods/enhancedvisuals)（有动画和半透明背景显示异常的报告）
* [Entity Model Features](https://modrinth.com/mod/entity-model-features)（有崩溃报告；请参阅[问题 #1115](https://github.com/Keksuccino/FancyMenu/issues/1115)）
* [Fossils and Archeology Revival](https://www.curseforge.com/minecraft/mc-mods/fossils)（游戏内可正常使用，但不支持自定义主菜单；可在其配置中禁用）
* [Holographic Renderers](https://www.curseforge.com/minecraft/mc-mods/holographic-renderers)（启动时崩溃）
* [Ice and Fire](https://www.curseforge.com/minecraft/mc-mods/ice-and-fire-dragons)（在配置中禁用自定义主菜单后即可使用）
* [Jurassicraft](https://www.curseforge.com/minecraft/mc-mods/jurassicraft)（为其 GUI 启用自定义功能时，启动游戏会崩溃——请从 `<game-directory>/config/fancymenu/customizablemenus.txt` 中删除这些界面）
* [Legacy4J](https://www.curseforge.com/minecraft/mc-mods/legacy-minecraft)（会导致游戏崩溃）
* [MalisisCore](https://www.curseforge.com/minecraft/mc-mods/malisiscore)（会导致主菜单自定义功能失效）
* [Main Menu Scale Mod](https://www.curseforge.com/minecraft/mc-mods/main-menu-scale)
* [MCA Reborn](https://www.curseforge.com/minecraft/mc-mods/minecraft-comes-alive-reborn)（可以使用，但其部分菜单会导致 FM 菜单栏失效，和/或无法自定义）
* [Minecraft Comes Alive](https://www.curseforge.com/minecraft/mc-mods/minecraft-comes-alive-mca)（有报告称兼容，但其菜单无法自定义）
* [MineTogether](https://www.curseforge.com/minecraft/mc-mods/creeperhost-minetogether)（GUI 缩放大于 2 时有布局异常的报告）
* [Mod Menu](https://www.curseforge.com/minecraft/mc-mods/modmenu)（通常兼容；如果“模组”按钮重复出现或无法自定义，请将 **主菜单 -> 模组 -> Mod Menu -> 模组按钮** 设为 **相邻**）
* [Modern Online Picture Frames](https://www.curseforge.com/minecraft/mc-mods/online-picture-frame)（会崩溃——请参阅[此问题](https://github.com/Keksuccino/FancyMenu/issues/776)）
* [Not Enough Animations](https://www.curseforge.com/minecraft/mc-mods/not-enough-animations)（有报告称在 1.16 及以上版本兼容，在 1.12 版本不兼容）
* [Optiscale](https://www.curseforge.com/minecraft/mc-mods/optiscale)（会导致 FancyMenu 的 UI 失效；按钮无法点击）
* [Pack Menu](https://www.curseforge.com/minecraft/mc-mods/packmenu)
* [Panorama Screens](https://modrinth.com/mod/panorama-screens)（有菜单自定义系统冲突的报告）
* [QuestCraft](https://github.com/QuestCraftPlusPlus/QuestCraft)（游戏无法加载）
* [RandomPatches](https://www.curseforge.com/minecraft/mc-mods/randompatches-forge)（在其配置中设置 `patchMinecraftClass = false` 后即可使用）
* [Remove Reloading Screen](https://www.curseforge.com/minecraft/mc-mods/rrls)（有报告称会导致 FancyMenu 和 Drippy Loading Screen 失效）
* [Replay Mod](https://www.replaymod.com/download/)（将 `<game-directory>/config/replaymod.json` 中的 `mainMenuButton` 设为 **BIG** 后即可使用）
* [Seamless Loading Screen](https://www.curseforge.com/minecraft/mc-mods/seamless-loading-screen)（会导致游戏崩溃）
* [Slight Gui Modifications](https://www.curseforge.com/minecraft/mc-mods/slight-gui-modifications)
* [Skin Layers 3D](https://www.curseforge.com/minecraft/mc-mods/skin-layers-3d)（有报告称在 1.16 及以上版本兼容，在 1.12 版本不兼容）
* [Smooth Scrolling Everywhere](https://www.curseforge.com/minecraft/mc-mods/smooth-scrolling-everywhere)
* [Sound Filters](https://www.curseforge.com/minecraft/mc-mods/sound-filters)（安装此模组后，音频扩展将无法使用）
* [Sound Physics Remastered](https://www.curseforge.com/minecraft/mc-mods/sound-physics-remastered)（安装此模组后，音频扩展将无法使用）
* [Stylish Effects](https://www.curseforge.com/minecraft/mc-mods/stylish-effects)（主菜单首次显示时无法加载布局）
* [Supplementaries](https://www.curseforge.com/minecraft/mc-mods/supplementaries)（自定义其配置界面时可能随机崩溃；请从 `<game-directory>/config/fancymenu/customization/` 中删除有问题的布局）
* [Terraria Craft](https://www.curseforge.com/minecraft/mc-mods/terraria-craft)
* [The Dalek Mod](https://www.curseforge.com/minecraft/mc-mods/the-dalek-mod)（在配置中禁用其自定义主菜单后即可使用）
* [ThonkUtil](https://www.curseforge.com/minecraft/mc-mods/thonkutil)（可以使用，但目前会在主菜单中添加一段无法移除的文本）
* [Trade Uses](https://modrinth.com/mod/trade-uses)（会导致村民交易菜单崩溃——可能仅在同时安装“Easy Villagers”时出现）
* [VanillaFix](https://www.curseforge.com/minecraft/mc-mods/vanillafix)（可以使用，但有用户报告称 VanillaFix 崩溃界面存在问题）
* [FireplaceMode](https://www.curseforge.com/minecraft/mc-mods/fireplacemode)（安装此模组后，暂停界面的自定义设置有时会重置）
* [Respackopts](https://www.curseforge.com/minecraft/mc-mods/respackopts)（可以使用，但必须禁用资源包界面的自定义功能）
* [Bind Pizzeria](https://modrinth.com/mod/jjpizza)（会导致 FancyMenu 上下文菜单中的文本渲染异常）
* [EnhancedTooltips](https://www.curseforge.com/minecraft/mc-mods/enhancedtooltips)（会导致 FancyMenu 的提示框失效）
* [Skin Shuffle](https://modrinth.com/mod/skinshuffle)（该模组添加到菜单中的玩家实体无法通过 FancyMenu 自定义
* [Wakes](https://modrinth.com/mod/wakes)（启动游戏时会因 `IncompatibleClassChangeError` 崩溃——该模组尝试覆盖最终方法 `AbstractSliderButton.getSprite()`，但该方法之所以是最终方法，仅仅是因为 Wakes 修改了它的可见性；更多信息请参阅 GitHub 上的问题：[Goby56/wakes #215](https://github.com/Goby56/wakes/issues/215)、[Keksuccino/FancyMenu #1733](https://github.com/Keksuccino/FancyMenu/issues/1733)）
* [Essential](https://www.curseforge.com/minecraft/mc-mods/essential)（更多信息请查看[此页面](/essential)）
