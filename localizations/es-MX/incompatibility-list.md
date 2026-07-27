---
title: Lista de incompatibilidades
description: >-
  Pantallas bloqueadas por FancyMenu e incompatibilidades reportadas por la
  comunidad.
---
# Incompatibilidades

# Pantallas donde la personalización está deshabilitada intencionalmente

FancyMenu bloquea pantallas que coinciden con ciertas rutas de paquetes de mods para evitar cierres inesperados o comportamientos incorrectos. El interruptor de personalización, la superposición y los diseños no están disponibles en las pantallas que coinciden.

Estos bloqueos usan el paquete Java de la clase de la pantalla en lugar de una lista seleccionada manualmente de pantallas individuales. Por lo tanto, una sola regla puede afectar a varias pantallas del mismo mod o de paquetes relacionados.

Los grupos de pantallas bloqueadas incluyen:

- Create
- Panoramica
- Alex's Mobs
- Screenshot Viewer
- Twilight Forest
- Supplementaries
- OptiFine; usa [Alternativas a OptiFine](./optifine-alternatives)
- SlimeKnights y Tinkers' Construct
- Mods de MidnightDust
- SkinSwapper
- Las propias pantallas de configuración de FancyMenu; se excluyen los [GUIs personalizados](./custom-guis)
- Immersive Engineering
- Dungeonz
- RPG-Hud
- Cobblemon y algunas pantallas relacionadas con Cobblemon
- Applied Energistics 2
- Mods de mapa de Xaero

# Incompatibilidades reportadas por la comunidad

Las entradas de abajo son reportes de la comunidad, no pantallas bloqueadas por FancyMenu como tal. La compatibilidad puede cambiar según las versiones de FancyMenu, Minecraft, el cargador y los mods en un paquete.

* [Animated Loading Screen](https://modrinth.com/mod/animated-loading-screen) (Hace que los menús se vean con errores)
* [Animated Mojang Logo](https://www.curseforge.com/minecraft/mc-mods/animated-mojang-logo) (A veces los diseños no cargan; también rompe Drippy Loading Screen)
* [Bedrockify](https://www.curseforge.com/minecraft/mc-mods/bedrockify) (Compatible cuando desactivas todas las modificaciones de menú del mod, al menos en los menús que quieras personalizar)
* [BetterFPS](https://www.curseforge.com/minecraft/mc-mods/betterfps) (Los botones y menús de este mod no son personalizables)
* [Chat Colors](https://www.curseforge.com/minecraft/mc-mods/chat-colours) (Cierre inesperado al iniciar)
* [Chloride](https://modrinth.com/mod/chloride) (El marcador de posición de FPS no funciona cuando este mod está instalado)
* [Colormatic](https://www.curseforge.com/minecraft/mc-mods/colormatic) (Retraso enorme al iniciar MC y rompe el audio de FM)
* [Controllable](https://www.curseforge.com/minecraft/mc-mods/controllable) (Los botones personalizados agregados a los menús con FancyMenu no se pueden pulsar mediante la función “Virtual Mouse” de Controllable)
* [Controlify](https://modrinth.com/mod/controlify) (Se reportó un cierre inesperado; consulta [el issue #1144](https://github.com/Keksuccino/FancyMenu/issues/1144))
* [Crash To Main Menu](https://www.curseforge.com/minecraft/mc-mods/crash-to-main-menu)
* [Custom Loading Screen](https://www.curseforge.com/minecraft/mc-mods/better-loading-screen)
* [Custom Main Menu](https://www.curseforge.com/minecraft/mc-mods/custom-main-menu)
* [Debugify](https://www.curseforge.com/minecraft/mc-mods/debugify) (Usa [Modern Debugify](https://www.curseforge.com/minecraft/mc-mods/modern-debugify) en su lugar)
* [Dynamic Surroundings](https://www.curseforge.com/minecraft/mc-mods/dynamic-surroundings) (Se reporta que rompe los elementos de audio)
* [EnhancedVisuals](https://www.curseforge.com/minecraft/mc-mods/enhancedvisuals) (Se reportan problemas con la animación y con el fondo translúcido)
* [Entity Model Features](https://modrinth.com/mod/entity-model-features) (Se reportó un cierre inesperado; consulta [el issue #1115](https://github.com/Keksuccino/FancyMenu/issues/1115))
* [Fossils and Archeology Revival](https://www.curseforge.com/minecraft/mc-mods/fossils) (Funciona en el juego, pero el menú principal personalizado no es compatible; se puede desactivar en su configuración)
* [Holographic Renderers](https://www.curseforge.com/minecraft/mc-mods/holographic-renderers) (Cierre inesperado al iniciar)
* [Ice and Fire](https://www.curseforge.com/minecraft/mc-mods/ice-and-fire-dragons) (Funciona si se desactiva el menú principal personalizado en su configuración)
* [Jurassicraft](https://www.curseforge.com/minecraft/mc-mods/jurassicraft) (Se cierra al iniciar cuando activas personalizaciones para sus GUIs; elimínalas de `<game-directory>/config/fancymenu/customizablemenus.txt`)
* [Legacy4J](https://www.curseforge.com/minecraft/mc-mods/legacy-minecraft) (Cierra el juego)
* [MalisisCore](https://www.curseforge.com/minecraft/mc-mods/malisiscore) (Rompe la personalización del menú principal)
* [Main Menu Scale Mod](https://www.curseforge.com/minecraft/mc-mods/main-menu-scale)
* [MCA Reborn](https://www.curseforge.com/minecraft/mc-mods/minecraft-comes-alive-reborn) (Funciona, pero algunos de sus menús rompen la barra de menú de FM y/o no son personalizables)
* [Minecraft Comes Alive](https://www.curseforge.com/minecraft/mc-mods/minecraft-comes-alive-mca) (Se reporta compatible, pero sus menús no son personalizables)
* [MineTogether](https://www.curseforge.com/minecraft/mc-mods/creeperhost-minetogether) (Se reportan problemas de diseño por encima de la escala de GUI 2)
* [Mod Menu](https://www.curseforge.com/minecraft/mc-mods/modmenu) (Normalmente compatible; para un botón de Mods duplicado o no personalizable, configura **Main Menu -> Mods -> Mod Menu -> Mods Button** en **Adjacent**)
* [Modern Online Picture Frames](https://www.curseforge.com/minecraft/mc-mods/online-picture-frame) (Cierre inesperado; consulta [este issue](https://github.com/Keksuccino/FancyMenu/issues/776))
* [Not Enough Animations](https://www.curseforge.com/minecraft/mc-mods/not-enough-animations) (Se reporta compatible en 1.16+ e incompatible en 1.12)
* [Optiscale](https://www.curseforge.com/minecraft/mc-mods/optiscale) (Rompe la interfaz de FancyMenu; los botones no se pueden pulsar)
* [Pack Menu](https://www.curseforge.com/minecraft/mc-mods/packmenu)
* [Panorama Screens](https://modrinth.com/mod/panorama-screens) (Se reporta conflicto entre los sistemas de personalización de menús)
* [QuestCraft](https://github.com/QuestCraftPlusPlus/QuestCraft) (El juego no logra cargar)
* [RandomPatches](https://www.curseforge.com/minecraft/mc-mods/randompatches-forge) (Funciona si `patchMinecraftClass = false` en su configuración)
* [Remove Reloading Screen](https://www.curseforge.com/minecraft/mc-mods/rrls) (Se reporta que rompe FancyMenu y Drippy Loading Screen)
* [Replay Mod](https://www.replaymod.com/download/) (Funciona cuando configuras `mainMenuButton` en **BIG** en `<game-directory>/config/replaymod.json`)
* [Seamless Loading Screen](https://www.curseforge.com/minecraft/mc-mods/seamless-loading-screen) (Cierra el juego)
* [Slight Gui Modifications](https://www.curseforge.com/minecraft/mc-mods/slight-gui-modifications)
* [Skin Layers 3D](https://www.curseforge.com/minecraft/mc-mods/skin-layers-3d) (Se reporta compatible en 1.16+ e incompatible en 1.12)
* [Smooth Scrolling Everywhere](https://www.curseforge.com/minecraft/mc-mods/smooth-scrolling-everywhere)
* [Sound Filters](https://www.curseforge.com/minecraft/mc-mods/sound-filters) (La extensión de audio no funcionará con este mod instalado)
* [Sound Physics Remastered](https://www.curseforge.com/minecraft/mc-mods/sound-physics-remastered) (La extensión de audio no funcionará con este mod instalado)
* [Stylish Effects](https://www.curseforge.com/minecraft/mc-mods/stylish-effects) (El menú principal no carga los diseños la primera vez que se muestra)
* [Supplementaries](https://www.curseforge.com/minecraft/mc-mods/supplementaries) (A veces se cierra al personalizar su pantalla de configuración; elimina el diseño problemático de `<game-directory>/config/fancymenu/customization/`)
* [Terraria Craft](https://www.curseforge.com/minecraft/mc-mods/terraria-craft)
* [The Dalek Mod](https://www.curseforge.com/minecraft/mc-mods/the-dalek-mod) (Funciona si se desactiva su menú principal personalizado en la configuración)
* [ThonkUtil](https://www.curseforge.com/minecraft/mc-mods/thonkutil) (Funciona, pero actualmente agrega un texto no removible al menú principal)
* [Trade Uses](https://modrinth.com/mod/trade-uses) (Causa cierres inesperados en el menú de comercio del aldeano; posiblemente solo cuando también está instalado “Easy Villagers”)
* [VanillaFix](https://www.curseforge.com/minecraft/mc-mods/vanillafix) (Se puede usar, pero algunos usuarios reportan problemas con la pantalla de error de VanillaFix)
* [FireplaceMode](https://www.curseforge.com/minecraft/mc-mods/fireplacemode) (La pantalla de pausa a veces restablece sus personalizaciones con este mod instalado)
* [Respackopts](https://www.curseforge.com/minecraft/mc-mods/respackopts) (Funciona, pero solo si desactivas las personalizaciones para la pantalla de Paquetes de recursos)
* [Bind Pizzeria](https://modrinth.com/mod/jjpizza) (Rompe el renderizado de texto en los menús contextuales de FancyMenu)
* [EnhancedTooltips](https://www.curseforge.com/minecraft/mc-mods/enhancedtooltips) (Rompe los tooltips de FancyMenu)
* [Skin Shuffle](https://modrinth.com/mod/skinshuffle) (La entidad del jugador agregada a los menús por ese mod no se puede personalizar mediante FancyMenu)
