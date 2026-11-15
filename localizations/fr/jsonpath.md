---
title: Chemins JSON
description: Comment utiliser Jayway JsonPath dans l’espace réservé de l’analyseur JSON.
excludeFromAiPlaintext: true
sourceBlobSha: 2aa2965bffefdb17d944b31190f40ec33198c1e4
---
# Chemins JSON dans FancyMenu

L’espace réservé **Analyseur JSON** de FancyMenu utilise [Jayway JsonPath](https://github.com/json-path/JsonPath) pour récupérer du contenu à partir de fichiers JSON.
Cette page explique les chemins JSON en détail.

Le texte de cette page est une copie du README du dépôt GitHub de Jayway JsonPath.

> [!NOTE]
> Dans ce texte, le terme « expression JsonPath » désigne un chemin JSON.

# JsonPath

Les expressions JsonPath font toujours référence à une structure JSON, de la même manière que les expressions XPath sont utilisées avec un document XML. L’« objet membre racine » dans JsonPath est toujours désigné par `$`, qu’il s’agisse d’un objet ou d’un tableau.

Les expressions JsonPath peuvent utiliser la notation avec points

`$.store.book[0].title`

ou la notation entre crochets

`$['store']['book'][0]['title']`

## Opérateurs

| Opérateur                 | Description                                                        |
| :------------------------ | :----------------------------------------------------------------- |
| `$`                       | Élément racine à interroger. Toutes les expressions de chemin commencent par celui-ci. |
| `@`                       | Nœud actuel traité par un prédicat de filtre.                     |
| `*`                       | Caractère générique. Disponible partout où un nom ou un nombre est requis. |
| `..`                      | Recherche approfondie. Disponible partout où un nom est requis.   |
| `.<name>`                 | Enfant avec notation utilisant des points                         |
| `['<name>' (, '<name>')]` | Enfant ou enfants avec notation entre crochets                     |
| `[<number> (, <number>)]` | Index ou indices de tableau                                       |
| `[start:end]`             | Opérateur de tranche de tableau                                   |
| `[?(<expression>)]`       | Expression de filtre. L’expression doit renvoyer une valeur booléenne. |


## Fonctions

Les fonctions peuvent être appelées à la fin d’un chemin : l’entrée d’une fonction correspond à la sortie de l’expression de chemin.
Le type de sortie dépend de la fonction elle-même.

| Fonction                  | Description                                                         | Type de sortie |
| :------------------------ | :------------------------------------------------------------------ |:----------- |
| min()                     | Fournit la valeur minimale d’un tableau de nombres                 | Double      |
| max()                     | Fournit la valeur maximale d’un tableau de nombres                 | Double      |
| avg()                     | Fournit la valeur moyenne d’un tableau de nombres                  | Double      | 
| stddev()                  | Fournit l’écart type d’un tableau de nombres                       | Double      | 
| length()                  | Fournit la longueur d’un tableau                                   | Integer     |
| sum()                     | Fournit la somme d’un tableau de nombres                           | Double      |
| keys()                    | Fournit les clés de propriété (une alternative au tilde final `~`) | `Set<E>`    |
| concat(X)                 | Fournit une version concaténée de la sortie du chemin avec un nouvel élément | comme l’entrée |
| append(X)                 | Ajoute un élément au tableau de sortie du chemin JSON              | comme l’entrée |

## Opérateurs de filtre

Les filtres sont des expressions logiques utilisées pour filtrer des tableaux. Un filtre typique serait `[?(@.age > 18)]`, où `@` représente l’élément actuellement traité. Des filtres plus complexes peuvent être créés avec les opérateurs logiques `&&` et `||`. Les littéraux chaîne doivent être entourés de guillemets simples ou doubles (`[?(@.color == 'blue')]` ou `[?(@.color == "blue")]`).   

| Opérateur                 | Description                                                           |
| :----------------------- | :-------------------------------------------------------------------- |
| ==                       | la valeur de gauche est égale à celle de droite (1 n’est pas égal à '1') |
| !=                       | la valeur de gauche n’est pas égale à celle de droite                |
| <                        | la valeur de gauche est inférieure à celle de droite                 |
| <=                       | la valeur de gauche est inférieure ou égale à celle de droite        |
| >                        | la valeur de gauche est supérieure à celle de droite                 |
| >=                       | la valeur de gauche est supérieure ou égale à celle de droite        |
| =~                       | la valeur de gauche correspond à une expression régulière `[?(@.name =~ /foo.*?/i)]` |
| in                       | la valeur de gauche existe dans celle de droite `[?(@.size in ['S', 'M'])]` |
| nin                      | la valeur de gauche n’existe pas dans celle de droite                |
| subsetof                 | la valeur de gauche est un sous-ensemble de celle de droite `[?(@.sizes subsetof ['S', 'M', 'L'])]` |
| anyof                    | la valeur de gauche a une intersection avec celle de droite `[?(@.sizes anyof ['M', 'L'])]` |
| noneof                   | la valeur de gauche n’a aucune intersection avec celle de droite `[?(@.sizes noneof ['M', 'L'])]` |
| size                     | la taille de la valeur de gauche (tableau ou chaîne) doit correspondre à celle de droite |
| empty                    | la valeur de gauche (tableau ou chaîne) doit être vide              |


## Exemples de chemins

Étant donné le JSON suivant

```javascript
{
    "store": {
        "book": [
            {
                "category": "reference",
                "author": "Nigel Rees",
                "title": "Sayings of the Century",
                "price": 8.95
            },
            {
                "category": "fiction",
                "author": "Evelyn Waugh",
                "title": "Sword of Honour",
                "price": 12.99
            },
            {
                "category": "fiction",
                "author": "Herman Melville",
                "title": "Moby Dick",
                "isbn": "0-553-21311-3",
                "price": 8.99
            },
            {
                "category": "fiction",
                "author": "J. R. R. Tolkien",
                "title": "The Lord of the Rings",
                "isbn": "0-395-19395-8",
                "price": 22.99
            }
        ],
        "bicycle": {
            "color": "red",
            "price": 19.95
        }
    },
    "expensive": 10
}
```

| JsonPath (cliquez sur le lien pour essayer)| Résultat |
| :------- | :----- |
| <a href="http://jsonpath.herokuapp.com/?path=$.store.book[*].author" target="_blank">$.store.book[*].author</a>| Les auteurs de tous les livres |
| <a href="http://jsonpath.herokuapp.com/?path=$..author" target="_blank">$..author</a>                   | Tous les auteurs |
| <a href="http://jsonpath.herokuapp.com/?path=$.store.*" target="_blank">$.store.*</a>                  | Tous les éléments, livres et vélos compris |
| <a href="http://jsonpath.herokuapp.com/?path=$.store..price" target="_blank">$.store..price</a>             | Le prix de tous les éléments |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[2]" target="_blank">$..book[2]</a>                 | Le troisième livre |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[2]" target="_blank">$..book[-2]</a>                 | L’avant-dernier livre |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[0,1]" target="_blank">$..book[0,1]</a>               | Les deux premiers livres |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[:2]" target="_blank">$..book[:2]</a>                | Tous les livres de l’index 0 (inclus) à l’index 2 (exclus) |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[1:2]" target="_blank">$..book[1:2]</a>                | Tous les livres de l’index 1 (inclus) à l’index 2 (exclus) |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[-2:]" target="_blank">$..book[-2:]</a>                | Les deux derniers livres |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[2:]" target="_blank">$..book[2:]</a>                | Le deuxième livre en partant de la fin |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[?(@.isbn)]" target="_blank">$..book[?(@.isbn)]</a>          | Tous les livres possédant un numéro ISBN |
| <a href="http://jsonpath.herokuapp.com/?path=$.store.book[?(@.price < 10)]" target="_blank">$.store.book[?(@.price < 10)]</a> | Tous les livres du magasin coûtant moins de 10 |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[?(@.price <= $['expensive'])]" target="_blank">$..book[?(@.price <= $['expensive'])]</a> | Tous les livres du magasin qui ne sont pas « chers » |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[?(@.author =~ /.*REES/i)]" target="_blank">$..book[?(@.author =~ /.*REES/i)]</a> | Tous les livres correspondant à l’expression régulière (sans tenir compte de la casse) |
| <a href="http://jsonpath.herokuapp.com/?path=$..*" target="_blank">$..*</a>                        | Tout afficher |
| <a href="http://jsonpath.herokuapp.com/?path=$..book.length()" target="_blank">$..book.length()</a>                 | Le nombre de livres |
