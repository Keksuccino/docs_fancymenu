---
title: Player Entities
description: How FancyMenu's "Player Entity" element works and how to use it correctly.
published: true
date: 2025-09-01T17:14:09.508Z
tags: 
editor: markdown
dateCreated: 2025-08-20T02:29:56.333Z
---

# Player Entities

FancyMenu allows you to add player entities to screens, so you can display the client player or other players, including custom entities that do not represent a real player at all with a custom skin, name, cape and so on.

# Client Player

To show a "mirror" of the client player, just right-click the Player Entity element and enable **Copy Client Player**. This will copy the client player's skin, cape and name.

# Other Players

If you want to show another existing player, just right-click the element and set the **Player Name** to an existing player name. This will automatically show the skin, cape and name of that existing player, as long as you do not have a custom skin or cape set and **Copy Client Player** is **disabled**.

# Custom Player Entities

If you do not want to show a real player at all and instead want to fully customize the entities skin, cape and name, you can right-click the element. There are options to set a custom skin and cape texture. If a custom skin and cape is active, you can also set any player name you want without it copying the player name's skin if the player exists.

# Entity Pose

The Player Entity element has full support for customizing its pose, so in other words you can freely move all of its limbs, body parts, etc.

To do that, right-click the element and click on **Player Pose**. This will open a screen with sliders to configure the X/Y/Z rotation of all body parts.

The player pose settings have a normal mode where you can customize the rotations with sliders and there's also an advanced mode that allows a text input for all rotations with full placeholder support, which makes it possible to even animate the entity with a Ticker element that sets rotation variables!

# Changing the Entity Size

Unlike most other elements in FancyMenu, Player Entity elements do not support direct resizing via the resize grabbers. Instead you need to right-click the element and click on **Scale**. This allows you to set a scale for the element. The default one should be `30`, so setting it to `60` for example makes the player twice as big as normal, setting it to `15` shows it at half the size and so on.

# Dependency: Fancy Entity Renderer (FER)

For Minecraft 1.21.4+, there is an extra mod needed for making Player Entity elements work. The mod is called "Fancy Entity Renderer" and is available on CurseForge and Modrinth.

If there is no build available yet for the Minecraft version you're using, it will most likely get released at a later point.

Please keep in mind that FER is not developed by Keksuccino, so he has no control over when builds get released.