---
title: Superpositions de décoration
description: >-
  Ajoutez des superpositions visuelles plein écran aux menus dans l’éditeur de
  mise en page FancyMenu.
---
# Superpositions de décoration

Les superpositions de décoration sont des effets plein écran qui s’affichent devant les éléments de votre menu.

Elles sont utiles lorsque vous souhaitez ajouter de l’ambiance ou du mouvement à un menu sans créer ces effets manuellement.

# Où le trouver

Ouvrez une mise en page dans l’éditeur de mise en page, puis faites un clic droit sur l’arrière-plan de l’éditeur et ouvrez **Superpositions de décoration**.

# Démarrage rapide

1. Ouvrez une mise en page dans l’éditeur de mise en page.
2. Faites un clic droit sur l’arrière-plan (zone vide).
3. Ouvrez **Superpositions de décoration**.
4. Sélectionnez un type de superposition.
5. Réglez **Afficher la superposition** sur **Activé**.
6. Configurez les paramètres de la superposition.
7. Enregistrez la mise en page et testez l’écran.

# Fonctionnement des types de superposition

Chaque type de superposition possède son propre sous-menu et son propre interrupteur **Afficher la superposition**.

- Vous pouvez activer uniquement les types que vous souhaitez.
- Vous pouvez combiner plusieurs types activés dans une même mise en page.
- Les paramètres sont propres à chaque type de superposition (par exemple couleur, intensité, vitesse, densité, échelle, comportement spécial).

> [!INFO]
> Il est possible d’empiler plusieurs instances du même type de superposition en utilisant plusieurs mises en page avec le même type activé.

# Types de superposition

- **Chute de neige** : neige avec accumulation optionnelle sur les surfaces/boutons.
- **Pluie** : pluie avec flaques, gouttes et éclairs de tonnerre optionnels.
- **Lucioles** : groupes de lucioles en mouvement avec quantité de groupes, densité, taille et couleur configurables.
- **Guirlandes lumineuses** : combinaisons de guirlandes configurables, couleurs des lumières, comportement vent/clignotement et mode couleur de fête.
- **Feuilles** : feuilles qui tombent avec couleurs, vent, vitesse, échelle et densité configurables.
- **Feux d’artifice** : feux d’artifice fréquents avec quantité, taille d’explosion et échelle configurables.
- **Confettis** : pluie de confettis avec mode confettis au clic de souris en option.
- **Buddy** : un animal de compagnie virtuel interactif avec faim, bonheur, énergie, amusement, activités, montée de niveau, succès et état persistant.
- **Navigateur** : superposition plein écran du navigateur avec URL et paramètres multimédias.
- **Shader GLSL** : superposition plein écran de shader personnalisé (pour des visuels animés ou statiques basés sur des shaders).

# Animal de compagnie virtuel Buddy

La superposition **Buddy** est un animal de compagnie virtuel de type Tamagotchi, pas seulement un personnage visuel. Il se déplace le long du bas de l’écran, affiche des bulles de pensée pour ses besoins, réagit aux interactions et conserve son état entre les sessions de jeu.

## Besoins et commandes

Buddy suit quatre valeurs de `0` à `100` :

- **Faim** diminue avec le temps et se restaure avec de la nourriture.
- **Bonheur** diminue avec le temps et augmente grâce aux soins, notamment les caresses et le jeu.
- **Énergie** diminue lorsqu’il est éveillé et pendant les activités, puis se régénère lorsqu’il dort.
- **Amusement** diminue avec le temps et augmente pendant le jeu.

Utilisez ces commandes à la souris et l’écran d’état pour en prendre soin :

- **Clic gauche sur Buddy** pour le caresser. Un clic gauche pendant qu’il dort le réveille et applique une légère pénalité de bonheur.
- **Clic droit sur Buddy** pour ouvrir son écran d’état. L’onglet Stats affiche les quatre besoins, le niveau et l’XP ; l’onglet Succès affiche la progression des succès.
- Sélectionnez **Nourrir** dans l’écran d’état, puis faites glisser la nourriture vers Buddy. La nourriture restaure la faim et le bonheur.
- Sélectionnez **Jouer** dans l’écran d’état, puis faites glisser et relâchez la balle. La balle utilise le mouvement de la souris pour calculer la vitesse du lancer, et Buddy peut la poursuivre, l’attraper, la tenir et jouer avec.
- Sélectionnez **Dormir** lorsque le bouton est disponible pour restaurer l’énergie. Buddy s’endort aussi automatiquement lorsque son énergie devient critique.
- Buddy laisse parfois des crottes derrière lui. **Clic gauche sur la crotte** pour la nettoyer. Laisser au moins trois crottes à l’écran réduit continuellement le bonheur jusqu’à ce qu’il en reste moins de trois ; le nombre maximal de crottes est configurable.

## XP, niveaux et succès

Prendre soin de Buddy, nettoyer les crottes, maintenir de bons besoins et atteindre d’autres objectifs récompense de l’XP. Buddy commence au niveau 1 et peut atteindre le niveau 30. Les niveaux plus élevés réduisent progressivement la baisse de la faim, du bonheur et de l’énergie (jusqu’à 50 % au niveau 30) et améliorent plusieurs effets liés aux soins et à l’XP.

Les succès suivent la progression des interactions, des stats, des niveaux, des sessions et des objectifs spéciaux. Ouvrez l’écran d’état avec un clic droit pour consulter les deux systèmes de progression.

## Mort et réinitialisation de la sauvegarde

**Buddy Peut Mourir** est activé par défaut. Si la faim ou le bonheur reste continuellement à `0` pendant **10 heures réelles**, Buddy meurt et est remplacé par une pierre tombale. Faire remonter le besoin à zéro avant l’expiration du minuteur réinitialise le minuteur de ce besoin ; désactiver **Buddy Peut Mourir** efface les deux minuteurs.

Pour recommencer après la mort, cliquez avec le bouton gauche sur la pierre tombale. Vous pouvez aussi utiliser **Réinitialiser la sauvegarde de Buddy** dans les paramètres de la superposition Buddy à tout moment. La réinitialisation supprime à la fois la sauvegarde de l’état de l’animal et la sauvegarde séparée du niveau/succès pour cette instance de superposition.

> [!WARNING]
> La réinitialisation d’une sauvegarde Buddy supprime définitivement ses besoins, son niveau, son XP, ses succès, ses compteurs d’activité et l’état enregistré de ses crottes.

## Persistance et personnalisation

L’état de Buddy est sauvegardé automatiquement environ toutes les deux minutes et lorsque son écran se ferme. L’état de l’animal et l’état de progression utilisent des fichiers JSON séparés pour chaque instance de superposition dans `<game-directory>/fancymenu_data/buddy/`. Consultez [Emplacements de stockage des données](./data-storage-locations) pour la référence complète des chemins FancyMenu.

Les paramètres de la superposition vous permettent également de remplacer l’atlas de sprites de Buddy, les objets d’interaction, les icônes de besoins, les textures de l’écran d’état et la pierre tombale. Les paramètres avancés des stats contrôlent la décroissance, les coûts et gains des activités, l’efficacité des soins, le nombre maximal de crottes et l’activation ou non de la mort.

# Superposition du navigateur : interactive ou passive

La superposition du navigateur peut être configurée soit comme un navigateur interactif, soit comme une couche visuelle passive.

- Les paramètres **Traiter la souris/le clavier** contrôlent si le navigateur gère lui-même les entrées.
- Les paramètres **Consommer la souris/le clavier** contrôlent si les entrées sont bloquées pour le menu situé derrière.

Exemples de configuration pratiques :

- Navigateur interactif au premier plan : activez **Traiter** et **Consommer**.
- Couche de navigateur uniquement visuelle : désactivez **Traiter** et désactivez **Consommer**.

> [!IMPORTANT]
> La superposition de décoration **Navigateur** nécessite le mod **MCEF**.
