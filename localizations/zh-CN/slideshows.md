---
title: 幻灯片放映
description: 依次显示你自己的图片，并在图片之间柔和淡入淡出，可用作菜单背景或显示在屏幕的一部分区域。
sourceBlobSha: 24ba0cbe9184108453b9829b8e6cd48d49a48b12
---

# 幻灯片放映

幻灯片放映会依次显示图片，并在图片之间柔和地淡入淡出，就像展示整合包世界的截图一样。

你可以将它用作布局的[菜单背景](/menu-backgrounds)，也可以通过屏幕某个区域中的[幻灯片放映元素](/elements#slideshow)来显示。

<img width="800" alt="带有幻灯片背景的标题屏幕，背景从河谷淡入樱花林和海岸，均为 Minecraft 世界的截图" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/slideshows_title.gif?raw=true">

# 创建幻灯片放映

1. 打开游戏目录下 `config/fancymenu/` 中的 `slideshows` 文件夹。**菜单栏 -> 工具 -> 打开 FancyMenu 目录**可以打开 `config/fancymenu/`。
2. 在其中为幻灯片放映创建一个文件夹，例如 `world_tour`。文件夹名称不限。
3. 在文件夹中放入一个 [`properties.txt`](#propertiestxt) 文件，以及一个名为 `images` 的文件夹，并将[图片](#图片)放入其中。还可以选择添加一个 [`overlay.png`](#覆盖图)。
4. 通过**菜单栏 -> 自定义 -> 重新加载 FancyMenu** 或按 `Ctrl + Alt + R`（macOS 上为 `Cmd + Alt + R`）重新加载 FancyMenu，也可以重启游戏。

```text
config/fancymenu/slideshows/
└── world_tour/
    ├── properties.txt
    ├── overlay.png
    └── images/
        ├── 01_river_valley.png
        ├── 02_cherry_grove.png
        └── 03_coast.png
```

# 图片

- 只有 PNG 和 JPG 文件会被识别，文件名必须以 `.png` 或 `.jpg` 结尾。请将 `.jpeg` 文件重命名为 `.jpg`。
- 图片按照文件名的字母顺序显示，从 A 到 Z。数字也按字符排序，因此 `10.png` 会排在 `2.png` 前面。请在数字前补零，例如 `01`、`02`……`10`。
- 所有图片的尺寸应相同。幻灯片放映的比例由第一张图片决定，其余图片会拉伸至相同尺寸。
- `images` 文件夹内子文件夹中的文件不会被识别。

# properties.txt

```text
type = slideshow

slideshow-meta {
  name = world_tour
  duration = 5.0
  fadespeed = 5.0
  randomize = false
}
```

| 设置 | 作用 |
|---|---|
| `name` | 用于选择幻灯片放映的名称。每个幻灯片放映都应使用不同的名称。 |
| `duration` | 从一张图片切换到下一张图片所需的秒数，包括淡入淡出时间。如果淡入淡出耗时更长，下一次切换会等它完成后再进行。 |
| `fadespeed` | 图片之间淡入淡出的速度。设为 `1.0` 时，淡入淡出约需 6 秒；设为 `3.0` 时，约需 2 秒。必须大于 `0`。 |
| `randomize` | 设为 `true` 时，图片会以随机顺序显示，且不会连续两次显示同一张。设为 `false` 时，图片会按文件名顺序显示。 |

只有 `name` 是必填项。未设置的选项将使用默认值：`duration = 10.0`、`fadespeed = 1.0` 和 `randomize = false`。请保持 `type = slideshow` 和 `slideshow-meta {` 这两行不变，每行填写一个设置，小数请使用英文句点，例如 `2.5`。

为旧版本创建的幻灯片放映可能包含 `width`、`height`、`x` 和 `y` 行。这些设置不会产生任何效果：幻灯片放映的显示位置和大小由背景或元素决定。

# 覆盖图

将 `overlay.png` 放在 `properties.txt` 旁边后，它会显示在每张图片上方，并拉伸至幻灯片放映的尺寸。覆盖图不会随图片淡入淡出，因此适合用于边框、暗角或角落里的徽标。覆盖图中的透明区域会透出图片。

覆盖图属于该幻灯片放映，因此无论幻灯片放映显示在哪里，它都会出现。如果想让同一组图片既能显示边框，也能不显示边框，请创建两个幻灯片放映。

# 使用幻灯片放映

## 作为菜单背景

<img width="800" alt="打开菜单背景设置，在布局编辑器中选择幻灯片放映，启用显示背景并在选择幻灯片放映中选取 world_tour，预览会淡入下一张图片，随后幻灯片放映显示在标题屏幕按钮后方" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/slideshows_background.gif?raw=true">

1. 在[布局编辑器](/layout-editor)中右键单击背景，然后打开**菜单背景 -> 幻灯片放映**。
2. 点击**显示背景**以启用此选项。
3. 点击**幻灯片放映名称**，选择你的幻灯片放映，然后点击**完成**。右侧的预览会显示正在播放的效果。

点击**清除幻灯片放映**即可移除它。如需将它与其他背景组合使用，请参阅[菜单背景](/menu-backgrounds)。

幻灯片放映会拉伸至整个屏幕。若要保持图片原有的比例，请在**菜单背景**中启用**保持背景纵横比**。这样，图片会铺满屏幕，并在左右两侧或上下边缘被裁切。

## 作为元素

<img width="800" alt="标题屏幕的按钮位于左侧，右侧有一个幻灯片放映元素，依次淡入淡出显示 Minecraft 世界的截图" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/slideshows_element.gif?raw=true">

1. 在布局编辑器中右键单击空白区域，然后通过**新建元素**添加一个幻灯片放映。
2. 右键单击该元素，点击**幻灯片放映**，然后选择你的幻灯片放映。元素会采用图片的纵横比。
3. 像调整其他元素一样移动和调整它的大小。点击**恢复纵横比**会根据元素高度重新调整宽度，避免图片被拉伸。

## 预加载

幻灯片放映会在每张图片首次显示时加载它，因此较大的图片第一次出现时可能会稍有延迟。若要在游戏启动时加载所有图片和覆盖图，请通过**菜单栏 -> 自定义 -> 预加载资源**中的**添加幻灯片放映**添加该幻灯片放映。请参阅[预加载资源](/preload-layouts#pre-loading-slideshows--panoramas)。

# 注意事项

- 所有显示同一个幻灯片放映的地方都会同时显示同一张图片，不同菜单中也是如此。
- 只有在某处显示时，幻灯片放映才会运行。如果它停止显示一段时间后再次出现，且间隔超过其 `duration`，它会立即淡入下一张图片。
- 重新加载 FancyMenu 会重置所有幻灯片放映。重置后显示的第一张图片只会显示其他图片一半的时长。
- 幻灯片放映属于当前加载的[配置文件](/profiles)。
- 如果某个幻灯片放映没有出现在**选择幻灯片放映**中，说明它未能加载。游戏日志 `logs/latest.log` 会说明原因，例如缺少 `name`、`properties.txt` 或 `images` 文件夹。
- 在 Windows 上，请在文件资源管理器中启用文件扩展名显示，避免意外将文件名保存为 `properties.txt.txt`。
- 如果出现紫黑色棋盘格，说明尚未选择幻灯片放映，或布局使用的幻灯片放映名称已不存在。
- 如果两个幻灯片放映使用了相同的 `name`，只会显示其中一个。
- **调试覆盖层**（`Ctrl + Alt + D`）会显示 FancyMenu 加载的幻灯片放映和图片数量。
