---
title: Слухачі
description: Як створювати та використовувати слухачів у FancyMenu.
---

# Слухачі

Слухачі запускають [сценарії дій](./action-scripts), коли відбуваються певні події. Вони не прив’язані до відкритого екрана, тож можуть працювати навіть під час гри або завантаження.

Слухачі можуть передавати своїм діям і вимогам значення `$$`, наприклад натиснуту клавішу або клікнуту кнопку миші.

> [!CAUTION]
> Слухач може запускати дії з файлами, мережею, командами, буфером обміну, ресурс-паком або посиланнями без відкритого екрана. Імпортуйте слухачі лише з надійних джерел.

# Використання слухачів

Поза редактором макета відкрийте **рядок меню -> Налаштування -> Керування слухачами**, щоб створити або редагувати слухачів.

<img src="https://github.com/Keksuccino/FancyMenu/blob/master/assets/docs/manage_listeners.png?raw=true" alt="Керування слухачами" style="max-width:800px;width:100%;height:auto;">

# Змінні слухачів

Слухачі можуть надавати своїм діям і вимогам значення лише для читання. Використовуйте їхні імена `$$` у підтримуваних текстових полях.

Наприклад, використайте [**On Keyboard Key Pressed**](#on-keyboard-key-pressed-keyboard_key_pressed) разом із дією [**Print to Game Log**](./action-scripts#print-to-game-log-print_to_log). Значення `Key pressed! The key is: $$key_name` вставить назву натиснутої клавіші.

> [!WARNING]
> Змінні слухачів окремі від [збережених змінних](./variables) FancyMenu. Дії зі збереженими змінними, вимоги та заповнювачі не працюють зі значеннями `$$`.

Імена змінних слухачів чутливі до регістру та працюють лише всередині сценарію цього слухача.

Ставтеся до значень із чату, віддалених серверів, файлів і введення користувача як до ненадійних. Не вставляйте їх безпосередньо в шляхи, URL-адреси чи команди.

Змінні слухачів є рядками. Коли інформація недоступна, слухач може повертати задокументований маркер, наприклад `ERROR`, `UNKNOWN`, `NONE`, `EMPTY`, `0`, `-1` або порожній рядок. Перевіряйте ці значення перед вставленням даних слухача в шляхи, команди чи URL-адреси.

# Слухачі детально

У цьому розділі перелічено вбудовані слухачі FancyMenu.

## On Markdown Text Clicked (`text_clicked`)
- Спрацьовує, коли клацнуто [Markdown-текст із подією `click:`](./text-formatting#click-and-hover-events), наприклад `[Відкрити](click:open_menu)`.
- Змінні:
  - `$$text_event_id` – ідентифікатор події з Markdown-посилання

## On Markdown Text Hovered (`text_hovered`)
- Спрацьовує, коли на [Markdown-тексті з подією `hover:`](./text-formatting#click-and-hover-events) знаходиться курсор, наприклад `[Підказка](hover:show_hint)`.
- Змінні:
  - `$$text_event_id` – ідентифікатор події з Markdown-посилання

## On ZIP Extracted via Action (`zip_extracted_via_action`)
- Спрацьовує, коли завершується [дія **Extract ZIP File In Game Directory**](./action-scripts#extract-zip-file-in-game-directory-extract_zip_file_in_game_dir).
- Змінні:
  - `$$source_zip_path` – нормалізований шлях до джерела у форматі для користувача; шляхи ігрового каталогу можуть повертатися як `/...`, тоді як звичні шляхи каталогу Minecraft можуть використовувати `.minecraft/...`
  - `$$target_folder_path` – нормалізований шлях до цільової папки в тому ж форматі
  - `$$extract_succeeded` – true/false
  - `$$failure_reason` – текст помилки, якщо розпакування не вдалося

## On Element Spawned (`element_spawned_via_action`)
- Спрацьовує, коли підтримувана функція або доповнення FancyMenu динамічно створює екземпляр елемента.
- Змінні:
  - `$$element_type` – тип створеного елемента
  - `$$element_identifier` – ідентифікатор створеного елемента
  - `$$target_screen` – ідентифікатор цільового екрана

## On Animated Texture Started Playing (`animated_texture_started_playing`)
- Спрацьовує, коли [анімована текстура](./fma) починає відтворення.
- Змінні:
  - `$$texture_source` – джерело текстури
  - `$$texture_source_type` – тип джерела
  - `$$texture_will_restart` – true/false

## On Animated Texture Finished Playing (`animated_texture_finished_playing`)
- Спрацьовує, коли анімована текстура завершує відтворення.
- Змінні:
  - `$$texture_source`
  - `$$texture_source_type`
  - `$$texture_will_restart`

## On Video Playback Status Changed (`video_playback_status_changed`)
- Спрацьовує, коли [елемент відео або фон меню](./video) змінює стан відтворення.
- Змінні:
  - `$$video_source` – джерело відео
  - `$$video_source_type` – тип джерела
  - `$$is_looping` – true/false
  - `$$new_status` – `PLAYING`, `STOPPED`, `PAUSED` або `FINISHED`

## On System Message Received in Chat (`system_message_received_in_chat`)
- Спрацьовує, коли клієнт отримує системне повідомлення чату, наприклад відповідь на команду.
- Змінні:
  - `$$system_message_string` – текстове повідомлення без форматування
  - `$$system_message_component` – JSON-компонент

## On FM Data Received (`fm_data_received`)
- Спрацьовує, коли сервер надсилає цьому клієнту [FM Data](./fm-data) через `/fmdata send`.
- Змінні:
  - `$$data_identifier` – рядок-ідентифікатор даних
  - `$$data` – корисне навантаження даних
  - `$$sent_by` – IP сервера або `integrated_server`

## On Remote Server Connected (`remote_server_connected`)
- Спрацьовує після успішного відкриття [підключення до віддаленого сервера](./remote-server-communication).
- Змінні:
  - `$$request_id` – кешований ID запиту
  - `$$remote_server_url` – URL віддаленого сервера

## On Remote Server Data Received (`remote_server_data_received`)
- Спрацьовує, коли від підключеного віддаленого сервера надходять текстові дані.
- Змінні:
  - `$$request_id` – ID запиту
  - `$$remote_server_url` – URL віддаленого сервера
  - `$$data` – отримане корисне навантаження

## On Remote Server Connection Closed (`remote_server_connection_closed`)
- Спрацьовує, коли підключення до віддаленого сервера закривається.
- Змінні:
  - `$$request_id` – ID запиту
  - `$$remote_server_url` – URL віддаленого сервера
  - `$$intentionally_closed` – TRUE, якщо закрито дією
  - `$$crashed` – TRUE, якщо з’єднання аварійно завершилося
  - `$$unknown_close_reason` – TRUE, якщо невідома причина закриття

## On Keyboard Key Pressed (`keyboard_key_pressed`)
- Спрацьовує щоразу, коли натискається клавіша (повторюється під час утримання; працює в екранах і в грі).
- Змінні:
  - `$$key_name` – відображувана назва клавіші
  - `$$key_keycode` – код клавіші GLFW
  - `$$key_scancode` – scancode GLFW
  - `$$key_modifiers` – активна бітова маска модифікаторів

## On Keyboard Key Released (`keyboard_key_released`)
- Спрацьовує, коли клавішу відпускають (екрани та гра).
- Змінні:
  - `$$key_name`
  - `$$key_keycode`
  - `$$key_scancode`
  - `$$key_modifiers`

## On Keyboard Character Typed in Screen (`keyboard_char_typed`)
- Спрацьовує, коли під час відкритого екрана вводиться символ.
- Змінні:
  - `$$char` – введений символ

## On Mouse Moved in Screen (`mouse_moved`)
- Спрацьовує щоразу, коли мишу рухають під час відкритого екрана.
- Змінні:
  - `$$mouse_pos_x` – поточний X
  - `$$mouse_pos_y` – поточний Y
  - `$$mouse_move_delta_x` – зміна X відносно попередньої події
  - `$$mouse_move_delta_y` – зміна Y відносно попередньої події

## On Mouse Button Clicked (`mouse_button_clicked`)
- Спрацьовує, коли натискається кнопка миші (екрани та гра).
- Змінні:
  - `$$button` – ліва/права/середня
  - `$$mouse_pos_x` – поточний X
  - `$$mouse_pos_y` – поточний Y

## On Mouse Button Released (`mouse_button_released`)
- Спрацьовує, коли кнопку миші відпускають (екрани та гра).
- Змінні:
  - `$$button`
  - `$$mouse_pos_x`
  - `$$mouse_pos_y`

## On Mouse Scrolled in Screen (`mouse_scrolled`)
- Спрацьовує, коли коліщатко миші прокручують під час відкритого екрана.
- Змінні:
  - `$$scroll_delta_y` – величина вертикальної прокрутки

## On Screen Opened (`screen_open`)
- Запускається відразу після того, як будь-який екран стає активним; може використовуватися для його заміни.
- Змінні:
  - `$$screen_identifier` – ідентифікатор відкритого екрана

## On Screen Closed (`screen_close`)
- Запускається відразу після закриття екрана.
- Змінні:
  - `$$screen_identifier` – ідентифікатор закритого екрана

## On Quit Minecraft (`quit_minecraft`)
- Спрацьовує один раз, коли клієнт починає завершення роботи.
- Змінні:
  - `$$timestamp_millis` – мілісекунди від епохи на момент виходу
  - `$$timestamp_iso` – позначка часу виходу у форматі ISO-8601

## On Death (`player_death`)
- Запускається, коли для локального гравця відкривається стандартний екран смерті.
- Змінні:
  - `$$days_survived` – днів від останньої смерті
  - `$$death_reason_string` – причина у звичайному тексті
  - `$$death_reason_component` – причина як JSON-компонент
  - `$$death_pos_x` – координата X смерті
  - `$$death_pos_y` – координата Y смерті
  - `$$death_pos_z` – координата Z смерті

## On Variable Updated [FM Variable] (`fm_variable_updated`)
- Спрацьовує щоразу, коли [змінну FancyMenu](./variables) встановлюють або оновлюють.
- Змінні:
  - `$$var_name` – назва змінної
  - `$$old_value` – попереднє значення
  - `$$new_value` – нове значення

## On File Downloaded via Action (`file_downloaded_via_action`)
- Спрацьовує після завершення дії [**Download File to Game Directory**](./action-scripts#download-file-to-game-directory-download_file_to_game_dir).
- Змінні:
  - `$$download_url` – джерело завантаження
  - `$$target_file_path` – шлях до збереженого файла у разі успіху; у разі помилки тут може бути лише цільова директорія, бо остаточну назву файла не було визначено
  - `$$download_succeeded` – true/false

## On File Selected (`file_selected_via_action`)
- Спрацьовує після завершення дії [**Select File from System**](./action-scripts#select-file-from-system-select_file_to_game_dir).
- Змінні:
  - `$$selected_file_path` – абсолютний шлях до вибраного файла або порожньо, якщо скасовано
  - `$$target_file_path` – обчислений шлях усередині інстансу
  - `$$selection_succeeded` – true, якщо копіювання вдалося
  - `$$selection_cancelled` – true, якщо діалог закрито
  - `$$failure_reason` – інформація про помилку в разі збою

## On Chat Message Received (`chat_message_received`)
- Спрацьовує, коли у клієнті з’являється звичайний рядок чату гравця.
- Змінні:
  - `$$chat_message_string` – рядок без форматування
  - `$$chat_message_component` – повний JSON-компонент
  - `$$sender_uuid` – UUID відправника або ERROR
  - `$$sender_name` – ім’я відправника або ERROR

## On Chat Message Sent (`chat_message_sent`)
- Спрацьовує, коли локальний гравець надсилає повідомлення в чат.
- Змінні:
  - `$$chat_message_string` – рядок без форматування
  - `$$chat_message_component` – повний JSON-компонент

## On Effect Gained (`effect_gained`)
- Спрацьовує, коли гравець отримує ефект стану.
- Змінні:
  - `$$effect_key` – resource location ефекту
  - `$$effect_type` – позитивний/негативний/нейтральний
  - `$$effect_duration` – кількість тіків, що залишилися

## On Effect Lost (`effect_lost`)
- Спрацьовує, коли гравець втрачає ефект стану.
- Змінні:
  - `$$effect_key` – ефект, що закінчився
  - `$$effect_type` – категорія

## On Experience Changed (`experience_changed`)
- Спрацьовує щоразу, коли змінюється загальний досвід гравця.
- Змінні:
  - `$$new_experience_amount` – після зміни
  - `$$old_experience_amount` – до зміни
  - `$$is_level_up` – TRUE, якщо рівень підвищився

## On Damage Taken (`damage_taken`)
- Спрацьовує один раз за удар, коли гравець отримує шкоду.
- Змінні:
  - `$$damage_amount` – зняте здоров’я
  - `$$damage_type` – resource location типу шкоди
  - `$$is_fatal_damage` – TRUE, якщо шкода смертельна
  - `$$damage_source` – resource location нападника або NONE

## On Started Freezing (`started_freezing`)
- Спрацьовує, коли гравець починає замерзати.
- Змінні:
  - `$$freezing_intensity` – 0.0 немає, 1.0 повністю замерз

## On Stopped Freezing (`stopped_freezing`)
- Спрацьовує, коли гравець перестає замерзати.
- Змінні:
  - (немає)

## On Fully Frozen (`fully_frozen`)
- Спрацьовує один раз, коли гравець повністю замерзає.
- Змінні:
  - (немає)

## On Start Looking At Block (`start_looking_at_block`)
- Спрацьовує один раз, коли приціл уперше наводиться на блок (максимальна відстань 20 блоків).
- Змінні:
  - `$$block_key` – цільовий блок
  - `$$block_pos_x` – X блоку
  - `$$block_pos_y` – Y блоку
  - `$$block_pos_z` – Z блоку
  - `$$distance_to_player` – від очей до точки влучання

## On Stop Looking At Block (`stop_looking_at_block`)
- Спрацьовує, коли приціл перестає наводитися на блок (повертає останній цільовий блок, максимум 20 блоків).
- Змінні:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`
  - `$$distance_to_player`

## On Start Looking At Entity (`start_looking_at_entity`)
- Спрацьовує один раз, коли приціл уперше наводиться на сутність (максимум 20 блоків).
- Змінні:
  - `$$entity_key` – цільовий тип сутності
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Stop Looking At Entity (`stop_looking_at_entity`)
- Спрацьовує, коли приціл перестає наводитися на сутність (повертає останню цільову сутність, максимум 20 блоків).
- Змінні:
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Entity Spawned (`entity_spawned`)
- **Потребує FancyMenu на сервері.** Спрацьовує, коли будь-яка сутність з’являється будь-де у підключеному світі/на сервері.
- Змінні:
  - `$$entity_key`
  - `$$distance_to_player` – −1, якщо інший вимір
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`
  - `$$dimension_key`
  - `$$is_same_dimension_as_player`

## On Entity Died (`entity_died`)
- **Потребує FancyMenu на сервері.** Спрацьовує, коли будь-яка сутність помирає у підключеному світі/на сервері.
- Змінні:
  - `$$entity_key`
  - `$$distance_to_player` – −1, якщо інший вимір
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

## On Entity Starts Being In Sight (`entity_starts_being_in_sight`)
- Спрацьовує, коли сутність уперше стає видимою в межах 200 блоків.
- Змінні:
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Entity Stops Being In Sight (`entity_stops_being_in_sight`)
- Спрацьовує, коли раніше видима сутність зникає з поля зору або віддаляється далі ніж на 200 блоків.
- Змінні:
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Interacted With Entity (`entity_interacted`)
- Спрацьовує, коли гравець успішно взаємодіє із сутністю.
- Змінні:
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Entity Mounted (`entity_mounted`)
- Спрацьовує, коли гравець починає їхати на сутності.
- Змінні:
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Entity Unmounted (`entity_unmounted`)
- Спрацьовує, коли гравець перестає їхати на поточній сутності.
- Змінні:
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Block Broke (`block_broke`)
- Спрацьовує, коли гравець ламає блок.
- Змінні:
  - `$$block_key`
  - `$$broke_with_item_key` – використаний інструмент або EMPTY
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## On Block Placed (`block_placed`)
- Спрацьовує, коли гравець ставить блок.
- Змінні:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## On Interacted With Block (`interacted_with_block`)
- Спрацьовує, коли гравець успішно взаємодіє з блоком.
- Змінні:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## On Stepping On Block (`stepping_on_block`)
- Спрацьовує, коли гравець стає на блок.
- Змінні:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## On Enter Biome (`enter_biome`)
- Спрацьовує, коли гравець входить у новий біом.
- Змінні:
  - `$$biome_key` – біом, у який увійшли

## On Leave Biome (`leave_biome`)
- Спрацьовує, коли гравець залишає поточний біом.
- Змінні:
  - `$$biome_key` – біом, який щойно залишено

## On Enter Structure (`enter_structure`)
- **Потребує FancyMenu на сервері.** Грубе визначення області структури; може спрацьовувати поруч із нею, над нею або під нею.
- Змінні:
  - `$$structure_key` – структура, у яку увійшли

## On Leave Structure (`leave_structure`)
- **Потребує FancyMenu на сервері.** Грубе визначення; може спрацьовувати поблизу контуру структури.
- Змінні:
  - `$$structure_key` – структура, яку щойно залишено

## On Enter Structure (High Precision) (`enter_structure_high_precision`)
- **Потребує FancyMenu на сервері.** Спрацьовує, коли гравець входить у межі структури.
- Змінні:
  - `$$structure_key`

## On Leave Structure (High Precision) (`leave_structure_high_precision`)
- **Потребує FancyMenu на сервері.** Спрацьовує після того, як гравець виходить за межі структури.
- Змінні:
  - `$$structure_key`

## On Dimension Entered (`enter_dimension`)
- Спрацьовує, коли гравець входить у новий вимір.
- Змінні:
  - `$$dimension_key` – вимір, у який увійшли

## On Start Swimming (`start_swimming`)
- Спрацьовує, коли гравець починає плисти.
- Змінні:
  - `$$fluid_type` – resource location рідини

## On Stop Swimming (`stop_swimming`)
- Спрацьовує, коли гравець перестає плисти.
- Змінні:
  - `$$fluid_type` – рідина, в якій плавання зупинилося

## On Start Touching Fluid (`start_touching_fluid`)
- Спрацьовує, коли гравець починає торкатися рідини.
- Змінні:
  - `$$fluid_type` – рідина, якої торкаються

## On Stop Touching Fluid (`stop_touching_fluid`)
- Спрацьовує, коли гравець перестає торкатися рідини.
- Змінні:
  - `$$fluid_type` – рідина, якої більше не торкаються

## On Music Track Started (`music_track_started`)
- Спрацьовує, коли починається новий музичний трек.
- Змінні:
  - `$$track_resource_location` – аудіофайл
  - `$$track_display_name` – зрозуміла назва або UNKNOWN
  - `$$track_artist` – виконавець або UNKNOWN
  - `$$track_duration_ms` – мілісекунди (0, якщо невідомо)

## On Music Track Stopped (`music_track_stopped`)
- Спрацьовує, коли поточний музичний трек закінчується або замінюється.
- Змінні:
  - `$$track_resource_location`
  - `$$track_display_name`
  - `$$track_artist`
  - `$$track_duration_ms`

## On World Sound Triggered (`world_sound_triggered`)
- Спрацьовує, коли просторовий звук світу починає відтворюватися поруч із гравцем.
- Змінні:
  - `$$sound_resource_location` – звуковий файл
  - `$$sound_display_name` – назва субтитрів, якщо доступна
  - `$$sound_origin_pos_x`
  - `$$sound_origin_pos_y`
  - `$$sound_origin_pos_z`
  - `$$sound_origin_distance_to_player`
  - `$$sound_origin_direction_from_player` – градуси 0–360 відносно напрямку погляду

## On Weather Changed (`weather_changed`)
- Спрацьовує, коли погода змінюється глобально або локально (зміна біому чи захід у приміщення може спричинити повторне спрацювання).
- Змінні:
  - `$$weather_type` – clear/rain/thunder
  - `$$weather_can_snow` – TRUE, якщо відображається сніг
  - `$$weather_can_rain` – TRUE, якщо відображається дощ

## On Started Burning (`started_burning`)
- Спрацьовує, коли гравець починає горіти.
- Змінні:
  - (немає)

## On Stopped Burning (`stopped_burning`)
- Спрацьовує, коли гравець перестає горіти.
- Змінні:
  - (немає)

## On Started Drowning (`started_drowning`)
- Спрацьовує, коли гравець починає отримувати шкоду від утоплення.
- Змінні:
  - (немає)

## On Position Changed (`position_changed`)
- Спрацьовує щоразу, коли змінюється блокова позиція гравця.
- Змінні:
  - `$$old_pos_x` – попередній X блоку
  - `$$old_pos_y` – попередній Y блоку
  - `$$old_pos_z` – попередній Z блоку
  - `$$new_pos_x` – новий X блоку
  - `$$new_pos_y` – новий Y блоку
  - `$$new_pos_z` – новий Z блоку

## On Started Running (`started_running`)
- Спрацьовує, коли гравець починає бігти спринтом.
- Змінні:
  - (немає)

## On Stopped Running (`stopped_running`)
- Спрацьовує, коли гравець перестає бігти спринтом.
- Змінні:
  - (немає)

## On Jump (`jump`)
- Спрацьовує щоразу, коли гравець стрибає.
- Змінні:
  - (немає)

## On Server Joined (`server_joined`)
- Спрацьовує після успішного підключення до багатокористувацького сервера.
- Змінні:
  - `$$server_ip` – адреса сервера, до якого підключено

## On Server Left (`server_left`)
- Спрацьовує після відключення від багатокористувацького сервера.
- Змінні:
  - `$$server_ip` – адреса сервера, який залишено

## Singleplayer World Entered (`world_entered`)
- Спрацьовує після того, як світ для одного гравця повністю завантажується і керування повертається гравцеві.
- Змінні:
  - `$$world_name` – відображувана назва
  - `$$world_save_path` – абсолютна папка збереження
  - `$$world_difficulty` – ключ складності
  - `$$world_cheats_allowed` – TRUE, якщо чіти ввімкнено
  - `$$world_icon_path` – абсолютний шлях до значка
  - `$$world_is_first_join` – TRUE під час першого відвідування

## Singleplayer World Left (`world_left`)
- Спрацьовує після закриття світу для одного гравця та завершення збереження.
- Змінні:
  - `$$world_name`
  - `$$world_save_path`
  - `$$world_difficulty`
  - `$$world_cheats_allowed`
  - `$$world_icon_path`

## On Other Player Joined World/Server (`other_player_joined_world`)
- Спрацьовує, коли інший гравець приєднується до поточного світу/сервера.
- Змінні:
  - `$$player_name` – ім’я гравця, що приєднався
  - `$$player_uuid` – UUID

## On Other Player Left World/Server (`other_player_left_world`)
- Спрацьовує, коли інший гравець залишає поточний світ/сервер.
- Змінні:
  - `$$player_name`
  - `$$player_uuid`

## On Other Player Died (`other_player_died`)
- Спрацьовує, коли інший гравець у поточному світі помирає.
- Змінні:
  - `$$player_name`
  - `$$player_uuid`
  - `$$death_pos_x`
  - `$$death_pos_y`
  - `$$death_pos_z`

## On Item Picked Up (`item_picked_up`)
- Спрацьовує, коли гравець підбирає сутність предмета.
- Змінні:
  - `$$item_key` – resource location підібраного предмета

## On Item Dropped (`item_dropped`)
- Спрацьовує, коли гравець викидає предмет зі свого інвентаря.
- Змінні:
  - `$$item_key` – resource location викинутого предмета

## On Item Consumed (`item_consumed`)
- Спрацьовує, коли гравець завершує споживання предмета.
- Змінні:
  - `$$item_key` – спожитий предмет

## On Item Hovered in Inventory (`item_hovered_in_inventory`)
- Спрацьовує, коли користувач наводить курсор на предмет у будь-якому екрані інвентаря.
- Змінні:
  - `$$item_key` – resource location предмета під курсором
  - `$$item_display_name_string` – назва предмета у звичайному тексті
  - `$$item_display_name_json` – назва предмета як JSON-компонент

## On Item Used (`item_used`)
- Спрацьовує, коли гравець використовує предмет.
- Змінні:
  - `$$item_key` – використаний предмет
  - `$$used_on_type` – block/entity/self/none
  - `$$used_on_entity_key` – цільовий тип сутності або порожньо
  - `$$used_on_block_key` – цільовий блок або порожньо
  - `$$target_pos_x` – цільовий X або -1
  - `$$target_pos_y` – цільовий Y або -1
  - `$$target_pos_z` – цільовий Z або -1

## On Item Broke (`item_broke`)
- Спрацьовує, коли предмет в інвентарі гравця ламається.
- Змінні:
  - `$$item_key` – зламаний предмет
  - `$$item_type` – інструмент/броня/інше
