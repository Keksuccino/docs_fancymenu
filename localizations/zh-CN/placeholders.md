---
title: 占位符
description: 如何使用占位符。
---
# 占位符

占位符会将实时值插入到文本、按钮、需求以及其他受支持的字段中。

# 一般信息

## 基本语法
FancyMenu 中的占位符使用类似 JSON 的语法：
```
{"placeholder":"modversion","values":{"modid":"fancymenu"}}
```

例如，要显示玩家名称：
```
{"placeholder":"playername"}
```

## 嵌套占位符
你可以在一个占位符的值中使用另一个占位符。

嵌套占位符示例：
```
{"placeholder":"calc","values":{"decimal":"true","expression":"{"placeholder":"maxram"} / 1024"}}
```
这个示例会取最大内存值并除以 1024，以便从 MB 转换为 GB。

> [!IMPORTANT]
> 这不是标准 JSON，而是 FancyMenu 语法。嵌套占位符必须使用上面显示的未转义原始形式，因此 JSON 格式化工具会拒绝或重写它们。占位符名称区分大小写；格式错误或未知的占位符仍会作为文本显示，并会被记录。

# 使用占位符

大多数带有文本输入的元素都支持占位符。编辑时你可以查看该文本输入是否支持占位符。如果编辑文本时会打开全屏的 **文本编辑器**，就表示它支持占位符。

要查看 **所有占位符的列表**，只需点击 **文本编辑器** 右上角的 **占位符** 按钮。

占位符列表顶部有一个 **搜索栏**，可用于搜索占位符。

在占位符列表中点击某个占位符，会将其粘贴到文本内容中。

# 占位符详解

本节列出了 FancyMenu 的内置占位符。

## 不可用结果

占位符的输出始终是文本。当数据不可用时，结果取决于具体占位符：常见回退值为空字符串、`0`、`0.0`、`00:00`、`false`、`UNKNOWN` 或 `ERROR`。带有特定回退值的条目会直接注明；在将依赖环境的输出用于 [需求](./conditions)、路径、命令或 URL 之前，请先测试其回退行为。

## 玩家名称 (`playername`)

**用途：** 返回当前玩家的用户名。

**值：** 无

**示例：**

```
{"placeholder":"playername"}
```

**输出：** `Steve`

## 玩家 UUID (`playeruuid`)

**用途：** 返回玩家的唯一标识符。

**值：** 无

**示例：**

```
{"placeholder":"playeruuid"}
```

**输出：** `c8cde7fe-7ced-11eb-9439-0242ac130002`

## Minecraft 版本 (`mcversion`)

**用途：** 返回当前 Minecraft 版本。

**值：** 无

**示例：**

```
{"placeholder":"mcversion"}
```

**输出：** `1.21.1`

## 模组加载器版本 (`loaderver`)

**用途：** 返回模组加载器（Fabric/NeoForge）的版本。

**值：** 无

**示例：**

```
{"placeholder":"loaderver"}
```

**输出：** `0.16.14`

## 模组加载器名称 (`loadername`)

**用途：** 返回模组加载器的名称。

**值：** 无

**示例：**

```
{"placeholder":"loadername"}
```

**输出：** `Fabric`

## 模组版本 (`modversion`)

**用途：** 返回某个特定模组的版本。

**值：** `modid`

**示例：**

```
{"placeholder":"modversion","values":{"modid":"example_mod"}}
```

**输出：** `1.2.3`

## 模组总数 (`totalmods`)

**用途：** 根据 `mods` 目录和已加载模组数量返回一个大致的模组文件计数。它不能可靠地统计每一个被禁用的模组。

**值：** 无

**示例：**

```
{"placeholder":"totalmods"}
```

**输出：** `45`

## 活动模组数量 (`loadedmods`)

**用途：** 返回当前已加载的模组数量。

**值：** 无

**示例：**

```
{"placeholder":"loadedmods"}
```

**输出：** `43`

## 世界加载进度 (`world_load_progress`)

**用途：** 返回当前世界加载进度百分比。

**值：** 无

**示例：**

```
{"placeholder":"world_load_progress"}
```

**输出：** `75`

## Minecraft 选项值 (`minecraft_option_value`)

**用途：** 返回某个 Minecraft 选项的值。

**值：** `name`

**示例：**

```
{"placeholder":"minecraft_option_value","values":{"name":"fov"}}
```

**输出：** `70`

## 上一个世界或服务器 (`last_world_server`)

**用途：** 返回最近访问的世界或服务器的信息。

**值：** `type`, `full_world_path`

**示例：**

```
{"placeholder":"last_world_server","values":{"type":"both","full_world_path":"true"}}
```
参数：
- `type`：决定返回哪种类型的信息
  - `"both"`：返回最近访问的世界或服务器（默认）
  - `"server"`：仅当最近访问的是服务器时返回
  - `"world"`：仅当最近访问的是世界时返回
- `full_world_path`：控制世界路径的显示方式
  - `"true"`：返回完整世界路径（默认）
  - `"false"`：仅返回世界名称，不包含路径（不影响服务器）

示例：
- 服务器：`mc.hypixel.net`
- 带完整路径的世界：`saves/New World`
- 不带完整路径的世界：`New World`

## 屏幕宽度 (`guiwidth`)

**用途：** 返回当前屏幕宽度，单位为 GUI 缩放后的像素，而不是物理显示器像素。

**值：** 无

**示例：**

```
{"placeholder":"guiwidth"}
```

**输出：** `960`

## 屏幕高度 (`guiheight`)

**用途：** 返回当前屏幕高度，单位为 GUI 缩放后的像素，而不是物理显示器像素。

**值：** 无

**示例：**

```
{"placeholder":"guiheight"}
```

**输出：** `540`

## 当前屏幕标识符 (`screenid`)

**用途：** 返回当前屏幕的标识符。

**值：** 无

**示例：**

```
{"placeholder":"screenid"}
```

**输出：** `title_screen`

## 元素宽度 (`elementwidth`)

**用途：** 返回某个特定元素的宽度。

**值：** `id`

**示例：**

```
{"placeholder":"elementwidth","values":{"id":"my_button"}}
```

**输出：** `200`

## 元素高度 (`elementheight`)

**用途：** 返回某个特定元素的高度。

**值：** `id`

**示例：**

```
{"placeholder":"elementheight","values":{"id":"my_button"}}
```

**输出：** `20`

## 元素 X 坐标 (`elementposx`)

**用途：** 返回某个特定元素的 X 坐标。

**值：** `id`

**示例：**

```
{"placeholder":"elementposx","values":{"id":"my_button"}}
```

**输出：** `150`

## 元素 Y 坐标 (`elementposy`)

**用途：** 返回某个特定元素的 Y 坐标。

**值：** `id`

**示例：**

```
{"placeholder":"elementposy","values":{"id":"my_button"}}
```

**输出：** `100`

## 鼠标 X 坐标 (`mouseposx`)

**用途：** 返回当前鼠标的 X 坐标。

**值：** 无

**示例：**

```
{"placeholder":"mouseposx"}
```

**输出：** `960`

## 鼠标 Y 坐标 (`mouseposy`)

**用途：** 返回当前鼠标的 Y 坐标。

**值：** 无

**示例：**

```
{"placeholder":"mouseposy"}
```

**输出：** `540`

## 每秒点击次数 (`clicks_per_second`)

**用途：** 返回鼠标按键当前的每秒点击次数。

**值：** `mouse_button`

**示例：**

```
{"placeholder":"clicks_per_second","values":{"mouse_button":"left"}}
```
参数：
- `mouse_button`：`left` 或 `right`

**输出：** `8`

## GUI 缩放 (`guiscale`)

**用途：** 返回当前 GUI 缩放。

**值：** 无

**示例：**

```
{"placeholder":"guiscale"}
```

**输出：** `2`

## 原版控件标签/文本 (`vanillabuttonlabel`)

**用途：** 返回原版控件/按钮的标签或文本。

**值：** `locator`

**示例：**

```
{"placeholder":"vanillabuttonlabel","values":{"locator":"some.menu.identifier:505280"}}
```

**输出：** `Options...`

## 文本输入字段值 (`text_input_field_value`)

**用途：** 通过元素标识符返回自定义或原版文本输入字段的当前值。

**值：** `element_identifier`

**示例：**

```
{"placeholder":"text_input_field_value","values":{"element_identifier":"my_input"}}
```

**输出：** `Hello World`

## 当前玩家生命值 (`current_player_health`)

**用途：** 返回玩家当前生命值。

**值：** 无

**示例：**

```
{"placeholder":"current_player_health"}
```

**输出：** `20.0`

## 玩家最大生命值 (`max_player_health`)

**用途：** 返回玩家的最大生命值。

**值：** 无

**示例：**

```
{"placeholder":"max_player_health"}
```

**输出：** `20.0`

## 当前玩家生命值（百分比） (`current_player_health_percent`)

**用途：** 返回玩家当前生命值的百分比。

**值：** 无

**示例：**

```
{"placeholder":"current_player_health_percent"}
```

**输出：** `100`

## 当前玩家吸收生命值 (`current_player_absorption_health`)

**用途：** 返回玩家的吸收生命值（金色心）。

**值：** 无

**示例：**

```
{"placeholder":"current_player_absorption_health"}
```

**输出：** `4.0`

## 玩家最大吸收生命值 (`max_player_absorption_health`)

**用途：** 返回最大吸收生命值。

**值：** 无

**示例：**

```
{"placeholder":"max_player_absorption_health"}
```

**输出：** `4.0`

## 当前玩家吸收生命值（百分比） (`current_player_absorption_health_percent`)

**用途：** 返回玩家吸收生命值的百分比。

**值：** 无

**示例：**

```
{"placeholder":"current_player_absorption_health_percent"}
```

**输出：** `100`

## 当前玩家饥饿值 (`current_player_hunger`)

**用途：** 返回玩家当前饥饿值。

**值：** 无

**示例：**

```
{"placeholder":"current_player_hunger"}
```

**输出：** `20`

## 玩家最大饥饿值 (`max_player_hunger`)

**用途：** 返回最大饥饿值。

**值：** 无

**示例：**

```
{"placeholder":"max_player_hunger"}
```

**输出：** `20`

## 当前玩家饥饿值（百分比） (`current_player_hunger_percent`)

**用途：** 返回玩家饥饿值的百分比。

**值：** 无

**示例：**

```
{"placeholder":"current_player_hunger_percent"}
```

**输出：** `100`

## 当前玩家饥饿饱和度 (`current_player_hunger_saturation`)

**用途：** 返回玩家当前饥饿饱和度值。

**值：** 无

**示例：**

```
{"placeholder":"current_player_hunger_saturation"}
```

**输出：** `5.0`

## 当前玩家护甲值 (`current_player_armor`)

**用途：** 返回玩家当前护甲值。

**值：** 无

**示例：**

```
{"placeholder":"current_player_armor"}
```

**输出：** `20`

## 玩家护甲韧性 (`player_armor_toughness`)

**用途：** 返回玩家总护甲韧性值。

**值：** 无

**示例：**

```
{"placeholder":"player_armor_toughness"}
```

**输出：** `8.0`

## 玩家最大护甲值 (`max_player_armor`)

**用途：** 返回最大护甲值。

**值：** 无

**示例：**

```
{"placeholder":"max_player_armor"}
```

**输出：** `20`

## 当前玩家护甲值（百分比） (`current_player_armor_percent`)

**用途：** 返回玩家护甲值的百分比。

**值：** 无

**示例：**

```
{"placeholder":"current_player_armor_percent"}
```

**输出：** `100`

## 当前玩家氧气值 (`current_player_oxygen`)

**用途：** 返回玩家当前氧气值（气泡数）。

**值：** 无

**示例：**

```
{"placeholder":"current_player_oxygen"}
```

**输出：** `300`

## 玩家最大氧气值 (`max_player_oxygen`)

**用途：** 返回最大氧气值。

**值：** 无

**示例：**

```
{"placeholder":"max_player_oxygen"}
```

**输出：** `300`

## 当前玩家氧气值（百分比） (`current_player_oxygen_percent`)

**用途：** 返回玩家氧气值的百分比。

**值：** 无

**示例：**

```
{"placeholder":"current_player_oxygen_percent"}
```

**输出：** `100`

## 当前玩家等级 (`current_player_level`)

**用途：** 返回玩家当前经验等级。

**值：** 无

**示例：**

```
{"placeholder":"current_player_level"}
```

**输出：** `30`

## 当前玩家经验值 (`current_player_exp`)

**用途：** 返回玩家总经验值。

**值：** 无

**示例：**

```
{"placeholder":"current_player_exp"}
```

**输出：** `1250`

## 玩家经验进度（百分比） (`current_player_exp_progress`)

**用途：** 返回玩家到下一等级的经验进度百分比。

**值：** 无

**示例：**

```
{"placeholder":"current_player_exp_progress"}
```

**输出：** `75`

## 玩家攻击强度（百分比） (`player_attack_strength`)

**用途：** 返回玩家攻击冷却进度的百分比。

**值：** 无

**示例：**

```
{"placeholder":"player_attack_strength"}
```

**输出：** `100`

## 玩家游戏模式 (`player_gamemode`)

**用途：** 返回玩家当前游戏模式。

**值：** 无

**示例：**

```
{"placeholder":"player_gamemode"}
```

**输出：** `survival`

## 玩家视线方向 (`player_view_direction`)

**用途：** 返回玩家当前面朝的方向。

**值：** 无

**示例：**

```
{"placeholder":"player_view_direction"}
```

**输出：** `north`

## 玩家 X 坐标 (`player_x_coordinate`)

**用途：** 返回玩家在世界中的 X 坐标。

**值：** 无

**示例：**

```
{"placeholder":"player_x_coordinate"}
```

**输出：** `125`

## 玩家 Y 坐标 (`player_y_coordinate`)

**用途：** 返回玩家在世界中的 Y 坐标。

**值：** 无

**示例：**

```
{"placeholder":"player_y_coordinate"}
```

**输出：** `64`

## 玩家 Z 坐标 (`player_z_coordinate`)

**用途：** 返回玩家在世界中的 Z 坐标。

**值：** 无

**示例：**

```
{"placeholder":"player_z_coordinate"}
```

**输出：** `-250`

## 当前坐骑生命值 (`current_mount_health`)

**用途：** 返回玩家所骑乘实体的当前生命值。

**值：** 无

**示例：**

```
{"placeholder":"current_mount_health"}
```

**输出：** `30.0`

## 坐骑最大生命值 (`max_mount_health`)

**用途：** 返回玩家所骑乘实体的最大生命值。

**值：** 无

**示例：**

```
{"placeholder":"max_mount_health"}
```

**输出：** `30.0`

## 当前坐骑生命值（百分比） (`current_mount_health_percent`)

**用途：** 返回坐骑生命值的百分比。

**值：** 无

**示例：**

```
{"placeholder":"current_mount_health_percent"}
```

**输出：** `100`

## 当前坐骑跳跃条（百分比） (`current_mount_jump_meter`)

**用途：** 返回坐骑跳跃能量条的值。

**值：** 无

**示例：**

```
{"placeholder":"current_mount_jump_meter"}
```

**输出：** `75`

## 当前 Boss 生命值（百分比） (`current_boss_health`)

**用途：** 返回选中的活动 Boss 的生命值，整数百分比范围为 `0` 到 `100`。`boss_index` 从 0 开始；`0` 选择第一个 Boss 生命条。

**值：** `boss_index`

**示例：**

```
{"placeholder":"current_boss_health","values":{"boss_index":"0"}}
```

**输出：** `75`

## Boss 名称 (`boss_name`)

**用途：** 返回活动 Boss 的名称。

**值：** `boss_index`, `as_json`

**示例：**

```
{"placeholder":"boss_name","values":{"boss_index":"0","as_json":"false"}}
```

**输出：** `Ender Dragon`

## Boss 数量 (`boss_count`)

**用途：** 返回当前活动 Boss 的数量。

**值：** 无

**示例：**

```
{"placeholder":"boss_count"}
```

**输出：** `1`

## 活动效果数量 (`effects_count`)

**用途：** 返回当前活跃药水效果数量。

**值：** 无

**示例：**

```
{"placeholder":"effects_count"}
```

**输出：** `3`

## 活动效果 (`active_effect`)

**用途：** 返回某个特定活动效果的信息。

**值：** `effect_index`

**示例：**

```
{"placeholder":"active_effect","values":{"effect_index":"0"}}
```

**输出：** `minecraft:speed`

## 选中的快捷栏槽位 (`active_hotbar_slot`)

**用途：** 返回当前选中的快捷栏槽位（0-8）。

**值：** 无

**示例：**

```
{"placeholder":"active_hotbar_slot"}
```

**输出：** `4`

## 槽位物品 (`slot_item`)

**用途：** 返回某个特定库存槽位中的物品信息。

**值：** `slot`

**示例：**

```
{"placeholder":"slot_item","values":{"slot":"0"}}
```

**输出：** `minecraft:diamond_sword`

## 槽位物品数量 (`slot_item_count`)

**用途：** 返回玩家库存特定槽位中物品的堆叠数量。

**值：** `slot`

**示例：**

```
{"placeholder":"slot_item_count","values":{"slot":"0"}}
```

**输出：** `64`

## 槽位物品耐久度 (`slot_item_durability`)

**用途：** 返回玩家库存特定槽位中物品的耐久信息。

**值：** `slot`, `format`

**示例：**

```
{"placeholder":"slot_item_durability","values":{"slot":"0","format":"percentage"}}
```
参数：
- `slot`：玩家库存槽位编号。
- `format`：`current`、`remaining`、`max`、`damage`、`percentage` 或 `percent`。

**输出：** `87`

## 槽位物品显示名称 (`slot_item_display_name_fm`)

**用途：** 以 JSON 文本组件的形式返回特定槽位中物品的显示名称。在旁观者模式下，快捷栏槽位可能会解析为旁观者菜单物品名称，除非 `ignore_spectator` 为 `true`。

**值：** `slot`, `ignore_spectator`

**示例：**

```
{"placeholder":"slot_item_display_name_fm","values":{"slot":"0","ignore_spectator":"false"}}
```

**输出：** `{"text":"Diamond Sword","color":"aqua"}`

## 库存物品数量 (`inventory_item_count`)

**用途：** 返回玩家库存中所有匹配物品的总数。当 `item` 为空时，它会汇总所有已占用库存槽位的堆叠数量。

**值：** `item`

**示例：**

```
{"placeholder":"inventory_item_count","values":{"item":"minecraft:diamond"}}
```

**输出：** `12`

## 库存槽位食物恢复量 (`inventory_slot_food_point_restore_amount`)

**用途：** 返回指定玩家库存槽位中的食物物品能恢复的饥饿值。

**值：** `slot`

**示例：**

```
{"placeholder":"inventory_slot_food_point_restore_amount","values":{"slot":"0"}}
```

**输出：** `4.0`

## 鼠标悬停的库存物品 (`hovered_inventory_item`)

**用途：** 返回当前在库存界面中鼠标悬停的物品键值。

**值：** 无

**示例：**

```
{"placeholder":"hovered_inventory_item"}
```

**输出：** `minecraft:apple`

## 世界游戏时间 (`game_time`)

**用途：** 返回当前游戏内时间刻计数。

**值：** 无

**示例：**

```
{"placeholder":"game_time"}
```

**输出：** `18000`

## 世界日间时间 (`world_daytime`)

**用途：** 返回当前世界日间时间。

**值：** 无

**示例：**

```
{"placeholder":"world_daytime"}
```

**输出：** `13000`

## 世界日间时间小时 (`world_daytime_hour`)

**用途：** 返回世界时间的小时部分。默认使用 24 小时制；将 `twelve_hour_format` 设为 `"true"` 可使用 12 小时制。

**值：** `twelve_hour_format`

**示例：**

```
{"placeholder":"world_daytime_hour","values":{"twelve_hour_format":"false"}}
```

**输出：** `12`

## 世界日间时间分钟 (`world_daytime_minute`)

**用途：** 返回世界时间的分钟部分（00-59）。

**值：** 无

**示例：**

```
{"placeholder":"world_daytime_minute"}
```

**输出：** `30`

## 世界难度 (`world_difficulty`)

**用途：** 返回当前世界难度。

**值：** 无

**示例：**

```
{"placeholder":"world_difficulty"}
```

**输出：** `normal`

## 当前世界种子 (`current_world_seed`)

**用途：** 返回当前单人世界的种子。当种子不可用时，返回空值。

**值：** 无

**示例：**

```
{"placeholder":"current_world_seed"}
```

**输出：** `123456789`

## 当前生物群系 (`current_biome`)

**用途：** 返回玩家当前所在的生物群系。将 `as_key` 设为 `"false"` 可在可用时返回翻译后的/显示名称。

**值：** `as_key`

**示例：**

```
{"placeholder":"current_biome","values":{"as_key":"true"}}
```

**输出：** `minecraft:plains`

## 当前维度 (`current_dimension`)

**用途：** 返回玩家当前所在的维度。将 `as_key` 设为 `"false"` 可在可用时返回翻译后的/显示名称。

**值：** `as_key`

**示例：**

```
{"placeholder":"current_dimension","values":{"as_key":"true"}}
```

**输出：** `minecraft:overworld`

## Gamerule 值 (`gamerule_value`)

**用途：** 返回已加载世界/服务器中某个 gamerule 的当前值。服务器世界需要服务器端安装 FancyMenu。

**值：** `name`

**示例：**

```
{"placeholder":"gamerule_value","values":{"name":"doDaylightCycle"}}
```

**输出：** `true`

## 物品分类 (`item_category`)

**用途：** 返回物品所在的创造模式标签分类。将 `as_key` 设为 `"true"` 可返回分类键，而不是显示名称。

**值：** `item`, `as_key`

**示例：**

```
{"placeholder":"item_category","values":{"item":"minecraft:diamond_sword","as_key":"false"}}
```

**输出：** `Combat`

## 当前 HUD 标题/副标题 (`current_title`)

**用途：** 返回当前显示的标题文本。

**值：** `is_subtitle`, `as_json`

**示例：**

```
{"placeholder":"current_title","values":{"is_subtitle":"false","as_json":"false"}}
```

**输出：** `Game Over!`

## 动作栏消息 (`action_bar_message_fm`)

**用途：** 以序列化的 Minecraft 文本组件形式返回当前原版动作栏消息。

**值：** 无

**示例：**

```
{"placeholder":"action_bar_message_fm"}
```

**输出：** `{"text":"You may not rest now","color":"red"}`

## 动作栏消息剩余时间 (`action_bar_message_time_fm`)

**用途：** 返回当前原版动作栏消息还会显示多少刻。

**值：** 无

**示例：**

```
{"placeholder":"action_bar_message_time_fm"}
```

**输出：** `42`

## 摄像机旋转 X (`camera_rotation_x_fm`)

**用途：** 返回当前摄像机俯仰角（度）。

**值：** 无

**示例：**

```
{"placeholder":"camera_rotation_x_fm"}
```

**输出：** `12.5`

## 摄像机旋转 Y (`camera_rotation_y_fm`)

**用途：** 返回当前摄像机偏航角（度）。

**值：** 无

**示例：**

```
{"placeholder":"camera_rotation_y_fm"}
```

**输出：** `-90.0`

## 摄像机旋转变化量 X (`camera_rotation_delta_x_fm`)

**用途：** 返回每刻摄像机俯仰角的变化量。

**值：** 无

**示例：**

```
{"placeholder":"camera_rotation_delta_x_fm"}
```

**输出：** `0.4`

## 摄像机旋转变化量 Y (`camera_rotation_delta_y_fm`)

**用途：** 返回每刻摄像机偏航角的变化量。

**值：** 无

**示例：**

```
{"placeholder":"camera_rotation_delta_y_fm"}
```

**输出：** `-1.2`

## 高亮物品显示时间 (`highlighted_item_time_fm`)

**用途：** 返回快捷栏上方高亮物品名称还会显示多少刻。

**值：** 无

**示例：**

```
{"placeholder":"highlighted_item_time_fm"}
```

**输出：** `30`

## 玩家使用物品进度 (`player_item_use_progress_fm`)

**用途：** 返回当前物品使用进度，范围为 `0.0` 到 `1.0`。

**值：** 无

**示例：**

```
{"placeholder":"player_item_use_progress_fm"}
```

**输出：** `0.65`

## 玩家位置变化量 X (`player_position_delta_x_fm`)

**用途：** 返回每刻玩家在 X 轴上的位置变化量。

**值：** 无

**示例：**

```
{"placeholder":"player_position_delta_x_fm"}
```

**输出：** `0.0`

## 玩家位置变化量 Y (`player_position_delta_y_fm`)

**用途：** 返回每刻玩家在 Y 轴上的位置变化量。

**值：** 无

**示例：**

```
{"placeholder":"player_position_delta_y_fm"}
```

**输出：** `-0.08`

## 玩家位置变化量 Z (`player_position_delta_z_fm`)

**用途：** 返回每刻玩家在 Z 轴上的位置变化量。

**值：** 无

**示例：**

```
{"placeholder":"player_position_delta_z_fm"}
```

**输出：** `0.12`

## 当前服务器 IP (`current_server_ip`)

**用途：** 返回已连接服务器的 IP。

**值：** 无

**示例：**

```
{"placeholder":"current_server_ip"}
```

**输出：** `mc.hypixel.net`

## 世界玩家列表 (`world_players_list`)

**用途：** 返回当前世界中所有玩家的列表。

**值：** `separator`

**示例：**

```
{"placeholder":"world_players_list","values":{"separator":", "}}
```

**输出：** `Steve, Alex, Notch`

## 服务器 MOTD (`servermotd`)

**用途：** 返回服务器的每日信息（Message of the Day）。

**值：** `ip`, `line`

**示例：**

```
{"placeholder":"servermotd","values":{"ip":"mc.hypixel.net","line":"1"}}
```

**输出：** `Welcome to Hypixel!`

## 服务器 PING (`serverping`)

**用途：** 返回服务器的延迟，单位毫秒。

**值：** `ip`

**示例：**

```
{"placeholder":"serverping","values":{"ip":"mc.hypixel.net"}}
```

**输出：** `54`

## 服务器玩家数量 (`serverplayercount`)

**用途：** 返回服务器的玩家数量。

**值：** `ip`

**示例：**

```
{"placeholder":"serverplayercount","values":{"ip":"mc.hypixel.net"}}
```

**输出：** `25000/30000`

## 服务器状态 (`serverstatus`)

**用途：** 返回服务器在线/离线状态。

**值：** `ip`

**示例：**

```
{"placeholder":"serverstatus","values":{"ip":"mc.hypixel.net"}}
```

**输出：** `§aOnline` 或 `§cOffline`

## 服务器版本 (`serverversion`)

**用途：** 返回服务器的 Minecraft 版本。

**值：** `ip`

**示例：**

```
{"placeholder":"serverversion","values":{"ip":"mc.hypixel.net"}}
```

**输出：** `1.21.1`

> [!NOTE]
> 下面的实时占位符接受 `timezone` 值。请使用 Java 时区 ID，例如 `UTC`、`Europe/Berlin` 或 `America/New_York`；也可以省略，或使用 `system` 表示系统时区。`unix_time` 始终返回 Unix 时间戳，并且没有 `timezone` 值。

## 年 (`realtimeyear`)

**用途：** 返回当前年份。

**值：** 无

**示例：**

```
{"placeholder":"realtimeyear"}
```

**输出：** `2024`

## 月 (`realtimemonth`)

**用途：** 返回当前月份（01-12）。

**值：** 无

**示例：**

```
{"placeholder":"realtimemonth"}
```

**输出：** `01`

## 日 (`realtimeday`)

**用途：** 返回当前月中的日期（01-31）。

**值：** 无

**示例：**

```
{"placeholder":"realtimeday"}
```

**输出：** `27`

## 小时 (`realtimehour`)

**用途：** 返回当前小时。默认使用 24 小时制；将 `twelve_hour_format` 设为 `"true"` 可使用 12 小时制。

**值：** `twelve_hour_format`, `timezone`

**示例：**

```
{"placeholder":"realtimehour","values":{"twelve_hour_format":"false","timezone":"system"}}
```

**输出：** `14`

## 分钟 (`realtimeminute`)

**用途：** 返回当前分钟（00-59）。

**值：** 无

**示例：**

```
{"placeholder":"realtimeminute"}
```

**输出：** `30`

## 秒 (`realtimesecond`)

**用途：** 返回当前秒数（00-59）。

**值：** 无

**示例：**

```
{"placeholder":"realtimesecond"}
```

**输出：** `45`

## 当前时间毫秒数（Unix 时间戳） (`unix_time`)

**用途：** 返回当前 Unix 时间戳，单位毫秒。

**值：** 无

**示例：**

```
{"placeholder":"unix_time"}
```

**输出：** `1716552478123`

## CPU 信息 (`cpuinfo`)

**用途：** 返回 CPU 信息。

**值：** 无

**示例：**

```
{"placeholder":"cpuinfo"}
```

**输出：** `Intel(R) Core(TM) i7-10700K CPU @ 3.80GHz`

## CPU 使用率（JVM） (`jvmcpu`)

**用途：** 返回 JVM 的 CPU 使用率百分比。

**值：** 无

**示例：**

```
{"placeholder":"jvmcpu"}
```

**输出：** `25.5`

## CPU 使用率（OS） (`oscpu`)

**用途：** 返回操作系统的 CPU 使用率百分比。

**值：** 无

**示例：**

```
{"placeholder":"oscpu"}
```

**输出：** `42.8`

## GPU 信息 (`gpuinfo`)

**用途：** 返回 Minecraft 当前渲染设备报告的名称。这并不保证能唯一识别某块物理 GPU。

**值：** 无

**示例：**

```
{"placeholder":"gpuinfo"}
```

**输出：** `NVIDIA GeForce RTX 3080`

## Java 版本 (`javaver`)

**用途：** 返回 Java 版本。

**值：** 无

**示例：**

```
{"placeholder":"javaver"}
```

**输出：** `17.0.2`

## Java 虚拟机 (`jvmname`)

**用途：** 返回 Java 虚拟机的名称。

**值：** 无

**示例：**

```
{"placeholder":"jvmname"}
```

**输出：** `OpenJDK 64-Bit Server VM`

## OpenGL 版本 (`glver`)

**用途：** 返回 Minecraft 当前渲染设备的驱动信息。尽管名称沿用了旧的 `glver`，其值并不保证只是一个 OpenGL 版本字符串。

**值：** 无

**示例：**

```
{"placeholder":"glver"}
```

**输出：** `4.6.0 NVIDIA 516.94`

## 操作系统名称 (`osname`)

**用途：** 返回操作系统名称。

**值：** 无

**示例：**

```
{"placeholder":"osname"}
```

**输出：** `Windows 10`

## FPS（每秒帧数） (`fps`)

**用途：** 返回当前每秒帧数。

**值：** 无

**示例：**

```
{"placeholder":"fps"}
```

**输出：** `120`

## 已用 RAM（MB） (`usedram`)

**用途：** 返回当前正在使用的内存量（MB）。

**值：** 无

**示例：**

```
{"placeholder":"usedram"}
```

**输出：** `4096`

## 最大 RAM（MB） (`maxram`)

**用途：** 返回分配的最大内存量（MB）。

**值：** 无

**示例：**

```
{"placeholder":"maxram"}
```

**输出：** `8192`

## 已用 RAM（%%） (`percentram`)

**用途：** 返回当前已使用的 RAM 百分比。

**值：** 无

**示例：**

```
{"placeholder":"percentram"}
```

**输出：** `50`

## 音频元素音量 (`audio_element_vol`)

**用途：** 返回一个音频元素的音量。

**值：** `element_identifier`

**示例：**

```
{"placeholder":"audio_element_vol","values":{"element_identifier":"background_music"}}
```

**输出：** `0.5`

## 当前音频曲目 (`audio_element_current_track`)

**用途：** 返回一个音频元素的曲目名称。

**值：** `element_identifier`, `display_name_mappings`

**示例：**

```
{"placeholder":"audio_element_current_track","values":{"element_identifier":"background_music","display_name_mappings":"track1.ogg=>Menu Theme%:%track2.ogg=>Credits Theme"}}
```

在 `display_name_mappings` 中，`=>` 用于分隔文件名和显示名称，`%:%` 用于分隔各个映射。

**输出：** `Menu Theme`

## 音频时长 (`audio_duration`)

**用途：** 以 `MM:SS` 格式返回 [音频元素](./elements#audio) 当前已加载曲目的时长。曲目可以正在播放、暂停或停止。

**值：** `element_identifier`

**示例：**

```
{"placeholder":"audio_duration","values":{"element_identifier":"background_music"}}
```

**输出：** `03:45`

## 音频播放时间 (`audio_playtime`)

**用途：** 返回音频曲目的当前播放时间。将 `show_percentage` 设为 `"true"` 可获得 0-100 的进度值，而不是 `MM:SS`。

**值：** `element_identifier`, `show_percentage`

**示例：**

```
{"placeholder":"audio_playtime","values":{"element_identifier":"background_music","show_percentage":"false"}}
```

**输出：** `01:30`（或在 `show_percentage` 为 `"true"` 时显示 `45`）

**不可用结果：** `00:00`，或在百分比模式下为 `0`。当前值在曲目播放或暂停时可用；已停止、缺失或尚未就绪的曲目会使用不可用结果。

## 音频播放状态 (`audio_playing_state`)

**用途：** 返回音频元素是否正在播放（true/false）。

**值：** `element_identifier`

**示例：**

```
{"placeholder":"audio_playing_state","values":{"element_identifier":"background_music"}}
```

**输出：** `true`

## 视频元素音量 (`video_element_vol`)

**用途：** 返回视频元素的音量级别（0.0 到 1.0）。

**值：** `element_identifier`

**示例：**

```
{"placeholder":"video_element_vol","values":{"element_identifier":"my_video_element"}}
```

**输出：** `0.5`

## 视频元素时长 (`video_element_duration`)

**用途：** 以 `MM:SS` 格式返回视频元素的总时长。将 `output_as_timestamp` 设为 `"true"` 可返回毫秒时间戳。

**值：** `element_identifier`, `output_as_timestamp`

**示例：**

```
{"placeholder":"video_element_duration","values":{"element_identifier":"my_video_element","output_as_timestamp":"false"}}
```

**输出：** `02:00`（或在 `output_as_timestamp` 为 `"true"` 时显示 `120000`）

## 视频元素播放时间 (`video_element_playtime`)

**用途：** 以 `MM:SS` 格式返回视频元素的当前播放时间（进度）。将 `show_percentage` 设为 `"true"` 可返回 0-100 的进度值，或将 `output_as_timestamp` 设为 `"true"` 返回毫秒值。

**值：** `element_identifier`, `show_percentage`, `output_as_timestamp`

**示例：**

```
{"placeholder":"video_element_playtime","values":{"element_identifier":"my_video_element","show_percentage":"false","output_as_timestamp":"false"}}
```

**输出：** `00:45`（或百分比 `38`，或时间戳 `45200`）

## 视频元素暂停状态 (`video_element_paused_state`)

**用途：** 返回视频元素是否处于暂停状态（true/false）。

**值：** `element_identifier`

**示例：**

```
{"placeholder":"video_element_paused_state","values":{"element_identifier":"my_video_element"}}
```

**输出：** `false`

## 视频背景音量 (`video_background_vol`)

**用途：** 返回视频菜单背景的音量级别（0.0 到 1.0）。

**值：** `background_identifier`

**示例：**

```
{"placeholder":"video_background_vol","values":{"background_identifier":"main_menu_video"}}
```

**输出：** `0.7`

## 视频背景时长 (`video_background_duration`)

**用途：** 以 `MM:SS` 格式返回视频菜单背景的总时长。将 `output_as_timestamp` 设为 `"true"` 可返回毫秒时间戳。

**值：** `background_identifier`, `output_as_timestamp`

**示例：**

```
{"placeholder":"video_background_duration","values":{"background_identifier":"main_menu_video","output_as_timestamp":"false"}}
```

**输出：** `03:00`（或在 `output_as_timestamp` 为 `"true"` 时显示 `180000`）

## 视频背景播放时间 (`video_background_playtime`)

**用途：** 以 `MM:SS` 格式返回视频菜单背景的当前播放时间（进度）。将 `show_percentage` 设为 `"true"` 可返回 0-100 的进度值，或将 `output_as_timestamp` 设为 `"true"` 返回毫秒值。

**值：** `background_identifier`, `show_percentage`, `output_as_timestamp`

**示例：**

```
{"placeholder":"video_background_playtime","values":{"background_identifier":"main_menu_video","show_percentage":"false","output_as_timestamp":"false"}}
```

**输出：** `01:00`（或百分比 `33`，或时间戳 `60500`）

## 视频背景暂停状态 (`video_background_paused_state`)

**用途：** 返回视频菜单背景是否处于暂停状态（true/false）。

**值：** `background_identifier`

**示例：**

```
{"placeholder":"video_background_paused_state","values":{"background_identifier":"main_menu_video"}}
```

**输出：** `true`

## 计算器 (`calc`)

**用途：** 计算器占位符是一个强大的工具，可让你在布局中执行数学计算。它支持多种数学运算，并且可以同时处理小数和整数。

**值：** `decimal`, `expression`

### 基本语法

**示例：**

```
{"placeholder":"calc","values":{"decimal":"true/false","expression":"your_expression"}}
```

计算器有两个主要参数：
- `decimal`：决定结果是否保留小数位（`true`）或四舍五入为整数（`false`）
- `expression`：要计算的数学表达式

### 支持的运算
计算器支持以下数学运算：
- 基础运算：`+`（加）、`-`（减）、`*`（乘）、`/`（除）
- 括号：使用 `( )` 对运算进行分组
- 幂：`^` 表示指数
- 平方根：`sqrt()`
- 三角函数：`sin()`、`cos()`、`tan()`
- 数学常量：`pi`、`e`
- 绝对值：`abs()`
- 对数：`log()`、`ln()`

## 随机数 (`random_number`)

**用途：** 在指定范围内生成一个随机数。

**值：** `min`, `max`

**示例：**

```
{"placeholder":"random_number","values":{"min":"1","max":"100"}}
```

**输出：** `42`

## 最大值 (`maxnum`)

**用途：** 返回两个数中较大的一个。

**值：** `first`, `second`

**示例：**

```
{"placeholder":"maxnum","values":{"first":"10","second":"20"}}
```

**输出：** `20`

## 最小值 (`minnum`)

**用途：** 返回两个数中较小的一个。

**值：** `first`, `second`

**示例：**

```
{"placeholder":"minnum","values":{"first":"10","second":"20"}}
```

**输出：** `10`

## 绝对值 (`absnum`)

**用途：** 返回一个数的绝对值。

**值：** `num`

**示例：**

```
{"placeholder":"absnum","values":{"num":"-10.5"}}
```

**输出：** `10.5`

## 转为负数 (`negnum`)

**用途：** 将一个正数变为负数。零和已经为负的值保持不变。

**值：** `num`

**示例：**

```
{"placeholder":"negnum","values":{"num":"10.5"}}
```

**输出：** `-10.5`

## *pi*（数学） (`math_pi`)

**用途：** 返回 π 的值。

**值：** 无

**示例：**

```
{"placeholder":"math_pi"}
```

**输出：** `3.141592653589793`

## 三角正弦（数学） (`math_sin`)

**用途：** 返回弧度角的正弦值。请先将角度值转换为弧度。

**值：** `angle`

**示例：**

```
{"placeholder":"math_sin","values":{"angle":"1.5707963267948966"}}
```

**输出：** `1.0`

## 三角余弦（数学） (`math_cos`)

**用途：** 返回弧度角的余弦值。请先将角度值转换为弧度。

**值：** `angle`

**示例：**

```
{"placeholder":"math_cos","values":{"angle":"0"}}
```

**输出：** `1.0`

## 三角正切（数学） (`math_tan`)

**用途：** 返回弧度角的正切值。请先将角度值转换为弧度。

**值：** `angle`

**示例：**

```
{"placeholder":"math_tan","values":{"angle":"0"}}
```

**输出：** `0.0`

## 向下取整（数学） (`math_floor`)

**用途：** 返回数值的数学向下取整结果，格式化为带 `.0` 的小数后缀。

**值：** `num`

**示例：**

```
{"placeholder":"math_floor","values":{"num":"3.14"}}
```

**输出：** `3.0`

## 向上取整（数学） (`math_ceil`)

**用途：** 返回数值的数学向上取整结果，格式化为带 `.0` 的小数后缀。

**值：** `num`

**示例：**

```
{"placeholder":"math_ceil","values":{"num":"3.14"}}
```

**输出：** `4.0`

当你需要不带 `.0` 的整数文本时，请使用 [**四舍五入**](#round-math-math_round) 或在关闭小数输出的情况下使用 [**计算器**](#计算器-calc)。

## 四舍五入（数学） (`math_round`)

**用途：** 对数字进行四舍五入。默认四舍五入到最接近的整数；将 `decimals` 设为非负数可保留对应的小数位数。

**值：** `num`, `decimals`

**示例：**

```
{"placeholder":"math_round","values":{"num":"3.14159","decimals":"2"}}
```

**输出：** `3.14`（若 `decimals:-1` 或未填写 → `3`）

## 符号（数学） (`math_sign`)

**用途：** 返回数字的符号（正数为 1，负数为 -1，零为 0）。

**值：** `num`

**示例：**

```
{"placeholder":"math_sign","values":{"num":"-3.14"}}
```

**输出：** `-1`

## 双曲正弦（数学） (`math_sinh`)

**用途：** 返回数字的双曲正弦值。

**值：** `num`

**示例：**

```
{"placeholder":"math_sinh","values":{"num":"1"}}
```

**输出：** `1.1752011936438014`

## 双曲余弦（数学） (`math_cosh`)

**用途：** 返回数字的双曲余弦值。

**值：** `num`

**示例：**

```
{"placeholder":"math_cosh","values":{"num":"1"}}
```

**输出：** `1.5430806348152437`

## 双曲正切（数学） (`math_tanh`)

**用途：** 返回数字的双曲正切值。

**值：** `num`

**示例：**

```
{"placeholder":"math_tanh","values":{"num":"1"}}
```

**输出：** `0.7615941559557649`

## 拆分文本 (`split_text`)

**用途：** 使用指定分隔符拆分文本。

**值：** `input`, `regex`, `max_parts`, `split_index`

**示例：**

```
{"placeholder":"split_text","values":{"input":"hello,world","regex":",","max_parts":"2","split_index":"1"}}
```

**输出：** `world`

## 去除首尾空白 (`trim_text`)

**用途：** 去除首尾空白字符。

**值：** `text`

**示例：**

```
{"placeholder":"trim_text","values":{"text":"  hello world  "}}
```

**输出：** `hello world`

## 裁剪文本 (`crop_text`)

**用途：** 从文本开头和结尾移除指定数量的字符。

**值：** `text`, `remove_from_start`, `remove_from_end`

**示例：**

```
{"placeholder":"crop_text","values":{"text":"hello world","remove_from_start":"1","remove_from_end":"1"}}
```

**输出：** `ello worl`

## 转义字符串 (`stringify`)

**用途：** 通过转义所有语法字符，将文本转换为字符串。

**值：** `text`

**示例：**

```
{"placeholder":"stringify","values":{"text":"text with {special} \"characters\""}}
```

**输出：** `text with \{special\} \"characters\"`

## 本地化文本 (`local`)

**用途：** 获取某个键对应的本地化文本。

**值：** `key`

**示例：**

```
{"placeholder":"local","values":{"key":"menu.singleplayer"}}
```

**输出：** `Singleplayer`

## Web 文本 (`webtext`)

**用途：** 从网页 URL 获取文本内容。

**值：** `link`

**示例：**

```
{"placeholder":"webtext","values":{"link":"http://somewebsite.com/textfile.txt"}}
```

**输出：** `Welcome to the server!`

## 随机文本 (`randomtext`)

**用途：** 从文本文件、URL 或直接输入的纯文本中返回一行随机文本。文本会按指定间隔变化。文件和 URL 内容大约每 30 秒刷新一次；直接纯文本内容会被缓存，因为它不需要重新加载。

**值：** `source`, `interval`

在占位符值中，`/config/...` 表示 `<game-directory>/config/...`；它不是文件系统根路径。参见 [资源](./resources#local-resources)。

**示例：**

```
{"placeholder":"randomtext","values":{"source":"/config/fancymenu/assets/<file_name.txt>","interval":"10"}}
```
参数：
- `source`：文本行的来源（替代旧的 `path` 参数）
  - 文件路径：`/config/fancymenu/assets/quotes.txt`
  - URL：`https://example.com/quotes.txt`
  - 纯文本：`Line 1\nLine 2\nLine 3`
- `interval`：文本变化之间的时间（秒）

该占位符现在支持三种来源类型：
1. **本地文件**：来自游戏目录中的文本文件
   ```
   {"placeholder":"randomtext","values":{"source":"/config/fancymenu/assets/quotes.txt","interval":"10"}}
   ```
2. **URL**：来自互联网的远程文本文件
   ```
   {"placeholder":"randomtext","values":{"source":"https://example.com/quotes.txt","interval":"10"}}
   ```
3. **纯文本**：直接输入的文本，使用 `\n` 分隔行
   ```
   {"placeholder":"randomtext","values":{"source":"First line\nSecond line\nThird line","interval":"5"}}
   ```

注意：使用 `path` 而不是 `source` 的旧占位符仍然有效。

## JSON 解析器 (`json`)

**用途：** 从文件、URL 或直接 JSON 内容中解析 JSON 数据，并使用 JSON Path 表达式提取值。

**值：** `source`, `json_path`

**示例：**

```
{"placeholder":"json","values":{"source":"path_or_link_or_json_content","json_path":"$.some.json.path"}}
```
参数：
- `source`：JSON 数据来源
  - 文件路径：`/config/fancymenu/assets/data.json`
  - URL：`https://api.example.com/data.json`
  - 直接 JSON：`{"name":"Steve","level":42}`
- `json_path`：用于提取数据的 JSON Path 表达式

该占位符现在支持三种来源类型：
1. **本地文件**：来自游戏目录中的 JSON 文件
   ```
   {"placeholder":"json","values":{"source":"/config/fancymenu/assets/playerdata.json","json_path":"$.player.name"}}
   ```
2. **URL**：来自 API 或网络服务的远程 JSON 数据
   ```
   {"placeholder":"json","values":{"source":"https://api.minecraft.com/server/status","json_path":"$.online"}}
   ```
3. **直接 JSON**：内联 JSON 内容
   ```
   {"placeholder":"json","values":{"source":"{"name":"Steve","score":42,"rank":"Diamond"}","json_path":"$.rank"}}
   ```

JSON Path 示例：
- `$.name` - 从根节点获取“name”字段
- `$.player.level` - 获取“player”内部嵌套的“level”字段
- `$.items[0].id` - 获取数组中第一个项的“id”
- `$.scores.*` - 获取“scores”对象中的所有值

## 绝对文件/文件夹路径 (`absolute_path`)

**用途：** 返回文件的绝对路径。

**值：** `short_path`

**示例：**

```
{"placeholder":"absolute_path","values":{"short_path":"relative/path/to/file.txt"}}
```

**输出：** `C:/Games/PrismLauncher/instances/My Pack/relative/path/to/file.txt`

## 文本字符数 (`text_character_count`)

**用途：** 返回给定文本中的字符数量。

**值：** `text`

**示例：**

```
{"placeholder":"text_character_count","values":{"text":"Hello World!"}}
```

**输出：** `12`

## 文本宽度 (`text_width`)

**用途：** 返回给定文本渲染后的像素宽度。

**值：** `text`

**示例：**

```
{"placeholder":"text_width","values":{"text":"Hello World!"}}
```

**输出：** `66`

## 转为大写 (`uppercase_text`)

**用途：** 将输入文本转换为全大写字母。

**值：** `text`

**示例：**

```
{"placeholder":"uppercase_text","values":{"text":"Hello World"}}
```

**输出：** `HELLO WORLD`

## 转为小写 (`lowercase_text`)

**用途：** 将输入文本转换为全小写字母。

**值：** `text`

**示例：**

```
{"placeholder":"lowercase_text","values":{"text":"Hello World"}}
```

**输出：** `hello world`

## 标题式大小写文本 (`title_case_text`)

**用途：** 将输入文本转换为标题式大小写。

**值：** `text`

**示例：**

```
{"placeholder":"title_case_text","values":{"text":"hello world"}}
```

**输出：** `Hello World`

## 句首大写文本 (`sentence_case_text`)

**用途：** 将输入文本转换为句首大写。

**值：** `text`

**示例：**

```
{"placeholder":"sentence_case_text","values":{"text":"hello world. this is fancymenu!"}}
```

**输出：** `Hello world. This is fancymenu!`

## 蛇形命名文本 (`snake_case_text`)

**用途：** 将输入文本转换为 `snake_case`。

**值：** `text`

**示例：**

```
{"placeholder":"snake_case_text","values":{"text":"Hello World"}}
```

**输出：** `hello_world`

## 连字符命名文本 (`kebab_case_text`)

**用途：** 将输入文本转换为 `kebab-case`。

**值：** `text`

**示例：**

```
{"placeholder":"kebab_case_text","values":{"text":"Hello World"}}
```

**输出：** `hello-world`

## 交替大小写文本 (`alternating_case_text`)

**用途：** 将输入文本转换为交替大小写。

**值：** `text`

**示例：**

```
{"placeholder":"alternating_case_text","values":{"text":"alternating case"}}
```

**输出：** `aLtErNaTiNg CaSe`

## 切换大小写文本 (`toggle_case_text`)

**用途：** 切换输入文本中每个字母的大小写。

**值：** `text`

**示例：**

```
{"placeholder":"toggle_case_text","values":{"text":"Toggle Case"}}
```

**输出：** `tOGGLE cASE`

## 编码为 Base64 (`base64_encode`)

**用途：** 将给定文本编码为 Base64。

**值：** `text`

**示例：**

```
{"placeholder":"base64_encode","values":{"text":"Hello World"}}
```

**输出：** `SGVsbG8gV29ybGQ=`

## 从 Base64 解码 (`base64_decode`)

**用途：** 将 Base64 字符串解码回纯文本。

**值：** `text`

**示例：**

```
{"placeholder":"base64_decode","values":{"text":"SGVsbG8gV29ybGQ="}}
```

**输出：** `Hello World`

## 文件文本 (`file_text`)

**用途：** 返回来自文件或 URL 的文本行。可以返回所有行，或仅返回最后 X 行。

**值：** `path_or_url`, `mode`, `separator`, `last_lines`

**示例：**

```
{"placeholder":"file_text","values":{"path_or_url":"/config/fancymenu/assets/some_file.txt","mode":"all","separator":"\n","last_lines":"1"}}
```
参数：
- `path_or_url`：要读取的文件路径或 URL
- `mode`：`"all"`（返回所有行）或 `"last"`（只返回最后 X 行）
- `separator`：行之间使用的文本（默认：`"\n"`）
- `last_lines`：当模式为 `"last"` 时返回的行数（默认：`"1"`）

**输出：**

```text
First line
Second line
```

## 剪贴板内容 (`clipboard_content`)

**用途：** 返回系统剪贴板中当前存储的文本内容。

**值：** 无

**示例：**

```
{"placeholder":"clipboard_content"}
```

**输出：** `Hello from the clipboard`

## 替换文本 (`replace_text`)

**用途：** 使用字面文本或正则表达式替换字符串中的文本。

**值：** `text`, `search`, `replacement`, `use_regex`, `replace_all`

**示例：**

```
{"placeholder":"replace_text","values":{"text":"Hello World! This is a test.","search":"World","replacement":"FancyMenu","use_regex":"false","replace_all":"true"}}
```
参数：
- `text`：要处理的输入文本
- `search`：要搜索的文本或正则表达式模式
- `replacement`：替换文本
- `use_regex`：是否使用正则表达式（`"true"`）或字面匹配（`"false"`）
- `replace_all`：替换所有匹配项（`"true"`）还是仅替换第一个（`"false"`）

**输出：** `Hello FancyMenu! This is a test.`

## 条件切换 (`switch_case`)

**用途：** 根据某个值执行 switch-case 操作。

**值：** `value`, `cases`, `default`

**示例：**

```
{"placeholder":"switch_case","values":{"value":"1","cases":"1:first case,2:second case,3:third case","default":"default case"}}
```

**输出：** `first case`（如果值为 1）

## 获取变量值（FM 变量） (`getvariable`)

**用途：** 检索之前保存的变量值。

**值：** `name`

**示例：**

```
{"placeholder":"getvariable","values":{"name":"some_variable"}}
```

**输出：** `42`

## 获取 NBT 数据 (`nbt_data_get`)

**用途：** 在客户端检索 NBT 数据（类似 `/data get` 命令）。当连接到服务器且需要服务器端权威值时，请使用服务器版本 `nbt_data_get_server`。

**值：** `source_type`, `entity_selector`, `nbt_path`, `scale`, `return_type`

**示例：**

```
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"foodLevel","scale":"1.0","return_type":"value"}}
```
参数：
- `source_type`：`"entity"` 或 `"block"`
- `entity_selector`：实体选择器，如 `@s`、`@p`、`@e`，或 UUID/名称（用于实体）
- `block_pos`：方块坐标，格式为 `"x y z"`（用于方块）
- `nbt_path`：要检索的 NBT 路径
- `scale`：数值的可选缩放因子（默认：`"1.0"`）
- `return_type`：返回数据的方式：
  - `"value"`：默认，返回值（数值可按需缩放）
  - `"string"`：以字符串形式返回实际 NBT 数据
  - `"snbt"`：以 SNBT（格式化 NBT）返回
  - `"json"`：以 JSON 格式的组件返回（用于复合标签）

**输出：** `20`（饥饿值）

## 获取 NBT 数据（服务器端） (`nbt_data_get_server`)

**用途：** 通过数据包查询服务器端的 NBT 数据，并短暂缓存结果。值与客户端占位符一致。

**值：** `source_type`, `entity_selector`, `block_pos`, `storage_id`, `nbt_path`, `scale`, `return_type`

**示例：**

```
{"placeholder":"nbt_data_get_server","values":{"source_type":"entity","entity_selector":"@s","block_pos":"","storage_id":"minecraft:storage_key","nbt_path":"SelectedItem.id","scale":"1.0","return_type":"value"}}
```

**输出：** `minecraft:diamond_sword`

## 上一次死亡消息 (`lastdeathmessage`)

**用途：** 返回客户端玩家最近记录的死亡消息。将 `as_json_component` 设为 `"true"` 可获取原始 JSON 文本组件。

**值：** `as_json_component`

**示例：**

```
{"placeholder":"lastdeathmessage","values":{"as_json_component":"false"}}
```

**输出：** `Steve was slain by Zombie`

## 运行时长 (`uptime_duration`)

**用途：** 返回 FancyMenu 已加载的时长。默认单位为秒；将 `output_as_millis` 设为 `"true"` 可返回毫秒。

**值：** `output_as_millis`

**示例：**

```
{"placeholder":"uptime_duration","values":{"output_as_millis":"false"}}
```

**输出：** `742`（加载后的秒数）

## 世界存档名称 (`level_save_names`)

**用途：** 使用所选分隔符列出所有本地世界存档名称。运行于客户端线程。

**值：** `separator`

**示例：**

```
{"placeholder":"level_save_names","values":{"separator":", "}}
```

**输出：** `Creative Test, Survival World, Hardcore`

## 世界存档数据 (`level_save_data`)

**用途：** 返回指定世界名称的序列化世界数据（必须与存档列表中显示的名称匹配）。

**值：** `level_name`

**示例：**

```
{"placeholder":"level_save_data","values":{"level_name":"Survival World"}}
```

**输出：** `{"name":"Survival World","gameMode":"survival",...}`

## 数字进制转换器 (`number_base_convert`)

**用途：** 将一个数字（整数或小数）从一种进制转换为另一种进制（2–36）。如果未提供进制，默认使用十进制。

**值：** `input`, `from_base`, `to_base`

**示例：**

```
{"placeholder":"number_base_convert","values":{"input":"67.5","from_base":"10","to_base":"16"}}
```

**输出：** `43.8`

## 文件大小 (`file_size`)

**用途：** 返回本地文件的大小，单位字节。仅允许本地路径。

**值：** `path`

**示例：**

```
{"placeholder":"file_size","values":{"path":"/config/fancymenu/assets/notes.txt"}}
```

**输出：** `1284`

## 文件 MD5 (`file_md5`)

**用途：** 返回本地文件的 MD5 哈希，格式为小写十六进制字符串。

**值：** `path`

**示例：**

```
{"placeholder":"file_md5","values":{"path":"/config/fancymenu/assets/notes.txt"}}
```

**输出：** `d41d8cd98f00b204e9800998ecf8427e`

# 实际示例

## 创建动态内存显示
```
已用内存：{"placeholder":"usedram"}MB / {"placeholder":"maxram"}MB（{"placeholder":"percentram"}%）
```

## 制作实时时钟
```
{"placeholder":"realtimehour","values":{"timezone":"system"}}:{"placeholder":"realtimeminute","values":{"timezone":"system"}}:{"placeholder":"realtimesecond","values":{"timezone":"system"}}
```

## 创建系统信息显示
```
操作系统：{"placeholder":"osname"}
CPU：{"placeholder":"cpuinfo"}
GPU：{"placeholder":"gpuinfo"}
Java：{"placeholder":"javaver"}
```

## 玩家状态 HUD
```
生命值：{"placeholder":"current_player_health"} / {"placeholder":"max_player_health"}（{"placeholder":"current_player_health_percent"}%）
护甲：{"placeholder":"current_player_armor"} / {"placeholder":"max_player_armor"}
经验等级：{"placeholder":"current_player_level"}
```

## 使用嵌套占位符进行复杂计算
```
{"placeholder":"calc","values":{"decimal":"true","expression":"({"placeholder":"usedram"} / {"placeholder":"maxram"}) * 100"}}
```

## 带四舍五入的坐标显示
```
X: {"placeholder":"math_round","values":{"num":"{"placeholder":"player_x_coordinate"}"}}
Y: {"placeholder":"math_round","values":{"num":"{"placeholder":"player_y_coordinate"}"}}
Z: {"placeholder":"math_round","values":{"num":"{"placeholder":"player_z_coordinate"}"}}
```

# 最佳实践

1. **缓存开销较大的操作**：某些占位符（例如读取系统信息的占位符）可能比较耗资源。如果需要多次使用，建议将其值存储到变量中。

2. **使用合适的小数设置**：在进行计算时，请恰当地使用 `decimal` 参数。当你需要整数时设为 `false`，当你需要精确的小数值时设为 `true`。

3. **处理缺失值**：始终考虑占位符没有返回值时应该如何处理。在这种情况下，你可能需要提供默认值。

4. **测试性能**：当使用大量占位符或复杂的嵌套结构时，请测试性能影响，尤其是在较低配置的系统上。

5. **使用高级尺寸/定位**：对于动态 UI 元素，将占位符与高级尺寸和定位结合使用，以创建响应式布局。

6. **与变量结合使用**：将占位符与变量一起使用，可以创建更动态、可通过动作更新的内容。

# 常见问题与解决方案

## 占位符未更新
如果占位符的值没有按预期更新，请检查：
- 占位符格式是否正确
- 是否使用了正确的占位符 ID 大小写
- 占位符是否需要特定条件才会更新

## 嵌套占位符无法工作
在嵌套占位符时：
- 确保引号已正确转义
- 验证每个嵌套占位符本身是否有效

## 性能问题
如果你注意到性能问题：
- 减少占位符的使用数量
- 避免不必要的嵌套
- 考虑对常用值使用变量
- 根据需求使用合适的占位符（例如，静态值足够时不要使用实时占位符）
