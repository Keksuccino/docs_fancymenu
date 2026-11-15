---
title: Liste des incompatibilités
description: Écrans bloqués par FancyMenu et incompatibilités signalées par la communauté.
sourceBlobSha: f5f938751a166796106f5074dc55137bcd40f203
---
# Écrans dont la personnalisation est volontairement désactivée

FancyMenu bloque les écrans correspondant à certains chemins de packages de mods afin d’éviter les plantages ou les comportements incorrects. Le bouton de personnalisation, la superposition et les mises en page ne sont pas disponibles sur les écrans concernés.

Ces blocages utilisent le package Java de la classe de l’écran plutôt qu’une liste prédéfinie d’écrans individuels. Une seule règle peut donc affecter plusieurs écrans d’un même mod ou de packages associés.

Les groupes d’écrans bloqués incluent :

- Create
- Panoramica
- Alex's Mobs
- Screenshot Viewer
- Twilight Forest
- Supplementaries
- OptiFine ; utilisez [les alternatives à OptiFine](./optifine-alternatives)
- SlimeKnights et Tinkers' Construct
- Les mods MidnightDust
- SkinSwapper
- Immersive Engineering
- Dungeonz
- RPG-Hud
- Cobblemon et certains écrans associés à Cobblemon
- Applied Energistics 2
- Les mods de carte de Xaero

# Incompatibilités signalées par la communauté

Les entrées ci-dessous sont des signalements de la communauté, et non des écrans bloqués par FancyMenu lui-même. La compatibilité peut changer selon les versions de FancyMenu, de Minecraft, du chargeur et des mods utilisés dans un pack.

* [Animated Loading Screen](https://modrinth.com/mod/animated-loading-screen) (Donne un aspect défectueux aux menus)
* [Animated Mojang Logo](https://www.curseforge.com/minecraft/mc-mods/animated-mojang-logo) (Les mises en page ne se chargent parfois pas ; casse également Drippy Loading Screen)
* [Bedrockify](https://www.curseforge.com/minecraft/mc-mods/bedrockify) (Compatible si vous désactivez toutes les modifications de menus du mod, au moins pour les menus que vous souhaitez personnaliser)
* [BetterFPS](https://www.curseforge.com/minecraft/mc-mods/betterfps) (Les boutons et les menus de ce mod ne sont pas personnalisables)
* [Chat Colors](https://www.curseforge.com/minecraft/mc-mods/chat-colours) (Plantage au démarrage)
* [Chloride](https://modrinth.com/mod/chloride) (L’indicateur d’IPS ne fonctionne pas lorsque ce mod est installé)
* [Colormatic](https://www.curseforge.com/minecraft/mc-mods/colormatic) (Provoque de gros ralentissements au démarrage de Minecraft et casse les fonctionnalités audio de FM)
* [Controllable](https://www.curseforge.com/minecraft/mc-mods/controllable) (Les boutons personnalisés ajoutés aux menus avec FancyMenu ne peuvent pas être cliqués via la fonctionnalité « Souris virtuelle » de Controllable)
* [Controlify](https://modrinth.com/mod/controlify) (Plantage signalé ; consultez [le problème n° 1144](https://github.com/Keksuccino/FancyMenu/issues/1144))
* [Crash To Main Menu](https://www.curseforge.com/minecraft/mc-mods/crash-to-main-menu)
* [Custom Loading Screen](https://www.curseforge.com/minecraft/mc-mods/better-loading-screen)
* [Custom Main Menu](https://www.curseforge.com/minecraft/mc-mods/custom-main-menu)
* [Debugify](https://www.curseforge.com/minecraft/mc-mods/debugify) (Utilisez plutôt [Modern Debugify](https://www.curseforge.com/minecraft/mc-mods/modern-debugify))
* [Dynamic Surroundings](https://www.curseforge.com/minecraft/mc-mods/dynamic-surroundings) (Signale des problèmes avec les éléments audio)
* [EnhancedVisuals](https://www.curseforge.com/minecraft/mc-mods/enhancedvisuals) (Problèmes signalés avec les animations et les arrière-plans translucides)
* [Entity Model Features](https://modrinth.com/mod/entity-model-features) (Plantage signalé ; consultez [le problème n° 1115](https://github.com/Keksuccino/FancyMenu/issues/1115))
* [Fossils and Archeology Revival](https://www.curseforge.com/minecraft/mc-mods/fossils) (Fonctionne en jeu, mais le menu principal personnalisé n’est pas pris en charge ; il peut être désactivé dans sa configuration)
* [Holographic Renderers](https://www.curseforge.com/minecraft/mc-mods/holographic-renderers) (Plantage au démarrage)
* [Ice and Fire](https://www.curseforge.com/minecraft/mc-mods/ice-and-fire-dragons) (Fonctionne si le menu principal personnalisé est désactivé dans sa configuration)
* [Jurassicraft](https://www.curseforge.com/minecraft/mc-mods/jurassicraft) (Provoque un plantage au démarrage lorsque des personnalisations sont activées pour ses interfaces ; supprimez-les de `<game-directory>/config/fancymenu/customizablemenus.txt`)
* [Legacy4J](https://www.curseforge.com/minecraft/mc-mods/legacy-minecraft) (Fait planter le jeu)
* [MalisisCore](https://www.curseforge.com/minecraft/mc-mods/malisiscore) (Casse la personnalisation du menu principal)
* [Main Menu Scale Mod](https://www.curseforge.com/minecraft/mc-mods/main-menu-scale)
* [MCA Reborn](https://www.curseforge.com/minecraft/mc-mods/minecraft-comes-alive-reborn) (Fonctionne, mais certains de ses menus cassent la barre de menus de FM et/ou ne sont pas personnalisables)
* [Minecraft Comes Alive](https://www.curseforge.com/minecraft/mc-mods/minecraft-comes-alive-mca) (Compatibilité signalée, mais ses menus ne sont pas personnalisables)
* [MineTogether](https://www.curseforge.com/minecraft/mc-mods/creeperhost-minetogether) (Problèmes de mise en page signalés au-delà d’une échelle d’interface de 2)
* [Mod Menu](https://www.curseforge.com/minecraft/mc-mods/modmenu) (Généralement compatible ; si le bouton Mods est dupliqué ou non personnalisable, définissez **Menu principal -> Mods -> Mod Menu -> Bouton Mods** sur **Adjacent**)
* [Modern Online Picture Frames](https://www.curseforge.com/minecraft/mc-mods/online-picture-frame) (Plantage — consultez [ce problème](https://github.com/Keksuccino/FancyMenu/issues/776))
* [Not Enough Animations](https://www.curseforge.com/minecraft/mc-mods/not-enough-animations) (Compatibilité signalée pour la version 1.16 et ultérieure, incompatibilité pour la version 1.12)
* [Optiscale](https://www.curseforge.com/minecraft/mc-mods/optiscale) (Casse l’interface de FancyMenu ; les boutons ne sont pas cliquables)
* [Pack Menu](https://www.curseforge.com/minecraft/mc-mods/packmenu)
* [Panorama Screens](https://modrinth.com/mod/panorama-screens) (Conflit signalé entre les systèmes de personnalisation des menus)
* [QuestCraft](https://github.com/QuestCraftPlusPlus/QuestCraft) (Le jeu ne se charge pas)
* [RandomPatches](https://www.curseforge.com/minecraft/mc-mods/randompatches-forge) (Fonctionne si `patchMinecraftClass = false` est défini dans sa configuration)
* [Remove Reloading Screen](https://www.curseforge.com/minecraft/mc-mods/rrls) (Signale des problèmes avec FancyMenu et Drippy Loading Screen)
* [Replay Mod](https://www.replaymod.com/download/) (Fonctionne lorsque `mainMenuButton` est défini sur **BIG** dans `<game-directory>/config/replaymod.json`)
* [Seamless Loading Screen](https://www.curseforge.com/minecraft/mc-mods/seamless-loading-screen) (Fait planter le jeu)
* [Slight Gui Modifications](https://www.curseforge.com/minecraft/mc-mods/slight-gui-modifications)
* [Skin Layers 3D](https://www.curseforge.com/minecraft/mc-mods/skin-layers-3d) (Compatibilité signalée pour la version 1.16 et ultérieure, incompatibilité pour la version 1.12)
* [Smooth Scrolling Everywhere](https://www.curseforge.com/minecraft/mc-mods/smooth-scrolling-everywhere)
* [Sound Filters](https://www.curseforge.com/minecraft/mc-mods/sound-filters) (L’extension audio ne fonctionnera pas si ce mod est installé)
* [Sound Physics Remastered](https://www.curseforge.com/minecraft/mc-mods/sound-physics-remastered) (L’extension audio ne fonctionnera pas si ce mod est installé)
* [Stylish Effects](https://www.curseforge.com/minecraft/mc-mods/stylish-effects) (Le menu principal ne parvient pas à charger les mises en page lors de sa première ouverture)
* [Supplementaries](https://www.curseforge.com/minecraft/mc-mods/supplementaries) (Provoque des plantages aléatoires lors de la personnalisation de son écran de configuration ; supprimez la mise en page problématique de `<game-directory>/config/fancymenu/customization/`)
* [Terraria Craft](https://www.curseforge.com/minecraft/mc-mods/terraria-craft)
* [The Dalek Mod](https://www.curseforge.com/minecraft/mc-mods/the-dalek-mod) (Fonctionne si son menu principal personnalisé est désactivé dans la configuration)
* [ThonkUtil](https://www.curseforge.com/minecraft/mc-mods/thonkutil) (Fonctionne, mais ajoute actuellement un texte impossible à supprimer au menu principal)
* [Trade Uses](https://modrinth.com/mod/trade-uses) (Provoque des plantages dans le menu d’échange avec les villageois — peut-être uniquement lorsque « Easy Villagers » est également installé)
* [VanillaFix](https://www.curseforge.com/minecraft/mc-mods/vanillafix) (Utilisable, mais certains utilisateurs signalent des problèmes avec l’écran de plantage de VanillaFix)
* [FireplaceMode](https://www.curseforge.com/minecraft/mc-mods/fireplacemode) (L’écran de pause réinitialise parfois ses personnalisations lorsque ce mod est installé)
* [Respackopts](https://www.curseforge.com/minecraft/mc-mods/respackopts) (Fonctionne, mais uniquement si vous désactivez les personnalisations de l’écran des packs de ressources)
* [Bind Pizzeria](https://modrinth.com/mod/jjpizza) (Casse le rendu du texte dans les menus contextuels de FancyMenu)
* [EnhancedTooltips](https://www.curseforge.com/minecraft/mc-mods/enhancedtooltips) (Casse les infobulles de FancyMenu)
* [Skin Shuffle](https://modrinth.com/mod/skinshuffle) (L’entité du joueur ajoutée aux menus par ce mod ne peut pas être personnalisée via FancyMenu)
* [Wakes](https://modrinth.com/mod/wakes) (Fait planter le jeu au lancement en raison d’une `IncompatibleClassChangeError` — le mod ne parvient pas à remplacer la méthode finale `AbstractSliderButton.getSprite()`, qui n’est finale qu’en raison de la modification de sa visibilité par Wakes ; consultez les problèmes GitHub pour plus d’informations : [Goby56/wakes n° 215](https://github.com/Goby56/wakes/issues/215), [Keksuccino/FancyMenu n° 1733](https://github.com/Keksuccino/FancyMenu/issues/1733))
* [Essential](https://www.curseforge.com/minecraft/mc-mods/essential-mod) (Consultez [cette page](/essential) pour plus d’informations)
