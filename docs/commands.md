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

> FancyMenu needs to be on the **SERVER** (and client) to use commands in Multiplayer!
{.is-warning}

## Target Players and Permissions

The target-player argument of `/openguiscreen`, `/closeguiscreen`, and `/fmlayout` is optional. When a player omits it, the command affects that player. When a target is provided, normal player names and selectors such as `@a` can be used.

- Supplying the target argument to `/openguiscreen` or `/closeguiscreen` requires **permission level 2** (Game Master / OP level 2), even if it names the command source.
- Supplying the target argument to `/fmlayout` requires **permission level 3** (Admin / OP level 3), even if it names the command source.
- Every `/fmdata` sub-command requires **permission level 2** (Game Master / OP level 2).

For the three commands with optional targets, omitting the target only works when the command source is a player. The server console must supply a target and meet the target argument's permission requirement.

## /openguiscreen

The `/openguiscreen` command lets you open a GUI (Vanilla/mod and custom GUIs).
It can even remotely open GUIs for other players when FancyMenu is installed on both server and clients.

For a more in-detail description of this command, take a look at the [Open GUIs by Command](/opengui-command) page.

This command will not work for every screen, especially mod screens. If the command fails to open a screen, it will show an error. There is not much you can do in that case, because then it's probably a screen that is too complex to get opened automatically by FancyMenu.

I will also not manually add compatibility for mod screens anymore, because adding compatibility for all the mods out there would take me ages, sorry.

**Usage:** `/openguiscreen <screen_identifier> [<target_players>]`

## /closeguiscreen

The `/closeguiscreen` command lets you close the current GUI.

Huh? This is totally useless you say?
Well yes, but actually no.

This command is useful for when using mods that trigger commands on specific actions.
So yes, this command is absolutely useless when using it without other mods, but can be really helpful if you have the right mods installed!

**Usage:** `/closeguiscreen [<target_players>]`

## /fmlayout

The `/fmlayout` command sets whether a layout is enabled on one or more clients. Use the layout's name exactly as it appears in FancyMenu, and put names containing spaces in quotes.

**Usage:** `/fmlayout <layout_name> <true|false> [<target_players>]`

Examples:

- `/fmlayout quest_complete true` enables `quest_complete` for the player running the command.
- `/fmlayout quest_complete false @a` disables it for every online player. Supplying the target argument requires permission level 3.

## /fmvariable

The `/fmvariable` command allows you to set and get FancyMenu variables.

To execute this command as another player on servers, you can use the `/execute as` Vanilla command.
So lets say you want to execute the `/fmvariable` command as the player `ExamplePlayer`. In that case you would type:
`/execute as ExamplePlayer run fmvariable...`.

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
