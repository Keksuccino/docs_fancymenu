---
title: Обмін даними між клієнтом і сервером
description: >-
  Надсилайте й отримуйте власні дані між сервером і клієнтом за допомогою
  FancyMenu.
sourceBlobSha: 35ae4605e43ac917f11c24e5d97a5c311c9aa01a
---

# FM Data

Система «FM Data» дає змогу надсилати власні текстові дані між сервером і клієнтом.

Для кожної підкоманди `/fmdata` потрібен **рівень дозволів 2** (Game Master / рівень OP 2).

Кожне повідомлення FM Data містить:

1. **Ідентифікатор даних** (тип повідомлення)
2. **Значення даних** (власне вміст)

Приклад:

- Ідентифікатор: `hud.food`
- Дані: `18/20`

# Швидкий початок

1. Сервер надсилає дані за допомогою `/fmdata send ...`
2. Клієнт отримує їх за допомогою слухача FancyMenu **Після отримання FM Data**
3. Клієнт також може надіслати дані у відповідь за допомогою дії **Надіслати FM Data на сервер**
4. Сервер може автоматично реагувати за допомогою `/fmdata listener ...`
5. Сервер може автоматично надсилати дані під час входу за допомогою `/fmdata welcome_data ...`

# Сервер -> Клієнт

Використовуйте:

```mcfunction
/fmdata send <target_players> <data_identifier> <string_data>
```

Приклади:

```mcfunction
/fmdata send Player761 hud.food 18/20
/fmdata send @a "food value update" "18 of 20"
```

Примітки:

- У `<target_players>` можна вказувати імена гравців і селектори, як-от `@a`, `@p` та `@s`
- Значення, що містять пробіли, потрібно брати в лапки

# Клієнт: отримання даних

Використовуйте слухач FancyMenu:

- **Після отримання FM Data**

Доступні змінні:

- `$$data_identifier`
- `$$data`
- `$$sent_by`

Значення `$$sent_by`:

- IP-адреса сервера в мережевій грі
- `integrated_server` в одиночній грі

Типові сценарії використання:

- Оновлення текстових елементів
- Запуск дій меню
- Виконання логіки на основі отриманого ідентифікатора/значення даних

# Клієнт -> Сервер

Використовуйте дію FancyMenu:

- **Надіслати FM Data на сервер**

Дія має два поля:

1. Ідентифікатор даних
2. Дані

Після цього сервер може обробити отримані дані за допомогою `/fmdata listener ...`.

# Слухачі сервера

Слухачі сервера очікують на дані від клієнтів і можуть виконувати одну або кілька команд після спрацювання.

Слухачі зберігаються й залишаються активними після перезапуску.

Керування слухачами:

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

## Типи зіставлення

Для `matching_type_identifier` і `matching_type_data` можна вказати:

- `equals`
- `contains`
- `starts_with`
- `ends_with`

## Правила зіставлення

- `ignore_case_identifier` і `ignore_case_data` — перемикачі зі значенням true/false
- Для `listen_for_identifier` підтримується символ узагальнення `*` (завжди відповідає)
- Для `listen_for_data` підтримується символ узагальнення `*` (завжди відповідає)
- У `fire_for_player` використовуються звичайні селектори гравців (наприклад, `@a`, `@p`, `Player761`)

## Команди після спрацювання

`commands_to_execute_on_fire` — це одне текстове поле.

- Розділяйте кілька команд за допомогою `|||`
- Щоб використати роздільник як звичайний текст, екрануйте його: `\|\|\|`

Тут можна використовувати два спеціальні заповнювачі, які замінюються безпосередньо перед виконанням команд:

- `%fm_sender%` -> гравець, який надіслав FM Data
- `%fm_data%` -> значення даних, отримане від клієнта

Команди виконуються як команди сервера.

## Приклади команд

Реагувати на натискання кнопки будь-яким гравцем:

```mcfunction
/fmdata listener add button_ping equals equals false false @a ui.button pressed "tellraw @a {\"text\":\"%fm_sender% pressed the button\"}"
```

Виконувати кілька команд, коли дані містять `gold`:

```mcfunction
/fmdata listener add reward equals contains false true @a reward "gold" "say Reward from %fm_sender%: %fm_data%|||effect give %fm_sender% minecraft:speed 3 1 true"
```

# Привітальні дані

Привітальні дані надсилають FM Data гравцям, які відповідають заданим умовам, коли вони приєднуються до гри.

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

- Для `<target_player>` підтримуються звичайні селектори, як-от `@a`, `@p`, `@s`
- Дані надсилаються гравцям, які відповідають умовам, коли вони приєднуються до гри
- Записи зберігаються та завантажуються автоматично

## Приклади команд

Надсилати привітальні дані всім гравцям, які приєднуються:

```mcfunction
/fmdata welcome_data add welcome_all @a hud.welcome "Welcome!"
```

Надсилати привітальні дані лише одному гравцеві:

```mcfunction
/fmdata welcome_data add welcome_vip Player761 hud.vip "VIP perks enabled"
```

# Експорт для ШІ

Щоб отримати допомогу від Alice або іншого ШІ, експортуйте слухачі й привітальні дані сервера за допомогою [Експорту для ШІ](/export-for-ai#servers):

```mcfunction
/fmdata export_for_ai copy
/fmdata export_for_ai file
```

`copy` надсилає повідомлення в чаті, натискання на яке копіює експорт. `file` зберігає його на сервері в `fancymenu_data/ai_exports/`.

# Рекомендації

1. Використовуйте зрозумілі ідентифікатори, як-от `hud.food`, `menu.shop.open`, `quest.progress`.
2. Дотримуйтеся єдиного формату даних для кожного ідентифікатора.
3. Почніть із простого: перевірте роботу за допомогою `/fmdata send`, перш ніж створювати складні слухачі.
4. Використовуйте `@a` лише тоді, коли справді потрібна дія для всіх гравців.
5. Використовуйте `/fmdata listener list` і `/fmdata welcome_data list`, щоб підтримувати порядок у налаштуваннях.
