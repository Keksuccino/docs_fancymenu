---
title: Vidéos (MP4)
description: Ce qu’il faut savoir sur l’utilisation des vidéos dans FancyMenu.
---

# Vidéos

FancyMenu prend en charge la lecture de vidéos MP4 comme éléments, arrière-plans de menus et contenu de Game Intro.

FancyMenu 3.9.0 ajoute un nouvel élément natif **Vidéo** et un nouvel arrière-plan de menu **Vidéo** propulsés par Watermedia V3. L’ancien type d’élément/arrière-plan **Video [MCEF]** est obsolète et ne devrait être conservé que pour les anciens agencements qui en ont encore besoin.

Il existe également les **actions** suivantes pour contrôler les arrière-plans vidéo et les éléments vidéo :

- **Set Video Element Volume** pour définir le volume d’un élément vidéo
- **Set Video Element Play Time** pour positionner un élément vidéo à un horodatage en millisecondes
- **Toggle Video Element Paused State** pour basculer l’état en pause d’un élément vidéo
- **Set Video Background Volume** pour définir le volume d’un arrière-plan de menu vidéo
- **Set Video Background Play Time** pour positionner un arrière-plan de menu vidéo à un horodatage en millisecondes
- **Toggle Video Background Paused State** pour basculer l’état en pause d’un arrière-plan de menu vidéo

Et les **placeholders** suivants pour obtenir des informations sur les arrière-plans vidéo et les éléments vidéo :

- **Video Element Volume** pour obtenir le volume d’un élément vidéo
- **Video Element Duration** pour obtenir la durée d’un élément vidéo
- **Video Element Play Time** pour obtenir le temps de lecture actuel (progression) d’un élément vidéo
- **Video Element Paused State** pour obtenir l’état en pause (true/false) d’un élément vidéo
- **Video Background Volume** pour obtenir le volume d’un arrière-plan de menu vidéo
- **Video Background Duration** pour obtenir la durée d’un arrière-plan de menu vidéo
- **Video Background Play Time** pour obtenir le temps de lecture actuel (progression) d’un arrière-plan de menu vidéo
- **Video Background Paused State** pour obtenir l’état en pause (true/false) d’un arrière-plan de menu vidéo

Les placeholders de durée et de temps de lecture renvoient `MM:SS` par défaut. Définissez `output_as_timestamp` sur `true` lorsque vous avez besoin d’horodatages en millisecondes. Les placeholders de temps de lecture peuvent toujours utiliser `show_percentage` pour obtenir des valeurs de progression de 0 à 100.

FancyMenu 3.9.0 ajoute également le listener **On Video Playback Status Changed**, qui peut réagir à `PLAYING`, `PAUSED`, `STOPPED` et `FINISHED`.

## Conditions requises

Pour utiliser le nouveau type natif d’élément Vidéo et d’arrière-plan de menu, vous devez installer :

- **Watermedia V3**
- **Watermedia Binaries V3**

Ce sont des dépendances optionnelles, elles doivent donc être ajoutées manuellement à l’instance si vous voulez prendre en charge les vidéos.

Le type obsolète **Video [MCEF]** utilise toujours MCEF. Pour les nouveaux agencements, utilisez plutôt le type Vidéo natif basé sur Watermedia.

## Vidéos dans les écrans de chargement

La prise en charge des vidéos ne fonctionne PAS dans les écrans de chargement (écran de chargement du jeu/des ressources et écran de chargement du monde).

Cela signifie aussi que vous ne devez PAS ajouter de vidéos à l’écran de chargement du jeu via **Drippy Loading Screen**, car cela ne fonctionnera pas dans la plupart des cas.

Vous devriez plutôt utiliser de courts fichiers AFMA/FMA simples dans les écrans de chargement, car les utilisateurs ne remarquent généralement pas qu’ils sont rechargés lorsque l’animation est assez simple et assez courte.

## Dépannage

Si vous rencontrez des problèmes avec la prise en charge native des vidéos, vérifiez d’abord que Watermedia V3 et Watermedia Binaries V3 sont tous deux installés et correspondent à votre version de Minecraft/de votre modloader.
