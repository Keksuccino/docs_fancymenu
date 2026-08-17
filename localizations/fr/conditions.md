---
title: Conditions (exigences)
description: Comment utiliser les exigences de chargement.
---
# Exigences

Les exigences (appelées **Exigences de chargement** dans certains menus) affichent ou masquent du contenu selon des conditions telles que l'état de survol, la taille de la fenêtre ou le chargement d'un monde.

Vous pouvez les utiliser sur des [éléments](./elements), des mises en page entières et des [scripts d'action](./action-scripts).

# Ajouter des exigences aux éléments

Pour ajouter des exigences à un élément, faites un clic droit dessus, puis sélectionnez **Exigences de chargement**.

Les exigences sont vérifiées tant que le menu est ouvert : les éléments sont donc mis à jour lorsqu'une condition change.

# Exigences appliquées à toute une mise en page

Vous pouvez également modifier la visibilité de mises en page entières en faisant un clic droit sur l'**arrière-plan de l'éditeur**, puis en cliquant sur **Exigences de chargement [toute la mise en page]**.

Lorsqu'un résultat appliqué à toute une mise en page change, FancyMenu reconstruit l'écran actuel et applique les mises en page dont les exigences sont désormais satisfaites.

# Scripts d'action

Les exigences peuvent également être utilisées dans les scripts d'action.
Vous pouvez les ajouter dans l'écran de l'éditeur de scripts d'action et les utiliser pour exécuter certaines actions uniquement lorsque la condition de l'exigence est satisfaite.

# Combiner les exigences

- Les exigences situées en dehors des groupes utilisent **ET** : elles doivent toutes être satisfaites.
- Dans un groupe, choisissez **ET** ou **OU**.
- Utilisez **SI NON** pour inverser une exigence.

Ces règles sont les mêmes pour les éléments, les mises en page et les scripts d'action.

# Valeurs des exigences

Pour les exigences nécessitant une valeur, utilisez **Modifier la valeur de l'exigence** et suivez la description affichée dans l'éditeur. Certains champs prennent en charge la complétion avec la touche **TAB**.

Si une exigence importée ne fonctionne plus après la modification de FancyMenu ou de modules complémentaires, modifiez-la dans l'écran des exigences et consultez `logs/latest.log` pour rechercher les erreurs.

L'éditeur d'exigences prend en charge un menu contextuel accessible par clic droit, la navigation au clavier, la recherche, l'annulation et le rétablissement (`Ctrl/Command + Z` / `Ctrl/Command + Y`), ainsi que `Ctrl/Command + S` pour enregistrer.

# Exigences en détail

Cette section répertorie les exigences intégrées de FancyMenu.

## L'élément est-il survolé (`fancymenu_visibility_requirement_is_element_hovered`)

**Objectif :** vérifie si le curseur de la souris survole un élément spécifique.

**Valeur :** requise — [Identifiant de l'élément](./element-identifiers) cible (par exemple, `some_element_ID`).

## L'élément est-il sélectionné (`is_element_focused`)

**Objectif :** vérifie si un élément spécifique possède actuellement le focus du clavier (par exemple, un champ de texte ou un bouton sélectionné).

**Valeur :** requise — ID de l'élément cible (le même ID que celui affiché dans l'éditeur)

> [!NOTE]
> Le focus et le survol sont deux états différents. Un élément peut conserver son apparence de sélection après que le pointeur l'a quitté ; un clic ou la navigation au clavier peut lui donner le focus.

## Un élément est-il survolé (`fancymenu_visibility_requirement_is_any_element_hovered`)

**Objectif :** vérifie les éléments visibles/rendables de la couche de personnalisation active, y compris les éléments provenant de mises en page empilées.

**Valeur :** non requise

## Un bouton est-il survolé (`fancymenu_visibility_requirement_is_any_button_hovered`)

**Objectif :** vérifie si un bouton vanilla ou personnalisé visible/rendable de la couche de personnalisation active est survolé, y compris les boutons provenant de mises en page empilées.

**Valeur :** non requise

## La mise en page est-elle activée (`fancymenu_visibility_requirement_is_layout_enabled`)

**Objectif :** vérifie si une mise en page spécifique est actuellement activée.

**Valeur :** requise — Nom de la mise en page (par exemple, `my_cool_main_menu_layout`)

## Le planificateur est-il en cours d'exécution (`fancymenu_visibility_requirement_is_scheduler_running`)

**Objectif :** vérifie si un [planificateur](./schedulers) est actuellement en cours d'exécution.

**Valeur :** requise — ID du planificateur (par exemple, `my_scheduler`)

## Échelle de l'interface (`fancymenu_loading_requirement_is_gui_scale`)

**Objectif :** vérifie si l'échelle actuelle de l'interface correspond à certaines conditions.

**Valeur :** requise — Utilisez un nombre pour l'égalité, `>` pour une valeur supérieure ou `<` pour une valeur inférieure.

Plusieurs conditions séparées par des virgules sont combinées avec ET. Par exemple, `>1,<4` n'est satisfaite que lorsque l'échelle de l'interface est supérieure à `1` et inférieure à `4`.

## Le bouton est-il actif (`fancymenu_visibility_requirement_is_button_active`)

**Objectif :** vérifie si un bouton spécifique est actif (cliquable).

**Valeur :** requise — ID de l'élément correspondant au bouton cible (par exemple, "some_element_ID")

## Titre de l'écran (`is_menu_title`)

**Objectif :** vérifie si le titre AFFICHÉ de l'écran correspond à un texte ou à une clé de localisation spécifique. Cette exigence vérifie uniquement le nom/titre affiché de l'écran, comme "Options" ou "Pause". Elle ne vérifie PAS l'identifiant du menu/de l'écran (comme `title_screen`) !

**Valeur :** requise — Texte exact du titre ou clé de localisation de l'écran

## Une touche est-elle enfoncée (`is_key_pressed`)

**Objectif :** vérifie si une touche spécifique du clavier est actuellement enfoncée.

**Valeur :** requise — Code de la touche cible. Sélectionné via une interface lors de la modification de la valeur de l'exigence.

## Un écran est-il ouvert (`is_any_screen_open`)

**Objectif :** vérifie si un écran/menu est actuellement ouvert (renvoie false si aucun écran n'est affiché).

**Valeur :** non requise

## L'overlay de débogage de Minecraft est-il activé (`is_debug_overlay_enabled`)

**Objectif :** vérifie si l'overlay de débogage F3 est actuellement visible.

**Valeur :** non requise

## Type de curseur actif (`is_active_cursor_type`)

**Objectif :** vérifie si le type de curseur actuellement actif de FancyMenu correspond à un type de curseur standard spécifique.

**Valeur :** requise — Type de curseur : `normal`, `writing`, `crosshair`, `pointing_hand`, `resize_horizontal`, `resize_vertical`, `resize_nwse`, `resize_nesw`, `resize_all` ou `not_allowed`

## Barre de menu de personnalisation visible (`is_customization_menu_bar_visible`)

**Objectif :** vérifie si la barre de menu de personnalisation de FancyMenu est actuellement visible.

**Valeur :** non requise

## Mode Modpack activé (`is_modpack_mode_enabled`)

**Objectif :** vérifie si le mode Modpack de FancyMenu est activé.

**Valeur :** non requise

## Le bouton de la souris est-il enfoncé (`mouse_click`)

**Objectif :** renvoie true tant qu'un bouton de souris spécifique est maintenu enfoncé. Il ne s'agit pas d'un événement de clic ponctuel ; utilisez le [listener **Lorsqu'un bouton de souris est cliqué**](./listeners#on-mouse-button-clicked-mouse_button_clicked) lorsqu'une action doit être exécutée une seule fois par clic.

**Valeur :** requise — `left` ou `right` pour indiquer le bouton de souris à vérifier

## Plein écran (`fancymenu_loading_requirement_is_fullscreen`)

**Objectif :** vérifie si le jeu est actuellement en mode plein écran.

**Valeur :** non requise

## Largeur de la fenêtre (`fancymenu_loading_requirement_is_window_width`)

**Objectif :** vérifie si la largeur de la fenêtre du jeu correspond à certaines valeurs.

**Valeur :** requise — Largeur de la fenêtre en pixels (par exemple, "1920"). Plusieurs valeurs peuvent être indiquées en les séparant par des virgules.

## Hauteur de la fenêtre (`fancymenu_loading_requirement_is_window_height`)

**Objectif :** vérifie si la hauteur de la fenêtre du jeu correspond à certaines valeurs.

**Valeur :** requise — Hauteur de la fenêtre en pixels (par exemple, "1080"). Plusieurs valeurs peuvent être indiquées en les séparant par des virgules.

## Largeur de la fenêtre supérieure à (`fancymenu_loading_requirement_is_window_width_bigger_than`)

**Objectif :** vérifie si la largeur de la fenêtre du jeu est supérieure à une valeur spécifique.

**Valeur :** requise — Largeur de la fenêtre en pixels (par exemple, "1920")

## Hauteur de la fenêtre supérieure à (`fancymenu_loading_requirement_is_window_height_bigger_than`)

**Objectif :** vérifie si la hauteur de la fenêtre du jeu est supérieure à une valeur spécifique.

**Valeur :** requise — Hauteur de la fenêtre en pixels (par exemple, "1080")

## Multijoueur (`fancymenu_loading_requirement_is_multiplayer`)

**Objectif :** vérifie si le joueur se trouve actuellement dans un monde multijoueur.

**Valeur :** non requise

## Solo (`fancymenu_loading_requirement_is_singpleplayer`)

**Objectif :** vérifie si le joueur se trouve actuellement dans un monde solo.

**Valeur :** non requise

## Un monde est-il chargé (`fancymenu_loading_requirement_is_world_loaded`)

**Objectif :** vérifie si un monde est actuellement chargé.

**Valeur :** non requise

## Mode Aventure (`fancymenu_visibility_requirement_is_adventure`)

**Objectif :** vérifie si le joueur est actuellement en mode de jeu Aventure.

**Valeur :** non requise

## Mode Créatif (`fancymenu_visibility_requirement_is_creative`)

**Objectif :** vérifie si le joueur est actuellement en mode de jeu Créatif.

**Valeur :** non requise

## Mode Spectateur (`fancymenu_visibility_requirement_is_spectator`)

**Objectif :** vérifie si le joueur est actuellement en mode de jeu Spectateur.

**Valeur :** non requise

## Mode Survie (`fancymenu_visibility_requirement_is_survival`)

**Objectif :** vérifie si le joueur est actuellement en mode de jeu Survie.

**Valeur :** non requise

## Mode de jeu (`is_gamemode`)

**Objectif :** vérifie si le joueur est dans un mode de jeu spécifique.

**Valeur :** requise — Nom du mode de jeu (par exemple, "creative", "survival", "adventure", "spectator")

## Difficulté (`is_difficulty`)

**Objectif :** vérifie si la difficulté actuelle du jeu correspond à une valeur spécifique.

**Valeur :** requise — Nom de la difficulté (par exemple, "peaceful", "easy", "normal", "hard")

## Hardcore (`is_hardcore`)

**Objectif :** vérifie si le monde actuellement chargé est en mode Hardcore.

**Valeur :** non requise

## Perspective de la caméra (`is_camera_perspective`)

**Objectif :** vérifie si la perspective actuelle de la caméra correspond à une perspective spécifique.

**Valeur :** requise — `first_person`, `third_person_back` ou `third_person_front`

## Pluie (`is_raining`)

**Objectif :** vérifie s'il pleut actuellement à l'emplacement du joueur.

**Valeur :** non requise

## Orage (`is_thundering`)

**Objectif :** vérifie si un orage est actuellement en cours dans le monde du joueur.

**Valeur :** non requise

## Temps dégagé (`is_clear_weather`)

**Objectif :** vérifie si le temps est actuellement dégagé (sans pluie ni orage).

**Valeur :** non requise

## Neige (`is_snowing`)

**Objectif :** vérifie s'il neige actuellement à l'emplacement du joueur.

**Valeur :** non requise

## Le joueur court (`is_player_running`)

**Objectif :** vérifie si le joueur est actuellement en train de sprinter.

**Valeur :** non requise

## Le joueur se baisse (`is_player_sneaking`)

**Objectif :** vérifie si le joueur est actuellement accroupi.

**Valeur :** non requise

## Le joueur utilise un objet (`is_player_using_item`)

**Objectif :** vérifie si le joueur utilise actuellement un objet.

**Valeur :** non requise

## Le joueur nage (`is_player_swimming`)

**Objectif :** vérifie si le joueur est actuellement en train de nager.

**Valeur :** non requise

## Le joueur saute ou tombe (`is_player_jumping`)

**Objectif :** renvoie true tant que le joueur est dans les airs lors d'un saut ou d'une chute normale. La nage, les fluides, le vol avec une élytre, le sommeil, la nage visuelle et le fait de ramper sont exclus.

**Valeur :** non requise

## Le joueur est sous l'eau (`is_player_under_water`)

**Objectif :** vérifie si le joueur est complètement sous l'eau.

**Valeur :** non requise

## Le joueur est dans l'eau (`is_player_in_water`)

**Objectif :** vérifie si le joueur est dans l'eau (il peut être partiellement immergé).

**Valeur :** non requise

## Le joueur est dans la lave (`is_player_in_lava`)

**Objectif :** vérifie si le joueur est dans la lave.

**Valeur :** non requise

## Le joueur est dans un fluide (`is_player_in_fluid`)

**Objectif :** vérifie si le joueur se trouve dans un fluide quelconque (eau, lave, etc.).

**Valeur :** non requise

## Le joueur chevauche une entité/un véhicule (`is_player_riding_entity`)

**Objectif :** vérifie si le joueur chevauche une entité.

**Valeur :** non requise

## Le joueur chevauche une entité pouvant sauter (`is_player_riding_jumpable_entity`)

**Objectif :** vérifie si le joueur chevauche une entité capable de sauter (comme un cheval).

**Valeur :** non requise

## Le joueur chevauche une entité possédant des points de vie (`is_player_riding_entity_with_health`)

**Objectif :** vérifie si le joueur chevauche une entité vivante possédant des points de vie (comme un animal, mais pas un bateau).

**Valeur :** non requise

## Le joueur est dans de la neige poudreuse (`is_player_in_powder_snow`)

**Objectif :** vérifie si le joueur se trouve actuellement dans de la neige poudreuse.

**Valeur :** non requise

## Le joueur était dans de la neige poudreuse (`was_player_in_powder_snow`)

**Objectif :** vérifie si le joueur se trouvait dans de la neige poudreuse (utilisé pour les effets qui persistent après qu'il en est sorti).

**Valeur :** non requise

## Le joueur porte une citrouille (`is_player_wearing_pumpkin`)

**Objectif :** vérifie si le joueur porte une citrouille sculptée sur la tête.

**Valeur :** non requise

## Le joueur vole avec une élytre (`is_player_flying_with_elytra`)

**Objectif :** vérifie si le joueur vole actuellement avec une élytre.

**Valeur :** non requise

## Le joueur vole en mode Créatif (`is_player_creative_flying`)

**Objectif :** vérifie si le joueur vole en mode Créatif.

**Valeur :** non requise

## Le joueur possède des cœurs d'absorption (`has_player_absorption_hearts`)

**Objectif :** vérifie si le joueur possède des cœurs d'absorption (cœurs dorés).

**Valeur :** non requise

## Le joueur est affecté par Wither (`is_player_withered`)

**Objectif :** vérifie si le joueur est affecté par l'effet Wither.

**Valeur :** non requise

## Le joueur est complètement gelé (`is_player_fully_frozen`)

**Objectif :** vérifie si le joueur est complètement gelé (généralement à cause de la neige poudreuse).

**Valeur :** non requise

## Le joueur est empoisonné (`is_player_poisoned`)

**Objectif :** vérifie si le joueur est affecté par l'effet de poison.

**Valeur :** non requise

## Le joueur est dans un biome (`is_player_in_biome`)

**Objectif :** vérifie si le joueur se trouve dans un biome spécifique.

**Valeur :** requise — Identifiant du biome (par exemple, `minecraft:birch_forest`)

## Le joueur est dans une dimension (`is_player_in_dimension`)

**Objectif :** vérifie si le joueur se trouve dans une dimension spécifique.

**Valeur :** requise — Identifiant de la dimension (par exemple, `minecraft:overworld`, `minecraft:the_nether`, `minecraft:the_end`)

## Le joueur est dans une structure (`is_player_in_structure`)

**Objectif :** vérifie si le joueur se trouve actuellement à l'intérieur d'une structure spécifique. FancyMenu doit être installé sur le serveur pour les mondes serveur.

**Valeur :** requise — Identifiant de la structure (par exemple, `minecraft:village`)

## Une entité est-elle à proximité (`is_entity_nearby`)

**Objectif :** vérifie si un type d'entité spécifique se trouve dans un certain rayon autour du joueur.

**Valeur :** requise — Format : "rayon:identifiant_entité" (par exemple, `10:minecraft:pig` vérifie la présence de cochons dans un rayon de 10 blocs)

## Un effet est-il actif (`is_effect_active`)

**Objectif :** vérifie si un effet de potion spécifique est actif sur le joueur.

**Valeur :** requise — Identifiant de l'effet (par exemple, `minecraft:speed`, `minecraft:strength`)

## Un effet est-il actif (`is_any_effect_active`)

**Objectif :** vérifie si le joueur possède un effet de potion actif.

**Valeur :** non requise

## Le joueur est gaucher (`is_left_handed`)

**Objectif :** vérifie si le joueur est configuré en mode gaucher dans les options du jeu.

**Valeur :** non requise

## Un emplacement de l'inventaire est-il rempli (`is_inventory_slot_filled`)

**Objectif :** vérifie si un emplacement spécifique de l'inventaire contient un objet.

**Valeur :** requise — Numéro de l'emplacement (0 à 35 pour l'inventaire principal ; les emplacements 0 à 8 correspondent à la barre rapide)

## Un objet est-il survolé dans l'inventaire (`is_item_hovered_in_inventory`)

**Objectif :** vérifie si le curseur survole un objet dans un écran d'inventaire.

**Valeur :** non requise

## Le curseur tient-il un objet de l'inventaire (`is_cursor_holding_inventory_item`)

**Objectif :** vérifie si le curseur tient actuellement une pile d'objets de l'inventaire.

**Valeur :** non requise

## Un emplacement de la barre rapide est-il sélectionné (`is_hotbar_slot_active`)

**Objectif :** vérifie si un emplacement spécifique de la barre rapide est actuellement sélectionné.

**Valeur :** requise — Numéro de l'emplacement de la barre rapide (0 à 8)

## Niveau d'autorisation du joueur (`fancymenu_loading_requirement_has_player_permission_level`)

**Objectif :** vérifie si le joueur possède au moins le niveau d'autorisation/OP indiqué dans le monde ou sur le serveur actuel.

**Valeur :** requise — Numéro du niveau d'autorisation (0 à 4, où 4 correspond à un opérateur du serveur)

## La puissance d'attaque est-elle réduite (`is_attack_strength_weakened`)

**Objectif :** vérifie si la puissance d'attaque du joueur est actuellement réduite (pas complètement chargée).

**Valeur :** non requise

## Jour réel (`fancymenu_visibility_requirement_is_realtime_day`)

**Objectif :** vérifie si le jour actuel du mois réel correspond à une valeur spécifique.

**Valeur :** requise — Numéro du jour (1 à 31). Plusieurs valeurs peuvent être indiquées en les séparant par des virgules.

## Heure réelle (`fancymenu_visibility_requirement_is_realtime_hour`)

**Objectif :** vérifie si l'heure réelle actuelle correspond à une valeur spécifique.

**Valeur :** requise — Heure au format 24 heures (0 à 23). Plusieurs valeurs peuvent être indiquées en les séparant par des virgules.

## Minute réelle (`fancymenu_visibility_requirement_is_realtime_minute`)

**Objectif :** vérifie si la minute réelle actuelle correspond à une valeur spécifique.

**Valeur :** requise — Minute (0 à 59). Plusieurs valeurs peuvent être indiquées en les séparant par des virgules.

## Mois réel (`fancymenu_visibility_requirement_is_realtime_month`)

**Objectif :** vérifie si le mois réel actuel correspond à une valeur spécifique.

**Valeur :** requise — Numéro du mois (1 à 12, où 1 correspond à janvier). Plusieurs valeurs peuvent être indiquées en les séparant par des virgules.

## Seconde réelle (`fancymenu_visibility_requirement_is_realtime_second`)

**Objectif :** vérifie si la seconde réelle actuelle correspond à une valeur spécifique.

**Valeur :** requise — Seconde (0 à 59). Plusieurs valeurs peuvent être indiquées en les séparant par des virgules.

## Jour de la semaine réel (`fancymenu_visibility_requirement_is_realtime_week_day`)

**Objectif :** vérifie si le jour réel actuel de la semaine correspond à une valeur spécifique.

**Valeur :** requise — Jour de la semaine sous forme de nombre (1 à 7, où 1 correspond au dimanche). Plusieurs valeurs peuvent être indiquées en les séparant par des virgules.

## Année réelle (`fancymenu_visibility_requirement_is_realtime_year`)

**Objectif :** vérifie si l'année réelle actuelle correspond à une valeur spécifique.

**Valeur :** requise — Année complète (par exemple, "2023"). Plusieurs valeurs peuvent être indiquées en les séparant par des virgules.

## Fichier/dossier existant (`fancymenu_loading_requirement_file_exists`)

**Objectif :** vérifie si un fichier ou un dossier existe.

**Valeur :** requise — Chemin relatif au dossier de jeu actif, ou chemin commençant par `.minecraft/` pour le dossier Minecraft habituel. Les fichiers et les dossiers sont tous deux considérés comme existants.

## Système d'exploitation Linux (`fancymenu_loading_requirement_is_os_linux`)

**Objectif :** vérifie si la plateforme actuelle n'est ni Windows ni macOS. Cela correspond normalement aux environnements Linux.

**Valeur :** non requise

## Système d'exploitation macOS (`fancymenu_loading_requirement_is_os_macos`)

**Objectif :** vérifie si le système d'exploitation est macOS.

**Valeur :** non requise

## Système d'exploitation Windows (`fancymenu_loading_requirement_is_os_windows`)

**Objectif :** vérifie si le système d'exploitation est Windows.

**Valeur :** non requise

## Connexion Internet disponible (`is_internet_connection_available`)

**Objectif :** vérifie si une connexion Internet active est disponible.

**Valeur :** non requise

## Langue du jeu (`fancymenu_loading_requirement_is_language`)

**Objectif :** vérifie si la langue actuelle du jeu correspond à une valeur spécifique.

**Valeur :** requise — Code de langue (par exemple, `en_us` pour l'anglais)

## Mod chargé (`fancymenu_loading_requirement_is_mod_loaded`)

**Objectif :** vérifie si un mod spécifique est chargé.

**Valeur :** requise — ID du mod (par exemple, `fancymenu`, `jei`). Vous pouvez également vérifier la présence d'OptiFine avec `optifine`. Plusieurs ID de mods séparés par des virgules sont pris en charge ; tous les mods indiqués doivent être chargés.

## Rinku chargé (`is_rinku_loaded`)

**Objectif :** vérifie si [Rinku](https://modrinth.com/mod/rinku) est installé et initialisé. [Rinku](https://modrinth.com/mod/rinku) est requis pour l'[élément Navigateur](./elements#browser) et les [types de vidéos basés sur Rinku et obsolètes](./video#requirements) ; les [fonctionnalités vidéo natives](./video) utilisent Watermedia.

**Valeur :** non requise

## Nombre (`fancymenu_visibility_requirement_is_number`)

**Objectif :** permet une comparaison avancée de nombres avec différents modes de comparaison.

**Valeur :** requise — Format complexe : `["mode":"comparison_mode","number":"value1","compare_with":"value2"]$`, où `comparison_mode` peut être `equals`, `bigger-than`, `smaller-than`, `bigger-than-or-equals` ou `smaller-than-or-equals`

## Texte (`fancymenu_visibility_requirement_is_text`)

**Objectif :** permet une comparaison avancée de textes avec différents modes de comparaison.

**Valeur :** requise — Format complexe : `["mode":"comparison_mode","text":"text1","compare_with":"text2"]$`, où `comparison_mode` peut être `equals`, `contains`, `starts-with` ou `ends-with`

## Adresse IP du serveur (`fancymenu_visibility_requirement_is_server_ip`)

**Objectif :** vérifie si l'adresse IP du serveur actuel correspond à une valeur spécifique.

**Valeur :** requise — Adresse IP du serveur (avec ou sans port)

## Serveur en ligne (`fancymenu_loading_requirement_is_server_online`)

**Objectif :** vérifie si un serveur spécifique est en ligne et accessible.

**Valeur :** requise — Adresse IP du serveur (avec ou sans port)

## Pack de ressources activé (`is_resource_pack_enabled`)

**Objectif :** vérifie si un pack de ressources spécifique est actuellement sélectionné/actif.

**Valeur :** requise — Titre du pack de ressources ou ID du pack (par exemple, `Programmer Art` ou l'ID du pack)

## Valeur d'une variable (variable FM) (`fancymenu_visibility_requirement_is_variable_value`)

**Objectif :** vérifie si une variable FancyMenu possède une valeur spécifique.

**Valeur :** requise — Format : "nom_de_variable:valeur_attendue"

## Une seule fois par session (`once_per_session`)

**Objectif :** chaque instance configurée renvoie true une fois par session de jeu. Les différentes instances sont suivies indépendamment.

**Valeur :** non requise
