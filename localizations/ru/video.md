---
title: Видео (MP4)
description: Что нужно знать об использовании видео в FancyMenu.
---
# Видео

FancyMenu поддерживает воспроизведение MP4-видео как [элементов](./elements#video), [фонов меню](./menu-backgrounds) и контента [Game Intro](./game-intro).

Нативный [**Video**-элемент](./elements#video) и фон меню **Video** используют Watermedia V3. Старые типы **Video [MCEF]** устарели и должны оставаться только в тех макетах, которым они всё ещё нужны.

Также доступны следующие **действия** для управления фоновыми видео и видеоэлементами:

- [**Set Video Element Volume**](./action-scripts#set-video-element-volume-set_video_element_volume) задаёт громкость Video-элемента.
- [**Set Video Element Play Time**](./action-scripts#set-video-element-play-time-set_video_element_play_time) перемещает Video-элемент к указанной временной метке в миллисекундах.
- [**Toggle Video Element Paused State**](./action-scripts#toggle-video-element-paused-state-toggle_video_element_pause_state) переключает состояние паузы Video-элемента.
- [**Set Video Background Volume**](./action-scripts#set-video-background-volume-set_video_menu_background_volume) задаёт громкость фона меню Video.
- [**Set Video Background Play Time**](./action-scripts#set-video-background-play-time-set_video_menu_background_play_time) перемещает фон меню Video к указанной временной метке в миллисекундах.
- [**Toggle Video Background Paused State**](./action-scripts#toggle-video-background-paused-state-toggle_video_menu_background_pause_state) переключает состояние паузы фона меню Video.

И следующие **плейсхолдеры** для получения информации о фоновых видео и элементах:

- [**Video Element Volume**](./placeholders#video-element-volume-video_element_vol) возвращает громкость Video-элемента.
- [**Video Element Duration**](./placeholders#video-element-duration-video_element_duration) возвращает длительность Video-элемента.
- [**Video Element Play Time**](./placeholders#video-element-play-time-video_element_playtime) возвращает текущий прогресс Video-элемента.
- [**Video Element Paused State**](./placeholders#video-element-paused-state-video_element_paused_state) возвращает, находится ли Video-элемент на паузе.
- [**Video Background Volume**](./placeholders#video-background-volume-video_background_vol) возвращает громкость фона меню Video.
- [**Video Background Duration**](./placeholders#video-background-duration-video_background_duration) возвращает длительность фона меню Video.
- [**Video Background Play Time**](./placeholders#video-background-play-time-video_background_playtime) возвращает текущий прогресс фона меню Video.
- [**Video Background Paused State**](./placeholders#video-background-paused-state-video_background_paused_state) возвращает, находится ли фон меню Video на паузе.

Плейсхолдеры длительности и времени воспроизведения по умолчанию возвращают значение в формате `MM:SS`. Установите `output_as_timestamp` в `true`, если вам нужны временные метки в миллисекундах. Плейсхолдеры времени воспроизведения по-прежнему могут использовать `show_percentage` для значений прогресса от 0 до 100.

Значения громкости и состояния паузы — это метаданные контроллера, связанные с идентификатором. Значения длительности и времени воспроизведения требуют, чтобы соответствующий Video-элемент или фон были активны и готовы на текущем экране.

[**On Video Playback Status Changed** listener](./listeners#on-video-playback-status-changed-video_playback_status_changed) может реагировать на `PLAYING`, `PAUSED`, `STOPPED` и `FINISHED`.

## Требования

Чтобы использовать новый нативный Video-элемент и тип фона меню, необходимо установить:

- **Watermedia V3**
- **Watermedia Binaries V3**

Это необязательные зависимости, поэтому их нужно добавлять в экземпляр вручную, если вам нужна поддержка видео.

Нативное воспроизведение видео также требует OpenGL-рендерер. Воспроизведение через Watermedia недоступно, пока Minecraft использует Vulkan; переключитесь на OpenGL, чтобы использовать Video-элементы, фоны меню Video и [Game Intro с видео](./game-intro).

Устаревший тип **Video [MCEF]** по-прежнему использует MCEF. Для новых макетов используйте вместо него нативный Video-тип на базе Watermedia.

## Видео на экранах загрузки

Поддержка видео НЕ работает на экранах загрузки (экран загрузки игры/ресурсов и экран загрузки мира).

Это также означает, что НЕ следует добавлять видео на экран загрузки игры через **Drippy Loading Screen**, поскольку в большинстве случаев это не будет работать.

Вместо этого используйте короткие и простые [AFMA/FMA-анимации](./fma) на экранах загрузки.

## Устранение неполадок

Если нативное видео не воспроизводится, убедитесь, что Watermedia V3 и Watermedia Binaries V3 соответствуют вашей версии Minecraft/модлоадера, и что Minecraft использует OpenGL вместо Vulkan.
