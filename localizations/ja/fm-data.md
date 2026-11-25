---
title: クライアント < - > サーバー間のデータ共有
description: FancyMenu を使って、サーバーとクライアント間でカスタムデータを送受信します。
sourceBlobSha: 35ae4605e43ac917f11c24e5d97a5c311c9aa01a
---

# FM Data

「FM Data」システムを使うと、サーバーとクライアント間で任意のテキストデータを送信できます。

すべての `/fmdata` サブコマンドには **権限レベル 2**（ゲームマスター / OP レベル 2）が必要です。

FM Data メッセージには、次の情報が含まれます。

1. **データ識別子**（メッセージの種類）
2. **データ値**（実際の内容）

例：

- 識別子：`hud.food`
- データ：`18/20`

# クイックスタート

1. サーバーから `/fmdata send ...` でデータを送信します。
2. クライアントは FancyMenu のリスナー **FM Data 受信時（On FM Data Received）** で受信します。
3. クライアントからアクション **サーバーに FM Data を送信（Send FM Data To Server）** を使って、データを返信することもできます。
4. サーバーは `/fmdata listener ...` を使って自動的に応答できます。
5. サーバーは `/fmdata welcome_data ...` を使って、プレイヤーの参加時にデータを自動送信できます。

# サーバーからクライアントへ

次のコマンドを使います。

```mcfunction
/fmdata send <target_players> <data_identifier> <string_data>
```

例：

```mcfunction
/fmdata send Player761 hud.food 18/20
/fmdata send @a "food value update" "18 of 20"
```

注意事項：

- `<target_players>` には、プレイヤー名や `@a`、`@p`、`@s` などのセレクターを指定できます。
- スペースを含む値には引用符を使います。

# クライアント：データの受信

FancyMenu の次のリスナーを使います。

- **FM Data 受信時（On FM Data Received）**

使用できる変数：

- `$$data_identifier`
- `$$data`
- `$$sent_by`

`$$sent_by` の値は次のとおりです。

- マルチプレイの場合はサーバー IP
- シングルプレイの場合は `integrated_server`

主な用途：

- テキスト要素の更新
- メニューアクションの実行
- 受信した識別子やデータに応じた処理の実行

# クライアントからサーバーへ

FancyMenu の次のアクションを使います。

- **サーバーに FM Data を送信（Send FM Data To Server）**

このアクションには、次の 2 つの入力項目があります。

1. データ識別子
2. データ

サーバーは `/fmdata listener ...` を使って、受信したデータを処理できます。

# サーバーリスナー

サーバーリスナーはクライアントからのデータを監視し、起動時に 1 つ以上のコマンドを実行できます。

サーバーリスナーは保存され、再起動後も有効な状態を保ちます。

次のコマンドで管理できます。

- `/fmdata listener list`
- `/fmdata listener add ...`
- `/fmdata listener edit ...`
- `/fmdata listener remove ...`

## 追加・編集の構文

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

## 一致タイプ

`matching_type_identifier` と `matching_type_data` には、次のいずれかを指定できます。

- `equals`
- `contains`
- `starts_with`
- `ends_with`

## 一致条件

- `ignore_case_identifier` と `ignore_case_data` は、true/false で切り替えます。
- `listen_for_identifier` ではワイルドカード `*` を使えます（常に一致）。
- `listen_for_data` ではワイルドカード `*` を使えます（常に一致）。
- `fire_for_player` には通常のプレイヤーセレクター（例：`@a`、`@p`、`Player761`）を指定します。

## 起動時に実行するコマンド

`commands_to_execute_on_fire` は、1 つのテキスト入力として指定します。

- 複数のコマンドは `|||` で区切ります。
- 区切り文字をそのまま含めるには、`\|\|\|` とエスケープします。

ここでは、コマンドの実行直前に置き換えられる特殊なプレースホルダーを 2 つ使用できます。

- `%fm_sender%` -> FM Data を送信したプレイヤー
- `%fm_data%` -> クライアントから受信したデータ値

コマンドはサーバーコマンドとして実行されます。

## コマンドの例

任意のプレイヤーによるボタン押下に反応する：

```mcfunction
/fmdata listener add button_ping equals equals false false @a ui.button pressed "tellraw @a {\"text\":\"%fm_sender% pressed the button\"}"
```

データに `gold` が含まれる場合に複数のコマンドを実行する：

```mcfunction
/fmdata listener add reward equals contains false true @a reward "gold" "say Reward from %fm_sender%: %fm_data%|||effect give %fm_sender% minecraft:speed 3 1 true"
```

# ウェルカムデータ

ウェルカムデータは、参加したプレイヤーが条件に一致すると、そのプレイヤーに FM Data を送信します。

次のコマンドでエントリを管理できます。

- `/fmdata welcome_data list`
- `/fmdata welcome_data add ...`
- `/fmdata welcome_data edit ...`
- `/fmdata welcome_data remove ...`

## 追加・編集の構文

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

注意事項：

- `<target_player>` には `@a`、`@p`、`@s` などの通常のセレクターを指定できます。
- 参加時に、条件に一致するプレイヤーへデータが送信されます。
- エントリは自動的に保存・読み込みされます。

## コマンドの例

参加するすべてのプレイヤーにウェルカムデータを送信する：

```mcfunction
/fmdata welcome_data add welcome_all @a hud.welcome "Welcome!"
```

特定のプレイヤー 1 人だけにウェルカムデータを送信する：

```mcfunction
/fmdata welcome_data add welcome_vip Player761 hud.vip "VIP perks enabled"
```

# AI 用にエクスポート

Alice やその他の AI に助けを求めるには、[AI 用にエクスポート](/export-for-ai#servers)を使って、サーバーのリスナーとウェルカムデータをエクスポートします。

```mcfunction
/fmdata export_for_ai copy
/fmdata export_for_ai file
```

`copy` は、クリックするとエクスポート内容をコピーできるチャットメッセージを送信します。`file` は、サーバー上の `fancymenu_data/ai_exports/` に保存します。

# ベストプラクティス

1. `hud.food`、`menu.shop.open`、`quest.progress` のように、わかりやすい識別子を使います。
2. 識別子ごとにデータ形式を統一します。
3. まずはシンプルに始めましょう。複雑なリスナーを作る前に、`/fmdata send` でテストします。
4. 全体に適用する場合に限り、`@a` を使います。
5. `/fmdata listener list` と `/fmdata welcome_data list` を使って、設定を整理しておきます。
