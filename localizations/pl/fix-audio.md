---
title: Naprawianie plików audio
description: 'Rozwiązywanie problemów z plikami audio, których FancyMenu nie może odtworzyć.'
sourceBlobSha: ca4c2e0bf2c12f28f0f74b5b3011a949e1a99413
---

# Naprawianie plików audio

Jeśli plik audio odtwarza się w innych programach, ale nie w FancyMenu, przekoduj go do formatu OGG lub PCM WAV. W przypadku WAV spróbuj użyć częstotliwości 48 kHz i głębi 16 bitów.

Możesz użyć FFmpeg lub innego zaufanego konwertera audio. Przekodowanie może pomóc nawet wtedy, gdy obecne rozszerzenie pliku i wyświetlane ustawienia wyglądają prawidłowo.

# Sprawdzanie

- Upewnij się, że przekodowany plik odtwarza się w innym odtwarzaczu audio.
- Nie używaj bardzo dużych plików audio na ekranach, na których zużycie pamięci ma znaczenie.
- Sprawdź kanał dźwiękowy wybrany w [elemencie audio](/elements#audio) lub akcji.
- Sprawdź głośność główną Minecrafta oraz głośność wybranego kanału.
- Jeśli dźwięk nadal nie działa, sprawdź, czy problem występuje również po wyłączeniu innych modów, które zastępują dźwięk Minecrafta lub go przetwarzają.
