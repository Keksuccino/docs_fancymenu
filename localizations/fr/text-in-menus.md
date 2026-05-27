---
title: Texte dans les menus
description: Comment ajouter du texte aux menus.
---
# Texte dans les menus

FancyMenu vous permet d’ajouter du contenu textuel aux menus/écrans via l’élément **Texte**.

Cet élément est défilable, prend en charge entièrement le Markdown et le retour à la ligne automatique, ce qui le rend très puissant pour afficher même du contenu textuel complexe, tout en étant aussi idéal pour de simples lignes uniques.

# Contenu textuel

L’élément Texte peut récupérer son contenu de nombreuses façons. Il vous permet de définir une source pour son contenu textuel, qui peut être une saisie de texte brut directe, un fichier texte local dans le dossier `assets` de FancyMenu (`/config/fancymenu/assets/`), un fichier texte en ligne (via URL) ou un fichier texte local chargé via un pack de ressources.

Utiliser le type de source web comme source de texte est particulièrement utile si vous voulez créer quelque chose comme un journal des modifications toujours à jour, un flux d’actualités ou des éléments similaires, sans avoir besoin de publier une mise à jour de votre modpack.

Gardez à l’esprit que FancyMenu met en cache le contenu des sources de texte, afin de ne pas devoir récupérer constamment le contenu à nouveau (ce qui serait très mauvais pour les performances). Le contenu n’est mis en cache que pour la session active, donc redémarrer le jeu videra le cache. Vous pouvez également vider le cache en rechargeant FancyMenu via **barre de menu -> Personnalisation -> Recharger FancyMenu**.

# Placeholders

L’élément Texte prend également en charge le système de placeholders de FancyMenu, ce qui permet de rendre le contenu textuel dynamique et de réagir à divers changements liés aux menus, mondes, joueurs, etc.

# Personnaliser ou désactiver le Markdown

Si vous voulez personnaliser les couleurs des titres ou d’autres éléments liés au Markdown, faites simplement un **clic droit** sur l’élément Texte, puis cliquez sur **Markdown**. Dans le sous-menu contextuel qui s’ouvre, vous verrez de nombreuses options pour personnaliser l’apparence et le comportement de l’analyseur Markdown.

Si vous ne voulez pas du tout d’analyse Markdown, ce qui peut améliorer les performances pour de longs contenus textuels, vous pouvez désactiver complètement le Markdown dans le menu **Markdown** en faisant un **clic droit** sur l’élément Texte.

# Désactiver le retour à la ligne automatique

Si vous ne voulez pas de retour à la ligne automatique, vous pouvez le désactiver en faisant un **clic droit** sur l’élément Texte.

# Désactiver le défilement et masquer les poignées de défilement

Les éléments Texte sont défilables par défaut, et si l’élément estime que l’utilisateur doit faire défiler pour voir tout son contenu, il affichera ses barres/poignées de défilement, qui sont de petites barres grises translucides (aux bords arrondis) sur les côtés droit et inférieur de l’élément Texte (barres de défilement verticale et horizontale). Les poignées de défilement sont parfois aussi prises pour des ombres.

Vous pouvez désactiver ces poignées en désactivant **Défilement** dans le menu qui s’ouvre lorsque vous faites un **clic droit** sur l’élément. Cela désactivera le défilement en général, pas seulement les poignées. Si vous voulez simplement que les poignées soient invisibles tout en gardant la possibilité de faire défiler, vous pouvez définir des textures personnalisées pour les poignées de défilement en faisant un clic droit sur l’élément. Il suffit d’y définir une texture entièrement transparente.

# Format de texte brut des composants de Minecraft (composants JSON sérialisés)

L’élément Texte ne prend PAS en charge le format de composants bruts de Minecraft. Ce format n’est pris en charge que par les libellés des boutons et des curseurs.
