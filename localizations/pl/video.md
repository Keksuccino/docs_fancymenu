---
title: Filmy (MP4)
description: Co należy wiedzieć o używaniu filmów w FancyMenu.
---
# Filmy

FancyMenu obsługuje odtwarzanie filmów MP4 jako [elementów](./elements#video), [teł menu](./menu-backgrounds) oraz zawartości [wprowadzenia do gry](./game-intro).

Natywny [element **Wideo**](./elements#video) oraz tło menu **Wideo** korzystają z Watermedia V3. Stare typy **Wideo [Rinku]** są przestarzałe i powinny pozostać wyłącznie w układach, które nadal ich wymagają.

Dostępne są również następujące **akcje** służące do sterowania tłami menu i elementami wideo:

- [**Ustaw głośność elementu wideo**](./action-scripts#set-video-element-volume-set_video_element_volume) ustawia głośność elementu Wideo.
- [**Ustaw czas odtwarzania elementu wideo**](./action-scripts#set-video-element-play-time-set_video_element_play_time) przewija element Wideo do podanego znacznika czasu w milisekundach.
- [**Przełącz stan wstrzymania elementu wideo**](./action-scripts#toggle-video-element-paused-state-toggle_video_element_pause_state) przełącza stan wstrzymania elementu Wideo.
- [**Ustaw głośność tła wideo**](./action-scripts#set-video-background-volume-set_video_menu_background_volume) ustawia głośność tła menu Wideo.
- [**Ustaw czas odtwarzania tła wideo**](./action-scripts#set-video-background-play-time-set_video_menu_background_play_time) przewija tło menu Wideo do podanego znacznika czasu w milisekundach.
- [**Przełącz stan wstrzymania tła wideo**](./action-scripts#toggle-video-background-paused-state-toggle_video_menu_background_pause_state) przełącza stan wstrzymania tła menu Wideo.

Dostępne są także następujące **zmienne** umożliwiające uzyskanie informacji o tłach menu i elementach wideo:

- [**Głośność elementu wideo**](./placeholders#video-element-volume-video_element_vol) zwraca głośność elementu Wideo.
- [**Czas trwania elementu wideo**](./placeholders#video-element-duration-video_element_duration) zwraca czas trwania elementu Wideo.
- [**Czas odtwarzania elementu wideo**](./placeholders#video-element-play-time-video_element_playtime) zwraca bieżący postęp odtwarzania elementu Wideo.
- [**Stan wstrzymania elementu wideo**](./placeholders#video-element-paused-state-video_element_paused_state) zwraca informację, czy element Wideo jest wstrzymany.
- [**Głośność tła wideo**](./placeholders#video-background-volume-video_background_vol) zwraca głośność tła menu Wideo.
- [**Czas trwania tła wideo**](./placeholders#video-background-duration-video_background_duration) zwraca czas trwania tła menu Wideo.
- [**Czas odtwarzania tła wideo**](./placeholders#video-background-play-time-video_background_playtime) zwraca bieżący postęp odtwarzania tła menu Wideo.
- [**Stan wstrzymania tła wideo**](./placeholders#video-background-paused-state-video_background_paused_state) zwraca informację, czy tło menu Wideo jest wstrzymane.

Zmienne dotyczące czasu trwania i czasu odtwarzania domyślnie zwracają wartość w formacie `MM:SS`. Ustaw `output_as_timestamp` na `true`, jeśli potrzebujesz znaczników czasu w milisekundach. Zmienne dotyczące czasu odtwarzania mogą nadal używać `show_percentage` do wyświetlania postępu w zakresie od 0 do 100.

Wartości głośności i stanu wstrzymania to metadane kontrolera powiązane z identyfikatorem. Wartości czasu trwania i czasu odtwarzania wymagają, aby odpowiedni element Wideo lub tło było aktywne i gotowe na bieżącym ekranie.

Listener [**Po zmianie stanu odtwarzania wideo**](./listeners#on-video-playback-status-changed-video_playback_status_changed) może reagować na stany `PLAYING`, `PAUSED`, `STOPPED` i `FINISHED`.

## Wymagania

Aby korzystać z nowego natywnego elementu Wideo i typu tła menu, należy zainstalować:

- **Watermedia V3**
- **Watermedia Binaries V3**

Są to opcjonalne zależności, dlatego należy dodać je ręcznie do instancji, jeśli chcesz korzystać z obsługi filmów.

Natywne odtwarzanie filmów wymaga również renderera OpenGL. Odtwarzanie za pomocą Watermedia jest niedostępne, gdy Minecraft korzysta z Vulkan — aby używać elementów Wideo, teł menu Wideo i [wprowadzeń do gry zawierających filmy](./game-intro), przełącz się na OpenGL.

Przestarzały typ **Wideo [Rinku]** nadal korzysta z [Rinku](https://modrinth.com/mod/rinku). W nowych układach używaj natywnego typu Wideo opartego na Watermedia.

## Filmy na ekranach ładowania

Obsługa filmów NIE działa na ekranach ładowania (ekranie ładowania gry/zasobów oraz ekranie ładowania świata).

Oznacza to również, że NIE należy dodawać filmów do ekranu ładowania gry za pomocą **Drippy Loading Screen**, ponieważ w większości przypadków nie zadziałają.

Zamiast tego na ekranach ładowania używaj krótkich, prostych [animacji AFMA/FMA](./fma).

## Rozwiązywanie problemów

Jeśli natywny film nie jest odtwarzany, upewnij się, że wersje Watermedia V3 i Watermedia Binaries V3 są zgodne z wersją Minecrafta/loadera modów oraz że Minecraft korzysta z OpenGL zamiast Vulkan.
