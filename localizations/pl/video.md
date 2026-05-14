---
title: Wideo (MP4)
description: Co warto wiedzieć o używaniu filmów w FancyMenu.
---

# Wideo

FancyMenu obsługuje odtwarzanie filmów MP4 jako elementów, tła menu oraz zawartości Game Intro.

FancyMenu 3.9.0 dodaje nowy natywny element **Wideo** oraz tło menu **Wideo**, obsługiwane przez Watermedia V3. Stary typ elementu/tła **Video [MCEF]** jest przestarzały i powinien być zachowany tylko dla starych układów, które nadal go potrzebują.

Dostępne są również następujące **akcje** do sterowania tłami wideo i elementami wideo:

- **Set Video Element Volume** — ustawia głośność elementu wideo
- **Set Video Element Play Time** — ustawia pozycję odtwarzania elementu wideo na znacznik czasu w milisekundach
- **Toggle Video Element Paused State** — przełącza stan pauzy elementu wideo
- **Set Video Background Volume** — ustawia głośność tła menu wideo
- **Set Video Background Play Time** — ustawia pozycję odtwarzania tła menu wideo na znacznik czasu w milisekundach
- **Toggle Video Background Paused State** — przełącza stan pauzy tła menu wideo

Oraz następujące **placeholders**, aby pobierać informacje o tłach wideo i elementach wideo:

- **Video Element Volume** — pobiera głośność elementu wideo
- **Video Element Duration** — pobiera czas trwania elementu wideo
- **Video Element Play Time** — pobiera aktualny czas odtwarzania (postęp) elementu wideo
- **Video Element Paused State** — pobiera stan pauzy (true/false) elementu wideo
- **Video Background Volume** — pobiera głośność tła menu wideo
- **Video Background Duration** — pobiera czas trwania tła menu wideo
- **Video Background Play Time** — pobiera aktualny czas odtwarzania (postęp) tła menu wideo
- **Video Background Paused State** — pobiera stan pauzy (true/false) tła menu wideo

Placeholders czasu trwania i czasu odtwarzania zwracają domyślnie `MM:SS`. Ustaw `output_as_timestamp` na `true`, gdy potrzebujesz znaczników czasu w milisekundach. Placeholders czasu odtwarzania nadal mogą używać `show_percentage` do wartości postępu 0-100.

FancyMenu 3.9.0 dodaje również listener **On Video Playback Status Changed**, który może reagować na `PLAYING`, `PAUSED`, `STOPPED` i `FINISHED`.

## Wymagania

Aby używać nowego natywnego elementu Wideo i typu tła menu, musisz zainstalować:

- **Watermedia V3**
- **Watermedia Binaries V3**

Są to zależności opcjonalne, więc trzeba je dodać do instancji ręcznie, jeśli chcesz korzystać z obsługi wideo.

Przestarzały typ **Video [MCEF]** nadal korzysta z MCEF. W nowych układach używaj zamiast tego natywnego typu Video opartego na Watermedia.

## Wideo na ekranach ładowania

Obsługa wideo NIE działa na ekranach ładowania (ekran ładowania gry/zasobów i ekran ładowania świata).

Oznacza to również, że NIE powinieneś dodawać wideo do ekranu ładowania gry przez **Drippy Loading Screen**, ponieważ w większości przypadków nie będzie to działać.

Zamiast tego na ekranach ładowania używaj krótkich, prostych plików AFMA/FMA, ponieważ użytkownicy zwykle nie zauważają ich ponownego wczytywania, jeśli animacja jest wystarczająco prosta i krótka.

## Rozwiązywanie problemów

Jeśli masz problemy z natywną obsługą wideo, najpierw upewnij się, że zarówno Watermedia V3, jak i Watermedia Binaries V3 są zainstalowane oraz pasują do Twojej wersji Minecrafta/modloadera.
