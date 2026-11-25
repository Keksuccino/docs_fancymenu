---
title: Ressources
description: >-
  Fonctionnement des ressources dans FancyMenu. Présentation des emplacements de
  ressources, des ressources locales et des ressources Web.
sourceBlobSha: eb783aaa0098ba295b3ebaf941bb4723e4d08970
---

# Ressources

Les champs de ressource peuvent charger du contenu depuis :

- **Minecraft :** un emplacement de ressource fourni par Minecraft ou un pack de ressources.
- **Local :** un fichier de l’instance de jeu active.
- **Web :** l’URL directe d’un fichier.

La plupart des champs d’image, d’audio, de vidéo et de texte utilisent le même sélecteur de ressources. Celui-ci inclut un navigateur pour le contenu de Minecraft et des packs de ressources.

# Ressources Minecraft (packs de ressources)

Les emplacements de ressources utilisent le format `namespace:path`. L’espace de noms correspond au dossier situé immédiatement sous `assets`, et le chemin correspond à tout ce qui se trouve sous cet espace de noms.

Par exemple, imaginons une image de pack de ressources stockée dans `/assets/custom_resources/images/image.png`.
Son emplacement de ressource est `custom_resources:images/image.png`.

> [!NOTE]
> Les ressources intégrées de Minecraft utilisent généralement l’espace de noms `minecraft`.

# Ressources locales

Stockez les ressources locales dans `<game-directory>/config/fancymenu/assets/`. `<game-directory>` correspond au dossier de l’instance active, qui peut être différent de `.minecraft`.

Les champs de ressource peuvent afficher le même chemin sous la forme `/config/fancymenu/assets/example.png`. Dans ces champs, le `/` initial désigne toujours `<game-directory>` ; il ne s’agit pas du chemin racine du système de fichiers.

Ces fichiers peuvent être [fournis avec un modpack](/modpacks) via son dossier de configuration.

Pour consulter la liste complète des chemins d’organisation, de ressources, de configuration et d’état généré de FancyMenu, voir [Emplacements de stockage des données](/data-storage-locations).

# Ressources Web

Utilisez l’URL directe du fichier, par exemple `https://example-domain.net/image.png`. Les pages et les liens de redirection sont plus lents et risquent davantage d’échouer que les URL directes se terminant par le nom et l’extension de la ressource.

# Espaces réservés dans les sources des ressources

Les champs de ressource utilisant un sélecteur peuvent contenir des [espaces réservés](/placeholders) dans les chemins locaux, les URL et les emplacements de ressources Minecraft. Sélectionnez **Ouvrir dans l’éditeur** à côté du champ source pour le modifier directement.

> [!WARNING]
> Les champs de ressource qui n’utilisent pas le sélecteur habituel peuvent ne pas prendre en charge les espaces réservés ni les mises à jour de la source en temps réel.
