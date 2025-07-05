---
title: Vanilla Elements
description: How to customize elements that are part of screens by default.
published: true
date: 2025-07-05T19:26:08.462Z
tags: 
editor: markdown
dateCreated: 2025-06-26T13:59:53.535Z
---

# Vanilla Elements

FancyMenu does not only allow you to add new stuff to screens, it also makes it possible to customize existing elements from the base game (Vanilla) and even other mods.

## Vanilla Buttons and Sliders (Widgets)

To customize existing Vanilla/mod widgets, just make a new layout **"for the current screen"** (NOT universal!) and **right-click** the elements in the editor just like you would do with custom ones.

You can customize their **labels and textures** just like you would do with custom buttons and sliders.

The only thing you **can't do** with Vanilla/mod widgets is customizing their **action script** (like changing what they do when interacting with them). This is only possible with custom buttons and sliders.

To **move** and **resize** Vanilla/mod widgets, you need to give them an anchor point first. To do that, **right-click** them and click on **Anchor Point**. Set it to anything other than **Original**, because that's the default anchor of Vanilla/mod elements.

You can also **hide** Vanilla/mod widgets by simply **right-clicking** them and clicking on **Delete**. They are not actually deleted, but hidden and you can restore them by clicking on **menu bar -> Element -> Deleted Vanilla Elements** and **left-clicking** the element(s) you want to make visible again.

> The **Copyright** widget in the Title screen is the only one you **CAN'T** hide/delete. This is by design. Please don't remove copyright notices.
{.is-warning}

## Title Screen Elements

The Title screen has elements that are not normal widgets (like the logo, splash text, etc.) that can't be moved or customized. They are meant to get deleted and replaced with custom elements (like an Image element for the logo or a custom Splash Text element for the Vanilla splash text).

To delete them, just right-click them. If you want to restore them later, just click on **menu bar -> Element -> Deleted Vanilla Elements** and **left-click** the element you want to make visible again.

## Troubleshooting: Customizations Don't Get Applied

If customizations to Vanilla elements do not get applied outside the editor, it is usually caused by another mod overriding or altering the parent menu of the Vanilla elements.

A pretty good example for a mod overriding a screen/menu is **Ice and Fire**, which overrides the Title screen.

Customizations not getting applied to menus is not limited to Vanilla elements. Custom elements added to screens will probably also fail to get applied to menus if a mod is overriding or altering them.