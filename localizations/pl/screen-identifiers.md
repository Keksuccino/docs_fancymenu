---
title: Identyfikatory ekranów
description: >-
  Informacje o identyfikatorach ekranów i o tym, jak znaleźć identyfikator
  ekranu.
sourceBlobSha: 64414e10bf5f532e075373a6a753e2f667448ceb
---
# Identyfikatory ekranów

FancyMenu używa identyfikatorów ekranów w układach, widżetach Vanilla, [akcjach ekranów](/action-scripts#open-screen-or-custom-gui) i [nadpisaniach niestandardowych GUI](/custom-guis#overriding-an-existing-screen). Identyfikatory rozróżniają wielkość liter, dlatego kopiuj je dokładnie z nakładki debugowania.

Wbudowane ekrany zazwyczaj używają krótkich, uniwersalnych identyfikatorów, takich jak `title_screen`. Ekrany z innych modów mogą używać nazw swoich klas Javy. Niestandardowe GUI używają identyfikatora podanego w ich menedżerze. Są to identyfikatory ekranów FancyMenu, a nie lokalizacje zasobów Minecrafta.

# Znajdowanie identyfikatora ekranu

Identyfikator aktualnie aktywnego menu można sprawdzić za pomocą **nakładki debugowania**.
Zawiera ona identyfikator bieżącego ekranu. Kliknięcie go lewym przyciskiem myszy kopiuje identyfikator do schowka.

>[!TIP]
>Nakładkę debugowania można włączyć, naciskając **CTRL + ALT + D**, gdy **nie** jesteś w edytorze układów.

<br>

<img width="553" alt="Screenshot_3" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/1800351e-f042-4826-8eed-7725b78bc84d">

<br>

<img width="579" alt="Screenshot_4" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/9e0d1e61-7f2d-4817-9be1-b63ee61978dd">

# Otwieranie ekranów

Akcja [**Otwórz ekran lub niestandardowe GUI**](/action-scripts#open-screen-or-custom-gui) może otworzyć tylko te ekrany, które FancyMenu jest w stanie utworzyć w bieżącym stanie gry. Niektóre ekrany wymagają wczytanego świata, połączenia, gracza lub ekranu nadrzędnego, z którego zostały otwarte.

Jeśli FancyMenu nie może utworzyć ekranu na podstawie identyfikatora, wyświetli błąd. Użyj opcji [**Naśladuj przycisk Vanilla/moda**](/action-scripts#mimic-vanillamod-button) na widżecie, który normalnie otwiera dany ekran.
