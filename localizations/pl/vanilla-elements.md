---
title: Elementy Vanilla
description: 'Jak dostosować elementy, które domyślnie są częścią ekranów.'
---

# Elementy Vanilla

FancyMenu nie tylko pozwala dodawać nowe elementy do ekranów, ale także umożliwia dostosowywanie istniejących elementów z podstawowej wersji gry (Vanilla), a nawet z innych modów.

## Przyciski i suwaki Vanilla (widgety)

Aby dostosować istniejące widgety Vanilla/modów, utwórz nowy układ **„dla bieżącego ekranu”** (NIE uniwersalny!) i **kliknij prawym przyciskiem myszy** elementy w edytorze, tak samo jak w przypadku elementów niestandardowych.

Możesz dostosować ich **etykiety i tekstury** tak samo jak w przypadku niestandardowych przycisków i suwaków.

Jedyną rzeczą, której **nie możesz** zrobić z widgetami Vanilla/modów, jest dostosowanie ich **skryptu akcji** (na przykład zmiana tego, co robią po wejściu w interakcję). Jest to możliwe tylko w przypadku niestandardowych przycisków i suwaków.

Aby **przesunąć** i **zmienić rozmiar** widgetów Vanilla/modów, najpierw musisz nadać im punkt zakotwiczenia. W tym celu **kliknij prawym przyciskiem myszy** i wybierz **Punkt zakotwiczenia**. Ustaw go na cokolwiek innego niż **Oryginalny**, ponieważ to domyślny punkt zakotwiczenia elementów Vanilla/modów.

Możesz też **ukryć** widgety Vanilla/modów, po prostu **klikając je prawym przyciskiem myszy** i wybierając **Usuń**. Nie są one tak naprawdę usuwane, lecz ukrywane, a możesz je przywrócić, klikając **pasek menu -> Element -> Usunięte elementy Vanilla** i **lewym przyciskiem myszy** wybierając element(y), które chcesz ponownie wyświetlić.

> Widget **Copyright** na ekranie tytułowym jest jedynym, którego **NIE MOŻNA** ukryć/usunąć. Jest to zamierzone. Prosimy nie usuwać informacji o prawach autorskich.
{.is-warning}

## Elementy ekranu tytułowego

Ekran tytułowy zawiera elementy, które nie są zwykłymi widgetami (takie jak logo, tekst splash itd.) i których nie da się przesuwać ani dostosowywać. Są one przeznaczone do usunięcia i zastąpienia niestandardowymi elementami (na przykład elementem obrazu dla logo lub niestandardowym elementem tekstu splash dla domyślnego tekstu splash).

Aby je usunąć, po prostu kliknij je prawym przyciskiem myszy. Jeśli chcesz później je przywrócić, kliknij **pasek menu -> Element -> Usunięte elementy Vanilla** i **lewym przyciskiem myszy** wybierz element, który chcesz ponownie wyświetlić.

## Rozwiązywanie problemów: Elementy Vanilla nie są widoczne w edytorze

Jeśli nie widzisz elementów Vanilla w edytorze, najprawdopodobniej jest to spowodowane używaniem **uniwersalnego układu** zamiast układu **dla bieżącego ekranu**. Upewnij się, że tworzysz układ dla bieżącego ekranu. Układy dla bieżącego ekranu można tworzyć tylko wtedy, gdy na danym ekranie włączone są modyfikacje.

## Rozwiązywanie problemów: Modyfikacje nie są stosowane

Jeśli modyfikacje elementów Vanilla nie są stosowane poza edytorem, zwykle jest to spowodowane tym, że inny mod nadpisuje lub zmienia nadrzędne menu elementów Vanilla.

Dobrym przykładem moda, który nadpisuje ekran/menu, jest **Ice and Fire**, który nadpisuje ekran tytułowy.

Brak zastosowania modyfikacji do menu nie dotyczy wyłącznie elementów Vanilla. Niestandardowe elementy dodane do ekranów również prawdopodobnie nie zostaną zastosowane do menu, jeśli mod je nadpisuje lub modyfikuje.
