---
title: Vidéos (MP4)
description: Ce qu’il faut savoir sur l’utilisation des vidéos dans FancyMenu.
---
# Vidéos

FancyMenu prend en charge la lecture de vidéos MP4 en tant qu’[éléments](./elements#video), de [fonds de menu](./menu-backgrounds) et de contenu [Game Intro](./game-intro).

L’[**élément Vidéo**](./elements#video) natif et le fond de menu **Video** utilisent Watermedia V3. Les anciens types **Video [Rinku]** sont obsolètes et ne devraient rester que dans les configurations qui en ont encore besoin.

Il existe également les **actions** suivantes pour contrôler les fonds vidéo et les éléments vidéo :

- [**Set Video Element Volume**](./action-scripts#set-video-element-volume-set_video_element_volume) règle le volume d’un élément Vidéo.
- [**Set Video Element Play Time**](./action-scripts#set-video-element-play-time-set_video_element_play_time) déplace un élément Vidéo à un horodatage en millisecondes.
- [**Toggle Video Element Paused State**](./action-scripts#toggle-video-element-paused-state-toggle_video_element_pause_state) bascule l’état en pause d’un élément Vidéo.
- [**Set Video Background Volume**](./action-scripts#set-video-background-volume-set_video_menu_background_volume) règle le volume d’un fond de menu Vidéo.
- [**Set Video Background Play Time**](./action-scripts#set-video-background-play-time-set_video_menu_background_play_time) déplace un fond de menu Vidéo à un horodatage en millisecondes.
- [**Toggle Video Background Paused State**](./action-scripts#toggle-video-background-paused-state-toggle_video_menu_background_pause_state) bascule l’état en pause d’un fond de menu Vidéo.

Et les **placeholders** suivants pour obtenir des informations sur les fonds et éléments vidéo :

- [**Video Element Volume**](./placeholders#video-element-volume-video_element_vol) renvoie le volume d’un élément Vidéo.
- [**Video Element Duration**](./placeholders#video-element-duration-video_element_duration) renvoie la durée d’un élément Vidéo.
- [**Video Element Play Time**](./placeholders#video-element-play-time-video_element_playtime) renvoie la progression actuelle d’un élément Vidéo.
- [**Video Element Paused State**](./placeholders#video-element-paused-state-video_element_paused_state) renvoie si un élément Vidéo est en pause.
- [**Video Background Volume**](./placeholders#video-background-volume-video_background_vol) renvoie le volume d’un fond de menu Vidéo.
- [**Video Background Duration**](./placeholders#video-background-duration-video_background_duration) renvoie la durée d’un fond de menu Vidéo.
- [**Video Background Play Time**](./placeholders#video-background-play-time-video_background_playtime) renvoie la progression actuelle d’un fond de menu Vidéo.
- [**Video Background Paused State**](./placeholders#video-background-paused-state-video_background_paused_state) renvoie si un fond de menu Vidéo est en pause.

Les placeholders de durée et de temps de lecture renvoient `MM:SS` par défaut. Définissez `output_as_timestamp` sur `true` lorsque vous avez besoin d’horodatages en millisecondes. Les placeholders de temps de lecture peuvent toujours utiliser `show_percentage` pour obtenir des valeurs de progression de 0 à 100.

Les valeurs de volume et d’état de pause sont des métadonnées du contrôleur associées à l’identifiant. Les valeurs de durée et de temps de lecture nécessitent que l’élément Vidéo ou le fond correspondant soit actif et prêt sur l’écran actuel.

Le [**listener On Video Playback Status Changed**](./listeners#on-video-playback-status-changed-video_playback_status_changed) peut réagir à `PLAYING`, `PAUSED`, `STOPPED` et `FINISHED`.

## Prérequis

Pour utiliser le nouvel élément Vidéo natif et le type de fond de menu, vous devez installer :

- **Watermedia V3**
- **Watermedia Binaries V3**

Il s’agit de dépendances facultatives, elles doivent donc être ajoutées manuellement à l’instance si vous চানtez la prise en charge des vidéos.

La lecture vidéo native nécessite également un rendu OpenGL. La lecture via Watermedia n’est pas disponible lorsque Minecraft utilise Vulkan ; passez à OpenGL pour utiliser les éléments Vidéo, les fonds de menu Vidéo et les [Game Intros vidéo](./game-intro).

Le type obsolète **Video [Rinku]** utilise toujours [Rinku](https://modrinth.com/mod/rinku). Pour les nouvelles configurations, utilisez plutôt le type Vidéo natif propulsé par Watermedia.

## Vidéos dans les écrans de chargement

La prise en charge des vidéos ne fonctionne PAS dans les écrans de chargement (écran de chargement du jeu/ressources et écran de chargement du monde).

Cela signifie également que vous ne devez PAS ajouter de vidéos à l’écran de chargement du jeu via **Drippy Loading Screen**, car cela ne fonctionnera pas dans la plupart des cas.

Utilisez plutôt de courtes animations [AFMA/FMA](./fma) simples dans les écrans de chargement.

## Dépannage

Si la vidéo native ne se lance pas, vérifiez que Watermedia V3 et Watermedia Binaries V3 correspondent à votre version de Minecraft/modloader et que Minecraft utilise OpenGL au lieu de Vulkan.
