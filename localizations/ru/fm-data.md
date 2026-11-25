---
title: Обмен данными между клиентом и сервером
description: >-
  Отправляйте и получайте пользовательские данные между сервером и клиентом с
  помощью FancyMenu.
sourceBlobSha: 35ae4605e43ac917f11c24e5d97a5c311c9aa01a
---

# FM Data

Система «FM Data» позволяет отправлять пользовательские текстовые данные между сервером и клиентом.

Для каждой подкоманды `/fmdata` требуется **уровень разрешений 2** (Игровой мастер / OP уровня 2).

Каждое сообщение FM Data содержит:

1. **Идентификатор данных** (тип сообщения)
2. **Значение данных** (собственно содержимое)

Например:

- Идентификатор: `hud.food`
- Данные: `18/20`

# Быстрый старт

1. Сервер отправляет данные командой `/fmdata send ...`
2. Клиент получает их с помощью обработчика FancyMenu **On FM Data Received**
3. Клиент также может отправить данные обратно с помощью действия **Send FM Data To Server**
4. Сервер может автоматически реагировать на них командой `/fmdata listener ...`
5. Сервер может автоматически отправлять данные при входе командой `/fmdata welcome_data ...`

# Сервер -> клиент

Используйте:

```mcfunction
/fmdata send <target_players> <data_identifier> <string_data>
```

Примеры:

```mcfunction
/fmdata send Player761 hud.food 18/20
/fmdata send @a "food value update" "18 of 20"
```

Примечания:

- `<target_players>` поддерживает имена игроков и селекторы, например `@a`, `@p` и `@s`
- Если значение содержит пробелы, заключите его в кавычки

# Клиент: получение данных

Используйте обработчик FancyMenu:

- **On FM Data Received**

Доступные переменные:

- `$$data_identifier`
- `$$data`
- `$$sent_by`

Значение `$$sent_by`:

- IP-адрес сервера в сетевой игре
- `integrated_server` в одиночной игре

Распространённые сценарии использования:

- Обновление текстовых элементов
- Запуск действий меню
- Выполнение логики на основе полученных идентификатора и данных

# Клиент -> сервер

Используйте действие FancyMenu:

- **Send FM Data To Server**

У действия два поля:

1. Идентификатор данных
2. Данные

После этого сервер может обработать полученные данные командой `/fmdata listener ...`.

# Обработчики сервера

Обработчики сервера отслеживают входящие от клиентов данные и могут выполнять одну или несколько команд при срабатывании.

Обработчики сохраняются и остаются активными после перезапуска.

Управление ими:

- `/fmdata listener list`
- `/fmdata listener add ...`
- `/fmdata listener edit ...`
- `/fmdata listener remove ...`

## Синтаксис добавления и редактирования

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

Для `matching_type_identifier` и `matching_type_data` можно указать:

- `equals`
- `contains`
- `starts_with`
- `ends_with`

## Правила сопоставления

- `ignore_case_identifier` и `ignore_case_data` — переключатели со значениями true/false
- `listen_for_identifier` поддерживает подстановочный символ `*` (совпадает всегда)
- `listen_for_data` поддерживает подстановочный символ `*` (совпадает всегда)
- `fire_for_player` использует обычные селекторы игроков (например, `@a`, `@p`, `Player761`)

## Команды при срабатывании

`commands_to_execute_on_fire` — одно текстовое поле.

- Разделяйте несколько команд последовательностью `|||`
- Чтобы указать этот разделитель как обычный текст, экранируйте его: `\|\|\|`

Здесь можно использовать два специальных заполнителя. Они заменяются непосредственно перед выполнением команд:

- `%fm_sender%` -> игрок, отправивший FM Data
- `%fm_data%` -> значение данных, полученное от клиента

Команды выполняются от имени сервера.

## Примеры команд

Реагировать на нажатие кнопки от любого игрока:

```mcfunction
/fmdata listener add button_ping equals equals false false @a ui.button pressed "tellraw @a {\"text\":\"%fm_sender% нажал кнопку\"}"
```

Выполнять несколько команд, если данные содержат `gold`:

```mcfunction
/fmdata listener add reward equals contains false true @a reward "gold" "say Награда от %fm_sender%: %fm_data%|||effect give %fm_sender% minecraft:speed 3 1 true"
```

# Приветственные данные

Приветственные данные отправляют FM Data подходящим игрокам при входе.

Управление записями:

- `/fmdata welcome_data list`
- `/fmdata welcome_data add ...`
- `/fmdata welcome_data edit ...`
- `/fmdata welcome_data remove ...`

## Синтаксис добавления и редактирования

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

- `<target_player>` поддерживает обычные селекторы, например `@a`, `@p`, `@s`
- Данные отправляются подходящим игрокам при входе
- Записи сохраняются и загружаются автоматически

## Примеры команд

Отправить приветственные данные всем игрокам, которые входят на сервер:

```mcfunction
/fmdata welcome_data add welcome_all @a hud.welcome "Добро пожаловать!"
```

Отправить приветственные данные только одному игроку:

```mcfunction
/fmdata welcome_data add welcome_vip Player761 hud.vip "Преимущества VIP активированы"
```

# Экспорт для ИИ

Чтобы получить помощь от Alice или другого ИИ, экспортируйте обработчики сервера и приветственные данные с помощью команды [Export for AI](/export-for-ai#servers):

```mcfunction
/fmdata export_for_ai copy
/fmdata export_for_ai file
```

`copy` отправляет сообщение в чат: нажмите на него, чтобы скопировать экспорт. `file` сохраняет его на сервере в папке `fancymenu_data/ai_exports/`.

# Рекомендации

1. Используйте понятные идентификаторы, например `hud.food`, `menu.shop.open`, `quest.progress`.
2. Для каждого идентификатора придерживайтесь единого формата данных.
3. Начните с простого: проверьте работу с помощью `/fmdata send`, прежде чем создавать сложные обработчики.
4. Используйте `@a`, только если вам действительно нужно, чтобы действие затрагивало всех игроков.
5. Используйте `/fmdata listener list` и `/fmdata welcome_data list`, чтобы конфигурация оставалась аккуратной.
