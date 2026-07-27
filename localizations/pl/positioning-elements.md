---
title: Pozycjonowanie elementów
description: Jak poprawnie używać punktów zaczepienia.
---

# Pozycjonowanie elementów w FancyMenu

W FancyMenu pozycja każdego elementu jest określana przez **punkty zaczepienia**. Są one potrzebne do obliczania, gdzie element powinien pojawić się na ekranie, aby elementy się nie nakładały, nie wychodziły poza ekran i nie przesuwały się nieprawidłowo po zmianie rozmiaru okna.

## Zrozumienie punktów zaczepienia

Punkty zaczepienia służą jako punkt odniesienia, od którego obliczana jest pozycja elementu. Domyślnie elementy dodawane do układów są przypisane do punktu zaczepienia **„Środek ekranu”**. Ten punkt znajduje się dokładnie na środku ekranu, niezależnie od rozmiaru okna.

Na przykład, jeśli element znajduje się 2 centymetry od środka ekranu i jest przypisany do punktu **„Środek ekranu”**, zachowa tę odległość niezależnie od zmian rozmiaru okna.

## Praca z punktami zaczepienia

Gdy przeciągasz element w edytorze, podświetlany jest punkt zaczepienia, do którego jest on podłączony. Domyślnie ta akcja pokazuje również wszystkie inne dostępne punkty zaczepienia. Możesz zmienić punkt zaczepienia elementu, przeciągając go nad inny punkt i czekając, aż pasek ładowania się wypełni.

![Illustration of anchor points](https://github.com/Keksuccino/FancyMenu/assets/35544624/25bff930-0b52-4d76-b0e9-3e1cbcf3c20e)

## Przypinanie elementów do innych elementów

Elementy mogą również służyć jako punkty zaczepienia dla innych elementów. Ta funkcja jest szczególnie przydatna do płynnego integrowania własnych elementów z wyglądem menu Vanilla, bez konieczności dostosowywania każdego elementu Vanilla osobno.

Aby przypiąć element do innego, po prostu przeciągnij go w kierunku wybranego elementu. Gdy przeciągany element znajdzie się nad innym, jego punkt zaczepienia zostanie zmieniony na ten, nad którym się znajduje — tak samo jak podczas najechania na rzeczywisty punkt zaczepienia.

Dzięki temu element może poruszać się razem ze swoim nadrzędnym elementem.

## Przykład przypinania elementów

Poniższy zrzut ekranu pokazuje, jak należy wybierać punkty zaczepienia dla elementów.

<br>
<img width="571" alt="Screenshot_2" src="https://gist.github.com/user-attachments/assets/159073e1-ab78-4086-9add-e660a1e4c93f">

Wszystkie elementy, które powinny pozostawać na środku ekranu (przyciski i postać gracza), są przypięte do punktu zaczepienia **Środek ekranu**.

Przyciski w lewym górnym rogu są przypięte do punktu **Górny lewy róg**, ponieważ powinny pozostać w lewym górnym rogu.

Element tekstowy w lewym dolnym rogu jest przypięty do punktu zaczepienia **Dolny lewy róg**, ponieważ powinien pozostać w lewym dolnym rogu.

Element obrazu w prawym dolnym rogu jest przypięty do punktu zaczepienia **Dolny prawy róg**, ponieważ powinien pozostać w prawym dolnym rogu.

## Przesuwanie elementów poza ekran

Domyślnie nie można przesuwać elementów poza ekran, co działa jak zabezpieczenie na wypadek wczytania układu w bardzo małym lub nietypowym rozmiarze okna, dzięki czemu elementy nadal są widoczne i można z nimi wchodzić w interakcję.

Zawsze pozostaną na ekranie i zachowają niewielki odstęp między sobą a jego krawędziami.

Możesz **wyłączyć** to dla pojedynczych elementów, klikając je **prawym przyciskiem myszy**, a następnie wyłączając opcję **Pozostaw na ekranie**.

> [!WARNING]
> Wyłączenie tej opcji może czasami spowodować, że element zniknie, ponieważ jego rzeczywista pozycja znajdowała się poza ekranem, a funkcja sprawiała, że pozostawał widoczny. Jeśli tak się stanie, **cofnij** ostatnią akcję (wyłączenie **Pozostaw na ekranie**) za pomocą skrótu cofania lub w **pasku menu -> Edycja -> Cofnij**, a następnie ręcznie przesuń element na środek ekranu i ponownie wyłącz **Pozostaw na ekranie**. Teraz powinien pozostać widoczny nawet przy wyłączonej tej funkcji.

## Centrowanie elementów

Jeśli elementy mają stały rozmiar, ich wyśrodkowanie jest tak proste, jak przypięcie ich do punktu zaczepienia opartego na środku.

Jeśli element dynamicznie zmienia swój rozmiar w zależności od warunków lub czegoś innego, jest to nieco bardziej skomplikowane, ale FancyMenu ma do tego świetną funkcję! W takim przypadku najpierw przypnij element do punktu zaczepienia opartego na środku, a następnie kliknij go prawym przyciskiem myszy. W menu kontekstowym włącz **Sticky Anchors**. Ta funkcja zmienia sposób, w jaki FancyMenu oblicza pozycję elementu, dzięki czemu zawsze zachowuje on tę samą odległość od swojego punktu zaczepienia, niezależnie od tego, czy jego rozmiar się zmienia. W przypadku punktów zaczepienia opartych na środku zawsze będzie zachowywać tę samą odległość od punktu zaczepienia względem absolutnego środka elementu, dzięki czemu pozostanie on wyśrodkowany przy użyciu punktów zaczepienia opartych na środku. (Dla punktów opartych na lewej stronie zawsze będzie zachowywać tę samą odległość od punktu zaczepienia względem lewej strony elementu, a dla punktów opartych na prawej stronie — względem prawej strony elementu.)

## Więcej sposobów na poprawę pozycjonowania elementów

Jeśli **wszystkie punkty zaczepienia są poprawne**, ale elementy nadal nachodzą na siebie, gdy okno jest zbyt małe, możliwe, że Twój układ jest po prostu zbyt przeładowany jak na standardową logikę skalowania interfejsu Minecrafta.

### Wymuszona skala GUI

Jednym ze sposobów na poprawę pozycjonowania elementów układu jest wymuszenie skali GUI dla menu poprzez **kliknięcie prawym przyciskiem myszy tła edytora** i wybranie **Force GUI Scale**. Sprawi to, że menu zawsze będzie miało tę samą skalę GUI, niezależnie od ustawienia w opcjach Minecrafta.

### Automatyczne skalowanie

Ostatnią opcją naprawy nakładania się elementów jest użycie **automatycznego skalowania**.
To ustawienie automatycznie dopasuje skalę menu do rozmiaru okna, aby jak najlepiej zachować pozycje elementów podczas zmiany rozmiaru okna. Aby włączyć automatyczne skalowanie, **kliknij prawym przyciskiem myszy tło edytora**, a następnie kliknij **Auto-Scaling**.

> [!WARNING]
> **Automatyczne skalowanie** może sprawić, że **tekst** renderowany przez Minecrafta będzie **wyglądał źle**. To nie jest błąd, tylko sposób, w jaki działa renderowanie tekstu w Minecraftcie. W przypadku przycisków dobrym obejściem jest umieszczenie etykiet przycisków jako części tekstury tła przycisku i ustawienie pustej etykiety zwykłego przycisku.
