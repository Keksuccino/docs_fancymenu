---
title: 动作脚本
description: 如何将动作脚本用于按钮、滑块、ticker 等更多元素。
---

# 动作脚本

FancyMenu 允许你通过为元素分配**动作**来为菜单添加交互性。这些动作会在按钮被点击、ticker 正在滚动、滑块被使用，或屏幕打开/关闭时执行。你还可以使用简单的控制语句构建高级动作脚本，例如 **if**、**else-if**、**else** 和 **while**，来控制哪些动作执行以及何时执行。

<img src="https://github.com/Keksuccino/FancyMenu/blob/master/assets/docs/action_script_editor.png?raw=true" alt="动作脚本编辑器" style="max-width:800px;width:100%;height:auto;">

# 什么是动作？

**动作**是 FancyMenu 在被触发时执行的任务或操作。例如，一个动作可以打开一个新屏幕、发送聊天消息，或调整音频元素的音量。在 FancyMenu 的编辑器中，动作会配置一个值（如果需要），用来提供额外信息——例如 URL 或服务器地址。

# 什么是语句？

为了创建更复杂的行为，FancyMenu 在动作脚本中支持基本的控制语句，包括：

- **If 语句：** 仅当满足指定的 [条件](/en/conditions) 时才执行一组动作。
- **Else-If 语句：** 如果前面的 *if*（或更早的 *else-if*）未满足，则检查另一个 [条件](/en/conditions)。
- **Else 语句：** 当前面所有 [条件](/en/conditions) 都不满足时执行。
- **While 语句：** 当某个 [条件](/en/conditions) 保持为真时，持续重复执行一组动作（内置超时以防止无限循环）。
- **延迟块：** 在执行其中包含的动作之前等待指定时间。在延迟计时的同时，脚本的其余部分会继续运行。
- **稍后执行块：** 将其中包含的动作排入队列，在毫秒级延迟后于主线程上执行。
- **注释：** 在脚本中添加备注以便整理。注释不会执行任何动作。

通过将这些语句与动作结合，你可以构建动态且有条件的行为，例如：在发送警告消息前检查玩家生命值是否过低，或者在条件变化前持续重复更新。

# 在哪里可以使用动作脚本？

动作脚本用途广泛，可用于布局中的多个位置。你可以将它们分配给，例如：

- **按钮：** 点击按钮时执行动作。
- **Ticker：** 持续运行动作脚本，以更新布局中的屏幕信息。
- **滑块：** 当滑块值变化时触发动作脚本。
- **屏幕事件：** 当屏幕打开或关闭时运行脚本（例如，菜单出现时播放声音）。
- **监听器：** 当监听某个特定事件的监听器被触发时，它会执行其动作脚本。
- **调度器：** 按时间安排执行动作，即使没有打开任何屏幕也可运行。

# 在动作中使用占位符

动作值支持通过**占位符**提供动态内容。大多数情况下，这些占位符使用类似 JSON 的语法，并会在动作执行时替换为实时数据。

## 类 JSON 占位符

这些是常规的 [占位符](/en/placeholders)，可在布局中的许多位置使用。

它们的语法如下：

```json
{"placeholder": "placeholder_id", "values": {"key1": "value1", "key2": "value2"}}
```

它们可以获取游戏数据，例如玩家名称、屏幕尺寸，或使用 **Calculator** 占位符计算得到的值。你也可以嵌套占位符以实现更高级的用法。

## `$$` 占位符（变量）

`$$` 占位符很特殊。FancyMenu 的某些功能会为其嵌套动作、要求和普通占位符提供这些特殊占位符，因此它们可在内部用于获取所在环境（元素、监听器等）的更多信息。

例如，如果动作用于滑块中，那么在动作里使用 `$$value` 会被替换为滑块当前的值。

在监听器中使用动作时，每个监听器都会提供自己独特的一组变量/占位符，用于获取有关该监听器的更多信息，例如按下的鼠标按键、输入的结构等。

# 如何设置和编辑动作

要为某个元素添加、编辑或移除动作（以及语句块），只需**右键单击该元素**（无论它是按钮、滑块、ticker 还是其他交互项），然后选择 **管理动作脚本**。这会打开“管理动作”界面，在这里你可以：

- **添加新动作或语句：** 插入新的动作条目或控制语句（if、else-if、else、while）来构建脚本。
- **编辑现有动作或语句：** 修改动作值或更改控制逻辑。
- **移除动作或语句：** 删除脚本中不需要的动作。

对于 [监听器](/listeners)，有一个专门的菜单用于管理和创建监听器，并可访问其动作脚本，体验与编辑按钮或滑块的动作脚本类似。

> 在动作脚本编辑器界面中，只需在大的深灰色区域上右键单击，即可打开用于添加动作、语句等内容的上下文菜单。
{.is-info}


# 动作脚本编辑器快捷键及更多功能

动作脚本编辑器提供了许多很实用的易用性功能，让脚本编辑变得非常简单。

## 快捷键

- `DEL`：快速删除选中的条目
- `ENTER`：开始对选中条目进行行内编辑（如果该条目没有行内编辑，则打开编辑界面）
- `CTRL + C`：复制选中的动作（目前仅对动作有效）
- `CTRL + V`：粘贴之前复制的动作
- `CTRL + Z`：后退一步（撤销）
- `CTRL + Y`：前进一步（重做）
- `ARROW UP`：从当前选中条目向上移动一项
- `ARROW DOWN`：从当前选中条目向下移动一项
- `SHIFT + ARROW UP`：将选中的条目上移一项
- `SHIFT + ARROW DOWN`：将选中的条目下移一项
- `A`：快速打开动作选择器界面以添加新动作
- `CTRL + S`：在编辑器窗口中完成/保存

## 更多易用性功能

- 双击动作的值，可以在不进入完整值编辑界面的情况下直接编辑该值。
- IF 语句链（以及追加的 ELSE/ELSE-IF 语句）、WHILE 循环和文件夹可以折叠（仅影响显示，不影响脚本逻辑）。
- 编辑器总是在选中条目的下方添加新动作（或嵌套到选中的链/循环/文件夹中）。
- 右键单击深灰色脚本区域背景会打开上下文菜单，其中包含添加动作、语句以及其他所有重要选项。

# 动作详解

此列表包含 FancyMenu 中大部分（如果不是全部）可用动作。由于模组更新，列表有时可能会略显过时。

## 下一个曲目 (`audio_next_track`)
- **说明：** 切换到音频元素中的下一曲目
- **需要值：** 是 - `audio_element_identifier`（要控制的音频元素 ID）

## 上一个曲目 (`audio_previous_track`)
- **说明：** 切换到音频元素中的上一曲目
- **需要值：** 是 - `audio_element_identifier`（要控制的音频元素 ID）

## 设置曲目音量 (`set_audio_element_volume`)
- **说明：** 设置音频元素的音量（0.0 到 1.0）
- **需要值：** 是 - `element_identifier:volume`

## 切换播放/暂停曲目 (`audio_toggle_play`)
- **说明：** 切换音频元素当前曲目的播放/暂停状态
- **需要值：** 是 - `audio_element_identifier`

## 播放音频 (`play_audio`)
- **说明：** 播放一次音频资源。该动作会跟踪其启动的音频，因此之后可通过 `stop_all_action_audios` 停止。
- **需要值：** 是 - 包含 `audioSource`、`soundChannel` 和 `baseVolume` 的 JSON 配置
- **示例值：** `{"audioSource":"[source:local]/config/fancymenu/assets/example.ogg","soundChannel":"master","baseVolume":1.0}`

## 停止所有动作音频 (`stop_all_action_audios`)
- **说明：** 停止由 **播放音频** 动作启动的所有音频轨道。不会停止音频元素、菜单打开/关闭声音、按钮声音或其他音频系统。
- **需要值：** 否

## 设置视频元素音量 (`set_video_element_volume`)
- **说明：** 设置视频元素的音量（0.0 到 1.0）
- **需要值：** 是 - `video_element_identifier:volume`

## 设置视频元素播放时间 (`set_video_element_play_time`)
- **说明：** 将视频元素跳转到指定的毫秒时间戳
- **需要值：** 是 - `video_element_identifier:timestamp_ms`

## 切换视频元素暂停状态 (`toggle_video_element_pause_state`)
- **说明：** 切换视频元素的暂停状态
- **需要值：** 是 - `video_element_identifier`

## 设置视频菜单背景音量 (`set_video_menu_background_volume`)
- **说明：** 设置视频菜单背景的音量（0.0 到 1.0）
- **需要值：** 是 - `background_identifier:volume`

> 要获取背景的标识符，请右键单击编辑器背景并点击“复制背景标识符”。
{.is-info}

## 设置视频菜单背景播放时间 (`set_video_menu_background_play_time`)
- **说明：** 将视频菜单背景跳转到指定的毫秒时间戳
- **需要值：** 是 - `background_identifier:timestamp_ms`

> 要获取背景的标识符，请右键单击编辑器背景并点击“复制背景标识符”。
{.is-info}

## 切换视频菜单背景暂停状态 (`toggle_video_menu_background_pause_state`)
- **说明：** 切换视频菜单背景的暂停状态
- **需要值：** 是 - `background_identifier`

> 要获取背景的标识符，请右键单击编辑器背景并点击“复制背景标识符”。
{.is-info}

## 切换布局 (`toggle_layout`)
- **说明：** 按名称切换一个布局（启用/禁用）
- **需要值：** 是 - `layout_name`

## 启用布局 (`enable_layout`)
- **说明：** 按名称启用一个布局
- **需要值：** 是 - `layout_name`

## 禁用布局 (`disable_layout`)
- **说明：** 按名称禁用一个布局
- **需要值：** 是 - `layout_name`

## 打开屏幕或自定义 GUI (`opengui`)
- **说明：** 按其标识符打开一个屏幕（原版、模组或自定义 GUI）
- **需要值：** 是 - `screen_identifier`

> 此动作**并不适用于所有屏幕**，尤其是模组屏幕。如果动作无法打开某个屏幕，它会显示错误。在这种情况下你能做的不多，因为那可能是一个过于复杂、无法被 FancyMenu 自动打开的屏幕。
> 
> FancyMenu 这边也不会再手动为模组屏幕添加兼容性，因为为所有模组添加兼容性会花费太久，抱歉。大多数情况下，也不建议在这种情况下联系另一个模组的开发者，因为如果 FancyMenu 无法打开该屏幕，就没有简单的方法为其添加支持。这里推荐的替代方案是尝试使用 **“模仿原版/模组按钮”** 动作，去模仿那个打开特定屏幕的按钮。如果没有对应按钮，那就没办法了，抱歉。
{.is-info}

## 关闭屏幕 (`closegui`)
- **说明：** 关闭当前活动屏幕
- **需要值：** 否

## 更新屏幕 (`update_screen`)
- **说明：** 重新初始化当前屏幕
- **需要值：** 否

## 返回上一个屏幕 (`back_to_last_screen`)
- **说明：** 返回到上一个屏幕（当前屏幕之前的那个）
- **需要值：** 否

## 加入服务器 (`joinserver`)
- **说明：** 将玩家连接到 Minecraft 服务器
- **需要值：** 是 - `server_ip:port`

## 进入世界 (`loadworld`)
- **说明：** 进入一个 Minecraft 世界
- **需要值：** 是 - `world_folder_name`

## 进入/加入上一个世界/服务器 (`join_last_world`)
- **说明：** 进入/加入玩家上一次所在的世界或服务器
- **需要值：** 否

## 离开世界或服务器 (`disconnect_server_or_world`)
- **说明：** 离开一个世界或服务器，并打开指定屏幕
- **需要值：** 是 - `screen_identifier`

## 退出 Minecraft (`quitgame`)
- **说明：** 完全退出 Minecraft
- **需要值：** 否

## 发送聊天消息/命令 (`sendmessage`)
- **说明：** 发送聊天消息或执行聊天命令
- **需要值：** 是 - `message_text` 或 `/command_text`

## 作为集成服务器执行命令 (`execute_command_as_integrated_server`)
- **说明：** 在单人游戏中强制以集成服务器身份执行命令，忽略权限和作弊设置。
- **需要值：** 是 - 命令文本，例如 `/give @p minecraft:diamond 1`

> 此动作仅在单人游戏且世界未开放到局域网时有效。在多人服务器中它会刻意不执行任何操作。
{.is-warning}

## 粘贴到聊天 (`paste_to_chat`)
- **说明：** 将文本粘贴到聊天输入框（追加或替换）
- **需要值：** 是 - `true:文本` 或 `false:文本`

## 在聊天中显示 [客户端] (`display_in_chat_client_side`)
- **说明：** 直接在本地聊天中打印文本（不经服务器）
- **需要值：** 是 - `text_or_json`

## 向服务器发送 FM 数据 (`send_fm_data_to_server`)
- **说明：** 通过 FM Data 数据包通道向当前 FancyMenu 服务器发送自定义文本数据。
- **需要值：** 是 - `data_identifier||data`

## 连接到远程服务器 (`connect_to_remote_server`)
- **说明：** 打开或复用一个由客户端发起、连接到外部远程服务器的 WebSocket 连接。
- **需要值：** 是 - 远程服务器 URL，例如 `wss://example.com/ws`

## 向远程服务器发送数据 (`send_data_to_remote_server`)
- **说明：** 打开或复用一个远程服务器连接，并向其发送文本数据。
- **需要值：** 是 - `remote_server_url||data`

## 关闭远程服务器连接 (`close_remote_server_connection`)
- **说明：** 按请求 ID 关闭特定的远程服务器连接。
- **需要值：** 是 - 请求 ID，通常来自远程服务器监听器变量，例如 `$$request_id`

## 关闭所有远程服务器连接 (`close_all_remote_server_connections`)
- **说明：** 关闭 FancyMenu 打开的所有活动远程服务器连接。
- **需要值：** 否

## 在浏览器中打开 URL (`openlink`)
- **说明：** 在默认浏览器中打开链接
- **需要值：** 是 - `https://example.com`

## 复制文本到剪贴板 (`copytoclipboard`)
- **说明：** 将文本复制到剪贴板
- **需要值：** 是 - `text_to_copy`

## 打印到游戏日志 (`print_to_log`)
- **说明：** 向游戏日志写入一行内容
- **需要值：** 是 - `text_to_log`

## 设置变量值（FM 变量） (`set_variable`)
- **说明：** 将文本内容存储到 FancyMenu 变量中
- **需要值：** 是 - `variable_name:variable_value`

## 清除所有变量（FM 变量） (`clear_variables`)
- **说明：** 清除 FancyMenu 存储的**所有**变量
- **需要值：** 否

## 发送 HTTP 请求 (`send_http_request`)
- **说明：** 发送 HTTP 请求；可将响应存储到变量中
- **需要值：** 是 - HTTP 请求配置

> 此动作可让你向 REST API、webhook 或任何 HTTP 端点发送数据。
> 支持多种身份验证方式、自定义请求头以及不同的请求类型。
> 
> 此动作还允许你将请求响应存储到 FancyMenu 变量中，供以后使用！
{.is-info}

## 管理资源包 (`manage_resource_pack`)
- **说明：** 按显示名称启用/禁用/切换资源包（可选重新加载）
- **需要值：** 是 - `pack_name|||MODE|||reload_bool`

## 重新加载资源包 (`reload_resource_packs`)
- **说明：** 重新加载资源包（5 秒冷却）
- **需要值：** 否

## 重新加载 FancyMenu (`reloadmenu`)
- **说明：** 重新加载 FancyMenu，包括全景图、幻灯片和所有资源（较重）
- **需要值：** 否

> 此动作对**性能影响很大**，如果在 Ticker 中使用可能会导致卡顿。不建议在按钮之外的其他地方使用此动作。
{.is-warning}

## 切换元素动画器 (`toggle_element_animator`)
- **说明：** 切换元素动画器的播放状态
- **需要值：** 是 - `animator_identifier`

## 启用元素动画器 (`enable_element_animator`)
- **说明：** 启用一个元素动画器
- **需要值：** 是 - `animator_identifier`

## 禁用元素动画器 (`disable_element_animator`)
- **说明：** 禁用一个元素动画器
- **需要值：** 是 - `animator_identifier`

## 重置元素动画器 (`reset_element_animator`)
- **说明：** 重置元素动画器的时间线/状态
- **需要值：** 是 - `animator_identifier`

## 模仿原版/模组按钮 (`mimicbutton`)
- **说明：** 模仿原版或模组按钮的点击动作
- **需要值：** 是 - `screen_identifier:widget_locator`

## 模仿按键绑定 (`mimic_keybind`)
- **说明：** 执行一个 Minecraft 按键绑定（可选保持按住）
- **需要值：** 是 - `keybind_id|||keep_pressed_bool|||duration_ms`

## 设置文本输入框值 (`set_text_input_field_value`)
- **说明：** 按元素标识符设置自定义或原版输入框的值。
- **需要值：** 是 - `element_identifier|||new_value|||force_set_when_inactive`

## 在游戏目录中创建文件 (`create_file_in_game_dir`)
- **说明：** 在游戏目录（实例根目录）中创建一个空文件。支持 `.minecraft/` 前缀以定位默认启动器配置目录（可能与当前实例目录不同）。
- **需要值：** 是 - `file_path`

## 在游戏目录中删除文件/文件夹 (`delete_file_in_game_dir`)
- **说明：** 删除游戏目录（实例根目录）中的文件或文件夹。支持 `.minecraft/` 前缀以作用于默认启动器配置目录（可能与运行中的实例不同）。在路径后附加 `*` 可删除文件夹内**直接包含的所有文件**（忽略子目录；保留文件夹本身）。
- **需要值：** 是 - `target_path`

## 在游戏目录中复制文件/文件夹 (`copy_file_in_game_dir`)
- **说明：** 在游戏目录（实例根目录）内复制；`.minecraft/` 前缀会指向默认启动器配置目录（不一定是当前实例）。在**源**路径后附加 `*` 可复制该文件夹内直接包含的每个文件（忽略子目录）；目标必须是目录，且不能使用 `*`。
- **需要值：** 是 - `source||destination`

## 在游戏目录中移动文件/文件夹 (`move_file_in_game_dir`)
- **说明：** 在游戏目录（实例根目录）内移动；`.minecraft/` 前缀会指向默认启动器配置目录（可能与当前实例不同）。在**源**路径后附加 `*` 可移动该文件夹内直接包含的每个文件（忽略子目录）；目标必须是目录，且不能使用 `*`。
- **需要值：** 是 - `source||destination`

## 重命名游戏目录中的文件/文件夹 (`rename_file_in_game_dir`)
- **说明：** 重命名游戏目录（实例根目录）中的文件或文件夹；`.minecraft/` 前缀会指向默认启动器配置目录（可能与当前实例不同）。保留内容不变，只更改名称。
- **需要值：** 是 - `path||new_name`

## 下载文件到游戏目录 (`download_file_to_game_dir`)
- **说明：** 异步下载文件到游戏目录（实例根目录）；`.minecraft/` 前缀会指向默认启动器配置目录（不一定是运行中的实例）。请提供**目标文件夹**；文件名会根据响应头/URL 自动推导。
- **需要值：** 是 - `url||target_folder`

## 在游戏目录中解压 ZIP 文件 (`extract_zip_file_in_game_dir`)
- **说明：** 将 ZIP 文件解压到游戏目录或默认 `.minecraft` 目录中的目标文件夹。完成后会触发 **通过动作解压 ZIP** 监听器。
- **需要值：** 是 - `source_zip_path||target_folder_path`

## 在游戏目录中打开文件/文件夹 (`open_file_folder_in_game_dir`)
- **说明：** 使用操作系统默认应用打开文件或文件夹。出于安全原因，目标必须位于游戏目录或默认 `.minecraft` 目录内。
- **需要值：** 是 - `target_path`

## 在游戏目录中写入文件 (`write_file_in_game_dir`)
- **说明：** 在游戏目录（实例根目录）中写入或追加文本；`.minecraft/` 前缀会指向默认启动器配置目录（可能与此实例不同）。如果文件不存在会自动创建。值中支持 `\n` 以插入换行；追加模式由最后一个布尔值控制。
- **需要值：** 是 - `path|||content|||append_bool`

## 从系统选择文件 (`select_file_to_game_dir`)
- **说明：** 打开原生文件选择器（任意位置），并将所选文件复制到游戏目录（实例根目录）或带 `.minecraft/` 前缀时复制到默认 `.minecraft/`（该默认目录可能与当前实例不同）。支持扩展名筛选、自定义筛选标签以及可选的覆盖切换。
- **需要值：** 是 - 选择配置

## 显示提示气泡 (`show_toast`)
- **说明：** 显示一个可配置的提示气泡通知
- **需要值：** 是 - 提示气泡配置

## 启动调度器 (`start_scheduler`)
- **说明：** 按其调度器 ID 启动一个调度器。
- **需要值：** 是 - `scheduler_id`

## 停止调度器 (`stop_scheduler`)
- **说明：** 按其调度器 ID 停止一个调度器。
- **需要值：** 是 - `scheduler_id`

## 设置 Minecraft 选项 (`edit_minecraft_option`)
- **说明：** 编辑一个 Minecraft 配置选项
- **需要值：** 是 - `option_name:set_to_value`
