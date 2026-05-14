---
title: Główne menu Ice & Fire
description: Jak wyłączyć niestandardowe główne menu Ice and Fire.
---

Aby wyłączyć niestandardowy ekran tytułowy w modzie Ice and Fire, musisz zmienić jego konfigurację. Oto jak możesz to zrobić:

## 1. Znajdź plik konfiguracyjny
- **Nazwa pliku:** To ustawienie znajduje się w pliku **`iceandfire-client.toml`**.
- **Lokalizacja folderu:** Ten plik zwykle znajduje się w folderze **`.minecraft/config`** (lub w odpowiednim katalogu konfiguracji, jeśli używasz niestandardowego launchera albo modpacka).

## 2. Edytuj plik konfiguracyjny
- **Otwórz plik:** Użyj dowolnego prostego edytora tekstu (np. Notatnika w systemie Windows lub TextEdit na macOS), aby otworzyć `iceandfire-client.toml`.
- **Znajdź ustawienie:** Przewiń w dół, aż znajdziesz opcję związaną z niestandardowym głównym menu. Może być zakomentowana i wyglądać mniej więcej tak:
  ```toml
  # Whether to display the dragon on the main menu or not [default: true]
  B:"Custom main menu"=true
  ```
- **Zmień wartość:** Ustaw tę opcję na **false**, zmieniając linię na:
  ```toml
  B:"Custom main menu"=false
  ```
  Ta zmiana informuje mod, aby nie wyświetlał własnego niestandardowego głównego menu (często z smokiem lub innymi tematycznymi elementami wizualnymi).

## 3. Zapisz i uruchom ponownie
- **Zapisz plik:** Po wprowadzeniu zmiany zapisz plik.
- **Uruchom ponownie Minecrafta:** Zamknij i ponownie uruchom Minecrafta, aby zmiany zaczęły obowiązywać. Po załadowaniu gry powinno być używane domyślne główne menu zamiast niestandardowego menu moda.

## Dodatkowe wskazówki
- **Upewnij się, że edytujesz właściwy plik:** Może istnieć oddzielny główny plik konfiguracji, więc sprawdź, czy edytujesz **`iceandfire-client.toml`** (to konfiguracja specyficzna dla klienta, a nie ogólna).
- **Zrób kopię zapasową:** Zawsze warto zrobić kopię oryginalnego pliku konfiguracyjnego przed jego modyfikacją.
- **Modpacki:** Jeśli korzystasz z modpacka, plik konfiguracyjny może znajdować się w strukturze folderów paczki, ale zasada pozostaje taka sama.

Ta metoda została potwierdzona przez użytkowników społeczności — na przykład kilku użytkowników na forum Feed The Beast wspomniało, że znalezienie i zmiana opcji `"Custom main menu"` w **`iceandfire-client.toml`** rozwiązało ich problem. (Zobacz dyskusję, w której użytkownik zauważył: „ustaw konfigurację ice and fire tak, aby tego nie wyświetlała w iceandfire-client.toml” oraz że plik znajduje się w folderze config.) citeturn0search1

Wykonanie tych kroków powinno wyłączyć niestandardowe główne menu dostarczane przez mod, dzięki czemu możesz używać własnego tła głównego menu z tekstury packa.
