---
title: Uniwersalne układy
description: Jak tworzyć i używać uniwersalnych układów.
---

# Czym są uniwersalne układy?

Uniwersalne układy to potężna funkcja w FancyMenu, która pozwala tworzyć układy możliwe do zastosowania na **wielu ekranach**, a nie tylko na jednym konkretnym. Dzięki temu są niezwykle przydatne do tworzenia spójnych elementów interfejsu, które pojawiają się w całej grze.

Możesz traktować uniwersalne układy jako układy „globalne”, które mogą pojawiać się wszędzie w grze.

# Dlaczego warto używać uniwersalnych układów?

Uniwersalne układy są bardzo przydatne, gdy chcesz:

- dodać to samo tło do wszystkich ekranów
- utworzyć logo lub tekst, który pojawia się na wielu ekranach
- sprawić, by elementy audio odtwarzały się dalej na wielu ekranach
- zbudować spójny wygląd i styl w całej grze

# Jak działają uniwersalne układy

Gdy tworzysz uniwersalny układ, jest on domyślnie wczytywany z **każdym ekranem** w grze. Oznacza to, że wszystkie elementy dodane do uniwersalnego układu, takie jak przyciski, obrazy czy tekst, będą widoczne na wszystkich ekranach.

Ale nie martw się! Możesz też ustawić, aby uniwersalny układ wczytywał się tylko na określonych ekranach. W tym celu przewiń do sekcji **blacklist** i **whitelist**.

# Tworzenie uniwersalnego układu

1. Otwórz dowolny ekran w grze
2. Naciśnij **Ctrl+Alt+C**, aby wyświetlić menu personalizacji
3. Przejdź do **Układy → Nowy → Dla wszystkich ekranów [Uniwersalny]**
4. Zaprojektuj swój układ, używając elementów takich jak obrazy, tekst lub przyciski
5. Zapisz układ, nadając mu opisową nazwę

# Zarządzanie tym, które ekrany otrzymują Twój uniwersalny układ

## Korzystanie z blacklisty

Blacklista pozwala określić ekrany, na których NIE chcesz, aby pojawiał się Twój uniwersalny układ:

1. W edytorze układu kliknij prawym przyciskiem myszy tło
2. Wybierz **Ustawienia układu → Opcje uniwersalnego układu**
3. Kliknij **Dodaj ekran do blacklisty**
4. Wpisz identyfikator ekranu (np. `title_screen` dla ekranu tytułowego)

Teraz Twój uniwersalny układ będzie widoczny na wszystkich ekranach, Z WYJĄTKIEM tych, które dodasz do blacklisty.

## Korzystanie z whitelisty

Whitelist działa odwrotnie — pokazuje Twój uniwersalny układ TYLKO na określonych ekranach:

1. W edytorze układu kliknij prawym przyciskiem myszy tło
2. Wybierz **Ustawienia układu → Opcje uniwersalnego układu**
3. Kliknij **Dodaj ekran do whitelisty**
4. Wpisz identyfikator każdego ekranu, na którym chcesz, aby układ się pojawiał

Przy użyciu whitelisty Twój uniwersalny układ będzie widoczny TYLKO na ekranach, które podasz.

# Jak znaleźć identyfikatory ekranów

Aby dodać ekrany do whitelisty lub blacklisty, musisz znać ich identyfikatory:

1. Przejdź do ekranu, który chcesz zidentyfikować
2. Naciśnij **Ctrl+Alt+C**, aby otworzyć menu personalizacji
3. Kliknij **Personalizacja → Skopiuj identyfikator bieżącego ekranu**
4. Identyfikator został teraz skopiowany do schowka

Możesz wkleić ten identyfikator do whitelisty lub blacklisty.

# Włączanie personalizacji dla wszystkich ekranów

Nie jest możliwe włączenie personalizacji dla wszystkich ekranów jednocześnie.
Jest to celowe i zapobiega sytuacjom, w których ktoś przypadkowo uszkodzi działanie gry, włączając personalizację dla modowanego ekranu, który nie jest obsługiwany.

# Wskazówki zaawansowane

## Zarządzanie kolejnością wczytywania

Gdy masz zarówno uniwersalne układy, jak i układy specyficzne dla ekranu, uniwersalne układy są wczytywane jako PIERWSZE. Oznacza to, że układy specyficzne dla ekranu mogą nadpisywać elementy z uniwersalnych układów.

## Wymagania wczytywania

Do swojego uniwersalnego układu możesz dodać wymagania wczytywania, aby był ładowany tylko w określonych warunkach:

1. Kliknij prawym przyciskiem myszy w edytorze
2. Wybierz **Ustawienia układu → Wymagania dotyczące całego układu**
3. Dodaj warunki, takie jak pora dnia, system operacyjny lub inne wymagania
