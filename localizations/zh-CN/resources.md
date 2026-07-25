---
title: 资源
description: 介绍 FancyMenu 中资源的工作方式。涵盖资源位置、本地资源和网络资源。
---
# 资源

资源字段可以从以下来源加载内容：

- **Minecraft：** 由 Minecraft 或资源包提供的资源位置。
- **本地：** 当前游戏实例中的文件。
- **网络：** 直接的文件 URL。

大多数图片、音频、视频和文本字段都使用相同的资源选择器。该选择器包含一个用于浏览 Minecraft 和资源包内容的浏览器。

# Minecraft 资源（资源包）

资源位置使用 `namespace:path` 格式。命名空间是位于 `assets` 下一级的目录，而路径则是该命名空间下的所有内容。

例如，假设资源包中的一张图片存储在 `/assets/custom_resources/images/image.png`。
它的资源位置就是 `custom_resources:images/image.png`。

> [!NOTE]
> Minecraft 内置资源通常使用 `minecraft` 命名空间。

# 本地资源

将本地资源存放在 `<game-directory>/config/fancymenu/assets/` 中。`<game-directory>` 是当前启用的实例文件夹，它可能与 `.minecraft` 不同。

资源字段可能会显示相同的路径为 `/config/fancymenu/assets/example.png`。在这些字段中，开头的 `/` 仍然表示 `<game-directory>`；它不是文件系统根路径。

这些文件可以通过其 config 文件夹随 [模组包](./modpacks) 一起分发。

有关 FancyMenu 的布局、资源、配置以及生成状态路径的完整映射，请参阅 [数据存储位置](./data-storage-locations)。

# 网络资源

使用文件的直接 URL，例如 `https://example-domain.net/image.png`。与直接以资源文件名和扩展名结尾的 URL 相比，网页和重定向链接更慢，也更容易失败。

# 资源源中的占位符

带选择器的资源字段可以在本地路径、URL 和 Minecraft 资源位置中使用 [占位符](./placeholders)。选择源字段旁边的 **在编辑器中打开**，即可直接编辑。

> [!WARNING]
> 不使用普通选择器的资源输入可能不支持占位符或实时源更新。
