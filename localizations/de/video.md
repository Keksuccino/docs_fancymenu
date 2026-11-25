---
title: Videos (MP4)
description: Was du über die Verwendung von Videos in FancyMenu wissen solltest.
sourceBlobSha: bd34c5c21a6c08d6b66a7b2acdaf9bd12739732f
---
# Videos

FancyMenu unterstützt die Wiedergabe von MP4-Videos als [Elemente](/elements#video), [Menühintergründe](/menu-backgrounds#video) und Inhalte für das [Game Intro](/game-intro).

Das native [**Video**-Element](/elements#video) und der **Video**-Menühintergrund verwenden Watermedia V3. Die alten Typen **Video [Rinku]** sind veraltet und sollten nur in Layouts verbleiben, die sie noch benötigen.

Außerdem gibt es die folgenden [Aktionen](/action-scripts), um Videohintergründe und -elemente zu steuern:

- [**Lautstärke des Video-Elements festlegen**](/action-scripts#set-video-element-volume) legt die Lautstärke eines Video-Elements fest.
- [**Wiedergabezeit des Video-Elements festlegen**](/action-scripts#set-video-element-play-time) springt in einem Video-Element zu einem Zeitstempel in Millisekunden.
- [**Pausezustand des Video-Elements umschalten**](/action-scripts#toggle-video-element-paused-state) schaltet den Pausezustand eines Video-Elements um.
- [**Lautstärke des Videohintergrunds festlegen**](/action-scripts#set-video-background-volume) legt die Lautstärke eines Video-Menühintergrunds fest.
- [**Wiedergabezeit des Videohintergrunds festlegen**](/action-scripts#set-video-background-play-time) springt in einem Video-Menühintergrund zu einem Zeitstempel in Millisekunden.
- [**Pausezustand des Videohintergrunds umschalten**](/action-scripts#toggle-video-background-paused-state) schaltet den Pausezustand eines Video-Menühintergrunds um.

Außerdem gibt es die folgenden [Platzhalter](/placeholders), um Informationen über Videohintergründe und -elemente abzurufen:

- [**Lautstärke des Video-Elements**](/placeholders#video-element-volume) gibt die Lautstärke eines Video-Elements zurück.
- [**Dauer des Video-Elements**](/placeholders#video-element-duration) gibt die Dauer eines Video-Elements zurück.
- [**Wiedergabezeit des Video-Elements**](/placeholders#video-element-play-time) gibt den aktuellen Fortschritt eines Video-Elements zurück.
- [**Pausezustand des Video-Elements**](/placeholders#video-element-paused-state) gibt zurück, ob ein Video-Element pausiert ist.
- [**Lautstärke des Videohintergrunds**](/placeholders#video-background-volume) gibt die Lautstärke eines Video-Menühintergrunds zurück.
- [**Dauer des Videohintergrunds**](/placeholders#video-background-duration) gibt die Dauer eines Video-Menühintergrunds zurück.
- [**Wiedergabezeit des Videohintergrunds**](/placeholders#video-background-play-time) gibt den aktuellen Fortschritt eines Video-Menühintergrunds zurück.
- [**Pausezustand des Videohintergrunds**](/placeholders#video-background-paused-state) gibt zurück, ob ein Video-Menühintergrund pausiert ist.

Die Platzhalter für Dauer und Wiedergabezeit geben standardmäßig `MM:SS` zurück. Setze `output_as_timestamp` auf `true`, wenn du Zeitstempel in Millisekunden benötigst. Für Platzhalter zur Wiedergabezeit kann weiterhin `show_percentage` verwendet werden, um Fortschrittswerte von 0 bis 100 auszugeben.

Lautstärke und Pausezustand sind Controller-Metadaten, die der jeweiligen Kennung zugeordnet sind. Werte für Dauer und Wiedergabezeit setzen voraus, dass das passende Video-Element oder der passende Videohintergrund auf dem aktuellen Bildschirm aktiv und bereit ist.

Mit dem [Listener **Videowiedergabestatus geändert**](/listeners#video-playback-status-changed) kannst du auf `PLAYING`, `PAUSED`, `STOPPED` und `FINISHED` reagieren.

## Anforderungen

Um den neuen nativen Video-Elementtyp und Menühintergrundtyp zu verwenden, musst du Folgendes installieren:

- **Watermedia V3**
- **Watermedia Binaries V3**

Dies sind optionale Abhängigkeiten. Wenn du Videounterstützung nutzen möchtest, musst du sie daher manuell zur Instanz hinzufügen.

Für die native Videowiedergabe ist außerdem ein OpenGL-Renderer erforderlich. Die Watermedia-Wiedergabe ist nicht verfügbar, während Minecraft Vulkan verwendet. Wechsle zu OpenGL, um Video-Elemente, Video-Menühintergründe und [Video-Game-Intros](/game-intro) zu verwenden.

Der veraltete Typ **Video [Rinku]** verwendet weiterhin [Rinku](https://modrinth.com/mod/rinku). Verwende für neue Layouts stattdessen den nativen, von Watermedia unterstützten Videotyp.

## Videos in Ladebildschirmen

Die Videounterstützung funktioniert NICHT in Ladebildschirmen (Ladebildschirm beim Laden des Spiels bzw. von Ressourcen und Ladebildschirm beim Laden einer Welt).

Das bedeutet auch, dass du über **Drippy Loading Screen** KEINE Videos zum Ladebildschirm des Spiels hinzufügen solltest, da dies in den meisten Fällen nicht funktioniert.

Verwende in Ladebildschirmen stattdessen kurze, einfache [Animationen](/animations) (APNG oder GIF).

## Fehlerbehebung

Wenn die native Videowiedergabe nicht funktioniert, überprüfe, ob Watermedia V3 und Watermedia Binaries V3 zu deiner Minecraft-/Modloader-Version passen und ob Minecraft OpenGL statt Vulkan verwendet.
