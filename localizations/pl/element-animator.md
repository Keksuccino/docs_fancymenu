---
title: Animator elementów
description: >-
  Jak animować elementy za pomocą klatek kluczowych przy użyciu Animatora
  elementów.
---

# Animator elementów

**Animator** to element, który pozwala animować inne elementy. Dzięki niemu możesz płynnie zmieniać rozmiar, pozycję i punkt zakotwiczenia innego elementu w czasie, używając klatek kluczowych. Klatki kluczowe są jak migawki, które zapisują, jak element powinien wyglądać w określonym momencie. Następnie element Animator odtwarza te migawki po kolei, tworząc płynny ruch.

> **Animator elementów** pozwala kontrolować **pozycję, rozmiar oraz punkt zakotwiczenia** elementów. **NIE** jest możliwe kontrolowanie żadnych innych ustawień elementów, takich jak przezroczystość, widoczność, obrót itd.!
{.is-warning}

# Samouczek wideo

Ponieważ wielu z was było trochę zdezorientowanych, jak działa animator, przygotowałem krótki film pokazujący, jak z niego korzystać.

[FancyMenu | Jak używać edytora elementów - YouTube](https://www.youtube.com/watch?v=F9S8cIPssww) (youtu.be/F9S8cIPssww)

<a href="https://www.youtube.com/watch?v=F9S8cIPssww" target="_blank" rel="noopener noreferrer">
  <img width="636" alt="Screenshot_2" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/element_animator_video_thumbnail.png" />
</a>

# Dodawanie elementu Animatora

1. **Kliknij prawym przyciskiem myszy tło:**  
   W edytorze układu kliknij prawym przyciskiem myszy na tle.

2. **Wybierz Nowy element -> Animator elementów:**  
   W wyskakującym menu przejdź do **Nowy element** i kliknij **Animator elementów**. Doda to element Animator do twojego układu.

3. **Skonfiguruj go:**  
   Po dodaniu element Animator pojawi się z domyślnymi ustawieniami. Możesz zmienić opcje, takie jak zapętlanie czy kolor, klikając Animator prawym przyciskiem myszy i wybierając odpowiednią opcję z menu.

# Zarządzanie klatkami kluczowymi

Klatki kluczowe są jak zakładki, które mówią Animatorowi, jak element powinien wyglądać w danym momencie.

## Otwieranie edytora klatek kluczowych

- **Otwórz edytor:**  
  Kliknij prawym przyciskiem myszy element Animator i wybierz **Edytuj klatki kluczowe** (lub **Zarządzaj klatkami kluczowymi**). Otworzy się ekran, na którym możesz dodawać, edytować lub usuwać klatki kluczowe.

## Nagrywanie i dodawanie klatek kluczowych

- **Rozpocznij nagrywanie:**  
  W edytorze klatek kluczowych naciśnij klawisz **`R`**, aby rozpocząć nagrywanie. Podczas nagrywania pole podglądu zmienia kolor, aby pokazać, że tryb jest aktywny.
  
- **Zmień podgląd:**  
  Przesuń lub zmień rozmiar pola podglądu, aby ustawić pożądany wygląd. W trybie przesunięcia podgląd pozostaje wycentrowany na celowniku, dzięki czemu zmiany są pokazywane jako przesunięcia.
  
- **Dodaj klatkę kluczową:**  
  Naciśnij klawisz **`K`**, aby zapisać bieżący wygląd jako klatkę kluczową. Ta klatka zapisuje pozycję, rozmiar i ustawienia punktu zakotwiczenia podglądu.

## Edytowanie klatek kluczowych

- **Zaznacz klatkę kluczową:**  
  Kliknij znacznik klatki kluczowej na osi czasu. Możesz też przytrzymać **Ctrl** i kliknąć, aby zaznaczyć więcej niż jedną.
  
- **Przesuń klatkę kluczową:**  
  Przeciągnij znacznik klatki kluczowej w lewo lub w prawo, aby zmienić jej czas. Możesz też użyć:
  - **Strzałka w lewo:** aby przesunąć ją o 100 ms wcześniej.
  - **Strzałka w prawo:** aby przesunąć ją o 100 ms później.
  
- **Doprecyzuj podgląd:**  
  Gdy klatka kluczowa jest zaznaczona, dostosuj pole podglądu, przesuwając je lub zmieniając jego rozmiar. W razie potrzeby użyj **Ctrl + Z**, aby cofnąć, oraz **Ctrl + Y**, aby ponowić zmiany.

## Usuwanie klatek kluczowych

- **Usuń klatkę kluczową:**  
  Zaznacz klatkę kluczową i naciśnij klawisz **Delete**, aby ją usunąć.
  
- **Usuń wiele klatek kluczowych:**  
  Możesz zaznaczyć kilka klatek kluczowych (na przykład używając **Ctrl + A**, aby zaznaczyć wszystkie) i nacisnąć Delete, aby usunąć je wszystkie.

## Wygładzanie klatek kluczowych

Wygładzanie klatek kluczowych to funkcja, która pomaga równomiernie rozłożyć klatki kluczowe w czasie. Dzięki temu animacja wygląda bardziej spójnie i płynnie.

- **Zaznacz wiele klatek kluczowych:**  
  Najpierw zaznacz dwie lub więcej klatek kluczowych, które chcesz wygładzić (użyj **Ctrl + kliknięcie** lub **Ctrl + A**).

- **Kliknij przycisk wygładzania:**  
  Na dolnym pasku narzędzi edytora klatek kluczowych kliknij przycisk **Distance Smoothing**.

- **Wprowadź nowy odstęp:**  
  Pojawi się małe pole wprowadzania. Wpisz wartość (w milisekundach), aby ustawić taki sam odstęp czasu między każdą zaznaczoną klatką kluczową.

- **Zastosuj wygładzanie:**  
  Naciśnij Enter, aby zastosować wygładzanie. Klatki kluczowe zostaną dostosowane tak, aby różnica czasu między nimi była równa.

# Podgląd animacji

Po nagraniu klatek kluczowych możesz sprawdzić, jak będzie wyglądać animacja:

- **Odtwórz animację:**  
  W edytorze klatek kluczowych naciśnij klawisz **`P`** lub kliknij przycisk odtwarzania. Podgląd zacznie się od początku i pokaże, jak pole podglądu zmienia się w czasie.
  
- **Uwaga dotycząca zapętlania:**  
  Podczas podglądu w edytorze klatek kluczowych animacja **nie będzie się zapętlać**. Oznacza to, że odtwarza się tylko raz, od początku do końca. Zapętlanie będzie aktywne tylko wtedy, gdy element Animator zostanie zastosowany do docelowego elementu w finalnym układzie.
  
- **Wstrzymaj podgląd:**  
  Naciśnij ponownie klawisz **`P`**, aby wstrzymać animację, jeśli chcesz zatrzymać ją w określonym momencie.
  
- **Przeciągnij pasek postępu:**  
  Jeśli jest dostępny, możesz przeciągnąć znacznik osi czasu, aby sprawdzić, jak animacja wygląda w dowolnym momencie.

# Wybieranie elementów docelowych

Po skonfigurowaniu klatek kluczowych musisz wybrać, które elementy układu mają być animowane:

1. **Otwórz menedżera elementów docelowych:**  
   Kliknij prawym przyciskiem myszy element Animator i wybierz **Zarządzaj celami**.
  
2. **Dodaj cele:**  
   Kliknij **Dodaj cel**, aby zobaczyć listę dostępnych elementów. Wybierz te, które chcesz animować.
  
3. **Usuń cele:**  
   Aby usunąć cel, otwórz menedżera i kliknij **Usuń cel**.

Gdy animacja odtwarza się w finalnym układzie, Animator użyje twoich klatek kluczowych do zmiany rozmiaru, pozycji i innych właściwości wybranych elementów. Jeśli ustawisz zapętlanie, zostanie ono tutaj zastosowane.

# Skróty klawiaturowe

Używaj tych skrótów w edytorze klatek kluczowych, aby pracować szybciej:

- **Klawisz `R`:** Rozpocznij lub zatrzymaj nagrywanie.
- **Klawisz `T`:** Wstrzymaj lub wznow nagrywanie.
- **Klawisz `P`:** Odtwórz lub wstrzymaj podgląd animacji.
- **Klawisz `K`:** Dodaj nową klatkę kluczową w bieżącym czasie.
- **Klawisze strzałek w lewo/prawo:**  
  - **Strzałka w lewo:** Przesuń klatkę kluczową o 100 ms wcześniej.
  - **Strzałka w prawo:** Przesuń klatkę kluczową o 100 ms później.
- **Klawisz Delete:** Usuń zaznaczoną klatkę / zaznaczone klatki kluczowe.
- **Ctrl + A:** Zaznacz wszystkie klatki kluczowe.
- **Ctrl + Z:** Cofnij ostatnią zmianę.
- **Ctrl + Y:** Ponów zmianę, którą właśnie cofnąłeś.
- **Ctrl + przeciąganie klatek kluczowych**: Przeciągaj jednocześnie wiele zaznaczonych klatek kluczowych.

# Dodatkowe ustawienia i wskazówki

- **Zapętl animację:**  
  Możesz ustawić Animatora tak, aby zapętlał animację. Gdy zapętlanie jest włączone, animacja uruchomi się ponownie po ostatniej klatce kluczowej — ale pamiętaj, że dotyczy to tylko finalnego elementu docelowego. W podglądzie w edytorze klatek kluczowych zapętlanie nie występuje.
  
- **Ignoruj rozmiar/pozycję:**  
  Jeśli nie chcesz, aby klatki kluczowe zmieniały rozmiar lub pozycję elementu, wyłącz te opcje.

- **Przesunięcia czasowe:**
  FancyMenu 3.9.0 dodaje przesunięcia czasowe dla kontrolowanych elementów. Możesz ustawić przesunięcie dla pojedynczych elementów docelowych albo użyć losowych przesunięć czasowych w skonfigurowanym zakresie, dzięki czemu jedna animacja może zaczynać się dla każdego celu nieco w innym momencie.
  
- **Tryb przesunięcia:**  
  W trybie przesunięcia animacje są stosowane jako zmiany względem pierwotnego położenia elementu. Podgląd jest wyświetlany wyśrodkowany na celowniku.
  
- **Cofanie i ponawianie:**  
  Użyj **Ctrl + Z**, aby cofnąć, oraz **Ctrl + Y**, aby ponowić zmiany.
  
- **Sprawdź kolejność:**  
  Upewnij się, że twoje klatki kluczowe są ułożone we właściwej kolejności czasowej. System sortuje je automatycznie, ale jeśli przeniesiesz jedną z nich, sprawdź ponownie kolejność.
  
- **Podgląd zmian:**  
  Użyj przycisku odtwarzania lub klawisza **`P`**, aby zobaczyć animację w działaniu przed zapisaniem.

# Podsumowanie

Postępując zgodnie z tymi prostymi krokami, możesz dodać element Animator do swojego układu i tworzyć płynne animacje. Niezależnie od tego, czy rejestrujesz zmiany na żywo w podglądzie, dostosowujesz klatki kluczowe za pomocą klawiatury, wybierasz elementy do animowania, czy podglądasz animację, aby zobaczyć, jak wygląda, element Animator daje ci łatwy sposób na ożywienie własnych menu.

Miłego animowania!
