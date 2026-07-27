---
title: Localisation des dispositions
description: Localisez le texte et les autres contenus de la disposition.
---

# Localisation des dispositions

Utilisez l’[espace réservé **Localize Text**](./placeholders#localize-text-local) pour le texte traduisible :

```text
{"placeholder":"local","values":{"key":"modpack.menu.play"}}
```

FancyMenu commence par vérifier les données de langue actives de Minecraft. Si la clé n’y est pas présente, il vérifie les fichiers de localisation personnalisés de FancyMenu. Si aucune des deux sources ne contient la clé, celle-ci est affichée telle quelle.

# Fichiers de localisation personnalisés de FancyMenu

Placez les fichiers ci-dessous :

```text
<game-directory>/config/fancymenu/custom_locals/
```

Créez un sous-dossier pour vos fichiers de localisation :

```text
custom_locals/
└── my_pack/
    └── text.json
```

Placez les fichiers de localisation dans au moins un sous-dossier de `custom_locals` ; les fichiers placés directement à la racine de `custom_locals` ne sont pas chargés. Les sous-dossiers imbriqués sont pris en charge.

Formats UTF-8 pris en charge :

| Extension | Format |
|---|---|
| `.json` | Objet JSON ; les objets imbriqués deviennent des clés séparées par des points |
| `.lang` | Lignes `key=value` |
| `.properties` | Syntaxe des propriétés Java |

Exemple JSON :

```json
{
  "modpack": {
    "menu": {
      "play": "Jouer"
    }
  }
}
```

Cela définit `modpack.menu.play`.

FancyMenu regroupe les fichiers pris en charge de ces sous-dossiers en un seul dictionnaire de localisation personnalisé. Utilisez chaque clé dans un seul fichier. Les fichiers de localisation personnalisés ne changent pas en fonction de la langue sélectionnée dans Minecraft ; utilisez la méthode du pack de ressources ci-dessous lorsque vous avez besoin d’un changement de langue automatique.

Redémarrez le client après avoir modifié les fichiers de localisation personnalisés.

# Texte spécifique à la langue

Pour un changement automatique en fonction de la langue sélectionnée dans Minecraft, fournissez des fichiers de langue Minecraft classiques via un [pack de ressources](./resources#minecraft-resources-resource-packs) :

```text
assets/<namespace>/lang/en_us.json
assets/<namespace>/lang/de_de.json
```

Utilisez les mêmes clés dans chaque fichier de langue, activez le pack de ressources, puis lisez-les avec l’[espace réservé **Localize Text**](./placeholders#localize-text-local).

# Localisation des images et des éléments

Utilisez l’[exigence **Is Game Language**](./conditions#is-game-language-fancymenu_loading_requirement_is_language) pour afficher différents éléments ou dispositions selon les codes de langue, comme `en_us` et `de_de`.
