---
title: クライアント < - > サーバー間データ共有
description: FancyMenu を使ってサーバーとクライアントの間でカスタムデータを送受信します。
---

# FM Data

「FM Data」システムを使うと、サーバーとクライアントの間でカスタムのテキストデータを送受信できます。

すべての FM Data メッセージには、次の 2 つが含まれます。

1. **データ識別子**（どの種類のメッセージか）
2. **データ値**（実際の内容）

例:

- 識別子: `hud.food`
- データ: `18/20`

# クイックスタート

1. サーバーが `/fmdata send ...` でデータを送信する
2. クライアントが FancyMenu のリスナー **On FM Data Received** で受信する
3. クライアントはアクション **Send FM Data To Server** でサーバーへ返送もできる
4. サーバーは `/fmdata listener ...` で自動的に反応できる
5. サーバーは `/fmdata welcome_data ...` で参加時に自動送信できる

# サーバー -> クライアント

次を使用します。

```mcfunction
/fmdata send <target_player> <data_identifier> <string_data>
```

例:

```mcfunction
/fmdata send Player761 hud.food 18/20
/fmdata send @a "food value update" "18 of 20"
```

注意:

- `<target_player>` は `@a`、`@p`、`@s` などの通常のプレイヤーセレクターに対応しています
- スペースを含む値は引用符で囲んでください

# クライアント: データを受信

FancyMenu のリスナーを使用します。

- **On FM Data Received**

利用可能な変数:

- `$$data_identifier`
- `$$data`
- `$$sent_by`

`$$sent_by` は次の値です。

- マルチプレイヤーではサーバー IP
- シングルプレイヤーでは `integrated_server`

よくある用途:

- テキスト要素の更新
- メニューアクションの発動
- 受信した識別子/データに応じた処理の実行

# クライアント -> サーバー

FancyMenu のアクションを使用します。

- **Send FM Data To Server**

このアクションには 2 つの入力があります。

1. データ識別子
2. データ

その後、サーバーは `/fmdata listener ...` で受信データを処理できます。

# サーバーリスナー

サーバーリスナーはクライアントからの受信データを監視し、トリガーされたときに 1 つまたは複数のコマンドを実行できます。

サーバーリスナーは保存され、再起動後も有効なままです。

次のコマンドで管理します。

- `/fmdata listener list`
- `/fmdata listener add ...`
- `/fmdata listener edit ...`
- `/fmdata listener remove ...`

## 追加 / 編集の構文

```mcfunction
/fmdata listener add <unique_listener_name> <matching_type_identifier> <matching_type_data> <ignore_case_identifier> <ignore_case_data> <fire_for_player> <listen_for_identifier> <listen_for_data> <commands_to_execute_on_fire>
```

```mcfunction
/fmdata listener edit <listener_name> <matching_type_identifier> <matching_type_data> <ignore_case_identifier> <ignore_case_data> <fire_for_player> <listen_for_identifier> <listen_for_data> <commands_to_execute_on_fire>
```

## 削除の構文

```mcfunction
/fmdata listener remove <listener_name>
```

## マッチングタイプ

`matching_type_identifier` と `matching_type_data` には次のいずれかを指定できます。

- `equals`
- `contains`
- `starts_with`
- `ends_with`

## マッチングルール

- `ignore_case_identifier` と `ignore_case_data` は true/false の切り替えです
- `listen_for_identifier` はワイルドカード `*` に対応しています（常に一致）
- `listen_for_data` はワイルドカード `*` に対応しています（常に一致）
- `fire_for_player` は通常のプレイヤーセレクターを使用します（例: `@a`、`@p`、`Player761`）

## 発火時に実行するコマンド

`commands_to_execute_on_fire` は 1 つのテキスト入力です。

- 複数コマンドは `|||` で区切ります
- 文字列としての区切り記号をそのまま使いたい場合は `\|\|\|` とエスケープします

ここでは、コマンド実行直前に置換される 2 つの特別なプレースホルダーを使えます。

- `%fm_sender%` -> FM Data を送信したプレイヤー
- `%fm_data%` -> クライアントから受信したデータ値

コマンドはサーバーコマンドとして実行されます。

## コマンド例

任意のプレイヤーからのボタン押下に反応する:

```mcfunction
/fmdata listener add button_ping equals equals false false @a ui.button pressed "tellraw @a {\"text\":\"%fm_sender% がボタンを押しました\"}"
```

データに `gold` が含まれるときに複数コマンドを実行する:

```mcfunction
/fmdata listener add reward equals contains false true @a reward "gold" "say %fm_sender% からの報酬: %fm_data%|||effect give %fm_sender% minecraft:speed 3 1 true"
```

# ウェルカムデータ

ウェルカムデータは、プレイヤーが参加したときに一致するプレイヤーへ FM Data を送信します。

エントリは次のコマンドで管理します。

- `/fmdata welcome_data list`
- `/fmdata welcome_data add ...`
- `/fmdata welcome_data edit ...`
- `/fmdata welcome_data remove ...`

## 追加 / 編集の構文

```mcfunction
/fmdata welcome_data add <unique_welcome_data_name> <target_player> <data_identifier> <string_data>
```

```mcfunction
/fmdata welcome_data edit <welcome_data_name> <target_player> <data_identifier> <string_data>
```

## 削除の構文

```mcfunction
/fmdata welcome_data remove <welcome_data_name>
```

注意:

- `<target_player>` は `@a`、`@p`、`@s` などの通常のセレクターに対応しています
- データは参加した一致プレイヤーに送信されます
- エントリは自動的に保存・読み込みされます

## コマンド例

参加したすべてのプレイヤーにウェルカムデータを送信する:

```mcfunction
/fmdata welcome_data add welcome_all @a hud.welcome "ようこそ!"
```

1 人のプレイヤーのみにウェルカムデータを送信する:

```mcfunction
/fmdata welcome_data add welcome_vip Player761 hud.vip "VIP 特典が有効になりました"
```

# ベストプラクティス

1. `hud.food`、`menu.shop.open`、`quest.progress` のような分かりやすい識別子を使いましょう。
2. 各識別子のデータ形式は一貫させましょう。
3. まずはシンプルに: 複雑なリスナーを作る前に `/fmdata send` でテストしましょう。
4. 本当に全体向けの動作が必要な場合だけ `@a` を使いましょう。
5. `/fmdata listener list` と `/fmdata welcome_data list` を使って設定を整理しましょう。
