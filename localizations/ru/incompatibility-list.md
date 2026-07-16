---
title: Список несовместимых модов
description: 'Список модов, которые, как известно, несовместимы с FancyMenu.'
---
# Список несовместимых модов

Следующие моды, как известно, в той или иной форме несовместимы с FancyMenu.

У некоторых модов есть обходные пути, позволяющие им работать с FancyMenu.
Если это так, соответствующая информация указана после названия мода в списке ниже.

**Если вы нашли несовместимый мод, которого ещё нет в этом списке, пожалуйста, откройте issue на GitHub! Большое спасибо!**

* [Animated Loading Screen](https://modrinth.com/mod/animated-loading-screen) (Из-за него меню выглядит сломанным)
* [Animated Mojang Logo](https://www.curseforge.com/minecraft/mc-mods/animated-mojang-logo) (Макеты иногда не загружаются; также ломает Drippy Loading Screen)
* [Bedrockify](https://www.curseforge.com/minecraft/mc-mods/bedrockify) (Совместим, если отключить все изменения меню, добавляемые модом, по крайней мере для тех меню, которые вы хотите настроить)
* [BetterFPS](https://www.curseforge.com/minecraft/mc-mods/betterfps) (Кнопки и меню этого мода нельзя настраивать)
* [Chat Colors](https://www.curseforge.com/minecraft/mc-mods/chat-colours) (Краш при запуске)
* [Chloride](https://modrinth.com/mod/chloride) (Плейсхолдер FPS не работает, когда установлен этот мод)
* [Colormatic](https://www.curseforge.com/minecraft/mc-mods/colormatic) (Сильные лаги при запуске Minecraft и ломает аудиофункции FM)
* [Controllable](https://www.curseforge.com/minecraft/mc-mods/controllable) (Пользовательские кнопки, добавленные в меню через FancyMenu, нельзя нажать с помощью функции «Virtual Mouse» в Controllable)
* [Controlify](https://modrinth.com/mod/controlify) (Похоже, вызывает краш игры, но с моей стороны я это исправить не могу — см. [этот issue](https://github.com/Keksuccino/FancyMenu/issues/1144) для дополнительного контекста)
* [Crash To Main Menu](https://www.curseforge.com/minecraft/mc-mods/crash-to-main-menu)
* [Custom Loading Screen](https://www.curseforge.com/minecraft/mc-mods/better-loading-screen)
* [Custom Main Menu](https://www.curseforge.com/minecraft/mc-mods/custom-main-menu)
* [Debugify](https://www.curseforge.com/minecraft/mc-mods/debugify) (Используйте вместо него [Modern Debugify](https://www.curseforge.com/minecraft/mc-mods/modern-debugify))
* [Dynamic Surroundings](https://www.curseforge.com/minecraft/mc-mods/dynamic-surroundings) (Ломает аудиоэлементы FancyMenu, но всё остальное должно работать нормально)
* [EnhancedVisuals](https://www.curseforge.com/minecraft/mc-mods/enhancedvisuals) (Похоже, ломает анимации, делает фоны полупрозрачными и, вероятно, не только это)
* [Entity Model Features](https://modrinth.com/mod/entity-model-features) (Крашит игру, но я не могу исправить это со своей стороны — см. [этот issue](https://github.com/Keksuccino/FancyMenu/issues/1115) для дополнительного контекста)
* [Fossils and Archeology Revival](https://www.curseforge.com/minecraft/mc-mods/fossils) (В игре работает, но кастомное главное меню не поддерживается — это можно отключить в его конфиге)
* [Holographic Renderers](https://www.curseforge.com/minecraft/mc-mods/holographic-renderers) (Краш при запуске)
* [Ice and Fire](https://www.curseforge.com/minecraft/mc-mods/ice-and-fire-dragons) (Работает, если отключить кастомное главное меню в конфиге)
* [Jurassicraft](https://www.curseforge.com/minecraft/mc-mods/jurassicraft) (Краш при запуске при включении кастомизации для его GUI — удалите их из `config/fancymenu/customizablemenus.txt`)
* [Legacy4J](https://www.curseforge.com/minecraft/mc-mods/legacy-minecraft) (Крашит игру)
* [MalisisCore](https://www.curseforge.com/minecraft/mc-mods/malisiscore) (Ломает кастомизацию главного меню)
* [Main Menu Scale Mod](https://www.curseforge.com/minecraft/mc-mods/main-menu-scale)
* [MCA Reborn](https://www.curseforge.com/minecraft/mc-mods/minecraft-comes-alive-reborn) (Работает, но некоторые его меню ломают панель меню FM и/или не поддаются настройке)
* [Minecraft Comes Alive](https://www.curseforge.com/minecraft/mc-mods/minecraft-comes-alive-mca) (Работает нормально, но его меню нельзя настраивать)
* [MineTogether](https://www.curseforge.com/minecraft/mc-mods/creeperhost-minetogether) (Похоже, ломает макеты при масштабе интерфейса > 2)
* [Mod Menu](https://www.curseforge.com/minecraft/mc-mods/modmenu) (**В БОЛЬШИНСТВЕ СЛУЧАЕВ РАБОТАЕТ НОРМАЛЬНО**, но если у вас дублируется кнопка Mods или её нельзя настроить, измените настройки кнопки Mod Menu на "Adjacent": Main Menu > Mods > Mod Menu > Mods Button: Adjacent)
* [Modern Online Picture Frames](https://www.curseforge.com/minecraft/mc-mods/online-picture-frame) (Краш — см. [этот issue](https://github.com/Keksuccino/FancyMenu/issues/776))
* [Not Enough Animations](https://www.curseforge.com/minecraft/mc-mods/not-enough-animations) (В 1.16+ работает нормально, но ломает 1.12)
* **OptiFine** (Ломает мод! Вместо него используйте [эти альтернативы](./optifine-alternatives))
* [Optiscale](https://www.curseforge.com/minecraft/mc-mods/optiscale) (Ломает интерфейс FancyMenu; кнопки нельзя нажать)
* [Pack Menu](https://www.curseforge.com/minecraft/mc-mods/packmenu)
* [Panorama Screens](https://modrinth.com/mod/panorama-screens) (Не будет работать и создаст проблемы, потому что накладывать друг на друга моды, изменяющие меню, — плохая идея)
* [QuestCraft](https://github.com/QuestCraftPlusPlus/QuestCraft) (Игра не загружается)
* [RandomPatches](https://www.curseforge.com/minecraft/mc-mods/randompatches-forge) (Работает, если в его конфиге `patchMinecraftClass = false`)
* [Remove Reloading Screen](https://www.curseforge.com/minecraft/mc-mods/rrls) (Ломает FM и Drippy. Не используйте этот мод.)
* [Replay Mod](https://www.replaymod.com/download/) (Работает, если установить `mainMenuButton` в **BIG** в `.minecraft/config/replaymod.json`)
* [Seamless Loading Screen](https://www.curseforge.com/minecraft/mc-mods/seamless-loading-screen) (Крашит игру)
* [Slight Gui Modifications](https://www.curseforge.com/minecraft/mc-mods/slight-gui-modifications)
* [Skin Layers 3D](https://www.curseforge.com/minecraft/mc-mods/skin-layers-3d) (В 1.16+ работает нормально, но ломает 1.12)
* [Smooth Scrolling Everywhere](https://www.curseforge.com/minecraft/mc-mods/smooth-scrolling-everywhere)
* [Sound Filters](https://www.curseforge.com/minecraft/mc-mods/sound-filters) (Аудиорасширение не будет работать при установленном этом моде)
* [Sound Physics Remastered](https://www.curseforge.com/minecraft/mc-mods/sound-physics-remastered) (Аудиорасширение не будет работать при установленном этом моде)
* [Stylish Effects](https://www.curseforge.com/minecraft/mc-mods/stylish-effects) (При первом открытии главное меню не загружает макеты)
* [Supplementaries](https://www.curseforge.com/minecraft/mc-mods/supplementaries) (Случайно крашится при настройке его экрана конфигурации; удалите проблемный макет из `.minecraft/config/fancymenu/customization`)
* [Terraria Craft](https://www.curseforge.com/minecraft/mc-mods/terraria-craft)
* [The Dalek Mod](https://www.curseforge.com/minecraft/mc-mods/the-dalek-mod) (Работает, если отключить его кастомное главное меню в конфиге)
* [ThonkUtil](https://www.curseforge.com/minecraft/mc-mods/thonkutil) (Работает, но сейчас добавляет в главное меню текст, который нельзя убрать)
* [Trade Uses](https://modrinth.com/mod/trade-uses) (Вызывает краши в меню торговли с жителем — возможно, только если также установлен мод “Easy Villagers”)
* [VanillaFix](https://www.curseforge.com/minecraft/mc-mods/vanillafix) (Можно использовать, но некоторые пользователи сообщают о проблемах с экраном краша VanillaFix)
* [FireplaceMode](https://www.curseforge.com/minecraft/mc-mods/fireplacemode) (При установленном этом моде экран паузы иногда сбрасывает свои настройки)
* [Respackopts](https://www.curseforge.com/minecraft/mc-mods/respackopts) (Работает, но только если отключить кастомизацию экрана ресурс-паков)
* [Bind Pizzeria](https://modrinth.com/mod/jjpizza) (Ломает рендеринг текста в контекстных меню FancyMenu)
* [EnhancedTooltips](https://www.curseforge.com/minecraft/mc-mods/enhancedtooltips) (Ломает подсказки FancyMenu)
* [Skin Shuffle](https://modrinth.com/mod/skinshuffle) (Игровой персонаж, добавляемый этим модом в меню, нельзя настроить через FancyMenu)
