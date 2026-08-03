---
title: 视频（MP4）
description: 关于在 FancyMenu 中使用视频需要了解的内容。
---
# 视频

FancyMenu 支持将 MP4 视频作为 [元素](./elements#video)、[菜单背景](./menu-backgrounds) 和 [游戏开场](./game-intro) 内容播放。

原生的 [**Video** 元素](./elements#video) 和 **Video** 菜单背景使用 Watermedia V3。旧的 **Video [Rinku]** 类型已被弃用，只应保留在仍然需要它们的布局中。

此外，还有以下用于控制视频背景和元素的 **动作**：

- [**设置视频元素音量**](./action-scripts#set-video-element-volume-set_video_element_volume) 用于设置 Video 元素的音量。
- [**设置视频元素播放时间**](./action-scripts#set-video-element-play-time-set_video_element_play_time) 用于将 Video 元素跳转到某个毫秒时间戳。
- [**切换视频元素暂停状态**](./action-scripts#toggle-video-element-paused-state-toggle_video_element_pause_state) 用于切换 Video 元素的暂停状态。
- [**设置视频背景音量**](./action-scripts#set-video-background-volume-set_video_menu_background_volume) 用于设置 Video 菜单背景的音量。
- [**设置视频背景播放时间**](./action-scripts#set-video-background-play-time-set_video_menu_background_play_time) 用于将 Video 菜单背景跳转到某个毫秒时间戳。
- [**切换视频背景暂停状态**](./action-scripts#toggle-video-background-paused-state-toggle_video_menu_background_pause_state) 用于切换 Video 菜单背景的暂停状态。

以及以下用于获取视频背景和元素信息的 **占位符**：

- [**视频元素音量**](./placeholders#video-element-volume-video_element_vol) 返回 Video 元素的音量。
- [**视频元素时长**](./placeholders#video-element-duration-video_element_duration) 返回 Video 元素的时长。
- [**视频元素播放时间**](./placeholders#video-element-play-time-video_element_playtime) 返回 Video 元素当前的进度。
- [**视频元素暂停状态**](./placeholders#video-element-paused-state-video_element_paused_state) 返回 Video 元素是否已暂停。
- [**视频背景音量**](./placeholders#video-background-volume-video_background_vol) 返回 Video 菜单背景的音量。
- [**视频背景时长**](./placeholders#video-background-duration-video_background_duration) 返回 Video 菜单背景的时长。
- [**视频背景播放时间**](./placeholders#video-background-play-time-video_background_playtime) 返回 Video 菜单背景当前的进度。
- [**视频背景暂停状态**](./placeholders#video-background-paused-state-video_background_paused_state) 返回 Video 菜单背景是否已暂停。

时长和播放时间占位符默认返回 `MM:SS`。当你需要毫秒时间戳时，将 `output_as_timestamp` 设为 `true`。播放时间占位符仍然可以使用 `show_percentage` 来返回 0-100 的进度值。

音量和暂停状态值是与标识符关联的控制器元数据。时长和播放时间值要求匹配的 Video 元素或背景在当前屏幕上处于活动并准备就绪状态。

[**视频播放状态变更** 监听器](./listeners#on-video-playback-status-changed-video_playback_status_changed) 可以响应 `PLAYING`、`PAUSED`、`STOPPED` 和 `FINISHED`。

## 要求

要使用新的原生 Video 元素和菜单背景类型，你需要安装：

- **Watermedia V3**
- **Watermedia Binaries V3**

这些都是可选依赖，因此如果你想要视频支持，必须手动将它们添加到实例中。

原生视频播放还需要 OpenGL 渲染器。当 Minecraft 使用 Vulkan 时，Watermedia 播放不可用；请切换到 OpenGL 才能使用 Video 元素、Video 菜单背景以及 [视频游戏开场](./game-intro)。

已弃用的 **Video [Rinku]** 类型仍然使用 [Rinku](https://modrinth.com/mod/rinku)。对于新布局，请改用由 Watermedia 驱动的原生 Video 类型。

## 加载界面中的视频

视频支持在加载界面中**不起作用**（游戏/资源加载界面和世界加载界面）。

这也意味着你**不应**通过 **Drippy Loading Screen** 将视频添加到游戏加载界面，因为在大多数情况下它不会生效。

请在加载界面中改用简短、简单的 [AFMA/FMA 动画](./fma)。

## 故障排除

如果原生视频无法播放，请确认 Watermedia V3 和 Watermedia Binaries V3 与你的 Minecraft/模组加载器版本匹配，并且 Minecraft 正在使用 OpenGL 而不是 Vulkan。
