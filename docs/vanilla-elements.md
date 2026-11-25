---
title: Vanilla Elements
description: How to customize elements that are part of screens by default.
published: true
date: 2025-07-05T20:08:37.114Z
tags: 
editor: markdown
dateCreated: 2025-06-26T13:59:53.535Z
---

# Vanilla Elements

FancyMenu does not only allow you to add new stuff to screens, it also makes it possible to customize existing elements from the base game (Vanilla) and even other mods.

## Vanilla Buttons and Sliders (Widgets)

To customize the buttons and sliders of a screen, make a layout for the current screen (not a [universal layout](/universal-layouts)) and right-click them in the editor.

They have the same settings as your own [buttons](/elements#button) and [sliders](/elements#slider), like textures, sounds and tooltips. Only their action script can't change: they keep doing what they did before.

Vanilla elements can't go into [Scrollable Areas](/scrollable-areas), because they belong to the menu itself.

### Labels

- **Label** and **Hover Label** replace the text of a button. For other widgets, like sliders, they're called **Widget Text** and **Hover Widget Text**. Without them, the widget keeps its own text.
- **Label Alignment** puts the label on the **Left**, **Centered** or on the **Right** side of the widget. Labels that are too wide for the widget scroll from side to side, wherever they're aligned.
- **Label Scale**, **Label Base Color**, **Label Hover Color**, **Label Shadow** and **Underline Label On Hover** change the size, colors and shadow of the label.

To align the labels of several buttons at once, select them with `Ctrl` + click (see [Selecting](/layout-editor#selecting)), right-click one of them and set **Label Alignment** for all of them. For the labels of all menus, use **Label Alignment** in [Global Customizations](/global-customizations#labels). A [template](/button-slider-templates) can also give all buttons of a screen its label style.

## Automated Clicks

Vanilla and mod widgets have an **Automated Clicks** property. Set it to an integer greater than `0` to invoke the widget's original left-click behavior that many times when the screen loads. For example, setting it to `2` clicks the widget twice during the first update of each newly opened screen. The default value `0` disables automated clicks.

These are real widget clicks: each click can change a slider or cycle-button value, run the widget's normal callback, or even open another screen. Test the result carefully, especially when configuring more than one click.

To **move** and **resize** Vanilla/mod widgets, you need to give them an anchor point first. To do that, **right-click** them and click on **Anchor Point**. Set it to anything other than **Original**, because that's the default anchor of Vanilla/mod elements.

You can also **hide** Vanilla/mod widgets by simply **right-clicking** them and clicking on **Delete**. They are not actually deleted, but hidden and you can restore them by clicking on **menu bar -> Element -> Deleted Vanilla Elements** and **left-clicking** the element(s) you want to make visible again.

> [!WARNING]
> The **Copyright** widget in the Title screen is the only one you **CAN'T** hide/delete. This is by design. Please don't remove copyright notices.

## Title Screen Elements

The Title screen has elements that are not normal widgets (like the logo, splash text, etc.) that can't be moved or customized. They are meant to get deleted and replaced with custom elements (like an Image element for the logo or a custom Splash Text element for the Vanilla splash text).

To delete them, just right-click them. If you want to restore them later, just click on **menu bar -> Element -> Deleted Vanilla Elements** and **left-click** the element you want to make visible again.

## Troubleshooting: Vanilla Elements Not Visible in The Editor

If you can't see Vanilla elements in the editor, it is probably caused by you using a **universal layout** instead of one **for the current screen**. Make sure to create a layout for the current screen. You can only create layouts for the current screen when customizations are enabled for that screen.

## Troubleshooting: Customizations Don't Get Applied

If customizations to Vanilla elements do not get applied outside the editor, it is usually caused by another mod overriding or altering the parent menu of the Vanilla elements.

A pretty good example for a mod overriding a screen/menu is **Ice and Fire**, which overrides the Title screen.

Customizations not getting applied to menus is not limited to Vanilla elements. Custom elements added to screens will probably also fail to get applied to menus if a mod is overriding or altering them.
