---
title: 클라이언트 < - > 서버 데이터 공유
description: FancyMenu를 사용하여 서버와 클라이언트 간에 사용자 지정 데이터를 주고받습니다.
---

# FM 데이터

"FM Data" 시스템을 사용하면 서버와 클라이언트 간에 사용자 지정 텍스트 데이터를 보낼 수 있습니다.

모든 `/fmdata` 하위 명령은 **권한 레벨 2**(게임 마스터 / OP 레벨 2)가 필요합니다.

모든 FM Data 메시지는 다음으로 구성됩니다:

1. **데이터 식별자** (어떤 종류의 메시지인지)
2. **데이터 값** (실제 내용)

예시:

- 식별자: `hud.food`
- 데이터: `18/20`

# 빠른 시작

1. 서버가 `/fmdata send ...`로 데이터를 보냅니다.
2. 클라이언트는 FancyMenu 리스너 **On FM Data Received**로 이를 받습니다.
3. 클라이언트도 액션 **Send FM Data To Server**로 데이터를 다시 보낼 수 있습니다.
4. 서버는 `/fmdata listener ...`로 자동 반응할 수 있습니다.
5. 서버는 `/fmdata welcome_data ...`로 접속 시 자동 전송도 할 수 있습니다.

# 서버 -> 클라이언트

다음을 사용하세요:

```mcfunction
/fmdata send <target_players> <data_identifier> <string_data>
```

예시:

```mcfunction
/fmdata send Player761 hud.food 18/20
/fmdata send @a "food value update" "18 of 20"
```

참고:

- `<target_players>`는 플레이어 이름과 `@a`, `@p`, `@s` 같은 선택자를 지원합니다.
- 공백이 있는 값은 따옴표로 감싸세요.

# 클라이언트: 데이터 받기

FancyMenu 리스너를 사용하세요:

- **On FM Data Received**

사용 가능한 변수:

- `$$data_identifier`
- `$$data`
- `$$sent_by`

`$$sent_by` 값은 다음과 같습니다:

- 멀티플레이에서는 서버 IP
- 싱글플레이에서는 `integrated_server`

일반적인 사용 사례:

- 텍스트 요소 업데이트
- 메뉴 액션 트리거
- 들어오는 식별자/데이터에 따라 로직 실행

# 클라이언트 -> 서버

FancyMenu 액션을 사용하세요:

- **Send FM Data To Server**

이 액션에는 2개의 입력이 있습니다:

1. Data Identifier
2. Data

그다음 서버는 `/fmdata listener ...`로 들어오는 데이터를 처리할 수 있습니다.

# 서버 리스너

서버 리스너는 클라이언트로부터 들어오는 데이터를 감시하며, 트리거되면 하나 또는 여러 개의 명령을 실행할 수 있습니다.

서버 리스너는 저장되며 재시작 후에도 활성 상태를 유지합니다.

다음 명령으로 관리할 수 있습니다:

- `/fmdata listener list`
- `/fmdata listener add ...`
- `/fmdata listener edit ...`
- `/fmdata listener remove ...`

## 추가 / 수정 문법

```mcfunction
/fmdata listener add <unique_listener_name> <matching_type_identifier> <matching_type_data> <ignore_case_identifier> <ignore_case_data> <fire_for_player> <listen_for_identifier> <listen_for_data> <commands_to_execute_on_fire>
```

```mcfunction
/fmdata listener edit <listener_name> <matching_type_identifier> <matching_type_data> <ignore_case_identifier> <ignore_case_data> <fire_for_player> <listen_for_identifier> <listen_for_data> <commands_to_execute_on_fire>
```

## 제거 문법

```mcfunction
/fmdata listener remove <listener_name>
```

## 매칭 유형

`matching_type_identifier`와 `matching_type_data`는 다음 중 하나일 수 있습니다:

- `equals`
- `contains`
- `starts_with`
- `ends_with`

## 매칭 규칙

- `ignore_case_identifier`와 `ignore_case_data`는 true/false 전환값입니다.
- `listen_for_identifier`는 와일드카드 `*`를 지원합니다(항상 일치).
- `listen_for_data`는 와일드카드 `*`를 지원합니다(항상 일치).
- `fire_for_player`는 일반적인 플레이어 선택자를 사용합니다(예: `@a`, `@p`, `Player761`)

## 발동 시 실행 명령

`commands_to_execute_on_fire`는 하나의 텍스트 입력입니다.

- 여러 명령은 `|||`로 구분합니다.
- 리터럴 구분자는 `\|\|\|`로 이스케이프합니다.

명령이 실행되기 직전에 다음 두 특수 플레이스홀더가 치환됩니다:

- `%fm_sender%` -> FM Data를 보낸 플레이어
- `%fm_data%` -> 클라이언트로부터 받은 데이터 값

명령은 서버 명령으로 실행됩니다.

## 예시 명령

모든 플레이어의 버튼 클릭에 반응하기:

```mcfunction
/fmdata listener add button_ping equals equals false false @a ui.button pressed "tellraw @a {\"text\":\"%fm_sender% pressed the button\"}"
```

데이터에 `gold`가 포함될 때 여러 명령 실행하기:

```mcfunction
/fmdata listener add reward equals contains false true @a reward "gold" "say Reward from %fm_sender%: %fm_data%|||effect give %fm_sender% minecraft:speed 3 1 true"
```

# 환영 데이터

환영 데이터는 플레이어가 접속할 때 일치하는 플레이어에게 FM Data를 보냅니다.

다음 명령으로 항목을 관리할 수 있습니다:

- `/fmdata welcome_data list`
- `/fmdata welcome_data add ...`
- `/fmdata welcome_data edit ...`
- `/fmdata welcome_data remove ...`

## 추가 / 수정 문법

```mcfunction
/fmdata welcome_data add <unique_welcome_data_name> <target_player> <data_identifier> <string_data>
```

```mcfunction
/fmdata welcome_data edit <welcome_data_name> <target_player> <data_identifier> <string_data>
```

## 제거 문법

```mcfunction
/fmdata welcome_data remove <welcome_data_name>
```

참고:

- `<target_player>`는 `@a`, `@p`, `@s` 같은 일반 선택자를 지원합니다.
- 데이터는 접속한 일치 플레이어에게 전송됩니다.
- 항목은 자동으로 저장되고 불러와집니다.

## 예시 명령

접속하는 모든 플레이어에게 환영 데이터 보내기:

```mcfunction
/fmdata welcome_data add welcome_all @a hud.welcome "Welcome!"
```

한 플레이어에게만 환영 데이터 보내기:

```mcfunction
/fmdata welcome_data add welcome_vip Player761 hud.vip "VIP perks enabled"
```

# 모범 사례

1. `hud.food`, `menu.shop.open`, `quest.progress`처럼 명확한 식별자를 사용하세요.
2. 각 식별자에 대해 데이터 형식을 일관되게 유지하세요.
3. 먼저 단순하게 시작하세요: 복잡한 리스너를 만들기 전에 `/fmdata send`로 테스트하세요.
4. 전역 동작이 정말 필요할 때만 `@a`를 사용하세요.
5. 설정을 깔끔하게 유지하려면 `/fmdata listener list`와 `/fmdata welcome_data list`를 사용하세요.
