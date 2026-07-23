---
title: Button & Slider Templates
description: >-
  How to use button/slider templates to apply a specific button/slider design to
  ALL buttons at once.
---

# Using Button Elements as Templates for Buttons and Sliders

It is possible to use a Button element as a template for other buttons and even sliders. By doing that, you can apply a specific button/slider design to ALL buttons/sliders in a menu or even the all menus at once when using a universal layout.

> [!IMPORTANT]
> Prefer [Global Customizations](./global-customizations) for broad Vanilla button and slider styling. Use Button/Slider Templates when the behavior must be layout-specific.

# Important Before You Start

For one button or slider, **right-click** it in the editor and edit its **Background Textures** or slider-handle textures directly.

# What is a Template Button?

A template button is a special kind of custom button in FancyMenu that lets you control how other buttons and sliders look and behave. It's like creating a master design that many other elements will follow.

When you create a template button, you can make many buttons or sliders share the same:
- Size (width and height)
- Position
- Visibility
- Opacity (how see-through they are)
- Text labels
- **Button textures** (automatically shared when custom textures are set)

This is super helpful when you want to make your menu look consistent or when you need to update many buttons at once!

# Who Can Use Templates?

Only **custom buttons** can work as templates. However, these templates can be applied to:
- Vanilla buttons (the default Minecraft buttons)
- Custom buttons (buttons you create in FancyMenu)
- Vanilla sliders (like volume controls)
- Custom sliders (sliders you create in FancyMenu)

# How to Create a Template Button

1. Open the FancyMenu editor for the screen you want to customize
2. Add a new custom button element to your layout
3. Right-click on your new button
4. Select "Template Settings" from the menu
5. Click "Is Template: ON" to enable template mode

Your button will now be ready to work as a template for other buttons and sliders!

# Template Sharing Options

You can choose which types of elements your template will affect:
- **Buttons** - Your template will only affect buttons (both vanilla and custom)
- **Sliders** - Your template will only affect sliders (both vanilla and custom)

To set this option:
1. Right-click your template button
2. Go to "Template Settings"
3. Click on "Share With: [Current Option]" to cycle between options

> **Important**: You can have two templates active at the same time - one for buttons AND one for sliders. This means you can create separate template designs for different element types on the same screen!
{.is-warning}


# What Can Be Templated

You can control exactly which properties your template will share with other elements:

## Properties That Can Be Toggled On/Off:

1. Right-click your template button
2. Go to "Template Settings" 
3. Toggle any of these options:
   - **Width** - Makes all affected elements the same width as your template
   - **Height** - Makes all affected elements the same height as your template
   - **X Position** - Places all affected elements at the same X coordinate as your template
   - **Y Position** - Places all affected elements at the same Y coordinate as your template
   - **Opacity** - Gives all affected elements the same transparency as your template
   - **Visibility** - Controls whether affected elements are shown or hidden
   - **Label** - Makes all affected elements use the same text as your template

## Properties That Are Always Shared:

- **Button textures** - When you set custom textures on your template, they will automatically be applied to all affected elements
  - Unlike other properties, texture sharing cannot be turned off
  - Textures are only applied when custom textures are actually set on the template
  - If no custom textures are set, the original element textures will be used

# Customizing the Template Appearance

Your template button can be customized just like any other button:

1. Right-click on your template button
2. You can set:
   - Button textures (normal, hover, and inactive states)
   - Labels (normal and hover)
   - Sounds (hover and click)
   - Tooltips

For buttons, you can set custom textures for different states:
- Normal background (when not interacting)
- Hover background (when your mouse is over it)
- Inactive background (when the button is disabled)

For sliders, you can also set:
- Slider handle textures
- Slider background textures

# Important Tips

1. **Template buttons won't appear in the game** - They're only visible in the editor, so place them wherever is convenient.

2. **You can have two templates active simultaneously** - One template for buttons and one template for sliders can be active at the same time.

3. **Only one template per type is active** - If you have multiple button templates, only the top one in your element list will be used for buttons. The same applies to slider templates.

4. **Changes to the template update instantly** - When you edit your template, all affected buttons and sliders will update right away.

5. **Use the right sharing mode** - Remember that "Buttons" mode won't affect sliders, and "Sliders" mode won't affect buttons.

6. **Apply properties selectively** - You don't have to apply all properties. For example, you might want to template just the textures and size but allow elements to keep their original positions.

7. **Textures are always shared when set** - Unlike other properties, any custom textures you apply to the template will automatically be shared with matching elements. You don't need to toggle this feature on/off.

# Example Uses

- Create a consistent style for all buttons on a screen
- Make all sliders match your custom theme with a separate template
- Create a "hidden mode" where you can show/hide multiple buttons at once
- Change the size of many buttons with just one edit
- Give all buttons in your menu the same custom textures and sounds
