---
title: Vidéos (MP4)
description: Ce qu’il faut savoir sur l’utilisation des vidéos dans FancyMenu.
---
# Vidéos

FancyMenu prend en charge la lecture de vidéos MP4 comme [éléments](./elements#video), [arrière-plans de menu](./menu-backgrounds) et contenu de [Game Intro](./game-intro).

Le [**Video** élément](./elements#video) natif et l’arrière-plan de menu **Video** utilisent Watermedia V3. Les anciens types **Video [MCEF]** sont obsolètes et ne devraient rester que dans les configurations qui en ont encore besoin.

Il existe également les **actions** suivantes pour contrôler les arrière-plans vidéo et les éléments vidéo :

- [**Set Video Element Volume**](./action-scripts#set-video-element-volume-set_video_element_volume) définit le volume d’un élément Video.
- [**Set Video Element Play Time**](./action-scripts#set-video-element-play-time-set_video_element_play_time) place un élément Video à un horodatage en millisecondes.
- [**Toggle Video Element Paused State**](./action-scripts#toggle-video-element-paused-state-toggle_video_element_pause_state) bascule l’état de pause d’un élément Video.
- [**Set Video Background Volume**](./action-scripts#set-video-background-volume-set_video_menu_background_volume) définit le volume d’un arrière-plan de menu Video.
- [**Set Video Background Play Time**](./action-scripts#set-video-background-play-time-set_video_menu_background_play_time) place un arrière-plan de menu Video à un horodatage en millisecondes.
- [**Toggle Video Background Paused State**](./action-scripts#toggle-video-background-paused-state-toggle_video_menu_background_pause_state) bascule l’état de pause d’un arrière-plan de menu Video.

Et les **placeholders** suivants pour obtenir des informations sur les arrière-plans et éléments vidéo :

- [**Video Element Volume**](./placeholders#video-element-volume-video_element_vol) renvoie le volume d’un élément Video.
- [**Video Element Duration**](./placeholders#video-element-duration-video_element_duration) renvoie la durée d’un élément Video.
- [**Video Element Play Time**](./placeholders#video-element-play-time-video_element_playtime) renvoie la progression actuelle d’un élément Video.
- [**Video Element Paused State**](./placeholders#video-element-paused-state-video_element_paused_state) renvoie si un élément Video est en pause.
- [**Video Background Volume**](./placeholders#video-background-volume-video_background_vol) renvoie le volume d’un arrière-plan de menu Video.
- [**Video Background Duration**](./placeholders#video-background-duration-video_background_duration) renvoie la durée d’un arrière-plan de menu Video.
- [**Video Background Play Time**](./placeholders#video-background-play-time-video_background_playtime) renvoie la progression actuelle d’un arrière-plan de menu Video.
- [**Video Background Paused State**](./placeholders#video-background-paused-state-video_background_paused_state) renvoie si un arrière-plan de menu Video est en pause.

Les placeholders de durée et de temps de lecture renvoient par défaut `MM:SS`. Définissez `output_as_timestamp` sur `true` lorsque vous avez besoin d’horodatages en millisecondes. Les placeholders de temps de lecture peuvent toujours utiliser `show_percentage` pour des valeurs de progression de 0 à 100.

Les valeurs de volume et d’état de pause sont des métadonnées du contrôleur associées à l’identifiant. Les valeurs de durée et de temps de lecture nécessitent que l’élément Video ou l’arrière-plan correspondant soit actif et prêt sur l’écran actuel.

Le [**On Video Playback Status Changed** listener](./listeners#on-video-playback-status-changed-video_playback_status_changed) peut réagir à `PLAYING`, `PAUSED`, `STOPPED` et `FINISHED`.

## Exigences

Pour utiliser le nouvel élément Video natif et le type d’arrière-plan de menu, vous devez installer :

- **Watermedia V3**
- **Watermedia Binaries V3**

Ce sont des dépendances facultatives, elles doivent donc être ajoutées manuellement à l’instance si vous souhaitez prendre en charge les vidéos.

La lecture vidéo native nécessite également un rendu OpenGL. La lecture via Watermedia n’est pas disponible lorsque Minecraft utilise Vulkan ; passez à OpenGL pour utiliser les éléments Video, les arrière-plans de menu Video et les [Game Intros vidéo](./game-intro).

Le type obsolète **Video [MCEF]** utilise encore MCEF. Pour les nouvelles configurations, utilisez plutôt le type Video natif propulsé par Watermedia.

## Vidéos dans les écrans de chargement

La prise en charge des vidéos ne fonctionne PAS dans les écrans de chargement (écran de chargement du jeu/des ressources et écran de chargement du monde).

Cela signifie également que vous ne devez PAS ajouter de vidéos à l’écran de chargement du jeu via **Drippy Loading Screen**, car cela ne fonctionnera pas dans la plupart des cas.

Utilisez plutôt de courtes animations simples [AFMA/FMA](./fma) dans les écrans de chargement.

## Dépannage

Si la vidéo native ne se lance pas, vérifiez que Watermedia V3 et Watermedia Binaries V3 correspondent à votre version de Minecraft/modloader et que Minecraft utilise OpenGL au lieu de Vulkan.
