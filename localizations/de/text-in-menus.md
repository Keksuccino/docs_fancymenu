---
title: Text in Menüs
description: Wie man Menüs Textinhalte hinzufügt.
---

# Text in Menüs

FancyMenu ermöglicht es dir, Menüs/Bildschirmen über das **Text**-Element Textinhalte hinzuzufügen.

Dieses Element ist scrollbar, unterstützt vollständiges Markdown und Zeilenumbrüche, was es sehr leistungsfähig macht, um selbst komplexe Textinhalte anzuzeigen. Es eignet sich aber auch hervorragend für einfache Einzeiler.

## Textinhalt

Das Text-Element kann seinen Inhalt auf viele Arten abrufen. Du kannst eine Quelle für seinen Textinhalt festlegen, etwa eine direkte Texteingabe, eine lokale Textdatei im `assets`-Ordner von FancyMenu (`/config/fancymenu/assets/`), eine Web-Textdatei (per URL) oder eine lokale Textdatei, die über ein Resource Pack geladen wird.

Die Web-Quellenart als Textquelle zu verwenden ist besonders nützlich, wenn du etwas wie ein Changelog erstellen möchtest, das immer aktuell ist, oder einen News-Ticker und Ähnliches, ohne dafür ein Update für dein Modpack veröffentlichen zu müssen.

Beachte, dass FancyMenu den Inhalt von Textquellen zwischenspeichert, damit er nicht ständig neu abgerufen werden muss (was die Leistung stark beeinträchtigen würde). Der Inhalt wird nur für die aktive Sitzung zwischengespeichert, daher wird der Cache beim Neustart des Spiels geleert. Du kannst den Cache auch leeren, indem du FancyMenu über **Menüleiste -> Anpassung -> FancyMenu neu laden** neu lädst.

## Platzhalter

Das Text-Element unterstützt außerdem das Platzhalter-System von FancyMenu, wodurch es möglich wird, Textinhalte dynamisch zu gestalten und auf verschiedene Änderungen an Menüs, Welten, Spielern usw. zu reagieren.

## Markdown anpassen oder deaktivieren

Wenn du die Farben für Überschriften oder andere Markdown-bezogene Dinge anpassen möchtest, klicke einfach mit der **rechten Maustaste** auf das Text-Element und dann auf **Markdown**. Im Untermenü, das sich öffnet, findest du zahlreiche Optionen, um das Aussehen und Verhalten des Markdown-Parsers anzupassen.

Falls du überhaupt keine Markdown-Analyse möchtest, was die Leistung bei langen Textinhalten verbessern kann, kannst du Markdown im **Markdown**-Menü vollständig deaktivieren, indem du mit der **rechten Maustaste** auf das Text-Element klickst.

## Zeilenumbrüche deaktivieren

Wenn du keine Zeilenumbrüche möchtest, kannst du sie per **Rechtsklick** auf das Text-Element deaktivieren.

## Scrollen deaktivieren

Text-Elemente sind standardmäßig scrollbar, und wenn das Element meint, dass der Nutzer scrollen muss, um den gesamten Inhalt zu sehen, zeigt es Scrollleisten an – kleine graue Balken an der rechten und unteren Seite des Text-Elements (vertikale und horizontale Scrollleisten).

Du kannst diese Balken deaktivieren, indem du **Scrolling** im Menü ausschaltest, das sich beim **Rechtsklick** auf das Element öffnet. Dadurch wird das Scrollen insgesamt deaktiviert, nicht nur die Balken. Wenn du stattdessen möchtest, dass die Balken unsichtbar sind, kannst du benutzerdefinierte Scrollleisten-Texturen festlegen, indem du mit der rechten Maustaste auf das Element klickst. Setze dort einfach eine vollständig transparente Textur.

## Minecrafts Roh-Komponenten-Textformat (serialisierte JSON-Komponenten)

Das Text-Element unterstützt das Roh-Komponenten-Format von Minecraft **nicht**. Dieses Format wird nur von Button- und Slider-Beschriftungen unterstützt.
