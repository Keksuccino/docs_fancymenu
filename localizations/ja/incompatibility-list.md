---
title: 互換性リスト
description: FancyMenu によってブロックされる画面と、コミュニティから報告された互換性問題。
sourceBlobSha: f5f938751a166796106f5074dc55137bcd40f203
---
# カスタマイズが意図的に無効化される画面

FancyMenu は、クラッシュや動作不良を防ぐため、特定の mod パッケージパスに一致する画面をブロックします。一致する画面では、カスタマイズ切り替え、オーバーレイ、レイアウトを利用できません。

これらのブロックには、個々の画面を手作業で選んだリストではなく、画面クラスの Java パッケージが使用されます。そのため、1 つのルールが同じ mod や関連パッケージに属する複数の画面に影響する場合があります。

ブロックされる画面グループは次のとおりです。

- Create
- Panoramica
- Alex's Mobs
- Screenshot Viewer
- Twilight Forest
- Supplementaries
- OptiFine：[OptiFine の代替 mod](./optifine-alternatives) を使用してください
- SlimeKnights および Tinkers' Construct
- MidnightDust の mod
- SkinSwapper
- Immersive Engineering
- Dungeonz
- RPG-Hud
- Cobblemon および一部の Cobblemon 関連画面
- Applied Energistics 2
- Xaero's のマップ mod

# コミュニティから報告された互換性問題

以下の項目はコミュニティからの報告であり、FancyMenu 自体によってブロックされている画面ではありません。互換性は、導入している mod パックの FancyMenu、Minecraft、ローダー、mod のバージョンによって変わる場合があります。

* [Animated Loading Screen](https://modrinth.com/mod/animated-loading-screen)（メニューの表示が壊れているように見える）
* [Animated Mojang Logo](https://www.curseforge.com/minecraft/mc-mods/animated-mojang-logo)（レイアウトが読み込まれないことがある。また、Drippy Loading Screen も壊れる）
* [Bedrockify](https://www.curseforge.com/minecraft/mc-mods/bedrockify)（カスタマイズしたいメニューについて、この mod のすべてのメニュー変更を無効にすれば互換性あり）
* [BetterFPS](https://www.curseforge.com/minecraft/mc-mods/betterfps)（この mod のボタンとメニューはカスタマイズできない）
* [Chat Colors](https://www.curseforge.com/minecraft/mc-mods/chat-colours)（起動時にクラッシュする）
* [Chloride](https://modrinth.com/mod/chloride)（この mod を導入すると FPS プレースホルダーが機能しない）
* [Colormatic](https://www.curseforge.com/minecraft/mc-mods/colormatic)（Minecraft の起動時に大きなラグが発生し、FM のオーディオ機能も壊れる）
* [Controllable](https://www.curseforge.com/minecraft/mc-mods/controllable)（FancyMenu でメニューに追加したカスタムボタンは、Controllable の「仮想マウス」機能ではクリックできない）
* [Controlify](https://modrinth.com/mod/controlify)（クラッシュが報告されている。[issue #1144](https://github.com/Keksuccino/FancyMenu/issues/1144) を参照）
* [Crash To Main Menu](https://www.curseforge.com/minecraft/mc-mods/crash-to-main-menu)
* [Custom Loading Screen](https://www.curseforge.com/minecraft/mc-mods/better-loading-screen)
* [Custom Main Menu](https://www.curseforge.com/minecraft/mc-mods/custom-main-menu)
* [Debugify](https://www.curseforge.com/minecraft/mc-mods/debugify)（代わりに [Modern Debugify](https://www.curseforge.com/minecraft/mc-mods/modern-debugify) を使用してください）
* [Dynamic Surroundings](https://www.curseforge.com/minecraft/mc-mods/dynamic-surroundings)（オーディオ要素を壊すことが報告されている）
* [EnhancedVisuals](https://www.curseforge.com/minecraft/mc-mods/enhancedvisuals)（アニメーションと半透明背景の問題が報告されている）
* [Entity Model Features](https://modrinth.com/mod/entity-model-features)（クラッシュが報告されている。[issue #1115](https://github.com/Keksuccino/FancyMenu/issues/1115) を参照）
* [Fossils and Archeology Revival](https://www.curseforge.com/minecraft/mc-mods/fossils)（ゲーム内では動作するが、カスタムメインメニューには対応していない。この機能は設定で無効にできる）
* [Holographic Renderers](https://www.curseforge.com/minecraft/mc-mods/holographic-renderers)（起動時にクラッシュする）
* [Ice and Fire](https://www.curseforge.com/minecraft/mc-mods/ice-and-fire-dragons)（設定でカスタムメインメニューを無効にすれば動作する）
* [Jurassicraft](https://www.curseforge.com/minecraft/mc-mods/jurassicraft)（GUI のカスタマイズを有効にすると起動時にクラッシュする。`<game-directory>/config/fancymenu/customizablemenus.txt` から該当する GUI を削除する）
* [Legacy4J](https://www.curseforge.com/minecraft/mc-mods/legacy-minecraft)（ゲームがクラッシュする）
* [MalisisCore](https://www.curseforge.com/minecraft/mc-mods/malisiscore)（メインメニューのカスタマイズが壊れる）
* [Main Menu Scale Mod](https://www.curseforge.com/minecraft/mc-mods/main-menu-scale)
* [MCA Reborn](https://www.curseforge.com/minecraft/mc-mods/minecraft-comes-alive-reborn)（動作するが、一部のメニューで FM のメニューバーが壊れる、またはカスタマイズできない）
* [Minecraft Comes Alive](https://www.curseforge.com/minecraft/mc-mods/minecraft-comes-alive-mca)（互換性があると報告されているが、この mod のメニューはカスタマイズできない）
* [MineTogether](https://www.curseforge.com/minecraft/mc-mods/creeperhost-minetogether)（GUI スケールが 2 を超えるとレイアウトの問題が報告されている）
* [Mod Menu](https://www.curseforge.com/minecraft/mc-mods/modmenu)（通常は互換性あり。Mods ボタンが重複する、またはカスタマイズできない場合は、**Main Menu -> Mods -> Mod Menu -> Mods Button** を **Adjacent** に設定する）
* [Modern Online Picture Frames](https://www.curseforge.com/minecraft/mc-mods/online-picture-frame)（クラッシュする。[この issue](https://github.com/Keksuccino/FancyMenu/issues/776) を参照）
* [Not Enough Animations](https://www.curseforge.com/minecraft/mc-mods/not-enough-animations)（1.16 以降では互換性があり、1.12 では互換性がないと報告されている）
* [Optiscale](https://www.curseforge.com/minecraft/mc-mods/optiscale)（FancyMenu の UI が壊れ、ボタンをクリックできなくなる）
* [Pack Menu](https://www.curseforge.com/minecraft/mc-mods/packmenu)
* [Panorama Screens](https://modrinth.com/mod/panorama-screens)（メニューカスタマイズシステム同士の競合が報告されている）
* [QuestCraft](https://github.com/QuestCraftPlusPlus/QuestCraft)（ゲームの読み込みに失敗する）
* [RandomPatches](https://www.curseforge.com/minecraft/mc-mods/randompatches-forge)（設定で `patchMinecraftClass = false` にすれば動作する）
* [Remove Reloading Screen](https://www.curseforge.com/minecraft/mc-mods/rrls)（FancyMenu と Drippy Loading Screen を壊すことが報告されている）
* [Replay Mod](https://www.replaymod.com/download/)（`<game-directory>/config/replaymod.json` で `mainMenuButton` を **BIG** に設定すれば動作する）
* [Seamless Loading Screen](https://www.curseforge.com/minecraft/mc-mods/seamless-loading-screen)（ゲームがクラッシュする）
* [Slight Gui Modifications](https://www.curseforge.com/minecraft/mc-mods/slight-gui-modifications)
* [Skin Layers 3D](https://www.curseforge.com/minecraft/mc-mods/skin-layers-3d)（1.16 以降では互換性があり、1.12 では互換性がないと報告されている）
* [Smooth Scrolling Everywhere](https://www.curseforge.com/minecraft/mc-mods/smooth-scrolling-everywhere)
* [Sound Filters](https://www.curseforge.com/minecraft/mc-mods/sound-filters)（導入するとオーディオ拡張機能が動作しない）
* [Sound Physics Remastered](https://www.curseforge.com/minecraft/mc-mods/sound-physics-remastered)（導入するとオーディオ拡張機能が動作しない）
* [Stylish Effects](https://www.curseforge.com/minecraft/mc-mods/stylish-effects)（メインメニューを初めて表示したときにレイアウトの読み込みに失敗する）
* [Supplementaries](https://www.curseforge.com/minecraft/mc-mods/supplementaries)（設定画面をカスタマイズするとランダムにクラッシュする。`<game-directory>/config/fancymenu/customization/` から問題のあるレイアウトを削除する）
* [Terraria Craft](https://www.curseforge.com/minecraft/mc-mods/terraria-craft)
* [The Dalek Mod](https://www.curseforge.com/minecraft/mc-mods/the-dalek-mod)（設定でカスタムメインメニューを無効にすれば動作する）
* [ThonkUtil](https://www.curseforge.com/minecraft/mc-mods/thonkutil)（動作するが、現在はメインメニューに削除できないテキストが追加される）
* [Trade Uses](https://modrinth.com/mod/trade-uses)（村人との取引メニューでクラッシュを引き起こす。「Easy Villagers」も導入している場合のみ発生する可能性がある）
* [VanillaFix](https://www.curseforge.com/minecraft/mc-mods/vanillafix)（使用できるが、VanillaFix のクラッシュ画面に関する問題が一部のユーザーから報告されている）
* [FireplaceMode](https://www.curseforge.com/minecraft/mc-mods/fireplacemode)（この mod を導入すると、一時停止画面のカスタマイズがリセットされることがある）
* [Respackopts](https://www.curseforge.com/minecraft/mc-mods/respackopts)（動作するが、リソースパック画面のカスタマイズを無効にした場合のみ）
* [Bind Pizzeria](https://modrinth.com/mod/jjpizza)（FancyMenu のコンテキストメニューでテキストの描画が壊れる）
* [EnhancedTooltips](https://www.curseforge.com/minecraft/mc-mods/enhancedtooltips)（FancyMenu のツールチップが壊れる）
* [Skin Shuffle](https://modrinth.com/mod/skinshuffle)（この mod がメニューに追加するプレイヤーエンティティは、FancyMenu ではカスタマイズできない）
* [Wakes](https://modrinth.com/mod/wakes)（`IncompatibleClassChangeError` により、起動時にゲームがクラッシュする。`AbstractSliderButton.getSprite()` の final メソッドをオーバーライドしようとするが、これは Wakes が可視性を変更しているためにのみ final になっている。詳細は GitHub の issue を参照：[Goby56/wakes #215](https://github.com/Goby56/wakes/issues/215)、[Keksuccino/FancyMenu #1733](https://github.com/Keksuccino/FancyMenu/issues/1733)）
* [Essential](https://www.curseforge.com/minecraft/mc-mods/essential-mod)（詳細は[このページ](/essential)を確認）
