---
title: Element-Animator
description: Wie man Elemente mit Keyframes mithilfe des Element-Animators animiert.
---

# Element-Animator

Der **Animator** ist ein Element, mit dem du andere Elemente animieren kannst. Mit diesem Element kannst du die **Größe**, **Position** und den **Ankerpunkt** eines anderen Elements im Laufe der Zeit mithilfe von Keyframes sanft verändern. Keyframes sind wie Schnappschüsse, die festhalten, wie das Element zu einem bestimmten Zeitpunkt aussehen soll. Das Animator-Element spielt diese Schnappschüsse dann der Reihe nach ab, um flüssige Bewegungen zu erzeugen.

> [!WARNING]
> Der **Element-Animator** ermöglicht dir die Steuerung von **Position, Größe und Ankerpunkt** von Elementen. Es ist **NICHT** möglich, andere Einstellungen von Elementen zu steuern, wie z. B. Deckkraft, Sichtbarkeit, Rotation usw.!

# Video-Tutorial

Da viele von euch etwas verwirrt darüber waren, wie der Animator funktioniert, habe ich ein kleines Video gemacht, das zeigt, wie man damit arbeitet.

[FancyMenu | How to Use the Element Editor - YouTube](https://www.youtube.com/watch?v=F9S8cIPssww) (youtu.be/F9S8cIPssww)

<a href="https://www.youtube.com/watch?v=F9S8cIPssww" target="_blank" rel="noopener noreferrer">
  <img width="636" alt="Screenshot_2" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/element_animator_video_thumbnail.png" />
</a>

# Hinzufügen des Animator-Elements

1. **Hintergrund rechtsklicken:**  
   Klicke im Layout-Editor mit der rechten Maustaste auf den Hintergrund.

2. **Neues Element -> Element-Animator auswählen:**  
   Gehe im erscheinenden Menü zu **Neues Element** und klicke auf **Element-Animator**. Dadurch wird das Animator-Element zu deinem Layout hinzugefügt.

3. **Einrichten:**  
   Nach dem Hinzufügen erscheint das Animator-Element mit seinen Standardeinstellungen. Du kannst Optionen wie Looping oder Farbe ändern, indem du den Animator rechtsklickst und im Menü eine Option auswählst.

# Keyframes verwalten

Keyframes sind wie Lesezeichen, die dem Animator mitteilen, wie das Element zu einem bestimmten Zeitpunkt aussehen soll.

## Den Keyframe-Editor öffnen

- **Editor öffnen:**  
  Klicke mit der rechten Maustaste auf das Animator-Element und wähle **Keyframes bearbeiten** (oder **Keyframes verwalten**). Dadurch öffnet sich ein स्क्रीन, in dem du Keyframes hinzufügen, bearbeiten oder löschen kannst.

## Keyframes aufnehmen und hinzufügen

- **Aufnahme starten:**  
  Drücke im Keyframe-Editor die **`R`-Taste**, um die Aufnahme zu starten. Während der Aufnahme ändert sich die Vorschau-Box ihre Farbe, um anzuzeigen, dass sie aktiv ist.
  
- **Vorschau ändern:**  
  Verschiebe oder skaliere die Vorschau-Box, um das gewünschte Aussehen festzulegen. Im Offset-Modus bleibt die Vorschau auf ein Fadenkreuz zentriert, sodass Änderungen als Offsets angezeigt werden.
  
- **Keyframe hinzufügen:**  
  Drücke die **`K`-Taste**, um das aktuelle Aussehen als Keyframe zu speichern. Dieser Keyframe speichert Position, Größe und Ankereinstellungen der Vorschau.

## Keyframes bearbeiten

- **Keyframe auswählen:**  
  Klicke auf einen Keyframe-Marker in der Zeitleiste. Du kannst außerdem **Strg** gedrückt halten und klicken, um mehrere auszuwählen.
  
- **Keyframe verschieben:**  
  Ziehe den Keyframe-Marker nach links oder rechts, um seine Zeit zu ändern. Du kannst auch Folgendes verwenden:
  - **Pfeil nach links:** um ihn 100 ms früher zu verschieben.
  - **Pfeil nach rechts:** um ihn 100 ms später zu verschieben.
  
- **Vorschau fein anpassen:**  
  Wenn ein Keyframe ausgewählt ist, passe die Vorschau-Box an, indem du sie verschiebst oder ihre Größe änderst. Verwende **Strg + Z**, um Änderungen rückgängig zu machen, und **Strg + Y**, um sie bei Bedarf wiederherzustellen.

## Keyframes entfernen

- **Keyframe löschen:**  
  Wähle einen Keyframe aus und drücke die **Entf-Taste**, um ihn zu entfernen.
  
- **Mehrere Keyframes löschen:**  
  Du kannst mehrere Keyframes auswählen (zum Beispiel mit **Strg + A**, um alle auszuwählen) und dann Entf drücken, um sie alle zu entfernen.

## Keyframe-Glättung

Die Keyframe-Glättung ist eine Funktion, die dir hilft, deine Keyframes gleichmäßig zu verteilen. Dadurch wirkt deine Animation konsistenter und flüssiger.

- **Mehrere Keyframes auswählen:**  
  Wähle zunächst zwei oder mehr Keyframes aus, die du glätten möchtest (verwende **Strg + Klick** oder **Strg + A**).

- **Auf den Glättungs-Button klicken:**  
  Klicke in der unteren Symbolleiste des Keyframe-Editors auf den Button **Distance Smoothing**.

- **Neuen Abstand eingeben:**  
  Es erscheint ein kleines Eingabefeld. Gib einen Wert (in Millisekunden) ein, um denselben zeitlichen Abstand zwischen jedem ausgewählten Keyframe festzulegen.

- **Glättung anwenden:**  
  Drücke die Eingabetaste, um die Glättung anzuwenden. Die Keyframes werden so angepasst, dass die Zeitabstände zwischen ihnen gleichmäßig sind.

# Vorschau deiner Animation

Nachdem du Keyframes aufgenommen hast, kannst du sehen, wie deine Animation aussehen wird:

- **Animation abspielen:**  
  Drücke im Keyframe-Editor die **`P`-Taste** oder klicke auf den Play-Button. Die Vorschau startet von Anfang an und zeigt, wie sich die Vorschau-Box im Laufe der Zeit verändert.
  
- **Hinweis zum Looping:**  
  Während der Vorschau im Keyframe-Editor wird die Animation **nicht** in einer Schleife abgespielt. Das bedeutet, sie läuft nur einmal von Anfang bis Ende. Looping ist erst aktiv, wenn das Animator-Element in deinem finalen Layout auf ein Zielelement angewendet wird.
  
- **Vorschau pausieren:**  
  Drücke die **`P`-Taste** erneut, um die Animation zu pausieren, wenn du an einer bestimmten Stelle anhalten möchtest.
  
- **Fortschrittsbalken ziehen:**  
  Falls verfügbar, kannst du den Zeitachsenmarker ziehen, um zu prüfen, wie die Animation zu einem bestimmten Zeitpunkt aussieht.

# Zielelemente auswählen

Nachdem du deine Keyframes eingerichtet hast, musst du auswählen, welche Layoutelemente animiert werden sollen:

1. **Zielverwaltung öffnen:**  
   Klicke mit der rechten Maustaste auf das Animator-Element und wähle **Ziele verwalten**.
  
2. **Ziele hinzufügen:**  
   Klicke auf **Ziel hinzufügen**, um eine Liste der verfügbaren Elemente anzuzeigen. Wähle die Elemente aus, die du animieren möchtest.
  
3. **Ziele entfernen:**  
   Um ein Ziel zu entfernen, öffne die Verwaltung und klicke auf **Ziel entfernen**.

Wenn die Animation im finalen Layout abgespielt wird, verwendet der Animator deine Keyframes, um Größe, Position und mehr der ausgewählten Elemente zu ändern. Looping wird hier angewendet, wenn du es aktiviert hast.

# Tastenkürzel

Verwende diese Tastenkürzel im Keyframe-Editor, um schneller zu arbeiten:

- **`R`-Taste:** Aufnahme starten oder stoppen.
- **`T`-Taste:** Aufnahme pausieren oder fortsetzen.
- **`P`-Taste:** Animation in der Vorschau abspielen oder pausieren.
- **`K`-Taste:** Einen neuen Keyframe zur aktuellen Zeit hinzufügen.
- **Pfeiltasten links/rechts:**  
  - **Pfeil nach links:** Einen Keyframe 100 ms früher verschieben.
  - **Pfeil nach rechts:** Einen Keyframe 100 ms später verschieben.
- **Entf-Taste:** Den/die ausgewählten Keyframe(s) entfernen.
- **Strg + A:** Alle Keyframes auswählen.
- **Strg + Z:** Deine letzte Änderung rückgängig machen.
- **Strg + Y:** Die gerade rückgängig gemachte Änderung wiederherstellen.
- **Strg + Ziehen von Keyframes**: Mehrere ausgewählte Keyframes gleichzeitig ziehen.

# Zusätzliche Einstellungen und Tipps

- **Animation loopen:**  
  Du kannst den Animator so einstellen, dass er in einer Schleife läuft. Wenn Looping aktiviert ist, startet die Animation nach dem letzten Keyframe erneut – beachte jedoch, dass dies nur für das finale Zielelement gilt. In der Vorschau des Keyframe-Editors findet kein Looping statt.
  
- **Größe/Position ignorieren:**  
  Wenn du nicht möchtest, dass die Keyframes die Größe oder Position eines Elements ändern, deaktiviere diese Optionen.

- **Zeitversätze:**
  Du kannst einzelne Zielelemente zeitlich versetzen oder zufällige Zeitversätze innerhalb eines konfigurierten Bereichs verwenden, sodass dieselbe Animation für jedes Ziel zu unterschiedlichen Zeiten startet.
  
- **Offset-Modus:**  
  Im Offset-Modus werden Animationen als Änderungen relativ zur ursprünglichen Position des Elements angewendet. Die Vorschau wird zentriert auf einem Fadenkreuz angezeigt.
  
- **Rückgängig und Wiederholen:**  
  Verwende **Strg + Z**, um Änderungen rückgängig zu machen, und **Strg + Y**, um sie wiederherzustellen.
  
- **Reihenfolge prüfen:**  
  Stelle sicher, dass deine Keyframes zeitlich in der richtigen Reihenfolge sind. Das System sortiert sie für dich, aber wenn du einen verschiebst, überprüfe die Reihenfolge noch einmal.
  
- **Änderungen in der Vorschau ansehen:**  
  Verwende den Play-Button oder die **`P`-Taste**, um deine Animation vor dem Speichern in Aktion zu sehen.
