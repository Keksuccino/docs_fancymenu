---
title: Lista de incompatibilidades
description: >-
  Pantallas bloqueadas por FancyMenu e incompatibilidades reportadas por la
  comunidad.
---
# Incompatibilidades

# Pantallas en las que la personalización está desactivada intencionalmente

FancyMenu bloquea las pantallas que coinciden con ciertas rutas de paquetes de mods para evitar fallos o comportamientos incorrectos. El interruptor de personalización, la superposición y los diseños no están disponibles en las pantallas que coinciden.

Estos bloqueos usan el paquete Java de la clase de la pantalla en lugar de una lista seleccionada manualmente de pantallas individuales. Por tanto, una sola regla puede afectar a varias pantallas del mismo mod o de paquetes relacionados.

Los grupos de pantallas bloqueados incluyen:

- Create
- Panoramica
- Alex's Mobs
- Screenshot Viewer
- Twilight Forest
- Supplementaries
- OptiFine; usa [Alternativas a OptiFine](./optifine-alternatives)
- SlimeKnights y Tinkers' Construct
- mods de MidnightDust
- SkinSwapper
- Las pantallas de configuración propias de FancyMenu; se excluyen los [GUI personalizados](./custom-guis)
- Immersive Engineering
- Dungeonz
- RPG-Hud
- Cobblemon y algunas pantallas relacionadas con Cobblemon
- Applied Energistics 2
- mods de mapas de Xaero

# Incompatibilidades reportadas por la comunidad

Las entradas de abajo son informes de la comunidad, no pantallas bloqueadas por FancyMenu en sí. La compatibilidad puede cambiar según las versiones de FancyMenu, Minecraft, el cargador y los mods del paquete.

* [Animated Loading Screen](https://modrinth.com/mod/animated-loading-screen) (Hace que los menús parezcan tener errores)
* [Animated Mojang Logo](https://www.curseforge.com/minecraft/mc-mods/animated-mojang-logo) (A veces los diseños no cargan; también rompe Drippy Loading Screen)
* [Bedrockify](https://www.curseforge.com/minecraft/mc-mods/bedrockify) (Compatible cuando desactivas todas las modificaciones de menús del mod, al menos para los menús que quieras personalizar)
* [BetterFPS](https://www.curseforge.com/minecraft/mc-mods/betterfps) (Los botones y menús de este mod no se pueden personalizar)
* [Chat Colors](https://www.curseforge.com/minecraft/mc-mods/chat-colours) (Cuelgue al iniciar)
* [Chloride](https://modrinth.com/mod/chloride) (El marcador de posición de FPS no funciona cuando este mod está instalado)
* [Colormatic](https://www.curseforge.com/minecraft/mc-mods/colormatic) (Gran lag al iniciar MC y rompe las funciones de audio de FM)
* [Controllable](https://www.curseforge.com/minecraft/mc-mods/controllable) (Los botones personalizados añadidos a los menús con FancyMenu no se pueden pulsar mediante la función “Virtual Mouse” de Controllable)
* [Controlify](https://modrinth.com/mod/controlify) (Se ha reportado un fallo; consulta [el issue #1144](https://github.com/Keksuccino/FancyMenu/issues/1144))
* [Crash To Main Menu](https://www.curseforge.com/minecraft/mc-mods/crash-to-main-menu)
* [Custom Loading Screen](https://www.curseforge.com/minecraft/mc-mods/better-loading-screen)
* [Custom Main Menu](https://www.curseforge.com/minecraft/mc-mods/custom-main-menu)
* [Debugify](https://www.curseforge.com/minecraft/mc-mods/debugify) (Usa [Modern Debugify](https://www.curseforge.com/minecraft/mc-mods/modern-debugify) en su lugar)
* [Dynamic Surroundings](https://www.curseforge.com/minecraft/mc-mods/dynamic-surroundings) (Se ha informado de que rompe los elementos de audio)
* [EnhancedVisuals](https://www.curseforge.com/minecraft/mc-mods/enhancedvisuals) (Se han reportado problemas de animación y de fondo translúcido)
* [Entity Model Features](https://modrinth.com/mod/entity-model-features) (Se ha reportado un fallo; consulta [el issue #1115](https://github.com/Keksuccino/FancyMenu/issues/1115))
* [Fossils and Archeology Revival](https://www.curseforge.com/minecraft/mc-mods/fossils) (Funciona en el juego, pero el menú principal personalizado no es compatible; se puede desactivar en su configuración)
* [Holographic Renderers](https://www.curseforge.com/minecraft/mc-mods/holographic-renderers) (Cuelgue al iniciar)
* [Ice and Fire](https://www.curseforge.com/minecraft/mc-mods/ice-and-fire-dragons) (Funciona si se desactiva el menú principal personalizado en su configuración)
* [Jurassicraft](https://www.curseforge.com/minecraft/mc-mods/jurassicraft) (Se bloquea al iniciar al activar personalizaciones para sus GUI; elimínalas de `<game-directory>/config/fancymenu/customizablemenus.txt`)
* [Legacy4J](https://www.curseforge.com/minecraft/mc-mods/legacy-minecraft) (Bloquea el juego)
* [MalisisCore](https://www.curseforge.com/minecraft/mc-mods/malisiscore) (Rompe la personalización del menú principal)
* [Main Menu Scale Mod](https://www.curseforge.com/minecraft/mc-mods/main-menu-scale)
* [MCA Reborn](https://www.curseforge.com/minecraft/mc-mods/minecraft-comes-alive-reborn) (Funciona, pero algunos de sus menús rompen la barra de menús de FM y/o no se pueden personalizar)
* [Minecraft Comes Alive](https://www.curseforge.com/minecraft/mc-mods/minecraft-comes-alive-mca) (Se ha informado de que es compatible, pero sus menús no se pueden personalizar)
* [MineTogether](https://www.curseforge.com/minecraft/mc-mods/creeperhost-minetogether) (Se han reportado problemas de diseño por encima del escalado de interfaz 2)
* [Mod Menu](https://www.curseforge.com/minecraft/mc-mods/modmenu) (Normalmente compatible; para un botón Mods duplicado o no personalizable, pon **Main Menu -> Mods -> Mod Menu -> Mods Button** en **Adjacent**)
* [Modern Online Picture Frames](https://www.curseforge.com/minecraft/mc-mods/online-picture-frame) (Fallo; consulta [este issue](https://github.com/Keksuccino/FancyMenu/issues/776))
* [Not Enough Animations](https://www.curseforge.com/minecraft/mc-mods/not-enough-animations) (Se ha informado de que es compatible en 1.16+ e incompatible en 1.12)
* [Optiscale](https://www.curseforge.com/minecraft/mc-mods/optiscale) (Rompe la interfaz de FancyMenu; los botones no se pueden pulsar)
* [Pack Menu](https://www.curseforge.com/minecraft/mc-mods/packmenu)
* [Panorama Screens](https://modrinth.com/mod/panorama-screens) (Se ha informado de un conflicto entre sistemas de personalización de menús)
* [QuestCraft](https://github.com/QuestCraftPlusPlus/QuestCraft) (El juego no llega a cargarse)
* [RandomPatches](https://www.curseforge.com/minecraft/mc-mods/randompatches-forge) (Funciona si `patchMinecraftClass = false` en su configuración)
* [Remove Reloading Screen](https://www.curseforge.com/minecraft/mc-mods/rrls) (Se ha informado de que rompe FancyMenu y Drippy Loading Screen)
* [Replay Mod](https://www.replaymod.com/download/) (Funciona cuando pones `mainMenuButton` en **BIG** en `<game-directory>/config/replaymod.json`)
* [Seamless Loading Screen](https://www.curseforge.com/minecraft/mc-mods/seamless-loading-screen) (Bloquea el juego)
* [Slight Gui Modifications](https://www.curseforge.com/minecraft/mc-mods/slight-gui-modifications)
* [Skin Layers 3D](https://www.curseforge.com/minecraft/mc-mods/skin-layers-3d) (Se ha informado de que es compatible en 1.16+ e incompatible en 1.12)
* [Smooth Scrolling Everywhere](https://www.curseforge.com/minecraft/mc-mods/smooth-scrolling-everywhere)
* [Sound Filters](https://www.curseforge.com/minecraft/mc-mods/sound-filters) (La extensión de audio no funcionará con este mod instalado)
* [Sound Physics Remastered](https://www.curseforge.com/minecraft/mc-mods/sound-physics-remastered) (La extensión de audio no funcionará con este mod instalado)
* [Stylish Effects](https://www.curseforge.com/minecraft/mc-mods/stylish-effects) (El menú principal no carga los diseños la primera vez que se muestra)
* [Supplementaries](https://www.curseforge.com/minecraft/mc-mods/supplementaries) (Se bloquea aleatoriamente al personalizar su pantalla de configuración; elimina el diseño problemático de `<game-directory>/config/fancymenu/customization/`)
* [Terraria Craft](https://www.curseforge.com/minecraft/mc-mods/terraria-craft)
* [The Dalek Mod](https://www.curseforge.com/minecraft/mc-mods/the-dalek-mod) (Funciona si su menú principal personalizado se desactiva en la configuración)
* [ThonkUtil](https://www.curseforge.com/minecraft/mc-mods/thonkutil) (Funciona, pero actualmente añade un texto no eliminable al menú principal)
* [Trade Uses](https://modrinth.com/mod/trade-uses) (Provoca fallos en el menú de comercio de aldeanos; posiblemente solo cuando también está instalado “Easy Villagers”)
* [VanillaFix](https://www.curseforge.com/minecraft/mc-mods/vanillafix) (Usable, pero algunos usuarios informan de problemas con la pantalla de fallo de VanillaFix)
* [FireplaceMode](https://www.curseforge.com/minecraft/mc-mods/fireplacemode) (La pantalla de pausa a veces restablece sus personalizaciones con este mod instalado)
* [Respackopts](https://www.curseforge.com/minecraft/mc-mods/respackopts) (Funciona, pero solo si desactivas las personalizaciones para la pantalla de Paquetes de recursos)
* [Bind Pizzeria](https://modrinth.com/mod/jjpizza) (Rompe el renderizado del texto en los menús contextuales de FancyMenu)
* [EnhancedTooltips](https://www.curseforge.com/minecraft/mc-mods/enhancedtooltips) (Rompe los tooltips de FancyMenu)
* [Skin Shuffle](https://modrinth.com/mod/skinshuffle) (La entidad del jugador añadida a los menús por ese mod no se puede personalizar mediante FancyMenu)
