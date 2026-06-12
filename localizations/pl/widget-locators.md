---
title: Lokatory widgetów
description: Czym są lokatory widgetów i jak je znaleźć.
---
# Lokatory widgetów

Lokatory widgetów służą do wskazywania konkretnego widgetu Vanilla/moda (przycisku, suwaka, pola tekstowego) w menu, co jest potrzebne w niektórych funkcjach FancyMenu, które muszą w jakiś sposób wchodzić w interakcję z widgetem.

# Uzyskiwanie lokatora widgetu

Istnieją dwa sposoby, aby uzyskać lokator widgetu Vanilla/moda.

Pierwszy polega na włączeniu **nakładki debugowania** w menu zawierającym dany widget, naciskając **CTRL + ALT + D**, a następnie **kliknięciu widgetu prawym przyciskiem myszy**. Spowoduje to otwarcie menu kontekstowego z opcją skopiowania lokatora do schowka.

Drugi sposób to otwarcie **edytora układu** dla menu zawierającego widget, a następnie **kliknięcie elementu widgetu prawym przyciskiem myszy**. Spowoduje to również otwarcie menu kontekstowego z opcją skopiowania lokatora do schowka.

>[!WARNING]
>Jeśli **nie możesz kliknąć widgetu prawym przyciskiem myszy** przez nakładkę debugowania albo **nie pojawia się** on w edytorze układu, to prawdopodobnie nie jest widoczny dla FancyMenu, co oznacza, że w takim przypadku nie ma lokatora. Najczęściej zdarza się to w przypadku przycisków modów, które są dodawane do menu w nietypowy sposób.
