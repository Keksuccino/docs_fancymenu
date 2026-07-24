---
title: 액션 스크립트
description: '버튼, 슬라이더, 티커 등과 함께 액션 스크립트를 사용하는 방법.'
---
# 액션 스크립트

액션 스크립트는 [버튼](./elements#button)이 클릭되거나, [티커](./elements#ticker)가 업데이트되거나, [슬라이더](./elements#slider)가 변경되거나, 화면이 열리거나 닫히거나, 또는 다른 지원되는 이벤트가 발생할 때 구성된 작업을 실행합니다. **if**, **else-if**, **else**, **while** 같은 문은 조건 제어를 추가합니다.

> [!CAUTION]
> 가져온 액션 스크립트는 파일을 수정하거나, 서버에 접속하거나, 링크를 열거나, 명령을 실행할 수 있습니다. 신뢰하는 출처의 스크립트만 사용하세요.

<img src="https://github.com/Keksuccino/FancyMenu/blob/master/assets/docs/action_script_editor.png?raw=true" alt="액션 스크립트 편집기" style="max-width:800px;width:100%;height:auto;">

# 액션이란?

**액션**은 트리거될 때 FancyMenu가 실행하는 작업 또는 동작입니다. 예를 들어, 액션은 새 화면을 열거나, 채팅 메시지를 보내거나, [오디오 요소](./elements#audio)의 볼륨을 조절할 수 있습니다. FancyMenu의 편집기에서는 필요한 경우 URL이나 서버 주소 같은 추가 세부 정보를 제공하는 값과 함께 액션을 구성합니다.

# 문(statement)

더 복잡한 동작을 만들기 위해 FancyMenu는 액션 스크립트에서 제어 문을 지원합니다:

| 문 | 동작 |
|---|---|
| **If** | [조건](./conditions)이 충족될 때만 그 액션을 실행합니다. |
| **Else-If** | 앞의 **If** 또는 **Else-If**가 실행되지 않았을 때 다른 [조건](./conditions) 집합을 확인합니다. |
| **Else** | 앞선 **If** 또는 **Else-If** 조건이 모두 충족되지 않았을 때 실행됩니다. |
| **While** | [조건](./conditions)이 참인 동안 그 액션을 반복합니다. 무한 루프를 방지하기 위해 3초 후 중지됩니다. 타이머로 사용하지 마세요. |

# 블록

블록은 스크립트에 추가할 수 있으며, 스크립트 실행 흐름/타이밍을 더 잘 제어할 수 있는 유용한 기능과 편의 기능을 제공합니다:

| 블록 | 동작 |
|---|---|
| **Delay** | 나머지 스크립트를 멈추지 않고 카운트다운을 시작합니다. 중첩된 액션은 지연이 끝난 후 실행 가능해지며, 화면 재초기화 시 카운트다운이 초기화됩니다. |
| **Execute Later** | 블록에 도달할 때마다 지연 후 중첩된 액션의 새 실행을 예약합니다. |
| **Comment** | 정리를 위해 스크립트 안에 메모를 추가하며 액션을 실행하지 않습니다. |

# 스크립트 실행

액션은 위에서 아래로 실행됩니다. 실패한 액션은 로그에 기록되며, 그 다음 스크립트가 계속 진행됩니다.

다운로드, ZIP 압축 해제, HTTP 요청은 나중에 완료되며, 다음 액션은 기다리지 않습니다. 결과가 필요할 때는 [**액션을 통한 파일 다운로드 완료 시**](./listeners#on-file-downloaded-via-action-file_downloaded_via_action), [**액션을 통한 ZIP 압축 해제 완료 시**](./listeners#on-zip-extracted-via-action-zip_extracted_via_action), 또는 HTTP 응답 변수를 사용하세요.

# 액션 스크립트를 어디에 사용할 수 있나요?

액션 스크립트는 다재다능하며 레이아웃 전반에서 사용할 수 있습니다. 예를 들어 다음에 할당할 수 있습니다:

- [**버튼**](./elements#button): 버튼이 클릭될 때 액션을 실행합니다.
- [**티커**](./elements#ticker): 레이아웃 내 화면 정보를 업데이트하기 위해 액션 스크립트를 계속 실행합니다.
- [**슬라이더**](./elements#slider): 슬라이더 값이 변경될 때마다 액션 스크립트를 트리거합니다.
- **화면 이벤트:** 화면이 열리거나 닫힐 때 스크립트를 실행합니다(예: 메뉴가 나타날 때 소리를 재생).
- [**리스너**](./listeners): 리스너가 설정된 이벤트를 받으면 해당 액션 스크립트를 실행합니다.
- [**스케줄러**](./schedulers): 화면이 열려 있지 않아도 시간 기반으로 액션을 실행합니다.

# 액션에서 플레이스홀더 사용하기

액션 값은 **플레이스홀더**를 통해 동적 콘텐츠를 지원합니다. 대부분의 경우 이러한 플레이스홀더는 JSON 유사 구문을 사용하며, 액션이 실행될 때 실시간 데이터로 대체됩니다.

## JSON 유사 플레이스홀더

이들은 레이아웃 전반의 여러 곳에서 사용할 수 있는 일반적인 [플레이스홀더](./placeholders)입니다.

다음과 같은 구문을 따릅니다:

```json
{"placeholder": "placeholder_id", "values": {"key1": "value1", "key2": "value2"}}
```

이들은 플레이어 이름, 화면 크기, 또는 [**Calculator** 플레이스홀더](./placeholders#calculator-calc)를 사용한 계산값 같은 게임 데이터를 가져올 수 있습니다. 더 고급 사용을 위해 플레이스홀더를 중첩할 수도 있습니다.

## `$$` 플레이스홀더(변수)

`$$` 값은 이를 실행하는 기능이 특정 액션 스크립트에 제공하는 읽기 전용 값입니다.

예를 들어, [슬라이더](./elements#slider)는 현재 값을 `$$value`로 제공합니다.

각 [리스너](./listeners)는 눌린 마우스 버튼이나 입력된 구조처럼 자신이 제공하는 `$$` 값을 문서화합니다.

`$$` 이름은 대소문자를 구분하며, 값을 제공하는 스크립트 안에서만 동작합니다. [리스너](./listeners#listener-variables)를 참조하세요.

## 액션 값 구분자

각 액션에 표시된 정확한 구분자 `:`, `||`, `|||`를 사용하세요. 필드 안의 구분자를 이스케이프하는 문법은 없습니다.

플레이스홀더는 값이 분리되기 전에 먼저 치환됩니다. `set_variable`의 경우 첫 번째 콜론만 이름과 값을 나누며, 그 뒤의 콜론은 값의 일부로 남습니다.

## 텍스트 값

[FancyMenu 서식 코드](./text-formatting#minecraft-text-formatting)는 서식 있는 텍스트를 허용하는 모든 액션에서 Minecraft의 `§` 문자 대신 `&`를 사용합니다.

- [**채팅 메시지/명령 보내기**](#send-chat-messagecommand-sendmessage) 및 [**채팅에 붙여넣기**](#paste-to-chat-paste_to_chat)는 이러한 서식 코드를 지원합니다.
- [**채팅에 표시 [클라이언트 측]**](#display-in-chat-client-side-display_in_chat_client_side)는 일반 텍스트 또는 직렬화된 Minecraft 텍스트 컴포넌트 JSON을 허용합니다.
- [**브라우저에서 URL 열기**](#open-url-in-browser-openlink)는 URL을 운영 체제에 전달하기 전에 동일한 서식 코드 변환을 적용합니다.

# 액션 설정 및 편집 방법

요소의 액션과 문 블록을 편집하려면 **요소를 우클릭**하고 **액션 스크립트 관리**를 선택하세요. 편집기에서 다음을 할 수 있습니다:

- **새 액션 또는 문 추가:** 새 액션 항목이나 제어 문(if, else-if, else, while)을 삽입하여 스크립트를 구성합니다.
- **기존 액션 또는 문 편집:** 액션 값을 수정하거나 제어 로직을 변경합니다.
- **액션 또는 문 제거:** 원하지 않는 액션을 스크립트에서 삭제합니다.

리스너 스크립트는 [**사용자 지정 -> 리스너 관리**](./listeners#using-listeners)를 통해 만들고 편집할 수 있습니다.

# 액션 스크립트 편집기 단축키

## 단축키

- `DEL` : 선택한 항목을 빠르게 삭제
- `ENTER` : 선택한 항목의 인라인 편집을 시작함(또는 선택한 항목에 인라인 편집이 없으면 편집 화면을 염)
- `Ctrl/Command + C` : 선택한 액션을 복사함(현재는 액션에만 동작)
- `Ctrl/Command + V` : 이전에 복사한 액션을 붙여넣음
- `Ctrl/Command + Z` : 한 단계 뒤로(실행 취소)
- `Ctrl/Command + Y` : 한 단계 앞으로(다시 실행)
- `ARROW UP` : 현재 선택된 항목에서 한 칸 위로 이동
- `ARROW DOWN` : 현재 선택된 항목에서 한 칸 아래로 이동
- `SHIFT + ARROW UP` : 선택한 항목을 한 칸 위로 이동
- `SHIFT + ARROW DOWN` : 선택한 항목을 한 칸 아래로 이동
- `A` : 액션 선택 화면을 빠르게 열어 새 액션 추가
- `Ctrl/Command + S` : 편집기 창에서 완료/저장

## 편집

- 액션 값을 더블클릭하면 전체 값 편집 화면으로 가지 않고도 값을 편집할 수 있습니다.
- IF 문 체인(뒤에 ELSE/ELSE-IF가 붙은 경우), WHILE 루프, 폴더는 접을 수 있습니다(시각적 기능일 뿐이며 스크립트 로직에는 영향을 주지 않음).
- 편집기는 항상 선택한 항목 아래에 새 액션을 추가합니다(또는 선택한 체인/루프/폴더 안에 중첩하여 추가).
- 짙은 회색 스크립트 영역 배경을 우클릭하면 액션, 문, 기타 중요한 항목을 추가할 수 있는 컨텍스트 메뉴가 열립니다.

# 액션 상세

이 섹션은 FancyMenu의 기본 제공 액션을 나열합니다.

## 다음 트랙 (`audio_next_track`)

**목적:** [오디오 요소](./elements#audio)에서 다음 트랙으로 이동합니다.

**값:** 필요 — `audio_element_identifier`(제어할 오디오 요소의 ID)

## 이전 트랙 (`audio_previous_track`)

**목적:** [오디오 요소](./elements#audio)에서 이전 트랙으로 이동합니다.

**값:** 필요 — `audio_element_identifier`(제어할 오디오 요소의 ID)

## 트랙 볼륨 설정 (`set_audio_element_volume`)

**목적:** [오디오 요소](./elements#audio)의 볼륨을 설정합니다(`0.0` ~ `1.0`)

**값:** 필요 — `element_identifier:volume`

## 재생/일시정지 토글 (`audio_toggle_play`)

**목적:** [오디오 요소](./elements#audio)의 현재 트랙을 재생과 일시정지 사이로 전환합니다.

**값:** 필요 — `audio_element_identifier`

## 오디오 재생 (`play_audio`)

**목적:** 오디오 리소스를 한 번 재생합니다. 이 액션으로 시작된 오디오는 나중에 [**모든 액션 오디오 중지**](#stop-all-action-audios-stop_all_action_audios)로 중지할 수 있습니다.

**값:** 필요 — `audioSource`, `soundChannel`, `baseVolume`이 포함된 JSON 구성

**예시:** `{"audioSource":"[source:local]/config/fancymenu/assets/example.ogg","soundChannel":"master","baseVolume":1.0}`

**동작:**

- `baseVolume`은 `0.0`~`1.0`으로 제한됩니다.
- 알 수 없는 사운드 채널은 Master 채널을 사용합니다.
- 이 액션은 비동기 [티커](./elements#ticker)에서 실행할 수 없으며, FancyMenu는 대신 오류를 표시합니다.
- FancyMenu는 오디오 리소스가 준비될 때까지 최대 10초 동안 기다립니다.
- 성공적으로 시작된 트랙은 [**모든 액션 오디오 중지**](#stop-all-action-audios-stop_all_action_audios)로 중지할 수 있습니다.

## 모든 액션 오디오 중지 (`stop_all_action_audios`)

**목적:** [**오디오 재생** 액션](#play-audio-play_audio)으로 시작된 모든 오디오 트랙을 중지합니다. 이는 [오디오 요소](./elements#audio), 메뉴 열기/닫기 소리, 버튼 소리, 또는 다른 오디오 시스템은 중지하지 않습니다.

**값:** 필요 없음

## 비디오 요소 볼륨 설정 (`set_video_element_volume`)

**목적:** [비디오 요소](./video)의 볼륨을 설정합니다(`0.0` ~ `1.0`)

**값:** 필요 — `video_element_identifier:volume`

## 비디오 요소 재생 시간 설정 (`set_video_element_play_time`)

**목적:** [비디오 요소](./video)를 밀리초 타임스탬프로 이동합니다.

**값:** 필요 — `video_element_identifier:timestamp_ms`

## 비디오 요소 일시정지 상태 토글 (`toggle_video_element_pause_state`)

**목적:** [비디오 요소](./video)의 일시정지 상태를 전환합니다.

**값:** 필요 — `video_element_identifier`

## 비디오 배경 볼륨 설정 (`set_video_menu_background_volume`)

**목적:** [비디오 메뉴 배경](./video)의 볼륨을 설정합니다(`0.0` ~ `1.0`)

**값:** 필요 — `background_identifier:volume`

> [!NOTE]
> 배경의 식별자를 얻으려면 편집기 배경을 우클릭한 다음 '배경 식별자 복사'를 클릭하세요.

## 비디오 배경 재생 시간 설정 (`set_video_menu_background_play_time`)

**목적:** [비디오 메뉴 배경](./video)를 밀리초 타임스탬프로 이동합니다.

**값:** 필요 — `background_identifier:timestamp_ms`

> [!NOTE]
> 배경의 식별자를 얻으려면 편집기 배경을 우클릭한 다음 '배경 식별자 복사'를 클릭하세요.

## 비디오 배경 일시정지 상태 토글 (`toggle_video_menu_background_pause_state`)

**목적:** [비디오 메뉴 배경](./video)의 일시정지 상태를 전환합니다.

**값:** 필요 — `background_identifier`

> [!NOTE]
> 배경의 식별자를 얻으려면 편집기 배경을 우클릭한 다음 '배경 식별자 복사'를 클릭하세요.

## 레이아웃 전환 (`toggle_layout`)

**목적:** `.txt`를 제외한 파일 이름으로 레이아웃을 활성화/비활성화합니다.

**값:** 필요 — `layout_name`

## 레이아웃 활성화 (`enable_layout`)

**목적:** `.txt`를 제외한 파일 이름으로 레이아웃을 활성화하고 저장합니다.

**값:** 필요 — `layout_name`

## 레이아웃 비활성화 (`disable_layout`)

**목적:** `.txt`를 제외한 파일 이름으로 레이아웃을 비활성화하고 저장합니다.

**값:** 필요 — `layout_name`

세 가지 레이아웃 액션은 모두 상태를 레이아웃 파일에 저장하고 현재 화면을 즉시 업데이트합니다. 대소문자를 구분하는 `.txt` 없는 파일 이름을 사용하세요.

## 화면 또는 사용자 지정 GUI 열기 (`opengui`)

**목적:** 식별자로 화면(바닐라, 모드, 또는 사용자 지정 GUI)을 엽니다.

**값:** 필요 — `screen_identifier`

[Screen Identifiers](./screen-identifiers) 디버그 오버레이에서 정확한 대소문자 구분 식별자를 복사하세요.

일부 모드 화면은 직접 생성할 수 없습니다. 열기에 실패하면 보통 해당 화면을 여는 위젯에 [**바닐라/모드 버튼 모방**](#mimic-vanillamod-button-mimicbutton)을 사용하세요.

## 화면 닫기 (`closegui`)

**목적:** 현재 활성 화면을 닫습니다.

**값:** 필요 없음

## 화면 업데이트 (`update_screen`)

**목적:** 현재 화면을 다시 초기화합니다.

**값:** 필요 없음

## 마지막 화면으로 돌아가기 (`back_to_last_screen`)

**목적:** [사용자 지정 GUI](./custom-guis)의 부모로 돌아가거나, 가장 최근에 닫힌 화면 인스턴스로 돌아갑니다.

**값:** 필요 없음

## 서버 접속 (`joinserver`)

**목적:** 플레이어를 Minecraft 서버에 연결합니다.

**값:** 필요 — `server_ip` 또는 `server_ip:port`

이 액션은 월드 또는 서버가 이미 로드된 상태에서는 실행할 수 없습니다. 포트는 생략 시 `25565`를 사용합니다. 주소가 Minecraft 저장 서버 목록에 없으면 FancyMenu가 추가하고 저장합니다.

## 월드 들어가기 (`loadworld`)

**목적:** Minecraft 월드에 들어갑니다.

**값:** 필요 — `world_folder_name`

값은 저장 폴더 이름입니다. 해당 저장이 없거나 다른 월드/서버가 이미 로드되어 있으면 아무 동작도 하지 않습니다.

## 마지막 월드/서버로 들어가기/접속 (`join_last_world`)

**목적:** 플레이어가 마지막으로 있었던 월드 또는 서버에 들어가거나 접속합니다.

**값:** 필요 없음

이 액션은 다른 월드/서버가 로드된 상태에서는 실행할 수 없습니다. Minecraft 저장 서버 목록에 없는 기억된 서버는 연결 전에 추가되고 저장됩니다.

## 월드 또는 서버 나가기 (`disconnect_server_or_world`)

**목적:** 월드 또는 서버를 나가고 지정된 화면을 엽니다.

**값:** 필요 — `screen_identifier`

이 액션은 월드와 플레이어가 로드된 상태에서만 동작합니다. 대상은 [사용자 지정 GUI](./custom-guis) 식별자이거나 FancyMenu가 구성할 수 있는 [화면 식별자](./screen-identifiers)일 수 있습니다. 대상이 열리지 않으면 FancyMenu는 타이틀 화면으로 돌아갑니다.

## Minecraft 종료 (`quitgame`)

**목적:** Minecraft를 완전히 종료합니다.

**값:** 필요 없음

## 채팅 메시지/명령 보내기 (`sendmessage`)

**목적:** 채팅 메시지를 보내거나 채팅 명령을 실행합니다. 메시지 텍스트는 [FancyMenu 서식 코드](./text-formatting#minecraft-text-formatting)를 지원합니다.

**값:** 필요 — `message_text` 또는 `/command_text`

## 통합 서버로 명령 실행 (`execute_command_as_integrated_server`)

**목적:** 싱글플레이에서 통합 서버로 명령을 강제 실행하며, 권한과 치트 설정을 무시합니다.

**값:** 필요 — 명령 텍스트, 예: `/give @p minecraft:diamond 1`

> [!WARNING]
> 이 액션은 월드가 **LAN에 공개되지 않은** 싱글플레이에서만 동작합니다. 통합 서버가 없거나, 통합 서버가 LAN에 공개된 경우에는 의도적으로 아무 동작도 하지 않습니다.

## 채팅에 붙여넣기 (`paste_to_chat`)

**목적:** 플레이어/월드가 로드된 상태에서 채팅 입력칸에 서식 있는 텍스트를 붙여넣습니다.

**값:** 필요 — `true:Text` 또는 `false:Text`

채팅이 아직 열려 있지 않으면 FancyMenu가 채팅을 열고 입력 텍스트를 설정합니다. 채팅이 이미 열려 있으면 `true`는 기존 입력에 추가하고 `false`는 교체합니다.

## 채팅에 표시 [클라이언트 측] (`display_in_chat_client_side`)

**목적:** 월드 또는 서버가 로드된 상태에서 클라이언트 측 채팅 메시지를 표시합니다. 서버로는 아무 것도 전송하지 않습니다.

**값:** 필요 — `text_or_json`

값은 일반 텍스트 또는 직렬화된 Minecraft 텍스트 컴포넌트일 수 있습니다. 월드가 로드되지 않았으면 이 액션은 아무 동작도 하지 않습니다.

## FM 데이터 서버로 보내기 (`send_fm_data_to_server`)

**목적:** 현재 FancyMenu 서버로 [FM 데이터](./fm-data)를 보냅니다.

**값:** 필요 — `data_identifier||data`

## 원격 서버에 연결 (`connect_to_remote_server`)

**목적:** 외부 원격 서버와 클라이언트가 시작한 WebSocket 연결을 열거나 재사용합니다.

**값:** 필요 — 원격 서버 URL, 예: `wss://example.com/ws`

허용되는 URL 형식은 [원격 서버 통신](./remote-server-communication#url-modes)을 참조하세요.

## 원격 서버에 데이터 보내기 (`send_data_to_remote_server`)

**목적:** 원격 서버 연결을 열거나 재사용하고 텍스트 데이터를 보냅니다.

**값:** 필요 — `remote_server_url||data`

## 원격 서버 연결 닫기 (`close_remote_server_connection`)

**목적:** 요청 ID로 특정 원격 서버 연결을 닫습니다.

**값:** 필요 — 요청 ID, 보통 [**원격 서버 연결 시**](./listeners#on-remote-server-connected-remote_server_connected)의 `$$request_id`

## 모든 원격 서버 연결 닫기 (`close_all_remote_server_connections`)

**목적:** FancyMenu가 연 모든 활성 원격 서버 연결을 닫습니다.

**값:** 필요 없음

## 브라우저에서 URL 열기 (`openlink`)

**목적:** FancyMenu 확인 프롬프트 없이 URL을 운영 체제의 기본 처리기로 전달합니다.

**값:** 필요 — `https://example.com`

신뢰할 수 있는 `https://` 링크를 사용하세요. FancyMenu는 URL을 운영 체제에 전달하기 전에 확인 프롬프트를 표시하지 않습니다.

## 텍스트를 클립보드에 복사 (`copytoclipboard`)

**목적:** 텍스트를 클립보드에 복사합니다.

**값:** 필요 — `text_to_copy`

## 게임 로그에 출력 (`print_to_log`)

**목적:** 게임 로그에 한 줄을 씁니다.

**값:** 필요 — `text_to_log`

## 변수 값 설정 (FM 변수) (`set_variable`)

**목적:** 텍스트 콘텐츠를 [FancyMenu 변수](./variables)에 저장합니다.

**값:** 필요 — `variable_name:variable_value`

첫 번째 콜론이 이름과 값을 구분합니다. 이후의 콜론은 값의 일부로 남습니다. 변경 사항은 즉시 저장됩니다.

## 모든 변수 지우기 (FM 변수) (`clear_variables`)

**목적:** 저장된 모든 [FancyMenu 변수](./variables) 값을 지웁니다.

**값:** 필요 없음

## HTTP 요청 보내기 (`send_http_request`)

**목적:** 백그라운드에서 HTTP/HTTPS 요청을 시작합니다. 응답을 로그에 기록하거나 변수에 저장할 수 있습니다.

**값:** 필요 — HTTP 요청 구성

| 설정 | 동작 |
|---|---|
| URL | HTTP 또는 HTTPS 엔드포인트 |
| Method | `GET`, `POST`, `PUT`, `DELETE`, `PATCH`, `HEAD`, 또는 `OPTIONS` |
| Body | `GET`과 `HEAD`를 제외한 메서드에 대해 전송됨 |
| Content type | 요청의 `Content-Type` 값 |
| Timeout | 연결 및 응답 읽기에 모두 사용되는 초 단위 시간 |
| Log response | 응답을 읽어 로그에 기록 |
| Response variable | 요청 완료 후 응답을 읽어 저장 |
| Single-line response | 저장 전에 응답의 줄바꿈 제거 |
| Authentication | 없음, Basic, Bearer, 또는 API key |
| Headers | 선택적 사용자 지정 요청 헤더 |

요청은 비동기적으로 실행되므로 다음 액션은 기다리지 않습니다. 응답 본문은 로깅이 활성화되었거나 응답 변수가 설정된 경우에만 읽습니다. 성공하지 못한 경우의 본문은 오류 응답에서 읽습니다. 액션 구성에 비밀번호나 액세스 토큰을 저장하지 마세요.

## 리소스 팩 관리 (`manage_resource_pack`)

**목적:** 선택적으로 다시 로드하면서 리소스 팩을 활성화, 비활성화 또는 전환합니다.

**값:** 필요 — `pack_name_or_id|||MODE|||reload_bool`

표시 이름과 내부 팩 ID는 대소문자를 구분하지 않고 일치시킵니다. 필수로 표시된 팩은 비활성화할 수 없습니다.

## 리소스 팩 다시 로드 (`reload_resource_packs`)

**목적:** Minecraft의 리소스 팩을 다시 로드합니다. 내장된 5초 쿨다운이 있어, 그동안 반복 트리거는 무시되어 다시 로드가 과도하게 발생하는 것을 방지합니다.

**값:** 필요 없음

## FancyMenu 다시 로드 (`reloadmenu`)

**목적:** 레이아웃, [사용자 지정 GUI](./custom-guis), [파노라마](./panoramas), [슬라이드쇼](./slideshows), 설정, 그리고 FancyMenu가 관리하는 리소스를 다시 로드합니다.

**값:** 필요 없음

이 작업은 Minecraft 리소스 팩을 다시 로드하지 않습니다. 그 경우에는 [**리소스 팩 다시 로드**](#reload-resource-packs-reload_resource_packs)를 사용하세요.

> [!WARNING]
> 다시 로드는 비용이 큰 작업입니다. [티커](./elements#ticker)나 자주 발동하는 [리스너](./listeners)가 아니라, 의도적으로 누르는 버튼 액션에서 트리거하세요.

## 요소 애니메이터 전환 (`toggle_element_animator`)

**목적:** 저장된 재생 상태를 전환하고 일치하는 활성 Animator 타임라인을 재설정합니다.

**값:** 필요 — `animator_identifier`

설정과 식별자 정보는 [Element Animator](./element-animator)를 참조하세요.

## 요소 애니메이터 활성화 (`enable_element_animator`)

**목적:** 재생을 활성화합니다. 활성 Animator 타임라인은 상태가 비활성에서 활성으로 바뀔 때만 재설정됩니다.

**값:** 필요 — `animator_identifier`

## 요소 애니메이터 비활성화 (`disable_element_animator`)

**목적:** 재생을 비활성화하고 일치하는 활성 Animator 타임라인을 재설정합니다.

**값:** 필요 — `animator_identifier`

## 요소 애니메이터 재설정 (`reset_element_animator`)

**목적:** 재생 활성 여부는 유지한 채 일치하는 활성 Animator 타임라인을 재설정합니다.

**값:** 필요 — `animator_identifier`

## 바닐라/모드 버튼 모방 (`mimicbutton`)

**목적:** 바닐라 또는 모드 버튼의 클릭 동작을 모방합니다.

**값:** 필요 — 전체 [위젯 로케이터](./widget-locators), 예: `example.menu.identifier:505280`

## 키 바인드 모방 (`mimic_keybind`)

**목적:** Minecraft 키보드 또는 마우스 키 바인드를 실행하며, 선택적으로 누른 상태를 유지할 수 있습니다.

**값:** 필요 — `keybind_id|||keep_pressed_bool|||duration_ms`

| 필드 | 의미 |
|---|---|
| `keybind_id` | `key.jump` 같은 Minecraft 키 바인드 식별자 |
| `keep_pressed_bool` | 키를 누른 상태로 유지하려면 `true`, 일반 누름은 `false` |
| `duration_ms` | `keep_pressed_bool`가 `true`일 때의 유지 시간; 기본값은 `1000` |

## 텍스트 입력 필드 값 설정 (`set_text_input_field_value`)

**목적:** 요소 식별자로 사용자 지정 또는 바닐라 [텍스트 입력 필드](./elements#text-input-field)의 값을 설정합니다.

**값:** 필요 — `element_identifier|||new_value|||force_set_when_inactive`

세 필드는 삼중 파이프 구분자 `|||`로 구분해야 합니다. 비활성화된 입력 필드도 업데이트하려면 `force_set_when_inactive`를 `true`로 설정하세요. `false`이면 비활성 필드는 변경되지 않습니다.

## 게임 디렉터리에 파일 생성 (`create_file_in_game_dir`)

**목적:** 활성 게임 디렉터리를 기준으로 빈 파일을 생성합니다. 일반적인 Minecraft 디렉터리(.minecraft/)를 대상으로 하려면 `.minecraft/` 접두사를 사용할 수 있습니다(현재 인스턴스와 다를 수 있음).

**값:** 필요 — `file_path`

예: `config/some_mod_folder/new_file.txt`. 상위 디렉터리가 없으면 생성되며, 기존 파일은 변경되지 않습니다.

## 게임 디렉터리의 파일/폴더 삭제 (`delete_file_in_game_dir`)

**목적:** 활성 게임 디렉터리를 기준으로 파일을 삭제하거나 폴더를 재귀적으로 삭제합니다. 일반적인 Minecraft 디렉터리를 대상으로 하려면 `.minecraft/`를 사용할 수 있습니다. 폴더 바로 안의 **모든 파일만** 삭제하려면 경로 끝에 `*`를 붙이세요(하위 디렉터리는 무시하고 폴더는 유지됨).

**값:** 필요 — `target_path`

예를 들어 `config/downloads/*`는 `config/downloads/` 바로 안의 파일만 삭제하며, 하위 디렉터리는 탐색하거나 삭제하지 않습니다.

## 게임 디렉터리의 파일/폴더 복사 (`copy_file_in_game_dir`)

**목적:** 활성 게임 디렉터리 내에서 복사합니다. `.minecraft/`는 일반적인 Minecraft 디렉터리를 대상으로 합니다. 이름이 있는 디렉터리는 재귀적으로 복사됩니다. **소스** 경로 끝에 `*`를 붙이면 바로 아래 자식 파일만 모두 복사하며, 대상은 디렉터리여야 하고 `*`를 사용할 수 없습니다.

**값:** 필요 — `source||destination`

예를 들어 `config/source/*||config/destination/`는 `config/source/` 바로 안의 파일만 복사합니다. 와일드카드 소스를 사용할 때 FancyMenu는 필요하면 대상 디렉터리를 만들지만, 소스 하위 디렉터리는 복사하지 않습니다. 복사는 기존 대상이나 충돌하는 파일을 덮어쓰지 않고 거부합니다.

## 게임 디렉터리의 파일/폴더 이동 (`move_file_in_game_dir`)

**목적:** 활성 게임 디렉터리 내에서 이동합니다. `.minecraft/`는 일반적인 Minecraft 디렉터리를 대상으로 합니다. **소스** 경로 끝에 `*`를 붙이면 바로 아래 자식 파일만 모두 이동하며, 대상은 디렉터리여야 하고 `*`를 사용할 수 없습니다.

**값:** 필요 — `source||destination`

예를 들어 `config/source/*||config/destination/`는 `config/source/` 바로 안의 파일만 이동합니다. 와일드카드 소스를 사용할 때 FancyMenu는 필요하면 대상 디렉터리를 만들지만, 소스 하위 디렉터리는 그대로 둡니다. 이동은 기존 대상이나 충돌하는 파일을 덮어쓰지 않고 거부합니다.

## 게임 디렉터리의 파일/폴더 이름 바꾸기 (`rename_file_in_game_dir`)

**목적:** 현재 상위 디렉터리 안에서 파일 또는 폴더의 이름을 바꿉니다. `.minecraft/`는 일반적인 Minecraft 디렉터리를 대상으로 합니다. 내용은 그대로 유지되며 기존 대상 이름은 거부됩니다.

**값:** 필요 — `path||new_name`

## 게임 디렉터리로 파일 다운로드 (`download_file_to_game_dir`)

**목적:** 활성 게임 디렉터리를 기준으로 한 디렉터리에 백그라운드로 파일을 다운로드합니다. `.minecraft/`는 일반적인 Minecraft 디렉터리를 대상으로 합니다.

**값:** 필요 — `url||target_folder`

두 번째 필드는 완전한 대상 파일 경로가 아니라 **대상 디렉터리**입니다. FancyMenu는 필요하면 디렉터리를 만들고, 응답의 `Content-Disposition` 헤더에서 파일 이름을 결정한 뒤, 없으면 URL 경로를 사용합니다. 해석된 이름은 사용 전에 URL 디코딩 및 정리됩니다. 어느 쪽에서도 사용할 수 있는 이름을 얻지 못하면 FancyMenu가 새 이름을 생성합니다. 같은 이름의 기존 파일은 덮어씁니다.

[**액션을 통한 파일 다운로드 완료 시** 리스너](./listeners#on-file-downloaded-via-action-file_downloaded_via_action)는 성공 및 실패한 다운로드 시도 후 모두 실행되며, URL, 해석된 대상 경로, 성공 상태를 노출합니다.

성공 시 `$$target_file_path`는 저장된 파일 경로입니다. 실패 시 최종 파일 이름이 해석되지 않아 대상 디렉터리만 포함할 수도 있습니다.

## 게임 디렉터리에서 ZIP 파일 압축 해제 (`extract_zip_file_in_game_dir`)

**목적:** 활성 게임 디렉터리 또는 일반 `.minecraft` 디렉터리 안의 대상 폴더로 ZIP을 압축 해제합니다. 완료되면 [**액션을 통한 ZIP 압축 해제 완료 시**](./listeners#on-zip-extracted-via-action-zip_extracted_via_action)를 트리거합니다.

**값:** 필요 — `source_zip_path||target_folder_path`

이름이 같은 기존 파일은 교체됩니다. 신뢰할 수 있는 ZIP 파일만 압축 해제하세요.

## 게임 디렉터리에서 파일/폴더 열기 (`open_file_folder_in_game_dir`)

**목적:** 파일 또는 폴더를 운영 체제의 기본 앱으로 엽니다. 보안상의 이유로 대상은 게임 디렉터리 또는 기본 `.minecraft` 디렉터리 안에 있어야 합니다.

**값:** 필요 — `target_path`

## 게임 디렉터리에 파일 쓰기 (`write_file_in_game_dir`)

**목적:** 활성 게임 디렉터리를 기준으로 텍스트를 쓰거나 덧붙입니다. `.minecraft/`는 일반적인 Minecraft 디렉터리를 대상으로 합니다. 파일과 상위 디렉터리가 없으면 생성합니다. `\n`은 줄바꿈을 삽입합니다. `append_bool=false`이면 기존 파일을 교체합니다.

**값:** 필요 — `path|||content|||append_bool`

## 시스템에서 파일 선택 (`select_file_to_game_dir`)

**목적:** 기본 파일 선택기를 열고 선택한 파일을 활성 게임 디렉터리 안으로 복사합니다. `.minecraft/` 접두사를 사용하면 일반적인 `.minecraft/`를 대상으로 합니다. 확장자 필터, 사용자 지정 필터 레이블, 덮어쓰기 토글을 지원합니다.

**값:** 필요 — `target_path|||filter_description|||extensions|||overwrite_bool`

`target_path`는 완전한 대상 파일 경로입니다. 여러 확장자는 `;` 또는 `,`로 구분하세요. 예: `png;jpg`. 확장자 목록이 비어 있으면 모든 파일이 허용됩니다. `overwrite_bool`이 `false`이면 기존 대상 파일을 교체하지 않고 실패합니다.

[**파일 선택 시** 리스너](./listeners#on-file-selected-file_selected_via_action)는 파일이 복사되거나, 선택이 취소되거나, 선택에 실패했을 때 실행됩니다. 선택된 경로, 해석된 대상 경로, 성공/취소 상태, 실패 이유를 제공합니다.

## 토스트 표시 (`show_toast`)

**목적:** 구성 가능한 토스트 알림을 표시합니다.

**값:** 필요 — JSON 토스트 구성

편집기는 이 액션을 JSON으로 저장합니다. 값을 수동으로 편집하기보다 구성 창을 사용하는 것이 좋습니다.

| 필드 | 의미 |
|---|---|
| `width` | `120`~`320`픽셀로 제한됨 |
| `durationMs` | `1000`~`600000`밀리초로 제한됨 |
| `title` | 일반 텍스트, 직렬화된 Minecraft 텍스트 컴포넌트, 또는 비어 있음 |
| `message` | 일반 텍스트, 직렬화된 텍스트 컴포넌트, 또는 비어 있음 |
| `iconSource` | 선택적 [이미지 소스](./resources) |
| `backgroundSource` | 선택적 [이미지 소스](./resources) |

## 스케줄러 시작 (`start_scheduler`)

**목적:** 스케줄러 ID로 스케줄러를 시작합니다.

**값:** 필요 — `scheduler_id`

스케줄러 ID 생성 및 관리는 [스케줄러](./schedulers)를 참조하세요.

## 스케줄러 중지 (`stop_scheduler`)

**목적:** 스케줄러 ID로 스케줄러를 중지합니다.

**값:** 필요 — `scheduler_id`

## Minecraft 옵션 설정 (`edit_minecraft_option`)

**목적:** Minecraft 구성 옵션을 편집합니다.

**값:** 필요 — `option_name:set_to_value`
