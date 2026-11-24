---
title: Player Entities
description: Show players in your menus with the Player Entity element, with their skin, name, pose, armor and more.
---

# Player Entities

The Player Entity element shows a player in 3D, like the player's own character next to the title screen buttons. It can copy the person who plays, show any other player, or be a character of your own with its own skin, cape and name.

<img width="800" alt="Five Player Entities: a real player with skin and cape, one in enchanted diamond armor with a sword and shield, one crouching, one waving and a baby" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/player_entities_showcase.png?raw=true">

> [!IMPORTANT]
> On Minecraft 1.20.1 and newer, Player Entities need the mod Fancy Entity Renderer ([CurseForge](https://www.curseforge.com/minecraft/mc-mods/fancy-entity-renderer), [Modrinth](https://modrinth.com/mod/fancy-entity-renderer)). Without it, they show a red box. When there's no build of it for your Minecraft version yet, Player Entities can't show there.

# Adding a Player Entity

Right-click the editor background and click **New Element -> Player Entity**. Drag its handles to change its size. The size of the player follows the height of the element.

All settings below are in the right-click menu of the element.

# Who It Shows

- **Copy Client Player** shows the person who plays, with their name, skin and cape. While it's on, the name, skin and cape settings are locked.
- **Player Name** can be any name, it doesn't have to belong to a real player. It supports [placeholders](/placeholders).
- **Show Player Name** shows the name tag above the head. With **Nametag Rotation** off, the name tag doesn't turn with the player.

## Skin and Cape

- **Auto Skin** and **Auto Cape** load the skin and cape of the player with that **Player Name**. That needs an internet connection.
- **Skin Texture** and **Cape Texture** use your own skin and cape files, like a skin from your [assets](/resources). Skins are the normal skin files of Minecraft.
- **Slim Skin** is for skins with thin arms, like Alex. **Auto Skin** and **Copy Client Player** find out on their own.

# Pose and Movement

<img width="800" alt="Two Player Entities look at the mouse pointer while it moves around: the left one only turns its head, the right one turns its head and body" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/player_entities_follow_mouse.gif?raw=true">

- **Head Follows Mouse** and **Body Follows Mouse** make the player look at the mouse pointer. Both are on for new Player Entities.
- **Pose** picks a body pose: **Standing**, **Crouching**, **Sleeping**, **Swimming**, **Dying** or **Spin Attack**.
- **Body Movement** animates the pose.

## Entity Pose

**Entity Pose** opens a window with the X, Y and Z rotation of the **Head**, **Body**, **Left Arm**, **Right Arm**, **Left Leg** and **Right Leg**, from `-180` to `180`.

<img width="800" alt="The Entity Pose window with rotation sliders for the head and body of the player" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/player_entities_pose_window.png?raw=true">

**Advanced Mode** next to a slider turns it into a text value with [placeholder](/placeholders) support. With a [variable](/variables) in it, like `$$arm_angle`, a [Scheduler](/schedulers) can animate the player by changing the variable.

# Armor, Items and More

- **Armor and Tools** puts items on the player: **Head Armor**, **Chest Armor**, **Legs Armor**, **Feet Armor**, **Left Hand Tool** and **Right Hand Tool**. Set them to an item ID, like `minecraft:diamond_sword`. Item IDs support placeholders. **Enchant Head Armor** and the other Enchant switches add the enchantment glint.
- **Is Baby** makes the player small, like a baby.
- **Parrot** puts a parrot on the right shoulder, or on the left one with **Parrot On Left Shoulder**.

# Good to Know

- Player Entities can't be rotated, tilted, faded or made see-through.
- For just the head of a player, see [Player Heads](/player-heads).
- On Minecraft 1.19.2, Player Entities don't need Fancy Entity Renderer, but they have fewer settings: **Crouching** instead of **Pose**, and no **Nametag Rotation**, **Body Movement** or **Armor and Tools**. Their size comes from **Entity Scale** (default `30`, so `60` is twice as big) instead of the element's size.
