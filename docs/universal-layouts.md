---
title: Universal Layouts
description: Apply one layout to multiple supported screens.
published: true
date: 2025-05-08T23:45:48.625Z
tags:
editor: markdown
dateCreated: 2025-05-08T23:42:27.319Z
---

# Universal Layouts

A Universal Layout is considered for every supported screen that has screen customization enabled. It does not apply to [blocked](./incompatibility-list#screens-where-customization-is-intentionally-disabled) or otherwise excluded screens.

Use Universal Layouts for shared elements such as logos, navigation, overlays, or [Audio elements](./elements#audio) that should continue across several screens.

# Creating One

1. Open a supported screen and show the FancyMenu menu bar.
2. Select **Layouts -> New -> For All Screens [Universal]**.
3. Add and configure elements.
4. Save the layout.

Ordinary screens still require **Current Screen Customization** to be enabled. There is no global enable-all switch because unsupported mod screens can break when customized.

# Limiting Screens

Open the Universal Layout settings from the editor background context menu.

- **Whitelist:** the layout applies only to listed screen identifiers.
- **Blacklist:** the layout applies to every eligible screen except listed identifiers.

Use **Customization -> Copy Identifier of Current Screen** to copy a [screen identifier](./screen-identifiers).

You can also add [layout-wide requirements](./conditions#layout-wide-requirements) to control when the layout applies.

# Layout Order

Eligible Universal Layouts and screen-specific layouts are combined and stacked by **Layout Index**. Lower indexes are applied first; later stackable settings can override earlier ones. At the same index, Universal Layouts are collected before screen-specific layouts.
