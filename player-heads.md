---
title: Player Heads
description: How to display a player's head as 2D or 3D image in a menu.
published: true
date: 2025-06-21T16:30:03.913Z
tags: 
editor: markdown
dateCreated: 2025-06-21T16:14:25.615Z
---

# Player Heads in Menus

To display a player's head as a 2D or 3D image using an Image element, you can use a 3rd-party web API called "Minotar".

## 2D Image

### 1. Add an Image Element

In the FancyMenu editor, right-click on the background, select "New Element," and then choose "Image" (or "Picture").

### 2. Set the Web Source

Right-click the Image element to access its properties. For the source type, select "Web."

### 3. Construct the URL with the Correct Placeholder

In the "Source" field, you would enter the following URL:
`https://minotar.net/avatar/{"placeholder":"playername"}.png`

FancyMenu will use the `{"placeholder":"playername"}` to dynamically insert the current player's username into the URL, allowing the Image element to fetch and display their head from Minotar.

## 3D Image

This one's pretty similar to the 2D version, but here we need to use a different URL:

`https://minotar.net/cube/{"placeholder":"playername"}/200.png`

The `200` is the pixel size in this case, so if you want a smaller version, just replace it with `100` for example, or for a bigger version, use `300` and so on.