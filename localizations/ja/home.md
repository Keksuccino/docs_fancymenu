---
title: 始め方
description: FancyMenu の世界へようこそ！ここから、美しい体験の始まりです！
---

# 開発者向け

FancyMenu 用のアドオンを作りたい方や、自分の MOD に FancyMenu を組み込みたい方は、[開発者向けドキュメント](https://github.com/Keksuccino/FancyMenu-Dev-Docs/wiki)をご覧ください。

# 始め方

FancyMenu を初めて使うと少し圧倒されるかもしれませんが、心配はいりません。実際には、触っていくうちにそのほとんどがすぐに分かるようになります！

> このページは FancyMenu に慣れるためのもので、**最初の一歩**を手助けするためのものだという点を **覚えておいてください**。
FancyMenu の機能についてさらに詳しく知りたい場合は、ドキュメントの残りのページもぜひ確認してください！
{.is-info}

# メニューバー

ゲームを起動して最初に目に入るもののひとつが、各メニュー上部にある **メニューバー** です。

**メニューバー** は、**レイアウトの作成**によるメニューの**カスタマイズ**、**ウィンドウタイトルとアイコンの変更**など、FancyMenu のほぼすべての機能への入口です。

> もし誤っていくつかキーを押して **メニューバーが消えてしまった** 場合は、**CTRL + ALT + C** を押すと元に戻せます。
{.is-warning}

<img width="650" alt="menu_bar" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/menu_bar.png?raw=true">

# 最初のレイアウト

Minecraft のメニューをカスタマイズしたいはずなので、ここで **レイアウト** について少し説明しましょう！

レイアウトはメニューのためのカスタマイズ用レイヤーのようなもので、新しい要素を追加したり、既存の要素を編集したりできます。

**特定のメニュー** 用に新しいレイアウトを作成するには:
1. レイアウトを作成したいメニューを開きます（たとえばタイトル画面）
2. **メニューバー** の **Customization** タブを開きます

カスタマイズ機能はデフォルトではすべてのメニューで無効になっているため、カスタマイズしたい各メニューごとに有効化する必要があります。まずは **"Current Screen Customization: Disabled"** をクリックして、トグルを **Enabled** に切り替えましょう。

<img width="475" alt="toggle_customizations" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/toggle_customizations.png?raw=true">

そのあと、**Layouts -> New -> For Current Screen** をクリックします。

これで **レイアウトエディター** が開き、レイアウトに要素を追加したり、バニラや MOD の要素（ボタンなど）をカスタマイズしたりできます。

<img width="550" alt="new_layout_current" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/new_layout_current.png?raw=true">

## レイアウトの編集

ほとんどのカスタマイズ項目には、**エディターの背景を右クリック**することでアクセスできます。
そうすると、**メニュー背景** のカスタマイズや、レイアウトへの **要素の追加** など、さまざまなオプションが入ったコンテキストメニューが開きます。

<br>
<img width="350" alt="context_menu" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/context_menu.png?raw=true">

## レイアウトへの要素追加

新しい要素をレイアウトに追加するには、エディターの背景を **右クリック** します。

開いたコンテキストメニューで **New Element** をクリックし、さまざまな要素タイプの中から1つを選びます。

<img width="525" alt="add_element" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/add_element.png?raw=true">

## 要素のカスタマイズ

要素をカスタマイズするには、それを **右クリック** します。すると、その要素タイプで設定できる内容がすべて入ったコンテキストメニューが開きます。

追加した要素だけでなく、バニラの要素もカスタマイズできます（ただし、場合によっては設定項目が少ないこともあります）。

<img width="525" alt="element_customization" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/element_customization.png?raw=true">

> [!IMPORTANT]
> このようなコンテキストメニューの中には、**スクロール可能** なものがあります！

## 要素の配置

FancyMenu のすべての要素は **アンカーポイント** に接続されています。

アンカーポイントは要素の位置を計算するために必要で、正しく使えば要素同士の重なり、画面外へのはみ出し、ウィンドウサイズ変更時の位置ずれを防げます。

これは、要素の位置を計算するための基準点です。

デフォルトでは、要素は **"Center of Screen"** アンカーポイントに接続されています。これはウィンドウサイズに関係なく、画面のちょうど中央を意味します。
たとえば、ある要素が **"Center of Screen"** アンカーに接続されていて、画面の中心から 2 センチ離れているとします。その場合、ウィンドウサイズに関係なく、その要素は **常に** 画面中央から 2 センチの位置にあります。

要素をドラッグしていると、その要素がどのアンカーポイントに接続されているかが表示されます。このとき、デフォルトでは他のすべてのアンカーポイントも表示されます。要素をドラッグ中にアンカーポイントへカーソルを合わせると、その要素のアンカーをそのアンカーポイントに変更できます。

他の要素のアンカーポイントとして、要素そのものを使うこともできます！ 別の要素をドラッグ中にその要素の上へカーソルを合わせるだけで、ドラッグしている要素のアンカーポイントがその要素に変更されます。

**[要素の配置方法についてさらに詳しく学ぶ](/positioning-elements)**

<img width="650" alt="anchor_points" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/anchor_points.png?raw=true">

## 作業の保存

傑作を保存するのを忘れないでください！

閉じる前に変更を保存する必要がある場合、エディター右上に "Unsaved Changes" の表示が出ます。

**Layout -> Save** をクリックして作業を保存しましょう！

<img width="375" alt="save_your_work" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/save_your_work.png?raw=true">

> [!TIP]
> キーボードショートカット **CTRL + S** を使って保存することもできます。

*おめでとうございます！ これで Minecraft のメニューをずっと美しくできます！*
