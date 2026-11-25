---
title: レイアウトのローカライズ
description: テキストやその他のレイアウトコンテンツをローカライズします。
sourceBlobSha: f4883414b07e0c024de7bef4f131b878ca4f5f37
---

# レイアウトのローカライズ

翻訳可能なテキストには、[**テキストのローカライズ**プレースホルダー](/placeholders#localize-text)を使用します。

```text
{"placeholder":"local","values":{"key":"modpack.menu.play"}}
```

FancyMenu は、まず Minecraft で有効な言語データを確認します。そこにキーがない場合は、FancyMenu のカスタムローカライズファイルを確認します。どちらにもキーが含まれていない場合は、キー自体が表示されます。

# FancyMenu のカスタムローカライズファイル

以下の場所にファイルを配置します。

```text
<game-directory>/config/fancymenu/custom_locals/
```

ローカライズファイル用のサブディレクトリを作成します。

```text
custom_locals/
└── my_pack/
    └── text.json
```

ローカライズファイルは、`custom_locals` 内の少なくとも1つのサブディレクトリに配置してください。`custom_locals` のルートに直接置かれたファイルは読み込まれません。サブディレクトリの階層化にも対応しています。

UTF-8 で、次の形式に対応しています。

| 拡張子 | 形式 |
|---|---|
| `.json` | JSON オブジェクト。ネストされたオブジェクトはドット区切りのキーになります |
| `.lang` | `key=value` 形式の行 |
| `.properties` | Java のプロパティ構文 |

JSON の例：

```json
{
  "modpack": {
    "menu": {
      "play": "Play"
    }
  }
}
```

この例では `modpack.menu.play` が定義されます。

FancyMenu は、これらのサブディレクトリにある対応ファイルを1つのカスタムローカライズ辞書にまとめます。各キーは1つのファイルでのみ使用してください。カスタムローカライズファイルは、Minecraft で選択した言語に応じて切り替わりません。言語の自動切り替えが必要な場合は、以下のリソースパック方式を使用してください。

カスタムローカライズファイルを編集した後は、クライアントを再起動してください。

# 言語ごとのテキスト

Minecraft で選択した言語に応じて自動的に切り替えるには、[リソースパック](/resources#minecraft-resources-resource-packs)を使って、通常の Minecraft 言語ファイルを用意します。

```text
assets/<namespace>/lang/en_us.json
assets/<namespace>/lang/de_de.json
```

各言語ファイルで同じキーを使用し、リソースパックを有効にしてから、[**テキストのローカライズ**プレースホルダー](/placeholders#localize-text)で読み込みます。

# 画像と要素のローカライズ

言語コード（`en_us` や `de_de` など）に応じて異なる要素やレイアウトを表示するには、[**ゲームの言語**条件](/conditions#is-game-language)を使用します。
