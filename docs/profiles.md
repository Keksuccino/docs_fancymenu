---
title: Profiles
description: Save, switch and share whole FancyMenu setups with profiles, and install layout templates of the community.
---

# Profiles

A profile is a complete FancyMenu setup: layouts, assets, variables, settings and everything else in `config/fancymenu/` (see [Data Storage Locations](/data-storage-locations#your-setup)). With profiles, you keep several setups in one Minecraft instance, switch between them in seconds and share them as a single file.

<img width="800" alt="Making the profile My Menu Pack, importing the profile Wind Chimes by dropping its .fmp file onto the Profiles window, deleting My Menu Pack and loading Wind Chimes, which changes the title screen" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/profiles_showcase.gif?raw=true">

# The Profiles Window

Open it with **menu bar -> Customization -> Profiles**.

- The list on the left shows all profiles. The loaded one comes first and is marked **Active**. Every change you make in FancyMenu goes straight into it.
- The right side shows the selected profile: its icon, title, version, authors, number of layouts, size, links and description.
- The buttons below the list and the details show their name when you hover them. A right-click on a profile shows its actions too.

Your setup becomes your first profile on its own, called **My Profile**.

# Loading a Profile

Select a profile and click **Load Profile**, double-click it or press `Enter`.

FancyMenu then reloads with the profile, like after a game start. All other FancyMenu windows close, and outside of a world, the title screen opens.

> [!NOTE]
> Loading never deletes anything. Your current setup gets saved as its own profile first, so you can always switch back.

# Making Profiles

- **New Profile** (the `+` button below the list) makes an empty profile and opens its details right away, so you can name it. It keeps your FancyMenu preferences, like the UI scale and theme, but has no layouts or other customizations. It doesn't get loaded on its own.
- **Duplicate** copies the selected profile, which is handy to try something out without touching the original.

# Editing Profile Details

Select a profile and click **Edit** to change its details:

- **Title**, the only thing a profile needs.
- **Version** and **Authors**. Separate several authors with commas.
- **Description**, with [Markdown](/text-formatting#markdown) like bold text, headlines and lists.
- **Issue Tracker**, a website where people can report problems with the profile. It shows up as **Report an Issue**.
- **Links** to your Discord server, YouTube channel, website and more. Click **Add Link** and paste the link: FancyMenu picks its platform on its own.
- An icon: **Choose Icon** takes a PNG image, and **Remove Icon** removes it. Images that aren't square get cropped to their center.

Nothing gets saved until you click **Done**.

# Sharing Profiles

> [!CAUTION]
> Profiles can run actions, like opening links or running commands. Import them only from sources you trust.

## Exporting

Select a profile, click **Export** and choose where to save it. This makes a `.fmp` file with the whole profile, ready to share.

## Importing

Click **Import** below the list and choose a `.fmp` file, or drag and drop the file onto the Profiles window.

- Imported profiles don't get loaded on their own. Load them like any other profile.
- If you already have the profile, like an older version of it, choose **Replace** or **Keep Both**. Replacing the loaded profile loads the imported one right away, and your changes to the old one are gone.
- Profiles made with a newer FancyMenu version show a warning first, because some parts of them might not work.
- Only `.fmp` files exported by FancyMenu work. For a plain folder, see the next section.

## Adding Setup Folders

Some setups come as a plain `fancymenu` folder (a copy of someone's `config/fancymenu/`) instead of a `.fmp` file. To add one as a profile:

1. Unzip it, if it comes as `.zip` file.
2. Move the folder into `<game-directory>/config/fancymenu/profiles/`. Make the `profiles` folder if it's not there yet.
3. Open the Profiles window, or close and open it again. FancyMenu adds the folder to your profiles.

The folder has to hold the files directly, like `customization/` and `options.txt`, not another `fancymenu` folder. The profile gets the folder's name as title, unless the folder brings its own profile details. Change it with **Edit**.

## Layout Templates

The [`#layout-templates`](https://discord.com/channels/704163135787106365/1234093433795383316) channel of the [Kekscord Discord server](https://discord.gg/rhayah27GC) (Keksuccino's official Discord server for mod support) has complete setups made by the community, for FancyMenu and its addons, like SpiffyHUD and Drippy Loading Screen. Every post has a download link, either to a `.fmp` file or to a `fancymenu` folder.

Templates are complex, so don't try to merge one with your own setup. Add it as its own profile instead:

1. [Import](#importing) the `.fmp` file, or [add the folder](#adding-setup-folders).
2. Select the template in the Profiles window and click **Load Profile**.

Your own setup stays available as its own profile, so you can always switch back.

Most templates allow you to edit them and to use them in your own projects, like modpacks, but not all of them. Always check the template's post for what you're allowed to do with it.

# Deleting Profiles

Select a profile and click **Delete**, or press `Delete` (`Fn + Delete` on macOS). Deleting can't be undone, so export the profile first if you want a backup.

The loaded profile can't be deleted. Load another profile first.

# Where Profiles Are Stored

- The loaded profile is the content of `<game-directory>/config/fancymenu/`.
- All other profiles are in `<game-directory>/config/fancymenu/profiles/`, one folder each. **Open Folder** opens the folder of the selected profile.

`<game-directory>` is the folder of your instance, which can be a different one than `.minecraft`. The data in `<game-directory>/fancymenu_data/` isn't part of profiles, see [Data Storage Locations](/data-storage-locations#instance-data).

# When Something Goes Wrong

- **Some of its files are still in use:** often the game itself is still loading something, like audio. Wait a few seconds and try again. If it keeps happening, close programs that could use the files, like your antivirus, cloud sync or a file explorer window.
- **The last profile switch isn't done yet:** nothing got lost. Load a profile again or restart the game to finish the switch.
- **There's not enough free disk space:** the message says how much space the profile needs. Free up some space and try again.
- Profile actions run one at a time. Exporting, importing and duplicating big profiles can take a moment, so these show a **Cancel** button while they run.
