---
title: Modpacki
description: Jak dołączyć układy do modpacka.
---

# FancyMenu w modpackach

Dodanie konfiguracji FancyMenu do modpacka jest bardzo proste i wymaga tylko kilku prostych kroków.

> Ta strona dotyczy **WYŁĄCZNIE** konfiguracji FancyMenu stworzonych w całości w **FancyMenu v3+**, więc jeśli używasz starszej konfiguracji (utworzonej w v2 i przekonwertowanej do v3), niektóre kroki mogą się różnić.
{.is-warning}

# Dodawanie konfiguracji FancyMenu do modpacka

Najważniejszą rzeczą, którą musisz zrobić, jest skopiowanie jednego specjalnego folderu, którego FancyMenu używa do zapisywania wszystkich twoich projektów.

## Czego będziesz potrzebować

1. **Folder „Minecraft Instance”**: To główny folder na twoim komputerze, w którym są przechowywane wszystkie pliki dla konkretnej instalacji Minecrafta (na przykład tej, w której projektowałeś menu). Launchery takie jak CurseForge i Modrinth nazywają je „instancjami” lub „profilami”.
2. **Folder `config`**: W folderze instancji Minecrafta zwykle znajduje się folder o nazwie `config`. To tutaj wiele modów przechowuje swoje ustawienia.
3. **Folder `fancymenu`**: Wewnątrz folderu `config` FancyMenu tworzy własny folder o nazwie `fancymenu`. To ten najważniejszy folder, którego potrzebujemy!

## Jak znaleźć lokalizację zapisu instancji

### Jeśli używasz aplikacji CurseForge

1. Otwórz CurseForge.
2. Znajdź swój profil/instancję Minecrafta na liście i otwórz go.
3. Kliknij trzy kropki.
4. Wybierz „Open Folder”. Spowoduje to otwarcie głównego folderu tej instancji Minecrafta.

<img width="630" alt="Screenshot_1" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/curseforge_launcher_instance.png">

### Jeśli używasz aplikacji Modrinth

1. Otwórz aplikację Modrinth.
2. Znajdź swój profil/instancję Minecrafta na liście i otwórz go.
3. Kliknij trzy kropki.
4. Wybierz „Open Folder”. Spowoduje to otwarcie głównego folderu tej instancji Minecrafta.

<img width="630" alt="Screenshot_1" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/modrinth_launcher_instance.png">

### Dla innych launcherów

Poszukaj podobnej opcji „Open Folder”, „Open Instance Folder” albo „View Files” dla twojej konkretnej konfiguracji Minecrafta.

## Kopiowanie konfiguracji FancyMenu

1. Przejdź do folderu `config` swojej instancji MODPACKA (tej, do której chcesz skopiować konfigurację).
2. Jeśli znajduje się w nim folder `fancymenu`, USUŃ go.
3. Otwórz folder `config` INSTANCJI ŹRÓDŁOWEJ (tej, z której chcesz użyć konfiguracji).
4. Skopiuj folder `fancymenu` z folderu `config` swojej instancji ŹRÓDŁOWEJ do folderu `config` swojej instancji MODPACKA.
5. Gotowe. To wszystko. Uruchom ponownie instancję modpacka, a konfiguracja powinna się wczytać.

> Pamiętaj, że stare, legacy konfiguracje utworzone w FancyMenu v2 (nawet jeśli przekonwertowane do v3) pozwalały przechowywać zasoby układów poza folderem `/config/fancymenu/assets/` FancyMenu, więc w takim przypadku musisz upewnić się, że dołączysz również wszystkie swoje zasoby do modpacka.
{.is-danger}

# Wyłączanie paska menu i skrótów klawiszowych

Z pewnością nie chcesz, aby pasek menu FancyMenu był widoczny w twoim modpacku, więc powinieneś go wyłączyć. Ale ponieważ użytkownicy nadal mogą nacisnąć skrót klawiszowy, żeby znowu go wyświetlić, zróbmy coś nieco bardziej *agresywnego*.

Przejdź do `/config/fancymenu/options.txt` i otwórz plik w edytorze tekstu.

Następnie ustaw `modpack_mode` na `true` i zapisz plik.
Spowoduje to całkowite wyłączenie wszystkich nakładek i skrótów klawiszowych.

Aby móc ponownie edytować swoje układy, ustaw tę opcję konfiguracyjną z powrotem na `false`.

# Wyłączanie ekranu powitalnego

W większości przypadków nie powinno to być potrzebne, ale jeśli jeszcze nie zamknąłeś ekranu powitalnego (ekranu, który informuje o konieczności przeczytania dokumentacji), upewnij się, że ustawisz `show_welcome_screen` na `false` w `/config/fancymenu/options.txt`.

Ten ekran wyświetla się tylko raz i wyłącza się sam po kliknięciu przycisku **Open Documentation**, więc ponownie: ręczne ustawianie tego zazwyczaj nie powinno być potrzebne.

<br>
<img width="630" alt="Screenshot_1" src="https://github.com/user-attachments/assets/4383b39f-f55a-4eb8-8142-34a425474bb3">
