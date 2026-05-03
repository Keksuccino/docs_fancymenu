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

FancyMenu comes with a command that lets you open Vanilla and Custom GUIs via command.
You can even remotely open GUIs for **other players** when installing FancyMenu on both **server and clients**.

To open a GUI, just use the command `/openguiscreen <screen_identifier> <target_player>`.

Replace `<screen_identifier>` with the actual menu identifier of the GUI you want to open.
This can be the identifier of your Custom GUI (made with FancyMenu) or the normal menu identifier of a Vanilla/mod GUI.

To get the **menu identifier of Vanilla/mod GUIs**, open the menu you want to know the identifier of and enable FancyMenu's **debug overlay** via **Customization -> Debug Overlay**, then you can click on the identifier shown as first line to copy it to your clipboard.

![copy_identifier](https://github.com/Keksuccino/FancyMenu/assets/35544624/dd6c53d9-d2bd-4810-be03-3741e326bd5a)

Leave the `<target_player>` argument empty to open the GUI for your client or choose a player (or multiple players) to open the GUI for.
Keep in mind that the other player needs to have FancyMenu installed on their client.

This command will not work for every screen, especially mod screens. If the command fails to open a screen, it will show an error. There is not much you can do in that case, because then it's probably a screen that is too complex to get opened automatically by FancyMenu.

I will also not manually add compatibility for mod screens anymore, because adding compatibility for all the mods out there would take me ages, sorry.

# Closing GUIs by Command

In the rare case you need it, there's also a `/closeguiscreen <target_player>` command that closes the current screen.
