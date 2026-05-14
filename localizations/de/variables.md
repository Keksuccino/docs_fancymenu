---
title: Variablen
description: Wie man Variablen erstellt und verwendet.
---

# Variablen in FancyMenu

Variablen sind ein leistungsstarkes Feature in FancyMenu, mit dem du Informationen speichern und in deinen Menü-Anpassungen immer wieder verwenden kannst. Sie funktionieren wie Behälter, in die du verschiedene Datentypen legen, jedem Behälter einen Namen geben und später über den Variablennamen wieder darauf zugreifen kannst. Variablen eröffnen dir unzählige Möglichkeiten, dynamische Menüs zu erstellen, die sich je nach den von dir definierten Bedingungen verändern.

## Variablen erstellen

So erstellst du eine Variable in FancyMenu:

1. Stelle sicher, dass du dich nicht gerade im Layout-Editor befindest.
2. Klicke auf die Menüleiste oben auf dem Bildschirm.
3. Gehe zu **Anpassung -> Variablen -> Variablen verwalten**.
4. Klicke im Fenster „Variablen verwalten“, das erscheint, auf die Schaltfläche **Variable hinzufügen**.
5. Gib einen Namen für deine neue Variable ein und klicke auf **OK**.

Das war's! Deine Variable ist nun einsatzbereit. Du kannst sie im Fenster „Variablen verwalten“ aufgelistet sehen.

FancyMenu 3.9.0 überarbeitet das Fenster „Variablen verwalten“. Wichtige Aktionen sind über ein Rechtsklick-Kontextmenü verfügbar, die Liste unterstützt die Tastaturnavigation, Variablen können kopiert/eingefügt werden, Änderungen können rückgängig gemacht/wiederholt werden, das Tippen startet eine Suche, **ENTF** löscht die ausgewählte Variable und **STRG + S** bestätigt das Fenster.

## Variablenwerte festlegen

Eine leere Variable ist für sich allein nicht besonders nützlich. Damit Variablen für dich arbeiten, musst du Daten in sie eintragen. In FancyMenu nennt man das „den Variablenwert festlegen“.

Es gibt zwei Hauptwege, einen Variablenwert festzulegen:

1. Suche im Fenster „Variablen verwalten“ die Variable in der Liste, klicke sie an und dann auf **Wert festlegen**. Gib die Daten ein, die gespeichert werden sollen.

2. Verwende beim Anpassen deines Menüs die Aktion **Variable setzen** für ein Button-, Slider- oder Ticker-Element. Mit dieser Aktion gibst du den Variablennamen und den zu speichernden Wert an. Wenn jemand beispielsweise auf eine Schaltfläche mit dieser Aktion klickt, wird die Variable mit dem neuen Wert aktualisiert.

Nehmen wir zum Beispiel an, du erstellst eine Variable namens `clicks`, um zu zählen, wie oft eine Schaltfläche gedrückt wird. Du würdest der Schaltfläche die Aktion **Variable setzen** hinzufügen und in dem Wert der Aktion einen Platzhalter verwenden, um den Klickzähler jedes Mal zu erhöhen, etwa so:

```
clicks:{"placeholder":"calc","values":{"expression":"{"placeholder":"getvariable","values":{"name":"clicks"}} + 1"}}
```

So funktioniert das:
1. Der Platzhalter **Gespeicherte Variable abrufen** ruft den aktuellen Wert der Variable `clicks` ab.
2. Der Platzhalter **Rechner** nimmt diesen Wert und addiert 1.
3. Das Ergebnis wird anschließend mit der Aktion **Variable setzen** wieder in der Variable `clicks` gespeichert.

Jedes Mal, wenn die Schaltfläche geklickt wird, erhöht sich die Variable `clicks` also um 1 und zählt damit die Gesamtzahl der Klicks.

## Variablen verwenden

Jetzt, da deine Variablen Daten enthalten, kannst du diese in verschiedenen Bereichen deiner Menü-Anpassung verwenden:

* **Ladeanforderungen**: Du kannst den Wert einer Variable in einer Ladeanforderung prüfen, um festzulegen, wann bestimmte Menuelemente angezeigt werden. Zum Beispiel könntest du ein Element nur anzeigen lassen, wenn die Variable `clicks` größer als 5 ist, indem du die Anforderung **Ist Zahl** mit dem Platzhalter **Gespeicherte Variable abrufen** kombinierst.

* **Platzhalter**: Variablen können mit dem Platzhalter **Gespeicherte Variable abrufen** in Text eingefügt werden. Wenn du ein Textelement hast, könntest du `{"placeholder":"getvariable","values":{"name":"clicks"}}` verwenden, um den aktuellen Wert der Variable „clicks“ anzuzeigen.

* **Verschachtelte Platzhalter**: Du kannst Variablen sogar in anderen Platzhaltern verwenden! Das Beispiel zum Klickzählen oben hat das gezeigt, indem der Platzhalter **Gespeicherte Variable abrufen** innerhalb des Platzhalters **Rechner** verwendet wurde.

* **Aktionen**: Variablen können in Aktionen verwendet werden, um dynamisches Verhalten auf Grundlage von Variablenwerten zu erzeugen. Hier sind einige Beispiele:
    - Verwende eine **IF**-Anweisung in einem Aktionsskript, um den Wert einer Variable mit einer Kombination aus der Ladeanforderung **Ist Zahl** und der Aktion **Gespeicherte Variable abrufen** zu prüfen und je nach Ergebnis unterschiedliche Aktionen auszuführen. Zum Beispiel könntest du eine Schaltfläche haben, die sagt: „Du hast mich X-mal geklickt!“, und einen IF-Block verwenden, um eine besondere Nachricht anzuzeigen, wenn die Anzahl der Klicks über 10 liegt.
    - Kombiniere den Platzhalter **Gespeicherte Variable abrufen** mit der Aktion **In die Zwischenablage kopieren**, damit Benutzer den Wert einer Variable in die Zwischenablage kopieren können.
    - Verwende Variablen in der Aktion **GUI öffnen**, um unterschiedliche Bildschirme je nach Fortschritt oder Vorlieben des Benutzers zu laden, die du mit Variablen nachverfolgst.

## Variablenbeispiele

Hier sind einige Beispiele, die dich für deine eigenen Variablen inspirieren sollen:

1. **Highscore**: Erstelle eine Variable `highscore` und eine Schaltfläche, die sie auf den aktuellen Punktestand des Spielers setzt, wenn dieser höher ist als der vorhandene Wert. Zeige den Highscore im Menü mit dem Platzhalter **Gespeicherte Variable abrufen** an.

2. **Schwierigkeitsauswahl**: Lege Variablen für verschiedene Spielschwierigkeiten an, etwa `easy`, `medium` und `hard`. Verwende Schaltflächen, um die Schwierigkeitsvariable zu setzen, und blende Elemente basierend auf der ausgewählten Schwierigkeit ein oder aus.

3. **Tutorial-Fortschritt**: Füge Variablen hinzu, um den Fortschritt des Spielers durch ein Tutorial zu verfolgen, etwa `tutorial_step`. Erhöhe die Variable, während sie jeden Schritt abschließen, und verwende Ladeanforderungen, um nach und nach mehr vom Menü freizugeben.

Variablen in Kombination mit den anderen Funktionen von FancyMenu geben dir unglaubliche Flexibilität, um Menüs zu erstellen, die auf die Aktionen und Vorlieben jedes Spielers zugeschnitten sind. Experimentiere mit verschiedenen Variablen-Setups, um das volle Potenzial deiner Menü-Anpassungen freizuschalten!
