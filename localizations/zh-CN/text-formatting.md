---
title: 文本格式化
description: 如何使用 Markdown 和 Minecraft 的格式化代码来格式化文本。
---

# 文本格式化

FancyMenu 有很多功能，可以让布局中的文本内容变得 *更花哨*！

文本元素完全支持 **Markdown**，并带有一些很酷的扩展；而且大多数其他文本内容都支持 **Minecraft 的文本格式化** 系统，按钮标签甚至还支持 **Minecraft 文本组件**，让你可以使用自定义字体等更多功能。

# Markdown

FancyMenu 的 **文本元素** 完全支持 Markdown，这意味着你可以通过添加特殊字符来格式化文本内容。

例如，要让文本变成粗体，你可以在粗体文本前后加上 `**`，所以 `**Some bold text that's very bold.**` 会显示为这样：
**Some bold text that's very bold.**

FancyMenu 的 Markdown 甚至还有一些特殊功能，让它更加强大！

> Markdown **不适用于** 其他基于文本的内容，例如按钮标签。它只对 **文本元素** 有效。对于其他所有内容，请使用 [Minecraft 的格式化代码](/text-formatting#minecraft-text-formatting)。
{.is-danger}

## 字体

你可以通过在文本前添加 `%!!<font_name>%`，并在文本后添加 `%!!%` 来显示资源包中加载的自定义字体。

基础游戏中一个有效的字体是 `uniform`，因此如果要使用 `uniform` 字体显示文本，可以这样写：
`%!!uniform%this is a custom font%!!%`

这将以 `uniform` 字体显示 `this is a custom font`。

## 文本颜色（HEX）

你可以通过在文本前添加 `%<HEX_color>%`，并在文本后添加 `%#%` 来显示指定 HEX 颜色的文本。

绿色的有效 HEX 颜色是 `#77fc03`，因此如果要以这种颜色显示文本，可以这样写：
`%#77fc03%this text is green!%#%`

这会将 `this text is green!` 显示为 `#77fc03`（绿色）。

请确保 HEX 颜色以 `#` 开头！

FancyMenu 3.9.0 还在这个相同的颜色格式代码中支持常见的、类似 HTML 的颜色名称：

```
%#red%This text is red!%#%
```

支持的名称有：`black`、`silver`、`gray`、`grey`、`white`、`maroon`、`red`、`purple`、`fuchsia`、`magenta`、`green`、`lime`、`olive`、`yellow`、`navy`、`blue`、`teal`、`aqua`、`cyan` 和 `transparent`。

## 文本对齐

你可以通过在某一行开头写入特定的对齐格式代码，接着写入你想以该对齐方式显示的文本行，然后在另一空行中再次写入该对齐代码，来对齐文本行。

所有文本内容默认都是 **左对齐**，因此这里只有 **居中** 和 **右对齐** 的格式代码。

### 居中

要让文本居中，请使用格式代码 `^^^`。

示例：
```
This text is not centered.

^^^
This text is centered.
This text is also centered.
^^^

This text is not centered anymore.
```

### 右对齐

要将文本显示为右对齐，请使用格式代码 `|||`。

示例：
```
This text is not right-aligned.

|||
This text is right-aligned.
This text is also right-aligned.
|||

This text is not right-aligned anymore.
```

## 标题

要将**一行文本**显示为标题（更大并带下划线），请在文本行前添加 `# `（非常大）、`## `（大）或 `### `（小）。

示例：
`## Big Headline`

## 粗体

在文本前后添加 `**` 可以让它显示为 **粗体**。

示例：
`**bold text content**`

## 斜体

在文本前后添加 `_` 或 `*` 可以让它显示为 *斜体*。

示例：
`*italic text content*`

## 删除线

在文本前后添加 `~` 可以让它显示为 ~~删除线~~。

示例：
`~strikethrough text content~`

## 超链接

你可以为文本内容添加超链接，点击后会打开一个网站。

要显示为 [超链接](https://google.com) 的文本，需要将其包在 `[ ]` 中，后面跟上实际链接，并用 `( )` 包裹。

所以如果你想让 `example text content` 可点击，并打开 `https://example-website.net`，可以这样写：
`[example text content](https://example-website.net)`

## 点击和悬停事件

FancyMenu 3.9.0 为文本元素和其他 Markdown 文本添加了 Markdown 点击和悬停事件。

点击事件使用 `click:` 前缀：

```
[some clickable text](click:unique_text_click_event_id)
```

悬停事件使用 `hover:` 前缀：

```
[some hoverable text](hover:unique_text_hover_event_id)
```

使用 **On Markdown Text Clicked** 和 **On Markdown Text Hovered** 监听器来响应这些事件。两个监听器都会将事件 ID 作为 `$$text_event_id` 公开。

## 图片

Markdown 支持在文本内容中显示图片。

FancyMenu 支持在 Markdown 中使用 Minecraft 资源、本地资源和网页资源。

要添加图片，请以 `![](` 开头写一行文本，然后写入 [URL、资源位置或资源路径](/resources)，最后加上 `)`。

例如，要显示网页资源 `https://example-website.net/image.png`，可以这样写：
`![](https://example-website.net/image.png)`

图片也可以作为**超链接**，只需像这样将整行图片文本包在**超链接**中：
`[![](https://example-website.net/image.png)](https://example-website.net)`

> 本地资源需要放在 `/config/fancymenu/assets/` 中！
{.is-warning}

## 引用

要将文本格式化为引用，请在文本行前添加 `> `。
这会将后续所有行都格式化为引用，直到遇到一行**空行**为止。

示例：
```
This will not look like a quote.

> This will look like a quote.
This will also look like a quote.

This will not look like a quote anymore.
```

## 项目符号列表

要将文本显示为如下的项目符号列表：
- Entry 1
- Entry 2
  - Sub-Entry

你只需要在一行开头添加 `- `。

示例：
```
- Entry 1
- Entry 2
  - Sub-Entry
```

## 分隔线

要为文本添加一条与整行文本同宽的分隔线，只需在一行开头添加 `---`，然后不要再添加其他内容。

效果大致如下：

---

## 代码块

代码块可以帮助你将文本显示为 `纯文本`，而不会被 Markdown 进行格式化；或者只是以类似代码的样式显示文本，并且不自动换行。

单行代码块（位于其他文本中间）以 \` 开始和结束，这实际上在 Markdown 文本中非常难展示。

包含单行代码块的一行文本看起来像这样：

![single_line_code_block](https://github.com/Keksuccino/FancyMenu/assets/35544624/e78fd38b-7b1a-4f00-9b11-797d964b3b43)

多行代码块会将多行内容包裹在一个大代码块中，并以只包含 \`\`\` 的一行开始，然后写入文本内容，再以 \`\`\` 结束：

![multi_line_code_block](https://github.com/Keksuccino/FancyMenu/assets/35544624/bf8c77eb-a97e-48cd-9270-8302c2995856) 

## 纯文本

纯文本格式代码会绕过其中所有其他格式代码。

它的工作方式类似于代码块，但不会把它显示成代码块样式。相反，它会像普通文本一样显示，但不带任何格式。

要在一行中把一部分文本包裹到纯文本格式代码中，你需要在想要显示为纯文本的文本前后添加 `;;`，例如：

```
This is a line of text with ;;**this part**;; showing as unformatted text with visible ** (bold) formatting code and _this part_ as normal formatted italic text.
```

纯文本也支持多行包裹代码。要包裹整行，请在你想显示为纯文本的行前后添加 `;;;`，例如：

```
;;;
This line will show **unformatted** with visible ** (bold) formatting codes.
This line will also show _unformatted_ with visible _ (italic) formatting codes.
;;;

This line will look **normal** again with the "normal" formatted as bold text.
```

# Minecraft 文本格式化

Minecraft 本身有一套相当不错的格式化系统，它的工作方式类似于 Markdown，你可以通过在文本内容中添加特殊字符来进行格式化。

要进一步了解 Minecraft 的格式化系统，请查看 [这个 Minecraft wiki 页面](https://minecraft.wiki/w/Formatting_codes)。

> 维基会写格式化代码前缀是 `§`，但在 FancyMenu 中你需要把它替换为 `&`。其他内容保持不变。
{.is-warning}

> **文本元素** 非常复杂，而为了支持 Markdown，代价是 **破坏了 Minecraft 原版格式化代码**，所以这些代码在文本元素中不会很好用（例如只会在格式化代码后面的第一个单词生效等）。你应该在文本元素中改用 Markdown 格式化代码。
{.is-danger}

# Minecraft 文本组件（原始组件系统）

Minecraft 的文本组件系统非常强大，适合用于 **单行** 文本内容，例如 **按钮标签**。

在原版 Minecraft 中，你可以在 `/tellraw` 和 `/title` 命令中使用它（以及其他可能的地方）。
它是以 JSON 序列化的格式化文本，因此你可以为文本内容添加格式属性。

要详细了解文本组件，请查看 [这个 Minecraft wiki 页面](https://minecraft.wiki/w/Raw_JSON_text_format)。
要了解 Minecraft 中的字体，请查看 [这个 Minecraft wiki 页面](https://minecraft.wiki/w/Resource_pack#Fonts)。

要让 FancyMenu 将按钮标签识别为 **文本组件**，只需把序列化后的组件文本直接作为标签即可，就像这样：
`{"text":"Button Label Text","font":"uniform"}`

上面的示例会以 `uniform` 字体显示按钮标签 `Button Label Text`。

> 你可以在组件的 `text` 值中使用 FancyMenu 的占位符。
{.is-info}
