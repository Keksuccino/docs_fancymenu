---
title: Interfaces personnalisées
description: >-
  Créez vos propres menus de zéro, ouvrez-les avec des boutons, des touches ou
  des commandes, affichez-les sous forme de fenêtres contextuelles et remplacez
  d’autres menus par ceux-ci.
sourceBlobSha: 0b336708473ae2964b3d9e777498c6cd40eaffc6
---

# Interfaces personnalisées

Les interfaces personnalisées sont des menus que vous créez vous-même, comme un écran d’informations sur un modpack, un salon de serveur ou une page de règles. Elles sont vides au départ et vous les remplissez avec une [mise en page](/layout-editor), comme n’importe quel autre menu. Vous pouvez ensuite les ouvrir avec des boutons, des touches ou des commandes.

<img width="800" alt="Cliquer sur le bouton Modpack Info de l’écran titre ouvre une interface personnalisée sous forme de fenêtre contextuelle au-dessus de l’écran titre flouté ; son bouton Retour permet ensuite de la fermer" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/custom_guis_popup.gif?raw=true">

# Créer une interface personnalisée

<img width="800" alt="Ouvrir Manage Custom GUIs, cliquer sur New GUI, saisir l’identifiant modpack_info, activer Popup Mode et ouvrir la nouvelle interface personnalisée" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/custom_guis_new.gif?raw=true">

1. Ouvrez **barre de menus -> Personnalisation -> Interfaces personnalisées -> Gérer les interfaces personnalisées**.
2. Cliquez sur **Nouvelle interface**.
3. Saisissez un **identifiant d’interface personnalisée**, par exemple `modpack_info`, configurez les [paramètres](#paramètres), puis cliquez sur **Terminé**.
4. Cliquez sur la nouvelle interface personnalisée dans la liste, puis sur **Ouvrir l’interface**.
5. Cliquez sur **Terminé** pour fermer **Gérer les interfaces personnalisées**.

**Gérer les interfaces personnalisées** n’enregistre vos modifications que lorsque vous cliquez sur **Terminé** ou **Ouvrir l’interface**. **Annuler** les supprime.

## L’identifiant

Les boutons, les commandes et les mises en page retrouvent une interface personnalisée grâce à son identifiant.

- Utilisez uniquement des lettres minuscules, des chiffres, `.`, `_` et `-`. Chaque interface personnalisée doit avoir un identifiant qui lui est propre.
- N’utilisez pas l’[identifiant d’un autre écran](/screen-identifiers), comme `title_screen`. L’interface personnalisée partagerait alors ses mises en page avec cet écran.
- Si vous modifiez l’identifiant plus tard, ses mises en page ainsi que les boutons et commandes qui utilisent l’ancien identifiant ne la retrouveront plus. Si vous rétablissez l’ancien identifiant, ils fonctionneront de nouveau.

## Créer sa mise en page

1. Ouvrez l’interface personnalisée.
2. Cliquez sur **barre de menus -> Personnalisation -> Mises en page -> Nouvelle -> Pour l’écran actuel**. La personnalisation est toujours activée pour les interfaces personnalisées.
3. Ajoutez des éléments et enregistrez la mise en page. Consultez l’article [Éditeur de mise en page](/layout-editor).

Une interface personnalisée ne contient rien, pas même un bouton Retour. Ajoutez-y un [bouton](/elements#button) avec l’action [**Retour à l’écran précédent**](/action-scripts#back-to-last-screen), ou laissez l’option **Autoriser la fermeture de l’interface avec Échap** activée pour que les joueurs puissent la quitter.

# Paramètres

L’option **Modifier l’interface** dans **Gérer les interfaces personnalisées** permet de modifier les paramètres de l’interface personnalisée sélectionnée.

| Paramètre | Fonction |
|---|---|
| **Identifiant d’interface personnalisée** | Le nom de l’interface personnalisée. Consultez la section [L’identifiant](#lidentifiant). |
| **Titre de l’écran (facultatif)** | Un titre blanc en haut de l’interface. Laissez ce champ vide pour ne pas en afficher. Les [espaces réservés](/placeholders) fonctionnent, et les clés de localisation du jeu, des mods et des packs de ressources s’affichent dans la langue du joueur. |
| **Autoriser la fermeture de l’interface avec Échap** | La touche `Échap` ferme l’interface. Activé par défaut. |
| **Mettre le jeu/le monde en pause** | Met en pause les mondes solo pendant que l’interface est ouverte. Activé par défaut. |
| **Afficher l’arrière-plan du monde** | Affiche le monde derrière l’interface pendant que vous jouez. En dehors des mondes, ou si cette option est désactivée, le panorama de Minecraft s’affiche. Activé par défaut. |
| **Afficher le voile sur l’arrière-plan du monde** | Floute et assombrit le monde ou le panorama derrière l’interface, comme dans le menu Pause. Fonctionne uniquement avec **Afficher l’arrière-plan du monde** : sans cette option, le panorama est toujours flouté et assombri. Activé par défaut. |
| **Mode fenêtre contextuelle** | Affiche l’interface par-dessus le menu depuis lequel elle a été ouverte. Consultez la section [Mode fenêtre contextuelle](#mode-fenetre-contextuelle). |
| **Voile d’arrière-plan du mode fenêtre contextuelle** | Floute le menu derrière la fenêtre contextuelle. Fonctionne uniquement avec le **Mode fenêtre contextuelle**. Activé par défaut. |

- Le flou est aussi intense que celui de l’option **Flou de l’arrière-plan des menus** de Minecraft.
- Un [arrière-plan de menu](/menu-backgrounds) dans la mise en page recouvre tous ces éléments : le monde, le panorama et le menu derrière une fenêtre contextuelle.
- L’éditeur de mise en page ne permet pas de modifier le titre (**Titre personnalisé de l’écran**) des interfaces personnalisées. Modifiez plutôt **Titre de l’écran (facultatif)**. Pour créer un titre avec sa propre police, couleur ou position, laissez ce champ vide et ajoutez un [élément de texte](/elements#text).

## Mode fenêtre contextuelle

Avec le **Mode fenêtre contextuelle**, le menu depuis lequel l’interface personnalisée a été ouverte reste visible derrière celle-ci, avec sa mise en page. Il est impossible de cliquer sur ce menu tant que la fenêtre contextuelle est ouverte.

- Les fenêtres contextuelles conviennent mieux aux contenus de petite taille, comme une boîte d’informations, une confirmation ou un panneau de paramètres. Laissez un peu d’espace libre pour que le menu de derrière reste visible.
- N’ajoutez pas d’arrière-plan de menu à la mise en page d’une fenêtre contextuelle, sinon le menu de derrière disparaîtra.
- Si l’interface personnalisée est ouverte alors qu’aucun menu n’est ouvert, par exemple avec une touche pendant le jeu, aucun menu ne pourra s’afficher derrière. L’arrière-plan normal de l’interface apparaîtra alors.

# Ouvrir une interface personnalisée

Tout ce qui permet d’ouvrir des écrans peut aussi ouvrir des interfaces personnalisées en utilisant leur identifiant :

- **Boutons :** utilisez l’action [**Ouvrir un écran ou une interface personnalisée**](/action-scripts#open-screen-or-custom-gui) avec la valeur `modpack_info`.
- **Touches :** ajoutez un [écouteur **À l’appui d’une touche du clavier**](/listeners#listener-variables) avec la même action. Il ouvre l’interface personnalisée dans les menus et pendant le jeu.
- **Commandes :** `/openguiscreen modpack_info`, y compris depuis les serveurs, les blocs de commande et les récompenses de quêtes. Consultez la section [Commandes](/commands#openguiscreen).
- **Quitter un monde :** l’action [**Quitter le monde ou le serveur**](/action-scripts#leave-world-or-server) ouvre l’interface personnalisée après avoir quitté le monde, si vous lui indiquez son identifiant.

Les interfaces personnalisées font partie de la configuration FancyMenu de chaque joueur. Un serveur ne peut ouvrir que les interfaces personnalisées dont ses joueurs disposent, comme celles du modpack.

Pour quitter une interface personnalisée :

- `Échap` (si **Autoriser la fermeture de l’interface avec Échap** est activé) et l’action **Retour à l’écran précédent** ramènent au menu depuis lequel l’interface a été ouverte. Si aucun menu n’était ouvert, `Échap` ramène au jeu.
- L’action [**Fermer l’écran**](/action-scripts#close-screen) ferme l’interface. En dehors des mondes, l’écran titre s’ouvre.

# Remplacer un écran existant

Une interface personnalisée peut remplacer un menu du jeu ou d’un mod. Chaque fois que ce menu devrait s’ouvrir, l’interface personnalisée s’ouvre à sa place.

> [!WARNING]
> Le menu remplacé ne s’ouvre jamais : ses fonctionnalités ne sont donc pas exécutées, et les autres mods qui en ont besoin risquent de ne plus fonctionner. Dans la mesure du possible, modifiez les menus avec une mise en page normale. Ne remplacez un menu que si une mise en page ne permet pas de faire ce dont vous avez besoin.

1. Activez **barre de menus -> Personnalisation -> Paramètres -> Mode de personnalisation avancé**.
2. Ouvrez le menu que vous souhaitez remplacer.
3. Cliquez sur **barre de menus -> Personnalisation -> Interfaces personnalisées -> Remplacer l’écran actuel par une interface personnalisée**.
4. Confirmez l’avertissement, puis sélectionnez l’interface personnalisée dans **Choisir une interface personnalisée**.

L’interface personnalisée s’ouvre immédiatement. `Échap` et l’action **Retour à l’écran précédent** permettent de revenir au menu qui était ouvert avant celui qui a été remplacé.

Pour annuler ce remplacement, ouvrez **barre de menus -> Personnalisation -> Interfaces personnalisées -> Gérer les écrans remplacés**, cliquez sur **Supprimer la règle de remplacement** sous l’écran, puis sur **Terminé**.

> [!TIP]
> Pour remplacer un menu uniquement dans certaines situations, par exemple lorsque seule une [variable](/variables) est définie, utilisez plutôt un [écouteur **À l’ouverture d’un écran**](/listeners#on-screen-opened) avec une instruction IF.

# Gérer les interfaces personnalisées

- **Nouvelle interface**, **Modifier l’interface** et **Ouvrir l’interface** dans **Gérer les interfaces personnalisées** permettent respectivement d’ajouter, de modifier et d’ouvrir des interfaces personnalisées.
- **Supprimer l’interface** supprime l’interface personnalisée sélectionnée après confirmation. Ses mises en page sont conservées et réapparaîtront dans toute nouvelle interface personnalisée portant le même identifiant.
- La barre de recherche permet de retrouver des interfaces personnalisées par leur identifiant.
- **barre de menus -> Aide -> Exporter pour l’IA -> Interfaces personnalisées** exporte toutes les interfaces personnalisées et les règles de remplacement pour une [conversation avec une IA](/export-for-ai).

Les interfaces personnalisées et les règles de remplacement sont enregistrées dans `config/fancymenu/custom_gui_screens.txt`. Leurs mises en page sont enregistrées dans `config/fancymenu/customization/`, comme toutes les autres (consultez [Emplacements de stockage des données](/data-storage-locations)). Chaque [profil](/profiles) possède ses propres interfaces personnalisées.
