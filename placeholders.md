---
title: Placeholders
description: How to use placeholders.
published: true
date: 2025-01-27T15:43:07.647Z
tags: 
editor: markdown
dateCreated: 2024-11-19T09:21:20.579Z
---

# Placeholders

Placeholders are dynamic values that get replaced with actual content when they are used. In FancyMenu, placeholders allow you to insert dynamic content into various elements like text, buttons, and loading requirements. Think of them as variables that get evaluated and replaced with their actual values when your layouts are displayed.

# General Information
<br>

## Basic Syntax
Placeholders in FancyMenu use a JSON-like syntax:
```
{"placeholder":"placeholder_id","values":{"value_name":"value"}}
```

For example, to display the player's name:
```
{"placeholder":"playername"}
```

## Nesting Placeholders
One of the most powerful features of FancyMenu's placeholder system is the ability to nest placeholders within other placeholders. This means you can use the output of one placeholder as an input for another.

Example of nested placeholders:
```
{"placeholder":"calc","values":{"decimal":"true","expression":"{"placeholder":"maxram"} / 1024"}}
```
This example takes the maximum RAM value and divides it by 1024 to convert it from MB to GB.

# Using Placeholders

Most elements that have text inputs support placeholders. You can see if a text input supports placeholders when editing it. If the full-screen **text editor** opens when editing the text, it supports placeholders. 

To find a **list of all placeholders**, just click on the **Placeholders** button in the **top-right corner** of the **text editor**.

Clicking on a placeholder in the placeholder list will paste it to the text content!

# Available Placeholders
<br>

## Minecraft Instance
<br>

### Minecraft Version (`mcversion`)
Returns the current Minecraft version.
```
{"placeholder":"mcversion"}
```
Example output: `1.19.2`

### Mod Loader Version (`loaderver`)
Returns the version of the mod loader (Forge/Fabric).
```
{"placeholder":"loaderver"}
```
Example output: `43.2.0`

### Mod Loader Name (`loadername`)
Returns the name of the mod loader.
```
{"placeholder":"loadername"}
```
Example output: `Forge`

### Mod Version (`modversion`)
Returns the version of a specific mod.
```
{"placeholder":"modversion","values":{"modid":"fancymenu"}}
```
Example output: `2.14.9`

### Total Mods (`totalmods`)
Returns the total number of mods installed.
```
{"placeholder":"totalmods"}
```
Example output: `45`

### Loaded Mods (`loadedmods`)
Returns the number of currently loaded mods.
```
{"placeholder":"loadedmods"}
```
Example output: `43`

### World Load Progress (`world_load_progress`)
Returns the current world loading progress as a percentage.
```
{"placeholder":"world_load_progress"}
```
Example output: `75`

### Minecraft Option Value (`minecraft_option_value`)
Returns the value of a Minecraft option.
```
{"placeholder":"minecraft_option_value","values":{"name":"fov"}}
```
Example output: `70`

## GUI (Screens / Menus)
<br>

### Screen Width (`guiwidth`)
Returns the current screen width.
```
{"placeholder":"guiwidth"}
```
Example output: `1920`

### Screen Height (`guiheight`)
Returns the current screen height.
```
{"placeholder":"guiheight"}
```
Example output: `1080`

### Screen Identifier (`screenid`)
Returns the identifier of the current screen.
```
{"placeholder":"screenid"}
```
Example output: `title_screen`

### Element Width (`elementwidth`)
Returns the width of a specific element.
```
{"placeholder":"elementwidth","values":{"id":"my_button"}}
```
Example output: `200`

### Element Height (`elementheight`)
Returns the height of a specific element.
```
{"placeholder":"elementheight","values":{"id":"my_button"}}
```
Example output: `20`

### Mouse Position X (`mouseposx`)
Returns the current X position of the mouse.
```
{"placeholder":"mouseposx"}
```
Example output: `960`

### Mouse Position Y (`mouseposy`)
Returns the current Y position of the mouse.
```
{"placeholder":"mouseposy"}
```
Example output: `540`

### GUI Scale (`guiscale`)
Returns the current GUI scale.
```
{"placeholder":"guiscale"}
```
Example output: `2`

## Advanced Category
<br>

### Calculator (`calc`)
The calculator placeholder is a powerful tool that allows you to perform mathematical calculations within your layouts. It supports a wide range of mathematical operations and can work with both decimal and integer numbers.

#### Basic Syntax
```
{"placeholder":"calc","values":{"decimal":"true/false","expression":"your_expression"}}
```

The calculator has two main parameters:
- `decimal`: Determines whether the result should include decimal places (`true`) or be rounded to integers (`false`)
- `expression`: The mathematical expression to evaluate

#### Supported Operations
The calculator supports these mathematical operations:
- Basic arithmetic: `+` (addition), `-` (subtraction), `*` (multiplication), `/` (division)
- Parentheses: `( )` for grouping operations
- Power: `^` for exponents
- Square root: `sqrt()`
- Trigonometric functions: `sin()`, `cos()`, `tan()`
- Mathematical constants: `pi`, `e`
- Absolute value: `abs()`
- Logarithms: `log()`, `ln()`

#### Examples

Basic arithmetic with decimals:
```
{"placeholder":"calc","values":{"decimal":"true","expression":"10.5 + 5.3"}}
```
Output: `15.8`

Integer arithmetic:
```
{"placeholder":"calc","values":{"decimal":"false","expression":"10.5 + 5.3"}}
```
Output: `16`

Complex calculations:
```
{"placeholder":"calc","values":{"decimal":"true","expression":"(5 + 3) * 2 ^ 2"}}
```
Output: `32.0`

Using mathematical functions:
```
{"placeholder":"calc","values":{"decimal":"true","expression":"sqrt(16) + sin(pi/2)"}}
```
Output: `5.0`

#### Using with Other Placeholders
The calculator becomes especially powerful when combined with other placeholders. Here are some practical examples:

Calculate RAM usage percentage:
```
{"placeholder":"calc","values":{"decimal":"false","expression":"({"placeholder":"usedram"} / {"placeholder":"maxram"}) * 100"}}
```
Output: `45` (if using 45% of RAM)

Convert milliseconds to seconds:
```
{"placeholder":"calc","values":{"decimal":"true","expression":"{"placeholder":"unix_time"} / 1000"}}
```
Output: `1706371526.543`

Calculate aspect ratio:
```
{"placeholder":"calc","values":{"decimal":"true","expression":"{"placeholder":"guiwidth"} / {"placeholder":"guiheight"}"}}
```
Output: `1.7777777778`

Temperature conversion:
```
{"placeholder":"calc","values":{"decimal":"true","expression":"({"placeholder":"get_variable","values":{"name":"temp_c"}} * 9/5) + 32"}}
```
This converts a temperature from Celsius (stored in a variable) to Fahrenheit.

#### Best Practices

1. **Decimal vs Integer**: Use `"decimal":"true"` when:
   - Working with percentages that need precision
   - Calculating ratios or scaling factors
   - Dealing with financial calculations
   Use `"decimal":"false"` when:
   - Working with whole numbers like counts or pixels
   - Displaying user-facing numbers that shouldn't have decimals
   - Performing integer-based calculations

2. **Parentheses**: Always use parentheses when combining multiple operations to ensure correct order of operations:
```
{"placeholder":"calc","values":{"decimal":"true","expression":"(5 + 3) * 2"}}
```
Instead of:
```
{"placeholder":"calc","values":{"decimal":"true","expression":"5 + 3 * 2"}}
```

3. **Error Handling**: The calculator will return an error if:
   - The expression is invalid
   - Division by zero occurs
   - Invalid function parameters are used
   Always test calculations with extreme values to ensure they work as expected.

### Random Number (`random_number`)
Generates a random number within a specified range.
```
{"placeholder":"random_number","values":{"min":"1","max":"100"}}
```
Example output: `42`

### Max Number (`maxnum`)
Returns the larger of two numbers.
```
{"placeholder":"maxnum","values":{"first":"10","second":"20"}}
```
Example output: `20`

### Min Number (`minnum`)
Returns the smaller of two numbers.
```
{"placeholder":"minnum","values":{"first":"10","second":"20"}}
```
Example output: `10`

### Math Functions
<br>

#### Pi (`math_pi`)
Returns the value of π.
```
{"placeholder":"math_pi"}
```
Example output: `3.141592653589793`

#### Sine (`math_sin`)
Returns the sine of an angle.
```
{"placeholder":"math_sin","values":{"angle":"45"}}
```
Example output: `0.7071067811865476`

#### Cosine (`math_cos`)
Returns the cosine of an angle.
```
{"placeholder":"math_cos","values":{"angle":"45"}}
```
Example output: `0.7071067811865476`

#### Tangent (`math_tan`)
Returns the tangent of an angle.
```
{"placeholder":"math_tan","values":{"angle":"45"}}
```
Example output: `1.0`

## Text Manipulation
<br>

### Split Text (`split_text`)
Splits text using a specified delimiter.
```
{"placeholder":"split_text","values":{"input":"hello,world","regex":",","max_parts":"2","split_index":"1"}}
```
Example output: `world`

### Trim Text (`trim_text`)
Removes leading and trailing whitespace.
```
{"placeholder":"trim_text","values":{"text":"  hello world  "}}
```
Example output: `hello world`

### Crop Text (`crop_text`)
Removes characters from the start and end of text.
```
{"placeholder":"crop_text","values":{"text":"hello world","remove_from_start":"1","remove_from_end":"1"}}
```
Example output: `ello worl`

## Real-time
<br>

### Year (`realtimeyear`)
Returns the current year.
```
{"placeholder":"realtimeyear"}
```
Example output: `2024`

### Month (`realtimemonth`)
Returns the current month (01-12).
```
{"placeholder":"realtimemonth"}
```
Example output: `01`

### Day (`realtimeday`)
Returns the current day of the month (01-31).
```
{"placeholder":"realtimeday"}
```
Example output: `27`

### Hour (`realtimehour`)
Returns the current hour (00-23).
```
{"placeholder":"realtimehour"}
```
Example output: `14`

### Minute (`realtimeminute`)
Returns the current minute (00-59).
```
{"placeholder":"realtimeminute"}
```
Example output: `30`

### Second (`realtimesecond`)
Returns the current second (00-59).
```
{"placeholder":"realtimesecond"}
```
Example output: `45`

## System Information
<br>

### CPU Info (`cpuinfo`)
Returns information about the CPU.
```
{"placeholder":"cpuinfo"}
```
Example output: `Intel(R) Core(TM) i7-10700K CPU @ 3.80GHz`

### GPU Info (`gpuinfo`)
Returns information about the GPU.
```
{"placeholder":"gpuinfo"}
```
Example output: `NVIDIA GeForce RTX 3080`

### Java Version (`javaver`)
Returns the Java version.
```
{"placeholder":"javaver"}
```
Example output: `17.0.2`

### Operating System (`osname`)
Returns the operating system name.
```
{"placeholder":"osname"}
```
Example output: `Windows 10`

## Memory Information
<br>

### Used RAM (`usedram`)
Returns the amount of RAM currently in use (MB).
```
{"placeholder":"usedram"}
```
Example output: `4096`

### Max RAM (`maxram`)
Returns the maximum allocated RAM (MB).
```
{"placeholder":"maxram"}
```
Example output: `8192`

### RAM Usage Percentage (`percentram`)
Returns the percentage of RAM currently in use.
```
{"placeholder":"percentram"}
```
Example output: `50`

## Audio
<br>

### Audio Element Volume (`audio_element_volume`)
Returns the volume of an audio element.
```
{"placeholder":"audio_element_volume","values":{"element_identifier":"background_music"}}
```
Example output: `0.5`

# Practical Examples
<br>

## Creating a Dynamic Memory Display
```
Used RAM: {"placeholder":"usedram"}MB / {"placeholder":"maxram"}MB ({"placeholder":"percentram"}%)
```

## Making a Real-time Clock
```
{"placeholder":"realtimehour"}:{"placeholder":"realtimeminute"}:{"placeholder":"realtimesecond"}
```

## Creating a System Info Display
```
OS: {"placeholder":"osname"}
CPU: {"placeholder":"cpuinfo"}
GPU: {"placeholder":"gpuinfo"}
Java: {"placeholder":"javaver"}
```

## Complex Calculation with Nested Placeholders
```
{"placeholder":"calc","values":{"decimal":"true","expression":"({"placeholder":"usedram"} / {"placeholder":"maxram"}) * 100"}}
```

# Best Practices

1. **Cache Expensive Operations**: Some placeholders (like those that read system information) can be resource-intensive. Consider using variables to store their values if you need to use them multiple times.

2. **Use Appropriate Decimal Settings**: When working with calculations, use the `decimal` parameter appropriately. Set it to `false` when you need integers and `true` when you need precise decimal values.

3. **Handle Missing Values**: Always consider what should happen if a placeholder returns no value. You might want to provide default values in such cases.

4. **Test Performance**: When using many placeholders or complex nested structures, test the performance impact, especially on lower-end systems.

# Common Issues and Solutions
<br>

## Placeholder Not Updating
If a placeholder's value isn't updating as expected, check:
- Whether the placeholder is properly formatted
- If you're using the correct case for placeholder IDs
- Whether the placeholder requires specific conditions to update

## Nested Placeholders Not Working
When nesting placeholders:
- Ensure proper escaping of quotes
- Verify that each nested placeholder is valid on its own
- Check that the total placeholder string length doesn't exceed the maximum limit

## Performance Issues
If you notice performance issues:
- Reduce the number of placeholders used
- Avoid unnecessary nesting
- Consider using variables for frequently accessed values
- Use the appropriate placeholder for your needs (e.g., don't use real-time placeholders when static values would suffice)