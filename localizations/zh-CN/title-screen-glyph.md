---
title: 标题屏幕图标
description: 如何隐藏/移除标题屏幕中那个小钻石或绿宝石（绿色或蓝色）图标。
---

# 标题屏幕中的绿宝石/钻石图标

如果你一直想把标题屏幕里反复出现的那个小图标隐藏掉——它看起来像一个小钻石或绿宝石（绿色或蓝色的小图标）——那么它通常是 Mod Menu（Fabric 模组）的更新通知，或者是 Forge（内置模组加载器功能）的更新通知。

在某些情况下，它也可能是原版 Minecraft 的 Realms 按钮的一部分（用于显示通知）。

# 隐藏 Mod Menu 图标

要隐藏 Mod Menu 的这个图标，你需要在它的设置中关闭“更新指示器（update indicator）”。

点击 **Mods** 按钮 -> 将鼠标悬停在模组列表中的 Mod Menu 图标上 -> 点击它 -> 将“Update Indicator”设置为“Hidden”。

# 隐藏 Forge 图标

Forge 使用内置的版本检查器来在模组过期时显示那个绿宝石图标。你可以把它关闭：

1. 打开你的 config/fml.toml 文件。
2. 找到 `versionCheck` 设置。
3. 将其设为 `false`：`versionCheck = false`
4. 保存并重启 Minecraft。

这会完全禁用版本检查，同时在启动时也会隐藏绿宝石图标。

另一种隐藏图标的方法，是直接通过 FancyMenu 把整个 Mods 按钮隐藏掉。隐藏这个按钮也会同时隐藏该图标。

# 隐藏原版 Realms 图标

如果它既不是 Mod Menu 也不是 Forge 的图标，那它很可能是 Minecraft 自己的 Realms 通知图标。这些图标大致会显示在 Realms 按钮的位置，并且可以在 FancyMenu 的布局编辑器中隐藏。你需要创建一个“针对当前屏幕”的布局（这里就是标题屏幕），然后你就会在编辑器中看到 Realms 图标作为一个独立元素。要隐藏它，只需**右键单击**它，然后点击 **Delete**。

Realms 图标可能是报纸图标、钻石图标，或者其他样式，比如带通知计数的红色圆圈。
