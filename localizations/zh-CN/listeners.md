---
title: 监听器
description: 如何在 FancyMenu 中创建和使用监听器。
---

# 监听器

监听器会在特定事件发生时运行 [动作脚本](./action-scripts)。它们不依赖于已打开的界面，因此在游玩或加载时也可以运行。

监听器可以向其动作和条件提供 `$$` 值，例如按下的按键或点击的鼠标按钮。

> [!CAUTION]
> 监听器可以在没有打开界面的情况下运行文件、网络、命令、剪贴板、资源包或链接类动作。只从你信任的来源导入监听器。

# 使用监听器

在布局编辑器之外，打开 **菜单栏 -> 自定义 -> 管理监听器** 来创建或编辑监听器。

<img src="https://github.com/Keksuccino/FancyMenu/blob/master/assets/docs/manage_listeners.png?raw=true" alt="管理监听器" style="max-width:800px;width:100%;height:auto;">

# 监听器变量

监听器可以向其动作和条件提供只读值。请在受支持的文本字段中使用它们的 `$$` 名称。

例如，将 [**按下键盘按键时**](#on-keyboard-key-pressed-keyboard_key_pressed) 与 [**打印到游戏日志** 动作](./action-scripts#print-to-game-log-print_to_log) 配合使用。值 `Key pressed! The key is: $$key_name` 会插入被按下按键的名称。

> [!WARNING]
> 监听器变量与 FancyMenu 的 [存储变量](./variables) 是分开的。存储变量的动作、条件和占位符不能与 `$$` 值一起使用。

监听器变量名区分大小写，并且只在该监听器的脚本内部有效。

将来自聊天、远程服务器、文件和用户输入的值视为不可信。不要将它们直接插入路径、URL 或命令中。

监听器变量都是字符串。当信息不可用时，监听器可能会返回文档中定义的哨兵值，例如 `ERROR`、`UNKNOWN`、`NONE`、`EMPTY`、`0`、`-1` 或空字符串。请在将监听器数据插入路径、命令或 URL 前先测试这些值。

# 详细监听器

本节列出 FancyMenu 的内置监听器。

## Markdown 文本被点击时 (`text_clicked`)
- 当 [带有 `click:` 事件的 Markdown 文本](./text-formatting#click-and-hover-events) 被点击时触发，例如 `[Open](click:open_menu)`。
- 变量：
  - `$$text_event_id` – 来自 Markdown 链接的事件 ID

## Markdown 文本被悬停时 (`text_hovered`)
- 当 [带有 `hover:` 事件的 Markdown 文本](./text-formatting#click-and-hover-events) 被悬停时触发，例如 `[Hint](hover:show_hint)`。
- 变量：
  - `$$text_event_id` – 来自 Markdown 链接的事件 ID

## 通过动作解压 ZIP 后 (`zip_extracted_via_action`)
- 在 [**在游戏目录中解压 ZIP 文件** 动作](./action-scripts#extract-zip-file-in-game-directory-extract_zip_file_in_game_dir) 完成后触发。
- 变量：
  - `$$source_zip_path` – 规范化后的用户可见源路径；游戏目录路径可能返回为 `/...`，而常规 Minecraft 目录路径可能使用 `.minecraft/...`
  - `$$target_folder_path` – 使用相同路径形式的规范化用户可见目标路径
  - `$$extract_succeeded` – true/false
  - `$$failure_reason` – 解压失败时的错误文本

## 元素通过动作生成时 (`element_spawned_via_action`)
- 当受支持的 FancyMenu 功能或附加组件动态生成一个元素实例时触发。
- 变量：
  - `$$element_type` – 生成的元素类型
  - `$$element_identifier` – 生成的元素标识符
  - `$$target_screen` – 目标界面标识符

## 动画纹理开始播放时 (`animated_texture_started_playing`)
- 当一个 [动画纹理](./fma) 开始播放时触发。
- 变量：
  - `$$texture_source` – 纹理来源
  - `$$texture_source_type` – 来源类型
  - `$$texture_will_restart` – true/false

## 动画纹理播放结束时 (`animated_texture_finished_playing`)
- 当动画纹理播放结束时触发。
- 变量：
  - `$$texture_source`
  - `$$texture_source_type`
  - `$$texture_will_restart`

## 视频播放状态改变时 (`video_playback_status_changed`)
- 当 [视频元素或菜单背景](./video) 的播放状态发生变化时触发。
- 变量：
  - `$$video_source` – 视频来源
  - `$$video_source_type` – 来源类型
  - `$$is_looping` – true/false
  - `$$new_status` – `PLAYING`、`STOPPED`、`PAUSED` 或 `FINISHED`

## 聊天中收到系统消息时 (`system_message_received_in_chat`)
- 当客户端收到系统聊天消息时触发，例如命令反馈。
- 变量：
  - `$$system_message_string` – 纯文本消息
  - `$$system_message_component` – JSON 组件

## 收到 FM 数据时 (`fm_data_received`)
- 当服务器通过 `/fmdata send` 向此客户端发送 [FM 数据](./fm-data) 时触发。
- 变量：
  - `$$data_identifier` – 数据标识字符串
  - `$$data` – 数据载荷
  - `$$sent_by` – 服务器 IP 或 `integrated_server`

## 远程服务器连接成功时 (`remote_server_connected`)
- 当 [远程服务器连接](./remote-server-communication) 成功建立后触发。
- 变量：
  - `$$request_id` – 缓存的请求 ID
  - `$$remote_server_url` – 远程服务器 URL

## 收到远程服务器数据时 (`remote_server_data_received`)
- 当从已连接的远程服务器收到文本数据时触发。
- 变量：
  - `$$request_id` – 请求 ID
  - `$$remote_server_url` – 远程服务器 URL
  - `$$data` – 接收到的载荷

## 远程服务器连接关闭时 (`remote_server_connection_closed`)
- 当远程服务器连接关闭时触发。
- 变量：
  - `$$request_id` – 请求 ID
  - `$$remote_server_url` – 远程服务器 URL
  - `$$intentionally_closed` – 如果由动作关闭则为 TRUE
  - `$$crashed` – 如果连接意外崩溃则为 TRUE
  - `$$unknown_close_reason` – 如果没有可用的已知关闭原因则为 TRUE

## 按下键盘按键时 (`keyboard_key_pressed`)
- 每当按键被按下时触发（按住时会重复；在界面和游戏中均可工作）。
- 变量：
  - `$$key_name` – 按键的显示名称
  - `$$key_keycode` – GLFW 键码
  - `$$key_scancode` – GLFW 扫描码
  - `$$key_modifiers` – 当前修饰键位掩码

## 松开键盘按键时 (`keyboard_key_released`)
- 当按键被松开时触发（界面和游戏中均可工作）。
- 变量：
  - `$$key_name`
  - `$$key_keycode`
  - `$$key_scancode`
  - `$$key_modifiers`

## 在界面中输入键盘字符时 (`keyboard_char_typed`)
- 当界面打开时输入字符会触发。
- 变量：
  - `$$char` – 输入的字符

## 在界面中移动鼠标时 (`mouse_moved`)
- 当界面打开时鼠标移动会触发。
- 变量：
  - `$$mouse_pos_x` – 当前 X
  - `$$mouse_pos_y` – 当前 Y
  - `$$mouse_move_delta_x` – 距离上次事件的 X 变化量
  - `$$mouse_move_delta_y` – 距离上次事件的 Y 变化量

## 鼠标按钮被点击时 (`mouse_button_clicked`)
- 当鼠标按钮被按下时触发（界面和游戏中均可工作）。
- 变量：
  - `$$button` – 左键/右键/中键
  - `$$mouse_pos_x` – 当前 X
  - `$$mouse_pos_y` – 当前 Y

## 鼠标按钮被松开时 (`mouse_button_released`)
- 当鼠标按钮被松开时触发（界面和游戏中均可工作）。
- 变量：
  - `$$button`
  - `$$mouse_pos_x`
  - `$$mouse_pos_y`

## 在界面中滚动鼠标时 (`mouse_scrolled`)
- 当界面打开时滚动鼠标滚轮会触发。
- 变量：
  - `$$scroll_delta_y` – 垂直滚动量

## 界面打开时 (`screen_open`)
- 在任何界面变为活动状态后立即运行；可用于覆盖它。
- 变量：
  - `$$screen_identifier` – 已打开界面的标识符

## 界面关闭时 (`screen_close`)
- 在界面关闭后立即运行。
- 变量：
  - `$$screen_identifier` – 已关闭界面的标识符

## 退出 Minecraft 时 (`quit_minecraft`)
- 客户端开始关闭时触发一次。
- 变量：
  - `$$timestamp_millis` – 退出时的纪元毫秒时间戳
  - `$$timestamp_iso` – 退出时刻的 ISO-8601 时间戳

## 死亡时 (`player_death`)
- 当本地玩家打开原版死亡界面时运行。
- 变量：
  - `$$days_survived` – 距离上次死亡的天数
  - `$$death_reason_string` – 纯文本原因
  - `$$death_reason_component` – JSON 组件原因
  - `$$death_pos_x` – 死亡时 X 坐标
  - `$$death_pos_y` – 死亡时 Y 坐标
  - `$$death_pos_z` – 死亡时 Z 坐标

## FM 变量更新时 (`fm_variable_updated`)
- 每当 [FancyMenu 变量](./variables) 被设置或更新时触发。
- 变量：
  - `$$var_name` – 变量名
  - `$$old_value` – 旧值
  - `$$new_value` – 新值

## 通过动作下载文件后 (`file_downloaded_via_action`)
- 在 [**下载文件到游戏目录** 动作](./action-scripts#download-file-to-game-directory-download_file_to_game_dir) 完成后触发。
- 变量：
  - `$$download_url` – 下载来源
  - `$$target_file_path` – 成功时保存的文件路径；失败时，这里可能只包含目标目录，因为未解析出最终文件名
  - `$$download_succeeded` – true/false

## 文件被选择时 (`file_selected_via_action`)
- 在 [**从系统中选择文件** 动作](./action-scripts#select-file-from-system-select_file_to_game_dir) 完成后触发。
- 变量：
  - `$$selected_file_path` – 选中的绝对文件路径；若取消则为空
  - `$$target_file_path` – 实例内解析后的路径
  - `$$selection_succeeded` – 如果复制成功则为 true
  - `$$selection_cancelled` – 如果对话框关闭则为 true
  - `$$failure_reason` – 失败时的错误信息

## 收到聊天消息时 (`chat_message_received`)
- 当客户端出现一条普通玩家聊天消息时触发。
- 变量：
  - `$$chat_message_string` – 纯文本行
  - `$$chat_message_component` – 完整的 JSON 组件
  - `$$sender_uuid` – 发送者 UUID 或 ERROR
  - `$$sender_name` – 发送者名称或 ERROR

## 发送聊天消息时 (`chat_message_sent`)
- 当本地玩家发送聊天消息时触发。
- 变量：
  - `$$chat_message_string` – 纯文本行
  - `$$chat_message_component` – 完整的 JSON 组件

## 获得效果时 (`effect_gained`)
- 当玩家获得状态效果时触发。
- 变量：
  - `$$effect_key` – 效果资源位置
  - `$$effect_type` – 正面/负面/中性
  - `$$effect_duration` – 剩余 ticks

## 效果失去时 (`effect_lost`)
- 当玩家失去状态效果时触发。
- 变量：
  - `$$effect_key` – 已过期的效果
  - `$$effect_type` – 类别

## 经验变化时 (`experience_changed`)
- 每当玩家总经验变化时触发。
- 变量：
  - `$$new_experience_amount` – 变化后
  - `$$old_experience_amount` – 变化前
  - `$$is_level_up` – 如果等级提升则为 TRUE

## 受到伤害时 (`damage_taken`)
- 当玩家受到伤害时，每次命中触发一次。
- 变量：
  - `$$damage_amount` – 扣除的生命值
  - `$$damage_type` – 伤害类型资源位置
  - `$$is_fatal_damage` – 如果致命则为 TRUE
  - `$$damage_source` – 攻击者资源位置或 NONE

## 开始冻结时 (`started_freezing`)
- 当玩家开始冻结时触发。
- 变量：
  - `$$freezing_intensity` – 0.0 表示未冻结，1.0 表示完全冻结

## 停止冻结时 (`stopped_freezing`)
- 当玩家停止冻结时触发。
- 变量：
  - （无）

## 完全冻结时 (`fully_frozen`)
- 当玩家变为完全冻结时触发一次。
- 变量：
  - （无）

## 开始看向方块时 (`start_looking_at_block`)
- 当准星首次指向一个方块时触发一次（最大 20 格距离）。
- 变量：
  - `$$block_key` – 目标方块
  - `$$block_pos_x` – 方块 X
  - `$$block_pos_y` – 方块 Y
  - `$$block_pos_z` – 方块 Z
  - `$$distance_to_player` – 从眼睛到命中位置的距离

## 停止看向方块时 (`stop_looking_at_block`)
- 当准星停止指向一个方块时触发（报告最后一个目标方块，最大 20 格）。
- 变量：
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`
  - `$$distance_to_player`

## 开始看向实体时 (`start_looking_at_entity`)
- 当准星首次指向一个实体时触发一次（最大 20 格）。
- 变量：
  - `$$entity_key` – 目标实体类型
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## 停止看向实体时 (`stop_looking_at_entity`)
- 当准星停止指向一个实体时触发（报告最后一个目标实体，最大 20 格）。
- 变量：
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## 实体生成时 (`entity_spawned`)
- **需要服务器上的 FancyMenu。** 当连接的世界/服务器中任意位置生成实体时触发。
- 变量：
  - `$$entity_key`
  - `$$distance_to_player` – 如果在其他维度则为 −1
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`
  - `$$dimension_key`
  - `$$is_same_dimension_as_player`

## 实体死亡时 (`entity_died`)
- **需要服务器上的 FancyMenu。** 当连接的世界/服务器中任意实体死亡时触发。
- 变量：
  - `$$entity_key`
  - `$$distance_to_player` – 如果在其他维度则为 −1
  - `$$death_pos_x`
  - `$$death_pos_y`
  - `$$death_pos_z`
  - `$$entity_uuid`
  - `$$dimension_key`
  - `$$damage_type`
  - `$$is_same_dimension_as_player`
  - `$$entity_killed_by_name`
  - `$$entity_killed_by_key`
  - `$$entity_killed_by_uuid`

## 实体开始进入视野时 (`entity_starts_being_in_sight`)
- 当实体首次在 200 格范围内变为可见时触发。
- 变量：
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## 实体停止在视野中时 (`entity_stops_being_in_sight`)
- 当之前可见的实体离开视野或移动到 200 格之外时触发。
- 变量：
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## 与实体交互时 (`entity_interacted`)
- 当玩家成功与实体交互时触发。
- 变量：
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## 实体被骑乘时 (`entity_mounted`)
- 当玩家开始骑乘某个实体时触发。
- 变量：
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## 实体取消骑乘时 (`entity_unmounted`)
- 当玩家停止骑乘当前实体时触发。
- 变量：
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## 方块被破坏时 (`block_broke`)
- 当玩家破坏方块时触发。
- 变量：
  - `$$block_key`
  - `$$broke_with_item_key` – 使用的工具或 EMPTY
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## 方块被放置时 (`block_placed`)
- 当玩家放置方块时触发。
- 变量：
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## 与方块交互时 (`interacted_with_block`)
- 当玩家成功与方块交互时触发。
- 变量：
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## 踩到方块时 (`stepping_on_block`)
- 当玩家踩到一个方块上时触发。
- 变量：
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## 进入生物群系时 (`enter_biome`)
- 当玩家进入新的生物群系时触发。
- 变量：
  - `$$biome_key` – 进入的生物群系

## 离开生物群系时 (`leave_biome`)
- 当玩家离开当前生物群系时触发。
- 变量：
  - `$$biome_key` – 刚离开的生物群系

## 进入结构时 (`enter_structure`)
- **需要服务器上的 FancyMenu。** 粗略的结构区域检测；可能在结构附近、上方或下方触发。
- 变量：
  - `$$structure_key` – 进入的结构

## 离开结构时 (`leave_structure`)
- **需要服务器上的 FancyMenu。** 粗略检测；可能在结构边界附近触发。
- 变量：
  - `$$structure_key` – 刚离开的结构

## 进入结构时（高精度）(`enter_structure_high_precision`)
- **需要服务器上的 FancyMenu。** 当玩家踏入结构的包围盒时触发。
- 变量：
  - `$$structure_key`

## 离开结构时（高精度）(`leave_structure_high_precision`)
- **需要服务器上的 FancyMenu。** 当玩家离开结构的包围盒后触发。
- 变量：
  - `$$structure_key`

## 进入维度时 (`enter_dimension`)
- 当玩家进入新的维度时触发。
- 变量：
  - `$$dimension_key` – 进入的维度

## 开始游泳时 (`start_swimming`)
- 当玩家开始游泳时触发。
- 变量：
  - `$$fluid_type` – 流体资源位置

## 停止游泳时 (`stop_swimming`)
- 当玩家停止游泳时触发。
- 变量：
  - `$$fluid_type` – 停止游泳所在的流体

## 开始接触流体时 (`start_touching_fluid`)
- 当玩家开始接触流体时触发。
- 变量：
  - `$$fluid_type` – 接触到的流体

## 停止接触流体时 (`stop_touching_fluid`)
- 当玩家停止接触流体时触发。
- 变量：
  - `$$fluid_type` – 不再接触的流体

## 音乐曲目开始时 (`music_track_started`)
- 当新的音乐曲目开始播放时触发。
- 变量：
  - `$$track_resource_location` – 音频文件
  - `$$track_display_name` – 人类可读名称或 UNKNOWN
  - `$$track_artist` – 艺术家或 UNKNOWN
  - `$$track_duration_ms` – 毫秒（未知时为 0）

## 音乐曲目停止时 (`music_track_stopped`)
- 当当前音乐曲目结束或被替换时触发。
- 变量：
  - `$$track_resource_location`
  - `$$track_display_name`
  - `$$track_artist`
  - `$$track_duration_ms`

## 世界音效触发时 (`world_sound_triggered`)
- 当一个带位置的世界音效在玩家附近开始播放时触发。
- 变量：
  - `$$sound_resource_location` – 音效文件
  - `$$sound_display_name` – 可用时的字幕名称
  - `$$sound_origin_pos_x`
  - `$$sound_origin_pos_y`
  - `$$sound_origin_pos_z`
  - `$$sound_origin_distance_to_player`
  - `$$sound_origin_direction_from_player` – 相对于朝向的 0–360 度角

## 天气改变时 (`weather_changed`)
- 当天气全局或局部发生变化时触发（生物群系变化或进入室内也可能再次触发）。
- 变量：
  - `$$weather_type` – clear/rain/thunder
  - `$$weather_can_snow` – 如果会渲染雪则为 TRUE
  - `$$weather_can_rain` – 如果会渲染雨则为 TRUE

## 开始燃烧时 (`started_burning`)
- 当玩家开始燃烧时触发。
- 变量：
  - （无）

## 停止燃烧时 (`stopped_burning`)
- 当玩家停止燃烧时触发。
- 变量：
  - （无）

## 开始溺水时 (`started_drowning`)
- 当玩家开始受到溺水伤害时触发。
- 变量：
  - （无）

## 位置改变时 (`position_changed`)
- 当玩家的方块位置发生变化时触发。
- 变量：
  - `$$old_pos_x` – 之前的方块 X
  - `$$old_pos_y` – 之前的方块 Y
  - `$$old_pos_z` – 之前的方块 Z
  - `$$new_pos_x` – 新的方块 X
  - `$$new_pos_y` – 新的方块 Y
  - `$$new_pos_z` – 新的方块 Z

## 开始疾跑时 (`started_running`)
- 当玩家开始疾跑时触发。
- 变量：
  - （无）

## 停止疾跑时 (`stopped_running`)
- 当玩家停止疾跑时触发。
- 变量：
  - （无）

## 跳跃时 (`jump`)
- 当玩家跳跃时触发。
- 变量：
  - （无）

## 加入服务器时 (`server_joined`)
- 成功加入多人服务器后触发。
- 变量：
  - `$$server_ip` – 加入的服务器地址

## 离开服务器时 (`server_left`)
- 从多人服务器断开后触发。
- 变量：
  - `$$server_ip` – 离开的服务器地址

## 进入单人世界时 (`world_entered`)
- 单人世界加载完成并恢复控制后触发。
- 变量：
  - `$$world_name` – 显示名称
  - `$$world_save_path` – 绝对存档文件夹路径
  - `$$world_difficulty` – 难度键
  - `$$world_cheats_allowed` – 如果已启用作弊则为 TRUE
  - `$$world_icon_path` – 绝对图标路径
  - `$$world_is_first_join` – 首次进入时为 TRUE

## 离开单人世界时 (`world_left`)
- 单人世界关闭并完成保存后触发。
- 变量：
  - `$$world_name`
  - `$$world_save_path`
  - `$$world_difficulty`
  - `$$world_cheats_allowed`
  - `$$world_icon_path`

## 其他玩家加入世界/服务器时 (`other_player_joined_world`)
- 当其他玩家加入当前世界/服务器时触发。
- 变量：
  - `$$player_name` – 加入玩家的名称
  - `$$player_uuid` – UUID

## 其他玩家离开世界/服务器时 (`other_player_left_world`)
- 当其他玩家离开当前世界/服务器时触发。
- 变量：
  - `$$player_name`
  - `$$player_uuid`

## 其他玩家死亡时 (`other_player_died`)
- 当当前世界中的其他玩家死亡时触发。
- 变量：
  - `$$player_name`
  - `$$player_uuid`
  - `$$death_pos_x`
  - `$$death_pos_y`
  - `$$death_pos_z`

## 拾取物品时 (`item_picked_up`)
- 当玩家拾取一个物品实体时触发。
- 变量：
  - `$$item_key` – 拾取的物品资源位置

## 丢出物品时 (`item_dropped`)
- 当玩家从背包中丢出一个物品时触发。
- 变量：
  - `$$item_key` – 丢出的物品资源位置

## 消耗物品时 (`item_consumed`)
- 当玩家完成消耗一个物品时触发。
- 变量：
  - `$$item_key` – 被消耗的物品

## 在背包中悬停物品时 (`item_hovered_in_inventory`)
- 当用户在任何背包界面中悬停在一个物品上时触发。
- 变量：
  - `$$item_key` – 悬停的物品资源位置
  - `$$item_display_name_string` – 纯文本物品显示名称
  - `$$item_display_name_json` – JSON 组件形式的物品显示名称

## 使用物品时 (`item_used`)
- 当玩家使用一个物品时触发。
- 变量：
  - `$$item_key` – 使用的物品
  - `$$used_on_type` – block/entity/self/none
  - `$$used_on_entity_key` – 目标实体类型或空
  - `$$used_on_block_key` – 目标方块或空
  - `$$target_pos_x` – 目标 X 或 -1
  - `$$target_pos_y` – 目标 Y 或 -1
  - `$$target_pos_z` – 目标 Z 或 -1

## 物品损坏时 (`item_broke`)
- 当玩家背包中的物品损坏时触发。
- 变量：
  - `$$item_key` – 损坏的物品
  - `$$item_type` – 工具/盔甲/其他
