---
title: Videos (MP4)
description: Was man über die Verwendung von Videos in FancyMenu wissen sollte.
---

# Videos

FancyMenu unterstützt die Wiedergabe von MP4-Videos als Elemente, als Menü-Hintergründe und als Game-Intro-Inhalt.

FancyMenu 3.9.0 fügt ein neues natives **Video**-Element und einen **Video**-Menühintergrund hinzu, die von Watermedia V3 unterstützt werden. Der alte Typ **Video [MCEF]** für Elemente/Hintergründe ist veraltet und sollte nur noch für alte Layouts beibehalten werden, die ihn weiterhin benötigen.

Außerdem gibt es die folgenden **Aktionen**, um Video-Hintergründe und -Elemente zu steuern:

- **Set Video Element Volume** setzt die Lautstärke eines Video-Elements
- **Set Video Element Play Time** springt ein Video-Element zu einem Zeitstempel in Millisekunden
- **Toggle Video Element Paused State** schaltet den Pausiert-Zustand eines Video-Elements um
- **Set Video Background Volume** setzt die Lautstärke eines Video-Menühintergrunds
- **Set Video Background Play Time** springt ein Video-Menühintergrund zu einem Zeitstempel in Millisekunden
- **Toggle Video Background Paused State** schaltet den Pausiert-Zustand eines Video-Menühintergrunds um

Und die folgenden **Platzhalter**, um Informationen über Video-Hintergründe und -Elemente abzurufen:

- **Video Element Volume** ruft die Lautstärke eines Video-Elements ab
- **Video Element Duration** ruft die Dauer eines Video-Elements ab
- **Video Element Play Time** ruft die aktuelle Wiedergabezeit (Fortschritt) eines Video-Elements ab
- **Video Element Paused State** ruft den Pausiert-Zustand (true/false) eines Video-Elements ab
- **Video Background Volume** ruft die Lautstärke eines Video-Menühintergrunds ab
- **Video Background Duration** ruft die Dauer eines Video-Menühintergrunds ab
- **Video Background Play Time** ruft die aktuelle Wiedergabezeit (Fortschritt) eines Video-Menühintergrunds ab
- **Video Background Paused State** ruft den Pausiert-Zustand (true/false) eines Video-Menühintergrunds ab

Die Platzhalter für Dauer und Wiedergabezeit geben standardmäßig `MM:SS` zurück. Setze `output_as_timestamp` auf `true`, wenn du Millisekunden-Zeitstempel benötigst. Platzhalter für die Wiedergabezeit können weiterhin `show_percentage` für Fortschrittswerte von 0–100 verwenden.

FancyMenu 3.9.0 fügt außerdem den Listener **On Video Playback Status Changed** hinzu, der auf `PLAYING`, `PAUSED`, `STOPPED` und `FINISHED` reagieren kann.

## Anforderungen

Um den neuen nativen Video-Element- und Menühintergrund-Typ zu verwenden, musst du Folgendes installieren:

- **Watermedia V3**
- **Watermedia Binaries V3**

Dies sind optionale Abhängigkeiten und müssen der Instanz manuell hinzugefügt werden, wenn du Videounterstützung möchtest.

Der veraltete Typ **Video [MCEF]** verwendet weiterhin MCEF. Für neue Layouts solltest du stattdessen den nativen, von Watermedia unterstützten Video-Typ verwenden.

## Videos in Ladebildschirmen

Videounterstützung funktioniert in Ladebildschirmen NICHT (Ladebildschirm für Spiel-/Ressourcenladen & Welt-Ladebildschirm).

Das bedeutet auch, dass du keine Videos über **Drippy Loading Screen** auf dem Spiel-Ladebildschirm hinzufügen solltest, da dies in den meisten Fällen nicht funktionieren wird.

Stattdessen solltest du in Ladebildschirmen kurze, einfache AFMA/FMA-Dateien verwenden, da Benutzer das erneute Laden in den meisten Fällen nicht bemerken, wenn die Animation einfach und kurz genug ist.

## Fehlerbehebung

Wenn du Probleme mit der nativen Videounterstützung hast, stelle zuerst sicher, dass sowohl Watermedia V3 als auch Watermedia Binaries V3 installiert sind und zu deiner Minecraft-/Modloader-Version passen.
