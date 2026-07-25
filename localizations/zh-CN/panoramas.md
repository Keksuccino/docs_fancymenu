---
title: 全景图
description: 创建并使用六图立方体全景图。
---
# 立方体全景图

每个全景图都有自己的目录，位于：

```text
<game-directory>/config/fancymenu/panoramas/
```

`<game-directory>` 是当前启动器实例的目录，它可能不同于常规的 `.minecraft` 目录。

# 目录结构

```text
<game-directory>/config/fancymenu/panoramas/
└── mypanorama/
    ├── properties.txt
    ├── overlay.png          # 可选
    └── panorama/
        ├── panorama_0.png
        ├── panorama_1.png
        ├── panorama_2.png
        ├── panorama_3.png
        ├── panorama_4.png
        └── panorama_5.png
```

六张面图必须是 PNG 文件，并且文件名必须与上方所示完全一致，且这六张图的尺寸必须完全相同。在某些操作系统上，文件名大小写可能会影响识别。

可在 `properties.txt` 旁边添加一个可选的 `overlay.png`，用于暗角或其他覆盖整个全景的叠加层。

# `properties.txt`

```text
type = panorama

panorama-meta {
  name = name_of_your_panorama
  speed = 1.0
  fov = 85.0
  angle = 25.0
  start_rotation = 0
}
```

| 属性 | 含义 |
|---|---|
| `name` | 必需，区分大小写的运行时标识符；请保持唯一 |
| `speed` | 旋转速度倍率；`1.0` 为默认值 |
| `fov` | 视野角度，单位为度 |
| `angle` | 垂直视角，单位为度 |
| `start_rotation` | 初始水平旋转角度，单位为度 |

只有 `name` 是必需项。缺少的可选值会使用示例中显示的默认值。请保持 `type = panorama` 和 `panorama-meta` 不变；每行写一个 `key = value`，小数请使用英文句点。

重复的名称不会被拒绝，目录扫描顺序会决定最终保留哪个全景图。请确保在 panoramas 目录中名称唯一。全景图和幻灯片使用的是分开的列表。

# 使用全景图

通过 **自定义 -> 重新加载 FancyMenu** 重新加载 FancyMenu，或重启客户端。然后右键单击布局编辑器背景，并选择 [**菜单背景**](./menu-backgrounds) -> **立方体全景图**。
