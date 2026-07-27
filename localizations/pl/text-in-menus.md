---
title: Tekst w menu
description: Jak dodawać treści tekstowe do menu.
---
# Tekst w menu

FancyMenu pozwala dodawać treści tekstowe do menu/ekranów za pomocą elementu **Tekst**.

Ten element można przewijać, obsługuje pełny Markdown i zawijanie wierszy, co czyni go bardzo potężnym narzędziem do wyświetlania nawet złożonych treści tekstowych, ale świetnie sprawdza się też przy prostych, jednolinijkowych komunikatach.

# Treść tekstowa

Element Tekst może pobierać swoją zawartość na wiele sposobów. Pozwala ustawić źródło treści tekstowej, którym może być bezpośrednie zwykłe pole tekstowe, lokalny plik tekstowy w katalogu zasobów FancyMenu (`<game-directory>/config/fancymenu/assets/`), webowy plik tekstowy (przez URL) albo lokalny plik tekstowy wczytywany przez resource pack.

Korzystanie z webowego typu źródła jako źródła tekstu jest szczególnie przydatne, jeśli chcesz stworzyć coś w rodzaju changelogu, który zawsze jest aktualny, albo ticker wiadomości i podobne rzeczy, bez potrzeby wydawania aktualizacji dla swojego modpacka.

Pamiętaj, że FancyMenu buforuje zawartość źródeł tekstowych, aby nie musieć jej pobierać ponownie cały czas (co byłoby bardzo złe dla wydajności). Zawartość jest buforowana tylko na czas aktywnej sesji, więc ponowne uruchomienie gry wyczyści pamięć podręczną. Możesz też wyczyścić pamięć podręczną, przeładowując FancyMenu przez **pasek menu -> Dostosowywanie -> Przeładuj FancyMenu**.

# Placeholders

Element Tekst obsługuje również system placeholderów FancyMenu, co umożliwia dynamiczne zmienianie treści tekstu i reagowanie na różne zmiany w menu, światach, graczach itd.

# Dostosowywanie lub wyłączanie Markdown

Jeśli chcesz dostosować kolory nagłówków lub inne rzeczy związane z Markdown, po prostu **kliknij prawym przyciskiem myszy** element Tekst i wybierz **Markdown**. W podmenu kontekstowym, które się otworzy, zobaczysz wiele opcji pozwalających dostosować wygląd i działanie parsera Markdown.

Jeśli w ogóle nie chcesz parsowania Markdown, co może poprawić wydajność przy długich treściach tekstowych, możesz całkowicie wyłączyć Markdown w menu **Markdown** po **kliknięciu prawym przyciskiem myszy** elementu Tekst.

# Wyłączanie zawijania wierszy

Jeśli nie chcesz zawijania wierszy, możesz je wyłączyć, **klikając prawym przyciskiem myszy** element Tekst.

# Wyłączanie przewijania i ukrywanie uchwytów przewijania

Elementy tekstowe są domyślnie przewijalne i jeśli element uzna, że użytkownik musi przewinąć zawartość, aby zobaczyć wszystko, wyświetli paski/uchwyty przewijania — małe, szare, półprzezroczyste paski (z zaokrąglonymi krawędziami) po prawej i dolnej stronie elementu Tekst (paski przewijania pionowego i poziomego). Uchwyty przewijania bywają czasem mylone z cieniami.

Możesz wyłączyć te uchwyty, odznaczając opcję **Przewijanie** w menu, które otwiera się po **kliknięciu prawym przyciskiem myszy** na element. Spowoduje to wyłączenie przewijania jako takiego, a nie tylko samych uchwytów. Jeśli chcesz tylko, aby uchwyty były niewidoczne, ale nadal chcesz móc przewijać, możesz ustawić własne tekstury uchwytów przewijania, klikając prawym przyciskiem myszy element. Po prostu ustaw tam całkowicie przezroczystą teksturę.

# Surowy format tekstu komponentów Minecrafta (serializowane komponenty JSON)

Element Tekst NIE obsługuje surowego formatu komponentów Minecrafta. Format ten jest obsługiwany tylko przez etykiety przycisków i suwaków.
