---
title: リモートサーバー通信
description: FancyMenu のクライアントと外部サーバー間で、カスタムテキストデータを送受信します。
---

# リモートサーバー通信

「リモートサーバー通信」システムを使うと、FancyMenu クライアントは WebSocket 接続を介して外部サーバーと通信できます。

すべてのデータはテキストベースです。

- プレーンテキストに対応しています
- JSON にも対応しています（通常のテキストとして扱われます）

各サーバー URL には、実行中に 1 つのキャッシュ済み **リクエスト ID** が割り当てられます。
FancyMenu はこの ID を使って接続を追跡し、リスナー変数で参照できるようにします。

# クイックスタート

1. アクション **Connect To Remote Server** を追加する（任意ですが、早めに接続を開くのに便利です）
2. 同じ URL でアクション **Send Data To Remote Server** を追加する
3. 返信に反応するため、リスナー **On Remote Server Data Received** を追加する
4. 接続状態の処理には **On Remote Server Connected** / **On Remote Server Connection Closed** を使う
5. 必要に応じて close アクションで接続を閉じる

# アクション

## Connect To Remote Server

ペイロードデータを送信せずに、リモートサーバー接続を初期化します。

入力:

- リモートサーバー URL

## Send Data To Remote Server

接続を行い（または既存の接続を再利用し）、テキストデータを送信します。

入力:

1. リモートサーバー URL
2. データ

## Close Remote Server Connection

リクエスト ID を指定して 1 つの接続を閉じます。

入力:

- 接続リクエスト ID

## Close All Remote Server Connections

現在アクティブなすべてのリモートサーバー接続を閉じます。

# リスナー

## On Remote Server Connected

リモートサーバー接続が初期化されたときにトリガーされます。

変数:

- `$$request_id`
- `$$remote_server_url`

## On Remote Server Data Received

接続済みのリモートサーバーからデータを受信したときにトリガーされます。

変数:

- `$$request_id`
- `$$remote_server_url`
- `$$data`

## On Remote Server Connection Closed

リモートサーバー接続が閉じられたときにトリガーされます。

変数:

- `$$request_id`
- `$$remote_server_url`
- `$$intentionally_closed`
- `$$crashed`
- `$$unknown_close_reason`

# 接続の動作

- 接続は **クライアント主導** です
- FancyMenu はバックグラウンドで接続を維持します
- 接続がクラッシュまたはタイムアウトした場合、FancyMenu は 10 秒ごとに再試行します
- クラッシュした接続が復旧すると、FancyMenu は復旧メッセージをログに記録します
- 送信されていないアウトゴーイングメッセージは **最大保持時間 30 秒** でキューに入れられます
- 30 秒を超えたキュー済みメッセージは破棄されます

# URL モード

- `wss://` = セキュア（TLS）、推奨
- `ws://` = 暗号化なし、ローカルテストに便利

ローカル URL の例:

- `ws://127.0.0.1:8765`

# ベストプラクティス

1. バックエンドサービスごとに、安定した URL を 1 つ使います。
2. 各ユースケースでペイロード形式を一貫させます。
3. 接続が閉じた／クラッシュした場合に備えて、フォールバック UI ロジックを用意します。
4. フローが完了したら、close アクションで接続を閉じます。
5. 本番環境では `wss://` を使用します。
