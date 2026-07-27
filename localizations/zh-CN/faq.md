---
title: 常见问题
description: 常见问题解答。
---
# 常见问题

### 我需要帮助解决一个问题。我应该提供哪些信息？

为了获得最佳帮助，请尽可能提供更多上下文：
1.  **清晰的问题描述：** 你期望发生什么，实际发生了什么？
2.  **你的 `latest.log` 文件：** 位于 `<game-directory>/logs/latest.log`。**不要发送崩溃日志**，除非特别要求；`latest.log` 通常已经包含所需的上下文。发布时请使用 https://gist.github.com 之类的网站。
3.  **你的 Minecraft 版本：**（例如 1.20.1）
4.  **你的模组加载器及其版本：**（例如 Forge 47.2.0、Fabric 0.15.7）
5.  **你的 FancyMenu 版本：**（例如 3.5.2）
6.  **问题的截图或视频** 也会非常有帮助。

### 我该如何改变元素的层级（把某个元素移到另一个前面或后面）？

*   **自定义 vs. 自定义：** 打开 **Window -> Editor Widgets -> Layers**，然后在层级结构中拖动元素。你也可以右键单击某个元素，使用 **Move One Layer Up/Down**。参见 [层和组](./layers-and-groups)。
*   **自定义 vs. 原版：** 若要让所有自定义元素渲染在所有原版元素后面（例如把背景图片放到默认按钮后面），请**右键单击编辑器背景**并切换选项 **"Render Custom Elements Behind Vanilla"**。

### 我可以把某些按钮排除在通用按钮模板之外吗？

**不行。如果模板按钮设置了自定义纹理，这些纹理始终会与所有受影响的元素共享。你不能排除单个按钮。**

### 我该如何让按钮在点击时执行某些操作？

使用 [**动作脚本**](./action-scripts)。
1.  在编辑器中右键单击该按钮。
2.  选择 **Edit Action Script**。
3. 点击 **Add Action** 并选择一个动作，例如 [**Open Screen or Custom GUI**](./action-scripts#open-screen-or-custom-gui-opengui)、[**Join Server**](./action-scripts#join-server-joinserver) 或 [**Set Variable Value**](./action-scripts#set-variable-value-fm-variable-set_variable)。

### 我可以从头创建一个全新的菜单界面吗？

请使用 [**自定义 GUI**](./custom-guis)。
1.  在菜单栏中，进入 **Customization -> Custom GUIs -> Manage Custom GUIs**。
2.  点击 **"New GUI"** 并为其指定一个唯一标识符。
3.  然后你就可以打开这个新的空白界面并为其创建布局，添加任意元素。
4. 使用 [**Open Screen or Custom GUI** 动作](./action-scripts#open-screen-or-custom-gui-opengui) 打开该自定义 GUI。

### 启用预加载后，我的游戏加载时间变长了。

这是正常现象。在初始启动时预加载高分辨率动画或音效等大型资源，必然会增加游戏加载时间。

### 我的 FMA 动画占用太多内存了！

经典 [FMA 动画](./fma) 在包含许多高分辨率帧时会消耗大量内存。AFMA 更适合大型或复杂的动画纹理。请将经典 FMA 动画保持简短；若需要完整视频播放，请使用 [Video](./video)。

### FancyMenu 可以和 OptiFine 一起使用吗？

不可以。OptiFine **不兼容**，并且已知会破坏许多模组，包括 FancyMenu。强烈建议使用 Sodium/Embeddium + Iris/Oculus 等现代替代方案。
参见 [OptiFine 替代方案](./optifine-alternatives)。

### 我的游戏崩溃了。我该如何判断是不是模组冲突？

检查模组冲突的最佳方法是：**只运行 FancyMenu 及其依赖项**（Konkrete、Melody）。如果崩溃不再发生，你可以再把其他模组分小组加回去，直到崩溃再次出现，以此找出冲突模组。

### 当我尝试编辑另一个模组的按钮时，它消失了或无法使用。

有些模组添加小部件的方式是 FancyMenu 无法检测或自定义的。请查看 [原版/模组元素](./vanilla-elements)，对于列表型界面，请查看 [自定义可滚动界面](./customizing-scrollable-screens)。如果该小部件仍然不显示，那么添加它的模组必须将其公开为受支持的界面小部件。

### 我可以在服务器上使用 FancyMenu 布局吗？

布局和视觉自定义保存在玩家客户端上；服务器无法强制将它们应用到未配置的客户端上。请将它们作为模组包的一部分分发。当你需要 [服务器命令](./commands)、[FM 数据](./fm-data)、[服务器端 NBT 访问](./nbt-data-placeholder#server-side-placeholder)、游戏规则、结构或服务器监听器时，请在服务器上安装 FancyMenu。

### FancyMenu v2（适用于较旧 MC 版本）和 v3 有什么区别？

FancyMenu v3 是一次彻底重写，带来了许多新功能、更稳定的架构以及更好的性能。v2 已经过时，不再受支持，并且缺少许多功能，例如高级占位符和脚本。强烈建议在现代 Minecraft 版本（1.18.2+）上使用 v3。加载 v2 布局时可以自动转换为 v3，但可能需要一些手动修复。

### 我可以在哪里找到现成的布局和模板？

FancyMenu 社区会在官方 Keksuccino's Mods Discord 服务器（“Kekscord”）的 `#layout-templates` 频道分享布局。

### 我如何让 Player Entity 渲染在其他元素后面？

通常你无法通过 [Layers 小部件](./layers-and-groups) 强制 [Player Entity 元素](./elements#player-entity) 位于普通 2D 元素后面。它的渲染器可以忽略正常的 GUI 层级顺序。请围绕这一限制设计布局，或者在需要严格层级顺序时使用预渲染图像。

### 我的 Player Entity 只有一条腿！发生什么了？

这是一个视觉故障，很可能是由与另一个会修改玩家动画或模型的模组发生冲突引起的。检查 Player Entity 的姿势设置，看看腿部是否被意外旋转或移动了。

### 我该如何在脚本中创建动作之间的延迟？

使用 [**Delay** 或 **Execute Later** 块](./action-scripts#what-are-statements) 来实现延迟动作逻辑。对于重复性的后台逻辑，请使用 [Schedulers](./schedulers)。

### 我可以自定义 Create 模组的菜单吗？

不可以。Create 的界面有意禁用了自定义。参见 [已明确禁用自定义的界面](./incompatibility-list#screens-where-customization-is-intentionally-disabled)。

### 背景图片和按钮纹理推荐使用什么分辨率？

背景：标准的 1920x1080（1080p）图片是很好的起点，适合大多数用户并能很好地缩放。
按钮：大多数原版按钮宽度约为 150-200 像素，高度约为 20 像素。为自定义纹理匹配这一尺寸是保持一致性的好做法。

### 有没有办法在玩家完成游戏内目标（比如任务）时自动打开菜单或运行命令？
FancyMenu 有许多[内置游戏事件监听器](./listeners)，但并没有针对每个第三方任务系统的通用监听器。如果任务模组支持命令奖励，请使用其中一个来运行 [`/openguiscreen`](./commands#openguiscreen)、[`/fmvariable`](./commands#fmvariable) 或其他合适的 [FancyMenu 命令](./commands)。

### 我该如何让按钮变为不可用或“灰掉”状态？

你可以使用 [加载条件](./conditions) 来控制按钮的激活状态。
在编辑器中右键单击该按钮并选择 **Control Active State**。
添加一个必须满足的条件，以便按钮处于激活状态。若要永久禁用它，请使用 [**Is Number**](./conditions#is-number-fancymenu_visibility_requirement_is_number) 来检查 0 是否等于 1。
这样按钮就会使用其“Inactive Background”纹理，并且无法点击。

### 我该如何移除可滚动界面上的顶部和底部（泥土纹理栏）？

在布局编辑器中打开 **Layout Properties -> Header/Footer Customizations**。将纹理设置为透明。某些模组界面可能无法使用此选项。

### 我无法创建“当前界面”的布局。这个按钮是灰色的。

你需要先通过 **menu bar -> Customization -> Current Screen Customizations -> Enabled** 为该界面启用自定义。

### 我在编辑器中打开一个界面时，无法自定义其中的任何元素。结果它只是个空白界面。

这可能意味着你创建的是一个 [通用布局](./universal-layouts)，而不是一个**针对当前界面**的布局。

也可能它是一个[可滚动界面](./customizing-scrollable-screens)，而 FancyMenu 默认无法自定义它。

第三种可能是，这是一个由模组添加元素且方式非原版的界面，这会导致 FancyMenu 无法自定义这些元素。

### 我的 Text 元素上有奇怪的灰色方块。

这些半透明方块是 [Text 元素](./elements#text) 的滚动拖块，不是渲染错误。

如果你不希望这些方块可见，可以右键单击该元素并完全禁用滚动；或者如果你希望元素仍可滚动，也可以在相同的右键菜单中将拖块纹理设置为完全透明。

### 我如何在菜单中显示最新的 Minecraft 更新日志？

有一个很棒的 [GitHub 项目](https://github.com/ClaytonTDM/minecraft-changelogs-markdown)，它可以将 Minecraft 的更新日志转换为与 FancyMenu 兼容的 Markdown，这样你就可以在菜单中显示最新的 MC 更新日志了！它会每天更新以获取新的更新日志。

要在 [Text 元素](./elements#text) 中显示它，请将 **Source Mode** 设置为 **Resource**，并将其资源源设置为 **Web**。使用 `https://clay.is-a.dev/minecraft-changelogs-markdown/{"placeholder":"mcversion"}/fancymenu.md`。

### 将任意元素拉伸到屏幕大小的最简单方法是什么？

大多数元素的右键菜单中都有一个选项，可以将其水平和垂直拉伸。启用后，它会始终拉伸到屏幕的全宽和/或全高。水平和垂直拉伸可以分别切换。

### 当按钮或滑块位于 Text 元素后面或前面时，我无法点击它们或与之交互。

这是因为 Text 元素默认是可交互的（这样才能拖动滚动条或点击 Markdown 超链接），这意味着它会消耗鼠标点击和滚轮事件。最好的办法是不要把按钮放到 Text 元素前后，如果实在无法避免，你可以通过**右键单击**该 Text 元素并将 **Interactable** 设为 **Disabled**，使其不可交互。请注意，这会让 Text 元素变成静态、不可交互的文本，因此你将无法再滚动它或点击超链接。

### 我该如何让按钮和滑块在使用方向键和 Tab 键浏览界面时不再被选中/聚焦？

要让按钮和滑块不可导航，你需要**右键单击**它并将 **Navigable** 设为 **Disabled**。按钮/滑块仍然可以点击，但你将无法再通过方向键/Tab 导航聚焦它。

如果你想在聊天界面中添加按钮/滑块，这也很有用；这样你仍然可以使用向上方向键滚动查看更早的消息，而不会意外选中界面中的按钮/滑块。

### FancyMenu 的某个右键菜单缺少一个应该存在的选项。

FancyMenu 的右键菜单（即你在某处右键单击或与菜单栏交互时打开的菜单）是**可滚动的**。这意味着你可以在鼠标指针位于菜单上方时使用滚轮上下滚动，从而看到之前不可见的更多选项。

### 我无法自定义标题界面，离开编辑器后它总是显示原版内容。

另一个模组正在替换原始的 `title_screen`。请在该模组的设置中禁用其自定义标题界面。如果它没有这样的选项，那么 FancyMenu 就无法将布局应用到替换后的界面上。
