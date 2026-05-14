---
title: NBT 数据占位符
description: 如何使用 NBT 数据占位符。
---


# 获取 NBT 数据

这些占位符可在 FancyMenu v3.8.0+ 中使用。

**客户端 NBT 数据获取** 和 **服务器 NBT 数据获取** 占位符允许你从 Minecraft 中的实体和方块检索 NBT（命名二进制标签）数据，类似于 `/data get` 命令。这对于创建会响应游戏状态、玩家属性或世界条件的动态布局非常有用。

> 这个占位符在模组化玩法中尤其强大，因为它可以访问模组添加到实体和玩家上的自定义 NBT 数据。无论你是在使用添加法力系统的魔法模组、带有自定义属性的 RPG 模组，还是具有能量值的科技模组，你都可以在 UI 布局中显示这些模组化数值。
{.is-info}

## 概览

这些占位符使用 NBT 路径从 NBT 数据结构中提取特定值。你可以检索玩家生命值、饥饿值、物品栏内容、方块状态、法力或能量等模组属性，以及更多内容。

占位符的客户端版本有一个很大的优势：它完全在客户端运行，因此服务器上不需要安装 FancyMenu；但这也使它受限很多，因为并不是所有与 NBT 数据相关的内容都会一直对所有客户端可见。

服务器版本要求在服务器上安装 FancyMenu，但这也让它对几乎**所有**以 NBT 形式存储的数据都具有**完整支持**。

本页将重点介绍客户端版本（`nbt_data_get`），但服务器版本（`nbt_data_get_server`）的工作方式也非常相似。

## 占位符语法

```
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Health"}}
```

## 必需值

| 值 | 说明 | 选项 |
|-------|-------------|---------|
| `source_type` | 数据来源类型 | `entity` 或 `block` |
| `nbt_path` | 要查询的 NBT 路径 | 例如 `Health`、`foodLevel`、`Pos[0]`、`Inventory[0].id` |

## 条件值

根据你的 `source_type`，你需要以下其中一个：

| 值 | 何时必需 | 说明 | 格式 |
|-------|--------------|---------|--------|
| `entity_selector` | `source_type` 为 `entity` 时 | 选择要查询的实体 | `@s`（自己）、`@p`（最近的玩家）、`@e`（最近的实体）、UUID 或实体名称 |
| `block_pos` | `source_type` 为 `block` 时 | 方块坐标 | `x y z`（例如 `100 64 -200`） |

## 可选值

| 值 | 说明 | 默认值 | 选项 |
|-------|-------------|---------|---------|
| `scale` | 数值的缩放因子 | `1.0` | 任意小数 |
| `return_type` | 返回数据的格式 | `value` | `value`（数值/数量）、`string`（文本）、`snbt`（格式化的 NBT）、`json`（JSON 格式） |

## 返回类型说明

- **`value`** - 返回数值或数量（默认）
  - 对于数字：返回该数值（可选缩放）
  - 对于字符串：返回字符串长度
  - 对于列表/数组：返回项目数量
  - 对于复合标签：返回标签数量

- **`string`** - 返回 NBT 数据的实际字符串值

- **`snbt`** - 以 SNBT（字符串化 NBT）格式返回数据

- **`json`** - 以 JSON 格式返回数据（仅适用于复合标签）

## 示例

### 获取玩家生命值
```json
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Health"}}
```

### 获取玩家饥饿值
```json
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"foodLevel"}}
```

### 获取玩家 X 坐标
```json
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Pos[0]"}}
```

### 获取热键栏第一个槽位中的物品
```json
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Inventory[{Slot:0b}].id","return_type":"string"}}
```

### 获取特定位置的方块数据
```json
{"placeholder":"nbt_data_get","values":{"source_type":"block","block_pos":"100 64 -200","nbt_path":"Items[0].Count"}}
```

### 获取缩放后的生命值百分比（Health * 5）
```json
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Health","scale":"5"}}
```

## 查找可用的 NBT 路径

### 方法 1：使用 `/data get` 命令（推荐）

发现可用 NBT 路径最简单的方法是在游戏中直接使用 `/data get` 命令而不指定路径：

1. **对于实体：** `/data get entity @p`
2. **对于方块：** `/data get block <x> <y> <z>`

这会显示该目标所有可用的 NBT 数据，让你看到可以使用的准确路径。

#### 理解输出内容

当你运行 `/data get entity @p` 时，你会看到类似这样的输出：

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

要从这个输出中提取有效路径：

1. **简单值** - 直接使用键名：
   - `Health: 20.0f` → 路径：`Health`
   - 示例：`{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Health"}}`

2. **嵌套值** - 使用点号表示法访问嵌套数据：
   - `abilities: {walkSpeed: 0.1f}` → 路径：`abilities.walkSpeed`
   - 示例：`{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"abilities.walkSpeed"}}`

3. **数组值** - 使用带索引编号的方括号：
   - `Motion: [0.0d, 0.0d, 0.0d]` → Y 方向运动路径：`Motion[1]`
   - 示例：`{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Motion[1]"}}`

### 方法 2：NBT 自动补全模组

为了更轻松地发现 NBT 路径，可以考虑安装 **NBT Autocomplete** 模组：
- 支持 Fabric 和 Forge（Minecraft 1.21.x）
- 在输入命令时提供游戏内自动补全建议
- 显示可用的标签名称和类型
- [Modrinth](https://modrinth.com/mod/nbt-autocomplete) | [CurseForge](https://www.curseforge.com/minecraft/mc-mods/nbt-autocomplete)

## 常见 NBT 路径

### 玩家实体
- `Health` - 当前生命值（float）
- `foodLevel` - 饥饿值（int，0-20）
- `foodSaturationLevel` - 饱和度（float）
- `XpLevel` - 经验等级（int）
- `XpP` - 经验进度（float，0.0-1.0）
- `Pos[0]`、`Pos[1]`、`Pos[2]` - X、Y、Z 坐标
- `Inventory` - 玩家物品栏数组
- `SelectedItemSlot` - 当前选中的热键栏槽位（int，0-8）

### 常见方块 NBT
- `Items` - 容器内容（箱子、熔炉等）
- `CustomName` - 方块的自定义名称
- `Lock` - 容器的锁定字符串

### 常见模组化 NBT 示例
- **魔法模组**：通常将法力存储为 `playerMana`、`mana.current` 或类似名称
- **科技模组**：能量值，如 `energy`、`forgeEnergy` 或 `energyStorage.energy`
- **RPG 模组**：自定义属性，如 `customStats.strength`、`rpgAttributes.level`

要查找模组化 NBT 路径，请在模组启用时使用 `/data get entity @p`，并查看模组添加的自定义标签。

## 限制

- **客户端无法访问存储** - 客户端不支持 storage 数据源（仅服务器端可用）
- **性能** - 频繁访问 NBT 数据可能会影响性能
- 如果路径无效或无法访问数据，则返回空字符串

## 提示

1. 始终先在游戏中使用 `/data get` 测试你的 NBT 路径
2. 使用 `scale` 参数将数值转换为百分比或其他有用格式
3. 记住某些 NBT 数据可能不会同步到客户端
4. 实体选择器仅限于渲染距离内的实体
5. 对于模组内容，请查阅模组文档，或使用 `/data get` 发现自定义 NBT 路径
