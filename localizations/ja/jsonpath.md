---
title: JSON パス
description: JSON Parser プレースホルダーで Jayway JsonPath を使用する方法。
---

# FancyMenu における JSON パス

FancyMenu の **JSON Parser** プレースホルダーは、[Jayway JsonPath](https://github.com/json-path/JsonPath) を使って JSON ファイルから内容を取得します。
このページでは JSON パスについて詳しく説明します。

このページの本文は、Jayway JsonPath の GitHub リポジトリにある README のコピーです。

> この本文では、「JsonPath expression」という用語は JSON パスを指します。
{.is-info}

# JsonPath

JsonPath expression は、XPath expression が XML ドキュメントと組み合わせて使われるのと同じように、常に JSON 構造を参照します。JsonPath における「root member object」は、それがオブジェクトであっても配列であっても、常に `$` で参照されます。

JsonPath expression はドット記法を使えます。

`$.store.book[0].title`

またはブラケット記法を使えます。

`$['store']['book'][0]['title']`

## 演算子

| 演算子                  | 説明                                                        |
| :------------------------ | :----------------------------------------------------------------- |
| `$`                       | クエリのルート要素。すべてのパス式はここから始まります。       |
| `@`                       | フィルタ述語で処理中の現在のノード。            |
| `*`                       | ワイルドカード。名前または数値が必要な場所ならどこでも使用できます。       |
| `..`                      | 深い検索。名前が必要な場所ならどこでも使用できます。                  |
| `.<name>`                 | ドット記法の子要素                                                  |
| `['<name>' (, '<name>')]` | ブラケット記法の子要素または子要素群                                  |
| `[<number> (, <number>)]` | 配列のインデックスまたはインデックス群                                             |
| `[start:end]`             | 配列のスライス演算子                                               |
| `[?(<expression>)]`       | フィルタ式。式は真偽値として評価される必要があります。    |


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
| keys()                    | プロパティキーを返します（末尾のチルダ `~` の代替）  | `Set<E>`    |
| concat(X)                 | パス出力に新しい項目を追加した連結版を返します  | like input  |
| append(X)                 | json path の出力配列に項目を追加します                           | like input  |

## フィルタ演算子

フィルタは配列を絞り込むために使う論理式です。典型的なフィルタは `[?(@.age > 18)]` で、ここで `@` は処理中の現在の項目を表します。より複雑なフィルタは、論理演算子 `&&` と `||` を使って作成できます。文字列リテラルはシングルクォートまたはダブルクォートで囲む必要があります（`[?(@.color == 'blue')]` または `[?(@.color == "blue")]`）。   

| 演算子                 | 説明                                                           |
| :----------------------- | :-------------------------------------------------------------------- |
| ==                       | 左辺は右辺と等しい（1 は '1' と等しくない点に注意）              |
| !=                       | 左辺は右辺と等しくない                                            |
| <                        | 左辺は右辺より小さい                                               |
| <=                       | 左辺は右辺以下                                        |
| >                        | 左辺は右辺より大きい                                            |
| >=                       | 左辺は右辺以上                                |
| =~                       | 左辺が正規表現に一致する  [?(@.name =~ /foo.*?/i)]             |
| in                       | 左辺が右辺の中に存在する [?(@.size in ['S', 'M'])]                        |
| nin                      | 左辺が右辺の中に存在しない                                         |
| subsetof                 | 左辺は右辺の部分集合である [?(@.sizes subsetof ['S', 'M', 'L'])]       |
| anyof                    | 左辺は右辺と共通要素を持つ [?(@.sizes anyof ['M', 'L'])]     |
| noneof                   | 左辺は右辺と共通要素を持たない [?(@.sizes noneof ['M', 'L'])]    |
| size                     | 左辺（配列または文字列）のサイズが右辺と一致する必要がある                     |
| empty                    | 左辺（配列または文字列）は空である必要がある                                |


## パスの例

次の JSON を例にします。

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

| JsonPath（クリックすると試せます）| 結果 |
| :------- | :----- |
| <a href="http://jsonpath.herokuapp.com/?path=$.store.book[*].author" target="_blank">$.store.book[*].author</a>| すべての本の著者     |
| <a href="http://jsonpath.herokuapp.com/?path=$..author" target="_blank">$..author</a>                   | すべての著者                         |
| <a href="http://jsonpath.herokuapp.com/?path=$.store.*" target="_blank">$.store.*</a>                  | 本と自転車を含むすべての要素  |
| <a href="http://jsonpath.herokuapp.com/?path=$.store..price" target="_blank">$.store..price</a>             | すべての価格         |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[2]" target="_blank">$..book[2]</a>                 | 3冊目の本                      |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[2]" target="_blank">$..book[-2]</a>                 | 後ろから2冊目の本            |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[0,1]" target="_blank">$..book[0,1]</a>               | 最初の2冊               |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[:2]" target="_blank">$..book[:2]</a>                | インデックス 0（含む）からインデックス 2（含まない）までのすべての本 |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[1:2]" target="_blank">$..book[1:2]</a>                | インデックス 1（含む）からインデックス 2（含まない）までのすべての本 |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[-2:]" target="_blank">$..book[-2:]</a>                | 最後の2冊                   |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[2:]" target="_blank">$..book[2:]</a>                | 後ろから3冊目の本          |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[?(@.isbn)]" target="_blank">$..book[?(@.isbn)]</a>          | ISBN 番号を持つすべての本         |
| <a href="http://jsonpath.herokuapp.com/?path=$.store.book[?(@.price < 10)]" target="_blank">$.store.book[?(@.price < 10)]</a> | 10 より安い store 内のすべての本  |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[?(@.price <= $['expensive'])]" target="_blank">$..book[?(@.price <= $['expensive'])]</a> | 「expensive」ではない store 内のすべての本  |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[?(@.author =~ /.*REES/i)]" target="_blank">$..book[?(@.author =~ /.*REES/i)]</a> | 正規表現に一致するすべての本（大文字小文字を区別しない）  |
| <a href="http://jsonpath.herokuapp.com/?path=$..*" target="_blank">$..*</a>                        | すべてを取得する   
| <a href="http://jsonpath.herokuapp.com/?path=$..book.length()" target="_blank">$..book.length()</a>                 | 本の数                      |
