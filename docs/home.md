---
title: Getting Started
description: >-
  The world of FancyMenu awaits you! This is the beginning of something
  beautiful!
---

# For Developers

If your are a developer and want to make an addon for FancyMenu or integrate FancyMenu in your mod, you should take a look at the [developer documentation](https://github.com/Keksuccino/FancyMenu-Dev-Docs/wiki).

# Getting Started

The first time using FancyMenu can be a bit overwhelming, but don't worry, most of it is actually pretty self-explanitory once you start working with it!

> Please **keep in mind** that this page is just to get into FancyMenu and help you with your **very first steps**.
Make sure to also check out the rest of the documentation for more in-detail information about FancyMenu's features!
{.is-info}

# The Menu Bar

One of the first things you will notice when starting the game is the **menu bar** at the top of every menu.

The **menu bar** is your entry point to basically all of FancyMenu's features like **creating layouts** to **customize menus**, changing the **window title and icon** and much more.

> If you acidentally pressed some keys and the **menu bar disappeared**, you can bring it back by pressing **CTRL + ALT + C**.
{.is-warning}

<img width="650" alt="menu_bar" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/menu_bar.png?raw=true">

# Your First Layout

Since you probably want to customize Minecraft's menus, let me tell you something about **layouts**!

Layouts are like customization layers for menus and they allow you to add new elements and customize existing ones.

To make a new layout for a **specific menu**:
1. Open the menu you want to create a layout for (the Title Screen for example)
2. Open the **Customization** tab of the **menu bar**

Customizations are disabled for all menus by default and you need to activate them for every menu you want to customize, so let's click on the **"Current Screen Customization: Disabled"** entry first, which will switch the toggle to **Enabled**.

<img width="475" alt="toggle_customizations" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/toggle_customizations.png?raw=true">

After doing that, click on **Layouts -> New -> For Current Screen**.

This will open the **layout editor** where you can add elements to the layout and customize Vanilla and mod elements (like buttons).

<img width="550" alt="new_layout_current" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/new_layout_current.png?raw=true">

## Editing the Layout

Most customization options can be accessed by **right-clicking the editor background**.
Doing that will open a context menu with lots of options, like customizing the **menu backround** or **adding elements** to the layout.

<br>
<img width="350" alt="context_menu" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/context_menu.png?raw=true">

## Adding Elements to Layouts

To add a new element to your layout, **right-click** the background of the editor.

In the context menu that opens, click on **New Element** and choose one of the many types of elements.

<img width="525" alt="add_element" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/add_element.png?raw=true">

## Customizing Elements

To customize an element, **right-click** it, which will open a context menu with everything you can customize for that element type.

As well as elements you've added, you can also customize vanilla elements (however there are sometimes less options with those)

<img width="525" alt="element_customization" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/element_customization.png?raw=true">

> [!IMPORTANT]
> Some context menus like this are **scrollable**!

## Positioning Elements

Every element in FancyMenu is connected to an **anchor point**.

Anchor points are necessary for calculating an element's position and if used correctly, they prevent elements from overlapping each other, going out-of-screen or move to the wrong place when resizing the window.

They are the origin point from where the element's position is getting calculated.

By default, elements are connected to the **"Center of Screen"** anchor point, which is basically just the exact center of the screen, no matter the window size.
So lets say an element is 2 centimetres away from the center of the screen while being connected to the **"Center of Screen"** anchor. In that case, the element will **always** be 2 centimetres away from the screen's center, no matter the window size.

You can see the anchor point an element is connected to when dragging it. This will (by default) also show all other anchor points. You can hover an anchor point while dragging an element to change the element's anchor to the hovered anchor point.

You can even use an element as an anchor point for other elements! Just hover an element while dragging another and the dragged element's anchor point will get changed to the hovered element.

**[Learn more about how to position your elements.](/positioning-elements)**

<img width="650" alt="anchor_points" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/anchor_points.png?raw=true">

## Saving Your Work

Don't forget to save your masterpiece!

You will see an "Unsaved Changes" indicator in the top-right corner of the editor if you need to save your changes before closing.

Save your work by clicking on **Layout -> Save**!

<img width="375" alt="save_your_work" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/save_your_work.png?raw=true">

> [!TIP]
> You can also save your work using the keyboard shortcut **CTRL + S**

*Congratulations! You can now make Minecraft's menus look a lot more beautiful!*
