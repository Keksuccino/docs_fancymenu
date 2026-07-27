---
title: レイアウトのローカライズ
description: テキストやその他のレイアウト内容をローカライズします。
---

# レイアウトのローカライズ

翻訳可能なテキストには、[**テキストをローカライズ** プレースホルダー](./placeholders#localize-text-local) を使用します:

```text
{"placeholder":"local","values":{"key":"modpack.menu.play"}}
```

FancyMenu はまず Minecraft の現在有効な言語データを確認します。キーがそこに存在しない場合は、FancyMenu のカスタムローカライズファイルを確認します。どちらにもキーが含まれていない場合は、キー自体が表示されます。

# FancyMenu のカスタムローカライズファイル

ファイルは次の場所に配置します:

```text
<game-directory>/config/fancymenu/custom_locals/
```

ローカライズファイル用のサブディレクトリを作成します:

```text
custom_locals/
└── my_pack/
    └── text.json
```

ローカライズファイルは `custom_locals` の少なくとも 1 つのサブディレクトリ内に配置してください。`custom_locals` のルート直下に置かれたファイルは読み込まれません。ネストしたサブディレクトリもサポートされています。

サポートされる UTF-8 形式:

| 拡張子 | 形式 |
|---|---|
| `.json` | JSON オブジェクト。入れ子のオブジェクトはドット区切りのキーになります |
| `.lang` | `key=value` 形式の行 |
| `.properties` | Java の properties 構文 |

JSON の例:

```json
{
  "modpack": {
    "menu": {
      "play": "Play"
    }
  }
}
```

これは `modpack.menu.play` を定義します。

FancyMenu は、これらのサブディレクトリ内にある対応形式のファイルを 1 つのカスタムローカライズ辞書にまとめます。各キーは 1 つのファイルにのみ含めてください。カスタムローカライズファイルは Minecraft で選択されている言語に応じて切り替わりません。自動的な言語切り替えが必要な場合は、以下のリソースパック方式を使用してください。

カスタムローカライズファイルを編集した後は、クライアントを再起動してください。

# 言語別テキスト

Minecraft の選択言語に応じて自動的に切り替えるには、[リソースパック](./resources#minecraft-resources-resource-packs) を通じて通常の Minecraft 言語ファイルを用意します:

```text
assets/<namespace>/lang/en_us.json
assets/<namespace>/lang/de_de.json
```

各言語ファイルで同じキーを使用し、リソースパックを有効にしてから、[**テキストをローカライズ** プレースホルダー](./placeholders#localize-text-local) で読み取ります。

# 画像と要素のローカライズ

[**ゲームの言語かどうか** 要件](./conditions#is-game-language-fancymenu_loading_requirement_is_language) を使用して、`en_us` や `de_de` などの言語コードごとに異なる要素やレイアウトを表示します。
