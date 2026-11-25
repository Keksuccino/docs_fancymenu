---
title: Pozycjonowanie elementów
description: Jak prawidłowo używać punktów zakotwiczenia.
sourceBlobSha: c6c6b53374ed720fcdc32a3a0fbc1784f202cc5a
---

# Pozycjonowanie elementów w FancyMenu

W FancyMenu położenie każdego elementu określają **punkty zakotwiczenia**. Są one potrzebne do obliczenia, gdzie element powinien pojawić się na ekranie. Dzięki nim elementy nie nachodzą na siebie, nie wychodzą poza ekran ani nie przesuwają się nieprawidłowo po zmianie rozmiaru okna.

## Zrozumienie punktów zakotwiczenia

Punkty zakotwiczenia wyznaczają punkt odniesienia, od którego obliczane jest położenie elementu. Domyślnie elementy dodawane do układów są powiązane z punktem zakotwiczenia **„Środek ekranu”**. Jest to dokładny środek ekranu, niezależnie od rozmiaru okna.

Na przykład, jeśli element jest oddalony o 2 centymetry od środka ekranu i jest powiązany z punktem zakotwiczenia **„Środek ekranu”**, zachowa tę odległość niezależnie od zmian rozmiaru okna.

## Korzystanie z punktów zakotwiczenia

Gdy przeciągasz element w edytorze, podświetlany jest punkt zakotwiczenia, z którym jest on połączony. Domyślnie ta czynność wyświetla również wszystkie pozostałe dostępne punkty zakotwiczenia. Możesz zmienić punkt zakotwiczenia elementu, przeciągając go nad inny punkt i czekając, aż pasek postępu się zapełni.

![Ilustracja punktów zakotwiczenia](https://github.com/Keksuccino/FancyMenu/assets/35544624/25bff930-0b52-4d76-b0e9-3e1cbcf3c20e)

## Zakotwiczanie elementów względem innych elementów

Jako punktu zakotwiczenia element może używać innego elementu. Będzie wtedy przesuwać się razem z nim, zachowując odległość od jego lewego górnego rogu. Przydaje się to w przypadku paneli złożonych z kilku elementów, etykiety obok przycisku z podstawowego interfejsu gry oraz [elementów przeciąganych](/dragger).

Można to zrobić na dwa sposoby. W obu przypadkach element pozostaje na swoim miejscu.

### Przeciąganie

1. Przeciągnij element i przytrzymaj wskaźnik nad drugim elementem.
2. Poczekaj, aż pasek się zapełni, a następnie puść.

Jeśli wskaźnik znajduje się już nad drugim elementem w chwili rozpoczęcia przeciągania, przesuń go poza ten element, a następnie z powrotem. Elementy, które od początku znajdują się pod wskaźnikiem, nie są uwzględniane.

Aby ta funkcja działała, opcje **Podświetlanie obszaru zakotwiczenia** i **Podświetlanie elementu zakotwiczenia** w menu **Okno** muszą być włączone. Obie są domyślnie włączone. Pierwsza włącza i wyłącza zakotwiczanie przez przytrzymanie, a druga dodaje inne elementy do punktów zakotwiczenia. Opcja **Czas przytrzymania obszaru/elementu zakotwiczenia (sekundy)** w tym samym menu określa, jak długo trzeba przytrzymać wskaźnik. Domyślnie są to 2 sekundy.

### Według identyfikatora

1. Kliknij prawym przyciskiem myszy drugi element, a następnie wybierz **Kopiuj identyfikator elementu**.
2. Kliknij prawym przyciskiem myszy pierwszy element i wybierz **Punkt zakotwiczenia -> Inny element**.
3. Wklej identyfikator w polu **Identyfikator elementu** i kliknij **Gotowe**.

Jeśli zaznaczono kilka elementów, wykonanie kroków 2 i 3 zakotwiczy je wszystkie jednocześnie. Więcej informacji o identyfikatorach znajdziesz w artykule [Identyfikatory elementów](/element-identifiers).

## Punkty zakotwiczenia w obszarach przewijania

Elementy w [obszarze przewijania](/scrollable-areas) również mają punkty zakotwiczenia, ale są one powiązane z zawartością obszaru, a nie z ekranem:

- **Lewy górny róg** oznacza lewy górny róg zawartości, **Środek ekranu** — jej środek, a dolne punkty zakotwiczenia są przytwierdzone do końca zawartości. Dzięki temu element może znajdować się na samym końcu długiej listy i pozostać tam, gdy lista się wydłuży.
- Elementy w obszarze mogą być zakotwiczone wyłącznie względem innych elementów z tego samego obszaru.
- Gdy przeniesiesz element do obszaru lub poza niego, elementy zakotwiczone po obu stronach jego krawędzi otrzymają punkt zakotwiczenia **Lewy górny róg** i pozostaną na swoich miejscach.

Działa to w trybie **Punkty zakotwiczenia** danego obszaru. W pozostałych trybach to obszar sam rozmieszcza elementy. Więcej informacji znajdziesz w artykule [Obszary przewijania](/scrollable-areas#anchors-mode).

## Przykład zakotwiczania elementów

Poniższy zrzut ekranu pokazuje, jak dobierać punkty zakotwiczenia elementów.

<br>
<img width="571" alt="Zrzut ekranu 2" src="https://gist.github.com/user-attachments/assets/159073e1-ab78-4086-9add-e660a1e4c93f">

Wszystkie elementy, które powinny pozostać na środku ekranu (przyciski i postać gracza), są zakotwiczone do punktu **Środek ekranu**.

Przyciski w lewym górnym rogu są zakotwiczone do punktu **Lewy górny róg**, ponieważ powinny pozostać w tym rogu.

Element tekstowy w lewym dolnym rogu jest zakotwiczony do punktu **Lewy dolny róg**, ponieważ powinien pozostać w tym rogu.

Element obrazu w prawym dolnym rogu jest zakotwiczony do punktu **Prawy dolny róg**, ponieważ powinien pozostać w tym rogu.

## Przesuwanie elementów poza ekran

Domyślnie nie można przesuwać elementów poza ekran. To zabezpieczenie przydaje się, gdy układ zostanie wczytany w bardzo małym lub nietypowym oknie — elementy pozostają wtedy widoczne i można z nimi wchodzić w interakcję.

Elementy zawsze pozostaną na ekranie, zachowując niewielki odstęp od jego krawędzi.

Możesz **wyłączyć** tę funkcję dla poszczególnych elementów, klikając je **prawym przyciskiem myszy**, a następnie wyłączając opcję **Pozostaw na ekranie**.

> [!WARNING]
> Wyłączenie tej funkcji może czasem spowodować zniknięcie elementu, ponieważ jego rzeczywiste położenie znajdowało się poza ekranem, a funkcja wymuszała jego widoczność. Jeśli tak się stanie, **cofnij** ostatnią czynność (wyłączenie opcji **Pozostaw na ekranie**) za pomocą skrótu cofania albo wybierając **pasek menu -> Edycja -> Cofnij**. Następnie ręcznie przesuń element na środek ekranu i ponownie wyłącz opcję **Pozostaw na ekranie**. Teraz element powinien pozostać widoczny mimo wyłączenia tej funkcji.

## Wyśrodkowywanie elementów

Jeśli elementy mają stały rozmiar, wyśrodkowanie ich jest proste — wystarczy zakotwiczyć je do punktu zakotwiczenia wyznaczającego środek.

Jeśli rozmiar elementu zmienia się dynamicznie zależnie od warunków lub innych czynników, sprawa jest nieco bardziej skomplikowana. FancyMenu oferuje jednak przydatną funkcję, która to ułatwia! Najpierw zakotwicz element do punktu wyznaczającego środek, a następnie kliknij go prawym przyciskiem myszy. W menu kontekstowym włącz opcję **Przyklejony punkt zakotwiczenia**. Funkcja ta zmienia sposób obliczania położenia elementu przez FancyMenu, dzięki czemu zachowuje on tę samą odległość od punktu zakotwiczenia niezależnie od zmian rozmiaru. W przypadku punktów wyznaczających środek element zawsze zachowuje tę samą odległość od punktu zakotwiczenia, mierzoną od jego geometrycznego środka. Dzięki temu pozostaje wyśrodkowany. (W przypadku punktów zakotwiczenia po lewej stronie odległość jest zawsze zachowywana względem lewej krawędzi elementu, a w przypadku punktów po prawej stronie — względem jego prawej krawędzi).

## Dodatkowe sposoby na poprawę położenia elementów

Jeśli **wszystkie punkty zakotwiczenia są ustawione prawidłowo**, ale elementy nadal nachodzą na siebie, gdy okno jest zbyt małe, układ może być po prostu zbyt rozbudowany jak na standardowy mechanizm skalowania interfejsu Minecrafta.

### Wymuszone skalowanie interfejsu

Jednym ze sposobów na poprawę położenia elementów układu jest wymuszenie skali interfejsu dla menu. W tym celu **kliknij prawym przyciskiem myszy tło edytora** i wybierz **Wymuś skalę interfejsu**. Menu będzie wtedy zawsze używać tej samej skali interfejsu, niezależnie od ustawień skali w opcjach Minecrafta.

### Automatyczne skalowanie

Ostatnim sposobem na rozwiązanie problemu nachodzących na siebie elementów jest użycie **automatycznego skalowania**.
To ustawienie automatycznie skaluje menu na podstawie rozmiaru okna, aby podczas jego zmiany jak najlepiej zachować położenie elementów. Aby włączyć automatyczne skalowanie, **kliknij prawym przyciskiem myszy tło edytora**, a następnie wybierz **Automatyczne skalowanie**.

> [!WARNING]
> **Automatyczne skalowanie** może sprawić, że tekst renderowany przez Minecrafta będzie **wyglądał nieprawidłowo**. To nie jest błąd — tak po prostu działa renderowanie tekstu w Minecrafcie. W przypadku przycisków można temu zaradzić, umieszczając etykietę przycisku w teksturze jego tła i ustawiając pustą etykietę zwykłego przycisku.
