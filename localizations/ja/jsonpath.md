---
title: JSON パス
description: JSON Parser プレースホルダーで Jayway JsonPath を使用する方法。
---
# FancyMenu における JSON パス

FancyMenu の **JSON Parser** プレースホルダーは、[Jayway JsonPath](https://github.com/json-path/JsonPath) を使用して JSON ファイルから内容を取得します。
このページでは、JSON パスについて詳しく説明します。

このページの本文は、Jayway JsonPath の GitHub リポジトリにある README のコピーです。

> [!NOTE]
> この文章では、「JsonPath 式」という用語は JSON パスを指します。

# JsonPath

JsonPath 式は、XPath 式が XML ドキュメントと組み合わせて使われるのと同じように、常に JSON 構造を参照します。JsonPath における「root member object」は、オブジェクトでも配列でも常に `$` で参照されます。

JsonPath 式ではドット表記を使えます

`$.store.book[0].title`

またはブラケット表記を使えます

`$['store']['book'][0]['title']`

## 演算子

| 演算子                  | 説明                                                        |
| :------------------------ | :----------------------------------------------------------------- |
| `$`                       | 問い合わせ対象のルート要素。すべてのパス式はここから始まります。       |
| `@`                       | フィルタ述語で処理中の現在のノード。            |
| `*`                       | ワイルドカード。名前または数値が必要なあらゆる場所で使用できます。       |
| `..`                      | 深い検索。名前が必要なあらゆる場所で使用できます。                  |
| `.<name>`                 | ドット表記の子要素                                                  |
| `['<name>' (, '<name>')]` | ブラケット表記の子要素または複数の子要素                                  |
| `[<number> (, <number>)]` | 配列のインデックスまたは複数のインデックス                                             |
| `[start:end]`             | 配列スライス演算子                                               |
| `[?(<expression>)]`       | フィルタ式。式はブール値に評価されなければなりません。    |


## 関数

関数はパスの末尾で呼び出せます。関数への入力はパス式の出力です。
関数の出力は、その関数自体によって決まります。

| 関数                  | 説明                                                         | 出力型 |
| :------------------------ | :------------------------------------------------------------------ |:----------- |
| min()                     | 数値配列の最小値を返します                       | Double      |
| max()                     | 数値配列の最大値を返します                       | Double      |
| avg()                     | 数値配列の平均値を返します                   | Double      | 
| stddev()                  | 数値配列の標準偏差を返します        | Double      | 
| length()                  | 配列の長さを返します                                     | Integer     |
| sum()                     | 数値配列の合計を返します                       | Double      |
| keys()                    | プロパティのキーを返します（末尾のチルダ `~` の代替）  | `Set<E>`    |
| concat(X)                 | パスの出力に新しい項目を連結したものを返します  | like input  |
| append(X)                 | json path の出力配列に項目を追加します                           | like input  |

## フィルタ演算子

フィルタは、配列を絞り込むために使う論理式です。典型的なフィルタは `[?(@.age > 18)]` で、`@` は処理中の現在の項目を表します。より複雑なフィルタは、論理演算子 `&&` と `||` を使って作成できます。文字列リテラルはシングルクォートまたはダブルクォートで囲む必要があります（`[?(@.color == 'blue')]` または `[?(@.color == "blue")]`）。   

| 演算子                 | 説明                                                           |
| :----------------------- | :-------------------------------------------------------------------- |
| ==                       | 左辺が右辺と等しい（`1` は `'1'` と等しくないことに注意）              |
| !=                       | 左辺が右辺と等しくない                                            |
| <                        | 左辺が右辺より小さい                                               |
| <=                       | 左辺が右辺以下である                                        |
| >                        | 左辺が右辺より大きい                                            |
| >=                       | 左辺が右辺以上である                                |
| =~                       | 左辺が正規表現に一致する  [?(@.name =~ /foo.*?/i)]             |
| in                       | 左辺が右辺の中に存在する [?(@.size in ['S', 'M'])]                        |
| nin                      | 左辺が右辺の中に存在しない                                         |
| subsetof                 | 左辺が右辺の部分集合である [?(@.sizes subsetof ['S', 'M', 'L'])]       |
| anyof                    | 左辺が右辺と共通要素を持つ [?(@.sizes anyof ['M', 'L'])]    |
| noneof                   | 左辺が右辺と共通要素を持たない [?(@.sizes noneof ['M', 'L'])]    |
| size                     | 左辺（配列または文字列）のサイズが右辺と一致する必要がある                     |
| empty                    | 左辺（配列または文字列）が空である必要がある                                |


## パスの例

次の JSON があるとします。

```javascript
{
    "store": {
        "book": [
            {
                "category": "reference",
                "author": "Nigel Rees",
                "title": "Sayings of the Century",
                "price": 8.95
            },
            {
                "category": "fiction",
                "author": "Evelyn Waugh",
                "title": "Sword of Honour",
                "price": 12.99
            },
            {
                "category": "fiction",
                "author": "Herman Melville",
                "title": "Moby Dick",
                "isbn": "0-553-21311-3",
                "price": 8.99
            },
            {
                "category": "fiction",
                "author": "J. R. R. Tolkien",
                "title": "The Lord of the Rings",
                "isbn": "0-395-19395-8",
                "price": 22.99
            }
        ],
        "bicycle": {
            "color": "red",
            "price": 19.95
        }
    },
    "expensive": 10
}
```

| JsonPath（リンクをクリックして試せます）| 結果 |
| :------- | :----- |
| <a href="http://jsonpath.herokuapp.com/?path=$.store.book[*].author" target="_blank">$.store.book[*].author</a>| すべての本の著者     |
| <a href="http://jsonpath.herokuapp.com/?path=$..author" target="_blank">$..author</a>                   | すべての著者                         |
| <a href="http://jsonpath.herokuapp.com/?path=$.store.*" target="_blank">$.store.*</a>                  | 本と自転車を含むすべての要素  |
| <a href="http://jsonpath.herokuapp.com/?path=$.store..price" target="_blank">$.store..price</a>             | すべての価格         |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[2]" target="_blank">$..book[2]</a>                 | 3 冊目の本                      |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[2]" target="_blank">$..book[-2]</a>                 | 最後から 2 冊目の本            |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[0,1]" target="_blank">$..book[0,1]</a>               | 最初の 2 冊の本               |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[:2]" target="_blank">$..book[:2]</a>                | インデックス 0（含む）からインデックス 2（含まない）までのすべての本 |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[1:2]" target="_blank">$..book[1:2]</a>                | インデックス 1（含む）からインデックス 2（含まない）までのすべての本 |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[-2:]" target="_blank">$..book[-2:]</a>                | 最後の 2 冊の本                   |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[2:]" target="_blank">$..book[2:]</a>                | 後ろから 2 冊目以降の本          |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[?(@.isbn)]" target="_blank">$..book[?(@.isbn)]</a>          | ISBN 番号を持つすべての本         |
| <a href="http://jsonpath.herokuapp.com/?path=$.store.book[?(@.price < 10)]" target="_blank">$.store.book[?(@.price < 10)]</a> | 10 より安いすべての本  |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[?(@.price <= $['expensive'])]" target="_blank">$..book[?(@.price <= $['expensive'])]</a> | "expensive" ではないすべての本  |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[?(@.author =~ /.*REES/i)]" target="_blank">$..book[?(@.author =~ /.*REES/i)]</a> | 正規表現に一致するすべての本（大文字小文字を区別しない）  |
| <a href="http://jsonpath.herokuapp.com/?path=$..*" target="_blank">$..*</a>                        | すべてを表示   
| <a href="http://jsonpath.herokuapp.com/?path=$..book.length()" target="_blank">$..book.length()</a>                 | 本の数                      |
