---
title: Known Issues
description: A list of known issues in the current FancyMenu version. Always up-to-date for the latest build.
published: true
date: 2025-11-09T04:30:38.922Z
tags: 
editor: markdown
dateCreated: 2025-11-09T04:27:59.235Z
---

# Known Issues in FancyMenu

This list always contains known issues of the latest FancyMenu version that did not get fixed yet or can't be fixed at all because of Minecraft limitations, mod conflicts, etc.

## Scoreboard-related placeholders don't work correctly for things not displayed client-side.

All current scoreboard-related placeholders are **client-side**, which means they can only work with data the client knows about, which is not much, because the client only knows about things that are visible to the user (sidebar, tab bar). This is considered a bug an will be fixed in the future.

GitHub Issue Reference: https://github.com/Keksuccino/FancyMenu/issues/1198

## NBT Data placeholder is client-side only currently.

The NBT Data placeholder currently does not work correctly in some cases, because it can't fetch everything client-side. This is considered a bug and will be fixed in the future.

GitHub Issue Reference: https://github.com/Keksuccino/FancyMenu/issues/1344, https://github.com/Keksuccino/FancyMenu/issues/1273, https://github.com/Keksuccino/FancyMenu/issues/1260

## MCEF-related features like video and browser stuff is unstable.

Videos sometimes show only a black screen, browsers don't load correctly and similar things. This is considered a bug in FancyMenu (not MCEF) and it will be fixed in the future.