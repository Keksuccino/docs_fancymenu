---
title: 布局本地化
description: 如何本地化布局内容。
---

# 布局本地化

FancyMenu 不仅可以本地化文本内容，甚至还能本地化整个元素或布局！

# 文本内容

FancyMenu 允许你向游戏中添加自己的本地化内容。
之后可以配合 **本地化文本（Localize Text）** 占位符，根据当前游戏语言显示对应文本。

## 使用原版 Minecraft 本地化键

在创建自定义本地化之前，你可能想先使用现有的 Minecraft 本地化键。这样可以节省时间，并确保与原版 Minecraft 文本保持一致。

### 查找原版本地化键

查找 Minecraft 本地化键最简单的方法是在线浏览游戏的资源文件：

1. **访问 MCAsset.cloud：**  
   打开 [https://mcasset.cloud/](https://mcasset.cloud/) - 这个网站允许你在不从游戏中提取文件的情况下浏览 Minecraft 的资源。

2. **进入语言文件：**  
   - 从下拉菜单中选择你的 Minecraft 版本
   - 进入：`assets` → `minecraft` → `lang`
   - 打开 `en_us.json` 查看所有英文本地化内容

3. **找到你需要的键：**  
   - 使用浏览器搜索功能（Ctrl+F 或 Cmd+F）查找特定文本
   - 格式为 `"key": "text"` - 冒号（`:`）前带引号的第一部分就是键
   - 例如：`"menu.singleplayer": "Singleplayer"` - 键是 `menu.singleplayer`

### 使用模组本地化键

如果你安装了其他模组，也可以使用它们的本地化键：

1. 查看该模组的文档，了解可用的键
2. 如果模组是开源的，可以浏览它的语言文件

## 自定义本地化文件

本地化文件是文本文件，其中包含应以多种语言提供的所有文本内容。每个可翻译文本都有一个唯一的键，这样 Minecraft 就能在本地化文件中找到正确的可翻译文本。

- **默认文件（en_us.json）：**  
  美式英语。如果没有选择其他语言文件，就会使用这个文件。它作为备用语言文件。

- **其他语言文件：**  
  例如，你可以为使用德语的玩家创建一个名为 `de_de.json` 的文件。

### 如何创建自定义本地化文件

你始终需要一个 `en_us.json` 文件！如果没有它，当出现问题或设置了不支持的语言时，游戏将没有备用内容。

1. **打开文本编辑器：**  
   使用记事本（Windows）、TextEdit（Mac）或任何简单的文本编辑器。

2. **编写你的 JSON 代码：**  
   使用你的自定义键创建文件。键是 Minecraft 用来查找文本的唯一名称。例如：
   
   ```json
   {
     "modpack_name.custom.localization.key": "Your custom text here",
     "modpack_name.another.key": "Another message"
   }
   ```

3. **保存文件：**  
   将文件保存为 `en_us.json`，作为默认英文文本。

如果你现在想添加翻译版本，比如德语，可以把 `en_us.json` 文件中的内容复制到新文件里，只翻译实际文本，**不要**翻译键！键必须保持不变，这样游戏才能继续找到这些文本。

对于德语，你可以将文件保存为 `de_de.json`。其他语言请查看 [这篇 Minecraft Wiki 页面](https://minecraft.wiki/w/Language) 获取你语言对应的正确语言代码，并据此命名文件。请查找你语言的 **“in-game locale code”**。

## 为 MC 1.21.4 创建 Minecraft 资源包

现在本地化文件已经准备好了，我们需要一种方式将它们加载进 Minecraft。为此，我们将使用资源包。我们会让这个资源包默认启用，如果不想让模组包用户随意修改它，甚至可以把它隐藏起来。

**资源包（resource pack）** 是一个 ZIP 文件，里面包含会改变游戏外观和感觉的文件。

### 创建资源包的步骤

1. **创建新文件夹：**  
   创建一个名为 `my_custom_pack` 之类的文件夹，用来放入你的自定义本地化文件。

2. **创建包文件（`pack.mcmeta`）：**  
   在文件夹内创建一个名为 `pack.mcmeta` 的文件，内容如下：
   
   ```json
   {
     "pack": {
       "pack_format": 16,
       "description": "My Custom Pack with Localizations"
     }
   }
   ```
   
   *注意：`pack_format` 16 适用于 Minecraft 1.21.4。*

3. **添加你的本地化文件：**  
   在资源包文件夹中，创建以下文件结构：
   
   ```
   my_custom_pack/
   ├── assets/
   │   └── minecraft/
   │       └── lang/
   │           ├── en_us.json
   │           └── de_de.json
   └── pack.mcmeta
   ```
   
   将你的自定义 `en_us.json`（以及其他语言文件，如 `de_de.json`）放入 `lang` 文件夹中。

4. **将资源包压缩为 ZIP：**  
   文件夹准备好后，**将整个文件夹压缩为 ZIP 文件**。将 ZIP 文件命名为 **my_custom_pack.zip**。这是本指南中使用的示例名称。

## 将资源包放在哪里

将你的 **my_custom_pack.zip** 文件放到 **Minecraft Resourcepacks 文件夹** 中。该文件夹通常位于：

- **Windows：** `%appdata%\.minecraft\resourcepacks`
- **Mac：** `~/Library/Application Support/minecraft/resourcepacks`
- **Linux：** `~/.minecraft/resourcepacks`

> 对于模组包，`resourcepacks` 文件夹位于你的模组包实例目录中。
{.is-warning}

## 使用“Resource Pack Overrides”自动加载资源包

**Resource Pack Overrides** 模组可以让资源包默认启用。

### 自动加载资源包的步骤

1. **安装模组：**  
   从 [CurseForge](https://www.curseforge.com/minecraft/mc-mods/resource-pack-overrides) 或 [Modrinth](https://modrinth.com/mod/resource-pack-overrides) 下载并安装该模组。

2. **找到配置文件：**  
   找到 `.minecraft/config/resourcepackoverrides.json` 文件。  
   *如果文件不存在，请手动创建。*

3. **编辑配置文件：**  
   打开文件，并使用资源包的文件名将其添加到 `default_packs` 列表中：
   
   ```json
   {
     "schema_version": 2,
     "default_packs": [
       "file/my_custom_pack.zip"
     ]
   }
   ```
   
   这样 Minecraft 在启动游戏时就会自动加载你的资源包。

   **请务必添加 `file/` 前缀！**


*注意：列表中的资源包会按相反顺序应用。这意味着列表顶部的资源包会在游戏资源包菜单中显示在其他资源包下方。*

## 在选择界面中隐藏资源包

你可以将资源包隐藏起来，这样玩家在资源包选择界面中就看不到它。

### 如何隐藏它

1. **再次编辑配置文件：**  
   在同一个 `.minecraft/config/resourcepackoverrides.json` 文件中，为你的资源包添加覆盖设置：
   
   ```json
   {
     "schema_version": 2,
     "default_packs": [
       "file/my_custom_pack.zip"
     ],
     "pack_overrides": {
       "file/my_custom_pack.zip": {
         "hidden": true
       }
     }
   }
   ```
   
   这个配置会在自动加载 **my_custom_pack.zip** 的同时，将它从选择界面中隐藏。

## 在 FancyMenu 中使用新的本地化键

现在你的自定义本地化文件已经加载完毕，就可以在 FancyMenu 布局中使用新的键了。

1. **编辑一个基于文本的元素：**  
   打开 FancyMenu，选择一个元素，例如按钮或文本元素。

2. **点击占位符按钮：**  
   在文本编辑器右上角找到占位符按钮。（如果看不到，可能是该元素不支持占位符。）

3. **插入“本地化文本”占位符：**  
   “本地化文本”占位符会以 JSON 片段形式出现，看起来像这样：
   
   ```json
   {"placeholder":"local","values":{"key":"localization.key"}}
   ```
   
   将 `localization.key` 替换为你自己的自定义键。例如，如果你想使用本地化文件中的某个键，可以改成：
   
   ```json
   {"placeholder":"local","values":{"key":"modpack_name.custom.localization.key"}}
   ```

好了，基本就是这样！当不在文本编辑器中编辑时，这个占位符应该会被替换为实际的本地化内容。

请记住，这个占位符始终会根据当前游戏语言本地化文本内容。

# 非文本内容（图片等）

FancyMenu 也允许你本地化图片，基本上任何你想要的元素都可以。

为此，你需要使用 **加载条件**。
更具体地说，是 **是否为游戏语言（Is Game Language）** 条件。

**是否为游戏语言** 条件允许你仅在设置了特定游戏语言时显示元素或布局，因此例如你可以制作两个包含文字的图片元素：当语言设置为日语时显示日语版本图片，当语言设置为英语时显示英语版本图片。

要为**元素**设置加载条件，请右键单击它，然后点击 **加载条件（Loading Requirements）**。

要为**整个布局**设置加载条件，请右键单击布局编辑器背景，然后点击 **加载条件 [布局级]（Loading Requirements [Layout-Wide]）**。
