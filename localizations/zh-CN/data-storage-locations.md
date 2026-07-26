---
title: 数据存储位置
description: FancyMenu 存储布局、资源、配置以及持久运行时状态的位置。
---

# 数据存储位置

`<game-directory>` 表示当前启用的 Minecraft 实例文件夹，它可能与 `.minecraft` 不同。

目录和文件通常只会在相关功能初始化或被使用后创建。手动编辑生成的状态文件前请关闭 Minecraft，迁移或重置数据时请务必保留备份。

# 布局、资源与配置

有些条目是作者编写的配置或资源；另一些则是 FancyMenu 在运行时更新的状态。

| 系统 / 功能 | 文件或目录 |
| --- | --- |
| 可自定义界面 | `<game-directory>/config/fancymenu/customizablemenus.txt` |
| [自定义 GUI](./custom-guis) 和界面覆盖规则 | `<game-directory>/config/fancymenu/custom_gui_screens.txt` |
| 布局 | `<game-directory>/config/fancymenu/customization/` |
| [本地资源](./resources#local-resources) | `<game-directory>/config/fancymenu/assets/` |
| [自定义本地化文件](./localization#fancymenu-custom-localization-files) | `<game-directory>/config/fancymenu/custom_locals/` |
| [全景图](./panoramas) | `<game-directory>/config/fancymenu/panoramas/` |
| [幻灯片](./slideshows) | `<game-directory>/config/fancymenu/slideshows/` |
| [FancyMenu 变量](./variables) | `<game-directory>/config/fancymenu/user_variables.db` |
| [视频元素](./elements#video) 控制器元数据 | `<game-directory>/config/fancymenu/video_element_controller_metas.json` |
| [音频元素](./elements#audio) 控制器元数据 | `<game-directory>/config/fancymenu/audio_element_controller_metas.json` |
| [FM Data](./fm-data) 服务器监听器 | `<game-directory>/config/fancymenu/fmdata_server_listeners.json` |
| [FM Data](./fm-data) 欢迎数据 | `<game-directory>/config/fancymenu/fmdata_welcome_data.json` |
| [监听器](./listeners) 实例和动作脚本 | `<game-directory>/config/fancymenu/listener_instances.txt` |
| [调度器](./schedulers) | `<game-directory>/config/fancymenu/scheduler_instances.txt` |

`customizablemenus.txt` 由 **当前界面自定义** 开关管理，并存储具体的界面类标识符。不要添加 [通用布局](./universal-layouts) 标识符；FancyMenu 在加载该文件时会忽略它们。

在专用服务器上，这两个 FM Data 文件相对于该服务器的游戏根目录。其他由客户端拥有的配置和资源则属于每个玩家各自的实例。

# 持久运行时状态

FancyMenu 会在 `config/fancymenu/` 之外保留额外生成的、按实例区分的状态。只有在你想保留相关用户/运行时状态时，才应将这些路径纳入备份；它们不是布局定义，也不是源资源。

| 系统 / 功能 | 文件或目录 |
| --- | --- |
| 非变量的 [复选框](./elements#checkbox) 状态 | `<game-directory>/checkbox_states.json` |
| [拖拽器](./dragger) 元素位置/元数据 | `<game-directory>/fancymenu_data/dragger_metas.json` |
| 上次世界状态 | `<game-directory>/fancymenu_data/last_world.fmdata` |
| [无缝世界加载](./seamless-world-loading) 状态 | `<game-directory>/fancymenu_data/seamless_world_loading/` |
| Buddy 宠物与升级存档 | `<game-directory>/fancymenu_data/buddy/` |
| 布局编辑器小部件位置和可见性 | `<game-directory>/config/fancymenu/layout_editor/widgets/` |
| 默认 GUI 缩放初始化标记 | `<game-directory>/fancymenu_data/default_scale_set.fm` |

Buddy 会将宠物状态以及升级/成就状态分别保存在其目录中的两个单独 JSON 文件里。每个 Buddy 覆盖层实例都会使用自己的一对文件。

布局编辑器小部件文件会存储每个小部件的位置、大小、可见性、展开状态以及吸附边。删除 `default_scale_set.fm` 会使 FancyMenu 在下次启动时将已配置的默认 GUI 缩放视为尚未应用。
