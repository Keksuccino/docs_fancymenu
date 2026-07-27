---
title: 화면 식별자
description: 화면 식별자와 화면의 식별자를 찾는 방법에 대해 설명합니다.
---
# 화면 식별자

FancyMenu는 레이아웃, 바닐라 위젯, [화면 동작](./action-scripts#open-screen-or-custom-gui-opengui), 그리고 [사용자 지정 GUI 재정의](./custom-guis#overriding-an-existing-screen)에 화면 식별자를 사용합니다. 식별자는 대소문자를 구분하므로, 디버그 오버레이에서 그대로 정확히 복사해야 합니다.

내장 화면은 보통 `title_screen` 같은 짧고 공통적인 식별자를 사용합니다. 다른 모드의 화면은 해당 Java 클래스 이름을 사용할 수 있습니다. 사용자 지정 GUI는 관리자에서 입력한 식별자를 사용합니다. 이는 Minecraft 리소스 위치가 아니라 FancyMenu 화면 식별자입니다.

# 화면의 식별자 찾기

**디버그 오버레이**를 사용하면 현재 활성 메뉴의 식별자를 확인할 수 있습니다.
이 오버레이에는 현재 화면의 식별자가 표시되며, 왼쪽 클릭으로 클립보드에 복사할 수 있습니다.

>[!TIP]
>**레이아웃 편집기**에 있지 않을 때 **CTRL + ALT + D**를 누르면 **디버그 오버레이**를 활성화할 수 있습니다.

<br>

<img width="553" alt="Screenshot_3" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/1800351e-f042-4826-8eed-7725b78bc84d">

<br>

<img width="579" alt="Screenshot_4" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/9e0d1e61-7f2d-4817-9be1-b63ee61978dd">

# 화면 열기

[**Open Screen or Custom GUI** 동작](./action-scripts#open-screen-or-custom-gui-opengui)은 현재 게임 상태에서 FancyMenu가 구성할 수 있는 화면만 열 수 있습니다. 일부 화면은 월드 로드, 연결, 플레이어, 또는 원래 상위 화면이 필요합니다.

FancyMenu가 해당 식별자의 화면을 구성할 수 없으면 오류가 표시됩니다. 일반적으로 해당 화면을 여는 위젯에 [**Mimic Vanilla/Mod Button**](./action-scripts#mimic-vanillamod-button-mimicbutton)을 사용하세요.
