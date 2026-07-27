---
title: リソース
description: FancyMenu におけるリソースの仕組み。リソースの場所、ローカルリソース、Web リソースについて説明します。
---

# リソース

リソースフィールドは、次の場所からコンテンツを読み込めます。

- **Minecraft:** Minecraft またはリソースパックによって提供されるリソースロケーション。
- **ローカル:** アクティブなゲームインスタンス内のファイル。
- **Web:** 直接指定したファイル URL。

多くの画像、音声、動画、テキストの各フィールドは、同じリソース選択画面を使用します。この選択画面には、Minecraft およびリソースパックのコンテンツを参照するブラウザが含まれています。

# Minecraft リソース（リソースパック）

リソースロケーションは `namespace:path` 形式を使用します。namespace は `assets` の直下にあるディレクトリで、path はその namespace の下にあるすべてです。

たとえば、`/assets/custom_resources/images/image.png` に保存されたリソースパックの画像を考えます。
そのリソースロケーションは `custom_resources:images/image.png` です。

> [!NOTE]
> Minecraft の組み込みリソースは通常 `minecraft` namespace を使用します。

# ローカルリソース

ローカルリソースは `<game-directory>/config/fancymenu/assets/` に保存します。`<game-directory>` はアクティブなインスタンスフォルダであり、`.minecraft` とは異なる場合があります。

リソースフィールドでは、同じパスが `/config/fancymenu/assets/example.png` のように表示されることがあります。これらのフィールドで先頭の `/` は依然として `<game-directory>` を意味し、ファイルシステムのルートパスではありません。

これらのファイルは、[modpack](./modpacks) の config フォルダを通じて同梱できます。

FancyMenu のレイアウト、リソース、設定、生成状態のパスを完全に把握するには、[データ保存場所](./data-storage-locations) を参照してください。

# Web リソース

ファイルへの直接 URL を使用してください。たとえば `https://example-domain.net/image.png` です。ページ URL やリダイレクトリンクは、リソースのファイル名と拡張子で終わる直接 URL よりも遅く、失敗しやすくなります。

# リソースソース内のプレースホルダー

選択画面付きのリソースフィールドでは、ローカルパス、URL、Minecraft のリソースロケーションに [プレースホルダー](./placeholders) を使用できます。ソースフィールドの横にある **エディターで開く** を選択すると、直接編集できます。

> [!WARNING]
> 通常の選択画面を使用しないリソース入力では、プレースホルダーやライブのソース更新がサポートされない場合があります。
