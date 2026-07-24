---
title: 条件（要件）
description: 読み込み要件の使い方。
---
# 要件

要件（いくつかのメニューでは **読み込み要件** と呼ばれます）は、ホバー状態、ウィンドウサイズ、ワールドの読み込み有無などの条件に応じてコンテンツを表示または非表示にします。

[要素](./elements)、レイアウト全体、[アクションスクリプト](./action-scripts) で使用できます。

# 要素に要件を追加する

要素に要件を追加するには、その要素を右クリックして **読み込み要件** を選択します。

要件はメニューが開いている間チェックされるため、条件が変わると要素も更新されます。

# レイアウト全体の要件

**エディタ背景** を右クリックしてから **読み込み要件 [レイアウト全体]** をクリックすると、レイアウト全体の表示/非表示も変更できます。

レイアウト全体の結果が変わると、FancyMenu は現在の画面を再構築し、要件を満たすレイアウトを適用します。

# アクションスクリプト

要件はアクションスクリプトでも使用できます。
アクションスクリプトエディタ画面で追加し、要件の条件が満たされた場合のみ特定のアクションを実行するようにできます。

# 要件の組み合わせ

- グループ外の要件は **AND** で判定されるため、すべてを満たす必要があります。
- グループ内では **AND** または **OR** を選べます。
- **IF NOT** を使うと、1つの要件を反転できます。

これらのルールは、要素、レイアウト、アクションスクリプトで共通です。

# 要件の値

値が必要な要件では、**要件の値を編集** を使用し、エディタに表示される説明に従ってください。一部のフィールドは **TAB** 補完に対応しています。

FancyMenu やアドオンを変更したあとに、インポートした要件が動作しなくなった場合は、要件画面で編集し、エラーについて `logs/latest.log` を確認してください。

要件エディタは、右クリックのコンテキストメニュー、キーボード操作、検索、元に戻す/やり直し（`Ctrl/Command + Z` / `Ctrl/Command + Y`）、`Ctrl/Command + S` による保存に対応しています。

# 要件の詳細

このセクションでは、FancyMenu に組み込まれている要件を一覧します。

## 要素がホバーされているか (`fancymenu_visibility_requirement_is_element_hovered`)

**目的:** 特定の要素がマウスカーソルでホバーされているかを確認します。

**値:** 必須 — 対象要素の [要素識別子](./element-identifiers)（例: `some_element_ID`）

## 要素がフォーカスされているか (`is_element_focused`)

**目的:** 特定の要素が現在キーボードフォーカスを持っているかを確認します（たとえばテキスト欄やフォーカスされたボタン）。

**値:** 必須 — 対象要素の要素 ID（エディタに表示されるものと同じ ID）

> [!NOTE]
> フォーカスとホバーは別の状態です。ポインタが離れたあとでも、要素はフォーカス時の見た目を維持できます。クリックやキーボード操作でフォーカスを与えることができます。

## いずれかの要素がホバーされているか (`fancymenu_visibility_requirement_is_any_element_hovered`)

**目的:** 現在のアクティブなカスタマイズレイヤー内の表示可能/描画可能な要素を確認します。スタックされたレイアウトから提供される要素も含まれます。

**値:** 不要

## いずれかのボタンがホバーされているか (`fancymenu_visibility_requirement_is_any_button_hovered`)

**目的:** 現在のアクティブなカスタマイズレイヤー内の表示可能/描画可能なバニラまたはカスタムボタンがホバーされているかを確認します。スタックされたレイアウトから提供されるボタンも含まれます。

**値:** 不要

## レイアウトが有効か (`fancymenu_visibility_requirement_is_layout_enabled`)

**目的:** 特定のレイアウトが現在有効かを確認します。

**値:** 必須 — レイアウト名（例: `my_cool_main_menu_layout`）

## スケジューラが実行中か (`fancymenu_visibility_requirement_is_scheduler_running`)

**目的:** [スケジューラ](./schedulers) が現在実行中かを確認します。

**値:** 必須 — スケジューラ ID（例: `my_scheduler`）

## GUI スケールか (`fancymenu_loading_requirement_is_gui_scale`)

**目的:** 現在の GUI スケールが特定の条件に一致するかを確認します。

**値:** 必須 — 等しい場合は数値、より大きい場合は `>`、より小さい場合は `<` を使用します。

カンマ区切りで複数の条件を指定すると AND で組み合わされます。たとえば `>1,<4` は、GUI スケールが `1` より大きく、かつ `4` より小さい場合のみ通過します。

## ボタンがアクティブか (`fancymenu_visibility_requirement_is_button_active`)

**目的:** 特定のボタンがアクティブ（クリック可能）かを確認します。

**値:** 必須 — 対象ボタンの要素 ID（例: "some_element_ID"）

## 画面タイトルか (`is_menu_title`)

**目的:** 画面の表示タイトルが、特定のテキストまたはローカライズキーと一致するかを確認します。これは "Options" や "Pause" のような画面の表示名/タイトルのみを確認します。メニュー/画面の識別子（`title_screen` など）は確認しません！

**値:** 必須 — 画面の正確なタイトル文字列、またはローカライズキー

## キーが押されているか (`is_key_pressed`)

**目的:** 特定のキーボードキーが現在押されているかを確認します。

**値:** 必須 — 対象キーのキーコード。要件値の編集時に UI で選択します。

## いずれかの画面が開いているか (`is_any_screen_open`)

**目的:** いずれかの画面/メニューが現在開いているかを確認します（画面が表示されていない場合は false を返します）。

**値:** 不要

## MC デバッグオーバーレイが有効か (`is_debug_overlay_enabled`)

**目的:** F3 デバッグオーバーレイが現在表示されているかを確認します。

**値:** 不要

## アクティブなカーソルタイプか (`is_active_cursor_type`)

**目的:** FancyMenu の現在アクティブなカーソルタイプが、特定の標準カーソルタイプと一致するかを確認します。

**値:** 必須 — カーソルタイプ: `normal`, `writing`, `crosshair`, `pointing_hand`, `resize_horizontal`, `resize_vertical`, `resize_nwse`, `resize_nesw`, `resize_all`, `not_allowed`

## カスタマイズメニューバーが表示されているか (`is_customization_menu_bar_visible`)

**目的:** FancyMenu のカスタマイズメニューバーが現在表示されているかを確認します。

**値:** 不要

## Modpack モードが有効か (`is_modpack_mode_enabled`)

**目的:** FancyMenu の Modpack モードが有効かを確認します。

**値:** 不要

## マウスボタンが押されているか (`mouse_click`)

**目的:** 特定のマウスボタンが押されている間 true を返します。これはワンショットのクリックイベントではありません。1回のクリックごとにアクションを実行したい場合は、[**マウスボタンがクリックされたとき** リスナー](./listeners#on-mouse-button-clicked-mouse_button_clicked) を使用してください。

**値:** 必須 — どのマウスボタンを確認するかを示す `left` または `right`

## フルスクリーンか (`fancymenu_loading_requirement_is_fullscreen`)

**目的:** ゲームが現在フルスクリーンモードかを確認します。

**値:** 不要

## ウィンドウ幅が一致するか (`fancymenu_loading_requirement_is_window_width`)

**目的:** ゲームウィンドウの幅が特定の値と一致するかを確認します。

**値:** 必須 — ウィンドウ幅（ピクセル単位。例: "1920"）。複数の値はカンマ区切りで指定できます。

## ウィンドウ高さが一致するか (`fancymenu_loading_requirement_is_window_height`)

**目的:** ゲームウィンドウの高さが特定の値と一致するかを確認します。

**値:** 必須 — ウィンドウ高さ（ピクセル単位。例: "1080"）。複数の値はカンマ区切りで指定できます。

## ウィンドウ幅がより大きいか (`fancymenu_loading_requirement_is_window_width_bigger_than`)

**目的:** ゲームウィンドウの幅が特定の値より大きいかを確認します。

**値:** 必須 — ウィンドウ幅（ピクセル単位。例: "1920"）

## ウィンドウ高さがより大きいか (`fancymenu_loading_requirement_is_window_height_bigger_than`)

**目的:** ゲームウィンドウの高さが特定の値より大きいかを確認します。

**値:** 必須 — ウィンドウ高さ（ピクセル単位。例: "1080"）

## マルチプレイか (`fancymenu_loading_requirement_is_multiplayer`)

**目的:** プレイヤーが現在マルチプレイワールドにいるかを確認します。

**値:** 不要

## シングルプレイか (`fancymenu_loading_requirement_is_singpleplayer`)

**目的:** プレイヤーが現在シングルプレイワールドにいるかを確認します。

**値:** 不要

## ワールドが読み込まれているか (`fancymenu_loading_requirement_is_world_loaded`)

**目的:** いずれかのワールドが現在読み込まれているかを確認します。

**値:** 不要

## アドベンチャーか (`fancymenu_visibility_requirement_is_adventure`)

**目的:** プレイヤーが現在アドベンチャーゲームモードかを確認します。

**値:** 不要

## クリエイティブか (`fancymenu_visibility_requirement_is_creative`)

**目的:** プレイヤーが現在クリエイティブゲームモードかを確認します。

**値:** 不要

## スペクテイターか (`fancymenu_visibility_requirement_is_spectator`)

**目的:** プレイヤーが現在スペクテイターゲームモードかを確認します。

**値:** 不要

## サバイバルか (`fancymenu_visibility_requirement_is_survival`)

**目的:** プレイヤーが現在サバイバルゲームモードかを確認します。

**値:** 不要

## ゲームモードか (`is_gamemode`)

**目的:** プレイヤーが特定のゲームモードにいるかを確認します。

**値:** 必須 — ゲームモード名（例: "creative", "survival", "adventure", "spectator"）

## 難易度か (`is_difficulty`)

**目的:** 現在のゲーム難易度が特定の値と一致するかを確認します。

**値:** 必須 — 難易度名（例: "peaceful", "easy", "normal", "hard"）

## ハードコアか (`is_hardcore`)

**目的:** 現在読み込まれているワールドがハードコアモードかを確認します。

**値:** 不要

## カメラ視点か (`is_camera_perspective`)

**目的:** 現在のカメラ視点が特定の視点と一致するかを確認します。

**値:** 必須 — `first_person`, `third_person_back`, `third_person_front`

## 雨が降っているか (`is_raining`)

**目的:** プレイヤーの位置で現在雨が降っているかを確認します。

**値:** 不要

## 雷雨か (`is_thundering`)

**目的:** プレイヤーのワールドで現在雷雨が発生しているかを確認します。

**値:** 不要

## 晴天か (`is_clear_weather`)

**目的:** 現在天候が晴れであるか（雨も雷もない）を確認します。

**値:** 不要

## 雪が降っているか (`is_snowing`)

**目的:** プレイヤーの位置で現在雪が降っているかを確認します。

**値:** 不要

## プレイヤーが走っているか (`is_player_running`)

**目的:** プレイヤーが現在スプリントしているかを確認します。

**値:** 不要

## プレイヤーがスニークしているか (`is_player_sneaking`)

**目的:** プレイヤーが現在スニーク/しゃがみ状態かを確認します。

**値:** 不要

## プレイヤーがアイテムを使用中か (`is_player_using_item`)

**目的:** プレイヤーが現在アイテムを使用しているかを確認します。

**値:** 不要

## プレイヤーが泳いでいるか (`is_player_swimming`)

**目的:** プレイヤーが現在泳いでいるかを確認します。

**値:** 不要

## プレイヤーがジャンプ中または落下中か (`is_player_jumping`)

**目的:** プレイヤーが通常のジャンプ中または落下中の空中状態である間 true を返します。水泳、液体、エリトラ飛行、睡眠、見た目上の水泳、這い状態は除外されます。

**値:** 不要

## プレイヤーが水中にいるか (`is_player_under_water`)

**目的:** プレイヤーが完全に水中にいるかを確認します。

**値:** 不要

## プレイヤーが水にいるか (`is_player_in_water`)

**目的:** プレイヤーが水中にいるかを確認します（部分的に浸かっていても可）。

**値:** 不要

## プレイヤーが溶岩にいるか (`is_player_in_lava`)

**目的:** プレイヤーが溶岩にいるかを確認します。

**値:** 不要

## プレイヤーが液体内にいるか (`is_player_in_fluid`)

**目的:** プレイヤーが任意の液体（水、溶岩など）の中にいるかを確認します。

**値:** 不要

## プレイヤーがエンティティ/乗り物に乗っているか (`is_player_riding_entity`)

**目的:** プレイヤーが何らかのエンティティに乗っているかを確認します。

**値:** 不要

## プレイヤーがジャンプ可能なエンティティに乗っているか (`is_player_riding_jumpable_entity`)

**目的:** プレイヤーがジャンプできるエンティティ（馬など）に乗っているかを確認します。

**値:** 不要

## プレイヤーが体力のあるエンティティに乗っているか (`is_player_riding_entity_with_health`)

**目的:** プレイヤーが体力のある生きたエンティティ（ボートではなく動物など）に乗っているかを確認します。

**値:** 不要

## プレイヤーが粉雪の中にいるか (`is_player_in_powder_snow`)

**目的:** プレイヤーが現在粉雪の中にいるかを確認します。

**値:** 不要

## プレイヤーが粉雪の中にいたか (`was_player_in_powder_snow`)

**目的:** プレイヤーが粉雪の中にいたかを確認します（離れた後も持続する効果に使用）。

**値:** 不要

## プレイヤーがかぼちゃをかぶっているか (`is_player_wearing_pumpkin`)

**目的:** プレイヤーが頭にくり抜かれたかぼちゃを装備しているかを確認します。

**値:** 不要

## プレイヤーがエリトラで飛行しているか (`is_player_flying_with_elytra`)

**目的:** プレイヤーが現在エリトラで飛行しているかを確認します。

**値:** 不要

## プレイヤーがクリエイティブ飛行中か (`is_player_creative_flying`)

**目的:** プレイヤーがクリエイティブモードで飛行しているかを確認します。

**値:** 不要

## プレイヤーが吸収のハートを持っているか (`has_player_absorption_hearts`)

**目的:** プレイヤーに吸収のハート（金色のハート）があるかを確認します。

**値:** 不要

## プレイヤーがウィザー状態か (`is_player_withered`)

**目的:** プレイヤーがウィザー効果を受けているかを確認します。

**値:** 不要

## プレイヤーが完全凍結しているか (`is_player_fully_frozen`)

**目的:** プレイヤーが完全に凍結しているかを確認します（通常は粉雪によるもの）。

**値:** 不要

## プレイヤーが毒状態か (`is_player_poisoned`)

**目的:** プレイヤーが毒効果を受けているかを確認します。

**値:** 不要

## プレイヤーがバイオーム内にいるか (`is_player_in_biome`)

**目的:** プレイヤーが特定のバイオームにいるかを確認します。

**値:** 必須 — バイオーム識別子（例: `minecraft:birch_forest`）

## プレイヤーがディメンション内にいるか (`is_player_in_dimension`)

**目的:** プレイヤーが特定のディメンションにいるかを確認します。

**値:** 必須 — ディメンション識別子（例: `minecraft:overworld`, `minecraft:the_nether`, `minecraft:the_end`）

## プレイヤーが構造物内にいるか (`is_player_in_structure`)

**目的:** プレイヤーが現在特定の構造物の内部にいるかを確認します。サーバーワールドではサーバー側に FancyMenu が必要です。

**値:** 必須 — 構造物識別子（例: `minecraft:village`）

## 近くにエンティティがいるか (`is_entity_nearby`)

**目的:** 特定のエンティティ種別がプレイヤーの一定半径内にいるかを確認します。

**値:** 必須 — 形式: "radius:entity_id"（例: `10:minecraft:pig` - 10 ブロック以内にブタがいるかを確認）

## 効果が有効か (`is_effect_active`)

**目的:** 特定のポーション効果がプレイヤーに有効かを確認します。

**値:** 必須 — 効果識別子（例: `minecraft:speed`, `minecraft:strength`）

## いずれかの効果が有効か (`is_any_effect_active`)

**目的:** プレイヤーに何らかのポーション効果が有効かを確認します。

**値:** 不要

## プレイヤーが左利きか (`is_left_handed`)

**目的:** プレイヤーがゲーム設定で左利きモードになっているかを確認します。

**値:** 不要

## インベントリスロットが埋まっているか (`is_inventory_slot_filled`)

**目的:** 特定のインベントリスロットにアイテムが入っているかを確認します。

**値:** 必須 — スロット番号（メインインベントリは 0-35、ホットバーは 0-8）

## インベントリでアイテムがホバーされているか (`is_item_hovered_in_inventory`)

**目的:** カーソルがインベントリ画面上の任意のアイテムにホバーしているかを確認します。

**値:** 不要

## カーソルがインベントリアイテムを持っているか (`is_cursor_holding_inventory_item`)

**目的:** カーソルが現在インベントリアイテムのスタックを持っているかを確認します。

**値:** 不要

## ホットバースロットが選択されているか (`is_hotbar_slot_active`)

**目的:** 特定のホットバースロットが現在選択されているかを確認します。

**値:** 必須 — ホットバースロット番号（0-8）

## プレイヤーが権限レベルを持っているか (`fancymenu_loading_requirement_has_player_permission_level`)

**目的:** プレイヤーが現在のワールドまたはサーバーで、指定された権限/OP レベル以上を持っているかを確認します。

**値:** 必須 — 権限レベルの数値（0-4、4 はサーバーオペレーター）

## 攻撃力が弱まっているか (`is_attack_strength_weakened`)

**目的:** プレイヤーの攻撃力が現在弱まっているか（完全にチャージされていないか）を確認します。

**値:** 不要

## 現地時間の日付が一致するか (`fancymenu_visibility_requirement_is_realtime_day`)

**目的:** 現在の実世界の日付が特定の値と一致するかを確認します。

**値:** 必須 — 日にち（1-31）。複数の値はカンマ区切りで指定できます。

## 現地時間の時刻が一致するか (`fancymenu_visibility_requirement_is_realtime_hour`)

**目的:** 現在の実世界の時刻が特定の値と一致するかを確認します。

**値:** 必須 — 24時間形式の時（0-23）。複数の値はカンマ区切りで指定できます。

## 現地時間の分が一致するか (`fancymenu_visibility_requirement_is_realtime_minute`)

**目的:** 現在の実世界の分が特定の値と一致するかを確認します。

**値:** 必須 — 分（0-59）。複数の値はカンマ区切りで指定できます。

## 現地時間の月が一致するか (`fancymenu_visibility_requirement_is_realtime_month`)

**目的:** 現在の実世界の月が特定の値と一致するかを確認します。

**値:** 必須 — 月の番号（1-12、1 は 1 月）。複数の値はカンマ区切りで指定できます。

## 現地時間の秒が一致するか (`fancymenu_visibility_requirement_is_realtime_second`)

**目的:** 現在の実世界の秒が特定の値と一致するかを確認します。

**値:** 必須 — 秒（0-59）。複数の値はカンマ区切りで指定できます。

## 現地時間の曜日が一致するか (`fancymenu_visibility_requirement_is_realtime_week_day`)

**目的:** 現在の実世界の曜日が特定の値と一致するかを確認します。

**値:** 必須 — 曜日を数値で指定（1-7、1 は日曜日）。複数の値はカンマ区切りで指定できます。

## 現地時間の年が一致するか (`fancymenu_visibility_requirement_is_realtime_year`)

**目的:** 現在の実世界の年が特定の値と一致するかを確認します。

**値:** 必須 — 西暦の年（例: "2023"）。複数の値はカンマ区切りで指定できます。

## ファイル/フォルダが存在するか (`fancymenu_loading_requirement_file_exists`)

**目的:** ファイルまたはディレクトリが存在するかを確認します。

**値:** 必須 — アクティブなゲームディレクトリからの相対パス、または標準的な Minecraft ディレクトリを示す `.minecraft/` で始まるパス。ファイルとディレクトリの両方が存在するとみなされます。

## OS が Linux か (`fancymenu_loading_requirement_is_os_linux`)

**目的:** 現在のプラットフォームが Windows でも macOS でもないかを確認します。通常は Linux 環境に対応します。

**値:** 不要

## OS が macOS か (`fancymenu_loading_requirement_is_os_macos`)

**目的:** オペレーティングシステムが macOS かを確認します。

**値:** 不要

## OS が Windows か (`fancymenu_loading_requirement_is_os_windows`)

**目的:** オペレーティングシステムが Windows かを確認します。

**値:** 不要

## インターネット接続が利用可能か (`is_internet_connection_available`)

**目的:** 有効なインターネット接続が利用可能かを確認します。

**値:** 不要

## ゲーム言語か (`fancymenu_loading_requirement_is_language`)

**目的:** 現在のゲーム言語が特定の値と一致するかを確認します。

**値:** 必須 — 言語コード（例: 英語なら `en_us`）

## Mod が読み込まれているか (`fancymenu_loading_requirement_is_mod_loaded`)

**目的:** 特定の Mod が読み込まれているかを確認します。

**値:** 必須 — Mod ID（例: `fancymenu`, `jei`）。OptiFine は `optifine` で確認できます。カンマ区切りで複数の Mod ID を指定でき、指定した Mod はすべて読み込まれている必要があります。

## MCEF が読み込まれているか (`is_mcef_loaded`)

**目的:** MCEF（Minecraft Chromium Embedded Framework）がインストールされ、初期化されているかを確認します。MCEF は [Browser 要素](./elements#browser) と [廃止済みの MCEF ベース動画タイプ](./video#requirements) に必要です。[ネイティブ動画機能](./video) では Watermedia を使用します。

**値:** 不要

## 数値か (`fancymenu_visibility_requirement_is_number`)

**目的:** さまざまな比較モードによる高度な数値比較を行います。

**値:** 必須 — 複雑な形式: `["mode":"comparison_mode","number":"value1","compare_with":"value2"]$`。`comparison_mode` は `equals`, `bigger-than`, `smaller-than`, `bigger-than-or-equals`, `smaller-than-or-equals` のいずれかです。

## テキストか (`fancymenu_visibility_requirement_is_text`)

**目的:** さまざまな比較モードによる高度なテキスト比較を行います。

**値:** 必須 — 複雑な形式: `["mode":"comparison_mode","text":"text1","compare_with":"text2"]$`。`comparison_mode` は `equals`, `contains`, `starts-with`, `ends-with` のいずれかです。

## サーバー IP が一致するか (`fancymenu_visibility_requirement_is_server_ip`)

**目的:** 現在のサーバー IP が特定の値と一致するかを確認します。

**値:** 必須 — サーバー IP アドレス（ポートあり/なし）

## サーバーがオンラインか (`fancymenu_loading_requirement_is_server_online`)

**目的:** 特定のサーバーがオンラインで到達可能かを確認します。

**値:** 必須 — サーバー IP アドレス（ポートあり/なし）

## リソースパックが有効か (`is_resource_pack_enabled`)

**目的:** 特定のリソースパックが現在選択/有効になっているかを確認します。

**値:** 必須 — リソースパックの表示名またはパック ID（例: `Programmer Art`、またはパックの ID）

## 変数の値が一致するか（FM 変数） (`fancymenu_visibility_requirement_is_variable_value`)

**目的:** FancyMenu の変数が特定の値を持っているかを確認します。

**値:** 必須 — 形式: "variable_name:expected_value"

## セッションごとに 1 回のみ (`once_per_session`)

**目的:** 設定された各インスタンスは、ゲームセッションごとに 1 回だけ true を返します。異なるインスタンスは個別に追跡されます。

**値:** 不要
