---
title: 条件
description: 显示元素和布局；仅在满足某些条件（例如时间、窗口大小或变量值）时，才允许点击按钮或执行操作。
sourceBlobSha: 8d7cc9e0182f8478f3a7ab86391e90cae12c626b
---

# 条件

条件是一些判断，例如“鼠标悬停在这个按钮上”“现在是十二月”或“已加载世界”。你可以使用条件来：

- 仅在某些时候显示一个[元素](/elements)，
- 仅在某些时候加载整个布局，
- 仅在某些时候允许点击按钮、滑块和复选框，
- 仅在某些时候运行[操作脚本](/action-scripts)中的部分内容。

菜单打开时，FancyMenu 会持续检查条件，因此内容会立即显示、隐藏或变化。此信息框只有在鼠标悬停于“多人游戏”时才会显示：

<img width="800" alt="将鼠标移到标题屏幕的“多人游戏”按钮上时，旁边会显示一个包含服务器地址的信息框" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/requirements_hover.gif?raw=true">

# 查找条件

| 位置 | 条件的作用 |
|---|---|
| 右键单击一个元素 -> **加载条件** | 只有满足条件时才显示该元素。对[原版元素](/vanilla-elements)也有效。 |
| 右键单击编辑器背景 -> **加载条件 [整个布局]** | 只有满足条件时才加载整个布局。请参阅[整个布局的条件](#整个布局的条件)。 |
| 右键单击按钮、滑块或复选框 -> **控件启用状态** | 只有满足条件时才能点击。否则会显示为灰色。原版按钮也有此选项。 |
| [操作脚本](/action-scripts#statements)中的 IF、ELSE-IF 和 WHILE | 只有满足条件时才运行其中的操作。 |

在布局编辑器中，元素始终会显示，因此你仍然可以编辑它们。元素的条件在编辑器外也会生效。

> [!TIP]
> [元素可见性](/element-visibility)介绍了更多显示和隐藏元素的方法，例如延迟、淡入淡出，以及通过按钮切换显示状态。

# 添加条件

<img width="800" alt="复制“多人游戏”按钮的 ID，然后在“管理条件”中为信息框添加“元素正被悬停”条件并填入该 ID" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/requirements_add.gif?raw=true">

1. 右键单击该元素，然后单击**加载条件**。此时会打开**管理条件**。
2. 右键单击空列表，然后单击**添加条件**，或按 `A`。
3. 在**可用条件**中单击一个类别，或开始输入以搜索名称和说明。**条件说明**会解释当前选中的条件。
4. 单击**下一步**来设置条件值。无需设置值的条件会显示**完成**。双击条件也会执行相同操作。
5. 填写条件值，然后单击**完成**。例如，**元素正被悬停**需要元素的 ID。右键单击一个元素，然后单击**复制元素 ID**即可获取。
6. 在**管理条件**中单击**完成**。

## 条件模式

条件选择器中的**条件模式**按钮可以在以下模式间切换：

- **正常**：条件为真时满足。
- **相反**：条件不为真时满足。例如，**世界已加载**在相反模式下仅会在主菜单中满足。

**管理条件**会显示每个条件的模式和值。

## 值

- 值支持[占位符](/placeholders)和你的[变量](/variables#showing-variables-in-text)，例如 `$$coins`。FancyMenu 每次检查条件时都会替换这些值。
- 许多值字段会在输入时提供建议，例如生物群系、模组 ID、语言或变量名称。单击建议项，或按 `Tab`。
- 值简单的条件会打开单行文本编辑器。编辑器标题会说明需要输入的内容，例如**目标元素 ID**。

## 管理条件

在**管理条件**中右键单击列表、条件或分组，可使用以下选项：

| 选项 | 快捷键 | 作用 |
|---|---|---|
| **添加条件** | `A` | 添加一个条件。 |
| **添加分组** | `G` | 添加一个分组（见下文）。 |
| **编辑条件** | `Enter` 或双击 | 打开条件选择器，可编辑条件类型、模式和值。 |
| **移除条件** / **移除分组** | `Delete` | 移除该条件或分组。 |
| **撤销** / **重做** | `Ctrl + Z` / `Ctrl + Y` | 撤销或重做此窗口中的更改。 |
| **导出条件供 AI 使用** | | 将此窗口中的所有条件（包括未保存的更改）导出，以供 [AI 聊天](/export-for-ai)使用。 |

按 `Up` 和 `Down` 可选择上一个或下一个条件。**完成**（`Ctrl + S`）会保存更改；**取消**会放弃你在此窗口中的所有更改。在 macOS 上，请用 `Cmd` 代替 `Ctrl`。

选中多个元素时，**加载条件**会同时修改所有选中元素的条件。如果它们的条件不同，FancyMenu 会先询问你，因为现有条件都会被替换。

# 组合条件

**管理条件**中的所有条件都必须满足。若要表达“这个或那个”，请使用分组。

分组的行为类似一个条件：

- **与**模式：分组中的所有条件都必须满足。新分组默认使用此模式。
- **或**模式：分组中只要有一个条件满足即可。

1. 右键单击列表，然后单击**添加分组**，或按 `G`。分组会获得类似 `group_1` 的名称。
2. 右键单击分组，然后单击**分组模式**，在**与**和**或**之间切换。
3. 单击**编辑分组条件**，或双击分组。此时会打开一个类似**管理条件**的窗口，用于编辑分组。
4. 添加分组中的条件，然后单击**完成**。

例如，若要让圣诞问候语在十二月或玩家开启 `xmas_lights` 时显示，可以创建一个“或”分组，其中包含**现实时间月份为** `12`，以及变量 `xmas_lights` 的**变量值 (FM Variable)** 为 `on`。

<img width="800" alt="在“管理条件”中添加分组，将其切换为“或”模式，然后添加“现实时间月份为”和“变量值 (FM Variable)”条件" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/requirements_group.gif?raw=true">

- 分组可以包含其他分组，以实现类似“(A 且 B) 或 (C 且 D)”的逻辑。窗口标题会显示你当前所在的位置，例如 `编辑分组：group_1 › group_2`。
- **编辑分组标识符**可以重命名分组。每个名称只能使用一次，包括分组内部的名称。
- 空的“或”模式分组永远不会满足。

# 整个布局的条件

整个布局的条件决定是否加载整个布局。你可以用它来创建夜间版标题屏幕、为不同语言分别创建布局，或创建仅在单人游戏中显示的布局。

右键单击编辑器背景，然后单击**加载条件 [整个布局]**。也可以通过**菜单栏 -> 布局 -> 布局属性**打开。

- 如果菜单打开时条件结果发生变化，FancyMenu 会使用当前满足条件的布局重新构建屏幕。
- 此功能也适用于[通用布局](/universal-layouts)。
- 若要通过按钮启用或禁用布局，请将按钮放在另一个布局中。请参阅[启用和禁用布局](/element-visibility#turning-layouts-on-and-off)。

# 注意事项

- 未加载世界时（例如在主菜单中），世界和玩家相关条件永远不会满足。
- 在启用了 **Async** 的 [Ticker](/elements#ticker) 中，元素、鼠标光标、物品栏、玩家和世界相关条件无法使用。此时 FancyMenu 会显示错误，并注明条件名称。
- 已移除的附加组件所提供的条件会被跳过。在编辑器中保存布局后，这些条件会被彻底移除。
- **菜单栏 -> 自定义 -> 设置 -> 条件缓存时长 [毫秒]** 会在一段时间内重用条件检查结果，从而加快大型布局的运行速度。默认值为 `0`，即关闭缓存。缓存可能导致操作脚本和快速更改出现意料之外的行为。

# 所有条件

条件的排序方式与条件选择器相同：先按类别，再按名称排序。没有类别的条件会显示在选择器底部，也会列在此处的[其他](#其他)类别中。

## GUI

### 当前光标类型为

**标识符：** `is_active_cursor_type`

当鼠标光标呈现指定形状时满足，例如悬停在链接上时显示**指针**，悬停在文本字段上时显示**文本光标**。

- 值：单击**光标类型**，然后选择**普通**、**文本光标**、**十字线**、**指针**、**水平调整大小**、**垂直调整大小**、**西北-东南调整大小**、**东北-西南调整大小**、**全方向调整大小**或**禁止**。

### 任意按钮正被悬停

**标识符：** `fancymenu_visibility_requirement_is_any_button_hovered`

鼠标悬停在任意可见按钮上时满足，无论按钮是原版还是自定义的。

### 任意元素正被悬停

**标识符：** `fancymenu_visibility_requirement_is_any_element_hovered`

鼠标悬停在任意可见元素上时满足，不限于按钮。

### 任意屏幕已打开

**标识符：** `is_any_screen_open`

任意菜单打开时满足，例如暂停菜单或物品栏。没有菜单、正在游玩时不满足。

### 按钮已启用

**标识符：** `fancymenu_visibility_requirement_is_button_active`

按钮可点击时满足。

- 值：按钮的[元素 ID](/element-identifiers)。在编辑器中右键单击按钮，然后单击**复制元素 ID**。

### 自定义菜单栏可见

**标识符：** `is_customization_menu_bar_visible`

FancyMenu 的菜单栏显示时满足。在整合包模式下或菜单栏关闭时不满足。

### 元素已获得焦点

**标识符：** `is_element_focused`

元素获得焦点时满足。单击按钮或滑块，或使用方向键或 `Tab` 移动到它们上面，都可以使它们获得焦点。使用按键移动到元素上不算悬停；如果要兼顾使用键盘的玩家，请将此条件与**元素正被悬停**放在一个[或分组](#组合条件)中。

- 值：[元素 ID](/element-identifiers)，例如 `mc_titlescreen_multiplayer_button`。

### 元素正被悬停

**标识符：** `fancymenu_visibility_requirement_is_element_hovered`

鼠标悬停在某个元素上时满足。该元素必须可见。

- 值：[元素 ID](/element-identifiers)，例如标题屏幕“多人游戏”按钮的 `mc_titlescreen_multiplayer_button`。在编辑器中右键单击元素，然后单击**复制元素 ID**即可获取。

### 元素已滚动到底部

**标识符：** `is_scroll_area_scrolled_to_end`

[可滚动区域](/scrollable-areas)或文本元素滚动到底部时满足。没有可滚动内容的元素也算已滚动到底部。适用于仅当玩家滚动阅读完规则后才可使用的**接受**按钮。

- 值：可滚动区域或文本元素的[元素 ID](/element-identifiers)。

### GUI 缩放为

**标识符：** `fancymenu_loading_requirement_is_gui_scale`

Minecraft 的 GUI 缩放比例符合指定值时满足。

- 值：输入数字，例如 `2` 表示缩放比例必须恰好为 2，`>2` 表示大于 2，`<4` 表示小于 4。也支持小数，例如 `<3.5`。
- 多个条件用逗号分隔。普通数字中只需有一个匹配，例如 `2,3`。所有 `>` 和 `<` 条件都必须满足，例如 `>1,<4`。

### 按键已按下

**标识符：** `is_key_pressed`

按键按住时满足。若要在每次按键时仅运行一次操作，请改用[**键盘按键按下时**](/listeners#on-keyboard-key-pressed)监听器。

- 值：在**按键选择**中单击**更改按键**，然后按下所需按键。

### 布局已启用

**标识符：** `fancymenu_visibility_requirement_is_layout_enabled`

布局已启用时满足。

- 值：布局名称，例如 `winter_title_screen`。

### Minecraft 调试界面已启用

**标识符：** `is_debug_overlay_enabled`

显示 F3 调试屏幕时满足。使用 F1 隐藏 HUD 时不满足。

### 整合包模式已启用

**标识符：** `is_modpack_mode_enabled`

FancyMenu 的整合包模式已开启时满足。

### 屏幕标题为

**标识符：** `is_menu_title`

打开的屏幕标题匹配时满足，例如“选项”或“游戏菜单”。这里指玩家看到的标题，而非[屏幕标识符](/screen-identifiers)。

- 值：标题文本或其本地化键，例如 `options.title`。值窗口会显示你正在编辑的屏幕的这两项内容，并提供本地化键建议。
- 本地化键适用于所有语言。标题文本必须完全匹配。

## 实时时间

这些条件会检查玩家电脑的时钟。多个值用逗号分隔：只需其中一个匹配即可。

### 实时时间的日期为

**标识符：** `fancymenu_visibility_requirement_is_realtime_day`

当月中的指定日期满足。

- 值：`1` 到 `31`，例如 `24,25,26`。

### 实时时间的小时为

**标识符：** `fancymenu_visibility_requirement_is_realtime_hour`

指定小时内满足。

- 值：`0` 到 `23`，例如 `20,21,22,23` 表示晚上。

### 实时时间的分钟为

**标识符：** `fancymenu_visibility_requirement_is_realtime_minute`

每小时中的指定分钟内满足。

- 值：`0` 到 `59`。

### 实时时间的月份为

**标识符：** `fancymenu_visibility_requirement_is_realtime_month`

指定月份内满足。

- 值：`1`（一月）到 `12`（十二月），例如圣诞节可填 `12`。

### 实时时间的秒数为

**标识符：** `fancymenu_visibility_requirement_is_realtime_second`

每分钟中的指定秒数内满足。

- 值：`0` 到 `59`。

### 实时时间的星期为

**标识符：** `fancymenu_visibility_requirement_is_realtime_week_day`

一周中的指定日期满足。

- 值：`1`（星期日）到 `7`（星期六），例如周末可填 `1,7`。

### 实时时间的年份为

**标识符：** `fancymenu_visibility_requirement_is_realtime_year`

指定年份内满足。

- 值：完整年份，例如 `2027`。

## 系统

### 文件/文件夹存在

**标识符：** `fancymenu_loading_requirement_file_exists`

文件或文件夹存在时满足。

- 值：游戏文件夹中的路径，例如 `config/mymodpack/welcome_seen.txt`。以 `.minecraft/` 开头的路径指向默认的 `.minecraft` 文件夹。

### 网络连接可用

**标识符：** `is_internet_connection_available`

电脑联网时满足。FancyMenu 会不时在后台检查网络状态。

### 操作系统为 Linux

**标识符：** `fancymenu_loading_requirement_is_os_linux`

在 Linux 上满足。严格来说，任何既不是 Windows 也不是 macOS 的系统都会满足。

### 操作系统为 macOS

**标识符：** `fancymenu_loading_requirement_is_os_macos`

在 macOS 上满足。

### 操作系统为 Windows

**标识符：** `fancymenu_loading_requirement_is_os_windows`

在 Windows 上满足。

### 调度器正在运行

**标识符：** `fancymenu_visibility_requirement_is_scheduler_running`

[调度器](/schedulers)正在运行时满足。

- 值：调度器的标识符，例如 `my_scheduler`。

## 窗口

窗口尺寸以游戏窗口的实际像素为单位，而非 GUI 像素。条件说明会显示当前尺寸。

### 全屏模式

**标识符：** `fancymenu_loading_requirement_is_fullscreen`

游戏处于全屏模式时满足。

### 窗口高度为

**标识符：** `fancymenu_loading_requirement_is_window_height`

窗口高度符合指定值时满足。

- 值：高度，例如 `1080`。多个高度用逗号分隔：只需其中一个匹配即可。

### 窗口高度大于

**标识符：** `fancymenu_loading_requirement_is_window_height_bigger_than`

窗口高度大于指定值时满足。

- 值：高度，例如 `1080`。

### 窗口宽度为

**标识符：** `fancymenu_loading_requirement_is_window_width`

窗口宽度符合指定值时满足。

- 值：宽度，例如 `1920`。多个宽度用逗号分隔：只需其中一个匹配即可。

### 窗口宽度大于

**标识符：** `fancymenu_loading_requirement_is_window_width_bigger_than`

窗口宽度大于指定值时满足。

- 值：宽度，例如 `1920`。

## 世界

未加载世界时，这些条件永远不会满足。**玩家在结构中**和**处于正在进行的袭击区域中**需要服务器端安装 FancyMenu。在单人游戏中，这些条件始终有效。

### 玩家拥有伤害吸收之心

**标识符：** `has_player_absorption_hearts`

玩家拥有金色伤害吸收之心时满足。

### 玩家权限等级为

**标识符：** `fancymenu_loading_requirement_has_player_permission_level`

玩家在世界或服务器中至少拥有指定权限等级时满足，例如拥有管理员权限。

- 值：`0` 到 `4`。`0` 始终满足；使用 `/gamemode` 等命令需要 `2`；`/op` 命令赋予的等级为 `4`。

### 冒险模式

**标识符：** `fancymenu_visibility_requirement_is_adventure`

玩家处于冒险模式时满足。

### 任意效果生效

**标识符：** `is_any_effect_active`

玩家拥有任意效果时满足，例如速度或中毒效果。

### 攻击蓄力不足

**标识符：** `is_attack_strength_weakened`

玩家的攻击尚未完全蓄力时满足。此时会显示攻击指示器。

### 方块/物品属于标签

**标识符：** `is_in_tag`

方块或物品属于某个标签时满足，例如 `minecraft:logs` 或 `c:tools`。标签仅在加载世界时存在。

- 值：单击**标签类型**，选择**方块**或**物品**，然后输入**方块/物品键**和**标签**。两个字段都会提供输入建议。标签前面的 `#` 可省略。
- 此键与监听器变量（例如 `$$block_key`）配合使用效果很好。例如，[**方块被破坏时**](/listeners#on-block-broke)监听器脚本中的 IF 语句可以只为原木显示提示信息。

### 摄像机视角为

**标识符：** `is_camera_perspective`

摄像机处于指定视角时满足（F5）。

- 值：单击按钮，选择**第一人称**、**第三人称**或**正面视角**。

### 天气晴朗

**标识符：** `is_clear_weather`

既没有下雨也没有打雷时满足。

### 创造模式

**标识符：** `fancymenu_visibility_requirement_is_creative`

玩家处于创造模式时满足。

### 光标正拿着物品栏物品

**标识符：** `is_cursor_holding_inventory_item`

在物品栏屏幕中，鼠标光标正拿着物品时满足。

### 难度为

**标识符：** `is_difficulty`

世界的难度符合指定值时满足。

- 值：`peaceful`、`easy`、`normal` 或 `hard`。

### 效果生效

**标识符：** `is_effect_active`

玩家拥有指定效果时满足。

- 值：效果的键，例如 `minecraft:speed`。在世界中时，字段会提供效果建议。

### 附近存在实体

**标识符：** `is_entity_nearby`

玩家附近存在指定类型的实体时满足。

- 值：**实体注册键**，例如 `minecraft:creeper`；以及**检测半径（方块）**，例如 `10`。在世界中时，键字段会提供实体建议。

### 游戏模式为

**标识符：** `is_gamemode`

玩家处于指定游戏模式时满足。

- 值：`survival`、`creative`、`adventure` 或 `spectator`。

### 极限模式

**标识符：** `is_hardcore`

处于极限模式世界时满足。

### 已选中快捷栏栏位

**标识符：** `is_hotbar_slot_active`

选中指定快捷栏栏位时满足。

- 值：`0`（最左侧栏位）到 `8`。

### 处于正在进行的袭击区域中

**标识符：** `is_in_active_raid_area`

玩家处于袭击区域（袭击进度条会显示）时满足。需要服务器端安装 FancyMenu。

### 物品栏栏位已填充

**标识符：** `is_inventory_slot_filled`

玩家物品栏的某个栏位中有物品时满足。

- 值：栏位编号。`0` 到 `8` 是快捷栏，`9` 到 `35` 是物品栏的其余部分。

### 鼠标正悬停在物品栏物品上

**标识符：** `is_item_hovered_in_inventory`

鼠标悬停在物品栏屏幕中的物品上时满足，例如玩家物品栏或箱子中的物品。

### 多人游戏

**标识符：** `fancymenu_loading_requirement_is_multiplayer`

玩家正在服务器上时满足。

### 玩家正在创造模式中飞行

**标识符：** `is_player_creative_flying`

玩家在创造模式中飞行时满足。

### 玩家正在使用鞘翅飞行

**标识符：** `is_player_flying_with_elytra`

玩家使用鞘翅滑翔时满足。

### 玩家完全冻僵

**标识符：** `is_player_fully_frozen`

玩家被细雪完全冻僵，生命值栏中出现冻结之心时满足。

### 玩家位于生物群系中

**标识符：** `is_player_in_biome`

玩家位于指定生物群系时满足。

- 值：生物群系的键，例如 `minecraft:birch_forest`。在世界中时，字段会提供生物群系建议。

### 玩家位于维度中

**标识符：** `is_player_in_dimension`

玩家位于指定维度时满足。

- 值：维度的键：`minecraft:overworld`、`minecraft:the_nether`、`minecraft:the_end` 或某个模组添加的维度。在世界中时，字段会提供维度建议。

### 玩家处于流体中

**标识符：** `is_player_in_fluid`

玩家处于任意流体中时满足，例如水或熔岩。

### 玩家处于熔岩中

**标识符：** `is_player_in_lava`

玩家处于熔岩中时满足。

### 玩家处于细雪中

**标识符：** `is_player_in_powder_snow`

玩家处于细雪中时满足。

### 玩家位于结构中

**标识符：** `is_player_in_structure`

玩家位于指定结构内部时满足。需要服务器端安装 FancyMenu。

- 值：结构的键，例如 `minecraft:village_plains`。在世界中时，字段会提供结构建议。

### 玩家处于水中

**标识符：** `is_player_in_water`

玩家处于水中时满足，即使只是部分浸入水中也算。

### 玩家正在跳跃或下落

**标识符：** `is_player_jumping`

玩家处于空中时满足。游泳、处于流体中、使用鞘翅飞行、睡觉和爬行均不算。

### 玩家为左撇子

**标识符：** `is_left_handed`

Minecraft 的皮肤自定义选项中，“主手”设为“左手”时满足。

### 玩家中毒

**标识符：** `is_player_poisoned`

玩家拥有中毒效果，且生命值栏中的心显示为中毒状态时满足。

### 玩家骑乘着有生命值的实体

**标识符：** `is_player_riding_entity_with_health`

玩家骑乘生物时满足，例如马或猪。船和矿车不算。

### 玩家正在骑乘实体/载具

**标识符：** `is_player_riding_entity`

玩家骑乘任何东西时满足，例如马、船或矿车。

### 玩家正在骑乘可跳跃的实体

**标识符：** `is_player_riding_jumpable_entity`

玩家骑乘可以跳跃的实体时满足，例如马。

### 玩家正在疾跑

**标识符：** `is_player_running`

玩家正在疾跑时满足。

### 玩家正在潜行

**标识符：** `is_player_sneaking`

玩家正在潜行时满足。

### 玩家正在游泳

**标识符：** `is_player_swimming`

玩家正在游泳时满足。

### 玩家在水下

**标识符：** `is_player_under_water`

玩家的头部位于水下时满足。

### 玩家正在使用物品

**标识符：** `is_player_using_item`

玩家正在使用物品时满足，例如进食、喝药水或拉弓。

### 玩家头戴南瓜

**标识符：** `is_player_wearing_pumpkin`

玩家头上戴着雕刻过的南瓜时满足。

### 玩家凋零

**标识符：** `is_player_withered`

玩家拥有凋零效果，且生命值栏中的心显示为凋零状态时满足。

### 正在下雨

**标识符：** `is_raining`

玩家所在位置正在下雨时满足。

### 单人游戏

**标识符：** `fancymenu_loading_requirement_is_singpleplayer`

玩家处于单人游戏世界中时满足。

### 正在下雪

**标识符：** `is_snowing`

玩家所在位置正在下雪时满足。

### 旁观者模式

**标识符：** `fancymenu_visibility_requirement_is_spectator`

玩家处于旁观者模式时满足。

### 生存模式

**标识符：** `fancymenu_visibility_requirement_is_survival`

玩家处于生存模式时满足。

### 正在打雷

**标识符：** `is_thundering`

发生雷暴时满足。

### 世界已加载

**标识符：** `fancymenu_loading_requirement_is_world_loaded`

玩家处于单人或多人游戏世界中时满足。

### 玩家刚才处于细雪中

**标识符：** `was_player_in_powder_snow`

玩家刚刚处于细雪中时满足。

## 其他

### 游戏语言为

**标识符：** `fancymenu_loading_requirement_is_language`

Minecraft 使用指定语言时满足。

- 值：语言代码，例如 `en_us` 或 `de_de`。字段会提供所有语言的建议。

### 已加载模组

**标识符：** `fancymenu_loading_requirement_is_mod_loaded`

已安装指定模组时满足。

- 值：模组 ID，例如 `jei`。字段会提供你已安装模组的 ID 建议。多个 ID 用逗号分隔：所有模组都必须安装。`optifine` 用于检测 OptiFine。

### 数值为

**标识符：** `fancymenu_visibility_requirement_is_number`

比较两个数值。可以在字段中使用占位符或变量，例如 `$$coins`。

- **比较模式**：**等于**、**大于**、**小于**、**大于或等于**或**小于或等于**。
- **数值**：要检查的数值，例如 `$$coins`。
- **与此数值比较**：用于比较的数值，例如 `100`。

支持小数，例如 `2.5`。字段内容不是数值时，条件永远不会满足。

### 资源包已启用

**标识符：** `is_resource_pack_enabled`

资源包已启用时满足。

- 值：资源包屏幕中显示的名称，例如 `Programmer Art`，或其 ID。大小写不敏感。

### Rinku 已加载

**标识符：** `is_rinku_loaded`

已安装 [Rinku](https://modrinth.com/mod/rinku) 模组时满足。[浏览器元素](/elements#browser)和旧版 [Rinku 视频类型](/video#requirements)需要此模组。

### 服务器 IP 为

**标识符：** `fancymenu_visibility_requirement_is_server_ip`

玩家正在指定服务器上时满足。

- 值：服务器地址，例如 `play.example.net`。如果填写了端口，例如 `play.example.net:25566`，端口也必须匹配。

### 服务器在线

**标识符：** `fancymenu_loading_requirement_is_server_online`

服务器在线时满足。FancyMenu 会在后台大约每 30 秒 ping 一次，因此游戏启动后可能需要稍等片刻。

- 值：服务器地址，例如 `play.example.net`。

### 文本为

**标识符：** `fancymenu_visibility_requirement_is_text`

比较两个文本。可以在字段中使用占位符或变量，例如 `$$key_name`。

- **比较模式**：**等于**、**包含**、**开头为**或**结尾为**。
- **文本**：要检查的文本。
- **与此文本比较**：用于比较的文本。

大小写敏感。

### 变量值 (FM Variable)

**标识符：** `fancymenu_visibility_requirement_is_variable_value`

你的某个[变量](/variables)具有指定值时满足。

- **变量名称**：变量名称，不包括 `$$`。字段会提供你的变量建议。
- **要检查的变量值**：指定值，例如 `on`。必须与整个值完全匹配，且区分大小写。

变量不存在时永远不会满足。对于列表变量，此条件会比较所有条目的 JSON 数组，例如 `["apple","banana"]`。若要检查其中一个条目，请使用**列表包含条目 (FM Variable)**。

### 列表包含条目 (FM Variable)

**标识符：** `list_contains_entry`

[列表变量](/variables#text-and-list-variables)包含指定条目时满足。

- **列表变量名称**：列表名称，不包括 `$$`。字段会提供列表变量建议；如果你输入了文本变量的名称，也会发出警告。
- **要查找的条目**：要查找的条目。必须与整个条目匹配，而非仅匹配其中一部分。
- **忽略大小写**：开启后，`Apple` 也会匹配 `apple`。

列表不存在时永远不会满足。

### 鼠标按键已按下

**标识符：** `mouse_click`

鼠标按键按住时满足。若要在每次点击时仅运行一次操作，请改用[**鼠标按键点击时**](/listeners#on-mouse-button-clicked)监听器。

- 值：`left` 或 `right`。

### 每个会话仅一次

**标识符：** `once_per_session`

首次检查时满足，此后直到游戏重启都不再满足。每个副本都会单独计数。

如果你希望元素在每次游戏会话中仅显示一次，使用元素的[**每个会话仅加载一次**](/element-visibility#load-once-per-session)选项会更简单：元素会一直保留，直到打开新的屏幕。
