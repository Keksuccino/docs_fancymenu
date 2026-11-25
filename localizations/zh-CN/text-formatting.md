---
title: 文本格式
description: 了解如何使用 Markdown、Minecraft 格式代码和文本组件来设置文本格式。
sourceBlobSha: c6ddde5939e929b3d4c04541f0b104ee6ee795bc
---
# 文本格式

FancyMenu 提供三种文本格式设置方式：

- **Markdown**：适用于[文本和工具提示元素](/text-in-menus)，可设置标题、列表、颜色、图片、表格等。
- **Minecraft 格式代码**：例如 `&c`，可快速设置颜色。它们适用于几乎所有文本字段，包括 Markdown 文本。
- **Minecraft 文本组件**：适用于按钮和滑块标签。

> [!TIP]
> 本页重点介绍*如何编写*格式化文本。若要了解如何在菜单中添加文本、修改文本外观或让文本滚动，请参阅[菜单中的文本](/text-in-menus)。

<img width="800" alt="文本元素中的 Markdown" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/markdown_showcase.png?raw=true">

# Markdown

Markdown 通过在文本两侧添加一些特殊字符来设置格式。例如，`**粗体**` 会显示为 **粗体** 文本。

Markdown 适用于[文本元素](/elements#text)和[工具提示元素](/elements#tooltip)。你编写的字符决定了内容的*类型*（标题、列表、引用等），而元素的[外观](/text-in-menus#looks-and-styles)决定了它的显示效果，例如颜色和大小。

## 快速概览

| 你输入的内容 | 显示效果 |
|---|---|
| `**粗体**` 或 `__粗体__` | 粗体文本 |
| `*斜体*` 或 `_斜体_` | 斜体文本 |
| `++下划线++` | 带下划线的文本 |
| `~~删除线~~` | 带删除线的文本 |
| `` `代码` `` | 行内代码 |
| `[打开网站](https://example.com)` | 可点击的链接 |
| `%#ff5555%红色文本%#%` | 彩色文本 |
| `# 标题` | 标题 |
| `- 项目` | 项目符号列表 |
| `1. 项目` | 编号列表 |
| `> 文本` | 引用 |
| `> [!TIP]` | 提示框 |
| `---` | 分隔线 |

## 文本样式

| 样式 | 编写方式 |
|---|---|
| **粗体** | `**文本**` 或 `__文本__` |
| **斜体** | `*文本*` 或 `_文本_` |
| **下划线** | `++文本++` |
| **删除线** | `~~文本~~`（两侧各用一个 `~` 也可以） |

样式可以组合使用，例如 `***粗体和斜体***`。

单词内部的单个下划线会保留为普通下划线，因此 `my_cool_layout` 不会变成斜体。像 `C++` 这样的名称也会保持原样。

> [!TIP]
> 在文本编辑器中选中一些文本，然后按 `Ctrl + B`、`Ctrl + I` 或 `Ctrl + U`（macOS 上按 `Cmd`），即可将其设为粗体、斜体或添加下划线。请参阅[格式设置快捷键](/text-in-menus#formatting-shortcuts)。

## 文本颜色（HEX）

在文本前加上 `%<HEX 颜色值>%`，并在文本后加上 `%#%`：

```
%#77fc03%这段文字是绿色的！%#%
```

HEX 颜色值必须以 `#` 开头。你也可以使用颜色名称：

```
%#red%这段文字是红色的！%#%
```

支持的颜色名称：`black`、`silver`、`gray`、`grey`、`white`、`maroon`、`red`、`purple`、`fuchsia`、`magenta`、`green`、`lime`、`olive`、`yellow`、`navy`、`blue`、`teal`、`aqua`、`cyan` 和 `transparent`。

## 字体

若要使用其他字体显示文本，请在文本前加上 `%!!<字体名称>%`，并在文本后加上 `%!!%`。字体可以来自 Minecraft 或资源包。

```
%!!uniform%这段文字使用 uniform 字体%!!%
```

## 文本对齐

文本默认左对齐。若要将文本行居中或右对齐，请在文本行前后各单独放置一行对齐代码：

- `^^^` 将文本行居中。
- `|||` 将文本行右对齐。

```
这一行左对齐。

^^^
这一行居中。
这一行也居中。
^^^

|||
这一行右对齐。
|||
```

> [!TIP]
> 在文本编辑器中，按 `Ctrl + L`、`Ctrl + E` 和 `Ctrl + R`（macOS 上按 `Cmd`），即可将选中的文本行分别设为左对齐、居中或右对齐。

## 标题

在行首输入 `# `（最大）、`## `（较大）或 `### `（较小）：

```
# 欢迎！
## 新闻
### 小标题
```

## 列表

<img width="460" alt="Markdown 列表" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/markdown_lists.png?raw=true">

### 项目符号列表

在行首输入 `- `。每增加一级嵌套，就在前面多加两个空格：

```
- 第一个项目
- 第二个项目
  - 嵌套项目
    - 更深一层
```

### 编号列表

在行首输入一个数字，再加句点或右括号：

```
1. 打开菜单栏
2. 点击“自定义”
3) 这样写也可以
```

### 更新日志标记

行首也可以使用 `+`、`-`、`~` 或 `*`。每种符号都会显示为各自的标记，非常适合用于补丁说明和更新日志：

```
+ 新增了一个主菜单
- 移除了旧版徽标
~ 修改了按钮颜色
* 修复了启动时崩溃的问题
```

| 标记 | 含义 |
|---|---|
| `+` | 添加了内容 |
| `-` | 移除了内容 |
| `~` | 修改了内容 |
| `*` | 值得特别说明的内容 |

只有当同一列表中也有 `+` 项目时，`-` 项目才会显示为“已移除”标记。否则，它会被视为普通的项目符号列表项。你可以通过 **Markdown -> Lists -> Extra Markers (+ - ~ \*) -> - Marker Used** 更改此设置。

> [!NOTE]
> 新建的文本和工具提示元素默认启用编号列表、更新日志标记和[提示框](#callouts)。旧版布局中的元素默认关闭这些功能，以免文本突然发生变化。你可以在元素的 **Markdown** 菜单中启用这些功能：**Lists -> Numbered Lists**、**Lists -> Extra Markers (+ - ~ \*)** 和 **Callouts**。

## 引用

在行首输入 `> ` 即可创建引用。引用会一直延续到下一个空行：

```
> 这是一段引用。
这一行也属于引用。

这一行恢复为普通文本。
```

引用中的行也可以用 `>` 开头；只包含 `>` 的行会在引用中添加一个空行：

```
> 引用的第一段。
>
> 引用的第二段。
```

## 提示框

提示框是带有图标和标签的彩色方框，非常适合显示提示和警告。输入一段引用，并将提示框类型放在第一行：

```
> [!WARNING]
> 别忘了保存布局！
```

<img width="640" alt="Markdown 提示框" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/markdown_callouts.png?raw=true">

提示框共有五种类型：`[!NOTE]`、`[!TIP]`、`[!IMPORTANT]`、`[!WARNING]` 和 `[!CAUTION]`。

## 超链接

将文本用 `[ ]` 括起来，并在后面的 `( )` 中填写链接：

```
[访问我们的网站](https://example.com)
```

链接中可以包含圆括号，例如 `https://en.wikipedia.org/wiki/Minecraft_(video_game)`。若要在链接文本中显示方括号，请在方括号前加上 `\`：`[点击\[此处\]](https://example.com)`。

## 点击和悬停事件

文本也可以触发[监听器](/listeners)，而不是打开网站。在链接前使用 `click:` 或 `hover:` 前缀，并为其指定一个 ID：

```
[一些可点击的文本](click:unique_text_click_event_id)
[一些悬停时可触发的文本](hover:unique_text_hover_event_id)
```

使用[**Markdown 文本被点击时**](/listeners#on-markdown-text-clicked)和[**鼠标悬停在 Markdown 文本上时**](/listeners#on-markdown-text-hovered)监听器来响应这些事件。两者都会将 ID 作为 `$$text_event_id` 提供给你。

## 图片

使用 `![](` + 图片来源 + `)`，将图片单独放在一行：

```
![](https://example.com/image.png)
```

图片来源可以是网址、本地文件（例如 `/config/fancymenu/assets/image.png`），也可以是资源包中的图片。所有来源类型请参阅[资源](/resources)。

方括号中的文本会成为图片说明：

```
![我的精彩截图](/config/fancymenu/assets/screenshot.png)
```

启用元素的 **Markdown -> Images -> Caption** 选项后，图片说明会显示在图片下方。

若要让图片可点击，请将图片嵌套在链接中：

```
[![](https://example.com/image.png)](https://example.com)
```

## 表格

使用 `|` 分隔单元格。第一行为表头，第二行则需为每一列填写 `---`：

```
| 物品 | 价格 |
|:---|---:|
| 钻石剑 | 10 |
| 金苹果 | 5 |
```

第二行中的冒号用于设置列对齐方式：`:---` 表示左对齐，`:---:` 表示居中对齐，`---:` 表示右对齐。若要在单元格中显示 `|`，请写作 `\|`。

<img width="640" alt="Markdown 表格和代码" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/markdown_table_code.png?raw=true">

## 分隔线

单独一行只写 `---`，即可在文本中绘制分隔线。

## 代码

代码会原样显示文本，不对其进行格式化。

- **行内代码：** 用 `` ` `` 包住一行中的部分文本，例如 `` `/spawn` ``。
- **代码块：** 在文本行前后各单独放置一行 `` ``` ``。代码块中的文本不会自动换行。

````
```
/give @p minecraft:diamond 64
```
````

你可以在开头的 `` ``` `` 后面写上语言名称，例如 `` ```json ``。FancyMenu 接受这种写法，但不会因此改变代码的显示效果。

[占位符](/placeholders)在代码中仍会被替换。

## 纯文本

纯文本会显示格式标记本身，但不会采用代码的样式。将一行中的部分文本用 `;;` 包住：

```
这里会显示 ;;**星号**;;，而不是粗体文本。
```

若要对整行文本使用此效果，请在文本前后各单独放置一行 `;;;`：

```
;;;
**不是粗体**，_也不是斜体_。
;;;
```

## 转义字符

若要将格式字符显示为普通文本，请在其前面加上 `\`。例如，`\*不是斜体\*` 会显示为 `*不是斜体*`。

此方法适用于 `\` `` ` `` `*` `_` `{` `}` `[` `]` `(` `)` `#` `+` `-` `.` `!` `|` `>` `~` 和 `^`。

# Minecraft 文本格式

Minecraft 格式代码适用于 FancyMenu 中的大多数文本字段。请使用 `&` 代替 Minecraft 的 `§`。例如，`&c警告` 会显示为红色文本，而 `&l` 会将文本设为粗体。`&r` 会重置格式。

所有代码请参阅 [Minecraft Wiki](https://minecraft.wiki/w/Formatting_codes)。

格式代码也适用于 Markdown 文本，但在代码和纯文本中无效。对于粗体和斜体等样式，Markdown 通常更易读；而格式代码则适合快速设置颜色。

# Minecraft 文本组件（原始组件系统）

Minecraft 文本组件是以 JSON 编写的格式化文本。它们适用于**单行**文本，例如**按钮和滑块标签**，但不适用于文本元素。

若要使用文本组件，请将标签内容设置为仅包含组件：

```
{"text":"按钮标签文本","font":"uniform"}
```

这会使用 `uniform` 字体显示“按钮标签文本”。你可以在 `text` 值中使用[占位符](/placeholders)。

若要了解更多信息，请参阅 Minecraft Wiki 上关于[文本组件格式](https://minecraft.wiki/w/Raw_JSON_text_format)和[字体](https://minecraft.wiki/w/Resource_pack#Fonts)的页面。
