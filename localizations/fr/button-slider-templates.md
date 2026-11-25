---
title: Modèles de boutons et de curseurs
description: >-
  Appliquez à tous les boutons ou curseurs d’un écran les textures, les sons et
  le style de libellé d’un bouton modèle.
sourceBlobSha: 805a2ae3221a644c78cd5eafebc5579bc8d60815
---

# Modèles de boutons et de curseurs

Un modèle est un [élément Bouton](/elements#button) qui transmet son apparence à tous les autres boutons ou à tous les curseurs de l’écran, qu’ils soient natifs ou personnalisés. Modifiez le modèle et ils changeront tous avec lui.

> [!TIP]
> Pour obtenir la même apparence dans tous les menus du jeu, utilisez plutôt les [personnalisations globales](/global-customizations). Les modèles s’appliquent à un seul écran, ou à tous les écrans chargés par une [disposition universelle](/universal-layouts).

# Créer un modèle

1. Ajoutez un élément Bouton à la disposition.
2. Faites un clic droit dessus, ouvrez **Paramètres du modèle** et activez **Mode modèle**.
3. Réglez **Partager les paramètres avec** sur **Boutons** ou **Curseurs**.
4. Attribuez au modèle les textures, les sons et les paramètres de libellé souhaités, comme pour n’importe quel bouton. Lorsque l’option **Curseurs** est sélectionnée, les paramètres de texture correspondent aux textures des curseurs.

Le modèle n’apparaît pas en dehors de l’éditeur : placez-le donc où il ne gênera pas. Dans l’éditeur, un modèle destiné aux curseurs ressemble à un curseur.

# Paramètres partagés par les modèles

## Toujours

- Ses textures de bouton (ou de curseur), ainsi que leurs paramètres de [découpage en neuf parties](/nine-slicing-and-tiling).
- Ses sons de survol, de fin de survol et de clic.

Lorsqu’un modèle est actif, les boutons utilisent ses textures et ses sons à la place des leurs. Si le modèle n’a pas de textures, les boutons n’utilisent pas non plus les leurs.

## À activer

Activez les paramètres suivants dans les **Paramètres du modèle** :

| Paramètre | Paramètres appliqués aux boutons par le modèle |
|---|---|
| **Partager le libellé en mode modèle** | Son **Libellé** et son **Libellé au survol**, ainsi que l’ensemble de son style de libellé : **Alignement du libellé**, **Échelle du libellé**, **Couleur de base du libellé**, **Couleur du libellé au survol**, **Ombre du libellé** et **Souligner le libellé au survol**. |
| **Partager la position X en mode modèle** et **Partager la position Y en mode modèle** | Sa position. Les boutons natifs ne se déplacent que si leur **Point d’ancrage** est différent de **Natif (original)**. |
| **Partager l’opacité en mode modèle** | Son opacité. |

## Alignement du libellé de tous les boutons

Avec **Partager le libellé en mode modèle**, tous les boutons reprennent également le texte du modèle : cette option est donc destinée aux écrans où tous les boutons doivent afficher le même texte.

Pour aligner uniquement les libellés tout en conservant leur texte :

- Pour un seul écran, sélectionnez les boutons en maintenant `Ctrl` et en cliquant (voir [Sélection](/layout-editor#selecting)), faites un clic droit sur l’un d’eux, puis définissez une seule fois **Alignement du libellé** pour tous.
- Pour tous les menus, utilisez **Alignement du libellé** dans les [personnalisations globales](/global-customizations#labels).

# Bon à savoir

- Seuls les éléments Bouton peuvent servir de modèles, mais ceux-ci fonctionnent avec les boutons et les curseurs natifs comme personnalisés.
- Un écran peut avoir simultanément un modèle pour les boutons et un autre pour les curseurs. S’il existe plusieurs modèles du même type, un seul d’entre eux fonctionne.
- Un modèle ne fonctionne que lorsqu’il est visible. Vous pouvez l’activer et le désactiver à l’aide de [conditions](/element-visibility).
