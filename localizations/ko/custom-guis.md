---
title: 사용자 지정 GUI
description: 게임에 새 GUI 화면을 추가하는 방법입니다.
---

# 사용자 지정 GUI

FancyMenu를 사용하면 기존 GUI 화면을 커스터마이즈할 수 있을 뿐만 아니라, 완전히 새로운 GUI를 추가하고 요소를 채워 넣을 수도 있습니다.

# 새 화면 추가하기

새 화면을 추가하려면 **Customization -> Custom GUIs -> Manage Custom GUIs**로 이동하세요.

![custom_gui_1](https://github.com/Keksuccino/FancyMenu/assets/35544624/23e704ee-ccb5-434d-b75f-f4418399d9b7)

다음 메뉴에서 **New GUI**를 클릭하세요.

![custom_gui_2](https://github.com/Keksuccino/FancyMenu/assets/35544624/035454e8-b089-4b9a-9092-89a193c0eacd)

여기에서 새 GUI에 고유한 식별자를 지정해야 하며, 기본 화면 동작의 다른 부분도 설정할 수 있습니다.
다 끝났으면 **Done**을 누르세요.

![custom_gui_3](https://github.com/Keksuccino/FancyMenu/assets/35544624/1fbed3f9-9c81-4c73-85c7-d152146c55d8)

이제 비어 있는 새 GUI가 생겼습니다. 열려면 **Manage Custom GUIs** 메뉴에서 해당 GUI를 선택한 다음 **Open GUI**를 클릭하세요.

![custom_gui_4](https://github.com/Keksuccino/FancyMenu/assets/35544624/b2e6a4b7-540d-4bf2-9dce-09bfff11ae7e)

그러면 아직 꽤 비어 있는 GUI 화면이 열립니다. 이 화면을 덜 비어 보이게 하려면, 다른 화면을 만들 때처럼 새 레이아웃을 추가하면 됩니다.

![custom_gui_5](https://github.com/Keksuccino/FancyMenu/assets/35544624/e7e06a5f-46b3-48f1-9ad9-96a7565c97a9)

# 액션으로 GUI 열기

마지막으로 일반 사용자가 이 GUI에 접근할 수 있도록 해야 합니다. 가장 쉬운 방법은 버튼, 슬라이더 또는 티커와 함께 **Open Screen or Custom GUI** 액션을 사용하는 것입니다.

![custom_gui_6](https://github.com/Keksuccino/FancyMenu/assets/35544624/b5cc6518-3fc4-4715-96d4-44b65ab7831d)

# 명령어로 GUI 열기

사용자 지정 GUI는 [게임 내 명령어](./commands#openguiscreen)로도 열 수 있습니다.
이 방법을 사용하면 다른 사용자에게도 원격으로 GUI를 열 수 있습니다!

# 팝업 모드

FancyMenu v3.8.0부터 사용자 지정 GUI는 "Popup Mode"를 지원하며, 이를 사용하면 다른 화면 위에 팝업이 열리는 것처럼 보이게 됩니다(사용자 지정 GUI를 열기 전의 이전 화면 위에 표시됨). 이 설정은 각 사용자 지정 GUI의 설정에서 개별적으로 전환할 수 있습니다.

FancyMenu 3.9.0에서는 월드 안에 있을 때 사용자 지정 GUI의 화면 배경 오버레이를 켜고 끌 수 있는 옵션도 추가되었습니다. 게임 플레이 중에 열린 사용자 지정 GUI 뒤의 블러/어두운 색조를 비활성화하거나 유지하고 싶을 때 사용하세요.
