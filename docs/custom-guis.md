---
title: Custom GUIs
description: Create and configure new GUI screens.
published: true
date: 2026-05-03T11:01:52.000Z
tags:
editor: markdown
dateCreated: 2025-04-14T20:14:26.193Z
---

# Custom GUIs

Custom GUIs are new screens that you can fill with FancyMenu [elements](./elements).

> [!CAUTION]
> Custom GUIs can run actions. Import them only from sources you trust.

# Creating a Custom GUI

1. Open **Customization -> Custom GUIs -> Manage Custom GUIs**.
2. Select **New GUI**.
3. Enter an identifier and configure the screen settings.
4. Select **Done**, then open the new GUI from the manager.
5. Create and edit its layout like any other screen.

Identifiers must be unique and use the lowercase filename-safe characters accepted by the editor. Empty, invalid, or duplicate identifiers cannot be saved.

Custom GUIs always have screen customization enabled; their customization toggle cannot be disabled.

# Screen Settings

| Setting | Behavior |
|---|---|
| Allow ESC | Lets Escape close the GUI and return to its parent screen |
| Pause Game/World | Pauses singleplayer while the GUI is open |
| Render World Background | Shows the loaded world behind the GUI |
| World Background Overlay | Adds the standard blur/dark overlay over the world |
| Popup Mode | Keeps the parent screen visible behind the Custom GUI |
| Popup Background Overlay | Adds blur/tint over the parent screen in Popup Mode |

Closing a Custom GUI returns to its parent screen when one exists.

# Opening a Custom GUI

Use the exact Custom GUI identifier with either:

- The [**Open Screen or Custom GUI** action](./action-scripts#open-screen-or-custom-gui-opengui).
- The [`/openguiscreen` command](./commands#openguiscreen).

# Overriding an Existing Screen

A Custom GUI can replace a Vanilla or mod screen whenever that screen opens.

1. Create the replacement Custom GUI.
2. Open the screen you want to replace.
3. Enable **Customization -> Settings -> Advanced Customization Mode**.
4. Select **Customization -> Custom GUIs -> Override Current with Custom GUI**.
5. Choose the replacement Custom GUI.

Manage saved overrides through **Customization -> Custom GUIs -> Manage Overridden Screens**.

An override skips the original screen, so test its navigation and any features that depend on the original screen's behavior.
