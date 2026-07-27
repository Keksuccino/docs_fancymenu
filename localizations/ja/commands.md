---
title: コマンド
description: FancyMenu のコマンドとその使い方。
---

# コマンド

FancyMenu は、FTB Quests などの他の MOD と組み合わせると非常に便利な、いくつかのコマンドをゲームに追加します。

> [!WARNING]
> マルチプレイでコマンドを使うには、FancyMenu を **サーバー**（およびクライアント）に導入する必要があります！

## 対象プレイヤーと権限

`/openguiscreen`、`/closeguiscreen`、`/fmlayout` の target-player 引数は省略可能です。プレイヤーが省略した場合、そのプレイヤー自身にコマンドが適用されます。対象を指定する場合は、通常のプレイヤー名や `@a` のようなセレクターを使えます。

- `/openguiscreen` または `/closeguiscreen` に対象引数を指定するには、コマンドの実行元がその対象であっても **権限レベル 2**（Game Master / OP レベル 2）が必要です。
- `/fmlayout` に対象引数を指定するには、コマンドの実行元がその対象であっても **権限レベル 3**（Admin / OP レベル 3）が必要です。
- `/fmdata` の各サブコマンドには、すべて **権限レベル 2**（Game Master / OP レベル 2）が必要です。

対象が省略可能な 3 つのコマンドでは、対象の省略はコマンドの実行元がプレイヤーの場合にのみ機能します。サーバーコンソールは対象を指定し、さらに対象引数に必要な権限条件を満たす必要があります。

## /openguiscreen

`/openguiscreen` コマンドは、バニラ、MOD、または [カスタム GUI](./custom-guis) を開きます。FancyMenu がサーバーとクライアントの両方に導入されていれば、他のプレイヤーを対象にできます。

[コマンドによる GUI の開き方](./opengui-command) と [画面識別子](./screen-identifiers) を参照してください。

すべての MOD の画面を直接作成できるわけではありません。対象の画面が未対応の場合、FancyMenu はエラーを表示します。ローカルレイアウトでは、通常その画面を開くウィジェットに [**バニラ/MOD ボタンを模倣**](./action-scripts#mimic-vanillamod-button-mimicbutton) を使ってください。

**使用方法:** `/openguiscreen <screen_identifier> [<target_players>]`

## /closeguiscreen

`/closeguiscreen` コマンドは、コマンド実行元または選択したプレイヤーの現在の画面を閉じます。コマンドを実行できるクエスト系、イベント系、または自動化系の MOD と組み合わせると便利です。

**使用方法:** `/closeguiscreen [<target_players>]`

## /fmlayout

`/fmlayout` コマンドは、1 人以上のクライアントでレイアウトを有効にするかどうかを設定します。FancyMenu に表示されている名前を正確に使い、スペースを含む名前は引用符で囲んでください。

**使用方法:** `/fmlayout <layout_name> <true|false> [<target_players>]`

例:

- `/fmlayout quest_complete true` は、コマンドを実行したプレイヤーに対して `quest_complete` を有効にします。
- `/fmlayout quest_complete false @a` は、オンラインの全プレイヤーに対して無効にします。対象引数を指定するには権限レベル 3 が必要です。

## /fmvariable

`/fmvariable` コマンドは [FancyMenu の変数](./variables) の設定と取得を行います。

このコマンドを別のプレイヤーとして実行するには、バニラの `/execute as` コマンドを使います。
`/execute as ExamplePlayer run fmvariable ...`

**使用方法:**

- `/fmvariable get <variable_name>`
- `/fmvariable set <variable_name> <send_chat_feedback> <set_to_value>`

### 取得

**変数の値を取得する**には、次のように `get` サブコマンドを使います:
`/fmvariable get some_variable`

すると、この変数の値がチャットに表示されます。

### 設定

**変数を設定する**には、新しい値の前にチャットフィードバックの真偽値を入れます:
`/fmvariable set some_variable true new_value`

`send_chat_feedback` 引数は、FancyMenu が変更をチャットで確認表示するかどうかを制御します。`set_to_value` 引数はコマンドの残りをすべて消費するため、値にスペースを含めることができます。たとえば、`/fmvariable set greeting false Hello from FancyMenu` は、成功フィードバックを送らずに `Hello from FancyMenu` を保存します。

## /fmdata

`/fmdata` コマンドは、サーバーと FancyMenu クライアント間でカスタムデータを送信し、サーバー側のリスナーを管理し、プレイヤー参加時に送信されるデータを設定します。`/fmdata` の各サブコマンドには権限レベル 2 が必要です。

すべてのサブコマンド、構文、例については [FM データ](./fm-data) を参照してください。
