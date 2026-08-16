---
title: テキストの書式設定
description: Markdown と Minecraft の書式コードを使ってテキストを整形する方法。
---
# テキストの書式設定

[テキスト要素](./elements#text) は Markdown をサポートしています。その他のテキスト欄では Minecraft の書式設定を使用し、ボタンラベルには Minecraft のテキストコンポーネントを使えます。

# Markdown

FancyMenu の **テキスト要素** は完全な Markdown に対応しており、特別な文字を追加することでテキスト内容を整形できます。

たとえば、文字を太字にしたい場合は太字にしたいテキストの前後に `**` を追加します。すると `**Some bold text that's very bold.**` は次のように表示されます:
**Some bold text that's very bold.**

FancyMenu は下記に記載する拡張機能にも対応しています。

> [!CAUTION]
> Markdown は **テキスト要素** のみで動作します。ボタンラベルやその他のテキスト欄では、[Minecraft の書式コード](#minecraft-text-formatting) を使用してください。

## フォント

テキストの前に `%!!<font_name>%` を、後ろに `%!!%` を追加すると、リソースパックで読み込まれたカスタムフォントでテキストを表示できます。

ベースゲームに含まれる有効なフォントは `uniform` です。`uniform` フォントでテキストを表示するには、次のようにします:
`%!!uniform%this is a custom font%!!%`

これにより `this is a custom font` が `uniform` フォントで表示されます。

## テキスト色（HEX）

テキストの前に `%<HEX_color>%` を、後ろに `%#%` を追加すると、特定の HEX 色で表示できます。

緑の有効な HEX 色は `#77fc03` です。この色で表示するには、次のようにします:
`%#77fc03%this text is green!%#%`

これにより `this text is green!` が `#77fc03`（緑）で表示されます。

HEX 色は `#` で始める必要があります。

一般的な HTML 風の色名も同じ色指定コードでサポートされています:

```
%#red%This text is red!%#%
```

対応している名前: `black`, `silver`, `gray`, `grey`, `white`, `maroon`, `red`, `purple`, `fuchsia`, `magenta`, `green`, `lime`, `olive`, `yellow`, `navy`, `blue`, `teal`, `aqua`, `cyan`, `transparent`。

## テキストの配置

特定の配置用書式コードで行を開始し、その後に何も置かず、表示したいテキスト行をその配置で続けたあと、空の行にもう一度その配置コードを書いて閉じることで、テキスト行を配置できます。

すべてのテキスト内容は **左寄せがデフォルト** なので、書式コードは **中央寄せ** と **右寄せ** だけがあります。

### 中央寄せ

テキスト行を中央寄せにするには、書式コード `^^^` を使用します。

例:
```
This text is not centered.

^^^
This text is centered.
This text is also centered.
^^^

This text is not centered anymore.
```

### 右寄せ

テキスト行を右寄せで表示するには、書式コード `|||` を使用します。

例:
```
This text is not right-aligned.

|||
This text is right-aligned.
This text is also right-aligned.
|||

This text is not right-aligned anymore.
```

## 見出し

**1 行のテキスト** を見出し（大きく、下線付き）として表示するには、テキスト行の前に `# `（とても大きい）、`## `（大きい）、または `### `（小さい）を追加します。

例:
`## Big Headline`

## 太字

テキストの前後に `**` を追加すると、**太字** になります。

例:
`**bold text content**`

## 斜体

テキストの前後に `_` または `*` を追加すると、*斜体* になります。

例:
`*italic text content*`

## 打ち消し線

テキストの前後に `~` を追加すると、~~打ち消し線~~ になります。

例:
`~strikethrough text content~`

## ハイパーリンク

クリックするとウェブサイトを開くリンクをテキスト内容に追加できます。

[ハイパーリンク](https://google.com) として表示したいテキストは `[ ]` で囲み、その後に実際のリンクを `( )` で囲みます。

たとえば、`example text content` をクリック可能にして `https://example-website.net` を開かせたい場合は、次のようにします:
`[example text content](https://example-website.net)`

## クリックイベントとホバーイベント

Markdown のクリックイベントとホバーイベントは、[テキスト要素](./elements#text) および他の Markdown テキストで利用できます。これらに反応するには [**Markdown テキストがクリックされたとき**](./listeners#on-markdown-text-clicked-text_clicked) と [**Markdown テキストがホバーされたとき**](./listeners#on-markdown-text-hovered-text_hovered) を使用してください。

クリックイベントは `click:` プレフィックスを使用します:

```
[some clickable text](click:unique_text_click_event_id)
```

ホバーイベントは `hover:` プレフィックスを使用します:

```
[some hoverable text](hover:unique_text_hover_event_id)
```

どちらのリスナーでも、イベント ID は `$$text_event_id` として公開されます。

## 画像

Markdown では、テキスト内容内に画像を表示できます。

FancyMenu は Markdown 内で Minecraft リソース、ローカルリソース、ウェブリソースをサポートしています。

画像を追加するには、テキスト行を `![](` で始め、その後に [URL、リソースの場所、またはパス](./resources) を書き、最後に `)` を付けます。

たとえば、ウェブリソース `https://example-website.net/image.png` を表示するには、次のようにします:
`![](https://example-website.net/image.png)`

画像全体を **ハイパーリンク** で囲むことで、画像を **リンク** にすることもできます:
`[![](https://example-website.net/image.png)](https://example-website.net)`

> [!WARNING]
> ローカルリソースは `<game-directory>/config/fancymenu/assets/` に配置する必要があります!

## 引用

テキストを引用として整形するには、テキスト行を `> ` で始めます。
これは、**空の** 行が見つかるまで、その後のすべての行を引用として整形します。

例:
```
This will not look like a quote.

> This will look like a quote.
This will also look like a quote.

This will not look like a quote anymore.
```

## 箇条書きリスト

次のような箇条書きリストを表示するには:
- Entry 1
- Entry 2
  - Sub-Entry

各行の先頭に `- ` を付けるだけです。

例:
```
- Entry 1
- Entry 2
  - Sub-Entry
```

## 区切り線

テキスト行全体の幅を持つ区切り線を追加するには、行の先頭に `---` を置き、それ以外は何も書きません。

すると、次のように表示されます:

---

## コードブロック

コードブロックを使うと、Markdown による整形を避けて `プレーンテキスト` として表示したり、テキストをコード風に表示したりできます。なお、テキスト行の自動折り返しはされません。

1 行コードブロック（他のテキストの途中にあるもの）は、開始と終了に \` を使います。Markdown テキストでは、これは実際にはかなり表示しにくいです。

1 行コードブロックを含むテキスト行は、次のように表示されます:

![single_line_code_block](https://github.com/Keksuccino/FancyMenu/assets/35544624/e78fd38b-7b1a-4f00-9b11-797d964b3b43)

複数行コードブロックは、複数行を 1 つの大きなコードブロックにまとめます。`\`\`\`` のみを含む行で始め、その後にテキスト内容を書き、最後にもう一度 `\`\`\`` を置きます:

![multi_line_code_block](https://github.com/Keksuccino/FancyMenu/assets/35544624/bf8c77eb-a97e-48cd-9270-8302c2995856) 

## プレーンテキスト

プレーンテキストの書式コードは、その中にある他のすべての書式コードを無視します。

コードブロックに似ていますが、コードブロックのような見た目にはなりません。代わりに通常のテキストとして表示されますが、書式は適用されません。

行の一部をプレーンテキストの書式コードで囲むには、次のように表示したいテキスト部分の前後に `;;` を追加します:

```
This is a line of text with ;;**this part**;; showing as unformatted text with visible ** (bold) formatting code and _this part_ as normal formatted italic text.
```

プレーンテキストは複数行のラッパーコードとしても機能します。行全体を囲むには、次のように表示したい行の前後に `;;;` を追加します:

```
;;;
This line will show **unformatted** with visible ** (bold) formatting codes.
This line will also show _unformatted_ with visible _ (italic) formatting codes.
;;;

This line will look **normal** again with the "normal" formatted as bold text.
```

# Minecraft のテキスト書式設定

Minecraft の書式コードは、FancyMenu 全体の対応した書式付きテキスト欄で使えます。Minecraft の `§` プレフィックスの代わりに `&` を使用してください。たとえば、`&cWarning` は赤いテキストを表示します。

利用可能な色とスタイルについては、[Minecraft Wiki の書式コード参照](https://minecraft.wiki/w/Formatting_codes) をご覧ください。

> [!CAUTION]
> **テキスト要素** では Markdown を解析するため、Minecraft の書式コードは信頼性がありません。代わりに、上記の Markdown 書式を使用してください。

# Minecraft のテキストコンポーネント（生コンポーネントシステム）

Minecraft のテキストコンポーネントシステムは、**ボタンラベル** のような **1 行** のテキスト内容に対して非常に強力です。

バニラ Minecraft では、`/tellraw` や `/title` コマンド（おそらく他の場所でも）で使用できます。
これは JSON にシリアライズされた書式付きテキストなので、テキスト内容に書式属性を追加できます。

テキストコンポーネントの詳細については、[この Minecraft Wiki のページ](https://minecraft.wiki/w/Raw_JSON_text_format) を参照してください。Minecraft のフォントについて詳しく知りたい場合は、[この Minecraft Wiki のページ](https://minecraft.wiki/w/Resource_pack#Fonts) をご覧ください。

FancyMenu にボタンラベルを **テキストコンポーネント** として認識させるには、シリアライズされたコンポーネントテキストだけをラベルとして設定します。次のようにします:
`{"text":"Button Label Text","font":"uniform"}`

上の例では、ボタンラベル `Button Label Text` が `uniform` フォントで表示されます。

> [!NOTE]
> コンポーネントの `text` 値には FancyMenu のプレースホルダーを使用できます。
