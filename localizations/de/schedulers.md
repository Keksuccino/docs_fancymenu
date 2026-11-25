---
title: Zeitplaner
description: >-
  Führe Aktionsskripte zeitgesteuert einmal oder wiederholt in jedem Menü und
  während des Spielens aus.
sourceBlobSha: 5abcc8450371fa0d23d67618db9cf27c9bd7de97
---

# Zeitplaner

Zeitplaner führen ein [Aktionsskript](/action-scripts) zeitgesteuert aus: einmal nach einer Wartezeit, einige Male oder wiederholt, bis sie angehalten werden. Sie funktionieren in jedem Menü und während des Spielens, auch wenn kein Menü geöffnet ist, und sind keinem Layout zugeordnet.

Zeitplaner sind die empfohlene Lösung für alles, was später oder wiederholt passieren soll. Verwende sie nach Möglichkeit statt [Ticker-Elementen](/elements#ticker).

<img width="800" alt="Ein Feld mit einem Überlebenstipp zeigt alle 4 Sekunden einen anderen Tipp an, weil ein Zeitplaner die Liste der Tipps mischt" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/schedulers_tips.gif?raw=true">

> [!CAUTION]
> Ein Zeitplaner kann Datei-, Netzwerk-, Befehls-, Zwischenablage-, Ressourcenpaket- und Linkaktionen ausführen, während kein Menü geöffnet ist. Verwende Zeitplaner nur aus Profilen und Dateien von Personen, denen du vertraust.

# Zeitplaner hinzufügen

<img width="800" alt="„Zeitplaner verwalten“ öffnen, auf „Zeitplaner hinzufügen“ klicken und ihm die Aktion „Liste anordnen“ mit „Mischen“ für die Liste tips zuweisen" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/schedulers_add.gif?raw=true">

1. Öffne **Menüleiste -> Anpassung -> Zeitplaner verwalten**.
2. Klicke auf **Zeitplaner hinzufügen**. Der Aktionsskript-Editor wird geöffnet.
3. Füge die Aktionen hinzu, die jedes Mal ausgeführt werden sollen, und klicke auf **Fertig**. Siehe [Aktionsskripte](/action-scripts#making-an-action-script).

<img width="800" alt="Den neuen Zeitplaner im Bereich „Einstellungen bearbeiten“ random_tip nennen, eine Tick-Verzögerung von 4000 und „Beim Start starten“ festlegen, ihn starten und sehen, wie sich der Tipp im Menü ändert" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/schedulers_start.gif?raw=true">

4. Der neue Zeitplaner wird mit einer zufälligen ID angezeigt. Klicke darauf und anschließend auf **Einstellungen bearbeiten**.
5. Vergib eine **Zeitplaner-ID**, zum Beispiel `random_tip`, richte den [Timer](#settings) ein und klicke auf **Fertig**.
6. Klicke auf **Jetzt starten**, um ihn auszuprobieren.

Alle Änderungen, die du unter **Zeitplaner verwalten** vornimmst, werden sofort gespeichert.

Der Zeitplaner in den GIFs führt alle 4 Sekunden [**Liste anordnen (FM-Variable)**](/action-scripts#arrange-list-fm-variable) mit **Mischen** für die Liste `tips` aus. Ein Textelement zeigt den ersten Eintrag der Liste an, sodass ein zufälliger Tipp erscheint. So funktionieren die Liste und der Text: [Listenaktionen](/variables#list-actions).

# Einstellungen

| Einstellung | Funktion |
|---|---|
| **Zeitplaner-ID** | Der Name, den Aktionen und Voraussetzungen verwenden. Zulässig sind nur Kleinbuchstaben, Zahlen, `.`, `_` und `-`. |
| **Startverzögerung (ms)** | Wie lange nach dem Start gewartet wird, bevor der Zeitplaner zum ersten Mal ausgeführt wird. Bei `0` läuft er sofort. |
| **Tick-Verzögerung (ms)** | Die Zeit zwischen zwei Ausführungen. Bei `0` läuft er bei jedem Tick, also 20-mal pro Sekunde. |
| **Auszuführende Ticks** | Wie oft er ausgeführt wird, bevor er von selbst stoppt. Bei `0` läuft er weiter, bis er angehalten wird. |
| **Beim Start starten** | Startet ihn bei jedem Spielstart. |

Zeitangaben erfolgen in Millisekunden: `1000` entspricht einer Sekunde, `60000` einer Minute und `1800000` einer halben Stunde.

# Starten und Anhalten

Ein Zeitplaner wird erst ausgeführt, nachdem er gestartet wurde:

- Mit **Beim Start starten**, wenn das Spiel gestartet wird und nach dem Wechseln von [Profilen](/profiles).
- Mit **Jetzt starten** unter **Zeitplaner verwalten**. Während der Zeitplaner läuft, lautet die Schaltfläche **Jetzt anhalten**.
- Mit der Aktion [**Zeitplaner starten**](/action-scripts#start-scheduler) und der ID des Zeitplaners, zum Beispiel in einem Skript für eine Schaltfläche oder einen [Listener](/listeners).

Er wird angehalten:

- Automatisch, nachdem er so oft ausgeführt wurde, wie unter **Auszuführende Ticks** festgelegt.
- Mit **Jetzt anhalten** oder der Aktion [**Zeitplaner anhalten**](/action-scripts#stop-scheduler) und seiner ID.
- Wenn er umbenannt oder entfernt wird, wenn du [Profile](/profiles) wechselst und wenn das Spiel geschlossen wird. Nach einem Neustart werden nur Zeitplaner mit **Beim Start starten** erneut ausgeführt.

Ein laufender Zeitplaner kann nicht ein zweites Mal gestartet werden: **Zeitplaner starten** bewirkt nichts, bis er angehalten wurde. Um ihn erneut zu starten, verwende **Zeitplaner anhalten** und danach **Zeitplaner starten**.

Mit der Voraussetzung [**Zeitplaner läuft**](/conditions#scheduler-is-running) kannst du überprüfen, ob ein Zeitplaner läuft, zum Beispiel um eine Stoppschaltfläche nur dann anzuzeigen.

## Nur bei geöffnetem Bildschirm

So führst du einen Zeitplaner nur aus, während ein bestimmter Bildschirm geöffnet ist, zum Beispiel der Titelbildschirm:

1. Öffne im Layout-Editor ein Layout des Bildschirms.
2. Klicke mit der rechten Maustaste auf den Editorhintergrund, wähle **„Bildschirm öffnen“-Aktionsskript bearbeiten** und füge **Zeitplaner starten** mit der ID des Zeitplaners hinzu.
3. Klicke erneut mit der rechten Maustaste auf den Hintergrund, wähle **„Bildschirm schließen“-Aktionsskript bearbeiten** und füge **Zeitplaner anhalten** mit derselben ID hinzu.

# Zeitplaner verwalten

<img width="800" alt="Das Fenster „Zeitplaner verwalten“ mit drei Zeitplanern, dem ausgewählten random_tip und seinen Einstellungen sowie dem Status „Wird ausgeführt“ auf der rechten Seite" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/schedulers_manage.png?raw=true">

- Klicke auf einen Zeitplaner, um rechts seine Einstellungen, seinen Status und sein Aktionsskript anzuzeigen.
- **Aktionen bearbeiten** oder ein Rechtsklick auf einen Zeitplaner öffnet sein Aktionsskript.
- Doppelklicke auf die ID eines Zeitplaners, um ihn umzubenennen. Mit `Enter` speicherst du den Namen, mit `Esc` brichst du ab. Beim Umbenennen wird der Zeitplaner angehalten, und Aktionen mit der alten ID finden ihn nicht mehr.
- **Zeitplaner entfernen** löscht den ausgewählten Zeitplaner, nachdem du dazu aufgefordert wurdest.
- **Für KI exportieren** kopiert den ausgewählten Zeitplaner oder alle Zeitplaner für einen [KI-Chat](/export-for-ai).
- Über die Suchleiste kannst du Zeitplaner anhand ihrer ID finden.

Zeitplaner werden in `config/fancymenu/scheduler_instances.txt` gespeichert (siehe [Speicherorte der Daten](/data-storage-locations)). Jedes [Profil](/profiles) hat seine eigenen Zeitplaner.

# Beispiel: Erinnerung an eine Pause

Alle 30 Minuten nach dem Spielstart eine Toast-Benachrichtigung anzeigen:

1. Füge einen Zeitplaner mit [**Toast anzeigen**](/action-scripts#show-toast) hinzu. Setze **Titel** auf `Zeit für eine Pause` und **Nachricht** auf `Steh auf, streck dich und trink etwas Wasser.`
2. Lege unter **Einstellungen bearbeiten** die **Zeitplaner-ID** auf `break_reminder`, die **Startverzögerung (ms)** und **Tick-Verzögerung (ms)** auf `1800000` sowie **Beim Start starten** auf **Aktiviert** fest.

Ohne **Startverzögerung (ms)** würde die erste Toast-Benachrichtigung direkt beim Spielstart angezeigt.

# Gut zu wissen

- Halte die **Tick-Verzögerung (ms)** so hoch, wie es die Aufgabe zulässt. Bei `0` werden die Aktionen 20-mal pro Sekunde ausgeführt, und langsame Aktionen können das Spiel verlangsamen.
- Wenn das Spiel ruckelt, können mehrere Ausführungen direkt nacheinander stattfinden.
- Änderungen am Aktionsskript werden sofort übernommen, auch während der Zeitplaner läuft. Änderungen an den Einstellungen werden beim nächsten Start wirksam.
- Schlägt eine Aktion fehl, läuft der Zeitplaner weiter. Der Fehler wird im Spielprotokoll unter `logs/latest.log` ausgegeben.
- Für eine einzelne Wartezeit innerhalb eines Aktionsskripts, etwa „Bildschirm 2 Sekunden nach dem Klick öffnen“, ist der Block [Später ausführen](/action-scripts#execute-later) einfacher.
