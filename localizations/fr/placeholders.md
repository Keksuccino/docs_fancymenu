---
title: Espaces réservés
description: Comment utiliser les espaces réservés.
---

# Espaces réservés

Les espaces réservés sont des valeurs dynamiques qui sont remplacées par du contenu réel lorsqu’elles sont utilisées. Dans FancyMenu, les espaces réservés vous permettent d’insérer du contenu dynamique dans différents éléments comme du texte, des boutons et des conditions de chargement. Voyez-les comme des variables qui sont évaluées puis remplacées par leurs valeurs réelles lorsque vos interfaces sont affichées.

# Informations générales

## Syntaxe de base
Les espaces réservés dans FancyMenu utilisent une syntaxe de type JSON :
```
{"placeholder":"modversion","values":{"modid":"fancymenu"}}
```

Par exemple, pour afficher le nom du joueur :
```
{"placeholder":"playername"}
```

## Imbrication des espaces réservés
L’une des fonctionnalités les plus puissantes du système d’espaces réservés de FancyMenu est la possibilité d’imbriquer des espaces réservés dans d’autres espaces réservés. Cela signifie que vous pouvez utiliser la sortie d’un espace réservé comme entrée pour un autre.

Exemple d’espaces réservés imbriqués :
```
{"placeholder":"calc","values":{"decimal":"true","expression":"{"placeholder":"maxram"} / 1024"}}
```
Cet exemple prend la valeur de la RAM maximale et la divise par 1024 pour la convertir de Mo en Go.

# Utilisation des espaces réservés

La plupart des éléments disposant de champs de texte prennent en charge les espaces réservés. Vous pouvez voir si un champ de texte les prend en charge lors de son édition. Si l’**éditeur de texte** plein écran s’ouvre lorsque vous modifiez le texte, cela signifie qu’il prend en charge les espaces réservés. 

Pour trouver une **liste de tous les espaces réservés**, cliquez simplement sur le bouton **Espaces réservés** dans le **coin supérieur droit** de l’**éditeur de texte**.

Une **barre de recherche** se trouve en haut de la liste des espaces réservés et vous permet d’en rechercher.

Cliquer sur un espace réservé dans la liste le collera dans le contenu du texte.

# Détails des espaces réservés

Cette liste contient la plupart, sinon la totalité, des espaces réservés disponibles dans FancyMenu. La liste peut parfois être légèrement obsolète en raison des mises à jour du mod.

## Nom du joueur (playername)
Renvoie le nom d’utilisateur du joueur actuel.
```
{"placeholder":"playername"}
```
Exemple de sortie : `Steve`

## UUID du joueur (playeruuid)
Renvoie l’identifiant unique du joueur.
```
{"placeholder":"playeruuid"}
```
Exemple de sortie : `c8cde7fe-7ced-11eb-9439-0242ac130002`

## Version de Minecraft (mcversion)
Renvoie la version actuelle de Minecraft.
```
{"placeholder":"mcversion"}
```
Exemple de sortie : `1.19.2`

## Version du chargeur de mods (loaderver)
Renvoie la version du chargeur de mods (Forge/Fabric).
```
{"placeholder":"loaderver"}
```
Exemple de sortie : `43.2.0`

## Nom du chargeur de mods (loadername)
Renvoie le nom du chargeur de mods.
```
{"placeholder":"loadername"}
```
Exemple de sortie : `Forge`

## Version du mod (modversion)
Renvoie la version d’un mod spécifique.
```
{"placeholder":"modversion","values":{"modid":"fancymenu"}}
```
Exemple de sortie : `2.14.9`

## Nombre total de mods (totalmods)
Renvoie le nombre total de mods installés.
```
{"placeholder":"totalmods"}
```
Exemple de sortie : `45`

## Nombre de mods actifs (loadedmods)
Renvoie le nombre de mods actuellement chargés.
```
{"placeholder":"loadedmods"}
```
Exemple de sortie : `43`

## Progression de chargement du monde (world_load_progress)
Renvoie la progression actuelle du chargement du monde en pourcentage.
```
{"placeholder":"world_load_progress"}
```
Exemple de sortie : `75`

## Valeur d’une option Minecraft (minecraft_option_value)
Renvoie la valeur d’une option de Minecraft.
```
{"placeholder":"minecraft_option_value","values":{"name":"fov"}}
```
Exemple de sortie : `70`

## Dernier monde ou serveur (last_world_server)
Renvoie des informations sur le dernier monde ou serveur consulté.
```
{"placeholder":"last_world_server","values":{"type":"both","full_world_path":"true"}}
```
Paramètres :
- `type` : Détermine le type d’information à renvoyer
  - `"both"` : Renvoie le dernier monde ou serveur consulté (par défaut)
  - `"server"` : Renvoie uniquement si le dernier élément consulté était un serveur
  - `"world"` : Renvoie uniquement si le dernier élément consulté était un monde
- `full_world_path` : Contrôle l’affichage des chemins de mondes
  - `"true"` : Renvoie le chemin complet du monde (par défaut)
  - `"false"` : Renvoie uniquement le nom du monde sans le chemin (n’affecte pas les serveurs)

Exemples :
- Serveur : `mc.hypixel.net`
- Monde avec chemin complet : `saves/New World`
- Monde sans chemin complet : `New World`

## Largeur de l’écran (guiwidth)
Renvoie la largeur actuelle de l’écran.
```
{"placeholder":"guiwidth"}
```
Exemple de sortie : `1920`

## Hauteur de l’écran (guiheight)
Renvoie la hauteur actuelle de l’écran.
```
{"placeholder":"guiheight"}
```
Exemple de sortie : `1080`

## Identifiant de l’écran actuel (screenid)
Renvoie l’identifiant de l’écran actuel.
```
{"placeholder":"screenid"}
```
Exemple de sortie : `title_screen`

## Largeur d’un élément (elementwidth)
Renvoie la largeur d’un élément spécifique.
```
{"placeholder":"elementwidth","values":{"id":"my_button"}}
```
Exemple de sortie : `200`

## Hauteur d’un élément (elementheight)
Renvoie la hauteur d’un élément spécifique.
```
{"placeholder":"elementheight","values":{"id":"my_button"}}
```
Exemple de sortie : `20`

## Position X d’un élément (elementposx)
Renvoie la position X d’un élément spécifique.
```
{"placeholder":"elementposx","values":{"id":"my_button"}}
```
Exemple de sortie : `150`

## Position Y d’un élément (elementposy)
Renvoie la position Y d’un élément spécifique.
```
{"placeholder":"elementposy","values":{"id":"my_button"}}
```
Exemple de sortie : `100`

## Position X de la souris (mouseposx)
Renvoie la position X actuelle de la souris.
```
{"placeholder":"mouseposx"}
```
Exemple de sortie : `960`

## Position Y de la souris (mouseposy)
Renvoie la position Y actuelle de la souris.
```
{"placeholder":"mouseposy"}
```
Exemple de sortie : `540`

## Clics par seconde (clicks_per_second)
Renvoie le nombre actuel de clics par seconde pour un bouton de souris.
```
{"placeholder":"clicks_per_second","values":{"mouse_button":"left"}}
```
Paramètres :
- `mouse_button` : `left` ou `right`

Exemple de sortie : `8`

## Échelle de l’interface (guiscale)
Renvoie l’échelle actuelle de l’interface.
```
{"placeholder":"guiscale"}
```
Exemple de sortie : `2`

## Libellé/texte d’un widget vanilla (vanillabuttonlabel)
Renvoie le libellé/texte d’un widget/bouton vanilla.
```
{"placeholder":"vanillabuttonlabel","values":{"locator":"some.menu.identifier:505280"}}
```
Exemple de sortie : `Options...`

## Valeur d’un champ de saisie de texte (text_input_field_value)
Renvoie la valeur actuelle d’un champ de saisie de texte personnalisé ou vanilla à partir de son identifiant d’élément.
```
{"placeholder":"text_input_field_value","values":{"element_identifier":"my_input"}}
```
Exemple de sortie : `Hello World`

## Santé actuelle du joueur (current_player_health)
Renvoie les points de vie actuels du joueur.
```
{"placeholder":"current_player_health"}
```
Exemple de sortie : `20.0`

## Santé maximale du joueur (max_player_health)
Renvoie les points de vie maximum du joueur.
```
{"placeholder":"max_player_health"}
```
Exemple de sortie : `20.0`

## Santé actuelle du joueur (pourcentage) (current_player_health_percent)
Renvoie la santé du joueur en pourcentage.
```
{"placeholder":"current_player_health_percent"}
```
Exemple de sortie : `100`

## Santé d’absorption actuelle du joueur (current_player_absorption_health)
Renvoie les points de vie d’absorption du joueur (cœurs dorés).
```
{"placeholder":"current_player_absorption_health"}
```
Exemple de sortie : `4.0`

## Santé d’absorption maximale du joueur (max_player_absorption_health)
Renvoie la santé d’absorption maximale.
```
{"placeholder":"max_player_absorption_health"}
```
Exemple de sortie : `4.0`

## Santé d’absorption actuelle du joueur (pourcentage) (current_player_absorption_health_percent)
Renvoie la santé d’absorption du joueur en pourcentage.
```
{"placeholder":"current_player_absorption_health_percent"}
```
Exemple de sortie : `100`

## Niveau de faim actuel du joueur (current_player_hunger)
Renvoie le niveau de faim actuel du joueur.
```
{"placeholder":"current_player_hunger"}
```
Exemple de sortie : `20`

## Niveau de faim maximum du joueur (max_player_hunger)
Renvoie le niveau de faim maximum.
```
{"placeholder":"max_player_hunger"}
```
Exemple de sortie : `20`

## Niveau de faim actuel du joueur (pourcentage) (current_player_hunger_percent)
Renvoie la faim du joueur en pourcentage.
```
{"placeholder":"current_player_hunger_percent"}
```
Exemple de sortie : `100`

## Saturation de faim actuelle du joueur (current_player_hunger_saturation)
Renvoie la valeur actuelle de saturation de faim du joueur.
```
{"placeholder":"current_player_hunger_saturation"}
```
Exemple de sortie : `5.0`

## Armure actuelle du joueur (current_player_armor)
Renvoie la valeur actuelle de l’armure du joueur.
```
{"placeholder":"current_player_armor"}
```
Exemple de sortie : `20`

## Robustesse de l’armure du joueur (player_armor_toughness)
Renvoie la valeur totale de robustesse de l’armure du joueur.
```
{"placeholder":"player_armor_toughness"}
```
Exemple de sortie : `8.0`

## Armure maximale du joueur (max_player_armor)
Renvoie la valeur maximale de l’armure.
```
{"placeholder":"max_player_armor"}
```
Exemple de sortie : `20`

## Armure actuelle du joueur (pourcentage) (current_player_armor_percent)
Renvoie l’armure du joueur en pourcentage.
```
{"placeholder":"current_player_armor_percent"}
```
Exemple de sortie : `100`

## Niveau d’oxygène actuel du joueur (current_player_oxygen)
Renvoie le niveau d’oxygène actuel du joueur (bulles d’air).
```
{"placeholder":"current_player_oxygen"}
```
Exemple de sortie : `300`

## Niveau d’oxygène maximal du joueur (max_player_oxygen)
Renvoie le niveau d’oxygène maximum.
```
{"placeholder":"max_player_oxygen"}
```
Exemple de sortie : `300`

## Niveau d’oxygène actuel du joueur (pourcentage) (current_player_oxygen_percent)
Renvoie le niveau d’oxygène du joueur en pourcentage.
```
{"placeholder":"current_player_oxygen_percent"}
```
Exemple de sortie : `100`

## Niveau actuel du joueur (current_player_level)
Renvoie le niveau d’expérience actuel du joueur.
```
{"placeholder":"current_player_level"}
```
Exemple de sortie : `30`

## Expérience actuelle du joueur (current_player_exp)
Renvoie le total de points d’expérience du joueur.
```
{"placeholder":"current_player_exp"}
```
Exemple de sortie : `1250`

## Progression d’expérience du joueur (pourcentage) (current_player_exp_progress)
Renvoie la progression d’expérience du joueur vers le prochain niveau en pourcentage.
```
{"placeholder":"current_player_exp_progress"}
```
Exemple de sortie : `75`

## Puissance d’attaque du joueur (pourcentage) (player_attack_strength)
Renvoie le temps de recharge d’attaque du joueur en pourcentage.
```
{"placeholder":"player_attack_strength"}
```
Exemple de sortie : `100`

## Mode de jeu du joueur (player_gamemode)
Renvoie le mode de jeu actuel du joueur.
```
{"placeholder":"player_gamemode"}
```
Exemple de sortie : `survival`

## Direction de vue du joueur (player_view_direction)
Renvoie la direction vers laquelle le joueur fait face.
```
{"placeholder":"player_view_direction"}
```
Exemple de sortie : `north`

## Coordonnée X du joueur (player_x_coordinate)
Renvoie la position X du joueur dans le monde.
```
{"placeholder":"player_x_coordinate"}
```
Exemple de sortie : `125`

## Coordonnée Y du joueur (player_y_coordinate)
Renvoie la position Y du joueur dans le monde.
```
{"placeholder":"player_y_coordinate"}
```
Exemple de sortie : `64`

## Coordonnée Z du joueur (player_z_coordinate)
Renvoie la position Z du joueur dans le monde.
```
{"placeholder":"player_z_coordinate"}
```
Exemple de sortie : `-250`

## Santé actuelle de la monture (current_mount_health)
Renvoie la santé actuelle de l’entité que le joueur monte.
```
{"placeholder":"current_mount_health"}
```
Exemple de sortie : `30.0`

## Santé maximale de la monture (max_mount_health)
Renvoie la santé maximale de l’entité que le joueur monte.
```
{"placeholder":"max_mount_health"}
```
Exemple de sortie : `30.0`

## Santé actuelle de la monture (pourcentage) (current_mount_health_percent)
Renvoie la santé de la monture en pourcentage.
```
{"placeholder":"current_mount_health_percent"}
```
Exemple de sortie : `100`

## Jauge de saut de la monture actuelle (pourcentage) (current_mount_jump_meter)
Renvoie la valeur de la jauge de puissance de saut de la monture.
```
{"placeholder":"current_mount_jump_meter"}
```
Exemple de sortie : `75`

## Santé actuelle du boss (pourcentage) (current_boss_health)
Renvoie la santé du boss actif.
```
{"placeholder":"current_boss_health"}
```
Exemple de sortie : `150.0`

## Nom du boss (boss_name)
Renvoie le nom du boss actif.
```
{"placeholder":"boss_name","values":{"boss_index":"0","as_json":"false"}}
```
Exemple de sortie : `Ender Dragon`

## Nombre de boss (boss_count)
Renvoie le nombre de boss actifs.
```
{"placeholder":"boss_count"}
```
Exemple de sortie : `1`

## Nombre d’effets actifs (effects_count)
Renvoie le nombre d’effets de potion actifs.
```
{"placeholder":"effects_count"}
```
Exemple de sortie : `3`

## Effet actif (active_effect)
Renvoie des informations sur un effet actif spécifique.
```
{"placeholder":"active_effect","values":{"effect_index":"0"}}
```
Exemple de sortie : `minecraft:speed`

## Emplacement sélectionné de la barre rapide (active_hotbar_slot)
Renvoie l’emplacement actuellement sélectionné de la barre rapide (0-8).
```
{"placeholder":"active_hotbar_slot"}
```
Exemple de sortie : `4`

## Objet d’un emplacement (slot_item)
Renvoie des informations sur un objet dans un emplacement d’inventaire spécifique.
```
{"placeholder":"slot_item","values":{"slot":"0"}}
```
Exemple de sortie : `minecraft:diamond_sword`

## Quantité d’objet dans un emplacement (slot_item_count)
Renvoie la taille de la pile d’objets dans un emplacement d’inventaire du joueur spécifique.
```
{"placeholder":"slot_item_count","values":{"slot":"0"}}
```
Exemple de sortie : `64`

## Durabilité d’un objet dans un emplacement (slot_item_durability)
Renvoie les informations de durabilité de l’objet dans un emplacement d’inventaire du joueur spécifique.
```
{"placeholder":"slot_item_durability","values":{"slot":"0","format":"percentage"}}
```
Paramètres :
- `slot` : Numéro de l’emplacement de l’inventaire du joueur.
- `format` : `current`, `remaining`, `max`, `damage`, `percentage` ou `percent`.

Exemple de sortie : `87`

## Nom d’affichage d’un objet dans un emplacement (slot_item_display_name_fm)
Renvoie le nom d’affichage de l’objet dans un emplacement spécifique sous forme de composant texte JSON. En mode spectateur, les emplacements de la barre rapide peuvent résoudre les noms d’objets du menu spectateur sauf si `ignore_spectator` vaut `true`.
```
{"placeholder":"slot_item_display_name_fm","values":{"slot":"0","ignore_spectator":"false"}}
```
Exemple de sortie : `{"text":"Diamond Sword","color":"aqua"}`

## Nombre d’objets dans l’inventaire (inventory_item_count)
Renvoie le nombre total d’un type d’objet dans l’inventaire du joueur. Si `item` est vide, compte toutes les piles d’objets de l’inventaire.
```
{"placeholder":"inventory_item_count","values":{"item":"minecraft:diamond"}}
```
Exemple de sortie : `12`

## Quantité de nourriture restaurée par un objet dans un emplacement d’inventaire (inventory_slot_food_point_restore_amount)
Renvoie les points de faim restaurés par l’objet alimentaire dans l’emplacement d’inventaire du joueur donné.
```
{"placeholder":"inventory_slot_food_point_restore_amount","values":{"slot":"0"}}
```
Exemple de sortie : `4.0`

## Objet d’inventaire survolé (hovered_inventory_item)
Renvoie la clé de l’objet actuellement survolé dans un écran d’inventaire.
```
{"placeholder":"hovered_inventory_item"}
```
Exemple de sortie : `minecraft:apple`

## Temps de jeu du monde (game_time)
Renvoie le compteur actuel des ticks du temps en jeu.
```
{"placeholder":"game_time"}
```
Exemple de sortie : `18000`

## Heure du jour du monde (world_daytime)
Renvoie l’heure actuelle du jour dans le monde.
```
{"placeholder":"world_daytime"}
```
Exemple de sortie : `13000`

## Heure du jour du monde (world_daytime_hour)
Renvoie la composante heure du temps du monde. Par défaut, le format 24 heures est utilisé ; définissez `twelve_hour_format` sur `"true"` pour un format 12 heures.
```
{"placeholder":"world_daytime_hour","values":{"twelve_hour_format":"false"}}
```
Exemple de sortie : `12`

## Minute du jour du monde (world_daytime_minute)
Renvoie la composante minute du temps du monde (00-59).
```
{"placeholder":"world_daytime_minute"}
```
Exemple de sortie : `30`

## Difficulté du monde (world_difficulty)
Renvoie la difficulté actuelle du monde.
```
{"placeholder":"world_difficulty"}
```
Exemple de sortie : `normal`

## Seed du monde actuel (current_world_seed)
Renvoie la seed du monde solo actuel. Renvoie une valeur vide lorsque la seed n’est pas disponible.
```
{"placeholder":"current_world_seed"}
```
Exemple de sortie : `123456789`

## Biome actuel (current_biome)
Renvoie le biome dans lequel se trouve actuellement le joueur. Définissez `as_key` sur `"false"` pour renvoyer un nom traduit/affiché lorsqu’il est disponible.
```
{"placeholder":"current_biome","values":{"as_key":"true"}}
```
Exemple de sortie : `minecraft:plains`

## Dimension actuelle (current_dimension)
Renvoie la dimension dans laquelle se trouve actuellement le joueur. Définissez `as_key` sur `"false"` pour renvoyer un nom traduit/affiché lorsqu’il est disponible.
```
{"placeholder":"current_dimension","values":{"as_key":"true"}}
```
Exemple de sortie : `minecraft:overworld`

## Valeur d’une règle de jeu (gamerule_value)
Renvoie la valeur actuelle d’une règle de jeu dans le monde/serveur chargé. Les mondes serveur nécessitent FancyMenu sur le serveur.
```
{"placeholder":"gamerule_value","values":{"name":"doDaylightCycle"}}
```
Exemple de sortie : `true`

## Catégorie d’objet (item_category)
Renvoie l’onglet créatif d’un objet. Définissez `as_key` sur `"true"` pour renvoyer la clé de la catégorie au lieu du nom affiché.
```
{"placeholder":"item_category","values":{"item":"minecraft:diamond_sword","as_key":"false"}}
```
Exemple de sortie : `Combat`

## Titre/Sous-titre HUD actuel (current_title)
Renvoie le texte du titre actuellement affiché.
```
{"placeholder":"current_title","values":{"is_subtitle":"false","as_json":"false"}}
```
Exemple de sortie : `Game Over!`

## Message de la barre d’action (action_bar_message_fm)
Renvoie le message vanilla actuel de la barre d’action au-dessus de la barre rapide.
```
{"placeholder":"action_bar_message_fm"}
```
Exemple de sortie : `You may not rest now`

## Durée du message de la barre d’action (action_bar_message_time_fm)
Renvoie le nombre de ticks pendant lesquels le message actuel de la barre d’action vanilla sera encore affiché.
```
{"placeholder":"action_bar_message_time_fm"}
```
Exemple de sortie : `42`

## Rotation X de la caméra (camera_rotation_x_fm)
Renvoie l’inclinaison actuelle de la caméra en degrés.
```
{"placeholder":"camera_rotation_x_fm"}
```
Exemple de sortie : `12.5`

## Rotation Y de la caméra (camera_rotation_y_fm)
Renvoie l’orientation horizontale actuelle de la caméra en degrés.
```
{"placeholder":"camera_rotation_y_fm"}
```
Exemple de sortie : `-90.0`

## Delta de rotation X de la caméra (camera_rotation_delta_x_fm)
Renvoie la variation par tick de l’inclinaison de la caméra.
```
{"placeholder":"camera_rotation_delta_x_fm"}
```
Exemple de sortie : `0.4`

## Delta de rotation Y de la caméra (camera_rotation_delta_y_fm)
Renvoie la variation par tick de l’orientation horizontale de la caméra.
```
{"placeholder":"camera_rotation_delta_y_fm"}
```
Exemple de sortie : `-1.2`

## Durée du texte d’objet surligné (highlighted_item_time_fm)
Renvoie le nombre de ticks pendant lesquels le nom de l’objet surligné sera encore affiché au-dessus de la barre rapide.
```
{"placeholder":"highlighted_item_time_fm"}
```
Exemple de sortie : `30`

## Progression d’utilisation d’un objet par le joueur (player_item_use_progress_fm)
Renvoie la progression actuelle d’utilisation de l’objet de `0.0` à `1.0`.
```
{"placeholder":"player_item_use_progress_fm"}
```
Exemple de sortie : `0.65`

## Delta de position X du joueur (player_position_delta_x_fm)
Renvoie la variation par tick de la position du joueur sur l’axe X.
```
{"placeholder":"player_position_delta_x_fm"}
```
Exemple de sortie : `0.0`

## Delta de position Y du joueur (player_position_delta_y_fm)
Renvoie la variation par tick de la position du joueur sur l’axe Y.
```
{"placeholder":"player_position_delta_y_fm"}
```
Exemple de sortie : `-0.08`

## Delta de position Z du joueur (player_position_delta_z_fm)
Renvoie la variation par tick de la position du joueur sur l’axe Z.
```
{"placeholder":"player_position_delta_z_fm"}
```
Exemple de sortie : `0.12`

## IP du serveur actuel (current_server_ip)
Renvoie l’adresse IP du serveur connecté.
```
{"placeholder":"current_server_ip"}
```
Exemple de sortie : `mc.hypixel.net`

## Liste des joueurs du monde (world_players_list)
Renvoie la liste de tous les joueurs actuellement dans le monde.
```
{"placeholder":"world_players_list","values":{"separator":", "}}
```
Exemple de sortie : `Steve, Alex, Notch`

## MOTD du serveur (servermotd)
Renvoie le message du jour d’un serveur.
```
{"placeholder":"servermotd","values":{"ip":"mc.hypixel.net","line":"1"}}
```
Exemple de sortie : `Welcome to Hypixel!`

## PING du serveur (serverping)
Renvoie la latence vers un serveur en millisecondes.
```
{"placeholder":"serverping","values":{"ip":"mc.hypixel.net"}}
```
Exemple de sortie : `54`

## Nombre de joueurs sur le serveur (serverplayercount)
Renvoie le nombre de joueurs sur un serveur.
```
{"placeholder":"serverplayercount","values":{"ip":"mc.hypixel.net"}}
```
Exemple de sortie : `25000/30000`

## État du serveur (serverstatus)
Renvoie l’état en ligne/hors ligne d’un serveur.
```
{"placeholder":"serverstatus","values":{"ip":"mc.hypixel.net"}}
```
Exemple de sortie : `§aOnline` ou `§cOffline`

## Version du serveur (serverversion)
Renvoie la version Minecraft d’un serveur.
```
{"placeholder":"serverversion","values":{"ip":"mc.hypixel.net"}}
```
Exemple de sortie : `1.19.2`

## Année (realtimeyear)
Renvoie l’année actuelle.
```
{"placeholder":"realtimeyear"}
```
Exemple de sortie : `2024`

## Mois (realtimemonth)
Renvoie le mois actuel (01-12).
```
{"placeholder":"realtimemonth"}
```
Exemple de sortie : `01`

## Jour (realtimeday)
Renvoie le jour actuel du mois (01-31).
```
{"placeholder":"realtimeday"}
```
Exemple de sortie : `27`

## Heure (realtimehour)
Renvoie l’heure actuelle. Par défaut, le format 24 heures est utilisé ; définissez `twelve_hour_format` sur `"true"` pour un format 12 heures.
```
{"placeholder":"realtimehour","values":{"twelve_hour_format":"false","timezone":"system"}}
```
Exemple de sortie : `14`

## Minute (realtimeminute)
Renvoie la minute actuelle (00-59).
```
{"placeholder":"realtimeminute"}
```
Exemple de sortie : `30`

## Seconde (realtimesecond)
Renvoie la seconde actuelle (00-59).
```
{"placeholder":"realtimesecond"}
```
Exemple de sortie : `45`

## Heure actuelle en millisecondes (horodatage Unix) (unix_time)
Renvoie l’horodatage Unix actuel en millisecondes.
```
{"placeholder":"unix_time"}
```
Exemple de sortie : `1716552478123`

> Les espaces réservés de temps réel (`realtimeyear`, `realtimemonth`, `realtimeday`, `realtimehour`, `realtimeminute`, `realtimesecond` et `unix_time`) prennent en charge une valeur `timezone`. Utilisez des identifiants de fuseaux horaires Java classiques comme `UTC`, `Europe/Berlin` ou `America/New_York` ; omettez-la ou utilisez `system` pour le fuseau horaire système.
{.is-info}

## Informations CPU (cpuinfo)
Renvoie des informations sur le processeur.
```
{"placeholder":"cpuinfo"}
```
Exemple de sortie : `Intel(R) Core(TM) i7-10700K CPU @ 3.80GHz`

## Utilisation CPU (JVM) (jvmcpu)
Renvoie l’utilisation CPU de la JVM en pourcentage.
```
{"placeholder":"jvmcpu"}
```
Exemple de sortie : `25.5`

## Utilisation CPU (OS) (oscpu)
Renvoie l’utilisation CPU du système d’exploitation en pourcentage.
```
{"placeholder":"oscpu"}
```
Exemple de sortie : `42.8`

## Informations GPU (gpuinfo)
Renvoie des informations sur le GPU.
```
{"placeholder":"gpuinfo"}
```
Exemple de sortie : `NVIDIA GeForce RTX 3080`

## Version de Java (javaver)
Renvoie la version de Java.
```
{"placeholder":"javaver"}
```
Exemple de sortie : `17.0.2`

## Machine virtuelle Java (jvmname)
Renvoie le nom de la machine virtuelle Java.
```
{"placeholder":"jvmname"}
```
Exemple de sortie : `OpenJDK 64-Bit Server VM`

## Version OpenGL (glver)
Renvoie la version OpenGL.
```
{"placeholder":"glver"}
```
Exemple de sortie : `4.6.0 NVIDIA 516.94`

## Nom du système d’exploitation (osname)
Renvoie le nom du système d’exploitation.
```
{"placeholder":"osname"}
```
Exemple de sortie : `Windows 10`

## FPS (images par seconde) (fps)
Renvoie le nombre actuel d’images par seconde.
```
{"placeholder":"fps"}
```
Exemple de sortie : `120`

## RAM utilisée en Mo (usedram)
Renvoie la quantité de RAM actuellement utilisée (Mo).
```
{"placeholder":"usedram"}
```
Exemple de sortie : `4096`

## RAM maximale en Mo (maxram)
Renvoie la quantité maximale de RAM allouée (Mo).
```
{"placeholder":"maxram"}
```
Exemple de sortie : `8192`

## RAM utilisée en %% (percentram)
Renvoie le pourcentage de RAM actuellement utilisé.
```
{"placeholder":"percentram"}
```
Exemple de sortie : `50`

## Volume d’un élément audio (audio_element_vol)
Renvoie le volume d’un élément audio.
```
{"placeholder":"audio_element_vol","values":{"element_identifier":"background_music"}}
```
Exemple de sortie : `0.5`

## Piste audio actuelle (audio_element_current_track)
Renvoie le nom de la piste d’un élément audio.
```
{"placeholder":"audio_element_current_track","values":{"element_identifier":"background_music","display_name_mappings":"track1.ogg=>Cool Track Name"}}
```
Exemple de sortie : `Cool Track Name`

## Durée audio (audio_duration)
Renvoie la durée totale d’une piste audio au format MM:SS.
```
{"placeholder":"audio_duration","values":{"element_identifier":"background_music"}}
```
Exemple de sortie : `03:45`

## Temps de lecture audio (audio_playtime)
Renvoie le temps de lecture actuel d’une piste audio. Définissez `show_percentage` sur `"true"` pour obtenir une valeur de progression de 0 à 100 au lieu de `MM:SS`.
```
{"placeholder":"audio_playtime","values":{"element_identifier":"background_music","show_percentage":"false"}}
```
Exemple de sortie : `01:30` (ou `45` lorsque `show_percentage` vaut `"true"`)

## État de lecture audio (audio_playing_state)
Renvoie si un élément audio est en cours de lecture (true/false).
```
{"placeholder":"audio_playing_state","values":{"element_identifier":"background_music"}}
```
Exemple de sortie : `true`

## Volume d’un élément vidéo (video_element_vol)
Renvoie le niveau de volume d’un élément vidéo (0.0 à 1.0).
```
{"placeholder":"video_element_vol","values":{"element_identifier":"my_video_element"}}
```
Exemple de sortie : `0.5`

## Durée d’un élément vidéo (video_element_duration)
Renvoie la durée totale d’un élément vidéo au format `MM:SS`. Définissez `output_as_timestamp` sur `"true"` pour renvoyer un horodatage en millisecondes.
```
{"placeholder":"video_element_duration","values":{"element_identifier":"my_video_element","output_as_timestamp":"false"}}
```
Exemple de sortie : `02:00` (ou `120000` lorsque `output_as_timestamp` vaut `"true"`)

## Temps de lecture d’un élément vidéo (video_element_playtime)
Renvoie le temps de lecture actuel (progression) d’un élément vidéo au format `MM:SS`. Définissez `show_percentage` sur `"true"` pour une valeur de progression de 0 à 100, ou `output_as_timestamp` sur `"true"` pour des millisecondes.
```
{"placeholder":"video_element_playtime","values":{"element_identifier":"my_video_element","show_percentage":"false","output_as_timestamp":"false"}}
```
Exemple de sortie : `00:45` (ou `38` en pourcentage, ou `45200` en horodatage)

## État en pause d’un élément vidéo (video_element_paused_state)
Renvoie si un élément vidéo est en pause (true/false).
```
{"placeholder":"video_element_paused_state","values":{"element_identifier":"my_video_element"}}
```
Exemple de sortie : `false`

## Volume d’arrière-plan vidéo (video_background_vol)
Renvoie le niveau de volume d’un arrière-plan vidéo de menu (0.0 à 1.0).
```
{"placeholder":"video_background_vol","values":{"background_identifier":"main_menu_video"}}
```
Exemple de sortie : `0.7`

## Durée d’arrière-plan vidéo (video_background_duration)
Renvoie la durée totale d’un arrière-plan vidéo de menu au format `MM:SS`. Définissez `output_as_timestamp` sur `"true"` pour renvoyer un horodatage en millisecondes.
```
{"placeholder":"video_background_duration","values":{"background_identifier":"main_menu_video","output_as_timestamp":"false"}}
```
Exemple de sortie : `03:00` (ou `180000` lorsque `output_as_timestamp` vaut `"true"`)

## Temps de lecture d’arrière-plan vidéo (video_background_playtime)
Renvoie le temps de lecture actuel (progression) d’un arrière-plan vidéo de menu au format `MM:SS`. Définissez `show_percentage` sur `"true"` pour une valeur de progression de 0 à 100, ou `output_as_timestamp` sur `"true"` pour des millisecondes.
```
{"placeholder":"video_background_playtime","values":{"background_identifier":"main_menu_video","show_percentage":"false","output_as_timestamp":"false"}}
```
Exemple de sortie : `01:00` (ou `33` en pourcentage, ou `60500` en horodatage)

## État en pause d’un arrière-plan vidéo (video_background_paused_state)
Renvoie si un arrière-plan vidéo de menu est en pause (true/false).
```
{"placeholder":"video_background_paused_state","values":{"background_identifier":"main_menu_video"}}
```
Exemple de sortie : `true`

## Calculatrice (calc)
L’espace réservé de calculatrice est un outil puissant qui vous permet d’effectuer des calculs mathématiques dans vos interfaces. Il prend en charge un large éventail d’opérations mathématiques et fonctionne avec des nombres décimaux et entiers.

### Syntaxe de base
```
{"placeholder":"calc","values":{"decimal":"true/false","expression":"your_expression"}}
```

La calculatrice possède deux paramètres principaux :
- `decimal` : Détermine si le résultat doit inclure des décimales (`true`) ou être arrondi à des entiers (`false`)
- `expression` : L’expression mathématique à évaluer

### Opérations prises en charge
La calculatrice prend en charge les opérations mathématiques suivantes :
- Arithmétique de base : `+` (addition), `-` (soustraction), `*` (multiplication), `/` (division)
- Parenthèses : `( )` pour regrouper les opérations
- Puissance : `^` pour les exposants
- Racine carrée : `sqrt()`
- Fonctions trigonométriques : `sin()`, `cos()`, `tan()`
- Constantes mathématiques : `pi`, `e`
- Valeur absolue : `abs()`
- Logarithmes : `log()`, `ln()`

## Nombre aléatoire (random_number)
Génère un nombre aléatoire dans une plage spécifiée.
```
{"placeholder":"random_number","values":{"min":"1","max":"100"}}
```
Exemple de sortie : `42`

## Nombre maximum (maxnum)
Renvoie le plus grand de deux nombres.
```
{"placeholder":"maxnum","values":{"first":"10","second":"20"}}
```
Exemple de sortie : `20`

## Nombre minimum (minnum)
Renvoie le plus petit de deux nombres.
```
{"placeholder":"minnum","values":{"first":"10","second":"20"}}
```
Exemple de sortie : `10`

## Valeur absolue (absnum)
Renvoie la valeur absolue d’un nombre.
```
{"placeholder":"absnum","values":{"num":"-10.5"}}
```
Exemple de sortie : `10.5`

## Négation d’un nombre (negnum)
Renvoie la valeur opposée d’un nombre.
```
{"placeholder":"negnum","values":{"num":"10.5"}}
```
Exemple de sortie : `-10.5`

## *pi* (Math) (math_pi)
Renvoie la valeur de π.
```
{"placeholder":"math_pi"}
```
Exemple de sortie : `3.141592653589793`

## Sinus trigonométrique (Math) (math_sin)
Renvoie le sinus d’un angle.
```
{"placeholder":"math_sin","values":{"angle":"45"}}
```
Exemple de sortie : `0.7071067811865476`

## Cosinus trigonométrique (Math) (math_cos)
Renvoie le cosinus d’un angle.
```
{"placeholder":"math_cos","values":{"angle":"45"}}
```
Exemple de sortie : `0.7071067811865476`

## Tangente trigonométrique (Math) (math_tan)
Renvoie la tangente d’un angle.
```
{"placeholder":"math_tan","values":{"angle":"45"}}
```
Exemple de sortie : `1.0`

## Arrondi inférieur (Math) (math_floor)
Arrondit un nombre à l’entier inférieur le plus proche.
```
{"placeholder":"math_floor","values":{"num":"3.14"}}
```
Exemple de sortie : `3`

## Arrondi supérieur (Math) (math_ceil)
Arrondit un nombre à l’entier supérieur le plus proche.
```
{"placeholder":"math_ceil","values":{"num":"3.14"}}
```
Exemple de sortie : `4`

## Arrondi (Math) (math_round)
Arrondit un nombre. Par défaut, il est arrondi à l’entier le plus proche ; définissez `decimals` sur un nombre positif ou nul pour arrondir à ce nombre de décimales.
```
{"placeholder":"math_round","values":{"num":"3.14159","decimals":"2"}}
```
Exemple de sortie : `3.14` (avec `decimals:-1` ou si omis → `3`)

## Signe (Math) (math_sign)
Renvoie le signe d’un nombre (1 pour positif, -1 pour négatif, 0 pour zéro).
```
{"placeholder":"math_sign","values":{"num":"-3.14"}}
```
Exemple de sortie : `-1`

## Sinus hyperbolique (Math) (math_sinh)
Renvoie le sinus hyperbolique d’un angle.
```
{"placeholder":"math_sinh","values":{"angle":"1"}}
```
Exemple de sortie : `1.1752011936438014`

## Cosinus hyperbolique (Math) (math_cosh)
Renvoie le cosinus hyperbolique d’un angle.
```
{"placeholder":"math_cosh","values":{"angle":"1"}}
```
Exemple de sortie : `1.5430806348152437`

## Tangente hyperbolique (Math) (math_tanh)
Renvoie la tangente hyperbolique d’un angle.
```
{"placeholder":"math_tanh","values":{"angle":"1"}}
```
Exemple de sortie : `0.7615941559557649`

## Fractionner le texte (split_text)
Fractionne du texte à l’aide d’un délimiteur spécifié.
```
{"placeholder":"split_text","values":{"input":"hello,world","regex":",","max_parts":"2","split_index":"1"}}
```
Exemple de sortie : `world`

## Nettoyer le texte (trim_text)
Supprime les espaces en début et en fin de texte.
```
{"placeholder":"trim_text","values":{"text":"  hello world  "}}
```
Exemple de sortie : `hello world`

## Rogner le texte (crop_text)
Supprime des caractères au début et à la fin du texte.
```
{"placeholder":"crop_text","values":{"text":"hello world","remove_from_start":"1","remove_from_end":"1"}}
```
Exemple de sortie : `ello worl`

## Chaîne littérale (stringify)
Convertit du texte en échappant tous les caractères de syntaxe.
```
{"placeholder":"stringify","values":{"text":"text with {special} \"characters\""}}
```
Exemple de sortie : `text with \{special\} \"characters\"`

## Localiser le texte (local)
Récupère le texte localisé pour une clé.
```
{"placeholder":"local","values":{"key":"menu.singleplayer"}}
```
Exemple de sortie : `Singleplayer`

## Texte web (webtext)
Récupère le contenu textuel depuis une URL web.
```
{"placeholder":"webtext","values":{"link":"http://somewebsite.com/textfile.txt"}}
```
Exemple de sortie : Contenu textuel de l’URL

## Texte aléatoire (randomtext)
Renvoie une ligne aléatoire à partir d’un fichier texte, d’une URL ou d’un texte brut direct. Le texte change à des intervalles spécifiés.
```
{"placeholder":"randomtext","values":{"source":"/config/fancymenu/assets/<file_name.txt>","interval":"10"}}
```
Paramètres :
- `source` : Source des lignes de texte (remplace l’ancien paramètre `path`)
  - Chemin de fichier : `/config/fancymenu/assets/quotes.txt`
  - URL : `https://example.com/quotes.txt`
  - Texte brut : `Line 1\nLine 2\nLine 3`
- `interval` : Temps en secondes entre les changements de texte

L’espace réservé prend désormais en charge trois types de source :
1. **Fichiers locaux** : fichiers texte depuis votre répertoire de jeu
   ```
   {"placeholder":"randomtext","values":{"source":"/config/fancymenu/assets/quotes.txt","interval":"10"}}
   ```
2. **URLs** : fichiers texte distants sur Internet
   ```
   {"placeholder":"randomtext","values":{"source":"https://example.com/quotes.txt","interval":"10"}}
   ```
3. **Texte brut** : saisie directe avec des lignes séparées par `\n`
   ```
   {"placeholder":"randomtext","values":{"source":"First line\nSecond line\nThird line","interval":"5"}}
   ```

Remarque : les anciens espaces réservés utilisant `path` au lieu de `source` continueront de fonctionner.

## Analyseur JSON (json)
Analyse des données JSON depuis un fichier, une URL ou du contenu JSON direct, et extrait des valeurs à l’aide d’expressions JSON path.
```
{"placeholder":"json","values":{"source":"path_or_link_or_json_content","json_path":"$.some.json.path"}}
```
Paramètres :
- `source` : Source des données JSON
  - Chemin de fichier : `/config/fancymenu/assets/data.json`
  - URL : `https://api.example.com/data.json`
  - JSON direct : `{"name":"Steve","level":42}`
- `json_path` : L’expression JSON path utilisée pour extraire les données

L’espace réservé prend désormais en charge trois types de source :
1. **Fichiers locaux** : fichiers JSON depuis votre répertoire de jeu
   ```
   {"placeholder":"json","values":{"source":"/config/fancymenu/assets/playerdata.json","json_path":"$.player.name"}}
   ```
2. **URLs** : données JSON distantes provenant d’API ou de services web
   ```
   {"placeholder":"json","values":{"source":"https://api.minecraft.com/server/status","json_path":"$.online"}}
   ```
3. **JSON direct** : contenu JSON intégré
   ```
   {"placeholder":"json","values":{"source":"{"name":"Steve","score":42,"rank":"Diamond"}","json_path":"$.rank"}}
   ```

Exemples de chemins JSON :
- `$.name` - Récupère le champ "name" à la racine
- `$.player.level` - Récupère le champ imbriqué "level" dans "player"
- `$.items[0].id` - Récupère l’"id" du premier élément d’un tableau
- `$.scores.*` - Récupère toutes les valeurs de l’objet "scores"

## Chemin absolu de fichier/dossier (absolute_path)
Renvoie le chemin absolu d’un fichier.
```
{"placeholder":"absolute_path","values":{"short_path":"relative/path/to/file.txt"}}
```
Exemple de sortie : `C:/Users/Username/AppData/Roaming/.minecraft/relative/path/to/file.txt`

## Nombre de caractères du texte (text_character_count)
Renvoie le nombre de caractères du texte donné.
```
{"placeholder":"text_character_count","values":{"text":"Hello World!"}}
```
Exemple de sortie : `12`

## Largeur du texte (text_width)
Renvoie la largeur en pixels du texte donné lorsqu’il est rendu.
```
{"placeholder":"text_width","values":{"text":"Hello World!"}}
```
Exemple de sortie : `66`

## Texte en majuscules (uppercase_text)
Convertit le texte saisi en lettres majuscules.
```
{"placeholder":"uppercase_text","values":{"text":"Hello World"}}
```
Exemple de sortie : `HELLO WORLD`

## Texte en minuscules (lowercase_text)
Convertit le texte saisi en lettres minuscules.
```
{"placeholder":"lowercase_text","values":{"text":"Hello World"}}
```
Exemple de sortie : `hello world`

## Texte en casse de titre (title_case_text)
Convertit le texte saisi en casse de titre.
```
{"placeholder":"title_case_text","values":{"text":"hello world"}}
```
Exemple de sortie : `Hello World`

## Texte en casse de phrase (sentence_case_text)
Convertit le texte saisi en casse de phrase.
```
{"placeholder":"sentence_case_text","values":{"text":"hello world. this is fancymenu!"}}
```
Exemple de sortie : `Hello world. This is fancymenu!`

## Texte en snake_case (snake_case_text)
Convertit le texte saisi en `snake_case`.
```
{"placeholder":"snake_case_text","values":{"text":"Hello World"}}
```
Exemple de sortie : `hello_world`

## Texte en kebab-case (kebab_case_text)
Convertit le texte saisi en `kebab-case`.
```
{"placeholder":"kebab_case_text","values":{"text":"Hello World"}}
```
Exemple de sortie : `hello-world`

## Texte en casse alternée (alternating_case_text)
Convertit le texte saisi en casse alternée.
```
{"placeholder":"alternating_case_text","values":{"text":"alternating case"}}
```
Exemple de sortie : `aLtErNaTiNg CaSe`

## Inverser la casse du texte (toggle_case_text)
Inverse la casse de chaque lettre du texte saisi.
```
{"placeholder":"toggle_case_text","values":{"text":"Toggle Case"}}
```
Exemple de sortie : `tOGGLE cASE`

## Encoder en Base64 (base64_encode)
Encode le texte donné en Base64.
```
{"placeholder":"base64_encode","values":{"text":"Hello World"}}
```
Exemple de sortie : `SGVsbG8gV29ybGQ=`

## Décoder depuis Base64 (base64_decode)
Décode une chaîne Base64 en texte brut.
```
{"placeholder":"base64_decode","values":{"text":"SGVsbG8gV29ybGQ="}}
```
Exemple de sortie : `Hello World`

## Texte d’un fichier (file_text)
Renvoie des lignes de texte d’un fichier ou d’une URL. Peut renvoyer toutes les lignes ou seulement les X dernières lignes.
```
{"placeholder":"file_text","values":{"path_or_url":"/config/fancymenu/assets/some_file.txt","mode":"all","separator":"\n","last_lines":"1"}}
```
Paramètres :
- `path_or_url` : Chemin de fichier ou URL à lire
- `mode` : Soit `"all"` (renvoie toutes les lignes) soit `"last"` (renvoie seulement les X dernières lignes)
- `separator` : Texte utilisé pour joindre les lignes (par défaut : `"\n"`)
- `last_lines` : Nombre de lignes à renvoyer lorsque le mode est `"last"` (par défaut : `"1"`)

Exemple de sortie : Dépend du contenu du fichier

## Contenu du presse-papiers (clipboard_content)
Renvoie le contenu textuel actuellement stocké dans le presse-papiers du système.
```
{"placeholder":"clipboard_content"}
```
Exemple de sortie : Le texte actuellement dans le presse-papiers

## Remplacer du texte (replace_text)
Remplace du texte dans une chaîne à l’aide de texte littéral ou d’expressions régulières.
```
{"placeholder":"replace_text","values":{"text":"Hello World! This is a test.","search":"World","replacement":"FancyMenu","use_regex":"false","replace_all":"true"}}
```
Paramètres :
- `text` : Texte d’entrée à traiter
- `search` : Texte ou motif regex à rechercher
- `replacement` : Texte de remplacement
- `use_regex` : Indique si les expressions régulières doivent être utilisées (`"true"`) ou non (`"false"`)
- `replace_all` : Remplace toutes les occurrences (`"true"`) ou seulement la première (`"false"`)

Exemple de sortie : `Hello FancyMenu! This is a test.`

## Sélection multiple (switch_case)
Effectue une opération de type switch-case selon une valeur.
```
{"placeholder":"switch_case","values":{"value":"1","cases":"1:first case,2:second case,3:third case","default":"default case"}}
```
Exemple de sortie : `first case` (si la valeur est 1)

## Obtenir la valeur d’une variable (Variable FM) (getvariable)
Récupère la valeur d’une variable précédemment stockée.
```
{"placeholder":"getvariable","values":{"name":"some_variable"}}
```
Exemple de sortie : Dépend de la valeur stockée

## Obtenir des données NBT (nbt_data_get)
Récupère des données NBT côté client (similaire à la commande `/data get`). Utilisez la variante serveur `nbt_data_get_server` lorsque vous êtes connecté à un serveur et que vous avez besoin de valeurs fiables côté serveur.
```
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"foodLevel","scale":"1.0","return_type":"value"}}
```
Paramètres :
- `source_type` : soit `"entity"` soit `"block"`
- `entity_selector` : Sélecteur d’entité comme `@s`, `@p`, `@e`, ou UUID/nom (pour les entités)
- `block_pos` : Position du bloc au format `"x y z"` (pour les blocs)
- `nbt_path` : Chemin NBT à récupérer
- `scale` : Facteur d’échelle optionnel pour les valeurs numériques (par défaut : `"1.0"`)
- `return_type` : Manière de renvoyer les données :
  - `"value"` : Valeur par défaut, renvoie la valeur (avec mise à l’échelle optionnelle pour les nombres)
  - `"string"` : Renvoie les données NBT réelles sous forme de chaîne
  - `"snbt"` : Renvoie au format SNBT (NBT formaté)
  - `"json"` : Renvoie sous forme de composant formaté JSON (pour les balises composées)

Exemple de sortie : `20` (pour le niveau de faim)

## Obtenir des données NBT (côté serveur) (nbt_data_get_server)
Interroge les données NBT côté serveur (à l’aide d’un paquet) et met les résultats en cache brièvement. Les valeurs reflètent l’espace réservé côté client.
```
{"placeholder":"nbt_data_get_server","values":{"source_type":"entity","entity_selector":"@s","block_pos":"","storage_id":"minecraft:storage_key","nbt_path":"SelectedItem.id","scale":"1.0","return_type":"value"}}
```
Exemple de sortie : `minecraft:diamond_sword`

## Dernier message de mort (lastdeathmessage)
Renvoie le dernier message de mort enregistré du joueur client. Définissez `as_json_component` sur `"true"` pour obtenir le composant texte JSON brut.
```
{"placeholder":"lastdeathmessage","values":{"as_json_component":"false"}}
```
Exemple de sortie : `Steve was slain by Zombie`

## Durée de fonctionnement (uptime_duration)
Renvoie depuis combien de temps FancyMenu est chargé. Par défaut, la valeur est en secondes ; définissez `output_as_millis` sur `"true"` pour recevoir des millisecondes.
```
{"placeholder":"uptime_duration","values":{"output_as_millis":"false"}}
```
Exemple de sortie : `742` (secondes depuis le chargement)

## Noms des sauvegardes du monde (level_save_names)
Liste tous les noms locaux des sauvegardes de mondes, joints par le séparateur choisi. S’exécute dans le thread client.
```
{"placeholder":"level_save_names","values":{"separator":", "}}
```
Exemple de sortie : `Creative Test, Survival World, Hardcore`

## Données de sauvegarde du monde (level_save_data)
Renvoie les données sérialisées du monde pour le nom de monde donné (doit correspondre au nom affiché dans la liste des sauvegardes).
```
{"placeholder":"level_save_data","values":{"level_name":"Survival World"}}
```
Exemple de sortie : `{"name":"Survival World","gameMode":"survival",...}`

## Conversion de base numérique (number_base_convert)
Convertit un nombre (entier ou fractionnaire) d’une base à une autre (2–36). Utilise la base décimale par défaut si les bases ne sont pas fournies.
```
{"placeholder":"number_base_convert","values":{"input":"67.5","from_base":"10","to_base":"16"}}
```
Exemple de sortie : `43.8`

## Taille d’un fichier (file_size)
Renvoie la taille d’un fichier local en octets. Seuls les chemins locaux sont autorisés.
```
{"placeholder":"file_size","values":{"path":"/config/fancymenu/assets/notes.txt"}}
```
Exemple de sortie : `1284`

## MD5 d’un fichier (file_md5)
Renvoie le hachage MD5 d’un fichier local sous forme de chaîne hexadécimale en minuscules.
```
{"placeholder":"file_md5","values":{"path":"/config/fancymenu/assets/notes.txt"}}
```
Exemple de sortie : `d41d8cd98f00b204e9800998ecf8427e`

# Exemples pratiques

## Créer un affichage mémoire dynamique
```
RAM utilisée : {"placeholder":"usedram"}Mo / {"placeholder":"maxram"}Mo ({"placeholder":"percentram"}%)
```

## Créer une horloge en temps réel
```
{"placeholder":"realtimehour"}:{"placeholder":"realtimeminute"}:{"placeholder":"realtimesecond"}
```

## Créer un affichage d’informations système
```
OS : {"placeholder":"osname"}
CPU : {"placeholder":"cpuinfo"}
GPU : {"placeholder":"gpuinfo"}
Java : {"placeholder":"javaver"}
```

## HUD d’état du joueur
```
Santé : {"placeholder":"current_player_health"} / {"placeholder":"max_player_health"} ({"placeholder":"current_player_health_percent"}%)
Armure : {"placeholder":"current_player_armor"} / {"placeholder":"max_player_armor"}
Niveau d’XP : {"placeholder":"current_player_level"}
```

## Calcul complexe avec espaces réservés imbriqués
```
{"placeholder":"calc","values":{"decimal":"true","expression":"({"placeholder":"usedram"} / {"placeholder":"maxram"}) * 100"}}
```

## Affichage des coordonnées avec arrondi
```
X : {"placeholder":"math_round","values":{"num":"{"placeholder":"player_x_coordinate"}"}}
Y : {"placeholder":"math_round","values":{"num":"{"placeholder":"player_y_coordinate"}"}}
Z : {"placeholder":"math_round","values":{"num":"{"placeholder":"player_z_coordinate"}"}}
```

# Bonnes pratiques

1. **Mettre en cache les opérations coûteuses** : certains espaces réservés (comme ceux qui lisent des informations système) peuvent être gourmands en ressources. Pensez à utiliser des variables pour stocker leurs valeurs si vous devez les réutiliser plusieurs fois.

2. **Utiliser des réglages décimaux appropriés** : lors d’un calcul, utilisez le paramètre `decimal` de manière adaptée. Réglez-le sur `false` lorsque vous avez besoin d’entiers et sur `true` lorsque vous avez besoin de valeurs décimales précises.

3. **Gérer les valeurs manquantes** : envisagez toujours ce qu’il faut faire si un espace réservé ne renvoie aucune valeur. Vous pouvez fournir des valeurs par défaut dans ce cas.

4. **Tester les performances** : lorsque vous utilisez beaucoup d’espaces réservés ou des structures imbriquées complexes, testez l’impact sur les performances, en particulier sur les systèmes moins puissants.

5. **Utiliser un dimensionnement/positionnement avancé** : pour les éléments d’interface dynamiques, combinez les espaces réservés avec un dimensionnement et un positionnement avancés afin de créer des interfaces réactives.

6. **Combiner avec des variables** : utilisez les espaces réservés avec des variables pour un contenu encore plus dynamique pouvant être mis à jour via des actions.

# Problèmes courants et solutions

## L’espace réservé ne se met pas à jour
Si la valeur d’un espace réservé ne se met pas à jour comme prévu, vérifiez :
- Si l’espace réservé est correctement formaté
- Si vous utilisez la bonne casse pour les identifiants d’espaces réservés
- Si l’espace réservé nécessite des conditions spécifiques pour se mettre à jour

## Les espaces réservés imbriqués ne fonctionnent pas
Lors de l’imbrication d’espaces réservés :
- Assurez-vous que les guillemets sont correctement échappés
- Vérifiez que chaque espace réservé imbriqué est valide individuellement

## Problèmes de performances
Si vous constatez des problèmes de performances :
- Réduisez le nombre d’espaces réservés utilisés
- Évitez les imbrications inutiles
- Pensez à utiliser des variables pour les valeurs fréquemment consultées
- Utilisez l’espace réservé approprié à votre besoin (par exemple, n’utilisez pas des espaces réservés en temps réel quand des valeurs statiques suffisent)
