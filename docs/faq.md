---
title: FAQ
description: Frequently asked questions.
---
# FAQ

### I need help with an issue. What information should I provide?

To get the best help, please provide as much context as possible:
1.  **A clear description of the problem:** What did you expect to happen, and what actually happened?
2.  **Your `latest.log` file:** Find it at `<game-directory>/logs/latest.log`. **Do not send a crash log** unless specifically requested; `latest.log` usually contains the needed context. Use a site such as https://gist.github.com when posting it.
3.  **Your Minecraft Version:** (e.g., 1.20.1)
4.  **Your Mod Loader and Version:** (e.g., Forge 47.2.0, Fabric 0.15.7)
5.  **Your FancyMenu Version:** (e.g., 3.5.2)
6.  **Screenshots or videos** of the issue can also be very helpful.

> [!TIP]
> Asking Alice or another AI for help? Add an [Export for AI](/export-for-ai) of what doesn't work. It shows the AI exactly how it's set up, and it already has your Minecraft, mod loader and FancyMenu versions.

### How do I change the layering of elements (move something in front of or behind another)?

- **Your own elements:** drag their layers in the Layers widget of the layout editor, or right-click an element and click **Move One Layer Up** or **Move One Layer Down**. See [Layers and Groups](/layout-editor#layers-and-groups).
- **Your elements and vanilla elements:** the order of vanilla elements can't change. To put all your elements behind them, like a background image behind the default buttons, right-click the editor background and set **Custom Elements Behind Vanilla** to **Enabled**.

### Can I exclude certain buttons from a universal button template?

**No. If a template button has custom textures set, these textures are always shared with all affected elements. You cannot exclude individual buttons.**

### How do I make a button do something when clicked?

Use an [**Action Script**](/action-scripts).
1.  Right-click the button in the editor.
2.  Select **Edit Action Script**.
3. Click **Add Action** and choose an action, such as [**Open Screen or Custom GUI**](/action-scripts#open-screen-or-custom-gui), [**Join Server**](/action-scripts#join-server), or [**Set Variable Value**](/action-scripts#set-variable-value-fm-variable).

### Can I create a completely new menu screen from scratch?

Yes, with a [Custom GUI](/custom-guis):

1. Open **menu bar -> Customization -> Custom GUIs -> Manage Custom GUIs** and click **New GUI**.
2. Give it an identifier, like `modpack_info`, and click **Done**.
3. Open it with **Open GUI** and make a layout for it, like for any other menu.
4. Open it from a button with the action [**Open Screen or Custom GUI**](/action-scripts#open-screen-or-custom-gui) and its identifier.

### My game is taking a long time to load after enabling pre-loading.

This is expected behavior. Pre-loading large resources like high-resolution animations or sounds during the initial startup will naturally increase the game's loading time.

### My animation uses a lot of RAM or makes the game lag!

Big frames and high frame rates cost memory and performance. Make the frames about as big as they show up on screen, and use fewer frames per second. See [Animations](/animations#performance). For long clips with sound, use a [Video](/video) instead.

### Does FancyMenu work with OptiFine?

No. OptiFine is **not compatible** and is known to break many mods, including FancyMenu. It is highly recommended to use modern alternatives like Sodium/Embeddium + Iris/Oculus.
See [OptiFine Alternatives](/optifine-alternatives).

### My game is crashing. How do I figure out if it's a mod conflict?

The best way to check for a mod conflict is to **run the game with only FancyMenu and its dependencies** (Konkrete, Melody). If the crash no longer occurs, you can add your other mods back in small groups until the crash happens again to identify the conflicting mod.

### A button from another mod disappears or doesn't work when I try to edit it.

Some mods add widgets in ways FancyMenu cannot detect or customize. Check [Vanilla/Mod Elements](/vanilla-elements) and, for list-based screens, [Customizing Scrollable Screens](/customizing-scrollable-screens). If the widget still does not appear, the mod that adds it must expose it as a supported screen widget.

### Can I use FancyMenu layouts on a server?

Layouts and visual customizations are stored on the player's client; a server cannot force them onto an unconfigured client. Distribute them as part of a modpack. Install FancyMenu on the server when you need [server commands](/commands), [FM Data](/fm-data), [server-side NBT access](/nbt-data-placeholder#server-side-placeholder), gamerules, structures, or server listeners.

### What's the difference between FancyMenu v2 (for older MC versions) and v3?

FancyMenu v3 is a complete rewrite with many new features, a more stable architecture, and better performance. V2 is outdated, no longer supported, and missing many features like advanced placeholders and scripting. It is highly recommended to use v3 on a modern Minecraft version (1.18.2+). V2 layouts can be automatically converted to v3 when you load them, but some manual fixing may be required.

### Where can I find pre-made layouts and templates?

The FancyMenu community shares complete setups in the [`#layout-templates`](https://discord.com/channels/704163135787106365/1234093433795383316) channel of the official Discord server ("Kekscord"). Install them as their own profile, see [Layout Templates](/profiles#layout-templates).

### How can I make the Player Entity render behind other elements?

You generally cannot force a [Player Entity element](/elements#player-entity) behind normal 2D elements through the [Layers widget](/layout-editor#layers-and-groups). Its renderer can ignore normal GUI layer order. Design the layout around that limitation or use a pre-rendered image when strict layer ordering is required.

### My Player Entity has only one leg! What happened?

This is a visual glitch, likely caused by a mod conflict with another mod that alters player animations or models. Check the Player Entity's Pose settings to see if the legs have been rotated or moved by accident.

### How do I create a delay between actions in a script?

Right-click the script area of the action script editor, click **Add EXECUTE LATER Block** and put the actions that should wait inside it. They run once after its time in milliseconds, and the rest of the script runs on right away. See [Execute Later](/action-scripts#execute-later).

For things that should happen over and over, use [Schedulers](/schedulers).

### Can I customize menus from the Create mod?

No. Customization is intentionally disabled for Create screens. See [Screens where customization is intentionally disabled](/incompatibility-list#screens-where-customization-is-intentionally-disabled).

### What is the recommended resolution for background images and button textures?

Backgrounds: A standard 1920x1080 (1080p) image is a great starting point and will scale well for most users.
Buttons: Most vanilla buttons are around 150-200 pixels wide and 20 pixels high. Matching this size for custom textures is a good practice for consistency.

### Is there a way to automatically open a menu or run a command when a player completes an in-game objective (like a quest)?
FancyMenu has many [built-in game-event listeners](/listeners), but there is no generic listener for every third-party quest system. If the quest mod supports command rewards, use one to run [`/openguiscreen`](/commands#openguiscreen), [`/fmvariable`](/commands#fmvariable), or another suitable [FancyMenu command](/commands).

### How do I make a button inactive or "grayed out"?

You can control a button's active state using [requirements](/conditions).
Right-click the button in the editor and select **Control Active State**.
Add a requirement that must be met for the button to be active. To permanently disable it, use [**Is Number**](/conditions#is-number) to check whether 0 equals 1.
The button will now use its "Inactive Background" texture and will be unclickable.

### How can I remove the header and footer (the dirt texture bars) on scrollable screens?

In the layout editor, open **Layout Properties -> Header/Footer Customizations**. Set the textures to transparent. This option may be unavailable on some modded screens.

### I can't create a layout "for the current screen". The button is greyed out.

Turn on customizations for that screen first: click **menu bar -> Customization -> Current Screen Customization**, so it shows **Enabled**.

### I can't customize any elements of a screen when opening it in the editor. It's just an empty screen then.

This could mean you created a [Universal Layout](/universal-layouts) instead of one **for the current screen**.

It could also be a [scrollable screen](/customizing-scrollable-screens), which FancyMenu cannot customize by default.

The third possibility is that it's a screen from a mod that adds elements in a non-Vanilla way, which makes FancyMenu unable to customize these elements.

### There are weird grey boxes at my Text element.

These are the scroll bars of the [Text element](/elements#text). They show up when the text doesn't fit into the element, so players can scroll it.

- Make the element bigger or the text shorter, and they go away.
- Right-click the element and open **Scroll Bars**. **Show** sets when they show up: **Always**, only **While Scrolling**, or **Never**. With **Never**, the mouse wheel still scrolls.
- In the same menu, **Scroll Grabber Style**, **Scroll Grabber Textures** and **Scroll Grabber Color [HEX]** change how they look.

See [Text in Menus](/text-in-menus#scroll-bars) for all scroll bar settings.

### How can I show the latest Minecraft changelog in my menus?

There's a great [GitHub project](https://github.com/ClaytonTDM/minecraft-changelogs-markdown) that converts Minecraft's changelogs to FancyMenu-compatible Markdown, so you can show the latest MC changelog in your menus! It updates daily to fetch new changelogs.

To show it in a [Text element](/elements#text), set **Source Mode** to **Resource** and its resource source to **Web**. Use `https://clay.is-a.dev/minecraft-changelogs-markdown/{"placeholder":"mcversion"}/fancymenu.md`.

### What's the easiest way to stretch any element to the size of the screen?

Most elements have an option in their right-click context menus to stretch them horizontally and vertically. Enabling this will make them always stretch to the full width and/or height of the screen. Horizontal and vertical stretching can be toggled independently.

### I can't click buttons or interact with sliders when they are behind or in front of a Text element.

This happens because Text elements are interactable by default (to be able to grab the scroll grabber or click Markdown hyperlinks), which means they consume mouse clicks and scroll events. The best way would be to simply not move buttons behind/in front of Text elements, but if there is no way around it, you can make the Text element not interactable by **right-clicking it** and then setting **Interactable** to **Disabled**. Keep in mind this makes the Text element a static, non-interactable text, so you can't scroll it anymore or click on hyperlinks.

### How can I make it so buttons and sliders do not get selected/focused anymore when navigating in screens with the Arrow and Tab keyboard keys?

To make buttons and sliders not navigable, you need to **right-click** it and set **Navigable** to **Disabled**. The button/slider will still be clickable, but you can't focus it with Arrow/Tab navigation anymore.

This is also useful if you want to add buttons/sliders to the Chat screen, so you can still use the Arrow Up key to scroll through older messages without accidentally selecting buttons/sliders in the screen.

### One of FancyMenu's context menus is missing an option that should be there.

FancyMenu's context menus (the menus that open when you right-click somewhere or when you interact with menu bars) are SCROLLABLE. This means you can use your scroll wheel while your mouse cursor is over the menu to scroll up or down, which let's you see more options that were previously not visible.

### I can't customize the Title screen, it keeps showing the original when I leave the editor.

Another mod is replacing the original `title_screen`. Disable that mod's custom Title screen in its settings. If it has no such option, FancyMenu cannot apply the layout to the replacement screen.

### When I try to customize the inventory screen, I can't customize the inventory container.

That is expected. FancyMenu does not support editing the actual container of any kind of inventory screen (player inventory, chest, workbench, etc.), because adding support for these would be very difficult.

It is still possible to add new elements to these screens, you just can't edit the container(s).

SpiffyHUD will also not help here by the way, because it is for editing the HUD (so for example the item hotbar), but it can't edit screens (like inventory screens).
