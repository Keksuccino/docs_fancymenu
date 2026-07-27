---
title: Découpage en neuf et mosaïque
description: Agrandir des textures bordées ou répéter des textures sans jointure.
---

# Découpage en neuf et mosaïque

Le découpage en neuf préserve les coins et les bordures d’une texture tout en étirant son centre. La mosaïque répète une texture au lieu de l’étirer.

<img src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/nine_slicing_example.png" alt="Régions du découpage en neuf" style="max-width:500px;height:auto;" />

# Prise en charge du découpage en neuf

| Zone | Cibles prises en charge |
|---|---|
| Widgets | Textures de [Button](./elements#button) et de [Slider](./elements#slider) ; [styles globaux des boutons et des curseurs](./global-customizations#button-visuals) |
| Images et panneaux | [Éléments Image](./elements#image) |
| Barres de progression | [Textures de remplissage et d’arrière-plan](./elements#progress-bar) |
| Info-bulles | [Textures d’arrière-plan personnalisées](./elements#tooltip) |

# Configuration du découpage en neuf

1. Définissez la texture cible.
2. सक्रियez son option **Découpage en neuf**.
3. Définissez les tailles des bordures pour correspondre à la zone fixe des bords dans la texture source.
4. Redimensionnez l’élément et ajustez les valeurs des bordures si les coins ou les bords se déforment.

Les paramètres des boutons et des images utilisent des tailles de bordure X/Y. Les barres de progression et les info-bulles exposent des valeurs de bord distinctes lorsque nécessaire.

# Prise en charge de la mosaïque

Les textures répétées sont disponibles pour :

- [Éléments Image](./elements#image).
- [Arrière-plans d’image des menus](./menu-backgrounds).
- [Textures d’en-tête et de pied de page des listes déroulantes](./customizing-scrollable-screens).

Activez **Répéter la texture** sur un élément Image ou un arrière-plan Image. Pour les écrans défilants, utilisez les options de répétition dans le menu de personnalisation de l’en-tête/pied de page.

Utilisez une texture source sans jointure ; des bords qui ne correspondent pas créeront des lignes visibles entre les tuiles.

Le découpage en neuf et la répétition sont deux modes distincts. Si les deux options sont affichées pour une cible, choisissez celle qui correspond au comportement de mise à l’échelle souhaité.
