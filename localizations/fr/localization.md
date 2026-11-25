---
title: Localiser les mises en page
description: Localisez le texte et les autres éléments de mise en page.
sourceBlobSha: f4883414b07e0c024de7bef4f131b878ca4f5f37
---

# Localiser les mises en page

Utilisez l’espace réservé [**Localiser le texte**](/placeholders#localize-text) pour le texte à traduire :

```text
{"placeholder":"local","values":{"key":"modpack.menu.play"}}
```

FancyMenu vérifie d’abord les données de langue actives de Minecraft. Si la clé ne s’y trouve pas, il vérifie les fichiers de localisation personnalisés de FancyMenu. Si aucun de ces emplacements ne contient la clé, celle-ci est affichée telle quelle.

# Fichiers de localisation personnalisés de FancyMenu

Placez les fichiers dans le répertoire suivant :

```text
<game-directory>/config/fancymenu/custom_locals/
```

Créez un sous-répertoire pour vos fichiers de localisation :

```text
custom_locals/
└── my_pack/
    └── text.json
```

Placez les fichiers de localisation dans au moins un sous-répertoire de `custom_locals` ; les fichiers placés directement à la racine de `custom_locals` ne sont pas chargés. Les sous-répertoires imbriqués sont pris en charge.

Formats UTF-8 pris en charge :

| Extension | Format |
|---|---|
| `.json` | Objet JSON ; les objets imbriqués deviennent des clés séparées par des points |
| `.lang` | Lignes au format `key=value` |
| `.properties` | Syntaxe des fichiers de propriétés Java |

Exemple JSON :

```json
{
  "modpack": {
    "menu": {
      "play": "Play"
    }
  }
}
```

Cela définit la clé `modpack.menu.play`.

FancyMenu regroupe les fichiers pris en charge de ces sous-répertoires dans un dictionnaire de localisation personnalisé unique. Utilisez chaque clé dans un seul fichier. Les fichiers de localisation personnalisés ne changent pas en fonction de la langue sélectionnée dans Minecraft ; si vous avez besoin d’un changement automatique de langue, utilisez la méthode des packs de ressources décrite ci-dessous.

Redémarrez le client après avoir modifié les fichiers de localisation personnalisés.

# Texte spécifique à une langue

Pour que la langue change automatiquement en fonction de celle sélectionnée dans Minecraft, fournissez des fichiers de langue Minecraft standard dans un [pack de ressources](/resources#minecraft-resources-resource-packs) :

```text
assets/<namespace>/lang/en_us.json
assets/<namespace>/lang/de_de.json
```

Utilisez les mêmes clés dans chaque fichier de langue, activez le pack de ressources, puis récupérez leur valeur à l’aide de l’espace réservé [**Localiser le texte**](/placeholders#localize-text).

# Localiser les images et les éléments

Utilisez la condition [**La langue du jeu est**](/conditions#is-game-language) pour afficher différents éléments ou mises en page selon les codes de langue, tels que `en_us` et `de_de`.
