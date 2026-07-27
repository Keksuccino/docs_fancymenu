---
title: Wstępne ładowanie zasobów
description: >-
  Jak wstępnie ładować zasoby, aby były gotowe do użycia zaraz po zakończeniu
  ładowania gry.
---

# Wstępne ładowanie zasobów

Wstępne ładowanie przygotowuje wybrane zasoby, zanim menu będzie ich potrzebować. Używaj go dla zasobów, które inaczej migoczą, pokazują czarną pierwszą klatkę albo uruchamiają się z opóźnieniem.

# Dodawanie zasobów do wstępnego ładowania

Otwórz **Dostosowanie -> Wstępne ładowanie zasobów**.

<br>

<img width="350" alt="Screenshot_1" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/3265da80-1bbc-4634-bd94-ba2795d7e3f2">

Lista obsługuje pliki graficzne, animacje, audio, wideo i zasoby tekstowe z plików lokalnych, adresów URL lub paczek zasobów. Nie wczytuje wstępnie aktywnej strony [Przeglądarki](./elements#browser).

Wstępne ładowanie rozpoczyna się podczas uruchamiania gry oraz odświeżania zasobów Minecrafta. Czeka, aż każdy wpis zakończy się powodzeniem lub błędem, zanim przejdzie dalej, z limitem dwóch minut na wpis.

Załadowane zasoby pozostają w pamięci podręcznej, dopóki FancyMenu nie zwolni zasobów podczas odświeżania lub zamykania klienta. **Dostosowanie -> Przeładuj FancyMenu** zwalnia pamięć podręczną, ale nie uruchamia ponownie wstępnego ładowania.

Wstępne ładowanie wydłuża czas ładowania oraz zużycie RAM/VRAM. Dodawaj tylko te zasoby, które muszą być dostępne natychmiast; usuń duże wpisy, jeśli klientowi kończy się pamięć.

<br>

<img width="731" alt="Screenshot_2" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/04632d52-c2a9-4f70-9d0a-e88c4cacc4c1">

# Wstępne ładowanie pokazów slajdów i panoram

Dodanie [pokazu slajdów](./slideshows) ładuje wszystkie jego obrazy oraz opcjonalną nakładkę. Dodanie [panoramy](./panoramas) ładuje wszystkie sześć ścian oraz jej opcjonalną nakładkę.

**Dostosowanie -> Przeładuj FancyMenu** nie uruchamia wstępnego ładowania. Po zmianie listy wstępnego ładowania użyj odświeżenia zasobów Minecrafta albo uruchom grę ponownie.
