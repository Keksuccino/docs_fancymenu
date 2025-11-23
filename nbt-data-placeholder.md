---
title: NBT Data Placeholder
description: How to use the NBT Data placeholder.
published: true
date: 2025-11-23T10:14:30.490Z
tags: 
editor: markdown
dateCreated: 2025-06-30T21:10:15.683Z
---


# Getting NBT Data

These placeholders are available in FancyMenu v3.8.0+.

The **Client NBT Data Get** and **Server NBT Data Get** placeholders allows you to retrieve NBT (Named Binary Tag) data from entities and blocks in Minecraft, similar to the `/data get` command. This is extremely useful for creating dynamic layouts that respond to game state, player stats, or world conditions.

> This placeholder is particularly powerful for modded gameplay, as it can access custom NBT data that mods add to entities and players. Whether you're playing with magic mods that add mana systems, RPG mods with custom stats, or technology mods with energy values, you can display these modded values in your UI layouts.
{.is-info}

## Overview

These placeholders extracts specific values from NBT data structures using NBT paths. You can retrieve player health, hunger, inventory items, block states, modded attributes like mana or energy, and much more.

The client-side version of the placeholder has the big advantage that it works purely client-side, so you don't need FancyMenu on the server, but this also makes it a lot more limited, because not everything related to NBT data is visible to all clients all the time.

The server-side version requires FancyMenu to be installed on the server, but this gives it **full support** for basically **everything** that is stored as NBT.

This page will focus on the client-side version (`nbt_data_get`), but everything works very similar for the server-side version (`nbt_data_get_server`) too.

## Placeholder Syntax

```
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Health"}}
```

## Required Values

| Value | Description | Options |
|-------|-------------|---------|
| `source_type` | The type of data source | `entity` or `block` |
| `nbt_path` | The NBT path to query | e.g. `Health`, `foodLevel`, `Pos[0]`, `Inventory[0].id` |

## Conditional Values

Depending on your `source_type`, you'll need one of these:

| Value | Required When | Description | Format |
|-------|--------------|-------------|--------|
| `entity_selector` | source_type is `entity` | Selects which entity to query | `@s` (self), `@p` (nearest player), `@e` (nearest entity), UUID, or entity name |
| `block_pos` | source_type is `block` | The block's coordinates | `x y z` (e.g. `100 64 -200`) |

## Optional Values

| Value | Description | Default | Options |
|-------|-------------|---------|---------|
| `scale` | Scale factor for numeric values | `1.0` | Any decimal number |
| `return_type` | How to format the returned data | `value` | `value` (numeric/size), `string` (text), `snbt` (formatted NBT), `json` (JSON format) |

## Return Types Explained

- **`value`** - Returns numeric values or sizes (default)
  - For numbers: returns the number (optionally scaled)
  - For strings: returns the string length
  - For lists/arrays: returns the item count
  - For compounds: returns the number of tags

- **`string`** - Returns the actual string value of the NBT data

- **`snbt`** - Returns the data in SNBT (Stringified NBT) format

- **`json`** - Returns the data in JSON format (only for compound tags)

## Examples

### Get Player Health
```json
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Health"}}
```

### Get Player Hunger Level
```json
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"foodLevel"}}
```

### Get Player X Coordinate
```json
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Pos[0]"}}
```

### Get Item in First Hotbar Slot
```json
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Inventory[{Slot:0b}].id","return_type":"string"}}
```

### Get Block Data at Specific Position
```json
{"placeholder":"nbt_data_get","values":{"source_type":"block","block_pos":"100 64 -200","nbt_path":"Items[0].Count"}}
```

### Get Scaled Health Percentage (Health * 5)
```json
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Health","scale":"5"}}
```

## Finding Available NBT Paths

### Method 1: Using `/data get` Command (Recommended)

The easiest way to discover available NBT paths is to use the `/data get` command in-game without specifying a path:

1. **For entities:** `/data get entity @p`
2. **For blocks:** `/data get block <x> <y> <z>`

This will display all available NBT data for that target, showing you the exact paths you can use.

#### Understanding the Output

When you run `/data get entity @p`, you'll see output similar to this:

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

To extract a valid path from this output:

1. **Simple values** - Use the key name directly:
   - `Health: 20.0f` → Path: `Health`
   - Example: `{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Health"}}`

2. **Nested values** - Use dot notation to access nested data:
   - `abilities: {walkSpeed: 0.1f}` → Path: `abilities.walkSpeed`
   - Example: `{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"abilities.walkSpeed"}}`

3. **Array values** - Use brackets with index numbers:
   - `Motion: [0.0d, 0.0d, 0.0d]` → Path for Y motion: `Motion[1]`
   - Example: `{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Motion[1]"}}`

### Method 2: NBT Autocomplete Mod

For easier NBT path discovery, consider installing the **NBT Autocomplete** mod:
- Available for Fabric and Forge (Minecraft 1.21.x)
- Provides in-game autocomplete suggestions while typing commands
- Shows available tag names and types
- [Modrinth](https://modrinth.com/mod/nbt-autocomplete) | [CurseForge](https://www.curseforge.com/minecraft/mc-mods/nbt-autocomplete)

## Common NBT Paths

### Player Entity
- `Health` - Current health (float)
- `foodLevel` - Hunger level (int, 0-20)
- `foodSaturationLevel` - Saturation level (float)
- `XpLevel` - Experience level (int)
- `XpP` - Experience progress (float, 0.0-1.0)
- `Pos[0]`, `Pos[1]`, `Pos[2]` - X, Y, Z coordinates
- `Inventory` - Player inventory array
- `SelectedItemSlot` - Currently selected hotbar slot (int, 0-8)

### Common Block NBT
- `Items` - Container contents (chests, furnaces, etc.)
- `CustomName` - Custom name of the block
- `Lock` - Lock string for containers

### Common Modded NBT Examples
- **Magic mods**: Often store mana as `playerMana`, `mana.current`, or similar
- **Tech mods**: Energy values like `energy`, `forgeEnergy`, or `energyStorage.energy`
- **RPG mods**: Custom stats like `customStats.strength`, `rpgAttributes.level`

To find modded NBT paths, use `/data get entity @p` while the mod is active and look for the custom tags added by the mod.

## Limitations

- **Client-side only** - Can only access data available to the client
- **No storage access** - Storage data source is not supported (server-side only)
- **Performance** - Accessing NBT data frequently may impact performance
- Returns empty string if the path is invalid or data cannot be accessed

## Tips

1. Always test your NBT paths in-game first using `/data get`
2. Use the `scale` parameter to convert values to percentages or other useful formats
3. Remember that some NBT data may not be synchronized to the client
4. Entity selectors are limited to entities within render distance
5. For modded content, check the mod's documentation or use `/data get` to discover custom NBT paths