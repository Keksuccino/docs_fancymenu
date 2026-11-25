---
title: 動画（MP4）
description: FancyMenuで動画を使用する際に知っておくべきこと。
sourceBlobSha: bd34c5c21a6c08d6b66a7b2acdaf9bd12739732f
---
# 動画

FancyMenuでは、MP4動画を[要素](/elements#video)、[メニュー背景](/menu-backgrounds#video)、[ゲームイントロ](/game-intro)のコンテンツとして再生できます。

標準の[**動画**要素](/elements#video)と**動画**メニュー背景には、Watermedia V3が使用されます。旧式の**動画 [Rinku]**タイプは非推奨です。引き続き必要なレイアウトにのみ残してください。

動画の背景や要素を操作するための[アクション](/action-scripts)もあります。

- [**動画要素の音量を設定**](/action-scripts#set-video-element-volume)は、動画要素の音量を設定します。
- [**動画要素の再生時間を設定**](/action-scripts#set-video-element-play-time)は、動画要素の再生位置をミリ秒単位のタイムスタンプに移動します。
- [**動画要素の一時停止状態を切り替え**](/action-scripts#toggle-video-element-paused-state)は、動画要素の一時停止状態を切り替えます。
- [**動画背景の音量を設定**](/action-scripts#set-video-background-volume)は、動画メニュー背景の音量を設定します。
- [**動画背景の再生時間を設定**](/action-scripts#set-video-background-play-time)は、動画メニュー背景の再生位置をミリ秒単位のタイムスタンプに移動します。
- [**動画背景の一時停止状態を切り替え**](/action-scripts#toggle-video-background-paused-state)は、動画メニュー背景の一時停止状態を切り替えます。

また、動画の背景や要素に関する情報を取得するための[プレースホルダー](/placeholders)もあります。

- [**動画要素の音量**](/placeholders#video-element-volume)は、動画要素の音量を返します。
- [**動画要素の長さ**](/placeholders#video-element-duration)は、動画要素の長さを返します。
- [**動画要素の再生時間**](/placeholders#video-element-play-time)は、動画要素の現在の再生位置を返します。
- [**動画要素の一時停止状態**](/placeholders#video-element-paused-state)は、動画要素が一時停止中かどうかを返します。
- [**動画背景の音量**](/placeholders#video-background-volume)は、動画メニュー背景の音量を返します。
- [**動画背景の長さ**](/placeholders#video-background-duration)は、動画メニュー背景の長さを返します。
- [**動画背景の再生時間**](/placeholders#video-background-play-time)は、動画メニュー背景の現在の再生位置を返します。
- [**動画背景の一時停止状態**](/placeholders#video-background-paused-state)は、動画メニュー背景が一時停止中かどうかを返します。

長さと再生時間のプレースホルダーは、デフォルトで`MM:SS`を返します。ミリ秒単位のタイムスタンプが必要な場合は、`output_as_timestamp`を`true`に設定してください。再生時間のプレースホルダーでは、引き続き`show_percentage`を使用して、0～100の進捗値を取得できます。

音量と一時停止状態の値は、識別子に関連付けられたコントローラーメタデータです。長さと再生時間の値を取得するには、対応する動画要素または背景が現在の画面で有効になり、再生準備が完了している必要があります。

[**動画再生状態変更**リスナー](/listeners#video-playback-status-changed)は、`PLAYING`、`PAUSED`、`STOPPED`、`FINISHED`に反応します。

## 必要条件

新しい標準の動画要素とメニュー背景タイプを使用するには、次のものをインストールする必要があります。

- **Watermedia V3**
- **Watermedia Binaries V3**

これらは任意の依存関係のため、動画を使用する場合はインスタンスに手動で追加する必要があります。

標準の動画再生にはOpenGLレンダラーも必要です。MinecraftがVulkanを使用している間はWatermediaで再生できません。動画要素、動画メニュー背景、[動画ゲームイントロ](/game-intro)を使用するには、OpenGLに切り替えてください。

非推奨の**動画 [Rinku]**タイプでは、引き続き[Rinku](https://modrinth.com/mod/rinku)が使用されます。新しいレイアウトでは、代わりにWatermediaを使用する標準の動画タイプを使用してください。

## ローディング画面での動画

ローディング画面（ゲーム／リソースの読み込み画面およびワールドの読み込み画面）では、動画は動作しません。

そのため、**Drippy Loading Screen**を使ってゲームのローディング画面に動画を追加しても、ほとんどの場合は動作しません。

ローディング画面では、代わりに短くシンプルな[アニメーション](/animations)（APNGまたはGIF）を使用してください。

## トラブルシューティング

標準の動画が再生されない場合は、Watermedia V3とWatermedia Binaries V3がMinecraft／Modローダーのバージョンに対応していること、およびMinecraftがVulkanではなくOpenGLを使用していることを確認してください。
