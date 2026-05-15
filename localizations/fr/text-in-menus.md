---
title: Texte dans les menus
description: Comment ajouter du texte aux menus.
---

# Texte dans les menus

FancyMenu vous permet d’ajouter du contenu textuel aux menus/écrans via l’élément **Texte**.

Cet élément est défilable, prend entièrement en charge le Markdown et le retour à la ligne, ce qui le rend très puissant pour afficher même du contenu textuel complexe, tout en étant aussi idéal pour de simples lignes uniques.

## Contenu textuel

L’élément Texte peut récupérer son contenu de nombreuses façons. Il vous permet de définir une source pour son contenu textuel, qui peut être une saisie de texte brut directe, un fichier texte local dans le dossier `assets` de FancyMenu (`/config/fancymenu/assets/`), un fichier texte en ligne (via une URL) ou un fichier texte local chargé via un pack de ressources.

L’utilisation du type de source web comme source de texte est particulièrement utile si vous souhaitez créer quelque chose comme un journal des modifications toujours à jour, un fil d’actualités ou des éléments similaires, sans avoir besoin de publier une mise à jour de votre modpack.

Gardez à l’esprit que FancyMenu met en cache le contenu des sources de texte, afin de ne pas avoir à le récupérer constamment à nouveau (ce qui nuirait fortement aux performances). Le contenu n’est mis en cache que pour la session active, donc redémarrer le jeu videra le cache. Vous pouvez également vider le cache en rechargant FancyMenu via **barre de menu -> Personnalisation -> Recharger FancyMenu**.

## Espaces réservés

L’élément Texte prend également en charge le système d’espaces réservés de FancyMenu, ce qui permet de rendre le contenu textuel dynamique et de réagir à divers changements liés aux menus, mondes, joueurs, etc.

## Personnaliser ou désactiver le Markdown

Si vous souhaitez personnaliser les couleurs des titres ou d’autres éléments liés au Markdown, faites simplement **clic droit** sur l’élément Texte, puis cliquez sur **Markdown**. Dans le sous-menu contextuel qui s’ouvre, vous verrez de nombreuses options pour personnaliser l’apparence et le comportement de l’analyseur Markdown.

Si vous ne voulez pas du tout de l’analyse Markdown, ce qui peut améliorer les performances pour les contenus textuels longs, vous pouvez désactiver complètement le Markdown dans le menu **Markdown** en faisant **clic droit** sur l’élément Texte.

## Désactiver le retour à la ligne automatique

Si vous ne souhaitez pas de retour à la ligne automatique, vous pouvez le désactiver en faisant **clic droit** sur l’élément Texte.

## Désactiver le défilement

Les éléments Texte sont défilables par défaut et, si l’élément estime que l’utilisateur doit faire défiler pour voir tout son contenu, il affichera ses barres de défilement, qui sont de petites barres grises sur les côtés droit et inférieur de l’élément Texte (barres de défilement verticale et horizontale).

Vous pouvez désactiver ces barres en désactivant **Défilement** dans le menu qui s’ouvre lorsque vous faites **clic droit** sur l’élément. Cela désactivera le défilement en général, pas seulement les barres. Si vous voulez plutôt que les barres soient invisibles, vous pouvez définir des textures de barre de défilement personnalisées en faisant un clic droit sur l’élément. Il suffit d’y définir une texture entièrement transparente.

## Format de texte brut des composants de Minecraft (composants JSON sérialisés)

L’élément Texte ne prend PAS en charge le format de composants bruts de Minecraft. Ce format est uniquement pris en charge par les étiquettes des boutons et des curseurs.
