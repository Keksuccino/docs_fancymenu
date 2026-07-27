---
title: Texte dans les menus
description: Comment ajouter du contenu textuel aux menus.
---
# Texte dans les menus

FancyMenu vous permet d'ajouter du contenu textuel aux menus/écrans via l'élément **Texte**.

Cet élément est défilable, prend en charge le Markdown complet et le retour à la ligne automatique, ce qui le rend très puissant pour afficher même du contenu textuel complexe, tout en étant aussi idéal pour de simples lignes de texte.

# Contenu textuel

L'élément Texte peut récupérer son contenu de plusieurs façons. Il vous permet de définir une source pour son contenu textuel, qui peut être une saisie de texte brut directe, un fichier texte local dans le répertoire des ressources de FancyMenu (`<game-directory>/config/fancymenu/assets/`), un fichier texte web (via une URL) ou un fichier texte local chargé via un pack de ressources.

L'utilisation d'une source web comme source de texte est particulièrement utile si vous souhaitez créer quelque chose comme un changelog toujours à jour, un fil d'actualités ou des éléments similaires, sans avoir à publier une mise à jour de votre modpack.

Gardez à l'esprit que FancyMenu met en cache le contenu des sources de texte, afin de ne pas devoir récupérer constamment le contenu à nouveau (ce qui nuirait fortement aux performances). Le contenu n'est mis en cache que pour la session active, donc redémarrer le jeu videra le cache. Vous pouvez également vider le cache en rechargeant FancyMenu via **barre de menus -> Personnalisation -> Recharger FancyMenu**.

# Espaces réservés

L'élément Texte prend également en charge le système d'espaces réservés de FancyMenu, ce qui permet de rendre le contenu textuel dynamique et de réagir à divers changements liés aux menus, aux mondes, aux joueurs, etc.

# Personnalisation ou désactivation du Markdown

Si vous souhaitez personnaliser les couleurs des titres ou d'autres éléments liés au Markdown, faites simplement un **clic droit** sur l'élément Texte, puis cliquez sur **Markdown**. Dans le sous-menu contextuel qui s'ouvre, vous verrez de nombreuses options pour personnaliser l'apparence et le comportement de l'analyseur Markdown.

Si vous ne souhaitez pas du tout d'analyse Markdown, ce qui peut améliorer les performances pour les longs contenus textuels, vous pouvez désactiver complètement le Markdown dans le menu **Markdown** en **faisant un clic droit** sur l'élément Texte.

# Désactiver le retour à la ligne automatique

Si vous ne souhaitez pas de retour à la ligne automatique, vous pouvez le désactiver en **faisant un clic droit** sur l'élément Texte.

# Désactiver le défilement et masquer les barres de défilement

Les éléments Texte sont défilables par défaut et, si l'élément estime que l'utilisateur doit faire défiler pour voir tout son contenu, il affichera ses barres/poignées de défilement, qui sont de petites barres grises semi-transparentes (avec des bords arrondis) sur les côtés droit et inférieur de l'élément Texte (barres de défilement verticale et horizontale). Il arrive aussi que les poignées de défilement soient confondues avec des ombres.

Vous pouvez désactiver ces poignées en désactivant **Défilement** dans le menu qui s'ouvre lorsque vous **faites un clic droit** sur l'élément. Cela désactivera le défilement en général, pas seulement les poignées. Si vous voulez simplement rendre les poignées invisibles tout en conservant la possibilité de faire défiler, vous pouvez définir des textures personnalisées pour les poignées de défilement en faisant un clic droit sur l'élément. Il suffit d'y définir une texture totalement transparente.

# Format de texte brut des composants de Minecraft (composants JSON sérialisés)

L'élément Texte ne prend pas en charge le format de composants bruts de Minecraft. Ce format n'est pris en charge que par les étiquettes des boutons et des curseurs.
