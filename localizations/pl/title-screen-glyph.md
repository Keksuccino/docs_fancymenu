---
title: Glyf ekranu tytułowego
description: >-
  Jak ukryć/usunąć mały diament lub szmaragd (zieloną albo niebieską) ikonę/glyf
  na ekranie tytułowym.
---

# Ikona szmaragdu/diamentu na ekranie tytułowym

Jeśli masz problem z ukryciem małej ikony, która pojawia się na ekranie tytułowym i wygląda jak mały diament albo szmaragd (mała zielona lub niebieska ikonka), to najczęściej jest to powiadomienie o aktualizacji z moda Mod Menu (mod Fabric) albo z Forge (wbudowana funkcja modułu ładującego mody).

W niektórych przypadkach może to też być część przycisku Minecraft Realms w wersji Vanilla (służąca do wyświetlania powiadomień).

# Ukrywanie ikony Mod Menu

Aby ukryć glyf z Mod Menu, musisz wyłączyć „wskaźnik aktualizacji” w jego ustawieniach.

Kliknij przycisk **Mods** -> Najedź kursorem na ikonę moda Mod Menu na liście modów -> Kliknij ją -> Ustaw „Update Indicator” na „Hidden”.

# Ukrywanie ikony Forge

Forge używa wbudowanego sprawdzania wersji, aby wyświetlać ikonę szmaragdu, gdy mody są nieaktualne. Możesz to wyłączyć:

1. Otwórz plik konfiguracyjny `config/fml.toml`.
2. Znajdź ustawienie `versionCheck`.
3. Ustaw je na `false`: `versionCheck = false`
4. Zapisz plik i uruchom Minecrafta ponownie.

Spowoduje to całkowite wyłączenie sprawdzania wersji, co również ukryje glyf szmaragdu przy uruchamianiu.

Innym sposobem na ukrycie ikony jest po prostu ukrycie całego przycisku Mods za pomocą FancyMenu. Ukrycie przycisku spowoduje też ukrycie glyfu.

# Ukrywanie ikon Vanilla Realms

Jeśli to nie jest ani glyf z Mod Menu, ani z Forge, to prawdopodobnie są to własne ikony powiadomień Realms w Minecraft. Ikony te pojawiają się mniej więcej w miejscu przycisku Realms i można je ukryć za pomocą FancyMenu w edytorze układu. Musisz utworzyć układ „dla bieżącego ekranu” (w tym przypadku ekran tytułowy), a następnie zobaczysz ikony Realms jako osobny element w edytorze. Aby je ukryć, po prostu **kliknij je prawym przyciskiem myszy** i wybierz **Delete**.

Ikony Realms mogą mieć postać ikony gazety, glyfu diamentu i innych, na przykład czerwonego kółka z licznikiem powiadomień.
