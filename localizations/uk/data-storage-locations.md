---
title: Розташування даних
description: >-
  Де FancyMenu зберігає макети, ресурси, конфігурацію та постійний стан
  виконання.
---

# Розташування даних

`<game-directory>` означає активну теку екземпляра Minecraft, яка може відрізнятися від `.minecraft`.

Теки та файли зазвичай створюються лише після того, як пов’язану функцію ініціалізовано або використано. Закрийте Minecraft перед ручним редагуванням згенерованих файлів стану та зберігайте резервну копію під час міграції або скидання даних.

# Макети, ресурси та конфігурація

Деякі записи — це авторські конфігурації або ресурси; інші — це стан, який FancyMenu оновлює під час виконання.

| Система / функція | Файл або тека |
| --- | --- |
| Налаштовувані екрани | `<game-directory>/config/fancymenu/customizablemenus.txt` |
| [Користувацькі GUI](./custom-guis) та правила перевизначення екранів | `<game-directory>/config/fancymenu/custom_gui_screens.txt` |
| Макети | `<game-directory>/config/fancymenu/customization/` |
| [Локальні ресурси](./resources#local-resources) | `<game-directory>/config/fancymenu/assets/` |
| [Користувацькі файли локалізації](./localization#fancymenu-custom-localization-files) | `<game-directory>/config/fancymenu/custom_locals/` |
| [Панорами](./panoramas) | `<game-directory>/config/fancymenu/panoramas/` |
| [Слайд-шоу](./slideshows) | `<game-directory>/config/fancymenu/slideshows/` |
| [Змінні FancyMenu](./variables) | `<game-directory>/config/fancymenu/user_variables.db` |
| Метадані контролера [елемента відео](./elements#video) | `<game-directory>/config/fancymenu/video_element_controller_metas.json` |
| Метадані контролера [аудіоелемента](./elements#audio) | `<game-directory>/config/fancymenu/audio_element_controller_metas.json` |
| Слухачі сервера [FM Data](./fm-data) | `<game-directory>/config/fancymenu/fmdata_server_listeners.json` |
| Дані привітання [FM Data](./fm-data) | `<game-directory>/config/fancymenu/fmdata_welcome_data.json` |
| Екземпляри [слухачів](./listeners) і сценарії дій | `<game-directory>/config/fancymenu/listener_instances.txt` |
| [Планувальники](./schedulers) | `<game-directory>/config/fancymenu/scheduler_instances.txt` |

`customizablemenus.txt` керується перемикачем **Current Screen Customization** і зберігає конкретні ідентифікатори класів екранів. Не додавайте ідентифікатори [Universal Layout](./universal-layouts); FancyMenu ігнорує їх під час завантаження файлу.

На виділеному сервері два файли FM Data розташовуються відносно кореня гри цього сервера. Інші налаштування та ресурси, що належать клієнту, зберігаються в екземплярі кожного гравця.

# Постійний стан виконання

FancyMenu зберігає додатковий згенерований стан для кожного екземпляра поза межами `config/fancymenu/`. Додавайте ці шляхи до резервної копії лише тоді, коли хочете зберегти пов’язаний стан користувача/виконання; це не макети й не вихідні ресурси.

| Система / функція | Файл або тека |
| --- | --- |
| Стан [Checkbox](./elements#checkbox), не пов’язаний зі змінними | `<game-directory>/checkbox_states.json` |
| Позиції/метадані елемента [Dragger](./dragger) | `<game-directory>/fancymenu_data/dragger_metas.json` |
| Останній стан світу | `<game-directory>/fancymenu_data/last_world.fmdata` |
| Стан [Seamless World Loading](./seamless-world-loading) | `<game-directory>/fancymenu_data/seamless_world_loading/` |
| Збереження Buddy-пета та прогресу рівнів | `<game-directory>/fancymenu_data/buddy/` |
| Позиції й видимість віджетів редактора макета | `<game-directory>/config/fancymenu/layout_editor/widgets/` |
| Маркер ініціалізації стандартного масштабу GUI | `<game-directory>/fancymenu_data/default_scale_set.fm` |

Buddy зберігає стан пета та стан рівнів/досягнень у окремих JSON-файлах у межах своєї теки. Кожен екземпляр Buddy overlay використовує власну пару файлів.

Файли віджетів редактора макета зберігають для кожного віджета його позицію, розмір, видимість, розгорнутий стан і сторону прилипання. Видалення `default_scale_set.fm` призведе до того, що під час наступного запуску FancyMenu вважатиме налаштований стандартний масштаб GUI таким, що ще не було застосовано.
