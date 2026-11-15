---
title: Modpacki
description: Jak dołączyć układy do modpacka.
sourceBlobSha: deb3c58e9536e0fe085820a2b9e463f5faaa7819
---

# FancyMenu w modpackach

Dołączenie konfiguracji FancyMenu do modpacka jest bardzo proste i wymaga tylko kilku nieskomplikowanych kroków.

> [!CAUTION]
> Konfiguracje FancyMenu mogą uruchamiać akcje. Importuj je tylko ze źródeł, którym ufasz.

> [!WARNING]
> Ta strona dotyczy **WYŁĄCZNIE** konfiguracji FancyMenu utworzonych w całości w **FancyMenu v3+**. Jeśli używasz starszej konfiguracji (utworzonej w wersji v2 i przekonwertowanej do v3), niektóre kroki mogą wyglądać inaczej.

# Dodawanie konfiguracji do modpacka

Najprostszym sposobem przeniesienia konfiguracji z instancji, w której została zaprojektowana, do instancji modpacka jest użycie [profilu](./profiles):

1. W instancji zawierającej konfigurację otwórz **pasek menu -> Dostosowywanie -> Profile**, wybierz swoją konfigurację i [wyeksportuj](./profiles#exporting) ją jako plik `.fmp`.
2. W instancji modpacka otwórz okno profili i [zaimportuj](./profiles#importing) plik `.fmp`, na przykład przeciągając go do tego okna.
3. Wybierz zaimportowany profil i kliknij **Wczytaj profil**.

Konfiguracja FancyMenu, która była wcześniej używana w instancji modpacka, nie zostanie utracona. Pozostanie dostępna jako osobny profil, więc zawsze będzie można do niej wrócić.

# Dołączanie konfiguracji do modpacka

Wczytany profil to zawartość folderu `<game-directory>/config/fancymenu/`, dlatego zostanie dołączony do folderu `config` modpacka, podobnie jak konfiguracje innych modów.

Wszystkie pozostałe profile instancji są przechowywane w folderze `<game-directory>/config/fancymenu/profiles/`. Przed wyeksportowaniem modpacka usuń profile, których gracze nie powinni otrzymać, albo pomiń folder `profiles` podczas eksportowania modpacka.

> [!CAUTION]
> Pamiętaj, że starsze konfiguracje utworzone w FancyMenu v2 (nawet jeśli zostały przekonwertowane do v3) pozwalały przechowywać zasoby układów poza folderem `<game-directory>/config/fancymenu/assets/` FancyMenu. Profile zawierają tylko folder konfiguracyjny FancyMenu, dlatego w takim przypadku musisz upewnić się, że wszystkie zasoby również zostaną dołączone do modpacka.

## Jak znaleźć folder instancji

Folder instancji to główny folder na komputerze, w którym przechowywane są wszystkie pliki konkretnej konfiguracji Minecrafta. Programy uruchamiające, takie jak CurseForge i Modrinth, nazywają je „instancjami” lub „profilami” (nie należy ich mylić z profilami FancyMenu).

### Jeśli używasz aplikacji CurseForge

1. Otwórz CurseForge.
2. Znajdź swój profil/instancję Minecrafta na liście i otwórz ją.
3. Kliknij trzy kropki.
4. Wybierz opcję „Otwórz folder”. Otworzy to główny folder tej instancji Minecrafta.

<img width="630" alt="Screenshot_1" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/curseforge_launcher_instance.png">

### Jeśli używasz aplikacji Modrinth

1. Otwórz aplikację Modrinth.
2. Znajdź swój profil/instancję Minecrafta na liście i otwórz ją.
3. Kliknij trzy kropki.
4. Wybierz opcję „Otwórz folder”. Otworzy to główny folder tej instancji Minecrafta.

<img width="630" alt="Screenshot_1" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/modrinth_launcher_instance.png">

### W przypadku innych programów uruchamiających

Poszukaj podobnej opcji, takiej jak „Otwórz folder”, „Otwórz folder instancji” lub „Wyświetl pliki”, odpowiedniej dla używanej konfiguracji Minecrafta.

# Wyłączanie paska menu i skrótów klawiszowych

Z pewnością nie chcesz, aby pasek menu FancyMenu był widoczny w modpacku, dlatego należy go wyłączyć. Ponieważ gracze nadal mogliby nacisnąć skrót klawiszowy, aby ponownie go wyświetlić, zastosujmy rozwiązanie nieco bardziej *radykalne*.

Przejdź do pliku `<game-directory>/config/fancymenu/options.txt` i otwórz go w edytorze tekstu.

Ustaw teraz `modpack_mode` na `true` i zapisz plik.
Spowoduje to całkowite wyłączenie wszystkich nakładek i skrótów klawiszowych.

Aby ponownie móc edytować układy, ustaw tę opcję konfiguracji z powrotem na `false`.

# Wyłączanie ekranu powitalnego

W większości przypadków nie powinno to być konieczne, ale jeśli ekran powitalny (ekran z prośbą o przeczytanie dokumentacji) nie został jeszcze zamknięty, ustaw wartość `show_welcome_screen` na `false` w pliku `<game-directory>/config/fancymenu/options.txt`.

Ekran ten wyświetla się tylko raz i wyłącza się po kliknięciu przycisku **Otwórz dokumentację**, więc w większości przypadków ręczne wykonywanie tej czynności nie powinno być konieczne.

<br>
<img width="630" alt="Screenshot_1" src="https://github.com/user-attachments/assets/4383b39f-f55a-4eb8-8142-34a425474bb3">
