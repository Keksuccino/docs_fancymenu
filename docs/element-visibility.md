---
title: Element Visibility
description: How to show and hide elements with requirements, delays, fading and opacity, and how to toggle them with a button.
---

# Element Visibility

Elements don't have to show all the time. They can show only in certain situations, show up a bit later, fade in and out, or get turned on and off with a button.

<img width="800" alt="A welcome text fades in a few seconds after the screen opens, then a Server Rules button fades a rules panel in and out" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/element_visibility_toggle.gif?raw=true">

In the layout editor, elements always show, so you can still edit them. Everything on this page works outside of the editor.

> [!TIP]
> All requirements are listed in [Requirements](/conditions).

# Showing Elements Only Sometimes

Right-click an element and click **Loading Requirements**. The element only shows while all of its [requirements](/conditions) are met, like "the mouse is over this button", "it's December" or "a variable has this value". FancyMenu checks them all the time, so the element shows and hides right away.

- **Requirement Mode** Opposite turns a requirement around, like "NOT December".
- Groups make "this OR that" possible.
- Vanilla elements have **Loading Requirements** too. To remove one completely, see [Deleted Vanilla Elements](/deleted-vanilla-elements).

How to add requirements and combine them: [Requirements](/conditions#adding-a-requirement).

## Load Once Per Session

Right-click an element and turn on **Load Once Per Session**. The element shows the first time its screen opens. Once the player goes to another screen, it stays hidden until the game restarts.

Good for hints that should only show once per game start, like "Press F1 to see the controls". To use the same idea in action scripts, there's the [**Only Once Per Session**](/conditions#only-once-per-session-once_per_session) requirement.

# Delaying Elements

## Delay Appearance

Right-click an element and click **Delay Appearance**:

- **Delay**:
  - **No Delay**: shows right away.
  - **First Time**: waits only the first time the element shows after the game starts.
  - **Every Time**: waits every time the screen opens, and every time its requirements get met again.
- **Delay In Seconds**: how long it waits, like `1.5`.

Resizing the window doesn't start the delay again.

## Delay Disappearance

Right-click an element and click **Delay Disappearance**. When its requirements stop being met, the element stays for **Delay In Seconds** before it goes. **Delay** has the same choices as above.

For example, an info box with the requirement [**Is Element Hovered**](/conditions#is-element-hovered-fancymenu_visibility_requirement_is_element_hovered) for a button stays 1 second after the mouse left the button.

# Fading In and Out

Right-click an element and click **Fading In/Out**:

- **Fade-In** and **Fade-Out**:
  - **No Fading**: shows or hides right away.
  - **Only Once**: fades only the first time after the game starts.
  - **Every Time**: fades every time.
- **Fade-In Speed** and **Fade-Out Speed**: at `1`, a fade takes 2.5 seconds. `2` is twice as fast.

Elements fade in when the screen opens and when their requirements get met. With **Delay Appearance**, the fade starts after the delay.

Fade-Out only happens when requirements hide the element, not when the screen closes.

# Opacity

Right-click an element and click **Opacity**: `1.0` is fully visible, `0.5` half see-through, `0.0` invisible. Most elements have it.

Opacity supports [placeholders](/placeholders) and [variables](/variables), like `$$panel_opacity`. Fade-ins stop at the element's opacity.

# Toggling Elements With a Button

A button can show and hide elements, like the rules panel in the GIF above. A [variable](/variables) remembers if the panel is shown.

1. Right-click the panel and click **Loading Requirements**. Add [**Is Variable Value (FM Variable)**](/conditions#is-variable-value-fm-variable-fancymenu_visibility_requirement_is_variable_value) with the variable `show_rules` and the value `true`.
2. Right-click the button and click **Edit Action Script**.
3. Right-click the script area and click **Add IF Statement**. Give it the same requirement as the panel.
4. Add [**Set Variable Value (FM Variable)**](/action-scripts#set-variable-value-fm-variable-set_variable) inside the IF, with this value:

   ```
   show_rules:false
   ```

5. Right-click the IF and click **Append ELSE Statement**. Add **Set Variable Value (FM Variable)** inside the ELSE, with this value:

   ```
   show_rules:true
   ```

So every click flips the variable: shown panels get hidden, hidden panels get shown. All elements with the same requirement show and hide together. For a smooth look, set **Fade-In** and **Fade-Out** of the panel to **Every Time**.

More about IF and ELSE in [Action Scripts](/action-scripts#if-else-if-and-else).

> [!NOTE]
> Variables stay after the game closes, so the panel is still open at the next start. To close it on every start, right-click the variable in **Manage Variables** and turn on **Clear Variable on Game Launch**.

## Cycling Through Versions

A button can also switch between more than two versions, like three backgrounds:

1. In **menu bar -> Customization -> Manage Variables**, add the text variable `background` with the value `0`.
2. Give the three [Image elements](/elements#image) the requirement **Is Variable Value (FM Variable)** for `background`, with the values `0`, `1` and `2`.
3. Give the button **Set Variable Value (FM Variable)** with this value. It counts `0`, `1`, `2` and starts at `0` again:

   ```
   background:{"placeholder":"calc","values":{"decimal":"false","expression":"({"placeholder":"getvariable","values":{"name":"background"}} + 1) % 3"}}
   ```

For more versions, change the `3` at the end. See [**Calculator**](/placeholders#calculator-calc) for the math.

# Turning Layouts On and Off

To show or hide a whole layout:

- **Loading Requirements [Layout-Wide]** in the right-click menu of the editor background works like the requirements of elements. See [Layout-Wide Requirements](/conditions#layout-wide-requirements).
- The actions [**Toggle Layout**](/action-scripts#toggle-layout-toggle_layout), [**Enable Layout**](/action-scripts#enable-layout-enable_layout) and [**Disable Layout**](/action-scripts#disable-layout-disable_layout) turn a layout on and off by its name.

Put the button in another layout than the one it turns off. Otherwise the button goes away with it, and nothing can turn the layout back on.
