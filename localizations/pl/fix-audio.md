---
title: Naprawianie plików audio
description: 'Rozwiązywanie problemów z plikami audio, których FancyMenu nie może odtworzyć.'
---

# Naprawianie plików audio

Jeśli plik audio odtwarza się gdzie indziej, ale nie w FancyMenu, zakoduj go ponownie do formatu OGG lub PCM WAV. W przypadku WAV spróbuj dźwięku 48 kHz, 16-bitowego.

Możesz użyć FFmpeg lub innego zaufanego konwertera audio. Ponowne kodowanie jest przydatne nawet wtedy, gdy bieżące rozszerzenie pliku i zgłaszane ustawienia wydają się już poprawne.

# Kontrole

- Potwierdź, że ponownie zakodowany plik odtwarza się w innym odtwarzaczu audio.
- Nie używaj bardzo dużych plików audio na ekranach wrażliwych na zużycie pamięci.
- Sprawdź kanał dźwięku wybrany przez [element Audio](./elements#audio) lub akcję.
- Sprawdź głośność Master w Minecrafcie oraz głośność wybranego kanału.
- Jeśli dźwięk nadal się nie odtwarza, przetestuj bez innych modów, które zastępują lub przetwarzają dźwięk w Minecrafcie.
