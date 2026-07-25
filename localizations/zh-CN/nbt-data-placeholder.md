---
title: NBT 数据占位符
description: 读取实体、方块和存储的 NBT 数据。
---
# NBT 数据占位符

FancyMenu 提供两个 NBT 占位符：

| 占位符 | 运行位置 | 可用数据 |
|---|---|---|
| `nbt_data_get` | 客户端 | 客户端可见的实体和方块实体 |
| `nbt_data_get_server` | 服务端 | 原版 `/data get` 目标；需要服务端安装 FancyMenu |

# 客户端占位符

```text
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Health"}}
```

## 值

| 值 | 必填 | 描述 |
|---|---|---|
| `source_type` | 是 | `entity` 或 `block` |
| `entity_selector` | 实体时需要 | 客户端选择器、UUID，或精确实体名称 |
| `block_pos` | 方块时需要 | 三个绝对整数坐标，例如 `100 64 -200` |
| `nbt_path` | 是 | NBT 路径，例如 `Health`、`Pos[0]` 或 `Inventory[0].id` |
| `scale` | 否 | 乘以数值类型 `value` 结果；默认 `1.0` |
| `return_type` | 否 | `value`、`string`、`snbt` 或 `json`；默认 `value` |

客户端方块位置不支持 `~` 或 `^` 坐标。

## 客户端实体选择器

| 选择器 | 初始目标 | 默认顺序 |
|---|---|---|
| `@s` | 本地玩家 | 自身 |
| `@p` | 玩家 | 最近 |
| `@a` | 玩家 | 客户端迭代顺序 |
| `@r` | 玩家 | 随机 |
| `@e` | 所有客户端可见实体 | 客户端迭代顺序 |

`@e` 不会选择最近的实体，除非你添加 `sort=nearest`。也支持直接按 UUID 和精确实体名称查找。

支持的选择器选项：

| 选项 | 描述 |
|---|---|
| `type` | 实体 ID；前缀 `!` 可排除 |
| `name` | 精确显示名称；前缀 `!` 可排除 |
| `tag` | 实体标签；前缀 `!` 可排除 |
| `limit` | 正结果上限 |
| `sort` | `nearest`、`furthest`、`random` 或 `arbitrary` |
| `distance` | 原版距离范围，例如 `..10` 或 `5..20` |
| `x`, `y`, `z` | 搜索原点；支持绝对值和 `~` 偏移 |
| `dx`, `dy`, `dz` | 从原点开始的搜索框大小 |

客户端占位符不支持本地 `^` 坐标和其他原版选择器选项。

示例：

```text
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@e[type=minecraft:zombie,sort=nearest,limit=1,distance=..20]","nbt_path":"Health"}}
```

## 返回类型

| 类型 | 结果 |
|---|---|
| `value` | 数值标签会按数值格式返回并应用 `scale`；字符串标签返回其文本；其他标签返回类似 SNBT 的文本 |
| `string` | 返回标签的字符串值；如果标签没有字符串值，则返回空字符串 |
| `snbt` | 返回标签的 SNBT 表示 |
| `json` | 仅适用于复合标签：返回一个序列化的 Minecraft 文本组件，其中包含格式化后的 NBT 输出 |

客户端的 `json` 模式不是直接的 NBT 到 JSON 转换。

## 示例

玩家饥饿值：

```text
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"foodLevel"}}
```

快捷栏第一个物品的 ID：

```text
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Inventory[{Slot:0b}].id","return_type":"string"}}
```

方块实体物品数量：

```text
{"placeholder":"nbt_data_get","values":{"source_type":"block","block_pos":"100 64 -200","nbt_path":"Items[0].count"}}
```

# 服务端占位符

`nbt_data_get_server` 遵循服务端的 `/data get` 行为，并支持：

- 完整的服务端实体选择器。
- 方块目标支持绝对坐标、相对坐标（`~`）或本地坐标（`^`）。
- 通过 `source_type:"storage"` 访问命令存储。

```text
{"placeholder":"nbt_data_get_server","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Health","return_type":"value"}}
```

在服务端响应到达之前，占位符会返回空值。为避免过多请求，响应会被短暂缓存。

# 查找 NBT 路径

使用对应命令并省略 NBT 路径，以查看可用数据：

```text
/data get entity @s
/data get block 100 64 -200
```

客户端结果仅限于已同步到客户端的数据。无效的目标或路径会返回空字符串，并将详细信息写入 `logs/latest.log`。
