---
title: 布局本地化
description: 将文本和其他布局内容本地化。
---

# 布局本地化

对可翻译文本使用 [**本地化文本** 占位符](./placeholders#localize-text-local)：

```text
{"placeholder":"local","values":{"key":"modpack.menu.play"}}
```

FancyMenu 会先检查 Minecraft 当前启用的语言数据。如果其中不存在该键，它会继续检查 FancyMenu 的自定义本地化文件。如果两个来源都不包含该键，则会直接显示该键本身。

# FancyMenu 自定义本地化文件

将文件放在以下位置：

```text
<game-directory>/config/fancymenu/custom_locals/
```

为你的本地化文件创建一个子目录：

```text
custom_locals/
└── my_pack/
    └── text.json
```

请至少将本地化文件放在 `custom_locals` 下的一个子目录中；直接放在 `custom_locals` 根目录中的文件不会被加载。支持嵌套子目录。

支持的 UTF-8 格式：

| 扩展名 | 格式 |
|---|---|
| `.json` | JSON 对象；嵌套对象会变成以点号分隔的键 |
| `.lang` | `key=value` 行 |
| `.properties` | Java 属性语法 |

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

FancyMenu 会将这些子目录中的受支持文件合并为一个自定义本地化字典。每个键只应在一个文件中使用。自定义本地化文件不会随着 Minecraft 选择的语言而切换；如果你需要自动语言切换，请使用下面的资源包方法。

编辑自定义本地化文件后，请重启客户端。

# 特定语言文本

如果你希望随 Minecraft 选择的语言自动切换，请通过 [资源包](./resources#minecraft-resources-resource-packs) 提供标准的 Minecraft 语言文件：

```text
assets/<namespace>/lang/en_us.json
assets/<namespace>/lang/de_de.json
```

在每个语言文件中使用相同的键，启用资源包，然后通过 [**本地化文本** 占位符](./placeholders#localize-text-local) 读取它们。

# 本地化图片和元素

使用 [**游戏语言** 要求](./conditions#is-game-language-fancymenu_loading_requirement_is_language) 为不同的语言代码（例如 `en_us` 和 `de_de`）显示不同的元素或布局。
