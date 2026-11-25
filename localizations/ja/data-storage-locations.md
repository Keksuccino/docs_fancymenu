---
title: データの保存場所
description: FancyMenuがレイアウト、アセット、設定などを保存する場所と、各プロファイルに属するファイルについて説明します。
sourceBlobSha: 30dd81ed90e08184e3063892870e3325d7d7c5cb
---

# データの保存場所

FancyMenuは、ゲームディレクトリ内の2つのフォルダーにすべてのデータを保存します。ここでいうゲームディレクトリはランチャーのインスタンスフォルダーで、`.minecraft`とは異なる場合があります。

- `config/fancymenu/` には、レイアウト、アセット、変数、設定などのセットアップ情報が保存されます。読み込まれている[プロファイル](/profiles)のデータで、MODパックにはこのフォルダーが含まれます。
- `fancymenu_data/` には、Draggerの位置やダウンロードデータなど、このゲームインスタンスのデータが保存されます。どのプロファイルでも共通です。

**メニューバー -> ツール -> FancyMenuのディレクトリを開く**を選ぶと、`config/fancymenu/`が開きます。

ほとんどのファイルやフォルダーは、該当する機能を使うと作成されます。ファイルを変更または削除する前に、ゲームを終了してください。

> [!TIP]
> これらのフォルダーを複数のインスタンス間で共有するには、別の場所に移動し、元の場所にシンボリックリンク（Windowsではジャンクション）を作成します。

# セットアップデータ

`<game-directory>/config/fancymenu/`内のすべてのデータです。すべて、読み込まれている[プロファイル](/profiles)に属します。

| 内容 | 場所 |
| --- | --- |
| `.txt`ファイル形式のレイアウト（サブフォルダー内のものも含む） | `customization/` |
| 画像やサウンドなどの[ローカルアセット](/resources#local-resources) | `assets/` |
| FancyMenuの設定 | `options.txt` |
| **現在の画面のカスタマイズ**が有効になっている画面 | `customizablemenus.txt` |
| [カスタムGUI](/custom-guis)と、そのカスタムGUIで置き換える画面 | `custom_gui_screens.txt` |
| [変数](/variables) | `user_variables.db` |
| [リスナー](/listeners) | `listener_instances.txt` |
| [スケジューラー](/schedulers) | `scheduler_instances.txt` |
| [パノラマ](/panoramas) | `panoramas/` |
| [スライドショー](/slideshows) | `slideshows/` |
| [カスタムローカライズ](/localization#fancymenu-custom-localization-files) | `custom_locals/` |
| FancyMenu独自のUIテーマ（**メニューバー -> カスタマイズ -> 設定 -> FancyMenuのUI -> UIテーマ**） | `ui_themes/` |
| 変数を使わない[チェックボックス要素](/elements#checkbox)の状態 | `checkbox_states.json` |
| アクションによって[動画要素](/video)に設定された音量と一時停止状態 | `video_element_controller_metas.json` |
| アクションによって[オーディオ要素](/elements#audio)に設定された音量 | `audio_element_controller_metas.json` |
| アクションによって[要素アニメーター](/element-animator)に設定されたオン／オフ状態 | `animation_controller_states.json` |
| **現在の画面のスクロール領域の内容を公開**が有効になっている画面（[スクロール可能な画面のカスタマイズ](/customizing-scrollable-screens)を参照） | `normalized_scroll_screens.json` |
| [FM Data](/fm-data)のサーバーリスナー | `fmdata_server_listeners.json` |
| [FM Data](/fm-data)のウェルカムデータ | `fmdata_welcome_data.json` |
| レイアウトエディターのウィジェットの位置、サイズ、表示状態 | `layout_editor/widgets/` |
| 読み込まれているプロファイルの名前、アイコン、詳細 | `profile.json`および`profile_icon.png` |
| その他の[プロファイル](/profiles#where-profiles-are-stored) | `profiles/` |
| 古いファイルに対するFancyMenuの更新処理の実行状況 | `legacy_checklist.txt` |

`customizablemenus.txt`には、画面がJavaクラス名で記録されます。`title_screen`のような短い[画面識別子](/screen-identifiers)は記録されません。

専用サーバーでは、FancyMenuはサーバーの`config/fancymenu/`フォルダーにある2つの[FM Data](/fm-data)ファイルのみを使用します。

# インスタンスデータ

`<game-directory>/fancymenu_data/`内のすべてのデータです。プロファイルには含まれないため、プロファイルを切り替えても保持されます。

| 内容 | 場所 |
| --- | --- |
| [Dragger要素](/dragger)の位置 | `dragger_metas.json` |
| **最後にプレイしたワールド／サーバーに入る**アクションと**最後のワールドまたはサーバー**プレースホルダーで使う、最後にプレイしたワールドまたはサーバー | `last_world.fmdata` |
| [シームレスなワールド読み込み](/seamless-world-loading)のスクリーンショット | `seamless_world_loading/` |
| [Buddy](/decoration-overlays#buddy)のセーブデータ（Buddyオーバーレイごとに2つのファイル） | `buddy/` |
| [AI向けエクスポート](/export-for-ai)のファイル | `ai_exports/` |
| アクション選択画面でお気に入りに登録したアクション | `action_favorites.json` |
| ファイル選択画面でのオーディオおよび動画プレビューの音量 | `browser_audio_settings.json`および`browser_video_settings.json` |
| 一時停止中に[動画背景](/video)に表示されるフレーム | `video_thumbnails/` |
| [AFMAクリエーター](/animations#fma-and-afma)用にFancyMenuがダウンロードするFFmpeg | `ffmpeg_cache/` |
| FancyMenuが[**デフォルトのGUIスケール**](/global-customizations)をすでに設定したことを示す記録 | `default_scale_set.fm` |
| 一時ファイル（ゲーム起動時に毎回削除されます） | `fancymenu_temp/` |

- FancyMenuが**デフォルトのGUIスケール**を設定するのは一度だけです。`default_scale_set.fm`を削除すると、次回起動時に再びスケールが設定されます。
- シームレスなワールド読み込みのスクリーンショットには、ワールド内で画面に表示されていたものがすべて写ります。残したくない場合は、ゲームを終了してから削除してください。

# 古いバージョンのファイル

古いバージョンのFancyMenuでは、一部のファイルが別の場所に保存されていました。これらのファイルは、次回ゲームを起動したときにFancyMenuによって引き継がれます。

- ゲームディレクトリ直下にある`checkbox_states.json`と`normalized_scroll_screens.json`は、`config/fancymenu/`に移動されます。
- `config/fancymenu/`にある`dragger_metas.json`は、`fancymenu_data/`に移動されます。
