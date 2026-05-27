---
title: Text in Menüs
description: Wie man Textinhalte zu Menüs hinzufügt.
---
# Text in Menüs

FancyMenu ermöglicht es dir, Menüs/Bildschirmen über das **Text**-Element Textinhalte hinzuzufügen.

Dieses Element ist scrollbar, unterstützt vollständig Markdown und Zeilenumbrüche, wodurch es sehr leistungsstark ist, um auch komplexe Textinhalte darzustellen, eignet sich aber genauso gut für einfache Einzeiler.

# Textinhalt

Das Text-Element kann seinen Inhalt auf viele Arten beziehen. Du kannst eine Quelle für seinen Textinhalt festlegen, die entweder eine direkte Klartexteingabe, eine lokale Textdatei im `assets`-Ordner von FancyMenu (`/config/fancymenu/assets/`), eine Web-Textdatei (per URL) oder eine lokale Textdatei ist, die über ein Ressourcenpaket geladen wird.

Die Web-Quelle als Textquelle zu verwenden ist besonders nützlich, wenn du so etwas wie ein stets aktuelles Changelog, einen News-Ticker oder Ähnliches erstellen möchtest, ohne dafür ein Update für dein Modpack veröffentlichen zu müssen.

Beachte, dass FancyMenu den Inhalt von Textquellen zwischenspeichert, damit er nicht ständig erneut abgerufen werden muss (was für die Leistung sehr schlecht wäre). Der Inhalt wird nur für die aktive Sitzung zwischengespeichert, daher wird der Cache beim Neustart des Spiels gelöscht. Du kannst den Cache auch leeren, indem du FancyMenu über **Menüleiste -> Anpassung -> FancyMenu neu laden** neu lädst.

# Platzhalter

Das Text-Element unterstützt außerdem das Platzhaltersystem von FancyMenu, wodurch es möglich wird, Textinhalte dynamisch zu gestalten und auf verschiedene Änderungen an Menüs, Welten, Spielern usw. zu reagieren.

# Markdown anpassen oder deaktivieren

Wenn du die Farben für Überschriften oder andere mit Markdown zusammenhängende Dinge anpassen möchtest, **klicke mit der rechten Maustaste** auf das Text-Element und dann auf **Markdown**. Im sich öffnenden Unter-Kontextmenü findest du viele Optionen, um das Aussehen und Verhalten des Markdown-Parsers anzupassen.

Falls du Markdown-Parsing überhaupt nicht möchtest, was die Leistung bei langen Textinhalten verbessern kann, kannst du Markdown im **Markdown**-Menü vollständig deaktivieren, indem du **mit der rechten Maustaste** auf das Text-Element klickst.

# Zeilenumbruch deaktivieren

Wenn du keinen Zeilenumbruch möchtest, kannst du ihn deaktivieren, indem du **mit der rechten Maustaste** auf das Text-Element klickst.

# Scrollen deaktivieren & Scroll-Griffe ausblenden

Text-Elemente sind standardmäßig scrollbar, und wenn das Element denkt, dass der Benutzer scrollen muss, um den gesamten Inhalt zu sehen, zeigt es seine Scrollbalken/-griffe an. Das sind kleine, graue, halbtransparente Balken (mit abgerundeten Kanten) auf der rechten und unteren Seite des Text-Elements (vertikale und horizontale Scrollbalken). Die Scroll-Griffe werden manchmal auch für Schatten gehalten.

Du kannst diese Griffe deaktivieren, indem du **Scrolling** in dem Menü ausschaltest, das sich öffnet, wenn du **mit der rechten Maustaste** auf das Element klickst. Dadurch wird das Scrollen generell deaktiviert, nicht nur die Griffe. Wenn du nur möchtest, dass die Griffe unsichtbar sind, du aber weiterhin scrollen können willst, kannst du benutzerdefinierte Texturen für die Scroll-Griffe festlegen, indem du mit der rechten Maustaste auf das Element klickst. Setze dort einfach eine vollständig transparente Textur.

# Minecrafts Raw-Component-Textformat (serialisierte JSON-Components)

Das Text-Element unterstützt das Raw-Component-Format von Minecraft NICHT. Dieses Format wird nur von Button- und Slider-Beschriftungen unterstützt.
