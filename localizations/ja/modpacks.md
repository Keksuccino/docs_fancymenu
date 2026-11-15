---
title: Modpack
description: Modpackにレイアウトを含める方法。
sourceBlobSha: deb3c58e9536e0fe085820a2b9e463f5faaa7819
---

# ModpackでFancyMenuを使用する

ModpackにFancyMenuの設定を含めるのはとても簡単で、いくつかの手順を行うだけです。

> [!CAUTION]
> FancyMenuの設定ではアクションを実行できます。信頼できるソースからのものだけをインポートしてください。

> [!WARNING]
> このページは、**FancyMenu v3以降**で完全に作成されたFancyMenuの設定**のみ**を対象としています。そのため、レガシー設定（v2で作成してv3に変換したもの）を使用している場合は、一部の手順が異なる可能性があります。

# 設定をModpackに取り込む

設定を作成したインスタンスからModpackのインスタンスへ設定を移動する最も簡単な方法は、[プロファイル](./profiles)を使用することです。

1. 設定があるインスタンスで、**メニューバー -> カスタマイズ -> プロファイル**を開き、設定を選択して、`.fmp`ファイルとして[エクスポート](./profiles#exporting)します。
2. Modpackのインスタンスでプロファイルウィンドウを開き、`.fmp`ファイルを[インポート](./profiles#importing)します。たとえば、ファイルをウィンドウにドラッグ＆ドロップします。
3. インポートしたプロファイルを選択し、**プロファイルを読み込む**をクリックします。

Modpackのインスタンスに以前からあったFancyMenuの設定が失われることはありません。独自のプロファイルとして引き続き利用できるため、いつでも元に戻せます。

# Modpackに設定を含める

読み込まれたプロファイルの内容は`<game-directory>/config/fancymenu/`にあるため、他のModの設定と同様に、Modpackの`config`フォルダーに含まれます。

インスタンスのその他のプロファイルは`<game-directory>/config/fancymenu/profiles/`に保存されます。Modpackをエクスポートする前に、プレイヤーに提供したくないプロファイルを削除するか、Modpackのエクスポート対象から`profiles`フォルダーを除外してください。

> [!CAUTION]
> FancyMenu v2で作成された古いレガシー設定（v3に変換したものも含む）では、レイアウトのアセットをFancyMenuの`<game-directory>/config/fancymenu/assets/`フォルダーの外部に保存できました。プロファイルに含まれるのはFancyMenuのconfigフォルダーだけなので、その場合はすべてのアセットもModpackに含める必要があります。

## インスタンスフォルダーの確認方法

インスタンスフォルダーとは、特定のMinecraft設定に関するすべてのファイルが保存されている、コンピューター上のメインフォルダーです。CurseForgeやModrinthなどのランチャーでは、これらを「インスタンス」または「プロファイル」と呼びます（FancyMenuのプロファイルと混同しないでください）。

### CurseForge Appを使用している場合

1. CurseForgeを開きます。
2. リストからMinecraftのプロファイル／インスタンスを見つけて開きます。
3. 3つの点をクリックします。
4. 「フォルダーを開く」を選択します。これで、そのMinecraftインスタンスのメインフォルダーが開きます。

<img width="630" alt="Screenshot_1" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/curseforge_launcher_instance.png">

### Modrinth Appを使用している場合

1. Modrinth Appを開きます。
2. リストからMinecraftのプロファイル／インスタンスを見つけて開きます。
3. 3つの点をクリックします。
4. 「フォルダーを開く」を選択します。これで、そのMinecraftインスタンスのメインフォルダーが開きます。

<img width="630" alt="Screenshot_1" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/modrinth_launcher_instance.png">

### その他のランチャーの場合

使用しているMinecraft設定に応じて、「フォルダーを開く」、「インスタンスフォルダーを開く」、「ファイルを表示」などの同様の項目を探してください。

# メニューバーとホットキーを無効にする

ModpackでFancyMenuのメニューバーを表示したままにしたくはないはずなので、無効にしましょう。ただし、ホットキーを押せば再び表示できてしまうため、ここではもう少し*徹底的な*方法を使います。

`<game-directory>/config/fancymenu/options.txt`に移動し、テキストエディターでファイルを開きます。

次に、`modpack_mode`を`true`に設定してファイルを保存します。
これにより、すべてのオーバーレイとホットキーが完全に無効になります。

再びレイアウトを編集できるようにするには、設定項目を`false`に戻してください。

# ウェルカム画面を無効にする

ほとんどの場合、この操作は必要ありません。ただし、まだウェルカム画面（ドキュメントを読むよう案内する画面）を閉じていない場合は、`<game-directory>/config/fancymenu/options.txt`で`show_welcome_screen`を`false`に設定してください。

この画面は一度しか表示されず、**ドキュメントを開く**ボタンをクリックすると自動的に無効になります。そのため、ほとんどの場合は手動で設定する必要はありません。

<br>
<img width="630" alt="Screenshot_1" src="https://github.com/user-attachments/assets/4383b39f-f55a-4eb8-8142-34a425474bb3">
