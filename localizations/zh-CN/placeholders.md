---
title: 占位符
description: 如何使用占位符。
---

# 占位符

占位符是动态值，在使用时会被实际内容替换。在 FancyMenu 中，占位符允许你将动态内容插入到各种元素中，例如文本、按钮和加载条件。你可以把它们理解为变量：当布局显示时，这些变量会被计算并替换为实际值。

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
FancyMenu 占位符系统最强大的功能之一，就是可以在其他占位符中嵌套占位符。这意味着你可以将一个占位符的输出作为另一个占位符的输入。

嵌套占位符示例：
```
{"placeholder":"calc","values":{"decimal":"true","expression":"{"placeholder":"maxram"} / 1024"}}
```
此示例将最大内存值除以 1024，把它从 MB 转换为 GB。

# 使用占位符

大多数带有文本输入的元素都支持占位符。你在编辑时可以查看文本输入是否支持占位符。如果编辑文本时打开的是全屏 **文本编辑器**，就说明它支持占位符。

要查看 **所有占位符的列表**，只需点击 **文本编辑器** 右上角的 **占位符** 按钮。

占位符列表顶部有一个 **搜索栏**，可用于搜索占位符。

在占位符列表中点击某个占位符，会将其粘贴到文本内容中。

# 占位符详解

此列表包含 FancyMenu 中大多数（如果不是全部）可用的占位符。由于模组更新，这个列表有时可能会略有过时。

## 玩家名称 (playername)
返回当前玩家的用户名。
```
{"placeholder":"playername"}
```
示例输出：`Steve`

## 玩家 UUID (playeruuid)
返回玩家的唯一标识符。
```
{"placeholder":"playeruuid"}
```
示例输出：`c8cde7fe-7ced-11eb-9439-0242ac130002`

## Minecraft 版本 (mcversion)
返回当前 Minecraft 版本。
```
{"placeholder":"mcversion"}
```
示例输出：`1.19.2`

## Mod 加载器版本 (loaderver)
返回模组加载器（Forge/Fabric）的版本。
```
{"placeholder":"loaderver"}
```
示例输出：`43.2.0`

## Mod 加载器名称 (loadername)
返回模组加载器的名称。
```
{"placeholder":"loadername"}
```
示例输出：`Forge`

## Mod 版本 (modversion)
返回指定模组的版本。
```
{"placeholder":"modversion","values":{"modid":"fancymenu"}}
```
示例输出：`2.14.9`

## Mod 总数 (totalmods)
返回已安装模组的总数。
```
{"placeholder":"totalmods"}
```
示例输出：`45`

## 已加载模组数 (loadedmods)
返回当前已加载的模组数量。
```
{"placeholder":"loadedmods"}
```
示例输出：`43`

## 世界加载进度 (world_load_progress)
返回当前世界加载进度百分比。
```
{"placeholder":"world_load_progress"}
```
示例输出：`75`

## Minecraft 选项值 (minecraft_option_value)
返回某个 Minecraft 选项的值。
```
{"placeholder":"minecraft_option_value","values":{"name":"fov"}}
```
示例输出：`70`

## 上一个世界或服务器 (last_world_server)
返回上一次访问的世界或服务器的信息。
```
{"placeholder":"last_world_server","values":{"type":"both","full_world_path":"true"}}
```
参数：
- `type`：决定返回哪种信息
  - `"both"`：返回上一次访问的世界或服务器（默认）
  - `"server"`：仅当上一次访问的是服务器时返回
  - `"world"`：仅当上一次访问的是世界时返回
- `full_world_path`：控制世界路径的显示方式
  - `"true"`：返回完整世界路径（默认）
  - `"false"`：仅返回世界名称，不包含路径（不影响服务器）

示例：
- 服务器：`mc.hypixel.net`
- 带完整路径的世界：`saves/New World`
- 不带完整路径的世界：`New World`

## 屏幕宽度 (guiwidth)
返回当前屏幕宽度。
```
{"placeholder":"guiwidth"}
```
示例输出：`1920`

## 屏幕高度 (guiheight)
返回当前屏幕高度。
```
{"placeholder":"guiheight"}
```
示例输出：`1080`

## 当前屏幕标识符 (screenid)
返回当前屏幕的标识符。
```
{"placeholder":"screenid"}
```
示例输出：`title_screen`

## 元素宽度 (elementwidth)
返回指定元素的宽度。
```
{"placeholder":"elementwidth","values":{"id":"my_button"}}
```
示例输出：`200`

## 元素高度 (elementheight)
返回指定元素的高度。
```
{"placeholder":"elementheight","values":{"id":"my_button"}}
```
示例输出：`20`

## 元素 X 坐标 (elementposx)
返回指定元素的 X 坐标。
```
{"placeholder":"elementposx","values":{"id":"my_button"}}
```
示例输出：`150`

## 元素 Y 坐标 (elementposy)
返回指定元素的 Y 坐标。
```
{"placeholder":"elementposy","values":{"id":"my_button"}}
```
示例输出：`100`

## 鼠标 X 坐标 (mouseposx)
返回当前鼠标的 X 坐标。
```
{"placeholder":"mouseposx"}
```
示例输出：`960`

## 鼠标 Y 坐标 (mouseposy)
返回当前鼠标的 Y 坐标。
```
{"placeholder":"mouseposy"}
```
示例输出：`540`

## 每秒点击数 (clicks_per_second)
返回鼠标按键当前的每秒点击数。
```
{"placeholder":"clicks_per_second","values":{"mouse_button":"left"}}
```
参数：
- `mouse_button`：`left` 或 `right`

示例输出：`8`

## GUI 缩放 (guiscale)
返回当前 GUI 缩放。
```
{"placeholder":"guiscale"}
```
示例输出：`2`

## 原版按钮标签/文本 (vanillabuttonlabel)
返回原版控件/按钮的标签或文本。
```
{"placeholder":"vanillabuttonlabel","values":{"locator":"some.menu.identifier:505280"}}
```
示例输出：`Options...`

## 文本输入框值 (text_input_field_value)
根据元素标识符返回自定义或原版文本输入框的当前值。
```
{"placeholder":"text_input_field_value","values":{"element_identifier":"my_input"}}
```
示例输出：`Hello World`

## 玩家当前生命值 (current_player_health)
返回玩家当前生命值。
```
{"placeholder":"current_player_health"}
```
示例输出：`20.0`

## 玩家最大生命值 (max_player_health)
返回玩家最大生命值。
```
{"placeholder":"max_player_health"}
```
示例输出：`20.0`

## 玩家当前生命值（百分比） (current_player_health_percent)
返回玩家生命值百分比。
```
{"placeholder":"current_player_health_percent"}
```
示例输出：`100`

## 玩家当前吸收生命值 (current_player_absorption_health)
返回玩家的吸收生命值（金色心心）。
```
{"placeholder":"current_player_absorption_health"}
```
示例输出：`4.0`

## 玩家最大吸收生命值 (max_player_absorption_health)
返回最大吸收生命值。
```
{"placeholder":"max_player_absorption_health"}
```
示例输出：`4.0`

## 玩家当前吸收生命值（百分比） (current_player_absorption_health_percent)
返回玩家吸收生命值百分比。
```
{"placeholder":"current_player_absorption_health_percent"}
```
示例输出：`100`

## 玩家当前饥饿值 (current_player_hunger)
返回玩家当前饥饿值。
```
{"placeholder":"current_player_hunger"}
```
示例输出：`20`

## 玩家最大饥饿值 (max_player_hunger)
返回最大饥饿值。
```
{"placeholder":"max_player_hunger"}
```
示例输出：`20`

## 玩家当前饥饿值（百分比） (current_player_hunger_percent)
返回玩家饥饿值百分比。
```
{"placeholder":"current_player_hunger_percent"}
```
示例输出：`100`

## 玩家当前饥饿饱和度 (current_player_hunger_saturation)
返回玩家当前的饥饿饱和度值。
```
{"placeholder":"current_player_hunger_saturation"}
```
示例输出：`5.0`

## 玩家当前护甲值 (current_player_armor)
返回玩家当前护甲值。
```
{"placeholder":"current_player_armor"}
```
示例输出：`20`

## 玩家护甲韧性 (player_armor_toughness)
返回玩家的总护甲韧性值。
```
{"placeholder":"player_armor_toughness"}
```
示例输出：`8.0`

## 玩家最大护甲值 (max_player_armor)
返回最大护甲值。
```
{"placeholder":"max_player_armor"}
```
示例输出：`20`

## 玩家当前护甲值（百分比） (current_player_armor_percent)
返回玩家护甲百分比。
```
{"placeholder":"current_player_armor_percent"}
```
示例输出：`100`

## 玩家当前氧气值 (current_player_oxygen)
返回玩家当前氧气值（气泡）。
```
{"placeholder":"current_player_oxygen"}
```
示例输出：`300`

## 玩家最大氧气值 (max_player_oxygen)
返回最大氧气值。
```
{"placeholder":"max_player_oxygen"}
```
示例输出：`300`

## 玩家当前氧气值（百分比） (current_player_oxygen_percent)
返回玩家氧气值百分比。
```
{"placeholder":"current_player_oxygen_percent"}
```
示例输出：`100`

## 玩家当前等级 (current_player_level)
返回玩家当前经验等级。
```
{"placeholder":"current_player_level"}
```
示例输出：`30`

## 玩家当前经验值 (current_player_exp)
返回玩家总经验值。
```
{"placeholder":"current_player_exp"}
```
示例输出：`1250`

## 玩家经验进度（百分比） (current_player_exp_progress)
返回玩家距离下一级的经验进度百分比。
```
{"placeholder":"current_player_exp_progress"}
```
示例输出：`75`

## 玩家攻击强度（百分比） (player_attack_strength)
返回玩家的攻击冷却百分比。
```
{"placeholder":"player_attack_strength"}
```
示例输出：`100`

## 玩家游戏模式 (player_gamemode)
返回玩家当前游戏模式。
```
{"placeholder":"player_gamemode"}
```
示例输出：`survival`

## 玩家视角方向 (player_view_direction)
返回玩家当前面向的方向。
```
{"placeholder":"player_view_direction"}
```
示例输出：`north`

## 玩家 X 坐标 (player_x_coordinate)
返回玩家在世界中的 X 坐标。
```
{"placeholder":"player_x_coordinate"}
```
示例输出：`125`

## 玩家 Y 坐标 (player_y_coordinate)
返回玩家在世界中的 Y 坐标。
```
{"placeholder":"player_y_coordinate"}
```
示例输出：`64`

## 玩家 Z 坐标 (player_z_coordinate)
返回玩家在世界中的 Z 坐标。
```
{"placeholder":"player_z_coordinate"}
```
示例输出：`-250`

## 当前坐骑生命值 (current_mount_health)
返回玩家正在骑乘实体的当前生命值。
```
{"placeholder":"current_mount_health"}
```
示例输出：`30.0`

## 坐骑最大生命值 (max_mount_health)
返回玩家正在骑乘实体的最大生命值。
```
{"placeholder":"max_mount_health"}
```
示例输出：`30.0`

## 当前坐骑生命值（百分比） (current_mount_health_percent)
返回坐骑生命值百分比。
```
{"placeholder":"current_mount_health_percent"}
```
示例输出：`100`

## 当前坐骑跳跃能量条（百分比） (current_mount_jump_meter)
返回坐骑跳跃能量条的数值。
```
{"placeholder":"current_mount_jump_meter"}
```
示例输出：`75`

## 当前 Boss 生命值（百分比） (current_boss_health)
返回当前活跃 Boss 的生命值。
```
{"placeholder":"current_boss_health"}
```
示例输出：`150.0`

## Boss 名称 (boss_name)
返回当前活跃 Boss 的名称。
```
{"placeholder":"boss_name","values":{"boss_index":"0","as_json":"false"}}
```
示例输出：`Ender Dragon`

## Boss 数量 (boss_count)
返回当前活跃 Boss 的数量。
```
{"placeholder":"boss_count"}
```
示例输出：`1`

## 活动效果数量 (effects_count)
返回当前激活的药水效果数量。
```
{"placeholder":"effects_count"}
```
示例输出：`3`

## 活动效果 (active_effect)
返回某个特定活动效果的信息。
```
{"placeholder":"active_effect","values":{"effect_index":"0"}}
```
示例输出：`minecraft:speed`

## 已选快捷栏槽位 (active_hotbar_slot)
返回当前选中的快捷栏槽位（0-8）。
```
{"placeholder":"active_hotbar_slot"}
```
示例输出：`4`

## 槽位物品 (slot_item)
返回指定库存槽位中的物品信息。
```
{"placeholder":"slot_item","values":{"slot":"0"}}
```
示例输出：`minecraft:diamond_sword`

## 槽位物品数量 (slot_item_count)
返回指定玩家背包槽位中的物品堆叠数量。
```
{"placeholder":"slot_item_count","values":{"slot":"0"}}
```
示例输出：`64`

## 槽位物品耐久度 (slot_item_durability)
返回指定玩家背包槽位中物品的耐久度信息。
```
{"placeholder":"slot_item_durability","values":{"slot":"0","format":"percentage"}}
```
参数：
- `slot`：玩家背包槽位编号。
- `format`：`current`、`remaining`、`max`、`damage`、`percentage` 或 `percent`。

示例输出：`87`

## 槽位物品显示名称 (slot_item_display_name_fm)
以 JSON 文本组件的形式返回指定槽位中物品的显示名称。在旁观者模式下，快捷栏槽位可能会解析为旁观者菜单物品名称，除非 `ignore_spectator` 为 `true`。
```
{"placeholder":"slot_item_display_name_fm","values":{"slot":"0","ignore_spectator":"false"}}
```
示例输出：`{"text":"Diamond Sword","color":"aqua"}`

## 背包物品总数 (inventory_item_count)
返回玩家背包中某种物品的总数量。如果 `item` 为空，则统计背包中的所有物品堆叠。
```
{"placeholder":"inventory_item_count","values":{"item":"minecraft:diamond"}}
```
示例输出：`12`

## 背包槽位食物恢复量 (inventory_slot_food_point_restore_amount)
返回指定玩家背包槽位中的食物物品可恢复的饥饿值。
```
{"placeholder":"inventory_slot_food_point_restore_amount","values":{"slot":"0"}}
```
示例输出：`4.0`

## 鼠标悬停的背包物品 (hovered_inventory_item)
返回当前在背包界面中鼠标悬停的物品键。
```
{"placeholder":"hovered_inventory_item"}
```
示例输出：`minecraft:apple`

## 世界游戏时间 (game_time)
返回当前游戏内时间刻计数。
```
{"placeholder":"game_time"}
```
示例输出：`18000`

## 世界日期时间 (world_daytime)
返回当前世界的日间时间。
```
{"placeholder":"world_daytime"}
```
示例输出：`13000`

## 世界日期时间小时 (world_daytime_hour)
返回世界时间中的小时部分。默认使用 24 小时制；将 `twelve_hour_format` 设为 `"true"` 可使用 12 小时制。
```
{"placeholder":"world_daytime_hour","values":{"twelve_hour_format":"false"}}
```
示例输出：`12`

## 世界日期时间分钟 (world_daytime_minute)
返回世界时间中的分钟部分（00-59）。
```
{"placeholder":"world_daytime_minute"}
```
示例输出：`30`

## 世界难度 (world_difficulty)
返回当前世界难度。
```
{"placeholder":"world_difficulty"}
```
示例输出：`normal`

## 当前世界种子 (current_world_seed)
返回当前单人世界的种子。若种子不可用，则返回空值。
```
{"placeholder":"current_world_seed"}
```
示例输出：`123456789`

## 当前生物群系 (current_biome)
返回玩家当前所在的生物群系。将 `as_key` 设为 `"false"` 可返回可翻译/显示名称（如果可用）。
```
{"placeholder":"current_biome","values":{"as_key":"true"}}
```
示例输出：`minecraft:plains`

## 当前维度 (current_dimension)
返回玩家当前所在的维度。将 `as_key` 设为 `"false"` 可返回可翻译/显示名称（如果可用）。
```
{"placeholder":"current_dimension","values":{"as_key":"true"}}
```
示例输出：`minecraft:overworld`

## 游戏规则值 (gamerule_value)
返回已加载世界/服务器中某个游戏规则的当前值。服务器世界需要服务器端也安装 FancyMenu。
```
{"placeholder":"gamerule_value","values":{"name":"doDaylightCycle"}}
```
示例输出：`true`

## 物品类别 (item_category)
返回某个物品在创造模式物品栏中的分类。将 `as_key` 设为 `"true"` 可返回分类键而不是显示名称。
```
{"placeholder":"item_category","values":{"item":"minecraft:diamond_sword","as_key":"false"}}
```
示例输出：`Combat`

## 当前 HUD 标题/副标题 (current_title)
返回当前显示的标题文本。
```
{"placeholder":"current_title","values":{"is_subtitle":"false","as_json":"false"}}
```
示例输出：`Game Over!`

## 动作栏消息 (action_bar_message_fm)
返回当前显示在快捷栏上方的原版动作栏消息。
```
{"placeholder":"action_bar_message_fm"}
```
示例输出：`You may not rest now`

## 动作栏消息时间 (action_bar_message_time_fm)
返回当前原版动作栏消息还会显示多少刻。
```
{"placeholder":"action_bar_message_time_fm"}
```
示例输出：`42`

## 摄像机旋转 X (camera_rotation_x_fm)
返回当前摄像机俯仰角（度）。
```
{"placeholder":"camera_rotation_x_fm"}
```
示例输出：`12.5`

## 摄像机旋转 Y (camera_rotation_y_fm)
返回当前摄像机偏航角（度）。
```
{"placeholder":"camera_rotation_y_fm"}
```
示例输出：`-90.0`

## 摄像机旋转 X 变化量 (camera_rotation_delta_x_fm)
返回每刻摄像机俯仰角的变化量。
```
{"placeholder":"camera_rotation_delta_x_fm"}
```
示例输出：`0.4`

## 摄像机旋转 Y 变化量 (camera_rotation_delta_y_fm)
返回每刻摄像机偏航角的变化量。
```
{"placeholder":"camera_rotation_delta_y_fm"}
```
示例输出：`-1.2`

## 高亮物品显示时间 (highlighted_item_time_fm)
返回高亮物品名称还会显示在快捷栏上方多少刻。
```
{"placeholder":"highlighted_item_time_fm"}
```
示例输出：`30`

## 玩家使用物品进度 (player_item_use_progress_fm)
返回当前物品使用进度，范围为 `0.0` 到 `1.0`。
```
{"placeholder":"player_item_use_progress_fm"}
```
示例输出：`0.65`

## 玩家位置 X 变化量 (player_position_delta_x_fm)
返回每刻玩家在 X 轴位置的变化量。
```
{"placeholder":"player_position_delta_x_fm"}
```
示例输出：`0.0`

## 玩家位置 Y 变化量 (player_position_delta_y_fm)
返回每刻玩家在 Y 轴位置的变化量。
```
{"placeholder":"player_position_delta_y_fm"}
```
示例输出：`-0.08`

## 玩家位置 Z 变化量 (player_position_delta_z_fm)
返回每刻玩家在 Z 轴位置的变化量。
```
{"placeholder":"player_position_delta_z_fm"}
```
示例输出：`0.12`

## 当前服务器 IP (current_server_ip)
返回当前连接服务器的 IP。
```
{"placeholder":"current_server_ip"}
```
示例输出：`mc.hypixel.net`

## 世界玩家列表 (world_players_list)
返回当前世界中的所有玩家列表。
```
{"placeholder":"world_players_list","values":{"separator":", "}}
```
示例输出：`Steve, Alex, Notch`

## 服务器 MOTD (servermotd)
返回服务器的每日消息（MOTD）。
```
{"placeholder":"servermotd","values":{"ip":"mc.hypixel.net","line":"1"}}
```
示例输出：`Welcome to Hypixel!`

## 服务器 PING (serverping)
返回到服务器的延迟，单位为毫秒。
```
{"placeholder":"serverping","values":{"ip":"mc.hypixel.net"}}
```
示例输出：`54`

## 服务器玩家数量 (serverplayercount)
返回服务器的玩家数量。
```
{"placeholder":"serverplayercount","values":{"ip":"mc.hypixel.net"}}
```
示例输出：`25000/30000`

## 服务器状态 (serverstatus)
返回服务器在线/离线状态。
```
{"placeholder":"serverstatus","values":{"ip":"mc.hypixel.net"}}
```
示例输出：`§a在线` 或 `§c离线`

## 服务器版本 (serverversion)
返回服务器的 Minecraft 版本。
```
{"placeholder":"serverversion","values":{"ip":"mc.hypixel.net"}}
```
示例输出：`1.19.2`

## 年 (realtimeyear)
返回当前年份。
```
{"placeholder":"realtimeyear"}
```
示例输出：`2024`

## 月 (realtimemonth)
返回当前月份（01-12）。
```
{"placeholder":"realtimemonth"}
```
示例输出：`01`

## 日 (realtimeday)
返回当前月份中的日期（01-31）。
```
{"placeholder":"realtimeday"}
```
示例输出：`27`

## 小时 (realtimehour)
返回当前小时。默认使用 24 小时制；将 `twelve_hour_format` 设为 `"true"` 可使用 12 小时制。
```
{"placeholder":"realtimehour","values":{"twelve_hour_format":"false","timezone":"system"}}
```
示例输出：`14`

## 分钟 (realtimeminute)
返回当前分钟（00-59）。
```
{"placeholder":"realtimeminute"}
```
示例输出：`30`

## 秒 (realtimesecond)
返回当前秒数（00-59）。
```
{"placeholder":"realtimesecond"}
```
示例输出：`45`

## 当前时间毫秒数（Unix 时间戳） (unix_time)
返回当前 Unix 时间戳，单位为毫秒。
```
{"placeholder":"unix_time"}
```
示例输出：`1716552478123`

> 实时时间占位符（`realtimeyear`、`realtimemonth`、`realtimeday`、`realtimehour`、`realtimeminute`、`realtimesecond` 和 `unix_time`）支持 `timezone` 值。请使用常规 Java 时区 ID，例如 `UTC`、`Europe/Berlin` 或 `America/New_York`；如果省略或使用 `system`，则使用系统时区。
{.is-info}

## CPU 信息 (cpuinfo)
返回 CPU 的信息。
```
{"placeholder":"cpuinfo"}
```
示例输出：`Intel(R) Core(TM) i7-10700K CPU @ 3.80GHz`

## CPU 使用率（JVM） (jvmcpu)
返回 JVM 的 CPU 使用率百分比。
```
{"placeholder":"jvmcpu"}
```
示例输出：`25.5`

## CPU 使用率（系统） (oscpu)
返回操作系统的 CPU 使用率百分比。
```
{"placeholder":"oscpu"}
```
示例输出：`42.8`

## GPU 信息 (gpuinfo)
返回 GPU 的信息。
```
{"placeholder":"gpuinfo"}
```
示例输出：`NVIDIA GeForce RTX 3080`

## Java 版本 (javaver)
返回 Java 版本。
```
{"placeholder":"javaver"}
```
示例输出：`17.0.2`

## Java 虚拟机 (jvmname)
返回 Java 虚拟机的名称。
```
{"placeholder":"jvmname"}
```
示例输出：`OpenJDK 64-Bit Server VM`

## OpenGL 版本 (glver)
返回 OpenGL 版本。
```
{"placeholder":"glver"}
```
示例输出：`4.6.0 NVIDIA 516.94`

## 操作系统名称 (osname)
返回操作系统名称。
```
{"placeholder":"osname"}
```
示例输出：`Windows 10`

## FPS（每秒帧数） (fps)
返回当前每秒帧数。
```
{"placeholder":"fps"}
```
示例输出：`120`

## 已使用内存 MB (usedram)
返回当前正在使用的内存量（MB）。
```
{"placeholder":"usedram"}
```
示例输出：`4096`

## 最大内存 MB (maxram)
返回分配的最大内存量（MB）。
```
{"placeholder":"maxram"}
```
示例输出：`8192`

## 已使用内存百分比 (percentram)
返回当前已使用内存的百分比。
```
{"placeholder":"percentram"}
```
示例输出：`50`

## 音频元素音量 (audio_element_vol)
返回某个音频元素的音量。
```
{"placeholder":"audio_element_vol","values":{"element_identifier":"background_music"}}
```
示例输出：`0.5`

## 当前音轨 (audio_element_current_track)
返回某个音频元素的音轨名称。
```
{"placeholder":"audio_element_current_track","values":{"element_identifier":"background_music","display_name_mappings":"track1.ogg=>Cool Track Name"}}
```
示例输出：`Cool Track Name`

## 音频时长 (audio_duration)
返回音轨总时长，格式为 MM:SS。
```
{"placeholder":"audio_duration","values":{"element_identifier":"background_music"}}
```
示例输出：`03:45`

## 音频播放时间 (audio_playtime)
返回音轨当前播放时间。将 `show_percentage` 设为 `"true"` 可返回 0-100 的进度值，而不是 `MM:SS`。
```
{"placeholder":"audio_playtime","values":{"element_identifier":"background_music","show_percentage":"false"}}
```
示例输出：`01:30`（或者当 `show_percentage` 为 `"true"` 时为 `45`）

## 音频播放状态 (audio_playing_state)
返回某个音频元素是否正在播放（true/false）。
```
{"placeholder":"audio_playing_state","values":{"element_identifier":"background_music"}}
```
示例输出：`true`

## 视频元素音量 (video_element_vol)
返回某个视频元素的音量级别（0.0 到 1.0）。
```
{"placeholder":"video_element_vol","values":{"element_identifier":"my_video_element"}}
```
示例输出：`0.5`

## 视频元素时长 (video_element_duration)
返回视频元素总时长，格式为 `MM:SS`。将 `output_as_timestamp` 设为 `"true"` 可返回毫秒时间戳。
```
{"placeholder":"video_element_duration","values":{"element_identifier":"my_video_element","output_as_timestamp":"false"}}
```
示例输出：`02:00`（或者当 `output_as_timestamp` 为 `"true"` 时为 `120000`）

## 视频元素播放时间 (video_element_playtime)
返回视频元素当前播放时间（进度），格式为 `MM:SS`。将 `show_percentage` 设为 `"true"` 可返回 0-100 的进度值，或将 `output_as_timestamp` 设为 `"true"` 返回毫秒数。
```
{"placeholder":"video_element_playtime","values":{"element_identifier":"my_video_element","show_percentage":"false","output_as_timestamp":"false"}}
```
示例输出：`00:45`（或者百分比 `38`，或者时间戳 `45200`）

## 视频元素暂停状态 (video_element_paused_state)
返回某个视频元素是否已暂停（true/false）。
```
{"placeholder":"video_element_paused_state","values":{"element_identifier":"my_video_element"}}
```
示例输出：`false`

## 视频背景音量 (video_background_vol)
返回视频菜单背景的音量级别（0.0 到 1.0）。
```
{"placeholder":"video_background_vol","values":{"background_identifier":"main_menu_video"}}
```
示例输出：`0.7`

## 视频背景时长 (video_background_duration)
返回视频菜单背景总时长，格式为 `MM:SS`。将 `output_as_timestamp` 设为 `"true"` 可返回毫秒时间戳。
```
{"placeholder":"video_background_duration","values":{"background_identifier":"main_menu_video","output_as_timestamp":"false"}}
```
示例输出：`03:00`（或者当 `output_as_timestamp` 为 `"true"` 时为 `180000`）

## 视频背景播放时间 (video_background_playtime)
返回视频菜单背景当前播放时间（进度），格式为 `MM:SS`。将 `show_percentage` 设为 `"true"` 可返回 0-100 的进度值，或将 `output_as_timestamp` 设为 `"true"` 返回毫秒数。
```
{"placeholder":"video_background_playtime","values":{"background_identifier":"main_menu_video","show_percentage":"false","output_as_timestamp":"false"}}
```
示例输出：`01:00`（或者百分比 `33`，或者时间戳 `60500`）

## 视频背景暂停状态 (video_background_paused_state)
返回视频菜单背景是否已暂停（true/false）。
```
{"placeholder":"video_background_paused_state","values":{"background_identifier":"main_menu_video"}}
```
示例输出：`true`

## 计算器 (calc)
计算器占位符是一个强大的工具，允许你在布局中执行数学计算。它支持广泛的数学运算，并且可用于小数和整数。

### 基本语法
```
{"placeholder":"calc","values":{"decimal":"true/false","expression":"your_expression"}}
```

计算器有两个主要参数：
- `decimal`：决定结果是否包含小数位（`true`）或四舍五入为整数（`false`）
- `expression`：要计算的数学表达式

### 支持的运算
计算器支持以下数学运算：
- 基本运算：`+`（加）、`-`（减）、`*`（乘）、`/`（除）
- 括号：`( )` 用于分组运算
- 幂运算：`^`
- 平方根：`sqrt()`
- 三角函数：`sin()`、`cos()`、`tan()`
- 数学常量：`pi`、`e`
- 绝对值：`abs()`
- 对数：`log()`、`ln()`

## 随机数 (random_number)
生成指定范围内的随机数。
```
{"placeholder":"random_number","values":{"min":"1","max":"100"}}
```
示例输出：`42`

## 最大值 (maxnum)
返回两个数中较大的那个。
```
{"placeholder":"maxnum","values":{"first":"10","second":"20"}}
```
示例输出：`20`

## 最小值 (minnum)
返回两个数中较小的那个。
```
{"placeholder":"minnum","values":{"first":"10","second":"20"}}
```
示例输出：`10`

## 绝对值 (absnum)
返回一个数的绝对值。
```
{"placeholder":"absnum","values":{"num":"-10.5"}}
```
示例输出：`10.5`

## 取负数 (negnum)
返回一个数的相反数。
```
{"placeholder":"negnum","values":{"num":"10.5"}}
```
示例输出：`-10.5`

## *pi*（数学） (math_pi)
返回 π 的值。
```
{"placeholder":"math_pi"}
```
示例输出：`3.141592653589793`

## 正弦（数学） (math_sin)
返回某个角度的正弦值。
```
{"placeholder":"math_sin","values":{"angle":"45"}}
```
示例输出：`0.7071067811865476`

## 余弦（数学） (math_cos)
返回某个角度的余弦值。
```
{"placeholder":"math_cos","values":{"angle":"45"}}
```
示例输出：`0.7071067811865476`

## 正切（数学） (math_tan)
返回某个角度的正切值。
```
{"placeholder":"math_tan","values":{"angle":"45"}}
```
示例输出：`1.0`

## 向下取整（数学） (math_floor)
将数字向下舍入到最接近的整数。
```
{"placeholder":"math_floor","values":{"num":"3.14"}}
```
示例输出：`3`

## 向上取整（数学） (math_ceil)
将数字向上舍入到最接近的整数。
```
{"placeholder":"math_ceil","values":{"num":"3.14"}}
```
示例输出：`4`

## 四舍五入（数学） (math_round)
对数字进行四舍五入。默认四舍五入到最接近的整数；将 `decimals` 设置为非负数，可四舍五入到相应的小数位数。
```
{"placeholder":"math_round","values":{"num":"3.14159","decimals":"2"}}
```
示例输出：`3.14`（当 `decimals:-1` 或省略时 → `3`）

## 符号（数学） (math_sign)
返回数字的符号（正数为 1，负数为 -1，零为 0）。
```
{"placeholder":"math_sign","values":{"num":"-3.14"}}
```
示例输出：`-1`

## 双曲正弦（数学） (math_sinh)
返回某个角度的双曲正弦值。
```
{"placeholder":"math_sinh","values":{"angle":"1"}}
```
示例输出：`1.1752011936438014`

## 双曲余弦（数学） (math_cosh)
返回某个角度的双曲余弦值。
```
{"placeholder":"math_cosh","values":{"angle":"1"}}
```
示例输出：`1.5430806348152437`

## 双曲正切（数学） (math_tanh)
返回某个角度的双曲正切值。
```
{"placeholder":"math_tanh","values":{"angle":"1"}}
```
示例输出：`0.7615941559557649`

## 分割文本 (split_text)
使用指定分隔符分割文本。
```
{"placeholder":"split_text","values":{"input":"hello,world","regex":",","max_parts":"2","split_index":"1"}}
```
示例输出：`world`

## 去除文本首尾空白 (trim_text)
移除开头和结尾的空白字符。
```
{"placeholder":"trim_text","values":{"text":"  hello world  "}}
```
示例输出：`hello world`

## 裁剪文本 (crop_text)
移除文本开头和结尾的字符。
```
{"placeholder":"crop_text","values":{"text":"hello world","remove_from_start":"1","remove_from_end":"1"}}
```
示例输出：`ello worl`

## 字符串化 (stringify)
通过转义所有语法字符将文本字符串化。
```
{"placeholder":"stringify","values":{"text":"text with {special} \"characters\""}}
```
示例输出：`text with \{special\} \"characters\"`

## 本地化文本 (local)
获取某个键对应的本地化文本。
```
{"placeholder":"local","values":{"key":"menu.singleplayer"}}
```
示例输出：`Singleplayer`

## 网络文本 (webtext)
从网页 URL 获取文本内容。
```
{"placeholder":"webtext","values":{"link":"http://somewebsite.com/textfile.txt"}}
```
示例输出：URL 中的文本内容

## 随机文本 (randomtext)
从文本文件、URL 或直接输入的纯文本中返回一行随机文本。文本会按指定间隔变化。
```
{"placeholder":"randomtext","values":{"source":"/config/fancymenu/assets/<file_name.txt>","interval":"10"}}
```
参数：
- `source`：文本行的来源（替代旧的 `path` 参数）
  - 文件路径：`/config/fancymenu/assets/quotes.txt`
  - URL：`https://example.com/quotes.txt`
  - 纯文本：`Line 1\nLine 2\nLine 3`
- `interval`：文本变化之间的时间，单位为秒

该占位符现在支持三种来源类型：
1. **本地文件**：来自游戏目录中的文本文件
   ```
   {"placeholder":"randomtext","values":{"source":"/config/fancymenu/assets/quotes.txt","interval":"10"}}
   ```
2. **URL**：来自互联网的远程文本文件
   ```
   {"placeholder":"randomtext","values":{"source":"https://example.com/quotes.txt","interval":"10"}}
   ```
3. **纯文本**：直接输入的文本，行与行之间用 `\n` 分隔
   ```
   {"placeholder":"randomtext","values":{"source":"First line\nSecond line\nThird line","interval":"5"}}
   ```

注意：使用 `path` 而不是 `source` 的旧占位符仍然可以正常工作。

## JSON 解析器 (json)
从文件、URL 或直接 JSON 内容中解析 JSON 数据，并使用 JSON 路径表达式提取值。
```
{"placeholder":"json","values":{"source":"path_or_link_or_json_content","json_path":"$.some.json.path"}}
```
参数：
- `source`：JSON 数据的来源
  - 文件路径：`/config/fancymenu/assets/data.json`
  - URL：`https://api.example.com/data.json`
  - 直接 JSON：`{"name":"Steve","level":42}`
- `json_path`：用于提取数据的 JSON 路径表达式

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

JSON 路径示例：
- `$.name` - 获取根节点中的 "name" 字段
- `$.player.level` - 获取 "player" 内嵌的 "level" 字段
- `$.items[0].id` - 获取数组中第一个物品的 "id"
- `$.scores.*` - 获取 "scores" 对象中的所有值

## 绝对文件/文件夹路径 (absolute_path)
返回文件的绝对路径。
```
{"placeholder":"absolute_path","values":{"short_path":"relative/path/to/file.txt"}}
```
示例输出：`C:/Users/Username/AppData/Roaming/.minecraft/relative/path/to/file.txt`

## 文本字符数 (text_character_count)
返回给定文本中的字符数量。
```
{"placeholder":"text_character_count","values":{"text":"Hello World!"}}
```
示例输出：`12`

## 文本宽度 (text_width)
返回给定文本渲染后的像素宽度。
```
{"placeholder":"text_width","values":{"text":"Hello World!"}}
```
示例输出：`66`

## 转为大写文本 (uppercase_text)
将输入文本转换为全大写字母。
```
{"placeholder":"uppercase_text","values":{"text":"Hello World"}}
```
示例输出：`HELLO WORLD`

## 转为小写文本 (lowercase_text)
将输入文本转换为全小写字母。
```
{"placeholder":"lowercase_text","values":{"text":"Hello World"}}
```
示例输出：`hello world`

## 标题式文本 (title_case_text)
将输入文本转换为标题格式。
```
{"placeholder":"title_case_text","values":{"text":"hello world"}}
```
示例输出：`Hello World`

## 句首大写文本 (sentence_case_text)
将输入文本转换为句首大写格式。
```
{"placeholder":"sentence_case_text","values":{"text":"hello world. this is fancymenu!"}}
```
示例输出：`Hello world. This is fancymenu!`

## 蛇形命名文本 (snake_case_text)
将输入文本转换为 `snake_case`。
```
{"placeholder":"snake_case_text","values":{"text":"Hello World"}}
```
示例输出：`hello_world`

## 连字符命名文本 (kebab_case_text)
将输入文本转换为 `kebab-case`。
```
{"placeholder":"kebab_case_text","values":{"text":"Hello World"}}
```
示例输出：`hello-world`

## 交替大小写文本 (alternating_case_text)
将输入文本转换为交替大小写。
```
{"placeholder":"alternating_case_text","values":{"text":"alternating case"}}
```
示例输出：`aLtErNaTiNg CaSe`

## 大小写切换文本 (toggle_case_text)
切换输入文本中每个字母的大小写。
```
{"placeholder":"toggle_case_text","values":{"text":"Toggle Case"}}
```
示例输出：`tOGGLE cASE`

## 编码为 Base64 (base64_encode)
将给定文本编码为 Base64。
```
{"placeholder":"base64_encode","values":{"text":"Hello World"}}
```
示例输出：`SGVsbG8gV29ybGQ=`

## 从 Base64 解码 (base64_decode)
将 Base64 字符串解码回纯文本。
```
{"placeholder":"base64_decode","values":{"text":"SGVsbG8gV29ybGQ="}}
```
示例输出：`Hello World`

## 文件文本 (file_text)
返回文件或 URL 中的文本行。可以返回全部行或仅返回最后 X 行。
```
{"placeholder":"file_text","values":{"path_or_url":"/config/fancymenu/assets/some_file.txt","mode":"all","separator":"\n","last_lines":"1"}}
```
参数：
- `path_or_url`：要读取的文件路径或 URL
- `mode`：`"all"`（返回全部行）或 `"last"`（仅返回最后 X 行）
- `separator`：用于连接各行的文本（默认：`"\n"`）
- `last_lines`：当模式为 `"last"` 时返回的行数（默认：`"1"`）

示例输出：取决于文件内容

## 剪贴板内容 (clipboard_content)
返回当前系统剪贴板中的文本内容。
```
{"placeholder":"clipboard_content"}
```
示例输出：剪贴板中当前的任何文本

## 替换文本 (replace_text)
使用字面文本或正则表达式替换字符串中的文本。
```
{"placeholder":"replace_text","values":{"text":"Hello World! This is a test.","search":"World","replacement":"FancyMenu","use_regex":"false","replace_all":"true"}}
```
参数：
- `text`：要处理的输入文本
- `search`：要搜索的文本或正则模式
- `replacement`：替换文本
- `use_regex`：是否使用正则表达式（`"true"`）还是字面匹配（`"false"`）
- `replace_all`：替换所有匹配项（`"true"`）还是仅替换第一个（`"false"`）

示例输出：`Hello FancyMenu! This is a test.`

## 分支选择 (switch_case)
根据某个值执行 switch-case 操作。
```
{"placeholder":"switch_case","values":{"value":"1","cases":"1:first case,2:second case,3:third case","default":"default case"}}
```
示例输出：`first case`（如果 value 为 1）

## 获取变量值（FM 变量） (getvariable)
检索之前存储的变量值。
```
{"placeholder":"getvariable","values":{"name":"some_variable"}}
```
示例输出：取决于存储的值

## 获取 NBT 数据 (nbt_data_get)
在客户端检索 NBT 数据（类似 `/data get` 命令）。当连接到服务器并需要权威的服务器端值时，请使用服务器变体 `nbt_data_get_server`。
```
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"foodLevel","scale":"1.0","return_type":"value"}}
```
参数：
- `source_type`：`"entity"` 或 `"block"`
- `entity_selector`：实体选择器，如 `@s`、`@p`、`@e`，或者 UUID/名称（用于实体）
- `block_pos`：方块位置，格式为 `"x y z"`（用于方块）
- `nbt_path`：要检索的 NBT 路径
- `scale`：数值的可选缩放因子（默认：`"1.0"`）
- `return_type`：返回数据的方式：
  - `"value"`：默认，返回值（数值可按需缩放）
  - `"string"`：返回实际 NBT 数据字符串
  - `"snbt"`：以 SNBT（格式化 NBT）形式返回
  - `"json"`：以 JSON 格式的组件返回（用于复合标签）

示例输出：`20`（饥饿值）

## 获取 NBT 数据（服务器端） (nbt_data_get_server)
在服务器端查询 NBT 数据（通过数据包），并短暂缓存结果。返回值与客户端占位符一致。
```
{"placeholder":"nbt_data_get_server","values":{"source_type":"entity","entity_selector":"@s","block_pos":"","storage_id":"minecraft:storage_key","nbt_path":"SelectedItem.id","scale":"1.0","return_type":"value"}}
```
示例输出：`minecraft:diamond_sword`

## 上一次死亡消息 (lastdeathmessage)
返回客户端玩家上一次记录的死亡消息。将 `as_json_component` 设为 `"true"` 可获取原始 JSON 文本组件。
```
{"placeholder":"lastdeathmessage","values":{"as_json_component":"false"}}
```
示例输出：`Steve was slain by Zombie`

## 运行时长 (uptime_duration)
返回 FancyMenu 已加载了多长时间。默认值单位为秒；将 `output_as_millis` 设为 `"true"` 可返回毫秒。
```
{"placeholder":"uptime_duration","values":{"output_as_millis":"false"}}
```
示例输出：`742`（加载后的秒数）

## 世界存档名称 (level_save_names)
列出所有本地世界存档名称，并使用所选分隔符连接。运行于客户端线程。
```
{"placeholder":"level_save_names","values":{"separator":", "}}
```
示例输出：`Creative Test, Survival World, Hardcore`

## 世界存档数据 (level_save_data)
返回指定世界名称的序列化世界数据（必须与存档列表中显示的名称匹配）。
```
{"placeholder":"level_save_data","values":{"level_name":"Survival World"}}
```
示例输出：`{"name":"Survival World","gameMode":"survival",...}`

## 数字进制转换器 (number_base_convert)
将数字（整数或小数）从一种进制转换到另一种进制（2–36）。如果未提供进制，默认使用十进制。
```
{"placeholder":"number_base_convert","values":{"input":"67.5","from_base":"10","to_base":"16"}}
```
示例输出：`43.8`

## 文件大小 (file_size)
返回本地文件的大小，单位为字节。仅允许本地路径。
```
{"placeholder":"file_size","values":{"path":"/config/fancymenu/assets/notes.txt"}}
```
示例输出：`1284`

## 文件 MD5 (file_md5)
返回本地文件的 MD5 哈希值，格式为小写十六进制字符串。
```
{"placeholder":"file_md5","values":{"path":"/config/fancymenu/assets/notes.txt"}}
```
示例输出：`d41d8cd98f00b204e9800998ecf8427e`

# 实用示例

## 创建动态内存显示
```
已用内存：{"placeholder":"usedram"}MB / {"placeholder":"maxram"}MB ({"placeholder":"percentram"}%)
```

## 制作实时时钟
```
{"placeholder":"realtimehour"}:{"placeholder":"realtimeminute"}:{"placeholder":"realtimesecond"}
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
生命值：{"placeholder":"current_player_health"} / {"placeholder":"max_player_health"} ({"placeholder":"current_player_health_percent"}%)
护甲：{"placeholder":"current_player_armor"} / {"placeholder":"max_player_armor"}
经验等级：{"placeholder":"current_player_level"}
```

## 使用嵌套占位符的复杂计算
```
{"placeholder":"calc","values":{"decimal":"true","expression":"({"placeholder":"usedram"} / {"placeholder":"maxram"}) * 100"}}
```

## 带四舍五入的坐标显示
```
X：{"placeholder":"math_round","values":{"num":"{"placeholder":"player_x_coordinate"}"}}
Y：{"placeholder":"math_round","values":{"num":"{"placeholder":"player_y_coordinate"}"}}
Z：{"placeholder":"math_round","values":{"num":"{"placeholder":"player_z_coordinate"}"}}
```

# 最佳实践

1. **缓存耗时操作**：某些占位符（例如读取系统信息的占位符）可能比较消耗资源。如果你需要多次使用它们，可以考虑使用变量来存储其值。

2. **使用合适的小数设置**：在进行计算时，请正确使用 `decimal` 参数。需要整数时设为 `false`，需要精确小数时设为 `true`。

3. **处理缺失值**：始终考虑占位符没有返回值时应如何处理。在这种情况下，你可能需要提供默认值。

4. **测试性能**：当使用大量占位符或复杂的嵌套结构时，请测试其对性能的影响，尤其是在低端系统上。

5. **使用高级尺寸/定位**：对于动态 UI 元素，将占位符与高级尺寸和定位结合起来，以创建响应式布局。

6. **与变量结合使用**：将占位符与变量结合起来，可以创建更动态的内容，并通过动作进行更新。

# 常见问题与解决方案

## 占位符未更新
如果占位符的值没有按预期更新，请检查：
- 占位符格式是否正确
- 是否为占位符 ID 使用了正确的大小写
- 占位符是否需要特定条件才能更新

## 嵌套占位符无法工作
当嵌套占位符时：
- 确保引号转义正确
- 确认每个嵌套占位符本身都是有效的

## 性能问题
如果你注意到性能问题：
- 减少使用的占位符数量
- 避免不必要的嵌套
- 考虑将经常访问的值存储为变量
- 根据需要使用合适的占位符（例如，当静态值足够时，不要使用实时时间占位符）
