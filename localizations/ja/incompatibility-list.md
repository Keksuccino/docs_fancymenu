---
title: 非互換性リスト
description: FancyMenu によってブロックされる画面と、コミュニティから報告された非互換性。
sourceBlobSha: 2f89775eade27d0a90dd3805b5c58d779676bdbd
---
# カスタマイズが意図的に無効化される画面

FancyMenu は、クラッシュや動作不良を防ぐため、特定の Mod パッケージパスに一致する画面をブロックします。一致する画面では、カスタマイズ切り替え、オーバーレイ、レイアウトを利用できません。

これらのブロック設定では、個々の画面を手作業でリストアップするのではなく、画面クラスの Java パッケージを使用します。そのため、1つのルールが同じ Mod または関連パッケージに属する複数の画面に影響する場合があります。

ブロックされる画面グループ：

- Create
- Panoramica
- Alex's Mobs
- Screenshot Viewer
- Twilight Forest
- Supplementaries
- OptiFine。[OptiFine の代替 Mod](/optifine-alternatives)を使用してください。
- SlimeKnights と Tinkers' Construct
- MidnightDust の Mod
- SkinSwapper
- Immersive Engineering
- Dungeonz
- RPG-Hud
- Cobblemon と一部の Cobblemon 関連画面
- Applied Energistics 2
- Xaero's のマップ Mod

# コミュニティから報告された非互換性

以下はコミュニティからの報告であり、FancyMenu 自体がブロックしている画面ではありません。互換性は、Mod パック内の FancyMenu、Minecraft、ローダー、各 Mod のバージョンによって変わる場合があります。

* [Animated Loading Screen](https://modrinth.com/mod/animated-loading-screen)（メニューの表示が壊れているように見える）
* [Animated Mojang Logo](https://www.curseforge.com/minecraft/mc-mods/animated-mojang-logo)（レイアウトが読み込まれない場合がある。また、Drippy Loading Screen も動作しなくなる）
* [Bedrockify](https://www.curseforge.com/minecraft/mc-mods/bedrockify)（この Mod のメニュー変更機能をすべて無効にすれば互換性あり。少なくとも、カスタマイズしたいメニューでは無効にする必要がある）
* [BetterFPS](https://www.curseforge.com/minecraft/mc-mods/betterfps)（この Mod のボタンとメニューはカスタマイズできない）
* [Chat Colors](https://www.curseforge.com/minecraft/mc-mods/chat-colours)（起動時にクラッシュする）
* [Chloride](https://modrinth.com/mod/chloride)（この Mod をインストールすると、FPS のプレースホルダーが動作しない）
* [Colormatic](https://www.curseforge.com/minecraft/mc-mods/colormatic)（Minecraft の起動時に大きなラグが発生し、FM のオーディオ機能も動作しなくなる）
* [Controllable](https://www.curseforge.com/minecraft/mc-mods/controllable)（FancyMenu でメニューに追加したカスタムボタンは、Controllable の「Virtual Mouse」機能ではクリックできない）
* [Controlify](https://modrinth.com/mod/controlify)（クラッシュの報告あり。[issue #1144](https://github.com/Keksuccino/FancyMenu/issues/1144)を参照）
* [Crash To Main Menu](https://www.curseforge.com/minecraft/mc-mods/crash-to-main-menu)
* [Custom Loading Screen](https://www.curseforge.com/minecraft/mc-mods/better-loading-screen)
* [Custom Main Menu](https://www.curseforge.com/minecraft/mc-mods/custom-main-menu)
* [Debugify](https://www.curseforge.com/minecraft/mc-mods/debugify)（代わりに[Modern Debugify](https://www.curseforge.com/minecraft/mc-mods/modern-debugify)を使用してください）
* [Dynamic Surroundings](https://www.curseforge.com/minecraft/mc-mods/dynamic-surroundings)（オーディオ要素が動作しなくなるとの報告あり）
* [EnhancedVisuals](https://www.curseforge.com/minecraft/mc-mods/enhancedvisuals)（アニメーションや半透明の背景に関する問題の報告あり）
* [Entity Model Features](https://modrinth.com/mod/entity-model-features)（クラッシュの報告あり。[issue #1115](https://github.com/Keksuccino/FancyMenu/issues/1115)を参照）
* [Fossils and Archeology Revival](https://www.curseforge.com/minecraft/mc-mods/fossils)（ゲーム内では動作するが、カスタムメインメニューには非対応。設定で無効にできる）
* [Holographic Renderers](https://www.curseforge.com/minecraft/mc-mods/holographic-renderers)（起動時にクラッシュする）
* [Ice and Fire](https://www.curseforge.com/minecraft/mc-mods/ice-and-fire-dragons)（設定でカスタムメインメニューを無効にすれば動作する）
* [Jurassicraft](https://www.curseforge.com/minecraft/mc-mods/jurassicraft)（GUI のカスタマイズを有効にすると起動時にクラッシュする。`<game-directory>/config/fancymenu/customizablemenus.txt`から該当する画面を削除してください）
* [Legacy4J](https://www.curseforge.com/minecraft/mc-mods/legacy-minecraft)（ゲームがクラッシュする）
* [MalisisCore](https://www.curseforge.com/minecraft/mc-mods/malisiscore)（メインメニューのカスタマイズが動作しなくなる）
* [Main Menu Scale Mod](https://www.curseforge.com/minecraft/mc-mods/main-menu-scale)
* [MCA Reborn](https://www.curseforge.com/minecraft/mc-mods/minecraft-comes-alive-reborn)（動作するが、一部のメニューによって FM のメニューバーが壊れる、またはカスタマイズできない）
* [Minecraft Comes Alive](https://www.curseforge.com/minecraft/mc-mods/minecraft-comes-alive-mca)（互換性ありとの報告があるが、この Mod のメニューはカスタマイズできない）
* [MineTogether](https://www.curseforge.com/minecraft/mc-mods/creeperhost-minetogether)（GUI スケールが 2 を超えるとレイアウトに問題が起きるとの報告あり）
* [Mod Menu](https://www.curseforge.com/minecraft/mc-mods/modmenu)（通常は互換性あり。「Mods」ボタンが重複する、またはカスタマイズできない場合は、**Main Menu -> Mods -> Mod Menu -> Mods Button**を**Adjacent**に設定してください）
* [Modern Online Picture Frames](https://www.curseforge.com/minecraft/mc-mods/online-picture-frame)（クラッシュする。[こちらの issue](https://github.com/Keksuccino/FancyMenu/issues/776)を参照）
* [Not Enough Animations](https://www.curseforge.com/minecraft/mc-mods/not-enough-animations)（1.16 以降では互換性あり、1.12 では非互換との報告あり）
* [Optiscale](https://www.curseforge.com/minecraft/mc-mods/optiscale)（FancyMenu の UI が壊れ、ボタンをクリックできなくなる）
* [Pack Menu](https://www.curseforge.com/minecraft/mc-mods/packmenu)
* [Panorama Screens](https://modrinth.com/mod/panorama-screens)（メニューカスタマイズ機能同士が競合するとの報告あり）
* [QuestCraft](https://github.com/QuestCraftPlusPlus/QuestCraft)（ゲームが読み込まれない）
* [RandomPatches](https://www.curseforge.com/minecraft/mc-mods/randompatches-forge)（設定で`patchMinecraftClass = false`にすれば動作する）
* [Remove Reloading Screen](https://www.curseforge.com/minecraft/mc-mods/rrls)（FancyMenu と Drippy Loading Screen が動作しなくなるとの報告あり）
* [Replay Mod](https://www.replaymod.com/download/)（`<game-directory>/config/replaymod.json`で`mainMenuButton`を**BIG**に設定すれば動作する）
* [Seamless Loading Screen](https://www.curseforge.com/minecraft/mc-mods/seamless-loading-screen)（ゲームがクラッシュする）
* [Slight Gui Modifications](https://www.curseforge.com/minecraft/mc-mods/slight-gui-modifications)
* [Skin Layers 3D](https://www.curseforge.com/minecraft/mc-mods/skin-layers-3d)（1.16 以降では互換性あり、1.12 では非互換との報告あり）
* [Smooth Scrolling Everywhere](https://www.curseforge.com/minecraft/mc-mods/smooth-scrolling-everywhere)
* [Sound Filters](https://www.curseforge.com/minecraft/mc-mods/sound-filters)（この Mod をインストールすると、オーディオ拡張機能が動作しない）
* [Sound Physics Remastered](https://www.curseforge.com/minecraft/mc-mods/sound-physics-remastered)（この Mod をインストールすると、オーディオ拡張機能が動作しない）
* [Stylish Effects](https://www.curseforge.com/minecraft/mc-mods/stylish-effects)（メインメニューを最初に表示したとき、レイアウトが読み込まれない）
* [Supplementaries](https://www.curseforge.com/minecraft/mc-mods/supplementaries)（設定画面をカスタマイズするとランダムにクラッシュする。問題のあるレイアウトを`<game-directory>/config/fancymenu/customization/`から削除してください）
* [Terraria Craft](https://www.curseforge.com/minecraft/mc-mods/terraria-craft)
* [The Dalek Mod](https://www.curseforge.com/minecraft/mc-mods/the-dalek-mod)（設定でカスタムメインメニューを無効にすれば動作する）
* [ThonkUtil](https://www.curseforge.com/minecraft/mc-mods/thonkutil)（動作するが、現在メインメニューに削除できないテキストが追加される）
* [Trade Uses](https://modrinth.com/mod/trade-uses)（村人との取引画面でクラッシュする。「Easy Villagers」もインストールされている場合に限る可能性あり）
* [VanillaFix](https://www.curseforge.com/minecraft/mc-mods/vanillafix)（使用可能だが、VanillaFix のクラッシュ画面に問題が起きるとの報告がある）
* [FireplaceMode](https://www.curseforge.com/minecraft/mc-mods/fireplacemode)（この Mod をインストールすると、一時停止画面のカスタマイズがリセットされることがある）
* [Respackopts](https://www.curseforge.com/minecraft/mc-mods/respackopts)（リソースパック画面のカスタマイズを無効にした場合に限り動作する）
* [Bind Pizzeria](https://modrinth.com/mod/jjpizza)（FancyMenu のコンテキストメニューでテキスト描画が壊れる）
* [EnhancedTooltips](https://www.curseforge.com/minecraft/mc-mods/enhancedtooltips)（FancyMenu のツールチップが壊れる）
* [Skin Shuffle](https://modrinth.com/mod/skinshuffle)（この Mod がメニューに追加するプレイヤーエンティティは FancyMenu でカスタマイズできない）
* [Wakes](https://modrinth.com/mod/wakes)（`IncompatibleClassChangeError`によりゲームの起動時にクラッシュする。Wakes が可視性を変更したことで final になっている`AbstractSliderButton.getSprite()`のオーバーライドに失敗する。詳細は GitHub の issue を参照：[Goby56/wakes #215](https://github.com/Goby56/wakes/issues/215)、[Keksuccino/FancyMenu #1733](https://github.com/Keksuccino/FancyMenu/issues/1733)）
* [Essential](https://www.curseforge.com/minecraft/mc-mods/essential)（詳細は[こちらのページ](/essential)を参照）
