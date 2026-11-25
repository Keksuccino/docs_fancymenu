---
title: API JavaScript du navigateur
description: >-
  Comment utiliser l’API JavaScript de FancyMenu dans les fonctionnalités de
  mods basées sur Rinku, comme l’élément Browser.
sourceBlobSha: 1dff260c0c5337037200dbf9033300a6bba56ca1
---
# API JavaScript de FancyMenu

FancyMenu injecte un pont JavaScript dans chaque fonctionnalité reposant sur [Rinku](https://modrinth.com/mod/rinku) (par exemple, l’élément **Browser**). Ce pont permet au contenu Web de :

- lancer directement depuis JavaScript n’importe quelle [action](/action-scripts) FancyMenu ;
- lire de manière asynchrone n’importe quel [paramètre de remplacement](/placeholders) FancyMenu.

Deux variables globales exposent l’API :
- `window.fancymenu` – espace de noms principal
- `window.FancyMenu` – alias (reproduit exactement la structure de `fancymenu`)

Utilisez l’événement `fancymenu-ready` ou la détection de fonctionnalités pour vous assurer que le pont est disponible avant de l’utiliser.

## 1. Espaces de noms et structure

- `fancymenu.actions` – exécuter des actions FancyMenu depuis le navigateur.
- `fancymenu.placeholders` – lire de manière asynchrone les valeurs des paramètres de remplacement FancyMenu.
- `FancyMenu` reproduit la structure de `fancymenu` : les deux exposent donc les mêmes sous-espaces de noms.

Les actions proposent deux fonctions utilitaires :
- `fancymenu.actions.execute(actionType, actionValue?)`
- `fancymenu.actions.executeWithCallback(actionType, actionValue?, onSuccess?, onFailure?)`

## 2. Disponibilité

```javascript
if (typeof fancymenu !== 'undefined') {
    // l’API peut être utilisée sans risque
}

window.addEventListener('fancymenu-ready', () => {
    console.log('L’API FancyMenu est prête');
});
```

Le contenu peut également être hébergé localement : placez les fichiers HTML dans `<game-directory>/config/fancymenu/assets/` et chargez-les à l’aide d’URL de la forme `file:///config/fancymenu/assets/<name>.html`.

## 3. Exécuter des actions

Utilisez l’espace de noms `fancymenu.actions`. Chaque appel reprend les chaînes d’action utilisées dans les scripts FancyMenu.

### Appels rapides

```javascript
fancymenu.actions.execute('quitgame');                // action sans valeur
fancymenu.actions.execute('opengui', 'title_screen'); // action avec valeur
fancymenu.actions.execute('set_variable', 'hp:20');   // la valeur utilise le format nom:valeur
```

### Avec des fonctions de rappel

```javascript
fancymenu.actions.executeWithCallback(
    'opengui',
    'title_screen',
    result => console.log('Écran titre ouvert'),
    error  => console.error('Échec de l’ouverture :', error)
);

// Le paramètre value est facultatif. S’il est omis, passez les fonctions de rappel directement après actionType.
fancymenu.actions.executeWithCallback(
    'quitgame',
    result => console.log('Fermeture du jeu lancée'),
    error  => console.error('Échec de la fermeture du jeu :', error)
);
```

Les anciennes fonctions utilitaires `fancymenu.execute(...)` et `fancymenu.executeWithCallback(...)` redirigent toujours les appels vers l’espace de noms `actions`.

### Types d’action courants

- `quitgame` – quitte immédiatement le jeu (sans valeur)
- `back_to_last_screen` – revient à l’interface précédente (sans valeur)
- `opengui` – ouvre un écran FancyMenu ou vanilla (valeur : identifiant de l’écran)
- `openlink` – lance un navigateur (valeur : URL)
- `sendmessage` – envoie un message dans le chat (valeur : texte du message)
- `set_variable` – définit une variable FancyMenu (valeur : `name:value`)
- `joinserver` – se connecte à un serveur (valeur : adresse)
- `disconnect_server_or_world` – se déconnecte et passe à l’écran cible (valeur : identifiant de l’écran)

Toutes les actions disponibles dans FancyMenu peuvent être utilisées via le pont ; consultez les [scripts d’action](/action-scripts) pour obtenir la liste complète.

## 4. Lire les paramètres de remplacement

Le système de [paramètres de remplacement](/placeholders) de FancyMenu est accessible via `fancymenu.placeholders` (et `FancyMenu.placeholders`). Les deux méthodes utilitaires renvoient un `Promise<string>` :

```ts
fancymenu.placeholders.get(identifier: string): Promise<string>
fancymenu.placeholders.getWithVars(identifier: string, ...vars: string[]): Promise<string>
```

### Fournir des variables

- Les variables sont des chaînes au format `nom:valeur`. Le pont ne sépare la chaîne qu’au **premier** deux-points ; la valeur peut donc en contenir d’autres.
- Les noms et les valeurs sont supprimés des espaces superflus ; les noms vides sont refusés.
- Fournissez autant de variables que le paramètre de remplacement en nécessite. Omettez celles qui sont facultatives.

### Exemples

```javascript
// Sans variable
fancymenu.placeholders.get('playername')
    .then(name => console.log('Joueur :', name));

// Une variable
fancymenu.placeholders.getWithVars('uptime_duration', 'output_as_millis:false')
    .then(seconds => console.log('Durée de fonctionnement (s) :', seconds));

// Plusieurs variables
fancymenu.placeholders.getWithVars(
    'split_text',
    'input:apple|banana|carrot',
    'regex:\\|',
    'max_parts:-1',
    'split_index:1'
).then(part => console.log('Élément sélectionné :', part));
```

### Gestion des erreurs

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
    <title>Intégration de FancyMenu</title>
</head>
<body>
    <h1>Commandes du jeu</h1>
    
    <button onclick="quitGame()">Quitter le jeu</button>
    <button onclick="openTitleScreen()">Écran titre</button>
    <button onclick="disconnectFromServer()">Se déconnecter</button>
    <button onclick="setVariable()">Définir une variable</button>
    <button onclick="loadPlaceholders()">Charger les paramètres de remplacement</button>

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
                console.warn('L’API des paramètres de remplacement FancyMenu n’est pas encore disponible.');
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
                    'Durée de fonctionnement (secondes) : ' + uptimeSeconds + '\n' +
                    'Deuxième fruit : ' + secondFruit;
            }).catch(error => {
                console.error('Échec de la requête de paramètre de remplacement :', error);
            });
        }
    </script>
</body>
</html>
```

## 6. Bonnes pratiques et remarques

- **Vérifiez la disponibilité du pont** avant de l’utiliser, ou écoutez l’événement `fancymenu-ready`.
- **Gérez les erreurs** (fonctions de rappel pour les [actions](/action-scripts), `.catch` pour les [paramètres de remplacement](/placeholders)) afin de fournir des informations utiles.
- **Validez les données saisies** avant de les transmettre aux actions ou aux variables de [paramètre de remplacement](/placeholders).
- **Limitez la fréquence des requêtes** ; évitez d’inonder le pont d’appels rapprochés (en particulier dans les boucles d’actualisation des paramètres de remplacement).
- **Sécurité :** le contenu du navigateur peut invoquer n’importe quelle action FancyMenu enregistrée, notamment les actions liées aux fichiers, au réseau, aux commandes, au presse-papiers, aux packs de ressources, aux liens et à la fermeture du jeu. Ne chargez que des pages de confiance et validez toutes les données provenant du contenu Web.

## 7. Dépannage

1. Vérifiez que la page est chargée dans un navigateur Rinku contrôlé par FancyMenu.
2. Consultez la console du navigateur pour repérer les erreurs JavaScript.
3. Vérifiez que l’identifiant du [paramètre de remplacement](/placeholders) ou le type d’[action](/action-scripts) est correct et que les valeurs requises sont fournies.
4. Si l’exécution échoue de façon inattendue, consultez le journal Minecraft (`latest.log`) pour repérer les messages d’erreur de FancyMenu.
