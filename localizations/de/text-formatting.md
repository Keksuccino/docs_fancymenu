---
title: Textformatierung
description: >-
  So formatierst du Text mit Markdown, Minecraft-Formatierungscodes und
  Textkomponenten.
sourceBlobSha: c6ddde5939e929b3d4c04541f0b104ee6ee795bc
---
# Textformatierung

FancyMenu bietet dir drei Möglichkeiten, Text zu formatieren:

- **Markdown** für [Text- und Tooltip-Elemente](/text-in-menus): Überschriften, Listen, Farben, Bilder, Tabellen und mehr.
- **Minecraft-Formatierungscodes** wie `&c` für schnelle Farbänderungen. Sie funktionieren in fast jedem Textfeld, auch in Markdown-Text.
- **Minecraft-Textkomponenten** für Beschriftungen von Buttons und Schiebereglern.

> [!TIP]
> Auf dieser Seite geht es darum, *wie du* formatierten Text schreibst. Wie du Text zu deinen Menüs hinzufügst, sein Aussehen änderst oder ihn scrollen lässt, erfährst du unter [Text in Menüs](/text-in-menus).

<img width="800" alt="Markdown in einem Textelement" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/markdown_showcase.png?raw=true">

# Markdown

Markdown formatiert Text mithilfe einiger Sonderzeichen. Zum Beispiel wird `**fett**` als **fetter** Text dargestellt.

Markdown funktioniert in [Textelementen](/elements#text) und [Tooltip-Elementen](/elements#tooltip). Die Zeichen, die du schreibst, bestimmen, *was* etwas ist (eine Überschrift, eine Liste, ein Zitat). Das [Aussehen](/text-in-menus#looks-and-styles) des Elements bestimmt, wie es dargestellt wird, zum Beispiel mit welchen Farben und Größen.

## Schnellübersicht

| Du schreibst | Du erhältst |
|---|---|
| `**fett**` oder `__fett__` | Fetter Text |
| `*kursiv*` oder `_kursiv_` | Kursiver Text |
| `++unterstrichen++` | Unterstrichener Text |
| `~~durchgestrichen~~` | Durchgestrichener Text |
| `` `Code` `` | Inline-Code |
| `[Website öffnen](https://example.com)` | Einen anklickbaren Link |
| `%#ff5555%roter Text%#%` | Farbigen Text |
| `# Überschrift` | Eine Überschrift |
| `- Eintrag` | Eine Aufzählungsliste |
| `1. Eintrag` | Eine nummerierte Liste |
| `> Text` | Ein Zitat |
| `> [!TIP]` | Eine Hinweisbox |
| `---` | Eine Trennlinie |

## Textstile

| Stil | So schreibst du ihn |
|---|---|
| **Fett** | `**Text**` oder `__Text__` |
| **Kursiv** | `*Text*` oder `_Text_` |
| **Unterstrichen** | `++Text++` |
| **Durchgestrichen** | `~~Text~~` (ein einzelnes `~` auf beiden Seiten funktioniert ebenfalls) |

Du kannst Stile kombinieren, zum Beispiel mit `***fett und kursiv***`.

Einzelne Unterstriche innerhalb von Wörtern bleiben normale Unterstriche. `mein_cooles_layout` wird also nicht kursiv dargestellt. Auch Namen wie `C++` bleiben unverändert.

> [!TIP]
> Markiere im Texteditor einen Textabschnitt und drücke `Ctrl + B`, `Ctrl + I` oder `Ctrl + U` (`Cmd` unter macOS), um ihn fett, kursiv oder unterstrichen zu formatieren. Weitere Informationen findest du unter [Formatierungs-Tastenkürzel](/text-in-menus#formatting-shortcuts).

## Textfarbe (HEX)

Setze `%<HEX-Farbe>%` vor den Text und `%#%` dahinter:

```
%#77fc03%Dieser Text ist grün!%#%
```

Die HEX-Farbe muss mit `#` beginnen. Du kannst auch Farbnamen verwenden:

```
%#red%Dieser Text ist rot!%#%
```

Unterstützte Namen: `black`, `silver`, `gray`, `grey`, `white`, `maroon`, `red`, `purple`, `fuchsia`, `magenta`, `green`, `lime`, `olive`, `yellow`, `navy`, `blue`, `teal`, `aqua`, `cyan` und `transparent`.

## Schriftarten

Um Text in einer anderen Schriftart darzustellen, setze `%!!<Schriftartname>%` davor und `%!!%` dahinter. Die Schriftart kann aus Minecraft oder einem Ressourcenpaket stammen.

```
%!!uniform%Dieser Text verwendet die Schriftart „uniform“.%!!%
```

## Textausrichtung

Text ist standardmäßig linksbündig. Um Zeilen zu zentrieren oder rechtsbündig auszurichten, setze den Ausrichtungscode jeweils in eine eigene Zeile davor und dahinter:

- `^^^` zentriert die Zeilen.
- `|||` richtet sie rechtsbündig aus.

```
Diese Zeile ist linksbündig.

^^^
Diese Zeile ist zentriert.
Diese ebenfalls.
^^^

|||
Diese Zeile ist rechtsbündig.
|||
```

> [!TIP]
> Im Texteditor kannst du mit `Ctrl + L`, `Ctrl + E` und `Ctrl + R` (`Cmd` unter macOS) die markierten Zeilen linksbündig, zentriert oder rechtsbündig ausrichten.

## Überschriften

Beginne eine Zeile mit `# ` (größte), `## ` (große) oder `### ` (kleine Überschrift):

```
# Willkommen!
## Neuigkeiten
### Kleine Überschrift
```

## Listen

<img width="460" alt="Markdown-Listen" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/markdown_lists.png?raw=true">

### Aufzählungslisten

Beginne eine Zeile mit `- `. Rücke sie für jede Verschachtelungsebene um zwei Leerzeichen ein:

```
- Erster Eintrag
- Zweiter Eintrag
  - Verschachtelter Eintrag
    - Noch tiefer verschachtelt
```

### Nummerierte Listen

Beginne eine Zeile mit einer Zahl und einem Punkt oder einer Klammer:

```
1. Öffne die Menüleiste
2. Klicke auf „Anpassung“
3) Das funktioniert ebenfalls
```

### Markierungen für Patchnotes

Zeilen können auch mit `+`, `-`, `~` oder `*` beginnen. Jedes Zeichen erhält eine eigene Markierung – ideal für Patchnotes und Änderungsprotokolle:

```
+ Neues Hauptmenü hinzugefügt
- Altes Logo entfernt
~ Buttonfarben geändert
* Absturz beim Start behoben
```

| Markierung | Bedeutung |
|---|---|
| `+` | Etwas wurde hinzugefügt |
| `-` | Etwas wurde entfernt |
| `~` | Etwas wurde geändert |
| `*` | Etwas ist besonders hervorzuheben |

Ein `-`-Eintrag erhält die Markierung „entfernt“ nur dann, wenn die Liste auch einen `+`-Eintrag enthält. Andernfalls ist es ein normaler Aufzählungseintrag. Du kannst dieses Verhalten unter **Markdown -> Listen -> Zusätzliche Markierungen (+ - ~ \*) -> Verwendete Markierung für -** ändern.

> [!NOTE]
> Bei neuen Text- und Tooltip-Elementen sind nummerierte Listen, Patchnote-Markierungen und [Hinweisboxen](#callouts) standardmäßig aktiviert. Bei Elementen aus älteren Layouts sind sie deaktiviert, damit sich der Text nicht plötzlich verändert. Aktiviere sie im Menü **Markdown** des Elements: **Listen -> Nummerierte Listen**, **Listen -> Zusätzliche Markierungen (+ - ~ \*)** und **Hinweisboxen**.

## Zitate

Beginne eine Zeile mit `> `, um ein Zitat zu erstellen. Das Zitat reicht bis zur nächsten leeren Zeile:

```
> Das ist ein Zitat.
Auch diese Zeile gehört dazu.

Diese Zeile ist wieder normaler Text.
```

Zeilen innerhalb eines Zitats können ebenfalls mit `>` beginnen. Eine Zeile, die nur aus `>` besteht, fügt dem Zitat eine Leerzeile hinzu:

```
> Erster Absatz des Zitats.
>
> Zweiter Absatz des Zitats.
```

## Hinweisboxen

Hinweisboxen sind farbige Kästen mit einem Symbol und einer Beschriftung – ideal für Tipps und Warnungen. Schreibe ein Zitat, dessen erste Zeile den Typ der Hinweisbox angibt:

```
> [!WARNING]
> Vergiss nicht, dein Layout zu speichern!
```

<img width="640" alt="Markdown-Hinweisboxen" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/markdown_callouts.png?raw=true">

Es gibt fünf Typen: `[!NOTE]`, `[!TIP]`, `[!IMPORTANT]`, `[!WARNING]` und `[!CAUTION]`.

## Links

Setze den Text in `[ ]` und den Link dahinter in `( )`:

```
[Besuche unsere Website](https://example.com)
```

Links können runde Klammern enthalten, zum Beispiel `https://en.wikipedia.org/wiki/Minecraft_(video_game)`. Um eckige Klammern im Linktext anzuzeigen, setze ein `\` davor: `[Klicke \[hier\]](https://example.com)`.

## Klick- und Hover-Ereignisse

Text kann auch [Listener](/listeners) auslösen, statt eine Website zu öffnen. Verwende dafür das Präfix `click:` oder `hover:` mit einer ID deiner Wahl:

```
[anklickbarer Beispieltext](click:unique_text_click_event_id)
[Text mit Hover-Effekt](hover:unique_text_hover_event_id)
```

Reagiere darauf mit den Listenern [**On Markdown Text Clicked**](/listeners#on-markdown-text-clicked) und [**On Markdown Text Hovered**](/listeners#on-markdown-text-hovered). Beide stellen dir die ID als `$$text_event_id` bereit.

## Bilder

Füge ein Bild in einer eigenen Zeile mit `![](` + der Bildquelle + `)` ein:

```
![](https://example.com/image.png)
```

Die Quelle kann eine Web-URL, eine lokale Datei wie `/config/fancymenu/assets/image.png` oder ein Bild aus einem Ressourcenpaket sein. Alle Quelltypen findest du unter [Ressourcen](/resources).

Der Text zwischen den eckigen Klammern wird zur Bildunterschrift:

```
![Mein toller Screenshot](/config/fancymenu/assets/screenshot.png)
```

Bildunterschriften werden unter dem Bild angezeigt, wenn die Option **Markdown -> Bilder -> Bildunterschrift** des Elements aktiviert ist.

Um ein Bild anklickbar zu machen, füge es in einen Link ein:

```
[![](https://example.com/image.png)](https://example.com)
```

## Tabellen

Trenne Zellen mit `|`. Die erste Zeile ist die Kopfzeile. In der zweiten Zeile steht für jede Spalte `---`:

```
| Gegenstand | Preis |
|:---|---:|
| Diamantschwert | 10 |
| Goldener Apfel | 5 |
```

Doppelpunkte in der zweiten Zeile richten die Spalten aus: `:---` linksbündig, `:---:` zentriert und `---:` rechtsbündig. Um ein `|` innerhalb einer Zelle anzuzeigen, schreibe `\|`.

<img width="640" alt="Markdown-Tabelle und Code" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/markdown_table_code.png?raw=true">

## Trennlinien

Eine Zeile, die nur aus `---` besteht, zeichnet eine Trennlinie über die gesamte Textbreite.

## Code

Code zeigt Text unverändert und ohne Formatierung an.

- **Inline-Code:** Schließe einen Teil einer Zeile in `` ` `` ein, zum Beispiel `` `/spawn` ``.
- **Codeblöcke:** Setze vor und nach den Zeilen jeweils eine Zeile mit `` ``` ``. Zeilen in Codeblöcken werden nicht umgebrochen.

````
```
/give @p minecraft:diamond 64
```
````

Du kannst hinter das erste `` ``` `` einen Sprachnamen schreiben, zum Beispiel `` ```json ``. FancyMenu akzeptiert ihn, aber er verändert nicht das Aussehen des Codes.

[Platzhalter](/placeholders) werden auch innerhalb von Code ersetzt.

## Klartext

Klartext zeigt Formatierungszeichen unverändert, aber nicht im Code-Stil an. Schließe einen Teil einer Zeile in `;;` ein:

```
Hier werden ;;**Sternchen**;; statt fettem Text angezeigt.
```

Für ganze Zeilen setzt du jeweils `;;;` in eine eigene Zeile davor und dahinter:

```
;;;
**Nicht fett**, _nicht kursiv_.
;;;
```

## Sonderzeichen maskieren

Um ein Formatierungszeichen als normalen Text anzuzeigen, setze ein `\` davor. Zum Beispiel wird `\*nicht kursiv\*` als `*nicht kursiv*` angezeigt.

Das funktioniert mit `\` `` ` `` `*` `_` `{` `}` `[` `]` `(` `)` `#` `+` `-` `.` `!` `|` `>` `~` und `^`.

# Minecraft-Textformatierung

Minecraft-Formatierungscodes funktionieren in den meisten Textfeldern von FancyMenu. Verwende `&` anstelle von Minecrafts `§`. Zum Beispiel stellt `&cWarnung` roten Text dar und `&l` macht Text fett. `&r` setzt die Formatierung zurück.

Alle Codes findest du im [Minecraft Wiki](https://minecraft.wiki/w/Formatting_codes).

Formatierungscodes funktionieren auch in Markdown-Text, außer innerhalb von Code und Klartext. Für Stile wie fett und kursiv ist Markdown meist leichter lesbar, für schnelle Farbänderungen sind Formatierungscodes jedoch praktisch.

# Minecraft-Textkomponenten (Raw Component System)

Minecraft-Textkomponenten sind formatierter Text im JSON-Format. Sie funktionieren für **einzeilige** Texte wie **Beschriftungen von Buttons und Schiebereglern**, aber nicht in Textelementen.

Um eine Textkomponente zu verwenden, setze sie als einzigen Inhalt der Beschriftung:

```
{"text":"Button-Beschriftung","font":"uniform"}
```

Damit wird `Button-Beschriftung` in der Schriftart `uniform` angezeigt. Im Wert von `text` kannst du [Platzhalter](/placeholders) verwenden.

Weitere Informationen findest du in den Minecraft-Wiki-Artikeln zum [Textkomponentenformat](https://minecraft.wiki/w/Raw_JSON_text_format) und zu [Schriftarten](https://minecraft.wiki/w/Resource_pack#Fonts).
