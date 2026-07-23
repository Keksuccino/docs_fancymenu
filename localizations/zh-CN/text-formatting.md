---
title: 文本格式化
description: 如何使用 Markdown 和 Minecraft 的格式化代码来格式化文本。
---
# 文本格式化

[文本元素](./elements#text) 支持 Markdown。其他文本字段使用 Minecraft 格式化，而按钮标签可以使用 Minecraft 文本组件。

# Markdown

FancyMenu 的 **文本元素** 完整支持 Markdown，这意味着你可以通过添加特殊字符来格式化文本内容。

例如，要让文本看起来加粗，只需在加粗文本前后添加 `**`，因此 `**Some bold text that's very bold.**` 会显示为：
**Some bold text that's very bold.**

FancyMenu 还支持下面文档中说明的扩展功能。

> Markdown 仅适用于 **文本元素**。对于按钮标签和其他文本字段，请使用 [Minecraft 的格式化代码](#minecraft-文本格式化)。
{.is-danger}

## 字体

你可以通过在文本前添加 `%!!<font_name>%`，并在文本后添加 `%!!%`，来使用资源包加载的自定义字体显示文本。

基础游戏中包含的有效字体之一是 `uniform`，因此若要使用 `uniform` 字体显示文本，请这样做：
`%!!uniform%这是自定义字体%!!%`

这将以 `uniform` 字体显示 `这是自定义字体`。

## 文本颜色（HEX）

可以通过在文本前添加 `%<HEX_color>%`，并在文本后添加 `%#%`，来以指定的 HEX 颜色显示文本。

绿色的有效 HEX 颜色是 `#77fc03`，因此若要以此颜色显示文本，请这样做：
`%#77fc03%这段文本是绿色的！%#%`

这将把 `这段文本是绿色的！` 显示为 `#77fc03`（绿色）。

请确保 HEX 颜色以 `#` 开头！

同样的颜色格式代码也支持常见的类似 HTML 的颜色名称：

```
%#red%这段文本是红色的！%#%
```

支持的名称：`black`、`silver`、`gray`、`grey`、`white`、`maroon`、`red`、`purple`、`fuchsia`、`magenta`、`green`、`lime`、`olive`、`yellow`、`navy`、`blue`、`teal`、`aqua`、`cyan` 和 `transparent`。

## 文本对齐

你可以通过在某一行的开头写入特定的对齐格式代码，然后什么都不写，再写入你想以该对齐方式显示的文本行，最后在另一行再次写入该对齐代码，来对齐文本行。

所有文本内容默认都是**左对齐**，因此只有**居中**和**右对齐**的格式代码。

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

要将**一行文本**显示为标题（更大并带下划线），在文本行前加上 `# `（超大）、`## `（大）或 `### `（小）。

示例：
`## 大标题`

## 加粗

在文本前后添加 `**` 可使其看起来**加粗**。

示例：
`**加粗文本内容**`

## 斜体

在文本前后添加 `_` 或 `*` 可使其看起来 *斜体*。

示例：
`*斜体文本内容*`

## 删除线

在文本前后添加 `~` 可使其看起来 ~~带删除线~~。

示例：
`~带删除线的文本内容~`

## 超链接

你可以为文本内容添加超链接，点击后会打开一个网站。

想要显示为 [超链接](https://google.com) 的文本，需要将其包裹在 `[ ]` 中，后面跟上实际链接，并将链接包裹在 `( )` 中。

因此，如果你想让 `example text content` 可点击并打开 `https://example-website.net`，请这样做：
`[example text content](https://example-website.net)`

## 点击与悬停事件

Markdown 点击和悬停事件适用于 [文本元素](./elements#text) 和其他 Markdown 文本。使用 [**Markdown 文本被点击时**](./listeners#on-markdown-text-clicked) 和 [**Markdown 文本被悬停时**](./listeners#on-markdown-text-hovered) 来响应它们。

点击事件使用 `click:` 前缀：

```
[some clickable text](click:unique_text_click_event_id)
```

悬停事件使用 `hover:` 前缀：

```
[some hoverable text](hover:unique_text_hover_event_id)
```

这两个监听器都会将事件 ID 以 `$$text_event_id` 的形式暴露出来。

## 图片

Markdown 支持在文本内容中显示图片。

FancyMenu 在 Markdown 中支持 Minecraft 资源、本地资源和网络资源。

要添加图片，请以 `![](` 开始一行文本，然后写入 [URL、资源位置或资源路径](./resources)，最后写入 `)`。

例如，要显示网络资源 `https://example-website.net/image.png`，请这样做：
`![](https://example-website.net/image.png)`

图片也可以作为**超链接**，只需将整行图片文本包裹在**超链接**中即可：
`[![](https://example-website.net/image.png)](https://example-website.net)`

> 本地资源必须放在 `<game-directory>/config/fancymenu/assets/` 中！
{.is-warning}

## 引用

要将文本格式化为引用，请以 `> ` 开始一行文本。
这会将后续所有行格式化为引用，直到遇到一行**空行**为止。

示例：
```
This will not look like a quote.

> This will look like a quote.
This will also look like a quote.

This will not look like a quote anymore.
```

## 项目符号列表

要将文本显示为如下项目符号列表：
- Entry 1
- Entry 2
  - Sub-Entry

你只需要在一行开头写 `- `。

示例：
```
- Entry 1
- Entry 2
  - Sub-Entry
```

## 分隔线

要为文本添加一条与整行文本宽度相同的分隔线，只需以 `---` 开始一行，然后不再添加其他内容。

它看起来会像这样：

---

## 代码块

代码块可以帮助你将文本以 `纯文本` 形式显示，而不会被 Markdown 尝试格式化；也可以用于以类似代码的样式显示文本，而不会自动换行。

单行代码块（位于其他文本之间）以 \` 开始和结束，这在 Markdown 文本中其实很难展示出来。

包含单行代码块的文本行看起来像这样：

![single_line_code_block](https://github.com/Keksuccino/FancyMenu/assets/35544624/e78fd38b-7b1a-4f00-9b11-797d964b3b43)

多行代码块会将多行内容包裹在一个大的代码块中，并以一行只包含 \`\`\` 的内容开始，然后是文本内容，最后再次以 \`\`\` 结束：

![multi_line_code_block](https://github.com/Keksuccino/FancyMenu/assets/35544624/bf8c77eb-a97e-48cd-9270-8302c2995856) 

## 纯文本

纯文本格式化代码会绕过其中的所有其他格式化代码。

它的工作方式类似于代码块，但不会将其显示为代码块样式。相反，它会像普通文本一样显示，但不会有任何格式化效果。

要在一行中的某个文本片段外包裹纯文本格式化代码，需要在你想显示为纯文本的文本片段前后添加 `;;`，如下所示：

```
This is a line of text with ;;**this part**;; showing as unformatted text with visible ** (bold) formatting code and _this part_ as normal formatted italic text.
```

纯文本也可作为多行包裹代码使用。要包裹整行内容，请在你想显示为纯文本的行前后添加 `;;;`，如下所示：

```
;;;
This line will show **unformatted** with visible ** (bold) formatting codes.
This line will also show _unformatted_ with visible _ (italic) formatting codes.
;;;

This line will look **normal** again with the "normal" formatted as bold text.
```

# Minecraft 文本格式化

Minecraft 本身有一套相当不错的格式化系统，工作方式类似于 Markdown，你可以通过向文本内容添加特殊字符来进行格式化。

要进一步了解 Minecraft 的格式化系统，请查看 [这个 Minecraft Wiki 页面](https://minecraft.wiki/w/Formatting_codes)。

> Wiki 上会写格式化代码前缀是 `§`，但在 FancyMenu 中你需要把它替换为 `&`。其他内容保持不变。
{.is-warning}

> **文本元素** 非常复杂，而为了支持 Markdown，代价是**破坏了 Minecraft 原版的格式化代码**，所以这些代码在文本元素中不会很好地工作（例如只有第一个单词会在格式化代码后被格式化等）。你应该在文本元素中改用 Markdown 格式化代码。
{.is-danger}

# Minecraft 文本组件（原始组件系统）

Minecraft 的文本组件系统非常强大，适合用于**单行**文本内容，例如**按钮标签**。

在原版 Minecraft 中，你可以在 `/tellraw` 和 `/title` 命令中使用它（以及可能的其他地方）。
它是将格式化文本序列化为 JSON，因此你可以为文本内容添加格式化属性。

要更详细地了解文本组件，请查看 [这个 Minecraft Wiki 页面](https://minecraft.wiki/w/Raw_JSON_text_format)。
要了解 Minecraft 中的字体，请查看 [这个 Minecraft Wiki 页面](https://minecraft.wiki/w/Resource_pack#Fonts)。

要让 FancyMenu 将按钮标签识别为**文本组件**，只需将序列化后的组件文本原样设置为标签，就像这样：
`{"text":"Button Label Text","font":"uniform"}`

上面的示例会以 `uniform` 字体显示按钮标签 `Button Label Text`。

> 你可以在组件的 `text` 值中使用 FancyMenu 的占位符。
{.is-info}
