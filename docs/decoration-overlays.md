---
title: Decoration Overlays
description: Add fullscreen visual overlays to menus in the FancyMenu layout editor.
---
# Decoration Overlays

Decoration Overlays are fullscreen effects that render in front of your menu elements.

They are useful when you want to add atmosphere or motion to a menu without building those effects manually.

# Where To Find It

Open a layout in the layout editor, then right-click the editor background and open **Decoration Overlays**.

# Quick Start

1. Open a layout in the layout editor.
2. Right-click the background (empty area).
3. Open **Decoration Overlays**.
4. Select an overlay type.
5. Set **Show Overlay** to **Enabled**.
6. Configure the overlay settings.
7. Save the layout and test the screen.

# How Overlay Types Work

Each overlay type has its own submenu and its own **Show Overlay** toggle.

- You can enable only the types you want.
- You can combine multiple enabled types in one layout.
- Settings are per overlay type (for example color, intensity, speed, density, scale, special behavior).

> [!INFO]
> It is possible to stack multiple instances of the same overlay type by using multiple layouts with the same type enabled.

# Overlay Types

- **Snowfall**: snowfall with optional snow accumulation on surfaces/buttons.
- **Rainfall**: rain with optional puddles, drips, and optional thunder flashes.
- **Fireflies**: moving firefly groups with configurable group amount, density, size, and color.
- **String Lights**: configurable string combinations, light colors, wind/flicker behavior, and holiday color mode.
- **Leaves**: falling leaves with configurable colors, wind, speed, scale, and density.
- **Fireworks**: frequent fireworks with configurable amount, explosion size, and scale.
- **Confetti**: confetti rain with optional mouse-click confetti mode.
- **Buddy**: an interactive virtual pet with hunger, happiness, energy, fun, activities, leveling, achievements, and persistent state.
- **Browser**: fullscreen browser overlay with URL and media settings.
- **GLSL Shader**: fullscreen custom shader overlay (for animated or static shader-based visuals).

# Buddy Virtual Pet

The **Buddy** overlay is a Tamagotchi-style virtual pet, not just a visual character. It walks along the bottom of the screen, displays thought bubbles for its needs, reacts to interaction, and keeps its state between game sessions.

## Needs and Controls

Buddy tracks four values from `0` to `100`:

- **Hunger** decreases over time and is restored by food.
- **Happiness** decreases over time and increases through care, including petting and play.
- **Energy** decreases while awake and during activities, then regenerates while sleeping.
- **Fun** decreases over time and increases while playing.

Use these mouse controls and the status screen to care for it:

- **Left-click Buddy** to pet it. Left-clicking while it sleeps wakes it and applies a small happiness penalty.
- **Right-click Buddy** to open its status screen. The Stats tab shows all four needs, level, and XP; the Achievements tab shows achievement progress.
- Select **Feed** in the status screen, then drag the food to Buddy. Food restores hunger and happiness.
- Select **Play** in the status screen, then drag and release the ball. The ball uses the mouse's movement to calculate throw velocity, and Buddy can chase, catch, hold, and play with it.
- Select **Sleep** when the button is available to restore energy. Buddy also falls asleep automatically when its energy becomes critically low.
- Buddy occasionally leaves poop behind. **Left-click the poop** to clean it. Leaving at least three poops on screen continually lowers happiness until fewer than three remain; the maximum poop count is configurable.

## XP, Levels, and Achievements

Caring for Buddy, cleaning poop, maintaining good needs, and completing other milestones awards XP. Buddy starts at level 1 and can reach level 30. Higher levels gradually reduce hunger, happiness, and energy decay (up to 50% at level 30) and improve several care and XP effects.

Achievements track interaction, stat, level, session, and special milestones. Open the status screen with a right-click to inspect both progression systems.

## Death and Resetting the Save

**Buddy Can Die** is enabled by default. If either hunger or happiness remains continuously at `0` for **10 real hours**, Buddy dies and is replaced by a gravestone. Raising the zero-valued need before the timer expires resets that need's timer; disabling **Buddy Can Die** clears both timers.

To start over after death, left-click the gravestone. You can also use **Reset Buddy Save** in the Buddy overlay settings at any time. Resetting removes both the pet-state save and the separate leveling/achievement save for that overlay instance.

> [!WARNING]
> Resetting a Buddy save permanently removes its needs, level, XP, achievements, activity counters, and saved poop state.

## Persistence and Customization

Buddy state is saved automatically about every two minutes and when its screen closes. Pet state and leveling state use separate JSON files for each overlay instance inside `<game-directory>/fancymenu_data/buddy/`. See [Data Storage Locations](./data-storage-locations) for the complete FancyMenu path reference.

The overlay settings also let you replace Buddy's sprite atlas, interaction items, need icons, status-screen textures, and gravestone. Advanced stat settings control decay, activity costs and gains, care effectiveness, maximum poop count, and whether death is enabled.

# Browser Overlay: Interactive vs Passive

The Browser overlay can be configured either as an interactive browser or as a passive visual layer.

- **Process Mouse/Keyboard** settings control whether the browser itself handles input.
- **Consume Mouse/Keyboard** settings control whether input is blocked from the menu behind it.

Practical setup examples:

- Interactive browser in front: enable both **Process** and **Consume**.
- Visual-only browser layer: disable **Process** and disable **Consume**.

> [!IMPORTANT]
> The Browser decoration overlay requires the **[Rinku](https://modrinth.com/mod/rinku)** mod.
