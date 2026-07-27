---
title: JSON-Pfade
description: Wie Jayway JsonPath im Platzhalter des JSON-Parsers verwendet wird.
---

# JSON-Pfade in FancyMenu

Der Platzhalter **JSON Parser** von FancyMenu verwendet [Jayway JsonPath](https://github.com/json-path/JsonPath), um Inhalte aus JSON-Dateien abzurufen.
Diese Seite erklärt JSON-Pfade im Detail.

Der Text auf dieser Seite ist eine Kopie der README aus dem GitHub-Repository von Jayway JsonPath.

> [!NOTE]
> In diesem Text bezieht sich der Begriff „JsonPath-Ausdruck“ auf einen JSON-Pfad.

# JsonPath

JsonPath-Ausdrücke beziehen sich immer auf eine JSON-Struktur, ähnlich wie XPath-Ausdrücke in Kombination mit 
Ein- XML-Dokument verwendet werden. Das „Root-Objekt“ in JsonPath wird immer mit `$` bezeichnet, unabhängig davon, ob es sich um ein 
Objekt oder ein Array handelt.

JsonPath-Ausdrücke können die Punkt-Notation verwenden

`$.store.book[0].title`

oder die Klammer-Notation

`$['store']['book'][0]['title']`

## Operatoren

| Operator                  | Beschreibung                                                     |
| :------------------------ | :---------------------------------------------------------------- |
| `$`                       | Das Root-Element, das abgefragt wird. Damit beginnen alle Pfadausdrücke. |
| `@`                       | Der aktuelle Knoten, der von einem Filterprädikat verarbeitet wird. |
| `*`                       | Platzhalter. Überall verfügbar, wo ein Name oder eine Zahl erwartet wird. |
| `..`                      | Tiefensuche. Überall verfügbar, wo ein Name erforderlich ist.     |
| `.<name>`                 | Kind in Punkt-Notation                                           |
| `['<name>' (, '<name>')]` | Kind oder Kinder in Klammer-Notation                              |
| `[<number> (, <number>)]` | Array-Index oder Indizes                                          |
| `[start:end]`             | Array-Slice-Operator                                              |
| `[?(<expression>)]`       | Filterausdruck. Der Ausdruck muss zu einem booleschen Wert ausgewertet werden. |


## Funktionen

Funktionen können am Ende eines Pfades aufgerufen werden - die Eingabe für eine Funktion ist die Ausgabe des Pfadausdrucks.
Die Ausgabe der Funktion wird von der Funktion selbst bestimmt.

| Funktion                  | Beschreibung                                                        | Ausgabetyp |
| :------------------------ | :------------------------------------------------------------------ |:----------- |
| min()                     | Liefert den Mindestwert eines Arrays von Zahlen                      | Double      |
| max()                     | Liefert den Höchstwert eines Arrays von Zahlen                       | Double      |
| avg()                     | Liefert den Durchschnittswert eines Arrays von Zahlen                | Double      | 
| stddev()                  | Liefert die Standardabweichung eines Arrays von Zahlen               | Double      | 
| length()                  | Liefert die Länge eines Arrays                                       | Integer     |
| sum()                     | Liefert die Summe eines Arrays von Zahlen                             | Double      |
| keys()                    | Liefert die Eigenschaftsschlüssel (eine Alternative zur abschließenden Tilde `~`)  | `Set<E>`    |
| concat(X)                 | Liefert eine verkettete Version der Pfadausgabe mit einem neuen Element | wie Eingabe |
| append(X)                 | Fügt der JSON-Pfad-Ausgabe ein Element hinzu                         | wie Eingabe |

## Filteroperatoren

Filter sind logische Ausdrücke, mit denen Arrays gefiltert werden. Ein typischer Filter wäre `[?(@.age > 18)]`, wobei `@` das aktuell verarbeitete Element darstellt. Komplexere Filter können mit den logischen Operatoren `&&` und `||` erstellt werden. Zeichenkettenliterale müssen in einfache oder doppelte Anführungszeichen gesetzt werden (`[?(@.color == 'blue')]` oder `[?(@.color == "blue")]`).   

| Operator                 | Beschreibung                                                           |
| :----------------------- | :-------------------------------------------------------------------- |
| ==                       | links ist gleich rechts (beachten Sie, dass 1 nicht gleich '1' ist)   |
| !=                       | links ist ungleich rechts                                             |
| <                        | links ist kleiner als rechts                                          |
| <=                       | links ist kleiner oder gleich rechts                                  |
| >                        | links ist größer als rechts                                           |
| >=                       | links ist größer oder gleich rechts                                   |
| =~                       | links entspricht regulärem Ausdruck  [?(@.name =~ /foo.*?/i)]         |
| in                       | links ist in rechts enthalten [?(@.size in ['S', 'M'])]              |
| nin                      | links ist nicht in rechts enthalten                                    |
| subsetof                 | links ist eine Teilmenge von rechts [?(@.sizes subsetof ['S', 'M', 'L'])] |
| anyof                    | links hat eine Schnittmenge mit rechts [?(@.sizes anyof ['M', 'L'])]  |
| noneof                   | links hat keine Schnittmenge mit rechts [?(@.sizes noneof ['M', 'L'])] |
| size                     | Die Größe von links (Array oder String) sollte mit rechts übereinstimmen |
| empty                    | links (Array oder String) sollte leer sein                            |


## Pfadbeispiele

Gegeben ist das JSON

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

| JsonPath (Link anklicken, um es auszuprobieren) | Ergebnis |
| :------- | :----- |
| <a href="http://jsonpath.herokuapp.com/?path=$.store.book[*].author" target="_blank">$.store.book[*].author</a>| Die Autoren aller Bücher     |
| <a href="http://jsonpath.herokuapp.com/?path=$..author" target="_blank">$..author</a>                   | Alle Autoren                         |
| <a href="http://jsonpath.herokuapp.com/?path=$.store.*" target="_blank">$.store.*</a>                  | Alles, sowohl Bücher als auch Fahrräder  |
| <a href="http://jsonpath.herokuapp.com/?path=$.store..price" target="_blank">$.store..price</a>             | Der Preis von allem         |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[2]" target="_blank">$..book[2]</a>                 | Das dritte Buch                      |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[2]" target="_blank">$..book[-2]</a>                 | Das vorletzte Buch            |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[0,1]" target="_blank">$..book[0,1]</a>               | Die ersten beiden Bücher               |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[:2]" target="_blank">$..book[:2]</a>                | Alle Bücher von Index 0 (inklusive) bis Index 2 (exklusive) |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[1:2]" target="_blank">$..book[1:2]</a>                | Alle Bücher von Index 1 (inklusive) bis Index 2 (exklusive) |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[-2:]" target="_blank">$..book[-2:]</a>                | Die letzten beiden Bücher                   |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[2:]" target="_blank">$..book[2:]</a>                | Zweites Buch von hinten          |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[?(@.isbn)]" target="_blank">$..book[?(@.isbn)]</a>          | Alle Bücher mit einer ISBN-Nummer         |
| <a href="http://jsonpath.herokuapp.com/?path=$.store.book[?(@.price < 10)]" target="_blank">$.store.book[?(@.price < 10)]</a> | Alle Bücher im Store, die günstiger als 10 sind  |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[?(@.price <= $['expensive'])]" target="_blank">$..book[?(@.price <= $['expensive'])]</a> | Alle Bücher im Store, die nicht „expensive“ sind  |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[?(@.author =~ /.*REES/i)]" target="_blank">$..book[?(@.author =~ /.*REES/i)]</a> | Alle Bücher, die dem regulären Ausdruck entsprechen (Groß-/Kleinschreibung ignorieren)  |
| <a href="http://jsonpath.herokuapp.com/?path=$..*" target="_blank">$..*</a>                        | Gib mir einfach alles   
| <a href="http://jsonpath.herokuapp.com/?path=$..book.length()" target="_blank">$..book.length()</a>                 | Die Anzahl der Bücher                      |
