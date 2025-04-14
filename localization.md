---
title: Localizing Layouts
description: How to localize layout content.
published: true
date: 2025-04-14T20:15:19.588Z
tags: 
editor: markdown
dateCreated: 2025-04-14T20:15:16.589Z
---

# Localizing Layouts

FancyMenu lets you localize text content and even whole elements or layouts!

# Text Content

FancyMenu allows you to add your own localizations to the game.
These can then be used with the **Localize Text** placeholder to localize text to the current game language.

> The following documentation focuses on how to load custom localizations, but instead of using custom ones, you can also use **Minecraft's Vanilla localization keys** or **keys of other loaded mods**.
{.is-info}

## Custom Localization Files

Localization files are text files with all the text content that should be available in multiple languages. Each translatable text has a unique key, so Minecraft can find the correct translatable text in the localization files.

- **Default File (en_us.json):**  
  English (US). This file is used when no other language file is chosen. It acts as the backup language file.

- **Other Language Files:**  
  For example, you can create a German file called `de_de.json` for players who use German.

### How to Create a Custom Localization File

You always need an `en_us.json` file! Without it, the game has no fallback when stuff goes wrong or an unsupported language is set.

1. **Open a Text Editor:**  
   Use Notepad (Windows), TextEdit (Mac), or any simple text editor.

2. **Write Your JSON Code:**  
   Create your file with your custom keys. A key is a unique name that Minecraft uses to find the text. For example:
   
   ```json
   {
     "modpack_name.custom.localization.key": "Your custom text here",
     "modpack_name.another.key": "Another message"
   }
   ```

3. **Save the File:**  
   Save the file as `en_us.json` for the default English text.

If you now want to add translated versions, like German, copy the content from the `en_us.json` file to the new file and only translate the actual text, NOT the keys! Keys need to stay the same, so the game can still find the text.

For German, you would then save the file as `de_de.json`. For other languages, please check [this Minecraft wiki page](https://minecraft.wiki/w/Language) for the correct language code for your language and name the file after it. Search for the **"in-game locale code"** for your language.

## Creating a Minecraft Resource Pack for MC 1.21.4

Now that your localization files are ready, we need a way to load them in Minecraft. For that, we will use a resource pack. We will make the pack to be enabled by default and we can even hide it if we don't want modpack users to mess with it.

A **resource pack** is a ZIP file that holds files that change the game’s look and feel.

### Steps to Create Your Resource Pack

1. **Make a New Folder:**  
   Create a folder named something like `my_custom_pack` where you will add your custom localization files.

2. **Create the Pack File (`pack.mcmeta`):**  
   Inside your folder, create a file called `pack.mcmeta` with the following content:
   
   ```json
   {
     "pack": {
       "pack_format": 16,
       "description": "My Custom Pack with Localizations"
     }
   }
   ```
   
   *Note: `pack_format` 16 is for Minecraft 1.21.4.*

3. **Add Your Localization Files:**  
   Inside your resource pack folder, create the following folder structure:
   
   ```
   my_custom_pack/
   ├── assets/
   │   └── minecraft/
   │       └── lang/
   │           ├── en_us.json
   │           └── de_de.json
   └── pack.mcmeta
   ```
   
   Place your custom `en_us.json` (and any other language files like `de_de.json`) in the `lang` folder.

4. **ZIP the Resource Pack:**  
   Once your folder is ready, **compress the entire folder into a ZIP file**. Name the ZIP file **my_custom_pack.zip**. This is the example name used throughout the guide.

## Where to Place the Resource Pack

Place your **my_custom_pack.zip** file in the **Minecraft Resourcepacks folder**. This folder is usually located at:

- **Windows:** `%appdata%\.minecraft\resourcepacks`
- **Mac:** `~/Library/Application Support/minecraft/resourcepacks`
- **Linux:** `~/.minecraft/resourcepacks`

> For modpacks, the `resourcepacks` folder is in your pack's instance directory.
{.is-warning}

## Auto-Loading the Pack with "Resource Pack Overrides"

The **Resource Pack Overrides** mod makes it possible enable resource packs by default.

### Steps to Auto-Load Your Pack

1. **Install the Mod:**  
   Download and install the mod from [CurseForge](https://www.curseforge.com/minecraft/mc-mods/resource-pack-overrides) or [Modrinth](https://modrinth.com/mod/resource-pack-overrides).

2. **Locate the Config File:**  
   Find the file at `.minecraft/config/resourcepackoverrides.json`.  
   *If the file does not exist, create it manually.*

3. **Edit the Config File:**  
   Open the file and add your resource pack to the `default_packs` list using its file name:
   
   ```json
   {
     "schema_version": 2,
     "default_packs": [
       "file/my_custom_pack.zip"
     ]
   }
   ```
   
   This tells Minecraft to load your resource pack automatically when you start the game.

   **It's important to add the `file/` prefix!**


*Note: The resource packs in the list are applied in reverse order. That means the pack at the top of the list will appear below the others in the game’s resource pack menu.*

## Hiding the Resource Pack in the Selection Screen

You can hide your resource pack so players do not see it in the resource pack selection screen.

### How to Hide It

1. **Edit the Config File Again:**  
   In the same file `.minecraft/config/resourcepackoverrides.json`, add an override for your pack:
   
   ```json
   {
     "schema_version": 2,
     "default_packs": [
       "file/my_custom_pack.zip"
     ],
     "pack_overrides": {
       "file/my_custom_pack.zip": {
         "hidden": true
       }
     }
   }
   ```
   
   This configuration will hide **my_custom_pack.zip** from the selection screen while still loading it automatically.

## Using Your New Localization Keys with FancyMenu

Now that your custom localization files are loaded, you can use your new keys in FancyMenu layouts.

1. **Edit a Text-Based Element:**  
   Open FancyMenu and choose an element like a Button or Text element.

2. **Click on the Placeholders Button:**  
   Look for the Placeholders button at the top-right of the text editor. (If you don’t see it, the element might not support placeholders.)

3. **Insert the Localize Text Placeholder:**  
   The Localize Text placeholder appears as a JSON snippet. It looks like this:
   
   ```json
   {"placeholder":"local","values":{"key":"localization.key"}}
   ```
   
   Replace `localization.key` with your own custom key. For example, if you want to use your key from the localization file, change it to:
   
   ```json
   {"placeholder":"local","values":{"key":"modpack_name.custom.localization.key"}}
   ```

Well, and that's basically it! The placeholder should get replaced with the actual localized content when not editing it in the text editor.

Keep in mind that the placeholder will always localize the text content to the current game language.

# Non-Text Content (Images, etc.)

FancyMenu also allows you to localize images and basically every element you want.

To do this, you will need to use **loading requirements**.
The **Is Game Language** requirement to be more specific.

The **Is Game Language** requirement allows you to show elements or layouts only if a specific game language is set, so you can, for example, make two Image elements that contains text and localize that image to a version with Japanese text when the language is set to Japanese or a version with English text, if the language is set to English.

To set loading requirements to an **element**, right-click it and click on **Loading Requirements**.

To set loading requirements to **whole layouts**, right-click the layout editor background and click on **Loading Requirements [Layout-Wide]**.