---
title: Erste Schritte
description: >-
  Die Welt von FancyMenu erwartet dich! Dies ist der Beginn von etwas
  Wunderbarem!
---

# Für Entwickler

Wenn du ein Entwickler bist und ein Add-on für FancyMenu erstellen oder FancyMenu in dein Mod integrieren möchtest, solltest du dir die [Entwicklerdokumentation](https://github.com/Keksuccino/FancyMenu-Dev-Docs/wiki) ansehen.

# Erste Schritte

FancyMenu zum ersten Mal zu benutzen kann etwas überwältigend sein, aber keine Sorge: Das meiste ist eigentlich ziemlich selbsterklärend, sobald du damit loslegst!

> Bitte **behalte im Hinterkopf**, dass diese Seite nur dazu dient, dir den Einstieg in FancyMenu zu erleichtern und dich bei deinen **allerersten Schritten** zu unterstützen.
Sieh dir unbedingt auch den Rest der Dokumentation an, um ausführlichere Informationen über die Funktionen von FancyMenu zu erhalten!
{.is-info}

# Die Menüleiste

Eines der ersten Dinge, die dir beim Start des Spiels auffallen werden, ist die **Menüleiste** oben in jedem Menü.

Die **Menüleiste** ist dein Einstiegspunkt zu praktisch allen Funktionen von FancyMenu, wie zum Beispiel **Layouts erstellen**, um Menüs zu **personalisieren**, den **Fenstertitel und das Symbol** zu ändern und vieles mehr.

> Falls du versehentlich einige Tasten gedrückt hast und die **Menüleiste verschwunden ist**, kannst du sie mit **STRG + ALT + C** wieder einblenden.
{.is-warning}

<img width="650" alt="menu_bar" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/menu_bar.png?raw=true">

# Dein erstes Layout

Da du wahrscheinlich Minecrafts Menüs anpassen möchtest, erzähle ich dir etwas über **Layouts**!

Layouts sind wie Anpassungsebenen für Menüs und ermöglichen es dir, neue Elemente hinzuzufügen und vorhandene anzupassen.

So erstellst du ein neues Layout für ein **bestimmtes Menü**:
1. Öffne das Menü, für das du ein Layout erstellen möchtest (zum Beispiel den Titelbildschirm)
2. Öffne im **Menüleisten**-Bereich den Reiter **Anpassung**

Anpassungen sind für alle Menüs standardmäßig deaktiviert, und du musst sie für jedes Menü einzeln aktivieren, das du anpassen möchtest. Klicke also zuerst auf den Eintrag **"Aktuelle Bildschirm-Anpassung: Deaktiviert"**, wodurch der Schalter auf **Aktiviert** umgestellt wird.

<img width="475" alt="toggle_customizations" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/toggle_customizations.png?raw=true">

Klicke danach auf **Layouts -> Neu -> Für aktuellen Bildschirm**.

Dadurch öffnet sich der **Layout-Editor**, in dem du Elemente zum Layout hinzufügen und Vanilla- sowie Mod-Elemente (wie Buttons) anpassen kannst.

<img width="550" alt="new_layout_current" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/new_layout_current.png?raw=true">

## Das Layout bearbeiten

Die meisten Anpassungsoptionen erreichst du, indem du mit der **rechten Maustaste auf den Hintergrund des Editors** klickst.
Dadurch öffnet sich ein Kontextmenü mit vielen Optionen, zum Beispiel zum Anpassen des **Menühintergrunds** oder zum **Hinzufügen von Elementen** zum Layout.

<br>
<img width="350" alt="context_menu" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/context_menu.png?raw=true">

## Elemente zu Layouts hinzufügen

Um deinem Layout ein neues Element hinzuzufügen, klicke mit der **rechten Maustaste** auf den Hintergrund des Editors.

Im sich öffnenden Kontextmenü klickst du auf **Neues Element** und wählst einen der vielen Elementtypen aus.

<img width="525" alt="add_element" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/add_element.png?raw=true">

## Elemente anpassen

Um ein Element anzupassen, klicke mit der **rechten Maustaste** darauf. Dadurch öffnet sich ein Kontextmenü mit allem, was du für diesen Elementtyp anpassen kannst.

Neben den von dir hinzugefügten Elementen kannst du auch Vanilla-Elemente anpassen (allerdings gibt es dort manchmal weniger Optionen)

<img width="525" alt="element_customization" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/element_customization.png?raw=true">

> [!IMPORTANT]
> Einige Kontextmenüs wie dieses sind **scrollbar**!

## Elemente positionieren

Jedes Element in FancyMenu ist mit einem **Ankerpunkt** verbunden.

Ankerpunkte sind notwendig, um die Position eines Elements zu berechnen, und wenn sie richtig verwendet werden, verhindern sie, dass sich Elemente überlappen, außerhalb des Bildschirms landen oder beim Ändern der Fenstergröße an die falsche Stelle verschoben werden.

Sie sind der Ausgangspunkt, von dem aus die Position des Elements berechnet wird.

Standardmäßig sind Elemente mit dem Ankerpunkt **"Mitte des Bildschirms"** verbunden, also im Grunde mit genau der Bildschirmmitte, unabhängig von der Fenstergröße.
Angenommen, ein Element ist 2 Zentimeter von der Bildschirmmitte entfernt und mit dem Anker **"Mitte des Bildschirms"** verbunden. In diesem Fall wird das Element **immer** 2 Zentimeter von der Bildschirmmitte entfernt sein, unabhängig von der Fenstergröße.

Du kannst den Ankerpunkt, mit dem ein Element verbunden ist, sehen, wenn du es ziehst. Dabei werden standardmäßig auch alle anderen Ankerpunkte angezeigt. Während du ein Element ziehst, kannst du mit der Maus über einen Ankerpunkt fahren, um den Anker des Elements auf diesen Ankerpunkt zu ändern.

Du kannst sogar ein Element selbst als Ankerpunkt für andere Elemente verwenden! Fahre einfach mit einem Element über ein anderes, während du es ziehst, und der Ankerpunkt des gezogenen Elements wird auf das angezeigte Element geändert.

**[Erfahre mehr darüber, wie du deine Elemente positionierst.](/positioning-elements)**

<img width="650" alt="anchor_points" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/anchor_points.png?raw=true">

## Deine Arbeit speichern

Vergiss nicht, dein Meisterwerk zu speichern!

Oben rechts im Editor siehst du einen Hinweis auf **"Nicht gespeicherte Änderungen"**, wenn du deine Änderungen vor dem Schließen speichern musst.

Speichere deine Arbeit, indem du auf **Layout -> Speichern** klickst!

<img width="375" alt="save_your_work" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/save_your_work.png?raw=true">

> [!TIP]
> Du kannst deine Arbeit auch mit der Tastenkombination **STRG + S** speichern

*Glückwunsch! Jetzt kannst du Minecrafts Menüs viel schöner gestalten!*
