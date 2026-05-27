---
title: Widget Locators
description: What are widgets locators and how to find them.
---
# Widget Locators

Widget locators are used for pointing at a specific Vanilla widget (button, slider, text input field) in a menu, which is needed for some of FancyMenu's features that need to interact with a widget in some way.

# Getting The Locator of a Widget

There are two ways to get the locator of a Vanilla widget.

The first one is activating the **debug overlay** in the menu that contains the widget, by pressing **CTRL + ALT + D**, and then **right-clicking the widget**, which will open a context menu with an option to copy the locator to the clipboard.

The second one is opening the **layout editor** for the menu that contains the widget, and then **right-clicking the widget element**, which will also open a context menu with an option to copy the locator to the clipboard.

>[!WARNING]
>If you **can't right-click** the widget via the debug overlay, or it **does not appear** in the layout editor, it is probably not visible for FancyMenu, which means that it does not have a locator in that case. This mostly happens for mod buttons that are added to menus in weird ways.
