---
title: カスタムGUI
description: 新しいGUI画面をゲームに追加する方法。
---

# カスタムGUI

FancyMenuでは既存のGUI画面をカスタマイズできますが、まったく新しい画面を追加して要素を配置することもできます。

# 新しい画面の追加

新しい画面を追加するには、**Customization -> Custom GUIs -> Manage Custom GUIs** に移動します。

![custom_gui_1](https://github.com/Keksuccino/FancyMenu/assets/35544624/23e704ee-ccb5-434d-b75f-f4418399d9b7)

次のメニューで、**New GUI** をクリックします。

![custom_gui_2](https://github.com/Keksuccino/FancyMenu/assets/35544624/035454e8-b089-4b9a-9092-89a193c0eacd)

ここで新しいGUIに一意の識別子を付ける必要があります。また、基本的な画面動作のほかの項目もカスタマイズできます。
設定が終わったら、**Done** を押します。

![custom_gui_3](https://github.com/Keksuccino/FancyMenu/assets/35544624/1fbed3f9-9c81-4c73-85c7-d152146c55d8)

これで空の新しいGUIが作成されます。開くには、**Manage Custom GUIs** メニューでそのGUIを選択し、**Open GUI** をクリックします。

![custom_gui_4](https://github.com/Keksuccino/FancyMenu/assets/35544624/b2e6a4b7-540d-4bf2-9dce-09bfff11ae7e)

これで、まだかなり空のGUI画面が開きます。もっと見やすくするには、他の画面と同じように新しいレイアウトを作成してください。

![custom_gui_5](https://github.com/Keksuccino/FancyMenu/assets/35544624/e7e06a5f-46b3-48f1-9ad9-96a7565c97a9)

# アクションでGUIを開く

最後に、通常のユーザーがあなたのGUIにアクセスできるようにします。最も簡単な方法は、ボタン、スライダー、またはティッカーに **Open Screen or Custom GUI** アクションを使うことです。

![custom_gui_6](https://github.com/Keksuccino/FancyMenu/assets/35544624/b5cc6518-3fc4-4715-96d4-44b65ab7831d)

# コマンドでGUIを開く

カスタムGUIは、[ゲーム内コマンド](./commands#openguiscreen) からも開けます。
これを使えば、他のユーザーのGUIをリモートで開くこともできます！

# ポップアップモード

FancyMenu v3.8.0 以降、カスタムGUIでは "Popup Mode" がサポートされ、別の画面の上にポップアップが開いたように表示できます（カスタムGUIを開いた直前の画面の上に表示されます）。この設定は、各カスタムGUIごとに個別に設定で切り替えられます。

また、FancyMenu 3.9.0 では、ワールド内でカスタムGUIを表示しているときの画面背景オーバーレイを切り替えるオプションも追加されました。ゲームプレイの上に開いたカスタムGUIの背後にあるぼかしや暗い色のオーバーレイを無効化したい場合、または維持したい場合に使用してください。
