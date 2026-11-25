---
title: Entités de joueur
description: >-
  Affichez des joueurs dans vos menus avec l’élément Entité de joueur, avec leur
  skin, leur nom, leur pose, leur armure et plus encore.
sourceBlobSha: b8f8d4340ca3a87e1c55c86f95f36786ab840644
---

# Entités de joueur

L’élément Entité de joueur affiche un joueur en 3D, comme le personnage du joueur à côté des boutons de l’écran titre. Il peut copier le joueur actuel, afficher n’importe quel autre joueur ou représenter un personnage que vous avez créé, avec son propre skin, sa cape et son nom.

<img width="800" alt="Cinq entités de joueur : un vrai joueur avec un skin et une cape, un joueur en armure de diamant enchantée avec une épée et un bouclier, un joueur accroupi, un joueur qui fait signe et un bébé" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/player_entities_showcase.png?raw=true">

> [!IMPORTANT]
> À partir de Minecraft 1.20.1, les entités de joueur nécessitent le mod Fancy Entity Renderer ([CurseForge](https://www.curseforge.com/minecraft/mc-mods/fancy-entity-renderer), [Modrinth](https://modrinth.com/mod/fancy-entity-renderer)). Sans celui-ci, elles apparaissent sous la forme d’un carré rouge. Tant qu’aucune version du mod n’est disponible pour votre version de Minecraft, les entités de joueur ne peuvent pas s’y afficher.

# Ajouter une entité de joueur

Faites un clic droit sur l’arrière-plan de l’éditeur, puis cliquez sur **Nouvel élément -> Entité de joueur**. Faites glisser ses poignées pour modifier sa taille. La taille du joueur dépend de la hauteur de l’élément.

Tous les paramètres ci-dessous se trouvent dans le menu contextuel de l’élément.

# Joueur affiché

- **Copier le joueur client** affiche le joueur actuel, avec son nom, son skin et sa cape. Lorsque cette option est activée, les paramètres du nom, du skin et de la cape sont verrouillés.
- **Nom du joueur** peut être n’importe quel nom, même s’il ne correspond pas à un vrai joueur. Les [espaces réservés](/placeholders) sont pris en charge.
- **Afficher le nom du joueur** affiche le nom au-dessus de la tête. Lorsque **Rotation de l’étiquette de nom** est désactivé, celle-ci ne tourne pas avec le joueur.

## Skin et cape

- **Skin automatique** et **Cape automatique** chargent le skin et la cape du joueur correspondant au **Nom du joueur**. Une connexion Internet est nécessaire.
- **Texture du skin** et **Texture de la cape** utilisent vos propres fichiers de skin et de cape, par exemple un skin provenant de vos [ressources](/resources). Les skins sont les fichiers de skin Minecraft habituels.
- **Skin fin** est destiné aux skins avec des bras fins, comme celui d’Alex. **Skin automatique** et **Copier le joueur client** détectent automatiquement ce type de skin.

# Pose et mouvement

<img width="800" alt="Deux entités de joueur suivent le pointeur de la souris lorsqu’il se déplace : celle de gauche ne tourne que la tête, celle de droite tourne la tête et le corps" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/player_entities_follow_mouse.gif?raw=true">

- **La tête suit la souris** et **Le corps suit la souris** font regarder le joueur vers le pointeur de la souris. Ces deux options sont activées par défaut pour les nouvelles entités de joueur.
- **Pose** choisit une pose du corps : **Debout**, **Accroupi**, **Allongé**, **En train de nager**, **En train de mourir** ou **Attaque tourbillon**.
- **Mouvement du corps** anime la pose.

## Pose de l’entité

**Pose de l’entité** ouvre une fenêtre qui permet de régler la rotation X, Y et Z de la **Tête**, du **Corps**, du **Bras gauche**, du **Bras droit**, de la **Jambe gauche** et de la **Jambe droite**, de `-180` à `180`.

<img width="800" alt="La fenêtre Pose de l’entité avec des curseurs de rotation pour la tête et le corps du joueur" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/player_entities_pose_window.png?raw=true">

**Mode avancé**, à côté d’un curseur, le transforme en valeur textuelle prenant en charge les [espaces réservés](/placeholders). Si elle contient une [variable](/variables), par exemple `$$arm_angle`, un [planificateur](/schedulers) peut animer le joueur en modifiant cette variable.

# Armure, objets et plus encore

- **Armure et outils** équipe le joueur : **Armure de tête**, **Armure de torse**, **Armure de jambes**, **Armure de pieds**, **Outil main gauche** et **Outil main droite**. Indiquez l’identifiant d’un objet, par exemple `minecraft:diamond_sword`. Les identifiants d’objets prennent en charge les espaces réservés. **Enchanter l’armure de tête** et les autres options d’enchantement ajoutent l’effet de scintillement des enchantements.
- **Est un bébé** rend le joueur petit, comme un bébé.
- **Perroquet** place un perroquet sur l’épaule droite, ou sur l’épaule gauche si **Perroquet sur l’épaule gauche** est activé.

# Bon à savoir

- Les entités de joueur ne peuvent pas être tournées, inclinées, estompées ni rendues transparentes.
- Pour afficher uniquement la tête d’un joueur, consultez [Têtes de joueur](/player-heads).
- Sur Minecraft 1.19.2, les entités de joueur n’ont pas besoin de Fancy Entity Renderer, mais elles proposent moins de paramètres : **Accroupi** au lieu de **Pose**, et pas d’options **Rotation de l’étiquette de nom**, **Mouvement du corps** ni **Armure et outils**. Leur taille est définie par **Échelle de l’entité** (30 par défaut, donc `60` correspond à une taille deux fois plus grande), plutôt que par la taille de l’élément.
