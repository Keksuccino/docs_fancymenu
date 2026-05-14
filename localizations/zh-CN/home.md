---
title: 入门指南
description: FancyMenu 的世界正在等待你！这是一段美好旅程的开始！
---

# 面向开发者

如果你是开发者，并且想为 FancyMenu 制作附属组件，或者在你的模组中集成 FancyMenu，请查看 [开发者文档](https://github.com/Keksuccino/FancyMenu-Dev-Docs/wiki)。

# 入门指南

第一次使用 FancyMenu 可能会让人有点不知所措，但别担心，一旦你开始上手，大部分内容其实都非常直观易懂！

> 请 **注意**，本页面只是帮助你初步了解 FancyMenu，并指导你完成 **第一步**。
请务必也查看文档的其他部分，以获取关于 FancyMenu 功能更详细的信息！
{.is-info}

# 菜单栏

启动游戏后，你首先会注意到的其中一项就是每个菜单顶部的 **菜单栏**。

**菜单栏**是你进入 FancyMenu 几乎所有功能的入口，比如 **创建布局** 来 **自定义菜单**、更改 **窗口标题和图标** 等等。

> 如果你不小心按到了某些键，导致 **菜单栏消失了**，你可以按 **CTRL + ALT + C** 将其重新显示。
{.is-warning}

<img width="650" alt="menu_bar" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/menu_bar.png?raw=true">

# 你的第一个布局

既然你大概率是想自定义 Minecraft 的菜单，那我就来讲讲 **布局** 吧！

布局就像是菜单的自定义层，它们允许你添加新元素并自定义已有元素。

要为 **特定菜单** 创建一个新布局：
1. 打开你想要创建布局的菜单（例如标题界面）
2. 打开 **菜单栏** 的 **自定义** 选项卡

默认情况下，所有菜单的自定义都是关闭的，你需要为每个想要自定义的菜单单独启用它。所以先点击 **“当前界面自定义：已禁用”** 这一项，它会把开关切换为 **已启用**。

<img width="475" alt="toggle_customizations" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/toggle_customizations.png?raw=true">

完成后，点击 **Layouts -> New -> For Current Screen**。

这将打开 **布局编辑器**，你可以在其中向布局添加元素，并自定义原版和模组元素（比如按钮）。

<img width="550" alt="new_layout_current" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/new_layout_current.png?raw=true">

## 编辑布局

大多数自定义选项都可以通过 **右键单击编辑器背景** 来访问。
这样会打开一个上下文菜单，里面有很多选项，例如自定义 **菜单背景** 或向布局中 **添加元素**。

<br>
<img width="350" alt="context_menu" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/context_menu.png?raw=true">

## 向布局添加元素

要向布局添加新元素，请 **右键单击** 编辑器背景。

在弹出的上下文菜单中，点击 **New Element**，然后选择众多元素类型中的一种。

<img width="525" alt="add_element" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/add_element.png?raw=true">

## 自定义元素

要自定义某个元素，请 **右键单击** 它，这将打开一个上下文菜单，里面包含该元素类型可供你自定义的所有内容。

除了你添加的元素之外，你也可以自定义原版元素（不过它们有时可用选项会更少）

<img width="525" alt="element_customization" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/element_customization.png?raw=true">

> [!IMPORTANT]
> 像这样的某些上下文菜单是 **可滚动** 的！

## 定位元素

FancyMenu 中的每个元素都与一个 **锚点** 相关联。

锚点对于计算元素位置是必需的，并且如果使用得当，它们可以防止元素互相重叠、移出屏幕，或在调整窗口大小时移动到错误的位置。

它们是计算元素位置的起点。

默认情况下，元素会连接到 **“屏幕中心”** 锚点，这基本上就是屏幕的正中心，不受窗口大小影响。
所以假设一个元素连接到 **“屏幕中心”** 锚点，并且距离屏幕中心 2 厘米。那么无论窗口大小如何，这个元素都将 **始终** 距离屏幕中心 2 厘米。

当你拖动元素时，可以看到它所连接的锚点。此时（默认情况下）也会显示所有其他锚点。你可以在拖动元素时悬停在某个锚点上，将该元素的锚点切换为你悬停的那个锚点。

你甚至可以把一个元素用作其他元素的锚点！只需在拖动另一个元素时悬停在某个元素上，被拖动元素的锚点就会更改为你悬停的那个元素。

**[了解更多关于如何定位元素的信息。](/positioning-elements)**

<img width="650" alt="anchor_points" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/anchor_points.png?raw=true">

## 保存你的成果

别忘了保存你的杰作！

如果你在关闭之前需要保存更改，编辑器右上角会显示一个“未保存的更改”提示。

点击 **Layout -> Save** 即可保存你的工作！

<img width="375" alt="save_your_work" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/save_your_work.png?raw=true">

> [!TIP]
> 你也可以使用键盘快捷键 **CTRL + S** 来保存你的工作

*恭喜你！现在你已经可以让 Minecraft 的菜单看起来更加漂亮了！*
