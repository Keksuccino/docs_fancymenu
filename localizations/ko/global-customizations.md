---
title: 전역 사용자 지정
description: 모든 화면에 적용되는 FancyMenu 전역 조정을 적용합니다.
---

# 전역 사용자 지정

전역 사용자 지정은 게임 UI 전반에 적용되는 FancyMenu 조정입니다.
각 화면 레이아웃을 따로 편집하는 대신, 모든 곳에 일관된 스타일/동작을 적용하고 싶을 때 사용하세요.

> [!INFO]
> 대부분의 FancyMenu 사용자 지정 기능과 달리, 전역 사용자 지정은 일반 화면 사용자 지정이 비활성화되어 있어도 작동합니다.
> 화면별로 사용자 지정을 켤 필요가 **없으므로**, 한 번의 변경으로 모든 화면에 바로 영향을 줄 수 있습니다.

일반적인 예시:

- 모든 화면에 하나의 공유 버튼 및 슬라이더 스타일 사용하기.
- 메뉴 배경, 파노라마, 메뉴 음악을 전역적으로 교체하기.
- 전역 시작/창 동작(GUI 크기, 전체 화면, 창 제목/아이콘) 적용하기.
- 리소스 팩 없이 바닐라 버튼 텍스처를 전역적으로 교체하기.
- 리소스 팩 없이 바닐라 메뉴 음악을 전역적으로 교체하기.

# 찾는 위치

레이아웃 편집기 안에 **있지 않은 상태에서** FancyMenu의 **메뉴 바**를 연 다음, **Customization -> Global Customizations**로 이동하세요.

# 빠른 시작

1. **Customization -> Global Customizations**를 엽니다.
2. 시작할 카테고리 하나를 선택합니다(예: **Custom Button Textures**).
3. 해당 카테고리의 옵션(리소스 선택기, 토글, 숫자 입력)을 설정합니다.
4. 여러 화면에서 결과를 테스트합니다.
5. 관련 설정(예: 투명도, 레이블 스타일, 9-slice 테두리)을 세부 조정합니다.

# 사용자 지정 가능한 항목

## 전역 동작 및 시작

- **Game Intro** (타이틀 화면이 표시되기 전에 재생되는 인트로 영상 또는 애니메이션)
- **Singleplayer Screen World Icons**
- **Multiplayer Screen Server Icons**
- **Seamless World Loading** (월드 로딩 화면 배경으로 월드의 스크린샷을 사용)
- **Custom Window Icon**
- **Custom Window Title**
- **Default GUI Scale**
- **Force Fullscreen on Launch**

## 버튼 시각 효과

- **Custom Button Textures** (Normal/Hover/Inactive 상태, 투명 모드, nine-slice + 테두리 크기)
- **Button Labels** (호버 시 밑줄, 기본/호버 색상, 크기, 그림자)

## 슬라이더 시각 효과

- **Custom Slider Textures**
- **Slider Background Texture** (텍스처, 투명 모드, nine-slice + 테두리 크기)
- **Slider Handle Textures** (Normal/Hover/Inactive 상태, nine-slice + 테두리 크기)
- **Slider Labels** (호버 시 밑줄, 기본/호버 색상, 크기, 그림자)

## 메뉴 시각 효과 및 오디오

- **Custom Menu Background Texture**
- **Custom Menu Background Panorama**
- **Play Vanilla Menu Music** (바닐라 메뉴 음악 재생 여부를 켜거나 끄기)
- **Custom Menu Music Tracks**
- **Custom Button/Slider Click Sound**

# Custom Menu Music Tracks

**Custom Menu Music Tracks**를 사용해 메뉴용 랜덤 재생 트랙 목록을 구성하세요.

설정된 사용자 지정 트랙은 메뉴에서 바닐라 메뉴 음악을 대체합니다.

- **Custom Menu Music Tracks**를 열어 **Manage Menu Music Tracks**를 엽니다.
- **Add Track**을 사용해 오디오 소스를 추가합니다.
- **Remove Track**을 사용해 항목 하나를 제거합니다.
- **Clear Tracks**를 사용해 모든 항목을 제거합니다.
