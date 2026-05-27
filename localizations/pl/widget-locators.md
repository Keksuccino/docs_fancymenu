---
title: Lokalizatory widgetów
description: Czym są lokalizatory widgetów i jak je znaleźć.
---
# Lokalizatory widgetów

Lokalizatory widgetów służą do wskazywania konkretnego widgetu Vanilla (przycisku, suwaka, pola tekstowego) w menu, co jest potrzebne do niektórych funkcji FancyMenu, które muszą w jakiś sposób wchodzić w interakcję z widgetem.

# Jak uzyskać lokalizator widgetu

Istnieją dwa sposoby uzyskania lokalizatora widgetu Vanilla.

Pierwszy polega na aktywowaniu **nakładki debugowania** w menu zawierającym dany widget, poprzez naciśnięcie **CTRL + ALT + D**, a następnie **kliknięcie widgetu prawym przyciskiem myszy**. Otworzy to menu kontekstowe z opcją skopiowania lokalizatora do schowka.

Drugi sposób to otwarcie **edytora układu** dla menu zawierającego widget, a następnie **kliknięcie prawym przyciskiem myszy elementu widgetu**. Spowoduje to również otwarcie menu kontekstowego z opcją skopiowania lokalizatora do schowka.

>[!WARNING]
>Jeśli **nie możesz kliknąć widgetu prawym przyciskiem myszy** przez nakładkę debugowania albo **nie pojawia się on** w edytorze układu, to prawdopodobnie nie jest widoczny dla FancyMenu, co oznacza, że w takim przypadku nie ma lokalizatora. Najczęściej zdarza się to w przypadku przycisków modów dodawanych do menu w nietypowy sposób.
