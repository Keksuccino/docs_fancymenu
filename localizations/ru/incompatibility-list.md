---
title: Список несовместимостей
description: 'Экраны, заблокированные FancyMenu, и несовместимости, сообщённые сообществом.'
---
# Несовместимости

# Экраны, для которых настройка намеренно отключена

FancyMenu блокирует экраны, соответствующие определённым путям Java-пакетов модов, чтобы предотвратить краши или некорректную работу. Переключатель настройки, оверлей и макеты недоступны на соответствующих экранах.

Эти блокировки используют Java-пакет класса экрана, а не вручную составленный список отдельных экранов. Поэтому одно правило может затронуть сразу несколько экранов из одного мода или связанных пакетов.

Заблокированные группы экранов включают:

- Create
- Panoramica
- Alex's Mobs
- Screenshot Viewer
- Twilight Forest
- Supplementaries
- OptiFine; используйте [Альтернативы OptiFine](./optifine-alternatives)
- SlimeKnights и Tinkers' Construct
- моды MidnightDust
- SkinSwapper
- собственные экраны настройки FancyMenu; [Пользовательские GUI](./custom-guis) исключены
- Immersive Engineering
- Dungeonz
- RPG-Hud
- Cobblemon и некоторые связанные с Cobblemon экраны
- Applied Energistics 2
- моды карты Xaero

# Несовместимости, о которых сообщило сообщество

Приведённые ниже записи — это сообщения пользователей, а не экраны, заблокированные самим FancyMenu. Совместимость может меняться в зависимости от версий FancyMenu, Minecraft, загрузчика и модов в сборке.

* [Animated Loading Screen](https://modrinth.com/mod/animated-loading-screen) (Меню выглядят сломанными)
* [Animated Mojang Logo](https://www.curseforge.com/minecraft/mc-mods/animated-mojang-logo) (Макеты иногда не загружаются; также ломает Drippy Loading Screen)
* [Bedrockify](https://www.curseforge.com/minecraft/mc-mods/bedrockify) (Совместим, если отключить все изменения меню в этом моде, по крайней мере для тех меню, которые вы хотите настраивать)
* [BetterFPS](https://www.curseforge.com/minecraft/mc-mods/betterfps) (Кнопки и меню этого мода нельзя настраивать)
* [Chat Colors](https://www.curseforge.com/minecraft/mc-mods/chat-colours) (Краш при запуске)
* [Chloride](https://modrinth.com/mod/chloride) (Плейсхолдер FPS не работает, когда установлен этот мод)
* [Colormatic](https://www.curseforge.com/minecraft/mc-mods/colormatic) (Сильные лаги при запуске MC и ломает аудиофункции FM)
* [Controllable](https://www.curseforge.com/minecraft/mc-mods/controllable) (Пользовательские кнопки, добавленные в меню через FancyMenu, нельзя нажать с помощью функции Controllable «Virtual Mouse»)
* [Controlify](https://modrinth.com/mod/controlify) (Сообщённый краш; см. [issue #1144](https://github.com/Keksuccino/FancyMenu/issues/1144))
* [Crash To Main Menu](https://www.curseforge.com/minecraft/mc-mods/crash-to-main-menu)
* [Custom Loading Screen](https://www.curseforge.com/minecraft/mc-mods/better-loading-screen)
* [Custom Main Menu](https://www.curseforge.com/minecraft/mc-mods/custom-main-menu)
* [Debugify](https://www.curseforge.com/minecraft/mc-mods/debugify) (Используйте вместо него [Modern Debugify](https://www.curseforge.com/minecraft/mc-mods/modern-debugify))
* [Dynamic Surroundings](https://www.curseforge.com/minecraft/mc-mods/dynamic-surroundings) (Сообщается, что ломает аудиоэлементы)
* [EnhancedVisuals](https://www.curseforge.com/minecraft/mc-mods/enhancedvisuals) (Сообщаются проблемы с анимациями и полупрозрачным фоном)
* [Entity Model Features](https://modrinth.com/mod/entity-model-features) (Сообщённый краш; см. [issue #1115](https://github.com/Keksuccino/FancyMenu/issues/1115))
* [Fossils and Archeology Revival](https://www.curseforge.com/minecraft/mc-mods/fossils) (В игре работает, но пользовательское главное меню не поддерживается — это можно отключить в его конфиге)
* [Holographic Renderers](https://www.curseforge.com/minecraft/mc-mods/holographic-renderers) (Краш при запуске)
* [Ice and Fire](https://www.curseforge.com/minecraft/mc-mods/ice-and-fire-dragons) (Работает, если отключить пользовательское главное меню в конфиге)
* [Jurassicraft](https://www.curseforge.com/minecraft/mc-mods/jurassicraft) (Крашится при запуске, если включить настройку его GUI — удалите их из `<game-directory>/config/fancymenu/customizablemenus.txt`)
* [Legacy4J](https://www.curseforge.com/minecraft/mc-mods/legacy-minecraft) (Крашит игру)
* [MalisisCore](https://www.curseforge.com/minecraft/mc-mods/malisiscore) (Ломает настройку главного меню)
* [Main Menu Scale Mod](https://www.curseforge.com/minecraft/mc-mods/main-menu-scale)
* [MCA Reborn](https://www.curseforge.com/minecraft/mc-mods/minecraft-comes-alive-reborn) (Работает, но некоторые его меню ломают панель меню FM и/или не поддаются настройке)
* [Minecraft Comes Alive](https://www.curseforge.com/minecraft/mc-mods/minecraft-comes-alive-mca) (Сообщается, что совместим, но его меню нельзя настраивать)
* [MineTogether](https://www.curseforge.com/minecraft/mc-mods/creeperhost-minetogether) (Сообщаются проблемы с макетами при масштабе GUI выше 2)
* [Mod Menu](https://www.curseforge.com/minecraft/mc-mods/modmenu) (Обычно совместим; если кнопка Mods дублируется или не настраивается, установите **Main Menu -> Mods -> Mod Menu -> Mods Button** в значение **Adjacent**)
* [Modern Online Picture Frames](https://www.curseforge.com/minecraft/mc-mods/online-picture-frame) (Краш — см. [this issue](https://github.com/Keksuccino/FancyMenu/issues/776))
* [Not Enough Animations](https://www.curseforge.com/minecraft/mc-mods/not-enough-animations) (Сообщается, что совместим в 1.16+ и несовместим в 1.12)
* [Optiscale](https://www.curseforge.com/minecraft/mc-mods/optiscale) (Ломает интерфейс FancyMenu; кнопки не нажимаются)
* [Pack Menu](https://www.curseforge.com/minecraft/mc-mods/packmenu)
* [Panorama Screens](https://modrinth.com/mod/panorama-screens) (Сообщается конфликт между системами настройки меню)
* [QuestCraft](https://github.com/QuestCraftPlusPlus/QuestCraft) (Игра не загружается)
* [RandomPatches](https://www.curseforge.com/minecraft/mc-mods/randompatches-forge) (Работает, если `patchMinecraftClass = false` в конфиге)
* [Remove Reloading Screen](https://www.curseforge.com/minecraft/mc-mods/rrls) (Сообщается, что ломает FancyMenu и Drippy Loading Screen)
* [Replay Mod](https://www.replaymod.com/download/) (Работает, если установить `mainMenuButton` в значение **BIG** в `<game-directory>/config/replaymod.json`)
* [Seamless Loading Screen](https://www.curseforge.com/minecraft/mc-mods/seamless-loading-screen) (Крашит игру)
* [Slight Gui Modifications](https://www.curseforge.com/minecraft/mc-mods/slight-gui-modifications)
* [Skin Layers 3D](https://www.curseforge.com/minecraft/mc-mods/skin-layers-3d) (Сообщается, что совместим в 1.16+ и несовместим в 1.12)
* [Smooth Scrolling Everywhere](https://www.curseforge.com/minecraft/mc-mods/smooth-scrolling-everywhere)
* [Sound Filters](https://www.curseforge.com/minecraft/mc-mods/sound-filters) (Аудиорасширение не будет работать при установленном этом моде)
* [Sound Physics Remastered](https://www.curseforge.com/minecraft/mc-mods/sound-physics-remastered) (Аудиорасширение не будет работать при установленном этом моде)
* [Stylish Effects](https://www.curseforge.com/minecraft/mc-mods/stylish-effects) (При первом открытии главный экран не загружает макеты)
* [Supplementaries](https://www.curseforge.com/minecraft/mc-mods/supplementaries) (Случайно крашится при настройке его экрана конфигурации; удалите проблемный макет из `<game-directory>/config/fancymenu/customization/`)
* [Terraria Craft](https://www.curseforge.com/minecraft/mc-mods/terraria-craft)
* [The Dalek Mod](https://www.curseforge.com/minecraft/mc-mods/the-dalek-mod) (Работает, если отключить его пользовательское главное меню в конфиге)
* [ThonkUtil](https://www.curseforge.com/minecraft/mc-mods/thonkutil) (Работает, но сейчас добавляет неснимаемый текст в главное меню)
* [Trade Uses](https://modrinth.com/mod/trade-uses) (Вызывает краши в меню торговли с жителем — возможно, только если также установлен «Easy Villagers»)
* [VanillaFix](https://www.curseforge.com/minecraft/mc-mods/vanillafix) (Можно использовать, но некоторые пользователи сообщают о проблемах с экраном краша VanillaFix)
* [FireplaceMode](https://www.curseforge.com/minecraft/mc-mods/fireplacemode) (Экран паузы иногда сбрасывает свои настройки при установленном этом моде)
* [Respackopts](https://www.curseforge.com/minecraft/mc-mods/respackopts) (Работает, но только если отключить настройки для экрана ресурс-пака)
* [Bind Pizzeria](https://modrinth.com/mod/jjpizza) (Ломает рендеринг текста в контекстных меню FancyMenu)
* [EnhancedTooltips](https://www.curseforge.com/minecraft/mc-mods/enhancedtooltips) (Ломает подсказки FancyMenu)
* [Skin Shuffle](https://modrinth.com/mod/skinshuffle) (Объект игрока, добавляемый этим модом в меню, нельзя настраивать через FancyMenu)
