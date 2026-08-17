---
title: 条件（要求）
description: 如何使用加载要求。
---
# 要求

要求（在某些菜单中称为**加载要求**）会根据悬停状态、窗口大小或世界是否已加载等条件，显示或隐藏内容。

你可以将它们用于[元素](./elements)、整个布局以及[操作脚本](./action-scripts)。

# 为元素添加要求

要为元素添加要求，请右键单击该元素，然后选择**加载要求**。

菜单打开时会持续检查要求，因此当条件发生变化时，元素也会随之更新。

# 应用于整个布局的要求

你也可以通过右键单击**编辑器背景**，然后点击**加载要求 [应用于整个布局]**，来更改整个布局的可见性。

当应用于整个布局的结果发生变化时，FancyMenu 会重建当前屏幕，并应用当前满足要求的布局。

# 操作脚本

要求也可以用于操作脚本。
你可以在操作脚本编辑器屏幕中添加要求，并使用它们仅在要求条件满足时执行特定操作。

# 组合要求

- 组外的要求使用**与（AND）**，因此所有要求都必须通过。
- 在组内，可以选择**与（AND）**或**或（OR）**。
- 使用**如果不（IF NOT）**来反转单个要求。

这些规则对元素、布局和操作脚本都相同。

# 要求值

对于需要值的要求，请使用**编辑要求值**，并按照编辑器中显示的说明操作。某些字段支持使用 **TAB** 键自动补全。

如果导入的要求在更改 FancyMenu 或附加组件后不再生效，请在要求界面中编辑它，并检查 `logs/latest.log` 中的错误。

要求编辑器支持右键上下文菜单、键盘导航、搜索、撤销/重做（`Ctrl/Command + Z` / `Ctrl/Command + Y`），以及使用 `Ctrl/Command + S` 保存。

# 要求详解

本节列出了 FancyMenu 内置的要求。

## 元素是否被悬停（`fancymenu_visibility_requirement_is_element_hovered`）

**用途：**检查鼠标指针是否悬停在指定元素上。

**值：**必填——目标元素的[元素标识符](./element-identifiers)（例如 `some_element_ID`）。

## 元素是否获得焦点（`is_element_focused`）

**用途：**检查指定元素当前是否获得键盘焦点（例如文本框或获得焦点的按钮）。

**值：**必填——目标元素的元素 ID（与编辑器中显示的 ID 相同）。

> [!NOTE]
> 焦点和悬停是不同的状态。指针离开元素后，元素仍可能保持获得焦点时的外观；单击或使用键盘导航都可以使元素获得焦点。

## 是否有任意元素被悬停（`fancymenu_visibility_requirement_is_any_element_hovered`）

**用途：**检查当前活动自定义层中的可见/可渲染元素，包括由堆叠布局提供的元素。

**值：**不需要

## 是否有任意按钮被悬停（`fancymenu_visibility_requirement_is_any_button_hovered`）

**用途：**检查当前活动自定义层中是否有任意可见/可渲染的原版或自定义按钮被悬停，包括由堆叠布局提供的按钮。

**值：**不需要

## 布局是否启用（`fancymenu_visibility_requirement_is_layout_enabled`）

**用途：**检查指定布局当前是否已启用。

**值：**必填——布局名称（例如 `my_cool_main_menu_layout`）。

## 调度器是否运行（`fancymenu_visibility_requirement_is_scheduler_running`）

**用途：**检查[调度器](./schedulers)当前是否正在运行。

**值：**必填——调度器 ID（例如 `my_scheduler`）。

## GUI 缩放是否符合条件（`fancymenu_loading_requirement_is_gui_scale`）

**用途：**检查当前 GUI 缩放是否符合指定条件。

**值：**必填——使用数字表示相等，使用 `>` 表示大于，或使用 `<` 表示小于。

多个以逗号分隔的条件会以 AND 组合。例如，`>1,<4` 仅在 GUI 缩放大于 `1` 且小于 `4` 时通过。

## 按钮是否处于活动状态（`fancymenu_visibility_requirement_is_button_active`）

**用途：**检查指定按钮是否处于活动状态（可点击）。

**值：**必填——目标按钮的元素 ID（例如 "some_element_ID"）。

## 是否为屏幕标题（`is_menu_title`）

**用途：**检查屏幕的显示标题是否与指定文本或本地化键匹配。此要求只会检查屏幕的显示名称/标题，例如 "Options" 或 "Pause"，不会检查菜单/屏幕标识符（例如 `title_screen`）！

**值：**必填——屏幕的确切标题文本或本地化键。

## 是否按下指定按键（`is_key_pressed`）

**用途：**检查指定键盘按键当前是否被按下。

**值：**必填——目标按键的键码。编辑要求值时通过界面选择。

## 是否打开任意屏幕（`is_any_screen_open`）

**用途：**检查当前是否打开了任意屏幕/菜单（没有显示屏幕时返回 false）。

**值：**不需要

## MC 调试叠加层是否启用（`is_debug_overlay_enabled`）

**用途：**检查 F3 调试叠加层当前是否可见。

**值：**不需要

## 当前光标类型（`is_active_cursor_type`）

**用途：**检查 FancyMenu 当前使用的光标类型是否与指定的标准光标类型匹配。

**值：**必填——光标类型：`normal`、`writing`、`crosshair`、`pointing_hand`、`resize_horizontal`、`resize_vertical`、`resize_nwse`、`resize_nesw`、`resize_all` 或 `not_allowed`。

## 自定义菜单栏是否可见（`is_customization_menu_bar_visible`）

**用途：**检查 FancyMenu 的自定义菜单栏当前是否可见。

**值：**不需要

## 模组包模式是否启用（`is_modpack_mode_enabled`）

**用途：**检查 FancyMenu 的模组包模式是否已启用。

**值：**不需要

## 鼠标按键是否按下（`mouse_click`）

**用途：**在指定鼠标按键被按住期间返回 true。这不是一次性单击事件；如果某个操作应在每次单击时只运行一次，请使用[**鼠标按键单击时**监听器](./listeners#on-mouse-button-clicked-mouse_button_clicked)。

**值：**必填——使用 `left` 或 `right` 指定要检查的鼠标按键。

## 是否为全屏（`fancymenu_loading_requirement_is_fullscreen`）

**用途：**检查游戏当前是否处于全屏模式。

**值：**不需要

## 窗口宽度是否符合条件（`fancymenu_loading_requirement_is_window_width`）

**用途：**检查游戏窗口宽度是否与指定值匹配。

**值：**必填——以像素为单位的窗口宽度（例如 "1920"）。可以使用逗号分隔来提供多个值。

## 窗口高度是否符合条件（`fancymenu_loading_requirement_is_window_height`）

**用途：**检查游戏窗口高度是否与指定值匹配。

**值：**必填——以像素为单位的窗口高度（例如 "1080"）。可以使用逗号分隔来提供多个值。

## 窗口宽度是否大于（`fancymenu_loading_requirement_is_window_width_bigger_than`）

**用途：**检查游戏窗口宽度是否大于指定值。

**值：**必填——以像素为单位的窗口宽度（例如 "1920"）。

## 窗口高度是否大于（`fancymenu_loading_requirement_is_window_height_bigger_than`）

**用途：**检查游戏窗口高度是否大于指定值。

**值：**必填——以像素为单位的窗口高度（例如 "1080"）。

## 是否为多人游戏（`fancymenu_loading_requirement_is_multiplayer`）

**用途：**检查玩家当前是否处于多人游戏世界中。

**值：**不需要

## 是否为单人游戏（`fancymenu_loading_requirement_is_singpleplayer`）

**用途：**检查玩家当前是否处于单人游戏世界中。

**值：**不需要

## 世界是否已加载（`fancymenu_loading_requirement_is_world_loaded`）

**用途：**检查当前是否加载了任意世界。

**值：**不需要

## 是否为冒险模式（`fancymenu_visibility_requirement_is_adventure`）

**用途：**检查玩家当前是否处于冒险游戏模式。

**值：**不需要

## 是否为创造模式（`fancymenu_visibility_requirement_is_creative`）

**用途：**检查玩家当前是否处于创造游戏模式。

**值：**不需要

## 是否为旁观模式（`fancymenu_visibility_requirement_is_spectator`）

**用途：**检查玩家当前是否处于旁观游戏模式。

**值：**不需要

## 是否为生存模式（`fancymenu_visibility_requirement_is_survival`）

**用途：**检查玩家当前是否处于生存游戏模式。

**值：**不需要

## 是否为指定游戏模式（`is_gamemode`）

**用途：**检查玩家是否处于指定的游戏模式。

**值：**必填——游戏模式名称（例如 "creative"、"survival"、"adventure"、"spectator"）。

## 是否为指定难度（`is_difficulty`）

**用途：**检查当前游戏难度是否与指定值匹配。

**值：**必填——难度名称（例如 "peaceful"、"easy"、"normal"、"hard"）。

## 是否为极限模式（`is_hardcore`）

**用途：**检查当前加载的世界是否处于极限模式。

**值：**不需要

## 是否为指定视角（`is_camera_perspective`）

**用途：**检查当前摄像机视角是否与指定视角匹配。

**值：**必填——`first_person`、`third_person_back` 或 `third_person_front`。

## 是否正在下雨（`is_raining`）

**用途：**检查玩家所在位置当前是否正在下雨。

**值：**不需要

## 是否正在打雷（`is_thundering`）

**用途：**检查玩家所在世界当前是否正在下雷暴。

**值：**不需要

## 是否为晴朗天气（`is_clear_weather`）

**用途：**检查当前天气是否晴朗（没有下雨或打雷）。

**值：**不需要

## 是否正在下雪（`is_snowing`）

**用途：**检查玩家所在位置当前是否正在下雪。

**值：**不需要

## 玩家是否正在疾跑（`is_player_running`）

**用途：**检查玩家当前是否正在疾跑。

**值：**不需要

## 玩家是否正在潜行（`is_player_sneaking`）

**用途：**检查玩家当前是否正在潜行/蹲下。

**值：**不需要

## 玩家是否正在使用物品（`is_player_using_item`）

**用途：**检查玩家当前是否正在使用物品。

**值：**不需要

## 玩家是否正在游泳（`is_player_swimming`）

**用途：**检查玩家当前是否正在游泳。

**值：**不需要

## 玩家是否正在跳跃或下落（`is_player_jumping`）

**用途：**当玩家处于普通跳跃或下落状态、在空中时返回 true。游泳、流体、鞘翅飞行、睡觉、视觉游泳和爬行状态不包括在内。

**值：**不需要

## 玩家是否完全在水下（`is_player_under_water`）

**用途：**检查玩家是否完全位于水下。

**值：**不需要

## 玩家是否在水中（`is_player_in_water`）

**用途：**检查玩家是否在水中（可以只是部分浸没）。

**值：**不需要

## 玩家是否在熔岩中（`is_player_in_lava`）

**用途：**检查玩家是否在熔岩中。

**值：**不需要

## 玩家是否在流体中（`is_player_in_fluid`）

**用途：**检查玩家是否处于任意流体中（水、熔岩等）。

**值：**不需要

## 玩家是否骑乘实体/载具（`is_player_riding_entity`）

**用途：**检查玩家是否正在骑乘任意实体。

**值：**不需要

## 玩家是否骑乘可跳跃实体（`is_player_riding_jumpable_entity`）

**用途：**检查玩家是否正在骑乘能够跳跃的实体（例如马）。

**值：**不需要

## 玩家是否骑乘具有生命值的实体（`is_player_riding_entity_with_health`）

**用途：**检查玩家是否正在骑乘具有生命值的生物实体（例如动物，不包括船）。

**值：**不需要

## 玩家是否处于细雪中（`is_player_in_powder_snow`）

**用途：**检查玩家当前是否处于细雪中。

**值：**不需要

## 玩家之前是否处于细雪中（`was_player_in_powder_snow`）

**用途：**检查玩家之前是否处于细雪中（用于离开细雪后仍会持续的效果）。

**值：**不需要

## 玩家是否佩戴南瓜（`is_player_wearing_pumpkin`）

**用途：**检查玩家头上是否佩戴雕刻南瓜。

**值：**不需要

## 玩家是否使用鞘翅飞行（`is_player_flying_with_elytra`）

**用途：**检查玩家当前是否正在使用鞘翅飞行。

**值：**不需要

## 玩家是否在创造模式飞行（`is_player_creative_flying`）

**用途：**检查玩家是否正在创造模式下飞行。

**值：**不需要

## 玩家是否拥有伤害吸收生命值（`has_player_absorption_hearts`）

**用途：**检查玩家是否拥有伤害吸收生命值（金色爱心）。

**值：**不需要

## 玩家是否受到凋零效果影响（`is_player_withered`）

**用途：**检查玩家是否受到凋零效果影响。

**值：**不需要

## 玩家是否完全冻结（`is_player_fully_frozen`）

**用途：**检查玩家是否完全冻结（通常由细雪造成）。

**值：**不需要

## 玩家是否中毒（`is_player_poisoned`）

**用途：**检查玩家是否受到中毒效果影响。

**值：**不需要

## 玩家是否处于指定生物群系（`is_player_in_biome`）

**用途：**检查玩家是否处于指定生物群系。

**值：**必填——生物群系标识符（例如 `minecraft:birch_forest`）。

## 玩家是否处于指定维度（`is_player_in_dimension`）

**用途：**检查玩家是否处于指定维度。

**值：**必填——维度标识符（例如 `minecraft:overworld`、`minecraft:the_nether`、`minecraft:the_end`）。

## 玩家是否处于指定结构中（`is_player_in_structure`）

**用途：**检查玩家当前是否位于指定结构内部。在服务器世界中，需要服务器安装 FancyMenu。

**值：**必填——结构标识符（例如 `minecraft:village`）。

## 附近是否有实体（`is_entity_nearby`）

**用途：**检查指定类型的实体是否在玩家的一定半径内。

**值：**必填——格式为“半径:实体 ID”（例如 `10:minecraft:pig`，检查 10 个方块内是否有猪）。

## 效果是否生效（`is_effect_active`）

**用途：**检查玩家身上是否有指定的药水效果生效。

**值：**必填——效果标识符（例如 `minecraft:speed`、`minecraft:strength`）。

## 是否有任意效果生效（`is_any_effect_active`）

**用途：**检查玩家是否有任意药水效果生效。

**值：**不需要

## 玩家是否为左撇子（`is_left_handed`）

**用途：**检查游戏选项中是否将玩家设置为左手模式。

**值：**不需要

## 背包槽位是否有物品（`is_inventory_slot_filled`）

**用途：**检查指定背包槽位是否包含物品。

**值：**必填——槽位编号（主背包为 0-35，其中 0-8 为快捷栏）。

## 背包中的物品是否被悬停（`is_item_hovered_in_inventory`）

**用途：**检查指针是否悬停在背包界面中的任意物品上。

**值：**不需要

## 光标是否拿着背包物品（`is_cursor_holding_inventory_item`）

**用途：**检查光标当前是否拿着背包物品堆。

**值：**不需要

## 是否选中快捷栏槽位（`is_hotbar_slot_active`）

**用途：**检查指定快捷栏槽位当前是否被选中。

**值：**必填——快捷栏槽位编号（0-8）。

## 玩家权限等级是否足够（`fancymenu_loading_requirement_has_player_permission_level`）

**用途：**检查玩家在当前世界或服务器中是否至少拥有指定的权限/OP 等级。

**值：**必填——权限等级数字（0-4，其中 4 为服务器管理员）。

## 攻击蓄力是否不足（`is_attack_strength_weakened`）

**用途：**检查玩家的攻击蓄力当前是否不足（尚未完全蓄力）。

**值：**不需要

## 现实时间日期是否匹配（`fancymenu_visibility_requirement_is_realtime_day`）

**用途：**检查当前现实世界日期中的日是否与指定值匹配。

**值：**必填——日期中的日（1-31）。可以使用逗号分隔来提供多个值。

## 现实时间小时是否匹配（`fancymenu_visibility_requirement_is_realtime_hour`）

**用途：**检查当前现实世界时间中的小时是否与指定值匹配。

**值：**必填——24 小时制的小时（0-23）。可以使用逗号分隔来提供多个值。

## 现实时间分钟是否匹配（`fancymenu_visibility_requirement_is_realtime_minute`）

**用途：**检查当前现实世界时间中的分钟是否与指定值匹配。

**值：**必填——分钟（0-59）。可以使用逗号分隔来提供多个值。

## 现实时间月份是否匹配（`fancymenu_visibility_requirement_is_realtime_month`）

**用途：**检查当前现实世界月份是否与指定值匹配。

**值：**必填——月份编号（1-12，其中 1 为一月）。可以使用逗号分隔来提供多个值。

## 现实时间秒数是否匹配（`fancymenu_visibility_requirement_is_realtime_second`）

**用途：**检查当前现实世界时间中的秒是否与指定值匹配。

**值：**必填——秒（0-59）。可以使用逗号分隔来提供多个值。

## 现实时间星期几是否匹配（`fancymenu_visibility_requirement_is_realtime_week_day`）

**用途：**检查当前现实世界星期几是否与指定值匹配。

**值：**必填——星期几的数字（1-7，其中 1 为星期日）。可以使用逗号分隔来提供多个值。

## 现实时间年份是否匹配（`fancymenu_visibility_requirement_is_realtime_year`）

**用途：**检查当前现实世界年份是否与指定值匹配。

**值：**必填——完整年份（例如 "2023"）。可以使用逗号分隔来提供多个值。

## 文件/文件夹是否存在（`fancymenu_loading_requirement_file_exists`）

**用途：**检查文件或目录是否存在。

**值：**必填——相对于当前游戏目录的路径，或以 `.minecraft/` 开头的传统 Minecraft 目录路径。文件和目录都算作存在。

## 操作系统是否为 Linux（`fancymenu_loading_requirement_is_os_linux`）

**用途：**检查当前平台是否既不是 Windows 也不是 macOS。这通常对应 Linux 环境。

**值：**不需要

## 操作系统是否为 macOS（`fancymenu_loading_requirement_is_os_macos`）

**用途：**检查操作系统是否为 macOS。

**值：**不需要

## 操作系统是否为 Windows（`fancymenu_loading_requirement_is_os_windows`）

**用途：**检查操作系统是否为 Windows。

**值：**不需要

## 是否有可用的互联网连接（`is_internet_connection_available`）

**用途：**检查是否有活动的互联网连接可用。

**值：**不需要

## 游戏语言是否匹配（`fancymenu_loading_requirement_is_language`）

**用途：**检查当前游戏语言是否与指定值匹配。

**值：**必填——语言代码（例如英语使用 `en_us`）。

## 模组是否已加载（`fancymenu_loading_requirement_is_mod_loaded`）

**用途：**检查指定模组是否已加载。

**值：**必填——模组 ID（例如 `fancymenu`、`jei`）。也可以使用 `optifine` 检查 OptiFine。支持使用逗号分隔的多个模组 ID；列出的所有模组都必须已加载。

## Rinku 是否已加载（`is_rinku_loaded`）

**用途：**检查是否已安装并初始化 [Rinku](https://modrinth.com/mod/rinku)。[Rinku](https://modrinth.com/mod/rinku) 是使用[浏览器元素](./elements#browser)和[已弃用的基于 Rinku 的视频类型](./video#requirements)所必需的；[原生视频功能](./video)使用 Watermedia。

**值：**不需要

## 是否为数字（`fancymenu_visibility_requirement_is_number`）

**用途：**使用不同的比较模式执行高级数字比较。

**值：**必填——复杂格式：`["mode":"comparison_mode","number":"value1","compare_with":"value2"]$`，其中 `comparison_mode` 可以是 `equals`、`bigger-than`、`smaller-than`、`bigger-than-or-equals` 或 `smaller-than-or-equals`。

## 是否为文本（`fancymenu_visibility_requirement_is_text`）

**用途：**使用不同的比较模式执行高级文本比较。

**值：**必填——复杂格式：`["mode":"comparison_mode","text":"text1","compare_with":"text2"]$`，其中 `comparison_mode` 可以是 `equals`、`contains`、`starts-with` 或 `ends-with`。

## 服务器 IP 是否匹配（`fancymenu_visibility_requirement_is_server_ip`）

**用途：**检查当前服务器 IP 是否与指定值匹配。

**值：**必填——服务器 IP 地址（可带或不带端口）。

## 服务器是否在线（`fancymenu_loading_requirement_is_server_online`）

**用途：**检查指定服务器是否在线且可访问。

**值：**必填——服务器 IP 地址（可带或不带端口）。

## 资源包是否启用（`is_resource_pack_enabled`）

**用途：**检查指定资源包当前是否已选中/处于活动状态。

**值：**必填——资源包标题或资源包 ID（例如 `Programmer Art` 或该资源包的 ID）。

## 变量值是否匹配（FM 变量）（`fancymenu_visibility_requirement_is_variable_value`）

**用途：**检查 FancyMenu 变量是否具有指定值。

**值：**必填——格式为“变量名:预期值”。

## 每个会话仅一次（`once_per_session`）

**用途：**每个配置实例在每个游戏会话中只返回一次 true。不同实例会独立跟踪。

**值：**不需要
