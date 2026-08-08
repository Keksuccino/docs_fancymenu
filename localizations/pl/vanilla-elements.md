---
title: Elementy Vanilla
description: 'Jak dostosowywać elementy, które domyślnie są częścią ekranów.'
---
# Elementy Vanilla

FancyMenu nie tylko pozwala dodawać nowe rzeczy do ekranów, ale także umożliwia dostosowywanie istniejących elementów z podstawowej gry (Vanilla), a nawet z innych modów.

## Przyciski i suwaki Vanilla (widgety)

Aby dostosować istniejące widgety Vanilla/modów, po prostu utwórz nowy układ **„dla bieżącego ekranu”** (NIE uniwersalny!) i kliknij elementy **prawym przyciskiem myszy** w edytorze, tak samo jak w przypadku własnych.

Możesz dostosować ich **etykiety i tekstury** tak samo jak w przypadku własnych przycisków i suwaków.

Jedyną rzeczą, której **nie da się** zrobić z widgetami Vanilla/modów, jest dostosowanie ich **skryptu akcji** (na przykład zmiana tego, co robią po interakcji). Jest to możliwe tylko w przypadku własnych przycisków i suwaków.

## Automatyczne kliknięcia

Widgety Vanilla i modów mają właściwość **Automated Clicks**. Ustaw ją na liczbę całkowitą większą niż `0`, aby wywołać oryginalne zachowanie widgetu po lewym kliknięciu tyle razy, ile podasz, gdy ekran się załaduje. Na przykład ustawienie `2` kliknie widget dwukrotnie podczas pierwszej aktualizacji każdego nowo otwartego ekranu. Wartość domyślna `0` wyłącza automatyczne kliknięcia.

To są prawdziwe kliknięcia widgetów: każde kliknięcie może zmienić wartość suwaka lub przycisku cyklicznego, uruchomić standardowy callback widgetu, a nawet otworzyć inny ekran. Testuj rezultat ostrożnie, zwłaszcza przy konfiguracji więcej niż jednego kliknięcia.

Aby **przesunąć** i **zmienić rozmiar** widgetów Vanilla/modów, najpierw trzeba nadać im punkt zakotwiczenia. W tym celu kliknij je **prawym przyciskiem myszy** i wybierz **Anchor Point**. Ustaw inną wartość niż **Original**, ponieważ to domyślny punkt zakotwiczenia elementów Vanilla/modów.

Możesz także **ukryć** widgety Vanilla/modów, po prostu klikając je **prawym przyciskiem myszy** i wybierając **Delete**. Nie są one naprawdę usuwane, tylko ukrywane, a przywrócić je można, klikając **menu bar -> Element -> Deleted Vanilla Elements** i **lewym przyciskiem myszy** wybierając elementy, które chcesz ponownie wyświetlić.

> [!WARNING]
> Widget **Copyright** na ekranie tytułowym jest jedynym, którego **NIE DA SIĘ** ukryć/usunąć. Takie jest zamierzone działanie. Prosimy nie usuwać informacji o prawach autorskich.

## Elementy ekranu tytułowego

Ekran tytułowy zawiera elementy, które nie są zwykłymi widgetami (takie jak logo, tekst zajawki itp.) i których nie da się przesuwać ani dostosowywać. Są one przeznaczone do usunięcia i zastąpienia własnymi elementami (np. elementem Image dla logo lub własnym elementem Splash Text dla domyślnego tekstu zajawki).

Aby je usunąć, po prostu kliknij je prawym przyciskiem myszy. Jeśli chcesz później je przywrócić, kliknij **menu bar -> Element -> Deleted Vanilla Elements** i **lewym przyciskiem myszy** wybierz element, który ma znów być widoczny.

## Rozwiązywanie problemów: Elementy Vanilla nie są widoczne w edytorze

Jeśli nie widzisz elementów Vanilla w edytorze, najprawdopodobniej używasz **uniwersalnego układu** zamiast układu **dla bieżącego ekranu**. Upewnij się, że tworzysz układ dla bieżącego ekranu. Układy dla bieżącego ekranu można tworzyć tylko wtedy, gdy dostosowywanie jest włączone dla tego ekranu.

## Rozwiązywanie problemów: Dostosowania nie są stosowane

Jeśli dostosowania elementów Vanilla nie są stosowane poza edytorem, zwykle jest to spowodowane przez inny mod, który nadpisuje lub modyfikuje nadrzędne menu elementów Vanilla.

Dobrym przykładem moda nadpisującego ekran/menu jest **Ice and Fire**, który zastępuje ekran tytułowy.

Brak zastosowania dostosowań do menu nie dotyczy wyłącznie elementów Vanilla. Własne elementy dodawane do ekranów również prawdopodobnie nie zostaną zastosowane do menu, jeśli mod je nadpisuje lub modyfikuje.
