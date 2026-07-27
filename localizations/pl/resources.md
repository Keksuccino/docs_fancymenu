---
title: Zasoby
description: >-
  Jak działają zasoby w FancyMenu. Obejmuje lokalizacje zasobów, zasoby lokalne
  i zasoby internetowe.
---

# Zasoby

Pola zasobów mogą ładować المحتوى z:

- **Minecraft:** lokalizacja zasobu udostępniana przez Minecrafta lub paczkę zasobów.
- **Lokalne:** plik w aktywnej instancji gry.
- **Sieć:** bezpośredni adres URL pliku.

Większość pól obrazów, dźwięków, wideo i tekstu używa tego samego wybieraka zasobów. Wybierak zawiera przeglądarkę zasobów Minecrafta i zawartości paczek zasobów.

# Zasoby Minecrafta (Paczki zasobów)

Lokalizacje zasobów używają formatu `namespace:path`. Namespace to katalog znajdujący się bezpośrednio pod `assets`, a path to wszystko znajdujące się poniżej tego namespace.

Na przykład rozważ obraz z paczki zasobów zapisany jako `/assets/custom_resources/images/image.png`.
Jego lokalizacja zasobu to `custom_resources:images/image.png`.

> [!NOTE]
> Wbudowane zasoby Minecrafta zwykle używają namespace `minecraft`.

# Zasoby lokalne

Przechowuj zasoby lokalne w `<game-directory>/config/fancymenu/assets/`. `<game-directory>` to folder aktywnej instancji, który może różnić się od `.minecraft`.

Pola zasobów mogą wyświetlać tę samą ścieżkę jako `/config/fancymenu/assets/example.png`. W tych polach początkowy `/` nadal oznacza `<game-directory>`; nie jest to ścieżka od katalogu głównego systemu plików.

Pliki te mogą być [dołączone do modpacka](./modpacks) przez jego folder config.

Aby zobaczyć pełną mapę układu FancyMenu, ścieżek zasobów, konfiguracji i wygenerowanego stanu, zobacz [Lokalizacje przechowywania danych](./data-storage-locations).

# Zasoby internetowe

Użyj bezpośredniego adresu URL do pliku, na przykład `https://example-domain.net/image.png`. Strony i linki przekierowujące działają wolniej i częściej zawodzą niż bezpośrednie adresy URL kończące się nazwą pliku zasobu i jego rozszerzeniem.

# Placeholdery w źródłach zasobów

Pola zasobów obsługiwane przez wybierak mogą używać [placeholderów](./placeholders) w lokalnych ścieżkach, adresach URL i lokalizacjach zasobów Minecrafta. Aby edytować je bezpośrednio, wybierz **Otwórz w edytorze** obok pola źródła.

> [!WARNING]
> Wejścia zasobów, które nie używają standardowego wybieraka, mogą nie obsługiwać placeholderów ani aktualizacji źródła na żywo.
