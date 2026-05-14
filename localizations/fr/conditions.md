---
title: Conditions (Exigences)
description: Comment utiliser les exigences de chargement.
---

# Exigences
Les exigences (aussi appelées « exigences de chargement ») vous permettent de rendre certaines parties de vos mises en page visibles ou invisibles selon विभिन्न conditions, par exemple si un élément est survolé, si la fenêtre a une taille spécifique ou si vous êtes actuellement dans un monde.

Elles peuvent aussi être utilisées dans les scripts d’action des boutons, des curseurs, des compteurs et de tout autre élément disposant d’une entrée de script d’action.

# Ajouter des exigences aux éléments
Pour ajouter une ou plusieurs exigences à des éléments, faites simplement un clic droit sur l’élément, puis cliquez sur **Loading Requirements**.

# Exigences à l’échelle de la mise en page
Vous pouvez aussi modifier la visibilité de mises en page entières en faisant un clic droit sur **l’arrière-plan de l’éditeur**, puis en cliquant sur **Loading Requirements [Layout-Wide]**.

# Scripts d’action
Les exigences peuvent également être utilisées dans les scripts d’action.
Vous pouvez les ajouter dans l’écran de l’éditeur de scripts d’action et les utiliser pour exécuter certaines actions uniquement si la condition de l’exigence est remplie.

# Valeurs des exigences
Certaines exigences nécessitent que vous définissiez des valeurs pour fonctionner correctement. Dans ce cas, l’écran des exigences devrait vous indiquer de renseigner toutes les valeurs d’abord, mais sinon, vérifiez simplement si le bouton **Edit Requirement Value** est cliquable lors de l’ajout de l’exigence.
Consultez toujours la description de l’exigence si vous n’êtes pas sûr de la valeur à définir.
Certaines zones de saisie prennent même en charge l’**auto-complétion avec TAB**.

FancyMenu 3.9.0 remanie la fenêtre Manage Requirements pour utiliser un menu contextuel au clic droit, la navigation au clavier, la recherche, annuler/rétablir (`CTRL + Z` / `CTRL + Y`) et `CTRL + S` comme raccourci **Done**.

# Exigences en détail
La liste suivante contient la plupart, sinon la totalité, des exigences disponibles dans FancyMenu. Il est possible que cette liste soit parfois légèrement obsolète en raison des mises à jour du mod.

## Is Element Hovered
Vérifie si un élément spécifique est survolé par le curseur de la souris.  
**Valeur requise** : Oui - ID de l’élément cible (par ex. `some_element_ID`). Vous pouvez obtenir l’ID en faisant un clic droit sur un élément dans l’éditeur.

## Is Element Focused
Vérifie si un élément spécifique a actuellement le focus clavier (par exemple, un champ de texte ou un bouton focalisé).
**Valeur requise** : Oui - ID de l’élément cible (le même ID affiché dans l’éditeur)

> Ce n’est pas la même chose qu’un simple survol d’élément, même si cela y ressemble. Les éléments focalisés continuent d’apparaître « survolés » même lorsqu’ils ne le sont plus. Les éléments prennent le focus lorsqu’on clique dessus ou lorsqu’on utilise le clavier pour naviguer dans les menus.
{.is-info}

## Is Any Element Hovered
Vérifie si un élément quelconque de la mise en page est actuellement survolé par le curseur de la souris.  
**Valeur requise** : Non

## Is Any Button Hovered
Vérifie si un bouton quelconque (vanilla ou personnalisé) est actuellement survolé par le curseur de la souris.  
**Valeur requise** : Non

## Is Layout Enabled
Vérifie si une mise en page spécifique est actuellement activée.  
**Valeur requise** : Oui - Nom de la mise en page (par ex. `my_cool_main_menu_layout`)

## Is Scheduler Running
Vérifie si un ordonnanceur est actuellement en cours d’exécution.
**Valeur requise** : Oui - ID de l’ordonnanceur (par ex. `my_scheduler`)

## Is GUI Scale
Vérifie si l’échelle actuelle de l’interface graphique correspond à certaines conditions.  
**Valeur requise** : Oui - Peut accepter des valeurs numériques comme `1`, `2`, etc.

## Is Button Active
Vérifie si un bouton spécifique est actif (cliquable).  
**Valeur requise** : Oui - ID de l’élément du bouton cible (par ex. "some_element_ID")

## Is Screen Title
Vérifie si le titre AFFICHÉ de l’écran correspond à un texte spécifique ou à une clé de localisation. Cela vérifie uniquement le nom/titre affiché de l’écran, comme « Options » ou « Pause ». Cela ne vérifie PAS l’identifiant du menu/écran (comme `title_screen`) !

**Valeur requise** : Oui - Le texte exact du titre ou la clé de localisation de l’écran

## Is Key Pressed
Vérifie si une touche clavier spécifique est actuellement enfoncée.  
**Valeur requise** : Oui - Le code de la touche cible. Sélectionné via une interface lors de la modification de la valeur de l’exigence.

## Is Any Screen Open
Vérifie si un écran/menu est actuellement ouvert (renvoie false si aucun écran n’est affiché).  
**Valeur requise** : Non

## Is MC Debug Overlay Enabled
Vérifie si la superposition de débogage F3 est actuellement visible.
**Valeur requise** : Non

## Is Active Cursor Type
Vérifie si le type de curseur actuellement actif de FancyMenu correspond à un type de curseur standard spécifique.
**Valeur requise** : Oui - Type de curseur : `normal`, `writing`, `crosshair`, `pointing_hand`, `resize_horizontal`, `resize_vertical`, `resize_nwse`, `resize_nesw`, `resize_all` ou `not_allowed`

## Is Customization Menu Bar Visible
Vérifie si la barre de menu de personnalisation de FancyMenu est actuellement visible.
**Valeur requise** : Non

## Is Modpack Mode Enabled
Vérifie si le mode Modpack de FancyMenu est activé.
**Valeur requise** : Non

## Mouse Clicked
Vérifie si un bouton de la souris spécifique est enfoncé.  
**Valeur requise** : Oui - `left` ou `right` pour indiquer quel bouton de la souris vérifier

## Is Fullscreen
Vérifie si le jeu est actuellement en mode plein écran.  
**Valeur requise** : Non

## Is Window Width
Vérifie si la largeur de la fenêtre du jeu correspond à des valeurs spécifiques.  
**Valeur requise** : Oui - Largeur de la fenêtre en pixels (par ex. "1920"). Plusieurs valeurs peuvent être fournies en les séparant par des virgules.

## Is Window Height
Vérifie si la hauteur de la fenêtre du jeu correspond à des valeurs spécifiques.  
**Valeur requise** : Oui - Hauteur de la fenêtre en pixels (par ex. "1080"). Plusieurs valeurs peuvent être fournies en les séparant par des virgules.

## Is Window Width Bigger Than
Vérifie si la largeur de la fenêtre du jeu est supérieure à une valeur spécifique.  
**Valeur requise** : Oui - Largeur de la fenêtre en pixels (par ex. "1920")

## Is Window Height Bigger Than
Vérifie si la hauteur de la fenêtre du jeu est supérieure à une valeur spécifique.  
**Valeur requise** : Oui - Hauteur de la fenêtre en pixels (par ex. "1080")

## Is Multiplayer
Vérifie si le joueur se trouve actuellement dans un monde multijoueur.  
**Valeur requise** : Non

## Is Singleplayer
Vérifie si le joueur se trouve actuellement dans un monde solo.  
**Valeur requise** : Non

## Is World Loaded
Vérifie si un monde est actuellement chargé.  
**Valeur requise** : Non

## Is Adventure
Vérifie si le joueur est actuellement en mode aventure.  
**Valeur requise** : Non

## Is Creative
Vérifie si le joueur est actuellement en mode créatif.  
**Valeur requise** : Non

## Is Spectator
Vérifie si le joueur est actuellement en mode spectateur.  
**Valeur requise** : Non

## Is Survival
Vérifie si le joueur est actuellement en mode survie.  
**Valeur requise** : Non

## Is Game Mode
Vérifie si le joueur est dans un mode de jeu spécifique.  
**Valeur requise** : Oui - Nom du mode de jeu (par ex. "creative", "survival", "adventure", "spectator")

## Is Difficulty
Vérifie si la difficulté actuelle du jeu correspond à une valeur spécifique.  
**Valeur requise** : Oui - Nom de la difficulté (par ex. "peaceful", "easy", "normal", "hard")

## Is Hardcore
Vérifie si le monde actuellement chargé est en mode hardcore.
**Valeur requise** : Non

## Is Camera Perspective
Vérifie si la perspective actuelle de la caméra correspond à une perspective spécifique.
**Valeur requise** : Oui - `first_person`, `third_person_back` ou `third_person_front`

## Is Raining
Vérifie s’il pleut actuellement à l’endroit où se trouve le joueur.  
**Valeur requise** : Non

## Is Thundering
Vérifie s’il y a actuellement un orage dans le monde du joueur.  
**Valeur requise** : Non

## Is Clear Weather
Vérifie si le temps est actuellement dégagé (ni pluie ni orage).  
**Valeur requise** : Non

## Is Snowing
Vérifie s’il neige actuellement à l’endroit où se trouve le joueur.  
**Valeur requise** : Non

## Is Player Running
Vérifie si le joueur sprinte actuellement.  
**Valeur requise** : Non

## Is Player Sneaking
Vérifie si le joueur est actuellement en train de se faufiler / s’accroupir.  
**Valeur requise** : Non

## Is Player Using Item
Vérifie si le joueur utilise actuellement un objet.
**Valeur requise** : Non

## Is Player Swimming
Vérifie si le joueur nage actuellement.  
**Valeur requise** : Non

## Is Player Jumping or Falling
Vérifie si le joueur est actuellement en train de sauter.  
**Valeur requise** : Non

## Is Player Under Water
Vérifie si le joueur est complètement sous l’eau.  
**Valeur requise** : Non

## Is Player In Water
Vérifie si le joueur est dans l’eau (peut être partiellement submergé).  
**Valeur requise** : Non

## Is Player In Lava
Vérifie si le joueur est dans la lave.  
**Valeur requise** : Non

## Is Player In Fluid
Vérifie si le joueur se trouve dans n’importe quel fluide (eau, lave, etc.).  
**Valeur requise** : Non

## Is Player Riding Entity/Vehicle
Vérifie si le joueur monte une entité quelconque.  
**Valeur requise** : Non

## Is Player Riding Jumpable Entity
Vérifie si le joueur monte une entité capable de sauter (comme un cheval).  
**Valeur requise** : Non

## Is Player Riding Entity With Health
Vérifie si le joueur monte une entité vivante avec des points de vie (comme des animaux, pas des bateaux).  
**Valeur requise** : Non

## Is Player In Powder Snow
Vérifie si le joueur se trouve actuellement dans de la neige poudreuse.  
**Valeur requise** : Non

## Was Player In Powder Snow
Vérifie si le joueur a été dans de la neige poudreuse (utilisé pour des effets qui persistent après en être sorti).  
**Valeur requise** : Non

## Is Player Wearing Pumpkin
Vérifie si le joueur porte une citrouille sculptée sur la tête.  
**Valeur requise** : Non

## Is Player Flying With Elytra
Vérifie si le joueur vole actuellement avec une elytre.  
**Valeur requise** : Non

## Is Player Creative Flying
Vérifie si le joueur vole en mode créatif.  
**Valeur requise** : Non

## Has Player Absorption Hearts
Vérifie si le joueur possède des cœurs d’absorption (cœurs dorés).  
**Valeur requise** : Non

## Is Player Withered
Vérifie si le joueur est प्रभावित par l’effet Wither.  
**Valeur requise** : Non

## Is Player Fully Frozen
Vérifie si le joueur est complètement gelé (généralement à cause de la neige poudreuse).  
**Valeur requise** : Non

## Is Player Poisoned
Vérifie si le joueur est affecté par l’effet Poison.  
**Valeur requise** : Non

## Is Player In Biome
Vérifie si le joueur se trouve dans un biome spécifique.  
**Valeur requise** : Oui - Identifiant du biome (par ex. `minecraft:birch_forest`)

## Is Player In Dimension
Vérifie si le joueur se trouve dans une dimension spécifique.  
**Valeur requise** : Oui - Identifiant de la dimension (par ex. `minecraft:overworld`, `minecraft:the_nether`, `minecraft:the_end`)

## Is Player In Structure
Vérifie si le joueur se trouve actuellement à l’intérieur d’une structure spécifique. Nécessite FancyMenu sur le serveur pour les mondes serveur.
**Valeur requise** : Oui - Identifiant de la structure (par ex. `minecraft:village`)

## Is Entity Nearby
Vérifie si un type d’entité spécifique se trouve dans un certain rayon autour du joueur.  
**Valeur requise** : Oui - Format : "radius:entity_id" (par ex. `10:minecraft:pig` - vérifie la présence de cochons dans un rayon de 10 blocs)

## Is Effect Active
Vérifie si un effet de potion spécifique est actif sur le joueur.  
**Valeur requise** : Oui - Identifiant de l’effet (par ex. `minecraft:speed`, `minecraft:strength`)

## Is Any Effect Active
Vérifie si le joueur a au moins un effet de potion actif.  
**Valeur requise** : Non

## Is Player Left-Handed
Vérifie si le joueur est réglé en mode gaucher dans les options du jeu.  
**Valeur requise** : Non

## Is Inventory Slot Filled
Vérifie si un slot d’inventaire spécifique contient un objet.  
**Valeur requise** : Oui - Numéro du slot (0-35 pour l’inventaire principal, les slots 0-8 correspondent à la barre rapide)

## Is Item Hovered in Inventory
Vérifie si le curseur survole un objet quelconque dans un écran d’inventaire.
**Valeur requise** : Non

## Is Cursor Holding Inventory Item
Vérifie si le curseur tient actuellement une pile d’objets d’inventaire.
**Valeur requise** : Non

## Is Hotbar Slot Selected
Vérifie si un slot spécifique de la barre rapide est actuellement sélectionné.  
**Valeur requise** : Oui - Numéro du slot de la barre rapide (0-8)

## Has Player Permission Level
Vérifie si le joueur possède au moins le niveau de permission / OP spécifié sur le monde ou serveur actuel.  
**Valeur requise** : Oui - Numéro du niveau de permission (0-4, où 4 est l’opérateur du serveur)

## Is Attack Strength Weakened
Vérifie si la force d’attaque du joueur est actuellement réduite (non complètement chargée).  
**Valeur requise** : Non

## Is Real Time Day
Vérifie si le jour réel actuel du mois correspond à une valeur spécifique.  
**Valeur requise** : Oui - Numéro du jour (1-31). Plusieurs valeurs peuvent être fournies en les séparant par des virgules.

## Is Real Time Hour
Vérifie si l’heure réelle actuelle correspond à une valeur spécifique.  
**Valeur requise** : Oui - Heure au format 24 heures (0-23). Plusieurs valeurs peuvent être fournies en les séparant par des virgules.

## Is Real Time Minute
Vérifie si la minute réelle actuelle correspond à une valeur spécifique.  
**Valeur requise** : Oui - Minute (0-59). Plusieurs valeurs peuvent être fournies en les séparant par des virgules.

## Is Real Time Month
Vérifie si le mois réel actuel correspond à une valeur spécifique.  
**Valeur requise** : Oui - Numéro du mois (1-12, où 1 est janvier). Plusieurs valeurs peuvent être fournies en les séparant par des virgules.

## Is Real Time Second
Vérifie si la seconde réelle actuelle correspond à une valeur spécifique.  
**Valeur requise** : Oui - Seconde (0-59). Plusieurs valeurs peuvent être fournies en les séparant par des virgules.

## Is Real Time Week Day
Vérifie si le jour de la semaine réel actuel correspond à une valeur spécifique.  
**Valeur requise** : Oui - Jour de la semaine sous forme de numéro (1-7, où 1 est dimanche). Plusieurs valeurs peuvent être fournies en les séparant par des virgules.

## Is Real Time Year
Vérifie si l’année réelle actuelle correspond à une valeur spécifique.  
**Valeur requise** : Oui - Année complète (par ex. "2023"). Plusieurs valeurs peuvent être fournies en les séparant par des virgules.

## File/Folder Exists
Vérifie si un fichier ou un dossier spécifique existe sur le système.  
**Valeur requise** : Oui - Chemin vers le fichier ou le dossier (absolu ou relatif au répertoire du jeu)

## Is OS Linux
Vérifie si le système d’exploitation est Linux.  
**Valeur requise** : Non

## Is OS macOS
Vérifie si le système d’exploitation est macOS.  
**Valeur requise** : Non

## Is OS Windows
Vérifie si le système d’exploitation est Windows.  
**Valeur requise** : Non

## Is Internet Connection Available
Vérifie si une connexion Internet active est disponible.  
**Valeur requise** : Non

## Is Game Language
Vérifie si la langue actuelle du jeu correspond à une valeur spécifique.  
**Valeur requise** : Oui - Code de langue (par ex. `en_us` pour l’anglais)

## Is Mod Loaded
Vérifie si un mod spécifique est chargé.  
**Valeur requise** : Oui - ID du mod (par ex. `fancymenu`, `jei`). Vous pouvez aussi vérifier Optifine avec `optifine`. Plusieurs IDs de mods peuvent être fournis en les séparant par des virgules.

## Is MCEF Loaded
Vérifie si MCEF (Minecraft Chromium Embedded Framework) est installé et initialisé.  
**Valeur requise** : Non

## Is Number
Fournit une comparaison numérique avancée avec différents modes de comparaison.  
**Valeur requise** : Oui - Format complexe : `["mode":"comparison_mode","number":"value1","compare_with":"value2"]$` où `comparison_mode` peut être `equals`, `bigger-than`, `smaller-than`, `bigger-than-or-equals` ou `smaller-than-or-equals`

## Is Text
Fournit une comparaison textuelle avancée avec différents modes de comparaison.  
**Valeur requise** : Oui - Format complexe : `["mode":"comparison_mode","text":"text1","compare_with":"text2"]$` où `comparison_mode` peut être `equals`, `contains`, `starts-with` ou `ends-with`

## Is Server IP
Vérifie si l’adresse IP du serveur actuel correspond à une valeur spécifique.  
**Valeur requise** : Oui - Adresse IP du serveur (avec ou sans port)

## Is Server Online
Vérifie si un serveur spécifique est en ligne et joignable.  
**Valeur requise** : Oui - Adresse IP du serveur (avec ou sans port)

## Is Resource Pack Enabled
Vérifie si un pack de ressources spécifique est actuellement sélectionné/actif.  
**Valeur requise** : Oui - Titre du pack de ressources ou ID du pack (par ex. `Programmer Art` ou l’ID du pack)

## Is Variable Value (FM Variable)
Vérifie si une variable FancyMenu a une valeur spécifique.  
**Valeur requise** : Oui - Format : "variable_name:expected_value"

## Only Once Per Session
Renvoie true une seule fois par session de jeu. Utile pour des annonces ou actions à usage unique.  
**Valeur requise** : Non
