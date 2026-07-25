---
title: Panoramas
description: Créez et utilisez des panoramas cubiques à six images.
---
# Panoramas cubiques

Chaque panorama possède son propre répertoire ci-dessous :

```text
<game-directory>/config/fancymenu/panoramas/
```

`<game-directory>` est l'instance de lancement active, qui peut être différente du répertoire `.minecraft` habituel.

# Structure du répertoire

```text
<game-directory>/config/fancymenu/panoramas/
└── mypanorama/
    ├── properties.txt
    ├── overlay.png          # facultatif
    └── panorama/
        ├── panorama_0.png
        ├── panorama_1.png
        ├── panorama_2.png
        ├── panorama_3.png
        ├── panorama_4.png
        └── panorama_5.png
```

Les six images de faces doivent être des fichiers PNG portant exactement les noms indiqués ci-dessus, et les six doivent avoir des dimensions identiques. La casse du nom de fichier peut compter sur certains systèmes d'exploitation.

Ajoutez un `overlay.png` facultatif à côté de `properties.txt` pour une vignette ou un autre calque superposé sur tout le panorama.

# `properties.txt`

```text
type = panorama

panorama-meta {
  name = name_of_your_panorama
  speed = 1.0
  fov = 85.0
  angle = 25.0
  start_rotation = 0
}
```

| Propriété | Signification |
|---|---|
| `name` | Identifiant d'exécution obligatoire, sensible à la casse ; conservez un nom unique |
| `speed` | Multiplicateur de vitesse de rotation ; `1.0` est la valeur par défaut |
| `fov` | Champ de vision en degrés |
| `angle` | Angle de vue vertical en degrés |
| `start_rotation` | Rotation horizontale initiale en degrés |

Seul `name` est obligatoire. Les valeurs facultatives manquantes utilisent les valeurs par défaut indiquées dans l'exemple. Conservez `type = panorama` et `panorama-meta` inchangés ; écrivez une ligne `key = value` par ligne et utilisez un point pour les décimales.

Les noms en double ne sont pas rejetés, et l'ordre d'analyse des répertoires détermine quel panorama reste disponible. Conservez des noms uniques dans le répertoire des panoramas. Les noms des panoramas et des diaporamas utilisent des listes séparées.

# Utiliser un panorama

Rechargez FancyMenu via **Personnalisation -> Recharger FancyMenu**, ou redémarrez le client. Ensuite, faites un clic droit sur l'arrière-plan de l'éditeur de disposition et sélectionnez [**Arrière-plans du menu**](./menu-backgrounds) -> **Panorama cubique**.
