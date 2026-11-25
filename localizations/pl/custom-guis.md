---
title: Niestandardowe GUI
description: >-
  Twórz własne menu od podstaw, otwieraj je przyciskami, klawiszami lub
  komendami, wyświetlaj jako wyskakujące okna i zastępuj nimi inne menu.
sourceBlobSha: 0b336708473ae2964b3d9e777498c6cd40eaffc6
---

# Niestandardowe GUI

Niestandardowe GUI to menu, które tworzysz samodzielnie, na przykład ekran z informacjami o modpacku, hub serwera lub stronę z zasadami. Są początkowo puste — wypełniasz je [układem](/layout-editor), tak jak każde inne menu. Można je otwierać przyciskami, klawiszami i komendami.

<img width="800" alt="Kliknięcie przycisku Modpack Info na ekranie tytułowym otwiera niestandardowe GUI jako wyskakujące okno na rozmytym ekranie tytułowym, a przycisk Back ponownie je zamyka" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/custom_guis_popup.gif?raw=true">

# Tworzenie niestandardowego GUI

<img width="800" alt="Otwarcie Manage Custom GUIs, kliknięcie New GUI, wpisanie identyfikatora modpack_info, włączenie Popup Mode i otwarcie nowego niestandardowego GUI" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/custom_guis_new.gif?raw=true">

1. Otwórz **pasek menu -> Dostosowywanie -> Niestandardowe GUI -> Zarządzaj niestandardowymi GUI**.
2. Kliknij **Nowe GUI**.
3. Wpisz **identyfikator niestandardowego GUI**, na przykład `modpack_info`, skonfiguruj [ustawienia](#ustawienia) i kliknij **Gotowe**.
4. Kliknij nowe niestandardowe GUI na liście, a następnie kliknij **Otwórz GUI**.
5. Kliknij **Gotowe**, aby zamknąć okno **Zarządzaj niestandardowymi GUI**.

Zmiany wprowadzone w oknie **Zarządzaj niestandardowymi GUI** są zapisywane dopiero po kliknięciu **Gotowe** lub **Otwórz GUI**. Kliknięcie **Anuluj** je odrzuca.

## Identyfikator

Przyciski, komendy i układy wyszukują niestandardowe GUI na podstawie jego identyfikatora.

- Dozwolone są tylko małe litery, cyfry oraz znaki `.`, `_` i `-`. Każde niestandardowe GUI musi mieć własny identyfikator.
- Nie używaj [identyfikatora innego ekranu](/screen-identifiers), na przykład `title_screen`. Niestandardowe GUI współdzieliłoby z tym ekranem swoje układy.
- Jeśli później zmienisz identyfikator, układy oraz przyciski i komendy korzystające ze starego identyfikatora przestaną je znajdować. Przywrócenie poprzedniego identyfikatora przywróci ich działanie.

## Tworzenie układu

1. Otwórz niestandardowe GUI.
2. Kliknij **pasek menu -> Dostosowywanie -> Układy -> Nowy -> Dla bieżącego ekranu**. Dostosowywanie jest zawsze włączone dla niestandardowych GUI.
3. Dodaj elementy i zapisz układ. Zobacz [Edytor układu](/layout-editor).

Niestandardowe GUI nie zawiera żadnych elementów, nawet przycisku Wstecz. Dodaj do niego [przycisk](/elements#button) z akcją [**Powrót do poprzedniego ekranu**](/action-scripts#back-to-last-screen) albo pozostaw włączoną opcję **Zezwalaj na zamykanie GUI klawiszem ESC**, aby gracze mogli je opuścić.

# Ustawienia

Opcja **Edytuj GUI** w oknie **Zarządzaj niestandardowymi GUI** pozwala zmienić ustawienia wybranego niestandardowego GUI.

| Ustawienie | Działanie |
|---|---|
| **Identyfikator niestandardowego GUI** | Nazwa niestandardowego GUI. Zobacz [Identyfikator](#identyfikator). |
| **Tytuł ekranu (opcjonalnie)** | Biały tytuł u góry GUI. Pozostaw pole puste, aby go nie wyświetlać. Działają [zmienne](/placeholders), a klucze lokalizacyjne gry, modów i paczek zasobów są wyświetlane w języku gracza. |
| **Zezwalaj na zamykanie GUI klawiszem ESC** | Klawisz `Esc` zamyka GUI. Domyślnie włączone. |
| **Wstrzymaj grę/świat** | Wstrzymuje światy jednoosobowe, gdy GUI jest otwarte. Domyślnie włączone. |
| **Renderuj tło świata** | Podczas gry wyświetla świat za GUI. Poza światem lub gdy ta opcja jest wyłączona wyświetlana jest panorama Minecrafta. Domyślnie włączone. |
| **Renderuj nakładkę na tło świata** | Rozmywa i przyciemnia świat lub panoramę za GUI, tak jak w menu pauzy. Działa tylko z opcją **Renderuj tło świata**; bez niej panorama jest zawsze rozmyta i przyciemniona. Domyślnie włączone. |
| **Tryb wyskakującego okna** | Wyświetla GUI nad menu, z którego zostało otwarte. Zobacz [Tryb wyskakującego okna](#tryb-wyskakującego-okna). |
| **Nakładka tła w trybie wyskakującego okna** | Rozmywa menu za wyskakującym oknem. Działa tylko w **trybie wyskakującego okna**. Domyślnie włączone. |

- Siła rozmycia odpowiada ustawieniu Minecrafta **Rozmycie tła menu**.
- [Tło menu](/menu-backgrounds) w układzie zakrywa wszystko: świat, panoramę i menu za wyskakującym oknem.
- Edytor układu nie pozwala zmienić tytułu (**Niestandardowy tytuł ekranu**) niestandardowych GUI. Zamiast tego zmień opcję **Tytuł ekranu (opcjonalnie)**. Aby użyć tytułu z własną czcionką, kolorem lub położeniem, pozostaw to pole puste i dodaj [element tekstowy](/elements#text).

## Tryb wyskakującego okna

W **trybie wyskakującego okna** menu, z którego otwarto niestandardowe GUI, pozostaje widoczne w tle wraz ze swoim układem. Gdy wyskakujące okno jest otwarte, nie można klikać menu w tle.

- Wyskakujące okna najlepiej sprawdzają się w przypadku niewielkich elementów, takich jak okno z informacjami, prośba o potwierdzenie lub panel ustawień. Pozostaw trochę wolnego miejsca, aby było widać menu w tle.
- Nie dodawaj tła menu do układu wyskakującego okna, bo menu w tle zniknie.
- Jeśli niestandardowe GUI zostanie otwarte, gdy żadne menu nie jest otwarte — na przykład klawiszem podczas gry — nie będzie menu, które można wyświetlić w tle. Wtedy pojawi się zwykłe tło GUI.

# Otwieranie niestandardowego GUI

Wszystko, co otwiera ekrany, może też otwierać niestandardowe GUI, jeśli podasz jego identyfikator:

- **Przyciski:** akcja [**Otwórz ekran lub niestandardowe GUI**](/action-scripts#open-screen-or-custom-gui) z wartością `modpack_info`.
- **Klawisze:** nasłuchiwacz [**Po naciśnięciu klawisza na klawiaturze**](/listeners#listener-variables) z tą samą akcją. Otwiera niestandardowe GUI w menu i podczas gry.
- **Komendy:** `/openguiscreen modpack_info`, także na serwerach, w blokach poleceń i jako nagrody za zadania. Zobacz [Komendy](/commands#openguiscreen).
- **Opuszczanie świata:** akcja [**Opuść świat lub serwer**](/action-scripts#leave-world-or-server) z identyfikatorem otwiera niestandardowe GUI po opuszczeniu świata lub serwera.

Niestandardowe GUI są częścią konfiguracji FancyMenu każdego gracza. Serwer może otworzyć tylko te niestandardowe GUI, które mają jego gracze, na przykład GUI z modpacka.

Aby opuścić niestandardowe GUI:

- Klawisz `Esc` (gdy włączono opcję **Zezwalaj na zamykanie GUI klawiszem ESC**) oraz akcja **Powrót do poprzedniego ekranu** przenoszą z powrotem do menu, z którego otwarto GUI. Jeśli żadne menu nie było otwarte, klawisz `Esc` przenosi z powrotem do gry.
- Akcja [**Zamknij ekran**](/action-scripts#close-screen) zamyka GUI. Poza światem otwiera się ekran tytułowy.

# Zastępowanie istniejącego ekranu

Niestandardowe GUI może zastąpić menu gry lub moda. Za każdym razem, gdy otworzyłoby się to menu, zamiast niego otworzy się niestandardowe GUI.

> [!WARNING]
> Zastąpione menu nigdy się nie otwiera, więc nie wykonuje żadnych działań, a mody, które go potrzebują, mogą przestać działać prawidłowo. Jeśli to możliwe, zmieniaj menu za pomocą zwykłego układu. Zastępuj menu tylko wtedy, gdy układ nie pozwala uzyskać potrzebnego efektu.

1. Włącz **pasek menu -> Dostosowywanie -> Ustawienia -> Zaawansowany tryb dostosowywania**.
2. Otwórz menu, które chcesz zastąpić.
3. Kliknij **pasek menu -> Dostosowywanie -> Niestandardowe GUI -> Zastąp bieżący ekran niestandardowym GUI**.
4. Potwierdź ostrzeżenie i wybierz niestandardowe GUI w oknie **Wybierz niestandardowe GUI**.

Niestandardowe GUI otworzy się od razu. Klawisz `Esc` i akcja **Powrót do poprzedniego ekranu** w tym GUI przenoszą z powrotem do menu, które było otwarte przed zastąpionym menu.

Aby cofnąć zmianę, otwórz **pasek menu -> Dostosowywanie -> Niestandardowe GUI -> Zarządzaj zastąpionymi ekranami**, kliknij **Usuń regułę zastępowania** pod ekranem i kliknij **Gotowe**.

> [!TIP]
> Aby zastępować menu tylko w niektórych sytuacjach, na przykład gdy ustawiona jest [zmienna](/variables), użyj zamiast tego nasłuchiwacza [**Po otwarciu ekranu**](/listeners#on-screen-opened) z instrukcją IF.

# Zarządzanie niestandardowymi GUI

- Opcje **Nowe GUI**, **Edytuj GUI** i **Otwórz GUI** w oknie **Zarządzaj niestandardowymi GUI** pozwalają dodawać, zmieniać i otwierać niestandardowe GUI.
- Opcja **Usuń GUI** usuwa wybrane niestandardowe GUI po potwierdzeniu. Jego układy pozostają i ponownie pojawią się w nowym niestandardowym GUI o tym samym identyfikatorze.
- Pasek wyszukiwania pozwala znaleźć niestandardowe GUI po identyfikatorze.
- **pasek menu -> Pomoc -> Eksportuj dla AI -> Niestandardowe GUI** eksportuje wszystkie niestandardowe GUI i reguły zastępowania do [czatu AI](/export-for-ai).

Niestandardowe GUI i reguły zastępowania są zapisywane w pliku `config/fancymenu/custom_gui_screens.txt`, a ich układy — tak jak wszystkie pozostałe — w folderze `config/fancymenu/customization/` (zobacz [Lokalizacje przechowywania danych](/data-storage-locations)). Każdy [profil](/profiles) ma własny zestaw niestandardowych GUI.
