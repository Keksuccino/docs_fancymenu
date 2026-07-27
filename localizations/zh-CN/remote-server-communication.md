---
title: 远程服务器通信
description: 在 FancyMenu 客户端与外部服务器之间发送和接收自定义文本数据。
---

# 远程服务器通信

“远程服务器通信”系统允许 FancyMenu 客户端通过 WebSocket 连接与外部服务器通信。

所有数据都基于文本：

- 支持纯文本
- 支持 JSON（作为普通文本）

每个服务器 URL 在运行期间都会获得一个缓存的 **请求 ID**。
FancyMenu 使用此 ID 跟踪连接，并在监听器变量中暴露它。

# 快速开始

1. 在连接应尽早建立时添加 [**连接到远程服务器**](#connect-to-remote-server)。
2. 使用相同的 URL 添加 [**向远程服务器发送数据**](#send-data-to-remote-server)。
3. 添加 [**远程服务器数据接收时**](#on-remote-server-data-received) 来响应回复。
4. 使用 [**远程服务器连接时**](#on-remote-server-connected) 和 [**远程服务器连接关闭时**](#on-remote-server-connection-closed) 处理连接状态逻辑。
5. 使用 [**关闭远程服务器连接**](#close-remote-server-connection) 或 [**关闭所有远程服务器连接**](#close-all-remote-server-connections) 关闭连接。

# 动作

## 连接到远程服务器

打开或复用远程服务器连接，但不发送负载数据。

输入：

- 远程服务器 URL

## 向远程服务器发送数据

连接（或复用现有连接）并发送文本数据。

输入：

1. 远程服务器 URL
2. 数据

## 关闭远程服务器连接

通过请求 ID 关闭一个连接。

输入：

- 连接请求 ID

## 关闭所有远程服务器连接

关闭当前所有活动的远程服务器连接。

# 监听器

## 远程服务器连接时

当远程服务器连接成功打开后触发。

变量：

- `$$request_id`
- `$$remote_server_url`

## 远程服务器数据接收时

当从已连接的远程服务器接收到数据时触发。

变量：

- `$$request_id`
- `$$remote_server_url`
- `$$data`

## 远程服务器连接关闭时

当远程服务器连接关闭时触发。

变量：

- `$$request_id`
- `$$remote_server_url`
- `$$intentionally_closed`
- `$$crashed`
- `$$unknown_close_reason`

# 连接行为

- 连接是**由客户端发起**的
- FancyMenu 会在后台保持连接活动
- 如果连接崩溃或超时，FancyMenu 会每 10 秒重试一次
- 当崩溃的连接恢复后，FancyMenu 会记录一条恢复消息
- 未发送的外发消息会进入队列，**最大保留时间为 30 秒**
- 队列中超过 30 秒的消息会被丢弃

# URL 模式

- `wss://` 会按原样使用，且推荐使用。
- `ws://` 会按原样使用，且不加密。
- `https://` 会转换为 `wss://`。
- `http://` 会转换为 `ws://`。
- 纯主机名会自动加上 `wss://` 前缀。
- 其他显式 URL 协议都会被拒绝。

建议优先使用显式的 `wss://` URL。局域网示例：

- `ws://127.0.0.1:8765`

每个服务请使用一个稳定的 URL，处理已关闭/已崩溃的监听器状态，并在不再需要连接时关闭连接。
