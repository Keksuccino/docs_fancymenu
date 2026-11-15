---
title: FAQ
description: Foire aux questions.
sourceBlobSha: 405be9869106a7871195d6e03828f428cc20b4a1
---
# FAQ

### J'ai besoin d'aide pour résoudre un problème. Quelles informations dois-je fournir ?

Pour obtenir la meilleure aide possible, fournissez autant de contexte que possible :
1.  **Une description claire du problème :** Que pensiez-vous qu'il allait se passer et que s'est-il réellement passé ?
2.  **Votre fichier `latest.log` :** Vous le trouverez à l'emplacement `<game-directory>/logs/latest.log`. **N'envoyez pas de rapport de crash** sauf si cela vous est expressément demandé ; `latest.log` contient généralement le contexte nécessaire. Utilisez un site tel que https://gist.github.com pour le publier.
3.  **Votre version de Minecraft :** (par ex. 1.20.1)
4.  **Votre chargeur de mods et sa version :** (par ex. Forge 47.2.0, Fabric 0.15.7)
5.  **Votre version de FancyMenu :** (par ex. 3.5.2)
6.  **Des captures d'écran ou des vidéos** du problème peuvent également être très utiles.

### Comment modifier la superposition des éléments (déplacer quelque chose devant ou derrière un autre élément) ?

*   **Personnalisé contre personnalisé :** Ouvrez **Window -> Editor Widgets -> Layers** et faites glisser les éléments dans la hiérarchie. Vous pouvez également faire un clic droit sur un élément et utiliser **Move One Layer Up/Down**. Consultez [Calques et groupes](./layers-and-groups).
*   **Personnalisé contre vanilla :** Pour afficher tous vos éléments personnalisés derrière tous les éléments vanilla (par ex. pour placer une image d'arrière-plan derrière les boutons par défaut), **faites un clic droit sur l'arrière-plan de l'éditeur** et activez l'option **"Render Custom Elements Behind Vanilla"**.

### Puis-je exclure certains boutons d'un modèle de bouton universel ?

**Non. Si un bouton modèle possède des textures personnalisées, celles-ci sont toujours partagées avec tous les éléments concernés. Vous ne pouvez pas exclure des boutons individuels.**

### Comment faire pour qu'un bouton effectue une action lorsqu'on clique dessus ?

Utilisez un [**script d'action**](./action-scripts).
1.  Faites un clic droit sur le bouton dans l'éditeur.
2.  Sélectionnez **Edit Action Script**.
3. Cliquez sur **Add Action** et choisissez une action, telle que [**Open Screen or Custom GUI**](./action-scripts#open-screen-or-custom-gui-opengui), [**Join Server**](./action-scripts#join-server-joinserver) ou [**Set Variable Value**](./action-scripts#set-variable-value-fm-variable-set_variable).

### Puis-je créer un écran de menu entièrement nouveau à partir de zéro ?

Utilisez une [**interface graphique personnalisée**](./custom-guis).
1.  Dans la barre de menu, accédez à **Customization -> Custom GUIs -> Manage Custom GUIs**.
2.  Cliquez sur **"New GUI"** et donnez-lui un identifiant unique.
3.  Vous pourrez ensuite ouvrir ce nouvel écran vide et créer sa disposition en y ajoutant les éléments de votre choix.
4. Ouvrez l'interface graphique personnalisée avec l'action [**Open Screen or Custom GUI**](./action-scripts#open-screen-or-custom-gui-opengui).

### Mon jeu met beaucoup de temps à se charger après l'activation du préchargement.

C'est le comportement attendu. Le préchargement de ressources volumineuses, comme des animations haute résolution ou des sons, au démarrage initial augmente naturellement le temps de chargement du jeu.

### Mon animation FMA utilise trop de RAM !

Les [animations FMA classiques](./fma) peuvent consommer beaucoup de mémoire lorsqu'elles contiennent de nombreuses images haute résolution. AFMA est mieux adapté aux textures animées volumineuses ou complexes. Gardez les animations FMA classiques courtes ; utilisez [Video](./video) pour lire des vidéos complètes.

### FancyMenu fonctionne-t-il avec OptiFine ?

Non. OptiFine est **incompatible** et est connu pour casser de nombreux mods, y compris FancyMenu. Il est fortement recommandé d'utiliser des alternatives modernes telles que Sodium/Embeddium + Iris/Oculus.
Consultez [Alternatives à OptiFine](./optifine-alternatives).

### Mon jeu plante. Comment savoir s'il s'agit d'un conflit entre mods ?

La meilleure façon de vérifier la présence d'un conflit entre mods est de **lancer le jeu avec uniquement FancyMenu et ses dépendances** (Konkrete, Melody). Si le crash ne se produit plus, réactivez progressivement vos autres mods par petits groupes jusqu'à ce que le crash se reproduise, afin d'identifier le mod en conflit.

### Un bouton provenant d'un autre mod disparaît ou ne fonctionne pas lorsque j'essaie de le modifier.

Certains mods ajoutent des widgets d'une manière que FancyMenu ne peut ni détecter ni personnaliser. Consultez [Éléments vanilla/de mods](./vanilla-elements) et, pour les écrans basés sur des listes, [Personnalisation des écrans défilants](./customizing-scrollable-screens). Si le widget n'apparaît toujours pas, le mod qui l'ajoute doit l'exposer en tant que widget d'écran pris en charge.

### Puis-je utiliser des dispositions FancyMenu sur un serveur ?

Les dispositions et personnalisations visuelles sont stockées sur le client du joueur ; un serveur ne peut pas les imposer à un client qui n'est pas configuré. Distribuez-les dans un modpack. Installez FancyMenu sur le serveur lorsque vous avez besoin des [commandes serveur](./commands), de [FM Data](./fm-data), de [l'accès aux données NBT côté serveur](./nbt-data-placeholder#server-side-placeholder), des règles de jeu, des structures ou des écouteurs serveur.

### Quelle est la différence entre FancyMenu v2 (pour les anciennes versions de Minecraft) et la v3 ?

FancyMenu v3 est une réécriture complète qui offre de nombreuses nouvelles fonctionnalités, une architecture plus stable et de meilleures performances. La v2 est obsolète, n'est plus prise en charge et ne possède pas de nombreuses fonctionnalités telles que les espaces réservés avancés et les scripts. Il est fortement recommandé d'utiliser la v3 avec une version moderne de Minecraft (1.18.2+). Les dispositions de la v2 peuvent être converties automatiquement vers la v3 lors de leur chargement, mais quelques corrections manuelles peuvent être nécessaires.

### Où puis-je trouver des dispositions et des modèles déjà créés ?

La communauté FancyMenu partage des dispositions dans le canal [`#layout-templates`](https://discord.com/channels/704163135787106365/1234093433795383316) du serveur Discord officiel Keksuccino's Mods ("Kekscord").

### Comment faire pour afficher l'entité du joueur derrière les autres éléments ?

En général, vous ne pouvez pas forcer un [élément Entité du joueur](./elements#player-entity) à se placer derrière les éléments 2D normaux via le [widget Calques](./layers-and-groups). Son moteur de rendu peut ignorer l'ordre normal des calques de l'interface. Concevez la disposition en tenant compte de cette limitation ou utilisez une image pré-rendue lorsqu'un ordre strict des calques est nécessaire.

### Mon entité du joueur n'a qu'une seule jambe ! Que s'est-il passé ?

Il s'agit d'un problème visuel probablement causé par un conflit avec un autre mod qui modifie les animations ou les modèles des joueurs. Vérifiez les paramètres de pose de l'entité du joueur pour voir si les jambes ont été tournées ou déplacées par accident.

### Comment créer un délai entre les actions d'un script ?

Utilisez les blocs [**Delay** ou **Execute Later**](./action-scripts#what-are-statements) pour gérer les actions différées. Pour une logique répétitive exécutée en arrière-plan, utilisez les [planificateurs](./schedulers).

### Puis-je personnaliser les menus du mod Create ?

Non. La personnalisation est volontairement désactivée pour les écrans de Create. Consultez [Écrans pour lesquels la personnalisation est volontairement désactivée](./incompatibility-list#screens-where-customization-is-intentionally-disabled).

### Quelle est la résolution recommandée pour les images d'arrière-plan et les textures des boutons ?

Arrière-plans : une image standard de 1920x1080 (1080p) constitue un excellent point de départ et s'adaptera correctement pour la plupart des utilisateurs.
Boutons : la plupart des boutons vanilla mesurent environ 150 à 200 pixels de large et 20 pixels de haut. Utiliser cette taille pour les textures personnalisées est une bonne pratique pour conserver une certaine cohérence.

### Est-il possible d'ouvrir automatiquement un menu ou d'exécuter une commande lorsqu'un joueur termine un objectif en jeu (comme une quête) ?
FancyMenu possède de nombreux [écouteurs d'événements de jeu intégrés](./listeners), mais il n'existe pas d'écouteur générique pour chaque système de quêtes tiers. Si le mod de quêtes prend en charge les récompenses sous forme de commandes, utilisez-en une pour exécuter [`/openguiscreen`](./commands#openguiscreen), [`/fmvariable`](./commands#fmvariable) ou une autre [commande FancyMenu](./commands) appropriée.

### Comment rendre un bouton inactif ou « grisé » ?

Vous pouvez contrôler l'état actif d'un bouton à l'aide des [conditions de chargement](./conditions).
Faites un clic droit sur le bouton dans l'éditeur et sélectionnez **Control Active State**.
Ajoutez une condition qui doit être remplie pour que le bouton soit actif. Pour le désactiver définitivement, utilisez [**Is Number**](./conditions#is-number-fancymenu_visibility_requirement_is_number) afin de vérifier si 0 est égal à 1.
Le bouton utilisera alors sa texture « Inactive Background » et ne pourra pas être cliqué.

### Comment supprimer l'en-tête et le pied de page (les barres de texture de terre) des écrans défilants ?

Dans l'éditeur de dispositions, ouvrez **Layout Properties -> Header/Footer Customizations**. Définissez les textures comme transparentes. Cette option peut être indisponible sur certains écrans modifiés par des mods.

### Je ne peux pas créer une disposition « pour l'écran actuel ». Le bouton est grisé.

Vous devez d'abord activer les personnalisations pour cet écran via **menu bar -> Customization -> Current Screen Customizations -> Enabled**.

### Je ne peux personnaliser aucun élément d'un écran lorsque je l'ouvre dans l'éditeur. L'écran est alors vide.

Cela peut signifier que vous avez créé une [disposition universelle](./universal-layouts) au lieu d'une disposition **pour l'écran actuel**.

Il peut également s'agir d'un [écran défilant](./customizing-scrollable-screens), que FancyMenu ne peut pas personnaliser par défaut.

La troisième possibilité est qu'il s'agisse d'un écran provenant d'un mod qui ajoute des éléments d'une manière non vanilla, ce qui empêche FancyMenu de les personnaliser.

### Des cases grises étranges apparaissent sur mon élément Texte.

Ces cases translucides sont les poignées de défilement de l'[élément Texte](./elements#text), et non un problème de rendu.

Si vous ne voulez pas que ces cases soient visibles, vous pouvez soit faire un clic droit sur l'élément et désactiver complètement le défilement, soit définir les textures des poignées comme entièrement transparentes dans le même menu contextuel si vous souhaitez que l'élément reste défilable.

### Comment afficher le journal des modifications Minecraft le plus récent dans mes menus ?

Il existe un excellent [projet GitHub](https://github.com/ClaytonTDM/minecraft-changelogs-markdown) qui convertit les journaux des modifications de Minecraft en Markdown compatible avec FancyMenu, afin que vous puissiez afficher le journal le plus récent dans vos menus ! Il est mis à jour quotidiennement pour récupérer les nouveaux journaux.

Pour l'afficher dans un [élément Texte](./elements#text), définissez le **Source Mode** sur **Resource** et sa source de ressource sur **Web**. Utilisez `https://clay.is-a.dev/minecraft-changelogs-markdown/{"placeholder":"mcversion"}/fancymenu.md`.

### Quelle est la manière la plus simple d'étirer n'importe quel élément à la taille de l'écran ?

La plupart des éléments disposent, dans leur menu contextuel accessible par clic droit, d'une option permettant de les étirer horizontalement et verticalement. En l'activant, ils s'étendront toujours sur toute la largeur et/ou toute la hauteur de l'écran. L'étirement horizontal et l'étirement vertical peuvent être activés indépendamment.

### Je ne peux pas cliquer sur les boutons ni interagir avec les curseurs lorsqu'ils se trouvent derrière ou devant un élément Texte.

Cela se produit parce que les éléments Texte sont interactifs par défaut (pour pouvoir saisir la poignée de défilement ou cliquer sur les hyperliens Markdown), ce qui signifie qu'ils interceptent les clics de souris et les événements de défilement. Le mieux serait simplement de ne pas placer les boutons derrière ou devant les éléments Texte, mais si cela est inévitable, vous pouvez rendre l'élément Texte non interactif en **faisant un clic droit dessus**, puis en définissant **Interactable** sur **Disabled**. Gardez à l'esprit que l'élément Texte deviendra alors un texte statique et non interactif : vous ne pourrez plus le faire défiler ni cliquer sur ses hyperliens.

### Comment empêcher les boutons et les curseurs d'être sélectionnés ou ciblés lors de la navigation dans les écrans avec les touches fléchées et Tab ?

Pour rendre les boutons et les curseurs non navigables, vous devez **faire un clic droit dessus** et définir **Navigable** sur **Disabled**. Le bouton ou le curseur restera cliquable, mais vous ne pourrez plus lui donner le focus avec la navigation par les touches fléchées ou Tab.

Cette option est également utile si vous souhaitez ajouter des boutons ou des curseurs à l'écran de discussion, afin de pouvoir continuer à utiliser la touche Flèche haut pour parcourir les anciens messages sans sélectionner accidentellement les boutons ou les curseurs présents à l'écran.

### Il manque une option dans l'un des menus contextuels de FancyMenu alors qu'elle devrait s'y trouver.

Les menus contextuels de FancyMenu (les menus qui s'ouvrent lorsque vous faites un clic droit quelque part ou lorsque vous interagissez avec les barres de menu) sont DÉFILABLES. Cela signifie que vous pouvez utiliser la molette de la souris lorsque le curseur se trouve au-dessus du menu pour faire défiler son contenu vers le haut ou vers le bas et voir davantage d'options qui n'étaient pas visibles auparavant.

### Je ne peux pas personnaliser l'écran titre : l'original s'affiche toujours lorsque je quitte l'éditeur.

Un autre mod remplace l'écran original `title_screen`. Désactivez l'écran titre personnalisé de ce mod dans ses paramètres. S'il ne propose pas cette option, FancyMenu ne peut pas appliquer la disposition à l'écran de remplacement.

### Lorsque j'essaie de personnaliser l'écran d'inventaire, je ne peux pas personnaliser le conteneur de l'inventaire.

C'est normal. FancyMenu ne prend pas en charge la modification du conteneur lui-même pour quelque type d'écran d'inventaire que ce soit (inventaire du joueur, coffre, établi, etc.), car l'ajout de cette fonctionnalité serait très difficile.

Il est néanmoins possible d'ajouter de nouveaux éléments à ces écrans ; vous ne pouvez simplement pas modifier le ou les conteneurs.

SpiffyHUD ne vous aidera pas non plus dans ce cas, car il sert à modifier l'interface du jeu (par exemple la barre d'objets), mais ne peut pas modifier les écrans (comme les écrans d'inventaire).
