---
title: FancyMenu 的 UI 缩放
description: 如何更改 FancyMenu 的 UI 缩放。
---

# FancyMenu 的 UI 缩放

FancyMenu 的 UI（例如菜单栏和右键菜单）使用的是独立缩放，不会与 Minecraft 的常规 GUI 缩放联动。

如果你觉得 FancyMenu 的 UI 看起来太小或太大，可以通过 **菜单栏 -> 自定义 -> 设置 -> FancyMenu 的 UI** 来更改 UI 缩放。

FancyMenu 3.9.0 新增了更多 UI 缩放选项。当 UI 缩放设置为 **自动** 时，新的最小自动缩放值为 `1.25`；如果你更喜欢，也仍然可以手动选择 `1`。

唯一的例外是 FancyMenu 添加的实际全屏界面，例如变量管理界面或布局编辑器。这些界面在大多数情况下使用 Minecraft 的常规 GUI 缩放，但某些界面也可能使用不同的自动缩放逻辑，以便在窗口过小时自动以更小的缩放显示，从而容纳界面的全部内容。
