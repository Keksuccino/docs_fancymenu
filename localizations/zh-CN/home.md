---
title: 入门指南
description: 开始使用 FancyMenu 的第一步。了解菜单栏、从头到尾制作你的第一个布局，以及接下来可以做什么。
sourceBlobSha: 0a9f8343e6964d75860fb6143e9b6fdecb6cf0ea
---

# 入门指南

FancyMenu 可以让你修改 Minecraft 的所有菜单，例如标题界面、暂停菜单和其他模组的菜单。你可以为它们添加自己的背景、徽标、按钮、文本、声音和动画，移动或隐藏现有元素，让按钮执行新的操作，或者创建全新的菜单。所有操作都能在游戏中完成，无需编写代码。

<img width="800" alt="使用 FancyMenu 制作的名为 Wildwood 的整合包标题界面：黄昏时分的像素风山谷中有一间小屋、一片湖泊和落日；背景图层会随鼠标移动，金色徽标、悬停时会发光的木质按钮，以及萤火虫点缀其中" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/getting_started_hero.gif?raw=true">

本页将循序渐进地介绍基础知识。过程中，你会制作一个更简单的版本；而[示例是如何制作的](#how-the-example-is-made)会介绍完整版本增加了哪些内容。

> [!TIP]
> 想在自己的游戏中使用这个标题界面？下载 [wildwood_title_screen.fmp](https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/wildwood_title_screen.fmp?raw=true)，然后在**菜单栏 -> 自定义 -> 配置档**中[导入](/profiles#importing)并[加载](/profiles#loading-a-profile)。你可以免费将它用于任何用途，例如试用 FancyMenu、从中学习，或用于你的整合包；可以修改，也可以保持原样。无需注明出处。

# 菜单栏

每个菜单顶部的菜单栏提供了 FancyMenu 的所有功能。

<img width="800" alt="标题界面顶部的菜单栏，以及展开的“自定义”菜单" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/getting_started_menu_bar.png?raw=true">

- **自定义**：当前菜单的布局，以及整个配置的各项设置，例如[全局自定义](/global-customizations)、[自定义 GUI](/custom-guis)、[变量](/variables)、[监听器](/listeners)、[调度器](/schedulers)、[配置档](/profiles)和 FancyMenu 设置。
- **工具**：一些辅助工具，例如[虚拟屏幕实例](/dummy-screen-instances)、[AFMA 创建器](/animations#fma-and-afma)、**浏览游戏资源**和**打开 FancyMenu 目录**；后者会打开你的配置文件夹（参见[数据存储位置](/data-storage-locations)）。
- **帮助**：本文档、Discord 服务器、**报告错误**和[导出供 AI 使用](/export-for-ai)。
- 右侧的门图标会关闭当前菜单，适用于没有退出方式的菜单。
- 最右侧的双箭头可以将菜单栏折叠成一个小按钮，也可以将其展开。

整合包的玩家不需要菜单栏。要了解如何关闭它，请参阅[整合包](/modpacks#disabling-the-menu-bar-and-hotkeys)。

## 菜单栏快捷键

这些快捷键在所有菜单中都有效，但在布局编辑器中以及启用整合包模式时无效。在 macOS 上，请用 `Cmd + Option` 代替 `Ctrl + Alt`。

| 快捷键 | 功能 |
|---|---|
| `Ctrl + Alt + C` | 显示或隐藏菜单栏。如果菜单栏突然消失，按此快捷键即可重新显示。 |
| `Ctrl + Alt + R` | 重新加载 FancyMenu，效果等同于**菜单栏 -> 自定义 -> 重新加载 FancyMenu** |
| `Ctrl + Alt + D` | 显示或隐藏**调试叠加层**，其中会显示菜单的[标识符](/screen-identifiers)等信息 |
| `Ctrl + Alt + L` | 打开[布局编辑器](/layout-editor)，并载入你上次编辑的布局 |

# 创建你的第一个布局

布局用于保存你对菜单所做的修改：背景、添加的元素，以及对现有按钮和文本所做的更改。一个菜单可以有多个布局，并且你可以分别启用或停用它们。

## 创建布局

<img width="800" alt="在标题界面的菜单栏中打开“自定义”，启用“自定义当前屏幕”，再次打开“自定义”并依次点击“布局”“新建”“当前屏幕”，随后进入布局编辑器" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/getting_started_new_layout.gif?raw=true">

1. 打开你想修改的菜单，例如标题界面。
2. 点击**菜单栏 -> 自定义 -> 自定义当前屏幕**，直到显示**已启用**。FancyMenu 只会修改已启用此选项的菜单。
3. 点击**菜单栏 -> 自定义 -> 布局 -> 新建 -> 当前屏幕**。

布局编辑器会打开。它会按照玩家看到的样子显示菜单，因此你可以立即看到所有更改。关于移动、调整大小和复制元素等操作，请参阅[布局编辑器](/layout-editor)。

选择**所有屏幕 [通用]**会创建一个[通用布局](/universal-layouts)，并在每个菜单中显示。

## 设置背景

请先将图片放入游戏的 `config/fancymenu/assets` 文件夹。点击**菜单栏 -> 工具 -> 打开 FancyMenu 目录**即可打开 `config/fancymenu`。

<img width="800" alt="右键点击编辑器背景，打开“菜单背景”“图片”，启用“显示背景”，然后点击“选择图片”，将“来源类型”切换为“本地”，并从 wildwood 文件夹中选取 background.png，随后山谷便会显示在按钮后方" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/getting_started_background.gif?raw=true">

1. 右键点击编辑器背景，然后打开**菜单背景 -> 图片**。
2. 点击**显示背景**，直到它显示为**已启用**。
3. 点击**选择图片**，将**来源类型**设为**本地**，然后点击**选择本地资源文件**。
4. 点击你的图片，然后点击**确定**。双击可以打开文件夹。

背景还可以使用全景图、幻灯片、视频、纯色等。请参阅[菜单背景](/menu-backgrounds)。

## 添加徽标

<img width="800" alt="删除 Minecraft 徽标和黄色闪烁文字，通过“元素”“新建”“图片”添加图片元素，并将 logo.png 设为图片来源，结果徽标被挤压成正方形" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/getting_started_logo_add.gif?raw=true">

1. 点击 Minecraft 徽标并按 `Delete`。对黄色闪烁文字也执行相同操作。
2. 在编辑器的菜单栏中，点击**元素 -> 新建 -> 图片**。
3. 右键点击新元素，点击**图片来源**，然后像选择背景一样选择你的徽标。

被删除的原版元素实际上只会被隐藏。点击**元素 -> 已删除的原版元素**即可将它们恢复。

<img width="800" alt="在徽标的右键菜单中点击“恢复宽高比”，使其恢复实际宽度；按 Esc 关闭菜单，然后将 Wildwood 徽标拖到按钮上方" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/getting_started_logo_place.gif?raw=true">

4. 再次右键点击它，然后点击**恢复宽高比**，这样它就不会被挤压。按 `Esc` 关闭菜单。
5. 将它拖到合适的位置。

你还可以添加很多其他内容，例如按钮、文本、视频和玩家模型。请参阅[元素](/elements)。

## 修改按钮

<img width="800" alt="点击“单人游戏”按钮，再按住 Ctrl 并点击其他四个按钮，然后通过“按钮纹理”“设置”“普通背景”，一次性为五个按钮设置木质纹理" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/getting_started_buttons_normal.gif?raw=true">

1. 点击第一个按钮，然后按住 `Ctrl`（macOS 上为 `Cmd`）并点击其他按钮，将它们全部选中。右键点击其中一个按钮即可同时修改所有选中的按钮。
2. 右键点击其中一个按钮，点击**按钮纹理 -> 设置 -> 普通背景**，然后像选择背景一样选择你的纹理。

<img width="800" alt="通过“按钮纹理”“设置”“悬停背景”设置发光纹理，并启用“九宫格自定义背景”，使木纹边缘保持清晰；鼠标悬停在“多人游戏”按钮上时，按钮会发光" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/getting_started_buttons_hover.gif?raw=true">

3. 对**悬停背景**执行相同操作，选择鼠标悬停在按钮上时显示的纹理。
4. 点击**按钮纹理 -> 九宫格自定义背景**，直到它显示为**已启用**。这样无论按钮宽度如何，纹理边缘都能保持清晰。请参阅[九宫格切片](/nine-slicing-and-tiling)。

同时选中多个元素时，右键菜单只会显示它们共有的设置，因此请只选择按钮。右键点击单个按钮即可查看它的全部设置，例如标签、声音、点击时执行的操作（[动作脚本](/action-scripts)）以及显示条件（[元素可见性](/element-visibility)）。请参阅[原版/模组元素](/vanilla-elements)。

## 保存

<img width="800" alt="按下 Ctrl + S，在保存文件窗口中点击“保存”，点击编辑器右上角的 X 关闭编辑器，最终标题界面显示山谷、Wildwood 徽标和木质按钮" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/getting_started_save.gif?raw=true">

1. 按 `Ctrl + S`（macOS 上为 `Cmd + S`），或点击**布局 -> 保存**。
2. 首次保存时，FancyMenu 会询问文件名。保留默认名称或输入新名称，然后点击**保存**。
3. 点击编辑器菜单栏右侧的 X 关闭编辑器。

菜单会立即显示你的布局。之后若要修改布局，将鼠标悬停在**菜单栏 -> 自定义 -> 布局**中的对应布局上，然后点击**编辑布局**；也可以按 `Ctrl + Alt + L`。

# 示例是如何制作的

本页顶部的标题界面比你刚刚制作的版本多了一些内容：

- 天空、山丘和树木由三张图片构成，并会随鼠标移动；树木移动得最多。请参阅[视差效果](/parallax)。
- 山丘和树木是与屏幕一样大的图片元素。为了让它们显示在按钮和文本后方，编辑器背景的右键菜单中启用了**自定义元素置于原版元素后方**。
- 萤火虫是一个[装饰叠加层](/decoration-overlays#fireflies)。
- 山丘、树木和徽标会通过占位符和[高级定位与尺寸调整](/advanced-positioning-sizing)根据屏幕尺寸自动调整，因此菜单适用于各种窗口尺寸。在屏幕较矮时，徽标会缩小，确保不会遮挡按钮。

要在布局编辑器中查看所有内容，请加载[示例配置档](#getting-started)并编辑其中的布局。

# 接下来可以做什么

**让它更好看**

- [元素](/elements)：可以添加到菜单中的所有内容。
- [元素定位](/positioning-elements)：确保元素在各种窗口尺寸下都能保持在合适的位置。
- [菜单背景](/menu-backgrounds)、[动画](/animations)、[视频](/video)、[装饰叠加层](/decoration-overlays)和[背景音乐](/background-music)。

**让它实现更多功能**

- [动作脚本](/action-scripts)：设置按钮和其他元素的操作。
- [元素可见性](/element-visibility)和[条件](/conditions)：让内容仅在特定情况下显示。
- [占位符](/placeholders)：在文本中显示实时信息，例如玩家名称。
- [变量](/variables)、[监听器](/listeners)和[调度器](/schedulers)：保存信息、响应游戏事件并定时执行操作。

**构建更多内容**

- [自定义 GUI](/custom-guis)：创建全新的菜单。
- [通用布局](/universal-layouts)：修改所有菜单。
- [全局自定义](/global-customizations)：调整整个游戏的设置，例如窗口标题。
- [加载界面](/loading-screen)和[游戏开场](/game-intro)。

**分享你的作品**

- [整合包](/modpacks)：将你的配置放入整合包。
- [配置档](/profiles)：在不同配置之间切换并导出配置。

# 获取帮助

- [常见问题](/faq)解答了最常见的问题。
- 点击**菜单栏 -> 帮助 -> 加入 Discord**即可进入 FancyMenu Discord 服务器。
- [导出供 AI 使用](/export-for-ai)可以将你的配置转换为文本，供 AI 聊天使用，例如 Discord 服务器上的支持机器人。
- 如果某项功能未能正常运行，请点击**菜单栏 -> 帮助 -> 报告错误**。

# 开发者须知

如需为 FancyMenu 制作附加组件或在自己的模组中使用 FancyMenu，请参阅[开发者文档](https://github.com/Keksuccino/FancyMenu-Dev-Docs/wiki)。
