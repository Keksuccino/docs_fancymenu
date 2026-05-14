---
title: Dragger
description: >-
  Comment faire glisser des éléments dans les menus à l’aide de l’élément
  Dragger.
---

# Dragger

L’élément Dragger est un élément de FancyMenu qui vous permet de rendre les menus interactifs d’une manière plutôt inhabituelle. Le Dragger est un élément que l’on peut faire glisser avec la souris EN DEHORS de l’éditeur, ce qui signifie que les utilisateurs peuvent simplement saisir l’élément et le déplacer.

C’est sympa, mais déplacer un élément qui ne fait rien d’autre, c’est assez inutile, non ? Eh bien non, parce que vous pouvez lui attacher d’autres éléments en définissant l’élément Dragger comme point d’ancrage pour les autres éléments qui doivent se déplacer avec lui.

Le décalage de position des éléments Dragger est persistant et est enregistré entre les redémarrages du jeu, ce qui signifie simplement que lorsque l’utilisateur déplace le Dragger, il reste à cette position « personnalisée », même après avoir redémarré le jeu.

L’élément Dragger n’est visible que dans l’éditeur et invisible en dehors, alors assurez-vous d’utiliser un autre élément comme « corps » si vous voulez que l’utilisateur voie où se trouve la zone de glissement.
