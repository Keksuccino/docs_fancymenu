---
title: 客户端 < - > 服务器数据共享
description: 使用 FancyMenu 在服务器和客户端之间发送和接收自定义数据。
sourceBlobSha: 35ae4605e43ac917f11c24e5d97a5c311c9aa01a
---

# FM 数据

“FM Data”系统可让你在服务器和客户端之间发送自定义文本数据。

每个 `/fmdata` 子命令都需要**权限等级 2**（游戏管理员 / OP 等级 2）。

每条 FM Data 消息都包含：

1. **数据标识符**（消息的类型）
2. **数据值**（实际内容）

示例：

- 标识符：`hud.food`
- 数据：`18/20`

# 快速开始

1. 服务器使用 `/fmdata send ...` 发送数据
2. 客户端通过 FancyMenu 监听器 **On FM Data Received** 接收数据
3. 客户端也可以通过 **Send FM Data To Server** 操作发送数据回服务器
4. 服务器可以通过 `/fmdata listener ...` 自动响应
5. 服务器可以通过 `/fmdata welcome_data ...` 在玩家加入时自动发送数据

# 服务器 -> 客户端

使用：

```mcfunction
/fmdata send <target_players> <data_identifier> <string_data>
```

示例：

```mcfunction
/fmdata send Player761 hud.food 18/20
/fmdata send @a "food value update" "18 of 20"
```

注意：

- `<target_players>` 支持玩家名称和选择器，例如 `@a`、`@p` 和 `@s`
- 值中包含空格时请使用引号

# 客户端：接收数据

使用 FancyMenu 监听器：

- **On FM Data Received**

可用变量：

- `$$data_identifier`
- `$$data`
- `$$sent_by`

`$$sent_by` 的值为：

- 多人游戏中的服务器 IP
- 单人游戏中的 `integrated_server`

常见用途：

- 更新文本元素
- 触发菜单操作
- 根据收到的标识符和数据运行逻辑

# 客户端 -> 服务器

使用 FancyMenu 操作：

- **Send FM Data To Server**

此操作包含 2 个输入项：

1. 数据标识符
2. 数据

随后，服务器可以使用 `/fmdata listener ...` 处理收到的数据。

# 服务器监听器

服务器监听器用于监听客户端发来的数据，并在触发时运行一个或多个命令。

服务器监听器会保存下来，并在重启后继续生效。

使用以下命令管理：

- `/fmdata listener list`
- `/fmdata listener add ...`
- `/fmdata listener edit ...`
- `/fmdata listener remove ...`

## 添加 / 编辑语法

```mcfunction
/fmdata listener add <unique_listener_name> <matching_type_identifier> <matching_type_data> <ignore_case_identifier> <ignore_case_data> <fire_for_player> <listen_for_identifier> <listen_for_data> <commands_to_execute_on_fire>
```

```mcfunction
/fmdata listener edit <listener_name> <matching_type_identifier> <matching_type_data> <ignore_case_identifier> <ignore_case_data> <fire_for_player> <listen_for_identifier> <listen_for_data> <commands_to_execute_on_fire>
```

## 移除语法

```mcfunction
/fmdata listener remove <listener_name>
```

## 匹配类型

`matching_type_identifier` 和 `matching_type_data` 可以是：

- `equals`
- `contains`
- `starts_with`
- `ends_with`

## 匹配规则

- `ignore_case_identifier` 和 `ignore_case_data` 是 true/false 开关
- `listen_for_identifier` 支持通配符 `*`（始终匹配）
- `listen_for_data` 支持通配符 `*`（始终匹配）
- `fire_for_player` 使用常规玩家选择器（例如 `@a`、`@p`、`Player761`）

## 触发时执行的命令

`commands_to_execute_on_fire` 是一个文本输入项。

- 使用 `|||` 分隔多个命令
- 使用 `\|\|\|` 转义字面量分隔符

你可以在此使用两个特殊占位符，它们会在命令执行前被替换：

- `%fm_sender%` -> 发送 FM Data 的玩家
- `%fm_data%` -> 从客户端收到的数据值

命令将以服务器命令的形式运行。

## 命令示例

响应任意玩家的按钮点击：

```mcfunction
/fmdata listener add button_ping equals equals false false @a ui.button pressed "tellraw @a {\"text\":\"%fm_sender% pressed the button\"}"
```

当数据包含 `gold` 时运行多个命令：

```mcfunction
/fmdata listener add reward equals contains false true @a reward "gold" "say Reward from %fm_sender%: %fm_data%|||effect give %fm_sender% minecraft:speed 3 1 true"
```

# 欢迎数据

玩家加入时，欢迎数据会向匹配的玩家发送 FM Data。

使用以下命令管理条目：

- `/fmdata welcome_data list`
- `/fmdata welcome_data add ...`
- `/fmdata welcome_data edit ...`
- `/fmdata welcome_data remove ...`

## 添加 / 编辑语法

```mcfunction
/fmdata welcome_data add <unique_welcome_data_name> <target_player> <data_identifier> <string_data>
```

```mcfunction
/fmdata welcome_data edit <welcome_data_name> <target_player> <data_identifier> <string_data>
```

## 移除语法

```mcfunction
/fmdata welcome_data remove <welcome_data_name>
```

注意：

- `<target_player>` 支持常规选择器，例如 `@a`、`@p`、`@s`
- 玩家加入时，数据会发送给匹配的玩家
- 条目会自动保存和加载

## 命令示例

向所有加入的玩家发送欢迎数据：

```mcfunction
/fmdata welcome_data add welcome_all @a hud.welcome "Welcome!"
```

仅向一名玩家发送欢迎数据：

```mcfunction
/fmdata welcome_data add welcome_vip Player761 hud.vip "VIP perks enabled"
```

# 导出供 AI 使用

如需向 Alice 或其他 AI 寻求帮助，可使用 [Export for AI](/export-for-ai#servers) 导出服务器的监听器和欢迎数据：

```mcfunction
/fmdata export_for_ai copy
/fmdata export_for_ai file
```

`copy` 会发送一条聊天消息，点击后即可复制导出内容。`file` 会将内容保存到服务器的 `fancymenu_data/ai_exports/` 目录中。

# 最佳实践

1. 使用清晰的标识符，例如 `hud.food`、`menu.shop.open`、`quest.progress`。
2. 为每个标识符保持一致的数据格式。
3. 从简单的用法开始：先使用 `/fmdata send` 测试，再构建复杂的监听器。
4. 只有确实需要全局行为时才使用 `@a`。
5. 使用 `/fmdata listener list` 和 `/fmdata welcome_data list` 保持配置整洁。
