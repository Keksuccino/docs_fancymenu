---
title: JSON 路径
description: 如何在 JSON Parser 占位符中使用 Jayway JsonPath。
---
# FancyMenu 中的 JSON 路径

FancyMenu 的 **JSON Parser** 占位符使用 [Jayway JsonPath](https://github.com/json-path/JsonPath) 从 JSON 文件中获取内容。
本页面会详细说明 JSON 路径。

本页文字是 Jayway JsonPath GitHub 仓库 README 的副本。

> [!NOTE]
> 在本文中，“JsonPath 表达式”指的是 JSON 路径。

# JsonPath

JsonPath 表达式始终用于引用 JSON 结构，其方式与 XPath 表达式结合 XML 文档使用时相同。JsonPath 中的“根成员对象”始终用 `$` 表示，无论它是对象还是数组。

JsonPath 表达式可以使用点表示法

`$.store.book[0].title`

或方括号表示法

`$['store']['book'][0]['title']`

## 运算符

| 运算符                  | 说明                                                        |
| :------------------------ | :----------------------------------------------------------------- |
| `$`                       | 要查询的根元素。所有路径表达式都从这里开始。       |
| `@`                       | 正在被过滤谓词处理的当前节点。            |
| `*`                       | 通配符。可用于任何需要名称或数字的地方。       |
| `..`                      | 深度扫描。可用于任何需要名称的地方。                  |
| `.<name>`                 | 点表示法的子项                                                  |
| `['<name>' (, '<name>')]` | 方括号表示法的单个子项或多个子项                                  |
| `[<number> (, <number>)]` | 数组索引或多个索引                                             |
| `[start:end]`             | 数组切片运算符                                               |
| `[?(<expression>)]`       | 过滤表达式。表达式必须求值为布尔值。    |


## 函数

函数可以在路径末尾调用——函数的输入是路径表达式的输出。
函数的输出由函数本身决定。

| 函数                  | 说明                                                         | 输出类型 |
| :------------------------ | :------------------------------------------------------------------ |:----------- |
| min()                     | 返回数字数组中的最小值                       | Double      |
| max()                     | 返回数字数组中的最大值                   | Double      | 
| avg()                     | 返回数字数组的平均值                   | Double      | 
| stddev()                  | 返回数字数组的标准差        | Double      | 
| length()                  | 返回数组的长度                                     | Integer     |
| sum()                     | 返回数字数组的总和                       | Double      |
| keys()                    | 返回属性键（是末尾波浪号 `~` 的替代写法）  | `Set<E>`    |
| concat(X)                 | 将路径输出与新项拼接成一个新的结果  | like input  |
| append(X)                 | 向 JSON 路径输出数组中添加一项                           | like input  |

## 过滤运算符

过滤器是用于筛选数组的逻辑表达式。典型的过滤器是 `[?(@.age > 18)]`，其中 `@` 表示当前正在处理的项。可以使用逻辑运算符 `&&` 和 `||` 创建更复杂的过滤条件。字符串字面量必须用单引号或双引号括起来（例如 `[?(@.color == 'blue')]` 或 `[?(@.color == "blue")]`）。   

| 运算符                 | 说明                                                           |
| :----------------------- | :-------------------------------------------------------------------- |
| ==                       | 左侧等于右侧（注意 1 不等于 '1'）              |
| !=                       | 左侧不等于右侧                                            |
| <                        | 左侧小于右侧                                               |
| <=                       | 左侧小于或等于右侧                                        |
| >                        | 左侧大于右侧                                            |
| >=                       | 左侧大于或等于右侧                                |
| =~                       | 左侧匹配正则表达式  [?(@.name =~ /foo.*?/i)]             |
| in                       | 左侧存在于右侧中 [?(@.size in ['S', 'M'])]                        |
| nin                      | 左侧不存在于右侧中                                         |
| subsetof                 | 左侧是右侧的子集 [?(@.sizes subsetof ['S', 'M', 'L'])]       |
| anyof                    | 左侧与右侧有交集 [?(@.sizes anyof ['M', 'L'])]     |
| noneof                   | 左侧与右侧没有交集 [?(@.sizes noneof ['M', 'L'])]    |
| size                     | 左侧的大小（数组或字符串）应与右侧匹配                     |
| empty                    | 左侧（数组或字符串）应为空                                |


## 路径示例

给定以下 JSON

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

| JsonPath（点击链接试试）| 结果 |
| :------- | :----- |
| <a href="http://jsonpath.herokuapp.com/?path=$.store.book[*].author" target="_blank">$.store.book[*].author</a>| 所有书籍的作者     |
| <a href="http://jsonpath.herokuapp.com/?path=$..author" target="_blank">$..author</a>                   | 所有作者                         |
| <a href="http://jsonpath.herokuapp.com/?path=$.store.*" target="_blank">$.store.*</a>                  | 所有内容，包括书和自行车  |
| <a href="http://jsonpath.herokuapp.com/?path=$.store..price" target="_blank">$.store..price</a>             | 所有价格         |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[2]" target="_blank">$..book[2]</a>                 | 第三本书                      |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[2]" target="_blank">$..book[-2]</a>                 | 倒数第二本书            |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[0,1]" target="_blank">$..book[0,1]</a>               | 前两本书               |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[:2]" target="_blank">$..book[:2]</a>                | 从索引 0（包含）到索引 2（不包含）的所有书籍 |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[1:2]" target="_blank">$..book[1:2]</a>                | 从索引 1（包含）到索引 2（不包含）的所有书籍 |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[-2:]" target="_blank">$..book[-2:]</a>                | 最后两本书                   |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[2:]" target="_blank">$..book[2:]</a>                | 倒数第二本书          |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[?(@.isbn)]" target="_blank">$..book[?(@.isbn)]</a>          | 所有带 ISBN 编号的书         |
| <a href="http://jsonpath.herokuapp.com/?path=$.store.book[?(@.price < 10)]" target="_blank">$.store.book[?(@.price < 10)]</a> | 商店中所有价格低于 10 的书  |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[?(@.price <= $['expensive'])]" target="_blank">$..book[?(@.price <= $['expensive'])]</a> | 商店中所有“不贵”的书  |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[?(@.author =~ /.*REES/i)]" target="_blank">$..book[?(@.author =~ /.*REES/i)]</a> | 所有匹配正则表达式的书（忽略大小写）  |
| <a href="http://jsonpath.herokuapp.com/?path=$..*" target="_blank">$..*</a>                        | 给我所有内容   
| <a href="http://jsonpath.herokuapp.com/?path=$..book.length()" target="_blank">$..book.length()</a>                 | 书籍数量                      |
