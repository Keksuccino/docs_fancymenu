---
title: Filmy (MP4)
description: Co warto wiedzieć o używaniu filmów w FancyMenu.
sourceBlobSha: bd34c5c21a6c08d6b66a7b2acdaf9bd12739732f
---
# Filmy

FancyMenu obsługuje odtwarzanie filmów MP4 jako [elementów](/elements#video), [teł menu](/menu-backgrounds#video) oraz zawartości [wprowadzenia do gry](/game-intro).

Natywny element [**Wideo**](/elements#video) i tło menu **Wideo** korzystają z Watermedia V3. Starsze typy **Wideo [Rinku]** są przestarzałe i powinny pozostać tylko w układach, które nadal ich wymagają.

Dostępne są też następujące [akcje](/action-scripts) do sterowania tłami wideo i elementami wideo:

- [**Ustaw głośność elementu wideo**](/action-scripts#set-video-element-volume) ustawia głośność elementu Wideo.
- [**Ustaw czas odtwarzania elementu wideo**](/action-scripts#set-video-element-play-time) przewija element Wideo do wskazanego czasu w milisekundach.
- [**Przełącz stan wstrzymania elementu wideo**](/action-scripts#toggle-video-element-paused-state) przełącza stan wstrzymania elementu Wideo.
- [**Ustaw głośność tła wideo**](/action-scripts#set-video-background-volume) ustawia głośność tła menu Wideo.
- [**Ustaw czas odtwarzania tła wideo**](/action-scripts#set-video-background-play-time) przewija tło menu Wideo do wskazanego czasu w milisekundach.
- [**Przełącz stan wstrzymania tła wideo**](/action-scripts#toggle-video-background-paused-state) przełącza stan wstrzymania tła menu Wideo.

Dostępne są również następujące [placeholdery](/placeholders), które pozwalają uzyskać informacje o tłach wideo i elementach wideo:

- [**Głośność elementu wideo**](/placeholders#video-element-volume) zwraca głośność elementu Wideo.
- [**Czas trwania elementu wideo**](/placeholders#video-element-duration) zwraca czas trwania elementu Wideo.
- [**Czas odtwarzania elementu wideo**](/placeholders#video-element-play-time) zwraca bieżący postęp odtwarzania elementu Wideo.
- [**Stan wstrzymania elementu wideo**](/placeholders#video-element-paused-state) zwraca informację, czy element Wideo jest wstrzymany.
- [**Głośność tła wideo**](/placeholders#video-background-volume) zwraca głośność tła menu Wideo.
- [**Czas trwania tła wideo**](/placeholders#video-background-duration) zwraca czas trwania tła menu Wideo.
- [**Czas odtwarzania tła wideo**](/placeholders#video-background-play-time) zwraca bieżący postęp odtwarzania tła menu Wideo.
- [**Stan wstrzymania tła wideo**](/placeholders#video-background-paused-state) zwraca informację, czy tło menu Wideo jest wstrzymane.

Placeholdery czasu trwania i czasu odtwarzania domyślnie zwracają wartość w formacie `MM:SS`. Ustaw `output_as_timestamp` na `true`, jeśli potrzebujesz znaczników czasu w milisekundach. Placeholdery czasu odtwarzania nadal mogą używać `show_percentage`, aby zwracać wartości postępu z zakresu 0–100.

Wartości głośności i stanu wstrzymania to metadane kontrolera powiązane z identyfikatorem. Wartości czasu trwania i czasu odtwarzania wymagają, aby odpowiadający im element Wideo lub tło było aktywne i gotowe na bieżącym ekranie.

[Listener **Zmiana stanu odtwarzania wideo**](/listeners#video-playback-status-changed) może reagować na stany `PLAYING`, `PAUSED`, `STOPPED` i `FINISHED`.

## Wymagania

Aby korzystać z nowego natywnego elementu Wideo i typu tła menu, musisz zainstalować:

- **Watermedia V3**
- **Watermedia Binaries V3**

Są to opcjonalne zależności, więc jeśli chcesz korzystać z obsługi wideo, musisz dodać je ręcznie do instancji.

Natywne odtwarzanie wideo wymaga również renderera OpenGL. Odtwarzanie przez Watermedia jest niedostępne, gdy Minecraft korzysta z Vulkan; aby używać elementów Wideo, teł menu Wideo i [wideo we wprowadzeniu do gry](/game-intro), przełącz się na OpenGL.

Przestarzały typ **Wideo [Rinku]** nadal korzysta z [Rinku](https://modrinth.com/mod/rinku). W nowych układach używaj natywnego typu Wideo opartego na Watermedia.

## Filmy na ekranach ładowania

Obsługa wideo NIE działa na ekranach ładowania (ekranie ładowania gry lub zasobów ani ekranie ładowania świata).

Oznacza to również, że NIE należy dodawać filmów do ekranu ładowania gry za pomocą **Drippy Loading Screen**, ponieważ w większości przypadków nie będą działać.

Na ekranach ładowania używaj zamiast tego krótkich, prostych [animacji](/animations) (APNG lub GIF).

## Rozwiązywanie problemów

Jeśli natywne wideo się nie odtwarza, sprawdź, czy wersje Watermedia V3 i Watermedia Binaries V3 są zgodne z wersją Minecrafta i modloadera oraz czy Minecraft korzysta z OpenGL, a nie z Vulkan.
