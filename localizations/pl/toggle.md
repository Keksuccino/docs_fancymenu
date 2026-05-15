---
title: Przełączanie elementów układów
description: Jak przełączać elementy układów na podstawie danych wejściowych użytkownika.
---

# Przełączanie elementów układów

Czasem dobrze mieć wybór! Może niektórzy użytkownicy nie lubią ciągle słyszeć Ricka Astleya jako muzyki w menu albo chcą mieć inny, uroczy obrazek anime jako tło menu.

Żaden problem! Możesz sprawić, aby użytkownicy mogli włączać i wyłączać poszczególne elementy układów albo przełączać się między wieloma wersjami tych elementów.

# Włączanie i wyłączanie

Aby na przykład przełączać widoczność elementu po kliknięciu przycisku, potrzebujesz zmiennej ustawianej po kliknięciu przycisku, a element, który chcesz przełączać, musi sprawdzać w swoich wymaganiach ładowania, czy ta zmienna ma odpowiednią wartość.

## Zmienna

Pierwszym krokiem jest utworzenie zmiennej, której użyjesz do przechowywania stanu widoczności elementu, który chcesz przełączać.

Aby dodać nową zmienną, przejdź do zakładki **Customization** na pasku menu i kliknij **Variables -> Manage Variables**, a następnie dodaj nową zmienną z **unikalną** nazwą! Upewnij się, że używasz naprawdę **unikalnej** nazwy, której nigdzie wcześniej nie użyto.

Po utworzeniu zmiennej ustaw jej wartość na `true`.

<br>
<img width="494" alt="Screenshot_9" src="https://gist.github.com/assets/35544624/1e29be13-e601-4669-8fa2-d78db945b07f">

## Element

Następny krok to dodanie elementu, który chcesz włączać i wyłączać.

<br>
<img width="270" alt="Screenshot_3" src="https://gist.github.com/assets/35544624/317460fc-310b-4941-ab9a-b56490c5ebb9">

Teraz kliknij element prawym przyciskiem myszy i wybierz **Loading Requirements**.
To otworzy ekran Manage Requirements. Kliknij **Add Requirement**.

Wyszukaj wymaganie **Is Variable Value**, zaznacz je i kliknij **Edit Requirement Value**.

<br>
<img width="501" alt="Screenshot_1" src="https://gist.github.com/assets/35544624/d0d342f5-617c-415e-b6f7-05087fc204b7">

Teraz wpisz nazwę zmiennej utworzonej wcześniej i ustaw, aby wymaganie sprawdzało wartość `true`.

<br>
<img width="500" alt="Screenshot_2" src="https://gist.github.com/assets/35544624/a1f356e9-7f96-4d8b-87b0-51f05898409a">

To wszystko w tej części. Teraz element będzie widoczny, gdy wartość zmiennej będzie równa `true`.

## Przycisk

Teraz musimy dodać nowy element Button.

<br>
<img width="270" alt="Screenshot_4" src="https://gist.github.com/assets/35544624/1bd1b781-0cdb-4b52-80a0-db8f44ead0db">

Po dodaniu kliknij go prawym przyciskiem myszy i wybierz **Edit Action Script**.
To otworzy ekran Manage Action Script dla przycisku.

Kliknij **Add IF Statement**, dodaj do niego wymaganie **Is Variable Value** i ustaw tryb wymagania na **OPPOSITE**.

<br>
<img width="520" alt="Screenshot_5" src="https://gist.github.com/assets/35544624/a024ea21-2244-4ca6-b44b-1a80f7936b8f">

Teraz kliknij **Edit Requirement Value**, tak jak zrobiłeś to wcześniej dla elementu, i wpisz dokładnie tę samą nazwę zmiennej oraz wartość, którą ma sprawdzać.

<br>
<img width="500" alt="Screenshot_2" src="https://gist.github.com/assets/35544624/a1f356e9-7f96-4d8b-87b0-51f05898409a">

Ponieważ ustawiliśmy tryb wymagania na **OPPOSITE**, teraz będzie sprawdzane, czy wartość zmiennej NIE wynosi `true`, a właśnie tego chcemy.

Po powrocie do ekranu Edit Action Script zobaczysz teraz właśnie dodany przez nas IF statement.

<br>
<img width="495" alt="Screenshot_6" src="https://gist.github.com/assets/35544624/6ac8444c-ca15-43ff-a633-df63e76e7433">

Teraz kliknij **Add Action**, wyszukaj akcję **Set Variable Value**, wybierz ją, a następnie kliknij **Edit Action Value**.

<br>
<img width="494" alt="Screenshot_7" src="https://gist.github.com/assets/35544624/8568e539-b4d0-49bd-89c4-4659ee71754c">

Jako wartość akcji wpisz najpierw nazwę swojej zmiennej, a potem wartość, na jaką chcesz ją ustawić. Oddziel nazwę i wartość znakiem `:`.
W tym przypadku chcemy ustawić wartość na `true`, ponieważ ta akcja zostanie później wykonana, gdy wartość NIE wynosi `true`.

<br>
<img width="496" alt="Screenshot_8" src="https://gist.github.com/assets/35544624/fab440ad-b335-4751-9651-4bb0b65bc968">

Teraz dołącz akcję do IF statement, przeciągając ją nad IF statement, aby była wykonywana tylko wtedy, gdy wartość naszej zmiennej NIE wynosi `true`.

<br>
<img width="496" alt="Screenshot_8" src="https://gist.github.com/assets/35544624/d1ac3ea9-44d7-4ad6-a4b2-455b21f6d1c4">

Po tym zaznacz IF statement, a następnie kliknij **Append ELSE Statement**.

Teraz dodaj kolejną akcję **Set Variable Value**, ale zamiast ustawiać wartość zmiennej na `true`, ustaw ją na `false`.

<br>
<img width="494" alt="Screenshot_9" src="https://gist.github.com/assets/35544624/d05400dc-b9b7-4c1a-8657-9e34939ed599">

Teraz dołącz drugą akcję do ELSE statement, aby była wykonywana, jeśli wartość zmiennej WYNOSI `true`.

<br>
<img width="494" alt="Screenshot_9" src="https://gist.github.com/assets/35544624/3191a1cc-c5c2-4cf1-a620-23bdbe639bf2">

I to wszystko! Na początku może wydawać się, że to dużo kroków, ale gdy już się do tego przyzwyczaisz, jest to naprawdę proste i szybkie.

Teraz możesz zapisać swój układ, wyjść z edytora i nacisnąć przycisk, aby sprawdzić, czy działa!

<br>
<img width="494" alt="Screenshot_9" src="https://gist.github.com/assets/35544624/e9a87aca-ba0f-4ce6-a39e-1e1d3796c9e3">

Możesz też użyć tej samej zmiennej dla innych elementów, aby **przełączać wiele elementów naraz** po naciśnięciu przycisku.

Możesz nawet przełączać całe układy, używając **Layout-Wide Loading Requirements**. Aby skonfigurować wymagania dla całego układu, kliknij prawym przyciskiem tło edytora. Pamiętaj tylko, aby dodać przycisk do innego układu, nie do tego, który chcesz przełączać.

# Przełączanie cykliczne

W przeciwieństwie do przełączania między dwiema wartościami, przełączanie cykliczne wymaga, aby skrypt akcji potrafił przechodzić między więcej niż dwiema wartościami.

Logika skryptu akcji jest bardzo podobna do tej używanej przy przełączaniu, więc opiszę to tutaj bardzo krótko. Koniecznie przeczytaj też część o przełączaniu.

Dodałem 3 obrazki. Pierwszy obrazek jest widoczny, gdy wartość zmiennej wynosi `1`, drugi, gdy wartość wynosi `2`, a trzeci, gdy wartość wynosi `3`.

<br>
<img width="494" alt="Screenshot_9" src="https://gist.github.com/assets/35544624/731c13cf-6f81-470b-8e1b-cba264ffbe05">

Następnie dodałem przycisk cykliczny i ustawiłem, aby przełączał wartość zmiennej z `1` na `2`, z `2` na `3` i z `3` z powrotem na `1`.

<br>
<img width="609" alt="Screenshot_1" src="https://gist.github.com/assets/35544624/9f2052b1-8d3d-4a35-884a-4a234e63d5e5">

I to wszystko. Teraz zapisz układ, wyjdź z edytora i sprawdź, czy przycisk cykliczny działa poprawnie.

<br>
<img width="494" alt="Screenshot_9" src="https://gist.github.com/assets/35544624/430c2369-a43f-4d0f-9203-3fdb1b9eae2c">
