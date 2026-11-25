---
title: Diaporamas
description: >-
  Affichez vos propres images les unes après les autres, avec un léger fondu
  entre chacune, en arrière-plan du menu ou dans une partie de l’écran.
sourceBlobSha: 24ba0cbe9184108453b9829b8e6cd48d49a48b12
---

# Diaporamas

Un diaporama affiche des images les unes après les autres, avec un léger fondu entre chacune, comme des captures d’écran du monde de votre modpack.

Vous pouvez l’afficher comme [arrière-plan du menu](/menu-backgrounds) d’une disposition, ou dans une partie de l’écran à l’aide d’un [élément Diaporama](/elements#slideshow).

<img width="800" alt="Écran titre avec un diaporama en arrière-plan qui passe en fondu d’une vallée fluviale à une cerisaie puis à une côte, des captures d’écran d’un monde Minecraft" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/slideshows_title.gif?raw=true">

# Créer un diaporama

1. Ouvrez le dossier `slideshows` dans `config/fancymenu/` du répertoire de votre jeu. **Barre de menu -> Tools -> Open FancyMenu Directory** ouvre `config/fancymenu/`.
2. Créez-y un dossier pour votre diaporama, par exemple `world_tour`. Son nom n’a pas d’importance.
3. Ajoutez-y un fichier [`properties.txt`](#propertiestxt) et un dossier nommé `images` contenant [vos images](#les-images). Le fichier [`overlay.png`](#superposition) est facultatif.
4. Rechargez FancyMenu avec **Barre de menu -> Customization -> Reload FancyMenu** ou `Ctrl + Alt + R` (`Cmd + Alt + R` sur macOS), ou redémarrez le jeu.

```text
config/fancymenu/slideshows/
└── world_tour/
    ├── properties.txt
    ├── overlay.png
    └── images/
        ├── 01_river_valley.png
        ├── 02_cherry_grove.png
        └── 03_coast.png
```

# Les images

- Seuls les fichiers PNG et JPG sont pris en compte, avec des noms se terminant par `.png` ou `.jpg`. Renommez les fichiers `.jpeg` en `.jpg`.
- Les images s’affichent dans l’ordre alphabétique de leurs noms de fichier. Les nombres sont considérés comme des lettres : `10.png` vient donc avant `2.png`. Commencez les nombres par des zéros, par exemple `01`, `02` … `10`.
- Donnez la même taille à toutes les images. La première détermine les proportions du diaporama, et les autres sont étirées pour s’y adapter.
- Les fichiers placés dans des sous-dossiers du dossier `images` ne sont pas pris en compte.

# properties.txt

```text
type = slideshow

slideshow-meta {
  name = world_tour
  duration = 5.0
  fadespeed = 5.0
  randomize = false
}
```

| Paramètre | Fonction |
|---|---|
| `name` | Le nom utilisé pour choisir le diaporama. Donnez un nom différent à chaque diaporama. |
| `duration` | Nombre de secondes entre deux changements d’image, fondu compris. Si le fondu dure plus longtemps, le changement suivant attendra qu’il se termine. |
| `fadespeed` | Vitesse à laquelle une image se fond dans la suivante. À `1.0`, le fondu dure environ 6 secondes ; à `3.0`, environ 2 secondes. La valeur doit être supérieure à `0`. |
| `randomize` | `true` affiche les images dans un ordre aléatoire, sans jamais afficher deux fois de suite la même image. `false` les affiche dans l’ordre de leurs noms de fichier. |

Seul `name` est obligatoire. Les paramètres omis prennent les valeurs par défaut `duration = 10.0`, `fadespeed = 1.0` et `randomize = false`. Conservez les lignes `type = slideshow` et `slideshow-meta {` telles quelles, écrivez un paramètre par ligne et utilisez un point pour les décimales, par exemple `2.5`.

Les diaporamas créés pour des versions plus anciennes peuvent contenir les lignes `width`, `height`, `x` et `y`. Elles n’ont aucun effet : c’est l’arrière-plan ou l’élément qui détermine l’emplacement et la taille du diaporama.

# Superposition

Un fichier `overlay.png` placé à côté de `properties.txt` est dessiné par-dessus chaque image et étiré aux dimensions du diaporama. Il ne se fond pas avec les images : il sert donc à ajouter des cadres, des vignettes ou un logo dans un coin. Les zones transparentes laissent apparaître les images.

La superposition fait partie du diaporama et s’affiche donc partout où celui-ci apparaît. Pour afficher les mêmes images avec et sans cadre, créez deux diaporamas.

# Utiliser un diaporama

## Comme arrière-plan du menu

<img width="800" alt="Ouverture de Menu Backgrounds, choix de Slideshow dans l’éditeur de disposition, activation de Show Background et sélection de world_tour dans Choose Slideshow ; l’aperçu passe à l’image suivante en fondu, puis le diaporama s’affiche derrière les boutons de l’écran titre" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/slideshows_background.gif?raw=true">

1. Dans l’[éditeur de disposition](/layout-editor), faites un clic droit sur l’arrière-plan et ouvrez **Menu Backgrounds -> Slideshow**.
2. Cliquez sur **Show Background** pour l’activer.
3. Cliquez sur **Slideshow Name**, sélectionnez votre diaporama, puis cliquez sur **Done**. L’aperçu à droite montre le diaporama en cours de lecture.

**Clear Slideshow** permet de le retirer. Pour le combiner à d’autres arrière-plans, consultez [Arrière-plans du menu](/menu-backgrounds).

Le diaporama est étiré sur tout l’écran. Pour conserver les proportions de ses images, activez **Preserve Background Aspect Ratio** dans **Menu Backgrounds**. Le diaporama remplit alors l’écran, mais ses côtés ou ses bords supérieur et inférieur sont coupés.

## Comme élément

<img width="800" alt="Écran titre avec ses boutons à gauche et un élément Diaporama à droite qui fait défiler en fondu des captures d’écran d’un monde Minecraft" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/slideshows_element.gif?raw=true">

1. Dans l’éditeur de disposition, faites un clic droit sur une zone libre et ajoutez un diaporama avec **New Element**.
2. Faites un clic droit sur l’élément, cliquez sur **Slideshow** et sélectionnez votre diaporama. L’élément adopte les proportions de ses images.
3. Déplacez-le et redimensionnez-le comme n’importe quel autre élément. **Restore Aspect Ratio** modifie de nouveau sa largeur pour l’adapter à sa hauteur, afin que les images ne soient pas étirées.

## Préchargement

Un diaporama charge chaque image la première fois qu’elle s’affiche : les grandes images peuvent donc apparaître avec un léger retard la première fois. Pour charger toutes les images et la superposition au démarrage du jeu, ajoutez le diaporama avec **Add Slideshow** dans **Barre de menu -> Customization -> Pre-Load Resources**. Consultez [Précharger les ressources](/preload-layouts#pre-loading-slideshows--panoramas).

# Bon à savoir

- Tous les éléments qui affichent le même diaporama montrent la même image au même moment, y compris dans différents menus.
- Un diaporama ne s’exécute que lorsqu’il est affiché. S’il réapparaît après une interruption plus longue que sa `duration`, il passe immédiatement à l’image suivante en fondu.
- Le rechargement de FancyMenu relance tous les diaporamas. Après le démarrage, la première image ne reste affichée que la moitié du temps des autres.
- Les diaporamas appartiennent au [profil](/profiles) chargé.
- Si un diaporama n’apparaît pas dans **Choose Slideshow**, c’est qu’il n’a pas été chargé. Le journal du jeu, `logs/latest.log`, indique pourquoi, par exemple si `name`, `properties.txt` ou le dossier `images` est manquant.
- Sous Windows, affichez les extensions de noms de fichiers dans l’Explorateur de fichiers pour éviter que `properties.txt` ne devienne par erreur `properties.txt.txt`.
- Un damier violet et noir indique qu’aucun diaporama n’est sélectionné ou que la disposition utilise un nom de diaporama qui n’existe plus.
- Si deux diaporamas ont le même `name`, un seul des deux s’affiche.
- La **Debug Overlay** (`Ctrl + Alt + D`) indique le nombre de diaporamas et d’images chargés par FancyMenu.
