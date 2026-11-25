---
title: Game Intro
description: Play an animation or video at every game start, before the Title screen shows up.
---

# Game Intro

The Game Intro plays an animation or a video when the game starts, right after Minecraft's loading screen. When it ends, it fades into the Title screen. It's made for modpacks: a logo, a studio intro or a short trailer.

<img width="800" alt="The Skyhaven intro: night turns into dawn over a floating island and the logo drops in letter by letter, then the intro fades into the Title screen, which has the same island as its background" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/game_intro_showcase.gif?raw=true">

Players can skip it with any key or a click. The Game Intro is one of the [Global Customizations](/global-customizations), so it needs no layout.

# Setting the Intro

<img width="800" alt="Opening Global Customizations and Game Intro from the menu bar, picking skyhaven_intro.apng with Set Game Intro, playing it with Re-Trigger Game Intro and skipping it with Space" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/game_intro_setup.gif?raw=true">

1. Put your animation or video into `<game-directory>/config/fancymenu/assets/`.
2. Open **menu bar -> Customization -> Global Customizations -> Game Intro**.
3. Click **Set Game Intro**. With **Source Type** on **Local**, click **Choose Local Resource File**, select your file and click **OK**.
4. Click **Re-Trigger Game Intro** to watch it right away.

To remove the intro, move the mouse onto **Set Game Intro** and click **Reset to Default**.

## Animations and Videos

- **Animations:** APNG or GIF files. How to make them: [Animations](/animations).
- **Videos:** MP4 files. They need the mods Watermedia V3 and Watermedia Binaries V3, see [Videos](/video#requirements). Without them, a video intro only shows a red note with download links for a few seconds.
- Files of your instance and of resource packs work, web links don't. See [Resources](/resources).

The intro fills the whole screen and keeps its proportions, so parts of it get cut off on screens with other proportions. Most screens are 16:9, so make your intro 16:9 too, like 1920x1080. See-through parts of it show black.

> [!TIP]
> Players see the intro at every game start, so keep it short, about 5 to 10 seconds.

## Free Example Intro

The Skyhaven intro from the GIFs on this page is free to use, for testing and in your modpacks:

- [skyhaven_intro.apng](https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/skyhaven_intro.apng?raw=true): the intro, 1280x720, 5.4 seconds long. It plays once.
- [skyhaven_menu.png](https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/skyhaven_menu.png?raw=true): its last scene without the logo, 1280x720. Make it the [image background](/menu-backgrounds#image) of a Title screen layout, and the intro fades into a matching menu, like in the first GIF.

# Settings

All settings are in **menu bar -> Customization -> Global Customizations -> Game Intro**:

| Setting | What it does |
|---|---|
| **Set Game Intro** | The animation or video. |
| **Game Intro Skipping** | Any key or click skips the intro, and **Press Any Key to Skip** shows at the bottom. Skipping ends the intro right away, without fading. Turned off, the intro always plays to its end. |
| **Game Intro Fade-Out** | Fades the intro into the Title screen when it ends. Turned off, the Title screen shows up right away. |
| **Ignore Game Intro Loops** | Ends the intro after its animation played once, even if the animation loops. Turned off, the intro plays all loops of the animation. Videos always play once. |
| **Custom Skip Text** | Replaces **Press Any Key to Skip**, like with `Press any key to start your adventure`. A localization key of a resource pack, like `skyhaven.intro.skip`, shows its text in the player's language. |
| **Game Intro Volume** | How loud a video intro is, from 0% to 100%. |
| **Game Intro Sound Channel** | The sound channel of video intros, like Music. The volume of that channel and the master volume in Minecraft's sound settings apply on top. |
| **Re-Trigger Game Intro** | Plays the intro right away, over the screen you're on. |

**Game Intro Skipping**, **Game Intro Fade-Out** and **Ignore Game Intro Loops** are on by default.

> [!WARNING]
> With **Game Intro Skipping** and **Ignore Game Intro Loops** both turned off, an animation that loops forever never ends, and players can't get to the Title screen.

# Good to Know

- The intro plays once per game start, before the first screen after the loading screen. Normally, that's the Title screen.
- To change Minecraft's loading screen before it, see [Loading Screen](/loading-screen).
- The source of the intro can contain [placeholders](/resources#placeholders-in-resource-sources).
- The Game Intro settings get saved in FancyMenu's `options.txt`, so they belong to the loaded [profile](/profiles). Modpacks that include `config/fancymenu/` ship the intro with them, together with its file in `assets/`. See [Modpacks](/modpacks).
