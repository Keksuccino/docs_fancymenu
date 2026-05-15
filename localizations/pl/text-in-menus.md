---
title: Tekst w menu
description: Jak dodawać treści tekstowe do menu.
---

# Tekst w menu

FancyMenu pozwala dodawać treści tekstowe do menu/ekranów za pomocą elementu **Tekst**.

Ten element jest przewijalny, w pełni obsługuje Markdown i zawijanie wierszy, co czyni go bardzo potężnym narzędziem do wyświetlania nawet złożonych treści tekstowych, ale świetnie sprawdza się także w przypadku prostych jednowierszowych komunikatów.

## Treść tekstu

Element Tekst może pobierać swoją zawartość na wiele sposobów. Umożliwia ustawienie źródła dla treści tekstowej, którym może być bezpośrednie zwykłe pole tekstowe, lokalny plik tekstowy w folderze `assets` FancyMenu (`/config/fancymenu/assets/`), internetowy plik tekstowy (przez URL) albo lokalny plik tekstowy wczytywany przez paczkę zasobów.

Korzystanie z typu źródła internetowego jako źródła tekstu jest szczególnie przydatne, jeśli chcesz stworzyć coś w rodzaju changeloga, który zawsze jest aktualny, albo ticker z wiadomościami i podobne rzeczy, bez potrzeby wydawania aktualizacji dla swojej paczki modów.

Pamiętaj, że FancyMenu buforuje zawartość źródeł tekstu, więc nie musi jej pobierać ponownie cały czas (co byłoby bardzo złe dla wydajności). Zawartość jest buforowana tylko na czas aktywnej sesji, więc ponowne uruchomienie gry wyczyści pamięć podręczną. Możesz też wyczyścić pamięć podręczną, przeładowując FancyMenu przez **pasek menu -> Dostosowywanie -> Przeładuj FancyMenu**.

## Placeholdery

Element Tekst obsługuje również system placeholderów FancyMenu, co umożliwia dynamiczne treści tekstowe reagujące na różne zmiany w menu, światach, graczach itd.

## Dostosowywanie lub wyłączanie Markdown

Jeśli chcesz dostosować kolory nagłówków lub innych elementów związanych z Markdownem, po prostu **kliknij element Tekst prawym przyciskiem myszy** i wybierz **Markdown**. W otwieranym menu kontekstowym podrzędnym zobaczysz wiele opcji dostosowania wyglądu i działania parsera Markdown.

Jeśli w ogóle nie chcesz parsowania Markdown, co może poprawić wydajność przy długich treściach tekstowych, możesz całkowicie wyłączyć Markdown w menu **Markdown** po **kliknięciu elementu Tekst prawym przyciskiem myszy**.

## Wyłączanie zawijania wierszy

Jeśli nie chcesz zawijania wierszy, możesz je wyłączyć, **klikając element Tekst prawym przyciskiem myszy**.

## Wyłączanie przewijania

Elementy tekstowe domyślnie są przewijalne i jeśli element uzna, że użytkownik musi przewinąć, aby zobaczyć całą zawartość, wyświetli paski przewijania — małe, szare belki po prawej stronie i na dole elementu Tekst (paski przewijania pionowe i poziome).

Możesz wyłączyć te paski, przełączając opcję **Przewijanie** w menu, które otwiera się po **kliknięciu elementu prawym przyciskiem myszy**. Spowoduje to wyłączenie przewijania w ogóle, a nie tylko samych pasków. Jeśli wolisz, aby paski były niewidoczne, możesz ustawić własne tekstury pasków przewijania, klikając element prawym przyciskiem myszy. Wystarczy ustawić tam całkowicie przezroczystą teksturę.

## Surowy format tekstu komponentów Minecrafta (serializowane komponenty JSON)

Element Tekst NIE obsługuje surowego formatu komponentów Minecrafta. Format ten jest obsługiwany wyłącznie przez etykiety przycisków i suwaków.
