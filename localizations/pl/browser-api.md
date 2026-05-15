---
title: Browser JavaScript API
description: >-
  Jak korzystać z interfejsu JavaScript FancyMenu w funkcjach modów opartych na
  MCEF, takich jak element Browser.
---

# Interfejs JavaScript FancyMenu

FancyMenu wstrzykuje most JavaScript do każdej funkcji opartej na MCEF (na przykład elementu **Browser**). Ten most pozwala treści webowej:

- uruchamiać dowolne [akcje](./action-scripts) FancyMenu bezpośrednio z JavaScript,
- odczytywać dowolne [placeholdery](/placeholders) FancyMenu asynchronicznie.

Interfejs API jest udostępniany przez dwie globalne zmienne:
- `window.fancymenu` – główna przestrzeń nazw
- `window.FancyMenu` – alias (odzwierciedla dokładnie strukturę `fancymenu`)

Użyj zdarzenia `fancymenu-ready` albo wykrywania dostępności funkcji, aby upewnić się, że most jest dostępny przed jego wywołaniem.

## 1. Przestrzenie nazw i struktura

- `fancymenu.actions` – wykonuje akcje FancyMenu z poziomu przeglądarki.
- `fancymenu.placeholders` – odczytuje wartości placeholderów FancyMenu asynchronicznie.
- `FancyMenu` odzwierciedla `fancymenu`, więc obie zmienne udostępniają te same podprzestrzenie nazw.

Akcje udostępniają dwa pomocnicze wywołania:
- `fancymenu.actions.execute(actionType, actionValue?)`
- `fancymenu.actions.executeWithCallback(actionType, actionValue?, onSuccess?, onFailure?)`

## 2. Dostępność

```javascript
if (typeof fancymenu !== 'undefined') {
    // można bezpiecznie używać
}

window.addEventListener('fancymenu-ready', () => {
    console.log('Interfejs API FancyMenu jest gotowy');
});
```

Treść może być także hostowana lokalnie: umieść pliki HTML w `config/fancymenu/assets/` i ładuj je przez adresy w formie `file:///config/fancymenu/assets/<nazwa>.html`.

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
    result => console.log('Ekran tytułowy otwarty'),
    error  => console.error('Otwarcie nie powiodło się:', error)
);

// Parametr value jest opcjonalny. Jeśli go nie podasz, przekaż callbacki bezpośrednio po actionType.
fancymenu.actions.executeWithCallback(
    'quitgame',
    result => console.log('Wywołano wyjście z gry'),
    error  => console.error('Wyjście nie powiodło się:', error)
);

Starsze pomocnicze funkcje `fancymenu.execute(...)` i `fancymenu.executeWithCallback(...)` nadal działają i przekazują wywołania do przestrzeni nazw `actions`, więc istniejącej treści nie trzeba od razu zmieniać.
```

### Najczęstsze typy akcji

- `quitgame` – natychmiast wychodzi z gry (bez wartości)
- `back_to_last_screen` – wraca do poprzedniego GUI (bez wartości)
- `opengui` – otwiera ekran FancyMenu lub domyślny ekran gry (wartość: identyfikator ekranu)
- `openlink` – uruchamia przeglądarkę (wartość: URL)
- `sendmessage` – wysyła wiadomość na czacie (wartość: treść wiadomości)
- `set_variable` – przypisuje zmienną FancyMenu (wartość: `name:value`)
- `joinserver` – łączy z serwerem (wartość: adres)
- `disconnect_server_or_world` – rozłącza i przechodzi do docelowego ekranu (wartość: identyfikator ekranu)

Każda akcja dostępna w FancyMenu jest dostępna przez most; zobacz [skrypty akcji](./action-scripts), aby uzyskać pełny katalog.

## 4. Odczytywanie placeholderów

System [placeholderów](/placeholders) FancyMenu jest udostępniany przez `fancymenu.placeholders` (oraz `FancyMenu.placeholders`). Obie metody pomocnicze zwracają `Promise<string>`:

```ts
fancymenu.placeholders.get(identifier: string): Promise<string>
fancymenu.placeholders.getWithVars(identifier: string, ...vars: string[]): Promise<string>
```

### Przekazywanie zmiennych

- Zmienne są ciągami w formacie `name:value`. Most dzieli tylko przy **pierwszym** dwukropku, więc wartość może zawierać dodatkowe dwukropki.
- Nazwy i wartości są przycinane z białych znaków; puste nazwy są odrzucane.
- Przekaż tyle zmiennych, ile wymaga dany placeholder. Pomiń opcjonalne.

### Przykłady

```javascript
// Bez zmiennych
fancymenu.placeholders.get('playername')
    .then(name => console.log('Gracz:', name));

// Jedna zmienna
fancymenu.placeholders.getWithVars('uptime_duration', 'output_as_millis:false')
    .then(seconds => console.log('Czas działania (s):', seconds));

// Kilka zmiennych
fancymenu.placeholders.getWithVars(
    'split_text',
    'input:apple|banana|carrot',
    'regex:\\|',
    'max_parts:-1',
    'split_index:1'
).then(part => console.log('Wybrana część:', part));
```

### Model błędów

Odrzucone promise zawierają ustrukturyzowany błąd:

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
    
    <button onclick="quitGame()">Wyjdź z gry</button>
    <button onclick="openTitleScreen()">Ekran tytułowy</button>
    <button onclick="disconnectFromServer()">Rozłącz</button>
    <button onclick="setVariable()">Ustaw zmienną</button>
    <button onclick="loadPlaceholders()">Wczytaj placeholdery</button>

    <div id="placeholderOutput" style="margin-top:16px;font-family:monospace"></div>
    
    <script>
        function getActions() {
            if (typeof fancymenu === 'undefined') {
                console.warn('Interfejs API FancyMenu nie jest jeszcze dostępny.');
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
                console.warn('Interfejs API placeholderów FancyMenu nie jest jeszcze dostępny.');
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

- **Wykrywaj most** przed użyciem lub nasłuchuj zdarzenia `fancymenu-ready`.
- **Obsługuj błędy** (callbacki dla [akcji](/action-scripts), `.catch` dla [placeholderów](/placeholders)), aby pokazywać użyteczne komunikaty.
- **Waliduj dane wejściowe** przed przekazaniem ich do akcji lub zmiennych [placeholderów](/placeholders).
- **Ograniczaj częstotliwość zapytań**; unikaj zalewania mostu szybkimi wywołaniami (szczególnie w pętlach odświeżania placeholderów).
- **Bezpieczeństwo**: akcje wykonują się z normalnymi uprawnieniami gracza. Traktuj dane od użytkownika ostrożnie, aby uniknąć wstrzyknięć.

## 7. Rozwiązywanie problemów

1. Upewnij się, że strona jest wczytana w przeglądarce MCEF kontrolowanej przez FancyMenu.
2. Sprawdź konsolę przeglądarki pod kątem błędów JavaScript.
3. Zweryfikuj, czy identyfikator [placeholdera](/placeholders) lub typ [akcji](/action-scripts) jest poprawny i czy wymagane wartości zostały podane.
4. Przejrzyj log Minecrafta (`latest.log`) w poszukiwaniu komunikatów błędów FancyMenu, jeśli wykonanie kończy się nieoczekiwanie.
