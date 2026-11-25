---
title: 监听器
description: 在游戏中发生事件时运行动作脚本，例如按下按键、收到聊天消息或解锁新进度。
sourceBlobSha: b8417f6287ac413d2d44e0fc5c2383c0b0fa6e1e
---

# 监听器

监听器会在游戏中发生事件时运行一个[动作脚本](/action-scripts)：例如按下按键、打开屏幕、解锁进度等等。它们在所有菜单中以及游戏过程中都能运行，并且不属于任何布局。

大多数监听器还会向脚本提供有关事件的信息，例如所按按键的名称。

<img width="800" alt="在标题屏幕上按下按键，提示框显示每个所按按键的名称" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/listeners_trigger.gif?raw=true">

> [!CAUTION]
> 即使当前没有打开任何菜单，监听器也可以运行文件、网络、命令、剪贴板、资源包和链接操作。只使用来自你信任的配置文件和文件的监听器。

# 添加监听器

<img width="800" alt="打开 Manage Listeners，添加一个带有 Show Toast 操作的 On Keyboard Key Pressed 监听器，然后按 H 进行测试" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/listeners_make.gif?raw=true">

1. 打开 **菜单栏 -> 自定义 -> 管理监听器**。
2. 点击 **添加监听器**。
3. 在 **可用监听器** 中点击事件。搜索栏可以根据名称和描述查找监听器。
   - **监听器描述**会显示监听器的作用以及它提供的变量。
   - **复制变量到剪贴板**会复制该监听器变量的名称。
   - **弹出描述**会在单独的窗口中打开描述。
4. 点击 **完成**，或双击该监听器。随后会打开动作脚本编辑器。
5. 添加要运行的操作，然后点击 **完成**。请参阅[动作脚本](/action-scripts#making-an-action-script)。
6. 在 **管理监听器** 中点击 **完成**以保存。监听器会立即生效。

点击 **取消** 后，在确认提示出现后，**管理监听器**中所做的所有更改都会被丢弃。

# 管理监听器

<img width="800" alt="管理监听器窗口中有五个监听器，其中一个已选中，右侧显示其动作脚本" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/listeners_manage.png?raw=true">

- 点击某个监听器，可在右侧查看其类型和动作脚本。
- 点击 **编辑操作**，或右键点击某个监听器，可以打开其动作脚本。
- 双击监听器名称可重命名，例如 `帮助按键`。按 `Enter` 保存名称，按 `Esc` 取消。名称留空时会再次显示监听器类型。
- **移除监听器**会删除选中的监听器。
- **导出供 AI 使用**会复制选中的监听器或所有监听器，以便用于[AI 聊天](/export-for-ai)；其中包含尚未保存的更改。

监听器保存在 `config/fancymenu/listener_instances.txt` 中（请参阅[数据存储位置](/data-storage-locations)）。每个[配置文件](/profiles)都有各自的监听器。

# 监听器变量

监听器变量以 `$$` 开头，在其脚本中可用于任何位置：包括每个操作值，以及[IF 语句](/action-scripts#if-else-if-and-else)的条件中。变量名区分大小写。下方列出了每个监听器的变量，其描述也会显示在监听器选择器中。

<img width="800" alt="监听器选择器中选中了 On Achievement Unlocked，其描述列出了对应变量" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/listeners_choose.png?raw=true">

例如，下面的监听器会在按下 `H` 时打开帮助屏幕：

1. 添加一个 **On Keyboard Key Pressed** 监听器。
2. 在脚本中使用 **添加 IF 语句**，并添加 [**是文本**](/conditions#is-text)条件。将 **比较模式**设为 **等于**，将 **文本**设为 `$$key_name`，并将 **比较文本**设为 `H`。
3. 在 IF 语句中，添加[**打开屏幕或自定义 GUI**](/action-scripts#open-screen-or-custom-gui)，并选择你的帮助屏幕。

有关监听器变量的更多信息：

- 监听器变量始终是文本。如果监听器无法获取某个值，变量会使用备用值，例如 `ERROR`、`UNKNOWN`、`NONE`、`EMPTY`、`0`、`-1` 或空值。
- 监听器变量会先于[占位符](/placeholders)填充，因此也可以在占位符中使用。
- 监听器变量只在其脚本运行期间存在。若要保留某个值，请使用[**设置变量值（FM Variable）**](/action-scripts#set-variable-value-fm-variable)将其保存到你的某个[变量](/variables)中。
- 通过 **菜单栏 -> 自定义 -> 管理变量**创建的自定义变量也可以在监听器脚本中使用：使用 `$$` 加变量名，例如 `$$coins`。如果自定义变量与监听器变量同名，那么 `$$name` 指的是监听器变量。名称更长的自定义变量（例如 `key_name_log`）仍然可以正常使用。
- 聊天、服务器、文件及其他玩家提供的文本可能包含任何内容。切勿将其直接放入命令、文件路径或链接中。

# 注意事项

- 某些监听器需要服务器端安装 FancyMenu，下文会特别说明。在单人游戏中，它们始终可用。
- 有些监听器会非常频繁地运行，例如 **On Mouse Moved in Screen**、**On Element Scrolled**、**On Position Changed** 和 **On World Sound Triggered**。请保持这些监听器的脚本简短，切勿在其中使用[**重新加载 FancyMenu**](/action-scripts#reload-fancymenu)等耗时操作。
- 若要使用 **On Screen Opened** 替换屏幕，请先通过 IF 语句检查 `$$screen_identifier`。否则每个屏幕都会被替换，包括你刚打开的屏幕。

# 所有监听器

以下按触发条件列出了 FancyMenu 中的所有监听器。

## 键盘和鼠标

若要检查按下的是哪个按键，请使用 `$$key_name`。按键的代码编号在不同 Minecraft 版本中并不相同。

### On Keyboard Key Pressed

**标识符：** `keyboard_key_pressed`

在菜单中或游戏过程中按下按键时运行。按住按键期间，它会反复运行。

- `$$key_name`：按键名称，例如 `H` 或 `Left Shift`
- `$$key_keycode`：按键的代码编号
- `$$key_scancode`：按键的扫描码
- `$$key_modifiers`：同时按住的修饰键（例如 `Shift` 和 `Ctrl`）对应的数值

### On Keyboard Key Released

**标识符：** `keyboard_key_released`

在菜单中或游戏过程中松开按键时运行。

它提供与 **On Keyboard Key Pressed** 相同的变量：`$$key_name`、`$$key_keycode`、`$$key_scancode` 和 `$$key_modifiers`。

### On Keyboard Character Typed in Screen

**标识符：** `keyboard_char_typed`

屏幕打开时，每输入一个字符都会运行一次。

- `$$char`：输入的字符

### On Mouse Moved in Screen

**标识符：** `mouse_moved`

屏幕打开时，每次鼠标移动都会运行。

- `$$mouse_pos_x`、`$$mouse_pos_y`：鼠标在 GUI 像素坐标中的位置
- `$$mouse_move_delta_x`、`$$mouse_move_delta_y`：鼠标自上次触发以来移动的距离

### On Mouse Button Clicked

**标识符：** `mouse_button_clicked`

在菜单中或游戏过程中按下鼠标按键时运行一次。

- `$$button`：`left`、`right` 或 `middle`。其他按键会返回其编号。
- `$$mouse_pos_x`、`$$mouse_pos_y`：鼠标在 GUI 像素坐标中的位置

### On Mouse Button Released

**标识符：** `mouse_button_released`

在菜单中或游戏过程中松开鼠标按键时运行一次。

它提供与 **On Mouse Button Clicked** 相同的变量：`$$button`、`$$mouse_pos_x` 和 `$$mouse_pos_y`。

### On Mouse Scrolled in Screen

**标识符：** `mouse_scrolled`

屏幕打开时滚动鼠标滚轮会触发此监听器。

- `$$scroll_delta_y`：滚轮滚动的幅度。向上滚动时大于 `0`，向下滚动时小于 `0`。

## 屏幕和元素

### On Screen Opened

**标识符：** `screen_open`

屏幕打开后立即运行。其脚本中的[**打开屏幕或自定义 GUI**](/action-scripts#open-screen-or-custom-gui)操作可以将当前屏幕替换为另一个屏幕。

- `$$screen_identifier`：屏幕的[标识符](/screen-identifiers)

### On Screen Closed

**标识符：** `screen_close`

屏幕关闭后立即运行。

- `$$screen_identifier`：已关闭屏幕的[标识符](/screen-identifiers)

### On Markdown Text Clicked

**标识符：** `text_clicked`

有人点击文本中的[点击事件](/text-formatting#click-and-hover-events)时运行，例如 `[查看规则](click:open_rules)`。

- `$$text_event_id`：事件 ID，例如 `open_rules`

### On Markdown Text Hovered

**标识符：** `text_hovered`

鼠标移到文本中的[悬停事件](/text-formatting#click-and-hover-events)上时运行，例如 `[这是什么？](hover:show_hint)`。

- `$$text_event_id`：事件 ID，例如 `show_hint`

### On Element Scrolled

**标识符：** `scroll_area_scrolled`

[可滚动区域](/scrollable-areas)或[文本元素](/text-in-menus)的内容每次移动时都会运行。内容平滑滚动时，每一帧都会运行。在布局编辑器中不会运行。

- `$$element_identifier`：元素的[标识符](/element-identifiers)
- `$$scroll_x`：内容横向滚动的距离，单位为像素
- `$$scroll_y`：内容向下滚动的距离，单位为像素
- `$$scroll_percent`：内容沿元素主要滚动方向滚动的百分比，从 `0`（起点）到 `100`（终点）

### On Element Scrolled to Start

**标识符：** `scroll_area_reached_start`

可滚动区域或文本元素的内容滚回起点时运行。

它提供与 **On Element Scrolled** 相同的变量：`$$element_identifier`、`$$scroll_x`、`$$scroll_y` 和 `$$scroll_percent`。

### On Element Scrolled to End

**标识符：** `scroll_area_reached_end`

可滚动区域或文本元素的内容滚到末尾时运行，例如有人滚动看完所有规则时。

它提供与 **On Element Scrolled** 相同的变量：`$$element_identifier`、`$$scroll_x`、`$$scroll_y` 和 `$$scroll_percent`。

### Animated Texture Started Playing

**标识符：** `animated_texture_started_playing`

[动态纹理](/animations)（GIF、APNG 或 FMA）开始播放时，以及每次重新开始播放时运行。

- `$$texture_source`：纹理来源，可以是文件路径、网页链接或资源位置
- `$$texture_source_type`：`LOCAL`、`WEB` 或 `RESOURCE_LOCATION`
- `$$texture_will_restart`：如果播放完本轮后会重新开始，则为 `true`；否则为 `false`

### Animated Texture Finished Playing

**标识符：** `animated_texture_finished_playing`

动态纹理播放完一轮时运行。如果纹理会循环播放，则会在重新开始前运行。

它提供与 **Animated Texture Started Playing** 相同的变量：`$$texture_source`、`$$texture_source_type` 和 `$$texture_will_restart`。

### Video Playback Status Changed

**标识符：** `video_playback_status_changed`

[视频](/video)元素或菜单背景视频开始播放、暂停、停止或播放结束时运行。

- `$$video_source`：视频来源，可以是文件路径、网页链接或资源位置
- `$$video_source_type`：`LOCAL`、`WEB` 或 `RESOURCE_LOCATION`
- `$$is_looping`：视频循环播放时为 `true`，否则为 `false`
- `$$new_status`：
  - `PLAYING`：视频开始播放或从暂停状态恢复
  - `PAUSED`：视频已暂停
  - `STOPPED`：视频已停止
  - `FINISHED`：视频播放完毕。循环视频也会触发此状态，并且会在重新开始播放前触发。

## 变量、文件和数据

### On Variable Updated [FM Variable]

**标识符：** `fm_variable_updated`

每次设置[变量](/variables)时都会运行。

- `$$var_name`：变量名称
- `$$old_value`：变量更新前的值
- `$$new_value`：变量的新值

对于列表变量，两个值都会以 JSON 数组的形式返回整个列表，例如 `["Diamonds","Emeralds"]`。

### On File Download Started via Action

**标识符：** `file_download_started_via_action`

通过[**将文件下载到游戏目录**](/action-scripts#download-file-to-game-directory)开始下载文件时运行，此时文件名已确定。下载完成后，文件才会出现在对应路径中；若要知道文件何时可用，请使用 **On File Downloaded via Action**。

- `$$download_url`：文件的链接
- `$$target_file_path`：文件的保存路径

### On File Downloaded via Action

**标识符：** `file_downloaded_via_action`

通过[**将文件下载到游戏目录**](/action-scripts#download-file-to-game-directory)进行的下载完成或失败时运行。

- `$$download_url`：文件的链接
- `$$target_file_path`：文件保存的位置。下载失败时，该值可能只包含文件夹路径。
- `$$download_succeeded`：`true` 或 `false`

### On File Selected

**标识符：** `file_selected_via_action`

[**从系统中选择文件**](/action-scripts#select-file-from-system)操作结束时运行：文件已复制、文件选择器已取消，或操作发生错误。

- `$$selected_file_path`：所选文件的完整路径。取消文件选择器时为空。
- `$$target_file_path`：文件复制到游戏文件夹后的路径
- `$$selection_succeeded`：文件复制成功时为 `true`
- `$$selection_cancelled`：未选择文件便关闭文件选择器时为 `true`
- `$$failure_reason`：错误原因。未发生错误时为空。

### On ZIP Extracted via Action

**标识符：** `zip_extracted_via_action`

[**在游戏目录中解压 ZIP 文件**](/action-scripts#extract-zip-file-in-game-directory)操作结束时运行。

- `$$source_zip_path`：ZIP 文件的路径
- `$$target_folder_path`：解压目标文件夹的路径
- `$$extract_succeeded`：`true` 或 `false`
- `$$failure_reason`：错误原因。未发生错误时为空。

游戏文件夹中的路径以 `/` 开头，例如 `/config/fancymenu/assets/pack.zip`。`.minecraft` 文件夹中的路径以 `.minecraft/` 开头。

### On FM Data Received

**标识符：** `fm_data_received`

服务器通过 `/fmdata send` 向此玩家发送数据时运行。请参阅 [FM 数据](/fm-data)。

- `$$data_identifier`：发送数据时使用的标识符
- `$$data`：数据
- `$$sent_by`：服务器的 IP 地址；单人游戏中为 `integrated_server`

### On Remote Server Connected

**标识符：** `remote_server_connected`

[远程服务器连接](/remote-server-communication)建立时运行。

- `$$request_id`：连接的请求 ID
- `$$remote_server_url`：远程服务器的链接

### On Remote Server Data Received

**标识符：** `remote_server_data_received`

已连接的远程服务器每次发送文本时都会运行。

- `$$request_id`：连接的请求 ID
- `$$remote_server_url`：远程服务器的链接
- `$$data`：服务器发送的文本

### On Remote Server Connection Closed

**标识符：** `remote_server_connection_closed`

远程服务器连接关闭时运行。

- `$$request_id`：连接的请求 ID
- `$$remote_server_url`：远程服务器的链接
- `$$intentionally_closed`：通过[**关闭远程服务器连接**](/action-scripts#close-remote-server-connection)关闭连接时为 `true`
- `$$crashed`：连接崩溃时为 `true`
- `$$unknown_close_reason`：连接因未知原因关闭时为 `true`

## 游戏、世界和服务器

### On Quit Minecraft

**标识符：** `quit_minecraft`

游戏开始关闭时运行一次。

- `$$timestamp_millis`：时间戳，单位为毫秒，自 1970 年起计算
- `$$timestamp_iso`：ISO-8601 格式的时间文本，例如 `2026-11-24T18:30:00.123Z`

### On Screenshot Taken

**标识符：** `screenshot_taken`

截图被拍摄并保存时运行，例如按下截图键时。

- `$$screenshot_path`：游戏文件夹中截图的路径，例如 `/screenshots/2026-10-29_14.30.00.png`

### Singleplayer World Entered

**标识符：** `world_entered`

单人世界加载完成且玩家可以移动时运行。

- `$$world_name`：世界名称
- `$$world_save_path`：世界存档文件夹的完整路径
- `$$world_difficulty`：世界难度
- `$$world_cheats_allowed`：启用作弊时为 `true`
- `$$world_icon_path`：世界图标的完整路径
- `$$world_is_first_join`：世界创建后首次进入时为 `true`

### Singleplayer World Left

**标识符：** `world_left`

单人世界关闭并保存后运行。

它提供与 **Singleplayer World Entered** 相同的变量，但不包含 `$$world_is_first_join`：`$$world_name`、`$$world_save_path`、`$$world_difficulty`、`$$world_cheats_allowed` 和 `$$world_icon_path`。

### On Start Joining Server

**标识符：** `start_joining_server`

游戏开始连接服务器或 Realm 时、加入之前运行。即使连接失败或被取消，也会运行，因此可以记住服务器信息，例如用于断开连接屏幕上的重新连接按钮。

- `$$server_ip`：服务器的 IP 地址

### On Server Joined

**标识符：** `server_joined`

加入多人游戏服务器后运行。

- `$$server_ip`：服务器的 IP 地址

### On Server Left

**标识符：** `server_left`

离开多人游戏服务器后运行。

- `$$server_ip`：服务器的 IP 地址

### On Other Player Joined World/Server

**标识符：** `other_player_joined_world`

其他玩家加入你的世界或服务器时运行。

- `$$player_name`：玩家名称
- `$$player_uuid`：玩家的 UUID

### On Other Player Left World/Server

**标识符：** `other_player_left_world`

其他玩家离开你的世界或服务器时运行。

- `$$player_name`：玩家名称
- `$$player_uuid`：玩家的 UUID

### On Other Player Died

**标识符：** `other_player_died`

你的世界中有其他玩家死亡时运行。

- `$$player_name`：玩家名称
- `$$player_uuid`：玩家的 UUID
- `$$death_pos_x`、`$$death_pos_y`、`$$death_pos_z`：玩家死亡的位置

## 聊天

### On Chat Message Received

**标识符：** `chat_message_received`

玩家发送的聊天消息显示在你的聊天窗口中时运行。

- `$$chat_message_string`：纯文本形式的消息
- `$$chat_message_component`：JSON 文本组件形式的消息
- `$$sender_uuid`：发送者的 UUID；未知时为 `ERROR`
- `$$sender_name`：发送者的名称；未知时为 `ERROR`

### On Chat Message Sent

**标识符：** `chat_message_sent`

你发送聊天消息时运行。命令不算聊天消息。

- `$$chat_message_string`：纯文本形式的消息
- `$$chat_message_component`：JSON 文本组件形式的消息

### On System Message Received in Chat

**标识符：** `system_message_received_in_chat`

非玩家发送的消息显示在聊天窗口中时运行，例如命令的反馈消息。

- `$$system_message_string`：纯文本形式的消息
- `$$system_message_component`：JSON 文本组件形式的消息

## 玩家

### On Death

**标识符：** `player_death`

死亡屏幕打开后立即运行。

- `$$days_survived`：自上次死亡以来在游戏中度过的天数，向下取整
- `$$death_reason_string`：纯文本形式的死亡消息
- `$$death_reason_component`：JSON 文本组件形式的死亡消息
- `$$death_pos_x`、`$$death_pos_y`、`$$death_pos_z`：你的死亡位置

### On Damage Taken

**标识符：** `damage_taken`

每次受到攻击时运行一次。

- `$$damage_amount`：此次攻击造成的生命值损失
- `$$damage_type`：伤害类型，例如 `minecraft:fall`
- `$$is_fatal_damage`：此次攻击导致你死亡时为 `true`
- `$$damage_source`：造成伤害的实体类型，例如 `minecraft:zombie`；没有时为 `NONE`

### On Effect Gained

**标识符：** `effect_gained`

获得状态效果时运行一次。

- `$$effect_key`：效果，例如 `minecraft:speed`
- `$$effect_type`：`positive`、`negative` 或 `neutral`
- `$$effect_duration`：效果持续时间，单位为刻（20 刻为 1 秒）

### On Effect Lost

**标识符：** `effect_lost`

状态效果结束时运行一次。

- `$$effect_key`：效果，例如 `minecraft:speed`
- `$$effect_type`：`positive`、`negative` 或 `neutral`

### On Experience Changed

**标识符：** `experience_changed`

经验值增加或减少时都会运行。

- `$$new_experience_amount`：当前经验总值
- `$$old_experience_amount`：更新前的经验总值
- `$$is_level_up`：升到新等级时为 `true`

### On Achievement Unlocked

**标识符：** `achievement_unlocked`

解锁进度时运行一次。加入世界时已经完成的进度不算。

- `$$achievement_key`：进度，例如 `minecraft:story/mine_diamond`
- `$$achievement_label`：进度标题，使用游戏语言
- `$$achievement_description`：进度描述，使用游戏语言
- `$$achievement_icon_item_key`：进度图标对应的物品，例如 `minecraft:diamond`
- `$$achievement_type`：`advancement`、`goal` 或 `challenge`

### On Jump

**标识符：** `jump`

每次跳跃时运行。此监听器没有变量。

### On Started Running

**标识符：** `started_running`

开始疾跑时运行一次。此监听器没有变量。

### On Stopped Running

**标识符：** `stopped_running`

停止疾跑时运行一次。此监听器没有变量。

### On Position Changed

**标识符：** `position_changed`

移动到另一个方块时运行。

- `$$old_pos_x`、`$$old_pos_y`、`$$old_pos_z`：之前所在的方块坐标
- `$$new_pos_x`、`$$new_pos_y`、`$$new_pos_z`：新的方块坐标

### On Started Burning

**标识符：** `started_burning`

开始着火时运行一次。此监听器没有变量。

### On Stopped Burning

**标识符：** `stopped_burning`

停止着火时运行一次。此监听器没有变量。

### On Started Drowning

**标识符：** `started_drowning`

开始受到溺水伤害时运行一次。此监听器没有变量。

### On Started Freezing

**标识符：** `started_freezing`

开始冻结时运行一次，例如身处细雪中时。

- `$$freezing_intensity`：冻结程度，从 `0.0`（完全未冻）到 `1.0`（完全冻结）

### On Stopped Freezing

**标识符：** `stopped_freezing`

停止冻结时运行一次。此监听器没有变量。

### On Fully Frozen

**标识符：** `fully_frozen`

完全冻结时运行一次。此监听器没有变量。

### On Start Swimming

**标识符：** `start_swimming`

开始游泳时运行一次。

- `$$fluid_type`：流体类型，例如 `minecraft:water`

### On Stop Swimming

**标识符：** `stop_swimming`

停止游泳时运行一次。

- `$$fluid_type`：流体类型，例如 `minecraft:water`

### On Start Touching Fluid

**标识符：** `start_touching_fluid`

开始接触流体（例如水或熔岩）时运行一次。

- `$$fluid_type`：流体类型，例如 `minecraft:lava`

### On Stop Touching Fluid

**标识符：** `stop_touching_fluid`

停止接触流体时运行一次。

- `$$fluid_type`：流体类型，例如 `minecraft:lava`

## 物品

### On Item Picked Up

**标识符：** `item_picked_up`

拾取物品时运行一次。

- `$$item_key`：物品，例如 `minecraft:diamond`

### On Item Dropped

**标识符：** `item_dropped`

从物品栏中丢弃物品时运行一次。

- `$$item_key`：物品，例如 `minecraft:diamond`

### On Item Consumed

**标识符：** `item_consumed`

吃完或喝完物品时运行一次。

- `$$item_key`：物品，例如 `minecraft:golden_apple`

### On Item Used

**标识符：** `item_used`

使用物品时运行一次。

- `$$item_key`：物品，例如 `minecraft:flint_and_steel`
- `$$used_on_type`：使用目标类型：`block`、`entity`、`self` 或 `none`
- `$$used_on_entity_key`：使用目标实体的类型。没有实体目标时为空。
- `$$used_on_block_key`：使用目标方块。没有方块目标时为空。
- `$$target_pos_x`、`$$target_pos_y`、`$$target_pos_z`：使用目标的位置；没有目标时为 `-1`

### On Item Broke

**标识符：** `item_broke`

物品栏中的物品损坏时运行一次。

- `$$item_key`：物品，例如 `minecraft:iron_pickaxe`
- `$$item_type`：`tool`、`armor` 或 `other`

### On Item Hovered In Inventory

**标识符：** `item_hovered_in_inventory`

鼠标移到任意物品栏中的物品上时运行一次，例如自己的物品栏或箱子。

- `$$item_key`：物品，例如 `minecraft:diamond_sword`
- `$$item_display_name_string`：纯文本形式的物品名称
- `$$item_display_name_json`：JSON 文本组件形式的物品名称

## 方块

### On Start Looking At Block

**标识符：** `start_looking_at_block`

准星开始指向一个方块时运行一次，方块最远可在 20 个方块之外。

- `$$block_key`：方块，例如 `minecraft:oak_log`
- `$$block_pos_x`、`$$block_pos_y`、`$$block_pos_z`：方块坐标
- `$$distance_to_player`：从你的眼睛到准星所指位置的距离

### On Stop Looking At Block

**标识符：** `stop_looking_at_block`

准星不再指向某个方块时运行一次。

它会针对之前注视的方块提供与 **On Start Looking At Block** 相同的变量：`$$block_key`、`$$block_pos_x`、`$$block_pos_y`、`$$block_pos_z` 和 `$$distance_to_player`。

### On Block Broke

**标识符：** `block_broke`

破坏方块时运行一次。

- `$$block_key`：方块，例如 `minecraft:stone`
- `$$broke_with_item_key`：手中物品，例如 `minecraft:iron_pickaxe`；没有物品时为 `EMPTY`
- `$$block_pos_x`、`$$block_pos_y`、`$$block_pos_z`：方块坐标

### On Block Placed

**标识符：** `block_placed`

放置方块时运行一次。

- `$$block_key`：方块，例如 `minecraft:torch`
- `$$block_pos_x`、`$$block_pos_y`、`$$block_pos_z`：方块坐标

### On Interacted With Block

**标识符：** `interacted_with_block`

与方块交互时运行一次，例如打开箱子或按下按钮。

- `$$block_key`：方块，例如 `minecraft:chest`
- `$$block_pos_x`、`$$block_pos_y`、`$$block_pos_z`：方块坐标

### On Stepping On Block

**标识符：** `stepping_on_block`

踏上方块时运行一次。

- `$$block_key`：方块，例如 `minecraft:grass_block`
- `$$block_pos_x`、`$$block_pos_y`、`$$block_pos_z`：方块坐标

## 实体

### On Start Looking At Entity

**标识符：** `start_looking_at_entity`

准星开始指向某个实体时运行一次，实体最远可在 20 个方块之外。

- `$$entity_key`：实体类型，例如 `minecraft:villager`
- `$$distance_to_player`：从你的眼睛到准星所指位置的距离
- `$$entity_pos_x`、`$$entity_pos_y`、`$$entity_pos_z`：实体坐标
- `$$entity_uuid`：实体的 UUID

### On Stop Looking At Entity

**标识符：** `stop_looking_at_entity`

准星不再指向某个实体时运行一次。

它会针对之前注视的实体提供与 **On Start Looking At Entity** 相同的变量：`$$entity_key`、`$$distance_to_player`、`$$entity_pos_x`、`$$entity_pos_y`、`$$entity_pos_z` 和 `$$entity_uuid`。

### On Entity Starts Being In Sight

**标识符：** `entity_starts_being_in_sight`

实体出现在你的屏幕中时运行一次，实体最远可在 200 个方块之外。

- `$$entity_key`：实体类型，例如 `minecraft:creeper`
- `$$distance_to_player`：从你的眼睛到实体的距离
- `$$entity_pos_x`、`$$entity_pos_y`、`$$entity_pos_z`：实体坐标
- `$$entity_uuid`：实体的 UUID

### On Entity Stops Being In Sight

**标识符：** `entity_stops_being_in_sight`

可见实体离开屏幕，或距离超过 200 个方块时运行一次。

它提供与 **On Entity Starts Being In Sight** 相同的变量：`$$entity_key`、`$$distance_to_player`、`$$entity_pos_x`、`$$entity_pos_y`、`$$entity_pos_z` 和 `$$entity_uuid`。

### On Interacted With Entity

**标识符：** `entity_interacted`

与实体交互时运行一次，例如与村民交易。

- `$$entity_key`：实体类型，例如 `minecraft:villager`
- `$$entity_pos_x`、`$$entity_pos_y`、`$$entity_pos_z`：实体坐标
- `$$entity_uuid`：实体的 UUID

### On Entity Mounted

**标识符：** `entity_mounted`

开始骑乘实体时运行一次，例如骑马或乘船。

- `$$entity_key`：实体类型，例如 `minecraft:horse`
- `$$entity_pos_x`、`$$entity_pos_y`、`$$entity_pos_z`：实体坐标
- `$$entity_uuid`：实体的 UUID

### On Entity Unmounted

**标识符：** `entity_unmounted`

停止骑乘实体时运行一次。

- `$$entity_key`：实体类型，例如 `minecraft:horse`
- `$$entity_pos_x`、`$$entity_pos_y`、`$$entity_pos_z`：实体坐标
- `$$entity_uuid`：实体的 UUID

### On Entity Spawned

**标识符：** `entity_spawned`

需要在服务器端安装 FancyMenu。世界中任何位置生成实体时都会运行，即使实体在很远的地方或位于其他维度。

- `$$entity_key`：实体类型，例如 `minecraft:zombie`
- `$$distance_to_player`：实体与你的距离；实体在其他维度时为 `-1`
- `$$entity_pos_x`、`$$entity_pos_y`、`$$entity_pos_z`：实体生成的位置
- `$$entity_uuid`：实体的 UUID
- `$$dimension_key`：维度，例如 `minecraft:overworld`
- `$$is_same_dimension_as_player`：实体在你所在维度生成时为 `true`

### On Entity Died

**标识符：** `entity_died`

需要在服务器端安装 FancyMenu。世界中任何位置的实体死亡时都会运行，即使实体在很远的地方或位于其他维度。

- `$$entity_key`：实体类型，例如 `minecraft:ender_dragon`
- `$$distance_to_player`：实体与你的距离；实体在其他维度时为 `-1`
- `$$death_pos_x`、`$$death_pos_y`、`$$death_pos_z`：实体死亡的位置
- `$$entity_uuid`：实体的 UUID
- `$$dimension_key`：维度，例如 `minecraft:the_end`
- `$$damage_type`：致死伤害的类型，例如 `minecraft:player_attack`
- `$$is_same_dimension_as_player`：实体在你所在维度死亡时为 `true`
- `$$entity_killed_by_name`：击杀者名称；未知时为 `NONE`
- `$$entity_killed_by_key`：击杀者类型，例如 `minecraft:player`；未知时为 `NONE`
- `$$entity_killed_by_uuid`：击杀者的 UUID；未知时为 `NONE`

## 世界和地点

### On Enter Biome

**标识符：** `enter_biome`

进入另一个生物群系时运行一次。

- `$$biome_key`：生物群系，例如 `minecraft:cherry_grove`

### On Leave Biome

**标识符：** `leave_biome`

离开某个生物群系时运行一次。

- `$$biome_key`：离开的生物群系，例如 `minecraft:cherry_grove`

### On Enter Structure

**标识符：** `enter_structure`

需要在服务器端安装 FancyMenu。进入结构区域时运行一次。区域判定并不精确，因此在结构附近或上方也可能触发，例如下方有废弃矿井时。若只想检测进入结构内部，请使用 **On Enter Structure (High Precision)**。

- `$$structure_key`：结构，例如 `minecraft:village_plains`

### On Leave Structure

**标识符：** `leave_structure`

需要在服务器端安装 FancyMenu。离开结构区域时运行一次，区域判定精度与 **On Enter Structure** 相同。

- `$$structure_key`：离开的结构

### On Enter Structure (High Precision)

**标识符：** `enter_structure_high_precision`

需要在服务器端安装 FancyMenu。进入结构内部时运行一次。

- `$$structure_key`：结构，例如 `minecraft:stronghold`

### On Leave Structure (High Precision)

**标识符：** `leave_structure_high_precision`

完全离开结构时运行一次。

- `$$structure_key`：离开的结构

### On Dimension Entered

**标识符：** `enter_dimension`

进入另一个维度时运行一次。

- `$$dimension_key`：维度，例如 `minecraft:the_nether`

### On Weather Changed

**标识符：** `weather_changed`

天气发生变化时运行一次。你所在位置的天气变化也会触发：即使正在下雨，走进沙漠、雪原生物群系或建筑中也算。

- `$$weather_type`：`clear`、`rain` 或 `thunder`
- `$$weather_can_snow`：你所在位置会下雪时为 `true`
- `$$weather_can_rain`：你所在位置会下雨时为 `true`

### On Raid Started

**标识符：** `raid_started`

需要在服务器端安装 FancyMenu。你位于袭击区域内且袭击开始时运行，此时袭击进度条会显示。此监听器没有变量。

如果你走进一个已经开始的袭击区域，则不会触发。此时请使用 **On Enter Active Raid Area**。

### On Enter Active Raid Area

**标识符：** `enter_active_raid_area`

需要在服务器端安装 FancyMenu。走进已经开始的袭击区域时运行，此时袭击进度条会显示。此监听器没有变量。

### On Leave Active Raid Area

**标识符：** `leave_active_raid_area`

需要在服务器端安装 FancyMenu。离开袭击区域时运行，此时袭击进度条会消失。在该区域内死亡或切换维度也会触发，但袭击结束不会触发。此监听器没有变量。

### On Raid Finished

**标识符：** `raid_finished`

需要在服务器端安装 FancyMenu。你位于袭击区域内且袭击结束时运行。

- `$$raid_result`：`victory` 或 `defeat`

## 音效和音乐

### On Music Track Started

**标识符：** `music_track_started`

音乐曲目开始播放时运行一次。

- `$$track_resource_location`：曲目的音频文件
- `$$track_display_name`：曲目名称；未知时为 `UNKNOWN`
- `$$track_artist`：曲目艺术家；未知时为 `UNKNOWN`
- `$$track_duration_ms`：曲目时长，单位为毫秒；未知时为 `0`

### On Music Track Stopped

**标识符：** `music_track_stopped`

音乐曲目停止时运行一次，原因可能是播放结束或被另一首曲目替换。

它提供与 **On Music Track Started** 相同的变量：`$$track_resource_location`、`$$track_display_name`、`$$track_artist` 和 `$$track_duration_ms`。

### On World Sound Triggered

**标识符：** `world_sound_triggered`

你附近的世界中每次有音效开始播放时都会运行，例如门声或苦力怕的声音。

- `$$sound_resource_location`：音效文件
- `$$sound_display_name`：音效的字幕；未知时为 `UNKNOWN`
- `$$sound_origin_pos_x`、`$$sound_origin_pos_y`、`$$sound_origin_pos_z`：音效来源的位置
- `$$sound_origin_distance_to_player`：音效与你的距离
- `$$sound_origin_direction_from_player`：音效相对于你所面朝方向的角度，范围为 0 到 360 度
