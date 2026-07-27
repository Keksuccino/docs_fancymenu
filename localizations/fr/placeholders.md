---
title: Substitutions
description: Comment utiliser les substitutions.
---
# Substitutions

Les substitutions insèrent des valeurs en direct dans du texte, des boutons, des conditions et d'autres champs pris en charge.

# Informations générales

## Syntaxe de base
Les substitutions dans FancyMenu utilisent une syntaxe proche de JSON :
```
{"placeholder":"modversion","values":{"modid":"fancymenu"}}
```

Par exemple, pour afficher le nom du joueur :
```
{"placeholder":"playername"}
```

## Imbriquer des substitutions
Vous pouvez utiliser une substitution à l'intérieur de la valeur d'une autre substitution.

Exemple de substitutions imbriquées :
```
{"placeholder":"calc","values":{"decimal":"true","expression":"{"placeholder":"maxram"} / 1024"}}
```
Cet exemple prend la valeur de la RAM maximale et la divise par 1024 pour la convertir de Mo en Go.

> [!IMPORTANT]
> Il s'agit de la syntaxe FancyMenu, pas de JSON. Les substitutions imbriquées utilisent exactement la forme non échappée affichée ci-dessus, donc les formateurs JSON les rejetteront ou les réécriront. Les noms des substitutions sont sensibles à la casse ; les substitutions mal formées ou inconnues restent visibles en tant que texte et sont consignées.

# Utilisation des substitutions

La plupart des éléments qui comportent des champs de texte prennent en charge les substitutions. Vous pouvez voir si un champ de texte les prend en charge lors de son édition. Si l'**éditeur de texte** plein écran s'ouvre lorsque vous modifiez le texte, cela signifie qu'il prend en charge les substitutions. 

Pour trouver une **liste de toutes les substitutions**, cliquez simplement sur le bouton **Substitutions** dans le **coin supérieur droit** de l'**éditeur de texte**.

Une **barre de recherche** se trouve en haut de la liste des substitutions et vous permet de rechercher des substitutions.

Cliquer sur une substitution dans la liste la collera dans le contenu du texte.

# Substitutions en détail

Cette section répertorie les substitutions intégrées de FancyMenu.

## Résultats indisponibles

La sortie d'une substitution est toujours du texte. Lorsque des données ne sont pas disponibles, le résultat dépend de la substitution : les valeurs de repli courantes sont une chaîne vide, `0`, `0.0`, `00:00`, `false`, `UNKNOWN` ou `ERROR`. Les entrées avec un état de repli spécifique l'indiquent directement ; testez le repli avant d'utiliser une sortie dépendante de l'environnement dans une [condition](./conditions), un chemin, une commande ou une URL.

## Nom du joueur (`playername`)

**But :** Renvoie le nom d'utilisateur du joueur actuel.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"playername"}
```

**Sortie :** `Steve`

## UUID du joueur (`playeruuid`)

**But :** Renvoie l'identifiant unique du joueur.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"playeruuid"}
```

**Sortie :** `c8cde7fe-7ced-11eb-9439-0242ac130002`

## Version de Minecraft (`mcversion`)

**But :** Renvoie la version actuelle de Minecraft.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"mcversion"}
```

**Sortie :** `1.21.1`

## Version du chargeur de mods (`loaderver`)

**But :** Renvoie la version du chargeur de mods (Fabric/NeoForge).

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"loaderver"}
```

**Sortie :** `0.16.14`

## Nom du chargeur de mods (`loadername`)

**But :** Renvoie le nom du chargeur de mods.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"loadername"}
```

**Sortie :** `Fabric`

## Version du mod (`modversion`)

**But :** Renvoie la version d'un mod spécifique.

**Valeurs :** `modid`

**Exemple :**

```
{"placeholder":"modversion","values":{"modid":"example_mod"}}
```

**Sortie :** `1.2.3`

## Nombre total de mods (`totalmods`)

**But :** Renvoie un nombre approximatif de fichiers de mods, basé sur le dossier `mods` et le nombre de mods chargés. Ne compte pas de manière fiable tous les mods désactivés.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"totalmods"}
```

**Sortie :** `45`

## Nombre de mods actifs (`loadedmods`)

**But :** Renvoie le nombre de mods actuellement chargés.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"loadedmods"}
```

**Sortie :** `43`

## Progression de chargement du monde (`world_load_progress`)

**But :** Renvoie la progression actuelle du chargement du monde en pourcentage.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"world_load_progress"}
```

**Sortie :** `75`

## Valeur d'une option Minecraft (`minecraft_option_value`)

**But :** Renvoie la valeur d'une option Minecraft.

**Valeurs :** `name`

**Exemple :**

```
{"placeholder":"minecraft_option_value","values":{"name":"fov"}}
```

**Sortie :** `70`

## Dernier monde ou serveur (`last_world_server`)

**But :** Renvoie des informations sur le dernier monde ou serveur consulté.

**Valeurs :** `type`, `full_world_path`

**Exemple :**

```
{"placeholder":"last_world_server","values":{"type":"both","full_world_path":"true"}}
```
Paramètres :
- `type` : Détermine quel type d'information renvoyer
  - `"both"` : Renvoie le dernier monde ou serveur consulté (par défaut)
  - `"server"` : Renvoie uniquement si le dernier élément consulté était un serveur
  - `"world"` : Renvoie uniquement si le dernier élément consulté était un monde
- `full_world_path` : Contrôle l'affichage des chemins des mondes
  - `"true"` : Renvoie le chemin complet du monde (par défaut)
  - `"false"` : Renvoie uniquement le nom du monde sans le chemin (n'affecte pas les serveurs)

Exemples :
- Serveur : `mc.hypixel.net`
- Monde avec chemin complet : `saves/New World`
- Monde sans chemin complet : `New World`

## Largeur de l'écran (`guiwidth`)

**But :** Renvoie la largeur actuelle de l'écran en pixels à l'échelle de l'interface, et non en pixels physiques du moniteur.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"guiwidth"}
```

**Sortie :** `960`

## Hauteur de l'écran (`guiheight`)

**But :** Renvoie la hauteur actuelle de l'écran en pixels à l'échelle de l'interface, et non en pixels physiques du moniteur.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"guiheight"}
```

**Sortie :** `540`

## Identifiant de l'écran actuel (`screenid`)

**But :** Renvoie l'identifiant de l'écran actuel.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"screenid"}
```

**Sortie :** `title_screen`

## Largeur d'un élément (`elementwidth`)

**But :** Renvoie la largeur d'un élément spécifique.

**Valeurs :** `id`

**Exemple :**

```
{"placeholder":"elementwidth","values":{"id":"my_button"}}
```

**Sortie :** `200`

## Hauteur d'un élément (`elementheight`)

**But :** Renvoie la hauteur d'un élément spécifique.

**Valeurs :** `id`

**Exemple :**

```
{"placeholder":"elementheight","values":{"id":"my_button"}}
```

**Sortie :** `20`

## Position X d'un élément (`elementposx`)

**But :** Renvoie la position X d'un élément spécifique.

**Valeurs :** `id`

**Exemple :**

```
{"placeholder":"elementposx","values":{"id":"my_button"}}
```

**Sortie :** `150`

## Position Y d'un élément (`elementposy`)

**But :** Renvoie la position Y d'un élément spécifique.

**Valeurs :** `id`

**Exemple :**

```
{"placeholder":"elementposy","values":{"id":"my_button"}}
```

**Sortie :** `100`

## Position X de la souris (`mouseposx`)

**But :** Renvoie la position X actuelle de la souris.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"mouseposx"}
```

**Sortie :** `960`

## Position Y de la souris (`mouseposy`)

**But :** Renvoie la position Y actuelle de la souris.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"mouseposy"}
```

**Sortie :** `540`

## Clics par seconde (`clicks_per_second`)

**But :** Renvoie le nombre actuel de clics par seconde pour un bouton de souris.

**Valeurs :** `mouse_button`

**Exemple :**

```
{"placeholder":"clicks_per_second","values":{"mouse_button":"left"}}
```
Paramètres :
- `mouse_button` : `left` ou `right`

**Sortie :** `8`

## Échelle de l'interface (`guiscale`)

**But :** Renvoie l'échelle actuelle de l'interface.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"guiscale"}
```

**Sortie :** `2`

## Libellé/texte d'un widget/bouton vanilla (`vanillabuttonlabel`)

**But :** Renvoie le libellé/le texte d'un widget/bouton vanilla.

**Valeurs :** `locator`

**Exemple :**

```
{"placeholder":"vanillabuttonlabel","values":{"locator":"some.menu.identifier:505280"}}
```

**Sortie :** `Options...`

## Valeur d'un champ de saisie (`text_input_field_value`)

**But :** Renvoie la valeur actuelle d'un champ de saisie personnalisé ou vanilla à l'aide de son identifiant d'élément.

**Valeurs :** `element_identifier`

**Exemple :**

```
{"placeholder":"text_input_field_value","values":{"element_identifier":"my_input"}}
```

**Sortie :** `Hello World`

## Santé actuelle du joueur (`current_player_health`)

**But :** Renvoie les points de vie actuels du joueur.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"current_player_health"}
```

**Sortie :** `20.0`

## Santé maximale du joueur (`max_player_health`)

**But :** Renvoie les points de vie maximum du joueur.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"max_player_health"}
```

**Sortie :** `20.0`

## Santé actuelle du joueur (pourcentage) (`current_player_health_percent`)

**But :** Renvoie la santé du joueur en pourcentage.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"current_player_health_percent"}
```

**Sortie :** `100`

## Santé d'absorption actuelle du joueur (`current_player_absorption_health`)

**But :** Renvoie les points de vie d'absorption du joueur (cœurs dorés).

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"current_player_absorption_health"}
```

**Sortie :** `4.0`

## Santé d'absorption maximale du joueur (`max_player_absorption_health`)

**But :** Renvoie la santé d'absorption maximale.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"max_player_absorption_health"}
```

**Sortie :** `4.0`

## Santé d'absorption actuelle du joueur (pourcentage) (`current_player_absorption_health_percent`)

**But :** Renvoie la santé d'absorption du joueur en pourcentage.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"current_player_absorption_health_percent"}
```

**Sortie :** `100`

## Niveau de faim actuel du joueur (`current_player_hunger`)

**But :** Renvoie le niveau de faim actuel du joueur.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"current_player_hunger"}
```

**Sortie :** `20`

## Niveau de faim maximal du joueur (`max_player_hunger`)

**But :** Renvoie le niveau de faim maximal.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"max_player_hunger"}
```

**Sortie :** `20`

## Niveau de faim actuel du joueur (pourcentage) (`current_player_hunger_percent`)

**But :** Renvoie la faim du joueur en pourcentage.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"current_player_hunger_percent"}
```

**Sortie :** `100`

## Saturation de faim actuelle du joueur (`current_player_hunger_saturation`)

**But :** Renvoie la valeur actuelle de saturation de faim du joueur.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"current_player_hunger_saturation"}
```

**Sortie :** `5.0`

## Armure actuelle du joueur (`current_player_armor`)

**But :** Renvoie la valeur actuelle d'armure du joueur.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"current_player_armor"}
```

**Sortie :** `20`

## Robustesse d'armure du joueur (`player_armor_toughness`)

**But :** Renvoie la valeur totale de robustesse d'armure du joueur.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"player_armor_toughness"}
```

**Sortie :** `8.0`

## Armure maximale du joueur (`max_player_armor`)

**But :** Renvoie la valeur maximale d'armure.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"max_player_armor"}
```

**Sortie :** `20`

## Armure actuelle du joueur (pourcentage) (`current_player_armor_percent`)

**But :** Renvoie l'armure du joueur en pourcentage.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"current_player_armor_percent"}
```

**Sortie :** `100`

## Niveau d'oxygène actuel du joueur (`current_player_oxygen`)

**But :** Renvoie le niveau d'oxygène actuel du joueur (bulles d'air).

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"current_player_oxygen"}
```

**Sortie :** `300`

## Niveau d'oxygène maximal du joueur (`max_player_oxygen`)

**But :** Renvoie le niveau d'oxygène maximal.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"max_player_oxygen"}
```

**Sortie :** `300`

## Niveau d'oxygène actuel du joueur (pourcentage) (`current_player_oxygen_percent`)

**But :** Renvoie le niveau d'oxygène du joueur en pourcentage.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"current_player_oxygen_percent"}
```

**Sortie :** `100`

## Niveau actuel du joueur (`current_player_level`)

**But :** Renvoie le niveau d'expérience actuel du joueur.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"current_player_level"}
```

**Sortie :** `30`

## Expérience actuelle du joueur (`current_player_exp`)

**But :** Renvoie les points d'expérience totaux du joueur.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"current_player_exp"}
```

**Sortie :** `1250`

## Progression d'expérience du joueur (pourcentage) (`current_player_exp_progress`)

**But :** Renvoie la progression d'expérience du joueur vers le niveau suivant en pourcentage.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"current_player_exp_progress"}
```

**Sortie :** `75`

## Force d'attaque du joueur (pourcentage) (`player_attack_strength`)

**But :** Renvoie le temps de recharge de l'attaque du joueur en pourcentage.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"player_attack_strength"}
```

**Sortie :** `100`

## Mode de jeu du joueur (`player_gamemode`)

**But :** Renvoie le mode de jeu actuel du joueur.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"player_gamemode"}
```

**Sortie :** `survival`

## Direction du regard du joueur (`player_view_direction`)

**But :** Renvoie la direction vers laquelle le joueur est orienté.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"player_view_direction"}
```

**Sortie :** `north`

## Coordonnée X du joueur (`player_x_coordinate`)

**But :** Renvoie la position X du joueur dans le monde.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"player_x_coordinate"}
```

**Sortie :** `125`

## Coordonnée Y du joueur (`player_y_coordinate`)

**But :** Renvoie la position Y du joueur dans le monde.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"player_y_coordinate"}
```

**Sortie :** `64`

## Coordonnée Z du joueur (`player_z_coordinate`)

**But :** Renvoie la position Z du joueur dans le monde.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"player_z_coordinate"}
```

**Sortie :** `-250`

## Santé actuelle de la monture (`current_mount_health`)

**But :** Renvoie la santé actuelle de l'entité que le joueur monte.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"current_mount_health"}
```

**Sortie :** `30.0`

## Santé maximale de la monture (`max_mount_health`)

**But :** Renvoie la santé maximale de l'entité que le joueur monte.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"max_mount_health"}
```

**Sortie :** `30.0`

## Santé actuelle de la monture (pourcentage) (`current_mount_health_percent`)

**But :** Renvoie la santé de la monture en pourcentage.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"current_mount_health_percent"}
```

**Sortie :** `100`

## Jauge de saut actuelle de la monture (pourcentage) (`current_mount_jump_meter`)

**But :** Renvoie la valeur de la jauge de puissance de saut de la monture.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"current_mount_jump_meter"}
```

**Sortie :** `75`

## Santé actuelle du boss (pourcentage) (`current_boss_health`)

**But :** Renvoie la santé d'un boss actif sélectionné sous forme de pourcentage entier de `0` à `100`. `boss_index` commence à zéro ; `0` sélectionne la première barre de boss.

**Valeurs :** `boss_index`

**Exemple :**

```
{"placeholder":"current_boss_health","values":{"boss_index":"0"}}
```

**Sortie :** `75`

## Nom du boss (`boss_name`)

**But :** Renvoie le nom du boss actif.

**Valeurs :** `boss_index`, `as_json`

**Exemple :**

```
{"placeholder":"boss_name","values":{"boss_index":"0","as_json":"false"}}
```

**Sortie :** `Ender Dragon`

## Nombre de boss (`boss_count`)

**But :** Renvoie le nombre de boss actifs.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"boss_count"}
```

**Sortie :** `1`

## Nombre d'effets actifs (`effects_count`)

**But :** Renvoie le nombre d'effets de potion actifs.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"effects_count"}
```

**Sortie :** `3`

## Effet actif (`active_effect`)

**But :** Renvoie des informations sur un effet actif spécifique.

**Valeurs :** `effect_index`

**Exemple :**

```
{"placeholder":"active_effect","values":{"effect_index":"0"}}
```

**Sortie :** `minecraft:speed`

## Emplacement de la barre rapide sélectionné (`active_hotbar_slot`)

**But :** Renvoie l'emplacement actuellement sélectionné dans la barre rapide (0-8).

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"active_hotbar_slot"}
```

**Sortie :** `4`

## Objet d'un emplacement (`slot_item`)

**But :** Renvoie des informations sur un objet dans un emplacement d'inventaire spécifique.

**Valeurs :** `slot`

**Exemple :**

```
{"placeholder":"slot_item","values":{"slot":"0"}}
```

**Sortie :** `minecraft:diamond_sword`

## Quantité d'objets dans l'emplacement (`slot_item_count`)

**But :** Renvoie la taille de la pile d'objets dans un emplacement spécifique de l'inventaire du joueur.

**Valeurs :** `slot`

**Exemple :**

```
{"placeholder":"slot_item_count","values":{"slot":"0"}}
```

**Sortie :** `64`

## Durabilité de l'objet dans l'emplacement (`slot_item_durability`)

**But :** Renvoie les informations de durabilité de l'objet dans un emplacement spécifique de l'inventaire du joueur.

**Valeurs :** `slot`, `format`

**Exemple :**

```
{"placeholder":"slot_item_durability","values":{"slot":"0","format":"percentage"}}
```
Paramètres :
- `slot` : Numéro de l'emplacement dans l'inventaire du joueur.
- `format` : `current`, `remaining`, `max`, `damage`, `percentage` ou `percent`.

**Sortie :** `87`

## Nom affiché de l'objet d'un emplacement (`slot_item_display_name_fm`)

**But :** Renvoie le nom affiché de l'objet dans un emplacement spécifique sous forme de composant texte JSON. En mode spectateur, les emplacements de la barre rapide peuvent résoudre les noms d'objets du menu spectateur, sauf si `ignore_spectator` est `true`.

**Valeurs :** `slot`, `ignore_spectator`

**Exemple :**

```
{"placeholder":"slot_item_display_name_fm","values":{"slot":"0","ignore_spectator":"false"}}
```

**Sortie :** `{"text":"Diamond Sword","color":"aqua"}`

## Nombre d'objets dans l'inventaire (`inventory_item_count`)

**But :** Renvoie le nombre total d'objets correspondants dans l'inventaire du joueur. Lorsque `item` est vide, additionne les tailles de pile de tous les emplacements d'inventaire occupés.

**Valeurs :** `item`

**Exemple :**

```
{"placeholder":"inventory_item_count","values":{"item":"minecraft:diamond"}}
```

**Sortie :** `12`

## Quantité de nourriture restaurée par l'emplacement de l'inventaire (`inventory_slot_food_point_restore_amount`)

**But :** Renvoie les points de faim restaurés par l'objet alimentaire dans l'emplacement d'inventaire du joueur donné.

**Valeurs :** `slot`

**Exemple :**

```
{"placeholder":"inventory_slot_food_point_restore_amount","values":{"slot":"0"}}
```

**Sortie :** `4.0`

## Objet d'inventaire survolé (`hovered_inventory_item`)

**But :** Renvoie la clé de l'objet actuellement survolé dans un écran d'inventaire.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"hovered_inventory_item"}
```

**Sortie :** `minecraft:apple`

## Temps de jeu du monde (`game_time`)

**But :** Renvoie le compteur actuel de ticks du temps en jeu.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"game_time"}
```

**Sortie :** `18000`

## Heure du monde (`world_daytime`)

**But :** Renvoie l'heure actuelle du monde.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"world_daytime"}
```

**Sortie :** `13000`

## Heure du monde en heures (`world_daytime_hour`)

**But :** Renvoie le composant heure du temps du monde. Par défaut, le format 24 heures est utilisé ; définissez `twelve_hour_format` sur `"true"` pour le format 12 heures.

**Valeurs :** `twelve_hour_format`

**Exemple :**

```
{"placeholder":"world_daytime_hour","values":{"twelve_hour_format":"false"}}
```

**Sortie :** `12`

## Minute du monde (`world_daytime_minute`)

**But :** Renvoie le composant minute du temps du monde (00-59).

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"world_daytime_minute"}
```

**Sortie :** `30`

## Difficulté du monde (`world_difficulty`)

**But :** Renvoie la difficulté actuelle du monde.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"world_difficulty"}
```

**Sortie :** `normal`

## Seed du monde actuel (`current_world_seed`)

**But :** Renvoie la seed du monde solo actuel. Renvoie une valeur vide lorsque la seed n'est pas disponible.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"current_world_seed"}
```

**Sortie :** `123456789`

## Biome actuel (`current_biome`)

**But :** Renvoie le biome dans lequel se trouve actuellement le joueur. Définissez `as_key` sur `"false"` pour renvoyer un nom traduit/affiché lorsqu'il est disponible.

**Valeurs :** `as_key`

**Exemple :**

```
{"placeholder":"current_biome","values":{"as_key":"true"}}
```

**Sortie :** `minecraft:plains`

## Dimension actuelle (`current_dimension`)

**But :** Renvoie la dimension dans laquelle se trouve actuellement le joueur. Définissez `as_key` sur `"false"` pour renvoyer un nom traduit/affiché lorsqu'il est disponible.

**Valeurs :** `as_key`

**Exemple :**

```
{"placeholder":"current_dimension","values":{"as_key":"true"}}
```

**Sortie :** `minecraft:overworld`

## Valeur d'une règle de jeu (`gamerule_value`)

**But :** Renvoie la valeur actuelle d'une règle de jeu dans le monde/serveur chargé. Les mondes serveur nécessitent FancyMenu sur le serveur.

**Valeurs :** `name`

**Exemple :**

```
{"placeholder":"gamerule_value","values":{"name":"doDaylightCycle"}}
```

**Sortie :** `true`

## Catégorie d'objet (`item_category`)

**But :** Renvoie l'onglet créatif auquel appartient un objet. Définissez `as_key` sur `"true"` pour renvoyer la clé de la catégorie au lieu du nom affiché.

**Valeurs :** `item`, `as_key`

**Exemple :**

```
{"placeholder":"item_category","values":{"item":"minecraft:diamond_sword","as_key":"false"}}
```

**Sortie :** `Combat`

## Titre/sous-titre HUD actuel (`current_title`)

**But :** Renvoie le texte du titre actuellement affiché.

**Valeurs :** `is_subtitle`, `as_json`

**Exemple :**

```
{"placeholder":"current_title","values":{"is_subtitle":"false","as_json":"false"}}
```

**Sortie :** `Game Over!`

## Message de la barre d'action (`action_bar_message_fm`)

**But :** Renvoie le message actuel de la barre d'action vanilla sous forme de composant texte Minecraft sérialisé.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"action_bar_message_fm"}
```

**Sortie :** `{"text":"You may not rest now","color":"red"}`

## Durée du message de la barre d'action (`action_bar_message_time_fm`)

**But :** Indique pendant combien de ticks le message actuel de la barre d'action vanilla sera encore affiché.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"action_bar_message_time_fm"}
```

**Sortie :** `42`

## Rotation X de la caméra (`camera_rotation_x_fm`)

**But :** Renvoie l'inclinaison actuelle de la caméra en degrés.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"camera_rotation_x_fm"}
```

**Sortie :** `12.5`

## Rotation Y de la caméra (`camera_rotation_y_fm`)

**But :** Renvoie le yaw actuel de la caméra en degrés.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"camera_rotation_y_fm"}
```

**Sortie :** `-90.0`

## Variation X de la rotation de la caméra (`camera_rotation_delta_x_fm`)

**But :** Renvoie la variation de l'inclinaison de la caméra à chaque tick.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"camera_rotation_delta_x_fm"}
```

**Sortie :** `0.4`

## Variation Y de la rotation de la caméra (`camera_rotation_delta_y_fm`)

**But :** Renvoie la variation du yaw de la caméra à chaque tick.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"camera_rotation_delta_y_fm"}
```

**Sortie :** `-1.2`

## Durée d'affichage de l'objet mis en surbrillance (`highlighted_item_time_fm`)

**But :** Indique pendant combien de ticks le nom de l'objet mis en surbrillance sera encore affiché au-dessus de la barre rapide.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"highlighted_item_time_fm"}
```

**Sortie :** `30`

## Progression d'utilisation de l'objet par le joueur (`player_item_use_progress_fm`)

**But :** Renvoie la progression actuelle d'utilisation de l'objet, de `0.0` à `1.0`.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"player_item_use_progress_fm"}
```

**Sortie :** `0.65`

## Variation X de la position du joueur (`player_position_delta_x_fm`)

**But :** Renvoie la variation de la position du joueur à chaque tick sur l'axe X.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"player_position_delta_x_fm"}
```

**Sortie :** `0.0`

## Variation Y de la position du joueur (`player_position_delta_y_fm`)

**But :** Renvoie la variation de la position du joueur à chaque tick sur l'axe Y.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"player_position_delta_y_fm"}
```

**Sortie :** `-0.08`

## Variation Z de la position du joueur (`player_position_delta_z_fm`)

**But :** Renvoie la variation de la position du joueur à chaque tick sur l'axe Z.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"player_position_delta_z_fm"}
```

**Sortie :** `0.12`

## IP actuelle du serveur (`current_server_ip`)

**But :** Renvoie l'adresse IP du serveur connecté.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"current_server_ip"}
```

**Sortie :** `mc.hypixel.net`

## Liste des joueurs du monde (`world_players_list`)

**But :** Renvoie une liste de tous les joueurs actuellement présents dans le monde.

**Valeurs :** `separator`

**Exemple :**

```
{"placeholder":"world_players_list","values":{"separator":", "}}
```

**Sortie :** `Steve, Alex, Notch`

## MOTD du serveur (`servermotd`)

**But :** Renvoie le message du jour d'un serveur.

**Valeurs :** `ip`, `line`

**Exemple :**

```
{"placeholder":"servermotd","values":{"ip":"mc.hypixel.net","line":"1"}}
```

**Sortie :** `Welcome to Hypixel!`

## Ping du serveur (`serverping`)

**But :** Renvoie le ping d'un serveur en millisecondes.

**Valeurs :** `ip`

**Exemple :**

```
{"placeholder":"serverping","values":{"ip":"mc.hypixel.net"}}
```

**Sortie :** `54`

## Nombre de joueurs sur le serveur (`serverplayercount`)

**But :** Renvoie le nombre de joueurs d'un serveur.

**Valeurs :** `ip`

**Exemple :**

```
{"placeholder":"serverplayercount","values":{"ip":"mc.hypixel.net"}}
```

**Sortie :** `25000/30000`

## État du serveur (`serverstatus`)

**But :** Renvoie l'état en ligne/hors ligne d'un serveur.

**Valeurs :** `ip`

**Exemple :**

```
{"placeholder":"serverstatus","values":{"ip":"mc.hypixel.net"}}
```

**Sortie :** `§aOnline` ou `§cOffline`

## Version du serveur (`serverversion`)

**But :** Renvoie la version Minecraft d'un serveur.

**Valeurs :** `ip`

**Exemple :**

```
{"placeholder":"serverversion","values":{"ip":"mc.hypixel.net"}}
```

**Sortie :** `1.21.1`

> [!NOTE]
> Les substitutions en temps réel ci-dessous acceptent une valeur `timezone`. Utilisez un identifiant de fuseau horaire Java comme `UTC`, `Europe/Berlin` ou `America/New_York` ; omettez-le ou utilisez `system` pour le fuseau horaire du système. `unix_time` renvoie toujours l'horodatage Unix et n'a pas de valeur `timezone`.

## Année (`realtimeyear`)

**But :** Renvoie l'année actuelle.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"realtimeyear"}
```

**Sortie :** `2024`

## Mois (`realtimemonth`)

**But :** Renvoie le mois actuel (01-12).

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"realtimemonth"}
```

**Sortie :** `01`

## Jour (`realtimeday`)

**But :** Renvoie le jour actuel du mois (01-31).

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"realtimeday"}
```

**Sortie :** `27`

## Heure (`realtimehour`)

**But :** Renvoie l'heure actuelle. Par défaut, le format 24 heures est utilisé ; définissez `twelve_hour_format` sur `"true"` pour le format 12 heures.

**Valeurs :** `twelve_hour_format`, `timezone`

**Exemple :**

```
{"placeholder":"realtimehour","values":{"twelve_hour_format":"false","timezone":"system"}}
```

**Sortie :** `14`

## Minute (`realtimeminute`)

**But :** Renvoie la minute actuelle (00-59).

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"realtimeminute"}
```

**Sortie :** `30`

## Seconde (`realtimesecond`)

**But :** Renvoie la seconde actuelle (00-59).

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"realtimesecond"}
```

**Sortie :** `45`

## Heure actuelle en millisecondes (timestamp Unix) (`unix_time`)

**But :** Renvoie l'horodatage Unix actuel en millisecondes.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"unix_time"}
```

**Sortie :** `1716552478123`

## Informations CPU (`cpuinfo`)

**But :** Renvoie des informations sur le processeur.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"cpuinfo"}
```

**Sortie :** `Intel(R) Core(TM) i7-10700K CPU @ 3.80GHz`

## Utilisation CPU (JVM) (`jvmcpu`)

**But :** Renvoie l'utilisation CPU de la JVM en pourcentage.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"jvmcpu"}
```

**Sortie :** `25.5`

## Utilisation CPU (OS) (`oscpu`)

**But :** Renvoie l'utilisation CPU du système en pourcentage.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"oscpu"}
```

**Sortie :** `42.8`

## Informations GPU (`gpuinfo`)

**But :** Renvoie le nom indiqué pour le périphérique de rendu actif de Minecraft. Cela ne permet pas de garantir l'identification d'un GPU physique précis.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"gpuinfo"}
```

**Sortie :** `NVIDIA GeForce RTX 3080`

## Version de Java (`javaver`)

**But :** Renvoie la version de Java.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"javaver"}
```

**Sortie :** `17.0.2`

## Machine virtuelle Java (`jvmname`)

**But :** Renvoie le nom de la machine virtuelle Java.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"jvmname"}
```

**Sortie :** `OpenJDK 64-Bit Server VM`

## Version d'OpenGL (`glver`)

**But :** Renvoie des informations de pilote pour le périphérique de rendu actif de Minecraft. Malgré l'ancien nom `glver`, la valeur ne correspond pas nécessairement uniquement à une chaîne de version OpenGL.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"glver"}
```

**Sortie :** `4.6.0 NVIDIA 516.94`

## Nom du système d'exploitation (`osname`)

**But :** Renvoie le nom du système d'exploitation.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"osname"}
```

**Sortie :** `Windows 10`

## FPS (images par seconde) (`fps`)

**But :** Renvoie le nombre actuel d'images par seconde.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"fps"}
```

**Sortie :** `120`

## RAM utilisée en Mo (`usedram`)

**But :** Renvoie la quantité de RAM actuellement utilisée (Mo).

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"usedram"}
```

**Sortie :** `4096`

## RAM maximale en Mo (`maxram`)

**But :** Renvoie la quantité maximale de RAM allouée (Mo).

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"maxram"}
```

**Sortie :** `8192`

## RAM utilisée en %% (`percentram`)

**But :** Renvoie le pourcentage de RAM actuellement utilisé.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"percentram"}
```

**Sortie :** `50`

## Volume d'un élément audio (`audio_element_vol`)

**But :** Renvoie le volume d'un élément audio.

**Valeurs :** `element_identifier`

**Exemple :**

```
{"placeholder":"audio_element_vol","values":{"element_identifier":"background_music"}}
```

**Sortie :** `0.5`

## Piste audio actuelle (`audio_element_current_track`)

**But :** Renvoie le nom de la piste d'un élément audio.

**Valeurs :** `element_identifier`, `display_name_mappings`

**Exemple :**

```
{"placeholder":"audio_element_current_track","values":{"element_identifier":"background_music","display_name_mappings":"track1.ogg=>Menu Theme%:%track2.ogg=>Credits Theme"}}
```

Dans `display_name_mappings`, `=>` sépare le nom de fichier de son nom affiché et `%:%` sépare les correspondances.

**Sortie :** `Menu Theme`

## Durée audio (`audio_duration`)

**But :** Renvoie la durée de la piste actuellement chargée de l'[élément audio](./elements#audio) au format `MM:SS`. La piste peut être en lecture, en pause ou arrêtée.

**Valeurs :** `element_identifier`

**Exemple :**

```
{"placeholder":"audio_duration","values":{"element_identifier":"background_music"}}
```

**Sortie :** `03:45`

## Temps de lecture audio (`audio_playtime`)

**But :** Renvoie le temps de lecture actuel d'une piste audio. Définissez `show_percentage` sur `"true"` pour obtenir une valeur de progression de 0 à 100 au lieu de `MM:SS`.

**Valeurs :** `element_identifier`, `show_percentage`

**Exemple :**

```
{"placeholder":"audio_playtime","values":{"element_identifier":"background_music","show_percentage":"false"}}
```

**Sortie :** `01:30` (ou `45` lorsque `show_percentage` est `"true"`)

**Résultat indisponible :** `00:00`, ou `0` en mode pourcentage. La valeur actuelle est disponible lorsque la piste est en lecture ou en pause ; les pistes arrêtées, manquantes ou non prêtes utilisent le résultat indisponible.

## État de lecture audio (`audio_playing_state`)

**But :** Indique si un élément audio est en cours de lecture (true/false).

**Valeurs :** `element_identifier`

**Exemple :**

```
{"placeholder":"audio_playing_state","values":{"element_identifier":"background_music"}}
```

**Sortie :** `true`

## Volume d'un élément vidéo (`video_element_vol`)

**But :** Renvoie le niveau de volume d'un élément vidéo (0.0 à 1.0).

**Valeurs :** `element_identifier`

**Exemple :**

```
{"placeholder":"video_element_vol","values":{"element_identifier":"my_video_element"}}
```

**Sortie :** `0.5`

## Durée d'un élément vidéo (`video_element_duration`)

**But :** Renvoie la durée totale d'un élément vidéo au format `MM:SS`. Définissez `output_as_timestamp` sur `"true"` pour renvoyer un horodatage en millisecondes.

**Valeurs :** `element_identifier`, `output_as_timestamp`

**Exemple :**

```
{"placeholder":"video_element_duration","values":{"element_identifier":"my_video_element","output_as_timestamp":"false"}}
```

**Sortie :** `02:00` (ou `120000` lorsque `output_as_timestamp` est `"true"`)

## Temps de lecture d'un élément vidéo (`video_element_playtime`)

**But :** Renvoie le temps de lecture actuel (progression) d'un élément vidéo au format `MM:SS`. Définissez `show_percentage` sur `"true"` pour une valeur de progression de 0 à 100, ou `output_as_timestamp` sur `"true"` pour des millisecondes.

**Valeurs :** `element_identifier`, `show_percentage`, `output_as_timestamp`

**Exemple :**

```
{"placeholder":"video_element_playtime","values":{"element_identifier":"my_video_element","show_percentage":"false","output_as_timestamp":"false"}}
```

**Sortie :** `00:45` (ou `38` en pourcentage, ou `45200` en horodatage)

## État de pause d'un élément vidéo (`video_element_paused_state`)

**But :** Indique si un élément vidéo est en pause (true/false).

**Valeurs :** `element_identifier`

**Exemple :**

```
{"placeholder":"video_element_paused_state","values":{"element_identifier":"my_video_element"}}
```

**Sortie :** `false`

## Volume de l'arrière-plan vidéo (`video_background_vol`)

**But :** Renvoie le niveau de volume d'un arrière-plan vidéo du menu (0.0 à 1.0).

**Valeurs :** `background_identifier`

**Exemple :**

```
{"placeholder":"video_background_vol","values":{"background_identifier":"main_menu_video"}}
```

**Sortie :** `0.7`

## Durée de l'arrière-plan vidéo (`video_background_duration`)

**But :** Renvoie la durée totale d'un arrière-plan vidéo du menu au format `MM:SS`. Définissez `output_as_timestamp` sur `"true"` pour renvoyer un horodatage en millisecondes.

**Valeurs :** `background_identifier`, `output_as_timestamp`

**Exemple :**

```
{"placeholder":"video_background_duration","values":{"background_identifier":"main_menu_video","output_as_timestamp":"false"}}
```

**Sortie :** `03:00` (ou `180000` lorsque `output_as_timestamp` est `"true"`)

## Temps de lecture de l'arrière-plan vidéo (`video_background_playtime`)

**But :** Renvoie le temps de lecture actuel (progression) d'un arrière-plan vidéo du menu au format `MM:SS`. Définissez `show_percentage` sur `"true"` pour une valeur de progression de 0 à 100, ou `output_as_timestamp` sur `"true"` pour des millisecondes.

**Valeurs :** `background_identifier`, `show_percentage`, `output_as_timestamp`

**Exemple :**

```
{"placeholder":"video_background_playtime","values":{"background_identifier":"main_menu_video","show_percentage":"false","output_as_timestamp":"false"}}
```

**Sortie :** `01:00` (ou `33` en pourcentage, ou `60500` en horodatage)

## État de pause de l'arrière-plan vidéo (`video_background_paused_state`)

**But :** Indique si un arrière-plan vidéo du menu est en pause (true/false).

**Valeurs :** `background_identifier`

**Exemple :**

```
{"placeholder":"video_background_paused_state","values":{"background_identifier":"main_menu_video"}}
```

**Sortie :** `true`

## Calculatrice (`calc`)

**But :** La substitution de calculatrice est un outil puissant qui vous permet d'effectuer des calculs mathématiques dans vos mises en page. Elle prend en charge un large éventail d'opérations mathématiques et peut fonctionner avec des nombres décimaux comme entiers.

**Valeurs :** `decimal`, `expression`

### Syntaxe de base

**Exemple :**

```
{"placeholder":"calc","values":{"decimal":"true/false","expression":"your_expression"}}
```

La calculatrice possède deux paramètres principaux :
- `decimal` : Détermine si le résultat doit inclure des décimales (`true`) ou être arrondi à des entiers (`false`)
- `expression` : L'expression mathématique à évaluer

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

## Nombre aléatoire (`random_number`)

**But :** Génère un nombre aléatoire dans une plage donnée.

**Valeurs :** `min`, `max`

**Exemple :**

```
{"placeholder":"random_number","values":{"min":"1","max":"100"}}
```

**Sortie :** `42`

## Nombre maximum (`maxnum`)

**But :** Renvoie le plus grand de deux nombres.

**Valeurs :** `first`, `second`

**Exemple :**

```
{"placeholder":"maxnum","values":{"first":"10","second":"20"}}
```

**Sortie :** `20`

## Nombre minimum (`minnum`)

**But :** Renvoie le plus petit de deux nombres.

**Valeurs :** `first`, `second`

**Exemple :**

```
{"placeholder":"minnum","values":{"first":"10","second":"20"}}
```

**Sortie :** `10`

## Valeur absolue (`absnum`)

**But :** Renvoie la valeur absolue d'un nombre.

**Valeurs :** `num`

**Exemple :**

```
{"placeholder":"absnum","values":{"num":"-10.5"}}
```

**Sortie :** `10.5`

## Rendre un nombre négatif (`negnum`)

**But :** Rend négatif un nombre positif. Les zéros et les valeurs déjà négatives sont renvoyés tels quels.

**Valeurs :** `num`

**Exemple :**

```
{"placeholder":"negnum","values":{"num":"10.5"}}
```

**Sortie :** `-10.5`

## *pi* (math) (`math_pi`)

**But :** Renvoie la valeur de π.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"math_pi"}
```

**Sortie :** `3.141592653589793`

## Sinus trigonométrique (math) (`math_sin`)

**But :** Renvoie le sinus d'un angle en radians. Convertissez d'abord les valeurs en degrés en radians.

**Valeurs :** `angle`

**Exemple :**

```
{"placeholder":"math_sin","values":{"angle":"1.5707963267948966"}}
```

**Sortie :** `1.0`

## Cosinus trigonométrique (math) (`math_cos`)

**But :** Renvoie le cosinus d'un angle en radians. Convertissez d'abord les valeurs en degrés en radians.

**Valeurs :** `angle`

**Exemple :**

```
{"placeholder":"math_cos","values":{"angle":"0"}}
```

**Sortie :** `1.0`

## Tangente trigonométrique (math) (`math_tan`)

**But :** Renvoie la tangente d'un angle en radians. Convertissez d'abord les valeurs en degrés en radians.

**Valeurs :** `angle`

**Exemple :**

```
{"placeholder":"math_tan","values":{"angle":"0"}}
```

**Sortie :** `0.0`

## Plancher (math) (`math_floor`)

**But :** Renvoie le plancher mathématique d'un nombre, formaté avec un suffixe décimal `.0`.

**Valeurs :** `num`

**Exemple :**

```
{"placeholder":"math_floor","values":{"num":"3.14"}}
```

**Sortie :** `3.0`

## Plafond (math) (`math_ceil`)

**But :** Renvoie le plafond mathématique d'un nombre, formaté avec un suffixe décimal `.0`.

**Valeurs :** `num`

**Exemple :**

```
{"placeholder":"math_ceil","values":{"num":"3.14"}}
```

**Sortie :** `4.0`

Utilisez [**Arrondir**](#round-math-math_round) ou [**Calculatrice**](#calculatrice-calc) avec la sortie décimale désactivée lorsque vous avez besoin d'un texte entier sans `.0`.

## Arrondir (math) (`math_round`)

**But :** Arrondit un nombre. Par défaut, il arrondit à l'entier le plus proche ; définissez `decimals` sur un nombre non négatif pour arrondir à ce nombre de décimales.

**Valeurs :** `num`, `decimals`

**Exemple :**

```
{"placeholder":"math_round","values":{"num":"3.14159","decimals":"2"}}
```

**Sortie :** `3.14` (avec `decimals:-1` ou omis → `3`)

## Signe (math) (`math_sign`)

**But :** Renvoie le signe d'un nombre (1 pour positif, -1 pour négatif, 0 pour zéro).

**Valeurs :** `num`

**Exemple :**

```
{"placeholder":"math_sign","values":{"num":"-3.14"}}
```

**Sortie :** `-1`

## Sinus hyperbolique (math) (`math_sinh`)

**But :** Renvoie le sinus hyperbolique d'un nombre.

**Valeurs :** `num`

**Exemple :**

```
{"placeholder":"math_sinh","values":{"num":"1"}}
```

**Sortie :** `1.1752011936438014`

## Cosinus hyperbolique (math) (`math_cosh`)

**But :** Renvoie le cosinus hyperbolique d'un nombre.

**Valeurs :** `num`

**Exemple :**

```
{"placeholder":"math_cosh","values":{"num":"1"}}
```

**Sortie :** `1.5430806348152437`

## Tangente hyperbolique (math) (`math_tanh`)

**But :** Renvoie la tangente hyperbolique d'un nombre.

**Valeurs :** `num`

**Exemple :**

```
{"placeholder":"math_tanh","values":{"num":"1"}}
```

**Sortie :** `0.7615941559557649`

## Découper le texte (`split_text`)

**But :** Découpe un texte à l'aide d'un séparateur spécifié.

**Valeurs :** `input`, `regex`, `max_parts`, `split_index`

**Exemple :**

```
{"placeholder":"split_text","values":{"input":"hello,world","regex":",","max_parts":"2","split_index":"1"}}
```

**Sortie :** `world`

## Rogner le texte (`trim_text`)

**But :** Supprime les espaces blancs au début et à la fin.

**Valeurs :** `text`

**Exemple :**

```
{"placeholder":"trim_text","values":{"text":"  hello world  "}}
```

**Sortie :** `hello world`

## Rogner le texte (`crop_text`)

**But :** Supprime des caractères au début et à la fin du texte.

**Valeurs :** `text`, `remove_from_start`, `remove_from_end`

**Exemple :**

```
{"placeholder":"crop_text","values":{"text":"hello world","remove_from_start":"1","remove_from_end":"1"}}
```

**Sortie :** `ello worl`

## Chaîne échappée (`stringify`)

**But :** Transforme un texte en chaîne en échappant tous les caractères syntaxiques.

**Valeurs :** `text`

**Exemple :**

```
{"placeholder":"stringify","values":{"text":"text with {special} \"characters\""}}
```

**Sortie :** `text with \{special\} \"characters\"`

## Texte localisé (`local`)

**But :** Récupère le texte localisé pour une clé.

**Valeurs :** `key`

**Exemple :**

```
{"placeholder":"local","values":{"key":"menu.singleplayer"}}
```

**Sortie :** `Singleplayer`

## Texte web (`webtext`)

**But :** Récupère le contenu texte depuis une URL web.

**Valeurs :** `link`

**Exemple :**

```
{"placeholder":"webtext","values":{"link":"http://somewebsite.com/textfile.txt"}}
```

**Sortie :** `Welcome to the server!`

## Texte aléatoire (`randomtext`)

**But :** Renvoie une ligne aléatoire d'un fichier texte, d'une URL ou d'un texte brut direct. Le texte change à intervalles spécifiés. Le contenu des fichiers et des URL est actualisé approximativement toutes les 30 secondes ; le contenu brut direct reste mis en cache car il ne nécessite pas de rechargement.

**Valeurs :** `source`, `interval`

Dans les valeurs de substitution, `/config/...` signifie `<game-directory>/config/...` ; ce n'est pas un chemin à la racine du système de fichiers. Voir [Ressources](./resources#local-resources).

**Exemple :**

```
{"placeholder":"randomtext","values":{"source":"/config/fancymenu/assets/<file_name.txt>","interval":"10"}}
```
Paramètres :
- `source` : La source des lignes de texte (remplace l'ancien paramètre `path`)
  - Chemin de fichier : `/config/fancymenu/assets/quotes.txt`
  - URL : `https://example.com/quotes.txt`
  - Texte brut : `Line 1\nLine 2\nLine 3`
- `interval` : Temps en secondes entre les changements de texte

La substitution prend désormais en charge trois types de source :
1. **Fichiers locaux** : fichiers texte provenant de votre répertoire de jeu
   ```
   {"placeholder":"randomtext","values":{"source":"/config/fancymenu/assets/quotes.txt","interval":"10"}}
   ```
2. **URL** : fichiers texte distants provenant d'Internet
   ```
   {"placeholder":"randomtext","values":{"source":"https://example.com/quotes.txt","interval":"10"}}
   ```
3. **Texte brut** : saisie de texte directe avec des lignes séparées par `\n`
   ```
   {"placeholder":"randomtext","values":{"source":"First line\nSecond line\nThird line","interval":"5"}}
   ```

Remarque : les anciennes substitutions utilisant `path` au lieu de `source` continueront de fonctionner.

## Analyseur JSON (`json`)

**But :** Analyse des données JSON provenant d'un fichier, d'une URL ou d'un contenu JSON direct et extraction de valeurs à l'aide d'expressions JSON path.

**Valeurs :** `source`, `json_path`

**Exemple :**

```
{"placeholder":"json","values":{"source":"path_or_link_or_json_content","json_path":"$.some.json.path"}}
```
Paramètres :
- `source` : La source des données JSON
  - Chemin de fichier : `/config/fancymenu/assets/data.json`
  - URL : `https://api.example.com/data.json`
  - JSON direct : `{"name":"Steve","level":42}`
- `json_path` : L'expression JSON path à utiliser pour extraire les données

La substitution prend désormais en charge trois types de source :
1. **Fichiers locaux** : fichiers JSON provenant de votre répertoire de jeu
   ```
   {"placeholder":"json","values":{"source":"/config/fancymenu/assets/playerdata.json","json_path":"$.player.name"}}
   ```
2. **URL** : données JSON distantes provenant d'API ou de services web
   ```
   {"placeholder":"json","values":{"source":"https://api.minecraft.com/server/status","json_path":"$.online"}}
   ```
3. **JSON direct** : contenu JSON en ligne
   ```
   {"placeholder":"json","values":{"source":"{"name":"Steve","score":42,"rank":"Diamond"}","json_path":"$.rank"}}
   ```

Exemples de JSON path :
- `$.name` - Récupère le champ "name" à partir de la racine
- `$.player.level` - Récupère le champ imbriqué "level" dans "player"
- `$.items[0].id` - Récupère l'"id" du premier élément d'un tableau
- `$.scores.*` - Récupère toutes les valeurs de l'objet "scores"

## Chemin absolu d'un fichier/dossier (`absolute_path`)

**But :** Renvoie le chemin absolu d'un fichier.

**Valeurs :** `short_path`

**Exemple :**

```
{"placeholder":"absolute_path","values":{"short_path":"relative/path/to/file.txt"}}
```

**Sortie :** `C:/Games/PrismLauncher/instances/My Pack/relative/path/to/file.txt`

## Nombre de caractères du texte (`text_character_count`)

**But :** Renvoie le nombre de caractères dans le texte donné.

**Valeurs :** `text`

**Exemple :**

```
{"placeholder":"text_character_count","values":{"text":"Hello World!"}}
```

**Sortie :** `12`

## Largeur du texte (`text_width`)

**But :** Renvoie la largeur en pixels du texte donné lorsqu'il est rendu.

**Valeurs :** `text`

**Exemple :**

```
{"placeholder":"text_width","values":{"text":"Hello World!"}}
```

**Sortie :** `66`

## Texte en majuscules (`uppercase_text`)

**But :** Convertit le texte d'entrée en majuscules.

**Valeurs :** `text`

**Exemple :**

```
{"placeholder":"uppercase_text","values":{"text":"Hello World"}}
```

**Sortie :** `HELLO WORLD`

## Texte en minuscules (`lowercase_text`)

**But :** Convertit le texte d'entrée en minuscules.

**Valeurs :** `text`

**Exemple :**

```
{"placeholder":"lowercase_text","values":{"text":"Hello World"}}
```

**Sortie :** `hello world`

## Texte en casse de titre (`title_case_text`)

**But :** Convertit le texte d'entrée en casse de titre.

**Valeurs :** `text`

**Exemple :**

```
{"placeholder":"title_case_text","values":{"text":"hello world"}}
```

**Sortie :** `Hello World`

## Texte en casse de phrase (`sentence_case_text`)

**But :** Convertit le texte d'entrée en casse de phrase.

**Valeurs :** `text`

**Exemple :**

```
{"placeholder":"sentence_case_text","values":{"text":"hello world. this is fancymenu!"}}
```

**Sortie :** `Hello world. This is fancymenu!`

## Texte en snake_case (`snake_case_text`)

**But :** Convertit le texte d'entrée en `snake_case`.

**Valeurs :** `text`

**Exemple :**

```
{"placeholder":"snake_case_text","values":{"text":"Hello World"}}
```

**Sortie :** `hello_world`

## Texte en kebab-case (`kebab_case_text`)

**But :** Convertit le texte d'entrée en `kebab-case`.

**Valeurs :** `text`

**Exemple :**

```
{"placeholder":"kebab_case_text","values":{"text":"Hello World"}}
```

**Sortie :** `hello-world`

## Texte en casse alternée (`alternating_case_text`)

**But :** Convertit le texte d'entrée en casse alternée.

**Valeurs :** `text`

**Exemple :**

```
{"placeholder":"alternating_case_text","values":{"text":"alternating case"}}
```

**Sortie :** `aLtErNaTiNg CaSe`

## Inverser la casse du texte (`toggle_case_text`)

**But :** Inverse la casse de chaque lettre du texte d'entrée.

**Valeurs :** `text`

**Exemple :**

```
{"placeholder":"toggle_case_text","values":{"text":"Toggle Case"}}
```

**Sortie :** `tOGGLE cASE`

## Encoder en Base64 (`base64_encode`)

**But :** Encode le texte donné en Base64.

**Valeurs :** `text`

**Exemple :**

```
{"placeholder":"base64_encode","values":{"text":"Hello World"}}
```

**Sortie :** `SGVsbG8gV29ybGQ=`

## Décoder depuis Base64 (`base64_decode`)

**But :** Décode une chaîne Base64 en texte brut.

**Valeurs :** `text`

**Exemple :**

```
{"placeholder":"base64_decode","values":{"text":"SGVsbG8gV29ybGQ="}}
```

**Sortie :** `Hello World`

## Texte de fichier (`file_text`)

**But :** Renvoie des lignes de texte depuis un fichier ou une URL. Peut renvoyer toutes les lignes ou seulement les X dernières lignes.

**Valeurs :** `path_or_url`, `mode`, `separator`, `last_lines`

**Exemple :**

```
{"placeholder":"file_text","values":{"path_or_url":"/config/fancymenu/assets/some_file.txt","mode":"all","separator":"\n","last_lines":"1"}}
```
Paramètres :
- `path_or_url` : Chemin de fichier ou URL à lire
- `mode` : Soit `"all"` (renvoie toutes les lignes) soit `"last"` (renvoie seulement les X dernières lignes)
- `separator` : Texte utilisé entre les lignes (par défaut : `"\n"`)
- `last_lines` : Nombre de lignes à renvoyer lorsque le mode est `"last"` (par défaut : `"1"`)

**Sortie :**

```text
First line
Second line
```

## Contenu du presse-papiers (`clipboard_content`)

**But :** Renvoie le contenu texte actuellement stocké dans le presse-papiers du système.

**Valeurs :** Aucune

**Exemple :**

```
{"placeholder":"clipboard_content"}
```

**Sortie :** `Hello from the clipboard`

## Remplacer du texte (`replace_text`)

**But :** Remplace du texte dans une chaîne à l'aide de texte littéral ou d'expressions régulières.

**Valeurs :** `text`, `search`, `replacement`, `use_regex`, `replace_all`

**Exemple :**

```
{"placeholder":"replace_text","values":{"text":"Hello World! This is a test.","search":"World","replacement":"FancyMenu","use_regex":"false","replace_all":"true"}}
```
Paramètres :
- `text` : Le texte d'entrée à traiter
- `search` : Le texte ou motif regex à rechercher
- `replacement` : Le texte de remplacement
- `use_regex` : Indique s'il faut utiliser les regex (`"true"`) ou une correspondance littérale (`"false"`)
- `replace_all` : Remplacer toutes les occurrences (`"true"`) ou seulement la première (`"false"`)

**Sortie :** `Hello FancyMenu! This is a test.`

## Instruction switch-case (`switch_case`)

**But :** Effectue une opération de type switch-case en fonction d'une valeur.

**Valeurs :** `value`, `cases`, `default`

**Exemple :**

```
{"placeholder":"switch_case","values":{"value":"1","cases":"1:first case,2:second case,3:third case","default":"default case"}}
```

**Sortie :** `first case` (si la valeur est 1)

## Obtenir la valeur d'une variable (variable FM) (`getvariable`)

**But :** Récupère la valeur d'une variable stockée précédemment.

**Valeurs :** `name`

**Exemple :**

```
{"placeholder":"getvariable","values":{"name":"some_variable"}}
```

**Sortie :** `42`

## Obtenir des données NBT (`nbt_data_get`)

**But :** Récupère des données NBT côté client (similaire à la commande `/data get`). Utilisez la variante serveur `nbt_data_get_server` lorsque vous êtes connecté à un serveur et avez besoin de valeurs fiables côté serveur.

**Valeurs :** `source_type`, `entity_selector`, `nbt_path`, `scale`, `return_type`

**Exemple :**

```
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"foodLevel","scale":"1.0","return_type":"value"}}
```
Paramètres :
- `source_type` : Soit `"entity"` soit `"block"`
- `entity_selector` : Sélecteur d'entité comme `@s`, `@p`, `@e`, ou UUID/nom (pour les entités)
- `block_pos` : Position du bloc au format `"x y z"` (pour les blocs)
- `nbt_path` : Le chemin NBT à récupérer
- `scale` : Facteur d'échelle facultatif pour les valeurs numériques (par défaut : `"1.0"`)
- `return_type` : Comment renvoyer les données :
  - `"value"` : Valeur par défaut, renvoie la valeur (avec mise à l'échelle facultative pour les nombres)
  - `"string"` : Renvoie les données NBT réelles sous forme de chaîne
  - `"snbt"` : Renvoie en SNBT (NBT formaté)
  - `"json"` : Renvoie sous forme de composant JSON (pour les balises de type compound)

**Sortie :** `20` (pour le niveau de faim)

## Obtenir des données NBT (côté serveur) (`nbt_data_get_server`)

**But :** Interroge les données NBT côté serveur (via un paquet) et met brièvement les résultats en cache. Les valeurs sont les mêmes que pour la substitution côté client.

**Valeurs :** `source_type`, `entity_selector`, `block_pos`, `storage_id`, `nbt_path`, `scale`, `return_type`

**Exemple :**

```
{"placeholder":"nbt_data_get_server","values":{"source_type":"entity","entity_selector":"@s","block_pos":"","storage_id":"minecraft:storage_key","nbt_path":"SelectedItem.id","scale":"1.0","return_type":"value"}}
```

**Sortie :** `minecraft:diamond_sword`

## Dernier message de mort (`lastdeathmessage`)

**But :** Renvoie le dernier message de mort enregistré du joueur client. Définissez `as_json_component` sur `"true"` pour obtenir le composant texte JSON brut.

**Valeurs :** `as_json_component`

**Exemple :**

```
{"placeholder":"lastdeathmessage","values":{"as_json_component":"false"}}
```

**Sortie :** `Steve was slain by Zombie`

## Durée de fonctionnement (`uptime_duration`)

**But :** Renvoie depuis combien de temps FancyMenu est chargé. Par défaut, la valeur est en secondes ; définissez `output_as_millis` sur `"true"` pour recevoir des millisecondes.

**Valeurs :** `output_as_millis`

**Exemple :**

```
{"placeholder":"uptime_duration","values":{"output_as_millis":"false"}}
```

**Sortie :** `742` (secondes depuis le chargement)

## Noms des sauvegardes de mondes (`level_save_names`)

**But :** Liste tous les noms de sauvegardes de mondes locaux joints par le séparateur choisi. S'exécute sur le thread client.

**Valeurs :** `separator`

**Exemple :**

```
{"placeholder":"level_save_names","values":{"separator":", "}}
```

**Sortie :** `Creative Test, Survival World, Hardcore`

## Données de sauvegarde de monde (`level_save_data`)

**But :** Renvoie les données sérialisées du niveau pour le nom de monde donné (doit correspondre au nom affiché dans la liste des sauvegardes).

**Valeurs :** `level_name`

**Exemple :**

```
{"placeholder":"level_save_data","values":{"level_name":"Survival World"}}
```

**Sortie :** `{"name":"Survival World","gameMode":"survival",...}`

## Convertisseur de base numérique (`number_base_convert`)

**But :** Convertit un nombre (entier ou fractionnaire) d'une base à une autre (2–36). Par défaut, la base décimale est utilisée si les bases ne sont pas fournies.

**Valeurs :** `input`, `from_base`, `to_base`

**Exemple :**

```
{"placeholder":"number_base_convert","values":{"input":"67.5","from_base":"10","to_base":"16"}}
```

**Sortie :** `43.8`

## Taille du fichier (`file_size`)

**But :** Renvoie la taille d'un fichier local en octets. Seuls les chemins locaux sont autorisés.

**Valeurs :** `path`

**Exemple :**

```
{"placeholder":"file_size","values":{"path":"/config/fancymenu/assets/notes.txt"}}
```

**Sortie :** `1284`

## MD5 du fichier (`file_md5`)

**But :** Renvoie le hachage MD5 d'un fichier local sous forme de chaîne hexadécimale en minuscules.

**Valeurs :** `path`

**Exemple :**

```
{"placeholder":"file_md5","values":{"path":"/config/fancymenu/assets/notes.txt"}}
```

**Sortie :** `d41d8cd98f00b204e9800998ecf8427e`

# Exemples pratiques

## Créer un affichage dynamique de la mémoire
```
RAM utilisée : {"placeholder":"usedram"}Mo / {"placeholder":"maxram"}Mo ({"placeholder":"percentram"}%)
```

## Créer une horloge en temps réel
```
{"placeholder":"realtimehour","values":{"timezone":"system"}}:{"placeholder":"realtimeminute","values":{"timezone":"system"}}:{"placeholder":"realtimesecond","values":{"timezone":"system"}}
```

## Créer un affichage d'informations système
```
OS : {"placeholder":"osname"}
CPU : {"placeholder":"cpuinfo"}
GPU : {"placeholder":"gpuinfo"}
Java : {"placeholder":"javaver"}
```

## HUD d'état du joueur
```
Santé : {"placeholder":"current_player_health"} / {"placeholder":"max_player_health"} ({"placeholder":"current_player_health_percent"}%)
Armure : {"placeholder":"current_player_armor"} / {"placeholder":"max_player_armor"}
Niveau XP : {"placeholder":"current_player_level"}
```

## Calcul complexe avec substitutions imbriquées
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

1. **Mettre en cache les opérations coûteuses** : certaines substitutions (comme celles qui lisent des informations système) peuvent consommer des ressources. Envisagez d'utiliser des variables pour stocker leurs valeurs si vous devez les utiliser plusieurs fois.

2. **Utiliser les bons paramètres décimaux** : lors de calculs, utilisez le paramètre `decimal` de manière appropriée. Réglez-le sur `false` lorsque vous avez besoin d'entiers et sur `true` lorsque vous avez besoin de valeurs décimales précises.

3. **Gérer les valeurs manquantes** : tenez toujours compte de ce qui doit se passer si une substitution ne renvoie aucune valeur. Vous pouvez vouloir fournir des valeurs par défaut dans ce cas.

4. **Tester les performances** : lorsque vous utilisez beaucoup de substitutions ou des structures imbriquées complexes, testez l'impact sur les performances, en particulier sur les systèmes moins puissants.

5. **Utiliser un dimensionnement/un positionnement avancé** : pour les éléments d'interface dynamiques, combinez les substitutions avec un dimensionnement et un positionnement avancés pour créer des mises en page adaptatives.

6. **Combiner avec des variables** : utilisez les substitutions avec les variables pour obtenir un contenu encore plus dynamique, pouvant être mis à jour via des actions.

# Problèmes courants et solutions

## La substitution ne se met pas à jour
Si la valeur d'une substitution ne se met pas à jour comme prévu, vérifiez :
- Que la substitution est correctement formatée
- Si vous utilisez la bonne casse pour les identifiants de substitution
- Si la substitution nécessite des conditions spécifiques pour se mettre à jour

## Les substitutions imbriquées ne fonctionnent pas
Lors de l'imbrication de substitutions :
- Assurez-vous que les guillemets sont correctement échappés
- Vérifiez que chaque substitution imbriquée est valide individuellement

## Problèmes de performances
Si vous remarquez des problèmes de performances :
- Réduisez le nombre de substitutions utilisées
- Évitez les imbrications inutiles
- Envisagez d'utiliser des variables pour les valeurs fréquemment consultées
- Utilisez la substitution appropriée à vos besoins (par exemple, n'utilisez pas des substitutions en temps réel lorsque des valeurs statiques suffisent)
