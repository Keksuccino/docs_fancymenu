---
title: Modpacki
description: Jak dołączyć układy do modpacka.
---
# FancyMenu w modpackach

Dołączenie konfiguracji FancyMenu do modpacka jest bardzo proste i zajmuje tylko kilka nieskomplikowanych kroków.

> [!CAUTION]
> Konfiguracje FancyMenu mogą uruchamiać akcje. Importuj je tylko z zaufanych źródeł.

> [!WARNING]
> Ta strona dotyczy **WYŁĄCZNIE** konfiguracji FancyMenu utworzonych w całości w **FancyMenu v3+**, więc jeśli używasz starszej konfiguracji (utworzonej w v2 i przekonwertowanej do v3), niektóre kroki mogą się różnić.

# Dołączanie konfiguracji FancyMenu do modpacka

Główna rzecz, którą musisz zrobić, to skopiować jeden specjalny folder, którego FancyMenu używa do zapisywania wszystkich projektów.

## Czego będziesz potrzebować

1. **Folder „Minecraft Instance”:** To główny folder na twoim komputerze, w którym przechowywane są wszystkie pliki konkretnej konfiguracji Minecrafta (na przykład tej, w której projektowałeś swoje menu). Launchery takie jak CurseForge i Modrinth nazywają je „instance” lub „profile”.
2. **Folder `config`:** W folderze twojej instancji Minecrafta zwykle znajduje się folder o nazwie `config`. To tutaj wiele modów zapisuje swoje ustawienia.
3. **Folder `fancymenu`:** Wewnątrz folderu `config` FancyMenu tworzy własny folder o nazwie `fancymenu`. To właśnie ten najważniejszy folder jest nam potrzebny!

## Jak znaleźć lokalizację zapisu instancji

### Jeśli używasz aplikacji CurseForge

1. Otwórz CurseForge.
2. Znajdź swoją profil/instancję Minecrafta na liście i otwórz ją.
3. Kliknij trzy kropki.
4. Wybierz „Open Folder”. Spowoduje to otwarcie głównego folderu tej instancji Minecrafta.

<img width="630" alt="Screenshot_1" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/curseforge_launcher_instance.png">

### Jeśli używasz aplikacji Modrinth

1. Otwórz aplikację Modrinth.
2. Znajdź swój profil/instancję Minecrafta na liście i otwórz ją.
3. Kliknij trzy kropki.
4. Wybierz „Open Folder”. Spowoduje to otwarcie głównego folderu tej instancji Minecrafta.

<img width="630" alt="Screenshot_1" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/modrinth_launcher_instance.png">

### W przypadku innych launcherów

Szukaj podobnej opcji „Open Folder”, „Open Instance Folder” lub „View Files” dla swojej konkretnej konfiguracji Minecrafta.

## Kopiowanie konfiguracji FancyMenu

1. Przejdź do folderu `config` swojej instancji MODPACKA (tej, do której chcesz skopiować konfigurację).
2. Jeśli znajduje się w nim folder `fancymenu`, USUŃ go.
3. Otwórz folder `config` swojej instancji ŹRÓDŁOWEJ (tej, z której chcesz użyć konfiguracji).
4. Skopiuj folder `fancymenu` z folderu `config` swojej instancji ŹRÓDŁOWEJ do folderu `config` swojej instancji MODPACKA.
5. Gotowe. To wszystko. Uruchom ponownie instancję modpacka, a powinieneś zobaczyć, jak konfiguracja się wczytuje.

> [!CAUTION]
> Pamiętaj, że stare, legacy konfiguracje utworzone w FancyMenu v2 (nawet jeśli zostały przekonwertowane do v3) pozwalały przechowywać zasoby układów poza folderem FancyMenu `<game-directory>/config/fancymenu/assets/`, więc w takim przypadku musisz upewnić się, że dołączysz również wszystkie swoje zasoby do modpacka.

# Wyłączanie paska menu i skrótów klawiszowych

Na pewno nie chcesz, aby pasek menu FancyMenu był widoczny w twoim modpacku, więc powinieneś go wyłączyć. Ale ponieważ użytkownicy nadal mogą nacisnąć skrót klawiszowy, aby ponownie go wyświetlić, zróbmy coś trochę bardziej *agresywnego*.

Przejdź do `<game-directory>/config/fancymenu/options.txt` i otwórz plik w edytorze tekstu.

Następnie ustaw `modpack_mode` na `true` i zapisz plik.
Spowoduje to całkowite wyłączenie wszystkich nakładek i skrótów klawiszowych.

Aby móc ponownie edytować swoje układy, ustaw tę opcję konfiguracji z powrotem na `false`.

# Wyłączanie ekranu powitalnego

W większości przypadków nie powinno to być potrzebne, ale jeśli jeszcze nie zamknąłeś ekranu powitalnego (tego, który prosi o przeczytanie dokumentacji), upewnij się, że ustawisz `show_welcome_screen` na `false` w `<game-directory>/config/fancymenu/options.txt`.

Ekran wyświetla się tylko raz i sam się wyłącza po kliknięciu przycisku **Open Documentation**, więc ponownie — ręczne robienie tego zwykle nie powinno być konieczne.

<br>
<img width="630" alt="Screenshot_1" src="https://github.com/user-attachments/assets/4383b39f-f55a-4eb8-8142-34a425474bb3">
