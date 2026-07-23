---
title: Localizing Layouts
description: Localize text and other layout content.
published: true
date: 2025-06-16T21:58:07.153Z
tags:
editor: markdown
dateCreated: 2025-04-14T20:15:16.589Z
---

# Localizing Layouts

Use the [**Localize Text** placeholder](./placeholders#localize-text-local) for translatable text:

```text
{"placeholder":"local","values":{"key":"modpack.menu.play"}}
```

FancyMenu first checks Minecraft's active language data. If the key is not present there, it checks FancyMenu's custom localization files. If neither source contains the key, the key itself is shown.

# FancyMenu Custom Localization Files

Place files below:

```text
<game-directory>/config/fancymenu/custom_locals/
```

Create a subdirectory for your localization files:

```text
custom_locals/
└── my_pack/
    └── text.json
```

Put localization files inside at least one subdirectory of `custom_locals`; files placed directly in the `custom_locals` root are not loaded. Nested subdirectories are supported.

Supported UTF-8 formats:

| Extension | Format |
|---|---|
| `.json` | JSON object; nested objects become dot-separated keys |
| `.lang` | `key=value` lines |
| `.properties` | Java properties syntax |

JSON example:

```json
{
  "modpack": {
    "menu": {
      "play": "Play"
    }
  }
}
```

This defines `modpack.menu.play`.

FancyMenu combines the supported files from these subdirectories into one custom localization dictionary. Use each key in only one file. Custom localization files do not switch with Minecraft's selected language; use the resource-pack method below when you need automatic language switching.

Restart the client after editing custom localization files.

# Language-Specific Text

For automatic switching with Minecraft's selected language, provide normal Minecraft language files through a [resource pack](./resources#minecraft-resources-resource-packs):

```text
assets/<namespace>/lang/en_us.json
assets/<namespace>/lang/de_de.json
```

Use the same keys in each language file, enable the resource pack, then read them with the [**Localize Text** placeholder](./placeholders#localize-text-local).

# Localizing Images and Elements

Use the [**Is Game Language** requirement](./conditions#is-game-language-fancymenu_loading_requirement_is_language) to show different elements or layouts for different language codes, such as `en_us` and `de_de`.
