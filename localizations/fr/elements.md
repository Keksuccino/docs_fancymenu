---
title: Éléments
description: Tout ce qu’il faut savoir sur les types d’éléments de FancyMenu.
---

# Éléments

Les éléments sont les briques de base de vos mises en page personnalisées dans FancyMenu. Vous pouvez les ajouter à n’importe quelle mise en page pour afficher des informations, ajouter de l’interactivité ou créer de superbes effets visuels.

# Ajouter des éléments à une mise en page

Vous pouvez ajouter un nouvel élément à votre mise en page depuis l’**éditeur de mise en page**.

1.  **Faites un clic droit** sur l’arrière-plan de l’éditeur pour ouvrir le menu contextuel.
2.  Survolez **Nouvel élément**.
3.  Une liste de tous les types d’éléments disponibles apparaît. Cliquez sur celui que vous souhaitez ajouter.

![add_element](https://github.com/Keksuccino/FancyMenu/assets/35544624/865a66c5-76a6-404d-b746-d57802b1c12f)

Une fois l’élément ajouté, vous pouvez le déplacer, le redimensionner et le personnaliser en **faisant un clic droit** dessus pour ouvrir son menu contextuel spécifique. Pour en savoir plus sur la disposition des éléments, consultez [Positionnement des éléments](./positioning-elements) et [Identifiants d’éléments](./element-identifiers).

# Détails des éléments

Cette section répertorie les éléments intégrés de FancyMenu. Utilisez [Couches et groupes](./layers-and-groups) pour organiser leur ordre d’affichage.

## Bouton
Un bouton cliquable qui peut effectuer une grande variété d’actions. C’est l’un des éléments les plus puissants et les plus polyvalents pour créer des menus interactifs.

*   **Cas d’utilisation :**
    *   Créer un bouton « Rejoindre Discord » ou « Visiter le site web ».
    *   Ajouter un bouton de connexion rapide pour un serveur spécifique.
    *   Construire une navigation personnalisée entre différents menus.
    *   Créer des boutons qui activent ou désactivent d’autres mises en page.
*   **Fonctionnalités clés :**
    *   **Actions :** Peut exécuter une séquence d’[actions](./action-scripts), comme ouvrir une URL, rejoindre un serveur, envoyer une commande de chat, imiter la fonction d’un autre bouton ou contrôler des variables.
    *   **Apparence personnalisée :** Textures entièrement personnalisables pour les états normal, survolé et inactif. Prend en charge les fonds transparents, le nine-slicing, les couleurs de label personnalisées, les couleurs de label au survol, l’échelle du label, l’activation ou non de l’ombre du label et les textures d’icône du bouton.
    *   **Sons :** Sons personnalisés au clic, au survol et à la sortie du survol.
    *   **Mode modèle :** Peut appliquer son apparence et ses propriétés à d’autres boutons Vanilla ou moddés du menu. Voir [Modèles de bouton et de curseur](./button-slider-templates).
    *   **Clics automatiques sur widgets Vanilla/moddés :** Les widgets Vanilla et moddés existants disposent d’une propriété **Clics automatiques** qui peut déclencher leur comportement de clic d’origine un nombre choisi de fois lors du chargement de l’écran. Voir [Éléments Vanilla](./vanilla-elements#automated-clicks) pour plus de détails.

## Curseur
Un curseur que les utilisateurs peuvent faire glisser pour sélectionner une valeur dans une liste ou une plage. Il peut exécuter des actions chaque fois que sa valeur change.

*   **Cas d’utilisation :**
    *   Créer un contrôle de volume personnalisé.
    *   Un curseur pour changer de thème ou d’image de fond (en utilisant le type « Liste »).
    *   Ajuster une option Minecraft spécifique, comme la luminosité ou la distance d’affichage.
*   **Fonctionnalités clés :**
    *   **Types :** Peut être une `Liste de valeurs` (par ex. « Facile », « Normal », « Difficile »), une `Plage entière` (par ex. 1–100) ou une `Plage décimale` (par ex. 0,0–1,0).
    *   **Actions dynamiques :** Exécute des actions lorsque sa valeur change. La valeur actuelle peut être utilisée avec les [Variables](./variables).
    *   **Personnalisation :** Le label du curseur peut afficher dynamiquement sa valeur actuelle. La texture du curseur et de l’arrière-plan est entièrement personnalisable, y compris les fonds transparents, les options de couleur/d’échelle du label, l’activation ou non de l’ombre du texte et les sons personnalisés au clic/à la sortie du survol.

## Case à cocher
Une case à cocher standard que l’on peut activer ou désactiver. Elle peut exécuter des actions lorsqu’elle est modifiée.

*   **Cas d’utilisation :**
    *   Une case « J’accepte les règles ».
    *   Un réglage pour activer ou désactiver une fonctionnalité spécifique dans votre menu personnalisé.
    *   Activer ou désactiver une mise en page ou une variable.
*   **Fonctionnalités clés :**
    *   **Actions lors du changement :** Exécute des [scripts d’actions](./action-scripts) lorsque son état change. L’état actuel (`true` ou `false`) est disponible pour ses actions.
    *   **Mode variable :** Peut être liée directement à une variable FancyMenu, ce qui fait que l’état de la case est lu depuis cette variable et y est écrit.
    *   **État persistant :** Lorsque le mode variable est désactivé, la case enregistre automatiquement son état par identifiant d’élément et le restaure après le redémarrage du jeu. Ces états sont stockés dans `<game-directory>/checkbox_states.json`. En mode variable, la variable FancyMenu liée est la source de l’état de la case.
    *   **Apparence personnalisée :** Prend en charge des textures personnalisées pour l’arrière-plan (dans les états normal, survolé et inactif) ainsi que pour la coche elle-même.

## Champ de saisie de texte
Un champ où les utilisateurs peuvent saisir du texte. Son contenu peut être lié à une variable FancyMenu, ce qui vous permet de capturer et d’utiliser la saisie utilisateur.

*   **Cas d’utilisation :**
    *   Un champ « IP du serveur » qui fonctionne avec un bouton « Rejoindre le serveur ».
    *   Un champ pour saisir le nom d’un joueur dans un aperçu de skin personnalisé.
    *   Créer une interface de type connexion basique.
*   **Fonctionnalités clés :**
    *   **Lien avec une variable :** Stocke le texte saisi dans une [variable](./variables) spécifiée.
    *   **Validation de la saisie :** Peut être configuré pour n’accepter que certains types de caractères, comme des nombres, des URL ou du texte brut.
    *   **Longueur maximale :** Vous pouvez définir une limite maximale de caractères pour la saisie.
    *   **Apparence et sons :** Prend en charge une couleur d’arrière-plan personnalisée, des couleurs de bordure, l’arrondi de la bordure, la couleur du texte, le texte d’indication/de remplacement, la couleur de l’indication, les sons au survol, à la sortie du survol et au clic.

## Info-bulle
Une boîte de texte qui peut apparaître à une position fixe ou suivre le curseur de la souris. Sa visibilité est normalement contrôlée avec des [conditions de chargement](./conditions).

*   **Cas d’utilisation :**
    *   Afficher des informations détaillées lorsqu’un utilisateur survole un bouton ou une image.
    *   Créer des conseils d’aide contextuels qui apparaissent sous certaines conditions.
    *   Afficher des informations dynamiques (comme l’état du serveur) à côté du curseur.
*   **Fonctionnalités clés :**
    *   **Suivi de la souris :** Peut suivre le pointeur de la souris.
    *   **Prise en charge du Markdown :** Le contenu de l’info-bulle prend en charge le formatage Markdown complet.
    *   **Arrière-plan personnalisé :** L’arrière-plan peut être une couleur unie ou une texture personnalisée avec nine-slicing pour un rendu entièrement thématique.

## Objet
Affiche un seul objet Minecraft, Vanilla ou provenant d’un mod.

*   **Cas d’utilisation :**
    *   Utiliser des objets comme icônes pour des boutons ou des sélections de menu.
    *   Créer une interface de boutique ou de sélection de kit.
    *   Afficher l’objet tenu ou l’armure d’un joueur.
*   **Fonctionnalités clés :**
    *   **Données personnalisées :** Prend en charge un nom personnalisé, une lore, une quantité, un effet visuel d’enchantement et des données NBT. Voir le [placeholder de données NBT](./nbt-data-placeholder).
    *   **Affichage de l’infobulle :** Peut être configuré pour afficher l’infobulle standard de l’objet au survol.

## Modèle JSON de bloc/objet
Rend un modèle JSON de bloc ou d’objet provenant des ressources de Minecraft ou de sources externes.

*   **Cas d’utilisation :**
    *   Afficher un modèle de pack de ressources 3D dans un menu.
    *   Montrer des aperçus de blocs/objets avec des textures personnalisées.
    *   Créer des éléments d’interface décoratifs basés sur des modèles.
*   **Fonctionnalités clés :**
    *   **Source du modèle :** Peut charger un JSON de modèle depuis les ressources de Minecraft ou des sources externes.
    *   **Remplacement de texture :** Permet de définir une texture personnalisée.
    *   **Contrôles de rendu :** Décalage du modèle, échelle, rotation sur trois axes, rendu translucide et transformation GUI du modèle.
    *   **Éclairage :** Deux lumières configurables avec des contrôles indépendants de teinte et de rotation.

## Image
Affiche une image statique depuis un fichier local, une URL web ou un emplacement de ressource Minecraft.

*   **Cas d’utilisation :**
    *   Ajouter un logo de serveur ou l’identité visuelle d’un modpack.
    *   Créer des bordures décoratives ou des cadres d’interface.
    *   Utiliser des images dans le cadre d’une conception d’interface plus complexe.
*   **Fonctionnalités clés :**
    *   **Nine-slicing :** Met à l’échelle les bordures ou les panneaux sans déformer les coins. Voir [Nine-Slicing et tiling](./nine-slicing-and-tiling).
    *   **Répétition de texture :** L’image peut être mise en mosaïque pour remplir la zone de l’élément.
    *   **Teinte :** Vous pouvez appliquer une teinte de couleur à l’image.
    *   **Coins arrondis :** Les images non découpées en nine-slicing et non répétées peuvent avoir des coins arrondis.
    *   **Effet de parallaxe :** Se déplace avec la souris pour créer une impression de profondeur visuelle. Voir [Effet de parallaxe](./parallax).

## Texte
Un élément très polyvalent pour afficher du texte. Il peut servir à tout, de simples libellés sur une seule ligne à des documents multipages et défilables.

*   **Cas d’utilisation :**
    *   Afficher les règles d’un serveur, les notes de mise à jour ou des messages de bienvenue.
    *   Créer des panneaux d’information dynamiques à l’aide de [placeholders](./placeholders), par exemple `Welcome, {"placeholder":"playername"}!`.
    *   Ajouter des libellés et des descriptions à votre interface.
*   **Fonctionnalités clés :**
    *   **Sources du contenu :** Le texte peut être saisi directement, chargé depuis un fichier local ou récupéré depuis une URL web.
    *   **Prise en charge du Markdown :** Prend en charge les titres, listes, blocs de code, tableaux et autres formats Markdown. Voir [Formatage du texte](./text-formatting).
    *   **Défilement :** Devient automatiquement défilable si le contenu dépasse la zone de l’élément. Les barres de défilement peuvent être personnalisées ou désactivées.
    *   **Mise en forme :** Contrôle complet de la couleur du texte, de l’échelle, de l’alignement, de l’ombre et de l’interligne.

## Vidéo
Lit un fichier vidéo. C’est idéal pour des intros cinématiques ou des arrière-plans animés en boucle.

> [!WARNING]
> L’élément Vidéo natif nécessite **Watermedia V3** et **Watermedia Binaries V3**. L’ancien élément **Video [MCEF]** est obsolète.

*   **Cas d’utilisation :**
    *   Une bande-annonce animée de modpack ou de serveur.
    *   Une vidéo d’ambiance en boucle pour donner de la vie à votre menu.
    *   Une vidéo tutorielle en jeu.
*   **Fonctionnalités clés :**
    *   **Sources :** Prend en charge les fichiers vidéo locaux et les URL web. Voir [Vidéos](./video).
    *   **Contrôle de la lecture :** Peut être configuré pour boucler automatiquement. Son volume, son canal audio et son comportement de conservation du ratio d’aspect sont ajustables.
    *   **Contrôle interactif :** La lecture, le temps de recherche et le volume de la vidéo peuvent être contrôlés via des actions de bouton.

## Shader GLSL
Rend un shader GLSL personnalisé dans un élément.

*   **Cas d’utilisation :**
    *   Panneaux shader animés.
    *   Effets visuels procéduraux.
    *   Effets de menu façon Shadertoy découpés dans le rectangle d’un élément.
*   **Fonctionnalités clés :**
    *   **Exécution du shader :** Prend en charge les shaders à passe unique et à plusieurs passes.
    *   **Prise en charge de Shadertoy :** Peut utiliser des shaders `mainImage` de type Shadertoy.
    *   **Uniforms :** Expose les uniforms de FancyMenu et d’entrée. Voir l’[API du shader GLSL](./glsl-shader-api).

## Diaporama
Affiche une séquence d’images. Ses images et son fichier de configuration `properties.txt` se trouvent dans le sous-répertoire propre au diaporama sous `<game-directory>/config/fancymenu/slideshows/`.

*   **Cas d’utilisation :**
    *   Une galerie rotative de captures d’écran en jeu.
    *   Mettre en avant les fonctionnalités clés d’un modpack.
    *   Un arrière-plan dynamique qui alterne entre différentes scènes.
*   **Fonctionnalités clés :**
    *   Charge des [diaporamas](./slideshows) préconfigurés.
    *   Peut être configuré pour conserver le ratio d’aspect des images.

## Forme rectangulaire
Un simple rectangle de couleur unie.

*   **Cas d’utilisation :**
    *   Créer un arrière-plan semi-transparent derrière du texte pour améliorer la lisibilité.
    *   Concevoir des panneaux et des séparateurs d’interface simples.
    *   Servir d’espace réservé coloré pendant la conception de la mise en page.
*   **Fonctionnalités clés :**
    *   Prend en charge les couleurs HEX RGBA, les coins arrondis et un flou optionnel, ce qui permet à la forme de servir de panneau simple, de teinte ou d’arrière-plan flouté.

## Forme circulaire
Une simple forme de cercle/ellipse de couleur unie.

*   **Cas d’utilisation :**
    *   Créer des accents circulaires, des indicateurs ou des zones d’interface douces.
    *   Construire des décorations d’interface thématiques sans fichier de texture.
*   **Fonctionnalités clés :**
    *   Prend en charge la couleur, le flou et une valeur de rondeur/exposant configurable.

## Texte d’écran titre
Une recréation du célèbre texte d’écran titre de Minecraft, jaune et rebondissant.

*   **Cas d’utilisation :**
    *   Remplacer le texte d’écran titre Vanilla par vos propres messages personnalisés.
    *   Ajouter un message animé et accrocheur à n’importe quel menu.
*   **Fonctionnalités clés :**
    *   **Sources du contenu :** Peut utiliser les messages par défaut de Vanilla, une liste de textes personnalisés saisis directement ou du texte provenant d’un fichier local.
    *   **Personnalisation :** Vous pouvez activer ou désactiver l’effet de rebond et personnaliser la couleur, l’échelle, la rotation et l’ombre du texte.

## Entité joueur
Rend un modèle de joueur dans le menu.

*   **Cas d’utilisation :**
    *   Afficher le personnage du joueur actuel dans le menu principal.
    *   Créer un écran de sélection d’équipe ou d’aperçu de classe.
    *   Une section « profil » montrant le skin et le nom du joueur.
*   **Fonctionnalités clés :**
    *   **Apparence dynamique :** Peut copier le skin, la cape et le nom du joueur actuel. Voir [Têtes de joueur](./player-heads).
    *   **Poses personnalisées :** Offre un contrôle précis de la rotation de la tête, du corps, des bras et des jambes. La tête et le corps peuvent aussi suivre le pointeur de la souris.
    *   **Attributs :** Peut être configuré comme bébé, accroupi ou avec un modèle fin.

## Navigateur
Un élément qui affiche une page web en direct dans le jeu.

Cet élément nécessite que le mod **MCEF (Minecraft Chromium Embedded Framework)** soit installé et fonctionne correctement !

Vous pouvez télécharger MCEF depuis les pages officielles du projet sur [CurseForge](https://www.curseforge.com/minecraft/mc-mods/mcef) et [Modrinth](https://modrinth.com/mod/mcef).

Pour les versions plus récentes de Minecraft (1.21.5+), les projets officiels MCEF ne fournissent pas de builds, mais il existe un fork avec des builds pour les dernières versions de Minecraft, disponible [ici](https://www.curseforge.com/minecraft/mc-mods/mcef-keksuccino) (CurseForge) et [ici](https://modrinth.com/mod/mcef-keksuccino) (Modrinth). Ce fork est maintenu par Keksuccino afin de proposer des builds pour les dernières versions de Minecraft aussi rapidement que possible.

*   **Cas d’utilisation :**
    *   Afficher le Dynmap en direct d’un serveur.
    *   Intégrer un lecteur vidéo YouTube.
    *   Afficher un wiki ou une page de documentation directement en jeu.
*   **Fonctionnalités clés :**
    *   **Interactivité :** Peut être rendu entièrement interactif, permettant aux utilisateurs de cliquer sur des liens, faire défiler et saisir du texte.
    *   **Contrôle des médias :** Propose des options pour couper le son des médias, boucler les vidéos et masquer les contrôles vidéo sur la page chargée.

### Chargement de fichiers HTML locaux
L’élément Navigateur peut charger des documents HTML locaux depuis `<game-directory>/config/fancymenu/assets/`.

Pour charger un fichier HTML local, commencez votre URL par `file:///`, suivi du chemin de fichier COURT, par exemple `/config/fancymenu/assets/cool_changelog.html`, ce qui donne : `file:///config/fancymenu/assets/cool_changelog.html`.

Sous **Linux**, utilisez le [placeholder de chemin absolu de fichier/dossier](./placeholders#absolute-filefolder-path-absolute_path) au lieu de coder en dur un chemin absolu propre à l’instance : `file:///{"placeholder":"absolute_path","values":{"short_path":"/config/fancymenu/assets/cool_changelog.html"}}`.

Le chemin court Linux doit commencer par `/`, comme indiqué dans l’exemple.

## Animateur d’éléments
Un outil puissant pour créer des animations complexes basées sur des images clés. Il peut animer la position, la taille et le point d’ancrage d’un ou de plusieurs autres éléments.

*   **Cas d’utilisation :**
    *   Faire entrer ou sortir des éléments en les faisant glisser.
    *   Redimensionner des panneaux ou des notifications.
    *   Animer des décalages de position et des transitions d’ancrage.
*   **Fonctionnalités clés :**
    *   **Éditeur d’images clés :** Un éditeur dédié pour ajouter, modifier et enchaîner des images clés sur une chronologie.
    *   **Cibles multiples :** Un seul animateur peut नियंत्रler plusieurs éléments « cibles » à la fois.
    *   **Contrôle :** Les animations peuvent être configurées en boucle. Vous pouvez aussi choisir d’animer uniquement la position ou la taille.
    *   **Décalages de timing :** Les éléments cibles peuvent utiliser des décalages de démarrage individuels ou aléatoires.
    *   Voir [Animateur d’éléments](./element-animator) pour la configuration et l’édition des images clés.

## Déclencheur
Un élément invisible qui exécute une liste d’actions à intervalle régulier (à chaque « tick »).

> [!NOTE]
> Pour l’automatisation en arrière-plan, pensez à utiliser les [Planificateurs](./schedulers). Les planificateurs sont globaux et peuvent fonctionner indépendamment d’un écran spécifique.

*   **Cas d’utilisation :**
    *   Vérifier périodiquement si un serveur est en ligne et mettre à jour un élément de texte.
    *   Créer un compte à rebours qui met à jour un libellé de texte.
    *   Exécuter un script de façon répétée pour créer des comportements personnalisés.
*   **Fonctionnalités clés :**
    *   **Contrôle du timing :** Vous pouvez définir le délai entre les ticks en millisecondes.
    *   **Modes de tick :** Peut être configuré pour fonctionner en continu, une seule fois par session de jeu, ou une fois à chaque chargement du menu.
    *   **Asynchrone :** Peut exécuter ses [actions](./action-scripts) séparément, bien que certaines actions ne puissent pas s’exécuter lorsque cette option est activée.

## Audio
Un élément invisible qui lit des fichiers audio. Il peut gérer une liste de lecture de pistes et offre divers contrôles de lecture.

*   **Cas d’utilisation :**
    *   Ajouter une musique de fond personnalisée à un menu.
    *   Créer un lecteur de musique avec des boutons pour contrôler la lecture (piste suivante/précédente, volume).
    *   Jouer des ambiances sonores.
*   **Fonctionnalités clés :**
    *   **Liste de lecture :** Peut gérer plusieurs pistes audio.
    *   **Modes de lecture :** Peut lire les pistes dans l’ordre ou en mode aléatoire (avec prise en charge du poids des pistes pour rendre certaines pistes plus fréquentes que d’autres).
    *   **Contrôle :** Prend en charge la boucle, le réglage du volume et la sélection du canal sonore. Voir [Musique de fond du menu](./background-music).

## Contrôleur de musique
Un élément invisible utilisé pour contrôler la lecture de la musique par défaut de Minecraft dans un menu spécifique.

*   **Cas d’utilisation :**
    *   Désactiver la musique de menu par défaut sur un écran où vous souhaitez jouer votre propre musique personnalisée via un [élément **Audio**](#audio).
    *   Empêcher la musique du monde de continuer à jouer lorsqu’un menu est ouvert en jeu.
*   **Fonctionnalités clés :**
    *   Des bascules distinctes pour contrôler la « Menu Music » et la « World Music » de Vanilla.

## Barre de progression
Une barre personnalisable qui représente visuellement une valeur numérique.

*   **Cas d’utilisation :**
    *   Une barre de chargement qui suit la progression du chargement du monde grâce à `{"placeholder":"world_load_progress"}`.
    *   Des barres visuelles de santé, de faim ou d’expérience pour une interface HUD en jeu.
    *   Un indicateur de volume contrôlé par un [élément **Curseur**](#slider).
*   **Fonctionnalités clés :**
    *   **Valeur dynamique :** La valeur de progression (0-100 ou 0,0-1,0) est définie via un champ de texte prenant en charge les [placeholders](./placeholders).
    *   **Apparence :** La direction de la barre (haut, bas, gauche, droite), les couleurs, les textures et le nine-slicing pour les textures de barre/arrière-plan sont tous personnalisables.
    *   **Animation :** Dispose d’une animation de remplissage fluide pour rendre les changements de progression moins brusques.
    *   **Ancrage d’élément basé sur la progression :** Lorsqu’un autre élément utilise la barre de progression comme ancre **Élément**, activez **Utiliser la progression pour l’ancre d’élément** pour déplacer cette ancre vers le bord actuel de la zone remplie. Les éléments ancrés se déplacent alors avec la progression de la barre au lieu de rester attachés aux limites statiques de la barre de progression.

## Déplaceur
Un élément invisible que l’utilisateur peut cliquer et faire glisser pour le déplacer. D’autres éléments peuvent s’y ancrer pour créer des widgets déplaçables.

*   **Cas d’utilisation :**
    *   Créer une horloge ou un panneau d’information déplaçable.
    *   Permettre aux utilisateurs de personnaliser la position des éléments d’interface selon leurs préférences.
*   **Fonctionnalités clés :**
    *   **Persistance facultative :** Activez **Enregistrer le décalage de déplacement de l’utilisateur** pour conserver la position déplacée par l’utilisateur entre les ouvertures d’écran et les redémarrages du jeu. Désactivez-la pour réinitialiser le décalage.
    *   **Point d’ancrage :** Agit comme une ancre déplaçable pour d’autres éléments, ce qui est une partie essentielle du [positionnement des éléments](./positioning-elements).

## Curseur de souris
Un élément invisible qui remplace le curseur système par défaut par une image personnalisée lorsqu’une mise en page est active.

*   **Cas d’utilisation :**
    *   Créer une interface entièrement thématique qui correspond à l’esthétique de votre modpack.
*   **Fonctionnalités clés :**
    *   **Texture personnalisée :** Utilisez n’importe quelle image pour votre curseur.
    *   **Hotspot :** Définit le pixel exact de l’image utilisé comme point de clic. Voir [Curseur personnalisé](./custom-cursor).
