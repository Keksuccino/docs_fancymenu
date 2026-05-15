---
title: Écouteurs
description: Comment créer et utiliser des écouteurs dans FancyMenu.
---

# Écouteurs

À partir de FancyMenu v3.8.0, une nouvelle fonctionnalité appelée « écouteurs » a été ajoutée.

Les écouteurs exécutent des scripts d’actions lorsque des événements spécifiques du client ou du gameplay se produisent.
Ils peuvent exposer des variables aux actions, aux placeholders et aux conditions imbriqués dans l’écouteur.

Contrairement à la plupart des éléments de FancyMenu, les écouteurs ne sont pas liés à un écran ou à un overlay. Ils s’exécutent en continu en arrière-plan et écoutent leurs événements. Dès qu’un écouteur est déclenché, il exécute son script d’actions, même si aucun écran n’est ouvert à ce moment-là.

# Utiliser les écouteurs

Pour créer un nouvel écouteur qui écoute un événement et exécute un script d’actions, cliquez sur **barre de menu -> Personnalisation -> Gérer les écouteurs** pendant que vous n’êtes **PAS** dans l’éditeur de disposition. Vous y trouverez une interface simple pour créer et gérer des écouteurs.

<img src="https://github.com/Keksuccino/FancyMenu/blob/master/assets/docs/manage_listeners.png?raw=true" alt="Gérer les écouteurs" style="max-width:800px;width:100%;height:auto;">

# Variables des écouteurs

Les écouteurs exposent souvent un type spécial de variables pour leurs actions, conditions et placeholders imbriqués.
Ces variables peuvent être utilisées comme des placeholders (elles en sont, en pratique).

Pour les utiliser, il suffit d’employer leur nom avec le préfixe `$$` dans les champs de texte, de la même façon qu’un placeholder normal.

Par exemple, si vous utilisez l’écouteur **À l’appui d’une touche du clavier** et que vous souhaitez afficher le nom de la touche dans le journal via l’action **Imprimer dans le journal**, vous pouvez utiliser quelque chose comme `Touche appuyée ! La touche est : $$key_name` comme message à afficher par l’action. Le placeholder de variable sera ensuite remplacé par le nom réel de la touche.

> Même si elles sont appelées « variables », elles n’ont aucun lien avec le [système de variables](/variables) normal de FancyMenu. Vous ne pouvez pas définir ces variables, car elles sont **en lecture seule**. Vous ne pouvez pas non plus utiliser les actions, conditions et placeholders destinés au système de variables de FancyMenu avec ces variables spéciales d’écouteur ; ainsi, **Get Variable Value [FM Variable]**, **Is Variable Value [FM Variable]** ou **Set Variable Value [FM Variable]** ne fonctionneront pas avec les variables d’écouteur.
{.is-warning}

# Écouteurs en détail

Cette liste devrait inclure la plupart, sinon la totalité, des écouteurs de FancyMenu. Il est possible que la liste ne soit pas toujours à jour en raison des mises à jour du mod.

## Au clic sur un texte Markdown
- Se déclenche lorsqu’un texte Markdown avec un événement `click:` est cliqué, par exemple `[Open](click:open_menu)`.
- Variables :
  - `$$text_event_id` – ID de l’événement depuis le lien Markdown

## Au survol d’un texte Markdown
- Se déclenche lorsqu’un texte Markdown avec un événement `hover:` est survolé, par exemple `[Hint](hover:show_hint)`.
- Variables :
  - `$$text_event_id` – ID de l’événement depuis le lien Markdown

## À l’extraction d’un ZIP via une action
- Se déclenche lorsque l’action **Extraire le fichier ZIP dans le répertoire du jeu** se termine.
- Variables :
  - `$$source_zip_path` – chemin source du ZIP résolu
  - `$$target_folder_path` – chemin de destination de l’extraction résolu
  - `$$extract_succeeded` – true/false
  - `$$failure_reason` – texte d’erreur si l’extraction a échoué

## À l’apparition d’un élément
- Se déclenche lorsqu’un élément est généré via une action ou un flux d’apparition d’élément scripté.
- Variables :
  - `$$element_type` – type d’élément généré
  - `$$element_identifier` – identifiant de l’élément généré
  - `$$target_screen` – identifiant de l’écran cible

## Au démarrage d’une texture animée
- Se déclenche lorsqu’une texture animée commence à jouer.
- Variables :
  - `$$texture_source` – source de la texture
  - `$$texture_source_type` – type de source
  - `$$texture_will_restart` – true/false

## À la fin de lecture d’une texture animée
- Se déclenche lorsqu’une texture animée termine sa lecture.
- Variables :
  - `$$texture_source`
  - `$$texture_source_type`
  - `$$texture_will_restart`

## Au changement d’état de lecture d’une vidéo
- Se déclenche lorsqu’un élément vidéo ou l’arrière-plan vidéo du menu change d’état de lecture.
- Variables :
  - `$$video_source` – source de la vidéo
  - `$$video_source_type` – type de source
  - `$$is_looping` – true/false
  - `$$new_status` – `PLAYING`, `STOPPED`, `PAUSED`, ou `FINISHED`

## À la réception d’un message système dans le chat
- Se déclenche lorsque le client reçoit un message de chat système, comme un retour de commande.
- Variables :
  - `$$system_message_string` – message en texte brut
  - `$$system_message_component` – composant JSON

## À la réception de données FM
- Se déclenche lorsqu’un serveur envoie des données FM à ce client via `/fmdata send`.
- Variables :
  - `$$data_identifier` – identifiant des données
  - `$$data` – charge utile des données
  - `$$sent_by` – IP du serveur ou `integrated_server`

## À la connexion à un serveur distant
- Se déclenche lorsque FancyMenu initialise une connexion à un serveur distant.
- Variables :
  - `$$request_id` – ID de requête mis en cache
  - `$$remote_server_url` – URL du serveur distant

## À la réception de données d’un serveur distant
- Se déclenche lorsque des données textuelles sont reçues d’un serveur distant connecté.
- Variables :
  - `$$request_id` – ID de requête
  - `$$remote_server_url` – URL du serveur distant
  - `$$data` – charge utile reçue

## À la fermeture de la connexion à un serveur distant
- Se déclenche lorsqu’une connexion à un serveur distant se ferme.
- Variables :
  - `$$request_id` – ID de requête
  - `$$remote_server_url` – URL du serveur distant
  - `$$intentionally_closed` – TRUE si fermé par une action
  - `$$crashed` – TRUE si la connexion s’est arrêtée de façon inattendue
  - `$$unknown_close_reason` – TRUE si aucune raison de fermeture connue n’était disponible

## À l’appui d’une touche du clavier
- Se déclenche chaque fois qu’une touche est pressée (se répète tant qu’elle est maintenue ; fonctionne dans les écrans et en jeu).
- Variables :
  - `$$key_name` – nom affiché de la touche
  - `$$key_keycode` – code de touche GLFW
  - `$$key_scancode` – code de balayage GLFW
  - `$$key_modifiers` – masque binaire des modificateurs actifs

## Au relâchement d’une touche du clavier
- Se déclenche lorsqu’une touche est relâchée (écrans et en jeu).
- Variables :
  - `$$key_name`
  - `$$key_keycode`
  - `$$key_scancode`
  - `$$key_modifiers`

## À la saisie d’un caractère au clavier dans un écran
- Se déclenche lorsqu’un caractère est saisi alors qu’un écran est ouvert.
- Variables :
  - `$$char` – caractère saisi

## Au déplacement de la souris dans un écran
- Se déclenche chaque fois que la souris bouge pendant qu’un écran est ouvert.
- Variables :
  - `$$mouse_pos_x` – X actuel
  - `$$mouse_pos_y` – Y actuel
  - `$$mouse_move_delta_x` – variation en X depuis le dernier événement
  - `$$mouse_move_delta_y` – variation en Y depuis le dernier événement

## Au clic sur un bouton de la souris
- Se déclenche lorsqu’un bouton de la souris est pressé (écrans et en jeu).
- Variables :
  - `$$button` – gauche/droite/milieu
  - `$$mouse_pos_x` – X actuel
  - `$$mouse_pos_y` – Y actuel

## Au relâchement d’un bouton de la souris
- Se déclenche lorsqu’un bouton de la souris est relâché (écrans et en jeu).
- Variables :
  - `$$button`
  - `$$mouse_pos_x`
  - `$$mouse_pos_y`

## Au défilement de la souris dans un écran
- Se déclenche lorsque la molette de la souris est utilisée alors qu’un écran est ouvert.
- Variables :
  - `$$scroll_delta_y` – quantité de défilement vertical

## À l’ouverture d’un écran
- S’exécute juste après qu’un écran devient actif ; peut être utilisé pour le remplacer.
- Variables :
  - `$$screen_identifier` – identifiant de l’écran ouvert

## À la fermeture d’un écran
- S’exécute immédiatement après la fermeture d’un écran.
- Variables :
  - `$$screen_identifier` – identifiant de l’écran fermé

## À la sortie de Minecraft
- Se déclenche une fois lorsque le client commence à s’arrêter.
- Variables :
  - `$$timestamp_millis` – millis epoch au moment de la sortie
  - `$$timestamp_iso` – horodatage ISO-8601 du moment de sortie

## À la mort
- S’exécute lorsque l’écran de mort vanilla s’ouvre pour le joueur local.
- Variables :
  - `$$days_survived` – jours écoulés depuis la dernière mort
  - `$$death_reason_string` – cause en texte brut
  - `$$death_reason_component` – cause en composant JSON
  - `$$death_pos_x` – coordonnée X de la mort
  - `$$death_pos_y` – coordonnée Y de la mort
  - `$$death_pos_z` – coordonnée Z de la mort

## À la mise à jour d’une variable [FM Variable]
- Se déclenche chaque fois qu’une variable FancyMenu est définie ou mise à jour.
- Variables :
  - `$$var_name` – nom de la variable
  - `$$old_value` – valeur précédente
  - `$$new_value` – nouvelle valeur

## Au téléchargement d’un fichier via une action
- Se déclenche après la fin de l’action « Télécharger un fichier dans le répertoire du jeu ».
- Variables :
  - `$$download_url` – source du téléchargement
  - `$$target_file_path` – chemin du fichier enregistré
  - `$$download_succeeded` – true/false

## À la sélection d’un fichier
- Se déclenche après l’exécution de l’action « Sélectionner un fichier ».
- Variables :
  - `$$selected_file_path` – chemin absolu du fichier choisi ou vide si annulé
  - `$$target_file_path` – chemin résolu dans l’instance
  - `$$selection_succeeded` – true si la copie a réussi
  - `$$selection_cancelled` – true si la boîte de dialogue a été fermée
  - `$$failure_reason` – informations d’erreur en cas d’échec

## À la réception d’un message de chat
- Se déclenche lorsqu’une ligne de chat normal d’un joueur apparaît sur le client.
- Variables :
  - `$$chat_message_string` – ligne en texte brut
  - `$$chat_message_component` – composant JSON complet
  - `$$sender_uuid` – UUID de l’expéditeur ou ERROR
  - `$$sender_name` – nom de l’expéditeur ou ERROR

## À l’envoi d’un message de chat
- Se déclenche lorsque le joueur local envoie un message de chat.
- Variables :
  - `$$chat_message_string` – ligne en texte brut
  - `$$chat_message_component` – composant JSON complet

## À l’obtention d’un effet
- Se déclenche lorsque le joueur gagne un effet de statut.
- Variables :
  - `$$effect_key` – emplacement de ressource de l’effet
  - `$$effect_type` – positif/négatif/neutre
  - `$$effect_duration` – ticks restants

## À la perte d’un effet
- Se déclenche lorsque le joueur perd un effet de statut.
- Variables :
  - `$$effect_key` – effet expiré
  - `$$effect_type` – catégorie

## Au changement d’expérience
- Se déclenche chaque fois que l’XP totale du joueur change.
- Variables :
  - `$$new_experience_amount` – après le changement
  - `$$old_experience_amount` – avant le changement
  - `$$is_level_up` – TRUE si le niveau a augmenté

## Aux dégâts subis
- Se déclenche une fois par coup lorsque le joueur subit des dégâts.
- Variables :
  - `$$damage_amount` – points de vie retirés
  - `$$damage_type` – emplacement de ressource du type de dégâts
  - `$$is_fatal_damage` – TRUE si mortel
  - `$$damage_source` – emplacement de ressource de l’attaquant ou NONE

## Au début du gel
- Se déclenche lorsque le joueur commence à geler.
- Variables :
  - `$$freezing_intensity` – 0.0 aucun gel, 1.0 complètement gelé

## À l’arrêt du gel
- Se déclenche lorsque le joueur cesse de geler.
- Variables :
  - (aucune)

## Au gel complet
- Se déclenche une fois lorsque le joueur devient complètement gelé.
- Variables :
  - (aucune)

## Au début de la visée d’un bloc
- Se déclenche une fois lorsque le réticule pointe pour la première fois vers un bloc (distance max. 20 blocs).
- Variables :
  - `$$block_key` – bloc ciblé
  - `$$block_pos_x` – X du bloc
  - `$$block_pos_y` – Y du bloc
  - `$$block_pos_z` – Z du bloc
  - `$$distance_to_player` – des yeux au point d’impact

## À l’arrêt de la visée d’un bloc
- Se déclenche lorsque le réticule cesse de pointer vers un bloc (rapporte le dernier bloc ciblé, 20 blocs max).
- Variables :
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`
  - `$$distance_to_player`

## Au début de la visée d’une entité
- Se déclenche une fois lorsque le réticule pointe pour la première fois vers une entité (20 blocs max.).
- Variables :
  - `$$entity_key` – type d’entité ciblé
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## À l’arrêt de la visée d’une entité
- Se déclenche lorsque le réticule cesse de pointer vers une entité (rapporte la dernière entité ciblée, 20 blocs max.).
- Variables :
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## À l’apparition d’une entité
- **Nécessite FancyMenu sur le serveur.** Se déclenche lorsqu’une entité apparaît n’importe où dans le monde/serveur connecté.
- Variables :
  - `$$entity_key`
  - `$$distance_to_player` – −1 si dans une autre dimension
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`
  - `$$dimension_key`
  - `$$is_same_dimension_as_player`

## À la mort d’une entité
- **Nécessite FancyMenu sur le serveur.** Se déclenche lorsqu’une entité meurt dans le monde/serveur connecté.
- Variables :
  - `$$entity_key`
  - `$$distance_to_player` – −1 si dans une autre dimension
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

## Au début de l’entité visible
- Se déclenche lorsqu’une entité devient visible pour la première fois dans un rayon de 200 blocs.
- Variables :
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## À la fin de visibilité d’une entité
- Se déclenche lorsqu’une entité auparavant visible sort du champ de vision ou dépasse 200 blocs.
- Variables :
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## Lors d’une interaction avec une entité
- Se déclenche lorsque le joueur interagit avec succès avec une entité.
- Variables :
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## À la montée sur une entité
- Se déclenche lorsque le joueur commence à monter une entité.
- Variables :
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## À la descente d’une entité
- Se déclenche lorsque le joueur cesse de monter l’entité qu’il utilise actuellement.
- Variables :
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## À la casse d’un bloc
- Se déclenche lorsque le joueur casse un bloc.
- Variables :
  - `$$block_key`
  - `$$broke_with_item_key` – outil utilisé ou EMPTY
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## À la pose d’un bloc
- Se déclenche lorsque le joueur place un bloc.
- Variables :
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## Lors d’une interaction avec un bloc
- Se déclenche lorsque le joueur interagit avec succès avec un bloc.
- Variables :
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## En marchant sur un bloc
- Se déclenche lorsque le joueur monte sur un bloc.
- Variables :
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## À l’entrée dans un biome
- Se déclenche lorsque le joueur entre dans un nouveau biome.
- Variables :
  - `$$biome_key` – biome dans lequel on entre

## À la sortie d’un biome
- Se déclenche lorsque le joueur quitte son biome actuel.
- Variables :
  - `$$biome_key` – biome juste quitté

## À l’entrée dans une structure
- **Nécessite FancyMenu sur le serveur.** Détection approximative de la zone de structure ; peut se déclencher près, au-dessus ou en dessous de la structure.
- Variables :
  - `$$structure_key` – structure dans laquelle on entre

## À la sortie d’une structure
- **Nécessite FancyMenu sur le serveur.** Détection approximative ; peut se déclencher près de l’emprise de la structure.
- Variables :
  - `$$structure_key` – structure juste quittée

## À l’entrée dans une structure (haute précision)
- **Nécessite FancyMenu sur le serveur.** Se déclenche lorsque le joueur entre dans les boîtes englobantes d’une structure.
- Variables :
  - `$$structure_key`

## À la sortie d’une structure (haute précision)
- **Nécessite FancyMenu sur le serveur.** Se déclenche après que le joueur a quitté les boîtes englobantes d’une structure.
- Variables :
  - `$$structure_key`

## À l’entrée dans une dimension
- Se déclenche lorsque le joueur entre dans une nouvelle dimension.
- Variables :
  - `$$dimension_key` – dimension dans laquelle on entre

## Au début de la nage
- Se déclenche lorsque le joueur commence à nager.
- Variables :
  - `$$fluid_type` – emplacement de ressource du fluide

## À l’arrêt de la nage
- Se déclenche lorsque le joueur arrête de nager.
- Variables :
  - `$$fluid_type` – fluide dans lequel la nage s’est arrêtée

## Au début du contact avec un fluide
- Se déclenche lorsque le joueur commence à toucher un fluide.
- Variables :
  - `$$fluid_type` – fluide touché

## À l’arrêt du contact avec un fluide
- Se déclenche lorsque le joueur ne touche plus un fluide.
- Variables :
  - `$$fluid_type` – fluide qui n’est plus touché

## Au démarrage d’une piste musicale
- Se déclenche lorsqu’une nouvelle piste musicale commence.
- Variables :
  - `$$track_resource_location` – fichier audio
  - `$$track_display_name` – nom lisible par l’humain ou UNKNOWN
  - `$$track_artist` – artiste ou UNKNOWN
  - `$$track_duration_ms` – millisecondes (0 si inconnu)

## À l’arrêt d’une piste musicale
- Se déclenche lorsque la piste musicale en cours se termine ou est remplacée.
- Variables :
  - `$$track_resource_location`
  - `$$track_display_name`
  - `$$track_artist`
  - `$$track_duration_ms`

## Au déclenchement d’un son du monde
- Se déclenche lorsqu’un son positionnel du monde commence près du joueur.
- Variables :
  - `$$sound_resource_location` – fichier sonore
  - `$$sound_display_name` – nom du sous-titre quand disponible
  - `$$sound_origin_pos_x`
  - `$$sound_origin_pos_y`
  - `$$sound_origin_pos_z`
  - `$$sound_origin_distance_to_player`
  - `$$sound_origin_direction_from_player` – degrés 0–360 par rapport à l’orientation

## Au changement de météo
- Se déclenche lorsque la météo change globalement ou localement (un changement de biome ou l’entrée à l’intérieur peut le redéclencher).
- Variables :
  - `$$weather_type` – clear/rain/thunder
  - `$$weather_can_snow` – TRUE si la neige s’affiche
  - `$$weather_can_rain` – TRUE si la pluie s’affiche

## Au début de la combustion
- Se déclenche lorsque le joueur commence à brûler.
- Variables :
  - (aucune)

## À l’arrêt de la combustion
- Se déclenche lorsque le joueur cesse de brûler.
- Variables :
  - (aucune)

## Au début de la noyade
- Se déclenche lorsque le joueur commence à subir des dégâts de noyade.
- Variables :
  - (aucune)

## Au changement de position
- Se déclenche chaque fois que la position du joueur en blocs change.
- Variables :
  - `$$old_pos_x` – ancien X du bloc
  - `$$old_pos_y` – ancien Y du bloc
  - `$$old_pos_z` – ancien Z du bloc
  - `$$new_pos_x` – nouveau X du bloc
  - `$$new_pos_y` – nouveau Y du bloc
  - `$$new_pos_z` – nouveau Z du bloc

## Au début de la course
- Se déclenche lorsque le joueur commence à sprinter.
- Variables :
  - (aucune)

## À l’arrêt de la course
- Se déclenche lorsque le joueur arrête de sprinter.
- Variables :
  - (aucune)

## Au saut
- Se déclenche chaque fois que le joueur saute.
- Variables :
  - (aucune)

## À la connexion à un serveur
- Se déclenche après avoir rejoint avec succès un serveur multijoueur.
- Variables :
  - `$$server_ip` – adresse du serveur rejoint

## À la déconnexion d’un serveur
- Se déclenche après la déconnexion d’un serveur multijoueur.
- Variables :
  - `$$server_ip` – adresse du serveur quitté

## Entrée dans un monde solo
- Se déclenche après le chargement complet d’un monde solo et le retour du contrôle.
- Variables :
  - `$$world_name` – nom affiché
  - `$$world_save_path` – dossier de sauvegarde absolu
  - `$$world_difficulty` – clé de difficulté
  - `$$world_cheats_allowed` – TRUE si les triches sont activées
  - `$$world_icon_path` – chemin absolu de l’icône
  - `$$world_is_first_join` – TRUE lors de la toute première visite

## Sortie d’un monde solo
- Se déclenche après la fermeture et la fin de l’enregistrement d’un monde solo.
- Variables :
  - `$$world_name`
  - `$$world_save_path`
  - `$$world_difficulty`
  - `$$world_cheats_allowed`
  - `$$world_icon_path`

## Lorsqu’un autre joueur rejoint le monde/serveur
- Se déclenche lorsqu’un autre joueur rejoint le monde/serveur actuel.
- Variables :
  - `$$player_name` – nom du joueur qui rejoint
  - `$$player_uuid` – UUID

## Lorsqu’un autre joueur quitte le monde/serveur
- Se déclenche lorsqu’un autre joueur quitte le monde/serveur actuel.
- Variables :
  - `$$player_name`
  - `$$player_uuid`

## À la mort d’un autre joueur
- Se déclenche lorsqu’un autre joueur du monde actuel meurt.
- Variables :
  - `$$player_name`
  - `$$player_uuid`
  - `$$death_pos_x`
  - `$$death_pos_y`
  - `$$death_pos_z`

## À la récupération d’un objet
- Se déclenche lorsque le joueur ramasse une entité objet.
- Variables :
  - `$$item_key` – emplacement de ressource de l’objet ramassé

## Au dépôt d’un objet
- Se déclenche lorsque le joueur jette un objet depuis son inventaire.
- Variables :
  - `$$item_key` – emplacement de ressource de l’objet jeté

## À la consommation d’un objet
- Se déclenche lorsque le joueur termine de consommer un objet.
- Variables :
  - `$$item_key` – objet consommé

## Au survol d’un objet dans l’inventaire
- Se déclenche lorsque l’utilisateur survole un objet dans n’importe quel écran d’inventaire.
- Variables :
  - `$$item_key` – emplacement de ressource de l’objet survolé
  - `$$item_display_name_string` – nom d’affichage en texte brut de l’objet
  - `$$item_display_name_json` – nom d’affichage de l’objet en composant JSON

## À l’utilisation d’un objet
- Se déclenche lorsque le joueur utilise un objet.
- Variables :
  - `$$item_key` – objet utilisé
  - `$$used_on_type` – bloc/entité/soi-même/aucun
  - `$$used_on_entity_key` – type d’entité ciblée ou vide
  - `$$used_on_block_key` – bloc ciblé ou vide
  - `$$target_pos_x` – X cible ou -1
  - `$$target_pos_y` – Y cible ou -1
  - `$$target_pos_z` – Z cible ou -1

## À la casse d’un objet
- Se déclenche lorsqu’un objet de l’inventaire du joueur se casse.
- Variables :
  - `$$item_key` – objet cassé
  - `$$item_type` – tool/armor/other
