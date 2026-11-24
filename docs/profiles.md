---
title: Profiles
description: How to save, switch, and share whole FancyMenu setups with profiles.
---
# Profiles

A profile is a complete FancyMenu setup: all layouts, assets, variables, and FancyMenu settings of an instance. Profiles let you keep multiple setups in one Minecraft instance, switch between them in seconds, and share them with others as a single file.

<img width="800" alt="profiles" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/profiles_showcase.gif?raw=true">

# Opening the Profiles Window

Open the Profiles window via **menu bar -> Customization -> Profiles**.

The list on the left shows all your profiles, and the right side shows the details of the selected one. The loaded profile is marked as **Active**. Every change you make in FancyMenu goes straight into the loaded profile.

Your existing setup automatically becomes your first profile, called **My Profile**.

> [!TIP]
> Right-click a profile in the list to see all actions for it.

# Switching Profiles

Select a profile and click **Load Profile**, or double-click it. FancyMenu then reloads with the selected setup.

> [!NOTE]
> Switching never deletes anything. Your current setup gets saved as its own profile before the other one loads, so you can always switch back.

# Creating Profiles

- **New Profile** (the **+** button below the list) creates an empty profile and opens its editor. Empty profiles keep your personal FancyMenu preferences, like the UI scale and theme.
- **Duplicate** creates a copy of the selected profile, which is handy for trying something out without touching the original.

# Editing Profiles

Click **Edit** to change the title, version, authors, description, icon, issue tracker, and links of a profile. The description supports Markdown, and the icon can be any PNG image.

Nothing gets saved until you click **Done**.

# Sharing Profiles

> [!CAUTION]
> Profiles can run actions. Import them only from sources you trust.

## Exporting

Select a profile, click **Export**, and choose where to save it. This creates a `.fmp` file that contains the whole profile.

## Importing

Click **Import** below the list and choose a `.fmp` file, or simply drag and drop the file onto the Profiles window.

- Imported profiles don't load automatically. Load them like any other profile.
- If you already have the same profile (like an older version of it), you can choose to **Replace** it or **Keep Both**. Replacing the loaded profile loads the imported version right away.
- Profiles made with a newer FancyMenu version show a warning, because some parts of them might not work.

## Adding Setup Folders

Some setups come as a plain `fancymenu` folder instead of a `.fmp` file. To add such a folder as a profile, rename it to the profile name you want, move it into `<game-directory>/config/fancymenu/profiles/` (create the `profiles` folder if it doesn't exist yet), and open the Profiles window. FancyMenu adds it to your profiles automatically.

# Deleting Profiles

Select a profile and click **Delete**. Deleting can't be undone, so export the profile first if you want to keep a backup.

The loaded profile can't be deleted. Load another profile first.

# Where Profiles Are Stored

- The loaded profile is the content of `<game-directory>/config/fancymenu/`, like any FancyMenu setup.
- All other profiles are stored in `<game-directory>/config/fancymenu/profiles/`. Click **Open Folder** to open the folder of a profile.

`<game-directory>` is the active instance folder, which may differ from `.minecraft`. The data in `<game-directory>/fancymenu_data/` is not part of profiles, see [Data Storage Locations](/data-storage-locations#instance-data).
