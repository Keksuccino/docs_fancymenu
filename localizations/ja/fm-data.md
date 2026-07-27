---
title: クライアント < - > サーバー間データ共有
description: FancyMenu を使って、サーバーとクライアント間でカスタムデータを送受信します。
---

# FM Data

「FM Data」システムを使うと、サーバーとクライアント間でカスタムのテキストデータを送信できます。

すべての `/fmdata` サブコマンドには **権限レベル 2**（Game Master / OP レベル 2）が必要です。

すべての FM Data メッセージには次の要素があります。

1. **データ識別子**（どの種類のメッセージか）
2. **データ値**（実際の内容）

例:

- 識別子: `hud.food`
- データ: `18/20`

# クイックスタート

1. サーバーが `/fmdata send ...` でデータを送信する
2. クライアントが FancyMenu リスナー **On FM Data Received** で受信する
3. クライアントはアクション **Send FM Data To Server** でデータをサーバーへ返送できる
4. サーバーは `/fmdata listener ...` で自動的に反応できる
5. サーバーは `/fmdata welcome_data ...` で参加時に自動送信できる

# サーバー -> クライアント

次を使用します。

```mcfunction
/fmdata send <target_players> <data_identifier> <string_data>
```

例:

```mcfunction
/fmdata send Player761 hud.food 18/20
/fmdata send @a "food value update" "18 of 20"
```

注意:

- `<target_players>` はプレイヤー名や `@a`、`@p`、`@s` などのセレクターに対応しています
- スペースを含む値には引用符を使ってください

# クライアント: データ受信

FancyMenu リスナーを使用します:

- **On FM Data Received**

利用可能な変数:

- `$$data_identifier`
- `$$data`
- `$$sent_by`

`$$sent_by` は次の値です。

- マルチプレイではサーバー IP
- シングルプレイでは `integrated_server`

主な用途:

- テキスト要素の更新
- メニューアクションのトリガー
- 受信した識別子/データに基づく処理の実行

# クライアント -> サーバー

FancyMenu アクションを使用します:

- **Send FM Data To Server**

このアクションには 2 つの入力があります。

1. データ識別子
2. データ

サーバーは `/fmdata listener ...` で受信データを処理できます。

# サーバーリスナー

サーバーリスナーはクライアントからの受信データを監視し、トリガーされると 1 つ以上のコマンドを実行できます。

サーバーリスナーは保存され、再起動後も有効なままです。

次のコマンドで管理します:

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

`matching_type_identifier` と `matching_type_data` には次の値を指定できます。

- `equals`
- `contains`
- `starts_with`
- `ends_with`

## マッチングルール

- `ignore_case_identifier` と `ignore_case_data` は true/false の切り替えです
- `listen_for_identifier` はワイルドカード `*` に対応します（常に一致）
- `listen_for_data` はワイルドカード `*` に対応します（常に一致）
- `fire_for_player` は通常のプレイヤーセレクターを使用します（例: `@a`、`@p`、`Player761`）

## 発火時に実行するコマンド

`commands_to_execute_on_fire` は 1 つのテキスト入力です。

- 複数のコマンドは `|||` で区切ります
- 文字列としての区切り記号をそのまま使いたい場合は `\|\|\|` とエスケープします

ここでは、コマンド実行直前に置換される 2 つの特別なプレースホルダーを使えます。

- `%fm_sender%` -> FM Data を送信したプレイヤー
- `%fm_data%` -> クライアントから受信したデータ値

コマンドはサーバーコマンドとして実行されます。

## コマンド例

任意のプレイヤーのボタン押下に反応する:

```mcfunction
/fmdata listener add button_ping equals equals false false @a ui.button pressed "tellraw @a {\"text\":\"%fm_sender% がボタンを押しました\"}"
```

データに `gold` が含まれているときに複数コマンドを実行する:

```mcfunction
/fmdata listener add reward equals contains false true @a reward "gold" "say Reward from %fm_sender%: %fm_data%|||effect give %fm_sender% minecraft:speed 3 1 true"
```

# ウェルカムデータ

ウェルカムデータは、プレイヤー参加時に一致するプレイヤーへ FM Data を送信します。

次のコマンドでエントリを管理します:

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
- データは、条件に一致するプレイヤーが参加したときに送信されます
- エントリは保存され、自動で読み込まれます

## コマンド例

参加したすべてのプレイヤーにウェルカムデータを送る:

```mcfunction
/fmdata welcome_data add welcome_all @a hud.welcome "ようこそ！"
```

1 人のプレイヤーだけにウェルカムデータを送る:

```mcfunction
/fmdata welcome_data add welcome_vip Player761 hud.vip "VIP 特典が有効になりました"
```

# ベストプラクティス

1. `hud.food`、`menu.shop.open`、`quest.progress` のような分かりやすい識別子を使いましょう。
2. 各識別子ごとにデータ形式を統一しましょう。
3. まずはシンプルに始め、複雑なリスナーを作る前に `/fmdata send` でテストしましょう。
4. 本当に全体向けの動作が必要な場合のみ `@a` を使いましょう。
5. 設定を整理するために `/fmdata listener list` と `/fmdata welcome_data list` を活用しましょう。
