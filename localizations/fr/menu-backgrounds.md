---
title: Arrière-plans des menus
description: >-
  Donnez à un menu son propre arrière-plan — image, panorama, vidéo, couleur ou
  shader — et superposez-en plusieurs.
sourceBlobSha: 934e0cbcce41f049826fcd7b96715e3cb0e27214
---

# Arrière-plans des menus

Une disposition peut donner à son écran son propre arrière-plan : une image, une animation, un panorama, un diaporama, une vidéo, une couleur, un site web ou un shader. Celui-ci remplace l’arrière-plan normal de l’écran, comme le panorama de l’écran titre, le flou des autres menus ou le monde derrière le menu de pause.

<img width="800" alt="L’écran titre avec un arrière-plan en pixel art représentant une vallée enneigée de nuit, avec une aurore boréale, une pleine lune et une cabane aux fenêtres éclairées" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/menu_backgrounds_hero.png?raw=true">

> [!TIP]
> Pour donner le même arrière-plan à tous les menus sans créer de dispositions, utilisez les [Personnalisations globales](/global-customizations#menu-backgrounds).

# Définir un arrière-plan

<img width="800" alt="Clic droit sur l’arrière-plan de l’éditeur de l’écran titre, ouverture de Arrière-plans des menus puis Image, activation de Afficher l’arrière-plan et sélection d’une image via Choisir une image" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/menu_backgrounds_image.gif?raw=true">

1. Ouvrez une disposition de l’écran dans l’[éditeur de disposition](/layout-editor).
2. Faites un clic droit sur l’arrière-plan de l’éditeur, puis ouvrez **Arrière-plans des menus**. Cette option se trouve également dans **barre de menus -> Disposition -> Propriétés de la disposition**.
3. Ouvrez un type d’arrière-plan, par exemple **Image**.
4. Cliquez sur **Afficher l’arrière-plan** pour le régler sur **Activé**.
5. Configurez l’arrière-plan, par exemple avec **Choisir une image** pour un arrière-plan de type Image.

<img width="800" alt="Le menu Arrière-plans des menus, avec une coche devant Image et une croix devant tous les autres types, puis les paramètres de tous les arrière-plans en dessous" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/menu_backgrounds_menu.png?raw=true">

Dans **Arrière-plans des menus**, chaque type activé est précédé d’un ✔ et chaque type désactivé d’un ✖. Survolez un type pour voir à quoi il sert.

Pour rétablir l’arrière-plan normal de l’écran, réglez de nouveau **Afficher l’arrière-plan** du type sur **Désactivé**. Ses paramètres sont conservés ; vous pourrez donc le réactiver plus tard.

# Types d’arrière-plans

## Image

Une image provenant de vos fichiers, d’un site web ou des ressources du jeu, étirée sur tout l’écran. Les images animées sont également prises en charge. La liste des fichiers compatibles figure dans [Images](/images).

- **Choisir une image** : l’image. Consultez [Ressources](/resources) pour connaître les sources possibles.
- **Choisir une image de secours** : image affichée lorsque l’image ne peut pas être chargée, par exemple une image web lorsque vous êtes hors ligne.
- **Redémarrer les textures animées à l’ouverture de l’écran** : relance une [image animée](/animations) depuis le début à chaque ouverture de l’écran. Sinon, elle reprend là où elle en était.
- **Répéter la texture** : répète l’image sur l’écran au lieu de l’étirer. Voir [Découpage en neuf et répétition](/nine-slicing-and-tiling).
- **Faire défiler les images larges de gauche à droite** : une image large, comme une photo d’un paysage entier, remplit la hauteur de l’écran et défile lentement d’un côté à l’autre, avec une courte pause à chaque extrémité.
- **Effet de parallaxe** et ses paramètres : l’image bouge légèrement avec la souris. Voir [Effet de parallaxe](/parallax#menu-backgrounds).

**Faire défiler les images larges de gauche à droite** ne peut pas être activé en même temps que **Répéter la texture** ou **Effet de parallaxe**.

## Couleur

Une seule couleur sur tout l’écran.

- **Couleur [HEX]** : la couleur, par exemple `#1B2440`. Ajoutez deux chiffres pour la rendre transparente, par exemple `#1B2440C8`. Il peut également s’agir d’un [espace réservé](/placeholders).

La couleur se trouve sous tous les autres arrière-plans de la disposition et remplit donc leurs parties transparentes. Voir [Superposer des arrière-plans](#stacking-backgrounds).

## Panorama cubique

Un panorama qui pivote lentement, comme celui de l’écran titre. Créez vos panoramas dans `config/fancymenu/panoramas/`. Voir [Panoramas](/panoramas).

- **Nom du panorama** : ouvre **Choisir un panorama**, où vous pouvez sélectionner l’un de vos panoramas et en voir un aperçu.
- **Effacer le panorama** : supprime le panorama.

Sans panorama, l’arrière-plan affiche la texture manquante violette et noire de Minecraft.

## Diaporama

Affiche les images d’un diaporama les unes après les autres. Créez vos diaporamas dans `config/fancymenu/slideshows/`. Voir [Diaporamas](/slideshows).

- **Nom du diaporama** : ouvre **Choisir un diaporama**, où vous pouvez sélectionner l’un de vos diaporamas.
- **Effacer le diaporama** : supprime le diaporama.

Sans diaporama, l’arrière-plan affiche également la texture manquante de Minecraft.

## Vidéo

Lit une vidéo provenant de vos fichiers, d’un site web ou des ressources du jeu. Watermedia est nécessaire : voir [Vidéos](/video#requirements). Sans ce mod, l’arrière-plan affiche une note avec des liens de téléchargement.

- **Source vidéo** : la vidéo.
- **Lire la vidéo en boucle**, **Volume** et **Canal audio** : les paramètres de lecture.
- **Effet de parallaxe** et ses paramètres : comme pour les arrière-plans de type Image.
- **Lire la vidéo dans l’éditeur de disposition** : si cette option est désactivée, la vidéo reste en pause dans l’éditeur de disposition.

Les [actions](/video) peuvent mettre la vidéo en pause et modifier son volume et sa position de lecture. Elles ont besoin de l’ID de l’arrière-plan : cliquez sur **Copier l’identifiant de l’arrière-plan** dans ses paramètres.

## Navigateur

Un site web sur tout l’écran, comme l’[élément Navigateur](/elements#browser).

> [!IMPORTANT]
> Le navigateur nécessite le mod [Rinku](https://modrinth.com/mod/rinku). Sans lui, l’arrière-plan est rouge et indique que Rinku est manquant.

- **URL** : le site web. Elle peut contenir des [espaces réservés](/placeholders).
- **Traiter les clics de souris**, **Traiter le défilement de la souris** et **Traiter les frappes au clavier** : permettent aux joueurs de cliquer, de faire défiler et de saisir du texte sur le site web. Le navigateur reçoit le clavier dès l’ouverture de l’écran.
- **Intercepter les clics de souris**, **Intercepter le défilement de la souris** et **Intercepter les frappes au clavier** : bloquent les clics, le défilement et les frappes sur le site web, afin que l’écran lui-même n’y réagisse pas non plus.
- **Couper le son du navigateur**, **Volume audio/vidéo**, **Lire les vidéos en boucle** et **Masquer les commandes vidéo** : paramètres des médias du site web.

Les boutons et éléments placés devant l’arrière-plan reçoivent toujours les clics en premier. Dans l’éditeur de disposition, l’arrière-plan affiche des rayures à la place du site web.

## Shader GLSL

Affiche un shader, un petit programme destiné à la carte graphique, qui peut produire des vagues animées, des étoiles ou des motifs, par exemple. Les shaders de Shadertoy sont également compatibles.

- **Source du shader** : le code du shader.
- **Afficher les erreurs de compilation** : affiche à l’écran les erreurs présentes dans le code. Désactivez cette option pour les dispositions terminées.

Tous les autres paramètres, comme les passes supplémentaires, les textures et le temps, sont expliqués dans l’[API Shader GLSL](/glsl-shader-api).

## Vidéo [Rinku]

Un ancien arrière-plan vidéo qui nécessite Rinku. Il n’apparaît dans la liste que lorsqu’il est activé, par exemple dans les dispositions créées avec d’anciennes versions. Utilisez plutôt **Vidéo**.

# Paramètres communs à tous les arrière-plans

Sous les types, **Arrière-plans des menus** propose des paramètres qui s’appliquent à tous les arrière-plans de la disposition :

- **Conserver les proportions de l’arrière-plan** : conserve les proportions des arrière-plans de type Image, Diaporama et Vidéo. Ils remplissent toujours tout l’écran, mais les parties qui ne tiennent pas sont coupées. Si cette option est désactivée, ils sont étirés pour remplir l’écran.
- **Afficher un voile sombre sur l’arrière-plan personnalisé** : ajoute par-dessus les arrière-plans le voile sombre et transparent des menus de Minecraft, afin de mieux faire ressortir les boutons et le texte.
- **Appliquer le flou d’arrière-plan de Minecraft** : floute les arrière-plans comme Minecraft floute le monde derrière les menus. L’intensité dépend du paramètre **Flou d’arrière-plan des menus** du joueur, dans les **Paramètres d’accessibilité** de Minecraft. À `0`, il n’y a aucun flou.

<img width="800" alt="Le même arrière-plan présenté trois fois côte à côte : tel quel, assombri avec Afficher un voile sombre sur l’arrière-plan personnalisé, puis flouté avec Appliquer le flou d’arrière-plan de Minecraft" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/menu_backgrounds_effects.png?raw=true">

De gauche à droite : aucun paramètre, **Afficher un voile sombre sur l’arrière-plan personnalisé** et **Appliquer le flou d’arrière-plan de Minecraft**.

# Superposer des arrière-plans

Vous pouvez activer plusieurs types dans une même disposition. Ils sont dessinés les uns par-dessus les autres dans cet ordre, du bas vers le haut :

1. Couleur
2. Panorama cubique
3. Image
4. Diaporama
5. Vidéo
6. Vidéo [Rinku]
7. Navigateur
8. Shader GLSL

Les types ajoutés par d’autres mods sont dessinés en dernier, tout en haut.

FancyMenu dessine du noir derrière les arrière-plans ; les parties transparentes d’une image apparaissent donc en noir. Un arrière-plan de type Couleur placé en dessous les remplit avec une couleur :

<img width="800" alt="Un paysage en pixel art avec un ciel transparent. Sur la moitié gauche, le ciel est noir. Sur la moitié droite, un arrière-plan de type Couleur le remplit de bleu" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/menu_backgrounds_stacking.png?raw=true">

À gauche, seul l’arrière-plan Image est activé. À droite, un arrière-plan de type Couleur remplit le ciel.

- Une Image, un Diaporama ou un Shader transparent placé au-dessus d’un Panorama cubique fonctionne de la même façon, par exemple comme un cadre autour d’un panorama en rotation.
- Un arrière-plan de type Vidéo n’est jamais transparent. Il recouvre tout ce qui se trouve dessous, même là où la vidéo ne s’étend pas.

## Plusieurs dispositions

Lorsque plusieurs dispositions sont actives sur un écran, par exemple une [disposition universelle](/universal-layouts) et une disposition propre à l’écran, leurs arrière-plans se superposent également :

- La disposition ayant l’**Index de disposition [Ordre multi-dispositions]** le plus élevé est placée au-dessus. Définissez cet index dans le menu contextuel accessible par clic droit sur l’arrière-plan de l’éditeur.
- Si l’une des dispositions active un [paramètre commun à tous les arrière-plans](#settings-for-all-backgrounds), celui-ci s’applique aux arrière-plans de toutes les dispositions.
- L’éditeur de disposition n’affiche que les arrière-plans de la disposition que vous modifiez.

# Bon à savoir

- Les éléments de la disposition sont toujours placés devant ses arrière-plans.
- **Copier l’identifiant de l’arrière-plan**, dans les paramètres de chaque type, copie l’ID de l’arrière-plan pour les actions et les espaces réservés qui le contrôlent, comme ceux des [arrière-plans vidéo](/video).
- **Exporter pour l’IA**, dans les paramètres de chaque type, copie l’arrière-plan pour une [conversation avec une IA](/export-for-ai).
- L’en-tête et le pied de page des écrans comportant des listes, comme la liste des mondes, ont leurs propres textures : faites un clic droit sur l’arrière-plan de l’éditeur, puis ouvrez **Personnalisations de l’en-tête/du pied de page**.
