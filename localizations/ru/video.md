---
title: Видео (MP4)
description: Что нужно знать об использовании видео в FancyMenu.
---
# Видео

FancyMenu поддерживает воспроизведение MP4-видео в качестве [элементов](./elements#video), [фонов меню](./menu-backgrounds) и содержимого [Game Intro](./game-intro).

Нативный [элемент **Video**](./elements#video) и фон меню **Video** используют Watermedia V3. Старые типы **Video [Rinku]** устарели и должны оставаться только в тех макетах, где они всё ещё нужны.

Также доступны следующие **действия** для управления фонами и элементами видео:

- [**Set Video Element Volume**](./action-scripts#set-video-element-volume-set_video_element_volume) задаёт громкость элемента Video.
- [**Set Video Element Play Time**](./action-scripts#set-video-element-play-time-set_video_element_play_time) перемещает элемент Video к отметке времени в миллисекундах.
- [**Toggle Video Element Paused State**](./action-scripts#toggle-video-element-paused-state-toggle_video_element_pause_state) переключает состояние паузы элемента Video.
- [**Set Video Background Volume**](./action-scripts#set-video-background-volume-set_video_menu_background_volume) задаёт громкость фона меню Video.
- [**Set Video Background Play Time**](./action-scripts#set-video-background-play-time-set_video_menu_background_play_time) перемещает фон меню Video к отметке времени в миллисекундах.
- [**Toggle Video Background Paused State**](./action-scripts#toggle-video-background-paused-state-toggle_video_menu_background_pause_state) переключает состояние паузы фона меню Video.

И следующие **плейсхолдеры** для получения информации о видеофонах и видеоэлементах:

- [**Video Element Volume**](./placeholders#video-element-volume-video_element_vol) возвращает громкость элемента Video.
- [**Video Element Duration**](./placeholders#video-element-duration-video_element_duration) возвращает длительность элемента Video.
- [**Video Element Play Time**](./placeholders#video-element-play-time-video_element_playtime) возвращает текущий прогресс элемента Video.
- [**Video Element Paused State**](./placeholders#video-element-paused-state-video_element_paused_state) возвращает, поставлен ли элемент Video на паузу.
- [**Video Background Volume**](./placeholders#video-background-volume-video_background_vol) возвращает громкость фона меню Video.
- [**Video Background Duration**](./placeholders#video-background-duration-video_background_duration) возвращает длительность фона меню Video.
- [**Video Background Play Time**](./placeholders#video-background-play-time-video_background_playtime) возвращает текущий прогресс фона меню Video.
- [**Video Background Paused State**](./placeholders#video-background-paused-state-video_background_paused_state) возвращает, поставлен ли фон меню Video на паузу.

Плейсхолдеры длительности и времени воспроизведения по умолчанию возвращают `MM:SS`. Установите `output_as_timestamp` в `true`, когда вам нужны отметки времени в миллисекундах. Плейсхолдеры времени воспроизведения по-прежнему могут использовать `show_percentage` для значений прогресса от 0 до 100.

Значения громкости и состояния паузы являются метаданными контроллера, связанными с идентификатором. Значения длительности и времени воспроизведения требуют, чтобы соответствующий элемент Video или фон были активны и готовы на текущем экране.

Слушатель [**On Video Playback Status Changed**](./listeners#on-video-playback-status-changed-video_playback_status_changed) может реагировать на `PLAYING`, `PAUSED`, `STOPPED` и `FINISHED`.

## Требования

Чтобы использовать новый нативный элемент Video и тип фона меню, необходимо установить:

- **Watermedia V3**
- **Watermedia Binaries V3**

Это необязательные зависимости, поэтому их нужно добавлять в экземпляр вручную, если вам нужна поддержка видео.

Для нативного воспроизведения видео также требуется рендерер OpenGL. Воспроизведение Watermedia недоступно, пока Minecraft использует Vulkan; переключитесь на OpenGL, чтобы использовать элементы Video, фоны меню Video и [видео Game Intros](./game-intro).

Устаревший тип **Video [Rinku]** по-прежнему использует [Rinku](https://modrinth.com/mod/rinku). Для новых макетов используйте вместо него нативный тип Video на базе Watermedia.

## Видео на экранах загрузки

Поддержка видео НЕ работает на экранах загрузки (экран загрузки игры/ресурсов и экран загрузки мира).

Это также означает, что НЕ следует добавлять видео на экран загрузки игры через **Drippy Loading Screen**, так как в большинстве случаев это не будет работать.

Вместо этого используйте короткие и простые анимации [AFMA/FMA](./fma) на экранах загрузки.

## Устранение неполадок

Если нативное видео не воспроизводится, убедитесь, что Watermedia V3 и Watermedia Binaries V3 соответствуют вашей версии Minecraft/загрузчика модов и что Minecraft использует OpenGL вместо Vulkan.
