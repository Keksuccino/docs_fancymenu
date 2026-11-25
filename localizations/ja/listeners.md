---
title: リスナー
description: キー入力、チャットメッセージ、新しい実績の解除など、ゲーム内で何かが起きたときにアクションスクリプトを実行します。
sourceBlobSha: b8417f6287ac413d2d44e0fc5c2383c0b0fa6e1e
---

# リスナー

リスナーは、キーが押されたとき、画面が開いたとき、実績を解除したときなど、ゲーム内で何かが起きると[アクションスクリプト](/action-scripts)を実行します。どのメニューやプレイ中でも動作し、レイアウトには属しません。

ほとんどのリスナーは、押されたキーの名前など、何が起きたかを示す変数もスクリプトに渡します。

<img width="800" alt="タイトル画面でキーを押すと、押したキーの名前がトーストに表示される" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/listeners_trigger.gif?raw=true">

> [!CAUTION]
> リスナーは、メニューが開いていないときでも、ファイル、ネットワーク、コマンド、クリップボード、リソースパック、リンクに関するアクションを実行できます。信頼できる人のプロフィールやファイルに含まれるリスナーだけを使用してください。

# リスナーを追加する

<img width="800" alt="リスナーの管理を開き、キーボードキー押下時リスナーを追加してトースト表示アクションを設定し、Hキーを押して試す" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/listeners_make.gif?raw=true">

1. **メニューバー -> カスタマイズ -> リスナーの管理**を開きます。
2. **リスナーを追加**をクリックします。
3. **使用可能なリスナー**でイベントをクリックします。検索バーを使って、名前や説明からリスナーを探せます。
   - **リスナーの説明**には、リスナーの動作と、利用できる変数が表示されます。
   - **変数をクリップボードにコピー**をクリックすると、変数名をコピーできます。
   - **説明を別ウィンドウで開く**をクリックすると、説明が独立したウィンドウで開きます。
4. **完了**をクリックするか、リスナーをダブルクリックします。アクションスクリプトエディターが開きます。
5. 実行するアクションを追加し、**完了**をクリックします。[アクションスクリプト](/action-scripts#making-an-action-script)を参照してください。
6. **リスナーの管理**で**完了**をクリックして保存します。リスナーはすぐに動作します。

**キャンセル**をクリックすると、確認後に**リスナーの管理**での変更がすべて破棄されます。

# リスナーを管理する

<img width="800" alt="5つのリスナーが並ぶリスナーの管理ウィンドウ。1つが選択され、右側にそのアクションスクリプトが表示されている" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/listeners_manage.png?raw=true">

- リスナーをクリックすると、種類とアクションスクリプトが右側に表示されます。
- **アクションを編集**をクリックするか、リスナーを右クリックすると、そのアクションスクリプトが開きます。
- リスナー名をダブルクリックすると、`ヘルプキー`のように名前を変更できます。`Enter`で確定し、`Esc`でキャンセルします。名前を空欄にすると、リスナーの種類が再び表示されます。
- **リスナーを削除**をクリックすると、選択したリスナーが削除されます。
- **AI用にエクスポート**をクリックすると、未保存の変更も含め、選択したリスナーまたはすべてのリスナーを[AIチャット](/export-for-ai)用にコピーします。

リスナーは`config/fancymenu/listener_instances.txt`に保存されます（[データ保存場所](/data-storage-locations)を参照）。各[プロフィール](/profiles)には、それぞれ固有のリスナーがあります。

# リスナー変数

リスナーの変数名は`$$`で始まり、そのスクリプト内のどこでも使用できます。すべてのアクションの値や、[IF文](/action-scripts#if-else-if-and-else)の条件で使えます。大文字と小文字は区別されます。以下の各リスナーには使用できる変数が記載されており、リスナー選択画面の説明にも表示されます。

<img width="800" alt="実績解除時リスナーを選択し、変数が記載された説明を表示しているリスナー選択画面" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/listeners_choose.png?raw=true">

たとえば、次のリスナーは`H`キーが押されるとヘルプ画面を開きます。

1. **キーボードキー押下時**リスナーを追加します。
2. スクリプトで[**テキスト判定**](/conditions#is-text)条件を使って**IF文を追加**します。**比較モード**を**等しい**に設定し、**テキスト**に`$$key_name`、**比較対象のテキスト**に`H`を指定します。
3. IF文の中に、ヘルプ画面を指定した[**画面またはカスタムGUIを開く**](/action-scripts#open-screen-or-custom-gui)を追加します。

リスナー変数についての補足:

- リスナー変数は常にテキストです。リスナーが値を取得できない場合、`ERROR`、`UNKNOWN`、`NONE`、`EMPTY`、`0`、`-1`などの代替値、または空欄が設定されます。
- リスナー変数は[プレースホルダー](/placeholders)より先に値が設定されるため、プレースホルダー内でも使えます。
- リスナー変数は、そのスクリプトの実行中だけ有効です。値を保持するには、[**変数の値を設定（FM変数）**](/action-scripts#set-variable-value-fm-variable)を使って、[変数](/variables)に保存してください。
- **メニューバー -> カスタマイズ -> 変数の管理**で作成した独自の変数も、リスナーのスクリプトで`$$`と変数名を使って参照できます（例: `$$coins`）。独自の変数とリスナー変数の名前が同じ場合、`$$name`はリスナー変数を意味します。`key_name_log`のように、より長い名前の独自変数は引き続き使用できます。
- チャット、サーバー、ファイル、他のプレイヤーからのテキストには、どんな内容でも含まれる可能性があります。テキストをコマンド、ファイルパス、リンクにそのまま使用しないでください。

# 知っておくと便利なこと

- 一部のリスナーは、サーバーにFancyMenuが必要です。該当するものには以下に記載があります。シングルプレイでは常に動作します。
- **画面内でマウスが動いたとき**、**要素がスクロールしたとき**、**位置が変わったとき**、**ワールド内でサウンドが再生されたとき**など、非常に頻繁に実行されるリスナーもあります。スクリプトは短くし、[**FancyMenuを再読み込み**](/action-scripts#reload-fancymenu)のような時間のかかるアクションは使わないでください。
- **画面が開いたとき**で画面を置き換える場合は、最初にIF文で`$$screen_identifier`を確認してください。確認しないと、開いた画面も含め、すべての画面が置き換えられてしまいます。

# すべてのリスナー

FancyMenuにあるすべてのリスナーを、反応する内容別に分類して紹介します。

## キーボードとマウス

どのキーが押されたか確認するには、`$$key_name`を使います。キーのコード番号はMinecraftのバージョンによって異なります。

### キーボードキー押下時

**識別子:** `keyboard_key_pressed`

メニュー内でもプレイ中でも、キーが押されると実行されます。キーを押し続けている間は、繰り返し実行されます。

- `$$key_name`: キーの名前（例: `H`、`Left Shift`）
- `$$key_keycode`: キーのコード番号
- `$$key_scancode`: キーのスキャンコード
- `$$key_modifiers`: `Shift`や`Ctrl`など、同時に押されている修飾キーを示す数値

### キーボードキー解放時

**識別子:** `keyboard_key_released`

メニュー内でもプレイ中でも、キーが離されると実行されます。

**キーボードキー押下時**と同じ変数を使用できます: `$$key_name`、`$$key_keycode`、`$$key_scancode`、`$$key_modifiers`。

### 画面内でキーボード文字が入力されたとき

**識別子:** `keyboard_char_typed`

画面が開いている間、文字が入力されるたびに実行されます。

- `$$char`: 入力された文字

### 画面内でマウスが動いたとき

**識別子:** `mouse_moved`

画面が開いている間、マウスが動くたびに実行されます。

- `$$mouse_pos_x`、`$$mouse_pos_y`: GUIピクセル単位のマウス位置
- `$$mouse_move_delta_x`、`$$mouse_move_delta_y`: 前回からの移動量

### マウスボタン押下時

**識別子:** `mouse_button_clicked`

メニュー内でもプレイ中でも、マウスボタンが押されたときに1回実行されます。

- `$$button`: `left`、`right`、`middle`のいずれか。その他のボタンは番号で示されます。
- `$$mouse_pos_x`、`$$mouse_pos_y`: GUIピクセル単位のマウス位置

### マウスボタン解放時

**識別子:** `mouse_button_released`

メニュー内でもプレイ中でも、マウスボタンが離されたときに1回実行されます。

**マウスボタン押下時**と同じ変数を使用できます: `$$button`、`$$mouse_pos_x`、`$$mouse_pos_y`。

### 画面内でマウスホイールがスクロールしたとき

**識別子:** `mouse_scrolled`

画面が開いている間、マウスホイールが回されると実行されます。

- `$$scroll_delta_y`: ホイールの回転量。上方向へのスクロールでは`0`より大きく、下方向では`0`より小さい値になります。

## 画面と要素

### 画面が開いたとき

**識別子:** `screen_open`

画面が開いた直後に実行されます。スクリプトで[**画面またはカスタムGUIを開く**](/action-scripts#open-screen-or-custom-gui)アクションを使うと、画面を別の画面に置き換えられます。

- `$$screen_identifier`: 画面の[識別子](/screen-identifiers)

### 画面が閉じたとき

**識別子:** `screen_close`

画面が閉じた直後に実行されます。

- `$$screen_identifier`: 閉じた画面の[識別子](/screen-identifiers)

### Markdownテキストがクリックされたとき

**識別子:** `text_clicked`

`[ルールを読む](click:open_rules)`のような、テキスト内の[クリックイベント](/text-formatting#click-and-hover-events)がクリックされると実行されます。

- `$$text_event_id`: イベントのID（例: `open_rules`）

### Markdownテキストにカーソルが重なったとき

**識別子:** `text_hovered`

`[これは何？](hover:show_hint)`のような、テキスト内の[ホバーイベント](/text-formatting#click-and-hover-events)にマウスカーソルが乗ると実行されます。

- `$$text_event_id`: イベントのID（例: `show_hint`）

### 要素がスクロールしたとき

**識別子:** `scroll_area_scrolled`

[スクロール可能な領域](/scrollable-areas)や[テキスト要素](/text-in-menus)のコンテンツが動くたびに実行されます。コンテンツが滑らかにスクロールしている間は、毎フレーム実行されます。レイアウトエディターでは実行されません。

- `$$element_identifier`: 要素の[識別子](/element-identifiers)
- `$$scroll_x`: コンテンツの横方向のスクロール量（ピクセル単位）
- `$$scroll_y`: コンテンツの下方向へのスクロール量（ピクセル単位）
- `$$scroll_percent`: 要素の主なスクロール方向におけるスクロール量。`0`（開始位置）から`100`（終了位置）まで

### 要素が先頭までスクロールしたとき

**識別子:** `scroll_area_reached_start`

スクロール可能な領域またはテキスト要素のコンテンツが先頭まで戻ると実行されます。

**要素がスクロールしたとき**と同じ変数を使用できます: `$$element_identifier`、`$$scroll_x`、`$$scroll_y`、`$$scroll_percent`。

### 要素が末尾までスクロールしたとき

**識別子:** `scroll_area_reached_end`

スクロール可能な領域またはテキスト要素のコンテンツが末尾までスクロールすると実行されます（ルールを最後まで読んだ場合など）。

**要素がスクロールしたとき**と同じ変数を使用できます: `$$element_identifier`、`$$scroll_x`、`$$scroll_y`、`$$scroll_percent`。

### アニメーションテクスチャの再生開始時

**識別子:** `animated_texture_started_playing`

[アニメーションテクスチャ](/animations)（GIF、APNG、FMA）の再生が始まったときと、再び最初から再生されるたびに実行されます。

- `$$texture_source`: テクスチャの取得元（ファイルパス、ウェブリンク、リソースロケーション）
- `$$texture_source_type`: `LOCAL`、`WEB`、`RESOURCE_LOCATION`のいずれか
- `$$texture_will_restart`: 次の再生で最初から再開する場合は`true`、それ以外は`false`

### アニメーションテクスチャの再生終了時

**識別子:** `animated_texture_finished_playing`

アニメーションテクスチャの1回分の再生が終わると実行されます。ループ再生の場合は、次の再生が始まる直前に実行されます。

**アニメーションテクスチャの再生開始時**と同じ変数を使用できます: `$$texture_source`、`$$texture_source_type`、`$$texture_will_restart`。

### 動画の再生状態が変わったとき

**識別子:** `video_playback_status_changed`

[動画](/video)要素またはメニュー背景の再生が始まった、一時停止した、停止した、または終了したときに実行されます。

- `$$video_source`: 動画の取得元（ファイルパス、ウェブリンク、リソースロケーション）
- `$$video_source_type`: `LOCAL`、`WEB`、`RESOURCE_LOCATION`のいずれか
- `$$is_looping`: 動画がループ再生される場合は`true`、それ以外は`false`
- `$$new_status`:
  - `PLAYING`: 動画の再生が始まった、または一時停止が解除された
  - `PAUSED`: 動画が一時停止された
  - `STOPPED`: 動画が停止された
  - `FINISHED`: 動画が最後まで再生された。ループ再生の場合も、次の再生が始まる直前に発生します。

## 変数、ファイル、データ

### FM変数が更新されたとき

**識別子:** `fm_variable_updated`

[変数](/variables)が設定されるたびに実行されます。

- `$$var_name`: 変数の名前
- `$$old_value`: 変更前の値
- `$$new_value`: 新しい値

リスト変数の場合、どちらの値も`["Diamonds","Emeralds"]`のようなJSON配列でリスト全体を表します。

### アクションによるファイルのダウンロード開始時

**識別子:** `file_download_started_via_action`

[**ゲームディレクトリにファイルをダウンロード**](/action-scripts#download-file-to-game-directory)によるダウンロードが始まり、ファイル名が判明した時点で実行されます。ダウンロードが完了するまではファイルは指定のパスに表示されません。完了を確認するには、**アクションによるファイルのダウンロード完了時**を使ってください。

- `$$download_url`: ファイルのリンク
- `$$target_file_path`: ファイルの保存先

### アクションによるファイルのダウンロード完了時

**識別子:** `file_downloaded_via_action`

[**ゲームディレクトリにファイルをダウンロード**](/action-scripts#download-file-to-game-directory)によるダウンロードが完了するか、失敗すると実行されます。

- `$$download_url`: ファイルのリンク
- `$$target_file_path`: ファイルの保存先。ダウンロードに失敗した場合は、フォルダーのみが設定されることがあります。
- `$$download_succeeded`: 成功した場合は`true`、失敗した場合は`false`

### ファイルが選択されたとき

**識別子:** `file_selected_via_action`

[**システムからファイルを選択**](/action-scripts#select-file-from-system)が完了したときに実行されます。ファイルがコピーされた、ファイル選択画面がキャンセルされた、または何らかのエラーが起きた場合に実行されます。

- `$$selected_file_path`: 選択したファイルのフルパス。選択画面をキャンセルした場合は空欄
- `$$target_file_path`: ゲームフォルダー内のコピー先
- `$$selection_succeeded`: ファイルがコピーされた場合は`true`
- `$$selection_cancelled`: ファイルを選択せずに選択画面を閉じた場合は`true`
- `$$failure_reason`: 失敗の理由。問題がなければ空欄

### アクションによるZIPの展開完了時

**識別子:** `zip_extracted_via_action`

[**ゲームディレクトリ内でZIPファイルを展開**](/action-scripts#extract-zip-file-in-game-directory)が完了すると実行されます。

- `$$source_zip_path`: ZIPファイル
- `$$target_folder_path`: 展開先のフォルダー
- `$$extract_succeeded`: 成功した場合は`true`、失敗した場合は`false`
- `$$failure_reason`: 失敗の理由。問題がなければ空欄

ゲームフォルダー内のパスは`/config/fancymenu/assets/pack.zip`のように`/`で始まります。`.minecraft`フォルダー内のパスは`.minecraft/`で始まります。

### FMデータ受信時

**識別子:** `fm_data_received`

サーバーが`/fmdata send`を使ってプレイヤーにデータを送信すると実行されます。[FMデータ](/fm-data)を参照してください。

- `$$data_identifier`: データの送信に使われた識別子
- `$$data`: データ
- `$$sent_by`: サーバーのIPアドレス。シングルプレイでは`integrated_server`

### リモートサーバーへの接続時

**識別子:** `remote_server_connected`

[リモートサーバー接続](/remote-server-communication)が開始されると実行されます。

- `$$request_id`: 接続のリクエストID
- `$$remote_server_url`: リモートサーバーのリンク

### リモートサーバーからデータを受信したとき

**識別子:** `remote_server_data_received`

接続中のリモートサーバーからテキストが送信されるたびに実行されます。

- `$$request_id`: 接続のリクエストID
- `$$remote_server_url`: リモートサーバーのリンク
- `$$data`: 送信されたテキスト

### リモートサーバー接続の終了時

**識別子:** `remote_server_connection_closed`

リモートサーバーとの接続が終了すると実行されます。

- `$$request_id`: 接続のリクエストID
- `$$remote_server_url`: リモートサーバーのリンク
- `$$intentionally_closed`: [**リモートサーバー接続を閉じる**](/action-scripts#close-remote-server-connection)によって接続が閉じられた場合は`true`
- `$$crashed`: 接続がクラッシュした場合は`true`
- `$$unknown_close_reason`: 不明な理由で接続が終了した場合は`true`

## ゲーム、ワールド、サーバー

### Minecraft終了時

**識別子:** `quit_minecraft`

ゲームの終了処理が始まると1回実行されます。

- `$$timestamp_millis`: 1970年からの経過時間（ミリ秒）
- `$$timestamp_iso`: `2026-11-24T18:30:00.123Z`のようなISO-8601形式の時刻

### スクリーンショット撮影時

**識別子:** `screenshot_taken`

スクリーンショットキーを押すなどして、スクリーンショットが撮影・保存されると実行されます。

- `$$screenshot_path`: ゲームフォルダー内のスクリーンショットのパス（例: `/screenshots/2026-10-29_14.30.00.png`）

### シングルプレイワールドに入ったとき

**識別子:** `world_entered`

シングルプレイワールドの読み込みが終わり、移動できるようになると実行されます。

- `$$world_name`: ワールド名
- `$$world_save_path`: ワールドのセーブフォルダーのフルパス
- `$$world_difficulty`: ワールドの難易度
- `$$world_cheats_allowed`: チートが有効な場合は`true`
- `$$world_icon_path`: ワールドアイコンのフルパス
- `$$world_is_first_join`: ワールド作成後、初めて訪れたときは`true`

### シングルプレイワールドを退出したとき

**識別子:** `world_left`

シングルプレイワールドが閉じられ、保存されると実行されます。

`$$world_is_first_join`を除き、**シングルプレイワールドに入ったとき**と同じ変数を使用できます: `$$world_name`、`$$world_save_path`、`$$world_difficulty`、`$$world_cheats_allowed`、`$$world_icon_path`。

### サーバーへの接続開始時

**識別子:** `start_joining_server`

サーバーまたはRealmsへの接続が始まったとき、接続が完了する前に実行されます。接続に失敗した場合やキャンセルした場合も実行されるため、切断画面の再接続ボタンなどで使うサーバー情報を記録できます。

- `$$server_ip`: サーバーのIPアドレス

### サーバーに参加したとき

**識別子:** `server_joined`

マルチプレイヤーサーバーに参加した後に実行されます。

- `$$server_ip`: サーバーのIPアドレス

### サーバーを退出したとき

**識別子:** `server_left`

マルチプレイヤーサーバーを退出した後に実行されます。

- `$$server_ip`: サーバーのIPアドレス

### 他のプレイヤーがワールド／サーバーに参加したとき

**識別子:** `other_player_joined_world`

他のプレイヤーが自分のワールドまたはサーバーに参加すると実行されます。

- `$$player_name`: プレイヤー名
- `$$player_uuid`: プレイヤーのUUID

### 他のプレイヤーがワールド／サーバーを退出したとき

**識別子:** `other_player_left_world`

他のプレイヤーが自分のワールドまたはサーバーを退出すると実行されます。

- `$$player_name`: プレイヤー名
- `$$player_uuid`: プレイヤーのUUID

### 他のプレイヤーが死亡したとき

**識別子:** `other_player_died`

自分のワールド内で他のプレイヤーが死亡すると実行されます。

- `$$player_name`: プレイヤー名
- `$$player_uuid`: プレイヤーのUUID
- `$$death_pos_x`、`$$death_pos_y`、`$$death_pos_z`: プレイヤーが死亡した位置

## チャット

### チャットメッセージを受信したとき

**識別子:** `chat_message_received`

プレイヤーのチャットメッセージが自分のチャットに表示されると実行されます。

- `$$chat_message_string`: プレーンテキスト形式のメッセージ
- `$$chat_message_component`: JSONテキストコンポーネント形式のメッセージ
- `$$sender_uuid`: 送信者のUUID。不明な場合は`ERROR`
- `$$sender_name`: 送信者の名前。不明な場合は`ERROR`

### チャットメッセージを送信したとき

**識別子:** `chat_message_sent`

チャットメッセージを送信すると実行されます。コマンドは対象外です。

- `$$chat_message_string`: プレーンテキスト形式のメッセージ
- `$$chat_message_component`: JSONテキストコンポーネント形式のメッセージ

### システムメッセージをチャットで受信したとき

**識別子:** `system_message_received_in_chat`

コマンドの実行結果など、プレイヤー以外からのメッセージがチャットに表示されると実行されます。

- `$$system_message_string`: プレーンテキスト形式のメッセージ
- `$$system_message_component`: JSONテキストコンポーネント形式のメッセージ

## プレイヤー

### 死亡時

**識別子:** `player_death`

死亡画面が開いた直後に実行されます。

- `$$days_survived`: 前回の死亡から経過したゲーム内の日数（小数点以下切り捨て）
- `$$death_reason_string`: プレーンテキスト形式の死亡メッセージ
- `$$death_reason_component`: JSONテキストコンポーネント形式の死亡メッセージ
- `$$death_pos_x`、`$$death_pos_y`、`$$death_pos_z`: 死亡した位置

### ダメージを受けたとき

**識別子:** `damage_taken`

ダメージを受けるたびに1回実行されます。

- `$$damage_amount`: 受けたダメージ量
- `$$damage_type`: ダメージの種類（例: `minecraft:fall`）
- `$$is_fatal_damage`: ダメージで死亡した場合は`true`
- `$$damage_source`: ダメージを与えたエンティティの種類（例: `minecraft:zombie`）。該当しない場合は`NONE`

### ステータス効果を得たとき

**識別子:** `effect_gained`

ステータス効果を得ると1回実行されます。

- `$$effect_key`: 効果（例: `minecraft:speed`）
- `$$effect_type`: `positive`、`negative`、`neutral`のいずれか
- `$$effect_duration`: 効果の持続時間（ティック単位。20ティックで1秒）

### ステータス効果が切れたとき

**識別子:** `effect_lost`

ステータス効果が終了すると1回実行されます。

- `$$effect_key`: 効果（例: `minecraft:speed`）
- `$$effect_type`: `positive`、`negative`、`neutral`のいずれか

### 経験値が変化したとき

**識別子:** `experience_changed`

経験値が増減するたびに実行されます。

- `$$new_experience_amount`: 現在の累計経験値
- `$$old_experience_amount`: 変更前の累計経験値
- `$$is_level_up`: レベルが上がった場合は`true`

### 実績を解除したとき

**識別子:** `achievement_unlocked`

実績（進捗）を解除すると1回実行されます。ワールドへの参加時点ですでに達成済みの実績は対象外です。

- `$$achievement_key`: 実績（例: `minecraft:story/mine_diamond`）
- `$$achievement_label`: ゲーム内の言語で表示されるタイトル
- `$$achievement_description`: ゲーム内の言語で表示される説明
- `$$achievement_icon_item_key`: アイコンのアイテム（例: `minecraft:diamond`）
- `$$achievement_type`: `advancement`、`goal`、`challenge`のいずれか

### ジャンプしたとき

**識別子:** `jump`

ジャンプするたびに実行されます。変数はありません。

### ダッシュを始めたとき

**識別子:** `started_running`

ダッシュを始めると1回実行されます。変数はありません。

### ダッシュをやめたとき

**識別子:** `stopped_running`

ダッシュをやめると1回実行されます。変数はありません。

### 位置が変わったとき

**識別子:** `position_changed`

別のブロックへ移動するたびに実行されます。

- `$$old_pos_x`、`$$old_pos_y`、`$$old_pos_z`: 移動前のブロック位置
- `$$new_pos_x`、`$$new_pos_y`、`$$new_pos_z`: 移動後のブロック位置

### 燃え始めたとき

**識別子:** `started_burning`

燃え始めると1回実行されます。変数はありません。

### 燃焼が終わったとき

**識別子:** `stopped_burning`

燃焼が終わると1回実行されます。変数はありません。

### 溺れ始めたとき

**識別子:** `started_drowning`

溺れによるダメージを受け始めると1回実行されます。変数はありません。

### 凍り始めたとき

**識別子:** `started_freezing`

粉雪の中にいるときなど、凍り始めると1回実行されます。

- `$$freezing_intensity`: 凍結の強さ。`0.0`（まったく凍っていない）から`1.0`（完全に凍っている）まで

### 凍結が止まったとき

**識別子:** `stopped_freezing`

凍結が止まると1回実行されます。変数はありません。

### 完全に凍ったとき

**識別子:** `fully_frozen`

完全に凍ると1回実行されます。変数はありません。

### 泳ぎ始めたとき

**識別子:** `start_swimming`

泳ぎ始めると1回実行されます。

- `$$fluid_type`: 液体の種類（例: `minecraft:water`）

### 泳ぐのをやめたとき

**識別子:** `stop_swimming`

泳ぐのをやめると1回実行されます。

- `$$fluid_type`: 液体の種類（例: `minecraft:water`）

### 液体に触れ始めたとき

**識別子:** `start_touching_fluid`

水や溶岩などの液体に触れ始めると1回実行されます。

- `$$fluid_type`: 液体の種類（例: `minecraft:lava`）

### 液体に触れなくなったとき

**識別子:** `stop_touching_fluid`

液体に触れなくなると1回実行されます。

- `$$fluid_type`: 液体の種類（例: `minecraft:lava`）

## アイテム

### アイテムを拾ったとき

**識別子:** `item_picked_up`

アイテムを拾うと1回実行されます。

- `$$item_key`: アイテム（例: `minecraft:diamond`）

### アイテムを捨てたとき

**識別子:** `item_dropped`

インベントリからアイテムを捨てると1回実行されます。

- `$$item_key`: アイテム（例: `minecraft:diamond`）

### アイテムを消費したとき

**識別子:** `item_consumed`

アイテムを食べ終えるか飲み終えると1回実行されます。

- `$$item_key`: アイテム（例: `minecraft:golden_apple`）

### アイテムを使用したとき

**識別子:** `item_used`

アイテムを使用すると1回実行されます。

- `$$item_key`: アイテム（例: `minecraft:flint_and_steel`）
- `$$used_on_type`: 使用対象の種類。`block`、`entity`、`self`、`none`のいずれか
- `$$used_on_entity_key`: 使用対象エンティティの種類。対象がない場合は空欄
- `$$used_on_block_key`: 使用対象ブロック。対象がない場合は空欄
- `$$target_pos_x`、`$$target_pos_y`、`$$target_pos_z`: 使用対象の位置。対象がない場合は`-1`

### アイテムが壊れたとき

**識別子:** `item_broke`

インベントリ内のアイテムが壊れると1回実行されます。

- `$$item_key`: アイテム（例: `minecraft:iron_pickaxe`）
- `$$item_type`: `tool`、`armor`、`other`のいずれか

### インベントリ内のアイテムにカーソルを合わせたとき

**識別子:** `item_hovered_in_inventory`

自分のインベントリやチェストなど、どのインベントリでも、アイテムにマウスカーソルを合わせると1回実行されます。

- `$$item_key`: アイテム（例: `minecraft:diamond_sword`）
- `$$item_display_name_string`: プレーンテキスト形式のアイテム名
- `$$item_display_name_json`: JSONテキストコンポーネント形式のアイテム名

## ブロック

### ブロックを見始めたとき

**識別子:** `start_looking_at_block`

クロスヘアが20ブロック以内のブロックを指し始めると1回実行されます。

- `$$block_key`: ブロック（例: `minecraft:oak_log`）
- `$$block_pos_x`、`$$block_pos_y`、`$$block_pos_z`: ブロックの位置
- `$$distance_to_player`: 目からクロスヘアが指す地点までの距離

### ブロックを見るのをやめたとき

**識別子:** `stop_looking_at_block`

クロスヘアがブロックを指さなくなると1回実行されます。

直前まで見ていたブロックについて、**ブロックを見始めたとき**と同じ変数を使用できます: `$$block_key`、`$$block_pos_x`、`$$block_pos_y`、`$$block_pos_z`、`$$distance_to_player`。

### ブロックを壊したとき

**識別子:** `block_broke`

ブロックを壊すと1回実行されます。

- `$$block_key`: ブロック（例: `minecraft:stone`）
- `$$broke_with_item_key`: 手に持っていたアイテム（例: `minecraft:iron_pickaxe`）。何も持っていない場合は`EMPTY`
- `$$block_pos_x`、`$$block_pos_y`、`$$block_pos_z`: ブロックの位置

### ブロックを設置したとき

**識別子:** `block_placed`

ブロックを設置すると1回実行されます。

- `$$block_key`: ブロック（例: `minecraft:torch`）
- `$$block_pos_x`、`$$block_pos_y`、`$$block_pos_z`: ブロックの位置

### ブロックを操作したとき

**識別子:** `interacted_with_block`

チェストを開いたりボタンを押したりするなど、ブロックを操作すると1回実行されます。

- `$$block_key`: ブロック（例: `minecraft:chest`）
- `$$block_pos_x`、`$$block_pos_y`、`$$block_pos_z`: ブロックの位置

### ブロックの上に乗ったとき

**識別子:** `stepping_on_block`

ブロックの上に乗ると1回実行されます。

- `$$block_key`: ブロック（例: `minecraft:grass_block`）
- `$$block_pos_x`、`$$block_pos_y`、`$$block_pos_z`: ブロックの位置

## エンティティ

### エンティティを見始めたとき

**識別子:** `start_looking_at_entity`

クロスヘアが20ブロック以内のエンティティを指し始めると1回実行されます。

- `$$entity_key`: エンティティの種類（例: `minecraft:villager`）
- `$$distance_to_player`: 目からクロスヘアが指す地点までの距離
- `$$entity_pos_x`、`$$entity_pos_y`、`$$entity_pos_z`: エンティティの位置
- `$$entity_uuid`: エンティティのUUID

### エンティティを見るのをやめたとき

**識別子:** `stop_looking_at_entity`

クロスヘアがエンティティを指さなくなると1回実行されます。

直前まで見ていたエンティティについて、**エンティティを見始めたとき**と同じ変数を使用できます: `$$entity_key`、`$$distance_to_player`、`$$entity_pos_x`、`$$entity_pos_y`、`$$entity_pos_z`、`$$entity_uuid`。

### エンティティが視界に入ったとき

**識別子:** `entity_starts_being_in_sight`

エンティティが画面内に見えるようになると1回実行されます。距離は最大200ブロックです。

- `$$entity_key`: エンティティの種類（例: `minecraft:creeper`）
- `$$distance_to_player`: 目からエンティティまでの距離
- `$$entity_pos_x`、`$$entity_pos_y`、`$$entity_pos_z`: エンティティの位置
- `$$entity_uuid`: エンティティのUUID

### エンティティが視界から外れたとき

**識別子:** `entity_stops_being_in_sight`

視界にいるエンティティが画面外に出るか、200ブロックより遠くなると1回実行されます。

**エンティティが視界に入ったとき**と同じ変数を使用できます: `$$entity_key`、`$$distance_to_player`、`$$entity_pos_x`、`$$entity_pos_y`、`$$entity_pos_z`、`$$entity_uuid`。

### エンティティを操作したとき

**識別子:** `entity_interacted`

村人と取引するなど、エンティティを操作すると1回実行されます。

- `$$entity_key`: エンティティの種類（例: `minecraft:villager`）
- `$$entity_pos_x`、`$$entity_pos_y`、`$$entity_pos_z`: エンティティの位置
- `$$entity_uuid`: エンティティのUUID

### エンティティに騎乗したとき

**識別子:** `entity_mounted`

馬やボートなどのエンティティに乗ると1回実行されます。

- `$$entity_key`: エンティティの種類（例: `minecraft:horse`）
- `$$entity_pos_x`、`$$entity_pos_y`、`$$entity_pos_z`: エンティティの位置
- `$$entity_uuid`: エンティティのUUID

### エンティティから降りたとき

**識別子:** `entity_unmounted`

エンティティから降りると1回実行されます。

- `$$entity_key`: エンティティの種類（例: `minecraft:horse`）
- `$$entity_pos_x`、`$$entity_pos_y`、`$$entity_pos_z`: エンティティの位置
- `$$entity_uuid`: エンティティのUUID

### エンティティがスポーンしたとき

**識別子:** `entity_spawned`

サーバーにFancyMenuが必要です。エンティティがワールド内のどこかにスポーンすると実行されます。遠く離れた場所や別ディメンションでのスポーンも対象です。

- `$$entity_key`: エンティティの種類（例: `minecraft:zombie`）
- `$$distance_to_player`: プレイヤーまでの距離。別ディメンションの場合は`-1`
- `$$entity_pos_x`、`$$entity_pos_y`、`$$entity_pos_z`: スポーンした位置
- `$$entity_uuid`: エンティティのUUID
- `$$dimension_key`: ディメンション（例: `minecraft:overworld`）
- `$$is_same_dimension_as_player`: プレイヤーと同じディメンションにスポーンした場合は`true`

### エンティティが死亡したとき

**識別子:** `entity_died`

サーバーにFancyMenuが必要です。エンティティがワールド内のどこかで死亡すると実行されます。遠く離れた場所や別ディメンションでの死亡も対象です。

- `$$entity_key`: エンティティの種類（例: `minecraft:ender_dragon`）
- `$$distance_to_player`: プレイヤーまでの距離。別ディメンションの場合は`-1`
- `$$death_pos_x`、`$$death_pos_y`、`$$death_pos_z`: 死亡した位置
- `$$entity_uuid`: エンティティのUUID
- `$$dimension_key`: ディメンション（例: `minecraft:the_end`）
- `$$damage_type`: 死亡原因となったダメージの種類（例: `minecraft:player_attack`）
- `$$is_same_dimension_as_player`: プレイヤーと同じディメンションで死亡した場合は`true`
- `$$entity_killed_by_name`: 倒した相手の名前。該当しない場合は`NONE`
- `$$entity_killed_by_key`: 倒した相手の種類（例: `minecraft:player`）。該当しない場合は`NONE`
- `$$entity_killed_by_uuid`: 倒した相手のUUID。該当しない場合は`NONE`

## ワールドと場所

### バイオームに入ったとき

**識別子:** `enter_biome`

別のバイオームに入ると1回実行されます。

- `$$biome_key`: バイオーム（例: `minecraft:cherry_grove`）

### バイオームから出たとき

**識別子:** `leave_biome`

バイオームから出ると1回実行されます。

- `$$biome_key`: 出たバイオーム（例: `minecraft:cherry_grove`）

### 構造物の範囲に入ったとき

**識別子:** `enter_structure`

サーバーにFancyMenuが必要です。構造物の範囲に入ると1回実行されます。範囲の判定はおおまかなため、構造物の近くや上空でも実行されることがあります（地下にある廃坑の上など）。内部に入ったときだけ実行するには、**構造物の内部に入ったとき（高精度）**を使ってください。

- `$$structure_key`: 構造物（例: `minecraft:village_plains`）

### 構造物の範囲から出たとき

**識別子:** `leave_structure`

サーバーにFancyMenuが必要です。**構造物の範囲に入ったとき**と同じく、おおまかな範囲判定で、構造物の範囲から出ると1回実行されます。

- `$$structure_key`: 出た構造物

### 構造物の内部に入ったとき（高精度）

**識別子:** `enter_structure_high_precision`

サーバーにFancyMenuが必要です。構造物の内部に入ると1回実行されます。

- `$$structure_key`: 構造物（例: `minecraft:stronghold`）

### 構造物の外に出たとき（高精度）

**識別子:** `leave_structure_high_precision`

サーバーにFancyMenuが必要です。構造物の外に完全に出ると1回実行されます。

- `$$structure_key`: 出た構造物

### ディメンションに入ったとき

**識別子:** `enter_dimension`

別のディメンションに入ると1回実行されます。

- `$$dimension_key`: ディメンション（例: `minecraft:the_nether`）

### 天候が変わったとき

**識別子:** `weather_changed`

天候が変わると1回実行されます。また、現在地の天候が変化した場合も実行されます。雨が降っているときに砂漠、雪の降るバイオーム、建物の中へ移動した場合も該当します。

- `$$weather_type`: `clear`、`rain`、`thunder`のいずれか
- `$$weather_can_snow`: 現在地で雪が降る場合は`true`
- `$$weather_can_rain`: 現在地で雨が降る場合は`true`

### 襲撃が始まったとき

**識別子:** `raid_started`

サーバーにFancyMenuが必要です。襲撃範囲内にいるときに襲撃が始まり、襲撃バーが表示されると実行されます。変数はありません。

すでに進行中の襲撃範囲に入った場合は対象外です。その場合は**進行中の襲撃範囲に入ったとき**を使ってください。

### 進行中の襲撃範囲に入ったとき

**識別子:** `enter_active_raid_area`

サーバーにFancyMenuが必要です。すでに進行中の襲撃の範囲に入り、襲撃バーが表示されると実行されます。変数はありません。

### 進行中の襲撃範囲から出たとき

**識別子:** `leave_active_raid_area`

サーバーにFancyMenuが必要です。襲撃範囲から出て襲撃バーが消えると実行されます。その場で死亡した場合や、ディメンションを変更した場合も対象ですが、襲撃が終了した場合は対象外です。変数はありません。

### 襲撃が終了したとき

**識別子:** `raid_finished`

サーバーにFancyMenuが必要です。襲撃範囲内にいるときに襲撃が終了すると実行されます。

- `$$raid_result`: `victory`または`defeat`

## サウンドと音楽

### 音楽トラックの再生開始時

**識別子:** `music_track_started`

音楽トラックの再生が始まると1回実行されます。

- `$$track_resource_location`: トラックのサウンドファイル
- `$$track_display_name`: トラック名。不明な場合は`UNKNOWN`
- `$$track_artist`: アーティスト名。不明な場合は`UNKNOWN`
- `$$track_duration_ms`: 再生時間（ミリ秒）。不明な場合は`0`

### 音楽トラックの再生終了時

**識別子:** `music_track_stopped`

トラックの再生が終わるか、別のトラックに置き換わると1回実行されます。

**音楽トラックの再生開始時**と同じ変数を使用できます: `$$track_resource_location`、`$$track_display_name`、`$$track_artist`、`$$track_duration_ms`。

### ワールド内でサウンドが再生されたとき

**識別子:** `world_sound_triggered`

ドアやクリーパーなど、プレイヤーの近くのワールド内でサウンドの再生が始まるたびに実行されます。

- `$$sound_resource_location`: サウンドファイル
- `$$sound_display_name`: サウンドの字幕。不明な場合は`UNKNOWN`
- `$$sound_origin_pos_x`、`$$sound_origin_pos_y`、`$$sound_origin_pos_z`: サウンドの発生位置
- `$$sound_origin_distance_to_player`: プレイヤーからの距離
- `$$sound_origin_direction_from_player`: 見ている方向を基準としたサウンドの方向（0～360度）
