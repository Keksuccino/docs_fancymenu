---
title: Animator elementu
description: >-
  Jak animować elementy za pomocą klatek kluczowych przy użyciu Animatora
  elementu.
---

# Animator elementu

**Animator** to element, który pozwala animować inne elementy. Za jego pomocą możesz płynnie zmieniać rozmiar, położenie i punkt zakotwiczenia innego elementu w czasie, używając klatek kluczowych. Klatki kluczowe są jak migawki, które zapisują, jak element powinien wyglądać w konkretnym momencie. Następnie element Animator odtwarza te migawki po kolei, aby stworzyć płynny ruch.

> [!WARNING]
> **Animator elementu** pozwala kontrolować **pozycję, rozmiar i punkt zakotwiczenia** elementów. **NIE** można kontrolować żadnych innych ustawień elementów, takich jak przezroczystość, widoczność, obrót itp.!

# Samouczek wideo

Ponieważ wielu z was miało pewne trudności ze zrozumieniem, jak działa animator, przygotowałem krótki film pokazujący, jak z niego korzystać.

[FancyMenu | How to Use the Element Editor - YouTube](https://www.youtube.com/watch?v=F9S8cIPssww) (youtu.be/F9S8cIPssww)

<a href="https://www.youtube.com/watch?v=F9S8cIPssww" target="_blank" rel="noopener noreferrer">
  <img width="636" alt="Screenshot_2" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/element_animator_video_thumbnail.png" />
</a>

# Dodawanie elementu Animator

1. **Kliknij prawym przyciskiem myszy tło:**  
   W edytorze układu kliknij prawym przyciskiem myszy tło.

2. **Wybierz Nowy element -> Animator elementu:**  
   W menu, które się pojawi, przejdź do **Nowy element** i kliknij **Animator elementu**. To doda element Animator do twojego układu.

3. **Skonfiguruj go:**  
   Po dodaniu element Animator pojawi się z domyślnymi ustawieniami. Możesz zmienić opcje, takie jak pętla lub kolor, klikając Animatora prawym przyciskiem myszy i wybierając odpowiednią opcję z menu.

# Zarządzanie klatkami kluczowymi

Klatki kluczowe są jak zakładki, które mówią Animatorowi, jak element ma wyglądać w danym momencie.

## Otwieranie edytora klatek kluczowych

- **Otwórz edytor:**  
  Kliknij prawym przyciskiem myszy element Animator i wybierz **Edytuj klatki kluczowe** (lub **Zarządzaj klatkami kluczowymi**). Otworzy się ekran, na którym możesz dodawać, edytować i usuwać klatki kluczowe.

## Nagrywanie i dodawanie klatek kluczowych

- **Rozpocznij nagrywanie:**  
  W edytorze klatek kluczowych naciśnij klawisz **`R`**, aby rozpocząć nagrywanie. Podczas nagrywania pole podglądu zmienia kolor, aby pokazać, że jest aktywne.
  
- **Zmień podgląd:**  
  Przesuń lub zmień rozmiar pola podglądu, aby ustawić żądany wygląd. W trybie offsetu podgląd pozostaje wyśrodkowany na krzyżyku, dzięki czemu zmiany są pokazywane jako przesunięcia.
  
- **Dodaj klatkę kluczową:**  
  Naciśnij klawisz **`K`**, aby zapisać bieżący wygląd jako klatkę kluczową. Ta klatka zapisuje pozycję, rozmiar i ustawienia kotwiczenia podglądu.

## Edytowanie klatek kluczowych

- **Zaznacz klatkę kluczową:**  
  Kliknij znacznik klatki kluczowej na osi czasu. Możesz też przytrzymać **Ctrl** i klikać, aby zaznaczyć więcej niż jedną.
  
- **Przesuń klatkę kluczową:**  
  Przeciągnij znacznik klatki kluczowej w lewo lub w prawo, aby zmienić jej czas. Możesz też użyć:
  - **Strzałka w lewo:** przesuwa ją 100 ms wcześniej.
  - **Strzałka w prawo:** przesuwa ją 100 ms później.
  
- **Dopasuj podgląd:**  
  Gdy klatka kluczowa jest zaznaczona, dostosuj pole podglądu, przesuwając je lub zmieniając jego rozmiar. W razie potrzeby użyj **Ctrl + Z**, aby cofnąć, oraz **Ctrl + Y**, aby ponowić zmiany.

## Usuwanie klatek kluczowych

- **Usuń klatkę kluczową:**  
  Zaznacz klatkę kluczową i naciśnij klawisz **Delete**, aby ją usunąć.
  
- **Usuń wiele klatek kluczowych:**  
  Możesz zaznaczyć kilka klatek kluczowych (na przykład używając **Ctrl + A**, aby zaznaczyć wszystkie) i nacisnąć Delete, aby usunąć je wszystkie.

## Wygładzanie klatek kluczowych

Wygładzanie klatek kluczowych to funkcja, która pomaga równomiernie rozmieścić klatki kluczowe. Dzięki temu animacja wygląda bardziej spójnie i płynnie.

- **Zaznacz wiele klatek kluczowych:**  
  Najpierw zaznacz dwie lub więcej klatek kluczowych, które chcesz wygładzić (użyj **Ctrl + kliknięcie** lub **Ctrl + A**).

- **Kliknij przycisk wygładzania:**  
  Na dolnym pasku narzędzi edytora klatek kluczowych kliknij przycisk **Distance Smoothing**.

- **Wprowadź nową odległość:**  
  Pojawi się małe pole wprowadzania. Wpisz wartość (w milisekundach), aby ustawić taki sam odstęp czasu między każdą zaznaczoną klatką kluczową.

- **Zastosuj wygładzanie:**  
  Naciśnij Enter, aby zastosować wygładzanie. Klatki kluczowe zostaną dostosowane tak, aby różnica czasu między nimi była równa.

# Podgląd animacji

Po nagraniu klatek kluczowych możesz zobaczyć, jak będzie wyglądać twoja animacja:

- **Odtwórz animację:**  
  W edytorze klatek kluczowych naciśnij klawisz **`P`** lub kliknij przycisk odtwarzania. Podgląd rozpocznie się od początku i pokaże, jak pole podglądu zmienia się w czasie.
  
- **Uwaga dotycząca pętli:**  
  Podczas podglądu w edytorze klatek kluczowych animacja **nie będzie się zapętlać**. Oznacza to, że zostanie odtworzona tylko raz, od początku do końca. Pętla będzie aktywna dopiero wtedy, gdy element Animator zostanie zastosowany do elementu docelowego w finalnym układzie.
  
- **Wstrzymaj podgląd:**  
  Naciśnij ponownie klawisz **`P`**, aby wstrzymać animację, jeśli chcesz zatrzymać się w określonym miejscu.
  
- **Przeciągnij pasek postępu:**  
  Jeśli jest dostępny, możesz przeciągnąć znacznik osi czasu, aby sprawdzić, jak animacja wygląda w dowolnym momencie.

# Wybieranie elementów docelowych

Po skonfigurowaniu klatek kluczowych musisz wybrać, które elementy układu będą animowane:

1. **Otwórz menedżera celów:**  
   Kliknij prawym przyciskiem myszy element Animator i wybierz **Zarządzaj celami**.
  
2. **Dodaj cele:**  
   Kliknij **Dodaj cel**, aby wyświetlić listę dostępnych elementów. Wybierz te, które chcesz animować.
  
3. **Usuń cele:**  
   Aby usunąć cel, otwórz menedżera i kliknij **Usuń cel**.

Gdy animacja jest odtwarzana w finalnym układzie, Animator użyje twoich klatek kluczowych do zmiany rozmiaru, położenia i innych właściwości wybranych elementów. Jeśli ustawisz pętlę, zostanie ona tutaj zastosowana.

# Skróty klawiaturowe

Używaj tych skrótów w edytorze klatek kluczowych, aby pracować szybciej:

- **Klawisz `R`:** Rozpocznij lub zatrzymaj nagrywanie.
- **Klawisz `T`:** Wstrzymaj lub wznow nagrywanie.
- **Klawisz `P`:** Odtwórz lub wstrzymaj podgląd animacji.
- **Klawisz `K`:** Dodaj nową klatkę kluczową w bieżącym czasie.
- **Klawisze Strzałka w lewo/w prawo:**  
  - **Strzałka w lewo:** Przesuwa klatkę kluczową 100 ms wcześniej.
  - **Strzałka w prawo:** Przesuwa klatkę kluczową 100 ms później.
- **Klawisz Delete:** Usuń zaznaczoną klatkę / zaznaczone klatki kluczowe.
- **Ctrl + A:** Zaznacz wszystkie klatki kluczowe.
- **Ctrl + Z:** Cofnij ostatnią zmianę.
- **Ctrl + Y:** Ponów zmianę, którą właśnie cofnięto.
- **Ctrl + przeciąganie klatek kluczowych**: Przeciągnij jednocześnie wiele zaznaczonych klatek kluczowych.

# Dodatkowe ustawienia i wskazówki

- **Pętla animacji:**  
  Możesz ustawić Animatora tak, aby działał w pętli. Gdy pętla jest włączona, animacja uruchomi się ponownie po ostatniej klatce kluczowej — pamiętaj jednak, że dzieje się to tylko dla finalnego elementu docelowego. W podglądzie edytora klatek kluczowych pętla nie jest odtwarzana.
  
- **Ignoruj rozmiar/pozycję:**  
  Jeśli nie chcesz, aby klatki kluczowe zmieniały rozmiar lub położenie elementu, wyłącz te opcje.

- **Przesunięcia czasowe:**
  Możesz ustawić przesunięcia czasowe dla poszczególnych elementów docelowych albo użyć losowych przesunięć w skonfigurowanym zakresie, dzięki czemu jedna animacja zaczyna się o różnych porach dla każdego celu.
  
- **Tryb offsetu:**  
  W trybie offsetu animacje są stosowane jako zmiany względem pierwotnego położenia elementu. Podgląd jest wyśrodkowany na krzyżyku.
  
- **Cofanie i ponawianie:**  
  Użyj **Ctrl + Z**, aby cofnąć zmiany, oraz **Ctrl + Y**, aby je ponowić.
  
- **Sprawdź kolejność:**  
  Upewnij się, że twoje klatki kluczowe są ułożone w prawidłowej kolejności czasowej. System sam je sortuje, ale jeśli przesuniesz którąś z nich, warto ponownie sprawdzić kolejność.
  
- **Sprawdź podgląd zmian:**  
  Użyj przycisku odtwarzania lub klawisza **`P`**, aby zobaczyć swoją animację w działaniu przed zapisaniem.
