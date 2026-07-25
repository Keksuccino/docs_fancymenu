---
title: 幻灯片播放
description: 创建并使用图片幻灯片播放。
---
# 幻灯片播放

每个幻灯片播放在下面都有自己的目录：

```text
<game-directory>/config/fancymenu/slideshows/
```

`<game-directory>` 是当前活动的启动器实例，可能与常规的 `.minecraft` 目录不同。

# 目录结构

```text
<game-directory>/config/fancymenu/slideshows/
└── myslideshow/
    ├── properties.txt
    ├── overlay.png          # 可选
    └── images/
        ├── image_01.png
        └── image_02.jpg
```

图片必须使用 `.png` 或 `.jpg`；其他扩展名（包括 `.jpeg`）都会被忽略。

当 `randomize = false` 时，图片会按文件名的字母顺序播放，不区分大小写。请使用带前导零的名称，例如 `image_01.png`、`image_02.png` 和 `image_10.png`。

# `properties.txt`

```text
type = slideshow

slideshow-meta {
  name = cool_slideshow
  width = 1920
  height = 1080
  x = 0
  y = 0
  duration = 5.0
  fadespeed = 12.0
  randomize = false
}
```

| 属性 | 含义 |
|---|---|
| `name` | 必填，运行时标识符，区分大小写；请保持唯一 |
| `width`, `height` | GUI 缩放后的基准像素大小，以及源图像的宽高比 |
| `x`, `y` | 基准左上角位置；普通元素和背景会使用各自的位置，因此请保持为 `0` |
| `duration` | 两次切换开始之间的最少秒数；包括淡入淡出时间，且必须大于 `0` |
| `fadespeed` | 淡出/淡入速度倍数；`1.0` 为默认值，数值越高淡出越快，且必须大于 `0` |
| `randomize` | `true` 表示随机选择，`false` 表示按文件名顺序 |

只有 `name` 是必填项。默认值为 `width = 50`、`height = 50`、`x = 0`、`y = 0`、`duration = 10.0`、`fadespeed = 1.0` 和 `randomize = false`。请保持 `type = slideshow` 和 `slideshow-meta` 不变；每行只写一个 `key = value`，小数点使用英文句点。

布局会选择 `name` 的值，而不是目录名。重复的名称不会被拒绝，目录扫描顺序决定保留哪个幻灯片播放。请确保在 slideshows 目录内名称唯一。

随机模式会在每次切换时独立选择，并在有多个图片可用时避免立即重复。计时使用真实时间；如果淡出/淡入时间长于 `duration`，则下一次切换会延后；如果一个幻灯片播放在隐藏后再次显示，可能会立即推进到下一张。

# 使用幻灯片播放

通过 **Customization -> Reload FancyMenu** 重新加载 FancyMenu，或重启客户端。使用 [**Slideshow** 元素](./elements#slideshow)，或者在布局编辑器背景上右键，选择 [**Menu Backgrounds**](./menu-backgrounds) -> **Slideshow**。
