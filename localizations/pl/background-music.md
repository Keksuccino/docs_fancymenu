---
title: Muzyka w tle menu
description: Jak dostosować muzykę odtwarzaną w menu.
---

# Muzyka w tle menu

Możesz zastąpić domyślną muzykę tła menu Minecrafta własnymi utworami albo po prostu wyłączyć normalną muzykę Vanilla, która odtwarza się w menu.

# Wyłączanie muzyki Vanilla

FancyMenu oferuje kilka sposobów na wyłączenie muzyki Vanilla w menu. Może to być przydatne, jeśli planujesz odtwarzać inne ścieżki audio na ekranach albo po prostu nie chcesz, aby w niektórych ekranach w ogóle grała muzyka.

## Globalnie

Jeśli chcesz, aby w menu nie było żadnej muzyki, to jest najprostszy sposób.

Aby globalnie wyłączyć lub zastąpić muzykę Vanilla w menu w FancyMenu 3.9.0+, przejdź do paska menu FancyMenu u góry ekranu i kliknij **Dostosowanie -> Globalne dostosowania**. Globalne dostosowania mogą zastąpić muzykę menu bez wymagania paczki zasobów i bez włączania dostosowań dla każdego ekranu.

<br>
<img width="600" alt="Screenshot_3" src="https://gist.github.com/assets/35544624/d829a35e-f23f-42a9-ad79-193de73b499b">

> Wyłączenie domyślnej muzyki Minecrafta spowoduje jej wyłączenie na każdym ekranie, a nie tylko na bieżącym.
{.is-info}

## Dla konkretnego ekranu

Jeśli chcesz mieć większą kontrolę nad tym, gdzie ma odtwarzać się muzyka Vanilla w menu, powinieneś użyć elementu **Music Controller**. Ten element dodaje się do układów tak jak każdy inny element, klikając **prawym przyciskiem myszy na tło edytora**, a następnie wybierając **New Element -> Music Controller**.

Klikając **prawym przyciskiem myszy** element, możesz dostosować, jakie rodzaje muzyki odtwarzanej w menu mają być wyłączone (zwykła muzyka menu oraz muzyka świata, która nadal gra na ekranach niepauzujących gry, takich jak ekran ekwipunku).

> Ten element obsługuje **wymagania ładowania**, więc masz jeszcze większą kontrolę nad tym, kiedy ma grać muzyka Vanilla!
{.is-info}


# Dodawanie własnej muzyki

Teraz możemy dodać właściwą własną muzykę w tle.

Jeśli chcesz odtwarzać tę samą własną muzykę na wszystkich ekranach i potrzebujesz kontroli na poziomie układu, powinieneś użyć **układu uniwersalnego**, który ładuje się na każdym ekranie, na którym włączono dostosowania. Do prostego globalnego zastąpienia muzyki menu użyj zamiast tego [Globalnych dostosowań](/global-customizations).

Podczas korzystania z układu uniwersalnego muzyka będzie **kontynuować odtwarzanie** podczas przechodzenia z jednego menu z włączonym tym układem do innego menu z tym samym włączonym układem.

Jeśli chcesz odtwarzać inną muzykę dla każdego ekranu, użyj zwykłych układów.

W tym przykładzie użyjemy **układów uniwersalnych**.

Dodaj nowy element **Audio** do układu uniwersalnego, który będzie pełnił rolę odtwarzacza muzyki w tle.

<br>
<img width="400" alt="Screenshot_2" src="https://gist.github.com/assets/35544624/bddf8f46-47c5-4a00-a6f7-b5ca1df8ae67">

Teraz dodaj do niego utwory, które mają być odtwarzane w tle.

<br>
<img width="300" alt="Screenshot_4" src="https://gist.github.com/assets/35544624/824dcb90-3bd5-4c0b-96d0-e581a7c2f9f7">

To w zasadzie wszystko.
W razie potrzeby możesz też ustawić element Audio w tryb losowego odtwarzania i zmienić jego kanał dźwięku.

Zapisz układ i wyjdź z edytora.

# Włączanie dostosowań dla wszystkich menu

W tym przykładzie użyliśmy **układu uniwersalnego**, ponieważ chcemy, aby nasza muzyka w tle odtwarzała się na wielu ekranach.

Ponieważ układy ładują się tylko na ekranach, na których włączono **dostosowania**, musimy teraz włączyć je dla każdego ekranu, na którym ma grać muzyka.

Aby to zrobić, kliknij **Dostosowanie** i włącz **Dostosowanie bieżącego ekranu**.

<br>
<img width="320" alt="Screenshot_5" src="https://gist.github.com/assets/35544624/2f6527b7-ae14-4e82-abc6-3572cc6490b2">

Powtórz to dla każdego ekranu, na którym ma odtwarzać się twoja własna muzyka w tle.

I to wszystko! Teraz masz własną muzykę w tle w menu Minecrafta!
