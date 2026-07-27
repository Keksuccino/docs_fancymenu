---
title: Lista niekompatybilności
description: >-
  Ekrany blokowane przez FancyMenu oraz niekompatybilności zgłaszane przez
  społeczność.
---
# Niekompatybilności

# Ekrany, na których personalizacja jest celowo wyłączona

FancyMenu blokuje ekrany pasujące do określonych ścieżek pakietów modów, aby zapobiec awariom lub nieprawidłowemu działaniu. Przełącznik personalizacji, nakładka i układy są niedostępne na pasujących ekranach.

Blokady te wykorzystują pakiet Java klasy ekranu, a nie ręcznie wybraną listę pojedynczych ekranów. Jedna reguła może więc wpływać na kilka ekranów z tego samego moda lub powiązanych pakietów.

Do zablokowanych grup ekranów należą:

- Create
- Panoramica
- Alex's Mobs
- Screenshot Viewer
- Twilight Forest
- Supplementaries
- OptiFine; użyj [Alternatyw dla OptiFine](./optifine-alternatives)
- SlimeKnights i Tinkers' Construct
- mody MidnightDust
- SkinSwapper
- własne ekrany konfiguracji FancyMenu; wyłączone są [Custom GUIs](./custom-guis)
- Immersive Engineering
- Dungeonz
- RPG-Hud
- Cobblemon i niektóre ekrany powiązane z Cobblemon
- Applied Energistics 2
- mody map Xaero

# Niekompatybilności zgłaszane przez społeczność

Poniższe pozycje pochodzą ze zgłoszeń społeczności, a nie z ekranów blokowanych bezpośrednio przez FancyMenu. Kompatybilność może się zmieniać w zależności od wersji FancyMenu, Minecrafta, loadera i modów w paczce.

* [Animated Loading Screen](https://modrinth.com/mod/animated-loading-screen) (Sprawia, że menu wyglądają na uszkodzone)
* [Animated Mojang Logo](https://www.curseforge.com/minecraft/mc-mods/animated-mojang-logo) (Układy czasami się nie ładują; psuje też Drippy Loading Screen)
* [Bedrockify](https://www.curseforge.com/minecraft/mc-mods/bedrockify) (Działa, gdy wyłączysz wszystkie modyfikacje menu tego moda, przynajmniej dla menu, które chcesz dostosować)
* [BetterFPS](https://www.curseforge.com/minecraft/mc-mods/betterfps) (Przyciski i menu tego moda nie są konfigurowalne)
* [Chat Colors](https://www.curseforge.com/minecraft/mc-mods/chat-colours) (Awaria przy uruchamianiu)
* [Chloride](https://modrinth.com/mod/chloride) (Zmienna zastępcza FPS nie działa, gdy ten mod jest zainstalowany)
* [Colormatic](https://www.curseforge.com/minecraft/mc-mods/colormatic) (Duże lagi przy uruchamianiu MC i psuje obsługę dźwięku FM)
* [Controllable](https://www.curseforge.com/minecraft/mc-mods/controllable) (Niestandardowe przyciski dodane do menu przez FancyMenu nie są klikalne przez funkcję „Virtual Mouse” moda Controllable)
* [Controlify](https://modrinth.com/mod/controlify) (Zgłoszona awaria; zobacz [problem #1144](https://github.com/Keksuccino/FancyMenu/issues/1144))
* [Crash To Main Menu](https://www.curseforge.com/minecraft/mc-mods/crash-to-main-menu)
* [Custom Loading Screen](https://www.curseforge.com/minecraft/mc-mods/better-loading-screen)
* [Custom Main Menu](https://www.curseforge.com/minecraft/mc-mods/custom-main-menu)
* [Debugify](https://www.curseforge.com/minecraft/mc-mods/debugify) (Użyj zamiast tego [Modern Debugify](https://www.curseforge.com/minecraft/mc-mods/modern-debugify))
* [Dynamic Surroundings](https://www.curseforge.com/minecraft/mc-mods/dynamic-surroundings) (Zgłaszane psucie elementów audio)
* [EnhancedVisuals](https://www.curseforge.com/minecraft/mc-mods/enhancedvisuals) (Zgłaszane problemy z animacją i półprzezroczystym tłem)
* [Entity Model Features](https://modrinth.com/mod/entity-model-features) (Zgłoszona awaria; zobacz [problem #1115](https://github.com/Keksuccino/FancyMenu/issues/1115))
* [Fossils and Archeology Revival](https://www.curseforge.com/minecraft/mc-mods/fossils) (Działa w grze, ale niestandardowe główne menu nie jest obsługiwane — można je wyłączyć w konfiguracji)
* [Holographic Renderers](https://www.curseforge.com/minecraft/mc-mods/holographic-renderers) (Awaria przy uruchamianiu)
* [Ice and Fire](https://www.curseforge.com/minecraft/mc-mods/ice-and-fire-dragons) (Działa, jeśli niestandardowe główne menu zostanie wyłączone w konfiguracji)
* [Jurassicraft](https://www.curseforge.com/minecraft/mc-mods/jurassicraft) (Crashes on start when enabling customizations for its GUIs—delete them from `<game-directory>/config/fancymenu/customizablemenus.txt`)
* [Legacy4J](https://www.curseforge.com/minecraft/mc-mods/legacy-minecraft) (Powoduje awarię gry)
* [MalisisCore](https://www.curseforge.com/minecraft/mc-mods/malisiscore) (Psuje personalizację głównego menu)
* [Main Menu Scale Mod](https://www.curseforge.com/minecraft/mc-mods/main-menu-scale)
* [MCA Reborn](https://www.curseforge.com/minecraft/mc-mods/minecraft-comes-alive-reborn) (Działa, ale niektóre jego menu psują pasek menu FM i/lub nie są konfigurowalne)
* [Minecraft Comes Alive](https://www.curseforge.com/minecraft/mc-mods/minecraft-comes-alive-mca) (Zgłaszana kompatybilność, ale jego menu nie są konfigurowalne)
* [MineTogether](https://www.curseforge.com/minecraft/mc-mods/creeperhost-minetogether) (Zgłaszane problemy z układem powyżej skali GUI 2)
* [Mod Menu](https://www.curseforge.com/minecraft/mc-mods/modmenu) (Zazwyczaj kompatybilny; w przypadku zduplikowanego lub niekonfigurowalnego przycisku Mods ustaw **Main Menu -> Mods -> Mod Menu -> Mods Button** na **Adjacent**)
* [Modern Online Picture Frames](https://www.curseforge.com/minecraft/mc-mods/online-picture-frame) (Awaria — zobacz [ten problem](https://github.com/Keksuccino/FancyMenu/issues/776))
* [Not Enough Animations](https://www.curseforge.com/minecraft/mc-mods/not-enough-animations) (Zgłaszana kompatybilność w wersjach 1.16+ i niekompatybilność w 1.12)
* [Optiscale](https://www.curseforge.com/minecraft/mc-mods/optiscale) (Psuje interfejs FancyMenu; przyciski nie są klikalne)
* [Pack Menu](https://www.curseforge.com/minecraft/mc-mods/packmenu)
* [Panorama Screens](https://modrinth.com/mod/panorama-screens) (Zgłaszany konflikt między systemami personalizacji menu)
* [QuestCraft](https://github.com/QuestCraftPlusPlus/QuestCraft) (Gra nie ładuje się)
* [RandomPatches](https://www.curseforge.com/minecraft/mc-mods/randompatches-forge) (Działa, jeśli `patchMinecraftClass = false` w konfiguracji)
* [Remove Reloading Screen](https://www.curseforge.com/minecraft/mc-mods/rrls) (Zgłaszane psucie FancyMenu i Drippy Loading Screen)
* [Replay Mod](https://www.replaymod.com/download/) (Działa po ustawieniu `mainMenuButton` na **BIG** w `<game-directory>/config/replaymod.json`)
* [Seamless Loading Screen](https://www.curseforge.com/minecraft/mc-mods/seamless-loading-screen) (Powoduje awarię gry)
* [Slight Gui Modifications](https://www.curseforge.com/minecraft/mc-mods/slight-gui-modifications)
* [Skin Layers 3D](https://www.curseforge.com/minecraft/mc-mods/skin-layers-3d) (Zgłaszana kompatybilność w wersjach 1.16+ i niekompatybilność w 1.12)
* [Smooth Scrolling Everywhere](https://www.curseforge.com/minecraft/mc-mods/smooth-scrolling-everywhere)
* [Sound Filters](https://www.curseforge.com/minecraft/mc-mods/sound-filters) (Rozszerzenie audio nie będzie działać przy zainstalowanym tym modzie)
* [Sound Physics Remastered](https://www.curseforge.com/minecraft/mc-mods/sound-physics-remastered) (Rozszerzenie audio nie będzie działać przy zainstalowanym tym modzie)
* [Stylish Effects](https://www.curseforge.com/minecraft/mc-mods/stylish-effects) (Główne menu nie wczytuje układów za pierwszym razem, gdy jest wyświetlane)
* [Supplementaries](https://www.curseforge.com/minecraft/mc-mods/supplementaries) (Losowo powoduje awarię podczas personalizowania ekranu konfiguracji; usuń problematyczny układ z `<game-directory>/config/fancymenu/customization/`)
* [Terraria Craft](https://www.curseforge.com/minecraft/mc-mods/terraria-craft)
* [The Dalek Mod](https://www.curseforge.com/minecraft/mc-mods/the-dalek-mod) (Działa, jeśli niestandardowe główne menu zostanie wyłączone w konfiguracji)
* [ThonkUtil](https://www.curseforge.com/minecraft/mc-mods/thonkutil) (Działa, ale obecnie dodaje do głównego menu tekst, którego nie da się usunąć)
* [Trade Uses](https://modrinth.com/mod/trade-uses) (Powoduje awarie w menu handlu z wieśniakiem — być może tylko wtedy, gdy zainstalowany jest też „Easy Villagers”)
* [VanillaFix](https://www.curseforge.com/minecraft/mc-mods/vanillafix) (Nadaje się do użycia, ale niektórzy użytkownicy zgłaszają problemy z ekranem awarii VanillaFix)
* [FireplaceMode](https://www.curseforge.com/minecraft/mc-mods/fireplacemode) (Ekran pauzy czasami resetuje swoje personalizacje, gdy ten mod jest zainstalowany)
* [Respackopts](https://www.curseforge.com/minecraft/mc-mods/respackopts) (Działa, ale tylko jeśli wyłączysz personalizacje dla ekranu pakietów zasobów)
* [Bind Pizzeria](https://modrinth.com/mod/jjpizza) (Psuje renderowanie tekstu w menu kontekstowych FancyMenu)
* [EnhancedTooltips](https://www.curseforge.com/minecraft/mc-mods/enhancedtooltips) (Psuje podpowiedzi FancyMenu)
* [Skin Shuffle](https://modrinth.com/mod/skinshuffle) (Encja gracza dodawana do menu przez ten mod nie jest konfigurowalna przez FancyMenu)
