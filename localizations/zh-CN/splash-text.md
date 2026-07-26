---
title: 闪屏文字
description: 如何在 FancyMenu 中制作自定义闪屏文字。
---
# 自定义闪屏文字元素

FancyMenu 里的闪屏文字元素，是对 Minecraft 原版会弹跳的标题闪屏文字的完全可自定义升级版。它保留了熟悉的弹跳效果，同时让你可以控制显示内容、外观，以及何时更新。

> [!WARNING]
> 请注意，你其实无法真正自定义标题界面中的原版 Vanilla 闪屏文字元素，所以你应该把它**删除**，然后改用自定义的闪屏文字元素。

## 添加与选择元素
- 打开布局编辑器，并添加名为 `Splash Text` 的元素。
- 左键单击一次以选中它并显示边界框，然后右键打开它的上下文菜单。所有配置选项都在那个菜单里。

## 选择闪屏文字的来源
- `Source Mode: Vanilla` 会保留 Minecraft 自带的经典随机闪屏文字。
- `Source Mode: Direct Input` 允许你通过 `Input Splash Text` 输入自己的文字。它只支持单行闪屏文字，但这一行可以包含占位符。
- `Source Mode: Text File` 会从你通过 `Set Source Text File` 选择的 `.txt` 文件中随机读取一行。每一行非空内容都可以成为当前显示的闪屏文字。
- 切换模式会重置当前文字，所以你可以放心尝试。如果文字看起来一直没变，可以切换到另一个模式，或者点击 `Refresh On Screen Load: Enabled`，强制每次打开菜单时重新抽取一次。

## 示例文本文件
当使用“Text File”来源模式时，请将你的闪屏列表保存为纯文本（UTF-8，无 BOM）。每一行都可以作为一个可能的闪屏文字：

```
欢迎来到 FancyMenu！
{"placeholder":"your_placeholder_id_here"}
{"text":"This is gold and bold text.","color":"gold","bold":true}
&6Use &lMinecraft formatting codes!
```

将 `your_placeholder_id_here` 替换为你希望在运行时解析的占位符。FancyMenu 每次刷新闪屏文字时，都会随机选择一行非空内容。

## 按你想要的方式调整外观
- 使用 `Set Scale` 和 `Set Rotation` 来控制大小和旋转角度。
- `Set Text Color` 接受十六进制颜色值（例如 `#FFFF00`），以匹配你的主题。
- `Shadow: Enabled` 会添加 Minecraft 的投影效果；关闭它则变为扁平文字。
- `Bouncing: Enabled` 会保留熟悉的上下弹跳动画；禁用后则显示为静态标签。
- FancyMenu 会将闪屏文字渲染为完整的 Minecraft 组件，因此颜色代码和其他文字装饰都能按预期生效。

## 动态文字功能
- 占位符会在渲染前解析，因此你可以在闪屏文字中引用玩家名称、日期或其他受支持的值。
- 由于该元素接受 Minecraft 的序列化组件 JSON，你可以将高级 JSON 片段直接粘贴到 Direct Input 或文本文件中。元素会自动反序列化这些内容，如果出现问题则回退为字面文本。

## 故障排除
- 在 Direct Input 中输入空文本时，编辑过程中会显示 `< empty splash element >`。输入任意内容（哪怕只是一个空格）即可清除该警告。
- 如果文本文件中没有任何有效行，元素会显示 `ERROR: SPLASH FILE IS EMPTY`。请至少添加一行非空内容并重新打开界面。
- 序列化 JSON 出错时会回退为纯文本。请使用 Mojang 的标准 JSON 结构，或者在粘贴前先用原版 `/tellraw` 命令测试片段。
