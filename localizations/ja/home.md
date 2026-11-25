---
title: はじめに
description: FancyMenuを始めるための第一歩。メニューバー、最初のレイアウトを完成させるまでの手順、そして次に進むための情報を紹介します。
sourceBlobSha: 0a9f8343e6964d75860fb6143e9b6fdecb6cf0ea
---

# はじめに

FancyMenuを使うと、タイトル画面やポーズメニュー、ほかのMODのメニューなど、Minecraftのあらゆるメニューを変更できます。背景、ロゴ、ボタン、テキスト、サウンド、アニメーションを追加したり、すでにある要素を移動または非表示にしたり、ボタンに新しい動作を設定したり、まったく新しいメニューを作ったりできます。すべてゲーム内で行え、コードは必要ありません。

<img width="800" alt="FancyMenuで作成したMODパック「Wildwood」のタイトル画面。夕暮れのピクセルアートの谷には小屋、湖、沈む太陽があり、レイヤーはマウスに合わせて動く。金色のロゴ、マウスを乗せると光る木製ボタン、ホタルも見える" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/getting_started_hero.gif?raw=true">

このページでは、基本的な使い方を順を追って説明します。手順を進めながら、このタイトル画面をシンプルにしたものを作ってみましょう。[サンプルの作り方](#how-the-example-is-made)では、完成版に追加されている要素を紹介します。

> [!TIP]
> このタイトル画面を自分のゲームでも使えます。[wildwood_title_screen.fmp](https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/wildwood_title_screen.fmp?raw=true)をダウンロードし、**メニューバー -> カスタマイズ -> プロファイル**から[インポート](/profiles#importing)して[読み込み](/profiles#loading-a-profile)ます。FancyMenuのお試しや学習、MODパックなど、変更の有無を問わず自由に無料で使用できます。クレジット表記は不要です。

# メニューバー

各メニューの上部にあるメニューバーから、FancyMenuのすべての機能を利用できます。

<img width="800" alt="タイトル画面上部のメニューバー。「カスタマイズ」メニューを開いている" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/getting_started_menu_bar.png?raw=true">

- **カスタマイズ**：現在のメニューのレイアウトや、[グローバルカスタマイズ](/global-customizations)、[カスタムGUI](/custom-guis)、[変数](/variables)、[リスナー](/listeners)、[スケジューラー](/schedulers)、[プロファイル](/profiles)、FancyMenuの設定など、セットアップ全体に関する項目です。
- **ツール**：[ダミー画面インスタンス](/dummy-screen-instances)、[AFMAクリエイター](/animations#fma-and-afma)、**ゲームリソースを参照**、**FancyMenuフォルダーを開く**などの便利な機能があります。最後の項目を選ぶと、セットアップのフォルダーが開きます（[データの保存場所](/data-storage-locations)を参照）。
- **ヘルプ**：このドキュメント、Discordサーバー、**バグを報告**、[AI向けにエクスポート](/export-for-ai)があります。
- 右端のドアアイコンをクリックすると、終了方法のないメニューを閉じられます。
- いちばん右の二重矢印をクリックすると、メニューバーを小さなボタンに折りたたんだり、元に戻したりできます。

MODパックのプレイヤーにメニューバーは必要ありません。無効にする方法は[MODパック](/modpacks#disabling-the-menu-bar-and-hotkeys)を参照してください。

## メニューバーのショートカット

これらのショートカットはすべてのメニューで使えますが、レイアウトエディター内とMODパックモード中は使えません。macOSでは、`Ctrl + Alt`の代わりに`Cmd + Option`を使ってください。

| ショートカット | 動作 |
|---|---|
| `Ctrl + Alt + C` | メニューバーの表示／非表示を切り替えます。突然消えてしまった場合は、この操作で再表示できます。 |
| `Ctrl + Alt + R` | **メニューバー -> カスタマイズ -> FancyMenuを再読み込み**と同じように、FancyMenuを再読み込みします。 |
| `Ctrl + Alt + D` | **デバッグオーバーレイ**の表示／非表示を切り替えます。メニューの[識別子](/screen-identifiers)などが表示されます。 |
| `Ctrl + Alt + L` | 最後に編集したレイアウトを開いた状態で、[レイアウトエディター](/layout-editor)を開きます。 |

# 最初のレイアウト

レイアウトには、メニューに加えた変更が保存されます。背景、追加した要素、既存のボタンやテキストに加えた変更などです。1つのメニューに複数のレイアウトを作成し、それぞれを有効または無効にできます。

## レイアウトを作成する

<img width="800" alt="タイトル画面のメニューバーで「カスタマイズ」を開き、「現在の画面のカスタマイズ」を有効にする。再び「カスタマイズ」を開き、「レイアウト」「新規」「現在の画面用」の順にクリックすると、レイアウトエディターが開く" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/getting_started_new_layout.gif?raw=true">

1. タイトル画面など、変更したいメニューを開きます。
2. **メニューバー -> カスタマイズ -> 現在の画面のカスタマイズ**をクリックし、**有効**と表示されるようにします。FancyMenuは、この設定が有効になっているメニューだけを変更します。
3. **メニューバー -> カスタマイズ -> レイアウト -> 新規 -> 現在の画面用**をクリックします。

レイアウトエディターが開きます。プレイヤーから見える状態のメニューが表示されるため、変更をすぐに確認できます。要素の移動、サイズ変更、コピーなど、詳しくは[レイアウトエディター](/layout-editor)を参照してください。

**すべての画面用 [ユニバーサル]**を選ぶと、代わりに[ユニバーサルレイアウト](/universal-layouts)が作成され、すべてのメニューに表示されます。

## 背景を設定する

まず、画像をゲームの`config/fancymenu/assets`フォルダーに入れてください。**メニューバー -> ツール -> FancyMenuフォルダーを開く**を選ぶと、`config/fancymenu`が開きます。

<img width="800" alt="エディターの背景を右クリックし、「メニュー背景」「画像」を開く。「背景を表示」を有効にしてから「画像を選択」をクリックし、「ソースの種類」を「ローカル」に切り替えてwildwoodフォルダーのbackground.pngを選択すると、ボタンの後ろに谷が表示される" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/getting_started_background.gif?raw=true">

1. エディターの背景を右クリックし、**メニュー背景 -> 画像**を開きます。
2. **背景を表示**をクリックし、**有効**と表示されるようにします。
3. **画像を選択**をクリックし、**ソースの種類**を**ローカル**に設定してから、**ローカルのリソースファイルを選択**をクリックします。
4. 画像をクリックして**OK**をクリックします。フォルダーを開くにはダブルクリックします。

背景にはパノラマ、スライドショー、動画、色なども使えます。詳しくは[メニュー背景](/menu-backgrounds)を参照してください。

## ロゴを追加する

<img width="800" alt="Minecraftのロゴとスプラッシュテキストを削除し、「要素」「新規」「画像」から画像要素を追加して、画像ソースにlogo.pngを選択すると、ロゴが正方形に押しつぶされた状態で表示される" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/getting_started_logo_add.gif?raw=true">

1. Minecraftのロゴをクリックして`Delete`キーを押します。黄色いスプラッシュテキストも同様に削除します。
2. エディターのメニューバーで、**要素 -> 新規 -> 画像**をクリックします。
3. 新しい要素を右クリックして**画像ソース**をクリックし、背景画像と同じ手順でロゴを選択します。

削除したバニラ要素は非表示になるだけです。**要素 -> 削除済みのバニラ要素**から元に戻せます。

<img width="800" alt="ロゴの右クリックメニューで「縦横比を復元」をクリックして本来の幅に戻し、Escキーでメニューを閉じ、Wildwoodのロゴをボタンの上にドラッグする" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/getting_started_logo_place.gif?raw=true">

4. もう一度右クリックし、**縦横比を復元**をクリックして、ロゴが押しつぶされた状態を直します。`Esc`キーでメニューを閉じます。
5. ロゴを所定の位置にドラッグします。

ボタン、テキスト、動画、プレイヤーなど、さまざまな要素を追加できます。詳しくは[要素](/elements)を参照してください。

## ボタンを変更する

<img width="800" alt="シングルプレイヤーボタンをクリックし、Ctrlキーを押しながらほかの4つのボタンをクリックして選択する。「ボタンのテクスチャ」「設定」「通常時の背景」から、5つすべてに木のテクスチャを一度に適用する" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/getting_started_buttons_normal.gif?raw=true">

1. 最初のボタンをクリックし、`Ctrl`キー（macOSでは`Cmd`キー）を押しながらほかのボタンをクリックして、すべて選択します。選択中のボタンの1つを右クリックすると、すべてに一括で変更を適用できます。
2. ボタンの1つを右クリックし、**ボタンのテクスチャ -> 設定 -> 通常時の背景**をクリックして、背景画像と同じ手順でテクスチャを選択します。

<img width="800" alt="「ボタンのテクスチャ」「設定」「マウスオーバー時の背景」から光るテクスチャを設定し、「カスタム背景にナインスライスを適用」を有効にして木の端を鮮明に保つ。マルチプレイヤーボタンにマウスを乗せると光る" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/getting_started_buttons_hover.gif?raw=true">

3. マウスをボタンに乗せたときに使うテクスチャを、**マウスオーバー時の背景**にも同じ手順で設定します。
4. **ボタンのテクスチャ -> カスタム背景にナインスライスを適用**をクリックし、**有効**と表示されるようにします。これにより、ボタンの幅にかかわらずテクスチャの端が鮮明に保たれます。詳しくは[ナインスライス](/nine-slicing-and-tiling)を参照してください。

複数の要素を選択して右クリックすると、表示されるのは選択したすべての要素に共通する設定だけです。ボタン以外の要素は選択しないでください。ボタンを1つだけ右クリックすると、ラベル、サウンド、クリック時の動作（[アクションスクリプト](/action-scripts)）、表示条件（[要素の表示](/element-visibility)）など、すべての設定を変更できます。詳しくは[バニラ／MODの要素](/vanilla-elements)を参照してください。

## 保存する

<img width="800" alt="Ctrl + Sを押し、「ファイルを保存」ウィンドウで「保存」をクリックする。エディターを右上のXで閉じると、谷、Wildwoodのロゴ、木製ボタンが設定された完成後のタイトル画面が表示される" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/getting_started_save.gif?raw=true">

1. `Ctrl + S`（macOSでは`Cmd + S`）を押すか、**レイアウト -> 保存**をクリックします。
2. 初回はファイル名を求められます。そのまま使うか、新しい名前を入力して**保存**をクリックします。
3. メニューバー右側のXをクリックして、エディターを閉じます。

メニューにはレイアウトがすぐに反映されます。後から変更するには、**メニューバー -> カスタマイズ -> レイアウト**でレイアウトにマウスを乗せて**レイアウトを編集**をクリックするか、`Ctrl + Alt + L`を押します。

# サンプルの作り方

このページの冒頭にあるタイトル画面には、作成したものに加えて次の要素があります。

- 空、丘、木々の3枚の画像がマウスに合わせて動き、木々が最も大きく動きます。[視差効果](/parallax)を参照してください。
- 丘と木々は、画面いっぱいの大きさの画像要素です。ボタンやテキストの背後に表示するため、エディターの背景を右クリックしたメニューで**バニラ要素の背後にカスタム要素を表示**を有効にしています。
- ホタルは[装飾オーバーレイ](/decoration-overlays#fireflies)です。
- 丘、木々、ロゴのサイズは、プレースホルダーを使った[高度な位置とサイズの設定](/advanced-positioning-sizing)で画面サイズに合わせています。そのため、どのウィンドウサイズでもメニューが適切に表示されます。縦の短い画面ではロゴが小さくなり、ボタンに重ならないようになっています。

レイアウトエディターですべての設定を見るには、[サンプルプロファイル](#getting-started)を読み込んで、そのレイアウトを編集してください。

# 次に読むページ

**見た目を整える**

- [要素](/elements)：メニューに追加できるものすべて。
- [要素の配置](/positioning-elements)：どのウィンドウサイズでも要素の位置を保つ方法。
- [メニュー背景](/menu-backgrounds)、[アニメーション](/animations)、[動画](/video)、[装飾オーバーレイ](/decoration-overlays)、[BGM](/background-music)。

**動作を設定する**

- [アクションスクリプト](/action-scripts)：ボタンなどの要素に設定できる動作。
- [要素の表示](/element-visibility)と[条件](/conditions)：特定の場合だけ要素を表示する方法。
- [プレースホルダー](/placeholders)：プレイヤー名など、テキストにリアルタイムの情報を表示する方法。
- [変数](/variables)、[リスナー](/listeners)、[スケジューラー](/schedulers)：情報を記憶し、ゲームに反応して、タイマーに沿って処理を実行する方法。

**さらに作り込む**

- [カスタムGUI](/custom-guis)：まったく新しいメニュー。
- [ユニバーサルレイアウト](/universal-layouts)：すべてのメニューに適用する変更。
- [グローバルカスタマイズ](/global-customizations)：ウィンドウタイトルなど、ゲーム全体に適用する調整。
- [ロード画面](/loading-screen)と[ゲームイントロ](/game-intro)。

**共有する**

- [MODパック](/modpacks)：セットアップをMODパックに組み込む方法。
- [プロファイル](/profiles)：セットアップの切り替えやエクスポート。

# ヘルプを受ける

- [よくある質問](/faq)では、特によく寄せられる質問に回答しています。
- **メニューバー -> ヘルプ -> Discordに参加**からFancyMenuのDiscordサーバーに参加できます。
- [AI向けにエクスポート](/export-for-ai)を使うと、Discordサーバーのサポートボットなど、AIチャットで使えるテキストにセットアップを変換できます。
- 正しく動作しない場合は、**メニューバー -> ヘルプ -> バグを報告**を選んでください。

# 開発者向け

FancyMenuのアドオンを作成する場合や、MODでFancyMenuを使う場合は、[開発者向けドキュメント](https://github.com/Keksuccino/FancyMenu-Dev-Docs/wiki)を参照してください。
