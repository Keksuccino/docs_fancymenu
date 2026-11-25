---
title: 资源
description: 了解 FancyMenu 中资源的工作方式，涵盖资源位置、本地资源和网络资源。
sourceBlobSha: eb783aaa0098ba295b3ebaf941bb4723e4d08970
---

# 资源

资源字段可以从以下位置加载内容：

- **Minecraft：**由 Minecraft 或资源包提供的资源位置。
- **本地：**当前游戏实例中的文件。
- **网络：**文件的直接 URL。

大多数图像、音频、视频和文本字段都使用相同的资源选择器。选择器内置了浏览器，可用于浏览 Minecraft 和资源包中的内容。

# Minecraft 资源（资源包）

资源位置采用 `namespace:path` 格式。命名空间是 `assets` 下一级目录的名称，而路径则是该命名空间目录下的所有内容。

例如，假设资源包图像存储在 `/assets/custom_resources/images/image.png`。
它的资源位置就是 `custom_resources:images/image.png`。

> [!NOTE]
> Minecraft 内置资源通常使用 `minecraft` 命名空间。

# 本地资源

将本地资源存储在 `<game-directory>/config/fancymenu/assets/` 中。`<game-directory>` 是当前实例的文件夹，可能与 `.minecraft` 不同。

资源字段中显示的路径可能与 `/config/fancymenu/assets/example.png` 相同。在这些字段中，开头的 `/` 仍表示 `<game-directory>`，而不是文件系统根目录。

这些文件可以通过整合包的配置文件夹[随整合包一起分发](/modpacks)。

如需完整了解 FancyMenu 的布局、资源、配置和生成状态文件路径，请参阅[数据存储位置](/data-storage-locations)。

# 网络资源

请使用文件的直接 URL，例如 `https://example-domain.net/image.png`。与以资源文件名和扩展名结尾的直接 URL 相比，网页链接和重定向链接速度更慢，也更容易失败。

# 资源来源中的占位符

使用资源选择器的资源字段可以在本地路径、URL 和 Minecraft 资源位置中使用[占位符](/placeholders)。点击来源字段旁的 **在编辑器中打开**，即可直接编辑。

> [!WARNING]
> 未使用标准资源选择器的资源输入框可能不支持占位符或实时更新来源。
