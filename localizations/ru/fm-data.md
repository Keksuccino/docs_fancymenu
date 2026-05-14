---
title: Обмен данными между клиентом и сервером
description: >-
  Отправляйте и получайте пользовательские данные между сервером и клиентом с
  помощью FancyMenu.
---

# FM Data

Система «FM Data» позволяет отправлять пользовательские текстовые данные между сервером и клиентом.

Каждое сообщение FM Data состоит из:

1. **Идентификатора данных** (какой это тип сообщения)
2. **Значения данных** (самого содержимого)

Пример:

- Идентификатор: `hud.food`
- Данные: `18/20`

# Быстрый старт

1. Сервер отправляет данные с помощью `/fmdata send ...`
2. Клиент получает их через обработчик FancyMenu **On FM Data Received**
3. Клиент также может отправить данные обратно с помощью действия **Send FM Data To Server**
4. Сервер может автоматически реагировать через `/fmdata listener ...`
5. Сервер может автоматически отправлять данные при входе игрока с помощью `/fmdata welcome_data ...`

# Сервер -> Клиент

Используйте:

```mcfunction
/fmdata send <target_player> <data_identifier> <string_data>
```

Примеры:

```mcfunction
/fmdata send Player761 hud.food 18/20
/fmdata send @a "food value update" "18 of 20"
```

Примечания:

- `<target_player>` поддерживает обычные селекторы игроков, такие как `@a`, `@p`, `@s`
- Для значений с пробелами используйте кавычки

# Клиент: получение данных

Используйте обработчик FancyMenu:

- **On FM Data Received**

Доступные переменные:

- `$$data_identifier`
- `$$data`
- `$$sent_by`

`$$sent_by` — это:

- IP сервера в многопользовательской игре
- `integrated_server` в одиночной игре

Частые сценарии использования:

- Обновление текстовых элементов
- Запуск действий меню
- Выполнение логики на основе входящего идентификатора/данных

# Клиент -> Сервер

Используйте действие FancyMenu:

- **Send FM Data To Server**

У действия 2 поля ввода:

1. Идентификатор данных
2. Данные

После этого сервер может обработать входящие данные через `/fmdata listener ...`.

# Серверные слушатели

Серверные слушатели отслеживают входящие данные от клиентов и могут выполнять одну или несколько команд при срабатывании.

Серверные слушатели сохраняются и остаются активными после перезапуска.

Управление ими:

- `/fmdata listener list`
- `/fmdata listener add ...`
- `/fmdata listener edit ...`
- `/fmdata listener remove ...`

## Синтаксис добавления / редактирования

```mcfunction
/fmdata listener add <unique_listener_name> <matching_type_identifier> <matching_type_data> <ignore_case_identifier> <ignore_case_data> <fire_for_player> <listen_for_identifier> <listen_for_data> <commands_to_execute_on_fire>
```

```mcfunction
/fmdata listener edit <listener_name> <matching_type_identifier> <matching_type_data> <ignore_case_identifier> <ignore_case_data> <fire_for_player> <listen_for_identifier> <listen_for_data> <commands_to_execute_on_fire>
```

## Синтаксис удаления

```mcfunction
/fmdata listener remove <listener_name>
```

## Типы сопоставления

`matching_type_identifier` и `matching_type_data` могут быть:

- `equals`
- `contains`
- `starts_with`
- `ends_with`

## Правила сопоставления

- `ignore_case_identifier` и `ignore_case_data` — это переключатели true/false
- `listen_for_identifier` поддерживает подстановочный знак `*` (всегда совпадает)
- `listen_for_data` поддерживает подстановочный знак `*` (всегда совпадает)
- `fire_for_player` использует обычные селекторы игроков (например, `@a`, `@p`, `Player761`)

## Команды при срабатывании

`commands_to_execute_on_fire` — это одно текстовое поле.

- Несколько команд разделяйте с помощью `|||`
- Чтобы передать буквальный разделитель, экранируйте его как `\|\|\|`

Здесь можно использовать два специальных плейсхолдера, которые заменяются непосредственно перед выполнением команд:

- `%fm_sender%` -> игрок, отправивший FM Data
- `%fm_data%` -> значение данных, полученное от клиента

Команды выполняются как серверные команды.

## Примеры команд

Реагировать на нажатие кнопки от любого игрока:

```mcfunction
/fmdata listener add button_ping equals equals false false @a ui.button pressed "tellraw @a {\"text\":\"%fm_sender% нажал кнопку\"}"
```

Выполнить несколько команд, когда данные содержат `gold`:

```mcfunction
/fmdata listener add reward equals contains false true @a reward "gold" "say Награда от %fm_sender%: %fm_data%|||effect give %fm_sender% minecraft:speed 3 1 true"
```

# Приветственные данные

Приветственные данные отправляют FM Data подходящим игрокам, когда они заходят на сервер.

Управление записями:

- `/fmdata welcome_data list`
- `/fmdata welcome_data add ...`
- `/fmdata welcome_data edit ...`
- `/fmdata welcome_data remove ...`

## Синтаксис добавления / редактирования

```mcfunction
/fmdata welcome_data add <unique_welcome_data_name> <target_player> <data_identifier> <string_data>
```

```mcfunction
/fmdata welcome_data edit <welcome_data_name> <target_player> <data_identifier> <string_data>
```

## Синтаксис удаления

```mcfunction
/fmdata welcome_data remove <welcome_data_name>
```

Примечания:

- `<target_player>` поддерживает обычные селекторы, такие как `@a`, `@p`, `@s`
- Данные отправляются подходящим игрокам при их входе
- Записи сохраняются и загружаются автоматически

## Примеры команд

Отправлять приветственные данные всем игрокам, которые заходят:

```mcfunction
/fmdata welcome_data add welcome_all @a hud.welcome "Добро пожаловать!"
```

Отправлять приветственные данные только одному игроку:

```mcfunction
/fmdata welcome_data add welcome_vip Player761 hud.vip "VIP-привилегии включены"
```

# Лучшие практики

1. Используйте понятные идентификаторы, например `hud.food`, `menu.shop.open`, `quest.progress`.
2. Сохраняйте единый формат данных для каждого идентификатора.
3. Начинайте с простого: сначала протестируйте `/fmdata send`, а уже потом создавайте сложные слушатели.
4. Используйте `@a` только если вам действительно нужно глобальное поведение.
5. Используйте `/fmdata listener list` и `/fmdata welcome_data list`, чтобы поддерживать конфигурации в порядке.
