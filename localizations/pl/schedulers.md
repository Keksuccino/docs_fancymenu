---
title: Harmonogramy
description: 'Uruchamiaj skrypty akcji FancyMenu na timerze, nawet w tle.'
---

# Harmonogramy

Harmonogramy uruchamiają skrypt akcji na timerze.

Są globalne (nie są przypisane do jednego konkretnego ekranu), więc mogą działać nawet wtedy, gdy nie jest otwarte żadne GUI.

Używaj harmonogramów, gdy chcesz automatyzacji rozłożonej w czasie, zamiast jednorazowej akcji.
Są przydatne do powtarzalnych zadań, opóźnionych działań i logiki działającej w tle.

Typowe przykłady:

- Aktualizowanie zmiennych lub elementów tekstowych co kilka sekund (na przykład własny zegar/wyświetlacz statusu).
- Uruchamianie okresowych sprawdzeń i wyzwalanie akcji, gdy spełnione są warunki.
- Start efektów menu, dźwięków lub innego skryptowego zachowania w zapętlonym rytmie czasowym.
- Opóźnienie akcji i uruchomienie jej później bez konieczności utrzymywania otwartego ekranu.

# Gdzie je znaleźć

Otwórz **pasek menu** FancyMenu, gdy **nie** jesteś w edytorze układu, a następnie wybierz **Customization -> Manage Schedulers**.

# Szybki start

1. Otwórz **Customization -> Manage Schedulers**.
2. Kliknij **Add Scheduler**.
3. Zbuduj **Action Script** harmonogramu (to on uruchamia się raz na każdy tick harmonogramu).
4. Zaznacz harmonogram i kliknij **Edit Settings**.
5. Skonfiguruj:
   - **Scheduler ID** (unikalna nazwa harmonogramu; używana przez akcje Start/Stop oraz wymagania; dozwolone: `a-z`, `0-9`, `.`, `_`, `-`)
   - **Start Delay (ms)** (czas oczekiwania przed uruchomieniem pierwszego ticka)
   - **Tick Delay (ms)** (czas oczekiwania między tickami; `0` = co każdy tick gry)
   - **Ticks to Run** (ile ticków ma zostać wykonanych przed automatycznym zatrzymaniem; `0` = bezterminowo)
   - **Start on Launch** (automatycznie uruchamia ten harmonogram po załadowaniu FancyMenu)
6. Użyj **Start Now**, aby uruchomić go od razu.
7. Użyj **Stop Now**, aby go zatrzymać.

# Sterowanie i obserwacja harmonogramów

Istnieją akcje i wymagania służące do sterowania harmonogramami oraz sprawdzania ich stanu uruchomienia.

## Akcje

- **Start Scheduler** przyjmuje ID harmonogramu i uruchamia go, jeśli nie jest jeszcze aktywny.
- **Stop Scheduler** również przyjmuje ID harmonogramu i go zatrzymuje.

## Wymaganie

Aby sprawdzić, czy harmonogram jest obecnie uruchomiony, użyj wymagania **Scheduler Is Running**, które przyjmuje ID harmonogramu.

# Wskazówki

1. Używaj czytelnych ID, takich jak `hud_update`, `menu_animation`, `music_fade`.
2. Zacznij od większego opóźnienia ticków (na przykład `200`-`1000` ms), a potem zmniejszaj je tylko jeśli to konieczne, aby oszczędzać wydajność.
3. Na liście harmonogramów kliknij harmonogram prawym przyciskiem myszy, aby szybko edytować jego akcje.
4. Na liście harmonogramów kliknij dwukrotnie ID harmonogramu, aby zmienić jego nazwę.
