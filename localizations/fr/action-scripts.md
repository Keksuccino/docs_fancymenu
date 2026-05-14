---
title: Scripts d’action
description: >-
  Comment utiliser des scripts d’action avec des boutons, des curseurs, des
  tickers et plus encore.
---

# Scripts d’action

FancyMenu vous permet d’ajouter de l’interactivité à vos menus en attribuant des **actions** à des éléments. Ces actions s’exécutent lorsqu’un bouton est cliqué, qu’un ticker tourne, qu’un curseur est utilisé ou qu’un écran s’ouvre ou se ferme. Vous pouvez aussi créer des scripts d’action avancés à l’aide d’instructions de contrôle simples, comme **if**, **else-if**, **else** et **while**, pour contrôler quelles actions s’exécutent et quand.

<img src="https://github.com/Keksuccino/FancyMenu/blob/master/assets/docs/action_script_editor.png?raw=true" alt="Éditeur de scripts d’action" style="max-width:800px;width:100%;height:auto;">

# Qu’est-ce qu’une action ?

Une **action** est une tâche ou une opération que FancyMenu exécute lorsqu’elle est déclenchée. Par exemple, une action peut ouvrir un nouvel écran, envoyer un message dans le chat ou ajuster le volume d’un élément audio. Dans l’éditeur de FancyMenu, les actions sont configurées avec une valeur (si nécessaire) qui fournit des détails supplémentaires — comme une URL ou une adresse de serveur.

# Qu’est-ce qu’une instruction ?

Pour créer un comportement plus complexe, FancyMenu prend en charge des instructions de contrôle de base dans les scripts d’action. Elles incluent :

- **Instruction If :** exécute un bloc d’actions uniquement si une [condition](/en/conditions) spécifiée est remplie.
- **Instruction Else-If :** vérifie une autre [condition](/en/conditions) si le précédent *if* (ou un *else-if* antérieur) n’a pas été rempli.
- **Instruction Else :** s’exécute si aucune des [conditions](/en/conditions) précédentes n’est remplie.
- **Instruction While :** répète en continu un bloc d’actions tant qu’une [condition](/en/conditions) reste vraie (avec un délai d’expiration intégré pour éviter les boucles infinies).
- **Bloc Delay :** attend le temps spécifié avant d’exécuter les actions qu’il contient. Le reste du script continue de s’exécuter pendant le compte à rebours.
- **Bloc Execute Later :** place les actions contenues dans une file d’attente pour les exécuter sur le thread principal après un délai en millisecondes.
- **Commentaire :** ajoute une note dans le script pour l’organiser. Les commentaires n’exécutent aucune action.

En combinant ces instructions avec des actions, vous pouvez construire un comportement dynamique et conditionnel, par exemple vérifier si la santé d’un joueur est faible avant d’envoyer un message d’avertissement, ou répéter une mise à jour jusqu’à ce qu’une condition change.

# Où peut-on utiliser les scripts d’action ?

Les scripts d’action sont polyvalents et peuvent être utilisés dans toute votre mise en page. Vous pouvez les attribuer, par exemple, à :

- **Boutons :** exécuter une action lorsque le bouton est cliqué.
- **Tickers :** exécuter en continu un script d’action pour mettre à jour des informations à l’écran dans une mise en page.
- **Curseurs :** déclencher un script d’action chaque fois que la valeur du curseur change.
- **Événements d’écran :** exécuter des scripts lorsqu’un écran s’ouvre ou se ferme (par exemple, jouer un son lorsqu’un menu apparaît).
- **Listeners :** lorsqu’un listener qui écoute un événement spécifique est déclenché, il exécute son script d’action.
- **Planificateurs :** exécuter des actions à intervalles réguliers, même lorsqu’aucun écran n’est ouvert.

# Utiliser des placeholders dans les actions

Les valeurs d’action prennent en charge du contenu dynamique grâce aux **placeholders**. La plupart du temps, ces placeholders utilisent une syntaxe de type JSON et sont remplacés par des données en temps réel lorsque l’action s’exécute.

## Placeholders de type JSON

Ce sont les [placeholders](/en/placeholders) habituels qui peuvent être utilisés à de nombreux endroits dans les mises en page.

Ils suivent cette syntaxe :

```json
{"placeholder": "placeholder_id", "values": {"key1": "value1", "key2": "value2"}}
```

Ils peuvent récupérer des données du jeu comme le nom du joueur, les dimensions de l’écran ou des valeurs calculées à l’aide du placeholder **Calculator**. Vous pouvez aussi imbriquer des placeholders pour des usages plus avancés.

## Placeholders `$$` (variables)

Les placeholders `$$` sont spéciaux. Certaines fonctionnalités de FancyMenu fourniront ces placeholders spéciaux pour leurs actions imbriquées, leurs prérequis et leurs placeholders normaux, afin qu’ils puissent être utilisés à l’intérieur pour obtenir plus d’informations sur l’environnement (élément, listener, etc.) dans lequel ils se trouvent.

Par exemple, si des actions sont utilisées dans un curseur, l’utilisation de `$$value` dans l’action sera remplacée par la valeur actuelle du curseur.

Lorsque des actions sont utilisées dans des listeners, chaque listener fournira son propre ensemble unique de variables/placeholders pour obtenir plus d’informations sur le listener, comme le bouton de souris pressé, la structure saisie, etc.

# Comment configurer et modifier des actions

Pour ajouter, modifier ou supprimer des actions (et des blocs d’instructions) pour un élément, faites simplement **clic droit sur l’élément** (qu’il s’agisse d’un bouton, d’un curseur, d’un ticker ou d’un autre élément interactif), puis sélectionnez **Gérer le script d’action**. Cela ouvre l’écran de gestion des actions, où vous pouvez :

- **Ajouter de nouvelles actions ou instructions :** insérer de nouvelles entrées d’action ou des instructions de contrôle (if, else-if, else, while) pour construire votre script.
- **Modifier des actions ou instructions existantes :** modifier la valeur de l’action ou changer la logique de contrôle.
- **Supprimer des actions ou instructions :** supprimer du script les actions indésirables.

Pour les [listeners](/listeners), il existe un menu spécial pour gérer et créer des listeners, y compris l’accès à leurs scripts d’action afin d’avoir la même expérience que lors de la modification du script d’action d’un bouton ou d’un curseur, par exemple.

> Dans l’écran de l’éditeur de script d’action, faites simplement un clic droit sur la grande zone gris foncé pour ouvrir un menu contextuel permettant d’ajouter des actions, des instructions et plus encore.
{.is-info}


# Raccourcis et autres fonctionnalités de l’éditeur de script d’action

L’éditeur de script d’action dispose de plusieurs fonctionnalités très pratiques qui rendent la modification de scripts extrêmement simple.

## Raccourcis

- `DEL` : suppression rapide de l’entrée sélectionnée
- `ENTER` : démarre l’édition en ligne de l’entrée sélectionnée (ou ouvre l’écran de modification s’il n’y a pas d’édition en ligne pour l’entrée sélectionnée)
- `CTRL + C` : copie l’action sélectionnée (fonctionne uniquement avec les actions pour le moment)
- `CTRL + V` : colle l’action précédemment copiée
- `CTRL + Z` : retour d’une étape (annuler)
- `CTRL + Y` : avance d’une étape (rétablir)
- `FLÈCHE HAUT` : navigue d’une entrée vers le haut à partir de l’entrée actuellement sélectionnée
- `FLÈCHE BAS` : navigue d’une entrée vers le bas à partir de l’entrée actuellement sélectionnée
- `SHIFT + FLÈCHE HAUT` : déplace l’entrée sélectionnée d’un cran vers le haut
- `SHIFT + FLÈCHE BAS` : déplace l’entrée sélectionnée d’un cran vers le bas
- `A` : ouvre rapidement l’écran de sélection d’action pour ajouter une nouvelle action
- `CTRL + S` : terminer/enregistrer depuis la fenêtre de l’éditeur

## Plus de fonctionnalités pratiques

- Un double-clic sur la valeur d’une action vous permet de modifier la valeur sans passer par l’écran complet de modification de la valeur.
- Les chaînes d’instructions IF (avec des instructions ELSE/ELSE-IF ajoutées), les boucles WHILE et les dossiers peuvent être réduits/rétractés (visuel uniquement, cela n’affecte pas la logique du script).
- L’éditeur ajoute toujours les nouvelles actions sous l’entrée sélectionnée (ou imbriquées dans la chaîne/la boucle/le dossier sélectionné).
- Un clic droit sur l’arrière-plan gris foncé de la zone du script ouvre un menu contextuel avec des options pour ajouter des actions, des instructions et tout le reste d’important.

# Détail des actions

Cette liste contient la plupart, sinon toutes, les actions disponibles dans FancyMenu. Il est possible que la liste soit parfois légèrement obsolète en raison des mises à jour du mod.

## Piste suivante (`audio_next_track`)
- **Description :** passe à la piste suivante dans un élément audio
- **Valeur requise :** Oui - `audio_element_identifier` (l’ID de l’élément audio à contrôler)

## Piste précédente (`audio_previous_track`)
- **Description :** passe à la piste précédente dans un élément audio
- **Valeur requise :** Oui - `audio_element_identifier` (l’ID de l’élément audio à contrôler)

## Définir le volume de la piste (`set_audio_element_volume`)
- **Description :** définit le volume d’un élément audio (0.0 à 1.0)
- **Valeur requise :** Oui - `element_identifier:volume`

## Basculer lecture/pause de la piste (`audio_toggle_play`)
- **Description :** bascule l’état lecture/pause de la piste actuelle d’un élément audio
- **Valeur requise :** Oui - `audio_element_identifier`

## Jouer l’audio (`play_audio`)
- **Description :** joue une ressource audio une seule fois. L’action suit l’audio qu’elle a démarré afin qu’il puisse ensuite être arrêté par `stop_all_action_audios`.
- **Valeur requise :** Oui - configuration JSON avec `audioSource`, `soundChannel` et `baseVolume`
- **Exemple de valeur :** `{"audioSource":"[source:local]/config/fancymenu/assets/example.ogg","soundChannel":"master","baseVolume":1.0}`

## Arrêter tous les audios d’action (`stop_all_action_audios`)
- **Description :** arrête toutes les pistes audio démarrées par l’action **Jouer l’audio**. Cela n’arrête pas les éléments Audio, les sons d’ouverture/fermeture de menu, les sons de boutons ou d’autres systèmes audio.
- **Valeur requise :** Non

## Définir le volume de l’élément vidéo (`set_video_element_volume`)
- **Description :** définit le volume d’un élément vidéo (0.0 à 1.0)
- **Valeur requise :** Oui - `video_element_identifier:volume`

## Définir le temps de lecture de l’élément vidéo (`set_video_element_play_time`)
- **Description :** place un élément vidéo à un timestamp en millisecondes
- **Valeur requise :** Oui - `video_element_identifier:timestamp_ms`

## Basculer l’état pause de l’élément vidéo (`toggle_video_element_pause_state`)
- **Description :** bascule l’état pause d’un élément vidéo
- **Valeur requise :** Oui - `video_element_identifier`

## Définir le volume d’arrière-plan vidéo (`set_video_menu_background_volume`)
- **Description :** définit le volume d’un arrière-plan de menu vidéo (0.0 à 1.0)
- **Valeur requise :** Oui - `background_identifier:volume`

> Pour obtenir l’identifiant d’un arrière-plan, faites un clic droit sur l’arrière-plan de l’éditeur et cliquez sur « Copier l’identifiant de l’arrière-plan ».
{.is-info}

## Définir le temps de lecture d’un arrière-plan vidéo (`set_video_menu_background_play_time`)
- **Description :** place un arrière-plan de menu vidéo à un timestamp en millisecondes
- **Valeur requise :** Oui - `background_identifier:timestamp_ms`

> Pour obtenir l’identifiant d’un arrière-plan, faites un clic droit sur l’arrière-plan de l’éditeur et cliquez sur « Copier l’identifiant de l’arrière-plan ».
{.is-info}

## Basculer l’état pause d’un arrière-plan vidéo (`toggle_video_menu_background_pause_state`)
- **Description :** bascule l’état pause d’un arrière-plan de menu vidéo
- **Valeur requise :** Oui - `background_identifier`

> Pour obtenir l’identifiant d’un arrière-plan, faites un clic droit sur l’arrière-plan de l’éditeur et cliquez sur « Copier l’identifiant de l’arrière-plan ».
{.is-info}

## Basculer une mise en page (`toggle_layout`)
- **Description :** bascule une mise en page (activer/désactiver) par son nom
- **Valeur requise :** Oui - `layout_name`

## Activer une mise en page (`enable_layout`)
- **Description :** active une mise en page par son nom
- **Valeur requise :** Oui - `layout_name`

## Désactiver une mise en page (`disable_layout`)
- **Description :** désactive une mise en page par son nom
- **Valeur requise :** Oui - `layout_name`

## Ouvrir un écran ou une interface graphique personnalisée (`opengui`)
- **Description :** ouvre un écran par son identifiant (vanilla, mod ou interface graphique personnalisée)
- **Valeur requise :** Oui - `screen_identifier`

> Cette action **ne fonctionnera pas pour tous les écrans**, en particulier les écrans de mods. Si l’action ne parvient pas à ouvrir un écran, une erreur sera affichée. Vous ne pouvez pas faire grand-chose dans ce cas, car il s’agit probablement d’un écran trop complexe pour être ouvert automatiquement par FancyMenu.
> 
> La compatibilité pour les écrans de mods ne sera plus ajoutée manuellement côté FancyMenu, car ajouter la compatibilité pour tous les mods existants prendrait un temps énorme, désolé. Dans la plupart des cas, il n’est pas non plus recommandé de contacter le développeur de l’autre mod dans ce cas, car si FancyMenu ne peut pas ouvrir l’écran, il n’existe pas de moyen simple d’ajouter la prise en charge. Le contournement recommandé ici est d’essayer d’utiliser l’action **« Mimic Vanilla/Mod Button »** pour imiter un bouton qui ouvre l’écran spécifique. S’il n’y a pas de bouton, alors il n’y a malheureusement pas de solution.
{.is-info}

## Fermer l’écran (`closegui`)
- **Description :** ferme l’écran actif
- **Valeur requise :** Non

## Mettre à jour l’écran (`update_screen`)
- **Description :** réinitialise l’écran actuel
- **Valeur requise :** Non

## Retourner au dernier écran (`back_to_last_screen`)
- **Description :** revient à l’écran précédent (celui d’avant l’écran actuel)
- **Valeur requise :** Non

## Rejoindre un serveur (`joinserver`)
- **Description :** connecte le joueur à un serveur Minecraft
- **Valeur requise :** Oui - `server_ip:port`

## Entrer dans un monde (`loadworld`)
- **Description :** entre dans un monde Minecraft
- **Valeur requise :** Oui - `world_folder_name`

## Entrer/Rejoindre le dernier monde/serveur (`join_last_world`)
- **Description :** entre/rejoint le dernier monde ou serveur dans lequel le joueur se trouvait
- **Valeur requise :** Non

## Quitter un monde ou un serveur (`disconnect_server_or_world`)
- **Description :** quitte un monde ou un serveur et ouvre un écran spécifié
- **Valeur requise :** Oui - `screen_identifier`

## Quitter complètement Minecraft (`quitgame`)
- **Description :** quitte complètement Minecraft
- **Valeur requise :** Non

## Envoyer un message/une commande dans le chat (`sendmessage`)
- **Description :** envoie un message de chat ou exécute une commande de chat
- **Valeur requise :** Oui - `message_text` ou `/command_text`

## Exécuter une commande en tant que serveur intégré (`execute_command_as_integrated_server`)
- **Description :** exécute de force une commande en solo en tant que serveur intégré, en ignorant les permissions et le paramètre de triche.
- **Valeur requise :** Oui - texte de commande, par exemple `/give @p minecraft:diamond 1`

> Cette action fonctionne uniquement en solo lorsque le monde n’est pas ouvert en LAN. Elle ne fait volontairement rien en multijoueur.
{.is-warning}

## Coller dans le chat (`paste_to_chat`)
- **Description :** colle du texte dans le champ de saisie du chat (ajout ou remplacement)
- **Valeur requise :** Oui - `true:Texte` ou `false:Texte`

## Afficher dans le chat [côté client] (`display_in_chat_client_side`)
- **Description :** affiche du texte directement dans le chat local (sans serveur)
- **Valeur requise :** Oui - `text_or_json`

## Envoyer des données FM au serveur (`send_fm_data_to_server`)
- **Description :** envoie des données textuelles personnalisées au serveur FancyMenu actuel via le canal de paquets FM Data.
- **Valeur requise :** Oui - `data_identifier||data`

## Se connecter à un serveur distant (`connect_to_remote_server`)
- **Description :** ouvre ou réutilise une connexion WebSocket initiée par le client vers un serveur distant externe.
- **Valeur requise :** Oui - URL du serveur distant, par exemple `wss://example.com/ws`

## Envoyer des données à un serveur distant (`send_data_to_remote_server`)
- **Description :** ouvre ou réutilise une connexion à un serveur distant et lui envoie des données textuelles.
- **Valeur requise :** Oui - `remote_server_url||data`

## Fermer la connexion à un serveur distant (`close_remote_server_connection`)
- **Description :** ferme une connexion spécifique à un serveur distant sur demande via son ID de requête.
- **Valeur requise :** Oui - ID de requête, généralement issu d’une variable de listener de serveur distant telle que `$$request_id`

## Fermer toutes les connexions aux serveurs distants (`close_all_remote_server_connections`)
- **Description :** ferme toutes les connexions actives aux serveurs distants ouvertes par FancyMenu.
- **Valeur requise :** Non

## Ouvrir une URL dans le navigateur (`openlink`)
- **Description :** ouvre un lien dans votre navigateur par défaut
- **Valeur requise :** Oui - `https://example.com`

## Copier du texte dans le presse-papiers (`copytoclipboard`)
- **Description :** copie du texte dans le presse-papiers
- **Valeur requise :** Oui - `text_to_copy`

## Écrire dans le journal du jeu (`print_to_log`)
- **Description :** écrit une ligne dans le journal du jeu
- **Valeur requise :** Oui - `text_to_log`

## Définir la valeur d’une variable (variable FM) (`set_variable`)
- **Description :** stocke du contenu textuel dans une variable FancyMenu
- **Valeur requise :** Oui - `variable_name:variable_value`

## Effacer toutes les variables (variable FM) (`clear_variables`)
- **Description :** efface TOUTES les variables stockées par FancyMenu
- **Valeur requise :** Non

## Envoyer une requête HTTP (`send_http_request`)
- **Description :** envoie une requête HTTP ; peut stocker la réponse dans une variable
- **Valeur requise :** Oui - configuration de la requête HTTP

> Cette action vous permet d’envoyer des données à des API REST, des webhooks ou n’importe quel point de terminaison HTTP.
> Prend en charge diverses méthodes d’authentification, des en-têtes personnalisés et différents types de requêtes.
> 
> Cette action vous permet aussi de stocker la réponse de la requête dans une variable FancyMenu pour une utilisation ultérieure !
{.is-info}

## Gérer le pack de ressources (`manage_resource_pack`)
- **Description :** active/désactive/bascule un pack de ressources par nom affiché (rechargement facultatif)
- **Valeur requise :** Oui - `pack_name|||MODE|||reload_bool`

## Recharger les packs de ressources (`reload_resource_packs`)
- **Description :** recharge les packs de ressources (cooldown de 5 s)
- **Valeur requise :** Non

## Recharger FancyMenu (`reloadmenu`)
- **Description :** recharge FancyMenu, y compris les panoramas, diaporamas et toutes les ressources (lourd)
- **Valeur requise :** Non

> Cette action a un **fort impact sur les performances** et peut provoquer des ralentissements si elle est utilisée dans des tickers. Il est déconseillé d’utiliser cette action ailleurs que sur un bouton.
{.is-warning}

## Basculer l’animateur d’élément (`toggle_element_animator`)
- **Description :** bascule l’état de lecture d’un animateur d’élément
- **Valeur requise :** Oui - `animator_identifier`

## Activer l’animateur d’élément (`enable_element_animator`)
- **Description :** active un animateur d’élément
- **Valeur requise :** Oui - `animator_identifier`

## Désactiver l’animateur d’élément (`disable_element_animator`)
- **Description :** désactive un animateur d’élément
- **Valeur requise :** Oui - `animator_identifier`

## Réinitialiser l’animateur d’élément (`reset_element_animator`)
- **Description :** réinitialise la chronologie/l’état d’un animateur d’élément
- **Valeur requise :** Oui - `animator_identifier`

## Imiter un bouton vanilla/mod (`mimicbutton`)
- **Description :** imite l’action de clic d’un bouton vanilla ou d’un mod
- **Valeur requise :** Oui - `screen_identifier:widget_locator`

## Imiter une touche de raccourci (`mimic_keybind`)
- **Description :** exécute un raccourci Minecraft (maintien facultatif)
- **Valeur requise :** Oui - `keybind_id|||keep_pressed_bool|||duration_ms`

## Définir la valeur d’un champ de saisie de texte (`set_text_input_field_value`)
- **Description :** définit la valeur d’un champ de saisie personnalisé ou vanilla par identifiant d’élément.
- **Valeur requise :** Oui - `element_identifier|||new_value|||force_set_when_inactive`

## Créer un fichier dans le répertoire du jeu (`create_file_in_game_dir`)
- **Description :** crée un fichier vide dans le répertoire du jeu (racine de l’instance). Accepte le préfixe `.minecraft/` pour cibler le répertoire du profil par défaut du launcher (peut différer du répertoire de l’instance actuelle).
- **Valeur requise :** Oui - `file_path`

## Supprimer un fichier/dossier dans le répertoire du jeu (`delete_file_in_game_dir`)
- **Description :** supprime un fichier ou un dossier dans le répertoire du jeu (racine de l’instance). Accepte le préfixe `.minecraft/` pour cibler le profil par défaut du launcher (peut différer de l’instance en cours). Ajoutez `*` pour supprimer **tous les fichiers directement à l’intérieur** d’un dossier (ignore les sous-dossiers ; conserve le dossier).
- **Valeur requise :** Oui - `target_path`

## Copier un fichier/dossier dans le répertoire du jeu (`copy_file_in_game_dir`)
- **Description :** copie à l’intérieur du répertoire du jeu (racine de l’instance) ; le préfixe `.minecraft/` cible le profil par défaut du launcher (pas toujours l’instance actuelle). Ajoutez `*` au chemin **source** pour copier chaque fichier directement à l’intérieur de ce dossier (ignore les sous-dossiers) ; la destination doit être un dossier et ne peut pas utiliser `*`.
- **Valeur requise :** Oui - `source||destination`

## Déplacer un fichier/dossier dans le répertoire du jeu (`move_file_in_game_dir`)
- **Description :** déplace à l’intérieur du répertoire du jeu (racine de l’instance) ; le préfixe `.minecraft/` cible le profil par défaut du launcher (peut différer de l’instance actuelle). Ajoutez `*` au chemin **source** pour déplacer chaque fichier directement à l’intérieur de ce dossier (ignore les sous-dossiers) ; la destination doit être un dossier et ne peut pas utiliser `*`.
- **Valeur requise :** Oui - `source||destination`

## Renommer un fichier/dossier dans le répertoire du jeu (`rename_file_in_game_dir`)
- **Description :** renomme un fichier ou un dossier à l’intérieur du répertoire du jeu (racine de l’instance) ; le préfixe `.minecraft/` cible le profil par défaut du launcher (peut différer de l’instance actuelle). Conserve le contenu intact, seul le nom change.
- **Valeur requise :** Oui - `path||new_name`

## Télécharger un fichier dans le répertoire du jeu (`download_file_to_game_dir`)
- **Description :** télécharge un fichier de manière asynchrone dans le répertoire du jeu (racine de l’instance) ; le préfixe `.minecraft/` cible le profil par défaut du launcher (pas nécessairement l’instance en cours). Indiquez le **dossier cible** ; le nom du fichier est dérivé automatiquement des en-têtes/de l’URL.
- **Valeur requise :** Oui - `url||target_folder`

## Extraire un fichier ZIP dans le répertoire du jeu (`extract_zip_file_in_game_dir`)
- **Description :** extrait un fichier ZIP dans un dossier cible à l’intérieur du répertoire du jeu ou du répertoire `.minecraft` par défaut. Déclenche le listener **On ZIP Extracted via Action** une fois terminé.
- **Valeur requise :** Oui - `source_zip_path||target_folder_path`

## Ouvrir un fichier/dossier dans le répertoire du jeu (`open_file_folder_in_game_dir`)
- **Description :** ouvre un fichier ou un dossier avec l’application par défaut du système d’exploitation. La cible doit rester à l’intérieur du répertoire du jeu ou du répertoire `.minecraft` par défaut pour des raisons de sécurité.
- **Valeur requise :** Oui - `target_path`

## Écrire dans un fichier dans le répertoire du jeu (`write_file_in_game_dir`)
- **Description :** écrit ou ajoute du texte dans le répertoire du jeu (racine de l’instance) ; le préfixe `.minecraft/` cible le profil par défaut du launcher (peut différer de cette instance). Crée le fichier s’il n’existe pas. Prend en charge `\n` dans la valeur pour insérer des retours à la ligne ; le mode ajout est contrôlé par le booléen final.
- **Valeur requise :** Oui - `path|||content|||append_bool`

## Sélectionner un fichier depuis le système (`select_file_to_game_dir`)
- **Description :** ouvre un sélecteur de fichiers natif (n’importe quel emplacement) et copie le fichier sélectionné dans le répertoire du jeu (racine de l’instance) ou dans le `.minecraft/` par défaut lorsqu’il est préfixé (ce défaut peut différer de cette instance). Prend en charge les filtres d’extension, une étiquette de filtre personnalisée et un basculement facultatif d’écrasement.
- **Valeur requise :** Oui - configuration de sélection

## Afficher une notification toast (`show_toast`)
- **Description :** affiche une notification toast configurable
- **Valeur requise :** Oui - configuration du toast

## Démarrer un planificateur (`start_scheduler`)
- **Description :** démarre un planificateur à partir de son ID de planificateur.
- **Valeur requise :** Oui - `scheduler_id`

## Arrêter un planificateur (`stop_scheduler`)
- **Description :** arrête un planificateur à partir de son ID de planificateur.
- **Valeur requise :** Oui - `scheduler_id`

## Définir une option Minecraft (`edit_minecraft_option`)
- **Description :** modifie une option de configuration Minecraft
- **Valeur requise :** Oui - `option_name:set_to_value`
