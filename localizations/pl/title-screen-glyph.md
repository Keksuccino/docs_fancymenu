---
title: Glif ekranu tytułowego
description: >-
  Jak ukryć/usunąć mały diament lub szmaragdowy (zielony albo niebieski)
  glif/ikonę na ekranie tytułowym.
---
# Ikona szmaragdu/diamentu na ekranie tytułowym

Jeśli masz problem z ukryciem małej ikony, która ciągle pojawia się na ekranie tytułowym i wygląda jak mały diament albo szmaragd (mała zielona lub niebieska ikonka), to najczęściej jest to powiadomienie o aktualizacji moda Mod Menu (mod Fabric) albo Forge (wbudowana funkcja modloadera).

W niektórych przypadkach może to być również element wbudowanego przycisku Realms w Vanilla Minecraft (pokazuje powiadomienia).

# Ukrywanie ikony Mod Menu

Aby ukryć glif z Mod Menu, musisz wyłączyć „wskaźnik aktualizacji” w jego ustawieniach.

Kliknij przycisk **Mods** -> najedź kursorem na ikonę moda Mod Menu na liście modów -> kliknij ją -> ustaw „Update Indicator” na „Hidden”.

# Ukrywanie ikony Forge

Forge używa wbudowanego sprawdzania wersji, aby pokazać tę szmaragdową ikonę, gdy mody są nieaktualne. Możesz to wyłączyć:

1. Otwórz plik `/config/fml.toml`.
2. Znajdź ustawienie `versionCheck`.
3. Ustaw je na `false`: `versionCheck = false`
4. Zapisz plik i uruchom ponownie Minecrafta.

Spowoduje to całkowite wyłączenie sprawdzania wersji, co ukryje również szmaragdowy glif przy uruchamianiu.

Innym sposobem ukrycia ikony jest po prostu ukrycie całego przycisku Mods za pomocą FancyMenu. Ukrycie przycisku spowoduje też ukrycie glifu.

# Ukrywanie ikony NeoForge

W przypadku NeoForge działa to dokładnie tak samo jak w klasycznym Forge.

1. Otwórz plik `/config/fml.toml`.
2. Znajdź ustawienie `versionCheck`.
3. Ustaw je na `false`: `versionCheck = false`
4. Zapisz plik i uruchom ponownie Minecrafta.

# Ukrywanie ikon Realms Vanilla

Jeśli to nie jest ani glif Mod Menu, ani Forge, to prawdopodobnie są to własne ikony powiadomień Realms w Minecraft. Ikony te pojawiają się mniej więcej w miejscu przycisku Realms i można je ukryć za pomocą FancyMenu w edytorze układu. Musisz utworzyć układ „dla bieżącego ekranu” (w tym przypadku ekranu tytułowego), a następnie zobaczysz ikony Realms jako osobny element w edytorze. Aby je ukryć, po prostu **kliknij je prawym przyciskiem myszy** i wybierz **Delete**.

Ikony Realms mogą mieć formę ikony gazety, glifu diamentu i innych, na przykład czerwonego kółka z licznikiem powiadomień.
