---
title: Zasoby
description: >-
  Jak działają zasoby w FancyMenu. Obejmuje lokalizacje zasobów, zasoby lokalne
  i zasoby internetowe.
---

# Zasoby

System zasobów FancyMenu umożliwia korzystanie z zasobów z własnego systemu ładowania zasobów Minecrafta (**Resource Packs**), zasobów **lokalnych** (plików z systemu klienta) oraz źródeł **webowych** (plików przechowywanych online).

Prawie wszystkie wejścia zasobów — czy to obrazy, dźwięki, wideo czy tekst — są ustawiane za pomocą selektora zasobów FancyMenu. Istnieją jednak pewne wyjątki, na przykład podczas ustawiania ścieżki źródłowej dla placeholdera lub akcji, ale w większości miejsc zasoby ustawiasz przez ten sam interfejs selektora zasobów.

Gdy ustawiasz wejście zasobu za pomocą interfejsu selektora zasobów, wybierasz zasadniczo tak zwane „źródło zasobu” (tak nazywa je FancyMenu), którym może być ścieżka, link lub lokalizacja zasobu, w zależności od typu źródła.

FancyMenu 3.9.0 dodaje przeglądarkę zasobów Minecrafta do selektora zasobów. Umożliwia ona przeglądanie zasobów wczytanych przez paczki zasobów jak katalogu, zamiast wpisywania każdej lokalizacji zasobu ręcznie.

# Zasoby Minecrafta (Resource Packs)

Minecraft używa tak zwanych „lokalizacji zasobów”, aby „wskazać” na zasób.

Lokalizacje zasobów zapisane jako tekst składają się z dwóch części, oddzielonych dwukropkiem (`:`).
Pierwsza część to **przestrzeń nazw** (namespace), a druga ścieżka to reszta **ścieżki do zasobu**, włącznie z nazwą zasobu i rozszerzeniem pliku.

**Przestrzeń nazw** lokalizacji zasobu to zawsze po prostu **katalog/folder najwyższego poziomu** pełnej ścieżki do zasobu.

Załóżmy więc, że wczytujesz paczkę zasobów z zasobem o nazwie `image.png`, który znajduje się w `/assets/custom_resources/images/image.png`.
W takim przypadku **przestrzenią nazw** lokalizacji zasobu byłoby `custom_resources`, ponieważ `/assets/` to tylko miejsce, z którego Minecraft wczytuje wszystkie swoje zasoby, więc `custom_resources` jest **katalogiem najwyższego poziomu** tego zasobu.
Oznacza to, że `images/image.png` to **reszta ścieżki** do zasobu.

Poprawna lokalizacja zasobu dla `image.png` wyglądałaby więc tak:
`custom_resources:images/image.png`

> **Ciekawostka**: Ponieważ Minecraft przechowuje większość swoich zasobów w `/assets/minecraft/`, **przestrzenią nazw** większości zasobów Minecrafta jest `minecraft`.
{.is-info}

# Zasoby lokalne

Najprostszym sposobem wczytywania zasobów jest po prostu użycie lokalnych plików przechowywanych na kliencie (i w większości przypadków dołączanych do modpacków).

FancyMenu pozwala wczytywać wyłącznie lokalne zasoby przechowywane w `/config/fancymenu/assets/`, więc upewnij się, że wszystkie zasoby znajdują się właśnie tam!

Dzięki temu bardzo łatwo jest też [dołączać lokalne zasoby do modpacków](./modpacks), ponieważ większość systemów modpacków (CurseForge, Modrinth itp.) domyślnie obsługuje dołączanie folderów konfiguracji modów.

# Zasoby webowe

Gdy chcesz dynamicznie zmieniać zasoby bez konieczności aktualizowania modpacka, zasoby **webowe** będą najlepszym rozwiązaniem.

Zasób webowy to po prostu **URL** do pliku przechowywanego na serwerze, na przykład `https://example-domain.net/image.png`.

Pamiętaj, aby zawsze używać **BEZPOŚREDNICH URL-i** — czyli adresów kończących się **nazwą pliku i rozszerzeniem** zasobu, tak jak w przykładzie powyżej.
Korzystanie z niebezpośrednich URL-i pogarsza wydajność i częściej prowadzi do błędów.

# Placeholdery w źródłach zasobów

Możliwe jest używanie placeholderów FancyMenu w źródłach zasobów, takich jak ścieżka do źródła lokalnego, URL do źródła webowego lub lokalizacja zasobu Minecrafta.

Umożliwia to dynamiczną zmianę źródeł, na przykład zmianę źródła obrazu tła menu po ustawieniu zmiennej FancyMenu, aby wyświetlić inne tło w zależności od wartości tej zmiennej.

Możesz ręcznie edytować źródło, klikając przycisk **Open in Editor** po prawej stronie pola wejściowego źródła zasobu.

> Pamiętaj, że dotyczy to wyłącznie wejść zasobów korzystających ze standardowego interfejsu selektora zasobów. Możliwe, że *niektóre* wejścia zasobów, które nie używają selektora, **NIE** obsługują placeholderów albo nie aktualizują się dynamicznie po zmianie placeholdera.
{.is-warning}
