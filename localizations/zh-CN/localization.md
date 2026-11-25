---
title: 本地化布局
description: 本地化文本和其他布局内容。
sourceBlobSha: f4883414b07e0c024de7bef4f131b878ca4f5f37
---

# 本地化布局

对于需要翻译的文本，请使用 [**本地化文本**占位符](/placeholders#localize-text)：

```text
{"placeholder":"local","values":{"key":"modpack.menu.play"}}
```

FancyMenu 会先检查 Minecraft 当前启用的语言数据。如果其中没有对应的键，则会检查 FancyMenu 的自定义本地化文件。如果这两个来源中都没有该键，则会显示键本身。

# FancyMenu 自定义本地化文件

将文件放在以下目录中：

```text
<game-directory>/config/fancymenu/custom_locals/
```

为本地化文件创建一个子目录：

```text
custom_locals/
└── my_pack/
    └── text.json
```

请将本地化文件放在 `custom_locals` 的至少一个子目录中；直接放在 `custom_locals` 根目录中的文件不会被加载。支持嵌套子目录。

支持的 UTF-8 格式：

| 扩展名 | 格式 |
|---|---|
| `.json` | JSON 对象；嵌套对象会转换为以点分隔的键 |
| `.lang` | `key=value` 格式的行 |
| `.properties` | Java properties 语法 |

JSON 示例：

```json
{
  "modpack": {
    "menu": {
      "play": "Play"
    }
  }
}
```

这会定义 `modpack.menu.play`。

FancyMenu 会将这些子目录中的受支持文件合并到一个自定义本地化字典中。每个键只能在一个文件中使用。自定义本地化文件不会随 Minecraft 所选语言切换；如果需要自动切换语言，请使用下方的资源包方法。

编辑自定义本地化文件后，请重启客户端。

# 特定语言的文本

若要随 Minecraft 所选语言自动切换，请通过[资源包](/resources#minecraft-resources-resource-packs)提供标准的 Minecraft 语言文件：

```text
assets/<namespace>/lang/en_us.json
assets/<namespace>/lang/de_de.json
```

在每个语言文件中使用相同的键，启用资源包，然后使用[**本地化文本**占位符](/placeholders#localize-text)读取这些键。

# 本地化图像和元素

使用[**游戏语言是**条件](/conditions#is-game-language)，根据不同的语言代码（例如 `en_us` 和 `de_de`）显示不同的元素或布局。
