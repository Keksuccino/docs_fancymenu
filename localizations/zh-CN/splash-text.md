---
title: 启动文字
description: 如何在 FancyMenu 中制作自定义启动文字。
---

# 自定义启动文字元素

FancyMenu 中的“启动文字”元素是对 Minecraft 原版会弹跳的标题启动文字的完全可自定义升级版。它保留了熟悉的弹跳效果，同时让你可以控制显示内容、外观以及更新时间。

> 请注意，你其实无法真正自定义标题界面中原版的启动文字元素，所以你应该先把它**删除**，然后改用自定义的“启动文字”元素。
{.is-warning}

## 添加并选择该元素
- 打开布局编辑器并添加名为 `Splash Text` 的元素。
- 左键单击一次以选中它并显示边界框，然后右键打开其上下文菜单。所有配置选项都在那个菜单里。

## 选择启动文字的来源
- `Source Mode: Vanilla` 保留 Minecraft 自带的经典随机启动文字。
- `Source Mode: Direct Input` 允许你通过 `Input Splash Text` 输入自己的文字。它只支持一行启动文字，但这一行可以包含占位符。
- `Source Mode: Text File` 会从你通过 `Set Source Text File` 选择的 `.txt` 文件中随机读取一行。每一行非空文本都可以成为当前显示的启动文字。
- 切换模式会重置当前文本，因此你可以安全地进行尝试。如果文本看起来没有变化，可以切换到另一个模式，或者点击 `Refresh On Screen Load: Enabled`，让每次菜单打开时都强制重新抽取一次。

## 示例文本文件
使用“Text File”来源模式时，请将你的启动文字列表保存为纯文本（UTF-8，无 BOM）。每一行都可以作为一个候选启动文字：

```
Welcome to FancyMenu!
{"placeholder":"your_placeholder_id_here"}
{"text":"This is gold and bold text.","color":"gold","bold":true}
&6Use &lMinecraft formatting codes!
```

把 `your_placeholder_id_here` 替换为你希望在运行时解析的占位符。FancyMenu 会在每次启动文字刷新时随机选择一行非空文本。

## 按你想要的方式显示
- 使用 `Set Scale` 和 `Set Rotation` 来控制大小和旋转角度。
- `Set Text Color` 接受十六进制值（例如 `#FFFF00`），以匹配你的主题。
- `Shadow: Enabled` 会添加 Minecraft 的投影；关闭后则为平面文字。
- `Bouncing: Enabled` 会保留熟悉的上下弹跳效果；禁用后则显示为静态文本。
- FancyMenu 会将启动文字作为完整的 Minecraft 组件进行渲染，因此颜色代码和其他文字装饰都能按预期工作。

## 动态文本功能
- 占位符会在渲染前解析，因此你可以在启动文字中引用玩家名称、日期或其他受支持的值。
- 由于该元素接受 Minecraft 序列化组件 JSON，你可以将高级 JSON 片段直接粘贴到 Direct Input 或文本文件中。该元素会自动反序列化它们，如果出现问题则回退为字面文本。

## 故障排除
- 在 Direct Input 中如果文本为空，编辑时会显示 `< empty splash element >`。输入任意内容（哪怕只是一个空格）即可清除该警告。
- 如果文本文件中没有有效行，元素会显示 `ERROR: SPLASH FILE IS EMPTY`。请至少添加一行非空文本，然后重新打开界面。
- 序列化 JSON 出错时会回退为纯文本。请遵循 Mojang 标准 JSON 结构，或先使用原版 `/tellraw` 命令测试片段，再进行粘贴。
