---
title: Dragger
description: >-
  Pozwól graczom chwytać panel, notatkę lub dowolny inny element menu i
  przesuwać go w wybrane miejsce.
sourceBlobSha: 5cfe57388c5b839c5a98045d0086a94df6b4110c
---

# Dragger

Dragger to niewidoczny obszar, który gracze mogą chwycić myszą i przesuwać. Wszystko, co jest do niego zakotwiczone, przesuwa się razem z nim, na przykład panel z informacjami o aktualizacji lub notatka z zasadami serwera. Menu zapamiętuje położenie pozostawione przez graczy — nawet po ponownym uruchomieniu gry.

<img width="800" alt="Gracz chwyta baner z informacjami o aktualizacji za skórzany uchwyt drążka i przesuwa go z lewej strony ekranu tytułowego na prawą, otwiera Opcje, wraca, a baner nadal znajduje się po prawej" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/dragger_hero.gif?raw=true">

Gracze mogą przeciągać Dragger tylko poza edytorem układu. W edytorze Dragger jest czerwonym prostokątem z nazwą (opcja **In-Editor Color** w jego menu kontekstowym, otwieranym prawym przyciskiem myszy, zmienia kolor czerwony), a wszystkie elementy pozostają na miejscach wyznaczonych przez układ.

# Tworzenie ruchomego elementu

<img width="800" alt="Dodawanie elementu Dragger za pomocą opcji New Element, zmiana jego rozmiaru na taki jak baner, przeciągnięcie go na baner i przesunięcie o dwie warstwy niżej, a następnie przeciągnięcie banera poza Dragger i z powrotem oraz przytrzymanie go, aż pasek się zapełni, co zakotwicza baner do Draggera" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/dragger_setup.gif?raw=true">

1. Utwórz element, który ma się przesuwać, na przykład obraz banera z elementem Text.
2. Kliknij prawym przyciskiem myszy wolne miejsce w edytorze układu, a następnie wybierz **New Element -> Dragger**.
3. Ustaw rozmiar Draggera tak, aby odpowiadał rozmiarowi banera, i umieść go na banerze.
4. Kliknij Dragger prawym przyciskiem myszy i wybierz **Move One Layer Down**, aż znajdzie się pod wszystkimi elementami banera. Zaznaczone elementy są zawsze wyświetlane na wierzchu, więc kliknij wolne miejsce, aby zobaczyć zmianę.
5. Zakotwicz baner do Draggera: przeciągnij baner nieco poza Dragger, a potem z powrotem i przytrzymaj, aż pasek się zapełni. Więcej informacji znajdziesz w sekcji [Pozycjonowanie elementów](/positioning-elements#anchoring-elements-to-other-elements).
6. Zapisz układ i przetestuj go poza edytorem.

Elementy zakotwiczone do przesuwanego elementu również przesuwają się razem z nim. Na GIF-ie tekst jest zakotwiczony do banera, więc tylko baner wymaga Draggera.

Aby zakotwiczyć kilka elementów naraz, przed wykonaniem kroku 4 kliknij Dragger prawym przyciskiem myszy i wybierz **Copy Element ID**. Następnie zaznacz elementy, kliknij jeden z nich prawym przyciskiem myszy, wybierz **Anchor Point -> Other Element** i wklej identyfikator.

> [!TIP]
> Gracze nie widzą Draggera, więc pokaż im, gdzie mogą chwycić element, na przykład za pomocą paska tytułu lub uchwytu.

# Zapisywanie położenia

Opcja **Save User Drag Offset** w menu kontekstowym Draggera jest domyślnie włączona dla nowych elementów Dragger.

- **Włączona**: położenie jest zapisywane, gdy gracz puści element. Pozostaje zapisane po zamknięciu ekranu i ponownym uruchomieniu gry.
- **Wyłączona**: po ponownym otwarciu ekranu, zmianie rozmiaru okna lub skali interfejsu wszystkie elementy wracają na miejsca wyznaczone w układzie.

Wyłączenie tej opcji w edytorze powoduje również usunięcie zapisanego przez gracza położenia tego Draggera.

Położenie każdego Draggera jest zapisywane na podstawie jego [identyfikatora elementu](/element-identifiers) w pliku `fancymenu_data/dragger_metas.json`. Ten folder nie należy do [profili](/profiles), więc położenia ustawione podczas testów nie trafiają do folderu `config/fancymenu/` w paczce modów. Zobacz [Lokalizacje przechowywania danych](/data-storage-locations#instance-data).

Aby przywrócić położenia wszystkich Draggerów z układu, usuń plik `dragger_metas.json`, gdy gra jest zamknięta.

# Co gracze mogą chwytać

Gracze chwytają Dragger w miejscach, w których żaden element znajdujący się nad nim nie przechwytuje kliknięcia:

- Obrazy umieszczone nad Draggerem przepuszczają kliknięcia, więc gracze chwytają sam baner.
- Przyciski i tekst elementów Text umieszczonych nad Draggerem przechwytują kliknięcia, dzięki czemu nadal działają na ruchomym panelu.
- W miejscach, gdzie Dragger znajduje się nad przyciskiem, kliknięcia przycisku nie są rejestrowane. Dlatego w powyższych krokach Dragger umieszcza się pod banerem.

Gdy [wymagania](/element-visibility#showing-elements-only-sometimes) ukrywają Dragger, gracze nie mogą go chwycić.

# Pozostawanie na ekranie

Opcja **Stay on Screen** jest domyślnie włączona dla nowych elementów. Zatrzymuje Dragger na krawędziach ekranu, aby gracze nie mogli przeciągnąć go poza widoczny obszar. Jeśli Dragger ma taki sam rozmiar jak cały baner, baner również zatrzyma się przy krawędzi.

Dragger może też obejmować tylko część elementu, na przykład pasek tytułu. Jednak zakotwiczone do niego elementy mają własne ustawienie **Stay on Screen**: przy krawędzi zatrzymują się samodzielnie, podczas gdy Dragger przesuwa się dalej, przez co panel się rozpada. Wyłącz **Stay on Screen** dla tych elementów, aby przesuwały się razem z Draggerem i tylko pasek tytułu pozostawał na ekranie.
