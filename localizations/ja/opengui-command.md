---
title: コマンドでGUIを開く
description: コマンドを使ってバニラおよびカスタムGUIを開く方法。
sourceBlobSha: 9d0c8fbc3fa1d1cb15dc19e94f1f0fc1ba37ae05
---

# コマンドでGUIを開く

`/openguiscreen` コマンドを使うと、バニラ、MOD、および[カスタムGUI](/custom-guis)を開けます。サーバーと対象プレイヤーのクライアントにFancyMenuがインストールされている場合は、ほかのプレイヤーを対象にできます。

GUIを開くには、`/openguiscreen <screen_identifier> [<target_players>]` を使用します。

`<screen_identifier>` は、カスタムGUIまたはバニラ／MOD画面の識別子に置き換えます。識別子は大文字と小文字を区別するため、正確に指定してください。

識別子を確認するには、対象の画面を開き、**CTRL + ALT + D** でデバッグオーバーレイを有効にします。1行目に表示される識別子を選択するとコピーできます。[画面識別子](/screen-identifiers)も参照してください。

![copy_identifier](https://github.com/Keksuccino/FancyMenu/assets/35544624/dd6c53d9-d2bd-4810-be03-3741e326bd5a)

自分自身にGUIを開く場合は `[<target_players>]` を省略します。1人以上のプレイヤーに開く場合は、プレイヤー名や `@a` などのセレクターを指定します。対象を指定するには、自分自身を指定する場合でも権限レベル2（ゲームマスター／OPレベル2）が必要です。また、対象となる各プレイヤーのクライアントにFancyMenuがインストールされている必要があります。

すべてのMOD画面を直接開けるわけではありません。対象の画面がサポートされていない場合、FancyMenuはエラーを表示します。ローカルレイアウトでは、通常その画面を開くウィジェットに[**バニラ／MODボタンを模倣**](/action-scripts#mimic-vanillamod-button)を使用してください。

# コマンドでGUIを閉じる

必要になることはまれですが、`/closeguiscreen [<target_players>]` を実行すると現在の画面を閉じられます。対象を省略すると自分の画面が閉じます。対象を指定するには権限レベル2が必要です。
