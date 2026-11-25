---
title: リソース
description: FancyMenuでのリソースの仕組みについて説明します。リソースの場所、ローカルリソース、Webリソースを扱います。
sourceBlobSha: eb783aaa0098ba295b3ebaf941bb4723e4d08970
---

# リソース

リソースフィールドでは、次の場所からコンテンツを読み込めます。

- **Minecraft:** Minecraftまたはリソースパックが提供するリソースロケーション。
- **ローカル:** 現在のゲームインスタンス内にあるファイル。
- **Web:** ファイルへの直接URL。

画像、音声、動画、テキストの各フィールドの多くは、同じリソース選択画面を使用します。この選択画面には、Minecraftとリソースパックのコンテンツを参照するブラウザーが含まれています。

# Minecraftのリソース（リソースパック）

リソースロケーションは `namespace:path` の形式です。namespaceは `assets` の直下にあるディレクトリで、pathはそのnamespace以下のすべてのパスを指します。

たとえば、リソースパックの画像が `/assets/custom_resources/images/image.png` に保存されているとします。
リソースロケーションは `custom_resources:images/image.png` です。

> [!NOTE]
> Minecraft標準のリソースでは、通常 `minecraft` namespaceが使われます。

# ローカルリソース

ローカルリソースは `<game-directory>/config/fancymenu/assets/` に保存します。`<game-directory>` は現在のインスタンスフォルダーで、`.minecraft` とは異なる場合があります。

リソースフィールドでは、同じパスが `/config/fancymenu/assets/example.png` のように表示されることがあります。この場合、先頭の `/` は引き続き `<game-directory>` を意味し、ファイルシステムのルートパスではありません。

これらのファイルは、設定フォルダーを通じて[Modパックに同梱](/modpacks)できます。

FancyMenuのレイアウト、リソース、設定、生成状態の各パスの全体像については、[データの保存場所](/data-storage-locations)を参照してください。

# Webリソース

ファイルへの直接URLを使用します。例: `https://example-domain.net/image.png`。ページURLやリダイレクトURLは、リソースのファイル名と拡張子で終わる直接URLよりも読み込みが遅く、失敗しやすくなります。

# リソースソースのプレースホルダー

リソース選択画面を使用するフィールドでは、ローカルパス、URL、Minecraftのリソースロケーションに[プレースホルダー](/placeholders)を使用できます。ソースフィールドの横にある **エディターで開く** を選択すると、直接編集できます。

> [!WARNING]
> 通常のリソース選択画面を使用しない入力欄では、プレースホルダーやソースのライブ更新がサポートされない場合があります。
