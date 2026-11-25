---
title: 玩家实体
description: 使用“玩家实体”元素在菜单中显示玩家，包括其皮肤、名称、姿势、盔甲等。
sourceBlobSha: b8f8d4340ca3a87e1c55c86f95f36786ab840644
---

# 玩家实体

“玩家实体”元素可以在 3D 场景中显示玩家，就像标题屏幕按钮旁边的玩家角色一样。它可以复制当前玩家、显示其他玩家，也可以显示一个拥有自己皮肤、披风和名称的自定义角色。

<img width="800" alt="五个玩家实体：一个拥有皮肤和披风的真实玩家、一个穿着附魔钻石盔甲并拿着剑和盾牌的玩家、一个蹲着的玩家、一个挥手的玩家和一个幼年玩家" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/player_entities_showcase.png?raw=true">

> [!IMPORTANT]
> 在 Minecraft 1.20.1 及更高版本中，玩家实体需要安装模组 Fancy Entity Renderer（[CurseForge](https://www.curseforge.com/minecraft/mc-mods/fancy-entity-renderer)、[Modrinth](https://modrinth.com/mod/fancy-entity-renderer)）。没有该模组时，玩家实体会显示为红色方框。如果目前还没有适用于你所用 Minecraft 版本的构建版本，则无法在该版本中显示玩家实体。

# 添加玩家实体

右键单击编辑器背景，然后点击 **新建元素 -> 玩家实体**。拖动控制点即可调整元素大小。玩家的大小会随元素的高度变化。

以下所有设置都可以在元素的右键菜单中找到。

# 显示谁

- **复制客户端玩家**会显示当前玩家及其名称、皮肤和披风。启用此选项后，名称、皮肤和披风设置将被锁定。
- **玩家名称**可以是任意名称，不必属于真实玩家。此设置支持[占位符](/placeholders)。
- **显示玩家名称**会在头部上方显示名称标签。关闭**名称标签旋转**后，名称标签不会随玩家转动。

## 皮肤和披风

- **自动皮肤**和**自动披风**会加载与**玩家名称**对应的玩家皮肤和披风。此功能需要联网。
- **皮肤纹理**和**披风纹理**使用你自己的皮肤和披风文件，例如来自[资源](/resources)的皮肤。皮肤使用 Minecraft 的标准皮肤文件。
- **细手臂皮肤**适用于手臂较细的皮肤，例如 Alex。**自动皮肤**和**复制客户端玩家**会自动识别。

# 姿势和动作

<img width="800" alt="两个玩家实体会随着鼠标指针移动而注视它：左边的只转动头部，右边的头部和身体都会转动" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/player_entities_follow_mouse.gif?raw=true">

- **头部跟随鼠标**和**身体跟随鼠标**会让玩家注视鼠标指针。新建的玩家实体默认启用这两个选项。
- **姿势**用于选择身体姿势：**站立**、**蹲下**、**睡觉**、**游泳**、**死亡**或**旋转攻击**。
- **身体动作**会为姿势添加动画。

## 实体姿势

**实体姿势**会打开一个窗口，可设置**头部**、**身体**、**左臂**、**右臂**、**左腿**和**右腿**在 X、Y、Z 轴上的旋转角度，范围为 `-180` 到 `180`。

<img width="800" alt="实体姿势窗口，包含用于调整玩家头部和身体旋转角度的滑块" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/player_entities_pose_window.png?raw=true">

滑块旁的**高级模式**可以将其转换为支持[占位符](/placeholders)的文本值。输入[变量](/variables)，例如 `$$arm_angle`，然后使用[调度器](/schedulers)更改该变量，即可为玩家添加动画。

# 盔甲、物品及其他

- **盔甲和工具**可以为玩家装备物品：**头部盔甲**、**胸部盔甲**、**腿部盔甲**、**脚部盔甲**、**左手工具**和**右手工具**。请将其设为物品 ID，例如 `minecraft:diamond_sword`。物品 ID 支持占位符。启用**附魔头部盔甲**及其他附魔开关后，会显示附魔光效。
- **幼年状态**会将玩家缩小，变成幼年体型。
- **鹦鹉**会让鹦鹉停在右肩上；启用**鹦鹉在左肩**后，鹦鹉会停在左肩上。

# 注意事项

- 玩家实体无法旋转、倾斜、淡化或设置为半透明。
- 如果只需要显示玩家的头部，请参阅[玩家头颅](/player-heads)。
- 在 Minecraft 1.19.2 中，玩家实体不需要 Fancy Entity Renderer，但可用设置较少：只有**蹲下**选项，而没有**名称标签旋转**、**身体动作**或**盔甲和工具**。玩家实体的大小由**实体缩放**设置控制（默认值为 `30`，设为 `60` 时大小会变为两倍），而非由元素大小控制。
