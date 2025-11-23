---
title: Known Issues
description: A list of known issues in the current FancyMenu version. Always up-to-date for the latest build.
published: true
date: 2025-11-23T09:59:04.818Z
tags: 
editor: markdown
dateCreated: 2025-11-09T04:27:59.235Z
---

# Known Issues in FancyMenu

This list always contains known issues of the latest FancyMenu version that did not get fixed yet or can't be fixed at all because of Minecraft limitations, mod conflicts, etc.

# Fixable

These issues can and will be fixed in the future.

## Scoreboard-related placeholders don't work correctly for things not displayed client-side.

All current scoreboard-related placeholders are **client-side**, which means they can only work with data the client knows about, which is not much, because the client only knows about things that are visible to the user (sidebar, tab bar). This is considered a bug an will be fixed in the future.

GitHub Issue Reference: https://github.com/Keksuccino/FancyMenu/issues/1198

# Not Fixable

These issues can't be fixed and will probably stay forever unless they get fixed on the other end (Minecraft, another mod, etc.).

## Player Entity & Item elements are always in front of everything.

FancyMenu's layer system does not work for Player Entity and Item elements, because of how Minecraft renders them. They are always rendered in front of all other GUI elements, at least in older Minecraft versions. It is possible that Minecraft 1.21.8+ is not affected by this anymore.