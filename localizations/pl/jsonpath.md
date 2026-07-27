---
title: Ścieżki JSON
description: Jak używać Jayway JsonPath w placeholderze JSON Parser.
---

# Ścieżki JSON w FancyMenu

Placeholder **JSON Parser** w FancyMenu używa [Jayway JsonPath](https://github.com/json-path/JsonPath), aby pobierać zawartość z plików JSON.
Ta strona szczegółowo wyjaśnia ścieżki JSON.

Tekst na tej stronie jest kopią README z repozytorium GitHub Jayway JsonPath.

> [!NOTE]
> W tym tekście termin „wyrażenie JsonPath” odnosi się do ścieżki JSON.

# JsonPath

Wyrażenia JsonPath zawsze odnoszą się do struktury JSON w taki sam sposób, w jaki wyrażenia XPath są używane w połączeniu 
z dokumentem XML. „Obiekt główny” w JsonPath jest zawsze oznaczany jako `$`, niezależnie od tego, czy jest to obiekt, czy tablica.

Wyrażenia JsonPath mogą używać zapisu kropkowego

`$.store.book[0].title`

lub zapisu nawiasowego

`$['store']['book'][0]['title']`

## Operatory

| Operator                  | Opis                                                               |
| :------------------------ | :----------------------------------------------------------------- |
| `$`                       | Element główny do zapytania. Od tego zaczynają się wszystkie ścieżki. |
| `@`                       | Bieżący węzeł przetwarzany przez predykat filtra.                  |
| `*`                       | Symbol wieloznaczny. Dostępny wszędzie tam, gdzie wymagane są nazwy lub liczby. |
| `..`                      | Głębokie przeszukiwanie. Dostępne wszędzie tam, gdzie wymagana jest nazwa. |
| `.<name>`                 | Dziecko w zapisie kropkowym                                       |
| `['<name>' (, '<name>')]` | Dziecko lub dzieci w zapisie nawiasowym                           |
| `[<number> (, <number>)]` | Indeks lub indeksy tablicy                                         |
| `[start:end]`             | Operator wycinka tablicy                                          |
| `[?(<expression>)]`       | Wyrażenie filtra. Wyrażenie musi zwracać wartość logiczną.        |


## Funkcje

Funkcje można wywoływać na końcu ścieżki — wejściem funkcji jest wynik wyrażenia ścieżki.
Wyjście funkcji jest określane przez samą funkcję.

| Function                  | Opis                                                               | Typ wyniku |
| :------------------------ | :------------------------------------------------------------------ |:----------- |
| min()                     | Zwraca minimalną wartość z tablicy liczb                           | Double      |
| max()                     | Zwraca maksymalną wartość z tablicy liczb                          | Double      |
| avg()                     | Zwraca średnią wartość z tablicy liczb                              | Double      | 
| stddev()                  | Zwraca odchylenie standardowe tablicy liczb                         | Double      | 
| length()                  | Zwraca długość tablicy                                             | Integer     |
| sum()                     | Zwraca sumę wartości z tablicy liczb                                | Double      |
| keys()                    | Zwraca klucze właściwości (alternatywa dla końcowego tyldy `~`)      | `Set<E>`    |
| concat(X)                 | Zwraca połączoną wersję wyniku ścieżki z nowym elementem            | jak wejście |
| append(X)                 | Dodaje element do tablicy wyniku json path                          | jak wejście |

## Operatory filtrów

Filtry to wyrażenia logiczne służące do filtrowania tablic. Typowy filtr wygląda tak: `[?(@.age > 18)]`, gdzie `@` reprezentuje bieżący element będący przetwarzany. Bardziej złożone filtry można tworzyć za pomocą operatorów logicznych `&&` i `||`. Literały tekstowe muszą być ujęte w pojedyncze lub podwójne cudzysłowy (`[?(@.color == 'blue')]` lub `[?(@.color == "blue")]`).   

| Operator                 | Opis                                                              |
| :----------------------- | :----------------------------------------------------------------- |
| ==                       | lewa strona jest równa prawej (zwróć uwagę, że 1 nie jest równe '1')              |
| !=                       | lewa strona nie jest równa prawej                                            |
| <                        | lewa strona jest mniejsza od prawej                                               |
| <=                       | lewa strona jest mniejsza lub równa prawej                                        |
| >                        | lewa strona jest większa od prawej                                            |
| >=                       | lewa strona jest większa lub równa prawej                                |
| =~                       | lewa strona pasuje do wyrażenia regularnego  [?(@.name =~ /foo.*?/i)]             |
| in                       | lewa strona występuje po prawej [?(@.size in ['S', 'M'])]                        |
| nin                      | lewa strona nie występuje po prawej                                         |
| subsetof                 | lewa strona jest podzbiorem prawej [?(@.sizes subsetof ['S', 'M', 'L'])]       |
| anyof                    | lewa strona ma część wspólną z prawą [?(@.sizes anyof ['M', 'L'])]    |
| noneof                   | lewa strona nie ma części wspólnej z prawą [?(@.sizes noneof ['M', 'L'])]    |
| size                     | rozmiar lewej strony (tablicy lub ciągu) powinien odpowiadać prawej stronie                     |
| empty                    | lewa strona (tablica lub ciąg) powinna być pusta                                |


## Przykłady ścieżek

Dla następującego JSON-a

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

| JsonPath (kliknij link, aby przetestować)| Wynik |
| :------- | :----- |
| <a href="http://jsonpath.herokuapp.com/?path=$.store.book[*].author" target="_blank">$.store.book[*].author</a>| Autorzy wszystkich książek     |
| <a href="http://jsonpath.herokuapp.com/?path=$..author" target="_blank">$..author</a>                   | Wszyscy autorzy                         |
| <a href="http://jsonpath.herokuapp.com/?path=$.store.*" target="_blank">$.store.*</a>                  | Wszystko, zarówno książki, jak i rowery  |
| <a href="http://jsonpath.herokuapp.com/?path=$.store..price" target="_blank">$.store..price</a>             | Cena wszystkiego         |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[2]" target="_blank">$..book[2]</a>                 | Trzecia książka                      |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[2]" target="_blank">$..book[-2]</a>                 | Przedostatnia książka            |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[0,1]" target="_blank">$..book[0,1]</a>               | Pierwsze dwie książki               |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[:2]" target="_blank">$..book[:2]</a>                | Wszystkie książki od indeksu 0 (włącznie) do indeksu 2 (wyłącznie) |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[1:2]" target="_blank">$..book[1:2]</a>                | Wszystkie książki od indeksu 1 (włącznie) do indeksu 2 (wyłącznie) |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[-2:]" target="_blank">$..book[-2:]</a>                | Ostatnie dwie książki                   |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[2:]" target="_blank">$..book[2:]</a>                | Książka numer dwa od końca          |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[?(@.isbn)]" target="_blank">$..book[?(@.isbn)]</a>          | Wszystkie książki z numerem ISBN         |
| <a href="http://jsonpath.herokuapp.com/?path=$.store.book[?(@.price < 10)]" target="_blank">$.store.book[?(@.price < 10)]</a> | Wszystkie książki w sklepie tańsze niż 10  |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[?(@.price <= $['expensive'])]" target="_blank">$..book[?(@.price <= $['expensive'])]</a> | Wszystkie książki w sklepie, które nie są „drogie”  |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[?(@.author =~ /.*REES/i)]" target="_blank">$..book[?(@.author =~ /.*REES/i)]</a> | Wszystkie książki pasujące do wyrażenia regularnego (bez uwzględniania wielkości liter)  |
| <a href="http://jsonpath.herokuapp.com/?path=$..*" target="_blank">$..*</a>                        | Pokaż mi wszystko   
| <a href="http://jsonpath.herokuapp.com/?path=$..book.length()" target="_blank">$..book.length()</a>                 | Liczba książek                      |
