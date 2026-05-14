---
title: Обмін даними між клієнтом і сервером
description: >-
  Надсилайте та отримуйте користувацькі дані між сервером і клієнтом за
  допомогою FancyMenu.
---

# FM Data

Система "FM Data" дає змогу надсилати користувацькі текстові дані між сервером і клієнтом.

Кожне повідомлення FM Data має:

1. **Ідентифікатор даних** (що це за тип повідомлення)
2. **Значення даних** (сам вміст)

Приклад:

- Ідентифікатор: `hud.food`
- Дані: `18/20`

# Швидкий старт

1. Сервер надсилає дані за допомогою `/fmdata send ...`
2. Клієнт отримує їх через слухач FancyMenu **On FM Data Received**
3. Клієнт також може надіслати дані назад за допомогою дії **Send FM Data To Server**
4. Сервер може автоматично реагувати через `/fmdata listener ...`
5. Сервер може автоматично надсилати дані під час входу за допомогою `/fmdata welcome_data ...`

# Сервер -> Клієнт

Використовуйте:

```mcfunction
/fmdata send <target_player> <data_identifier> <string_data>
```

Приклади:

```mcfunction
/fmdata send Player761 hud.food 18/20
/fmdata send @a "оновлення значення їжі" "18 із 20"
```

Примітки:

- `<target_player>` підтримує стандартні селектори гравців, як-от `@a`, `@p`, `@s`
- Використовуйте лапки для значень із пробілами

# Клієнт: отримання даних

Використовуйте слухач FancyMenu:

- **On FM Data Received**

Доступні змінні:

- `$$data_identifier`
- `$$data`
- `$$sent_by`

`$$sent_by` — це:

- IP сервера в багатокористувацькій грі
- `integrated_server` в одиночній грі

Типові випадки використання:

- Оновлення текстових елементів
- Запуск дій меню
- Виконання логіки на основі вхідного ідентифікатора/даних

# Клієнт -> Сервер

Використовуйте дію FancyMenu:

- **Send FM Data To Server**

Дія має 2 поля введення:

1. Ідентифікатор даних
2. Дані

Потім сервер може обробляти вхідні дані за допомогою `/fmdata listener ...`.

# Слухачі сервера

Слухачі сервера відстежують вхідні дані від клієнтів і можуть запускати одну або кілька команд, коли спрацьовують.

Слухачі сервера зберігаються та залишаються активними після перезапуску.

Керування ними:

- `/fmdata listener list`
- `/fmdata listener add ...`
- `/fmdata listener edit ...`
- `/fmdata listener remove ...`

## Синтаксис додавання / редагування

```mcfunction
/fmdata listener add <unique_listener_name> <matching_type_identifier> <matching_type_data> <ignore_case_identifier> <ignore_case_data> <fire_for_player> <listen_for_identifier> <listen_for_data> <commands_to_execute_on_fire>
```

```mcfunction
/fmdata listener edit <listener_name> <matching_type_identifier> <matching_type_data> <ignore_case_identifier> <ignore_case_data> <fire_for_player> <listen_for_identifier> <listen_for_data> <commands_to_execute_on_fire>
```

## Синтаксис видалення

```mcfunction
/fmdata listener remove <listener_name>
```

## Типи відповідності

`matching_type_identifier` і `matching_type_data` можуть бути:

- `equals`
- `contains`
- `starts_with`
- `ends_with`

## Правила відповідності

- `ignore_case_identifier` і `ignore_case_data` — це перемикачі true/false
- `listen_for_identifier` підтримує wildcard `*` (завжди збігається)
- `listen_for_data` підтримує wildcard `*` (завжди збігається)
- `fire_for_player` використовує стандартні селектори гравців (наприклад `@a`, `@p`, `Player761`)

## Команди під час спрацювання

`commands_to_execute_on_fire` — це одне текстове поле.

- Для розділення кількох команд використовуйте `|||`
- Щоб екранувати буквальний роздільник, використовуйте `\|\|\|`

Тут можна використовувати два спеціальні заповнювачі, які будуть замінені безпосередньо перед виконанням команд:

- `%fm_sender%` -> гравець, який надіслав FM Data
- `%fm_data%` -> значення даних, отримане від клієнта

Команди виконуються як серверні команди.

## Приклади команд

Реагувати на натискання кнопки від будь-якого гравця:

```mcfunction
/fmdata listener add button_ping equals equals false false @a ui.button pressed "tellraw @a {\"text\":\"%fm_sender% натиснув кнопку\"}"
```

Запустити кілька команд, коли дані містять `gold`:

```mcfunction
/fmdata listener add reward equals contains false true @a reward "gold" "say Нагорода від %fm_sender%: %fm_data%|||effect give %fm_sender% minecraft:speed 3 1 true"
```

# Вітальні дані

Вітальні дані надсилають FM Data відповідним гравцям, коли вони приєднуються.

Керування записами:

- `/fmdata welcome_data list`
- `/fmdata welcome_data add ...`
- `/fmdata welcome_data edit ...`
- `/fmdata welcome_data remove ...`

## Синтаксис додавання / редагування

```mcfunction
/fmdata welcome_data add <unique_welcome_data_name> <target_player> <data_identifier> <string_data>
```

```mcfunction
/fmdata welcome_data edit <welcome_data_name> <target_player> <data_identifier> <string_data>
```

## Синтаксис видалення

```mcfunction
/fmdata welcome_data remove <welcome_data_name>
```

Примітки:

- `<target_player>` підтримує стандартні селектори, як-от `@a`, `@p`, `@s`
- Дані надсилаються відповідним гравцям, коли вони приєднуються
- Записи зберігаються та завантажуються автоматично

## Приклади команд

Надіслати вітальні дані всім гравцям, які входять:

```mcfunction
/fmdata welcome_data add welcome_all @a hud.welcome "Ласкаво просимо!"
```

Надіслати вітальні дані лише одному гравцю:

```mcfunction
/fmdata welcome_data add welcome_vip Player761 hud.vip "Переваги VIP увімкнено"
```

# Кращі практики

1. Використовуйте зрозумілі ідентифікатори, як-от `hud.food`, `menu.shop.open`, `quest.progress`.
2. Для кожного ідентифікатора дотримуйтеся однакового формату даних.
3. Починайте просто: протестуйте з `/fmdata send`, перш ніж будувати складні слухачі.
4. Використовуйте `@a` лише тоді, коли вам справді потрібна глобальна поведінка.
5. Використовуйте `/fmdata listener list` і `/fmdata welcome_data list`, щоб підтримувати конфігурації в порядку.
