---
title: Paczki modów
description: Jak dołączyć układy do paczki modów.
sourceBlobSha: c19df01d8e726bbff6c9d1d147287ada5d1773eb
---

# FancyMenu w paczkach modów

Dołączenie konfiguracji FancyMenu do paczki modów jest bardzo łatwe i wymaga tylko kilku prostych kroków.

> [!CAUTION]
> Konfiguracje FancyMenu mogą wykonywać akcje. Importuj je tylko z zaufanych źródeł.

> [!WARNING]
> Ta strona dotyczy **TYLKO** konfiguracji FancyMenu utworzonych w całości w **FancyMenu v3+**. Jeśli więc używasz starszej konfiguracji (utworzonej w v2 i przekonwertowanej do v3), niektóre kroki mogą wyglądać inaczej.

# Przenoszenie konfiguracji do paczki modów

Najłatwiejszym sposobem przeniesienia konfiguracji z instancji, w której została utworzona, do instancji paczki modów jest użycie [profilu](/profiles):

1. W instancji z Twoją konfiguracją otwórz **pasek menu -> Personalizacja -> Profile**, wybierz swoją konfigurację i [wyeksportuj ją](/profiles#exporting) jako plik `.fmp`.
2. W instancji paczki modów otwórz okno Profile i [zaimportuj](/profiles#importing) plik `.fmp`, na przykład przeciągając go do okna.
3. Wybierz zaimportowany profil i kliknij **Załaduj profil**.

Konfiguracja FancyMenu, która była wcześniej używana w instancji paczki modów, nie zostanie utracona. Pozostanie dostępna jako osobny profil, więc zawsze możesz do niej wrócić.

# Dołączanie konfiguracji do paczki modów

Załadowany profil znajduje się w `<game-directory>/config/fancymenu/`, więc jest dołączany do folderu `config` paczki modów, podobnie jak konfiguracje innych modów.

Wszystkie pozostałe profile instancji są przechowywane w `<game-directory>/config/fancymenu/profiles/`. Przed wyeksportowaniem paczki modów usuń profile, których gracze nie powinni otrzymać, albo pomiń folder `profiles` podczas eksportowania paczki.

> [!CAUTION]
> Pamiętaj, że starsze konfiguracje utworzone w FancyMenu v2 (nawet po przekonwertowaniu do v3) umożliwiały przechowywanie zasobów układów poza folderem `<game-directory>/config/fancymenu/assets/` FancyMenu. Profile zawierają tylko folder konfiguracyjny FancyMenu, więc w takim przypadku musisz dopilnować, aby do paczki modów dołączyć również wszystkie zasoby.

## Resetowanie pól wyboru przed eksportem

[Pola wyboru](/elements#checkbox) zapamiętują swój stan w pliku `config/fancymenu/checkbox_states.json`. Oznacza to, że pola kliknięte podczas testowania będą zaznaczone również u Twoich graczy.

Aby gracze mogli zacząć od zera, zamknij grę i usuń plik `checkbox_states.json` przed wyeksportowaniem paczki modów lub profilu. Jeśli pliku nie ma, wszystkie pola wyboru będą początkowo odznaczone. Pola wyboru korzystające ze [zmiennej](/variables) przechowują swój stan w tej zmiennej.

To samo dotyczy zmian wprowadzonych podczas testowania przez akcje, na przykład głośności [elementów wideo](/video). Pliki te opisano w sekcji [Lokalizacje przechowywania danych](/data-storage-locations#your-setup).

## Jak znaleźć folder instancji

Folder instancji to główny folder na komputerze, w którym przechowywane są wszystkie pliki konkretnej konfiguracji Minecrafta. Launchery takie jak CurseForge i Modrinth nazywają je „instancjami” lub „profilami” (nie należy ich mylić z profilami FancyMenu).

### Jeśli używasz aplikacji CurseForge

1. Otwórz CurseForge.
2. Znajdź na liście swój profil/instancję Minecrafta i otwórz go.
3. Kliknij trzy kropki.
4. Wybierz „Otwórz folder”. Otworzy się główny folder tej instancji Minecrafta.

<img width="630" alt="Screenshot_1" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/curseforge_launcher_instance.png">

### Jeśli używasz aplikacji Modrinth

1. Otwórz aplikację Modrinth.
2. Znajdź na liście swój profil/instancję Minecrafta i otwórz go.
3. Kliknij trzy kropki.
4. Wybierz „Otwórz folder”. Otworzy się główny folder tej instancji Minecrafta.

<img width="630" alt="Screenshot_1" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/modrinth_launcher_instance.png">

### Inne launchery

Poszukaj podobnej opcji, takiej jak „Otwórz folder”, „Otwórz folder instancji” lub „Wyświetl pliki”, dostępnej dla Twojej konfiguracji Minecrafta.

# Wyłączanie paska menu i skrótów klawiszowych

Pasek menu FancyMenu nie powinien być widoczny w Twojej paczce modów, więc należy go wyłączyć. Ponieważ gracze nadal mogliby użyć skrótu klawiszowego, aby ponownie go wyświetlić, zastosujmy nieco bardziej *radykalne* rozwiązanie.

Przejdź do `<game-directory>/config/fancymenu/options.txt` i otwórz plik w edytorze tekstu.

Ustaw `modpack_mode` na `true` i zapisz plik.
Spowoduje to całkowite wyłączenie wszystkich nakładek i skrótów klawiszowych.

Aby znów móc edytować układy, ustaw tę opcję w konfiguracji z powrotem na `false`.

# Wyłączanie ekranu powitalnego

W większości przypadków nie powinno to być konieczne. Jeśli jednak ekran powitalny (zachęcający do przeczytania dokumentacji) nie został jeszcze zamknięty, ustaw `show_welcome_screen` na `false` w pliku `<game-directory>/config/fancymenu/options.txt`.

Ekran wyświetla się tylko raz i wyłącza po kliknięciu przycisku **Otwórz dokumentację**, więc w większości przypadków ręczna zmiana tego ustawienia nie powinna być potrzebna.

<br>
<img width="630" alt="Screenshot_1" src="https://github.com/user-attachments/assets/4383b39f-f55a-4eb8-8142-34a425474bb3">
