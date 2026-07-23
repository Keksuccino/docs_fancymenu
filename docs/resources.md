---
title: Resources
description: How resources work in FancyMenu. Covers resource locations, local resources and web resources.
published: true
date: 2026-05-03T11:01:52.000Z
tags: 
editor: markdown
dateCreated: 2025-04-14T20:15:54.572Z
---

# Resources

Resource fields can load content from:

- **Minecraft:** a resource location provided by Minecraft or a resource pack.
- **Local:** a file in the active game instance.
- **Web:** a direct file URL.

Most image, audio, video, and text fields use the same resource chooser. The chooser includes a browser for Minecraft and resource-pack content.

# Minecraft Resources (Resource Packs)

Resource locations use `namespace:path`. The namespace is the directory immediately below `assets`, and the path is everything below that namespace.

For example, consider a resource pack image stored at `/assets/custom_resources/images/image.png`.
Its resource location is `custom_resources:images/image.png`.

> Minecraft's built-in resources normally use the `minecraft` namespace.
{.is-info}

# Local Resources

Store local resources in `<game-directory>/config/fancymenu/assets/`. `<game-directory>` is the active instance folder, which may differ from `.minecraft`.

Resource fields may show the same path as `/config/fancymenu/assets/example.png`. In those fields, the leading `/` still means `<game-directory>`; it is not a filesystem-root path.

These files can be [shipped with a modpack](./modpacks) through its config folder.

For a complete map of FancyMenu's layout, resource, configuration, and generated-state paths, see [Data Storage Locations](./data-storage-locations).

# Web Resources

Use a direct URL to the file, for example `https://example-domain.net/image.png`. Pages and redirect links are slower and more likely to fail than direct URLs ending in the resource's filename and extension.

# Placeholders in Resource Sources

Chooser-backed resource fields can use [placeholders](./placeholders) in local paths, URLs, and Minecraft resource locations. Select **Open in Editor** beside the source field to edit it directly.

> Resource inputs that do not use the normal chooser may not support placeholders or live source updates.
{.is-warning}
