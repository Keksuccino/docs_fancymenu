---
title: JavaScript API браузера
description: >-
  Как использовать JavaScript API FancyMenu в функциях мода на базе MCEF, таких
  как элемент Browser.
---
# JavaScript API FancyMenu

FancyMenu внедряет JavaScript-мост в каждую функцию, основанную на MCEF (например, в элемент **Browser**). Этот мост позволяет веб-контенту:

- запускать любые [действия](./action-scripts) FancyMenu напрямую из JavaScript,
- асинхронно читать любые [плейсхолдеры](/placeholders) FancyMenu.

Два глобальных объекта предоставляют API:
- `window.fancymenu` — основной namespace
- `window.FancyMenu` — псевдоним (повторяет точную структуру `fancymenu`)

Используйте событие `fancymenu-ready` или проверку наличия, чтобы убедиться, что мост доступен, прежде чем вызывать его.

## 1. Namespace и структура

- `fancymenu.actions` — выполнение действий FancyMenu из браузера.
- `fancymenu.placeholders` — асинхронное чтение значений плейсхолдеров FancyMenu.
- `FancyMenu` повторяет `fancymenu`, поэтому оба объекта предоставляют одинаковые подпространства имен.

Действия предоставляют два вспомогательных метода:
- `fancymenu.actions.execute(actionType, actionValue?)`
- `fancymenu.actions.executeWithCallback(actionType, actionValue?, onSuccess?, onFailure?)`

## 2. Доступность

```javascript
if (typeof fancymenu !== 'undefined') {
    // можно безопасно использовать
}

window.addEventListener('fancymenu-ready', () => {
    console.log('API FancyMenu готов');
});
```

Контент также может размещаться локально: поместите HTML-файлы в `<game-directory>/config/fancymenu/assets/` и открывайте их по URL вида `file:///config/fancymenu/assets/<name>.html`.

## 3. Выполнение действий

Используйте namespace `fancymenu.actions`. Каждый вызов повторяет строки действий, используемые в скриптах FancyMenu.

### Быстрые вызовы

```javascript
fancymenu.actions.execute('quitgame');                // действие без значения
fancymenu.actions.execute('opengui', 'title_screen'); // действие со значением
fancymenu.actions.execute('set_variable', 'hp:20');   // значение использует формат name:value
```

### С callback-ами

```javascript
fancymenu.actions.executeWithCallback(
    'opengui',
    'title_screen',
    result => console.log('Главный экран открыт'),
    error  => console.error('Не удалось открыть:', error)
);

// Параметр value необязателен. Если он не указан, callback-и передаются сразу после actionType.
fancymenu.actions.executeWithCallback(
    'quitgame',
    result => console.log('Выход запущен'),
    error  => console.error('Не удалось выйти:', error)
);
```

Наследуемые вспомогательные методы `fancymenu.execute(...)` и `fancymenu.executeWithCallback(...)` по-прежнему перенаправляются в namespace `actions`.

### Распространенные типы действий

- `quitgame` — немедленно выходит из игры (без значения)
- `back_to_last_screen` — возвращает к предыдущему GUI (без значения)
- `opengui` — открывает экран FancyMenu или стандартный экран (значение: идентификатор экрана)
- `openlink` — запускает браузер (значение: URL)
- `sendmessage` — отправляет строку в чат (значение: текст сообщения)
- `set_variable` — задает переменную FancyMenu (значение: `name:value`)
- `joinserver` — подключается к серверу (значение: адрес)
- `disconnect_server_or_world` — отключается и переходит на целевой экран (значение: идентификатор экрана)

Через мост доступно любое действие, существующее в FancyMenu; полный каталог см. в [скриптах действий](./action-scripts).

## 4. Чтение плейсхолдеров

Система [плейсхолдеров](/placeholders) FancyMenu доступна через `fancymenu.placeholders` (и `FancyMenu.placeholders`). Оба вспомогательных метода возвращают `Promise<string>`:

```ts
fancymenu.placeholders.get(identifier: string): Promise<string>
fancymenu.placeholders.getWithVars(identifier: string, ...vars: string[]): Promise<string>
```

### Передача переменных

- Переменные — это строки в формате `name:value`. Мост разделяет их только по **первому** двоеточию, поэтому значение может содержать дополнительные двоеточия.
- Имена и значения обрезаются по пробелам; пустые имена отклоняются.
- Передавайте столько переменных, сколько требует плейсхолдер. Необязательные можно опустить.

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

Отклоненные Promise содержат структурированную ошибку:

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
    <button onclick="openTitleScreen()">Главный экран</button>
    <button onclick="disconnectFromServer()">Отключиться</button>
    <button onclick="setVariable()">Установить переменную</button>
    <button onclick="loadPlaceholders()">Загрузить плейсхолдеры</button>

    <div id="placeholderOutput" style="margin-top:16px;font-family:monospace"></div>
    
    <script>
        function getActions() {
            if (typeof fancymenu === 'undefined') {
                console.warn('API FancyMenu еще недоступен.');
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
                () => console.log('Главный экран открыт!'),
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
                console.warn('API плейсхолдеров FancyMenu еще недоступен.');
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

- **Проверяйте наличие моста** перед использованием или слушайте событие `fancymenu-ready`.
- **Обрабатывайте ошибки** (callback-и для [действий](/action-scripts), `.catch` для [плейсхолдеров](/placeholders)), чтобы показывать полезную обратную связь.
- **Проверяйте вводимые данные** перед передачей их в действия или переменные [плейсхолдеров](/placeholders).
- **Ограничивайте частоту запросов**; не спамьте мост частыми вызовами (особенно в циклах обновления плейсхолдеров).
- **Безопасность:** Контент браузера может вызывать любое зарегистрированное действие FancyMenu, включая действия с файлами, сетью, командами, буфером обмена, ресурс-паками, ссылками и выходом из игры. Загружайте только доверенные страницы и проверяйте все данные, полученные из веб-контента.

## 7. Устранение неполадок

1. Убедитесь, что страница загружена в браузере MCEF, управляемом FancyMenu.
2. Проверьте консоль браузера на наличие ошибок JavaScript.
3. Убедитесь, что [идентификатор плейсхолдера](/placeholders) или тип [действия](/action-scripts) указан правильно и что необходимые значения переданы.
4. Если выполнение неожиданно завершается с ошибкой, проверьте журнал Minecraft (`latest.log`) на наличие сообщений об ошибках FancyMenu.
