---
title: FAQ
description: Questions fréquemment posées.
---

# FAQ

### J’ai besoin d’aide pour un problème. Quelles informations dois-je fournir ?
Pour obtenir la meilleure aide possible, veuillez fournir autant de contexte que possible :
1.  **Une description claire du problème :** Qu’aviez-vous l’attente qu’il se passe, et que s’est-il réellement passé ?
2.  **Votre fichier `latest.log` :** C’est le fichier le plus important pour le dépannage. Trouvez-le dans le dossier `/logs/` de votre instance. **N’envoyez pas un journal de crash** sauf si on vous le demande explicitement ; `latest.log` est bien plus utile. Utilisez un site comme https://gist.github.com pour le partager.
3.  **Votre version de Minecraft :** (par ex. 1.20.1)
4.  **Votre chargeur de mods et sa version :** (par ex. Forge 47.2.0, Fabric 0.15.7)
5.  **Votre version de FancyMenu :** (par ex. 3.5.2)
6.  **Des captures d’écran ou des vidéos** du problème peuvent aussi être très utiles.

### Comment puis-je changer l’ordre d’affichage des éléments (mettre quelque chose devant ou derrière un autre) ?
*   **Custom vs. Custom :** Pour modifier l’ordre de rendu de vos propres éléments personnalisés, utilisez le **widget Layers**. Vous pouvez l’ouvrir via la barre de menu : **Window -> Widgets -> Layers**. De là, vous pouvez faire glisser les éléments vers le haut ou vers le bas dans la hiérarchie. Vous pouvez aussi faire un clic droit sur un élément et utiliser « Move One Layer Up/Down ».
*   **Custom vs. Vanilla :** Pour afficher tous vos éléments personnalisés derrière tous les éléments vanilla (par ex. pour placer une image d’arrière-plan derrière les boutons par défaut), **faites un clic droit sur l’arrière-plan de l’éditeur** et activez l’option **« Render Custom Elements Behind Vanilla »**.

### Puis-je exclure certains boutons d’un modèle de bouton universel ?
**Non. Si un bouton modèle a des textures personnalisées définies, ces textures sont toujours partagées avec tous les éléments concernés. Vous ne pouvez pas exclure des boutons individuellement.**

### Comment faire pour qu’un bouton exécute une action lorsqu’on clique dessus ?
Utilisez un **Action Script**.
1.  Faites un clic droit sur le bouton dans l’éditeur.
2.  Sélectionnez **Edit Action Script**.
3.  Cliquez sur **Add Action** et choisissez dans la liste (par ex. `Open Screen or Custom GUI`, `Join Server`, `Set Variable Value`).
*   Plus d’infos : [Action Scripts](https://docs.fancymenu.net/en/action-scripts)

### Puis-je créer un tout nouveau menu à partir de zéro ?
Oui, cela se fait avec les **Custom GUIs**.
1.  Dans la barre de menu, allez dans **Customization -> Custom GUIs -> Manage Custom GUIs**.
2.  Cliquez sur **« New GUI »** et donnez-lui un identifiant unique.
3.  Vous pouvez ensuite ouvrir cet écran vide et lui créer une mise en page, en ajoutant tous les éléments souhaités.
4.  Cette Custom GUI peut ensuite être ouverte via l’action d’un bouton.
*   Plus d’infos : [Custom GUIs](https://docs.fancymenu.net/en/custom-guis)

### Mon jeu met beaucoup de temps à charger après avoir activé le préchargement.
C’est un comportement attendu. Le préchargement de ressources volumineuses, comme des animations ou des sons en haute résolution, pendant le démarrage initial augmentera naturellement le temps de chargement du jeu.

### Mon animation FMA utilise trop de RAM !
Les fichiers FMA classiques peuvent consommer beaucoup de mémoire lorsqu’ils contiennent de nombreuses images en haute résolution. FancyMenu 3.9.0 ajoute AFMA, qui est bien plus adapté aux grandes textures animées ou complexes. Pour les fichiers FMA classiques, gardez les animations courtes et évitez les nombres d’images/résolutions très élevés. Les animations sont prévues pour de courtes boucles décoratives, pas pour lire des vidéos entières.

### FancyMenu fonctionne-t-il avec OptiFine ?
Non. OptiFine **n’est pas compatible** et est connu pour casser de nombreux mods, y compris FancyMenu. Il est fortement recommandé d’utiliser des alternatives modernes comme Sodium/Embeddium + Iris/Oculus.
*   Plus d’infos : [OptiFine Alternatives](https://docs.fancymenu.net/en/optifine-alternatives)

### Mon jeu plante. Comment savoir s’il s’agit d’un conflit entre mods ?
La meilleure façon de vérifier un conflit entre mods est de **lancer le jeu uniquement avec FancyMenu et ses dépendances** (Konkrete, Melody). Si le crash ne se reproduit plus, vous pouvez rajouter vos autres mods par petits groupes jusqu’à ce que le crash réapparaisse afin d’identifier le mod conflictuel.

### Le bouton d’un autre mod disparaît ou ne fonctionne pas lorsque j’essaie de le modifier.
Cela signifie généralement que l’autre mod ajoute ses boutons d’une manière non standard avec laquelle FancyMenu ne peut pas interagir. C’est un problème que le développeur de l’autre mod devra corriger de son côté. FancyMenu ne peut pas personnaliser des éléments qu’il ne peut pas « voir ».

### Puis-je utiliser les mises en page FancyMenu sur un serveur ?
FancyMenu est un mod côté client. Toutes les mises en page et personnalisations se trouvent sur le client du joueur. Vous ne pouvez pas mettre des mises en page sur un serveur pour obliger les joueurs à les voir. En revanche, vous pouvez distribuer votre dossier `config/fancymenu` dans le cadre d’un modpack. Si vous voulez utiliser des commandes comme `/fmvariable` ou `/openguiscreen` depuis le serveur, alors FancyMenu (ou son plugin Spigot) doit être installé sur le serveur.

### Quelle est la différence entre FancyMenu v2 (pour les anciennes versions de MC) et v3 ?
FancyMenu v3 est une réécriture complète avec de nombreuses nouvelles fonctionnalités, une architecture plus stable et de meilleures performances. V2 est obsolète, n’est plus pris en charge et manque de nombreuses fonctionnalités comme les placeholders avancés et le scripting. Il est fortement recommandé d’utiliser v3 sur une version moderne de Minecraft (1.18.2+). Les mises en page V2 peuvent être automatiquement converties en v3 lors du chargement, mais quelques corrections manuelles peuvent être nécessaires.

### Où puis-je trouver des mises en page et modèles prêts à l’emploi ?
La communauté FancyMenu partage des mises en page dans le canal `#layout-templates` sur le serveur Discord officiel Keksuccino's Mods.

### Comment puis-je faire en sorte que l’entité joueur s’affiche derrière les autres éléments ?
On ne peut pas. En raison de la façon dont Minecraft rend les entités, l’élément Player Entity s’affichera presque toujours devant les autres éléments 2D, quels que soient les paramètres de calque.

### Mon Player Entity n’a qu’une seule jambe ! Que s’est-il passé ?
C’est un bug visuel, probablement causé par un conflit avec un autre mod qui modifie les animations ou les modèles des joueurs. Vérifiez les paramètres de pose du Player Entity pour voir si les jambes ont été tournées ou déplacées par accident.

### Comment créer un délai entre des actions dans un script ?
FancyMenu 3.9.0 ajoute les blocs **Delay** et **Execute Later** aux scripts d’actions. Utilisez-les pour la plupart des logiques d’action différées. Pour une logique répétée en arrière-plan, utilisez les [Schedulers](https://docs.fancymenu.net/en/schedulers).

### Puis-je personnaliser les menus du mod Create ?
Non. FancyMenu présente des incompatibilités connues avec les interfaces complexes de Create. La personnalisation des écrans Create a été volontairement désactivée pour éviter les plantages.

### Pourquoi les boutons du mod X disparaissent-ils dans l’éditeur ?
Cela signifie que le mod ajoute ses boutons d’une manière personnalisée, non vanilla. FancyMenu ne peut pas « voir » ni interagir avec ces éléments, donc il ne peut pas les personnaliser. Le développeur de l’autre mod devrait modifier la façon dont il ajoute ses boutons pour qu’ils soient compatibles.

### Quelle est la résolution recommandée pour les images d’arrière-plan et les textures de boutons ?
Arrière-plans : une image standard en 1920x1080 (1080p) est un excellent point de départ et s’adaptera bien à la plupart des utilisateurs.
Boutons : la plupart des boutons vanilla font environ 150 à 200 pixels de large et 20 pixels de haut. Reproduire cette taille pour des textures personnalisées est une bonne pratique pour garder une cohérence visuelle.

### Existe-t-il un moyen d’ouvrir automatiquement un menu ou d’exécuter une commande lorsqu’un joueur termine un objectif en jeu (comme une quête) ?
FancyMenu seul ne peut pas détecter ce type d’événements en jeu. Cependant, vous pouvez l’intégrer avec un mod de quêtes comme FTB Quests. La plupart des mods de quêtes permettent d’exécuter une commande en tant que récompense de quête. Il vous suffirait de définir la récompense pour exécuter la commande `/openguiscreen` ou `/fmvariable` afin d’interagir avec vos menus.

### Comment faire pour qu’un bouton soit inactif ou « grisé » ?
Vous pouvez contrôler l’état actif d’un bouton à l’aide des Loading Requirements.
Faites un clic droit sur le bouton dans l’éditeur et sélectionnez « Active State ».
Ajoutez une condition qui doit être remplie pour que le bouton soit actif. Par exemple, pour désactiver définitivement un bouton, vous pouvez ajouter une condition Is Number qui vérifie si 0 est égal à 1 (ce qui est toujours faux).
Le bouton utilisera alors sa texture « Inactive Background » et ne sera pas cliquable.

### Comment puis-je supprimer l’en-tête et le pied de page (les barres de texture de terre) sur les écrans défilables ?
Dans FancyMenu v3, vous pouvez les personnaliser. Dans l’éditeur de mise en page, faites un clic droit sur l’arrière-plan de l’éditeur et recherchez des options comme « Customize Header/Footer ». Vous pouvez définir leurs textures comme entièrement transparentes pour les faire disparaître visuellement. Notez que cela peut ne pas fonctionner sur tous les écrans, en particulier les plus anciens ou très moddés.

### Je ne peux pas créer une mise en page « pour l’écran actuel ». Le bouton est grisé.
Vous devez d’abord activer les personnalisations pour cet écran via **menu bar -> Customization -> Current Screen Customizations -> toggle it to Enabled**.

### Je ne peux personnaliser aucun élément d’un écran lorsque je l’ouvre dans l’éditeur. L’écran est simplement vide.

Cela peut vouloir dire que vous avez accidentellement créé une mise en page universelle au lieu d’une mise en page **pour l’écran actuel**.

Cela peut aussi vouloir dire que l’écran que vous personnalisez est un écran défilable, c’est-à-dire un écran que FancyMenu ne peut pas personnaliser par défaut.

La troisième possibilité est qu’il s’agisse d’un écran provenant d’un mod qui ajoute des éléments d’une manière non vanilla, ce qui empêche FancyMenu de personnaliser ces éléments.

### Il y a d’étranges boîtes grises sur mon élément Text.

Ces boîtes/rectangles translucides (faible opacité) peuvent se trouver sur le bord droit ou inférieur de votre élément Text et ce n’est pas un bug. Ce sont les poignées de défilement de l’élément Text, puisqu’il est défilable.

Si vous ne voulez pas que ces boîtes soient visibles, vous pouvez soit faire un clic droit sur l’élément et désactiver complètement le défilement, soit définir les textures des poignées sur des textures complètement transparentes dans le même menu contextuel, si vous voulez que l’élément reste défilable.

### Comment puis-je afficher le dernier changelog de Minecraft dans mes menus ?

Il existe un excellent [projet GitHub](https://github.com/ClaytonTDM/minecraft-changelogs-markdown) qui convertit les changelogs de Minecraft en Markdown compatible avec FancyMenu, afin que vous puissiez afficher le dernier changelog de MC dans vos menus ! Il se met à jour quotidiennement pour récupérer les nouveaux changelogs.

Par exemple, pour afficher le dernier changelog de Minecraft dans un élément Text, définissez son **Source Mode** sur **Resource** et sa source de ressource sur **Web**. Utilisez ensuite cette URL comme source : `https://clay.is-a.dev/minecraft-changelogs-markdown/{"placeholder":"mcversion"}/fancymenu.md`

### Quelle est la façon la plus simple d’étirer n’importe quel élément à la taille de l’écran ?

La plupart des éléments ont une option dans leur menu contextuel accessible par clic droit pour les étirer horizontalement et verticalement. L’activer fera en sorte qu’ils s’étendent toujours sur toute la largeur et/ou la hauteur de l’écran. L’étirement horizontal et vertical peut être activé indépendamment.

### Je ne peux pas cliquer sur les boutons ni interagir avec les curseurs lorsqu’ils se trouvent derrière ou devant un élément Text.

Cela se produit parce que les éléments Text sont interactifs par défaut (pour pouvoir saisir la poignée de défilement ou cliquer sur les liens Markdown), ce qui signifie qu’ils consomment les clics souris et les événements de défilement. La meilleure solution serait simplement de ne pas placer de boutons devant/derrière des éléments Text, mais s’il n’y a pas d’autre choix, vous pouvez rendre l’élément Text non interactif en **faisant un clic droit dessus**, puis en réglant **Interactable** sur **Disabled**. Gardez à l’esprit que cela transforme l’élément Text en texte statique non interactif, vous ne pourrez donc plus le faire défiler ni cliquer sur les liens hypertexte.

### Comment faire pour que les boutons et les curseurs ne soient plus sélectionnés/focalisés lors de la navigation dans les écrans avec les touches fléchées et Tab du clavier ?

Pour rendre les boutons et les curseurs non navigables, vous devez **faire un clic droit** dessus et régler **Navigable** sur **Disabled**. Le bouton/le curseur restera cliquable, mais vous ne pourrez plus le focaliser avec la navigation par touches fléchées/Tab.

C’est aussi utile si vous voulez ajouter des boutons/curseurs à l’écran du chat, afin de pouvoir toujours utiliser la touche Flèche Haut pour parcourir les anciens messages sans sélectionner accidentellement les boutons/curseurs de l’écran.

### L’un des menus contextuels de FancyMenu manque une option qui devrait s’y trouver.

Les menus contextuels de FancyMenu (les menus qui s’ouvrent lorsque vous faites un clic droit quelque part ou interagissez avec des barres de menu) sont DÉFILABLES. Cela signifie que vous pouvez utiliser la molette de la souris lorsque le curseur est au-dessus du menu pour faire défiler vers le haut ou vers le bas, ce qui vous permet de voir plus d’options qui n’étaient pas visibles auparavant.
