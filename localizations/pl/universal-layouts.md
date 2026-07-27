---
title: Uniwersalne układy
description: Zastosuj jeden układ do wielu obsługiwanych ekranów.
---

# Uniwersalne układy

Uniwersalny układ jest brany pod uwagę dla każdego obsługiwanego ekranu, na którym włączono dostosowywanie ekranu. Nie dotyczy to ekranów [zablokowanych](./incompatibility-list#screens-where-customization-is-intentionally-disabled) ani w inny sposób wykluczonych.

Używaj uniwersalnych układów dla wspólnych elementów, takich jak logo, nawigacja, nakładki czy [elementy Audio](./elements#audio), które mają pojawiać się na kilku ekranach.

# Tworzenie

1. Otwórz obsługiwany ekran i wyświetl pasek menu FancyMenu.
2. Wybierz **Layouts -> New -> For All Screens [Universal]**.
3. Dodaj i skonfiguruj elementy.
4. Zapisz układ.

Zwykłe ekrany nadal wymagają włączenia **Current Screen Customization**. Nie ma globalnego przełącznika „włącz dla wszystkich”, ponieważ nieobsługiwane ekrany moda mogą ulec awarii po dostosowaniu.

# Ograniczanie ekranów

Otwórz ustawienia uniwersalnego układu z menu kontekstowego tła edytora.

- **Whitelist:** układ ma zastosowanie tylko do wymienionych identyfikatorów ekranów.
- **Blacklist:** układ ma zastosowanie do każdego kwalifikującego się ekranu z wyjątkiem wymienionych identyfikatorów.

Użyj **Customization -> Copy Identifier of Current Screen**, aby skopiować [identyfikator ekranu](./screen-identifiers).

Możesz też dodać [wymagania dla całego układu](./conditions#layout-wide-requirements), aby kontrolować, kiedy układ ma zastosowanie.

# Kolejność układów

Kwalifikujące się uniwersalne układy i układy specyficzne dla ekranu są łączone i nakładane według **Layout Index**. Niższe indeksy są stosowane jako pierwsze; późniejsze ustawienia, które można nakładać, mogą zastąpić wcześniejsze. Przy tym samym indeksie uniwersalne układy są pobierane przed układami specyficznymi dla ekranu.
