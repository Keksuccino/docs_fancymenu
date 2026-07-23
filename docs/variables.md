---
title: Variables
description: How to create and use variables.
published: true
date: 2026-05-03T11:01:52.000Z
tags: 
editor: markdown
dateCreated: 2025-04-14T20:16:28.294Z
---

# Variables in FancyMenu

Variables store text values that layouts, actions, placeholders, requirements, listeners, schedulers, and Custom GUIs can reuse.

## Creating Variables

To create a variable in FancyMenu:

1. Make sure you're not currently in the Layout Editor. 
2. Click on the menu bar at the top of the screen.
3. Go to **Customization -> Variables -> Manage Variables**.
4. In the "Manage Variables" screen that appears, click the **Add Variable** button.
5. Type in a name for your new variable and click **OK**.

That's it! Your variable is ready to use. You can see it listed in the "Manage Variables" screen.

The Manage Variables window supports a right-click context menu, keyboard navigation, copy/paste, undo/redo, type-to-search, **Delete** to delete, and **Ctrl/Command + S** to save.

## Setting Variable Values

An empty variable isn't very useful on its own. To make variables work for you, you need to put data into them. In FancyMenu, this is called "setting the variable value." 

There are two main ways to set a variable's value:

1. In the "Manage Variables" screen, find the variable in the list, click it, and then click **Set Value**. Type in the data you want to store.

2. While customizing your menu, use the [**Set Variable Value** action](./action-scripts#set-variable-value-fm-variable-set_variable) on a [Button](./elements#button), [Slider](./elements#slider), or [Ticker](./elements#ticker) element.

For example, create a variable named `clicks` and add the [**Set Variable Value** action](./action-scripts#set-variable-value-fm-variable-set_variable) to a button:

```
clicks:{"placeholder":"calc","values":{"expression":"{"placeholder":"getvariable","values":{"name":"clicks"}} + 1"}}
```

Here's how this works:
1. The [**Get Stored Variable** placeholder](./placeholders#get-variable-value-fm-variable-getvariable) retrieves the current value of the `clicks` variable.
2. The [**Calculator** placeholder](./placeholders#calculator-calc) takes that value and adds 1 to it.
3. The result is stored back into `clicks` using the [**Set Variable Value** action](./action-scripts#set-variable-value-fm-variable-set_variable).

So each time the button is clicked, the `clicks` variable will increment by 1, effectively counting the total number of clicks.

## Using Variables

Now that you have variables holding data, you can use that data in different parts of your menu customization:

* [**Loading Requirements**](./conditions): Check a variable's value to control when elements appear. For example, show an element when `clicks` is greater than 5 by combining [**Is Number**](./conditions#is-number-fancymenu_visibility_requirement_is_number) with the [**Get Stored Variable** placeholder](./placeholders#get-variable-value-fm-variable-getvariable).

* **Placeholders**: Insert a variable into text with the [**Get Stored Variable** placeholder](./placeholders#get-variable-value-fm-variable-getvariable), for example `{"placeholder":"getvariable","values":{"name":"clicks"}}`.

* **Nested Placeholders**: You can use the [**Get Stored Variable** placeholder](./placeholders#get-variable-value-fm-variable-getvariable) inside the [**Calculator** placeholder](./placeholders#calculator-calc).

* **Actions**: Variables can create dynamic behavior:
  - Use an **IF** statement in an [action script](./action-scripts#what-are-statements) with [**Is Number**](./conditions#is-number-fancymenu_visibility_requirement_is_number) and the [**Get Stored Variable** placeholder](./placeholders#get-variable-value-fm-variable-getvariable).
  - Combine the [**Get Stored Variable** placeholder](./placeholders#get-variable-value-fm-variable-getvariable) with [**Copy Text to Clipboard**](./action-scripts#copy-text-to-clipboard-copytoclipboard).
  - Use variables in [**Open Screen or Custom GUI**](./action-scripts#open-screen-or-custom-gui-opengui) to select a screen from stored progress or preferences.

## Variable Examples

Here are a few examples to inspire your own variable usage:

1. **High Score**: Create a `highscore` variable and a button that sets it to the player's current score if it is higher than the existing value. Display it with the [**Get Stored Variable** placeholder](./placeholders#get-variable-value-fm-variable-getvariable).

2. **Difficulty Selector**: Make variables for different game difficulties, like `easy`, `medium`, and `hard`. Use buttons to set the difficulty variable, and show/hide elements based on the selected difficulty.

3. **Tutorial Progress**: Add variables to track the player's progress through a tutorial, like `tutorial_step`. Increment the variable as they complete each step, and use loading requirements to gradually reveal more of the menu.

## Persistence, Scope, and Storage

Variables are shared across the current Minecraft instance. They are not separated per layout, world, server, or player.

Values are saved immediately in `<game-directory>/config/fancymenu/user_variables.db` and survive restarts.

- **Reset on Launch** empties that variable the next time the game starts.
- [**Clear All Variables**](./action-scripts#clear-all-variables-fm-variable-clear_variables) removes all stored variable values.
- Names are case-sensitive. Use simple, unique names such as `tutorial_step`.

The [**Get Stored Variable** placeholder](./placeholders#get-variable-value-fm-variable-getvariable) returns `0` when the named variable does not exist or when its stored value is empty. This fallback matters in comparisons and calculator expressions.

The [**Set Variable Value** action](./action-scripts#set-variable-value-fm-variable-set_variable) uses `variable_name:variable_value` and splits at the first colon, so the value may contain more colons.

Do not store passwords, tokens, or other secrets in FancyMenu variables. They are readable configuration data.
