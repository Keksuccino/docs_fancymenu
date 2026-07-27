---
title: JSON-шляхи
description: Як використовувати Jayway JsonPath у плейсхолдері JSON Parser.
---

# JSON-шляхи у FancyMenu

Плейсхолдер **JSON Parser** у FancyMenu використовує [Jayway JsonPath](https://github.com/json-path/JsonPath), щоб отримувати вміст із JSON-файлів.
Ця сторінка детально пояснює JSON-шляхи.

Текст на цій сторінці є копією README з GitHub-репозиторію Jayway JsonPath.

> [!NOTE]
> У цьому тексті термін «вираз JsonPath» означає JSON-шлях.

# JsonPath

Вирази JsonPath завжди посилаються на JSON-структуру так само, як вирази XPath використовуються разом із XML-документом. «Кореневий об’єкт члена» у JsonPath завжди позначається як `$`, незалежно від того, є це об’єкт чи масив.

Вирази JsonPath можуть використовувати крапкову нотацію

`$.store.book[0].title`

або нотацію в квадратних дужках

`$['store']['book'][0]['title']`

## Оператори

| Оператор                  | Опис                                                               |
| :------------------------ | :----------------------------------------------------------------- |
| `$`                       | Кореневий елемент для запиту. З цього починаються всі вирази шляху. |
| `@`                       | Поточний вузол, що обробляється фільтрувальним предикатом.        |
| `*`                       | Підстановний символ. Доступний будь-де, де потрібні ім’я або число. |
| `..`                      | Глибоке сканування. Доступне будь-де, де потрібне ім’я.            |
| `.<name>`                 | Дочірній елемент у крапковій нотації                               |
| `['<name>' (, '<name>')]` | Дочірній елемент або елементи у квадратних дужках                  |
| `[<number> (, <number>)]` | Індекс або індекси масиву                                           |
| `[start:end]`             | Оператор зрізу масиву                                              |
| `[?(<expression>)]`       | Фільтрувальний вираз. Вираз має повертати логічне значення.       |


## Функції

Функції можна викликати в кінці шляху — вхідними даними для функції є результат виразу шляху.
Вихід функції визначається самою функцією.

| Функція                  | Опис                                                         | Тип виходу |
| :------------------------ | :----------------------------------------------------------- |:----------- |
| min()                     | Повертає мінімальне значення масиву чисел                     | Double      |
| max()                     | Повертає максимальне значення масиву чисел                    | Double      |
| avg()                     | Повертає середнє значення масиву чисел                        | Double      | 
| stddev()                  | Повертає значення стандартного відхилення для масиву чисел    | Double      | 
| length()                  | Повертає довжину масиву                                       | Integer     |
| sum()                     | Повертає суму значень масиву чисел                            | Double      |
| keys()                    | Повертає ключі властивостей (альтернатива завершальному тильда `~`)  | `Set<E>`    |
| concat(X)                 | Повертає об’єднану версію результату шляху з новим елементом | як у вхідних даних |
| append(X)                 | Додає елемент до масиву результату JSON-шляху                  | як у вхідних даних |

## Фільтрувальні оператори

Фільтри — це логічні вирази, які використовуються для фільтрації масивів. Типовий фільтр — `[?(@.age > 18)]`, де `@` позначає поточний елемент, що обробляється. Більш складні фільтри можна створювати за допомогою логічних операторів `&&` і `||`. Рядкові літерали мають бути взяті в одинарні або подвійні лапки (`[?(@.color == 'blue')]` або `[?(@.color == "blue")]`).   

| Оператор                 | Опис                                                           |
| :----------------------- | :------------------------------------------------------------- |
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

| JsonPath (натисніть посилання, щоб спробувати)| Результат |
| :------- | :----- |
| <a href="http://jsonpath.herokuapp.com/?path=$.store.book[*].author" target="_blank">$.store.book[*].author</a>| Автори всіх книжок     |
| <a href="http://jsonpath.herokuapp.com/?path=$..author" target="_blank">$..author</a>                   | Усі автори                         |
| <a href="http://jsonpath.herokuapp.com/?path=$.store.*" target="_blank">$.store.*</a>                  | Усе в магазині: і книжки, і велосипеди  |
| <a href="http://jsonpath.herokuapp.com/?path=$.store..price" target="_blank">$.store..price</a>             | Ціна всього         |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[2]" target="_blank">$..book[2]</a>                 | Третя книжка                      |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[2]" target="_blank">$..book[-2]</a>                 | Передостання книжка            |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[0,1]" target="_blank">$..book[0,1]</a>               | Перші дві книжки               |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[:2]" target="_blank">$..book[:2]</a>                | Усі книжки з індексу 0 (включно) до індексу 2 (не включно) |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[1:2]" target="_blank">$..book[1:2]</a>                | Усі книжки з індексу 1 (включно) до індексу 2 (не включно) |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[-2:]" target="_blank">$..book[-2:]</a>                | Останні дві книжки                   |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[2:]" target="_blank">$..book[2:]</a>                | Книжка з кінця під номером два          |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[?(@.isbn)]" target="_blank">$..book[?(@.isbn)]</a>          | Усі книжки з номером ISBN         |
| <a href="http://jsonpath.herokuapp.com/?path=$.store.book[?(@.price < 10)]" target="_blank">$.store.book[?(@.price < 10)]</a> | Усі книжки в магазині, дешевші за 10  |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[?(@.price <= $['expensive'])]" target="_blank">$..book[?(@.price <= $['expensive'])]</a> | Усі книжки в магазині, які не є «дорогими»  |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[?(@.author =~ /.*REES/i)]" target="_blank">$..book[?(@.author =~ /.*REES/i)]</a> | Усі книжки, що відповідають регулярному виразу (без урахування регістру)  |
| <a href="http://jsonpath.herokuapp.com/?path=$..*" target="_blank">$..*</a>                        | Покажи мені все   
| <a href="http://jsonpath.herokuapp.com/?path=$..book.length()" target="_blank">$..book.length()</a>                 | Кількість книжок                      |
