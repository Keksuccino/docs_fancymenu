---
title: Videos (MP4)
description: Was du über die Verwendung von Videos in FancyMenu wissen solltest.
---
# Videos

FancyMenu unterstützt das Abspielen von MP4-Videos als [Elemente](./elements#video), [Menühintergründe](./menu-backgrounds) und [Game Intro](./game-intro)-Inhalte.

Das native [**Video**-Element](./elements#video) und der **Video**-Menühintergrund verwenden Watermedia V3. Die alten **Video [MCEF]**-Typen sind veraltet und sollten nur noch in Layouts verbleiben, die sie weiterhin benötigen.

Außerdem gibt es die folgenden **Aktionen**, um Videohintergründe und -elemente zu steuern:

- [**Video-Element-Lautstärke setzen**](./action-scripts#set-video-element-volume-set_video_element_volume) setzt die Lautstärke eines Video-Elements.
- [**Video-Element-Wiedergabezeit setzen**](./action-scripts#set-video-element-play-time-set_video_element_play_time) springt ein Video-Element zu einem Zeitstempel in Millisekunden.
- [**Pausierten Zustand des Video-Elements umschalten**](./action-scripts#toggle-video-element-paused-state-toggle_video_element_pause_state) schaltet den pausierten Zustand eines Video-Elements um.
- [**Lautstärke des Video-Hintergrunds setzen**](./action-scripts#set-video-background-volume-set_video_menu_background_volume) setzt die Lautstärke eines Video-Menühintergrunds.
- [**Wiedergabezeit des Video-Hintergrunds setzen**](./action-scripts#set-video-background-play-time-set_video_menu_background_play_time) springt einen Video-Menühintergrund zu einem Zeitstempel in Millisekunden.
- [**Pausierten Zustand des Video-Hintergrunds umschalten**](./action-scripts#toggle-video-background-paused-state-toggle_video_menu_background_pause_state) schaltet den pausierten Zustand eines Video-Menühintergrunds um.

Und die folgenden **Platzhalter**, um Informationen über Videohintergründe und -elemente abzurufen:

- [**Lautstärke des Video-Elements**](./placeholders#video-element-volume-video_element_vol) gibt die Lautstärke eines Video-Elements zurück.
- [**Dauer des Video-Elements**](./placeholders#video-element-duration-video_element_duration) gibt die Dauer eines Video-Elements zurück.
- [**Wiedergabezeit des Video-Elements**](./placeholders#video-element-play-time-video_element_playtime) gibt den aktuellen Fortschritt eines Video-Elements zurück.
- [**Pausierter Zustand des Video-Elements**](./placeholders#video-element-paused-state-video_element_paused_state) gibt zurück, ob ein Video-Element pausiert ist.
- [**Lautstärke des Video-Hintergrunds**](./placeholders#video-background-volume-video_background_vol) gibt die Lautstärke eines Video-Menühintergrunds zurück.
- [**Dauer des Video-Hintergrunds**](./placeholders#video-background-duration-video_background_duration) gibt die Dauer eines Video-Menühintergrunds zurück.
- [**Wiedergabezeit des Video-Hintergrunds**](./placeholders#video-background-play-time-video_background_playtime) gibt den aktuellen Fortschritt eines Video-Menühintergrunds zurück.
- [**Pausierter Zustand des Video-Hintergrunds**](./placeholders#video-background-paused-state-video_background_paused_state) gibt zurück, ob ein Video-Menühintergrund pausiert ist.

Die Platzhalter für Dauer und Wiedergabezeit geben standardmäßig `MM:SS` zurück. Setze `output_as_timestamp` auf `true`, wenn du Zeitstempel in Millisekunden benötigst. Platzhalter für die Wiedergabezeit können weiterhin `show_percentage` für Fortschrittswerte von 0–100 verwenden.

Lautstärke- und Pausiert-Status-Werte sind Controller-Metadaten, die mit dem Identifier verknüpft sind. Werte für Dauer und Wiedergabezeit erfordern, dass das passende Video-Element oder der passende Hintergrund auf dem aktuellen Bildschirm aktiv und bereit ist.

Der [**On Video Playback Status Changed**-Listener](./listeners#on-video-playback-status-changed-video_playback_status_changed) kann auf `PLAYING`, `PAUSED`, `STOPPED` und `FINISHED` reagieren.

## Voraussetzungen

Um den neuen nativen Video-Element- und Menühintergrund-Typ zu verwenden, musst du Folgendes installieren:

- **Watermedia V3**
- **Watermedia Binaries V3**

Diese sind optionale Abhängigkeiten und müssen der Instanz manuell hinzugefügt werden, wenn du Video-Unterstützung möchtest.

Die native Videowiedergabe erfordert außerdem einen OpenGL-Renderer. Watermedia-Wiedergabe ist nicht verfügbar, solange Minecraft Vulkan verwendet; wechsle zu OpenGL, um Video-Elemente, Video-Menühintergründe und [video Game Intros](./game-intro) zu verwenden.

Der veraltete Typ **Video [MCEF]** verwendet weiterhin MCEF. Für neue Layouts solltest du stattdessen den nativen, auf Watermedia basierenden Video-Typ verwenden.

## Videos in Ladebildschirmen

Video-Unterstützung funktioniert in Ladebildschirmen NICHT (Spiel-/Ressourcen-Ladebildschirm und Welten-Ladebildschirm).

Das bedeutet auch, dass du Videos NICHT über **Drippy Loading Screen** zum Spiel-Ladebildschirm hinzufügen solltest, da es in den meisten Fällen nicht funktionieren wird.

Verwende stattdessen kurze, einfache [AFMA/FMA-Animationen](./fma) in Ladebildschirmen.

## Fehlerbehebung

Wenn native Videos nicht abgespielt werden, überprüfe, ob Watermedia V3 und Watermedia Binaries V3 zu deiner Minecraft-/Modloader-Version passen und ob Minecraft OpenGL statt Vulkan verwendet.
