---
title: 非互換リスト
description: FancyMenu によってブロックされる画面と、コミュニティから報告された非互換性。
---
# 非互換性

# カスタマイズが意図的に無効化される画面

FancyMenu は、クラッシュや不具合を防ぐため、特定の Mod のパッケージパスに一致する画面をブロックします。一致した画面では、カスタマイズ切り替え、オーバーレイ、レイアウトは利用できません。

これらのブロックは、個々の画面を手作業で列挙するのではなく、画面クラスの Java パッケージを基準にしています。そのため、1 つのルールが同じ Mod や関連パッケージの複数の画面に影響する場合があります。

ブロックされる画面グループには次が含まれます:

- Create
- Panoramica
- Alex's Mobs
- Screenshot Viewer
- Twilight Forest
- Supplementaries
- OptiFine; [OptiFine の代替](./optifine-alternatives)を使用してください
- SlimeKnights と Tinkers' Construct
- MidnightDust 系 Mod
- SkinSwapper
- FancyMenu 自身の設定画面; [カスタム GUI](./custom-guis) は対象外です
- Immersive Engineering
- Dungeonz
- RPG-Hud
- Cobblemon および一部の Cobblemon 関連画面
- Applied Energistics 2
- Xaero のマップ系 Mod

# コミュニティから報告された非互換性

以下の項目はコミュニティ報告によるもので、FancyMenu 自身がブロックしている画面ではありません。互換性は、パック内の FancyMenu、Minecraft、ローダー、Mod の各バージョンによって変わることがあります。

* [Animated Loading Screen](https://modrinth.com/mod/animated-loading-screen)（メニューがバグって見えるようになります）
* [Animated Mojang Logo](https://www.curseforge.com/minecraft/mc-mods/animated-mojang-logo)（レイアウトが読み込まれないことがある; Drippy Loading Screen も壊します）
* [Bedrockify](https://www.curseforge.com/minecraft/mc-mods/bedrockify)（この Mod のメニュー改変をすべて無効にすれば互換あり。少なくとも、カスタマイズしたいメニューでは無効にしてください）
* [BetterFPS](https://www.curseforge.com/minecraft/mc-mods/betterfps)（この Mod のボタンやメニューはカスタマイズできません）
* [Chat Colors](https://www.curseforge.com/minecraft/mc-mods/chat-colours)（起動時にクラッシュ）
* [Chloride](https://modrinth.com/mod/chloride)（この Mod が入っていると FPS プレースホルダーが動作しません）
* [Colormatic](https://www.curseforge.com/minecraft/mc-mods/colormatic)（MC 起動時に大きなラグが発生し、FM の音声関連機能を壊します）
* [Controllable](https://www.curseforge.com/minecraft/mc-mods/controllable)（FancyMenu で追加したカスタムボタンは、Controllable の「Virtual Mouse」機能ではクリックできません）
* [Controlify](https://modrinth.com/mod/controlify)（クラッシュ報告あり; [issue #1144](https://github.com/Keksuccino/FancyMenu/issues/1144) を参照）
* [Crash To Main Menu](https://www.curseforge.com/minecraft/mc-mods/crash-to-main-menu)
* [Custom Loading Screen](https://www.curseforge.com/minecraft/mc-mods/better-loading-screen)
* [Custom Main Menu](https://www.curseforge.com/minecraft/mc-mods/custom-main-menu)
* [Debugify](https://www.curseforge.com/minecraft/mc-mods/debugify)（代わりに [Modern Debugify](https://www.curseforge.com/minecraft/mc-mods/modern-debugify) を使用してください）
* [Dynamic Surroundings](https://www.curseforge.com/minecraft/mc-mods/dynamic-surroundings)（Audio 要素が壊れるという報告あり）
* [EnhancedVisuals](https://www.curseforge.com/minecraft/mc-mods/enhancedvisuals)（アニメーションと半透明背景に問題があるという報告あり）
* [Entity Model Features](https://modrinth.com/mod/entity-model-features)（クラッシュ報告あり; [issue #1115](https://github.com/Keksuccino/FancyMenu/issues/1115) を参照）
* [Fossils and Archeology Revival](https://www.curseforge.com/minecraft/mc-mods/fossils)（ゲーム内では動作しますが、カスタムメインメニューはサポートされません。設定で無効化できます）
* [Holographic Renderers](https://www.curseforge.com/minecraft/mc-mods/holographic-renderers)（起動時にクラッシュ）
* [Ice and Fire](https://www.curseforge.com/minecraft/mc-mods/ice-and-fire-dragons)（設定でカスタムメインメニューを無効にすれば動作します）
* [Jurassicraft](https://www.curseforge.com/minecraft/mc-mods/jurassicraft)（GUI に対してカスタマイズを有効にすると起動時にクラッシュします—`<game-directory>/config/fancymenu/customizablemenus.txt` から削除してください）
* [Legacy4J](https://www.curseforge.com/minecraft/mc-mods/legacy-minecraft)（ゲームがクラッシュします）
* [MalisisCore](https://www.curseforge.com/minecraft/mc-mods/malisiscore)（メインメニューのカスタマイズを壊します）
* [Main Menu Scale Mod](https://www.curseforge.com/minecraft/mc-mods/main-menu-scale)
* [MCA Reborn](https://www.curseforge.com/minecraft/mc-mods/minecraft-comes-alive-reborn)（動作しますが、一部のメニューで FM のメニューバーが壊れたり、カスタマイズできなかったりします）
* [Minecraft Comes Alive](https://www.curseforge.com/minecraft/mc-mods/minecraft-comes-alive-mca)（互換ありと報告されていますが、メニューはカスタマイズできません）
* [MineTogether](https://www.curseforge.com/minecraft/mc-mods/creeperhost-minetogether)（GUI スケール 2 を超えるとレイアウト問題が報告されています）
* [Mod Menu](https://www.curseforge.com/minecraft/mc-mods/modmenu)（通常は互換あり; Mods ボタンが重複する、またはカスタマイズできない場合は、**Main Menu -> Mods -> Mod Menu -> Mods Button** を **Adjacent** に設定してください）
* [Modern Online Picture Frames](https://www.curseforge.com/minecraft/mc-mods/online-picture-frame)（クラッシュ—[この issue](https://github.com/Keksuccino/FancyMenu/issues/776) を参照）
* [Not Enough Animations](https://www.curseforge.com/minecraft/mc-mods/not-enough-animations)（1.16 以降では互換あり、1.12 では非互換と報告されています）
* [Optiscale](https://www.curseforge.com/minecraft/mc-mods/optiscale)（FancyMenu の UI を壊します; ボタンをクリックできません）
* [Pack Menu](https://www.curseforge.com/minecraft/mc-mods/packmenu)
* [Panorama Screens](https://modrinth.com/mod/panorama-screens)（メニューのカスタマイズシステム同士で競合が報告されています）
* [QuestCraft](https://github.com/QuestCraftPlusPlus/QuestCraft)（ゲームの読み込みに失敗します）
* [RandomPatches](https://www.curseforge.com/minecraft/mc-mods/randompatches-forge)（設定で `patchMinecraftClass = false` にすれば動作します）
* [Remove Reloading Screen](https://www.curseforge.com/minecraft/mc-mods/rrls)（FancyMenu と Drippy Loading Screen を壊すという報告あり）
* [Replay Mod](https://www.replaymod.com/download/)（`<game-directory>/config/replaymod.json` で `mainMenuButton` を **BIG** に設定すれば動作します）
* [Seamless Loading Screen](https://www.curseforge.com/minecraft/mc-mods/seamless-loading-screen)（ゲームがクラッシュします）
* [Slight Gui Modifications](https://www.curseforge.com/minecraft/mc-mods/slight-gui-modifications)
* [Skin Layers 3D](https://www.curseforge.com/minecraft/mc-mods/skin-layers-3d)（1.16 以降では互換あり、1.12 では非互換と報告されています）
* [Smooth Scrolling Everywhere](https://www.curseforge.com/minecraft/mc-mods/smooth-scrolling-everywhere)
* [Sound Filters](https://www.curseforge.com/minecraft/mc-mods/sound-filters)（これが入っていると音声拡張は動作しません）
* [Sound Physics Remastered](https://www.curseforge.com/minecraft/mc-mods/sound-physics-remastered)（これが入っていると音声拡張は動作しません）
* [Stylish Effects](https://www.curseforge.com/minecraft/mc-mods/stylish-effects)（メインメニューが初めて表示されたときにレイアウトの読み込みに失敗します）
* [Supplementaries](https://www.curseforge.com/minecraft/mc-mods/supplementaries)（設定画面のカスタマイズ時にランダムにクラッシュします。問題のあるレイアウトを `<game-directory>/config/fancymenu/customization/` から削除してください）
* [Terraria Craft](https://www.curseforge.com/minecraft/mc-mods/terraria-craft)
* [The Dalek Mod](https://www.curseforge.com/minecraft/mc-mods/the-dalek-mod)（設定でカスタムメインメニューを無効にすれば動作します）
* [ThonkUtil](https://www.curseforge.com/minecraft/mc-mods/thonkutil)（動作しますが、現在は削除できないテキストがメインメニューに追加されます）
* [Trade Uses](https://modrinth.com/mod/trade-uses)（村人の取引メニューでクラッシュを引き起こします。もしかすると「Easy Villagers」も入っている場合のみかもしれません）
* [VanillaFix](https://www.curseforge.com/minecraft/mc-mods/vanillafix)（使用可能ですが、VanillaFix のクラッシュ画面で問題が出ると報告しているユーザーがいます）
* [FireplaceMode](https://www.curseforge.com/minecraft/mc-mods/fireplacemode)（この Mod が入っていると、Pause 画面のカスタマイズが時々リセットされます）
* [Respackopts](https://www.curseforge.com/minecraft/mc-mods/respackopts)（Resource Pack 画面のカスタマイズを無効にした場合のみ動作します）
* [Bind Pizzeria](https://modrinth.com/mod/jjpizza)（FancyMenu のコンテキストメニューでテキスト描画が壊れます）
* [EnhancedTooltips](https://www.curseforge.com/minecraft/mc-mods/enhancedtooltips)（FancyMenu のツールチップを壊します）
* [Skin Shuffle](https://modrinth.com/mod/skinshuffle)（この Mod がメニューに追加するプレイヤーエンティティは、FancyMenu ではカスタマイズできません）
