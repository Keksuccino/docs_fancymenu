---
title: Slideshows
description: Create and use image slideshows.
published: true
date: 2025-04-14T20:16:14.375Z
tags:
editor: markdown
dateCreated: 2025-04-14T20:16:11.469Z
---

# Slideshows

Each slideshow has its own directory below:

```text
<game-directory>/config/fancymenu/slideshows/
```

`<game-directory>` is the active launcher instance, which may differ from the conventional `.minecraft` directory.

# Directory Structure

```text
<game-directory>/config/fancymenu/slideshows/
└── myslideshow/
    ├── properties.txt
    ├── overlay.png          # optional
    └── images/
        ├── image_01.png
        └── image_02.jpg
```

Images must use `.png` or `.jpg`; other extensions, including `.jpeg`, are ignored.

When `randomize = false`, images play in case-insensitive alphabetical filename order. Use zero-padded names such as `image_01.png`, `image_02.png`, and `image_10.png`.

# `properties.txt`

```text
type = slideshow

slideshow-meta {
  name = cool_slideshow
  width = 1920
  height = 1080
  x = 0
  y = 0
  duration = 5.0
  fadespeed = 12.0
  randomize = false
}
```

| Property | Meaning |
|---|---|
| `name` | Required, case-sensitive runtime identifier; keep it unique |
| `width`, `height` | Base size in GUI-scaled pixels and the source aspect ratio |
| `x`, `y` | Base top-left position; normal elements and backgrounds use their own position, so keep these at `0` |
| `duration` | Minimum seconds between transition starts; includes fade time and must be above `0` |
| `fadespeed` | Fade-speed multiplier; `1.0` is the default, higher values fade faster, and the value must be above `0` |
| `randomize` | `true` for random selection or `false` for filename order |

Only `name` is required. Defaults are `width = 50`, `height = 50`, `x = 0`, `y = 0`, `duration = 10.0`, `fadespeed = 1.0`, and `randomize = false`. Keep `type = slideshow` and `slideshow-meta` unchanged; write one `key = value` per line and use a period for decimals.

Layouts select the value of `name`, not the directory name. Duplicate names are not rejected, and directory scan order decides which slideshow remains available. Keep names unique within the slideshows directory.

Random mode picks independently at each transition and avoids an immediate repeat when several images are available. Timing uses real time; a fade that takes longer than `duration` delays the next transition, and returning to a slideshow after it was hidden can advance it immediately.

# Using a Slideshow

Reload FancyMenu through **Customization -> Reload FancyMenu**, or restart the client. Use the [**Slideshow** element](./elements#slideshow), or right-click the layout editor background and select [**Menu Backgrounds**](./menu-backgrounds) -> **Slideshow**.
