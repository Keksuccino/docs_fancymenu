---
title: 预加载资源
description: 了解如何预加载资源，以便游戏加载完成后立即使用。
sourceBlobSha: 8eca400e05987468c1fd0dc29faa5267083e38d0
---

# 预加载资源

预加载会在菜单需要使用资源之前提前准备好选定的资源。对于可能出现闪烁、首帧为黑屏或启动较晚的资源，可以使用此功能。

# 将资源添加到预加载器

打开 **自定义 -> 预加载资源**。

<br>

<img width="350" alt="Screenshot_1" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/3265da80-1bbc-4634-bd94-ba2795d7e3f2">

列表支持来自本地文件、网络 URL 或资源包的图像、动画、音频、视频和文本资源。它不会预加载实时的 [浏览器](/elements#browser) 页面。

预加载器会在游戏启动和 Minecraft 资源重载时运行。它会等待每个条目加载完成或失败后再继续，每个条目的等待时间最长为两分钟。

已加载的资源会一直保留在缓存中，直到 FancyMenu 在重载或客户端关闭期间释放资源。**自定义 -> 重载 FancyMenu** 会释放缓存，但不会再次运行预加载器。

预加载会增加加载时间，并占用更多 RAM/VRAM。请仅添加必须立即就绪的资源；如果客户端内存不足，请移除较大的条目。

<br>

<img width="731" alt="Screenshot_2" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/04632d52-c2a9-4f70-9d0a-e88c4cacc4c1">

# 预加载幻灯片和全景图

添加[幻灯片](/slideshows)后，会加载其中的所有图像和可选叠加层。添加[全景图](/panoramas)后，会加载全部六个面和可选叠加层。

**自定义 -> 重载 FancyMenu** 不会运行预加载器。更改预加载列表后，请重载 Minecraft 资源或重启游戏。
