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

FancyMenu 3.9.0 reworks the Manage Variables window. Important actions are available through a right-click context menu, the list supports keyboard navigation, variables can be copied/pasted, changes can be undone/redone, typing starts a search, **DEL** deletes the selected variable, and **CTRL + S** confirms the window.

## Setting Variable Values

An empty variable isn't very useful on its own. To make variables work for you, you need to put data into them. In FancyMenu, this is called "setting the variable value." 

There are two main ways to set a variable's value:

1. In the "Manage Variables" screen, find the variable in the list, click it, and then click **Set Value**. Type in the data you want to store.

2. While customizing your menu, use the **Set Variable** action on a Button, Slider or Ticker element. With this action, you specify the variable name and the value to store in it. When someone, for example, clicks a button with this action, the variable will update with the new value.

For example, let's say you create a variable named `clicks` to count how many times a button is pressed. You would add the **Set Variable** action to the button, and use a placeholder in the action's value to increment the click count each time, like this:

```
clicks:{"placeholder":"calc","values":{"expression":"{"placeholder":"getvariable","values":{"name":"clicks"}} + 1"}}
```

Here's how this works:
1. The **Get Stored Variable** placeholder retrieves the current value of the `clicks` variable.
2. The **Calculator** placeholder takes that value and adds 1 to it.
3. The result is then stored back into the `clicks` variable using the **Set Variable** action.

So each time the button is clicked, the `clicks` variable will increment by 1, effectively counting the total number of clicks.

## Using Variables

Now that you have variables holding data, you can use that data in different parts of your menu customization:

* **Loading Requirements**: You can check a variable's value in a loading requirement to control when certain menu elements appear. For example, you could make an element only show up if the `clicks` variable is greater than 5 by using a combination of the **Is Number** requirement and the **Get Stored Variable** placeholder.

* **Placeholders**: Variables can be inserted into text using the **Get Stored Variable** placeholder. If you have a text element, you could use `{"placeholder":"getvariable","values":{"name":"clicks"}}` to display the current value of the "clicks" variable.

* **Nested Placeholders**: You can even use variables inside other placeholders! The click counting example above demonstrated this by using the **Get Stored Variable** placeholder inside the **Calculator** placeholder.

* **Actions**: Variables can be used in actions to create dynamic behavior based on variable values. Here are a few examples:
    - Use an **IF** statement in an action script to check a variable's value using a combination of the **Is Number** requirement and the **Get Stored Variable** placeholder, then perform different actions based on the result. For instance, you could have a button that says "You've clicked me X times!" and use an IF block to show a special message if the number of clicks is over 10.
    - Combine the **Get Stored Variable** placeholder with the **Copy to Clipboard** action to let users copy the value of a variable to their clipboard.
    - Use variables in the **Open GUI** action to load different screens based on the user's progress or preferences, which you track with variables.

## Variable Examples

Here are a few examples to inspire your own variable usage:

1. **High Score**: Create a `highscore` variable and a button that sets it to the player's current score if it's higher than the existing value. Display the high score on the menu using the **Get Stored Variable** placeholder.

2. **Difficulty Selector**: Make variables for different game difficulties, like `easy`, `medium`, and `hard`. Use buttons to set the difficulty variable, and show/hide elements based on the selected difficulty.

3. **Tutorial Progress**: Add variables to track the player's progress through a tutorial, like `tutorial_step`. Increment the variable as they complete each step, and use loading requirements to gradually reveal more of the menu.

## Persistence, Scope, and Storage

Variables are shared across the current Minecraft instance. They are not separated per layout, world, server, or player.

Values are saved immediately in `<game-directory>/config/fancymenu/user_variables.db` and survive restarts.

- **Reset on Launch** empties that variable the next time the game starts.
- **Clear All Variables** removes all stored variable values.
- Names are case-sensitive. Use simple, unique names such as `tutorial_step`.

The **Get Stored Variable** placeholder returns `0` when the named variable does not exist or when its stored value is empty. This fallback matters in comparisons and calculator expressions.

The **Set Variable** action uses `variable_name:variable_value` and splits at the first colon, so the value may contain more colons.

Do not store passwords, tokens, or other secrets in FancyMenu variables. They are readable configuration data.
