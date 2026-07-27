---
title: Text in Menüs
description: Wie man Menüs Textinhalte hinzufügt.
---
# Text in Menüs

FancyMenu ermöglicht es dir, Menüs/Bildschirme über das **Text**-Element mit Textinhalten zu versehen.

Dieses Element ist scrollbar, unterstützt vollständiges Markdown und Zeilenumbruch, was es sehr leistungsfähig macht, um selbst komplexe Textinhalte darzustellen, aber es eignet sich auch hervorragend für einfache Einzeiler.

# Textinhalt

Das Text-Element kann seinen Inhalt auf viele Arten beziehen. Du kannst eine Quelle für den Textinhalt festlegen, die entweder eine direkte Klartexteingabe, eine lokale Textdatei im Assets-Verzeichnis von FancyMenu (`<game-directory>/config/fancymenu/assets/`), eine Web-Textdatei (per URL) oder eine lokale Textdatei ist, die über ein Resource Pack geladen wird.

Die Verwendung des Web-Quellentyps als Textquelle ist besonders nützlich, wenn du so etwas wie ein stets aktuelles Changelog, einen News-Ticker oder Ähnliches erstellen möchtest, ohne für dein Modpack ein Update veröffentlichen zu müssen.

Beachte, dass FancyMenu den Inhalt von Textquellen zwischenspeichert, damit er nicht ständig erneut geladen werden muss (was für die Performance sehr schlecht wäre). Der Inhalt wird nur für die aktive Sitzung zwischengespeichert, daher wird der Cache beim Neustart des Spiels gelöscht. Du kannst den Cache auch leeren, indem du FancyMenu über **Menüleiste -> Anpassung -> FancyMenu neu laden** neu lädst.

# Platzhalter

Das Text-Element unterstützt außerdem das Platzhaltersystem von FancyMenu, wodurch es möglich ist, Textinhalte dynamisch zu gestalten und auf verschiedene Änderungen an Menüs, Welten, Spielern usw. zu reagieren.

# Markdown anpassen oder deaktivieren

Wenn du die Farben für Überschriften oder andere mit Markdown zusammenhängende Dinge anpassen möchtest, klicke einfach mit der **rechten Maustaste** auf das Text-Element und dann auf **Markdown**. Im sich öffnenden Unterkontextmenü findest du zahlreiche Optionen, um das Aussehen und Verhalten des Markdown-Parsers anzupassen.

Falls du Markdown gar nicht parsen möchtest, was die Performance bei langen Textinhalten verbessern kann, kannst du Markdown im **Markdown**-Menü vollständig deaktivieren, indem du mit der **rechten Maustaste** auf das Text-Element klickst.

# Zeilenumbruch deaktivieren

Wenn du keinen Zeilenumbruch möchtest, kannst du ihn durch **Rechtsklick** auf das Text-Element deaktivieren.

# Scrollen deaktivieren und Scroll-Griffe ausblenden

Text-Elemente sind standardmäßig scrollbar und wenn das Element denkt, dass der Benutzer scrollen muss, um den gesamten Inhalt zu sehen, werden Scrollleisten/Griffe angezeigt. Das sind kleine, graue, halbtransparente Balken mit abgerundeten Kanten an der rechten und unteren Seite des Text-Elements (vertikale und horizontale Scrollleisten). Die Scroll-Griffe werden manchmal auch mit Schatten verwechselt.

Du kannst diese Griffe deaktivieren, indem du **Scrolling** im Menü deaktivierst, das sich beim **Rechtsklick** auf das Element öffnet. Dadurch wird das Scrollen generell deaktiviert, nicht nur die Griffe. Wenn du die Griffe nur unsichtbar machen möchtest, das Scrollen aber weiterhin nutzen willst, kannst du benutzerdefinierte Scroll-Griff-Texturen festlegen, indem du mit der rechten Maustaste auf das Element klickst. Lege dort einfach eine vollständig transparente Textur fest.

# Minecrafts Raw-Component-Textformat (Serialisierte JSON-Components)

Das Text-Element unterstützt das Raw-Component-Format von Minecraft NICHT. Dieses Format wird nur von Button- und Slider-Beschriftungen unterstützt.
