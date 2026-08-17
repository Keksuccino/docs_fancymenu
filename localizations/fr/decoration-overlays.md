---
title: Superpositions décoratives
description: >-
  Ajoutez des superpositions visuelles en plein écran aux menus dans l’éditeur
  de mise en page de FancyMenu.
---
# Superpositions décoratives

Les superpositions décoratives sont des effets en plein écran qui s’affichent devant les éléments de votre menu.

Elles sont utiles lorsque vous souhaitez ajouter une atmosphère ou du mouvement à un menu sans devoir créer ces effets manuellement.

# Où les trouver

Ouvrez une mise en page dans l’éditeur, puis faites un clic droit sur l’arrière-plan de l’éditeur et ouvrez **Superpositions décoratives**.

# Démarrage rapide

1. Ouvrez une mise en page dans l’éditeur.
2. Faites un clic droit sur l’arrière-plan (zone vide).
3. Ouvrez **Superpositions décoratives**.
4. Sélectionnez un type de superposition.
5. Réglez **Afficher la superposition** sur **Activé**.
6. Configurez les paramètres de la superposition.
7. Enregistrez la mise en page et testez l’écran.

# Fonctionnement des types de superposition

Chaque type de superposition possède son propre sous-menu et son propre bouton **Afficher la superposition**.

- Vous pouvez activer uniquement les types souhaités.
- Vous pouvez combiner plusieurs types activés dans une même mise en page.
- Les paramètres sont propres à chaque type de superposition (par exemple la couleur, l’intensité, la vitesse, la densité, l’échelle ou certains comportements spéciaux).

> [!INFO]
> Il est possible d’empiler plusieurs instances d’un même type de superposition en utilisant plusieurs mises en page avec ce même type activé.

# Types de superposition

- **Chute de neige** : chute de neige avec accumulation facultative sur les surfaces et les boutons.
- **Pluie** : pluie avec flaques et gouttes facultatives, ainsi que des éclairs de tonnerre optionnels.
- **Lucioles** : groupes de lucioles en mouvement avec quantité, densité, taille et couleur configurables.
- **Guirlandes lumineuses** : combinaisons de guirlandes, couleurs des ampoules, comportement au vent et au scintillement, ainsi qu’un mode de couleurs de fête configurables.
- **Feuilles** : feuilles qui tombent avec couleurs, vent, vitesse, échelle et densité configurables.
- **Feux d’artifice** : feux d’artifice fréquents avec quantité, taille des explosions et échelle configurables.
- **Confettis** : pluie de confettis avec un mode de confettis déclenché par les clics de souris, en option.
- **Buddy** : animal virtuel interactif avec faim, bonheur, énergie, amusement, activités, niveaux, succès et état persistant.
- **Navigateur** : superposition de navigateur en plein écran avec paramètres d’URL et de contenu multimédia.
- **Shader GLSL** : superposition de shader personnalisé en plein écran (pour des visuels animés ou statiques basés sur des shaders).

# Animal virtuel Buddy

La superposition **Buddy** est un animal virtuel de type Tamagotchi, et pas seulement un personnage visuel. Il se déplace en bas de l’écran, affiche des bulles de pensée pour signaler ses besoins, réagit aux interactions et conserve son état entre les sessions de jeu.

## Besoins et commandes

Buddy suit quatre valeurs comprises entre `0` et `100` :

- La **Faim** diminue avec le temps et est restaurée par la nourriture.
- Le **Bonheur** diminue avec le temps et augmente grâce aux soins, notamment les caresses et le jeu.
- L’**Énergie** diminue lorsqu’il est éveillé et pendant les activités, puis se régénère lorsqu’il dort.
- L’**Amusement** diminue avec le temps et augmente pendant les parties de jeu.

Utilisez ces commandes de souris et l’écran d’état pour vous en occuper :

- **Clic gauche sur Buddy** pour le caresser. Un clic gauche pendant son sommeil le réveille et applique une légère pénalité de bonheur.
- **Clic droit sur Buddy** pour ouvrir son écran d’état. L’onglet Statistiques affiche les quatre besoins, le niveau et l’XP ; l’onglet Succès affiche la progression des succès.
- Sélectionnez **Nourrir** dans l’écran d’état, puis faites glisser la nourriture jusqu’à Buddy. La nourriture restaure la faim et le bonheur.
- Sélectionnez **Jouer** dans l’écran d’état, puis faites glisser et relâchez la balle. La balle utilise le mouvement de la souris pour calculer la vitesse du lancer, et Buddy peut la poursuivre, l’attraper, la tenir et jouer avec.
- Sélectionnez **Dormir** lorsque le bouton est disponible pour restaurer l’énergie. Buddy s’endort également automatiquement lorsque son énergie devient dangereusement faible.
- Buddy laisse parfois des crottes derrière lui. **Faites un clic gauche sur les crottes** pour les nettoyer. Laisser au moins trois crottes à l’écran réduit continuellement le bonheur jusqu’à ce qu’il en reste moins de trois ; le nombre maximal de crottes est configurable.

## XP, niveaux et succès

S’occuper de Buddy, nettoyer les crottes, maintenir de bons niveaux de besoins et accomplir d’autres étapes importantes rapporte de l’XP. Buddy commence au niveau 1 et peut atteindre le niveau 30. Les niveaux supérieurs réduisent progressivement la diminution de la faim, du bonheur et de l’énergie (jusqu’à 50 % au niveau 30) et améliorent plusieurs effets liés aux soins et à l’XP.

Les succès suivent les interactions, les statistiques, les niveaux, les sessions et certaines étapes spéciales. Ouvrez l’écran d’état avec un clic droit pour consulter ces deux systèmes de progression.

## Mort et réinitialisation de la sauvegarde

**Buddy peut mourir** est activé par défaut. Si la faim ou le bonheur reste continuellement à `0` pendant **10 heures réelles**, Buddy meurt et est remplacé par une pierre tombale. Augmenter le besoin à zéro avant l’expiration du délai réinitialise le minuteur correspondant ; désactiver **Buddy peut mourir** efface les deux minuteurs.

Pour recommencer après sa mort, faites un clic gauche sur la pierre tombale. Vous pouvez également utiliser **Réinitialiser la sauvegarde de Buddy** dans les paramètres de la superposition Buddy à tout moment. La réinitialisation supprime à la fois la sauvegarde de l’état de l’animal et la sauvegarde distincte des niveaux et des succès pour cette instance de superposition.

> [!WARNING]
> La réinitialisation d’une sauvegarde Buddy supprime définitivement ses besoins, son niveau, son XP, ses succès, les compteurs d’activités et l’état sauvegardé de ses crottes.

## Persistance et personnalisation

L’état de Buddy est automatiquement sauvegardé environ toutes les deux minutes et lorsque son écran se ferme. L’état de l’animal et l’état de progression utilisent des fichiers JSON distincts pour chaque instance de superposition dans `<game-directory>/fancymenu_data/buddy/`. Consultez [Emplacements de stockage des données](./data-storage-locations) pour connaître le chemin complet des données de FancyMenu.

Les paramètres de la superposition vous permettent également de remplacer l’atlas de sprites de Buddy, les objets d’interaction, les icônes des besoins, les textures de l’écran d’état et la pierre tombale. Les paramètres avancés des statistiques contrôlent la diminution des besoins, les coûts et gains des activités, l’efficacité des soins, le nombre maximal de crottes et l’activation ou non de la mort.

# Superposition Navigateur : interactive ou passive

La superposition Navigateur peut être configurée soit comme un navigateur interactif, soit comme une couche visuelle passive.

- Les paramètres **Traiter la souris/le clavier** contrôlent si le navigateur lui-même gère les entrées.
- Les paramètres **Intercepter la souris/le clavier** contrôlent si les entrées sont bloquées pour le menu situé derrière.

Exemples de configuration pratiques :

- Navigateur interactif au premier plan : activez **Traiter** et **Intercepter**.
- Couche de navigateur uniquement visuelle : désactivez **Traiter** et **Intercepter**.

> [!IMPORTANT]
> La superposition décorative Navigateur nécessite le mod **[Rinku](https://modrinth.com/mod/rinku)**.
