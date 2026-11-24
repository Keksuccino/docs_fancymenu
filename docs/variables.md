---
title: Variables
description: How to store texts and lists in variables, and use them in texts, actions and requirements.
---

# Variables

Variables are values FancyMenu remembers, even after the game closes. Use them to count clicks, remember choices, track progress, or keep lists like loading tips. Texts, actions, requirements, listeners and some elements can read and change them.

> [!TIP]
> The actions for variables are listed in [Action Scripts](/action-scripts), the requirements in [Requirements](/conditions), and the listener in [Listeners](/listeners#on-variable-updated-fm-variable-fm_variable_updated).

# Text and List Variables

There are two kinds of variables:

- Text variables hold one text, like `dark`, `5` or `true`.
- List variables hold a list of entries, like loading tips or server names. Every entry is a text of its own.

The position of an entry in a list is its index. The first entry has index `0`, the second one `1`, and so on. Negative indexes count from the end, so `-1` is the last entry.

Things that only know text, like `$$name` or **Is Variable Value (FM Variable)**, get a list as a JSON array of its entries, like `["Craft a bed","Torches keep mobs away"]`.

# Managing Variables

Open **menu bar -> Customization -> Manage Variables**. The menu bar only has it outside of the layout editor.

## Adding Variables

1. Right-click the list and click **Add Text Variable** or **Add List Variable**.
2. Type a name and click **Done**.

Names can have lowercase letters, numbers, `.`, `_` and `-`, and every name can only exist once.

## Changing Variables

Right-click a variable for these options:

| Option | What it does |
|---|---|
| **Set Value** | Sets the text of a text variable. |
| **Edit List** | Opens the list editor of a list variable (see below). |
| **Convert to List…** | Turns a text variable into a list. A **Separator** splits the text into entries: type `\n` to split at line breaks. **Trim Entries** removes spaces around every entry, and **Skip Empty Entries** leaves out empty ones. Text that already is a JSON array, like `["a","b"]`, gets read as one (**Read as JSON Array**). |
| **Convert to Text…** | Turns a list into a text variable. The **Separator** goes between the entries, or **Keep JSON Text** keeps the list as JSON array. |
| **Clear Variable on Game Launch** | Empties the variable every time the game starts. Good for values that should only last one session. |
| **Delete Variable** | Deletes the variable. |
| **Copy** and **Paste** | Make a copy of a variable. |
| **Export Variable for AI** | Copies the variable for [AI chats](/export-for-ai). |

Changes apply right away. Undo them with `Ctrl + Z` and redo them with `Ctrl + Y` (`Cmd` on macOS). Start typing to search, press `Enter` to edit the selected variable, or `Delete` to delete it.

## Editing Lists

The list editor shows every entry with its index.

- To add entries, click **Add Entry** below the list, type the entry and press `Enter`. The next new entry starts right away. Press `Enter` on an empty entry, or `Esc`, to stop adding.
- To edit an entry, double-click it. `Shift + Enter` opens it in the text editor, where it can have line breaks.
- To reorder entries, drag them, or press `Alt + Up` and `Alt + Down`.
- Right-click an entry for **Duplicate Entry** (`Ctrl + D`), **Delete Entry** (`Delete`), **Copy**, **Paste**, **Move Up** and **Move Down**.
- **Edit as Text** edits all entries at once, one per line.

**Done** saves the list. **Cancel** throws away everything you changed in the list editor.

# Showing Variables in Text

Type `$$` and the name of a variable to show its value. This works in every text that supports [placeholders](/placeholders), like [Text elements](/text-in-menus), button labels, tooltips and action values. The text updates by itself when the variable changes.

```
Current theme: $$menu_theme
```

- `$$name` of a variable that doesn't exist stays as it is.
- When names start the same, like `coins` and `coins_record`, `$$coins_record` always means the longer name.
- A list shows as JSON array. These placeholders show lists in a nicer way:

| Placeholder | Example | Gives you |
|---|---|---|
| **Get Variable Value (FM Variable)** | `{"placeholder":"getvariable","values":{"name":"clicks"}}` | The value, or `0` when the variable is empty or doesn't exist. Best for numbers. |
| **Get List Entry (FM Variable)** | `{"placeholder":"list_get","values":{"name":"tips","index":"0","fallback":"No tips yet"}}` | The entry at the index, or the `fallback` when there's none. |
| **List Size (FM Variable)** | `{"placeholder":"list_size","values":{"name":"tips"}}` | How many entries the list has. |
| **Index of List Entry (FM Variable)** | `{"placeholder":"list_index_of","values":{"name":"tips","value":"Torches keep mobs away","ignore_case":"false"}}` | The index of the first entry that matches the whole `value`, or `-1`. |
| **Join List Entries (FM Variable)** | `{"placeholder":"list_join","values":{"name":"tips","separator":"\n"}}` | All entries in one text, with the `separator` between them (`, ` when left out). `\n` is a line break. |

# Changing Variables with Actions

[Action scripts](/action-scripts) change variables when a button gets clicked, a ticker runs, a listener fires, and so on.

## Text Variables

[**Set Variable Value (FM Variable)**](/action-scripts#set-variable-value-fm-variable-set_variable) takes the name and the new value, separated by `:`. A variable that doesn't exist yet gets created.

```
menu_theme:dark
```

Only the first `:` separates the name, so the value can have more of them, like `last_server:play.example.net:25565`.

To count button clicks, add 1 to the old value:

```
clicks:{"placeholder":"calc","values":{"decimal":"false","expression":"{"placeholder":"getvariable","values":{"name":"clicks"}} + 1"}}
```

**Get Variable Value (FM Variable)** gives `0` while `clicks` is still empty, so the first click sets it to `1`.

Set Variable Value never turns a list into text. A JSON array becomes the entries of the list, empty text empties it, and any other text becomes its only entry.

[**Delete Variable (FM Variable)**](/action-scripts#delete-variable-fm-variable-delete_variable) deletes one variable, and [**Clear All Variables (FM Variable)**](/action-scripts#clear-all-variables-fm-variable-clear_variables) deletes all of them.

## List Actions

Every list action has its own window. All its fields support placeholders.

| Action | What it does |
|---|---|
| [**Add to List (FM Variable)**](/action-scripts#add-to-list-fm-variable-add_to_list) | Adds an entry at the end, or at an index. **Skip If Already in List** adds nothing when the list already has it. |
| [**Set List Entry (FM Variable)**](/action-scripts#set-list-entry-fm-variable-set_list_entry) | Replaces the entry at an index. |
| [**Remove from List (FM Variable)**](/action-scripts#remove-from-list-fm-variable-remove_from_list) | Removes the **Entry at Index**, the **First Match** of a value, or **All Matches**. |
| [**Clear List (FM Variable)**](/action-scripts#clear-list-fm-variable-clear_list) | Removes all entries. The list stays, but empty. |
| [**Set List (FM Variable)**](/action-scripts#set-list-fm-variable-set_list) | Replaces all entries with the parts of a **Split Text**, or the entries of a **JSON Array**. `$$other_list` as JSON Array copies another list. |
| [**Arrange List (FM Variable)**](/action-scripts#arrange-list-fm-variable-arrange_list) | **Sort A–Z**, **Sort Z–A**, **Numbers, Smallest First**, **Numbers, Biggest First**, **Reverse Order**, **Shuffle** or **Remove Duplicates**. |

- List actions create a list that doesn't exist yet, and turn empty text variables into lists. They never change a text variable that has a value: [convert it](#changing-variables) first.
- Type the name of the list without `$$`. With `$$`, the action uses the value of that variable as name.

## Going Through a List

The [FOR EACH loop](/action-scripts#for-each-loop) runs the actions inside it once for every entry of a list, from the first to the last.

1. Right-click the script area of the action script editor and click **Add FOR EACH Loop**.
2. Type the name of the list variable, without `$$`, and click **Done**.
3. Add actions inside the loop. In their values, `$$list_entry` is the current entry and `$$list_index` its index.

For example, a list `starter_commands` with the entries `/time set day` and `/weather clear`, and a [**Send Chat Message/Command**](/action-scripts#send-chat-messagecommand-sendmessage) action inside the loop with this value, runs both commands:

```
$$list_entry
```

- The loop reads the list once when it starts. Actions inside it can change the list without changing which entries the loop goes through.
- A text variable or a list that doesn't exist makes the loop run zero times.
- Like WHILE loops, it stops after 3 seconds, so it can't freeze the game.

# Checking Variables

[Requirements](/conditions) show elements or run parts of action scripts only when a variable has a certain value.

- [**Is Variable Value (FM Variable)**](/conditions#is-variable-value-fm-variable-fancymenu_visibility_requirement_is_variable_value) checks the whole value. For lists, it compares the JSON array of all entries.
- **List Contains Entry (FM Variable)** checks if a list has an entry. It has to match the whole entry. **Ignore Case** makes `Apple` match `apple`.
- [**Is Number**](/conditions#is-number-fancymenu_visibility_requirement_is_number) compares numbers, like `$$clicks` bigger than `5`.

For example, a button opens the latest news post and adds `news_42` to a list `read_news` with **Add to List (FM Variable)**. A "New!" badge next to the button has the requirement **List Contains Entry (FM Variable)** for `news_42`, with the **Requirement Mode** Opposite. So the badge hides once the player read the post.

# Linking Variables to Elements

- [Text Input Field](/elements#text-input-field): **Link To Variable** writes what the player types into the variable, and the field shows the value of the variable. Linked to a list, the typed text replaces the whole list.
- [Checkbox](/elements#checkbox): turn on **Variable Mode** and set **Link To Variable**. The checkbox writes `true` or `false` into the variable.
- [Slider](/elements#slider) of the type **Value List**: **Values From List Variable** takes the slider values from a list. Entries the list gets or loses show up right away.

# Reacting to Changes

- The [**On Variable Updated [FM Variable]**](/listeners#on-variable-updated-fm-variable-fm_variable_updated) listener runs an action script every time a variable gets set.
- The [`/fmvariable` command](/commands#fmvariable) sets and reads variables from chat, command blocks and other mods.

# Where Variables Are Saved

FancyMenu saves variables right away in `<game-directory>/config/fancymenu/user_variables.db`, so they stay after restarts.

- Variables belong to the whole Minecraft instance and its active [profile](/profiles). They aren't separate per layout, world, server or player.
- Names are case-sensitive.
- Don't store passwords, tokens or other secrets in variables. Anyone with access to the game folder can read them.
