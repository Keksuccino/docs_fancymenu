---
title: Audiodateien reparieren
description: 'Behebe Probleme mit Audiodateien, die FancyMenu nicht abspielen kann.'
sourceBlobSha: ca4c2e0bf2c12f28f0f74b5b3011a949e1a99413
---

# Audiodateien reparieren

Wenn eine Audiodatei anderswo abgespielt wird, aber nicht in FancyMenu, kodiere sie erneut als OGG oder PCM-WAV. Versuche es bei WAV mit 48 kHz und 16 Bit.

Du kannst FFmpeg oder einen anderen vertrauenswürdigen Audiokonverter verwenden. Eine erneute Kodierung ist auch dann hilfreich, wenn die aktuelle Dateiendung und die angezeigten Einstellungen korrekt aussehen.

# Prüfungen

- Vergewissere dich, dass die neu kodierte Datei in einem anderen Audioplayer abgespielt wird.
- Verwende sehr große Audiodateien nicht auf Oberflächen, bei denen der Speicherverbrauch eine Rolle spielt.
- Überprüfe den Soundkanal, der vom [Audioelement](/elements#audio) oder der Aktion ausgewählt wurde.
- Überprüfe die Master-Lautstärke von Minecraft und die Lautstärke des ausgewählten Kanals.
- Wenn die Audiowiedergabe weiterhin fehlschlägt, teste es ohne andere Mods, die Minecraft-Audio ersetzen oder verarbeiten.
