---
title: Ressources
description: >-
  Comment fonctionnent les ressources dans FancyMenu. Couvre les emplacements
  des ressources, les ressources locales et les ressources web.
---

# Ressources

Les champs de ressource peuvent charger du contenu depuis :

- **Minecraft :** un emplacement de ressource fourni par Minecraft ou par un pack de ressources.
- **Local :** un fichier dans l’instance de jeu active.
- **Web :** une URL directe vers un fichier.

La plupart des champs d’image, d’audio, de vidéo et de texte utilisent le même sélecteur de ressources. Le sélecteur inclut un navigateur pour le contenu Minecraft et celui des packs de ressources.

# Ressources Minecraft (packs de ressources)

Les emplacements de ressource utilisent le format `namespace:path`. Le namespace est le dossier situé juste sous `assets`, et le chemin correspond à tout ce qui se trouve en dessous de ce namespace.

Par exemple, prenons une image de pack de ressources stockée à `/assets/custom_resources/images/image.png`.
Son emplacement de ressource est `custom_resources:images/image.png`.

> [!NOTE]
> Les ressources intégrées de Minecraft utilisent normalement le namespace `minecraft`.

# Ressources locales

Stockez les ressources locales dans `<game-directory>/config/fancymenu/assets/`. `<game-directory>` est le dossier de l’instance active, qui peut être différent de `.minecraft`.

Les champs de ressource peuvent afficher le même chemin que `/config/fancymenu/assets/example.png`. Dans ces champs, le `/` initial signifie toujours `<game-directory>` ; ce n’est pas un chemin racine du système de fichiers.

Ces fichiers peuvent être [inclus avec un modpack](./modpacks) via son dossier de configuration.

Pour une carte complète des chemins de FancyMenu pour la disposition, les ressources, la configuration et l’état généré, voir [Emplacements de stockage des données](./data-storage-locations).

# Ressources web

Utilisez une URL directe vers le fichier, par exemple `https://example-domain.net/image.png`. Les pages et les liens de redirection sont plus lents et risquent davantage d’échouer que les URL directes se terminant par le nom et l’extension de la ressource.

# Placeholders dans les sources de ressources

Les champs de ressource basés sur un sélecteur peuvent utiliser des [placeholders](./placeholders) dans les chemins locaux, les URL et les emplacements de ressources Minecraft. Sélectionnez **Ouvrir dans l’éditeur** à côté du champ source pour le modifier directement.

> [!WARNING]
> Les entrées de ressource qui n’utilisent pas le sélecteur normal peuvent ne pas prendre en charge les placeholders ou les mises à jour en direct de la source.
