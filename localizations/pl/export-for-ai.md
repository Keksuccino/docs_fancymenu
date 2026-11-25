---
title: Eksport dla AI
description: >-
  Zamień wybrane części konfiguracji FancyMenu na tekst dla asystentów AI,
  takich jak Alice, aby mogli szybciej Ci pomóc.
sourceBlobSha: 37ce2fdd6cf8d770ca3f6f31528ac6076fe46922
---
# Eksport dla AI

**Eksport dla AI** zamienia wybraną część konfiguracji FancyMenu na tekst przygotowany z myślą o asystentach AI, takich jak Alice — botka pomagająca na [Discordzie FancyMenu](https://discord.gg/rhayah27GC). Wklej go na czacie, a AI zobaczy dokładną konfigurację zamiast zgadywać.

<img width="800" alt="Wpis na Discordzie z prośbą Alice o eksport; Alice znajduje w nim problem i pomaga graczowi naprawić przycisk" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/export_for_ai_chat.gif?raw=true">

# Dlaczego powstała ta funkcja

Zrzut ekranu pokazuje, jak coś wygląda, ale nie wyjaśnia, jak jest skonfigurowane. Ręczne przepisywanie skryptu akcji lub wymagania zajmuje dużo czasu, a po drodze często umyka właśnie ten szczegół, który ma znaczenie.

Eksport zawiera wszystkie informacje potrzebne AI:

- Wszystkie ustawienia, akcje, wymagania i wartości eksportowanego elementu.
- Wersje FancyMenu, Minecrafta, programu ładującego mody, Javy i systemu.
- Krótkie objaśnienia działania FancyMenu, dzięki którym AI prawidłowo odczyta eksport.

Eksporty są zawsze po angielsku, niezależnie od języka gry. Nazwa konta w ścieżkach do plików jest zastępowana tekstem `<user>`, więc możesz udostępniać eksporty na publicznych czatach.

# Kiedy warto z tego skorzystać

- Coś nie działa tak, jak powinno, na przykład przycisk nie reaguje albo element nigdy się nie wyświetla.
- FancyMenu pokazuje błąd lub ostrzeżenie.
- Chcesz uzyskać pomoc w stworzeniu czegoś, na przykład skryptu akcji, wymagania lub całego menu.
- Chcesz sprawdzić, co możesz zrobić w grze. **Wszystko, co potrafi FancyMenu** zawiera listę wszystkich dostępnych elementów, teł, akcji, wymagań, symboli zastępczych i nasłuchiwaczy, w tym tych dodawanych przez dodatki.

Eksportuj tylko to, czego dotyczy Twoje pytanie, na przykład jeden niedziałający przycisk. Mniejsze eksporty pomagają AI skupić się na problemie. Następnie opisz, czego się spodziewałeś i co się stało.

# Jak wyeksportować dane

Każda z poniższych opcji otwiera niewielkie menu:

- **Kopiuj do schowka** kopiuje eksport, dzięki czemu możesz wkleić go na czacie za pomocą `Ctrl + V` (`Cmd + V` w systemie macOS).
- **Zapisz jako plik** zapisuje eksport jako plik Markdown w lokalizacji `<game-directory>/fancymenu_data/ai_exports/` i otwiera ten folder, aby można było przeciągnąć plik na czat. Użyj tej opcji w przypadku dużych eksportów, które nie mieszczą się w wiadomości.

Eksporty z edytora układów oraz okien nasłuchiwaczy i harmonogramów uwzględniają także niezapisane zmiany.

# Gdzie można wyeksportować dane

## Pasek menu

| Co zostanie wyeksportowane | Gdzie to znaleźć |
|---|---|
| Bieżący ekran, jego widżety oraz działanie FancyMenu na tym ekranie | **pasek menu -> Customization -> Export Current Screen for AI** |
| Układ | **pasek menu -> Customization -> Layouts**, wybierz układ, a następnie **Export Layout for AI** |
| Informacje o grze, sprzęcie i modach oraz dostępne funkcje FancyMenu, takie jak obsługa wideo i przeglądarki | **pasek menu -> Help -> Export for AI -> System Info** |
| Wszystkie ustawienia FancyMenu, w tym [ustawienia globalne](/global-customizations) | **pasek menu -> Help -> Export for AI -> FancyMenu Settings** |
| Wszystkie [zmienne](/variables) | **pasek menu -> Help -> Export for AI -> All Variables** |
| Wszyscy [nasłuchiwacze](/listeners) | **pasek menu -> Help -> Export for AI -> All Listeners** |
| Wszystkie [harmonogramy](/schedulers) | **pasek menu -> Help -> Export for AI -> All Schedulers** |
| Wszystkie [niestandardowe interfejsy GUI](/custom-guis) | **pasek menu -> Help -> Export for AI -> Custom GUIs** |
| Wszystkie [profile](/profiles) | **pasek menu -> Help -> Export for AI -> Profiles** |
| Wszystkie elementy, tła, akcje, wymagania, symbole zastępcze i nasłuchiwacze dostępne w grze | **pasek menu -> Help -> Export for AI -> Everything FancyMenu Can Do** |

## Edytor układów

| Co zostanie wyeksportowane | Gdzie to znaleźć |
|---|---|
| Edytowany układ | **Layout -> Export Layout for AI** na pasku menu edytora |
| Inny układ ekranu | **Layout -> Open** na pasku menu edytora, wybierz układ, a następnie **Export Layout for AI** |
| Jeden element | Kliknij element prawym przyciskiem myszy, a następnie wybierz **Export for AI** |
| Wszystkie zaznaczone elementy | **Edit -> Export Selected Elements for AI** na pasku menu edytora |
| [Tło menu](/menu-backgrounds) | Kliknij prawym przyciskiem myszy tło edytora, wybierz **Menu Backgrounds**, wskaż tło, a następnie wybierz **Export for AI** |
| [Nakładka dekoracyjna](/decoration-overlays) | Kliknij prawym przyciskiem myszy tło edytora, wybierz **Decoration Overlays**, wskaż nakładkę, a następnie wybierz **Export for AI** |

## Edytory i okna

| Co zostanie wyeksportowane | Gdzie to znaleźć |
|---|---|
| [Skrypt akcji](/action-scripts) | Kliknij prawym przyciskiem myszy w edytorze skryptów akcji, a następnie wybierz **Export Action Script for AI** |
| [Wymagania](/conditions) | Kliknij prawym przyciskiem myszy w oknie **Manage Requirements**, a następnie wybierz **Export Requirements for AI** |
| Tekst, na przykład treść elementu tekstowego | Kliknij prawym przyciskiem myszy w edytorze tekstu, a następnie wybierz **Export Text for AI** |
| Jedna zmienna lub wszystkie zmienne | Otwórz **pasek menu -> Customization -> Manage Variables**, kliknij prawym przyciskiem myszy, a następnie wybierz **Export Variable for AI** lub **Export All Variables for AI** |
| Jeden nasłuchiwacz lub wszyscy nasłuchiwacze | Otwórz **pasek menu -> Customization -> Manage Listeners**, kliknij **Export for AI**, a następnie wybierz **Selected Listener** lub **All Listeners** |
| Jeden harmonogram lub wszystkie harmonogramy | Otwórz **pasek menu -> Customization -> Manage Schedulers**, kliknij **Export for AI**, a następnie wybierz **Selected Scheduler** lub **All Schedulers** |

## Błędy i ostrzeżenia

Gdy FancyMenu wyświetli błąd lub ostrzeżenie, kliknij **Export for AI** obok **OK**, aby wyeksportować komunikat.

## Serwery

Konfigurację [FMData](/fm-data) na serwerze, wraz z nasłuchiwaczami serwera i danymi powitalnymi, można wyeksportować za pomocą polecenia. Wymagany jest poziom uprawnień 2 — tak samo jak w przypadku wszystkich poleceń `/fmdata`.

```mcfunction
/fmdata export_for_ai copy
/fmdata export_for_ai file
```

- `copy` wysyła wiadomość na czat. Kliknij ją, aby skopiować eksport. W konsoli serwera wyświetlany jest cały eksport.
- `file` zapisuje eksport na serwerze w folderze `fancymenu_data/ai_exports/`. Użyj tej opcji, gdy eksport jest zbyt duży, by wysłać go na czacie.
