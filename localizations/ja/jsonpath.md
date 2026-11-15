---
title: JSONパス
description: JSON ParserプレースホルダーでJayway JsonPathを使用する方法。
excludeFromAiPlaintext: true
sourceBlobSha: 2aa2965bffefdb17d944b31190f40ec33198c1e4
---
# FancyMenuのJSONパス

FancyMenuの**JSON Parser**プレースホルダーは、[Jayway JsonPath](https://github.com/json-path/JsonPath)を使用してJSONファイルからコンテンツを取得します。
このページでは、JSONパスについて詳しく説明します。

このページの文章は、Jayway JsonPathのGitHubリポジトリにあるREADMEを転載したものです。

> [!NOTE]
> この文章では、「JsonPath式」という用語はJSONパスを指します。

# JsonPath

JsonPath式は、XPath式をXMLドキュメントと組み合わせて使用する場合と同じように、常にJSON構造を参照します。JsonPathにおける「ルートメンバーオブジェクト」は、それがオブジェクトであるか配列であるかにかかわらず、常に`$`で表されます。

JsonPath式では、ドット記法

`$.store.book[0].title`

またはブラケット記法

`$['store']['book'][0]['title']`

を使用できます。

## 演算子

| 演算子                  | 説明                                                        |
| :------------------------ | :----------------------------------------------------------------- |
| `$`                       | クエリ対象のルート要素。すべてのパス式はここから始まります。       |
| `@`                       | フィルター述語によって処理中の現在のノード。            |
| `*`                       | ワイルドカード。名前または数値が必要な場所で使用できます。       |
| `..`                      | 深部スキャン。名前が必要な場所で使用できます。                  |
| `.<name>`                 | ドット記法による子要素                                                  |
| `['<name>' (, '<name>')]` | ブラケット記法による子要素または子要素群                                  |
| `[<number> (, <number>)]` | 配列のインデックスまたはインデックス群                                             |
| `[start:end]`             | 配列スライス演算子                                               |
| `[?(<expression>)]`       | フィルター式。式はブール値に評価される必要があります。    |


## 関数

関数はパスの末尾で呼び出すことができます。関数への入力は、パス式の出力です。
関数の出力は、関数自体によって決まります。

| 関数                  | 説明                                                         | 出力型 |
| :------------------------ | :------------------------------------------------------------------ |:----------- |
| min()                     | 数値配列の最小値を返します                       | Double      |
| max()                     | 数値配列の最大値を返します                       | Double      |
| avg()                     | 数値配列の平均値を返します                   | Double      | 
| stddev()                  | 数値配列の標準偏差を返します        | Double      | 
| length()                  | 配列の長さを返します                                     | Integer     |
| sum()                     | 数値配列の合計値を返します                       | Double      |
| keys()                    | プロパティキーを返します（末尾のチルダ`~`の代替）  | `Set<E>`    |
| concat(X)                 | パスの出力に新しい項目を追加して連結した値を返します  | 入力と同じ  |
| append(X)                 | JSONパスの出力配列に項目を追加します                           | 入力と同じ  |

## フィルター演算子

フィルターは、配列を絞り込むために使用する論理式です。一般的なフィルターは`[?(@.age > 18)]`で、`@`は処理中の現在の項目を表します。論理演算子`&&`と`||`を使用すると、より複雑なフィルターを作成できます。文字列リテラルは、単引用符または二重引用符で囲む必要があります（`[?(@.color == 'blue')]`または`[?(@.color == "blue")]`）。   

| 演算子                 | 説明                                                           |
| :----------------------- | :-------------------------------------------------------------------- |
| ==                       | 左辺が右辺と等しい（1は`'1'`とは等しくないことに注意）              |
| !=                       | 左辺が右辺と等しくない                                            |
| <                        | 左辺が右辺より小さい                                               |
| <=                       | 左辺が右辺以下                                        |
| >                        | 左辺が右辺より大きい                                            |
| >=                       | 左辺が右辺以上                                |
| =~                       | 左辺が正規表現に一致する  `[?(@.name =~ /foo.*?/i)]`             |
| in                       | 左辺が右辺に含まれる `[?(@.size in ['S', 'M'])]`                        |
| nin                      | 左辺が右辺に含まれない                                         |
| subsetof                 | 左辺が右辺の部分集合である `[?(@.sizes subsetof ['S', 'M', 'L'])]`       |
| anyof                    | 左辺と右辺に共通する要素がある `[?(@.sizes anyof ['M', 'L'])]`     |
| noneof                   | 左辺と右辺に共通する要素がない `[?(@.sizes noneof ['M', 'L'])]`    |
| size                     | 左辺（配列または文字列）のサイズが右辺と一致する                     |
| empty                    | 左辺（配列または文字列）が空である                                |


## パスの例

次のJSONを使用します。

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

| JsonPath（リンクをクリックして試す）| 結果 |
| :------- | :----- |
| <a href="http://jsonpath.herokuapp.com/?path=$.store.book[*].author" target="_blank">$.store.book[*].author</a>| すべての本の著者     |
| <a href="http://jsonpath.herokuapp.com/?path=$..author" target="_blank">$..author</a>                   | すべての著者                         |
| <a href="http://jsonpath.herokuapp.com/?path=$.store.*" target="_blank">$.store.*</a>                  | 本と自転車を含む、すべての項目  |
| <a href="http://jsonpath.herokuapp.com/?path=$.store..price" target="_blank">$.store..price</a>             | すべての価格         |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[2]" target="_blank">$..book[2]</a>                 | 3冊目の本                      |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[2]" target="_blank">$..book[-2]</a>                 | 最後から2番目の本            |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[0,1]" target="_blank">$..book[0,1]</a>               | 最初の2冊               |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[:2]" target="_blank">$..book[:2]</a>                | インデックス0（含む）からインデックス2（含まない）までのすべての本 |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[1:2]" target="_blank">$..book[1:2]</a>                | インデックス1（含む）からインデックス2（含まない）までのすべての本 |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[-2:]" target="_blank">$..book[-2:]</a>                | 最後の2冊                   |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[2:]" target="_blank">$..book[2:]</a>                | 後ろから数えて2番目以降の本          |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[?(@.isbn)]" target="_blank">$..book[?(@.isbn)]</a>          | ISBN番号があるすべての本         |
| <a href="http://jsonpath.herokuapp.com/?path=$.store.book[?(@.price < 10)]" target="_blank">$.store.book[?(@.price < 10)]</a> | 店内で10未満のすべての本  |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[?(@.price <= $['expensive'])]" target="_blank">$..book[?(@.price <= $['expensive'])]</a> | 店内で「高価」ではないすべての本  |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[?(@.author =~ /.*REES/i)]" target="_blank">$..book[?(@.author =~ /.*REES/i)]</a> | 正規表現に一致するすべての本（大文字と小文字を区別しない）  |
| <a href="http://jsonpath.herokuapp.com/?path=$..*" target="_blank">$..*</a>                        | すべての項目   
| <a href="http://jsonpath.herokuapp.com/?path=$..book.length()" target="_blank">$..book.length()</a>                 | 本の冊数                      |
