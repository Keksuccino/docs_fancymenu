---
title: Liste des incompatibilités
description: Écrans bloqués par FancyMenu et incompatibilités signalées par la communauté.
---
# Incompatibilités

# Écrans où la personnalisation est intentionnellement désactivée

FancyMenu bloque les écrans correspondant à certains chemins de package de mods afin d’éviter les crashs ou les comportements incorrects. Le bouton d’activation de la personnalisation, la superposition et les mises en page ne sont pas disponibles sur les écrans correspondants.

Ces blocages utilisent le package Java de la classe d’écran plutôt qu’une liste manuellement choisie d’écrans individuels. Une seule règle peut donc affecter plusieurs écrans provenant du même mod ou de packages associés.

Les groupes d’écrans bloqués incluent :

- Create
- Panoramica
- Alex's Mobs
- Screenshot Viewer
- Twilight Forest
- Supplementaries
- OptiFine ; utilisez [OptiFine Alternatives](./optifine-alternatives)
- SlimeKnights et Tinkers' Construct
- mods MidnightDust
- SkinSwapper
- Les propres écrans de configuration de FancyMenu ; les [Custom GUIs](./custom-guis) en sont exclus
- Immersive Engineering
- Dungeonz
- RPG-Hud
- Cobblemon et certains écrans liés à Cobblemon
- Applied Energistics 2
- les mods de carte de Xaero

# Incompatibilités signalées par la communauté

Les entrées ci-dessous sont des signalements de la communauté, et non des écrans bloqués par FancyMenu lui-même. La compatibilité peut changer selon les versions de FancyMenu, de Minecraft, du chargeur et des mods dans un modpack.

* [Animated Loading Screen](https://modrinth.com/mod/animated-loading-screen) (Les menus semblent buguer)
* [Animated Mojang Logo](https://www.curseforge.com/minecraft/mc-mods/animated-mojang-logo) (Les mises en page ne se chargent parfois pas ; casse aussi Drippy Loading Screen)
* [Bedrockify](https://www.curseforge.com/minecraft/mc-mods/bedrockify) (Compatible lorsque vous désactivez toutes les modifications de menus du mod, au moins pour les menus que vous souhaitez personnaliser)
* [BetterFPS](https://www.curseforge.com/minecraft/mc-mods/betterfps) (Les boutons et menus de ce mod ne sont pas personnalisables)
* [Chat Colors](https://www.curseforge.com/minecraft/mc-mods/chat-colours) (Crash au démarrage)
* [Chloride](https://modrinth.com/mod/chloride) (Le faux-texte d’IPS ne fonctionne pas lorsque ce mod est installé)
* [Colormatic](https://www.curseforge.com/minecraft/mc-mods/colormatic) (Fort lag au lancement de MC et casse les fonctionnalités audio de FM)
* [Controllable](https://www.curseforge.com/minecraft/mc-mods/controllable) (Les boutons personnalisés ajoutés aux menus avec FancyMenu ne sont pas cliquables via la fonctionnalité « Virtual Mouse » de Controllable)
* [Controlify](https://modrinth.com/mod/controlify) (Crash signalé ; voir [issue #1144](https://github.com/Keksuccino/FancyMenu/issues/1144))
* [Crash To Main Menu](https://www.curseforge.com/minecraft/mc-mods/crash-to-main-menu)
* [Custom Loading Screen](https://www.curseforge.com/minecraft/mc-mods/better-loading-screen)
* [Custom Main Menu](https://www.curseforge.com/minecraft/mc-mods/custom-main-menu)
* [Debugify](https://www.curseforge.com/minecraft/mc-mods/debugify) (Utilisez plutôt [Modern Debugify](https://www.curseforge.com/minecraft/mc-mods/modern-debugify))
* [Dynamic Surroundings](https://www.curseforge.com/minecraft/mc-mods/dynamic-surroundings) (Signalé comme cassant les éléments audio)
* [EnhancedVisuals](https://www.curseforge.com/minecraft/mc-mods/enhancedvisuals) (Problèmes signalés d’animation et de fond translucide)
* [Entity Model Features](https://modrinth.com/mod/entity-model-features) (Crash signalé ; voir [issue #1115](https://github.com/Keksuccino/FancyMenu/issues/1115))
* [Fossils and Archeology Revival](https://www.curseforge.com/minecraft/mc-mods/fossils) (Fonctionne en jeu, mais le menu principal personnalisé n’est pas pris en charge — peut être désactivé dans sa configuration)
* [Holographic Renderers](https://www.curseforge.com/minecraft/mc-mods/holographic-renderers) (Crash au démarrage)
* [Ice and Fire](https://www.curseforge.com/minecraft/mc-mods/ice-and-fire-dragons) (Fonctionne si le menu principal personnalisé est désactivé dans sa configuration)
* [Jurassicraft](https://www.curseforge.com/minecraft/mc-mods/jurassicraft) (Crash au lancement lors de l’activation des personnalisations pour ses GUI — supprimez-les de `<game-directory>/config/fancymenu/customizablemenus.txt`)
* [Legacy4J](https://www.curseforge.com/minecraft/mc-mods/legacy-minecraft) (Fait crasher le jeu)
* [MalisisCore](https://www.curseforge.com/minecraft/mc-mods/malisiscore) (Casse la personnalisation du menu principal)
* [Main Menu Scale Mod](https://www.curseforge.com/minecraft/mc-mods/main-menu-scale)
* [MCA Reborn](https://www.curseforge.com/minecraft/mc-mods/minecraft-comes-alive-reborn) (Fonctionne, mais certains de ses menus cassent la barre de menu de FM et/ou ne sont pas personnalisables)
* [Minecraft Comes Alive](https://www.curseforge.com/minecraft/mc-mods/minecraft-comes-alive-mca) (Signalé comme compatible, mais ses menus ne sont pas personnalisables)
* [MineTogether](https://www.curseforge.com/minecraft/mc-mods/creeperhost-minetogether) (Problèmes de mise en page signalés au-dessus d’une échelle d’interface 2)
* [Mod Menu](https://www.curseforge.com/minecraft/mc-mods/modmenu) (Généralement compatible ; pour un bouton Mods dupliqué ou non personnalisable, définissez **Main Menu -> Mods -> Mod Menu -> Mods Button** sur **Adjacent**)
* [Modern Online Picture Frames](https://www.curseforge.com/minecraft/mc-mods/online-picture-frame) (Crash — voir [ce problème](https://github.com/Keksuccino/FancyMenu/issues/776))
* [Not Enough Animations](https://www.curseforge.com/minecraft/mc-mods/not-enough-animations) (Signalé comme compatible en 1.16+ et incompatible en 1.12)
* [Optiscale](https://www.curseforge.com/minecraft/mc-mods/optiscale) (Casse l’interface de FancyMenu ; les boutons ne sont pas cliquables)
* [Pack Menu](https://www.curseforge.com/minecraft/mc-mods/packmenu)
* [Panorama Screens](https://modrinth.com/mod/panorama-screens) (Conflit signalé entre les systèmes de personnalisation des menus)
* [QuestCraft](https://github.com/QuestCraftPlusPlus/QuestCraft) (Le jeu ne se charge pas)
* [RandomPatches](https://www.curseforge.com/minecraft/mc-mods/randompatches-forge) (Fonctionne si `patchMinecraftClass = false` dans sa configuration)
* [Remove Reloading Screen](https://www.curseforge.com/minecraft/mc-mods/rrls) (Signalé comme cassant FancyMenu et Drippy Loading Screen)
* [Replay Mod](https://www.replaymod.com/download/) (Fonctionne lorsque vous réglez `mainMenuButton` sur **BIG** dans `<game-directory>/config/replaymod.json`)
* [Seamless Loading Screen](https://www.curseforge.com/minecraft/mc-mods/seamless-loading-screen) (Fait crasher le jeu)
* [Slight Gui Modifications](https://www.curseforge.com/minecraft/mc-mods/slight-gui-modifications)
* [Skin Layers 3D](https://www.curseforge.com/minecraft/mc-mods/skin-layers-3d) (Signalé comme compatible en 1.16+ et incompatible en 1.12)
* [Smooth Scrolling Everywhere](https://www.curseforge.com/minecraft/mc-mods/smooth-scrolling-everywhere)
* [Sound Filters](https://www.curseforge.com/minecraft/mc-mods/sound-filters) (L’extension audio ne fonctionne pas avec ce mod installé)
* [Sound Physics Remastered](https://www.curseforge.com/minecraft/mc-mods/sound-physics-remastered) (L’extension audio ne fonctionne pas avec ce mod installé)
* [Stylish Effects](https://www.curseforge.com/minecraft/mc-mods/stylish-effects) (Le menu principal ne charge pas les mises en page la première fois qu’il est affiché)
* [Supplementaries](https://www.curseforge.com/minecraft/mc-mods/supplementaries) (Crash aléatoire lors de la personnalisation de son écran de configuration ; supprimez la mise en page problématique de `<game-directory>/config/fancymenu/customization/`)
* [Terraria Craft](https://www.curseforge.com/minecraft/mc-mods/terraria-craft)
* [The Dalek Mod](https://www.curseforge.com/minecraft/mc-mods/the-dalek-mod) (Fonctionne si son menu principal personnalisé est désactivé dans la configuration)
* [ThonkUtil](https://www.curseforge.com/minecraft/mc-mods/thonkutil) (Fonctionne, mais ajoute actuellement un texte non supprimable au menu principal)
* [Trade Uses](https://modrinth.com/mod/trade-uses) (Provoque des crashs dans le menu d’échange du villageois — peut-être seulement lorsque « Easy Villagers » est également installé)
* [VanillaFix](https://www.curseforge.com/minecraft/mc-mods/vanillafix) (Utilisable, mais certains utilisateurs signalent des problèmes avec l’écran de crash de VanillaFix)
* [FireplaceMode](https://www.curseforge.com/minecraft/mc-mods/fireplacemode) (L’écran de pause réinitialise parfois ses personnalisations avec ce mod installé)
* [Respackopts](https://www.curseforge.com/minecraft/mc-mods/respackopts) (Fonctionne, mais seulement si vous désactivez les personnalisations de l’écran du pack de ressources)
* [Bind Pizzeria](https://modrinth.com/mod/jjpizza) (Casse le rendu du texte dans les menus contextuels de FancyMenu)
* [EnhancedTooltips](https://www.curseforge.com/minecraft/mc-mods/enhancedtooltips) (Casse les infobulles de FancyMenu)
* [Skin Shuffle](https://modrinth.com/mod/skinshuffle) (L’entité joueur ajoutée aux menus par ce mod n’est pas personnalisable via FancyMenu)
