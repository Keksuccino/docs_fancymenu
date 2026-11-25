---
title: 游戏片头
description: 在每次游戏启动时、标题界面显示前播放动画或视频。
sourceBlobSha: 2f40eb874b4aebaf4b32ffa2b8980310d71510b7
---

# 游戏片头

游戏片头会在游戏启动时、Minecraft 加载界面结束后播放动画或视频。播放结束后，画面会淡入标题界面。它专为整合包设计，可用于展示徽标、工作室片头或简短预告片。

<img width="800" alt="Skyhaven 片头：夜色渐渐变为浮空岛上的黎明，徽标逐字出现，随后片头淡入标题界面；标题界面使用同一座岛屿作为背景" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/game_intro_showcase.gif?raw=true">

玩家可以按任意键或单击来跳过片头。游戏片头属于[全局自定义](/global-customizations)，因此不需要布局。

# 设置片头

<img width="800" alt="从菜单栏打开全局自定义和游戏片头，使用 Set Game Intro 选择 skyhaven_intro.apng，使用 Re-Trigger Game Intro 播放，并按 Space 跳过" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/game_intro_setup.gif?raw=true">

1. 将动画或视频放入 `<game-directory>/config/fancymenu/assets/`。
2. 打开 **菜单栏 -> 自定义 -> 全局自定义 -> 游戏片头**。
3. 点击 **设置游戏片头**。将 **来源类型**设为 **本地**，点击 **选择本地资源文件**，选择文件后点击 **确定**。
4. 点击 **重新播放游戏片头**，即可立即预览。

要移除片头，将鼠标移到 **设置游戏片头**上，然后点击 **重置为默认值**。

## 动画和视频

- **动画：**APNG 或 GIF 文件。制作方法请参阅[动画](/animations)。
- **视频：**MP4 文件。需要安装 Watermedia V3 和 Watermedia Binaries V3 模组，详见[视频](/video#requirements)。如果未安装这些模组，视频片头只会显示一条红色提示，其中包含下载链接，持续几秒钟。
- 可使用实例文件和资源包中的文件，但不能使用网页链接。请参阅[资源](/resources)。

片头会铺满整个屏幕并保持原有比例，因此在比例不同的屏幕上会有部分内容被裁切。大多数屏幕的比例为 16:9，所以片头也应使用 16:9 比例，例如 1920x1080。片头中的透明部分会显示为黑色。

> [!TIP]
> 玩家每次启动游戏都会看到片头，因此请尽量保持简短，时长约为 5 到 10 秒。

## 免费示例片头

本页 GIF 中的 Skyhaven 片头可免费使用，既可用于测试，也可用于整合包：

- [skyhaven_intro.apng](https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/skyhaven_intro.apng?raw=true)：片头动画，分辨率为 1280x720，时长 5.4 秒，播放一次。
- [skyhaven_menu.png](https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/skyhaven_menu.png?raw=true)：片头的最后一幕，不含徽标，分辨率为 1280x720。将其设为标题界面布局的[图像背景](/menu-backgrounds#image)，这样片头就会淡入风格相配的菜单，如第一个 GIF 所示。

# 设置

所有设置都位于 **菜单栏 -> 自定义 -> 全局自定义 -> 游戏片头**：

| 设置 | 功能 |
|---|---|
| **设置游戏片头** | 设置要播放的动画或视频。 |
| **游戏片头跳过功能** | 按任意键或单击即可跳过片头，屏幕底部会显示 **按任意键跳过**。跳过时片头会立即结束，不会淡出。关闭此选项后，片头总会播放至结束。 |
| **游戏片头淡出** | 片头结束时淡入标题界面。关闭此选项后，标题界面会立即显示。 |
| **忽略游戏片头循环** | 即使动画设置为循环播放，也会在动画播放一次后结束片头。关闭此选项后，片头会播放动画的所有循环。视频始终只播放一次。 |
| **自定义跳过文本** | 替换 **按任意键跳过**，例如改为 `按任意键开始你的冒险`。如果填写资源包中的本地化键（例如 `skyhaven.intro.skip`），玩家会看到对应语言的文本。 |
| **游戏片头音量** | 设置视频片头的音量，范围为 0% 到 100%。 |
| **游戏片头声音通道** | 设置视频片头使用的声音通道，例如“音乐”。Minecraft 声音设置中该通道的音量和主音量也会同时生效。 |
| **重新播放游戏片头** | 在当前屏幕上方立即播放片头。 |

默认情况下，**游戏片头跳过功能**、**游戏片头淡出**和**忽略游戏片头循环**均处于开启状态。

> [!WARNING]
> 如果同时关闭**游戏片头跳过功能**和**忽略游戏片头循环**，无限循环的动画将永远不会结束，玩家也无法进入标题界面。

# 其他须知

- 每次启动游戏时，片头都会播放一次，并在加载界面后的第一个屏幕出现前播放。通常，这个屏幕就是标题界面。
- 如需更改 Minecraft 在片头之前显示的加载界面，请参阅[加载界面](/loading-screen)。
- 片头来源可以包含[占位符](/resources#placeholders-in-resource-sources)。
- 游戏片头设置会保存在 FancyMenu 的 `options.txt` 中，因此归属于当前加载的[配置档案](/profiles)。包含 `config/fancymenu/` 的整合包会随附片头设置，以及放在 `assets/` 中的片头文件。请参阅[整合包](/modpacks)。
