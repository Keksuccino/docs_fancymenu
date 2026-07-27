---
title: 명령으로 GUI 열기
description: 명령을 통해 바닐라 및 사용자 지정 GUI를 여는 방법입니다.
---

# 명령으로 GUI 열기

`/openguiscreen` 명령은 바닐라, 모드, 그리고 [사용자 지정 GUI](./custom-guis)를 엽니다. FancyMenu가 서버와 해당 클라이언트에 설치되어 있으면 다른 플레이어를 대상으로 할 수도 있습니다.

GUI를 열려면 `/openguiscreen <screen_identifier> [<target_players>]`를 사용하세요.

`<screen_identifier>`에는 사용자 지정 GUI 또는 바닐라/모드 화면의 정확한 식별자(대소문자 구분)를 입력하세요.

식별자를 찾으려면 대상 화면을 열고 **CTRL + ALT + D**로 디버그 오버레이를 활성화하세요. 첫 번째 줄에 있는 식별자를 선택하면 복사됩니다. [화면 식별자](./screen-identifiers)를 참고하세요.

![copy_identifier](https://github.com/Keksuccino/FancyMenu/assets/35544624/dd6c53d9-d2bd-4810-be03-3741e326bd5a)

자신에게 GUI를 열려면 `[<target_players>]`를 생략하세요. 또는 플레이어 이름이나 `@a` 같은 셀렉터를 사용해 한 명 또는 여러 명에게 열 수 있습니다. 대상 인수를 지정하려면 자신을 대상으로 하더라도 권한 수준 2(Game Master / OP 레벨 2)가 필요하며, 대상이 되는 모든 플레이어의 클라이언트에 FancyMenu가 설치되어 있어야 합니다.

모든 모드 화면을 직접 생성할 수 있는 것은 아닙니다. FancyMenu는 대상 화면이 지원되지 않으면 오류를 표시합니다. 로컬 레이아웃에서는 일반적으로 해당 화면을 여는 위젯에 [**바닐라/모드 버튼 모방**](./action-scripts#mimic-vanillamod-button-mimicbutton)을 사용하세요.

# 명령으로 GUI 닫기

드물게 필요할 경우, `/closeguiscreen [<target_players>]`를 사용해 현재 화면을 닫을 수 있습니다. 대상 인수를 생략하면 자신에게 적용되며, 대상 인수를 지정하려면 권한 수준 2가 필요합니다.
