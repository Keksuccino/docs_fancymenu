---
title: Otwieranie GUI za pomocą komendy
description: Jak otwierać standardowe i niestandardowe GUI za pomocą komendy.
---

# Otwieranie GUI za pomocą komendy

Komenda `/openguiscreen` otwiera Vanilla, mody oraz [niestandardowe GUI](./custom-guis). Może być używana do innych graczy, gdy FancyMenu jest zainstalowane na serwerze i na ich klientach.

Aby otworzyć GUI, użyj `/openguiscreen <screen_identifier> [<target_players>]`.

Zastąp `<screen_identifier>` dokładnym, rozróżniającym wielkość liter identyfikatorem niestandardowego GUI lub ekranu Vanilla/moda.

Aby znaleźć identyfikator, otwórz docelowy ekran i włącz nakładkę debugowania za pomocą **CTRL + ALT + D**. Wybierz identyfikator z jego pierwszej linii, aby go skopiować. Zobacz [Identyfikatory ekranów](./screen-identifiers).

![copy_identifier](https://github.com/Keksuccino/FancyMenu/assets/35544624/dd6c53d9-d2bd-4810-be03-3741e326bd5a)

Pomiń `[<target_players>]`, aby otworzyć GUI dla siebie, albo użyj nazwy gracza lub selektora, takiego jak `@a`, aby otworzyć je dla jednego lub więcej graczy. Podanie argumentu celu wymaga poziomu uprawnień 2 (Game Master / OP poziomu 2), nawet jeśli wskazuje na ciebie, a każdy docelowy gracz musi mieć zainstalowane FancyMenu na swoim kliencie.

Nie każdy ekran moda można utworzyć bezpośrednio. FancyMenu wyświetla błąd, gdy docelowy ekran nie jest obsługiwany. W układzie lokalnym użyj [**Mimic Vanilla/Mod Button**](./action-scripts#mimic-vanillamod-button-mimicbutton) na widżecie, który normalnie go otwiera.

# Zamykanie GUI za pomocą komendy

W rzadkich przypadkach, gdy jest to potrzebne, `/closeguiscreen [<target_players>]` zamyka bieżący ekran. Dotyczy ciebie, gdy argument celu jest pominięty; podanie argumentu celu wymaga poziomu uprawnień 2.
