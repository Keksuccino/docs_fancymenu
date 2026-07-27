---
title: 条件（要求）
description: 如何使用加载要求。
---

# 要求

要求（在某些菜单中称为 **加载要求**）会根据悬停状态、窗口大小或世界是否已加载等条件显示或隐藏内容。

你可以将它们用于[元素](./elements)、整个布局以及[动作脚本](./action-scripts)。

# 将要求添加到元素

要向某个元素添加要求，请右键单击它并选择 **加载要求**。

菜单打开时会检查这些要求，因此当某个条件发生变化时，元素会随之更新。

# 整个布局的要求

你也可以通过右键单击 **编辑器背景**，然后点击 **加载要求 [布局范围]** 来更改整个布局的可见性。

当布局范围的结果发生变化时，FancyMenu 会重建当前屏幕，并应用其要求已通过的布局。

# 动作脚本

要求也可以用于动作脚本。
你可以在动作脚本编辑器界面中添加它们，并用它们仅在满足要求条件时执行特定动作。

# 组合要求

- 组外的要求使用 **AND**，因此它们都必须通过。
- 在组内，可以选择 **AND** 或 **OR**。
- 使用 **IF NOT** 可对单个要求取反。

这些规则同样适用于元素、布局和动作脚本。

# 要求值

对于需要值的要求，请使用 **编辑要求值**，并按照编辑器中显示的说明进行操作。某些字段支持 **TAB** 自动补全。

如果导入的要求在更改 FancyMenu 或附加组件后不再生效，请在要求界面中编辑它，并检查 `logs/latest.log` 中的错误。

要求编辑器支持右键上下文菜单、键盘导航、搜索、撤销/重做（`Ctrl/Command + Z` / `Ctrl/Command + Y`）以及使用 `Ctrl/Command + S` 保存。

# 详细要求

本节列出 FancyMenu 内置的要求。

## 元素是否被悬停（`fancymenu_visibility_requirement_is_element_hovered`）

**用途：** 检查某个特定元素是否被鼠标光标悬停。

**值：** 必需 — 目标元素的[元素标识符](./element-identifiers)（例如 `some_element_ID`）。

## 元素是否聚焦（`is_element_focused`）

**用途：** 检查某个特定元素当前是否具有键盘焦点（例如文本框或已聚焦的按钮）。

**值：** 必需 — 目标元素的元素 ID（与编辑器中显示的 ID 相同）

> [!NOTE]
> 焦点和悬停是不同状态。即使指针离开某个元素，该元素仍可能保持聚焦外观；点击或键盘导航都可以使其获得焦点。

## 任意元素是否被悬停（`fancymenu_visibility_requirement_is_any_element_hovered`）

**用途：** 检查当前活动自定义层中的可见/可渲染元素，包括由叠加布局提供的元素。

**值：** 不需要

## 任意按钮是否被悬停（`fancymenu_visibility_requirement_is_any_button_hovered`）

**用途：** 检查当前活动自定义层中的任意可见/可渲染原版按钮或自定义按钮是否被悬停，包括由叠加布局提供的按钮。

**值：** 不需要

## 布局是否启用（`fancymenu_visibility_requirement_is_layout_enabled`）

**用途：** 检查某个特定布局当前是否已启用。

**值：** 必需 — 布局名称（例如 `my_cool_main_menu_layout`）

## 调度器是否运行中（`fancymenu_visibility_requirement_is_scheduler_running`）

**用途：** 检查某个[调度器](./schedulers)当前是否正在运行。

**值：** 必需 — 调度器 ID（例如 `my_scheduler`）

## 是否为 GUI 缩放（`fancymenu_loading_requirement_is_gui_scale`）

**用途：** 检查当前 GUI 缩放是否符合某些条件。

**值：** 必需 — 等于使用数字，`>` 表示大于，`<` 表示小于。

多个以逗号分隔的条件会以 AND 组合。例如，`>1,<4` 仅在 GUI 缩放大于 `1` 且小于 `4` 时通过。

## 按钮是否激活（`fancymenu_visibility_requirement_is_button_active`）

**用途：** 检查某个特定按钮是否处于激活状态（可点击）。

**值：** 必需 — 目标按钮的元素 ID（例如 "some_element_ID"）

## 是否为屏幕标题（`is_menu_title`）

**用途：** 检查屏幕的显示标题是否与特定文本或本地化键匹配。此项只会检查屏幕的显示名称/标题，例如 "Options" 或 "Pause"。不会检查菜单/屏幕标识符（如 `title_screen`）！

**值：** 必需 — 屏幕的精确标题文本或本地化键

## 按键是否按下（`is_key_pressed`）

**用途：** 检查某个特定键盘按键当前是否正在被按下。

**值：** 必需 — 目标按键的键码。在编辑要求值时通过 UI 选择。

## 是否打开了任意屏幕（`is_any_screen_open`）

**用途：** 检查当前是否有任何屏幕/菜单打开（如果没有显示任何屏幕则返回 false）。

**值：** 不需要

## MC 调试叠加层是否启用（`is_debug_overlay_enabled`）

**用途：** 检查 F3 调试叠加层当前是否可见。

**值：** 不需要

## 当前光标类型是否匹配（`is_active_cursor_type`）

**用途：** 检查 FancyMenu 当前激活的光标类型是否匹配某个标准光标类型。

**值：** 必需 — 光标类型：`normal`、`writing`、`crosshair`、`pointing_hand`、`resize_horizontal`、`resize_vertical`、`resize_nwse`、`resize_nesw`、`resize_all` 或 `not_allowed`

## 自定义菜单栏是否可见（`is_customization_menu_bar_visible`）

**用途：** 检查 FancyMenu 的自定义菜单栏当前是否可见。

**值：** 不需要

## 是否启用整合包模式（`is_modpack_mode_enabled`）

**用途：** 检查 FancyMenu 的整合包模式是否已启用。

**值：** 不需要

## 鼠标按键是否按下（`mouse_click`）

**用途：** 在特定鼠标按键按住期间返回 true。这不是一次性的点击事件；如果某个动作应在每次点击时只执行一次，请使用[**鼠标按键点击时**监听器](./listeners#on-mouse-button-clicked-mouse_button_clicked)。

**值：** 必需 — `left` 或 `right`，用于指定要检查的鼠标按键

## 是否全屏（`fancymenu_loading_requirement_is_fullscreen`）

**用途：** 检查游戏当前是否处于全屏模式。

**值：** 不需要

## 是否为窗口宽度（`fancymenu_loading_requirement_is_window_width`）

**用途：** 检查游戏窗口宽度是否匹配特定值。

**值：** 必需 — 以像素为单位的窗口宽度（例如 "1920"）。可以使用逗号分隔多个值。

## 是否为窗口高度（`fancymenu_loading_requirement_is_window_height`）

**用途：** 检查游戏窗口高度是否匹配特定值。

**值：** 必需 — 以像素为单位的窗口高度（例如 "1080"）。可以使用逗号分隔多个值。

## 窗口宽度是否大于（`fancymenu_loading_requirement_is_window_width_bigger_than`）

**用途：** 检查游戏窗口宽度是否大于某个特定值。

**值：** 必需 — 以像素为单位的窗口宽度（例如 "1920"）

## 窗口高度是否大于（`fancymenu_loading_requirement_is_window_height_bigger_than`）

**用途：** 检查游戏窗口高度是否大于某个特定值。

**值：** 必需 — 以像素为单位的窗口高度（例如 "1080"）

## 是否多人游戏（`fancymenu_loading_requirement_is_multiplayer`）

**用途：** 检查玩家当前是否在多人世界中。

**值：** 不需要

## 是否单人游戏（`fancymenu_loading_requirement_is_singpleplayer`）

**用途：** 检查玩家当前是否在单人世界中。

**值：** 不需要

## 世界是否已加载（`fancymenu_loading_requirement_is_world_loaded`）

**用途：** 检查当前是否已加载任何世界。

**值：** 不需要

## 是否为冒险模式（`fancymenu_visibility_requirement_is_adventure`）

**用途：** 检查玩家当前是否处于冒险游戏模式。

**值：** 不需要

## 是否为创造模式（`fancymenu_visibility_requirement_is_creative`）

**用途：** 检查玩家当前是否处于创造游戏模式。

**值：** 不需要

## 是否为旁观模式（`fancymenu_visibility_requirement_is_spectator`）

**用途：** 检查玩家当前是否处于旁观游戏模式。

**值：** 不需要

## 是否为生存模式（`fancymenu_visibility_requirement_is_survival`）

**用途：** 检查玩家当前是否处于生存游戏模式。

**值：** 不需要

## 是否为游戏模式（`is_gamemode`）

**用途：** 检查玩家是否处于某个特定游戏模式。

**值：** 必需 — 游戏模式名称（例如 "creative"、"survival"、"adventure"、"spectator"）

## 是否为难度（`is_difficulty`）

**用途：** 检查当前游戏难度是否匹配某个特定值。

**值：** 必需 — 难度名称（例如 "peaceful"、"easy"、"normal"、"hard"）

## 是否为极限模式（`is_hardcore`）

**用途：** 检查当前加载的世界是否为极限模式。

**值：** 不需要

## 是否为摄像机视角（`is_camera_perspective`）

**用途：** 检查当前摄像机视角是否匹配某个特定视角。

**值：** 必需 — `first_person`、`third_person_back` 或 `third_person_front`

## 是否正在下雨（`is_raining`）

**用途：** 检查玩家所在位置当前是否正在下雨。

**值：** 不需要

## 是否正在打雷（`is_thundering`）

**用途：** 检查玩家所在世界当前是否有雷暴。

**值：** 不需要

## 是否为晴天（`is_clear_weather`）

**用途：** 检查当前天气是否晴朗（未下雨或未打雷）。

**值：** 不需要

## 是否在下雪（`is_snowing`）

**用途：** 检查玩家所在位置当前是否正在下雪。

**值：** 不需要

## 玩家是否在奔跑（`is_player_running`）

**用途：** 检查玩家当前是否在疾跑。

**值：** 不需要

## 玩家是否在潜行（`is_player_sneaking`）

**用途：** 检查玩家当前是否在潜行/蹲伏。

**值：** 不需要

## 玩家是否正在使用物品（`is_player_using_item`）

**用途：** 检查玩家当前是否正在使用物品。

**值：** 不需要

## 玩家是否在游泳（`is_player_swimming`）

**用途：** 检查玩家当前是否在游泳。

**值：** 不需要

## 玩家是否正在跳跃或下落（`is_player_jumping`）

**用途：** 当玩家处于正常跳跃或下落的空中状态时返回 true。不包括游泳、流体、鞘翅飞行、睡眠、视觉游泳和爬行。

**值：** 不需要

## 玩家是否在水下（`is_player_under_water`）

**用途：** 检查玩家是否完全处于水下。

**值：** 不需要

## 玩家是否在水中（`is_player_in_water`）

**用途：** 检查玩家是否在水中（可以是部分浸没）。

**值：** 不需要

## 玩家是否在熔岩中（`is_player_in_lava`）

**用途：** 检查玩家是否在熔岩中。

**值：** 不需要

## 玩家是否在流体中（`is_player_in_fluid`）

**用途：** 检查玩家是否在任意流体中（水、熔岩等）。

**值：** 不需要

## 玩家是否骑乘实体/载具（`is_player_riding_entity`）

**用途：** 检查玩家是否正在骑乘任意实体。

**值：** 不需要

## 玩家是否骑乘可跳跃实体（`is_player_riding_jumpable_entity`）

**用途：** 检查玩家是否正在骑乘可跳跃的实体（例如马）。

**值：** 不需要

## 玩家是否骑乘具有生命值的实体（`is_player_riding_entity_with_health`）

**用途：** 检查玩家是否正在骑乘有生命值的生物实体（例如动物，不包括船）。

**值：** 不需要

## 玩家是否在细雪中（`is_player_in_powder_snow`）

**用途：** 检查玩家当前是否处于细雪中。

**值：** 不需要

## 玩家曾经在细雪中（`was_player_in_powder_snow`）

**用途：** 检查玩家是否曾处于细雪中（用于离开后仍持续的效果）。

**值：** 不需要

## 玩家是否戴着南瓜（`is_player_wearing_pumpkin`）

**用途：** 检查玩家头上是否戴着雕刻南瓜。

**值：** 不需要

## 玩家是否正在使用鞘翅飞行（`is_player_flying_with_elytra`）

**用途：** 检查玩家当前是否正在使用鞘翅飞行。

**值：** 不需要

## 玩家是否在创造飞行（`is_player_creative_flying`）

**用途：** 检查玩家是否正在创造模式中飞行。

**值：** 不需要

## 玩家是否拥有吸收生命值（`has_player_absorption_hearts`）

**用途：** 检查玩家是否拥有任何吸收生命值（金色心心）。

**值：** 不需要

## 玩家是否凋零（`is_player_withered`）

**用途：** 检查玩家是否受凋零效果影响。

**值：** 不需要

## 玩家是否完全冻结（`is_player_fully_frozen`）

**用途：** 检查玩家是否完全冻结（通常由细雪造成）。

**值：** 不需要

## 玩家是否中毒（`is_player_poisoned`）

**用途：** 检查玩家是否受中毒效果影响。

**值：** 不需要

## 玩家是否在生物群系中（`is_player_in_biome`）

**用途：** 检查玩家是否位于某个特定生物群系中。

**值：** 必需 — 生物群系标识符（例如 `minecraft:birch_forest`）

## 玩家是否在维度中（`is_player_in_dimension`）

**用途：** 检查玩家是否位于某个特定维度中。

**值：** 必需 — 维度标识符（例如 `minecraft:overworld`、`minecraft:the_nether`、`minecraft:the_end`）

## 玩家是否在结构中（`is_player_in_structure`）

**用途：** 检查玩家当前是否位于某个特定结构内。对于服务器世界，需要服务器端安装 FancyMenu。

**值：** 必需 — 结构标识符（例如 `minecraft:village`）

## 附近是否有实体（`is_entity_nearby`）

**用途：** 检查玩家一定半径内是否存在某种特定实体类型。

**值：** 必需 — 格式："radius:entity_id"（例如 `10:minecraft:pig` - 检查 10 格内是否有猪）

## 效果是否激活（`is_effect_active`）

**用途：** 检查玩家身上是否激活了某个特定药水效果。

**值：** 必需 — 效果标识符（例如 `minecraft:speed`、`minecraft:strength`）

## 是否有任意效果激活（`is_any_effect_active`）

**用途：** 检查玩家是否拥有任何激活中的药水效果。

**值：** 不需要

## 玩家是否为左手模式（`is_left_handed`）

**用途：** 检查玩家是否在游戏选项中设置为左手模式。

**值：** 不需要

## 背包槽是否已填充（`is_inventory_slot_filled`）

**用途：** 检查某个特定背包槽位是否包含物品。

**值：** 必需 — 槽位编号（主背包为 0-35，其中 0-8 为快捷栏）

## 背包中物品是否被悬停（`is_item_hovered_in_inventory`）

**用途：** 检查光标是否悬停在背包界面中的任意物品上。

**值：** 不需要

## 光标是否正在拿着背包物品（`is_cursor_holding_inventory_item`）

**用途：** 检查光标当前是否拿着一个背包物品堆叠。

**值：** 不需要

## 快捷栏槽位是否已选中（`is_hotbar_slot_active`）

**用途：** 检查某个特定快捷栏槽位当前是否已选中。

**值：** 必需 — 快捷栏槽位编号（0-8）

## 是否具有玩家权限等级（`fancymenu_loading_requirement_has_player_permission_level`）

**用途：** 检查玩家在当前世界或服务器上是否至少拥有指定的权限/OP 等级。

**值：** 必需 — 权限等级数字（0-4，其中 4 为服务器管理员）

## 攻击强度是否减弱（`is_attack_strength_weakened`）

**用途：** 检查玩家的攻击强度当前是否减弱（未完全蓄满）。

**值：** 不需要

## 是否为实时时间的日（`fancymenu_visibility_requirement_is_realtime_day`）

**用途：** 检查当前现实世界中的日期是否与特定值匹配。

**值：** 必需 — 日号（1-31）。可以使用逗号分隔多个值。

## 是否为实时时间的小时（`fancymenu_visibility_requirement_is_realtime_hour`）

**用途：** 检查当前现实世界中的小时是否与特定值匹配。

**值：** 必需 — 24 小时制小时（0-23）。可以使用逗号分隔多个值。

## 是否为实时时间的分钟（`fancymenu_visibility_requirement_is_realtime_minute`）

**用途：** 检查当前现实世界中的分钟是否与特定值匹配。

**值：** 必需 — 分钟（0-59）。可以使用逗号分隔多个值。

## 是否为实时时间的月（`fancymenu_visibility_requirement_is_realtime_month`）

**用途：** 检查当前现实世界中的月份是否与特定值匹配。

**值：** 必需 — 月份数字（1-12，其中 1 为一月）。可以使用逗号分隔多个值。

## 是否为实时时间的秒（`fancymenu_visibility_requirement_is_realtime_second`）

**用途：** 检查当前现实世界中的秒数是否与特定值匹配。

**值：** 必需 — 秒数（0-59）。可以使用逗号分隔多个值。

## 是否为实时时间的星期几（`fancymenu_visibility_requirement_is_realtime_week_day`）

**用途：** 检查当前现实世界中的星期几是否与特定值匹配。

**值：** 必需 — 以数字表示的星期几（1-7，其中 1 为星期日）。可以使用逗号分隔多个值。

## 是否为实时时间的年（`fancymenu_visibility_requirement_is_realtime_year`）

**用途：** 检查当前现实世界中的年份是否与特定值匹配。

**值：** 必需 — 完整年份（例如 "2023"）。可以使用逗号分隔多个值。

## 文件/文件夹是否存在（`fancymenu_loading_requirement_file_exists`）

**用途：** 检查文件或目录是否存在。

**值：** 必需 — 相对于当前游戏目录的路径，或以 `.minecraft/` 开头的路径（用于常规 Minecraft 目录）。文件和目录都视为存在。

## 是否为 Linux 系统（`fancymenu_loading_requirement_is_os_linux`）

**用途：** 检查当前平台是否既不是 Windows 也不是 macOS。通常对应 Linux 环境。

**值：** 不需要

## 是否为 macOS 系统（`fancymenu_loading_requirement_is_os_macos`）

**用途：** 检查操作系统是否为 macOS。

**值：** 不需要

## 是否为 Windows 系统（`fancymenu_loading_requirement_is_os_windows`）

**用途：** 检查操作系统是否为 Windows。

**值：** 不需要

## 是否可连接互联网（`is_internet_connection_available`）

**用途：** 检查当前是否有可用的互联网连接。

**值：** 不需要

## 是否为游戏语言（`fancymenu_loading_requirement_is_language`）

**用途：** 检查当前游戏语言是否与特定值匹配。

**值：** 必需 — 语言代码（例如 `en_us` 表示英语）

## 是否已加载模组（`fancymenu_loading_requirement_is_mod_loaded`）

**用途：** 检查某个特定模组是否已加载。

**值：** 必需 — 模组 ID（例如 `fancymenu`、`jei`）。也可以使用 `optifine` 检查 OptiFine。支持多个以逗号分隔的模组 ID；列出的所有模组都必须已加载。

## 是否已加载 MCEF（`is_mcef_loaded`）

**用途：** 检查 MCEF（Minecraft Chromium Embedded Framework）是否已安装并初始化。MCEF 是[浏览器元素](./elements#browser)和[已弃用的基于 MCEF 的视频类型](./video#requirements)所必需的；[原生视频功能](./video)使用 Watermedia。

**值：** 不需要

## 是否为数字（`fancymenu_visibility_requirement_is_number`）

**用途：** 提供具有不同比较模式的高级数字比较。

**值：** 必需 — 复杂格式：`["mode":"comparison_mode","number":"value1","compare_with":"value2"]$`，其中 `comparison_mode` 可以是 `equals`、`bigger-than`、`smaller-than`、`bigger-than-or-equals` 或 `smaller-than-or-equals`

## 是否为文本（`fancymenu_visibility_requirement_is_text`）

**用途：** 提供具有不同比较模式的高级文本比较。

**值：** 必需 — 复杂格式：`["mode":"comparison_mode","text":"text1","compare_with":"text2"]$`，其中 `comparison_mode` 可以是 `equals`、`contains`、`starts-with` 或 `ends-with`

## 是否为服务器 IP（`fancymenu_visibility_requirement_is_server_ip`）

**用途：** 检查当前服务器 IP 是否与特定值匹配。

**值：** 必需 — 服务器 IP 地址（可带或不带端口）

## 服务器是否在线（`fancymenu_loading_requirement_is_server_online`）

**用途：** 检查某个特定服务器是否在线且可访问。

**值：** 必需 — 服务器 IP 地址（可带或不带端口）

## 资源包是否启用（`is_resource_pack_enabled`）

**用途：** 检查某个特定资源包当前是否已选中/已激活。

**值：** 必需 — 资源包标题或包 ID（例如 `Programmer Art` 或该资源包的 ID）

## 变量值是否匹配（FM 变量）（`fancymenu_visibility_requirement_is_variable_value`）

**用途：** 检查 FancyMenu 变量是否具有特定值。

**值：** 必需 — 格式："variable_name:expected_value"

## 每个会话仅一次（`once_per_session`）

**用途：** 每个已配置实例在每个游戏会话中只会返回 true 一次。不同实例会独立追踪。

**值：** 不需要
