---
title: Placeholders
description: Show live values like the player's name, the time or the player count of a server in your texts, and every placeholder FancyMenu has.
---

# Placeholders

Placeholders are short codes that FancyMenu replaces with a live value, like the name of the player, the time or the player count of a server. They work in the texts of elements, button labels, tooltips, the values of actions and requirements, and most other texts you can type.

<img width="800" alt="Adding the Player Name placeholder to a Text element in the layout editor: Placeholders in the text editor, the Player category, and the text greets the player by name" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/placeholders_add.gif?raw=true">

> [!TIP]
> Your own [variables](/variables) work in the same texts, with `$$` and their name, like `$$coins`.

# Adding Placeholders

1. Open the text in the text editor, like **Text Content** of a [Text element](/text-in-menus). Text fields in windows, like the values of actions, have an **Open in Editor** button next to them.
2. Click where the placeholder should go.
3. Click **Placeholders** in the top-right corner of the text editor.
4. Click a category, or search by name, identifier or description. **BACK** goes back to the categories. Placeholders without a category are listed below the categories.
5. Move the mouse over a placeholder to see what it does, and click it to add it.
6. Replace its example values, like the mod ID of **Mod Version**.

Texts whose text editor has no **Placeholders** button don't support placeholders.

# How Placeholders Work

A placeholder looks like this:

```
{"placeholder":"playername"}
```

Placeholders with settings have them in `values`:

```
{"placeholder":"modversion","values":{"modid":"fancymenu"}}
```

- The identifier, like `playername`, is case-sensitive. Every placeholder below lists its identifier and its values.
- The order of the values doesn't matter. Values marked as optional can be left out.
- A placeholder FancyMenu can't replace, like one with a typo, stays in the text as you typed it.
- Placeholders always give text. When there's nothing to show, they give a fallback, like `0`, `0.0`, `---` or nothing.
- [Formatting codes](/text-formatting) work around placeholders: `&6{"placeholder":"playername"}` shows the name in gold.

> [!IMPORTANT]
> Placeholders look like JSON, but they aren't. Don't put them through a JSON formatter or validator, because placeholders inside other placeholders aren't valid JSON.

## Placeholders in Placeholders

Values can contain other placeholders and [variables](/variables#showing-variables-in-text). FancyMenu replaces the inner ones first. Quotes inside values need no escaping.

This turns the max RAM from MB into GB:

```
{"placeholder":"calc","values":{"decimal":"true","expression":"{"placeholder":"maxram"} / 1024"}}
```

This shows the variable `rank` in capital letters:

```
{"placeholder":"uppercase_text","values":{"text":"$$rank"}}
```

When a placeholder gives back text with placeholders in it, like a file read with [**File Text**](#file-text), FancyMenu replaces those too.

# Good to Know

- Placeholders update by themselves. FancyMenu keeps a replaced text for 30 milliseconds before it replaces its placeholders again. Change that with **Placeholder Caching Duration [MS]** in **menu bar -> Customization -> Settings**. `0` replaces them every frame, which costs more performance.
- Placeholders that read websites, files or servers, like **Web Text** or **Server Status**, load in the background. Until then, they give nothing or a fallback.
- In [actions](/action-scripts), placeholders get their current value right when the action runs.
- Placeholders about the world, the screen and elements only work on the game's main thread. In a [Ticker](/elements#ticker) that runs in the background (asynchronous), FancyMenu shows an error instead.
- **Random Number** gives a new number every time the text updates. To keep one, save it in a [variable](/variables) with [**Set Variable Value (FM Variable)**](/action-scripts#set-variable-value-fm-variable).

> [!CAUTION]
> Placeholders like **JSON Parser**, **File Text** and **Clipboard Content** can read files of the game folder and your clipboard. Together with actions that contact websites, a layout could send that data away. Only use layouts you trust.

# Examples

## Welcome Panel

<img width="800" alt="A Text element greets the player by name and shows the Minecraft version, the number of mods and the time" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/placeholders_welcome.png?raw=true">

```
### Welcome back, {"placeholder":"playername"}!
Minecraft {"placeholder":"mcversion"} with {"placeholder":"loadedmods"} mods
It's {"placeholder":"realtimehour"}:{"placeholder":"realtimeminute"}
```

## Server Status and Players

```
Survival: {"placeholder":"serverstatus","values":{"ip":"play.example.net"}}&r, {"placeholder":"serverplayercount","values":{"ip":"play.example.net"}} players
```

## Date and Time

```
{"placeholder":"realtimeday"}.{"placeholder":"realtimemonth"}.{"placeholder":"realtimeyear"}, {"placeholder":"realtimehour"}:{"placeholder":"realtimeminute"}
```

## RAM Usage

```
RAM: {"placeholder":"usedram"} / {"placeholder":"maxram"} MB ({"placeholder":"percentram"}%)
```

# All Placeholders

Every placeholder FancyMenu has. The big **Advanced** and **World** categories of the placeholder menu are split into smaller groups here.

## Variables and Lists

These are in the **Advanced** category. See [Variables](/variables) for making variables and lists.

### Get Variable Value (FM Variable)

**Identifier:** `getvariable`

The value of one of your variables. Gives `0` when the variable is empty or doesn't exist, which makes it good for numbers. A list gives all its entries as JSON array, like `["Steve","Alex"]`.

- `name`: the name of the variable, without `$$`

```
{"placeholder":"getvariable","values":{"name":"clicks"}}
```

### Get List Entry (FM Variable)

**Identifier:** `list_get`

One entry of a list variable.

- `name`: the name of the list
- `index`: the position of the entry. The first entry is `0`, and negative numbers count from the end, so `-1` is the last entry.
- `fallback` (optional): what you get when there's no entry at that index, or no list with that name. Empty by default.

```
{"placeholder":"list_get","values":{"name":"tips","index":"0","fallback":"No tips yet"}}
```

### List Size (FM Variable)

**Identifier:** `list_size`

How many entries a list has. `0` when there's no list with that name.

- `name`: the name of the list

```
{"placeholder":"list_size","values":{"name":"tips"}}
```

### Index of List Entry (FM Variable)

**Identifier:** `list_index_of`

The index of the first entry that matches the whole `value`, or `-1` when the list doesn't have it.

- `name`: the name of the list
- `value`: the entry to look for
- `ignore_case` (optional): `true` makes `Apple` match `apple`. `false` by default.

```
{"placeholder":"list_index_of","values":{"name":"read_news","value":"news_42","ignore_case":"false"}}
```

### Join List Entries (FM Variable)

**Identifier:** `list_join`

All entries of a list in one text. Empty when there's no list with that name.

- `name`: the name of the list
- `separator` (optional): the text between the entries. `\n` is a line break. `, ` by default.

```
{"placeholder":"list_join","values":{"name":"tips","separator":"\n"}}
```

## Math

These are in the **Advanced** category. Numbers use a dot for decimals, like `2.5`.

### Calculator

**Identifier:** `calc`

Solves a math expression, like `2 + 3 * 4`.

- `expression`: the math to solve
- `decimal` (optional): `false` rounds the result to a whole number. `true` by default, which gives results like `14.0`.

```
{"placeholder":"calc","values":{"decimal":"false","expression":"{"placeholder":"usedram"} * 100 / {"placeholder":"maxram"}"}}
```

| In expressions | What it does |
|---|---|
| `+` `-` `*` `/` | Add, subtract, multiply, divide |
| `^` | Power, like `2 ^ 3` for 8 |
| `%` | Remainder, like `7 % 3` for 1 |
| `( )` | Groups parts, like `(2 + 3) * 4` |
| `pi`, `e` | The numbers π and e |
| `abs(x)` | Number without its minus |
| `sqrt(x)`, `cbrt(x)` | Square root, cube root |
| `pow(x, y)` | x to the power of y |
| `floor(x)`, `ceil(x)` | Rounds down, rounds up |
| `sin(x)`, `cos(x)`, `tan(x)`, `cot(x)` | Trigonometry, with angles in radians |
| `asin(x)`, `acos(x)`, `atan(x)` | Inverse trigonometry |
| `sinh(x)`, `cosh(x)`, `tanh(x)` | Hyperbolic functions |
| `log(x)`, `log2(x)`, `log10(x)` | Logarithms to the base e, 2 and 10 |
| `exp(x)` | e to the power of x |
| `signum(x)` | `1`, `-1` or `0`, like [**Sign (Math)**](#sign-math) |

### Random Number

**Identifier:** `random_number`

A random whole number between `min` and `max`. It changes every time the text updates.

- `min`, `max`: the lowest and highest number

```
{"placeholder":"random_number","values":{"min":"1","max":"6"}}
```

### Max Number

**Identifier:** `maxnum`

The bigger one of two numbers.

- `first`, `second`: the numbers

```
{"placeholder":"maxnum","values":{"first":"$$score","second":"$$best_score"}}
```

### Min Number

**Identifier:** `minnum`

The smaller one of two numbers.

- `first`, `second`: the numbers

```
{"placeholder":"minnum","values":{"first":"10","second":"15"}}
```

### Absolute Number

**Identifier:** `absnum`

The number without its minus, so `-10.5` gives `10.5`.

- `num`: the number

```
{"placeholder":"absnum","values":{"num":"-10.5"}}
```

### Negate Number

**Identifier:** `negnum`

Makes a positive number negative, so `10.5` gives `-10.5`. Zero and negative numbers stay as they are.

- `num`: the number

```
{"placeholder":"negnum","values":{"num":"10.5"}}
```

### Round (Math)

**Identifier:** `math_round`

Rounds a number. `2.5` rounds up to `3`.

- `num`: the number
- `decimals` (optional): how many decimal places to keep, so `2` turns `3.14159` into `3.14`. `0`, `-1` or nothing rounds to a whole number.

```
{"placeholder":"math_round","values":{"num":"3.14159","decimals":"2"}}
```

### Floor (Math)

**Identifier:** `math_floor`

Rounds a number down to a whole number, so `3.7` gives `3` and `-3.2` gives `-4`.

- `num`: the number

```
{"placeholder":"math_floor","values":{"num":"3.7"}}
```

### Ceiling (Math)

**Identifier:** `math_ceil`

Rounds a number up to a whole number, so `3.2` gives `4` and `-3.7` gives `-3`.

- `num`: the number

```
{"placeholder":"math_ceil","values":{"num":"3.2"}}
```

### Sign (Math)

**Identifier:** `math_sign`

`1` for positive numbers, `-1` for negative ones and `0` for zero.

- `num`: the number

```
{"placeholder":"math_sign","values":{"num":"-3.14"}}
```

### *pi* (Math)

**Identifier:** `math_pi`

The number π: `3.141592653589793`.

```
{"placeholder":"math_pi"}
```

### Trigonometric Sine (Math)

**Identifier:** `math_sin`

The sine of an angle in radians. For degrees, multiply them by π / 180 first, with the Calculator.

- `angle`: the angle in radians

```
{"placeholder":"math_sin","values":{"angle":"1.5707963267948966"}}
```

### Trigonometric Cosine (Math)

**Identifier:** `math_cos`

The cosine of an angle in radians.

- `angle`: the angle in radians

```
{"placeholder":"math_cos","values":{"angle":"0"}}
```

### Trigonometric Tangent (Math)

**Identifier:** `math_tan`

The tangent of an angle in radians.

- `angle`: the angle in radians

```
{"placeholder":"math_tan","values":{"angle":"0.7853981633974483"}}
```

### Hyperbolic Sine (Math)

**Identifier:** `math_sinh`

The hyperbolic sine of a number.

- `num`: the number

```
{"placeholder":"math_sinh","values":{"num":"1"}}
```

### Hyperbolic Cosine (Math)

**Identifier:** `math_cosh`

The hyperbolic cosine of a number.

- `num`: the number

```
{"placeholder":"math_cosh","values":{"num":"1"}}
```

### Hyperbolic Tangent (Math)

**Identifier:** `math_tanh`

The hyperbolic tangent of a number.

- `num`: the number

```
{"placeholder":"math_tanh","values":{"num":"1"}}
```

### Number Base Converter

**Identifier:** `number_base_convert`

Converts a number to another base, like from decimal to binary or hex. Decimals work too, with up to 16 digits after the dot. Letters of the result are capital, like `FF`.

- `input`: the number
- `from_base` (optional): the base of `input`, from `2` to `36`. `10` by default.
- `to_base` (optional): the base of the result, from `2` to `36`. `10` by default.

```
{"placeholder":"number_base_convert","values":{"input":"255","from_base":"10","to_base":"16"}}
```

## Text

These are in the **Advanced** category.

### Uppercase Text

**Identifier:** `uppercase_text`

The text in capital letters: `Hello World` gives `HELLO WORLD`. [Formatting codes](/text-formatting) like `&a` stay as they are.

- `text`: the text

```
{"placeholder":"uppercase_text","values":{"text":"Hello World"}}
```

### Lowercase Text

**Identifier:** `lowercase_text`

The text in small letters: `HELLO WORLD` gives `hello world`. Formatting codes stay as they are.

- `text`: the text

```
{"placeholder":"lowercase_text","values":{"text":"HELLO WORLD"}}
```

### Title Case Text

**Identifier:** `title_case_text`

Every word starts with a capital letter: `hello world` gives `Hello World`. Formatting codes stay as they are.

- `text`: the text

```
{"placeholder":"title_case_text","values":{"text":"hello world"}}
```

### Sentence Case Text

**Identifier:** `sentence_case_text`

Every sentence starts with a capital letter: `hello world. this is fancymenu!` gives `Hello world. This is fancymenu!`. Formatting codes stay as they are.

- `text`: the text

```
{"placeholder":"sentence_case_text","values":{"text":"hello world. this is fancymenu!"}}
```

### Snake Case Text

**Identifier:** `snake_case_text`

Small letters with `_` between the words: `Hello World` gives `hello_world`. Formatting codes get removed.

- `text`: the text

```
{"placeholder":"snake_case_text","values":{"text":"Hello World"}}
```

### Kebab Case Text

**Identifier:** `kebab_case_text`

Small letters with `-` between the words: `Hello World` gives `hello-world`. Formatting codes get removed.

- `text`: the text

```
{"placeholder":"kebab_case_text","values":{"text":"Hello World"}}
```

### Alternating Case Text

**Identifier:** `alternating_case_text`

Small and capital letters take turns: `alternating case` gives `aLtErNaTiNg CaSe`.

- `text`: the text

```
{"placeholder":"alternating_case_text","values":{"text":"alternating case"}}
```

### Toggle Case Text

**Identifier:** `toggle_case_text`

Small letters become capital and capital ones small: `Toggle Case` gives `tOGGLE cASE`.

- `text`: the text

```
{"placeholder":"toggle_case_text","values":{"text":"Toggle Case"}}
```

### Trim Text

**Identifier:** `trim_text`

Removes the spaces at the start and the end of a text. Spaces inside it stay.

- `text`: the text

```
{"placeholder":"trim_text","values":{"text":"  Welcome!  "}}
```

### Crop Text

**Identifier:** `crop_text`

Removes a number of characters from the start and the end of a text. `hello world` without 1 character on each side gives `ello worl`.

- `text`: the text
- `remove_from_start`: how many characters to remove from the start
- `remove_from_end`: how many characters to remove from the end

```
{"placeholder":"crop_text","values":{"text":"hello world","remove_from_start":"1","remove_from_end":"1"}}
```

### Split Text

**Identifier:** `split_text`

Splits a text and gives one of its parts. `Steve,Alex,Notch` split at `,` gives `Alex` as part `1`.

- `input`: the text
- `regex`: where to split, as regular expression. Characters like `.`, `|` and `?` need a `\` in front, like `\.`.
- `max_parts` (optional): the most parts to split into. `-1` (the default) splits at every match.
- `split_index`: the part you get. The first part is `0`.

```
{"placeholder":"split_text","values":{"input":"Steve,Alex,Notch","regex":",","max_parts":"-1","split_index":"1"}}
```

### Replace Text

**Identifier:** `replace_text`

Replaces parts of a text: `Hello World!` with `World` replaced by `FancyMenu` gives `Hello FancyMenu!`.

- `text`: the text
- `search`: what to look for
- `replacement` (optional): what to put in its place. Empty by default, which removes what's found.
- `use_regex` (optional): `true` makes `search` a regular expression. Then `$1`, `$2` and so on in `replacement` are the groups it found. `false` by default.
- `replace_all` (optional): `false` only replaces the first match. `true` by default.

```
{"placeholder":"replace_text","values":{"text":"Hello World!","search":"World","replacement":"FancyMenu","use_regex":"false","replace_all":"true"}}
```

### Switch Case

**Identifier:** `switch_case`

Gives the result of the case that matches a value. When the variable `difficulty_level` is `2`, the example gives `Hard Mode`.

- `value`: the value to check
- `cases`: pairs of value and result, like `1:Easy Mode,2:Hard Mode`. Values and results can't contain `,` or `:`.
- `default` (optional): the result when no case matches. Without one, the placeholder stays as it is then.

```
{"placeholder":"switch_case","values":{"value":"$$difficulty_level","cases":"1:Easy Mode,2:Hard Mode","default":"Normal Mode"}}
```

### Localize Text

**Identifier:** `local`

The text of a localization key in the current language of the game, like `Singleplayer` for `menu.singleplayer`. Works with Minecraft's keys, keys of mods and your own keys (see [Localization](/localization)).

- `key`: the localization key

```
{"placeholder":"local","values":{"key":"menu.singleplayer"}}
```

### Stringify

**Identifier:** `stringify`

Replaces the placeholders in the text, then puts a `\` in front of every `"`, `{` and `}`. This way, text from outside, like a website, can't turn into placeholders.

- `text`: the text

```
{"placeholder":"stringify","values":{"text":"{"placeholder":"webtext","values":{"link":"https://example.com/motd.txt"}}"}}
```

## Data and Files

These are in the **Advanced** category. Local paths start in the game folder, like `/config/fancymenu/assets/news.txt`, and can't leave it (see [Resources](/resources#local-resources)).

### JSON Parser

**Identifier:** `json`

Reads a value from JSON. Several results show one per line.

- `source`: JSON text, a JSON file in the game folder, or the URL of a JSON file
- `json_path`: the path to the value, like `$.name` or `$.players[0].name`. See [json.fancymenu.net](https://json.fancymenu.net) to learn more about JSON paths.

```
{"placeholder":"json","values":{"source":"https://example.com/server_info.json","json_path":"$.news.title"}}
```

JSON from the web gets loaded once, and again when FancyMenu reloads. Changes to files show right away.

| Path | What you get |
|---|---|
| `$.name` | The `name` of the top level |
| `$.player.level` | `level` inside `player` |
| `$.items[0].id` | The `id` of the first entry of `items` |
| `$.scores.*` | All values inside `scores` |

### File Text

**Identifier:** `file_text`

The text of a file or a URL. Files get read again every second, URLs every 10 seconds. Gives nothing while the text loads or when it can't be read.

- `path_or_url`: a file in the game folder, or a URL. Paths that start with `.minecraft/` point to the default Minecraft folder.
- `mode` (optional): `all` for the whole text, or `last` for the last lines. `all` by default.
- `separator` (optional): the text between the lines. `\n` (a line break) by default.
- `last_lines` (optional): how many lines `last` gives. `1` by default.

```
{"placeholder":"file_text","values":{"path_or_url":"/config/fancymenu/assets/changelog.txt","mode":"all","separator":"\n","last_lines":"1"}}
```

### File Size

**Identifier:** `file_size`

The size of a file in bytes. `0` when the file doesn't exist. Paths that start with `.minecraft/` point to the default Minecraft folder.

- `path`: the file

```
{"placeholder":"file_size","values":{"path":"/config/fancymenu/assets/news.txt"}}
```

### File MD5

**Identifier:** `file_md5`

The MD5 hash of a file, like `d41d8cd98f00b204e9800998ecf8427e`. Empty when the file doesn't exist. Paths that start with `.minecraft/` point to the default Minecraft folder.

- `path`: the file

```
{"placeholder":"file_md5","values":{"path":"/config/fancymenu/assets/menu_music.ogg"}}
```

### Encode To Base64

**Identifier:** `base64_encode`

The text as Base64: `Hello World` gives `SGVsbG8gV29ybGQ=`.

- `text`: the text

```
{"placeholder":"base64_encode","values":{"text":"Hello World"}}
```

### Decode From Base64

**Identifier:** `base64_decode`

Base64 back as text: `SGVsbG8gV29ybGQ=` gives `Hello World`.

- `text`: the Base64 text

```
{"placeholder":"base64_decode","values":{"text":"SGVsbG8gV29ybGQ="}}
```

### Get NBT Data (Client-Side)

**Identifier:** `nbt_data_get`

Reads NBT data, like `/data get`, from what your game knows about the world. That's quick, but servers don't send everything to players.

- `source_type`: `entity` or `block`
- `entity_selector`: for `entity`, a selector like `@s` (you), `@p`, `@e[type=minecraft:horse,limit=1,sort=nearest]`, or the name or UUID of an entity. Selectors can have `type`, `name`, `tag`, `limit`, `sort`, `distance`, `x`, `y`, `z`, `dx`, `dy` and `dz`. The first match counts.
- `block_pos`: for `block`, the position of a block entity, like a chest: `120 64 -35`
- `nbt_path`: the NBT path, like `foodLevel` or `Inventory[0].id`
- `scale` (optional): multiplies numbers. `1.0` by default.
- `return_type` (optional): `value` (numbers and texts as they are), `string`, `snbt` or `json`. `value` by default.

```
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"foodLevel","scale":"1.0","return_type":"value"}}
```

### Get NBT Data (Server-Side)

**Identifier:** `nbt_data_get_server`

Reads NBT data from the server, exactly like `/data get`. Needs FancyMenu on the server. In singleplayer, it always works. Gives nothing until the server answers, then updates about every 100 milliseconds.

- `source_type`: `entity`, `block` or `storage`
- `entity_selector`: for `entity`, any selector of `/data get` that finds one entity, like `@s` or `@e[type=minecraft:villager,limit=1,sort=nearest]`
- `block_pos`: for `block`, a position like `120 64 -35`, `~ ~-1 ~` or `^ ^ ^1`
- `storage_id`: for `storage`, the ID of a command storage, like `mypack:quests`
- `nbt_path` (optional): the NBT path. Without one, you get all data.
- `scale` (optional): multiplies numbers. `1.0` by default.
- `return_type` (optional): `value`, `string`, `snbt` or `json`. `value` by default.

```
{"placeholder":"nbt_data_get_server","values":{"source_type":"storage","storage_id":"mypack:quests","nbt_path":"completed","return_type":"value"}}
```

## Audio

These read [Audio elements](/elements#audio) of the open menu. Right-click an Audio element in the layout editor and click **Copy Element ID** for its ID.

### Audio Element Volume

**Identifier:** `audio_element_vol`

The volume of the Audio element, from `0.0` (0%) to `1.0` (100%).

- `element_identifier`: the ID of the Audio element

```
{"placeholder":"audio_element_vol","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Current Audio Track

**Identifier:** `audio_element_current_track`

The file name of the track that plays right now, like `menu_theme.ogg`. `---` when no track plays.

- `element_identifier`: the ID of the Audio element
- `display_name_mappings` (optional): names to show instead of file names. `=>` goes between file name and display name, and `%:%` between the pairs.

```
{"placeholder":"audio_element_current_track","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","display_name_mappings":"menu_theme.ogg=>Menu Theme%:%credits.ogg=>Credits Theme"}}
```

### Audio Duration

**Identifier:** `audio_duration`

How long the current track is, like `03:45`. `00:00` while it loads.

- `element_identifier`: the ID of the Audio element

```
{"placeholder":"audio_duration","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Audio Play Time

**Identifier:** `audio_playtime`

How far the current track is, like `01:30`. `00:00` (or `0`) while it's stopped.

- `element_identifier`: the ID of the Audio element
- `show_percentage` (optional): `true` gives the progress from `0` to `100` instead. `false` by default.

```
{"placeholder":"audio_playtime","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","show_percentage":"false"}}
```

### Audio Playing State

**Identifier:** `audio_playing_state`

`true` while the Audio element plays, `false` while it's paused or stopped.

- `element_identifier`: the ID of the Audio element

```
{"placeholder":"audio_playing_state","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

## Client

These are about the game and its mods.

### Minecraft Version

**Identifier:** `mcversion`

The version of Minecraft, like `1.21.1`.

```
{"placeholder":"mcversion"}
```

### Mod Loader Name

**Identifier:** `loadername`

The name of the mod loader, like `Fabric` or `NeoForge`.

```
{"placeholder":"loadername"}
```

### Mod Loader Version

**Identifier:** `loaderver`

The version of the mod loader, like `0.16.14`.

```
{"placeholder":"loaderver"}
```

### Mod Version

**Identifier:** `modversion`

The version of an installed mod, like `3.11.0`. `0.0.0` when the mod isn't installed.

- `modid`: the ID of the mod, like `fancymenu`

```
{"placeholder":"modversion","values":{"modid":"fancymenu"}}
```

### Active Mods Count

**Identifier:** `loadedmods`

How many mods are loaded. Libraries and mods inside other mods count too, so it's often more than the number of mod files.

```
{"placeholder":"loadedmods"}
```

### Total Mods Count

**Identifier:** `totalmods`

Roughly how many mods are installed, counted from the `.jar` files in the `mods` folder once per game start. It's never less than **Active Mods Count**.

```
{"placeholder":"totalmods"}
```

### World Loading Progress

**Identifier:** `world_load_progress`

How far a world loads, from `0` to `100`, while its loading screen shows. Good for loading bars. `0` on all other screens.

```
{"placeholder":"world_load_progress"}
```

### Minecraft Option Value

**Identifier:** `minecraft_option_value`

The value of a Minecraft option, as it's saved in the `options.txt` file of the game folder, like `12` for `renderDistance`. Empty when there's no option with that name.

- `name`: the name of the option in `options.txt`

```
{"placeholder":"minecraft_option_value","values":{"name":"renderDistance"}}
```

### Keybind Key

**Identifier:** `keybind_key`

The key a keybind uses right now, like in the Controls screen: `Space` for jumping. Empty when there's no keybind with that name.

- `keybind`: the name of the keybind, like `key.jump` or `key.inventory`. The names are in `options.txt`, without the `key_` at the start: `key_key.jump` is `key.jump`.

```
Press {"placeholder":"keybind_key","values":{"keybind":"key.inventory"}} to open your inventory!
```

### Last World or Server

**Identifier:** `last_world_server`

The world or server the player joined last. Servers show as `play.example.net:25565`.

- `type`: `both` for worlds and servers, `world` for worlds only, or `server` for servers only. With `world` or `server`, it's empty when the last one was the other kind.
- `full_world_path` (optional): `false` only gives the name of a world, like `New World`. `true` gives the path of its folder. `true` by default.

```
{"placeholder":"last_world_server","values":{"type":"world","full_world_path":"false"}}
```

## GUI

These are about the open screen and its elements. Element placeholders take the ID of an element: right-click it in the layout editor and click **Copy Element ID**.

### Screen Width

**Identifier:** `guiwidth`

The width of the screen in GUI pixels. That's the size elements use, not the pixels of your monitor.

```
{"placeholder":"guiwidth"}
```

### Screen Height

**Identifier:** `guiheight`

The height of the screen in GUI pixels.

```
{"placeholder":"guiheight"}
```

### GUI Scale

**Identifier:** `guiscale`

The GUI scale of the game, like `2`.

```
{"placeholder":"guiscale"}
```

### Current Screen Identifier

**Identifier:** `screenid`

The [identifier](/screen-identifiers) of the open screen, like `title_screen`. Empty when no screen is open.

```
{"placeholder":"screenid"}
```

### Element Width

**Identifier:** `elementwidth`

The width of an element in GUI pixels. `1` when there's no element with that ID.

- `id`: the ID of the element

```
{"placeholder":"elementwidth","values":{"id":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Element Height

**Identifier:** `elementheight`

The height of an element in GUI pixels. `1` when there's no element with that ID.

- `id`: the ID of the element

```
{"placeholder":"elementheight","values":{"id":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Element X Position

**Identifier:** `elementposx`

Where the left edge of an element is, in GUI pixels from the left of the screen. `1` when there's no element with that ID.

- `id`: the ID of the element

```
{"placeholder":"elementposx","values":{"id":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Element Y Position

**Identifier:** `elementposy`

Where the top edge of an element is, in GUI pixels from the top of the screen. `1` when there's no element with that ID.

- `id`: the ID of the element

```
{"placeholder":"elementposy","values":{"id":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Text Element Content Height

**Identifier:** `text_element_content_height`

How high a [Text element](/text-in-menus) needs to be to show all of its text without scrolling, in GUI pixels. It counts wrapped lines, text scale and line spacing, so it's good for backgrounds that fit the text. `0` when the element isn't a Text element.

- `element_identifier`: the ID of the Text element

```
{"placeholder":"text_element_content_height","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Element Scroll Position

**Identifier:** `scroll_area_scroll_position`

How far the content of a [Scrollable Area](/scrollable-areas) or a Text element is scrolled, in GUI pixels from its start. `0` for other elements.

- `element_identifier`: the ID of the element
- `axis`: `vertical` or `horizontal`. Anything else means the direction the element scrolls in.

```
{"placeholder":"scroll_area_scroll_position","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","axis":"vertical"}}
```

### Element Scroll Percent

**Identifier:** `scroll_area_scroll_percent`

How far the content of a Scrollable Area or a Text element is scrolled, from `0` (start) to `100` (end). `0` for other elements, and when there's nothing to scroll.

- `element_identifier`: the ID of the element
- `axis`: `vertical` or `horizontal`. Anything else means the direction the element scrolls in.

```
{"placeholder":"scroll_area_scroll_percent","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","axis":"vertical"}}
```

### Element Scroll Content Size

**Identifier:** `scroll_area_content_size`

How big the content of a Scrollable Area or a Text element is: its height for `vertical`, its width for `horizontal`. `0` for other elements.

- `element_identifier`: the ID of the element
- `axis`: `vertical` or `horizontal`. Anything else means the direction the element scrolls in.

```
{"placeholder":"scroll_area_content_size","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","axis":"vertical"}}
```

### Text Input Field Value

**Identifier:** `text_input_field_value`

What's typed into a [Text Input Field](/elements#text-input-field) or a text field of the original screen. Empty when the element is no text field.

- `element_identifier`: the ID of the element

```
{"placeholder":"text_input_field_value","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Vanilla Widget Label/Text

**Identifier:** `vanillabuttonlabel`

The label of a button or another widget of the original screen, like `Options...`. Right-click the widget in the layout editor and click **Copy Widget Locator** for its locator.

- `locator`: the locator of the widget

```
{"placeholder":"vanillabuttonlabel","values":{"locator":"title_screen:mc_titlescreen_options_button"}}
```

### Mouse X Position

**Identifier:** `mouseposx`

Where the mouse is, in GUI pixels from the left of the screen. Always `10` in the layout editor, so elements that follow the mouse stay where you can edit them.

```
{"placeholder":"mouseposx"}
```

### Mouse Y Position

**Identifier:** `mouseposy`

Where the mouse is, in GUI pixels from the top of the screen. Always `10` in the layout editor.

```
{"placeholder":"mouseposy"}
```

### Clicks Per Second

**Identifier:** `clicks_per_second`

How often a mouse button got clicked in the last second.

- `mouse_button` (optional): `left` or `right`. `left` by default.

```
{"placeholder":"clicks_per_second","values":{"mouse_button":"left"}}
```

## Player

### Player Name

**Identifier:** `playername`

The name of the player, like `Steve`.

```
{"placeholder":"playername"}
```

### Player UUID

**Identifier:** `playeruuid`

The UUID of the player, like `c8cde7fe-7ced-11eb-9439-0242ac130002`.

```
{"placeholder":"playeruuid"}
```

### Last Death Message

**Identifier:** `lastdeathmessage`

The last death message of the player since the game started, like `Steve was slain by Zombie`. Empty before the first death.

- `as_json_component` (optional): `true` gives it as JSON text component, with its colors. `false` by default.

```
{"placeholder":"lastdeathmessage","values":{"as_json_component":"false"}}
```

## Realtime

These are about the time on your computer. The ones for date and time have an optional `timezone`: `system` for the time zone of the computer (the default), or an ID like `UTC`, `Europe/Berlin` or `America/New_York`. See [nodatime.org/TimeZones](https://nodatime.org/TimeZones) for all IDs.

### Realtime Year

**Identifier:** `realtimeyear`

The year, like `2026`.

```
{"placeholder":"realtimeyear","values":{"timezone":"system"}}
```

### Realtime Month

**Identifier:** `realtimemonth`

The month, from `01` to `12`.

```
{"placeholder":"realtimemonth","values":{"timezone":"system"}}
```

### Realtime Day

**Identifier:** `realtimeday`

The day of the month, from `01` to `31`.

```
{"placeholder":"realtimeday","values":{"timezone":"system"}}
```

### Realtime Hour

**Identifier:** `realtimehour`

The hour, from `00` to `23`.

- `twelve_hour_format` (optional): `true` gives `01` to `12` instead. `false` by default.

```
{"placeholder":"realtimehour","values":{"twelve_hour_format":"false","timezone":"Europe/Berlin"}}
```

### Realtime Minute

**Identifier:** `realtimeminute`

The minute, from `00` to `59`.

```
{"placeholder":"realtimeminute","values":{"timezone":"system"}}
```

### Realtime Second

**Identifier:** `realtimesecond`

The second, from `00` to `59`.

```
{"placeholder":"realtimesecond","values":{"timezone":"system"}}
```

### Current Time in Millis (Unix Timestamp)

**Identifier:** `unix_time`

The milliseconds since January 1, 1970 (UTC), like `1732456789012`. Good for timers: save it in a variable, and subtract it from a later one with the Calculator.

```
{"placeholder":"unix_time"}
```

## Server

These ask a server for its status, like the server list does. FancyMenu asks every 30 seconds while a customized screen is open. Until the first answer, the server counts as offline.

- `ip`: the address of the server, with the port when it isn't the default one, like `play.example.net` or `play.example.net:25566`

### Server Status

**Identifier:** `serverstatus`

`Online` in green or `Offline` in red.

```
{"placeholder":"serverstatus","values":{"ip":"play.example.net"}}
```

### Server Player Count

**Identifier:** `serverplayercount`

The players online and the max players, like `12/100`. `0/0` until the server answers.

```
{"placeholder":"serverplayercount","values":{"ip":"play.example.net"}}
```

### Server MOTD

**Identifier:** `servermotd`

One line of the server's message of the day.

- `line`: `1` or `2`

```
{"placeholder":"servermotd","values":{"ip":"play.example.net","line":"1"}}
```

### Server PING

**Identifier:** `serverping`

The ping to the server in milliseconds, like `54`. `-1` while it's offline.

```
{"placeholder":"serverping","values":{"ip":"play.example.net"}}
```

### Server Version

**Identifier:** `serverversion`

The Minecraft version of the server, like `1.21.1`. Some servers show their own text here. `---` until the server answers.

```
{"placeholder":"serverversion","values":{"ip":"play.example.net"}}
```

## Video

These read [Video elements and video menu backgrounds](/video) of the open menu. For Video elements, right-click one in the layout editor and click **Copy Element ID**. For backgrounds, right-click the editor background and click **Copy Background Identifier**.

### Video Element Volume

**Identifier:** `video_element_vol`

The volume of a Video element, from `0.0` (0%) to `1.0` (100%).

- `element_identifier`: the ID of the Video element

```
{"placeholder":"video_element_vol","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Video Element Duration

**Identifier:** `video_element_duration`

How long the video of a Video element is, like `02:00`. `00:00` (or `0`) while it loads.

- `element_identifier`: the ID of the Video element
- `output_as_timestamp` (optional): `true` gives milliseconds instead, like `120000`. `false` by default.

```
{"placeholder":"video_element_duration","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","output_as_timestamp":"false"}}
```

### Video Element Play Time

**Identifier:** `video_element_playtime`

How far the video of a Video element is, like `00:45`. `00:00` (or `0`) while it loads.

- `element_identifier`: the ID of the Video element
- `show_percentage` (optional): `true` gives the progress from `0` to `100`. `false` by default.
- `output_as_timestamp` (optional): `true` gives milliseconds. `show_percentage` wins when both are `true`. `false` by default.

```
{"placeholder":"video_element_playtime","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","show_percentage":"false","output_as_timestamp":"false"}}
```

### Video Element Paused State

**Identifier:** `video_element_paused_state`

`true` while a Video element is paused, otherwise `false`.

- `element_identifier`: the ID of the Video element

```
{"placeholder":"video_element_paused_state","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Video Background Volume

**Identifier:** `video_background_vol`

The volume of a video menu background, from `0.0` (0%) to `1.0` (100%).

- `background_identifier`: the identifier of the menu background

```
{"placeholder":"video_background_vol","values":{"background_identifier":"8c2e4f6a-1b3d-4e5f-8a7b-9c0d1e2f3a4b-1732456789012"}}
```

### Video Background Duration

**Identifier:** `video_background_duration`

How long the video of a menu background is, like `03:00`. `00:00` (or `0`) while it loads.

- `background_identifier`: the identifier of the menu background
- `output_as_timestamp` (optional): `true` gives milliseconds instead. `false` by default.

```
{"placeholder":"video_background_duration","values":{"background_identifier":"8c2e4f6a-1b3d-4e5f-8a7b-9c0d1e2f3a4b-1732456789012","output_as_timestamp":"false"}}
```

### Video Background Play Time

**Identifier:** `video_background_playtime`

How far the video of a menu background is, like `01:00`. `00:00` (or `0`) while it loads.

- `background_identifier`: the identifier of the menu background
- `show_percentage` (optional): `true` gives the progress from `0` to `100`. `false` by default.
- `output_as_timestamp` (optional): `true` gives milliseconds. `show_percentage` wins when both are `true`. `false` by default.

```
{"placeholder":"video_background_playtime","values":{"background_identifier":"8c2e4f6a-1b3d-4e5f-8a7b-9c0d1e2f3a4b-1732456789012","show_percentage":"true","output_as_timestamp":"false"}}
```

### Video Background Paused State

**Identifier:** `video_background_paused_state`

`true` while a video menu background is paused, otherwise `false`.

- `background_identifier`: the identifier of the menu background

```
{"placeholder":"video_background_paused_state","values":{"background_identifier":"8c2e4f6a-1b3d-4e5f-8a7b-9c0d1e2f3a4b-1732456789012"}}
```

## World: Player Stats

The **World** category is about the world you play in. Most of its placeholders need a loaded world. Outside of one, they give `0`, `0.0` or nothing.

### Current Player Health

**Identifier:** `current_player_health`

The health of the player, like `20.0`. Every heart is `2.0`.

```
{"placeholder":"current_player_health"}
```

### Max Player Health

**Identifier:** `max_player_health`

The max health of the player, like `20.0`.

```
{"placeholder":"max_player_health"}
```

### Current Player Health (Percent)

**Identifier:** `current_player_health_percent`

The health of the player in percent, from `0` to `100`.

```
{"placeholder":"current_player_health_percent"}
```

### Current Player Absorption Health

**Identifier:** `current_player_absorption_health`

The absorption health of the player (the golden hearts), like `4.0`.

```
{"placeholder":"current_player_absorption_health"}
```

### Max Player Absorption Health

**Identifier:** `max_player_absorption_health`

The max absorption health of the player, like `4.0`.

```
{"placeholder":"max_player_absorption_health"}
```

### Current Player Absorption Health (Percent)

**Identifier:** `current_player_absorption_health_percent`

The absorption health of the player in percent, from `0` to `100`.

```
{"placeholder":"current_player_absorption_health_percent"}
```

### Current Player Food Level

**Identifier:** `current_player_hunger`

The food level of the player, from `0.0` to `20.0`.

```
{"placeholder":"current_player_hunger"}
```

### Max Player Food Level

**Identifier:** `max_player_hunger`

The max food level of players: always `20.0`.

```
{"placeholder":"max_player_hunger"}
```

### Current Player Food Level (Percent)

**Identifier:** `current_player_hunger_percent`

The food level of the player in percent, from `0` to `100`.

```
{"placeholder":"current_player_hunger_percent"}
```

### Current Player Hunger Saturation

**Identifier:** `current_player_hunger_saturation`

The saturation of the player, like `5.0`. Food only goes down after it's used up.

```
{"placeholder":"current_player_hunger_saturation"}
```

### Current Player Armor

**Identifier:** `current_player_armor`

The armor points of the player, from `0.0` to `20.0`.

```
{"placeholder":"current_player_armor"}
```

### Max Player Armor

**Identifier:** `max_player_armor`

The max armor points of the armor bar: always `20.0`.

```
{"placeholder":"max_player_armor"}
```

### Current Player Armor (Percent)

**Identifier:** `current_player_armor_percent`

The armor points of the player in percent, from `0` to `100`.

```
{"placeholder":"current_player_armor_percent"}
```

### Player Armor Toughness

**Identifier:** `player_armor_toughness`

The armor toughness of the player, like `8.0` with full diamond armor.

```
{"placeholder":"player_armor_toughness"}
```

### Current Player Oxygen Level

**Identifier:** `current_player_oxygen`

The air of the player under water, from `0.0` to `300.0`.

```
{"placeholder":"current_player_oxygen"}
```

### Max Player Oxygen Level

**Identifier:** `max_player_oxygen`

The max air of the player, like `300.0`.

```
{"placeholder":"max_player_oxygen"}
```

### Current Player Oxygen Level (Percent)

**Identifier:** `current_player_oxygen_percent`

The air of the player in percent, from `0` to `100`.

```
{"placeholder":"current_player_oxygen_percent"}
```

### Current Player Level

**Identifier:** `current_player_level`

The experience level of the player, like `30`.

```
{"placeholder":"current_player_level"}
```

### Current Player Experience

**Identifier:** `current_player_exp`

The total experience points of the player, like `1395.0`. It's not the level.

```
{"placeholder":"current_player_exp"}
```

### Player Experience Progress (Percent)

**Identifier:** `current_player_exp_progress`

How full the experience bar is, from `0` to `100`.

```
{"placeholder":"current_player_exp_progress"}
```

### Player Attack Strength (Percent)

**Identifier:** `player_attack_strength`

How charged the next attack is, from `0` to `100`, like the attack indicator.

```
{"placeholder":"player_attack_strength"}
```

### Player Game Mode

**Identifier:** `player_gamemode`

`survival`, `creative`, `adventure` or `spectator`.

```
{"placeholder":"player_gamemode"}
```

### Player Item Use Progress (FM)

**Identifier:** `player_item_use_progress_fm`

How far the player is with using an item, like eating, drinking or drawing a bow, from `0.0` to `1.0`.

```
{"placeholder":"player_item_use_progress_fm"}
```

### Current Mount Health

**Identifier:** `current_mount_health`

The health of the mob the player rides, like a horse, like `30.0`.

```
{"placeholder":"current_mount_health"}
```

### Max Mount Health

**Identifier:** `max_mount_health`

The max health of the mob the player rides.

```
{"placeholder":"max_mount_health"}
```

### Current Mount Health (Percent)

**Identifier:** `current_mount_health_percent`

The health of the mob the player rides in percent, from `0` to `100`.

```
{"placeholder":"current_mount_health_percent"}
```

### Current Mount Jump Meter (Percent)

**Identifier:** `current_mount_jump_meter`

How charged the jump of a horse is, from `0` to `100`.

```
{"placeholder":"current_mount_jump_meter"}
```

### Active Effects Count

**Identifier:** `effects_count`

How many effects the player has right now.

```
{"placeholder":"effects_count"}
```

### Active Effect

**Identifier:** `active_effect`

The ID of an effect of the player, like `minecraft:speed`, in the order of the effect icons at the top right. Empty when there's no effect at that index.

- `effect_index`: the position of the effect. The first one is `0`.

```
{"placeholder":"active_effect","values":{"effect_index":"0"}}
```

## World: Inventory and Items

These are in the **World** category. Slot numbers: `0` to `8` are the hotbar, `9` to `35` the rest of the inventory, `36` to `39` the armor from boots to helmet, and `40` the offhand.

### Selected Hotbar Slot

**Identifier:** `active_hotbar_slot`

The selected hotbar slot, from `0` to `8`.

```
{"placeholder":"active_hotbar_slot"}
```

### Slot Item

**Identifier:** `slot_item`

The ID of the item in a slot, like `minecraft:diamond_sword`. Empty slots give `minecraft:air`.

- `slot`: the slot number

```
{"placeholder":"slot_item","values":{"slot":"0"}}
```

### Slot Item Count

**Identifier:** `slot_item_count`

How many items are in a slot, like `64`.

- `slot`: the slot number

```
{"placeholder":"slot_item_count","values":{"slot":"0"}}
```

### Slot Item Durability

**Identifier:** `slot_item_durability`

The durability of the item in a slot. `0` for items without durability.

- `slot`: the slot number
- `format` (optional): `current` (the durability left), `max`, `damage` (the durability lost) or `percentage` (left, from `0` to `100`). `current` by default.

```
{"placeholder":"slot_item_durability","values":{"slot":"39","format":"percentage"}}
```

### Slot Item Display Name (FM)

**Identifier:** `slot_item_display_name_fm`

The name of the item in a slot as JSON text component, with its rarity color, like `{"text":"Diamond Sword","color":"aqua"}`. In spectator mode, hotbar slots give the names of the spectator menu.

- `slot`: the slot number
- `ignore_spectator` (optional): `true` gives the item names in spectator mode too. `false` by default.

```
{"placeholder":"slot_item_display_name_fm","values":{"slot":"0","ignore_spectator":"false"}}
```

### Inventory Item Count

**Identifier:** `inventory_item_count`

How many of an item the player has in the whole inventory.

- `item`: the ID of the item, like `minecraft:diamond`. Empty counts all items.

```
{"placeholder":"inventory_item_count","values":{"item":"minecraft:diamond"}}
```

### Inventory Slot Food Point Restore Amount

**Identifier:** `inventory_slot_food_point_restore_amount`

How many food points the item in a slot gives when eaten, like `4.0` for an apple. `0.0` for items that aren't food.

- `slot`: the slot number

```
{"placeholder":"inventory_slot_food_point_restore_amount","values":{"slot":"0"}}
```

### Item Category

**Identifier:** `item_category`

The creative inventory tab of an item, like `Combat`. `UNKNOWN` for items without a tab.

- `item`: the ID of the item
- `as_key` (optional): `true` gives the ID of the tab, like `minecraft:combat`. `false` by default.

```
{"placeholder":"item_category","values":{"item":"minecraft:diamond_sword","as_key":"false"}}
```

### Hovered Inventory Item

**Identifier:** `hovered_inventory_item`

The ID of the item the mouse is on in an inventory screen, like `minecraft:apple`. Empty when there's none.

```
{"placeholder":"hovered_inventory_item"}
```

## World: HUD and Bosses

These are in the **World** category. The raid placeholders read the raid whose bar shows at the top of the screen, and need FancyMenu on the server. In singleplayer, they always work. Without a raid, they give `0` or nothing.

### Action Bar Message (FM)

**Identifier:** `action_bar_message_fm`

The message above the hotbar as JSON text component, like `{"text":"You may not rest now","color":"red"}`. Empty when there's none.

```
{"placeholder":"action_bar_message_fm"}
```

### Action Bar Message Time (FM)

**Identifier:** `action_bar_message_time_fm`

How many ticks the message above the hotbar still shows. 20 ticks are one second.

```
{"placeholder":"action_bar_message_time_fm"}
```

### Highlighted Item Time (FM)

**Identifier:** `highlighted_item_time_fm`

How many ticks the name of the selected item still shows above the hotbar.

```
{"placeholder":"highlighted_item_time_fm"}
```

### Current HUD Title/Subtitle

**Identifier:** `current_title`

The title or subtitle that shows right now, like from `/title`. Empty when there's none.

- `is_subtitle` (optional): `true` gives the subtitle. `false` by default.
- `as_json` (optional): `true` gives it as JSON text component. `false` by default.

```
{"placeholder":"current_title","values":{"is_subtitle":"false","as_json":"false"}}
```

### Bosses Count

**Identifier:** `boss_count`

How many boss bars show right now.

```
{"placeholder":"boss_count"}
```

### Boss Name

**Identifier:** `boss_name`

The name of a boss bar, like `Ender Dragon`. Empty when there's no boss bar at that index.

- `boss_index`: the position of the boss bar. The top one is `0`.
- `as_json` (optional): `true` gives it as JSON text component. `false` by default.

```
{"placeholder":"boss_name","values":{"boss_index":"0","as_json":"false"}}
```

### Current Boss Health (Percent)

**Identifier:** `current_boss_health`

How full a boss bar is, from `0` to `100`.

- `boss_index`: the position of the boss bar. The top one is `0`.

```
{"placeholder":"current_boss_health","values":{"boss_index":"0"}}
```

### Total Active Raid Waves

**Identifier:** `active_raid_total_waves`

How many waves the raid has, with its bonus wave.

```
{"placeholder":"active_raid_total_waves"}
```

### Remaining Active Raid Waves

**Identifier:** `active_raid_remaining_waves`

How many waves of the raid still have to come.

```
{"placeholder":"active_raid_remaining_waves"}
```

### Current Active Raid Wave

**Identifier:** `active_raid_current_wave`

The number of the latest wave, so `1` while the first wave attacks. `0` before the first wave.

```
Wave {"placeholder":"active_raid_current_wave"} of {"placeholder":"active_raid_total_waves"}
```

### Active Raid Alive Raiders Count

**Identifier:** `active_raid_alive_raiders_count`

How many raiders of the raid are still alive.

```
{"placeholder":"active_raid_alive_raiders_count"}
```

### Active Raid Alive Raiders List

**Identifier:** `active_raid_alive_raiders_list`

All raiders that are still alive, separated by commas. Every entry is the mob ID and the UUID of the raider, like `minecraft:pillager#0d9a4b2e-5f1c-4a8e-9b3d-6c2f1e7a8b90`.

```
{"placeholder":"active_raid_alive_raiders_list"}
```

## World: Position and Camera

These are in the **World** category.

### Player X Coordinate

**Identifier:** `player_x_coordinate`

The X coordinate of the block the player stands in, like `125`.

```
{"placeholder":"player_x_coordinate"}
```

### Player Y Coordinate

**Identifier:** `player_y_coordinate`

The Y coordinate of the block the player stands in, like `64`.

```
{"placeholder":"player_y_coordinate"}
```

### Player Z Coordinate

**Identifier:** `player_z_coordinate`

The Z coordinate of the block the player stands in, like `-250`.

```
{"placeholder":"player_z_coordinate"}
```

### Player View Direction

**Identifier:** `player_view_direction`

The direction the player looks in: `north`, `east`, `south` or `west`.

```
{"placeholder":"player_view_direction"}
```

### Player Position Delta X (FM)

**Identifier:** `player_position_delta_x_fm`

How far the player moved along X since the last tick, in blocks, like `0.12`. Negative when moving the other way.

```
{"placeholder":"player_position_delta_x_fm"}
```

### Player Position Delta Y (FM)

**Identifier:** `player_position_delta_y_fm`

How far the player moved along Y since the last tick, like `-0.08` while falling.

```
{"placeholder":"player_position_delta_y_fm"}
```

### Player Position Delta Z (FM)

**Identifier:** `player_position_delta_z_fm`

How far the player moved along Z since the last tick.

```
{"placeholder":"player_position_delta_z_fm"}
```

### Camera Rotation X (FM)

**Identifier:** `camera_rotation_x_fm`

How far the camera looks up or down, in degrees, from `-90.0` (straight up) to `90.0` (straight down).

```
{"placeholder":"camera_rotation_x_fm"}
```

### Camera Rotation Y (FM)

**Identifier:** `camera_rotation_y_fm`

Which way the camera faces, in degrees from `-180.0` to `180.0`. `0.0` is south.

```
{"placeholder":"camera_rotation_y_fm"}
```

### Camera Rotation Delta X (FM)

**Identifier:** `camera_rotation_delta_x_fm`

How far the camera turned up or down since the last tick, in degrees.

```
{"placeholder":"camera_rotation_delta_x_fm"}
```

### Camera Rotation Delta Y (FM)

**Identifier:** `camera_rotation_delta_y_fm`

How far the camera turned left or right since the last tick, in degrees.

```
{"placeholder":"camera_rotation_delta_y_fm"}
```

## World: World Info

These are in the **World** category.

### World Day Time

**Identifier:** `world_daytime`

The time of day of the world in ticks. A day has 24000 ticks and starts at 6:00 in the morning. It keeps counting from day to day, so `{"placeholder":"world_daytime"} % 24000` in a Calculator gives the time of the current day.

```
{"placeholder":"world_daytime"}
```

### World Day Time Hour

**Identifier:** `world_daytime_hour`

The hour of the world's time of day, from `00` to `23`.

- `twelve_hour_format` (optional): `true` gives `01` to `12` instead. `false` by default.

```
{"placeholder":"world_daytime_hour","values":{"twelve_hour_format":"false"}}
```

### World Day Time Minute

**Identifier:** `world_daytime_minute`

The minute of the world's time of day, from `00` to `59`.

```
{"placeholder":"world_daytime_hour"}:{"placeholder":"world_daytime_minute"}
```

### World Game Time

**Identifier:** `game_time`

How many ticks the world ran in total. Unlike the day time, commands like `/time set` don't change it.

```
{"placeholder":"game_time"}
```

### World Difficulty

**Identifier:** `world_difficulty`

`peaceful`, `easy`, `normal` or `hard`.

```
{"placeholder":"world_difficulty"}
```

### Current Dimension

**Identifier:** `current_dimension`

The dimension the player is in, like `minecraft:overworld`.

- `as_key` (optional): `false` gives its name, like `Overworld`. Dimensions without a name give their ID. `true` by default.

```
{"placeholder":"current_dimension","values":{"as_key":"false"}}
```

### Current Biome

**Identifier:** `current_biome`

The biome the player is in, like `minecraft:plains`.

- `as_key` (optional): `false` gives its name, like `Plains`. `true` by default.

```
{"placeholder":"current_biome","values":{"as_key":"false"}}
```

### Current World Seed

**Identifier:** `current_world_seed`

The seed of the singleplayer world, like `-4172144997902289642`. Empty on servers.

```
{"placeholder":"current_world_seed"}
```

### Gamerule Value

**Identifier:** `gamerule_value`

The value of a game rule, like `true` or `3`. In singleplayer, it always works. On servers, it needs FancyMenu on the server. Empty when there's no game rule with that name.

- `name`: the name of the game rule, like `keep_inventory`. In Minecraft 1.21.10 and older, game rules have names like `keepInventory`, and these old names work in newer versions too.

```
{"placeholder":"gamerule_value","values":{"name":"keep_inventory"}}
```

### Current Server IP

**Identifier:** `current_server_ip`

The address of the server the player is on, like `play.example.net`. Empty in singleplayer.

```
{"placeholder":"current_server_ip"}
```

### World Players List

**Identifier:** `world_players_list`

The names of the players in the world your game knows about, sorted alphabetically, like `Alex, Notch, Steve`.

- `separator` (optional): the text between the names. `, ` by default.

```
{"placeholder":"world_players_list","values":{"separator":", "}}
```

## World: World Saves

These are in the **World** category and work in every menu, without a loaded world.

### World Save Count

**Identifier:** `level_save_count`

How many singleplayer worlds there are.

```
{"placeholder":"level_save_count"}
```

### World Save Names

**Identifier:** `level_save_names`

The names of all singleplayer worlds, in the order of the world list, like `Survival World, Creative Test`.

- `separator` (optional): the text between the names. `, ` by default.

```
{"placeholder":"level_save_names","values":{"separator":", "}}
```

### World Save Data

**Identifier:** `level_save_data`

All data of a singleplayer world as JSON, like `{"file_name":"Survival World","game_type":"survival","difficulty":"normal",...}`. It has `file_name`, `display_name`, `game_type`, `difficulty`, `allow_commands`, `last_played` (as Unix timestamp), `minecraft_version_name` and more. Read single values with [**JSON Parser**](#json-parser).

- `level_name`: the name of the world, exactly like in the world list

```
{"placeholder":"json","values":{"source":"{"placeholder":"level_save_data","values":{"level_name":"Survival World"}}","json_path":"$.game_type"}}
```

## Other

These have no category, so the placeholder menu lists them below the categories.

### FPS (Frames Per Second)

**Identifier:** `fps`

The frames per second, like `120`.

```
{"placeholder":"fps"}
```

### Used RAM in MB

**Identifier:** `usedram`

The RAM the game uses right now, in MB, like `4096`.

```
{"placeholder":"usedram"}
```

### Max RAM in MB

**Identifier:** `maxram`

The most RAM the game can use, in MB, like `8192`.

```
{"placeholder":"maxram"}
```

### Used RAM in %

**Identifier:** `percentram`

The RAM the game uses, in percent of the max RAM, like `50`.

```
{"placeholder":"percentram"}
```

### CPU Usage (JVM)

**Identifier:** `jvmcpu`

How much of the CPU the game uses, in percent, like `25.5`.

```
{"placeholder":"jvmcpu"}
```

### CPU Usage (OS)

**Identifier:** `oscpu`

How much of the CPU the whole computer uses, in percent, like `42.8`.

```
{"placeholder":"oscpu"}
```

### CPU Info

**Identifier:** `cpuinfo`

The name of the CPU, like `Intel(R) Core(TM) i7-10700K CPU @ 3.80GHz`.

```
{"placeholder":"cpuinfo"}
```

### GPU Info

**Identifier:** `gpuinfo`

The name of the graphics device the game uses, like `NVIDIA GeForce RTX 3080`.

```
{"placeholder":"gpuinfo"}
```

### OpenGL Version

**Identifier:** `glver`

The driver info of the graphics device the game uses, like `4.6.0 NVIDIA 566.36`.

```
{"placeholder":"glver"}
```

### Java Version

**Identifier:** `javaver`

The Java version the game runs on, like `21.0.5`.

```
{"placeholder":"javaver"}
```

### Java Virtual Machine

**Identifier:** `jvmname`

The name of the Java virtual machine, like `OpenJDK 64-Bit Server VM`.

```
{"placeholder":"jvmname"}
```

### Operating System Name

**Identifier:** `osname`

The name of the operating system, like `Windows 11`.

```
{"placeholder":"osname"}
```

### Uptime Duration

**Identifier:** `uptime_duration`

How long the game runs, in seconds, like `742`.

- `output_as_millis` (optional): `true` gives milliseconds instead. `false` by default.

```
{"placeholder":"uptime_duration","values":{"output_as_millis":"false"}}
```

### Random Text

**Identifier:** `randomtext`

A random line of a text file, a URL or a text you type, like a random tip. Files and URLs get read again every 30 seconds.

- `source`: a `.txt` file in the game folder, a URL, or lines separated by `\n`, like `Tip 1\nTip 2\nTip 3`
- `interval` (optional): after how many seconds a new line gets picked. `0` picks one line per game session. `10` by default.

```
{"placeholder":"randomtext","values":{"source":"/config/fancymenu/assets/tips.txt","interval":"10"}}
```

### Web Text

**Identifier:** `webtext`

The first line of the text of a web page, like a text file on your website. It gets loaded once, and again when FancyMenu reloads. Empty while it loads.

- `link`: the URL of the page

```
{"placeholder":"webtext","values":{"link":"https://example.com/motd.txt"}}
```

### Absolute File/Folder Path

**Identifier:** `absolute_path`

The full path of a file or folder in the game folder, like `C:/Users/Steve/AppData/Roaming/.minecraft/config/fancymenu`.

- `short_path`: the path inside the game folder

```
{"placeholder":"absolute_path","values":{"short_path":"config/fancymenu"}}
```

### Text Character Count

**Identifier:** `text_character_count`

How many characters a text has: `Hello World!` has `12`.

- `text`: the text

```
{"placeholder":"text_character_count","values":{"text":"$$player_nickname"}}
```

### Text Width

**Identifier:** `text_width`

How wide a text is in GUI pixels: `Hello World!` is `57`. Formatting codes like `&l` count like in the game, so bold text is wider.

- `text`: the text

```
{"placeholder":"text_width","values":{"text":"Hello World!"}}
```

### Text Height

**Identifier:** `text_height`

How high a text is in GUI pixels, with all of its lines. Line breaks are `\n`. To fit something to a Text element, use [**Text Element Content Height**](#text-element-content-height), which also counts its text scale, line spacing and wrapped lines.

- `text`: the text

```
{"placeholder":"text_height","values":{"text":"First line\nSecond line"}}
```

### Clipboard Content

**Identifier:** `clipboard_content`

The text in the clipboard of your computer. Empty when there's none.

```
{"placeholder":"clipboard_content"}
```
