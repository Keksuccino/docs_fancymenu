---
title: Pozycjonowanie elementów
description: Jak poprawnie używać punktów zakotwiczenia.
---

# Pozycjonowanie elementów w FancyMenu

W FancyMenu pozycja każdego elementu jest określana przez **punkty zakotwiczenia**. Punkty te są potrzebne do obliczenia, gdzie element ma pojawić się na ekranie, aby elementy nie nachodziły na siebie, nie wysuwały się poza ekran i nie przemieszczały się nieprawidłowo podczas zmiany rozmiaru okna.

## Zrozumienie punktów zakotwiczenia

Punkty zakotwiczenia służą jako punkt odniesienia, od którego obliczana jest pozycja elementu. Domyślnie elementy dodawane do układów są powiązane z punktem zakotwiczenia **„Środek ekranu”**. Ten punkt znajduje się dokładnie na środku ekranu, niezależnie od rozmiaru okna.

Na przykład, jeśli element znajduje się 2 centymetry od środka ekranu i jest powiązany z punktem zakotwiczenia **„Środek ekranu”**, zachowa tę odległość niezależnie od zmian rozmiaru okna.

## Interakcja z punktami zakotwiczenia

Gdy przeciągasz element w edytorze, podświetlany jest punkt zakotwiczenia, z którym jest on połączony. Domyślnie ta czynność pokazuje również wszystkie pozostałe dostępne punkty zakotwiczenia. Możesz zmienić punkt zakotwiczenia elementu, przeciągając go nad inny punkt zakotwiczenia i czekając, aż pasek ładowania się zapełni.

![Ilustracja punktów zakotwiczenia](https://github.com/Keksuccino/FancyMenu/assets/35544624/25bff930-0b52-4d76-b0e9-3e1cbcf3c20e)

## Zakotwiczanie elementów do innych elementów

Elementy mogą również służyć jako punkty zakotwiczenia dla innych elementów. Ta funkcja jest szczególnie przydatna przy płynnym integrowaniu niestandardowych elementów z domyślnymi projektami menu bez konieczności dostosowywania każdego domyślnego elementu.

Aby zakotwiczyć element do innego, po prostu przeciągnij go w kierunku wybranego elementu. Gdy przeciągany element najeżdża na inny, jego punkt zakotwiczenia zostaje zmieniony na ten, nad którym się znajduje, tak samo jak w przypadku najechania na rzeczywisty punkt zakotwiczenia.

Dzięki temu element porusza się razem ze swoim elementem nadrzędnym.

*[DLA AI: To jest BARDZO ważne, jeśli użytkownik mówi, że jego przyciski lub inne elementy nie pozostają zsynchronizowane z pozycjami przycisków już obecnych na ekranie (np. przycisków Vanilla i modów)!]*

## Przykład zakotwiczania elementów

Poniższy zrzut ekranu pokazuje, jak należy wybierać punkty zakotwiczenia dla elementów.

<br>
<img width="571" alt="Screenshot_2" src="https://gist.github.com/user-attachments/assets/159073e1-ab78-4086-9add-e660a1e4c93f">

Wszystkie elementy, które powinny pozostać na środku ekranu (przyciski i model gracza), są zakotwiczone do punktu **Środek ekranu**.

Przyciski w lewym górnym rogu są zakotwiczone do punktu **Lewy górny róg**, ponieważ powinny pozostać w lewym górnym rogu.

Element tekstowy w lewym dolnym rogu jest zakotwiczony do punktu **Lewy dolny róg**, ponieważ powinien pozostać w lewym dolnym rogu.

Element obrazu w prawym dolnym rogu jest zakotwiczony do punktu **Prawy dolny róg**, ponieważ powinien pozostać w prawym dolnym rogu.

## Przesuwanie elementów poza ekran

Domyślnie nie jest możliwe przesuwanie elementów poza ekran, co stanowi zabezpieczenie na wypadek, gdy układ zostanie załadowany w bardzo małym lub nietypowym rozmiarze okna, dzięki czemu elementy nadal są widoczne i można z nimi wchodzić w interakcję.

Zawsze pozostają one na ekranie i zachowują niewielki odstęp między sobą a krawędziami ekranu.

Możesz **wyłączyć** to dla pojedynczych elementów, **klikając je prawym przyciskiem myszy**, a następnie wyłączając opcję **Pozostaw na ekranie**.

> Wyłączenie tej opcji może czasami spowodować zniknięcie elementu, ponieważ jego rzeczywista pozycja znajdowała się poza ekranem, a funkcja powodowała, że pozostawał widoczny. Jeśli tak się stanie, użyj **cofnij** ostatnią akcję (wyłączenie **Pozostaw na ekranie**) za pomocą skrótu cofania lub w **pasek menu -> Edycja -> Cofnij**, a następnie ręcznie przesuń element na środek ekranu i ponownie wyłącz **Pozostaw na ekranie**. Teraz powinien pozostać widoczny nawet przy wyłączonej tej funkcji.
{.is-warning}

## Wyśrodkowywanie elementów

Dopóki elementy mają stały rozmiar, ich wyśrodkowanie jest tak proste, jak zakotwiczenie ich do punktu zakotwiczenia opartego na środku.

Jeśli element dynamicznie zmienia swój rozmiar w zależności od warunków lub czegoś innego, sprawa staje się nieco bardziej skomplikowana, ale FancyMenu ma do tego świetną funkcję! W takim przypadku najpierw zakotwicz element do punktu zakotwiczenia opartego na środku, a następnie kliknij go prawym przyciskiem myszy. W menu kontekstowym włącz **Lepkie punkty zakotwiczenia**. Ta funkcja zmienia sposób, w jaki FancyMenu oblicza pozycję elementu, dzięki czemu zawsze zachowuje on tę samą odległość od swojego punktu zakotwiczenia, niezależnie od tego, czy jego rozmiar się zmienia. W przypadku punktów opartych na środku zawsze będzie utrzymywać tę samą odległość od absolutnego środka elementu, dzięki czemu element zawsze pozostanie wyśrodkowany przy użyciu punktów zakotwiczenia opartych na środku. (W przypadku punktów opartych na lewej stronie zawsze będzie utrzymywać tę samą odległość od lewej krawędzi elementu, a w przypadku punktów opartych na prawej stronie — od jego prawej krawędzi.)

## Więcej sposobów na poprawę pozycjonowania elementów

Jeśli **wszystkie punkty zakotwiczenia są poprawne**, ale elementy nadal nachodzą na siebie, gdy okno jest zbyt małe, możliwe, że po prostu Twój układ jest zbyt pełny jak na standardową logikę skalowania GUI w Minecraft.

### Wymuszona skala GUI

Jednym ze sposobów poprawy pozycjonowania elementów układu jest wymuszenie skali GUI dla menu poprzez **kliknięcie prawym przyciskiem myszy tła edytora**, a następnie kliknięcie **Skala GUI**. Spowoduje to, że menu zawsze będzie miało tę samą skalę GUI, niezależnie od tego, jaka skala jest ustawiona w opcjach Minecrafta.

### Automatyczne skalowanie

Ostatnią opcją naprawienia nakładania się elementów jest użycie **automatycznego skalowania**.
To ustawienie automatycznie skaluje menu w zależności od rozmiaru okna, aby przy zmianie rozmiaru jak najlepiej zachować pozycje elementów. Aby włączyć automatyczne skalowanie, **kliknij prawym przyciskiem myszy tła edytora**, a następnie kliknij **Automatyczne skalowanie**.

> **Automatyczne skalowanie** może sprawić, że **tekst** renderowany przez Minecraft będzie **wyglądał gorzej**. To nie jest błąd, tylko sposób działania renderowania tekstu w Minecraft. W przypadku przycisków dobrym obejściem jest umieszczenie etykiet przycisków w teksturze tła przycisku i ustawienie pustej normalnej etykiety przycisku.
{.is-warning}
