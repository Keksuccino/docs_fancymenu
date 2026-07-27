---
title: Diaporamas
description: Créer et utiliser des diaporamas d’images.
---

# Diaporamas

Chaque diaporama possède son propre dossier ci-dessous :

```text
<game-directory>/config/fancymenu/slideshows/
```

`<game-directory>` est l’instance de lancement active, qui peut différer du dossier `.minecraft` conventionnel.

# Structure du dossier

```text
<game-directory>/config/fancymenu/slideshows/
└── myslideshow/
    ├── properties.txt
    ├── overlay.png          # facultatif
    └── images/
        ├── image_01.png
        └── image_02.jpg
```

Les images doivent utiliser l’extension `.png` ou `.jpg` ; les autres extensions, y compris `.jpeg`, sont ignorées.

Lorsque `randomize = false`, les images sont lues dans l’ordre alphabétique des noms de fichiers, sans tenir compte des majuscules/minuscules. Utilisez des noms avec des zéros en tête, par exemple `image_01.png`, `image_02.png` et `image_10.png`.

# `properties.txt`

```text
type = slideshow

slideshow-meta {
  name = cool_slideshow
  width = 1920
  height = 1080
  x = 0
  y = 0
  duration = 5.0
  fadespeed = 12.0
  randomize = false
}
```

| Propriété | Signification |
|---|---|
| `name` | Identifiant d’exécution requis et sensible à la casse ; gardez-le unique |
| `width`, `height` | Taille de base en pixels à l’échelle de l’interface et rapport d’aspect de la source |
| `x`, `y` | Position de base en haut à gauche ; les éléments normaux et les arrière-plans utilisent leur propre position, donc laissez-les à `0` |
| `duration` | Nombre minimal de secondes entre les débuts de transition ; inclut le temps de fondu et doit être supérieur à `0` |
| `fadespeed` | Multiplicateur de vitesse de fondu ; `1.0` est la valeur par défaut, des valeurs plus élevées accélèrent le fondu, et la valeur doit être supérieure à `0` |
| `randomize` | `true` pour une sélection aléatoire ou `false` pour l’ordre des noms de fichiers |

Seul `name` est requis. Les valeurs par défaut sont `width = 50`, `height = 50`, `x = 0`, `y = 0`, `duration = 10.0`, `fadespeed = 1.0` et `randomize = false`. Conservez `type = slideshow` et `slideshow-meta` inchangés ; écrivez une seule ligne `key = value` par ligne et utilisez un point pour les décimales.

Les dispositions utilisent la valeur de `name`, et non le nom du dossier. Les noms en double ne sont pas rejetés, et l’ordre d’analyse des dossiers détermine quel diaporama reste disponible. Gardez des noms uniques dans le dossier des diaporamas.

Le mode aléatoire choisit indépendamment à chaque transition et évite une répétition immédiate lorsque plusieurs images sont disponibles. Le minutage utilise le temps réel ; un fondu qui dure plus longtemps que `duration` retarde la transition suivante, et le retour à un diaporama après qu’il a été masqué peut le faire avancer immédiatement.

# Utiliser un diaporama

Rechargez FancyMenu via **Personnalisation -> Recharger FancyMenu**, ou redémarrez le client. Utilisez l’[élément **Diaporama**](./elements#slideshow), ou faites un clic droit sur l’arrière-plan de l’éditeur de disposition et sélectionnez [**Arrière-plans du menu**](./menu-backgrounds) -> **Diaporama**.
