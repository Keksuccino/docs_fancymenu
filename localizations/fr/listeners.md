---
title: Déclencheurs
description: >-
  Exécutez des scripts d’action lorsqu’un événement se produit dans le jeu,
  comme l’appui sur une touche, la réception d’un message dans le chat ou le
  déblocage d’un nouveau haut fait.
sourceBlobSha: b8417f6287ac413d2d44e0fc5c2383c0b0fa6e1e
---

# Déclencheurs

Les déclencheurs exécutent un [script d’action](/action-scripts) lorsqu’un événement se produit dans le jeu : une touche est enfoncée, un écran s’ouvre, vous débloquez un haut fait, et bien plus encore. Ils fonctionnent dans tous les menus et pendant le jeu, et ne sont associés à aucune disposition.

La plupart des déclencheurs fournissent également à leur script des variables décrivant l’événement, comme le nom de la touche enfoncée.

<img width="800" alt="Appui sur des touches dans l’écran titre, avec une notification affichant le nom de chaque touche enfoncée" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/listeners_trigger.gif?raw=true">

> [!CAUTION]
> Un déclencheur peut exécuter des actions sur des fichiers, le réseau, des commandes, le presse-papiers, des packs de ressources et des liens même lorsqu’aucun menu n’est ouvert. N’utilisez que des déclencheurs provenant de profils et de fichiers de personnes de confiance.

# Ajouter un déclencheur

<img width="800" alt="Ouverture de Gérer les déclencheurs, ajout d’un déclencheur À l’appui sur une touche du clavier avec une action Afficher une notification, puis appui sur H pour le tester" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/listeners_make.gif?raw=true">

1. Ouvrez **barre de menu -> Personnalisation -> Gérer les déclencheurs**.
2. Cliquez sur **Ajouter un déclencheur**.
3. Cliquez sur l’événement dans **Déclencheurs disponibles**. La barre de recherche permet de trouver les déclencheurs par leur nom et leur description.
   - **Description du déclencheur** indique son fonctionnement et les variables qu’il fournit.
   - **Copier les variables dans le presse-papiers** copie le nom de ses variables.
   - **Détacher la description** ouvre la description dans une fenêtre séparée.
4. Cliquez sur **Terminé**, ou double-cliquez sur le déclencheur. L’éditeur de scripts d’action s’ouvre.
5. Ajoutez les actions à exécuter, puis cliquez sur **Terminé**. Consultez la page [Scripts d’action](/action-scripts#making-an-action-script).
6. Cliquez sur **Terminé** dans **Gérer les déclencheurs** pour enregistrer. Le déclencheur fonctionne immédiatement.

**Annuler** abandonne toutes les modifications apportées dans **Gérer les déclencheurs**, après vous avoir demandé confirmation.

# Gérer les déclencheurs

<img width="800" alt="Fenêtre Gérer les déclencheurs affichant cinq déclencheurs, dont un sélectionné avec son script d’action à droite" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/listeners_manage.png?raw=true">

- Cliquez sur un déclencheur pour afficher son type et son script d’action à droite.
- **Modifier les actions**, ou un clic droit sur un déclencheur, ouvre son script d’action.
- Double-cliquez sur le nom d’un déclencheur pour le renommer, par exemple `Help Key`. Appuyez sur `Entrée` pour enregistrer le nom, ou sur `Échap` pour annuler. Si le nom est vide, le type du déclencheur s’affiche à nouveau.
- **Supprimer le déclencheur** supprime le déclencheur sélectionné.
- **Exporter pour l’IA** copie le déclencheur sélectionné ou tous les déclencheurs pour une [conversation avec une IA](/export-for-ai), avec les modifications non enregistrées.

Les déclencheurs sont enregistrés dans `config/fancymenu/listener_instances.txt` (voir [Emplacements de stockage des données](/data-storage-locations)). Chaque [profil](/profiles) possède ses propres déclencheurs.

# Variables des déclencheurs

Les variables d’un déclencheur commencent par `$$` et sont utilisables partout dans son script : dans chaque valeur d’action et dans les conditions des [instructions IF](/action-scripts#if-else-if-and-else). Les majuscules et les minuscules sont importantes. Les variables de chaque déclencheur sont répertoriées ci-dessous, ainsi que dans sa description dans le sélecteur de déclencheurs.

<img width="800" alt="Sélecteur de déclencheurs avec À la réception d’un haut fait sélectionné et sa description listant ses variables" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/listeners_choose.png?raw=true">

Par exemple, ce déclencheur ouvre un écran d’aide lorsque vous appuyez sur `H` :

1. Ajoutez un déclencheur **À l’appui sur une touche du clavier**.
2. Dans son script, utilisez **Ajouter une instruction IF** avec la condition [**Est du texte**](/conditions#is-text). Réglez **Mode de comparaison** sur **Égal à**, **Texte** sur `$$key_name` et **Comparer au texte** sur `H`.
3. Dans le bloc IF, ajoutez [**Ouvrir un écran ou une interface personnalisée**](/action-scripts#open-screen-or-custom-gui) avec votre écran d’aide.

À propos des variables des déclencheurs :

- Les variables des déclencheurs sont toujours du texte. Lorsqu’un déclencheur ne parvient pas à déterminer une valeur, la variable reçoit une valeur de remplacement, par exemple `ERROR`, `UNKNOWN`, `NONE`, `EMPTY`, `0`, `-1` ou rien.
- Les variables des déclencheurs sont renseignées avant les [espaces réservés](/placeholders) : elles fonctionnent donc aussi à l’intérieur de ceux-ci.
- Les variables des déclencheurs n’existent que pendant l’exécution de leur script. Pour conserver une valeur, enregistrez-la dans l’une de vos [variables](/variables) à l’aide de [**Définir la valeur d’une variable (variable FM)**](/action-scripts#set-variable-value-fm-variable).
- Vos propres variables, créées via **barre de menu -> Personnalisation -> Gérer les variables**, fonctionnent aussi dans les scripts de déclencheurs : utilisez `$$` suivi de leur nom, comme `$$coins`. Si l’une d’elles porte le même nom qu’une variable de déclencheur, `$$name` désigne la variable du déclencheur. Vos variables aux noms plus longs, comme `key_name_log`, fonctionnent toujours.
- Le texte provenant du chat, des serveurs, des fichiers et d’autres joueurs peut contenir n’importe quoi. Ne l’insérez jamais directement dans des commandes, des chemins de fichiers ou des liens.

# Bon à savoir

- Certains déclencheurs nécessitent que FancyMenu soit installé sur le serveur. Cela est indiqué ci-dessous. En solo, ils fonctionnent toujours.
- Certains déclencheurs se déclenchent très souvent, comme **Au déplacement de la souris dans un écran**, **Au défilement d’un élément**, **Au changement de position** et **Au déclenchement d’un son du monde**. Gardez leurs scripts courts et n’y utilisez jamais d’actions lentes comme [**Recharger FancyMenu**](/action-scripts#reload-fancymenu).
- Pour remplacer un écran avec **À l’ouverture d’un écran**, vérifiez d’abord `$$screen_identifier` avec une instruction IF. Sinon, tous les écrans seront remplacés, y compris celui que vous ouvrez.

# Tous les déclencheurs

Tous les déclencheurs disponibles dans FancyMenu, classés selon l’événement auquel ils réagissent.

## Clavier et souris

Pour vérifier quelle touche a été utilisée, consultez `$$key_name`. Les codes numériques des touches ne sont pas identiques dans toutes les versions de Minecraft.

### À l’appui sur une touche du clavier

**Identifiant :** `keyboard_key_pressed`

Se déclenche lorsqu’une touche est enfoncée, dans les menus comme pendant le jeu. Tant que la touche reste enfoncée, il se déclenche encore et encore.

- `$$key_name` : nom de la touche, par exemple `H` ou `Left Shift`
- `$$key_keycode` : code numérique de la touche
- `$$key_scancode` : code de balayage de la touche
- `$$key_modifiers` : nombre correspondant aux touches de modification enfoncées en même temps, comme `Shift` et `Ctrl`

### Au relâchement d’une touche du clavier

**Identifiant :** `keyboard_key_released`

Se déclenche lorsqu’une touche est relâchée, dans les menus comme pendant le jeu.

Fournit les mêmes variables que **À l’appui sur une touche du clavier** : `$$key_name`, `$$key_keycode`, `$$key_scancode` et `$$key_modifiers`.

### À la saisie d’un caractère dans un écran

**Identifiant :** `keyboard_char_typed`

Se déclenche pour chaque caractère saisi lorsqu’un écran est ouvert.

- `$$char` : le caractère saisi

### Au déplacement de la souris dans un écran

**Identifiant :** `mouse_moved`

Se déclenche à chaque déplacement de la souris lorsqu’un écran est ouvert.

- `$$mouse_pos_x`, `$$mouse_pos_y` : position de la souris, en pixels de l’interface
- `$$mouse_move_delta_x`, `$$mouse_move_delta_y` : distance parcourue depuis le dernier déplacement

### Au clic sur un bouton de la souris

**Identifiant :** `mouse_button_clicked`

Se déclenche une fois lorsqu’un bouton de la souris est enfoncé, dans les menus comme pendant le jeu.

- `$$button` : `left`, `right` ou `middle`. Les autres boutons renvoient leur numéro.
- `$$mouse_pos_x`, `$$mouse_pos_y` : position de la souris, en pixels de l’interface

### Au relâchement d’un bouton de la souris

**Identifiant :** `mouse_button_released`

Se déclenche une fois lorsqu’un bouton de la souris est relâché, dans les menus comme pendant le jeu.

Fournit les mêmes variables que **Au clic sur un bouton de la souris** : `$$button`, `$$mouse_pos_x` et `$$mouse_pos_y`.

### Au défilement de la souris dans un écran

**Identifiant :** `mouse_scrolled`

Se déclenche lorsque la molette de la souris tourne alors qu’un écran est ouvert.

- `$$scroll_delta_y` : distance parcourue par la molette. Supérieure à `0` lors d’un défilement vers le haut, inférieure à `0` lors d’un défilement vers le bas.

## Écrans et éléments

### À l’ouverture d’un écran

**Identifiant :** `screen_open`

Se déclenche juste après l’ouverture d’un écran. Une action [**Ouvrir un écran ou une interface personnalisée**](/action-scripts#open-screen-or-custom-gui) dans son script peut remplacer l’écran par un autre.

- `$$screen_identifier` : l’[identifiant](/screen-identifiers) de l’écran

### À la fermeture d’un écran

**Identifiant :** `screen_close`

Se déclenche juste après la fermeture d’un écran.

- `$$screen_identifier` : l’[identifiant](/screen-identifiers) de l’écran fermé

### Au clic sur un texte Markdown

**Identifiant :** `text_clicked`

Se déclenche lorsque quelqu’un clique sur un [événement de clic](/text-formatting#click-and-hover-events) dans un texte, comme `[Lire le règlement](click:open_rules)`.

- `$$text_event_id` : l’identifiant de l’événement, par exemple `open_rules`

### Au survol d’un texte Markdown

**Identifiant :** `text_hovered`

Se déclenche lorsque la souris passe sur un [événement de survol](/text-formatting#click-and-hover-events) dans un texte, comme `[Qu’est-ce que c’est ?](hover:show_hint)`.

- `$$text_event_id` : l’identifiant de l’événement, par exemple `show_hint`

### Au défilement d’un élément

**Identifiant :** `scroll_area_scrolled`

Se déclenche à chaque déplacement du contenu d’une [zone défilante](/scrollable-areas) ou d’un [élément de texte](/text-in-menus). Pendant le défilement inertiel du contenu, il se déclenche à chaque image. Il ne se déclenche pas dans l’éditeur de disposition.

- `$$element_identifier` : l’[identifiant](/element-identifiers) de l’élément
- `$$scroll_x` : distance de défilement horizontal du contenu, en pixels
- `$$scroll_y` : distance de défilement vertical du contenu, en pixels
- `$$scroll_percent` : distance de défilement du contenu dans la direction principale de l’élément, de `0` (début) à `100` (fin)

### Quand un élément est ramené au début

**Identifiant :** `scroll_area_reached_start`

Se déclenche lorsque le contenu d’une zone défilante ou d’un élément de texte revient à son début.

Fournit les mêmes variables que **Au défilement d’un élément** : `$$element_identifier`, `$$scroll_x`, `$$scroll_y` et `$$scroll_percent`.

### Quand un élément atteint la fin du défilement

**Identifiant :** `scroll_area_reached_end`

Se déclenche lorsque le contenu d’une zone défilante ou d’un élément de texte atteint sa fin, par exemple lorsque quelqu’un a parcouru tout le règlement.

Fournit les mêmes variables que **Au défilement d’un élément** : `$$element_identifier`, `$$scroll_x`, `$$scroll_y` et `$$scroll_percent`.

### Au démarrage d’une texture animée

**Identifiant :** `animated_texture_started_playing`

Se déclenche lorsqu’une [texture animée](/animations) (GIF, APNG ou FMA) commence à être lue, puis à chaque redémarrage.

- `$$texture_source` : origine de la texture : chemin de fichier, lien Web ou emplacement de ressource
- `$$texture_source_type` : `LOCAL`, `WEB` ou `RESOURCE_LOCATION`
- `$$texture_will_restart` : `true` si elle redémarre après cette lecture, sinon `false`

### À la fin de la lecture d’une texture animée

**Identifiant :** `animated_texture_finished_playing`

Se déclenche lorsqu’une texture animée termine une lecture. En cas de boucle, il se déclenche juste avant le redémarrage.

Fournit les mêmes variables que **Au démarrage d’une texture animée** : `$$texture_source`, `$$texture_source_type` et `$$texture_will_restart`.

### Au changement de l’état de lecture d’une vidéo

**Identifiant :** `video_playback_status_changed`

Se déclenche lorsqu’un élément [vidéo](/video) ou un arrière-plan de menu démarre, se met en pause, s’arrête ou se termine.

- `$$video_source` : origine de la vidéo : chemin de fichier, lien Web ou emplacement de ressource
- `$$video_source_type` : `LOCAL`, `WEB` ou `RESOURCE_LOCATION`
- `$$is_looping` : `true` si la vidéo est en boucle, sinon `false`
- `$$new_status` :
  - `PLAYING` : la vidéo a démarré ou a repris la lecture
  - `PAUSED` : la vidéo a été mise en pause
  - `STOPPED` : la vidéo a été arrêtée
  - `FINISHED` : la vidéo est arrivée à la fin. Les vidéos en boucle renvoient aussi cet état juste avant de redémarrer.

## Variables, fichiers et données

### À la mise à jour d’une variable [variable FM]

**Identifiant :** `fm_variable_updated`

Se déclenche chaque fois qu’une [variable](/variables) reçoit une valeur.

- `$$var_name` : nom de la variable
- `$$old_value` : valeur précédente
- `$$new_value` : nouvelle valeur

Pour les variables de liste, les deux valeurs correspondent à la liste entière au format tableau JSON, par exemple `["Diamonds","Emeralds"]`.

### Au début du téléchargement d’un fichier via une action

**Identifiant :** `file_download_started_via_action`

Se déclenche au début d’un téléchargement lancé par [**Télécharger un fichier dans le répertoire du jeu**](/action-scripts#download-file-to-game-directory), dès que le nom du fichier est connu. Le fichier n’apparaît à son emplacement qu’une fois le téléchargement terminé ; utilisez donc **À la fin du téléchargement d’un fichier via une action** pour savoir quand il est prêt.

- `$$download_url` : lien du fichier
- `$$target_file_path` : emplacement où le fichier sera enregistré

### À la fin du téléchargement d’un fichier via une action

**Identifiant :** `file_downloaded_via_action`

Se déclenche à la fin ou en cas d’échec d’un téléchargement lancé par [**Télécharger un fichier dans le répertoire du jeu**](/action-scripts#download-file-to-game-directory).

- `$$download_url` : lien du fichier
- `$$target_file_path` : emplacement où le fichier a été enregistré. En cas d’échec du téléchargement, il peut ne s’agir que du dossier.
- `$$download_succeeded` : `true` ou `false`

### À la sélection d’un fichier

**Identifiant :** `file_selected_via_action`

Se déclenche lorsque l’action [**Sélectionner un fichier sur le système**](/action-scripts#select-file-from-system) se termine : le fichier a été copié, le sélecteur de fichiers a été fermé ou une erreur s’est produite.

- `$$selected_file_path` : chemin complet du fichier choisi. Vide si le sélecteur a été fermé.
- `$$target_file_path` : emplacement où le fichier a été copié dans le dossier du jeu
- `$$selection_succeeded` : `true` si le fichier a été copié
- `$$selection_cancelled` : `true` si le sélecteur a été fermé sans qu’un fichier soit choisi
- `$$failure_reason` : cause de l’échec. Vide si tout s’est bien passé.

### Après l’extraction d’un fichier ZIP via une action

**Identifiant :** `zip_extracted_via_action`

Se déclenche lorsque l’action [**Extraire un fichier ZIP dans le répertoire du jeu**](/action-scripts#extract-zip-file-in-game-directory) se termine.

- `$$source_zip_path` : fichier ZIP
- `$$target_folder_path` : dossier où il a été extrait
- `$$extract_succeeded` : `true` ou `false`
- `$$failure_reason` : cause de l’échec. Vide si tout s’est bien passé.

Les chemins dans le dossier du jeu commencent par `/`, par exemple `/config/fancymenu/assets/pack.zip`. Les chemins dans le dossier `.minecraft` commencent par `.minecraft/`.

### À la réception de données FM

**Identifiant :** `fm_data_received`

Se déclenche lorsque le serveur envoie des données à ce joueur avec `/fmdata send`. Consultez la page [Données FM](/fm-data).

- `$$data_identifier` : identifiant utilisé pour envoyer les données
- `$$data` : données reçues
- `$$sent_by` : adresse IP du serveur, ou `integrated_server` en solo

### À la connexion à un serveur distant

**Identifiant :** `remote_server_connected`

Se déclenche lorsqu’une [connexion à un serveur distant](/remote-server-communication) s’ouvre.

- `$$request_id` : identifiant de la requête de connexion
- `$$remote_server_url` : lien du serveur distant

### À la réception de données d’un serveur distant

**Identifiant :** `remote_server_data_received`

Se déclenche chaque fois qu’un serveur distant connecté envoie du texte.

- `$$request_id` : identifiant de la requête de connexion
- `$$remote_server_url` : lien du serveur distant
- `$$data` : texte envoyé

### À la fermeture d’une connexion à un serveur distant

**Identifiant :** `remote_server_connection_closed`

Se déclenche lorsqu’une connexion à un serveur distant est fermée.

- `$$request_id` : identifiant de la requête de connexion
- `$$remote_server_url` : lien du serveur distant
- `$$intentionally_closed` : `true` si l’action [**Fermer la connexion au serveur distant**](/action-scripts#close-remote-server-connection) a fermé la connexion
- `$$crashed` : `true` si la connexion a planté
- `$$unknown_close_reason` : `true` si la connexion a été fermée pour une raison inconnue

## Jeu, mondes et serveurs

### À la fermeture de Minecraft

**Identifiant :** `quit_minecraft`

Se déclenche une fois lorsque le jeu commence à se fermer.

- `$$timestamp_millis` : heure exprimée en millisecondes depuis 1970
- `$$timestamp_iso` : heure au format ISO-8601, par exemple `2026-11-24T18:30:00.123Z`

### À la prise d’une capture d’écran

**Identifiant :** `screenshot_taken`

Se déclenche lorsqu’une capture d’écran est prise et enregistrée, par exemple à l’aide de la touche de capture d’écran.

- `$$screenshot_path` : chemin de la capture d’écran dans le dossier du jeu, par exemple `/screenshots/2026-10-29_14.30.00.png`

### À l’entrée dans un monde solo

**Identifiant :** `world_entered`

Se déclenche lorsque le chargement d’un monde solo est terminé et que vous pouvez vous déplacer.

- `$$world_name` : nom du monde
- `$$world_save_path` : chemin complet du dossier de sauvegarde du monde
- `$$world_difficulty` : difficulté du monde
- `$$world_cheats_allowed` : `true` si les commandes de triche sont activées
- `$$world_icon_path` : chemin complet de l’icône du monde
- `$$world_is_first_join` : `true` lors de la toute première visite après la création du monde

### À la sortie d’un monde solo

**Identifiant :** `world_left`

Se déclenche lorsqu’un monde solo est fermé et sauvegardé.

Fournit les mêmes variables que **À l’entrée dans un monde solo**, sauf `$$world_is_first_join` : `$$world_name`, `$$world_save_path`, `$$world_difficulty`, `$$world_cheats_allowed` et `$$world_icon_path`.

### Au début de la connexion à un serveur

**Identifiant :** `start_joining_server`

Se déclenche lorsque le jeu commence à se connecter à un serveur ou à un Realm, avant d’y entrer. Il se déclenche également si la connexion échoue ou est annulée, ce qui permet de mémoriser le serveur, par exemple pour créer un bouton de reconnexion sur l’écran de déconnexion.

- `$$server_ip` : adresse IP du serveur

### À la connexion à un serveur

**Identifiant :** `server_joined`

Se déclenche après votre connexion à un serveur multijoueur.

- `$$server_ip` : adresse IP du serveur

### À la déconnexion d’un serveur

**Identifiant :** `server_left`

Se déclenche après votre déconnexion d’un serveur multijoueur.

- `$$server_ip` : adresse IP du serveur

### À l’arrivée d’un autre joueur dans le monde ou sur le serveur

**Identifiant :** `other_player_joined_world`

Se déclenche lorsqu’un autre joueur rejoint votre monde ou votre serveur.

- `$$player_name` : nom du joueur
- `$$player_uuid` : UUID du joueur

### Au départ d’un autre joueur du monde ou du serveur

**Identifiant :** `other_player_left_world`

Se déclenche lorsqu’un autre joueur quitte votre monde ou votre serveur.

- `$$player_name` : nom du joueur
- `$$player_uuid` : UUID du joueur

### À la mort d’un autre joueur

**Identifiant :** `other_player_died`

Se déclenche lorsqu’un autre joueur de votre monde meurt.

- `$$player_name` : nom du joueur
- `$$player_uuid` : UUID du joueur
- `$$death_pos_x`, `$$death_pos_y`, `$$death_pos_z` : position où le joueur est mort

## Chat

### À la réception d’un message dans le chat

**Identifiant :** `chat_message_received`

Se déclenche lorsqu’un message d’un joueur apparaît dans votre chat.

- `$$chat_message_string` : message en texte brut
- `$$chat_message_component` : message sous forme de composant texte JSON
- `$$sender_uuid` : UUID de l’expéditeur, ou `ERROR` s’il est inconnu
- `$$sender_name` : nom de l’expéditeur, ou `ERROR` s’il est inconnu

### À l’envoi d’un message dans le chat

**Identifiant :** `chat_message_sent`

Se déclenche lorsque vous envoyez un message dans le chat. Les commandes ne sont pas prises en compte.

- `$$chat_message_string` : message en texte brut
- `$$chat_message_component` : message sous forme de composant texte JSON

### À la réception d’un message système dans le chat

**Identifiant :** `system_message_received_in_chat`

Se déclenche lorsqu’un message qui ne provient pas d’un joueur apparaît dans votre chat, par exemple le résultat d’une commande.

- `$$system_message_string` : message en texte brut
- `$$system_message_component` : message sous forme de composant texte JSON

## Joueur

### À la mort

**Identifiant :** `player_death`

Se déclenche juste après l’ouverture de l’écran de mort.

- `$$days_survived` : nombre de jours en jeu écoulés depuis votre dernière mort, arrondi à l’entier inférieur
- `$$death_reason_string` : message de mort en texte brut
- `$$death_reason_component` : message de mort sous forme de composant texte JSON
- `$$death_pos_x`, `$$death_pos_y`, `$$death_pos_z` : position où vous êtes mort

### À la réception de dégâts

**Identifiant :** `damage_taken`

Se déclenche une fois pour chaque coup reçu.

- `$$damage_amount` : quantité de points de vie retirés par le coup
- `$$damage_type` : type de dégâts, par exemple `minecraft:fall`
- `$$is_fatal_damage` : `true` si le coup vous a tué
- `$$damage_source` : type de l’entité à l’origine des dégâts, par exemple `minecraft:zombie`, ou `NONE`

### À l’obtention d’un effet

**Identifiant :** `effect_gained`

Se déclenche une fois lorsque vous obtenez un effet de statut.

- `$$effect_key` : effet obtenu, par exemple `minecraft:speed`
- `$$effect_type` : `positive`, `negative` ou `neutral`
- `$$effect_duration` : durée de l’effet en ticks (20 ticks correspondent à 1 seconde)

### À la fin d’un effet

**Identifiant :** `effect_lost`

Se déclenche une fois lorsqu’un effet de statut prend fin.

- `$$effect_key` : effet, par exemple `minecraft:speed`
- `$$effect_type` : `positive`, `negative` ou `neutral`

### Au changement d’expérience

**Identifiant :** `experience_changed`

Se déclenche chaque fois que votre nombre de points d’expérience augmente ou diminue.

- `$$new_experience_amount` : nombre actuel de vos points d’expérience
- `$$old_experience_amount` : nombre précédent de vos points d’expérience
- `$$is_level_up` : `true` si vous avez gagné un niveau

### Au déblocage d’un haut fait

**Identifiant :** `achievement_unlocked`

Se déclenche une fois lorsque vous débloquez un haut fait (avancement). Les hauts faits déjà obtenus, par exemple en rejoignant un monde, ne sont pas pris en compte.

- `$$achievement_key` : haut fait, par exemple `minecraft:story/mine_diamond`
- `$$achievement_label` : titre dans la langue du jeu
- `$$achievement_description` : description dans la langue du jeu
- `$$achievement_icon_item_key` : objet utilisé comme icône, par exemple `minecraft:diamond`
- `$$achievement_type` : `advancement`, `goal` ou `challenge`

### Au saut

**Identifiant :** `jump`

Se déclenche à chaque saut. Il ne possède aucune variable.

### Au début du sprint

**Identifiant :** `started_running`

Se déclenche une fois lorsque vous commencez à sprinter. Il ne possède aucune variable.

### À la fin du sprint

**Identifiant :** `stopped_running`

Se déclenche une fois lorsque vous arrêtez de sprinter. Il ne possède aucune variable.

### Au changement de position

**Identifiant :** `position_changed`

Se déclenche chaque fois que vous passez dans un autre bloc.

- `$$old_pos_x`, `$$old_pos_y`, `$$old_pos_z` : position précédente du bloc
- `$$new_pos_x`, `$$new_pos_y`, `$$new_pos_z` : nouvelle position du bloc

### Au début de l’embrasement

**Identifiant :** `started_burning`

Se déclenche une fois lorsque vous commencez à brûler. Il ne possède aucune variable.

### À la fin de l’embrasement

**Identifiant :** `stopped_burning`

Se déclenche une fois lorsque vous cessez de brûler. Il ne possède aucune variable.

### Au début de la noyade

**Identifiant :** `started_drowning`

Se déclenche une fois lorsque vous commencez à subir des dégâts de noyade. Il ne possède aucune variable.

### Au début du gel

**Identifiant :** `started_freezing`

Se déclenche une fois lorsque vous commencez à geler, par exemple dans de la neige poudreuse.

- `$$freezing_intensity` : degré de gel, de `0.0` (pas du tout gelé) à `1.0` (complètement gelé)

### À la fin du gel

**Identifiant :** `stopped_freezing`

Se déclenche une fois lorsque vous cessez de geler. Il ne possède aucune variable.

### En cas de gel complet

**Identifiant :** `fully_frozen`

Se déclenche une fois lorsque vous êtes complètement gelé. Il ne possède aucune variable.

### Au début de la nage

**Identifiant :** `start_swimming`

Se déclenche une fois lorsque vous commencez à nager.

- `$$fluid_type` : fluide concerné, par exemple `minecraft:water`

### À la fin de la nage

**Identifiant :** `stop_swimming`

Se déclenche une fois lorsque vous arrêtez de nager.

- `$$fluid_type` : fluide concerné, par exemple `minecraft:water`

### Au contact d’un fluide

**Identifiant :** `start_touching_fluid`

Se déclenche une fois lorsque vous commencez à toucher un fluide, comme de l’eau ou de la lave.

- `$$fluid_type` : fluide concerné, par exemple `minecraft:lava`

### À la fin du contact avec un fluide

**Identifiant :** `stop_touching_fluid`

Se déclenche une fois lorsque vous cessez de toucher un fluide.

- `$$fluid_type` : fluide concerné, par exemple `minecraft:lava`

## Objets

### À la récupération d’un objet

**Identifiant :** `item_picked_up`

Se déclenche une fois lorsque vous ramassez un objet.

- `$$item_key` : objet ramassé, par exemple `minecraft:diamond`

### Au lâcher d’un objet

**Identifiant :** `item_dropped`

Se déclenche une fois lorsque vous lâchez un objet de votre inventaire.

- `$$item_key` : objet lâché, par exemple `minecraft:diamond`

### À la consommation d’un objet

**Identifiant :** `item_consumed`

Se déclenche une fois lorsque vous avez fini de manger ou de boire un objet.

- `$$item_key` : objet consommé, par exemple `minecraft:golden_apple`

### À l’utilisation d’un objet

**Identifiant :** `item_used`

Se déclenche une fois lorsque vous utilisez un objet.

- `$$item_key` : objet utilisé, par exemple `minecraft:flint_and_steel`
- `$$used_on_type` : cible de l’utilisation : `block`, `entity`, `self` ou `none`
- `$$used_on_entity_key` : type de l’entité visée. Vide si aucune entité n’est visée.
- `$$used_on_block_key` : bloc visé. Vide si aucun bloc n’est visé.
- `$$target_pos_x`, `$$target_pos_y`, `$$target_pos_z` : position de la cible, ou `-1`

### À la casse d’un objet

**Identifiant :** `item_broke`

Se déclenche une fois lorsqu’un objet de votre inventaire casse.

- `$$item_key` : objet cassé, par exemple `minecraft:iron_pickaxe`
- `$$item_type` : `tool`, `armor` ou `other`

### Au survol d’un objet dans un inventaire

**Identifiant :** `item_hovered_in_inventory`

Se déclenche une fois lorsque la souris passe sur un objet dans n’importe quel inventaire, le vôtre ou celui d’un coffre, par exemple.

- `$$item_key` : objet survolé, par exemple `minecraft:diamond_sword`
- `$$item_display_name_string` : nom de l’objet en texte brut
- `$$item_display_name_json` : nom de l’objet sous forme de composant texte JSON

## Blocs

### Au début de l’observation d’un bloc

**Identifiant :** `start_looking_at_block`

Se déclenche une fois lorsque votre viseur commence à pointer vers un bloc situé à 20 blocs maximum.

- `$$block_key` : bloc visé, par exemple `minecraft:oak_log`
- `$$block_pos_x`, `$$block_pos_y`, `$$block_pos_z` : position du bloc
- `$$distance_to_player` : distance entre vos yeux et le point visé par le viseur

### À la fin de l’observation d’un bloc

**Identifiant :** `stop_looking_at_block`

Se déclenche une fois lorsque votre viseur cesse de pointer vers un bloc.

Fournit les mêmes variables que **Au début de l’observation d’un bloc**, pour le bloc que vous regardiez précédemment : `$$block_key`, `$$block_pos_x`, `$$block_pos_y`, `$$block_pos_z` et `$$distance_to_player`.

### À la destruction d’un bloc

**Identifiant :** `block_broke`

Se déclenche une fois lorsque vous cassez un bloc.

- `$$block_key` : bloc cassé, par exemple `minecraft:stone`
- `$$broke_with_item_key` : objet tenu en main, par exemple `minecraft:iron_pickaxe`, ou `EMPTY`
- `$$block_pos_x`, `$$block_pos_y`, `$$block_pos_z` : position du bloc

### À la pose d’un bloc

**Identifiant :** `block_placed`

Se déclenche une fois lorsque vous posez un bloc.

- `$$block_key` : bloc posé, par exemple `minecraft:torch`
- `$$block_pos_x`, `$$block_pos_y`, `$$block_pos_z` : position du bloc

### À l’interaction avec un bloc

**Identifiant :** `interacted_with_block`

Se déclenche une fois lorsque vous utilisez un bloc, par exemple en ouvrant un coffre ou en appuyant sur un bouton.

- `$$block_key` : bloc utilisé, par exemple `minecraft:chest`
- `$$block_pos_x`, `$$block_pos_y`, `$$block_pos_z` : position du bloc

### En marchant sur un bloc

**Identifiant :** `stepping_on_block`

Se déclenche une fois lorsque vous marchez sur un bloc.

- `$$block_key` : bloc, par exemple `minecraft:grass_block`
- `$$block_pos_x`, `$$block_pos_y`, `$$block_pos_z` : position du bloc

## Entités

### Au début de l’observation d’une entité

**Identifiant :** `start_looking_at_entity`

Se déclenche une fois lorsque votre viseur commence à pointer vers une entité située à 20 blocs maximum.

- `$$entity_key` : type de l’entité, par exemple `minecraft:villager`
- `$$distance_to_player` : distance entre vos yeux et le point visé par le viseur
- `$$entity_pos_x`, `$$entity_pos_y`, `$$entity_pos_z` : position de l’entité
- `$$entity_uuid` : UUID de l’entité

### À la fin de l’observation d’une entité

**Identifiant :** `stop_looking_at_entity`

Se déclenche une fois lorsque votre viseur cesse de pointer vers une entité.

Fournit les mêmes variables que **Au début de l’observation d’une entité**, pour l’entité que vous regardiez précédemment : `$$entity_key`, `$$distance_to_player`, `$$entity_pos_x`, `$$entity_pos_y`, `$$entity_pos_z` et `$$entity_uuid`.

### Lorsqu’une entité entre dans le champ de vision

**Identifiant :** `entity_starts_being_in_sight`

Se déclenche une fois lorsqu’une entité devient visible à l’écran, jusqu’à 200 blocs de distance.

- `$$entity_key` : type de l’entité, par exemple `minecraft:creeper`
- `$$distance_to_player` : distance entre vos yeux et l’entité
- `$$entity_pos_x`, `$$entity_pos_y`, `$$entity_pos_z` : position de l’entité
- `$$entity_uuid` : UUID de l’entité

### Lorsqu’une entité quitte le champ de vision

**Identifiant :** `entity_stops_being_in_sight`

Se déclenche une fois lorsqu’une entité visible sort de votre écran ou s’éloigne à plus de 200 blocs.

Fournit les mêmes variables que **Lorsqu’une entité entre dans le champ de vision** : `$$entity_key`, `$$distance_to_player`, `$$entity_pos_x`, `$$entity_pos_y`, `$$entity_pos_z` et `$$entity_uuid`.

### À l’interaction avec une entité

**Identifiant :** `entity_interacted`

Se déclenche une fois lorsque vous utilisez une entité, par exemple en faisant du commerce avec un villageois.

- `$$entity_key` : type de l’entité, par exemple `minecraft:villager`
- `$$entity_pos_x`, `$$entity_pos_y`, `$$entity_pos_z` : position de l’entité
- `$$entity_uuid` : UUID de l’entité

### En montant sur une entité

**Identifiant :** `entity_mounted`

Se déclenche une fois lorsque vous commencez à monter sur une entité, comme un cheval ou un bateau.

- `$$entity_key` : type de l’entité, par exemple `minecraft:horse`
- `$$entity_pos_x`, `$$entity_pos_y`, `$$entity_pos_z` : position de l’entité
- `$$entity_uuid` : UUID de l’entité

### En descendant d’une entité

**Identifiant :** `entity_unmounted`

Se déclenche une fois lorsque vous cessez de monter sur une entité.

- `$$entity_key` : type de l’entité, par exemple `minecraft:horse`
- `$$entity_pos_x`, `$$entity_pos_y`, `$$entity_pos_z` : position de l’entité
- `$$entity_uuid` : UUID de l’entité

### À l’apparition d’une entité

**Identifiant :** `entity_spawned`

Nécessite que FancyMenu soit installé sur le serveur. Se déclenche lorsqu’une entité apparaît n’importe où dans le monde, même à grande distance ou dans une autre dimension.

- `$$entity_key` : type de l’entité, par exemple `minecraft:zombie`
- `$$distance_to_player` : distance qui vous sépare de l’entité, ou `-1` dans une autre dimension
- `$$entity_pos_x`, `$$entity_pos_y`, `$$entity_pos_z` : position d’apparition
- `$$entity_uuid` : UUID de l’entité
- `$$dimension_key` : dimension, par exemple `minecraft:overworld`
- `$$is_same_dimension_as_player` : `true` si l’entité est apparue dans votre dimension

### À la mort d’une entité

**Identifiant :** `entity_died`

Nécessite que FancyMenu soit installé sur le serveur. Se déclenche lorsqu’une entité meurt n’importe où dans le monde, même à grande distance ou dans une autre dimension.

- `$$entity_key` : type de l’entité, par exemple `minecraft:ender_dragon`
- `$$distance_to_player` : distance qui vous sépare de l’entité, ou `-1` dans une autre dimension
- `$$death_pos_x`, `$$death_pos_y`, `$$death_pos_z` : position où elle est morte
- `$$entity_uuid` : UUID de l’entité
- `$$dimension_key` : dimension, par exemple `minecraft:the_end`
- `$$damage_type` : type de dégâts qui l’a tuée, par exemple `minecraft:player_attack`
- `$$is_same_dimension_as_player` : `true` si elle est morte dans votre dimension
- `$$entity_killed_by_name` : nom du tueur, ou `NONE`
- `$$entity_killed_by_key` : type du tueur, par exemple `minecraft:player`, ou `NONE`
- `$$entity_killed_by_uuid` : UUID du tueur, ou `NONE`

## Monde et lieux

### À l’entrée dans un biome

**Identifiant :** `enter_biome`

Se déclenche une fois lorsque vous entrez dans un autre biome.

- `$$biome_key` : biome, par exemple `minecraft:cherry_grove`

### À la sortie d’un biome

**Identifiant :** `leave_biome`

Se déclenche une fois lorsque vous quittez un biome.

- `$$biome_key` : biome quitté, par exemple `minecraft:cherry_grove`

### À l’entrée dans une structure

**Identifiant :** `enter_structure`

Nécessite que FancyMenu soit installé sur le serveur. Se déclenche une fois lorsque vous entrez dans la zone d’une structure. La délimitation est approximative : le déclencheur peut donc s’activer près d’une structure ou au-dessus, par exemple au-dessus d’une galerie de mine souterraine. Pour ne détecter que l’intérieur, utilisez **À l’entrée dans une structure (haute précision)**.

- `$$structure_key` : structure, par exemple `minecraft:village_plains`

### À la sortie d’une structure

**Identifiant :** `leave_structure`

Nécessite que FancyMenu soit installé sur le serveur. Se déclenche une fois lorsque vous quittez la zone d’une structure, selon une délimitation aussi approximative que celle de **À l’entrée dans une structure**.

- `$$structure_key` : structure quittée

### À l’entrée dans une structure (haute précision)

**Identifiant :** `enter_structure_high_precision`

Nécessite que FancyMenu soit installé sur le serveur. Se déclenche une fois lorsque vous entrez à l’intérieur d’une structure.

- `$$structure_key` : structure, par exemple `minecraft:stronghold`

### À la sortie d’une structure (haute précision)

**Identifiant :** `leave_structure_high_precision`

Nécessite que FancyMenu soit installé sur le serveur. Se déclenche une fois lorsque vous êtes entièrement sorti d’une structure.

- `$$structure_key` : structure quittée

### À l’entrée dans une dimension

**Identifiant :** `enter_dimension`

Se déclenche une fois lorsque vous entrez dans une autre dimension.

- `$$dimension_key` : dimension, par exemple `minecraft:the_nether`

### Au changement de météo

**Identifiant :** `weather_changed`

Se déclenche une fois lorsque la météo change. Il se déclenche également lorsque la météo change à l’endroit où vous vous trouvez : marcher dans un désert, un biome enneigé ou un bâtiment pendant qu’il pleut compte aussi.

- `$$weather_type` : `clear`, `rain` ou `thunder`
- `$$weather_can_snow` : `true` s’il pourrait neiger à l’endroit où vous vous trouvez
- `$$weather_can_rain` : `true` s’il pourrait pleuvoir à l’endroit où vous vous trouvez

### Au début d’un raid

**Identifiant :** `raid_started`

Nécessite que FancyMenu soit installé sur le serveur. Se déclenche lorsqu’un raid commence dans la zone où vous vous trouvez, et que la barre de raid apparaît. Il ne possède aucune variable.

Entrer dans une zone où un raid est déjà en cours ne compte pas. Utilisez **À l’entrée dans la zone d’un raid en cours** dans ce cas.

### À l’entrée dans la zone d’un raid en cours

**Identifiant :** `enter_active_raid_area`

Nécessite que FancyMenu soit installé sur le serveur. Se déclenche lorsque vous entrez dans la zone d’un raid déjà en cours, et que la barre de raid apparaît. Il ne possède aucune variable.

### À la sortie de la zone d’un raid en cours

**Identifiant :** `leave_active_raid_area`

Nécessite que FancyMenu soit installé sur le serveur. Se déclenche lorsque vous quittez la zone d’un raid et que la barre de raid disparaît. Mourir ou changer de dimension dans cette zone compte également, mais la fin du raid ne compte pas. Il ne possède aucune variable.

### À la fin d’un raid

**Identifiant :** `raid_finished`

Nécessite que FancyMenu soit installé sur le serveur. Se déclenche lorsqu’un raid prend fin alors que vous vous trouvez dans sa zone.

- `$$raid_result` : `victory` ou `defeat`

## Sons et musique

### Au démarrage d’une piste musicale

**Identifiant :** `music_track_started`

Se déclenche une fois lorsqu’une piste musicale commence à être lue.

- `$$track_resource_location` : fichier audio de la piste
- `$$track_display_name` : nom de la piste, ou `UNKNOWN`
- `$$track_artist` : artiste de la piste, ou `UNKNOWN`
- `$$track_duration_ms` : durée en millisecondes, ou `0` si elle est inconnue

### À l’arrêt d’une piste musicale

**Identifiant :** `music_track_stopped`

Se déclenche une fois lorsque la piste musicale s’arrête, parce qu’elle est terminée ou qu’elle a été remplacée par une autre.

Fournit les mêmes variables que **Au démarrage d’une piste musicale** : `$$track_resource_location`, `$$track_display_name`, `$$track_artist` et `$$track_duration_ms`.

### Au déclenchement d’un son du monde

**Identifiant :** `world_sound_triggered`

Se déclenche chaque fois qu’un son commence à être joué dans le monde près de vous, comme le bruit d’une porte ou d’un creeper.

- `$$sound_resource_location` : fichier audio
- `$$sound_display_name` : sous-titre du son, ou `UNKNOWN`
- `$$sound_origin_pos_x`, `$$sound_origin_pos_y`, `$$sound_origin_pos_z` : origine du son
- `$$sound_origin_distance_to_player` : distance à laquelle se trouve l’origine du son
- `$$sound_origin_direction_from_player` : direction du son en degrés (de 0 à 360), par rapport à votre orientation
