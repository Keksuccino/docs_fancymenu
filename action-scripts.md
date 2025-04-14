---
title: Action Scripts
description: How to use action scripts with buttons, sliders, tickers and more.
published: true
date: 2025-04-14T20:15:42.266Z
tags: 
editor: markdown
dateCreated: 2025-04-14T20:02:13.319Z
---

# Action Scripts

FancyMenu lets you add interactivity to your menus by assigning **actions** to elements. These actions run when a button is clicked, ticker is ticking, slider gets used, or when a screen opens or closes. You can also build advanced action scripts using simple control statements, such as **if**, **else-if**, **else**, and **while**, to control which actions run and when.

# What Are Actions?

An **action** is a task or job that FancyMenu runs when triggered. For example, an action might open a new screen, send a chat message, or adjust the volume of an audio element. In FancyMenu’s editor, actions are configured with a value (if needed) that provides extra details—such as a URL or server address.

# What Are Statements?

To create more complex behavior, FancyMenu supports basic control statements in action scripts. These include:

- **If Statement:** Runs a block of actions only if a specified [condition](/en/conditions) is met.
- **Else-If Statement:** Checks another [condition](/en/conditions) if the preceding *if* (or earlier *else-if*) wasn’t met.
- **Else Statement:** Runs if none of the preceding [conditions](/en/conditions) are met.
- **While Statement:** Repeats a block of actions continuously while a [condition](/en/conditions) remains true (with a built‑in timeout to prevent infinite loops).

By combining these statements with actions, you can build dynamic and conditional behavior, for example, checking if a player’s health is low before sending a warning message or repeating an update until a condition changes.

# Where Can You Use Action Scripts?

Action scripts are versatile and can be used throughout your layout. You can assign them, for example, to:

- **Buttons:** Execute an action when the button is clicked.
- **Tickers:** Continuously run an action script to update on-screen information.
- **Sliders:** Trigger an action script whenever the slider’s value changes.
- **Screen Events:** Run scripts when a screen opens or closes (for example, playing a sound when a menu appears).

# Using Placeholders in Actions

Action values support dynamic content through **placeholders**. Most of the time these placeholders use a JSON-like syntax and are replaced with live data when the action runs.

## JSON-Like Placeholders

These are the normal [placeholders](/en/placeholders) that can be used in many places throughout layouts.

They follow this syntax:

```json
{"placeholder": "placeholder_id", "values": {"key1": "value1", "key2": "value2"}}
```

They can fetch game data like the player’s name, screen dimensions, or calculated values using the **Calculator** placeholder. You can also nest placeholders for more advanced uses.

## The `$$value` Placeholder

The `$$value` placeholder is special. It’s used to insert the current interactive value of the element that the action is attached to. For example, if actions are used with a slider, using `$$value` in the action will be replaced with the slider’s current value.

# Examples of Actions

Here are a few common actions you can assign via FancyMenu:

## Open URL in Browser

- **Description:** Opens a URL in your web browser.  
- **Value Example:** `https://example.com`  
- **Usage:** Assign this action to a button. When clicked, FancyMenu opens the specified URL.

## Join Server

- **Description:** Connects the player to a Minecraft server.  
- **Value Example:** `exampleserver.com:25565`  
- **Usage:** Attach this action to a button to allow players to join a server.

## Send Chat Message/Command

- **Description:** Sends a chat message or executes a chat command.  
- **Value Example:** `Hello, world!` or `/help`  
- **Usage:** When triggered, the provided text is sent as a chat message. If the text begins with a `/`, it’s treated as a command.

# How to Set Up and Edit Actions

To add, edit, or remove actions (and statement blocks) for an element, simply **right-click the element** (whether it’s a button, slider, ticker, or other interactive item) and then select **Manage Action Script**. This opens the Manage Actions screen, where you can:

- **Add new actions or statements:** Insert new action entries or control statements (if, else-if, else, while) to build your script.
- **Edit existing actions or statements:** Modify the action value or change the control logic.
- **Remove actions or statements:** Delete unwanted actions from the script.