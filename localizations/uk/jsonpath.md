---
title: JSON-шляхи
description: Як використовувати Jayway JsonPath у заповнювачі JSON Parser.
excludeFromAiPlaintext: true
sourceBlobSha: 2aa2965bffefdb17d944b31190f40ec33198c1e4
---
# JSON-шляхи у FancyMenu

Заповнювач **JSON Parser** у FancyMenu використовує [Jayway JsonPath](https://github.com/json-path/JsonPath) для отримання вмісту з JSON-файлів.
На цій сторінці докладно пояснюється використання JSON-шляхів.

Текст на цій сторінці є копією README з репозиторію Jayway JsonPath на GitHub.

> [!NOTE]
> У цьому тексті термін «вираз JsonPath» означає JSON-шлях.

# JsonPath

Вирази JsonPath завжди посилаються на структуру JSON так само, як вирази XPath використовуються разом із документом XML. «Кореневий об’єкт» у JsonPath завжди позначається як `$`, незалежно від того, є він об’єктом чи масивом.

У виразах JsonPath можна використовувати крапкову нотацію

`$.store.book[0].title`

або дужкову нотацію

`$['store']['book'][0]['title']`

## Оператори

| Оператор                  | Опис                                                               |
| :------------------------ | :----------------------------------------------------------------- |
| `$`                       | Кореневий елемент для запиту. З нього починаються всі вирази шляхів. |
| `@`                       | Поточний вузол, який обробляється предикатом фільтра.              |
| `*`                       | Шаблон. Доступний у будь-якому місці, де потрібні ім’я або число.  |
| `..`                      | Глибоке сканування. Доступне в будь-якому місці, де потрібне ім’я. |
| `.<name>`                 | Дочірній елемент у крапковій нотації                         |
| `['<name>' (, '<name>')]` | Дочірній елемент або дочірні елементи у дужковій нотації       |
| `[<number> (, <number>)]` | Індекс або індекси масиву                                     |
| `[start:end]`             | Оператор зрізу масиву                                          |
| `[?(<expression>)]`       | Вираз фільтра. Вираз має повертати логічне значення.            |


## Функції

Функції можна викликати в кінці шляху — вхідним значенням функції є результат виразу шляху.
Тип результату функції визначається самою функцією.

| Функція                  | Опис                                                               | Тип результату |
| :------------------------ | :------------------------------------------------------------------ |:----------- |
| min()                     | Повертає мінімальне значення масиву чисел                           | Double      |
| max()                     | Повертає максимальне значення масиву чисел                          | Double      |
| avg()                     | Повертає середнє значення масиву чисел                              | Double      | 
| stddev()                  | Повертає стандартне відхилення масиву чисел                         | Double      | 
| length()                  | Повертає довжину масиву                                            | Integer     |
| sum()                     | Повертає суму значень масиву чисел                                  | Double      |
| keys()                    | Повертає ключі властивостей (альтернатива кінцевій тильді `~`)      | `Set<E>`    |
| concat(X)                 | Повертає об’єднану версію результату шляху з новим елементом         | як у вхідного значення  |
| append(X)                 | Додає елемент до масиву результату JSON-шляху                       | як у вхідного значення  |

## Оператори фільтра

Фільтри — це логічні вирази, які використовуються для фільтрації масивів. Типовим фільтром є `[?(@.age > 18)]`, де `@` позначає поточний оброблюваний елемент. Складніші фільтри можна створювати за допомогою логічних операторів `&&` і `||`. Рядкові літерали потрібно брати в одинарні або подвійні лапки (`[?(@.color == 'blue')]` або `[?(@.color == "blue")]`).   

| Оператор                 | Опис                                                                  |
| :----------------------- | :-------------------------------------------------------------------- |
| ==                       | ліве значення дорівнює правому (зверніть увагу: 1 не дорівнює '1')    |
| !=                       | ліве значення не дорівнює правому                                    |
| <                        | ліве значення менше за праве                                          |
| <=                       | ліве значення менше або дорівнює правому                              |
| >                        | ліве значення більше за праве                                         |
| >=                       | ліве значення більше або дорівнює правому                             |
| =~                       | ліве значення відповідає регулярному виразу [?(@.name =~ /foo.*?/i)]  |
| in                       | ліве значення міститься у правому [?(@.size in ['S', 'M'])]           |
| nin                      | ліве значення не міститься у правому                                  |
| subsetof                 | ліве значення є підмножиною правого [?(@.sizes subsetof ['S', 'M', 'L'])] |
| anyof                    | ліве значення має спільні елементи з правим [?(@.sizes anyof ['M', 'L'])] |
| noneof                   | ліве значення не має спільних елементів із правим [?(@.sizes noneof ['M', 'L'])] |
| size                     | розмір лівого значення (масиву або рядка) має відповідати правому   |
| empty                    | ліве значення (масив або рядок) має бути порожнім                    |


## Приклади шляхів

Для наведеного JSON

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
| <a href="http://jsonpath.herokuapp.com/?path=$.store.book[*].author" target="_blank">$.store.book[*].author</a>| Автори всіх книг     |
| <a href="http://jsonpath.herokuapp.com/?path=$..author" target="_blank">$..author</a>                   | Усі автори                         |
| <a href="http://jsonpath.herokuapp.com/?path=$.store.*" target="_blank">$.store.*</a>                  | Усі елементи: і книги, і велосипеди  |
| <a href="http://jsonpath.herokuapp.com/?path=$.store..price" target="_blank">$.store..price</a>             | Ціна всіх товарів         |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[2]" target="_blank">$..book[2]</a>                 | Третя книга                      |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[2]" target="_blank">$..book[-2]</a>                 | Передостання книга            |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[0,1]" target="_blank">$..book[0,1]</a>               | Перші дві книги               |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[:2]" target="_blank">$..book[:2]</a>                | Усі книги від індексу 0 (включно) до індексу 2 (не включно) |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[1:2]" target="_blank">$..book[1:2]</a>                | Усі книги від індексу 1 (включно) до індексу 2 (не включно) |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[-2:]" target="_blank">$..book[-2:]</a>                | Останні дві книги                   |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[2:]" target="_blank">$..book[2:]</a>                | Книги, починаючи з третьої          |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[?(@.isbn)]" target="_blank">$..book[?(@.isbn)]</a>          | Усі книги з номером ISBN         |
| <a href="http://jsonpath.herokuapp.com/?path=$.store.book[?(@.price < 10)]" target="_blank">$.store.book[?(@.price < 10)]</a> | Усі книги в магазині, дешевші за 10  |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[?(@.price <= $['expensive'])]" target="_blank">$..book[?(@.price <= $['expensive'])]</a> | Усі книги в магазині, які не є «дорогими»  |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[?(@.author =~ /.*REES/i)]" target="_blank">$..book[?(@.author =~ /.*REES/i)]</a> | Усі книги, що відповідають регулярному виразу (без урахування регістру)  |
| <a href="http://jsonpath.herokuapp.com/?path=$..*" target="_blank">$..*</a>                        | Показати все   
| <a href="http://jsonpath.herokuapp.com/?path=$..book.length()" target="_blank">$..book.length()</a>                 | Кількість книг                      |
