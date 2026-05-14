---
title: APNGs
description: Wie man FancyMenu-kompatible APNG-Bilder erstellt.
---

# Animierte PNG-Bilder

> Für neue große oder komplexe Animationen solltest du [AFMA/FMA-Dateien](/fma) bevorzugen. FancyMenu 3.9.0 kann Watermedia V3 + Watermedia Binaries V3 für schnelleres APNG-/GIF-Decoding verwenden, wenn verfügbar, aber AFMA ist weiterhin das bevorzugte FancyMenu-Animationsformat.
{.is-info}


APNGs sind eine animierte Version von PNG-Bildern und machen es möglich, dieselben Funktionen wie bei einem GIF zu nutzen, aber in voller, verlustfreier PNG-Qualität!

FancyMenu hat integrierte APNG-Unterstützung, ist aber etwas wählerisch, welche APNGs unterstützt werden.
Es benötigt **unkomprimierte** APNGs, die **nicht interlaced** sind.

# APNG-Animationen erstellen

Es würde dich überraschen, wie schwierig es ist, einen guten APNG-Editor zu finden, besonders mit Optionen zum Deaktivieren von Komprimierung und Interlacing.

Eine gute Wahl für einen Editor ist [ScreenToGif](https://www.screentogif.com/). Das ist eigentlich ein Tool zum Aufzeichnen von GIFs und APNGs deines Bildschirms, aber es eignet sich auch hervorragend, um normale APNGs zu erstellen, indem du den Aufnahme-Teil überspringst und die Dateien direkt im Editor lädst!

## Den Editor öffnen

Das Erste, was du nach dem Öffnen von [ScreenToGif](https://www.screentogif.com/) siehst, ist dieser Bildschirm. Klicke hier auf **Editor**.

![screentogif_2](https://github.com/Keksuccino/FancyMenu/assets/35544624/a8d34313-b841-4fb6-bf3a-ff02c39792cb)

## Die Frames laden

Jetzt brauchst du deine PNG-Frames. Ziehe sie per Drag-and-Drop in den Editor.

![screentogif_dragndrop](https://github.com/Keksuccino/FancyMenu/assets/35544624/ba4ad4a5-484e-46f1-8efd-90ba764462d8)

## Frame-Verzögerung

Um die Verzögerung zwischen den Frames zu konfigurieren, wähle die Frame(s) aus, die du bearbeiten möchtest, wechsle zum Reiter **Edit** und klicke im Abschnitt **Delay (Duration)** auf **Override**.

![screentogif_delay](https://github.com/Keksuccino/FancyMenu/assets/35544624/a5d93139-3192-4090-b243-e5c0fe299963)

## Wiederholung

Das Wiederholungsverhalten kann im Menü **Save As** konfiguriert werden. Im nächsten Schritt erfährst du, wie du dieses Menü öffnest.

## Das APNG exportieren

Jetzt bist du bereit, wieder zum Reiter **File** zu wechseln und auf **Save As** zu klicken.

Stelle im Speichermenü sicher, dass du:
- den Dateityp auf **APNG** setzt (erste Einstellung, eventuell musst du zuerst zum Anfang des Menüs scrollen)
- **Detect Unchanged Pixels** deaktivierst

> Du kannst in diesem Menü auch das **Wiederholungsverhalten** konfigurieren! Wenn du **Looped Apng** deaktivierst, wird das APNG gar nicht wiederholt; wenn du es aktivierst, kannst du zwischen einer bestimmten Anzahl an Wiederholungen oder endloser Wiederholung wählen.
{.is-info}

![screentogif_save](https://github.com/Keksuccino/FancyMenu/assets/35544624/954353da-45ed-4df8-9f06-c78a0a469fc8)

## Das APNG in FancyMenu verwenden

Jetzt kannst du deine APNG-Datei nach `/config/fancymenu/assets/` kopieren. Danach kannst du sie für fast alles verwenden, was Bilder akzeptiert.

> Es ist **wirklich wichtig**, dass der APNG-Dateiname mit `.apng` endet!
> FancyMenu kann das Bild nicht als APNG erkennen, wenn es nicht auf `.apng` endet.
{.is-warning}

![screentogif_use_apng](https://github.com/Keksuccino/FancyMenu/assets/35544624/2322da62-4013-451e-9a8b-3df0bf92df54)
