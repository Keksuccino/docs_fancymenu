---
title: Lokalizacje przechowywania danych
description: >-
  Gdzie FancyMenu przechowuje układy, zasoby, konfigurację oraz trwały stan
  wykonania.
---

# Lokalizacje przechowywania danych

`<game-directory>` oznacza aktywny folder instancji Minecrafta, który może różnić się od `.minecraft`.

Katalogi i pliki są zwykle tworzone dopiero po zainicjowaniu lub użyciu powiązanej funkcji. Zamknij Minecrafta przed ręczną edycją wygenerowanych plików stanu i zachowaj kopię zapasową podczas migracji lub resetowania danych.

# Układy, zasoby i konfiguracja

Niektóre wpisy są skonfigurowanymi ręcznie ustawieniami lub zasobami; inne to stan, który FancyMenu aktualizuje w czasie działania.

| System / funkcja | Plik lub katalog |
| --- | --- |
| Ekrany konfigurowalne | `<game-directory>/config/fancymenu/customizablemenus.txt` |
| [Niestandardowe GUI](./custom-guis) i reguły nadpisywania ekranów | `<game-directory>/config/fancymenu/custom_gui_screens.txt` |
| Układy | `<game-directory>/config/fancymenu/customization/` |
| [Zasoby lokalne](./resources#local-resources) | `<game-directory>/config/fancymenu/assets/` |
| [Niestandardowe pliki lokalizacji](./localization#fancymenu-custom-localization-files) | `<game-directory>/config/fancymenu/custom_locals/` |
| [Panoramy](./panoramas) | `<game-directory>/config/fancymenu/panoramas/` |
| [Pokazy slajdów](./slideshows) | `<game-directory>/config/fancymenu/slideshows/` |
| [Zmienne FancyMenu](./variables) | `<game-directory>/config/fancymenu/user_variables.db` |
| Metadane kontrolera [elementu wideo](./elements#video) | `<game-directory>/config/fancymenu/video_element_controller_metas.json` |
| Metadane kontrolera [elementu audio](./elements#audio) | `<game-directory>/config/fancymenu/audio_element_controller_metas.json` |
| Serwerowe listenery [FM Data](./fm-data) | `<game-directory>/config/fancymenu/fmdata_server_listeners.json` |
| Dane powitalne [FM Data](./fm-data) | `<game-directory>/config/fancymenu/fmdata_welcome_data.json` |
| Instancje [listenerów](./listeners) i skrypty akcji | `<game-directory>/config/fancymenu/listener_instances.txt` |
| [Schedulery](./schedulers) | `<game-directory>/config/fancymenu/scheduler_instances.txt` |

`customizablemenus.txt` jest zarządzany przez przełącznik **Current Screen Customization** i przechowuje konkretne identyfikatory klas ekranów. Nie dodawaj identyfikatorów [Universal Layout](./universal-layouts); FancyMenu ignoruje je podczas wczytywania pliku.

Na serwerze dedykowanym dwa pliki FM Data są względne względem głównego katalogu gry tego serwera. Pozostała konfiguracja i zasoby należące do klienta znajdują się w instancji każdego gracza.

# Trwały stan wykonania

FancyMenu przechowuje dodatkowy wygenerowany stan per instancja poza `config/fancymenu/`. Uwzględniaj te ścieżki w kopii zapasowej tylko wtedy, gdy chcesz zachować powiązany stan użytkownika/wykonania; nie są to definicje układów ani źródłowe zasoby.

| System / funkcja | Plik lub katalog |
| --- | --- |
| Stany [Checkbox](./elements#checkbox) inne niż zmienne | `<game-directory>/checkbox_states.json` |
| Pozycje/metadane elementu [Dragger](./dragger) | `<game-directory>/fancymenu_data/dragger_metas.json` |
| Stan ostatniego świata | `<game-directory>/fancymenu_data/last_world.fmdata` |
| Stan [Seamless World Loading](./seamless-world-loading) | `<game-directory>/fancymenu_data/seamless_world_loading/` |
| Zapis stanu zwierzaka Buddy i poziomowania | `<game-directory>/fancymenu_data/buddy/` |
| Pozycje i widoczność widżetów edytora układu | `<game-directory>/config/fancymenu/layout_editor/widgets/` |
| Znacznik inicjalizacji domyślnej skali GUI | `<game-directory>/fancymenu_data/default_scale_set.fm` |

Buddy przechowuje stan zwierzaka oraz stan poziomowania/osiągnięć w oddzielnych plikach JSON w swoim katalogu. Każda instancja nakładki Buddy używa własnej pary plików.

Pliki widżetów edytora układu przechowują pozycję, rozmiar, widoczność, stan rozwinięcia oraz stronę przyciągania każdego widżetu. Usunięcie `default_scale_set.fm` powoduje, że przy następnym uruchomieniu FancyMenu potraktuje skonfigurowaną domyślną skalę GUI tak, jakby nie została jeszcze zastosowana.
