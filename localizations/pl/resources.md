---
title: Zasoby
description: >-
  Jak działają zasoby w FancyMenu. Omówiono lokalizacje zasobów, zasoby lokalne
  i zasoby internetowe.
sourceBlobSha: eb783aaa0098ba295b3ebaf941bb4723e4d08970
---

# Zasoby

Pola zasobów mogą wczytywać zawartość z:

- **Minecrafta:** lokalizacji zasobu udostępnionej przez Minecrafta lub paczkę zasobów.
- **Lokalizacji:** pliku w aktywnej instancji gry.
- **Internetu:** bezpośredniego adresu URL pliku.

Większość pól obrazów, dźwięku, wideo i tekstu korzysta z tego samego selektora zasobów. Selektor zawiera przeglądarkę zawartości Minecrafta i paczek zasobów.

# Zasoby Minecrafta (paczki zasobów)

Lokalizacje zasobów mają format `namespace:path`. Przestrzeń nazw to katalog znajdujący się bezpośrednio w folderze `assets`, a ścieżka obejmuje wszystko, co znajduje się w tej przestrzeni nazw.

Na przykład rozważmy obraz z paczki zasobów znajdujący się w `/assets/custom_resources/images/image.png`.
Jego lokalizacja zasobu to `custom_resources:images/image.png`.

> [!NOTE]
> Wbudowane zasoby Minecrafta zwykle korzystają z przestrzeni nazw `minecraft`.

# Zasoby lokalne

Zasoby lokalne przechowuj w `<game-directory>/config/fancymenu/assets/`. `<game-directory>` to folder aktywnej instancji, który może różnić się od `.minecraft`.

Pola zasobów mogą wyświetlać tę samą ścieżkę jako `/config/fancymenu/assets/example.png`. W tych polach początkowy `/` nadal oznacza `<game-directory>`; nie jest to ścieżka od katalogu głównego systemu plików.

Pliki te można [dołączyć do paczki modów](/modpacks) w jej folderze konfiguracji.

Pełną mapę ścieżek FancyMenu dotyczących układu plików, zasobów, konfiguracji i wygenerowanego stanu znajdziesz w sekcji [Lokalizacje przechowywania danych](/data-storage-locations).

# Zasoby internetowe

Użyj bezpośredniego adresu URL pliku, na przykład `https://example-domain.net/image.png`. Strony i linki przekierowujące działają wolniej i częściej zawodzą niż bezpośrednie adresy URL kończące się nazwą pliku i jego rozszerzeniem.

# Symbole zastępcze w źródłach zasobów

Pola zasobów korzystające z selektora obsługują [symbole zastępcze](/placeholders) w lokalnych ścieżkach, adresach URL i lokalizacjach zasobów Minecrafta. Wybierz **Otwórz w edytorze** obok pola źródła, aby edytować je bezpośrednio.

> [!WARNING]
> Pola zasobów, które nie korzystają ze standardowego selektora, mogą nie obsługiwać symboli zastępczych ani aktualizacji źródła na żywo.
