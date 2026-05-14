---
title: Pokazy slajdów
description: Jak tworzyć i używać pokazów slajdów.
---

# Pokazy slajdów

FancyMenu pozwala dodawać pokazy slajdów i wyświetlać je w menu oraz jako tła menu.

> **WAŻNE**: Jeśli używasz systemu Windows, nie zapomnij włączyć [rozszerzeń plików](https://vtcri.kayako.com/article/296-view-file-extensions-windows-10), ponieważ w przeciwnym razie później nie będziesz w stanie zobaczyć ważnych części nazw plików!
{.is-warning}

# Tworzenie pokazu slajdów

Każdy pokaz slajdów musi znajdować się we własnym folderze **wewnątrz** katalogu pokazów slajdów znajdującego się w `/config/fancymenu/slideshows/`.

![1](https://user-images.githubusercontent.com/35544624/105209961-b823e600-5b4a-11eb-8ed2-1016d3b05815.png)

Aby system rozpoznał coś jako pokaz slajdów, w jego folderze musi znajdować się plik właściwości, więc jeśli nazwałeś folder pokazu slajdów `myslideshow`, plik właściwości powinien znajdować się w `/config/fancymenu/slideshows/myslideshow/properties.txt`.

**Ten plik zawsze musi nazywać się `properties.txt`!**
Na razie utwórz tylko **pusty** plik właściwości i przejdź do następnego kroku.

![2](https://user-images.githubusercontent.com/35544624/105210016-cbcf4c80-5b4a-11eb-84ad-9aa735340287.png)

## Dodawanie obrazów

Pokaz slajdów potrzebuje obrazów (oczywiście), więc dodajmy kilka!

> Obrazy do pokazu slajdów muszą być plikami **PNG**! Żadnych JPEG-ów, GIF-ów, APNG ani FMA!
{.is-danger}

Wszystkie obrazy pokazu slajdów trafiają do dodatkowego folderu **wewnątrz** folderu pokazu slajdów (w powyższym przykładzie `myslideshow`).
Ten folder musi mieć nazwę `images`.

![3](https://user-images.githubusercontent.com/35544624/105210833-d9d19d00-5b4b-11eb-8ae7-528ad156e27a.png)

Teraz umieść wszystkie obrazy pokazu slajdów w folderze `images`.
Będą one sortowane alfabetycznie (z uwzględnieniem liczb), więc po prostu nadaj im nazwy w stylu `image_1.png`, `image_2.png` itd.
W moim przykładzie `image_1.png` będzie wyświetlany jako pierwszy, a `image_2.png` po nim.

<br>
<img width="548" alt="Screenshot_2" src="https://github.com/user-attachments/assets/f58ecbfa-affa-4071-8a84-18ed27a6cfee">

## Dodawanie zawartości do pliku właściwości

Na początku utworzyłeś pusty plik `properties.txt` w folderze pokazu slajdów.
Teraz plik ten trzeba wypełnić ważnymi danymi.

Każdy plik właściwości pokazu slajdów powinien wyglądać tak:

```
type = slideshow

slideshow-meta {
   name = cool_slideshow
   width = 1920
   height = 1080
   x = 0
   y = 0
   duration = 5.0
   fadespeed = 12.0
   randomize = false
}
```
Tylko zmienne wewnątrz sekcji `slideshow-meta` mogą być zmieniane!

### name

To jest nazwa, a właściwie identyfikator, twojego pokazu slajdów.
Nazwy pokazów slajdów muszą być **unikalne**, więc nie da się mieć dwóch pokazów slajdów o tej samej nazwie!

### width | height

Bazowe `width` i `height` twojego pokazu slajdów.
Używane przez FancyMenu do obliczania proporcji obrazu.

### x | y

Pozycja `x` i `y` twojego pokazu slajdów.
Bardziej do celów debugowania, więc ustaw oba na `0`.

### duration

Czas trwania w **sekundach**, przez jaki każdy obraz jest wyświetlany przed przejściem do następnego.
Obsługuje wartości dziesiętne!

### fadespeed

Prędkość animacji zanikania podczas przechodzenia do następnego obrazu.
Ta wartość jest mnożnikiem prędkości. Na przykład `1.0` to domyślna prędkość, `2.0` podwaja prędkość, a `0.5` spowolni ją o połowę względem domyślnej.
Wartości ujemne nie są obsługiwane.

### randomize

Czy obrazy pokazu slajdów mają być odtwarzane w losowej kolejności (`true`), czy nie (`false`).

# Korzystanie z pokazu slajdów

Wszystkie ważne kroki są już wykonane i twój pokaz slajdów powinien być gotowy, więc przetestujmy go!

Aby wczytać nowy (lub edytowany) pokaz slajdów do FancyMenu, przeładuj mod przez **Customization -> Reload FancyMenu**.

Teraz możesz użyć swojego pokazu slajdów jako elementu **Slideshow** lub jako tła menu (kliknij prawym przyciskiem myszy tło edytora układu -> **Menu Background**).
