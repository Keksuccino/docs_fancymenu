---
title: Variables
description: >-
  Comment stocker du texte et des listes dans des variables, et les utiliser
  dans des textes, des actions et des conditions.
sourceBlobSha: 2f0d48fd6cc100f976d4fdf1bceb28fe1a540a52
---

# Variables

Les variables sont des valeurs que FancyMenu mémorise, même après la fermeture du jeu. Utilisez-les pour compter les clics, mémoriser des choix, suivre la progression ou conserver des listes, comme des astuces de chargement. Les textes, les actions, les conditions, les écouteurs et certains éléments peuvent les lire et les modifier.

> [!TIP]
> Les actions liées aux variables sont répertoriées dans les [scripts d’action](/action-scripts), les conditions dans les [conditions](/conditions) et l’écouteur dans les [écouteurs](/listeners#on-variable-updated-fm-variable).

# Variables de texte et de liste

Il existe deux types de variables :

- Les variables de texte contiennent un seul texte, comme `dark`, `5` ou `true`.
- Les variables de liste contiennent une liste d’entrées, comme des astuces de chargement ou des noms de serveurs. Chaque entrée est un texte distinct.

La position d’une entrée dans une liste est son index. La première entrée a l’index `0`, la deuxième `1`, et ainsi de suite. Les index négatifs comptent à partir de la fin : `-1` correspond donc à la dernière entrée.

Les éléments qui ne prennent en charge que le texte, comme `$$name` ou **Is Variable Value (FM Variable)**, obtiennent une liste sous forme de tableau JSON contenant ses entrées, par exemple `["Craft a bed before your first night.","Torches keep most mobs away."]`.

# Gérer les variables

Ouvrez **barre de menus -> Personnalisation -> Gérer les variables**. Cette option n’est disponible dans la barre de menus qu’en dehors de l’éditeur de disposition.

<img width="800" alt="Ajout de la variable de texte menu_theme avec la valeur dark et de la variable de liste tips avec trois astuces dans le menu Gérer les variables" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/variables_manage.gif?raw=true">

## Ajouter des variables

1. Faites un clic droit sur la liste, puis cliquez sur **Ajouter une variable de texte** ou **Ajouter une variable de liste**.
2. Saisissez un nom, puis cliquez sur **Terminé**.

Les noms peuvent contenir des lettres minuscules, des chiffres, `.`, `_` et `-`. Chaque nom ne peut être utilisé qu’une seule fois.

## Modifier des variables

Faites un clic droit sur une variable pour accéder aux options suivantes :

| Option | Description |
|---|---|
| **Définir la valeur** | Définit le texte d’une variable de texte. |
| **Modifier la liste** | Ouvre l’éditeur de liste d’une variable de liste (voir ci-dessous). |
| **Convertir en liste…** | Convertit une variable de texte en liste. Le **Séparateur** divise le texte en entrées : saisissez `\n` pour séparer les lignes. **Supprimer les espaces autour des entrées** enlève les espaces autour de chaque entrée et **Ignorer les entrées vides** exclut les entrées vides. Un texte qui est déjà un tableau JSON, comme `["a","b"]`, est lu comme tel (**Lire comme un tableau JSON**). |
| **Convertir en texte…** | Convertit une liste en variable de texte. Le **Séparateur** est placé entre les entrées, ou **Conserver le texte JSON** conserve la liste sous forme de tableau JSON. |
| **Vider la variable au démarrage du jeu** | Vide la variable chaque fois que le jeu démarre. Utile pour les valeurs qui ne doivent durer qu’une session. |
| **Supprimer la variable** | Supprime la variable. |
| **Copier** et **Coller** | Créent une copie d’une variable. |
| **Exporter la variable pour l’IA** | Exporte la variable pour les [conversations avec l’IA](/export-for-ai). |

Les modifications sont appliquées immédiatement. Annulez-les avec `Ctrl + Z` et rétablissez-les avec `Ctrl + Y` (`Cmd` sur macOS). Commencez à taper pour effectuer une recherche, appuyez sur `Enter` pour modifier la variable sélectionnée ou sur `Delete` pour la supprimer.

## Modifier des listes

L’éditeur de liste affiche chaque entrée avec son index.

- Pour ajouter des entrées, cliquez sur **Ajouter une entrée** sous la liste, saisissez l’entrée et appuyez sur `Enter`. La saisie de l’entrée suivante commence immédiatement. Appuyez sur `Enter` sur une entrée vide ou sur `Esc` pour arrêter l’ajout.
- Pour modifier une entrée, double-cliquez dessus. `Shift + Enter` l’ouvre dans l’éditeur de texte, où vous pouvez ajouter des sauts de ligne.
- Pour réorganiser les entrées, faites-les glisser ou appuyez sur `Alt + Up` et `Alt + Down`.
- Faites un clic droit sur une entrée pour accéder à **Dupliquer l’entrée** (`Ctrl + D`), **Supprimer l’entrée** (`Delete`), **Copier**, **Coller**, **Déplacer vers le haut** et **Déplacer vers le bas**.
- **Modifier comme du texte** permet de modifier toutes les entrées à la fois, à raison d’une par ligne.

**Terminé** enregistre la liste. **Annuler** abandonne toutes les modifications apportées dans l’éditeur de liste.

# Afficher des variables dans du texte

Saisissez `$$` suivi du nom d’une variable pour afficher sa valeur : une variable nommée `menu_theme` s’écrit `$$menu_theme`. Cela fonctionne dans tous les textes compatibles avec les [espaces réservés](/placeholders), comme les [éléments de texte](/text-in-menus), les libellés de boutons, les info-bulles et les valeurs des actions et des conditions. Le texte est automatiquement mis à jour lorsque la variable change.

```
Thème actuel : $$menu_theme
```

- `$$name` reste inchangé si la variable n’existe pas.
- Lorsque plusieurs noms commencent de la même façon, comme `coins` et `coins_record`, `$$coins_record` correspond toujours au nom le plus long.
- Une liste s’affiche sous forme de tableau JSON. Ces espaces réservés permettent d’afficher les listes de manière plus lisible :

| Espace réservé | Exemple | Résultat |
|---|---|---|
| **Get Variable Value (FM Variable)** | `{"placeholder":"getvariable","values":{"name":"clicks"}}` | La valeur, ou `0` si la variable est vide ou n’existe pas. Idéal pour les nombres. |
| **Get List Entry (FM Variable)** | `{"placeholder":"list_get","values":{"name":"tips","index":"0","fallback":"No tips yet"}}` | L’entrée à l’index indiqué, ou la valeur `fallback` s’il n’y en a pas. |
| **List Size (FM Variable)** | `{"placeholder":"list_size","values":{"name":"tips"}}` | Le nombre d’entrées de la liste. |
| **Index of List Entry (FM Variable)** | `{"placeholder":"list_index_of","values":{"name":"tips","value":"Torches keep most mobs away.","ignore_case":"false"}}` | L’index de la première entrée correspondant exactement à `value`, ou `-1`. |
| **Join List Entries (FM Variable)** | `{"placeholder":"list_join","values":{"name":"tips","separator":"\n"}}` | Toutes les entrées réunies dans un texte, avec `separator` entre elles (`, ` si ce paramètre est omis). `\n` correspond à un saut de ligne. |

# Modifier des variables avec des actions

Les [scripts d’action](/action-scripts) modifient les variables lorsqu’on clique sur un bouton, qu’un minuteur s’exécute, qu’un écouteur se déclenche, et ainsi de suite.

## Variables de texte

[**Set Variable Value (FM Variable)**](/action-scripts#set-variable-value-fm-variable) prend le nom et la nouvelle valeur, séparés par `:`. Si la variable n’existe pas encore, elle est créée.

```
menu_theme:dark
```

Seul le premier `:` sépare le nom de la valeur. La valeur peut donc en contenir d’autres, comme dans `last_server:play.example.net:25565`.

Pour compter les clics sur un bouton, ajoutez 1 à l’ancienne valeur :

```
clicks:{"placeholder":"calc","values":{"decimal":"false","expression":"{"placeholder":"getvariable","values":{"name":"clicks"}} + 1"}}
```

**Get Variable Value (FM Variable)** renvoie `0` tant que `clicks` est vide. Le premier clic lui attribue donc la valeur `1`.

Set Variable Value ne convertit jamais une liste en texte. Un tableau JSON devient les entrées de la liste, un texte vide la vide et tout autre texte devient son unique entrée.

[**Delete Variable (FM Variable)**](/action-scripts#delete-variable-fm-variable) supprime une variable, tandis que [**Clear All Variables (FM Variable)**](/action-scripts#clear-all-variables-fm-variable) les supprime toutes.

## Actions de liste

Chaque action de liste possède sa propre fenêtre. Tous ses champs acceptent les espaces réservés.

| Action | Description |
|---|---|
| [**Add to List (FM Variable)**](/action-scripts#add-to-list-fm-variable) | Ajoute une entrée à la fin ou à un index donné. **Ignorer si déjà dans la liste** n’ajoute rien si la liste contient déjà cette entrée. |
| [**Set List Entry (FM Variable)**](/action-scripts#set-list-entry-fm-variable) | Remplace l’entrée à un index donné. |
| [**Remove from List (FM Variable)**](/action-scripts#remove-from-list-fm-variable) | Supprime l’**entrée à l’index**, la **première correspondance** d’une valeur ou **toutes les correspondances**. |
| [**Clear List (FM Variable)**](/action-scripts#clear-list-fm-variable) | Supprime toutes les entrées. La liste est conservée, mais reste vide. |
| [**Set List (FM Variable)**](/action-scripts#set-list-fm-variable) | Remplace toutes les entrées par les parties d’un **texte à séparer** ou par les entrées d’un **tableau JSON**. `$$other_list` au format tableau JSON copie une autre liste. |
| [**Arrange List (FM Variable)**](/action-scripts#arrange-list-fm-variable) | **Trier de A à Z**, **Trier de Z à A**, **Nombres, du plus petit au plus grand**, **Nombres, du plus grand au plus petit**, **Inverser l’ordre**, **Mélanger** ou **Supprimer les doublons**. |

- Les actions de liste créent une liste si elle n’existe pas encore et convertissent les variables de texte vides en listes. Elles ne modifient jamais une variable de texte qui contient une valeur : [convertissez-la](#changing-variables) d’abord.
- Saisissez le nom de la liste sans `$$`. Avec `$$`, l’action utilise la valeur de cette variable comme nom.

Par exemple, un élément de texte affiche la première entrée de la liste `tips` :

```
{"placeholder":"list_get","values":{"name":"tips","index":"0"}}
```

Un bouton Astuce suivante placé en dessous utilise l’action **Arrange List (FM Variable)** avec l’option **Mélanger** dans son script d’action :

<img width="800" alt="Ajout de l’action Arrange List avec la liste tips et l’option Shuffle au script d’action d’un bouton Astuce suivante dans l’éditeur de disposition" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/variables_next_tip_script.gif?raw=true">

À chaque clic, la liste est mélangée et le texte affiche donc une astuce aléatoire :

<img width="800" alt="Un clic sur le bouton Astuce suivante affiche une autre astuce du jour" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/variables_next_tip_result.gif?raw=true">

## Parcourir une liste

La [boucle FOR EACH](/action-scripts#for-each-loop) exécute les actions qu’elle contient une fois pour chaque entrée d’une liste, de la première à la dernière.

1. Faites un clic droit dans la zone de script de l’éditeur de scripts d’action, puis cliquez sur **Ajouter une boucle FOR EACH**.
2. Saisissez le nom de la variable de liste, sans `$$`, puis cliquez sur **Terminé**.
3. Ajoutez des actions dans la boucle. Dans leurs valeurs, `$$list_entry` correspond à l’entrée actuelle et `$$list_index` à son index.

Par exemple, une liste `starter_commands` contenant les entrées `/time set day` et `/weather clear`, avec une action [**Send Chat Message/Command**](/action-scripts#send-chat-messagecommand) dans la boucle et cette valeur, exécute les deux commandes :

```
$$list_entry
```

- La boucle lit la liste une seule fois, au démarrage. Les actions qu’elle contient peuvent modifier la liste sans changer les entrées parcourues par la boucle.
- Une variable de texte ou une liste inexistante fait que la boucle ne s’exécute aucune fois.
- Comme les boucles WHILE, elle s’arrête au bout de 3 secondes afin d’éviter de bloquer le jeu.

# Vérifier des variables

Les [conditions](/conditions) affichent des éléments ou exécutent certaines parties des scripts d’action uniquement lorsqu’une variable a une valeur précise.

- [**Is Variable Value (FM Variable)**](/conditions#is-variable-value-fm-variable) vérifie la valeur complète. Pour les listes, la comparaison porte sur le tableau JSON de toutes les entrées.
- [**List Contains Entry (FM Variable)**](/conditions#list-contains-entry-fm-variable) vérifie si une liste contient une entrée. La correspondance doit porter sur l’entrée entière. **Ignorer la casse** permet à `Apple` de correspondre à `apple`.
- [**Is Number**](/conditions#is-number) compare des nombres, par exemple pour vérifier si `$$clicks` est supérieur à `5`.

Par exemple, un bouton ouvre le dernier article d’actualité et ajoute `news_42` à une liste `read_news` à l’aide de **Add to List (FM Variable)**. Un badge « Nouveau ! » à côté du bouton utilise la condition **List Contains Entry (FM Variable)** pour `news_42`, avec le **mode de condition** réglé sur l’option opposée. Le badge disparaît donc une fois que le joueur a lu l’article.

# Lier des variables à des éléments

- [Champ de saisie de texte](/elements#text-input-field) : **Lier à une variable** enregistre dans la variable le texte saisi par le joueur et le champ affiche la valeur de cette variable. Si le champ est lié à une liste, le texte saisi remplace toute la liste.
- [Case à cocher](/elements#checkbox) : activez le **mode variable** et définissez **Lier à une variable**. La case à cocher écrit `true` ou `false` dans la variable.
- [Curseur](/elements#slider) de type **Liste de valeurs** : **Valeurs depuis une variable de liste** récupère les valeurs du curseur depuis une liste. Les entrées ajoutées à la liste ou supprimées de celle-ci sont immédiatement prises en compte.

# Réagir aux modifications

- L’écouteur [**On Variable Updated [FM Variable]**](/listeners#on-variable-updated-fm-variable) exécute un script d’action chaque fois qu’une variable est définie.
- La [commande `/fmvariable`](/commands#fmvariable) permet de définir et de lire des variables depuis le chat, les blocs de commande et d’autres mods.

# Où les variables sont-elles enregistrées ?

FancyMenu enregistre immédiatement les variables dans `<game-directory>/config/fancymenu/user_variables.db`. Elles sont donc conservées après le redémarrage du jeu.

- Les variables sont communes à toute l’instance Minecraft et à son [profil](/profiles) actif. Elles ne sont pas séparées par disposition, monde, serveur ou joueur.
- Les noms sont sensibles à la casse.
- Ne stockez pas de mots de passe, de jetons ni d’autres secrets dans des variables. Toute personne ayant accès au dossier du jeu peut les lire.
