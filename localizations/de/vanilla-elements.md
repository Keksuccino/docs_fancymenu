---
title: Vanilla-Elemente
description: 'So passt du Elemente an, die standardmäßig zu Bildschirmen gehören.'
sourceBlobSha: 3943106d1e4f0722aad0d1578908262b7c8d92ec
---

# Vanilla-Elemente

FancyMenu ermöglicht es dir nicht nur, Bildschirmen neue Inhalte hinzuzufügen, sondern auch vorhandene Elemente aus dem Grundspiel (Vanilla) und sogar aus anderen Mods anzupassen.

## Vanilla-Schaltflächen und Schieberegler (Widgets)

Um die Schaltflächen und Schieberegler eines Bildschirms anzupassen, erstelle ein Layout für den aktuellen Bildschirm (kein [universelles Layout](/universal-layouts)) und klicke im Editor mit der rechten Maustaste auf die Elemente.

Sie verfügen über dieselben Einstellungen wie deine eigenen [Schaltflächen](/elements#button) und [Schieberegler](/elements#slider), etwa Texturen, Sounds und Tooltips. Nur ihr Aktionsskript lässt sich nicht ändern: Sie führen weiterhin dieselbe Aktion wie zuvor aus.

Vanilla-Elemente können nicht in [scrollbare Bereiche](/scrollable-areas) verschoben werden, da sie zum Menü selbst gehören.

### Beschriftungen

- **Beschriftung** und **Beschriftung beim Darüberfahren** ersetzen den Text einer Schaltfläche. Bei anderen Widgets, etwa Schiebereglern, heißen sie **Widget-Text** und **Widget-Text beim Darüberfahren**. Ohne diese Einstellungen behält das Widget seinen eigenen Text.
- **Ausrichtung der Beschriftung** positioniert die Beschriftung **Links**, **Zentriert** oder **Rechts** im Widget. Beschriftungen, die zu breit für das Widget sind, scrollen von einer Seite zur anderen – unabhängig von ihrer Ausrichtung.
- Mit **Skalierung der Beschriftung**, **Grundfarbe der Beschriftung**, **Farbe der Beschriftung beim Darüberfahren**, **Schatten der Beschriftung** und **Beschriftung beim Darüberfahren unterstreichen** kannst du Größe, Farben und Schatten der Beschriftung ändern.

Um die Beschriftungen mehrerer Schaltflächen gleichzeitig auszurichten, wähle sie mit `Strg` + Klick aus (siehe [Auswählen](/layout-editor#selecting)), klicke mit der rechten Maustaste auf eine davon und lege für alle die **Ausrichtung der Beschriftung** fest. Für die Beschriftungen aller Menüs verwende **Ausrichtung der Beschriftung** unter [Globale Anpassungen](/global-customizations#labels). Mit einer [Vorlage](/button-slider-templates) kannst du außerdem allen Schaltflächen eines Bildschirms denselben Beschriftungsstil zuweisen.

## Automatisierte Klicks

Vanilla- und Mod-Widgets verfügen über die Eigenschaft **Automatisierte Klicks**. Lege dafür eine ganze Zahl größer als `0` fest, damit beim Laden des Bildschirms so oft das ursprüngliche Verhalten des Widgets bei einem Linksklick ausgelöst wird. Wenn du den Wert beispielsweise auf `2` setzt, wird das Widget während der ersten Aktualisierung jedes neu geöffneten Bildschirms zweimal angeklickt. Der Standardwert `0` deaktiviert automatisierte Klicks.

Dabei handelt es sich um echte Widget-Klicks: Jeder Klick kann den Wert eines Schiebereglers oder einer Umschaltfläche ändern, den normalen Callback des Widgets ausführen oder sogar einen anderen Bildschirm öffnen. Teste das Ergebnis sorgfältig, besonders wenn du mehr als einen Klick einstellst.

Um Vanilla-/Mod-Widgets zu **verschieben** und ihre **Größe zu ändern**, musst du ihnen zuerst einen Ankerpunkt zuweisen. Klicke dazu mit der **rechten Maustaste** darauf und wähle **Ankerpunkt**. Stelle einen anderen Wert als **Original** ein, da dies der Standardanker für Vanilla-/Mod-Elemente ist.

Du kannst Vanilla-/Mod-Widgets auch **ausblenden**, indem du einfach mit der **rechten Maustaste** darauf klickst und **Löschen** auswählst. Sie werden dadurch nicht wirklich gelöscht, sondern nur ausgeblendet. Du kannst sie wiederherstellen, indem du auf **Menüleiste -> Element -> Gelöschte Vanilla-Elemente** klickst und mit der **linken Maustaste** die Elemente auswählst, die wieder sichtbar sein sollen.

> [!WARNING]
> Das Widget **Copyright** auf dem Titelbildschirm ist das einzige, das du **NICHT** ausblenden oder löschen kannst. Das ist beabsichtigt. Bitte entferne keine Copyright-Hinweise.

## Elemente des Titelbildschirms

Auf dem Titelbildschirm gibt es Elemente, die keine normalen Widgets sind (wie das Logo, der Begrüßungstext usw.) und die sich nicht verschieben oder anpassen lassen. Sie sind dafür vorgesehen, gelöscht und durch eigene Elemente ersetzt zu werden (zum Beispiel durch ein Bildelement für das Logo oder ein eigenes Begrüßungstext-Element anstelle des Vanilla-Begrüßungstextes).

Um sie zu löschen, klicke einfach mit der rechten Maustaste darauf. Wenn du sie später wiederherstellen möchtest, klicke auf **Menüleiste -> Element -> Gelöschte Vanilla-Elemente** und dann mit der **linken Maustaste** auf das Element, das wieder sichtbar sein soll.

## Fehlerbehebung: Vanilla-Elemente sind im Editor nicht sichtbar

Wenn du Vanilla-Elemente im Editor nicht sehen kannst, verwendest du wahrscheinlich ein **universelles Layout** anstelle eines Layouts **für den aktuellen Bildschirm**. Achte darauf, ein Layout für den aktuellen Bildschirm zu erstellen. Layouts für den aktuellen Bildschirm kannst du nur erstellen, wenn Anpassungen für diesen Bildschirm aktiviert sind.

## Fehlerbehebung: Anpassungen werden nicht übernommen

Wenn Anpassungen an Vanilla-Elementen außerhalb des Editors nicht übernommen werden, liegt das normalerweise daran, dass eine andere Mod das übergeordnete Menü der Vanilla-Elemente überschreibt oder verändert.

Ein gutes Beispiel für eine Mod, die einen Bildschirm bzw. ein Menü überschreibt, ist **Ice and Fire**. Diese Mod überschreibt den Titelbildschirm.

Dass Anpassungen auf Menüs nicht übernommen werden, betrifft nicht nur Vanilla-Elemente. Auch eigene Elemente, die Bildschirmen hinzugefügt wurden, werden wahrscheinlich nicht auf Menüs angewendet, wenn eine Mod diese überschreibt oder verändert.
