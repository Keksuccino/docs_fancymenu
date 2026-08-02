---
title: 동영상 (MP4)
description: FancyMenu에서 동영상을 사용할 때 알아야 할 내용입니다.
---
# 동영상

FancyMenu는 MP4 동영상을 [요소](./elements#video), [메뉴 배경](./menu-backgrounds), [게임 인트로](./game-intro) 콘텐츠로 재생할 수 있습니다.

기본 제공 [**동영상**](./elements#video) 요소와 **동영상** 메뉴 배경은 Watermedia V3를 사용합니다. 기존의 **Video [MCEF]** 유형은 더 이상 권장되지 않으며, 아직 필요한 레이아웃에만 남겨 두어야 합니다.

동영상 배경과 요소를 제어하는 다음 **액션**도 있습니다:

- [**동영상 요소 볼륨 설정**](./action-scripts#set-video-element-volume-set_video_element_volume)은 동영상 요소의 볼륨을 설정합니다.
- [**동영상 요소 재생 시간 설정**](./action-scripts#set-video-element-play-time-set_video_element_play_time)은 동영상 요소를 밀리초 타임스탬프로 이동합니다.
- [**동영상 요소 일시정지 상태 전환**](./action-scripts#toggle-video-element-paused-state-toggle_video_element_pause_state)은 동영상 요소의 일시정지 상태를 전환합니다.
- [**동영상 배경 볼륨 설정**](./action-scripts#set-video-background-volume-set_video_menu_background_volume)은 동영상 메뉴 배경의 볼륨을 설정합니다.
- [**동영상 배경 재생 시간 설정**](./action-scripts#set-video-background-play-time-set_video_menu_background_play_time)은 동영상 메뉴 배경을 밀리초 타임스탬프로 이동합니다.
- [**동영상 배경 일시정지 상태 전환**](./action-scripts#toggle-video-background-paused-state-toggle_video_menu_background_pause_state)은 동영상 메뉴 배경의 일시정지 상태를 전환합니다.

또한 동영상 배경과 요소에 대한 정보를 가져오는 다음 **플레이스홀더**가 있습니다:

- [**동영상 요소 볼륨**](./placeholders#video-element-volume-video_element_vol)은 동영상 요소의 볼륨을 반환합니다.
- [**동영상 요소 재생 시간**](./placeholders#video-element-duration-video_element_duration)은 동영상 요소의 재생 시간을 반환합니다.
- [**동영상 요소 재생 시각**](./placeholders#video-element-play-time-video_element_playtime)은 동영상 요소의 현재 진행 시간을 반환합니다.
- [**동영상 요소 일시정지 상태**](./placeholders#video-element-paused-state-video_element_paused_state)은 동영상 요소가 일시정지되어 있는지 반환합니다.
- [**동영상 배경 볼륨**](./placeholders#video-background-volume-video_background_vol)은 동영상 메뉴 배경의 볼륨을 반환합니다.
- [**동영상 배경 재생 시간**](./placeholders#video-background-duration-video_background_duration)은 동영상 메뉴 배경의 재생 시간을 반환합니다.
- [**동영상 배경 재생 시각**](./placeholders#video-background-play-time-video_background_playtime)은 동영상 메뉴 배경의 현재 진행 시간을 반환합니다.
- [**동영상 배경 일시정지 상태**](./placeholders#video-background-paused-state-video_background_paused_state)은 동영상 메뉴 배경이 일시정지되어 있는지 반환합니다.

재생 시간과 진행 시간 플레이스홀더는 기본적으로 `MM:SS` 형식으로 반환됩니다. 밀리초 타임스탬프가 필요하면 `output_as_timestamp`를 `true`로 설정하세요. 진행 시간 플레이스홀더는 0~100 진행률 값을 위해 `show_percentage`를 계속 사용할 수 있습니다.

볼륨과 일시정지 상태 값은 해당 식별자와 연결된 컨트롤러 메타데이터입니다. 재생 시간과 진행 시간 값은 현재 화면에서 일치하는 동영상 요소 또는 배경이 활성화되어 있고 준비된 상태여야 합니다.

[**On Video Playback Status Changed** 리스너](./listeners#on-video-playback-status-changed-video_playback_status_changed)는 `PLAYING`, `PAUSED`, `STOPPED`, `FINISHED` 상태에 반응할 수 있습니다.

## 요구 사항

새로운 기본 제공 동영상 요소와 메뉴 배경 유형을 사용하려면 다음을 설치해야 합니다:

- **Watermedia V3**
- **Watermedia Binaries V3**

이들은 선택적 의존성이므로, 동영상 지원을 원할 경우 인스턴스에 수동으로 추가해야 합니다.

기본 동영상 재생에는 OpenGL 렌더러도 필요합니다. Minecraft가 Vulkan을 사용하는 동안에는 Watermedia 재생을 사용할 수 없습니다. 동영상 요소, 동영상 메뉴 배경, 그리고 [동영상 게임 인트로](./game-intro)를 사용하려면 OpenGL로 전환하세요.

더 이상 권장되지 않는 **Video [MCEF]** 유형은 계속 MCEF를 사용합니다. 새 레이아웃에서는 대신 Watermedia 기반의 기본 동영상 유형을 사용하세요.

## 로딩 화면의 동영상

동영상 지원은 로딩 화면(게임/리소스 로딩 화면 및 월드 로딩 화면)에서 작동하지 않습니다.

따라서 **Drippy Loading Screen**을 통해 게임 로딩 화면에 동영상을 추가하는 것도 **해당되지 않아야 하며**, 대부분의 경우 작동하지 않습니다.

대신 로딩 화면에는 짧고 단순한 [AFMA/FMA 애니메이션](./fma)을 사용하세요.

## 문제 해결

기본 동영상이 재생되지 않으면 Watermedia V3와 Watermedia Binaries V3가 Minecraft/모드로더 버전과 일치하는지, 그리고 Minecraft가 Vulkan 대신 OpenGL을 사용 중인지 확인하세요.
