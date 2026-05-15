---
title: Слушатели
description: Как создавать и использовать слушатели в FancyMenu.
---

# Слушатели

Начиная с FancyMenu v3.8.0, появилась новая функция под названием «слушатели».

Слушатели выполняют скрипты действий, когда происходят определённые события клиента или игрового процесса.
Они могут предоставлять переменные для действий, плейсхолдеров и условий, вложенных в слушатель.

В отличие от большинства других объектов в FancyMenu, слушатели не привязаны к экрану или оверлею. Они постоянно работают в фоне, отслеживая свои события. Как только слушатель срабатывает, он выполняет свой скрипт действий, даже если в этот момент не открыт ни один экран.

# Использование слушателей

Чтобы создать новый слушатель, который отслеживает событие и выполняет скрипт действий, нажмите **menu bar -> Customization -> Manage Listeners**, находясь **НЕ** в редакторе макета. Там вы найдёте удобный интерфейс для создания и управления слушателями.

<img src="https://github.com/Keksuccino/FancyMenu/blob/master/assets/docs/manage_listeners.png?raw=true" alt="Управление слушателями" style="max-width:800px;width:100%;height:auto;">

# Переменные слушателей

Слушатели часто предоставляют особый тип переменных для вложенных действий, условий и плейсхолдеров.
К этим переменным можно обращаться как к плейсхолдерам (по сути, они ими и являются).

Используйте их, просто подставляя имена с префиксом `$$` в текстовых полях — так же, как обычный плейсхолдер.

Например, если вы используете слушатель **On Keyboard Key Pressed** и хотите вывести имя клавиши в лог через действие **Print to Log**, в качестве сообщения можно указать, например, `Key pressed! The key is: $$key_name`. Позже плейсхолдер-переменная будет заменена на фактическое имя клавиши.

> Хотя они и называются «переменными», они никак не связаны с обычной [системой переменных](/variables) FancyMenu. Вы не можете задавать эти переменные, так как они доступны только для чтения. Также нельзя использовать действия, условия и плейсхолдеры, предназначенные для системы переменных FancyMenu, с этими специальными переменными слушателей, поэтому **Get Variable Value [FM Variable]**, **Is Variable Value [FM Variable]** или **Set Variable Value [FM Variable]** для переменных слушателей работать не будут.
{.is-warning}

# Слушатели подробно

Этот список должен включать большинство, если не все, слушателей FancyMenu. Возможно, он не всегда актуален из-за обновлений мода.

## On Markdown Text Clicked
- Срабатывает, когда щёлкают по тексту Markdown с событием `click:`, например `[Open](click:open_menu)`.
- Переменные:
  - `$$text_event_id` – ID события из ссылки Markdown

## On Markdown Text Hovered
- Срабатывает, когда наводят курсор на текст Markdown с событием `hover:`, например `[Hint](hover:show_hint)`.
- Переменные:
  - `$$text_event_id` – ID события из ссылки Markdown

## On ZIP Extracted via Action
- Срабатывает, когда завершается действие **Extract ZIP File In Game Directory**.
- Переменные:
  - `$$source_zip_path` – разрешённый путь к исходному ZIP-архиву
  - `$$target_folder_path` – разрешённый путь назначения для распаковки
  - `$$extract_succeeded` – true/false
  - `$$failure_reason` – текст ошибки при неудачной распаковке

## On Element Spawned
- Срабатывает, когда элемент создаётся через действие/скриптовый поток создания элемента.
- Переменные:
  - `$$element_type` – тип созданного элемента
  - `$$element_identifier` – идентификатор созданного элемента
  - `$$target_screen` – идентификатор целевого экрана

## On Animated Texture Started Playing
- Срабатывает, когда анимированная текстура начинает воспроизводиться.
- Переменные:
  - `$$texture_source` – источник текстуры
  - `$$texture_source_type` – тип источника
  - `$$texture_will_restart` – true/false

## On Animated Texture Finished Playing
- Срабатывает, когда анимированная текстура заканчивает воспроизведение.
- Переменные:
  - `$$texture_source`
  - `$$texture_source_type`
  - `$$texture_will_restart`

## On Video Playback Status Changed
- Срабатывает, когда видеодолжность элемента или фон меню с видео меняет статус воспроизведения.
- Переменные:
  - `$$video_source` – источник видео
  - `$$video_source_type` – тип источника
  - `$$is_looping` – true/false
  - `$$new_status` – `PLAYING`, `STOPPED`, `PAUSED` или `FINISHED`

## On System Message Received in Chat
- Срабатывает, когда клиент получает системное сообщение чата, например ответ команды.
- Переменные:
  - `$$system_message_string` – обычный текст сообщения
  - `$$system_message_component` – JSON-компонент

## On FM Data Received
- Срабатывает, когда сервер отправляет FM Data этому клиенту через `/fmdata send`.
- Переменные:
  - `$$data_identifier` – строка идентификатора данных
  - `$$data` – полезная нагрузка данных
  - `$$sent_by` – IP сервера или `integrated_server`

## On Remote Server Connected
- Срабатывает, когда FancyMenu инициализирует подключение к удалённому серверу.
- Переменные:
  - `$$request_id` – кэшированный ID запроса
  - `$$remote_server_url` – URL удалённого сервера

## On Remote Server Data Received
- Срабатывает, когда от подключённого удалённого сервера получены текстовые данные.
- Переменные:
  - `$$request_id` – ID запроса
  - `$$remote_server_url` – URL удалённого сервера
  - `$$data` – полученная полезная нагрузка

## On Remote Server Connection Closed
- Срабатывает, когда соединение с удалённым сервером закрывается.
- Переменные:
  - `$$request_id` – ID запроса
  - `$$remote_server_url` – URL удалённого сервера
  - `$$intentionally_closed` – TRUE, если соединение было закрыто действием
  - `$$crashed` – TRUE, если соединение аварийно завершилось
  - `$$unknown_close_reason` – TRUE, если неизвестна причина закрытия

## On Keyboard Key Pressed
- Срабатывает при каждом нажатии клавиши (повторяется при удержании; работает в экранах и в игре).
- Переменные:
  - `$$key_name` – отображаемое имя клавиши
  - `$$key_keycode` – код клавиши GLFW
  - `$$key_scancode` – сканкод GLFW
  - `$$key_modifiers` – активная битовая маска модификаторов

## On Keyboard Key Released
- Срабатывает, когда клавиша отпускается (экраны и игра).
- Переменные:
  - `$$key_name`
  - `$$key_keycode`
  - `$$key_scancode`
  - `$$key_modifiers`

## On Keyboard Character Typed in Screen
- Срабатывает, когда вводится символ, пока открыт экран.
- Переменные:
  - `$$char` – введённый символ

## On Mouse Moved in Screen
- Срабатывает каждый раз, когда мышь перемещается, пока открыт экран.
- Переменные:
  - `$$mouse_pos_x` – текущая X
  - `$$mouse_pos_y` – текущая Y
  - `$$mouse_move_delta_x` – смещение по X с прошлого события
  - `$$mouse_move_delta_y` – смещение по Y с прошлого события

## On Mouse Button Clicked
- Срабатывает, когда нажимается кнопка мыши (экраны и игра).
- Переменные:
  - `$$button` – левая/правая/средняя
  - `$$mouse_pos_x` – текущая X
  - `$$mouse_pos_y` – текущая Y

## On Mouse Button Released
- Срабатывает, когда кнопка мыши отпускается (экраны и игра).
- Переменные:
  - `$$button`
  - `$$mouse_pos_x`
  - `$$mouse_pos_y`

## On Mouse Scrolled in Screen
- Срабатывает, когда колёсико мыши прокручивается, пока открыт экран.
- Переменные:
  - `$$scroll_delta_y` – величина вертикальной прокрутки

## On Screen Opened
- Выполняется сразу после того, как любой экран становится активным; может использоваться для его замены.
- Переменные:
  - `$$screen_identifier` – идентификатор открытого экрана

## On Screen Closed
- Выполняется сразу после закрытия экрана.
- Переменные:
  - `$$screen_identifier` – идентификатор закрытого экрана

## On Quit Minecraft
- Срабатывает один раз, когда клиент начинает завершение работы.
- Переменные:
  - `$$timestamp_millis` – эпоха в миллисекундах в момент выхода
  - `$$timestamp_iso` – временная метка в формате ISO-8601 момента выхода

## On Death
- Выполняется, когда для локального игрока открывается стандартный экран смерти.
- Переменные:
  - `$$days_survived` – дней с последней смерти
  - `$$death_reason_string` – причина в виде обычного текста
  - `$$death_reason_component` – причина как JSON-компонент
  - `$$death_pos_x` – координата X смерти
  - `$$death_pos_y` – координата Y смерти
  - `$$death_pos_z` – координата Z смерти

## On Variable Updated [FM Variable]
- Срабатывает каждый раз, когда переменная FancyMenu задаётся/обновляется.
- Переменные:
  - `$$var_name` – имя переменной
  - `$$old_value` – предыдущее значение
  - `$$new_value` – новое значение

## On File Downloaded via Action
- Срабатывает после завершения действия «Download File to Game Directory».
- Переменные:
  - `$$download_url` – источник загрузки
  - `$$target_file_path` – путь сохранённого файла
  - `$$download_succeeded` – true/false

## On File Selected
- Срабатывает после завершения действия «Select File».
- Переменные:
  - `$$selected_file_path` – абсолютный путь выбранного файла или пусто, если отменено
  - `$$target_file_path` – разрешённый путь внутри инстанса
  - `$$selection_succeeded` – true, если копирование удалось
  - `$$selection_cancelled` – true, если диалог был закрыт
  - `$$failure_reason` – сведения об ошибке при неудаче

## On Chat Message Received
- Срабатывает, когда обычное сообщение чата игрока появляется у клиента.
- Переменные:
  - `$$chat_message_string` – строка обычного текста
  - `$$chat_message_component` – полный JSON-компонент
  - `$$sender_uuid` – UUID отправителя или ERROR
  - `$$sender_name` – имя отправителя или ERROR

## On Chat Message Sent
- Срабатывает, когда локальный игрок отправляет сообщение в чат.
- Переменные:
  - `$$chat_message_string` – строка обычного текста
  - `$$chat_message_component` – полный JSON-компонент

## On Effect Gained
- Срабатывает, когда игрок получает статусный эффект.
- Переменные:
  - `$$effect_key` – ресурсный адрес эффекта
  - `$$effect_type` – положительный/отрицательный/нейтральный
  - `$$effect_duration` – оставшиеся тики

## On Effect Lost
- Срабатывает, когда игрок теряет статусный эффект.
- Переменные:
  - `$$effect_key` – истёкший эффект
  - `$$effect_type` – категория

## On Experience Changed
- Срабатывает каждый раз, когда общее количество опыта игрока изменяется.
- Переменные:
  - `$$new_experience_amount` – после изменения
  - `$$old_experience_amount` – до изменения
  - `$$is_level_up` – TRUE, если уровень повысился

## On Damage Taken
- Срабатывает один раз за удар, когда игрок получает урон.
- Переменные:
  - `$$damage_amount` – количество потерянного здоровья
  - `$$damage_type` – ресурсный адрес типа урона
  - `$$is_fatal_damage` – TRUE, если урон смертельный
  - `$$damage_source` – ресурсный адрес атакующего или NONE

## On Started Freezing
- Срабатывает, когда игрок начинает замерзать.
- Переменные:
  - `$$freezing_intensity` – 0.0 — не замерзает, 1.0 — полностью замёрз

## On Stopped Freezing
- Срабатывает, когда игрок перестаёт замерзать.
- Переменные:
  - (нет)

## On Fully Frozen
- Срабатывает один раз, когда игрок полностью замерзает.
- Переменные:
  - (нет)

## On Start Looking At Block
- Срабатывает один раз, когда прицел впервые указывает на блок (макс. 20 блоков).
- Переменные:
  - `$$block_key` – целевой блок
  - `$$block_pos_x` – X блока
  - `$$block_pos_y` – Y блока
  - `$$block_pos_z` – Z блока
  - `$$distance_to_player` – от глаз до точки попадания

## On Stop Looking At Block
- Срабатывает, когда прицел перестаёт указывать на блок (сообщает последний целевой блок, макс. 20 блоков).
- Переменные:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`
  - `$$distance_to_player`

## On Start Looking At Entity
- Срабатывает один раз, когда прицел впервые указывает на сущность (макс. 20 блоков).
- Переменные:
  - `$$entity_key` – тип целевой сущности
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Stop Looking At Entity
- Срабатывает, когда прицел перестаёт указывать на сущность (сообщает последнюю целевую сущность, макс. 20 блоков).
- Переменные:
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Entity Spawned
- **Требуется FancyMenu на сервере.** Срабатывает, когда любая сущность появляется где-либо в подключённом мире/на сервере.
- Переменные:
  - `$$entity_key`
  - `$$distance_to_player` – −1, если в другой измерении
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`
  - `$$dimension_key`
  - `$$is_same_dimension_as_player`

## On Entity Died
- **Требуется FancyMenu на сервере.** Срабатывает, когда любая сущность умирает в подключённом мире/на сервере.
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

## On Entity Starts Being In Sight
- Срабатывает, когда сущность впервые становится видимой в пределах 200 блоков.
- Переменные:
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Entity Stops Being In Sight
- Срабатывает, когда ранее видимая сущность исчезает из поля зрения или удаляется дальше чем на 200 блоков.
- Переменные:
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Interacted With Entity
- Срабатывает, когда игрок успешно взаимодействует с сущностью.
- Переменные:
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Entity Mounted
- Срабатывает, когда игрок начинает ездить на сущности.
- Переменные:
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Entity Unmounted
- Срабатывает, когда игрок перестаёт ездить на текущей сущности.
- Переменные:
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Block Broke
- Срабатывает, когда игрок ломает блок.
- Переменные:
  - `$$block_key`
  - `$$broke_with_item_key` – использованный инструмент или EMPTY
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## On Block Placed
- Срабатывает, когда игрок ставит блок.
- Переменные:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## On Interacted With Block
- Срабатывает, когда игрок успешно взаимодействует с блоком.
- Переменные:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## On Stepping On Block
- Срабатывает, когда игрок наступает на блок.
- Переменные:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## On Enter Biome
- Срабатывает, когда игрок входит в новый биом.
- Переменные:
  - `$$biome_key` – вошедший биом

## On Leave Biome
- Срабатывает, когда игрок покидает текущий биом.
- Переменные:
  - `$$biome_key` – только что покинутый биом

## On Enter Structure
- **Требуется FancyMenu на сервере.** Грубое определение области структуры; может сработать рядом, над или под структурой.
- Переменные:
  - `$$structure_key` – вошедшая структура

## On Leave Structure
- **Требуется FancyMenu на сервере.** Грубое определение; может сработать рядом с границами структуры.
- Переменные:
  - `$$structure_key` – только что покинутая структура

## On Enter Structure (High Precision)
- **Требуется FancyMenu на сервере.** Срабатывает, когда игрок входит в ограничивающие объёмы структуры.
- Переменные:
  - `$$structure_key`

## On Leave Structure (High Precision)
- **Требуется FancyMenu на сервере.** Срабатывает после выхода игрока из ограничивающих объёмов структуры.
- Переменные:
  - `$$structure_key`

## On Dimension Entered
- Срабатывает, когда игрок входит в новое измерение.
- Переменные:
  - `$$dimension_key` – вошедшее измерение

## On Start Swimming
- Срабатывает, когда игрок начинает плыть.
- Переменные:
  - `$$fluid_type` – ресурсный адрес жидкости

## On Stop Swimming
- Срабатывает, когда игрок перестаёт плыть.
- Переменные:
  - `$$fluid_type` – жидкость, в которой плавание прекратилось

## On Start Touching Fluid
- Срабатывает, когда игрок начинает касаться жидкости.
- Переменные:
  - `$$fluid_type` – затронутая жидкость

## On Stop Touching Fluid
- Срабатывает, когда игрок перестаёт касаться жидкости.
- Переменные:
  - `$$fluid_type` – жидкость, которой больше не касается

## On Music Track Started
- Срабатывает, когда начинается новый музыкальный трек.
- Переменные:
  - `$$track_resource_location` – аудиофайл
  - `$$track_display_name` – читаемое имя или UNKNOWN
  - `$$track_artist` – исполнитель или UNKNOWN
  - `$$track_duration_ms` – миллисекунды (0, если неизвестно)

## On Music Track Stopped
- Срабатывает, когда текущий музыкальный трек заканчивается или заменяется.
- Переменные:
  - `$$track_resource_location`
  - `$$track_display_name`
  - `$$track_artist`
  - `$$track_duration_ms`

## On World Sound Triggered
- Срабатывает, когда пространственный звук мира начинается рядом с игроком.
- Переменные:
  - `$$sound_resource_location` – звуковой файл
  - `$$sound_display_name` – название субтитра, если доступно
  - `$$sound_origin_pos_x`
  - `$$sound_origin_pos_y`
  - `$$sound_origin_pos_z`
  - `$$sound_origin_distance_to_player`
  - `$$sound_origin_direction_from_player` – градусы 0–360 относительно направления взгляда

## On Weather Changed
- Срабатывает при изменении погоды глобально или локально (смена биома или вход в помещение могут вызвать повторное срабатывание).
- Переменные:
  - `$$weather_type` – clear/rain/thunder
  - `$$weather_can_snow` – TRUE, если отображается снег
  - `$$weather_can_rain` – TRUE, если отображается дождь

## On Started Burning
- Срабатывает, когда игрок начинает гореть.
- Переменные:
  - (нет)

## On Stopped Burning
- Срабатывает, когда игрок перестаёт гореть.
- Переменные:
  - (нет)

## On Started Drowning
- Срабатывает, когда игрок начинает получать урон от утопления.
- Переменные:
  - (нет)

## On Position Changed
- Срабатывает каждый раз, когда изменяется блоковая позиция игрока.
- Переменные:
  - `$$old_pos_x` – предыдущий X блока
  - `$$old_pos_y` – предыдущий Y блока
  - `$$old_pos_z` – предыдущий Z блока
  - `$$new_pos_x` – новый X блока
  - `$$new_pos_y` – новый Y блока
  - `$$new_pos_z` – новый Z блока

## On Started Running
- Срабатывает, когда игрок начинает спринт.
- Переменные:
  - (нет)

## On Stopped Running
- Срабатывает, когда игрок перестаёт спринтить.
- Переменные:
  - (нет)

## On Jump
- Срабатывает каждый раз, когда игрок прыгает.
- Переменные:
  - (нет)

## On Server Joined
- Срабатывает после успешного подключения к многопользовательскому серверу.
- Переменные:
  - `$$server_ip` – адрес подключённого сервера

## On Server Left
- Срабатывает после отключения от многопользовательского сервера.
- Переменные:
  - `$$server_ip` – адрес покинутого сервера

## Singleplayer World Entered
- Срабатывает после полной загрузки одиночного мира и возврата управления.
- Переменные:
  - `$$world_name` – отображаемое имя
  - `$$world_save_path` – абсолютная папка сохранения
  - `$$world_difficulty` – ключ сложности
  - `$$world_cheats_allowed` – TRUE, если читы включены
  - `$$world_icon_path` – абсолютный путь к иконке
  - `$$world_is_first_join` – TRUE при самом первом посещении

## Singleplayer World Left
- Срабатывает после закрытия и завершения сохранения одиночного мира.
- Переменные:
  - `$$world_name`
  - `$$world_save_path`
  - `$$world_difficulty`
  - `$$world_cheats_allowed`
  - `$$world_icon_path`

## On Other Player Joined World/Server
- Срабатывает, когда другой игрок присоединяется к текущему миру/серверу.
- Переменные:
  - `$$player_name` – имя вошедшего игрока
  - `$$player_uuid` – UUID

## On Other Player Left World/Server
- Срабатывает, когда другой игрок покидает текущий мир/сервер.
- Переменные:
  - `$$player_name`
  - `$$player_uuid`

## On Other Player Died
- Срабатывает, когда другой игрок в текущем мире умирает.
- Переменные:
  - `$$player_name`
  - `$$player_uuid`
  - `$$death_pos_x`
  - `$$death_pos_y`
  - `$$death_pos_z`

## On Item Picked Up
- Срабатывает, когда игрок подбирает сущность предмета.
- Переменные:
  - `$$item_key` – ресурсный адрес подобранного предмета

## On Item Dropped
- Срабатывает, когда игрок выбрасывает предмет из инвентаря.
- Переменные:
  - `$$item_key` – ресурсный адрес выброшенного предмета

## On Item Consumed
- Срабатывает, когда игрок завершает потребление предмета.
- Переменные:
  - `$$item_key` – потреблённый предмет

## On Item Hovered in Inventory
- Срабатывает, когда пользователь наводит курсор на предмет в любом экране инвентаря.
- Переменные:
  - `$$item_key` – ресурсный адрес предмета под курсором
  - `$$item_display_name_string` – отображаемое имя предмета в виде обычного текста
  - `$$item_display_name_json` – отображаемое имя предмета как JSON-компонент

## On Item Used
- Срабатывает, когда игрок использует предмет.
- Переменные:
  - `$$item_key` – использованный предмет
  - `$$used_on_type` – block/entity/self/none
  - `$$used_on_entity_key` – тип целевой сущности или empty
  - `$$used_on_block_key` – целевой блок или empty
  - `$$target_pos_x` – целевая X или -1
  - `$$target_pos_y` – целевая Y или -1
  - `$$target_pos_z` – целевая Z или -1

## On Item Broke
- Срабатывает, когда предмет в инвентаре игрока ломается.
- Переменные:
  - `$$item_key` – сломанный предмет
  - `$$item_type` – tool/armor/other
