---
title: 通用布局
description: 将同一布局应用于多个受支持的屏幕。
sourceBlobSha: 2179fed92c6598b6e5c3ecfea354a4c853bc394b
---

# 通用布局

通用布局会应用于所有启用了屏幕自定义功能的受支持屏幕。它不会应用于[已屏蔽的屏幕](/incompatibility-list#screens-where-customization-is-intentionally-disabled)或其他被排除的屏幕。

通用布局适用于需要在多个屏幕上持续显示的共享元素，例如徽标、导航、叠加层或[音频元素](/elements#audio)。

# 创建通用布局

1. 打开一个受支持的屏幕，并显示 FancyMenu 菜单栏。
2. 选择 **Layouts -> New -> For All Screens [Universal]**。
3. 添加并配置元素。
4. 保存布局。

普通屏幕仍需启用 **Current Screen Customization**。由于自定义可能导致不受支持的模组屏幕无法正常运行，因此没有全局启用所有屏幕的开关。

# 限制适用的屏幕

在编辑器背景的上下文菜单中打开通用布局设置。

- **白名单：**布局仅应用于列出的屏幕标识符。
- **黑名单：**布局应用于所有符合条件的屏幕，但列出的屏幕除外。

使用 **Customization -> Copy Identifier of Current Screen** 复制[屏幕标识符](/screen-identifiers)。

你还可以添加[布局级要求](/conditions#layout-wide-requirements)，以控制布局的应用时机。

# 布局顺序

符合条件的通用布局和特定屏幕布局会按照 **Layout Index** 合并并叠放。索引较低的布局先应用；后续可叠放的设置可以覆盖之前的设置。索引相同时，会先收集通用布局，再收集特定屏幕布局。
