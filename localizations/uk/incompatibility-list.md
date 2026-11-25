---
title: Список несумісностей
description: 'Екрани, заблоковані FancyMenu, та повідомлення спільноти про несумісності.'
sourceBlobSha: 2f89775eade27d0a90dd3805b5c58d779676bdbd
---
# Екрани, налаштування яких навмисно вимкнено

FancyMenu блокує екрани, що відповідають певним шляхам пакетів модів, щоб запобігти збоям або некоректній роботі. На таких екранах недоступні перемикач налаштування, накладка та макети.

Для блокування використовуються Java-пакети класу екрана, а не вручну вибраний список окремих екранів. Тому одне правило може впливати на кілька екранів того самого мода або пов’язаних пакетів.

Заблоковані групи екранів:

- Create
- Panoramica
- Alex's Mobs
- Screenshot Viewer
- Twilight Forest
- Supplementaries
- OptiFine; скористайтеся [альтернативами OptiFine](/optifine-alternatives)
- SlimeKnights і Tinkers' Construct
- моди MidnightDust
- SkinSwapper
- Immersive Engineering
- Dungeonz
- RPG-Hud
- Cobblemon і деякі пов’язані з Cobblemon екрани
- Applied Energistics 2
- картографічні моди Xaero

# Повідомлення спільноти про несумісності

Наведені нижче випадки — це повідомлення спільноти, а не екрани, які блокує сам FancyMenu. Сумісність може змінюватися залежно від версій FancyMenu, Minecraft, завантажувача та модів у збірці.

* [Animated Loading Screen](https://modrinth.com/mod/animated-loading-screen) (Через мод меню виглядають зламаними)
* [Animated Mojang Logo](https://www.curseforge.com/minecraft/mc-mods/animated-mojang-logo) (Макети іноді не завантажуються; також порушує роботу Drippy Loading Screen)
* [Bedrockify](https://www.curseforge.com/minecraft/mc-mods/bedrockify) (Сумісний, якщо вимкнути всі зміни меню, які вносить мод, принаймні для меню, які ви хочете налаштувати)
* [BetterFPS](https://www.curseforge.com/minecraft/mc-mods/betterfps) (Кнопки й меню цього мода не можна налаштовувати)
* [Chat Colors](https://www.curseforge.com/minecraft/mc-mods/chat-colours) (Збій під час запуску)
* [Chloride](https://modrinth.com/mod/chloride) (Заповнювач FPS не працює, якщо встановлено цей мод)
* [Colormatic](https://www.curseforge.com/minecraft/mc-mods/colormatic) (Сильно гальмує запуск MC і порушує роботу аудіофункцій FM)
* [Controllable](https://www.curseforge.com/minecraft/mc-mods/controllable) (Користувацькі кнопки, додані до меню через FancyMenu, не можна натискати за допомогою функції «Віртуальна миша» в Controllable)
* [Controlify](https://modrinth.com/mod/controlify) (Повідомляли про збій; див. [проблему №1144](https://github.com/Keksuccino/FancyMenu/issues/1144))
* [Crash To Main Menu](https://www.curseforge.com/minecraft/mc-mods/crash-to-main-menu)
* [Custom Loading Screen](https://www.curseforge.com/minecraft/mc-mods/better-loading-screen)
* [Custom Main Menu](https://www.curseforge.com/minecraft/mc-mods/custom-main-menu)
* [Debugify](https://www.curseforge.com/minecraft/mc-mods/debugify) (Натомість використовуйте [Modern Debugify](https://www.curseforge.com/minecraft/mc-mods/modern-debugify))
* [Dynamic Surroundings](https://www.curseforge.com/minecraft/mc-mods/dynamic-surroundings) (Повідомляли, що мод порушує роботу аудіоелементів)
* [EnhancedVisuals](https://www.curseforge.com/minecraft/mc-mods/enhancedvisuals) (Повідомляли про проблеми з анімацією та напівпрозорим тлом)
* [Entity Model Features](https://modrinth.com/mod/entity-model-features) (Повідомляли про збій; див. [проблему №1115](https://github.com/Keksuccino/FancyMenu/issues/1115))
* [Fossils and Archeology Revival](https://www.curseforge.com/minecraft/mc-mods/fossils) (Працює в грі, але користувацьке головне меню не підтримується — його можна вимкнути в конфігурації мода)
* [Holographic Renderers](https://www.curseforge.com/minecraft/mc-mods/holographic-renderers) (Збій під час запуску)
* [Ice and Fire](https://www.curseforge.com/minecraft/mc-mods/ice-and-fire-dragons) (Працює, якщо вимкнути користувацьке головне меню в конфігурації мода)
* [Jurassicraft](https://www.curseforge.com/minecraft/mc-mods/jurassicraft) (Гра аварійно завершує роботу під час запуску, якщо ввімкнути налаштування його графічних інтерфейсів — видаліть їх із `<game-directory>/config/fancymenu/customizablemenus.txt`)
* [Legacy4J](https://www.curseforge.com/minecraft/mc-mods/legacy-minecraft) (Призводить до аварійного завершення гри)
* [MalisisCore](https://www.curseforge.com/minecraft/mc-mods/malisiscore) (Порушує налаштування головного меню)
* [Main Menu Scale Mod](https://www.curseforge.com/minecraft/mc-mods/main-menu-scale)
* [MCA Reborn](https://www.curseforge.com/minecraft/mc-mods/minecraft-comes-alive-reborn) (Працює, але деякі його меню порушують роботу панелі меню FM та/або не піддаються налаштуванню)
* [Minecraft Comes Alive](https://www.curseforge.com/minecraft/mc-mods/minecraft-comes-alive-mca) (Повідомляли про сумісність, але його меню не можна налаштувати)
* [MineTogether](https://www.curseforge.com/minecraft/mc-mods/creeperhost-minetogether) (Повідомляли про проблеми з макетами за масштабу інтерфейсу вище 2)
* [Mod Menu](https://www.curseforge.com/minecraft/mc-mods/modmenu) (Зазвичай сумісний; якщо кнопка Mods дублюється або її не можна налаштувати, установіть **Головне меню -> Mods -> Mod Menu -> Кнопка Mods** у значення **Поруч**)
* [Modern Online Picture Frames](https://www.curseforge.com/minecraft/mc-mods/online-picture-frame) (Збій — див. [цю проблему](https://github.com/Keksuccino/FancyMenu/issues/776))
* [Not Enough Animations](https://www.curseforge.com/minecraft/mc-mods/not-enough-animations) (Повідомляли про сумісність з версіями 1.16+ і несумісність із 1.12)
* [Optiscale](https://www.curseforge.com/minecraft/mc-mods/optiscale) (Порушує роботу інтерфейсу FancyMenu; на кнопки не можна натискати)
* [Pack Menu](https://www.curseforge.com/minecraft/mc-mods/packmenu)
* [Panorama Screens](https://modrinth.com/mod/panorama-screens) (Повідомляли про конфлікт між системами налаштування меню)
* [QuestCraft](https://github.com/QuestCraftPlusPlus/QuestCraft) (Гра не завантажується)
* [RandomPatches](https://www.curseforge.com/minecraft/mc-mods/randompatches-forge) (Працює, якщо в конфігурації встановити `patchMinecraftClass = false`)
* [Remove Reloading Screen](https://www.curseforge.com/minecraft/mc-mods/rrls) (Повідомляли, що мод порушує роботу FancyMenu та Drippy Loading Screen)
* [Replay Mod](https://www.replaymod.com/download/) (Працює, якщо встановити для `mainMenuButton` значення **BIG** у файлі `<game-directory>/config/replaymod.json`)
* [Seamless Loading Screen](https://www.curseforge.com/minecraft/mc-mods/seamless-loading-screen) (Призводить до аварійного завершення гри)
* [Slight Gui Modifications](https://www.curseforge.com/minecraft/mc-mods/slight-gui-modifications)
* [Skin Layers 3D](https://www.curseforge.com/minecraft/mc-mods/skin-layers-3d) (Повідомляли про сумісність з версіями 1.16+ і несумісність із 1.12)
* [Smooth Scrolling Everywhere](https://www.curseforge.com/minecraft/mc-mods/smooth-scrolling-everywhere)
* [Sound Filters](https://www.curseforge.com/minecraft/mc-mods/sound-filters) (Аудіорозширення не працюватиме, якщо встановлено цей мод)
* [Sound Physics Remastered](https://www.curseforge.com/minecraft/mc-mods/sound-physics-remastered) (Аудіорозширення не працюватиме, якщо встановлено цей мод)
* [Stylish Effects](https://www.curseforge.com/minecraft/mc-mods/stylish-effects) (Під час першого відкриття головне меню не завантажує макети)
* [Supplementaries](https://www.curseforge.com/minecraft/mc-mods/supplementaries) (Під час налаштування екрана конфігурації іноді стається збій; видаліть проблемний макет із `<game-directory>/config/fancymenu/customization/`)
* [Terraria Craft](https://www.curseforge.com/minecraft/mc-mods/terraria-craft)
* [The Dalek Mod](https://www.curseforge.com/minecraft/mc-mods/the-dalek-mod) (Працює, якщо вимкнути користувацьке головне меню в конфігурації мода)
* [ThonkUtil](https://www.curseforge.com/minecraft/mc-mods/thonkutil) (Працює, але наразі додає до головного меню текст, який не можна прибрати)
* [Trade Uses](https://modrinth.com/mod/trade-uses) (Спричиняє збої в меню торгівлі з жителями — можливо, лише за умови, що також встановлено «Easy Villagers»)
* [VanillaFix](https://www.curseforge.com/minecraft/mc-mods/vanillafix) (Модом можна користуватися, але деякі користувачі повідомляють про проблеми з екраном збою VanillaFix)
* [FireplaceMode](https://www.curseforge.com/minecraft/mc-mods/fireplacemode) (Якщо встановлено цей мод, налаштування екрана паузи іноді скидаються)
* [Respackopts](https://www.curseforge.com/minecraft/mc-mods/respackopts) (Працює, але лише якщо вимкнути налаштування для екрана пакета ресурсів)
* [Bind Pizzeria](https://modrinth.com/mod/jjpizza) (Порушує відображення тексту в контекстних меню FancyMenu)
* [EnhancedTooltips](https://www.curseforge.com/minecraft/mc-mods/enhancedtooltips) (Порушує роботу підказок FancyMenu)
* [Skin Shuffle](https://modrinth.com/mod/skinshuffle) (Сутність гравця, яку цей мод додає до меню, не можна налаштувати через FancyMenu
* [Wakes](https://modrinth.com/mod/wakes) (Гра аварійно завершує роботу під час запуску через `IncompatibleClassChangeError` — мод не може перевизначити фінальний метод `AbstractSliderButton.getSprite()`, який є фінальним лише тому, що Wakes змінює його видимість. Докладніше див. проблеми на GitHub: [Goby56/wakes #215](https://github.com/Goby56/wakes/issues/215), [Keksuccino/FancyMenu #1733](https://github.com/Keksuccino/FancyMenu/issues/1733))
* [Essential](https://www.curseforge.com/minecraft/mc-mods/essential-mod) (Докладніше див. [цю сторінку](/essential))
