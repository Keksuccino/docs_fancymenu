---
title: Profile
description: >-
  Jak zapisywać, przełączać i udostępniać całe konfiguracje FancyMenu za pomocą
  profili.
sourceBlobSha: d0a07901ee271d802c7bc07ea6d787575f48d51c
---
# Profile

Profil to kompletna konfiguracja FancyMenu: wszystkie układy, zasoby, zmienne i ustawienia FancyMenu danej instancji. Profile pozwalają przechowywać wiele konfiguracji w jednej instancji Minecrafta, przełączać się między nimi w kilka sekund oraz udostępniać je innym jako pojedynczy plik.

<img width="800" alt="profile" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/profiles_showcase.gif?raw=true">

# Otwieranie okna profili

Otwórz okno profili przez **pasek menu -> Dostosowywanie -> Profile**.

Lista po lewej stronie pokazuje wszystkie profile, a po prawej wyświetlane są szczegóły wybranego profilu. Załadowany profil jest oznaczony jako **Aktywny**. Każda zmiana wprowadzona w FancyMenu jest zapisywana bezpośrednio w załadowanym profilu.

Istniejąca konfiguracja automatycznie staje się pierwszym profilem o nazwie **Mój profil**.

> [!TIP]
> Kliknij profil na liście prawym przyciskiem myszy, aby zobaczyć wszystkie dostępne dla niego działania.

# Przełączanie profili

Wybierz profil i kliknij **Załaduj profil** albo kliknij go dwukrotnie. FancyMenu uruchomi się ponownie z wybraną konfiguracją.

> [!NOTE]
> Przełączanie nigdy niczego nie usuwa. Bieżąca konfiguracja zostaje zapisana jako osobny profil przed załadowaniem innego, więc zawsze możesz do niej wrócić.

# Tworzenie profili

- **Nowy profil** (przycisk **+** poniżej listy) tworzy pusty profil i otwiera jego edytor. Puste profile zachowują osobiste ustawienia FancyMenu, takie jak skala interfejsu i motyw.
- **Duplikuj** tworzy kopię wybranego profilu, co jest przydatne podczas testowania zmian bez modyfikowania oryginału.

# Edytowanie profili

Kliknij **Edytuj**, aby zmienić tytuł, wersję, autorów, opis, ikonę, narzędzie do zgłaszania problemów oraz linki profilu. Opis obsługuje Markdown, a ikoną może być dowolny obraz PNG.

Nic nie zostanie zapisane, dopóki nie klikniesz **Gotowe**.

# Udostępnianie profili

> [!CAUTION]
> Profile mogą wykonywać działania. Importuj je wyłącznie z zaufanych źródeł.

## Eksportowanie

Wybierz profil, kliknij **Eksportuj** i wybierz miejsce zapisu. Zostanie utworzony plik `.fmp` zawierający cały profil.

## Importowanie

Kliknij **Importuj** poniżej listy i wybierz plik `.fmp` albo po prostu przeciągnij go i upuść w oknie profili.

- Zaimportowane profile nie są ładowane automatycznie. Załaduj je tak jak każdy inny profil.
- Jeśli masz już ten sam profil (na przykład jego starszą wersję), możesz wybrać **Zastąp** albo **Zachowaj oba**. Zastąpienie załadowanego profilu powoduje natychmiastowe załadowanie zaimportowanej wersji.
- Profile utworzone w nowszej wersji FancyMenu wyświetlają ostrzeżenie, ponieważ niektóre ich elementy mogą nie działać.

## Dodawanie folderów z konfiguracjami

Niektóre konfiguracje są dostarczane jako zwykły folder `fancymenu`, a nie jako plik `.fmp`. Aby dodać taki folder jako profil, zmień jego nazwę na wybraną nazwę profilu, przenieś go do `<game-directory>/config/fancymenu/profiles/` (utwórz folder `profiles`, jeśli jeszcze nie istnieje) i otwórz okno profili. FancyMenu automatycznie doda go do listy profili.

# Usuwanie profili

Wybierz profil i kliknij **Usuń**. Usunięcia nie można cofnąć, dlatego jeśli chcesz zachować kopię zapasową, najpierw wyeksportuj profil.

Załadowanego profilu nie można usunąć. Najpierw załaduj inny profil.

# Gdzie przechowywane są profile

- Załadowany profil zawiera się w `<game-directory>/config/fancymenu/`, tak jak każda konfiguracja FancyMenu.
- Wszystkie pozostałe profile są przechowywane w `<game-directory>/config/fancymenu/profiles/`. Kliknij **Otwórz folder**, aby otworzyć folder profilu.

`<game-directory>` to folder aktywnej instancji, który może różnić się od `.minecraft`. Stan działania przechowywany przez FancyMenu poza `config/fancymenu/` nie jest częścią profili — zobacz [Lokalizacje przechowywania danych](./data-storage-locations#persistent-runtime-state).
