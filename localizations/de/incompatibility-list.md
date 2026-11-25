---
title: Inkompatibilitätsliste
description: >-
  Bildschirme, die von FancyMenu blockiert werden, und von der Community
  gemeldete Inkompatibilitäten.
sourceBlobSha: 2f89775eade27d0a90dd3805b5c58d779676bdbd
---
# Bildschirme, deren Anpassung absichtlich deaktiviert ist

FancyMenu blockiert Bildschirme, deren Mod-Paketpfade bestimmten Mustern entsprechen, um Abstürze oder fehlerhaftes Verhalten zu verhindern. Auf diesen Bildschirmen sind der Anpassungsschalter, das Overlay und Layouts nicht verfügbar.

Diese Blockierungen basieren auf dem Java-Paket der Bildschirmklasse und nicht auf einer handverlesenen Liste einzelner Bildschirme. Eine Regel kann daher mehrere Bildschirme desselben Mods oder verwandter Pakete betreffen.

Zu den blockierten Bildschirmgruppen gehören:

- Create
- Panoramica
- Alex's Mobs
- Screenshot Viewer
- Twilight Forest
- Supplementaries
- OptiFine; verwende [OptiFine-Alternativen](/optifine-alternatives)
- SlimeKnights und Tinkers' Construct
- MidnightDust-Mods
- SkinSwapper
- Immersive Engineering
- Dungeonz
- RPG-Hud
- Cobblemon und einige Cobblemon-bezogene Bildschirme
- Applied Energistics 2
- Xaeros Karten-Mods

# Von der Community gemeldete Inkompatibilitäten

Bei den folgenden Einträgen handelt es sich um Meldungen aus der Community, nicht um Bildschirme, die von FancyMenu selbst blockiert werden. Die Kompatibilität kann sich je nach FancyMenu-, Minecraft-, Loader- und Mod-Versionen eines Modpacks ändern.

* [Animated Loading Screen](https://modrinth.com/mod/animated-loading-screen) (Lässt Menüs fehlerhaft aussehen)
* [Animated Mojang Logo](https://www.curseforge.com/minecraft/mc-mods/animated-mojang-logo) (Layouts werden manchmal nicht geladen; verursacht außerdem Probleme mit Drippy Loading Screen)
* [Bedrockify](https://www.curseforge.com/minecraft/mc-mods/bedrockify) (Kompatibel, wenn du alle Menüänderungen des Mods deaktivierst – zumindest für die Menüs, die du anpassen möchtest)
* [BetterFPS](https://www.curseforge.com/minecraft/mc-mods/betterfps) (Schaltflächen und Menüs dieses Mods lassen sich nicht anpassen)
* [Chat Colors](https://www.curseforge.com/minecraft/mc-mods/chat-colours) (Absturz beim Start)
* [Chloride](https://modrinth.com/mod/chloride) (Der FPS-Platzhalter funktioniert nicht, wenn dieser Mod installiert ist)
* [Colormatic](https://www.curseforge.com/minecraft/mc-mods/colormatic) (Starke Verzögerungen beim Start von Minecraft und Probleme mit der Audiofunktion von FancyMenu)
* [Controllable](https://www.curseforge.com/minecraft/mc-mods/controllable) (Mit FancyMenu zu Menüs hinzugefügte benutzerdefinierte Schaltflächen lassen sich nicht über die Funktion „Virtual Mouse“ von Controllable anklicken)
* [Controlify](https://modrinth.com/mod/controlify) (Absturz gemeldet; siehe [Issue #1144](https://github.com/Keksuccino/FancyMenu/issues/1144))
* [Crash To Main Menu](https://www.curseforge.com/minecraft/mc-mods/crash-to-main-menu)
* [Custom Loading Screen](https://www.curseforge.com/minecraft/mc-mods/better-loading-screen)
* [Custom Main Menu](https://www.curseforge.com/minecraft/mc-mods/custom-main-menu)
* [Debugify](https://www.curseforge.com/minecraft/mc-mods/debugify) (Verwende stattdessen [Modern Debugify](https://www.curseforge.com/minecraft/mc-mods/modern-debugify))
* [Dynamic Surroundings](https://www.curseforge.com/minecraft/mc-mods/dynamic-surroundings) (Es wurde gemeldet, dass der Mod Audioelemente beeinträchtigt)
* [EnhancedVisuals](https://www.curseforge.com/minecraft/mc-mods/enhancedvisuals) (Probleme mit Animationen und transparenten Hintergründen wurden gemeldet)
* [Entity Model Features](https://modrinth.com/mod/entity-model-features) (Absturz gemeldet; siehe [Issue #1115](https://github.com/Keksuccino/FancyMenu/issues/1115))
* [Fossils and Archeology Revival](https://www.curseforge.com/minecraft/mc-mods/fossils) (Funktioniert im Spiel, aber das benutzerdefinierte Hauptmenü wird nicht unterstützt – es lässt sich in der Konfiguration deaktivieren)
* [Holographic Renderers](https://www.curseforge.com/minecraft/mc-mods/holographic-renderers) (Absturz beim Start)
* [Ice and Fire](https://www.curseforge.com/minecraft/mc-mods/ice-and-fire-dragons) (Funktioniert, wenn das benutzerdefinierte Hauptmenü in der Konfiguration deaktiviert ist)
* [Jurassicraft](https://www.curseforge.com/minecraft/mc-mods/jurassicraft) (Absturz beim Start, wenn Anpassungen für die GUIs aktiviert werden – entferne sie aus `<game-directory>/config/fancymenu/customizablemenus.txt`)
* [Legacy4J](https://www.curseforge.com/minecraft/mc-mods/legacy-minecraft) (Das Spiel stürzt ab)
* [MalisisCore](https://www.curseforge.com/minecraft/mc-mods/malisiscore) (Beeinträchtigt die Anpassung des Hauptmenüs)
* [Main Menu Scale Mod](https://www.curseforge.com/minecraft/mc-mods/main-menu-scale)
* [MCA Reborn](https://www.curseforge.com/minecraft/mc-mods/minecraft-comes-alive-reborn) (Funktioniert, aber einige Menüs beeinträchtigen die Menüleiste von FancyMenu und/oder lassen sich nicht anpassen)
* [Minecraft Comes Alive](https://www.curseforge.com/minecraft/mc-mods/minecraft-comes-alive-mca) (Als kompatibel gemeldet, aber die Menüs lassen sich nicht anpassen)
* [MineTogether](https://www.curseforge.com/minecraft/mc-mods/creeperhost-minetogether) (Layoutprobleme bei einer GUI-Skalierung über 2 gemeldet)
* [Mod Menu](https://www.curseforge.com/minecraft/mc-mods/modmenu) (Meist kompatibel; bei einer doppelten oder nicht anpassbaren Mods-Schaltfläche setze **Hauptmenü -> Mods -> Mod Menu -> Mods Button** auf **Adjacent**)
* [Modern Online Picture Frames](https://www.curseforge.com/minecraft/mc-mods/online-picture-frame) (Absturz – siehe [dieses Issue](https://github.com/Keksuccino/FancyMenu/issues/776))
* [Not Enough Animations](https://www.curseforge.com/minecraft/mc-mods/not-enough-animations) (Als kompatibel für 1.16+ und inkompatibel für 1.12 gemeldet)
* [Optiscale](https://www.curseforge.com/minecraft/mc-mods/optiscale) (Beeinträchtigt die Benutzeroberfläche von FancyMenu; Schaltflächen lassen sich nicht anklicken)
* [Pack Menu](https://www.curseforge.com/minecraft/mc-mods/packmenu)
* [Panorama Screens](https://modrinth.com/mod/panorama-screens) (Konflikt zwischen den Menüanpassungssystemen gemeldet)
* [QuestCraft](https://github.com/QuestCraftPlusPlus/QuestCraft) (Das Spiel kann nicht geladen werden)
* [RandomPatches](https://www.curseforge.com/minecraft/mc-mods/randompatches-forge) (Funktioniert, wenn `patchMinecraftClass = false` in der Konfiguration eingestellt ist)
* [Remove Reloading Screen](https://www.curseforge.com/minecraft/mc-mods/rrls) (Es wurde gemeldet, dass der Mod FancyMenu und Drippy Loading Screen beeinträchtigt)
* [Replay Mod](https://www.replaymod.com/download/) (Funktioniert, wenn du `mainMenuButton` in `<game-directory>/config/replaymod.json` auf **BIG** setzt)
* [Seamless Loading Screen](https://www.curseforge.com/minecraft/mc-mods/seamless-loading-screen) (Das Spiel stürzt ab)
* [Slight Gui Modifications](https://www.curseforge.com/minecraft/mc-mods/slight-gui-modifications)
* [Skin Layers 3D](https://www.curseforge.com/minecraft/mc-mods/skin-layers-3d) (Als kompatibel für 1.16+ und inkompatibel für 1.12 gemeldet)
* [Smooth Scrolling Everywhere](https://www.curseforge.com/minecraft/mc-mods/smooth-scrolling-everywhere)
* [Sound Filters](https://www.curseforge.com/minecraft/mc-mods/sound-filters) (Die Audio-Erweiterung funktioniert nicht, wenn dieser Mod installiert ist)
* [Sound Physics Remastered](https://www.curseforge.com/minecraft/mc-mods/sound-physics-remastered) (Die Audio-Erweiterung funktioniert nicht, wenn dieser Mod installiert ist)
* [Stylish Effects](https://www.curseforge.com/minecraft/mc-mods/stylish-effects) (Beim ersten Anzeigen lädt das Hauptmenü die Layouts nicht)
* [Supplementaries](https://www.curseforge.com/minecraft/mc-mods/supplementaries) (Beim Anpassen des Konfigurationsbildschirms kommt es gelegentlich zu Abstürzen; lösche das problematische Layout aus `<game-directory>/config/fancymenu/customization/`)
* [Terraria Craft](https://www.curseforge.com/minecraft/mc-mods/terraria-craft)
* [The Dalek Mod](https://www.curseforge.com/minecraft/mc-mods/the-dalek-mod) (Funktioniert, wenn das benutzerdefinierte Hauptmenü in der Konfiguration deaktiviert ist)
* [ThonkUtil](https://www.curseforge.com/minecraft/mc-mods/thonkutil) (Funktioniert, fügt dem Hauptmenü derzeit aber einen nicht entfernbaren Text hinzu)
* [Trade Uses](https://modrinth.com/mod/trade-uses) (Verursacht Abstürze im Handelsmenü der Dorfbewohner – möglicherweise nur, wenn auch „Easy Villagers“ installiert ist)
* [VanillaFix](https://www.curseforge.com/minecraft/mc-mods/vanillafix) (Nutzbar, aber einige Nutzer melden Probleme mit dem VanillaFix-Absturzbildschirm)
* [FireplaceMode](https://www.curseforge.com/minecraft/mc-mods/fireplacemode) (Der Pausenbildschirm setzt seine Anpassungen manchmal zurück, wenn dieser Mod installiert ist)
* [Respackopts](https://www.curseforge.com/minecraft/mc-mods/respackopts) (Funktioniert, aber nur, wenn du die Anpassungen für den Ressourcenpaket-Bildschirm deaktivierst)
* [Bind Pizzeria](https://modrinth.com/mod/jjpizza) (Beeinträchtigt die Textdarstellung in den Kontextmenüs von FancyMenu)
* [EnhancedTooltips](https://www.curseforge.com/minecraft/mc-mods/enhancedtooltips) (Beeinträchtigt die Tooltips von FancyMenu)
* [Skin Shuffle](https://modrinth.com/mod/skinshuffle) (Die von diesem Mod zu Menüs hinzugefügte Spielerentität lässt sich nicht mit FancyMenu anpassen
* [Wakes](https://modrinth.com/mod/wakes) (Das Spiel stürzt beim Start aufgrund eines `IncompatibleClassChangeError` ab – der Mod kann die finale Methode `AbstractSliderButton.getSprite()` nicht überschreiben, die nur deshalb final ist, weil Wakes ihre Sichtbarkeit verändert. Weitere Informationen findest du in den GitHub-Issues: [Goby56/wakes #215](https://github.com/Goby56/wakes/issues/215), [Keksuccino/FancyMenu #1733](https://github.com/Keksuccino/FancyMenu/issues/1733))
* [Essential](https://www.curseforge.com/minecraft/mc-mods/essential) (Weitere Informationen findest du auf [dieser Seite](/essential))
