---
title: Espace réservé aux données NBT
description: Comment utiliser l'espace réservé aux données NBT.
---


# Obtenir des données NBT

Ces espaces réservés sont disponibles dans FancyMenu v3.8.0+.

Les espaces réservés **Client NBT Data Get** et **Server NBT Data Get** vous permettent de récupérer des données NBT (Named Binary Tag) depuis des entités et des blocs dans Minecraft, de manière similaire à la commande `/data get`. C’est extrêmement utile pour créer des interfaces dynamiques qui réagissent à l’état du jeu, aux statistiques du joueur ou aux conditions du monde.

> Cet espace réservé est particulièrement puissant pour le jeu moddé, car il peut accéder aux données NBT personnalisées que les mods ajoutent aux entités et aux joueurs. Que vous jouiez avec des mods de magie qui ajoutent des systèmes de mana, des mods RPG avec des statistiques personnalisées, ou des mods de technologie avec des valeurs d’énergie, vous pouvez afficher ces valeurs modifiées dans vos interfaces.
{.is-info}

## Vue d’ensemble

Ces espaces réservés extraient des valeurs spécifiques à partir de structures de données NBT à l’aide de chemins NBT. Vous pouvez récupérer la santé du joueur, la faim, les objets de l’inventaire, les états de blocs, des attributs moddés comme le mana ou l’énergie, et bien plus encore.

La version côté client de l’espace réservé a le grand avantage de fonctionner entièrement côté client, donc vous n’avez pas besoin de FancyMenu sur le serveur, mais cela la rend aussi beaucoup plus limitée, car tout ce qui est lié aux données NBT n’est pas visible par tous les clients en permanence.

La version côté serveur nécessite que FancyMenu soit installé sur le serveur, mais elle offre alors une **prise en charge complète** de pratiquement **tout** ce qui est stocké en NBT.

Cette page se concentre sur la version côté client (`nbt_data_get`), mais tout fonctionne de manière très similaire pour la version côté serveur (`nbt_data_get_server`) également.

## Syntaxe de l’espace réservé

```
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Health"}}
```

## Valeurs requises

| Valeur | Description | Options |
|-------|-------------|---------|
| `source_type` | Le type de source de données | `entity` ou `block` |
| `nbt_path` | Le chemin NBT à interroger | ex. `Health`, `foodLevel`, `Pos[0]`, `Inventory[0].id` |

## Valeurs conditionnelles

Selon votre `source_type`, vous aurez besoin de l’une de ces valeurs :

| Valeur | Requis lorsque | Description | Format |
|-------|--------------|-------------|--------|
| `entity_selector` | `source_type` est `entity` | Sélectionne l’entité à interroger | `@s` (soi-même), `@p` (joueur le plus proche), `@e` (entité la plus proche), UUID, ou nom d’entité |
| `block_pos` | `source_type` est `block` | Les coordonnées du bloc | `x y z` (ex. `100 64 -200`) |

## Valeurs facultatives

| Valeur | Description | Défaut | Options |
|-------|-------------|--------|---------|
| `scale` | Facteur d’échelle pour les valeurs numériques | `1.0` | N’importe quel nombre décimal |
| `return_type` | Formatage des données retournées | `value` | `value` (numérique/taille), `string` (texte), `snbt` (NBT formaté), `json` (format JSON) |

## Explication des types de retour

- **`value`** - Retourne des valeurs numériques ou des tailles (par défaut)
  - Pour les nombres : retourne le nombre (éventuellement mis à l’échelle)
  - Pour les chaînes : retourne la longueur de la chaîne
  - Pour les listes/tableaux : retourne le nombre d’éléments
  - Pour les compounds : retourne le nombre de tags

- **`string`** - Retourne la valeur de chaîne réelle des données NBT

- **`snbt`** - Retourne les données au format SNBT (Stringified NBT)

- **`json`** - Retourne les données au format JSON (uniquement pour les tags compound)

## Exemples

### Obtenir la santé du joueur
```json
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Health"}}
```

### Obtenir le niveau de faim du joueur
```json
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"foodLevel"}}
```

### Obtenir la coordonnée X du joueur
```json
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Pos[0]"}}
```

### Obtenir l’objet dans le premier emplacement de la barre rapide
```json
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Inventory[{Slot:0b}].id","return_type":"string"}}
```

### Obtenir les données d’un bloc à une position spécifique
```json
{"placeholder":"nbt_data_get","values":{"source_type":"block","block_pos":"100 64 -200","nbt_path":"Items[0].Count"}}
```

### Obtenir un pourcentage de santé mis à l’échelle (Health * 5)
```json
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Health","scale":"5"}}
```

## Trouver les chemins NBT disponibles

### Méthode 1 : utiliser la commande `/data get` (recommandé)

La manière la plus simple de découvrir les chemins NBT disponibles est d’utiliser la commande `/data get` en jeu sans spécifier de chemin :

1. **Pour les entités :** `/data get entity @p`
2. **Pour les blocs :** `/data get block <x> <y> <z>`

Cela affichera toutes les données NBT disponibles pour cette cible, en montrant les chemins exacts que vous pouvez utiliser.

#### Comprendre la sortie

Lorsque vous exécutez `/data get entity @p`, vous verrez une sortie similaire à celle-ci :

```
Player616 has the following entity data: {Brain: {memories: {}}, 
HurtByTimestamp: 0, SleepTimer: 0s, Invulnerable: 0b, FallFlying: 
0b, PortalCooldown: 0, AbsorptionAmount: 0.0f, abilities: 
{invulnerable: 1b, mayfly: 1b, instabuild: 1b, walkSpeed: 0.1f, 
mayBuild: 1b, flying: 1b, flySpeed: 0.05f}, FallDistance: 0.0f, 
recipeBook: {recipes: ["minecraft:crafting_table"]}, 
DeathTime: 0s, XpSeed: -380875747, XpTotal: 0, UUID: [I; 1379890089, -1732753738, 
-2135065633, -718799804], playerGameType: 1, seenCredits: 
0b, Motion: [0.0d, 0.0d, 0.0d], Health: 20.0f, foodSaturationLevel: 
5.0f, ...}
```

Pour extraire un chemin valide à partir de cette sortie :

1. **Valeurs simples** - Utilisez directement le nom de la clé :
   - `Health: 20.0f` → Chemin : `Health`
   - Exemple : `{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Health"}}`

2. **Valeurs imbriquées** - Utilisez la notation par points pour accéder aux données imbriquées :
   - `abilities: {walkSpeed: 0.1f}` → Chemin : `abilities.walkSpeed`
   - Exemple : `{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"abilities.walkSpeed"}}`

3. **Valeurs de tableau** - Utilisez des crochets avec des indices numériques :
   - `Motion: [0.0d, 0.0d, 0.0d]` → Chemin pour le mouvement Y : `Motion[1]`
   - Exemple : `{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Motion[1]"}}`

### Méthode 2 : mod NBT Autocomplete

Pour faciliter la découverte des chemins NBT, pensez à installer le mod **NBT Autocomplete** :
- Disponible pour Fabric et Forge (Minecraft 1.21.x)
- Fournit des suggestions d’autocomplétion en jeu أثناء la saisie des commandes
- Affiche les noms et types de tags disponibles
- [Modrinth](https://modrinth.com/mod/nbt-autocomplete) | [CurseForge](https://www.curseforge.com/minecraft/mc-mods/nbt-autocomplete)

## Chemins NBT courants

### Entité joueur
- `Health` - Santé actuelle (float)
- `foodLevel` - Niveau de faim (int, 0-20)
- `foodSaturationLevel` - Niveau de satiété (float)
- `XpLevel` - Niveau d’expérience (int)
- `XpP` - Progression d’expérience (float, 0.0-1.0)
- `Pos[0]`, `Pos[1]`, `Pos[2]` - Coordonnées X, Y, Z
- `Inventory` - Tableau de l’inventaire du joueur
- `SelectedItemSlot` - Emplacement de la barre rapide actuellement sélectionné (int, 0-8)

### NBT de bloc courant
- `Items` - Contenu du conteneur (coffres, fours, etc.)
- `CustomName` - Nom personnalisé du bloc
- `Lock` - Chaîne de verrouillage pour les conteneurs

### Exemples courants de NBT moddé
- **Mods de magie** : stockent souvent le mana comme `playerMana`, `mana.current` ou similaire
- **Mods techno** : valeurs d’énergie comme `energy`, `forgeEnergy` ou `energyStorage.energy`
- **Mods RPG** : statistiques personnalisées comme `customStats.strength`, `rpgAttributes.level`

Pour trouver les chemins NBT moddés, utilisez `/data get entity @p` pendant que le mod est actif et recherchez les tags personnalisés ajoutés par le mod.

## Limitations

- **Pas d’accès au stockage côté client** - La source de données de stockage n’est pas prise en charge côté client (serveur uniquement)
- **Performances** - L’accès fréquent aux données NBT peut affecter les performances
- Retourne une chaîne vide si le chemin est invalide ou si les données sont inaccessibles

## Conseils

1. Testez toujours d’abord vos chemins NBT en jeu avec `/data get`
2. Utilisez le paramètre `scale` pour convertir les valeurs en pourcentages ou dans d’autres formats utiles
3. N’oubliez pas que certaines données NBT peuvent ne pas être synchronisées avec le client
4. Les sélecteurs d’entités sont limités aux entités situées dans la distance de rendu
5. Pour le contenu moddé, consultez la documentation du mod ou utilisez `/data get` pour découvrir les chemins NBT personnalisés
