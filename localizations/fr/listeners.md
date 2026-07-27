---
title: Écouteurs
description: Comment créer et utiliser des écouteurs dans FancyMenu.
---

# Écouteurs

Les écouteurs exécutent des [scripts d'action](./action-scripts) lorsque des événements spécifiques se produisent. Ils ne sont liés à aucun écran ouvert, ils peuvent donc aussi s'exécuter pendant une partie ou un chargement.

Les écouteurs peuvent fournir des valeurs `$$`, comme une touche pressée ou un bouton de souris cliqué, à leurs actions et à leurs conditions.

> [!CAUTION]
> Un écouteur peut exécuter des actions de fichier, réseau, commande, presse-papiers, pack de ressources ou lien sans qu’un écran soit ouvert. N’importez des écouteurs que depuis des sources de confiance.

# Utiliser les écouteurs

En dehors de l’Éditeur de disposition, ouvrez **barre de menu -> Personnalisation -> Gérer les écouteurs** pour créer ou modifier des écouteurs.

<img src="https://github.com/Keksuccino/FancyMenu/blob/master/assets/docs/manage_listeners.png?raw=true" alt="Gérer les écouteurs" style="max-width:800px;width:100%;height:auto;">

# Variables des écouteurs

Les écouteurs peuvent fournir des valeurs en lecture seule à leurs actions et à leurs conditions. Utilisez leurs noms `$$` dans les champs de texte pris en charge.

Par exemple, utilisez [**Sur touche du clavier pressée**](#on-keyboard-key-pressed-keyboard_key_pressed) avec l'[action **Imprimer dans le journal du jeu**](./action-scripts#print-to-game-log-print_to_log). La valeur `Touche pressée ! La touche est : $$key_name` insère le nom de la touche pressée.

> [!WARNING]
> Les variables des écouteurs sont distinctes des [variables stockées](./variables) de FancyMenu. Les actions, conditions et espaces réservés des variables stockées ne fonctionnent pas avec les valeurs `$$`.

Les noms des variables d'écouteur sont sensibles à la casse et ne fonctionnent que dans le script de cet écouteur.

Considérez comme non fiables les valeurs provenant du chat, des serveurs distants, des fichiers et des saisies utilisateur. Ne les insérez pas directement dans des chemins, des URL ou des commandes.

Les variables des écouteurs sont des chaînes de caractères. Lorsqu’une information n’est pas disponible, un écouteur peut renvoyer une valeur sentinelle documentée telle que `ERROR`, `UNKNOWN`, `NONE`, `EMPTY`, `0`, `-1` ou une chaîne vide. Testez ces valeurs avant d’insérer des données d’écouteur dans des chemins, des commandes ou des URL.

# Écouteurs en détail

Cette section répertorie les écouteurs intégrés de FancyMenu.

## Sur texte Markdown cliqué (`text_clicked`)
- Déclenché lorsqu’un [texte Markdown avec un événement `click:`](./text-formatting#click-and-hover-events) est cliqué, par exemple `[Ouvrir](click:open_menu)`.
- Variables :
  - `$$text_event_id` – ID d’événement du lien Markdown

## Sur texte Markdown survolé (`text_hovered`)
- Déclenché lorsqu’un [texte Markdown avec un événement `hover:`](./text-formatting#click-and-hover-events) est survolé, par exemple `[Indice](hover:show_hint)`.
- Variables :
  - `$$text_event_id` – ID d’événement du lien Markdown

## Sur ZIP extrait via une action (`zip_extracted_via_action`)
- Déclenché lorsque l'[action **Extraire le fichier ZIP dans le répertoire du jeu**](./action-scripts#extract-zip-file-in-game-directory-extract_zip_file_in_game_dir) se termine.
- Variables :
  - `$$source_zip_path` – chemin source normalisé affiché à l’utilisateur ; les chemins du répertoire du jeu peuvent être renvoyés comme `/...`, tandis que les chemins classiques du répertoire Minecraft peuvent utiliser `.minecraft/...`
  - `$$target_folder_path` – chemin de destination normalisé affiché à l’utilisateur en utilisant les mêmes formes de chemin
  - `$$extract_succeeded` – vrai/faux
  - `$$failure_reason` – texte d’erreur lorsque l’extraction a échoué

## Sur élément instancié (`element_spawned_via_action`)
- Déclenché lorsqu’une fonctionnalité ou un ajout FancyMenu pris en charge instancie dynamiquement une instance d’élément.
- Variables :
  - `$$element_type` – type d’élément instancié
  - `$$element_identifier` – identifiant de l’élément instancié
  - `$$target_screen` – identifiant de l’écran cible

## Sur démarrage de lecture d’une texture animée (`animated_texture_started_playing`)
- Déclenché lorsqu’une [texture animée](./fma) commence à jouer.
- Variables :
  - `$$texture_source` – source de la texture
  - `$$texture_source_type` – type de source
  - `$$texture_will_restart` – vrai/faux

## Sur fin de lecture d’une texture animée (`animated_texture_finished_playing`)
- Déclenché lorsqu’une texture animée finit de jouer.
- Variables :
  - `$$texture_source`
  - `$$texture_source_type`
  - `$$texture_will_restart`

## Sur changement de statut de lecture vidéo (`video_playback_status_changed`)
- Déclenché lorsqu’un [élément vidéo ou fond de menu](./video) change d’état de lecture.
- Variables :
  - `$$video_source` – source vidéo
  - `$$video_source_type` – type de source
  - `$$is_looping` – vrai/faux
  - `$$new_status` – `PLAYING`, `STOPPED`, `PAUSED` ou `FINISHED`

## Sur réception d’un message système dans le chat (`system_message_received_in_chat`)
- Déclenché lorsque le client reçoit un message de chat système, comme un retour de commande.
- Variables :
  - `$$system_message_string` – message en texte brut
  - `$$system_message_component` – composant JSON

## Sur réception de données FM (`fm_data_received`)
- Déclenché lorsqu’un serveur envoie des [données FM](./fm-data) à ce client via `/fmdata send`.
- Variables :
  - `$$data_identifier` – chaîne d’identifiant des données
  - `$$data` – charge utile des données
  - `$$sent_by` – IP du serveur ou `integrated_server`

## Sur connexion à un serveur distant (`remote_server_connected`)
- Déclenché après l’ouverture réussie d’une [connexion à un serveur distant](./remote-server-communication).
- Variables :
  - `$$request_id` – ID de requête mis en cache
  - `$$remote_server_url` – URL du serveur distant

## Sur réception de données d’un serveur distant (`remote_server_data_received`)
- Déclenché lorsque des données textuelles sont reçues depuis un serveur distant connecté.
- Variables :
  - `$$request_id` – ID de requête
  - `$$remote_server_url` – URL du serveur distant
  - `$$data` – charge utile reçue

## Sur fermeture de connexion à un serveur distant (`remote_server_connection_closed`)
- Déclenché lorsqu’une connexion à un serveur distant se ferme.
- Variables :
  - `$$request_id` – ID de requête
  - `$$remote_server_url` – URL du serveur distant
  - `$$intentionally_closed` – TRUE si fermé par une action
  - `$$crashed` – TRUE si la connexion s’est interrompue de façon inattendue
  - `$$unknown_close_reason` – TRUE si aucune raison de fermeture connue n’était disponible

## Sur touche du clavier pressée (`keyboard_key_pressed`)
- Déclenché chaque fois qu’une touche est pressée (se répète tant qu’elle est maintenue ; fonctionne dans les écrans et en jeu).
- Variables :
  - `$$key_name` – nom affiché de la touche
  - `$$key_keycode` – code de touche GLFW
  - `$$key_scancode` – code de balayage GLFW
  - `$$key_modifiers` – masque binaire des modificateurs actifs

## Sur touche du clavier relâchée (`keyboard_key_released`)
- Déclenché lorsqu’une touche est relâchée (écrans et en jeu).
- Variables :
  - `$$key_name`
  - `$$key_keycode`
  - `$$key_scancode`
  - `$$key_modifiers`

## Sur saisie d’un caractère au clavier dans un écran (`keyboard_char_typed`)
- Déclenché lorsqu’un caractère est saisi pendant qu’un écran est ouvert.
- Variables :
  - `$$char` – caractère saisi

## Sur déplacement de la souris dans un écran (`mouse_moved`)
- Déclenché chaque fois que la souris se déplace pendant qu’un écran est ouvert.
- Variables :
  - `$$mouse_pos_x` – X actuel
  - `$$mouse_pos_y` – Y actuel
  - `$$mouse_move_delta_x` – variation en X depuis le dernier événement
  - `$$mouse_move_delta_y` – variation en Y depuis le dernier événement

## Sur clic d’un bouton de souris (`mouse_button_clicked`)
- Déclenché lorsqu’un bouton de souris est pressé (écrans et en jeu).
- Variables :
  - `$$button` – gauche/droite/milieu
  - `$$mouse_pos_x` – X actuel
  - `$$mouse_pos_y` – Y actuel

## Sur relâchement d’un bouton de souris (`mouse_button_released`)
- Déclenché lorsqu’un bouton de souris est relâché (écrans et en jeu).
- Variables :
  - `$$button`
  - `$$mouse_pos_x`
  - `$$mouse_pos_y`

## Sur défilement de la souris dans un écran (`mouse_scrolled`)
- Déclenché lorsque la molette de la souris est utilisée pendant qu’un écran est ouvert.
- Variables :
  - `$$scroll_delta_y` – quantité de défilement verticale

## Sur ouverture d’écran (`screen_open`)
- S’exécute juste après qu’un écran devient actif ; peut être utilisé pour le remplacer.
- Variables :
  - `$$screen_identifier` – identifiant de l’écran ouvert

## Sur fermeture d’écran (`screen_close`)
- S’exécute immédiatement après la fermeture d’un écran.
- Variables :
  - `$$screen_identifier` – identifiant de l’écran fermé

## Sur fermeture de Minecraft (`quit_minecraft`)
- Déclenché une fois lorsque le client commence à s’arrêter.
- Variables :
  - `$$timestamp_millis` – millisecondes depuis l’epoch au moment de la fermeture
  - `$$timestamp_iso` – horodatage ISO-8601 du moment de la fermeture

## Sur mort (`player_death`)
- S’exécute lorsque l’écran de mort vanilla s’ouvre pour le joueur local.
- Variables :
  - `$$days_survived` – jours depuis la dernière mort
  - `$$death_reason_string` – cause en texte brut
  - `$$death_reason_component` – cause sous forme de composant JSON
  - `$$death_pos_x` – coordonnée X de la mort
  - `$$death_pos_y` – coordonnée Y de la mort
  - `$$death_pos_z` – coordonnée Z de la mort

## Sur variable mise à jour [Variable FM] (`fm_variable_updated`)
- Déclenché chaque fois qu’une [variable FancyMenu](./variables) est définie ou mise à jour.
- Variables :
  - `$$var_name` – nom de la variable
  - `$$old_value` – valeur précédente
  - `$$new_value` – nouvelle valeur

## Sur fichier téléchargé via une action (`file_downloaded_via_action`)
- Déclenché après la fin de l'[action **Télécharger un fichier dans le répertoire du jeu**](./action-scripts#download-file-to-game-directory-download_file_to_game_dir).
- Variables :
  - `$$download_url` – source du téléchargement
  - `$$target_file_path` – chemin du fichier enregistré en cas de succès ; en cas d’échec, peut contenir uniquement le répertoire cible car aucun nom de fichier final n’a été résolu
  - `$$download_succeeded` – vrai/faux

## Sur fichier sélectionné (`file_selected_via_action`)
- Déclenché après la fin de l'[action **Sélectionner un fichier depuis le système**](./action-scripts#select-file-from-system-select_file_to_game_dir).
- Variables :
  - `$$selected_file_path` – chemin absolu du fichier choisi ou vide si annulé
  - `$$target_file_path` – chemin résolu dans l’instance
  - `$$selection_succeeded` – vrai si la copie a réussi
  - `$$selection_cancelled` – vrai si la boîte de dialogue a été fermée
  - `$$failure_reason` – informations d’erreur en cas d’échec

## Sur message de chat reçu (`chat_message_received`)
- Déclenché lorsqu’une ligne de chat de joueur normale apparaît sur le client.
- Variables :
  - `$$chat_message_string` – ligne en texte brut
  - `$$chat_message_component` – composant JSON complet
  - `$$sender_uuid` – UUID de l’expéditeur ou ERROR
  - `$$sender_name` – nom de l’expéditeur ou ERROR

## Sur message de chat envoyé (`chat_message_sent`)
- Déclenché lorsque le joueur local envoie un message de chat.
- Variables :
  - `$$chat_message_string` – ligne en texte brut
  - `$$chat_message_component` – composant JSON complet

## Sur effet obtenu (`effect_gained`)
- Déclenché lorsque le joueur obtient un effet de statut.
- Variables :
  - `$$effect_key` – emplacement de ressource de l’effet
  - `$$effect_type` – positif/négatif/neutre
  - `$$effect_duration` – ticks restants

## Sur effet perdu (`effect_lost`)
- Déclenché lorsque le joueur perd un effet de statut.
- Variables :
  - `$$effect_key` – effet expiré
  - `$$effect_type` – catégorie

## Sur changement d’expérience (`experience_changed`)
- Déclenché chaque fois que l’XP totale du joueur change.
- Variables :
  - `$$new_experience_amount` – après le changement
  - `$$old_experience_amount` – avant le changement
  - `$$is_level_up` – TRUE si le niveau a augmenté

## Sur dégâts subis (`damage_taken`)
- Déclenché une fois par coup lorsque le joueur subit des dégâts.
- Variables :
  - `$$damage_amount` – points de vie retirés
  - `$$damage_type` – emplacement de ressource du type de dégâts
  - `$$is_fatal_damage` – TRUE si mortel
  - `$$damage_source` – emplacement de ressource de l’attaquant ou NONE

## Sur début de gel (`started_freezing`)
- Déclenché lorsque le joueur commence à geler.
- Variables :
  - `$$freezing_intensity` – 0.0 aucun, 1.0 complètement gelé

## Sur fin de gel (`stopped_freezing`)
- Déclenché lorsque le joueur cesse de geler.
- Variables :
  - (aucune)

## Sur gel complet (`fully_frozen`)
- Déclenché une fois lorsque le joueur devient complètement gelé.
- Variables :
  - (aucune)

## Sur début de visée d’un bloc (`start_looking_at_block`)
- Déclenché une fois lorsque le réticule pointe pour la première fois vers un bloc (distance maximale de 20 blocs).
- Variables :
  - `$$block_key` – bloc ciblé
  - `$$block_pos_x` – X du bloc
  - `$$block_pos_y` – Y du bloc
  - `$$block_pos_z` – Z du bloc
  - `$$distance_to_player` – des yeux au point touché

## Sur fin de visée d’un bloc (`stop_looking_at_block`)
- Déclenché lorsque le réticule cesse de pointer vers un bloc (signale le dernier bloc ciblé, max. 20 blocs).
- Variables :
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`
  - `$$distance_to_player`

## Sur début de visée d’une entité (`start_looking_at_entity`)
- Déclenché une fois lorsque le réticule pointe pour la première fois vers une entité (max. 20 blocs).
- Variables :
  - `$$entity_key` – type d’entité ciblée
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## Sur fin de visée d’une entité (`stop_looking_at_entity`)
- Déclenché lorsque le réticule cesse de pointer vers une entité (signale la dernière entité ciblée, max. 20 blocs).
- Variables :
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## Sur apparition d’une entité (`entity_spawned`)
- **Nécessite FancyMenu sur le serveur.** Déclenché lorsqu’une entité apparaît n’importe où dans le monde/serveur connecté.
- Variables :
  - `$$entity_key`
  - `$$distance_to_player` – −1 si autre dimension
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`
  - `$$dimension_key`
  - `$$is_same_dimension_as_player`

## Sur mort d’une entité (`entity_died`)
- **Nécessite FancyMenu sur le serveur.** Déclenché lorsqu’une entité meurt dans le monde/serveur connecté.
- Variables :
  - `$$entity_key`
  - `$$distance_to_player` – −1 si autre dimension
  - `$$death_pos_x`
  - `$$death_pos_y`
  - `$$death_pos_z`
  - `$$entity_uuid`
  - `$$dimension_key`
  - `$$damage_type`
  - `$$is_same_dimension_as_player`
  - `$$entity_killed_by_name`
  - `$$entity_killed_by_key`
  - `$$entity_killed_by_uuid`

## Sur début de visibilité d’une entité (`entity_starts_being_in_sight`)
- Déclenché lorsqu’une entité devient visible pour la première fois à moins de 200 blocs.
- Variables :
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## Sur fin de visibilité d’une entité (`entity_stops_being_in_sight`)
- Déclenché lorsqu’une entité auparavant visible quitte le champ de vision ou dépasse 200 blocs.
- Variables :
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## Sur interaction avec une entité (`entity_interacted`)
- Déclenché lorsque le joueur interagit avec succès avec une entité.
- Variables :
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## Sur monture d’une entité (`entity_mounted`)
- Déclenché lorsque le joueur commence à monter une entité.
- Variables :
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## Sur démontage d’une entité (`entity_unmounted`)
- Déclenché lorsque le joueur cesse de monter son entité actuelle.
- Variables :
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## Sur bloc cassé (`block_broke`)
- Déclenché lorsque le joueur casse un bloc.
- Variables :
  - `$$block_key`
  - `$$broke_with_item_key` – outil utilisé ou EMPTY
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## Sur bloc placé (`block_placed`)
- Déclenché lorsque le joueur place un bloc.
- Variables :
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## Sur interaction avec un bloc (`interacted_with_block`)
- Déclenché lorsque le joueur interagit avec succès avec un bloc.
- Variables :
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## Sur marche sur un bloc (`stepping_on_block`)
- Déclenché lorsque le joueur marche sur un bloc.
- Variables :
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## Sur entrée dans un biome (`enter_biome`)
- Déclenché lorsque le joueur entre dans un nouveau biome.
- Variables :
  - `$$biome_key` – biome dans lequel on entre

## Sur sortie d’un biome (`leave_biome`)
- Déclenché lorsque le joueur quitte son biome actuel.
- Variables :
  - `$$biome_key` – biome venant d’être quitté

## Sur entrée dans une structure (`enter_structure`)
- **Nécessite FancyMenu sur le serveur.** Détection approximative de la zone d’une structure ; peut se déclencher à proximité, au-dessus ou en dessous de la structure.
- Variables :
  - `$$structure_key` – structure dans laquelle on entre

## Sur sortie d’une structure (`leave_structure`)
- **Nécessite FancyMenu sur le serveur.** Détection approximative ; peut se déclencher à proximité de l’emprise de la structure.
- Variables :
  - `$$structure_key` – structure venant d’être quittée

## Sur entrée dans une structure (haute précision) (`enter_structure_high_precision`)
- **Nécessite FancyMenu sur le serveur.** Déclenché lorsque le joueur pénètre dans les boîtes englobantes d’une structure.
- Variables :
  - `$$structure_key`

## Sur sortie d’une structure (haute précision) (`leave_structure_high_precision`)
- **Nécessite FancyMenu sur le serveur.** Déclenché après que le joueur a quitté les boîtes englobantes d’une structure.
- Variables :
  - `$$structure_key`

## Sur entrée dans une dimension (`enter_dimension`)
- Déclenché lorsque le joueur entre dans une nouvelle dimension.
- Variables :
  - `$$dimension_key` – dimension dans laquelle on entre

## Sur début de nage (`start_swimming`)
- Déclenché lorsque le joueur commence à nager.
- Variables :
  - `$$fluid_type` – emplacement de ressource du fluide

## Sur fin de nage (`stop_swimming`)
- Déclenché lorsque le joueur cesse de nager.
- Variables :
  - `$$fluid_type` – fluide dans lequel la nage s’est arrêtée

## Sur début de contact avec un fluide (`start_touching_fluid`)
- Déclenché lorsque le joueur commence à toucher un fluide.
- Variables :
  - `$$fluid_type` – fluide touché

## Sur fin de contact avec un fluide (`stop_touching_fluid`)
- Déclenché lorsque le joueur cesse de toucher un fluide.
- Variables :
  - `$$fluid_type` – fluide qui n’est plus touché

## Sur démarrage d’un morceau de musique (`music_track_started`)
- Déclenché lorsqu’un nouveau morceau de musique commence.
- Variables :
  - `$$track_resource_location` – fichier audio
  - `$$track_display_name` – nom lisible ou UNKNOWN
  - `$$track_artist` – artiste ou UNKNOWN
  - `$$track_duration_ms` – millisecondes (0 si inconnu)

## Sur arrêt d’un morceau de musique (`music_track_stopped`)
- Déclenché lorsque le morceau de musique en cours se termine ou est remplacé.
- Variables :
  - `$$track_resource_location`
  - `$$track_display_name`
  - `$$track_artist`
  - `$$track_duration_ms`

## Sur déclenchement d’un son du monde (`world_sound_triggered`)
- Déclenché lorsqu’un son du monde positionnel commence près du joueur.
- Variables :
  - `$$sound_resource_location` – fichier son
  - `$$sound_display_name` – nom du sous-titre lorsqu’il est disponible
  - `$$sound_origin_pos_x`
  - `$$sound_origin_pos_y`
  - `$$sound_origin_pos_z`
  - `$$sound_origin_distance_to_player`
  - `$$sound_origin_direction_from_player` – degrés 0–360 par rapport à l’orientation

## Sur changement de météo (`weather_changed`)
- Déclenché lorsque la météo change globalement ou localement (un changement de biome ou le fait d’entrer à l’intérieur peut le redéclencher).
- Variables :
  - `$$weather_type` – clear/rain/thunder
  - `$$weather_can_snow` – TRUE si la neige s’affiche
  - `$$weather_can_rain` – TRUE si la pluie s’affiche

## Sur début de combustion (`started_burning`)
- Déclenché lorsque le joueur commence à brûler.
- Variables :
  - (aucune)

## Sur fin de combustion (`stopped_burning`)
- Déclenché lorsque le joueur cesse de brûler.
- Variables :
  - (aucune)

## Sur début de noyade (`started_drowning`)
- Déclenché lorsque le joueur commence à subir des dégâts de noyade.
- Variables :
  - (aucune)

## Sur changement de position (`position_changed`)
- Déclenché chaque fois que la position du joueur en blocs change.
- Variables :
  - `$$old_pos_x` – ancien X du bloc
  - `$$old_pos_y` – ancien Y du bloc
  - `$$old_pos_z` – ancien Z du bloc
  - `$$new_pos_x` – nouveau X du bloc
  - `$$new_pos_y` – nouveau Y du bloc
  - `$$new_pos_z` – nouveau Z du bloc

## Sur début de course (`started_running`)
- Déclenché lorsque le joueur commence à sprinter.
- Variables :
  - (aucune)

## Sur fin de course (`stopped_running`)
- Déclenché lorsque le joueur cesse de sprinter.
- Variables :
  - (aucune)

## Sur saut (`jump`)
- Déclenché chaque fois que le joueur saute.
- Variables :
  - (aucune)

## Sur connexion au serveur (`server_joined`)
- Déclenché après une connexion réussie à un serveur multijoueur.
- Variables :
  - `$$server_ip` – adresse du serveur rejoint

## Sur départ du serveur (`server_left`)
- Déclenché après la déconnexion d’un serveur multijoueur.
- Variables :
  - `$$server_ip` – adresse du serveur quitté

## Monde solo entré (`world_entered`)
- Déclenché après le chargement complet d’un monde solo et le retour du contrôle.
- Variables :
  - `$$world_name` – nom affiché
  - `$$world_save_path` – dossier de sauvegarde absolu
  - `$$world_difficulty` – clé de difficulté
  - `$$world_cheats_allowed` – TRUE si les triches sont activées
  - `$$world_icon_path` – chemin absolu de l’icône
  - `$$world_is_first_join` – TRUE lors de la toute première visite

## Monde solo quitté (`world_left`)
- Déclenché après la fermeture d’un monde solo et la fin de l’enregistrement.
- Variables :
  - `$$world_name`
  - `$$world_save_path`
  - `$$world_difficulty`
  - `$$world_cheats_allowed`
  - `$$world_icon_path`

## Sur autre joueur ayant rejoint le monde/serveur (`other_player_joined_world`)
- Déclenché lorsqu’un autre joueur rejoint le monde/serveur actuel.
- Variables :
  - `$$player_name` – nom du joueur rejoignant
  - `$$player_uuid` – UUID

## Sur autre joueur ayant quitté le monde/serveur (`other_player_left_world`)
- Déclenché lorsqu’un autre joueur quitte le monde/serveur actuel.
- Variables :
  - `$$player_name`
  - `$$player_uuid`

## Sur mort d’un autre joueur (`other_player_died`)
- Déclenché lorsqu’un autre joueur du monde actuel meurt.
- Variables :
  - `$$player_name`
  - `$$player_uuid`
  - `$$death_pos_x`
  - `$$death_pos_y`
  - `$$death_pos_z`

## Sur ramassage d’objet (`item_picked_up`)
- Déclenché lorsque le joueur ramasse une entité objet.
- Variables :
  - `$$item_key` – emplacement de ressource de l’objet ramassé

## Sur objet jeté (`item_dropped`)
- Déclenché lorsque le joueur jette un objet depuis son inventaire.
- Variables :
  - `$$item_key` – emplacement de ressource de l’objet jeté

## Sur consommation d’objet (`item_consumed`)
- Déclenché lorsque le joueur termine de consommer un objet.
- Variables :
  - `$$item_key` – objet consommé

## Sur objet survolé dans l’inventaire (`item_hovered_in_inventory`)
- Déclenché lorsque l’utilisateur survole un objet dans n’importe quel écran d’inventaire.
- Variables :
  - `$$item_key` – emplacement de ressource de l’objet survolé
  - `$$item_display_name_string` – nom d’affichage en texte brut de l’objet
  - `$$item_display_name_json` – nom d’affichage de l’objet en composant JSON

## Sur utilisation d’objet (`item_used`)
- Déclenché lorsque le joueur utilise un objet.
- Variables :
  - `$$item_key` – objet utilisé
  - `$$used_on_type` – block/entity/self/none
  - `$$used_on_entity_key` – type d’entité ciblée ou vide
  - `$$used_on_block_key` – bloc ciblé ou vide
  - `$$target_pos_x` – X cible ou -1
  - `$$target_pos_y` – Y cible ou -1
  - `$$target_pos_z` – Z cible ou -1

## Sur objet cassé (`item_broke`)
- Déclenché lorsqu’un objet dans l’inventaire du joueur se casse.
- Variables :
  - `$$item_key` – objet cassé
  - `$$item_type` – tool/armor/other
