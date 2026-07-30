---
title: 動画（MP4）
description: FancyMenu で動画を使う際に知っておくべきこと。
---
# 動画

FancyMenu は、MP4 動画を [要素](./elements#video)、[メニュー背景](./menu-backgrounds)、および [ゲームイントロ](./game-intro) のコンテンツとして再生できます。

ネイティブの [**Video** 要素](./elements#video) と **Video** メニュー背景は Watermedia V3 を使用します。旧 **Video [MCEF]** タイプは非推奨であり、まだ必要なレイアウトにのみ残してください。

動画背景や要素を制御するための次の **アクション** もあります。

- [**Set Video Element Volume**](./action-scripts#set-video-element-volume-set_video_element_volume) は Video 要素の音量を設定します。
- [**Set Video Element Play Time**](./action-scripts#set-video-element-play-time-set_video_element_play_time) は Video 要素をミリ秒単位のタイムスタンプへシークします。
- [**Toggle Video Element Paused State**](./action-scripts#toggle-video-element-paused-state-toggle_video_element_pause_state) は Video 要素の一時停止状態を切り替えます。
- [**Set Video Background Volume**](./action-scripts#set-video-background-volume-set_video_menu_background_volume) は Video メニュー背景の音量を設定します。
- [**Set Video Background Play Time**](./action-scripts#set-video-background-play-time-set_video_menu_background_play_time) は Video メニュー背景をミリ秒単位のタイムスタンプへシークします。
- [**Toggle Video Background Paused State**](./action-scripts#toggle-video-background-paused-state-toggle_video_menu_background_pause_state) は Video メニュー背景の一時停止状態を切り替えます。

また、動画背景や要素に関する情報を取得するための次の **プレースホルダー** もあります。

- [**Video Element Volume**](./placeholders#video-element-volume-video_element_vol) は Video 要素の音量を返します。
- [**Video Element Duration**](./placeholders#video-element-duration-video_element_duration) は Video 要素の再生時間を返します。
- [**Video Element Play Time**](./placeholders#video-element-play-time-video_element_playtime) は Video 要素の現在の進行状況を返します。
- [**Video Element Paused State**](./placeholders#video-element-paused-state-video_element_paused_state) は Video 要素が一時停止中かどうかを返します。
- [**Video Background Volume**](./placeholders#video-background-volume-video_background_vol) は Video メニュー背景の音量を返します。
- [**Video Background Duration**](./placeholders#video-background-duration-video_background_duration) は Video メニュー背景の再生時間を返します。
- [**Video Background Play Time**](./placeholders#video-background-play-time-video_background_playtime) は Video メニュー背景の現在の進行状況を返します。
- [**Video Background Paused State**](./placeholders#video-background-paused-state-video_background_paused_state) は Video メニュー背景が一時停止中かどうかを返します。

再生時間と進行時間のプレースホルダーは、デフォルトで `MM:SS` を返します。ミリ秒単位のタイムスタンプが必要な場合は、`output_as_timestamp` を `true` に設定してください。再生時間のプレースホルダーでは、0～100 の進行値を取得するために `show_percentage` も引き続き使用できます。

音量と一時停止状態の値は、識別子に関連付けられたコントローラーメタデータです。再生時間と進行時間の値は、現在の画面で対応する Video 要素または背景がアクティブで、準備完了である必要があります。

[**On Video Playback Status Changed** リスナー](./listeners#on-video-playback-status-changed-video_playback_status_changed) は、`PLAYING`、`PAUSED`、`STOPPED`、`FINISHED` に反応できます。

## 要件

新しいネイティブの Video 要素とメニュー背景タイプを使用するには、次をインストールする必要があります。

- **Watermedia V3**
- **Watermedia Binaries V3**

これらはオプションの依存関係のため、動画サポートを使いたい場合はインスタンスに手動で追加する必要があります。

ネイティブ動画再生には OpenGL レンダラーも必要です。Minecraft が Vulkan を使用している間は Watermedia 再生は利用できません。Video 要素、Video メニュー背景、[動画ゲームイントロ](./game-intro) を使うには OpenGL に切り替えてください。

非推奨の **Video [MCEF]** タイプは、引き続き MCEF を使用します。新しいレイアウトでは、代わりに Watermedia ベースのネイティブ Video タイプを使用してください。

## 読み込み画面での動画

動画サポートは、読み込み画面（ゲーム/リソース読み込み画面およびワールド読み込み画面）では動作しません。

つまり、**Drippy Loading Screen** を使ってゲーム読み込み画面に動画を追加するべきではありません。ほとんどの場合、正常に動作しないためです。

代わりに、読み込み画面では短くてシンプルな [AFMA/FMA アニメーション](./fma) を使用してください。

## トラブルシューティング

ネイティブ動画が再生されない場合は、Watermedia V3 と Watermedia Binaries V3 が Minecraft / mod ローダーのバージョンと一致していること、また Minecraft が Vulkan ではなく OpenGL を使用していることを確認してください。
