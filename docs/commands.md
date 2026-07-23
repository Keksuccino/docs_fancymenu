---
title: Commands
description: FancyMenu's commands and how to use them.
published: true
date: 2025-06-26T20:50:09.935Z
tags: 
editor: markdown
dateCreated: 2025-04-14T20:14:18.072Z
---

# Commands

FancyMenu adds some commands to the game that can be very useful when combining them with other mods like FTB Quests.

> [!WARNING]
> FancyMenu needs to be on the **SERVER** (and client) to use commands in Multiplayer!

## Target Players and Permissions

The target-player argument of `/openguiscreen`, `/closeguiscreen`, and `/fmlayout` is optional. When a player omits it, the command affects that player. When a target is provided, normal player names and selectors such as `@a` can be used.

- Supplying the target argument to `/openguiscreen` or `/closeguiscreen` requires **permission level 2** (Game Master / OP level 2), even if it names the command source.
- Supplying the target argument to `/fmlayout` requires **permission level 3** (Admin / OP level 3), even if it names the command source.
- Every `/fmdata` sub-command requires **permission level 2** (Game Master / OP level 2).

For the three commands with optional targets, omitting the target only works when the command source is a player. The server console must supply a target and meet the target argument's permission requirement.

## /openguiscreen

The `/openguiscreen` command opens a Vanilla, mod, or [Custom GUI](./custom-guis). It can target other players when FancyMenu is installed on the server and their clients.

See [Opening GUIs by Command](./opengui-command) and [Screen Identifiers](./screen-identifiers).

Not every mod screen can be created directly. FancyMenu shows an error when a target screen is unsupported. In a local layout, use [**Mimic Vanilla/Mod Button**](./action-scripts#mimic-vanillamod-button-mimicbutton) on the widget that normally opens it.

**Usage:** `/openguiscreen <screen_identifier> [<target_players>]`

## /closeguiscreen

The `/closeguiscreen` command closes the current screen for the command source or selected players. It is useful with quest, event, or automation mods that can run commands.

**Usage:** `/closeguiscreen [<target_players>]`

## /fmlayout

The `/fmlayout` command sets whether a layout is enabled on one or more clients. Use the layout's name exactly as it appears in FancyMenu, and put names containing spaces in quotes.

**Usage:** `/fmlayout <layout_name> <true|false> [<target_players>]`

Examples:

- `/fmlayout quest_complete true` enables `quest_complete` for the player running the command.
- `/fmlayout quest_complete false @a` disables it for every online player. Supplying the target argument requires permission level 3.

## /fmvariable

The `/fmvariable` command sets and reads [FancyMenu variables](./variables).

To execute this command as another player, use Vanilla's `/execute as` command:
`/execute as ExamplePlayer run fmvariable ...`

**Usage:**

- `/fmvariable get <variable_name>`
- `/fmvariable set <variable_name> <send_chat_feedback> <set_to_value>`

### Get

To **get a variable value**, use the `get` sub-command like this:
`/fmvariable get some_variable`

Then the value of this variable will be printed to your chat.

### Set

To **set a variable**, put the chat-feedback boolean before the new value:
`/fmvariable set some_variable true new_value`

The `send_chat_feedback` argument controls whether FancyMenu confirms the change in chat. The `set_to_value` argument consumes the rest of the command, so the value can contain spaces. For example, `/fmvariable set greeting false Hello from FancyMenu` stores `Hello from FancyMenu` without sending success feedback.

## /fmdata

The `/fmdata` command sends custom data between the server and FancyMenu clients, manages server-side listeners, and configures data that is sent when players join. Every `/fmdata` sub-command requires permission level 2.

See [FM Data](./fm-data) for all sub-commands, syntax, and examples.
