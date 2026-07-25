---
title: FancyMenu 的 UI 缩放
description: 如何更改 FancyMenu 的 UI 缩放。
---
# FancyMenu 的 UI 缩放

FancyMenu 的 UI（例如菜单栏和上下文菜单）使用的是单独的缩放，不会与 Minecraft 的普通 GUI 缩放联动。

如果 FancyMenu 的 UI 看起来对你来说太小或太大，你可以通过 **菜单栏 -> 自定义 -> 设置 -> FancyMenu 的 UI** 来更改 UI 缩放。

当 UI 缩放设置为 **自动** 时，最小的自动缩放值是 `1.25`。你也可以手动选择 `1` 这个缩放值。

唯一的例外是 FancyMenu 添加的实际全屏界面，例如管理变量的界面或布局编辑器。这些界面在大多数情况下会使用 Minecraft 的普通 GUI 缩放，但也有可能某些界面会使用不同的自动缩放逻辑，以便在窗口太小时自动以较小的缩放显示，从而容纳整个界面的所有内容。
