---
title: Wideo (MP4)
description: Co warto wiedzieć o używaniu wideo w FancyMenu.
---
# Wideo

FancyMenu obsługuje odtwarzanie filmów MP4 jako [elementów](./elements#video), [tła menu](./menu-backgrounds) oraz treści [Intro gry](./game-intro).

Natywny [element **Wideo**](./elements#video) oraz tło menu **Wideo** korzystają z Watermedia V3. Stare typy **Wideo [MCEF]** są przestarzałe i powinny pozostać jedynie w układach, które nadal ich wymagają.

Dostępne są również następujące **akcje** do sterowania tłami wideo i elementami:

- [**Ustaw głośność elementu wideo**](./action-scripts#set-video-element-volume-set_video_element_volume) ustawia głośność elementu wideo.
- [**Ustaw czas odtwarzania elementu wideo**](./action-scripts#set-video-element-play-time-set_video_element_play_time) przeskakuje element wideo do znacznika czasu w milisekundach.
- [**Przełącz stan wstrzymania elementu wideo**](./action-scripts#toggle-video-element-paused-state-toggle_video_element_pause_state) przełącza stan wstrzymania elementu wideo.
- [**Ustaw głośność tła wideo**](./action-scripts#set-video-background-volume-set_video_menu_background_volume) ustawia głośność tła menu wideo.
- [**Ustaw czas odtwarzania tła wideo**](./action-scripts#set-video-background-play-time-set_video_menu_background_play_time) przeskakuje tło menu wideo do znacznika czasu w milisekundach.
- [**Przełącz stan wstrzymania tła wideo**](./action-scripts#toggle-video-background-paused-state-toggle_video_menu_background_pause_state) przełącza stan wstrzymania tła menu wideo.

Oraz następujące **placeholdery**, które pozwalają pobrać informacje o tłach i elementach wideo:

- [**Głośność elementu wideo**](./placeholders#video-element-volume-video_element_vol) zwraca głośność elementu wideo.
- [**Czas trwania elementu wideo**](./placeholders#video-element-duration-video_element_duration) zwraca czas trwania elementu wideo.
- [**Czas odtwarzania elementu wideo**](./placeholders#video-element-play-time-video_element_playtime) zwraca bieżący postęp odtwarzania elementu wideo.
- [**Stan wstrzymania elementu wideo**](./placeholders#video-element-paused-state-video_element_paused_state) zwraca informację, czy element wideo jest wstrzymany.
- [**Głośność tła wideo**](./placeholders#video-background-volume-video_background_vol) zwraca głośność tła menu wideo.
- [**Czas trwania tła wideo**](./placeholders#video-background-duration-video_background_duration) zwraca czas trwania tła menu wideo.
- [**Czas odtwarzania tła wideo**](./placeholders#video-background-play-time-video_background_playtime) zwraca bieżący postęp odtwarzania tła menu wideo.
- [**Stan wstrzymania tła wideo**](./placeholders#video-background-paused-state-video_background_paused_state) zwraca informację, czy tło menu wideo jest wstrzymane.

Placeholdery czasu trwania i czasu odtwarzania domyślnie zwracają `MM:SS`. Ustaw `output_as_timestamp` na `true`, gdy potrzebujesz znaczników czasu w milisekundach. Placeholdery czasu odtwarzania mogą nadal używać `show_percentage` dla wartości postępu 0-100.

Wartości głośności i stanu wstrzymania są metadanymi kontrolera powiązanymi z identyfikatorem. Wartości czasu trwania i czasu odtwarzania wymagają, aby pasujący element wideo lub tło były aktywne i gotowe na bieżącym ekranie.

[**Nasłuchiwacz Zmiana stanu odtwarzania wideo**](./listeners#on-video-playback-status-changed-video_playback_status_changed) może reagować na `PLAYING`, `PAUSED`, `STOPPED` i `FINISHED`.

## Wymagania

Aby używać nowego natywnego elementu Wideo i typu tła menu, musisz zainstalować:

- **Watermedia V3**
- **Binarne pliki Watermedia V3**

Są to zależności opcjonalne, więc muszą zostać dodane do instancji ręcznie, jeśli chcesz korzystać z obsługi wideo.

Natywne odtwarzanie wideo wymaga również renderera OpenGL. Odtwarzanie Watermedia jest niedostępne, gdy Minecraft używa Vulkan; przełącz się na OpenGL, aby korzystać z elementów Wideo, teł menu Wideo oraz [intro gry wideo](./game-intro).

Przestarzały typ **Wideo [MCEF]** nadal korzysta z MCEF. W nowych układach używaj zamiast tego natywnego typu Wideo opartego na Watermedia.

## Wideo na ekranach ładowania

Obsługa wideo NIE działa na ekranach ładowania (ekran ładowania gry/zasobów oraz ekran ładowania świata).

Oznacza to również, że NIE powinieneś dodawać wideo do ekranu ładowania gry za pomocą **Drippy Loading Screen**, ponieważ w większości przypadków nie będzie to działać.

Zamiast tego używaj krótkich, prostych [animacji AFMA/FMA](./fma) na ekranach ładowania.

## Rozwiązywanie problemów

Jeśli natywne wideo się nie odtwarza, upewnij się, że Watermedia V3 i Watermedia Binaries V3 są zgodne z Twoją wersją Minecrafta/modloadera oraz że Minecraft używa OpenGL zamiast Vulkan.
