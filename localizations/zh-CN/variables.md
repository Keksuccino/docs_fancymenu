---
title: 变量
description: 如何创建和使用变量。
---
# FancyMenu 中的变量

变量用于存储文本值，布局、动作、占位符、条件、监听器、计划任务以及自定义 GUI 都可以重复使用这些值。

## 创建变量

要在 FancyMenu 中创建变量：

1. 确保你当前不在布局编辑器中。
2. 点击屏幕顶部的菜单栏。
3. 进入 **Customization -> Variables -> Manage Variables**。
4. 在出现的“Manage Variables”界面中，点击 **Add Variable** 按钮。
5. 为新变量输入名称，然后点击 **OK**。

就这样！你的变量已经可以使用了。你可以在“Manage Variables”界面中看到它。

Manage Variables 窗口支持右键上下文菜单、键盘导航、复制/粘贴、撤销/重做、输入搜索、按 **Delete** 删除，以及使用 **Ctrl/Command + S** 保存。

## 设置变量值

空变量本身并没有太大作用。要让变量发挥作用，你需要向其中写入数据。在 FancyMenu 中，这称为“设置变量值”。

设置变量值主要有两种方式：

1. 在“Manage Variables”界面中，在列表里找到该变量，点击它，然后点击 **Set Value**。输入你想保存的数据。

2. 在自定义菜单时，将 [**Set Variable Value** 动作](./action-scripts#set-variable-value-fm-variable-set_variable)用于 [Button](./elements#button)、[Slider](./elements#slider) 或 [Ticker](./elements#ticker) 元素。

例如，创建一个名为 `clicks` 的变量，并将 [**Set Variable Value** 动作](./action-scripts#set-variable-value-fm-variable-set_variable)添加到一个按钮上：

```
clicks:{"placeholder":"calc","values":{"expression":"{"placeholder":"getvariable","values":{"name":"clicks"}} + 1"}}
```

其工作方式如下：
1. [**Get Stored Variable** 占位符](./placeholders#get-variable-value-fm-variable-getvariable) 获取 `clicks` 变量的当前值。
2. [**Calculator** 占位符](./placeholders#calculator-calc) 将该值加 1。
3. 结果通过 [**Set Variable Value** 动作](./action-scripts#set-variable-value-fm-variable-set_variable) 写回到 `clicks` 中。

因此，每次点击按钮时，`clicks` 变量都会加 1，从而实际上记录总点击次数。

## 使用变量

现在你已经有了保存数据的变量，可以在菜单自定义的不同部分中使用这些数据：

* [**加载条件**](./conditions)：检查变量值以控制元素何时显示。例如，将 [**Is Number**](./conditions#is-number-fancymenu_visibility_requirement_is_number) 与 [**Get Stored Variable** 占位符](./placeholders#get-variable-value-fm-variable-getvariable) 结合使用，当 `clicks` 大于 5 时显示某个元素。

* **占位符**：使用 [**Get Stored Variable** 占位符](./placeholders#get-variable-value-fm-variable-getvariable) 将变量插入文本中，例如 `{"placeholder":"getvariable","values":{"name":"clicks"}}`。

* **嵌套占位符**：你可以在 [**Calculator** 占位符](./placeholders#calculator-calc) 中使用 [**Get Stored Variable** 占位符](./placeholders#get-variable-value-fm-variable-getvariable)。

* **动作**：变量可以创建动态行为：
  - 在 [动作脚本](./action-scripts#what-are-statements) 中使用 **IF** 语句，并结合 [**Is Number**](./conditions#is-number-fancymenu_visibility_requirement_is_number) 和 [**Get Stored Variable** 占位符](./placeholders#get-variable-value-fm-variable-getvariable)。
  - 将 [**Get Stored Variable** 占位符](./placeholders#get-variable-value-fm-variable-getvariable) 与 [**Copy Text to Clipboard**](./action-scripts#copy-text-to-clipboard-copytoclipboard) 结合使用。
  - 在 [**Open Screen or Custom GUI**](./action-scripts#open-screen-or-custom-gui-opengui) 中使用变量，根据已保存的进度或偏好来选择界面。

## 变量示例

下面是一些示例，帮助你获得灵感并开始使用变量：

1. **高分**：创建一个 `highscore` 变量，并做一个按钮，在玩家当前分数高于现有值时将其设为当前分数。使用 [**Get Stored Variable** 占位符](./placeholders#get-variable-value-fm-variable-getvariable) 显示它。

2. **难度选择器**：为不同的游戏难度创建变量，例如 `easy`、`medium` 和 `hard`。使用按钮设置难度变量，并根据所选难度显示/隐藏元素。

3. **教程进度**：添加变量来跟踪玩家在教程中的进度，例如 `tutorial_step`。每完成一步就递增该变量，并使用加载条件逐步显示更多菜单内容。

## 持久性、作用域和存储

变量在当前 Minecraft 实例中共享。它们不会按布局、世界、服务器或玩家分别隔离。

值会立即保存到 `<game-directory>/config/fancymenu/user_variables.db`，并会在重启后保留。

- **Reset on Launch** 会在下次游戏启动时清空该变量。
- [**Clear All Variables**](./action-scripts#clear-all-variables-fm-variable-clear_variables) 会移除所有已存储的变量值。
- 名称区分大小写。请使用简单且唯一的名称，例如 `tutorial_step`。

当命名的变量不存在，或其存储值为空时，[**Get Stored Variable** 占位符](./placeholders#get-variable-value-fm-variable-getvariable) 会返回 `0`。这个默认值在比较和计算器表达式中很重要。

[**Set Variable Value** 动作](./action-scripts#set-variable-value-fm-variable-set_variable) 使用 `variable_name:variable_value` 格式，并在第一个冒号处拆分，因此值中可以包含更多冒号。

不要在 FancyMenu 变量中存储密码、令牌或其他机密信息。它们属于可读的配置数据。
