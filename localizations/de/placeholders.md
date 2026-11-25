---
title: Platzhalter
description: >-
  Zeige in deinen Texten aktuelle Werte wie den Spielernamen, die Uhrzeit oder
  die Spieleranzahl eines Servers sowie alle Platzhalter, die FancyMenu bietet.
sourceBlobSha: 951d7772d640bc6b19d6f4dcc2fef4adcd1f13aa
---

# Platzhalter

Platzhalter sind kurze Codes, die FancyMenu durch einen aktuellen Wert ersetzt, zum Beispiel den Namen des Spielers, die Uhrzeit oder die Spieleranzahl eines Servers. Sie funktionieren in Elementtexten, Schaltflächenbeschriftungen, Tooltips, Aktions- und Anforderungswerten sowie in den meisten anderen Texten, die du eingeben kannst.

<img width="800" alt="Hinzufügen des Platzhalters für den Spielernamen zu einem Textelement im Layout-Editor: Platzhalter im Texteditor, die Kategorie Spieler und ein Text, der den Spieler mit seinem Namen begrüßt" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/placeholders_add.gif?raw=true">

> [!TIP]
> Deine eigenen [Variablen](/variables) funktionieren in denselben Texten. Verwende dazu `$$` und den Namen der Variable, zum Beispiel `$$coins`.

# Platzhalter hinzufügen

1. Öffne den Text im Texteditor, zum Beispiel **Textinhalt** eines [Textelements](/text-in-menus). Neben Textfeldern in Fenstern, etwa den Werten von Aktionen, findest du die Schaltfläche **Im Editor öffnen**.
2. Klicke an die Stelle, an der der Platzhalter eingefügt werden soll.
3. Klicke rechts oben im Texteditor auf **Platzhalter**.
4. Klicke auf eine Kategorie oder suche nach Name, Kennung oder Beschreibung. Mit **ZURÜCK** gelangst du zu den Kategorien. Platzhalter ohne Kategorie werden unterhalb der Kategorien aufgeführt.
5. Bewege die Maus über einen Platzhalter, um zu sehen, was er bewirkt, und klicke darauf, um ihn einzufügen.
6. Ersetze Beispielwerte, etwa die Mod-ID bei **Mod-Version**.

Texte, deren Texteditor keine Schaltfläche **Platzhalter** hat, unterstützen keine Platzhalter.

# Funktionsweise von Platzhaltern

Ein Platzhalter sieht so aus:

```
{"placeholder":"playername"}
```

Platzhalter mit Einstellungen haben diese unter `values`:

```
{"placeholder":"modversion","values":{"modid":"fancymenu"}}
```

- Die Kennung, zum Beispiel `playername`, unterscheidet Groß- und Kleinschreibung. Bei jedem Platzhalter unten sind seine Kennung und seine Werte aufgeführt.
- Die Reihenfolge der Werte ist unerheblich. Als optional gekennzeichnete Werte können weggelassen werden.
- Einen Platzhalter, den FancyMenu nicht ersetzen kann, etwa wegen eines Tippfehlers, lässt es so im Text stehen, wie du ihn eingegeben hast.
- Platzhalter geben immer Text zurück. Wenn es nichts anzuzeigen gibt, liefern sie einen Ersatzwert wie `0`, `0.0`, `---` oder nichts.
- [Formatierungscodes](/text-formatting) funktionieren auch mit Platzhaltern: `&6{"placeholder":"playername"}` zeigt den Namen in Gold an.

> [!IMPORTANT]
> Platzhalter sehen wie JSON aus, sind aber kein JSON. Verwende keinen JSON-Formatter und keinen JSON-Validator dafür, denn Platzhalter innerhalb anderer Platzhalter sind kein gültiges JSON.

## Platzhalter in Platzhaltern

Werte können andere Platzhalter und [Variablen](/variables#showing-variables-in-text) enthalten. FancyMenu ersetzt zuerst die inneren Platzhalter. Anführungszeichen innerhalb von Werten müssen nicht maskiert werden.

Damit wird der maximale RAM-Wert von MB in GB umgerechnet:

```
{"placeholder":"calc","values":{"decimal":"true","expression":"{"placeholder":"maxram"} / 1024"}}
```

Damit wird die Variable `rank` in Großbuchstaben angezeigt:

```
{"placeholder":"uppercase_text","values":{"text":"$$rank"}}
```

Wenn ein Platzhalter Text mit weiteren Platzhaltern zurückgibt, etwa einen mit [**Dateitext**](#file-text) ausgelesenen Dateiinhalt, ersetzt FancyMenu auch diese.

# Wissenswertes

- Platzhalter werden automatisch aktualisiert. FancyMenu hält einen ersetzten Text 30 Millisekunden lang vor, bevor es seine Platzhalter erneut ersetzt. Ändere diesen Wert unter **Menüleiste -> Anpassung -> Einstellungen** bei **Platzhalter-Cachingdauer [MS]**. Mit `0` werden die Platzhalter in jedem Frame ersetzt, was mehr Leistung kostet.
- Platzhalter, die Websites, Dateien oder Server auslesen, wie **Webtext** oder **Serverstatus**, werden im Hintergrund geladen. Bis dahin geben sie nichts oder einen Ersatzwert zurück.
- In [Aktionen](/action-scripts) erhalten Platzhalter ihren aktuellen Wert genau dann, wenn die Aktion ausgeführt wird.
- Platzhalter zu Welt, Bildschirm und Elementen funktionieren nur im Hauptthread des Spiels. In einem [Ticker](/elements#ticker), der im Hintergrund (asynchron) ausgeführt wird, zeigt FancyMenu stattdessen einen Fehler an.
- **Zufallszahl** liefert bei jeder Textaktualisierung eine neue Zahl. Um eine Zahl beizubehalten, speichere sie mit [**Variablenwert festlegen (FM-Variable)**](/action-scripts#set-variable-value-fm-variable) in einer [Variablen](/variables).

> [!CAUTION]
> Platzhalter wie **JSON-Parser**, **Dateitext** und **Inhalt der Zwischenablage** können Dateien im Spielordner und deine Zwischenablage auslesen. Zusammen mit Aktionen, die Websites kontaktieren, könnte ein Layout diese Daten nach außen senden. Verwende nur Layouts, denen du vertraust.

# Beispiele

## Willkommensfeld

<img width="800" alt="Ein Textelement begrüßt den Spieler mit Namen und zeigt die Minecraft-Version, die Anzahl der Mods und die Uhrzeit an" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/placeholders_welcome.png?raw=true">

```
### Welcome back, {"placeholder":"playername"}!
Minecraft {"placeholder":"mcversion"} with {"placeholder":"loadedmods"} mods
It's {"placeholder":"realtimehour"}:{"placeholder":"realtimeminute"}
```

## Serverstatus und Spieler

```
Survival: {"placeholder":"serverstatus","values":{"ip":"play.example.net"}}&r, {"placeholder":"serverplayercount","values":{"ip":"play.example.net"}} players
```

## Datum und Uhrzeit

```
{"placeholder":"realtimeday"}.{"placeholder":"realtimemonth"}.{"placeholder":"realtimeyear"}, {"placeholder":"realtimehour"}:{"placeholder":"realtimeminute"}
```

## RAM-Auslastung

```
RAM: {"placeholder":"usedram"} / {"placeholder":"maxram"} MB ({"placeholder":"percentram"}%)
```

# Alle Platzhalter

Hier findest du alle Platzhalter, die FancyMenu bietet. Die großen Kategorien **Erweitert** und **Welt** im Platzhaltermenü sind hier in kleinere Gruppen unterteilt.

## Variablen und Listen

Diese Platzhalter gehören zur Kategorie **Erweitert**. Unter [Variablen](/variables) erfährst du, wie du Variablen und Listen erstellst.

### Variablenwert abrufen (FM-Variable)

**Kennung:** `getvariable`

Der Wert einer deiner Variablen. Wenn die Variable leer ist oder nicht existiert, wird `0` zurückgegeben. Das ist praktisch für Zahlen. Eine Liste gibt alle Einträge als JSON-Array zurück, zum Beispiel `["Steve","Alex"]`.

- `name`: der Name der Variable, ohne `$$`

```
{"placeholder":"getvariable","values":{"name":"clicks"}}
```

### Listeneintrag abrufen (FM-Variable)

**Kennung:** `list_get`

Ein Eintrag einer Listenvariable.

- `name`: der Name der Liste
- `index`: die Position des Eintrags. Der erste Eintrag hat den Index `0`. Negative Zahlen zählen vom Ende aus, daher ist `-1` der letzte Eintrag.
- `fallback` (optional): der Rückgabewert, wenn an diesem Index kein Eintrag vorhanden ist oder keine Liste mit diesem Namen existiert. Standardmäßig leer.

```
{"placeholder":"list_get","values":{"name":"tips","index":"0","fallback":"No tips yet"}}
```

### Listengröße (FM-Variable)

**Kennung:** `list_size`

Die Anzahl der Listeneinträge. Wenn keine Liste mit diesem Namen existiert, wird `0` zurückgegeben.

- `name`: der Name der Liste

```
{"placeholder":"list_size","values":{"name":"tips"}}
```

### Index eines Listeneintrags (FM-Variable)

**Kennung:** `list_index_of`

Der Index des ersten Eintrags, der genau mit `value` übereinstimmt. Wenn der Eintrag nicht in der Liste vorkommt, wird `-1` zurückgegeben.

- `name`: der Name der Liste
- `value`: der Eintrag, nach dem gesucht wird
- `ignore_case` (optional): Mit `true` wird `Apple` auch als Treffer für `apple` gewertet. Standardmäßig `false`.

```
{"placeholder":"list_index_of","values":{"name":"read_news","value":"news_42","ignore_case":"false"}}
```

### Listeneinträge verbinden (FM-Variable)

**Kennung:** `list_join`

Alle Einträge einer Liste in einem Text. Wenn keine Liste mit diesem Namen existiert, wird nichts zurückgegeben.

- `name`: der Name der Liste
- `separator` (optional): der Text zwischen den Einträgen. `\n` steht für einen Zeilenumbruch. Standardmäßig `, `.

```
{"placeholder":"list_join","values":{"name":"tips","separator":"\n"}}
```

## Mathematik

Diese Platzhalter gehören zur Kategorie **Erweitert**. Bei Zahlen wird ein Punkt als Dezimaltrennzeichen verwendet, zum Beispiel `2.5`.

### Taschenrechner

**Kennung:** `calc`

Berechnet einen mathematischen Ausdruck, zum Beispiel `2 + 3 * 4`.

- `expression`: der zu berechnende Ausdruck
- `decimal` (optional): Mit `false` wird das Ergebnis auf eine ganze Zahl gerundet. Standardmäßig `true`; dann sind Ergebnisse wie `14.0` möglich.

```
{"placeholder":"calc","values":{"decimal":"false","expression":"{"placeholder":"usedram"} * 100 / {"placeholder":"maxram"}"}}
```

| In Ausdrücken | Funktion |
|---|---|
| `+` `-` `*` `/` | Addieren, subtrahieren, multiplizieren, dividieren |
| `^` | Potenz, zum Beispiel `2 ^ 3` ergibt 8 |
| `%` | Rest, zum Beispiel `7 % 3` ergibt 1 |
| `( )` | Fasst Teile zusammen, zum Beispiel `(2 + 3) * 4` |
| `pi`, `e` | Die Zahlen π und e |
| `abs(x)` | Zahl ohne Vorzeichen |
| `sqrt(x)`, `cbrt(x)` | Quadratwurzel, Kubikwurzel |
| `pow(x, y)` | x hoch y |
| `floor(x)`, `ceil(x)` | Rundet ab, rundet auf |
| `sin(x)`, `cos(x)`, `tan(x)`, `cot(x)` | Trigonometrie mit Winkeln im Bogenmaß |
| `asin(x)`, `acos(x)`, `atan(x)` | Umkehrfunktionen der Trigonometrie |
| `sinh(x)`, `cosh(x)`, `tanh(x)` | Hyperbolische Funktionen |
| `log(x)`, `log2(x)`, `log10(x)` | Logarithmen zur Basis e, 2 und 10 |
| `exp(x)` | e hoch x |
| `signum(x)` | `1`, `-1` oder `0`, wie bei [**Vorzeichen (Mathematik)**](#sign-math) |

### Zufallszahl

**Kennung:** `random_number`

Eine zufällige ganze Zahl zwischen `min` und `max`. Sie ändert sich bei jeder Textaktualisierung.

- `min`, `max`: die kleinste und die größte Zahl

```
{"placeholder":"random_number","values":{"min":"1","max":"6"}}
```

### Größte Zahl

**Kennung:** `maxnum`

Die größere von zwei Zahlen.

- `first`, `second`: die Zahlen

```
{"placeholder":"maxnum","values":{"first":"$$score","second":"$$best_score"}}
```

### Kleinste Zahl

**Kennung:** `minnum`

Die kleinere von zwei Zahlen.

- `first`, `second`: die Zahlen

```
{"placeholder":"minnum","values":{"first":"10","second":"15"}}
```

### Absolutwert einer Zahl

**Kennung:** `absnum`

Die Zahl ohne ihr Minuszeichen. Aus `-10.5` wird also `10.5`.

- `num`: die Zahl

```
{"placeholder":"absnum","values":{"num":"-10.5"}}
```

### Zahl negieren

**Kennung:** `negnum`

Macht eine positive Zahl negativ. Aus `10.5` wird also `-10.5`. Null und negative Zahlen bleiben unverändert.

- `num`: die Zahl

```
{"placeholder":"negnum","values":{"num":"10.5"}}
```

### Runden (Mathematik)

**Kennung:** `math_round`

Rundet eine Zahl. `2.5` wird auf `3` aufgerundet.

- `num`: die Zahl
- `decimals` (optional): Anzahl der beizubehaltenden Dezimalstellen. Mit `2` wird aus `3.14159` zum Beispiel `3.14`. Bei `0`, `-1` oder ohne Angabe wird auf eine ganze Zahl gerundet.

```
{"placeholder":"math_round","values":{"num":"3.14159","decimals":"2"}}
```

### Abrunden (Mathematik)

**Kennung:** `math_floor`

Rundet eine Zahl auf eine ganze Zahl ab. Aus `3.7` wird `3`, aus `-3.2` wird `-4`.

- `num`: die Zahl

```
{"placeholder":"math_floor","values":{"num":"3.7"}}
```

### Aufrunden (Mathematik)

**Kennung:** `math_ceil`

Rundet eine Zahl auf eine ganze Zahl auf. Aus `3.2` wird `4`, aus `-3.7` wird `-3`.

- `num`: die Zahl

```
{"placeholder":"math_ceil","values":{"num":"3.2"}}
```

### Vorzeichen (Mathematik)

**Kennung:** `math_sign`

`1` für positive Zahlen, `-1` für negative Zahlen und `0` für null.

- `num`: die Zahl

```
{"placeholder":"math_sign","values":{"num":"-3.14"}}
```

### *pi* (Mathematik)

**Kennung:** `math_pi`

Die Zahl π: `3.141592653589793`.

```
{"placeholder":"math_pi"}
```

### Trigonometrischer Sinus (Mathematik)

**Kennung:** `math_sin`

Der Sinus eines Winkels im Bogenmaß. Für Grad multiplizierst du diese zuerst mit π / 180, und zwar mit dem Taschenrechner.

- `angle`: der Winkel im Bogenmaß

```
{"placeholder":"math_sin","values":{"angle":"1.5707963267948966"}}
```

### Trigonometrischer Kosinus (Mathematik)

**Kennung:** `math_cos`

Der Kosinus eines Winkels im Bogenmaß.

- `angle`: der Winkel im Bogenmaß

```
{"placeholder":"math_cos","values":{"angle":"0"}}
```

### Trigonometrischer Tangens (Mathematik)

**Kennung:** `math_tan`

Der Tangens eines Winkels im Bogenmaß.

- `angle`: der Winkel im Bogenmaß

```
{"placeholder":"math_tan","values":{"angle":"0.7853981633974483"}}
```

### Hyperbolischer Sinus (Mathematik)

**Kennung:** `math_sinh`

Der hyperbolische Sinus einer Zahl.

- `num`: die Zahl

```
{"placeholder":"math_sinh","values":{"num":"1"}}
```

### Hyperbolischer Kosinus (Mathematik)

**Kennung:** `math_cosh`

Der hyperbolische Kosinus einer Zahl.

- `num`: die Zahl

```
{"placeholder":"math_cosh","values":{"num":"1"}}
```

### Hyperbolischer Tangens (Mathematik)

**Kennung:** `math_tanh`

Der hyperbolische Tangens einer Zahl.

- `num`: die Zahl

```
{"placeholder":"math_tanh","values":{"num":"1"}}
```

### Zahlensystem-Konverter

**Kennung:** `number_base_convert`

Wandelt eine Zahl in ein anderes Zahlensystem um, zum Beispiel von Dezimal in Binär- oder Hexadezimaldarstellung. Auch Dezimalzahlen funktionieren, mit bis zu 16 Stellen nach dem Punkt. Buchstaben im Ergebnis sind großgeschrieben, zum Beispiel `FF`.

- `input`: die Zahl
- `from_base` (optional): die Basis von `input`, von `2` bis `36`. Standardmäßig `10`.
- `to_base` (optional): die Basis des Ergebnisses, von `2` bis `36`. Standardmäßig `10`.

```
{"placeholder":"number_base_convert","values":{"input":"255","from_base":"10","to_base":"16"}}
```

## Text

Diese Platzhalter gehören zur Kategorie **Erweitert**.

### Text in Großbuchstaben

**Kennung:** `uppercase_text`

Der Text in Großbuchstaben: Aus `Hello World` wird `HELLO WORLD`. [Formatierungscodes](/text-formatting) wie `&a` bleiben unverändert.

- `text`: der Text

```
{"placeholder":"uppercase_text","values":{"text":"Hello World"}}
```

### Text in Kleinbuchstaben

**Kennung:** `lowercase_text`

Der Text in Kleinbuchstaben: Aus `HELLO WORLD` wird `hello world`. Formatierungscodes bleiben unverändert.

- `text`: der Text

```
{"placeholder":"lowercase_text","values":{"text":"HELLO WORLD"}}
```

### Text in Titelschreibung

**Kennung:** `title_case_text`

Jedes Wort beginnt mit einem Großbuchstaben: Aus `hello world` wird `Hello World`. Formatierungscodes bleiben unverändert.

- `text`: der Text

```
{"placeholder":"title_case_text","values":{"text":"hello world"}}
```

### Text in Satzschreibung

**Kennung:** `sentence_case_text`

Jeder Satz beginnt mit einem Großbuchstaben: Aus `hello world. this is fancymenu!` wird `Hello world. This is fancymenu!`. Formatierungscodes bleiben unverändert.

- `text`: der Text

```
{"placeholder":"sentence_case_text","values":{"text":"hello world. this is fancymenu!"}}
```

### Text in Snake Case

**Kennung:** `snake_case_text`

Kleinbuchstaben mit `_` zwischen den Wörtern: Aus `Hello World` wird `hello_world`. Formatierungscodes werden entfernt.

- `text`: der Text

```
{"placeholder":"snake_case_text","values":{"text":"Hello World"}}
```

### Text in Kebab Case

**Kennung:** `kebab_case_text`

Kleinbuchstaben mit `-` zwischen den Wörtern: Aus `Hello World` wird `hello-world`. Formatierungscodes werden entfernt.

- `text`: der Text

```
{"placeholder":"kebab_case_text","values":{"text":"Hello World"}}
```

### Text mit wechselnder Groß- und Kleinschreibung

**Kennung:** `alternating_case_text`

Klein- und Großbuchstaben wechseln sich ab: Aus `alternating case` wird `aLtErNaTiNg CaSe`.

- `text`: der Text

```
{"placeholder":"alternating_case_text","values":{"text":"alternating case"}}
```

### Groß- und Kleinschreibung umkehren

**Kennung:** `toggle_case_text`

Kleinbuchstaben werden zu Großbuchstaben und Großbuchstaben zu Kleinbuchstaben: Aus `Toggle Case` wird `tOGGLE cASE`.

- `text`: der Text

```
{"placeholder":"toggle_case_text","values":{"text":"Toggle Case"}}
```

### Text bereinigen

**Kennung:** `trim_text`

Entfernt Leerzeichen am Anfang und Ende eines Textes. Leerzeichen im Text bleiben erhalten.

- `text`: der Text

```
{"placeholder":"trim_text","values":{"text":"  Welcome!  "}}
```

### Text kürzen

**Kennung:** `crop_text`

Entfernt eine bestimmte Anzahl von Zeichen am Anfang und Ende eines Textes. Bei `hello world` ergibt das Entfernen eines Zeichens auf jeder Seite `ello worl`.

- `text`: der Text
- `remove_from_start`: Anzahl der Zeichen, die am Anfang entfernt werden
- `remove_from_end`: Anzahl der Zeichen, die am Ende entfernt werden

```
{"placeholder":"crop_text","values":{"text":"hello world","remove_from_start":"1","remove_from_end":"1"}}
```

### Text aufteilen

**Kennung:** `split_text`

Teilt einen Text auf und gibt einen seiner Teile zurück. Wird `Steve,Alex,Notch` bei `,` aufgeteilt, ist `Alex` der Teil mit Index `1`.

- `input`: der Text
- `regex`: die Stelle, an der geteilt wird, als regulärer Ausdruck. Zeichen wie `.`, `|` und `?` benötigen davor ein `\`, zum Beispiel `\.`.
- `max_parts` (optional): maximale Anzahl der Teile. Mit `-1` (Standard) wird bei jedem Treffer geteilt.
- `split_index`: der zurückzugebende Teil. Der erste Teil hat den Index `0`.

```
{"placeholder":"split_text","values":{"input":"Steve,Alex,Notch","regex":",","max_parts":"-1","split_index":"1"}}
```

### Text ersetzen

**Kennung:** `replace_text`

Ersetzt Teile eines Textes: Wenn in `Hello World!` `World` durch `FancyMenu` ersetzt wird, ergibt sich `Hello FancyMenu!`.

- `text`: der Text
- `search`: wonach gesucht wird
- `replacement` (optional): womit der Treffer ersetzt wird. Standardmäßig leer; dadurch wird der Treffer entfernt.
- `use_regex` (optional): Mit `true` ist `search` ein regulärer Ausdruck. Dann stehen `$1`, `$2` und so weiter in `replacement` für die gefundenen Gruppen. Standardmäßig `false`.
- `replace_all` (optional): Mit `false` wird nur der erste Treffer ersetzt. Standardmäßig `true`.

```
{"placeholder":"replace_text","values":{"text":"Hello World!","search":"World","replacement":"FancyMenu","use_regex":"false","replace_all":"true"}}
```

### Fallauswahl

**Kennung:** `switch_case`

Gibt das Ergebnis des Falls zurück, der zu einem Wert passt. Wenn die Variable `difficulty_level` den Wert `2` hat, gibt das Beispiel `Hard Mode` zurück.

- `value`: der zu prüfende Wert
- `cases`: Wert-Ergebnis-Paare, zum Beispiel `1:Easy Mode,2:Hard Mode`. Werte und Ergebnisse dürfen weder `,` noch `:` enthalten.
- `default` (optional): das Ergebnis, wenn kein Fall passt. Ohne diesen Wert bleibt der Platzhalter unverändert.

```
{"placeholder":"switch_case","values":{"value":"$$difficulty_level","cases":"1:Easy Mode,2:Hard Mode","default":"Normal Mode"}}
```

### Text lokalisieren

**Kennung:** `local`

Der Text eines Lokalisierungsschlüssels in der aktuellen Spielsprache, zum Beispiel `Singleplayer` für `menu.singleplayer`. Funktioniert mit Minecraft-Schlüsseln, Schlüsseln von Mods und eigenen Schlüsseln (siehe [Lokalisierung](/localization)).

- `key`: der Lokalisierungsschlüssel

```
{"placeholder":"local","values":{"key":"menu.singleplayer"}}
```

### Als Text maskieren

**Kennung:** `stringify`

Ersetzt die Platzhalter im Text und setzt dann vor jedes `\`, `{` und `}` ein Maskierungszeichen. So kann externer Text, etwa von einer Website, nicht als Platzhalter interpretiert werden.

- `text`: der Text

```
{"placeholder":"stringify","values":{"text":"{"placeholder":"webtext","values":{"link":"https://example.com/motd.txt"}}"}}
```

## Daten und Dateien

Diese Platzhalter gehören zur Kategorie **Erweitert**. Lokale Pfade beginnen im Spielordner, zum Beispiel `/config/fancymenu/assets/news.txt`, und können nicht aus diesem Ordner herausführen (siehe [Ressourcen](/resources#local-resources)).

### JSON-Parser

**Kennung:** `json`

Liest einen Wert aus JSON aus. Bei mehreren Ergebnissen wird jeweils eines pro Zeile angezeigt.

- `source`: JSON-Text, eine JSON-Datei im Spielordner oder die URL einer JSON-Datei
- `json_path`: der Pfad zum Wert, zum Beispiel `$.name` oder `$.players[0].name`. Weitere Informationen zu JSON-Pfaden findest du auf [json.fancymenu.net](https://json.fancymenu.net).

```
{"placeholder":"json","values":{"source":"https://example.com/server_info.json","json_path":"$.news.title"}}
```

JSON aus dem Web wird einmal geladen und erneut, wenn FancyMenu neu geladen wird. Änderungen an Dateien werden sofort angezeigt.

| Pfad | Rückgabewert |
|---|---|
| `$.name` | `name` auf der obersten Ebene |
| `$.player.level` | `level` innerhalb von `player` |
| `$.items[0].id` | `id` des ersten Eintrags in `items` |
| `$.scores.*` | Alle Werte in `scores` |

### Dateitext

**Kennung:** `file_text`

Der Text einer Datei oder URL. Dateien werden jede Sekunde erneut gelesen, URLs alle 10 Sekunden. Während des Ladens oder wenn der Inhalt nicht gelesen werden kann, wird nichts zurückgegeben.

- `path_or_url`: eine Datei im Spielordner oder eine URL. Pfade, die mit `.minecraft/` beginnen, verweisen auf den standardmäßigen Minecraft-Ordner.
- `mode` (optional): `all` für den gesamten Text oder `last` für die letzten Zeilen. Standardmäßig `all`.
- `separator` (optional): der Text zwischen den Zeilen. Standardmäßig `\n` (Zeilenumbruch).
- `last_lines` (optional): Anzahl der Zeilen, die `last` zurückgibt. Standardmäßig `1`.

```
{"placeholder":"file_text","values":{"path_or_url":"/config/fancymenu/assets/changelog.txt","mode":"all","separator":"\n","last_lines":"1"}}
```

### Dateigröße

**Kennung:** `file_size`

Die Größe einer Datei in Byte. Wenn die Datei nicht existiert, wird `0` zurückgegeben. Pfade, die mit `.minecraft/` beginnen, verweisen auf den standardmäßigen Minecraft-Ordner.

- `path`: die Datei

```
{"placeholder":"file_size","values":{"path":"/config/fancymenu/assets/news.txt"}}
```

### Datei-MD5

**Kennung:** `file_md5`

Der MD5-Hash einer Datei, zum Beispiel `d41d8cd98f00b204e9800998ecf8427e`. Wenn die Datei nicht existiert, ist der Wert leer. Pfade, die mit `.minecraft/` beginnen, verweisen auf den standardmäßigen Minecraft-Ordner.

- `path`: die Datei

```
{"placeholder":"file_md5","values":{"path":"/config/fancymenu/assets/menu_music.ogg"}}
```

### In Base64 kodieren

**Kennung:** `base64_encode`

Der Text als Base64: Aus `Hello World` wird `SGVsbG8gV29ybGQ=`.

- `text`: der Text

```
{"placeholder":"base64_encode","values":{"text":"Hello World"}}
```

### Aus Base64 dekodieren

**Kennung:** `base64_decode`

Dekodiert Base64 zurück in Text: Aus `SGVsbG8gV29ybGQ=` wird `Hello World`.

- `text`: der Base64-Text

```
{"placeholder":"base64_decode","values":{"text":"SGVsbG8gV29ybGQ="}}
```

### NBT-Daten abrufen (clientseitig)

**Kennung:** `nbt_data_get`

Liest NBT-Daten aus dem, was dein Spiel über die Welt weiß, ähnlich wie `/data get`. Das geht schnell, aber Server senden Spielern nicht alle Daten.

- `source_type`: `entity` oder `block`
- `entity_selector`: bei `entity` ein Selektor wie `@s` (du selbst), `@p`, `@e[type=minecraft:horse,limit=1,sort=nearest]` oder der Name beziehungsweise die UUID einer Entität. Selektoren können `type`, `name`, `tag`, `limit`, `sort`, `distance`, `x`, `y`, `z`, `dx`, `dy` und `dz` enthalten. Es wird der erste Treffer verwendet.
- `block_pos`: bei `block` die Position einer Block-Entität, etwa einer Truhe: `120 64 -35`
- `nbt_path`: der NBT-Pfad, zum Beispiel `foodLevel` oder `Inventory[0].id`
- `scale` (optional): multipliziert Zahlen. Standardmäßig `1.0`.
- `return_type` (optional): `value` (Zahlen und Texte unverändert), `string`, `snbt` oder `json`. Standardmäßig `value`.

```
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"foodLevel","scale":"1.0","return_type":"value"}}
```

### NBT-Daten abrufen (serverseitig)

**Kennung:** `nbt_data_get_server`

Liest NBT-Daten direkt vom Server aus, genau wie `/data get`. Dafür muss FancyMenu auf dem Server installiert sein. Im Einzelspielermodus funktioniert es immer. Bis der Server antwortet, wird nichts zurückgegeben; danach wird der Wert etwa alle 100 Millisekunden aktualisiert.

- `source_type`: `entity`, `block` oder `storage`
- `entity_selector`: bei `entity` ein beliebiger Selektor von `/data get`, der eine Entität findet, zum Beispiel `@s` oder `@e[type=minecraft:villager,limit=1,sort=nearest]`
- `block_pos`: bei `block` eine Position wie `120 64 -35`, `~ ~-1 ~` oder `^ ^ ^1`
- `storage_id`: bei `storage` die ID eines Befehls-Speichers, zum Beispiel `mypack:quests`
- `nbt_path` (optional): der NBT-Pfad. Ohne Angabe erhältst du alle Daten.
- `scale` (optional): multipliziert Zahlen. Standardmäßig `1.0`.
- `return_type` (optional): `value`, `string`, `snbt` oder `json`. Standardmäßig `value`.

```
{"placeholder":"nbt_data_get_server","values":{"source_type":"storage","storage_id":"mypack:quests","nbt_path":"completed","return_type":"value"}}
```

## Audio

Diese Platzhalter lesen [Audioelemente](/elements#audio) des geöffneten Menüs aus. Klicke im Layout-Editor mit der rechten Maustaste auf ein Audioelement und dann auf **Element-ID kopieren**, um seine ID zu erhalten.

### Lautstärke des Audioelements

**Kennung:** `audio_element_vol`

Die Lautstärke des Audioelements von `0.0` (0 %) bis `1.0` (100 %).

- `element_identifier`: die ID des Audioelements

```
{"placeholder":"audio_element_vol","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Aktueller Audiotitel

**Kennung:** `audio_element_current_track`

Der Dateiname des Titels, der gerade abgespielt wird, zum Beispiel `menu_theme.ogg`. Wenn kein Titel abgespielt wird, lautet der Wert `---`.

- `element_identifier`: die ID des Audioelements
- `display_name_mappings` (optional): Namen, die statt der Dateinamen angezeigt werden. Zwischen Dateiname und Anzeigename steht `=>`, zwischen den Paaren `%:%`.

```
{"placeholder":"audio_element_current_track","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","display_name_mappings":"menu_theme.ogg=>Menu Theme%:%credits.ogg=>Credits Theme"}}
```

### Audiodauer

**Kennung:** `audio_duration`

Die Dauer des aktuellen Titels, zum Beispiel `03:45`. Während des Ladens wird `00:00` angezeigt.

- `element_identifier`: die ID des Audioelements

```
{"placeholder":"audio_duration","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Audio-Wiedergabezeit

**Kennung:** `audio_playtime`

Die aktuelle Position im Titel, zum Beispiel `01:30`. Wenn die Wiedergabe angehalten oder gestoppt ist, wird `00:00` (oder `0`) angezeigt.

- `element_identifier`: die ID des Audioelements
- `show_percentage` (optional): Mit `true` wird stattdessen der Fortschritt von `0` bis `100` zurückgegeben. Standardmäßig `false`.

```
{"placeholder":"audio_playtime","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","show_percentage":"false"}}
```

### Audio-Wiedergabestatus

**Kennung:** `audio_playing_state`

`true`, solange das Audioelement wiedergegeben wird, und `false`, wenn es pausiert oder gestoppt ist.

- `element_identifier`: die ID des Audioelements

```
{"placeholder":"audio_playing_state","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

## Client

Diese Platzhalter beziehen sich auf das Spiel und seine Mods.

### Minecraft-Version

**Kennung:** `mcversion`

Die Minecraft-Version, zum Beispiel `1.21.1`.

```
{"placeholder":"mcversion"}
```

### Name des Mod-Loaders

**Kennung:** `loadername`

Der Name des Mod-Loaders, zum Beispiel `Fabric` oder `NeoForge`.

```
{"placeholder":"loadername"}
```

### Version des Mod-Loaders

**Kennung:** `loaderver`

Die Version des Mod-Loaders, zum Beispiel `0.16.14`.

```
{"placeholder":"loaderver"}
```

### Mod-Version

**Kennung:** `modversion`

Die Version eines installierten Mods, zum Beispiel `3.11.0`. Wenn der Mod nicht installiert ist, wird `0.0.0` zurückgegeben.

- `modid`: die ID des Mods, zum Beispiel `fancymenu`

```
{"placeholder":"modversion","values":{"modid":"fancymenu"}}
```

### Anzahl aktiver Mods

**Kennung:** `loadedmods`

Die Anzahl der geladenen Mods. Bibliotheken und Mods innerhalb anderer Mods werden mitgezählt; daher ist der Wert oft höher als die Anzahl der Mod-Dateien.

```
{"placeholder":"loadedmods"}
```

### Gesamtzahl der Mods

**Kennung:** `totalmods`

Ungefähre Anzahl der installierten Mods, ermittelt anhand der `.jar`-Dateien im Ordner `mods` einmal pro Spielstart. Der Wert ist nie kleiner als **Anzahl aktiver Mods**.

```
{"placeholder":"totalmods"}
```

### Fortschritt beim Laden der Welt

**Kennung:** `world_load_progress`

Der Ladefortschritt einer Welt von `0` bis `100`, solange der Ladebildschirm angezeigt wird. Praktisch für Ladebalken. Auf allen anderen Bildschirmen ist der Wert `0`.

```
{"placeholder":"world_load_progress"}
```

### Wert einer Minecraft-Option

**Kennung:** `minecraft_option_value`

Der Wert einer Minecraft-Option, wie er in der Datei `options.txt` im Spielordner gespeichert ist, zum Beispiel `12` für `renderDistance`. Wenn keine Option mit diesem Namen existiert, ist der Wert leer.

- `name`: der Name der Option in `options.txt`

```
{"placeholder":"minecraft_option_value","values":{"name":"renderDistance"}}
```

### Taste einer Tastenbelegung

**Kennung:** `keybind_key`

Die Taste, die momentan einer Tastenbelegung zugewiesen ist, wie im Steuerungsbildschirm angezeigt: zum Springen etwa `Space`. Wenn keine Tastenbelegung mit diesem Namen existiert, ist der Wert leer.

- `keybind`: der Name der Tastenbelegung, zum Beispiel `key.jump` oder `key.inventory`. Die Namen stehen in `options.txt`, jedoch ohne das vorangestellte `key_`: Aus `key_key.jump` wird also `key.jump`.

```
Press {"placeholder":"keybind_key","values":{"keybind":"key.inventory"}} to open your inventory!
```

### Zuletzt besuchte Welt oder Server

**Kennung:** `last_world_server`

Die Welt oder der Server, dem der Spieler zuletzt beigetreten ist. Server werden als `play.example.net:25565` angezeigt.

- `type`: `both` für Welten und Server, `world` nur für Welten oder `server` nur für Server. Bei `world` oder `server` bleibt der Wert leer, wenn der zuletzt besuchte Eintrag vom jeweils anderen Typ war.
- `full_world_path` (optional): Mit `false` wird nur der Name einer Welt zurückgegeben, zum Beispiel `New World`. Mit `true` wird der Pfad ihres Ordners zurückgegeben. Standardmäßig `true`.

```
{"placeholder":"last_world_server","values":{"type":"world","full_world_path":"false"}}
```

## GUI

Diese Platzhalter beziehen sich auf den geöffneten Bildschirm und seine Elemente. Bei Elementplatzhaltern musst du die ID eines Elements angeben: Klicke im Layout-Editor mit der rechten Maustaste darauf und wähle **Element-ID kopieren**.

### Bildschirmbreite

**Kennung:** `guiwidth`

Die Breite des Bildschirms in GUI-Pixeln. Das ist die Größe, die Elemente verwenden, nicht die Pixelanzahl deines Monitors.

```
{"placeholder":"guiwidth"}
```

### Bildschirmhöhe

**Kennung:** `guiheight`

Die Höhe des Bildschirms in GUI-Pixeln.

```
{"placeholder":"guiheight"}
```

### GUI-Skalierung

**Kennung:** `guiscale`

Die GUI-Skalierung des Spiels, zum Beispiel `2`.

```
{"placeholder":"guiscale"}
```

### Kennung des aktuellen Bildschirms

**Kennung:** `screenid`

Die [Kennung](/screen-identifiers) des geöffneten Bildschirms, zum Beispiel `title_screen`. Wenn kein Bildschirm geöffnet ist, ist der Wert leer.

```
{"placeholder":"screenid"}
```

### Elementbreite

**Kennung:** `elementwidth`

Die Breite eines Elements in GUI-Pixeln. Wenn kein Element mit dieser ID existiert, wird `1` zurückgegeben.

- `id`: die ID des Elements

```
{"placeholder":"elementwidth","values":{"id":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Elementhöhe

**Kennung:** `elementheight`

Die Höhe eines Elements in GUI-Pixeln. Wenn kein Element mit dieser ID existiert, wird `1` zurückgegeben.

- `id`: die ID des Elements

```
{"placeholder":"elementheight","values":{"id":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### X-Position des Elements

**Kennung:** `elementposx`

Die Position der linken Kante eines Elements in GUI-Pixeln, gemessen vom linken Bildschirmrand. Wenn kein Element mit dieser ID existiert, wird `1` zurückgegeben.

- `id`: die ID des Elements

```
{"placeholder":"elementposx","values":{"id":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Y-Position des Elements

**Kennung:** `elementposy`

Die Position der oberen Kante eines Elements in GUI-Pixeln, gemessen vom oberen Bildschirmrand. Wenn kein Element mit dieser ID existiert, wird `1` zurückgegeben.

- `id`: die ID des Elements

```
{"placeholder":"elementposy","values":{"id":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Inhaltshöhe eines Textelements

**Kennung:** `text_element_content_height`

Wie hoch ein [Textelement](/text-in-menus) sein muss, um seinen gesamten Text ohne Scrollen anzuzeigen, in GUI-Pixeln. Berücksichtigt umbrochene Zeilen, Textskalierung und Zeilenabstand. Daher eignet sich der Wert für Hintergründe, die sich an den Text anpassen. Wenn es sich nicht um ein Textelement handelt, wird `0` zurückgegeben.

- `element_identifier`: die ID des Textelements

```
{"placeholder":"text_element_content_height","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Scrollposition des Elements

**Kennung:** `scroll_area_scroll_position`

Wie weit der Inhalt eines [scrollbaren Bereichs](/scrollable-areas) oder eines Textelements vom Anfang aus gescrollt wurde, in GUI-Pixeln. Bei anderen Elementen ist der Wert `0`.

- `element_identifier`: die ID des Elements
- `axis`: `vertical` oder `horizontal`. Jeder andere Wert bedeutet die Scrollrichtung des Elements.

```
{"placeholder":"scroll_area_scroll_position","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","axis":"vertical"}}
```

### Scrollfortschritt des Elements

**Kennung:** `scroll_area_scroll_percent`

Wie weit der Inhalt eines scrollbaren Bereichs oder eines Textelements gescrollt wurde, von `0` (Anfang) bis `100` (Ende). Bei anderen Elementen und wenn nichts gescrollt werden kann, ist der Wert `0`.

- `element_identifier`: die ID des Elements
- `axis`: `vertical` oder `horizontal`. Jeder andere Wert bedeutet die Scrollrichtung des Elements.

```
{"placeholder":"scroll_area_scroll_percent","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","axis":"vertical"}}
```

### Größe des Scrollinhalts eines Elements

**Kennung:** `scroll_area_content_size`

Die Größe des Inhalts eines scrollbaren Bereichs oder Textelements: bei `vertical` dessen Höhe, bei `horizontal` dessen Breite. Bei anderen Elementen ist der Wert `0`.

- `element_identifier`: die ID des Elements
- `axis`: `vertical` oder `horizontal`. Jeder andere Wert bedeutet die Scrollrichtung des Elements.

```
{"placeholder":"scroll_area_content_size","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","axis":"vertical"}}
```

### Wert eines Texteingabefelds

**Kennung:** `text_input_field_value`

Der Inhalt eines [Texteingabefelds](/elements#text-input-field) oder eines Textfelds des ursprünglichen Bildschirms. Wenn das Element kein Textfeld ist, ist der Wert leer.

- `element_identifier`: die ID des Elements

```
{"placeholder":"text_input_field_value","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Beschriftung/Text eines Vanilla-Widgets

**Kennung:** `vanillabuttonlabel`

Die Beschriftung einer Schaltfläche oder eines anderen Widgets des ursprünglichen Bildschirms, zum Beispiel `Options...`. Klicke im Layout-Editor mit der rechten Maustaste auf das Widget und dann auf **Widget-Locator kopieren**, um seinen Locator zu erhalten.

- `locator`: der Locator des Widgets

```
{"placeholder":"vanillabuttonlabel","values":{"locator":"title_screen:mc_titlescreen_options_button"}}
```

### X-Position der Maus

**Kennung:** `mouseposx`

Die Position der Maus in GUI-Pixeln vom linken Bildschirmrand aus. Im Layout-Editor immer `10`, damit Elemente, die der Maus folgen, an einer bearbeitbaren Stelle bleiben.

```
{"placeholder":"mouseposx"}
```

### Y-Position der Maus

**Kennung:** `mouseposy`

Die Position der Maus in GUI-Pixeln vom oberen Bildschirmrand aus. Im Layout-Editor immer `10`.

```
{"placeholder":"mouseposy"}
```

### Klicks pro Sekunde

**Kennung:** `clicks_per_second`

Wie oft in der letzten Sekunde eine Maustaste geklickt wurde.

- `mouse_button` (optional): `left` oder `right`. Standardmäßig `left`.

```
{"placeholder":"clicks_per_second","values":{"mouse_button":"left"}}
```

## Spieler

### Spielername

**Kennung:** `playername`

Der Name des Spielers, zum Beispiel `Steve`.

```
{"placeholder":"playername"}
```

### Spieler-UUID

**Kennung:** `playeruuid`

Die UUID des Spielers, zum Beispiel `c8cde7fe-7ced-11eb-9439-0242ac130002`.

```
{"placeholder":"playeruuid"}
```

### Letzte Todesnachricht

**Kennung:** `lastdeathmessage`

Die letzte Todesnachricht des Spielers seit dem Spielstart, zum Beispiel `Steve was slain by Zombie`. Vor dem ersten Tod ist der Wert leer.

- `as_json_component` (optional): Mit `true` wird die Nachricht als JSON-Textkomponente mit ihren Farben zurückgegeben. Standardmäßig `false`.

```
{"placeholder":"lastdeathmessage","values":{"as_json_component":"false"}}
```

## Echtzeit

Diese Platzhalter beziehen sich auf die Uhrzeit auf deinem Computer. Bei Datums- und Uhrzeitplatzhaltern ist `timezone` optional: `system` verwendet die Zeitzone des Computers (Standard) oder du gibst eine Kennung wie `UTC`, `Europe/Berlin` oder `America/New_York` an. Alle Kennungen findest du unter [nodatime.org/TimeZones](https://nodatime.org/TimeZones).

### Echtzeit-Jahr

**Kennung:** `realtimeyear`

Das Jahr, zum Beispiel `2026`.

```
{"placeholder":"realtimeyear","values":{"timezone":"system"}}
```

### Echtzeit-Monat

**Kennung:** `realtimemonth`

Der Monat von `01` bis `12`.

```
{"placeholder":"realtimemonth","values":{"timezone":"system"}}
```

### Echtzeit-Tag

**Kennung:** `realtimeday`

Der Tag des Monats von `01` bis `31`.

```
{"placeholder":"realtimeday","values":{"timezone":"system"}}
```

### Echtzeit-Stunde

**Kennung:** `realtimehour`

Die Stunde von `00` bis `23`.

- `twelve_hour_format` (optional): Mit `true` wird stattdessen der Bereich `01` bis `12` verwendet. Standardmäßig `false`.

```
{"placeholder":"realtimehour","values":{"twelve_hour_format":"false","timezone":"Europe/Berlin"}}
```

### Echtzeit-Minute

**Kennung:** `realtimeminute`

Die Minute von `00` bis `59`.

```
{"placeholder":"realtimeminute","values":{"timezone":"system"}}
```

### Echtzeit-Sekunde

**Kennung:** `realtimesecond`

Die Sekunde von `00` bis `59`.

```
{"placeholder":"realtimesecond","values":{"timezone":"system"}}
```

### Aktuelle Zeit in Millisekunden (Unix-Zeitstempel)

**Kennung:** `unix_time`

Die Millisekunden seit dem 1. Januar 1970 (UTC), zum Beispiel `1732456789012`. Praktisch für Timer: Speichere den Wert in einer Variablen und ziehe ihn mit dem Taschenrechner von einem späteren Wert ab.

```
{"placeholder":"unix_time"}
```

## Server

Diese Platzhalter fragen den Status eines Servers ab, ähnlich wie die Serverliste. FancyMenu fragt alle 30 Sekunden nach, solange ein angepasstes Bildschirmmenü geöffnet ist. Bis die erste Antwort eintrifft, gilt der Server als offline.

- `ip`: die Serveradresse, einschließlich Port, wenn nicht der Standardport verwendet wird, zum Beispiel `play.example.net` oder `play.example.net:25566`

### Serverstatus

**Kennung:** `serverstatus`

`Online` in Grün oder `Offline` in Rot.

```
{"placeholder":"serverstatus","values":{"ip":"play.example.net"}}
```

### Spieleranzahl des Servers

**Kennung:** `serverplayercount`

Die Anzahl der Spieler online und die maximale Spielerzahl, zum Beispiel `12/100`. Bis der Server antwortet, wird `0/0` angezeigt.

```
{"placeholder":"serverplayercount","values":{"ip":"play.example.net"}}
```

### Server-MOTD

**Kennung:** `servermotd`

Eine Zeile der Servernachricht des Tages.

- `line`: `1` oder `2`

```
{"placeholder":"servermotd","values":{"ip":"play.example.net","line":"1"}}
```

### Server-PING

**Kennung:** `serverping`

Die Ping-Zeit zum Server in Millisekunden, zum Beispiel `54`. Wenn der Server offline ist, wird `-1` angezeigt.

```
{"placeholder":"serverping","values":{"ip":"play.example.net"}}
```

### Serverversion

**Kennung:** `serverversion`

Die Minecraft-Version des Servers, zum Beispiel `1.21.1`. Manche Server zeigen hier einen eigenen Text an. Bis der Server antwortet, wird `---` angezeigt.

```
{"placeholder":"serverversion","values":{"ip":"play.example.net"}}
```

## Video

Diese Platzhalter lesen [Videoelemente und Videomenühintergründe](/video) des geöffneten Menüs aus. Klicke bei Videoelementen im Layout-Editor mit der rechten Maustaste auf ein Element und dann auf **Element-ID kopieren**. Für Hintergründe klickst du mit der rechten Maustaste auf den Editorhintergrund und wählst **Hintergrundkennung kopieren**.

### Lautstärke des Videoelements

**Kennung:** `video_element_vol`

Die Lautstärke eines Videoelements von `0.0` (0 %) bis `1.0` (100 %).

- `element_identifier`: die ID des Videoelements

```
{"placeholder":"video_element_vol","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Dauer des Videoelements

**Kennung:** `video_element_duration`

Die Dauer des Videos eines Videoelements, zum Beispiel `02:00`. Während des Ladens wird `00:00` (oder `0`) angezeigt.

- `element_identifier`: die ID des Videoelements
- `output_as_timestamp` (optional): Mit `true` werden stattdessen Millisekunden zurückgegeben, zum Beispiel `120000`. Standardmäßig `false`.

```
{"placeholder":"video_element_duration","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","output_as_timestamp":"false"}}
```

### Wiedergabezeit des Videoelements

**Kennung:** `video_element_playtime`

Die aktuelle Position im Video eines Videoelements, zum Beispiel `00:45`. Während des Ladens wird `00:00` (oder `0`) angezeigt.

- `element_identifier`: die ID des Videoelements
- `show_percentage` (optional): Mit `true` wird der Fortschritt von `0` bis `100` zurückgegeben. Standardmäßig `false`.
- `output_as_timestamp` (optional): Mit `true` werden Millisekunden zurückgegeben. Wenn beide Werte `true` sind, hat `show_percentage` Vorrang. Standardmäßig `false`.

```
{"placeholder":"video_element_playtime","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","show_percentage":"false","output_as_timestamp":"false"}}
```

### Pausenzustand des Videoelements

**Kennung:** `video_element_paused_state`

`true`, solange ein Videoelement pausiert ist, andernfalls `false`.

- `element_identifier`: die ID des Videoelements

```
{"placeholder":"video_element_paused_state","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Lautstärke des Videohintergrunds

**Kennung:** `video_background_vol`

Die Lautstärke eines Videomenühintergrunds von `0.0` (0 %) bis `1.0` (100 %).

- `background_identifier`: die Kennung des Menühintergrunds

```
{"placeholder":"video_background_vol","values":{"background_identifier":"8c2e4f6a-1b3d-4e5f-8a7b-9c0d1e2f3a4b-1732456789012"}}
```

### Dauer des Videohintergrunds

**Kennung:** `video_background_duration`

Die Dauer des Videos eines Menühintergrunds, zum Beispiel `03:00`. Während des Ladens wird `00:00` (oder `0`) angezeigt.

- `background_identifier`: die Kennung des Menühintergrunds
- `output_as_timestamp` (optional): Mit `true` werden stattdessen Millisekunden zurückgegeben. Standardmäßig `false`.

```
{"placeholder":"video_background_duration","values":{"background_identifier":"8c2e4f6a-1b3d-4e5f-8a7b-9c0d1e2f3a4b-1732456789012","output_as_timestamp":"false"}}
```

### Wiedergabezeit des Videohintergrunds

**Kennung:** `video_background_playtime`

Die aktuelle Position im Video eines Menühintergrunds, zum Beispiel `01:00`. Während des Ladens wird `00:00` (oder `0`) angezeigt.

- `background_identifier`: die Kennung des Menühintergrunds
- `show_percentage` (optional): Mit `true` wird der Fortschritt von `0` bis `100` zurückgegeben. Standardmäßig `false`.
- `output_as_timestamp` (optional): Mit `true` werden Millisekunden zurückgegeben. Wenn beide Werte `true` sind, hat `show_percentage` Vorrang. Standardmäßig `false`.

```
{"placeholder":"video_background_playtime","values":{"background_identifier":"8c2e4f6a-1b3d-4e5f-8a7b-9c0d1e2f3a4b-1732456789012","show_percentage":"true","output_as_timestamp":"false"}}
```

### Pausenzustand des Videohintergrunds

**Kennung:** `video_background_paused_state`

`true`, solange ein Videomenühintergrund pausiert ist, andernfalls `false`.

- `background_identifier`: die Kennung des Menühintergrunds

```
{"placeholder":"video_background_paused_state","values":{"background_identifier":"8c2e4f6a-1b3d-4e5f-8a7b-9c0d1e2f3a4b-1732456789012"}}
```

## Welt: Spielerwerte

Die Kategorie **Welt** bezieht sich auf die Welt, in der du spielst. Die meisten ihrer Platzhalter benötigen eine geladene Welt. Außerhalb einer Welt geben sie `0`, `0.0` oder nichts zurück.

### Aktuelle Spielergesundheit

**Kennung:** `current_player_health`

Die Gesundheit des Spielers, zum Beispiel `20.0`. Jedes Herz entspricht `2.0`.

```
{"placeholder":"current_player_health"}
```

### Maximale Spielergesundheit

**Kennung:** `max_player_health`

Die maximale Gesundheit des Spielers, zum Beispiel `20.0`.

```
{"placeholder":"max_player_health"}
```

### Aktuelle Spielergesundheit (Prozent)

**Kennung:** `current_player_health_percent`

Die Gesundheit des Spielers in Prozent von `0` bis `100`.

```
{"placeholder":"current_player_health_percent"}
```

### Aktuelle Absorptionsgesundheit des Spielers

**Kennung:** `current_player_absorption_health`

Die Absorptionsgesundheit des Spielers (die goldenen Herzen), zum Beispiel `4.0`.

```
{"placeholder":"current_player_absorption_health"}
```

### Maximale Absorptionsgesundheit des Spielers

**Kennung:** `max_player_absorption_health`

Die maximale Absorptionsgesundheit des Spielers, zum Beispiel `4.0`.

```
{"placeholder":"max_player_absorption_health"}
```

### Aktuelle Absorptionsgesundheit des Spielers (Prozent)

**Kennung:** `current_player_absorption_health_percent`

Die Absorptionsgesundheit des Spielers in Prozent von `0` bis `100`.

```
{"placeholder":"current_player_absorption_health_percent"}
```

### Aktueller Hungerwert des Spielers

**Kennung:** `current_player_hunger`

Der Hungerwert des Spielers von `0.0` bis `20.0`.

```
{"placeholder":"current_player_hunger"}
```

### Maximaler Hungerwert des Spielers

**Kennung:** `max_player_hunger`

Der maximale Hungerwert von Spielern: immer `20.0`.

```
{"placeholder":"max_player_hunger"}
```

### Aktueller Hungerwert des Spielers (Prozent)

**Kennung:** `current_player_hunger_percent`

Der Hungerwert des Spielers in Prozent von `0` bis `100`.

```
{"placeholder":"current_player_hunger_percent"}
```

### Aktuelle Hungersättigung des Spielers

**Kennung:** `current_player_hunger_saturation`

Die Sättigung des Spielers, zum Beispiel `5.0`. Der Hunger nimmt erst ab, wenn die Sättigung aufgebraucht ist.

```
{"placeholder":"current_player_hunger_saturation"}
```

### Aktuelle Rüstung des Spielers

**Kennung:** `current_player_armor`

Die Rüstungspunkte des Spielers von `0.0` bis `20.0`.

```
{"placeholder":"current_player_armor"}
```

### Maximale Rüstung des Spielers

**Kennung:** `max_player_armor`

Die maximalen Rüstungspunkte der Rüstungsleiste: immer `20.0`.

```
{"placeholder":"max_player_armor"}
```

### Aktuelle Rüstung des Spielers (Prozent)

**Kennung:** `current_player_armor_percent`

Die Rüstungspunkte des Spielers in Prozent von `0` bis `100`.

```
{"placeholder":"current_player_armor_percent"}
```

### Rüstungshärte des Spielers

**Kennung:** `player_armor_toughness`

Die Rüstungshärte des Spielers, zum Beispiel `8.0` bei vollständiger Diamantrüstung.

```
{"placeholder":"player_armor_toughness"}
```

### Aktueller Sauerstoffwert des Spielers

**Kennung:** `current_player_oxygen`

Die Luft des Spielers unter Wasser von `0.0` bis `300.0`.

```
{"placeholder":"current_player_oxygen"}
```

### Maximaler Sauerstoffwert des Spielers

**Kennung:** `max_player_oxygen`

Die maximale Luft des Spielers, zum Beispiel `300.0`.

```
{"placeholder":"max_player_oxygen"}
```

### Aktueller Sauerstoffwert des Spielers (Prozent)

**Kennung:** `current_player_oxygen_percent`

Die Luft des Spielers in Prozent von `0` bis `100`.

```
{"placeholder":"current_player_oxygen_percent"}
```

### Aktuelle Spielerstufe

**Kennung:** `current_player_level`

Die Erfahrungsstufe des Spielers, zum Beispiel `30`.

```
{"placeholder":"current_player_level"}
```

### Aktuelle Spielererfahrung

**Kennung:** `current_player_exp`

Die gesamten Erfahrungspunkte des Spielers, zum Beispiel `1395.0`. Dies ist nicht die Stufe.

```
{"placeholder":"current_player_exp"}
```

### Erfahrungsfortschritt des Spielers (Prozent)

**Kennung:** `current_player_exp_progress`

Wie voll die Erfahrungsleiste ist, von `0` bis `100`.

```
{"placeholder":"current_player_exp_progress"}
```

### Angriffsstärke des Spielers (Prozent)

**Kennung:** `player_attack_strength`

Wie weit der nächste Angriff aufgeladen ist, von `0` bis `100`, wie beim Angriffsindikator.

```
{"placeholder":"player_attack_strength"}
```

### Spielmodus des Spielers

**Kennung:** `player_gamemode`

`survival`, `creative`, `adventure` oder `spectator`.

```
{"placeholder":"player_gamemode"}
```

### Fortschritt bei der Verwendung eines Gegenstands (FM)

**Kennung:** `player_item_use_progress_fm`

Wie weit der Spieler mit der Verwendung eines Gegenstands ist, etwa beim Essen, Trinken oder Spannen eines Bogens, von `0.0` bis `1.0`.

```
{"placeholder":"player_item_use_progress_fm"}
```

### Aktuelle Gesundheit des Reittiers

**Kennung:** `current_mount_health`

Die Gesundheit des Mobs, auf dem der Spieler reitet, zum Beispiel eines Pferdes: etwa `30.0`.

```
{"placeholder":"current_mount_health"}
```

### Maximale Gesundheit des Reittiers

**Kennung:** `max_mount_health`

Die maximale Gesundheit des Mobs, auf dem der Spieler reitet.

```
{"placeholder":"max_mount_health"}
```

### Aktuelle Gesundheit des Reittiers (Prozent)

**Kennung:** `current_mount_health_percent`

Die Gesundheit des Mobs, auf dem der Spieler reitet, in Prozent von `0` bis `100`.

```
{"placeholder":"current_mount_health_percent"}
```

### Aktuelle Sprunganzeige des Reittiers (Prozent)

**Kennung:** `current_mount_jump_meter`

Wie weit der Sprung eines Pferdes aufgeladen ist, von `0` bis `100`.

```
{"placeholder":"current_mount_jump_meter"}
```

### Anzahl aktiver Effekte

**Kennung:** `effects_count`

Wie viele Effekte der Spieler gerade hat.

```
{"placeholder":"effects_count"}
```

### Aktiver Effekt

**Kennung:** `active_effect`

Die ID eines Effekts des Spielers, zum Beispiel `minecraft:speed`, in der Reihenfolge der Effekticons oben rechts. Wenn an diesem Index kein Effekt vorhanden ist, bleibt der Wert leer.

- `effect_index`: die Position des Effekts. Der erste hat den Index `0`.

```
{"placeholder":"active_effect","values":{"effect_index":"0"}}
```

## Welt: Inventar und Gegenstände

Diese Platzhalter gehören zur Kategorie **Welt**. Slotnummern: `0` bis `8` sind die Schnellleiste, `9` bis `35` der restliche Inventarbereich, `36` bis `39` die Rüstung von Stiefeln bis Helm und `40` die Zweithand.

### Ausgewählter Schnellleisten-Slot

**Kennung:** `active_hotbar_slot`

Der ausgewählte Slot der Schnellleiste von `0` bis `8`.

```
{"placeholder":"active_hotbar_slot"}
```

### Gegenstand im Slot

**Kennung:** `slot_item`

Die ID des Gegenstands in einem Slot, zum Beispiel `minecraft:diamond_sword`. Leere Slots geben `minecraft:air` zurück.

- `slot`: die Slotnummer

```
{"placeholder":"slot_item","values":{"slot":"0"}}
```

### Anzahl der Gegenstände im Slot

**Kennung:** `slot_item_count`

Wie viele Gegenstände sich in einem Slot befinden, zum Beispiel `64`.

- `slot`: die Slotnummer

```
{"placeholder":"slot_item_count","values":{"slot":"0"}}
```

### Haltbarkeit des Gegenstands im Slot

**Kennung:** `slot_item_durability`

Die Haltbarkeit des Gegenstands in einem Slot. Bei Gegenständen ohne Haltbarkeit wird `0` zurückgegeben.

- `slot`: die Slotnummer
- `format` (optional): `current` (verbleibende Haltbarkeit), `max`, `damage` (verbrauchte Haltbarkeit) oder `percentage` (verbleibend, von `0` bis `100`). Standardmäßig `current`.

```
{"placeholder":"slot_item_durability","values":{"slot":"39","format":"percentage"}}
```

### Anzeigename des Gegenstands im Slot (FM)

**Kennung:** `slot_item_display_name_fm`

Der Name des Gegenstands in einem Slot als JSON-Textkomponente mit seiner Seltenheitsfarbe, zum Beispiel `{"text":"Diamond Sword","color":"aqua"}`. Im Zuschauermodus geben Schnellleisten-Slots die Namen des Zuschauermenüs zurück.

- `slot`: die Slotnummer
- `ignore_spectator` (optional): Mit `true` werden die Gegenstandsnamen auch im Zuschauermodus ausgegeben. Standardmäßig `false`.

```
{"placeholder":"slot_item_display_name_fm","values":{"slot":"0","ignore_spectator":"false"}}
```

### Anzahl eines Gegenstands im Inventar

**Kennung:** `inventory_item_count`

Wie viele Exemplare eines Gegenstands der Spieler im gesamten Inventar hat.

- `item`: die ID des Gegenstands, zum Beispiel `minecraft:diamond`. Bei leerem Wert werden alle Gegenstände gezählt.

```
{"placeholder":"inventory_item_count","values":{"item":"minecraft:diamond"}}
```

### Nahrungswert eines Gegenstands im Inventarslot

**Kennung:** `inventory_slot_food_point_restore_amount`

Wie viele Hungerpunkte der Gegenstand in einem Slot beim Essen wiederherstellt, zum Beispiel `4.0` bei einem Apfel. Bei Gegenständen, die keine Nahrung sind, wird `0.0` zurückgegeben.

- `slot`: die Slotnummer

```
{"placeholder":"inventory_slot_food_point_restore_amount","values":{"slot":"0"}}
```

### Gegenstandskategorie

**Kennung:** `item_category`

Der Kreativinventar-Reiter eines Gegenstands, zum Beispiel `Combat`. Bei Gegenständen ohne Reiter wird `UNKNOWN` zurückgegeben.

- `item`: die ID des Gegenstands
- `as_key` (optional): Mit `true` wird die ID des Reiters zurückgegeben, zum Beispiel `minecraft:combat`. Standardmäßig `false`.

```
{"placeholder":"item_category","values":{"item":"minecraft:diamond_sword","as_key":"false"}}
```

### Gegenstand unter dem Mauszeiger im Inventar

**Kennung:** `hovered_inventory_item`

Die ID des Gegenstands, über dem sich die Maus in einem Inventarbildschirm befindet, zum Beispiel `minecraft:apple`. Wenn kein Gegenstand darunterliegt, ist der Wert leer.

```
{"placeholder":"hovered_inventory_item"}
```

## Welt: HUD und Bosse

Diese Platzhalter gehören zur Kategorie **Welt**. Die Raid-Platzhalter lesen den Raid aus, dessen Leiste oben auf dem Bildschirm angezeigt wird, und benötigen FancyMenu auf dem Server. Im Einzelspielermodus funktionieren sie immer. Wenn kein Raid aktiv ist, geben sie `0` oder nichts zurück.

### Aktionsleisten-Nachricht (FM)

**Kennung:** `action_bar_message_fm`

Die Nachricht über der Schnellleiste als JSON-Textkomponente, zum Beispiel `{"text":"You may not rest now","color":"red"}`. Wenn keine Nachricht angezeigt wird, ist der Wert leer.

```
{"placeholder":"action_bar_message_fm"}
```

### Anzeigedauer der Aktionsleisten-Nachricht (FM)

**Kennung:** `action_bar_message_time_fm`

Wie viele Ticks die Nachricht über der Schnellleiste noch angezeigt wird. 20 Ticks entsprechen einer Sekunde.

```
{"placeholder":"action_bar_message_time_fm"}
```

### Anzeigedauer des hervorgehobenen Gegenstands (FM)

**Kennung:** `highlighted_item_time_fm`

Wie viele Ticks der Name des ausgewählten Gegenstands noch über der Schnellleiste angezeigt wird.

```
{"placeholder":"highlighted_item_time_fm"}
```

### Aktueller HUD-Titel/Untertitel

**Kennung:** `current_title`

Der Titel oder Untertitel, der gerade angezeigt wird, zum Beispiel von `/title`. Wenn keiner angezeigt wird, ist der Wert leer.

- `is_subtitle` (optional): Mit `true` wird der Untertitel zurückgegeben. Standardmäßig `false`.
- `as_json` (optional): Mit `true` wird der Text als JSON-Textkomponente zurückgegeben. Standardmäßig `false`.

```
{"placeholder":"current_title","values":{"is_subtitle":"false","as_json":"false"}}
```

### Anzahl der Bossleisten

**Kennung:** `boss_count`

Wie viele Bossleisten gerade angezeigt werden.

```
{"placeholder":"boss_count"}
```

### Bossname

**Kennung:** `boss_name`

Der Name einer Bossleiste, zum Beispiel `Ender Dragon`. Wenn an diesem Index keine Bossleiste existiert, ist der Wert leer.

- `boss_index`: die Position der Bossleiste. Die oberste hat den Index `0`.
- `as_json` (optional): Mit `true` wird der Name als JSON-Textkomponente zurückgegeben. Standardmäßig `false`.

```
{"placeholder":"boss_name","values":{"boss_index":"0","as_json":"false"}}
```

### Aktuelle Bossgesundheit (Prozent)

**Kennung:** `current_boss_health`

Wie voll eine Bossleiste ist, von `0` bis `100`.

- `boss_index`: die Position der Bossleiste. Die oberste hat den Index `0`.

```
{"placeholder":"current_boss_health","values":{"boss_index":"0"}}
```

### Gesamtzahl der aktiven Raidwellen

**Kennung:** `active_raid_total_waves`

Wie viele Wellen der Raid einschließlich der Bonuswelle hat.

```
{"placeholder":"active_raid_total_waves"}
```

### Verbleibende aktive Raidwellen

**Kennung:** `active_raid_remaining_waves`

Wie viele Wellen des Raids noch ausstehen.

```
{"placeholder":"active_raid_remaining_waves"}
```

### Aktuelle aktive Raidwelle

**Kennung:** `active_raid_current_wave`

Die Nummer der zuletzt gestarteten Welle. Während des Angriffs der ersten Welle ist der Wert also `1`. Vor der ersten Welle ist er `0`.

```
Wave {"placeholder":"active_raid_current_wave"} of {"placeholder":"active_raid_total_waves"}
```

### Anzahl lebender Plünderer im aktiven Raid

**Kennung:** `active_raid_alive_raiders_count`

Wie viele Plünderer des Raids noch am Leben sind.

```
{"placeholder":"active_raid_alive_raiders_count"}
```

### Liste lebender Plünderer im aktiven Raid

**Kennung:** `active_raid_alive_raiders_list`

Alle noch lebenden Plünderer, durch Kommas getrennt. Jeder Eintrag enthält die Mob-ID und die UUID des Plünderers, zum Beispiel `minecraft:pillager#0d9a4b2e-5f1c-4a8e-9b3d-6c2f1e7a8b90`.

```
{"placeholder":"active_raid_alive_raiders_list"}
```

## Welt: Position und Kamera

Diese Platzhalter gehören zur Kategorie **Welt**.

### X-Koordinate des Spielers

**Kennung:** `player_x_coordinate`

Die X-Koordinate des Blocks, in dem der Spieler steht, zum Beispiel `125`.

```
{"placeholder":"player_x_coordinate"}
```

### Y-Koordinate des Spielers

**Kennung:** `player_y_coordinate`

Die Y-Koordinate des Blocks, in dem der Spieler steht, zum Beispiel `64`.

```
{"placeholder":"player_y_coordinate"}
```

### Z-Koordinate des Spielers

**Kennung:** `player_z_coordinate`

Die Z-Koordinate des Blocks, in dem der Spieler steht, zum Beispiel `-250`.

```
{"placeholder":"player_z_coordinate"}
```

### Blickrichtung des Spielers

**Kennung:** `player_view_direction`

Die Blickrichtung des Spielers: `north`, `east`, `south` oder `west`.

```
{"placeholder":"player_view_direction"}
```

### Positionsänderung des Spielers auf der X-Achse (FM)

**Kennung:** `player_position_delta_x_fm`

Wie weit sich der Spieler seit dem letzten Tick entlang der X-Achse bewegt hat, in Blöcken, zum Beispiel `0.12`. Bei Bewegung in die entgegengesetzte Richtung ist der Wert negativ.

```
{"placeholder":"player_position_delta_x_fm"}
```

### Positionsänderung des Spielers auf der Y-Achse (FM)

**Kennung:** `player_position_delta_y_fm`

Wie weit sich der Spieler seit dem letzten Tick entlang der Y-Achse bewegt hat, zum Beispiel `-0.08` beim Fallen.

```
{"placeholder":"player_position_delta_y_fm"}
```

### Positionsänderung des Spielers auf der Z-Achse (FM)

**Kennung:** `player_position_delta_z_fm`

Wie weit sich der Spieler seit dem letzten Tick entlang der Z-Achse bewegt hat.

```
{"placeholder":"player_position_delta_z_fm"}
```

### X-Drehung der Kamera (FM)

**Kennung:** `camera_rotation_x_fm`

Wie weit die Kamera nach oben oder unten blickt, in Grad von `-90.0` (gerade nach oben) bis `90.0` (gerade nach unten).

```
{"placeholder":"camera_rotation_x_fm"}
```

### Y-Drehung der Kamera (FM)

**Kennung:** `camera_rotation_y_fm`

In welche Richtung die Kamera blickt, in Grad von `-180.0` bis `180.0`. `0.0` entspricht Süden.

```
{"placeholder":"camera_rotation_y_fm"}
```

### Änderung der X-Kameradrehung (FM)

**Kennung:** `camera_rotation_delta_x_fm`

Wie weit die Kamera seit dem letzten Tick nach oben oder unten gedreht wurde, in Grad.

```
{"placeholder":"camera_rotation_delta_x_fm"}
```

### Änderung der Y-Kameradrehung (FM)

**Kennung:** `camera_rotation_delta_y_fm`

Wie weit die Kamera seit dem letzten Tick nach links oder rechts gedreht wurde, in Grad.

```
{"placeholder":"camera_rotation_delta_y_fm"}
```

## Welt: Weltinformationen

Diese Platzhalter gehören zur Kategorie **Welt**.

### Tageszeit der Welt

**Kennung:** `world_daytime`

Die Tageszeit der Welt in Ticks. Ein Tag hat 24000 Ticks und beginnt um 6:00 Uhr morgens. Der Wert zählt von Tag zu Tag weiter. Mit `{"placeholder":"world_daytime"} % 24000` im Taschenrechner erhältst du die Uhrzeit des aktuellen Tages.

```
{"placeholder":"world_daytime"}
```

### Stunde der Tageszeit in der Welt

**Kennung:** `world_daytime_hour`

Die Stunde der Tageszeit der Welt von `00` bis `23`.

- `twelve_hour_format` (optional): Mit `true` wird stattdessen der Bereich `01` bis `12` verwendet. Standardmäßig `false`.

```
{"placeholder":"world_daytime_hour","values":{"twelve_hour_format":"false"}}
```

### Minute der Tageszeit in der Welt

**Kennung:** `world_daytime_minute`

Die Minute der Tageszeit der Welt von `00` bis `59`.

```
{"placeholder":"world_daytime_hour"}:{"placeholder":"world_daytime_minute"}
```

### Spielzeit der Welt

**Kennung:** `game_time`

Wie viele Ticks die Welt insgesamt gelaufen ist. Anders als die Tageszeit wird dieser Wert durch Befehle wie `/time set` nicht verändert.

```
{"placeholder":"game_time"}
```

### Schwierigkeitsgrad der Welt

**Kennung:** `world_difficulty`

`peaceful`, `easy`, `normal` oder `hard`.

```
{"placeholder":"world_difficulty"}
```

### Aktuelle Dimension

**Kennung:** `current_dimension`

Die Dimension, in der sich der Spieler befindet, zum Beispiel `minecraft:overworld`.

- `as_key` (optional): Mit `false` wird ihr Name zurückgegeben, zum Beispiel `Overworld`. Dimensionen ohne Namen geben ihre ID zurück. Standardmäßig `true`.

```
{"placeholder":"current_dimension","values":{"as_key":"false"}}
```

### Aktuelles Biom

**Kennung:** `current_biome`

Das Biom, in dem sich der Spieler befindet, zum Beispiel `minecraft:plains`.

- `as_key` (optional): Mit `false` wird der Name zurückgegeben, zum Beispiel `Plains`. Standardmäßig `true`.

```
{"placeholder":"current_biome","values":{"as_key":"false"}}
```

### Aktueller Welt-Seed

**Kennung:** `current_world_seed`

Der Seed der Einzelspielerwelt, zum Beispiel `-4172144997902289642`. Auf Servern ist der Wert leer.

```
{"placeholder":"current_world_seed"}
```

### Gamerule-Wert

**Kennung:** `gamerule_value`

Der Wert einer Spielregel, zum Beispiel `true` oder `3`. Im Einzelspielermodus funktioniert der Platzhalter immer. Auf Servern muss FancyMenu auf dem Server installiert sein. Wenn keine Spielregel mit diesem Namen existiert, ist der Wert leer.

- `name`: der Name der Spielregel, zum Beispiel `keep_inventory`. In Minecraft 1.21.10 und älteren Versionen heißen Spielregeln etwa `keepInventory`; diese alten Namen funktionieren auch in neueren Versionen.

```
{"placeholder":"gamerule_value","values":{"name":"keep_inventory"}}
```

### IP des aktuellen Servers

**Kennung:** `current_server_ip`

Die Adresse des Servers, auf dem sich der Spieler befindet, zum Beispiel `play.example.net`. Im Einzelspielermodus ist der Wert leer.

```
{"placeholder":"current_server_ip"}
```

### Spielerliste der Welt

**Kennung:** `world_players_list`

Die Namen der Spieler in der Welt, die deinem Spiel bekannt sind, alphabetisch sortiert, zum Beispiel `Alex, Notch, Steve`.

- `separator` (optional): der Text zwischen den Namen. Standardmäßig `, `.

```
{"placeholder":"world_players_list","values":{"separator":", "}}
```

## Welt: Weltstände

Diese Platzhalter gehören zur Kategorie **Welt** und funktionieren in jedem Menü, auch wenn keine Welt geladen ist.

### Anzahl der Weltstände

**Kennung:** `level_save_count`

Wie viele Einzelspielerwelten es gibt.

```
{"placeholder":"level_save_count"}
```

### Namen der Weltstände

**Kennung:** `level_save_names`

Die Namen aller Einzelspielerwelten in der Reihenfolge der Weltliste, zum Beispiel `Survival World, Creative Test`.

- `separator` (optional): der Text zwischen den Namen. Standardmäßig `, `.

```
{"placeholder":"level_save_names","values":{"separator":", "}}
```

### Daten eines Weltstands

**Kennung:** `level_save_data`

Alle Daten einer Einzelspielerwelt als JSON, zum Beispiel `{"file_name":"Survival World","game_type":"survival","difficulty":"normal",...}`. Dazu gehören unter anderem `file_name`, `display_name`, `game_type`, `difficulty`, `allow_commands`, `last_played` (als Unix-Zeitstempel), `minecraft_version_name` und weitere Werte. Einzelne Werte lassen sich mit [**JSON-Parser**](#json-parser) auslesen.

- `level_name`: der Name der Welt, genau wie in der Weltliste

```
{"placeholder":"json","values":{"source":"{"placeholder":"level_save_data","values":{"level_name":"Survival World"}}","json_path":"$.game_type"}}
```

## Sonstiges

Diese Platzhalter haben keine Kategorie und werden daher im Platzhaltermenü unterhalb der Kategorien aufgelistet.

### FPS (Bilder pro Sekunde)

**Kennung:** `fps`

Die Bilder pro Sekunde, zum Beispiel `120`.

```
{"placeholder":"fps"}
```

### Verwendeter RAM in MB

**Kennung:** `usedram`

Der RAM, den das Spiel gerade verwendet, in MB, zum Beispiel `4096`.

```
{"placeholder":"usedram"}
```

### Maximaler RAM in MB

**Kennung:** `maxram`

Der maximale RAM, den das Spiel verwenden kann, in MB, zum Beispiel `8192`.

```
{"placeholder":"maxram"}
```

### Verwendeter RAM in %

**Kennung:** `percentram`

Der vom Spiel verwendete RAM als Prozentsatz des maximalen RAM, zum Beispiel `50`.

```
{"placeholder":"percentram"}
```

### CPU-Auslastung (JVM)

**Kennung:** `jvmcpu`

Wie viel CPU-Leistung das Spiel verwendet, in Prozent, zum Beispiel `25.5`.

```
{"placeholder":"jvmcpu"}
```

### CPU-Auslastung (Betriebssystem)

**Kennung:** `oscpu`

Wie stark der gesamte Computer ausgelastet ist, in Prozent, zum Beispiel `42.8`.

```
{"placeholder":"oscpu"}
```

### CPU-Informationen

**Kennung:** `cpuinfo`

Der Name der CPU, zum Beispiel `Intel(R) Core(TM) i7-10700K CPU @ 3.80GHz`.

```
{"placeholder":"cpuinfo"}
```

### GPU-Informationen

**Kennung:** `gpuinfo`

Der Name der Grafikeinheit, die das Spiel verwendet, zum Beispiel `NVIDIA GeForce RTX 3080`.

```
{"placeholder":"gpuinfo"}
```

### OpenGL-Version

**Kennung:** `glver`

Die Treiberinformationen der Grafikeinheit, die das Spiel verwendet, zum Beispiel `4.6.0 NVIDIA 566.36`.

```
{"placeholder":"glver"}
```

### Java-Version

**Kennung:** `javaver`

Die Java-Version, mit der das Spiel ausgeführt wird, zum Beispiel `21.0.5`.

```
{"placeholder":"javaver"}
```

### Java Virtual Machine

**Kennung:** `jvmname`

Der Name der Java Virtual Machine, zum Beispiel `OpenJDK 64-Bit Server VM`.

```
{"placeholder":"jvmname"}
```

### Betriebssystemname

**Kennung:** `osname`

Der Name des Betriebssystems, zum Beispiel `Windows 11`.

```
{"placeholder":"osname"}
```

### Laufzeit

**Kennung:** `uptime_duration`

Wie lange das Spiel läuft, in Sekunden, zum Beispiel `742`.

- `output_as_millis` (optional): Mit `true` werden stattdessen Millisekunden zurückgegeben. Standardmäßig `false`.

```
{"placeholder":"uptime_duration","values":{"output_as_millis":"false"}}
```

### Zufallstext

**Kennung:** `randomtext`

Eine zufällige Zeile aus einer Textdatei, einer URL oder einem von dir eingegebenen Text, etwa ein zufälliger Tipp. Dateien und URLs werden alle 30 Sekunden erneut gelesen.

- `source`: eine `.txt`-Datei im Spielordner, eine URL oder durch `\n` getrennte Zeilen, zum Beispiel `Tip 1\nTip 2\nTip 3`
- `interval` (optional): nach wie vielen Sekunden eine neue Zeile ausgewählt wird. Mit `0` wird eine Zeile pro Spielsitzung ausgewählt. Standardmäßig `10`.

```
{"placeholder":"randomtext","values":{"source":"/config/fancymenu/assets/tips.txt","interval":"10"}}
```

### Webtext

**Kennung:** `webtext`

Die erste Textzeile einer Webseite, zum Beispiel einer Textdatei auf deiner Website. Der Inhalt wird einmal geladen und erneut, wenn FancyMenu neu geladen wird. Während des Ladens ist der Wert leer.

- `link`: die URL der Seite

```
{"placeholder":"webtext","values":{"link":"https://example.com/motd.txt"}}
```

### Absoluter Datei-/Ordnerpfad

**Kennung:** `absolute_path`

Der vollständige Pfad einer Datei oder eines Ordners im Spielordner, zum Beispiel `C:/Users/Steve/AppData/Roaming/.minecraft/config/fancymenu`.

- `short_path`: der Pfad innerhalb des Spielordners

```
{"placeholder":"absolute_path","values":{"short_path":"config/fancymenu"}}
```

### Anzahl der Textzeichen

**Kennung:** `text_character_count`

Wie viele Zeichen ein Text hat: `Hello World!` hat `12` Zeichen.

- `text`: der Text

```
{"placeholder":"text_character_count","values":{"text":"$$player_nickname"}}
```

### Textbreite

**Kennung:** `text_width`

Wie breit ein Text in GUI-Pixeln ist: `Hello World!` ist `57` Pixel breit. Formatierungscodes wie `&l` werden wie im Spiel berücksichtigt, daher ist fetter Text breiter.

- `text`: der Text

```
{"placeholder":"text_width","values":{"text":"Hello World!"}}
```

### Texthöhe

**Kennung:** `text_height`

Wie hoch ein Text mit all seinen Zeilen in GUI-Pixeln ist. Zeilenumbrüche werden mit `\n` angegeben. Um die Höhe an ein Textelement anzupassen, verwende [**Inhaltshöhe eines Textelements**](#text-element-content-height); dieser Platzhalter berücksichtigt auch Textskalierung, Zeilenabstand und umbrochene Zeilen.

- `text`: der Text

```
{"placeholder":"text_height","values":{"text":"First line\nSecond line"}}
```

### Inhalt der Zwischenablage

**Kennung:** `clipboard_content`

Der Text in der Zwischenablage deines Computers. Wenn sie leer ist, wird nichts zurückgegeben.

```
{"placeholder":"clipboard_content"}
```
