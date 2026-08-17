---
title: Éléments
description: Tout ce qu’il faut savoir sur les types d’éléments de FancyMenu.
---
# Éléments

Les éléments sont les composants de base de vos mises en page personnalisées dans FancyMenu. Vous pouvez les ajouter à n’importe quelle mise en page pour afficher des informations, ajouter de l’interactivité ou créer des effets visuels impressionnants.

# Ajouter des éléments à une mise en page

Vous pouvez ajouter un nouvel élément à votre mise en page depuis l’**éditeur de mise en page**.

1.  **Faites un clic droit** sur l’arrière-plan de l’éditeur pour ouvrir le menu contextuel.
2.  Survolez **Nouvel élément**.
3.  Une liste de tous les types d’éléments disponibles s’affiche. Cliquez sur celui que vous souhaitez ajouter.

![add_element](https://github.com/Keksuccino/FancyMenu/assets/35544624/865a66c5-76a6-404d-b746-d57802b1c12f)

Une fois l’élément ajouté, vous pouvez le déplacer, le redimensionner et le personnaliser en **faisant un clic droit** dessus pour ouvrir son menu contextuel spécifique. Pour en savoir plus sur l’organisation des éléments, consultez [Positionner les éléments](./positioning-elements) et [Identifiants des éléments](./element-identifiers).

# Les éléments en détail

Cette section répertorie les éléments intégrés de FancyMenu. Utilisez [Calques et groupes](./layers-and-groups) pour organiser leur ordre de rendu.

## Bouton
Un bouton cliquable capable d’effectuer une grande variété d’actions. C’est l’un des éléments les plus puissants et polyvalents pour créer des menus interactifs.

*   **Cas d’utilisation :**
    *   Créer un bouton « Rejoindre Discord » ou « Visiter le site web ».
    *   Ajouter un bouton de connexion rapide à un serveur spécifique.
    *   Créer une navigation personnalisée entre différents menus.
    *   Créer des boutons qui activent ou désactivent d’autres mises en page.
*   **Fonctionnalités principales :**
    *   **Actions :** Peut exécuter une séquence d’[actions](./action-scripts), comme ouvrir une URL, rejoindre un serveur, envoyer une commande de chat, reproduire la fonction d’un autre bouton ou contrôler des variables.
    *   **Apparence personnalisée :** Textures entièrement personnalisables pour les états normal, survolé et inactif. Prend en charge les arrière-plans transparents, le découpage en neuf parties, les couleurs personnalisées du libellé, les couleurs du libellé au survol, l’échelle du libellé, l’activation ou la désactivation de son ombre et les textures d’icône du bouton.
    *   **Sons :** Sons personnalisés de clic, de survol et de fin de survol.
    *   **Mode modèle :** Peut appliquer son apparence et ses propriétés à d’autres boutons Vanilla ou moddés du menu. Consultez [Modèles de boutons et de curseurs](./button-slider-templates).
    *   **Clics automatisés des widgets Vanilla/moddés :** Les widgets Vanilla et moddés existants disposent d’une propriété **Clics automatisés** qui peut déclencher leur comportement de clic d’origine un nombre choisi de fois au chargement de l’écran. Consultez [Éléments Vanilla](./vanilla-elements#automated-clicks) pour plus de détails.

## Curseur
Un curseur que les utilisateurs peuvent faire glisser pour sélectionner une valeur dans une liste ou une plage. Il peut exécuter des actions chaque fois que sa valeur change.

*   **Cas d’utilisation :**
    *   Créer un contrôle de volume personnalisé.
    *   Créer un curseur pour basculer entre différents thèmes ou images d’arrière-plan (avec le type « Liste »).
    *   Ajuster une option spécifique de Minecraft, comme la luminosité ou la distance de rendu.
*   **Fonctionnalités principales :**
    *   **Types :** Peut être une `Liste de valeurs` (par exemple « Facile », « Normal », « Difficile »), une `Plage entière` (par exemple 1-100) ou une `Plage décimale` (par exemple 0.0-1.0).
    *   **Actions dynamiques :** Exécute des actions lorsque sa valeur change. La valeur actuelle peut être utilisée avec les [variables](./variables).
    *   **Personnalisation :** Le libellé du curseur peut afficher dynamiquement sa valeur actuelle. Les textures de la poignée et de l’arrière-plan sont entièrement personnalisables, y compris les arrière-plans transparents, les options de couleur et d’échelle du libellé, l’activation ou la désactivation de l’ombre du texte et les sons personnalisés de clic et de fin de survol.

## Case à cocher
Une case à cocher standard qui peut être activée ou désactivée. Elle peut exécuter des actions lorsqu’elle est basculée.

*   **Cas d’utilisation :**
    *   Une case « J’accepte les règles ».
    *   Un paramètre permettant d’activer ou de désactiver une fonctionnalité spécifique de votre menu personnalisé.
    *   Activer ou désactiver une mise en page ou une variable.
*   **Fonctionnalités principales :**
    *   **Actions lors du basculement :** Exécute des [scripts d’action](./action-scripts) lorsque son état change. L’état actuel (`true` ou `false`) est disponible pour ses actions.
    *   **Mode variable :** Peut être directement liée à une variable FancyMenu, de sorte que l’état de la case soit lu depuis cette variable et y soit écrit.
    *   **État persistant :** Lorsque le mode variable est désactivé, la case enregistre automatiquement son état par identifiant d’élément et le restaure après le redémarrage du jeu. Ces états sont stockés dans `<game-directory>/checkbox_states.json`. En mode variable, la variable FancyMenu liée constitue à la place la source de l’état de la case.
    *   **Apparence personnalisée :** Prend en charge les textures personnalisées de l’arrière-plan (dans les états normal, survolé et inactif) ainsi que de la coche elle-même.

## Champ de saisie de texte
Un champ dans lequel les utilisateurs peuvent saisir du texte. Son contenu peut être lié à une variable FancyMenu, ce qui permet de récupérer et d’utiliser la saisie de l’utilisateur.

*   **Cas d’utilisation :**
    *   Un champ « Adresse IP du serveur » fonctionnant avec un bouton « Rejoindre le serveur ».
    *   Un champ permettant de saisir le nom d’un joueur pour un aperçu de skin personnalisé.
    *   Créer une interface de type connexion basique.
*   **Fonctionnalités principales :**
    *   **Liaison à une variable :** Enregistre le texte saisi dans une [variable](./variables) spécifiée.
    *   **Validation de la saisie :** Peut être configuré pour n’accepter que certains types de caractères, comme des chiffres, des URL ou du texte brut.
    *   **Longueur maximale :** Vous pouvez définir une limite maximale de caractères pour la saisie.
    *   **Apparence et sons :** Prend en charge la couleur d’arrière-plan personnalisée, les couleurs et l’arrondi des bordures, la couleur du texte, le texte indicatif/placeholder, la couleur du texte indicatif, les sons de survol, de fin de survol et de clic.

## Info-bulle
Une boîte de texte qui peut apparaître à une position fixe ou suivre le curseur de la souris. Sa visibilité est généralement contrôlée par les [conditions de chargement](./conditions).

*   **Cas d’utilisation :**
    *   Afficher des informations détaillées lorsqu’un utilisateur survole un bouton ou une image.
    *   Créer des conseils contextuels qui apparaissent dans certaines conditions.
    *   Afficher des informations dynamiques (comme l’état d’un serveur) à côté du curseur.
*   **Fonctionnalités principales :**
    *   **Suivi de la souris :** Peut être configurée pour suivre le pointeur de la souris.
    *   **Prise en charge de Markdown :** Le contenu de l’info-bulle prend entièrement en charge la mise en forme Markdown.
    *   **Arrière-plan personnalisé :** L’arrière-plan peut être une couleur unie ou une texture personnalisée découpée en neuf parties pour un style entièrement thématisé.

## Objet
Affiche un objet Minecraft unique, provenant du jeu de base ou d’un mod.

*   **Cas d’utilisation :**
    *   Utiliser des objets comme icônes pour des boutons ou des sélections de menu.
    *   Créer une interface graphique de boutique ou de sélection d’équipement.
    *   Afficher l’objet tenu ou l’armure d’un joueur.
*   **Fonctionnalités principales :**
    *   **Données personnalisées :** Prend en charge un nom personnalisé, une description, une quantité, l’effet de brillance d’enchantement et les données NBT. Consultez [Placeholder de données NBT](./nbt-data-placeholder).
    *   **Affichage de l’info-bulle :** Peut être configuré pour afficher l’info-bulle standard de l’objet au survol.

## Modèle JSON de bloc/objet
Affiche un modèle JSON de bloc ou d’objet provenant des ressources de Minecraft ou de sources externes.

*   **Cas d’utilisation :**
    *   Afficher un modèle 3D de pack de ressources dans un menu.
    *   Afficher des aperçus d’objets/blocs avec des textures personnalisées.
    *   Créer des éléments d’interface décoratifs basés sur des modèles.
*   **Fonctionnalités principales :**
    *   **Source du modèle :** Peut charger un modèle JSON depuis les ressources de Minecraft ou des sources externes.
    *   **Remplacement de texture :** Permet de définir une texture personnalisée.
    *   **Contrôles du rendu :** Décalage, échelle et rotation sur trois axes du modèle, rendu translucide et transformation d’interface graphique du modèle.
    *   **Éclairage :** Deux lumières configurables avec des contrôles indépendants de teinte et de rotation.

## Image
Affiche une image statique provenant d’un fichier local, d’une URL web ou d’un emplacement de ressource Minecraft.

*   **Cas d’utilisation :**
    *   Ajouter le logo d’un serveur ou la marque d’un modpack.
    *   Créer des bordures décoratives ou des cadres d’interface.
    *   Utiliser des images dans une conception d’interface plus complexe.
*   **Fonctionnalités principales :**
    *   **Découpage en neuf parties :** Redimensionne les bordures ou les panneaux sans déformer leurs coins. Consultez [Découpage en neuf parties et mosaïque](./nine-slicing-and-tiling).
    *   **Répétition de texture :** L’image peut être répétée pour remplir la zone de l’élément.
    *   **Teinte :** Vous pouvez appliquer une teinte de couleur à l’image.
    *   **Coins arrondis :** Les images qui ne sont ni découpées en neuf parties ni répétées peuvent avoir des coins arrondis.
    *   **Effet de parallaxe :** Se déplace avec la souris pour créer une profondeur visuelle. Consultez [Effet de parallaxe](./parallax).

## Texte
Un élément très polyvalent pour afficher du texte. Il peut être utilisé pour tout, des libellés sur une seule ligne aux documents multipages avec défilement.

*   **Cas d’utilisation :**
    *   Afficher les règles du serveur, des notes de mise à jour ou des messages de bienvenue.
    *   Créer des panneaux d’informations dynamiques avec des [placeholders](./placeholders), par exemple `Bienvenue, {"placeholder":"playername"} !`.
    *   Ajouter des libellés et des descriptions à votre interface.
*   **Fonctionnalités principales :**
    *   **Sources du contenu :** Le texte peut être saisi directement, chargé depuis un fichier local ou récupéré depuis une URL web.
    *   **Prise en charge de Markdown :** Prend en charge les titres, listes, blocs de code, tableaux et autres formats Markdown. Consultez [Mise en forme du texte](./text-formatting).
    *   **Défilement :** Devient automatiquement défilable si le contenu dépasse la zone de l’élément. Les barres de défilement peuvent être personnalisées ou désactivées.
    *   **Style :** Contrôle total de la couleur, de l’échelle, de l’alignement et de l’ombre du texte, ainsi que de l’espacement entre les lignes.

## Vidéo
Lit un fichier vidéo. Cet élément est idéal pour les introductions cinématiques ou les arrière-plans décoratifs en boucle.

> [!WARNING]
> L’élément Vidéo natif nécessite **Watermedia V3** et **Watermedia Binaries V3**. L’ancien élément **Vidéo [Rinku]** est obsolète.

*   **Cas d’utilisation :**
    *   Une bande-annonce animée de modpack ou de serveur.
    *   Une vidéo d’ambiance en boucle pour donner vie à votre menu.
    *   Une vidéo de tutoriel en jeu.
*   **Fonctionnalités principales :**
    *   **Sources :** Prend en charge les fichiers vidéo locaux et les URL web. Consultez [Vidéos](./video).
    *   **Contrôle de la lecture :** Peut être configurée pour se répéter automatiquement. Son volume, son canal audio et son comportement de conservation des proportions sont réglables.
    *   **Contrôle interactif :** La lecture, la position et le volume de la vidéo peuvent être contrôlés par des actions de bouton.

## Shader GLSL
Affiche un shader GLSL personnalisé à l’intérieur d’un élément.

*   **Cas d’utilisation :**
    *   Panneaux de shaders animés.
    *   Effets visuels procéduraux.
    *   Effets de menu de type Shadertoy limités au rectangle d’un élément.
*   **Fonctionnalités principales :**
    *   **Exécution du shader :** Prend en charge les shaders en une ou plusieurs passes.
    *   **Prise en charge de Shadertoy :** Peut utiliser des shaders de type Shadertoy avec `mainImage`.
    *   **Uniformes :** Expose les uniformes de FancyMenu et d’entrée. Consultez l’[API des shaders GLSL](./glsl-shader-api).

## Diaporama
Affiche une suite d’images. Ses images et son fichier de configuration `properties.txt` se trouvent dans le sous-dossier du diaporama, sous `<game-directory>/config/fancymenu/slideshows/`.

*   **Cas d’utilisation :**
    *   Une galerie tournante de captures d’écran du jeu.
    *   Mettre en avant les fonctionnalités principales d’un modpack.
    *   Un arrière-plan dynamique qui alterne entre différentes scènes.
*   **Fonctionnalités principales :**
    *   Charge des [diaporamas](./slideshows) préconfigurés.
    *   Peut être configuré pour conserver les proportions des images.

## Forme rectangulaire
Un simple rectangle de couleur unie.

*   **Cas d’utilisation :**
    *   Créer un arrière-plan semi-transparent derrière du texte pour améliorer sa lisibilité.
    *   Concevoir des panneaux et séparateurs d’interface simples.
    *   Servir de placeholder coloré pendant la conception de la mise en page.
*   **Fonctionnalités principales :**
    *   Prend en charge les couleurs HEX RGBA, les coins arrondis et le flou facultatif, permettant à la forme de servir de panneau simple, de teinte ou d’arrière-plan flouté.

## Forme circulaire
Une simple forme circulaire/elliptique de couleur unie.

*   **Cas d’utilisation :**
    *   Créer des accents circulaires, des indicateurs ou des zones d’interface douces.
    *   Créer des décorations d’interface thématiques sans fichier de texture.
*   **Fonctionnalités principales :**
    *   Prend en charge la couleur, le flou et une valeur configurable d’arrondi/exposant.

## Texte d’éclaboussure
Une reproduction du célèbre texte d’éclaboussure jaune et bondissant de Minecraft, présent sur l’écran-titre.

*   **Cas d’utilisation :**
    *   Remplacer le texte d’éclaboussure Vanilla par vos propres messages personnalisés.
    *   Ajouter un message animé accrocheur à n’importe quel menu.
*   **Fonctionnalités principales :**
    *   **Sources du contenu :** Peut utiliser les textes d’éclaboussure Vanilla par défaut, une liste de textes personnalisés saisis directement ou du texte provenant d’un fichier local.
    *   **Personnalisation :** Vous pouvez activer ou désactiver l’effet de rebond et personnaliser la couleur, l’échelle, la rotation et l’ombre du texte.

## Entité joueur
Affiche un modèle de joueur dans le menu.

*   **Cas d’utilisation :**
    *   Afficher le personnage du joueur actuel dans le menu principal.
    *   Créer un écran de sélection d’équipe ou d’aperçu de classe.
    *   Une section « profil » affichant le skin et le nom du joueur.
*   **Fonctionnalités principales :**
    *   **Apparence dynamique :** Peut copier le skin, la cape et le nom du joueur actuel. Consultez [Têtes de joueur](./player-heads).
    *   **Positions personnalisées :** Offre un contrôle précis de la rotation de la tête, du corps, des bras et des jambes. La tête et le corps peuvent également être configurés pour suivre le curseur de la souris.
    *   **Attributs :** Peut être configurée comme étant un bébé, accroupie ou dotée d’un modèle fin.

## Navigateur
Un élément qui affiche une page web en direct dans le jeu.

Cet élément nécessite l’installation et le fonctionnement du mod **[Rinku](https://modrinth.com/mod/rinku)** !

Vous pouvez télécharger Rinku depuis les pages officielles du projet sur [CurseForge](https://www.curseforge.com/minecraft/mc-mods/rinku) et [Modrinth](https://modrinth.com/mod/rinku).

*   **Cas d’utilisation :**
    *   Afficher la Dynmap en direct d’un serveur.
    *   Intégrer un lecteur vidéo YouTube.
    *   Afficher directement en jeu une page de wiki ou de documentation.
*   **Fonctionnalités principales :**
    *   **Interactivité :** Peut être rendu entièrement interactif, permettant aux utilisateurs de cliquer sur des liens, de faire défiler la page et de saisir du texte.
    *   **Contrôle des médias :** Offre des options pour couper le son des médias, répéter les vidéos et masquer les contrôles vidéo de la page chargée.

### Charger des fichiers HTML locaux
L’élément Navigateur peut charger des documents HTML locaux depuis `<game-directory>/config/fancymenu/assets/`.

Pour charger un fichier HTML local, commencez votre URL par `file:///`, suivi du CHEMIN court du fichier, par exemple `/config/fancymenu/assets/cool_changelog.html`, ce qui donne : `file:///config/fancymenu/assets/cool_changelog.html`.

Sous **Linux**, utilisez le [placeholder **Chemin absolu du fichier/dossier**](./placeholders#absolute-filefolder-path-absolute_path) au lieu d’inscrire en dur un chemin absolu propre à l’instance : `file:///{"placeholder":"absolute_path","values":{"short_path":"/config/fancymenu/assets/cool_changelog.html"}}`.

Le chemin court Linux doit commencer par `/`, comme dans l’exemple.

## Animateur d’éléments
Un outil puissant permettant de créer des animations complexes basées sur des images clés. Il peut animer la position, la taille et le point d’ancrage d’un ou plusieurs autres éléments.

*   **Cas d’utilisation :**
    *   Faire apparaître ou disparaître des éléments en les faisant glisser.
    *   Redimensionner des panneaux ou des notifications.
    *   Animer les décalages de position et les transitions d’ancrage.
*   **Fonctionnalités principales :**
    *   **Éditeur d’images clés :** Un éditeur dédié pour ajouter, modifier et séquencer des images clés sur une timeline.
    *   **Cibles multiples :** Un même animateur peut contrôler plusieurs éléments « cibles » à la fois.
    *   **Contrôle :** Les animations peuvent être configurées pour se répéter. Vous pouvez également choisir d’animer uniquement la position ou la taille.
    *   **Décalages temporels :** Les éléments cibles peuvent utiliser des décalages de démarrage individuels ou aléatoires.
    *   Consultez [Animateur d’éléments](./element-animator) pour la configuration et la modification des images clés.

## Déclencheur périodique
Un élément invisible qui exécute une liste d’actions à intervalles réguliers (à chaque « tick »).

> [!NOTE]
> Pour l’automatisation en arrière-plan, envisagez d’utiliser les [planificateurs](./schedulers). Les planificateurs sont globaux et peuvent fonctionner indépendamment d’un écran spécifique.

*   **Cas d’utilisation :**
    *   Vérifier périodiquement l’état en ligne d’un serveur et mettre à jour un élément texte.
    *   Créer un compte à rebours qui met à jour un libellé de texte.
    *   Exécuter un script de manière répétée pour créer des comportements personnalisés.
*   **Fonctionnalités principales :**
    *   **Contrôle du timing :** Vous pouvez définir le délai entre les ticks en millisecondes.
    *   **Modes de tick :** Peut être configuré pour fonctionner en continu, une seule fois par session de jeu ou une fois à chaque chargement du menu.
    *   **Asynchrone :** Peut exécuter ses [actions](./action-scripts) séparément, bien que certaines actions ne puissent pas fonctionner lorsque cette option est activée.

## Audio
Un élément invisible qui lit des fichiers audio. Il peut gérer une playlist de pistes et propose différents contrôles de lecture.

*   **Cas d’utilisation :**
    *   Ajouter une musique de fond personnalisée à un menu.
    *   Créer un lecteur de musique avec des boutons de contrôle de la lecture (piste suivante/précédente, volume).
    *   Lire des paysages sonores d’ambiance.
*   **Fonctionnalités principales :**
    *   **Playlist :** Peut gérer plusieurs pistes audio.
    *   **Modes de lecture :** Peut lire les pistes dans l’ordre ou les mélanger (avec la possibilité de pondérer les pistes pour que certaines apparaissent plus souvent que d’autres).
    *   **Contrôle :** Prend en charge la répétition, le réglage du volume et la sélection du canal audio. Consultez [Musique de fond des menus](./background-music).

## Contrôleur de musique
Un élément invisible utilisé pour contrôler la lecture de la musique par défaut de Minecraft dans un menu spécifique.

*   **Cas d’utilisation :**
    *   Désactiver la musique de menu par défaut sur un écran où vous souhaitez lire votre propre musique personnalisée via un élément [**Audio**](#audio).
    *   Empêcher la musique du monde de continuer à jouer lorsqu’un menu est ouvert en jeu.
*   **Fonctionnalités principales :**
    *   Boutons distincts permettant de contrôler la « Musique des menus » et la « Musique du monde » Vanilla.

## Barre de progression
Une barre personnalisable qui représente visuellement une valeur numérique.

*   **Cas d’utilisation :**
    *   Une barre de chargement qui suit la progression du chargement du monde à l’aide de `{"placeholder":"world_load_progress"}`.
    *   Des barres visuelles de santé, de faim ou d’expérience pour une interface en jeu.
    *   Un indicateur de volume contrôlé par un élément [**Curseur**](#slider).
*   **Fonctionnalités principales :**
    *   **Valeur dynamique :** La valeur de progression (0-100 ou 0.0-1.0) est définie via un champ de texte prenant en charge les [placeholders](./placeholders).
    *   **Apparence :** La direction de la barre (haut, bas, gauche, droite), ses couleurs, ses textures et le découpage en neuf parties des textures de la barre et de l’arrière-plan sont entièrement personnalisables.
    *   **Animation :** Offre une animation de remplissage fluide afin de rendre les changements de progression moins brusques.
    *   **Ancrage d’élément basé sur la progression :** Lorsqu’un autre élément utilise la barre de progression comme ancrage **Élément**, activez **Utiliser la progression pour l’ancrage de l’élément** afin de déplacer cet ancrage vers le bord actuel de la zone remplie. Les éléments ancrés suivent alors la progression de la barre au lieu de rester attachés à ses limites statiques.

## Déplaceur
Un élément invisible que l’utilisateur peut cliquer et faire glisser pour le déplacer. D’autres éléments peuvent y être ancrés afin de créer des widgets mobiles.

*   **Cas d’utilisation :**
    *   Créer une horloge ou un panneau d’informations déplaçable.
    *   Permettre aux utilisateurs de personnaliser la position des éléments de l’interface selon leurs préférences.
*   **Fonctionnalités principales :**
    *   **Persistance facultative :** Activez **Enregistrer le décalage de déplacement de l’utilisateur** pour conserver la position déplacée par l’utilisateur lors des ouvertures d’écran suivantes et des redémarrages du jeu. Désactivez cette option pour réinitialiser le décalage.
    *   **Point d’ancrage :** Sert d’ancrage mobile pour les autres éléments, ce qui constitue une partie importante de [Positionner les éléments](./positioning-elements).

## Curseur
Un élément invisible qui remplace le curseur système par défaut par une image personnalisée lorsqu’une mise en page est active.

*   **Cas d’utilisation :**
    *   Créer une interface entièrement thématisée correspondant à l’esthétique de votre modpack.
*   **Fonctionnalités principales :**
    *   **Texture personnalisée :** Utilisez n’importe quelle image pour votre curseur.
    *   **Point actif :** Définit le pixel exact de l’image utilisé comme point de clic. Consultez [Curseur personnalisé](./custom-cursor).
