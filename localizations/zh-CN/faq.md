---
title: 常见问题
description: 常见问题解答。
sourceBlobSha: 405be9869106a7871195d6e03828f428cc20b4a1
---
# 常见问题

### 我需要寻求问题帮助。应该提供哪些信息？

为了获得最佳帮助，请尽可能提供完整的上下文信息：
1.  **清晰的问题描述：** 你原本期望发生什么，实际又发生了什么？
2.  **你的 `latest.log` 文件：** 文件位于 `<game-directory>/logs/latest.log`。**除非特别要求，否则不要发送崩溃日志**；`latest.log` 通常包含所需的上下文信息。发布日志时，可以使用 https://gist.github.com 之类的网站。
3.  **你的 Minecraft 版本：**（例如 1.20.1）
4.  **你的模组加载器及版本：**（例如 Forge 47.2.0、Fabric 0.15.7）
5.  **你的 FancyMenu 版本：**（例如 3.5.2）
6.  **问题的截图或视频**也会非常有帮助。

### 如何更改元素的层级（将某个元素移到另一个元素前面或后面）？

*   **自定义元素之间：** 打开 **Window -> Editor Widgets -> Layers**，然后在层级结构中拖动元素。你也可以右键单击元素，并使用 **Move One Layer Up/Down**。请参阅[层与组](./layers-and-groups)。
*   **自定义元素与原版元素之间：** 如果要将所有自定义元素渲染在所有原版元素后面（例如，将背景图片放在默认按钮后面），请**右键单击编辑器背景**，然后启用或禁用 **"Render Custom Elements Behind Vanilla"** 选项。

### 可以从通用按钮模板中排除某些按钮吗？

**不可以。如果模板按钮设置了自定义纹理，这些纹理就会始终与所有受影响的元素共享。你无法排除单个按钮。**

### 如何让按钮在点击时执行某些操作？

使用一个[**操作脚本**](./action-scripts)。
1.  在编辑器中右键单击按钮。
2.  选择 **Edit Action Script**。
3. 点击 **Add Action** 并选择一个操作，例如[**打开界面或自定义 GUI**](./action-scripts#open-screen-or-custom-gui-opengui)、[**加入服务器**](./action-scripts#join-server-joinserver)或[**设置变量值**](./action-scripts#set-variable-value-fm-variable-set_variable)。

### 可以从头创建一个全新的菜单界面吗？

使用[**自定义 GUI**](./custom-guis)。
1.  在菜单栏中，前往 **Customization -> Custom GUIs -> Manage Custom GUIs**。
2.  点击 **"New GUI"**，并为其设置一个唯一标识符。
3.  随后你可以打开这个新的空界面，为其创建布局并添加所需的任意元素。
4. 使用[**打开界面或自定义 GUI**操作](./action-scripts#open-screen-or-custom-gui-opengui)打开自定义 GUI。

### 启用预加载后，游戏加载时间变得很长。

这是预期行为。在初始启动期间预加载高分辨率动画或声音等大型资源，自然会延长游戏的加载时间。

### 我的 FMA 动画占用了太多内存！

当经典的 [FMA 动画](./fma)包含许多高分辨率帧时，可能会消耗大量内存。对于大型或复杂的动画纹理，AFMA 更加合适。请保持经典 FMA 动画较短；如果要完整播放视频，请使用[视频](./video)。

### FancyMenu 能与 OptiFine 一起使用吗？

不能。OptiFine **不兼容**，并且已知会破坏包括 FancyMenu 在内的许多模组。强烈建议使用 Sodium/Embeddium + Iris/Oculus 等现代替代方案。
请参阅 [OptiFine 替代方案](./optifine-alternatives)。

### 我的游戏崩溃了。如何判断是否是模组冲突？

检查模组冲突的最佳方法是**仅使用 FancyMenu 及其依赖项**（Konkrete、Melody）运行游戏。如果不再发生崩溃，可以分小批逐步重新添加其他模组，直到再次发生崩溃，从而找出冲突的模组。

### 我尝试编辑其他模组中的按钮时，该按钮消失了或无法使用。

有些模组以 FancyMenu 无法检测或自定义的方式添加控件。请查看[原版/模组元素](./vanilla-elements)，对于基于列表的界面，请查看[自定义可滚动界面](./customizing-scrollable-screens)。如果控件仍未显示，则添加该控件的模组必须将其公开为受支持的界面控件。

### 可以在服务器上使用 FancyMenu 布局吗？

布局和视觉自定义内容存储在玩家客户端上；服务器无法将其强制应用到未配置的客户端。请将它们作为整合包的一部分进行分发。当你需要使用[服务器命令](./commands)、[FM Data](./fm-data)、[服务器端 NBT 访问](./nbt-data-placeholder#server-side-placeholder)、游戏规则、结构或服务器监听器时，请在服务器上安装 FancyMenu。

### FancyMenu v2（适用于旧版 MC）和 v3 有什么区别？

FancyMenu v3 是一次完整重写，拥有许多新功能、更稳定的架构和更好的性能。V2 已经过时，不再受支持，并且缺少高级占位符和脚本等许多功能。强烈建议在现代 Minecraft 版本（1.18.2+）上使用 v3。加载 v2 布局时，可以自动将其转换为 v3，但可能需要进行一些手动修复。

### 在哪里可以找到预制布局和模板？

FancyMenu 社区会在官方 Keksuccino's Mods Discord 服务器（“Kekscord”）的 [`#layout-templates`](https://discord.com/channels/704163135787106365/1234093433795383316) 频道中分享布局。

### 如何让玩家实体渲染在其他元素后面？

通常无法通过[层](./layers-and-groups)控件强制[玩家实体元素](./elements#player-entity)位于普通 2D 元素后面。玩家实体的渲染器可能会忽略普通 GUI 层级顺序。请围绕这一限制设计布局；如果需要严格的层级顺序，请使用预渲染图片。

### 我的玩家实体只有一条腿！发生了什么？

这是一个视觉故障，可能是与其他修改玩家动画或模型的模组发生冲突所致。请检查玩家实体的姿势设置，确认腿部是否被意外旋转或移动。

### 如何在脚本中的操作之间创建延迟？

使用[**Delay** 或 **Execute Later** 区块](./action-scripts#what-are-statements)实现延迟操作逻辑。对于重复执行的后台逻辑，请使用[调度器](./schedulers)。

### 可以自定义 Create 模组的菜单吗？

不可以。Create 界面的自定义功能已被有意禁用。请参阅[有意禁用自定义功能的界面](./incompatibility-list#screens-where-customization-is-intentionally-disabled)。

### 背景图片和按钮纹理推荐使用什么分辨率？

背景：标准的 1920x1080（1080p）图片是很好的起点，并且对大多数用户来说都能良好缩放。
按钮：大多数原版按钮的尺寸约为 150–200 像素宽、20 像素高。让自定义纹理匹配这一尺寸，有助于保持一致性。

### 是否可以在玩家完成游戏内目标（例如任务）时自动打开菜单或运行命令？
FancyMenu 提供许多[内置游戏事件监听器](./listeners)，但没有适用于所有第三方任务系统的通用监听器。如果任务模组支持命令奖励，可以使用命令运行 [`/openguiscreen`](./commands#openguiscreen)、[`/fmvariable`](./commands#fmvariable) 或其他合适的 [FancyMenu 命令](./commands)。

### 如何让按钮处于非活动状态或“灰掉”？

你可以使用[加载条件](./conditions)控制按钮的活动状态。
在编辑器中右键单击按钮，然后选择 **Control Active State**。
添加一个按钮处于活动状态必须满足的条件。要永久禁用按钮，可以使用[**Is Number**](./conditions#is-number-fancymenu_visibility_requirement_is_number)检查 0 是否等于 1。
此时按钮将使用其“非活动背景”纹理，并且无法点击。

### 如何移除可滚动界面中的页眉和页脚（泥土纹理条）？

在布局编辑器中，打开 **Layout Properties -> Header/Footer Customizations**。将纹理设置为透明。在某些模组界面中，此选项可能不可用。

### 我无法创建“当前界面”的布局。按钮是灰色的。

你需要先通过 **菜单栏 -> Customization -> Current Screen Customizations -> Enabled** 为该界面启用自定义功能。

### 在编辑器中打开界面时，我无法自定义其中的任何元素。界面只是空的。

这可能意味着你创建的是一个[通用布局](./universal-layouts)，而不是**当前界面**的布局。

也可能是一个[可滚动界面](./customizing-scrollable-screens)，FancyMenu 默认无法对其进行自定义。

第三种可能是，这是某个模组以非原版方式添加元素的界面，因此 FancyMenu 无法自定义这些元素。

### 我的文本元素中出现了奇怪的灰色方框。

这些半透明方框是[文本元素](./elements#text)的滚动拖拽条，并非渲染错误。

如果不希望显示这些方框，可以右键单击该元素并完全禁用滚动；如果仍希望元素可滚动，也可以在同一个右键菜单中将拖拽条纹理设置为完全透明的纹理。

### 如何在菜单中显示最新的 Minecraft 更新日志？

有一个很棒的 [GitHub 项目](https://github.com/ClaytonTDM/minecraft-changelogs-markdown)，可以将 Minecraft 的更新日志转换为 FancyMenu 兼容的 Markdown，因此你可以在菜单中显示最新的 MC 更新日志！该项目每天更新，以获取新的更新日志。

要在[文本元素](./elements#text)中显示它，请将 **Source Mode** 设置为 **Resource**，并将其资源来源设置为 **Web**。使用 `https://clay.is-a.dev/minecraft-changelogs-markdown/{"placeholder":"mcversion"}/fancymenu.md`。

### 将任意元素拉伸到屏幕大小的最简单方法是什么？

大多数元素的右键上下文菜单中都有水平和垂直拉伸选项。启用后，元素将始终拉伸至屏幕的完整宽度和/或高度。水平和垂直拉伸可以分别开关。

### 当按钮或滑块位于文本元素前面或后面时，我无法点击或操作它们。

这是因为文本元素默认可交互（这样才能拖动滚动条或点击 Markdown 超链接），所以它们会接收鼠标点击和滚动事件。最好的方法是不要将按钮移到文本元素的前面或后面；但如果无法避免，可以**右键单击文本元素**，然后将 **Interactable** 设置为 **Disabled**，使其不可交互。请注意，这会使文本元素变成静态且不可交互的文本，因此你将无法再滚动文本或点击超链接。

### 如何让按钮和滑块在使用方向键和 Tab 键浏览界面时不再被选中或获得焦点？

要让按钮和滑块无法通过键盘导航，请**右键单击**它，并将 **Navigable** 设置为 **Disabled**。按钮或滑块仍然可以点击，但无法再通过方向键或 Tab 键导航获得焦点。

如果你想在聊天界面中添加按钮或滑块，这也很有用：这样你仍然可以使用向上箭头键浏览较早的消息，而不会意外选中界面中的按钮或滑块。

### FancyMenu 的某个上下文菜单缺少本应存在的选项。

FancyMenu 的上下文菜单（右键单击某处或与菜单栏交互时打开的菜单）是**可滚动的**。这意味着当鼠标光标位于菜单上时，可以使用滚轮上下滚动，从而查看之前未显示的更多选项。

### 我无法自定义标题界面，离开编辑器后它总是显示原版界面。

另一个模组正在替换原版的 `title_screen`。请在该模组的设置中禁用其自定义标题界面。如果它没有此选项，FancyMenu 就无法将布局应用到被替换的界面上。

### 尝试自定义物品栏界面时，我无法自定义物品栏容器。

这是预期行为。FancyMenu 不支持编辑任何类型物品栏界面的实际容器（玩家物品栏、箱子、工作台等），因为添加这些支持会非常困难。

你仍然可以向这些界面添加新元素，只是无法编辑容器本身。

顺便说一句，SpiffyHUD 也无法解决这个问题，因为它用于编辑 HUD（例如物品快捷栏），而不能编辑界面（例如物品栏界面）。
