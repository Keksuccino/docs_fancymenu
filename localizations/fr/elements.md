---
title: Éléments
description: Tout ce qu’il faut savoir sur les types d’éléments de FancyMenu.
---

# Éléments

Les éléments sont les blocs de base de vos mises en page personnalisées dans FancyMenu. Vous pouvez les ajouter à n’importe quelle mise en page pour afficher des informations, ajouter de l’interactivité ou créer de superbes effets visuels.

# Ajouter des éléments à une mise en page

Vous pouvez ajouter un nouvel élément à votre mise en page depuis l’**éditeur de mise en page**.

1.  **Cliquez avec le bouton droit** sur l’arrière-plan de l’éditeur pour ouvrir le menu contextuel.
2.  Survolez **Nouvel élément**.
3.  Une liste de tous les types d’éléments disponibles apparaîtra. Cliquez sur celui que vous souhaitez ajouter.

![add_element](https://github.com/Keksuccino/FancyMenu/assets/35544624/865a66c5-76a6-404d-b746-d57802b1c12f)

Une fois qu’un élément a été ajouté, vous pouvez le déplacer, le redimensionner et le personnaliser en faisant un **clic droit** dessus pour ouvrir son menu contextuel spécifique. Pour en savoir plus sur la manière d’organiser les éléments, consultez les pages [Positionner les éléments](https://docs.fancymenu.net/en/positioning-elements) et [იდენტifiants d’élément](https://docs.fancymenu.net/en/element-identifiers).

# Détails des éléments

La liste suivante contient la plupart, sinon la totalité, des éléments disponibles dans FancyMenu. La liste peut parfois être un peu obsolète en raison des mises à jour de FancyMenu.

## Bouton
Un bouton cliquable pouvant effectuer une grande variété d’actions. C’est l’un des éléments les plus puissants et polyvalents pour créer des menus interactifs.

*   **Cas d’utilisation :**
    *   Créer un bouton « Rejoindre Discord » ou « Visiter le site Web ».
    *   Ajouter un bouton de connexion rapide pour un serveur spécifique.
    *   Créer une navigation personnalisée entre différents menus.
    *   Créer des boutons qui activent ou désactivent d’autres mises en page.
*   **Fonctionnalités clés :**
    *   **Actions :** Peut exécuter une série d’actions, comme ouvrir une URL, rejoindre un serveur, envoyer une commande de chat, imiter la fonction d’un autre bouton, contrôler des variables, et bien plus encore. En savoir plus dans la documentation [Scripts d’actions](https://docs.fancymenu.net/en/action-scripts).
    *   **Apparence personnalisée :** Textures entièrement personnalisables pour les états normal, survolé et inactif. Prend en charge les arrière-plans transparents, le nine-slicing, les couleurs de label personnalisées, les couleurs de label au survol, l’échelle du label, l’activation/désactivation de l’ombre du label et les textures d’icône du bouton.
    *   **Sons :** Sons personnalisés de clic, de survol et de sortie de survol.
    *   **Mode modèle :** Peut servir de modèle pour appliquer son apparence et ses propriétés à tous les autres boutons Vanilla ou moddés du menu, afin d’assurer un aspect cohérent. En savoir plus sur la page [Modèles de boutons et de curseurs](https://docs.fancymenu.net/en/button-slider-templates).

## Curseur
Un curseur que les utilisateurs peuvent faire glisser pour sélectionner une valeur dans une liste ou une plage. Il peut exécuter des actions chaque fois que sa valeur change.

*   **Cas d’utilisation :**
    *   Créer un contrôle de volume personnalisé.
    *   Un curseur pour basculer entre différents thèmes ou images d’arrière-plan (en utilisant le type « Liste »).
    *   Ajuster une option Minecraft spécifique, comme la luminosité ou la distance de rendu.
*   **Fonctionnalités clés :**
    *   **Types :** Peut être une `Value List` (par ex. « Facile », « Normal », « Difficile »), une `Integer Range` (par ex. 1-100) ou une `Decimal Range` (par ex. 0.0-1.0).
    *   **Actions dynamiques :** Exécute des actions lors du changement de valeur. La valeur actuelle du curseur peut être utilisée dans ses actions pour effectuer des tâches dynamiques, ce qui peut être utilisé avec les [Variables](https://docs.fancymenu.net/en/variables).
    *   **Personnalisation :** Le label du curseur peut afficher dynamiquement sa valeur actuelle. Les textures de la poignée et de l’arrière-plan sont entièrement personnalisables, y compris les arrière-plans transparents, les options de couleur/échelle du label, l’activation/désactivation de l’ombre du texte et les sons personnalisés de clic/sortie de survol.

## Case à cocher
Une case à cocher standard qui peut être activée ou désactivée. Elle peut exécuter des actions lorsqu’elle est modifiée.

*   **Cas d’utilisation :**
    *   Une case « J’accepte les règles ».
    *   Un réglage permettant d’activer ou de désactiver une fonctionnalité spécifique dans votre menu personnalisé.
    *   Activer ou désactiver une mise en page ou une variable.
*   **Fonctionnalités clés :**
    *   **Actions lors du basculement :** Exécute des [Scripts d’actions](https://docs.fancymenu.net/en/action-scripts) lorsque son état change. L’état actuel (`true` ou `false`) peut être utilisé dans ses actions.
    *   **Mode variable :** Peut être liée directement à une variable FancyMenu, permettant à l’état de la case d’être lu depuis et écrit vers cette variable.
    *   **Apparence personnalisée :** Prend en charge des textures personnalisées pour l’arrière-plan (dans les états normal, survolé et inactif) ainsi que pour la coche elle-même.

## Champ de saisie de texte
Un champ dans lequel les utilisateurs peuvent saisir du texte. Son contenu peut être lié à une variable FancyMenu, ce qui vous permet de capturer et d’utiliser la saisie de l’utilisateur.

*   **Cas d’utilisation :**
    *   Un champ de saisie « IP du serveur » qui fonctionne avec un bouton « Rejoindre le serveur ».
    *   Un champ permettant de saisir le nom d’un joueur pour un aperçu de skin personnalisé.
    *   Créer une interface de type connexion basique.
*   **Fonctionnalités clés :**
    *   **Liaison à une variable :** Le texte saisi par l’utilisateur est stocké dans une [variable](https://docs.fancymenu.net/en/variables) spécifiée.
    *   **Validation de la saisie :** Peut être configuré pour n’accepter que certains types de caractères, comme des nombres, des URL ou du texte brut.
    *   **Longueur maximale :** Vous pouvez définir une limite maximale de caractères pour la saisie.
    *   **Apparence et sons :** Prend en charge une couleur d’arrière-plan personnalisée, des couleurs de bordure, l’arrondi des bordures, la couleur du texte, le texte d’indication/de remplacement, la couleur de l’indication, les sons de survol, de sortie de survol et de clic.

## Info-bulle
Une boîte de texte qui peut être configurée pour apparaître à un emplacement précis ou suivre le curseur de la souris. Sa visibilité est généralement contrôlée par les [Conditions (Exigences de chargement)](https://docs.fancymenu.net/en/conditions).

*   **Cas d’utilisation :**
    *   Afficher des informations détaillées lorsqu’un utilisateur survole un bouton ou une image.
    *   Créer des aides contextuelles qui apparaissent dans certaines conditions.
    *   Afficher des informations dynamiques (comme l’état d’un serveur) à côté du curseur.
*   **Fonctionnalités clés :**
    *   **Suivi de la souris :** Peut suivre le pointeur de la souris.
    *   **Prise en charge du Markdown :** Le contenu de l’info-bulle prend en charge le formatage Markdown complet.
    *   **Arrière-plan personnalisé :** L’arrière-plan peut être une couleur unie ou une texture personnalisée en nine-slicing pour un rendu entièrement thématique.

## Objet
Affiche un objet Minecraft unique, issu du jeu de base ou d’un mod.

*   **Cas d’utilisation :**
    *   Utiliser des objets comme icônes pour des boutons ou des sélections de menu.
    *   Créer une interface de boutique ou de sélection de kits.
    *   Afficher l’objet tenu ou l’armure d’un joueur.
*   **Fonctionnalités clés :**
    *   **Données personnalisées :** Vous pouvez définir le nom, l’histoire, la quantité, l’effet visuel d’enchantement et même des données NBT personnalisées de l’objet. Vous pouvez en savoir plus sur l’utilisation du NBT avec la documentation [Placehelder de données NBT](https://docs.fancymenu.net/en/nbt-data-placeholder).
    *   **Affichage de l’infobulle :** Peut être configuré pour afficher l’infobulle standard de l’objet au survol.

## Modèle JSON de bloc/objet
Rend un modèle JSON de bloc ou d’objet provenant des ressources Minecraft ou de sources externes.

*   **Cas d’utilisation :**
    *   Afficher un modèle de pack de ressources en 3D dans un menu.
    *   Montrer des aperçus d’objets/blocs avec des textures personnalisées.
    *   Créer des éléments décoratifs d’interface basés sur des modèles.
*   **Fonctionnalités clés :**
    *   **Source du modèle :** Peut charger le JSON du modèle depuis les ressources Minecraft ou depuis des sources externes.
    *   **Remplacements de texture :** Permet de définir une texture personnalisée.
    *   **Contrôles de rendu :** Inclut des contrôles de rotation et d’éclairage.

## Image
Affiche une image statique depuis un fichier local, une URL web ou un emplacement de ressource Minecraft.

*   **Cas d’utilisation :**
    *   Ajouter un logo de serveur ou une marque de modpack.
    *   Créer des bordures décoratives ou des cadres d’interface.
    *   Utiliser des images dans le cadre d’une conception d’interface plus complexe.
*   **Fonctionnalités clés :**
    *   **Nine-slicing :** Permet d’utiliser l’image comme bordure ou panneau redimensionnable sans déformer les coins. En savoir plus sur la page [Nine-Slicing & Tiling](https://docs.fancymenu.net/en/nine-slicing-and-tiling).
    *   **Répétition de texture :** L’image peut être répétée pour remplir la zone de l’élément.
    *   **Teinte :** Vous pouvez appliquer une teinte colorée à l’image.
    *   **Coins arrondis :** Les images non nine-sliced et non répétées peuvent avoir des coins arrondis.
    *   **Effet de parallaxe :** Peut être configuré pour bouger légèrement avec la souris afin de créer un effet 3D. Voir la page [Effet de parallaxe](https://docs.fancymenu.net/en/parallax) pour plus d’informations.

## Texte
Un élément très polyvalent pour afficher du texte. Il peut être utilisé pour tout, depuis des étiquettes sur une seule ligne jusqu’à des documents multi-pages défilants.

*   **Cas d’utilisation :**
    *   Afficher les règles du serveur, des notes de mise à jour ou des messages de bienvenue.
    *   Créer des panneaux d’information dynamiques à l’aide de [placeholders](https://docs.fancymenu.net/en/placeholders), par ex. « Bienvenue, `{"placeholder":"playername"}` ! ».
    *   Ajouter des étiquettes et des descriptions à votre interface.
*   **Fonctionnalités clés :**
    *   **Sources du contenu :** Le texte peut être saisi directement, chargé depuis un fichier local ou récupéré depuis une URL web.
    *   **Prise en charge du Markdown :** Prend en charge un large éventail de Markdown pour un formatage riche du texte, y compris les titres, les listes, les blocs de code et les tableaux. L’apparence des éléments Markdown est entièrement personnalisable. Voir la page [Formatage du texte](https://docs.fancymenu.net/en/text-formatting) pour plus d’informations.
    *   **Défilement :** Devient automatiquement défilable si le contenu est plus grand que la zone de l’élément. Les barres de défilement peuvent être personnalisées ou désactivées.
    *   **Style :** Contrôle total de la couleur du texte, de l’échelle, de l’alignement, de l’ombre et de l’espacement des lignes.

## Vidéo
Lit un fichier vidéo. C’est parfait pour des intros cinématiques ou des arrière-plans décoratifs en boucle.

> Le nouvel élément vidéo natif de FancyMenu 3.9.0 nécessite **Watermedia V3** et **Watermedia Binaries V3**. L’ancien élément **Video [MCEF]** est obsolète.
{.is-warning}

*   **Cas d’utilisation :**
    *   Une bande-annonce animée de modpack ou de serveur.
    *   Une vidéo d’ambiance en boucle pour donner vie à votre menu.
    *   Une vidéo tutorielle en jeu.
*   **Fonctionnalités clés :**
    *   **Sources :** Prend en charge les fichiers vidéo locaux et les URL web. Voir la page [Vidéos (MP4)](https://docs.fancymenu.net/en/video) pour plus de détails.
    *   **Contrôle de la lecture :** Peut être configuré pour boucler automatiquement. Son volume, son canal audio et son comportement de conservation du rapport hauteur/largeur sont ajustables.
    *   **Contrôle interactif :** La lecture de la vidéo, le temps de recherche et le volume peuvent être contrôlés via des actions de bouton.

## Shader GLSL
Rend un shader GLSL personnalisé à l’intérieur d’un élément.

*   **Cas d’utilisation :**
    *   Panneaux animés utilisant des shaders.
    *   Effets visuels procéduraux.
    *   Effets de menu de type Shadertoy découpés dans un rectangle d’élément.
*   **Fonctionnalités clés :**
    *   **Runtime du shader :** Prend en charge les shaders à passage unique et à passages multiples.
    *   **Prise en charge de Shadertoy :** Peut utiliser des shaders `mainImage` de type Shadertoy.
    *   **Uniformes :** Expose des uniformes FancyMenu et d’entrée. Voir la page [API du shader GLSL](https://docs.fancymenu.net/en/glsl-shader-api) pour plus de détails.

## Diaporama
Affiche une séquence d’images. La configuration du diaporama (images, durée, transitions) se fait dans un fichier `.properties` distinct situé dans le répertoire `/config/fancymenu/assets/slideshows/`.

*   **Cas d’utilisation :**
    *   Une galerie tournante de captures d’écran en jeu.
    *   Mettre en avant les fonctionnalités clés d’un modpack.
    *   Un arrière-plan dynamique qui alterne entre différentes scènes.
*   **Fonctionnalités clés :**
    *   Charge des diaporamas préconfigurés. Consultez la documentation [Diaporamas](https://docs.fancymenu.net/en/slideshows) pour les instructions de configuration.
    *   Peut être configuré pour conserver le rapport hauteur/largeur des images.

## Rectangle
Un simple rectangle de couleur unie.

*   **Cas d’utilisation :**
    *   Créer un arrière-plan semi-transparent derrière du texte pour améliorer la lisibilité.
    *   Concevoir des panneaux et des séparateurs d’interface simples.
    *   Servir d’espace réservé coloré lors de la conception de la mise en page.
*   **Fonctionnalités clés :**
    *   Prend en charge les couleurs HEX RGBA, les coins arrondis et un flou facultatif, ce qui permet à la forme de servir de panneau simple, de teinte ou d’arrière-plan flouté.

## Cercle
Une simple forme de cercle/ellipse de couleur unie.

*   **Cas d’utilisation :**
    *   Créer des accents circulaires, des indicateurs ou des zones d’interface douces.
    *   Construire des décorations d’interface thématiques sans fichier de texture.
*   **Fonctionnalités clés :**
    *   Fonctionne de manière similaire à l’élément Rectangle et prend en charge une personnalisation visuelle de type couleur/flou.

## Texte d’accueil
Une recréation du célèbre texte d’accueil jaune et rebondissant de Minecraft sur l’écran titre.

*   **Cas d’utilisation :**
    *   Remplacer le texte d’accueil vanilla par vos propres messages personnalisés.
    *   Ajouter un message animé et accrocheur à n’importe quel menu.
*   **Fonctionnalités clés :**
    *   **Sources du contenu :** Peut utiliser les textes d’accueil vanilla par défaut, une liste de textes personnalisés saisis directement, ou du texte provenant d’un fichier local.
    *   **Personnalisation :** Vous pouvez activer ou désactiver l’effet rebondissant et personnaliser la couleur, l’échelle, la rotation et l’ombre du texte.

## Entité joueur
Rend un modèle de joueur dans le menu.

*   **Cas d’utilisation :**
    *   Afficher le personnage du joueur actuel dans le menu principal.
    *   Créer un écran de sélection d’équipe ou d’aperçu de classe.
    *   Une section « profil » affichant le skin et le nom du joueur.
*   **Fonctionnalités clés :**
    *   **Apparence dynamique :** Peut être configuré pour copier automatiquement le skin, la cape et le nom du joueur actuel. Pour en savoir plus, consultez le guide [Têtes de joueur](https://docs.fancymenu.net/en/player-heads).
    *   **Poses personnalisées :** Offre un contrôle précis de la rotation de la tête, du corps, des bras et des jambes. La tête et le corps peuvent également suivre le curseur de la souris.
    *   **Attributs :** Peut être configuré pour être un bébé, être accroupi ou avoir un modèle fin.

## Navigateur
Un élément qui affiche une page Web en direct dans le jeu.

Ce élément nécessite que le mod **MCEF (Minecraft Chromium Embedded Framework)** soit installé et fonctionnel !

Vous pouvez télécharger MCEF depuis les pages officielles du projet sur [CurseForge](https://www.curseforge.com/minecraft/mc-mods/mcef) et [Modrinth](https://modrinth.com/mod/mcef).

Pour les versions plus récentes de Minecraft (1.21.5+), les projets MCEF officiels ne fournissent pas de builds, mais il existe un fork avec des builds pour les dernières versions de Minecraft, que vous pouvez trouver [ici](https://www.curseforge.com/minecraft/mc-mods/mcef-keksuccino) (CurseForge) et [ici](https://modrinth.com/mod/mcef-keksuccino) (Modrinth). Ce fork est maintenu par Keksuccino afin de fournir des builds pour les dernières versions de Minecraft le plus rapidement possible.

*   **Cas d’utilisation :**
    *   Afficher la carte Dynmap en direct d’un serveur.
    *   Intégrer un lecteur vidéo YouTube.
    *   Afficher directement en jeu un wiki ou une page de documentation.
*   **Fonctionnalités clés :**
    *   **Interactivité :** Peut être rendu entièrement interactif, permettant aux utilisateurs de cliquer sur des liens, faire défiler et saisir du texte.
    *   **Contrôle des médias :** Offre des options pour couper le son des médias, mettre les vidéos en boucle et masquer les contrôles vidéo sur la page chargée.

### Chargement de fichiers HTML locaux
L’élément Navigateur vous permet de charger des documents HTML locaux dans `/config/fancymenu/assets/` ! Cela signifie que vous pouvez afficher du contenu local rendu dans le navigateur pour de beaux journaux des modifications, et plus encore.

Pour charger un fichier HTML local, commencez votre URL par `file:///`, suivi du chemin de fichier COURT, par exemple `/config/fancymenu/assets/cool_changelog.html`, ce qui donnera : `file:///config/fancymenu/assets/cool_changelog.html`.

Sous **Linux**, vous devez fournir le chemin absolu du fichier, mais comme coder en dur un chemin absolu casserait la mise en page, vous devez laisser un placeholder convertir dynamiquement le chemin court en chemin absolu : `file:///{"placeholder":"absolute_path","values":{"short_path":"/config/fancymenu/assets/cool_changelog.html"}}`.

Il est TRÈS IMPORTANT que vous commenciez le chemin court par `/` sous Linux, comme dans l’exemple ci-dessus. Sans cela, cela ne fonctionnera pas.

## Animateur d’éléments
Un outil puissant pour créer des animations complexes basées sur des images clés. Il peut animer la position, la taille et le point d’ancrage d’un ou de plusieurs autres éléments.

*   **Cas d’utilisation :**
    *   Créer une animation d’introduction sophistiquée où les éléments du menu glissent ou apparaissent en fondu.
    *   Faire pulser, tourner ou déplacer des éléments décoratifs le long d’un chemin.
    *   Animer une notification pour qu’elle apparaisse puis disparaisse.
*   **Fonctionnalités clés :**
    *   **Éditeur d’images clés :** Un éditeur dédié pour ajouter, modifier et séquencer des images clés sur une timeline.
    *   **Multi-cible :** Un seul animateur peut contrôler plusieurs éléments « cibles » en même temps.
    *   **Contrôle :** Les animations peuvent être configurées en boucle. Vous pouvez également choisir d’animer uniquement la position ou la taille.
    *   **Décalages de timing :** Les éléments cibles peuvent utiliser des décalages de démarrage individuels ou aléatoires.
    *   **[En savoir plus sur l’animateur d’éléments.](https://docs.fancymenu.net/en/element-animator)**

## Répétiteur
Un élément invisible qui exécute une liste d’actions à intervalle régulier (à chaque « tick »).

> Pour les nouvelles automatisations en arrière-plan dans FancyMenu 3.9.0+, envisagez d’utiliser les [Planificateurs](https://docs.fancymenu.net/en/schedulers). Les planificateurs sont globaux, plus faciles à organiser et peuvent continuer à fonctionner indépendamment d’un écran spécifique.
{.is-info}

*   **Cas d’utilisation :**
    *   Vérifier périodiquement l’état en ligne d’un serveur et mettre à jour un élément de texte.
    *   Créer un compte à rebours qui met à jour un label textuel.
    *   Exécuter un script de manière répétée pour créer des comportements personnalisés.
*   **Fonctionnalités clés :**
    *   **Contrôle du timing :** Vous pouvez définir le délai entre les ticks en millisecondes.
    *   **Modes de tick :** Peut être configuré pour s’exécuter en continu, une seule fois par session de jeu, ou une fois à chaque chargement du menu.
    *   **Asynchrone :** Peut exécuter ses [actions](https://docs.fancymenu.net/en/action-scripts) dans un thread séparé afin de ne pas impacter les performances du jeu, bien que certaines actions ne puissent pas être exécutées de cette manière.

## Audio
Un élément invisible qui lit des fichiers audio. Il peut gérer une liste de lecture de pistes et offre divers contrôles de lecture.

*   **Cas d’utilisation :**
    *   Ajouter de la musique d’ambiance personnalisée à un menu.
    *   Créer un lecteur de musique avec des boutons pour contrôler la lecture (piste suivante/précédente, volume).
    *   Jouer des ambiances sonores.
*   **Fonctionnalités clés :**
    *   **Liste de lecture :** Peut gérer plusieurs pistes audio.
    *   **Modes de lecture :** Peut lire les pistes dans l’ordre ou les mélanger (avec prise en charge du poids des pistes pour rendre certaines pistes plus fréquentes que d’autres).
    *   **Contrôle :** Prend en charge la lecture en boucle, le réglage du volume et peut être assigné à un canal audio spécifique (par ex. Master, Musique). Pour plus d’informations, consultez la page [Musique d’arrière-plan du menu](https://docs.fancymenu.net/en/background-music).

## Contrôleur de musique
Un élément invisible utilisé pour contrôler la lecture de la musique par défaut de Minecraft dans un menu spécifique.

*   **Cas d’utilisation :**
    *   Désactiver la musique de menu par défaut sur un écran où vous souhaitez lire votre propre musique personnalisée via un élément **Audio**.
    *   Empêcher la musique du monde de continuer à jouer lorsqu’un menu est ouvert en jeu.
*   **Fonctionnalités clés :**
    *   Des options séparées permettent de contrôler la « Musique du menu » vanilla et la « Musique du monde ».

## Barre de progression
Une barre personnalisable qui représente visuellement une valeur numérique.

*   **Cas d’utilisation :**
    *   Une barre de chargement qui suit la progression du chargement du monde à l’aide de `{"placeholder":"world_load_progress"}`.
    *   Des barres de vie, de faim ou d’expérience visuelles pour un HUD en jeu.
    *   Un indicateur de volume contrôlé par un élément **Curseur**.
*   **Fonctionnalités clés :**
    *   **Valeur dynamique :** La valeur de progression (0-100 ou 0.0-1.0) est définie via un champ de texte prenant en charge les [placeholders](https://docs.fancymenu.net/en/placeholders).
    *   **Apparence :** La direction de la barre (haut, bas, gauche, droite), les couleurs, les textures et le nine-slicing pour les textures de barre/arrière-plan sont tous personnalisables.
    *   **Animation :** Dispose d’une animation de remplissage fluide pour rendre les changements de progression moins brusques.

## Déplaceur
Un élément invisible que l’utilisateur peut cliquer et faire glisser pour le déplacer. D’autres éléments peuvent y être ancrés pour créer des widgets mobiles.

*   **Cas d’utilisation :**
    *   Créer une horloge ou un panneau d’information déplaçable.
    *   Permettre aux utilisateurs de personnaliser la position des éléments d’interface selon leurs préférences.
*   **Fonctionnalités clés :**
    *   **Position persistante :** Le décalage déplacé est enregistré, de sorte que l’élément reste là où l’utilisateur l’a laissé, même après le redémarrage du jeu.
    *   **Point d’ancrage :** Sert d’ancre mobile pour d’autres éléments, ce qui est une partie essentielle de [Positionner les éléments](https://docs.fancymenu.net/en/positioning-elements).

## Curseur de souris
Un élément invisible qui remplace le curseur système par une image personnalisée lorsqu’une mise en page est active.

*   **Cas d’utilisation :**
    *   Créer une interface entièrement thématisée qui correspond à l’esthétique de votre modpack.
*   **Fonctionnalités clés :**
    *   **Texture personnalisée :** Utilisez n’importe quelle image pour votre curseur.
    *   **Point chaud :** Vous pouvez définir le pixel exact de l’image qui sert de « point de clic ». Voir le guide [Curseur personnalisé](https://docs.fancymenu.net/en/custom-cursor) pour plus de détails.
