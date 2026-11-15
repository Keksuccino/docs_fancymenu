---
title: 模组包
description: 如何在模组包中包含布局。
sourceBlobSha: deb3c58e9536e0fe085820a2b9e463f5faaa7819
---

# 模组包中的 FancyMenu

将你的 FancyMenu 配置包含到模组包中非常简单，只需几个步骤即可完成。

> [!CAUTION]
> FancyMenu 配置可以运行操作。请仅从你信任的来源导入配置。

> [!WARNING]
> 本页面**仅**适用于完全使用 **FancyMenu v3+** 创建的 FancyMenu 配置。如果你使用的是旧版配置（在 v2 中创建并转换到 v3），部分步骤可能会有所不同。

# 将你的配置导入模组包

将配置从创建它的实例转移到模组包实例中，最简单的方法是使用[配置档案](./profiles)：

1. 在包含你的配置的实例中，打开**菜单栏 -> 自定义 -> 配置档案**，选择你的配置，然后将其[导出](./profiles#exporting)为 `.fmp` 文件。
2. 在你的模组包实例中，打开配置档案窗口，并[导入](./profiles#importing) `.fmp` 文件，例如将文件拖到窗口中。
3. 选择导入的配置档案，然后点击**加载配置档案**。

模组包实例之前使用的 FancyMenu 配置不会丢失。它会作为独立的配置档案保留，因此你随时都可以切换回去。

# 将配置随模组包一起发布

已加载的配置档案就是 `<game-directory>/config/fancymenu/` 中的内容，因此它会与其他模组的配置文件一样，随模组包的 `config` 文件夹一起发布。

实例中的其他配置档案存储在 `<game-directory>/config/fancymenu/profiles/` 中。在导出模组包之前，请删除不应提供给玩家的配置档案，或者不要将 `profiles` 文件夹包含在模组包导出文件中。

> [!CAUTION]
> 请注意，在 FancyMenu v2 中创建的旧版配置（即使已转换到 v3）允许你将布局资源存储在 FancyMenu 的 `<game-directory>/config/fancymenu/assets/` 文件夹之外。配置档案只包含 FancyMenu 的配置文件夹，因此在这种情况下，你还需要确保将所有资源一并包含在模组包中。

## 如何找到实例文件夹

实例文件夹是你电脑上用于存储某个特定 Minecraft 配置的所有文件的主文件夹。CurseForge 和 Modrinth 等启动器将其称为“实例”或“配置文件”（不要与 FancyMenu 的配置档案混淆）。

### 如果你使用 CurseForge 应用

1. 打开 CurseForge。
2. 在列表中找到你的 Minecraft 配置文件/实例并打开它。
3. 点击三个点。
4. 选择“打开文件夹”。这将打开该 Minecraft 实例的主文件夹。

<img width="630" alt="截图_1" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/curseforge_launcher_instance.png">

### 如果你使用 Modrinth 应用

1. 打开 Modrinth 应用。
2. 在列表中找到你的 Minecraft 配置文件/实例并打开它。
3. 点击三个点。
4. 选择“打开文件夹”。这将打开该 Minecraft 实例的主文件夹。

<img width="630" alt="截图_1" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/modrinth_launcher_instance.png">

### 对于其他启动器

请在对应的 Minecraft 配置中查找类似“打开文件夹”、“打开实例文件夹”或“查看文件”的选项。

# 禁用菜单栏和快捷键

你肯定不希望在模组包中继续显示 FancyMenu 的菜单栏，因此应该将其禁用。不过，由于用户仍然可以按下快捷键使菜单栏再次显示，我们来采取更*彻底*的措施。

前往 `<game-directory>/config/fancymenu/options.txt`，并使用文本编辑器打开该文件。

现在将 `modpack_mode` 设置为 `true`，然后保存文件。
这将完全禁用所有覆盖层和快捷键。

若要再次编辑布局，请将此配置选项改回 `false`。

# 禁用欢迎屏幕

在大多数情况下，你不需要执行此操作。但如果你还没有关闭欢迎屏幕（即提示你阅读文档的屏幕），请确保将 `<game-directory>/config/fancymenu/options.txt` 中的 `show_welcome_screen` 设置为 `false`。

该屏幕只会显示一次，并且在点击**打开文档**按钮后会自动禁用，因此在大多数情况下，你无需手动进行设置。

<br>
<img width="630" alt="截图_1" src="https://github.com/user-attachments/assets/4383b39f-f55a-4eb8-8142-34a425474bb3">
