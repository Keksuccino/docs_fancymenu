---
title: JSON Paths
description: Як використовувати Jayway JsonPath у заповнювачі JSON Parser.
---

# JSON Paths у FancyMenu

Заповнювач **JSON Parser** у FancyMenu використовує [Jayway JsonPath](https://github.com/json-path/JsonPath) для отримання вмісту з JSON-файлів.
Ця сторінка детально пояснює JSON paths.

Текст на цій сторінці є копією README з GitHub-репозиторію Jayway JsonPath.

> У цьому тексті термін "вираз JsonPath" означає JSON path.
{.is-info}

# JsonPath

Вирази JsonPath завжди посилаються на JSON-структуру так само, як вирази XPath використовуються разом із 
XML-документом. "Кореневий об’єкт-член" у JsonPath завжди позначається як `$`, незалежно від того, 
є це об’єкт чи масив.

Вирази JsonPath можуть використовувати крапкову нотацію

`$.store.book[0].title`

або нотацію в квадратних дужках

`$['store']['book'][0]['title']`

## Оператори

| Operator                  | Description                                                        |
| :------------------------ | :----------------------------------------------------------------- |
| `$`                       | Кореневий елемент для запиту. З нього починаються всі вирази шляху.       |
| `@`                       | Поточний вузол, який обробляється предикатом фільтра.            |
| `*`                       | Підстановочний символ. Доступний будь-де, де потрібна назва або число.       |
| `..`                      | Глибоке сканування. Доступне будь-де, де потрібна назва.                  |
| `.<name>`                 | Дочірній елемент у крапковій нотації                                                  |
| `['<name>' (, '<name>')]` | Дочірній елемент або елементи у квадратних дужках                                  |
| `[<number> (, <number>)]` | Індекс або індекси масиву                                             |
| `[start:end]`             | Оператор зрізу масиву                                               |
| `[?(<expression>)]`       | Вираз фільтра. Вираз має обчислюватися до булевого значення.    |


## Функції

Функції можна викликати в кінці шляху — вхід для функції є результатом виразу шляху.
Вихід функції визначається самою функцією.

| Function                  | Description                                                         | Output type |
| :------------------------ | :------------------------------------------------------------------ |:----------- |
| min()                     | Повертає мінімальне значення масиву чисел                       | Double      |
| max()                     | Повертає максимальне значення масиву чисел                       | Double      |
| avg()                     | Повертає середнє значення масиву чисел                   | Double      | 
| stddev()                  | Повертає стандартне відхилення для масиву чисел        | Double      | 
| length()                  | Повертає довжину масиву                                     | Integer     |
| sum()                     | Повертає суму значень масиву чисел                       | Double      |
| keys()                    | Повертає ключі властивостей (альтернатива кінцевій тильді `~`)  | `Set<E>`    |
| concat(X)                 | Повертає об’єднану версію результату шляху з новим елементом  | like input  |
| append(X)                 | Додає елемент до масиву результату json path                           | like input  |

## Оператори фільтра

Фільтри — це логічні вирази, які використовуються для фільтрації масивів. Типовий фільтр виглядає так: `[?(@.age > 18)]`, де `@` представляє поточний елемент, що обробляється. Більш складні фільтри можна створювати за допомогою логічних операторів `&&` і `||`. Рядкові літерали мають бути взяті в одинарні або подвійні лапки (`[?(@.color == 'blue')]` або `[?(@.color == "blue")]`).   

| Operator                 | Description                                                           |
| :----------------------- | :-------------------------------------------------------------------- |
| ==                       | ліве значення дорівнює правому (зверніть увагу, що 1 не дорівнює '1')              |
| !=                       | ліве значення не дорівнює правому                                            |
| <                        | ліве значення менше за праве                                               |
| <=                       | ліве значення менше або дорівнює правому                                        |
| >                        | ліве значення більше за праве                                            |
| >=                       | ліве значення більше або дорівнює правому                                |
| =~                       | ліве значення відповідає регулярному виразу  [?(@.name =~ /foo.*?/i)]             |
| in                       | ліве значення існує в правому [?(@.size in ['S', 'M'])]                        |
| nin                      | ліве значення не існує в правому                                         |
| subsetof                 | ліве значення є підмножиною правого [?(@.sizes subsetof ['S', 'M', 'L'])]       |
| anyof                    | ліве значення має перетин із правим [?(@.sizes anyof ['M', 'L'])]    |
| noneof                   | ліве значення не має перетину з правим [?(@.sizes noneof ['M', 'L'])]    |
| size                     | розмір лівого значення (масиву або рядка) має відповідати правому                     |
| empty                    | ліве значення (масив або рядок) має бути порожнім                                |


## Приклади шляхів

Для такого JSON

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

| JsonPath (click link to try)| Result |
| :------- | :----- |
| <a href="http://jsonpath.herokuapp.com/?path=$.store.book[*].author" target="_blank">$.store.book[*].author</a>| Автори всіх книжок     |
| <a href="http://jsonpath.herokuapp.com/?path=$..author" target="_blank">$..author</a>                   | Усі автори                         |
| <a href="http://jsonpath.herokuapp.com/?path=$.store.*" target="_blank">$.store.*</a>                  | Усе в store, і книжки, і велосипеди  |
| <a href="http://jsonpath.herokuapp.com/?path=$.store..price" target="_blank">$.store..price</a>             | Ціна всього         |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[2]" target="_blank">$..book[2]</a>                 | Третя книжка                      |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[2]" target="_blank">$..book[-2]</a>                 | Передостання книжка            |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[0,1]" target="_blank">$..book[0,1]</a>               | Перші дві книжки               |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[:2]" target="_blank">$..book[:2]</a>                | Усі книжки з індексу 0 (включно) до індексу 2 (невключно) |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[1:2]" target="_blank">$..book[1:2]</a>                | Усі книжки з індексу 1 (включно) до індексу 2 (невключно) |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[-2:]" target="_blank">$..book[-2:]</a>                | Дві останні книжки                   |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[2:]" target="_blank">$..book[2:]</a>                | Книжка під номером два з кінця          |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[?(@.isbn)]" target="_blank">$..book[?(@.isbn)]</a>          | Усі книжки з номером ISBN         |
| <a href="http://jsonpath.herokuapp.com/?path=$.store.book[?(@.price < 10)]" target="_blank">$.store.book[?(@.price < 10)]</a> | Усі книжки в store, дешевші за 10  |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[?(@.price <= $['expensive'])]" target="_blank">$..book[?(@.price <= $['expensive'])]</a> | Усі книжки в store, які не є "дорогими"  |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[?(@.author =~ /.*REES/i)]" target="_blank">$..book[?(@.author =~ /.*REES/i)]</a> | Усі книжки, що відповідають регулярному виразу (без урахування регістру)  |
| <a href="http://jsonpath.herokuapp.com/?path=$..*" target="_blank">$..*</a>                        | Покажи мені все   
| <a href="http://jsonpath.herokuapp.com/?path=$..book.length()" target="_blank">$..book.length()</a>                 | Кількість книжок                      |
