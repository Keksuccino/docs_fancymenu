---
title: 動画 (MP4)
description: FancyMenu で動画を使用する際に知っておくべきこと。
---

# 動画

FancyMenu は、MP4 動画を要素、メニューバックグラウンド、Game Intro コンテンツとして再生することをサポートしています。

FancyMenu 3.9.0 では、Watermedia V3 を利用した新しいネイティブの **Video** 要素と **Video** メニューバックグラウンドが追加されました。旧 **Video [MCEF]** 要素/バックグラウンドタイプは非推奨で、まだ必要な古いレイアウトにのみ残してください。

動画のバックグラウンドや要素を制御するための次の **アクション** もあります。

- **Set Video Element Volume**: Video 要素の音量を設定する
- **Set Video Element Play Time**: Video 要素をミリ秒のタイムスタンプへシークする
- **Toggle Video Element Paused State**: Video 要素の一時停止状態を切り替える
- **Set Video Background Volume**: Video メニューバックグラウンドの音量を設定する
- **Set Video Background Play Time**: Video メニューバックグラウンドをミリ秒のタイムスタンプへシークする
- **Toggle Video Background Paused State**: Video メニューバックグラウンドの一時停止状態を切り替える

また、動画のバックグラウンドや要素に関する情報を取得するための次の **プレースホルダー** もあります。

- **Video Element Volume**: Video 要素の音量を取得する
- **Video Element Duration**: Video 要素の再生時間を取得する
- **Video Element Play Time**: Video 要素の現在の再生時間（進行状況）を取得する
- **Video Element Paused State**: Video 要素の一時停止状態（true/false）を取得する
- **Video Background Volume**: Video メニューバックグラウンドの音量を取得する
- **Video Background Duration**: Video メニューバックグラウンドの再生時間を取得する
- **Video Background Play Time**: Video メニューバックグラウンドの現在の再生時間（進行状況）を取得する
- **Video Background Paused State**: Video メニューバックグラウンドの一時停止状態（true/false）を取得する

再生時間と再生位置のプレースホルダーは、既定では `MM:SS` を返します。ミリ秒のタイムスタンプが必要な場合は `output_as_timestamp` を `true` に設定してください。再生位置のプレースホルダーでは、`show_percentage` を使って 0〜100 の進行率を表示することもできます。

FancyMenu 3.9.0 では、`PLAYING`、`PAUSED`、`STOPPED`、`FINISHED` に反応できる **On Video Playback Status Changed** リスナーも追加されています。

## 要件

新しいネイティブの Video 要素とメニューバックグラウンドタイプを使用するには、以下をインストールする必要があります。

- **Watermedia V3**
- **Watermedia Binaries V3**

これらは任意依存関係なので、動画サポートを使いたい場合はインスタンスに手動で追加する必要があります。

非推奨の **Video [MCEF]** タイプは、引き続き MCEF を使用します。新しいレイアウトでは、代わりに Watermedia ベースのネイティブ Video タイプを使用してください。

## ローディング画面での動画

動画サポートはローディング画面（ゲーム/リソース読み込み画面とワールド読み込み画面）では動作しません。

そのため、**Drippy Loading Screen** を使ってゲームのローディング画面に動画を追加するべきではありません。ほとんどの場合、動作しないためです。

代わりに、ローディング画面では短くてシンプルな AFMA/FMA ファイルを使用してください。アニメーションが十分に短く単純であれば、ユーザーは再読み込みされていることにほとんど気づきません。

## トラブルシューティング

ネイティブ動画サポートに問題がある場合は、まず Watermedia V3 と Watermedia Binaries V3 の両方がインストールされており、Minecraft / modloader のバージョンと一致していることを確認してください。
