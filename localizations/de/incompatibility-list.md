---
title: Inkompatibilitätsliste
description: >-
  Von FancyMenu blockierte Bildschirme und von der Community gemeldete
  Inkompatibilitäten.
sourceBlobSha: f5f938751a166796106f5074dc55137bcd40f203
---
# Bildschirme, auf denen die Anpassung absichtlich deaktiviert ist

FancyMenu blockiert Bildschirme, die bestimmten Paketpfaden von Mods entsprechen, um Abstürze oder fehlerhaftes Verhalten zu verhindern. Der Anpassungsschalter, das Overlay und Layouts sind auf entsprechenden Bildschirmen nicht verfügbar.

Diese Blockierungen verwenden das Java-Paket der Bildschirmklasse statt einer von Hand zusammengestellten Liste einzelner Bildschirme. Eine Regel kann daher mehrere Bildschirme derselben Mod oder verwandter Pakete betreffen.

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
- Immersive Engineering
- Dungeonz
- RPG-Hud
- Cobblemon und einige mit Cobblemon verbundene Bildschirme
- Applied Energistics 2
- Xaeros Karten-Mods

# Von der Community gemeldete Inkompatibilitäten

Die folgenden Einträge sind Meldungen aus der Community und keine von FancyMenu selbst blockierten Bildschirme. Die Kompatibilität kann sich abhängig von den Versionen von FancyMenu, Minecraft, dem Loader und den Mods in einem Modpack ändern.

* [Animated Loading Screen](https://modrinth.com/mod/animated-loading-screen) (Lässt Menüs fehlerhaft aussehen)
* [Animated Mojang Logo](https://www.curseforge.com/minecraft/mc-mods/animated-mojang-logo) (Layouts werden manchmal nicht geladen; außerdem wird Drippy Loading Screen beeinträchtigt)
* [Bedrockify](https://www.curseforge.com/minecraft/mc-mods/bedrockify) (Kompatibel, wenn du alle Menüänderungen der Mod deaktivierst, zumindest für die Menüs, die du anpassen möchtest)
* [BetterFPS](https://www.curseforge.com/minecraft/mc-mods/betterfps) (Schaltflächen und Menüs dieser Mod können nicht angepasst werden)
* [Chat Colors](https://www.curseforge.com/minecraft/mc-mods/chat-colours) (Absturz beim Start)
* [Chloride](https://modrinth.com/mod/chloride) (Der FPS-Platzhalter funktioniert nicht, wenn diese Mod installiert ist)
* [Colormatic](https://www.curseforge.com/minecraft/mc-mods/colormatic) (Starke Verzögerungen beim Start von Minecraft und Beeinträchtigung der Audiofunktionen von FM)
* [Controllable](https://www.curseforge.com/minecraft/mc-mods/controllable) (Mit FancyMenu zu Menüs hinzugefügte benutzerdefinierte Schaltflächen können über die Funktion „Virtuelle Maus“ von Controllable nicht angeklickt werden)
* [Controlify](https://modrinth.com/mod/controlify) (Absturz gemeldet; siehe [Issue #1144](https://github.com/Keksuccino/FancyMenu/issues/1144))
* [Crash To Main Menu](https://www.curseforge.com/minecraft/mc-mods/crash-to-main-menu)
* [Custom Loading Screen](https://www.curseforge.com/minecraft/mc-mods/better-loading-screen)
* [Custom Main Menu](https://www.curseforge.com/minecraft/mc-mods/custom-main-menu)
* [Debugify](https://www.curseforge.com/minecraft/mc-mods/debugify) (Verwende stattdessen [Modern Debugify](https://www.curseforge.com/minecraft/mc-mods/modern-debugify))
* [Dynamic Surroundings](https://www.curseforge.com/minecraft/mc-mods/dynamic-surroundings) (Beeinträchtigt laut Meldungen Audioelemente)
* [EnhancedVisuals](https://www.curseforge.com/minecraft/mc-mods/enhancedvisuals) (Probleme mit Animationen und transparenten Hintergründen gemeldet)
* [Entity Model Features](https://modrinth.com/mod/entity-model-features) (Absturz gemeldet; siehe [Issue #1115](https://github.com/Keksuccino/FancyMenu/issues/1115))
* [Fossils and Archeology Revival](https://www.curseforge.com/minecraft/mc-mods/fossils) (Funktioniert im Spiel, aber das benutzerdefinierte Hauptmenü wird nicht unterstützt – es kann in der Konfiguration deaktiviert werden)
* [Holographic Renderers](https://www.curseforge.com/minecraft/mc-mods/holographic-renderers) (Absturz beim Start)
* [Ice and Fire](https://www.curseforge.com/minecraft/mc-mods/ice-and-fire-dragons) (Funktioniert, wenn das benutzerdefinierte Hauptmenü in der Konfiguration deaktiviert ist)
* [Jurassicraft](https://www.curseforge.com/minecraft/mc-mods/jurassicraft) (Stürzt beim Start ab, wenn Anpassungen für die GUIs aktiviert werden – lösche sie aus `<game-directory>/config/fancymenu/customizablemenus.txt`)
* [Legacy4J](https://www.curseforge.com/minecraft/mc-mods/legacy-minecraft) (Lässt das Spiel abstürzen)
* [MalisisCore](https://www.curseforge.com/minecraft/mc-mods/malisiscore) (Beeinträchtigt die Anpassung des Hauptmenüs)
* [Main Menu Scale Mod](https://www.curseforge.com/minecraft/mc-mods/main-menu-scale)
* [MCA Reborn](https://www.curseforge.com/minecraft/mc-mods/minecraft-comes-alive-reborn) (Funktioniert, aber einige Menüs beeinträchtigen die Menüleiste von FM und/oder können nicht angepasst werden)
* [Minecraft Comes Alive](https://www.curseforge.com/minecraft/mc-mods/minecraft-comes-alive-mca) (Als kompatibel gemeldet, aber die Menüs können nicht angepasst werden)
* [MineTogether](https://www.curseforge.com/minecraft/mc-mods/creeperhost-minetogether) (Probleme mit Layouts oberhalb einer GUI-Skalierung von 2 gemeldet)
* [Mod Menu](https://www.curseforge.com/minecraft/mc-mods/modmenu) (Normalerweise kompatibel; bei einer doppelten oder nicht anpassbaren Mods-Schaltfläche setze **Hauptmenü -> Mods -> Mod Menu -> Mods-Schaltfläche** auf **Angrenzend**)
* [Modern Online Picture Frames](https://www.curseforge.com/minecraft/mc-mods/online-picture-frame) (Absturz – siehe [dieses Issue](https://github.com/Keksuccino/FancyMenu/issues/776))
* [Not Enough Animations](https://www.curseforge.com/minecraft/mc-mods/not-enough-animations) (Für 1.16+ als kompatibel und für 1.12 als inkompatibel gemeldet)
* [Optiscale](https://www.curseforge.com/minecraft/mc-mods/optiscale) (Beeinträchtigt die Benutzeroberfläche von FancyMenu; Schaltflächen können nicht angeklickt werden)
* [Pack Menu](https://www.curseforge.com/minecraft/mc-mods/packmenu)
* [Panorama Screens](https://modrinth.com/mod/panorama-screens) (Konflikt zwischen den Menüanpassungssystemen gemeldet)
* [QuestCraft](https://github.com/QuestCraftPlusPlus/QuestCraft) (Das Spiel kann nicht geladen werden)
* [RandomPatches](https://www.curseforge.com/minecraft/mc-mods/randompatches-forge) (Funktioniert, wenn `patchMinecraftClass = false` in der Konfiguration gesetzt ist)
* [Remove Reloading Screen](https://www.curseforge.com/minecraft/mc-mods/rrls) (Beeinträchtigt laut Meldungen FancyMenu und Drippy Loading Screen)
* [Replay Mod](https://www.replaymod.com/download/) (Funktioniert, wenn du `mainMenuButton` in `<game-directory>/config/replaymod.json` auf **BIG** setzt)
* [Seamless Loading Screen](https://www.curseforge.com/minecraft/mc-mods/seamless-loading-screen) (Lässt das Spiel abstürzen)
* [Slight Gui Modifications](https://www.curseforge.com/minecraft/mc-mods/slight-gui-modifications)
* [Skin Layers 3D](https://www.curseforge.com/minecraft/mc-mods/skin-layers-3d) (Für 1.16+ als kompatibel und für 1.12 als inkompatibel gemeldet)
* [Smooth Scrolling Everywhere](https://www.curseforge.com/minecraft/mc-mods/smooth-scrolling-everywhere)
* [Sound Filters](https://www.curseforge.com/minecraft/mc-mods/sound-filters) (Die Audioerweiterung funktioniert nicht, wenn diese Mod installiert ist)
* [Sound Physics Remastered](https://www.curseforge.com/minecraft/mc-mods/sound-physics-remastered) (Die Audioerweiterung funktioniert nicht, wenn diese Mod installiert ist)
* [Stylish Effects](https://www.curseforge.com/minecraft/mc-mods/stylish-effects) (Das Hauptmenü lädt Layouts beim ersten Anzeigen nicht)
* [Supplementaries](https://www.curseforge.com/minecraft/mc-mods/supplementaries) (Stürzt beim Anpassen des Konfigurationsbildschirms zufällig ab; lösche das problematische Layout aus `<game-directory>/config/fancymenu/customization/`)
* [Terraria Craft](https://www.curseforge.com/minecraft/mc-mods/terraria-craft)
* [The Dalek Mod](https://www.curseforge.com/minecraft/mc-mods/the-dalek-mod) (Funktioniert, wenn das benutzerdefinierte Hauptmenü in der Konfiguration deaktiviert ist)
* [ThonkUtil](https://www.curseforge.com/minecraft/mc-mods/thonkutil) (Funktioniert, fügt dem Hauptmenü derzeit jedoch einen nicht entfernbaren Text hinzu)
* [Trade Uses](https://modrinth.com/mod/trade-uses) (Verursacht Abstürze im Handelmenü der Dorfbewohner – möglicherweise nur, wenn zusätzlich „Easy Villagers“ installiert ist)
* [VanillaFix](https://www.curseforge.com/minecraft/mc-mods/vanillafix) (Nutzbar, aber einige Benutzer melden Probleme mit dem Absturzbildschirm von VanillaFix)
* [FireplaceMode](https://www.curseforge.com/minecraft/mc-mods/fireplacemode) (Der Pausenbildschirm setzt seine Anpassungen manchmal zurück, wenn diese Mod installiert ist)
* [Respackopts](https://www.curseforge.com/minecraft/mc-mods/respackopts) (Funktioniert, aber nur, wenn du Anpassungen für den Ressourcenpaket-Bildschirm deaktivierst)
* [Bind Pizzeria](https://modrinth.com/mod/jjpizza) (Beeinträchtigt die Textdarstellung in den Kontextmenüs von FancyMenu)
* [EnhancedTooltips](https://www.curseforge.com/minecraft/mc-mods/enhancedtooltips) (Beeinträchtigt die Tooltips von FancyMenu)
* [Skin Shuffle](https://modrinth.com/mod/skinshuffle) (Die von dieser Mod zu Menüs hinzugefügte Spielerkreatur kann nicht über FancyMenu angepasst werden
* [Wakes](https://modrinth.com/mod/wakes) (Lässt das Spiel beim Start aufgrund eines `IncompatibleClassChangeError` abstürzen – die Mod kann eine finale Methode `AbstractSliderButton.getSprite()` nicht überschreiben, die nur deshalb final ist, weil Wakes ihre Sichtbarkeit verändert; weitere Informationen findest du in den GitHub-Issues: [Goby56/wakes #215](https://github.com/Goby56/wakes/issues/215), [Keksuccino/FancyMenu #1733](https://github.com/Keksuccino/FancyMenu/issues/1733))
* [Essential](https://www.curseforge.com/minecraft/mc-mods/essential-mod) (Weitere Informationen findest du auf [dieser Seite](/essential))
