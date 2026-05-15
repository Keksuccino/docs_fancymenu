---
title: Opacité des éléments
description: Comment contrôler l'opacité des éléments.
---

# Opacité des éléments

La plupart des éléments de FancyMenu (avec quelques exceptions) prennent en charge le réglage de leur opacité via leur menu contextuel accessible par clic droit.

La valeur d'opacité des éléments prend en charge les placeholders, ce qui permet de mettre à jour leur opacité de manière dynamique en fonction du placeholder.

Cela permet de créer une logique de fondu personnalisée lorsqu'elle est utilisée en combinaison avec des éléments Ticker pour mettre à jour des valeurs variables, puis les appliquer comme opacité via des placeholders.

Pour définir l'opacité des éléments, **clic droit sur l'élément -> Opacité -> Définir**.

# Faire apparaître/disparaître les éléments en fondu

Si vous souhaitez simplement faire apparaître ou disparaître des éléments en fondu, il est probablement plus simple d'utiliser la fonctionnalité de fondu intégrée des éléments. Vous pouvez l'activer dans le menu contextuel accessible par clic droit des éléments.

Cette fonctionnalité fait apparaître les éléments en fondu à chaque chargement, que ce soit lors du chargement initial à l'ouverture d'un menu ou lorsque les conditions de chargement de l'élément provoquent son chargement. Ils disparaîtront en fondu chaque fois que leurs conditions de chargement les rendent déchargés/invisibles.

La fonctionnalité de fondu permet de définir une vitesse de fondu afin de contrôler la rapidité avec laquelle un élément doit apparaître ou disparaître en fondu.
