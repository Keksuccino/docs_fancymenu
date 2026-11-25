---
title: Custom GUIs
description: Make your own menus from scratch, open them with buttons, keys or commands, show them as popups, and replace other menus with them.
---

# Custom GUIs

Custom GUIs are menus you make yourself, like a modpack info screen, a server hub or a rules page. They start empty, and you fill them with a [layout](/layout-editor) like any other menu. Then buttons, keys and commands open them.

<img width="800" alt="Clicking a Modpack Info button on the title screen opens a Custom GUI as a popup over the blurred title screen, and its Back button closes it again" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/custom_guis_popup.gif?raw=true">

# Making a Custom GUI

<img width="800" alt="Opening Manage Custom GUIs, clicking New GUI, typing the identifier modpack_info, turning on Popup Mode and opening the new Custom GUI" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/custom_guis_new.gif?raw=true">

1. Open **menu bar -> Customization -> Custom GUIs -> Manage Custom GUIs**.
2. Click **New GUI**.
3. Type a **Custom GUI Identifier**, like `modpack_info`, set up the [settings](#settings) and click **Done**.
4. Click the new Custom GUI in the list and click **Open GUI**.
5. Click **Done** to close **Manage Custom GUIs**.

**Manage Custom GUIs** only saves your changes when you click **Done** or **Open GUI**. **Cancel** throws them away.

## The Identifier

Buttons, commands and layouts find a Custom GUI by its identifier.

- Only lowercase letters, numbers, `.`, `_` and `-`. Every Custom GUI needs its own.
- Don't use the [identifier of another screen](/screen-identifiers), like `title_screen`. The Custom GUI would share its layouts with that screen.
- If you change the identifier later, its layouts, and buttons and commands with the old identifier, don't find it anymore. Changing it back brings them back.

## Building Its Layout

1. Open the Custom GUI.
2. Click **menu bar -> Customization -> Layouts -> New -> For Current Screen**. Customization is always on for Custom GUIs.
3. Add elements and save the layout. See [Layout Editor](/layout-editor).

A Custom GUI has nothing in it, not even a Back button. Give it a [Button](/elements#button) with the action [**Back to Last Screen**](/action-scripts#back-to-last-screen), or leave **Allow ESC to Close GUI** on, so players can leave it.

# Settings

**Edit GUI** in **Manage Custom GUIs** changes the settings of the selected Custom GUI.

| Setting | What it does |
|---|---|
| **Custom GUI Identifier** | The name of the Custom GUI. See [The Identifier](#the-identifier). |
| **Screen Title (Optional)** | A white title at the top of the GUI. Leave it empty for none. [Placeholders](/placeholders) work, and localization keys of the game, mods and resource packs show in the player's language. |
| **Allow ESC to Close GUI** | `Esc` closes the GUI. On by default. |
| **Pause Game/World** | Pauses singleplayer worlds while the GUI is open. On by default. |
| **Render World Background** | Shows the world behind the GUI while you play. Outside of worlds, or when it's off, the Minecraft panorama shows. On by default. |
| **Render World Background Overlay** | Blurs and darkens the world or panorama behind the GUI, like the pause menu does. Only works with **Render World Background**: without it, the panorama is always blurred and darker. On by default. |
| **Popup Mode** | Shows the GUI on top of the menu it got opened from. See [Popup Mode](#popup-mode). |
| **Popup Mode Background Overlay** | Blurs the menu behind the popup. Only works with **Popup Mode**. On by default. |

- The blur is as strong as Minecraft's **Menu Background Blur** option.
- A [menu background](/menu-backgrounds) in the layout covers all of this: the world, the panorama and the menu behind a popup.
- The layout editor can't change the title (**Custom Screen Title**) of Custom GUIs. Change **Screen Title (Optional)** instead. For a title with its own font, color or spot, leave it empty and add a [Text element](/elements#text).

## Popup Mode

With **Popup Mode**, the menu the Custom GUI got opened from stays visible behind it, with its layout. It can't be clicked while the popup is open.

- Popups work best for small things like an info box, a confirmation or a settings panel. Leave some space free, so the menu behind shows.
- Don't give the layout of a popup a menu background, or the menu behind disappears.
- When the Custom GUI gets opened while no menu is open, like with a key while playing, there's no menu to show behind it. Then it shows its normal background.

# Opening a Custom GUI

Everything that opens screens can open Custom GUIs, with their identifier:

- **Buttons:** the action [**Open Screen or Custom GUI**](/action-scripts#open-screen-or-custom-gui) with the value `modpack_info`.
- **Keys:** an [**On Keyboard Key Pressed** listener](/listeners#listener-variables) with the same action. It opens the Custom GUI in menus and while playing.
- **Commands:** `/openguiscreen modpack_info`, also from servers, command blocks and quest rewards. See [Commands](/commands#openguiscreen).
- **Leaving a world:** the action [**Leave World or Server**](/action-scripts#leave-world-or-server) with the identifier opens the Custom GUI after leaving.

Custom GUIs are part of each player's own FancyMenu setup. A server can only open the Custom GUIs that its players have, like the ones of the modpack.

To leave a Custom GUI:

- `Esc` (with **Allow ESC to Close GUI**) and the action **Back to Last Screen** go back to the menu it got opened from. When no menu was open, `Esc` goes back to the game.
- The action [**Close Screen**](/action-scripts#close-screen) closes it. Outside of worlds, the title screen opens.

# Overriding an Existing Screen

A Custom GUI can replace a menu of the game or a mod. Every time that menu would open, the Custom GUI opens instead.

> [!WARNING]
> The replaced menu never opens, so nothing it does happens, and other mods that need it can break. Change menus with a normal layout whenever you can. Only replace a menu when a layout can't do what you need.

1. Turn on **menu bar -> Customization -> Settings -> Advanced Customization Mode**.
2. Open the menu you want to replace.
3. Click **menu bar -> Customization -> Custom GUIs -> Override Current with Custom GUI**.
4. Confirm the warning and pick the Custom GUI in **Choose Custom GUI**.

The Custom GUI opens right away. `Esc` and **Back to Last Screen** in it go back to the menu that was open before the replaced one.

To undo it, open **menu bar -> Customization -> Custom GUIs -> Manage Overridden Screens**, click **Delete Override Rule** below the screen and click **Done**.

> [!TIP]
> To replace a menu only in some cases, like only while a [variable](/variables) is set, use an [**On Screen Opened** listener](/listeners#on-screen-opened) with an IF statement instead.

# Managing Custom GUIs

- **New GUI**, **Edit GUI** and **Open GUI** in **Manage Custom GUIs** add, change and open Custom GUIs.
- **Delete GUI** deletes the selected Custom GUI, after asking you. Its layouts stay, and show again in a new Custom GUI with the same identifier.
- The search bar finds Custom GUIs by their identifier.
- **menu bar -> Help -> Export for AI -> Custom GUIs** exports all Custom GUIs and override rules for an [AI chat](/export-for-ai).

Custom GUIs and override rules get saved in `config/fancymenu/custom_gui_screens.txt`, their layouts in `config/fancymenu/customization/` like all others (see [Data Storage Locations](/data-storage-locations)). Every [profile](/profiles) has its own Custom GUIs.
