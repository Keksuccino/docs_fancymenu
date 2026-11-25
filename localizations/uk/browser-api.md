---
title: API JavaScript браузера
description: >-
  Як використовувати JavaScript API FancyMenu у функціях на базі Rinku,
  наприклад в елементі Browser.
sourceBlobSha: 1dff260c0c5337037200dbf9033300a6bba56ca1
---
# JavaScript API FancyMenu

FancyMenu додає міст JavaScript до кожної функції на базі [Rinku](https://modrinth.com/mod/rinku) (наприклад, до елемента **Browser**). Завдяки цьому вебвміст може:

- запускати будь-яку [дію](/action-scripts) FancyMenu безпосередньо з JavaScript;
- асинхронно читати будь-який [заповнювач](/placeholders) FancyMenu.

API доступний через дві глобальні змінні:
- `window.fancymenu` — основний простір імен;
- `window.FancyMenu` — псевдонім (має ту саму структуру, що й `fancymenu`).

Перш ніж викликати API, переконайтеся, що міст доступний: дочекайтеся події `fancymenu-ready` або скористайтеся перевіркою наявності функції.

## 1. Простори імен і структура

- `fancymenu.actions` — запуск дій FancyMenu у браузері.
- `fancymenu.placeholders` — асинхронне читання значень заповнювачів FancyMenu.
- `FancyMenu` є псевдонімом `fancymenu`, тож обидва об’єкти містять однакові підпростори імен.

Для дій доступні два допоміжні методи:
- `fancymenu.actions.execute(actionType, actionValue?)`
- `fancymenu.actions.executeWithCallback(actionType, actionValue?, onSuccess?, onFailure?)`

## 2. Доступність

```javascript
if (typeof fancymenu !== 'undefined') {
    // API можна безпечно використовувати
}

window.addEventListener('fancymenu-ready', () => {
    console.log('API FancyMenu готовий');
});
```

Вміст також можна розмістити локально: помістіть HTML-файли в `<game-directory>/config/fancymenu/assets/` і завантажуйте їх за URL такого формату: `file:///config/fancymenu/assets/<name>.html`.

## 3. Запуск дій

Використовуйте простір імен `fancymenu.actions`. Кожен виклик відповідає рядкам дій, які використовуються у скриптах FancyMenu.

### Швидкі виклики

```javascript
fancymenu.actions.execute('quitgame');                // дія без значення
fancymenu.actions.execute('opengui', 'title_screen'); // дія зі значенням
fancymenu.actions.execute('set_variable', 'hp:20');   // значення у форматі name:value
```

### Виклики зі зворотними викликами

```javascript
fancymenu.actions.executeWithCallback(
    'opengui',
    'title_screen',
    result => console.log('Відкрито головне меню'),
    error  => console.error('Не вдалося відкрити:', error)
);

// Параметр value необов’язковий. Якщо його не вказано, передайте зворотні виклики одразу після actionType.
fancymenu.actions.executeWithCallback(
    'quitgame',
    result => console.log('Вихід запущено'),
    error  => console.error('Не вдалося вийти:', error)
);
```

Застарілі допоміжні методи `fancymenu.execute(...)` і `fancymenu.executeWithCallback(...)` досі делегують виклики простору імен `actions`.

### Поширені типи дій

- `quitgame` — негайно завершує гру (без значення);
- `back_to_last_screen` — повертає до попереднього екрана GUI (без значення);
- `opengui` — відкриває екран FancyMenu або стандартний екран гри (значення: ідентифікатор екрана);
- `openlink` — відкриває браузер (значення: URL-адреса);
- `sendmessage` — надсилає повідомлення в чат (значення: текст повідомлення);
- `set_variable` — задає змінну FancyMenu (значення: `name:value`);
- `joinserver` — підключається до сервера (значення: адреса);
- `disconnect_server_or_world` — від’єднується та переходить до цільового екрана (значення: ідентифікатор екрана).

Через міст доступні всі дії FancyMenu. Повний список див. у розділі [скрипти дій](/action-scripts).

## 4. Читання заповнювачів

Система [заповнювачів](/placeholders) FancyMenu доступна через `fancymenu.placeholders` (а також `FancyMenu.placeholders`). Обидва допоміжні методи повертають `Promise<string>`:

```ts
fancymenu.placeholders.get(identifier: string): Promise<string>
fancymenu.placeholders.getWithVars(identifier: string, ...vars: string[]): Promise<string>
```

### Передавання змінних

- Змінні — це рядки у форматі `name:value`. Міст розділяє рядок лише за **першою** двокрапкою, тож значення може містити додаткові двокрапки.
- Пробіли на початку й у кінці імен та значень видаляються; порожні імена не допускаються.
- Передайте стільки змінних, скільки вимагає заповнювач. Необов’язкові змінні можна опустити.

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

### Обробка помилок

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
    <button onclick="openTitleScreen()">Головне меню</button>
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
                () => console.log('Головне меню відкрито!'),
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
                console.error('Не вдалося отримати заповнювачі:', error);
            });
        }
    </script>
</body>
</html>
```

## 6. Рекомендації та примітки

- **Перевіряйте наявність мосту** перед використанням або очікуйте на подію `fancymenu-ready`.
- **Обробляйте помилки** (зворотні виклики для [дій](/action-scripts), `.catch` для [заповнювачів](/placeholders)), щоб показувати корисні повідомлення.
- **Перевіряйте введені дані** перед передаванням їх діям або як змінних [заповнювачів](/placeholders).
- **Обмежуйте частоту запитів** і не надсилайте їх через міст надто часто (особливо в циклах оновлення заповнювачів).
- **Безпека:** вміст браузера може запускати будь-яку зареєстровану дію FancyMenu, зокрема дії з файлами, мережею, командами, буфером обміну, наборами ресурсів, посиланнями та виходом із гри. Завантажуйте лише довірені сторінки й перевіряйте всі дані, отримані з вебвмісту.

## 7. Усунення проблем

1. Переконайтеся, що сторінку відкрито в браузері Rinku, яким керує FancyMenu.
2. Перевірте консоль браузера на наявність помилок JavaScript.
3. Переконайтеся, що ідентифікатор [заповнювача](/placeholders) або тип [дії](/action-scripts) правильний і передано всі обов’язкові значення.
4. Якщо виконання несподівано завершується помилкою, перевірте журнал Minecraft (`latest.log`) на наявність повідомлень про помилки FancyMenu.
