---
title: Otwieranie GUI za pomocą komendy
description: Jak otwierać podstawowe i niestandardowe GUI za pomocą komendy.
sourceBlobSha: 9d0c8fbc3fa1d1cb15dc19e94f1f0fc1ba37ae05
---

# Otwieranie GUI za pomocą komendy

Komenda `/openguiscreen` otwiera podstawowe GUI, GUI modów oraz [niestandardowe GUI](/custom-guis). Jeśli FancyMenu jest zainstalowane na serwerze i u graczy, można wskazać innych graczy jako odbiorców.

Aby otworzyć GUI, użyj `/openguiscreen <screen_identifier> [<target_players>]`.

Zastąp `<screen_identifier>` dokładnym identyfikatorem niestandardowego GUI lub podstawowego ekranu/modu. Wielkość liter ma znaczenie.

Aby znaleźć identyfikator, otwórz docelowy ekran i włącz nakładkę debugowania skrótem **CTRL + ALT + D**. Zaznacz identyfikator w pierwszym wierszu, aby go skopiować. Zobacz [Identyfikatory ekranów](/screen-identifiers).

![copy_identifier](https://github.com/Keksuccino/FancyMenu/assets/35544624/dd6c53d9-d2bd-4810-be03-3741e326bd5a)

Pomiń `[<target_players>]`, aby otworzyć GUI dla siebie. Możesz też podać nazwę gracza lub selektor, taki jak `@a`, aby otworzyć je dla jednego lub większej liczby graczy. Podanie argumentu docelowego wymaga poziomu uprawnień 2 (Mistrz Gry / poziom OP 2), nawet jeśli wskazujesz siebie. Każdy gracz docelowy musi mieć zainstalowane FancyMenu.

Nie każdy ekran moda można utworzyć bezpośrednio. Jeśli docelowy ekran nie jest obsługiwany, FancyMenu wyświetli błąd. W lokalnym układzie użyj opcji [**Naśladuj przycisk podstawowy/modu**](/action-scripts#mimic-vanillamod-button) na widżecie, który normalnie otwiera ten ekran.

# Zamykanie GUI za pomocą komendy

W rzadkich przypadkach możesz użyć komendy `/closeguiscreen [<target_players>]`, aby zamknąć bieżący ekran. Jeśli pominiesz argument docelowy, komenda zadziała na ciebie. Podanie argumentu docelowego wymaga poziomu uprawnień 2.
