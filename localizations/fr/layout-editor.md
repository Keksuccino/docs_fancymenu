---
title: Éditeur de mise en page
description: >-
  Comment ouvrir l’éditeur de mise en page, sélectionner, déplacer et
  redimensionner des éléments, les organiser avec des calques et des groupes,
  enregistrer votre mise en page et utiliser tous les raccourcis de l’éditeur.
sourceBlobSha: c247d44a67ac209f2a0b638cb4748b408c7e7b13
---

# Éditeur de mise en page

L’éditeur de mise en page vous permet de créer des [mises en page](/home#your-first-layout) : vous ajoutez des éléments, les déplacez et les redimensionnez, et modifiez le menu qui les entoure. Il affiche le menu tel que les joueurs le voient, ce qui vous permet de voir immédiatement le résultat.

<img width="800" alt="Déplacement et élargissement d’un titre, léger ajustement de sa position, sélection de deux boutons, copie et collage, déplacement des copies vers le bas et annulation de l’action" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/layout_editor_basics.gif?raw=true">

# Ouvrir l’éditeur

1. Ouvrez le menu que vous souhaitez modifier, comme l’écran titre.
2. Cliquez sur **barre de menu -> Personnalisation -> Personnalisation de l’écran actuel**, de sorte que l’option affiche **Activé**.
3. Cliquez sur **barre de menu -> Personnalisation -> Mises en page -> Nouveau -> Pour l’écran actuel**.

- **Pour tous les écrans [universel]** crée une [mise en page universelle](/universal-layouts), qui s’affiche dans tous les menus.
- Vos mises en page existantes apparaissent également dans **Mises en page**. Survolez-en une et cliquez sur **Modifier la mise en page**.
- Dans n’importe quel menu, `Ctrl + Alt + L` ouvre la dernière mise en page que vous avez modifiée. Consultez [les raccourcis de la barre de menu](/home#menu-bar-shortcuts).

# Aperçu de l’éditeur

<img width="800" alt="Éditeur de mise en page avec le bouton Rejoindre le serveur sélectionné, la barre de menu en haut et le panneau Calques à droite" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/layout_editor_overview.png?raw=true">

- Faites un clic droit sur l’arrière-plan pour afficher les paramètres de toute la mise en page et ajouter des éléments avec **Nouvel élément**.
- Faites un clic droit sur un élément pour afficher ses paramètres. Consultez [Éléments](/elements#settings-of-all-elements).
- Le panneau **Calques** à droite répertorie tous les éléments de la mise en page. Consultez [Calques et groupes](#layers-and-groups).
- La barre de menu en haut :

| Menu | Contenu |
|---|---|
| **Mise en page** | **Nouveau**, **Ouvrir**, **Enregistrer**, **Enregistrer sous**, **Exporter la mise en page pour l’IA**, **Propriétés de la mise en page** (comme dans le menu contextuel de l’arrière-plan), **Paramètres** et **Fermer l’éditeur** |
| **Édition** | **Annuler**, **Rétablir**, **Copier**, **Coller** et **Tout sélectionner** |
| **Élément** | **Nouveau** pour ajouter des éléments et **Éléments vanilla supprimés** pour restaurer les [éléments vanilla que vous avez supprimés](/deleted-vanilla-elements) |
| **Fenêtre** | **Widgets de l’éditeur**, la [grille](#grid-and-anchor-overlay), la [superposition des points d’ancrage](#grid-and-anchor-overlay), **Commandes de rotation des éléments** et **Commandes d’inclinaison des éléments** |

## Paramètres de la mise en page

Le menu contextuel de l’arrière-plan regroupe tous les paramètres de la mise en page, notamment :

- [**Arrière-plans des menus**](/menu-backgrounds) et [**Superpositions décoratives**](/decoration-overlays)
- **Titre d’écran personnalisé** pour le texte affiché en haut de certains menus, comme « Options ». Les [espaces réservés](/placeholders) y fonctionnent.
- **Personnalisation de l’en-tête et du pied de page** pour les [écrans défilants](/customizing-scrollable-screens)
- **Index de mise en page [ordre multi-mises en page]** et **Mode aléatoire** pour [utiliser plusieurs mises en page dans un même menu](/randomize-layouts)
- **Conditions de chargement [ensemble de la mise en page]**, consultez [Conditions](/conditions#layout-wide-requirements)
- **Modifier le script d’action « Ouvrir l’écran »** et **Modifier le script d’action « Fermer l’écran »**, consultez [Scripts d’action](/action-scripts)
- **Options de mise en page universelle**, uniquement dans les [mises en page universelles](/universal-layouts)

# Travailler avec les éléments

## Sélectionner

- Cliquez sur un élément pour le sélectionner. Cliquez sur l’arrière-plan pour tout désélectionner.
- Faites glisser le pointeur sur l’arrière-plan pour sélectionner tous les éléments à l’intérieur du rectangle.
- `Ctrl` + clic ajoute un élément à la sélection ou l’en retire s’il est déjà sélectionné.
- `Ctrl + A` sélectionne tous les éléments.

Les clics, les sélections par rectangle et `Ctrl + A` ignorent les éléments que vous avez [masqués dans les calques](#hiding-and-renaming).

## Déplacer

- Faites glisser un élément pour le déplacer. Pour déplacer plusieurs éléments sélectionnés, maintenez `Ctrl` enfoncé au début du déplacement. Sans `Ctrl`, le clic sélectionne uniquement l’élément sur lequel vous avez cliqué.
- Les touches fléchées déplacent les éléments sélectionnés d’un pixel.
- Pendant le déplacement, les points d’ancrage s’affichent. Placez l’élément au-dessus d’un autre point d’ancrage ou d’un autre élément pour l’y ancrer. Consultez [Positionner les éléments](/positioning-elements).
- Déposez un élément dans une [zone défilante](/scrollable-areas) pour l’y placer.

## Redimensionner

Faites glisser un bord ou un coin d’un élément sélectionné. Maintenez `Shift` enfoncée pour conserver ses proportions.

Le redimensionnement ne fonctionne que lorsqu’un seul élément est sélectionné.

## Faire pivoter et incliner

Les éléments sélectionnés qui le permettent affichent des commandes pour les [faire pivoter et les incliner](/rotating-elements). Maintenez `Shift` enfoncée pendant le déplacement pour accrocher l’élément à des incréments : 45° pour la rotation et 15° pour l’inclinaison.

Les options **Fenêtre -> Commandes de rotation des éléments** et **Commandes d’inclinaison des éléments** masquent ces commandes.

## Copier, coller et supprimer

- `Ctrl + C` copie les éléments sélectionnés et `Ctrl + V` les colle. Les copies se superposent aux originaux et sont sélectionnées ; vous pouvez donc les déplacer immédiatement.
- Vous pouvez aussi coller des éléments dans une autre mise en page, tant que le jeu n’est pas fermé.
- `Delete` supprime les éléments sélectionnés. Les éléments vanilla sont simplement masqués : restaurez-les avec **Élément -> Éléments vanilla supprimés**.
- Lorsque vous supprimez une zone défilante, l’éditeur vous demande si son contenu doit également être supprimé ou rester dans la mise en page.

## Annuler et rétablir

`Ctrl + Z` annule la dernière modification et `Ctrl + Y` la rétablit. Ces deux commandes se trouvent également dans le menu **Édition**.

## Éléments invisibles

Les joueurs ne peuvent pas voir les éléments [Audio](/elements#audio), [Déplaceur](/dragger), [Animateur d’élément](/element-animator), [Contrôleur de musique](/elements#music-controller) et [Défileur](/elements#ticker). Dans l’éditeur, ils apparaissent sous forme de rectangles colorés portant leur nom, ce qui vous permet de les repérer, de les déplacer et de les redimensionner.

- **Couleur dans l’éditeur**, dans leur menu contextuel, permet de modifier la couleur du rectangle, par exemple pour distinguer plusieurs défileurs. Les couleurs s’écrivent au format `#RRGGBB`, ou `#RRGGBBAA` avec transparence : une couleur semi-transparente comme `#E30E2366` laisse voir ce qui se trouve derrière le rectangle.
- Le nom affiché dans le rectangle est le nom du calque de l’élément. Consultez [Masquer et renommer](#hiding-and-renaming).

Les joueurs ne voient jamais le rectangle, sa couleur ni son nom.

# Calques et groupes

Le panneau **Calques** répertorie tous les éléments de la mise en page, en commençant par celui qui se trouve le plus haut : un élément s’affiche devant tous ceux qui se trouvent plus bas dans la liste. L’option **Fenêtre -> Widgets de l’éditeur -> Calques** permet d’afficher ou de masquer le panneau.

<img width="800" alt="Déplacement du calque Arrière-plan des actualités sous Texte des actualités, pour afficher les notes de mise à jour après sa désélection, puis ajout d’un groupe, placement des deux calques dedans, masquage et affichage du groupe avec son icône en forme d’œil, et réduction du groupe" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/layout_editor_layers.gif?raw=true">

## Modifier l’ordre

- Cliquez sur un calque pour sélectionner son élément, puis faites-le glisser vers le haut ou le bas. Un trait indique où il sera placé. Tous les calques sélectionnés se déplacent ensemble.
- Vous pouvez aussi faire un clic droit sur un élément ou son calque, puis cliquer sur **Monter d’un calque** ou **Descendre d’un calque**.

Dans l’éditeur, les éléments sélectionnés s’affichent toujours devant les autres. Désélectionnez-les pour voir leur ordre réel.

Dans certaines versions de Minecraft, les éléments [Entité du joueur](/elements#player-entity) et [Objet](/elements#item) s’affichent toujours devant tout le reste, quel que soit leur calque. Consultez [Problèmes connus](/known-issues#1-player-entity--item-elements-are-always-in-front-of-everything).

## Éléments vanilla

La ligne **Éléments vanilla** représente tous les éléments du menu lui-même, comme ses boutons. Leur ordre ne peut pas être modifié, mais le bouton à droite de la ligne permet de placer tous vos éléments derrière ou devant eux. Il a le même effet que l’option **Éléments personnalisés derrière les éléments vanilla** dans le menu contextuel de l’arrière-plan.

## Masquer et renommer

- L’icône en forme d’œil d’un calque masque son élément dans l’éditeur, pour qu’il ne vous gêne pas pendant que vous travaillez sur les autres. Cliquez à nouveau sur l’icône pour afficher l’élément.
- Les éléments masqués ne peuvent pas être sélectionnés, déplacés, copiés ni supprimés. Les joueurs les voient toujours : ils sont masqués uniquement dans l’éditeur. La mise en page mémorise les éléments que vous avez masqués.
- Faites un clic droit sur un calque, puis cliquez sur **Renommer le calque** pour lui donner un nom plus facile à repérer, comme `Panneau des actualités`. Cela correspond au **Nom d’affichage dans l’éditeur** de l’élément ; les joueurs ne le voient pas.

## Groupes

Les groupes rassemblent sous un même nom les calques associés, comme toutes les parties d’un panneau d’actualités. Ils servent uniquement à organiser la liste : les éléments s’affichent et fonctionnent comme avant.

- Faites un clic droit dans le panneau Calques, puis cliquez sur **Ajouter un groupe**. Le groupe apparaît sous les calques.
- Faites glisser des calques sur le groupe pour les y placer. Faites-les glisser hors du groupe pour les en retirer.
- Cliquez sur un groupe pour sélectionner tous ses éléments. Faites-le glisser pour déplacer tous ses éléments vers le haut ou le bas en même temps.
- La flèche d’un groupe permet de réduire ou de développer ses calques ; son icône en forme d’œil permet de tous les masquer ou de les afficher.
- Faites un clic droit sur un groupe pour le renommer, le déplacer d’un calque vers le haut ou le bas, ou le supprimer. **Supprimer le groupe** conserve ses éléments.

Les commandes **Monter d’un calque** et **Descendre d’un calque** conservent l’élément dans son groupe. Pour l’en retirer, faites glisser son calque hors du groupe.

La mise en page enregistre ses groupes et leur état réduit ou développé.

## Zones défilantes

Les éléments d’une [zone défilante](/scrollable-areas) apparaissent sous le calque de la zone, avec un retrait.

- Faites glisser un calque sur la moitié inférieure du calque d’une zone pour placer l’élément dans cette zone. Faites-le glisser hors de la zone, entre d’autres calques, pour l’en retirer. Il reste à la même position à l’écran.
- La flèche du calque d’une zone permet de réduire ou de développer ses éléments.
- Les éléments d’une zone n’appartiennent à aucun groupe. Ils se déplacent avec la zone.

# Grille et superposition des points d’ancrage

Le menu **Fenêtre** regroupe les paramètres des outils d’aide de l’éditeur :

- **Grille** affiche les lignes de la grille ; `Ctrl + G` permet de les afficher ou de les masquer. **Taille de la grille** définit l’espacement entre les lignes.
- **Alignement sur la grille** fait accrocher à la grille les éléments déplacés, lorsque celle-ci est affichée. **Force de l’alignement sur la grille** définit l’intensité de cet effet.
- **Visibilité de la superposition des points d’ancrage** définit quand les points d’ancrage s’affichent :
  - **Afficher pendant le déplacement d’un élément** : pendant que vous déplacez des éléments.
  - **Toujours visible** : en permanence.
  - **Afficher à l’appui d’une touche (touche « O »)** : lorsque vous maintenez `O` enfoncée.
  - **Désactivé** : jamais.
- **Détection du survol des zones d’ancrage** détermine si le fait de placer un élément au-dessus d’un point d’ancrage modifie son ancrage. **Détection du survol des éléments d’ancrage** ajoute d’autres éléments aux points d’ancrage ; cette option ne fonctionne que si **Détection du survol des zones d’ancrage** est également activée.

# Enregistrer et fermer

- `Ctrl + S` ou **Mise en page -> Enregistrer** enregistre la mise en page. La première fois, FancyMenu vous demande un nom de fichier.
- **Mise en page -> Enregistrer sous** enregistre la mise en page dans un nouveau fichier.
- Tant qu’il reste des modifications non enregistrées, la barre de menu affiche **\* Modifications non enregistrées ! \***.
- Le X à droite de la barre de menu ou **Mise en page -> Fermer l’éditeur** ferme l’éditeur. Si des modifications n’ont pas été enregistrées, l’éditeur vous le signale d’abord.

# Raccourcis

Sur macOS, utilisez `Cmd` à la place de `Ctrl`.

| Raccourci | Action |
|---|---|
| `Ctrl + S` | Enregistrer |
| `Ctrl + Z` | Annuler |
| `Ctrl + Y` | Rétablir |
| `Ctrl + C` | Copier les éléments sélectionnés |
| `Ctrl + V` | Coller |
| `Ctrl + A` | Sélectionner tous les éléments |
| `Delete` | Supprimer les éléments sélectionnés |
| Touches fléchées | Déplacer les éléments sélectionnés d’un pixel |
| `Ctrl` + clic | Ajouter un élément à la sélection ou l’en retirer |
| `Ctrl` + glisser | Déplacer plusieurs éléments sélectionnés |
| `Shift` + redimensionnement | Conserver les proportions |
| `Shift` + rotation ou inclinaison | Accrocher à des incréments |
| `Ctrl + G` | Afficher ou masquer la grille |
| Maintenir `O` | Afficher les points d’ancrage avec **Afficher à l’appui d’une touche (touche « O »)** |

> [!TIP]
> L’éditeur de texte possède ses propres raccourcis ; consultez [Texte dans les menus](/text-in-menus#the-text-editor). Les fenêtres comme les [scripts d’action](/action-scripts#shortcuts) répertorient leurs raccourcis sur leurs pages respectives.
