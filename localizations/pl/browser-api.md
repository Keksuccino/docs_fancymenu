---
title: JavaScript API przeglądarki
description: >-
  Jak korzystać z JavaScript API FancyMenu w funkcjach modów opartych na Rinku,
  takich jak element Browser.
---
# JavaScript API FancyMenu

FancyMenu wstrzykuje most JavaScript do każdej funkcji opartej na [Rinku](https://modrinth.com/mod/rinku) (na przykład elementu **Browser**). Most umożliwia zawartości internetowej:

- bezpośrednie uruchamianie dowolnej [akcji](./action-scripts) FancyMenu z poziomu JavaScriptu,
- asynchroniczne odczytywanie dowolnego [placeholdera](/placeholders) FancyMenu.

API udostępniają dwa obiekty globalne:
- `window.fancymenu` – główna przestrzeń nazw
- `window.FancyMenu` – alias (ma dokładnie taką samą strukturę jak `fancymenu`)

Użyj zdarzenia `fancymenu-ready` lub wykrywania funkcji, aby upewnić się, że most jest dostępny, zanim zaczniesz z niego korzystać.

## 1. Przestrzenie nazw i struktura

- `fancymenu.actions` – uruchamianie akcji FancyMenu z poziomu przeglądarki.
- `fancymenu.placeholders` – asynchroniczne odczytywanie wartości placeholderów FancyMenu.
- `FancyMenu` jest odbiciem `fancymenu`, więc obie przestrzenie udostępniają te same podprzestrzenie nazw.

Akcje udostępniają dwie metody pomocnicze:
- `fancymenu.actions.execute(actionType, actionValue?)`
- `fancymenu.actions.executeWithCallback(actionType, actionValue?, onSuccess?, onFailure?)`

## 2. Dostępność

```javascript
if (typeof fancymenu !== 'undefined') {
    // można bezpiecznie używać
}

window.addEventListener('fancymenu-ready', () => {
    console.log('API FancyMenu jest gotowe');
});
```

Zawartość może być także hostowana lokalnie: umieść pliki HTML w `<game-directory>/config/fancymenu/assets/` i wczytuj je za pomocą adresów w formacie `file:///config/fancymenu/assets/<name>.html`.

## 3. Uruchamianie akcji

Użyj przestrzeni nazw `fancymenu.actions`. Każde wywołanie odpowiada ciągom akcji używanym w skryptach FancyMenu.

### Szybkie wywołania

```javascript
fancymenu.actions.execute('quitgame');                // akcja bez wartości
fancymenu.actions.execute('opengui', 'title_screen'); // akcja z wartością
fancymenu.actions.execute('set_variable', 'hp:20');   // wartość w formacie nazwa:wartość
```

### Z funkcjami zwrotnymi

```javascript
fancymenu.actions.executeWithCallback(
    'opengui',
    'title_screen',
    result => console.log('Ekran tytułowy został otwarty'),
    error  => console.error('Nie udało się otworzyć:', error)
);

// Parametr value jest opcjonalny. Gdy zostanie pominięty, przekaż funkcje zwrotne bezpośrednio po actionType.
fancymenu.actions.executeWithCallback(
    'quitgame',
    result => console.log('Rozpoczęto zamykanie gry'),
    error  => console.error('Nie udało się zamknąć gry:', error)
);
```

Starsze metody pomocnicze `fancymenu.execute(...)` i `fancymenu.executeWithCallback(...)` nadal przekazują wywołania do przestrzeni nazw `actions`.

### Typowe typy akcji

- `quitgame` – natychmiast zamyka grę (bez wartości)
- `back_to_last_screen` – wraca do poprzedniego GUI (bez wartości)
- `opengui` – otwiera ekran FancyMenu lub waniliowego Minecrafta (wartość: identyfikator ekranu)
- `openlink` – uruchamia przeglądarkę (wartość: URL)
- `sendmessage` – wysyła wiadomość na czat (wartość: treść wiadomości)
- `set_variable` – przypisuje wartość zmiennej FancyMenu (wartość: `nazwa:wartość`)
- `joinserver` – łączy z serwerem (wartość: adres)
- `disconnect_server_or_world` – rozłącza i przechodzi do wskazanego ekranu (wartość: identyfikator ekranu)

Każda akcja dostępna w FancyMenu jest dostępna również przez most; pełny katalog znajdziesz w sekcji [skrypty akcji](./action-scripts).

## 4. Odczytywanie placeholderów

System [placeholderów](/placeholders) FancyMenu jest dostępny przez `fancymenu.placeholders` (oraz `FancyMenu.placeholders`). Obie metody pomocnicze zwracają `Promise<string>`:

```ts
fancymenu.placeholders.get(identifier: string): Promise<string>
fancymenu.placeholders.getWithVars(identifier: string, ...vars: string[]): Promise<string>
```

### Przekazywanie zmiennych

- Zmienne są ciągami w formacie `nazwa:wartość`. Most dzieli ciąg tylko przy **pierwszym** dwukropku, więc wartość może zawierać kolejne dwukropki.
- Nazwy i wartości są przycinane; puste nazwy są odrzucane.
- Podaj tyle zmiennych, ile wymaga placeholder. Pomiń zmienne opcjonalne.

### Przykłady

```javascript
// Bez zmiennych
fancymenu.placeholders.get('playername')
    .then(name => console.log('Gracz:', name));

// Jedna zmienna
fancymenu.placeholders.getWithVars('uptime_duration', 'output_as_millis:false')
    .then(seconds => console.log('Czas działania (s):', seconds));

// Wiele zmiennych
fancymenu.placeholders.getWithVars(
    'split_text',
    'input:apple|banana|carrot',
    'regex:\\|',
    'max_parts:-1',
    'split_index:1'
).then(part => console.log('Wybrana część:', part));
```

### Model błędów

Odrzucone obietnice zawierają ustrukturyzowany błąd:

```ts
interface PlaceholderError {
    code: 'NOT_FOUND' | 'MISSING_VARIABLE' | 'INVALID_VARIABLE' | 'EVALUATION_ERROR' | 'INTERNAL_ERROR';
    message: string;
    details?: unknown;
}
```

Przykład obsługi:

```javascript
fancymenu.placeholders.get('unknown')
    .catch(error => console.warn(error.code, error.message));
```

## 5. Kompletny przykład

```html
<!DOCTYPE html>
<html>
<head>
    <title>Integracja z FancyMenu</title>
</head>
<body>
    <h1>Sterowanie grą</h1>
    
    <button onclick="quitGame()">Zamknij grę</button>
    <button onclick="openTitleScreen()">Ekran tytułowy</button>
    <button onclick="disconnectFromServer()">Rozłącz</button>
    <button onclick="setVariable()">Ustaw zmienną</button>
    <button onclick="loadPlaceholders()">Wczytaj placeholdery</button>

    <div id="placeholderOutput" style="margin-top:16px;font-family:monospace"></div>
    
    <script>
        function getActions() {
            if (typeof fancymenu === 'undefined') {
                console.warn('API FancyMenu nie jest jeszcze dostępne.');
                return null;
            }
            return fancymenu.actions || fancymenu;
        }

        function quitGame() {
            const actions = getActions();
            if (!actions) return;
            actions.execute('quitgame');
        }
        
        function openTitleScreen() {
            const actions = getActions();
            if (!actions) return;
            actions.executeWithCallback(
                'opengui',
                'title_screen',
                () => console.log('Ekran tytułowy został otwarty!'),
                err => console.error('Błąd:', err)
            );
        }
        
        function disconnectFromServer() {
            const actions = getActions();
            if (!actions) return;
            actions.execute('disconnect_server_or_world', 'title_screen');
        }
        
        function setVariable() {
            const actions = getActions();
            if (!actions) return;
            var varName = prompt('Nazwa zmiennej:');
            var varValue = prompt('Wartość zmiennej:');
            if (varName && varValue) {
                actions.execute('set_variable', varName + ':' + varValue);
            }
        }

        function loadPlaceholders() {
            if (typeof fancymenu === 'undefined' || !fancymenu.placeholders) {
                console.warn('API placeholderów FancyMenu nie jest jeszcze dostępne.');
                return;
            }

            Promise.all([
                fancymenu.placeholders.get('playername'),
                fancymenu.placeholders.getWithVars('uptime_duration', 'output_as_millis:false'),
                fancymenu.placeholders.getWithVars(
                    'split_text',
                    'input:apple|banana|carrot',
                    'regex:\\|',
                    'max_parts:-1',
                    'split_index:1'
                )
            ]).then(([playerName, uptimeSeconds, secondFruit]) => {
                document.getElementById('placeholderOutput').textContent =
                    'Gracz: ' + playerName + '\n' +
                    'Czas działania (sekundy): ' + uptimeSeconds + '\n' +
                    'Drugi owoc: ' + secondFruit;
            }).catch(error => {
                console.error('Żądanie placeholdera nie powiodło się:', error);
            });
        }
    </script>
</body>
</html>
```

## 6. Dobre praktyki i uwagi

- **Wykrywaj most** przed użyciem lub nasłuchuj zdarzenia `fancymenu-ready`.
- **Obsługuj błędy** (funkcje zwrotne dla [akcji](/action-scripts), `.catch` dla [placeholderów](/placeholders)), aby wyświetlać przydatne informacje.
- **Weryfikuj dane wejściowe** przed przekazaniem ich do akcji lub zmiennych [placeholderów](/placeholders).
- **Ograniczaj częstotliwość żądań**; unikaj zasypywania mostu szybkimi, powtarzającymi się wywołaniami (szczególnie w pętlach odświeżających placeholdery).
- **Bezpieczeństwo:** zawartość przeglądarki może wywołać dowolną zarejestrowaną akcję FancyMenu, w tym akcje dotyczące plików, sieci, poleceń, schowka, paczek zasobów, linków i zamykania gry. Wczytuj wyłącznie zaufane strony i weryfikuj wszystkie dane otrzymane z zawartości internetowej.

## 7. Rozwiązywanie problemów

1. Upewnij się, że strona jest wczytana w przeglądarce Rinku kontrolowanej przez FancyMenu.
2. Sprawdź konsolę przeglądarki pod kątem błędów JavaScript.
3. Zweryfikuj, czy identyfikator [placeholdera](/placeholders) lub typ [akcji](/action-scripts) jest poprawny oraz czy podano wszystkie wymagane wartości.
4. Jeśli wykonanie nieoczekiwanie się nie powiedzie, sprawdź dziennik Minecrafta (`latest.log`) pod kątem komunikatów o błędach FancyMenu.
