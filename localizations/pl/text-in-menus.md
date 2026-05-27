---
title: Tekst w menu
description: Jak dodać tekst do menu.
---
# Tekst w menu

FancyMenu pozwala dodawać treść tekstową do menu/ekranów za pomocą elementu **Tekst**.

Ten element można przewijać, obsługuje pełny Markdown i zawijanie wierszy, dzięki czemu świetnie nadaje się nawet do wyświetlania złożonych treści tekstowych, ale doskonale sprawdza się także w prostych, jednolinijkowych tekstach.

# Treść tekstu

Element Tekst może pobierać swoją zawartość na wiele sposobów. Umożliwia ustawienie źródła tekstu, którym może być bezpośrednie zwykłe pole tekstowe, lokalny plik tekstowy w folderze `assets` FancyMenu (`/config/fancymenu/assets/`), internetowy plik tekstowy (przez URL) albo lokalny plik tekstowy wczytywany przez pakiet zasobów.

Użycie internetowego typu źródła jako źródła tekstu jest szczególnie przydatne, jeśli chcesz stworzyć coś takiego jak changelog, który zawsze jest aktualny, albo przewijane wiadomości i podobne rzeczy, bez potrzeby wydawania aktualizacji dla swojego modpacka.

Pamiętaj, że FancyMenu buforuje zawartość źródeł tekstu, aby nie musiał jej pobierać za każdym razem od nowa (co byłoby bardzo złe dla wydajności). Zawartość jest buforowana tylko na czas aktywnej sesji, więc ponowne uruchomienie gry wyczyści pamięć podręczną. Możesz też wyczyścić cache, przeładowując FancyMenu przez **pasek menu -> Dostosowywanie -> Przeładuj FancyMenu**.

# Zmienne

Element Tekst obsługuje również system zmiennych FancyMenu, co umożliwia dynamiczną treść tekstową reagującą na różne zmiany w menu, światach, graczach itd.

# Dostosowywanie lub wyłączanie Markdown

Jeśli chcesz dostosować kolory nagłówków lub inne elementy związane z Markdownem, po prostu **kliknij prawym przyciskiem myszy** element Tekst i wybierz **Markdown**. W otwartym podmenu zobaczysz wiele opcji pozwalających dostosować wygląd i działanie parsera Markdown.

Jeśli w ogóle nie chcesz używać parsowania Markdown, co może poprawić wydajność przy długiej treści tekstowej, możesz całkowicie wyłączyć Markdown w menu **Markdown** po **kliknięciu prawym przyciskiem myszy** elementu Tekst.

# Wyłączanie zawijania wierszy

Jeśli nie chcesz zawijania wierszy, możesz je wyłączyć, **klikając prawym przyciskiem myszy** element Tekst.

# Wyłączanie przewijania i ukrywanie uchwytów przewijania

Elementy tekstowe domyślnie można przewijać i jeśli element uzna, że użytkownik musi przewinąć, aby zobaczyć całą zawartość, wyświetli swoje paski/uchwyty przewijania, czyli małe, szare, półprzezroczyste paski (z zaokrąglonymi krawędziami) po prawej i na dole elementu Tekst (pionowy i poziomy pasek przewijania). Uchwyty przewijania bywają czasem mylone z cieniami.

Możesz wyłączyć te uchwyty, wyłączając opcję **Przewijanie** w menu, które otwiera się po **kliknięciu prawym przyciskiem myszy** elementu. Spowoduje to wyłączenie przewijania jako takiego, a nie tylko samych uchwytów. Jeśli chcesz tylko, aby uchwyty były niewidoczne, ale jednocześnie nadal dało się przewijać, możesz ustawić własne tekstury uchwytów przewijania, klikając prawym przyciskiem myszy element. Wystarczy ustawić tam całkowicie przezroczystą teksturę.

# Surowy format tekstu komponentów Minecrafta (serializowane komponenty JSON)

Element Tekst NIE obsługuje surowego formatu komponentów Minecrafta. Format ten jest obsługiwany wyłącznie przez etykiety przycisków i suwaków.
