---
title: Список несумісностей
description: 'Екрани, заблоковані FancyMenu, та несумісності, про які повідомила спільнота.'
---
# Несумісності

# Екрани, на яких налаштування навмисно вимкнено

FancyMenu блокує екрани, що відповідають певним шляхам пакетів модів, щоб запобігти збоям або некоректній роботі. Перемикач налаштувань, накладка та макети недоступні на екранах, що відповідають цим правилам.

Ці блокування використовують Java-пакет класу екрана, а не вручну підібраний список окремих екранів. Тому одне правило може впливати на кілька екранів з одного мода або суміжних пакетів.

Заблоковані групи екранів включають:

- Create
- Panoramica
- Alex's Mobs
- Screenshot Viewer
- Twilight Forest
- Supplementaries
- OptiFine; використовуйте [OptiFine Alternatives](./optifine-alternatives)
- SlimeKnights і Tinkers' Construct
- моди MidnightDust
- SkinSwapper
- екрани конфігурації самого FancyMenu; [Custom GUIs](./custom-guis) не включені
- Immersive Engineering
- Dungeonz
- RPG-Hud
- Cobblemon і деякі пов’язані з Cobblemon екрани
- Applied Energistics 2
- моди карт Xaero

# Несумісності, про які повідомила спільнота

Наведені нижче записи — це повідомлення спільноти, а не екрани, заблоковані самим FancyMenu. Сумісність може змінюватися залежно від версій FancyMenu, Minecraft, завантажувача та модів у збірці.

* [Animated Loading Screen](https://modrinth.com/mod/animated-loading-screen) (Робить меню виглядати зламаним)
* [Animated Mojang Logo](https://www.curseforge.com/minecraft/mc-mods/animated-mojang-logo) (Макети інколи не завантажуються; також ламає Drippy Loading Screen)
* [Bedrockify](https://www.curseforge.com/minecraft/mc-mods/bedrockify) (Сумісний, якщо вимкнути всі модифікації меню цього мода, принаймні для тих меню, які ви хочете налаштувати)
* [BetterFPS](https://www.curseforge.com/minecraft/mc-mods/betterfps) (Кнопки та меню цього мода не можна налаштувати)
* [Chat Colors](https://www.curseforge.com/minecraft/mc-mods/chat-colours) (Збій під час запуску)
* [Chloride](https://modrinth.com/mod/chloride) (Плейсхолдер FPS не працює, коли встановлено цей мод)
* [Colormatic](https://www.curseforge.com/minecraft/mc-mods/colormatic) (Сильні затримки під час запуску MC і ламає аудіо-функції FM)
* [Controllable](https://www.curseforge.com/minecraft/mc-mods/controllable) (Кнопки, додані до меню за допомогою FancyMenu, не можна натискати через функцію «Virtual Mouse» від Controllable)
* [Controlify](https://modrinth.com/mod/controlify) (Повідомляється про збій; див. [issue #1144](https://github.com/Keksuccino/FancyMenu/issues/1144))
* [Crash To Main Menu](https://www.curseforge.com/minecraft/mc-mods/crash-to-main-menu)
* [Custom Loading Screen](https://www.curseforge.com/minecraft/mc-mods/better-loading-screen)
* [Custom Main Menu](https://www.curseforge.com/minecraft/mc-mods/custom-main-menu)
* [Debugify](https://www.curseforge.com/minecraft/mc-mods/debugify) (Використовуйте [Modern Debugify](https://www.curseforge.com/minecraft/mc-mods/modern-debugify) замість нього)
* [Dynamic Surroundings](https://www.curseforge.com/minecraft/mc-mods/dynamic-surroundings) (Повідомляється, що ламає аудіо-елементи)
* [EnhancedVisuals](https://www.curseforge.com/minecraft/mc-mods/enhancedvisuals) (Повідомляються проблеми з анімацією та напівпрозорим фоном)
* [Entity Model Features](https://modrinth.com/mod/entity-model-features) (Повідомляється про збій; див. [issue #1115](https://github.com/Keksuccino/FancyMenu/issues/1115))
* [Fossils and Archeology Revival](https://www.curseforge.com/minecraft/mc-mods/fossils) (Працює в грі, але власне головне меню не підтримується — його можна вимкнути в конфігурації)
* [Holographic Renderers](https://www.curseforge.com/minecraft/mc-mods/holographic-renderers) (Збій під час запуску)
* [Ice and Fire](https://www.curseforge.com/minecraft/mc-mods/ice-and-fire-dragons) (Працює, якщо вимкнути власне головне меню в конфігурації)
* [Jurassicraft](https://www.curseforge.com/minecraft/mc-mods/jurassicraft) (Під час запуску стався збій при ввімкненні налаштувань для його GUI — видаліть їх із `<game-directory>/config/fancymenu/customizablemenus.txt`)
* [Legacy4J](https://www.curseforge.com/minecraft/mc-mods/legacy-minecraft) (Викликає збій гри)
* [MalisisCore](https://www.curseforge.com/minecraft/mc-mods/malisiscore) (Ламає налаштування головного меню)
* [Main Menu Scale Mod](https://www.curseforge.com/minecraft/mc-mods/main-menu-scale)
* [MCA Reborn](https://www.curseforge.com/minecraft/mc-mods/minecraft-comes-alive-reborn) (Працює, але деякі його меню ламають панель меню FM і/або не підлягають налаштуванню)
* [Minecraft Comes Alive](https://www.curseforge.com/minecraft/mc-mods/minecraft-comes-alive-mca) (Повідомляється про сумісність, але його меню не можна налаштувати)
* [MineTogether](https://www.curseforge.com/minecraft/mc-mods/creeperhost-minetogether) (Повідомляються проблеми з макетами при GUI scale вище 2)
* [Mod Menu](https://www.curseforge.com/minecraft/mc-mods/modmenu) (Зазвичай сумісний; якщо кнопка Mods дублюється або не підлягає налаштуванню, встановіть **Main Menu -> Mods -> Mod Menu -> Mods Button** на **Adjacent**)
* [Modern Online Picture Frames](https://www.curseforge.com/minecraft/mc-mods/online-picture-frame) (Збій — див. [цей issue](https://github.com/Keksuccino/FancyMenu/issues/776))
* [Not Enough Animations](https://www.curseforge.com/minecraft/mc-mods/not-enough-animations) (Повідомляється як сумісний у 1.16+ і несумісний у 1.12)
* [Optiscale](https://www.curseforge.com/minecraft/mc-mods/optiscale) (Ламає інтерфейс FancyMenu; кнопки не натискаються)
* [Pack Menu](https://www.curseforge.com/minecraft/mc-mods/packmenu)
* [Panorama Screens](https://modrinth.com/mod/panorama-screens) (Повідомляється про конфлікт між системами налаштування меню)
* [QuestCraft](https://github.com/QuestCraftPlusPlus/QuestCraft) (Гра не завантажується)
* [RandomPatches](https://www.curseforge.com/minecraft/mc-mods/randompatches-forge) (Працює, якщо `patchMinecraftClass = false` у конфігурації)
* [Remove Reloading Screen](https://www.curseforge.com/minecraft/mc-mods/rrls) (Повідомляється, що ламає FancyMenu та Drippy Loading Screen)
* [Replay Mod](https://www.replaymod.com/download/) (Працює, якщо встановити `mainMenuButton` на **BIG** у `<game-directory>/config/replaymod.json`)
* [Seamless Loading Screen](https://www.curseforge.com/minecraft/mc-mods/seamless-loading-screen) (Викликає збій гри)
* [Slight Gui Modifications](https://www.curseforge.com/minecraft/mc-mods/slight-gui-modifications)
* [Skin Layers 3D](https://www.curseforge.com/minecraft/mc-mods/skin-layers-3d) (Повідомляється як сумісний у 1.16+ і несумісний у 1.12)
* [Smooth Scrolling Everywhere](https://www.curseforge.com/minecraft/mc-mods/smooth-scrolling-everywhere)
* [Sound Filters](https://www.curseforge.com/minecraft/mc-mods/sound-filters) (Аудіорозширення не працюватиме з цим модом)
* [Sound Physics Remastered](https://www.curseforge.com/minecraft/mc-mods/sound-physics-remastered) (Аудіорозширення не працюватиме з цим модом)
* [Stylish Effects](https://www.curseforge.com/minecraft/mc-mods/stylish-effects) (Головне меню не завантажує макети під час першого показу)
* [Supplementaries](https://www.curseforge.com/minecraft/mc-mods/supplementaries) (Випадково викликає збій під час налаштування екрана конфігурації; видаліть проблемний макет із `<game-directory>/config/fancymenu/customization/`)
* [Terraria Craft](https://www.curseforge.com/minecraft/mc-mods/terraria-craft)
* [The Dalek Mod](https://www.curseforge.com/minecraft/mc-mods/the-dalek-mod) (Працює, якщо вимкнути власне головне меню в конфігурації)
* [ThonkUtil](https://www.curseforge.com/minecraft/mc-mods/thonkutil) (Працює, але наразі додає до головного меню текст, який не можна прибрати)
* [Trade Uses](https://modrinth.com/mod/trade-uses) (Спричиняє збої в меню торгівлі селянина — можливо, лише якщо також встановлено “Easy Villagers”)
* [VanillaFix](https://www.curseforge.com/minecraft/mc-mods/vanillafix) (Можна використовувати, але деякі користувачі повідомляють про проблеми з екраном збою VanillaFix)
* [FireplaceMode](https://www.curseforge.com/minecraft/mc-mods/fireplacemode) (Екран паузи інколи скидає свої налаштування, коли встановлено цей мод)
* [Respackopts](https://www.curseforge.com/minecraft/mc-mods/respackopts) (Працює, але лише якщо вимкнути налаштування для екрана Resource Pack)
* [Bind Pizzeria](https://modrinth.com/mod/jjpizza) (Ламає відображення тексту в контекстних меню FancyMenu)
* [EnhancedTooltips](https://www.curseforge.com/minecraft/mc-mods/enhancedtooltips) (Ламає підказки FancyMenu)
* [Skin Shuffle](https://modrinth.com/mod/skinshuffle) (Елемент гравця, який цей мод додає до меню, не можна налаштувати через FancyMenu)
