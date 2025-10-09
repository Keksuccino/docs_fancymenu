---
title: FAQ
description: Frequently asked questions.
published: true
date: 2025-09-05T10:54:17.927Z
tags: 
editor: markdown
dateCreated: 2025-08-04T19:44:22.004Z
---

# FAQ

### I need help with an issue. What information should I provide?
To get the best help, please provide as much context as possible:
1.  **A clear description of the problem:** What did you expect to happen, and what actually happened?
2.  **Your `latest.log` file:** This is the most important file for troubleshooting. Find it in your instance's `/logs/` folder. **Do not send a crash log** unless specifically asked; the `latest.log` is much more useful. Use a site like https://gist.github.com to share it.
3.  **Your Minecraft Version:** (e.g., 1.20.1)
4.  **Your Mod Loader and Version:** (e.g., Forge 47.2.0, Fabric 0.15.7)
5.  **Your FancyMenu Version:** (e.g., 3.5.2)
6.  **Screenshots or videos** of the issue can also be very helpful.

### How do I change the layering of elements (move something in front of or behind another)?
*   **Custom vs. Custom:** To change the render order of your own custom elements, use the **Layers widget**. You can open it via the menu bar: **Window -> Widgets -> Layers**. From there, you can drag elements up or down in the hierarchy. You can also right-click an element and use "Move One Layer Up/Down".
*   **Custom vs. Vanilla:** To render all your custom elements behind all vanilla elements (e.g., to put a background image behind the default buttons), **right-click the editor background** and toggle the option **"Render Custom Elements Behind Vanilla"**.

### Can I exclude certain buttons from a universal button template?
**No. If a template button has custom textures set, these textures are always shared with all affected elements. You cannot exclude individual buttons.**

### How do I make a button do something when clicked?
Use an **Action Script**.
1.  Right-click the button in the editor.
2.  Select **Edit Action Script**.
3.  Click **Add Action** and choose from the list (e.g., `Open Screen or Custom GUI`, `Join Server`, `Set Variable Value`).
*   More info: [Action Scripts](https://docs.fancymenu.net/en/action-scripts)

### Can I create a completely new menu screen from scratch?
Yes, this is done using **Custom GUIs**.
1.  In the menu bar, go to **Customization -> Custom GUIs -> Manage Custom GUIs**.
2.  Click **"New GUI"** and give it a unique identifier.
3.  You can then open this new empty screen and create a layout for it, adding any elements you want.
4.  This Custom GUI can then be opened via a button action.
*   More info: [Custom GUIs](https://docs.fancymenu.net/en/custom-guis)

### My game is taking a long time to load after enabling pre-loading.
This is expected behavior. Pre-loading large resources like high-resolution animations or sounds during the initial startup will naturally increase the game's loading time.

### My FMA animation is using too much RAM!
FMA files are uncompressed animations and can consume a lot of memory. The recommended limits are a maximum of **200 frames** at a resolution of **1080p**. Using more frames or a higher resolution will significantly increase RAM usage. Animations are meant for short, decorative loops, not for playing full videos.

### Does FancyMenu work with OptiFine?
No. OptiFine is **not compatible** and is known to break many mods, including FancyMenu. It is highly recommended to use modern alternatives like Sodium/Embeddium + Iris/Oculus.
*   More info: [OptiFine Alternatives](https://docs.fancymenu.net/en/optifine-alternatives)

### My game is crashing. How do I figure out if it's a mod conflict?
The best way to check for a mod conflict is to **run the game with only FancyMenu and its dependencies** (Konkrete, Melody). If the crash no longer occurs, you can add your other mods back in small groups until the crash happens again to identify the conflicting mod.

### A button from another mod disappears or doesn't work when I try to edit it.
This usually means the other mod adds its buttons in a non-standard way that FancyMenu cannot interact with. This is an issue that the other mod's developer would need to fix on their end. FancyMenu cannot customize elements it cannot "see".

### Is there a way to open a file or folder on my computer with a button?
Yes, but this requires the **System Interactions Addon** for FancyMenu, which is a separate download. This addon may not be up-to-date with the latest Minecraft versions.

### Can I use FancyMenu layouts on a server?
FancyMenu is a client-side mod. All layouts and customizations are on the player's client. You cannot put layouts on a server to force players to see them. However, you can distribute your `config/fancymenu` folder as part of a modpack. If you want to use commands like `/fmvariable` or `/openguiscreen` from the server, then FancyMenu (or its Spigot plugin) must be installed on the server.

### What's the difference between FancyMenu v2 (for older MC versions) and v3?
FancyMenu v3 is a complete rewrite with many new features, a more stable architecture, and better performance. V2 is outdated, no longer supported, and missing many features like advanced placeholders and scripting. It is highly recommended to use v3 on a modern Minecraft version (1.18.2+). V2 layouts can be automatically converted to v3 when you load them, but some manual fixing may be required.

### Where can I find pre-made layouts and templates?
The FancyMenu community shares layouts in the `#layout-templates` channel on the official Keksuccino's Mods Discord server.

### How can I make the Player Entity render behind other elements?
You can't. Due to how Minecraft renders entities, the Player Entity element will almost always render in front of other 2D elements, regardless of the layer settings.

### My Player Entity has only one leg! What happened?
This is a visual glitch, likely caused by a mod conflict with another mod that alters player animations or models. Check the Player Entity's Pose settings to see if the legs have been rotated or moved by accident.

### How do I create a delay between actions in a script?
You cannot add a "wait" or "sleep" action, as this would freeze the game. To create a delay, you must use a Ticker element to count up a variable. For example, have a Ticker increase a timer variable by 1 every tick. Then, use an IF statement to check if timer has reached your desired value (e.g., 20 for a 1-second delay if the ticker runs every 50ms) before executing the next action.

### Can I customize menus from the Create mod?
No. FancyMenu has known incompatibilities with Create's complex GUIs. Customization for Create screens has been intentionally disabled to prevent crashes.

### Why do buttons from mod X disappear in the editor?
This means the mod adds its buttons in a custom, non-vanilla way. FancyMenu cannot "see" or interact with these elements, so it cannot customize them. The developer of the other mod would need to change how they add their buttons for them to be compatible.

### What is the recommended resolution for background images and button textures?
Backgrounds: A standard 1920x1080 (1080p) image is a great starting point and will scale well for most users.
Buttons: Most vanilla buttons are around 150-200 pixels wide and 20 pixels high. Matching this size for custom textures is a good practice for consistency.

### Is there a way to automatically open a menu or run a command when a player completes an in-game objective (like a quest)?
FancyMenu itself cannot detect in-game events like this. However, you can integrate it with a questing mod like FTB Quests. Most quest mods allow you to run a command as a quest reward. You would set the reward to execute the `/openguiscreen` or `/fmvariable` command to interact with your menus.

### How do I make a button inactive or "grayed out"?
You can control a button's active state using Loading Requirements.
Right-click the button in the editor and select "Active State".
Add a requirement that must be met for the button to be active. For example, to permanently disable a button, you could add an Is Number requirement that checks if 0 equals 1 (which is always false).
The button will now use its "Inactive Background" texture and will be unclickable.

### How can I remove the header and footer (the dirt texture bars) on scrollable screens?
In FancyMenu v3, you can customize these. In the layout editor, right-click the editor background and look for options like "Customize Header/Footer". You can set their textures to be fully transparent to effectively remove them visually. Note that this may not work on all screens, especially older or heavily modded ones.

### I can't create a layout "for the current screen". The button is greyed out.
You need to enabled customizations for that screen first via **menu bar -> Customization -> Current Screen Customizations -> toggle it to Enabled**.

### I can't customize any elements of a screen when opening it in the editor. It's just an empty screen then.

This could mean you accidentally created a universal layout instead of one **for the current screen**.

It could also mean that the screen you are customizing is a scrollable screen, which are screens that FancyMenu can't customize by default.

The third possibility is that it's a screen from a mod that adds elements in a non-Vanilla way, which makes FancyMenu unable to customize these elements.

### There are weird grey boxes at my Text element.

These translucent (low opacity) boxes/rectangles can be at the right or bottom edge of your Text element and they are not a bug. These are the scroll grabbers of the Text element, since the element is scrollable.

If you don't want these boxes to be visible, you can either right-click the element and disable scrolling completely OR you can also set the grabber textures to completely transparent ones in the same right-click menu, if you want the element to be still scrollable.