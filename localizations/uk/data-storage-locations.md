---
title: Місця зберігання даних
description: >-
  Де FancyMenu зберігає макети, ресурси, налаштування та інші дані, а також які
  файли належать до профілів.
sourceBlobSha: 30dd81ed90e08184e3063892870e3325d7d7c5cb
---

# Місця зберігання даних

FancyMenu зберігає всі дані у двох папках каталогу гри. Це папка екземпляра у вашому лаунчері, яка може відрізнятися від `.minecraft`.

- `config/fancymenu/` містить ваші налаштування: макети, ресурси, змінні та інше. Це папка завантаженого [профілю](/profiles), тому модпаки містять цю папку.
- `fancymenu_data/` містить дані цього екземпляра гри, наприклад позиції Dragger та завантаження. Ця папка спільна для всіх профілів.

**Рядок меню -> Інструменти -> Відкрити каталог FancyMenu** відкриває `config/fancymenu/`.

Більшість файлів і папок з'являються лише після використання відповідної функції. Перш ніж змінювати або видаляти файли в них, закрийте гру.

> [!TIP]
> Щоб спільно використовувати ці папки між екземплярами, перемістіть їх в інше місце, а на їхньому місці створіть символічне посилання (у Windows — точку з'єднання).

# Ваші налаштування

Усе міститься в `<game-directory>/config/fancymenu/`. Ці дані належать завантаженому [профілю](/profiles).

| Що | Де |
| --- | --- |
| Макети у файлах `.txt`, зокрема в підпапках | `customization/` |
| [Локальні ресурси](/resources#local-resources), як-от зображення та звуки | `assets/` |
| Налаштування FancyMenu | `options.txt` |
| Екрани, для яких увімкнено **Налаштування поточного екрана** | `customizablemenus.txt` |
| [Власні GUI](/custom-guis) і екрани, які вони замінюють | `custom_gui_screens.txt` |
| [Змінні](/variables) | `user_variables.db` |
| [Слухачі](/listeners) | `listener_instances.txt` |
| [Планувальники](/schedulers) | `scheduler_instances.txt` |
| [Панорами](/panoramas) | `panoramas/` |
| [Слайд-шоу](/slideshows) | `slideshows/` |
| [Власні локалізації](/localization#fancymenu-custom-localization-files) | `custom_locals/` |
| Теми власного інтерфейсу FancyMenu (**Рядок меню -> Налаштування зовнішнього вигляду -> Налаштування -> Інтерфейс FancyMenu -> Тема інтерфейсу**) | `ui_themes/` |
| Стани [прапорців](/elements#checkbox), які не використовують змінну | `checkbox_states.json` |
| Гучність і стан паузи, задані діями для [відеоелементів](/video) | `video_element_controller_metas.json` |
| Гучність, задана діями для [аудіоелементів](/elements#audio) | `audio_element_controller_metas.json` |
| Стан увімкнення та вимкнення, заданий діями для [аніматорів елементів](/element-animator) | `animation_controller_states.json` |
| Екрани, для яких увімкнено **Відкривати вміст області прокручування поточного екрана** (див. [Налаштування екранів із прокручуванням](/customizing-scrollable-screens)) | `normalized_scroll_screens.json` |
| Серверні слухачі [FM Data](/fm-data) | `fmdata_server_listeners.json` |
| Привітальні дані [FM Data](/fm-data) | `fmdata_welcome_data.json` |
| Позиція, розмір і видимість віджетів редактора макетів | `layout_editor/widgets/` |
| Назва, піктограма й відомості про завантажений профіль | `profile.json` і `profile_icon.png` |
| Усі інші [профілі](/profiles#where-profiles-are-stored) | `profiles/` |
| Інформація про вже виконані FancyMenu оновлення застарілих файлів | `legacy_checklist.txt` |

`customizablemenus.txt` містить назви екранів у вигляді імен їхніх Java-класів. Короткі [ідентифікатори екранів](/screen-identifiers), як-от `title_screen`, до цього списку не додаються.

На виділеному сервері FancyMenu використовує лише два файли [FM Data](/fm-data) у папці `config/fancymenu/` сервера.

# Дані екземпляра

Усе міститься в `<game-directory>/fancymenu_data/`. Ця папка не входить до складу профілів, тому її вміст зберігається під час перемикання між ними.

| Що | Де |
| --- | --- |
| Позиції [елементів Dragger](/dragger) | `dragger_metas.json` |
| Останній світ або сервер для дії **Увійти до останнього світу/сервера** та заповнювача **Останній світ або сервер** | `last_world.fmdata` |
| Знімки екрана для [безшовного завантаження світу](/seamless-world-loading) | `seamless_world_loading/` |
| Збереження [Buddy](/decoration-overlays#buddy), два файли для кожного накладання Buddy | `buddy/` |
| Файли [експорту для ШІ](/export-for-ai) | `ai_exports/` |
| Ваші улюблені дії у вікні вибору дій | `action_favorites.json` |
| Гучність попереднього прослуховування аудіо та відео у вікнах вибору файлів | `browser_audio_settings.json` і `browser_video_settings.json` |
| Кадр, який показує [відеофон](/video) під час паузи | `video_thumbnails/` |
| FFmpeg, який FancyMenu завантажує для [творця AFMA](/animations#fma-and-afma) | `ffmpeg_cache/` |
| Позначка про те, що FancyMenu вже встановив [**Типовий масштаб GUI**](/global-customizations) | `default_scale_set.fm` |
| Тимчасові файли, які видаляються під час кожного запуску гри | `fancymenu_temp/` |

- FancyMenu встановлює **Типовий масштаб GUI** лише один раз. Видаліть `default_scale_set.fm`, щоб під час наступного запуску масштаб було встановлено знову.
- На знімках екрана для безшовного завантаження світу видно все, що було на екрані у світі. Якщо не хочете їх зберігати, видаліть їх, коли гру закрито.

# Файли старих версій

Старіші версії FancyMenu зберігали деякі файли в інших місцях. Під час наступного запуску гри FancyMenu перенесе їх:

- `checkbox_states.json` і `normalized_scroll_screens.json` — із самого каталогу гри до `config/fancymenu/`.
- `dragger_metas.json` — із `config/fancymenu/` до `fancymenu_data/`.
