---
title: 명령어
description: FancyMenu의 명령어와 사용 방법입니다.
sourceBlobSha: 265258e46a219a12892146238e379af513ff0848
---

# 명령어

FancyMenu는 게임에 명령어를 추가합니다. FTB Quests 같은 다른 모드와 함께 사용하면 매우 유용합니다.

> [!WARNING]
> 멀티플레이에서 명령어를 사용하려면 FancyMenu가 **서버**와 클라이언트에 모두 설치되어 있어야 합니다!

## 대상 플레이어 및 권한

`/openguiscreen`, `/closeguiscreen`, `/fmlayout` 명령어의 대상 플레이어 인수는 선택 사항입니다. 인수를 생략하면 명령어를 실행한 플레이어에게 적용됩니다. 대상을 지정하면 일반 플레이어 이름과 `@a` 같은 선택자를 사용할 수 있습니다.

- `/openguiscreen` 또는 `/closeguiscreen`에 대상 인수를 지정하려면 명령어 실행자 본인을 대상으로 지정하더라도 **권한 레벨 2**(게임 마스터 / OP 레벨 2)가 필요합니다.
- `/fmlayout`에 대상 인수를 지정하려면 명령어 실행자 본인을 대상으로 지정하더라도 **권한 레벨 3**(관리자 / OP 레벨 3)이 필요합니다.
- `/fmdata`의 모든 하위 명령어에는 **권한 레벨 2**(게임 마스터 / OP 레벨 2)가 필요합니다.

대상을 선택적으로 지정할 수 있는 세 명령어에서 대상을 생략하려면 명령어 실행자가 플레이어여야 합니다. 서버 콘솔에서는 대상을 지정하고 대상 인수에 필요한 권한을 갖춰야 합니다.

## /openguiscreen

`/openguiscreen` 명령어는 바닐라 화면, 모드 화면 또는 [커스텀 GUI](/custom-guis)를 엽니다. FancyMenu가 서버와 해당 플레이어의 클라이언트에 설치되어 있으면 다른 플레이어를 대상으로 지정할 수 있습니다.

[명령어로 GUI 열기](/opengui-command) 및 [화면 식별자](/screen-identifiers)를 참조하세요.

모든 모드 화면을 직접 생성할 수 있는 것은 아닙니다. 대상 화면이 지원되지 않으면 FancyMenu가 오류를 표시합니다. 로컬 레이아웃에서는 해당 화면을 여는 위젯에 [**바닐라/모드 버튼 모방**](/action-scripts#mimic-vanillamod-button)을 사용하세요.

**사용법:** `/openguiscreen <screen_identifier> [<target_players>]`

## /closeguiscreen

`/closeguiscreen` 명령어는 명령어 실행자 또는 선택한 플레이어의 현재 화면을 닫습니다. 명령어를 실행할 수 있는 퀘스트, 이벤트 또는 자동화 모드와 함께 사용하면 유용합니다.

**사용법:** `/closeguiscreen [<target_players>]`

## /fmlayout

`/fmlayout` 명령어는 하나 이상의 클라이언트에서 레이아웃을 활성화할지 설정합니다. FancyMenu에 표시되는 레이아웃 이름을 정확히 사용하고, 이름에 공백이 있으면 따옴표로 묶으세요.

**사용법:** `/fmlayout <layout_name> <true|false> [<target_players>]`

예시:

- `/fmlayout quest_complete true`는 명령어를 실행한 플레이어에게 `quest_complete`를 활성화합니다.
- `/fmlayout quest_complete false @a`는 온라인 상태인 모든 플레이어에게 해당 레이아웃을 비활성화합니다. 대상을 지정하려면 권한 레벨 3이 필요합니다.

## /fmvariable

`/fmvariable` 명령어로 [FancyMenu 변수](/variables)를 설정하고 읽을 수 있습니다.

다른 플레이어로 이 명령어를 실행하려면 바닐라의 `/execute as` 명령어를 사용하세요.
`/execute as ExamplePlayer run fmvariable ...`

**사용법:**

- `/fmvariable get <variable_name>`
- `/fmvariable set <variable_name> <send_chat_feedback> <set_to_value>`

### 가져오기

**변수 값을 가져오려면** 다음과 같이 `get` 하위 명령어를 사용하세요.
`/fmvariable get some_variable`

그러면 해당 변수의 값이 채팅에 표시됩니다.

### 설정

**변수를 설정하려면** 새 값 앞에 채팅 피드백 여부를 나타내는 불리언 값을 입력하세요.
`/fmvariable set some_variable true new_value`

`send_chat_feedback` 인수는 FancyMenu가 채팅으로 변경을 확인할지 여부를 설정합니다. `set_to_value` 인수는 명령어의 나머지 부분을 값으로 사용하므로 값에 공백을 포함할 수 있습니다. 예를 들어 `/fmvariable set greeting false Hello from FancyMenu`는 성공 피드백을 보내지 않고 `Hello from FancyMenu`를 저장합니다.

## /fmdata

`/fmdata` 명령어는 서버와 FancyMenu 클라이언트 간에 사용자 지정 데이터를 전송하고, 서버 측 리스너를 관리하며, 플레이어가 접속할 때 전송할 데이터를 설정하고, 이 설정을 [AI 채팅](/export-for-ai#servers)용으로 내보냅니다. `/fmdata`의 모든 하위 명령어에는 권한 레벨 2가 필요합니다.

모든 하위 명령어와 구문, 예시는 [FM Data](/fm-data)를 참조하세요.
