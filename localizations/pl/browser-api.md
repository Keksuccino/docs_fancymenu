---
title: JavaScript API przeglądarki
description: >-
  Jak korzystać z JavaScript API FancyMenu w funkcjach opartych na Rinku, takich
  jak element Browser.
sourceBlobSha: 1dff260c0c5337037200dbf9033300a6bba56ca1
---
# JavaScript API FancyMenu

FancyMenu wstrzykuje most JavaScript do każdej funkcji opartej na [Rinku](https://modrinth.com/mod/rinku) (na przykład do elementu **Browser**). Most umożliwia treściom internetowym:

- bezpośrednie uruchamianie dowolnych [akcji](/action-scripts) FancyMenu z poziomu JavaScriptu,
- asynchroniczne odczytywanie dowolnych [symboli zastępczych](/placeholders) FancyMenu.

Dostęp do API zapewniają dwa obiekty globalne:
- `window.fancymenu` – główna przestrzeń nazw,
- `window.FancyMenu` – alias (ma dokładnie taką samą strukturę jak `fancymenu`).

Zanim wywołasz API, upewnij się, że most jest dostępny — nasłuchuj zdarzenia `fancymenu-ready` lub użyj wykrywania funkcji.

## 1. Przestrzenie nazw i struktura

- `fancymenu.actions` – uruchamia akcje FancyMenu w przeglądarce.
- `fancymenu.placeholders` – asynchronicznie odczytuje wartości symboli zastępczych FancyMenu.
- `FancyMenu` jest kopią `fancymenu`, więc oba obiekty udostępniają te same podprzestrzenie nazw.

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

Treści można też hostować lokalnie: umieść pliki HTML w `<game-directory>/config/fancymenu/assets/` i wczytuj je za pomocą adresów w formacie `file:///config/fancymenu/assets/<name>.html`.

## 3. Uruchamianie akcji

Używaj przestrzeni nazw `fancymenu.actions`. Każde wywołanie odpowiada ciągom akcji używanym w skryptach FancyMenu.

### Szybkie wywołania

```javascript
fancymenu.actions.execute('quitgame');                // akcja bez wartości
fancymenu.actions.execute('opengui', 'title_screen'); // akcja z wartością
fancymenu.actions.execute('set_variable', 'hp:20');   // wartość w formacie nazwa:wartość
```

### Wywołania z funkcjami zwrotnymi

```javascript
fancymenu.actions.executeWithCallback(
    'opengui',
    'title_screen',
    result => console.log('Otworzono ekran tytułowy'),
    error  => console.error('Nie udało się otworzyć:', error)
);

// Parametr value jest opcjonalny. Jeśli go pominięto, przekaż funkcje zwrotne bezpośrednio po actionType.
fancymenu.actions.executeWithCallback(
    'quitgame',
    result => console.log('Zainicjowano wyjście z gry'),
    error  => console.error('Nie udało się wyjść z gry:', error)
);
```

Starsze metody `fancymenu.execute(...)` i `fancymenu.executeWithCallback(...)` nadal przekazują wywołania do przestrzeni nazw `actions`.

### Najczęściej używane typy akcji

- `quitgame` – natychmiast zamyka grę (bez wartości)
- `back_to_last_screen` – wraca do poprzedniego ekranu GUI (bez wartości)
- `opengui` – otwiera ekran FancyMenu lub vanilla (wartość: identyfikator ekranu)
- `openlink` – uruchamia przeglądarkę (wartość: adres URL)
- `sendmessage` – wysyła wiadomość na czacie (wartość: treść wiadomości)
- `set_variable` – przypisuje wartość zmiennej FancyMenu (wartość: `nazwa:wartość`)
- `joinserver` – łączy się z serwerem (wartość: adres)
- `disconnect_server_or_world` – rozłącza i przechodzi do wskazanego ekranu (wartość: identyfikator ekranu)

Za pomocą mostu dostępne są wszystkie akcje FancyMenu. Pełną listę znajdziesz w dokumentacji [skryptów akcji](/action-scripts).

## 4. Odczytywanie symboli zastępczych

System [symboli zastępczych](/placeholders) FancyMenu jest dostępny przez `fancymenu.placeholders` (oraz `FancyMenu.placeholders`). Obie metody pomocnicze zwracają `Promise<string>`:

```ts
fancymenu.placeholders.get(identifier: string): Promise<string>
fancymenu.placeholders.getWithVars(identifier: string, ...vars: string[]): Promise<string>
```

### Przekazywanie zmiennych

- Zmienne są ciągami znaków w formacie `nazwa:wartość`. Most dzieli ciąg tylko przy **pierwszym** dwukropku, więc wartość może zawierać kolejne dwukropki.
- Białe znaki na początku i końcu nazw oraz wartości są usuwane; puste nazwy są odrzucane.
- Przekaż tyle zmiennych, ile wymaga dany symbol zastępczy. Zmienne opcjonalne możesz pominąć.

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
).then(part => console.log('Wybrany element:', part));
```

### Obsługa błędów

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
    
    <button onclick="quitGame()">Wyjdź z gry</button>
    <button onclick="openTitleScreen()">Ekran tytułowy</button>
    <button onclick="disconnectFromServer()">Rozłącz</button>
    <button onclick="setVariable()">Ustaw zmienną</button>
    <button onclick="loadPlaceholders()">Wczytaj symbole zastępcze</button>

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
                () => console.log('Otworzono ekran tytułowy!'),
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
                console.warn('API symboli zastępczych FancyMenu nie jest jeszcze dostępne.');
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
                console.error('Nie udało się pobrać symboli zastępczych:', error);
            });
        }
    </script>
</body>
</html>
```

## 6. Dobre praktyki i uwagi

- **Sprawdź, czy most jest dostępny**, zanim go użyjesz, albo nasłuchuj zdarzenia `fancymenu-ready`.
- **Obsługuj błędy** (funkcje zwrotne dla [akcji](/action-scripts), `.catch` dla [symboli zastępczych](/placeholders)), aby wyświetlać przydatne informacje.
- **Weryfikuj dane wejściowe** przed przekazaniem ich do akcji lub zmiennych [symboli zastępczych](/placeholders).
- **Ogranicz częstotliwość żądań**; unikaj zasypywania mostu szybkimi wywołaniami, zwłaszcza w pętlach odświeżających symbole zastępcze.
- **Bezpieczeństwo:** treści przeglądarki mogą wywoływać dowolne zarejestrowane akcje FancyMenu, w tym akcje związane z plikami, siecią, poleceniami, schowkiem, paczkami zasobów, linkami i zamykaniem gry. Wczytuj wyłącznie zaufane strony i weryfikuj wszystkie dane otrzymane z treści internetowych.

## 7. Rozwiązywanie problemów

1. Upewnij się, że strona jest wczytana w przeglądarce Rinku kontrolowanej przez FancyMenu.
2. Sprawdź, czy w konsoli przeglądarki nie ma błędów JavaScriptu.
3. Sprawdź, czy identyfikator [symbolu zastępczego](/placeholders) lub typ [akcji](/action-scripts) jest poprawny i czy przekazano wymagane wartości.
4. Jeśli wykonanie niespodziewanie się nie powiedzie, sprawdź dziennik Minecrafta (`latest.log`) pod kątem komunikatów o błędach FancyMenu.
