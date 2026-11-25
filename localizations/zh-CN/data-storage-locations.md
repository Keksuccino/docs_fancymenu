---
title: 数据存储位置
description: 了解 FancyMenu 将布局、资源、设置及其他内容保存在哪里，以及哪些文件属于配置档案。
sourceBlobSha: 30dd81ed90e08184e3063892870e3325d7d7c5cb
---

# 数据存储位置

FancyMenu 会将所有内容保存在游戏目录中的两个文件夹内。这里指的是启动器的实例文件夹，它可能与 `.minecraft` 不同。

- `config/fancymenu/` 存放你的配置：布局、资源、变量、设置等。它属于当前加载的[配置档案](/profiles)，因此整合包会包含此文件夹。
- `fancymenu_data/` 存放此游戏实例的数据，例如 Dragger 的位置和下载内容。所有配置档案共用此文件夹。

**菜单栏 -> 工具 -> 打开 FancyMenu 目录**会打开 `config/fancymenu/`。

大多数文件和文件夹只有在你使用相应功能后才会出现。修改或删除其中的文件前，请先关闭游戏。

> [!TIP]
> 若要让多个实例共用这些文件夹，可以将它们移到其他位置，并在原位置创建符号链接（Windows 上为目录联接）。

# 你的配置

`<game-directory>/config/fancymenu/` 中的所有内容都属于当前加载的[配置档案](/profiles)。

| 内容 | 位置 |
| --- | --- |
| 布局（`.txt` 文件，也可能位于子文件夹中） | `customization/` |
| [本地资源](/resources#local-resources)，例如图像和声音 | `assets/` |
| FancyMenu 的设置 | `options.txt` |
| 已启用**当前屏幕自定义**的屏幕 | `customizablemenus.txt` |
| [自定义 GUI](/custom-guis)及其替换的屏幕 | `custom_gui_screens.txt` |
| [变量](/variables) | `user_variables.db` |
| [监听器](/listeners) | `listener_instances.txt` |
| [调度器](/schedulers) | `scheduler_instances.txt` |
| [全景图](/panoramas) | `panoramas/` |
| [幻灯片](/slideshows) | `slideshows/` |
| [自定义本地化](/localization#fancymenu-custom-localization-files) | `custom_locals/` |
| FancyMenu 自身界面的主题（**菜单栏 -> 自定义 -> 设置 -> FancyMenu 界面 -> 界面主题**） | `ui_themes/` |
| 未使用变量的[复选框元素](/elements#checkbox)状态 | `checkbox_states.json` |
| 操作设置的[视频元素](/video)音量和暂停状态 | `video_element_controller_metas.json` |
| 操作设置的[音频元素](/elements#audio)音量 | `audio_element_controller_metas.json` |
| 操作设置的[元素动画器](/element-animator)开关状态 | `animation_controller_states.json` |
| 已启用**公开当前屏幕的滚动区域内容**的屏幕（参见[自定义可滚动屏幕](/customizing-scrollable-screens)） | `normalized_scroll_screens.json` |
| [FM Data](/fm-data)服务器监听器 | `fmdata_server_listeners.json` |
| [FM Data](/fm-data)欢迎数据 | `fmdata_welcome_data.json` |
| 布局编辑器各组件的位置、大小和可见性 | `layout_editor/widgets/` |
| 当前加载配置档案的名称、图标和详细信息 | `profile.json` 和 `profile_icon.png` |
| 其他所有[配置档案](/profiles#where-profiles-are-stored) | `profiles/` |
| FancyMenu 已执行过的旧文件更新记录 | `legacy_checklist.txt` |

`customizablemenus.txt` 使用屏幕的 Java 类名列出屏幕。像 `title_screen` 这样的简短[屏幕标识符](/screen-identifiers)不会列在其中。

在专用服务器上，FancyMenu 只会使用服务器 `config/fancymenu/` 文件夹中的两个 [FM Data](/fm-data) 文件。

# 实例数据

`<game-directory>/fancymenu_data/` 中的所有内容都不属于配置档案，因此切换配置档案时会保留。

| 内容 | 位置 |
| --- | --- |
| [Dragger 元素](/dragger)的位置 | `dragger_metas.json` |
| 上次游玩的世界或上次加入的服务器，供**进入/加入上次的世界/服务器**操作和**上次的世界或服务器**占位符使用 | `last_world.fmdata` |
| [无缝世界加载](/seamless-world-loading)的屏幕截图 | `seamless_world_loading/` |
| [Buddy](/decoration-overlays#buddy)的存档；每个 Buddy 覆盖层对应两个文件 | `buddy/` |
| [AI 导出](/export-for-ai)的文件 | `ai_exports/` |
| 操作选择器中收藏的操作 | `action_favorites.json` |
| 文件选择器中音频和视频预览的音量 | `browser_audio_settings.json` 和 `browser_video_settings.json` |
| 暂停时[视频背景](/video)显示的画面 | `video_thumbnails/` |
| FancyMenu 为 [AFMA 创建器](/animations#fma-and-afma)下载的 FFmpeg | `ffmpeg_cache/` |
| 记录 FancyMenu 已设置过[**默认 GUI 缩放**](/global-customizations)的文件 | `default_scale_set.fm` |
| 每次启动游戏时都会删除的临时文件 | `fancymenu_temp/` |

- FancyMenu 只会设置一次**默认 GUI 缩放**。删除 `default_scale_set.fm`，即可让它在下次启动时重新设置缩放比例。
- 无缝世界加载的屏幕截图会显示当时世界中的屏幕内容。如果不想保留这些截图，请在游戏关闭时将其删除。

# 旧版本的文件

较旧版本的 FancyMenu 会将部分文件保存在其他位置。FancyMenu 会在下次启动游戏时迁移这些文件：

- 将游戏目录中的 `checkbox_states.json` 和 `normalized_scroll_screens.json` 移至 `config/fancymenu/`。
- 将 `config/fancymenu/` 中的 `dragger_metas.json` 移至 `fancymenu_data/`。
