---
title: Intro gry
description: >-
  Odtwarzaj animację lub film przy każdym uruchomieniu gry, zanim pojawi się
  ekran tytułowy.
sourceBlobSha: 2f40eb874b4aebaf4b32ffa2b8980310d71510b7
---

# Intro gry

Intro gry odtwarza animację lub film po uruchomieniu gry, zaraz po ekranie ładowania Minecrafta. Po zakończeniu przechodzi płynnie w ekran tytułowy. Funkcja została stworzona z myślą o paczkach modów: może wyświetlać logo, intro studia lub krótki zwiastun.

<img width="800" alt="Intro Skyhaven: noc zamienia się w świt nad unoszącą się wyspą, a logo pojawia się litera po literze. Następnie intro przechodzi płynnie w ekran tytułowy z tą samą wyspą w tle" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/game_intro_showcase.gif?raw=true">

Gracze mogą pominąć intro dowolnym klawiszem lub kliknięciem. Intro gry to jedna z [globalnych personalizacji](/global-customizations), więc nie wymaga układu.

# Konfigurowanie intro

<img width="800" alt="Otwieranie Global Customizations i Game Intro z paska menu, wybieranie skyhaven_intro.apng za pomocą Set Game Intro, odtwarzanie intro przez Re-Trigger Game Intro i pomijanie go spacją" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/game_intro_setup.gif?raw=true">

1. Umieść animację lub film w folderze `<game-directory>/config/fancymenu/assets/`.
2. Otwórz **pasek menu -> Personalizacja -> Globalne personalizacje -> Intro gry**.
3. Kliknij **Ustaw intro gry**. Gdy **Typ źródła** jest ustawiony na **Lokalne**, kliknij **Wybierz lokalny plik zasobu**, wybierz plik i kliknij **OK**.
4. Kliknij **Odtwórz ponownie intro gry**, aby od razu je obejrzeć.

Aby usunąć intro, najedź kursorem na **Ustaw intro gry** i kliknij **Przywróć domyślne**.

## Animacje i filmy

- **Animacje:** pliki APNG lub GIF. Instrukcje tworzenia znajdziesz w sekcji [Animacje](/animations).
- **Filmy:** pliki MP4. Wymagają modów Watermedia V3 i Watermedia Binaries V3. Więcej informacji znajdziesz w sekcji [Filmy](/video#requirements). Bez tych modów intro wideo wyświetla przez kilka sekund tylko czerwoną notatkę z linkami do pobrania.
- Obsługiwane są pliki z folderu instancji i paczek zasobów, ale nie linki internetowe. Zobacz [Zasoby](/resources).

Intro wypełnia cały ekran, zachowując proporcje, dlatego jego części zostaną przycięte na ekranach o innych proporcjach. Większość ekranów ma proporcje 16:9, więc intro również powinno mieć proporcje 16:9, na przykład rozdzielczość 1920x1080. Przezroczyste obszary intro są wyświetlane na czarno.

> [!TIP]
> Gracze widzą intro przy każdym uruchomieniu gry, dlatego niech będzie krótkie — najlepiej około 5–10 sekund.

## Darmowe przykładowe intro

Intro Skyhaven widoczne na GIF-ach na tej stronie jest darmowe i można go używać do testów oraz w paczkach modów:

- [skyhaven_intro.apng](https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/skyhaven_intro.apng?raw=true): intro o rozdzielczości 1280x720 i długości 5,4 sekundy. Odtwarzane jest raz.
- [skyhaven_menu.png](https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/skyhaven_menu.png?raw=true): ostatnia scena intro bez logo, o rozdzielczości 1280x720. Ustaw ją jako [tło obrazu](/menu-backgrounds#image) układu ekranu tytułowego, a intro przejdzie płynnie w pasujące do niego menu, tak jak na pierwszym GIF-ie.

# Ustawienia

Wszystkie ustawienia znajdziesz w sekcji **pasek menu -> Personalizacja -> Globalne personalizacje -> Intro gry**:

| Ustawienie | Działanie |
|---|---|
| **Ustaw intro gry** | Animacja lub film. |
| **Pomijanie intro gry** | Intro można pominąć dowolnym klawiszem lub kliknięciem. U dołu ekranu wyświetlany jest komunikat **Naciśnij dowolny klawisz, aby pominąć**. Pominięcie natychmiast kończy intro, bez przejścia. Po wyłączeniu tej opcji intro jest zawsze odtwarzane do końca. |
| **Wygaszanie intro gry** | Po zakończeniu intro płynnie przechodzi ono w ekran tytułowy. Po wyłączeniu tej opcji ekran tytułowy pojawia się od razu. |
| **Ignoruj pętle intro gry** | Kończy intro po jednokrotnym odtworzeniu animacji, nawet jeśli animacja jest zapętlona. Po wyłączeniu tej opcji intro odtwarza wszystkie pętle animacji. Filmy zawsze odtwarzane są raz. |
| **Niestandardowy tekst pomijania** | Zastępuje komunikat **Naciśnij dowolny klawisz, aby pominąć**, na przykład tekstem `Naciśnij dowolny klawisz, aby rozpocząć przygodę`. Klucz lokalizacji z paczki zasobów, na przykład `skyhaven.intro.skip`, wyświetla tekst w języku gracza. |
| **Głośność intro gry** | Głośność intro wideo, od 0% do 100%. |
| **Kanał dźwiękowy intro gry** | Kanał dźwiękowy intro wideo, na przykład Muzyka. Głośność tego kanału i głośność główna w ustawieniach dźwięku Minecrafta mają dodatkowy wpływ na poziom głośności. |
| **Odtwórz ponownie intro gry** | Odtwarza intro od razu, na ekranie, na którym aktualnie jesteś. |

Opcje **Pomijanie intro gry**, **Wygaszanie intro gry** i **Ignoruj pętle intro gry** są domyślnie włączone.

> [!WARNING]
> Jeśli opcje **Pomijanie intro gry** i **Ignoruj pętle intro gry** są wyłączone, zapętlona w nieskończoność animacja nigdy się nie zakończy, a gracze nie będą mogli przejść do ekranu tytułowego.

# Warto wiedzieć

- Intro jest odtwarzane raz przy każdym uruchomieniu gry, przed pierwszym ekranem po ekranie ładowania. Zwykle jest to ekran tytułowy.
- Aby zmienić ekran ładowania Minecrafta wyświetlany przed intro, zobacz [Ekran ładowania](/loading-screen).
- Źródło intro może zawierać [symbole zastępcze](/resources#placeholders-in-resource-sources).
- Ustawienia intro gry są zapisywane w pliku `options.txt` moda FancyMenu, dlatego należą do załadowanego [profilu](/profiles). Paczki modów zawierające folder `config/fancymenu/` dołączają intro wraz z jego plikiem w folderze `assets/`. Zobacz [Paczki modów](/modpacks).
