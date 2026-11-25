---
title: Zones défilantes
description: >-
  Comment ajouter des éléments à une zone défilante, les organiser et modifier
  le défilement de la zone.
sourceBlobSha: a424c5e8680ece5f25846de0399fc8e78f375e15
---
# Zones défilantes

Une **zone défilante** contient d'autres éléments et permet aux joueurs de les faire défiler. Elle est idéale pour les longues listes de boutons, les sélecteurs de mondes ou de serveurs, les présentations d'objets, les panneaux d'actualités et tout ce qui ne tient pas sur un seul écran.

Tout ce qui se trouve dans la zone défile avec elle et est coupé au niveau de ses bords.

<img width="800" alt="Ajouter des boutons à une zone défilante et les empiler" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/scroll_area_showcase.gif?raw=true">

> [!NOTE]
> Seuls les éléments que vous avez ajoutés à la disposition peuvent être placés dans une zone. Les [éléments Vanilla](/vanilla-elements) ne le peuvent pas, car ils appartiennent au menu lui-même.

# Ajouter une zone défilante

1. Ouvrez une disposition dans l'éditeur de dispositions.
2. Faites un clic droit sur l'arrière-plan de l'éditeur, puis sélectionnez **Nouvel élément -> Zone défilante**.
3. Faites glisser des éléments dans la zone.

# Ajouter ou retirer des éléments

- Faites glisser un élément sur la zone pour l'y ajouter. La zone s'illumine lorsqu'elle accepte l'élément. Pour qu'un élément y soit ajouté, une partie de celui-ci doit se trouver dans la zone.
- Pour faire glisser plusieurs éléments sélectionnés à la fois, maintenez la touche `Ctrl` (`Cmd` sur macOS) enfoncée lorsque vous commencez à les faire glisser.
- Lorsque vous faites glisser un élément près du bord de la zone, celle-ci défile pour vous permettre d'accéder à toutes ses parties. Vous pouvez également la faire défiler avec la molette de la souris dans l'éditeur.
- Pour retirer un élément, faites-le glisser hors de la zone ou faites un clic droit dessus et sélectionnez **Sortir de la zone défilante**. Il reste à sa place à l'écran.
- Les zones peuvent également être placées dans d'autres zones.

## Calques

Dans le widget [Calques](/layout-editor#scrollable-areas), les éléments d'une zone apparaissent sous celle-ci. Faites glisser les calques dans ce widget pour ajouter ou retirer des éléments d'une zone, ou pour modifier leur ordre. Le bouton de réduction du calque d'une zone masque ses éléments dans la liste.

## Copier et supprimer

- Copier une zone copie également tout ce qu'elle contient.
- Si vous supprimez une zone qui contient encore des éléments, vous devez choisir quoi en faire : **Supprimer les éléments** les supprime également, tandis que **Conserver les éléments** les laisse à leur place à l'écran.

# Organiser les éléments

Faites un clic droit sur la zone, puis ouvrez **Organisation**. **Mode** définit la façon dont la zone positionne ses éléments :

- **Ancrages** : vous placez les éléments vous-même, comme dans le reste de la disposition. Les nouvelles zones utilisent ce mode.
- **Pile** : les éléments s'alignent les uns après les autres.
- **Grille** : les éléments s'alignent dans des cellules de même taille.
- **Flux** : les éléments s'alignent les uns à côté des autres et passent à la ligne suivante lorsque la ligne est pleine.

<img width="800" alt="Zones défilantes en modes Pile, Grille et Flux" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/scroll_area_modes.png?raw=true">

## Mode Ancrages

Les éléments d'une zone ont leurs propres ancrages, qui se rapportent au contenu de la zone plutôt qu'à l'écran. Par exemple, l'ancrage **Coin supérieur gauche** correspond au coin supérieur gauche du contenu, et les ancrages du bas se fixent à la fin du contenu. Consultez la page [Positionner des éléments](/positioning-elements) pour en savoir plus sur le fonctionnement des ancrages.

- **Étirer horizontalement** et **Étirer verticalement** ajustent la largeur ou la hauteur d'un élément à celle du contenu.
- Les éléments ne peuvent être ancrés qu'à d'autres éléments de la même zone. Lorsque vous déplacez un élément vers une zone ou hors de celle-ci, les éléments qui étaient ancrés de l'autre côté du bord de la zone adoptent l'ancrage **Coin supérieur gauche** et restent à leur place.

### Taille du contenu

En mode Ancrages, vous choisissez la taille du contenu, ce qui détermine la distance de défilement de la zone.

Sélectionnez la zone et faites glisser la poignée située à l'extrémité de son contenu. Faites-la glisser au-delà du bord de la zone pour continuer : la zone défile en même temps.

<img width="698" alt="Poignée de contenu d'une zone défilante sélectionnée" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/scroll_area_content_handle.png?raw=true">

Vous pouvez également faire un clic droit sur la zone, puis ouvrir **Taille du contenu** :

- **Largeur du contenu** et **Hauteur du contenu** définissent la taille sous forme de valeur numérique. Elles prennent en charge les [espaces réservés](/placeholders). Si vous utilisez un espace réservé, vous ne pouvez pas faire glisser la poignée.
- **Ajuster au contenu** fait terminer le contenu exactement à la fin de son dernier élément. Les éléments ancrés au milieu ou à l'extrémité du contenu se déplacent avec celui-ci et ne sont donc pas pris en compte.

Le contenu n'est jamais plus petit que la zone et ne s'agrandit que dans les directions où la zone défile.

## Modes Pile, Grille et Flux

- La zone positionne les éléments pour vous et le contenu s'agrandit automatiquement en fonction de ceux-ci.
- Faites glisser un élément pour modifier l'ordre. Une ligne indique son nouvel emplacement.
- Lorsque vous passez du mode Ancrages à l'un de ces modes, les éléments conservent l'ordre qu'ils avaient à l'écran. Si vous repassez en mode Ancrages, chaque élément reste à sa place.
- Les éléments masqués par leurs [conditions](/conditions) ne laissent aucun espace vide.
- L'étirement ne fonctionne pas dans ces modes.
- Ces modes ne permettent de défiler que dans une seule direction. Une zone réglée sur **Les deux** défile verticalement.

Ouvrez **Organisation** pour affiner les réglages :

| Réglage | Fonction |
|---|---|
| **Alignement** | Position des éléments dans la direction perpendiculaire à leur alignement : **Début**, **Centre**, **Fin** ou **Remplir**. Avec **Remplir**, ils occupent toute la largeur disponible (ou toute la hauteur, pour les zones qui défilent horizontalement). Le mode Flux ne propose pas l'option **Remplir**. |
| **Espacement** | Espace entre les éléments. |
| **Marge intérieure** | Espace entre les éléments et les bords du contenu. |
| **Éléments par ligne** | Grille uniquement. Nombre d'éléments sur chaque ligne. |
| **En placer autant que possible** | Grille uniquement. Place autant d'éléments que possible sur une ligne, au lieu d'utiliser un nombre fixe. **Taille minimale des cellules** détermine combien d'éléments peuvent être placés. |

# Défilement

Les joueurs font défiler la zone avec la molette de la souris. Maintenez `Shift` enfoncée pour faire défiler horizontalement.

- **Direction du défilement** définit si la zone défile **Verticalement**, **Horizontalement** ou dans **Les deux** directions. Dans la direction où elle ne défile pas, le contenu a exactement la même taille que la zone.
- Les éléments de texte d'une zone défilent en premier. Lorsqu'ils atteignent leur fin, la zone reprend le défilement.
- Lorsque les joueurs passent d'un bouton à l'autre avec `Tab`, la zone défile jusqu'au bouton sélectionné.

Les menus **Défilement**, **Défilement automatique** et **Barres de défilement** proposent les mêmes réglages que pour les éléments de texte. Consultez la page [Texte dans les menus](/text-in-menus#scrolling-settings) pour les découvrir. Voici les différences :

- **Alignement par crans** peut aligner le contenu **Sur les éléments**, de sorte qu'un élément se trouve toujours au début de la zone, ou **Sur les pages**.
- Les boutons et tous les autres éléments de la zone continuent de fonctionner lorsque **Faire défiler par glissement** est activé.
- Les poignées de défilement sont des poignées pixelisées, sauf si vous leur attribuez vos propres **Textures de poignée de défilement** ou une **Couleur de poignée de défilement [HEX]**.

# Arrière-plan

Les zones dessinent un panneau derrière leur contenu. Ouvrez **Arrière-plan** pour le modifier. Le fonctionnement est similaire à celui de l'[arrière-plan des éléments de texte](/text-in-menus#background) : désactivez-le avec **Afficher l'arrière-plan**, utilisez votre propre texture avec le [découpage en neuf](/nine-slicing-and-tiling) ou le carrelage, et réglez sa portée avec **Marge intérieure**.

# Faire défiler avec des actions

Vous pouvez également contrôler les zones et suivre leur état depuis d'autres parties de FancyMenu :

- L'[action](/action-scripts) **Faire défiler un élément** fait défiler une zone jusqu'à son début, sa fin, une position ou l'un des éléments qu'elle contient.
- Les [espaces réservés](/placeholders) **Position de défilement de l'élément**, **Pourcentage de défilement de l'élément** et **Taille du contenu défilant de l'élément** indiquent la position de défilement de la zone et la taille de son contenu.
- La [condition](/conditions) **L'élément a atteint la fin du défilement** vérifie si la zone a atteint la fin de son contenu.
- Les [déclencheurs](/listeners) **Lors du défilement de l'élément**, **Lorsque l'élément atteint le début du défilement** et **Lorsque l'élément atteint la fin du défilement** exécutent des actions pendant le défilement de la zone.

Tous ces éléments nécessitent l'[identifiant de l'élément](/element-identifiers) de la zone. Par exemple, voici comment afficher la distance parcourue par une zone sur une échelle de 0 à 100 :

```
{"placeholder":"scroll_area_scroll_percent","values":{"element_identifier":"3f2a9c1e-7b4d-4e8a-9c2f-1d5e6a7b8c9d-1763950000000","axis":"vertical"}}
```

# Bon à savoir

- Masquer une zone masque tout ce qu'elle contient, et son opacité s'applique également à tous ses éléments.
- Les zones ne peuvent pas être pivotées ni inclinées, et l'effet de parallaxe ne fonctionne ni pour les zones ni pour les éléments qu'elles contiennent.
- Les infobulles des éléments d'une zone sont coupées au niveau de ses bords, sauf si elles suivent la souris.
