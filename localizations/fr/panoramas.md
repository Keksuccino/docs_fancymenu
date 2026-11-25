---
title: Panoramas
description: >-
  Créez vos propres arrière-plans panoramiques rotatifs à partir de six images,
  comme celui de l’écran-titre de Minecraft.
sourceBlobSha: e1f9ab155301f1b88df58dd8414eeee5714cfba6
---

# Panoramas

Un panorama est un arrière-plan qui tourne lentement autour de vous, comme celui de l’écran-titre de Minecraft. Il est composé de six images qui forment un cube autour du spectateur.

Vous pouvez afficher vos propres panoramas comme [arrière-plan de menu](/menu-backgrounds) d’une mise en page, ou remplacer le panorama de Minecraft dans tous les menus.

<img width="800" alt="L’écran-titre devant un panorama qui tourne lentement, représentant une cabane en rondins dans une clairière au coucher du soleil, avec un jardin, un abri à bois et un poulailler" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/panoramas_title.gif?raw=true">

> [!TIP]
> Le panorama présenté sur cette page est gratuit et peut être utilisé à des fins de test ou dans vos propres modpacks : [forest_homestead.zip](https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/forest_homestead.zip) (4 Mo). Décompressez-le dans `config/fancymenu/panoramas/`, puis rechargez FancyMenu.

# Créer un panorama

1. Ouvrez le dossier `panoramas` dans `config/fancymenu/`, dans le répertoire de votre jeu. **Barre de menus -> Outils -> Ouvrir le répertoire FancyMenu** ouvre `config/fancymenu/`.
2. Créez-y un dossier pour votre panorama, par exemple `forest_homestead`. Son nom n’a pas d’importance.
3. Ajoutez-y un fichier `properties.txt` et un dossier nommé `panorama` contenant les [six images](#les-six-images). Le fichier `overlay.png` est facultatif.
4. Rechargez FancyMenu avec **Barre de menus -> Personnalisation -> Recharger FancyMenu** ou `Ctrl + Alt + R` (`Cmd + Alt + R` sur macOS), ou redémarrez le jeu.

```text
config/fancymenu/panoramas/
└── forest_homestead/
    ├── properties.txt
    ├── overlay.png
    └── panorama/
        ├── panorama_0.png
        ├── panorama_1.png
        ├── panorama_2.png
        ├── panorama_3.png
        ├── panorama_4.png
        └── panorama_5.png
```

# Les six images

Chaque image représente une face du cube :

<img width="796" alt="Les six images du panorama forest_homestead disposées comme un cube déplié : l’image du haut au-dessus de celle de devant, les images de gauche, de devant, de droite et de derrière alignées, et l’image du bas sous celle de devant" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/panoramas_cube.png?raw=true">

| Image | Face |
|---|---|
| `panorama_0.png` | Devant |
| `panorama_1.png` | Droite |
| `panorama_2.png` | Derrière |
| `panorama_3.png` | Gauche |
| `panorama_4.png` | Haut |
| `panorama_5.png` | Bas |

- Les quatre faces latérales se succèdent autour de vous dans cet ordre : le bord droit de chaque image se prolonge au bord gauche de la suivante, et le bord droit de `panorama_3.png` rejoint le bord gauche de `panorama_0.png`.
- Le bord inférieur de l’image du haut touche le bord supérieur de l’image de devant. Le bord supérieur de l’image du bas touche le bord inférieur de l’image de devant.
- Les six fichiers doivent être des images PNG de même taille. Utilisez des images carrées, par exemple de 1024 × 1024 pixels.
- FancyMenu ne lisse pas les images : le pixel art reste donc net.

Minecraft utilise la même disposition pour son propre panorama. Les panoramas créés pour Minecraft fonctionnent donc aussi.

# properties.txt

```text
type = panorama

panorama-meta {
  name = forest_homestead
  speed = 2.0
  fov = 85.0
  angle = 25.0
  start_rotation = 0
}
```

| Paramètre | Fonction |
|---|---|
| `name` | Le nom permettant de sélectionner le panorama. Attribuez un nom unique à chaque panorama. |
| `speed` | La vitesse de rotation. `1.0` correspond à un tour complet en environ 4 minutes ; `2.0` est deux fois plus rapide. `0` désactive la rotation. Les valeurs supérieures à `10.0` n’accélèrent pas davantage la rotation. |
| `fov` | La portion du panorama visible à l’écran, en degrés du haut vers le bas de l’écran. Plus la valeur est petite, plus l’image est zoomée. |
| `angle` | L’inclinaison vers le bas, en degrés. `0` correspond à une vue à l’horizontale ; les valeurs négatives orientent la vue vers le haut. |
| `start_rotation` | L’angle de départ de la rotation, de `0` à `360` degrés. `0` commence avec l’image de devant au centre. |

Seul le paramètre `name` est obligatoire. Les paramètres omis prennent les valeurs `speed = 1.0`, `fov = 85.0`, `angle = 25.0` et `start_rotation = 0`. Conservez les lignes `type = panorama` et `panorama-meta {` telles quelles, écrivez un paramètre par ligne et utilisez un point pour les décimales, par exemple `1.5`.

# Superposition

Un fichier `overlay.png` placé à côté de `properties.txt` est affiché par-dessus le panorama et étiré pour couvrir tout l’écran. Il ne tourne pas avec le panorama : il sert donc à ajouter, par exemple, un vignettage, un cadre ou une teinte. Les parties transparentes laissent voir le panorama.

# Utiliser un panorama

## Comme arrière-plan de menu

<img width="800" alt="Ouverture de la rubrique Arrière-plans de menu, sélection de Panorama cubique dans l’éditeur de mise en page, activation de Afficher l’arrière-plan et choix de forest_homestead dans Choisir un panorama ; le panorama tourne ensuite derrière les boutons de l’écran-titre" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/panoramas_background.gif?raw=true">

1. Dans l’[éditeur de mise en page](/layout-editor), faites un clic droit sur l’arrière-plan, puis ouvrez **Arrière-plans de menu -> Panorama cubique**.
2. Cliquez sur **Afficher l’arrière-plan** pour l’activer.
3. Cliquez sur **Nom du panorama**, sélectionnez votre panorama, puis cliquez sur **Terminé**. L’aperçu à droite montre le panorama en rotation.

**Effacer le panorama** permet de le retirer. Pour le combiner avec d’autres arrière-plans, consultez la page [Arrière-plans de menu](/menu-backgrounds).

## Dans tous les menus

**Barre de menus -> Personnalisation -> Personnalisations globales -> Panorama d’arrière-plan personnalisé des menus -> Choisir un panorama** affiche votre panorama à la place de celui de Minecraft sur l’écran-titre et dans tous les menus avant que vous rejoigniez un monde. Consultez la page [Personnalisations globales](/global-customizations#menu-backgrounds).

## Préchargement

Un grand panorama peut mettre un instant à s’afficher la première fois. Pour le charger pendant le démarrage du jeu, ajoutez-le avec **Ajouter un panorama cubique** dans **Barre de menus -> Personnalisation -> Précharger des ressources**. Consultez la page [Précharger des ressources](/preload-layouts#pre-loading-slideshows--panoramas).

# Bon à savoir

- Les panoramas tournent vers la droite : l’image de devant se déplace vers la gauche et l’image de droite apparaît.
- Tous les menus affichant le même panorama partagent sa rotation. Celle-ci se poursuit donc sans à-coups lorsque vous passez d’un menu à l’autre. La rotation se met en pause lorsqu’aucun menu n’affiche le panorama.
- Lorsque vous rechargez FancyMenu, chaque panorama reprend à son angle `start_rotation`.
- Les panoramas appartiennent au [profil](/profiles) chargé.
- Si un panorama n’apparaît pas dans **Choisir un panorama**, c’est qu’il n’a pas été chargé. Le journal du jeu, `logs/latest.log`, indique la raison, par exemple un paramètre `name` ou une image manquante.
- Un damier violet et noir signifie qu’aucun panorama n’a encore été sélectionné, que les six images n’ont pas la même taille ou que la mise en page utilise un nom de panorama qui n’existe plus.
- Si deux panoramas ont le même `name`, un seul d’entre eux s’affiche.
