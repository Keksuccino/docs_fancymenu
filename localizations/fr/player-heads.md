---
title: Têtes de joueur
description: Comment afficher la tête d’un joueur en image 2D ou 3D dans un menu.
---

# Têtes de joueur dans les menus

Pour afficher la tête d’un joueur en image 2D ou 3D à l’aide d’un élément Image, vous pouvez utiliser une API web tierce appelée « Minotar ».

## Image 2D

### 1. Ajouter un élément Image

Dans l’éditeur FancyMenu, faites un clic droit sur l’arrière-plan, sélectionnez « New Element », puis choisissez « Image » (ou « Picture »).

### 2. Définir la source Web

Faites un clic droit sur l’élément Image pour accéder à ses propriétés. Pour le type de source, sélectionnez « Web ».

### 3. Construire l’URL avec le bon placeholder

Dans le champ « Source », saisissez l’URL suivante :
`https://minotar.net/avatar/{"placeholder":"playername"}.png`

FancyMenu utilisera `{"placeholder":"playername"}` pour insérer dynamiquement le nom d’utilisateur actuel du joueur dans l’URL, ce qui permet à l’élément Image de récupérer et d’afficher sa tête depuis Minotar.

## Image 3D

C’est assez similaire à la version 2D, mais ici nous devons utiliser une URL différente :

`https://minotar.net/cube/{"placeholder":"playername"}/200.png`

Le `200` correspond à la taille en pixels dans ce cas. Donc si vous voulez une version plus petite, remplacez-le simplement par `100`, par exemple. Pour une version plus grande, utilisez `300`, et ainsi de suite.
