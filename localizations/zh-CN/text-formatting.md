---
title: 文本格式
description: 如何使用 Markdown 和 Minecraft 的格式代码来格式化文本。
---
# 文本格式

[文本元素](./elements#text) 支持 Markdown。其他文本字段使用 Minecraft 格式，按钮标签可以使用 Minecraft 文本组件。

# Markdown

FancyMenu 的 **文本元素** 完全支持 Markdown，这意味着你可以通过添加特殊字符来格式化文本内容。

例如，要让文本显示为粗体，你可以在粗体文本前后加上 `**`，因此 `**Some bold text that's very bold.**` 会显示为：
**Some bold text that's very bold.**

FancyMenu 也支持下面文档中提到的扩展语法。

> [!CAUTION]
> Markdown 仅在 **文本元素** 中生效。对于按钮标签和其他文本字段，请使用 [Minecraft 的格式代码](#minecraft-text-formatting)。

## 字体

你可以通过在文本前添加 `%!!<font_name>%`，并在文本后添加 `%!!%`，来使用资源包加载的自定义字体显示文本。

基础游戏中包含的一个有效字体是 `uniform`，因此如果要使用 `uniform` 字体显示文本，请这样写：
`%!!uniform%this is a custom font%!!%`

这将以 `uniform` 字体显示 `this is a custom font`。

## 文本颜色（HEX）

你可以通过在文本前添加 `%<HEX_color>%`，并在文本后添加 `%#%`，来让文本显示为指定的 HEX 颜色。

绿色的有效 HEX 颜色是 `#77fc03`，因此如果要用这种颜色显示文本，请这样写：
`%#77fc03%this text is green!%#%`

这将把 `this text is green!` 显示为 `#77fc03`（绿色）。

请确保 HEX 颜色以 `#` 开头！

同样的颜色格式代码也支持常见的类似 HTML 的颜色名称：

```
%#red%This text is red!%#%
```

支持的名称有：`black`、`silver`、`gray`、`grey`、`white`、`maroon`、`red`、`purple`、`fuchsia`、`magenta`、`green`、`lime`、`olive`、`yellow`、`navy`、`blue`、`teal`、`aqua`、`cyan` 和 `transparent`。

## 文本对齐

你可以通过在某一行开头写入特定的对齐格式代码，然后什么都不写，再写入要以该对齐方式显示的文本行，最后在单独一行再次写入对齐代码，来对齐文本行。

所有文本内容默认都是**左对齐**的，因此这里只有用于**居中**和**右对齐**的格式代码。

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

要让文本右对齐，请使用格式代码 `|||`。

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

在文本前后添加 `**` 可将其显示为**粗体**。

示例：
`**bold text content**`

## 斜体

在文本前后添加 `_` 或 `*` 可将其显示为*斜体*。

示例：
`*italic text content*`

## 删除线

在文本前后添加 `~` 可将其显示为~~删除线~~。

示例：
`~strikethrough text content~`

## 超链接

你可以为文本内容添加超链接，点击后会打开网站。

想要显示为 [超链接](https://google.com) 的文本，需要用 `[ ]` 包裹，再在后面跟上用 `( )` 包裹的实际链接。

因此，如果你想让 `example text content` 可点击并打开 `https://example-website.net`，请这样写：
`[example text content](https://example-website.net)`

## 点击和悬停事件

Markdown 点击和悬停事件可用于 [文本元素](./elements#text) 和其他 Markdown 文本。使用 [**On Markdown Text Clicked**](./listeners#on-markdown-text-clicked-text_clicked) 和 [**On Markdown Text Hovered**](./listeners#on-markdown-text-hovered-text_hovered) 来响应它们。

点击事件使用 `click:` 前缀：

```
[some clickable text](click:unique_text_click_event_id)
```

悬停事件使用 `hover:` 前缀：

```
[some hoverable text](hover:unique_text_hover_event_id)
```

这两个监听器都会将事件 ID 作为 `$$text_event_id` 暴露出来。

## 图片

Markdown 支持在文本内容中显示图片。

FancyMenu 的 Markdown 支持 Minecraft 资源、本地资源和网络资源。

要添加图片，请在文本行开头写入 `![](`，然后写入 [URL、资源位置或资源路径](./resources)，最后写入 `)`。

因此，要显示网络资源 `https://example-website.net/image.png`，请这样写：
`![](https://example-website.net/image.png)`

图片也可以作为**超链接**使用，只需将整行图片文本包裹在一个**超链接**中，如下所示：
`[![](https://example-website.net/image.png)](https://example-website.net)`

> [!WARNING]
> 本地资源必须放在 `<game-directory>/config/fancymenu/assets/` 中！

## 引用

要将文本格式化为引用，请在文本行开头写入 `> `。
这会将其后所有行都格式化为引用，直到遇到一个**空白**行。

示例：
```
This will not look like a quote.

> This will look like a quote.
This will also look like a quote.

This will not look like a quote anymore.
```

## 项目符号列表

要像下面这样显示项目符号列表：
- Entry 1
- Entry 2
  - Sub-Entry

你只需要在某一行开头写入 `- `。

示例：
```
- Entry 1
- Entry 2
  - Sub-Entry
```

## 分隔线

要在文本中添加一条宽度与整行文本相同的分隔线，只需在某一行开头写入 `---`，并且不要再添加其他内容。

它会显示成类似这样：

---

## 代码块

代码块可以帮助你将文本以 `纯文本` 形式显示，而不会被 Markdown 尝试格式化；或者只是以类似代码的样式显示文本，同时避免文本自动换行。

单行代码块（位于其他文本中间）以 \` 开始并以 \` 结束，这在 Markdown 文本里其实很难展示。

包含单行代码块的文本行看起来像这样：

![single_line_code_block](https://github.com/Keksuccino/FancyMenu/assets/35544624/e78fd38b-7b1a-4f00-9b11-797d964b3b43)

多行代码块会将多行内容包裹在一个大的代码块中，格式为：先写一行只包含 \`\`\` 的内容，然后写文本内容，最后再写一次 \`\`\`：

![multi_line_code_block](https://github.com/Keksuccino/FancyMenu/assets/35544624/bf8c77eb-a97e-48cd-9270-8302c2995856) 

## 纯文本

纯文本格式代码会绕过其中所有其他格式代码。

它的工作方式类似于代码块，但不会把内容格式化成代码块样式。相反，它会像普通文本一样显示，但不应用任何格式。

要在一行文本中把某一部分包裹进纯文本格式代码，需要像这样在你想显示为纯文本的部分前后添加 `;;`：

```
This is a line of text with ;;**this part**;; showing as unformatted text with visible ** (bold) formatting code and _this part_ as normal formatted italic text.
```

纯文本也支持多行包裹代码。要包裹整行，请在你想显示为纯文本的行前后添加 `;;;`，如下所示：

```
;;;
This line will show **unformatted** with visible ** (bold) formatting codes.
This line will also show _unformatted_ with visible _ (italic) formatting codes.
;;;

This line will look **normal** again with the "normal" formatted as bold text.
```

# Minecraft 文本格式

Minecraft 格式代码可用于 FancyMenu 中支持格式化的文本字段。使用 `&` 代替 Minecraft 的 `§` 前缀；例如，`&cWarning` 会显示红色文本。

可用颜色和样式请参阅 [Minecraft Wiki 格式代码参考](https://minecraft.wiki/w/Formatting_codes)。

> [!CAUTION]
> 由于 **文本元素** 会解析 Markdown，因此 Minecraft 格式代码在这些元素中并不可靠。请改用上面介绍的 Markdown 格式。

# Minecraft 文本组件（原始组件系统）

Minecraft 的文本组件系统对于像**按钮标签**这样的**单行**文本内容非常强大。

在原版 Minecraft 中，你可以在 `/tellraw` 和 `/title` 命令中使用它（也许在其他地方也能用）。
它是以 JSON 序列化的格式化文本，因此你可以为文本内容添加格式属性。

要更详细地了解文本组件，请查看 [这个 Minecraft Wiki 页面](https://minecraft.wiki/w/Raw_JSON_text_format)。
要了解 Minecraft 中的字体，请查看 [这个 Minecraft Wiki 页面](https://minecraft.wiki/w/Resource_pack#Fonts)。

要让 FancyMenu 将按钮标签识别为**文本组件**，标签内容只需填写序列化后的组件文本，就像这样：
`{"text":"Button Label Text","font":"uniform"}`

上面的示例会以 `uniform` 字体显示按钮标签 `Button Label Text`。

> [!NOTE]
> 你可以在组件的 `text` 值中使用 FancyMenu 的占位符。
