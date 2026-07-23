---
title: Niestandardowe GUI
description: Twórz i konfiguruj nowe ekrany GUI.
---
# Niestandardowe GUI

Niestandardowe GUI to nowe ekrany, które możesz wypełniać [elementami](./elements) FancyMenu.

> [!CAUTION]
> Niestandardowe GUI mogą uruchamiać działania. Importuj je tylko z zaufanych źródeł.

# Tworzenie niestandardowego GUI

1. Otwórz **Dostosowywanie -> Niestandardowe GUI -> Zarządzaj niestandardowymi GUI**.
2. Wybierz **Nowe GUI**.
3. Wpisz identyfikator i skonfiguruj ustawienia ekranu.
4. Wybierz **Gotowe**, a następnie otwórz nowe GUI z menedżera.
5. Utwórz jego układ i edytuj go tak jak każdy inny ekran.

Identyfikatory mogą zawierać małe litery, cyfry, `.`, `_` i `-`. Nie mogą zawierać spacji i muszą być unikalne. Pustych, nieprawidłowych ani zduplikowanych identyfikatorów nie można zapisać.

Niestandardowe GUI zawsze mają włączone dostosowywanie ekranu; ich przełącznika dostosowywania nie można wyłączyć.

# Ustawienia ekranu

| Ustawienie | Działanie |
|---|---|
| Zezwól na ESC | Pozwala klawiszowi Escape zamknąć GUI i wrócić do nadrzędnego ekranu |
| Wstrzymaj grę/świat | Wstrzymuje grę w trybie jednego gracza, gdy GUI jest otwarte |
| Renderuj tło świata | Pokazuje załadowany świat za GUI |
| Nakładka tła świata | Dodaje standardowe rozmycie/ciemną nakładkę na świat |
| Tryb wyskakujący | Utrzymuje nadrzędny ekran widoczny za niestandardowym GUI |
| Nakładka tła wyskakującego okna | Dodaje rozmycie/kolorową nakładkę na nadrzędny ekran w trybie wyskakującym |

Tryb wyskakujący nie łączy obu ekranów. Niestandardowe GUI pozostaje aktywnym ekranem, podczas gdy jego ekran nadrzędny jest renderowany za nim. Zamknięcie niestandardowego GUI wraca do tego nadrzędnego ekranu, jeśli istnieje.

# Otwieranie niestandardowego GUI

Użyj dokładnego identyfikatora niestandardowego GUI z jedną z tych opcji:

- [**Akcja Otwórz ekran lub niestandardowe GUI**](./action-scripts#open-screen-or-custom-gui-opengui).
- [Komenda `/openguiscreen`](./commands#openguiscreen).

# Zastępowanie istniejącego ekranu

Niestandardowe GUI może zastąpić ekran Vanilla lub modu za każdym razem, gdy ten ekran się otwiera.

1. Utwórz niestandardowe GUI zastępujące ekran.
2. Otwórz ekran, który chcesz zastąpić.
3. Włącz **Dostosowywanie -> Ustawienia -> Zaawansowany tryb dostosowywania**.
4. Wybierz **Dostosowywanie -> Niestandardowe GUI -> Zastąp bieżący ekran niestandardowym GUI**.
5. Wybierz niestandardowe GUI zastępujące ekran.

Zarządzaj zapisanymi zastąpieniami przez **Dostosowywanie -> Niestandardowe GUI -> Zarządzaj zastąpionymi ekranami**.

Zastąpienie pomija oryginalny ekran, więc przetestuj jego nawigację oraz wszystkie funkcje zależne od zachowania oryginalnego ekranu.
