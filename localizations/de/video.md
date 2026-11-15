---
title: Videos (MP4)
description: Was du über die Verwendung von Videos in FancyMenu wissen solltest.
sourceBlobSha: 2ec0bfe39528bb93095798f6a2a1cc7cbe17e5eb
---
# Videos

FancyMenu unterstützt die Wiedergabe von MP4-Videos als [Elemente](./elements#video), [Menühintergründe](./menu-backgrounds) und Inhalte für den [Spieleinstieg](./game-intro).

Das native [**Video**-Element](./elements#video) und der **Video**-Menühintergrund verwenden Watermedia V3. Die alten Typen **Video [Rinku]** sind veraltet und sollten nur in Layouts verbleiben, die sie noch benötigen.

Außerdem gibt es die folgenden **Aktionen**, um Videohintergründe und -elemente zu steuern:

- [**Lautstärke des Video-Elements festlegen**](./action-scripts#set-video-element-volume-set_video_element_volume) legt die Lautstärke eines Video-Elements fest.
- [**Wiedergabezeit des Video-Elements festlegen**](./action-scripts#set-video-element-play-time-set_video_element_play_time) springt in einem Video-Element zu einem Zeitstempel in Millisekunden.
- [**Pausenzustand des Video-Elements umschalten**](./action-scripts#toggle-video-element-paused-state-toggle_video_element_pause_state) schaltet den Pausenzustand eines Video-Elements um.
- [**Lautstärke des Videohintergrunds festlegen**](./action-scripts#set-video-background-volume-set_video_menu_background_volume) legt die Lautstärke eines Video-Menühintergrunds fest.
- [**Wiedergabezeit des Videohintergrunds festlegen**](./action-scripts#set-video-background-play-time-set_video_menu_background_play_time) springt in einem Video-Menühintergrund zu einem Zeitstempel in Millisekunden.
- [**Pausenzustand des Videohintergrunds umschalten**](./action-scripts#toggle-video-background-paused-state-toggle_video_menu_background_pause_state) schaltet den Pausenzustand eines Video-Menühintergrunds um.

Außerdem gibt es die folgenden **Platzhalter**, um Informationen über Videohintergründe und -elemente abzurufen:

- [**Lautstärke des Video-Elements**](./placeholders#video-element-volume-video_element_vol) gibt die Lautstärke eines Video-Elements zurück.
- [**Dauer des Video-Elements**](./placeholders#video-element-duration-video_element_duration) gibt die Dauer eines Video-Elements zurück.
- [**Wiedergabezeit des Video-Elements**](./placeholders#video-element-play-time-video_element_playtime) gibt den aktuellen Fortschritt eines Video-Elements zurück.
- [**Pausenzustand des Video-Elements**](./placeholders#video-element-paused-state-video_element_paused_state) gibt zurück, ob ein Video-Element pausiert ist.
- [**Lautstärke des Videohintergrunds**](./placeholders#video-background-volume-video_background_vol) gibt die Lautstärke eines Video-Menühintergrunds zurück.
- [**Dauer des Videohintergrunds**](./placeholders#video-background-duration-video_background_duration) gibt die Dauer eines Video-Menühintergrunds zurück.
- [**Wiedergabezeit des Videohintergrunds**](./placeholders#video-background-play-time-video_background_playtime) gibt den aktuellen Fortschritt eines Video-Menühintergrunds zurück.
- [**Pausenzustand des Videohintergrunds**](./placeholders#video-background-paused-state-video_background_paused_state) gibt zurück, ob ein Video-Menühintergrund pausiert ist.

Die Platzhalter für Dauer und Wiedergabezeit geben standardmäßig `MM:SS` zurück. Setze `output_as_timestamp` auf `true`, wenn du Zeitstempel in Millisekunden benötigst. Für Platzhalter zur Wiedergabezeit kann weiterhin `show_percentage` verwendet werden, um Fortschrittswerte von 0 bis 100 zu erhalten.

Werte für Lautstärke und Pausenzustand sind Controller-Metadaten, die mit der Kennung verknüpft sind. Werte für Dauer und Wiedergabezeit erfordern, dass das passende Video-Element oder der passende Hintergrund auf dem aktuellen Bildschirm aktiv und bereit ist.

Der [Listener **Bei Änderung des Videowiedergabestatus**](./listeners#on-video-playback-status-changed-video_playback_status_changed) kann auf `PLAYING`, `PAUSED`, `STOPPED` und `FINISHED` reagieren.

## Voraussetzungen

Um den neuen nativen Video-Element- und Menühintergrundtyp zu verwenden, musst du Folgendes installieren:

- **Watermedia V3**
- **Watermedia Binaries V3**

Diese Abhängigkeiten sind optional und müssen daher manuell zur Instanz hinzugefügt werden, wenn du Videounterstützung verwenden möchtest.

Die native Videowiedergabe erfordert außerdem einen OpenGL-Renderer. Die Watermedia-Wiedergabe ist nicht verfügbar, während Minecraft Vulkan verwendet. Wechsle zu OpenGL, um Video-Elemente, Video-Menühintergründe und [Video-Spieleinstiege](./game-intro) zu verwenden.

Der veraltete Typ **Video [Rinku]** verwendet weiterhin [Rinku](https://modrinth.com/mod/rinku). Verwende für neue Layouts stattdessen den nativen, von Watermedia unterstützten Videotyp.

## Videos in Ladebildschirmen

Videounterstützung funktioniert NICHT in Ladebildschirmen (Ladebildschirm beim Laden des Spiels/der Ressourcen und Ladebildschirm beim Laden der Welt).

Das bedeutet auch, dass du über **Drippy Loading Screen** KEINE Videos zum Ladebildschirm des Spiels hinzufügen solltest, da dies in den meisten Fällen nicht funktioniert.

Verwende stattdessen kurze, einfache [AFMA-/FMA-Animationen](./fma) in Ladebildschirmen.

## Fehlerbehebung

Wenn ein natives Video nicht abgespielt wird, überprüfe, ob Watermedia V3 und Watermedia Binaries V3 zu deiner Minecraft-/Modloader-Version passen und ob Minecraft OpenGL anstelle von Vulkan verwendet.
