---
title: API JavaScript для браузера
description: >-
  Как использовать JavaScript API FancyMenu в функциях модов на базе Rinku,
  таких как элемент Browser.
---
# JavaScript API FancyMenu

FancyMenu внедряет JavaScript-мост в каждую функцию на базе [Rinku](https://modrinth.com/mod/rinku) (например, элемент **Browser**). Этот мост позволяет веб-контенту:

- запускать любые [действия] FancyMenu (./action-scripts) прямо из JavaScript,
- асинхронно читать любые [плейсхолдеры] FancyMenu (/placeholders).

API доступен через две глобальные переменные:
- `window.fancymenu` — основной namespace
- `window.FancyMenu` — псевдоним (полностью повторяет структуру `fancymenu`)

Используйте событие `fancymenu-ready` или проверку наличия функции, чтобы убедиться, что мост доступен, прежде чем вызывать его.

## 1. Пространства имён и структура

- `fancymenu.actions` — выполнение действий FancyMenu из браузера.
- `fancymenu.placeholders` — асинхронное чтение значений плейсхолдеров FancyMenu.
- `FancyMenu` повторяет `fancymenu`, поэтому оба объекта предоставляют одинаковые подпространства имён.

Для действий доступны две вспомогательные функции:
- `fancymenu.actions.execute(actionType, actionValue?)`
- `fancymenu.actions.executeWithCallback(actionType, actionValue?, onSuccess?, onFailure?)`

## 2. Доступность

```javascript
if (typeof fancymenu !== 'undefined') {
    // можно безопасно использовать
}

window.addEventListener('fancymenu-ready', () => {
    console.log('FancyMenu API is ready');
});
```

Контент также может храниться локально: поместите HTML-файлы в `<game-directory>/config/fancymenu/assets/` и загружайте их по URL вида `file:///config/fancymenu/assets/<name>.html`.

## 3. Выполнение действий

Используйте пространство имён `fancymenu.actions`. Каждый вызов повторяет строки действий, используемые в скриптах FancyMenu.

### Быстрые вызовы

```javascript
fancymenu.actions.execute('quitgame');                // действие без значения
fancymenu.actions.execute('opengui', 'title_screen'); // действие со значением
fancymenu.actions.execute('set_variable', 'hp:20');   // значение в формате name:value
```

### С обратными вызовами

```javascript
fancymenu.actions.executeWithCallback(
    'opengui',
    'title_screen',
    result => console.log('Открыт экран заголовка'),
    error  => console.error('Не удалось открыть:', error)
);

// Параметр value необязателен. Если он опущен, передавайте callback-функции сразу после actionType.
fancymenu.actions.executeWithCallback(
    'quitgame',
    result => console.log('Выход запущен'),
    error  => console.error('Не удалось выйти:', error)
);
```

Устаревшие помощники `fancymenu.execute(...)` и `fancymenu.executeWithCallback(...)` по-прежнему перенаправляются к пространству имён `actions`.

### Распространённые типы действий

- `quitgame` — немедленно завершает игру (без значения)
- `back_to_last_screen` — возвращает к предыдущему GUI (без значения)
- `opengui` — открывает экран FancyMenu или ванильный экран (значение: идентификатор экрана)
- `openlink` — открывает браузер (значение: URL)
- `sendmessage` — отправляет строку в чат (значение: текст сообщения)
- `set_variable` — задаёт переменную FancyMenu (значение: `name:value`)
- `joinserver` — подключается к серверу (значение: адрес)
- `disconnect_server_or_world` — отключается и переходит на целевой экран (значение: идентификатор экрана)

Через мост доступно любое действие, существующее в FancyMenu; полный каталог см. в [скриптах действий](./action-scripts).

## 4. Чтение плейсхолдеров

Система [плейсхолдеров] FancyMenu (/placeholders) доступна через `fancymenu.placeholders` (и `FancyMenu.placeholders`). Оба вспомогательных метода возвращают `Promise<string>`:

```ts
fancymenu.placeholders.get(identifier: string): Promise<string>
fancymenu.placeholders.getWithVars(identifier: string, ...vars: string[]): Promise<string>
```

### Передача переменных

- Переменные — это строки в формате `name:value`. Мост разделяет их только по **первому** двоеточию, поэтому значение может содержать дополнительные двоеточия.
- Имена и значения обрезаются по краям; пустые имена отклоняются.
- Передавайте столько переменных, сколько требует плейсхолдер. Необязательные можно пропускать.

### Примеры

```javascript
// Без переменных
fancymenu.placeholders.get('playername')
    .then(name => console.log('Игрок:', name));

// Одна переменная
fancymenu.placeholders.getWithVars('uptime_duration', 'output_as_millis:false')
    .then(seconds => console.log('Время работы (с):', seconds));

// Несколько переменных
fancymenu.placeholders.getWithVars(
    'split_text',
    'input:apple|banana|carrot',
    'regex:\\|',
    'max_parts:-1',
    'split_index:1'
).then(part => console.log('Выбранная часть:', part));
```

### Модель ошибок

Отклонённые Promise содержат структурированную ошибку:

```ts
interface PlaceholderError {
    code: 'NOT_FOUND' | 'MISSING_VARIABLE' | 'INVALID_VARIABLE' | 'EVALUATION_ERROR' | 'INTERNAL_ERROR';
    message: string;
    details?: unknown;
}
```

Пример обработки:

```javascript
fancymenu.placeholders.get('unknown')
    .catch(error => console.warn(error.code, error.message));
```

## 5. Полный пример

```html
<!DOCTYPE html>
<html>
<head>
    <title>Интеграция FancyMenu</title>
</head>
<body>
    <h1>Управление игрой</h1>
    
    <button onclick="quitGame()">Выйти из игры</button>
    <button onclick="openTitleScreen()">Экран заголовка</button>
    <button onclick="disconnectFromServer()">Отключиться</button>
    <button onclick="setVariable()">Задать переменную</button>
    <button onclick="loadPlaceholders()">Загрузить плейсхолдеры</button>

    <div id="placeholderOutput" style="margin-top:16px;font-family:monospace"></div>
    
    <script>
        function getActions() {
            if (typeof fancymenu === 'undefined') {
                console.warn('API FancyMenu пока недоступен.');
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
                () => console.log('Экран заголовка открыт!'),
                err => console.error('Ошибка:', err)
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
            var varName = prompt('Имя переменной:');
            var varValue = prompt('Значение переменной:');
            if (varName && varValue) {
                actions.execute('set_variable', varName + ':' + varValue);
            }
        }

        function loadPlaceholders() {
            if (typeof fancymenu === 'undefined' || !fancymenu.placeholders) {
                console.warn('API плейсхолдеров FancyMenu пока недоступен.');
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
                    'Игрок: ' + playerName + '\n' +
                    'Время работы (секунды): ' + uptimeSeconds + '\n' +
                    'Второй фрукт: ' + secondFruit;
            }).catch(error => {
                console.error('Не удалось запросить плейсхолдер:', error);
            });
        }
    </script>
</body>
</html>
```

## 6. Лучшие практики и примечания

- **Определяйте наличие моста** перед использованием или слушайте событие `fancymenu-ready`.
- **Обрабатывайте ошибки** (callback-функции для [действий](/action-scripts), `.catch` для [плейсхолдеров](/placeholders)), чтобы показывать понятные сообщения.
- **Проверяйте входные данные** перед передачей их в действия или переменные [плейсхолдеров](/placeholders).
- **Ограничивайте частоту запросов**; не перегружайте мост частыми вызовами (особенно в циклах обновления плейсхолдеров).
- **Безопасность:** браузерный контент может вызывать любое зарегистрированное действие FancyMenu, включая действия с файлами, сетью, командами, буфером обмена, ресурс-паками, ссылками и выходом из игры. Загружайте только доверенные страницы и проверяйте все данные, полученные из веб-контента.

## 7. Устранение неполадок

1. Убедитесь, что страница загружена в браузере Rinku, управляемом FancyMenu.
2. Проверьте консоль браузера на наличие ошибок JavaScript.
3. Убедитесь, что идентификатор [плейсхолдера](/placeholders) или тип [действия](/action-scripts) указан правильно и все требуемые значения переданы.
4. Если выполнение неожиданно завершается с ошибкой, проверьте журнал Minecraft (`latest.log`) на наличие сообщений об ошибках FancyMenu.
