---
title: Расположение хранилищ данных
description: >-
  Где FancyMenu хранит макеты, ресурсы, конфигурацию и постоянное состояние во
  время работы.
---

# Расположение хранилищ данных

`<game-directory>` означает активную папку экземпляра Minecraft, которая может отличаться от `.minecraft`.

Каталоги и файлы обычно создаются только после инициализации или использования соответствующей функции. Закрывайте Minecraft перед ручным редактированием сгенерированных файлов состояния и обязательно делайте резервную копию при переносе или сбросе данных.

# Макеты, ресурсы и конфигурация

Некоторые записи — это авторская конфигурация или ресурсы; другие — состояние, которое FancyMenu обновляет во время работы.

| Система / Функция | Файл или каталог |
| --- | --- |
| Настраиваемые экраны | `<game-directory>/config/fancymenu/customizablemenus.txt` |
| [Пользовательские GUI](./custom-guis) и правила переопределения экранов | `<game-directory>/config/fancymenu/custom_gui_screens.txt` |
| Макеты | `<game-directory>/config/fancymenu/customization/` |
| [Локальные ресурсы](./resources#local-resources) | `<game-directory>/config/fancymenu/assets/` |
| [Файлы пользовательской локализации](./localization#fancymenu-custom-localization-files) | `<game-directory>/config/fancymenu/custom_locals/` |
| [Панорамы](./panoramas) | `<game-directory>/config/fancymenu/panoramas/` |
| [Слайд-шоу](./slideshows) | `<game-directory>/config/fancymenu/slideshows/` |
| [Переменные FancyMenu](./variables) | `<game-directory>/config/fancymenu/user_variables.db` |
| Метаданные контроллера [видеоэлемента](./elements#video) | `<game-directory>/config/fancymenu/video_element_controller_metas.json` |
| Метаданные контроллера [аудиоэлемента](./elements#audio) | `<game-directory>/config/fancymenu/audio_element_controller_metas.json` |
| Слушатели сервера [FM Data](./fm-data) | `<game-directory>/config/fancymenu/fmdata_server_listeners.json` |
| Приветственные данные [FM Data](./fm-data) | `<game-directory>/config/fancymenu/fmdata_welcome_data.json` |
| Экземпляры [слушателей](./listeners) и скрипты действий | `<game-directory>/config/fancymenu/listener_instances.txt` |
| [Планировщики](./schedulers) | `<game-directory>/config/fancymenu/scheduler_instances.txt` |

`customizablemenus.txt` управляется переключателем **Current Screen Customization** и хранит идентификаторы конкретных классов экранов. Не добавляйте идентификаторы [Universal Layout](./universal-layouts); FancyMenu игнорирует их при загрузке файла.

На выделенном сервере два файла FM Data находятся относительно корневой папки игры этого сервера. Остальные клиентские конфигурации и ресурсы относятся к экземпляру каждого игрока.

# Постоянное состояние во время работы

FancyMenu хранит дополнительное сгенерированное состояние для каждого экземпляра вне `config/fancymenu/`. Включайте эти пути в резервную копию только если хотите сохранить соответствующее состояние пользователя/времени выполнения; это не определения макетов и не исходные ресурсы.

| Система / Функция | Файл или каталог |
| --- | --- |
| Состояния не-`variable` [Checkbox](./elements#checkbox) | `<game-directory>/checkbox_states.json` |
| Позиции/метаданные элемента [Dragger](./dragger) | `<game-directory>/fancymenu_data/dragger_metas.json` |
| Состояние последнего мира | `<game-directory>/fancymenu_data/last_world.fmdata` |
| Состояние [Seamless World Loading](./seamless-world-loading) | `<game-directory>/fancymenu_data/seamless_world_loading/` |
| Сохранения питомца Buddy и уровней | `<game-directory>/fancymenu_data/buddy/` |
| Позиции и видимость виджетов редактора макета | `<game-directory>/config/fancymenu/layout_editor/widgets/` |
| Маркер инициализации масштаба GUI по умолчанию | `<game-directory>/fancymenu_data/default_scale_set.fm` |

Buddy хранит состояние питомца и состояние уровней/достижений в отдельных JSON-файлах внутри своего каталога. Каждый экземпляр наложения Buddy использует свою пару файлов.

Файлы виджетов редактора макета хранят позицию, размер, видимость, состояние разворачивания и сторону привязки каждого виджета. Удаление `default_scale_set.fm` заставляет FancyMenu считать, что настроенный масштаб GUI по умолчанию ещё не был применён при следующем запуске.
