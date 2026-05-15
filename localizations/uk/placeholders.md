---
title: Заповнювачі
description: Як використовувати заповнювачі.
---

# Заповнювачі

Заповнювачі — це динамічні значення, які під час використання замінюються на фактичний вміст. У FancyMenu заповнювачі дають змогу вставляти динамічний контент у різні елементи, як-от текст, кнопки та умови завантаження. Думайте про них як про змінні, які обчислюються й замінюються своїми реальними значеннями, коли відображаються ваші макети.

# Загальна інформація

## Базовий синтаксис
Заповнювачі у FancyMenu використовують синтаксис, схожий на JSON:
```
{"placeholder":"modversion","values":{"modid":"fancymenu"}}
```

Наприклад, щоб відобразити ім'я гравця:
```
{"placeholder":"playername"}
```

## Вкладені заповнювачі
Одна з найпотужніших можливостей системи заповнювачів FancyMenu — це вкладати заповнювачі в інші заповнювачі. Це означає, що ви можете використовувати результат одного заповнювача як вхідні дані для іншого.

Приклад вкладених заповнювачів:
```
{"placeholder":"calc","values":{"decimal":"true","expression":"{"placeholder":"maxram"} / 1024"}}
```
У цьому прикладі береться значення максимальної оперативної пам'яті й ділиться на 1024, щоб перетворити МБ на ГБ.

# Використання заповнювачів

Більшість елементів, що мають текстові поля, підтримують заповнювачі. Ви можете побачити, чи підтримує текстове поле заповнювачі, під час його редагування. Якщо під час редагування тексту відкривається повноекранний **текстовий редактор**, це означає, що заповнювачі підтримуються. 

Щоб знайти **список усіх заповнювачів**, просто натисніть кнопку **Заповнювачі** у **верхньому правому куті** **текстового редактора**.

Угорі списку заповнювачів є **рядок пошуку**, який дає змогу шукати заповнювачі.

Натискання на заповнювач у списку вставить його в текстовий вміст.

# Заповнювачі детально

Цей список містить більшість, якщо не всі, заповнювачі, доступні у FancyMenu. Іноді список може бути дещо застарілим через оновлення мода.

## Ім'я гравця (playername)
Повертає ім'я користувача поточного гравця.
```
{"placeholder":"playername"}
```
Приклад виводу: `Steve`

## UUID гравця (playeruuid)
Повертає унікальний ідентифікатор гравця.
```
{"placeholder":"playeruuid"}
```
Приклад виводу: `c8cde7fe-7ced-11eb-9439-0242ac130002`

## Версія Minecraft (mcversion)
Повертає поточну версію Minecraft.
```
{"placeholder":"mcversion"}
```
Приклад виводу: `1.19.2`

## Версія завантажувача модів (loaderver)
Повертає версію завантажувача модів (Forge/Fabric).
```
{"placeholder":"loaderver"}
```
Приклад виводу: `43.2.0`

## Назва завантажувача модів (loadername)
Повертає назву завантажувача модів.
```
{"placeholder":"loadername"}
```
Приклад виводу: `Forge`

## Версія мода (modversion)
Повертає версію вказаного мода.
```
{"placeholder":"modversion","values":{"modid":"fancymenu"}}
```
Приклад виводу: `2.14.9`

## Загальна кількість модів (totalmods)
Повертає загальну кількість установлених модів.
```
{"placeholder":"totalmods"}
```
Приклад виводу: `45`

## Кількість активних модів (loadedmods)
Повертає кількість модів, які наразі завантажені.
```
{"placeholder":"loadedmods"}
```
Приклад виводу: `43`

## Прогрес завантаження світу (world_load_progress)
Повертає поточний прогрес завантаження світу у відсотках.
```
{"placeholder":"world_load_progress"}
```
Приклад виводу: `75`

## Значення опції Minecraft (minecraft_option_value)
Повертає значення параметра Minecraft.
```
{"placeholder":"minecraft_option_value","values":{"name":"fov"}}
```
Приклад виводу: `70`

## Останній світ або сервер (last_world_server)
Повертає інформацію про останній відкритий світ або сервер.
```
{"placeholder":"last_world_server","values":{"type":"both","full_world_path":"true"}}
```
Параметри:
- `type`: Визначає, який тип інформації повертати
  - `"both"`: Повертає останній відкритий світ або сервер (за замовчуванням)
  - `"server"`: Повертає лише якщо останнім був сервер
  - `"world"`: Повертає лише якщо останнім був світ
- `full_world_path`: Керує відображенням шляхів до світу
  - `"true"`: Повертає повний шлях до світу (за замовчуванням)
  - `"false"`: Повертає лише назву світу без шляху (не впливає на сервери)

Приклади:
- Сервер: `mc.hypixel.net`
- Світ із повним шляхом: `saves/New World`
- Світ без повного шляху: `New World`

## Ширина екрана (guiwidth)
Повертає поточну ширину екрана.
```
{"placeholder":"guiwidth"}
```
Приклад виводу: `1920`

## Висота екрана (guiheight)
Повертає поточну висоту екрана.
```
{"placeholder":"guiheight"}
```
Приклад виводу: `1080`

## Ідентифікатор поточного екрана (screenid)
Повертає ідентифікатор поточного екрана.
```
{"placeholder":"screenid"}
```
Приклад виводу: `title_screen`

## Ширина елемента (elementwidth)
Повертає ширину вказаного елемента.
```
{"placeholder":"elementwidth","values":{"id":"my_button"}}
```
Приклад виводу: `200`

## Висота елемента (elementheight)
Повертає висоту вказаного елемента.
```
{"placeholder":"elementheight","values":{"id":"my_button"}}
```
Приклад виводу: `20`

## Позиція елемента X (elementposx)
Повертає позицію X вказаного елемента.
```
{"placeholder":"elementposx","values":{"id":"my_button"}}
```
Приклад виводу: `150`

## Позиція елемента Y (elementposy)
Повертає позицію Y вказаного елемента.
```
{"placeholder":"elementposy","values":{"id":"my_button"}}
```
Приклад виводу: `100`

## Позиція миші X (mouseposx)
Повертає поточну позицію миші по осі X.
```
{"placeholder":"mouseposx"}
```
Приклад виводу: `960`

## Позиція миші Y (mouseposy)
Повертає поточну позицію миші по осі Y.
```
{"placeholder":"mouseposy"}
```
Приклад виводу: `540`

## Кліків за секунду (clicks_per_second)
Повертає поточну кількість кліків за секунду для кнопки миші.
```
{"placeholder":"clicks_per_second","values":{"mouse_button":"left"}}
```
Параметри:
- `mouse_button`: `left` або `right`

Приклад виводу: `8`

## Масштаб GUI (guiscale)
Повертає поточний масштаб GUI.
```
{"placeholder":"guiscale"}
```
Приклад виводу: `2`

## Підпис/текст стандартного віджета (vanillabuttonlabel)
Повертає підпис/текст стандартного віджета або кнопки.
```
{"placeholder":"vanillabuttonlabel","values":{"locator":"some.menu.identifier:505280"}}
```
Приклад виводу: `Options...`

## Значення поля введення тексту (text_input_field_value)
Повертає поточне значення користувацького або стандартного поля введення тексту за ідентифікатором елемента.
```
{"placeholder":"text_input_field_value","values":{"element_identifier":"my_input"}}
```
Приклад виводу: `Hello World`

## Поточне здоров'я гравця (current_player_health)
Повертає поточну кількість очок здоров'я гравця.
```
{"placeholder":"current_player_health"}
```
Приклад виводу: `20.0`

## Максимальне здоров'я гравця (max_player_health)
Повертає максимальну кількість очок здоров'я гравця.
```
{"placeholder":"max_player_health"}
```
Приклад виводу: `20.0`

## Поточне здоров'я гравця (у відсотках) (current_player_health_percent)
Повертає здоров'я гравця у відсотках.
```
{"placeholder":"current_player_health_percent"}
```
Приклад виводу: `100`

## Поточне поглинання гравця (current_player_absorption_health)
Повертає очки поглинання гравця (золоті серця).
```
{"placeholder":"current_player_absorption_health"}
```
Приклад виводу: `4.0`

## Максимальне поглинання гравця (max_player_absorption_health)
Повертає максимальне поглинання здоров'я.
```
{"placeholder":"max_player_absorption_health"}
```
Приклад виводу: `4.0`

## Поточне поглинання гравця (у відсотках) (current_player_absorption_health_percent)
Повертає поглинання гравця у відсотках.
```
{"placeholder":"current_player_absorption_health_percent"}
```
Приклад виводу: `100`

## Поточний рівень голоду гравця (current_player_hunger)
Повертає поточний рівень голоду гравця.
```
{"placeholder":"current_player_hunger"}
```
Приклад виводу: `20`

## Максимальний рівень голоду гравця (max_player_hunger)
Повертає максимальний рівень голоду.
```
{"placeholder":"max_player_hunger"}
```
Приклад виводу: `20`

## Поточний рівень голоду гравця (у відсотках) (current_player_hunger_percent)
Повертає голод гравця у відсотках.
```
{"placeholder":"current_player_hunger_percent"}
```
Приклад виводу: `100`

## Поточна насиченість голоду гравця (current_player_hunger_saturation)
Повертає поточне значення насиченості голоду гравця.
```
{"placeholder":"current_player_hunger_saturation"}
```
Приклад виводу: `5.0`

## Поточна броня гравця (current_player_armor)
Повертає поточне значення броні гравця.
```
{"placeholder":"current_player_armor"}
```
Приклад виводу: `20`

## Міцність броні гравця (player_armor_toughness)
Повертає загальне значення міцності броні гравця.
```
{"placeholder":"player_armor_toughness"}
```
Приклад виводу: `8.0`

## Максимальна броня гравця (max_player_armor)
Повертає максимальне значення броні.
```
{"placeholder":"max_player_armor"}
```
Приклад виводу: `20`

## Поточна броня гравця (у відсотках) (current_player_armor_percent)
Повертає броню гравця у відсотках.
```
{"placeholder":"current_player_armor_percent"}
```
Приклад виводу: `100`

## Поточний рівень кисню гравця (current_player_oxygen)
Повертає поточний рівень кисню гравця (бульбашки повітря).
```
{"placeholder":"current_player_oxygen"}
```
Приклад виводу: `300`

## Максимальний рівень кисню гравця (max_player_oxygen)
Повертає максимальний рівень кисню.
```
{"placeholder":"max_player_oxygen"}
```
Приклад виводу: `300`

## Поточний рівень кисню гравця (у відсотках) (current_player_oxygen_percent)
Повертає рівень кисню гравця у відсотках.
```
{"placeholder":"current_player_oxygen_percent"}
```
Приклад виводу: `100`

## Поточний рівень гравця (current_player_level)
Повертає поточний рівень досвіду гравця.
```
{"placeholder":"current_player_level"}
```
Приклад виводу: `30`

## Поточний досвід гравця (current_player_exp)
Повертає загальну кількість очок досвіду гравця.
```
{"placeholder":"current_player_exp"}
```
Приклад виводу: `1250`

## Прогрес досвіду гравця (у відсотках) (current_player_exp_progress)
Повертає прогрес досвіду гравця до наступного рівня у відсотках.
```
{"placeholder":"current_player_exp_progress"}
```
Приклад виводу: `75`

## Сила атаки гравця (у відсотках) (player_attack_strength)
Повертає перезарядку атаки гравця у відсотках.
```
{"placeholder":"player_attack_strength"}
```
Приклад виводу: `100`

## Режим гри гравця (player_gamemode)
Повертає поточний режим гри гравця.
```
{"placeholder":"player_gamemode"}
```
Приклад виводу: `survival`

## Напрямок погляду гравця (player_view_direction)
Повертає напрямок, у який дивиться гравець.
```
{"placeholder":"player_view_direction"}
```
Приклад виводу: `north`

## Координата X гравця (player_x_coordinate)
Повертає позицію гравця по осі X у світі.
```
{"placeholder":"player_x_coordinate"}
```
Приклад виводу: `125`

## Координата Y гравця (player_y_coordinate)
Повертає позицію гравця по осі Y у світі.
```
{"placeholder":"player_y_coordinate"}
```
Приклад виводу: `64`

## Координата Z гравця (player_z_coordinate)
Повертає позицію гравця по осі Z у світі.
```
{"placeholder":"player_z_coordinate"}
```
Приклад виводу: `-250`

## Поточне здоров'я верхової істоти (current_mount_health)
Повертає поточне здоров'я сутності, на якій їде гравець.
```
{"placeholder":"current_mount_health"}
```
Приклад виводу: `30.0`

## Максимальне здоров'я верхової істоти (max_mount_health)
Повертає максимальне здоров'я сутності, на якій їде гравець.
```
{"placeholder":"max_mount_health"}
```
Приклад виводу: `30.0`

## Поточне здоров'я верхової істоти (у відсотках) (current_mount_health_percent)
Повертає здоров'я верхової істоти у відсотках.
```
{"placeholder":"current_mount_health_percent"}
```
Приклад виводу: `100`

## Поточний індикатор стрибка верхової істоти (у відсотках) (current_mount_jump_meter)
Повертає значення індикатора сили стрибка верхової істоти.
```
{"placeholder":"current_mount_jump_meter"}
```
Приклад виводу: `75`

## Поточне здоров'я боса (у відсотках) (current_boss_health)
Повертає здоров'я активного боса.
```
{"placeholder":"current_boss_health"}
```
Приклад виводу: `150.0`

## Ім'я боса (boss_name)
Повертає ім'я активного боса.
```
{"placeholder":"boss_name","values":{"boss_index":"0","as_json":"false"}}
```
Приклад виводу: `Ender Dragon`

## Кількість босів (boss_count)
Повертає кількість активних босів.
```
{"placeholder":"boss_count"}
```
Приклад виводу: `1`

## Кількість активних ефектів (effects_count)
Повертає кількість активних ефектів зілля.
```
{"placeholder":"effects_count"}
```
Приклад виводу: `3`

## Активний ефект (active_effect)
Повертає інформацію про вказаний активний ефект.
```
{"placeholder":"active_effect","values":{"effect_index":"0"}}
```
Приклад виводу: `minecraft:speed`

## Вибраний слот панелі швидкого доступу (active_hotbar_slot)
Повертає поточний вибраний слот панелі швидкого доступу (0-8).
```
{"placeholder":"active_hotbar_slot"}
```
Приклад виводу: `4`

## Предмет у слоті (slot_item)
Повертає інформацію про предмет у вказаному слоті інвентаря.
```
{"placeholder":"slot_item","values":{"slot":"0"}}
```
Приклад виводу: `minecraft:diamond_sword`

## Кількість предметів у слоті (slot_item_count)
Повертає розмір стека предмета у вказаному слоті інвентаря гравця.
```
{"placeholder":"slot_item_count","values":{"slot":"0"}}
```
Приклад виводу: `64`

## Міцність предмета у слоті (slot_item_durability)
Повертає інформацію про міцність предмета у вказаному слоті інвентаря гравця.
```
{"placeholder":"slot_item_durability","values":{"slot":"0","format":"percentage"}}
```
Параметри:
- `slot`: Номер слота інвентаря гравця.
- `format`: `current`, `remaining`, `max`, `damage`, `percentage` або `percent`.

Приклад виводу: `87`

## Відображувана назва предмета у слоті (slot_item_display_name_fm)
Повертає відображувану назву предмета у вказаному слоті як JSON-текстовий компонент. У режимі спостерігача слоти панелі швидкого доступу можуть повертати назви предметів меню спостерігача, якщо `ignore_spectator` має значення `false`.
```
{"placeholder":"slot_item_display_name_fm","values":{"slot":"0","ignore_spectator":"false"}}
```
Приклад виводу: `{"text":"Diamond Sword","color":"aqua"}`

## Кількість предметів в інвентарі (inventory_item_count)
Повертає загальну кількість предметів указаного типу в інвентарі гравця. Якщо `item` порожній, рахує всі стеки предметів в інвентарі.
```
{"placeholder":"inventory_item_count","values":{"item":"minecraft:diamond"}}
```
Приклад виводу: `12`

## Кількість відновлення голоду предметом у слоті інвентаря (inventory_slot_food_point_restore_amount)
Повертає кількість одиниць голоду, які відновлює харчовий предмет у вказаному слоті інвентаря гравця.
```
{"placeholder":"inventory_slot_food_point_restore_amount","values":{"slot":"0"}}
```
Приклад виводу: `4.0`

## Предмет під курсором в інвентарі (hovered_inventory_item)
Повертає ключ предмета, на який наразі наведено курсор в екрані інвентаря.
```
{"placeholder":"hovered_inventory_item"}
```
Приклад виводу: `minecraft:apple`

## Ігровий час світу (game_time)
Повертає поточний лічильник ігрових тіків.
```
{"placeholder":"game_time"}
```
Приклад виводу: `18000`

## Денний час світу (world_daytime)
Повертає поточний денний час світу.
```
{"placeholder":"world_daytime"}
```
Приклад виводу: `13000`

## Година денного часу світу (world_daytime_hour)
Повертає годинну складову часу світу. За замовчуванням використовується 24-годинний формат; встановіть `twelve_hour_format` у `"true"` для 12-годинного формату.
```
{"placeholder":"world_daytime_hour","values":{"twelve_hour_format":"false"}}
```
Приклад виводу: `12`

## Хвилина денного часу світу (world_daytime_minute)
Повертає хвилинну складову часу світу (00-59).
```
{"placeholder":"world_daytime_minute"}
```
Приклад виводу: `30`

## Складність світу (world_difficulty)
Повертає поточну складність світу.
```
{"placeholder":"world_difficulty"}
```
Приклад виводу: `normal`

## Поточний seed світу (current_world_seed)
Повертає seed поточного одиночного світу. Повертає порожнє значення, коли seed недоступний.
```
{"placeholder":"current_world_seed"}
```
Приклад виводу: `123456789`

## Поточний біом (current_biome)
Повертає біом, у якому наразі перебуває гравець. Встановіть `as_key` у `"false"`, щоб повертати перекладену/відображувану назву, якщо вона доступна.
```
{"placeholder":"current_biome","values":{"as_key":"true"}}
```
Приклад виводу: `minecraft:plains`

## Поточний вимір (current_dimension)
Повертає вимір, у якому наразі перебуває гравець. Встановіть `as_key` у `"false"`, щоб повертати перекладену/відображувану назву, якщо вона доступна.
```
{"placeholder":"current_dimension","values":{"as_key":"true"}}
```
Приклад виводу: `minecraft:overworld`

## Значення gamerule (gamerule_value)
Повертає поточне значення gamerule у завантаженому світі/на сервері. Для серверних світів потрібен FancyMenu на сервері.
```
{"placeholder":"gamerule_value","values":{"name":"doDaylightCycle"}}
```
Приклад виводу: `true`

## Категорія предмета (item_category)
Повертає категорію предмета у творчій вкладці. Встановіть `as_key` у `"true"`, щоб повертати ключ категорії замість назви, що відображається.
```
{"placeholder":"item_category","values":{"item":"minecraft:diamond_sword","as_key":"false"}}
```
Приклад виводу: `Combat`

## Поточний заголовок/підзаголовок HUD (current_title)
Повертає поточний відображуваний текст заголовка.
```
{"placeholder":"current_title","values":{"is_subtitle":"false","as_json":"false"}}
```
Приклад виводу: `Game Over!`

## Повідомлення action bar (action_bar_message_fm)
Повертає поточне стандартне повідомлення action bar над панеллю швидкого доступу.
```
{"placeholder":"action_bar_message_fm"}
```
Приклад виводу: `You may not rest now`

## Час повідомлення action bar (action_bar_message_time_fm)
Повертає, скільки тіків ще буде показано поточне стандартне повідомлення action bar.
```
{"placeholder":"action_bar_message_time_fm"}
```
Приклад виводу: `42`

## Обертання камери X (camera_rotation_x_fm)
Повертає поточний pitch камери в градусах.
```
{"placeholder":"camera_rotation_x_fm"}
```
Приклад виводу: `12.5`

## Обертання камери Y (camera_rotation_y_fm)
Повертає поточний yaw камери в градусах.
```
{"placeholder":"camera_rotation_y_fm"}
```
Приклад виводу: `-90.0`

## Зміна обертання камери X (camera_rotation_delta_x_fm)
Повертає зміну pitch камери за тик.
```
{"placeholder":"camera_rotation_delta_x_fm"}
```
Приклад виводу: `0.4`

## Зміна обертання камери Y (camera_rotation_delta_y_fm)
Повертає зміну yaw камери за тик.
```
{"placeholder":"camera_rotation_delta_y_fm"}
```
Приклад виводу: `-1.2`

## Час відображення підсвіченого предмета (highlighted_item_time_fm)
Повертає, скільки тіків ще буде показано назву підсвіченого предмета над панеллю швидкого доступу.
```
{"placeholder":"highlighted_item_time_fm"}
```
Приклад виводу: `30`

## Прогрес використання предмета гравцем (player_item_use_progress_fm)
Повертає поточний прогрес використання предмета від `0.0` до `1.0`.
```
{"placeholder":"player_item_use_progress_fm"}
```
Приклад виводу: `0.65`

## Зміна позиції гравця по X (player_position_delta_x_fm)
Повертає зміну позиції гравця по осі X за тик.
```
{"placeholder":"player_position_delta_x_fm"}
```
Приклад виводу: `0.0`

## Зміна позиції гравця по Y (player_position_delta_y_fm)
Повертає зміну позиції гравця по осі Y за тик.
```
{"placeholder":"player_position_delta_y_fm"}
```
Приклад виводу: `-0.08`

## Зміна позиції гравця по Z (player_position_delta_z_fm)
Повертає зміну позиції гравця по осі Z за тик.
```
{"placeholder":"player_position_delta_z_fm"}
```
Приклад виводу: `0.12`

## Поточний IP сервера (current_server_ip)
Повертає IP підключеного сервера.
```
{"placeholder":"current_server_ip"}
```
Приклад виводу: `mc.hypixel.net`

## Список гравців світу (world_players_list)
Повертає список усіх гравців, які наразі є у світі.
```
{"placeholder":"world_players_list","values":{"separator":", "}}
```
Приклад виводу: `Steve, Alex, Notch`

## MOTD сервера (servermotd)
Повертає Message of the Day сервера.
```
{"placeholder":"servermotd","values":{"ip":"mc.hypixel.net","line":"1"}}
```
Приклад виводу: `Welcome to Hypixel!`

## ПІНГ сервера (serverping)
Повертає пінг до сервера в мілісекундах.
```
{"placeholder":"serverping","values":{"ip":"mc.hypixel.net"}}
```
Приклад виводу: `54`

## Кількість гравців на сервері (serverplayercount)
Повертає кількість гравців на сервері.
```
{"placeholder":"serverplayercount","values":{"ip":"mc.hypixel.net"}}
```
Приклад виводу: `25000/30000`

## Статус сервера (serverstatus)
Повертає статус сервера онлайн/офлайн.
```
{"placeholder":"serverstatus","values":{"ip":"mc.hypixel.net"}}
```
Приклад виводу: `§aOnline` або `§cOffline`

## Версія сервера (serverversion)
Повертає версію Minecraft сервера.
```
{"placeholder":"serverversion","values":{"ip":"mc.hypixel.net"}}
```
Приклад виводу: `1.19.2`

## Рік (realtimeyear)
Повертає поточний рік.
```
{"placeholder":"realtimeyear"}
```
Приклад виводу: `2024`

## Місяць (realtimemonth)
Повертає поточний місяць (01-12).
```
{"placeholder":"realtimemonth"}
```
Приклад виводу: `01`

## День (realtimeday)
Повертає поточний день місяця (01-31).
```
{"placeholder":"realtimeday"}
```
Приклад виводу: `27`

## Година (realtimehour)
Повертає поточну годину. За замовчуванням використовується 24-годинний формат; встановіть `twelve_hour_format` у `"true"`, щоб використовувати 12-годинний формат.
```
{"placeholder":"realtimehour","values":{"twelve_hour_format":"false","timezone":"system"}}
```
Приклад виводу: `14`

## Хвилина (realtimeminute)
Повертає поточну хвилину (00-59).
```
{"placeholder":"realtimeminute"}
```
Приклад виводу: `30`

## Секунда (realtimesecond)
Повертає поточну секунду (00-59).
```
{"placeholder":"realtimesecond"}
```
Приклад виводу: `45`

## Поточний час у мілісекундах (Unix Timestamp) (unix_time)
Повертає поточний Unix timestamp у мілісекундах.
```
{"placeholder":"unix_time"}
```
Приклад виводу: `1716552478123`

> Реальні часові заповнювачі (`realtimeyear`, `realtimemonth`, `realtimeday`, `realtimehour`, `realtimeminute`, `realtimesecond` і `unix_time`) підтримують значення `timezone`. Використовуйте звичайні Java-ідентифікатори часових поясів, як-от `UTC`, `Europe/Berlin` або `America/New_York`; не вказуйте його або використовуйте `system` для системного часового поясу.
{.is-info}

## Інформація про CPU (cpuinfo)
Повертає інформацію про процесор.
```
{"placeholder":"cpuinfo"}
```
Приклад виводу: `Intel(R) Core(TM) i7-10700K CPU @ 3.80GHz`

## Завантаження CPU (JVM) (jvmcpu)
Повертає використання CPU для JVM у відсотках.
```
{"placeholder":"jvmcpu"}
```
Приклад виводу: `25.5`

## Завантаження CPU (ОС) (oscpu)
Повертає використання CPU операційною системою у відсотках.
```
{"placeholder":"oscpu"}
```
Приклад виводу: `42.8`

## Інформація про GPU (gpuinfo)
Повертає інформацію про відеокарту.
```
{"placeholder":"gpuinfo"}
```
Приклад виводу: `NVIDIA GeForce RTX 3080`

## Версія Java (javaver)
Повертає версію Java.
```
{"placeholder":"javaver"}
```
Приклад виводу: `17.0.2`

## Віртуальна машина Java (jvmname)
Повертає назву Java Virtual Machine.
```
{"placeholder":"jvmname"}
```
Приклад виводу: `OpenJDK 64-Bit Server VM`

## Версія OpenGL (glver)
Повертає версію OpenGL.
```
{"placeholder":"glver"}
```
Приклад виводу: `4.6.0 NVIDIA 516.94`

## Назва операційної системи (osname)
Повертає назву операційної системи.
```
{"placeholder":"osname"}
```
Приклад виводу: `Windows 10`

## FPS (кадри за секунду) (fps)
Повертає поточну кількість кадрів за секунду.
```
{"placeholder":"fps"}
```
Приклад виводу: `120`

## Використана RAM у МБ (usedram)
Повертає обсяг RAM, який зараз використовується (МБ).
```
{"placeholder":"usedram"}
```
Приклад виводу: `4096`

## Максимальна RAM у МБ (maxram)
Повертає максимальний обсяг виділеної RAM (МБ).
```
{"placeholder":"maxram"}
```
Приклад виводу: `8192`

## Використана RAM у %% (percentram)
Повертає відсоток RAM, який зараз використовується.
```
{"placeholder":"percentram"}
```
Приклад виводу: `50`

## Гучність аудіоелемента (audio_element_vol)
Повертає гучність аудіоелемента.
```
{"placeholder":"audio_element_vol","values":{"element_identifier":"background_music"}}
```
Приклад виводу: `0.5`

## Поточний аудіотрек (audio_element_current_track)
Повертає назву треку аудіоелемента.
```
{"placeholder":"audio_element_current_track","values":{"element_identifier":"background_music","display_name_mappings":"track1.ogg=>Cool Track Name"}}
```
Приклад виводу: `Cool Track Name`

## Тривалість аудіо (audio_duration)
Повертає загальну тривалість аудіотреку у форматі MM:SS.
```
{"placeholder":"audio_duration","values":{"element_identifier":"background_music"}}
```
Приклад виводу: `03:45`

## Час відтворення аудіо (audio_playtime)
Повертає поточний час відтворення аудіотреку. Встановіть `show_percentage` у `"true"`, щоб отримати значення прогресу 0-100 замість `MM:SS`.
```
{"placeholder":"audio_playtime","values":{"element_identifier":"background_music","show_percentage":"false"}}
```
Приклад виводу: `01:30` (або `45`, коли `show_percentage` має значення `"true"`)

## Статус відтворення аудіо (audio_playing_state)
Повертає, чи відтворюється аудіоелемент (true/false).
```
{"placeholder":"audio_playing_state","values":{"element_identifier":"background_music"}}
```
Приклад виводу: `true`

## Гучність відеоелемента (video_element_vol)
Повертає рівень гучності відеоелемента (0.0 до 1.0).
```
{"placeholder":"video_element_vol","values":{"element_identifier":"my_video_element"}}
```
Приклад виводу: `0.5`

## Тривалість відеоелемента (video_element_duration)
Повертає загальну тривалість відеоелемента у форматі `MM:SS`. Встановіть `output_as_timestamp` у `"true"`, щоб повернути timestamp у мілісекундах.
```
{"placeholder":"video_element_duration","values":{"element_identifier":"my_video_element","output_as_timestamp":"false"}}
```
Приклад виводу: `02:00` (або `120000`, коли `output_as_timestamp` має значення `"true"`)

## Час відтворення відеоелемента (video_element_playtime)
Повертає поточний час відтворення (прогрес) відеоелемента у форматі `MM:SS`. Встановіть `show_percentage` у `"true"` для значення прогресу 0-100 або `output_as_timestamp` у `"true"` для мілісекунд.
```
{"placeholder":"video_element_playtime","values":{"element_identifier":"my_video_element","show_percentage":"false","output_as_timestamp":"false"}}
```
Приклад виводу: `00:45` (або `38` у відсотках, або `45200` як timestamp)

## Статус паузи відеоелемента (video_element_paused_state)
Повертає, чи відеоелемент на паузі (true/false).
```
{"placeholder":"video_element_paused_state","values":{"element_identifier":"my_video_element"}}
```
Приклад виводу: `false`

## Гучність відеофону (video_background_vol)
Повертає рівень гучності відеофону меню (0.0 до 1.0).
```
{"placeholder":"video_background_vol","values":{"background_identifier":"main_menu_video"}}
```
Приклад виводу: `0.7`

## Тривалість відеофону (video_background_duration)
Повертає загальну тривалість відеофону меню у форматі `MM:SS`. Встановіть `output_as_timestamp` у `"true"`, щоб повернути timestamp у мілісекундах.
```
{"placeholder":"video_background_duration","values":{"background_identifier":"main_menu_video","output_as_timestamp":"false"}}
```
Приклад виводу: `03:00` (або `180000`, коли `output_as_timestamp` має значення `"true"`)

## Час відтворення відеофону (video_background_playtime)
Повертає поточний час відтворення (прогрес) відеофону меню у форматі `MM:SS`. Встановіть `show_percentage` у `"true"` для значення прогресу 0-100 або `output_as_timestamp` у `"true"` для мілісекунд.
```
{"placeholder":"video_background_playtime","values":{"background_identifier":"main_menu_video","show_percentage":"false","output_as_timestamp":"false"}}
```
Приклад виводу: `01:00` (або `33` у відсотках, або `60500` як timestamp)

## Статус паузи відеофону (video_background_paused_state)
Повертає, чи відеофон меню на паузі (true/false).
```
{"placeholder":"video_background_paused_state","values":{"background_identifier":"main_menu_video"}}
```
Приклад виводу: `true`

## Калькулятор (calc)
Заповнювач калькулятора — це потужний інструмент, який дає змогу виконувати математичні обчислення всередині ваших макетів. Він підтримує широкий спектр математичних операцій і може працювати як із десятковими, так і з цілими числами.

### Базовий синтаксис
```
{"placeholder":"calc","values":{"decimal":"true/false","expression":"your_expression"}}
```

У калькулятора є два основні параметри:
- `decimal`: Визначає, чи результат має містити десяткові знаки (`true`), чи бути округленим до цілих чисел (`false`)
- `expression`: Математичний вираз для обчислення

### Підтримувані операції
Калькулятор підтримує такі математичні операції:
- Базова арифметика: `+` (додавання), `-` (віднімання), `*` (множення), `/` (ділення)
- Дужки: `( )` для групування операцій
- Степінь: `^` для піднесення до степеня
- Квадратний корінь: `sqrt()`
- Тригонометричні функції: `sin()`, `cos()`, `tan()`
- Математичні константи: `pi`, `e`
- Абсолютне значення: `abs()`
- Логарифми: `log()`, `ln()`

## Випадкове число (random_number)
Генерує випадкове число у вказаному діапазоні.
```
{"placeholder":"random_number","values":{"min":"1","max":"100"}}
```
Приклад виводу: `42`

## Максимальне число (maxnum)
Повертає більше з двох чисел.
```
{"placeholder":"maxnum","values":{"first":"10","second":"20"}}
```
Приклад виводу: `20`

## Мінімальне число (minnum)
Повертає менше з двох чисел.
```
{"placeholder":"minnum","values":{"first":"10","second":"20"}}
```
Приклад виводу: `10`

## Абсолютне число (absnum)
Повертає абсолютне значення числа.
```
{"placeholder":"absnum","values":{"num":"-10.5"}}
```
Приклад виводу: `10.5`

## Заперечити число (negnum)
Повертає заперечене значення числа.
```
{"placeholder":"negnum","values":{"num":"10.5"}}
```
Приклад виводу: `-10.5`

## *pi* (Математика) (math_pi)
Повертає значення π.
```
{"placeholder":"math_pi"}
```
Приклад виводу: `3.141592653589793`

## Тригонометричний синус (Математика) (math_sin)
Повертає синус кута.
```
{"placeholder":"math_sin","values":{"angle":"45"}}
```
Приклад виводу: `0.7071067811865476`

## Тригонометричний косинус (Математика) (math_cos)
Повертає косинус кута.
```
{"placeholder":"math_cos","values":{"angle":"45"}}
```
Приклад виводу: `0.7071067811865476`

## Тригонометричний тангенс (Математика) (math_tan)
Повертає тангенс кута.
```
{"placeholder":"math_tan","values":{"angle":"45"}}
```
Приклад виводу: `1.0`

## Підлога (Математика) (math_floor)
Округлює число вниз до найближчого цілого.
```
{"placeholder":"math_floor","values":{"num":"3.14"}}
```
Приклад виводу: `3`

## Стеля (Математика) (math_ceil)
Округлює число вгору до найближчого цілого.
```
{"placeholder":"math_ceil","values":{"num":"3.14"}}
```
Приклад виводу: `4`

## Округлення (Математика) (math_round)
Округлює число. За замовчуванням до найближчого цілого; встановіть `decimals` у невід'ємне число, щоб округлити до потрібної кількості знаків після коми.
```
{"placeholder":"math_round","values":{"num":"3.14159","decimals":"2"}}
```
Приклад виводу: `3.14` (із `decimals:-1` або якщо параметр відсутній → `3`)

## Знак (Математика) (math_sign)
Повертає знак числа (1 для додатного, -1 для від'ємного, 0 для нуля).
```
{"placeholder":"math_sign","values":{"num":"-3.14"}}
```
Приклад виводу: `-1`

## Гіперболічний синус (Математика) (math_sinh)
Повертає гіперболічний синус кута.
```
{"placeholder":"math_sinh","values":{"angle":"1"}}
```
Приклад виводу: `1.1752011936438014`

## Гіперболічний косинус (Математика) (math_cosh)
Повертає гіперболічний косинус кута.
```
{"placeholder":"math_cosh","values":{"angle":"1"}}
```
Приклад виводу: `1.5430806348152437`

## Гіперболічний тангенс (Математика) (math_tanh)
Повертає гіперболічний тангенс кута.
```
{"placeholder":"math_tanh","values":{"angle":"1"}}
```
Приклад виводу: `0.7615941559557649`

## Розділити текст (split_text)
Розділяє текст за вказаним роздільником.
```
{"placeholder":"split_text","values":{"input":"hello,world","regex":",","max_parts":"2","split_index":"1"}}
```
Приклад виводу: `world`

## Обрізати пробіли в тексті (trim_text)
Видаляє пробіли на початку та в кінці.
```
{"placeholder":"trim_text","values":{"text":"  hello world  "}}
```
Приклад виводу: `hello world`

## Обрізати текст (crop_text)
Видаляє символи на початку та в кінці тексту.
```
{"placeholder":"crop_text","values":{"text":"hello world","remove_from_start":"1","remove_from_end":"1"}}
```
Приклад виводу: `ello worl`

## Рядок як літерал (stringify)
Перетворює текст у рядок, екрануючи всі синтаксичні символи.
```
{"placeholder":"stringify","values":{"text":"text with {special} \"characters\""}}
```
Приклад виводу: `text with \{special\} \"characters\"`

## Локалізований текст (local)
Повертає локалізований текст за ключем.
```
{"placeholder":"local","values":{"key":"menu.singleplayer"}}
```
Приклад виводу: `Singleplayer`

## Вебтекст (webtext)
Отримує текстовий вміст із веб-URL.
```
{"placeholder":"webtext","values":{"link":"http://somewebsite.com/textfile.txt"}}
```
Приклад виводу: Текстовий вміст з URL

## Випадковий текст (randomtext)
Повертає випадковий рядок із текстового файла, URL або безпосередньо введеного звичайного тексту. Текст змінюється через вказані інтервали.
```
{"placeholder":"randomtext","values":{"source":"/config/fancymenu/assets/<file_name.txt>","interval":"10"}}
```
Параметри:
- `source`: Джерело текстових рядків (замінює старий параметр `path`)
  - Шлях до файла: `/config/fancymenu/assets/quotes.txt`
  - URL: `https://example.com/quotes.txt`
  - Звичайний текст: `Line 1\nLine 2\nLine 3`
- `interval`: Час у секундах між змінами тексту

Заповнювач тепер підтримує три типи джерел:
1. **Локальні файли**: Текстові файли з вашого каталогу гри
   ```
   {"placeholder":"randomtext","values":{"source":"/config/fancymenu/assets/quotes.txt","interval":"10"}}
   ```
2. **URL**: Віддалені текстові файли з інтернету
   ```
   {"placeholder":"randomtext","values":{"source":"https://example.com/quotes.txt","interval":"10"}}
   ```
3. **Звичайний текст**: Прямий текстовий ввід із рядками, розділеними `\n`
   ```
   {"placeholder":"randomtext","values":{"source":"First line\nSecond line\nThird line","interval":"5"}}
   ```

Примітка: Старі заповнювачі, що використовують `path` замість `source`, продовжать працювати.

## Парсер JSON (json)
Розбирає JSON-дані з файла, URL або безпосереднього JSON-вмісту та витягує значення за допомогою JSON path-виразів.
```
{"placeholder":"json","values":{"source":"path_or_link_or_json_content","json_path":"$.some.json.path"}}
```
Параметри:
- `source`: Джерело JSON-даних
  - Шлях до файла: `/config/fancymenu/assets/data.json`
  - URL: `https://api.example.com/data.json`
  - Прямий JSON: `{"name":"Steve","level":42}`
- `json_path`: JSON path-вираз для витягування даних

Заповнювач тепер підтримує три типи джерел:
1. **Локальні файли**: JSON-файли з вашого каталогу гри
   ```
   {"placeholder":"json","values":{"source":"/config/fancymenu/assets/playerdata.json","json_path":"$.player.name"}}
   ```
2. **URL**: Віддалені JSON-дані з API або вебсервісів
   ```
   {"placeholder":"json","values":{"source":"https://api.minecraft.com/server/status","json_path":"$.online"}}
   ```
3. **Прямий JSON**: Вбудований JSON-вміст
   ```
   {"placeholder":"json","values":{"source":"{"name":"Steve","score":42,"rank":"Diamond"}","json_path":"$.rank"}}
   ```

Приклади JSON path:
- `$.name` - Отримує поле "name" з кореня
- `$.player.level` - Отримує вкладене поле "level" всередині "player"
- `$.items[0].id` - Отримує "id" першого елемента в масиві
- `$.scores.*` - Отримує всі значення з об'єкта "scores"

## Абсолютний шлях до файла/папки (absolute_path)
Повертає абсолютний шлях до файла.
```
{"placeholder":"absolute_path","values":{"short_path":"relative/path/to/file.txt"}}
```
Приклад виводу: `C:/Users/Username/AppData/Roaming/.minecraft/relative/path/to/file.txt`

## Кількість символів у тексті (text_character_count)
Повертає кількість символів у вказаному тексті.
```
{"placeholder":"text_character_count","values":{"text":"Hello World!"}}
```
Приклад виводу: `12`

## Ширина тексту (text_width)
Повертає ширину в пікселях вказаного тексту під час відображення.
```
{"placeholder":"text_width","values":{"text":"Hello World!"}}
```
Приклад виводу: `66`

## Текст великими літерами (uppercase_text)
Перетворює введений текст на великі літери.
```
{"placeholder":"uppercase_text","values":{"text":"Hello World"}}
```
Приклад виводу: `HELLO WORLD`

## Текст малими літерами (lowercase_text)
Перетворює введений текст на малі літери.
```
{"placeholder":"lowercase_text","values":{"text":"Hello World"}}
```
Приклад виводу: `hello world`

## Текст у форматі Title Case (title_case_text)
Перетворює введений текст у формат Title Case.
```
{"placeholder":"title_case_text","values":{"text":"hello world"}}
```
Приклад виводу: `Hello World`

## Текст у форматі речення (sentence_case_text)
Перетворює введений текст у формат речення.
```
{"placeholder":"sentence_case_text","values":{"text":"hello world. this is fancymenu!"}}
```
Приклад виводу: `Hello world. This is fancymenu!`

## Текст у snake_case (snake_case_text)
Перетворює введений текст у `snake_case`.
```
{"placeholder":"snake_case_text","values":{"text":"Hello World"}}
```
Приклад виводу: `hello_world`

## Текст у kebab-case (kebab_case_text)
Перетворює введений текст у `kebab-case`.
```
{"placeholder":"kebab_case_text","values":{"text":"Hello World"}}
```
Приклад виводу: `hello-world`

## Текст з чергуванням регістру (alternating_case_text)
Перетворює введений текст у чергування регістру.
```
{"placeholder":"alternating_case_text","values":{"text":"alternating case"}}
```
Приклад виводу: `aLtErNaTiNg CaSe`

## Перемикання регістру тексту (toggle_case_text)
Змінює регістр кожної літери у введеному тексті.
```
{"placeholder":"toggle_case_text","values":{"text":"Toggle Case"}}
```
Приклад виводу: `tOGGLE cASE`

## Кодувати в Base64 (base64_encode)
Кодує вказаний текст у Base64.
```
{"placeholder":"base64_encode","values":{"text":"Hello World"}}
```
Приклад виводу: `SGVsbG8gV29ybGQ=`

## Декодувати з Base64 (base64_decode)
Декодує рядок Base64 назад у звичайний текст.
```
{"placeholder":"base64_decode","values":{"text":"SGVsbG8gV29ybGQ="}}
```
Приклад виводу: `Hello World`

## Текст із файла (file_text)
Повертає рядки тексту з файла або URL. Може повертати всі рядки або лише останні X рядків.
```
{"placeholder":"file_text","values":{"path_or_url":"/config/fancymenu/assets/some_file.txt","mode":"all","separator":"\n","last_lines":"1"}}
```
Параметри:
- `path_or_url`: Шлях до файла або URL, з якого читати
- `mode`: Або `"all"` (повертає всі рядки), або `"last"` (повертає лише останні X рядків)
- `separator`: Текст, яким з'єднувати рядки (за замовчуванням: `"\n"`)
- `last_lines`: Кількість рядків, які повертати, коли режим `"last"` (за замовчуванням: `"1"`)

Приклад виводу: Залежить від вмісту файла

## Вміст буфера обміну (clipboard_content)
Повертає поточний текстовий вміст, збережений у системному буфері обміну.
```
{"placeholder":"clipboard_content"}
```
Приклад виводу: Будь-який текст, що наразі є в буфері обміну

## Замінити текст (replace_text)
Замінює текст у рядку за допомогою буквального тексту або регулярних виразів.
```
{"placeholder":"replace_text","values":{"text":"Hello World! This is a test.","search":"World","replacement":"FancyMenu","use_regex":"false","replace_all":"true"}}
```
Параметри:
- `text`: Вхідний текст для обробки
- `search`: Текст або шаблон regex для пошуку
- `replacement`: Текст заміни
- `use_regex`: Чи використовувати regex (`"true"`) чи буквальне зіставлення (`"false"`)
- `replace_all`: Замінити всі входження (`"true"`) чи лише перше (`"false"`)

Приклад виводу: `Hello FancyMenu! This is a test.`

## Перемикання за умовами (switch_case)
Виконує операцію switch-case на основі значення.
```
{"placeholder":"switch_case","values":{"value":"1","cases":"1:first case,2:second case,3:third case","default":"default case"}}
```
Приклад виводу: `first case` (якщо значення — 1)

## Отримати значення змінної (FM Variable) (getvariable)
Отримує значення раніше збереженої змінної.
```
{"placeholder":"getvariable","values":{"name":"some_variable"}}
```
Приклад виводу: Залежить від збереженого значення

## Отримати NBT-дані (nbt_data_get)
Отримує NBT-дані на клієнті (подібно до команди `/data get`). Використовуйте серверний варіант `nbt_data_get_server`, коли ви підключені до сервера і вам потрібні достовірні значення з боку сервера.
```
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"foodLevel","scale":"1.0","return_type":"value"}}
```
Параметри:
- `source_type`: Або `"entity"`, або `"block"`
- `entity_selector`: Селектор сутності, наприклад `@s`, `@p`, `@e` або UUID/ім'я (для сутностей)
- `block_pos`: Позиція блока у форматі `"x y z"` (для блоків)
- `nbt_path`: Шлях NBT, який потрібно отримати
- `scale`: Необов'язковий коефіцієнт масштабування для числових значень (за замовчуванням: `"1.0"`)
- `return_type`: Як повертати дані:
  - `"value"`: За замовчуванням, повертає значення (із необов'язковим масштабуванням для чисел)
  - `"string"`: Повертає фактичні NBT-дані як рядок
  - `"snbt"`: Повертає як SNBT (форматовані NBT-дані)
  - `"json"`: Повертає як JSON-форматований компонент (для compound-тегів)

Приклад виводу: `20` (для рівня голоду)

## Отримати NBT-дані (на стороні сервера) (nbt_data_get_server)
Запитує NBT-дані на стороні сервера (через пакет) і ненадовго кешує результати. Значення відповідають клієнтському заповнювачу.
```
{"placeholder":"nbt_data_get_server","values":{"source_type":"entity","entity_selector":"@s","block_pos":"","storage_id":"minecraft:storage_key","nbt_path":"SelectedItem.id","scale":"1.0","return_type":"value"}}
```
Приклад виводу: `minecraft:diamond_sword`

## Останнє повідомлення про смерть (lastdeathmessage)
Повертає останнє записане повідомлення про смерть клієнтського гравця. Встановіть `as_json_component` у `"true"`, щоб отримати сирий JSON-текстовий компонент.
```
{"placeholder":"lastdeathmessage","values":{"as_json_component":"false"}}
```
Приклад виводу: `Steve was slain by Zombie`

## Тривалість роботи (uptime_duration)
Повертає, як довго FancyMenu завантажено. За замовчуванням значення подається в секундах; встановіть `output_as_millis` у `"true"`, щоб отримати мілісекунди.
```
{"placeholder":"uptime_duration","values":{"output_as_millis":"false"}}
```
Приклад виводу: `742` (секунди від завантаження)

## Назви збережень світу (level_save_names)
Перелічує всі локальні назви збережень світу, з'єднані вибраним роздільником. Виконується в потоці клієнта.
```
{"placeholder":"level_save_names","values":{"separator":", "}}
```
Приклад виводу: `Creative Test, Survival World, Hardcore`

## Дані збереження світу (level_save_data)
Повертає серіалізовані дані рівня для вказаної назви світу (має точно збігатися з назвою, показаною у списку збережень).
```
{"placeholder":"level_save_data","values":{"level_name":"Survival World"}}
```
Приклад виводу: `{"name":"Survival World","gameMode":"survival",...}`

## Перетворення основи чисел (number_base_convert)
Перетворює число (ціле або дробове) з однієї основи в іншу (2–36). За замовчуванням використовується десяткова система, якщо основи не вказані.
```
{"placeholder":"number_base_convert","values":{"input":"67.5","from_base":"10","to_base":"16"}}
```
Приклад виводу: `43.8`

## Розмір файла (file_size)
Повертає розмір локального файла в байтах. Дозволено лише локальні шляхи.
```
{"placeholder":"file_size","values":{"path":"/config/fancymenu/assets/notes.txt"}}
```
Приклад виводу: `1284`

## MD5 файла (file_md5)
Повертає MD5-хеш локального файла у вигляді рядка з малих шістнадцяткових символів.
```
{"placeholder":"file_md5","values":{"path":"/config/fancymenu/assets/notes.txt"}}
```
Приклад виводу: `d41d8cd98f00b204e9800998ecf8427e`

# Практичні приклади

## Створення динамічного відображення пам'яті
```
Used RAM: {"placeholder":"usedram"}MB / {"placeholder":"maxram"}MB ({"placeholder":"percentram"}%)
```

## Створення годинника в реальному часі
```
{"placeholder":"realtimehour"}:{"placeholder":"realtimeminute"}:{"placeholder":"realtimesecond"}
```

## Створення дисплея системної інформації
```
OS: {"placeholder":"osname"}
CPU: {"placeholder":"cpuinfo"}
GPU: {"placeholder":"gpuinfo"}
Java: {"placeholder":"javaver"}
```

## HUD стану гравця
```
Health: {"placeholder":"current_player_health"} / {"placeholder":"max_player_health"} ({"placeholder":"current_player_health_percent"}%)
Armor: {"placeholder":"current_player_armor"} / {"placeholder":"max_player_armor"}
XP Level: {"placeholder":"current_player_level"}
```

## Складне обчислення з вкладеними заповнювачами
```
{"placeholder":"calc","values":{"decimal":"true","expression":"({"placeholder":"usedram"} / {"placeholder":"maxram"}) * 100"}}
```

## Відображення координат з округленням
```
X: {"placeholder":"math_round","values":{"num":"{"placeholder":"player_x_coordinate"}"}}
Y: {"placeholder":"math_round","values":{"num":"{"placeholder":"player_y_coordinate"}"}}
Z: {"placeholder":"math_round","values":{"num":"{"placeholder":"player_z_coordinate"}"}}
```

# Найкращі практики

1. **Кешуйте дорогі операції**: Деякі заповнювачі (наприклад, ті, що читають системну інформацію) можуть бути ресурсоємними. Якщо вам потрібно використовувати їх кілька разів, розгляньте можливість зберігання їхніх значень у змінних.

2. **Використовуйте відповідні налаштування десяткових знаків**: Під час роботи з обчисленнями правильно використовуйте параметр `decimal`. Встановіть його в `false`, коли потрібні цілі числа, і в `true`, коли потрібні точні десяткові значення.

3. **Обробляйте відсутні значення**: Завжди враховуйте, що робити, якщо заповнювач не повертає значення. У таких випадках може знадобитися вказувати значення за замовчуванням.

4. **Перевіряйте продуктивність**: Якщо ви використовуєте багато заповнювачів або складні вкладені структури, перевіряйте вплив на продуктивність, особливо на слабших системах.

5. **Використовуйте розширене налаштування розміру/позиціонування**: Для динамічних елементів інтерфейсу поєднуйте заповнювачі з розширеним налаштуванням розміру та позиціонування, щоб створювати адаптивні макети.

6. **Поєднуйте зі змінними**: Використовуйте заповнювачі разом зі змінними для ще більш динамічного вмісту, який можна оновлювати діями.

# Поширені проблеми та рішення

## Заповнювач не оновлюється
Якщо значення заповнювача не оновлюється так, як очікується, перевірте:
- чи правильно відформатовано заповнювач
- чи використовуєте ви правильний регістр у ідентифікаторах заповнювача
- чи не потрібні заповнювачу спеціальні умови для оновлення

## Вкладені заповнювачі не працюють
Під час вкладення заповнювачів:
- переконайтеся, що лапки правильно екрановано
- перевірте, що кожен вкладений заповнювач сам по собі є валідним

## Проблеми з продуктивністю
Якщо ви помічаєте проблеми з продуктивністю:
- зменште кількість використаних заповнювачів
- уникайте непотрібного вкладення
- розгляньте використання змінних для значень, до яких часто звертаються
- використовуйте відповідний заповнювач для ваших потреб (наприклад, не використовуйте заповнювачі реального часу, якщо достатньо статичних значень)
