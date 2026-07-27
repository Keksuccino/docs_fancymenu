---
title: Modpacks
description: Modpack にレイアウトを含める方法。
---

# Modpack 内の FancyMenu

FancyMenu の設定を modpack に含めるのはとても簡単で、いくつかの手順を行うだけです。

> [!CAUTION]
> FancyMenu の設定にはアクションを実行するものがあります。信頼できるソースからのみインポートしてください。

> [!WARNING]
> このページは、**FancyMenu v3+** で完全に作成された FancyMenu 設定 **のみ** を対象としています。旧式の設定（v2 で作成され、v3 に変換されたもの）を使っている場合、一部の手順が異なることがあります。

# FancyMenu の設定を Modpack に含める

まず行うべき主な作業は、FancyMenu がすべてのデザインを保存するために使用している特別なフォルダを 1 つコピーすることです。

## 見つける必要があるもの

1. **「Minecraft インスタンス」フォルダ:** これは、特定の Minecraft 設定（たとえばメニューを作成したもの）に関するすべてのファイルが保存されている、コンピューター上のメインフォルダです。CurseForge や Modrinth などのランチャーでは、これらを「instance」または「profile」と呼びます。
2. **`config` フォルダ:** Minecraft インスタンスフォルダの中には、通常 `config` という名前のフォルダがあります。多くの mod がここに設定を保存します。
3. **`fancymenu` フォルダ:** その `config` フォルダの中に、FancyMenu は `fancymenu` という自分専用のフォルダを作成します。これが、私たちが必要としている重要なフォルダです！

## インスタンスの保存場所を見つける方法

### CurseForge App を使っている場合

1. CurseForge を開きます。
2. 一覧から Minecraft の profile/instance を見つけて開きます。
3. 三点メニューをクリックします。
4. 「Open Folder」を選びます。これで、その Minecraft インスタンスのメインフォルダが開きます。

<img width="630" alt="Screenshot_1" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/curseforge_launcher_instance.png">

### Modrinth App を使っている場合

1. Modrinth App を開きます。
2. 一覧から Minecraft の profile/instance を見つけて開きます。
3. 三点メニューをクリックします。
4. 「Open Folder」を選びます。これで、その Minecraft インスタンスのメインフォルダが開きます。

<img width="630" alt="Screenshot_1" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/modrinth_launcher_instance.png">

### その他のランチャーの場合

お使いの Minecraft 設定に応じて、同様の「Open Folder」「Open Instance Folder」「View Files」などのオプションを探してください。

## FancyMenu の設定をコピーする

1. MODPACK 側のインスタンスの `config` フォルダ（設定をコピー先にしたい方）へ移動します。
2. その中に `fancymenu` フォルダがある場合は、**削除**します。
3. SOURCE 側のインスタンスの `config` フォルダ（設定の元にしたい方）を開きます。
4. SOURCE 側インスタンスの `config` フォルダ内にある `fancymenu` フォルダを、MODPACK 側インスタンスの `config` フォルダへコピーします。
5. 完了です。これで終わりです。modpack インスタンスを再起動すると、設定が読み込まれるはずです。

> [!CAUTION]
> FancyMenu v2 で作成された古い旧式の設定（v3 に変換されていても）は、レイアウト素材を FancyMenu の `<game-directory>/config/fancymenu/assets/` フォルダの外に保存できた点に注意してください。その場合、modpack にすべての素材も含める必要があります。

# メニューバーとホットキーを無効にする

modpack 内で FancyMenu のメニューバーを表示したままにしたくはないはずなので、無効にしておきましょう。しかし、ホットキーを押せば再び表示できてしまうので、もう少し *強力* な方法を使います。

`<game-directory>/config/fancymenu/options.txt` に移動し、テキストエディタでこのファイルを開きます。

次に、`modpack_mode` を `true` に設定して保存します。
これで、すべてのオーバーレイとホットキーが完全に無効になります。

レイアウトを再編集できるようにするには、この設定を `false` に戻してください。

# ウェルカム画面を無効にする

ほとんどの場合、これは不要です。ただし、まだ Welcome 画面（ドキュメントを読むよう案内する画面）を閉じていない場合は、`<game-directory>/config/fancymenu/options.txt` で `show_welcome_screen` を `false` に設定してください。

この画面は **Open Documentation** ボタンをクリックすると 1 回だけ表示されて自動的に無効化されるため、繰り返しますが、通常は手動で行う必要はありません。

<br>
<img width="630" alt="Screenshot_1" src="https://github.com/user-attachments/assets/4383b39f-f55a-4eb8-8142-34a425474bb3">
