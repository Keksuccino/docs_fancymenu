---
title: API JavaScript du navigateur
description: >-
  Comment utiliser l'API JavaScript de FancyMenu dans des fonctionnalités de mod
  basées sur MCEF, comme l'élément Navigateur.
---

# API JavaScript de FancyMenu

FancyMenu injecte un pont JavaScript dans chaque fonctionnalité basée sur MCEF (par exemple l'élément **Navigateur**). Ce pont permet au contenu web de :

- exécuter directement depuis JavaScript n'importe quelle [action](./action-scripts) FancyMenu,
- lire de manière asynchrone n'importe quel [placeholder](/placeholders) FancyMenu.

Deux variables globales exposent l'API :
- `window.fancymenu` – espace de noms principal
- `window.FancyMenu` – alias (reproduit exactement la structure de `fancymenu`)

Utilisez l'événement `fancymenu-ready`, ou la détection de fonctionnalité, pour vous assurer que le pont est disponible avant de l'appeler.

## 1. Espaces de noms et structure

- `fancymenu.actions` – exécute des actions FancyMenu depuis le navigateur.
- `fancymenu.placeholders` – lit de manière asynchrone les valeurs des placeholders FancyMenu.
- `FancyMenu` reflète `fancymenu`, donc les deux exposent les mêmes sous-espaces de noms.

Les actions exposent deux assistants :
- `fancymenu.actions.execute(actionType, actionValue?)`
- `fancymenu.actions.executeWithCallback(actionType, actionValue?, onSuccess?, onFailure?)`

## 2. Disponibilité

```javascript
if (typeof fancymenu !== 'undefined') {
    // utilisation sûre
}

window.addEventListener('fancymenu-ready', () => {
    console.log('L’API FancyMenu est prête');
});
```

Le contenu peut également être hébergé localement : placez les fichiers HTML dans `<game-directory>/config/fancymenu/assets/` et chargez-les via des URL de la forme `file:///config/fancymenu/assets/<name>.html`.

## 3. Exécution des actions

Utilisez l'espace de noms `fancymenu.actions`. Chaque appel correspond aux chaînes d'actions utilisées dans les scripts FancyMenu.

### Appels rapides

```javascript
fancymenu.actions.execute('quitgame');                // action sans valeur
fancymenu.actions.execute('opengui', 'title_screen'); // action avec valeur
fancymenu.actions.execute('set_variable', 'hp:20');   // la valeur utilise le format nom:valeur
```

### Avec callbacks

```javascript
fancymenu.actions.executeWithCallback(
    'opengui',
    'title_screen',
    result => console.log('Écran titre ouvert'),
    error  => console.error('L’ouverture a échoué :', error)
);

// Le paramètre value est facultatif. S’il est omis, passez les callbacks directement après actionType.
fancymenu.actions.executeWithCallback(
    'quitgame',
    result => console.log('Quitter déclenché'),
    error  => console.error('L’arrêt a échoué :', error)
);
```

Les assistants hérités `fancymenu.execute(...)` et `fancymenu.executeWithCallback(...)` délèguent toujours à l'espace de noms `actions`.

### Types d'actions courants

- `quitgame` – quitte immédiatement le jeu (sans valeur)
- `back_to_last_screen` – retourne à l'interface précédente (sans valeur)
- `opengui` – ouvre un écran FancyMenu ou vanilla (valeur : identifiant de l'écran)
- `openlink` – lance un navigateur (valeur : URL)
- `sendmessage` – envoie une ligne de chat (valeur : texte du message)
- `set_variable` – attribue une variable FancyMenu (valeur : `name:value`)
- `joinserver` – se connecte à un serveur (valeur : adresse)
- `disconnect_server_or_world` – se déconnecte et bascule vers un écran cible (valeur : identifiant de l'écran)

Toute action existant dans FancyMenu est disponible via le pont ; consultez les [scripts d'action](./action-scripts) pour le catalogue complet.

## 4. Lecture des placeholders

Le système de [placeholder](/placeholders) de FancyMenu est exposé via `fancymenu.placeholders` (et `FancyMenu.placeholders`). Les deux méthodes d'assistance renvoient `Promise<string>` :

```ts
fancymenu.placeholders.get(identifier: string): Promise<string>
fancymenu.placeholders.getWithVars(identifier: string, ...vars: string[]): Promise<string>
```

### Fourniture de variables

- Les variables sont des chaînes au format `name:value`. Le pont ne coupe qu'au niveau du **premier** deux-points, de sorte que la valeur peut contenir d'autres deux-points.
- Les noms et les valeurs sont trimés ; les noms vides sont rejetés.
- Fournissez autant de variables que le placeholder l'exige. Omettez celles qui sont facultatives.

### Exemples

```javascript
// Sans variables
fancymenu.placeholders.get('playername')
    .then(name => console.log('Joueur :', name));

// Une variable
fancymenu.placeholders.getWithVars('uptime_duration', 'output_as_millis:false')
    .then(seconds => console.log('Temps de fonctionnement (s) :', seconds));

// Plusieurs variables
fancymenu.placeholders.getWithVars(
    'split_text',
    'input:apple|banana|carrot',
    'regex:\\|',
    'max_parts:-1',
    'split_index:1'
).then(part => console.log('Partie sélectionnée :', part));
```

### Modèle d'erreur

Les promesses rejetées contiennent une erreur structurée :

```ts
interface PlaceholderError {
    code: 'NOT_FOUND' | 'MISSING_VARIABLE' | 'INVALID_VARIABLE' | 'EVALUATION_ERROR' | 'INTERNAL_ERROR';
    message: string;
    details?: unknown;
}
```

Exemple de gestion :

```javascript
fancymenu.placeholders.get('unknown')
    .catch(error => console.warn(error.code, error.message));
```

## 5. Exemple complet

```html
<!DOCTYPE html>
<html>
<head>
    <title>Intégration FancyMenu</title>
</head>
<body>
    <h1>Contrôles du jeu</h1>
    
    <button onclick="quitGame()">Quitter le jeu</button>
    <button onclick="openTitleScreen()">Écran titre</button>
    <button onclick="disconnectFromServer()">Se déconnecter</button>
    <button onclick="setVariable()">Définir une variable</button>
    <button onclick="loadPlaceholders()">Charger les placeholders</button>

    <div id="placeholderOutput" style="margin-top:16px;font-family:monospace"></div>
    
    <script>
        function getActions() {
            if (typeof fancymenu === 'undefined') {
                console.warn('L’API FancyMenu n’est pas encore disponible.');
                return null;
            }
            return fancymenu.actions || fancymenu;
        }

        function quitGame() {
            const actions = getActions();
            if (!actions) return;
            actions.execute('quitgame');
        }
        
        function openTitleScreen() {
            const actions = getActions();
            if (!actions) return;
            actions.executeWithCallback(
                'opengui',
                'title_screen',
                () => console.log('Écran titre ouvert !'),
                err => console.error('Erreur :', err)
            );
        }
        
        function disconnectFromServer() {
            const actions = getActions();
            if (!actions) return;
            actions.execute('disconnect_server_or_world', 'title_screen');
        }
        
        function setVariable() {
            const actions = getActions();
            if (!actions) return;
            var varName = prompt('Nom de la variable :');
            var varValue = prompt('Valeur de la variable :');
            if (varName && varValue) {
                actions.execute('set_variable', varName + ':' + varValue);
            }
        }

        function loadPlaceholders() {
            if (typeof fancymenu === 'undefined' || !fancymenu.placeholders) {
                console.warn('L’API des placeholders FancyMenu n’est pas encore disponible.');
                return;
            }

            Promise.all([
                fancymenu.placeholders.get('playername'),
                fancymenu.placeholders.getWithVars('uptime_duration', 'output_as_millis:false'),
                fancymenu.placeholders.getWithVars(
                    'split_text',
                    'input:apple|banana|carrot',
                    'regex:\\|',
                    'max_parts:-1',
                    'split_index:1'
                )
            ]).then(([playerName, uptimeSeconds, secondFruit]) => {
                document.getElementById('placeholderOutput').textContent =
                    'Joueur : ' + playerName + '\n' +
                    'Temps de fonctionnement (secondes) : ' + uptimeSeconds + '\n' +
                    'Deuxième fruit : ' + secondFruit;
            }).catch(error => {
                console.error('La requête de placeholder a échoué :', error);
            });
        }
    </script>
</body>
</html>
```

## 6. Bonnes pratiques et remarques

- **Détectez le pont** avant de l’utiliser, ou écoutez `fancymenu-ready`.
- **Gérez les erreurs** (callbacks pour les [actions](/action-scripts), `.catch` pour les [placeholders](/placeholders)) afin d’afficher des retours utiles.
- **Validez les entrées** avant de les transmettre aux actions ou aux variables de [placeholder](/placeholders).
- **Limitez le débit des requêtes** ; évitez de bombarder le pont avec des appels trop fréquents (surtout les boucles d’actualisation de placeholders).
- **Sécurité :** le contenu du navigateur peut invoquer n’importe quelle action FancyMenu enregistrée, y compris les actions de fichiers, réseau, commandes, presse-papiers, resource-pack, liens et quitter. Ne chargez que des pages de confiance et validez toutes les données reçues du contenu web.

## 7. Dépannage

1. Vérifiez que la page est chargée dans un navigateur MCEF contrôlé par FancyMenu.
2. Consultez la console du navigateur pour détecter les erreurs JavaScript.
3. Vérifiez que l'identifiant du [placeholder](/placeholders) ou le type d'[action](/action-scripts) est correct et que les valeurs requises sont fournies.
4. Consultez le journal Minecraft (`latest.log`) pour les messages d'erreur FancyMenu si l'exécution échoue de manière inattendue.
