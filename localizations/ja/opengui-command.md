---
title: コマンドでGUIを開く
description: コマンドを使って Vanilla およびカスタムGUIを開く方法。
---

# コマンドでGUIを開く

`/openguiscreen` コマンドは、Vanilla、mod、[カスタムGUI](./custom-guis) を開きます。FancyMenu がサーバーとクライアントの両方に導入されている場合、他のプレイヤーを対象にすることもできます。

GUI を開くには、`/openguiscreen <screen_identifier> [<target_players>]` を使用します。

`<screen_identifier>` には、カスタムGUIまたは Vanilla/mod 画面の正確な識別子を、大文字小文字も含めてそのまま指定してください。

識別子を確認するには、対象の画面を開いて **CTRL + ALT + D** でデバッグオーバーレイを有効にします。1行目に表示される識別子を選択するとコピーできます。詳しくは [画面識別子](./screen-identifiers) を参照してください。

![copy_identifier](https://github.com/Keksuccino/FancyMenu/assets/35544624/dd6c53d9-d2bd-4810-be03-3741e326bd5a)

`[<target_players>]` を省略すると自分自身に GUI を開きます。`@a` のようなプレイヤー名やセレクターを使うと、1人または複数のプレイヤーに対して開けます。対象引数を指定するには権限レベル 2（Game Master / OP レベル 2）が必要です。たとえ自分自身を指定する場合でも必要で、対象となる各プレイヤーのクライアントにも FancyMenu が導入されている必要があります。

すべての mod 画面を直接作成できるわけではありません。対象画面が非対応の場合、FancyMenu はエラーを表示します。ローカルレイアウトでは、通常その画面を開くウィジェットに [**Vanilla/Mod ボタンを模倣**](./action-scripts#mimic-vanillamod-button-mimicbutton) を使用してください。

# コマンドでGUIを閉じる

必要になることはまれですが、`/closeguiscreen [<target_players>]` で現在の画面を閉じられます。対象を省略した場合は自分に対して動作します。対象引数を指定するには権限レベル 2 が必要です。
