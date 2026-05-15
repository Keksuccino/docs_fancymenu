---
title: Ustawianie/Pobieranie opcji Minecrafta
description: >-
  Jak ustawiać i odczytywać opcje Minecrafta, takie jak głośność, FOV, render
  distance itp.
---

# Praca z opcjami Minecrafta w FancyMenu

FancyMenu pozwala odczytywać i ustawiać ustawienia gry Minecraft (opcje) za pomocą różnych elementów interfejsu. Ten przewodnik pokaże, jak używać przycisków, suwaków i tickerów do pracy z opcjami Minecrafta w niestandardowych układach menu.

# Zrozumienie opcji Minecrafta

Minecraft ma wiele wbudowanych opcji, które kontrolują wszystko — od ustawień grafiki po głośność dźwięku. FancyMenu pozwala uzyskiwać dostęp do tych opcji po ich nazwach.

Niektóre popularne nazwy opcji to:
- `soundCategory_master` - Główna głośność
- `soundCategory_music` - Głośność muzyki
- `soundCategory_ambient` - Głośność dźwięków otoczenia
- `soundCategory_players` - Głośność dźwięków graczy
- `soundCategory_blocks` - Głośność dźwięków bloków
- `fov` - Pole widzenia
- `gamma` - Jasność
- `renderDistance` - Odległość renderowania

# Wyświetlanie wartości opcji

Możesz wyświetlić bieżącą wartość dowolnej opcji Minecrafta za pomocą specjalnego placeholdera.

Placeholder wygląda tak:
```
{"placeholder":"minecraft_option_value","values":{"name":"option_name"}}
```

Zastąp `option_name` rzeczywistą nazwą opcji, którą chcesz wyświetlić.

# Ustawianie opcji za pomocą przycisków

Przyciski można wykorzystać do ustawiania konkretnych wartości opcji Minecrafta.

## Jak skonfigurować przycisk:

1. Utwórz nowy element Button
2. Ustaw etykietę przycisku (to, co pojawi się na przycisku)
3. Dodaj akcję: kliknij prawym przyciskiem myszy na przycisk → Edit Action Script → Add Action → Set Minecraft Option Value
4. W oknie "Set Minecraft Option Value":
   - Name: Wpisz nazwę opcji (np. `renderDistance`)
   - Value: Wpisz wartość do ustawienia (np. `16`)

## Przykład: 

Utworzenie przycisku ustawiającego odległość renderowania na 16 chunków:
- Option Name: `renderDistance`
- Value: `16`
- Label: "Ustaw odległość renderowania na 16 chunków"

# Ustawianie opcji za pomocą suwaków

Suwaki są idealne dla opcji z zakresem wartości, takich jak ustawienia głośności czy jasności.

## Jak skonfigurować suwak:

1. Utwórz nowy element Slider
2. Ustaw typ suwaka:
   - Dla liczb całkowitych (np. odległość renderowania): wybierz "Integer Range"
   - Dla liczb dziesiętnych (np. głośność): wybierz "Decimal Range"
3. Ustaw wartości minimalną i maksymalną
4. Dodaj akcję ustawiania opcji Minecrafta:
   - Kliknij prawym przyciskiem myszy → Edit Action Script → Add Action → Set Minecraft Option Value
   - Name: Nazwa opcji
   - Value: `$$value` (ta specjalna zmienna zawiera bieżącą wartość suwaka)
5. Ustaw wstępnie wybraną wartość na bieżącą wartość opcji:
   - Ustaw "Pre-Selected Value" na `{"placeholder":"minecraft_option_value","values":{"name":"option_name"}}`

## Przykładowe formaty etykiet suwaka:

Aby pokazać bieżącą wartość opcji w etykiecie suwaka, użyj:
```
Głośność: {"placeholder":"minecraft_option_value","values":{"name":"soundCategory_master"}}
```

Aby pokazać wartość procentową (przydatne dla głośności):
```
Głośność: {"placeholder":"calc","values":{"expression":"$$value * 100.0","decimal":"false"}}%
```

# Ustawianie opcji za pomocą tickerów

Tickery to niewidoczne elementy, które mogą automatycznie zmieniać opcje według harmonogramu.

## Jak skonfigurować ticker:

1. Utwórz nowy element Ticker
2. Skonfiguruj ustawienia ticków:
   - Tick Mode: Wybierz, kiedy opcja ma się aktualizować
   - Tick Delay: Ustaw, jak często ma się aktualizować (w milisekundach)
3. Dodaj akcję ustawiania opcji Minecrafta:
   - Kliknij prawym przyciskiem myszy → Edit Action Script → Add Action → Set Minecraft Option Value
   - Ustaw nazwę opcji i wartość

## Przykład:

Ustawianie gamma (jasności) na maksimum po wczytaniu menu:
- Tick Mode: On Load Screen
- Name: `gamma`
- Value: `1.0`

# Typowe zastosowania

Oto kilka typowych przykładów tego, co możesz zrobić, używając FancyMenu do ustawiania i odczytywania opcji Minecrafta.

## Tworzenie własnych suwaków głośności

Suwaki głośności to jedno z najczęstszych zastosowań integracji opcji Minecrafta. Oto jak utworzyć własny suwak głośności muzyki:

1. Utwórz nowy element Slider
2. Ustaw "Slider Type" na "Decimal Range"
3. Ustaw "Minimum Range Value" na "0.0"
4. Ustaw "Maximum Range Value" na "1.0"
5. Edit Action Script → Add Action → Set Minecraft Option Value
   - Ustaw Name na `soundCategory_music`
   - Ustaw Value na `$$value`
6. Ustaw "Pre-Selected Value" na `{"placeholder":"minecraft_option_value","values":{"name":"soundCategory_music"}}`
7. Aby wyświetlić głośność jako procent, ustaw etykietę na: 
   ```
   Muzyka: {"placeholder":"calc","values":{"expression":"$$value * 100.0","decimal":"false"}}%
   ```

Możesz tworzyć podobne suwaki dla innych kategorii dźwięku:
- Główna głośność: `soundCategory_master`
- Muzyka: `soundCategory_music`
- Dźwięki otoczenia: `soundCategory_ambient`
- Bloki: `soundCategory_blocks`
- Gracze: `soundCategory_players`
- Pogoda: `soundCategory_weather`

## Tworzenie własnego suwaka FOV

Pole widzenia (FOV) to ważne ustawienie grafiki, które określa, jak szeroko widzisz w grze. Opcja FOV wewnętrznie używa wartości od -1.0 do 1.0, ale w interfejsie wyświetla się jako 30 do 110.

### Zrozumienie mapowania wartości FOV
- Wewnętrzny zakres wartości: -1.0 do 1.0
- Zakres wyświetlanej wartości: 30 do 110
- Wzór mapowania: `(internal_value + 1) * 40 + 30`

### Krok 1: Utwórz element Ticker do aktualizacji tekstu FOV

Najpierw potrzebujemy tickera, który sprawdzi bieżącą wartość FOV i ustawi zmienną z odpowiednim opisem:

1. Utwórz nowy element Ticker
2. Ustaw "Tick Mode" na "Normal" (aby aktualizował się stale)
3. Ustaw "Tick Delay" na około "10" (milisekund), aby uniknąć zbyt częstych sprawdzeń

Teraz musimy skonfigurować akcje dla etykiet FOV. Struktura skryptu akcji powinna wyglądać tak:

```
▶ Action Script
│
├─▶ IF (zmapowany FOV = 70)
│  └─■ Set Variable Value: fov_text:Normal
│
├─▶ ELSE-IF (zmapowany FOV = 110)
│  └─■ Set Variable Value: fov_text:Quake Pro
│
└─▶ ELSE
   └─■ Set Variable Value: fov_text:[obliczona wartość liczbowa]
```

Ustawmy każdą część:

#### Ustawienie etykiety FOV „Normal”:
1. Kliknij prawym przyciskiem myszy → Edit Action Script → Add Action
2. Kliknij "IF Statement", aby dodać blok warunkowy
3. Ustaw wymaganie na "Is Number" z:
   - Compare Mode: "equals"
   - Number: `{"placeholder":"calc","values":{"decimal":"false","expression":"({"placeholder":"minecraft_option_value","values":{"name":"fov"}} + 1) * 40 + 30"}}`
   - Compare With: "70"
4. Wewnątrz tego bloku IF dodaj akcję "Set Variable Value (FM Variable)" z:
   - Value: `fov_text:Normal`

#### Ustawienie etykiety FOV „Quake Pro”:
1. Wewnątrz Action Script dodaj "ELSE-IF Statement"
2. Ustaw wymaganie na "Is Number" z:
   - Compare Mode: "equals"
   - Number: `{"placeholder":"calc","values":{"decimal":"false","expression":"({"placeholder":"minecraft_option_value","values":{"name":"fov"}} + 1) * 40 + 30"}}`
   - Compare With: "110"
3. Wewnątrz tego bloku ELSE-IF dodaj akcję "Set Variable Value (FM Variable)" z:
   - Value: `fov_text:Quake Pro`

#### Ustawienie numerycznej etykiety FOV:
1. Dodaj blok "ELSE Statement"
2. Wewnątrz tego bloku ELSE dodaj akcję "Set Variable Value (FM Variable)" z:
   - Value: `fov_text:{"placeholder":"calc","values":{"decimal":"false","expression":"({"placeholder":"minecraft_option_value","values":{"name":"fov"}} + 1) * 40 + 30"}}`

<img src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/fov_slider_action_script.png" alt="FOV Slider Action Script" style="max-width: 600px; height: auto;">

### Krok 2: Utwórz suwak FOV

1. Utwórz nowy element Slider
2. Ustaw "Slider Type" na "Decimal Range"
3. Ustaw "Minimum Range Value" na "-1.0"
4. Ustaw "Maximum Range Value" na "1.0"
5. Edit Action Script → Add Action → Set Minecraft Option Value
   - Ustaw Name na `fov`
   - Ustaw Value na `$$value`
6. Ustaw "Pre-Selected Value" na `{"placeholder":"minecraft_option_value","values":{"name":"fov"}}`

### Krok 3: Ustaw etykietę suwaka

Ustaw etykietę suwaka tak, aby po prostu wyświetlała zmienną tekstową FOV:

```
FOV: {"placeholder":"getvariable","values":{"name":"fov_text"}}
```

Ta etykieta pokaże:
- "FOV: Normal" gdy wartość wynosi 70
- "FOV: Quake Pro" gdy wartość wynosi 110  
- "FOV: 85" (lub dowolną inną liczbę) dla wszystkich pozostałych wartości

### Wskazówki dotyczące suwaków FOV

- Wewnętrzny zakres wartości suwaka to -1.0 do 1.0, który trzeba zmapować na 30 do 110 do wyświetlania
- Wzór konwersji to: `(internal_value + 1) * 40 + 30`
- Tylko dwie wartości mają specjalne etykiety: 70 (Normal) i 110 (Quake Pro)
- Domyślne FOV w Minecraft to 70 (co odpowiada wewnętrznej wartości 0.0)
- Zmienna `fov_text` automatycznie zawiera albo specjalną etykietę, albo wartość liczbową

## Wyświetlanie wartości opcji w elementach tekstowych

Możesz również wyświetlać bieżące wartości opcji w elementach Text:

1. Utwórz element Text
2. W treści tekstu użyj placeholdera: `{"placeholder":"minecraft_option_value","values":{"name":"option_name"}}`

Na przykład, aby pokazać bieżącą odległość renderowania:
```
Bieżąca odległość renderowania: {"placeholder":"minecraft_option_value","values":{"name":"renderDistance"}} chunków
```

# Znajdowanie nazw opcji

Nazwy wszystkich dostępnych opcji możesz znaleźć w następujący sposób:

  1. Utwórz przycisk
  2. Kliknij go prawym przyciskiem myszy
  3. Kliknij "Edit Action Script"
  4. Dodaj akcję "Set Minecraft Option Value"
  5. Podczas edycji wartości akcji zwróć uwagę na sugestie z listy rozwijanej, gdy zaczniesz wpisywać w polu "Name"
  
# Ważne wskazówki

- **Prawidłowe wartości**: Nie wszystkie opcje akceptują wszystkie wartości. Na przykład:
  - Opcje głośności akceptują wartości od 0.0 do 1.0
  - Odległość renderowania zwykle akceptuje liczby całkowite od 2 do 32
  - Opcje logiczne (true/false), takie jak `pauseOnLostFocus`, akceptują "true" lub "false"

- **Testowanie**: Zawsze testuj ustawienia, aby upewnić się, że działają zgodnie z oczekiwaniami!

- **Informacja wizualna**: Daj użytkownikom wizualną informację o bieżącej wartości, korzystając z opisanych powyżej placeholderów.
