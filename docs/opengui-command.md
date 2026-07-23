---
title: Open GUIs by Command
description: How to open Vanilla and Custom GUIs via command.
published: true
date: 2025-06-26T20:50:52.238Z
tags: 
editor: markdown
dateCreated: 2025-04-14T20:15:25.104Z
---

# Opening GUIs by Command

The `/openguiscreen` command opens Vanilla, mod, and [Custom GUIs](./custom-guis). It can target other players when FancyMenu is installed on the server and their clients.

To open a GUI, use `/openguiscreen <screen_identifier> [<target_players>]`.

Replace `<screen_identifier>` with the exact, case-sensitive identifier of the Custom GUI or Vanilla/mod screen.

To find an identifier, open the target screen and enable the debug overlay with **CTRL + ALT + D**. Select the identifier on its first line to copy it. See [Screen Identifiers](./screen-identifiers).

![copy_identifier](https://github.com/Keksuccino/FancyMenu/assets/35544624/dd6c53d9-d2bd-4810-be03-3741e326bd5a)

Omit `[<target_players>]` to open the GUI for yourself, or use a player name or selector such as `@a` to open it for one or more players. Supplying the target argument requires permission level 2 (Game Master / OP level 2), even if it names yourself, and every target player needs FancyMenu installed on their client.

Not every mod screen can be created directly. FancyMenu shows an error when a target screen is unsupported. In a local layout, use [**Mimic Vanilla/Mod Button**](./action-scripts#mimic-vanillamod-button-mimicbutton) on the widget that normally opens it.

# Closing GUIs by Command

In the rare case you need it, `/closeguiscreen [<target_players>]` closes the current screen. It affects you when the target is omitted; supplying the target argument requires permission level 2.
