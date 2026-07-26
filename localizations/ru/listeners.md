---
title: Слушатели
description: Как создавать и использовать слушатели в FancyMenu.
---
# Слушатели

Слушатели запускают [скрипты действий](./action-scripts), когда происходят определённые события. Они не привязаны к открытому экрану, поэтому могут запускаться и во время игры или загрузки.

Слушатели могут передавать своим действиям и условиям значения `$$`, например нажатую клавишу или щёлкнутую кнопку мыши.

> [!CAUTION]
> Слушатель может запускать действия с файлами, сетью, командами, буфером обмена, ресурс-паком или ссылками без открытого экрана. Импортируйте слушатели только из доверенных источников.

# Использование слушателей

Вне редактора макетов откройте **menu bar -> Customization -> Manage Listeners**, чтобы создать или изменить слушатели.

<img src="https://github.com/Keksuccino/FancyMenu/blob/master/assets/docs/manage_listeners.png?raw=true" alt="Manage listeners" style="max-width:800px;width:100%;height:auto;">

# Переменные слушателей

Слушатели могут передавать своим действиям и условиям значения только для чтения. Используйте их имена `$$` в поддерживаемых текстовых полях.

Например, используйте [**On Keyboard Key Pressed**](#on-keyboard-key-pressed-keyboard_key_pressed) вместе с действием [**Print to Game Log**](./action-scripts#print-to-game-log-print_to_log). Значение `Key pressed! The key is: $$key_name` подставит имя нажатой клавиши.

> [!WARNING]
> Переменные слушателей не связаны со [сохранёнными переменными](./variables) FancyMenu. Действия, условия и подстановки сохранённых переменных не работают со значениями `$$`.

Имена переменных слушателей чувствительны к регистру и работают только внутри скрипта этого слушателя.

Считайте значения из чата, удалённых серверов, файлов и пользовательского ввода недоверенными. Не вставляйте их напрямую в пути, URL или команды.

Переменные слушателей — это строки. Если информация недоступна, слушатель может вернуть документированное сигнальное значение, такое как `ERROR`, `UNKNOWN`, `NONE`, `EMPTY`, `0`, `-1` или пустую строку. Проверяйте эти значения перед вставкой данных слушателя в пути, команды или URL.

# Слушатели подробно

В этом разделе перечислены встроенные слушатели FancyMenu.

## On Markdown Text Clicked (`text_clicked`)
- Срабатывает при щелчке по [тексту Markdown с событием `click:`](./text-formatting#click-and-hover-events), например `[Open](click:open_menu)`.
- Переменные:
  - `$$text_event_id` – ID события из ссылки Markdown

## On Markdown Text Hovered (`text_hovered`)
- Срабатывает при наведении на [текст Markdown с событием `hover:`](./text-formatting#click-and-hover-events), например `[Hint](hover:show_hint)`.
- Переменные:
  - `$$text_event_id` – ID события из ссылки Markdown

## On ZIP Extracted via Action (`zip_extracted_via_action`)
- Срабатывает после завершения действия [**Extract ZIP File In Game Directory**](./action-scripts#extract-zip-file-in-game-directory-extract_zip_file_in_game_dir).
- Переменные:
  - `$$source_zip_path` – нормализованный пользовательский путь к исходному архиву; пути в каталоге игры могут возвращаться как `/...`, а обычные пути каталога Minecraft — как `.minecraft/...`
  - `$$target_folder_path` – нормализованный пользовательский путь к целевой папке с теми же форматами путей
  - `$$extract_succeeded` – true/false
  - `$$failure_reason` – текст ошибки при неудачном извлечении

## On Element Spawned (`element_spawned_via_action`)
- Срабатывает, когда поддерживаемая функция FancyMenu или дополнение динамически создаёт экземпляр элемента.
- Переменные:
  - `$$element_type` – тип созданного элемента
  - `$$element_identifier` – идентификатор созданного элемента
  - `$$target_screen` – идентификатор целевого экрана

## On Animated Texture Started Playing (`animated_texture_started_playing`)
- Срабатывает, когда [анимированная текстура](./fma) начинает воспроизведение.
- Переменные:
  - `$$texture_source` – источник текстуры
  - `$$texture_source_type` – тип источника
  - `$$texture_will_restart` – true/false

## On Animated Texture Finished Playing (`animated_texture_finished_playing`)
- Срабатывает, когда анимированная текстура заканчивает воспроизведение.
- Переменные:
  - `$$texture_source`
  - `$$texture_source_type`
  - `$$texture_will_restart`

## On Video Playback Status Changed (`video_playback_status_changed`)
- Срабатывает, когда [элемент видео или фон меню](./video) меняет статус воспроизведения.
- Переменные:
  - `$$video_source` – источник видео
  - `$$video_source_type` – тип источника
  - `$$is_looping` – true/false
  - `$$new_status` – `PLAYING`, `STOPPED`, `PAUSED` или `FINISHED`

## On System Message Received in Chat (`system_message_received_in_chat`)
- Срабатывает, когда клиент получает системное сообщение чата, например ответ на команду.
- Переменные:
  - `$$system_message_string` – сообщение в виде простого текста
  - `$$system_message_component` – JSON-компонент

## On FM Data Received (`fm_data_received`)
- Срабатывает, когда сервер отправляет этому клиенту [FM Data](./fm-data) через `/fmdata send`.
- Переменные:
  - `$$data_identifier` – строка идентификатора данных
  - `$$data` – полезная нагрузка данных
  - `$$sent_by` – IP сервера или `integrated_server`

## On Remote Server Connected (`remote_server_connected`)
- Срабатывает после успешного открытия [подключения к удалённому серверу](./remote-server-communication).
- Переменные:
  - `$$request_id` – кэшированный ID запроса
  - `$$remote_server_url` – URL удалённого сервера

## On Remote Server Data Received (`remote_server_data_received`)
- Срабатывает, когда от подключённого удалённого сервера получены текстовые данные.
- Переменные:
  - `$$request_id` – ID запроса
  - `$$remote_server_url` – URL удалённого сервера
  - `$$data` – полученная полезная нагрузка

## On Remote Server Connection Closed (`remote_server_connection_closed`)
- Срабатывает, когда соединение с удалённым сервером закрывается.
- Переменные:
  - `$$request_id` – ID запроса
  - `$$remote_server_url` – URL удалённого сервера
  - `$$intentionally_closed` – TRUE, если закрыто действием
  - `$$crashed` – TRUE, если соединение аварийно завершилось
  - `$$unknown_close_reason` – TRUE, если известная причина закрытия отсутствовала

## On Keyboard Key Pressed (`keyboard_key_pressed`)
- Срабатывает каждый раз при нажатии клавиши (повторяется, пока клавиша удерживается; работает в экранах и в игре).
- Переменные:
  - `$$key_name` – отображаемое имя клавиши
  - `$$key_keycode` – код клавиши GLFW
  - `$$key_scancode` – сканкод GLFW
  - `$$key_modifiers` – активная битовая маска модификаторов

## On Keyboard Key Released (`keyboard_key_released`)
- Срабатывает при отпускании клавиши (в экранах и в игре).
- Переменные:
  - `$$key_name`
  - `$$key_keycode`
  - `$$key_scancode`
  - `$$key_modifiers`

## On Keyboard Character Typed in Screen (`keyboard_char_typed`)
- Срабатывает, когда вводится символ при открытом экране.
- Переменные:
  - `$$char` – введённый символ

## On Mouse Moved in Screen (`mouse_moved`)
- Срабатывает при каждом движении мыши, пока открыт экран.
- Переменные:
  - `$$mouse_pos_x` – текущая X
  - `$$mouse_pos_y` – текущая Y
  - `$$mouse_move_delta_x` – изменение X с прошлого события
  - `$$mouse_move_delta_y` – изменение Y с прошлого события

## On Mouse Button Clicked (`mouse_button_clicked`)
- Срабатывает при нажатии кнопки мыши (в экранах и в игре).
- Переменные:
  - `$$button` – left/right/middle
  - `$$mouse_pos_x` – текущая X
  - `$$mouse_pos_y` – текущая Y

## On Mouse Button Released (`mouse_button_released`)
- Срабатывает при отпускании кнопки мыши (в экранах и в игре).
- Переменные:
  - `$$button`
  - `$$mouse_pos_x`
  - `$$mouse_pos_y`

## On Mouse Scrolled in Screen (`mouse_scrolled`)
- Срабатывает при прокрутке колеса мыши, пока открыт экран.
- Переменные:
  - `$$scroll_delta_y` – величина вертикальной прокрутки

## On Screen Opened (`screen_open`)
- Запускается сразу после того, как любой экран становится активным; можно использовать для его переопределения.
- Переменные:
  - `$$screen_identifier` – идентификатор открытого экрана

## On Screen Closed (`screen_close`)
- Запускается сразу после закрытия экрана.
- Переменные:
  - `$$screen_identifier` – идентификатор закрытого экрана

## On Quit Minecraft (`quit_minecraft`)
- Срабатывает один раз, когда клиент начинает завершение работы.
- Переменные:
  - `$$timestamp_millis` – миллисекунды эпохи в момент выхода
  - `$$timestamp_iso` – временная метка ISO-8601 момента выхода

## On Death (`player_death`)
- Запускается, когда для локального игрока открывается стандартный экран смерти.
- Переменные:
  - `$$days_survived` – число дней с последней смерти
  - `$$death_reason_string` – причина в виде простого текста
  - `$$death_reason_component` – JSON-компонент причины
  - `$$death_pos_x` – координата X смерти
  - `$$death_pos_y` – координата Y смерти
  - `$$death_pos_z` – координата Z смерти

## On Variable Updated [FM Variable] (`fm_variable_updated`)
- Срабатывает каждый раз, когда [переменная FancyMenu](./variables) задаётся или обновляется.
- Переменные:
  - `$$var_name` – имя переменной
  - `$$old_value` – предыдущее значение
  - `$$new_value` – новое значение

## On File Downloaded via Action (`file_downloaded_via_action`)
- Срабатывает после завершения действия [**Download File to Game Directory**](./action-scripts#download-file-to-game-directory-download_file_to_game_dir).
- Переменные:
  - `$$download_url` – источник загрузки
  - `$$target_file_path` – путь к сохранённому файлу при успехе; при ошибке может содержать только целевую папку, если итоговое имя файла не было определено
  - `$$download_succeeded` – true/false

## On File Selected (`file_selected_via_action`)
- Срабатывает после завершения действия [**Select File from System**](./action-scripts#select-file-from-system-select_file_to_game_dir).
- Переменные:
  - `$$selected_file_path` – абсолютный путь к выбранному файлу или пусто, если действие отменено
  - `$$target_file_path` – разрешённый путь внутри экземпляра
  - `$$selection_succeeded` – true, если копирование удалось
  - `$$selection_cancelled` – true, если диалог был закрыт
  - `$$failure_reason` – информация об ошибке при сбое

## On Chat Message Received (`chat_message_received`)
- Срабатывает, когда на клиенте появляется обычная строка чата игрока.
- Переменные:
  - `$$chat_message_string` – строка простого текста
  - `$$chat_message_component` – полный JSON-компонент
  - `$$sender_uuid` – UUID отправителя или ERROR
  - `$$sender_name` – имя отправителя или ERROR

## On Chat Message Sent (`chat_message_sent`)
- Срабатывает, когда локальный игрок отправляет сообщение в чат.
- Переменные:
  - `$$chat_message_string` – строка простого текста
  - `$$chat_message_component` – полный JSON-компонент

## On Effect Gained (`effect_gained`)
- Срабатывает, когда игрок получает эффект состояния.
- Переменные:
  - `$$effect_key` – ресурсное расположение эффекта
  - `$$effect_type` – positive/negative/neutral
  - `$$effect_duration` – оставшиеся тики

## On Effect Lost (`effect_lost`)
- Срабатывает, когда игрок теряет эффект состояния.
- Переменные:
  - `$$effect_key` – истёкший эффект
  - `$$effect_type` – категория

## On Experience Changed (`experience_changed`)
- Срабатывает всякий раз, когда изменяется общий опыт игрока.
- Переменные:
  - `$$new_experience_amount` – после изменения
  - `$$old_experience_amount` – до изменения
  - `$$is_level_up` – TRUE, если уровень повысился

## On Damage Taken (`damage_taken`)
- Срабатывает один раз за удар, когда игрок получает урон.
- Переменные:
  - `$$damage_amount` – снятое здоровье
  - `$$damage_type` – ресурсное расположение типа урона
  - `$$is_fatal_damage` – TRUE, если урон смертельный
  - `$$damage_source` – ресурсное расположение атакующего или NONE

## On Started Freezing (`started_freezing`)
- Срабатывает, когда игрок начинает замерзать.
- Переменные:
  - `$$freezing_intensity` – 0.0 нет замерзания, 1.0 полностью замёрз

## On Stopped Freezing (`stopped_freezing`)
- Срабатывает, когда игрок перестаёт замерзать.
- Переменные:
  - (нет)

## On Fully Frozen (`fully_frozen`)
- Срабатывает один раз, когда игрок полностью замерзает.
- Переменные:
  - (нет)

## On Start Looking At Block (`start_looking_at_block`)
- Срабатывает один раз, когда прицел впервые указывает на блок (максимум 20 блоков по расстоянию).
- Переменные:
  - `$$block_key` – целевой блок
  - `$$block_pos_x` – X блока
  - `$$block_pos_y` – Y блока
  - `$$block_pos_z` – Z блока
  - `$$distance_to_player` – от глаз до точки попадания

## On Stop Looking At Block (`stop_looking_at_block`)
- Срабатывает, когда прицел перестаёт указывать на блок (сообщает последний целевой блок, максимум 20 блоков).
- Переменные:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`
  - `$$distance_to_player`

## On Start Looking At Entity (`start_looking_at_entity`)
- Срабатывает один раз, когда прицел впервые указывает на сущность (максимум 20 блоков).
- Переменные:
  - `$$entity_key` – целевой тип сущности
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Stop Looking At Entity (`stop_looking_at_entity`)
- Срабатывает, когда прицел перестаёт указывать на сущность (сообщает последнюю целевую сущность, максимум 20 блоков).
- Переменные:
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Entity Spawned (`entity_spawned`)
- **Требует FancyMenu на сервере.** Срабатывает, когда любая сущность появляется где-либо в подключённом мире/на сервере.
- Переменные:
  - `$$entity_key`
  - `$$distance_to_player` – −1, если в другой измерении
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`
  - `$$dimension_key`
  - `$$is_same_dimension_as_player`

## On Entity Died (`entity_died`)
- **Требует FancyMenu на сервере.** Срабатывает, когда любая сущность умирает в подключённом мире/на сервере.
- Переменные:
  - `$$entity_key`
  - `$$distance_to_player` – −1, если в другой измерении
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
- Срабатывает, когда сущность впервые становится видимой в пределах 200 блоков.
- Переменные:
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Entity Stops Being In Sight (`entity_stops_being_in_sight`)
- Срабатывает, когда ранее видимая сущность исчезает из поля зрения или удаляется дальше чем на 200 блоков.
- Переменные:
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Interacted With Entity (`entity_interacted`)
- Срабатывает, когда игрок успешно взаимодействует с сущностью.
- Переменные:
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Entity Mounted (`entity_mounted`)
- Срабатывает, когда игрок начинает ездить верхом на сущности.
- Переменные:
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Entity Unmounted (`entity_unmounted`)
- Срабатывает, когда игрок перестаёт ездить верхом на текущей сущности.
- Переменные:
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Block Broke (`block_broke`)
- Срабатывает, когда игрок ломает блок.
- Переменные:
  - `$$block_key`
  - `$$broke_with_item_key` – использованный инструмент или EMPTY
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## On Block Placed (`block_placed`)
- Срабатывает, когда игрок ставит блок.
- Переменные:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## On Interacted With Block (`interacted_with_block`)
- Срабатывает, когда игрок успешно взаимодействует с блоком.
- Переменные:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## On Stepping On Block (`stepping_on_block`)
- Срабатывает, когда игрок наступает на блок.
- Переменные:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## On Enter Biome (`enter_biome`)
- Срабатывает, когда игрок входит в новый биом.
- Переменные:
  - `$$biome_key` – вошедший биом

## On Leave Biome (`leave_biome`)
- Срабатывает, когда игрок покидает текущий биом.
- Переменные:
  - `$$biome_key` – только что покинутый биом

## On Enter Structure (`enter_structure`)
- **Требует FancyMenu на сервере.** Грубое определение области структуры; может сработать рядом с ней, над ней или под ней.
- Переменные:
  - `$$structure_key` – вошедшая структура

## On Leave Structure (`leave_structure`)
- **Требует FancyMenu на сервере.** Грубое определение; может сработать рядом с границами структуры.
- Переменные:
  - `$$structure_key` – только что покинутая структура

## On Enter Structure (High Precision) (`enter_structure_high_precision`)
- **Требует FancyMenu на сервере.** Срабатывает, когда игрок входит в bounding boxes структуры.
- Переменные:
  - `$$structure_key`

## On Leave Structure (High Precision) (`leave_structure_high_precision`)
- **Требует FancyMenu на сервере.** Срабатывает после выхода игрока из bounding boxes структуры.
- Переменные:
  - `$$structure_key`

## On Dimension Entered (`enter_dimension`)
- Срабатывает, когда игрок входит в новое измерение.
- Переменные:
  - `$$dimension_key` – вошедшее измерение

## On Start Swimming (`start_swimming`)
- Срабатывает, когда игрок начинает плыть.
- Переменные:
  - `$$fluid_type` – ресурсное расположение жидкости

## On Stop Swimming (`stop_swimming`)
- Срабатывает, когда игрок перестаёт плыть.
- Переменные:
  - `$$fluid_type` – жидкость, в которой плавание прекратилось

## On Start Touching Fluid (`start_touching_fluid`)
- Срабатывает, когда игрок начинает касаться жидкости.
- Переменные:
  - `$$fluid_type` – касающаяся жидкость

## On Stop Touching Fluid (`stop_touching_fluid`)
- Срабатывает, когда игрок перестаёт касаться жидкости.
- Переменные:
  - `$$fluid_type` – жидкость, которой больше не касается

## On Music Track Started (`music_track_started`)
- Срабатывает, когда начинается новый музыкальный трек.
- Переменные:
  - `$$track_resource_location` – аудиофайл
  - `$$track_display_name` – понятное человеку имя или UNKNOWN
  - `$$track_artist` – исполнитель или UNKNOWN
  - `$$track_duration_ms` – миллисекунды (0, если неизвестно)

## On Music Track Stopped (`music_track_stopped`)
- Срабатывает, когда текущий музыкальный трек заканчивается или заменяется.
- Переменные:
  - `$$track_resource_location`
  - `$$track_display_name`
  - `$$track_artist`
  - `$$track_duration_ms`

## On World Sound Triggered (`world_sound_triggered`)
- Срабатывает, когда рядом с игроком начинается позиционный звуковой эффект мира.
- Переменные:
  - `$$sound_resource_location` – звуковой файл
  - `$$sound_display_name` – имя субтитров, если доступно
  - `$$sound_origin_pos_x`
  - `$$sound_origin_pos_y`
  - `$$sound_origin_pos_z`
  - `$$sound_origin_distance_to_player`
  - `$$sound_origin_direction_from_player` – градусы 0–360 относительно направления взгляда

## On Weather Changed (`weather_changed`)
- Срабатывает при изменении погоды глобально или локально (смена биома или вход в помещение может вызвать повторный запуск).
- Переменные:
  - `$$weather_type` – clear/rain/thunder
  - `$$weather_can_snow` – TRUE, если отображается снег
  - `$$weather_can_rain` – TRUE, если отображается дождь

## On Started Burning (`started_burning`)
- Срабатывает, когда игрок начинает гореть.
- Переменные:
  - (нет)

## On Stopped Burning (`stopped_burning`)
- Срабатывает, когда игрок перестаёт гореть.
- Переменные:
  - (нет)

## On Started Drowning (`started_drowning`)
- Срабатывает, когда игрок начинает получать урон от утопления.
- Переменные:
  - (нет)

## On Position Changed (`position_changed`)
- Срабатывает всякий раз, когда меняется блоковая позиция игрока.
- Переменные:
  - `$$old_pos_x` – предыдущий X блока
  - `$$old_pos_y` – предыдущий Y блока
  - `$$old_pos_z` – предыдущий Z блока
  - `$$new_pos_x` – новый X блока
  - `$$new_pos_y` – новый Y блока
  - `$$new_pos_z` – новый Z блока

## On Started Running (`started_running`)
- Срабатывает, когда игрок начинает спринт.
- Переменные:
  - (нет)

## On Stopped Running (`stopped_running`)
- Срабатывает, когда игрок перестаёт спринтовать.
- Переменные:
  - (нет)

## On Jump (`jump`)
- Срабатывает каждый раз, когда игрок прыгает.
- Переменные:
  - (нет)

## On Server Joined (`server_joined`)
- Срабатывает после успешного подключения к многопользовательскому серверу.
- Переменные:
  - `$$server_ip` – адрес подключённого сервера

## On Server Left (`server_left`)
- Срабатывает после отключения от многопользовательского сервера.
- Переменные:
  - `$$server_ip` – адрес покинутого сервера

## Singleplayer World Entered (`world_entered`)
- Срабатывает после полной загрузки одиночного мира и возврата управления игроку.
- Переменные:
  - `$$world_name` – отображаемое имя
  - `$$world_save_path` – абсолютная папка сохранения
  - `$$world_difficulty` – ключ сложности
  - `$$world_cheats_allowed` – TRUE, если читы включены
  - `$$world_icon_path` – абсолютный путь к значку
  - `$$world_is_first_join` – TRUE при самом первом посещении

## Singleplayer World Left (`world_left`)
- Срабатывает после закрытия одиночного мира и завершения сохранения.
- Переменные:
  - `$$world_name`
  - `$$world_save_path`
  - `$$world_difficulty`
  - `$$world_cheats_allowed`
  - `$$world_icon_path`

## On Other Player Joined World/Server (`other_player_joined_world`)
- Срабатывает, когда другой игрок присоединяется к текущему миру/серверу.
- Переменные:
  - `$$player_name` – имя вошедшего игрока
  - `$$player_uuid` – UUID

## On Other Player Left World/Server (`other_player_left_world`)
- Срабатывает, когда другой игрок покидает текущий мир/сервер.
- Переменные:
  - `$$player_name`
  - `$$player_uuid`

## On Other Player Died (`other_player_died`)
- Срабатывает, когда другой игрок в текущем мире умирает.
- Переменные:
  - `$$player_name`
  - `$$player_uuid`
  - `$$death_pos_x`
  - `$$death_pos_y`
  - `$$death_pos_z`

## On Item Picked Up (`item_picked_up`)
- Срабатывает, когда игрок подбирает сущность предмета.
- Переменные:
  - `$$item_key` – ресурсное расположение подобранного предмета

## On Item Dropped (`item_dropped`)
- Срабатывает, когда игрок выбрасывает предмет из инвентаря.
- Переменные:
  - `$$item_key` – ресурсное расположение выброшенного предмета

## On Item Consumed (`item_consumed`)
- Срабатывает, когда игрок завершает использование предмета с потреблением.
- Переменные:
  - `$$item_key` – consumed item

## On Item Hovered in Inventory (`item_hovered_in_inventory`)
- Срабатывает, когда пользователь наводит курсор на предмет в любом экране инвентаря.
- Переменные:
  - `$$item_key` – ресурсное расположение наведённого предмета
  - `$$item_display_name_string` – отображаемое имя предмета в виде простого текста
  - `$$item_display_name_json` – отображаемое имя предмета в виде JSON-компонента

## On Item Used (`item_used`)
- Срабатывает, когда игрок использует предмет.
- Переменные:
  - `$$item_key` – использованный предмет
  - `$$used_on_type` – block/entity/self/none
  - `$$used_on_entity_key` – тип целевой сущности или пусто
  - `$$used_on_block_key` – целевой блок или пусто
  - `$$target_pos_x` – целевая X или -1
  - `$$target_pos_y` – целевая Y или -1
  - `$$target_pos_z` – целевая Z или -1

## On Item Broke (`item_broke`)
- Срабатывает, когда предмет в инвентаре игрока ломается.
- Переменные:
  - `$$item_key` – сломавшийся предмет
  - `$$item_type` – tool/armor/other
