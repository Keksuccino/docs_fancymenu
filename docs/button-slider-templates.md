---
title: Button and Slider Templates
description: Give all buttons or sliders of a screen the textures, sounds and label style of one template button.
---

# Button and Slider Templates

A template is a [Button element](/elements#button) that passes its look on to all other buttons or all sliders of the screen, vanilla ones and your own. Change the template, and all of them change with it.

> [!TIP]
> For the same look in every menu of the game, use [Global Customizations](/global-customizations) instead. Templates are for one screen, or for all screens a [universal layout](/universal-layouts) loads in.

# Making a Template

1. Add a Button element to the layout.
2. Right-click it, open **Template Settings** and turn on **Template Mode**.
3. Set **Share Settings With** to **Buttons** or **Sliders**.
4. Give the template the textures, sounds and label settings you want, like any other button. Set to **Sliders**, its texture settings are slider textures.

The template doesn't show up outside the editor, so put it wherever it doesn't get in the way. In the editor, a template for sliders looks like a slider.

# What Templates Share

## Always

- Its button textures (or slider textures), with their [nine-slicing](/nine-slicing-and-tiling) settings.
- Its hover, unhover and click sounds.

While a template works, the buttons use its textures and sounds instead of their own. If the template has no textures, the buttons don't use their own textures either.

## When You Turn It On

Turn these on in **Template Settings** of the template:

| Setting | What the buttons get from the template |
|---|---|
| **Share Label in Template Mode** | Its **Label** and **Hover Label**, and its whole label style: **Label Alignment**, **Label Scale**, **Label Base Color**, **Label Hover Color**, **Label Shadow** and **Underline Label On Hover**. |
| **Share X-Position in Template Mode** and **Share Y-Position in Template Mode** | Its position. Vanilla buttons only move once their **Anchor Point** is something other than **Vanilla (Original)**. |
| **Share Opacity in Template Mode** | Its opacity. |

## Label Alignment for All Buttons

With **Share Label in Template Mode**, all buttons get the template's text too, so it's meant for screens where all buttons should say the same.

To only align the labels and keep their texts:

- For one screen, select the buttons with `Ctrl` + click (see [Selecting](/layout-editor#selecting)), right-click one of them and set **Label Alignment** once for all of them.
- For all menus, use **Label Alignment** in [Global Customizations](/global-customizations#labels).

# Good to Know

- Only Button elements can be templates, but they work for vanilla and custom buttons and sliders.
- A screen can have one template for buttons and one for sliders at the same time. With more than one template for the same kind, only one of them works.
- A template only works while it's visible. With [requirements](/element-visibility) on the template, you can turn it on and off.
