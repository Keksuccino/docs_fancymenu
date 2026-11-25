---
title: Text in Menüs
description: >-
  So zeigst du Text in Menüs mit Text- und Tooltip-Elementen an und passt ihn an
  und scrollst darin.
sourceBlobSha: 557734a5ca4e53d75045d7086642e9c561805b29
---
# Text in Menüs

FancyMenu bietet zwei Elemente für Text:

- **Text** zeigt Text direkt in deinem Menü an – von einer einzelnen Zeile bis hin zu langen, scrollbaren Seiten wie Änderungsprotokollen, Regeln oder Neuigkeiten.
- **Tooltip** zeigt ein Textfeld an einer festen Stelle oder neben der Maus an, zum Beispiel wenn sich der Mauszeiger über einer Schaltfläche befindet.

Beide unterstützen [Markdown](/text-formatting) und [Platzhalter](/placeholders) und verwenden dieselben Einstellungen für Darstellung und Stil.

<img width="800" alt="Ein Textelement bearbeiten" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/text_editor_showcase.gif?raw=true">

> [!TIP]
> Auf dieser Seite geht es um die Elemente und ihre Einstellungen. Alles darüber, was du in deinen Text schreiben kannst – zum Beispiel Überschriften, Listen, Links und Farben –, findest du unter [Textformatierung](/text-formatting).

# Text hinzufügen

1. Öffne ein Layout im Layout-Editor.
2. Klicke mit der rechten Maustaste auf den Hintergrund des Editors und wähle **Neues Element -> Text**.
3. Klicke mit der rechten Maustaste auf das neue Element und wähle **Textinhalt**.
4. Gib deinen Text ein und klicke auf **Fertig**.

# Textinhalt

## Quellmodus

Klicke mit der rechten Maustaste auf das Element und lege den **Quellmodus** fest:

- **Direkt**: Du gibst den Text selbst im Texteditor ein.
- **Ressource**: Der Text stammt aus einer Textdatei. Klicke auf **Textquelle**, um eine lokale Datei aus `<game-directory>/config/fancymenu/assets/`, eine Web-URL oder eine Ressource-Pack-Datei auszuwählen. Weitere Informationen findest du unter [Ressourcen](/resources).

Webquellen eignen sich hervorragend für Dinge wie Änderungsprotokolle oder Neuigkeiten, die immer aktuell sein sollen, ohne dass du dein Modpack aktualisieren musst.

FancyMenu merkt sich den Text aus Dateien und Webquellen, bis das Spiel geschlossen wird. Um ihn erneut zu laden, lade FancyMenu über **Menüleiste -> Anpassung -> FancyMenu neu laden** neu.

## Dynamischer Text

Mit [Platzhaltern](/placeholders) kann Text Live-Werte anzeigen, zum Beispiel `Willkommen, {"placeholder":"playername"}!`. Außerdem kann er Werte von [Variablen](/variables) anzeigen. Der Text wird automatisch aktualisiert, wenn sich diese Werte ändern.

## Der Texteditor

Wenn du auf **Textinhalt** klickst, öffnet sich der Texteditor. Klicke oben rechts auf **Platzhalter**, um alle Platzhalter anzuzeigen und sie deinem Text hinzuzufügen.

### Formatierungs-Tastenkürzel

Der Texteditor von Text- und Tooltip-Elementen bietet Tastenkürzel für gängige Formatierungen. Verwende unter macOS `Cmd` statt `Ctrl`.

| Tastenkürzel | Funktion |
|---|---|
| `Ctrl + B` | Fett |
| `Ctrl + I` | Kursiv |
| `Ctrl + U` | Unterstrichen |
| `Ctrl + L` | Linksbündig |
| `Ctrl + E` | Zentriert |
| `Ctrl + R` | Rechtsbündig |

- Markiere zuerst Text, um ihn zu formatieren. Drücke dasselbe Tastenkürzel erneut, um die Formatierung zu entfernen.
- Ohne Markierung fügt das Tastenkürzel die Formatierungszeichen ein und setzt den Cursor dazwischen, sodass du direkt weiterschreiben kannst.
- Die Tastenkürzel für die Ausrichtung gelten für die markierten Zeilen oder für die Zeile, in der sich der Cursor befindet. Wenn du `Ctrl + E` oder `Ctrl + R` auf Zeilen anwendest, die bereits entsprechend ausgerichtet sind, werden sie wieder linksbündig ausgerichtet.
- Klicke im Editor mit der rechten Maustaste und öffne **Formatierung**, um alle diese Optionen in einem Menü zu sehen.

### Weitere Tastenkürzel

Derselbe Texteditor wird für die meisten Texte in FancyMenu verwendet, zum Beispiel für Aktionswerte und viele Element-Einstellungen. Diese Tastenkürzel funktionieren überall. Verwende unter macOS `Cmd` statt `Ctrl`.

| Tastenkürzel | Funktion |
|---|---|
| `Ctrl + C` | Markierten Text kopieren |
| `Ctrl + X` | Markierten Text ausschneiden |
| `Ctrl + V` | Einfügen |
| `Ctrl + A` | Gesamten Text markieren |
| `Ctrl + Z` | Rückgängig |
| `Ctrl + Y` | Wiederholen |
| `Ctrl + D` | Zeile duplizieren, in der sich der Cursor befindet |
| `Alt + Pfeil nach oben` / `Alt + Pfeil nach unten` | Zeile, in der sich der Cursor befindet, nach oben oder unten verschieben |
| `Umschalt + Pfeiltasten` | Text markieren |
| `Ctrl + Home` / `Ctrl + End` | Zum Anfang oder Ende des Textes springen |
| `Ctrl + G` | Zu einer Zeile springen: Nummer eingeben und `Enter` drücken |
| `Ctrl + S` | Entspricht **Fertig** |

Die Tastenkürzel für den Layout-Editor findest du unter [Layout-Editor](/layout-editor#shortcuts).

# Darstellung und Stile

Klicke mit der rechten Maustaste auf das Element und öffne **Markdown**, um das Erscheinungsbild des Textes anzupassen.

## Darstellung

Eine **Darstellung** legt alle Stileinstellungen des Textes auf einmal fest:

- **Pixel**: Pixelgrafik passend zur Minecraft-Schriftart, mit warmen Farben, goldenen Details und handgezeichneten Markierungen.
- **Klassisch**: Der klassische FancyMenu-Stil mit weißem Text, grauen Feldern und grauen Linien.
- **Neutral**: Ein klares Erscheinungsbild in den Farben des aktuellen FancyMenu-UI-Themes. Die Farben werden mit dem Element gespeichert und bleiben daher gleich, wenn du später das Theme wechselst.

<img width="800" alt="Die drei Markdown-Darstellungen" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/markdown_looks.png?raw=true">

Neue Elemente verwenden standardmäßig die Darstellung Pixel. Elemente aus älteren Layouts behalten die klassische Darstellung, die sie schon immer hatten.

> [!NOTE]
> Wenn du eine Darstellung auswählst, werden deine eigenen Stiländerungen ersetzt. Anders überlegt? Mach die Änderung einfach mit `Ctrl + Z` rückgängig.

## Stileinstellungen

Auch nach der Auswahl einer Darstellung kannst du jeden einzelnen Teil fein abstimmen. Das Menü **Markdown** bietet Optionen für **Text**, **Überschriften**, **Listen**, **Links**, **Code**, **Zitate**, **Hinweisfelder**, **Tabellen**, **Bilder** und **Trennlinien**. Bewege den Mauszeiger über eine Option, um zu sehen, was sie bewirkt.

Unter **Markdown -> Text** findest du grundlegende Einstellungen wie Textfarbe, Textschatten, Zeilenabstand und den Abstand zwischen dem Text und den Kanten des Elements.

## Markdown deaktivieren

Wenn du Markdown nicht brauchst, deaktiviere **Markdown -> Markdown-Parser**. Dann wird der Text genau so angezeigt, wie du ihn eingegeben hast. Bei sehr langen Texten ist das außerdem etwas schneller.

## Weitere Texteinstellungen

Klicke mit der rechten Maustaste auf das Element, um auch diese Optionen zu finden:

- **Textskalierung** vergrößert oder verkleinert den Text.
- **Groß-/Kleinschreibung** zeigt den Text normal, nur in Großbuchstaben oder nur in Kleinbuchstaben an.
- **Automatischer Zeilenumbruch** bricht Zeilen um, die zu lang für das Element sind. Wenn die Option deaktiviert ist, laufen lange Zeilen einfach weiter.
- **HTML-Zeilenumbrüche entfernen** entfernt HTML-Zeilenumbrüche (`<br>`) aus dem Text. Das ist praktisch bei Texten von Websites.

# Hintergrund

Textelemente können hinter ihrem Text ein Feld anzeigen. Öffne **Hintergrund** im Rechtsklickmenü des Elements:

- **Hintergrund anzeigen** schaltet das Feld ein oder aus. Bei neuen Textelementen ist es aktiviert.
- Standardmäßig wird ein integriertes dunkles Feld verwendet. Du kannst stattdessen eine eigene Textur verwenden und mit [Neun-Slicing](/nine-slicing-and-tiling) sowie Kachelung dafür sorgen, dass die Kanten ihre Form behalten.
- **Abstand** legt fest, wie weit der Hintergrund über den Text hinausragt.
- **Hinter Scrollleisten reichen** lässt den Hintergrund auch die Scrollleisten überdecken. Wenn die Option deaktiviert ist, befinden sich die Scrollleisten direkt daneben.

Tooltips haben ein eigenes Menü **Hintergrund**, in dem du eine Textur und deren Neun-Slicing einstellen kannst.

# Scrollen

Ein Textelement lässt sich scrollen, wenn sein Text nicht vollständig hineinpasst. Verwende das Mausrad zum Scrollen. Halte `Shift` gedrückt, um seitwärts zu scrollen.

Mit **Scrollrichtung** legst du fest, ob der Text **Vertikal**, **Horizontal** oder **In beide Richtungen** scrollt. In den Richtungen, in denen nicht gescrollt wird, wird alles abgeschnitten, was nicht hineinpasst.

## Scroll-Einstellungen

Öffne **Scrollen** im Rechtsklickmenü des Elements:

| Einstellung | Funktion |
|---|---|
| **Spielern das Scrollen erlauben** | Legt fest, ob Spieler den Text selbst scrollen können. Wenn die Option deaktiviert ist, scrollt der Text nur automatisch und über Aktionen. |
| **Scrollgeschwindigkeit** | Legt fest, wie weit ein Schritt des Mausrads scrollt. |
| **Sanftes Scrollen** | Lässt den Text gleiten, statt ruckartig weiterzuspringen. |
| **Ziehen zum Scrollen** | Spieler können den Text mit der Maus greifen und ziehen, wie auf einem Touchscreen. |
| **Mit der Tastatur scrollen** | Wenn sich der Mauszeiger über dem Text befindet, scrollen `Page Up` und `Page Down` jeweils um eine Seite. Mit `Home` und `End` springst du zum Anfang beziehungsweise Ende. |
| **Einrasten** | Legt fest, wo der Text zum Stillstand kommt: an einer beliebigen Stelle (**Aus**), mit einer ganzen Zeile oben (**An Zeilen**), mit einer Überschrift oben (**An Überschriften**) oder jeweils eine ganze Seite weiter (**An Seiten**). |
| **Startposition** | Legt fest, ob der Text am **Anfang** oder am **Ende** beginnt. Das Ende ist praktisch für Dinge wie Protokolle, bei denen die neuesten Einträge zuletzt stehen. |
| **Beim Öffnen des Bildschirms zurücksetzen** | Setzt den Text bei jedem Öffnen des Bildschirms an den Anfang zurück. Wenn die Option deaktiviert ist, merkt sich der Text seine Scrollposition, bis das Spiel geschlossen wird. |

## Automatisches Scrollen

Öffne **Automatisches Scrollen**, damit der Text langsam von selbst scrollt, wie bei einem Abspann oder Nachrichtenticker:

- **Automatisch scrollen** aktiviert die Funktion.
- **Geschwindigkeit [Pixel pro Sekunde]** legt fest, wie schnell der Text scrollt.
- **Am Ende von vorn beginnen** startet wieder am Anfang, sobald das Ende erreicht ist.
- **Bei Mauszeiger darüber pausieren** hält das Scrollen an, solange sich der Mauszeiger über dem Text befindet, damit Spieler in Ruhe lesen können.

## Scrollleisten

Öffne **Scrollleisten**, um die Leisten anzupassen:

- **Anzeigen** legt fest, wann die Leisten erscheinen: **Immer**, nur **Beim Scrollen** oder **Nie**. Bei **Nie** funktioniert das Mausrad weiterhin.
- **Dicke** legt fest, wie dick die Leisten sind.
- **Vertikale Leiste links** und **Horizontale Leiste oben** verschieben die Leisten auf die jeweils andere Seite.
- **Stil des Scrollgriffs** legt das Erscheinungsbild der Griffe fest: **Theme-Leiste** (in den Farben deines FancyMenu-UI-Themes) oder **Pixel-Griff** (Pixelgrafik, die gut zur Darstellung Pixel passt).
- **Texturen des Scrollgriffs** und **Farbe des Scrollgriffs [HEX]** ersetzen die Griffe durch eigene Texturen oder Farben.
- **Hintergründe der Scrollleisten** fügen Texturen hinter den Griffen hinzu, entlang ihrer Bewegungsbahn.

## Scrollen mit Aktionen

Du kannst das Scrollen auch von anderen Bereichen in FancyMenu aus steuern und beobachten:

- Mit der [Aktion](/action-scripts) **Element scrollen** scrollst du ein Textelement an den Anfang, ans Ende, zu einer Position oder Zeilennummer oder zur ersten Zeile, die einen bestimmten Text enthält.
- Die [Platzhalter](/placeholders) **Scrollposition des Elements**, **Scrollprozentsatz des Elements** und **Inhaltsgröße des Elements** geben an, wie weit der Text gescrollt ist und wie groß er ist.
- Die [Bedingung](/conditions) **Ist das Element bis zum Ende gescrollt** prüft, ob der Text bis zum Ende gescrollt wurde. Damit kannst du zum Beispiel eine Schaltfläche „Akzeptieren“ erst aktivieren, nachdem die Regeln gelesen wurden.
- Die [Listener](/listeners) **Beim Scrollen des Elements**, **Beim Scrollen des Elements zum Anfang** und **Beim Scrollen des Elements zum Ende** führen Aktionen aus, während der Text gescrollt wird.

Für all diese Funktionen benötigst du den [Elementbezeichner](/element-identifiers) des Textelements.

# Klicks durch Textelemente hindurch

Textelemente reagieren auf die Maus, damit ihre Links und Scrollleisten funktionieren. Dadurch fangen sie aber auch Klicks ab, sodass Schaltflächen hinter oder vor einem Textelement möglicherweise keine Klicks erhalten.

Wenn das ein Problem ist, klicke mit der rechten Maustaste auf das Textelement und deaktiviere **Interaktiv**. Der Text kann dann nicht mehr gescrollt und seine Links können nicht mehr angeklickt werden.

# Tooltips

Tooltip-Elemente funktionieren wie Textelemente, nur ohne Scrollen:

- Für Text, Darstellung und Stil gelten dieselben Einstellungen wie für Textelemente.
- **Maus folgen** lässt den Tooltip der Maus folgen.
- Verwende [Bedingungen](/conditions), um festzulegen, wann der Tooltip angezeigt wird. Mit der Bedingung [**Ist das Element unter dem Mauszeiger**](/conditions#is-element-hovered) kannst du ihn zum Beispiel anzeigen, wenn sich der Mauszeiger über einer Schaltfläche befindet.
