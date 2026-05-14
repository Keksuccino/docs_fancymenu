---
title: Lokalizowanie układów
description: Jak lokalizować zawartość układów.
---

# Lokalizowanie układów

FancyMenu pozwala lokalizować treści tekstowe, a nawet całe elementy lub układy!

# Treści tekstowe

FancyMenu umożliwia dodawanie własnych lokalizacji do gry.
Można ich następnie używać z placeholderem **Localize Text**, aby lokalizować tekst do bieżącego języka gry.

## Używanie standardowych kluczy lokalizacji Minecrafta

Zanim utworzysz własne lokalizacje, warto rozważyć użycie istniejących kluczy lokalizacji Minecrafta. Oszczędza to czas i zapewnia spójność z domyślnymi tekstami Minecrafta.

### Znajdowanie standardowych kluczy lokalizacji

Najłatwiejszym sposobem znalezienia kluczy lokalizacji Minecrafta jest przeglądanie internetowych plików zasobów gry:

1. **Odwiedź MCAsset.cloud:**  
   Przejdź do [https://mcasset.cloud/](https://mcasset.cloud/) — ta strona pozwala przeglądać zasoby Minecrafta bez ich wyodrębniania z gry.

2. **Przejdź do plików językowych:**  
   - Wybierz swoją wersję Minecrafta z listy rozwijanej
   - Przejdź do: `assets` → `minecraft` → `lang`
   - Otwórz `en_us.json`, aby zobaczyć wszystkie angielskie lokalizacje

3. **Znajdź potrzebny klucz:**  
   - Użyj funkcji wyszukiwania w przeglądarce (Ctrl+F lub Cmd+F), aby znaleźć konkretny tekst
   - Format to `"klucz": "tekst"` — pierwsza część w cudzysłowie przed dwukropkiem (`:`) to klucz
   - Na przykład: `"menu.singleplayer": "Singleplayer"` — kluczem jest `menu.singleplayer`

### Używanie kluczy lokalizacji modów

Jeśli masz zainstalowane inne mody, możesz także używać ich kluczy lokalizacji:

1. Sprawdź dokumentację moda, aby zobaczyć dostępne klucze
2. Przejrzyj pliki językowe moda, jeśli są dostępne jako open source

## Własne pliki lokalizacji

Pliki lokalizacji to pliki tekstowe zawierające całą treść, która ma być dostępna w wielu językach. Każdy tłumaczalny tekst ma unikalny klucz, dzięki czemu Minecraft może znaleźć odpowiedni tekst w plikach lokalizacji.

- **Domyślny plik (en_us.json):**  
  Angielski (USA). Ten plik jest używany, gdy nie wybrano innego pliku językowego. Działa jako plik zapasowy.

- **Inne pliki językowe:**  
  Na przykład możesz utworzyć niemiecki plik o nazwie `de_de.json` dla graczy używających języka niemieckiego.

### Jak utworzyć własny plik lokalizacji

Zawsze potrzebujesz pliku `en_us.json`! Bez niego gra nie ma pliku awaryjnego, gdy coś pójdzie nie tak albo zostanie ustawiony nieobsługiwany język.

1. **Otwórz edytor tekstu:**  
   Użyj Notatnika (Windows), TextEdit (Mac) lub dowolnego prostego edytora tekstu.

2. **Napisz kod JSON:**  
   Utwórz plik z własnymi kluczami. Klucz to unikalna nazwa, której Minecraft używa do odnajdywania tekstu. Na przykład:
   
   ```json
   {
     "modpack_name.custom.localization.key": "Twój własny tekst tutaj",
     "modpack_name.another.key": "Inna wiadomość"
   }
   ```

3. **Zapisz plik:**  
   Zapisz plik jako `en_us.json` dla domyślnego angielskiego tekstu.

Jeśli chcesz teraz dodać wersje tłumaczone, na przykład niemiecką, skopiuj zawartość z pliku `en_us.json` do nowego pliku i tłumacz tylko właściwy tekst, a NIE klucze! Klucze muszą pozostać takie same, aby gra nadal mogła znaleźć tekst.

W przypadku niemieckiego zapiszesz plik jako `de_de.json`. Dla innych języków sprawdź proszę [tę stronę wiki Minecrafta](https://minecraft.wiki/w/Language), aby znaleźć poprawny kod językowy dla Twojego języka, i nazwij plik zgodnie z nim. Szukaj hasła **"in-game locale code"** dla swojego języka.

## Tworzenie pakietu zasobów Minecrafta dla MC 1.21.4

Skoro pliki lokalizacji są już gotowe, potrzebujemy sposobu na wczytanie ich w Minecraftcie. W tym celu użyjemy pakietu zasobów. Ustawimy go tak, aby był włączony domyślnie, a nawet możemy go ukryć, jeśli nie chcemy, aby użytkownicy modpacka mogli go zmieniać.

**Pakiet zasobów** to plik ZIP zawierający pliki, które zmieniają wygląd i charakter gry.

### Kroki tworzenia pakietu zasobów

1. **Utwórz nowy folder:**  
   Utwórz folder o nazwie np. `my_custom_pack`, do którego dodasz własne pliki lokalizacji.

2. **Utwórz plik pakietu (`pack.mcmeta`):**  
   Wewnątrz folderu utwórz plik o nazwie `pack.mcmeta` z następującą zawartością:
   
   ```json
   {
     "pack": {
       "pack_format": 16,
       "description": "Mój własny pakiet z lokalizacjami"
     }
   }
   ```
   
   *Uwaga: `pack_format` 16 dotyczy Minecrafta 1.21.4.*

3. **Dodaj pliki lokalizacji:**  
   W folderze pakietu zasobów utwórz następującą strukturę folderów:
   
   ```
   my_custom_pack/
   ├── assets/
   │   └── minecraft/
   │       └── lang/
   │           ├── en_us.json
   │           └── de_de.json
   └── pack.mcmeta
   ```
   
   Umieść swój własny plik `en_us.json` (oraz inne pliki językowe, takie jak `de_de.json`) w folderze `lang`.

4. **Spakuj pakiet zasobów do ZIP-a:**  
   Gdy folder będzie gotowy, **skompresuj cały folder do pliku ZIP**. Nazwij plik ZIP **my_custom_pack.zip**. To przykładowa nazwa używana w całym poradniku.

## Gdzie umieścić pakiet zasobów

Umieść plik **my_custom_pack.zip** w folderze **Minecraft Resourcepacks**. Ten folder zwykle znajduje się tutaj:

- **Windows:** `%appdata%\.minecraft\resourcepacks`
- **Mac:** `~/Library/Application Support/minecraft/resourcepacks`
- **Linux:** `~/.minecraft/resourcepacks`

> W przypadku modpacków folder `resourcepacks` znajduje się w katalogu instancji Twojego packa.
{.is-warning}

## Automatyczne wczytywanie pakietu za pomocą „Resource Pack Overrides”

Mod **Resource Pack Overrides** umożliwia domyślne włączanie pakietów zasobów.

### Kroki automatycznego wczytywania pakietu

1. **Zainstaluj mod:**  
   Pobierz i zainstaluj mod z [CurseForge](https://www.curseforge.com/minecraft/mc-mods/resource-pack-overrides) lub [Modrinth](https://modrinth.com/mod/resource-pack-overrides).

2. **Znajdź plik konfiguracyjny:**  
   Znajdź plik `.minecraft/config/resourcepackoverrides.json`.  
   *Jeśli plik nie istnieje, utwórz go ręcznie.*

3. **Edytuj plik konfiguracyjny:**  
   Otwórz plik i dodaj swój pakiet zasobów do listy `default_packs`, używając jego nazwy pliku:
   
   ```json
   {
     "schema_version": 2,
     "default_packs": [
       "file/my_custom_pack.zip"
     ]
   }
   ```
   
   To informuje Minecrafta, aby automatycznie wczytywał pakiet zasobów przy uruchomieniu gry.

   **Ważne jest dodanie prefiksu `file/`!**


*Uwaga: Pakiety zasobów na liście są stosowane w odwrotnej kolejności. Oznacza to, że pakiet znajdujący się na górze listy pojawi się poniżej pozostałych w menu pakietów zasobów gry.*

## Ukrywanie pakietu zasobów na ekranie wyboru

Możesz ukryć swój pakiet zasobów, aby gracze nie widzieli go na ekranie wyboru pakietów zasobów.

### Jak go ukryć

1. **Ponownie edytuj plik konfiguracyjny:**  
   W tym samym pliku `.minecraft/config/resourcepackoverrides.json` dodaj nadpisanie dla swojego pakietu:
   
   ```json
   {
     "schema_version": 2,
     "default_packs": [
       "file/my_custom_pack.zip"
     ],
     "pack_overrides": {
       "file/my_custom_pack.zip": {
         "hidden": true
       }
     }
   }
   ```
   
   Ta konfiguracja ukryje **my_custom_pack.zip** na ekranie wyboru, a jednocześnie nadal będzie go automatycznie wczytywać.

## Używanie nowych kluczy lokalizacji w FancyMenu

Skoro Twoje własne pliki lokalizacji są już wczytane, możesz używać nowych kluczy w układach FancyMenu.

1. **Edytuj element oparty na tekście:**  
   Otwórz FancyMenu i wybierz element, taki jak przycisk lub element tekstowy.

2. **Kliknij przycisk Placeholders:**  
   Znajdź przycisk Placeholders w prawym górnym rogu edytora tekstu. (Jeśli go nie widzisz, element może nie obsługiwać placeholderów.)

3. **Wstaw placeholder Localize Text:**  
   Placeholder Localize Text pojawia się jako fragment JSON. Wygląda tak:
   
   ```json
   {"placeholder":"local","values":{"key":"localization.key"}}
   ```
   
   Zastąp `localization.key` własnym kluczem. Na przykład, jeśli chcesz użyć klucza z pliku lokalizacji, zmień go na:
   
   ```json
   {"placeholder":"local","values":{"key":"modpack_name.custom.localization.key"}}
   ```

I to właściwie wszystko! Placeholder powinien zostać zastąpiony rzeczywistą, przetłumaczoną treścią, gdy nie edytujesz jej w edytorze tekstu.

Pamiętaj, że placeholder zawsze będzie lokalizował treść do bieżącego języka gry.

# Treści nietekstowe (obrazy itp.)

FancyMenu umożliwia również lokalizowanie obrazów i praktycznie każdego elementu, jaki chcesz.

Aby to zrobić, musisz użyć **wymagań ładowania**.
Dokładniej: wymagania **Is Game Language**.

Wymaganie **Is Game Language** pozwala wyświetlać elementy lub całe układy tylko wtedy, gdy ustawiony jest konkretny język gry, więc możesz na przykład przygotować dwa elementy Image zawierające tekst i lokalizować ten obraz do wersji z japońskim tekstem, gdy język jest ustawiony na japoński, albo do wersji z angielskim tekstem, gdy język jest ustawiony na angielski.

Aby ustawić wymagania ładowania dla **elementu**, kliknij go prawym przyciskiem myszy i wybierz **Loading Requirements**.

Aby ustawić wymagania ładowania dla **całych układów**, kliknij prawym przyciskiem myszy tło edytora układu i wybierz **Loading Requirements [Layout-Wide]**.
