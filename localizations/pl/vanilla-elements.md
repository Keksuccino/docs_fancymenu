---
title: Elementy z wersji podstawowej
description: 'Jak dostosowywać elementy, które domyślnie znajdują się na ekranach.'
sourceBlobSha: 3943106d1e4f0722aad0d1578908262b7c8d92ec
---

# Elementy z wersji podstawowej

FancyMenu pozwala nie tylko dodawać nowe elementy do ekranów, ale także dostosowywać istniejące elementy z podstawowej wersji gry (Vanilla), a nawet z innych modów.

## Przyciski i suwaki z wersji podstawowej (widżety)

Aby dostosować przyciski i suwaki na ekranie, utwórz układ dla bieżącego ekranu (a nie [układ uniwersalny](/universal-layouts)), a następnie kliknij je prawym przyciskiem myszy w edytorze.

Mają takie same ustawienia jak własne [przyciski](/elements#button) i [suwaki](/elements#slider), takie jak tekstury, dźwięki i podpowiedzi. Nie można zmienić jedynie ich skryptów akcji — nadal będą działać tak jak wcześniej.

Elementów z wersji podstawowej nie można umieszczać w [obszarach przewijania](/scrollable-areas), ponieważ należą do samego menu.

### Etykiety

- **Etykieta** i **Etykieta po najechaniu** zastępują tekst przycisku. W przypadku innych widżetów, takich jak suwaki, te opcje nazywają się **Tekst widżetu** i **Tekst widżetu po najechaniu**. Bez nich widżet zachowuje własny tekst.
- **Wyrównanie etykiety** umieszcza etykietę po **lewej**, na **środku** lub po **prawej** stronie widżetu. Etykiety, które są zbyt szerokie, by zmieścić się w widżecie, przewijają się z jednej strony na drugą, niezależnie od wyrównania.
- Opcje **Skala etykiety**, **Podstawowy kolor etykiety**, **Kolor etykiety po najechaniu**, **Cień etykiety** i **Podkreśl etykietę po najechaniu** zmieniają rozmiar i kolor etykiety oraz jej cień.

Aby wyrównać etykiety kilku przycisków jednocześnie, zaznacz je, klikając z wciśniętym klawiszem `Ctrl` (zobacz [Zaznaczanie](/layout-editor#selecting)), kliknij prawym przyciskiem myszy jeden z nich i ustaw dla wszystkich **Wyrównanie etykiety**. Aby zmienić wyrównanie etykiet we wszystkich menu, użyj opcji **Wyrównanie etykiety** w sekcji [Globalne dostosowania](/global-customizations#labels). [Szablon](/button-slider-templates) może też nadać wszystkim przyciskom na danym ekranie ten sam styl etykiet.

## Automatyczne kliknięcia

Widżety z wersji podstawowej i modów mają właściwość **Automatyczne kliknięcia**. Ustaw ją na liczbę całkowitą większą od `0`, aby po załadowaniu ekranu tyle razy wywołać oryginalne działanie widżetu przypisane do kliknięcia lewym przyciskiem myszy. Na przykład ustawienie wartości `2` spowoduje dwukrotne kliknięcie widżetu podczas pierwszej aktualizacji każdego nowo otwartego ekranu. Domyślna wartość `0` wyłącza automatyczne kliknięcia.

Są to rzeczywiste kliknięcia widżetu: każde z nich może zmienić wartość suwaka lub przycisku cyklicznego, uruchomić zwykłą funkcję zwrotną widżetu, a nawet otworzyć inny ekran. Dokładnie sprawdź efekt, zwłaszcza jeśli ustawiasz więcej niż jedno kliknięcie.

Aby **przesuwać** i **zmieniać rozmiar** widżetów z wersji podstawowej lub modów, najpierw musisz przypisać im punkt zakotwiczenia. W tym celu kliknij je **prawym przyciskiem myszy**, a następnie wybierz **Punkt zakotwiczenia**. Ustaw dowolną opcję inną niż **Oryginalny**, ponieważ jest to domyślny punkt zakotwiczenia elementów z wersji podstawowej i modów.

Możesz też **ukryć** widżety z wersji podstawowej lub modów: kliknij je **prawym przyciskiem myszy**, a następnie wybierz **Usuń**. Nie zostaną faktycznie usunięte, a jedynie ukryte. Możesz je przywrócić, klikając **pasek menu -> Element -> Usunięte elementy Vanilla**, a następnie **lewym przyciskiem myszy** wybierając elementy, które chcesz ponownie wyświetlić.

> [!WARNING]
> Widżet **Prawa autorskie** na ekranie tytułowym to jedyny element, którego **NIE MOŻNA** ukryć ani usunąć. Takie jest zamierzenie. Prosimy nie usuwać informacji o prawach autorskich.

## Elementy ekranu tytułowego

Na ekranie tytułowym znajdują się elementy, które nie są zwykłymi widżetami (takie jak logo czy tekst powitalny) i których nie można przesuwać ani dostosowywać. Można je usunąć i zastąpić własnymi elementami (na przykład elementem Obraz dla logo albo własnym elementem Tekst powitalny zamiast tekstu powitalnego z wersji podstawowej).

Aby je usunąć, kliknij je prawym przyciskiem myszy. Jeśli później zechcesz je przywrócić, kliknij **pasek menu -> Element -> Usunięte elementy Vanilla**, a następnie **lewym przyciskiem myszy** wybierz element, który chcesz ponownie wyświetlić.

## Rozwiązywanie problemów: elementy z wersji podstawowej nie są widoczne w edytorze

Jeśli nie widzisz w edytorze elementów z wersji podstawowej, prawdopodobnie używasz **układu uniwersalnego** zamiast układu **dla bieżącego ekranu**. Upewnij się, że utworzysz układ dla bieżącego ekranu. Układy dla bieżącego ekranu można tworzyć tylko wtedy, gdy dostosowywanie jest włączone dla tego ekranu.

## Rozwiązywanie problemów: dostosowania nie są stosowane

Jeśli dostosowania elementów z wersji podstawowej nie są stosowane poza edytorem, zwykle przyczyną jest inny mod, który zastępuje lub modyfikuje nadrzędne menu tych elementów.

Dobrym przykładem moda, który zastępuje ekran lub menu, jest **Ice and Fire** — mod ten zastępuje ekran tytułowy.

Problem ze stosowaniem dostosowań do menu nie dotyczy wyłącznie elementów z wersji podstawowej. Własne elementy dodane do ekranów również prawdopodobnie nie będą wyświetlane w menu, jeśli mod je zastępuje lub modyfikuje.
