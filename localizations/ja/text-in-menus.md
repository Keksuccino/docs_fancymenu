---
title: メニュー内のテキスト
description: Text要素とTooltip要素を使ってメニューにテキストを表示する方法と、スタイルやスクロールの設定方法を説明します。
sourceBlobSha: 557734a5ca4e53d75045d7086642e9c561805b29
---
# メニュー内のテキスト

FancyMenuには、テキストを表示する要素が2種類あります。

- **Text**：メニュー内にテキストを表示します。1行のテキストから、変更履歴やルール、ニュースのようなスクロール可能な長文まで表示できます。
- **Tooltip**：固定位置またはマウスの横にテキストボックスを表示します。たとえば、ボタンにマウスを重ねたときに表示できます。

どちらも[Markdown](/text-formatting)と[プレースホルダー](/placeholders)に対応しており、見た目やスタイルの設定も共通です。

<img width="800" alt="Text要素の編集" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/text_editor_showcase.gif?raw=true">

> [!TIP]
> このページでは、各要素とその設定について説明します。見出し、リスト、リンク、色など、テキストに記述できる内容については、[テキストの書式設定](/text-formatting)を参照してください。

# テキストの追加

1. レイアウトエディターでレイアウトを開きます。
2. エディターの背景を右クリックし、**New Element -> Text**を選択します。
3. 新しい要素を右クリックし、**Text Content**を選択します。
4. テキストを入力して、**Done**をクリックします。

# テキストの内容

## ソースモード

要素を右クリックして、**Source Mode**を設定します。

- **Direct**：テキストエディターに自分でテキストを入力します。
- **Resource**：テキストファイルから内容を読み込みます。**Text Source**をクリックして、`<game-directory>/config/fancymenu/assets/`内のローカルファイル、Web URL、またはリソースパック内のファイルを選択します。[リソース](/resources)を参照してください。

Webソースを使うと、MODパックを更新しなくても常に最新の変更履歴やニュースを表示できるため便利です。

FancyMenuは、ゲームを終了するまでファイルやWebソースのテキストを記憶します。再読み込みするには、**menu bar -> Customization -> Reload FancyMenu**からFancyMenuを再読み込みしてください。

## 動的なテキスト

[プレースホルダー](/placeholders)を使うと、たとえば`Welcome, {"placeholder":"playername"}!`のように、変化する値をテキストに表示できます。[変数](/variables)の値も表示できます。これらの値が変わると、テキストも自動的に更新されます。

## テキストエディター

**Text Content**をクリックすると、テキストエディターが開きます。右上の**Placeholders**をクリックすると、利用可能なプレースホルダーを参照して、テキストに追加できます。

### 書式設定のショートカット

Text要素とTooltip要素のテキストエディターには、よく使う書式設定のショートカットがあります。macOSでは、`Ctrl`の代わりに`Cmd`を使ってください。

| ショートカット | 動作 |
|---|---|
| `Ctrl + B` | 太字 |
| `Ctrl + I` | 斜体 |
| `Ctrl + U` | 下線 |
| `Ctrl + L` | 左揃え |
| `Ctrl + E` | 中央揃え |
| `Ctrl + R` | 右揃え |

- 書式を設定するには、まずテキストを選択します。同じショートカットをもう一度押すと、書式が解除されます。
- テキストを選択せずにショートカットを押すと、書式用の記号が挿入され、その間にカーソルが置かれます。そのまま入力を続けられます。
- 配置のショートカットは、選択した行、またはカーソルがある行に適用されます。すでにその配置になっている行で`Ctrl + E`または`Ctrl + R`を押すと、左揃えに戻ります。
- エディター内を右クリックして**Formatting**を開くと、これらの操作をメニューから選べます。

### その他のショートカット

FancyMenuの多くのテキスト入力欄（アクションの値や各種要素の設定など）では、同じテキストエディターが開きます。以下のショートカットは、どの入力欄でも使えます。macOSでは、`Ctrl`の代わりに`Cmd`を使ってください。

| ショートカット | 動作 |
|---|---|
| `Ctrl + C` | 選択したテキストをコピー |
| `Ctrl + X` | 選択したテキストを切り取り |
| `Ctrl + V` | 貼り付け |
| `Ctrl + A` | すべてのテキストを選択 |
| `Ctrl + Z` | 元に戻す |
| `Ctrl + Y` | やり直す |
| `Ctrl + D` | カーソルがある行を複製 |
| `Alt + Arrow Up` / `Alt + Arrow Down` | カーソルがある行を上下に移動 |
| `Shift + Arrow keys` | テキストを選択 |
| `Ctrl + Home` / `Ctrl + End` | テキストの先頭または末尾に移動 |
| `Ctrl + G` | 行へ移動：行番号を入力して`Enter`を押します |
| `Ctrl + S` | **Done**と同じ動作 |

レイアウトエディターのショートカットについては、[レイアウトエディター](/layout-editor#shortcuts)を参照してください。

# 見た目とスタイル

要素を右クリックして**Markdown**を開くと、テキストの見た目を変更できます。

## 外観

**Look**を選ぶと、テキストのスタイル設定をまとめて適用できます。

- **Pixel**：Minecraftのフォントに合わせたピクセルアート風の見た目です。暖色、金色の装飾、手描き風のマーカーが使われます。
- **Classic**：FancyMenuのクラシックな見た目です。白いテキスト、グレーのボックス、グレーの線が使われます。
- **Neutral**：現在のFancyMenu UIテーマの色を使った、すっきりとした見た目です。色は要素と一緒に保存されるため、後でテーマを切り替えても変わりません。

<img width="800" alt="3種類のMarkdownの外観" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/markdown_looks.png?raw=true">

新しい要素にはPixelの外観が適用されます。古いレイアウトの要素には、これまでどおりClassicの外観が適用されます。

> [!NOTE]
> 外観を選ぶと、独自に変更したスタイルは置き換わります。選び直したい場合は、`Ctrl + Z`で元に戻せます。

## スタイルの設定

外観を選んだ後も、各項目を細かく調整できます。**Markdown**メニューには、**Text**、**Headlines**、**Lists**、**Links**、**Code**、**Quotes**、**Callouts**、**Tables**、**Images**、**Separators**の設定があります。項目にマウスを重ねると、各設定の説明が表示されます。

**Markdown -> Text**では、文字色、文字の影、行間、テキストと要素の端との間隔など、基本的な設定ができます。

## Markdownを無効にする

Markdownが不要な場合は、**Markdown -> Markdown Parser**をオフにしてください。入力したテキストがそのまま表示されます。また、非常に長いテキストの場合は、少し処理が速くなります。

## その他のテキスト設定

要素を右クリックすると、次の設定も見つかります。

- **Text Scale**：テキストを拡大または縮小します。
- **Case Mode**：テキストを通常、大文字のみ、小文字のみで表示します。
- **Auto Line Wrapping**：要素に収まらない長い行を折り返します。オフにすると、長い行はそのまま続きます。
- **Remove HTML Line Breaks**：テキストからHTMLの改行（`<br>`）を削除します。Webサイトから取得したテキストに便利です。

# 背景

Text要素では、テキストの背後にパネルを表示できます。要素を右クリックして、**Background**を開きます。

- **Show Background**：パネルの表示・非表示を切り替えます。新しいText要素ではオンになっています。
- デフォルトでは、組み込みの暗いパネルが使われます。独自のテクスチャを使うこともでき、[9スライス](/nine-slicing-and-tiling)やタイル表示を利用して、端の形を保てます。
- **Padding**：背景をテキストの外側にどれだけ広げるかを設定します。
- **Reach Behind Scroll Bars**：背景をスクロールバーの背後まで表示します。オフにすると、スクロールバーは背景のすぐ横に配置されます。

Tooltipには専用の**Background**メニューがあり、テクスチャと9スライスを設定できます。

# スクロール

Text要素では、テキストが要素に収まらない場合にスクロールできます。マウスホイールでスクロールします。`Shift`を押しながら操作すると、横にスクロールできます。

**Scroll Direction**では、テキストのスクロール方向を**Vertical**、**Horizontal**、**Both**から選びます。スクロールしない方向で収まりきらない内容は、表示されずに切り取られます。

## スクロール設定

要素を右クリックして**Scrolling**を開きます。

| 設定 | 動作 |
|---|---|
| **Let Players Scroll** | プレイヤーが自分でテキストをスクロールできるかを設定します。オフにすると、テキストは自動スクロールまたはアクションによってのみスクロールします。 |
| **Scroll Speed** | マウスホイールを1段階動かしたときのスクロール量を設定します。 |
| **Smooth Scrolling** | スクロールを段階的に移動させず、滑らかに動かします。 |
| **Drag to Scroll** | タッチスクリーンのように、マウスでテキストをつかんでドラッグできるようにします。 |
| **Scroll with Keyboard** | テキストの上にマウスがあるとき、`Page Up`と`Page Down`で1ページ分スクロールし、`Home`と`End`で先頭または末尾に移動できるようにします。 |
| **Snap** | スクロールの停止位置を設定します。どこでも停止する（**Off**）、行の先頭に合わせる（**To Lines**）、見出しの先頭に合わせる（**To Headlines**）、ページ単位にする（**To Pages**）から選べます。 |
| **Start At** | テキストの開始位置を**Start**または**End**に設定します。ログのように新しい内容が末尾に追加される場合は、Endが便利です。 |
| **Reset When Screen Opens** | 画面を開くたびに、テキストを先頭に戻します。オフにすると、ゲームを終了するまでスクロール位置が記憶されます。 |

## 自動スクロール

**Auto-Scroll**を開くと、クレジットやニュースティッカーのように、テキストをゆっくり自動でスクロールできます。

- **Scroll on Its Own**：自動スクロールを有効にします。
- **Speed [Pixels per Second]**：スクロール速度を設定します。
- **Start Over at the End**：末尾に到達したとき、先頭から再開します。
- **Pause While Hovered**：マウスがテキストの上にある間はスクロールを停止し、プレイヤーが落ち着いて読めるようにします。

## スクロールバー

**Scroll Bars**を開くと、スクロールバーを変更できます。

- **Show**：スクロールバーを表示するタイミングを設定します。**Always**、**While Scrolling**のみ、または**Never**から選べます。**Never**にしても、マウスホイールでスクロールできます。
- **Thickness**：スクロールバーの太さを設定します。
- **Vertical Bar on the Left**と**Horizontal Bar on Top**：スクロールバーを反対側に移動します。
- **Scroll Grabber Style**：つまみの見た目を選びます。FancyMenu UIテーマの色を使う**Theme Bar**、またはPixelの外観によく合うピクセルアートの**Pixel Handle**から選べます。
- **Scroll Grabber Textures**と**Scroll Grabber Color [HEX]**：つまみを独自のテクスチャや色に置き換えます。
- **Scroll Bar Backgrounds**：つまみの移動範囲に沿って、背後にテクスチャを追加します。

## アクションによるスクロール

FancyMenuの他の機能から、スクロールを操作したり状態を確認したりすることもできます。

- **Scroll an Element**[アクション](/action-scripts)を使うと、Text要素を先頭、末尾、指定位置、指定行、または指定したテキストを含む最初の行へスクロールできます。
- **Element Scroll Position**、**Element Scroll Percent**、**Element Scroll Content Size**[プレースホルダー](/placeholders)を使うと、テキストのスクロール位置やサイズを取得できます。
- **Is Element Scrolled to End**[条件](/conditions)を使うと、テキストが末尾までスクロールされたかを確認できます。たとえば、ルールを読んだ後にのみ「Accept」ボタンを有効にできます。
- **On Element Scrolled**、**On Element Scrolled to Start**、**On Element Scrolled to End**[リスナー](/listeners)を使うと、テキストのスクロール中にアクションを実行できます。

これらの機能を使うには、Text要素の[要素識別子](/element-identifiers)が必要です。

# Text要素の背後にある要素をクリックする

Text要素はマウス操作に反応するため、リンクやスクロールバーを使えます。一方で、クリックを受け取るため、Text要素の背後や前面にあるボタンがクリックを受け取れない場合があります。

問題がある場合は、Text要素を右クリックして**Interactable**をオフにしてください。テキストをスクロールできなくなり、リンクもクリックできなくなります。

# Tooltip

Tooltip要素はスクロール機能がない点を除き、Text要素と同じように動作します。

- テキスト、外観、スタイルの設定はText要素と共通です。
- **Follow Mouse**を有効にすると、Tooltipがマウスに追従します。
- [条件](/conditions)を使うと、Tooltipを表示するタイミングを決められます。たとえば、ボタンにマウスを重ねたときに表示するには、[**Is Element Hovered**](/conditions#is-element-hovered)条件を使います。
