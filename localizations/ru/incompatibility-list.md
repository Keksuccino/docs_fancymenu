---
title: Список несовместимостей
description: >-
  Экраны, заблокированные FancyMenu, и несовместимости, о которых сообщило
  сообщество.
sourceBlobSha: 2f89775eade27d0a90dd3805b5c58d779676bdbd
---
# Экраны, для которых настройка намеренно отключена

FancyMenu блокирует экраны, соответствующие определённым путям пакетов модов, чтобы избежать сбоев и некорректной работы. Для таких экранов недоступны переключатель настройки, оверлей и макеты.

При блокировке учитывается Java-пакет класса экрана, а не вручную составленный список отдельных экранов. Поэтому одно правило может затронуть несколько экранов одного мода или связанных пакетов.

Заблокированные группы экранов:

- Create
- Panoramica
- Alex's Mobs
- Screenshot Viewer
- Twilight Forest
- Supplementaries
- OptiFine; используйте [альтернативы OptiFine](/optifine-alternatives)
- SlimeKnights и Tinkers' Construct
- моды MidnightDust
- SkinSwapper
- Immersive Engineering
- Dungeonz
- RPG-Hud
- Cobblemon и некоторые связанные с ним экраны
- Applied Energistics 2
- моды карт Xaero

# Несовместимости, о которых сообщило сообщество

Приведённые ниже сведения получены от сообщества. Эти экраны не блокируются самим FancyMenu. Совместимость может меняться в зависимости от версий FancyMenu, Minecraft, загрузчика и модов в сборке.

* [Animated Loading Screen](https://modrinth.com/mod/animated-loading-screen) (Из-за него меню выглядят неисправными)
* [Animated Mojang Logo](https://www.curseforge.com/minecraft/mc-mods/animated-mojang-logo) (Макеты иногда не загружаются; также нарушает работу Drippy Loading Screen)
* [Bedrockify](https://www.curseforge.com/minecraft/mc-mods/bedrockify) (Совместим, если отключить все изменения меню, вносимые этим модом, по крайней мере для меню, которые вы хотите настроить)
* [BetterFPS](https://www.curseforge.com/minecraft/mc-mods/betterfps) (Кнопки и меню этого мода нельзя настроить)
* [Chat Colors](https://www.curseforge.com/minecraft/mc-mods/chat-colours) (Сбой при запуске)
* [Chloride](https://modrinth.com/mod/chloride) (При установленном моде не работает заполнитель FPS)
* [Colormatic](https://www.curseforge.com/minecraft/mc-mods/colormatic) (Вызывает сильные задержки при запуске MC и нарушает работу аудиофункций FM)
* [Controllable](https://www.curseforge.com/minecraft/mc-mods/controllable) (Пользовательские кнопки, добавленные в меню с помощью FancyMenu, нельзя нажимать функцией «Виртуальная мышь» в Controllable)
* [Controlify](https://modrinth.com/mod/controlify) (Сообщалось о сбое; см. [issue #1144](https://github.com/Keksuccino/FancyMenu/issues/1144))
* [Crash To Main Menu](https://www.curseforge.com/minecraft/mc-mods/crash-to-main-menu)
* [Custom Loading Screen](https://www.curseforge.com/minecraft/mc-mods/better-loading-screen)
* [Custom Main Menu](https://www.curseforge.com/minecraft/mc-mods/custom-main-menu)
* [Debugify](https://www.curseforge.com/minecraft/mc-mods/debugify) (Вместо него используйте [Modern Debugify](https://www.curseforge.com/minecraft/mc-mods/modern-debugify))
* [Dynamic Surroundings](https://www.curseforge.com/minecraft/mc-mods/dynamic-surroundings) (Сообщалось, что он нарушает работу аудиоэлементов)
* [EnhancedVisuals](https://www.curseforge.com/minecraft/mc-mods/enhancedvisuals) (Сообщалось о проблемах с анимацией и полупрозрачным фоном)
* [Entity Model Features](https://modrinth.com/mod/entity-model-features) (Сообщалось о сбое; см. [issue #1115](https://github.com/Keksuccino/FancyMenu/issues/1115))
* [Fossils and Archeology Revival](https://www.curseforge.com/minecraft/mc-mods/fossils) (В игре работает, но пользовательское главное меню не поддерживается — его можно отключить в конфигурации мода)
* [Holographic Renderers](https://www.curseforge.com/minecraft/mc-mods/holographic-renderers) (Сбой при запуске)
* [Ice and Fire](https://www.curseforge.com/minecraft/mc-mods/ice-and-fire-dragons) (Работает, если отключить пользовательское главное меню в конфигурации мода)
* [Jurassicraft](https://www.curseforge.com/minecraft/mc-mods/jurassicraft) (Сбой при запуске, если включить настройку его графических интерфейсов — удалите их из `<game-directory>/config/fancymenu/customizablemenus.txt`)
* [Legacy4J](https://www.curseforge.com/minecraft/mc-mods/legacy-minecraft) (Вызывает сбой игры)
* [MalisisCore](https://www.curseforge.com/minecraft/mc-mods/malisiscore) (Нарушает работу настройки главного меню)
* [Main Menu Scale Mod](https://www.curseforge.com/minecraft/mc-mods/main-menu-scale)
* [MCA Reborn](https://www.curseforge.com/minecraft/mc-mods/minecraft-comes-alive-reborn) (Работает, но некоторые его меню нарушают работу строки меню FM и/или не поддаются настройке)
* [Minecraft Comes Alive](https://www.curseforge.com/minecraft/mc-mods/minecraft-comes-alive-mca) (По сообщениям, совместим, но его меню нельзя настроить)
* [MineTogether](https://www.curseforge.com/minecraft/mc-mods/creeperhost-minetogether) (Сообщалось о проблемах с макетом при масштабе интерфейса выше 2)
* [Mod Menu](https://www.curseforge.com/minecraft/mc-mods/modmenu) (Обычно совместим; если кнопка «Моды» дублируется или не поддаётся настройке, выберите **Главное меню -> Моды -> Mod Menu -> Кнопка «Моды»** и установите значение **Рядом**)
* [Modern Online Picture Frames](https://www.curseforge.com/minecraft/mc-mods/online-picture-frame) (Сбой — см. [это сообщение](https://github.com/Keksuccino/FancyMenu/issues/776))
* [Not Enough Animations](https://www.curseforge.com/minecraft/mc-mods/not-enough-animations) (По сообщениям, совместим с версиями 1.16 и новее и несовместим с версией 1.12)
* [Optiscale](https://www.curseforge.com/minecraft/mc-mods/optiscale) (Нарушает работу интерфейса FancyMenu; кнопки нельзя нажимать)
* [Pack Menu](https://www.curseforge.com/minecraft/mc-mods/packmenu)
* [Panorama Screens](https://modrinth.com/mod/panorama-screens) (Сообщалось о конфликте систем настройки меню)
* [QuestCraft](https://github.com/QuestCraftPlusPlus/QuestCraft) (Игра не загружается)
* [RandomPatches](https://www.curseforge.com/minecraft/mc-mods/randompatches-forge) (Работает, если в конфигурации мода указано `patchMinecraftClass = false`)
* [Remove Reloading Screen](https://www.curseforge.com/minecraft/mc-mods/rrls) (По сообщениям, нарушает работу FancyMenu и Drippy Loading Screen)
* [Replay Mod](https://www.replaymod.com/download/) (Работает, если установить для `mainMenuButton` значение **BIG** в файле `<game-directory>/config/replaymod.json`)
* [Seamless Loading Screen](https://www.curseforge.com/minecraft/mc-mods/seamless-loading-screen) (Вызывает сбой игры)
* [Slight Gui Modifications](https://www.curseforge.com/minecraft/mc-mods/slight-gui-modifications)
* [Skin Layers 3D](https://www.curseforge.com/minecraft/mc-mods/skin-layers-3d) (По сообщениям, совместим с версиями 1.16 и новее и несовместим с версией 1.12)
* [Smooth Scrolling Everywhere](https://www.curseforge.com/minecraft/mc-mods/smooth-scrolling-everywhere)
* [Sound Filters](https://www.curseforge.com/minecraft/mc-mods/sound-filters) (При установленном моде аудиорасширение не работает)
* [Sound Physics Remastered](https://www.curseforge.com/minecraft/mc-mods/sound-physics-remastered) (При установленном моде аудиорасширение не работает)
* [Stylish Effects](https://www.curseforge.com/minecraft/mc-mods/stylish-effects) (При первом отображении главного меню макеты не загружаются)
* [Supplementaries](https://www.curseforge.com/minecraft/mc-mods/supplementaries) (При настройке экрана конфигурации иногда возникают случайные сбои; удалите проблемный макет из `<game-directory>/config/fancymenu/customization/`)
* [Terraria Craft](https://www.curseforge.com/minecraft/mc-mods/terraria-craft)
* [The Dalek Mod](https://www.curseforge.com/minecraft/mc-mods/the-dalek-mod) (Работает, если отключить пользовательское главное меню мода в конфигурации)
* [ThonkUtil](https://www.curseforge.com/minecraft/mc-mods/thonkutil) (Работает, но сейчас добавляет в главное меню неудаляемый текст)
* [Trade Uses](https://modrinth.com/mod/trade-uses) (Вызывает сбои в меню торговли с жителями — возможно, только если также установлен «Easy Villagers»)
* [VanillaFix](https://www.curseforge.com/minecraft/mc-mods/vanillafix) (Можно использовать, но некоторые пользователи сообщают о проблемах с экраном сбоя VanillaFix)
* [FireplaceMode](https://www.curseforge.com/minecraft/mc-mods/fireplacemode) (При установленном моде настройки экрана паузы иногда сбрасываются)
* [Respackopts](https://www.curseforge.com/minecraft/mc-mods/respackopts) (Работает, только если отключить настройку экрана наборов ресурсов)
* [Bind Pizzeria](https://modrinth.com/mod/jjpizza) (Нарушает отображение текста в контекстных меню FancyMenu)
* [EnhancedTooltips](https://www.curseforge.com/minecraft/mc-mods/enhancedtooltips) (Нарушает работу подсказок FancyMenu)
* [Skin Shuffle](https://modrinth.com/mod/skinshuffle) (Сущность игрока, добавляемая этим модом в меню, не поддаётся настройке через FancyMenu
* [Wakes](https://modrinth.com/mod/wakes) (Игра вылетает при запуске из-за `IncompatibleClassChangeError` — мод не может переопределить финальный метод `AbstractSliderButton.getSprite()`, который стал финальным только потому, что Wakes изменяет его видимость. Подробнее см. в сообщениях на GitHub: [Goby56/wakes #215](https://github.com/Goby56/wakes/issues/215), [Keksuccino/FancyMenu #1733](https://github.com/Keksuccino/FancyMenu/issues/1733))
* [Essential](https://www.curseforge.com/minecraft/mc-mods/essential-mod) (Подробнее см. [эту страницу](/essential))
