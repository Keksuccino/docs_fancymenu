---
title: Identyfikatory ekranów
description: 'O identyfikatorach ekranów i o tym, jak znaleźć identyfikator ekranu.'
---
# Identyfikatory ekranów

FancyMenu używa identyfikatorów ekranów do układów, widżetów Vanilla, [akcji ekranowych](./action-scripts#open-screen-or-custom-gui-opengui) oraz [nadpisań niestandardowych GUI](./custom-guis#overriding-an-existing-screen). Identyfikatory są rozróżniane wielkością liter, więc kopiuj je dokładnie z nakładki debugowania.

Wbudowane ekrany zwykle używają krótkiego, uniwersalnego identyfikatora, takiego jak `title_screen`. Inne ekrany modów mogą używać nazwy swojej klasy Java. Niestandardowe GUI używają identyfikatora wpisanego w ich menedżerze. Są to identyfikatory ekranów FancyMenu, a nie lokalizacje zasobów Minecrafta.

# Znajdowanie identyfikatora ekranu

Identyfikator aktualnie aktywnego menu możesz zobaczyć, korzystając z **nakładki debugowania**.
Zawiera ona identyfikator bieżącego ekranu i pozwala skopiować go do schowka przez kliknięcie lewym przyciskiem myszy.

>[!TIP]
>Możesz włączyć **nakładkę debugowania**, naciskając **CTRL + ALT + D**, gdy **nie** jesteś w edytorze układu.

<br>

<img width="553" alt="Screenshot_3" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/1800351e-f042-4826-8eed-7725b78bc84d">

<br>

<img width="579" alt="Screenshot_4" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/9e0d1e61-7f2d-4817-9be1-b63ee61978dd">

# Otwieranie ekranów

[**Akcja Open Screen or Custom GUI**](./action-scripts#open-screen-or-custom-gui-opengui) może otwierać tylko te ekrany, które FancyMenu potrafi utworzyć w bieżącym stanie gry. Niektóre ekrany wymagają załadowanego świata, połączenia, gracza lub oryginalnego ekranu nadrzędnego.

Jeśli FancyMenu nie może utworzyć identyfikatora, wyświetli błąd. Użyj [**Mimic Vanilla/Mod Button**](./action-scripts#mimic-vanillamod-button-mimicbutton) na widżecie, który normalnie otwiera dany ekran.
