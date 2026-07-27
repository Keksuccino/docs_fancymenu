---
title: リスナー
description: FancyMenu でリスナーを作成して使用する方法。
---

# リスナー

リスナーは、特定のイベントが発生したときに [アクションスクリプト](./action-scripts) を実行します。開いている画面に依存しないため、プレイ中やロード中にも実行できます。

リスナーは、押されたキーやクリックされたマウスボタンなどの `$$` 値を、アクションや条件に渡すことができます。

> [!CAUTION]
> リスナーは、画面が開いていない状態でも、ファイル、ネットワーク、コマンド、クリップボード、リソースパック、またはリンクのアクションを実行できます。信頼できる提供元のリスナーのみをインポートしてください。

# リスナーの使用

レイアウトエディタの外では、**メニューバー -> カスタマイズ -> リスナーの管理** を開いてリスナーを作成または編集します。

<img src="https://github.com/Keksuccino/FancyMenu/blob/master/assets/docs/manage_listeners.png?raw=true" alt="リスナーの管理" style="max-width:800px;width:100%;height:auto;">

# リスナー変数

リスナーは、アクションや条件に読み取り専用の値を提供できます。対応しているテキストフィールドでは、これらの `$$` 名を使用してください。

たとえば、[**キーボードキー押下時**](#on-keyboard-key-pressed-keyboard_key_pressed) と [**ゲームログに出力** アクション](./action-scripts#print-to-game-log-print_to_log) を組み合わせます。`Key pressed! The key is: $$key_name` という値を使うと、押されたキーの名前が挿入されます。

> [!WARNING]
> リスナー変数は、FancyMenu の [保存変数](./variables) とは別物です。保存変数を使うアクション、条件、プレースホルダーは `$$` 値では動作しません。

リスナー変数名は大文字小文字を区別し、そのリスナーのスクリプト内でのみ機能します。

チャット、リモートサーバー、ファイル、ユーザー入力からの値は信頼できないものとして扱ってください。パス、URL、コマンドに直接挿入しないでください。

リスナー変数は文字列です。情報が利用できない場合、リスナーは `ERROR`、`UNKNOWN`、`NONE`、`EMPTY`、`0`、`-1`、または空文字列といった文書化された特別値を返すことがあります。リスナーのデータをパス、コマンド、URL に挿入する前に、これらの値を確認してください。

# 詳細なリスナー

このセクションでは、FancyMenu の組み込みリスナーを一覧表示します。

## Markdown テキストがクリックされたとき (`text_clicked`)
- [Markdown テキストの `click:` イベント](./text-formatting#click-and-hover-events) がクリックされたときに発火します。例: `[Open](click:open_menu)`。
- 変数:
  - `$$text_event_id` – Markdown リンクのイベント ID

## Markdown テキストにホバーしたとき (`text_hovered`)
- [Markdown テキストの `hover:` イベント](./text-formatting#click-and-hover-events) にホバーしたときに発火します。例: `[Hint](hover:show_hint)`。
- 変数:
  - `$$text_event_id` – Markdown リンクのイベント ID

## アクション経由で ZIP が展開されたとき (`zip_extracted_via_action`)
- [**ゲームディレクトリに ZIP ファイルを展開** アクション](./action-scripts#extract-zip-file-in-game-directory-extract_zip_file_in_game_dir) が完了したときに発火します。
- 変数:
  - `$$source_zip_path` – 正規化されたユーザー向けの元パス。ゲームディレクトリのパスは `/...` として返される場合があり、一般的な Minecraft ディレクトリのパスは `.minecraft/...` を使用する場合があります
  - `$$target_folder_path` – 同じパス形式を使う正規化済みのユーザー向けターゲットパス
  - `$$extract_succeeded` – true/false
  - `$$failure_reason` – 展開に失敗した場合のエラー文

## 要素が生成されたとき (`element_spawned_via_action`)
- 対応する FancyMenu の機能またはアドオンが、要素インスタンスを動的に生成したときに発火します。
- 変数:
  - `$$element_type` – 生成された要素タイプ
  - `$$element_identifier` – 生成された要素の識別子
  - `$$target_screen` – 対象画面の識別子

## アニメーションテクスチャの再生開始 (`animated_texture_started_playing`)
- [アニメーションテクスチャ](./fma) の再生が始まったときに発火します。
- 変数:
  - `$$texture_source` – テクスチャのソース
  - `$$texture_source_type` – ソース種別
  - `$$texture_will_restart` – true/false

## アニメーションテクスチャの再生終了 (`animated_texture_finished_playing`)
- アニメーションテクスチャの再生が終了したときに発火します。
- 変数:
  - `$$texture_source`
  - `$$texture_source_type`
  - `$$texture_will_restart`

## 動画再生状態が変化したとき (`video_playback_status_changed`)
- [動画要素またはメニュー背景](./video) の再生状態が変化したときに発火します。
- 変数:
  - `$$video_source` – 動画ソース
  - `$$video_source_type` – ソース種別
  - `$$is_looping` – true/false
  - `$$new_status` – `PLAYING`、`STOPPED`、`PAUSED`、または `FINISHED`

## チャットでシステムメッセージを受信したとき (`system_message_received_in_chat`)
- クライアントがシステムチャットメッセージを受信したときに発火します。たとえばコマンドの応答などです。
- 変数:
  - `$$system_message_string` – プレーンテキストのメッセージ
  - `$$system_message_component` – JSON コンポーネント

## FM データを受信したとき (`fm_data_received`)
- サーバーが `/fmdata send` を通じてこのクライアントに [FM Data](./fm-data) を送信したときに発火します。
- 変数:
  - `$$data_identifier` – データ識別子文字列
  - `$$data` – データ本体
  - `$$sent_by` – サーバー IP または `integrated_server`

## リモートサーバーに接続したとき (`remote_server_connected`)
- [リモートサーバー接続](./remote-server-communication) が正常に開いた後に発火します。
- 変数:
  - `$$request_id` – キャッシュされたリクエスト ID
  - `$$remote_server_url` – リモートサーバー URL

## リモートサーバーデータを受信したとき (`remote_server_data_received`)
- 接続中のリモートサーバーからテキストデータを受信したときに発火します。
- 変数:
  - `$$request_id` – リクエスト ID
  - `$$remote_server_url` – リモートサーバー URL
  - `$$data` – 受信した本体データ

## リモートサーバー接続が閉じたとき (`remote_server_connection_closed`)
- リモートサーバー接続が閉じたときに発火します。
- 変数:
  - `$$request_id` – リクエスト ID
  - `$$remote_server_url` – リモートサーバー URL
  - `$$intentionally_closed` – アクションによって閉じられた場合は TRUE
  - `$$crashed` – 接続が予期せずクラッシュした場合は TRUE
  - `$$unknown_close_reason` – 既知の終了理由が利用できなかった場合は TRUE

## キーボードキーが押されたとき (`keyboard_key_pressed`)
- キーが押されたときにトリガーされます（押し続けている間は繰り返し発火。画面内とゲーム内の両方で動作）。
- 変数:
  - `$$key_name` – キーの表示名
  - `$$key_keycode` – GLFW キーコード
  - `$$key_scancode` – GLFW スキャンコード
  - `$$key_modifiers` – 有効な修飾キーのビットマスク

## キーボードキーが離されたとき (`keyboard_key_released`)
- キーが離されたときにトリガーされます（画面内とゲーム内）。
- 変数:
  - `$$key_name`
  - `$$key_keycode`
  - `$$key_scancode`
  - `$$key_modifiers`

## 画面内で文字が入力されたとき (`keyboard_char_typed`)
- 画面が開いている間に文字が入力されたときに発火します。
- 変数:
  - `$$char` – 入力された文字

## 画面内でマウスが移動したとき (`mouse_moved`)
- 画面が開いている間にマウスが動くたびに発火します。
- 変数:
  - `$$mouse_pos_x` – 現在の X
  - `$$mouse_pos_y` – 現在の Y
  - `$$mouse_move_delta_x` – 前回イベントからの X 差分
  - `$$mouse_move_delta_y` – 前回イベントからの Y 差分

## マウスボタンがクリックされたとき (`mouse_button_clicked`)
- マウスボタンが押されたときに発火します（画面内とゲーム内）。
- 変数:
  - `$$button` – 左/右/中
  - `$$mouse_pos_x` – 現在の X
  - `$$mouse_pos_y` – 現在の Y

## マウスボタンが離されたとき (`mouse_button_released`)
- マウスボタンが離されたときに発火します（画面内とゲーム内）。
- 変数:
  - `$$button`
  - `$$mouse_pos_x`
  - `$$mouse_pos_y`

## 画面内でマウスホイールがスクロールされたとき (`mouse_scrolled`)
- 画面が開いている間にマウスホイールがスクロールされたときに発火します。
- 変数:
  - `$$scroll_delta_y` – 縦スクロール量

## 画面が開かれたとき (`screen_open`)
- 画面がアクティブになった直後に実行されます。上書きに使用できます。
- 変数:
  - `$$screen_identifier` – 開かれた画面の識別子

## 画面が閉じられたとき (`screen_close`)
- 画面が閉じた直後に実行されます。
- 変数:
  - `$$screen_identifier` – 閉じられた画面の識別子

## Minecraft を終了したとき (`quit_minecraft`)
- クライアントがシャットダウンを開始したときに 1 回発火します。
- 変数:
  - `$$timestamp_millis` – 終了時のエポックミリ秒
  - `$$timestamp_iso` – 終了時刻の ISO-8601 タイムスタンプ

## 死亡時 (`player_death`)
- ローカルプレイヤーに対してバニラの死亡画面が開いたときに実行されます。
- 変数:
  - `$$days_survived` – 前回死亡からの日数
  - `$$death_reason_string` – プレーンテキストの原因
  - `$$death_reason_component` – JSON コンポーネントの原因
  - `$$death_pos_x` – 死亡時の X 座標
  - `$$death_pos_y` – 死亡時の Y 座標
  - `$$death_pos_z` – 死亡時の Z 座標

## 変数が更新されたとき [FM 変数] (`fm_variable_updated`)
- [FancyMenu 変数](./variables) が設定または更新されるたびに発火します。
- 変数:
  - `$$var_name` – 変数名
  - `$$old_value` – 以前の値
  - `$$new_value` – 新しい値

## アクション経由でファイルがダウンロードされたとき (`file_downloaded_via_action`)
- [**ゲームディレクトリにファイルをダウンロード** アクション](./action-scripts#download-file-to-game-directory-download_file_to_game_dir) が完了した後に発火します。
- 変数:
  - `$$download_url` – ダウンロード元
  - `$$target_file_path` – 成功時に保存されたファイルパス。失敗時は、最終的なファイル名が解決されなかったため、対象ディレクトリのみが含まれる場合があります
  - `$$download_succeeded` – true/false

## ファイルが選択されたとき (`file_selected_via_action`)
- [**システムからファイルを選択** アクション](./action-scripts#select-file-from-system-select_file_to_game_dir) が完了した後に発火します。
- 変数:
  - `$$selected_file_path` – 選択されたファイルの絶対パス、またはキャンセル時は空
  - `$$target_file_path` – インスタンス内に解決されたパス
  - `$$selection_succeeded` – コピーが成功した場合は true
  - `$$selection_cancelled` – ダイアログが閉じられた場合は true
  - `$$failure_reason` – 失敗時のエラー情報

## チャットメッセージを受信したとき (`chat_message_received`)
- 通常のプレイヤーチャット行がクライアントに表示されたときに発火します。
- 変数:
  - `$$chat_message_string` – プレーンテキストの行
  - `$$chat_message_component` – 完全な JSON コンポーネント
  - `$$sender_uuid` – 送信者 UUID、または ERROR
  - `$$sender_name` – 送信者名、または ERROR

## チャットメッセージを送信したとき (`chat_message_sent`)
- ローカルプレイヤーがチャットメッセージを送信したときに発火します。
- 変数:
  - `$$chat_message_string` – プレーンテキストの行
  - `$$chat_message_component` – 完全な JSON コンポーネント

## 効果を獲得したとき (`effect_gained`)
- プレイヤーがステータス効果を得たときに発火します。
- 変数:
  - `$$effect_key` – 効果のリソースロケーション
  - `$$effect_type` – positive/negative/neutral
  - `$$effect_duration` – 残りティック数

## 効果を失ったとき (`effect_lost`)
- プレイヤーがステータス効果を失ったときに発火します。
- 変数:
  - `$$effect_key` – 期限切れになった効果
  - `$$effect_type` – 分類

## 経験値が変化したとき (`experience_changed`)
- プレイヤーの総 XP が変化するたびに発火します。
- 変数:
  - `$$new_experience_amount` – 変化後
  - `$$old_experience_amount` – 変化前
  - `$$is_level_up` – レベルが上がった場合は TRUE

## ダメージを受けたとき (`damage_taken`)
- プレイヤーがダメージを受けるたび、1 回だけ発火します。
- 変数:
  - `$$damage_amount` – 減少した体力
  - `$$damage_type` – ダメージ種別のリソースロケーション
  - `$$is_fatal_damage` – 致命傷なら TRUE
  - `$$damage_source` – 攻撃者のリソースロケーション、または NONE

## 凍結を開始したとき (`started_freezing`)
- プレイヤーが凍結し始めたときに発火します。
- 変数:
  - `$$freezing_intensity` – 0.0 はなし、1.0 は完全凍結

## 凍結を停止したとき (`stopped_freezing`)
- プレイヤーが凍結を停止したときに発火します。
- 変数:
  - (なし)

## 完全に凍結したとき (`fully_frozen`)
- プレイヤーが完全に凍結したときに 1 回発火します。
- 変数:
  - (なし)

## ブロックを見始めたとき (`start_looking_at_block`)
- クロスヘアが初めてブロックを指したときに 1 回発火します（最大距離 20 ブロック）。
- 変数:
  - `$$block_key` – 対象ブロック
  - `$$block_pos_x` – ブロック X
  - `$$block_pos_y` – ブロック Y
  - `$$block_pos_z` – ブロック Z
  - `$$distance_to_player` – 目線からヒット位置までの距離

## ブロックを見終えたとき (`stop_looking_at_block`)
- クロスヘアがブロックを指さなくなったときに発火します（最後に対象だったブロックを報告、最大距離 20 ブロック）。
- 変数:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`
  - `$$distance_to_player`

## エンティティを見始めたとき (`start_looking_at_entity`)
- クロスヘアが初めてエンティティを指したときに 1 回発火します（最大距離 20 ブロック）。
- 変数:
  - `$$entity_key` – 対象エンティティの種類
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## エンティティを見終えたとき (`stop_looking_at_entity`)
- クロスヘアがエンティティを指さなくなったときに発火します（最後に対象だったエンティティを報告、最大距離 20 ブロック）。
- 変数:
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## エンティティが生成されたとき (`entity_spawned`)
- **サーバー側で FancyMenu が必要です。** 接続中のワールド/サーバーのどこかでエンティティが生成されたときに発火します。
- 変数:
  - `$$entity_key`
  - `$$distance_to_player` – 他ディメンションの場合は −1
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`
  - `$$dimension_key`
  - `$$is_same_dimension_as_player`

## エンティティが死亡したとき (`entity_died`)
- **サーバー側で FancyMenu が必要です。** 接続中のワールド/サーバーでエンティティが死亡したときに発火します。
- 変数:
  - `$$entity_key`
  - `$$distance_to_player` – 他ディメンションの場合は −1
  - `$$death_pos_x`
  - `$$death_pos_y`
  - `$$death_pos_z`
  - `$$entity_uuid`
  - `$$dimension_key`
  - `$$damage_type`
  - `$$is_same_dimension_as_player`
  - `$$entity_killed_by_name`
  - `$$entity_killed_by_key`
  - `$$entity_killed_by_uuid`

## エンティティが視界に入り始めたとき (`entity_starts_being_in_sight`)
- エンティティが 200 ブロック以内で最初に視認可能になったときに発火します。
- 変数:
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## エンティティが視界から外れたとき (`entity_stops_being_in_sight`)
- 以前見えていたエンティティが視界から消えるか、200 ブロックを超えたときに発火します。
- 変数:
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## エンティティとインタラクトしたとき (`entity_interacted`)
- プレイヤーがエンティティとのインタラクトに成功したときに発火します。
- 変数:
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## エンティティに乗ったとき (`entity_mounted`)
- プレイヤーがエンティティに乗り始めたときに発火します。
- 変数:
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## エンティティから降りたとき (`entity_unmounted`)
- プレイヤーが現在乗っているエンティティから降りたときに発火します。
- 変数:
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## ブロックを壊したとき (`block_broke`)
- プレイヤーがブロックを壊したときに発火します。
- 変数:
  - `$$block_key`
  - `$$broke_with_item_key` – 使用した道具、または EMPTY
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## ブロックを設置したとき (`block_placed`)
- プレイヤーがブロックを設置したときに発火します。
- 変数:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## ブロックとインタラクトしたとき (`interacted_with_block`)
- プレイヤーがブロックとのインタラクトに成功したときに発火します。
- 変数:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## ブロックの上に乗ったとき (`stepping_on_block`)
- プレイヤーがブロックの上に足を踏み入れたときに発火します。
- 変数:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## バイオームに入ったとき (`enter_biome`)
- プレイヤーが新しいバイオームに入ったときに発火します。
- 変数:
  - `$$biome_key` – 入ったバイオーム

## バイオームから出たとき (`leave_biome`)
- プレイヤーが現在のバイオームから出たときに発火します。
- 変数:
  - `$$biome_key` – 直前までいたバイオーム

## 構造物に入ったとき (`enter_structure`)
- **サーバー側で FancyMenu が必要です。** 粗い構造物領域検出です。構造物の近く・上・下でも発火する場合があります。
- 変数:
  - `$$structure_key` – 入った構造物

## 構造物から出たとき (`leave_structure`)
- **サーバー側で FancyMenu が必要です。** 粗い検出です。構造物の外周付近で発火する場合があります。
- 変数:
  - `$$structure_key` – 直前までいた構造物

## 構造物に入ったとき（高精度） (`enter_structure_high_precision`)
- **サーバー側で FancyMenu が必要です。** プレイヤーが構造物の境界ボックス内に入ったときに発火します。
- 変数:
  - `$$structure_key`

## 構造物から出たとき（高精度） (`leave_structure_high_precision`)
- **サーバー側で FancyMenu が必要です。** プレイヤーが構造物の境界ボックスの外に出た後に発火します。
- 変数:
  - `$$structure_key`

## ディメンションに入ったとき (`enter_dimension`)
- プレイヤーが新しいディメンションに入ったときに発火します。
- 変数:
  - `$$dimension_key` – 入ったディメンション

## 泳ぎ始めたとき (`start_swimming`)
- プレイヤーが泳ぎ始めたときに発火します。
- 変数:
  - `$$fluid_type` – 流体のリソースロケーション

## 泳ぎ終えたとき (`stop_swimming`)
- プレイヤーが泳ぐのをやめたときに発火します。
- 変数:
  - `$$fluid_type` – 泳ぎ終えた流体

## 流体に触れ始めたとき (`start_touching_fluid`)
- プレイヤーが流体に触れ始めたときに発火します。
- 変数:
  - `$$fluid_type` – 触れている流体

## 流体に触れなくなったとき (`stop_touching_fluid`)
- プレイヤーが流体に触れなくなったときに発火します。
- 変数:
  - `$$fluid_type` – もう触れていない流体

## 音楽トラックが開始したとき (`music_track_started`)
- 新しい音楽トラックの再生が始まったときに発火します。
- 変数:
  - `$$track_resource_location` – 音声ファイル
  - `$$track_display_name` – 人間向けの名前、または UNKNOWN
  - `$$track_artist` – アーティスト名、または UNKNOWN
  - `$$track_duration_ms` – ミリ秒（不明な場合は 0）

## 音楽トラックが停止したとき (`music_track_stopped`)
- 現在の音楽トラックが終了または置き換えられたときに発火します。
- 変数:
  - `$$track_resource_location`
  - `$$track_display_name`
  - `$$track_artist`
  - `$$track_duration_ms`

## ワールドサウンドが鳴ったとき (`world_sound_triggered`)
- 位置付きのワールドサウンドがプレイヤー付近で再生開始されたときに発火します。
- 変数:
  - `$$sound_resource_location` – サウンドファイル
  - `$$sound_display_name` – 利用可能な場合の字幕名
  - `$$sound_origin_pos_x`
  - `$$sound_origin_pos_y`
  - `$$sound_origin_pos_z`
  - `$$sound_origin_distance_to_player`
  - `$$sound_origin_direction_from_player` – 向きに対する相対角度 0〜360 度

## 天候が変化したとき (`weather_changed`)
- 天候が全体的または局所的に変化したときに発火します（バイオームの変化や屋内に入ることでも再発火する場合があります）。
- 変数:
  - `$$weather_type` – clear/rain/thunder
  - `$$weather_can_snow` – 雪が表示される場合は TRUE
  - `$$weather_can_rain` – 雨が表示される場合は TRUE

## 燃え始めたとき (`started_burning`)
- プレイヤーが燃え始めたときに発火します。
- 変数:
  - (なし)

## 燃え終わったとき (`stopped_burning`)
- プレイヤーが燃え終わったときに発火します。
- 変数:
  - (なし)

## 溺れ始めたとき (`started_drowning`)
- プレイヤーが溺れダメージを受け始めたときに発火します。
- 変数:
  - (なし)

## 位置が変化したとき (`position_changed`)
- プレイヤーのブロック位置が変化するたびに発火します。
- 変数:
  - `$$old_pos_x` – 以前のブロック X
  - `$$old_pos_y` – 以前のブロック Y
  - `$$old_pos_z` – 以前のブロック Z
  - `$$new_pos_x` – 新しいブロック X
  - `$$new_pos_y` – 新しいブロック Y
  - `$$new_pos_z` – 新しいブロック Z

## 走り始めたとき (`started_running`)
- プレイヤーがダッシュを始めたときに発火します。
- 変数:
  - (なし)

## 走り終えたとき (`stopped_running`)
- プレイヤーがダッシュをやめたときに発火します。
- 変数:
  - (なし)

## ジャンプしたとき (`jump`)
- プレイヤーがジャンプするたびに発火します。
- 変数:
  - (なし)

## サーバーに参加したとき (`server_joined`)
- マルチプレイヤーサーバーへの参加に成功した後に発火します。
- 変数:
  - `$$server_ip` – 参加したサーバーのアドレス

## サーバーから退出したとき (`server_left`)
- マルチプレイヤーサーバーから切断した後に発火します。
- 変数:
  - `$$server_ip` – 退出したサーバーのアドレス

## シングルプレイワールドに入ったとき (`world_entered`)
- シングルプレイワールドの読み込みが完了し、操作が戻った後に発火します。
- 変数:
  - `$$world_name` – 表示名
  - `$$world_save_path` – 絶対保存フォルダー
  - `$$world_difficulty` – 難易度キー
  - `$$world_cheats_allowed` – チートが有効なら TRUE
  - `$$world_icon_path` – 絶対アイコンパス
  - `$$world_is_first_join` – 初回訪問時に TRUE

## シングルプレイワールドから出たとき (`world_left`)
- シングルプレイワールドが閉じ、保存が完了した後に発火します。
- 変数:
  - `$$world_name`
  - `$$world_save_path`
  - `$$world_difficulty`
  - `$$world_cheats_allowed`
  - `$$world_icon_path`

## 他のプレイヤーがワールド/サーバーに参加したとき (`other_player_joined_world`)
- 別のプレイヤーが現在のワールド/サーバーに参加したときに発火します。
- 変数:
  - `$$player_name` – 参加したプレイヤー名
  - `$$player_uuid` – UUID

## 他のプレイヤーがワールド/サーバーから退出したとき (`other_player_left_world`)
- 別のプレイヤーが現在のワールド/サーバーから退出したときに発火します。
- 変数:
  - `$$player_name`
  - `$$player_uuid`

## 他のプレイヤーが死亡したとき (`other_player_died`)
- 現在のワールド内の別のプレイヤーが死亡したときに発火します。
- 変数:
  - `$$player_name`
  - `$$player_uuid`
  - `$$death_pos_x`
  - `$$death_pos_y`
  - `$$death_pos_z`

## アイテムを拾ったとき (`item_picked_up`)
- プレイヤーがアイテムエンティティを拾ったときに発火します。
- 変数:
  - `$$item_key` – 拾ったアイテムのリソースロケーション

## アイテムを落としたとき (`item_dropped`)
- プレイヤーがインベントリからアイテムを捨てたときに発火します。
- 変数:
  - `$$item_key` – 落としたアイテムのリソースロケーション

## アイテムを消費したとき (`item_consumed`)
- プレイヤーがアイテムの消費を完了したときに発火します。
- 変数:
  - `$$item_key` – 消費したアイテム

## インベントリでアイテムにホバーしたとき (`item_hovered_in_inventory`)
- どのインベントリ画面でも、ユーザーがアイテムにホバーしたときに発火します。
- 変数:
  - `$$item_key` – ホバーしたアイテムのリソースロケーション
  - `$$item_display_name_string` – プレーンテキストのアイテム表示名
  - `$$item_display_name_json` – JSON コンポーネントのアイテム表示名

## アイテムを使用したとき (`item_used`)
- プレイヤーがアイテムを使用したときに発火します。
- 変数:
  - `$$item_key` – 使用したアイテム
  - `$$used_on_type` – block/entity/self/none
  - `$$used_on_entity_key` – 対象エンティティの種類、または空
  - `$$used_on_block_key` – 対象ブロック、または空
  - `$$target_pos_x` – 対象 X、または -1
  - `$$target_pos_y` – 対象 Y、または -1
  - `$$target_pos_z` – 対象 Z、または -1

## アイテムが壊れたとき (`item_broke`)
- プレイヤーのインベントリ内のアイテムが壊れたときに発火します。
- 変数:
  - `$$item_key` – 壊れたアイテム
  - `$$item_type` – tool/armor/other
