---
title: Список несовместимостей
description: >-
  Экраны, заблокированные FancyMenu, и несовместимости, о которых сообщили
  пользователи.
sourceBlobSha: f5f938751a166796106f5074dc55137bcd40f203
---
# Экраны, на которых настройка намеренно отключена

FancyMenu блокирует экраны, соответствующие определённым путям пакетов модов, чтобы предотвратить сбои или некорректную работу. Переключатель настройки, наложение и макеты недоступны на соответствующих экранах.

Для этих блокировок используется Java-пакет класса экрана, а не вручную составленный список отдельных экранов. Поэтому одно правило может затрагивать несколько экранов одного мода или связанных пакетов.

Заблокированные группы экранов:

- Create
- Panoramica
- Alex's Mobs
- Screenshot Viewer
- Twilight Forest
- Supplementaries
- OptiFine; используйте [альтернативы OptiFine](./optifine-alternatives)
- SlimeKnights и Tinkers' Construct
- Моды MidnightDust
- SkinSwapper
- Immersive Engineering
- Dungeonz
- RPG-Hud
- Cobblemon и некоторые связанные с Cobblemon экраны
- Applied Energistics 2
- Картографические моды Xaero

# Несовместимости, о которых сообщили пользователи

Приведённые ниже сведения основаны на сообщениях сообщества и не относятся к экранам, заблокированным самим FancyMenu. Совместимость может измениться в зависимости от версий FancyMenu, Minecraft, загрузчика и модов в сборке.

* [Animated Loading Screen](https://modrinth.com/mod/animated-loading-screen) (Меню могут выглядеть неисправными)
* [Animated Mojang Logo](https://www.curseforge.com/minecraft/mc-mods/animated-mojang-logo) (Макеты иногда не загружаются; также нарушается работа Drippy Loading Screen)
* [Bedrockify](https://www.curseforge.com/minecraft/mc-mods/bedrockify) (Совместим, если отключить все изменения меню, вносимые модом, по крайней мере для тех меню, которые вы хотите настроить)
* [BetterFPS](https://www.curseforge.com/minecraft/mc-mods/betterfps) (Кнопки и меню этого мода нельзя настроить)
* [Chat Colors](https://www.curseforge.com/minecraft/mc-mods/chat-colours) (Сбой при запуске)
* [Chloride](https://modrinth.com/mod/chloride) (Заполнитель FPS не работает при установленном моде)
* [Colormatic](https://www.curseforge.com/minecraft/mc-mods/colormatic) (Вызывает сильные задержки при запуске Minecraft и нарушает работу аудиофункций FM)
* [Controllable](https://www.curseforge.com/minecraft/mc-mods/controllable) (Пользовательские кнопки, добавленные в меню с помощью FancyMenu, нельзя нажимать через функцию «Виртуальная мышь» мода Controllable)
* [Controlify](https://modrinth.com/mod/controlify) (Сообщалось о сбоях; см. [issue #1144](https://github.com/Keksuccino/FancyMenu/issues/1144))
* [Crash To Main Menu](https://www.curseforge.com/minecraft/mc-mods/crash-to-main-menu)
* [Custom Loading Screen](https://www.curseforge.com/minecraft/mc-mods/better-loading-screen)
* [Custom Main Menu](https://www.curseforge.com/minecraft/mc-mods/custom-main-menu)
* [Debugify](https://www.curseforge.com/minecraft/mc-mods/debugify) (Вместо него используйте [Modern Debugify](https://www.curseforge.com/minecraft/mc-mods/modern-debugify))
* [Dynamic Surroundings](https://www.curseforge.com/minecraft/mc-mods/dynamic-surroundings) (Сообщалось о нарушении работы аудиоэлементов)
* [EnhancedVisuals](https://www.curseforge.com/minecraft/mc-mods/enhancedvisuals) (Сообщалось о проблемах с анимациями и прозрачным фоном)
* [Entity Model Features](https://modrinth.com/mod/entity-model-features) (Сообщалось о сбоях; см. [issue #1115](https://github.com/Keksuccino/FancyMenu/issues/1115))
* [Fossils and Archeology Revival](https://www.curseforge.com/minecraft/mc-mods/fossils) (В игре работает, но пользовательское главное меню не поддерживается — его можно отключить в настройках мода)
* [Holographic Renderers](https://www.curseforge.com/minecraft/mc-mods/holographic-renderers) (Сбой при запуске)
* [Ice and Fire](https://www.curseforge.com/minecraft/mc-mods/ice-and-fire-dragons) (Работает, если отключить пользовательское главное меню в настройках мода)
* [Jurassicraft](https://www.curseforge.com/minecraft/mc-mods/jurassicraft) (При включении настроек для его графических интерфейсов происходит сбой во время запуска — удалите их из `<game-directory>/config/fancymenu/customizablemenus.txt`)
* [Legacy4J](https://www.curseforge.com/minecraft/mc-mods/legacy-minecraft) (Вызывает сбой игры)
* [MalisisCore](https://www.curseforge.com/minecraft/mc-mods/malisiscore) (Нарушает настройку главного меню)
* [Main Menu Scale Mod](https://www.curseforge.com/minecraft/mc-mods/main-menu-scale)
* [MCA Reborn](https://www.curseforge.com/minecraft/mc-mods/minecraft-comes-alive-reborn) (Работает, но некоторые его меню нарушают работу панели меню FM и/или не поддаются настройке)
* [Minecraft Comes Alive](https://www.curseforge.com/minecraft/mc-mods/minecraft-comes-alive-mca) (Сообщалось о совместимости, но его меню нельзя настроить)
* [MineTogether](https://www.curseforge.com/minecraft/mc-mods/creeperhost-minetogether) (Сообщалось о проблемах с макетами при масштабе GUI выше 2)
* [Mod Menu](https://www.curseforge.com/minecraft/mc-mods/modmenu) (Обычно совместим; если кнопка «Моды» дублируется или не настраивается, установите **Главное меню -> Моды -> Mod Menu -> Кнопка «Моды»** в значение **Рядом**)
* [Modern Online Picture Frames](https://www.curseforge.com/minecraft/mc-mods/online-picture-frame) (Сбой — см. [эту проблему](https://github.com/Keksuccino/FancyMenu/issues/776))
* [Not Enough Animations](https://www.curseforge.com/minecraft/mc-mods/not-enough-animations) (Сообщалось о совместимости с версией 1.16+ и несовместимости с версией 1.12)
* [Optiscale](https://www.curseforge.com/minecraft/mc-mods/optiscale) (Нарушает работу интерфейса FancyMenu; кнопки нельзя нажимать)
* [Pack Menu](https://www.curseforge.com/minecraft/mc-mods/packmenu)
* [Panorama Screens](https://modrinth.com/mod/panorama-screens) (Сообщалось о конфликте между системами настройки меню)
* [QuestCraft](https://github.com/QuestCraftPlusPlus/QuestCraft) (Игра не загружается)
* [RandomPatches](https://www.curseforge.com/minecraft/mc-mods/randompatches-forge) (Работает, если в настройках мода указано `patchMinecraftClass = false`)
* [Remove Reloading Screen](https://www.curseforge.com/minecraft/mc-mods/rrls) (Сообщалось о нарушении работы FancyMenu и Drippy Loading Screen)
* [Replay Mod](https://www.replaymod.com/download/) (Работает, если установить для `mainMenuButton` значение **BIG** в `<game-directory>/config/replaymod.json`)
* [Seamless Loading Screen](https://www.curseforge.com/minecraft/mc-mods/seamless-loading-screen) (Вызывает сбой игры)
* [Slight Gui Modifications](https://www.curseforge.com/minecraft/mc-mods/slight-gui-modifications)
* [Skin Layers 3D](https://www.curseforge.com/minecraft/mc-mods/skin-layers-3d) (Сообщалось о совместимости с версией 1.16+ и несовместимости с версией 1.12)
* [Smooth Scrolling Everywhere](https://www.curseforge.com/minecraft/mc-mods/smooth-scrolling-everywhere)
* [Sound Filters](https://www.curseforge.com/minecraft/mc-mods/sound-filters) (Расширение аудио не работает при установленном моде)
* [Sound Physics Remastered](https://www.curseforge.com/minecraft/mc-mods/sound-physics-remastered) (Расширение аудио не работает при установленном моде)
* [Stylish Effects](https://www.curseforge.com/minecraft/mc-mods/stylish-effects) (При первом отображении главное меню не загружает макеты)
* [Supplementaries](https://www.curseforge.com/minecraft/mc-mods/supplementaries) (При настройке экрана конфигурации может случайно происходить сбой; удалите проблемный макет из `<game-directory>/config/fancymenu/customization/`)
* [Terraria Craft](https://www.curseforge.com/minecraft/mc-mods/terraria-craft)
* [The Dalek Mod](https://www.curseforge.com/minecraft/mc-mods/the-dalek-mod) (Работает, если отключить пользовательское главное меню в настройках мода)
* [ThonkUtil](https://www.curseforge.com/minecraft/mc-mods/thonkutil) (Работает, но в настоящее время добавляет в главное меню неудаляемый текст)
* [Trade Uses](https://modrinth.com/mod/trade-uses) (Вызывает сбои в меню торговли с жителями — возможно, только при установленном моде «Easy Villagers»)
* [VanillaFix](https://www.curseforge.com/minecraft/mc-mods/vanillafix) (Можно использовать, но некоторые пользователи сообщают о проблемах с экраном сбоя VanillaFix)
* [FireplaceMode](https://www.curseforge.com/minecraft/mc-mods/fireplacemode) (При установленном моде экран паузы иногда сбрасывает настройки)
* [Respackopts](https://www.curseforge.com/minecraft/mc-mods/respackopts) (Работает, но только если отключить настройки для экрана ресурспаков)
* [Bind Pizzeria](https://modrinth.com/mod/jjpizza) (Нарушает отображение текста в контекстных меню FancyMenu)
* [EnhancedTooltips](https://www.curseforge.com/minecraft/mc-mods/enhancedtooltips) (Нарушает работу всплывающих подсказок FancyMenu)
* [Skin Shuffle](https://modrinth.com/mod/skinshuffle) (Сущность игрока, добавляемая этим модом в меню, не настраивается через FancyMenu)
* [Wakes](https://modrinth.com/mod/wakes) (Вызывает сбой игры при запуске из-за `IncompatibleClassChangeError` — мод не может переопределить финальный метод `AbstractSliderButton.getSprite()`, который является финальным только из-за изменения его видимости модом Wakes; дополнительную информацию см. в проблемах на GitHub: [Goby56/wakes #215](https://github.com/Goby56/wakes/issues/215), [Keksuccino/FancyMenu #1733](https://github.com/Keksuccino/FancyMenu/issues/1733))
* [Essential](https://www.curseforge.com/minecraft/mc-mods/essential-mod) (Дополнительную информацию см. на [этой странице](/essential))
