---
title: Naprawa plików audio
description: 'Jak naprawić pliki audio na wypadek, gdy FancyMenu nie potrafi ich odtworzyć.'
---

# Naprawianie plików audio

Minecraft jest dość wybredny, jeśli chodzi o pliki audio, które odtwarza.
Czasami zdarza się, że pliki audio działają bez problemu w innych odtwarzaczach, ale FancyMenu nie potrafi ich odtworzyć.
Jeśli tak jest, możesz spróbować naprawić plik audio, aby działał w Minecrafcie.

# Pliki OGG

W większości przypadków naprawa plików OGG jest bardzo prosta.

90% problemów z plikami audio rozwiązuje samo ponowne przekonwertowanie pliku.

1. Wejdź na https://convertio.co/ogg-mp3/ i przekonwertuj plik OGG do MP3.
2. Wejdź na https://convertio.co/mp3-ogg/ i przekonwertuj plik MP3 uzyskany w poprzednim kroku z powrotem do OGG.

Plik powinien teraz działać poprawnie.
Jeśli nadal nie działa, upewnij się, że nie jest to bardzo duży plik audio, i sprawdź, czy odtwarza się w innych odtwarzaczach audio.

# Pliki WAV

W przypadku plików WAV najczęściej problemem jest nieobsługiwana częstotliwość próbkowania i podobne ustawienia, przez które dźwięk nie działa poprawnie w Minecrafcie.

Upewnij się, że Twój plik audio:

- Ma częstotliwość próbkowania 48 KHz
- Ma głębię bitową 16 bitów
- Jest poprawnym plikiem WAV, który działa poza MC

Możesz łatwo przekonwertować ponownie swój plik audio do odpowiedniej głębi bitowej i częstotliwości próbkowania, korzystając z tej strony:
https://audio.online-convert.com/convert-to-wav

**WAŻNE:**
Nawet jeśli uważasz, że Twój plik audio ma już prawidłowy format, głębię bitową i częstotliwość próbkowania, i tak przekonwertuj go ponownie, korzystając ze strony podanej powyżej.

# Inne przyczyny

Czasami problemem nie jest sam plik, ale inne rzeczy, które nie są poprawnie skonfigurowane itd.

## Zbyt niski poziom głośności

Być może głośność w Minecrafcie jest zbyt niska, aby usłyszeć dźwięk.
Upewnij się, że kanał MASTER oraz wszystkie pozostałe kanały są wystarczająco głośne.

## Konflikt modów

Być może inny mod jest niekompatybilny z systemem audio używanym przez moje mody.
W takim przypadku proszę otworzyć zgłoszenie na GitHubie, bardzo dziękuję.
