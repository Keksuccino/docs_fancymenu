---
title: Lokalizacje przechowywania danych
description: >-
  Gdzie FancyMenu zapisuje układy, zasoby, ustawienia i pozostałe dane oraz
  które pliki należą do profili.
sourceBlobSha: 30dd81ed90e08184e3063892870e3325d7d7c5cb
---

# Lokalizacje przechowywania danych

FancyMenu zapisuje wszystkie dane w dwóch folderach katalogu gry. Chodzi o folder instancji launchera, który może być inny niż `.minecraft`.

- `config/fancymenu/` zawiera konfigurację: układy, zasoby, zmienne, ustawienia i inne dane. To folder wczytanego [profilu](/profiles), dlatego paczki modów dołączają ten folder.
- `fancymenu_data/` zawiera dane tej instancji gry, takie jak pozycje elementów Dragger i pobrane pliki. Dane te pozostają takie same we wszystkich profilach.

**Pasek menu -> Narzędzia -> Otwórz katalog FancyMenu** otwiera folder `config/fancymenu/`.

Większość plików i folderów pojawia się dopiero po użyciu danej funkcji. Przed zmianą lub usunięciem plików zamknij grę.

> [!TIP]
> Aby współdzielić te foldery między instancjami, możesz przenieść je w inne miejsce, a w ich dotychczasowej lokalizacji utworzyć dowiązanie symboliczne (w systemie Windows — junction).

# Twoja konfiguracja

Wszystko znajduje się w `<game-directory>/config/fancymenu/`. Cała zawartość należy do wczytanego [profilu](/profiles).

| Co | Gdzie |
| --- | --- |
| Układy w plikach `.txt`, również w podfolderach | `customization/` |
| [Zasoby lokalne](/resources#local-resources), takie jak obrazy i dźwięki | `assets/` |
| Ustawienia FancyMenu | `options.txt` |
| Ekrany z włączoną opcją **Dostosowywanie bieżącego ekranu** | `customizablemenus.txt` |
| [Niestandardowe GUI](/custom-guis) i zastępowane przez nie ekrany | `custom_gui_screens.txt` |
| [Zmienne](/variables) | `user_variables.db` |
| [Nasłuchiwacze](/listeners) | `listener_instances.txt` |
| [Harmonogramy](/schedulers) | `scheduler_instances.txt` |
| [Panoramy](/panoramas) | `panoramas/` |
| [Pokazy slajdów](/slideshows) | `slideshows/` |
| [Niestandardowe tłumaczenia](/localization#fancymenu-custom-localization-files) | `custom_locals/` |
| Motywy interfejsu FancyMenu (**pasek menu -> Dostosowywanie -> Ustawienia -> Interfejs FancyMenu -> Motyw interfejsu**) | `ui_themes/` |
| Stany [elementów pola wyboru](/elements#checkbox), które nie używają zmiennej | `checkbox_states.json` |
| Głośność i stan wstrzymania nadane [elementom wideo](/video) przez akcje | `video_element_controller_metas.json` |
| Głośność nadana [elementom audio](/elements#audio) przez akcje | `audio_element_controller_metas.json` |
| Stany włączenia i wyłączenia nadane [animatorom elementów](/element-animator) przez akcje | `animation_controller_states.json` |
| Ekrany z włączoną opcją **Udostępnij zawartość obszaru przewijania bieżącego ekranu** (zob. [Dostosowywanie przewijanych ekranów](/customizing-scrollable-screens)) | `normalized_scroll_screens.json` |
| Nasłuchiwacze serwera [FM Data](/fm-data) | `fmdata_server_listeners.json` |
| Dane powitalne [FM Data](/fm-data) | `fmdata_welcome_data.json` |
| Pozycja, rozmiar i widoczność widżetów edytora układów | `layout_editor/widgets/` |
| Nazwa, ikona i szczegóły wczytanego profilu | `profile.json` i `profile_icon.png` |
| Wszystkie pozostałe [profile](/profiles#where-profiles-are-stored) | `profiles/` |
| Lista aktualizacji starszych plików wykonanych już przez FancyMenu | `legacy_checklist.txt` |

Plik `customizablemenus.txt` zawiera nazwy ekranów w postaci nazw ich klas Java. Krótkie [identyfikatory ekranów](/screen-identifiers), takie jak `title_screen`, są w nim pomijane.

Na serwerze dedykowanym FancyMenu używa tylko dwóch plików [FM Data](/fm-data), znajdujących się w folderze serwera `config/fancymenu/`.

# Dane instancji

Wszystko znajduje się w `<game-directory>/fancymenu_data/`. Dane te nie należą do profili, więc pozostają przy zmianie profilu.

| Co | Gdzie |
| --- | --- |
| Pozycje [elementów Dragger](/dragger) | `dragger_metas.json` |
| Ostatni świat lub serwer — na potrzeby akcji **Wejdź do ostatniego świata / Dołącz do ostatniego serwera** oraz symbolu zastępczego **Ostatni świat lub serwer** | `last_world.fmdata` |
| Zrzuty ekranu z funkcji [Płynne wczytywanie świata](/seamless-world-loading) | `seamless_world_loading/` |
| Zapisane dane [Buddy](/decoration-overlays#buddy) — dwa pliki na każdą nakładkę Buddy | `buddy/` |
| Pliki funkcji [Eksport na potrzeby AI](/export-for-ai) | `ai_exports/` |
| Ulubione akcje w selektorze akcji | `action_favorites.json` |
| Głośność podglądu audio i wideo w selektorach plików | `browser_audio_settings.json` i `browser_video_settings.json` |
| Klatka wyświetlana przez [tło wideo](/video), gdy odtwarzanie jest wstrzymane | `video_thumbnails/` |
| FFmpeg pobierany przez FancyMenu na potrzeby [kreatora AFMA](/animations#fma-and-afma) | `ffmpeg_cache/` |
| Informacja, że FancyMenu ustawiło już [**domyślną skalę interfejsu**](/global-customizations) | `default_scale_set.fm` |
| Pliki tymczasowe, usuwane przy każdym uruchomieniu gry | `fancymenu_temp/` |

- FancyMenu ustawia **domyślną skalę interfejsu** tylko raz. Usuń `default_scale_set.fm`, aby przy następnym uruchomieniu skala została ustawiona ponownie.
- Zrzuty ekranu funkcji Płynne wczytywanie świata pokazują wszystko, co było widoczne na ekranie w świecie gry. Jeśli nie chcesz ich zachowywać, usuń je przy zamkniętej grze.

# Pliki ze starszych wersji

Starsze wersje FancyMenu zapisywały niektóre pliki w innych lokalizacjach. FancyMenu przenosi je przy następnym uruchomieniu gry:

- `checkbox_states.json` i `normalized_scroll_screens.json` z katalogu gry do `config/fancymenu/`.
- `dragger_metas.json` z `config/fancymenu/` do `fancymenu_data/`.
