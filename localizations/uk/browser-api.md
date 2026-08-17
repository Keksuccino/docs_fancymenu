---
title: Браузерний JavaScript API
description: >-
  Як використовувати JavaScript API FancyMenu у функціях на основі Rinku, таких
  як елемент Browser.
---
# JavaScript API FancyMenu

FancyMenu впроваджує JavaScript-міст у кожну функцію на основі [Rinku](https://modrinth.com/mod/rinku) (наприклад, в елемент **Browser**). Міст дає вебвмісту змогу:

- безпосередньо запускати будь-яку [дію](./action-scripts) FancyMenu з JavaScript;
- асинхронно отримувати значення будь-якого [заповнювача](/placeholders) FancyMenu.

API доступний через два глобальні об’єкти:
- `window.fancymenu` — основний простір імен;
- `window.FancyMenu` — псевдонім (має точно таку саму структуру, як `fancymenu`).

Використовуйте подію `fancymenu-ready` або перевірку наявності функції, щоб переконатися, що міст доступний, перш ніж викликати його.

## 1. Простори імен і структура

- `fancymenu.actions` — виконання дій FancyMenu у браузері.
- `fancymenu.placeholders` — асинхронне отримання значень заповнювачів FancyMenu.
- `FancyMenu` є дзеркалом `fancymenu`, тому обидва об’єкти надають однакові підпростори імен.

Дії мають два допоміжні методи:
- `fancymenu.actions.execute(actionType, actionValue?)`
- `fancymenu.actions.executeWithCallback(actionType, actionValue?, onSuccess?, onFailure?)`

## 2. Доступність

```javascript
if (typeof fancymenu !== 'undefined') {
    // безпечно використовувати
}

window.addEventListener('fancymenu-ready', () => {
    console.log('API FancyMenu готовий');
});
```

Вміст також можна розміщувати локально: помістіть HTML-файли в `<game-directory>/config/fancymenu/assets/` і завантажуйте їх через URL-адреси формату `file:///config/fancymenu/assets/<name>.html`.

## 3. Виконання дій

Використовуйте простір імен `fancymenu.actions`. Кожен виклик відповідає рядкам дій, що використовуються у скриптах FancyMenu.

### Швидкі виклики

```javascript
fancymenu.actions.execute('quitgame');                // дія без значення
fancymenu.actions.execute('opengui', 'title_screen'); // дія зі значенням
fancymenu.actions.execute('set_variable', 'hp:20');   // значення має формат name:value
```

### Виклики зі зворотними викликами

```javascript
fancymenu.actions.executeWithCallback(
    'opengui',
    'title_screen',
    result => console.log('Головний екран відкрито'),
    error  => console.error('Не вдалося відкрити:', error)
);

// Параметр value необов’язковий. Якщо його пропущено, передайте зворотні виклики безпосередньо після actionType.
fancymenu.actions.executeWithCallback(
    'quitgame',
    result => console.log('Вихід запущено'),
    error  => console.error('Не вдалося вийти:', error)
);
```

Застарілі допоміжні методи `fancymenu.execute(...)` і `fancymenu.executeWithCallback(...)` досі делегують виклики до простору імен `actions`.

### Поширені типи дій

- `quitgame` — негайно завершує гру (без значення);
- `back_to_last_screen` — повертає до попереднього GUI (без значення);
- `opengui` — відкриває екран FancyMenu або ванільний екран (значення: ідентифікатор екрана);
- `openlink` — запускає браузер (значення: URL-адреса);
- `sendmessage` — надсилає рядок у чат (значення: текст повідомлення);
- `set_variable` — задає змінну FancyMenu (значення: `name:value`);
- `joinserver` — підключається до сервера (значення: адреса);
- `disconnect_server_or_world` — розриває з’єднання та переходить до цільового екрана (значення: ідентифікатор екрана).

Через міст доступна кожна дія, що існує у FancyMenu; повний список наведено в документації про [скрипти дій](./action-scripts).

## 4. Отримання заповнювачів

Система [заповнювачів](/placeholders) FancyMenu доступна через `fancymenu.placeholders` (а також через `FancyMenu.placeholders`). Обидва допоміжні методи повертають `Promise<string>`:

```ts
fancymenu.placeholders.get(identifier: string): Promise<string>
fancymenu.placeholders.getWithVars(identifier: string, ...vars: string[]): Promise<string>
```

### Передавання змінних

- Змінні мають формат `name:value`. Міст розділяє рядок лише за **першою** двокрапкою, тому значення може містити додаткові двокрапки.
- Пробіли на початку й у кінці імен і значень видаляються; порожні імена відхиляються.
- Передавайте стільки змінних, скільки потребує заповнювач. Необов’язкові змінні можна не передавати.

### Приклади

```javascript
// Без змінних
fancymenu.placeholders.get('playername')
    .then(name => console.log('Гравець:', name));

// Одна змінна
fancymenu.placeholders.getWithVars('uptime_duration', 'output_as_millis:false')
    .then(seconds => console.log('Час роботи (с):', seconds));

// Кілька змінних
fancymenu.placeholders.getWithVars(
    'split_text',
    'input:apple|banana|carrot',
    'regex:\\|',
    'max_parts:-1',
    'split_index:1'
).then(part => console.log('Вибрана частина:', part));
```

### Модель помилок

Відхилені проміси містять структуровану помилку:

```ts
interface PlaceholderError {
    code: 'NOT_FOUND' | 'MISSING_VARIABLE' | 'INVALID_VARIABLE' | 'EVALUATION_ERROR' | 'INTERNAL_ERROR';
    message: string;
    details?: unknown;
}
```

Приклад обробки:

```javascript
fancymenu.placeholders.get('unknown')
    .catch(error => console.warn(error.code, error.message));
```

## 5. Повний приклад

```html
<!DOCTYPE html>
<html>
<head>
    <title>Інтеграція FancyMenu</title>
</head>
<body>
    <h1>Керування грою</h1>
    
    <button onclick="quitGame()">Вийти з гри</button>
    <button onclick="openTitleScreen()">Головний екран</button>
    <button onclick="disconnectFromServer()">Від’єднатися</button>
    <button onclick="setVariable()">Задати змінну</button>
    <button onclick="loadPlaceholders()">Завантажити заповнювачі</button>

    <div id="placeholderOutput" style="margin-top:16px;font-family:monospace"></div>
    
    <script>
        function getActions() {
            if (typeof fancymenu === 'undefined') {
                console.warn('API FancyMenu ще недоступний.');
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
                () => console.log('Головний екран відкрито!'),
                err => console.error('Помилка:', err)
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
            var varName = prompt('Ім’я змінної:');
            var varValue = prompt('Значення змінної:');
            if (varName && varValue) {
                actions.execute('set_variable', varName + ':' + varValue);
            }
        }

        function loadPlaceholders() {
            if (typeof fancymenu === 'undefined' || !fancymenu.placeholders) {
                console.warn('API заповнювачів FancyMenu ще недоступний.');
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
                    'Гравець: ' + playerName + '\n' +
                    'Час роботи (секунди): ' + uptimeSeconds + '\n' +
                    'Другий фрукт: ' + secondFruit;
            }).catch(error => {
                console.error('Не вдалося отримати заповнювач:', error);
            });
        }
    </script>
</body>
</html>
```

## 6. Рекомендації та примітки

- **Перевіряйте наявність моста** перед використанням або слухайте подію `fancymenu-ready`.
- **Обробляйте помилки** (зворотні виклики для [дій](/action-scripts), `.catch` для [заповнювачів](/placeholders)), щоб надавати корисний зворотний зв’язок.
- **Перевіряйте вхідні дані** перед передаванням їх у дії або змінні [заповнювачів](/placeholders).
- **Обмежуйте частоту запитів**; не надсилайте місту надто багато швидких викликів (особливо в циклах оновлення заповнювачів).
- **Безпека:** вміст браузера може викликати будь-яку зареєстровану дію FancyMenu, зокрема дії для роботи з файлами, мережею, командами, буфером обміну, наборами ресурсів, посиланнями та виходом із гри. Завантажуйте лише довірені сторінки та перевіряйте всі дані, отримані з вебвмісту.

## 7. Усунення несправностей

1. Переконайтеся, що сторінку завантажено у браузері Rinku, яким керує FancyMenu.
2. Перевірте консоль браузера на наявність помилок JavaScript.
3. Переконайтеся, що ідентифікатор [заповнювача](/placeholders) або тип [дії](/action-scripts) вказано правильно, а всі необхідні значення передано.
4. Якщо виконання несподівано завершується помилкою, перегляньте журнал Minecraft (`latest.log`) на наявність повідомлень про помилки FancyMenu.
