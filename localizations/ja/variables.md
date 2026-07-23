---
title: 変数
description: 変数の作成と使用方法。
---
# FancyMenu の変数

変数にはテキスト値を保存できます。レイアウト、アクション、プレースホルダー、要件、リスナー、スケジューラー、カスタム GUI で再利用できます。

## 変数の作成

FancyMenu で変数を作成するには、次の手順を行います。

1. 現在レイアウトエディターを開いていないことを確認します。
2. 画面上部のメニューバーをクリックします。
3. **Customization -> Variables -> Manage Variables** に進みます。
4. 表示された「Manage Variables」画面で、**Add Variable** ボタンをクリックします。
5. 新しい変数の名前を入力し、**OK** をクリックします。

これで完了です。変数を使用できるようになりました。「Manage Variables」画面に一覧表示されます。

「Manage Variables」ウィンドウでは、右クリックのコンテキストメニュー、キーボード操作、コピー/貼り付け、元に戻す/やり直し、検索入力、**Delete** による削除、**Ctrl/Command + S** による保存をサポートしています。

## 変数の値を設定する

空の変数だけではあまり役に立ちません。変数を活用するには、その中にデータを入れる必要があります。FancyMenu では、これを「変数の値を設定する」と呼びます。

変数の値を設定する主な方法は 2 つあります。

1. 「Manage Variables」画面で一覧から変数を見つけてクリックし、**Set Value** をクリックします。保存したいデータを入力します。

2. メニューをカスタマイズしている最中に、[**Set Variable Value** アクション](./action-scripts#set-variable-value-fm-variable-set_variable) を [Button](./elements#button)、[Slider](./elements#slider)、または [Ticker](./elements#ticker) 要素に使用します。

たとえば、`clicks` という名前の変数を作成し、ボタンに [**Set Variable Value** アクション](./action-scripts#set-variable-value-fm-variable-set_variable) を追加します。

```
clicks:{"placeholder":"calc","values":{"expression":"{"placeholder":"getvariable","values":{"name":"clicks"}} + 1"}}
```

この仕組みは次のとおりです。
1. [**Get Stored Variable** プレースホルダー](./placeholders#get-variable-value-fm-variable-getvariable) が `clicks` 変数の現在値を取得します。
2. [**Calculator** プレースホルダー](./placeholders#calculator-calc) がその値に 1 を足します。
3. 結果は [**Set Variable Value** アクション](./action-scripts#set-variable-value-fm-variable-set_variable) を使って `clicks` に保存されます。

そのため、ボタンがクリックされるたびに `clicks` 変数が 1 ずつ増え、クリック数の合計を数えられます。

## 変数の使用

変数にデータを保存したら、そのデータをメニューのさまざまな部分で使えます。

* [**Loading Requirements**](./conditions): 変数の値を確認して、要素を表示するタイミングを制御できます。たとえば、[**Is Number**](./conditions#is-number-fancymenu_visibility_requirement_is_number) と [**Get Stored Variable** プレースホルダー](./placeholders#get-variable-value-fm-variable-getvariable) を組み合わせて、`clicks` が 5 より大きいときに要素を表示できます。

* **プレースホルダー**: [**Get Stored Variable** プレースホルダー](./placeholders#get-variable-value-fm-variable-getvariable) を使って、テキスト内に変数を挿入できます。たとえば `{"placeholder":"getvariable","values":{"name":"clicks"}}` のようにします。

* **ネストされたプレースホルダー**: [**Calculator** プレースホルダー](./placeholders#calculator-calc) の中で [**Get Stored Variable** プレースホルダー](./placeholders#get-variable-value-fm-variable-getvariable) を使えます。

* **アクション**: 変数を使うことで動的な動作を作れます。
  - [**Is Number**](./conditions#is-number-fancymenu_visibility_requirement_is_number) と [**Get Stored Variable** プレースホルダー](./placeholders#get-variable-value-fm-variable-getvariable) を使い、アクションスクリプトの [IF](./action-scripts#what-are-statements) 文で条件分岐できます。
  - [**Get Stored Variable** プレースホルダー](./placeholders#get-variable-value-fm-variable-getvariable) と [**Copy Text to Clipboard**](./action-scripts#copy-text-to-clipboard-copytoclipboard) を組み合わせられます。
  - [**Open Screen or Custom GUI**](./action-scripts#open-screen-or-custom-gui-opengui) で変数を使い、保存された進行状況や設定に応じて画面を選択できます。

## 変数の使用例

自分の変数活用の参考になるいくつかの例を紹介します。

1. **ハイスコア**: `highscore` 変数を作成し、現在のプレイヤースコアが既存値より高い場合にその値を設定するボタンを作ります。[**Get Stored Variable** プレースホルダー](./placeholders#get-variable-value-fm-variable-getvariable) で表示できます。

2. **難易度セレクター**: `easy`、`medium`、`hard` など、ゲームの難易度ごとに変数を作成します。ボタンで難易度変数を設定し、選択された難易度に応じて要素の表示/非表示を切り替えます。

3. **チュートリアルの進行状況**: `tutorial_step` のような変数を追加して、プレイヤーのチュートリアル進行を追跡します。各ステップを完了するたびに変数を増やし、Loading Requirements を使ってメニューの内容を少しずつ表示します。

## 永続性、スコープ、保存先

変数は現在の Minecraft インスタンス全体で共有されます。レイアウト、ワールド、サーバー、プレイヤーごとには分かれません。

値は `<game-directory>/config/fancymenu/user_variables.db` に即座に保存され、再起動後も保持されます。

- **Reset on Launch** は、次回ゲーム起動時にその変数を空にします。
- [**Clear All Variables**](./action-scripts#clear-all-variables-fm-variable-clear_variables) は、保存されているすべての変数値を削除します。
- 名前は大文字と小文字を区別します。`tutorial_step` のような、シンプルで一意な名前を使ってください。

[**Get Stored Variable** プレースホルダー](./placeholders#get-variable-value-fm-variable-getvariable) は、指定した名前の変数が存在しない場合、または保存値が空の場合に `0` を返します。このフォールバックは、比較や計算式で重要です。

[**Set Variable Value** アクション](./action-scripts#set-variable-value-fm-variable-set_variable) は `variable_name:variable_value` の形式を使い、最初のコロンで分割します。そのため、値にコロンを複数含めることができます。

FancyMenu の変数には、パスワード、トークン、その他の秘密情報を保存しないでください。変数は読み取り可能な設定データです。
