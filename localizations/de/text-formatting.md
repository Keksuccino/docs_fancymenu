---
title: Textformatierung
description: Wie man Text mit Markdown und den Formatierungscodes von Minecraft formatiert.
---

# Textformatierung

FancyMenu hat viele Funktionen, mit denen Textinhalte in Layouts noch *schicker* werden!

Textelemente unterstützen vollständig **Markdown** mit einigen coolen Extras, und die meisten anderen textbasierten Inhalte unterstützen außerdem das **Textformatierungssystem von Minecraft**. Sogar Beschriftungen von Buttons unterstützen **Minecraft-Textkomponenten**, mit denen du benutzerdefinierte Schriftarten und mehr verwenden kannst.

# Markdown

Die **Textelemente** von FancyMenu unterstützen Markdown vollständig. Das bedeutet, du kannst Textinhalte formatieren, indem du spezielle Zeichen hinzufügst.

Wenn du zum Beispiel Text fett darstellen willst, fügst du `**` vor und nach dem fetten Text ein, sodass `**Some bold text that's very bold.**` so aussieht:
**Some bold text that's very bold.**

Das Markdown von FancyMenu hat sogar einige besondere Funktionen, die es noch leistungsfähiger machen!

> Markdown funktioniert **NICHT** für andere textbasierte Inhalte wie Button-Beschriftungen. Es funktioniert nur für **TEXTELEMENTE**. Für alles andere verwende bitte [die Formatierungscodes von Minecraft](/text-formatting#minecraft-text-formatting).
{.is-danger}

## Schriftarten

Du kannst Text in einer benutzerdefinierten Schriftart anzeigen, die über ein Resource Pack geladen wurde, indem du `%!!<font_name>%` vor den Text und `%!!%` danach setzt.

Eine gültige Schriftart, die im Basisspiel enthalten ist, ist `uniform`. Um Text in der Schriftart `uniform` anzuzeigen, mache Folgendes:
`%!!uniform%this is a custom font%!!%`

Dadurch wird `this is a custom font` in der Schriftart `uniform` angezeigt.

## Textfarbe (HEX)

Text in einer bestimmten HEX-Farbe anzuzeigen ist möglich, indem du `%<HEX_color>%` vor den Text und `%#%` danach setzt.

Eine gültige HEX-Farbe für Grün ist `#77fc03`. Um Text in dieser Farbe anzuzeigen, mache Folgendes:
`%#77fc03%this text is green!%#%`

Dadurch wird `this text is green!` in `#77fc03` (grün) angezeigt.

Achte darauf, dass die HEX-Farbe mit `#` beginnt!

FancyMenu 3.9.0 unterstützt in diesem Farbformatierungscode außerdem häufig verwendete farbähnliche HTML-Namen:

```
%#red%This text is red!%#%
```

Unterstützte Namen: `black`, `silver`, `gray`, `grey`, `white`, `maroon`, `red`, `purple`, `fuchsia`, `magenta`, `green`, `lime`, `olive`, `yellow`, `navy`, `blue`, `teal`, `aqua`, `cyan` und `transparent`.

## Textausrichtung

Du kannst Textzeilen ausrichten, indem du eine Zeile mit dem jeweiligen Ausrichtungsformatierungscode beginnst, dann nichts anderes, dann die Textzeilen, die mit dieser Ausrichtung angezeigt werden sollen, und danach den Ausrichtungscode erneut in einer extra Zeile einfügst.

Alle Textinhalte sind standardmäßig **linksbündig**. Daher gibt es nur Formatierungscodes für **zentriert** und **rechtsbündig**.

### Zentriert

Um Textzeilen zu zentrieren, verwende den Formatierungscode `^^^`.

Beispiel:
```
This text is not centered.

^^^
This text is centered.
This text is also centered.
^^^

This text is not centered anymore.
```

### Rechtsbündig

Um Textzeilen rechtsbündig anzuzeigen, verwende den Formatierungscode `|||`.

Beispiel:
```
This text is not right-aligned.

|||
This text is right-aligned.
This text is also right-aligned.
|||

This text is not right-aligned anymore.
```

## Überschriften

Um **eine Textzeile** als Überschrift anzuzeigen (größer und unterstrichen), füge vor der Textzeile `# ` (sehr groß), `## ` (groß) oder `### ` (klein) ein.

Beispiel:
`## Big Headline`

## Fett

Füge `**` vor und nach Text ein, damit er **fett** erscheint.

Beispiel:
`**bold text content**`

## Kursiv

Füge `_` ODER `*` vor und nach Text ein, damit er *kursiv* erscheint.

Beispiel:
`*italic text content*`

## Durchgestrichen

Füge `~` vor und nach Text ein, damit er ~~durchgestrichen~~ erscheint.

Beispiel:
`~strikethrough text content~`

## Hyperlinks

Du kannst Hyperlinks zu Textinhalten hinzufügen, die beim Anklicken eine Website öffnen.

Text, der als [Hyperlink](https://google.com) erscheinen soll, muss in `[ ]` eingeschlossen werden, gefolgt vom eigentlichen Link in `( )`.

Wenn du also `example text content` anklickbar machen und `https://example-website.net` öffnen lassen willst, mache Folgendes:
`[example text content](https://example-website.net)`

## Klick- und Hover-Events

FancyMenu 3.9.0 fügt Markdown-Klick- und Hover-Events für Textelemente und andere Markdown-Texte hinzu.

Klick-Events verwenden den Präfix `click:`:

```
[some clickable text](click:unique_text_click_event_id)
```

Hover-Events verwenden den Präfix `hover:`:

```
[some hoverable text](hover:unique_text_hover_event_id)
```

Verwende die Listener **On Markdown Text Clicked** und **On Markdown Text Hovered**, um auf diese Events zu reagieren. Beide Listener stellen die Event-ID als `$$text_event_id` bereit.

## Bilder

Markdown unterstützt die Anzeige von Bildern in Textinhalten.

FancyMenu unterstützt in Markdown Minecraft-Ressourcen, lokale Ressourcen und Web-Ressourcen.

Um ein Bild hinzuzufügen, beginne eine Textzeile mit `![](`, dann die [URL, den Resource-Lokationspfad oder den Pfad zur Ressource](/resources) und dann `)`.

Um also die Web-Ressource `https://example-website.net/image.png` anzuzeigen, mache Folgendes:
`![](https://example-website.net/image.png)`

Bilder können auch **Hyperlinks** sein, indem du die gesamte Bild-Textzeile in einen **Hyperlink** einschließt, etwa so:
`[![](https://example-website.net/image.png)](https://example-website.net)`

> Lokale Ressourcen müssen sich in `/config/fancymenu/assets/` befinden!
{.is-warning}

## Zitat

Um Text als Zitat zu formatieren, beginne eine Textzeile mit `> `.
Dadurch werden alle folgenden Zeilen als Zitat formatiert, bis eine **leere** Zeile gefunden wird.

Beispiel:
```
This will not look like a quote.

> This will look like a quote.
This will also look like a quote.

This will not look like a quote anymore.
```

## Aufzählungslisten

Um Text als Aufzählungsliste wie diese darzustellen:
- Entry 1
- Entry 2
  - Sub-Entry

musst du einfach eine Zeile mit `- ` beginnen.

Beispiel:
```
- Entry 1
- Entry 2
  - Sub-Entry
```

## Trennlinie

Um eine Trennlinie zu deinem Text hinzuzufügen, die die Breite einer ganzen Textzeile hat, beginne einfach eine Zeile mit `---` und füge danach nichts Weiteres hinzu.

Es sieht dann ungefähr so aus:

---

## Codeblöcke

Codeblöcke können dir helfen, Text als `Plain Text` anzuzeigen, ohne dass Markdown versucht, ihn zu formatieren, oder einfach Text in einem codeähnlichen Stil ohne automatisches Umbrechen der Textzeilen darzustellen.

Ein einzeiliger Codeblock (zwischen anderem Text) beginnt und endet mit \` , was in einem Markdown-Text tatsächlich ziemlich schwer darzustellen ist.

Eine Textzeile mit einem einzeiligen Codeblock sieht so aus:

![single_line_code_block](https://github.com/Keksuccino/FancyMenu/assets/35544624/e78fd38b-7b1a-4f00-9b11-797d964b3b43)

Mehrzeilige Codeblöcke umfassen mehrere Zeilen in einem großen Codeblock und beginnen mit einer Zeile, die nur \`\`\` enthält, dann folgt der Textinhalt und dann wieder \`\`\`:

![multi_line_code_block](https://github.com/Keksuccino/FancyMenu/assets/35544624/bf8c77eb-a97e-48cd-9270-8302c2995856) 

## Reiner Text

Der Formatierungscode für reinen Text umgeht alle anderen darin enthaltenen Formatierungscodes.

Er funktioniert ähnlich wie Codeblöcke, formatiert den Text aber nicht wie einen Codeblock. Stattdessen wird er wie normaler Text angezeigt, jedoch ohne jegliche Formatierung.

Um einen Textabschnitt innerhalb einer Zeile in einen Formatierungscode für reinen Text einzuschließen, musst du `;;` vor und nach dem Textabschnitt einfügen, den du als reinen Text anzeigen möchtest, so:

```
This is a line of text with ;;**this part**;; showing as unformatted text with visible ** (bold) formatting code and _this part_ as normal formatted italic text.
```

Reiner Text funktioniert auch als mehrzeiliger Wrapper-Code. Um ganze Zeilen einzuschließen, füge `;;;` vor und nach den Zeilen ein, die als reiner Text angezeigt werden sollen, so:

```
;;;
This line will show **unformatted** with visible ** (bold) formatting codes.
This line will also show _unformatted_ with visible _ (italic) formatting codes.
;;;

This line will look **normal** again with the "normal" formatted as bold text.
```

# Minecraft-Textformatierung

Minecraft selbst hat ein ziemlich gutes Formatierungssystem, das ähnlich wie Markdown funktioniert, indem du spezielle Zeichen zu deinem Text hinzufügst, um ihn zu formatieren.

Um mehr über das Formatierungssystem von Minecraft zu erfahren, wirf bitte einen Blick auf [diese Minecraft-Wiki-Seite](https://minecraft.wiki/w/Formatting_codes).

> Die Wiki gibt als Präfix für den Formatierungscode `§` an, aber in FancyMenu musst du es durch `&` ersetzen. Alles andere bleibt gleich.
{.is-warning}

> **Textelemente** sind sehr komplex, und um Markdown zu unterstützen, war der Kompromiss, die **Vanilla-Formatierungscodes von Minecraft zu brechen**. Deshalb funktionieren diese Codes in Textelementen nicht gut (nur das erste Wort wird nach dem Formatierungscode formatiert usw.). Du solltest in Textelementen stattdessen Markdown-Formatierungscodes verwenden.
{.is-danger}

# Minecraft-Textkomponenten (Raw Component System)

Das Textkomponentensystem von Minecraft ist sehr leistungsfähig für **einzeilige** Textinhalte wie **Button-Beschriftungen**.

In Vanilla-Minecraft kannst du es in den Befehlen `/tellraw` und `/title` verwenden (und wahrscheinlich auch an anderen Stellen).
Es handelt sich um formatierten Text, der als JSON serialisiert ist, sodass du Formatierungsattribute zu Textinhalten hinzufügen kannst.

Um mehr über Textkomponenten im Detail zu erfahren, wirf bitte einen Blick auf [diese Minecraft-Wiki-Seite](https://minecraft.wiki/w/Raw_JSON_text_format).
Um mehr über Schriftarten in Minecraft zu erfahren, wirf einen Blick auf [diese Minecraft-Wiki-Seite](https://minecraft.wiki/w/Resource_pack#Fonts).

Damit FancyMenu eine Button-Beschriftung als **Textkomponente** erkennt, darf als Beschriftung nur der serialisierte Komponententext gesetzt sein, so wie hier:
`{"text":"Button Label Text","font":"uniform"}`

Das obige Beispiel zeigt die Button-Beschriftung `Button Label Text` in der Schriftart `uniform` an.

> Du kannst FancyMenus Platzhalter im `text`-Wert von Komponenten verwenden.
{.is-info}
