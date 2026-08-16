---
title: 常见问题
description: 常见问题解答。
---
# 常见问题

### 我遇到了一个问题，需要帮助。我应该提供哪些信息？

为了获得最好的帮助，请尽可能提供更多上下文信息：
1.  **问题的清晰描述：** 你原本预期会发生什么，实际又发生了什么？
2.  **你的 `latest.log` 文件：** 位置在 `<game-directory>/logs/latest.log`。**不要发送崩溃日志**，除非对方明确要求；`latest.log` 通常已经包含所需的上下文。发布时请使用 https://gist.github.com 之类的网站。
3.  **你的 Minecraft 版本：**（例如 1.20.1）
4.  **你的模组加载器及其版本：**（例如 Forge 47.2.0、Fabric 0.15.7）
5.  **你的 FancyMenu 版本：**（例如 3.5.2）
6.  **问题的截图或视频** 也会非常有帮助。

### 如何更改元素的层级（将某个元素移到另一个元素前面或后面）？

*   **自定义 vs. 自定义：** 打开 **Window -> Editor Widgets -> Layers**，并在层级结构中拖动元素。你也可以右键单击某个元素，并使用 **Move One Layer Up/Down**。请参阅 [图层和组](./layers-and-groups)。
*   **自定义 vs. 原版：** 如果你想让所有自定义元素渲染在所有原版元素后面（例如把背景图放在默认按钮后面），请**右键单击编辑器背景**，然后切换 **"Render Custom Elements Behind Vanilla"** 选项。

### 我可以从通用按钮模板中排除某些按钮吗？

**不可以。如果模板按钮设置了自定义纹理，这些纹理始终会共享给所有受影响的元素。你无法排除单个按钮。**

### 如何让按钮在点击时执行某些操作？

使用 [**Action Script**](./action-scripts)。
1.  在编辑器中右键单击该按钮。
2.  选择 **Edit Action Script**。
3. 点击 **Add Action**，然后选择一个动作，例如 [**Open Screen or Custom GUI**](./action-scripts#open-screen-or-custom-gui-opengui)、[**Join Server**](./action-scripts#join-server-joinserver) 或 [**Set Variable Value**](./action-scripts#set-variable-value-fm-variable-set_variable)。

### 我可以从零创建一个全新的菜单界面吗？

使用 [**Custom GUI**](./custom-guis)。
1.  在菜单栏中，进入 **Customization -> Custom GUIs -> Manage Custom GUIs**。
2.  点击 **"New GUI"** 并为其指定一个唯一标识符。
3.  然后你可以打开这个新的空白界面并为其创建布局，添加你想要的任何元素。
4. 使用 [**Open Screen or Custom GUI** 动作](./action-scripts#open-screen-or-custom-gui-opengui) 打开这个 Custom GUI。

### 启用预加载后，我的游戏加载时间变长了。

这是预期行为。在初始启动时预加载高分辨率动画或音效等大型资源，自然会增加游戏加载时间。

### 我的 FMA 动画占用太多内存了！

经典 [FMA 动画](./fma) 在包含许多高分辨率帧时可能会消耗大量内存。AFMA 更适合大型或复杂的动画纹理。请尽量让经典 FMA 动画保持简短；如果需要完整视频播放，请使用 [Video](./video)。

### FancyMenu 可以和 OptiFine 一起使用吗？

不可以。OptiFine **不兼容**，并且已知会破坏许多模组，包括 FancyMenu。强烈建议使用现代替代方案，例如 Sodium/Embeddium + Iris/Oculus。
请参阅 [OptiFine Alternatives](./optifine-alternatives)。

### 我的游戏崩溃了。我该如何判断是否是模组冲突？

检查模组冲突的最佳方法是**只安装 FancyMenu 及其依赖项（Konkrete、Melody）运行游戏**。如果崩溃不再发生，你可以把其他模组分成小组逐步加回去，直到再次出现崩溃，从而找出冲突的模组。

### 我尝试编辑时，另一个模组的按钮消失了，或者无法正常工作。

某些模组添加控件的方式 FancyMenu 无法检测或自定义。请查看 [原版/模组元素](./vanilla-elements)，对于基于列表的界面，请查看 [自定义可滚动界面](./customizing-scrollable-screens)。如果该控件仍然不显示，则添加它的模组必须将其暴露为受支持的界面控件。

### 我可以在服务器上使用 FancyMenu 布局吗？

布局和视觉自定义会保存在玩家客户端上；服务器不能强制未配置的客户端使用它们。请将它们作为模组包的一部分分发。如果你需要 [服务器命令](./commands)、[FM Data](./fm-data)、[服务器端 NBT 访问](./nbt-data-placeholder#server-side-placeholder)、游戏规则、结构或服务器监听器，请在服务器上安装 FancyMenu。

### FancyMenu v2（适用于较旧 MC 版本）和 v3 有什么区别？

FancyMenu v3 是一次完整重写，带来了许多新功能、更稳定的架构以及更好的性能。V2 已过时，不再受支持，而且缺少许多功能，例如高级占位符和脚本。强烈建议在现代 Minecraft 版本（1.18.2+）上使用 v3。加载 V2 布局时可以自动转换为 v3，但可能仍需要手动修复一些内容。

### 我在哪里可以找到预制布局和模板？

FancyMenu 社区会在官方 Keksuccino's Mods Discord 服务器（“Kekscord”）的 [`#layout-templates`](https://discord.com/channels/704163135787106365/1234093433795383316) 频道分享布局。

### 如何让 Player Entity 渲染在其他元素后面？

通常你不能通过 [Layers 小部件](./layers-and-groups) 强制 [Player Entity 元素](./elements#player-entity) 位于普通 2D 元素之后。它的渲染器可能会忽略正常的 GUI 层级顺序。请围绕这一限制来设计布局，或者在需要严格层级顺序时使用预渲染图像。

### 我的 Player Entity 只剩下一条腿了！怎么回事？

这是一个视觉故障，很可能是因为与另一个会修改玩家动画或模型的模组发生了冲突。检查 Player Entity 的 Pose 设置，看看腿是否被意外旋转或移动了。

### 如何在脚本中创建动作之间的延迟？

使用 [**Delay** 或 **Execute Later** 语句块](./action-scripts#what-are-statements) 来实现延迟动作逻辑。对于重复的后台逻辑，请使用 [Schedulers](./schedulers)。

### 我可以自定义 Create 模组的菜单吗？

不可以。Create 的界面故意禁用了自定义。请参阅 [明确禁用自定义的界面](./incompatibility-list#screens-where-customization-is-intentionally-disabled)。

### 背景图片和按钮纹理的推荐分辨率是多少？

背景：标准的 1920x1080（1080p）图片是一个很好的起点，并且能很好地适配大多数用户。
按钮：大多数原版按钮宽度约为 150-200 像素，高度约为 20 像素。自定义纹理尽量匹配这个尺寸，有助于保持一致性。

### 有没有办法在玩家完成游戏内目标（例如任务）时自动打开菜单或执行命令？
FancyMenu 内置了许多 [游戏事件监听器](./listeners)，但没有针对每一种第三方任务系统的通用监听器。如果任务模组支持命令奖励，可以使用它来执行 [`/openguiscreen`](./commands#openguiscreen)、[`/fmvariable`](./commands#fmvariable) 或其他合适的 [FancyMenu 命令](./commands)。

### 如何让按钮变为不可用或“灰掉”？

你可以使用 [加载条件](./conditions) 来控制按钮的激活状态。
在编辑器中右键单击按钮，然后选择 **Control Active State**。
添加一个必须满足的条件，使按钮处于激活状态。若要永久禁用它，可以使用 [**Is Number**](./conditions#is-number-fancymenu_visibility_requirement_is_number) 检查 0 是否等于 1。
这样按钮将使用其“Inactive Background”纹理，并且无法点击。

### 如何移除可滚动界面上的标题和页脚（泥土纹理条）？

在布局编辑器中，打开 **Layout Properties -> Header/Footer Customizations**。将纹理设置为透明。某些模组界面上可能无法使用此选项。

### 我无法创建“当前界面”的布局。按钮是灰色的。

你需要先通过 **菜单栏 -> Customization -> Current Screen Customizations -> Enabled** 启用该界面的自定义。

### 我在编辑器中打开一个界面时，无法自定义其中任何元素。结果只显示一个空白界面。

这可能意味着你创建的是 [Universal Layout](./universal-layouts)，而不是“当前界面”的布局。

也可能是因为这是一个 [可滚动界面](./customizing-scrollable-screens)，FancyMenu 默认无法自定义它。

第三种可能是，这个界面来自某个以非原版方式添加元素的模组，这会导致 FancyMenu 无法自定义这些元素。

### 我的 Text 元素上有奇怪的灰色方块。

这些半透明方块是 [Text 元素](./elements#text) 的滚动抓手，不是渲染错误。

如果你不想让这些方块可见，可以右键单击该元素并完全禁用滚动；或者如果你仍希望该元素可滚动，也可以在同一个右键菜单中将抓手纹理设置为完全透明。

### 如何在菜单中显示最新的 Minecraft 更新日志？

有一个很棒的 [GitHub 项目](https://github.com/ClaytonTDM/minecraft-changelogs-markdown)，可以把 Minecraft 的更新日志转换为 FancyMenu 兼容的 Markdown，这样你就能在菜单中显示最新的 MC 更新日志！它会每天更新以获取新的更新日志。

要在 [Text 元素](./elements#text) 中显示它，请将 **Source Mode** 设置为 **Resource**，并将其资源来源设置为 **Web**。使用 `https://clay.is-a.dev/minecraft-changelogs-markdown/{"placeholder":"mcversion"}/fancymenu.md`。

### 让任意元素拉伸到屏幕大小的最简单方法是什么？

大多数元素在其右键菜单中都有一个选项，可以让它们水平和垂直拉伸。启用后，它们会始终拉伸到屏幕的全宽和/或全高。水平和垂直拉伸可以独立切换。

### 当按钮或滑块位于 Text 元素前后时，我无法点击它们或与之交互。

这是因为 Text 元素默认可交互（这样才能拖动滚动抓手或点击 Markdown 超链接），因此它们会消耗鼠标点击和滚动事件。最好的办法是不要把按钮放在 Text 元素前面或后面；但如果实在无法避免，你可以通过**右键单击**该 Text 元素，然后将 **Interactable** 设置为 **Disabled**，使其不可交互。请注意，这会让 Text 元素变成静态、不可交互的文本，因此你将无法再滚动它或点击超链接。

### 如何让按钮和滑块在使用方向键和 Tab 键浏览界面时不再被选中/聚焦？

要让按钮和滑块无法被键盘导航，你需要**右键单击**它并将 **Navigable** 设置为 **Disabled**。按钮/滑块仍然可以点击，但你将无法再通过方向键/Tab 导航聚焦它。

如果你想在聊天界面中添加按钮/滑块，这也很有用，这样你仍然可以用方向键向上查看更早的消息，而不会意外选中界面中的按钮/滑块。

### FancyMenu 的某个右键菜单缺少一个本应存在的选项。

FancyMenu 的右键菜单（也就是你在某处右键单击，或与菜单栏交互时弹出的菜单）是**可滚动**的。这意味着当鼠标指针悬停在菜单上时，你可以使用滚轮上下滚动，从而看到更多之前不可见的选项。

### 我无法自定义标题界面，离开编辑器后它总是显示原版界面。

另一个模组替换了原始的 `title_screen`。请在该模组的设置中禁用其自定义标题界面。如果它没有这样的选项，FancyMenu 就无法将布局应用到替换后的界面上。
