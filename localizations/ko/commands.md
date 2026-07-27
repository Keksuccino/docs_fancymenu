---
title: 명령어
description: FancyMenu의 명령어와 사용 방법입니다.
---

# 명령어

FancyMenu는 FTB Quests 같은 다른 모드와 함께 사용할 때 매우 유용할 수 있는 몇 가지 명령어를 게임에 추가합니다.

> [!WARNING]
> 멀티플레이에서 명령어를 사용하려면 FancyMenu가 **서버**(및 클라이언트)에 설치되어 있어야 합니다!

## 대상 플레이어 및 권한

`/openguiscreen`, `/closeguiscreen`, `/fmlayout`의 대상 플레이어 인자는 선택 사항입니다. 플레이어가 이를 생략하면 해당 플레이어에게 명령어가 적용됩니다. 대상을 지정하면 일반 플레이어 이름과 `@a` 같은 셀렉터를 사용할 수 있습니다.

- `/openguiscreen` 또는 `/closeguiscreen`에 대상 인자를 지정하려면, 명령어의 실행 주체가 자신이더라도 **권한 레벨 2**(게임 마스터 / OP 레벨 2)가 필요합니다.
- `/fmlayout`에 대상 인자를 지정하려면, 명령어의 실행 주체가 자신이더라도 **권한 레벨 3**(관리자 / OP 레벨 3)가 필요합니다.
- 모든 `/fmdata` 하위 명령어는 **권한 레벨 2**(게임 마스터 / OP 레벨 2)가 필요합니다.

선택적 대상을 가진 세 명령어는 명령어 실행 주체가 플레이어일 때만 대상을 생략할 수 있습니다. 서버 콘솔은 반드시 대상을 지정해야 하며, 대상 인자에 필요한 권한 조건도 충족해야 합니다.

## /openguiscreen

`/openguiscreen` 명령어는 바닐라, 모드 또는 [사용자 지정 GUI](./custom-guis)를 엽니다. FancyMenu가 서버와 해당 클라이언트에 설치되어 있으면 다른 플레이어를 대상으로 할 수 있습니다.

자세한 내용은 [명령어로 GUI 열기](./opengui-command)와 [화면 식별자](./screen-identifiers)를 참조하세요.

모든 모드 화면을 직접 생성할 수 있는 것은 아닙니다. 대상 화면이 지원되지 않으면 FancyMenu가 오류를 표시합니다. 로컬 레이아웃에서는, 일반적으로 해당 화면을 여는 위젯에 [**바닐라/모드 버튼 흉내내기**](./action-scripts#mimic-vanillamod-button-mimicbutton)를 사용하세요.

**사용법:** `/openguiscreen <screen_identifier> [<target_players>]`

## /closeguiscreen

`/closeguiscreen` 명령어는 명령어 실행 주체 또는 선택된 플레이어의 현재 화면을 닫습니다. 명령어를 실행할 수 있는 퀘스트, 이벤트, 자동화 모드와 함께 사용할 때 유용합니다.

**사용법:** `/closeguiscreen [<target_players>]`

## /fmlayout

`/fmlayout` 명령어는 하나 이상의 클라이언트에서 레이아웃을 활성화할지 여부를 설정합니다. 레이아웃 이름은 FancyMenu에 표시되는 그대로 정확히 사용해야 하며, 공백이 포함된 이름은 따옴표로 감싸세요.

**사용법:** `/fmlayout <layout_name> <true|false> [<target_players>]`

예시:

- `/fmlayout quest_complete true`는 명령어를 실행한 플레이어에게 `quest_complete`를 활성화합니다.
- `/fmlayout quest_complete false @a`는 접속 중인 모든 플레이어에 대해 이를 비활성화합니다. 대상 인자를 지정하려면 권한 레벨 3이 필요합니다.

## /fmvariable

`/fmvariable` 명령어는 [FancyMenu 변수](./variables)를 설정하고 읽습니다.

이 명령어를 다른 플레이어로 실행하려면 바닐라의 `/execute as` 명령어를 사용하세요:
`/execute as ExamplePlayer run fmvariable ...`

**사용법:**

- `/fmvariable get <variable_name>`
- `/fmvariable set <variable_name> <send_chat_feedback> <set_to_value>`

### 가져오기

변수 값을 **가져오려면**, 다음처럼 `get` 하위 명령어를 사용하세요:
`/fmvariable get some_variable`

그러면 이 변수의 값이 채팅에 출력됩니다.

### 설정

변수를 **설정하려면**, 새 값 앞에 채팅 피드백 불리언을 넣으세요:
`/fmvariable set some_variable true new_value`

`send_chat_feedback` 인자는 FancyMenu가 변경 사항을 채팅에 확인 표시할지 여부를 제어합니다. `set_to_value` 인자는 명령어의 나머지 부분을 모두 소비하므로, 값에 공백을 포함할 수 있습니다. 예를 들어 `/fmvariable set greeting false Hello from FancyMenu`는 성공 피드백을 보내지 않고 `Hello from FancyMenu`를 저장합니다.

## /fmdata

`/fmdata` 명령어는 서버와 FancyMenu 클라이언트 간에 사용자 지정 데이터를 전송하고, 서버 측 리스너를 관리하며, 플레이어가 접속할 때 전송될 데이터를 구성합니다. 모든 `/fmdata` 하위 명령어는 권한 레벨 2가 필요합니다.

모든 하위 명령어, 문법, 예시는 [FM 데이터](./fm-data)를 참조하세요.
