---
title: Modpack
description: Modpackにレイアウトを含める方法。
sourceBlobSha: c19df01d8e726bbff6c9d1d147287ada5d1773eb
---

# ModpackでFancyMenuを使う

ModpackにFancyMenuの設定を含めるのはとても簡単で、いくつかの手順を行うだけです。

> [!CAUTION]
> FancyMenuの設定にはアクションを実行するものがあります。信頼できる提供元の設定のみインポートしてください。

> [!WARNING]
> このページは、**FancyMenu v3以降**で完全に作成されたFancyMenuの設定のみを対象としています。そのため、旧形式の設定（v2で作成し、v3に変換したもの）を使用している場合は、一部の手順が異なることがあります。

# Modpackに設定を取り込む

設定を作成したインスタンスからModpackのインスタンスへ移す最も簡単な方法は、[プロファイル](/profiles)を使うことです。

1. 設定を作成したインスタンスで、**メニューバー -> カスタマイズ -> プロファイル**を開き、設定を選択して、`.fmp`ファイルとして[エクスポート](/profiles#exporting)します。
2. Modpackのインスタンスでプロファイルウィンドウを開き、`.fmp`ファイルを[インポート](/profiles#importing)します。たとえば、ファイルをウィンドウにドラッグしてインポートできます。
3. インポートしたプロファイルを選択し、**プロファイルを読み込む**をクリックします。

Modpackのインスタンスに元からあったFancyMenuの設定が失われることはありません。独立したプロファイルとして残るので、いつでも元に戻せます。

# 設定をModpackに同梱する

読み込んだプロファイルの内容は`<game-directory>/config/fancymenu/`にあるため、ほかのModの設定と同様に、Modpackの`config`フォルダーに含まれます。

そのほかのインスタンスのプロファイルは、`<game-directory>/config/fancymenu/profiles/`に保存されています。Modpackをエクスポートする前に、プレイヤーに配布しないプロファイルを削除するか、Modpackのエクスポートに`profiles`フォルダーを含めないようにしてください。

> [!CAUTION]
> FancyMenu v2で作成された古い形式の設定（v3に変換したものも含む）では、FancyMenuの`<game-directory>/config/fancymenu/assets/`フォルダー以外にレイアウト用アセットを保存できました。プロファイルに含まれるのはFancyMenuの設定フォルダーだけです。そのため、このような場合は、すべてのアセットもModpackに含めてください。

## エクスポート前にチェックボックスをリセットする

[チェックボックス要素](/elements#checkbox)は、`config/fancymenu/checkbox_states.json`にチェック状態を記録します。そのため、テスト中にクリックしたチェックボックスは、プレイヤー側でもチェック済みになります。

プレイヤーが初期状態から始められるようにするには、ゲームを終了し、Modpackまたはプロファイルをエクスポートする前に`checkbox_states.json`を削除してください。このファイルがなければ、すべてのチェックボックスが未チェックの状態で始まります。[変数](/variables)を使用するチェックボックスは、変数に状態が保存されます。

テスト中にアクションで変更したもの（たとえば[動画要素](/video)の音量）についても同様です。該当するファイルについては、[データの保存場所](/data-storage-locations#your-setup)を参照してください。

## インスタンスフォルダーの場所

インスタンスフォルダーとは、特定のMinecraft環境のすべてのファイルが保存されている、コンピューター上のメインフォルダーです。CurseForgeやModrinthなどのランチャーでは、これを「インスタンス」または「プロファイル」と呼びます（FancyMenuのプロファイルとは異なります）。

### CurseForge Appを使用している場合

1. CurseForgeを開きます。
2. 一覧からMinecraftのプロファイル／インスタンスを探して開きます。
3. 3つの点のアイコンをクリックします。
4. 「フォルダーを開く」を選択します。Minecraftインスタンスのメインフォルダーが開きます。

<img width="630" alt="Screenshot_1" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/curseforge_launcher_instance.png">

### Modrinth Appを使用している場合

1. Modrinth Appを開きます。
2. 一覧からMinecraftのプロファイル／インスタンスを探して開きます。
3. 3つの点のアイコンをクリックします。
4. 「フォルダーを開く」を選択します。Minecraftインスタンスのメインフォルダーが開きます。

<img width="630" alt="Screenshot_1" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/modrinth_launcher_instance.png">

### その他のランチャーの場合

使用しているMinecraft環境で、「フォルダーを開く」「インスタンスフォルダーを開く」「ファイルを表示」などの項目を探してください。

# メニューバーとホットキーを無効にする

ModpackでFancyMenuのメニューバーを表示したくない場合は、無効にしておきましょう。ただし、ホットキーを押せば再び表示できてしまいます。そこで、もう少し*強力な*方法を使います。

`<game-directory>/config/fancymenu/options.txt`を開き、テキストエディターで編集します。

`modpack_mode`を`true`に設定して、ファイルを保存します。
これにより、すべてのオーバーレイとホットキーが完全に無効になります。

再びレイアウトを編集できるようにするには、設定を`false`に戻してください。

# ウェルカム画面を無効にする

ほとんどの場合、この操作は不要です。ただし、まだウェルカム画面（ドキュメントを読むよう案内する画面）を閉じていない場合は、`<game-directory>/config/fancymenu/options.txt`の`show_welcome_screen`を`false`に設定してください。

この画面は一度だけ表示され、**ドキュメントを開く**ボタンをクリックすると自動的に無効になります。そのため、ほとんどの場合、手動で設定する必要はありません。

<br>
<img width="630" alt="Screenshot_1" src="https://github.com/user-attachments/assets/4383b39f-f55a-4eb8-8142-34a425474bb3">
