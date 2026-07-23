---
title: NBT Data Placeholder
description: Read entity, block, and storage NBT data.
published: true
date: 2025-11-23T10:15:53.194Z
tags:
editor: markdown
dateCreated: 2025-06-30T21:10:15.683Z
---

# NBT Data Placeholders

FancyMenu provides two NBT placeholders:

| Placeholder | Runs on | Available data |
|---|---|---|
| `nbt_data_get` | Client | Client-visible entities and block entities |
| `nbt_data_get_server` | Server | Vanilla `/data get` targets; requires FancyMenu on the server |

# Client-Side Placeholder

```text
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Health"}}
```

## Values

| Value | Required | Description |
|---|---|---|
| `source_type` | Yes | `entity` or `block` |
| `entity_selector` | For entities | Client-side selector, UUID, or exact entity name |
| `block_pos` | For blocks | Three absolute integer coordinates, such as `100 64 -200` |
| `nbt_path` | Yes | NBT path, such as `Health`, `Pos[0]`, or `Inventory[0].id` |
| `scale` | No | Multiplies numeric `value` results; default `1.0` |
| `return_type` | No | `value`, `string`, `snbt`, or `json`; default `value` |

Client-side block positions do not support `~` or `^` coordinates.

## Client Entity Selectors

| Selector | Initial targets | Default order |
|---|---|---|
| `@s` | Local player | Self |
| `@p` | Players | Nearest |
| `@a` | Players | Client iteration order |
| `@r` | Players | Random |
| `@e` | All client-visible entities | Client iteration order |

`@e` does not select the nearest entity unless you add `sort=nearest`. Direct UUID and exact entity-name lookup are also supported.

Supported selector options:

| Option | Description |
|---|---|
| `type` | Entity ID; prefix with `!` to exclude |
| `name` | Exact display name; prefix with `!` to exclude |
| `tag` | Entity tag; prefix with `!` to exclude |
| `limit` | Positive result limit |
| `sort` | `nearest`, `furthest`, `random`, or `arbitrary` |
| `distance` | Vanilla distance range, such as `..10` or `5..20` |
| `x`, `y`, `z` | Search origin; accepts absolute values and `~` offsets |
| `dx`, `dy`, `dz` | Search-box size from the origin |

Local `^` coordinates and other vanilla selector options are not supported by the client placeholder.

Example:

```text
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@e[type=minecraft:zombie,sort=nearest,limit=1,distance=..20]","nbt_path":"Health"}}
```

## Return Types

| Type | Result |
|---|---|
| `value` | Numeric tags are formatted numerically and apply `scale`; string tags return their text; other tags return SNBT-like text |
| `string` | Returns the tag's string value, or an empty string when the tag has no string value |
| `snbt` | Returns the tag's SNBT representation |
| `json` | For compound tags only: returns a serialized Minecraft text component containing pretty NBT output |

The client-side `json` mode is not a direct NBT-to-JSON conversion.

## Examples

Player hunger:

```text
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"foodLevel"}}
```

First hotbar item ID:

```text
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Inventory[{Slot:0b}].id","return_type":"string"}}
```

Block-entity item count:

```text
{"placeholder":"nbt_data_get","values":{"source_type":"block","block_pos":"100 64 -200","nbt_path":"Items[0].count"}}
```

# Server-Side Placeholder

`nbt_data_get_server` follows the server's `/data get` behavior and supports:

- Full server-side entity selectors.
- Block targets with absolute, relative (`~`), or local (`^`) coordinates.
- Command storage through `source_type:"storage"`.

```text
{"placeholder":"nbt_data_get_server","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Health","return_type":"value"}}
```

The placeholder returns an empty value until the server response arrives. Responses are briefly cached to avoid excessive requests.

# Finding NBT Paths

Use the matching command without an NBT path to inspect available data:

```text
/data get entity @s
/data get block 100 64 -200
```

Client-side results are limited to data synchronized to the client. Invalid targets or paths return an empty string and write details to `logs/latest.log`.
