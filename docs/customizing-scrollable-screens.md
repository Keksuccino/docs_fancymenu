---
title: Scrollable Screens
description: How to customize scrollable screens.
published: true
date: 2025-07-17T15:16:10.099Z
tags: 
editor: markdown
dateCreated: 2025-07-05T20:01:34.059Z
---

# Customizing Scrollable Screens

Customizing scrollable screens like the Options screens can be a bit tricky, since FancyMenu can't "see" or customize content inside scroll areas.

Some scrollable screens can be made customizable by exposing widgets inside their scroll areas. This is experimental and does not work on every screen.

To enable the exposing feature for a specific screen, click on **menu bar -> Customization -> Expose Scroll Area Content Of Current Screen**. It is not possible to enable this feature for all screens at once and some screens will not allow you to enable it at all, like the Singleplayer and Multiplayer menus.

Enabling this feature will stack all widgets found in scroll areas in the top-left corner of the screen. This is by design and not a bug. You can then open a layout **for the current screen** and should be able to see and edit (move, resize, etc.) these widgets in the editor.

The most important thing to keep in mind when using this feature is that exposing scroll area widgets will REMOVE the original scroll area from the screen and everything inside the scroll area that is not a normal widget (widgets are buttons and sliders) will get LOST, so it will not be visible or interactable while the exposing feature is enabled.
