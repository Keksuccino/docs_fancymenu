---
title: 标题界面符号
description: 如何隐藏/移除标题界面里那个小菱形或绿宝石（绿色或蓝色）的符号/图标。
---
# 标题界面中的绿宝石/菱形图标

如果你一直想隐藏那个总是出现在标题界面里的小图标——看起来像一个小菱形或绿宝石（绿色或蓝色的小图标）——这通常是 Mod Menu（Fabric 模组）或 Forge（内置模组加载器功能）的模组更新通知。

在某些情况下，它也可能是原版 Minecraft 的 Realms 按钮的一部分（用于显示通知）。

# 隐藏 Mod Menu 图标

要隐藏 Mod Menu 的符号，你需要在它的设置中禁用“更新指示器”。

点击 **Mods** 按钮 -> 将鼠标悬停在模组列表中的 Mod Menu 图标上 -> 点击它 -> 将“Update Indicator”设为“Hidden”。

# 隐藏 Forge 图标

Forge 使用内置的版本检查器，在模组过期时显示那个绿宝石图标。你可以将其关闭：

1. 打开你的 `/config/fml.toml` 文件。
2. 找到 `versionCheck` 设置。
3. 将其设为 `false`：`versionCheck = false`
4. 保存并重启 Minecraft。

这会完全禁用版本检查，也会在启动时隐藏绿宝石符号。

另一种隐藏该图标的方法是直接通过 FancyMenu 隐藏整个 Mods 按钮。隐藏该按钮也会一并隐藏这个符号。

# 隐藏 NeoForge 图标

对于 NeoForge，做法和经典 Forge 完全一样。

1. 打开你的 `/config/fml.toml` 文件。
2. 找到 `versionCheck` 设置。
3. 将其设为 `false`：`versionCheck = false`
4. 保存并重启 Minecraft。

# 隐藏原版 Realms 图标

如果它既不是 Mod Menu，也不是 Forge 的符号，那它很可能是 Minecraft 自己的 Realms 通知图标。这些图标大致显示在 Realms 按钮所在的位置，可以通过 FancyMenu 在布局编辑器中隐藏。你需要创建一个“针对当前界面”的布局（这里指标题界面），然后你就会在编辑器中看到 Realms 图标作为一个独立元素。要隐藏它，只需**右键**它，然后点击**Delete**。

Realms 图标可能是报纸图标、菱形符号等，也可能是带通知数量的红色圆圈。
