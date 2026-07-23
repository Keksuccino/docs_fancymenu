---
title: 常见问题
description: 常见问题解答。
---
# 常见问题

### 我遇到了问题，需要帮助。我应该提供哪些信息？

为了获得最好的帮助，请尽可能提供更多上下文：
1.  **问题的清晰描述：** 你原本期望发生什么，实际又发生了什么？
2.  **你的 `latest.log` 文件：** 位于 `<game-directory>/logs/latest.log`。**不要发送崩溃日志**，除非被明确要求；`latest.log` 通常包含所需的上下文。发布时请使用 https://gist.github.com 等网站。
3.  **你的 Minecraft 版本：**（例如 1.20.1）
4.  **你的模组加载器及其版本：**（例如 Forge 47.2.0、Fabric 0.15.7）
5.  **你的 FancyMenu 版本：**（例如 3.5.2）
6.  **问题的截图或视频** 也会非常有帮助。

### 我如何改变元素的层级（把某个元素移到另一个元素前面或后面）？

*   **自定义 vs. 自定义：** 打开 **Window -> Editor Widgets -> Layers**，然后在层级结构中拖动元素。你也可以右键单击某个元素，并使用 **向上一层/向下一层移动**。参见 [图层和组](./layers-and-groups)。
*   **自定义 vs. 原版：** 如果要让所有自定义元素都渲染在所有原版元素后面（例如把背景图放到默认按钮后面），请**右键单击编辑器背景**并切换选项 **“Render Custom Elements Behind Vanilla”**。

### 我可以从一个通用按钮模板中排除某些按钮吗？

**不可以。如果模板按钮设置了自定义纹理，这些纹理会始终与所有受影响的元素共享。你不能排除单个按钮。**

### 我如何让按钮在点击时执行某些操作？

使用 [**Action Script**](./action-scripts)。
1.  在编辑器中右键单击该按钮。
2.  选择 **Edit Action Script**。
3.  点击 **Add Action**，然后选择一个动作，例如 [**Open Screen or Custom GUI**](./action-scripts#open-screen-or-custom-gui-opengui)、[**Join Server**](./action-scripts#join-server-joinserver) 或 [**Set Variable Value**](./action-scripts#set-variable-value-fm-variable-set_variable)。

### 我可以从头创建一个全新的菜单界面吗？

使用 [**Custom GUI**](./custom-guis)。
1.  在菜单栏中，进入 **Customization -> Custom GUIs -> Manage Custom GUIs**。
2.  点击 **“New GUI”**，并为它指定一个唯一标识符。
3.  然后你可以打开这个新的空白界面并为其创建布局，添加任何你想要的元素。
4. 使用 [**Open Screen or Custom GUI** 动作](./action-scripts#open-screen-or-custom-gui-opengui) 打开该 Custom GUI。

### 启用预加载后，我的游戏加载时间变得很长。

这是预期行为。在初始启动期间预加载高分辨率动画或音效等大型资源，自然会增加游戏的加载时间。

### 我的 FMA 动画占用了太多内存！

当经典 [FMA 动画](./fma)包含许多高分辨率帧时，会消耗大量内存。AFMA 更适合大型或复杂的动画纹理。请将经典 FMA 动画保持简短；完整视频播放请使用 [Video](./video)。

### FancyMenu 能和 OptiFine 一起使用吗？

不能。OptiFine **不兼容**，而且已知会破坏许多模组，包括 FancyMenu。强烈建议使用现代替代方案，例如 Sodium/Embeddium + Iris/Oculus。
参见 [OptiFine 替代方案](./optifine-alternatives)。

### 我的游戏崩溃了。我该如何判断是不是模组冲突？

检查模组冲突的最佳方法是**只带 FancyMenu 及其依赖项（Konkrete、Melody）运行游戏**。如果崩溃不再发生，你可以将其他模组分批重新加回，直到再次发生崩溃，从而找出冲突的模组。

### 当我尝试编辑另一个模组的按钮时，它消失了或无法使用。

这通常意味着那个模组以 FancyMenu 无法交互的非标准方式添加了按钮。这需要由那个模组的开发者在其端修复。FancyMenu 无法自定义它“看不见”的元素。

### 我可以在服务器上使用 FancyMenu 布局吗？

布局和视觉自定义都保存在玩家客户端上；服务器无法强制未配置的客户端使用它们。你可以将它们作为模组包的一部分分发。如果你需要 [服务器命令](./commands)、[FM Data](./fm-data)、[服务端 NBT 访问](./nbt-data-placeholder#server-side-placeholder)、gamerule、结构或服务器监听器，请在服务器上安装 FancyMenu。

### FancyMenu v2（适用于旧版 MC）和 v3 有什么区别？

FancyMenu v3 是一次彻底重写，带来了许多新功能、更稳定的架构以及更好的性能。V2 已过时，不再受支持，并且缺少许多功能，例如高级占位符和脚本。强烈建议在现代 Minecraft 版本（1.18.2+）中使用 v3。加载 v2 布局时可以自动转换为 v3，但可能仍需要一些手动修正。

### 我在哪里可以找到预制布局和模板？

FancyMenu 社区会在 Keksuccino 官方 Mods Discord 服务器（“Kekscord”）的 `#layout-templates` 频道分享布局。

### 如何让 Player Entity 渲染在其他元素后面？

[Player Entity 元素](./elements#player-entity)通常无论层级顺序如何，都会渲染在 2D 元素前面。

### 我的 Player Entity 只有一条腿！怎么回事？

这是一种视觉故障，可能是由于与其他会修改玩家动画或模型的模组冲突导致的。检查 Player Entity 的姿势设置，看看腿是否被意外旋转或移动了。

### 我如何在脚本中的操作之间创建延迟？

使用 [**Delay** 或 **Execute Later** 块](./action-scripts#what-are-statements)来实现延迟动作逻辑。对于重复执行的后台逻辑，请使用 [Schedulers](./schedulers)。

### 我可以自定义 Create 模组的菜单吗？

不可以。Create 的界面已被有意禁用自定义。参见 [已被有意禁用自定义的界面](./incompatibility-list#screens-where-customization-is-intentionally-disabled)。

### 为什么模组 X 的按钮会在编辑器中消失？

这表示该模组以自定义的、非原版方式添加按钮。FancyMenu 无法“看见”或与这些元素交互，因此无法自定义它们。需要由那个模组的开发者更改其添加按钮的方式，才能实现兼容。

### 背景图和按钮纹理推荐使用什么分辨率？

背景图：标准的 1920x1080（1080p）图像是很好的起点，并且对大多数用户来说都能良好缩放。
按钮：大多数原版按钮宽约 150-200 像素、高 20 像素。自定义纹理尽量匹配这个尺寸，有助于保持一致性。

### 有没有办法在玩家完成游戏内目标（例如任务）时自动打开菜单或运行命令？
FancyMenu 内置了许多 [游戏事件监听器](./listeners)，但并没有针对每个第三方任务系统的通用监听器。如果任务模组支持命令奖励，可以使用它来运行 [`/openguiscreen`](./commands#openguiscreen)、[`/fmvariable`](./commands#fmvariable) 或其他合适的 [FancyMenu 命令](./commands)。

### 我如何让按钮变为不可用或“灰掉”的状态？

你可以通过 [加载条件](./conditions)控制按钮的激活状态。
在编辑器中右键单击按钮并选择“Active State”。
添加一个按钮要处于激活状态时必须满足的条件。若要永久禁用它，请使用 [**Is Number**](./conditions#is-number) 检查 0 是否等于 1。
此时按钮将使用其“Inactive Background”纹理，并且不可点击。

### 我如何移除可滚动界面上的页眉和页脚（灰色泥土纹理条）？

在布局编辑器中，右键单击编辑器背景并打开 **Customize Header/Footer**。将纹理设置为透明。某些模组化界面可能没有此选项。

### 我无法创建“用于当前界面”的布局。按钮是灰色的。

你需要先通过 **菜单栏 -> Customization -> Current Screen Customizations -> 将其切换为 Enabled** 来为该界面启用自定义。

### 我在编辑器中打开某个界面时，无法自定义其中任何元素。结果它只是一个空白界面。

这可能表示你创建的是 [Universal Layout](./universal-layouts)，而不是用于**当前界面**的布局。

也可能这是一个 [可滚动界面](./customizing-scrollable-screens)，FancyMenu 默认无法自定义它。

第三种可能是，该界面来自某个以非原版方式添加元素的模组，这会导致 FancyMenu 无法自定义这些元素。

### 我的 Text 元素上有奇怪的灰色方块。

这些半透明方块是 [Text 元素](./elements#text)的滚动抓手，不是渲染错误。

如果你不想看到这些方块，可以右键单击该元素并完全禁用滚动；或者如果你仍希望它可滚动，也可以在同一个右键菜单中把抓手纹理设置为完全透明的纹理。

### 我如何在菜单中显示最新的 Minecraft 更新日志？

有一个很棒的 [GitHub 项目](https://github.com/ClaytonTDM/minecraft-changelogs-markdown)，可以将 Minecraft 的更新日志转换为 FancyMenu 兼容的 Markdown，这样你就可以在菜单中显示最新的 MC 更新日志！它会每天更新以获取新的更新日志。

要在 [Text 元素](./elements#text)中显示它，请将 **Source Mode** 设为 **Resource**，并将其资源源设为 **Web**。使用 `https://clay.is-a.dev/minecraft-changelogs-markdown/{"placeholder":"mcversion"}/fancymenu.md`。

### 将任意元素拉伸到屏幕大小的最简单方法是什么？

大多数元素的右键菜单中都有一个选项，可将其水平和垂直拉伸。启用后，它们会始终拉伸到屏幕的全宽和/或全高。水平和垂直拉伸可以分别切换。

### 当按钮或滑块位于 Text 元素后面或前面时，我无法点击它们或与之交互。

这是因为 Text 元素默认是可交互的（这样才能拖动滚动抓手或点击 Markdown 超链接），因此它们会接收鼠标点击和滚轮事件。最好的办法是尽量不要把按钮放在 Text 元素前后；但如果实在无法避免，你可以**右键单击** Text 元素，然后将 **Interactable** 设为 **Disabled**，使其不再可交互。请注意，这会让 Text 元素变成静态、不可交互的文本，因此你将无法再滚动它或点击其中的超链接。

### 我如何让按钮和滑块在使用方向键和 Tab 键浏览界面时，不再被选中/聚焦？

要让按钮和滑块不可导航，你需要**右键单击**它，并将 **Navigable** 设为 **Disabled**。按钮/滑块仍然可以点击，但你将无法再通过方向键/Tab 导航聚焦它。

如果你想在聊天界面添加按钮/滑块，这也很有用，这样你仍然可以使用向上方向键滚动查看较早的消息，而不会意外选中界面中的按钮/滑块。

### FancyMenu 的某个右键菜单里缺少一个本应存在的选项。

FancyMenu 的右键菜单（即在某处右键单击或与菜单栏交互时打开的菜单）是**可滚动的**。这意味着当鼠标指针悬停在菜单上时，你可以使用滚轮向上或向下滚动，从而看到之前不可见的更多选项。

### 我无法自定义标题界面，离开编辑器后它总是显示原版界面。

另一个模组替换了原始的 `title_screen`。请在该模组的设置中禁用它的自定义标题界面。如果它没有这样的选项，FancyMenu 就无法将布局应用到被替换的界面上。
