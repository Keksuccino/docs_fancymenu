---
title: Scripts d’action
description: >-
  Comment utiliser des scripts d’action avec des boutons, des curseurs, des
  compteurs et plus encore.
---
# Scripts d’action

Les scripts d’action exécutent des tâches configurées lorsqu’un [Bouton](./elements#button) est cliqué, qu’un [Ticker](./elements#ticker) se met à jour, qu’un [Curseur](./elements#slider) change, qu’un écran s’ouvre ou se ferme, ou qu’un autre événement pris en charge se produit. Des instructions telles que **if**, **else-if**, **else** et **while** ajoutent un contrôle conditionnel.

> [!CAUTION]
> Les scripts d’action importés peuvent modifier des fichiers, contacter des serveurs, ouvrir des liens ou exécuter des commandes. N’utilisez que des sources de confiance.

<img src="https://github.com/Keksuccino/FancyMenu/blob/master/assets/docs/action_script_editor.png?raw=true" alt="Éditeur de script d’action" style="max-width:800px;width:100%;height:auto;">

# Qu’est-ce qu’une action ?

Une **action** est une tâche ou un travail que FancyMenu exécute lorsqu’elle est déclenchée. Par exemple, une action peut ouvrir un nouvel écran, envoyer un message de chat ou ajuster le volume d’un [élément Audio](./elements#audio). Dans l’éditeur de FancyMenu, les actions sont configurées avec une valeur (si nécessaire) qui fournit des détails supplémentaires — comme une URL ou une adresse de serveur.

# Instructions

Pour créer un comportement plus complexe, FancyMenu prend en charge des instructions de contrôle dans les scripts d’action :

| Instruction | Comportement |
|---|---|
| **If** | Exécute ses actions uniquement lorsque ses [conditions requises](./conditions) sont remplies. |
| **Else-If** | Vérifie un autre ensemble de [conditions requises](./conditions) lorsque le **If** ou le **Else-If** précédent ne s’est pas exécuté. |
| **Else** | S’exécute lorsque aucune des [conditions requises](./conditions) des **If** ou **Else-If** précédents n’est remplie. |
| **While** | Répète ses actions tant que ses [conditions requises](./conditions) restent vraies. Il s’arrête après trois secondes pour éviter les boucles infinies ; ne l’utilisez pas comme minuteur. |

# Blocs

Des blocs peuvent être ajoutés aux scripts et offrent des fonctionnalités utiles pour mieux contrôler le flux/le timing d’exécution du script, ainsi que quelques fonctionnalités pratiques :

| Bloc | Comportement |
|---|---|
| **Delay** | Lance un compte à rebours sans arrêter le reste du script. Ses actions imbriquées deviennent éligibles après le délai ; la réinitialisation de l’écran réinitialise le compte à rebours. |
| **Execute Later** | Planifie une nouvelle exécution de ses actions imbriquées après le délai à chaque fois que le bloc est atteint. |
| **Comment** | Ajoute une note dans le script pour l’organisation et n’exécute aucune action. |

# Exécution du script

Les actions s’exécutent de haut en bas. Une action échouée est consignée dans le journal, puis le script continue.

Les téléchargements, l’extraction ZIP et les requêtes HTTP se terminent plus tard ; l’action suivante n’attend pas. Utilisez [**On File Downloaded via Action**](./listeners#on-file-downloaded-via-action-file_downloaded_via_action), [**On ZIP Extracted via Action**](./listeners#on-zip-extracted-via-action-zip_extracted_via_action), ou une variable de réponse HTTP lorsque le travail ultérieur dépend du résultat.

# Où pouvez-vous utiliser des scripts d’action ?

Les scripts d’action sont polyvalents et peuvent être utilisés dans toute votre mise en page. Vous pouvez les attribuer, par exemple, à :

- [**Boutons**](./elements#button) : exécuter une action lorsque le bouton est cliqué.
- [**Tickers**](./elements#ticker) : exécuter en continu un script d’action pour mettre à jour les informations affichées à l’écran dans une mise en page.
- [**Curseurs**](./elements#slider) : déclencher un script d’action chaque fois que la valeur du curseur change.
- **Événements d’écran :** exécuter des scripts lorsqu’un écran s’ouvre ou se ferme (par exemple, jouer un son lorsqu’un menu apparaît).
- [**Listeners**](./listeners) : lorsqu’un listener reçoit son événement configuré, il exécute son script d’action.
- [**Schedulers**](./schedulers) : exécuter des actions à intervalles réguliers, même lorsqu’aucun écran n’est ouvert.

# Utiliser des placeholders dans les actions

Les valeurs d’action prennent en charge du contenu dynamique via des **placeholders**. La plupart du temps, ces placeholders utilisent une syntaxe de type JSON et sont remplacés par des données en direct lorsque l’action s’exécute.

## Placeholders de type JSON

Ce sont les [placeholders](./placeholders) normaux qui peuvent être utilisés à de nombreux endroits dans les mises en page.

Ils suivent cette syntaxe :

```json
{"placeholder": "placeholder_id", "values": {"key1": "value1", "key2": "value2"}}
```

Ils peuvent récupérer des données du jeu comme le nom du joueur, les dimensions de l’écran ou des valeurs calculées à l’aide du placeholder [**Calculator**](./placeholders#calculator-calc). Vous pouvez également imbriquer des placeholders pour des utilisations plus avancées.

## Placeholders `$$` (variables)

Les valeurs `$$` sont des valeurs en lecture seule fournies à un script d’action spécifique par la fonctionnalité qui l’exécute.

Par exemple, un [Curseur](./elements#slider) fournit sa valeur actuelle sous la forme `$$value`.

Chaque [listener](./listeners) documente les valeurs `$$` qu’il fournit, comme un bouton de souris pressé ou une structure saisie.

Les noms `$$` sont sensibles à la casse et ne fonctionnent que dans le script qui les fournit. Voir [Listeners](./listeners#listener-variables).

## Délimiteurs de valeur d’action

Utilisez exactement le délimiteur indiqué pour chaque action : `:`, `||` ou `|||`. Il n’existe pas de syntaxe d’échappement pour les délimiteurs à l’intérieur d’un champ.

Les placeholders sont remplacés avant que la valeur ne soit séparée. Pour `set_variable`, seul le premier deux-points sépare le nom de la valeur ; les deux-points suivants restent dans la valeur.

## Valeurs textuelles

Les [codes de formatage FancyMenu](./text-formatting#minecraft-text-formatting) utilisent `&` à la place du caractère `§` de Minecraft partout où une action accepte du texte formaté.

- [**Send Chat Message/Command**](#send-chat-messagecommand-sendmessage) et [**Paste to Chat**](#paste-to-chat-paste_to_chat) prennent en charge ces codes de formatage.
- [**Display In Chat [Client-Side]**](#display-in-chat-client-side-display_in_chat_client_side) accepte du texte brut ou du JSON sérialisé d’un composant de texte Minecraft.
- [**Open URL in Browser**](#open-url-in-browser-openlink) applique la même conversion des codes de formatage avant de transmettre l’URL au système d’exploitation.

# Comment configurer et modifier des actions

Pour modifier les actions et les blocs d’instructions d’un élément, **faites un clic droit sur l’élément** puis sélectionnez **Manage Action Script**. Dans l’éditeur, vous pouvez :

- **Ajouter de nouvelles actions ou instructions :** insérez de nouvelles entrées d’action ou des instructions de contrôle (if, else-if, else, while) pour construire votre script.
- **Modifier des actions ou instructions existantes :** modifiez la valeur de l’action ou changez la logique de contrôle.
- **Supprimer des actions ou instructions :** supprimez les actions indésirables du script.

Créez et modifiez les scripts de listeners via [**Customization -> Manage Listeners**](./listeners#using-listeners).

# Raccourcis de l’éditeur de script d’action

## Raccourcis

- `DEL` : suppression rapide de l’entrée sélectionnée
- `ENTER` : commence l’édition en ligne de l’entrée sélectionnée (ou ouvre l’écran d’édition s’il n’existe pas d’édition en ligne pour l’entrée sélectionnée)
- `Ctrl/Command + C` : copie l’action sélectionnée (fonctionne uniquement avec les actions pour le moment)
- `Ctrl/Command + V` : colle l’action copiée précédemment
- `Ctrl/Command + Z` : retour d’un pas (annuler)
- `Ctrl/Command + Y` : avancer d’un pas (rétablir)
- `ARROW UP` : naviguer d’une entrée vers le haut à partir de l’entrée actuellement sélectionnée
- `ARROW DOWN` : naviguer d’une entrée vers le bas à partir de l’entrée actuellement sélectionnée
- `SHIFT + ARROW UP` : déplacer l’entrée sélectionnée d’un cran vers le haut
- `SHIFT + ARROW DOWN` : déplacer l’entrée sélectionnée d’un cran vers le bas
- `A` : ouvre rapidement l’écran Action Chooser pour ajouter une nouvelle action
- `Ctrl/Command + S` : terminer/enregistrer depuis la fenêtre de l’éditeur

## Édition

- Un double-clic sur la valeur d’une action vous permet de modifier la valeur sans passer par l’écran complet d’édition de la valeur.
- Les chaînes d’instructions IF (avec les instructions ELSE/ELSE-IF ajoutées), les boucles WHILE et les dossiers peuvent être réduits (uniquement visuel, n’affecte pas la logique du script).
- L’éditeur ajoute toujours les nouvelles actions sous l’entrée sélectionnée (ou imbriquées dans la chaîne/boucle/dossier sélectionné).
- Un clic droit sur l’arrière-plan gris foncé de la zone du script ouvre un menu contextuel avec des options pour ajouter des actions, des instructions et tout le reste d’important.

# Détails des actions

Cette section répertorie les actions intégrées de FancyMenu.

## Next Track (`audio_next_track`)

**But :** passe à la piste suivante dans un [élément Audio](./elements#audio)

**Valeur :** requise — `audio_element_identifier` (l’ID de l’élément audio à contrôler)

## Previous Track (`audio_previous_track`)

**But :** passe à la piste précédente dans un [élément Audio](./elements#audio)

**Valeur :** requise — `audio_element_identifier` (l’ID de l’élément audio à contrôler)

## Set Track Volume (`set_audio_element_volume`)

**But :** définit le volume d’un [élément Audio](./elements#audio) (`0.0` à `1.0`)

**Valeur :** requise — `element_identifier:volume`

## Toggle Play/Pause Track (`audio_toggle_play`)

**But :** bascule la piste actuelle d’un [élément Audio](./elements#audio) entre lecture et pause

**Valeur :** requise — `audio_element_identifier`

## Play Audio (`play_audio`)

**But :** joue une ressource audio une seule fois. L’audio démarré par cette action peut ensuite être arrêté avec [**Stop All Action Audios**](#stop-all-action-audios-stop_all_action_audios).

**Valeur :** requise — configuration JSON avec `audioSource`, `soundChannel` et `baseVolume`

**Exemple :** `{"audioSource":"[source:local]/config/fancymenu/assets/example.ogg","soundChannel":"master","baseVolume":1.0}`

**Comportement :**

- `baseVolume` est limité à `0.0`–`1.0`.
- Un canal audio inconnu utilise le canal Master.
- L’action ne peut pas s’exécuter depuis un [Ticker](./elements#ticker) asynchrone ; FancyMenu affiche une erreur à la place.
- FancyMenu attend jusqu’à dix secondes que la ressource audio soit prête.
- Les pistes démarrées avec succès peuvent être arrêtées avec [**Stop All Action Audios**](#stop-all-action-audios-stop_all_action_audios).

## Stop All Action Audios (`stop_all_action_audios`)

**But :** arrête toutes les pistes audio qui ont été lancées par l’[action **Play Audio**](#play-audio-play_audio). Cela n’arrête pas les [éléments Audio](./elements#audio), les sons d’ouverture/fermeture de menu, les sons de bouton ou d’autres systèmes audio.

**Valeur :** non requise

## Set Video Element Volume (`set_video_element_volume`)

**But :** définit le volume d’un [élément Vidéo](./video) (`0.0` à `1.0`)

**Valeur :** requise — `video_element_identifier:volume`

## Set Video Element Play Time (`set_video_element_play_time`)

**But :** avance un [élément Vidéo](./video) à un horodatage en millisecondes

**Valeur :** requise — `video_element_identifier:timestamp_ms`

## Toggle Video Element Paused State (`toggle_video_element_pause_state`)

**But :** bascule l’état de pause d’un [élément Vidéo](./video)

**Valeur :** requise — `video_element_identifier`

## Set Video Background Volume (`set_video_menu_background_volume`)

**But :** définit le volume d’un [arrière-plan vidéo de menu](./video) (`0.0` à `1.0`)

**Valeur :** requise — `background_identifier:volume`

> [!NOTE]
> Pour obtenir l’identifiant d’un arrière-plan, faites un clic droit sur l’arrière-plan de l’éditeur et cliquez sur « Copy Background Identifier ».

## Set Video Background Play Time (`set_video_menu_background_play_time`)

**But :** avance un [arrière-plan vidéo de menu](./video) à un horodatage en millisecondes

**Valeur :** requise — `background_identifier:timestamp_ms`

> [!NOTE]
> Pour obtenir l’identifiant d’un arrière-plan, faites un clic droit sur l’arrière-plan de l’éditeur et cliquez sur « Copy Background Identifier ».

## Toggle Video Background Paused State (`toggle_video_menu_background_pause_state`)

**But :** bascule l’état de pause d’un [arrière-plan vidéo de menu](./video)

**Valeur :** requise — `background_identifier`

> [!NOTE]
> Pour obtenir l’identifiant d’un arrière-plan, faites un clic droit sur l’arrière-plan de l’éditeur et cliquez sur « Copy Background Identifier ».

## Toggle Layout (`toggle_layout`)

**But :** bascule une mise en page (activer/désactiver) à partir de son nom de fichier sans `.txt`

**Valeur :** requise — `layout_name`

## Enable Layout (`enable_layout`)

**But :** active et enregistre une mise en page à partir de son nom de fichier sans `.txt`

**Valeur :** requise — `layout_name`

## Disable Layout (`disable_layout`)

**But :** désactive et enregistre une mise en page à partir de son nom de fichier sans `.txt`

**Valeur :** requise — `layout_name`

Les trois actions de mise en page enregistrent l’état dans le fichier de mise en page et mettent à jour l’écran actuel immédiatement. Utilisez le nom de fichier sensible à la casse sans `.txt`.

## Open Screen or Custom GUI (`opengui`)

**But :** ouvre un écran à partir de son identifiant (vanilla, mod ou GUI personnalisé)

**Valeur :** requise — `screen_identifier`

Copiez l’identifiant exact, sensible à la casse, depuis la surcouche de débogage [Screen Identifiers](./screen-identifiers).

Certains écrans de mod ne peuvent pas être créés directement. Si l’ouverture échoue, utilisez [**Mimic Vanilla/Mod Button**](#mimic-vanillamod-button-mimicbutton) sur un widget qui ouvre normalement cet écran.

## Close Screen (`closegui`)

**But :** ferme l’écran actif

**Valeur :** non requise

## Update Screen (`update_screen`)

**But :** réinitialise l’écran actuel

**Valeur :** non requise

## Back to Last Screen (`back_to_last_screen`)

**But :** revient au parent d’un [GUI personnalisé](./custom-guis) ou à l’instance d’écran fermée la plus récente

**Valeur :** non requise

## Join Server (`joinserver`)

**But :** connecte le joueur à un serveur Minecraft

**Valeur :** requise — `server_ip` ou `server_ip:port`

Cette action ne peut pas s’exécuter lorsqu’un monde ou un serveur est déjà chargé. Le port `25565` est utilisé lorsqu’il est omis. Si l’adresse ne figure pas dans la liste des serveurs enregistrés de Minecraft, FancyMenu l’ajoute et l’enregistre.

## Enter World (`loadworld`)

**But :** entre dans un monde Minecraft

**Valeur :** requise — `world_folder_name`

La valeur correspond au nom du dossier de sauvegarde. L’action ne fait rien si cette sauvegarde n’existe pas ou si un autre monde/serveur est déjà chargé.

## Enter/Join Last World/Server (`join_last_world`)

**But :** entre/rejoint le dernier monde ou serveur dans lequel le joueur se trouvait

**Valeur :** non requise

Cette action ne peut pas s’exécuter lorsqu’un autre monde/serveur est déjà chargé. Un serveur mémorisé qui ne se trouve pas dans la liste des serveurs enregistrés de Minecraft est ajouté et enregistré avant la connexion.

## Leave World or Server (`disconnect_server_or_world`)

**But :** quitte un monde ou un serveur et ouvre un écran spécifié

**Valeur :** requise — `screen_identifier`

Cette action ne s’exécute que lorsqu’un monde et un joueur sont chargés. La cible peut être un identifiant de [GUI personnalisé](./custom-guis) ou un [identifiant d’écran](./screen-identifiers) que FancyMenu peut construire. Si la cible ne peut pas être ouverte, FancyMenu revient à l’écran Titre.

## Quit Minecraft (`quitgame`)

**But :** quitte complètement Minecraft

**Valeur :** non requise

## Send Chat Message/Command (`sendmessage`)

**But :** envoie un message de chat ou exécute une commande de chat. Le texte du message prend en charge les [codes de formatage FancyMenu](./text-formatting#minecraft-text-formatting).

**Valeur :** requise — `message_text` ou `/command_text`

## Execute Command As Integrated Server (`execute_command_as_integrated_server`)

**But :** exécute de force une commande en solo en tant que serveur intégré, en ignorant les permissions et le réglage des cheats.

**Valeur :** requise — texte de commande, par exemple `/give @p minecraft:diamond 1`

> [!WARNING]
> Cette action ne fonctionne qu’en solo lorsque le monde **n’est pas ouvert en LAN**. Elle ne fait volontairement rien lorsqu’il n’existe aucun serveur intégré ou lorsque le serveur intégré est publié en LAN.

## Paste to Chat (`paste_to_chat`)

**But :** colle du texte formaté dans le champ de saisie du chat lorsqu’un joueur/monde est chargé

**Valeur :** requise — `true:Text` ou `false:Text`

Lorsque le chat n’est pas déjà ouvert, FancyMenu l’ouvre et définit le texte de saisie. Lorsque le chat est déjà ouvert, `true` ajoute au texte existant et `false` le remplace.

## Display In Chat [Client-Side] (`display_in_chat_client_side`)

**But :** affiche un message de chat côté client lorsqu’un monde ou un serveur est chargé. Rien n’est envoyé au serveur.

**Valeur :** requise — `text_or_json`

La valeur peut être du texte brut ou un composant de texte Minecraft sérialisé. L’action ne fait rien lorsqu’aucun monde n’est chargé.

## Send FM Data To Server (`send_fm_data_to_server`)

**But :** envoie des [données FM](./fm-data) au serveur FancyMenu actuel.

**Valeur :** requise — `data_identifier||data`

## Connect To Remote Server (`connect_to_remote_server`)

**But :** ouvre ou réutilise une connexion WebSocket initiée par le client vers un serveur distant externe.

**Valeur :** requise — URL du serveur distant, par exemple `wss://example.com/ws`

Voir [Communication avec un serveur distant](./remote-server-communication#url-modes) pour les formes d’URL acceptées.

## Send Data To Remote Server (`send_data_to_remote_server`)

**But :** ouvre ou réutilise une connexion à un serveur distant et lui envoie des données textuelles.

**Valeur :** requise — `remote_server_url||data`

## Close Remote Server Connection (`close_remote_server_connection`)

**But :** ferme une connexion spécifique à un serveur distant par ID de requête.

**Valeur :** requise — ID de requête, généralement `$$request_id` de [**On Remote Server Connected**](./listeners#on-remote-server-connected-remote_server_connected)

## Close All Remote Server Connections (`close_all_remote_server_connections`)

**But :** ferme toutes les connexions actives aux serveurs distants ouvertes par FancyMenu.

**Valeur :** non requise

## Open URL in Browser (`openlink`)

**But :** transmet une URL au gestionnaire par défaut du système d’exploitation sans invite de confirmation FancyMenu

**Valeur :** requise — `https://example.com`

Utilisez des liens `https://` de confiance. FancyMenu n’affiche pas d’invite de confirmation avant de transmettre l’URL au système d’exploitation.

## Copy Text to Clipboard (`copytoclipboard`)

**But :** copie du texte dans le presse-papiers

**Valeur :** requise — `text_to_copy`

## Print to Game Log (`print_to_log`)

**But :** écrit une ligne dans le journal du jeu

**Valeur :** requise — `text_to_log`

## Set Variable Value (FM Variable) (`set_variable`)

**But :** stocke du contenu textuel dans une [variable FancyMenu](./variables)

**Valeur :** requise — `variable_name:variable_value`

Le premier deux-points sépare le nom de la valeur. Les deux-points suivants restent dans la valeur. Les modifications sont enregistrées immédiatement.

## Clear All Variables (FM Variable) (`clear_variables`)

**But :** efface toutes les valeurs de [variables FancyMenu](./variables) stockées

**Valeur :** non requise

## Send HTTP Request (`send_http_request`)

**But :** lance une requête HTTP/HTTPS en arrière-plan ; peut consigner et/ou stocker la réponse dans une variable

**Valeur :** requise — configuration de requête HTTP

| Paramètre | Comportement |
|---|---|
| URL | Point de terminaison HTTP ou HTTPS |
| Méthode | `GET`, `POST`, `PUT`, `DELETE`, `PATCH`, `HEAD` ou `OPTIONS` |
| Body | Envoyé pour les méthodes autres que `GET` et `HEAD` |
| Content type | Valeur `Content-Type` de la requête |
| Timeout | Secondes utilisées pour la connexion et la lecture de la réponse |
| Log response | Lit et écrit la réponse dans le journal |
| Response variable | Lit la réponse et la stocke après la fin de la requête |
| Single-line response | Supprime les retours à la ligne de la réponse avant de la stocker |
| Authentication | Aucune, Basic, Bearer ou clé API |
| Headers | En-têtes de requête personnalisés facultatifs |

Les requêtes s’exécutent de manière asynchrone, donc l’action suivante n’attend pas. Les corps de réponse ne sont lus que lorsque la journalisation est activée ou qu’une variable de réponse est configurée ; les corps non réussis sont lus depuis la réponse d’erreur. Ne stockez pas de mots de passe ou de jetons d’accès dans la configuration de l’action.

## Manage Resource Pack (`manage_resource_pack`)

**But :** active, désactive ou bascule un pack de ressources, avec un rechargement facultatif

**Valeur :** requise — `pack_name_or_id|||MODE|||reload_bool`

Les noms affichés et les ID internes des packs sont comparés sans tenir compte de la casse. Les packs marqués comme obligatoires ne peuvent pas être désactivés.

## Reload Resource Packs (`reload_resource_packs`)

**But :** recharge les packs de ressources de Minecraft. Un délai de réutilisation intégré de cinq secondes ignore les déclenchements répétés pendant cette période pour éviter le spam de rechargement.

**Valeur :** non requise

## Reload FancyMenu (`reloadmenu`)

**But :** recharge les mises en page, les [GUIs personnalisés](./custom-guis), les [panoramas](./panoramas), les [diaporamas](./slideshows), les paramètres et les ressources gérées par FancyMenu

**Valeur :** non requise

Cela ne recharge pas les packs de ressources de Minecraft. Utilisez [**Reload Resource Packs**](#reload-resource-packs-reload_resource_packs) pour cela.

> [!WARNING]
> Le rechargement est coûteux. Déclenchez-le depuis une action de bouton volontaire, pas depuis un [Ticker](./elements#ticker) ou un [listener](./listeners) fréquemment déclenché.

## Toggle Element Animator (`toggle_element_animator`)

**But :** bascule l’état de lecture enregistré et réinitialise la timeline Animator active correspondante

**Valeur :** requise — `animator_identifier`

Voir [Element Animator](./element-animator) pour la configuration et les détails de l’identifiant.

## Enable Element Animator (`enable_element_animator`)

**But :** active la lecture ; une timeline Animator active ne se réinitialise que lorsque l’état passe de désactivé à activé

**Valeur :** requise — `animator_identifier`

## Disable Element Animator (`disable_element_animator`)

**But :** désactive la lecture et réinitialise la timeline Animator active correspondante

**Valeur :** requise — `animator_identifier`

## Reset Element Animator (`reset_element_animator`)

**But :** réinitialise la timeline Animator active correspondante sans modifier l’activation ou non de la lecture

**Valeur :** requise — `animator_identifier`

## Mimic Vanilla/Mod Button (`mimicbutton`)

**But :** imite l’action de clic d’un bouton vanilla ou d’un bouton de mod

**Valeur :** requise — le [localisateur de widget](./widget-locators) complet, par exemple `example.menu.identifier:505280`

## Mimic Keybind (`mimic_keybind`)

**But :** exécute un raccourci clavier ou souris Minecraft, avec maintien facultatif

**Valeur :** requise — `keybind_id|||keep_pressed_bool|||duration_ms`

| Champ | Signification |
|---|---|
| `keybind_id` | Identifiant de raccourci Minecraft, comme `key.jump` |
| `keep_pressed_bool` | `true` pour maintenir la touche ; `false` pour une pression normale |
| `duration_ms` | Durée du maintien lorsque `keep_pressed_bool` est `true` ; valeur par défaut `1000` |

## Set Text Input Field Value (`set_text_input_field_value`)

**But :** définit la valeur d’un [champ de saisie de texte](./elements#text-input-field) personnalisé ou Vanilla à partir de l’identifiant de l’élément.

**Valeur :** requise — `element_identifier|||new_value|||force_set_when_inactive`

Les trois champs doivent être séparés par le délimiteur triple barre verticale `|||`. Réglez `force_set_when_inactive` sur `true` pour mettre aussi à jour un champ de saisie désactivé ; lorsqu’il est `false`, les champs inactifs restent inchangés.

## Create File in Game Directory (`create_file_in_game_dir`)

**But :** crée un fichier vide dans le répertoire de jeu actif. Accepte le préfixe `.minecraft/` pour cibler le répertoire Minecraft conventionnel (qui peut différer de l’instance actuelle).

**Valeur :** requise — `file_path`

Exemple : `config/some_mod_folder/new_file.txt`. Les répertoires parents manquants sont créés ; un fichier existant n’est pas modifié.

## Delete File/Folder in Game Directory (`delete_file_in_game_dir`)

**But :** supprime un fichier ou supprime récursivement un dossier dans le répertoire de jeu actif. Accepte `.minecraft/` pour cibler le répertoire Minecraft conventionnel. Ajoutez `*` pour supprimer **tous les fichiers directement à l’intérieur** d’un dossier (ignore les sous-dossiers et conserve le dossier).

**Valeur :** requise — `target_path`

Par exemple, `config/downloads/*` supprime les fichiers directement dans `config/downloads/`, mais ne parcourt ni ne supprime ses sous-dossiers.

## Copy File/Folder in Game Directory (`copy_file_in_game_dir`)

**But :** copie au sein du répertoire de jeu actif ; `.minecraft/` cible le répertoire Minecraft conventionnel. Un dossier nommé est copié récursivement. Ajoutez `*` au chemin source pour copier uniquement chaque fichier enfant direct ; la destination doit être un dossier et ne peut pas utiliser `*`.

**Valeur :** requise — `source||destination`

Par exemple, `config/source/*||config/destination/` copie uniquement les fichiers directement dans `config/source/`. Avec une source générique, FancyMenu crée le dossier de destination si nécessaire mais ne copie aucun sous-dossier source. La copie refuse tout fichier de destination existant/conflit au lieu de l’écraser.

## Move File/Folder in Game Directory (`move_file_in_game_dir`)

**But :** déplace au sein du répertoire de jeu actif ; `.minecraft/` cible le répertoire Minecraft conventionnel. Ajoutez `*` au chemin source pour déplacer uniquement chaque fichier enfant direct ; la destination doit être un dossier et ne peut pas utiliser `*`.

**Valeur :** requise — `source||destination`

Par exemple, `config/source/*||config/destination/` déplace uniquement les fichiers directement dans `config/source/`. Avec une source générique, FancyMenu crée le dossier de destination si nécessaire mais laisse les sous-dossiers source en place. Le déplacement refuse tout fichier de destination existant/conflit au lieu de l’écraser.

## Rename File/Folder in Game Directory (`rename_file_in_game_dir`)

**But :** renomme un fichier ou un dossier dans son dossier parent actuel ; `.minecraft/` cible le répertoire Minecraft conventionnel. Conserve le contenu intact et refuse un nom cible existant.

**Valeur :** requise — `path||new_name`

## Download File to Game Directory (`download_file_to_game_dir`)

**But :** télécharge un fichier en arrière-plan vers un dossier relatif au répertoire de jeu actif ; `.minecraft/` cible le répertoire Minecraft conventionnel.

**Valeur :** requise — `url||target_folder`

Le deuxième champ est un **dossier cible**, pas un chemin complet de fichier de destination. FancyMenu crée le dossier si nécessaire et détermine le nom du fichier à partir de l’en-tête `Content-Disposition` de la réponse, puis à défaut à partir du chemin de l’URL. Le nom résolu est décodé depuis l’URL et nettoyé avant utilisation ; si aucune source ne fournit de nom exploitable, FancyMenu en génère un. Un fichier existant portant le même nom est écrasé.

Le [**On File Downloaded via Action** listener](./listeners#on-file-downloaded-via-action-file_downloaded_via_action) se déclenche après les tentatives de téléchargement réussies et échouées et expose l’URL, le chemin cible résolu et l’état de réussite.

En cas de réussite, `$$target_file_path` est le chemin du fichier enregistré. En cas d’échec, il peut contenir uniquement le dossier cible car aucun nom de fichier final n’a été résolu.

## Extract ZIP File In Game Directory (`extract_zip_file_in_game_dir`)

**But :** extrait un ZIP dans un dossier cible à l’intérieur du répertoire de jeu actif ou du répertoire `.minecraft` conventionnel. Déclenche [**On ZIP Extracted via Action**](./listeners#on-zip-extracted-via-action-zip_extracted_via_action) une fois terminé.

**Valeur :** requise — `source_zip_path||target_folder_path`

Les fichiers existants portant le même nom sont remplacés. N’extrayez que des fichiers ZIP de confiance.

## Open File/Folder In Game Directory (`open_file_folder_in_game_dir`)

**But :** ouvre un fichier ou un dossier avec l’application par défaut du système d’exploitation. La cible doit rester à l’intérieur du répertoire de jeu ou du répertoire `.minecraft` par défaut pour des raisons de sécurité.

**Valeur :** requise — `target_path`

## Write File in Game Directory (`write_file_in_game_dir`)

**But :** écrit ou ajoute du texte dans le répertoire de jeu actif ; `.minecraft/` cible le répertoire Minecraft conventionnel. Crée le fichier et les dossiers parents s’ils sont manquants. `\n` insère des sauts de ligne ; `append_bool=false` remplace un fichier existant.

**Valeur :** requise — `path|||content|||append_bool`

## Select File from System (`select_file_to_game_dir`)

**But :** ouvre un sélecteur de fichiers natif et copie le fichier sélectionné dans le répertoire de jeu actif, ou dans `.minecraft/` conventionnel lorsqu’il est préfixé. Prend en charge les filtres d’extension, un libellé de filtre personnalisé et un basculement d’écrasement.

**Valeur :** requise — `target_path|||filter_description|||extensions|||overwrite_bool`

`target_path` est le chemin complet du fichier de destination. Séparez plusieurs extensions par `;` ou `,`, par exemple `png;jpg` ; une liste d’extensions vide autorise tous les fichiers. Si `overwrite_bool` est `false`, l’action échoue au lieu de remplacer un fichier de destination existant.

Le [**On File Selected** listener](./listeners#on-file-selected-file_selected_via_action) se déclenche lorsque le fichier est copié, que la sélection est annulée ou qu’elle échoue. Il expose le chemin sélectionné, le chemin cible résolu, les états de réussite/d’annulation et une raison d’échec.

## Show Toast (`show_toast`)

**But :** affiche une notification toast configurable

**Valeur :** requise — configuration JSON du toast

L’éditeur enregistre cette action sous forme de JSON. Préférez sa fenêtre de configuration plutôt que de modifier la valeur manuellement.

| Champ | Signification |
|---|---|
| `width` | Limité à `120`–`320` pixels |
| `durationMs` | Limité à `1000`–`600000` millisecondes |
| `title` | Texte brut, composant de texte Minecraft sérialisé, ou vide |
| `message` | Texte brut, composant de texte sérialisé, ou vide |
| `iconSource` | [Source d’image](./resources) facultative |
| `backgroundSource` | [Source d’image](./resources) facultative |

## Start Scheduler (`start_scheduler`)

**But :** démarre un scheduler à partir de son ID de scheduler.

**Valeur :** requise — `scheduler_id`

Voir [Schedulers](./schedulers) pour créer et gérer les IDs de scheduler.

## Stop Scheduler (`stop_scheduler`)

**But :** arrête un scheduler à partir de son ID de scheduler.

**Valeur :** requise — `scheduler_id`

## Set Minecraft Option (`edit_minecraft_option`)

**But :** modifie une option de configuration Minecraft

**Valeur :** requise — `option_name:set_to_value`
