---
title: 전역 사용자 지정
description: 모든 화면에 적용되는 전역 FancyMenu 조정을 적용합니다.
---

# 전역 사용자 지정

전역 사용자 지정은 각 화면 레이아웃을 수정하지 않고도 공유 UI 및 시작 설정을 적용합니다. 일반 화면 사용자 지정이 비활성화되어 있어도 작동합니다.

일반적인 예:

- 모든 화면에 하나의 공유 버튼 및 슬라이더 스타일 사용
- 메뉴 배경, 파노라마, 메뉴 음악을 전역적으로 교체
- 전역 시작/창 동작 적용(GUI 크기, 전체화면, 창 제목/아이콘)
- 리소스 팩 없이 바닐라 버튼 텍스처를 전역적으로 교체
- 리소스 팩 없이 바닐라 메뉴 음악을 전역적으로 교체

# 찾는 위치

레이아웃 편집기가 **아닌** 상태에서 FancyMenu의 **메뉴 바**를 연 다음 **Customization -> Global Customizations**로 이동하세요.

# 사용자 지정 가능한 항목

## 전역 동작 및 시작

- [**Game Intro**](./game-intro) (타이틀 화면 전에 재생되는 소개 영상 또는 애니메이션)
- **Singleplayer Screen World Icons**
- **Multiplayer Screen Server Icons**
- [**Seamless World Loading**](./seamless-world-loading) (최근 월드 스크린샷을 로딩 화면 배경으로 사용)
- [**Custom Window Icon**](./window-customization#custom-icon)
- [**Custom Window Title**](./window-customization#custom-title)
- **Default GUI Scale**
- **Force Fullscreen on Launch**

## 버튼 시각 효과

- **Custom Button Textures** (Normal/Hover/Inactive 상태, 투명 모드, [nine-slice](./nine-slicing-and-tiling) + 테두리 크기)
- **Button Labels** (호버 시 밑줄, 기본/호버 색상, 크기, 그림자)

## 슬라이더 시각 효과

- **Custom Slider Textures**
- **Slider Background Texture** (텍스처, 투명 모드, [nine-slice](./nine-slicing-and-tiling) + 테두리 크기)
- **Slider Handle Textures** (Normal/Hover/Inactive 상태, [nine-slice](./nine-slicing-and-tiling) + 테두리 크기)
- **Slider Labels** (호버 시 밑줄, 기본/호버 색상, 크기, 그림자)

## 메뉴 시각 효과 및 오디오

- [**Custom Menu Background Texture**](./menu-backgrounds)
- [**Custom Menu Background Panorama**](./panoramas)
- **Play Vanilla Menu Music** (바닐라 메뉴 음악 재생을 활성화/비활성화)
- [**Custom Menu Music Tracks**](./background-music)
- **Custom Button/Slider Click Sound**

# Custom Menu Music Tracks

**Custom Menu Music Tracks**를 사용하여 메뉴용 무작위 트랙 목록을 만드세요.

> [!IMPORTANT]
> 전역 사용자 지정 메뉴 트랙은 타이틀 화면처럼 월드가 로드되지 않은 경우에만 재생됩니다. 월드 내 메뉴 오디오에는 [**Audio** 요소](./elements#audio)를 사용하세요.

설정된 트랙은 Music 사운드 채널을 사용하며, 지원되는 월드 밖 메뉴에서 바닐라 메뉴 음악을 대체합니다.

- 첫 번째 트랙은 약 5초 후에 시작됩니다.
- 이후 트랙은 약 1초에서 30초 사이의 무작위 지연 후 시작됩니다.
- 트랙은 무작위로 선택됩니다.
- 여러 트랙이 있을 경우 이전 트랙이 연속해서 두 번 선택되지 않습니다.

트랙 목록은 **Custom Menu Music Tracks**에서 관리하세요:

- **Custom Menu Music Tracks**를 열어 **Manage Menu Music Tracks**를 엽니다.
- **Add Track**으로 오디오 소스를 추가합니다.
- **Remove Track**으로 항목 하나를 제거합니다.
- **Clear Tracks**로 모든 항목을 제거합니다.
