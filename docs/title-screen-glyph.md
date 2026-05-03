---
title: Title Screen Glyph
description: How to hide/remove the little diamond or emerald (green or blue) glyph/icon in the Title screen.
published: true
date: 2025-07-06T15:15:42.758Z
tags: 
editor: markdown
dateCreated: 2025-07-06T15:15:39.543Z
---

# Emerald/Diamond Icon in the Title Screen

If you struggle to hide the little icon that keeps appearing in your Title screen and that looks like a little diamond or emerald (green or blue little icon), this is mostly the mod update notification of either Mod Menu (Fabric mod) or Forge (built-in modloader feature).

In some cases it can also be part of Vanilla Minecraft's Realms button (to show notifications).

# Hiding the Mod Menu Icon

To hide the glyph from Mod Menu, you need to disable the "update indicator" in its settings.

Click on the **Mods** button -> Hover over the icon of the Mod Menu mod in the mods list -> Click on it -> Set the "Update Indicator" to "Hidden".

# Hiding the Forge Icon

Forge uses a built-in version checker to show that emerald icon when mods are outdated. You can turn it off:

1. Open your config/fml.toml file.
2. Find the `versionCheck` setting.
3. Set it to `false`: `versionCheck = false`
4. Save and restart Minecraft.

This disables the version check entirely, which also hides the emerald glyph at launch.

Another way to hide the icon is by simply hiding the whole Mods button via FancyMenu. Hiding the button will also hide the glyph.

# Hiding the Vanilla Realms Icons

In case it's neither the Mod Menu nor the Forge glyph, it's probably Minecraft's own Realms notification icons. These icons show roughly at the position of the Realms button and can be hidden with FancyMenu in the layout editor. You need to make a layout "for the current screen" (Title screen in this case) and then you will the the Realms icons as a dedicated element in the editor. To hide it, just **right-click** it and click on **Delete**.

The Realms icons can be a newspaper icon, a diamond glyph and others, like a red circle with a notification counter.
