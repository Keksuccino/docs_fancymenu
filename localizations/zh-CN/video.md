---
title: 视频（MP4）
description: 了解在 FancyMenu 中使用视频时需要注意的事项。
sourceBlobSha: bd34c5c21a6c08d6b66a7b2acdaf9bd12739732f
---
# 视频

FancyMenu 支持将 MP4 视频用作[元素](/elements#video)、[菜单背景](/menu-backgrounds#video)和[游戏开场](/game-intro)内容。

原生的[**视频**元素](/elements#video)和**视频**菜单背景使用 Watermedia V3。旧版 **Video [Rinku]** 类型已弃用，仅应保留在仍需要它们的布局中。

以下[动作](/action-scripts)还可用于控制视频背景和元素：

- [**设置视频元素音量**](/action-scripts#set-video-element-volume)可设置视频元素的音量。
- [**设置视频元素播放时间**](/action-scripts#set-video-element-play-time)可将视频元素定位到指定的毫秒时间点。
- [**切换视频元素暂停状态**](/action-scripts#toggle-video-element-paused-state)可切换视频元素的暂停状态。
- [**设置视频背景音量**](/action-scripts#set-video-background-volume)可设置视频菜单背景的音量。
- [**设置视频背景播放时间**](/action-scripts#set-video-background-play-time)可将视频菜单背景定位到指定的毫秒时间点。
- [**切换视频背景暂停状态**](/action-scripts#toggle-video-background-paused-state)可切换视频菜单背景的暂停状态。

以下[占位符](/placeholders)可用于获取视频背景和元素的信息：

- [**视频元素音量**](/placeholders#video-element-volume)返回视频元素的音量。
- [**视频元素时长**](/placeholders#video-element-duration)返回视频元素的时长。
- [**视频元素播放时间**](/placeholders#video-element-play-time)返回视频元素的当前播放进度。
- [**视频元素暂停状态**](/placeholders#video-element-paused-state)返回视频元素是否处于暂停状态。
- [**视频背景音量**](/placeholders#video-background-volume)返回视频菜单背景的音量。
- [**视频背景时长**](/placeholders#video-background-duration)返回视频菜单背景的时长。
- [**视频背景播放时间**](/placeholders#video-background-play-time)返回视频菜单背景的当前播放进度。
- [**视频背景暂停状态**](/placeholders#video-background-paused-state)返回视频菜单背景是否处于暂停状态。

时长和播放时间占位符默认返回 `MM:SS` 格式。如果需要毫秒时间戳，请将 `output_as_timestamp` 设为 `true`。播放时间占位符仍可使用 `show_percentage` 来显示 0–100 的进度值。

音量和暂停状态的值是与标识符关联的控制器元数据。时长和播放时间的值则要求对应的视频元素或背景已在当前屏幕上激活并准备就绪。

[**视频播放状态变化**监听器](/listeners#video-playback-status-changed)可对 `PLAYING`、`PAUSED`、`STOPPED` 和 `FINISHED` 状态变化作出响应。

## 要求

要使用新式原生视频元素和菜单背景类型，必须安装：

- **Watermedia V3**
- **Watermedia Binaries V3**

这些是可选依赖，因此如果需要视频支持，必须手动将它们添加到实例中。

原生视频播放还需要 OpenGL 渲染器。Minecraft 使用 Vulkan 时，Watermedia 无法播放视频；请切换到 OpenGL，以使用视频元素、视频菜单背景和[视频游戏开场](/game-intro)。

已弃用的 **Video [Rinku]** 类型仍使用 [Rinku](https://modrinth.com/mod/rinku)。对于新布局，请改用由 Watermedia 提供支持的原生视频类型。

## 加载屏幕中的视频

视频支持在加载屏幕（游戏/资源加载屏幕和世界加载屏幕）中**不起作用**。

这也意味着，**不要**通过 **Drippy Loading Screen** 将视频添加到游戏加载屏幕，因为大多数情况下都无法正常播放。

请改用简短、简单的[动画](/animations)（APNG 或 GIF）作为加载屏幕内容。

## 故障排除

如果原生视频无法播放，请确认 Watermedia V3 和 Watermedia Binaries V3 与你的 Minecraft/模组加载器版本相匹配，并确认 Minecraft 使用的是 OpenGL，而不是 Vulkan。
