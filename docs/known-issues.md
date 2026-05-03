---
title: Known Issues
description: A list of known issues in the current FancyMenu version. Always up-to-date for the latest build.
published: true
date: 2026-02-07T05:24:40.032Z
tags: 
editor: markdown
dateCreated: 2025-11-09T04:27:59.235Z
---

# Known Issues in FancyMenu

This list always contains known issues of the latest FancyMenu version that did not get fixed yet or can't be fixed at all because of Minecraft limitations, mod conflicts, etc.

# Fixable

These issues can and will be fixed in the future.

## Scoreboard-related features are broken. They do not work.

All features (placeholders, actions, requirements) that access scoreboard, score or player tag data DO NOT WORK as intended right now. Depending on the FancyMenu version, scoreboard-related features are not available at all anymore, because they got removed for now, to rework them and re-implement them in the future. Even if available, these features should NOT GET USED right now! They will not work anyway.

# Not Fixable

These issues can't be fixed and will probably stay forever unless they get fixed on the other end (Minecraft, another mod, etc.).

## Player Entity & Item elements are always in front of everything.

FancyMenu's layer system does not work for Player Entity and Item elements, because of how Minecraft renders them. They are always rendered in front of all other GUI elements, at least in older Minecraft versions. It is possible that Minecraft 1.21.8+ is not affected by this anymore.