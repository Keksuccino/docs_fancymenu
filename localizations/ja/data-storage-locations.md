---
title: データ保存場所
description: FancyMenu がレイアウト、リソース、設定、および永続的なランタイム状態を保存する場所。
---

# データ保存場所

`<game-directory>` は有効な Minecraft インスタンスのフォルダを意味し、`.minecraft` とは異なる場合があります。

ディレクトリやファイルは、通常、関連機能が初期化または使用された後にのみ作成されます。生成された状態ファイルを手動で編集する前には Minecraft を終了し、データを移行またはリセットする際はバックアップを保管してください。

# レイアウト、リソース、設定

一部の項目は設定やアセットとして作成され、ほかは FancyMenu が実行時に更新する状態データです。

| システム / 機能 | ファイルまたはディレクトリ |
| --- | --- |
| カスタマイズ可能な画面 | `<game-directory>/config/fancymenu/customizablemenus.txt` |
| [カスタム GUI](./custom-guis) と画面上書きルール | `<game-directory>/config/fancymenu/custom_gui_screens.txt` |
| レイアウト | `<game-directory>/config/fancymenu/customization/` |
| [ローカルアセット](./resources#local-resources) | `<game-directory>/config/fancymenu/assets/` |
| [カスタムローカライズファイル](./localization#fancymenu-custom-localization-files) | `<game-directory>/config/fancymenu/custom_locals/` |
| [パノラマ](./panoramas) | `<game-directory>/config/fancymenu/panoramas/` |
| [スライドショー](./slideshows) | `<game-directory>/config/fancymenu/slideshows/` |
| [FancyMenu 変数](./variables) | `<game-directory>/config/fancymenu/user_variables.db` |
| [ビデオ要素](./elements#video) のコントローラメタデータ | `<game-directory>/config/fancymenu/video_element_controller_metas.json` |
| [オーディオ要素](./elements#audio) のコントローラメタデータ | `<game-directory>/config/fancymenu/audio_element_controller_metas.json` |
| [FM Data](./fm-data) のサーバーリスナー | `<game-directory>/config/fancymenu/fmdata_server_listeners.json` |
| [FM Data](./fm-data) のウェルカムデータ | `<game-directory>/config/fancymenu/fmdata_welcome_data.json` |
| [リスナー](./listeners) のインスタンスとアクションスクリプト | `<game-directory>/config/fancymenu/listener_instances.txt` |
| [スケジューラ](./schedulers) | `<game-directory>/config/fancymenu/scheduler_instances.txt` |

`customizablemenus.txt` は **現在の画面のカスタマイズ** トグルによって管理され、具体的な画面クラスの識別子を保存します。[ユニバーサル レイアウト](./universal-layouts) の識別子は追加しないでください。FancyMenu はファイルの読み込み時にそれらを無視します。

専用サーバーでは、2 つの FM Data ファイルはそのサーバーのゲームルートを基準とした相対パスになります。その他のクライアント所有の設定とリソースは、各プレイヤーのインスタンスに属します。

# 永続的なランタイム状態

FancyMenu は、`config/fancymenu/` の外にも、追加の生成済みインスタンス別状態を保存します。これらのパスは、関連するユーザー／ランタイム状態を保持したい場合にのみバックアップに含めてください。これらはレイアウト定義や元のアセットではありません。

| システム / 機能 | ファイルまたはディレクトリ |
| --- | --- |
| 変数ではない [チェックボックス](./elements#checkbox) の状態 | `<game-directory>/checkbox_states.json` |
| [ドラッガー](./dragger) 要素の位置 / メタデータ | `<game-directory>/fancymenu_data/dragger_metas.json` |
| 最後のワールド状態 | `<game-directory>/fancymenu_data/last_world.fmdata` |
| [シームレス ワールド ローディング](./seamless-world-loading) の状態 | `<game-directory>/fancymenu_data/seamless_world_loading/` |
| Buddy のペットおよびレベルアップの保存データ | `<game-directory>/fancymenu_data/buddy/` |
| レイアウトエディタのウィジェット位置と表示状態 | `<game-directory>/config/fancymenu/layout_editor/widgets/` |
| デフォルト GUI スケール初期化マーカー | `<game-directory>/fancymenu_data/default_scale_set.fm` |

Buddy は、ペットの状態とレベルアップ／実績の状態を、それぞれディレクトリ内の別々の JSON ファイルに保存します。Buddy の各オーバーレイインスタンスは、それぞれ独自の 2 つのファイルを使用します。

レイアウトエディタのウィジェットファイルには、各ウィジェットの位置、サイズ、表示状態、展開状態、およびスナップ先の側が保存されます。`default_scale_set.fm` を削除すると、次回起動時に FancyMenu は設定済みのデフォルト GUI スケールがまだ適用されていないものとして扱います。
