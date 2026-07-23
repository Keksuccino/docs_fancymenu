---
title: Text in Menus
description: How to add text content to menus.
---
# Text in Menus

FancyMenu allows you to add text content to menus/screens via the **Text** element.

This element is scrollable, has full Markdown support and line wrapping, which makes it very powerful for displaying even complex text content, but it's also great for simple one-liners.

# Text Content

The Text element can fetch its content in many ways. It allows you to set a source for its text content, which can be a direct plain text input, a local text file in FancyMenu's assets directory (`<game-directory>/config/fancymenu/assets/`), a web text file (via URL) or a local text file loaded via resource pack.

Using the web source type as text source is especially useful if you want to make something like a changelog that's always up-to-date or a news tickers and similar things, without the need to release an update for your modpack.

Keep in mind that FancyMenu caches the content of text sources, so it doesn't have to constantly fetch the content again (which would be very bad for performance). The content is only cached for the active session, so restarting the game will clear the cache. You can also clear the cache by reloading FancyMenu via **menu bar -> Customization -> Reload FancyMenu**.

# Placeholders

The Text element also supports FancyMenu's placeholder system, which makes it possible to make text content dynamic and react to various changes to menus, worlds, players, etc.

# Customizing or Disabling Markdown

If you want to customize the colors for headlines or other things related to Markdown, just **right-click** the Text element and click on **Markdown**. In the sub context menu that opens, you will see lots of options for customizing the appearance and behaviour of the Markdown parser.

In case you don't want Markdown parsing at all, which can improve performance for long text content, you can disable Markdown completely in the **Markdown** menu when **right-clicking** the Text element.

# Disabling Line Wrapping

If you don't want line wrapping, you can disable it by **right-clicking** the Text element.

# Disabling Scrolling & Hiding The Scroll Grabbers

Text elements are scrollable by default and if the element thinks the user needs to scroll for seeing all of its content, it will show its scroll bars/grabbers, which are small, grey translucent bars (with rounded edges) at the right and bottom sides of the Text element (vertical and horizontal scroll bars). The scroll grabbers sometimes also get mistaken for shadows.

You can disable these grabbers by toggling off **Scrolling** in the menu that opens when **right-clicking** the element. This will disable scrolling in general, not just the grabbers. If you just want the grabbers to be invisible, while still being able to scroll, you can set custom scroll grabber textures by right-clicking the element. Just set a fully transparent texture there.

# Minecraft's Raw Component Text Format (Serialized JSON Components)

The Text element does NOT have support for Minecraft's raw component format. This format is only supported by button and slider labels.
