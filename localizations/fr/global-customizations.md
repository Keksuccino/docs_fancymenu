---
title: Personnalisations globales
description: >-
  Modifiez en une seule fois les boutons, les curseurs, les arrière-plans des
  menus, la musique et la fenêtre de tous les écrans, sans mise en page.
sourceBlobSha: cafc7ed87ce931e406fb14b7a605085b565ce1a7
---

# Personnalisations globales

Les personnalisations globales s’appliquent en une seule fois à tous les écrans : boutons, curseurs, arrière-plans des menus, musique, fenêtre du jeu et bien plus encore. Elles ne nécessitent aucune mise en page et fonctionnent également sur les écrans dont la personnalisation est désactivée.

Ouvrez-les depuis **barre de menus -> Personnalisation -> Personnalisations globales**, sur n’importe quel écran en dehors de l’éditeur de mise en page. Les modifications s’appliquent immédiatement et sont enregistrées automatiquement.

<img width="800" alt="Les écrans Titre, Options et Musique et sons sans mise en page, tous avec les mêmes boutons en bois, des poignées de curseur en laiton, des libellés qui deviennent dorés au survol et un arrière-plan nocturne" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/global_customizations_tour.gif?raw=true">

> [!TIP]
> Pour ne modifier que certains écrans, utilisez les [mises en page](/layout-editor). Pour donner un style particulier aux boutons de certaines mises en page, utilisez les [modèles de boutons et de curseurs](/button-slider-templates).

# Boutons et curseurs

Ces paramètres modifient tous les boutons et curseurs de tous les écrans, y compris ceux d’autres mods.

- Les boutons et curseurs qui ont leurs propres textures ou paramètres de libellé provenant d’une [mise en page](/layout-editor) ou d’un [modèle](/button-slider-templates) les conservent.
- Les boutons qui sont uniquement des images, comme celui du livre de recettes, conservent leur apparence.

## Textures des boutons

**Textures de boutons personnalisées** permet de définir une texture pour chaque état d’un bouton :

- **Normal**
- **Survolé** : lorsque la souris se trouve sur le bouton ou qu’il est sélectionné au clavier.
- **Désactivé** : lorsque le bouton ne peut pas être cliqué.

Définissez les trois textures. Si un état n’a pas de texture, le bouton Minecraft correspondant s’affiche.

Autres paramètres du même menu :

- **Arrière-plan transparent** masque l’arrière-plan de tous les boutons pour n’afficher que leurs libellés. Ce paramètre a priorité sur les textures.
- **Arrière-plans de boutons en neuf tranches** préserve la netteté des bords des textures, quelle que soit la taille des boutons, grâce aux quatre dimensions de bordure ci-dessous. Consultez [Découpage en neuf tranches et répétition](/nine-slicing-and-tiling).

> [!TIP]
> Sans découpage en neuf tranches, les textures sont étirées pour s’adapter à la taille de chaque bouton. Les boutons Minecraft font 20 pixels de haut et mesurent le plus souvent 200 ou 150 pixels de large. Le découpage en neuf tranches permet d’utiliser une petite texture pour tous ces boutons.

## Textures des curseurs

**Textures de curseurs personnalisées** comporte deux parties :

- **Texture d’arrière-plan du curseur** : la barre du curseur. Définissez-la avec **Définir la texture**. Les options **Arrière-plan transparent** et **Arrière-plan du curseur en neuf tranches** fonctionnent comme celles des boutons.
- **Textures de la poignée du curseur** : la partie que vous faites glisser, avec les textures **Normal**, **Survolé** et **Désactivé**, ainsi que l’option **Poignée du curseur en neuf tranches**.

La poignée des curseurs Minecraft fait 8 pixels de large et a la même hauteur que le curseur, généralement 20 pixels. Sans découpage en neuf tranches, les textures de poignée sont étirées pour atteindre ces dimensions.

## Libellés

**Libellés des boutons** et **Libellés des curseurs** proposent les mêmes paramètres :

| Paramètre | Fonction |
|---|---|
| **Souligner le libellé au survol** | Souligne le libellé lorsque la souris se trouve dessus. |
| **Couleur de base du libellé** | Couleur du libellé. Choisissez-la avec le sélecteur de couleurs ou saisissez un code HEX, comme `#FFF1D6`. |
| **Couleur du libellé au survol** | Couleur du libellé lorsque la souris se trouve dessus. |
| **Échelle du libellé** | Taille du libellé. `1` correspond à la taille normale. |
| **Alignement du libellé** | **À gauche**, **Centré** ou **À droite**. |
| **Ombre du libellé** | Ombre sombre derrière le libellé. Si cette option est désactivée, aucun libellé n’a d’ombre, même ceux provenant de mises en page. |

Les libellés qui ont leurs propres paramètres provenant d’une mise en page ou d’un modèle les conservent. Pour **Échelle du libellé** et **Alignement du libellé**, le paramètre global ne s’applique qu’aux libellés de taille normale et **Centrés**.

## Son de clic

- **Son de clic personnalisé des boutons** remplace le son de clic de Minecraft pour les boutons et les curseurs. Les boutons qui ont leur propre son de clic défini dans une mise en page le conservent.
- **Volume du son de clic personnalisé des boutons** va de 0 % à 100 %. Le curseur de volume du canal correspondant dans les paramètres audio de Minecraft s’applique également.
- **Canal du son de clic personnalisé des boutons** définit le canal audio utilisé, par exemple Musique. Par défaut, il s’agit du volume principal, le canal de tous les sons.

# Arrière-plans des menus

**Texture d’arrière-plan de menu personnalisée** affiche une image derrière tous les menus, à l’exception de l’écran titre :

- Elle s’affiche également derrière le menu Pause et les options lorsque vous jouez, masquant ainsi le monde. Les inventaires, panneaux et livres restent transparents.
- **Conserver les proportions de la texture d’arrière-plan** préserve les proportions de l’image. Celle-ci remplit tout de même l’écran, et les parties qui dépassent sont coupées. Si l’option est désactivée, l’image est étirée pour remplir l’écran.

**Panorama personnalisé des menus** remplace le panorama de Minecraft sur l’écran titre et dans tous les menus avant que vous rejoigniez un monde :

- **Choisir un panorama** permet de choisir l’un de vos [panoramas](/panoramas).
- **Effacer le panorama** rétablit le panorama de Minecraft.
- **Panorama actuel** indique celui qui est défini.

Si les deux options sont définies, la texture recouvre le panorama, qui ne reste donc visible que sur l’écran titre.

Les écrans dont la mise en page possède son propre [arrière-plan de menu](/menu-backgrounds) l’affichent à la place.

# Musique des menus

- **Lire la musique des menus par défaut** active ou désactive la musique de Minecraft dans les menus.
- **Pistes musicales personnalisées des menus** ouvre **Gérer les pistes musicales des menus**. **Ajouter une piste** ajoute un son, **Supprimer la piste** supprime la piste sélectionnée, **Effacer les pistes** les supprime toutes et **Terminé** enregistre la liste.

Les pistes sont lues dans un ordre aléatoire dans les menus, avant que vous rejoigniez un monde, à la place de la musique des menus de Minecraft. Pour en savoir plus sur ces pistes et sur la musique propre à chaque écran : [Musique d’arrière-plan des menus](/background-music).

# Écrans et fenêtres contextuelles

| Paramètre | Fonction |
|---|---|
| [**Intro du jeu**](/game-intro) | Lance une animation ou une vidéo avant l’affichage de l’écran titre. |
| **Icônes des mondes de l’écran Solo** | Icônes des mondes dans la liste des mondes. Si l’option est désactivée, elles sont masquées. |
| **Icônes des serveurs de l’écran Multijoueur** | Icônes des serveurs dans la liste des serveurs. Si l’option est désactivée, elles sont masquées. |
| [**Chargement fluide des mondes**](/seamless-world-loading) | Prend une capture d’écran lorsque vous quittez un monde ou un serveur, puis l’affiche comme arrière-plan de chargement lorsque vous le rejoignez à nouveau. |
| **Notifications de succès** | Fenêtres contextuelles en haut à droite qui s’affichent lorsque vous débloquez un succès, ainsi que leurs sons. Si l’option est désactivée, elles sont masquées. Les messages de succès dans le chat restent visibles et le déclencheur [Lorsqu’un succès est débloqué](/listeners#on-achievement-unlocked) fonctionne toujours. |

# Fenêtre et démarrage du jeu

| Paramètre | Fonction |
|---|---|
| [**Icône de fenêtre personnalisée**](/window-customization#custom-icon) | Icône de la fenêtre du jeu. Il faut une icône PNG de 16x16, une de 32x32 et une icône macOS. |
| [**Titre de fenêtre personnalisé**](/window-customization#custom-title) | Remplace le titre de la fenêtre Minecraft. Les [espaces réservés](/placeholders) sont pris en charge et le titre est actualisé lorsqu’ils changent. |
| **Échelle de l’interface par défaut** | Définit l’échelle de l’interface Minecraft une seule fois, au premier démarrage de l’instance du jeu, par exemple `2` ou `3`. La valeur `-1` désactive cette option. Conçue pour les modpacks. |
| **Forcer le plein écran au démarrage** | Lance le jeu en plein écran à chaque démarrage. |

FancyMenu mémorise qu’il a défini l’**Échelle de l’interface par défaut** dans `fancymenu_data/default_scale_set.fm`. Supprimez ce fichier pour qu’il définisse à nouveau l’échelle au prochain démarrage (voir [Emplacements de stockage des données](/data-storage-locations#instance-data)).

# Bon à savoir

- Les personnalisations globales sont enregistrées dans le fichier `options.txt` de FancyMenu. Elles sont donc associées au [profil](/profiles) chargé et incluses dans les modpacks qui contiennent `config/fancymenu/`.
- Les textures et les sons peuvent être des fichiers de votre instance, des liens Web ou des fichiers de packs de ressources. Consultez [Ressources](/resources).
- **barre de menus -> Aide -> Exporter pour l’IA -> Paramètres de FancyMenu** les inclut, pour vous aider à poser des questions dans une [conversation avec une IA](/export-for-ai).
