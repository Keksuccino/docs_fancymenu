---
title: Скрипти дій
description: 'Як використовувати скрипти дій із кнопками, повзунками, тікерами та іншим.'
---

# Скрипти дій

FancyMenu дає змогу додавати інтерактивність до ваших меню, призначаючи елементам **дії**. Ці дії виконуються, коли кнопку натиснуто, тікер оновлюється, використано повзунок або коли екран відкривається чи закривається. Ви також можете створювати складні скрипти дій за допомогою простих керувальних операторів, таких як **if**, **else-if**, **else** і **while**, щоб контролювати, які дії виконуються і коли.

<img src="https://github.com/Keksuccino/FancyMenu/blob/master/assets/docs/action_script_editor.png?raw=true" alt="Редактор скриптів дій" style="max-width:800px;width:100%;height:auto;">

# Що таке дії?

**Дія** — це завдання або операція, яку FancyMenu виконує під час спрацювання. Наприклад, дія може відкривати новий екран, надсилати повідомлення в чат або регулювати гучність аудіоелемента. В редакторі FancyMenu дії налаштовуються зі значенням (за потреби), яке містить додаткові деталі — наприклад, URL або адресу сервера.

# Що таке оператори?

Щоб створювати складнішу поведінку, FancyMenu підтримує базові керувальні оператори в скриптах дій. До них належать:

- **If Statement:** Виконує блок дій лише тоді, коли виконується вказана [умова](/en/conditions).
- **Else-If Statement:** Перевіряє іншу [умову](/en/conditions), якщо попередній *if* (або попередній *else-if*) не спрацював.
- **Else Statement:** Виконується, якщо жодна з попередніх [умов](/en/conditions) не виконується.
- **While Statement:** Безперервно повторює блок дій, поки [умова](/en/conditions) залишається істинною (із вбудованим тайм-аутом для запобігання нескінченним циклам).
- **Delay Block:** Очікує вказаний час перед виконанням дій усередині нього. Решта скрипта продовжує виконуватися, поки триває відлік затримки.
- **Execute Later Block:** Ставит у чергу дії всередині блока для виконання в головному потоці після затримки в мілісекундах.
- **Comment:** Додає примітку всередині скрипта для зручності. Коментарі не виконують жодних дій.

Поєднуючи ці оператори з діями, ви можете будувати динамічну та умовну поведінку, наприклад, перевіряти, чи низьке здоров’я гравця, перш ніж надсилати попереджувальне повідомлення, або повторювати оновлення, доки умова не зміниться.

# Де можна використовувати скрипти дій?

Скрипти дій універсальні та можуть використовуватися в усій вашій розкладці. Їх можна призначати, наприклад, для:

- **Buttons:** Виконання дії під час натискання кнопки.
- **Tickers:** Безперервне виконання скрипта дій для оновлення інформації на екрані в межах розкладки.
- **Sliders:** Запуск скрипта дій щоразу, коли змінюється значення повзунка.
- **Screen Events:** Запуск скриптів, коли екран відкривається або закривається (наприклад, відтворення звуку під час появи меню).
- **Listeners:** Коли спрацьовує слухач, що слухає певну подію, він виконає свій скрипт дій.
- **Schedulers:** Виконання дій за розкладом, навіть коли жоден екран не відкрито.

# Використання заповнювачів у діях

Значення дій підтримують динамічний вміст через **заповнювачі**. Найчастіше ці заповнювачі використовують JSON-подібний синтаксис і замінюються актуальними даними під час виконання дії.

## Заповнювачі у JSON-подібному форматі

Це звичайні [заповнювачі](/en/placeholders), які можна використовувати в багатьох місцях у розкладках.

Вони мають такий синтаксис:

```json
{"placeholder": "placeholder_id", "values": {"key1": "value1", "key2": "value2"}}
```

Вони можуть отримувати ігрові дані, як-от ім’я гравця, розміри екрана або обчислені значення за допомогою заповнювача **Calculator**. Також можна вкладати заповнювачі для більш складних випадків.

## Заповнювачі `$$` (змінні)

Заповнювачі `$$` є спеціальними. Деякі функції FancyMenu надають ці спеціальні заповнювачі для вкладених дій, вимог і звичайних заповнювачів, щоб їх можна було використовувати всередині для отримання додаткової інформації про середовище (елемент, слухач тощо), у якому вони знаходяться.

Наприклад, якщо дії використовуються всередині повзунка, то `$$value` у дії буде замінено на поточне значення повзунка.

Під час використання дій у слухачах кожен слухач надаватиме власний унікальний набір змінних/заповнювачів для отримання додаткової інформації про слухача, наприклад натиснуту кнопку миші, введену структуру тощо.

# Як налаштувати та редагувати дії

Щоб додати, відредагувати або видалити дії (і блоки операторів) для елемента, просто **клацніть елемент правою кнопкою миші** (це може бути кнопка, повзунок, тікер або інший інтерактивний об’єкт), а потім виберіть **Manage Action Script**. Відкриється екран керування діями, де ви можете:

- **Add new actions or statements:** Додати нові записи дій або керувальні оператори (if, else-if, else, while) для побудови вашого скрипта.
- **Edit existing actions or statements:** Змінити значення дії або логіку керування.
- **Remove actions or statements:** Видалити небажані дії зі скрипта.

Для [listeners](/listeners) є спеціальне меню для керування та створення слухачів, зокрема для доступу до їхніх скриптів дій, щоб отримати той самий досвід, як під час редагування, наприклад, скрипта дій кнопки чи повзунка.

> У вікні редактора скриптів дій просто клацніть правою кнопкою миші по великій темно-сірій області, щоб відкрити контекстне меню для додавання дій, операторів та іншого.
{.is-info}


# Скорочення та інше в редакторі скриптів дій

Редактор скриптів дій має чудові функції для підвищення зручності, які роблять редагування скриптів надзвичайно простим.

## Скорочення

- `DEL` : Швидко видалити вибраний запис
- `ENTER` : Почати вбудоване редагування вибраного запису (або відкрити екран редагування, якщо для вибраного запису немає вбудованого редагування)
- `CTRL + C` : Скопіювати вибрану дію (поки що працює лише з діями)
- `CTRL + V` : Вставити раніше скопійовану дію
- `CTRL + Z` : Один крок назад (скасувати)
- `CTRL + Y` : Один крок уперед (повторити)
- `ARROW UP` : Перейти на один запис вище від поточного вибраного
- `ARROW DOWN` : Перейти на один запис нижче від поточного вибраного
- `SHIFT + ARROW UP` : Перемістити вибраний запис на одну позицію вгору
- `SHIFT + ARROW DOWN` : Перемістити вибраний запис на одну позицію вниз
- `A` : Швидко відкрити екран вибору дії, щоб додати нову дію
- `CTRL + S` : Готово/зберегти з вікна редактора

## Інші функції для зручності

- Подвійне клацання по значенню дії дає змогу редагувати значення без переходу до повного екрана редагування значення.
- Ланцюжки операторів IF (із доданими операторами ELSE/ELSE-IF), цикли WHILE і папки можна згортати (лише візуально, це не впливає на логіку скрипта).
- Редактор завжди додає нові дії нижче вибраного запису (або всередині вибраного ланцюжка/циклу/папки).
- Клацання правою кнопкою миші по темно-сірому фону області скрипта відкриває контекстне меню з опціями для додавання дій, операторів і всього іншого важливого.

# Дії детально

Цей список містить більшість, якщо не всі, дії, доступні у FancyMenu. Можливо, список інколи трохи застаріває через оновлення мода.

## Next Track (`audio_next_track`)
- **Description:** Перейти до наступної композиції в аудіоелементі
- **Value Required:** Yes - `audio_element_identifier` (ID аудіоелемента, яким потрібно керувати)

## Previous Track (`audio_previous_track`)
- **Description:** Перейти до попередньої композиції в аудіоелементі
- **Value Required:** Yes - `audio_element_identifier` (ID аудіоелемента, яким потрібно керувати)

## Set Track Volume (`set_audio_element_volume`)
- **Description:** Встановлює гучність аудіоелемента (0.0 to 1.0)
- **Value Required:** Yes - `element_identifier:volume`

## Toggle Play/Pause Track (`audio_toggle_play`)
- **Description:** Перемикає відтворення/паузу поточної композиції аудіоелемента
- **Value Required:** Yes - `audio_element_identifier`

## Play Audio (`play_audio`)
- **Description:** Відтворює аудіоресурс один раз. Дія відстежує запущене аудіо, щоб його можна було пізніше зупинити через `stop_all_action_audios`.
- **Value Required:** Yes - JSON-конфігурація з `audioSource`, `soundChannel` і `baseVolume`
- **Example Value:** `{"audioSource":"[source:local]/config/fancymenu/assets/example.ogg","soundChannel":"master","baseVolume":1.0}`

## Stop All Action Audios (`stop_all_action_audios`)
- **Description:** Зупиняє всі аудіодоріжки, запущені дією **Play Audio**. Це не зупиняє аудіоелементи, звуки відкриття/закриття меню, звуки кнопок або інші аудіосистеми.
- **Value Required:** No

## Set Video Element Volume (`set_video_element_volume`)
- **Description:** Встановлює гучність відеоелемента (0.0 to 1.0)
- **Value Required:** Yes - `video_element_identifier:volume`

## Set Video Element Play Time (`set_video_element_play_time`)
- **Description:** Перемотує відеоелемент до позначки часу в мілісекундах
- **Value Required:** Yes - `video_element_identifier:timestamp_ms`

## Toggle Video Element Paused State (`toggle_video_element_pause_state`)
- **Description:** Перемикає стан паузи відеоелемента
- **Value Required:** Yes - `video_element_identifier`

## Set Video Background Volume (`set_video_menu_background_volume`)
- **Description:** Встановлює гучність відеофону меню (0.0 to 1.0)
- **Value Required:** Yes - `background_identifier:volume`

> Щоб отримати ідентифікатор фону, клацніть правою кнопкою миші по фону редактора і виберіть 'Copy Background Identifier'.
{.is-info}

## Set Video Background Play Time (`set_video_menu_background_play_time`)
- **Description:** Перемотує відеофон меню до позначки часу в мілісекундах
- **Value Required:** Yes - `background_identifier:timestamp_ms`

> Щоб отримати ідентифікатор фону, клацніть правою кнопкою миші по фону редактора і виберіть 'Copy Background Identifier'.
{.is-info}

## Toggle Video Background Paused State (`toggle_video_menu_background_pause_state`)
- **Description:** Перемикає стан паузи відеофону меню
- **Value Required:** Yes - `background_identifier`

> Щоб отримати ідентифікатор фону, клацніть правою кнопкою миші по фону редактора і виберіть 'Copy Background Identifier'.
{.is-info}

## Toggle Layout (`toggle_layout`)
- **Description:** Перемикає розкладку (увімкнути/вимкнути) за її назвою
- **Value Required:** Yes - `layout_name`

## Enable Layout (`enable_layout`)
- **Description:** Увімкнути розкладку за її назвою
- **Value Required:** Yes - `layout_name`

## Disable Layout (`disable_layout`)
- **Description:** Вимкнути розкладку за її назвою
- **Value Required:** Yes - `layout_name`

## Open Screen or Custom GUI (`opengui`)
- **Description:** Відкриває екран за його ідентифікатором (vanilla, mod або custom GUI)
- **Value Required:** Yes - `screen_identifier`

> Ця дія **працює не для кожного екрана**, особливо для екранів модів. Якщо дія не зможе відкрити екран, буде показано помилку. У такому разі ви мало що можете зробити, бо, ймовірно, це занадто складний екран, який FancyMenu не може відкрити автоматично.
> 
> Підтримка екранів модів також більше не додаватиметься вручну з боку FancyMenu, оскільки додавання сумісності для всіх існуючих модів зайняло б надто багато часу, вибачте. У більшості випадків також не рекомендується звертатися до розробника іншого мода, оскільки якщо FancyMenu не може відкрити екран, то додати підтримку буде нелегко. Рекомендований обхідний шлях тут — спробувати використати дію **"Mimic Vanilla/Mod Button"**, щоб імітувати кнопку, яка відкриває потрібний екран. Якщо кнопки немає, то, на жаль, нічого не вийде.
{.is-info}

## Close Screen (`closegui`)
- **Description:** Закриває активний екран
- **Value Required:** No

## Update Screen (`update_screen`)
- **Description:** Повторно ініціалізує поточний екран
- **Value Required:** No

## Back to Last Screen (`back_to_last_screen`)
- **Description:** Повертається до попереднього екрана (того, що був перед поточним)
- **Value Required:** No

## Join Server (`joinserver`)
- **Description:** Підключає гравця до сервера Minecraft
- **Value Required:** Yes - `server_ip:port`

## Enter World (`loadworld`)
- **Description:** Заходить у світ Minecraft
- **Value Required:** Yes - `world_folder_name`

## Enter/Join Last World/Server (`join_last_world`)
- **Description:** Заходить/підключається до останнього світу або сервера, на якому перебував гравець
- **Value Required:** No

## Leave World or Server (`disconnect_server_or_world`)
- **Description:** Виходить зі світу або сервера та відкриває вказаний екран
- **Value Required:** Yes - `screen_identifier`

## Quit Minecraft (`quitgame`)
- **Description:** Повністю виходить із Minecraft
- **Value Required:** No

## Send Chat Message/Command (`sendmessage`)
- **Description:** Надсилає повідомлення в чат або виконує команду чату
- **Value Required:** Yes - `message_text` or `/command_text`

## Execute Command As Integrated Server (`execute_command_as_integrated_server`)
- **Description:** Примусово виконує команду в одиночній грі як інтегрований сервер, ігноруючи дозволи та налаштування читів.
- **Value Required:** Yes - Текст команди, наприклад `/give @p minecraft:diamond 1`

> Ця дія працює лише в одиночній грі, коли світ не відкрито для LAN. На багатокористувацьких серверах вона навмисно нічого не робить.
{.is-warning}

## Paste to Chat (`paste_to_chat`)
- **Description:** Вставляє текст у поле введення чату (додає або замінює)
- **Value Required:** Yes - `true:Text` or `false:Text`

## Display In Chat [Client-Side] (`display_in_chat_client_side`)
- **Description:** Виводить текст безпосередньо в локальний чат (без сервера)
- **Value Required:** Yes - `text_or_json`

## Send FM Data To Server (`send_fm_data_to_server`)
- **Description:** Надсилає користувацькі текстові дані на поточний сервер FancyMenu через канал пакетів FM Data.
- **Value Required:** Yes - `data_identifier||data`

## Connect To Remote Server (`connect_to_remote_server`)
- **Description:** Відкриває або повторно використовує ініційоване клієнтом WebSocket-з’єднання із зовнішнім віддаленим сервером.
- **Value Required:** Yes - URL віддаленого сервера, наприклад `wss://example.com/ws`

## Send Data To Remote Server (`send_data_to_remote_server`)
- **Description:** Відкриває або повторно використовує з’єднання з віддаленим сервером і надсилає йому текстові дані.
- **Value Required:** Yes - `remote_server_url||data`

## Close Remote Server Connection (`close_remote_server_connection`)
- **Description:** Закриває певне з’єднання з віддаленим сервером за ID запиту.
- **Value Required:** Yes - ID запиту, зазвичай із змінної слухача Remote Server, наприклад `$$request_id`

## Close All Remote Server Connections (`close_all_remote_server_connections`)
- **Description:** Закриває всі активні з’єднання з віддаленими серверами, відкриті FancyMenu.
- **Value Required:** No

## Open URL in Browser (`openlink`)
- **Description:** Відкриває посилання у браузері за замовчуванням
- **Value Required:** Yes - `https://example.com`

## Copy Text to Clipboard (`copytoclipboard`)
- **Description:** Копіює текст у буфер обміну
- **Value Required:** Yes - `text_to_copy`

## Print to Game Log (`print_to_log`)
- **Description:** Записує рядок у журнал гри
- **Value Required:** Yes - `text_to_log`

## Set Variable Value (FM Variable) (`set_variable`)
- **Description:** Зберігає текстовий вміст у змінній FancyMenu
- **Value Required:** Yes - `variable_name:variable_value`

## Clear All Variables (FM Variable) (`clear_variables`)
- **Description:** Очищує ВСІ збережені змінні FancyMenu
- **Value Required:** No

## Send HTTP Request (`send_http_request`)
- **Description:** Надсилає HTTP-запит; може зберігати відповідь у змінну
- **Value Required:** Yes - конфігурація HTTP-запиту

> Ця дія дає змогу надсилати дані до REST API, вебхуків або будь-якої HTTP-крапки призначення.
> Підтримує різні методи автентифікації, користувацькі заголовки та різні типи запитів.
> 
> Ця дія також дає змогу зберігати відповідь запиту в змінну FancyMenu для подальшого використання!
{.is-info}

## Manage Resource Pack (`manage_resource_pack`)
- **Description:** Увімкнути/вимкнути/перемкнути ресурс-пак за його назвою, що відображається (за потреби з перезавантаженням)
- **Value Required:** Yes - `pack_name|||MODE|||reload_bool`

## Reload Resource Packs (`reload_resource_packs`)
- **Description:** Перезавантажує ресурс-паки (cooldown 5 с)
- **Value Required:** No

## Reload FancyMenu (`reloadmenu`)
- **Description:** Перезавантажує FancyMenu, включно з панорамами, слайд-шоу та всіма ресурсами (важка операція)
- **Value Required:** No

> Ця дія має **великий вплив на продуктивність** і може спричиняти лаги, якщо використовувати її в тікерах. Не рекомендується використовувати цю дію ніде, окрім кнопки.
{.is-warning}

## Toggle Element Animator (`toggle_element_animator`)
- **Description:** Перемикає стан відтворення аніматора елемента
- **Value Required:** Yes - `animator_identifier`

## Enable Element Animator (`enable_element_animator`)
- **Description:** Увімкнути аніматор елемента
- **Value Required:** Yes - `animator_identifier`

## Disable Element Animator (`disable_element_animator`)
- **Description:** Вимкнути аніматор елемента
- **Value Required:** Yes - `animator_identifier`

## Reset Element Animator (`reset_element_animator`)
- **Description:** Скидає часову шкалу/стан аніматора елемента
- **Value Required:** Yes - `animator_identifier`

## Mimic Vanilla/Mod Button (`mimicbutton`)
- **Description:** Імітує натискання кнопки vanilla або мода
- **Value Required:** Yes - `screen_identifier:widget_locator`

## Mimic Keybind (`mimic_keybind`)
- **Description:** Виконує Minecraft-прив’язку клавіші (за потреби з утриманням)
- **Value Required:** Yes - `keybind_id|||keep_pressed_bool|||duration_ms`

## Set Text Input Field Value (`set_text_input_field_value`)
- **Description:** Встановлює значення користувацького або стандартного поля введення за ідентифікатором елемента.
- **Value Required:** Yes - `element_identifier|||new_value|||force_set_when_inactive`

## Create File in Game Directory (`create_file_in_game_dir`)
- **Description:** Створює порожній файл у каталозі гри (корінь інстансу). Приймає префікс `.minecraft/` для звернення до стандартного каталогу профілю лаунчера (може відрізнятися від поточного каталогу інстансу).
- **Value Required:** Yes - `file_path`

## Delete File/Folder in Game Directory (`delete_file_in_game_dir`)
- **Description:** Видаляє файл або папку в каталозі гри (корінь інстансу). Приймає префікс `.minecraft/` для звернення до стандартного профілю лаунчера (може відрізнятися від поточного інстансу). Додайте `*`, щоб видалити **всі файли безпосередньо всередині** папки (ігнорує підкаталоги; папка лишається).
- **Value Required:** Yes - `target_path`

## Copy File/Folder in Game Directory (`copy_file_in_game_dir`)
- **Description:** Копіює всередині каталогу гри (корінь інстансу); префікс `.minecraft/` вказує на стандартний профіль лаунчера (не завжди поточний інстанс). Додайте `*` до шляху **джерела**, щоб скопіювати кожен файл безпосередньо всередині цієї папки (ігнорує підкаталоги); призначення має бути каталогом і не може використовувати `*`.
- **Value Required:** Yes - `source||destination`

## Move File/Folder in Game Directory (`move_file_in_game_dir`)
- **Description:** Переміщує всередині каталогу гри (корінь інстансу); префікс `.minecraft/` вказує на стандартний профіль лаунчера (може відрізнятися від поточного інстансу). Додайте `*` до шляху **джерела**, щоб перемістити кожен файл безпосередньо всередині цієї папки (ігнорує підкаталоги); призначення має бути каталогом і не може використовувати `*`.
- **Value Required:** Yes - `source||destination`

## Rename File/Folder in Game Directory (`rename_file_in_game_dir`)
- **Description:** Перейменовує файл або папку всередині каталогу гри (корінь інстансу); префікс `.minecraft/` вказує на стандартний профіль лаунчера (може відрізнятися від поточного інстансу). Вміст лишається без змін, змінюється лише назва.
- **Value Required:** Yes - `path||new_name`

## Download File to Game Directory (`download_file_to_game_dir`)
- **Description:** Асинхронно завантажує файл у каталог гри (корінь інстансу); префікс `.minecraft/` вказує на стандартний профіль лаунчера (не обов’язково поточний інстанс). Вкажіть **цільову папку**; ім’я файлу визначається автоматично з заголовків/URL.
- **Value Required:** Yes - `url||target_folder`

## Extract ZIP File In Game Directory (`extract_zip_file_in_game_dir`)
- **Description:** Розпаковує ZIP-файл у цільову папку всередині каталогу гри або стандартного каталогу `.minecraft`. Після завершення запускає слухач **On ZIP Extracted via Action**.
- **Value Required:** Yes - `source_zip_path||target_folder_path`

## Open File/Folder In Game Directory (`open_file_folder_in_game_dir`)
- **Description:** Відкриває файл або папку стандартною програмою операційної системи. З міркувань безпеки ціль має залишатися всередині каталогу гри або стандартного каталогу `.minecraft`.
- **Value Required:** Yes - `target_path`

## Write File in Game Directory (`write_file_in_game_dir`)
- **Description:** Записує або додає текст усередині каталогу гри (корінь інстансу); префікс `.minecraft/` вказує на стандартний профіль лаунчера (може відрізнятися від цього інстансу). Створює файл, якщо його немає. Підтримує `\n` у значенні для вставлення переносів рядка; режим додавання керується фінальним логічним значенням.
- **Value Required:** Yes - `path|||content|||append_bool`

## Select File from System (`select_file_to_game_dir`)
- **Description:** Відкриває нативний вибір файлу (з будь-якого місця) і копіює вибраний файл у каталог гри (корінь інстансу) або в стандартний `.minecraft/`, якщо вказано префікс (цей стандартний шлях може відрізнятися від цього інстансу). Підтримує фільтри розширень, власну назву фільтра та необов’язкове перемикання перезапису.
- **Value Required:** Yes - конфігурація вибору

## Show Toast (`show_toast`)
- **Description:** Відображає налаштовуване спливаюче toast-сповіщення
- **Value Required:** Yes - конфігурація toast

## Start Scheduler (`start_scheduler`)
- **Description:** Запускає планувальник за його ID.
- **Value Required:** Yes - `scheduler_id`

## Stop Scheduler (`stop_scheduler`)
- **Description:** Зупиняє планувальник за його ID.
- **Value Required:** Yes - `scheduler_id`

## Set Minecraft Option (`edit_minecraft_option`)
- **Description:** Змінює параметр конфігурації Minecraft
- **Value Required:** Yes - `option_name:set_to_value`
