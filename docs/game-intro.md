---
title: Game Intro
description: >-
  Play animated content before the game shows the Title screen for the first
  time.
---

# Game Intros

Game Intros play an animated image or video before the Title screen first appears.

# Setup

Open [**Global Customizations**](./global-customizations) through **Customization -> Global Customizations**, then configure these settings:

| Setting | Behavior |
|---|---|
| Set Game Intro | Selects a local, web, or Minecraft-resource animated image or video |
| Game Intro Skipping | Lets any key or mouse click skip the intro |
| Game Intro Fade-Out | Fades the intro into the target screen |
| Custom Skip Text | Replaces the default skip prompt with plain text or a localization key |
| Game Intro Volume | Sets the base volume from `0.0` to `1.0` |
| Game Intro Sound Channel | Selects the Minecraft sound category |
| Re-Trigger Game Intro | Plays the configured intro again for testing |

Video intros require **Watermedia V3**, **Watermedia Binaries V3**, and an OpenGL renderer. Watermedia video playback is unavailable with Vulkan. When playback is unavailable, FancyMenu displays an explanation over the intro screen. See [Videos](./video#requirements).

<br>
<img width="700" alt="Screenshot_1" src="https://gist.github.com/assets/35544624/71cec75b-33f1-4a21-9f18-d0adc7ceebb6">
