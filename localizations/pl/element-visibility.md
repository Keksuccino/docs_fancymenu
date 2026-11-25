---
title: Widoczność elementów
description: >-
  Jak pokazywać i ukrywać elementy za pomocą wymagań, opóźnień, zanikania i
  przezroczystości oraz jak przełączać ich widoczność przyciskiem.
sourceBlobSha: 819fbc2639734fc8658f6fb65e9df6b1234e9cc5
---

# Widoczność elementów

Elementy nie muszą być widoczne przez cały czas. Mogą pojawiać się tylko w określonych sytuacjach, pokazywać się z opóźnieniem, stopniowo pojawiać się i znikać albo być włączane i wyłączane przyciskiem.

<img width="800" alt="Tekst powitalny pojawia się stopniowo kilka sekund po otwarciu ekranu, a następnie przycisk Server Rules stopniowo pokazuje i ukrywa panel z zasadami" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/element_visibility_toggle.gif?raw=true">

W edytorze układu elementy są zawsze widoczne, aby można było je edytować. Wszystkie opisane na tej stronie funkcje działają poza edytorem.

> [!TIP]
> Wszystkie wymagania znajdziesz na stronie [Wymagania](/conditions).

# Pokazywanie elementów tylko w określonych sytuacjach

Kliknij element prawym przyciskiem myszy, a następnie kliknij **Wymagania wyświetlania**. Element będzie widoczny tylko wtedy, gdy spełnione będą wszystkie jego [wymagania](/conditions), takie jak „kursor znajduje się nad tym przyciskiem”, „jest grudzień” lub „zmienna ma tę wartość”. FancyMenu sprawdza je cały czas, więc element natychmiast się pojawia lub znika.

- **Tryb wymagania** Odwraca działanie wymagania, na przykład „NIE jest grudzień”.
- Grupy umożliwiają określenie warunku „to LUB tamto”.
- Elementy vanilla również mają opcję **Wymagania wyświetlania**. Aby całkowicie usunąć taki element, zobacz [Usunięte elementy vanilla](/deleted-vanilla-elements).

Jak dodawać wymagania i łączyć je ze sobą: [Wymagania](/conditions#adding-a-requirement).

## Wczytuj raz na sesję

Kliknij element prawym przyciskiem myszy i włącz opcję **Wczytuj raz na sesję**. Element pojawi się przy pierwszym otwarciu jego ekranu. Gdy gracz przejdzie do innego ekranu, element pozostanie ukryty aż do ponownego uruchomienia gry.

To dobre rozwiązanie w przypadku wskazówek, które powinny pojawiać się tylko raz po uruchomieniu gry, na przykład „Naciśnij F1, aby wyświetlić sterowanie”. Podobny efekt można uzyskać w skryptach akcji za pomocą wymagania [**Tylko raz na sesję**](/conditions#only-once-per-session).

# Opóźnianie wyświetlania elementów

## Opóźnienie pojawienia się

Kliknij element prawym przyciskiem myszy, a następnie kliknij **Opóźnienie pojawienia się**:

- **Opóźnienie**:
  - **Brak opóźnienia**: element pojawia się od razu.
  - **Tylko za pierwszym razem**: opóźnienie występuje tylko przy pierwszym pojawieniu się elementu po uruchomieniu gry.
  - **Za każdym razem**: opóźnienie występuje przy każdym otwarciu ekranu oraz za każdym razem, gdy ponownie zostaną spełnione wymagania elementu.
- **Opóźnienie w sekundach**: czas oczekiwania, na przykład `1.5`.

Zmiana rozmiaru okna nie uruchamia opóźnienia ponownie.

## Opóźnienie zniknięcia

Kliknij element prawym przyciskiem myszy, a następnie kliknij **Opóźnienie zniknięcia**. Gdy wymagania przestaną być spełnione, element pozostanie widoczny przez czas określony w polu **Opóźnienie w sekundach**, a następnie zniknie. Opcja **Opóźnienie** ma te same ustawienia co powyżej.

Na przykład pole informacyjne z wymaganiem [**Kursor nad elementem**](/conditions#is-element-hovered) dla przycisku pozostanie widoczne przez 1 sekundę po odsunięciu kursora od przycisku.

# Stopniowe pojawianie się i znikanie

Kliknij element prawym przyciskiem myszy, a następnie kliknij **Stopniowe pojawianie się/znikanie**:

- **Pojawianie się** i **Znikanie**:
  - **Bez efektu**: element pojawia się lub znika od razu.
  - **Tylko raz**: efekt występuje tylko za pierwszym razem po uruchomieniu gry.
  - **Za każdym razem**: efekt występuje za każdym razem.
- **Szybkość pojawiania się** i **Szybkość znikania**: przy wartości `1` efekt trwa 2,5 sekundy. Wartość `2` oznacza dwukrotnie większą szybkość.

Elementy pojawiają się stopniowo po otwarciu ekranu oraz po spełnieniu ich wymagań. Jeśli ustawiono **Opóźnienie pojawienia się**, efekt rozpoczyna się po upływie opóźnienia.

Efekt znikania występuje tylko wtedy, gdy wymagania powodują ukrycie elementu, a nie przy zamknięciu ekranu.

# Przezroczystość

Kliknij element prawym przyciskiem myszy, a następnie kliknij **Przezroczystość**: `1.0` oznacza pełną widoczność, `0.5` — półprzezroczystość, a `0.0` — całkowitą niewidoczność. Większość elementów ma to ustawienie.

Wartość przezroczystości obsługuje [symbole zastępcze](/placeholders) i [zmienne](/variables), na przykład `$$panel_opacity`. Efekt stopniowego pojawiania się kończy się na poziomie przezroczystości ustawionym dla elementu.

# Przełączanie widoczności elementów przyciskiem

Przycisk może pokazywać i ukrywać elementy, tak jak panel z zasadami na powyższym GIF-ie. [Zmienna](/variables) zapamiętuje, czy panel jest widoczny.

1. Kliknij panel prawym przyciskiem myszy, a następnie kliknij **Wymagania wyświetlania**. Dodaj wymaganie [**Czy wartość zmiennej jest równa (zmienna FM)**](/conditions#is-variable-value-fm-variable) ze zmienną `show_rules` i wartością `true`.
2. Kliknij przycisk prawym przyciskiem myszy, a następnie kliknij **Edytuj skrypt akcji**.
3. Kliknij prawym przyciskiem myszy obszar skryptu i kliknij **Dodaj instrukcję IF**. Ustaw dla niej takie samo wymaganie jak dla panelu.
4. Wewnątrz instrukcji IF dodaj działanie [**Ustaw wartość zmiennej (zmienna FM)**](/action-scripts#set-variable-value-fm-variable) z następującą wartością:

   ```
   show_rules:false
   ```

5. Kliknij instrukcję IF prawym przyciskiem myszy i kliknij **Dodaj instrukcję ELSE**. Wewnątrz instrukcji ELSE dodaj działanie **Ustaw wartość zmiennej (zmienna FM)** z następującą wartością:

   ```
   show_rules:true
   ```

Każde kliknięcie przełącza więc wartość zmiennej: widoczne panele zostają ukryte, a ukryte — pokazane. Wszystkie elementy z tym samym wymaganiem będą pokazywane i ukrywane jednocześnie. Aby uzyskać płynny efekt, ustaw opcje **Pojawianie się** i **Znikanie** panelu na **Za każdym razem**.

Więcej informacji o instrukcjach IF i ELSE znajdziesz w sekcji [Skrypty akcji](/action-scripts#if-else-if-and-else).

> [!NOTE]
> Zmienne zachowują swoje wartości po zamknięciu gry, więc panel pozostanie otwarty po jej ponownym uruchomieniu. Aby zamykał się przy każdym uruchomieniu, kliknij zmienną prawym przyciskiem myszy w sekcji **Zarządzaj zmiennymi** i włącz opcję **Wyczyść zmienną przy uruchomieniu gry**.

## Przełączanie między wersjami

Przycisk może również przełączać się między więcej niż dwiema wersjami, na przykład trzema tłami:

1. Wybierz **pasek menu -> Dostosowywanie -> Zarządzaj zmiennymi** i dodaj zmienną tekstową `background` o wartości `0`.
2. Ustaw dla trzech [elementów Obraz](/elements#image) wymaganie **Czy wartość zmiennej jest równa (zmienna FM)** dla zmiennej `background`, z wartościami `0`, `1` i `2`.
3. Ustaw dla przycisku działanie **Ustaw wartość zmiennej (zmienna FM)** z następującą wartością. Zwiększa ona wartość od `0` do `1` i `2`, a następnie ponownie zaczyna od `0`:

   ```
   background:{"placeholder":"calc","values":{"decimal":"false","expression":"({"placeholder":"getvariable","values":{"name":"background"}} + 1) % 3"}}
   ```

Aby dodać więcej wersji, zmień końcową wartość `3`. Wyjaśnienie działania obliczeń znajdziesz w sekcji [**Kalkulator**](/placeholders#calculator).

# Włączanie i wyłączanie układów

Aby pokazać lub ukryć cały układ:

- Opcja **Wymagania wyświetlania [dla całego układu]** w menu kontekstowym tła edytora działa tak samo jak wymagania elementów. Zobacz [Wymagania dla całego układu](/conditions#layout-wide-requirements).
- Działania [**Przełącz układ**](/action-scripts#toggle-layout), [**Włącz układ**](/action-scripts#enable-layout) i [**Wyłącz układ**](/action-scripts#disable-layout) włączają i wyłączają układ na podstawie jego nazwy.

Umieść przycisk w innym układzie niż ten, który ma wyłączać. W przeciwnym razie przycisk zniknie razem z nim i nie będzie można ponownie włączyć układu.
