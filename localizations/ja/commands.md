---
title: コマンド
description: FancyMenu のコマンドとその使い方。
---

# コマンド

FancyMenu は、FTB Quests などの他のMODと組み合わせると非常に便利なコマンドをゲームに追加します。

> マルチプレイでコマンドを使うには、FancyMenu が **サーバー**（およびクライアント）に導入されている必要があります！
{.is-warning}

## /openguiscreen

`/openguiscreen` コマンドを使うと、GUI（バニラ/MOD、およびカスタム GUI）を開けます。
FancyMenu がサーバーとクライアントの両方に導入されていれば、他のプレイヤーの GUI をリモートで開くこともできます。

このコマンドのより詳しい説明については、[コマンドで GUI を開く](/opengui-command) ページを参照してください。

このコマンドはすべての画面で動作するわけではなく、特に MOD の画面では失敗することがあります。画面を開けなかった場合はエラーが表示されます。その場合、FancyMenu で自動的に開けるようにするには複雑すぎる画面である可能性が高いため、できることはあまりありません。

また、今後は MOD の画面への互換性を手動で追加することもしません。世の中にあるすべての MOD に対応させるには途方もない時間がかかるためです。ごめんなさい。

**使用法:** `/openguiscreen <screen_identifier> <target_player>`

## /closeguiscreen

`/closeguiscreen` コマンドを使うと、現在の GUI を閉じられます。

え？ まったく役に立たないって？

まあ、そうでもあり、そうでもありません。

このコマンドは、特定の操作でコマンドを発動する MOD を使っているときに便利です。
つまり、他の MOD がない状態では完全に無意味ですが、適切な MOD が導入されていればとても役立つことがあります！

**使用法:** `/closeguiscreen <target_player>`

## /fmvariable

`/fmvariable` コマンドを使うと、FancyMenu の変数を設定・取得できます。

サーバー上でこのコマンドを別のプレイヤーとして実行するには、バニラの `/execute as` コマンドを使えます。
たとえば、プレイヤー `ExamplePlayer` として `/fmvariable` コマンドを実行したい場合は、次のように入力します。
`/execute as ExamplePlayer run fmvariable...`。

**使用法:** `/fmvariable <get_or_set> <variable_name> [<set_to_value>] [<send_chat_feedback>]`

### 取得
変数の値を**取得**するには、次のように `get` サブコマンドを使います。
`/fmvariable get some_variable`

すると、この変数の値がチャットに表示されます。

### 設定
変数を**設定**するには、次のように `set` サブコマンドを使います。
`/fmvariable set some_variable new_value true`

最後の引数は、チャットフィードバックを受け取るかどうかを設定するものです。つまり、このコマンドのメッセージをチャットに表示するかどうかを指定します。
