---
title: Commencer
description: >-
  Le monde de FancyMenu vous attend ! C'est le début de quelque chose de
  magnifique !
---

# Pour les développeurs

Si vous êtes développeur et que vous souhaitez créer un addon pour FancyMenu ou intégrer FancyMenu à votre mod, vous devriez consulter la [documentation pour les développeurs](https://github.com/Keksuccino/FancyMenu-Dev-Docs/wiki).

# Commencer

La première utilisation de FancyMenu peut sembler un peu intimidante, mais ne vous inquiétez pas : la plupart des choses deviennent en fait assez simples une fois que vous commencez à l'utiliser !

> Veuillez **garder à l'esprit** que cette page sert uniquement à découvrir FancyMenu et à vous aider pour vos **tout premiers pas**.
Assurez-vous également de consulter le reste de la documentation pour obtenir des informations plus détaillées sur les fonctionnalités de FancyMenu !
{.is-info}

# La barre de menu

L'une des premières choses que vous remarquerez en lançant le jeu est la **barre de menu** en haut de chaque menu.

La **barre de menu** est votre point d'entrée vers pratiquement toutes les fonctionnalités de FancyMenu, comme **créer des layouts** pour **personnaliser les menus**, modifier le **titre et l'icône de la fenêtre**, et bien plus encore.

> Si vous avez appuyé accidentellement sur certaines touches et que la **barre de menu a disparu**, vous pouvez la faire réapparaître en appuyant sur **CTRL + ALT + C**.
{.is-warning}

<img width="650" alt="menu_bar" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/menu_bar.png?raw=true">

# Votre premier layout

Comme vous souhaitez probablement personnaliser les menus de Minecraft, laissez-moi vous parler des **layouts** !

Les layouts sont comme des couches de personnalisation pour les menus, et ils vous permettent d'ajouter de nouveaux éléments et de personnaliser ceux qui existent déjà.

Pour créer un nouveau layout pour un **menu spécifique** :
1. Ouvrez le menu pour lequel vous souhaitez créer un layout (l'écran titre, par exemple)
2. Ouvrez l'onglet **Personnalisation** de la **barre de menu**

Les personnalisations sont désactivées par défaut pour tous les menus, et vous devez les activer pour chaque menu que vous souhaitez personnaliser. Cliquez donc d'abord sur l'entrée **"Personnalisation de l'écran actuel : désactivée"**, ce qui basculera l'option sur **Activée**.

<img width="475" alt="toggle_customizations" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/toggle_customizations.png?raw=true">

Ensuite, cliquez sur **Layouts -> New -> For Current Screen**.

Cela ouvrira l'**éditeur de layout**, où vous pourrez ajouter des éléments au layout et personnaliser les éléments Vanilla et ceux des mods (comme les boutons).

<img width="550" alt="new_layout_current" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/new_layout_current.png?raw=true">

## Modifier le layout

La plupart des options de personnalisation sont accessibles en **cliquant avec le bouton droit sur l'arrière-plan de l'éditeur**.
Cela ouvrira un menu contextuel contenant de nombreuses options, comme la personnalisation de l'**arrière-plan du menu** ou l'**ajout d'éléments** au layout.

<br>
<img width="350" alt="context_menu" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/context_menu.png?raw=true">

## Ajouter des éléments aux layouts

Pour ajouter un nouvel élément à votre layout, **cliquez avec le bouton droit** sur l'arrière-plan de l'éditeur.

Dans le menu contextuel qui s'ouvre, cliquez sur **New Element** et choisissez l'un des nombreux types d'éléments.

<img width="525" alt="add_element" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/add_element.png?raw=true">

## Personnaliser des éléments

Pour personnaliser un élément, **cliquez dessus avec le bouton droit**, ce qui ouvrira un menu contextuel contenant tout ce que vous pouvez modifier pour ce type d'élément.

En plus des éléments que vous avez ajoutés, vous pouvez également personnaliser les éléments vanilla (même s'ils offrent parfois moins d'options)

<img width="525" alt="element_customization" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/element_customization.png?raw=true">

> [!IMPORTANT]
> Certains menus contextuels comme celui-ci sont **défilables** !

## Positionner les éléments

Chaque élément dans FancyMenu est lié à un **point d'ancrage**.

Les points d'ancrage sont nécessaires pour calculer la position d'un élément et, s'ils sont utilisés correctement, ils empêchent les éléments de se chevaucher, de sortir de l'écran ou de se déplacer au mauvais endroit lors du redimensionnement de la fenêtre.

Ils constituent le point d'origine à partir duquel la position de l'élément est calculée.

Par défaut, les éléments sont reliés au point d'ancrage **"Center of Screen"**, qui correspond en gros au centre exact de l'écran, quelle que soit la taille de la fenêtre.
Supposons donc qu'un élément se trouve à 2 centimètres du centre de l'écran tout en étant relié à l'ancre **"Center of Screen"**. Dans ce cas, l'élément sera **toujours** à 2 centimètres du centre de l'écran, quelle que soit la taille de la fenêtre.

Vous pouvez voir le point d'ancrage auquel un élément est lié lorsque vous le faites glisser. Cela affichera également, par défaut, tous les autres points d'ancrage. Vous pouvez survoler un point d'ancrage en faisant glisser un élément afin de modifier l'ancre de cet élément vers le point survolé.

Vous pouvez même utiliser un élément comme point d'ancrage pour d'autres éléments ! Il suffit de survoler un élément tout en en faisant glisser un autre, et le point d'ancrage de l'élément déplacé sera modifié pour correspondre à l'élément survolé.

**[En savoir plus sur la façon de positionner vos éléments.](/positioning-elements)**

<img width="650" alt="anchor_points" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/anchor_points.png?raw=true">

## Enregistrer votre travail

N'oubliez pas d'enregistrer votre chef-d'œuvre !

Vous verrez un indicateur "Unsaved Changes" en haut à droite de l'éditeur si vous devez enregistrer vos modifications avant de le fermer.

Enregistrez votre travail en cliquant sur **Layout -> Save** !

<img width="375" alt="save_your_work" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/save_your_work.png?raw=true">

> [!TIP]
> Vous pouvez également enregistrer votre travail à l'aide du raccourci clavier **CTRL + S**

*Félicitations ! Vous pouvez maintenant rendre les menus de Minecraft beaucoup plus beaux !*
