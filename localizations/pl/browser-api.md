---
title: Browser JavaScript API
description: >-
  Jak używać API JavaScript FancyMenu w funkcjach moda opartych na MCEF, takich
  jak element Browser.
---

# FancyMenu JavaScript API

FancyMenu wstrzykuje most JavaScript do każdej funkcji opartej na MCEF (na przykład elementu **Browser**). Most umożliwia treści webowej:

- uruchamianie dowolnej [akcji](./action-scripts) FancyMenu bezpośrednio z JavaScriptu,
- asynchroniczne odczytywanie dowolnego [placeholdera](/placeholders) FancyMenu.

Dwie globalne zmienne udostępniają API:
- `window.fancymenu` – główna przestrzeń nazw
- `window.FancyMenu` – alias (odzwierciedla dokładnie strukturę `fancymenu`)

Użyj zdarzenia `fancymenu-ready` albo wykrywania dostępności funkcji, aby upewnić się, że most jest dostępny przed wywołaniem.

## 1. Przestrzenie nazw i struktura

- `fancymenu.actions` – wykonuje akcje FancyMenu z poziomu przeglądarki.
- `fancymenu.placeholders` – odczytuje wartości placeholderów FancyMenu asynchronicznie.
- `FancyMenu` odzwierciedla `fancymenu`, więc oba udostępniają te same podprzestrzenie nazw.

Akcje udostępniają dwa pomocnicze wywołania:
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

Treść może być również hostowana lokalnie: umieść pliki HTML w `<game-directory>/config/fancymenu/assets/` i ładuj je przez adresy w formacie `file:///config/fancymenu/assets/<nazwa>.html`.

## 3. Wykonywanie akcji

Użyj przestrzeni nazw `fancymenu.actions`. Każde wywołanie odpowiada ciągom akcji używanym w skryptach FancyMenu.

### Szybkie wywołania

```javascript
fancymenu.actions.execute('quitgame');                // akcja bez wartości
fancymenu.actions.execute('opengui', 'title_screen'); // akcja z wartością
fancymenu.actions.execute('set_variable', 'hp:20');   // wartość w formacie name:value
```

### Z callbackami

```javascript
fancymenu.actions.executeWithCallback(
    'opengui',
    'title_screen',
    result => console.log('Otwarto ekran tytułowy'),
    error  => console.error('Otwarcie nie powiodło się:', error)
);

// Parametr value jest opcjonalny. Gdy go pomijasz, przekaż callbacki bezpośrednio po actionType.
fancymenu.actions.executeWithCallback(
    'quitgame',
    result => console.log('Wyzwolono zamknięcie gry'),
    error  => console.error('Zamykanie nie powiodło się:', error)
);
```

Starsze pomocnicze wywołania `fancymenu.execute(...)` i `fancymenu.executeWithCallback(...)` nadal przekazują operacje do przestrzeni nazw `actions`.

### Częste typy akcji

- `quitgame` – natychmiast zamyka grę (bez wartości)
- `back_to_last_screen` – wraca do poprzedniego GUI (bez wartości)
- `opengui` – otwiera FancyMenu lub ekran vanilla (wartość: identyfikator ekranu)
- `openlink` – uruchamia przeglądarkę (wartość: adres URL)
- `sendmessage` – wysyła wiadomość na czacie (wartość: tekst wiadomości)
- `set_variable` – przypisuje zmienną FancyMenu (wartość: `name:value`)
- `joinserver` – łączy z serwerem (wartość: adres)
- `disconnect_server_or_world` – rozłącza i przechodzi do docelowego ekranu (wartość: identyfikator ekranu)

Każda akcja dostępna w FancyMenu jest dostępna przez most; zobacz [skrypty akcji](./action-scripts), aby poznać pełny katalog.

## 4. Odczytywanie placeholderów

System [placeholderów](/placeholders) FancyMenu jest udostępniany przez `fancymenu.placeholders` (oraz `FancyMenu.placeholders`). Obie metody pomocnicze zwracają `Promise<string>`:

```ts
fancymenu.placeholders.get(identifier: string): Promise<string>
fancymenu.placeholders.getWithVars(identifier: string, ...vars: string[]): Promise<string>
```

### Przekazywanie zmiennych

- Zmienne są ciągami w formacie `name:value`. Most dzieli je tylko przy **pierwszym** dwukropku, więc wartość może zawierać dodatkowe dwukropki.
- Nazwy i wartości są przycinane z białych znaków; puste nazwy są odrzucane.
- Podaj tyle zmiennych, ile wymaga placeholder. Opcjonalne można pominąć.

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

Odrzucone promise zawierają uporządkowany błąd:

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

## 5. Pełny przykład

```html
<!DOCTYPE html>
<html>
<head>
    <title>Integracja FancyMenu</title>
</head>
<body>
    <h1>Sterowanie grą</h1>
    
    <button onclick="quitGame()">Zakończ grę</button>
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
                () => console.log('Ekran tytułowy otwarty!'),
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

## 6. Najlepsze praktyki i uwagi

- **Wykrywaj most** przed użyciem albo nasłuchuj zdarzenia `fancymenu-ready`.
- **Obsługuj błędy** (callbacki dla [akcji](/action-scripts), `.catch` dla [placeholderów](/placeholders)), aby wyświetlać użyteczne informacje.
- **Waliduj dane wejściowe** przed przekazaniem ich do akcji lub zmiennych [placeholderów](/placeholders).
- **Ograniczaj częstotliwość żądań**; unikaj zalewania mostu częstymi wywołaniami (zwłaszcza w pętlach odświeżania placeholderów).
- **Bezpieczeństwo:** Treść przeglądarkowa może wywołać dowolną zarejestrowaną akcję FancyMenu, w tym akcje plikowe, sieciowe, poleceń, schowka, resource packów, linków i zamykania gry. Ładuj tylko zaufane strony i waliduj wszystkie dane otrzymane z treści webowej.

## 7. Rozwiązywanie problemów

1. Potwierdź, że strona jest ładowana w przeglądarce MCEF kontrolowanej przez FancyMenu.
2. Sprawdź konsolę przeglądarki pod kątem błędów JavaScript.
3. Upewnij się, że identyfikator [placeholdera](/placeholders) lub typ [akcji](/action-scripts) jest poprawny i że wymagane wartości zostały podane.
4. Sprawdź log Minecrafta (`latest.log`) pod kątem komunikatów o błędach FancyMenu, jeśli wykonanie kończy się nieoczekiwaną porażką.
