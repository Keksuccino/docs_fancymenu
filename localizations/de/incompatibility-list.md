---
title: Liste der Inkompatibilitäten
description: >-
  Von FancyMenu blockierte Bildschirme und von der Community gemeldete
  Inkompatibilitäten.
---
# Inkompatibilitäten

# Bildschirme, bei denen die Anpassung absichtlich deaktiviert ist

FancyMenu blockiert Bildschirme, die zu bestimmten Mod-Paketpfaden passen, um Abstürze oder fehlerhaftes Verhalten zu verhindern. Der Anpassungs-Schalter, das Overlay und Layouts sind auf passenden Bildschirmen nicht verfügbar.

Diese Sperren verwenden das Java-Paket der Bildschirmklasse statt einer manuell ausgewählten Liste einzelner Bildschirme. Eine Regel kann daher mehrere Bildschirme desselben Mods oder verwandter Pakete betreffen.

Zu den blockierten Bildschirmgruppen gehören:

- Create
- Panoramica
- Alex's Mobs
- Screenshot Viewer
- Twilight Forest
- Supplementaries
- OptiFine; verwende [OptiFine-Alternativen](./optifine-alternatives)
- SlimeKnights und Tinkers' Construct
- MidnightDust-Mods
- SkinSwapper
- Die Konfigurationsbildschirme von FancyMenu selbst; [Benutzerdefinierte GUIs](./custom-guis) sind ausgenommen
- Immersive Engineering
- Dungeonz
- RPG-Hud
- Cobblemon und einige mit Cobblemon verbundene Bildschirme
- Applied Energistics 2
- Karten-Mods von Xaero

# Von der Community gemeldete Inkompatibilitäten

Die Einträge unten sind Meldungen aus der Community und keine von FancyMenu selbst blockierten Bildschirme. Die Kompatibilität kann sich je nach Version von FancyMenu, Minecraft, Loader und Modpack ändern.

* [Animated Loading Screen](https://modrinth.com/mod/animated-loading-screen) (Lässt Menüs fehlerhaft aussehen)
* [Animated Mojang Logo](https://www.curseforge.com/minecraft/mc-mods/animated-mojang-logo) (Layouts werden manchmal nicht geladen; beschädigt außerdem Drippy Loading Screen)
* [Bedrockify](https://www.curseforge.com/minecraft/mc-mods/bedrockify) (Kompatibel, wenn du alle Menüänderungen des Mods deaktivierst, zumindest für die Menüs, die du anpassen möchtest)
* [BetterFPS](https://www.curseforge.com/minecraft/mc-mods/betterfps) (Schaltflächen und Menüs dieses Mods sind nicht anpassbar)
* [Chat Colors](https://www.curseforge.com/minecraft/mc-mods/chat-colours) (Absturz beim Start)
* [Chloride](https://modrinth.com/mod/chloride) (Der FPS-Platzhalter funktioniert nicht, wenn dieser Mod installiert ist)
* [Colormatic](https://www.curseforge.com/minecraft/mc-mods/colormatic) (Starke Verzögerungen beim Starten von MC und beschädigt die Audio-Funktionen von FM)
* [Controllable](https://www.curseforge.com/minecraft/mc-mods/controllable) (Benutzerdefinierte Schaltflächen, die mit FancyMenu zu Menüs hinzugefügt werden, sind über die Funktion „Virtual Mouse“ von Controllable nicht anklickbar)
* [Controlify](https://modrinth.com/mod/controlify) (Absturz gemeldet; siehe [Issue #1144](https://github.com/Keksuccino/FancyMenu/issues/1144))
* [Crash To Main Menu](https://www.curseforge.com/minecraft/mc-mods/crash-to-main-menu)
* [Custom Loading Screen](https://www.curseforge.com/minecraft/mc-mods/better-loading-screen)
* [Custom Main Menu](https://www.curseforge.com/minecraft/mc-mods/custom-main-menu)
* [Debugify](https://www.curseforge.com/minecraft/mc-mods/debugify) (Verwende stattdessen [Modern Debugify](https://www.curseforge.com/minecraft/mc-mods/modern-debugify))
* [Dynamic Surroundings](https://www.curseforge.com/minecraft/mc-mods/dynamic-surroundings) (Soll Audio-Elemente beschädigen)
* [EnhancedVisuals](https://www.curseforge.com/minecraft/mc-mods/enhancedvisuals) (Gemeldete Probleme mit Animationen und transparenten Hintergründen)
* [Entity Model Features](https://modrinth.com/mod/entity-model-features) (Absturz gemeldet; siehe [Issue #1115](https://github.com/Keksuccino/FancyMenu/issues/1115))
* [Fossils and Archeology Revival](https://www.curseforge.com/minecraft/mc-mods/fossils) (Funktioniert im Spiel, aber das benutzerdefinierte Hauptmenü wird nicht unterstützt — kann in der Konfiguration deaktiviert werden)
* [Holographic Renderers](https://www.curseforge.com/minecraft/mc-mods/holographic-renderers) (Absturz beim Start)
* [Ice and Fire](https://www.curseforge.com/minecraft/mc-mods/ice-and-fire-dragons) (Funktioniert, wenn das benutzerdefinierte Hauptmenü in der Konfiguration deaktiviert ist)
* [Jurassicraft](https://www.curseforge.com/minecraft/mc-mods/jurassicraft) (Absturz beim Start, wenn Anpassungen für seine GUIs aktiviert werden — lösche sie aus `<game-directory>/config/fancymenu/customizablemenus.txt`)
* [Legacy4J](https://www.curseforge.com/minecraft/mc-mods/legacy-minecraft) (Lässt das Spiel abstürzen)
* [MalisisCore](https://www.curseforge.com/minecraft/mc-mods/malisiscore) (Beschädigt die Anpassung des Hauptmenüs)
* [Main Menu Scale Mod](https://www.curseforge.com/minecraft/mc-mods/main-menu-scale)
* [MCA Reborn](https://www.curseforge.com/minecraft/mc-mods/minecraft-comes-alive-reborn) (Funktioniert, aber einige seiner Menüs beschädigen die Menüleiste von FM und/oder sind nicht anpassbar)
* [Minecraft Comes Alive](https://www.curseforge.com/minecraft/mc-mods/minecraft-comes-alive-mca) (Als kompatibel gemeldet, aber seine Menüs sind nicht anpassbar)
* [MineTogether](https://www.curseforge.com/minecraft/mc-mods/creeperhost-minetogether) (Gemeldete Layoutprobleme oberhalb von GUI-Skalierung 2)
* [Mod Menu](https://www.curseforge.com/minecraft/mc-mods/modmenu) (In der Regel kompatibel; für einen doppelten oder nicht anpassbaren Mods-Button setze **Main Menu -> Mods -> Mod Menu -> Mods Button** auf **Adjacent**)
* [Modern Online Picture Frames](https://www.curseforge.com/minecraft/mc-mods/online-picture-frame) (Absturz — siehe [dieses Issue](https://github.com/Keksuccino/FancyMenu/issues/776))
* [Not Enough Animations](https://www.curseforge.com/minecraft/mc-mods/not-enough-animations) (Als kompatibel auf 1.16+ und inkompatibel auf 1.12 gemeldet)
* [Optiscale](https://www.curseforge.com/minecraft/mc-mods/optiscale) (Beschädigt die Benutzeroberfläche von FancyMenu; Schaltflächen sind nicht anklickbar)
* [Pack Menu](https://www.curseforge.com/minecraft/mc-mods/packmenu)
* [Panorama Screens](https://modrinth.com/mod/panorama-screens) (Gemeldeter Konflikt zwischen den Anpassungssystemen der Menüs)
* [QuestCraft](https://github.com/QuestCraftPlusPlus/QuestCraft) (Spiel lädt nicht)
* [RandomPatches](https://www.curseforge.com/minecraft/mc-mods/randompatches-forge) (Funktioniert, wenn `patchMinecraftClass = false` in der Konfiguration gesetzt ist)
* [Remove Reloading Screen](https://www.curseforge.com/minecraft/mc-mods/rrls) (Soll FancyMenu und Drippy Loading Screen beschädigen)
* [Replay Mod](https://www.replaymod.com/download/) (Funktioniert, wenn du `mainMenuButton` in `<game-directory>/config/replaymod.json` auf **BIG** setzt)
* [Seamless Loading Screen](https://www.curseforge.com/minecraft/mc-mods/seamless-loading-screen) (Lässt das Spiel abstürzen)
* [Slight Gui Modifications](https://www.curseforge.com/minecraft/mc-mods/slight-gui-modifications)
* [Skin Layers 3D](https://www.curseforge.com/minecraft/mc-mods/skin-layers-3d) (Als kompatibel auf 1.16+ und inkompatibel auf 1.12 gemeldet)
* [Smooth Scrolling Everywhere](https://www.curseforge.com/minecraft/mc-mods/smooth-scrolling-everywhere)
* [Sound Filters](https://www.curseforge.com/minecraft/mc-mods/sound-filters) (Die Audio-Erweiterung funktioniert mit installiertem Mod nicht)
* [Sound Physics Remastered](https://www.curseforge.com/minecraft/mc-mods/sound-physics-remastered) (Die Audio-Erweiterung funktioniert mit installiertem Mod nicht)
* [Stylish Effects](https://www.curseforge.com/minecraft/mc-mods/stylish-effects) (Das Hauptmenü lädt beim ersten Anzeigen keine Layouts)
* [Supplementaries](https://www.curseforge.com/minecraft/mc-mods/supplementaries) (Stürzt beim Anpassen seines Konfigurationsbildschirms zufällig ab; lösche das problematische Layout aus `<game-directory>/config/fancymenu/customization/`)
* [Terraria Craft](https://www.curseforge.com/minecraft/mc-mods/terraria-craft)
* [The Dalek Mod](https://www.curseforge.com/minecraft/mc-mods/the-dalek-mod) (Funktioniert, wenn das benutzerdefinierte Hauptmenü in der Konfiguration deaktiviert ist)
* [ThonkUtil](https://www.curseforge.com/minecraft/mc-mods/thonkutil) (Funktioniert, fügt dem Hauptmenü aber derzeit einen nicht entfernbaren Text hinzu)
* [Trade Uses](https://modrinth.com/mod/trade-uses) (Verursacht Abstürze im Handelsmenü von Dorfbewohnern — möglicherweise nur, wenn auch „Easy Villagers“ installiert ist)
* [VanillaFix](https://www.curseforge.com/minecraft/mc-mods/vanillafix) (Benutzbar, aber einige Nutzer berichten von Problemen mit dem VanillaFix-Absturzbildschirm)
* [FireplaceMode](https://www.curseforge.com/minecraft/mc-mods/fireplacemode) (Der Pause-Bildschirm setzt seine Anpassungen mit diesem Mod manchmal zurück)
* [Respackopts](https://www.curseforge.com/minecraft/mc-mods/respackopts) (Funktioniert, aber nur, wenn du Anpassungen für den Ressourcenpaket-Bildschirm deaktivierst)
* [Bind Pizzeria](https://modrinth.com/mod/jjpizza) (Beschädigt die Textdarstellung in den Kontextmenüs von FancyMenu)
* [EnhancedTooltips](https://www.curseforge.com/minecraft/mc-mods/enhancedtooltips) (Beschädigt die Tooltips von FancyMenu)
* [Skin Shuffle](https://modrinth.com/mod/skinshuffle) (Die von diesem Mod zu Menüs hinzugefügte Spieler-Entität ist über FancyMenu nicht anpassbar)
