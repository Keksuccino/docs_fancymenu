---
title: 设置/获取 Minecraft 选项
description: 如何设置和获取 Minecraft 选项，例如音量、视野、渲染距离等。
---

# 在 FancyMenu 中使用 Minecraft 选项

FancyMenu 允许你通过不同的 UI 元素来获取和设置 Minecraft 游戏设置（选项）。本指南将向你展示如何使用按钮、滑块和 ticker，在自定义菜单布局中操作 Minecraft 选项。

# 理解 Minecraft 选项

Minecraft 有许多内置选项，用于控制从图形设置到音量大小等各种内容。FancyMenu 让你可以通过选项名称来访问它们。

一些常见的选项名称包括：
- `soundCategory_master` - 主音量
- `soundCategory_music` - 音乐音量
- `soundCategory_ambient` - 环境音音量
- `soundCategory_players` - 玩家音效音量
- `soundCategory_blocks` - 方块音效音量
- `fov` - 视野
- `gamma` - 亮度
- `renderDistance` - 渲染距离

# 显示选项值

你可以使用一个特殊的占位符来显示任意 Minecraft 选项的当前值。

这个占位符的格式如下：
```
{"placeholder":"minecraft_option_value","values":{"name":"option_name"}}
```

将 `option_name` 替换为你想显示的实际选项名称。

# 使用按钮设置选项

按钮可用于为 Minecraft 选项设置特定值。

## 如何设置一个按钮：

1. 创建一个新的 Button 元素
2. 设置按钮标签（显示在按钮上的文字）
3. 添加一个动作：右键单击按钮 → 编辑动作脚本 → 添加动作 → 设置 Minecraft 选项值
4. 在“设置 Minecraft 选项值”窗口中：
   - Name：输入选项名称（例如 `renderDistance`）
   - Value：输入要设置的值（例如 `16`）

## 示例：

创建一个将渲染距离设置为 16 区块的按钮：
- Option Name: `renderDistance`
- Value: `16`
- Label: "将渲染距离设置为 16 区块"

# 使用滑块设置选项

滑块非常适合用于有范围的选项，例如音量设置或亮度。

## 如何设置一个滑块：

1. 创建一个新的 Slider 元素
2. 设置滑块类型：
   - 对于整数（例如渲染距离）：选择“整数范围”
   - 对于小数（例如音量）：选择“小数范围”
3. 设置最小值和最大值
4. 添加一个动作来设置 Minecraft 选项：
   - 右键 → 编辑动作脚本 → 添加动作 → 设置 Minecraft 选项值
   - Name：选项名称
   - Value：`$$value`（这个特殊变量包含当前滑块值）
5. 将预选值设置为当前选项值：
   - 将“Pre-Selected Value”设置为 `{"placeholder":"minecraft_option_value","values":{"name":"option_name"}}`

## 滑块标签示例格式：

要在滑块标签中显示当前选项值，请使用：
```
音量：{"placeholder":"minecraft_option_value","values":{"name":"soundCategory_master"}}
```

要显示百分比（适用于音量）：
```
音量：{"placeholder":"calc","values":{"expression":"$$value * 100.0","decimal":"false"}}%
```

# 使用 ticker 设置选项

Ticker 是不可见元素，可以按计划自动更改选项。

## 如何设置一个 ticker：

1. 创建一个新的 Ticker 元素
2. 配置 tick 设置：
   - Tick Mode：选择选项应在何时更新
   - Tick Delay：设置更新频率（以毫秒为单位）
3. 添加用于设置 Minecraft 选项的动作：
   - 右键 → 编辑动作脚本 → 添加动作 → 设置 Minecraft 选项值
   - 设置选项名称和值

## 示例：

当菜单加载时将 gamma（亮度）设置为最高：
- Tick Mode：On Load Screen
- Name: `gamma`
- Value: `1.0`

# 常见用途

以下是使用 FancyMenu 设置和获取 Minecraft 选项时的一些常见用法。

## 创建自定义音量滑块

音量滑块是 Minecraft 选项集成中最常见的用途之一。下面是制作自定义音乐音量滑块的方法：

1. 创建一个新的 Slider 元素
2. 将“Slider Type”设置为“Decimal Range”
3. 将“Minimum Range Value”设置为“0.0”
4. 将“Maximum Range Value”设置为“1.0”
5. 编辑动作脚本 → 添加动作 → 设置 Minecraft 选项值
   - 将 Name 设置为 `soundCategory_music`
   - 将 Value 设置为 `$$value`
6. 将“Pre-Selected Value”设置为 `{"placeholder":"minecraft_option_value","values":{"name":"soundCategory_music"}}`
7. 如果要将音量显示为百分比，请将标签设置为：
   ```
   音乐：{"placeholder":"calc","values":{"expression":"$$value * 100.0","decimal":"false"}}%
   ```

你可以为其他声音类别创建类似的滑块：
- 主音量：`soundCategory_master`
- 音乐：`soundCategory_music`
- 环境音：`soundCategory_ambient`
- 方块：`soundCategory_blocks`
- 玩家：`soundCategory_players`
- 天气：`soundCategory_weather`

## 创建自定义 FOV 滑块

视野（FOV）是一个重要的图形设置，用于决定你在游戏中的视野宽度。FOV 选项在内部使用 -1.0 到 1.0 的值范围，但在界面中显示为 30 到 110。

### 理解 FOV 值映射
- 内部值范围：-1.0 到 1.0
- 显示值范围：30 到 110
- 映射公式：`(internal_value + 1) * 40 + 30`

### 第 1 步：创建一个 Ticker 元素来更新 FOV 文本

首先，我们需要一个 ticker，用来检查当前 FOV 值并设置一个变量，以显示相应的说明：

1. 创建一个新的 Ticker 元素
2. 将“Tick Mode”设置为“Normal”（这样它会持续更新）
3. 将“Tick Delay”设置为大约“10”（毫秒），以避免过于频繁地检查

现在我们需要为 FOV 标签设置动作。你的动作脚本结构应如下所示：

```
▶ Action Script
│
├─▶ IF (mapped FOV = 70)
│  └─■ Set Variable Value: fov_text:Normal
│
├─▶ ELSE-IF (mapped FOV = 110)
│  └─■ Set Variable Value: fov_text:Quake Pro
│
└─▶ ELSE
   └─■ Set Variable Value: fov_text:[calculated numeric value]
```

下面来设置每一部分：

#### 设置“Normal” FOV 标签：
1. 右键 → 编辑动作脚本 → 添加动作
2. 点击“IF Statement”添加一个条件块
3. 将条件设置为“Is Number”，并使用：
   - Compare Mode: “equals”
   - Number: `{"placeholder":"calc","values":{"decimal":"false","expression":"({"placeholder":"minecraft_option_value","values":{"name":"fov"}} + 1) * 40 + 30"}}`
   - Compare With: "70"
4. 在这个 IF 块中，添加“Set Variable Value (FM Variable)”动作，并设置：
   - Value: `fov_text:Normal`

#### 设置“Quake Pro” FOV 标签：
1. 在动作脚本中添加“ELSE-IF Statement”
2. 将条件设置为“Is Number”，并使用：
   - Compare Mode: “equals”
   - Number: `{"placeholder":"calc","values":{"decimal":"false","expression":"({"placeholder":"minecraft_option_value","values":{"name":"fov"}} + 1) * 40 + 30"}}`
   - Compare With: "110"
3. 在这个 ELSE-IF 块中，添加“Set Variable Value (FM Variable)”动作，并设置：
   - Value: `fov_text:Quake Pro`

#### 设置数值型 FOV 标签：
1. 添加一个“ELSE Statement”块
2. 在这个 ELSE 块中，添加“Set Variable Value (FM Variable)”动作，并设置：
   - Value: `fov_text:{"placeholder":"calc","values":{"decimal":"false","expression":"({"placeholder":"minecraft_option_value","values":{"name":"fov"}} + 1) * 40 + 30"}}`

<img src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/fov_slider_action_script.png" alt="FOV Slider Action Script" style="max-width: 600px; height: auto;">

### 第 2 步：创建 FOV 滑块

1. 创建一个新的 Slider 元素
2. 将“Slider Type”设置为“Decimal Range”
3. 将“Minimum Range Value”设置为“-1.0”
4. 将“Maximum Range Value”设置为“1.0”
5. 编辑动作脚本 → 添加动作 → 设置 Minecraft 选项值
   - 将 Name 设置为 `fov`
   - 将 Value 设置为 `$$value`
6. 将“Pre-Selected Value”设置为 `{"placeholder":"minecraft_option_value","values":{"name":"fov"}}`

### 第 3 步：设置滑块标签

将滑块标签设置为仅显示 FOV 文本变量：

```
FOV: {"placeholder":"getvariable","values":{"name":"fov_text"}}
```

此标签将显示：
- 当值为 70 时显示 “FOV: Normal”
- 当值为 110 时显示 “FOV: Quake Pro”  
- 对于其他所有值，显示 “FOV: 85”（或任何其他数字）

### FOV 滑块提示

- 内部滑块值范围是 -1.0 到 1.0，需要映射到 30 到 110 进行显示
- 转换公式是：`(internal_value + 1) * 40 + 30`
- 只有两个值有特殊标签：70（Normal）和 110（Quake Pro）
- Minecraft 的默认 FOV 是 70（对应内部值 0.0）
- `fov_text` 变量会自动包含特殊标签或数值

## 在文本元素中显示选项值

你也可以在 Text 元素中显示当前选项值：

1. 创建一个 Text 元素
2. 对于文本内容，使用占位符：`{"placeholder":"minecraft_option_value","values":{"name":"option_name"}}`

例如，要显示当前渲染距离：
```
当前渲染距离：{"placeholder":"minecraft_option_value","values":{"name":"renderDistance"}} 区块
```

# 查找选项名称

你可以通过以下方式找到所有可用选项的名称：

  1. 创建一个按钮
  2. 右键单击它
  3. 点击“Edit Action Script”
  4. 添加“Set Minecraft Option Value”动作
  5. 在编辑动作值时，当你开始在“Name”字段中输入时，查看下拉建议
  
# 重要提示

- **有效值**：并非所有选项都接受所有值。例如：
  - 音量选项接受 0.0 到 1.0 之间的值
  - 渲染距离通常接受 2 到 32 之间的整数
  - 像 `pauseOnLostFocus` 这样的布尔选项（true/false）接受 "true" 或 "false"

- **测试**：始终测试你的设置，确保它们按预期工作！

- **视觉反馈**：使用上面描述的占位符，为用户显示当前值的视觉反馈。
