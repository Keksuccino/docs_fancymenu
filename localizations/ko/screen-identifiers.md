---
title: 화면 식별자
description: 화면 식별자와 화면의 식별자를 찾는 방법에 관한 안내입니다.
sourceBlobSha: 64414e10bf5f532e075373a6a753e2f667448ceb
---
# 화면 식별자

FancyMenu는 레이아웃, 바닐라 위젯, [화면 동작](/action-scripts#open-screen-or-custom-gui), [사용자 지정 GUI 재정의](/custom-guis#overriding-an-existing-screen)에 화면 식별자를 사용합니다. 식별자는 대소문자를 구분하므로 디버그 오버레이에 표시된 값을 정확히 복사하세요.

기본 제공 화면에는 보통 `title_screen`과 같은 짧고 보편적인 식별자가 사용됩니다. 다른 모드의 화면에는 Java 클래스 이름이 사용될 수 있습니다. 사용자 지정 GUI에는 해당 GUI 관리자에서 입력한 식별자가 사용됩니다. 이 식별자는 FancyMenu 화면 식별자이며, Minecraft 리소스 위치가 아닙니다.

# 화면 식별자 찾기

**디버그 오버레이**를 사용하면 현재 활성화된 메뉴의 식별자를 확인할 수 있습니다.
디버그 오버레이에는 현재 화면의 식별자가 표시되며, 해당 식별자를 마우스 왼쪽 버튼으로 클릭하면 클립보드에 복사할 수 있습니다.

>[!TIP]
>레이아웃 편집기를 사용하고 있지 않을 때 **CTRL + ALT + D**를 눌러 **디버그 오버레이**를 활성화할 수 있습니다.

<br>

<img width="553" alt="Screenshot_3" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/1800351e-f042-4826-8eed-7725b78bc84d">

<br>

<img width="579" alt="Screenshot_4" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/9e0d1e61-7f2d-4817-9be1-b63ee61978dd">

# 화면 열기

[**화면 또는 사용자 지정 GUI 열기** 동작](/action-scripts#open-screen-or-custom-gui)은 현재 게임 상태에서 FancyMenu가 구성할 수 있는 화면만 열 수 있습니다. 일부 화면은 월드, 연결, 플레이어 또는 원래 상위 화면이 로드되어 있어야 합니다.

FancyMenu가 해당 식별자의 화면을 구성할 수 없으면 오류가 표시됩니다. 해당 화면을 평소에 여는 위젯에 [**바닐라/모드 버튼 모방**](/action-scripts#mimic-vanillamod-button)을 사용하세요.
