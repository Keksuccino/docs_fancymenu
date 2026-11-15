---
title: JSON-Pfade
description: So verwenden Sie Jayway JsonPath im Platzhalter „JSON Parser“.
excludeFromAiPlaintext: true
sourceBlobSha: 2aa2965bffefdb17d944b31190f40ec33198c1e4
---
# JSON-Pfade in FancyMenu

Der Platzhalter **JSON Parser** von FancyMenu verwendet [Jayway JsonPath](https://github.com/json-path/JsonPath), um Inhalte aus JSON-Dateien abzurufen.
Auf dieser Seite werden JSON-Pfade ausführlich erklärt.

Der Text auf dieser Seite ist eine Kopie der README-Datei aus dem GitHub-Repository von Jayway JsonPath.

> [!NOTE]
> In diesem Text bezeichnet der Begriff „JsonPath-Ausdruck“ einen JSON-Pfad.

# JsonPath

JsonPath-Ausdrücke beziehen sich immer auf eine JSON-Struktur, so wie XPath-Ausdrücke in Verbindung mit einem XML-Dokument verwendet werden. Das „Stammobjekt“ in JsonPath wird immer mit `$` bezeichnet, unabhängig davon, ob es sich um ein Objekt oder ein Array handelt.

JsonPath-Ausdrücke können die Punktnotation verwenden

`$.store.book[0].title`

oder die Klammernotation

`$['store']['book'][0]['title']`

## Operatoren

| Operator                  | Beschreibung                                                        |
| :------------------------ | :----------------------------------------------------------------- |
| `$`                       | Das Stamm element, das abgefragt werden soll. Damit beginnen alle Pfadausdrücke. |
| `@`                       | Der aktuelle Knoten, der von einem Filterprädikat verarbeitet wird. |
| `*`                       | Platzhalter. Überall verfügbar, wo ein Name oder eine Zahl erforderlich ist. |
| `..`                      | Tiefensuche. Überall verfügbar, wo ein Name erforderlich ist.     |
| `.<name>`                 | Unterelement in Punktnotation                                      |
| `['<name>' (, '<name>')]` | Unterelement oder Unterelemente in Klammernotation                 |
| `[<number> (, <number>)]` | Array-Index oder -Indizes                                          |
| `[start:end]`             | Array-Slice-Operator                                               |
| `[?(<expression>)]`       | Filterausdruck. Der Ausdruck muss einen booleschen Wert ergeben.   |


## Funktionen

Funktionen können am Ende eines Pfads aufgerufen werden – die Eingabe einer Funktion ist die Ausgabe des Pfadausdrucks.
Die Ausgabe der Funktion wird durch die Funktion selbst bestimmt.

| Funktion                  | Beschreibung                                                         | Ausgabetyp |
| :------------------------ | :------------------------------------------------------------------ |:----------- |
| min()                     | Liefert den Minimalwert eines Zahlenarrays                           | Double      |
| max()                     | Liefert den Maximalwert eines Zahlenarrays                           | Double      |
| avg()                     | Liefert den Durchschnittswert eines Zahlenarrays                     | Double      | 
| stddev()                  | Liefert die Standardabweichung eines Zahlenarrays                   | Double      | 
| length()                  | Liefert die Länge eines Arrays                                       | Integer     |
| sum()                     | Liefert die Summe eines Zahlenarrays                                 | Double      |
| keys()                    | Liefert die Eigenschaftsschlüssel (eine Alternative zur abschließenden Tilde `~`) | `Set<E>`    |
| concat(X)                 | Liefert eine verkettete Version der Pfadausgabe mit einem neuen Element | wie Eingabe  |
| append(X)                 | Fügt der Ausgabe des JSON-Pfads ein Element hinzu                    | wie Eingabe  |

## Filteroperatoren

Filter sind logische Ausdrücke, die zum Filtern von Arrays verwendet werden. Ein typischer Filter wäre `[?(@.age > 18)]`, wobei `@` das aktuell verarbeitete Element darstellt. Mit den logischen Operatoren `&&` und `||` können komplexere Filter erstellt werden. Zeichenfolgenliterale müssen in einfache oder doppelte Anführungszeichen eingeschlossen werden (`[?(@.color == 'blue')]` oder `[?(@.color == "blue")]`).   

| Operator                 | Beschreibung                                                           |
| :----------------------- | :-------------------------------------------------------------------- |
| ==                       | links ist gleich rechts (beachten Sie, dass 1 nicht gleich '1' ist)   |
| !=                       | links ist nicht gleich rechts                                         |
| <                        | links ist kleiner als rechts                                          |
| <=                       | links ist kleiner oder gleich rechts                                  |
| >                        | links ist größer als rechts                                           |
| >=                       | links ist größer oder gleich rechts                                   |
| =~                       | links entspricht dem regulären Ausdruck [?(@.name =~ /foo.*?/i)]     |
| in                       | links ist in rechts enthalten [?(@.size in ['S', 'M'])]              |
| nin                      | links ist nicht in rechts enthalten                                   |
| subsetof                 | links ist eine Teilmenge von rechts [?(@.sizes subsetof ['S', 'M', 'L'])] |
| anyof                    | links überschneidet sich mit rechts [?(@.sizes anyof ['M', 'L'])]     |
| noneof                   | links überschneidet sich nicht mit rechts [?(@.sizes noneof ['M', 'L'])] |
| size                     | Die Größe von links (Array oder Zeichenfolge) muss rechts entsprechen |
| empty                    | links (Array oder Zeichenfolge) muss leer sein                       |


## Beispiele für Pfade

Gegeben sei das folgende JSON:

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

| JsonPath (Link zum Ausprobieren anklicken) | Ergebnis |
| :------- | :----- |
| <a href="http://jsonpath.herokuapp.com/?path=$.store.book[*].author" target="_blank">$.store.book[*].author</a>| Die Autoren aller Bücher     |
| <a href="http://jsonpath.herokuapp.com/?path=$..author" target="_blank">$..author</a>                   | Alle Autoren                         |
| <a href="http://jsonpath.herokuapp.com/?path=$.store.*" target="_blank">$.store.*</a>                  | Alle Elemente, sowohl Bücher als auch Fahrräder  |
| <a href="http://jsonpath.herokuapp.com/?path=$.store..price" target="_blank">$.store..price</a>             | Der Preis von allem         |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[2]" target="_blank">$..book[2]</a>                 | Das dritte Buch                      |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[2]" target="_blank">$..book[-2]</a>                 | Das vorletzte Buch            |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[0,1]" target="_blank">$..book[0,1]</a>               | Die ersten beiden Bücher               |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[:2]" target="_blank">$..book[:2]</a>                | Alle Bücher ab Index 0 (einschließlich) bis Index 2 (ausschließlich) |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[1:2]" target="_blank">$..book[1:2]</a>                | Alle Bücher ab Index 1 (einschließlich) bis Index 2 (ausschließlich) |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[-2:]" target="_blank">$..book[-2:]</a>                | Die letzten beiden Bücher                   |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[2:]" target="_blank">$..book[2:]</a>                | Buch Nummer zwei vom Ende aus          |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[?(@.isbn)]" target="_blank">$..book[?(@.isbn)]</a>          | Alle Bücher mit einer ISBN-Nummer         |
| <a href="http://jsonpath.herokuapp.com/?path=$.store.book[?(@.price < 10)]" target="_blank">$.store.book[?(@.price < 10)]</a> | Alle Bücher im Geschäft, die weniger als 10 kosten  |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[?(@.price <= $['expensive'])]" target="_blank">$..book[?(@.price <= $['expensive'])]</a> | Alle Bücher im Geschäft, die nicht „teuer“ sind  |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[?(@.author =~ /.*REES/i)]" target="_blank">$..book[?(@.author =~ /.*REES/i)]</a> | Alle Bücher, die dem regulären Ausdruck entsprechen (Groß-/Kleinschreibung ignorieren)  |
| <a href="http://jsonpath.herokuapp.com/?path=$..*" target="_blank">$..*</a>                        | Alles anzeigen   
| <a href="http://jsonpath.herokuapp.com/?path=$..book.length()" target="_blank">$..book.length()</a>                 | Die Anzahl der Bücher                      |
