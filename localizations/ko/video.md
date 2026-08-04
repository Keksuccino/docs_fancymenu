---
title: 비디오 (MP4)
description: FancyMenu에서 비디오를 사용할 때 알아야 할 사항입니다.
---
# 비디오

FancyMenu는 MP4 비디오를 [요소](./elements#video), [메뉴 배경](./menu-backgrounds), 그리고 [게임 인트로](./game-intro) 콘텐츠로 재생할 수 있습니다.

기본 제공 [**비디오**](./elements#video) 요소와 **비디오** 메뉴 배경은 Watermedia V3를 사용합니다. 기존의 **Video [Rinku]** 타입은 더 이상 사용되지 않으며, 아직 필요한 레이아웃에만 남겨 두어야 합니다.

비디오 배경과 요소를 제어할 수 있는 다음 **액션**도 있습니다:

- [**비디오 요소 볼륨 설정**](./action-scripts#set-video-element-volume-set_video_element_volume)은 비디오 요소의 볼륨을 설정합니다.
- [**비디오 요소 재생 시간 설정**](./action-scripts#set-video-element-play-time-set_video_element_play_time)은 비디오 요소를 밀리초 타임스탬프로 이동합니다.
- [**비디오 요소 일시정지 상태 전환**](./action-scripts#toggle-video-element-paused-state-toggle_video_element_pause_state)은 비디오 요소의 일시정지 상태를 전환합니다.
- [**비디오 배경 볼륨 설정**](./action-scripts#set-video-background-volume-set_video_menu_background_volume)은 비디오 메뉴 배경의 볼륨을 설정합니다.
- [**비디오 배경 재생 시간 설정**](./action-scripts#set-video-background-play-time-set_video_menu_background_play_time)은 비디오 메뉴 배경을 밀리초 타임스탬프로 이동합니다.
- [**비디오 배경 일시정지 상태 전환**](./action-scripts#toggle-video-background-paused-state-toggle_video_menu_background_pause_state)은 비디오 메뉴 배경의 일시정지 상태를 전환합니다.

또한 비디오 배경과 요소에 대한 정보를 가져오는 다음 **플레이스홀더**도 있습니다:

- [**비디오 요소 볼륨**](./placeholders#video-element-volume-video_element_vol)은 비디오 요소의 볼륨을 반환합니다.
- [**비디오 요소 길이**](./placeholders#video-element-duration-video_element_duration)은 비디오 요소의 재생 길이를 반환합니다.
- [**비디오 요소 재생 시간**](./placeholders#video-element-play-time-video_element_playtime)은 비디오 요소의 현재 진행 시간을 반환합니다.
- [**비디오 요소 일시정지 상태**](./placeholders#video-element-paused-state-video_element_paused_state)은 비디오 요소가 일시정지되어 있는지 반환합니다.
- [**비디오 배경 볼륨**](./placeholders#video-background-volume-video_background_vol)은 비디오 메뉴 배경의 볼륨을 반환합니다.
- [**비디오 배경 길이**](./placeholders#video-background-duration-video_background_duration)은 비디오 메뉴 배경의 재생 길이를 반환합니다.
- [**비디오 배경 재생 시간**](./placeholders#video-background-play-time-video_background_playtime)은 비디오 메뉴 배경의 현재 진행 시간을 반환합니다.
- [**비디오 배경 일시정지 상태**](./placeholders#video-background-paused-state-video_background_paused_state)은 비디오 메뉴 배경이 일시정지되어 있는지 반환합니다.

길이 및 재생 시간 플레이스홀더는 기본적으로 `MM:SS` 형식으로 반환됩니다. 밀리초 타임스탬프가 필요하면 `output_as_timestamp`를 `true`로 설정하세요. 재생 시간 플레이스홀더는 0-100 진행률 값에 대해 `show_percentage`를 계속 사용할 수 있습니다.

볼륨 및 일시정지 상태 값은 식별자에 연결된 컨트롤러 메타데이터입니다. 길이 및 재생 시간 값은 현재 화면에서 일치하는 비디오 요소 또는 배경이 활성화되어 있고 준비되어 있어야 합니다.

[**비디오 재생 상태 변경 시**](./listeners#on-video-playback-status-changed-video_playback_status_changed) 리스너는 `PLAYING`, `PAUSED`, `STOPPED`, `FINISHED`에 반응할 수 있습니다.

## 요구 사항

새로운 기본 비디오 요소와 메뉴 배경 유형을 사용하려면 다음을 설치해야 합니다:

- **Watermedia V3**
- **Watermedia Binaries V3**

이들은 선택적 종속성입니다. 따라서 비디오 지원을 사용하려면 인스턴스에 수동으로 추가해야 합니다.

기본 비디오 재생에는 OpenGL 렌더러도 필요합니다. Minecraft가 Vulkan을 사용하는 동안에는 Watermedia 재생을 사용할 수 없으며, Video 요소, Video 메뉴 배경, 그리고 [비디오 게임 인트로](./game-intro)를 사용하려면 OpenGL로 전환해야 합니다.

더 이상 사용되지 않는 **Video [Rinku]** 타입은 여전히 [Rinku](https://modrinth.com/mod/rinku)를 사용합니다. 새 레이아웃에서는 대신 Watermedia 기반의 기본 Video 타입을 사용하세요.

## 로딩 화면의 비디오

비디오 지원은 로딩 화면(게임/리소스 로딩 화면 및 월드 로딩 화면)에서 작동하지 않습니다.

즉, 대부분의 경우 작동하지 않으므로 **Drippy Loading Screen**을 통해 게임 로딩 화면에 비디오를 추가해서는 안 됩니다.

대신 로딩 화면에서는 짧고 단순한 [AFMA/FMA 애니메이션](./fma)을 사용하세요.

## 문제 해결

기본 비디오가 재생되지 않으면 Watermedia V3와 Watermedia Binaries V3가 Minecraft/modloader 버전과 일치하는지, 그리고 Minecraft가 Vulkan 대신 OpenGL을 사용하고 있는지 확인하세요.
