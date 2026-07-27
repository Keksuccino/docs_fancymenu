---
title: APNGs
description: Wie man mit FancyMenu kompatible APNG-Bilder erstellt.
---

# Animierte PNG-Bilder

> [!NOTE]
> Für große oder komplexe Animationen sind [AFMA-Dateien](./fma) die bessere Wahl. Watermedia V3 und Watermedia Binaries V3 können die APNG/GIF-Dekodierung beschleunigen, wenn sie verfügbar sind, aber AFMA bleibt das bevorzugte Animationsformat von FancyMenu.


APNGs sind eine animierte Version von PNG-Bildern und ermöglichen damit dieselben Funktionen wie ein GIF, aber in voller, verlustfreier PNG-Qualität!

FancyMenu unterstützt APNGs nativ, ist dabei aber etwas wählerisch, welche APNGs unterstützt werden.
Es benötigt **unkomprimierte** APNGs, die **nicht interlaced** sind.

# APNG-Animationen erstellen

Es würde dich überraschen, wie schwierig es ist, einen guten APNG-Editor zu finden, besonders mit Optionen zum Deaktivieren von Komprimierung und Interlacing.

Eine sehr gute Wahl für einen Editor ist [ScreenToGif](https://www.screentogif.com/). Das ist eigentlich ein Tool, um GIFs und APNGs von deinem Bildschirm aufzunehmen, aber es eignet sich auch hervorragend zum Erstellen normaler APNGs, indem du den Aufnahme-Teil überspringst und die Dateien direkt im Editor lädst!

## Den Editor öffnen

Das Erste, was du nach dem Öffnen von [ScreenToGif](https://www.screentogif.com/) siehst, ist dieser Bildschirm. Klicke hier auf **Editor**.

![screentogif_2](https://github.com/Keksuccino/FancyMenu/assets/35544624/a8d34313-b841-4fb6-bf3a-ff02c39792cb)

## Die Frames laden

Jetzt brauchst du deine PNG-Frames. Ziehe sie per Drag & Drop in den Editor.

![screentogif_dragndrop](https://github.com/Keksuccino/FancyMenu/assets/35544624/ba4ad4a5-484e-46f1-8efd-90ba764462d8)

## Frame-Verzögerung

Um die Verzögerung zwischen den Frames zu konfigurieren, wähle den/die Frame(s) aus, die du bearbeiten möchtest, wechsle zum Tab **Edit** und klicke im Bereich **Delay (Duration)** auf **Override**.

![screentogif_delay](https://github.com/Keksuccino/FancyMenu/assets/35544624/a5d93139-3192-4090-b243-e5c0fe299963)

## Wiederholung

Das Wiederholungsverhalten kann im Menü **Save As** konfiguriert werden. Schau dir den nächsten Schritt an, um zu erfahren, wie du dieses Menü öffnest.

## Das APNG exportieren

Jetzt bist du bereit, wieder zum Tab **File** zu wechseln und auf **Save As** zu klicken.

Stelle im Speichermenü sicher, dass du:
- den Dateityp auf **APNG** setzt (erste Einstellung, du musst eventuell zuerst ganz nach oben im Menü scrollen)
- **Detect Unchanged Pixels** deaktivierst

> [!NOTE]
> Du kannst in diesem Menü auch das **Wiederholungsverhalten** konfigurieren! Wenn du **Looped Apng** deaktivierst, wird das APNG überhaupt nicht wiederholt; wenn du es aktivierst, kannst du zwischen einer bestimmten Anzahl von Wiederholungen oder unendlicher Wiederholung wählen.

![screentogif_save](https://github.com/Keksuccino/FancyMenu/assets/35544624/954353da-45ed-4df8-9f06-c78a0a469fc8)

## Das APNG in FancyMenu verwenden

Kopiere nun deine APNG-Datei nach `<game-directory>/config/fancymenu/assets/`. Danach kannst du sie für fast alles verwenden, was Bilder akzeptiert.

> [!WARNING]
> Es ist **sehr wichtig**, dass der Dateiname der APNG mit `.apng` endet!
> FancyMenu kann das Bild nicht als APNG erkennen, wenn es nicht auf `.apng` endet.

![screentogif_use_apng](https://github.com/Keksuccino/FancyMenu/assets/35544624/2322da62-4013-451e-9a8b-3df0bf92df54)
