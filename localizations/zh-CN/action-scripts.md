---
title: 动作脚本
description: 如何将动作脚本与按钮、滑块、计数器等一起使用。
---
# 动作脚本

当 [Button](./elements#button) 被点击、[Ticker](./elements#ticker) 更新、[Slider](./elements#slider) 变化、屏幕打开或关闭，或发生其他受支持的事件时，动作脚本会运行已配置的任务。诸如 **if**、**else-if**、**else** 和 **while** 之类的语句可添加条件控制。

> [!CAUTION]
> 导入的动作脚本可能会修改文件、连接服务器、打开链接或运行命令。请仅使用你信任的来源。

<img src="https://github.com/Keksuccino/FancyMenu/blob/master/assets/docs/action_script_editor.png?raw=true" alt="动作脚本编辑器" style="max-width:800px;width:100%;height:auto;">

# 什么是动作？

**动作**是 FancyMenu 在触发时执行的任务或操作。例如，某个动作可以打开一个新界面、发送聊天消息，或调整 [Audio element](./elements#audio) 的音量。在 FancyMenu 的编辑器中，动作可以配合一个值进行配置（如需要），以提供更多细节——例如 URL 或服务器地址。

# 语句

为了创建更复杂的行为，FancyMenu 在动作脚本中支持控制语句：

| 语句 | 行为 |
|---|---|
| **If** | 仅当其 [条件](./conditions) 满足时才运行其动作。 |
| **Else-If** | 当前面的 **If** 或 **Else-If** 没有运行时，检查另一组 [条件](./conditions)。 |
| **Else** | 当前面所有 **If** 或 **Else-If** 的条件都不满足时运行。 |
| **While** | 在其 [条件](./conditions) 仍为真时重复执行其动作。为防止无限循环，它会在三秒后停止；不要把它当作计时器使用。 |

# 块

脚本中可以添加块，以便更好地控制脚本执行流程/时机，并提供一些实用的易用性功能：

| 块 | 行为 |
|---|---|
| **Delay** | 开始倒计时，但不会停止脚本其余部分。其嵌套动作会在延迟结束后变为可执行；屏幕重新初始化会重置倒计时。 |
| **Execute Later** | 每次到达该块时，都会在延迟结束后安排一次新的嵌套动作执行。 |
| **Comment** | 在脚本中添加备注用于整理，不会执行任何动作。 |

# 脚本执行

动作按从上到下的顺序运行。失败的动作会被记录，然后脚本继续执行。

下载、ZIP 解压和 HTTP 请求会稍后完成；下一个动作不会等待它们完成。若后续工作依赖结果，请使用 [**On File Downloaded via Action**](./listeners#on-file-downloaded-via-action-file_downloaded_via_action)、[**On ZIP Extracted via Action**](./listeners#on-zip-extracted-via-action-zip_extracted_via_action) 或 HTTP 响应变量。

# 在哪里可以使用动作脚本？

动作脚本用途广泛，可用于布局中的多个位置。你可以将它们分配给，例如：

- [**Buttons**](./elements#button)：点击按钮时执行一个动作。
- [**Tickers**](./elements#ticker)：持续运行动作脚本，以更新布局中的屏幕信息。
- [**Sliders**](./elements#slider)：当滑块值变化时触发动作脚本。
- **Screen Events：** 当屏幕打开或关闭时运行脚本（例如，菜单出现时播放声音）。
- [**Listeners**](./listeners)：当监听器接收到其配置的事件时，它会运行其动作脚本。
- [**Schedulers**](./schedulers)：按时间计划执行动作，即使没有打开任何屏幕。

# 在动作中使用占位符

动作值支持通过 **占位符** 提供动态内容。大多数情况下，这些占位符使用类似 JSON 的语法，并会在动作运行时替换为实时数据。

## 类 JSON 占位符

这些是常规的 [占位符](./placeholders)，可在布局中的许多位置使用。

它们遵循以下语法：

```json
{"placeholder": "placeholder_id", "values": {"key1": "value1", "key2": "value2"}}
```

它们可以获取游戏数据，例如玩家名称、屏幕尺寸，或使用 [**Calculator** 占位符](./placeholders#calculator-calc) 计算出的值。你也可以嵌套占位符以实现更高级的用法。

## `$$` 占位符（变量）

`$$` 值是由运行特定动作脚本的功能提供的只读值。

例如，[Slider](./elements#slider) 会将其当前值作为 `$$value` 提供。

每个 [listener](./listeners) 都会说明它提供了哪些 `$$` 值，例如按下的鼠标按钮或输入的结构。

`$$` 名称区分大小写，并且仅在提供它们的脚本中可用。请参见 [Listeners](./listeners#listener-variables)。

## 动作值分隔符

请使用每个动作中显示的精确分隔符：`:`, `||` 或 `|||`。字段内部没有转义分隔符的语法。

在按分隔符拆分值之前，会先替换占位符。对于 `set_variable`，只有第一个冒号用于分隔名称和值，后续的冒号仍会保留在值中。

## 文本值

[FancyMenu 格式化代码](./text-formatting#minecraft-text-formatting) 在任何接受格式化文本的动作中，都使用 `&` 代替 Minecraft 的 `§` 字符。

- [**Send Chat Message/Command**](#send-chat-messagecommand-sendmessage) 和 [**Paste to Chat**](#paste-to-chat-paste_to_chat) 支持这些格式化代码。
- [**Display In Chat [Client-Side]**](#display-in-chat-client-side-display_in_chat_client_side) 接受纯文本或序列化的 Minecraft 文本组件 JSON。
- [**Open URL in Browser**](#open-url-in-browser-openlink) 在将 URL 传递给操作系统之前，会应用相同的格式化代码转换。

# 如何设置和编辑动作

要编辑元素的动作和语句块，请**右键点击该元素**并选择 **Manage Action Script**。在编辑器中，你可以：

- **添加新的动作或语句：** 插入新的动作条目或控制语句（if、else-if、else、while）来构建脚本。
- **编辑现有动作或语句：** 修改动作值或更改控制逻辑。
- **移除动作或语句：** 从脚本中删除不需要的动作。

通过 [**Customization -> Manage Listeners**](./listeners#using-listeners) 创建和编辑监听器脚本。

# 动作脚本编辑器快捷键

## 快捷键

- `DEL` : 快速删除所选条目
- `ENTER` : 开始对所选条目进行行内编辑（如果所选条目没有行内编辑，则打开编辑界面）
- `Ctrl/Command + C` : 复制所选动作（目前仅对动作有效）
- `Ctrl/Command + V` : 粘贴之前复制的动作
- `Ctrl/Command + Z` : 撤销一步
- `Ctrl/Command + Y` : 重做一步
- `ARROW UP` : 从当前所选条目向上移动一项
- `ARROW DOWN` : 从当前所选条目向下移动一项
- `SHIFT + ARROW UP` : 将所选条目上移一项
- `SHIFT + ARROW DOWN` : 将所选条目下移一项
- `A` : 快速打开 Action Chooser 界面以添加新动作
- `Ctrl/Command + S` : 在编辑器窗口中完成/保存

## 编辑

- 双击动作的值可直接编辑该值，而无需进入完整的值编辑界面。
- IF 语句链（附加 ELSE/ELSE-IF 语句）、WHILE 循环和文件夹都可以折叠（仅视觉效果，不影响脚本逻辑）。
- 编辑器总是在所选条目下方添加新动作（或嵌套到所选链/循环/文件夹中）。
- 右键点击深灰色脚本区域背景会打开上下文菜单，其中包含添加动作、语句以及其他重要内容的选项。

# 动作详解

本节列出 FancyMenu 内置的动作。

## 下一曲目 (`audio_next_track`)

**用途：** 切换到 [Audio element](./elements#audio) 的下一曲目

**值：** 必需 — `audio_element_identifier`（要控制的音频元素 ID）

## 上一曲目 (`audio_previous_track`)

**用途：** 切换到 [Audio element](./elements#audio) 的上一曲目

**值：** 必需 — `audio_element_identifier`（要控制的音频元素 ID）

## 设置曲目音量 (`set_audio_element_volume`)

**用途：** 设置 [Audio element](./elements#audio) 的音量（`0.0` 到 `1.0`）

**值：** 必需 — `element_identifier:volume`

## 切换曲目播放/暂停 (`audio_toggle_play`)

**用途：** 在 [Audio element](./elements#audio) 的当前曲目播放与暂停之间切换

**值：** 必需 — `audio_element_identifier`

## 播放音频 (`play_audio`)

**用途：** 播放一次音频资源。此动作启动的音频之后可通过 [**Stop All Action Audios**](#stop-all-action-audios-stop_all_action_audios) 停止。

**值：** 必需 — 包含 `audioSource`、`soundChannel` 和 `baseVolume` 的 JSON 配置

**示例：** `{"audioSource":"[source:local]/config/fancymenu/assets/example.ogg","soundChannel":"master","baseVolume":1.0}`

**行为：**

- `baseVolume` 会被限制在 `0.0`–`1.0`。
- 未知的音效通道将使用主通道（Master）。
- 该动作不能从异步 [Ticker](./elements#ticker) 中运行；FancyMenu 会改为显示错误。
- FancyMenu 最多等待十秒，直到音频资源准备就绪。
- 成功启动的曲目可通过 [**Stop All Action Audios**](#stop-all-action-audios-stop_all_action_audios) 停止。

## 停止所有动作音频 (`stop_all_action_audios`)

**用途：** 停止所有由 [**Play Audio** 动作](#play-audio-play_audio) 启动的音轨。这不会停止 [Audio elements](./elements#audio)、菜单打开/关闭声音、按钮声音或其他音频系统。

**值：** 不需要

## 设置视频元素音量 (`set_video_element_volume`)

**用途：** 设置 [Video element](./video) 的音量（`0.0` 到 `1.0`）

**值：** 必需 — `video_element_identifier:volume`

## 设置视频元素播放时间 (`set_video_element_play_time`)

**用途：** 将 [Video element](./video) 定位到指定的毫秒时间戳

**值：** 必需 — `video_element_identifier:timestamp_ms`

## 切换视频元素暂停状态 (`toggle_video_element_pause_state`)

**用途：** 切换 [Video element](./video) 的暂停状态

**值：** 必需 — `video_element_identifier`

## 设置视频背景音量 (`set_video_menu_background_volume`)

**用途：** 设置 [Video menu background](./video) 的音量（`0.0` 到 `1.0`）

**值：** 必需 — `background_identifier:volume`

> [!NOTE]
> 要获取背景的标识符，请右键点击编辑器背景，然后点击“Copy Background Identifier”。

## 设置视频背景播放时间 (`set_video_menu_background_play_time`)

**用途：** 将 [Video menu background](./video) 定位到指定的毫秒时间戳

**值：** 必需 — `background_identifier:timestamp_ms`

> [!NOTE]
> 要获取背景的标识符，请右键点击编辑器背景，然后点击“Copy Background Identifier”。

## 切换视频背景暂停状态 (`toggle_video_menu_background_pause_state`)

**用途：** 切换 [Video menu background](./video) 的暂停状态

**值：** 必需 — `background_identifier`

> [!NOTE]
> 要获取背景的标识符，请右键点击编辑器背景，然后点击“Copy Background Identifier”。

## 切换布局 (`toggle_layout`)

**用途：** 通过布局文件名（不含 `.txt`）切换布局的启用/禁用状态

**值：** 必需 — `layout_name`

## 启用布局 (`enable_layout`)

**用途：** 通过布局文件名（不含 `.txt`）启用并保存布局

**值：** 必需 — `layout_name`

## 禁用布局 (`disable_layout`)

**用途：** 通过布局文件名（不含 `.txt`）禁用并保存布局

**值：** 必需 — `layout_name`

这三个布局动作都会将状态保存到布局文件中，并立即更新当前屏幕。请使用区分大小写、且不带 `.txt` 的文件名。

## 打开屏幕或自定义 GUI (`opengui`)

**用途：** 通过其标识符打开一个屏幕（原版、模组或自定义 GUI）

**值：** 必需 — `screen_identifier`

请从 [Screen Identifiers](./screen-identifiers) 调试覆盖层中复制准确的、区分大小写的标识符。

某些模组界面无法直接创建。如果打开失败，请在通常会打开该界面的控件上使用 [**Mimic Vanilla/Mod Button**](#mimic-vanillamod-button-mimicbutton)。

## 关闭屏幕 (`closegui`)

**用途：** 关闭当前活动屏幕

**值：** 不需要

## 更新屏幕 (`update_screen`)

**用途：** 重新初始化当前屏幕

**值：** 不需要

## 返回上一个屏幕 (`back_to_last_screen`)

**用途：** 返回到 [Custom GUI](./custom-guis) 的父级，或返回到最近关闭的屏幕实例

**值：** 不需要

## 加入服务器 (`joinserver`)

**用途：** 让玩家连接到 Minecraft 服务器

**值：** 必需 — `server_ip` 或 `server_ip:port`

当世界或服务器已经加载时，此动作无法运行。若省略端口，则使用 `25565`。如果地址不在 Minecraft 已保存的服务器列表中，FancyMenu 会将其添加并保存。

## 进入世界 (`loadworld`)

**用途：** 进入一个 Minecraft 世界

**值：** 必需 — `world_folder_name`

该值是存档文件夹名称。如果该存档不存在，或已加载了其他世界/服务器，则此动作不会执行任何操作。

## 进入/加入上一个世界/服务器 (`join_last_world`)

**用途：** 进入/加入玩家上次所在的世界或服务器

**值：** 不需要

当已加载其他世界/服务器时，此动作无法运行。若记住的服务器不在 Minecraft 已保存的服务器列表中，会先添加并保存，然后再连接。

## 离开世界或服务器 (`disconnect_server_or_world`)

**用途：** 离开一个世界或服务器，并打开指定屏幕

**值：** 必需 — `screen_identifier`

此动作仅在已加载世界和玩家时运行。目标可以是 [Custom GUI](./custom-guis) 标识符，或 FancyMenu 能够构建的 [screen identifier](./screen-identifiers)。如果目标无法打开，FancyMenu 会返回标题屏幕。

## 退出 Minecraft (`quitgame`)

**用途：** 完全退出 Minecraft

**值：** 不需要

## 发送聊天消息/命令 (`sendmessage`)

**用途：** 发送聊天消息或执行聊天命令。消息文本支持 [FancyMenu 格式化代码](./text-formatting#minecraft-text-formatting)。

**值：** 必需 — `message_text` 或 `/command_text`

## 以集成服务器执行命令 (`execute_command_as_integrated_server`)

**用途：** 在单人游戏中以集成服务器身份强制执行命令，忽略权限和作弊设置。

**值：** 必需 — 命令文本，例如 `/give @p minecraft:diamond 1`

> [!WARNING]
> 此动作仅在单人游戏且世界**未对局域网开放**时有效。当不存在集成服务器，或集成服务器已发布到局域网时，它会刻意不执行任何操作。

## 粘贴到聊天 (`paste_to_chat`)

**用途：** 在玩家/世界已加载时，将格式化文本粘贴到聊天输入框

**值：** 必需 — `true:文本` 或 `false:文本`

当聊天尚未打开时，FancyMenu 会打开聊天并设置输入文本。当聊天已经打开时，`true` 会追加到现有输入中，`false` 会替换它。

## 在聊天中显示 [客户端] (`display_in_chat_client_side`)

**用途：** 在世界或服务器已加载时显示一条客户端聊天消息。它不会向服务器发送任何内容。

**值：** 必需 — `text_or_json`

该值可以是纯文本，也可以是序列化的 Minecraft 文本组件。若未加载世界，此动作不会执行任何操作。

## 向服务器发送 FM 数据 (`send_fm_data_to_server`)

**用途：** 向当前 FancyMenu 服务器发送 [FM Data](./fm-data)。

**值：** 必需 — `data_identifier||data`

## 连接到远程服务器 (`connect_to_remote_server`)

**用途：** 打开或复用一个由客户端发起的 WebSocket 连接，连接到外部远程服务器。

**值：** 必需 — 远程服务器 URL，例如 `wss://example.com/ws`

可接受的 URL 形式请参见 [Remote Server Communication](./remote-server-communication#url-modes)。

## 向远程服务器发送数据 (`send_data_to_remote_server`)

**用途：** 打开或复用远程服务器连接，并向其发送文本数据。

**值：** 必需 — `remote_server_url||data`

## 关闭远程服务器连接 (`close_remote_server_connection`)

**用途：** 通过请求 ID 关闭一个指定的远程服务器连接。

**值：** 必需 — 请求 ID，通常为 [**On Remote Server Connected**](./listeners#on-remote-server-connected-remote_server_connected) 中的 `$$request_id`

## 关闭所有远程服务器连接 (`close_all_remote_server_connections`)

**用途：** 关闭所有由 FancyMenu 打开的活动远程服务器连接。

**值：** 不需要

## 在浏览器中打开 URL (`openlink`)

**用途：** 将 URL 交给操作系统的默认处理程序，不显示 FancyMenu 确认提示

**值：** 必需 — `https://example.com`

请使用受信任的 `https://` 链接。FancyMenu 在将 URL 传递给操作系统之前不会显示确认提示。

## 复制文本到剪贴板 (`copytoclipboard`)

**用途：** 将文本复制到剪贴板

**值：** 必需 — `text_to_copy`

## 输出到游戏日志 (`print_to_log`)

**用途：** 向游戏日志写入一行内容

**值：** 必需 — `text_to_log`

## 设置变量值（FM 变量）(`set_variable`)

**用途：** 将文本内容存储到 [FancyMenu 变量](./variables) 中

**值：** 必需 — `variable_name:variable_value`

第一个冒号用于分隔名称和值。后续的冒号仍会保留在值中。更改会立即保存。

## 清除所有变量（FM 变量）(`clear_variables`)

**用途：** 清除所有已存储的 [FancyMenu 变量](./variables) 值

**值：** 不需要

## 发送 HTTP 请求 (`send_http_request`)

**用途：** 在后台发起 HTTP/HTTPS 请求；可记录和/或将响应存储到变量中

**值：** 必需 — HTTP 请求配置

| 设置 | 行为 |
|---|---|
| URL | HTTP 或 HTTPS 端点 |
| Method | `GET`、`POST`、`PUT`、`DELETE`、`PATCH`、`HEAD` 或 `OPTIONS` |
| Body | 对 `GET` 和 `HEAD` 之外的方法发送 |
| Content type | 请求的 `Content-Type` 值 |
| Timeout | 用于连接和响应读取的秒数 |
| Log response | 读取并将响应写入日志 |
| Response variable | 在请求完成后读取响应并将其存储 |
| Single-line response | 存储前移除响应中的换行 |
| Authentication | None、Basic、Bearer 或 API key |
| Headers | 可选的自定义请求头 |

请求会异步运行，因此下一个动作不会等待。仅当启用日志记录或配置了响应变量时才会读取响应体；非成功响应体会从错误响应中读取。不要在动作配置中存储密码或访问令牌。

## 管理资源包 (`manage_resource_pack`)

**用途：** 启用、禁用或切换资源包，并可选择重新加载

**值：** 必需 — `pack_name_or_id|||MODE|||reload_bool`

显示名称和内部包 ID 会以不区分大小写的方式匹配。标记为必需的资源包不能被禁用。

## 重新加载资源包 (`reload_resource_packs`)

**用途：** 重新加载 Minecraft 的资源包。内置的五秒冷却会忽略这段时间内的重复触发，以防止频繁重载。

**值：** 不需要

## 重新加载 FancyMenu (`reloadmenu`)

**用途：** 重新加载布局、[Custom GUIs](./custom-guis)、[panoramas](./panoramas)、[slideshows](./slideshows)、设置以及 FancyMenu 管理的资源

**值：** 不需要

这不会重新加载 Minecraft 资源包。若要重新加载资源包，请使用 [**Reload Resource Packs**](#reload-resource-packs-reload_resource_packs)。

> [!WARNING]
> 重新加载开销很大。请从有意触发的按钮动作中调用它，而不是通过 [Ticker](./elements#ticker) 或频繁触发的 [listener](./listeners)。

## 切换元素动画器 (`toggle_element_animator`)

**用途：** 切换已保存的播放状态，并重置匹配的活动 Animator 时间线

**值：** 必需 — `animator_identifier`

有关设置和标识符详情，请参见 [Element Animator](./element-animator)。

## 启用元素动画器 (`enable_element_animator`)

**用途：** 启用播放；只有当状态从禁用变为启用时，活动 Animator 时间线才会重置

**值：** 必需 — `animator_identifier`

## 禁用元素动画器 (`disable_element_animator`)

**用途：** 禁用播放并重置匹配的活动 Animator 时间线

**值：** 必需 — `animator_identifier`

## 重置元素动画器 (`reset_element_animator`)

**用途：** 在不改变播放启用状态的情况下，重置匹配的活动 Animator 时间线

**值：** 必需 — `animator_identifier`

## 模拟原版/模组按钮 (`mimicbutton`)

**用途：** 模拟原版或模组按钮的点击动作

**值：** 必需 — 完整的 [widget locator](./widget-locators)，例如 `example.menu.identifier:505280`

## 模拟按键绑定 (`mimic_keybind`)

**用途：** 执行 Minecraft 键盘或鼠标按键绑定，可选择是否持续按住

**值：** 必需 — `keybind_id|||keep_pressed_bool|||duration_ms`

| 字段 | 含义 |
|---|---|
| `keybind_id` | Minecraft 按键绑定标识符，例如 `key.jump` |
| `keep_pressed_bool` | `true` 表示按住该键；`false` 表示普通按下 |
| `duration_ms` | 当 `keep_pressed_bool` 为 `true` 时的按住时长；默认 `1000` |

## 设置文本输入框值 (`set_text_input_field_value`)

**用途：** 通过元素标识符设置自定义或原版 [Text Input Field](./elements#text-input-field) 的值。

**值：** 必需 — `element_identifier|||new_value|||force_set_when_inactive`

这三个字段必须使用三竖线分隔符 `|||` 分隔。将 `force_set_when_inactive` 设为 `true` 可在输入框禁用时也进行更新；当它为 `false` 时，非活动输入框保持不变。

## 在游戏目录中创建文件 (`create_file_in_game_dir`)

**用途：** 在当前游戏目录下创建一个空文件。支持 `.minecraft/` 前缀以指向常规 Minecraft 目录（该目录可能与当前实例不同）。

**值：** 必需 — `file_path`

示例：`config/some_mod_folder/new_file.txt`。缺失的父目录会被创建；已存在的文件保持不变。

## 删除游戏目录中的文件/文件夹 (`delete_file_in_game_dir`)

**用途：** 删除当前游戏目录下的文件，或递归删除文件夹。支持使用 `.minecraft/` 指向常规 Minecraft 目录。给路径附加 `*` 可删除文件夹内**所有直接包含的文件**（忽略子目录并保留文件夹）。

**值：** 必需 — `target_path`

例如，`config/downloads/*` 会删除 `config/downloads/` 中直接包含的文件，但不会遍历或删除其子目录。

## 复制游戏目录中的文件/文件夹 (`copy_file_in_game_dir`)

**用途：** 在当前游戏目录内复制；`.minecraft/` 指向常规 Minecraft 目录。命名目录会递归复制。给**源**路径附加 `*` 可仅复制所有直接子文件；目标必须是目录，且不能使用 `*`。

**值：** 必需 — `source||destination`

例如，`config/source/*||config/destination/` 只会复制 `config/source/` 中直接包含的文件。对于带通配符的源路径，FancyMenu 会在需要时创建目标目录，但不会复制任何源子目录。复制时会拒绝任何已存在的目标/冲突文件，而不是覆盖它。

## 移动游戏目录中的文件/文件夹 (`move_file_in_game_dir`)

**用途：** 在当前游戏目录内移动；`.minecraft/` 指向常规 Minecraft 目录。给**源**路径附加 `*` 可仅移动所有直接子文件；目标必须是目录，且不能使用 `*`。

**值：** 必需 — `source||destination`

例如，`config/source/*||config/destination/` 只会移动 `config/source/` 中直接包含的文件。对于带通配符的源路径，FancyMenu 会在需要时创建目标目录，但会保留源子目录。移动时会拒绝已存在的目标/冲突文件，而不是覆盖它。

## 重命名游戏目录中的文件/文件夹 (`rename_file_in_game_dir`)

**用途：** 在当前父目录内重命名文件或文件夹；`.minecraft/` 指向常规 Minecraft 目录。保留内容不变，并拒绝已存在的目标名称。

**值：** 必需 — `path||new_name`

## 下载文件到游戏目录 (`download_file_to_game_dir`)

**用途：** 在后台将文件下载到当前游戏目录下的某个目录；`.minecraft/` 指向常规 Minecraft 目录。

**值：** 必需 — `url||target_folder`

第二个字段是**目标目录**，不是完整的目标文件路径。FancyMenu 会在需要时创建该目录，并从响应的 `Content-Disposition` 标头中确定文件名，然后回退到 URL 路径。解析出的名称在使用前会经过 URL 解码和清理；如果两者都没有提供可用名称，FancyMenu 会生成一个名称。同名现有文件会被覆盖。

[**On File Downloaded via Action** 监听器](./listeners#on-file-downloaded-via-action-file_downloaded_via_action) 会在成功和失败的下载尝试后触发，并提供 URL、解析后的目标路径以及成功状态。

成功时，`$$target_file_path` 是已保存文件的路径。失败时，它可能只包含目标目录，因为未能解析出最终文件名。

## 在游戏目录中解压 ZIP 文件 (`extract_zip_file_in_game_dir`)

**用途：** 将 ZIP 解压到当前游戏目录或常规 `.minecraft` 目录内的目标文件夹。完成时触发 [**On ZIP Extracted via Action**](./listeners#on-zip-extracted-via-action-zip_extracted_via_action)。

**值：** 必需 — `source_zip_path||target_folder_path`

同名的现有文件会被替换。仅解压可信的 ZIP 文件。

## 在游戏目录中打开文件/文件夹 (`open_file_folder_in_game_dir`)

**用途：** 使用操作系统的默认应用打开文件或文件夹。出于安全原因，目标必须位于游戏目录或默认的 `.minecraft` 目录内。

**值：** 必需 — `target_path`

## 在游戏目录中写入文件 (`write_file_in_game_dir`)

**用途：** 相对于当前游戏目录写入或追加文本；`.minecraft/` 指向常规 Minecraft 目录。若文件或父目录缺失则会创建它们。`\n` 可插入换行；`append_bool=false` 会替换现有文件。

**值：** 必需 — `path|||content|||append_bool`

## 从系统中选择文件 (`select_file_to_game_dir`)

**用途：** 打开原生文件选择器，并将所选文件复制到当前游戏目录内，或者在带有前缀时复制到常规 `.minecraft/`。支持扩展名筛选、自定义筛选标签，以及覆盖开关。

**值：** 必需 — `target_path|||filter_description|||extensions|||overwrite_bool`

`target_path` 是完整的目标文件路径。多个扩展名请用 `;` 或 `,` 分隔，例如 `png;jpg`；空扩展名列表表示允许所有文件。如果 `overwrite_bool` 为 `false`，当目标文件已存在时，动作会失败而不是替换它。

[**On File Selected** 监听器](./listeners#on-file-selected-file_selected_via_action) 会在文件被复制、选择器被取消或选择失败时触发。它会提供所选路径、解析后的目标路径、成功/取消状态以及失败原因。

## 显示 Toast (`show_toast`)

**用途：** 显示一个可配置的 toast 通知

**值：** 必需 — JSON toast 配置

编辑器会将此动作以 JSON 形式保存。请优先使用其配置窗口，而不是手动编辑值。

| 字段 | 含义 |
|---|---|
| `width` | 限制在 `120`–`320` 像素 |
| `durationMs` | 限制在 `1000`–`600000` 毫秒 |
| `title` | 纯文本、序列化的 Minecraft 文本组件，或为空 |
| `message` | 纯文本、序列化的文本组件，或为空 |
| `iconSource` | 可选的 [图像源](./resources) |
| `backgroundSource` | 可选的 [图像源](./resources) |

## 启动调度器 (`start_scheduler`)

**用途：** 通过调度器 ID 启动一个调度器。

**值：** 必需 — `scheduler_id`

有关创建和管理调度器 ID，请参见 [Schedulers](./schedulers)。

## 停止调度器 (`stop_scheduler`)

**用途：** 通过调度器 ID 停止一个调度器。

**值：** 必需 — `scheduler_id`

## 设置 Minecraft 选项 (`edit_minecraft_option`)

**用途：** 编辑一个 Minecraft 配置选项

**值：** 必需 — `option_name:set_to_value`
