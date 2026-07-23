---
title: アクションスクリプト
description: ボタン、スライダー、ティッカーなどでアクションスクリプトを使う方法。
---
# アクションスクリプト

アクションスクリプトは、[Button](./elements#button) がクリックされたとき、[Ticker](./elements#ticker) が更新されたとき、[Slider](./elements#slider) が変化したとき、画面が開閉されたとき、またはその他の対応イベントが発生したときに、設定されたタスクを実行します。**if**、**else-if**、**else**、**while** などの文によって条件付き制御を追加できます。

> [!CAUTION]
> インポートされたアクションスクリプトは、ファイルの変更、サーバーへの接続、リンクの開封、コマンドの実行を行う場合があります。信頼できるソースのものだけを使用してください。

<img src="https://github.com/Keksuccino/FancyMenu/blob/master/assets/docs/action_script_editor.png?raw=true" alt="Action script editor" style="max-width:800px;width:100%;height:auto;">

# アクションとは？

**アクション**とは、トリガーされたときに FancyMenu が実行するタスクや処理のことです。たとえば、アクションは新しい画面を開いたり、チャットメッセージを送信したり、[Audio element](./elements#audio) の音量を調整したりできます。FancyMenu のエディタでは、必要に応じて、URL やサーバーアドレスなどの追加情報を与える値とともにアクションを設定します。

# 文

より複雑な動作を作成するために、FancyMenu はアクションスクリプト内で制御文をサポートしています。

| 文 | 動作 |
|---|---|
| **If** | [条件](./conditions) が満たされた場合にのみ、そのアクションを実行します。 |
| **Else-If** | 直前の **If** または **Else-If** が実行されなかった場合に、別の [条件](./conditions) を確認します。 |
| **Else** | それ以前の **If** または **Else-If** の条件がどれも満たされなかった場合に実行します。 |
| **While** | [条件](./conditions) が真である間、そのアクションを繰り返し実行します。無限ループを防ぐため 3 秒後に停止します。タイマーとして使用しないでください。 |

# ブロック

ブロックをスクリプトに追加すると、スクリプトの実行フローやタイミングをより細かく制御でき、便利な QoL 機能も利用できます。

| ブロック | 動作 |
|---|---|
| **Delay** | スクリプトの残りの部分を止めずにカウントダウンを開始します。ネストされたアクションは遅延後に実行可能になり、画面の再初期化でカウントダウンはリセットされます。 |
| **Execute Later** | ブロックに到達するたびに、遅延後にネストされたアクションの新しい実行を予約します。 |
| **Comment** | 整理用のメモをスクリプト内に追加し、アクションは実行しません。 |

# スクリプトの実行

アクションは上から下へ実行されます。失敗したアクションはログに記録され、その後スクリプトは続行されます。

ダウンロード、ZIP の展開、HTTP リクエストは後で完了するため、次のアクションは待機しません。結果に依存する後続処理がある場合は、[**On File Downloaded via Action**](./listeners#on-file-downloaded-via-action-file_downloaded_via_action)、[**On ZIP Extracted via Action**](./listeners#on-zip-extracted-via-action-zip_extracted_via_action)、または HTTP 応答変数を使用してください。

# アクションスクリプトはどこで使えますか？

アクションスクリプトは柔軟で、レイアウト全体で使用できます。たとえば、次のような場所に割り当てられます。

- [**Buttons**](./elements#button): ボタンがクリックされたときにアクションを実行します。
- [**Tickers**](./elements#ticker): レイアウト内の画面情報を更新するために、アクションスクリプトを継続的に実行します。
- [**Sliders**](./elements#slider): スライダーの値が変わるたびにアクションスクリプトをトリガーします。
- **Screen Events:** 画面が開いたり閉じたりしたときにスクリプトを実行します（たとえば、メニューが表示されたときに音を鳴らす）。
- [**Listeners**](./listeners): リスナーが設定されたイベントを受信すると、アクションスクリプトを実行します。
- [**Schedulers**](./schedulers): 画面が開いていなくても、一定間隔でアクションを実行します。

# アクションでプレースホルダーを使う

アクションの値は、**プレースホルダー**による動的な内容をサポートしています。ほとんどの場合、これらのプレースホルダーは JSON 風の構文を使い、アクション実行時にライブデータへ置き換えられます。

## JSON 風プレースホルダー

これらは、レイアウト内の多くの場所で使用できる通常の [プレースホルダー](./placeholders) です。

構文は次のとおりです。

```json
{"placeholder": "placeholder_id", "values": {"key1": "value1", "key2": "value2"}}
```

プレーヤー名、画面サイズ、[**Calculator** プレースホルダー](./placeholders#calculator-calc) を使った計算値などのゲームデータを取得できます。さらに、より高度な用途のためにプレースホルダーを入れ子にすることもできます。

## `$$` プレースホルダー（変数）

`$$` 値は、それを実行している機能から特定のアクションスクリプトに渡される読み取り専用の値です。

たとえば、[Slider](./elements#slider) は現在の値を `$$value` として提供します。

各 [listener](./listeners) は、押されたマウスボタンや入力された構造など、提供する `$$` 値を文書化しています。

`$$` 名は大文字と小文字を区別し、その値を提供するスクリプト内でのみ機能します。[Listeners](./listeners#listener-variables) を参照してください。

## アクション値の区切り文字

各アクションで表示されている正確な区切り文字を使用してください: `:`、`||`、または `|||`。フィールド内で区切り文字をエスケープする構文はありません。

プレースホルダーは値を分割する前に置換されます。`set_variable` では、最初のコロンだけが名前と値を分け、それ以降のコロンは値の一部として残ります。

## テキスト値

[FancyMenu の書式コード](./text-formatting#minecraft-text-formatting) は、アクションが書式付きテキストを受け付ける場所では、Minecraft の `§` 文字の代わりに `&` を使います。

- [**Send Chat Message/Command**](#send-chat-messagecommand-sendmessage) と [**Paste to Chat**](#paste-to-chat-paste_to_chat) はこれらの書式コードをサポートします。
- [**Display In Chat [Client-Side]**](#display-in-chat-client-side-display_in_chat_client_side) は、プレーンテキストまたはシリアライズされた Minecraft テキストコンポーネント JSON を受け付けます。
- [**Open URL in Browser**](#open-url-in-browser-openlink) は、URL を OS に渡す前に同じ書式コード変換を適用します。

# アクションの設定と編集方法

要素のアクションと文ブロックを編集するには、**要素を右クリック**して **Manage Action Script** を選択します。エディタでは次のことができます。

- **新しいアクションまたは文を追加する:** 新しいアクション項目や制御文（if、else-if、else、while）を挿入してスクリプトを構築します。
- **既存のアクションまたは文を編集する:** アクション値を変更したり、制御ロジックを変更したりできます。
- **アクションまたは文を削除する:** 不要なアクションをスクリプトから削除します。

リスナースクリプトは [**Customization -> Manage Listeners**](./listeners#using-listeners) から作成・編集します。

# アクションスクリプトエディタのショートカット

## ショートカット

- `DEL` : 選択中の項目をすばやく削除
- `ENTER` : 選択中の項目のインライン編集を開始する（または、選択中の項目にインライン編集がない場合は編集画面を開く）
- `Ctrl/Command + C` : 選択中のアクションをコピー（現時点ではアクションのみ対応）
- `Ctrl/Command + V` : 以前コピーしたアクションを貼り付け
- `Ctrl/Command + Z` : 1 ステップ戻る（元に戻す）
- `Ctrl/Command + Y` : 1 ステップ進む（やり直し）
- `ARROW UP` : 現在選択中の項目から 1 つ上へ移動
- `ARROW DOWN` : 現在選択中の項目から 1 つ下へ移動
- `SHIFT + ARROW UP` : 選択中の項目を 1 つ上へ移動
- `SHIFT + ARROW DOWN` : 選択中の項目を 1 つ下へ移動
- `A` : アクション選択画面をすばやく開いて新しいアクションを追加
- `Ctrl/Command + S` : エディタウィンドウで完了/保存

## 編集

- アクションの値をダブルクリックすると、完全な値編集画面に入らずに値を編集できます。
- IF 文の連鎖（追加された ELSE/ELSE-IF 文を含む）、WHILE ループ、フォルダは折りたたみ可能です（見た目のみで、スクリプトのロジックには影響しません）。
- エディタは常に、選択中の項目の下（または選択中の連鎖/ループ/フォルダ内）に新しいアクションを追加します。
- 濃いグレーのスクリプト領域の背景を右クリックすると、アクション、文、その他重要な項目を追加するためのコンテキストメニューが開きます。

# アクションの詳細

このセクションでは、FancyMenu に組み込まれているアクションを一覧表示します。

## 次のトラック (`audio_next_track`)

**目的:** [Audio element](./elements#audio) の次のトラックに移動します

**値:** 必須 — `audio_element_identifier`（制御するオーディオ要素の ID）

## 前のトラック (`audio_previous_track`)

**目的:** [Audio element](./elements#audio) の前のトラックに移動します

**値:** 必須 — `audio_element_identifier`（制御するオーディオ要素の ID）

## トラック音量を設定 (`set_audio_element_volume`)

**目的:** [Audio element](./elements#audio) の音量を設定します（`0.0`～`1.0`）

**値:** 必須 — `element_identifier:volume`

## 再生/一時停止を切り替え (`audio_toggle_play`)

**目的:** [Audio element](./elements#audio) の現在のトラックを再生と一時停止の間で切り替えます

**値:** 必須 — `audio_element_identifier`

## オーディオを再生 (`play_audio`)

**目的:** オーディオリソースを 1 回再生します。このアクションで開始された音声は、後で [**Stop All Action Audios**](#stop-all-action-audios-stop_all_action_audios) で停止できます。

**値:** 必須 — `audioSource`、`soundChannel`、`baseVolume` を含む JSON 設定

**例:** `{"audioSource":"[source:local]/config/fancymenu/assets/example.ogg","soundChannel":"master","baseVolume":1.0}`

**動作:**

- `baseVolume` は `0.0`～`1.0` にクランプされます。
- 不明なサウンドチャンネルは Master チャンネルを使用します。
- このアクションは非同期の [Ticker](./elements#ticker) からは実行できません。FancyMenu は代わりにエラーを表示します。
- FancyMenu はオーディオリソースの準備が整うまで最大 10 秒待機します。
- 正常に開始したトラックは [**Stop All Action Audios**](#stop-all-action-audios-stop_all_action_audios) で停止できます。

## すべてのアクション音声を停止 (`stop_all_action_audios`)

**目的:** [**Play Audio** アクション](#play-audio-play_audio) で開始されたすべてのオーディオトラックを停止します。これは [Audio element](./elements#audio)、メニューの開閉音、ボタン音、その他のオーディオシステムは停止しません。

**値:** 不要

## 動画要素の音量を設定 (`set_video_element_volume`)

**目的:** [Video element](./video) の音量を設定します（`0.0`～`1.0`）

**値:** 必須 — `video_element_identifier:volume`

## 動画要素の再生位置を設定 (`set_video_element_play_time`)

**目的:** [Video element](./video) をミリ秒単位のタイムスタンプにシークします

**値:** 必須 — `video_element_identifier:timestamp_ms`

## 動画要素の一時停止状態を切り替え (`toggle_video_element_pause_state`)

**目的:** [Video element](./video) の一時停止状態を切り替えます

**値:** 必須 — `video_element_identifier`

## 動画メニュー背景の音量を設定 (`set_video_menu_background_volume`)

**目的:** [Video menu background](./video) の音量を設定します（`0.0`～`1.0`）

**値:** 必須 — `background_identifier:volume`

> [!NOTE]
> 背景の識別子を取得するには、エディタ背景を右クリックして 'Copy Background Identifier' をクリックしてください。

## 動画メニュー背景の再生位置を設定 (`set_video_menu_background_play_time`)

**目的:** [Video menu background](./video) をミリ秒単位のタイムスタンプにシークします

**値:** 必須 — `background_identifier:timestamp_ms`

> [!NOTE]
> 背景の識別子を取得するには、エディタ背景を右クリックして 'Copy Background Identifier' をクリックしてください。

## 動画メニュー背景の一時停止状態を切り替え (`toggle_video_menu_background_pause_state`)

**目的:** [Video menu background](./video) の一時停止状態を切り替えます

**値:** 必須 — `background_identifier`

> [!NOTE]
> 背景の識別子を取得するには、エディタ背景を右クリックして 'Copy Background Identifier' をクリックしてください。

## レイアウトを切り替え (`toggle_layout`)

**目的:** `.txt` を除いたファイル名でレイアウトを切り替え（有効/無効）ます

**値:** 必須 — `layout_name`

## レイアウトを有効化 (`enable_layout`)

**目的:** `.txt` を除いたファイル名でレイアウトを有効化し、保存します

**値:** 必須 — `layout_name`

## レイアウトを無効化 (`disable_layout`)

**目的:** `.txt` を除いたファイル名でレイアウトを無効化し、保存します

**値:** 必須 — `layout_name`

これら 3 つのレイアウトアクションはいずれも、状態をレイアウトファイルに保存し、現在の画面を即座に更新します。`.txt` を付けない、大文字小文字を区別するファイル名を使用してください。

## 画面またはカスタム GUI を開く (`opengui`)

**目的:** 識別子で画面（バニラ、MOD、またはカスタム GUI）を開きます

**値:** 必須 — `screen_identifier`

[Screen Identifiers](./screen-identifiers) のデバッグオーバーレイから、正確な大文字小文字を区別する識別子をコピーしてください。

一部の MOD 画面は直接生成できません。開けない場合は、その画面を通常開くウィジェットに対して [**Mimic Vanilla/Mod Button**](#mimic-vanillamod-button-mimicbutton) を使用してください。

## 画面を閉じる (`closegui`)

**目的:** アクティブな画面を閉じます

**値:** 不要

## 画面を更新 (`update_screen`)

**目的:** 現在の画面を再初期化します

**値:** 不要

## 前の画面に戻る (`back_to_last_screen`)

**目的:** [Custom GUI](./custom-guis) の親、または直近に閉じた画面インスタンスに戻ります

**値:** 不要

## サーバーに参加 (`joinserver`)

**目的:** プレーヤーを Minecraft サーバーに接続します

**値:** 必須 — `server_ip` または `server_ip:port`

このアクションは、ワールドまたはサーバーがすでに読み込まれている間は実行できません。ポートは省略時に `25565` が使用されます。アドレスが Minecraft の保存済みサーバー一覧にない場合、FancyMenu はそれを追加して保存します。

## ワールドに入る (`loadworld`)

**目的:** Minecraft のワールドに入ります

**値:** 必須 — `world_folder_name`

値はセーブフォルダ名です。そのセーブが存在しない場合、または別のワールド/サーバーがすでに読み込まれている場合、このアクションは何もしません。

## 最後のワールド/サーバーに参加 (`join_last_world`)

**目的:** プレーヤーが最後にいたワールドまたはサーバーに入る/参加します

**値:** 不要

このアクションは、別のワールド/サーバーが読み込まれている間は実行できません。Minecraft の保存済みサーバー一覧にない記憶済みサーバーは、接続前に追加されて保存されます。

## ワールドまたはサーバーから退出 (`disconnect_server_or_world`)

**目的:** ワールドまたはサーバーから退出し、指定した画面を開きます

**値:** 必須 — `screen_identifier`

このアクションは、ワールドとプレーヤーが読み込まれているときのみ実行されます。対象は [Custom GUI](./custom-guis) の識別子、または FancyMenu が構築できる [screen identifier](./screen-identifiers) です。対象を開けない場合、FancyMenu はタイトル画面に戻ります。

## Minecraft を終了 (`quitgame`)

**目的:** Minecraft を完全に終了します

**値:** 不要

## チャットメッセージ/コマンドを送信 (`sendmessage`)

**目的:** チャットメッセージを送信するか、チャットコマンドを実行します。メッセージテキストは [FancyMenu の書式コード](./text-formatting#minecraft-text-formatting) をサポートします。

**値:** 必須 — `message_text` または `/command_text`

## 統合サーバーとしてコマンドを実行 (`execute_command_as_integrated_server`)

**目的:** シングルプレイで統合サーバーとしてコマンドを強制実行し、権限とチート設定を無視します。

**値:** 必須 — コマンドテキスト、たとえば `/give @p minecraft:diamond 1`

> [!WARNING]
> このアクションは、シングルプレイ中かつワールドが **LAN 公開されていない** 場合にのみ機能します。統合サーバーが存在しない場合、または統合サーバーが LAN に公開されている場合は、意図的に何もしません。

## チャットに貼り付け (`paste_to_chat`)

**目的:** プレーヤー/ワールドが読み込まれている間、書式付きテキストをチャット入力欄に貼り付けます

**値:** 必須 — `true:Text` または `false:Text`

チャットがまだ開いていない場合、FancyMenu はチャットを開いて入力テキストを設定します。チャットがすでに開いている場合、`true` は既存の入力に追加し、`false` は置き換えます。

## チャットに表示 [クライアント側] (`display_in_chat_client_side`)

**目的:** ワールドまたはサーバーが読み込まれている間に、クライアント側のチャットメッセージを表示します。サーバーには何も送信しません。

**値:** 必須 — `text_or_json`

値はプレーンテキストまたはシリアライズされた Minecraft テキストコンポーネントにできます。ワールドが読み込まれていない場合、このアクションは何もしません。

## FM データをサーバーに送信 (`send_fm_data_to_server`)

**目的:** [FM Data](./fm-data) を現在の FancyMenu サーバーに送信します。

**値:** 必須 — `data_identifier||data`

## リモートサーバーに接続 (`connect_to_remote_server`)

**目的:** クライアント起点の WebSocket 接続を外部のリモートサーバーに開くか、再利用します。

**値:** 必須 — リモートサーバー URL、たとえば `wss://example.com/ws`

受け付ける URL 形式については [Remote Server Communication](./remote-server-communication#url-modes) を参照してください。

## リモートサーバーにデータを送信 (`send_data_to_remote_server`)

**目的:** リモートサーバー接続を開くか再利用し、テキストデータを送信します。

**値:** 必須 — `remote_server_url||data`

## リモートサーバー接続を閉じる (`close_remote_server_connection`)

**目的:** リクエスト ID によって特定のリモートサーバー接続を閉じます。

**値:** 必須 — リクエスト ID。通常は [**On Remote Server Connected**](./listeners#on-remote-server-connected-remote_server_connected) の `$$request_id`

## すべてのリモートサーバー接続を閉じる (`close_all_remote_server_connections`)

**目的:** FancyMenu が開いたすべてのアクティブなリモートサーバー接続を閉じます。

**値:** 不要

## ブラウザーで URL を開く (`openlink`)

**目的:** FancyMenu の確認プロンプトなしで、URL を OS の既定の処理に渡します

**値:** 必須 — `https://example.com`

信頼できる `https://` リンクを使用してください。FancyMenu は URL を OS に渡す前に確認プロンプトを表示しません。

## テキストをクリップボードにコピー (`copytoclipboard`)

**目的:** テキストをクリップボードにコピーします

**値:** 必須 — `text_to_copy`

## ゲームログに出力 (`print_to_log`)

**目的:** ゲームログに 1 行を書き込みます

**値:** 必須 — `text_to_log`

## 変数値を設定（FM 変数） (`set_variable`)

**目的:** テキスト内容を [FancyMenu 変数](./variables) に保存します

**値:** 必須 — `variable_name:variable_value`

最初のコロンが名前と値を分けます。それ以降のコロンは値の一部として残ります。変更はすぐに保存されます。

## すべての変数をクリア（FM 変数） (`clear_variables`)

**目的:** 保存されているすべての [FancyMenu 変数](./variables) の値をクリアします

**値:** 不要

## HTTP リクエストを送信 (`send_http_request`)

**目的:** バックグラウンドで HTTP/HTTPS リクエストを開始します。レスポンスをログに出したり、変数に保存したりできます

**値:** 必須 — HTTP リクエスト設定

| 設定 | 動作 |
|---|---|
| URL | HTTP または HTTPS のエンドポイント |
| Method | `GET`、`POST`、`PUT`、`DELETE`、`PATCH`、`HEAD`、または `OPTIONS` |
| Body | `GET` と `HEAD` 以外のメソッドで送信されます |
| Content type | リクエストの `Content-Type` 値 |
| Timeout | 接続とレスポンス読み取りの両方に使われる秒数 |
| Log response | レスポンスを読み取り、ログに書き込みます |
| Response variable | レスポンスを読み取り、リクエスト完了後に保存します |
| Single-line response | 保存前にレスポンスの改行を削除します |
| Authentication | なし、Basic、Bearer、または API key |
| Headers | 任意のカスタムリクエストヘッダー |

リクエストは非同期で実行されるため、次のアクションは待機しません。レスポンス本文は、ログ記録が有効な場合、またはレスポンス変数が設定されている場合にのみ読み取られます。成功しなかった場合の本文はエラーレスポンスから読み取られます。パスワードやアクセストークンはアクション設定に保存しないでください。

## リソースパックを管理 (`manage_resource_pack`)

**目的:** リソースパックを有効化、無効化、または切り替えします。必要に応じて再読み込みも行えます

**値:** 必須 — `pack_name_or_id|||MODE|||reload_bool`

表示名と内部のパック ID は、大文字小文字を区別せずに照合されます。必須としてマークされたパックは無効化できません。

## リソースパックを再読み込み (`reload_resource_packs`)

**目的:** Minecraft のリソースパックを再読み込みします。組み込みの 5 秒クールダウンにより、その期間中の繰り返しトリガーは無視され、再読み込みの連打を防ぎます。

**値:** 不要

## FancyMenu を再読み込み (`reloadmenu`)

**目的:** レイアウト、[Custom GUIs](./custom-guis)、[panoramas](./panoramas)、[slideshows](./slideshows)、設定、および FancyMenu が管理するリソースを再読み込みします

**値:** 不要

これは Minecraft のリソースパックは再読み込みしません。必要な場合は [**Reload Resource Packs**](#reload-resource-packs-reload_resource_packs) を使用してください。

> [!WARNING]
> 再読み込みは重い処理です。[Ticker](./elements#ticker) や頻繁に発火する [listener](./listeners) ではなく、意図したボタン操作からトリガーしてください。

## 要素アニメーターを切り替え (`toggle_element_animator`)

**目的:** 保存された再生状態を切り替え、対応するアクティブな Animator タイムラインをリセットします

**値:** 必須 — `animator_identifier`

設定と識別子の詳細は [Element Animator](./element-animator) を参照してください。

## 要素アニメーターを有効化 (`enable_element_animator`)

**目的:** 再生を有効化します。アクティブな Animator タイムラインは、状態が無効から有効へ変わったときのみリセットされます

**値:** 必須 — `animator_identifier`

## 要素アニメーターを無効化 (`disable_element_animator`)

**目的:** 再生を無効化し、対応するアクティブな Animator タイムラインをリセットします

**値:** 必須 — `animator_identifier`

## 要素アニメーターをリセット (`reset_element_animator`)

**目的:** 再生が有効かどうかを変えずに、対応するアクティブな Animator タイムラインをリセットします

**値:** 必須 — `animator_identifier`

## バニラ/Mod ボタンを模倣 (`mimicbutton`)

**目的:** バニラまたは MOD のボタンのクリック動作を模倣します

**値:** 必須 — 完全な [widget locator](./widget-locators)、たとえば `example.menu.identifier:505280`

## キーバインドを模倣 (`mimic_keybind`)

**目的:** Minecraft のキーボードまたはマウスのキーバインドを実行します。必要に応じて押し続けることもできます

**値:** 必須 — `keybind_id|||keep_pressed_bool|||duration_ms`

| フィールド | 意味 |
|---|---|
| `keybind_id` | `key.jump` などの Minecraft キーバインド識別子 |
| `keep_pressed_bool` | キーを押し続ける場合は `true`、通常の押下なら `false` |
| `duration_ms` | `keep_pressed_bool` が `true` のときの保持時間。既定は `1000` |

## テキスト入力欄の値を設定 (`set_text_input_field_value`)

**目的:** カスタムまたはバニラの [Text Input Field](./elements#text-input-field) の値を要素識別子で設定します。

**値:** 必須 — `element_identifier|||new_value|||force_set_when_inactive`

3 つのフィールドは triple-pipe 区切り `|||` で分ける必要があります。`force_set_when_inactive` を `true` にすると無効化された入力欄も更新します。`false` の場合、非アクティブな欄は変更されません。

## ゲームディレクトリにファイルを作成 (`create_file_in_game_dir`)

**目的:** アクティブなゲームディレクトリを基準に空ファイルを作成します。`.minecraft/` プレフィックスを指定すると、現在のインスタンスと異なる場合でも標準の Minecraft ディレクトリを対象にできます。

**値:** 必須 — `file_path`

例: `config/some_mod_folder/new_file.txt`。親ディレクトリが存在しない場合は作成され、既存ファイルは変更されません。

## ゲームディレクトリのファイル/フォルダを削除 (`delete_file_in_game_dir`)

**目的:** アクティブなゲームディレクトリを基準にファイルを削除するか、フォルダを再帰的に削除します。`.minecraft/` を付けると標準の Minecraft ディレクトリを対象にします。フォルダ内の **すべての直接ファイル** を削除するには、末尾に `*` を付けます（サブディレクトリは無視され、フォルダ自体は残ります）。

**値:** 必須 — `target_path`

たとえば `config/downloads/*` は `config/downloads/` の直下にあるファイルを削除しますが、サブディレクトリには入らず、それらを削除もしません。

## ゲームディレクトリのファイル/フォルダをコピー (`copy_file_in_game_dir`)

**目的:** アクティブなゲームディレクトリ内でコピーします。`.minecraft/` は標準の Minecraft ディレクトリを対象にします。名前付きディレクトリは再帰的にコピーされます。**ソース** パスの末尾に `*` を付けると、直下の子ファイルだけをすべてコピーします。コピー先はディレクトリでなければならず、`*` は使用できません。

**値:** 必須 — `source||destination`

たとえば `config/source/*||config/destination/` は `config/source/` の直下にあるファイルだけをコピーします。ワイルドカードソースの場合、FancyMenu は必要に応じてコピー先ディレクトリを作成しますが、ソースのサブディレクトリはコピーしません。コピーは既存のコピー先や衝突するファイルを上書きせず、拒否します。

## ゲームディレクトリのファイル/フォルダを移動 (`move_file_in_game_dir`)

**目的:** アクティブなゲームディレクトリ内で移動します。`.minecraft/` は標準の Minecraft ディレクトリを対象にします。**ソース** パスの末尾に `*` を付けると、直下の子ファイルだけをすべて移動します。コピー先はディレクトリでなければならず、`*` は使用できません。

**値:** 必須 — `source||destination`

たとえば `config/source/*||config/destination/` は `config/source/` の直下にあるファイルだけを移動します。ワイルドカードソースの場合、FancyMenu は必要に応じてコピー先ディレクトリを作成しますが、ソースのサブディレクトリはそのまま残します。移動は既存のコピー先や衝突するファイルを上書きせず、拒否します。

## ゲームディレクトリのファイル/フォルダ名を変更 (`rename_file_in_game_dir`)

**目的:** ファイルまたはフォルダを現在の親ディレクトリ内で名前変更します。`.minecraft/` は標準の Minecraft ディレクトリを対象にします。内容はそのまま保持され、既存のターゲット名は拒否されます。

**値:** 必須 — `path||new_name`

## ゲームディレクトリにファイルをダウンロード (`download_file_to_game_dir`)

**目的:** アクティブなゲームディレクトリを基準としたディレクトリへ、バックグラウンドでファイルをダウンロードします。`.minecraft/` は標準の Minecraft ディレクトリを対象にします。

**値:** 必須 — `url||target_folder`

2 つ目のフィールドは **ターゲットディレクトリ** であり、完全な保存先ファイルパスではありません。FancyMenu は必要に応じてディレクトリを作成し、レスポンスの `Content-Disposition` ヘッダーからファイル名を決定し、なければ URL パスを使用します。解決された名前は使用前に URL デコードとサニタイズが行われます。どちらのソースからも有効な名前が得られない場合、FancyMenu が名前を生成します。同名の既存ファイルは上書きされます。

[**On File Downloaded via Action** リスナー](./listeners#on-file-downloaded-via-action-file_downloaded_via_action) は、ダウンロード成功・失敗の両方の試行後に発火し、URL、解決されたターゲットパス、成功状態を公開します。

成功時、`$$target_file_path` は保存されたファイルパスです。失敗時、最終ファイル名が解決されていないため、ターゲットディレクトリだけが含まれることがあります。

## ゲームディレクトリ内の ZIP を展開 (`extract_zip_file_in_game_dir`)

**目的:** アクティブなゲームディレクトリまたは標準の `.minecraft` ディレクトリ内のターゲットフォルダへ ZIP を展開します。完了時に [**On ZIP Extracted via Action**](./listeners#on-zip-extracted-via-action-zip_extracted_via_action) を発火します。

**値:** 必須 — `source_zip_path||target_folder_path`

名前が一致する既存ファイルは置き換えられます。信頼できる ZIP ファイルのみを展開してください。

## ゲームディレクトリ内のファイル/フォルダを開く (`open_file_folder_in_game_dir`)

**目的:** ファイルまたはフォルダを OS の既定アプリで開きます。安全上の理由から、対象はゲームディレクトリまたは既定の `.minecraft` ディレクトリ内にある必要があります。

**値:** 必須 — `target_path`

## ゲームディレクトリにファイルを書き込む (`write_file_in_game_dir`)

**目的:** アクティブなゲームディレクトリを基準にテキストを書き込む、または追記します。`.minecraft/` は標準の Minecraft ディレクトリを対象にします。ファイルや親ディレクトリがなければ作成します。`\n` で改行を挿入できます。`append_bool=false` で既存ファイルを置き換えます。

**値:** 必須 — `path|||content|||append_bool`

## システムからファイルを選択 (`select_file_to_game_dir`)

**目的:** ネイティブのファイルピッカーを開き、選択したファイルをアクティブなゲームディレクトリ内、またはプレフィックス指定時は標準の `.minecraft/` にコピーします。拡張子フィルター、カスタムフィルターラベル、上書き切り替えに対応しています。

**値:** 必須 — `target_path|||filter_description|||extensions|||overwrite_bool`

`target_path` は完全な保存先ファイルパスです。複数の拡張子は `;` または `,` で区切ります。たとえば `png;jpg`。拡張子リストが空の場合はすべてのファイルが許可されます。`overwrite_bool` が `false` の場合、既存の保存先ファイルを置き換える代わりにアクションは失敗します。

[**On File Selected** リスナー](./listeners#on-file-selected-file_selected_via_action) は、ファイルがコピーされたとき、ピッカーがキャンセルされたとき、または選択に失敗したときに発火します。選択されたパス、解決されたターゲットパス、成功/キャンセル状態、および失敗理由を公開します。

## トーストを表示 (`show_toast`)

**目的:** 設定可能なトースト通知を表示します

**値:** 必須 — JSON 形式のトースト設定

エディタはこのアクションを JSON として保存します。値を手動で編集するよりも、設定ウィンドウの使用を推奨します。

| フィールド | 意味 |
|---|---|
| `width` | `120`～`320` ピクセルにクランプされます |
| `durationMs` | `1000`～`600000` ミリ秒にクランプされます |
| `title` | プレーンテキスト、シリアライズされた Minecraft テキストコンポーネント、または空 |
| `message` | プレーンテキスト、シリアライズされたテキストコンポーネント、または空 |
| `iconSource` | 任意の [image source](./resources) |
| `backgroundSource` | 任意の [image source](./resources) |

## スケジューラーを開始 (`start_scheduler`)

**目的:** スケジューラー ID でスケジューラーを開始します。

**値:** 必須 — `scheduler_id`

スケジューラー ID の作成と管理については [Schedulers](./schedulers) を参照してください。

## スケジューラーを停止 (`stop_scheduler`)

**目的:** スケジューラー ID でスケジューラーを停止します。

**値:** 必須 — `scheduler_id`

## Minecraft オプションを設定 (`edit_minecraft_option`)

**目的:** Minecraft の設定オプションを編集します

**値:** 必須 — `option_name:set_to_value`
