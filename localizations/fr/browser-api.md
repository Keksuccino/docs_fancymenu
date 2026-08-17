---
title: API JavaScript du navigateur
description: >-
  Comment utiliser l’API JavaScript de FancyMenu dans les fonctionnalités basées
  sur Rinku, comme l’élément Browser.
---
# API JavaScript de FancyMenu

FancyMenu injecte un pont JavaScript dans chaque fonctionnalité basée sur [Rinku](https://modrinth.com/mod/rinku) (par exemple, l’élément **Browser**). Ce pont permet au contenu web de :

- exécuter directement n’importe quelle [action](./action-scripts) de FancyMenu depuis JavaScript ;
- lire de manière asynchrone n’importe quel [placeholder](/placeholders) de FancyMenu.

Deux variables globales exposent l’API :
- `window.fancymenu` – espace de noms principal ;
- `window.FancyMenu` – alias (reproduit exactement la structure de `fancymenu`).

Utilisez l’événement `fancymenu-ready` ou la détection de fonctionnalité pour vous assurer que le pont est disponible avant de l’appeler.

## 1. Espaces de noms et structure

- `fancymenu.actions` – exécute les actions FancyMenu depuis le navigateur ;
- `fancymenu.placeholders` – lit de manière asynchrone les valeurs des placeholders FancyMenu ;
- `FancyMenu` reproduit `fancymenu` : les deux exposent donc les mêmes sous-espaces de noms.

Les actions exposent deux fonctions utilitaires :
- `fancymenu.actions.execute(actionType, actionValue?)`
- `fancymenu.actions.executeWithCallback(actionType, actionValue?, onSuccess?, onFailure?)`

## 2. Disponibilité

```javascript
if (typeof fancymenu !== 'undefined') {
    // utilisation possible en toute sécurité
}

window.addEventListener('fancymenu-ready', () => {
    console.log('L’API FancyMenu est prête');
});
```

Le contenu peut également être hébergé localement : placez les fichiers HTML dans `<game-directory>/config/fancymenu/assets/` et chargez-les via des URL de la forme `file:///config/fancymenu/assets/<name>.html`.

## 3. Exécution d’actions

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
    result => console.log('Écran-titre ouvert'),
    error  => console.error('Échec de l’ouverture :', error)
);

// Le paramètre de valeur est facultatif. S’il est omis, transmettez directement les fonctions de rappel après actionType.
fancymenu.actions.executeWithCallback(
    'quitgame',
    result => console.log('Fermeture du jeu déclenchée'),
    error  => console.error('Échec de la fermeture :', error)
);
```

Les anciennes fonctions utilitaires `fancymenu.execute(...)` et `fancymenu.executeWithCallback(...)` délèguent toujours leurs appels à l’espace de noms `actions`.

### Types d’actions courants

- `quitgame` – quitte immédiatement le jeu (aucune valeur) ;
- `back_to_last_screen` – revient à l’interface précédente (aucune valeur) ;
- `opengui` – ouvre un écran FancyMenu ou vanilla (valeur : identifiant de l’écran) ;
- `openlink` – lance un navigateur (valeur : URL) ;
- `sendmessage` – envoie une ligne de discussion (valeur : texte du message) ;
- `set_variable` – définit une variable FancyMenu (valeur : `name:value`) ;
- `joinserver` – se connecte à un serveur (valeur : adresse) ;
- `disconnect_server_or_world` – se déconnecte et affiche un écran cible (valeur : identifiant de l’écran).

Toutes les actions disponibles dans FancyMenu sont accessibles via le pont. Consultez les [scripts d’action](./action-scripts) pour obtenir le catalogue complet.

## 4. Lecture des placeholders

Le système de [placeholders](/placeholders) de FancyMenu est exposé via `fancymenu.placeholders` (et `FancyMenu.placeholders`). Les deux fonctions utilitaires renvoient une `Promise<string>` :

```ts
fancymenu.placeholders.get(identifier: string): Promise<string>
fancymenu.placeholders.getWithVars(identifier: string, ...vars: string[]): Promise<string>
```

### Fourniture de variables

- Les variables sont des chaînes au format `nom:valeur`. Le pont ne sépare qu’au niveau des **deux-points** (`:`) présents en premier : la valeur peut donc contenir d’autres deux-points.
- Les noms et les valeurs sont supprimés des espaces superflus ; les noms vides sont rejetés.
- Fournissez autant de variables que le placeholder l’exige. Omettez les variables facultatives.

### Exemples

```javascript
// Aucune variable
fancymenu.placeholders.get('playername')
    .then(name => console.log('Joueur :', name));

// Une variable
fancymenu.placeholders.getWithVars('uptime_duration', 'output_as_millis:false')
    .then(seconds => console.log('Temps d’activité (s) :', seconds));

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
    <button onclick="openTitleScreen()">Écran-titre</button>
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
                () => console.log('Écran-titre ouvert !'),
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
                    'Temps d’activité (secondes) : ' + uptimeSeconds + '\n' +
                    'Deuxième fruit : ' + secondFruit;
            }).catch(error => {
                console.error('Échec de la requête de placeholder :', error);
            });
        }
    </script>
</body>
</html>
```

## 6. Bonnes pratiques et remarques

- **Détectez le pont** avant de l’utiliser ou écoutez l’événement `fancymenu-ready`.
- **Gérez les erreurs** (fonctions de rappel pour les [actions](/action-scripts), `.catch` pour les [placeholders](/placeholders)) afin de fournir des informations utiles.
- **Validez les entrées** avant de les transmettre aux actions ou aux variables de [placeholder](/placeholders).
- **Limitez la fréquence des requêtes** : évitez de surcharger le pont avec des appels répétés très rapides, en particulier lors des boucles d’actualisation des placeholders.
- **Sécurité :** le contenu du navigateur peut invoquer n’importe quelle action FancyMenu enregistrée, notamment les actions liées aux fichiers, au réseau, aux commandes, au presse-papiers, aux packs de ressources, aux liens et à la fermeture du jeu. Ne chargez que des pages fiables et validez toutes les données reçues du contenu web.

## 7. Dépannage

1. Vérifiez que la page est chargée dans un navigateur Rinku contrôlé par FancyMenu.
2. Consultez la console du navigateur pour repérer d’éventuelles erreurs JavaScript.
3. Vérifiez que l’identifiant du [placeholder](/placeholders) ou le type d’[action](/action-scripts) est correct et que les valeurs requises sont fournies.
4. Si l’exécution échoue de manière inattendue, consultez le journal de Minecraft (`latest.log`) pour rechercher les messages d’erreur de FancyMenu.
