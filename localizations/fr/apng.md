---
title: APNG
description: Comment créer des images APNG compatibles avec FancyMenu.
---

# Images PNG animées

> [!NOTE]
> Pour les animations longues ou complexes, privilégiez les [fichiers AFMA](./fma). Watermedia V3 et Watermedia Binaries V3 peuvent accélérer le décodage des APNG/GIF lorsqu’ils sont disponibles, mais AFMA reste le format d’animation FancyMenu recommandé.


Les APNG sont une version animée des images PNG, ce qui permet d’avoir les mêmes fonctionnalités qu’un GIF, mais avec la qualité PNG complète et sans perte !

FancyMenu prend en charge les APNG nativement, mais il est un peu pointilleux sur les APNG acceptés.
Il faut des APNG **non compressés** et **non entrelacés**.

# Créer des animations APNG

Vous seriez surpris de voir à quel point il est difficile de trouver un bon éditeur APNG, surtout avec des options pour désactiver la compression et l’entrelacement.

Un excellent choix d’éditeur est [ScreenToGif](https://www.screentogif.com/), qui est en réalité un outil pour enregistrer des GIF et des APNG de votre écran, mais il est aussi parfait pour créer des APNG classiques en ignorant la partie enregistrement et en chargeant directement les images dans l’éditeur !

## Ouvrir l’éditeur

La première chose que vous voyez après avoir ouvert [ScreenToGif](https://www.screentogif.com/) est cet écran. Cliquez ici sur **Editor**.

![screentogif_2](https://github.com/Keksuccino/FancyMenu/assets/35544624/a8d34313-b841-4fb6-bf3a-ff02c39792cb)

## Charger les images

Vous avez maintenant besoin de vos images PNG. Glissez-déposez-les dans l’éditeur.

![screentogif_dragndrop](https://github.com/Keksuccino/FancyMenu/assets/35544624/ba4ad4a5-484e-46f1-8efd-90ba764462d8)

## Délai entre les images

Pour configurer le délai entre les images, sélectionnez la ou les images que vous voulez modifier, passez à l’onglet **Edit** et, dans la section **Delay (Duration)**, cliquez sur **Override**.

![screentogif_delay](https://github.com/Keksuccino/FancyMenu/assets/35544624/a5d93139-3192-4090-b243-e5c0fe299963)

## Boucle

Le comportement de la boucle peut être configuré dans le menu **Save As**. Consultez l’étape suivante pour savoir comment ouvrir ce menu.

## Exporter l’APNG

Vous êtes maintenant prêt à revenir à l’onglet **File** pour cliquer sur **Save As**.

Dans le menu d’enregistrement, assurez-vous de :
- Définir le type de fichier sur **APNG** (premier paramètre, il peut être nécessaire de faire défiler le menu vers le haut)
- Désactiver **Detect Unchanged Pixels**

> [!NOTE]
> Vous pouvez également configurer le **comportement de boucle** dans ce menu ! Désactiver **Looped Apng** empêchera l’APNG de boucler, et si vous l’activez, vous pourrez choisir entre un nombre précis de boucles ou une boucle infinie.

![screentogif_save](https://github.com/Keksuccino/FancyMenu/assets/35544624/954353da-45ed-4df8-9f06-c78a0a469fc8)

## Utiliser l’APNG dans FancyMenu

Copiez maintenant votre fichier APNG dans `<game-directory>/config/fancymenu/assets/`. Vous pourrez ensuite l’utiliser pour presque tout ce qui accepte des images.

> [!WARNING]
> Il est **très important** que le nom du fichier APNG se termine par `.apng` !
> FancyMenu ne pourra pas identifier l’image comme APNG si son nom ne se termine pas par `.apng`.

![screentogif_use_apng](https://github.com/Keksuccino/FancyMenu/assets/35544624/2322da62-4013-451e-9a8b-3df0bf92df54)
