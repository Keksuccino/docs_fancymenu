---
title: 游戏介绍
description: 在游戏首次显示标题屏幕之前播放动画内容。
---
# 游戏介绍

游戏介绍会在标题屏幕首次出现之前播放一段动画图片或视频。

# 设置

通过 **自定义 -> 全局自定义** 打开 [**全局自定义**](./global-customizations)，然后配置以下设置：

| 设置 | 行为 |
|---|---|
| 设置游戏介绍 | 选择本地、网页或 Minecraft 资源的动画图片或视频 |
| 游戏介绍跳过 | 允许按任意键或鼠标单击跳过介绍 |
| 游戏介绍淡出 | 将介绍淡出到目标屏幕 |
| 自定义跳过文本 | 用纯文本或本地化键替换默认的跳过提示 |
| 游戏介绍音量 | 将基础音量设置为 `0.0` 到 `1.0` |
| 游戏介绍声音通道 | 选择 Minecraft 的声音类别 |
| 重新触发游戏介绍 | 再次播放已配置的介绍以便测试 |

视频介绍需要 **Watermedia V3**、**Watermedia Binaries V3** 以及 OpenGL 渲染器。使用 Vulkan 时无法进行 Watermedia 视频播放。当无法播放时，FancyMenu 会在介绍屏幕上显示说明。请参阅 [视频](./video#requirements)。

<br>
<img width="700" alt="Screenshot_1" src="https://gist.github.com/assets/35544624/71cec75b-33f1-4a21-9f18-d0adc7ceebb6">
