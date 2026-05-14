---
title: Browser JavaScript API
description: >-
  Як використовувати JavaScript API FancyMenu у функціях мода на основі MCEF,
  таких як елемент Browser.
---

# JavaScript API FancyMenu

FancyMenu вбудовує JavaScript-міст у кожну функцію на базі MCEF (наприклад, елемент **Browser**). Цей міст дає вебвмісту змогу:

- безпосередньо запускати будь-яку [дію](./action-scripts) FancyMenu з JavaScript,
- асинхронно читати будь-який [плейсхолдер](/placeholders) FancyMenu.

Доступ до API відкривають два глобальні об’єкти:
- `window.fancymenu` – основний простір імен
- `window.FancyMenu` – псевдонім (повністю повторює структуру `fancymenu`)

Використовуйте подію `fancymenu-ready` або перевірку наявності функцій, щоб переконатися, що міст доступний перед викликом.

## 1. Простори імен і структура

- `fancymenu.actions` – виконання дій FancyMenu з браузера.
- `fancymenu.placeholders` – асинхронне читання значень плейсхолдерів FancyMenu.
- `FancyMenu` повторює `fancymenu`, тож обидва об’єкти надають однакові підпростори імен.

Для дій доступні два допоміжні методи:
- `fancymenu.actions.execute(actionType, actionValue?)`
- `fancymenu.actions.executeWithCallback(actionType, actionValue?, onSuccess?, onFailure?)`

## 2. Доступність

```javascript
if (typeof fancymenu !== 'undefined') {
    // можна безпечно використовувати
}

window.addEventListener('fancymenu-ready', () => {
    console.log('API FancyMenu готовий');
});
```

Вміст також може бути локальним: розмістіть HTML-файли в `config/fancymenu/assets/` і завантажуйте їх через URL виду `file:///config/fancymenu/assets/<name>.html`.

## 3. Виконання дій

Використовуйте простір імен `fancymenu.actions`. Кожен виклик відповідає рядкам дій, що використовуються в скриптах FancyMenu.

### Швидкі виклики

```javascript
fancymenu.actions.execute('quitgame');                // дія без значення
fancymenu.actions.execute('opengui', 'title_screen'); // дія зі значенням
fancymenu.actions.execute('set_variable', 'hp:20');   // значення у форматі name:value
```

### Зворотні виклики

```javascript
fancymenu.actions.executeWithCallback(
    'opengui',
    'title_screen',
    result => console.log('Відкрито титульний екран'),
    error  => console.error('Не вдалося відкрити:', error)
);

// Параметр value є необов’язковим. Якщо його немає, передавайте callback-и одразу після actionType.
fancymenu.actions.executeWithCallback(
    'quitgame',
    result => console.log('Запит на вихід надіслано'),
    error  => console.error('Не вдалося вийти:', error)
);

Старі допоміжні методи `fancymenu.execute(...)` і `fancymenu.executeWithCallback(...)` усе ще працюють і перенаправляють виклики до простору імен `actions`, тож наявний вміст не потребує негайних змін.
```

### Поширені типи дій

- `quitgame` – негайно завершує гру (без значення)
- `back_to_last_screen` – повертає до попереднього GUI (без значення)
- `opengui` – відкриває екран FancyMenu або стандартний екран (значення: ідентифікатор екрана)
- `openlink` – відкриває браузер (значення: URL)
- `sendmessage` – надсилає повідомлення в чат (значення: текст повідомлення)
- `set_variable` – присвоює змінну FancyMenu (значення: `name:value`)
- `joinserver` – підключається до сервера (значення: адреса)
- `disconnect_server_or_world` – від’єднується і переходить до цільового екрана (значення: ідентифікатор екрана)

Усі дії, що існують у FancyMenu, доступні через міст; див. [action scripts](./action-scripts) для повного каталогу.

## 4. Читання плейсхолдерів

Система [плейсхолдерів](/placeholders) FancyMenu доступна через `fancymenu.placeholders` (і `FancyMenu.placeholders`). Обидва допоміжні методи повертають `Promise<string>`:

```ts
fancymenu.placeholders.get(identifier: string): Promise<string>
fancymenu.placeholders.getWithVars(identifier: string, ...vars: string[]): Promise<string>
```

### Передавання змінних

- Змінні — це рядки у форматі `name:value`. Міст розбиває рядок лише за **першою** двокрапкою, тож значення може містити додаткові двокрапки.
- Імена та значення обрізаються від зайвих пробілів; порожні імена відхиляються.
- Передавайте стільки змінних, скільки вимагає плейсхолдер. Необов’язкові можна пропускати.

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
).then(part => console.log('Обрана частина:', part));
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
    <button onclick="openTitleScreen()">Титульний екран</button>
    <button onclick="disconnectFromServer()">Від’єднатися</button>
    <button onclick="setVariable()">Встановити змінну</button>
    <button onclick="loadPlaceholders()">Завантажити плейсхолдери</button>

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
                () => console.log('Титульний екран відкрито!'),
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
                console.warn('API плейсхолдерів FancyMenu ще недоступний.');
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
                console.error('Не вдалося отримати плейсхолдер:', error);
            });
        }
    </script>
</body>
</html>
```

## 6. Рекомендації та примітки

- **Перевіряйте наявність мосту** перед використанням або підписуйтеся на `fancymenu-ready`.
- **Обробляйте помилки** (callback-и для [дій](/action-scripts), `.catch` для [плейсхолдерів](/placeholders)), щоб надавати корисний зворотний зв’язок.
- **Перевіряйте вхідні дані** перед передаванням їх у дії або змінні [плейсхолдерів](/placeholders).
- **Обмежуйте частоту запитів**; не перевантажуйте міст частими викликами (особливо циклами оновлення плейсхолдерів).
- **Безпека**: дії виконуються з нормальними правами гравця. Обережно ставтеся до даних, наданих користувачем, щоб уникнути ін’єкцій.

## 7. Усунення несправностей

1. Переконайтеся, що сторінка завантажена у браузері MCEF, яким керує FancyMenu.
2. Перевірте консоль браузера на наявність JavaScript-помилок.
3. Переконайтеся, що ідентифікатор [плейсхолдера](/placeholders) або тип [дії](/action-scripts) правильний і що потрібні значення передано.
4. Якщо виконання несподівано завершується помилкою, перегляньте журнал Minecraft (`latest.log`) на наявність повідомлень про помилки FancyMenu.
