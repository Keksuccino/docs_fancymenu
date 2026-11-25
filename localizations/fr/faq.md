---
title: FAQ
description: Foire aux questions.
sourceBlobSha: 4ae872e8e4a54fc6a89de7c87c8a137a89292455
---
# FAQ

### J’ai besoin d’aide pour résoudre un problème. Quelles informations dois-je fournir ?

Pour obtenir la meilleure aide possible, fournissez autant de contexte que possible :
1.  **Une description claire du problème :** Qu’espériez-vous voir se produire, et que s’est-il réellement passé ?
2.  **Votre fichier `latest.log` :** Vous le trouverez dans `<game-directory>/logs/latest.log`. **N’envoyez pas de journal de crash**, sauf si on vous le demande expressément ; `latest.log` contient généralement le contexte nécessaire. Utilisez un site comme https://gist.github.com pour le partager.
3.  **Votre version de Minecraft :** (par ex. 1.20.1)
4.  **Votre chargeur de mods et sa version :** (par ex. Forge 47.2.0, Fabric 0.15.7)
5.  **Votre version de FancyMenu :** (par ex. 3.5.2)
6.  **Des captures d’écran ou des vidéos** du problème peuvent également être très utiles.

> [!TIP]
> Vous demandez de l’aide à Alice ou à une autre IA ? Ajoutez un [Export for AI](/export-for-ai) de ce qui ne fonctionne pas. L’IA pourra voir exactement comment votre configuration est faite, et l’export contient déjà les versions de Minecraft, du chargeur de mods et de FancyMenu.

### Comment modifier la superposition des éléments (placer un élément devant ou derrière un autre) ?

- **Vos propres éléments :** faites glisser leurs calques dans le widget Layers de l’éditeur de mise en page, ou faites un clic droit sur un élément et sélectionnez **Move One Layer Up** ou **Move One Layer Down**. Consultez [Calques et groupes](/layout-editor#layers-and-groups).
- **Vos éléments et les éléments vanilla :** l’ordre des éléments vanilla ne peut pas être modifié. Pour placer tous vos éléments derrière eux, par exemple une image d’arrière-plan derrière les boutons par défaut, faites un clic droit sur l’arrière-plan de l’éditeur et réglez **Custom Elements Behind Vanilla** sur **Enabled**.

### Puis-je exclure certains boutons d’un modèle universel de boutons ?

**Non. Si des textures personnalisées sont définies pour un bouton de modèle, elles sont toujours partagées avec tous les éléments concernés. Vous ne pouvez pas exclure des boutons individuellement.**

### Comment faire en sorte qu’un bouton déclenche une action quand on clique dessus ?

Utilisez un [**script d’action**](/action-scripts).
1.  Faites un clic droit sur le bouton dans l’éditeur.
2.  Sélectionnez **Edit Action Script**.
3. Cliquez sur **Add Action** et choisissez une action, comme [**Open Screen or Custom GUI**](/action-scripts#open-screen-or-custom-gui), [**Join Server**](/action-scripts#join-server) ou [**Set Variable Value**](/action-scripts#set-variable-value-fm-variable).

### Puis-je créer un tout nouvel écran de menu à partir de zéro ?

Oui, avec une [interface graphique personnalisée](/custom-guis) :

1. Ouvrez **menu bar -> Customization -> Custom GUIs -> Manage Custom GUIs**, puis cliquez sur **New GUI**.
2. Donnez-lui un identifiant, comme `modpack_info`, puis cliquez sur **Done**.
3. Ouvrez-la avec **Open GUI** et créez sa mise en page comme pour n’importe quel autre menu.
4. Ouvrez-la depuis un bouton avec l’action [**Open Screen or Custom GUI**](/action-scripts#open-screen-or-custom-gui) et son identifiant.

### Mon jeu met longtemps à se charger après l’activation du préchargement.

C’est normal. Le préchargement de ressources volumineuses, comme des animations haute résolution ou des sons, au démarrage initial augmente naturellement le temps de chargement du jeu.

### Mon animation utilise beaucoup de RAM ou ralentit le jeu !

Les images de grande taille et les fréquences d’images élevées consomment beaucoup de mémoire et de ressources. Donnez aux images une taille proche de celle de leur affichage à l’écran et réduisez le nombre d’images par seconde. Consultez [Animations](/animations#performance). Pour les clips longs avec du son, utilisez plutôt une [vidéo](/video).

### FancyMenu est-il compatible avec OptiFine ?

Non. OptiFine est **incompatible** et est connu pour provoquer des problèmes avec de nombreux mods, dont FancyMenu. Il est fortement recommandé d’utiliser des alternatives modernes comme Sodium/Embeddium + Iris/Oculus.
Consultez [Alternatives à OptiFine](/optifine-alternatives).

### Mon jeu plante. Comment savoir si le problème vient d’un conflit entre mods ?

Le meilleur moyen de vérifier s’il y a un conflit entre mods est de **lancer le jeu avec uniquement FancyMenu et ses dépendances** (Konkrete, Melody). Si le jeu ne plante plus, réactivez vos autres mods par petits groupes jusqu’à ce que le plantage se reproduise, afin d’identifier le mod en conflit.

### Un bouton ajouté par un autre mod disparaît ou ne fonctionne pas lorsque j’essaie de le modifier.

Certains mods ajoutent des widgets d’une manière que FancyMenu ne peut pas détecter ni personnaliser. Consultez [Éléments vanilla et de mods](/vanilla-elements) et, pour les écrans basés sur des listes, [Personnaliser les écrans défilants](/customizing-scrollable-screens). Si le widget n’apparaît toujours pas, le mod qui l’ajoute doit l’exposer en tant que widget d’écran pris en charge.

### Puis-je utiliser des mises en page FancyMenu sur un serveur ?

Les mises en page et personnalisations visuelles sont enregistrées sur le client du joueur ; un serveur ne peut pas les imposer à un client qui n’est pas configuré. Distribuez-les dans le cadre d’un modpack. Installez FancyMenu sur le serveur si vous avez besoin des [commandes serveur](/commands), de [FM Data](/fm-data), de l’[accès aux données NBT côté serveur](/nbt-data-placeholder#server-side-placeholder), des règles de jeu, des structures ou des écouteurs côté serveur.

### Quelle est la différence entre FancyMenu v2 (pour les anciennes versions de Minecraft) et v3 ?

FancyMenu v3 est une réécriture complète qui apporte de nombreuses nouvelles fonctionnalités, une architecture plus stable et de meilleures performances. La v2 est obsolète, n’est plus prise en charge et ne dispose pas de nombreuses fonctionnalités, comme les espaces réservés avancés et les scripts. Il est fortement recommandé d’utiliser la v3 avec une version moderne de Minecraft (1.18.2+). Les mises en page v2 peuvent être converties automatiquement en v3 lors de leur chargement, mais certaines corrections manuelles peuvent être nécessaires.

### Où trouver des mises en page et des modèles déjà créés ?

La communauté FancyMenu partage des configurations complètes dans le salon [`#layout-templates`](https://discord.com/channels/704163135787106365/1234093433795383316) du serveur Discord officiel (« Kekscord »). Installez-les comme profils distincts ; consultez [Modèles de mise en page](/profiles#layout-templates).

### Comment faire en sorte que l’entité du joueur s’affiche derrière les autres éléments ?

En général, il est impossible de forcer un [élément Entité du joueur](/elements#player-entity) à passer derrière les éléments 2D classiques à l’aide du [widget Layers](/layout-editor#layers-and-groups). Son moteur de rendu peut ignorer l’ordre normal des calques de l’interface. Concevez votre mise en page en tenant compte de cette limite ou utilisez une image pré-rendue lorsque l’ordre des calques doit être strictement respecté.

### Il ne reste qu’une seule jambe à mon entité du joueur ! Que s’est-il passé ?

Il s’agit d’un problème d’affichage, probablement causé par un conflit avec un autre mod qui modifie les animations ou les modèles du joueur. Vérifiez les paramètres de pose de l’entité du joueur pour voir si ses jambes ont été tournées ou déplacées par inadvertance.

### Comment créer un délai entre les actions d’un script ?

Faites un clic droit dans la zone de script de l’éditeur de scripts d’action, cliquez sur **Add EXECUTE LATER Block** et placez-y les actions qui doivent attendre. Elles s’exécutent une fois le délai écoulé, en millisecondes, tandis que le reste du script continue immédiatement. Consultez [Execute Later](/action-scripts#execute-later).

Pour les actions qui doivent se répéter, utilisez les [planificateurs](/schedulers).

### Puis-je personnaliser les menus du mod Create ?

Non. La personnalisation des écrans de Create est volontairement désactivée. Consultez [Écrans dont la personnalisation est volontairement désactivée](/incompatibility-list#screens-where-customization-is-intentionally-disabled).

### Quelle résolution est recommandée pour les images d’arrière-plan et les textures des boutons ?

Arrière-plans : une image standard de 1920 × 1080 (1080p) constitue un excellent point de départ et s’adaptera bien à la plupart des utilisateurs.
Boutons : la plupart des boutons vanilla mesurent environ 150 à 200 pixels de large et 20 pixels de haut. Pour assurer une certaine cohérence, il est recommandé de donner aux textures personnalisées une taille similaire.

### Est-il possible d’ouvrir automatiquement un menu ou d’exécuter une commande lorsqu’un joueur termine un objectif en jeu (comme une quête) ?
FancyMenu dispose de nombreux [écouteurs d’événements de jeu intégrés](/listeners), mais il n’existe pas d’écouteur générique pour tous les systèmes de quêtes tiers. Si le mod de quêtes prend en charge les récompenses sous forme de commandes, utilisez-en une pour lancer [`/openguiscreen`](/commands#openguiscreen), [`/fmvariable`](/commands#fmvariable) ou une autre [commande FancyMenu](/commands) adaptée.

### Comment désactiver un bouton ou le rendre « grisé » ?

Vous pouvez contrôler l’état actif d’un bouton à l’aide de [conditions](/conditions).
Faites un clic droit sur le bouton dans l’éditeur et sélectionnez **Control Active State**.
Ajoutez une condition qui doit être remplie pour que le bouton soit actif. Pour le désactiver de façon permanente, utilisez [**Is Number**](/conditions#is-number) afin de vérifier si 0 est égal à 1.
Le bouton utilisera alors sa texture « Inactive Background » et ne pourra pas être cliqué.

### Comment supprimer l’en-tête et le pied de page (les bandes texturées de terre) des écrans défilants ?

Dans l’éditeur de mise en page, ouvrez **Layout Properties -> Header/Footer Customizations**. Définissez les textures comme transparentes. Cette option peut être indisponible sur certains écrans moddés.

### Je ne peux pas créer de mise en page « pour l’écran actuel ». Le bouton est grisé.

Activez d’abord les personnalisations pour cet écran : cliquez sur **menu bar -> Customization -> Current Screen Customization** pour afficher **Enabled**.

### Je ne peux personnaliser aucun élément d’un écran lorsque je l’ouvre dans l’éditeur. L’écran est vide.

Vous avez peut-être créé une [mise en page universelle](/universal-layouts) au lieu d’une mise en page **pour l’écran actuel**.

Il peut aussi s’agir d’un [écran défilant](/customizing-scrollable-screens), que FancyMenu ne peut pas personnaliser par défaut.

Enfin, il peut s’agir d’un écran provenant d’un mod qui ajoute des éléments d’une manière non vanilla, ce qui empêche FancyMenu de les personnaliser.

### Des cases grises bizarres apparaissent sur mon élément Texte.

Ce sont les barres de défilement de l’[élément Texte](/elements#text). Elles apparaissent lorsque le texte ne tient pas dans l’élément, afin que les joueurs puissent le faire défiler.

- Agrandissez l’élément ou raccourcissez le texte pour les faire disparaître.
- Faites un clic droit sur l’élément et ouvrez **Scroll Bars**. L’option **Show** détermine quand elles apparaissent : **Always**, **While Scrolling** uniquement ou **Never**. Avec **Never**, la molette de la souris permet toujours de faire défiler le texte.
- Dans le même menu, les options **Scroll Grabber Style**, **Scroll Grabber Textures** et **Scroll Grabber Color [HEX]** permettent de modifier leur apparence.

Consultez [Texte dans les menus](/text-in-menus#scroll-bars) pour voir tous les paramètres des barres de défilement.

### Comment afficher les dernières notes de version de Minecraft dans mes menus ?

Il existe un excellent [projet GitHub](https://github.com/ClaytonTDM/minecraft-changelogs-markdown) qui convertit les notes de version de Minecraft en Markdown compatible avec FancyMenu, afin de vous permettre d’afficher les dernières notes de version de Minecraft dans vos menus ! Il est mis à jour quotidiennement pour récupérer les nouvelles notes.

Pour les afficher dans un [élément Texte](/elements#text), réglez **Source Mode** sur **Resource** et la source de la ressource sur **Web**. Utilisez `https://clay.is-a.dev/minecraft-changelogs-markdown/{"placeholder":"mcversion"}/fancymenu.md`.

### Quel est le moyen le plus simple d’étirer un élément aux dimensions de l’écran ?

La plupart des éléments proposent, dans leur menu contextuel accessible par clic droit, une option permettant de les étirer horizontalement et verticalement. Une fois activée, l’option étire toujours l’élément sur toute la largeur et/ou la hauteur de l’écran. L’étirement horizontal et vertical peut être activé indépendamment.

### Je ne peux pas cliquer sur les boutons ni interagir avec les curseurs lorsqu’ils sont derrière ou devant un élément Texte.

Cela se produit parce que les éléments Texte sont interactifs par défaut (pour pouvoir saisir la poignée de défilement ou cliquer sur les liens Markdown) ; ils interceptent donc les clics de souris et les événements de défilement. Le plus simple est de ne pas placer de boutons derrière ou devant des éléments Texte. Si cela n’est pas possible, vous pouvez rendre l’élément Texte non interactif en faisant **un clic droit dessus**, puis en réglant **Interactable** sur **Disabled**. Notez que l’élément Texte devient alors un texte statique non interactif : vous ne pourrez plus le faire défiler ni cliquer sur ses liens.

### Comment empêcher les boutons et les curseurs d’être sélectionnés ou de recevoir le focus quand je navigue dans les écrans avec les touches fléchées et Tab ?

Pour empêcher la navigation vers les boutons et les curseurs, faites **un clic droit dessus** et réglez **Navigable** sur **Disabled**. Le bouton ou le curseur restera cliquable, mais vous ne pourrez plus lui donner le focus avec les touches fléchées ou Tab.

C’est également utile si vous souhaitez ajouter des boutons ou des curseurs à l’écran de discussion : vous pourrez toujours utiliser la flèche vers le haut pour parcourir les anciens messages sans sélectionner accidentellement les boutons ou les curseurs de l’écran.

### Une option manque dans l’un des menus contextuels de FancyMenu.

Les menus contextuels de FancyMenu (ceux qui s’ouvrent lorsque vous faites un clic droit quelque part ou interagissez avec les barres de menu) sont **défilants**. Vous pouvez donc utiliser la molette de la souris lorsque le curseur se trouve sur le menu pour faire défiler les options vers le haut ou vers le bas et afficher celles qui n’étaient pas visibles auparavant.

### Je ne peux pas personnaliser l’écran titre ; l’écran d’origine réapparaît lorsque je quitte l’éditeur.

Un autre mod remplace l’écran `title_screen` d’origine. Désactivez l’écran titre personnalisé de ce mod dans ses paramètres. S’il ne propose pas cette option, FancyMenu ne peut pas appliquer la mise en page à l’écran de remplacement.

### Lorsque j’essaie de personnaliser l’écran d’inventaire, je ne peux pas modifier le conteneur d’inventaire.

C’est normal. FancyMenu ne permet pas de modifier le conteneur lui-même, quel que soit le type d’écran d’inventaire (inventaire du joueur, coffre, établi, etc.), car la prise en charge de cette fonctionnalité serait très difficile à mettre en œuvre.

Il est néanmoins possible d’ajouter de nouveaux éléments à ces écrans ; vous ne pouvez simplement pas modifier le ou les conteneurs.

Au passage, SpiffyHUD ne vous aidera pas non plus, car il sert à modifier le HUD (par exemple, la barre d’objets), et non les écrans (comme les écrans d’inventaire).
