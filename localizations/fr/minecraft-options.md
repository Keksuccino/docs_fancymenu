---
title: Définir/Lire les options Minecraft
description: >-
  Comment définir et lire des options Minecraft comme le volume, le FOV, la
  distance de rendu, etc.
---

# Travailler avec les options Minecraft dans FancyMenu

FancyMenu vous permet de lire et de définir les paramètres du jeu Minecraft (options) à l’aide de différents éléments d’interface. Ce guide vous montrera comment utiliser des boutons, des curseurs et des tickers pour travailler avec les options Minecraft dans vos mises en page de menu personnalisées.

# Comprendre les options Minecraft

Minecraft possède de nombreuses options intégrées qui contrôlent tout, des paramètres graphiques au volume sonore. FancyMenu vous permet d’y accéder par leur nom.

Voici quelques noms d’options courants :
- `soundCategory_master` - Volume principal
- `soundCategory_music` - Volume de la musique
- `soundCategory_ambient` - Volume des sons ambiants
- `soundCategory_players` - Volume des sons des joueurs
- `soundCategory_blocks` - Volume des sons des blocs
- `fov` - Champ de vision
- `gamma` - Luminosité
- `renderDistance` - Distance de rendu

# Afficher les valeurs des options

Vous pouvez afficher la valeur actuelle de n’importe quelle option Minecraft à l’aide d’un placeholder spécial.

Le placeholder ressemble à ceci :
```
{"placeholder":"minecraft_option_value","values":{"name":"option_name"}}
```

Remplacez `option_name` par le vrai nom de l’option que vous souhaitez afficher.

# Définir des options avec des boutons

Les boutons peuvent être utilisés pour définir des valeurs spécifiques pour les options Minecraft.

## Comment configurer un bouton :

1. Créez un nouvel élément Button
2. Définissez le texte du bouton (ce qui apparaît sur le bouton)
3. Ajoutez une action : clic droit sur le bouton → Edit Action Script → Add Action → Set Minecraft Option Value
4. Dans la fenêtre "Set Minecraft Option Value" :
   - Name : saisissez le nom de l’option (par exemple `renderDistance`)
   - Value : saisissez la valeur à définir (par exemple `16`)

## Exemple : 

Créer un bouton qui règle la distance de rendu sur 16 chunks :
- Option Name : `renderDistance`
- Value : `16`
- Label : "Définir la distance de rendu à 16 chunks"

# Définir des options avec des curseurs

Les curseurs sont parfaits pour les options avec une plage de valeurs, comme les réglages de volume ou la luminosité.

## Comment configurer un curseur :

1. Créez un nouvel élément Slider
2. Définissez le type de curseur :
   - Pour les nombres entiers (comme la distance de rendu) : choisissez "Integer Range"
   - Pour les nombres décimaux (comme le volume) : choisissez "Decimal Range"
3. Définissez les valeurs minimale et maximale
4. Ajoutez une action pour définir l’option Minecraft :
   - Clic droit → Edit Action Script → Add Action → Set Minecraft Option Value
   - Name : le nom de l’option
   - Value : `$$value` (cette variable spéciale contient la valeur actuelle du curseur)
5. Définissez la valeur présélectionnée sur la valeur actuelle de l’option :
   - Réglez "Pre-Selected Value" sur `{"placeholder":"minecraft_option_value","values":{"name":"option_name"}}`

## Exemples de formats de libellé pour un curseur :

Pour afficher la valeur actuelle de l’option dans le libellé du curseur, utilisez :
```
Volume: {"placeholder":"minecraft_option_value","values":{"name":"soundCategory_master"}}
```

Pour afficher un pourcentage (utile pour le volume) :
```
Volume: {"placeholder":"calc","values":{"expression":"$$value * 100.0","decimal":"false"}}%
```

# Définir des options avec des tickers

Les tickers sont des éléments invisibles qui peuvent changer automatiquement des options selon un planning.

## Comment configurer un ticker :

1. Créez un nouvel élément Ticker
2. Configurez les paramètres de tick :
   - Tick Mode : choisissez quand l’option doit être mise à jour
   - Tick Delay : définissez la fréquence de mise à jour (en millisecondes)
3. Ajoutez l’action pour définir une option Minecraft :
   - Clic droit → Edit Action Script → Add Action → Set Minecraft Option Value
   - Définissez le nom et la valeur de l’option

## Exemple :

Définir gamma (luminosité) au maximum au chargement du menu :
- Tick Mode : On Load Screen
- Name : `gamma`
- Value : `1.0`

# Cas d’utilisation courants

Voici quelques cas courants de ce que vous pouvez faire en utilisant FancyMenu pour définir et lire les options Minecraft.

## Créer des curseurs de volume personnalisés

Les curseurs de volume sont une utilisation courante de l’intégration des options Minecraft. Voici comment créer un curseur personnalisé pour le volume de la musique :

1. Créez un nouvel élément Slider
2. Définissez "Slider Type" sur "Decimal Range"
3. Définissez "Minimum Range Value" sur "0.0"
4. Définissez "Maximum Range Value" sur "1.0"
5. Edit Action Script → Add Action → Set Minecraft Option Value
   - Définissez Name sur `soundCategory_music`
   - Définissez Value sur `$$value`
6. Définissez "Pre-Selected Value" sur `{"placeholder":"minecraft_option_value","values":{"name":"soundCategory_music"}}`
7. Pour afficher le volume en pourcentage, définissez le libellé sur : 
   ```
   Music: {"placeholder":"calc","values":{"expression":"$$value * 100.0","decimal":"false"}}%
   ```

Vous pouvez créer des curseurs similaires pour les autres catégories sonores :
- Volume principal : `soundCategory_master`
- Musique : `soundCategory_music`
- Ambiant : `soundCategory_ambient`
- Blocs : `soundCategory_blocks`
- Joueurs : `soundCategory_players`
- Météo : `soundCategory_weather`

## Créer un curseur FOV personnalisé

Le champ de vision (FOV) est un réglage graphique important qui détermine l’ampleur de votre vue dans le jeu. L’option FOV utilise en interne des valeurs de -1.0 à 1.0, mais s’affiche de 30 à 110 dans l’interface.

### Comprendre le mappage de la valeur FOV
- Plage de valeurs internes : -1.0 à 1.0
- Plage de valeurs affichées : 30 à 110
- Formule de mappage : `(internal_value + 1) * 40 + 30`

### Étape 1 : Créer un élément Ticker pour mettre à jour le texte FOV

D’abord, nous avons besoin d’un ticker qui vérifiera la valeur actuelle du FOV et définira une variable avec la description appropriée :

1. Créez un nouvel élément Ticker
2. Réglez "Tick Mode" sur "Normal" (pour qu’il se mette à jour en continu)
3. Réglez "Tick Delay" sur environ "10" (millisecondes) afin d’éviter des vérifications excessives

Maintenant, nous devons configurer les actions pour les libellés FOV. Voici à quoi devrait ressembler la structure de votre script d’action :

```
▶ Action Script
│
├─▶ IF (mapped FOV = 70)
│  └─■ Set Variable Value: fov_text:Normal
│
├─▶ ELSE-IF (mapped FOV = 110)
│  └─■ Set Variable Value: fov_text:Quake Pro
│
└─▶ ELSE
   └─■ Set Variable Value: fov_text:[calculated numeric value]
```

Configurons chaque partie :

#### Configurer le libellé FOV "Normal" :
1. Clic droit → Edit Action Script → Add Action
2. Cliquez sur "IF Statement" pour ajouter un bloc conditionnel
3. Définissez la condition sur "Is Number" avec :
   - Compare Mode : "equals"
   - Number : `{"placeholder":"calc","values":{"decimal":"false","expression":"({"placeholder":"minecraft_option_value","values":{"name":"fov"}} + 1) * 40 + 30"}}`
   - Compare With : "70"
4. À l’intérieur de ce bloc IF, ajoutez l’action "Set Variable Value (FM Variable)" avec :
   - Value : `fov_text:Normal`

#### Configurer le libellé FOV "Quake Pro" :
1. Dans le script d’action, ajoutez "ELSE-IF Statement"
2. Définissez la condition sur "Is Number" avec :
   - Compare Mode : "equals"
   - Number : `{"placeholder":"calc","values":{"decimal":"false","expression":"({"placeholder":"minecraft_option_value","values":{"name":"fov"}} + 1) * 40 + 30"}}`
   - Compare With : "110"
3. À l’intérieur de ce bloc ELSE-IF, ajoutez l’action "Set Variable Value (FM Variable)" avec :
   - Value : `fov_text:Quake Pro`

#### Configurer le libellé FOV numérique :
1. Ajoutez un bloc "ELSE Statement"
2. À l’intérieur de ce bloc ELSE, ajoutez l’action "Set Variable Value (FM Variable)" avec :
   - Value : `fov_text:{"placeholder":"calc","values":{"decimal":"false","expression":"({"placeholder":"minecraft_option_value","values":{"name":"fov"}} + 1) * 40 + 30"}}`

<img src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/fov_slider_action_script.png" alt="Script d’action du curseur FOV" style="max-width: 600px; height: auto;">

### Étape 2 : Créer le curseur FOV

1. Créez un nouvel élément Slider
2. Définissez "Slider Type" sur "Decimal Range"
3. Définissez "Minimum Range Value" sur "-1.0"
4. Définissez "Maximum Range Value" sur "1.0"
5. Edit Action Script → Add Action → Set Minecraft Option Value
   - Définissez Name sur `fov`
   - Définissez Value sur `$$value`
6. Définissez "Pre-Selected Value" sur `{"placeholder":"minecraft_option_value","values":{"name":"fov"}}`

### Étape 3 : Définir le libellé du curseur

Définissez le libellé du curseur pour afficher simplement la variable de texte du FOV :

```
FOV: {"placeholder":"getvariable","values":{"name":"fov_text"}}
```

Ce libellé affichera :
- "FOV: Normal" lorsque la valeur est 70
- "FOV: Quake Pro" lorsque la valeur est 110  
- "FOV: 85" (ou tout autre nombre) pour toutes les autres valeurs

### Conseils pour les curseurs FOV

- La plage de valeurs internes du curseur est de -1.0 à 1.0, et doit être convertie en 30 à 110 pour l’affichage
- La formule de conversion est : `(internal_value + 1) * 40 + 30`
- Seules deux valeurs ont des libellés spéciaux : 70 (Normal) et 110 (Quake Pro)
- Le FOV par défaut dans Minecraft est 70 (ce qui correspond à la valeur interne 0.0)
- La variable `fov_text` contient automatiquement soit le libellé spécial, soit la valeur numérique

## Afficher les valeurs des options dans des éléments Text

Vous pouvez également afficher les valeurs actuelles des options dans des éléments Text :

1. Créez un élément Text
2. Pour le contenu du texte, utilisez le placeholder : `{"placeholder":"minecraft_option_value","values":{"name":"option_name"}}`

Par exemple, pour afficher la distance de rendu actuelle :
```
Distance de rendu actuelle : {"placeholder":"minecraft_option_value","values":{"name":"renderDistance"}} chunks
```

# Trouver les noms des options

Vous pouvez trouver les noms de toutes les options disponibles en :

  1. Créant un bouton
  2. En faisant un clic droit dessus
  3. En cliquant sur "Edit Action Script"
  4. En ajoutant l’action "Set Minecraft Option Value"
  5. Lors de l’édition de la valeur de l’action, regardez les suggestions du menu déroulant lorsque vous commencez à taper dans le champ "Name"
  
# Conseils importants

- **Valeurs valides** : toutes les options n’acceptent pas toutes les valeurs. Par exemple :
  - Les options de volume acceptent des valeurs de 0.0 à 1.0
  - La distance de rendu accepte généralement des nombres entiers de 2 à 32
  - Les options booléennes (true/false) comme `pauseOnLostFocus` acceptent "true" ou "false"

- **Tests** : testez toujours vos réglages pour vous assurer qu’ils fonctionnent comme prévu !

- **Retour visuel** : donnez aux utilisateurs un retour visuel sur la valeur actuelle à l’aide des placeholders décrits ci-dessus.
