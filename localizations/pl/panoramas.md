---
title: Panoramy
description: Jak tworzyć i używać niestandardowych panoram tła.
---

# Kubiczne panoramy

FancyMenu obsługuje wczytywanie niestandardowych panoram złożonych z 6 obrazów jako tła menu.

Te panoramy to specjalny sześcienny format panoramy używany przez Minecrafta jako tło na ekranie tytułowym. Składają się z 6 obrazów (boków), które są renderowane jako sześcian (a dokładniej jako skybox).

> **WAŻNE**: Jeśli używasz Windowsa, nie zapomnij włączyć [rozszerzeń plików](https://cdn.discordapp.com/attachments/795308330746511390/801561308012347482/unknown.png), ponieważ w przeciwnym razie później nie będziesz w stanie zobaczyć ważnych części nazw plików!
{.is-warning}

# Tworzenie panoramy

Jeśli nie wiesz, jak Minecraft obsługuje swoje panoramy tła i jak je tworzyć, powinieneś obejrzeć [ten film](https://www.youtube.com/watch?v=F7jMd3zsjZQ&t).
Da Ci on bardzo dobre zrozumienie tego, jak działają panoramy w Minecraftcie i jak jedną stworzyć!

Po obejrzeniu filmu zauważysz, że tworzenie takich panoram może być dość czasochłonne.
Aby zaoszczędzić trochę czasu, możesz rozważyć użycie moda, który tworzy je za Ciebie.
Możesz znaleźć kilka, wyszukując `minecraft panorama mod`, a jednym z nich jest [Panoramica](https://www.curseforge.com/minecraft/mc-mods/panoramica) (stworzone przeze mnie).

# Przygotowanie panoramy

Gdy już masz 6 obrazów panoramy, musisz przenieść je we właściwe miejsce!

Folder panoram FancyMenu znajduje się w `.minecraft/config/fancymenu/panoramas`.
To katalog dla wszystkich panoram, których chcesz używać w modzie.

## Folder panoramy

Każda panorama ma swój własny folder.
Będziesz musiał utworzyć nowy folder w `.minecraft/config/fancymenu/panoramas`, jeśli chcesz dodać nową panoramę.
W moim przykładzie nazwę folder `mypanorama`.

![1](https://user-images.githubusercontent.com/35544624/100791916-2802d380-341a-11eb-8e32-f9913e93a38c.png)

## Zawartość folderu

Po utworzeniu folderu musisz go wypełnić.

### Plik właściwości
Każda panorama potrzebuje pliku właściwości, aby działać.
Ten plik zawsze musi nazywać się `properties.txt` i musi zawierać kilka ważnych informacji.

Zawartość pliku właściwości panoramy powinna zawsze wyglądać tak:
```
type = panorama

panorama-meta {
  name = name_of_your_panorama
  speed = 1.0
  fov = 85.0
  angle = 25.0
  start_rotation = 0
}
```
Tylko zmienne wewnątrz sekcji `panorama-meta` można zmieniać!

#### name
Musi to być **unikalna** nazwa Twojej panoramy.
Nie da się wczytać dwóch panoram o tej samej nazwie!
Tej nazwy użyjesz później do identyfikowania swojej panoramy.

#### speed
Prędkość, z jaką obraca się panorama.
Ta wartość jest mnożnikiem prędkości. Na przykład `1.0` to prędkość domyślna, `2.0` podwaja prędkość, a `0.5` ją zmniejsza o połowę.
Wartości ujemne nie są obsługiwane; aby spowolnić panoramę, używaj wartości dziesiętnych.

#### fov
Pole widzenia.
Domyślne FOV to `85.0`.
Zbyt duże lub zbyt małe wartości tutaj zepsują panoramę. Po prostu poeksperymentuj, aby znaleźć odpowiednie FOV.

#### angle
Pionowy kąt, pod jakim oglądana jest panorama.
Domyślny kąt to `25.0`.

#### start_rotation
Kąt obrotu (poziomy), od którego panorama ma się zaczynać. Wartość między 0 a 360.

<br>

### Folder obrazów panoramy

Drugą obowiązkową rzeczą, której potrzebuje folder panoramy, jest właściwy folder z obrazami panoramy.

Nazwa tego folderu musi brzmieć `panorama`.

Umieść w nim wszystkie obrazy panoramy, ale nie zapomnij nadać im poprawnych nazw, tak jak pokazano w powyższym [filmie](https://www.youtube.com/watch?v=F7jMd3zsjZQ&t)!

![3](https://user-images.githubusercontent.com/35544624/100791922-29340080-341a-11eb-8174-874a180d0485.png)

> Jako obrazy panoramy obsługiwane są tylko pliki PNG!
{.is-warning}

### Nakładka panoramy

Ostatni krok jest **opcjonalny** i można go pominąć, jeśli nie chcesz nakładki na panoramie.

Jeśli chcesz dodać do panoramy winietę lub inne rodzaje nakładek, możesz dodać plik o nazwie `overlay.png`.
Pamiętaj, że dla nakładki obsługiwany jest tylko format PNG, a nazwa pliku zawsze musi brzmieć `overlay.png`!

### Ponowne sprawdzenie wszystkiego

Powinieneś teraz mieć folder znajdujący się w `.minecraft/config/fancymenu/panoramas`, zawierający plik `properties.txt`, inny folder o nazwie `panorama` i ewentualnie nakładkę o nazwie `overlay.png`.

![2](https://user-images.githubusercontent.com/35544624/100791920-29340080-341a-11eb-8e26-98a7fd2ad7eb.png)

# Używanie panoramy

Po (ponownym) uruchomieniu gry lub przeładowaniu FancyMenu przez **Customization -> Reload FancyMenu** powinieneś teraz móc ustawić swoją panoramę jako tło menu. Aby to zrobić, kliknij prawym przyciskiem myszy tło edytora układu i wybierz **Menu Background**.
