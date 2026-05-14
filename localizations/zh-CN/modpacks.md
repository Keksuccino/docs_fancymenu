---
title: 整合包
description: 如何在整合包中包含布局。
---

# 整合包中的 FancyMenu

把你的 FancyMenu 设置包含到整合包中非常简单，只需要几个步骤。

> 本页**仅**适用于完全使用 **FancyMenu v3+** 制作的 FancyMenu 设置。如果你使用的是旧版设置（在 v2 中创建并转换到 v3），某些步骤可能会有所不同。
{.is-warning}

# 将 FancyMenu 设置包含到你的整合包中

你需要做的主要事情，就是复制 FancyMenu 用来保存你所有设计的一个特殊文件夹。

## 你需要找到的内容

1. **你的“Minecraft 实例”文件夹：** 这是你电脑上存放某个 Minecraft 配置全部文件的主文件夹（例如你制作菜单时使用的那个配置）。像 CurseForge 和 Modrinth 这类启动器会把它们称为“实例”或“配置文件”。
2. **`config` 文件夹：** 在你的 Minecraft 实例文件夹中，通常会有一个名为 `config` 的文件夹。许多模组会把设置存放在这里。
3. **`fancymenu` 文件夹：** 在那个 `config` 文件夹里，FancyMenu 会创建一个名为 `fancymenu` 的文件夹。这就是我们要找的宝藏文件夹！

## 如何找到实例的保存位置

### 如果你使用 CurseForge App

1. 打开 CurseForge。
2. 在列表中找到你的 Minecraft 配置/实例并打开它。
3. 点击三点菜单。
4. 选择“Open Folder”。这会打开该 Minecraft 实例的主文件夹。

<img width="630" alt="Screenshot_1" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/curseforge_launcher_instance.png">

### 如果你使用 Modrinth App

1. 打开 Modrinth App。
2. 在列表中找到你的 Minecraft 配置/实例并打开它。
3. 点击三点菜单。
4. 选择“Open Folder”。这会打开该 Minecraft 实例的主文件夹。

<img width="630" alt="Screenshot_1" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/modrinth_launcher_instance.png">

### 其他启动器

请为你使用的 Minecraft 配置查找类似的“Open Folder”、“Open Instance Folder”或“View Files”选项。

## 复制 FancyMenu 设置

1. 进入你的 **MODPACK 实例** 的 `config` 文件夹（也就是你想把设置复制到的那个实例）。
2. 如果里面已经有一个 `fancymenu` 文件夹，请将其**删除**。
3. 打开 **源实例** 的 `config` 文件夹（也就是你想从中使用这套设置的那个实例）。
4. 将源实例 `config` 文件夹中的 `fancymenu` 文件夹复制到你的 MODPACK 实例的 `config` 文件夹中。
5. 完成。就是这么简单。现在重启你的整合包实例，你应该就能看到这套设置加载了。

> 请注意，旧版 FancyMenu v2 中制作的旧式设置（即使已转换到 v3）允许你将布局资源存放在 FancyMenu 的 `/config/fancymenu/assets/` 文件夹之外，因此在这种情况下，你还需要确保将所有资源一并包含到整合包中。
{.is-danger}

# 禁用菜单栏和快捷键

你当然不希望在整合包中一直显示 FancyMenu 的菜单栏，所以你应该将它禁用。不过由于用户仍然可以按快捷键把它重新显示出来，我们来做得更“强硬”一点。

进入 `/config/fancymenu/options.txt` 并用文本编辑器打开该文件。

然后将 `modpack_mode` 设为 `true` 并保存文件。
这样会完全禁用所有覆盖层和快捷键。

如果你之后还想再次编辑布局，只需将这个配置项改回 `false` 即可。

# 禁用欢迎界面

在大多数情况下这应该不需要，但如果你还没有关闭欢迎界面（也就是提示你阅读文档的那个界面），请确保在 `/config/fancymenu/options.txt` 中将 `show_welcome_screen` 设为 `false`。

这个界面只会显示一次，并且在点击 **Open Documentation** 按钮后会自动禁用，所以同样地，通常并不需要手动这样做。

<br>
<img width="630" alt="Screenshot_1" src="https://github.com/user-attachments/assets/4383b39f-f55a-4eb8-8142-34a425474bb3">
