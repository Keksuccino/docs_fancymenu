---
title: テキストの書式設定
description: Markdown と Minecraft の書式コードを使ってテキストを整形する方法。
---

# テキストの書式設定

FancyMenu には、レイアウト内のテキストをもっと *おしゃれ* にするための機能がたくさんあります！

テキスト要素は充実した **Markdown** に対応しており、さらに便利な拡張機能もあります。また、ほとんどの他のテキスト内容は **Minecraft のテキスト書式** システムに対応しています。ボタンラベルは **Minecraft のテキストコンポーネント** にも対応しているので、カスタムフォントなども使えます。

# Markdown

FancyMenu の **Text 要素** は Markdown に完全対応しているため、特殊な記号を追加することでテキストを装飾できます。

たとえば、太字にしたい場合は、太字にしたい文字列の前後に `**` を追加します。すると `**Some bold text that's very bold.**` は次のように表示されます:
**Some bold text that's very bold.**

FancyMenu の Markdown には、さらに強力にするための特別な機能もあります！

> Markdown は、ボタンラベルのような他のテキストベースのものでは **動作しません**。これは **TEXT 要素** にのみ適用されます。それ以外では、[Minecraft の書式コード](/text-formatting#minecraft-text-formatting) を使用してください。
{.is-danger}

## フォント

`%!!<font_name>%` をテキストの前に、`%!!%` を後ろに付けることで、リソースパック経由で読み込まれたカスタムフォントでテキストを表示できます。

基本ゲームに含まれている有効なフォントは `uniform` です。`uniform` フォントでテキストを表示するには、次のようにします:
`%!!uniform%this is a custom font%!!%`

これにより、`this is a custom font` が `uniform` フォントで表示されます。

## テキストカラー（HEX）

`%<HEX_color>%` をテキストの前に、`%#%` を後ろに付けることで、特定の HEX カラーでテキストを表示できます。

緑色の有効な HEX カラーは `#77fc03` なので、この色で表示するには次のようにします:
`%#77fc03%this text is green!%#%`

これにより、`this text is green!` が `#77fc03`（緑）で表示されます。

HEX カラーは必ず `#` から始めてください！

FancyMenu 3.9.0 では、この同じ色指定コードで一般的な HTML 風の色名もサポートされています:

```
%#red%This text is red!%#%
```

対応している名前: `black`, `silver`, `gray`, `grey`, `white`, `maroon`, `red`, `purple`, `fuchsia`, `magenta`, `green`, `lime`, `olive`, `yellow`, `navy`, `blue`, `teal`, `aqua`, `cyan`, `transparent`。

## テキストの配置

テキスト行の先頭に特定の配置用書式コードを置き、その後に何も書かず、表示したいテキスト行を続け、最後に別の行で同じ配置コードをもう一度書くことで、テキストを揃えられます。

すべてのテキスト内容は **左寄せがデフォルト** なので、書式コードは **中央揃え** と **右寄せ** のみがあります。

### 中央揃え

テキスト行を中央揃えにするには、書式コード `^^^` を使います。

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

テキスト行を右寄せで表示するには、書式コード `|||` を使います。

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

クリックするとウェブサイトを開くハイパーリンクをテキスト内容に追加できます。

[hyperlink](https://google.com) のように表示したいテキストは `[ ]` で囲み、その後に実際のリンクを `( )` で囲みます。

たとえば、`example text content` をクリック可能にして `https://example-website.net` を開くようにするには、次のようにします:
`[example text content](https://example-website.net)`

## クリックイベントとホバーイベント

FancyMenu 3.9.0 では、Text 要素やその他の Markdown テキストに対して Markdown のクリックイベントとホバーイベントが追加されました。

クリックイベントでは `click:` プレフィックスを使います:

```
[some clickable text](click:unique_text_click_event_id)
```

ホバーイベントでは `hover:` プレフィックスを使います:

```
[some hoverable text](hover:unique_text_hover_event_id)
```

これらのイベントに反応するには、**On Markdown Text Clicked** と **On Markdown Text Hovered** リスナーを使います。どちらのリスナーでも、イベント ID は `$$text_event_id` として公開されます。

## 画像

Markdown では、テキスト内容の中に画像を表示できます。

FancyMenu の Markdown では、Minecraft のリソース、ローカルリソース、Web リソースがサポートされています。

画像を追加するには、テキスト行を `![](` で始め、その後に [URL、リソースロケーション、またはリソースへのパス](/resources) を書き、最後に `)` を付けます。

たとえば Web リソース `https://example-website.net/image.png` を表示するには、次のようにします:
`![](https://example-website.net/image.png)`

画像は、画像全体のテキスト行を次のような **ハイパーリンク** で囲むことで、**リンク** にすることもできます:
`[![](https://example-website.net/image.png)](https://example-website.net)`

> ローカルリソースは `/config/fancymenu/assets/` に置く必要があります！
{.is-warning}

## 引用

テキストを引用として整形するには、テキスト行の先頭に `> ` を付けます。
これ以降の行は、**空** の行が見つかるまで引用として整形されます。

例:
```
This will not look like a quote.

> This will look like a quote.
This will also look like a quote.

This will not look like a quote anymore.
```

## 箇条書き

次のような箇条書きとしてテキストを表示するには:
- Entry 1
- Entry 2
  - Sub-Entry

行の先頭に `- ` を付けるだけです。

例:
```
- Entry 1
- Entry 2
  - Sub-Entry
```

## 区切り線

テキスト行全体の幅を持つ区切り線を追加するには、行の先頭に `---` を付け、それ以外は何も書きません。

すると次のようになります:

---

## コードブロック

コードブロックを使うと、Markdown による整形を行わずに `プレーンテキスト` を表示したり、テキスト行を自動折り返しせずにコード風の見た目で表示したりできます。

1 行のコードブロック（他のテキストの中にあるもの）は、\` で始まり \` で終わります。Markdown テキストでこれを示すのは実はかなり難しいです。

1 行のコードブロックを含むテキスト行は、次のようになります:

![single_line_code_block](https://github.com/Keksuccino/FancyMenu/assets/35544624/e78fd38b-7b1a-4f00-9b11-797d964b3b43)

複数行コードブロックは、複数行を 1 つの大きなコードブロックとしてまとめ、`\`\`\`` のみを含む行で始め、その後にテキスト内容を書き、再度 `\`\`\`` で終わります:

![multi_line_code_block](https://github.com/Keksuccino/FancyMenu/assets/35544624/bf8c77eb-a97e-48cd-9270-8302c2995856) 

## プレーンテキスト

プレーンテキストの書式コードは、その内部にある他のすべての書式コードを無効化して通過させます。

これはコードブロックに似ていますが、コードブロックのような見た目にはなりません。代わりに通常のテキストとして表示されますが、書式は適用されません。

行の中のテキストの一部をプレーンテキストの書式コードで囲むには、プレーンテキストとして表示したい部分の前後に `;;` を追加します。たとえば次のようになります:

```
This is a line of text with ;;**this part**;; showing as unformatted text with visible ** (bold) formatting code and _this part_ as normal formatted italic text.
```

プレーンテキストは複数行のラッパーコードとしても機能します。行全体を囲むには、プレーンテキストとして表示したい行の前後に `;;;` を追加します。たとえば次のようになります:

```
;;;
This line will show **unformatted** with visible ** (bold) formatting codes.
This line will also show _unformatted_ with visible _ (italic) formatting codes.
;;;

This line will look **normal** again with the "normal" formatted as bold text.
```

# Minecraft のテキスト書式

Minecraft には、Markdown に似たかなり優れた書式システムがあり、テキストに特殊な文字を追加して整形できます。

Minecraft の書式システムについて詳しく知りたい場合は、[この Minecraft wiki ページ](https://minecraft.wiki/w/Formatting_codes) をご覧ください。

> wiki では書式コードの接頭辞が `§` と説明されていますが、FancyMenu ではこれを `&` に置き換える必要があります。それ以外は同じです。
{.is-warning}

> **Text 要素** は非常に複雑で、Markdown をサポートするために、代償として **Minecraft のバニラ書式コードが壊れる** 仕様になっています。そのため、Text 要素ではこれらのコードはうまく動作しません（書式コードの後の最初の単語だけが書式設定される、など）。代わりに Text 要素では Markdown の書式コードを使用してください。
{.is-danger}

# Minecraft のテキストコンポーネント（生コンポーネントシステム）

Minecraft のテキストコンポーネントシステムは、**1 行** のテキスト内容、たとえば **ボタンラベル** にはとても強力です。

バニラ Minecraft では、`/tellraw` や `/title` コマンド（おそらく他の場所でも）で使用できます。
これは JSON にシリアライズされた書式付きテキストなので、テキスト内容に書式属性を追加できます。

テキストコンポーネントについて詳しく知りたい場合は、[この Minecraft wiki ページ](https://minecraft.wiki/w/Raw_JSON_text_format) をご覧ください。
Minecraft のフォントについて詳しく知りたい場合は、[この Minecraft wiki ページ](https://minecraft.wiki/w/Resource_pack#Fonts) をご覧ください。

FancyMenu にボタンラベルを **テキストコンポーネント** として認識させるには、シリアライズされたコンポーネントテキストだけをラベルとして設定します。たとえば次のようにします:
`{"text":"Button Label Text","font":"uniform"}`

上の例では、ボタンラベル `Button Label Text` が `uniform` フォントで表示されます。

> コンポーネントの `text` 値には、FancyMenu のプレースホルダーを使用できます。
{.is-info}
