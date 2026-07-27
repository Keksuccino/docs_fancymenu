---
title: Conditions (Exigences)
description: Comment utiliser les exigences de chargement.
---

# Exigences

Les exigences (appelées **Loading Requirements** dans certains menus) affichent ou masquent du contenu en fonction de conditions telles que l’état de survol, la taille de la fenêtre ou le fait qu’un monde soit chargé.

Vous pouvez les utiliser sur des [éléments](./elements), des mises en page entières et des [scripts d’action](./action-scripts).

# Ajouter des exigences aux éléments

Pour ajouter des exigences à un élément, faites un clic droit dessus et sélectionnez **Loading Requirements**.

Les exigences sont vérifiées tant que le menu est ouvert, donc les éléments se mettent à jour lorsqu’une condition change.

# Exigences à l’échelle de la mise en page

Vous pouvez également modifier la visibilité de mises en page entières en faisant un clic droit sur l’**arrière-plan de l’éditeur**, puis en cliquant sur **Loading Requirements [Layout-Wide]**.

Lorsqu’un résultat à l’échelle de la mise en page change, FancyMenu reconstruit l’écran actuel et applique les mises en page dont les exigences sont désormais validées.

# Scripts d’action

Les exigences peuvent aussi être utilisées dans les scripts d’action.
Vous pouvez les ajouter dans l’écran de l’éditeur de scripts d’action et les utiliser pour exécuter des actions spécifiques uniquement si la condition de l’exigence est remplie.

# Combiner les exigences

- Les exigences en dehors des groupes utilisent **AND**, donc elles doivent toutes être validées.
- Dans un groupe, choisissez **AND** ou **OR**.
- Utilisez **IF NOT** pour inverser une exigence.

Ces règles sont les mêmes pour les éléments, les mises en page et les scripts d’action.

# Valeurs des exigences

Pour les exigences qui nécessitent une valeur, utilisez **Edit Requirement Value** et suivez la description affichée dans l’éditeur. Certains champs prennent en charge la complétion avec **TAB**.

Si une exigence importée ne fonctionne plus après une modification de FancyMenu ou des modules complémentaires, modifiez-la dans l’écran des exigences et consultez `logs/latest.log` pour les erreurs.

L’éditeur d’exigences prend en charge un menu contextuel au clic droit, la navigation au clavier, la recherche, annuler/rétablir (`Ctrl/Command + Z` / `Ctrl/Command + Y`) et `Ctrl/Command + S` pour enregistrer.

# Exigences en détail

Cette section répertorie les exigences intégrées de FancyMenu.

## Is Element Hovered (`fancymenu_visibility_requirement_is_element_hovered`)

**Objectif :** Vérifie si un élément spécifique est survolé par le curseur de la souris.

**Valeur :** Requise — [Identifiant de l’élément](./element-identifiers) cible (par exemple `some_element_ID`).

## Is Element Focused (`is_element_focused`)

**Objectif :** Vérifie si un élément spécifique a actuellement le focus clavier (par exemple, un champ de texte ou un bouton sélectionné).

**Valeur :** Requise — ID de l’élément cible (le même ID que celui affiché dans l’éditeur)

> [!NOTE]
> Le focus et le survol sont deux états différents. Un élément peut conserver son apparence de focus après que le pointeur l’a quitté ; un clic ou la navigation au clavier peut lui donner le focus.

## Is Any Element Hovered (`fancymenu_visibility_requirement_is_any_element_hovered`)

**Objectif :** Vérifie les éléments visibles/rendérisables dans la couche de personnalisation active actuelle, y compris les éléments fournis par des mises en page empilées.

**Valeur :** Non requise

## Is Any Button Hovered (`fancymenu_visibility_requirement_is_any_button_hovered`)

**Objectif :** Vérifie si un bouton vanilla ou personnalisé visible/rendérisable dans la couche de personnalisation active actuelle est survolé, y compris les boutons fournis par des mises en page empilées.

**Valeur :** Non requise

## Is Layout Enabled (`fancymenu_visibility_requirement_is_layout_enabled`)

**Objectif :** Vérifie si une mise en page spécifique est actuellement activée.

**Valeur :** Requise — Nom de la mise en page (par exemple `my_cool_main_menu_layout`)

## Is Scheduler Running (`fancymenu_visibility_requirement_is_scheduler_running`)

**Objectif :** Vérifie si un [scheduler](./schedulers) est actuellement en cours d’exécution.

**Valeur :** Requise — ID du scheduler (par exemple `my_scheduler`)

## Is GUI Scale (`fancymenu_loading_requirement_is_gui_scale`)

**Objectif :** Vérifie si l’échelle GUI actuelle correspond à certaines conditions.

**Valeur :** Requise — Utilisez un nombre pour l’égalité, `>` pour supérieur à, ou `<` pour inférieur à.

Plusieurs conditions séparées par des virgules sont combinées avec AND. Par exemple, `>1,<4` ne passe que lorsque l’échelle GUI est supérieure à `1` et inférieure à `4`.

## Is Button Active (`fancymenu_visibility_requirement_is_button_active`)

**Objectif :** Vérifie si un bouton spécifique est actif (cliquable).

**Valeur :** Requise — ID de l’élément du bouton cible (par exemple "some_element_ID")

## Is Screen Title (`is_menu_title`)

**Objectif :** Vérifie si le titre AFFICHÉ de l’écran correspond à un texte spécifique ou à une clé de localisation. Cela vérifie uniquement le nom/titre affiché de l’écran, comme "Options" ou "Pause". Cela ne vérifie PAS l’identifiant du menu/de l’écran (comme `title_screen`) !

**Valeur :** Requise — Le texte exact du titre ou la clé de localisation de l’écran

## Is Key Pressed (`is_key_pressed`)

**Objectif :** Vérifie si une touche du clavier spécifique est actuellement enfoncée.

**Valeur :** Requise — Le code de la touche cible. Sélectionné via une interface lors de la modification de la valeur de l’exigence.

## Is Any Screen Open (`is_any_screen_open`)

**Objectif :** Vérifie si un écran/menu est actuellement ouvert (retourne faux si aucun écran n’est affiché).

**Valeur :** Non requise

## Is MC Debug Overlay Enabled (`is_debug_overlay_enabled`)

**Objectif :** Vérifie si l’overlay de débogage F3 est actuellement visible.

**Valeur :** Non requise

## Is Active Cursor Type (`is_active_cursor_type`)

**Objectif :** Vérifie si le type de curseur actuellement actif de FancyMenu correspond à un type de curseur standard spécifique.

**Valeur :** Requise — Type de curseur : `normal`, `writing`, `crosshair`, `pointing_hand`, `resize_horizontal`, `resize_vertical`, `resize_nwse`, `resize_nesw`, `resize_all`, ou `not_allowed`

## Is Customization Menu Bar Visible (`is_customization_menu_bar_visible`)

**Objectif :** Vérifie si la barre de menu de personnalisation de FancyMenu est actuellement visible.

**Valeur :** Non requise

## Is Modpack Mode Enabled (`is_modpack_mode_enabled`)

**Objectif :** Vérifie si le Mode Modpack de FancyMenu est activé.

**Valeur :** Non requise

## Mouse Button Is Pressed (`mouse_click`)

**Objectif :** Renvoie vrai tant qu’un bouton de souris spécifique est maintenu enfoncé. Ce n’est pas un événement de clic unique ; utilisez le [**On Mouse Button Clicked** listener](./listeners#on-mouse-button-clicked-mouse_button_clicked) lorsqu’une action doit s’exécuter une fois par clic.

**Valeur :** Requise — `left` ou `right` pour indiquer quel bouton de souris vérifier

## Is Fullscreen (`fancymenu_loading_requirement_is_fullscreen`)

**Objectif :** Vérifie si le jeu est actuellement en mode plein écran.

**Valeur :** Non requise

## Is Window Width (`fancymenu_loading_requirement_is_window_width`)

**Objectif :** Vérifie si la largeur de la fenêtre du jeu correspond à des valeurs spécifiques.

**Valeur :** Requise — Largeur de fenêtre en pixels (par exemple "1920"). Plusieurs valeurs peuvent être fournies en les séparant par des virgules.

## Is Window Height (`fancymenu_loading_requirement_is_window_height`)

**Objectif :** Vérifie si la hauteur de la fenêtre du jeu correspond à des valeurs spécifiques.

**Valeur :** Requise — Hauteur de fenêtre en pixels (par exemple "1080"). Plusieurs valeurs peuvent être fournies en les séparant par des virgules.

## Is Window Width Bigger Than (`fancymenu_loading_requirement_is_window_width_bigger_than`)

**Objectif :** Vérifie si la largeur de la fenêtre du jeu est supérieure à une valeur spécifique.

**Valeur :** Requise — Largeur de fenêtre en pixels (par exemple "1920")

## Is Window Height Bigger Than (`fancymenu_loading_requirement_is_window_height_bigger_than`)

**Objectif :** Vérifie si la hauteur de la fenêtre du jeu est supérieure à une valeur spécifique.

**Valeur :** Requise — Hauteur de fenêtre en pixels (par exemple "1080")

## Is Multiplayer (`fancymenu_loading_requirement_is_multiplayer`)

**Objectif :** Vérifie si le joueur se trouve actuellement dans un monde multijoueur.

**Valeur :** Non requise

## Is Singleplayer (`fancymenu_loading_requirement_is_singpleplayer`)

**Objectif :** Vérifie si le joueur se trouve actuellement dans un monde solo.

**Valeur :** Non requise

## Is World Loaded (`fancymenu_loading_requirement_is_world_loaded`)

**Objectif :** Vérifie si un monde est actuellement chargé.

**Valeur :** Non requise

## Is Adventure (`fancymenu_visibility_requirement_is_adventure`)

**Objectif :** Vérifie si le joueur est actuellement en mode aventure.

**Valeur :** Non requise

## Is Creative (`fancymenu_visibility_requirement_is_creative`)

**Objectif :** Vérifie si le joueur est actuellement en mode créatif.

**Valeur :** Non requise

## Is Spectator (`fancymenu_visibility_requirement_is_spectator`)

**Objectif :** Vérifie si le joueur est actuellement en mode spectateur.

**Valeur :** Non requise

## Is Survival (`fancymenu_visibility_requirement_is_survival`)

**Objectif :** Vérifie si le joueur est actuellement en mode survie.

**Valeur :** Non requise

## Is Game Mode (`is_gamemode`)

**Objectif :** Vérifie si le joueur est dans un mode de jeu spécifique.

**Valeur :** Requise — Nom du mode de jeu (par exemple "creative", "survival", "adventure", "spectator")

## Is Difficulty (`is_difficulty`)

**Objectif :** Vérifie si la difficulté actuelle du jeu correspond à une valeur spécifique.

**Valeur :** Requise — Nom de la difficulté (par exemple "peaceful", "easy", "normal", "hard")

## Is Hardcore (`is_hardcore`)

**Objectif :** Vérifie si le monde actuellement chargé est en mode hardcore.

**Valeur :** Non requise

## Is Camera Perspective (`is_camera_perspective`)

**Objectif :** Vérifie si la perspective de caméra actuelle correspond à une perspective spécifique.

**Valeur :** Requise — `first_person`, `third_person_back`, ou `third_person_front`

## Is Raining (`is_raining`)

**Objectif :** Vérifie s’il pleut actuellement à l’emplacement du joueur.

**Valeur :** Non requise

## Is Thundering (`is_thundering`)

**Objectif :** Vérifie s’il y a actuellement un orage dans le monde du joueur.

**Valeur :** Non requise

## Is Clear Weather (`is_clear_weather`)

**Objectif :** Vérifie si le temps est actuellement dégagé (sans pluie ni orage).

**Valeur :** Non requise

## Is Snowing (`is_snowing`)

**Objectif :** Vérifie s’il neige actuellement à l’emplacement du joueur.

**Valeur :** Non requise

## Is Player Running (`is_player_running`)

**Objectif :** Vérifie si le joueur sprinte actuellement.

**Valeur :** Non requise

## Is Player Sneaking (`is_player_sneaking`)

**Objectif :** Vérifie si le joueur se déplace actuellement en étant accroupi.

**Valeur :** Non requise

## Is Player Using Item (`is_player_using_item`)

**Objectif :** Vérifie si le joueur utilise actuellement un objet.

**Valeur :** Non requise

## Is Player Swimming (`is_player_swimming`)

**Objectif :** Vérifie si le joueur nage actuellement.

**Valeur :** Non requise

## Is Player Jumping or Falling (`is_player_jumping`)

**Objectif :** Renvoie vrai tant que le joueur est dans les airs dans un état normal de saut ou de chute. La nage, les fluides, le vol à l’elytra, le sommeil, la nage visuelle et le fait de ramper sont exclus.

**Valeur :** Non requise

## Is Player Under Water (`is_player_under_water`)

**Objectif :** Vérifie si le joueur est complètement sous l’eau.

**Valeur :** Non requise

## Is Player In Water (`is_player_in_water`)

**Objectif :** Vérifie si le joueur est dans l’eau (peut être partiellement immergé).

**Valeur :** Non requise

## Is Player In Lava (`is_player_in_lava`)

**Objectif :** Vérifie si le joueur est dans la lave.

**Valeur :** Non requise

## Is Player In Fluid (`is_player_in_fluid`)

**Objectif :** Vérifie si le joueur est dans n’importe quel fluide (eau, lave, etc.).

**Valeur :** Non requise

## Is Player Riding Entity/Vehicle (`is_player_riding_entity`)

**Objectif :** Vérifie si le joueur monte une entité quelconque.

**Valeur :** Non requise

## Is Player Riding Jumpable Entity (`is_player_riding_jumpable_entity`)

**Objectif :** Vérifie si le joueur monte une entité capable de sauter (comme un cheval).

**Valeur :** Non requise

## Is Player Riding Entity With Health (`is_player_riding_entity_with_health`)

**Objectif :** Vérifie si le joueur monte une entité vivante avec des points de vie (comme des animaux, pas des bateaux).

**Valeur :** Non requise

## Is Player In Powder Snow (`is_player_in_powder_snow`)

**Objectif :** Vérifie si le joueur est actuellement dans de la neige poudreuse.

**Valeur :** Non requise

## Was Player In Powder Snow (`was_player_in_powder_snow`)

**Objectif :** Vérifie si le joueur était dans de la neige poudreuse (utilisé pour les effets qui persistent après en être sorti).

**Valeur :** Non requise

## Is Player Wearing Pumpkin (`is_player_wearing_pumpkin`)

**Objectif :** Vérifie si le joueur porte une citrouille sculptée sur la tête.

**Valeur :** Non requise

## Is Player Flying With Elytra (`is_player_flying_with_elytra`)

**Objectif :** Vérifie si le joueur vole actuellement avec une élytre.

**Valeur :** Non requise

## Is Player Creative Flying (`is_player_creative_flying`)

**Objectif :** Vérifie si le joueur vole en mode créatif.

**Valeur :** Non requise

## Has Player Absorption Hearts (`has_player_absorption_hearts`)

**Objectif :** Vérifie si le joueur possède des cœurs d’absorption (cœurs dorés).

**Valeur :** Non requise

## Is Player Withered (`is_player_withered`)

**Objectif :** Vérifie si le joueur est प्रभावित par l’effet Wither.

**Valeur :** Non requise

## Is Player Fully Frozen (`is_player_fully_frozen`)

**Objectif :** Vérifie si le joueur est complètement gelé (généralement à cause de la neige poudreuse).

**Valeur :** Non requise

## Is Player Poisoned (`is_player_poisoned`)

**Objectif :** Vérifie si le joueur est प्रभावित par l’effet poison.

**Valeur :** Non requise

## Is Player In Biome (`is_player_in_biome`)

**Objectif :** Vérifie si le joueur se trouve dans un biome spécifique.

**Valeur :** Requise — Identifiant du biome (par exemple `minecraft:birch_forest`)

## Is Player In Dimension (`is_player_in_dimension`)

**Objectif :** Vérifie si le joueur se trouve dans une dimension spécifique.

**Valeur :** Requise — Identifiant de la dimension (par exemple `minecraft:overworld`, `minecraft:the_nether`, `minecraft:the_end`)

## Is Player In Structure (`is_player_in_structure`)

**Objectif :** Vérifie si le joueur se trouve actuellement à l’intérieur d’une structure spécifique. Nécessite FancyMenu sur le serveur pour les mondes serveur.

**Valeur :** Requise — Identifiant de la structure (par exemple `minecraft:village`)

## Is Entity Nearby (`is_entity_nearby`)

**Objectif :** Vérifie si un type d’entité spécifique se trouve dans un certain rayon du joueur.

**Valeur :** Requise — Format : "rayon:entity_id" (par exemple `10:minecraft:pig` - vérifie la présence de cochons dans un rayon de 10 blocs)

## Is Effect Active (`is_effect_active`)

**Objectif :** Vérifie si un effet de potion spécifique est actif sur le joueur.

**Valeur :** Requise — Identifiant de l’effet (par exemple `minecraft:speed`, `minecraft:strength`)

## Is Any Effect Active (`is_any_effect_active`)

**Objectif :** Vérifie si le joueur a un effet de potion actif.

**Valeur :** Non requise

## Is Player Left-Handed (`is_left_handed`)

**Objectif :** Vérifie si le joueur est configuré en mode gaucher dans les options du jeu.

**Valeur :** Non requise

## Is Inventory Slot Filled (`is_inventory_slot_filled`)

**Objectif :** Vérifie si un emplacement d’inventaire spécifique contient un objet.

**Valeur :** Requise — Numéro de slot (0-35 pour l’inventaire principal, les slots 0-8 correspondent à la barre rapide)

## Is Item Hovered in Inventory (`is_item_hovered_in_inventory`)

**Objectif :** Vérifie si le curseur survole un objet quelconque dans un écran d’inventaire.

**Valeur :** Non requise

## Is Cursor Holding Inventory Item (`is_cursor_holding_inventory_item`)

**Objectif :** Vérifie si le curseur tient actuellement une pile d’objets d’inventaire.

**Valeur :** Non requise

## Is Hotbar Slot Selected (`is_hotbar_slot_active`)

**Objectif :** Vérifie si un emplacement spécifique de la barre rapide est actuellement sélectionné.

**Valeur :** Requise — Numéro de slot de la barre rapide (0-8)

## Has Player Permission Level (`fancymenu_loading_requirement_has_player_permission_level`)

**Objectif :** Vérifie si le joueur possède au moins le niveau d’autorisation/OP spécifié sur le monde ou serveur actuel.

**Valeur :** Requise — Niveau d’autorisation (0-4, où 4 correspond à l’opérateur du serveur)

## Is Attack Strength Weakened (`is_attack_strength_weakened`)

**Objectif :** Vérifie si la force d’attaque du joueur est actuellement affaiblie (pas complètement chargée).

**Valeur :** Non requise

## Is Real Time Day (`fancymenu_visibility_requirement_is_realtime_day`)

**Objectif :** Vérifie si le jour du mois réel actuel correspond à une valeur spécifique.

**Valeur :** Requise — Numéro du jour (1-31). Plusieurs valeurs peuvent être fournies en les séparant par des virgules.

## Is Real Time Hour (`fancymenu_visibility_requirement_is_realtime_hour`)

**Objectif :** Vérifie si l’heure réelle actuelle correspond à une valeur spécifique.

**Valeur :** Requise — Heure au format 24 heures (0-23). Plusieurs valeurs peuvent être fournies en les séparant par des virgules.

## Is Real Time Minute (`fancymenu_visibility_requirement_is_realtime_minute`)

**Objectif :** Vérifie si la minute réelle actuelle correspond à une valeur spécifique.

**Valeur :** Requise — Minute (0-59). Plusieurs valeurs peuvent être fournies en les séparant par des virgules.

## Is Real Time Month (`fancymenu_visibility_requirement_is_realtime_month`)

**Objectif :** Vérifie si le mois réel actuel correspond à une valeur spécifique.

**Valeur :** Requise — Numéro du mois (1-12, où 1 est janvier). Plusieurs valeurs peuvent être fournies en les séparant par des virgules.

## Is Real Time Second (`fancymenu_visibility_requirement_is_realtime_second`)

**Objectif :** Vérifie si la seconde réelle actuelle correspond à une valeur spécifique.

**Valeur :** Requise — Seconde (0-59). Plusieurs valeurs peuvent être fournies en les séparant par des virgules.

## Is Real Time Week Day (`fancymenu_visibility_requirement_is_realtime_week_day`)

**Objectif :** Vérifie si le jour de la semaine réel actuel correspond à une valeur spécifique.

**Valeur :** Requise — Jour de la semaine sous forme de nombre (1-7, où 1 est dimanche). Plusieurs valeurs peuvent être fournies en les séparant par des virgules.

## Is Real Time Year (`fancymenu_visibility_requirement_is_realtime_year`)

**Objectif :** Vérifie si l’année réelle actuelle correspond à une valeur spécifique.

**Valeur :** Requise — Année complète (par exemple "2023"). Plusieurs valeurs peuvent être fournies en les séparant par des virgules.

## File/Folder Exists (`fancymenu_loading_requirement_file_exists`)

**Objectif :** Vérifie si un fichier ou un dossier existe.

**Valeur :** Requise — Un chemin relatif au répertoire de jeu actif, ou un chemin commençant par `.minecraft/` pour le répertoire Minecraft conventionnel. Les fichiers et les dossiers sont tous deux considérés comme existants.

## Is OS Linux (`fancymenu_loading_requirement_is_os_linux`)

**Objectif :** Vérifie si la plateforme actuelle n’est ni Windows ni macOS. Cela correspond normalement aux environnements Linux.

**Valeur :** Non requise

## Is OS macOS (`fancymenu_loading_requirement_is_os_macos`)

**Objectif :** Vérifie si le système d’exploitation est macOS.

**Valeur :** Non requise

## Is OS Windows (`fancymenu_loading_requirement_is_os_windows`)

**Objectif :** Vérifie si le système d’exploitation est Windows.

**Valeur :** Non requise

## Is Internet Connection Available (`is_internet_connection_available`)

**Objectif :** Vérifie si une connexion Internet active est disponible.

**Valeur :** Non requise

## Is Game Language (`fancymenu_loading_requirement_is_language`)

**Objectif :** Vérifie si la langue actuelle du jeu correspond à une valeur spécifique.

**Valeur :** Requise — Code de langue (par exemple `en_us` pour l’anglais)

## Is Mod Loaded (`fancymenu_loading_requirement_is_mod_loaded`)

**Objectif :** Vérifie si un mod spécifique est chargé.

**Valeur :** Requise — ID du mod (par exemple `fancymenu`, `jei`). Vous pouvez également vérifier OptiFine avec `optifine`. Plusieurs IDs de mods séparés par des virgules sont pris en charge ; tous les mods listés doivent être chargés.

## Is MCEF Loaded (`is_mcef_loaded`)

**Objectif :** Vérifie si MCEF (Minecraft Chromium Embedded Framework) est installé et initialisé. MCEF est requis pour l’[élément Browser](./elements#browser) et les [types de vidéo basés sur MCEF obsolètes](./video#requirements) ; les [fonctionnalités vidéo natives](./video) utilisent Watermedia.

**Valeur :** Non requise

## Is Number (`fancymenu_visibility_requirement_is_number`)

**Objectif :** Fournit une comparaison numérique avancée avec différents modes de comparaison.

**Valeur :** Requise — Format complexe : `["mode":"comparison_mode","number":"value1","compare_with":"value2"]$` où `comparison_mode` peut être `equals`, `bigger-than`, `smaller-than`, `bigger-than-or-equals`, ou `smaller-than-or-equals`

## Is Text (`fancymenu_visibility_requirement_is_text`)

**Objectif :** Fournit une comparaison textuelle avancée avec différents modes de comparaison.

**Valeur :** Requise — Format complexe : `["mode":"comparison_mode","text":"text1","compare_with":"text2"]$` où `comparison_mode` peut être `equals`, `contains`, `starts-with`, ou `ends-with`

## Is Server IP (`fancymenu_visibility_requirement_is_server_ip`)

**Objectif :** Vérifie si l’adresse IP du serveur actuel correspond à une valeur spécifique.

**Valeur :** Requise — Adresse IP du serveur (avec ou sans port)

## Is Server Online (`fancymenu_loading_requirement_is_server_online`)

**Objectif :** Vérifie si un serveur spécifique est en ligne et joignable.

**Valeur :** Requise — Adresse IP du serveur (avec ou sans port)

## Is Resource Pack Enabled (`is_resource_pack_enabled`)

**Objectif :** Vérifie si un pack de ressources spécifique est actuellement sélectionné/actif.

**Valeur :** Requise — Titre du pack de ressources ou ID du pack (par exemple `Programmer Art` ou l’ID du pack)

## Is Variable Value (FM Variable) (`fancymenu_visibility_requirement_is_variable_value`)

**Objectif :** Vérifie si une variable FancyMenu a une valeur spécifique.

**Valeur :** Requise — Format : "nom_variable:valeur_attendue"

## Only Once Per Session (`once_per_session`)

**Objectif :** Chaque instance configurée renvoie vrai une fois par session de jeu. Les différentes instances sont suivies indépendamment.

**Valeur :** Non requise
