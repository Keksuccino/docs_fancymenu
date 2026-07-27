---
title: Główne menu Ice & Fire
description: Jak wyłączyć niestandardowe główne menu Ice and Fire.
---

# Główne menu Ice & Fire

Aby wyłączyć niestandardowy ekran tytułowy w modzie Ice and Fire, musisz zmienić jego konfigurację. Oto jak możesz to zrobić:

## 1. Znajdź plik konfiguracyjny
- **Nazwa pliku:** To ustawienie znajduje się w pliku o nazwie **`iceandfire-client.toml`**.
- **Lokalizacja folderu:** Plik ten zwykle znajduje się w **`<game-directory>/config/`**, gdzie `<game-directory>` to aktywny katalog instancji/profilu w launcherze.

## 2. Edytuj plik konfiguracyjny
- **Otwórz plik:** Użyj dowolnego prostego edytora tekstu (takiego jak Notatnik w systemie Windows lub TextEdit w systemie macOS), aby otworzyć `iceandfire-client.toml`.
- **Znajdź ustawienie:** Przewiń w dół, aż znajdziesz opcję związaną z niestandardowym głównym menu. Może być zakomentowana i wyglądać podobnie do tej:
  ```toml
  # Czy wyświetlać smoka w głównym menu, czy nie [domyślnie: true]
  B:"Custom main menu"=true
  ```
- **Zmień wartość:** Ustaw tę opcję na **false**, zmieniając linię na:
  ```toml
  B:"Custom main menu"=false
  ```
  Ta zmiana informuje mod, aby nie renderował własnego niestandardowego głównego menu (często z motywem smoka lub innymi wizualizacjami).

## 3. Zapisz i uruchom ponownie
- **Zapisz plik:** Po wprowadzeniu zmiany zapisz plik.
- **Uruchom ponownie Minecrafta:** Zamknij i ponownie uruchom Minecrafta, aby zmiany zaczęły obowiązywać. Po załadowaniu gry powinno być używane domyślne główne menu zamiast niestandardowego menu z moda.

## Dodatkowe wskazówki
- **Sprawdź, czy edytujesz właściwy plik:** Może istnieć osobny wspólny plik konfiguracyjny, więc upewnij się, że edytujesz **`iceandfire-client.toml`** (to konfiguracja specyficzna dla klienta, a nie plik wspólny).
- **Zrób kopię zapasową:** Zawsze warto zrobić kopię zapasową oryginalnego pliku konfiguracyjnego przed jego modyfikacją.
- **Modpacki:** Jeśli używasz modpacka, plik konfiguracyjny może znajdować się w strukturze folderów paczki, ale zasada pozostaje taka sama.

Wykonanie tych kroków powinno wyłączyć niestandardowe główne menu dostarczane przez mod, dzięki czemu będziesz mógł używać tła głównego menu z własnego pakietu tekstur.
