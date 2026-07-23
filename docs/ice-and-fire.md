---
title: Ice & Fire Main Menu
description: How to disable Ice and Fire's custom main menu.
published: true
date: 2025-04-14T20:15:02.802Z
tags: 
editor: markdown
dateCreated: 2025-04-14T20:14:59.763Z
---

# Ice & Fire Main Menu

To disable the custom title screen in the Ice and Fire mod you need to change its configuration. Here’s how you can do it:

## 1. Locate the Configuration File
- **File Name:** The setting is found in the file named **`iceandfire-client.toml`**.
- **Folder Location:** This file is usually located in **`<game-directory>/config/`**, where `<game-directory>` is the active launcher's instance/profile directory.

## 2. Edit the Config File
- **Open the File:** Use any plain text editor (such as Notepad on Windows or TextEdit on macOS) to open `iceandfire-client.toml`.
- **Find the Setting:** Scroll down until you find an option related to the custom main menu. It may be commented and look similar to this:
  ```toml
  # Whether to display the dragon on the main menu or not [default: true]
  B:"Custom main menu"=true
  ```
- **Change the Value:** Set this option to **false** by changing the line to:
  ```toml
  B:"Custom main menu"=false
  ```
  This change tells the mod not to render its custom main menu (often featuring the dragon or other thematic visuals).

## 3. Save and Restart
- **Save the File:** After making the change, save the file.
- **Restart Minecraft:** Close and restart Minecraft for the changes to take effect. When the game loads, it should now use the default main menu rather than the custom one from the mod.

## Additional Tips
- **Double-check You’re Editing the Correct File:** There might be a separate common configuration file, so make sure you’re editing **`iceandfire-client.toml`** (this is the client-specific configuration, not the common one).
- **Back Up First:** It’s always a good idea to make a backup of the original config file before you modify it.
- **Modpacks:** If you’re using a modpack, the config file might be inside the pack’s folder structure, but the principle remains the same.

Following these steps should disable the custom main menu provided by the mod so you can use your texture pack’s own main menu background.
