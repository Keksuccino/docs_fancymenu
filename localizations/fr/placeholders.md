---
title: Espaces réservés
description: Comment utiliser les espaces réservés.
---
# Espaces réservés

Les espaces réservés sont des valeurs dynamiques qui sont remplacées par du contenu réel lorsqu’ils sont utilisés. Dans FancyMenu, les espaces réservés vous permettent d’insérer du contenu dynamique dans divers éléments comme le texte, les boutons et les conditions de chargement. Voyez-les comme des variables qui sont évaluées et remplacées par leurs valeurs réelles lorsque vos mises en page s’affichent.

# Informations générales

## Syntaxe de base
Les espaces réservés dans FancyMenu utilisent une syntaxe proche du JSON :
```
{"placeholder":"modversion","values":{"modid":"fancymenu"}}
```

Par exemple, pour afficher le nom du joueur :
```
{"placeholder":"playername"}
```

## Imbrication d’espaces réservés
L’une des fonctionnalités les plus puissantes du système d’espaces réservés de FancyMenu est la possibilité d’imbriquer des espaces réservés dans d’autres espaces réservés. Cela signifie que vous pouvez utiliser la sortie d’un espace réservé comme entrée d’un autre.

Exemple d’espaces réservés imbriqués :
```
{"placeholder":"calc","values":{"decimal":"true","expression":"{"placeholder":"maxram"} / 1024"}}
```
Cet exemple prend la valeur maximale de RAM et la divise par 1024 pour la convertir de Mo en Go.

> [!IMPORTANT]
> Contrairement au vrai JSON, les espaces réservés imbriqués ne sont **pas** **échappés** avec `\`. C’est très important, car les espaces réservés cesseront de fonctionner s’ils sont échappés (évidemment). Les espaces réservés utilisent simplement une syntaxe proche du JSON. Ce n’est pas du vrai JSON.

# Utiliser les espaces réservés

La plupart des éléments disposant de champs de texte prennent en charge les espaces réservés. Vous pouvez voir si un champ texte les prend en charge lorsque vous le modifiez. Si l’**éditeur de texte** plein écran s’ouvre lorsque vous modifiez le texte, cela signifie qu’il prend en charge les espaces réservés. 

Pour trouver une **liste de tous les espaces réservés**, cliquez simplement sur le bouton **Espaces réservés** dans le **coin supérieur droit** de l’**éditeur de texte**.

Une **barre de recherche** se trouve en haut de la liste des espaces réservés et vous permet d’en rechercher.

Cliquer sur un espace réservé dans la liste l’insérera dans le contenu texte.

# Détails des espaces réservés

Cette liste contient la plupart, sinon la totalité, des espaces réservés disponibles dans FancyMenu. La liste peut parfois être un peu obsolète à cause des mises à jour du mod.

## Nom du joueur (playername)
Renvoie le nom d’utilisateur actuel du joueur.
```
{"placeholder":"playername"}
```
Sortie exemple : `Steve`

## UUID du joueur (playeruuid)
Renvoie l’identifiant unique du joueur.
```
{"placeholder":"playeruuid"}
```
Sortie exemple : `c8cde7fe-7ced-11eb-9439-0242ac130002`

## Version de Minecraft (mcversion)
Renvoie la version actuelle de Minecraft.
```
{"placeholder":"mcversion"}
```
Sortie exemple : `1.19.2`

## Version du chargeur de mods (loaderver)
Renvoie la version du chargeur de mods (Forge/Fabric).
```
{"placeholder":"loaderver"}
```
Sortie exemple : `43.2.0`

## Nom du chargeur de mods (loadername)
Renvoie le nom du chargeur de mods.
```
{"placeholder":"loadername"}
```
Sortie exemple : `Forge`

## Version du mod (modversion)
Renvoie la version d’un mod spécifique.
```
{"placeholder":"modversion","values":{"modid":"fancymenu"}}
```
Sortie exemple : `2.14.9`

## Nombre total de mods (totalmods)
Renvoie le nombre total de mods installés.
```
{"placeholder":"totalmods"}
```
Sortie exemple : `45`

## Nombre de mods actifs (loadedmods)
Renvoie le nombre de mods actuellement chargés.
```
{"placeholder":"loadedmods"}
```
Sortie exemple : `43`

## Progression du chargement du monde (world_load_progress)
Renvoie la progression actuelle du chargement du monde en pourcentage.
```
{"placeholder":"world_load_progress"}
```
Sortie exemple : `75`

## Valeur d’une option Minecraft (minecraft_option_value)
Renvoie la valeur d’une option Minecraft.
```
{"placeholder":"minecraft_option_value","values":{"name":"fov"}}
```
Sortie exemple : `70`

## Dernier monde ou serveur (last_world_server)
Renvoie des informations sur le dernier monde ou serveur consulté.
```
{"placeholder":"last_world_server","values":{"type":"both","full_world_path":"true"}}
```
Paramètres :
- `type` : détermine quel type d’information renvoyer
  - `"both"` : renvoie le dernier monde ou serveur consulté (par défaut)
  - `"server"` : renvoie uniquement si le dernier élément consulté était un serveur
  - `"world"` : renvoie uniquement si le dernier élément consulté était un monde
- `full_world_path` : contrôle l’affichage des chemins de monde
  - `"true"` : renvoie le chemin complet du monde (par défaut)
  - `"false"` : renvoie seulement le nom du monde sans le chemin (n’affecte pas les serveurs)

Exemples :
- Serveur : `mc.hypixel.net`
- Monde avec chemin complet : `saves/New World`
- Monde sans chemin complet : `New World`

## Largeur de l’écran (guiwidth)
Renvoie la largeur actuelle de l’écran.
```
{"placeholder":"guiwidth"}
```
Sortie exemple : `1920`

## Hauteur de l’écran (guiheight)
Renvoie la hauteur actuelle de l’écran.
```
{"placeholder":"guiheight"}
```
Sortie exemple : `1080`

## Identifiant de l’écran actuel (screenid)
Renvoie l’identifiant de l’écran actuel.
```
{"placeholder":"screenid"}
```
Sortie exemple : `title_screen`

## Largeur d’un élément (elementwidth)
Renvoie la largeur d’un élément spécifique.
```
{"placeholder":"elementwidth","values":{"id":"my_button"}}
```
Sortie exemple : `200`

## Hauteur d’un élément (elementheight)
Renvoie la hauteur d’un élément spécifique.
```
{"placeholder":"elementheight","values":{"id":"my_button"}}
```
Sortie exemple : `20`

## Position X d’un élément (elementposx)
Renvoie la position X d’un élément spécifique.
```
{"placeholder":"elementposx","values":{"id":"my_button"}}
```
Sortie exemple : `150`

## Position Y d’un élément (elementposy)
Renvoie la position Y d’un élément spécifique.
```
{"placeholder":"elementposy","values":{"id":"my_button"}}
```
Sortie exemple : `100`

## Position X de la souris (mouseposx)
Renvoie la position X actuelle de la souris.
```
{"placeholder":"mouseposx"}
```
Sortie exemple : `960`

## Position Y de la souris (mouseposy)
Renvoie la position Y actuelle de la souris.
```
{"placeholder":"mouseposy"}
```
Sortie exemple : `540`

## Clics par seconde (clicks_per_second)
Renvoie le nombre actuel de clics par seconde pour un bouton de souris.
```
{"placeholder":"clicks_per_second","values":{"mouse_button":"left"}}
```
Paramètres :
- `mouse_button` : `left` ou `right`

Sortie exemple : `8`

## Échelle de l’interface (guiscale)
Renvoie l’échelle actuelle de l’interface graphique.
```
{"placeholder":"guiscale"}
```
Sortie exemple : `2`

## Libellé/texte d’un widget/bouton vanilla (vanillabuttonlabel)
Renvoie le libellé/texte d’un widget/bouton vanilla.
```
{"placeholder":"vanillabuttonlabel","values":{"locator":"some.menu.identifier:505280"}}
```
Sortie exemple : `Options...`

## Valeur d’un champ de saisie (text_input_field_value)
Renvoie la valeur actuelle d’un champ de saisie personnalisé ou vanilla à partir de l’identifiant de l’élément.
```
{"placeholder":"text_input_field_value","values":{"element_identifier":"my_input"}}
```
Sortie exemple : `Hello World`

## Santé actuelle du joueur (current_player_health)
Renvoie les points de vie actuels du joueur.
```
{"placeholder":"current_player_health"}
```
Sortie exemple : `20.0`

## Santé maximale du joueur (max_player_health)
Renvoie les points de vie maximum du joueur.
```
{"placeholder":"max_player_health"}
```
Sortie exemple : `20.0`

## Santé actuelle du joueur (pourcentage) (current_player_health_percent)
Renvoie la santé du joueur en pourcentage.
```
{"placeholder":"current_player_health_percent"}
```
Sortie exemple : `100`

## Santé d’absorption actuelle du joueur (current_player_absorption_health)
Renvoie les points de vie d’absorption du joueur (cœurs dorés).
```
{"placeholder":"current_player_absorption_health"}
```
Sortie exemple : `4.0`

## Santé d’absorption maximale du joueur (max_player_absorption_health)
Renvoie la santé d’absorption maximale.
```
{"placeholder":"max_player_absorption_health"}
```
Sortie exemple : `4.0`

## Santé d’absorption actuelle du joueur (pourcentage) (current_player_absorption_health_percent)
Renvoie la santé d’absorption du joueur en pourcentage.
```
{"placeholder":"current_player_absorption_health_percent"}
```
Sortie exemple : `100`

## Niveau de faim actuel du joueur (current_player_hunger)
Renvoie le niveau de faim actuel du joueur.
```
{"placeholder":"current_player_hunger"}
```
Sortie exemple : `20`

## Niveau de faim maximal du joueur (max_player_hunger)
Renvoie le niveau de faim maximum.
```
{"placeholder":"max_player_hunger"}
```
Sortie exemple : `20`

## Niveau de faim actuel du joueur (pourcentage) (current_player_hunger_percent)
Renvoie la faim du joueur en pourcentage.
```
{"placeholder":"current_player_hunger_percent"}
```
Sortie exemple : `100`

## Saturation de faim actuelle du joueur (current_player_hunger_saturation)
Renvoie la valeur actuelle de saturation de faim du joueur.
```
{"placeholder":"current_player_hunger_saturation"}
```
Sortie exemple : `5.0`

## Armure actuelle du joueur (current_player_armor)
Renvoie la valeur actuelle d’armure du joueur.
```
{"placeholder":"current_player_armor"}
```
Sortie exemple : `20`

## Robustesse de l’armure du joueur (player_armor_toughness)
Renvoie la valeur totale de robustesse d’armure du joueur.
```
{"placeholder":"player_armor_toughness"}
```
Sortie exemple : `8.0`

## Armure maximale du joueur (max_player_armor)
Renvoie la valeur maximale d’armure.
```
{"placeholder":"max_player_armor"}
```
Sortie exemple : `20`

## Armure actuelle du joueur (pourcentage) (current_player_armor_percent)
Renvoie l’armure du joueur en pourcentage.
```
{"placeholder":"current_player_armor_percent"}
```
Sortie exemple : `100`

## Niveau d’oxygène actuel du joueur (current_player_oxygen)
Renvoie le niveau d’oxygène actuel du joueur (bulles d’air).
```
{"placeholder":"current_player_oxygen"}
```
Sortie exemple : `300`

## Niveau d’oxygène maximal du joueur (max_player_oxygen)
Renvoie le niveau d’oxygène maximum.
```
{"placeholder":"max_player_oxygen"}
```
Sortie exemple : `300`

## Niveau d’oxygène actuel du joueur (pourcentage) (current_player_oxygen_percent)
Renvoie le niveau d’oxygène du joueur en pourcentage.
```
{"placeholder":"current_player_oxygen_percent"}
```
Sortie exemple : `100`

## Niveau actuel du joueur (current_player_level)
Renvoie le niveau d’expérience actuel du joueur.
```
{"placeholder":"current_player_level"}
```
Sortie exemple : `30`

## Expérience actuelle du joueur (current_player_exp)
Renvoie le total de points d’expérience du joueur.
```
{"placeholder":"current_player_exp"}
```
Sortie exemple : `1250`

## Progression d’expérience du joueur (pourcentage) (current_player_exp_progress)
Renvoie la progression d’expérience du joueur vers le niveau suivant en pourcentage.
```
{"placeholder":"current_player_exp_progress"}
```
Sortie exemple : `75`

## Force d’attaque du joueur (pourcentage) (player_attack_strength)
Renvoie le temps de recharge d’attaque du joueur en pourcentage.
```
{"placeholder":"player_attack_strength"}
```
Sortie exemple : `100`

## Mode de jeu du joueur (player_gamemode)
Renvoie le mode de jeu actuel du joueur.
```
{"placeholder":"player_gamemode"}
```
Sortie exemple : `survival`

## Direction de regard du joueur (player_view_direction)
Renvoie la direction vers laquelle le joueur fait face.
```
{"placeholder":"player_view_direction"}
```
Sortie exemple : `north`

## Coordonnée X du joueur (player_x_coordinate)
Renvoie la position X du joueur dans le monde.
```
{"placeholder":"player_x_coordinate"}
```
Sortie exemple : `125`

## Coordonnée Y du joueur (player_y_coordinate)
Renvoie la position Y du joueur dans le monde.
```
{"placeholder":"player_y_coordinate"}
```
Sortie exemple : `64`

## Coordonnée Z du joueur (player_z_coordinate)
Renvoie la position Z du joueur dans le monde.
```
{"placeholder":"player_z_coordinate"}
```
Sortie exemple : `-250`

## Santé actuelle de la monture (current_mount_health)
Renvoie la santé actuelle de l’entité montée par le joueur.
```
{"placeholder":"current_mount_health"}
```
Sortie exemple : `30.0`

## Santé maximale de la monture (max_mount_health)
Renvoie la santé maximale de l’entité montée par le joueur.
```
{"placeholder":"max_mount_health"}
```
Sortie exemple : `30.0`

## Santé actuelle de la monture (pourcentage) (current_mount_health_percent)
Renvoie la santé de la monture en pourcentage.
```
{"placeholder":"current_mount_health_percent"}
```
Sortie exemple : `100`

## Jauge de saut actuelle de la monture (pourcentage) (current_mount_jump_meter)
Renvoie la valeur actuelle de la jauge de saut de la monture.
```
{"placeholder":"current_mount_jump_meter"}
```
Sortie exemple : `75`

## Santé actuelle du boss (pourcentage) (current_boss_health)
Renvoie la santé du boss actif.
```
{"placeholder":"current_boss_health"}
```
Sortie exemple : `150.0`

## Nom du boss (boss_name)
Renvoie le nom du boss actif.
```
{"placeholder":"boss_name","values":{"boss_index":"0","as_json":"false"}}
```
Sortie exemple : `Ender Dragon`

## Nombre de boss (boss_count)
Renvoie le nombre de boss actifs.
```
{"placeholder":"boss_count"}
```
Sortie exemple : `1`

## Nombre d’effets actifs (effects_count)
Renvoie le nombre d’effets de potion actifs.
```
{"placeholder":"effects_count"}
```
Sortie exemple : `3`

## Effet actif (active_effect)
Renvoie des informations sur un effet actif spécifique.
```
{"placeholder":"active_effect","values":{"effect_index":"0"}}
```
Sortie exemple : `minecraft:speed`

## Emplacement sélectionné de la barre rapide (active_hotbar_slot)
Renvoie l’emplacement actuellement sélectionné de la barre rapide (0-8).
```
{"placeholder":"active_hotbar_slot"}
```
Sortie exemple : `4`

## Objet d’un emplacement (slot_item)
Renvoie des informations sur l’objet contenu dans un emplacement d’inventaire spécifique.
```
{"placeholder":"slot_item","values":{"slot":"0"}}
```
Sortie exemple : `minecraft:diamond_sword`

## Quantité d’objets dans un emplacement (slot_item_count)
Renvoie la taille de pile de l’objet dans un emplacement d’inventaire joueur spécifique.
```
{"placeholder":"slot_item_count","values":{"slot":"0"}}
```
Sortie exemple : `64`

## Durabilité d’un objet dans un emplacement (slot_item_durability)
Renvoie des informations de durabilité pour l’objet dans un emplacement d’inventaire joueur spécifique.
```
{"placeholder":"slot_item_durability","values":{"slot":"0","format":"percentage"}}
```
Paramètres :
- `slot` : numéro de l’emplacement de l’inventaire du joueur.
- `format` : `current`, `remaining`, `max`, `damage`, `percentage`, ou `percent`.

Sortie exemple : `87`

## Nom affiché d’un objet dans un emplacement (slot_item_display_name_fm)
Renvoie le nom affiché de l’objet dans un emplacement spécifique sous forme de composant texte JSON. En mode spectateur, les emplacements de la barre rapide peuvent résoudre les noms des objets du menu spectateur, sauf si `ignore_spectator` est `true`.
```
{"placeholder":"slot_item_display_name_fm","values":{"slot":"0","ignore_spectator":"false"}}
```
Sortie exemple : `{"text":"Diamond Sword","color":"aqua"}`

## Quantité d’un objet dans l’inventaire (inventory_item_count)
Renvoie la quantité totale d’un type d’objet dans l’inventaire du joueur. Si `item` est vide, compte toutes les piles d’objets dans l’inventaire.
```
{"placeholder":"inventory_item_count","values":{"item":"minecraft:diamond"}}
```
Sortie exemple : `12`

## Quantité de nourriture restaurée par un objet dans un emplacement (inventory_slot_food_point_restore_amount)
Renvoie les points de faim restaurés par l’objet alimentaire dans l’emplacement d’inventaire du joueur donné.
```
{"placeholder":"inventory_slot_food_point_restore_amount","values":{"slot":"0"}}
```
Sortie exemple : `4.0`

## Objet d’inventaire survolé (hovered_inventory_item)
Renvoie la clé de l’objet actuellement survolé dans un écran d’inventaire.
```
{"placeholder":"hovered_inventory_item"}
```
Sortie exemple : `minecraft:apple`

## Temps de jeu du monde (game_time)
Renvoie le compteur de ticks du temps actuel en jeu.
```
{"placeholder":"game_time"}
```
Sortie exemple : `18000`

## Heure du monde (world_daytime)
Renvoie l’heure actuelle du monde.
```
{"placeholder":"world_daytime"}
```
Sortie exemple : `13000`

## Heure du monde, composant heure (world_daytime_hour)
Renvoie le composant heure du temps du monde. Par défaut, le format 24 heures est utilisé ; définissez `twelve_hour_format` sur `"true"` pour un format 12 heures.
```
{"placeholder":"world_daytime_hour","values":{"twelve_hour_format":"false"}}
```
Sortie exemple : `12`

## Heure du monde, composant minute (world_daytime_minute)
Renvoie le composant minute du temps du monde (00-59).
```
{"placeholder":"world_daytime_minute"}
```
Sortie exemple : `30`

## Difficulté du monde (world_difficulty)
Renvoie la difficulté actuelle du monde.
```
{"placeholder":"world_difficulty"}
```
Sortie exemple : `normal`

## Seed du monde actuel (current_world_seed)
Renvoie la seed du monde solo actuel. Renvoie une valeur vide lorsque la seed n’est pas disponible.
```
{"placeholder":"current_world_seed"}
```
Sortie exemple : `123456789`

## Biome actuel (current_biome)
Renvoie le biome dans lequel se trouve actuellement le joueur. Définissez `as_key` sur `"false"` pour renvoyer un nom traduit/affiché lorsque disponible.
```
{"placeholder":"current_biome","values":{"as_key":"true"}}
```
Sortie exemple : `minecraft:plains`

## Dimension actuelle (current_dimension)
Renvoie la dimension dans laquelle se trouve actuellement le joueur. Définissez `as_key` sur `"false"` pour renvoyer un nom traduit/affiché lorsque disponible.
```
{"placeholder":"current_dimension","values":{"as_key":"true"}}
```
Sortie exemple : `minecraft:overworld`

## Valeur d’une règle de jeu (gamerule_value)
Renvoie la valeur actuelle d’une règle de jeu dans le monde/serveur chargé. Les mondes serveur nécessitent FancyMenu sur le serveur.
```
{"placeholder":"gamerule_value","values":{"name":"doDaylightCycle"}}
```
Sortie exemple : `true`

## Catégorie d’objet (item_category)
Renvoie la catégorie de l’onglet créatif d’un objet. Définissez `as_key` sur `"true"` pour renvoyer la clé de la catégorie au lieu du nom affiché.
```
{"placeholder":"item_category","values":{"item":"minecraft:diamond_sword","as_key":"false"}}
```
Sortie exemple : `Combat`

## Titre/Sous-titre HUD actuel (current_title)
Renvoie le texte du titre actuellement affiché.
```
{"placeholder":"current_title","values":{"is_subtitle":"false","as_json":"false"}}
```
Sortie exemple : `Game Over!`

## Message de la barre d’action (action_bar_message_fm)
Renvoie le message actuel de la barre d’action vanilla au-dessus de la barre rapide.
```
{"placeholder":"action_bar_message_fm"}
```
Sortie exemple : `You may not rest now`

## Durée du message de la barre d’action (action_bar_message_time_fm)
Renvoie combien de ticks le message actuel de la barre d’action vanilla restera affiché.
```
{"placeholder":"action_bar_message_time_fm"}
```
Sortie exemple : `42`

## Rotation X de la caméra (camera_rotation_x_fm)
Renvoie l’inclinaison actuelle de la caméra en degrés.
```
{"placeholder":"camera_rotation_x_fm"}
```
Sortie exemple : `12.5`

## Rotation Y de la caméra (camera_rotation_y_fm)
Renvoie le lacet actuel de la caméra en degrés.
```
{"placeholder":"camera_rotation_y_fm"}
```
Sortie exemple : `-90.0`

## Variation X de rotation de la caméra (camera_rotation_delta_x_fm)
Renvoie la variation par tick de l’inclinaison de la caméra.
```
{"placeholder":"camera_rotation_delta_x_fm"}
```
Sortie exemple : `0.4`

## Variation Y de rotation de la caméra (camera_rotation_delta_y_fm)
Renvoie la variation par tick du lacet de la caméra.
```
{"placeholder":"camera_rotation_delta_y_fm"}
```
Sortie exemple : `-1.2`

## Durée de l’objet surligné (highlighted_item_time_fm)
Renvoie combien de ticks le nom de l’objet surligné restera affiché au-dessus de la barre rapide.
```
{"placeholder":"highlighted_item_time_fm"}
```
Sortie exemple : `30`

## Progression d’utilisation de l’objet par le joueur (player_item_use_progress_fm)
Renvoie la progression actuelle d’utilisation de l’objet de `0.0` à `1.0`.
```
{"placeholder":"player_item_use_progress_fm"}
```
Sortie exemple : `0.65`

## Variation X de position du joueur (player_position_delta_x_fm)
Renvoie la variation par tick de la position du joueur sur l’axe X.
```
{"placeholder":"player_position_delta_x_fm"}
```
Sortie exemple : `0.0`

## Variation Y de position du joueur (player_position_delta_y_fm)
Renvoie la variation par tick de la position du joueur sur l’axe Y.
```
{"placeholder":"player_position_delta_y_fm"}
```
Sortie exemple : `-0.08`

## Variation Z de position du joueur (player_position_delta_z_fm)
Renvoie la variation par tick de la position du joueur sur l’axe Z.
```
{"placeholder":"player_position_delta_z_fm"}
```
Sortie exemple : `0.12`

## IP actuelle du serveur (current_server_ip)
Renvoie l’IP du serveur connecté.
```
{"placeholder":"current_server_ip"}
```
Sortie exemple : `mc.hypixel.net`

## Liste des joueurs du monde (world_players_list)
Renvoie la liste de tous les joueurs actuellement dans le monde.
```
{"placeholder":"world_players_list","values":{"separator":", "}}
```
Sortie exemple : `Steve, Alex, Notch`

## MOTD du serveur (servermotd)
Renvoie le Message of the Day d’un serveur.
```
{"placeholder":"servermotd","values":{"ip":"mc.hypixel.net","line":"1"}}
```
Sortie exemple : `Welcome to Hypixel!`

## PING du serveur (serverping)
Renvoie la latence vers un serveur en millisecondes.
```
{"placeholder":"serverping","values":{"ip":"mc.hypixel.net"}}
```
Sortie exemple : `54`

## Nombre de joueurs du serveur (serverplayercount)
Renvoie le nombre de joueurs d’un serveur.
```
{"placeholder":"serverplayercount","values":{"ip":"mc.hypixel.net"}}
```
Sortie exemple : `25000/30000`

## État du serveur (serverstatus)
Renvoie l’état en ligne/hors ligne d’un serveur.
```
{"placeholder":"serverstatus","values":{"ip":"mc.hypixel.net"}}
```
Sortie exemple : `§aOnline` ou `§cOffline`

## Version du serveur (serverversion)
Renvoie la version Minecraft d’un serveur.
```
{"placeholder":"serverversion","values":{"ip":"mc.hypixel.net"}}
```
Sortie exemple : `1.19.2`

## Année (realtimeyear)
Renvoie l’année actuelle.
```
{"placeholder":"realtimeyear"}
```
Sortie exemple : `2024`

## Mois (realtimemonth)
Renvoie le mois actuel (01-12).
```
{"placeholder":"realtimemonth"}
```
Sortie exemple : `01`

## Jour (realtimeday)
Renvoie le jour du mois actuel (01-31).
```
{"placeholder":"realtimeday"}
```
Sortie exemple : `27`

## Heure (realtimehour)
Renvoie l’heure actuelle. Par défaut, le format 24 heures est utilisé ; définissez `twelve_hour_format` sur `"true"` pour un format 12 heures.
```
{"placeholder":"realtimehour","values":{"twelve_hour_format":"false","timezone":"system"}}
```
Sortie exemple : `14`

## Minute (realtimeminute)
Renvoie la minute actuelle (00-59).
```
{"placeholder":"realtimeminute"}
```
Sortie exemple : `30`

## Seconde (realtimesecond)
Renvoie la seconde actuelle (00-59).
```
{"placeholder":"realtimesecond"}
```
Sortie exemple : `45`

## Heure actuelle en millisecondes (horodatage Unix) (unix_time)
Renvoie l’horodatage Unix actuel en millisecondes.
```
{"placeholder":"unix_time"}
```
Sortie exemple : `1716552478123`

> Les espaces réservés en temps réel (`realtimeyear`, `realtimemonth`, `realtimeday`, `realtimehour`, `realtimeminute`, `realtimesecond` et `unix_time`) prennent en charge une valeur `timezone`. Utilisez des identifiants de fuseau horaire Java normaux comme `UTC`, `Europe/Berlin` ou `America/New_York` ; omettez-la ou utilisez `system` pour le fuseau horaire système.
{.is-info}

## Informations CPU (cpuinfo)
Renvoie des informations sur le processeur.
```
{"placeholder":"cpuinfo"}
```
Sortie exemple : `Intel(R) Core(TM) i7-10700K CPU @ 3.80GHz`

## Utilisation CPU (JVM) (jvmcpu)
Renvoie l’utilisation CPU de la JVM en pourcentage.
```
{"placeholder":"jvmcpu"}
```
Sortie exemple : `25.5`

## Utilisation CPU (OS) (oscpu)
Renvoie l’utilisation CPU du système d’exploitation en pourcentage.
```
{"placeholder":"oscpu"}
```
Sortie exemple : `42.8`

## Informations GPU (gpuinfo)
Renvoie des informations sur le GPU.
```
{"placeholder":"gpuinfo"}
```
Sortie exemple : `NVIDIA GeForce RTX 3080`

## Version de Java (javaver)
Renvoie la version de Java.
```
{"placeholder":"javaver"}
```
Sortie exemple : `17.0.2`

## Machine virtuelle Java (jvmname)
Renvoie le nom de la machine virtuelle Java.
```
{"placeholder":"jvmname"}
```
Sortie exemple : `OpenJDK 64-Bit Server VM`

## Version d’OpenGL (glver)
Renvoie la version d’OpenGL.
```
{"placeholder":"glver"}
```
Sortie exemple : `4.6.0 NVIDIA 516.94`

## Nom du système d’exploitation (osname)
Renvoie le nom du système d’exploitation.
```
{"placeholder":"osname"}
```
Sortie exemple : `Windows 10`

## FPS (images par seconde) (fps)
Renvoie le nombre actuel d’images par seconde.
```
{"placeholder":"fps"}
```
Sortie exemple : `120`

## RAM utilisée en Mo (usedram)
Renvoie la quantité de RAM actuellement utilisée (Mo).
```
{"placeholder":"usedram"}
```
Sortie exemple : `4096`

## RAM maximale en Mo (maxram)
Renvoie la quantité maximale de RAM allouée (Mo).
```
{"placeholder":"maxram"}
```
Sortie exemple : `8192`

## RAM utilisée en %% (percentram)
Renvoie le pourcentage de RAM actuellement utilisé.
```
{"placeholder":"percentram"}
```
Sortie exemple : `50`

## Volume d’un élément audio (audio_element_vol)
Renvoie le volume d’un élément audio.
```
{"placeholder":"audio_element_vol","values":{"element_identifier":"background_music"}}
```
Sortie exemple : `0.5`

## Piste audio actuelle (audio_element_current_track)
Renvoie le nom de la piste d’un élément audio.
```
{"placeholder":"audio_element_current_track","values":{"element_identifier":"background_music","display_name_mappings":"track1.ogg=>Cool Track Name"}}
```
Sortie exemple : `Cool Track Name`

## Durée audio (audio_duration)
Renvoie la durée totale d’une piste audio au format MM:SS.
```
{"placeholder":"audio_duration","values":{"element_identifier":"background_music"}}
```
Sortie exemple : `03:45`

## Temps de lecture audio (audio_playtime)
Renvoie le temps de lecture actuel d’une piste audio. Définissez `show_percentage` sur `"true"` pour obtenir une valeur de progression de 0 à 100 au lieu de `MM:SS`.
```
{"placeholder":"audio_playtime","values":{"element_identifier":"background_music","show_percentage":"false"}}
```
Sortie exemple : `01:30` (ou `45` quand `show_percentage` est `"true"`)

## État de lecture audio (audio_playing_state)
Renvoie si un élément audio est en lecture (true/false).
```
{"placeholder":"audio_playing_state","values":{"element_identifier":"background_music"}}
```
Sortie exemple : `true`

## Volume d’un élément vidéo (video_element_vol)
Renvoie le niveau de volume d’un élément vidéo (0.0 à 1.0).
```
{"placeholder":"video_element_vol","values":{"element_identifier":"my_video_element"}}
```
Sortie exemple : `0.5`

## Durée d’un élément vidéo (video_element_duration)
Renvoie la durée totale d’un élément vidéo au format `MM:SS`. Définissez `output_as_timestamp` sur `"true"` pour renvoyer un horodatage en millisecondes.
```
{"placeholder":"video_element_duration","values":{"element_identifier":"my_video_element","output_as_timestamp":"false"}}
```
Sortie exemple : `02:00` (ou `120000` quand `output_as_timestamp` est `"true"`)

## Temps de lecture d’un élément vidéo (video_element_playtime)
Renvoie le temps de lecture actuel (progression) d’un élément vidéo au format `MM:SS`. Définissez `show_percentage` sur `"true"` pour une valeur de progression de 0 à 100, ou `output_as_timestamp` sur `"true"` pour les millisecondes.
```
{"placeholder":"video_element_playtime","values":{"element_identifier":"my_video_element","show_percentage":"false","output_as_timestamp":"false"}}
```
Sortie exemple : `00:45` (ou `38` en pourcentage, ou `45200` en horodatage)

## État de pause d’un élément vidéo (video_element_paused_state)
Renvoie si un élément vidéo est en pause (true/false).
```
{"placeholder":"video_element_paused_state","values":{"element_identifier":"my_video_element"}}
```
Sortie exemple : `false`

## Volume d’arrière-plan vidéo (video_background_vol)
Renvoie le niveau de volume d’un arrière-plan vidéo de menu (0.0 à 1.0).
```
{"placeholder":"video_background_vol","values":{"background_identifier":"main_menu_video"}}
```
Sortie exemple : `0.7`

## Durée d’arrière-plan vidéo (video_background_duration)
Renvoie la durée totale d’un arrière-plan vidéo de menu au format `MM:SS`. Définissez `output_as_timestamp` sur `"true"` pour renvoyer un horodatage en millisecondes.
```
{"placeholder":"video_background_duration","values":{"background_identifier":"main_menu_video","output_as_timestamp":"false"}}
```
Sortie exemple : `03:00` (ou `180000` quand `output_as_timestamp` est `"true"`)

## Temps de lecture d’un arrière-plan vidéo (video_background_playtime)
Renvoie le temps de lecture actuel (progression) d’un arrière-plan vidéo de menu au format `MM:SS`. Définissez `show_percentage` sur `"true"` pour une valeur de progression de 0 à 100, ou `output_as_timestamp` sur `"true"` pour les millisecondes.
```
{"placeholder":"video_background_playtime","values":{"background_identifier":"main_menu_video","show_percentage":"false","output_as_timestamp":"false"}}
```
Sortie exemple : `01:00` (ou `33` en pourcentage, ou `60500` en horodatage)

## État de pause d’un arrière-plan vidéo (video_background_paused_state)
Renvoie si un arrière-plan vidéo de menu est en pause (true/false).
```
{"placeholder":"video_background_paused_state","values":{"background_identifier":"main_menu_video"}}
```
Sortie exemple : `true`

## Calculatrice (calc)
L’espace réservé calculatrice est un outil puissant qui vous permet d’effectuer des calculs mathématiques dans vos mises en page. Il prend en charge un large éventail d’opérations mathématiques et peut fonctionner avec des nombres décimaux et entiers.

### Syntaxe de base
```
{"placeholder":"calc","values":{"decimal":"true/false","expression":"your_expression"}}
```

La calculatrice possède deux paramètres principaux :
- `decimal` : détermine si le résultat doit inclure des décimales (`true`) ou être arrondi aux entiers (`false`)
- `expression` : l’expression mathématique à évaluer

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
Sortie exemple : `42`

## Nombre maximum (maxnum)
Renvoie le plus grand de deux nombres.
```
{"placeholder":"maxnum","values":{"first":"10","second":"20"}}
```
Sortie exemple : `20`

## Nombre minimum (minnum)
Renvoie le plus petit de deux nombres.
```
{"placeholder":"minnum","values":{"first":"10","second":"20"}}
```
Sortie exemple : `10`

## Nombre absolu (absnum)
Renvoie la valeur absolue d’un nombre.
```
{"placeholder":"absnum","values":{"num":"-10.5"}}
```
Sortie exemple : `10.5`

## Négatif d’un nombre (negnum)
Renvoie la valeur opposée d’un nombre.
```
{"placeholder":"negnum","values":{"num":"10.5"}}
```
Sortie exemple : `-10.5`

## *pi* (Math) (math_pi)
Renvoie la valeur de π.
```
{"placeholder":"math_pi"}
```
Sortie exemple : `3.141592653589793`

## Sinus trigonométrique (Math) (math_sin)
Renvoie le sinus d’un angle.
```
{"placeholder":"math_sin","values":{"angle":"45"}}
```
Sortie exemple : `0.7071067811865476`

## Cosinus trigonométrique (Math) (math_cos)
Renvoie le cosinus d’un angle.
```
{"placeholder":"math_cos","values":{"angle":"45"}}
```
Sortie exemple : `0.7071067811865476`

## Tangente trigonométrique (Math) (math_tan)
Renvoie la tangente d’un angle.
```
{"placeholder":"math_tan","values":{"angle":"45"}}
```
Sortie exemple : `1.0`

## Plancher (Math) (math_floor)
Arrondit un nombre à l’entier inférieur le plus proche.
```
{"placeholder":"math_floor","values":{"num":"3.14"}}
```
Sortie exemple : `3`

## Plafond (Math) (math_ceil)
Arrondit un nombre à l’entier supérieur le plus proche.
```
{"placeholder":"math_ceil","values":{"num":"3.14"}}
```
Sortie exemple : `4`

## Arrondi (Math) (math_round)
Arrondit un nombre. Par défaut, il arrondit à l’entier le plus proche ; définissez `decimals` sur un nombre non négatif pour arrondir à ce nombre de décimales.
```
{"placeholder":"math_round","values":{"num":"3.14159","decimals":"2"}}
```
Sortie exemple : `3.14` (avec `decimals:-1` ou si omis → `3`)

## Signe (Math) (math_sign)
Renvoie le signe d’un nombre (1 pour positif, -1 pour négatif, 0 pour zéro).
```
{"placeholder":"math_sign","values":{"num":"-3.14"}}
```
Sortie exemple : `-1`

## Sinus hyperbolique (Math) (math_sinh)
Renvoie le sinus hyperbolique d’un angle.
```
{"placeholder":"math_sinh","values":{"angle":"1"}}
```
Sortie exemple : `1.1752011936438014`

## Cosinus hyperbolique (Math) (math_cosh)
Renvoie le cosinus hyperbolique d’un angle.
```
{"placeholder":"math_cosh","values":{"angle":"1"}}
```
Sortie exemple : `1.5430806348152437`

## Tangente hyperbolique (Math) (math_tanh)
Renvoie la tangente hyperbolique d’un angle.
```
{"placeholder":"math_tanh","values":{"angle":"1"}}
```
Sortie exemple : `0.7615941559557649`

## Découper du texte (split_text)
Découpe du texte à l’aide d’un délimiteur spécifié.
```
{"placeholder":"split_text","values":{"input":"hello,world","regex":",","max_parts":"2","split_index":"1"}}
```
Sortie exemple : `world`

## Tronquer les espaces (trim_text)
Supprime les espaces blancs en début et en fin de texte.
```
{"placeholder":"trim_text","values":{"text":"  hello world  "}}
```
Sortie exemple : `hello world`

## Rogner du texte (crop_text)
Supprime des caractères au début et à la fin du texte.
```
{"placeholder":"crop_text","values":{"text":"hello world","remove_from_start":"1","remove_from_end":"1"}}
```
Sortie exemple : `ello worl`

## Chaîne littérale sécurisée (stringify)
Transforme un texte en échappant tous les caractères de syntaxe.
```
{"placeholder":"stringify","values":{"text":"text with {special} \"characters\""}}
```
Sortie exemple : `text with \{special\} \"characters\"`

## Localiser du texte (local)
Récupère le texte localisé pour une clé.
```
{"placeholder":"local","values":{"key":"menu.singleplayer"}}
```
Sortie exemple : `Singleplayer`

## Texte web (webtext)
Récupère le contenu textuel d’une URL web.
```
{"placeholder":"webtext","values":{"link":"http://somewebsite.com/textfile.txt"}}
```
Sortie exemple : contenu texte provenant de l’URL

## Texte aléatoire (randomtext)
Renvoie une ligne aléatoire depuis un fichier texte, une URL ou un texte brut direct. Le texte change à des intervalles spécifiés.
```
{"placeholder":"randomtext","values":{"source":"/config/fancymenu/assets/<file_name.txt>","interval":"10"}}
```
Paramètres :
- `source` : la source des lignes de texte (remplace l’ancien paramètre `path`)
  - Chemin de fichier : `/config/fancymenu/assets/quotes.txt`
  - URL : `https://example.com/quotes.txt`
  - Texte brut : `Line 1\nLine 2\nLine 3`
- `interval` : temps en secondes entre les changements de texte

L’espace réservé prend désormais en charge trois types de source :
1. **Fichiers locaux** : fichiers texte depuis votre dossier de jeu
   ```
   {"placeholder":"randomtext","values":{"source":"/config/fancymenu/assets/quotes.txt","interval":"10"}}
   ```
2. **URLs** : fichiers texte distants provenant d’internet
   ```
   {"placeholder":"randomtext","values":{"source":"https://example.com/quotes.txt","interval":"10"}}
   ```
3. **Texte brut** : saisie directe avec des lignes séparées par `\n`
   ```
   {"placeholder":"randomtext","values":{"source":"First line\nSecond line\nThird line","interval":"5"}}
   ```

Remarque : les anciens espaces réservés utilisant `path` au lieu de `source` continueront de fonctionner.

## Analyseur JSON (json)
Analyse des données JSON depuis un fichier, une URL ou un contenu JSON direct et extrait des valeurs à l’aide d’expressions JSON path.
```
{"placeholder":"json","values":{"source":"path_or_link_or_json_content","json_path":"$.some.json.path"}}
```
Paramètres :
- `source` : la source des données JSON
  - Chemin de fichier : `/config/fancymenu/assets/data.json`
  - URL : `https://api.example.com/data.json`
  - JSON direct : `{"name":"Steve","level":42}`
- `json_path` : l’expression JSON path utilisée pour extraire les données

L’espace réservé prend désormais en charge trois types de source :
1. **Fichiers locaux** : fichiers JSON depuis votre dossier de jeu
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

Exemples de JSON path :
- `$.name` - Récupère le champ "name" à la racine
- `$.player.level` - Récupère le champ "level" imbriqué dans "player"
- `$.items[0].id` - Récupère l’"id" du premier élément d’un tableau
- `$.scores.*` - Récupère toutes les valeurs de l’objet "scores"

## Chemin absolu de fichier/dossier (absolute_path)
Renvoie le chemin absolu d’un fichier.
```
{"placeholder":"absolute_path","values":{"short_path":"relative/path/to/file.txt"}}
```
Sortie exemple : `C:/Users/Username/AppData/Roaming/.minecraft/relative/path/to/file.txt`

## Nombre de caractères du texte (text_character_count)
Renvoie le nombre de caractères du texte fourni.
```
{"placeholder":"text_character_count","values":{"text":"Hello World!"}}
```
Sortie exemple : `12`

## Largeur du texte (text_width)
Renvoie la largeur en pixels du texte fourni lorsqu’il est rendu.
```
{"placeholder":"text_width","values":{"text":"Hello World!"}}
```
Sortie exemple : `66`

## Texte en majuscules (uppercase_text)
Convertit le texte d’entrée en lettres majuscules.
```
{"placeholder":"uppercase_text","values":{"text":"Hello World"}}
```
Sortie exemple : `HELLO WORLD`

## Texte en minuscules (lowercase_text)
Convertit le texte d’entrée en lettres minuscules.
```
{"placeholder":"lowercase_text","values":{"text":"Hello World"}}
```
Sortie exemple : `hello world`

## Texte en capitales initiales (title_case_text)
Convertit le texte d’entrée en casse de titre.
```
{"placeholder":"title_case_text","values":{"text":"hello world"}}
```
Sortie exemple : `Hello World`

## Texte en casse de phrase (sentence_case_text)
Convertit le texte d’entrée en casse de phrase.
```
{"placeholder":"sentence_case_text","values":{"text":"hello world. this is fancymenu!"}}
```
Sortie exemple : `Hello world. This is fancymenu!`

## Texte en snake_case (snake_case_text)
Convertit le texte d’entrée en `snake_case`.
```
{"placeholder":"snake_case_text","values":{"text":"Hello World"}}
```
Sortie exemple : `hello_world`

## Texte en kebab-case (kebab_case_text)
Convertit le texte d’entrée en `kebab-case`.
```
{"placeholder":"kebab_case_text","values":{"text":"Hello World"}}
```
Sortie exemple : `hello-world`

## Texte en casse alternée (alternating_case_text)
Convertit le texte d’entrée en casse alternée.
```
{"placeholder":"alternating_case_text","values":{"text":"alternating case"}}
```
Sortie exemple : `aLtErNaTiNg CaSe`

## Inverser la casse (toggle_case_text)
Inverse la casse de chaque lettre du texte d’entrée.
```
{"placeholder":"toggle_case_text","values":{"text":"Toggle Case"}}
```
Sortie exemple : `tOGGLE cASE`

## Encoder en Base64 (base64_encode)
Encode le texte fourni en Base64.
```
{"placeholder":"base64_encode","values":{"text":"Hello World"}}
```
Sortie exemple : `SGVsbG8gV29ybGQ=`

## Décoder depuis Base64 (base64_decode)
Décode une chaîne Base64 en texte brut.
```
{"placeholder":"base64_decode","values":{"text":"SGVsbG8gV29ybGQ="}}
```
Sortie exemple : `Hello World`

## Texte d’un fichier (file_text)
Renvoie les lignes de texte d’un fichier ou d’une URL. Peut renvoyer toutes les lignes ou seulement les X dernières lignes.
```
{"placeholder":"file_text","values":{"path_or_url":"/config/fancymenu/assets/some_file.txt","mode":"all","separator":"\n","last_lines":"1"}}
```
Paramètres :
- `path_or_url` : chemin de fichier ou URL à lire
- `mode` : soit `"all"` (renvoie toutes les lignes) soit `"last"` (renvoie seulement les X dernières lignes)
- `separator` : texte utilisé pour joindre les lignes (par défaut : `"\n"`)
- `last_lines` : nombre de lignes à renvoyer quand `mode` est `"last"` (par défaut : `"1"`)

Sortie exemple : dépend du contenu du fichier

## Contenu du presse-papiers (clipboard_content)
Renvoie le texte actuellement stocké dans le presse-papiers du système.
```
{"placeholder":"clipboard_content"}
```
Sortie exemple : le texte actuellement dans le presse-papiers

## Remplacer du texte (replace_text)
Remplace du texte dans une chaîne à l’aide de texte littéral ou d’expressions régulières.
```
{"placeholder":"replace_text","values":{"text":"Hello World! This is a test.","search":"World","replacement":"FancyMenu","use_regex":"false","replace_all":"true"}}
```
Paramètres :
- `text` : le texte d’entrée à traiter
- `search` : le texte ou motif regex à rechercher
- `replacement` : le texte de remplacement
- `use_regex` : utiliser une expression régulière (`"true"`) ou une correspondance littérale (`"false"`)
- `replace_all` : remplacer toutes les occurrences (`"true"`) ou seulement la première (`"false"`)

Sortie exemple : `Hello FancyMenu! This is a test.`

## Switch case (switch_case)
Effectue une opération switch-case en fonction d’une valeur.
```
{"placeholder":"switch_case","values":{"value":"1","cases":"1:first case,2:second case,3:third case","default":"default case"}}
```
Sortie exemple : `first case` (si la valeur est 1)

## Obtenir la valeur d’une variable (variable FM) (getvariable)
Récupère la valeur d’une variable enregistrée précédemment.
```
{"placeholder":"getvariable","values":{"name":"some_variable"}}
```
Sortie exemple : dépend de la valeur stockée

## Obtenir des données NBT (nbt_data_get)
Récupère des données NBT côté client (similaire à la commande `/data get`). Utilisez la variante serveur `nbt_data_get_server` lorsque vous êtes connecté à un serveur et que vous avez besoin de valeurs faisant autorité côté serveur.
```
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"foodLevel","scale":"1.0","return_type":"value"}}
```
Paramètres :
- `source_type` : soit `"entity"` soit `"block"`
- `entity_selector` : sélecteur d’entité comme `@s`, `@p`, `@e`, ou UUID/nom (pour les entités)
- `block_pos` : position du bloc au format `"x y z"` (pour les blocs)
- `nbt_path` : le chemin NBT à récupérer
- `scale` : facteur d’échelle optionnel pour les valeurs numériques (par défaut : `"1.0"`)
- `return_type` : manière de renvoyer les données :
  - `"value"` : par défaut, renvoie la valeur (avec mise à l’échelle optionnelle pour les nombres)
  - `"string"` : renvoie les données NBT réelles sous forme de chaîne
  - `"snbt"` : renvoie en SNBT (NBT formaté)
  - `"json"` : renvoie sous forme de composant au format JSON (pour les balises composées)

Sortie exemple : `20` (pour le niveau de faim)

## Obtenir des données NBT (côté serveur) (nbt_data_get_server)
Interroge les données NBT côté serveur (via un paquet) et met brièvement les résultats en cache. Les valeurs correspondent à l’espace réservé côté client.
```
{"placeholder":"nbt_data_get_server","values":{"source_type":"entity","entity_selector":"@s","block_pos":"","storage_id":"minecraft:storage_key","nbt_path":"SelectedItem.id","scale":"1.0","return_type":"value"}}
```
Sortie exemple : `minecraft:diamond_sword`

## Dernier message de mort (lastdeathmessage)
Renvoie le dernier message de mort enregistré du joueur client. Définissez `as_json_component` sur `"true"` pour obtenir le composant texte JSON brut.
```
{"placeholder":"lastdeathmessage","values":{"as_json_component":"false"}}
```
Sortie exemple : `Steve was slain by Zombie`

## Durée de fonctionnement (uptime_duration)
Renvoie depuis combien de temps FancyMenu est chargé. Par défaut, la valeur est en secondes ; définissez `output_as_millis` sur `"true"` pour obtenir les millisecondes.
```
{"placeholder":"uptime_duration","values":{"output_as_millis":"false"}}
```
Sortie exemple : `742` (secondes depuis le chargement)

## Noms des sauvegardes du monde (level_save_names)
Liste tous les noms locaux de sauvegardes du monde, joints par le séparateur choisi. S’exécute dans le thread client.
```
{"placeholder":"level_save_names","values":{"separator":", "}}
```
Sortie exemple : `Creative Test, Survival World, Hardcore`

## Données de sauvegarde du monde (level_save_data)
Renvoie les données sérialisées du niveau pour le nom de monde donné (doit correspondre au nom affiché dans la liste des sauvegardes).
```
{"placeholder":"level_save_data","values":{"level_name":"Survival World"}}
```
Sortie exemple : `{"name":"Survival World","gameMode":"survival",...}`

## Convertisseur de base numérique (number_base_convert)
Convertit un nombre (entier ou fractionnaire) d’une base vers une autre (2–36). La base décimale est utilisée par défaut si aucune base n’est fournie.
```
{"placeholder":"number_base_convert","values":{"input":"67.5","from_base":"10","to_base":"16"}}
```
Sortie exemple : `43.8`

## Taille du fichier (file_size)
Renvoie la taille d’un fichier local en octets. Seuls les chemins locaux sont autorisés.
```
{"placeholder":"file_size","values":{"path":"/config/fancymenu/assets/notes.txt"}}
```
Sortie exemple : `1284`

## MD5 du fichier (file_md5)
Renvoie le hachage MD5 d’un fichier local sous forme de chaîne hexadécimale en minuscules.
```
{"placeholder":"file_md5","values":{"path":"/config/fancymenu/assets/notes.txt"}}
```
Sortie exemple : `d41d8cd98f00b204e9800998ecf8427e`

# Exemples pratiques

## Créer un affichage dynamique de la mémoire
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

## HUD de statut du joueur
```
Santé : {"placeholder":"current_player_health"} / {"placeholder":"max_player_health"} ({"placeholder":"current_player_health_percent"}%)
Armure : {"placeholder":"current_player_armor"} / {"placeholder":"max_player_armor"}
Niveau XP : {"placeholder":"current_player_level"}
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

1. **Mettre en cache les opérations coûteuses** : certains espaces réservés (comme ceux qui lisent des informations système) peuvent consommer beaucoup de ressources. Pensez à utiliser des variables pour stocker leurs valeurs si vous devez les utiliser plusieurs fois.

2. **Utiliser les bons réglages de décimales** : lors des calculs, utilisez le paramètre `decimal` de manière appropriée. Mettez-le à `false` quand vous avez besoin d’entiers, et à `true` quand vous avez besoin de valeurs décimales précises.

3. **Gérer les valeurs manquantes** : réfléchissez toujours à ce qu’il faut faire si un espace réservé ne renvoie aucune valeur. Vous voudrez peut-être fournir des valeurs par défaut dans ces cas-là.

4. **Tester les performances** : lorsque vous utilisez de nombreux espaces réservés ou des structures imbriquées complexes, testez l’impact sur les performances, surtout sur des systèmes moins puissants.

5. **Utiliser un dimensionnement et un positionnement avancés** : pour les éléments d’interface dynamiques, combinez les espaces réservés avec le dimensionnement et le positionnement avancés afin de créer des mises en page réactives.

6. **Combiner avec des variables** : utilisez les espaces réservés avec des variables pour un contenu encore plus dynamique pouvant être mis à jour via des actions.

# Problèmes courants et solutions

## L’espace réservé ne se met pas à jour
Si la valeur d’un espace réservé ne se met pas à jour comme prévu, vérifiez :
- si l’espace réservé est correctement formaté
- si vous utilisez la bonne casse pour les identifiants d’espaces réservés
- si l’espace réservé nécessite des conditions particulières pour se mettre à jour

## Les espaces réservés imbriqués ne fonctionnent pas
Lors de l’imbrication d’espaces réservés :
- assurez-vous que les guillemets sont correctement échappés
- vérifiez que chaque espace réservé imbriqué est valide indépendamment

## Problèmes de performances
Si vous remarquez des problèmes de performances :
- réduisez le nombre d’espaces réservés utilisés
- évitez les imbrications inutiles
- envisagez d’utiliser des variables pour les valeurs fréquemment consultées
- utilisez l’espace réservé adapté à vos besoins (par exemple, n’utilisez pas des espaces réservés en temps réel quand des valeurs statiques suffisent)
