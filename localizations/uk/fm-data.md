---
title: Обмін даними між клієнтом і сервером
description: >-
  Надсилайте та отримуйте власні дані між сервером і клієнтом за допомогою
  FancyMenu.
---

# FM Data

Система "FM Data" дає змогу надсилати власні текстові дані між сервером і клієнтом.

Кожна підкоманда `/fmdata` вимагає **рівня дозволів 2** (Game Master / OP level 2).

Кожне повідомлення FM Data має:

1. **Ідентифікатор даних** (який саме це тип повідомлення)
2. **Значення даних** (безпосередній вміст)

Приклад:

- Ідентифікатор: `hud.food`
- Дані: `18/20`

# Швидкий старт

1. Сервер надсилає дані за допомогою `/fmdata send ...`
2. Клієнт отримує їх через слухач FancyMenu **On FM Data Received**
3. Клієнт також може надіслати дані назад за допомогою дії **Send FM Data To Server**
4. Сервер може автоматично реагувати через `/fmdata listener ...`
5. Сервер може автоматично надсилати дані під час входу через `/fmdata welcome_data ...`

# Сервер -> Клієнт

Використовуйте:

```mcfunction
/fmdata send <target_players> <data_identifier> <string_data>
```

Приклади:

```mcfunction
/fmdata send Player761 hud.food 18/20
/fmdata send @a "оновлення значення їжі" "18 із 20"
```

Примітки:

- `<target_players>` підтримує імена гравців та селектори, такі як `@a`, `@p` і `@s`
- Для значень із пробілами використовуйте лапки

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

Типові варіанти використання:

- Оновлення текстових елементів
- Запуск дій меню
- Виконання логіки на основі вхідного ідентифікатора/даних

# Клієнт -> Сервер

Використовуйте дію FancyMenu:

- **Send FM Data To Server**

Дія має 2 поля вводу:

1. Ідентифікатор даних
2. Дані

Потім сервер може обробити вхідні дані за допомогою `/fmdata listener ...`.

# Слухачі сервера

Слухачі сервера відстежують вхідні дані від клієнтів і можуть виконувати одну або кілька команд після спрацьовування.

Слухачі сервера зберігаються та залишаються активними після перезапуску.

Керуйте ними за допомогою:

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
- `fire_for_player` використовує звичайні селектори гравців (наприклад `@a`, `@p`, `Player761`)

## Команди під час спрацьовування

`commands_to_execute_on_fire` — це одне текстове поле вводу.

- Розділяйте кілька команд за допомогою `|||`
- Екрануйте буквальний роздільник як `\|\|\|`

Тут можна використовувати два спеціальні заповнювачі, які замінюються безпосередньо перед виконанням команд:

- `%fm_sender%` -> гравець, який надіслав FM Data
- `%fm_data%` -> значення даних, отримане від клієнта

Команди виконуються як серверні команди.

## Приклади команд

Реакція на натискання кнопки від будь-якого гравця:

```mcfunction
/fmdata listener add button_ping equals equals false false @a ui.button pressed "tellraw @a {\"text\":\"%fm_sender% натиснув кнопку\"}"
```

Виконання кількох команд, коли дані містять `gold`:

```mcfunction
/fmdata listener add reward equals contains false true @a reward "gold" "say Нагорода від %fm_sender%: %fm_data%|||effect give %fm_sender% minecraft:speed 3 1 true"
```

# Привітальні дані

Привітальні дані надсилають FM Data відповідним гравцям, коли вони входять.

Керуйте записами за допомогою:

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

- `<target_player>` підтримує звичайні селектори, такі як `@a`, `@p`, `@s`
- Дані надсилаються відповідним гравцям під час їхнього входу
- Записи зберігаються та завантажуються автоматично

## Приклади команд

Надсилання привітальних даних усім гравцям, що входять:

```mcfunction
/fmdata welcome_data add welcome_all @a hud.welcome "Ласкаво просимо!"
```

Надсилання привітальних даних лише одному гравцеві:

```mcfunction
/fmdata welcome_data add welcome_vip Player761 hud.vip "Увімкнено VIP-переваги"
```

# Найкращі практики

1. Використовуйте зрозумілі ідентифікатори, як-от `hud.food`, `menu.shop.open`, `quest.progress`.
2. Для кожного ідентифікатора підтримуйте однаковий формат даних.
3. Починайте просто: перевірте `/fmdata send`, перш ніж будувати складні слухачі.
4. Використовуйте `@a` лише тоді, коли вам справді потрібна глобальна поведінка.
5. Використовуйте `/fmdata listener list` і `/fmdata welcome_data list`, щоб підтримувати конфігурації в чистоті.
