---
title: Scripts d’action
description: >-
  Faites agir les boutons et les menus grâce aux scripts d’action, et découvrez
  toutes les actions de FancyMenu.
sourceBlobSha: 07ed5af6f189a91c518131cf3a7ab7a1e0a8305d
---

# Scripts d’action

Un script d’action est une liste de tâches que FancyMenu exécute lorsqu’un événement se produit, par exemple quand on clique sur un bouton ou qu’un menu s’ouvre. Chaque tâche est une action : ouvrir un menu, rejoindre un serveur, afficher un message, jouer un son, et bien plus encore. Des instructions comme IF et WHILE déterminent quelles actions sont exécutées et à quelle fréquence.

> [!CAUTION]
> Les scripts d’action peuvent modifier des fichiers, contacter des serveurs, ouvrir des liens et exécuter des commandes. N’utilisez que des scripts provenant de mises en page auxquelles vous faites confiance.

<img width="800" alt="Le script d’action d’un bouton est créé dans l’éditeur de mise en page : Edit Action Script, le sélecteur d’action avec Show Toast, puis le titre et le message de la notification" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/action_script_make.gif?raw=true">

# Créer un script d’action

1. Dans l’éditeur de mise en page, faites un clic droit sur un bouton, puis cliquez sur **Edit Action Script**.
2. Appuyez sur `A` pour ouvrir le sélecteur d’action.
3. Recherchez l’action, cliquez dessus, puis cliquez sur **Next Step**.
4. Configurez l’action dans sa fenêtre, puis cliquez sur **Done**. Pour les actions sans paramètres, il suffit de cliquer sur **Done** dans le sélecteur.
5. Cliquez sur **Done** dans l’éditeur de script, puis enregistrez la mise en page.

En dehors de l’éditeur, le bouton exécute son script lorsque vous cliquez dessus :

<img width="800" alt="Un clic sur le bouton What's New? de l’écran titre affiche une notification avec le titre et le message de mise à jour" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/action_script_use.gif?raw=true">

> [!TIP]
> Faites un clic droit dans la zone du script et ouvrez **Add Action** pour afficher la liste de toutes les actions. Faites un clic droit sur une action de cette liste pour l’ajouter aux favoris : elle apparaîtra alors en haut de la liste.

# Où utiliser les scripts d’action

| Emplacement | S’exécute lorsque… | Où le modifier |
|---|---|---|
| [Bouton](/elements#button) | On clique sur le bouton. | Clic droit sur le bouton -> **Edit Action Script** |
| [Curseur](/elements#slider) | La valeur du curseur change. `$$value` correspond à la nouvelle valeur. | Clic droit sur le curseur -> **Edit Action Script** |
| [Case à cocher](/elements#checkbox) | On coche ou décoche la case. `$$value` correspond à son nouvel état : `true` ou `false`. | Clic droit sur la case -> **Edit Action Script** |
| [Ticker](/elements#ticker) | Selon son **Tick Mode** : en boucle, une fois par session de jeu ou une fois au chargement du menu. | Clic droit sur le ticker -> **Edit Action Script** |
| Ouverture d’un menu | Le menu de la mise en page s’ouvre. | Clic droit sur l’arrière-plan de l’éditeur -> **Edit 'Open Screen' Action Script** |
| Fermeture d’un menu | Le menu de la mise en page se ferme. | Clic droit sur l’arrière-plan de l’éditeur -> **Edit 'Close Screen' Action Script** |
| [Écouteurs](/listeners) | Leur événement se produit, par exemple à la pression d’une touche ou à la réception d’un message dans le chat. | **barre de menu -> Customization -> Manage Listeners** |
| [Planificateurs](/schedulers) | Leur minuteur se déclenche, même si aucun menu n’est ouvert. | **barre de menu -> Customization -> Manage Schedulers** |

Les scripts d’ouverture et de fermeture se trouvent aussi dans le menu **Layout -> Layout Properties** de l’éditeur.

# L’éditeur de scripts

- Les actions s’exécutent de haut en bas. Les entrées d’une instruction ou d’un dossier sont indentées sous celle-ci.
- Les nouvelles entrées sont ajoutées sous l’entrée sélectionnée. Si une instruction ou un dossier est sélectionné, elles sont ajoutées au début de celui-ci.
- Double-cliquez sur une valeur pour la modifier directement dans la liste. Les valeurs accompagnées d’un bref résumé ouvrent plutôt leur fenêtre de configuration.
- Faites glisser les entrées pour les déplacer. Les chaînes IF, les boucles et les dossiers peuvent être repliés à l’aide du petit bouton situé devant eux. Cela ne modifie que l’affichage.
- La barre à droite représente l’ensemble du script. Cliquez dessus pour accéder directement à une partie du script.
- Faites un clic droit dans la zone du script pour accéder aux autres options, comme l’ajout d’instructions et **Export Action Script for AI** (voir [Exporter pour l’IA](/export-for-ai)).
- **Cancel** ou la fermeture de la fenêtre annule vos modifications. Si vous en avez apporté, l’éditeur vous le demande d’abord.

## Raccourcis

Sur macOS, `Ctrl` correspond à `Cmd`.

| Raccourci | Fonction |
|---|---|
| `A` | Ouvre le sélecteur d’action. |
| `Enter` | Modifie l’entrée sélectionnée. |
| `Delete` | Supprime l’entrée sélectionnée. |
| `Up` / `Down` | Sélectionne l’entrée au-dessus ou au-dessous. |
| `Shift + Up` / `Shift + Down` | Déplace l’entrée sélectionnée vers le haut ou le bas. |
| `Ctrl + C` / `Ctrl + V` | Copie et colle une action. Les instructions et les blocs ne peuvent pas être copiés. |
| `Ctrl + Z` | Annule la dernière action. |
| `Ctrl + Y` ou `Ctrl + Shift + Z` | Rétablit la dernière action annulée. |
| `Ctrl + S` | Enregistre le script et ferme l’éditeur, comme **Done**. |

# Instructions

Les instructions déterminent quelles actions s’exécutent et à quelle fréquence. Ajoutez-les en faisant un clic droit dans la zone du script.

## If, Else-If et Else

**Add IF Statement** vous demande de définir des [conditions](/conditions). Les actions à l’intérieur de IF ne s’exécutent que si ces conditions sont remplies.

Faites un clic droit sur un IF pour ajouter des éléments à sa chaîne :

- **Append ELSE-IF Statement** : vérifie ses propres conditions si le IF précédent ne s’est pas exécuté.
- **Append ELSE Statement** : s’exécute si aucune instruction précédente de la chaîne ne s’est exécutée.

Par exemple, un IF avec **Is Layout Enabled** peut afficher une notification uniquement lorsque la mise en page hivernale est activée, tandis qu’un ELSE joue un son dans le cas contraire.

## Boucle While

**Add WHILE Loop** répète ses actions tant que ses [conditions](/conditions) sont remplies.

Chaque exécution s’arrête au bout de 3 secondes. Ainsi, une boucle sans fin ne peut pas bloquer le jeu. Ce n’est pas un minuteur : pour déclencher des actions plus tard ou de façon répétée, utilisez [Execute Later](#execute-later), un [Ticker](/elements#ticker) ou un [planificateur](/schedulers).

## Boucle For Each

**Add FOR EACH Loop** exécute ses actions une fois pour chaque entrée d’une [variable de liste](/variables#text-and-list-variables), de la première à la dernière.

- `$$list_entry` correspond à l’entrée actuelle et `$$list_index` à son index. La première entrée a l’index 0.
- Ces deux variables sont utilisables dans les valeurs des actions et les conditions de la boucle.
- Saisissez le nom de la liste sans `$$`, par exemple `quest_log`. Les espaces réservés sont également acceptés dans le nom.
- La boucle lit la liste une seule fois au démarrage. Les actions qu’elle contient peuvent donc modifier la liste sans risque.
- Comme les boucles WHILE, chaque exécution s’arrête au bout de 3 secondes.

Consultez [Parcourir une liste](/variables#going-through-a-list) pour voir des exemples.

# Blocs

Les blocs modifient le moment où les actions s’exécutent ou permettent de garder votre script organisé. Ajoutez-les en faisant un clic droit dans la zone du script.

## Bloc Delay Gate

**Add DELAY GATE Block** retarde ses actions pendant une durée en millisecondes (`1000` correspond à une seconde).

- La première fois que le script atteint le bloc, le minuteur démarre et les actions du bloc sont ignorées. Le reste du script s’exécute immédiatement.
- Si le script atteint de nouveau le bloc avant la fin du délai, les actions sont encore ignorées.
- Une fois le délai écoulé, les actions du bloc s’exécutent chaque fois que le script l’atteint.
- Dans les scripts d’éléments, le minuteur repart de zéro lorsque le menu est rouvert ou redimensionné.

Ce bloc est donc pratique avec les [Tickers](/elements#ticker), par exemple pour afficher quelque chose seulement après quelques secondes d’ouverture du menu. Il ne déclenche jamais d’action de lui-même : pour cela, utilisez Execute Later.

## Execute Later

**Add EXECUTE LATER Block** exécute ses actions une seule fois, après un délai en millisecondes. Le reste du script s’exécute immédiatement.

Chaque fois que le script atteint le bloc, un nouveau compte à rebours démarre. Ce bloc est adapté aux scripts qui ne s’exécutent qu’une fois, par exemple au clic sur un bouton ou à l’ouverture d’un menu.

## Dossier

**Add Folder** regroupe des actions sous un nom. Il exécute toutes les actions qu’il contient et permet simplement de garder les scripts longs bien organisés. Double-cliquez sur son nom pour le renommer.

## Commentaire

**Add Comment** ajoute une note pour vous-même. Elle n’a aucun effet. Double-cliquez dessus pour la modifier.

# Fonctionnement des scripts

- Les actions s’exécutent de haut en bas. Si une action échoue, une erreur est inscrite dans le journal du jeu, mais le reste du script continue de s’exécuter.
- Les espaces réservés contenus dans les valeurs sont remplacés par leur valeur actuelle au moment de l’exécution de l’action. Une action voit donc les modifications effectuées par les actions précédentes.
- Les téléchargements, l’extraction de fichiers ZIP et les requêtes Web s’effectuent en arrière-plan. L’action suivante ne les attend pas. Pour lancer des actions une fois ces opérations terminées, utilisez les écouteurs [**On File Downloaded via Action**](/listeners#on-file-downloaded-via-action) et [**On ZIP Extracted via Action**](/listeners#on-zip-extracted-via-action), ou une variable de réponse de [**Send HTTP Request**](#send-http-request).

# Valeurs des actions

La plupart des actions nécessitent une valeur, comme l’adresse d’un serveur. Les valeurs simples sont du texte que vous saisissez. Les actions comportant plus de paramètres ont leur propre fenêtre.

## Espaces réservés

Les valeurs peuvent contenir des [espaces réservés](/placeholders), comme le nom du joueur. Ils sont remplacés lorsque l’action s’exécute :

```
/say Welcome back, {"placeholder":"playername"}!
```

## Variables $$

Saisissez `$$` suivi du nom d’une variable pour utiliser sa valeur dans une action ou une condition. Les majuscules et les minuscules comptent dans les noms. Cela fonctionne avec deux types de variables :

### Vos propres variables

Toutes les variables que vous créez dans **barre de menu -> Customization -> Manage Variables** peuvent être utilisées avec `$$` suivi de leur nom. Une variable nommée `coins` s’écrit `$$coins` dans tous les scripts. Par exemple, **Display In Chat [Client-Side]**, avec la valeur suivante, indique au joueur combien de pièces il possède :

```
&6You have $$coins coins!
```

Consultez [Variables](/variables) pour apprendre à les créer et à les modifier.

### Variables du script

Certaines fonctionnalités fournissent leurs propres variables au script :

- Un [curseur](/elements#slider) fournit `$$value`, qui correspond à sa nouvelle valeur.
- Une [case à cocher](/elements#checkbox) fournit `$$value`, qui correspond à son nouvel état : `true` ou `false`.
- Une [boucle For Each](#boucle-for-each) fournit `$$list_entry` et `$$list_index`.
- Chaque [écouteur](/listeners#listener-variables) indique les variables qu’il fournit, comme la touche qui a été pressée.

Ces variables n’existent que pendant l’exécution du script. Si une variable du script porte le même nom que l’une de vos variables, `$$name` désigne la variable du script.

# Toutes les actions

Voici toutes les actions de FancyMenu, classées par fonction.

## Écrans et menus

### Ouvrir un écran ou une interface personnalisée

**Identifiant :** `opengui`

Ouvre un menu du jeu, d’un mod ou une [interface personnalisée](/custom-guis).

**Valeur :** l’[identifiant de l’écran](/screen-identifiers), par exemple `options_screen`

Les majuscules et les minuscules comptent. Certains menus de mods ne peuvent pas être ouverts de cette façon. Dans ce cas, utilisez [**Mimic Vanilla/Mod Button**](#imiter-un-bouton-vanillamod) sur un bouton qui permet de les ouvrir.

### Fermer l’écran

**Identifiant :** `closegui`

Ferme le menu ouvert. En dehors d’un monde, l’écran titre s’ouvre.

**Valeur :** aucune

### Actualiser l’écran

**Identifiant :** `update_screen`

Reconstruit le menu ouvert, comme lors du redimensionnement de la fenêtre. Pratique après avoir modifié l’échelle de l’interface ou d’autres options.

**Valeur :** aucune

### Revenir à l’écran précédent

**Identifiant :** `back_to_last_screen`

Revient au menu qui était ouvert auparavant. Pour une [interface personnalisée](/custom-guis), il s’agit du menu depuis lequel elle a été ouverte.

**Valeur :** aucune

### Afficher une notification

**Identifiant :** `show_toast`

Affiche une notification dans le coin supérieur droit. Configurez-la dans sa fenêtre :

- **Toast Width** : de 120 à 320 pixels.
- **Duration (ms)** : durée d’affichage, de 1 seconde (`1000`) à 10 minutes.
- **Title** et **Message** : texte avec des [codes de mise en forme](/text-formatting#minecraft-text-formatting), ou au format JSON des composants de texte Minecraft.
- **Icon Texture Source** et **Background Texture Source** : [images](/resources) facultatives. Les icônes rendent mieux en 20 x 20 pixels ; les arrière-plans doivent faire 32 pixels de haut et avoir la même largeur que la notification.

### Imiter un bouton Vanilla/Mod

**Identifiant :** `mimicbutton`

Clique sur un bouton du jeu ou d’un mod comme si le joueur avait cliqué dessus.

**Valeur :** le [sélecteur de widget](/widget-locators) du bouton, par exemple `title_screen:mc_titlescreen_options_button`

Pour l’obtenir, faites un clic droit sur le bouton dans l’éditeur et cliquez sur **Copy Widget Locator**.

## Mises en page et éléments

### Activer/désactiver une mise en page

**Identifiant :** `toggle_layout`

Désactive une mise en page si elle est activée, et l’active si elle est désactivée.

**Valeur :** le nom de la mise en page, sans `.txt`, par exemple `winter_title_screen`

### Activer une mise en page

**Identifiant :** `enable_layout`

Active une mise en page.

**Valeur :** le nom de la mise en page, sans `.txt`

### Désactiver une mise en page

**Identifiant :** `disable_layout`

Désactive une mise en page.

**Valeur :** le nom de la mise en page, sans `.txt`

Ces trois actions enregistrent la modification et actualisent immédiatement le menu ouvert. Les majuscules et les minuscules comptent dans le nom.

### Activer/désactiver un animateur d’élément

**Identifiant :** `toggle_element_animator`

Active un [animateur d’élément](/element-animator) s’il est désactivé, et le désactive s’il est activé. L’animation reprend depuis le début. L’état est conservé.

**Valeur :** l’identifiant de l’animateur d’élément

### Activer un animateur d’élément

**Identifiant :** `enable_element_animator`

Active un [animateur d’élément](/element-animator). S’il était désactivé, son animation reprend depuis le début.

**Valeur :** l’identifiant de l’animateur d’élément

### Désactiver un animateur d’élément

**Identifiant :** `disable_element_animator`

Désactive un [animateur d’élément](/element-animator) et réinitialise son animation.

**Valeur :** l’identifiant de l’animateur d’élément

### Réinitialiser un animateur d’élément

**Identifiant :** `reset_element_animator`

Relance l’animation d’un [animateur d’élément](/element-animator) depuis le début, sans l’activer ni le désactiver.

**Valeur :** l’identifiant de l’animateur d’élément

### Définir la valeur d’un champ de saisie de texte

**Identifiant :** `set_text_input_field_value`

Définit le texte d’un [champ de saisie de texte](/elements#text-input-field), qu’il provienne de FancyMenu ou du jeu.

**Valeur :** `element_identifier|||text|||force`

Si `force` est défini sur `true`, le texte change également lorsque le champ est désactivé (inactif).

### Faire défiler un élément

**Identifiant :** `scroll_scroll_area`

Fait défiler une [zone défilante](/scrollable-areas) ou un élément [Texte](/elements#text). Configurez le défilement dans sa fenêtre :

- **Identifier of the Element to Scroll** : la zone ou l’élément Texte à faire défiler.
- **Scroll To** :
  - **Start** ou **End**.
  - **Position** : les **Horizontal Position** et **Vertical Position** en pixels. Laissez l’une des valeurs vide pour la conserver.
  - **Element** (zones uniquement) : fait défiler jusqu’à ce que l’élément indiqué dans **Identifier of the Element to Scroll To** se trouve au début.
  - **Line Number** (éléments Texte uniquement) : la première ligne porte le numéro `1`.
  - **Line with Text** (éléments Texte uniquement) : la première ligne contenant le **Text in the Line**. Les majuscules et les minuscules ne comptent pas.
- **Glide There** : fait défiler progressivement plutôt que de sauter directement à la position voulue. Le défilement fluide doit être activé pour l’élément.

Ne fait rien si l’élément n’existe pas.

## Audio et vidéo

### Piste suivante

**Identifiant :** `audio_next_track`

Passe à la piste suivante d’un [élément Audio](/elements#audio).

**Valeur :** l’identifiant de l’élément Audio, par exemple `menu_music`

### Piste précédente

**Identifiant :** `audio_previous_track`

Revient à la piste précédente d’un [élément Audio](/elements#audio).

**Valeur :** l’identifiant de l’élément Audio

### Définir le volume de la piste

**Identifiant :** `set_audio_element_volume`

Définit le volume d’un [élément Audio](/elements#audio), de `0.0` (0 %) à `1.0` (100 %).

**Valeur :** `element_identifier:volume`, par exemple `menu_music:0.5`

### Lire/mettre en pause une piste

**Identifiant :** `audio_toggle_play`

Met en pause un [élément Audio](/elements#audio) en cours de lecture, ou reprend sa lecture s’il est en pause.

**Valeur :** l’identifiant de l’élément Audio

### Lire un fichier audio

**Identifiant :** `play_audio`

Lit un fichier audio une fois. Configurez-le dans sa fenêtre : **Audio Source**, **Sound Channel** et **Base Volume** (jusqu’à 100 %).

- FancyMenu attend jusqu’à dix secondes que le fichier audio soit chargé.
- Ne fonctionne pas dans un [Ticker](/elements#ticker) qui s’exécute en arrière-plan (de façon asynchrone). FancyMenu affiche alors une erreur.

[**Stop All Action Audios**](#arreter-tous-les-sons-des-actions) arrête les sons lancés par cette action.

### Arrêter tous les sons des actions

**Identifiant :** `stop_all_action_audios`

Arrête tous les sons lancés par [**Play Audio**](#lire-un-fichier-audio). Les éléments Audio, les sons des menus et ceux des boutons continuent de jouer.

**Valeur :** aucune

### Définir le volume d’un élément vidéo

**Identifiant :** `set_video_element_volume`

Définit le volume d’un [élément Vidéo](/video), de `0.0` (0 %) à `1.0` (100 %).

**Valeur :** `video_element_identifier:volume`

### Définir le temps de lecture d’un élément vidéo

**Identifiant :** `set_video_element_play_time`

Passe à un instant donné d’un [élément Vidéo](/video), en millisecondes.

**Valeur :** `video_element_identifier:time_in_ms`, par exemple `intro_video:30000`

### Lire/mettre en pause un élément vidéo

**Identifiant :** `toggle_video_element_pause_state`

Met en pause un [élément Vidéo](/video) en cours de lecture, ou reprend sa lecture s’il est en pause.

**Valeur :** l’identifiant de l’élément Vidéo

### Définir le volume de l’arrière-plan vidéo

**Identifiant :** `set_video_menu_background_volume`

Définit le volume d’un [arrière-plan vidéo de menu](/video), de `0.0` (0 %) à `1.0` (100 %).

**Valeur :** `background_identifier:volume`

> [!NOTE]
> Pour obtenir l’identifiant d’un arrière-plan de menu, faites un clic droit sur l’arrière-plan de l’éditeur, puis cliquez sur **Copy Background Identifier**.

### Définir le temps de lecture de l’arrière-plan vidéo

**Identifiant :** `set_video_menu_background_play_time`

Passe à un instant donné d’un [arrière-plan vidéo de menu](/video), en millisecondes.

**Valeur :** `background_identifier:time_in_ms`

### Lire/mettre en pause l’arrière-plan vidéo

**Identifiant :** `toggle_video_menu_background_pause_state`

Met en pause un [arrière-plan vidéo de menu](/video) en cours de lecture, ou reprend sa lecture s’il est en pause.

**Valeur :** l’identifiant de l’arrière-plan du menu

## Mondes et serveurs

### Rejoindre un serveur

**Identifiant :** `joinserver`

Se connecte à un serveur Minecraft.

**Valeur :** `adresse` ou `adresse:port`, par exemple `play.example.net`

Si aucun port n’est indiqué, `25565` est utilisé. Si un monde ou un serveur est déjà chargé, une erreur s’affiche. Les serveurs absents de la liste des serveurs y sont ajoutés.

### Entrer dans un monde

**Identifiant :** `loadworld`

Charge un monde solo.

**Valeur :** le nom du dossier du monde dans `saves`, par exemple `Survival Island`

Ne fait rien si le monde n’existe pas. Si un monde ou un serveur est déjà chargé, une erreur s’affiche.

### Entrer dans le dernier monde/rejoindre le dernier serveur

**Identifiant :** `join_last_world`

Charge le monde ou rejoint le serveur auquel le joueur a joué en dernier.

**Valeur :** aucune

Si un monde ou un serveur est déjà chargé, une erreur s’affiche. Les serveurs absents de la liste des serveurs y sont ajoutés.

### Quitter un monde ou un serveur

**Identifiant :** `disconnect_server_or_world`

Quitte le monde ou le serveur et ouvre un menu.

**Valeur :** l’[identifiant de l’écran](/screen-identifiers) du menu à ouvrir, par exemple `title_screen`

Fonctionne uniquement lorsqu’un monde est chargé. Les [interfaces personnalisées](/custom-guis) sont également prises en charge. Si le menu ne peut pas être ouvert, l’écran titre s’ouvre.

## Chat et commandes

### Envoyer un message dans le chat/une commande

**Identifiant :** `sendmessage`

Envoie un message dans le chat ou exécute une commande, comme si le joueur l’avait saisie.

**Valeur :** le message, ou une commande précédée de `/`, par exemple `/spawn`

### Exécuter une commande en tant que serveur intégré

**Identifiant :** `execute_command_as_integrated_server`

Exécute une commande en solo en tant que serveur, quelles que soient les permissions du joueur ou l’activation des commandes de triche.

**Valeur :** la commande, par exemple `/give @p minecraft:diamond 1`

> [!WARNING]
> Fonctionne uniquement en solo lorsque le monde n’est pas ouvert au réseau local. Dans tous les autres cas, ne fait rien.

### Coller dans le chat

**Identifiant :** `paste_to_chat`

Insère du texte dans le champ de saisie du chat lorsqu’un monde est chargé. Si le chat n’est pas ouvert, il s’ouvre avec le texte.

**Valeur :** `true:text` ajoute le texte à celui déjà saisi ; `false:text` le remplace

### Afficher dans le chat [côté client]

**Identifiant :** `display_in_chat_client_side`

Affiche un message dans le chat que seul ce joueur voit. Rien n’est envoyé au serveur.

**Valeur :** le texte, avec des [codes de mise en forme](/text-formatting#minecraft-text-formatting) ou au format JSON des composants de texte Minecraft, par exemple `&aWelcome back!`

Ne fait rien si aucun monde n’est chargé.

## Variables et listes

### Définir la valeur d’une variable (variable FM)

**Identifiant :** `set_variable`

Définit une [variable](/variables).

**Valeur :** `variable_name:value`, par exemple `coins:100`

- Seul le premier `:` sépare le nom de la valeur.
- Les [variables de liste](/variables#text-and-list-variables) restent des listes : un tableau JSON comme `["a","b"]` devient leurs entrées ; tout autre texte devient leur unique entrée ; un texte vide vide la liste.

### Supprimer une variable (variable FM)

**Identifiant :** `delete_variable`

Supprime complètement une [variable](/variables). Toutes les autres variables sont conservées. Pour simplement la vider, utilisez [**Set Variable Value (FM Variable)**](#definir-la-valeur-dune-variable-variable-fm).

**Valeur :** le nom de la variable

### Effacer toutes les variables (variable FM)

**Identifiant :** `clear_variables`

Supprime toutes les [variables](/variables), qu’il s’agisse de variables de texte ou de liste.

**Valeur :** aucune

### Ajouter à une liste (variable FM)

**Identifiant :** `add_to_list`

Ajoute une entrée à une [variable de liste](/variables#list-actions).

- **List Variable** : le nom de la liste. Si aucune variable ne porte encore ce nom, l’action crée la liste.
- **New Entry** : le texte de l’entrée.
- **Index (Optional)** : l’emplacement de l’entrée. Si ce champ est vide, l’entrée est ajoutée à la fin. Les entrées suivantes sont décalées d’une position.
- **Skip If Already in List** : n’ajoute rien si la liste contient déjà une entrée identique. **Ignore Case** considère `Apple` et `apple` comme identiques.

### Définir une entrée de liste (variable FM)

**Identifiant :** `set_list_entry`

Remplace l’entrée à un **Index** d’une [variable de liste](/variables#list-actions) par une **New Value**. Ne fait rien si la liste ne contient aucune entrée à cet index.

### Supprimer de la liste (variable FM)

**Identifiant :** `remove_from_list`

Supprime des entrées d’une [variable de liste](/variables#list-actions). **Remove** permet de choisir lesquelles :

- **Entry at Index** : l’entrée à un index donné.
- **First Match** : la première entrée correspondant exactement à la **Value to Remove**.
- **All Matches** : toutes les entrées correspondantes.

**Ignore Case** considère `Apple` et `apple` comme identiques.

### Vider une liste (variable FM)

**Identifiant :** `clear_list`

Supprime toutes les entrées d’une [variable de liste](/variables#list-actions). La liste vide est conservée.

### Définir une liste (variable FM)

**Identifiant :** `set_list`

Remplace toutes les entrées d’une [variable de liste](/variables#list-actions). **Entries From** permet de choisir leur source :

- **Split Text** : découpe le **Text to Split** au niveau du **Separator**, par exemple `,`. Si le séparateur est vide, le texte est découpé aux retours à la ligne. **Trim Entries** supprime les espaces au début et à la fin des entrées ; **Skip Empty Entries** ignore les entrées vides.
- **JSON Array** : utilise les entrées d’un tableau comme `["Diamonds","Emeralds"]`, ou `$$other_list` pour copier une autre liste. Tout autre texte devient l’unique entrée de la liste ; un texte vide vide la liste.

La fenêtre affiche un aperçu des entrées.

### Réorganiser une liste (variable FM)

**Identifiant :** `arrange_list`

Modifie l’ordre d’une [variable de liste](/variables#list-actions). **Arrangement** :

- **Sort A–Z** et **Sort Z–A** : tri alphabétique.
- **Numbers, Smallest First** et **Numbers, Biggest First** : tri numérique. Les entrées qui ne sont pas des nombres sont placées à la fin.
- **Reverse Order** : la dernière entrée devient la première.
- **Shuffle** : ordre aléatoire.
- **Remove Duplicates** : ne conserve que la première occurrence de chaque valeur.

Dans toutes les actions de liste, la première entrée a l’index `0` et `-1` correspond à la dernière. Le nom de la liste peut contenir des espaces réservés ; s’il est précédé de `$$`, l’action utilise la valeur de cette variable comme nom de liste. Les variables de texte qui contiennent une valeur restent inchangées, et l’action inscrit un avertissement dans le journal du jeu.

## Web et réseau

### Ouvrir une URL dans le navigateur

**Identifiant :** `openlink`

Ouvre un lien dans le navigateur par défaut sans demander de confirmation.

**Valeur :** le lien, par exemple `https://discord.gg/example`

N’utilisez que des liens auxquels vous faites confiance.

### Envoyer une requête HTTP

**Identifiant :** `send_http_request`

Envoie une requête Web en arrière-plan. La réponse peut être inscrite dans le journal du jeu ou enregistrée dans une variable.

| Paramètre | Fonction |
|---|---|
| URL | L’adresse HTTP ou HTTPS. |
| Method | `GET`, `POST`, `PUT`, `DELETE`, `PATCH`, `HEAD` ou `OPTIONS`. |
| Body | Les données à envoyer. Non envoyé avec `GET` et `HEAD`. |
| Content type | Le type de contenu (`Content-Type`) du corps, par exemple `application/json`. |
| Timeout | Durée d’attente de la connexion et de la réponse, en secondes. |
| Log response | Inscrit la réponse dans le journal du jeu. |
| Response variable | Enregistre la réponse dans cette variable à sa réception. |
| Single-line response | Supprime les retours à la ligne de la réponse avant de l’enregistrer. |
| Authentication | Aucune, Basic, Bearer ou clé API. |
| Headers | En-têtes de requête supplémentaires. |

L’action suivante n’attend pas la réponse. Les réponses contenant des erreurs sont également inscrites dans le journal et enregistrées. Ne mettez pas de mots de passe ni de jetons d’accès dans l’action : toute personne ayant accès à la mise en page peut les lire.

### Envoyer des données FM au serveur

**Identifiant :** `send_fm_data_to_server`

Envoie des [données FM](/fm-data) au serveur, qui doit également utiliser FancyMenu.

**Valeur :** `data_identifier||data`

### Se connecter à un serveur distant

**Identifiant :** `connect_to_remote_server`

Se connecte à un serveur distant ou utilise la connexion déjà ouverte.

**Valeur :** l’adresse du serveur, par exemple `wss://example.com/ws`

Consultez [Communication avec un serveur distant](/remote-server-communication#url-modes) pour connaître les formats d’adresse compatibles.

### Envoyer des données à un serveur distant

**Identifiant :** `send_data_to_remote_server`

Envoie du texte à un serveur distant et s’y connecte d’abord si nécessaire.

**Valeur :** `server_address||data`

### Fermer une connexion à un serveur distant

**Identifiant :** `close_remote_server_connection`

Ferme une connexion à un serveur distant.

**Valeur :** son identifiant de requête, généralement `$$request_id` fourni par [**On Remote Server Connected**](/listeners#on-remote-server-connected)

### Fermer toutes les connexions aux serveurs distants

**Identifiant :** `close_all_remote_server_connections`

Ferme toutes les connexions aux serveurs distants ouvertes par FancyMenu.

**Valeur :** aucune

## Fichiers

### Créer un fichier dans le dossier du jeu

**Identifiant :** `create_file_in_game_dir`

Crée un fichier vide. Les dossiers manquants sont également créés. Un fichier existant reste inchangé.

**Valeur :** le chemin du fichier, par exemple `config/mymodpack/first_start.txt`

Toutes les actions sur les fichiers fonctionnent uniquement dans le dossier du jeu (dossier de l’instance). Les chemins commençant par `.minecraft/` utilisent le dossier `.minecraft` par défaut, qui peut être différent.

### Supprimer un fichier/dossier du dossier du jeu

**Identifiant :** `delete_file_in_game_dir`

Supprime un fichier ou un dossier avec tout son contenu.

**Valeur :** le chemin, par exemple `config/mymodpack/cache.txt`

Avec `*` à la fin, par exemple `config/downloads/*`, l’action supprime tous les fichiers directement contenus dans ce dossier, mais conserve le dossier lui-même et ses sous-dossiers.

### Copier un fichier/dossier dans le dossier du jeu

**Identifiant :** `copy_file_in_game_dir`

Copie un fichier ou un dossier avec tout son contenu.

**Valeur :** `source||destination`, par exemple `config/presets/default.json||config/mymod/settings.json`

- Si la source se termine par `*`, par exemple `config/presets/*||config/mymod/`, l’action copie tous les fichiers directement contenus dans le dossier, mais pas les sous-dossiers. La destination doit alors être un dossier, qui est créé si nécessaire.
- Aucun fichier n’est écrasé : si la destination existe déjà, l’action échoue.

### Déplacer un fichier/dossier dans le dossier du jeu

**Identifiant :** `move_file_in_game_dir`

Déplace un fichier ou un dossier avec tout son contenu.

**Valeur :** `source||destination`

Le `*` à la fin de la source fonctionne comme pour [**Copier un fichier/dossier dans le dossier du jeu**](#copier-un-fichierdossier-dans-le-dossier-du-jeu). Aucun fichier n’est écrasé.

### Renommer un fichier/dossier dans le dossier du jeu

**Identifiant :** `rename_file_in_game_dir`

Renomme un fichier ou un dossier. L’action échoue si un élément portant déjà le nouveau nom existe.

**Valeur :** `path||new_name`, par exemple `config/mymod/old_name.txt||new_name.txt`

### Télécharger un fichier dans le dossier du jeu

**Identifiant :** `download_file_to_game_dir`

Télécharge un fichier dans un dossier, en arrière-plan.

**Valeur :** `url||target_folder`, par exemple `https://example.com/pack.zip||downloads`

- La deuxième partie est un dossier, et non un nom de fichier. FancyMenu récupère le nom depuis le téléchargement ou le lien.
- Un fichier portant le même nom est écrasé.
- [**On File Downloaded via Action**](/listeners#on-file-downloaded-via-action) s’exécute lorsque le téléchargement est terminé ou a échoué. En cas de réussite, `$$target_file_path` indique le chemin du fichier enregistré.

### Extraire un fichier ZIP dans le dossier du jeu

**Identifiant :** `extract_zip_file_in_game_dir`

Extrait un fichier ZIP dans un dossier, en arrière-plan.

**Valeur :** `zip_path||target_folder`, par exemple `downloads/pack.zip||resourcepacks/MyPack`

Les fichiers portant le même nom sont remplacés et aucun dossier supplémentaire portant le nom du ZIP n’est créé. [**On ZIP Extracted via Action**](/listeners#on-zip-extracted-via-action) s’exécute une fois l’opération terminée. N’extrayez que des fichiers ZIP auxquels vous faites confiance.

### Ouvrir un fichier/dossier du dossier du jeu

**Identifiant :** `open_file_folder_in_game_dir`

Ouvre un fichier ou un dossier avec le programme associé par le système.

**Valeur :** le chemin, par exemple `screenshots`

### Écrire dans un fichier du dossier du jeu

**Identifiant :** `write_file_in_game_dir`

Écrit du texte dans un fichier. Le fichier et ses dossiers sont créés si nécessaire.

**Valeur :** `path|||text|||append`, par exemple `config/mymodpack/log.txt|||Joined the server\n|||true`

`\n` insère un retour à la ligne. Si `append` est défini sur `true`, le texte est ajouté à la fin du fichier ; si sa valeur est `false`, le contenu existant est remplacé.

### Sélectionner un fichier sur le système

**Identifiant :** `select_file_to_game_dir`

Ouvre le sélecteur de fichiers du système et copie le fichier choisi dans le dossier du jeu.

**Valeur :** `target_path|||filter_name|||extensions|||overwrite`, par exemple `config/fancymenu/assets/background.png|||Images|||png;jpg|||true`

- `target_path` correspond au chemin complet de la copie, nom de fichier compris.
- Séparez les extensions avec `;` ou `,`. Sans extension indiquée, tous les fichiers peuvent être sélectionnés.
- Si `overwrite` est défini sur `false`, l’action échoue si le fichier existe déjà.

[**On File Selected**](/listeners#on-file-selected) s’exécute lorsque le fichier a été copié, que le sélecteur a été fermé sans sélection ou qu’une erreur s’est produite.

## Jeu et FancyMenu

### Quitter Minecraft

**Identifiant :** `quitgame`

Ferme le jeu.

**Valeur :** aucune

### Définir une option Minecraft

**Identifiant :** `edit_minecraft_option`

Modifie une option Minecraft, comme la distance de rendu ou l’échelle de l’interface.

**Valeur :** `option_name:value`, par exemple `renderDistance:12`

Consultez [Options Minecraft](/minecraft-options) pour connaître les noms des options.

### Imiter une touche

**Identifiant :** `mimic_keybind`

Appuie sur une touche associée à une action Minecraft, comme sauter ou s’accroupir, et peut la maintenir enfoncée.

**Valeur :** `keybind|||hold|||duration_ms`, par exemple `key.jump|||false|||1000`

| Partie | Description |
|---|---|
| `keybind` | L’identifiant de la touche associée, par exemple `key.jump` ou `key.sneak`. |
| `hold` | `true` maintient la touche enfoncée ; `false` appuie une fois dessus. |
| `duration_ms` | Durée pendant laquelle la touche est maintenue, en millisecondes. Valeur par défaut : `1000`. |

### Gérer un pack de ressources

**Identifiant :** `manage_resource_pack`

Active ou désactive un pack de ressources. Configurez l’action dans sa fenêtre :

- **Target Resource Pack** : le nom du pack tel qu’il apparaît dans l’écran des packs de ressources. Les majuscules et les minuscules ne comptent pas.
- **Action Mode** : **Enable**, **Disable** ou **Toggle**.
- **Reload Resources** : recharge les packs de ressources immédiatement après la modification. Désactivez cette option pour les recharger plus tard, par exemple avec [**Reload Resource Packs**](#recharger-les-packs-de-ressources).

Les packs nécessaires au jeu ne peuvent pas être désactivés.

### Recharger les packs de ressources

**Identifiant :** `reload_resource_packs`

Recharge les packs de ressources, comme avec `F3 + T`. Pendant les cinq secondes suivant un rechargement, l’action ne fait rien afin d’éviter de relancer l’opération en boucle.

**Valeur :** aucune

### Recharger FancyMenu

**Identifiant :** `reloadmenu`

Recharge les mises en page, les [interfaces personnalisées](/custom-guis), les [panoramas](/panoramas), les [diaporamas](/slideshows), les paramètres et les fichiers de FancyMenu. Les packs de ressources ne sont pas rechargés.

**Valeur :** aucune

> [!WARNING]
> Le rechargement prend un moment. Utilisez cette action sur un bouton, jamais dans un [Ticker](/elements#ticker) ni dans un [écouteur](/listeners) qui s’exécute fréquemment.

### Démarrer un planificateur

**Identifiant :** `start_scheduler`

Démarre un [planificateur](/schedulers).

**Valeur :** l’identifiant du planificateur

### Arrêter un planificateur

**Identifiant :** `stop_scheduler`

Arrête un [planificateur](/schedulers).

**Valeur :** l’identifiant du planificateur

### Copier du texte dans le presse-papiers

**Identifiant :** `copytoclipboard`

Copie du texte dans le presse-papiers.

**Valeur :** le texte, par exemple `play.example.net`

### Écrire dans le journal du jeu

**Identifiant :** `print_to_log`

Écrit une ligne dans le journal du jeu. Pratique pour comprendre ce que fait un script.

**Valeur :** le texte
