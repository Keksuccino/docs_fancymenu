---
title: 動画（MP4）
description: FancyMenuで動画を使用する際に知っておくべきこと。
sourceBlobSha: 2ec0bfe39528bb93095798f6a2a1cc7cbe17e5eb
---
# 動画

FancyMenuは、MP4動画を[要素](./elements#video)、[メニュー背景](./menu-backgrounds)、および[ゲームイントロ](./game-intro)のコンテンツとして再生できます。

ネイティブの[**Video**要素](./elements#video)と**Video**メニュー背景は、Watermedia V3を使用します。従来の**Video [Rinku]**タイプは非推奨であり、引き続き必要とするレイアウトにのみ残してください。

動画の背景や要素を制御するために、次の**アクション**も利用できます。

- [**Video要素の音量を設定**](./action-scripts#set-video-element-volume-set_video_element_volume)：Video要素の音量を設定します。
- [**Video要素の再生時間を設定**](./action-scripts#set-video-element-play-time-set_video_element_play_time)：Video要素を指定したミリ秒のタイムスタンプへシークします。
- [**Video要素の一時停止状態を切り替え**](./action-scripts#toggle-video-element-paused-state-toggle_video_element_pause_state)：Video要素の一時停止状態を切り替えます。
- [**Video背景の音量を設定**](./action-scripts#set-video-background-volume-set_video_menu_background_volume)：Videoメニュー背景の音量を設定します。
- [**Video背景の再生時間を設定**](./action-scripts#set-video-background-play-time-set_video_menu_background_play_time)：Videoメニュー背景を指定したミリ秒のタイムスタンプへシークします。
- [**Video背景の一時停止状態を切り替え**](./action-scripts#toggle-video-background-paused-state-toggle_video_menu_background_pause_state)：Videoメニュー背景の一時停止状態を切り替えます。

また、動画の背景や要素に関する情報を取得するために、次の**プレースホルダー**を使用できます。

- [**Video要素の音量**](./placeholders#video-element-volume-video_element_vol)：Video要素の音量を返します。
- [**Video要素の長さ**](./placeholders#video-element-duration-video_element_duration)：Video要素の長さを返します。
- [**Video要素の再生時間**](./placeholders#video-element-play-time-video_element_playtime)：Video要素の現在の再生進行状況を返します。
- [**Video要素の一時停止状態**](./placeholders#video-element-paused-state-video_element_paused_state)：Video要素が一時停止中かどうかを返します。
- [**Video背景の音量**](./placeholders#video-background-volume-video_background_vol)：Videoメニュー背景の音量を返します。
- [**Video背景の長さ**](./placeholders#video-background-duration-video_background_duration)：Videoメニュー背景の長さを返します。
- [**Video背景の再生時間**](./placeholders#video-background-play-time-video_background_playtime)：Videoメニュー背景の現在の再生進行状況を返します。
- [**Video背景の一時停止状態**](./placeholders#video-background-paused-state-video_background_paused_state)：Videoメニュー背景が一時停止中かどうかを返します。

長さと再生時間のプレースホルダーは、デフォルトで `MM:SS` を返します。ミリ秒のタイムスタンプが必要な場合は、`output_as_timestamp`を`true`に設定してください。再生時間のプレースホルダーでは、0～100の進行状況を示す`show_percentage`も引き続き使用できます。

音量と一時停止状態の値は、識別子に関連付けられたコントローラーメタデータです。長さと再生時間の値を取得するには、現在の画面で対応するVideo要素または背景がアクティブで、再生可能な状態になっている必要があります。

[**動画再生ステータス変更時**リスナー](./listeners#on-video-playback-status-changed-video_playback_status_changed)は、`PLAYING`、`PAUSED`、`STOPPED`、`FINISHED`に反応できます。

## 必要条件

新しいネイティブのVideo要素とメニュー背景タイプを使用するには、次のものをインストールする必要があります。

- **Watermedia V3**
- **Watermedia Binaries V3**

これらはオプションの依存関係であるため、動画をサポートする場合はインスタンスに手動で追加する必要があります。

ネイティブ動画の再生には、OpenGLレンダラーも必要です。MinecraftがVulkanを使用している間はWatermediaによる再生を利用できません。Video要素、Videoメニュー背景、および[動画ゲームイントロ](./game-intro)を使用するには、OpenGLに切り替えてください。

非推奨の**Video [Rinku]**タイプは、引き続き[Rinku](https://modrinth.com/mod/rinku)を使用します。新しいレイアウトでは、代わりにWatermediaを使用するネイティブのVideoタイプを利用してください。

## ロード画面での動画

動画サポートはロード画面（ゲーム／リソースのロード画面およびワールドのロード画面）では機能しません。

これは、**Drippy Loading Screen**を使用してゲームのロード画面に動画を追加しても、ほとんどの場合機能しないことを意味します。

代わりに、ロード画面では短くシンプルな[AFMA/FMAアニメーション](./fma)を使用してください。

## トラブルシューティング

ネイティブ動画が再生されない場合は、Watermedia V3とWatermedia Binaries V3がMinecraft／Mod Loaderのバージョンに対応していること、およびMinecraftがVulkanではなくOpenGLを使用していることを確認してください。
