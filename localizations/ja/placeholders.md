---
title: プレースホルダー
description: プレースホルダーの使い方。
---

# プレースホルダー

プレースホルダーは、使用時に実際の内容へ置き換えられる動的な値です。FancyMenu では、プレースホルダーを使うことで、テキスト、ボタン、読み込み条件など、さまざまな要素に動的な内容を挿入できます。レイアウトが表示されるときに評価され、実際の値に置き換わる変数のようなものだと考えてください。

# 基本情報

## 基本構文
FancyMenu のプレースホルダーは、JSON 風の構文を使用します:
```
{"placeholder":"modversion","values":{"modid":"fancymenu"}}
```

たとえば、プレイヤー名を表示するには:
```
{"placeholder":"playername"}
```

## プレースホルダーのネスト
FancyMenu のプレースホルダーシステムの最も強力な機能の 1 つが、他のプレースホルダー内にプレースホルダーを入れ子にできることです。つまり、あるプレースホルダーの出力を別のプレースホルダーの入力として使えます。

ネストされたプレースホルダーの例:
```
{"placeholder":"calc","values":{"decimal":"true","expression":"{"placeholder":"maxram"} / 1024"}}
```
この例では、最大 RAM の値を 1024 で割って、MB を GB に変換しています。

# プレースホルダーの使用

テキスト入力を持つほとんどの要素は、プレースホルダーをサポートしています。編集時に、そのテキスト入力がプレースホルダーに対応しているか確認できます。テキスト編集中に全画面の**テキストエディタ**が開く場合、その入力はプレースホルダーに対応しています。

**すべてのプレースホルダーの一覧**を表示するには、**テキストエディタ**の**右上**にある**Placeholders**ボタンをクリックしてください。

プレースホルダー一覧の上部には**検索バー**があり、プレースホルダーを検索できます。

一覧内のプレースホルダーをクリックすると、そのプレースホルダーがテキスト内容に貼り付けられます。

# 詳細なプレースホルダー一覧

この一覧には、FancyMenu で利用できるプレースホルダーのほとんど、場合によってはすべてが含まれています。MOD の更新により、一覧が少し古くなることがあります。

## プレイヤー名 (playername)
現在のプレイヤーのユーザー名を返します。
```
{"placeholder":"playername"}
```
出力例: `Steve`

## プレイヤー UUID (playeruuid)
プレイヤーの一意の識別子を返します。
```
{"placeholder":"playeruuid"}
```
出力例: `c8cde7fe-7ced-11eb-9439-0242ac130002`

## Minecraft バージョン (mcversion)
現在の Minecraft バージョンを返します。
```
{"placeholder":"mcversion"}
```
出力例: `1.19.2`

## MOD ローダーのバージョン (loaderver)
MOD ローダー（Forge/Fabric）のバージョンを返します。
```
{"placeholder":"loaderver"}
```
出力例: `43.2.0`

## MOD ローダー名 (loadername)
MOD ローダーの名前を返します。
```
{"placeholder":"loadername"}
```
出力例: `Forge`

## MOD バージョン (modversion)
特定の MOD のバージョンを返します。
```
{"placeholder":"modversion","values":{"modid":"fancymenu"}}
```
出力例: `2.14.9`

## インストール済み MOD の総数 (totalmods)
インストールされている MOD の総数を返します。
```
{"placeholder":"totalmods"}
```
出力例: `45`

## 読み込まれている MOD の数 (loadedmods)
現在読み込まれている MOD の数を返します。
```
{"placeholder":"loadedmods"}
```
出力例: `43`

## ワールド読み込み進行状況 (world_load_progress)
現在のワールド読み込み進行状況をパーセンテージで返します。
```
{"placeholder":"world_load_progress"}
```
出力例: `75`

## Minecraft オプションの値 (minecraft_option_value)
Minecraft のオプション値を返します。
```
{"placeholder":"minecraft_option_value","values":{"name":"fov"}}
```
出力例: `70`

## 最後に開いたワールドまたはサーバー (last_world_server)
最後にアクセスしたワールドまたはサーバーに関する情報を返します。
```
{"placeholder":"last_world_server","values":{"type":"both","full_world_path":"true"}}
```
パラメータ:
- `type`: 返す情報の種類を決定します
  - `"both"`: 最後にアクセスしたワールドまたはサーバーを返します（既定）
  - `"server"`: 最後にアクセスしたものがサーバーの場合のみ返します
  - `"world"`: 最後にアクセスしたものがワールドの場合のみ返します
- `full_world_path`: ワールドパスの表示方法を制御します
  - `"true"`: 完全なワールドパスを返します（既定）
  - `"false"`: パスなしのワールド名のみを返します（サーバーには影響しません）

例:
- サーバー: `mc.hypixel.net`
- 完全パス付きのワールド: `saves/New World`
- 完全パスなしのワールド: `New World`

## 画面幅 (guiwidth)
現在の画面幅を返します。
```
{"placeholder":"guiwidth"}
```
出力例: `1920`

## 画面高さ (guiheight)
現在の画面高さを返します。
```
{"placeholder":"guiheight"}
```
出力例: `1080`

## 現在の画面識別子 (screenid)
現在の画面の識別子を返します。
```
{"placeholder":"screenid"}
```
出力例: `title_screen`

## 要素の幅 (elementwidth)
特定の要素の幅を返します。
```
{"placeholder":"elementwidth","values":{"id":"my_button"}}
```
出力例: `200`

## 要素の高さ (elementheight)
特定の要素の高さを返します。
```
{"placeholder":"elementheight","values":{"id":"my_button"}}
```
出力例: `20`

## 要素の X 座標 (elementposx)
特定の要素の X 座標を返します。
```
{"placeholder":"elementposx","values":{"id":"my_button"}}
```
出力例: `150`

## 要素の Y 座標 (elementposy)
特定の要素の Y 座標を返します。
```
{"placeholder":"elementposy","values":{"id":"my_button"}}
```
出力例: `100`

## マウスの X 座標 (mouseposx)
現在のマウスの X 座標を返します。
```
{"placeholder":"mouseposx"}
```
出力例: `960`

## マウスの Y 座標 (mouseposy)
現在のマウスの Y 座標を返します。
```
{"placeholder":"mouseposy"}
```
出力例: `540`

## 1 秒あたりのクリック数 (clicks_per_second)
マウスボタンの現在の 1 秒あたりのクリック数を返します。
```
{"placeholder":"clicks_per_second","values":{"mouse_button":"left"}}
```
パラメータ:
- `mouse_button`: `left` または `right`

出力例: `8`

## GUI スケール (guiscale)
現在の GUI スケールを返します。
```
{"placeholder":"guiscale"}
```
出力例: `2`

## Vanilla ウィジェットのラベル/テキスト (vanillabuttonlabel)
Vanilla のウィジェット/ボタンのラベルまたはテキストを返します。
```
{"placeholder":"vanillabuttonlabel","values":{"locator":"some.menu.identifier:505280"}}
```
出力例: `Options...`

## テキスト入力欄の値 (text_input_field_value)
要素識別子で、カスタムまたは Vanilla のテキスト入力欄の現在値を返します。
```
{"placeholder":"text_input_field_value","values":{"element_identifier":"my_input"}}
```
出力例: `Hello World`

## 現在のプレイヤーの体力 (current_player_health)
プレイヤーの現在の体力を返します。
```
{"placeholder":"current_player_health"}
```
出力例: `20.0`

## 最大プレイヤー体力 (max_player_health)
プレイヤーの最大体力を返します。
```
{"placeholder":"max_player_health"}
```
出力例: `20.0`

## 現在のプレイヤー体力（割合）(current_player_health_percent)
プレイヤーの体力をパーセンテージで返します。
```
{"placeholder":"current_player_health_percent"}
```
出力例: `100`

## 現在のプレイヤーの吸収体力 (current_player_absorption_health)
プレイヤーの吸収体力（金のハート）を返します。
```
{"placeholder":"current_player_absorption_health"}
```
出力例: `4.0`

## 最大プレイヤー吸収体力 (max_player_absorption_health)
最大吸収体力を返します。
```
{"placeholder":"max_player_absorption_health"}
```
出力例: `4.0`

## 現在のプレイヤー吸収体力（割合）(current_player_absorption_health_percent)
プレイヤーの吸収体力をパーセンテージで返します。
```
{"placeholder":"current_player_absorption_health_percent"}
```
出力例: `100`

## 現在のプレイヤーの満腹度 (current_player_hunger)
プレイヤーの現在の満腹度を返します。
```
{"placeholder":"current_player_hunger"}
```
出力例: `20`

## 最大プレイヤー満腹度 (max_player_hunger)
最大満腹度を返します。
```
{"placeholder":"max_player_hunger"}
```
出力例: `20`

## 現在のプレイヤー満腹度（割合）(current_player_hunger_percent)
プレイヤーの満腹度をパーセンテージで返します。
```
{"placeholder":"current_player_hunger_percent"}
```
出力例: `100`

## 現在のプレイヤーの満腹度飽和値 (current_player_hunger_saturation)
プレイヤーの現在の満腹度飽和値を返します。
```
{"placeholder":"current_player_hunger_saturation"}
```
出力例: `5.0`

## 現在のプレイヤーの防具値 (current_player_armor)
プレイヤーの現在の防具値を返します。
```
{"placeholder":"current_player_armor"}
```
出力例: `20`

## プレイヤーの防具耐久補正 (player_armor_toughness)
プレイヤーの合計防具耐久補正値を返します。
```
{"placeholder":"player_armor_toughness"}
```
出力例: `8.0`

## 最大プレイヤー防具値 (max_player_armor)
最大防具値を返します。
```
{"placeholder":"max_player_armor"}
```
出力例: `20`

## 現在のプレイヤー防具値（割合）(current_player_armor_percent)
プレイヤーの防具値をパーセンテージで返します。
```
{"placeholder":"current_player_armor_percent"}
```
出力例: `100`

## 現在のプレイヤー酸素レベル (current_player_oxygen)
プレイヤーの現在の酸素レベル（空気泡）を返します。
```
{"placeholder":"current_player_oxygen"}
```
出力例: `300`

## 最大プレイヤー酸素レベル (max_player_oxygen)
最大酸素レベルを返します。
```
{"placeholder":"max_player_oxygen"}
```
出力例: `300`

## 現在のプレイヤー酸素レベル（割合）(current_player_oxygen_percent)
プレイヤーの酸素レベルをパーセンテージで返します。
```
{"placeholder":"current_player_oxygen_percent"}
```
出力例: `100`

## 現在のプレイヤーレベル (current_player_level)
プレイヤーの現在の経験値レベルを返します。
```
{"placeholder":"current_player_level"}
```
出力例: `30`

## 現在のプレイヤー経験値 (current_player_exp)
プレイヤーの合計経験値を返します。
```
{"placeholder":"current_player_exp"}
```
出力例: `1250`

## プレイヤー経験値進行度（割合）(current_player_exp_progress)
次のレベルまでのプレイヤーの経験値進行度をパーセンテージで返します。
```
{"placeholder":"current_player_exp_progress"}
```
出力例: `75`

## プレイヤーの攻撃力（割合）(player_attack_strength)
プレイヤーの攻撃クールダウンをパーセンテージで返します。
```
{"placeholder":"player_attack_strength"}
```
出力例: `100`

## プレイヤーのゲームモード (player_gamemode)
プレイヤーの現在のゲームモードを返します。
```
{"placeholder":"player_gamemode"}
```
出力例: `survival`

## プレイヤーの向いている方向 (player_view_direction)
プレイヤーが向いている方向を返します。
```
{"placeholder":"player_view_direction"}
```
出力例: `north`

## プレイヤーの X 座標 (player_x_coordinate)
ワールド内のプレイヤーの X 位置を返します。
```
{"placeholder":"player_x_coordinate"}
```
出力例: `125`

## プレイヤーの Y 座標 (player_y_coordinate)
ワールド内のプレイヤーの Y 位置を返します。
```
{"placeholder":"player_y_coordinate"}
```
出力例: `64`

## プレイヤーの Z 座標 (player_z_coordinate)
ワールド内のプレイヤーの Z 位置を返します。
```
{"placeholder":"player_z_coordinate"}
```
出力例: `-250`

## 現在の乗り物の体力 (current_mount_health)
プレイヤーが乗っているエンティティの現在の体力を返します。
```
{"placeholder":"current_mount_health"}
```
出力例: `30.0`

## 最大乗り物体力 (max_mount_health)
プレイヤーが乗っているエンティティの最大体力を返します。
```
{"placeholder":"max_mount_health"}
```
出力例: `30.0`

## 現在の乗り物の体力（割合）(current_mount_health_percent)
乗り物の体力をパーセンテージで返します。
```
{"placeholder":"current_mount_health_percent"}
```
出力例: `100`

## 現在の乗り物ジャンプメーター（割合）(current_mount_jump_meter)
乗り物のジャンプ力メーター値を返します。
```
{"placeholder":"current_mount_jump_meter"}
```
出力例: `75`

## 現在のボスの体力（割合）(current_boss_health)
アクティブなボスの体力を返します。
```
{"placeholder":"current_boss_health"}
```
出力例: `150.0`

## ボス名 (boss_name)
アクティブなボスの名前を返します。
```
{"placeholder":"boss_name","values":{"boss_index":"0","as_json":"false"}}
```
出力例: `Ender Dragon`

## ボスの数 (boss_count)
アクティブなボスの数を返します。
```
{"placeholder":"boss_count"}
```
出力例: `1`

## アクティブな効果数 (effects_count)
有効なポーション効果の数を返します。
```
{"placeholder":"effects_count"}
```
出力例: `3`

## アクティブな効果 (active_effect)
特定の有効な効果に関する情報を返します。
```
{"placeholder":"active_effect","values":{"effect_index":"0"}}
```
出力例: `minecraft:speed`

## 選択中のホットバースロット (active_hotbar_slot)
現在選択されているホットバースロット（0-8）を返します。
```
{"placeholder":"active_hotbar_slot"}
```
出力例: `4`

## スロット内アイテム (slot_item)
特定のインベントリスロット内のアイテムに関する情報を返します。
```
{"placeholder":"slot_item","values":{"slot":"0"}}
```
出力例: `minecraft:diamond_sword`

## スロット内アイテム数 (slot_item_count)
特定のプレイヤーインベントリスロット内のアイテムスタック数を返します。
```
{"placeholder":"slot_item_count","values":{"slot":"0"}}
```
出力例: `64`

## スロット内アイテム耐久値 (slot_item_durability)
特定のプレイヤーインベントリスロット内のアイテムの耐久値情報を返します。
```
{"placeholder":"slot_item_durability","values":{"slot":"0","format":"percentage"}}
```
パラメータ:
- `slot`: プレイヤーインベントリのスロット番号。
- `format`: `current`、`remaining`、`max`、`damage`、`percentage`、`percent` のいずれか。

出力例: `87`

## スロット内アイテムの表示名 (slot_item_display_name_fm)
特定のスロット内アイテムの表示名を JSON テキストコンポーネントとして返します。スペクテイターモードでは、`ignore_spectator` が `true` でない限り、ホットバースロットがスペクテイターメニューのアイテム名として解決される場合があります。
```
{"placeholder":"slot_item_display_name_fm","values":{"slot":"0","ignore_spectator":"false"}}
```
出力例: `{"text":"Diamond Sword","color":"aqua"}`

## インベントリ内アイテム数 (inventory_item_count)
プレイヤーインベントリ内の、指定したアイテム種別の合計数を返します。`item` が空の場合は、インベントリ内のすべてのアイテムスタック数を数えます。
```
{"placeholder":"inventory_item_count","values":{"item":"minecraft:diamond"}}
```
出力例: `12`

## インベントリスロットの食料回復量 (inventory_slot_food_point_restore_amount)
指定したプレイヤーインベントリスロットにある食料アイテムが回復する満腹度を返します。
```
{"placeholder":"inventory_slot_food_point_restore_amount","values":{"slot":"0"}}
```
出力例: `4.0`

## ホバー中のインベントリアイテム (hovered_inventory_item)
インベントリ画面で現在ホバーしているアイテムのキーを返します。
```
{"placeholder":"hovered_inventory_item"}
```
出力例: `minecraft:apple`

## ワールドのゲーム時間 (game_time)
現在のゲーム内時間ティックカウンターを返します。
```
{"placeholder":"game_time"}
```
出力例: `18000`

## ワールドの時刻 (world_daytime)
現在のワールド時刻を返します。
```
{"placeholder":"world_daytime"}
```
出力例: `13000`

## ワールド時刻の時 (world_daytime_hour)
ワールド時刻の時を返します。既定では 24 時間形式を使用します。12 時間形式にするには `twelve_hour_format` を `"true"` に設定してください。
```
{"placeholder":"world_daytime_hour","values":{"twelve_hour_format":"false"}}
```
出力例: `12`

## ワールド時刻の分 (world_daytime_minute)
ワールド時刻の分（00-59）を返します。
```
{"placeholder":"world_daytime_minute"}
```
出力例: `30`

## ワールドの難易度 (world_difficulty)
現在のワールドの難易度を返します。
```
{"placeholder":"world_difficulty"}
```
出力例: `normal`

## 現在のワールドシード (current_world_seed)
シングルプレイワールドのシードを返します。シードが利用できない場合は空の値を返します。
```
{"placeholder":"current_world_seed"}
```
出力例: `123456789`

## 現在のバイオーム (current_biome)
プレイヤーが現在いるバイオームを返します。利用可能な場合は翻訳済み/表示名を返すには `as_key` を `"false"` に設定してください。
```
{"placeholder":"current_biome","values":{"as_key":"true"}}
```
出力例: `minecraft:plains`

## 現在のディメンション (current_dimension)
プレイヤーが現在いるディメンションを返します。利用可能な場合は翻訳済み/表示名を返すには `as_key` を `"false"` に設定してください。
```
{"placeholder":"current_dimension","values":{"as_key":"true"}}
```
出力例: `minecraft:overworld`

## ゲームルールの値 (gamerule_value)
読み込まれているワールド/サーバー内のゲームルールの現在値を返します。サーバーワールドでは、サーバー側に FancyMenu が必要です。
```
{"placeholder":"gamerule_value","values":{"name":"doDaylightCycle"}}
```
出力例: `true`

## アイテムカテゴリ (item_category)
アイテムのクリエイティブタブカテゴリを返します。カテゴリ名ではなくカテゴリキーを返すには `as_key` を `"true"` に設定してください。
```
{"placeholder":"item_category","values":{"item":"minecraft:diamond_sword","as_key":"false"}}
```
出力例: `Combat`

## 現在の HUD タイトル/サブタイトル (current_title)
現在表示されているタイトルテキストを返します。
```
{"placeholder":"current_title","values":{"is_subtitle":"false","as_json":"false"}}
```
出力例: `Game Over!`

## アクションバーのメッセージ (action_bar_message_fm)
ホットバーの上にある Vanilla の現在のアクションバーメッセージを返します。
```
{"placeholder":"action_bar_message_fm"}
```
出力例: `You may not rest now`

## アクションバーメッセージの表示時間 (action_bar_message_time_fm)
現在の Vanilla のアクションバーメッセージがあと何ティック表示されるかを返します。
```
{"placeholder":"action_bar_message_time_fm"}
```
出力例: `42`

## カメラ回転 X (camera_rotation_x_fm)
現在のカメラのピッチを度数で返します。
```
{"placeholder":"camera_rotation_x_fm"}
```
出力例: `12.5`

## カメラ回転 Y (camera_rotation_y_fm)
現在のカメラのヨーを度数で返します。
```
{"placeholder":"camera_rotation_y_fm"}
```
出力例: `-90.0`

## カメラ回転の変化量 X (camera_rotation_delta_x_fm)
1 ティックあたりのカメラピッチの変化を返します。
```
{"placeholder":"camera_rotation_delta_x_fm"}
```
出力例: `0.4`

## カメラ回転の変化量 Y (camera_rotation_delta_y_fm)
1 ティックあたりのカメラヨーの変化を返します。
```
{"placeholder":"camera_rotation_delta_y_fm"}
```
出力例: `-1.2`

## ハイライト中のアイテム表示時間 (highlighted_item_time_fm)
ホットバーの上にアイテム名があと何ティック表示されるかを返します。
```
{"placeholder":"highlighted_item_time_fm"}
```
出力例: `30`

## プレイヤーのアイテム使用進行度 (player_item_use_progress_fm)
現在のアイテム使用進行度を `0.0` から `1.0` の範囲で返します。
```
{"placeholder":"player_item_use_progress_fm"}
```
出力例: `0.65`

## プレイヤー位置の変化量 X (player_position_delta_x_fm)
1 ティックあたりのプレイヤー位置の X 軸変化を返します。
```
{"placeholder":"player_position_delta_x_fm"}
```
出力例: `0.0`

## プレイヤー位置の変化量 Y (player_position_delta_y_fm)
1 ティックあたりのプレイヤー位置の Y 軸変化を返します。
```
{"placeholder":"player_position_delta_y_fm"}
```
出力例: `-0.08`

## プレイヤー位置の変化量 Z (player_position_delta_z_fm)
1 ティックあたりのプレイヤー位置の Z 軸変化を返します。
```
{"placeholder":"player_position_delta_z_fm"}
```
出力例: `0.12`

## 現在のサーバー IP (current_server_ip)
接続中のサーバーの IP を返します。
```
{"placeholder":"current_server_ip"}
```
出力例: `mc.hypixel.net`

## ワールド内プレイヤー一覧 (world_players_list)
現在ワールド内にいるすべてのプレイヤーの一覧を返します。
```
{"placeholder":"world_players_list","values":{"separator":", "}}
```
出力例: `Steve, Alex, Notch`

## サーバーの MOTD (servermotd)
サーバーの Message of the Day を返します。
```
{"placeholder":"servermotd","values":{"ip":"mc.hypixel.net","line":"1"}}
```
出力例: `Welcome to Hypixel!`

## サーバー PING (serverping)
サーバーへの ping をミリ秒で返します。
```
{"placeholder":"serverping","values":{"ip":"mc.hypixel.net"}}
```
出力例: `54`

## サーバーのプレイヤー数 (serverplayercount)
サーバーのプレイヤー数を返します。
```
{"placeholder":"serverplayercount","values":{"ip":"mc.hypixel.net"}}
```
出力例: `25000/30000`

## サーバーの状態 (serverstatus)
サーバーのオンライン/オフライン状態を返します。
```
{"placeholder":"serverstatus","values":{"ip":"mc.hypixel.net"}}
```
出力例: `§aOnline` または `§cOffline`

## サーバーバージョン (serverversion)
サーバーの Minecraft バージョンを返します。
```
{"placeholder":"serverversion","values":{"ip":"mc.hypixel.net"}}
```
出力例: `1.19.2`

## 年 (realtimeyear)
現在の年を返します。
```
{"placeholder":"realtimeyear"}
```
出力例: `2024`

## 月 (realtimemonth)
現在の月（01-12）を返します。
```
{"placeholder":"realtimemonth"}
```
出力例: `01`

## 日 (realtimeday)
現在の日付（01-31）を返します。
```
{"placeholder":"realtimeday"}
```
出力例: `27`

## 時 (realtimehour)
現在の時刻の時を返します。既定では 24 時間形式を使用します。12 時間形式にするには `twelve_hour_format` を `"true"` に設定してください。
```
{"placeholder":"realtimehour","values":{"twelve_hour_format":"false","timezone":"system"}}
```
出力例: `14`

## 分 (realtimeminute)
現在の分（00-59）を返します。
```
{"placeholder":"realtimeminute"}
```
出力例: `30`

## 秒 (realtimesecond)
現在の秒（00-59）を返します。
```
{"placeholder":"realtimesecond"}
```
出力例: `45`

## 現在時刻のミリ秒（Unix タイムスタンプ）(unix_time)
現在の Unix タイムスタンプをミリ秒で返します。
```
{"placeholder":"unix_time"}
```
出力例: `1716552478123`

> リアルタイム系のプレースホルダー（`realtimeyear`、`realtimemonth`、`realtimeday`、`realtimehour`、`realtimeminute`、`realtimesecond`、`unix_time`）は `timezone` の値をサポートしています。`UTC`、`Europe/Berlin`、`America/New_York` のような通常の Java のタイムゾーン ID を使用してください。指定しない場合、または `system` を使用するとシステムのタイムゾーンになります。
{.is-info}

## CPU 情報 (cpuinfo)
CPU に関する情報を返します。
```
{"placeholder":"cpuinfo"}
```
出力例: `Intel(R) Core(TM) i7-10700K CPU @ 3.80GHz`

## CPU 使用率（JVM）(jvmcpu)
JVM の CPU 使用率をパーセンテージで返します。
```
{"placeholder":"jvmcpu"}
```
出力例: `25.5`

## CPU 使用率（OS）(oscpu)
OS の CPU 使用率をパーセンテージで返します。
```
{"placeholder":"oscpu"}
```
出力例: `42.8`

## GPU 情報 (gpuinfo)
GPU に関する情報を返します。
```
{"placeholder":"gpuinfo"}
```
出力例: `NVIDIA GeForce RTX 3080`

## Java バージョン (javaver)
Java のバージョンを返します。
```
{"placeholder":"javaver"}
```
出力例: `17.0.2`

## Java 仮想マシン (jvmname)
Java Virtual Machine の名前を返します。
```
{"placeholder":"jvmname"}
```
出力例: `OpenJDK 64-Bit Server VM`

## OpenGL バージョン (glver)
OpenGL のバージョンを返します。
```
{"placeholder":"glver"}
```
出力例: `4.6.0 NVIDIA 516.94`

## OS 名 (osname)
オペレーティングシステム名を返します。
```
{"placeholder":"osname"}
```
出力例: `Windows 10`

## FPS（1 秒あたりのフレーム数）(fps)
現在の FPS を返します。
```
{"placeholder":"fps"}
```
出力例: `120`

## 使用中 RAM（MB）(usedram)
現在使用中の RAM 量を MB で返します。
```
{"placeholder":"usedram"}
```
出力例: `4096`

## 最大 RAM（MB）(maxram)
割り当てられている最大 RAM を MB で返します。
```
{"placeholder":"maxram"}
```
出力例: `8192`

## 使用中 RAM（%%）(percentram)
現在使用中の RAM の割合を返します。
```
{"placeholder":"percentram"}
```
出力例: `50`

## 音声要素の音量 (audio_element_vol)
音声要素の音量を返します。
```
{"placeholder":"audio_element_vol","values":{"element_identifier":"background_music"}}
```
出力例: `0.5`

## 現在の音声トラック (audio_element_current_track)
音声要素のトラック名を返します。
```
{"placeholder":"audio_element_current_track","values":{"element_identifier":"background_music","display_name_mappings":"track1.ogg=>Cool Track Name"}}
```
出力例: `Cool Track Name`

## 音声の再生時間 (audio_duration)
音声トラックの合計再生時間を `MM:SS` 形式で返します。
```
{"placeholder":"audio_duration","values":{"element_identifier":"background_music"}}
```
出力例: `03:45`

## 音声の再生時間経過 (audio_playtime)
音声トラックの現在の再生時間を返します。`show_percentage` を `"true"` にすると、`MM:SS` の代わりに 0-100 の進行値を返します。
```
{"placeholder":"audio_playtime","values":{"element_identifier":"background_music","show_percentage":"false"}}
```
出力例: `01:30`（または `show_percentage` が `"true"` の場合は `45`）

## 音声の再生状態 (audio_playing_state)
音声要素が再生中かどうか（true/false）を返します。
```
{"placeholder":"audio_playing_state","values":{"element_identifier":"background_music"}}
```
出力例: `true`

## 動画要素の音量 (video_element_vol)
動画要素の音量レベルを返します（0.0 から 1.0）。
```
{"placeholder":"video_element_vol","values":{"element_identifier":"my_video_element"}}
```
出力例: `0.5`

## 動画要素の再生時間 (video_element_duration)
動画要素の合計再生時間を `MM:SS` 形式で返します。ミリ秒のタイムスタンプを返すには `output_as_timestamp` を `"true"` に設定してください。
```
{"placeholder":"video_element_duration","values":{"element_identifier":"my_video_element","output_as_timestamp":"false"}}
```
出力例: `02:00`（または `output_as_timestamp` が `"true"` の場合は `120000`）

## 動画要素の再生時間経過 (video_element_playtime)
動画要素の現在の再生時間（進行度）を `MM:SS` 形式で返します。0-100 の進行値にするには `show_percentage` を `"true"` に、ミリ秒にするには `output_as_timestamp` を `"true"` に設定してください。
```
{"placeholder":"video_element_playtime","values":{"element_identifier":"my_video_element","show_percentage":"false","output_as_timestamp":"false"}}
```
出力例: `00:45`（または割合として `38`、タイムスタンプとして `45200`）

## 動画要素の一時停止状態 (video_element_paused_state)
動画要素が一時停止中かどうか（true/false）を返します。
```
{"placeholder":"video_element_paused_state","values":{"element_identifier":"my_video_element"}}
```
出力例: `false`

## 動画背景の音量 (video_background_vol)
動画メニュー背景の音量レベルを返します（0.0 から 1.0）。
```
{"placeholder":"video_background_vol","values":{"background_identifier":"main_menu_video"}}
```
出力例: `0.7`

## 動画背景の再生時間 (video_background_duration)
動画メニュー背景の合計再生時間を `MM:SS` 形式で返します。ミリ秒のタイムスタンプを返すには `output_as_timestamp` を `"true"` に設定してください。
```
{"placeholder":"video_background_duration","values":{"background_identifier":"main_menu_video","output_as_timestamp":"false"}}
```
出力例: `03:00`（または `output_as_timestamp` が `"true"` の場合は `180000`）

## 動画背景の再生時間経過 (video_background_playtime)
動画メニュー背景の現在の再生時間（進行度）を `MM:SS` 形式で返します。0-100 の進行値にするには `show_percentage` を `"true"` に、ミリ秒にするには `output_as_timestamp` を `"true"` に設定してください。
```
{"placeholder":"video_background_playtime","values":{"background_identifier":"main_menu_video","show_percentage":"false","output_as_timestamp":"false"}}
```
出力例: `01:00`（または割合として `33`、タイムスタンプとして `60500`）

## 動画背景の一時停止状態 (video_background_paused_state)
動画メニュー背景が一時停止中かどうか（true/false）を返します。
```
{"placeholder":"video_background_paused_state","values":{"background_identifier":"main_menu_video"}}
```
出力例: `true`

## 計算機 (calc)
計算機プレースホルダーは、レイアウト内で数学計算を行える強力なツールです。幅広い数学演算をサポートしており、小数と整数の両方に対応しています。

### 基本構文
```
{"placeholder":"calc","values":{"decimal":"true/false","expression":"your_expression"}}
```

計算機には、主に 2 つのパラメータがあります:
- `decimal`: 結果に小数を含めるか（`true`）、整数に丸めるか（`false`）を決定します
- `expression`: 評価する数式

### 対応する演算
計算機は次の数学演算をサポートしています:
- 四則演算: `+`（加算）、`-`（減算）、`*`（乗算）、`/`（除算）
- 括弧: `(` `)` によるグループ化
- べき乗: `^`
- 平方根: `sqrt()`
- 三角関数: `sin()`、`cos()`、`tan()`
- 数学定数: `pi`、`e`
- 絶対値: `abs()`
- 対数: `log()`、`ln()`

## ランダム数 (random_number)
指定した範囲内のランダムな数を生成します。
```
{"placeholder":"random_number","values":{"min":"1","max":"100"}}
```
出力例: `42`

## 最大値 (maxnum)
2 つの数のうち大きい方を返します。
```
{"placeholder":"maxnum","values":{"first":"10","second":"20"}}
```
出力例: `20`

## 最小値 (minnum)
2 つの数のうち小さい方を返します。
```
{"placeholder":"minnum","values":{"first":"10","second":"20"}}
```
出力例: `10`

## 絶対値 (absnum)
数の絶対値を返します。
```
{"placeholder":"absnum","values":{"num":"-10.5"}}
```
出力例: `10.5`

## 符号反転 (negnum)
数の符号を反転した値を返します。
```
{"placeholder":"negnum","values":{"num":"10.5"}}
```
出力例: `-10.5`

## *π*（Math）(math_pi)
π の値を返します。
```
{"placeholder":"math_pi"}
```
出力例: `3.141592653589793`

## 三角関数の正弦（Math）(math_sin)
角度の正弦を返します。
```
{"placeholder":"math_sin","values":{"angle":"45"}}
```
出力例: `0.7071067811865476`

## 三角関数の余弦（Math）(math_cos)
角度の余弦を返します。
```
{"placeholder":"math_cos","values":{"angle":"45"}}
```
出力例: `0.7071067811865476`

## 三角関数の正接（Math）(math_tan)
角度の正接を返します。
```
{"placeholder":"math_tan","values":{"angle":"45"}}
```
出力例: `1.0`

## 切り捨て（Math）(math_floor)
数を最も近い整数以下に切り捨てます。
```
{"placeholder":"math_floor","values":{"num":"3.14"}}
```
出力例: `3`

## 切り上げ（Math）(math_ceil)
数を最も近い整数以上に切り上げます。
```
{"placeholder":"math_ceil","values":{"num":"3.14"}}
```
出力例: `4`

## 四捨五入（Math）(math_round)
数を丸めます。既定では最も近い整数に丸めます。`decimals` を 0 以上の数に設定すると、その小数桁数で丸めます。
```
{"placeholder":"math_round","values":{"num":"3.14159","decimals":"2"}}
```
出力例: `3.14`（`decimals:-1` または省略時 → `3`）

## 符号（Math）(math_sign)
数の符号を返します（正なら 1、負なら -1、0 なら 0）。
```
{"placeholder":"math_sign","values":{"num":"-3.14"}}
```
出力例: `-1`

## 双曲線正弦（Math）(math_sinh)
角度の双曲線正弦を返します。
```
{"placeholder":"math_sinh","values":{"angle":"1"}}
```
出力例: `1.1752011936438014`

## 双曲線余弦（Math）(math_cosh)
角度の双曲線余弦を返します。
```
{"placeholder":"math_cosh","values":{"angle":"1"}}
```
出力例: `1.5430806348152437`

## 双曲線正接（Math）(math_tanh)
角度の双曲線正接を返します。
```
{"placeholder":"math_tanh","values":{"angle":"1"}}
```
出力例: `0.7615941559557649`

## テキスト分割 (split_text)
指定した区切り文字でテキストを分割します。
```
{"placeholder":"split_text","values":{"input":"hello,world","regex":",","max_parts":"2","split_index":"1"}}
```
出力例: `world`

## テキストのトリム (trim_text)
先頭と末尾の空白を削除します。
```
{"placeholder":"trim_text","values":{"text":"  hello world  "}}
```
出力例: `hello world`

## テキストの切り取り (crop_text)
テキストの先頭と末尾から文字を削除します。
```
{"placeholder":"crop_text","values":{"text":"hello world","remove_from_start":"1","remove_from_end":"1"}}
```
出力例: `ello worl`

## 文字列化 (stringify)
すべての構文文字をエスケープしてテキストを文字列化します。
```
{"placeholder":"stringify","values":{"text":"text with {special} \"characters\""}}
```
出力例: `text with \{special\} \"characters\"`

## テキストのローカライズ (local)
キーに対応するローカライズ済みテキストを取得します。
```
{"placeholder":"local","values":{"key":"menu.singleplayer"}}
```
出力例: `Singleplayer`

## Web テキスト (webtext)
Web URL からテキストコンテンツを取得します。
```
{"placeholder":"webtext","values":{"link":"http://somewebsite.com/textfile.txt"}}
```
出力例: URL から取得したテキスト内容

## ランダムテキスト (randomtext)
テキストファイル、URL、または直接入力されたプレーンテキストからランダムな 1 行を返します。テキストは指定間隔で変化します。
```
{"placeholder":"randomtext","values":{"source":"/config/fancymenu/assets/<file_name.txt>","interval":"10"}}
```
パラメータ:
- `source`: テキスト行の取得元（旧 `path` パラメータの代わり）
  - ファイルパス: `/config/fancymenu/assets/quotes.txt`
  - URL: `https://example.com/quotes.txt`
  - プレーンテキスト: `Line 1\nLine 2\nLine 3`
- `interval`: テキスト変更の間隔（秒）

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

注: `source` ではなく `path` を使った旧プレースホルダーも引き続き動作します。

## JSON パーサー (json)
ファイル、URL、または直接の JSON 内容から JSON データを解析し、JSON パス式を使って値を抽出します。
```
{"placeholder":"json","values":{"source":"path_or_link_or_json_content","json_path":"$.some.json.path"}}
```
パラメータ:
- `source`: JSON データの取得元
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
3. **直接 JSON**: インラインの JSON 内容
   ```
   {"placeholder":"json","values":{"source":"{"name":"Steve","score":42,"rank":"Diamond"}","json_path":"$.rank"}}
   ```

JSON パスの例:
- `$.name` - ルートから「name」フィールドを取得
- `$.player.level` - 「player」内のネストされた「level」フィールドを取得
- `$.items[0].id` - 配列の最初の要素の「id」を取得
- `$.scores.*` - 「scores」オブジェクト内のすべての値を取得

## 絶対ファイル/フォルダパス (absolute_path)
ファイルの絶対パスを返します。
```
{"placeholder":"absolute_path","values":{"short_path":"relative/path/to/file.txt"}}
```
出力例: `C:/Users/Username/AppData/Roaming/.minecraft/relative/path/to/file.txt`

## テキストの文字数 (text_character_count)
指定したテキストの文字数を返します。
```
{"placeholder":"text_character_count","values":{"text":"Hello World!"}}
```
出力例: `12`

## テキスト幅 (text_width)
指定したテキストを描画したときのピクセル幅を返します。
```
{"placeholder":"text_width","values":{"text":"Hello World!"}}
```
出力例: `66`

## 大文字化 (uppercase_text)
入力テキストをすべて大文字に変換します。
```
{"placeholder":"uppercase_text","values":{"text":"Hello World"}}
```
出力例: `HELLO WORLD`

## 小文字化 (lowercase_text)
入力テキストをすべて小文字に変換します。
```
{"placeholder":"lowercase_text","values":{"text":"Hello World"}}
```
出力例: `hello world`

## タイトルケース (title_case_text)
入力テキストをタイトルケースに変換します。
```
{"placeholder":"title_case_text","values":{"text":"hello world"}}
```
出力例: `Hello World`

## 文頭大文字化 (sentence_case_text)
入力テキストを文頭大文字に変換します。
```
{"placeholder":"sentence_case_text","values":{"text":"hello world. this is fancymenu!"}}
```
出力例: `Hello world. This is fancymenu!`

## スネークケース (snake_case_text)
入力テキストを `snake_case` に変換します。
```
{"placeholder":"snake_case_text","values":{"text":"Hello World"}}
```
出力例: `hello_world`

## ケバブケース (kebab_case_text)
入力テキストを `kebab-case` に変換します。
```
{"placeholder":"kebab_case_text","values":{"text":"Hello World"}}
```
出力例: `hello-world`

## 交互ケース (alternating_case_text)
入力テキストを交互ケースに変換します。
```
{"placeholder":"alternating_case_text","values":{"text":"alternating case"}}
```
出力例: `aLtErNaTiNg CaSe`

## 反転ケース (toggle_case_text)
入力テキストの各文字の大文字小文字を反転します。
```
{"placeholder":"toggle_case_text","values":{"text":"Toggle Case"}}
```
出力例: `tOGGLE cASE`

## Base64 にエンコード (base64_encode)
指定したテキストを Base64 にエンコードします。
```
{"placeholder":"base64_encode","values":{"text":"Hello World"}}
```
出力例: `SGVsbG8gV29ybGQ=`

## Base64 からデコード (base64_decode)
Base64 文字列をプレーンテキストにデコードします。
```
{"placeholder":"base64_decode","values":{"text":"SGVsbG8gV29ybGQ="}}
```
出力例: `Hello World`

## ファイルテキスト (file_text)
ファイルまたは URL からテキスト行を返します。すべての行、または最後の X 行のみを返せます。
```
{"placeholder":"file_text","values":{"path_or_url":"/config/fancymenu/assets/some_file.txt","mode":"all","separator":"\n","last_lines":"1"}}
```
パラメータ:
- `path_or_url`: 読み込むファイルパスまたは URL
- `mode`: `"all"`（すべての行を返す）または `"last"`（最後の X 行のみを返す）
- `separator`: 行を結合する文字列（既定: `"\n"`）
- `last_lines`: `mode` が `"last"` のときに返す行数（既定: `"1"`）

出力例: ファイル内容による

## クリップボードの内容 (clipboard_content)
システムのクリップボードに保存されている現在のテキスト内容を返します。
```
{"placeholder":"clipboard_content"}
```
出力例: 現在クリップボードにあるテキスト

## テキスト置換 (replace_text)
リテラルテキストまたは正規表現を使って、文字列内のテキストを置換します。
```
{"placeholder":"replace_text","values":{"text":"Hello World! This is a test.","search":"World","replacement":"FancyMenu","use_regex":"false","replace_all":"true"}}
```
パラメータ:
- `text`: 処理する入力テキスト
- `search`: 検索するテキストまたは正規表現パターン
- `replacement`: 置換後のテキスト
- `use_regex`: 正規表現を使うか（`"true"`）、リテラル一致にするか（`"false"`）
- `replace_all`: すべて置換するか（`"true"`）、最初の 1 件だけか（`"false"`）

出力例: `Hello FancyMenu! This is a test.`

## 条件分岐 (switch_case)
値に基づいて switch-case 操作を行います。
```
{"placeholder":"switch_case","values":{"value":"1","cases":"1:first case,2:second case,3:third case","default":"default case"}}
```
出力例: `first case`（value が 1 の場合）

## 変数の値を取得 (FM Variable) (getvariable)
以前に保存した変数の値を取得します。
```
{"placeholder":"getvariable","values":{"name":"some_variable"}}
```
出力例: 保存された値による

## NBT データの取得 (nbt_data_get)
クライアント側で NBT データを取得します（`/data get` コマンドに類似）。サーバーに接続していて、サーバー側の正確な値が必要な場合は、サーバー版の `nbt_data_get_server` を使用してください。
```
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"foodLevel","scale":"1.0","return_type":"value"}}
```
パラメータ:
- `source_type`: `"entity"` または `"block"`
- `entity_selector`: エンティティ用の `@s`、`@p`、`@e`、または UUID/名前のようなセレクター
- `block_pos`: ブロック用の座標形式 `"x y z"`
- `nbt_path`: 取得する NBT パス
- `scale`: 数値に対する任意のスケーリング係数（既定: `"1.0"`）
- `return_type`: データの返し方
  - `"value"`: 既定。値を返します（数値には任意でスケーリング適用）
  - `"string"`: 実際の NBT データを文字列として返します
  - `"snbt"`: SNBT（整形済み NBT）として返します
  - `"json"`: JSON 形式のコンポーネントとして返します（compound タグ用）

出力例: `20`（食料値の場合）

## NBT データの取得（サーバー側）(nbt_data_get_server)
サーバー側で NBT データを（パケットを使って）問い合わせ、結果を短時間キャッシュします。値はクライアント側プレースホルダーと同じです。
```
{"placeholder":"nbt_data_get_server","values":{"source_type":"entity","entity_selector":"@s","block_pos":"","storage_id":"minecraft:storage_key","nbt_path":"SelectedItem.id","scale":"1.0","return_type":"value"}}
```
出力例: `minecraft:diamond_sword`

## 最後の死亡メッセージ (lastdeathmessage)
クライアントプレイヤーの最後に記録された死亡メッセージを返します。生の JSON テキストコンポーネントを取得するには `as_json_component` を `"true"` に設定してください。
```
{"placeholder":"lastdeathmessage","values":{"as_json_component":"false"}}
```
出力例: `Steve was slain by Zombie`

## 稼働時間 (uptime_duration)
FancyMenu が読み込まれてからの経過時間を返します。既定では秒単位です。ミリ秒で受け取るには `output_as_millis` を `"true"` に設定してください。
```
{"placeholder":"uptime_duration","values":{"output_as_millis":"false"}}
```
出力例: `742`（読み込み後の秒数）

## ワールドセーブ名 (level_save_names)
ローカルのワールドセーブ名を、選択した区切り文字で結合して一覧表示します。クライアントスレッドで実行されます。
```
{"placeholder":"level_save_names","values":{"separator":", "}}
```
出力例: `Creative Test, Survival World, Hardcore`

## ワールドセーブデータ (level_save_data)
指定したワールド名のシリアライズ済みレベルデータを返します（セーブ一覧に表示される表示名と一致している必要があります）。
```
{"placeholder":"level_save_data","values":{"level_name":"Survival World"}}
```
出力例: `{"name":"Survival World","gameMode":"survival",...}`

## 数値基数変換 (number_base_convert)
数（整数または小数）を、ある基数から別の基数へ変換します（2〜36）。基数が指定されていない場合は 10 進数が既定です。
```
{"placeholder":"number_base_convert","values":{"input":"67.5","from_base":"10","to_base":"16"}}
```
出力例: `43.8`

## ファイルサイズ (file_size)
ローカルファイルのサイズをバイト単位で返します。ローカルパスのみ使用できます。
```
{"placeholder":"file_size","values":{"path":"/config/fancymenu/assets/notes.txt"}}
```
出力例: `1284`

## ファイル MD5 (file_md5)
ローカルファイルの MD5 ハッシュを小文字の 16 進文字列で返します。
```
{"placeholder":"file_md5","values":{"path":"/config/fancymenu/assets/notes.txt"}}
```
出力例: `d41d8cd98f00b204e9800998ecf8427e`

# 実用例

## 動的なメモリ表示の作成
```
使用中 RAM: {"placeholder":"usedram"}MB / {"placeholder":"maxram"}MB ({"placeholder":"percentram"}%)
```

## リアルタイム時計の作成
```
{"placeholder":"realtimehour"}:{"placeholder":"realtimeminute"}:{"placeholder":"realtimesecond"}
```

## システム情報表示の作成
```
OS: {"placeholder":"osname"}
CPU: {"placeholder":"cpuinfo"}
GPU: {"placeholder":"gpuinfo"}
Java: {"placeholder":"javaver"}
```

## プレイヤーステータス HUD
```
体力: {"placeholder":"current_player_health"} / {"placeholder":"max_player_health"} ({"placeholder":"current_player_health_percent"}%)
防具: {"placeholder":"current_player_armor"} / {"placeholder":"max_player_armor"}
XP レベル: {"placeholder":"current_player_level"}
```

## ネストされたプレースホルダーを使った複雑な計算
```
{"placeholder":"calc","values":{"decimal":"true","expression":"({"placeholder":"usedram"} / {"placeholder":"maxram"}) * 100"}}
```

## 丸め付き座標表示
```
X: {"placeholder":"math_round","values":{"num":"{"placeholder":"player_x_coordinate"}"}}
Y: {"placeholder":"math_round","values":{"num":"{"placeholder":"player_y_coordinate"}"}}
Z: {"placeholder":"math_round","values":{"num":"{"placeholder":"player_z_coordinate"}"}}
```

# ベストプラクティス

1. **コストの高い処理はキャッシュする**: 一部のプレースホルダー（システム情報を読み取るものなど）は、リソースを多く消費する場合があります。複数回使う必要がある場合は、変数に値を保存することを検討してください。

2. **適切な小数設定を使う**: 計算を行うときは、`decimal` パラメータを適切に使ってください。整数が必要なときは `false`、正確な小数値が必要なときは `true` に設定します。

3. **欠損値を考慮する**: プレースホルダーが値を返さない場合にどうするか、常に考えておきましょう。そのような場合のために、既定値を用意するとよいでしょう。

4. **パフォーマンスをテストする**: 多数のプレースホルダーや複雑なネスト構造を使う場合は、特に低スペック環境でパフォーマンスへの影響をテストしてください。

5. **高度なサイズ調整/配置を使う**: 動的な UI 要素では、プレースホルダーと高度なサイズ調整・配置を組み合わせて、レスポンシブなレイアウトを作成できます。

6. **変数と組み合わせる**: プレースホルダーを変数と一緒に使うことで、アクションを通じて更新できる、さらに動的な内容を作れます。

# よくある問題と解決策

## プレースホルダーが更新されない
プレースホルダーの値が期待どおり更新されない場合は、次を確認してください:
- プレースホルダーの書式が正しいか
- プレースホルダー ID の大文字小文字が正しいか
- 更新に特定の条件が必要なプレースホルダーではないか

## ネストしたプレースホルダーが動作しない
プレースホルダーをネストする場合は:
- 引用符のエスケープが正しいことを確認する
- ネストされた各プレースホルダーが単体でも有効か確認する

## パフォーマンスの問題
パフォーマンスの問題が見られる場合は:
- 使用するプレースホルダーの数を減らす
- 不要なネストを避ける
- 頻繁に参照する値には変数の使用を検討する
- 用途に合った適切なプレースホルダーを使う（たとえば、静的な値で足りるならリアルタイム系プレースホルダーは使わない）
