---
title: Profile
description: >-
  Zapisuj, przełączaj i udostępniaj kompletne konfiguracje FancyMenu za pomocą
  profili oraz instaluj szablony układów społeczności.
sourceBlobSha: 52348efde29798073477e572b59a7630f96013ad
---

# Profile

Profil to kompletna konfiguracja FancyMenu: układy, zasoby, zmienne, ustawienia i wszystko inne z katalogu `config/fancymenu/` (zobacz [Lokalizacje przechowywania danych](/data-storage-locations#your-setup)). Dzięki profilom możesz przechowywać kilka konfiguracji w jednej instancji Minecrafta, przełączać się między nimi w kilka sekund i udostępniać je jako pojedynczy plik.

<img width="800" alt="Tworzenie profilu My Menu Pack, importowanie profilu Wind Chimes przez upuszczenie jego pliku .fmp na okno Profile, usuwanie profilu My Menu Pack i wczytywanie Wind Chimes, co zmienia ekran tytułowy" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/profiles_showcase.gif?raw=true">

# Okno Profili

Otwórz je, wybierając **pasek menu -> Dostosowywanie -> Profile**.

- Lista po lewej stronie zawiera wszystkie profile. Wczytany profil znajduje się na początku i jest oznaczony jako **Aktywny**. Wszystkie zmiany wprowadzane w FancyMenu są od razu zapisywane w tym profilu.
- Po prawej stronie wyświetlane są informacje o wybranym profilu: jego ikona, tytuł, wersja, autorzy, liczba układów, rozmiar, linki i opis.
- Po najechaniu kursorem na przyciski pod listą i szczegółami wyświetlana jest ich nazwa. Kliknięcie profilu prawym przyciskiem myszy również wyświetla dostępne dla niego akcje.

Twoja konfiguracja automatycznie staje się pierwszym profilem o nazwie **Mój profil**.

# Wczytywanie profilu

Wybierz profil i kliknij **Wczytaj profil**, kliknij go dwukrotnie albo naciśnij `Enter`.

FancyMenu uruchomi się ponownie z wybranym profilem, tak jak po uruchomieniu gry. Wszystkie pozostałe okna FancyMenu zostaną zamknięte, a jeśli nie jesteś w świecie, otworzy się ekran tytułowy.

> [!NOTE]
> Wczytywanie nigdy niczego nie usuwa. Bieżąca konfiguracja zostaje najpierw zapisana jako osobny profil, więc zawsze możesz do niej wrócić.

# Tworzenie profili

- **Nowy profil** (przycisk `+` pod listą) tworzy pusty profil i od razu otwiera jego szczegóły, aby można było nadać mu nazwę. Zachowuje preferencje FancyMenu, takie jak skala interfejsu i motyw, ale nie zawiera układów ani innych dostosowań. Nie zostaje wczytany automatycznie.
- **Duplikuj** kopiuje wybrany profil. To przydatne, gdy chcesz coś przetestować bez modyfikowania oryginału.

# Edytowanie szczegółów profilu

Wybierz profil i kliknij **Edytuj**, aby zmienić jego szczegóły:

- **Tytuł** — jedyna wymagana informacja o profilu.
- **Wersja** i **Autorzy**. Oddzielaj nazwiska kilku autorów przecinkami.
- **Opis** z formatowaniem [Markdown](/text-formatting#markdown), takim jak pogrubienie, nagłówki i listy.
- **Zgłaszanie problemów** — strona internetowa, na której można zgłaszać problemy z profilem. Wyświetla się jako **Zgłoś problem**.
- **Linki** do serwera Discord, kanału YouTube, strony internetowej i innych miejsc. Kliknij **Dodaj link** i wklej link — FancyMenu samo rozpozna platformę.
- Ikona: **Wybierz ikonę** pozwala wybrać obraz PNG, a **Usuń ikonę** usuwa ikonę. Obrazy, które nie są kwadratowe, zostaną przycięte do środka.

Zmiany nie zostaną zapisane, dopóki nie klikniesz **Gotowe**.

# Udostępnianie profili

> [!CAUTION]
> Profile mogą wykonywać akcje, takie jak otwieranie linków lub uruchamianie poleceń. Importuj je tylko z zaufanych źródeł.

## Eksportowanie

Wybierz profil, kliknij **Eksportuj** i wskaż miejsce zapisu. W ten sposób powstanie plik `.fmp` zawierający cały profil, gotowy do udostępnienia.

## Importowanie

Kliknij **Importuj** pod listą i wybierz plik `.fmp` albo przeciągnij go i upuść na oknie Profili.

- Zaimportowane profile nie są wczytywane automatycznie. Wczytaj je tak jak każdy inny profil.
- Jeśli masz już dany profil, na przykład jego starszą wersję, wybierz **Zastąp** albo **Zachowaj oba**. Zastąpienie wczytanego profilu natychmiast wczyta zaimportowany profil, a zmiany wprowadzone w starym zostaną utracone.
- Profile utworzone w nowszej wersji FancyMenu najpierw wyświetlą ostrzeżenie, ponieważ niektóre ich elementy mogą nie działać.
- Działają tylko pliki `.fmp` wyeksportowane przez FancyMenu. Informacje o zwykłych folderach znajdziesz w następnej sekcji.

## Dodawanie folderów z konfiguracją

Niektóre konfiguracje są udostępniane jako zwykły folder `fancymenu` (kopia czyjegoś katalogu `config/fancymenu/`), a nie jako plik `.fmp`. Aby dodać taki folder jako profil:

1. Rozpakuj go, jeśli jest w pliku `.zip`.
2. Przenieś folder do `<game-directory>/config/fancymenu/profiles/`. Jeśli folderu `profiles` jeszcze tam nie ma, utwórz go.
3. Otwórz okno Profili albo zamknij je i otwórz ponownie. FancyMenu doda folder do listy profili.

Folder musi zawierać bezpośrednio pliki, takie jak `customization/` i `options.txt`, a nie kolejny folder `fancymenu`. Tytułem profilu będzie nazwa folderu, chyba że zawiera on własne szczegóły profilu. Zmienisz je, klikając **Edytuj**.

## Szablony układów

Na kanale [`#layout-templates`](https://discord.com/channels/704163135787106365/1234093433795383316) na [serwerze Discord Kekscord](https://discord.gg/rhayah27GC) (oficjalnym serwerze Discord Keksuccino poświęconym pomocy dotyczącej modów) społeczność udostępnia kompletne konfiguracje FancyMenu i jego dodatków, takich jak SpiffyHUD i Drippy Loading Screen. Każdy wpis zawiera link do pobrania pliku `.fmp` albo folderu `fancymenu`.

Szablony są złożone, dlatego nie próbuj łączyć ich z własną konfiguracją. Zamiast tego dodaj je jako osobny profil:

1. [Zaimportuj](#importing) plik `.fmp` albo [dodaj folder](#adding-setup-folders).
2. Wybierz szablon w oknie Profili i kliknij **Wczytaj profil**.

Twoja konfiguracja pozostanie dostępna jako osobny profil, więc zawsze możesz do niej wrócić.

Większość szablonów można edytować i wykorzystywać we własnych projektach, takich jak paczki modów, ale nie wszystkie. Zawsze sprawdź we wpisie dotyczącym szablonu, co wolno z nim robić.

# Usuwanie profili

Wybierz profil i kliknij **Usuń** albo naciśnij `Delete` (`Fn + Delete` na macOS). Usunięcia nie można cofnąć, więc jeśli chcesz mieć kopię zapasową, najpierw wyeksportuj profil.

Nie można usunąć wczytanego profilu. Najpierw wczytaj inny profil.

# Gdzie przechowywane są profile

- Wczytany profil znajduje się w katalogu `<game-directory>/config/fancymenu/`.
- Wszystkie pozostałe profile znajdują się w katalogu `<game-directory>/config/fancymenu/profiles/`, każdy we własnym folderze. **Otwórz folder** otwiera folder wybranego profilu.

`<game-directory>` to folder instancji, który może być inny niż `.minecraft`. Dane w `<game-directory>/fancymenu_data/` nie należą do profili — zobacz [Lokalizacje przechowywania danych](/data-storage-locations#instance-data).

# Rozwiązywanie problemów

- **Niektóre pliki są nadal używane:** często oznacza to, że gra nadal coś wczytuje, na przykład dźwięk. Odczekaj kilka sekund i spróbuj ponownie. Jeśli problem nie ustąpi, zamknij programy, które mogą korzystać z tych plików, takie jak program antywirusowy, usługa synchronizacji w chmurze albo okno menedżera plików.
- **Poprzednie przełączanie profilu jeszcze się nie zakończyło:** nic nie zostało utracone. Wczytaj ponownie profil albo uruchom grę ponownie, aby dokończyć przełączanie.
- **Brakuje wolnego miejsca na dysku:** komunikat informuje, ile miejsca potrzebuje profil. Zwolnij trochę miejsca i spróbuj ponownie.
- Akcje dotyczące profili są wykonywane pojedynczo. Eksportowanie, importowanie i duplikowanie dużych profili może chwilę potrwać, dlatego na czas ich wykonywania wyświetlany jest przycisk **Anuluj**.
