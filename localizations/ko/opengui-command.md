---
title: 명령어로 GUI 열기
description: 명령어로 바닐라 및 커스텀 GUI를 여는 방법입니다.
sourceBlobSha: 9d0c8fbc3fa1d1cb15dc19e94f1f0fc1ba37ae05
---

# 명령어로 GUI 열기

`/openguiscreen` 명령어를 사용하면 바닐라, 모드 및 [커스텀 GUI](/custom-guis)를 열 수 있습니다. 서버와 플레이어의 클라이언트에 FancyMenu가 설치되어 있으면 다른 플레이어를 대상으로 지정할 수 있습니다.

GUI를 열려면 `/openguiscreen <screen_identifier> [<target_players>]`를 사용하세요.

`<screen_identifier>`를 커스텀 GUI 또는 바닐라/모드 화면의 정확한 식별자로 바꾸세요. 대소문자도 정확히 일치해야 합니다.

식별자를 찾으려면 대상 화면을 열고 **CTRL + ALT + D**를 눌러 디버그 오버레이를 활성화하세요. 첫 번째 줄에 표시되는 식별자를 선택하면 복사할 수 있습니다. 자세한 내용은 [화면 식별자](/screen-identifiers)를 참조하세요.

![copy_identifier](https://github.com/Keksuccino/FancyMenu/assets/35544624/dd6c53d9-d2bd-4810-be03-3741e326bd5a)

`[<target_players>]`를 생략하면 자신에게 GUI가 열립니다. 플레이어 이름이나 `@a` 같은 선택자를 사용하면 한 명 이상의 플레이어에게 GUI를 열 수 있습니다. 대상 인수를 지정하려면 자신을 대상으로 지정하더라도 권한 레벨 2(Game Master / OP 레벨 2)가 필요하며, 대상 플레이어의 클라이언트에도 FancyMenu가 설치되어 있어야 합니다.

모든 모드 화면을 직접 생성할 수 있는 것은 아닙니다. 대상 화면을 지원하지 않는 경우 FancyMenu에 오류가 표시됩니다. 로컬 레이아웃에서는 해당 화면을 원래 여는 위젯에 [**바닐라/모드 버튼 모방**](/action-scripts#mimic-vanillamod-button)을 사용하세요.

# 명령어로 GUI 닫기

필요한 경우 `/closeguiscreen [<target_players>]`를 사용하면 현재 화면을 닫을 수 있습니다. 대상을 생략하면 자신에게 적용되며, 대상 인수를 지정하려면 권한 레벨 2가 필요합니다.
