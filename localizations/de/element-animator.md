---
title: Element-Animator
description: Wie man Elemente mit Keyframes mithilfe des Element-Animators animiert.
---

# Element-Animator

Der **Animator** ist ein Element, mit dem du andere Elemente animieren kannst. Mit diesem Element kannst du die Größe, Position und den Ankerpunkt eines anderen Elements im Laufe der Zeit mithilfe von Keyframes sanft verändern. Keyframes sind wie Schnappschüsse, die festhalten, wie das Element zu einem bestimmten Zeitpunkt aussehen soll. Das Animator-Element spielt diese Schnappschüsse dann der Reihe nach ab, um eine flüssige Bewegung zu erzeugen.

> Der **Element-Animator** ermöglicht es dir, die **Position, Größe und den Ankerpunkt** von Elementen zu steuern. Es ist **NICHT** möglich, andere Einstellungen von Elementen zu steuern, wie z. B. Deckkraft, Sichtbarkeit, Drehung usw.!
{.is-warning}

# Video-Tutorial

Da viele von euch etwas verwirrt darüber waren, wie der Animator funktioniert, habe ich ein kleines Video erstellt, das zeigt, wie man damit arbeitet.

[FancyMenu | How to Use the Element Editor - YouTube](https://www.youtube.com/watch?v=F9S8cIPssww) (youtu.be/F9S8cIPssww)

<a href="https://www.youtube.com/watch?v=F9S8cIPssww" target="_blank" rel="noopener noreferrer">
  <img width="636" alt="Screenshot_2" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/element_animator_video_thumbnail.png" />
</a>

# Das Animator-Element hinzufügen

1. **Hintergrund rechtsklicken:**  
   Klicke im Layout-Editor mit der rechten Maustaste auf den Hintergrund.

2. **Neues Element -> Element-Animator auswählen:**  
   Wähle im erscheinenden Menü **Neues Element** und klicke auf **Element-Animator**. Dadurch wird der Animator deinem Layout hinzugefügt.

3. **Einrichten:**  
   Nach dem Hinzufügen erscheint das Animator-Element mit seinen Standardeinstellungen. Du kannst Optionen wie Schleifen oder die Farbe ändern, indem du den Animator rechtsklickst und eine Auswahl aus dem Menü triffst.

# Keyframes verwalten

Keyframes sind wie Lesezeichen, die dem Animator sagen, wie das Element zu einem bestimmten Zeitpunkt aussehen soll.

## Den Keyframe-Editor öffnen

- **Den Editor öffnen:**  
  Klicke mit der rechten Maustaste auf das Animator-Element und wähle **Keyframes bearbeiten** (oder **Keyframes verwalten**). Dadurch öffnet sich ein Bildschirm, auf dem du Keyframes hinzufügen, bearbeiten oder löschen kannst.

## Keyframes aufzeichnen und hinzufügen

- **Aufnahme starten:**  
  Drücke im Keyframe-Editor die **`R`-Taste**, um die Aufnahme zu starten. Während der Aufnahme ändert sich die Vorschaufläche ihre Farbe, um anzuzeigen, dass sie aktiv ist.
  
- **Vorschau ändern:**  
  Verschiebe oder skaliere die Vorschaufläche, um das gewünschte Aussehen festzulegen. Im Offset-Modus bleibt die Vorschau auf einem Fadenkreuz zentriert, sodass Änderungen als Offsets angezeigt werden.
  
- **Keyframe hinzufügen:**  
  Drücke die **`K`-Taste**, um das aktuelle Aussehen als Keyframe zu speichern. Dieser Keyframe speichert Position, Größe und Ankereinstellungen der Vorschau.

## Keyframes bearbeiten

- **Keyframe auswählen:**  
  Klicke auf einen Keyframe-Marker in der Zeitleiste. Du kannst auch **Strg** gedrückt halten und klicken, um mehrere auszuwählen.
  
- **Keyframe verschieben:**  
  Ziehe den Keyframe-Marker nach links oder rechts, um seinen Zeitpunkt zu ändern. Du kannst auch:
  - **Pfeil links:** um ihn 100 ms früher zu verschieben.
  - **Pfeil rechts:** um ihn 100 ms später zu verschieben.
  
- **Vorschau feinabstimmen:**  
  Wenn ein Keyframe ausgewählt ist, passe die Vorschaufläche an, indem du sie verschiebst oder skalierst. Verwende bei Bedarf **Strg + Z**, um Änderungen rückgängig zu machen, und **Strg + Y**, um sie zu wiederholen.

## Keyframes entfernen

- **Keyframe löschen:**  
  Wähle einen Keyframe aus und drücke die **Entf-Taste**, um ihn zu entfernen.
  
- **Mehrere Keyframes löschen:**  
  Du kannst mehrere Keyframes auswählen (zum Beispiel mit **Strg + A**, um alle auszuwählen) und dann Entf drücken, um sie alle zu löschen.

## Keyframe-Glättung

Die Keyframe-Glättung ist eine Funktion, mit der du deine Keyframes gleichmäßig verteilen kannst. Dadurch wirkt deine Animation gleichmäßiger und flüssiger.

- **Mehrere Keyframes auswählen:**  
  Wähle zuerst zwei oder mehr Keyframes aus, die du glätten möchtest (verwende **Strg + Klick** oder **Strg + A**).

- **Auf die Schaltfläche für Glättung klicken:**  
  Klicke in der unteren Symbolleiste des Keyframe-Editors auf die Schaltfläche **Abstands-Glättung**.

- **Neuen Abstand eingeben:**  
  Es erscheint ein kleines Eingabefeld. Gib einen Wert (in Millisekunden) ein, um den gleichen Zeitabstand zwischen jedem ausgewählten Keyframe festzulegen.

- **Glättung anwenden:**  
  Drücke die Eingabetaste, um die Glättung anzuwenden. Die Keyframes werden so angepasst, dass der zeitliche Abstand zwischen ihnen gleichmäßig ist.

# Deine Animation in der Vorschau ansehen

Nachdem du Keyframes aufgezeichnet hast, kannst du sehen, wie deine Animation aussehen wird:

- **Animation abspielen:**  
  Drücke im Keyframe-Editor die **`P`-Taste** oder klicke auf die Wiedergabetaste. Die Vorschau startet von Anfang an und zeigt, wie sich die Vorschaufläche im Laufe der Zeit verändert.
  
- **Hinweis zu Schleifen:**  
  Während der Vorschau im Keyframe-Editor wird die Animation **nicht** in einer Schleife abgespielt. Das bedeutet, sie läuft nur einmal von Anfang bis Ende. Die Schleife ist erst aktiv, wenn das Animator-Element in deinem finalen Layout auf ein Zielelement angewendet wird.
  
- **Vorschau pausieren:**  
  Drücke erneut die **`P`-Taste**, um die Animation zu pausieren, wenn du an einer bestimmten Stelle anhalten möchtest.
  
- **Fortschrittsleiste ziehen:**  
  Falls verfügbar, kannst du den Zeitleistenmarker ziehen, um zu prüfen, wie die Animation zu einem bestimmten Zeitpunkt aussieht.

# Zielelemente auswählen

Nachdem du deine Keyframes eingerichtet hast, musst du auswählen, welche Layout-Elemente animiert werden sollen:

1. **Ziel-Manager öffnen:**  
   Klicke mit der rechten Maustaste auf das Animator-Element und wähle **Ziele verwalten**.
  
2. **Ziele hinzufügen:**  
   Klicke auf **Ziel hinzufügen**, um eine Liste der verfügbaren Elemente anzuzeigen. Wähle die Elemente aus, die du animieren möchtest.
  
3. **Ziele entfernen:**  
   Um ein Ziel zu entfernen, öffne den Manager und klicke auf **Ziel entfernen**.

Wenn die Animation im finalen Layout abgespielt wird, verwendet der Animator deine Keyframes, um Größe, Position und mehr der ausgewählten Elemente zu ändern. Die Schleife wird hier angewendet, wenn du sie festgelegt hast.

# Tastenkombinationen

Verwende diese Tastenkombinationen im Keyframe-Editor, um schneller zu arbeiten:

- **`R`-Taste:** Aufnahme starten oder stoppen.
- **`T`-Taste:** Aufnahme pausieren oder fortsetzen.
- **`P`-Taste:** Animationsvorschau abspielen oder pausieren.
- **`K`-Taste:** Einen neuen Keyframe zur aktuellen Zeit hinzufügen.
- **Pfeiltasten links/rechts:**  
  - **Pfeil links:** Einen Keyframe 100 ms früher verschieben.
  - **Pfeil rechts:** Einen Keyframe 100 ms später verschieben.
- **Entf-Taste:** Die ausgewählten Keyframes entfernen.
- **Strg + A:** Alle Keyframes auswählen.
- **Strg + Z:** Die letzte Änderung rückgängig machen.
- **Strg + Y:** Die gerade rückgängig gemachte Änderung wiederholen.
- **Strg + Ziehen von Keyframes**: Mehrere ausgewählte Keyframes gleichzeitig ziehen.

# Zusätzliche Einstellungen und Tipps

- **Animation in Schleife abspielen:**  
  Du kannst den Animator so einstellen, dass er in einer Schleife läuft. Wenn die Schleife aktiviert ist, beginnt die Animation nach dem letzten Keyframe erneut von vorne – beachte jedoch, dass dies nur für das endgültige Zielelement gilt. In der Vorschau des Keyframe-Editors wird keine Schleife abgespielt.
  
- **Größe/Position ignorieren:**  
  Wenn du nicht möchtest, dass die Keyframes die Größe oder Position eines Elements ändern, schalte diese Optionen aus.

- **Zeitversätze:**
  FancyMenu 3.9.0 fügt Zeitversätze für gesteuerte Elemente hinzu. Du kannst einzelne Zielelemente mit einem Zeitversatz versehen oder zufällige Zeitversätze innerhalb eines konfigurierten Bereichs verwenden, sodass eine Animation für jedes Ziel zu leicht unterschiedlichen Zeiten startet.
  
- **Offset-Modus:**  
  Im Offset-Modus werden Animationen als Änderungen relativ zur ursprünglichen Position des Elements angewendet. Die Vorschau wird zentriert auf einem Fadenkreuz angezeigt.
  
- **Rückgängig und Wiederholen:**  
  Verwende **Strg + Z**, um Änderungen rückgängig zu machen, und **Strg + Y**, um sie wiederherzustellen.
  
- **Reihenfolge prüfen:**  
  Achte darauf, dass deine Keyframes zeitlich in der richtigen Reihenfolge sind. Das System sortiert sie automatisch für dich, aber wenn du einen verschiebst, überprüfe die Reihenfolge noch einmal.
  
- **Änderungen in der Vorschau ansehen:**  
  Verwende die Wiedergabetaste oder die **`P`-Taste**, um deine Animation vor dem Speichern in Aktion zu sehen.

# Fazit

Wenn du diese einfachen Schritte befolgst, kannst du ein Animator-Element zu deinem Layout hinzufügen und flüssige Animationen erstellen. Egal, ob du Live-Änderungen mit der Vorschau aufzeichnest, Keyframes mit deiner Tastatur anpasst, auswählst, welche Elemente animiert werden sollen, oder deine Animation in der Vorschau ansiehst, der Animator bietet dir eine einfache Möglichkeit, deine benutzerdefinierten Menüs zum Leben zu erwecken.

Viel Spaß beim Animieren!
