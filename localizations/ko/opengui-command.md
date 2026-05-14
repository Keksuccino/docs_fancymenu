---
title: 명령으로 GUI 열기
description: 명령어를 통해 바닐라 및 커스텀 GUI를 여는 방법입니다.
---

# 명령으로 GUI 열기

FancyMenu에는 명령어로 바닐라 및 커스텀 GUI를 열 수 있는 명령어가 포함되어 있습니다.
심지어 **서버와 클라이언트 모두**에 FancyMenu를 설치하면 **다른 플레이어**의 GUI도 원격으로 열 수 있습니다.

GUI를 열려면 `/openguiscreen <screen_identifier> <target_player>` 명령어를 사용하세요.

`<screen_identifier>`를 열고 싶은 GUI의 실제 메뉴 식별자로 바꾸세요.
이 값은 FancyMenu로 만든 커스텀 GUI의 식별자일 수도 있고, 일반 바닐라/모드 GUI의 메뉴 식별자일 수도 있습니다.

**바닐라/모드 GUI의 메뉴 식별자**를 확인하려면, 식별자를 알고 싶은 메뉴를 연 다음 **Customization -> Debug Overlay**에서 FancyMenu의 **디버그 오버레이**를 활성화하세요. 그러면 첫 번째 줄로 표시되는 식별자를 클릭해 클립보드에 복사할 수 있습니다.

![copy_identifier](https://github.com/Keksuccino/FancyMenu/assets/35544624/dd6c53d9-d2bd-4810-be03-3741e326bd5a)

`<target_player>` 인자를 비워 두면 자신의 클라이언트에서 GUI가 열리고, 원하는 플레이어(또는 여러 플레이어)를 지정하면 그 플레이어들에게 GUI가 열립니다.
다른 플레이어의 클라이언트에도 FancyMenu가 설치되어 있어야 한다는 점을 기억하세요.

이 명령어는 모든 화면에서 동작하지는 않습니다. 특히 모드 화면에서는 그렇습니다. 명령어가 화면 열기에 실패하면 오류가 표시됩니다. 이 경우에는 할 수 있는 일이 많지 않습니다. 아마도 FancyMenu가 자동으로 열기에는 너무 복잡한 화면일 가능성이 큽니다.

또한 이제는 모드 화면에 대한 호환성을 제가 수동으로 추가하지 않을 예정입니다. 세상에 있는 모든 모드에 대한 호환성을 추가하려면 너무 오래 걸리기 때문입니다. 죄송합니다.

# 명령으로 GUI 닫기

드물게 필요할 수 있는 경우를 위해, 현재 화면을 닫는 `/closeguiscreen <target_player>` 명령어도 있습니다.
