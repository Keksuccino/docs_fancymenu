---
title: プレースホルダー
description: プレースホルダーの使い方。
---
# プレースホルダー

プレースホルダーは、テキスト、ボタン、要件、その他対応フィールドにリアルタイムの値を差し込みます。

# 一般情報

## 基本構文
FancyMenu のプレースホルダーは、JSON に似た構文を使用します:
```
{"placeholder":"modversion","values":{"modid":"fancymenu"}}
```

たとえば、プレイヤー名を表示するには:
```
{"placeholder":"playername"}
```

## プレースホルダーのネスト
1つのプレースホルダーの値の中に、別のプレースホルダーを入れ子で使えます。

ネストされたプレースホルダーの例:
```
{"placeholder":"calc","values":{"decimal":"true","expression":"{"placeholder":"maxram"} / 1024"}}
```
この例では、最大 RAM 値を 1024 で割って、MB から GB に変換しています。

> [!IMPORTANT]
> これは FancyMenu の構文であり、JSON ではありません。ネストされたプレースホルダーは、上に示したエスケープされていない正確な形式を使うため、JSON フォーマッターは拒否または書き換えます。プレースホルダー名は大文字と小文字を区別します。形式が壊れている、または不明なプレースホルダーはそのままテキストとして表示され、ログに記録されます。

# プレースホルダーの使い方

テキスト入力に対応している要素の多くは、プレースホルダーをサポートしています。編集時に、そのテキスト入力がプレースホルダー対応かどうかを確認できます。テキストを編集したときに全画面の **テキストエディター** が開く場合、その項目はプレースホルダーに対応しています。

**利用可能なすべてのプレースホルダーの一覧** を確認するには、**テキストエディター** の **右上** にある **Placeholders** ボタンをクリックします。

プレースホルダー一覧の上部には、プレースホルダーを検索できる **検索バー** があります。

一覧の中のプレースホルダーをクリックすると、そのプレースホルダーがテキスト内容に貼り付けられます。

# プレースホルダーの詳細

このセクションでは、FancyMenu に組み込まれているプレースホルダーを一覧で紹介します。

## 取得できない場合の結果

プレースホルダーの出力は常にテキストです。データが取得できない場合、結果はプレースホルダーによって異なります。一般的なフォールバックは、空文字列、`0`、`0.0`、`00:00`、`false`、`UNKNOWN`、`ERROR` です。特定のフォールバックがある項目ではそれを直接示しています。環境に依存する出力を [要件](./conditions)、パス、コマンド、URL で使う前に、必ずフォールバックをテストしてください。

## プレイヤー名 (`playername`)

**目的:** 現在のプレイヤーのユーザー名を返します。

**値:** なし

**例:**

```
{"placeholder":"playername"}
```

**出力:** `Steve`

## プレイヤー UUID (`playeruuid`)

**目的:** プレイヤーの一意識別子を返します。

**値:** なし

**例:**

```
{"placeholder":"playeruuid"}
```

**出力:** `c8cde7fe-7ced-11eb-9439-0242ac130002`

## Minecraft バージョン (`mcversion`)

**目的:** 現在の Minecraft のバージョンを返します。

**値:** なし

**例:**

```
{"placeholder":"mcversion"}
```

**出力:** `1.21.1`

## Mod ローダーのバージョン (`loaderver`)

**目的:** Mod ローダー（Fabric/NeoForge）のバージョンを返します。

**値:** なし

**例:**

```
{"placeholder":"loaderver"}
```

**出力:** `0.16.14`

## Mod ローダー名 (`loadername`)

**目的:** Mod ローダーの名前を返します。

**値:** なし

**例:**

```
{"placeholder":"loadername"}
```

**出力:** `Fabric`

## Mod バージョン (`modversion`)

**目的:** 特定の Mod のバージョンを返します。

**値:** `modid`

**例:**

```
{"placeholder":"modversion","values":{"modid":"example_mod"}}
```

**出力:** `1.2.3`

## 総 Mod 数 (`totalmods`)

**目的:** `mods` ディレクトリと読み込まれている Mod 数に基づいて、おおよその Mod ファイル数を返します。無効化されたすべての Mod を正確に数えるわけではありません。

**値:** なし

**例:**

```
{"placeholder":"totalmods"}
```

**出力:** `45`

## 有効な Mod 数 (`loadedmods`)

**目的:** 現在読み込まれている Mod の数を返します。

**値:** なし

**例:**

```
{"placeholder":"loadedmods"}
```

**出力:** `43`

## ワールド読み込み進行状況 (`world_load_progress`)

**目的:** 現在のワールド読み込み進行状況をパーセンテージで返します。

**値:** なし

**例:**

```
{"placeholder":"world_load_progress"}
```

**出力:** `75`

## Minecraft オプション値 (`minecraft_option_value`)

**目的:** Minecraft のオプションの値を返します。

**値:** `name`

**例:**

```
{"placeholder":"minecraft_option_value","values":{"name":"fov"}}
```

**出力:** `70`

## 最後に開いたワールドまたはサーバー (`last_world_server`)

**目的:** 最後にアクセスしたワールドまたはサーバーの情報を返します。

**値:** `type`, `full_world_path`

**例:**

```
{"placeholder":"last_world_server","values":{"type":"both","full_world_path":"true"}}
```
パラメーター:
- `type`: 返す情報の種類を決定します
  - `"both"`: 最後に開いたワールドまたはサーバーを返します（既定）
  - `"server"`: 最後に開いたものがサーバーだった場合のみ返します
  - `"world"`: 最後に開いたものがワールドだった場合のみ返します
- `full_world_path`: ワールドパスの表示方法を制御します
  - `"true"`: ワールドの完全なパスを返します（既定）
  - `"false"`: パスなしのワールド名のみを返します（サーバーには影響しません）

例:
- サーバー: `mc.hypixel.net`
- 完全パス付きワールド: `saves/New World`
- 完全パスなしワールド: `New World`

## 画面幅 (`guiwidth`)

**目的:** 現在の画面幅を GUI スケールのピクセル単位で返します。物理モニターのピクセルではありません。

**値:** なし

**例:**

```
{"placeholder":"guiwidth"}
```

**出力:** `960`

## 画面高さ (`guiheight`)

**目的:** 現在の画面高さを GUI スケールのピクセル単位で返します。物理モニターのピクセルではありません。

**値:** なし

**例:**

```
{"placeholder":"guiheight"}
```

**出力:** `540`

## 現在の画面 ID (`screenid`)

**目的:** 現在の画面の識別子を返します。

**値:** なし

**例:**

```
{"placeholder":"screenid"}
```

**出力:** `title_screen`

## 要素の幅 (`elementwidth`)

**目的:** 特定の要素の幅を返します。

**値:** `id`

**例:**

```
{"placeholder":"elementwidth","values":{"id":"my_button"}}
```

**出力:** `200`

## 要素の高さ (`elementheight`)

**目的:** 特定の要素の高さを返します。

**値:** `id`

**例:**

```
{"placeholder":"elementheight","values":{"id":"my_button"}}
```

**出力:** `20`

## 要素の X 位置 (`elementposx`)

**目的:** 特定の要素の X 座標を返します。

**値:** `id`

**例:**

```
{"placeholder":"elementposx","values":{"id":"my_button"}}
```

**出力:** `150`

## 要素の Y 位置 (`elementposy`)

**目的:** 特定の要素の Y 座標を返します。

**値:** `id`

**例:**

```
{"placeholder":"elementposy","values":{"id":"my_button"}}
```

**出力:** `100`

## マウスの X 位置 (`mouseposx`)

**目的:** 現在のマウスの X 座標を返します。

**値:** なし

**例:**

```
{"placeholder":"mouseposx"}
```

**出力:** `960`

## マウスの Y 位置 (`mouseposy`)

**目的:** 現在のマウスの Y 座標を返します。

**値:** なし

**例:**

```
{"placeholder":"mouseposy"}
```

**出力:** `540`

## 1 秒あたりのクリック数 (`clicks_per_second`)

**目的:** マウスボタンの現在の 1 秒あたりのクリック数を返します。

**値:** `mouse_button`

**例:**

```
{"placeholder":"clicks_per_second","values":{"mouse_button":"left"}}
```
パラメーター:
- `mouse_button`: `left` または `right`

**出力:** `8`

## GUI スケール (`guiscale`)

**目的:** 現在の GUI スケールを返します。

**値:** なし

**例:**

```
{"placeholder":"guiscale"}
```

**出力:** `2`

## バニラのウィジェット/ボタンのラベル・テキスト (`vanillabuttonlabel`)

**目的:** バニラのウィジェット/ボタンのラベルまたはテキストを返します。

**値:** `locator`

**例:**

```
{"placeholder":"vanillabuttonlabel","values":{"locator":"some.menu.identifier:505280"}}
```

**出力:** `Options...`

## テキスト入力欄の値 (`text_input_field_value`)

**目的:** 要素識別子で、カスタムまたはバニラのテキスト入力欄の現在の値を返します。

**値:** `element_identifier`

**例:**

```
{"placeholder":"text_input_field_value","values":{"element_identifier":"my_input"}}
```

**出力:** `Hello World`

## 現在のプレイヤー体力 (`current_player_health`)

**目的:** プレイヤーの現在の体力を返します。

**値:** なし

**例:**

```
{"placeholder":"current_player_health"}
```

**出力:** `20.0`

## プレイヤー最大体力 (`max_player_health`)

**目的:** プレイヤーの最大体力を返します。

**値:** なし

**例:**

```
{"placeholder":"max_player_health"}
```

**出力:** `20.0`

## 現在のプレイヤー体力（パーセント） (`current_player_health_percent`)

**目的:** プレイヤーの体力をパーセンテージで返します。

**値:** なし

**例:**

```
{"placeholder":"current_player_health_percent"}
```

**出力:** `100`

## 現在のプレイヤー吸収体力 (`current_player_absorption_health`)

**目的:** プレイヤーの吸収体力（黄金のハート）を返します。

**値:** なし

**例:**

```
{"placeholder":"current_player_absorption_health"}
```

**出力:** `4.0`

## プレイヤー最大吸収体力 (`max_player_absorption_health`)

**目的:** 吸収体力の最大値を返します。

**値:** なし

**例:**

```
{"placeholder":"max_player_absorption_health"}
```

**出力:** `4.0`

## 現在のプレイヤー吸収体力（パーセント） (`current_player_absorption_health_percent`)

**目的:** プレイヤーの吸収体力をパーセンテージで返します。

**値:** なし

**例:**

```
{"placeholder":"current_player_absorption_health_percent"}
```

**出力:** `100`

## 現在のプレイヤー満腹度 (`current_player_hunger`)

**目的:** プレイヤーの現在の満腹度を返します。

**値:** なし

**例:**

```
{"placeholder":"current_player_hunger"}
```

**出力:** `20`

## プレイヤー最大満腹度 (`max_player_hunger`)

**目的:** 最大満腹度を返します。

**値:** なし

**例:**

```
{"placeholder":"max_player_hunger"}
```

**出力:** `20`

## 現在のプレイヤー満腹度（パーセント） (`current_player_hunger_percent`)

**目的:** プレイヤーの満腹度をパーセンテージで返します。

**値:** なし

**例:**

```
{"placeholder":"current_player_hunger_percent"}
```

**出力:** `100`

## 現在のプレイヤー満腹度飽和値 (`current_player_hunger_saturation`)

**目的:** プレイヤーの現在の満腹度飽和値を返します。

**値:** なし

**例:**

```
{"placeholder":"current_player_hunger_saturation"}
```

**出力:** `5.0`

## 現在のプレイヤー防具値 (`current_player_armor`)

**目的:** プレイヤーの現在の防具値を返します。

**値:** なし

**例:**

```
{"placeholder":"current_player_armor"}
```

**出力:** `20`

## プレイヤーの防具耐性 (`player_armor_toughness`)

**目的:** プレイヤーの総防具耐性値を返します。

**値:** なし

**例:**

```
{"placeholder":"player_armor_toughness"}
```

**出力:** `8.0`

## プレイヤー最大防具値 (`max_player_armor`)

**目的:** 最大防具値を返します。

**値:** なし

**例:**

```
{"placeholder":"max_player_armor"}
```

**出力:** `20`

## 現在のプレイヤー防具値（パーセント） (`current_player_armor_percent`)

**目的:** プレイヤーの防具値をパーセンテージで返します。

**値:** なし

**例:**

```
{"placeholder":"current_player_armor_percent"}
```

**出力:** `100`

## 現在のプレイヤー酸素レベル (`current_player_oxygen`)

**目的:** プレイヤーの現在の酸素レベル（空気の泡）を返します。

**値:** なし

**例:**

```
{"placeholder":"current_player_oxygen"}
```

**出力:** `300`

## プレイヤー最大酸素レベル (`max_player_oxygen`)

**目的:** 最大酸素レベルを返します。

**値:** なし

**例:**

```
{"placeholder":"max_player_oxygen"}
```

**出力:** `300`

## 現在のプレイヤー酸素レベル（パーセント） (`current_player_oxygen_percent`)

**目的:** プレイヤーの酸素レベルをパーセンテージで返します。

**値:** なし

**例:**

```
{"placeholder":"current_player_oxygen_percent"}
```

**出力:** `100`

## 現在のプレイヤーレベル (`current_player_level`)

**目的:** プレイヤーの現在の経験値レベルを返します。

**値:** なし

**例:**

```
{"placeholder":"current_player_level"}
```

**出力:** `30`

## 現在のプレイヤー経験値 (`current_player_exp`)

**目的:** プレイヤーの総経験値を返します。

**値:** なし

**例:**

```
{"placeholder":"current_player_exp"}
```

**出力:** `1250`

## プレイヤー経験値進行度（パーセント） (`current_player_exp_progress`)

**目的:** 次のレベルまでのプレイヤーの経験値進行度をパーセンテージで返します。

**値:** なし

**例:**

```
{"placeholder":"current_player_exp_progress"}
```

**出力:** `75`

## プレイヤー攻撃力（パーセント） (`player_attack_strength`)

**目的:** プレイヤーの攻撃クールダウンをパーセンテージで返します。

**値:** なし

**例:**

```
{"placeholder":"player_attack_strength"}
```

**出力:** `100`

## プレイヤーのゲームモード (`player_gamemode`)

**目的:** プレイヤーの現在のゲームモードを返します。

**値:** なし

**例:**

```
{"placeholder":"player_gamemode"}
```

**出力:** `survival`

## プレイヤーの向いている方向 (`player_view_direction`)

**目的:** プレイヤーが向いている方向を返します。

**値:** なし

**例:**

```
{"placeholder":"player_view_direction"}
```

**出力:** `north`

## プレイヤーの X 座標 (`player_x_coordinate`)

**目的:** ワールド内のプレイヤーの X 位置を返します。

**値:** なし

**例:**

```
{"placeholder":"player_x_coordinate"}
```

**出力:** `125`

## プレイヤーの Y 座標 (`player_y_coordinate`)

**目的:** ワールド内のプレイヤーの Y 位置を返します。

**値:** なし

**例:**

```
{"placeholder":"player_y_coordinate"}
```

**出力:** `64`

## プレイヤーの Z 座標 (`player_z_coordinate`)

**目的:** ワールド内のプレイヤーの Z 位置を返します。

**値:** なし

**例:**

```
{"placeholder":"player_z_coordinate"}
```

**出力:** `-250`

## 現在の乗り物の体力 (`current_mount_health`)

**目的:** プレイヤーが乗っているエンティティの現在の体力を返します。

**値:** なし

**例:**

```
{"placeholder":"current_mount_health"}
```

**出力:** `30.0`

## 乗り物の最大体力 (`max_mount_health`)

**目的:** プレイヤーが乗っているエンティティの最大体力を返します。

**値:** なし

**例:**

```
{"placeholder":"max_mount_health"}
```

**出力:** `30.0`

## 現在の乗り物の体力（パーセント） (`current_mount_health_percent`)

**目的:** 乗り物の体力をパーセンテージで返します。

**値:** なし

**例:**

```
{"placeholder":"current_mount_health_percent"}
```

**出力:** `100`

## 現在の乗り物ジャンプメーター（パーセント） (`current_mount_jump_meter`)

**目的:** 乗り物のジャンプ力メーター値を返します。

**値:** なし

**例:**

```
{"placeholder":"current_mount_jump_meter"}
```

**出力:** `75`

## 現在のボス体力（パーセント） (`current_boss_health`)

**目的:** 選択されたアクティブなボスの体力を、`0` から `100` の整数パーセンテージで返します。`boss_index` は 0 から始まります。`0` は最初のボスバーを選択します。

**値:** `boss_index`

**例:**

```
{"placeholder":"current_boss_health","values":{"boss_index":"0"}}
```

**出力:** `75`

## ボス名 (`boss_name`)

**目的:** アクティブなボスの名前を返します。

**値:** `boss_index`, `as_json`

**例:**

```
{"placeholder":"boss_name","values":{"boss_index":"0","as_json":"false"}}
```

**出力:** `Ender Dragon`

## ボス数 (`boss_count`)

**目的:** アクティブなボスの数を返します。

**値:** なし

**例:**

```
{"placeholder":"boss_count"}
```

**出力:** `1`

## アクティブな効果数 (`effects_count`)

**目的:** 有効なポーション効果の数を返します。

**値:** なし

**例:**

```
{"placeholder":"effects_count"}
```

**出力:** `3`

## アクティブな効果 (`active_effect`)

**目的:** 特定の有効効果の情報を返します。

**値:** `effect_index`

**例:**

```
{"placeholder":"active_effect","values":{"effect_index":"0"}}
```

**出力:** `minecraft:speed`

## 選択中のホットバー スロット (`active_hotbar_slot`)

**目的:** 現在選択されているホットバーのスロット（0-8）を返します。

**値:** なし

**例:**

```
{"placeholder":"active_hotbar_slot"}
```

**出力:** `4`

## スロット内アイテム (`slot_item`)

**目的:** 特定のインベントリスロット内のアイテム情報を返します。

**値:** `slot`

**例:**

```
{"placeholder":"slot_item","values":{"slot":"0"}}
```

**出力:** `minecraft:diamond_sword`

## スロット内アイテム数 (`slot_item_count`)

**目的:** 特定のプレイヤーインベントリスロットにあるアイテムのスタック数を返します。

**値:** `slot`

**例:**

```
{"placeholder":"slot_item_count","values":{"slot":"0"}}
```

**出力:** `64`

## スロット内アイテム耐久値 (`slot_item_durability`)

**目的:** 特定のプレイヤーインベントリスロットにあるアイテムの耐久値情報を返します。

**値:** `slot`, `format`

**例:**

```
{"placeholder":"slot_item_durability","values":{"slot":"0","format":"percentage"}}
```
パラメーター:
- `slot`: プレイヤーインベントリのスロット番号。
- `format`: `current`、`remaining`、`max`、`damage`、`percentage`、`percent` のいずれか。

**出力:** `87`

## スロット内アイテム表示名 (`slot_item_display_name_fm`)

**目的:** 特定スロット内のアイテムの表示名を JSON テキストコンポーネントとして返します。スペクテイターモードでは、`ignore_spectator` が `true` でない限り、ホットバースロットはスペクテイター用メニューアイテム名に解決される場合があります。

**値:** `slot`, `ignore_spectator`

**例:**

```
{"placeholder":"slot_item_display_name_fm","values":{"slot":"0","ignore_spectator":"false"}}
```

**出力:** `{"text":"Diamond Sword","color":"aqua"}`

## インベントリ内アイテム数 (`inventory_item_count`)

**目的:** プレイヤーのインベントリ全体で一致するアイテムの合計数を返します。`item` が空の場合は、空でないすべてのインベントリスロットのスタック数を合計します。

**値:** `item`

**例:**

```
{"placeholder":"inventory_item_count","values":{"item":"minecraft:diamond"}}
```

**出力:** `12`

## インベントリスロットの食料回復量 (`inventory_slot_food_point_restore_amount`)

**目的:** 指定したプレイヤーインベントリスロットの食料アイテムが回復する満腹度を返します。

**値:** `slot`

**例:**

```
{"placeholder":"inventory_slot_food_point_restore_amount","values":{"slot":"0"}}
```

**出力:** `4.0`

## ホバー中のインベントリアイテム (`hovered_inventory_item`)

**目的:** インベントリ画面で現在ホバーしているアイテムのアイテムキーを返します。

**値:** なし

**例:**

```
{"placeholder":"hovered_inventory_item"}
```

**出力:** `minecraft:apple`

## ワールドゲーム時間 (`game_time`)

**目的:** 現在のゲーム内ティックカウンターを返します。

**値:** なし

**例:**

```
{"placeholder":"game_time"}
```

**出力:** `18000`

## ワールド時刻 (`world_daytime`)

**目的:** 現在のワールドの時刻を返します。

**値:** なし

**例:**

```
{"placeholder":"world_daytime"}
```

**出力:** `13000`

## ワールド時刻の時 (`world_daytime_hour`)

**目的:** ワールド時刻の「時」を返します。既定では 24 時間形式を使います。12 時間形式にするには `twelve_hour_format` を `"true"` にしてください。

**値:** `twelve_hour_format`

**例:**

```
{"placeholder":"world_daytime_hour","values":{"twelve_hour_format":"false"}}
```

**出力:** `12`

## ワールド時刻の分 (`world_daytime_minute`)

**目的:** ワールド時刻の「分」（00-59）を返します。

**値:** なし

**例:**

```
{"placeholder":"world_daytime_minute"}
```

**出力:** `30`

## ワールドの難易度 (`world_difficulty`)

**目的:** 現在のワールド難易度を返します。

**値:** なし

**例:**

```
{"placeholder":"world_difficulty"}
```

**出力:** `normal`

## 現在のワールドシード (`current_world_seed`)

**目的:** 現在のシングルプレイワールドのシードを返します。シードが利用できない場合は空の値を返します。

**値:** なし

**例:**

```
{"placeholder":"current_world_seed"}
```

**出力:** `123456789`

## 現在のバイオーム (`current_biome`)

**目的:** プレイヤーが現在いるバイオームを返します。表示名や翻訳済みの名前が利用可能な場合は、それを返すには `as_key` を `"false"` に設定してください。

**値:** `as_key`

**例:**

```
{"placeholder":"current_biome","values":{"as_key":"true"}}
```

**出力:** `minecraft:plains`

## 現在のディメンション (`current_dimension`)

**目的:** プレイヤーが現在いるディメンションを返します。表示名や翻訳済みの名前が利用可能な場合は、それを返すには `as_key` を `"false"` に設定してください。

**値:** `as_key`

**例:**

```
{"placeholder":"current_dimension","values":{"as_key":"true"}}
```

**出力:** `minecraft:overworld`

## ゲームルールの値 (`gamerule_value`)

**目的:** 読み込まれているワールド/サーバー内のゲームルールの現在値を返します。サーバーワールドではサーバー側に FancyMenu が必要です。

**値:** `name`

**例:**

```
{"placeholder":"gamerule_value","values":{"name":"doDaylightCycle"}}
```

**出力:** `true`

## アイテムカテゴリ (`item_category`)

**目的:** アイテムのクリエイティブタブのカテゴリを返します。カテゴリ名ではなくカテゴリキーを返すには `as_key` を `"true"` に設定してください。

**値:** `item`, `as_key`

**例:**

```
{"placeholder":"item_category","values":{"item":"minecraft:diamond_sword","as_key":"false"}}
```

**出力:** `Combat`

## 現在の HUD タイトル/サブタイトル (`current_title`)

**目的:** 現在表示されているタイトルテキストを返します。

**値:** `is_subtitle`, `as_json`

**例:**

```
{"placeholder":"current_title","values":{"is_subtitle":"false","as_json":"false"}}
```

**出力:** `Game Over!`

## アクションバーのメッセージ (`action_bar_message_fm`)

**目的:** 現在のバニラのアクションバーメッセージをシリアライズされた Minecraft テキストコンポーネントとして返します。

**値:** なし

**例:**

```
{"placeholder":"action_bar_message_fm"}
```

**出力:** `{"text":"You may not rest now","color":"red"}`

## アクションバーメッセージの表示時間 (`action_bar_message_time_fm`)

**目的:** 現在のバニラのアクションバーメッセージがあと何ティック表示されるかを返します。

**値:** なし

**例:**

```
{"placeholder":"action_bar_message_time_fm"}
```

**出力:** `42`

## カメラ回転 X (`camera_rotation_x_fm`)

**目的:** 現在のカメラのピッチを度単位で返します。

**値:** なし

**例:**

```
{"placeholder":"camera_rotation_x_fm"}
```

**出力:** `12.5`

## カメラ回転 Y (`camera_rotation_y_fm`)

**目的:** 現在のカメラのヨーを度単位で返します。

**値:** なし

**例:**

```
{"placeholder":"camera_rotation_y_fm"}
```

**出力:** `-90.0`

## カメラ回転の変化量 X (`camera_rotation_delta_x_fm`)

**目的:** 1 ティックあたりのカメラピッチの変化量を返します。

**値:** なし

**例:**

```
{"placeholder":"camera_rotation_delta_x_fm"}
```

**出力:** `0.4`

## カメラ回転の変化量 Y (`camera_rotation_delta_y_fm`)

**目的:** 1 ティックあたりのカメラヨーの変化量を返します。

**値:** なし

**例:**

```
{"placeholder":"camera_rotation_delta_y_fm"}
```

**出力:** `-1.2`

## ハイライトされたアイテムの表示時間 (`highlighted_item_time_fm`)

**目的:** ハイライトされたアイテム名がホットバー上にあと何ティック表示されるかを返します。

**値:** なし

**例:**

```
{"placeholder":"highlighted_item_time_fm"}
```

**出力:** `30`

## プレイヤーのアイテム使用進行度 (`player_item_use_progress_fm`)

**目的:** 現在のアイテム使用進行度を `0.0` から `1.0` で返します。

**値:** なし

**例:**

```
{"placeholder":"player_item_use_progress_fm"}
```

**出力:** `0.65`

## プレイヤー位置の変化量 X (`player_position_delta_x_fm`)

**目的:** 1 ティックあたりのプレイヤー位置の X 軸変化量を返します。

**値:** なし

**例:**

```
{"placeholder":"player_position_delta_x_fm"}
```

**出力:** `0.0`

## プレイヤー位置の変化量 Y (`player_position_delta_y_fm`)

**目的:** 1 ティックあたりのプレイヤー位置の Y 軸変化量を返します。

**値:** なし

**例:**

```
{"placeholder":"player_position_delta_y_fm"}
```

**出力:** `-0.08`

## プレイヤー位置の変化量 Z (`player_position_delta_z_fm`)

**目的:** 1 ティックあたりのプレイヤー位置の Z 軸変化量を返します。

**値:** なし

**例:**

```
{"placeholder":"player_position_delta_z_fm"}
```

**出力:** `0.12`

## 現在のサーバー IP (`current_server_ip`)

**目的:** 接続中のサーバーの IP を返します。

**値:** なし

**例:**

```
{"placeholder":"current_server_ip"}
```

**出力:** `mc.hypixel.net`

## ワールド内プレイヤー一覧 (`world_players_list`)

**目的:** 現在ワールド内にいるすべてのプレイヤーの一覧を返します。

**値:** `separator`

**例:**

```
{"placeholder":"world_players_list","values":{"separator":", "}}
```

**出力:** `Steve, Alex, Notch`

## サーバー MOTD (`servermotd`)

**目的:** サーバーの MOTD（Message of the Day）を返します。

**値:** `ip`, `line`

**例:**

```
{"placeholder":"servermotd","values":{"ip":"mc.hypixel.net","line":"1"}}
```

**出力:** `Welcome to Hypixel!`

## サーバー PING (`serverping`)

**目的:** サーバーへの ping をミリ秒で返します。

**値:** `ip`

**例:**

```
{"placeholder":"serverping","values":{"ip":"mc.hypixel.net"}}
```

**出力:** `54`

## サーバーのプレイヤー数 (`serverplayercount`)

**目的:** サーバーのプレイヤー数を返します。

**値:** `ip`

**例:**

```
{"placeholder":"serverplayercount","values":{"ip":"mc.hypixel.net"}}
```

**出力:** `25000/30000`

## サーバーの状態 (`serverstatus`)

**目的:** サーバーのオンライン/オフライン状態を返します。

**値:** `ip`

**例:**

```
{"placeholder":"serverstatus","values":{"ip":"mc.hypixel.net"}}
```

**出力:** `§aOnline` または `§cOffline`

## サーバーバージョン (`serverversion`)

**目的:** サーバーの Minecraft バージョンを返します。

**値:** `ip`

**例:**

```
{"placeholder":"serverversion","values":{"ip":"mc.hypixel.net"}}
```

**出力:** `1.21.1`

> [!NOTE]
> 以下のリアルタイム系プレースホルダーは `timezone` 値を受け付けます。`UTC`、`Europe/Berlin`、`America/New_York` のような Java のタイムゾーン ID を使用してください。システムのタイムゾーンを使う場合は省略するか `system` を指定します。`unix_time` は常に Unix タイムスタンプを返し、`timezone` 値はありません。

## 年 (`realtimeyear`)

**目的:** 現在の年を返します。

**値:** なし

**例:**

```
{"placeholder":"realtimeyear"}
```

**出力:** `2024`

## 月 (`realtimemonth`)

**目的:** 現在の月を返します（01-12）。

**値:** なし

**例:**

```
{"placeholder":"realtimemonth"}
```

**出力:** `01`

## 日 (`realtimeday`)

**目的:** 現在の日付を返します（01-31）。

**値:** なし

**例:**

```
{"placeholder":"realtimeday"}
```

**出力:** `27`

## 時 (`realtimehour`)

**目的:** 現在の時を返します。既定では 24 時間形式を使います。12 時間形式にするには `twelve_hour_format` を `"true"` にしてください。

**値:** `twelve_hour_format`, `timezone`

**例:**

```
{"placeholder":"realtimehour","values":{"twelve_hour_format":"false","timezone":"system"}}
```

**出力:** `14`

## 分 (`realtimeminute`)

**目的:** 現在の分を返します（00-59）。

**値:** なし

**例:**

```
{"placeholder":"realtimeminute"}
```

**出力:** `30`

## 秒 (`realtimesecond`)

**目的:** 現在の秒を返します（00-59）。

**値:** なし

**例:**

```
{"placeholder":"realtimesecond"}
```

**出力:** `45`

## 現在時刻ミリ秒（Unix タイムスタンプ） (`unix_time`)

**目的:** 現在の Unix タイムスタンプをミリ秒で返します。

**値:** なし

**例:**

```
{"placeholder":"unix_time"}
```

**出力:** `1716552478123`

## CPU 情報 (`cpuinfo`)

**目的:** CPU に関する情報を返します。

**値:** なし

**例:**

```
{"placeholder":"cpuinfo"}
```

**出力:** `Intel(R) Core(TM) i7-10700K CPU @ 3.80GHz`

## CPU 使用率（JVM） (`jvmcpu`)

**目的:** JVM の CPU 使用率をパーセンテージで返します。

**値:** なし

**例:**

```
{"placeholder":"jvmcpu"}
```

**出力:** `25.5`

## CPU 使用率（OS） (`oscpu`)

**目的:** OS の CPU 使用率をパーセンテージで返します。

**値:** なし

**例:**

```
{"placeholder":"oscpu"}
```

**出力:** `42.8`

## GPU 情報 (`gpuinfo`)

**目的:** Minecraft のアクティブな描画デバイスとして報告される名前を返します。特定の物理 GPU を必ずしも識別できるとは限りません。

**値:** なし

**例:**

```
{"placeholder":"gpuinfo"}
```

**出力:** `NVIDIA GeForce RTX 3080`

## Java バージョン (`javaver`)

**目的:** Java のバージョンを返します。

**値:** なし

**例:**

```
{"placeholder":"javaver"}
```

**出力:** `17.0.2`

## Java 仮想マシン (`jvmname`)

**目的:** Java Virtual Machine の名前を返します。

**値:** なし

**例:**

```
{"placeholder":"jvmname"}
```

**出力:** `OpenJDK 64-Bit Server VM`

## OpenGL バージョン (`glver`)

**目的:** Minecraft のアクティブな描画デバイスのドライバー情報を返します。旧来の `glver` という名前ですが、値が OpenGL のバージョン文字列だけであるとは限りません。

**値:** なし

**例:**

```
{"placeholder":"glver"}
```

**出力:** `4.6.0 NVIDIA 516.94`

## OS 名 (`osname`)

**目的:** オペレーティングシステム名を返します。

**値:** なし

**例:**

```
{"placeholder":"osname"}
```

**出力:** `Windows 10`

## FPS（フレーム毎秒） (`fps`)

**目的:** 現在のフレームレートを返します。

**値:** なし

**例:**

```
{"placeholder":"fps"}
```

**出力:** `120`

## 使用中 RAM（MB） (`usedram`)

**目的:** 現在使用中の RAM 量を MB で返します。

**値:** なし

**例:**

```
{"placeholder":"usedram"}
```

**出力:** `4096`

## 最大 RAM（MB） (`maxram`)

**目的:** 割り当てられた最大 RAM を MB で返します。

**値:** なし

**例:**

```
{"placeholder":"maxram"}
```

**出力:** `8192`

## 使用中 RAM（%%） (`percentram`)

**目的:** 現在使用中の RAM の割合を返します。

**値:** なし

**例:**

```
{"placeholder":"percentram"}
```

**出力:** `50`

## オーディオ要素の音量 (`audio_element_vol`)

**目的:** オーディオ要素の音量を返します。

**値:** `element_identifier`

**例:**

```
{"placeholder":"audio_element_vol","values":{"element_identifier":"background_music"}}
```

**出力:** `0.5`

## 現在のオーディオトラック (`audio_element_current_track`)

**目的:** オーディオ要素のトラック名を返します。

**値:** `element_identifier`, `display_name_mappings`

**例:**

```
{"placeholder":"audio_element_current_track","values":{"element_identifier":"background_music","display_name_mappings":"track1.ogg=>Menu Theme%:%track2.ogg=>Credits Theme"}}
```

`display_name_mappings` では、`=>` がファイル名と表示名の区切り、`%:%` が各マッピングの区切りです。

**出力:** `Menu Theme`

## オーディオの再生時間 (`audio_duration`)

**目的:** [Audio element](./elements#audio) の現在読み込まれているトラックの長さを `MM:SS` 形式で返します。トラックは再生中、停止中、または一時停止中のいずれでもかまいません。

**値:** `element_identifier`

**例:**

```
{"placeholder":"audio_duration","values":{"element_identifier":"background_music"}}
```

**出力:** `03:45`

## オーディオ再生時間 (`audio_playtime`)

**目的:** オーディオトラックの現在の再生時間を返します。`show_percentage` を `"true"` にすると、`MM:SS` の代わりに 0-100 の進行値を返します。

**値:** `element_identifier`, `show_percentage`

**例:**

```
{"placeholder":"audio_playtime","values":{"element_identifier":"background_music","show_percentage":"false"}}
```

**出力:** `01:30`（`show_percentage` が `"true"` の場合は `45`）

**取得できない場合の結果:** `00:00`、またはパーセンテージモードでは `0`。現在値はトラックの再生中または一時停止中に利用できます。停止中、欠落、未準備のトラックでは取得できない場合の結果になります。

## オーディオ再生状態 (`audio_playing_state`)

**目的:** オーディオ要素が再生中かどうか（true/false）を返します。

**値:** `element_identifier`

**例:**

```
{"placeholder":"audio_playing_state","values":{"element_identifier":"background_music"}}
```

**出力:** `true`

## ビデオ要素の音量 (`video_element_vol`)

**目的:** ビデオ要素の音量レベルを返します（0.0 から 1.0）。

**値:** `element_identifier`

**例:**

```
{"placeholder":"video_element_vol","values":{"element_identifier":"my_video_element"}}
```

**出力:** `0.5`

## ビデオ要素の長さ (`video_element_duration`)

**目的:** ビデオ要素の総再生時間を `MM:SS` 形式で返します。ミリ秒のタイムスタンプで返すには `output_as_timestamp` を `"true"` にしてください。

**値:** `element_identifier`, `output_as_timestamp`

**例:**

```
{"placeholder":"video_element_duration","values":{"element_identifier":"my_video_element","output_as_timestamp":"false"}}
```

**出力:** `02:00`（`output_as_timestamp` が `"true"` の場合は `120000`）

## ビデオ要素の再生時間 (`video_element_playtime`)

**目的:** ビデオ要素の現在の再生時間（進行度）を `MM:SS` 形式で返します。0-100 の進行値を返すには `show_percentage` を `"true"` に、ミリ秒で返すには `output_as_timestamp` を `"true"` にしてください。

**値:** `element_identifier`, `show_percentage`, `output_as_timestamp`

**例:**

```
{"placeholder":"video_element_playtime","values":{"element_identifier":"my_video_element","show_percentage":"false","output_as_timestamp":"false"}}
```

**出力:** `00:45`（パーセンテージなら `38`、タイムスタンプなら `45200`）

## ビデオ要素の一時停止状態 (`video_element_paused_state`)

**目的:** ビデオ要素が一時停止中かどうか（true/false）を返します。

**値:** `element_identifier`

**例:**

```
{"placeholder":"video_element_paused_state","values":{"element_identifier":"my_video_element"}}
```

**出力:** `false`

## ビデオ背景の音量 (`video_background_vol`)

**目的:** ビデオメニュー背景の音量レベルを返します（0.0 から 1.0）。

**値:** `background_identifier`

**例:**

```
{"placeholder":"video_background_vol","values":{"background_identifier":"main_menu_video"}}
```

**出力:** `0.7`

## ビデオ背景の長さ (`video_background_duration`)

**目的:** ビデオメニュー背景の総再生時間を `MM:SS` 形式で返します。ミリ秒のタイムスタンプで返すには `output_as_timestamp` を `"true"` にしてください。

**値:** `background_identifier`, `output_as_timestamp`

**例:**

```
{"placeholder":"video_background_duration","values":{"background_identifier":"main_menu_video","output_as_timestamp":"false"}}
```

**出力:** `03:00`（`output_as_timestamp` が `"true"` の場合は `180000`）

## ビデオ背景の再生時間 (`video_background_playtime`)

**目的:** ビデオメニュー背景の現在の再生時間（進行度）を `MM:SS` 形式で返します。0-100 の進行値を返すには `show_percentage` を `"true"` に、ミリ秒で返すには `output_as_timestamp` を `"true"` にしてください。

**値:** `background_identifier`, `show_percentage`, `output_as_timestamp`

**例:**

```
{"placeholder":"video_background_playtime","values":{"background_identifier":"main_menu_video","show_percentage":"false","output_as_timestamp":"false"}}
```

**出力:** `01:00`（パーセンテージなら `33`、タイムスタンプなら `60500`）

## ビデオ背景の一時停止状態 (`video_background_paused_state`)

**目的:** ビデオメニュー背景が一時停止中かどうか（true/false）を返します。

**値:** `background_identifier`

**例:**

```
{"placeholder":"video_background_paused_state","values":{"background_identifier":"main_menu_video"}}
```

**出力:** `true`

## 計算機 (`calc`)

**目的:** 計算機プレースホルダーは、レイアウト内で数式計算を行える強力なツールです。幅広い数学演算をサポートし、小数と整数の両方で動作します。

**値:** `decimal`, `expression`

### 基本構文

**例:**

```
{"placeholder":"calc","values":{"decimal":"true/false","expression":"your_expression"}}
```

計算機には、主に次の 2 つのパラメーターがあります:
- `decimal`: 結果に小数点以下を含めるか（`true`）、整数に丸めるか（`false`）を決定します
- `expression`: 評価する数式

### 対応演算
計算機は次の数学演算をサポートしています:
- 基本四則演算: `+`（加算）、`-`（減算）、`*`（乗算）、`/`（除算）
- 括弧: `( )` によるグループ化
- べき乗: 指数の `^`
- 平方根: `sqrt()`
- 三角関数: `sin()`、`cos()`、`tan()`
- 数学定数: `pi`、`e`
- 絶対値: `abs()`
- 対数: `log()`、`ln()`

## 乱数 (`random_number`)

**目的:** 指定範囲内の乱数を生成します。

**値:** `min`, `max`

**例:**

```
{"placeholder":"random_number","values":{"min":"1","max":"100"}}
```

**出力:** `42`

## 最大値 (`maxnum`)

**目的:** 2 つの数値のうち大きい方を返します。

**値:** `first`, `second`

**例:**

```
{"placeholder":"maxnum","values":{"first":"10","second":"20"}}
```

**出力:** `20`

## 最小値 (`minnum`)

**目的:** 2 つの数値のうち小さい方を返します。

**値:** `first`, `second`

**例:**

```
{"placeholder":"minnum","values":{"first":"10","second":"20"}}
```

**出力:** `10`

## 絶対値 (`absnum`)

**目的:** 数値の絶対値を返します。

**値:** `num`

**例:**

```
{"placeholder":"absnum","values":{"num":"-10.5"}}
```

**出力:** `10.5`

## 数値を負にする (`negnum`)

**目的:** 正の数を負の数にします。0 と、すでに負の値はそのまま返されます。

**値:** `num`

**例:**

```
{"placeholder":"negnum","values":{"num":"10.5"}}
```

**出力:** `-10.5`

## *pi*（数学） (`math_pi`)

**目的:** π の値を返します。

**値:** なし

**例:**

```
{"placeholder":"math_pi"}
```

**出力:** `3.141592653589793`

## 三角関数サイン（数学） (`math_sin`)

**目的:** ラジアン単位の角度の正弦を返します。度数法の値は先にラジアンへ変換してください。

**値:** `angle`

**例:**

```
{"placeholder":"math_sin","values":{"angle":"1.5707963267948966"}}
```

**出力:** `1.0`

## 三角関数コサイン（数学） (`math_cos`)

**目的:** ラジアン単位の角度の余弦を返します。度数法の値は先にラジアンへ変換してください。

**値:** `angle`

**例:**

```
{"placeholder":"math_cos","values":{"angle":"0"}}
```

**出力:** `1.0`

## 三角関数タンジェント（数学） (`math_tan`)

**目的:** ラジアン単位の角度の正接を返します。度数法の値は先にラジアンへ変換してください。

**値:** `angle`

**例:**

```
{"placeholder":"math_tan","values":{"angle":"0"}}
```

**出力:** `0.0`

## 切り捨て（数学） (`math_floor`)

**目的:** 数値の数学的な床関数を返します。結果は `.0` の小数接尾辞付きで書式化されます。

**値:** `num`

**例:**

```
{"placeholder":"math_floor","values":{"num":"3.14"}}
```

**出力:** `3.0`

## 切り上げ（数学） (`math_ceil`)

**目的:** 数値の数学的な天井関数を返します。結果は `.0` の小数接尾辞付きで書式化されます。

**値:** `num`

**例:**

```
{"placeholder":"math_ceil","values":{"num":"3.14"}}
```

**出力:** `4.0`

整数テキストを `.0` なしで使いたい場合は、[**Round**](#round-math-math_round) または、小数出力を無効にした [**Calculator**](#calculator-calc) を使ってください。

## 四捨五入（数学） (`math_round`)

**目的:** 数値を丸めます。既定では最も近い整数に丸めます。`decimals` を 0 以上の数にすると、その桁数まで丸めます。

**値:** `num`, `decimals`

**例:**

```
{"placeholder":"math_round","values":{"num":"3.14159","decimals":"2"}}
```

**出力:** `3.14`（`decimals:-1` または省略 → `3`）

## 符号（数学） (`math_sign`)

**目的:** 数値の符号を返します（正なら 1、負なら -1、0 なら 0）。

**値:** `num`

**例:**

```
{"placeholder":"math_sign","values":{"num":"-3.14"}}
```

**出力:** `-1`

## 双曲線サイン（数学） (`math_sinh`)

**目的:** 数値の双曲線正弦を返します。

**値:** `num`

**例:**

```
{"placeholder":"math_sinh","values":{"num":"1"}}
```

**出力:** `1.1752011936438014`

## 双曲線コサイン（数学） (`math_cosh`)

**目的:** 数値の双曲線余弦を返します。

**値:** `num`

**例:**

```
{"placeholder":"math_cosh","values":{"num":"1"}}
```

**出力:** `1.5430806348152437`

## 双曲線タンジェント（数学） (`math_tanh`)

**目的:** 数値の双曲線正接を返します。

**値:** `num`

**例:**

```
{"placeholder":"math_tanh","values":{"num":"1"}}
```

**出力:** `0.7615941559557649`

## テキスト分割 (`split_text`)

**目的:** 指定した区切り文字でテキストを分割します。

**値:** `input`, `regex`, `max_parts`, `split_index`

**例:**

```
{"placeholder":"split_text","values":{"input":"hello,world","regex":",","max_parts":"2","split_index":"1"}}
```

**出力:** `world`

## テキストのトリム (`trim_text`)

**目的:** 前後の空白を削除します。

**値:** `text`

**例:**

```
{"placeholder":"trim_text","values":{"text":"  hello world  "}}
```

**出力:** `hello world`

## テキストの切り取り (`crop_text`)

**目的:** テキストの先頭と末尾から文字を削除します。

**値:** `text`, `remove_from_start`, `remove_from_end`

**例:**

```
{"placeholder":"crop_text","values":{"text":"hello world","remove_from_start":"1","remove_from_end":"1"}}
```

**出力:** `ello worl`

## 文字列化 (`stringify`)

**目的:** すべての構文文字をエスケープしてテキストを文字列化します。

**値:** `text`

**例:**

```
{"placeholder":"stringify","values":{"text":"text with {special} \"characters\""}}
```

**出力:** `text with \{special\} \"characters\"`

## ローカライズテキスト取得 (`local`)

**目的:** キーに対応するローカライズ済みテキストを取得します。

**値:** `key`

**例:**

```
{"placeholder":"local","values":{"key":"menu.singleplayer"}}
```

**出力:** `Singleplayer`

## Web テキスト (`webtext`)

**目的:** Web URL からテキスト内容を取得します。

**値:** `link`

**例:**

```
{"placeholder":"webtext","values":{"link":"http://somewebsite.com/textfile.txt"}}
```

**出力:** `Welcome to the server!`

## ランダムテキスト (`randomtext`)

**目的:** テキストファイル、URL、または直接入力したプレーンテキストからランダムな行を返します。テキストは指定間隔で切り替わります。ファイルと URL の内容は約 30 秒ごとに更新されます。直接入力のプレーンテキストは再読み込み不要のためキャッシュされたままです。

**値:** `source`, `interval`

プレースホルダーの値では、`/config/...` は `<game-directory>/config/...` を意味します。ファイルシステムのルートパスではありません。[Resources](./resources#local-resources) を参照してください。

**例:**

```
{"placeholder":"randomtext","values":{"source":"/config/fancymenu/assets/<file_name.txt>","interval":"10"}}
```
パラメーター:
- `source`: テキスト行のソース（旧 `path` パラメーターの代わり）
  - ファイルパス: `/config/fancymenu/assets/quotes.txt`
  - URL: `https://example.com/quotes.txt`
  - プレーンテキスト: `Line 1\nLine 2\nLine 3`
- `interval`: テキストが切り替わるまでの秒数

このプレースホルダーは、次の 3 種類のソースに対応しています:
1. **ローカルファイル**: ゲームディレクトリ内のテキストファイル
   ```
   {"placeholder":"randomtext","values":{"source":"/config/fancymenu/assets/quotes.txt","interval":"10"}}
   ```
2. **URL**: インターネット上のリモートテキストファイル
   ```
   {"placeholder":"randomtext","values":{"source":"https://example.com/quotes.txt","interval":"10"}}
   ```
3. **プレーンテキスト**: `\n` で区切られた直接入力テキスト
   ```
   {"placeholder":"randomtext","values":{"source":"First line\nSecond line\nThird line","interval":"5"}}
   ```

注: `source` の代わりに `path` を使っている古いプレースホルダーも引き続き動作します。

## JSON パーサー (`json`)

**目的:** ファイル、URL、または直接入力の JSON からデータを解析し、JSON パス式を使って値を抽出します。

**値:** `source`, `json_path`

**例:**

```
{"placeholder":"json","values":{"source":"path_or_link_or_json_content","json_path":"$.some.json.path"}}
```
パラメーター:
- `source`: JSON データのソース
  - ファイルパス: `/config/fancymenu/assets/data.json`
  - URL: `https://api.example.com/data.json`
  - 直接 JSON: `{"name":"Steve","level":42}`
- `json_path`: データを抽出する JSON パス式

このプレースホルダーは、次の 3 種類のソースに対応しています:
1. **ローカルファイル**: ゲームディレクトリ内の JSON ファイル
   ```
   {"placeholder":"json","values":{"source":"/config/fancymenu/assets/playerdata.json","json_path":"$.player.name"}}
   ```
2. **URL**: API や Web サービスからのリモート JSON データ
   ```
   {"placeholder":"json","values":{"source":"https://api.minecraft.com/server/status","json_path":"$.online"}}
   ```
3. **直接 JSON**: インラインの JSON コンテンツ
   ```
   {"placeholder":"json","values":{"source":"{"name":"Steve","score":42,"rank":"Diamond"}","json_path":"$.rank"}}
   ```

JSON パスの例:
- `$.name` - ルートから「name」フィールドを取得
- `$.player.level` - 「player」内のネストされた「level」フィールドを取得
- `$.items[0].id` - 配列の最初の要素の「id」を取得
- `$.scores.*` - 「scores」オブジェクトのすべての値を取得

## 絶対ファイル/フォルダパス (`absolute_path`)

**目的:** ファイルの絶対パスを返します。

**値:** `short_path`

**例:**

```
{"placeholder":"absolute_path","values":{"short_path":"relative/path/to/file.txt"}}
```

**出力:** `C:/Games/PrismLauncher/instances/My Pack/relative/path/to/file.txt`

## テキスト文字数 (`text_character_count`)

**目的:** 指定されたテキストの文字数を返します。

**値:** `text`

**例:**

```
{"placeholder":"text_character_count","values":{"text":"Hello World!"}}
```

**出力:** `12`

## テキスト幅 (`text_width`)

**目的:** 描画時の指定テキストの幅をピクセル単位で返します。

**値:** `text`

**例:**

```
{"placeholder":"text_width","values":{"text":"Hello World!"}}
```

**出力:** `66`

## 文字列を大文字に (`uppercase_text`)

**目的:** 入力テキストをすべて大文字に変換します。

**値:** `text`

**例:**

```
{"placeholder":"uppercase_text","values":{"text":"Hello World"}}
```

**出力:** `HELLO WORLD`

## 文字列を小文字に (`lowercase_text`)

**目的:** 入力テキストをすべて小文字に変換します。

**値:** `text`

**例:**

```
{"placeholder":"lowercase_text","values":{"text":"Hello World"}}
```

**出力:** `hello world`

## 文字列をタイトルケースに (`title_case_text`)

**目的:** 入力テキストをタイトルケースに変換します。

**値:** `text`

**例:**

```
{"placeholder":"title_case_text","values":{"text":"hello world"}}
```

**出力:** `Hello World`

## 文字列を文頭のみ大文字に (`sentence_case_text`)

**目的:** 入力テキストを文頭のみ大文字に変換します。

**値:** `text`

**例:**

```
{"placeholder":"sentence_case_text","values":{"text":"hello world. this is fancymenu!"}}
```

**出力:** `Hello world. This is fancymenu!`

## 文字列をスネークケースに (`snake_case_text`)

**目的:** 入力テキストを `snake_case` に変換します。

**値:** `text`

**例:**

```
{"placeholder":"snake_case_text","values":{"text":"Hello World"}}
```

**出力:** `hello_world`

## 文字列をケバブケースに (`kebab_case_text`)

**目的:** 入力テキストを `kebab-case` に変換します。

**値:** `text`

**例:**

```
{"placeholder":"kebab_case_text","values":{"text":"Hello World"}}
```

**出力:** `hello-world`

## 文字列を交互大小文字に (`alternating_case_text`)

**目的:** 入力テキストを交互の大小文字に変換します。

**値:** `text`

**例:**

```
{"placeholder":"alternating_case_text","values":{"text":"alternating case"}}
```

**出力:** `aLtErNaTiNg CaSe`

## 文字列の大文字小文字を反転 (`toggle_case_text`)

**目的:** 入力テキストの各文字の大文字小文字を反転します。

**値:** `text`

**例:**

```
{"placeholder":"toggle_case_text","values":{"text":"Toggle Case"}}
```

**出力:** `tOGGLE cASE`

## Base64 にエンコード (`base64_encode`)

**目的:** 指定テキストを Base64 としてエンコードします。

**値:** `text`

**例:**

```
{"placeholder":"base64_encode","values":{"text":"Hello World"}}
```

**出力:** `SGVsbG8gV29ybGQ=`

## Base64 からデコード (`base64_decode`)

**目的:** Base64 文字列をプレーンテキストにデコードします。

**値:** `text`

**例:**

```
{"placeholder":"base64_decode","values":{"text":"SGVsbG8gV29ybGQ="}}
```

**出力:** `Hello World`

## ファイルテキスト (`file_text`)

**目的:** ファイルまたは URL からテキスト行を返します。すべての行、または最後の X 行のみを返せます。

**値:** `path_or_url`, `mode`, `separator`, `last_lines`

**例:**

```
{"placeholder":"file_text","values":{"path_or_url":"/config/fancymenu/assets/some_file.txt","mode":"all","separator":"\n","last_lines":"1"}}
```
パラメーター:
- `path_or_url`: 読み取り元のファイルパスまたは URL
- `mode`: `"all"`（すべての行を返す）または `"last"`（最後の X 行のみ返す）
- `separator`: 行の間に使う文字列（既定: `"\n"`）
- `last_lines`: `mode` が `"last"` のときに返す行数（既定: `"1"`）

**出力:**

```text
First line
Second line
```

## クリップボードの内容 (`clipboard_content`)

**目的:** システムのクリップボードに保存されている現在のテキスト内容を返します。

**値:** なし

**例:**

```
{"placeholder":"clipboard_content"}
```

**出力:** `Hello from the clipboard`

## テキスト置換 (`replace_text`)

**目的:** 文字列内のテキストを、リテラル文字列または正規表現で置き換えます。

**値:** `text`, `search`, `replacement`, `use_regex`, `replace_all`

**例:**

```
{"placeholder":"replace_text","values":{"text":"Hello World! This is a test.","search":"World","replacement":"FancyMenu","use_regex":"false","replace_all":"true"}}
```
パラメーター:
- `text`: 処理対象の入力テキスト
- `search`: 検索する文字列または正規表現パターン
- `replacement`: 置換後の文字列
- `use_regex`: 正規表現を使うかどうか（`"true"`）またはリテラル一致か（`"false"`）
- `replace_all`: すべて置換するか（`"true"`）、最初の 1 件だけにするか（`"false"`）

**出力:** `Hello FancyMenu! This is a test.`

## スイッチケース (`switch_case`)

**目的:** 値に基づいて switch-case 処理を行います。

**値:** `value`, `cases`, `default`

**例:**

```
{"placeholder":"switch_case","values":{"value":"1","cases":"1:first case,2:second case,3:third case","default":"default case"}}
```

**出力:** `first case`（value が 1 の場合）

## 変数の値を取得（FM 変数） (`getvariable`)

**目的:** 以前に保存した変数の値を取得します。

**値:** `name`

**例:**

```
{"placeholder":"getvariable","values":{"name":"some_variable"}}
```

**出力:** `42`

## NBT データを取得 (`nbt_data_get`)

**目的:** クライアント側で NBT データを取得します（`/data get` コマンドに似ています）。サーバー接続中に、サーバー側の確定値が必要な場合は、サーバー版の `nbt_data_get_server` を使ってください。

**値:** `source_type`, `entity_selector`, `nbt_path`, `scale`, `return_type`

**例:**

```
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"foodLevel","scale":"1.0","return_type":"value"}}
```
パラメーター:
- `source_type`: `"entity"` または `"block"`
- `entity_selector`: `@s`、`@p`、`@e`、UUID/名前などのエンティティセレクター（エンティティ用）
- `block_pos`: ブロック位置の形式 `"x y z"`（ブロック用）
- `nbt_path`: 取得する NBT パス
- `scale`: 数値に適用する任意のスケール係数（既定: `"1.0"`）
- `return_type`: データの返し方:
  - `"value"`: 既定。値を返します（数値には任意でスケーリング適用）
  - `"string"`: 実際の NBT データを文字列で返します
  - `"snbt"`: SNBT（整形済み NBT）として返します
  - `"json"`: JSON 形式のコンポーネントとして返します（compound タグ用）

**出力:** `20`（food level の場合）

## NBT データを取得（サーバー側） (`nbt_data_get_server`)

**目的:** パケットを使ってサーバー側の NBT データを問い合わせ、結果を短時間キャッシュします。値はクライアント側プレースホルダーと同じです。

**値:** `source_type`, `entity_selector`, `block_pos`, `storage_id`, `nbt_path`, `scale`, `return_type`

**例:**

```
{"placeholder":"nbt_data_get_server","values":{"source_type":"entity","entity_selector":"@s","block_pos":"","storage_id":"minecraft:storage_key","nbt_path":"SelectedItem.id","scale":"1.0","return_type":"value"}}
```

**出力:** `minecraft:diamond_sword`

## 最後の死亡メッセージ (`lastdeathmessage`)

**目的:** クライアントプレイヤーの最後に記録された死亡メッセージを返します。生の JSON テキストコンポーネントを取得するには `as_json_component` を `"true"` にしてください。

**値:** `as_json_component`

**例:**

```
{"placeholder":"lastdeathmessage","values":{"as_json_component":"false"}}
```

**出力:** `Steve was slain by Zombie`

## 稼働時間 (`uptime_duration`)

**目的:** FancyMenu が読み込まれてからの経過時間を返します。既定では秒単位です。ミリ秒で受け取るには `output_as_millis` を `"true"` にしてください。

**値:** `output_as_millis`

**例:**

```
{"placeholder":"uptime_duration","values":{"output_as_millis":"false"}}
```

**出力:** `742`（読み込み後の秒数）

## ワールドセーブ名 (`level_save_names`)

**目的:** ローカルのワールドセーブ名を、選択した区切り文字で連結して一覧表示します。クライアントスレッドで実行されます。

**値:** `separator`

**例:**

```
{"placeholder":"level_save_names","values":{"separator":", "}}
```

**出力:** `Creative Test, Survival World, Hardcore`

## ワールドセーブデータ (`level_save_data`)

**目的:** 指定したワールド名のシリアライズ済みレベルデータを返します（セーブ一覧に表示される表示名と一致している必要があります）。

**値:** `level_name`

**例:**

```
{"placeholder":"level_save_data","values":{"level_name":"Survival World"}}
```

**出力:** `{"name":"Survival World","gameMode":"survival",...}`

## 数値基数変換 (`number_base_convert`)

**目的:** 数値（整数または小数）をある基数から別の基数へ変換します（2〜36）。基数が指定されていない場合は 10 進数を既定とします。

**値:** `input`, `from_base`, `to_base`

**例:**

```
{"placeholder":"number_base_convert","values":{"input":"67.5","from_base":"10","to_base":"16"}}
```

**出力:** `43.8`

## ファイルサイズ (`file_size`)

**目的:** ローカルファイルのサイズをバイト単位で返します。ローカルパスのみ使用できます。

**値:** `path`

**例:**

```
{"placeholder":"file_size","values":{"path":"/config/fancymenu/assets/notes.txt"}}
```

**出力:** `1284`

## ファイル MD5 (`file_md5`)

**目的:** ローカルファイルの MD5 ハッシュを小文字の 16 進文字列で返します。

**値:** `path`

**例:**

```
{"placeholder":"file_md5","values":{"path":"/config/fancymenu/assets/notes.txt"}}
```

**出力:** `d41d8cd98f00b204e9800998ecf8427e`

# 実践例

## 動的なメモリ表示の作成
```
使用中 RAM: {"placeholder":"usedram"}MB / {"placeholder":"maxram"}MB ({"placeholder":"percentram"}%)
```

## リアルタイム時計の作成
```
{"placeholder":"realtimehour","values":{"timezone":"system"}}:{"placeholder":"realtimeminute","values":{"timezone":"system"}}:{"placeholder":"realtimesecond","values":{"timezone":"system"}}
```

## システム情報表示の作成
```
OS: {"placeholder":"osname"}
CPU: {"placeholder":"cpuinfo"}
GPU: {"placeholder":"gpuinfo"}
Java: {"placeholder":"javaver"}
```

## プレイヤー状態 HUD
```
体力: {"placeholder":"current_player_health"} / {"placeholder":"max_player_health"} ({"placeholder":"current_player_health_percent"}%)
防具: {"placeholder":"current_player_armor"} / {"placeholder":"max_player_armor"}
XP レベル: {"placeholder":"current_player_level"}
```

## ネストされたプレースホルダーを使った複雑な計算
```
{"placeholder":"calc","values":{"decimal":"true","expression":"({"placeholder":"usedram"} / {"placeholder":"maxram"}) * 100"}}
```

## 四捨五入付きの座標表示
```
X: {"placeholder":"math_round","values":{"num":"{"placeholder":"player_x_coordinate"}"}}
Y: {"placeholder":"math_round","values":{"num":"{"placeholder":"player_y_coordinate"}"}}
Z: {"placeholder":"math_round","values":{"num":"{"placeholder":"player_z_coordinate"}"}}
```

# ベストプラクティス

1. **重い処理はキャッシュする**: 一部のプレースホルダー（システム情報を読み取るものなど）は、負荷が高い場合があります。複数回使うなら、変数に保存して使い回すことを検討してください。

2. **適切な小数設定を使う**: 計算を行うときは、`decimal` パラメーターを適切に使ってください。整数が必要なら `false`、正確な小数値が必要なら `true` に設定します。

3. **欠損値を考慮する**: プレースホルダーが値を返さない場合にどうするか、常に考慮してください。そのような場合は、既定値を用意するとよいでしょう。

4. **パフォーマンスをテストする**: 多数のプレースホルダーや複雑なネスト構造を使う場合は、特に低スペック環境で性能への影響を確認してください。

5. **高度なサイズ/配置を活用する**: 動的な UI 要素では、プレースホルダーと高度なサイズ調整・配置を組み合わせて、レスポンシブなレイアウトを作成してください。

6. **変数と組み合わせる**: プレースホルダーを変数と併用すると、アクションで更新できるさらに動的なコンテンツを作れます。

# よくある問題と解決策

## プレースホルダーが更新されない
プレースホルダーの値が期待どおりに更新されない場合は、次を確認してください:
- プレースホルダーの形式が正しいか
- プレースホルダー ID の大文字小文字が正しいか
- そのプレースホルダーに、更新に必要な特定条件があるか

## ネストされたプレースホルダーが動作しない
プレースホルダーをネストする場合は:
-  उद्ध? Ensure proper escaping of quotes  
- 各ネストされたプレースホルダーが、それ単体でも有効であることを確認する

## パフォーマンス問題
パフォーマンスに問題がある場合は:
- 使用するプレースホルダーの数を減らす
- 不要なネストを避ける
- よく使う値には変数の使用を検討する
- 必要に合った適切なプレースホルダーを使う（たとえば、静的な値で足りるならリアルタイム系プレースホルダーは使わない）
