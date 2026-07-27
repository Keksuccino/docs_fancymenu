---
title: FAQ
description: Questions fréquemment posées.
---
# FAQ

### J’ai besoin d’aide pour un problème. Quelles informations dois-je fournir ?

Pour obtenir la meilleure aide possible, veuillez fournir le plus de contexte possible :
1.  **Une description claire du problème :** Qu’espériez-vous qu’il se passe, et que s’est-il réellement passé ?
2.  **Votre fichier `latest.log` :** Vous le trouverez dans `<game-directory>/logs/latest.log`. **N’envoyez pas de journal de crash** sauf si cela vous est explicitement demandé ; `latest.log` contient généralement le contexte nécessaire. Utilisez un site comme https://gist.github.com pour le partager.
3.  **Votre version de Minecraft :** (par ex. 1.20.1)
4.  **Votre chargeur de mods et sa version :** (par ex. Forge 47.2.0, Fabric 0.15.7)
5.  **Votre version de FancyMenu :** (par ex. 3.5.2)
6.  **Des captures d’écran ou des vidéos** du problème peuvent aussi être très utiles.

### Comment modifier l’empilement des éléments (mettre quelque chose devant ou derrière autre chose) ?

*   **Personnalisé vs. Personnalisé :** Ouvrez **Fenêtre -> Widgets de l’éditeur -> Calques** et faites glisser les éléments dans la hiérarchie. Vous pouvez aussi faire un clic droit sur un élément et utiliser **Déplacer d’un calque vers le haut/bas**. Voir [Calques et groupes](./layers-and-groups).
*   **Personnalisé vs. Vanilla :** Pour afficher tous vos éléments personnalisés derrière tous les éléments vanilla (par ex. pour placer une image de fond derrière les boutons par défaut), **faites un clic droit sur l’arrière-plan de l’éditeur** et activez l’option **"Rendre les éléments personnalisés derrière Vanilla"**.

### Puis-je exclure certains boutons d’un modèle de bouton universel ?

**Non. Si un bouton de modèle a des textures personnalisées définies, ces textures sont toujours partagées avec tous les éléments concernés. Vous ne pouvez pas exclure des boutons individuels.**

### Comment faire exécuter une action à un bouton lorsqu’on clique dessus ?

Utilisez un [**Script d’action**](./action-scripts).
1.  Faites un clic droit sur le bouton dans l’éditeur.
2.  Sélectionnez **Modifier le script d’action**.
3. Cliquez sur **Ajouter une action** et choisissez une action, comme [**Ouvrir un écran ou une interface personnalisée**](./action-scripts#open-screen-or-custom-gui-opengui), [**Rejoindre un serveur**](./action-scripts#join-server-joinserver), ou [**Définir la valeur d’une variable**](./action-scripts#set-variable-value-fm-variable-set_variable).

### Puis-je créer un tout nouvel écran de menu à partir de zéro ?

Utilisez une [**Interface personnalisée**](./custom-guis).
1.  Dans la barre de menu, allez à **Personnalisation -> Interfaces personnalisées -> Gérer les interfaces personnalisées**.
2.  Cliquez sur **"Nouvelle interface"** et donnez-lui un identifiant unique.
3.  Vous pouvez ensuite ouvrir cet écran vide et lui créer une disposition, en ajoutant tous les éléments souhaités.
4. Ouvrez l’interface personnalisée avec l’[**action Ouvrir un écran ou une interface personnalisée**](./action-scripts#open-screen-or-custom-gui-opengui).

### Mon jeu met beaucoup de temps à se charger après l’activation du préchargement.

C’est un comportement attendu. Précharger de grosses რესsources comme des animations ou des sons en haute résolution lors du démarrage initial augmentera naturellement le temps de chargement du jeu.

### Mon animation FMA consomme trop de RAM !

Les [animations FMA](./fma) classiques peuvent consommer beaucoup de mémoire lorsqu’elles contiennent de nombreuses images en haute résolution. AFMA est mieux adapté aux textures animées volumineuses ou complexes. Gardez les animations FMA classiques courtes ; utilisez [Vidéo](./video) pour une lecture vidéo complète.

### FancyMenu fonctionne-t-il avec OptiFine ?

Non. OptiFine n’est **pas compatible** et est connu pour casser de nombreux mods, y compris FancyMenu. Il est fortement recommandé d’utiliser des alternatives modernes comme Sodium/Embeddium + Iris/Oculus.
Voir [Alternatives à OptiFine](./optifine-alternatives).

### Mon jeu plante. Comment savoir s’il s’agit d’un conflit entre mods ?

La meilleure façon de vérifier un conflit entre mods est de **lancer le jeu uniquement avec FancyMenu et ses dépendances** (Konkrete, Melody). Si le crash ne se produit plus, vous pouvez réajouter vos autres mods par petits groupes jusqu’à ce que le crash se reproduise afin d’identifier le mod en conflit.

### Un bouton provenant d’un autre mod disparaît ou ne fonctionne pas lorsque j’essaie de le modifier.

Certains mods ajoutent des widgets d’une manière que FancyMenu ne peut pas détecter ou personnaliser. Consultez [Éléments Vanilla/Mod](./vanilla-elements) et, pour les écrans basés sur des listes, [Personnalisation des écrans défilants](./customizing-scrollable-screens). Si le widget n’apparaît toujours pas, le mod qui l’ajoute doit l’exposer comme un widget d’écran pris en charge.

### Puis-je utiliser des dispositions FancyMenu sur un serveur ?

Les dispositions et personnalisations visuelles sont stockées sur le client du joueur ; un serveur ne peut pas les imposer à un client non configuré. Distribuez-les dans le cadre d’un modpack. Installez FancyMenu sur le serveur lorsque vous avez besoin de [commandes serveur](./commands), de [FM Data](./fm-data), d’un [accès NBT côté serveur](./nbt-data-placeholder#server-side-placeholder), de gamerules, de structures ou d’écouteurs côté serveur.

### Quelle est la différence entre FancyMenu v2 (pour les anciennes versions de MC) et v3 ?

FancyMenu v3 est une réécriture complète avec de nombreuses nouvelles fonctionnalités, une architecture plus stable et de meilleures performances. La v2 est obsolète, plus prise en charge, et manque de nombreuses fonctionnalités comme les placeholders avancés et le scripting. Il est fortement recommandé d’utiliser la v3 sur une version moderne de Minecraft (1.18.2+). Les dispositions de la v2 peuvent être converties automatiquement en v3 lors du chargement, mais quelques corrections manuelles peuvent être nécessaires.

### Où puis-je trouver des dispositions et des modèles prêts à l’emploi ?

La communauté FancyMenu partage des dispositions dans le canal `#layout-templates` du serveur Discord officiel de Keksuccino's Mods ("Kekscord").

### Comment faire pour que l’élément Player Entity s’affiche derrière les autres éléments ?

En général, vous ne pouvez pas forcer un [élément Player Entity](./elements#player-entity) à passer derrière les éléments 2D normaux via le [widget Calques](./layers-and-groups). Son moteur de rendu peut ignorer l’ordre normal des calques de l’interface. Concevez la disposition en tenant compte de cette limitation ou utilisez une image pré-rendue lorsqu’un ordre de calques strict est nécessaire.

### Mon Player Entity n’a qu’une seule jambe ! Que s’est-il passé ?

Il s’agit d’un bug visuel, probablement causé par un conflit avec un autre mod qui modifie les animations ou les modèles des joueurs. Vérifiez les paramètres de pose du Player Entity pour voir si les jambes ont été tournées ou déplacées par erreur.

### Comment créer un délai entre des actions dans un script ?

Utilisez des blocs [**Délai** ou **Exécuter plus tard**](./action-scripts#what-are-statements) pour la logique d’actions différées. Pour une logique de fond répétée, utilisez des [Planificateurs](./schedulers).

### Puis-je personnaliser les menus du mod Create ?

Non. La personnalisation est volontairement désactivée pour les écrans Create. Voir [Écrans pour lesquels la personnalisation est volontairement désactivée](./incompatibility-list#screens-where-customization-is-intentionally-disabled).

### Quelle est la résolution recommandée pour les images d’arrière-plan et les textures de boutons ?

Arrière-plans : une image standard en 1920x1080 (1080p) est un excellent point de départ et s’adaptera bien à la plupart des utilisateurs.
Boutons : la plupart des boutons vanilla mesurent environ 150 à 200 pixels de large et 20 pixels de haut. Reproduire cette taille pour des textures personnalisées est une bonne pratique pour garder une certaine cohérence.

### Existe-t-il un moyen d’ouvrir automatiquement un menu ou d’exécuter une commande lorsqu’un joueur termine un objectif en jeu (comme une quête) ?
FancyMenu dispose de nombreux [écouteurs d’événements de jeu intégrés](./listeners), mais il n’existe pas d’écouteur générique pour chaque système de quêtes tiers. Si le mod de quêtes prend en charge les récompenses par commande, utilisez-en une pour exécuter [`/openguiscreen`](./commands#openguiscreen), [`/fmvariable`](./commands#fmvariable), ou une autre [commande FancyMenu](./commands) appropriée.

### Comment rendre un bouton inactif ou « grisé » ?

Vous pouvez contrôler l’état actif d’un bouton à l’aide des [Exigences de chargement](./conditions).
Faites un clic droit sur le bouton dans l’éditeur et sélectionnez **Contrôler l’état actif**.
Ajoutez une condition qui doit être remplie pour que le bouton soit actif. Pour le désactiver définitivement, utilisez [**Est un nombre**](./conditions#is-number-fancymenu_visibility_requirement_is_number) pour vérifier si 0 est égal à 1.
Le bouton utilisera alors sa texture **Arrière-plan inactif** et ne sera plus cliquable.

### Comment puis-je supprimer l’en-tête et le pied de page (les barres de texture de terre) sur les écrans défilants ?

Dans l’éditeur de disposition, ouvrez **Propriétés de la disposition -> Personnalisations de l’en-tête/du pied de page**. Définissez les textures comme transparentes. Cette option peut être indisponible sur certains écrans moddés.

### Je n’arrive pas à créer une disposition « pour l’écran actuel ». Le bouton est grisé.

Vous devez d’abord activer les personnalisations pour cet écran via **barre de menu -> Personnalisation -> Personnalisations de l’écran actuel -> Activé**.

### Je ne peux personnaliser aucun élément d’un écran quand je l’ouvre dans l’éditeur. Il est simplement vide.

Cela peut signifier que vous avez créé une [Disposition universelle](./universal-layouts) au lieu d’une disposition **pour l’écran actuel**.

Cela peut aussi être un [écran défilant](./customizing-scrollable-screens), que FancyMenu ne peut pas personnaliser par défaut.

La troisième possibilité est qu’il s’agisse d’un écran provenant d’un mod qui ajoute des éléments d’une manière non vanilla, ce qui empêche FancyMenu de personnaliser ces éléments.

### Il y a d’étranges boîtes grises sur mon élément Texte.

Ces boîtes translucides sont les poignées de défilement de l’[élément Texte](./elements#text), pas un bug de rendu.

Si vous ne souhaitez pas qu’elles soient visibles, vous pouvez soit faire un clic droit sur l’élément et désactiver complètement le défilement, soit définir les textures des poignées comme complètement transparentes dans le même menu de clic droit, si vous voulez que l’élément reste défilable.

### Comment afficher le dernier journal des changements de Minecraft dans mes menus ?

Il existe un excellent [projet GitHub](https://github.com/ClaytonTDM/minecraft-changelogs-markdown) qui convertit les journaux des changements de Minecraft en Markdown compatible avec FancyMenu, afin que vous puissiez afficher le dernier journal des changements MC dans vos menus ! Il est mis à jour quotidiennement pour récupérer les nouveaux journaux des changements.

Pour l’afficher dans un [élément Texte](./elements#text), réglez **Mode source** sur **Ressource** et sa source de ressource sur **Web**. Utilisez `https://clay.is-a.dev/minecraft-changelogs-markdown/{"placeholder":"mcversion"}/fancymenu.md`.

### Quelle est la manière la plus simple d’étirer n’importe quel élément à la taille de l’écran ?

La plupart des éléments ont une option dans leur menu contextuel de clic droit pour les étirer horizontalement et verticalement. L’activer les fera toujours s’étendre sur toute la largeur et/ou toute la hauteur de l’écran. L’étirement horizontal et vertical peut être activé séparément.

### Je ne peux pas cliquer sur les boutons ni interagir avec les curseurs lorsqu’ils sont derrière ou devant un élément Texte.

Cela se produit parce que les éléments Texte sont interactifs par défaut (afin de pouvoir attraper la poignée de défilement ou cliquer sur les liens Markdown), ce qui signifie qu’ils consomment les clics de souris et les événements de défilement. La meilleure solution serait simplement de ne pas placer de boutons derrière/devant les éléments Texte, mais s’il n’y a pas d’autre choix, vous pouvez rendre l’élément Texte non interactif en **faisant un clic droit dessus**, puis en réglant **Interactif** sur **Désactivé**. Gardez à l’esprit que cela transforme l’élément Texte en texte statique non interactif ; vous ne pourrez donc plus le faire défiler ni cliquer sur les liens hypertexte.

### Comment faire pour que les boutons et les curseurs ne soient plus sélectionnés ou focalisés lors de la navigation dans les écrans avec les touches fléchées et Tab du clavier ?

Pour que les boutons et les curseurs ne soient plus navigables, vous devez **faire un clic droit** dessus et définir **Navigable** sur **Désactivé**. Le bouton/le curseur restera cliquable, mais vous ne pourrez plus le sélectionner via la navigation avec les flèches/Tab.

C’est aussi utile si vous souhaitez ajouter des boutons/curseurs à l’écran de chat, afin de pouvoir toujours utiliser la touche Flèche haut pour faire défiler les anciens messages sans sélectionner accidentellement des boutons/curseurs dans l’écran.

### Un des menus contextuels de FancyMenu manque une option qui devrait s’y trouver.

Les menus contextuels de FancyMenu (les menus qui s’ouvrent lorsque vous faites un clic droit quelque part ou lorsque vous interagissez avec les barres de menu) sont DÉFILABLES. Cela signifie que vous pouvez utiliser la molette de la souris lorsque le curseur est au-dessus du menu pour faire défiler vers le haut ou vers le bas, ce qui vous permet de voir d’autres options auparavant invisibles.

### Je ne peux pas personnaliser l’écran titre, il affiche toujours l’original quand je quitte l’éditeur.

Un autre mod remplace l’original `title_screen`. Désactivez l’écran titre personnalisé de ce mod dans ses paramètres. S’il n’a pas cette option, FancyMenu ne peut pas appliquer la disposition à l’écran de remplacement.
