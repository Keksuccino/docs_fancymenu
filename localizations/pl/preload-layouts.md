---
title: Wstępne ładowanie zasobów
description: 'Jak wstępnie ładować zasoby, aby były gotowe do użycia po załadowaniu gry.'
sourceBlobSha: 8eca400e05987468c1fd0dc29faa5267083e38d0
---

# Wstępne ładowanie zasobów

Wstępne ładowanie przygotowuje wybrane zasoby, zanim będą potrzebne w menu. Użyj go w przypadku zasobów, które w przeciwnym razie migają, wyświetlają czarną pierwszą klatkę lub ładują się z opóźnieniem.

# Dodawanie zasobów do wstępnego ładowania

Otwórz **Dostosowywanie -> Wstępne ładowanie zasobów**.

<br>

<img width="350" alt="Screenshot_1" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/3265da80-1bbc-4634-bd94-ba2795d7e3f2">

Lista obsługuje obrazy, animacje, dźwięki, wideo i zasoby tekstowe z plików lokalnych, adresów URL lub paczek zasobów. Nie wstępnie ładuje aktywnych stron [Przeglądarki](/elements#browser).

Wstępne ładowanie rozpoczyna się podczas uruchamiania gry i ponownego ładowania zasobów Minecrafta. Przed przejściem do kolejnego wpisu mechanizm czeka, aż ładowanie bieżącego zasobu się zakończy lub nie powiedzie. Na każdy wpis przypada maksymalnie dwie minuty.

Załadowane zasoby pozostają w pamięci podręcznej, dopóki FancyMenu nie zwolni ich podczas ponownego ładowania zasobów lub zamykania klienta. Opcja **Dostosowywanie -> Przeładuj FancyMenu** zwalnia pamięć podręczną, ale nie uruchamia ponownie wstępnego ładowania.

Wstępne ładowanie wydłuża czas ładowania i zwiększa zużycie pamięci RAM/VRAM. Dodawaj tylko zasoby, które muszą być dostępne natychmiast; usuń duże wpisy, jeśli klientowi brakuje pamięci.

<br>

<img width="731" alt="Screenshot_2" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/04632d52-c2a9-4f70-9d0a-e88c4cacc4c1">

# Wstępne ładowanie pokazów slajdów i panoram

Dodanie [pokazu slajdów](/slideshows) ładuje wszystkie jego obrazy i opcjonalną nakładkę. Dodanie [panoramy](/panoramas) ładuje wszystkie sześć ścian oraz opcjonalną nakładkę.

Opcja **Dostosowywanie -> Przeładuj FancyMenu** nie uruchamia wstępnego ładowania. Po zmianie listy zasobów do wstępnego ładowania ponownie załaduj zasoby Minecrafta lub uruchom grę ponownie.
