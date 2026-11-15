---
title: Список несумісностей
description: 'Екрани, заблоковані FancyMenu, і несумісності, про які повідомила спільнота.'
sourceBlobSha: f5f938751a166796106f5074dc55137bcd40f203
---
# Екрани, для яких налаштування навмисно вимкнено

FancyMenu блокує екрани, що відповідають певним шляхам пакетів модів, щоб запобігти збоям або некоректній роботі. Перемикач налаштування, накладання та макети недоступні на таких екранах.

Для цих блокувань використовується Java-пакет класу екрана, а не вручну підібраний список окремих екранів. Тому одне правило може впливати на кілька екранів того самого мода або пов’язаних пакетів.

До заблокованих груп екранів належать:

- Create
- Panoramica
- Alex's Mobs
- Screenshot Viewer
- Twilight Forest
- Supplementaries
- OptiFine; використовуйте [альтернативи OptiFine](./optifine-alternatives)
- SlimeKnights і Tinkers' Construct
- Моди MidnightDust
- SkinSwapper
- Immersive Engineering
- Dungeonz
- RPG-Hud
- Cobblemon і деякі пов’язані з Cobblemon екрани
- Applied Energistics 2
- Картографічні моди Xaero

# Несумісності, про які повідомила спільнота

Наведені нижче записи є повідомленнями спільноти, а не екранами, заблокованими самим FancyMenu. Сумісність може змінюватися залежно від версій FancyMenu, Minecraft, завантажувача та модів у збірці.

* [Animated Loading Screen](https://modrinth.com/mod/animated-loading-screen) (Меню виглядають зламаними)
* [Animated Mojang Logo](https://www.curseforge.com/minecraft/mc-mods/animated-mojang-logo) (Макети іноді не завантажуються; також ламає Drippy Loading Screen)
* [Bedrockify](https://www.curseforge.com/minecraft/mc-mods/bedrockify) (Сумісний, якщо вимкнути всі зміни меню цього мода, принаймні для меню, які потрібно налаштувати)
* [BetterFPS](https://www.curseforge.com/minecraft/mc-mods/betterfps) (Кнопки та меню цього мода неможливо налаштувати)
* [Chat Colors](https://www.curseforge.com/minecraft/mc-mods/chat-colours) (Збій під час запуску)
* [Chloride](https://modrinth.com/mod/chloride) (Заповнювач FPS не працює, якщо цей мод встановлено)
* [Colormatic](https://www.curseforge.com/minecraft/mc-mods/colormatic) (Сильні затримки під час запуску Minecraft і проблеми з аудіофункціями FM)
* [Controllable](https://www.curseforge.com/minecraft/mc-mods/controllable) (Користувацькі кнопки, додані до меню за допомогою FancyMenu, неможливо натискати через функцію «Віртуальна миша» мода Controllable)
* [Controlify](https://modrinth.com/mod/controlify) (Повідомлялося про збій; див. [проблему №1144](https://github.com/Keksuccino/FancyMenu/issues/1144))
* [Crash To Main Menu](https://www.curseforge.com/minecraft/mc-mods/crash-to-main-menu)
* [Custom Loading Screen](https://www.curseforge.com/minecraft/mc-mods/better-loading-screen)
* [Custom Main Menu](https://www.curseforge.com/minecraft/mc-mods/custom-main-menu)
* [Debugify](https://www.curseforge.com/minecraft/mc-mods/debugify) (Замість нього використовуйте [Modern Debugify](https://www.curseforge.com/minecraft/mc-mods/modern-debugify))
* [Dynamic Surroundings](https://www.curseforge.com/minecraft/mc-mods/dynamic-surroundings) (Повідомлялося, що він ламає аудіоелементи)
* [EnhancedVisuals](https://www.curseforge.com/minecraft/mc-mods/enhancedvisuals) (Повідомлялося про проблеми з анімаціями та прозорим тлом)
* [Entity Model Features](https://modrinth.com/mod/entity-model-features) (Повідомлялося про збій; див. [проблему №1115](https://github.com/Keksuccino/FancyMenu/issues/1115))
* [Fossils and Archeology Revival](https://www.curseforge.com/minecraft/mc-mods/fossils) (Працює в грі, але користувацьке головне меню не підтримується — його можна вимкнути в конфігурації)
* [Holographic Renderers](https://www.curseforge.com/minecraft/mc-mods/holographic-renderers) (Збій під час запуску)
* [Ice and Fire](https://www.curseforge.com/minecraft/mc-mods/ice-and-fire-dragons) (Працює, якщо вимкнути користувацьке головне меню в конфігурації)
* [Jurassicraft](https://www.curseforge.com/minecraft/mc-mods/jurassicraft) (Завершує роботу під час запуску, якщо ввімкнути налаштування його графічних інтерфейсів — видаліть їх із `<game-directory>/config/fancymenu/customizablemenus.txt`)
* [Legacy4J](https://www.curseforge.com/minecraft/mc-mods/legacy-minecraft) (Викликає збій гри)
* [MalisisCore](https://www.curseforge.com/minecraft/mc-mods/malisiscore) (Ламає налаштування головного меню)
* [Main Menu Scale Mod](https://www.curseforge.com/minecraft/mc-mods/main-menu-scale)
* [MCA Reborn](https://www.curseforge.com/minecraft/mc-mods/minecraft-comes-alive-reborn) (Працює, але деякі його меню ламають панель меню FM та/або не підлягають налаштуванню)
* [Minecraft Comes Alive](https://www.curseforge.com/minecraft/mc-mods/minecraft-comes-alive-mca) (Повідомлялося про сумісність, але його меню не підлягають налаштуванню)
* [MineTogether](https://www.curseforge.com/minecraft/mc-mods/creeperhost-minetogether) (Повідомлялося про проблеми з макетами за масштабу GUI понад 2)
* [Mod Menu](https://www.curseforge.com/minecraft/mc-mods/modmenu) (Зазвичай сумісний; якщо кнопка «Моди» дублюється або не налаштовується, встановіть **Головне меню -> Моди -> Mod Menu -> Кнопка «Моди»** у значення **Поруч**)
* [Modern Online Picture Frames](https://www.curseforge.com/minecraft/mc-mods/online-picture-frame) (Збій — див. [цю проблему](https://github.com/Keksuccino/FancyMenu/issues/776))
* [Not Enough Animations](https://www.curseforge.com/minecraft/mc-mods/not-enough-animations) (Повідомлялося про сумісність у версіях 1.16+ і несумісність у версії 1.12)
* [Optiscale](https://www.curseforge.com/minecraft/mc-mods/optiscale) (Ламає інтерфейс FancyMenu; кнопки не натискаються)
* [Pack Menu](https://www.curseforge.com/minecraft/mc-mods/packmenu)
* [Panorama Screens](https://modrinth.com/mod/panorama-screens) (Повідомлялося про конфлікт між системами налаштування меню)
* [QuestCraft](https://github.com/QuestCraftPlusPlus/QuestCraft) (Гра не завантажується)
* [RandomPatches](https://www.curseforge.com/minecraft/mc-mods/randompatches-forge) (Працює, якщо в його конфігурації встановлено `patchMinecraftClass = false`)
* [Remove Reloading Screen](https://www.curseforge.com/minecraft/mc-mods/rrls) (Повідомлялося, що він ламає FancyMenu та Drippy Loading Screen)
* [Replay Mod](https://www.replaymod.com/download/) (Працює, якщо встановити для `mainMenuButton` значення **BIG** у `<game-directory>/config/replaymod.json`)
* [Seamless Loading Screen](https://www.curseforge.com/minecraft/mc-mods/seamless-loading-screen) (Викликає збій гри)
* [Slight Gui Modifications](https://www.curseforge.com/minecraft/mc-mods/slight-gui-modifications)
* [Skin Layers 3D](https://www.curseforge.com/minecraft/mc-mods/skin-layers-3d) (Повідомлялося про сумісність у версіях 1.16+ і несумісність у версії 1.12)
* [Smooth Scrolling Everywhere](https://www.curseforge.com/minecraft/mc-mods/smooth-scrolling-everywhere)
* [Sound Filters](https://www.curseforge.com/minecraft/mc-mods/sound-filters) (Аудіорозширення не працюватиме, якщо цей мод встановлено)
* [Sound Physics Remastered](https://www.curseforge.com/minecraft/mc-mods/sound-physics-remastered) (Аудіорозширення не працюватиме, якщо цей мод встановлено)
* [Stylish Effects](https://www.curseforge.com/minecraft/mc-mods/stylish-effects) (Під час першого відкриття головне меню не завантажує макети)
* [Supplementaries](https://www.curseforge.com/minecraft/mc-mods/supplementaries) (Випадково завершує роботу під час налаштування екрана конфігурації; видаліть проблемний макет із `<game-directory>/config/fancymenu/customization/`)
* [Terraria Craft](https://www.curseforge.com/minecraft/mc-mods/terraria-craft)
* [The Dalek Mod](https://www.curseforge.com/minecraft/mc-mods/the-dalek-mod) (Працює, якщо вимкнути його користувацьке головне меню в конфігурації)
* [ThonkUtil](https://www.curseforge.com/minecraft/mc-mods/thonkutil) (Працює, але наразі додає до головного меню текст, який неможливо видалити)
* [Trade Uses](https://modrinth.com/mod/trade-uses) (Викликає збої в меню торгівлі із селянами — можливо, лише коли також встановлено «Easy Villagers»)
* [VanillaFix](https://www.curseforge.com/minecraft/mc-mods/vanillafix) (Придатний до використання, але деякі користувачі повідомляють про проблеми з екраном збою VanillaFix)
* [FireplaceMode](https://www.curseforge.com/minecraft/mc-mods/fireplacemode) (Екран паузи іноді скидає налаштування, якщо цей мод встановлено)
* [Respackopts](https://www.curseforge.com/minecraft/mc-mods/respackopts) (Працює, але лише якщо вимкнути налаштування екрана пакета ресурсів)
* [Bind Pizzeria](https://modrinth.com/mod/jjpizza) (Ламає відтворення тексту в контекстних меню FancyMenu)
* [EnhancedTooltips](https://www.curseforge.com/minecraft/mc-mods/enhancedtooltips) (Ламає підказки FancyMenu)
* [Skin Shuffle](https://modrinth.com/mod/skinshuffle) (Сутність гравця, яку цей мод додає до меню, неможливо налаштувати через FancyMenu
* [Wakes](https://modrinth.com/mod/wakes) (Гра завершує роботу під час запуску через `IncompatibleClassChangeError` — мод не може перевизначити фінальний метод `AbstractSliderButton.getSprite()`, який є фінальним лише через зміну його видимості модом Wakes; докладнішу інформацію див. у проблемах на GitHub: [Goby56/wakes #215](https://github.com/Goby56/wakes/issues/215), [Keksuccino/FancyMenu #1733](https://github.com/Keksuccino/FancyMenu/issues/1733))
* [Essential](https://www.curseforge.com/minecraft/mc-mods/essential-mod) (Докладнішу інформацію див. на [цій сторінці](/essential))
