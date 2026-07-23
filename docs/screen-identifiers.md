---
title: Screen Identifiers
description: About screen identifiers and how to find the identifier of a screen.
---
# Screen Identifiers

FancyMenu uses screen identifiers for layouts, Vanilla widgets, [screen actions](./action-scripts#open-screen-or-custom-gui-opengui), and [Custom GUI overrides](./custom-guis#overriding-an-existing-screen). Identifiers are case-sensitive, so copy them exactly from the debug overlay.

Built-in screens normally use a short universal identifier such as `title_screen`. Other mod screens may use their Java class name. Custom GUIs use the identifier entered in their manager. These are FancyMenu screen identifiers, not Minecraft resource locations.

# Finding the Identifier of a Screen

You can see the identifier of the currently active menu by using the **debug overlay**.
It contains the current screen's identifier and allows you to copy it to the clipboard by left-clicking it.

>[!TIP]
>You can enable the **debug overlay** by pressing **CTRL + ALT + D** while you are **not** in the layout editor.

<br>

<img width="553" alt="Screenshot_3" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/1800351e-f042-4826-8eed-7725b78bc84d">

<br>

<img width="579" alt="Screenshot_4" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/9e0d1e61-7f2d-4817-9be1-b63ee61978dd">

# Opening Screens

The [**Open Screen or Custom GUI** action](./action-scripts#open-screen-or-custom-gui-opengui) can open only screens FancyMenu can construct in the current game state. Some screens require a loaded world, connection, player, or original parent screen.

If FancyMenu cannot construct the identifier, it shows an error. Use [**Mimic Vanilla/Mod Button**](./action-scripts#mimic-vanillamod-button-mimicbutton) on the widget that normally opens the screen.
