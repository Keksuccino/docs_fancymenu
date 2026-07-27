---
title: Textformatierung
description: Wie man Text mit Markdown und den Formatierungscodes von Minecraft formatiert.
---

# Textformatierung

[Textelemente](./elements#text) unterstützen Markdown. Andere Textfelder verwenden Minecraft-Formatierung, und Schaltflächenbeschriftungen können Minecraft-Textkomponenten verwenden.

# Markdown

FancyMenus **Textelemente** unterstützen Markdown vollständig. Das bedeutet, dass du Textinhalte formatieren kannst, indem du spezielle Zeichen hinzufügst.

Um zum Beispiel Text fett darzustellen, füge `**` vor und nach dem fetten Text hinzu. `**Ein fetter Text, der sehr fett ist.**` sieht dann so aus:
**Ein fetter Text, der sehr fett ist.**

FancyMenu unterstützt außerdem die unten dokumentierten Erweiterungen.

> [!CAUTION]
> Markdown funktioniert nur in **Textelementen**. Für Schaltflächenbeschriftungen und andere Textfelder verwende bitte [Minecrafts Formatierungscodes](#minecraft-textformatierung).

## Schriftarten

Du kannst Text in einer benutzerdefinierten Schriftart anzeigen, die über ein Resource Pack geladen wurde, indem du vor den Text `%!!<schriftname>%` und danach `%!!%` einfügst.

Eine gültige Schriftart aus dem Basisspiel ist `uniform`. Um Text in der Schriftart `uniform` anzuzeigen, verwende also Folgendes:
`%!!uniform%dies ist eine benutzerdefinierte Schriftart%!!%`

Dadurch wird `dies ist eine benutzerdefinierte Schriftart` in der Schriftart `uniform` angezeigt.

## Textfarbe (HEX)

Text in einer bestimmten HEX-Farbe anzeigen zu lassen ist möglich, indem du vor den Text `%<HEX_farbe>%` und danach `%#%` einfügst.

Eine gültige HEX-Farbe für Grün ist `#77fc03`. Um Text in dieser Farbe anzuzeigen, verwende also Folgendes:
`%#77fc03%dieser Text ist grün!%#%`

Dadurch wird `dieser Text ist grün!` in `#77fc03` (grün) angezeigt.

Achte darauf, dass die HEX-Farbe mit `#` beginnt!

Übliche farbliche Namen im HTML-Stil werden im selben Farbformatierungscode unterstützt:

```
%#red%Dieser Text ist rot!%#%
```

Unterstützte Namen: `black`, `silver`, `gray`, `grey`, `white`, `maroon`, `red`, `purple`, `fuchsia`, `magenta`, `green`, `lime`, `olive`, `yellow`, `navy`, `blue`, `teal`, `aqua`, `cyan` und `transparent`.

## Textausrichtung

Du kannst Textzeilen ausrichten, indem du eine Zeile mit dem jeweiligen Ausrichtungs-Formatierungscode beginnst, dann nichts Weiteres folgst, dann die Textzeilen hinzufügst, die mit dieser Ausrichtung angezeigt werden sollen, und anschließend den Ausrichtungscode wieder in einer zusätzlichen Zeile schreibst.

Alle Textinhalte sind standardmäßig **linksbündig** ausgerichtet, daher gibt es nur Formatierungscodes für **zentriert** und **rechtsbündig**.

### Zentriert

Um Textzeilen zu zentrieren, verwende den Formatierungscode `^^^`.

Beispiel:
```
Dieser Text ist nicht zentriert.

^^^
Dieser Text ist zentriert.
Dieser Text ist ebenfalls zentriert.
^^^

Dieser Text ist nicht mehr zentriert.
```

### Rechtsbündig

Um Textzeilen rechtsbündig anzuzeigen, verwende den Formatierungscode `|||`.

Beispiel:
```
Dieser Text ist nicht rechtsbündig.

|||
Dieser Text ist rechtsbündig.
Dieser Text ist ebenfalls rechtsbündig.
|||

Dieser Text ist nicht mehr rechtsbündig.
```

## Überschriften

Um **eine Textzeile** als Überschrift anzuzeigen (größer und unterstrichen), füge `# ` (sehr groß), `## ` (groß) oder `### ` (klein) vor der Textzeile hinzu.

Beispiel:
`## Große Überschrift`

## Fett

Füge `**` vor und nach dem Text hinzu, um ihn **fett** darzustellen.

Beispiel:
`**fetter Textinhalt**`

## Kursiv

Füge `_` ODER `*` vor und nach dem Text hinzu, um ihn *kursiv* darzustellen.

Beispiel:
`*kursiver Textinhalt*`

## Durchgestrichen

Füge `~` vor und nach dem Text hinzu, um ihn ~~durchgestrichen~~ darzustellen.

Beispiel:
`~durchgestrichener Textinhalt~`

## Hyperlinks

Du kannst Textinhalte mit Hyperlinks versehen, die beim Anklicken eine Website öffnen.

Text, der als [Hyperlink](https://google.com) erscheinen soll, muss in `[ ]` eingeschlossen werden, gefolgt vom eigentlichen Link in `( )`.

Wenn du also `Beispiel-Textinhalt` anklickbar machen und `https://example-website.net` öffnen lassen willst, verwende Folgendes:
`[Beispiel-Textinhalt](https://example-website.net)`

## Klick- und Hover-Ereignisse

Markdown-Klick- und Hover-Ereignisse sind für [Textelemente](./elements#text) und andere Markdown-Texte verfügbar. Verwende [**Bei Klick auf Markdown-Text**](./listeners#on-markdown-text-clicked-text_clicked) und [**Bei Hover über Markdown-Text**](./listeners#on-markdown-text-hovered-text_hovered), um darauf zu reagieren.

Klick-Ereignisse verwenden das Präfix `click:`:

```
[anklickbarer Text](click:unique_text_click_event_id)
```

Hover-Ereignisse verwenden das Präfix `hover:`:

```
[hoverbarer Text](hover:unique_text_hover_event_id)
```

Beide Listener stellen die Ereignis-ID als `$$text_event_id` bereit.

## Bilder

Markdown unterstützt das Anzeigen von Bildern in Textinhalten.

FancyMenu unterstützt Minecraft-Ressourcen, lokale Ressourcen und Web-Ressourcen in Markdown.

Um ein Bild hinzuzufügen, beginne eine Textzeile mit `![](`, dann die [URL, den Ressourcenpfad oder den Pfad zur Ressource](./resources) und dann `)`.

Um also die Web-Ressource `https://example-website.net/image.png` anzuzeigen, verwende Folgendes:
`![](https://example-website.net/image.png)`

Bilder können auch **Hyperlinks** sein, indem die gesamte Bild-Textzeile in einen **Hyperlink** eingebettet wird, etwa so:
`[![](https://example-website.net/image.png)](https://example-website.net)`

> [!WARNING]
> Lokale Ressourcen müssen sich in `<game-directory>/config/fancymenu/assets/` befinden!

## Zitat

Um Text als Zitat zu formatieren, beginne eine Textzeile mit `> `.
Dadurch werden alle folgenden Zeilen als Zitat formatiert, bis eine **leere** Zeile gefunden wird.

Beispiel:
```
Das wird nicht wie ein Zitat aussehen.

> Das wird wie ein Zitat aussehen.
Dieser Text wird ebenfalls wie ein Zitat aussehen.

Das wird nicht mehr wie ein Zitat aussehen.
```

## Aufzählungen

Um Text als Aufzählung wie diese anzuzeigen:
- Eintrag 1
- Eintrag 2
  - Untereintrag

musst du einfach eine Zeile mit `- ` beginnen.

Beispiel:
```
- Eintrag 1
- Eintrag 2
  - Untereintrag
```

## Trennlinie

Um deinem Text eine Trennlinie mit der Breite einer ganzen Textzeile hinzuzufügen, beginne einfach eine Zeile mit `---` und füge nichts Weiteres hinzu.

Dann sieht sie ungefähr so aus:

---

## Codeblöcke

Codeblöcke helfen dir dabei, Text als `reinen Text` anzuzeigen, ohne dass Markdown versucht, ihn zu formatieren, oder einfach Text in einer codeähnlichen Darstellung ohne automatisches Umbrechen von Textzeilen zu zeigen.

Ein einzeiliger Codeblock (zwischen anderem Text) beginnt und endet mit \` , was in einem Markdown-Text tatsächlich ziemlich schwer darzustellen ist.

Eine Textzeile mit einem einzeiligen Codeblock sieht so aus:

![single_line_code_block](https://github.com/Keksuccino/FancyMenu/assets/35544624/e78fd38b-7b1a-4f00-9b11-797d964b3b43)

Mehrzeilige Codeblöcke umfassen mehrere Zeilen in einem großen Codeblock und beginnen mit einer Zeile, die nur \`\`\` enthält, dann folgt der Textinhalt und anschließend erneut \`\`\`:

![multi_line_code_block](https://github.com/Keksuccino/FancyMenu/assets/35544624/bf8c77eb-a97e-48cd-9270-8302c2995856) 

## Klartext

Der Klartext-Formatierungscode umgeht alle anderen Formatierungscodes innerhalb davon.

Er funktioniert ähnlich wie Codeblöcke, formatiert den Inhalt jedoch nicht wie einen Codeblock. Stattdessen wird er wie normaler Text angezeigt, aber ohne jegliche Formatierung.

Um einen Textteil innerhalb einer Zeile in einen Klartext-Formatierungscode einzuschließen, musst du `;;` vor und nach dem Textteil hinzufügen, den du als Klartext anzeigen möchtest, etwa so:

```
Dies ist eine Textzeile mit ;;**diesem Teil**;;, der als unformatierter Text mit sichtbarem **- (fett) Formatierungscode angezeigt wird, und _dieser Teil_ als normal formatierter kursiver Text.
```

Klartext funktioniert auch als mehrzeiliger Umschließungscode. Um ganze Zeilen einzuschließen, füge `;;;` vor und nach den Zeilen hinzu, die du als Klartext anzeigen möchtest, etwa so:

```
;;;
Diese Zeile wird **unformatiert** mit sichtbaren **- (fett) Formatierungscodes angezeigt.
Diese Zeile wird ebenfalls _unformatiert_ mit sichtbaren _- (kursiv) Formatierungscodes angezeigt.
;;;

Diese Zeile sieht wieder **normal** aus, wobei "normal" als fetter Text formatiert ist.
```

# Minecraft-Textformatierung

Minecraft-Formatierungscodes funktionieren in unterstützten formatierten Textfeldern in ganz FancyMenu. Verwende `&` anstelle des Minecraft-Präfixes `§`; zum Beispiel zeigt `&cWarnung` roten Text an.

Siehe die [Referenz zu Formatierungscodes im Minecraft-Wiki](https://minecraft.wiki/w/Formatting_codes) für die verfügbaren Farben und Stile.

> [!CAUTION]
> Minecraft-Formatierungscodes sind in **Textelementen** unzuverlässig, da diese Elemente Markdown parsen. Verwende stattdessen die oben beschriebene Markdown-Formatierung.

# Minecraft-Textkomponenten (Raw Component System)

Das Textkomponentensystem von Minecraft ist ziemlich mächtig für **einzeilige** Textinhalte wie **Schaltflächenbeschriftungen**.

Im Vanilla-Minecraft kannst du es in den Befehlen `/tellraw` und `/title` verwenden (und wahrscheinlich auch an anderen Stellen).
Es handelt sich um formatierten Text, der als JSON serialisiert wird, sodass du Formatierungsattribute zu Textinhalten hinzufügen kannst.

Um mehr über Textkomponenten im Detail zu erfahren, wirf bitte einen Blick auf [diese Minecraft-Wiki-Seite](https://minecraft.wiki/w/Raw_JSON_text_format).
Um mehr über Schriftarten in Minecraft zu erfahren, schau dir bitte [diese Minecraft-Wiki-Seite](https://minecraft.wiki/w/Resource_pack#Fonts) an.

Damit FancyMenu eine Schaltflächenbeschriftung als **Textkomponente** erkennt, darfst du als Beschriftung nichts weiter als den serialisierten Komponententext angeben, also so:
`{"text":"Schaltflächenbeschriftungstext","font":"uniform"}`

Das obige Beispiel zeigt die Schaltflächenbeschriftung `Schaltflächenbeschriftungstext` in der Schriftart `uniform` an.

> [!NOTE]
> Du kannst in den `text`-Wert von Komponenten die Platzhalter von FancyMenu verwenden.
