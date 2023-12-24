---
title: Localizing Layouts
description: How to localize layout content.
published: true
date: 2023-12-24T07:59:54.994Z
tags: 
editor: markdown
dateCreated: 2023-12-24T07:59:54.994Z
---

# Localizing Layouts

FancyMenu lets you localize text content and even images and other element types.

# Text Content

FancyMenu allows you to add your own localizations to the game.
These can then be used in the **Localize Text** placeholder to localize a text to the current game language.

The following documentation focuses on how to load localizations via FancyMenu's own localization system, but instead of using FancyMenu's system, you can also use **Minecraft's localization system** and load your localizations via resource pack or a resource loader mod.

The **Localize Text** placeholder works with keys from both FancyMenu's and Minecraft's localization systems.

## Adding Localizations via FancyMenu
<br>

### Localization Directory

To add your own localization files, you first need to create a localization directory in `.minecraft/config/fancymenu/custom_locals/`.
This directory should have a unique name, like your username.

In this case, I will name the directory `keksuccino`.
So now I have my localization directory in `.minecraft/config/fancymenu/custom_locals/keksuccino`.

![](https://user-images.githubusercontent.com/35544624/134380681-59f9bd02-aefd-4b67-9ee4-ca7568d23935.png)

This is the directory where you will put all your localization files.

### The First Localization File

Localization files contain all of your localized text content for different languages.
There's always one localization file per language.

This means that you put the same text content in multiple files, but in different languages.

To make the game being able to find the same localized content across multiple files, you need to give every localization a **unique** key (like an ID).

Because you will most likely not localize your content to every language in the game, you will need a **fallback language** that gets used when the game is set to a language your content is not localized to.

This is why the **first file you need to create** in your localization directory is the `en_us.local` file!
The `en_us.local` (English US) file is always the fallback language, so make sure to add it!

To do this, just open your **localization directory** and **right-click** into the folder to create a new **text document**.

![](https://user-images.githubusercontent.com/35544624/134384066-256c0495-30b6-42b5-95ff-bcb3d34e3f28.png)

> **IMPORTANT:** Now you will need to [turn on file extensions](https://cdn.discordapp.com/attachments/795308330746511390/801561308012347482/unknown.png) on Windows and maybe other systems, to see the `.txt` extension of your newly created text file.
{.is-warning}

Rename this text file to `en_us.local` (make sure to remove the old `.txt` extension).

![](https://user-images.githubusercontent.com/35544624/134384272-6891f062-5f7a-4ba0-bcbc-6c3c6d96924a.png)

Right-click it and click on **Open with -> Choose another app** (on Windows) and search and select the text editor of your choice in the list. Now enable the **Always use this app to open .local files** option at the bottom of the window and click **OK**.

![](https://user-images.githubusercontent.com/35544624/134385052-d569d8b5-ec15-44d2-b103-da7d3f6288a0.png)

Now you can open and edit `.local` files with your normal text editor.

### Localization File Content

You just created your first localization file (**English US**).
This means, when the game language is set to English US, your text elements will be localized to the content in the `en_us.local` file (and in the case of this specific file, it will also get used if you don't have a localization file for the current game language).

But the file is still empty, so none of your text elements can get any content from this file.
Lets change this.

Open your `en_us.local` file with a text editor.

There's always one localization key with its value per text line, so line breaks will not work (and will break the localization file).

To add a new localization, just start with the **unique** key you've chosen for it, followed by an equals sign and the actual value.

![](https://user-images.githubusercontent.com/35544624/134387882-87d163d7-e974-4f42-b736-3e0c0e1f98e6.png)

Keys need to be **unique**, so you can't use the same key for more than one localization **in the same file**.

Just like for the first localization, you can now add more localizations to the localization file.

![](https://user-images.githubusercontent.com/35544624/134388902-b61b0fab-8e79-428b-ad53-3756e0f9fcf1.png)

Now you have your first (and most important) localization file ready to use.

### Adding More Languages

But your currently only have one language, so it's not really localization, right?

Well, no problem! Just like you've created and edited your `en_us.local` file, you can now make files for other languages!

In my example, I will create a file to localize my text content to German.

To do this, I will create a `de_de.local` file in my localization directory.

![](https://user-images.githubusercontent.com/35544624/134390071-97ea159f-5eb0-4695-89e5-6dbfa637c9c5.png)

You've probably noticed at this point that the names of your localization files can't be random.
You always need to use the **correct language code** for the localization file as file name.

If you want to know the correct language code (aka. local code) for a language, check out [this Minecraft wiki page](https://minecraft.fandom.com/wiki/Language).

Now I will add the exact same values as in the `en_us.local` file to my new `de_de.local` file, but will translate the values to German.

Make sure to **only translate the value** and **not the key**.

![](https://user-images.githubusercontent.com/35544624/134391225-0e44e7bc-b8bf-4f98-a5bc-d4564ba92686.png)

Now you have your default `en_us.local` file and one or more other localization files with the same values for other languages.

You can edit these files later to add more values or to edit existing ones.

## 1.2. Use Your Localizations

Your localization files are ready now, so lets see if they work.

To use your localizations in text elements, you just need to edit the content of a text element (like button labels, normal text, etc.) and click on the little PLUS (+) button at the right side of the text edit box and click on **Advanced -> Localize Text**.

![](https://user-images.githubusercontent.com/35544624/218220965-76b79586-1945-4179-9845-254275f5e6d5.png)

This will add a new placeholder text value to your text edit box.

![](https://user-images.githubusercontent.com/35544624/218220967-a26bfed3-1074-42f2-a94c-e2e69efe7d2e.png)

Now just replace `localization.key` with one of your own localization keys from your localization files.

![](https://user-images.githubusercontent.com/35544624/218221194-bb686d86-3dc0-4bbd-b142-186ef8c8f4cc.png)

You can also add normal text to the element.

![](https://user-images.githubusercontent.com/35544624/218221289-2c71cb02-42c5-48b7-acc7-089c5fcf8b35.png)

Text elements with placeholder values will look a bit special in the editor, but they will look normal in the actual menu later.

![](https://user-images.githubusercontent.com/35544624/218221392-b89286a8-406a-40e0-a85b-88e9cff48e17.png)

![](https://user-images.githubusercontent.com/35544624/134394901-1a09e605-1498-47f2-b11d-061ba53ebdde.png)

And now you can switch the language to one of your other supported languages and see if the value changes to the new language.

![](https://user-images.githubusercontent.com/35544624/134395496-1e9cb636-d45f-4cc8-9a42-bc56eda5c016.png)

And that's basically it. No other special things to know. Not too difficult, right?

# 2. How to Localize Non-Text Elements

*Ha! Bold of you to assume you can only localize boring text elements!*

FancyMenu also allows you to localize images and basically every element you want.

To do this, you will need to use **visibility requirements**.
The **Is Game Language** requirement, to be more specific.

Every element in your layout has its own visibility requirements.
To access the visibility requirements of an element, **right-click** the element and click on **Visibility Requirements**.

Now use the arrow buttons to switch to the **Is Game Language** requirement.

![](https://user-images.githubusercontent.com/35544624/134397174-b086ef00-b526-4c7c-9c5d-674c15cad5db.png)

Click on the first button to **enable** the requirement and then write the correct language code you want to check for in the text box.

If you want to know the correct language code (aka. local code) for a language, check out [this Minecraft wiki page](https://minecraft.fandom.com/wiki/Language).

You can choose between **Show If** and **Show If Not**. The first one will show the element **if** the game language is set to the choosen language and the second one will show the element if the language is **not** set to the choosen one.

In our case, we just need the **Show If** mode.

Now you can show, for example, a specific image for English and another one for German or other languages.
That way you can show an element with maybe some localized parts in it (like text) for the correct game language.