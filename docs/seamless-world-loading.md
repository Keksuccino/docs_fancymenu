---
title: Seamless World Loading
description: Use a recent world view as the next loading background.
published: true
date: 2026-05-03T11:01:52.000Z
tags:
editor: markdown
dateCreated: 2026-05-03T11:01:52.000Z
---

# Seamless World Loading

Seamless World Loading uses a recent view of a world or server as its next loading-screen background.

Enable it through [**Customization -> Global Customizations**](./global-customizations) -> **Seamless World Loading**.

# How It Works

- FancyMenu periodically captures the current frame while you are in a tracked world or server.
- The latest capture is saved when you leave.
- Each world and server has its own hashed PNG filename.
- FancyMenu preloads up to five recent world captures and five recent server captures.
- Nothing is shown for a target until its first capture has been saved.

Captures are stored in:

```text
<game-directory>/fancymenu_data/seamless_world_loading/
```

The screenshots can contain anything visible in the world when captured. Disabling Seamless World Loading stops capture and use, but does not delete existing PNG files. Delete unwanted captures from the directory while the game is closed.
