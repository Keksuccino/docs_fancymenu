---
title: 监听器
description: 如何在 FancyMenu 中创建和使用监听器。
---

# 监听器

从 FancyMenu v3.8.0 开始，新增了一个名为“监听器”的功能。

监听器会在特定的客户端或游戏玩法事件发生时执行动作脚本。
它们可以向动作、占位符以及嵌套在监听器中的要求暴露变量。

与 FancyMenu 中的大多数功能不同，监听器并不绑定到某个界面或覆盖层。它们会持续在后台运行，监听对应的事件。一旦某个监听器被触发，即使当时没有打开任何界面，它也会执行自己的动作脚本。

# 使用监听器

要创建一个监听某个事件并执行动作脚本的新监听器，请在**不处于布局编辑器**时点击 **菜单栏 -> 自定义 -> 管理监听器**。在那里你可以找到一个易于使用的界面来创建和管理监听器。

<img src="https://github.com/Keksuccino/FancyMenu/blob/master/assets/docs/manage_listeners.png?raw=true" alt="管理监听器" style="max-width:800px;width:100%;height:auto;">

# 监听器变量

监听器通常会为其嵌套的动作、要求和占位符暴露一种特殊类型的变量。
这些变量可以像占位符一样被访问（它们实际上就是占位符）。

你只需在文本输入框中使用 `$$` 前缀加上变量名即可使用这些变量，方式类似于使用普通占位符。

例如，如果你使用 **按下键盘按键时** 监听器，并且想通过 **打印到日志** 动作把按键名称输出到日志中，你可以在动作要打印的消息输入框中填入类似 `按键被按下！按键是：$$key_name` 的内容。之后，这个变量占位符会被实际的按键名称替换。

> 尽管这些被称为“变量”，但它们与 FancyMenu 的普通[变量系统](/variables)没有任何关系。你不能设置这些变量，因为它们是**只读**的。你也不能将 FancyMenu 变量系统中的任何动作、要求和占位符用于这些特殊的监听器变量，因此使用 **获取变量值 [FM 变量]**、**判断变量值 [FM 变量]** 或 **设置变量值 [FM 变量]** 都不会对监听器变量生效。
{.is-warning}

# 监听器详解

下面的列表应包含 FancyMenu 大多数、如果不是全部的话，监听器。由于模组更新，列表可能不会始终保持最新。

## 点击 Markdown 文本时
- 当带有 `click:` 事件的 Markdown 文本被点击时触发，例如 `[打开](click:open_menu)`。
- 变量：
  - `$$text_event_id` – Markdown 链接中的事件 ID

## 悬停 Markdown 文本时
- 当带有 `hover:` 事件的 Markdown 文本被悬停时触发，例如 `[提示](hover:show_hint)`。
- 变量：
  - `$$text_event_id` – Markdown 链接中的事件 ID

## 通过动作解压 ZIP 时
- 当 **在游戏目录中解压 ZIP 文件** 动作完成时触发。
- 变量：
  - `$$source_zip_path` – 已解析的源 ZIP 路径
  - `$$target_folder_path` – 已解析的解压目标路径
  - `$$extract_succeeded` – true/false
  - `$$failure_reason` – 解压失败时的错误文本

## 元素生成时
- 当一个元素通过动作/脚本化的元素生成流程被生成时触发。
- 变量：
  - `$$element_type` – 生成的元素类型
  - `$$element_identifier` – 生成的元素标识符
  - `$$target_screen` – 目标界面标识符

## 动画纹理开始播放时
- 当动画纹理开始播放时触发。
- 变量：
  - `$$texture_source` – 纹理来源
  - `$$texture_source_type` – 来源类型
  - `$$texture_will_restart` – true/false

## 动画纹理播放完成时
- 当动画纹理播放结束时触发。
- 变量：
  - `$$texture_source`
  - `$$texture_source_type`
  - `$$texture_will_restart`

## 视频播放状态变化时
- 当视频元素或视频菜单背景的播放状态发生变化时触发。
- 变量：
  - `$$video_source` – 视频来源
  - `$$video_source_type` – 来源类型
  - `$$is_looping` – true/false
  - `$$new_status` – `PLAYING`、`STOPPED`、`PAUSED` 或 `FINISHED`

## 在聊天中收到系统消息时
- 当客户端收到系统聊天消息时触发，例如命令反馈。
- 变量：
  - `$$system_message_string` – 纯文本消息
  - `$$system_message_component` – JSON 组件

## 接收到 FM 数据时
- 当服务器通过 `/fmdata send` 向此客户端发送 FM 数据时触发。
- 变量：
  - `$$data_identifier` – 数据标识字符串
  - `$$data` – 数据载荷
  - `$$sent_by` – 服务器 IP 或 `integrated_server`

## 远程服务器连接时
- 当 FancyMenu 初始化远程服务器连接时触发。
- 变量：
  - `$$request_id` – 已缓存的请求 ID
  - `$$remote_server_url` – 远程服务器 URL

## 接收到远程服务器数据时
- 当从已连接的远程服务器接收到文本数据时触发。
- 变量：
  - `$$request_id` – 请求 ID
  - `$$remote_server_url` – 远程服务器 URL
  - `$$data` – 接收到的载荷

## 远程服务器连接关闭时
- 当远程服务器连接关闭时触发。
- 变量：
  - `$$request_id` – 请求 ID
  - `$$remote_server_url` – 远程服务器 URL
  - `$$intentionally_closed` – 如果由动作关闭则为 TRUE
  - `$$crashed` – 如果连接意外崩溃则为 TRUE
  - `$$unknown_close_reason` – 如果没有可用的已知关闭原因则为 TRUE

## 按下键盘按键时
- 每当按下一个按键时触发（按住时会重复触发；在界面内和游戏中都有效）。
- 变量：
  - `$$key_name` – 按键显示名称
  - `$$key_keycode` – GLFW 键码
  - `$$key_scancode` – GLFW 扫描码
  - `$$key_modifiers` – 当前激活的修饰键位掩码

## 释放键盘按键时
- 当按键被释放时触发（界面内和游戏中都有效）。
- 变量：
  - `$$key_name`
  - `$$key_keycode`
  - `$$key_scancode`
  - `$$key_modifiers`

## 在界面中键入键盘字符时
- 当界面打开时输入字符会触发。
- 变量：
  - `$$char` – 输入的字符

## 在界面中移动鼠标时
- 当界面打开时，只要鼠标移动就会触发。
- 变量：
  - `$$mouse_pos_x` – 当前 X
  - `$$mouse_pos_y` – 当前 Y
  - `$$mouse_move_delta_x` – 自上次事件以来的 X 变化量
  - `$$mouse_move_delta_y` – 自上次事件以来的 Y 变化量

## 鼠标按钮点击时
- 当鼠标按钮被按下时触发（界面内和游戏中都有效）。
- 变量：
  - `$$button` – 左/右/中
  - `$$mouse_pos_x` – 当前 X
  - `$$mouse_pos_y` – 当前 Y

## 鼠标按钮释放时
- 当鼠标按钮被释放时触发（界面内和游戏中都有效）。
- 变量：
  - `$$button`
  - `$$mouse_pos_x`
  - `$$mouse_pos_y`

## 在界面中滚动鼠标时
- 当界面打开时滚动鼠标滚轮会触发。
- 变量：
  - `$$scroll_delta_y` – 纵向滚动量

## 界面打开时
- 在任何界面变为活动状态后立即运行；可用于覆盖它。
- 变量：
  - `$$screen_identifier` – 打开的界面标识符

## 界面关闭时
- 在界面关闭后立即运行。
- 变量：
  - `$$screen_identifier` – 关闭的界面标识符

## 退出 Minecraft 时
- 在客户端开始关闭时触发一次。
- 变量：
  - `$$timestamp_millis` – 退出时的纪元毫秒时间戳
  - `$$timestamp_iso` – 退出时刻的 ISO-8601 时间戳

## 死亡时
- 当原版死亡界面为本地玩家打开时运行。
- 变量：
  - `$$days_survived` – 自上次死亡以来的天数
  - `$$death_reason_string` – 纯文本死亡原因
  - `$$death_reason_component` – JSON 组件死亡原因
  - `$$death_pos_x` – 死亡 X 坐标
  - `$$death_pos_y` – 死亡 Y 坐标
  - `$$death_pos_z` – 死亡 Z 坐标

## 变量更新时 [FM 变量]
- 每当 FancyMenu 变量被设置/更新时触发。
- 变量：
  - `$$var_name` – 变量名
  - `$$old_value` – 旧值
  - `$$new_value` – 新值

## 通过动作下载文件时
- 在“下载文件到游戏目录”动作完成后触发。
- 变量：
  - `$$download_url` – 下载来源
  - `$$target_file_path` – 保存的文件路径
  - `$$download_succeeded` – true/false

## 选择文件时
- 在“选择文件”动作完成后触发。
- 变量：
  - `$$selected_file_path` – 选择的文件绝对路径；如果已取消则为空
  - `$$target_file_path` – 实例内已解析的路径
  - `$$selection_succeeded` – 如果复制成功则为 true
  - `$$selection_cancelled` – 如果对话框被关闭则为 true
  - `$$failure_reason` – 失败时的错误信息

## 接收到聊天消息时
- 当普通玩家聊天消息出现在客户端时触发。
- 变量：
  - `$$chat_message_string` – 纯文本消息
  - `$$chat_message_component` – 完整 JSON 组件
  - `$$sender_uuid` – 发送者 UUID 或 ERROR
  - `$$sender_name` – 发送者名称或 ERROR

## 发送聊天消息时
- 当本地玩家发送聊天消息时触发。
- 变量：
  - `$$chat_message_string` – 纯文本消息
  - `$$chat_message_component` – 完整 JSON 组件

## 获得效果时
- 当玩家获得状态效果时触发。
- 变量：
  - `$$effect_key` – 效果资源位置
  - `$$effect_type` – 正面/负面/中性
  - `$$effect_duration` – 剩余刻数

## 失去效果时
- 当玩家失去状态效果时触发。
- 变量：
  - `$$effect_key` – 已失效的效果
  - `$$effect_type` – 类别

## 经验变化时
- 当玩家总经验发生变化时触发。
- 变量：
  - `$$new_experience_amount` – 变化后的值
  - `$$old_experience_amount` – 变化前的值
  - `$$is_level_up` – 如果等级提升则为 TRUE

## 受到伤害时
- 每次玩家受到伤害时触发一次。
- 变量：
  - `$$damage_amount` – 扣除的生命值
  - `$$damage_type` – 伤害类型资源位置
  - `$$is_fatal_damage` – 如果致命则为 TRUE
  - `$$damage_source` – 攻击者资源位置或 NONE

## 开始冻结时
- 当玩家开始冻结时触发。
- 变量：
  - `$$freezing_intensity` – 0.0 表示未冻结，1.0 表示完全冻结

## 停止冻结时
- 当玩家停止冻结时触发。
- 变量：
  - （无）

## 完全冻结时
- 当玩家变为完全冻结时触发一次。
- 变量：
  - （无）

## 开始看向方块时
- 当准星第一次指向一个方块时触发一次（最大距离 20 格）。
- 变量：
  - `$$block_key` – 目标方块
  - `$$block_pos_x` – 方块 X
  - `$$block_pos_y` – 方块 Y
  - `$$block_pos_z` – 方块 Z
  - `$$distance_to_player` – 从眼睛到命中位置的距离

## 停止看向方块时
- 当准星停止指向某个方块时触发（报告最后指向的方块，最大 20 格）。
- 变量：
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`
  - `$$distance_to_player`

## 开始看向实体时
- 当准星第一次指向一个实体时触发一次（最大 20 格）。
- 变量：
  - `$$entity_key` – 目标实体类型
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## 停止看向实体时
- 当准星停止指向某个实体时触发（报告最后指向的实体，最大 20 格）。
- 变量：
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## 实体生成时
- **需要服务器端安装 FancyMenu。** 当连接的世界/服务器中的任意实体在任何位置生成时触发。
- 变量：
  - `$$entity_key`
  - `$$distance_to_player` – 如果在其他维度则为 -1
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`
  - `$$dimension_key`
  - `$$is_same_dimension_as_player`

## 实体死亡时
- **需要服务器端安装 FancyMenu。** 当连接的世界/服务器中的任意实体死亡时触发。
- 变量：
  - `$$entity_key`
  - `$$distance_to_player` – 如果在其他维度则为 -1
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

## 实体首次进入视野时
- 当一个实体首次在 200 格范围内变为可见时触发。
- 变量：
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## 实体离开视野时
- 当一个先前可见的实体离开视野或移动到 200 格之外时触发。
- 变量：
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## 与实体交互时
- 当玩家成功与一个实体交互时触发。
- 变量：
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## 实体骑乘时
- 当玩家开始骑乘一个实体时触发。
- 变量：
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## 停止骑乘实体时
- 当玩家停止骑乘当前实体时触发。
- 变量：
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## 方块被破坏时
- 当玩家破坏一个方块时触发。
- 变量：
  - `$$block_key`
  - `$$broke_with_item_key` – 使用的工具或 EMPTY
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## 方块被放置时
- 当玩家放置一个方块时触发。
- 变量：
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## 与方块交互时
- 当玩家成功与一个方块交互时触发。
- 变量：
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## 踏上方块时
- 当玩家踩到一个方块上时触发。
- 变量：
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## 进入生物群系时
- 当玩家进入一个新的生物群系时触发。
- 变量：
  - `$$biome_key` – 进入的生物群系

## 离开生物群系时
- 当玩家离开当前生物群系时触发。
- 变量：
  - `$$biome_key` – 刚离开的生物群系

## 进入结构时
- **需要服务器端安装 FancyMenu。** 粗略的结构区域检测；可能会在结构附近、上方或下方触发。
- 变量：
  - `$$structure_key` – 进入的结构

## 离开结构时
- **需要服务器端安装 FancyMenu。** 粗略检测；可能会在结构轮廓附近触发。
- 变量：
  - `$$structure_key` – 刚离开的结构

## 进入结构时（高精度）
- **需要服务器端安装 FancyMenu。** 当玩家进入结构的包围盒时触发。
- 变量：
  - `$$structure_key`

## 离开结构时（高精度）
- **需要服务器端安装 FancyMenu。** 当玩家离开结构的包围盒后触发。
- 变量：
  - `$$structure_key`

## 进入维度时
- 当玩家进入一个新维度时触发。
- 变量：
  - `$$dimension_key` – 进入的维度

## 开始游泳时
- 当玩家开始游泳时触发。
- 变量：
  - `$$fluid_type` – 流体资源位置

## 停止游泳时
- 当玩家停止游泳时触发。
- 变量：
  - `$$fluid_type` – 停止游泳所在的流体

## 开始接触流体时
- 当玩家开始接触某种流体时触发。
- 变量：
  - `$$fluid_type` – 接触到的流体

## 停止接触流体时
- 当玩家不再接触某种流体时触发。
- 变量：
  - `$$fluid_type` – 不再接触的流体

## 音乐曲目开始时
- 当一首新的音乐曲目开始播放时触发。
- 变量：
  - `$$track_resource_location` – 音频文件
  - `$$track_display_name` – 可读名称或 UNKNOWN
  - `$$track_artist` – 艺术家或 UNKNOWN
  - `$$track_duration_ms` – 毫秒数（未知则为 0）

## 音乐曲目停止时
- 当当前音乐曲目结束或被替换时触发。
- 变量：
  - `$$track_resource_location`
  - `$$track_display_name`
  - `$$track_artist`
  - `$$track_duration_ms`

## 世界音效触发时
- 当一个有位置的世界音效在玩家附近开始播放时触发。
- 变量：
  - `$$sound_resource_location` – 音效文件
  - `$$sound_display_name` – 若可用则为字幕名称
  - `$$sound_origin_pos_x`
  - `$$sound_origin_pos_y`
  - `$$sound_origin_pos_z`
  - `$$sound_origin_distance_to_player`
  - `$$sound_origin_direction_from_player` – 相对于朝向的 0–360 度角

## 天气变化时
- 当天气在全局或局部发生变化时触发（生物群系变化或进入室内也可能再次触发）。
- 变量：
  - `$$weather_type` – clear/rain/thunder
  - `$$weather_can_snow` – 如果会显示雪则为 TRUE
  - `$$weather_can_rain` – 如果会显示雨则为 TRUE

## 开始燃烧时
- 当玩家开始燃烧时触发。
- 变量：
  - （无）

## 停止燃烧时
- 当玩家停止燃烧时触发。
- 变量：
  - （无）

## 开始溺水时
- 当玩家开始受到溺水伤害时触发。
- 变量：
  - （无）

## 位置变化时
- 当玩家的方块坐标发生变化时触发。
- 变量：
  - `$$old_pos_x` – 之前的方块 X
  - `$$old_pos_y` – 之前的方块 Y
  - `$$old_pos_z` – 之前的方块 Z
  - `$$new_pos_x` – 新的方块 X
  - `$$new_pos_y` – 新的方块 Y
  - `$$new_pos_z` – 新的方块 Z

## 开始奔跑时
- 当玩家开始冲刺时触发。
- 变量：
  - （无）

## 停止奔跑时
- 当玩家停止冲刺时触发。
- 变量：
  - （无）

## 跳跃时
- 当玩家跳跃时触发。
- 变量：
  - （无）

## 连接到服务器时
- 在成功加入多人服务器后触发。
- 变量：
  - `$$server_ip` – 加入的服务器地址

## 离开服务器时
- 在与多人服务器断开连接后触发。
- 变量：
  - `$$server_ip` – 离开的服务器地址

## 进入单人世界时
- 在单人世界加载完成并恢复控制后触发。
- 变量：
  - `$$world_name` – 显示名称
  - `$$world_save_path` – 绝对存档文件夹
  - `$$world_difficulty` – 难度键
  - `$$world_cheats_allowed` – 如果启用了作弊则为 TRUE
  - `$$world_icon_path` – 绝对图标路径
  - `$$world_is_first_join` – 首次进入时为 TRUE

## 离开单人世界时
- 在单人世界关闭并完成保存后触发。
- 变量：
  - `$$world_name`
  - `$$world_save_path`
  - `$$world_difficulty`
  - `$$world_cheats_allowed`
  - `$$world_icon_path`

## 其他玩家加入世界/服务器时
- 当其他玩家加入当前世界/服务器时触发。
- 变量：
  - `$$player_name` – 加入玩家的名称
  - `$$player_uuid` – UUID

## 其他玩家离开世界/服务器时
- 当其他玩家离开当前世界/服务器时触发。
- 变量：
  - `$$player_name`
  - `$$player_uuid`

## 其他玩家死亡时
- 当当前世界中的其他玩家死亡时触发。
- 变量：
  - `$$player_name`
  - `$$player_uuid`
  - `$$death_pos_x`
  - `$$death_pos_y`
  - `$$death_pos_z`

## 拾取物品时
- 当玩家拾取一个物品实体时触发。
- 变量：
  - `$$item_key` – 拾取到的物品资源位置

## 丢弃物品时
- 当玩家从物品栏中丢弃一个物品时触发。
- 变量：
  - `$$item_key` – 丢弃的物品资源位置

## 消耗物品时
- 当玩家完成消耗一个物品时触发。
- 变量：
  - `$$item_key` – 消耗的物品

## 在物品栏中悬停物品时
- 当用户在任何物品栏界面中悬停一个物品时触发。
- 变量：
  - `$$item_key` – 悬停的物品资源位置
  - `$$item_display_name_string` – 纯文本物品显示名称
  - `$$item_display_name_json` – JSON 组件物品显示名称

## 使用物品时
- 当玩家使用一个物品时触发。
- 变量：
  - `$$item_key` – 使用的物品
  - `$$used_on_type` – block/entity/self/none
  - `$$used_on_entity_key` – 目标实体类型或空
  - `$$used_on_block_key` – 目标方块或空
  - `$$target_pos_x` – 目标 X 或 -1
  - `$$target_pos_y` – 目标 Y 或 -1
  - `$$target_pos_z` – 目标 Z 或 -1

## 物品损坏时
- 当玩家物品栏中的一个物品损坏时触发。
- 变量：
  - `$$item_key` – 损坏的物品
  - `$$item_type` – 工具/盔甲/其他
