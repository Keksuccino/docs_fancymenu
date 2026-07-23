---
title: Panoramas
description: Create and use six-image cubic panoramas.
published: true
date: 2025-04-14T20:15:36.113Z
tags:
editor: markdown
dateCreated: 2025-04-14T20:15:33.094Z
---

# Cubic Panoramas

Each panorama has its own directory below:

```text
<game-directory>/config/fancymenu/panoramas/
```

`<game-directory>` is the active launcher instance, which may differ from the conventional `.minecraft` directory.

# Directory Structure

```text
<game-directory>/config/fancymenu/panoramas/
└── mypanorama/
    ├── properties.txt
    ├── overlay.png          # optional
    └── panorama/
        ├── panorama_0.png
        ├── panorama_1.png
        ├── panorama_2.png
        ├── panorama_3.png
        ├── panorama_4.png
        └── panorama_5.png
```

The six face images must be PNG files with the exact names shown above, and all six must have identical dimensions. File-name case can matter on some operating systems.

Add an optional `overlay.png` beside `properties.txt` for a vignette or other full-panorama overlay.

# `properties.txt`

```text
type = panorama

panorama-meta {
  name = name_of_your_panorama
  speed = 1.0
  fov = 85.0
  angle = 25.0
  start_rotation = 0
}
```

| Property | Meaning |
|---|---|
| `name` | Required, case-sensitive runtime identifier; keep it unique |
| `speed` | Rotation-speed multiplier; `1.0` is the default |
| `fov` | Field of view in degrees |
| `angle` | Vertical viewing angle in degrees |
| `start_rotation` | Initial horizontal rotation in degrees |

Only `name` is required. Missing optional values use the defaults shown in the example. Keep `type = panorama` and `panorama-meta` unchanged; write one `key = value` per line and use a period for decimals.

Duplicate names are not rejected, and directory scan order decides which panorama remains available. Keep names unique within the panoramas directory. Panorama and slideshow names use separate lists.

# Using a Panorama

Reload FancyMenu through **Customization -> Reload FancyMenu**, or restart the client. Then right-click the layout editor background and select [**Menu Backgrounds**](./menu-backgrounds) -> **Cubic Panorama**.
