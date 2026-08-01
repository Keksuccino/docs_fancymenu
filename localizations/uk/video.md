---
title: Відео (MP4)
description: Що потрібно знати про використання відео у FancyMenu.
---
# Відео

FancyMenu підтримує відтворення MP4-відео як [елементів](./elements#video), [фонових зображень меню](./menu-backgrounds) та вмісту [Game Intro](./game-intro).

Вбудований [**Video** елемент](./elements#video) і фонове зображення меню **Video** використовують Watermedia V3. Старі типи **Video [MCEF]** застарілі й мають залишатися лише в макетах, які все ще потребують їх.

Також доступні такі **дії** для керування фоновими відео та елементами:

- [**Set Video Element Volume**](./action-scripts#set-video-element-volume-set_video_element_volume) встановлює гучність Video-елемента.
- [**Set Video Element Play Time**](./action-scripts#set-video-element-play-time-set_video_element_play_time) перемотує Video-елемент до позначки часу в мілісекундах.
- [**Toggle Video Element Paused State**](./action-scripts#toggle-video-element-paused-state-toggle_video_element_pause_state) перемикає стан паузи Video-елемента.
- [**Set Video Background Volume**](./action-scripts#set-video-background-volume-set_video_menu_background_volume) встановлює гучність фонового відео меню.
- [**Set Video Background Play Time**](./action-scripts#set-video-background-play-time-set_video_menu_background_play_time) перемотує фонове відео меню до позначки часу в мілісекундах.
- [**Toggle Video Background Paused State**](./action-scripts#toggle-video-background-paused-state-toggle_video_menu_background_pause_state) перемикає стан паузи фонового відео меню.

І такі **плейсхолдери** для отримання інформації про фонові відео та елементи:

- [**Video Element Volume**](./placeholders#video-element-volume-video_element_vol) повертає гучність Video-елемента.
- [**Video Element Duration**](./placeholders#video-element-duration-video_element_duration) повертає тривалість Video-елемента.
- [**Video Element Play Time**](./placeholders#video-element-play-time-video_element_playtime) повертає поточний прогрес Video-елемента.
- [**Video Element Paused State**](./placeholders#video-element-paused-state-video_element_paused_state) повертає, чи Video-елемент поставлено на паузу.
- [**Video Background Volume**](./placeholders#video-background-volume-video_background_vol) повертає гучність фонового відео меню.
- [**Video Background Duration**](./placeholders#video-background-duration-video_background_duration) повертає тривалість фонового відео меню.
- [**Video Background Play Time**](./placeholders#video-background-play-time-video_background_playtime) повертає поточний прогрес фонового відео меню.
- [**Video Background Paused State**](./placeholders#video-background-paused-state-video_background_paused_state) повертає, чи фонове відео меню поставлено на паузу.

Плейсхолдери тривалості та часу відтворення за замовчуванням повертають `MM:SS`. Встановіть `output_as_timestamp` у `true`, якщо вам потрібні позначки часу в мілісекундах. Плейсхолдери часу відтворення все ще можуть використовувати `show_percentage` для значень прогресу від 0 до 100.

Значення гучності та стану паузи — це метадані контролера, пов’язані з ідентифікатором. Значення тривалості та часу відтворення вимагають, щоб відповідний Video-елемент або фон був активним і готовим на поточному екрані.

[**On Video Playback Status Changed** listener](./listeners#on-video-playback-status-changed-video_playback_status_changed) може реагувати на `PLAYING`, `PAUSED`, `STOPPED` і `FINISHED`.

## Вимоги

Щоб використовувати новий вбудований тип Video-елемента та фону меню, потрібно встановити:

- **Watermedia V3**
- **Watermedia Binaries V3**

Це необов’язкові залежності, тому їх потрібно додати до інстансу вручну, якщо вам потрібна підтримка відео.

Вбудоване відтворення відео також вимагає рендерера OpenGL. Відтворення Watermedia недоступне, коли Minecraft використовує Vulkan; перемкніться на OpenGL, щоб використовувати Video-елементи, фонові відео меню та [відео Game Intro](./game-intro).

Застарілий тип **Video [MCEF]** усе ще використовує MCEF. Для нових макетів використовуйте натомість вбудований тип Video на базі Watermedia.

## Відео на екранах завантаження

Підтримка відео НЕ працює на екранах завантаження (екран завантаження гри/ресурсів і екран завантаження світу).

Це також означає, що вам НЕ слід додавати відео на екран завантаження гри через **Drippy Loading Screen**, оскільки в більшості випадків це не працюватиме.

Натомість використовуйте короткі прості [AFMA/FMA анімації](./fma) на екранах завантаження.

## Усунення несправностей

Якщо вбудоване відео не відтворюється, переконайтеся, що Watermedia V3 і Watermedia Binaries V3 відповідають вашій версії Minecraft/modloader і що Minecraft використовує OpenGL, а не Vulkan.
