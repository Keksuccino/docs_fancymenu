---
title: Otwieranie GUI za pomocą komendy
description: Jak otwierać Vanilla i niestandardowe GUI za pomocą komendy.
---

# Otwieranie GUI za pomocą komendy

FancyMenu zawiera komendę, która pozwala otwierać Vanilla i niestandardowe GUI za pomocą komendy.
Możesz nawet zdalnie otwierać GUI dla **innych graczy**, jeśli zainstalujesz FancyMenu zarówno na **serwerze, jak i na klientach**.

Aby otworzyć GUI, użyj komendy `/openguiscreen <screen_identifier> <target_player>`.

Zastąp `<screen_identifier>` rzeczywistym identyfikatorem menu GUI, które chcesz otworzyć.
Może to być identyfikator Twojego niestandardowego GUI (utworzonego w FancyMenu) albo zwykły identyfikator menu Vanilla/modu.

Aby uzyskać **identyfikator menu GUI Vanilla/modu**, otwórz menu, którego identyfikator chcesz poznać, i włącz **nakładkę debugowania** FancyMenu przez **Customization -> Debug Overlay**, a następnie możesz kliknąć identyfikator wyświetlany jako pierwsza linia, aby skopiować go do schowka.

![copy_identifier](https://github.com/Keksuccino/FancyMenu/assets/35544624/dd6c53d9-d2bd-4810-be03-3741e326bd5a)

Pozostaw argument `<target_player>` pusty, aby otworzyć GUI dla swojego klienta, albo wybierz gracza (lub wielu graczy), dla których GUI ma zostać otwarte.
Pamiętaj, że drugi gracz musi mieć zainstalowane FancyMenu na swoim kliencie.

Ta komenda nie zadziała dla każdego ekranu, szczególnie dla ekranów modów. Jeśli komenda nie otworzy ekranu, zostanie wyświetlony błąd. Niewiele da się wtedy zrobić, ponieważ prawdopodobnie jest to ekran zbyt złożony, aby FancyMenu mogło otworzyć go automatycznie.

Nie będę też już ręcznie dodawać kompatybilności dla ekranów modów, ponieważ dodanie wsparcia dla wszystkich dostępnych modów zajęłoby mi wieki, przepraszam.

# Zamykanie GUI za pomocą komendy

W rzadkich przypadkach, gdy jest to potrzebne, dostępna jest też komenda `/closeguiscreen <target_player>`, która zamyka bieżący ekran.
