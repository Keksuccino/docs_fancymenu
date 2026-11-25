---
title: コマンド
description: FancyMenuのコマンドとその使い方。
sourceBlobSha: 265258e46a219a12892146238e379af513ff0848
---

# コマンド

FancyMenuは、FTB Questsなどの他のMODと組み合わせると非常に便利なコマンドをゲームに追加します。

> [!WARNING]
> マルチプレイでコマンドを使用するには、FancyMenuを**サーバー**（およびクライアント）に導入する必要があります！

## 対象プレイヤーと権限

`/openguiscreen`、`/closeguiscreen`、`/fmlayout` の対象プレイヤー引数は省略できます。省略した場合、コマンドは実行したプレイヤーに適用されます。対象を指定する場合は、通常のプレイヤー名や `@a` などのセレクターを使用できます。

- `/openguiscreen` または `/closeguiscreen` に対象引数を指定するには、コマンド実行者自身を指定する場合でも**権限レベル2**（ゲームマスター / OPレベル2）が必要です。
- `/fmlayout` に対象引数を指定するには、コマンド実行者自身を指定する場合でも**権限レベル3**（管理者 / OPレベル3）が必要です。
- `/fmdata` のすべてのサブコマンドには、**権限レベル2**（ゲームマスター / OPレベル2）が必要です。

対象を省略できる3つのコマンドで、対象を省略できるのはコマンド実行者がプレイヤーの場合のみです。サーバーコンソールから実行する場合は対象を指定し、対象引数に必要な権限を満たす必要があります。

## /openguiscreen

`/openguiscreen` コマンドは、バニラ、MOD、または[カスタムGUI](/custom-guis)を開きます。サーバーと各プレイヤーのクライアントにFancyMenuが導入されていれば、他のプレイヤーを対象にできます。

[コマンドでGUIを開く](/opengui-command)と[画面識別子](/screen-identifiers)を参照してください。

すべてのMODの画面を直接作成できるわけではありません。対象の画面がサポートされていない場合、FancyMenuはエラーを表示します。ローカルレイアウトでは、通常その画面を開くウィジェットに[**バニラ/MODのボタンを再現**](/action-scripts#mimic-vanillamod-button)を使用してください。

**使い方:** `/openguiscreen <screen_identifier> [<target_players>]`

## /closeguiscreen

`/closeguiscreen` コマンドは、コマンド実行者または選択したプレイヤーの現在の画面を閉じます。コマンドを実行できるクエスト、イベント、自動化MODと組み合わせると便利です。

**使い方:** `/closeguiscreen [<target_players>]`

## /fmlayout

`/fmlayout` コマンドは、1人または複数のクライアントでレイアウトを有効にするかどうかを設定します。FancyMenuに表示されているレイアウト名を正確に使用し、スペースを含む名前は引用符で囲んでください。

**使い方:** `/fmlayout <layout_name> <true|false> [<target_players>]`

例:

- `/fmlayout quest_complete true` は、コマンドを実行したプレイヤーに対して `quest_complete` を有効にします。
- `/fmlayout quest_complete false @a` は、オンラインのすべてのプレイヤーに対して無効にします。対象引数を指定するには権限レベル3が必要です。

## /fmvariable

`/fmvariable` コマンドでは、[FancyMenuの変数](/variables)を設定したり、値を取得したりできます。

別のプレイヤーとしてこのコマンドを実行するには、バニラの `/execute as` コマンドを使用します:
`/execute as ExamplePlayer run fmvariable ...`

**使い方:**

- `/fmvariable get <variable_name>`
- `/fmvariable set <variable_name> <send_chat_feedback> <set_to_value>`

### 取得

**変数の値を取得する**には、次のように `get` サブコマンドを使用します:
`/fmvariable get some_variable`

変数の値がチャットに表示されます。

### 設定

**変数を設定する**には、新しい値の前にチャット通知の真偽値を指定します:
`/fmvariable set some_variable true new_value`

`send_chat_feedback` 引数は、FancyMenuが変更をチャットで通知するかどうかを制御します。`set_to_value` 引数はコマンドの残りすべてを値として扱うため、値にスペースを含めることができます。たとえば、`/fmvariable set greeting false Hello from FancyMenu` は、成功通知を送信せずに `Hello from FancyMenu` を保存します。

## /fmdata

`/fmdata` コマンドでは、サーバーとFancyMenuクライアント間でカスタムデータを送信したり、サーバー側のリスナーを管理したり、プレイヤーの参加時に送信するデータを設定したりできます。また、この設定を[AIチャット](/export-for-ai#servers)用にエクスポートできます。`/fmdata` のすべてのサブコマンドには権限レベル2が必要です。

すべてのサブコマンド、構文、使用例については、[FM Data](/fm-data)を参照してください。
