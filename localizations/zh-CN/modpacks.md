---
title: 整合包
description: 如何将布局包含到整合包中。
---
# 整合包中的 FancyMenu

将你的 FancyMenu 设置包含到整合包中非常简单，只需要几个步骤。

> [!CAUTION]
> FancyMenu 设置可以执行操作。请只从你信任的来源导入它们。

> 此页面 **仅** 适用于完全使用 **FancyMenu v3+** 制作的 FancyMenu 设置，因此如果你使用的是旧版设置（在 v2 中制作并转换到 v3），某些步骤可能会有所不同。
{.is-warning}

# 将 FancyMenu 设置包含到你的整合包中

你需要做的主要事情，就是复制 FancyMenu 用来保存所有设计的一个特殊文件夹。

## 你需要找到什么

1. **你的“Minecraft 实例”文件夹：** 这是你电脑上存放某个特定 Minecraft 配置全部文件的主文件夹（例如你设计菜单所使用的那个）。像 CurseForge 和 Modrinth 这样的启动器会把它们称为“实例”或“配置文件”。
2. **`config` 文件夹：** 在你的 Minecraft 实例文件夹中，通常会有一个名为 `config` 的文件夹。许多模组会把设置存放在这里。
3. **`fancymenu` 文件夹：** 在那个 `config` 文件夹中，FancyMenu 会创建一个名为 `fancymenu` 的文件夹。这就是我们需要的“黄金文件夹”！

## 如何找到实例的保存位置

### 如果你使用 CurseForge App

1. 打开 CurseForge。
2. 在列表中找到你的 Minecraft 配置文件/实例并打开它。
3. 点击三个点。
4. 选择“Open Folder（打开文件夹）”。这将打开该 Minecraft 实例的主文件夹。

<img width="630" alt="Screenshot_1" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/curseforge_launcher_instance.png">

### 如果你使用 Modrinth App

1. 打开 Modrinth App。
2. 在列表中找到你的 Minecraft 配置文件/实例并打开它。
3. 点击三个点。
4. 选择“Open Folder（打开文件夹）”。这将打开该 Minecraft 实例的主文件夹。

<img width="630" alt="Screenshot_1" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/modrinth_launcher_instance.png">

### 适用于其他启动器

请为你所使用的 Minecraft 配置查找类似的“Open Folder（打开文件夹）”、“Open Instance Folder（打开实例文件夹）”或“View Files（查看文件）”选项。

## 复制 FancyMenu 设置

1. 进入你要复制设置到的 **整合包** 实例的 `config` 文件夹。
2. 如果其中已经有 `fancymenu` 文件夹，请将其 **删除**。
3. 打开 **源** 实例的 `config` 文件夹（也就是你想要使用该设置的来源实例）。
4. 将源实例 `config` 文件夹中的 `fancymenu` 文件夹复制到整合包实例的 `config` 文件夹中。
5. 完成。就是这样。现在重启你的整合包实例，你应该就能看到该设置被加载了。

> 请注意，使用 FancyMenu v2 制作的旧版设置（即使已转换到 v3）允许你将布局资源存放在 FancyMenu 的 `<game-directory>/config/fancymenu/assets/` 文件夹之外，因此在这种情况下，你还需要确保将所有资源一并包含到整合包中。
{.is-danger}

# 禁用菜单栏和快捷键

你肯定不希望在整合包里一直显示 FancyMenu 的菜单栏，所以你应该把它禁用。但由于玩家仍然可以通过快捷键再次把它显示出来，我们来做一些更“激进”的操作。

进入 `<game-directory>/config/fancymenu/options.txt`，并用文本编辑器打开该文件。

然后将 `modpack_mode` 设置为 `true` 并保存文件。
这将完全禁用所有覆盖层和快捷键。

如果你想再次编辑你的布局，只需将该配置选项改回 `false`。

# 禁用欢迎界面

大多数情况下这一步不需要，但如果你还没有关闭欢迎界面（也就是提示你阅读文档的那个界面），请确保在 `<game-directory>/config/fancymenu/options.txt` 中将 `show_welcome_screen` 设置为 `false`。

这个界面只会显示一次，并且在点击 **Open Documentation（打开文档）** 按钮时会自动禁用，所以同样地，通常不需要手动这样做。

<br>
<img width="630" alt="Screenshot_1" src="https://github.com/user-attachments/assets/4383b39f-f55a-4eb8-8142-34a425474bb3">
