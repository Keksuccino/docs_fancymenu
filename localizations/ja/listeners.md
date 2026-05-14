---
title: リスナー
description: FancyMenu でリスナーを作成して使用する方法。
---

# リスナー

FancyMenu v3.8.0 から、「リスナー」と呼ばれる新機能が追加されました。

リスナーは、特定のクライアントイベントやゲームプレイイベントが発生したときにアクションスクリプトを実行します。
また、リスナー内のアクション、プレースホルダー、要件で使用できる変数を公開できます。

FancyMenu の他の多くの機能と違い、リスナーは画面やオーバーレイに固定されません。イベントを常にバックグラウンドで監視し、イベントが発火すると、その時点で画面が開いていなくてもアクションスクリプトを実行します。

# リスナーの使い方

イベントを監視してアクションスクリプトを実行する新しいリスナーを作成するには、**レイアウトエディター以外**の状態で **メニューバー -> カスタマイズ -> リスナーの管理** をクリックします。ここで、リスナーを簡単に作成・管理できる UI を利用できます。

<img src="https://github.com/Keksuccino/FancyMenu/blob/master/assets/docs/manage_listeners.png?raw=true" alt="リスナーの管理" style="max-width:800px;width:100%;height:auto;">

# リスナー変数

リスナーは、内部のアクション、要件、プレースホルダー向けに特別な種類の変数を公開することがあります。
これらの変数はプレースホルダーのようにアクセスできます（実質的にはプレースホルダーです）。

これらの変数は、テキスト入力欄で名前の前に `$$` を付けてそのまま使用します。通常のプレースホルダーを使う場合と同じような使い方です。

たとえば **On Keyboard Key Pressed** リスナーを使い、**Print to Log** アクションでキー名をログに出力したい場合、アクションに渡すメッセージとして `Key pressed! The key is: $$key_name` のように入力します。変数プレースホルダーは後で実際のキー名に置き換えられます。

> これらは「変数」と呼ばれていますが、FancyMenu の通常の[変数システム](/variables)とは一切関係ありません。これらの変数は **読み取り専用** なので設定できません。また、FancyMenu の変数システム向けのアクション、要件、プレースホルダーをこれらの特別なリスナー変数に対して使うこともできません。そのため、**Get Variable Value [FM Variable]**、**Is Variable Value [FM Variable]**、**Set Variable Value [FM Variable]** はリスナー変数では動作しません。
{.is-warning}

# リスナーの詳細

この一覧には、FancyMenu のリスナーのほとんど、あるいはすべてが含まれています。MOD の更新により、一覧が常に最新とは限りません。

## On Markdown Text Clicked
- `click:` イベントを持つ Markdown テキストがクリックされたときに発火します。例: `[Open](click:open_menu)`。
- 変数:
  - `$$text_event_id` – Markdown リンクのイベント ID

## On Markdown Text Hovered
- `hover:` イベントを持つ Markdown テキストにカーソルが乗ったときに発火します。例: `[Hint](hover:show_hint)`。
- 変数:
  - `$$text_event_id` – Markdown リンクのイベント ID

## On ZIP Extracted via Action
- **Extract ZIP File In Game Directory** アクションの完了時に発火します。
- 変数:
  - `$$source_zip_path` – 解決済みの ZIP ソースパス
  - `$$target_folder_path` – 解決済みの展開先パス
  - `$$extract_succeeded` – true/false
  - `$$failure_reason` – 展開に失敗した場合のエラーテキスト

## On Element Spawned
- アクション/スクリプトによる要素生成フローで要素が生成されたときに発火します。
- 変数:
  - `$$element_type` – 生成された要素の種類
  - `$$element_identifier` – 生成された要素の識別子
  - `$$target_screen` – 対象スクリーンの識別子

## On Animated Texture Started Playing
- アニメーションテクスチャの再生が開始されたときに発火します。
- 変数:
  - `$$texture_source` – テクスチャのソース
  - `$$texture_source_type` – ソース種別
  - `$$texture_will_restart` – true/false

## On Animated Texture Finished Playing
- アニメーションテクスチャの再生が終了したときに発火します。
- 変数:
  - `$$texture_source`
  - `$$texture_source_type`
  - `$$texture_will_restart`

## On Video Playback Status Changed
- 動画要素または動画メニュー背景の再生状態が変わったときに発火します。
- 変数:
  - `$$video_source` – 動画ソース
  - `$$video_source_type` – ソース種別
  - `$$is_looping` – true/false
  - `$$new_status` – `PLAYING`、`STOPPED`、`PAUSED`、または `FINISHED`

## On System Message Received in Chat
- コマンドのフィードバックなど、クライアントがシステムチャットメッセージを受信したときに発火します。
- 変数:
  - `$$system_message_string` – プレーンテキストメッセージ
  - `$$system_message_component` – JSON コンポーネント

## On FM Data Received
- サーバーが `/fmdata send` によりこのクライアントへ FM データを送信したときに発火します。
- 変数:
  - `$$data_identifier` – データ識別子文字列
  - `$$data` – データペイロード
  - `$$sent_by` – サーバー IP または `integrated_server`

## On Remote Server Connected
- FancyMenu がリモートサーバー接続を初期化したときに発火します。
- 変数:
  - `$$request_id` – キャッシュされたリクエスト ID
  - `$$remote_server_url` – リモートサーバー URL

## On Remote Server Data Received
- 接続済みのリモートサーバーからテキストデータを受信したときに発火します。
- 変数:
  - `$$request_id` – リクエスト ID
  - `$$remote_server_url` – リモートサーバー URL
  - `$$data` – 受信したペイロード

## On Remote Server Connection Closed
- リモートサーバー接続が閉じたときに発火します。
- 変数:
  - `$$request_id` – リクエスト ID
  - `$$remote_server_url` – リモートサーバー URL
  - `$$intentionally_closed` – アクションによって閉じられた場合は TRUE
  - `$$crashed` – 接続が予期せずクラッシュした場合は TRUE
  - `$$unknown_close_reason` – 既知の終了理由がない場合は TRUE

## On Keyboard Key Pressed
- キーが押されたときに発火します（押し続けている間は繰り返し発火。画面内でもゲーム内でも動作します）。
- 変数:
  - `$$key_name` – キーの表示名
  - `$$key_keycode` – GLFW キーコード
  - `$$key_scancode` – GLFW スキャンコード
  - `$$key_modifiers` – 有効な修飾キーのビットマスク

## On Keyboard Key Released
- キーが離されたときに発火します（画面内でもゲーム内でも動作します）。
- 変数:
  - `$$key_name`
  - `$$key_keycode`
  - `$$key_scancode`
  - `$$key_modifiers`

## On Keyboard Character Typed in Screen
- 画面が開いている間に文字が入力されたときに発火します。
- 変数:
  - `$$char` – 入力された文字

## On Mouse Moved in Screen
- 画面が開いている間にマウスが移動するたびに発火します。
- 変数:
  - `$$mouse_pos_x` – 現在の X 座標
  - `$$mouse_pos_y` – 現在の Y 座標
  - `$$mouse_move_delta_x` – 前回イベントからの X 変化量
  - `$$mouse_move_delta_y` – 前回イベントからの Y 変化量

## On Mouse Button Clicked
- マウスボタンが押されたときに発火します（画面内でもゲーム内でも動作します）。
- 変数:
  - `$$button` – 左/右/中
  - `$$mouse_pos_x` – 現在の X 座標
  - `$$mouse_pos_y` – 現在の Y 座標

## On Mouse Button Released
- マウスボタンが離されたときに発火します（画面内でもゲーム内でも動作します）。
- 変数:
  - `$$button`
  - `$$mouse_pos_x`
  - `$$mouse_pos_y`

## On Mouse Scrolled in Screen
- 画面が開いている間にマウスホイールがスクロールされたときに発火します。
- 変数:
  - `$$scroll_delta_y` – 縦スクロール量

## On Screen Opened
- いずれかの画面がアクティブになった直後に実行されます。上書き用途に使えます。
- 変数:
  - `$$screen_identifier` – 開いた画面の識別子

## On Screen Closed
- 画面が閉じられた直後に実行されます。
- 変数:
  - `$$screen_identifier` – 閉じた画面の識別子

## On Quit Minecraft
- クライアントの終了処理が始まったときに 1 回発火します。
- 変数:
  - `$$timestamp_millis` – 終了時のエポックミリ秒
  - `$$timestamp_iso` – 終了時刻の ISO-8601 タイムスタンプ

## On Death
- ローカルプレイヤーに対してバニラの死亡画面が開いたときに実行されます。
- 変数:
  - `$$days_survived` – 最後の死亡からの日数
  - `$$death_reason_string` – プレーンテキストの死因
  - `$$death_reason_component` – JSON コンポーネントの死因
  - `$$death_pos_x` – 死亡地点の X 座標
  - `$$death_pos_y` – 死亡地点の Y 座標
  - `$$death_pos_z` – 死亡地点の Z 座標

## On Variable Updated [FM Variable]
- FancyMenu の変数が設定/更新されたときに発火します。
- 変数:
  - `$$var_name` – 変数名
  - `$$old_value` – 以前の値
  - `$$new_value` – 新しい値

## On File Downloaded via Action
- “Download File to Game Directory” アクションの完了後に発火します。
- 変数:
  - `$$download_url` – ダウンロード元
  - `$$target_file_path` – 保存されたファイルのパス
  - `$$download_succeeded` – true/false

## On File Selected
- “Select File” アクションの完了後に発火します。
- 変数:
  - `$$selected_file_path` – 選択されたファイルの絶対パス、またはキャンセル時は空
  - `$$target_file_path` – インスタンス内で解決されたパス
  - `$$selection_succeeded` – コピー成功時は true
  - `$$selection_cancelled` – ダイアログを閉じた場合は true
  - `$$failure_reason` – 失敗時のエラー情報

## On Chat Message Received
- 通常のプレイヤーチャット行がクライアントに表示されたときに発火します。
- 変数:
  - `$$chat_message_string` – プレーンテキスト行
  - `$$chat_message_component` – 完全な JSON コンポーネント
  - `$$sender_uuid` – 送信者の UUID、または ERROR
  - `$$sender_name` – 送信者名、または ERROR

## On Chat Message Sent
- ローカルプレイヤーがチャットメッセージを送信したときに発火します。
- 変数:
  - `$$chat_message_string` – プレーンテキスト行
  - `$$chat_message_component` – 完全な JSON コンポーネント

## On Effect Gained
- プレイヤーがステータス効果を得たときに発火します。
- 変数:
  - `$$effect_key` – 効果のリソースロケーション
  - `$$effect_type` – positive/negative/neutral
  - `$$effect_duration` – 残りティック数

## On Effect Lost
- プレイヤーがステータス効果を失ったときに発火します。
- 変数:
  - `$$effect_key` – 期限切れになった効果
  - `$$effect_type` – 種別

## On Experience Changed
- プレイヤーの総 XP が変化するたびに発火します。
- 変数:
  - `$$new_experience_amount` – 変更後
  - `$$old_experience_amount` – 変更前
  - `$$is_level_up` – レベルが上がった場合は TRUE

## On Damage Taken
- プレイヤーがダメージを受けるたび、ヒットごとに 1 回発火します。
- 変数:
  - `$$damage_amount` – 減った体力
  - `$$damage_type` – ダメージ種別のリソースロケーション
  - `$$is_fatal_damage` – 致死ダメージなら TRUE
  - `$$damage_source` – 攻撃者のリソースロケーション、または NONE

## On Started Freezing
- プレイヤーが凍結し始めたときに発火します。
- 変数:
  - `$$freezing_intensity` – 0.0 で凍結なし、1.0 で完全凍結

## On Stopped Freezing
- プレイヤーが凍結を停止したときに発火します。
- 変数:
  - (なし)

## On Fully Frozen
- プレイヤーが完全に凍結したときに 1 回発火します。
- 変数:
  - (なし)

## On Start Looking At Block
- クロスヘアが最初にブロックを指したときに 1 回発火します（最大 20 ブロック先）。
- 変数:
  - `$$block_key` – 対象ブロック
  - `$$block_pos_x` – ブロックの X 座標
  - `$$block_pos_y` – ブロックの Y 座標
  - `$$block_pos_z` – ブロックの Z 座標
  - `$$distance_to_player` – 目線からヒット位置までの距離

## On Stop Looking At Block
- クロスヘアがブロックを指さなくなったときに発火します（最後に対象だったブロックを報告、最大 20 ブロック先）。
- 変数:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`
  - `$$distance_to_player`

## On Start Looking At Entity
- クロスヘアが最初にエンティティを指したときに 1 回発火します（最大 20 ブロック先）。
- 変数:
  - `$$entity_key` – 対象エンティティの種類
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Stop Looking At Entity
- クロスヘアがエンティティを指さなくなったときに発火します（最後に対象だったエンティティを報告、最大 20 ブロック先）。
- 変数:
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Entity Spawned
- **サーバー側にも FancyMenu が必要です。** 接続中のワールド/サーバー内のどこかでエンティティがスポーンしたときに発火します。
- 変数:
  - `$$entity_key`
  - `$$distance_to_player` – 他ディメンションの場合は −1
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`
  - `$$dimension_key`
  - `$$is_same_dimension_as_player`

## On Entity Died
- **サーバー側にも FancyMenu が必要です。** 接続中のワールド/サーバー内でエンティティが死亡したときに発火します。
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

## On Entity Starts Being In Sight
- エンティティが初めて 200 ブロック以内で視界に入ったときに発火します。
- 変数:
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Entity Stops Being In Sight
- 以前見えていたエンティティが視界から外れるか、200 ブロックを超えて離れたときに発火します。
- 変数:
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Interacted With Entity
- プレイヤーがエンティティとのインタラクトに成功したときに発火します。
- 変数:
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Entity Mounted
- プレイヤーがエンティティに乗り始めたときに発火します。
- 変数:
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Entity Unmounted
- プレイヤーが現在乗っているエンティティから降りたときに発火します。
- 変数:
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Block Broke
- プレイヤーがブロックを破壊したときに発火します。
- 変数:
  - `$$block_key`
  - `$$broke_with_item_key` – 使用した道具、または EMPTY
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## On Block Placed
- プレイヤーがブロックを設置したときに発火します。
- 変数:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## On Interacted With Block
- プレイヤーがブロックとのインタラクトに成功したときに発火します。
- 変数:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## On Stepping On Block
- プレイヤーがブロックの上に乗ったときに発火します。
- 変数:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## On Enter Biome
- プレイヤーが新しいバイオームに入ったときに発火します。
- 変数:
  - `$$biome_key` – 入ったバイオーム

## On Leave Biome
- プレイヤーが現在のバイオームを離れたときに発火します。
- 変数:
  - `$$biome_key` – 直前までいたバイオーム

## On Enter Structure
- **サーバー側にも FancyMenu が必要です。** 大まかな構造物エリア検出です。構造物の近く/上/下で発火することがあります。
- 変数:
  - `$$structure_key` – 入った構造物

## On Leave Structure
- **サーバー側にも FancyMenu が必要です。** 大まかな検出です。構造物の外周付近で発火することがあります。
- 変数:
  - `$$structure_key` – 直前までいた構造物

## On Enter Structure (High Precision)
- **サーバー側にも FancyMenu が必要です。** プレイヤーが構造物のバウンディングボックス内に入ったときに発火します。
- 変数:
  - `$$structure_key`

## On Leave Structure (High Precision)
- **サーバー側にも FancyMenu が必要です。** プレイヤーが構造物のバウンディングボックスから出た後に発火します。
- 変数:
  - `$$structure_key`

## On Dimension Entered
- プレイヤーが新しいディメンションに入ったときに発火します。
- 変数:
  - `$$dimension_key` – 入ったディメンション

## On Start Swimming
- プレイヤーが泳ぎ始めたときに発火します。
- 変数:
  - `$$fluid_type` – 流体のリソースロケーション

## On Stop Swimming
- プレイヤーが泳ぐのをやめたときに発火します。
- 変数:
  - `$$fluid_type` – 泳ぐのをやめた流体

## On Start Touching Fluid
- プレイヤーが流体に触れ始めたときに発火します。
- 変数:
  - `$$fluid_type` – 触れた流体

## On Stop Touching Fluid
- プレイヤーが流体に触れなくなったときに発火します。
- 変数:
  - `$$fluid_type` – もはや触れていない流体

## On Music Track Started
- 新しい音楽トラックが始まったときに発火します。
- 変数:
  - `$$track_resource_location` – 音声ファイル
  - `$$track_display_name` – 人間が読める名前、または UNKNOWN
  - `$$track_artist` – アーティスト名、または UNKNOWN
  - `$$track_duration_ms` – ミリ秒（不明な場合は 0）

## On Music Track Stopped
- 現在の音楽トラックが終了または差し替えられたときに発火します。
- 変数:
  - `$$track_resource_location`
  - `$$track_display_name`
  - `$$track_artist`
  - `$$track_duration_ms`

## On World Sound Triggered
- 位置を持つワールドサウンドがプレイヤーの近くで再生開始されたときに発火します。
- 変数:
  - `$$sound_resource_location` – サウンドファイル
  - `$$sound_display_name` – 利用可能な場合の字幕名
  - `$$sound_origin_pos_x`
  - `$$sound_origin_pos_y`
  - `$$sound_origin_pos_z`
  - `$$sound_origin_distance_to_player`
  - `$$sound_origin_direction_from_player` – 向きに対する相対角度 0–360 度

## On Weather Changed
- 天候が全体的またはローカルに変化したときに発火します（バイオームの変化や屋内への移動で再度発火することがあります）。
- 変数:
  - `$$weather_type` – clear/rain/thunder
  - `$$weather_can_snow` – 雪が描画される場合は TRUE
  - `$$weather_can_rain` – 雨が描画される場合は TRUE

## On Started Burning
- プレイヤーが燃え始めたときに発火します。
- 変数:
  - (なし)

## On Stopped Burning
- プレイヤーが燃えなくなったときに発火します。
- 変数:
  - (なし)

## On Started Drowning
- プレイヤーが溺れダメージを受け始めたときに発火します。
- 変数:
  - (なし)

## On Position Changed
- プレイヤーのブロック座標が変わるたびに発火します。
- 変数:
  - `$$old_pos_x` – 以前のブロック X
  - `$$old_pos_y` – 以前のブロック Y
  - `$$old_pos_z` – 以前のブロック Z
  - `$$new_pos_x` – 新しいブロック X
  - `$$new_pos_y` – 新しいブロック Y
  - `$$new_pos_z` – 新しいブロック Z

## On Started Running
- プレイヤーがスプリントを始めたときに発火します。
- 変数:
  - (なし)

## On Stopped Running
- プレイヤーがスプリントをやめたときに発火します。
- 変数:
  - (なし)

## On Jump
- プレイヤーがジャンプするたびに発火します。
- 変数:
  - (なし)

## On Server Joined
- マルチプレイヤーサーバーへの参加に成功した後に発火します。
- 変数:
  - `$$server_ip` – 参加したサーバーのアドレス

## On Server Left
- マルチプレイヤーサーバーから切断した後に発火します。
- 変数:
  - `$$server_ip` – 離脱したサーバーのアドレス

## Singleplayer World Entered
- シングルプレイワールドの読み込みが完了し、操作が戻った後に発火します。
- 変数:
  - `$$world_name` – 表示名
  - `$$world_save_path` – 絶対セーブフォルダ
  - `$$world_difficulty` – 難易度キー
  - `$$world_cheats_allowed` – チートが有効なら TRUE
  - `$$world_icon_path` – 絶対アイコンパス
  - `$$world_is_first_join` – 初回訪問なら TRUE

## Singleplayer World Left
- シングルプレイワールドが閉じて保存が完了した後に発火します。
- 変数:
  - `$$world_name`
  - `$$world_save_path`
  - `$$world_difficulty`
  - `$$world_cheats_allowed`
  - `$$world_icon_path`

## On Other Player Joined World/Server
- 別のプレイヤーが現在のワールド/サーバーに参加したときに発火します。
- 変数:
  - `$$player_name` – 参加したプレイヤー名
  - `$$player_uuid` – UUID

## On Other Player Left World/Server
- 別のプレイヤーが現在のワールド/サーバーから退出したときに発火します。
- 変数:
  - `$$player_name`
  - `$$player_uuid`

## On Other Player Died
- 現在のワールド内の別プレイヤーが死亡したときに発火します。
- 変数:
  - `$$player_name`
  - `$$player_uuid`
  - `$$death_pos_x`
  - `$$death_pos_y`
  - `$$death_pos_z`

## On Item Picked Up
- プレイヤーがアイテムエンティティを拾ったときに発火します。
- 変数:
  - `$$item_key` – 拾ったアイテムのリソースロケーション

## On Item Dropped
- プレイヤーがインベントリからアイテムを落としたときに発火します。
- 変数:
  - `$$item_key` – 落としたアイテムのリソースロケーション

## On Item Consumed
- プレイヤーがアイテムの消費を完了したときに発火します。
- 変数:
  - `$$item_key` – 消費したアイテム

## On Item Hovered in Inventory
- 任意のインベントリ画面でアイテムにカーソルを合わせたときに発火します。
- 変数:
  - `$$item_key` – カーソルを合わせたアイテムのリソースロケーション
  - `$$item_display_name_string` – プレーンテキストのアイテム表示名
  - `$$item_display_name_json` – JSON コンポーネントのアイテム表示名

## On Item Used
- プレイヤーがアイテムを使用したときに発火します。
- 変数:
  - `$$item_key` – 使用したアイテム
  - `$$used_on_type` – block/entity/self/none
  - `$$used_on_entity_key` – 対象エンティティの種類、または空
  - `$$used_on_block_key` – 対象ブロック、または空
  - `$$target_pos_x` – 対象 X、または -1
  - `$$target_pos_y` – 対象 Y、または -1
  - `$$target_pos_z` – 対象 Z、または -1

## On Item Broke
- プレイヤーのインベントリ内のアイテムが壊れたときに発火します。
- 変数:
  - `$$item_key` – 壊れたアイテム
  - `$$item_type` – tool/armor/other
