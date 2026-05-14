---
title: 비디오 (MP4)
description: FancyMenu에서 비디오를 사용할 때 알아두어야 할 내용입니다.
---

# 비디오

FancyMenu는 요소, 메뉴 배경, Game Intro 콘텐츠로 MP4 비디오 재생을 지원합니다.

FancyMenu 3.9.0에서는 Watermedia V3 기반의 새로운 기본 **Video** 요소와 **Video** 메뉴 배경이 추가되었습니다. 기존의 **Video [MCEF]** 요소/배경 유형은 더 이상 권장되지 않으며, 아직 필요한 이전 레이아웃에서만 유지해야 합니다.

비디오 배경과 요소를 제어하기 위한 다음 **액션**도 있습니다:

- **Set Video Element Volume**: Video 요소의 볼륨 설정
- **Set Video Element Play Time**: Video 요소를 밀리초 타임스탬프로 탐색
- **Toggle Video Element Paused State**: Video 요소의 일시정지 상태 전환
- **Set Video Background Volume**: Video 메뉴 배경의 볼륨 설정
- **Set Video Background Play Time**: Video 메뉴 배경을 밀리초 타임스탬프로 탐색
- **Toggle Video Background Paused State**: Video 메뉴 배경의 일시정지 상태 전환

그리고 비디오 배경과 요소 정보를 가져오기 위한 다음 **플레이스홀더**도 있습니다:

- **Video Element Volume**: Video 요소의 볼륨 가져오기
- **Video Element Duration**: Video 요소의 재생 시간 가져오기
- **Video Element Play Time**: Video 요소의 현재 재생 시간(진행률) 가져오기
- **Video Element Paused State**: Video 요소의 일시정지 상태(true/false) 가져오기
- **Video Background Volume**: Video 메뉴 배경의 볼륨 가져오기
- **Video Background Duration**: Video 메뉴 배경의 재생 시간 가져오기
- **Video Background Play Time**: Video 메뉴 배경의 현재 재생 시간(진행률) 가져오기
- **Video Background Paused State**: Video 메뉴 배경의 일시정지 상태(true/false) 가져오기

재생 시간 및 진행 시간 플레이스홀더는 기본적으로 `MM:SS` 형식으로 반환됩니다. 밀리초 타임스탬프가 필요할 때는 `output_as_timestamp`를 `true`로 설정하세요. 재생 시간 플레이스홀더는 `show_percentage`를 사용하여 0-100 진행률 값도 표시할 수 있습니다.

FancyMenu 3.9.0에는 또한 **On Video Playback Status Changed** 리스너가 추가되었으며, `PLAYING`, `PAUSED`, `STOPPED`, `FINISHED` 상태에 반응할 수 있습니다.

## 요구 사항

새로운 기본 Video 요소와 메뉴 배경 유형을 사용하려면 다음을 설치해야 합니다:

- **Watermedia V3**
- **Watermedia Binaries V3**

이들은 선택적 종속성이므로, 비디오 지원을 사용하려면 인스턴스에 수동으로 추가해야 합니다.

더 이상 권장되지 않는 **Video [MCEF]** 유형은 계속 MCEF를 사용합니다. 새 레이아웃에서는 대신 Watermedia 기반의 기본 Video 유형을 사용하세요.

## 로딩 화면의 비디오

비디오 지원은 로딩 화면(게임/리소스 로딩 화면 및 월드 로딩 화면)에서는 작동하지 않습니다.

따라서 **Drippy Loading Screen**을 통해 게임 로딩 화면에 비디오를 추가해서도 안 됩니다. 대부분의 경우 작동하지 않기 때문입니다.

대신 로딩 화면에서는 짧고 단순한 AFMA/FMA 파일을 사용하는 것이 좋습니다. 애니메이션이 충분히 단순하고 짧다면, 대부분의 경우 사용자는 다시 로드되는 것을 알아차리지 못합니다.

## 문제 해결

기본 비디오 지원에 문제가 있다면, 먼저 Watermedia V3와 Watermedia Binaries V3가 모두 설치되어 있고 Minecraft/모드로더 버전과 일치하는지 확인하세요.
