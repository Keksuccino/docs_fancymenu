---
title: 클라이언트 < - > 서버 데이터 공유
description: FancyMenu로 서버와 클라이언트 간에 사용자 지정 데이터를 주고받습니다.
sourceBlobSha: 35ae4605e43ac917f11c24e5d97a5c311c9aa01a
---

# FM 데이터

"FM Data" 시스템을 사용하면 서버와 클라이언트 간에 사용자 지정 텍스트 데이터를 주고받을 수 있습니다.

모든 `/fmdata` 하위 명령어를 사용하려면 **권한 레벨 2**(게임 마스터 / OP 레벨 2)가 필요합니다.

모든 FM Data 메시지는 다음 항목으로 구성됩니다.

1. **데이터 식별자**(메시지의 종류)
2. **데이터 값**(실제 콘텐츠)

예시:

- 식별자: `hud.food`
- 데이터: `18/20`

# 빠른 시작

1. 서버에서 `/fmdata send ...`로 데이터를 보냅니다.
2. 클라이언트에서 FancyMenu 리스너 **On FM Data Received**로 데이터를 받습니다.
3. 클라이언트에서도 **Send FM Data To Server** 액션을 사용해 데이터를 서버로 보낼 수 있습니다.
4. 서버에서 `/fmdata listener ...`로 자동 반응을 설정할 수 있습니다.
5. 서버에서 `/fmdata welcome_data ...`로 플레이어가 접속할 때 데이터를 자동으로 보낼 수 있습니다.

# 서버 -> 클라이언트

다음 명령어를 사용합니다.

```mcfunction
/fmdata send <target_players> <data_identifier> <string_data>
```

예시:

```mcfunction
/fmdata send Player761 hud.food 18/20
/fmdata send @a "food value update" "18 of 20"
```

참고:

- `<target_players>`에는 플레이어 이름과 `@a`, `@p`, `@s` 같은 선택자를 사용할 수 있습니다.
- 공백이 포함된 값에는 따옴표를 사용합니다.

# 클라이언트: 데이터 받기

FancyMenu 리스너를 사용합니다.

- **On FM Data Received**

사용할 수 있는 변수:

- `$$data_identifier`
- `$$data`
- `$$sent_by`

`$$sent_by`의 값은 다음과 같습니다.

- 멀티플레이에서는 서버 IP
- 싱글플레이에서는 `integrated_server`

일반적인 사용 사례:

- 텍스트 요소 업데이트
- 메뉴 액션 실행
- 수신한 식별자/데이터에 따라 로직 실행

# 클라이언트 -> 서버

FancyMenu 액션을 사용합니다.

- **Send FM Data To Server**

액션에는 입력값이 2개 있습니다.

1. 데이터 식별자
2. 데이터

이후 서버에서 `/fmdata listener ...`로 수신 데이터를 처리할 수 있습니다.

# 서버 리스너

서버 리스너는 클라이언트에서 들어오는 데이터를 감지하고, 실행 조건이 충족되면 하나 이상의 명령어를 실행할 수 있습니다.

서버 리스너는 저장되며 서버를 다시 시작한 후에도 활성 상태로 유지됩니다.

다음 명령어로 관리합니다.

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

## 일치 유형

`matching_type_identifier`와 `matching_type_data`에는 다음 값을 사용할 수 있습니다.

- `equals`
- `contains`
- `starts_with`
- `ends_with`

## 일치 규칙

- `ignore_case_identifier`와 `ignore_case_data`는 true/false를 지정하는 옵션입니다.
- `listen_for_identifier`에는 와일드카드 `*`를 사용할 수 있습니다(항상 일치).
- `listen_for_data`에는 와일드카드 `*`를 사용할 수 있습니다(항상 일치).
- `fire_for_player`에는 일반 플레이어 선택자를 사용합니다(예: `@a`, `@p`, `Player761`).

## 실행할 명령어

`commands_to_execute_on_fire`는 텍스트 입력 하나입니다.

- 여러 명령어는 `|||`로 구분합니다.
- 구분 기호를 문자 그대로 사용하려면 `\|\|\|`로 이스케이프합니다.

여기에서 사용할 수 있는 특수 플레이스홀더 두 개는 명령어 실행 직전에 실제 값으로 바뀝니다.

- `%fm_sender%` -> FM Data를 보낸 플레이어
- `%fm_data%` -> 클라이언트에서 수신한 데이터 값

명령어는 서버 명령어로 실행됩니다.

## 명령어 예시

모든 플레이어의 버튼 누름에 반응합니다.

```mcfunction
/fmdata listener add button_ping equals equals false false @a ui.button pressed "tellraw @a {\"text\":\"%fm_sender% pressed the button\"}"
```

데이터에 `gold`가 포함되어 있을 때 여러 명령어를 실행합니다.

```mcfunction
/fmdata listener add reward equals contains false true @a reward "gold" "say Reward from %fm_sender%: %fm_data%|||effect give %fm_sender% minecraft:speed 3 1 true"
```

# 접속 환영 데이터

접속 환영 데이터는 조건에 맞는 플레이어가 서버에 접속할 때 FM Data를 보냅니다.

다음 명령어로 항목을 관리합니다.

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

- `<target_player>`에는 `@a`, `@p`, `@s` 같은 일반 선택자를 사용할 수 있습니다.
- 조건에 맞는 플레이어가 접속하면 데이터가 전송됩니다.
- 항목은 자동으로 저장되고 불러와집니다.

## 명령어 예시

접속하는 모든 플레이어에게 환영 데이터를 보냅니다.

```mcfunction
/fmdata welcome_data add welcome_all @a hud.welcome "Welcome!"
```

플레이어 한 명에게만 환영 데이터를 보냅니다.

```mcfunction
/fmdata welcome_data add welcome_vip Player761 hud.vip "VIP perks enabled"
```

# AI용 내보내기

Alice 또는 다른 AI의 도움을 받으려면 [AI용 내보내기](/export-for-ai#servers)를 사용해 서버 리스너와 접속 환영 데이터를 내보내세요.

```mcfunction
/fmdata export_for_ai copy
/fmdata export_for_ai file
```

`copy`는 클릭하면 내보낸 내용이 복사되는 채팅 메시지를 보냅니다. `file`은 서버의 `fancymenu_data/ai_exports/`에 파일을 저장합니다.

# 권장 사항

1. `hud.food`, `menu.shop.open`, `quest.progress`처럼 의미가 분명한 식별자를 사용합니다.
2. 각 식별자마다 데이터 형식을 일관되게 유지합니다.
3. 복잡한 리스너를 만들기 전에 `/fmdata send`로 간단하게 테스트합니다.
4. 모든 플레이어에게 적용하려는 경우에만 `@a`를 사용합니다.
5. 설정을 깔끔하게 유지하려면 `/fmdata listener list`와 `/fmdata welcome_data list`를 사용합니다.
