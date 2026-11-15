---
title: Variablen
description: So erstellst und verwendest du Variablen.
sourceBlobSha: dcd1512bc7f20f3ab535205f24a67c6489231e11
---

# Variablen in FancyMenu

Variablen speichern Textwerte, die von Layouts, Aktionen, Platzhaltern, Anforderungen, Listenern, Zeitplänen und benutzerdefinierten GUIs wiederverwendet werden können.

## Variablen erstellen

So erstellst du eine Variable in FancyMenu:

1. Stelle sicher, dass du dich momentan nicht im Layout-Editor befindest. 
2. Klicke auf die Menüleiste oben auf dem Bildschirm.
3. Gehe zu **Anpassung -> Variablen -> Variablen verwalten**.
4. Klicke im angezeigten Bildschirm „Variablen verwalten“ auf die Schaltfläche **Variable hinzufügen**.
5. Gib einen Namen für deine neue Variable ein und klicke auf **OK**.

Das war's! Deine Variable ist bereit zur Verwendung. Du findest sie im Bildschirm „Variablen verwalten“ in der Liste.

Das Fenster „Variablen verwalten“ unterstützt ein Kontextmenü per Rechtsklick, Tastaturnavigation, Kopieren/Einfügen, Rückgängig/Wiederholen, Suchen durch Eingabe, **Entf** zum Löschen sowie **Strg/Befehlstaste + S** zum Speichern.

## Variablenwerte festlegen

Eine leere Variable ist allein nicht besonders nützlich. Damit Variablen für dich arbeiten können, musst du Daten in ihnen speichern. In FancyMenu wird dies als „Variablenwert festlegen“ bezeichnet. 

Es gibt zwei grundlegende Möglichkeiten, den Wert einer Variable festzulegen:

1. Suche im Bildschirm „Variablen verwalten“ die Variable in der Liste, klicke sie an und klicke anschließend auf **Wert festlegen**. Gib die Daten ein, die du speichern möchtest.

2. Verwende beim Anpassen deines Menüs die [Aktion **Variablenwert festlegen**](./action-scripts#set-variable-value-fm-variable-set_variable) bei einem [Schaltflächen](./elements#button)-, [Schieberegler](./elements#slider)- oder [Ticker](./elements#ticker)-Element.

Erstelle beispielsweise eine Variable namens `clicks` und füge einem Button die [Aktion **Variablenwert festlegen**](./action-scripts#set-variable-value-fm-variable-set_variable) hinzu:

```
clicks:{"placeholder":"calc","values":{"expression":"{"placeholder":"getvariable","values":{"name":"clicks"}} + 1"}}
```

So funktioniert das:
1. Der [Platzhalter **Gespeicherte Variable abrufen**](./placeholders#get-variable-value-fm-variable-getvariable) ruft den aktuellen Wert der Variable `clicks` ab.
2. Der [Platzhalter **Rechner**](./placeholders#calculator-calc) nimmt diesen Wert und addiert 1 dazu.
3. Das Ergebnis wird mithilfe der [Aktion **Variablenwert festlegen**](./action-scripts#set-variable-value-fm-variable-set_variable) wieder in `clicks` gespeichert.

Bei jedem Klick auf den Button wird die Variable `clicks` also um 1 erhöht und zählt dadurch effektiv die Gesamtzahl der Klicks.

## Variablen verwenden

Nachdem deine Variablen Daten enthalten, kannst du diese Daten in verschiedenen Bereichen deiner Menükonfiguration verwenden:

* [**Anforderungen zum Laden**](./conditions): Überprüfe den Wert einer Variable, um zu steuern, wann Elemente angezeigt werden. Zeige beispielsweise ein Element an, wenn `clicks` größer als 5 ist, indem du [**Ist eine Zahl**](./conditions#is-number-fancymenu_visibility_requirement_is_number) mit dem [Platzhalter **Gespeicherte Variable abrufen**](./placeholders#get-variable-value-fm-variable-getvariable) kombinierst.

* **Platzhalter**: Füge mit dem [Platzhalter **Gespeicherte Variable abrufen**](./placeholders#get-variable-value-fm-variable-getvariable) eine Variable in Text ein, zum Beispiel `{"placeholder":"getvariable","values":{"name":"clicks"}}`.

* **Verschachtelte Platzhalter**: Du kannst den [Platzhalter **Gespeicherte Variable abrufen**](./placeholders#get-variable-value-fm-variable-getvariable) innerhalb des [Platzhalters **Rechner**](./placeholders#calculator-calc) verwenden.

* **Aktionen**: Variablen können dynamisches Verhalten ermöglichen:
  - Verwende eine **IF**-Anweisung in einem [Aktionsskript](./action-scripts#what-are-statements) zusammen mit [**Ist eine Zahl**](./conditions#is-number-fancymenu_visibility_requirement_is_number) und dem [Platzhalter **Gespeicherte Variable abrufen**](./placeholders#get-variable-value-fm-variable-getvariable).
  - Kombiniere den [Platzhalter **Gespeicherte Variable abrufen**](./placeholders#get-variable-value-fm-variable-getvariable) mit [**Text in Zwischenablage kopieren**](./action-scripts#copy-text-to-clipboard-copytoclipboard).
  - Verwende Variablen in [**Bildschirm oder benutzerdefinierte GUI öffnen**](./action-scripts#open-screen-or-custom-gui-opengui), um anhand des gespeicherten Fortschritts oder der gespeicherten Einstellungen einen Bildschirm auszuwählen.

## Beispiele für Variablen

Hier sind einige Beispiele, die dich zur eigenen Verwendung von Variablen inspirieren sollen:

1. **Höchstpunktzahl**: Erstelle eine Variable `highscore` und einen Button, der sie auf die aktuelle Punktzahl des Spielers setzt, wenn diese höher als der bisherige Wert ist. Zeige sie mit dem [Platzhalter **Gespeicherte Variable abrufen**](./placeholders#get-variable-value-fm-variable-getvariable) an.

2. **Schwierigkeitsauswahl**: Erstelle Variablen für verschiedene Spielschwierigkeitsgrade wie `easy`, `medium` und `hard`. Verwende Buttons, um die Schwierigkeitsvariable festzulegen, und zeige Elemente abhängig vom ausgewählten Schwierigkeitsgrad an oder blende sie aus.

3. **Tutorialfortschritt**: Füge Variablen hinzu, um den Fortschritt des Spielers in einem Tutorial zu verfolgen, beispielsweise `tutorial_step`. Erhöhe die Variable, wenn der Spieler jeden Schritt abschließt, und verwende Anforderungen zum Laden, um nach und nach weitere Teile des Menüs anzuzeigen.

## Persistenz, Gültigkeitsbereich und Speicherung

Variablen werden von der aktuellen Minecraft-Instanz gemeinsam verwendet. Sie sind nicht nach Layout, Welt, Server oder Spieler getrennt.

Werte werden sofort in `<game-directory>/config/fancymenu/user_variables.db` gespeichert und bleiben auch nach einem Neustart erhalten.

- **Beim Start zurücksetzen** leert diese Variable beim nächsten Spielstart.
- [**Alle Variablen löschen**](./action-scripts#clear-all-variables-fm-variable-clear_variables) entfernt alle gespeicherten Variablenwerte.
- Bei Namen wird zwischen Groß- und Kleinschreibung unterschieden. Verwende einfache, eindeutige Namen wie `tutorial_step`.

Der [Platzhalter **Gespeicherte Variable abrufen**](./placeholders#get-variable-value-fm-variable-getvariable) gibt `0` zurück, wenn die angegebene Variable nicht existiert oder ihr gespeicherter Wert leer ist. Dieser Ersatzwert ist bei Vergleichen und Rechnerausdrücken wichtig.

Die [Aktion **Variablenwert festlegen**](./action-scripts#set-variable-value-fm-variable-set_variable) verwendet `variable_name:variable_value` und teilt am ersten Doppelpunkt auf. Daher darf der Wert weitere Doppelpunkte enthalten.

Speichere keine Passwörter, Token oder andere vertrauliche Daten in FancyMenu-Variablen. Sie werden als lesbare Konfigurationsdaten gespeichert.
