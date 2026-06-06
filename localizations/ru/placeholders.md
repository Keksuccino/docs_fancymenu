---
title: Заполнители
description: Как использовать заполнители.
---
# Заполнители

Заполнители — это динамические значения, которые заменяются на фактическое содержимое при использовании. В FancyMenu заполнители позволяют вставлять динамические данные в различные элементы, такие как текст, кнопки и условия загрузки. Представьте их как переменные, которые вычисляются и подставляются своими значениями, когда отображаются ваши макеты.

# Общая информация

## Базовый синтаксис
Заполнители в FancyMenu используют синтаксис, похожий на JSON:
```
{"placeholder":"modversion","values":{"modid":"fancymenu"}}
```

Например, чтобы отобразить имя игрока:
```
{"placeholder":"playername"}
```

## Вложенные заполнители
Одна из самых мощных возможностей системы заполнителей FancyMenu — это возможность вкладывать одни заполнители в другие. Это означает, что вы можете использовать результат одного заполнителя как входные данные для другого.

Пример вложенных заполнителей:
```
{"placeholder":"calc","values":{"decimal":"true","expression":"{"placeholder":"maxram"} / 1024"}}
```
В этом примере берётся максимальный объём ОЗУ и делится на 1024, чтобы преобразовать его из МБ в ГБ.

> [!IMPORTANT]
> В отличие от настоящего JSON, вложенные заполнители **не** экранируются с помощью `\`. Это очень важно, потому что при экранировании заполнители перестанут работать (что, впрочем, очевидно). Заполнители используют лишь синтаксис, похожий на JSON. Это не настоящий JSON.

# Использование заполнителей

Большинство элементов, у которых есть поля ввода текста, поддерживают заполнители. Вы можете увидеть, поддерживает ли текстовое поле заполнители, при его редактировании. Если при редактировании текста открывается полноэкранный **текстовый редактор**, значит, он поддерживает заполнители. 

Чтобы найти **список всех заполнителей**, просто нажмите кнопку **Заполнители** в **правом верхнем углу** **текстового редактора**.

Вверху списка заполнителей есть **строка поиска**, которая позволяет искать нужные заполнители.

Нажатие на заполнитель в списке заполнителей вставит его в текст.

# Заполнители подробно

Этот список содержит большинство, если не все, заполнители, доступные в FancyMenu. Иногда список может быть немного устаревшим из-за обновлений мода.

## Имя игрока (playername)
Возвращает имя текущего игрока.
```
{"placeholder":"playername"}
```
Пример вывода: `Steve`

## UUID игрока (playeruuid)
Возвращает уникальный идентификатор игрока.
```
{"placeholder":"playeruuid"}
```
Пример вывода: `c8cde7fe-7ced-11eb-9439-0242ac130002`

## Версия Minecraft (mcversion)
Возвращает текущую версию Minecraft.
```
{"placeholder":"mcversion"}
```
Пример вывода: `1.19.2`

## Версия загрузчика модов (loaderver)
Возвращает версию загрузчика модов (Forge/Fabric).
```
{"placeholder":"loaderver"}
```
Пример вывода: `43.2.0`

## Название загрузчика модов (loadername)
Возвращает название загрузчика модов.
```
{"placeholder":"loadername"}
```
Пример вывода: `Forge`

## Версия мода (modversion)
Возвращает версию указанного мода.
```
{"placeholder":"modversion","values":{"modid":"fancymenu"}}
```
Пример вывода: `2.14.9`

## Общее количество модов (totalmods)
Возвращает общее число установленных модов.
```
{"placeholder":"totalmods"}
```
Пример вывода: `45`

## Количество активных модов (loadedmods)
Возвращает количество модов, которые сейчас загружены.
```
{"placeholder":"loadedmods"}
```
Пример вывода: `43`

## Прогресс загрузки мира (world_load_progress)
Возвращает текущий прогресс загрузки мира в процентах.
```
{"placeholder":"world_load_progress"}
```
Пример вывода: `75`

## Значение настройки Minecraft (minecraft_option_value)
Возвращает значение настройки Minecraft.
```
{"placeholder":"minecraft_option_value","values":{"name":"fov"}}
```
Пример вывода: `70`

## Последний мир или сервер (last_world_server)
Возвращает информацию о последнем открытом мире или сервере.
```
{"placeholder":"last_world_server","values":{"type":"both","full_world_path":"true"}}
```
Параметры:
- `type`: Определяет, какой тип информации возвращать
  - `"both"`: Возвращает последний открытый мир или сервер (по умолчанию)
  - `"server"`: Возвращает только если последним был сервер
  - `"world"`: Возвращает только если последним был мир
- `full_world_path`: Управляет отображением пути к миру
  - `"true"`: Возвращает полный путь к миру (по умолчанию)
  - `"false"`: Возвращает только имя мира без пути (не влияет на серверы)

Примеры:
- Сервер: `mc.hypixel.net`
- Мир с полным путём: `saves/New World`
- Мир без полного пути: `New World`

## Ширина экрана (guiwidth)
Возвращает текущую ширину экрана.
```
{"placeholder":"guiwidth"}
```
Пример вывода: `1920`

## Высота экрана (guiheight)
Возвращает текущую высоту экрана.
```
{"placeholder":"guiheight"}
```
Пример вывода: `1080`

## Идентификатор текущего экрана (screenid)
Возвращает идентификатор текущего экрана.
```
{"placeholder":"screenid"}
```
Пример вывода: `title_screen`

## Ширина элемента (elementwidth)
Возвращает ширину указанного элемента.
```
{"placeholder":"elementwidth","values":{"id":"my_button"}}
```
Пример вывода: `200`

## Высота элемента (elementheight)
Возвращает высоту указанного элемента.
```
{"placeholder":"elementheight","values":{"id":"my_button"}}
```
Пример вывода: `20`

## Позиция элемента по X (elementposx)
Возвращает позицию X указанного элемента.
```
{"placeholder":"elementposx","values":{"id":"my_button"}}
```
Пример вывода: `150`

## Позиция элемента по Y (elementposy)
Возвращает позицию Y указанного элемента.
```
{"placeholder":"elementposy","values":{"id":"my_button"}}
```
Пример вывода: `100`

## Позиция мыши по X (mouseposx)
Возвращает текущую позицию мыши по X.
```
{"placeholder":"mouseposx"}
```
Пример вывода: `960`

## Позиция мыши по Y (mouseposy)
Возвращает текущую позицию мыши по Y.
```
{"placeholder":"mouseposy"}
```
Пример вывода: `540`

## Клики в секунду (clicks_per_second)
Возвращает текущее количество кликов в секунду для кнопки мыши.
```
{"placeholder":"clicks_per_second","values":{"mouse_button":"left"}}
```
Параметры:
- `mouse_button`: `left` или `right`

Пример вывода: `8`

## Масштаб GUI (guiscale)
Возвращает текущий масштаб интерфейса.
```
{"placeholder":"guiscale"}
```
Пример вывода: `2`

## Надпись/текст ванильного виджета (vanillabuttonlabel)
Возвращает надпись/текст ванильного виджета/кнопки.
```
{"placeholder":"vanillabuttonlabel","values":{"locator":"some.menu.identifier:505280"}}
```
Пример вывода: `Options...`

## Значение текстового поля ввода (text_input_field_value)
Возвращает текущее значение пользовательского или ванильного текстового поля по идентификатору элемента.
```
{"placeholder":"text_input_field_value","values":{"element_identifier":"my_input"}}
```
Пример вывода: `Hello World`

## Текущее здоровье игрока (current_player_health)
Возвращает текущее количество очков здоровья игрока.
```
{"placeholder":"current_player_health"}
```
Пример вывода: `20.0`

## Максимальное здоровье игрока (max_player_health)
Возвращает максимальное количество очков здоровья игрока.
```
{"placeholder":"max_player_health"}
```
Пример вывода: `20.0`

## Текущее здоровье игрока (в процентах) (current_player_health_percent)
Возвращает здоровье игрока в процентах.
```
{"placeholder":"current_player_health_percent"}
```
Пример вывода: `100`

## Текущее поглощаемое здоровье игрока (current_player_absorption_health)
Возвращает количество очков поглощаемого здоровья игрока (золотые сердца).
```
{"placeholder":"current_player_absorption_health"}
```
Пример вывода: `4.0`

## Максимальное поглощаемое здоровье игрока (max_player_absorption_health)
Возвращает максимальное поглощаемое здоровье.
```
{"placeholder":"max_player_absorption_health"}
```
Пример вывода: `4.0`

## Текущее поглощаемое здоровье игрока (в процентах) (current_player_absorption_health_percent)
Возвращает поглощаемое здоровье игрока в процентах.
```
{"placeholder":"current_player_absorption_health_percent"}
```
Пример вывода: `100`

## Текущий уровень голода игрока (current_player_hunger)
Возвращает текущий уровень голода игрока.
```
{"placeholder":"current_player_hunger"}
```
Пример вывода: `20`

## Максимальный уровень голода игрока (max_player_hunger)
Возвращает максимальный уровень голода.
```
{"placeholder":"max_player_hunger"}
```
Пример вывода: `20`

## Текущий уровень голода игрока (в процентах) (current_player_hunger_percent)
Возвращает голод игрока в процентах.
```
{"placeholder":"current_player_hunger_percent"}
```
Пример вывода: `100`

## Текущая насыщенность голода игрока (current_player_hunger_saturation)
Возвращает текущее значение насыщенности голода игрока.
```
{"placeholder":"current_player_hunger_saturation"}
```
Пример вывода: `5.0`

## Текущая броня игрока (current_player_armor)
Возвращает текущее значение брони игрока.
```
{"placeholder":"current_player_armor"}
```
Пример вывода: `20`

## Прочность брони игрока (player_armor_toughness)
Возвращает общее значение прочности брони игрока.
```
{"placeholder":"player_armor_toughness"}
```
Пример вывода: `8.0`

## Максимальная броня игрока (max_player_armor)
Возвращает максимальное значение брони.
```
{"placeholder":"max_player_armor"}
```
Пример вывода: `20`

## Текущая броня игрока (в процентах) (current_player_armor_percent)
Возвращает броню игрока в процентах.
```
{"placeholder":"current_player_armor_percent"}
```
Пример вывода: `100`

## Текущий уровень кислорода игрока (current_player_oxygen)
Возвращает текущий уровень кислорода игрока (пузыри воздуха).
```
{"placeholder":"current_player_oxygen"}
```
Пример вывода: `300`

## Максимальный уровень кислорода игрока (max_player_oxygen)
Возвращает максимальный уровень кислорода.
```
{"placeholder":"max_player_oxygen"}
```
Пример вывода: `300`

## Текущий уровень кислорода игрока (в процентах) (current_player_oxygen_percent)
Возвращает уровень кислорода игрока в процентах.
```
{"placeholder":"current_player_oxygen_percent"}
```
Пример вывода: `100`

## Текущий уровень игрока (current_player_level)
Возвращает текущий уровень опыта игрока.
```
{"placeholder":"current_player_level"}
```
Пример вывода: `30`

## Текущий опыт игрока (current_player_exp)
Возвращает общее количество очков опыта игрока.
```
{"placeholder":"current_player_exp"}
```
Пример вывода: `1250`

## Прогресс опыта игрока (в процентах) (current_player_exp_progress)
Возвращает прогресс опыта игрока до следующего уровня в процентах.
```
{"placeholder":"current_player_exp_progress"}
```
Пример вывода: `75`

## Сила атаки игрока (в процентах) (player_attack_strength)
Возвращает перезарядку атаки игрока в процентах.
```
{"placeholder":"player_attack_strength"}
```
Пример вывода: `100`

## Игровой режим игрока (player_gamemode)
Возвращает текущий игровой режим игрока.
```
{"placeholder":"player_gamemode"}
```
Пример вывода: `survival`

## Направление взгляда игрока (player_view_direction)
Возвращает направление, в которое смотрит игрок.
```
{"placeholder":"player_view_direction"}
```
Пример вывода: `north`

## Координата X игрока (player_x_coordinate)
Возвращает позицию игрока по оси X в мире.
```
{"placeholder":"player_x_coordinate"}
```
Пример вывода: `125`

## Координата Y игрока (player_y_coordinate)
Возвращает позицию игрока по оси Y в мире.
```
{"placeholder":"player_y_coordinate"}
```
Пример вывода: `64`

## Координата Z игрока (player_z_coordinate)
Возвращает позицию игрока по оси Z в мире.
```
{"placeholder":"player_z_coordinate"}
```
Пример вывода: `-250`

## Текущее здоровье средства передвижения (current_mount_health)
Возвращает текущее здоровье сущности, на которой едет игрок.
```
{"placeholder":"current_mount_health"}
```
Пример вывода: `30.0`

## Максимальное здоровье средства передвижения (max_mount_health)
Возвращает максимальное здоровье сущности, на которой едет игрок.
```
{"placeholder":"max_mount_health"}
```
Пример вывода: `30.0`

## Текущее здоровье средства передвижения (в процентах) (current_mount_health_percent)
Возвращает здоровье средства передвижения в процентах.
```
{"placeholder":"current_mount_health_percent"}
```
Пример вывода: `100`

## Текущий индикатор прыжка средства передвижения (в процентах) (current_mount_jump_meter)
Возвращает значение шкалы силы прыжка средства передвижения.
```
{"placeholder":"current_mount_jump_meter"}
```
Пример вывода: `75`

## Текущее здоровье босса (в процентах) (current_boss_health)
Возвращает здоровье активного босса.
```
{"placeholder":"current_boss_health"}
```
Пример вывода: `150.0`

## Имя босса (boss_name)
Возвращает имя активного босса.
```
{"placeholder":"boss_name","values":{"boss_index":"0","as_json":"false"}}
```
Пример вывода: `Ender Dragon`

## Количество боссов (boss_count)
Возвращает число активных боссов.
```
{"placeholder":"boss_count"}
```
Пример вывода: `1`

## Количество активных эффектов (effects_count)
Возвращает количество активных эффектов зелий.
```
{"placeholder":"effects_count"}
```
Пример вывода: `3`

## Активный эффект (active_effect)
Возвращает информацию об указанном активном эффекте.
```
{"placeholder":"active_effect","values":{"effect_index":"0"}}
```
Пример вывода: `minecraft:speed`

## Выбранный слот хотбара (active_hotbar_slot)
Возвращает текущий выбранный слот хотбара (0-8).
```
{"placeholder":"active_hotbar_slot"}
```
Пример вывода: `4`

## Предмет в слоте (slot_item)
Возвращает информацию о предмете в указанном слоте инвентаря.
```
{"placeholder":"slot_item","values":{"slot":"0"}}
```
Пример вывода: `minecraft:diamond_sword`

## Количество предметов в слоте (slot_item_count)
Возвращает размер стака предмета в указанном слоте инвентаря игрока.
```
{"placeholder":"slot_item_count","values":{"slot":"0"}}
```
Пример вывода: `64`

## Прочность предмета в слоте (slot_item_durability)
Возвращает информацию о прочности предмета в указанном слоте инвентаря игрока.
```
{"placeholder":"slot_item_durability","values":{"slot":"0","format":"percentage"}}
```
Параметры:
- `slot`: Номер слота инвентаря игрока.
- `format`: `current`, `remaining`, `max`, `damage`, `percentage` или `percent`.

Пример вывода: `87`

## Отображаемое имя предмета в слоте (slot_item_display_name_fm)
Возвращает отображаемое имя предмета в указанном слоте как JSON-компонент текста. В режиме наблюдателя слоты хотбара могут возвращать имена предметов меню наблюдателя, если только `ignore_spectator` не равно `true`.
```
{"placeholder":"slot_item_display_name_fm","values":{"slot":"0","ignore_spectator":"false"}}
```
Пример вывода: `{"text":"Diamond Sword","color":"aqua"}`

## Количество предметов в инвентаре (inventory_item_count)
Возвращает общее количество предметов указанного типа в инвентаре игрока. Если `item` пустой, считает все стеки предметов в инвентаре.
```
{"placeholder":"inventory_item_count","values":{"item":"minecraft:diamond"}}
```
Пример вывода: `12`

## Количество восстанавливаемых очков голода предметом в слоте инвентаря (inventory_slot_food_point_restore_amount)
Возвращает количество очков голода, восстанавливаемых едой в указанном слоте инвентаря игрока.
```
{"placeholder":"inventory_slot_food_point_restore_amount","values":{"slot":"0"}}
```
Пример вывода: `4.0`

## Предмет под курсором в инвентаре (hovered_inventory_item)
Возвращает ключ предмета, на который сейчас наведён курсор в экране инвентаря.
```
{"placeholder":"hovered_inventory_item"}
```
Пример вывода: `minecraft:apple`

## Игровое время мира (game_time)
Возвращает текущий счётчик тиков внутриигрового времени.
```
{"placeholder":"game_time"}
```
Пример вывода: `18000`

## Время суток мира (world_daytime)
Возвращает текущее время суток мира.
```
{"placeholder":"world_daytime"}
```
Пример вывода: `13000`

## Час времени суток мира (world_daytime_hour)
Возвращает компонент часов времени мира. По умолчанию используется 24-часовой формат; задайте `twelve_hour_format` как `"true"` для 12-часового формата.
```
{"placeholder":"world_daytime_hour","values":{"twelve_hour_format":"false"}}
```
Пример вывода: `12`

## Минута времени суток мира (world_daytime_minute)
Возвращает компонент минут времени мира (00-59).
```
{"placeholder":"world_daytime_minute"}
```
Пример вывода: `30`

## Сложность мира (world_difficulty)
Возвращает текущую сложность мира.
```
{"placeholder":"world_difficulty"}
```
Пример вывода: `normal`

## Текущий сид одиночного мира (current_world_seed)
Возвращает сид текущего одиночного мира. Если сид недоступен, возвращает пустое значение.
```
{"placeholder":"current_world_seed"}
```
Пример вывода: `123456789`

## Текущий биом (current_biome)
Возвращает биом, в котором сейчас находится игрок. Установите `as_key` в `"false"`, чтобы возвращать переведённое/отображаемое имя, если оно доступно.
```
{"placeholder":"current_biome","values":{"as_key":"true"}}
```
Пример вывода: `minecraft:plains`

## Текущее измерение (current_dimension)
Возвращает измерение, в котором сейчас находится игрок. Установите `as_key` в `"false"`, чтобы возвращать переведённое/отображаемое имя, если оно доступно.
```
{"placeholder":"current_dimension","values":{"as_key":"true"}}
```
Пример вывода: `minecraft:overworld`

## Значение gamerule (gamerule_value)
Возвращает текущее значение gamerule в загруженном мире/на сервере. Для серверных миров требуется FancyMenu на сервере.
```
{"placeholder":"gamerule_value","values":{"name":"doDaylightCycle"}}
```
Пример вывода: `true`

## Категория предмета (item_category)
Возвращает категорию предмета во вкладке творчества. Установите `as_key` в `"true"`, чтобы возвращать ключ категории вместо отображаемого имени.
```
{"placeholder":"item_category","values":{"item":"minecraft:diamond_sword","as_key":"false"}}
```
Пример вывода: `Combat`

## Текущий заголовок/подзаголовок HUD (current_title)
Возвращает текущий отображаемый текст заголовка.
```
{"placeholder":"current_title","values":{"is_subtitle":"false","as_json":"false"}}
```
Пример вывода: `Game Over!`

## Сообщение панели действий (action_bar_message_fm)
Возвращает текущее стандартное сообщение панели действий над хотбаром.
```
{"placeholder":"action_bar_message_fm"}
```
Пример вывода: `You may not rest now`

## Время сообщения панели действий (action_bar_message_time_fm)
Возвращает, сколько тиков ещё будет отображаться текущее стандартное сообщение панели действий.
```
{"placeholder":"action_bar_message_time_fm"}
```
Пример вывода: `42`

## Поворот камеры X (camera_rotation_x_fm)
Возвращает текущий наклон камеры в градусах.
```
{"placeholder":"camera_rotation_x_fm"}
```
Пример вывода: `12.5`

## Поворот камеры Y (camera_rotation_y_fm)
Возвращает текущий поворот камеры по горизонтали в градусах.
```
{"placeholder":"camera_rotation_y_fm"}
```
Пример вывода: `-90.0`

## Изменение поворота камеры по X (camera_rotation_delta_x_fm)
Возвращает изменение наклона камеры за тик.
```
{"placeholder":"camera_rotation_delta_x_fm"}
```
Пример вывода: `0.4`

## Изменение поворота камеры по Y (camera_rotation_delta_y_fm)
Возвращает изменение горизонтального поворота камеры за тик.
```
{"placeholder":"camera_rotation_delta_y_fm"}
```
Пример вывода: `-1.2`

## Время отображения выделенного предмета (highlighted_item_time_fm)
Возвращает, сколько тиков ещё будет отображаться название выделенного предмета над хотбаром.
```
{"placeholder":"highlighted_item_time_fm"}
```
Пример вывода: `30`

## Прогресс использования предмета игроком (player_item_use_progress_fm)
Возвращает текущий прогресс использования предмета от `0.0` до `1.0`.
```
{"placeholder":"player_item_use_progress_fm"}
```
Пример вывода: `0.65`

## Изменение позиции игрока по X (player_position_delta_x_fm)
Возвращает изменение позиции игрока по оси X за тик.
```
{"placeholder":"player_position_delta_x_fm"}
```
Пример вывода: `0.0`

## Изменение позиции игрока по Y (player_position_delta_y_fm)
Возвращает изменение позиции игрока по оси Y за тик.
```
{"placeholder":"player_position_delta_y_fm"}
```
Пример вывода: `-0.08`

## Изменение позиции игрока по Z (player_position_delta_z_fm)
Возвращает изменение позиции игрока по оси Z за тик.
```
{"placeholder":"player_position_delta_z_fm"}
```
Пример вывода: `0.12`

## Текущий IP сервера (current_server_ip)
Возвращает IP подключённого сервера.
```
{"placeholder":"current_server_ip"}
```
Пример вывода: `mc.hypixel.net`

## Список игроков мира (world_players_list)
Возвращает список всех игроков, которые сейчас находятся в мире.
```
{"placeholder":"world_players_list","values":{"separator":", "}}
```
Пример вывода: `Steve, Alex, Notch`

## MOTD сервера (servermotd)
Возвращает сообщение дня сервера.
```
{"placeholder":"servermotd","values":{"ip":"mc.hypixel.net","line":"1"}}
```
Пример вывода: `Welcome to Hypixel!`

## PING сервера (serverping)
Возвращает пинг до сервера в миллисекундах.
```
{"placeholder":"serverping","values":{"ip":"mc.hypixel.net"}}
```
Пример вывода: `54`

## Количество игроков на сервере (serverplayercount)
Возвращает количество игроков на сервере.
```
{"placeholder":"serverplayercount","values":{"ip":"mc.hypixel.net"}}
```
Пример вывода: `25000/30000`

## Статус сервера (serverstatus)
Возвращает статус сервера: онлайн/оффлайн.
```
{"placeholder":"serverstatus","values":{"ip":"mc.hypixel.net"}}
```
Пример вывода: `§aOnline` или `§cOffline`

## Версия сервера (serverversion)
Возвращает версию Minecraft сервера.
```
{"placeholder":"serverversion","values":{"ip":"mc.hypixel.net"}}
```
Пример вывода: `1.19.2`

## Год (realtimeyear)
Возвращает текущий год.
```
{"placeholder":"realtimeyear"}
```
Пример вывода: `2024`

## Месяц (realtimemonth)
Возвращает текущий месяц (01-12).
```
{"placeholder":"realtimemonth"}
```
Пример вывода: `01`

## День (realtimeday)
Возвращает текущий день месяца (01-31).
```
{"placeholder":"realtimeday"}
```
Пример вывода: `27`

## Час (realtimehour)
Возвращает текущий час. По умолчанию используется 24-часовой формат; задайте `twelve_hour_format` как `"true"`, чтобы использовать 12-часовой формат.
```
{"placeholder":"realtimehour","values":{"twelve_hour_format":"false","timezone":"system"}}
```
Пример вывода: `14`

## Минута (realtimeminute)
Возвращает текущую минуту (00-59).
```
{"placeholder":"realtimeminute"}
```
Пример вывода: `30`

## Секунда (realtimesecond)
Возвращает текущую секунду (00-59).
```
{"placeholder":"realtimesecond"}
```
Пример вывода: `45`

## Текущее время в миллисекундах (Unix Timestamp) (unix_time)
Возвращает текущую метку времени Unix в миллисекундах.
```
{"placeholder":"unix_time"}
```
Пример вывода: `1716552478123`

> Реалтайм-заполнители (`realtimeyear`, `realtimemonth`, `realtimeday`, `realtimehour`, `realtimeminute`, `realtimesecond` и `unix_time`) поддерживают значение `timezone`. Используйте обычные идентификаторы часовых поясов Java, такие как `UTC`, `Europe/Berlin` или `America/New_York`; не указывайте его или используйте `system` для системного часового пояса.
{.is-info}

## Информация о CPU (cpuinfo)
Возвращает информацию о процессоре.
```
{"placeholder":"cpuinfo"}
```
Пример вывода: `Intel(R) Core(TM) i7-10700K CPU @ 3.80GHz`

## Загрузка CPU (JVM) (jvmcpu)
Возвращает загрузку CPU JVM в процентах.
```
{"placeholder":"jvmcpu"}
```
Пример вывода: `25.5`

## Загрузка CPU (ОС) (oscpu)
Возвращает загрузку CPU операционной системы в процентах.
```
{"placeholder":"oscpu"}
```
Пример вывода: `42.8`

## Информация о GPU (gpuinfo)
Возвращает информацию о видеокарте.
```
{"placeholder":"gpuinfo"}
```
Пример вывода: `NVIDIA GeForce RTX 3080`

## Версия Java (javaver)
Возвращает версию Java.
```
{"placeholder":"javaver"}
```
Пример вывода: `17.0.2`

## Виртуальная машина Java (jvmname)
Возвращает название Java Virtual Machine.
```
{"placeholder":"jvmname"}
```
Пример вывода: `OpenJDK 64-Bit Server VM`

## Версия OpenGL (glver)
Возвращает версию OpenGL.
```
{"placeholder":"glver"}
```
Пример вывода: `4.6.0 NVIDIA 516.94`

## Название операционной системы (osname)
Возвращает название операционной системы.
```
{"placeholder":"osname"}
```
Пример вывода: `Windows 10`

## FPS (кадров в секунду) (fps)
Возвращает текущую частоту кадров в секунду.
```
{"placeholder":"fps"}
```
Пример вывода: `120`

## Используемая RAM в МБ (usedram)
Возвращает объём RAM, который сейчас используется (МБ).
```
{"placeholder":"usedram"}
```
Пример вывода: `4096`

## Максимальная RAM в МБ (maxram)
Возвращает максимальный выделенный объём RAM (МБ).
```
{"placeholder":"maxram"}
```
Пример вывода: `8192`

## Используемая RAM в %% (percentram)
Возвращает процент используемой в данный момент RAM.
```
{"placeholder":"percentram"}
```
Пример вывода: `50`

## Громкость аудиоэлемента (audio_element_vol)
Возвращает громкость аудиоэлемента.
```
{"placeholder":"audio_element_vol","values":{"element_identifier":"background_music"}}
```
Пример вывода: `0.5`

## Текущий трек аудиоэлемента (audio_element_current_track)
Возвращает название трека аудиоэлемента.
```
{"placeholder":"audio_element_current_track","values":{"element_identifier":"background_music","display_name_mappings":"track1.ogg=>Cool Track Name"}}
```
Пример вывода: `Cool Track Name`

## Длительность аудио (audio_duration)
Возвращает общую длительность аудиотрека в формате MM:SS.
```
{"placeholder":"audio_duration","values":{"element_identifier":"background_music"}}
```
Пример вывода: `03:45`

## Время воспроизведения аудио (audio_playtime)
Возвращает текущее время воспроизведения аудиотрека. Установите `show_percentage` в `"true"`, чтобы получить значение прогресса 0-100 вместо `MM:SS`.
```
{"placeholder":"audio_playtime","values":{"element_identifier":"background_music","show_percentage":"false"}}
```
Пример вывода: `01:30` (или `45`, если `show_percentage` равно `"true"`)

## Состояние воспроизведения аудио (audio_playing_state)
Возвращает, воспроизводится ли аудиоэлемент (true/false).
```
{"placeholder":"audio_playing_state","values":{"element_identifier":"background_music"}}
```
Пример вывода: `true`

## Громкость видеоэлемента (video_element_vol)
Возвращает уровень громкости видеоэлемента (0.0 to 1.0).
```
{"placeholder":"video_element_vol","values":{"element_identifier":"my_video_element"}}
```
Пример вывода: `0.5`

## Длительность видеоэлемента (video_element_duration)
Возвращает общую длительность видеоэлемента в формате `MM:SS`. Установите `output_as_timestamp` в `"true"`, чтобы получить метку времени в миллисекундах.
```
{"placeholder":"video_element_duration","values":{"element_identifier":"my_video_element","output_as_timestamp":"false"}}
```
Пример вывода: `02:00` (или `120000`, если `output_as_timestamp` равно `"true"`)

## Время воспроизведения видеоэлемента (video_element_playtime)
Возвращает текущее время воспроизведения (прогресс) видеоэлемента в формате `MM:SS`. Установите `show_percentage` в `"true"` для значения прогресса 0-100, или `output_as_timestamp` в `"true"` для миллисекунд.
```
{"placeholder":"video_element_playtime","values":{"element_identifier":"my_video_element","show_percentage":"false","output_as_timestamp":"false"}}
```
Пример вывода: `00:45` (или `38` в процентах, или `45200` как метка времени)

## Состояние паузы видеоэлемента (video_element_paused_state)
Возвращает, поставлен ли видеоэлемент на паузу (true/false).
```
{"placeholder":"video_element_paused_state","values":{"element_identifier":"my_video_element"}}
```
Пример вывода: `false`

## Громкость фонового видео (video_background_vol)
Возвращает уровень громкости фона видео в меню (0.0 to 1.0).
```
{"placeholder":"video_background_vol","values":{"background_identifier":"main_menu_video"}}
```
Пример вывода: `0.7`

## Длительность фонового видео (video_background_duration)
Возвращает общую длительность фонового видео в меню в формате `MM:SS`. Установите `output_as_timestamp` в `"true"`, чтобы получить метку времени в миллисекундах.
```
{"placeholder":"video_background_duration","values":{"background_identifier":"main_menu_video","output_as_timestamp":"false"}}
```
Пример вывода: `03:00` (или `180000`, если `output_as_timestamp` равно `"true"`)

## Время воспроизведения фонового видео (video_background_playtime)
Возвращает текущее время воспроизведения (прогресс) фонового видео в меню в формате `MM:SS`. Установите `show_percentage` в `"true"` для значения прогресса 0-100, или `output_as_timestamp` в `"true"` для миллисекунд.
```
{"placeholder":"video_background_playtime","values":{"background_identifier":"main_menu_video","show_percentage":"false","output_as_timestamp":"false"}}
```
Пример вывода: `01:00` (или `33` в процентах, или `60500` как метка времени)

## Состояние паузы фонового видео (video_background_paused_state)
Возвращает, поставлен ли фон видео в меню на паузу (true/false).
```
{"placeholder":"video_background_paused_state","values":{"background_identifier":"main_menu_video"}}
```
Пример вывода: `true`

## Калькулятор (calc)
Заполнитель калькулятора — это мощный инструмент, который позволяет выполнять математические вычисления внутри ваших макетов. Он поддерживает широкий спектр математических операций и может работать как с десятичными, так и с целыми числами.

### Базовый синтаксис
```
{"placeholder":"calc","values":{"decimal":"true/false","expression":"your_expression"}}
```

У калькулятора есть два основных параметра:
- `decimal`: Определяет, должен ли результат содержать десятичные знаки (`true`) или быть округлённым до целых (`false`)
- `expression`: Математическое выражение для вычисления

### Поддерживаемые операции
Калькулятор поддерживает следующие математические операции:
- Базовая арифметика: `+` (сложение), `-` (вычитание), `*` (умножение), `/` (деление)
- Скобки: `( )` для группировки операций
- Степень: `^` для возведения в степень
- Квадратный корень: `sqrt()`
- Тригонометрические функции: `sin()`, `cos()`, `tan()`
- Математические константы: `pi`, `e`
- Модуль: `abs()`
- Логарифмы: `log()`, `ln()`

## Случайное число (random_number)
Генерирует случайное число в указанном диапазоне.
```
{"placeholder":"random_number","values":{"min":"1","max":"100"}}
```
Пример вывода: `42`

## Максимальное число (maxnum)
Возвращает большее из двух чисел.
```
{"placeholder":"maxnum","values":{"first":"10","second":"20"}}
```
Пример вывода: `20`

## Минимальное число (minnum)
Возвращает меньшее из двух чисел.
```
{"placeholder":"minnum","values":{"first":"10","second":"20"}}
```
Пример вывода: `10`

## Модуль числа (absnum)
Возвращает абсолютное значение числа.
```
{"placeholder":"absnum","values":{"num":"-10.5"}}
```
Пример вывода: `10.5`

## Отрицание числа (negnum)
Возвращает отрицательное значение числа.
```
{"placeholder":"negnum","values":{"num":"10.5"}}
```
Пример вывода: `-10.5`

## *пи* (Math) (math_pi)
Возвращает значение π.
```
{"placeholder":"math_pi"}
```
Пример вывода: `3.141592653589793`

## Тригонометрический синус (Math) (math_sin)
Возвращает синус угла.
```
{"placeholder":"math_sin","values":{"angle":"45"}}
```
Пример вывода: `0.7071067811865476`

## Тригонометрический косинус (Math) (math_cos)
Возвращает косинус угла.
```
{"placeholder":"math_cos","values":{"angle":"45"}}
```
Пример вывода: `0.7071067811865476`

## Тригонометрический тангенс (Math) (math_tan)
Возвращает тангенс угла.
```
{"placeholder":"math_tan","values":{"angle":"45"}}
```
Пример вывода: `1.0`

## Округление вниз (Math) (math_floor)
Округляет число вниз до ближайшего целого.
```
{"placeholder":"math_floor","values":{"num":"3.14"}}
```
Пример вывода: `3`

## Округление вверх (Math) (math_ceil)
Округляет число вверх до ближайшего целого.
```
{"placeholder":"math_ceil","values":{"num":"3.14"}}
```
Пример вывода: `4`

## Округление (Math) (math_round)
Округляет число. По умолчанию — до ближайшего целого; задайте `decimals` неотрицательным числом, чтобы округлить до указанного количества знаков после запятой.
```
{"placeholder":"math_round","values":{"num":"3.14159","decimals":"2"}}
```
Пример вывода: `3.14` (при `decimals:-1` или если параметр не указан → `3`)

## Знак числа (Math) (math_sign)
Возвращает знак числа (1 для положительного, -1 для отрицательного, 0 для нуля).
```
{"placeholder":"math_sign","values":{"num":"-3.14"}}
```
Пример вывода: `-1`

## Гиперболический синус (Math) (math_sinh)
Возвращает гиперболический синус угла.
```
{"placeholder":"math_sinh","values":{"angle":"1"}}
```
Пример вывода: `1.1752011936438014`

## Гиперболический косинус (Math) (math_cosh)
Возвращает гиперболический косинус угла.
```
{"placeholder":"math_cosh","values":{"angle":"1"}}
```
Пример вывода: `1.5430806348152437`

## Гиперболический тангенс (Math) (math_tanh)
Возвращает гиперболический тангенс угла.
```
{"placeholder":"math_tanh","values":{"angle":"1"}}
```
Пример вывода: `0.7615941559557649`

## Разделение текста (split_text)
Разделяет текст с помощью указанного разделителя.
```
{"placeholder":"split_text","values":{"input":"hello,world","regex":",","max_parts":"2","split_index":"1"}}
```
Пример вывода: `world`

## Обрезка пробелов (trim_text)
Удаляет пробелы в начале и конце строки.
```
{"placeholder":"trim_text","values":{"text":"  hello world  "}}
```
Пример вывода: `hello world`

## Обрезка текста (crop_text)
Удаляет символы с начала и конца текста.
```
{"placeholder":"crop_text","values":{"text":"hello world","remove_from_start":"1","remove_from_end":"1"}}
```
Пример вывода: `ello worl`

## Строковое представление (stringify)
Преобразует текст в строку, экранируя все символы синтаксиса.
```
{"placeholder":"stringify","values":{"text":"text with {special} \"characters\""}}
```
Пример вывода: `text with \{special\} \"characters\"`

## Локализованный текст (local)
Получает локализованный текст по ключу.
```
{"placeholder":"local","values":{"key":"menu.singleplayer"}}
```
Пример вывода: `Singleplayer`

## Веб-текст (webtext)
Получает текстовое содержимое из веб-URL.
```
{"placeholder":"webtext","values":{"link":"http://somewebsite.com/textfile.txt"}}
```
Пример вывода: Текстовое содержимое из URL

## Случайный текст (randomtext)
Возвращает случайную строку из текстового файла, URL или прямого обычного текста. Текст меняется через указанные интервалы.
```
{"placeholder":"randomtext","values":{"source":"/config/fancymenu/assets/<file_name.txt>","interval":"10"}}
```
Параметры:
- `source`: Источник текстовых строк (заменяет старый параметр `path`)
  - Путь к файлу: `/config/fancymenu/assets/quotes.txt`
  - URL: `https://example.com/quotes.txt`
  - Обычный текст: `Line 1\nLine 2\nLine 3`
- `interval`: Интервал в секундах между изменениями текста

Теперь заполнител поддерживает три типа источника:
1. **Локальные файлы**: текстовые файлы из каталога игры
   ```
   {"placeholder":"randomtext","values":{"source":"/config/fancymenu/assets/quotes.txt","interval":"10"}}
   ```
2. **URL**: удалённые текстовые файлы из интернета
   ```
   {"placeholder":"randomtext","values":{"source":"https://example.com/quotes.txt","interval":"10"}}
   ```
3. **Обычный текст**: прямой ввод текста со строками, разделёнными `\n`
   ```
   {"placeholder":"randomtext","values":{"source":"First line\nSecond line\nThird line","interval":"5"}}
   ```

Примечание: Старые заполнители, использующие `path` вместо `source`, продолжат работать.

## JSON-парсер (json)
Парсит JSON-данные из файла, URL или прямого JSON-содержимого и извлекает значения с помощью выражений JSON Path.
```
{"placeholder":"json","values":{"source":"path_or_link_or_json_content","json_path":"$.some.json.path"}}
```
Параметры:
- `source`: Источник JSON-данных
  - Путь к файлу: `/config/fancymenu/assets/data.json`
  - URL: `https://api.example.com/data.json`
  - Прямой JSON: `{"name":"Steve","level":42}`
- `json_path`: Выражение JSON Path для извлечения данных

Теперь заполнител поддерживает три типа источника:
1. **Локальные файлы**: JSON-файлы из каталога игры
   ```
   {"placeholder":"json","values":{"source":"/config/fancymenu/assets/playerdata.json","json_path":"$.player.name"}}
   ```
2. **URL**: удалённые JSON-данные из API или веб-сервисов
   ```
   {"placeholder":"json","values":{"source":"https://api.minecraft.com/server/status","json_path":"$.online"}}
   ```
3. **Прямой JSON**: встроенное JSON-содержимое
   ```
   {"placeholder":"json","values":{"source":"{"name":"Steve","score":42,"rank":"Diamond"}","json_path":"$.rank"}}
   ```

Примеры JSON Path:
- `$.name` — получает поле "name" из корня
- `$.player.level` — получает вложенное поле "level" внутри "player"
- `$.items[0].id` — получает "id" первого элемента массива
- `$.scores.*` — получает все значения из объекта "scores"

## Абсолютный путь к файлу/папке (absolute_path)
Возвращает абсолютный путь к файлу.
```
{"placeholder":"absolute_path","values":{"short_path":"relative/path/to/file.txt"}}
```
Пример вывода: `C:/Users/Username/AppData/Roaming/.minecraft/relative/path/to/file.txt`

## Количество символов в тексте (text_character_count)
Возвращает количество символов в указанном тексте.
```
{"placeholder":"text_character_count","values":{"text":"Hello World!"}}
```
Пример вывода: `12`

## Ширина текста (text_width)
Возвращает ширину указанного текста в пикселях при отрисовке.
```
{"placeholder":"text_width","values":{"text":"Hello World!"}}
```
Пример вывода: `66`

## Текст в верхнем регистре (uppercase_text)
Преобразует входной текст в заглавные буквы.
```
{"placeholder":"uppercase_text","values":{"text":"Hello World"}}
```
Пример вывода: `HELLO WORLD`

## Текст в нижнем регистре (lowercase_text)
Преобразует входной текст в строчные буквы.
```
{"placeholder":"lowercase_text","values":{"text":"Hello World"}}
```
Пример вывода: `hello world`

## Текст в формате Title Case (title_case_text)
Преобразует входной текст в формат с заглавными буквами в начале слов.
```
{"placeholder":"title_case_text","values":{"text":"hello world"}}
```
Пример вывода: `Hello World`

## Текст в формате предложения (sentence_case_text)
Преобразует входной текст в формат предложения.
```
{"placeholder":"sentence_case_text","values":{"text":"hello world. this is fancymenu!"}}
```
Пример вывода: `Hello world. This is fancymenu!`

## Текст в snake_case (snake_case_text)
Преобразует входной текст в `snake_case`.
```
{"placeholder":"snake_case_text","values":{"text":"Hello World"}}
```
Пример вывода: `hello_world`

## Текст в kebab-case (kebab_case_text)
Преобразует входной текст в `kebab-case`.
```
{"placeholder":"kebab_case_text","values":{"text":"Hello World"}}
```
Пример вывода: `hello-world`

## Текст с чередованием регистра (alternating_case_text)
Преобразует входной текст в чередующийся регистр.
```
{"placeholder":"alternating_case_text","values":{"text":"alternating case"}}
```
Пример вывода: `aLtErNaTiNg CaSe`

## Переключение регистра текста (toggle_case_text)
Меняет регистр каждой буквы во входном тексте.
```
{"placeholder":"toggle_case_text","values":{"text":"Toggle Case"}}
```
Пример вывода: `tOGGLE cASE`

## Кодировать в Base64 (base64_encode)
Кодирует указанный текст в Base64.
```
{"placeholder":"base64_encode","values":{"text":"Hello World"}}
```
Пример вывода: `SGVsbG8gV29ybGQ=`

## Декодировать из Base64 (base64_decode)
Декодирует строку Base64 обратно в обычный текст.
```
{"placeholder":"base64_decode","values":{"text":"SGVsbG8gV29ybGQ="}}
```
Пример вывода: `Hello World`

## Текст из файла (file_text)
Возвращает строки текста из файла или URL. Может возвращать все строки или только последние X строк.
```
{"placeholder":"file_text","values":{"path_or_url":"/config/fancymenu/assets/some_file.txt","mode":"all","separator":"\n","last_lines":"1"}}
```
Параметры:
- `path_or_url`: Путь к файлу или URL для чтения
- `mode`: Либо `"all"` (возвращает все строки), либо `"last"` (возвращает только последние X строк)
- `separator`: Текст для объединения строк (по умолчанию: `"\n"`)
- `last_lines`: Количество строк, которое нужно вернуть, если `mode` равно `"last"` (по умолчанию: `"1"`)

Пример вывода: Зависит от содержимого файла

## Содержимое буфера обмена (clipboard_content)
Возвращает текущий текст, хранящийся в системном буфере обмена.
```
{"placeholder":"clipboard_content"}
```
Пример вывода: Любой текст, который сейчас находится в буфере обмена

## Замена текста (replace_text)
Заменяет текст в строке с помощью буквального совпадения или регулярных выражений.
```
{"placeholder":"replace_text","values":{"text":"Hello World! This is a test.","search":"World","replacement":"FancyMenu","use_regex":"false","replace_all":"true"}}
```
Параметры:
- `text`: Входной текст для обработки
- `search`: Текст или шаблон regex для поиска
- `replacement`: Текст замены
- `use_regex`: Использовать ли regex (`"true"`) или буквальное совпадение (`"false"`)
- `replace_all`: Заменять все вхождения (`"true"`) или только первое (`"false"`)

Пример вывода: `Hello FancyMenu! This is a test.`

## Переключатель вариантов (switch_case)
Выполняет операцию switch-case на основе значения.
```
{"placeholder":"switch_case","values":{"value":"1","cases":"1:first case,2:second case,3:third case","default":"default case"}}
```
Пример вывода: `first case` (если значение равно 1)

## Получить значение переменной (FM Variable) (getvariable)
Извлекает значение ранее сохранённой переменной.
```
{"placeholder":"getvariable","values":{"name":"some_variable"}}
```
Пример вывода: Зависит от сохранённого значения

## Получить NBT-данные (nbt_data_get)
Извлекает NBT-данные на клиенте (аналог команды `/data get`). Используйте серверный вариант `nbt_data_get_server`, когда вы подключены к серверу и нужны авторитетные серверные значения.
```
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"foodLevel","scale":"1.0","return_type":"value"}}
```
Параметры:
- `source_type`: Либо `"entity"`, либо `"block"`
- `entity_selector`: Селектор сущности, например `@s`, `@p`, `@e`, либо UUID/имя (для сущностей)
- `block_pos`: Позиция блока в формате `"x y z"` (для блоков)
- `nbt_path`: Путь NBT для извлечения
- `scale`: Необязательный коэффициент масштабирования для числовых значений (по умолчанию: `"1.0"`)
- `return_type`: Как возвращать данные:
  - `"value"`: По умолчанию, возвращает значение (с необязательным масштабированием для чисел)
  - `"string"`: Возвращает сами NBT-данные как строку
  - `"snbt"`: Возвращает SNBT (форматированные NBT-данные)
  - `"json"`: Возвращает JSON-форматированный компонент (для compound-тегов)

Пример вывода: `20` (для уровня голода)

## Получить NBT-данные (на стороне сервера) (nbt_data_get_server)
Запрашивает NBT-данные на стороне сервера (с помощью пакета) и ненадолго кэширует результаты. Значения соответствуют клиентскому заполнителю.
```
{"placeholder":"nbt_data_get_server","values":{"source_type":"entity","entity_selector":"@s","block_pos":"","storage_id":"minecraft:storage_key","nbt_path":"SelectedItem.id","scale":"1.0","return_type":"value"}}
```
Пример вывода: `minecraft:diamond_sword`

## Последнее сообщение о смерти (lastdeathmessage)
Возвращает последнее записанное сообщение о смерти клиента-игрока. Установите `as_json_component` в `"true"`, чтобы получить исходный JSON-компонент текста.
```
{"placeholder":"lastdeathmessage","values":{"as_json_component":"false"}}
```
Пример вывода: `Steve was slain by Zombie`

## Длительность работы (uptime_duration)
Возвращает, как долго загружен FancyMenu. По умолчанию значение измеряется в секундах; установите `output_as_millis` в `"true"`, чтобы получить миллисекунды.
```
{"placeholder":"uptime_duration","values":{"output_as_millis":"false"}}
```
Пример вывода: `742` (секунд с момента загрузки)

## Имена сохранений миров (level_save_names)
Перечисляет все локальные сохранения миров, объединяя их выбранным разделителем. Выполняется в потоке клиента.
```
{"placeholder":"level_save_names","values":{"separator":", "}}
```
Пример вывода: `Creative Test, Survival World, Hardcore`

## Данные сохранения мира (level_save_data)
Возвращает сериализованные данные уровня для указанного имени мира (должно совпадать с отображаемым именем в списке сохранений).
```
{"placeholder":"level_save_data","values":{"level_name":"Survival World"}}
```
Пример вывода: `{"name":"Survival World","gameMode":"survival",...}`

## Конвертер систем счисления (number_base_convert)
Преобразует число (целое или дробное) из одной системы счисления в другую (2–36). По умолчанию используется десятичная система, если основания не указаны.
```
{"placeholder":"number_base_convert","values":{"input":"67.5","from_base":"10","to_base":"16"}}
```
Пример вывода: `43.8`

## Размер файла (file_size)
Возвращает размер локального файла в байтах. Разрешены только локальные пути.
```
{"placeholder":"file_size","values":{"path":"/config/fancymenu/assets/notes.txt"}}
```
Пример вывода: `1284`

## MD5 файла (file_md5)
Возвращает MD5-хэш локального файла в виде шестнадцатеричной строки в нижнем регистре.
```
{"placeholder":"file_md5","values":{"path":"/config/fancymenu/assets/notes.txt"}}
```
Пример вывода: `d41d8cd98f00b204e9800998ecf8427e`

# Практические примеры

## Создание динамического отображения памяти
```
Используемая RAM: {"placeholder":"usedram"}МБ / {"placeholder":"maxram"}МБ ({"placeholder":"percentram"}%)
```

## Создание часов реального времени
```
{"placeholder":"realtimehour"}:{"placeholder":"realtimeminute"}:{"placeholder":"realtimesecond"}
```

## Создание отображения системной информации
```
OS: {"placeholder":"osname"}
CPU: {"placeholder":"cpuinfo"}
GPU: {"placeholder":"gpuinfo"}
Java: {"placeholder":"javaver"}
```

## HUD состояния игрока
```
Здоровье: {"placeholder":"current_player_health"} / {"placeholder":"max_player_health"} ({"placeholder":"current_player_health_percent"}%)
Броня: {"placeholder":"current_player_armor"} / {"placeholder":"max_player_armor"}
Уровень XP: {"placeholder":"current_player_level"}
```

## Сложный расчёт с вложенными заполнителями
```
{"placeholder":"calc","values":{"decimal":"true","expression":"({"placeholder":"usedram"} / {"placeholder":"maxram"}) * 100"}}
```

## Отображение координат с округлением
```
X: {"placeholder":"math_round","values":{"num":"{"placeholder":"player_x_coordinate"}"}}
Y: {"placeholder":"math_round","values":{"num":"{"placeholder":"player_y_coordinate"}"}}
Z: {"placeholder":"math_round","values":{"num":"{"placeholder":"player_z_coordinate"}"}}
```

# Лучшие практики

1. **Кэшируйте дорогие операции**: Некоторые заполнители (например, те, что читают системную информацию) могут быть ресурсоёмкими. Рассмотрите возможность использования переменных для хранения их значений, если вам нужно использовать их несколько раз.

2. **Используйте подходящие настройки decimal**: При работе с вычислениями используйте параметр `decimal` надлежащим образом. Устанавливайте его в `false`, когда нужны целые числа, и в `true`, когда нужны точные десятичные значения.

3. **Обрабатывайте отсутствующие значения**: Всегда учитывайте, что должно происходить, если заполнител не возвращает значение. В таких случаях может быть полезно задать значения по умолчанию.

4. **Проверяйте производительность**: При использовании множества заполнителей или сложных вложенных структур тестируйте влияние на производительность, особенно на слабых системах.

5. **Используйте расширенное изменение размеров и позиционирование**: Для динамических элементов интерфейса комбинируйте заполнители с расширенными настройками размера и позиционирования, чтобы создавать адаптивные макеты.

6. **Сочетайте с переменными**: Используйте заполнители вместе с переменными для ещё более динамического содержимого, которое можно обновлять через действия.

# Частые проблемы и решения

## Заполнитель не обновляется
Если значение заполнителя не обновляется так, как ожидается, проверьте:
- Правильно ли отформатирован заполнител
- Используете ли вы правильный регистр в идентификаторах заполнителей
- Не требует ли заполнител особых условий для обновления

## Вложенные заполнители не работают
При вложении заполнителей:
- Убедитесь, что кавычки правильно экранированы
- Проверьте, что каждый вложенный заполнител сам по себе корректен

## Проблемы с производительностью
Если вы замечаете проблемы с производительностью:
- Уменьшите количество используемых заполнителей
- Избегайте ненужного вложения
- Рассмотрите использование переменных для часто запрашиваемых значений
- Используйте подходящий заполнител для ваших задач (например, не используйте заполнители реального времени, если достаточно статических значений)
