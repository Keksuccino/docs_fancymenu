---
title: 模组包
description: 如何在模组包中包含布局。
sourceBlobSha: c19df01d8e726bbff6c9d1d147287ada5d1773eb
---

# 模组包中的 FancyMenu

将 FancyMenu 设置包含在模组包中非常简单，只需几个步骤即可完成。

> [!CAUTION]
> FancyMenu 设置可以执行操作。请只从你信任的来源导入设置。

> [!WARNING]
> 本页面**仅适用于完全使用** **FancyMenu v3+** 创建的 FancyMenu 设置。因此，如果你使用的是旧版设置（在 v2 中创建并转换为 v3），部分步骤可能会有所不同。

# 将设置导入模组包

将设置从创建它的实例迁移到模组包实例，最简单的方法是使用[配置档案](/profiles)：

1. 在包含你设置的实例中，打开**菜单栏 -> 自定义 -> 配置档案**，选择你的设置，并将其[导出](/profiles#exporting)为 `.fmp` 文件。
2. 在模组包实例中，打开配置档案窗口并[导入](/profiles#importing) `.fmp` 文件，例如将文件拖到窗口中。
3. 选择导入的配置档案，然后点击**加载配置档案**。

模组包实例原有的 FancyMenu 设置不会丢失。它会作为独立的配置档案保留，因此你随时可以切换回去。

# 随模组包一起发布设置

已加载的配置档案内容位于 `<game-directory>/config/fancymenu/`，因此它会随模组包的 `config` 文件夹一起发布，就像其他模组的配置文件一样。

此实例的其他配置档案都存储在 `<game-directory>/config/fancymenu/profiles/` 中。导出模组包之前，请删除玩家不应获取的配置档案，或者在导出模组包时排除 `profiles` 文件夹。

> [!CAUTION]
> 请注意，在 FancyMenu v2 中创建的旧版设置（即使已转换为 v3）允许你将布局资源存储在 FancyMenu 的 `<game-directory>/config/fancymenu/assets/` 文件夹之外。配置档案只包含 FancyMenu 的配置文件夹，因此如果遇到这种情况，请确保也将所有资源包含在模组包中。

## 导出前重置复选框

[复选框元素](/elements#checkbox)会在 `config/fancymenu/checkbox_states.json` 中记录其勾选状态。因此，你测试时点击过的复选框，对玩家来说也会处于勾选状态。

若要让玩家从初始状态开始，请关闭游戏，并在导出模组包或配置档案之前删除 `checkbox_states.json`。没有此文件时，所有复选框都会默认为未勾选状态。使用[变量](/variables)的复选框会将状态保存在变量中。

测试期间被操作修改的其他内容也是如此，例如[视频元素](/video)的音量：这些文件的位置请参阅[数据存储位置](/data-storage-locations#your-setup)。

## 如何找到实例文件夹

实例文件夹是电脑上存放某个 Minecraft 配置所有文件的主文件夹。CurseForge 和 Modrinth 等启动器会将其称为“实例”或“配置档案”（不要与 FancyMenu 的配置档案混淆）。

### 如果你使用 CurseForge App

1. 打开 CurseForge。
2. 在列表中找到你的 Minecraft 配置档案/实例并打开。
3. 点击三点按钮。
4. 选择“打开文件夹”。这会打开该 Minecraft 实例的主文件夹。

<img width="630" alt="Screenshot_1" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/curseforge_launcher_instance.png">

### 如果你使用 Modrinth App

1. 打开 Modrinth App。
2. 在列表中找到你的 Minecraft 配置档案/实例并打开。
3. 点击三点按钮。
4. 选择“打开文件夹”。这会打开该 Minecraft 实例的主文件夹。

<img width="630" alt="Screenshot_1" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/modrinth_launcher_instance.png">

### 使用其他启动器时

找到类似“打开文件夹”“打开实例文件夹”或“查看文件”的选项，具体名称取决于你使用的 Minecraft 配置。

# 禁用菜单栏和快捷键

你肯定不希望在模组包中保留 FancyMenu 的菜单栏，因此应该将其禁用。但玩家仍然可以按快捷键重新显示菜单栏，所以我们来采取更*彻底*的做法。

前往 `<game-directory>/config/fancymenu/options.txt`，并使用文本编辑器打开该文件。

将 `modpack_mode` 设置为 `true`，然后保存文件。
这会彻底禁用所有覆盖层和快捷键。

若要再次编辑布局，请将此配置选项改回 `false`。

# 禁用欢迎屏幕

大多数情况下无需进行此操作，但如果你还没有关闭欢迎屏幕（提示你阅读文档的那个屏幕），请确保将 `<game-directory>/config/fancymenu/options.txt` 中的 `show_welcome_screen` 设置为 `false`。

此屏幕只会显示一次，点击**打开文档**按钮后便会自动禁用，因此大多数情况下无需手动进行此操作。

<br>
<img width="630" alt="Screenshot_1" src="https://github.com/user-attachments/assets/4383b39f-f55a-4eb8-8142-34a425474bb3">
