---
title: Custom Cursor
description: How to make menus use a custom mouse cursor.
published: true
date: 2025-06-25T18:46:37.027Z
tags: 
editor: markdown
dateCreated: 2025-06-25T18:46:32.912Z
---

# Custom Mouse Cursor

Add a [**Cursor** element](./elements#cursor) to a layout to replace the system cursor on that screen:

1. Select **New Element -> Cursor**.
2. Set a PNG texture with RGBA color.
3. Set **Hotspot X** and **Hotspot Y** to the texture pixel where clicks should occur.
4. Enable the editor preview when you want to check the cursor while editing.
5. Use a [Universal Layout](./universal-layouts) when the same cursor should appear on multiple supported screens.

Small cursor textures such as `32×32` or `64×64` are recommended. Cursor appearance and behavior can vary by operating system.
