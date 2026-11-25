---
title: Vidéos (MP4)
description: Ce qu’il faut savoir sur l’utilisation des vidéos dans FancyMenu.
sourceBlobSha: bd34c5c21a6c08d6b66a7b2acdaf9bd12739732f
---
# Vidéos

FancyMenu prend en charge la lecture de vidéos MP4 en tant qu’[éléments](/elements#video), [arrière-plans de menu](/menu-backgrounds#video) et contenu d’[intro du jeu](/game-intro).

L’élément natif [**Video**](/elements#video) et l’arrière-plan de menu **Video** utilisent Watermedia V3. Les anciens types **Video [Rinku]** sont obsolètes et ne devraient être conservés que dans les mises en page qui en ont encore besoin.

Les [actions](/action-scripts) suivantes permettent également de contrôler les arrière-plans vidéo et les éléments vidéo :

- [**Set Video Element Volume**](/action-scripts#set-video-element-volume) définit le volume d’un élément Video.
- [**Set Video Element Play Time**](/action-scripts#set-video-element-play-time) place la lecture d’un élément Video à un horodatage en millisecondes.
- [**Toggle Video Element Paused State**](/action-scripts#toggle-video-element-paused-state) active ou désactive la pause d’un élément Video.
- [**Set Video Background Volume**](/action-scripts#set-video-background-volume) définit le volume d’un arrière-plan de menu Video.
- [**Set Video Background Play Time**](/action-scripts#set-video-background-play-time) place la lecture d’un arrière-plan de menu Video à un horodatage en millisecondes.
- [**Toggle Video Background Paused State**](/action-scripts#toggle-video-background-paused-state) active ou désactive la pause d’un arrière-plan de menu Video.

Les [placeholders](/placeholders) suivants permettent d’obtenir des informations sur les arrière-plans vidéo et les éléments vidéo :

- [**Video Element Volume**](/placeholders#video-element-volume) renvoie le volume d’un élément Video.
- [**Video Element Duration**](/placeholders#video-element-duration) renvoie la durée d’un élément Video.
- [**Video Element Play Time**](/placeholders#video-element-play-time) renvoie la progression actuelle d’un élément Video.
- [**Video Element Paused State**](/placeholders#video-element-paused-state) indique si un élément Video est en pause.
- [**Video Background Volume**](/placeholders#video-background-volume) renvoie le volume d’un arrière-plan de menu Video.
- [**Video Background Duration**](/placeholders#video-background-duration) renvoie la durée d’un arrière-plan de menu Video.
- [**Video Background Play Time**](/placeholders#video-background-play-time) renvoie la progression actuelle d’un arrière-plan de menu Video.
- [**Video Background Paused State**](/placeholders#video-background-paused-state) indique si un arrière-plan de menu Video est en pause.

Par défaut, les placeholders de durée et de temps de lecture renvoient une valeur au format `MM:SS`. Définissez `output_as_timestamp` sur `true` pour obtenir des horodatages en millisecondes. Les placeholders de temps de lecture peuvent toujours utiliser `show_percentage` pour renvoyer une progression de 0 à 100.

Les valeurs de volume et d’état de pause sont des métadonnées du contrôleur associées à l’identifiant. Les valeurs de durée et de temps de lecture nécessitent que l’élément Video ou l’arrière-plan correspondant soit actif et prêt sur l’écran actuel.

Le [listener **Video Playback Status Changed**](/listeners#video-playback-status-changed) peut réagir aux états `PLAYING`, `PAUSED`, `STOPPED` et `FINISHED`.

## Prérequis

Pour utiliser le nouvel élément Video natif et le nouveau type d’arrière-plan de menu, vous devez installer :

- **Watermedia V3**
- **Watermedia Binaries V3**

Ces dépendances étant facultatives, vous devez les ajouter manuellement à l’instance si vous souhaitez prendre en charge les vidéos.

La lecture vidéo native nécessite également un moteur de rendu OpenGL. Watermedia ne permet pas la lecture lorsque Minecraft utilise Vulkan. Passez à OpenGL pour utiliser les éléments Video, les arrière-plans de menu Video et les [intros vidéo du jeu](/game-intro).

Le type obsolète **Video [Rinku]** utilise toujours [Rinku](https://modrinth.com/mod/rinku). Pour les nouvelles mises en page, utilisez plutôt le type Video natif basé sur Watermedia.

## Vidéos dans les écrans de chargement

La prise en charge des vidéos ne fonctionne PAS dans les écrans de chargement (écrans de chargement du jeu/des ressources et du monde).

Cela signifie également que vous ne devez PAS ajouter de vidéos à l’écran de chargement du jeu via **Drippy Loading Screen**, car cela ne fonctionnera pas dans la plupart des cas.

Utilisez plutôt des [animations](/animations) courtes et simples (APNG ou GIF) dans les écrans de chargement.

## Dépannage

Si la vidéo native ne se lance pas, vérifiez que Watermedia V3 et Watermedia Binaries V3 sont compatibles avec votre version de Minecraft/du modloader et que Minecraft utilise OpenGL plutôt que Vulkan.
