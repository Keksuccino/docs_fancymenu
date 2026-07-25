---
title: 整合包
description: 如何将布局包含到整合包中。
---
# 整合包中的 FancyMenu

将你的 FancyMenu 设置包含到整合包里非常简单，只需要几个步骤。

> [!CAUTION]
> FancyMenu 设置可能会执行操作。请只从你信任的来源导入它们。

> [!WARNING]
> 本页 **仅** 适用于完全使用 **FancyMenu v3+** 创建的 FancyMenu 设置，因此如果你使用的是旧版设置（在 v2 中创建并转换到 v3），某些步骤可能会有所不同。

# 将 FancyMenu 设置包含到你的整合包中

你需要做的主要事情，就是复制 FancyMenu 用来保存所有设计的一个特殊文件夹。

## 你需要找到的内容

1. **你的“Minecraft 实例”文件夹：** 这是你电脑上存放某个特定 Minecraft 安装（例如你设计菜单所用的那个安装）所有文件的主文件夹。CurseForge 和 Modrinth 之类的启动器会把它们称为“实例”或“配置文件”。
2. **`config` 文件夹：** 在你的 Minecraft 实例文件夹中，通常会有一个名为 `config` 的文件夹。许多模组会把它们的设置保存在这里。
3. **`fancymenu` 文件夹：** 在那个 `config` 文件夹里，FancyMenu 会创建自己的文件夹，叫做 `fancymenu`。这就是我们要找的关键文件夹！

## 如何找到实例保存位置

### 如果你使用 CurseForge App

1. 打开 CurseForge。
2. 在列表中找到你的 Minecraft 配置文件/实例并打开它。
3. 点击三个点。
4. 选择“Open Folder”。这会打开该 Minecraft 实例的主文件夹。

<img width="630" alt="Screenshot_1" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/curseforge_launcher_instance.png">

### 如果你使用 Modrinth App

1. 打开 Modrinth App。
2. 在列表中找到你的 Minecraft 配置文件/实例并打开它。
3. 点击三个点。
4. 选择“Open Folder”。这会打开该 Minecraft 实例的主文件夹。

<img width="630" alt="Screenshot_1" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/modrinth_launcher_instance.png">

### 其他启动器

请为你的具体 Minecraft 安装查找类似的“Open Folder”、“Open Instance Folder”或“View Files”选项。

## 复制 FancyMenu 设置

1. 进入你的 **MODPACK** 实例的 `config` 文件夹（也就是你想把设置复制到的那个实例）。
2. 如果里面已经有一个 `fancymenu` 文件夹，请将其删除。
3. 打开 **源** 实例的 `config` 文件夹（也就是你想从中使用设置的那个实例）。
4. 将 **源** 实例 `config` 文件夹中的 `fancymenu` 文件夹复制到你的 **MODPACK** 实例的 `config` 文件夹中。
5. 完成。就是这样。现在重启你的整合包实例，你应该就能看到设置被加载了。

> [!CAUTION]
> 请记住，使用 FancyMenu v2 制作的旧版设置（即使已转换为 v3）允许你将布局资源存放在 FancyMenu 的 `<game-directory>/config/fancymenu/assets/` 文件夹之外，因此在这种情况下，你还需要确保把所有资源一起包含进整合包中。

# 禁用菜单栏和快捷键

你肯定不想让 FancyMenu 的菜单栏在你的整合包里一直可见，所以你应该把它禁用。但由于别人仍然可以按快捷键把它再次显示出来，我们来做点稍微更 *激进* 的操作。

进入 `<game-directory>/config/fancymenu/options.txt` 并用文本编辑器打开这个文件。

然后将 `modpack_mode` 设置为 `true` 并保存文件。
这会完全禁用所有覆盖层和快捷键。

如果你想再次编辑你的布局，只需把这个配置项改回 `false`。

# 禁用欢迎界面

在大多数情况下这并不需要，但如果你还没有关闭欢迎界面（也就是提示你阅读文档的那个界面），请确保在 `<game-directory>/config/fancymenu/options.txt` 中将 `show_welcome_screen` 设置为 `false`。

这个界面只会显示一次，并且在点击 **Open Documentation** 按钮后会自动关闭，所以同样地，通常不需要手动这么做。

<br>
<img width="630" alt="Screenshot_1" src="https://github.com/user-attachments/assets/4383b39f-f55a-4eb8-8142-34a425474bb3">
