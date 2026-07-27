---
title: Audiodateien beheben
description: 'Probleme mit Audiodateien beheben, die FancyMenu nicht abspielen kann.'
---

# Audiodateien beheben

Wenn eine Audiodatei an anderer Stelle abgespielt wird, aber nicht in FancyMenu, kodiere sie erneut als OGG oder PCM-WAV. Bei WAV-Dateien versuche es mit 48 kHz, 16-Bit-Audio.

Du kannst FFmpeg oder einen anderen vertrauenswürdigen Audiokonverter verwenden. Eine erneute Kodierung ist auch dann sinnvoll, wenn die aktuelle Dateiendung und die gemeldeten Einstellungen bereits korrekt aussehen.

# Prüfungen

- Bestätige, dass die erneut kodierte Datei in einem anderen Audioplayer abgespielt wird.
- Halte sehr große Audiodateien von speicherempfindlichen Bildschirmen fern.
- Überprüfe den ausgewählten Soundkanal des [Audio-Elements](./elements#audio) oder der Aktion.
- Prüfe die Hauptlautstärke von Minecraft und die Lautstärke des ausgewählten Kanals.
- Wenn die Audioausgabe weiterhin fehlschlägt, teste ohne andere Mods, die Minecraft-Audio ersetzen oder verarbeiten.
