---
title: 비디오 (MP4)
description: FancyMenu에서 비디오를 사용할 때 알아야 할 사항입니다.
sourceBlobSha: bd34c5c21a6c08d6b66a7b2acdaf9bd12739732f
---
# 비디오

FancyMenu는 MP4 비디오를 [요소](/elements#video), [메뉴 배경](/menu-backgrounds#video), [게임 인트로](/game-intro) 콘텐츠로 재생할 수 있습니다.

기본 제공 [**비디오** 요소](/elements#video)와 **비디오** 메뉴 배경은 Watermedia V3를 사용합니다. 이전의 **비디오 [Rinku]** 유형은 더 이상 사용되지 않으므로, 계속 필요한 레이아웃에서만 사용해야 합니다.

비디오 배경과 요소를 제어하는 다음 [액션](/action-scripts)도 사용할 수 있습니다.

- [**비디오 요소 볼륨 설정**](/action-scripts#set-video-element-volume)은 비디오 요소의 볼륨을 설정합니다.
- [**비디오 요소 재생 시간 설정**](/action-scripts#set-video-element-play-time)은 비디오 요소를 지정한 밀리초 시점으로 이동합니다.
- [**비디오 요소 일시 정지 상태 전환**](/action-scripts#toggle-video-element-paused-state)은 비디오 요소의 일시 정지 상태를 전환합니다.
- [**비디오 배경 볼륨 설정**](/action-scripts#set-video-background-volume)은 비디오 메뉴 배경의 볼륨을 설정합니다.
- [**비디오 배경 재생 시간 설정**](/action-scripts#set-video-background-play-time)은 비디오 메뉴 배경을 지정한 밀리초 시점으로 이동합니다.
- [**비디오 배경 일시 정지 상태 전환**](/action-scripts#toggle-video-background-paused-state)은 비디오 메뉴 배경의 일시 정지 상태를 전환합니다.

비디오 배경과 요소에 관한 정보를 가져오는 다음 [플레이스홀더](/placeholders)도 사용할 수 있습니다.

- [**비디오 요소 볼륨**](/placeholders#video-element-volume)은 비디오 요소의 볼륨을 반환합니다.
- [**비디오 요소 재생 시간**](/placeholders#video-element-duration)은 비디오 요소의 재생 시간을 반환합니다.
- [**비디오 요소 재생 위치**](/placeholders#video-element-play-time)은 비디오 요소의 현재 재생 진행 상황을 반환합니다.
- [**비디오 요소 일시 정지 상태**](/placeholders#video-element-paused-state)는 비디오 요소가 일시 정지되었는지 반환합니다.
- [**비디오 배경 볼륨**](/placeholders#video-background-volume)은 비디오 메뉴 배경의 볼륨을 반환합니다.
- [**비디오 배경 재생 시간**](/placeholders#video-background-duration)은 비디오 메뉴 배경의 재생 시간을 반환합니다.
- [**비디오 배경 재생 위치**](/placeholders#video-background-play-time)은 비디오 메뉴 배경의 현재 재생 진행 상황을 반환합니다.
- [**비디오 배경 일시 정지 상태**](/placeholders#video-background-paused-state)는 비디오 메뉴 배경이 일시 정지되었는지 반환합니다.

재생 시간 및 재생 위치 플레이스홀더는 기본적으로 `MM:SS` 형식의 값을 반환합니다. 밀리초 단위 타임스탬프가 필요하면 `output_as_timestamp`를 `true`로 설정하세요. 재생 위치 플레이스홀더에서는 `show_percentage`를 사용해 0~100의 진행률 값을 표시할 수도 있습니다.

볼륨 및 일시 정지 상태 값은 식별자와 연결된 컨트롤러 메타데이터입니다. 재생 시간 및 재생 위치 값을 가져오려면 현재 화면에서 해당 비디오 요소나 배경이 활성화되어 재생 준비를 마쳐야 합니다.

[**비디오 재생 상태 변경** 리스너](/listeners#video-playback-status-changed)는 `PLAYING`, `PAUSED`, `STOPPED`, `FINISHED` 상태에 반응할 수 있습니다.

## 요구 사항

새로운 기본 제공 비디오 요소와 메뉴 배경 유형을 사용하려면 다음을 설치해야 합니다.

- **Watermedia V3**
- **Watermedia Binaries V3**

이들은 선택적 종속성이므로 비디오를 지원하려면 인스턴스에 직접 추가해야 합니다.

기본 비디오 재생에는 OpenGL 렌더러도 필요합니다. Minecraft가 Vulkan을 사용하는 동안에는 Watermedia로 재생할 수 없습니다. 비디오 요소, 비디오 메뉴 배경, [비디오 게임 인트로](/game-intro)를 사용하려면 OpenGL로 전환하세요.

더 이상 사용되지 않는 **비디오 [Rinku]** 유형은 여전히 [Rinku](https://modrinth.com/mod/rinku)를 사용합니다. 새 레이아웃에는 Watermedia 기반의 기본 비디오 유형을 사용하세요.

## 로딩 화면의 비디오

로딩 화면(게임/리소스 로딩 화면 및 월드 로딩 화면)에서는 비디오를 지원하지 않습니다.

따라서 **Drippy Loading Screen**을 통해 게임 로딩 화면에 비디오를 추가해서도 안 됩니다. 대부분의 경우 작동하지 않습니다.

대신 로딩 화면에서는 짧고 단순한 [애니메이션](/animations)(APNG 또는 GIF)을 사용하세요.

## 문제 해결

기본 비디오가 재생되지 않으면 Watermedia V3와 Watermedia Binaries V3가 사용 중인 Minecraft/모드 로더 버전과 호환되는지, 그리고 Minecraft가 Vulkan이 아닌 OpenGL을 사용하는지 확인하세요.
