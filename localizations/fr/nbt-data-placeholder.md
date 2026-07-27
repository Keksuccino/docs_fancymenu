---
title: Espace réservé pour les données NBT
description: 'Lire les données NBT des entités, des blocs et du stockage.'
---

# Espaces réservés pour les données NBT

FancyMenu fournit deux espaces réservés NBT :

| Espace réservé | S’exécute sur | Données disponibles |
|---|---|---|
| `nbt_data_get` | Client | Entités et entités de bloc visibles côté client |
| `nbt_data_get_server` | Serveur | Cibles vanilla de `/data get` ; nécessite FancyMenu sur le serveur |

# Espace réservé côté client

```text
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Health"}}
```

## Valeurs

| Valeur | Requis | Description |
|---|---|---|
| `source_type` | Oui | `entity` ou `block` |
| `entity_selector` | Pour les entités | Sélecteur côté client, UUID ou nom exact de l’entité |
| `block_pos` | Pour les blocs | Trois coordonnées entières absolues, par exemple `100 64 -200` |
| `nbt_path` | Oui | Chemin NBT, par exemple `Health`, `Pos[0]` ou `Inventory[0].id` |
| `scale` | Non | Multiplie les résultats numériques de `value` ; valeur par défaut : `1.0` |
| `return_type` | Non | `value`, `string`, `snbt` ou `json` ; valeur par défaut : `value` |

Les positions de blocs côté client ne prennent pas en charge les coordonnées `~` ou `^`.

## Sélecteurs d’entités côté client

| Sélecteur | Cibles initiales | Ordre par défaut |
|---|---|---|
| `@s` | Joueur local | Lui-même |
| `@p` | Joueurs | Le plus proche |
| `@a` | Joueurs | Ordre d’itération du client |
| `@r` | Joueurs | Aléatoire |
| `@e` | Toutes les entités visibles côté client | Ordre d’itération du client |

`@e` ne sélectionne pas l’entité la plus proche, sauf si vous ajoutez `sort=nearest`. La recherche directe par UUID et par nom exact de l’entité est également prise en charge.

Options de sélecteur prises en charge :

| Option | Description |
|---|---|
| `type` | ID d’entité ; préfixez avec `!` pour exclure |
| `name` | Nom d’affichage exact ; préfixez avec `!` pour exclure |
| `tag` | Balise d’entité ; préfixez avec `!` pour exclure |
| `limit` | Limite positive du nombre de résultats |
| `sort` | `nearest`, `furthest`, `random` ou `arbitrary` |
| `distance` | Intervalle de distance vanilla, par exemple `..10` ou `5..20` |
| `x`, `y`, `z` | Origine de recherche ; accepte les valeurs absolues et les décalages `~` |
| `dx`, `dy`, `dz` | Taille de la zone de recherche à partir de l’origine |

Les coordonnées locales `^` et les autres options vanilla des sélecteurs ne sont pas prises en charge par l’espace réservé côté client.

Exemple :

```text
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@e[type=minecraft:zombie,sort=nearest,limit=1,distance=..20]","nbt_path":"Health"}}
```

## Types de retour

| Type | Résultat |
|---|---|
| `value` | Les balises numériques sont formatées numériquement et utilisent `scale` ; les balises de type chaîne renvoient leur texte ; les autres balises renvoient un texte de type SNBT |
| `string` | Renvoie la valeur chaîne de la balise, ou une chaîne vide si la balise n’a pas de valeur chaîne |
| `snbt` | Renvoie la représentation SNBT de la balise |
| `json` | Pour les balises compound uniquement : renvoie un composant de texte Minecraft sérialisé contenant un affichage NBT lisible |

Le mode `json` côté client n’est pas une conversion directe de NBT en JSON.

## Exemples

Faim du joueur :

```text
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"foodLevel"}}
```

ID du premier objet de la barre d’accès rapide :

```text
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Inventory[{Slot:0b}].id","return_type":"string"}}
```

Nombre d’objets d’une entité de bloc :

```text
{"placeholder":"nbt_data_get","values":{"source_type":"block","block_pos":"100 64 -200","nbt_path":"Items[0].count"}}
```

# Espace réservé côté serveur

`nbt_data_get_server` suit le comportement de `/data get` côté serveur et prend en charge :

- Les sélecteurs d’entités complets côté serveur.
- Les cibles de blocs avec des coordonnées absolues, relatives (`~`) ou locales (`^`).
- Le stockage de commandes via `source_type:"storage"`.

```text
{"placeholder":"nbt_data_get_server","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Health","return_type":"value"}}
```

L’espace réservé renvoie une valeur vide jusqu’à l’arrivée de la réponse du serveur. Les réponses sont mises en cache brièvement pour éviter des requêtes excessives.

# Trouver des chemins NBT

Utilisez la commande correspondante sans chemin NBT pour inspecter les données disponibles :

```text
/data get entity @s
/data get block 100 64 -200
```

Les résultats côté client sont limités aux données synchronisées avec le client. Les cibles ou chemins invalides renvoient une chaîne vide et écrivent des détails dans `logs/latest.log`.
