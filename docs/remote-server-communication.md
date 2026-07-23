---
title: Remote Server Communication
description: Send and receive custom text data between FancyMenu clients and external servers.
published: true
date: 2026-05-03T11:01:52.000Z
tags:
editor: markdown
dateCreated: 2026-05-03T11:01:52.000Z
---

# Remote Server Communication

The "Remote Server Communication" system lets FancyMenu clients communicate with external servers using WebSocket connections.

All data is text-based:

- Plain text is supported
- JSON is supported (as normal text)

Each server URL gets one cached **request ID** during runtime.
FancyMenu uses this ID to track the connection and expose it in listener variables.

# Quick Start

1. Add [**Connect To Remote Server**](#connect-to-remote-server) when the connection should open early.
2. Add [**Send Data To Remote Server**](#send-data-to-remote-server) with the same URL.
3. Add [**On Remote Server Data Received**](#on-remote-server-data-received) to react to replies.
4. Use [**On Remote Server Connected**](#on-remote-server-connected) and [**On Remote Server Connection Closed**](#on-remote-server-connection-closed) for connection-state logic.
5. Close connections with [**Close Remote Server Connection**](#close-remote-server-connection) or [**Close All Remote Server Connections**](#close-all-remote-server-connections).

# Actions

## Connect To Remote Server

Opens or reuses a remote server connection without sending payload data.

Input:

- Remote Server URL

## Send Data To Remote Server

Connects (or reuses an existing connection) and sends text data.

Inputs:

1. Remote Server URL
2. Data

## Close Remote Server Connection

Closes one connection by request ID.

Input:

- Connection Request ID

## Close All Remote Server Connections

Closes all currently active remote server connections.

# Listeners

## On Remote Server Connected

Triggers after a remote server connection successfully opens.

Variables:

- `$$request_id`
- `$$remote_server_url`

## On Remote Server Data Received

Triggers when data is received from a connected remote server.

Variables:

- `$$request_id`
- `$$remote_server_url`
- `$$data`

## On Remote Server Connection Closed

Triggers when a remote server connection closes.

Variables:

- `$$request_id`
- `$$remote_server_url`
- `$$intentionally_closed`
- `$$crashed`
- `$$unknown_close_reason`

# Connection Behavior

- Connections are **client-initiated**
- FancyMenu keeps connections active in the background
- If a connection crashes or times out, FancyMenu retries every 10 seconds
- When a crashed connection is restored, FancyMenu logs a restore message
- Outgoing unsent messages are queued with a **max age of 30 seconds**
- Queued messages older than 30 seconds are dropped

# URL Modes

- `wss://` is used as written and is recommended.
- `ws://` is used as written and is unencrypted.
- `https://` is converted to `wss://`.
- `http://` is converted to `ws://`.
- A bare host is prefixed with `wss://`.
- Other explicit URL schemes are rejected.

Prefer explicit `wss://` URLs. Example local URL:

- `ws://127.0.0.1:8765`

Use one stable URL per service, handle the closed/crashed listener states, and close connections when they are no longer needed.
