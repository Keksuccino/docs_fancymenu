---
title: Pierwsze kroki
description: Świat FancyMenu czeka na Ciebie! To początek czegoś pięknego!
---

# Dla deweloperów

Jeśli jesteś deweloperem i chcesz stworzyć dodatek do FancyMenu albo zintegrować FancyMenu ze swoim modem, powinieneś zajrzeć do [dokumentacji dla deweloperów](https://github.com/Keksuccino/FancyMenu-Dev-Docs/wiki).

# Pierwsze kroki

Pierwsze użycie FancyMenu może być trochę przytłaczające, ale nie martw się — większość rzeczy staje się całkiem intuicyjna, gdy tylko zaczniesz z nich korzystać!

> Pamiętaj **prosze** również, że ta strona służy tylko do wprowadzenia Cię w FancyMenu i pomocy przy Twoich **pierwszych krokach**.
Koniecznie sprawdź też resztę dokumentacji, aby uzyskać bardziej szczegółowe informacje o funkcjach FancyMenu!
{.is-info}

# Pasek menu

Jedną z pierwszych rzeczy, które zauważysz po uruchomieniu gry, jest **pasek menu** u góry każdego menu.

**Pasek menu** jest punktem wejścia do praktycznie wszystkich funkcji FancyMenu, takich jak **tworzenie layoutów** do **personalizowania menu**, zmiana **tytułu i ikony okna** oraz wiele więcej.

> Jeśli przez pomyłkę nacisnąłeś jakieś klawisze i **pasek menu zniknął**, możesz przywrócić go, naciskając **CTRL + ALT + C**.
{.is-warning}

<img width="650" alt="menu_bar" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/menu_bar.png?raw=true">

# Twój pierwszy layout

Ponieważ prawdopodobnie chcesz dostosować menu Minecrafta, opowiem Ci trochę o **layoutach**!

Layouty są jak warstwy personalizacji menu i pozwalają dodawać nowe elementy oraz dostosowywać istniejące.

Aby utworzyć nowy layout dla **konkretnego menu**:
1. Otwórz menu, dla którego chcesz utworzyć layout (na przykład ekran tytułowy)
2. Otwórz zakładkę **Customization** na **pasku menu**

Personalizacje są domyślnie wyłączone dla wszystkich menu i musisz je aktywować osobno dla każdego menu, które chcesz dostosować, więc kliknij najpierw wpis **"Current Screen Customization: Disabled"**, aby przełączyć opcję na **Enabled**.

<img width="475" alt="toggle_customizations" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/toggle_customizations.png?raw=true">

Następnie kliknij **Layouts -> New -> For Current Screen**.

Spowoduje to otwarcie **edytora layoutu**, w którym możesz dodawać elementy do layoutu oraz dostosowywać elementy Vanilla i z modów (takie jak przyciski).

<img width="550" alt="new_layout_current" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/new_layout_current.png?raw=true">

## Edytowanie layoutu

Do większości opcji personalizacji można uzyskać dostęp, **klikając prawym przyciskiem myszy tło edytora**.
Spowoduje to otwarcie menu kontekstowego z wieloma opcjami, takimi jak dostosowanie **tła menu** lub **dodawanie elementów** do layoutu.

<br>
<img width="350" alt="context_menu" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/context_menu.png?raw=true">

## Dodawanie elementów do layoutów

Aby dodać nowy element do layoutu, **kliknij prawym przyciskiem myszy** tło edytora.

W otwartym menu kontekstowym kliknij **New Element** i wybierz jeden z wielu typów elementów.

<img width="525" alt="add_element" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/add_element.png?raw=true">

## Dostosowywanie elementów

Aby dostosować element, **kliknij go prawym przyciskiem myszy**, co otworzy menu kontekstowe ze wszystkim, co można skonfigurować dla tego typu elementu.

Oprócz dodanych przez Ciebie elementów możesz także dostosowywać elementy Vanilla (choć czasem mają one mniej opcji)

<img width="525" alt="element_customization" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/element_customization.png?raw=true">

> [!IMPORTANT]
> Niektóre takie menu kontekstowe są **przewijalne**!

## Pozycjonowanie elementów

Każdy element w FancyMenu jest powiązany z **punktem zakotwiczenia**.

Punkty zakotwiczenia są niezbędne do obliczania pozycji elementu i, jeśli są używane prawidłowo, zapobiegają nakładaniu się elementów na siebie, wychodzeniu poza ekran lub przesuwaniu się w złe miejsce podczas zmiany rozmiaru okna.

To punkt odniesienia, od którego obliczana jest pozycja elementu.

Domyślnie elementy są powiązane z punktem zakotwiczenia **"Center of Screen"**, czyli po prostu dokładnym środkiem ekranu, niezależnie od rozmiaru okna.
Załóżmy więc, że element znajduje się 2 centymetry od środka ekranu, będąc powiązanym z kotwicą **"Center of Screen"**. W takim przypadku element będzie **zawsze** znajdował się 2 centymetry od środka ekranu, niezależnie od rozmiaru okna.

Możesz zobaczyć punkt zakotwiczenia, z którym powiązany jest element, podczas jego przeciągania. Spowoduje to również wyświetlenie wszystkich innych punktów zakotwiczenia (domyślnie). Możesz najechać na punkt zakotwiczenia podczas przeciągania elementu, aby zmienić kotwicę elementu na ten punkt.

Możesz nawet użyć jednego elementu jako punktu zakotwiczenia dla innych elementów! Wystarczy najechać na element podczas przeciągania innego, a punkt zakotwiczenia przeciąganego elementu zostanie zmieniony na wskazany element.

**[Dowiedz się więcej o tym, jak pozycjonować elementy.](/positioning-elements)**

<img width="650" alt="anchor_points" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/anchor_points.png?raw=true">

## Zapisywanie pracy

Nie zapomnij zapisać swojego arcydzieła!

Jeśli przed zamknięciem musisz zapisać zmiany, w prawym górnym rogu edytora zobaczysz wskaźnik „Unsaved Changes”.

Zapisz swoją pracę, klikając **Layout -> Save**!

<img width="375" alt="save_your_work" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/save_your_work.png?raw=true">

> [!TIP]
> Możesz też zapisać swoją pracę za pomocą skrótu klawiszowego **CTRL + S**

*Gratulacje! Teraz możesz sprawić, że menu Minecrafta będą wyglądały znacznie piękniej!*
