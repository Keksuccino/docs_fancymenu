---
title: Слухачі
description: Як створювати та використовувати слухачів у FancyMenu.
---

# Слухачі

Починаючи з FancyMenu v3.8.0, з’явилася нова функція під назвою «слухачі».

Слухачі виконують сценарії дій, коли відбуваються певні події клієнта або ігрового процесу.
Вони можуть надавати змінні для дій, заповнювачів і вимог, вкладених у слухача.

На відміну від більшості елементів у FancyMenu, слухачі не прив’язані до екрана або накладки. Вони постійно працюють у фоновому режимі, відстежуючи свої події. Щойно слухач спрацьовує, він виконує свій сценарій дій, навіть якщо в цей момент жоден екран не відкрито.

# Використання слухачів

Щоб створити новий слухач, який відстежує подію та виконує сценарій дій, натисніть **панель меню -> Налаштування -> Керування слухачами**, перебуваючи **НЕ** у редакторі макета. Там ви знайдете зручний інтерфейс для створення та керування слухачами.

<img src="https://github.com/Keksuccino/FancyMenu/blob/master/assets/docs/manage_listeners.png?raw=true" alt="Керування слухачами" style="max-width:800px;width:100%;height:auto;">

# Змінні слухачів

Слухачі часто надають особливий тип змінних для своїх вкладених дій, вимог і заповнювачів.
До цих змінних можна звертатися як до заповнювачів (по суті, це і є заповнювачі).

Ви використовуєте ці змінні, просто вказуючи їхні імена з префіксом `$$` у полях введення тексту, подібно до того, як ви використовували б звичайний заповнювач.

Наприклад, якщо ви використовуєте слухач **On Keyboard Key Pressed** і хочете вивести назву клавіші в лог за допомогою дії **Print to Log**, ви можете вказати щось на кшталт `Key pressed! The key is: $$key_name` як вхідне значення для повідомлення, яке має надрукувати дія. Пізніше заповнювач змінної буде замінено на фактичну назву клавіші.

> Хоча це й називається «змінними», вони жодним чином не пов’язані зі звичайною [системою змінних](/variables) FancyMenu. Ви не можете встановлювати ці змінні, оскільки вони є **лише для читання**. Також ви не можете використовувати для цих спеціальних змінних слухача будь-які дії, вимоги та заповнювачі, призначені для системи змінних FancyMenu, тож використання **Get Variable Value [FM Variable]**, **Is Variable Value [FM Variable]** або **Set Variable Value [FM Variable]** не працюватиме для змінних слухача.
{.is-warning}

# Слухачі докладніше

Цей список має містити більшість, якщо не всі, слухачі FancyMenu. Цілком можливо, що список не завжди є актуальним через оновлення мода.

## On Markdown Text Clicked
- Спрацьовує, коли натискають на Markdown-текст із подією `click:`, наприклад `[Open](click:open_menu)`.
- Змінні:
  - `$$text_event_id` – ID події з Markdown-посилання

## On Markdown Text Hovered
- Спрацьовує, коли на Markdown-тексті з подією `hover:` затримують курсор, наприклад `[Hint](hover:show_hint)`.
- Змінні:
  - `$$text_event_id` – ID події з Markdown-посилання

## On ZIP Extracted via Action
- Спрацьовує, коли дія **Extract ZIP File In Game Directory** завершується.
- Змінні:
  - `$$source_zip_path` – розв’язаний шлях до ZIP-архіву
  - `$$target_folder_path` – розв’язаний шлях до папки розпакування
  - `$$extract_succeeded` – true/false
  - `$$failure_reason` – текст помилки, якщо розпакування не вдалося

## On Element Spawned
- Спрацьовує, коли елемент створюється через дію/сценарій створення елемента.
- Змінні:
  - `$$element_type` – тип створеного елемента
  - `$$element_identifier` – ідентифікатор створеного елемента
  - `$$target_screen` – ідентифікатор цільового екрана

## On Animated Texture Started Playing
- Спрацьовує, коли анімована текстура починає відтворюватися.
- Змінні:
  - `$$texture_source` – джерело текстури
  - `$$texture_source_type` – тип джерела
  - `$$texture_will_restart` – true/false

## On Animated Texture Finished Playing
- Спрацьовує, коли анімована текстура завершує відтворення.
- Змінні:
  - `$$texture_source`
  - `$$texture_source_type`
  - `$$texture_will_restart`

## On Video Playback Status Changed
- Спрацьовує, коли відеоелемент або фон відеоменю змінює статус відтворення.
- Змінні:
  - `$$video_source` – джерело відео
  - `$$video_source_type` – тип джерела
  - `$$is_looping` – true/false
  - `$$new_status` – `PLAYING`, `STOPPED`, `PAUSED` або `FINISHED`

## On System Message Received in Chat
- Спрацьовує, коли клієнт отримує системне чат-повідомлення, наприклад відповідь на команду.
- Змінні:
  - `$$system_message_string` – текстове повідомлення без форматування
  - `$$system_message_component` – JSON-компонент

## On FM Data Received
- Спрацьовує, коли сервер надсилає FM Data цьому клієнту через `/fmdata send`.
- Змінні:
  - `$$data_identifier` – рядок ідентифікатора даних
  - `$$data` – корисне навантаження даних
  - `$$sent_by` – IP сервера або `integrated_server`

## On Remote Server Connected
- Спрацьовує, коли FancyMenu ініціалізує підключення до віддаленого сервера.
- Змінні:
  - `$$request_id` – кешований ID запиту
  - `$$remote_server_url` – URL віддаленого сервера

## On Remote Server Data Received
- Спрацьовує, коли текстові дані отримано від підключеного віддаленого сервера.
- Змінні:
  - `$$request_id` – ID запиту
  - `$$remote_server_url` – URL віддаленого сервера
  - `$$data` – отримане корисне навантаження

## On Remote Server Connection Closed
- Спрацьовує, коли з’єднання з віддаленим сервером закривається.
- Змінні:
  - `$$request_id` – ID запиту
  - `$$remote_server_url` – URL віддаленого сервера
  - `$$intentionally_closed` – TRUE, якщо закрито дією
  - `$$crashed` – TRUE, якщо з’єднання аварійно перервалося
  - `$$unknown_close_reason` – TRUE, якщо невідома причина закриття недоступна

## On Keyboard Key Pressed
- Спрацьовує щоразу, коли натискається клавіша (повторюється, поки клавішу утримують; працює на екранах і в грі).
- Змінні:
  - `$$key_name` – відображувана назва клавіші
  - `$$key_keycode` – код клавіші GLFW
  - `$$key_scancode` – скан-код GLFW
  - `$$key_modifiers` – активна бітова маска модифікаторів

## On Keyboard Key Released
- Спрацьовує, коли клавішу відпускають (на екранах і в грі).
- Змінні:
  - `$$key_name`
  - `$$key_keycode`
  - `$$key_scancode`
  - `$$key_modifiers`

## On Keyboard Character Typed in Screen
- Спрацьовує, коли вводиться символ, поки відкрито екран.
- Змінні:
  - `$$char` – введений символ

## On Mouse Moved in Screen
- Спрацьовує щоразу, коли рухається миша, поки відкрито екран.
- Змінні:
  - `$$mouse_pos_x` – поточний X
  - `$$mouse_pos_y` – поточний Y
  - `$$mouse_move_delta_x` – зміна X від останньої події
  - `$$mouse_move_delta_y` – зміна Y від останньої події

## On Mouse Button Clicked
- Спрацьовує, коли натискається кнопка миші (на екранах і в грі).
- Змінні:
  - `$$button` – ліва/права/середня
  - `$$mouse_pos_x` – поточний X
  - `$$mouse_pos_y` – поточний Y

## On Mouse Button Released
- Спрацьовує, коли кнопку миші відпускають (на екранах і в грі).
- Змінні:
  - `$$button`
  - `$$mouse_pos_x`
  - `$$mouse_pos_y`

## On Mouse Scrolled in Screen
- Спрацьовує, коли прокручують колесо миші, поки відкрито екран.
- Змінні:
  - `$$scroll_delta_y` – величина вертикального прокручування

## On Screen Opened
- Запускається одразу після того, як будь-який екран стає активним; може використовуватися для його перевизначення.
- Змінні:
  - `$$screen_identifier` – ідентифікатор відкритого екрана

## On Screen Closed
- Запускається одразу після закриття екрана.
- Змінні:
  - `$$screen_identifier` – ідентифікатор закритого екрана

## On Quit Minecraft
- Спрацьовує один раз, коли клієнт починає завершення роботи.
- Змінні:
  - `$$timestamp_millis` – epoch millis у момент виходу
  - `$$timestamp_iso` – мітка часу ISO-8601 моменту виходу

## On Death
- Запускається, коли для локального гравця відкривається ванільний екран смерті.
- Змінні:
  - `$$days_survived` – дні від останньої смерті
  - `$$death_reason_string` – причина у вигляді звичайного тексту
  - `$$death_reason_component` – причина як JSON-компонент
  - `$$death_pos_x` – координата X смерті
  - `$$death_pos_y` – координата Y смерті
  - `$$death_pos_z` – координата Z смерті

## On Variable Updated [FM Variable]
- Спрацьовує щоразу, коли змінну FancyMenu встановлено/оновлено.
- Змінні:
  - `$$var_name` – ім’я змінної
  - `$$old_value` – попереднє значення
  - `$$new_value` – нове значення

## On File Downloaded via Action
- Спрацьовує після завершення дії “Download File to Game Directory”.
- Змінні:
  - `$$download_url` – джерело завантаження
  - `$$target_file_path` – шлях до збереженого файла
  - `$$download_succeeded` – true/false

## On File Selected
- Спрацьовує після завершення дії “Select File”.
- Змінні:
  - `$$selected_file_path` – абсолютний шлях до вибраного файла або порожньо, якщо скасовано
  - `$$target_file_path` – розв’язаний шлях усередині інстансу
  - `$$selection_succeeded` – true, якщо копіювання вдалося
  - `$$selection_cancelled` – true, якщо діалог закрито
  - `$$failure_reason` – інформація про помилку у разі збою

## On Chat Message Received
- Спрацьовує, коли звичайне повідомлення гравця з’являється у клієнті.
- Змінні:
  - `$$chat_message_string` – рядок звичайного тексту
  - `$$chat_message_component` – повний JSON-компонент
  - `$$sender_uuid` – UUID відправника або ERROR
  - `$$sender_name` – ім’я відправника або ERROR

## On Chat Message Sent
- Спрацьовує, коли локальний гравець надсилає чат-повідомлення.
- Змінні:
  - `$$chat_message_string` – рядок звичайного тексту
  - `$$chat_message_component` – повний JSON-компонент

## On Effect Gained
- Спрацьовує, коли гравець отримує ефект статусу.
- Змінні:
  - `$$effect_key` – resource location ефекту
  - `$$effect_type` – позитивний/негативний/нейтральний
  - `$$effect_duration` – залишок тіку

## On Effect Lost
- Спрацьовує, коли гравець втрачає ефект статусу.
- Змінні:
  - `$$effect_key` – ефект, що завершився
  - `$$effect_type` – категорія

## On Experience Changed
- Спрацьовує щоразу, коли змінюється загальний досвід гравця.
- Змінні:
  - `$$new_experience_amount` – після зміни
  - `$$old_experience_amount` – до зміни
  - `$$is_level_up` – TRUE, якщо рівень підвищився

## On Damage Taken
- Спрацьовує один раз за удар, коли гравець отримує шкоду.
- Змінні:
  - `$$damage_amount` – кількість втраченої шкоди/здоров’я
  - `$$damage_type` – resource location типу шкоди
  - `$$is_fatal_damage` – TRUE, якщо шкода смертельна
  - `$$damage_source` – resource location нападника або NONE

## On Started Freezing
- Спрацьовує, коли гравець починає замерзати.
- Змінні:
  - `$$freezing_intensity` – 0.0 немає, 1.0 повністю замерз

## On Stopped Freezing
- Спрацьовує, коли гравець перестає замерзати.
- Змінні:
  - (немає)

## On Fully Frozen
- Спрацьовує один раз, коли гравець стає повністю замерзлим.
- Змінні:
  - (немає)

## On Start Looking At Block
- Спрацьовує один раз, коли приціл уперше наводиться на блок (максимальна відстань 20 блоків).
- Змінні:
  - `$$block_key` – цільовий блок
  - `$$block_pos_x` – X блока
  - `$$block_pos_y` – Y блока
  - `$$block_pos_z` – Z блока
  - `$$distance_to_player` – від очей до точки влучання

## On Stop Looking At Block
- Спрацьовує, коли приціл перестає бути наведений на блок (повідомляє про останній цільовий блок, максимум 20 блоків).
- Змінні:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`
  - `$$distance_to_player`

## On Start Looking At Entity
- Спрацьовує один раз, коли приціл уперше наводиться на сутність (максимальна відстань 20 блоків).
- Змінні:
  - `$$entity_key` – тип цільової сутності
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Stop Looking At Entity
- Спрацьовує, коли приціл перестає бути наведений на сутність (повідомляє про останню цільову сутність, максимум 20 блоків).
- Змінні:
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Entity Spawned
- **Потрібен FancyMenu на сервері.** Спрацьовує, коли будь-яка сутність з’являється будь-де у підключеному світі/на сервері.
- Змінні:
  - `$$entity_key`
  - `$$distance_to_player` – −1, якщо в іншому вимірі
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`
  - `$$dimension_key`
  - `$$is_same_dimension_as_player`

## On Entity Died
- **Потрібен FancyMenu на сервері.** Спрацьовує, коли будь-яка сутність помирає у підключеному світі/на сервері.
- Змінні:
  - `$$entity_key`
  - `$$distance_to_player` – −1, якщо в іншому вимірі
  - `$$death_pos_x`
  - `$$death_pos_y`
  - `$$death_pos_z`
  - `$$entity_uuid`
  - `$$dimension_key`
  - `$$damage_type`
  - `$$is_same_dimension_as_player`
  - `$$entity_killed_by_name`
  - `$$entity_killed_by_key`
  - `$$entity_killed_by_uuid`

## On Entity Starts Being In Sight
- Спрацьовує, коли сутність уперше стає видимою в межах 200 блоків.
- Змінні:
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Entity Stops Being In Sight
- Спрацьовує, коли раніше видима сутність зникає з поля зору або віддаляється більш ніж на 200 блоків.
- Змінні:
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Interacted With Entity
- Спрацьовує, коли гравець успішно взаємодіє із сутністю.
- Змінні:
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Entity Mounted
- Спрацьовує, коли гравець починає їхати верхи на сутності.
- Змінні:
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Entity Unmounted
- Спрацьовує, коли гравець перестає їхати верхи на поточній сутності.
- Змінні:
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Block Broke
- Спрацьовує, коли гравець ламає блок.
- Змінні:
  - `$$block_key`
  - `$$broke_with_item_key` – інструмент, що використовувався, або EMPTY
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## On Block Placed
- Спрацьовує, коли гравець ставить блок.
- Змінні:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## On Interacted With Block
- Спрацьовує, коли гравець успішно взаємодіє з блоком.
- Змінні:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## On Stepping On Block
- Спрацьовує, коли гравець стає на блок.
- Змінні:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## On Enter Biome
- Спрацьовує, коли гравець входить у новий біом.
- Змінні:
  - `$$biome_key` – біом, у який увійшли

## On Leave Biome
- Спрацьовує, коли гравець залишає поточний біом.
- Змінні:
  - `$$biome_key` – біом, який щойно залишили

## On Enter Structure
- **Потрібен FancyMenu на сервері.** Грубе визначення зони структури; може спрацьовувати біля/над/під структурою.
- Змінні:
  - `$$structure_key` – структура, у яку увійшли

## On Leave Structure
- **Потрібен FancyMenu на сервері.** Грубе визначення; може спрацьовувати біля контуру структури.
- Змінні:
  - `$$structure_key` – структура, яку щойно залишили

## On Enter Structure (High Precision)
- **Потрібен FancyMenu на сервері.** Спрацьовує, коли гравець заходить у bounding box структури.
- Змінні:
  - `$$structure_key`

## On Leave Structure (High Precision)
- **Потрібен FancyMenu на сервері.** Спрацьовує після того, як гравець виходить із bounding box структури.
- Змінні:
  - `$$structure_key`

## On Dimension Entered
- Спрацьовує, коли гравець входить у новий вимір.
- Змінні:
  - `$$dimension_key` – вимір, у який увійшли

## On Start Swimming
- Спрацьовує, коли гравець починає плавати.
- Змінні:
  - `$$fluid_type` – resource location рідини

## On Stop Swimming
- Спрацьовує, коли гравець перестає плавати.
- Змінні:
  - `$$fluid_type` – рідина, у якій плавання припинилося

## On Start Touching Fluid
- Спрацьовує, коли гравець починає торкатися рідини.
- Змінні:
  - `$$fluid_type` – рідина, якої торкнулися

## On Stop Touching Fluid
- Спрацьовує, коли гравець перестає торкатися рідини.
- Змінні:
  - `$$fluid_type` – рідина, якої більше не торкаються

## On Music Track Started
- Спрацьовує, коли починається новий музичний трек.
- Змінні:
  - `$$track_resource_location` – аудіофайл
  - `$$track_display_name` – зрозуміла назва або UNKNOWN
  - `$$track_artist` – виконавець або UNKNOWN
  - `$$track_duration_ms` – мілісекунди (0, якщо невідомо)

## On Music Track Stopped
- Спрацьовує, коли поточний музичний трек закінчується або замінюється.
- Змінні:
  - `$$track_resource_location`
  - `$$track_display_name`
  - `$$track_artist`
  - `$$track_duration_ms`

## On World Sound Triggered
- Спрацьовує, коли просторовий звуковий ефект світу починає відтворюватися поблизу гравця.
- Змінні:
  - `$$sound_resource_location` – звуковий файл
  - `$$sound_display_name` – назва субтитрів, якщо доступна
  - `$$sound_origin_pos_x`
  - `$$sound_origin_pos_y`
  - `$$sound_origin_pos_z`
  - `$$sound_origin_distance_to_player`
  - `$$sound_origin_direction_from_player` – градуси 0–360 відносно напряму погляду

## On Weather Changed
- Спрацьовує, коли погода змінюється глобально або локально (зміна біому чи захід у приміщення можуть викликати це знову).
- Змінні:
  - `$$weather_type` – clear/rain/thunder
  - `$$weather_can_snow` – TRUE, якщо відображається сніг
  - `$$weather_can_rain` – TRUE, якщо відображається дощ

## On Started Burning
- Спрацьовує, коли гравець починає горіти.
- Змінні:
  - (немає)

## On Stopped Burning
- Спрацьовує, коли гравець перестає горіти.
- Змінні:
  - (немає)

## On Started Drowning
- Спрацьовує, коли гравець починає отримувати шкоду від утоплення.
- Змінні:
  - (немає)

## On Position Changed
- Спрацьовує щоразу, коли змінюється блокова позиція гравця.
- Змінні:
  - `$$old_pos_x` – попередній X блока
  - `$$old_pos_y` – попередній Y блока
  - `$$old_pos_z` – попередній Z блока
  - `$$new_pos_x` – новий X блока
  - `$$new_pos_y` – новий Y блока
  - `$$new_pos_z` – новий Z блока

## On Started Running
- Спрацьовує, коли гравець починає спринтувати.
- Змінні:
  - (немає)

## On Stopped Running
- Спрацьовує, коли гравець перестає спринтувати.
- Змінні:
  - (немає)

## On Jump
- Спрацьовує щоразу, коли гравець стрибає.
- Змінні:
  - (немає)

## On Server Joined
- Спрацьовує після успішного входу на багатокористувацький сервер.
- Змінні:
  - `$$server_ip` – адреса сервера, на який увійшли

## On Server Left
- Спрацьовує після відключення від багатокористувацького сервера.
- Змінні:
  - `$$server_ip` – адреса сервера, який залишили

## Singleplayer World Entered
- Спрацьовує після повного завантаження світу для одиночної гри та повернення керування.
- Змінні:
  - `$$world_name` – відображувана назва
  - `$$world_save_path` – абсолютна папка збереження
  - `$$world_difficulty` – ключ складності
  - `$$world_cheats_allowed` – TRUE, якщо чіти ввімкнено
  - `$$world_icon_path` – абсолютний шлях до іконки
  - `$$world_is_first_join` – TRUE під час першого входу

## Singleplayer World Left
- Спрацьовує після закриття світу одиночної гри та завершення збереження.
- Змінні:
  - `$$world_name`
  - `$$world_save_path`
  - `$$world_difficulty`
  - `$$world_cheats_allowed`
  - `$$world_icon_path`

## On Other Player Joined World/Server
- Спрацьовує, коли інший гравець приєднується до поточного світу/сервера.
- Змінні:
  - `$$player_name` – ім’я гравця, що приєднується
  - `$$player_uuid` – UUID

## On Other Player Left World/Server
- Спрацьовує, коли інший гравець залишає поточний світ/сервер.
- Змінні:
  - `$$player_name`
  - `$$player_uuid`

## On Other Player Died
- Спрацьовує, коли інший гравець у поточному світі помирає.
- Змінні:
  - `$$player_name`
  - `$$player_uuid`
  - `$$death_pos_x`
  - `$$death_pos_y`
  - `$$death_pos_z`

## On Item Picked Up
- Спрацьовує, коли гравець підбирає предмет-об’єкт.
- Змінні:
  - `$$item_key` – resource location підібраного предмета

## On Item Dropped
- Спрацьовує, коли гравець викидає предмет зі свого інвентаря.
- Змінні:
  - `$$item_key` – resource location викинутого предмета

## On Item Consumed
- Спрацьовує, коли гравець завершує споживання предмета.
- Змінні:
  - `$$item_key` – спожитий предмет

## On Item Hovered in Inventory
- Спрацьовує, коли користувач наводить курсор на предмет у будь-якому екрані інвентаря.
- Змінні:
  - `$$item_key` – resource location предмета під курсором
  - `$$item_display_name_string` – назва предмета звичайним текстом
  - `$$item_display_name_json` – назва предмета як JSON-компонент

## On Item Used
- Спрацьовує, коли гравець використовує предмет.
- Змінні:
  - `$$item_key` – використаний предмет
  - `$$used_on_type` – block/entity/self/none
  - `$$used_on_entity_key` – тип цільової сутності або порожньо
  - `$$used_on_block_key` – цільовий блок або порожньо
  - `$$target_pos_x` – цільовий X або -1
  - `$$target_pos_y` – цільовий Y або -1
  - `$$target_pos_z` – цільовий Z або -1

## On Item Broke
- Спрацьовує, коли предмет в інвентарі гравця ламається.
- Змінні:
  - `$$item_key` – зламаний предмет
  - `$$item_type` – tool/armor/other
