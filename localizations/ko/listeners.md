---
title: 리스너
description: FancyMenu에서 리스너를 생성하고 사용하는 방법입니다.
---

# 리스너

FancyMenu v3.8.0부터 "리스너"라는 새로운 기능이 추가되었습니다.

리스너는 특정 클라이언트 또는 게임플레이 이벤트가 발생할 때 액션 스크립트를 실행합니다.
또한 리스너 안에 중첩된 액션, 플레이스홀더, 요구사항에서 사용할 수 있는 변수를 제공할 수 있습니다.

FancyMenu의 대부분 기능과 달리, 리스너는 화면이나 오버레이에 묶여 있지 않습니다. 이들은 백그라운드에서 계속 실행되며, 이벤트를 감지합니다. 리스너가 발동되는 즉시, 그 시점에 화면이 열려 있지 않더라도 액션 스크립트를 실행합니다.

# 리스너 사용하기

이벤트를 감지하고 액션 스크립트를 실행하는 새 리스너를 만들려면, **레이아웃 편집기 밖에서** **메뉴 바 -> 사용자 지정 -> 리스너 관리**를 클릭하세요. 여기에서 리스너를 쉽게 생성하고 관리할 수 있는 UI를 사용할 수 있습니다.

<img src="https://github.com/Keksuccino/FancyMenu/blob/master/assets/docs/manage_listeners.png?raw=true" alt="리스너 관리" style="max-width:800px;width:100%;height:auto;">

# 리스너 변수

리스너는 종종 내부에 중첩된 액션, 요구사항, 플레이스홀더에서 사용할 수 있는 특별한 유형의 변수를 제공합니다.
이 변수들은 플레이스홀더처럼 접근할 수 있습니다(사실상 플레이스홀더와 같습니다).

이 변수들은 텍스트 입력란에서 이름 앞에 `$$` 접두사를 붙여 사용합니다. 일반적인 플레이스홀더를 사용하는 방식과 비슷합니다.

예를 들어, **키보드 키 눌림 시** 리스너를 사용하고, **로그에 출력** 액션으로 키 이름을 로그에 출력하고 싶다면, 액션이 출력할 메시지 입력값으로 `키가 눌렸습니다! 키는: $$key_name` 같은 형식을 사용하면 됩니다. 그러면 변수 플레이스홀더가 나중에 실제 키 이름으로 치환됩니다.

> 이들은 "변수"라고 불리지만, FancyMenu의 일반 [변수 시스템](/variables)과는 전혀 관련이 없습니다. 이 변수들은 **읽기 전용**이므로 값을 설정할 수 없습니다. 또한 FancyMenu의 변수 시스템을 위한 액션, 요구사항, 플레이스홀더는 이 특별한 리스너 변수에 사용할 수 없습니다. 따라서 **변수 값 가져오기 [FM Variable]**, **변수 값인지 확인 [FM Variable]**, **변수 값 설정 [FM Variable]**은 리스너 변수에 대해 작동하지 않습니다.
{.is-warning}

# 리스너 상세

이 목록에는 FancyMenu의 리스너 대부분이 포함되어 있습니다. 모드 업데이트로 인해 목록이 항상 최신이 아닐 수 있습니다.

## 마크다운 텍스트 클릭 시
- `click:` 이벤트가 있는 마크다운 텍스트를 클릭하면 발동합니다. 예: `[Open](click:open_menu)`.
- 변수:
  - `$$text_event_id` – 마크다운 링크의 이벤트 ID

## 마크다운 텍스트에 마우스 오버 시
- `hover:` 이벤트가 있는 마크다운 텍스트에 마우스를 올리면 발동합니다. 예: `[Hint](hover:show_hint)`.
- 변수:
  - `$$text_event_id` – 마크다운 링크의 이벤트 ID

## 액션을 통해 ZIP 압축 해제 완료 시
- **게임 디렉터리에 ZIP 파일 추출** 액션이 끝나면 발동합니다.
- 변수:
  - `$$source_zip_path` – 확인된 원본 ZIP 경로
  - `$$target_folder_path` – 확인된 압축 해제 대상 경로
  - `$$extract_succeeded` – true/false
  - `$$failure_reason` – 압축 해제 실패 시 오류 텍스트

## 요소 생성 시
- 액션/스크립트화된 요소 생성 흐름을 통해 요소가 생성되면 발동합니다.
- 변수:
  - `$$element_type` – 생성된 요소 유형
  - `$$element_identifier` – 생성된 요소 식별자
  - `$$target_screen` – 대상 화면 식별자

## 애니메이션 텍스처 재생 시작 시
- 애니메이션 텍스처가 재생을 시작하면 발동합니다.
- 변수:
  - `$$texture_source` – 텍스처 소스
  - `$$texture_source_type` – 소스 유형
  - `$$texture_will_restart` – true/false

## 애니메이션 텍스처 재생 종료 시
- 애니메이션 텍스처 재생이 끝나면 발동합니다.
- 변수:
  - `$$texture_source`
  - `$$texture_source_type`
  - `$$texture_will_restart`

## 비디오 재생 상태 변경 시
- 비디오 요소 또는 비디오 메뉴 배경의 재생 상태가 변경되면 발동합니다.
- 변수:
  - `$$video_source` – 비디오 소스
  - `$$video_source_type` – 소스 유형
  - `$$is_looping` – true/false
  - `$$new_status` – `PLAYING`, `STOPPED`, `PAUSED`, 또는 `FINISHED`

## 채팅에서 시스템 메시지 수신 시
- 명령 피드백과 같은 시스템 채팅 메시지를 클라이언트가 받으면 발동합니다.
- 변수:
  - `$$system_message_string` – 일반 텍스트 메시지
  - `$$system_message_component` – JSON 컴포넌트

## FM 데이터 수신 시
- 서버가 `/fmdata send`를 통해 이 클라이언트로 FM 데이터를 보내면 발동합니다.
- 변수:
  - `$$data_identifier` – 데이터 식별자 문자열
  - `$$data` – 데이터 페이로드
  - `$$sent_by` – 서버 IP 또는 `integrated_server`

## 원격 서버 연결 시
- FancyMenu가 원격 서버 연결을 초기화하면 발동합니다.
- 변수:
  - `$$request_id` – 캐시된 요청 ID
  - `$$remote_server_url` – 원격 서버 URL

## 원격 서버 데이터 수신 시
- 연결된 원격 서버로부터 텍스트 데이터가 수신되면 발동합니다.
- 변수:
  - `$$request_id` – 요청 ID
  - `$$remote_server_url` – 원격 서버 URL
  - `$$data` – 수신된 페이로드

## 원격 서버 연결 종료 시
- 원격 서버 연결이 종료되면 발동합니다.
- 변수:
  - `$$request_id` – 요청 ID
  - `$$remote_server_url` – 원격 서버 URL
  - `$$intentionally_closed` – 액션으로 인해 종료되었으면 TRUE
  - `$$crashed` – 연결이 예기치 않게 충돌했으면 TRUE
  - `$$unknown_close_reason` – 알려진 종료 이유가 없으면 TRUE

## 키보드 키 눌림 시
- 키를 누를 때마다 발동합니다(누르고 있는 동안 반복됨; 화면 안과 게임 내 모두에서 작동).
- 변수:
  - `$$key_name` – 키 표시 이름
  - `$$key_keycode` – GLFW 키 코드
  - `$$key_scancode` – GLFW 스캔 코드
  - `$$key_modifiers` – 활성 수정 키 비트 마스크

## 키보드 키 뗌 시
- 키에서 손을 뗄 때 발동합니다(화면 안과 게임 내 모두에서 작동).
- 변수:
  - `$$key_name`
  - `$$key_keycode`
  - `$$key_scancode`
  - `$$key_modifiers`

## 화면에서 키보드 문자 입력 시
- 화면이 열려 있을 때 문자를 입력하면 발동합니다.
- 변수:
  - `$$char` – 입력된 문자

## 화면에서 마우스 이동 시
- 화면이 열려 있는 동안 마우스가 움직일 때마다 발동합니다.
- 변수:
  - `$$mouse_pos_x` – 현재 X
  - `$$mouse_pos_y` – 현재 Y
  - `$$mouse_move_delta_x` – 마지막 이벤트 이후 X 변화량
  - `$$mouse_move_delta_y` – 마지막 이벤트 이후 Y 변화량

## 마우스 버튼 클릭 시
- 마우스 버튼을 누르면 발동합니다(화면 안과 게임 내 모두에서 작동).
- 변수:
  - `$$button` – 왼쪽/오른쪽/가운데
  - `$$mouse_pos_x` – 현재 X
  - `$$mouse_pos_y` – 현재 Y

## 마우스 버튼 뗌 시
- 마우스 버튼에서 손을 떼면 발동합니다(화면 안과 게임 내 모두에서 작동).
- 변수:
  - `$$button`
  - `$$mouse_pos_x`
  - `$$mouse_pos_y`

## 화면에서 마우스 휠 스크롤 시
- 화면이 열려 있을 때 마우스 휠을 스크롤하면 발동합니다.
- 변수:
  - `$$scroll_delta_y` – 세로 스크롤 양

## 화면 열림 시
- 어떤 화면이든 활성화된 직후 실행됩니다. 이를 덮어쓰는 용도로 사용할 수 있습니다.
- 변수:
  - `$$screen_identifier` – 열린 화면의 식별자

## 화면 닫힘 시
- 화면이 닫힌 직후 실행됩니다.
- 변수:
  - `$$screen_identifier` – 닫힌 화면의 식별자

## 마인크래프트 종료 시
- 클라이언트가 종료를 시작할 때 한 번 발동합니다.
- 변수:
  - `$$timestamp_millis` – 종료 시점의 epoch 밀리초
  - `$$timestamp_iso` – 종료 시점의 ISO-8601 타임스탬프

## 사망 시
- 로컬 플레이어에게 바닐라 사망 화면이 열릴 때 실행됩니다.
- 변수:
  - `$$days_survived` – 마지막 사망 이후 지난 일수
  - `$$death_reason_string` – 일반 텍스트 사망 원인
  - `$$death_reason_component` – JSON 컴포넌트 사망 원인
  - `$$death_pos_x` – 사망 X 좌표
  - `$$death_pos_y` – 사망 Y 좌표
  - `$$death_pos_z` – 사망 Z 좌표

## 변수 업데이트 시 [FM Variable]
- FancyMenu 변수가 설정/업데이트될 때마다 발동합니다.
- 변수:
  - `$$var_name` – 변수 이름
  - `$$old_value` – 이전 값
  - `$$new_value` – 새 값

## 액션을 통해 파일 다운로드 완료 시
- “게임 디렉터리에 파일 다운로드” 액션이 끝나면 발동합니다.
- 변수:
  - `$$download_url` – 다운로드 원본
  - `$$target_file_path` – 저장된 파일 경로
  - `$$download_succeeded` – true/false

## 파일 선택 시
- “파일 선택” 액션이 완료되면 발동합니다.
- 변수:
  - `$$selected_file_path` – 선택한 파일의 절대 경로, 또는 취소 시 비어 있음
  - `$$target_file_path` – 인스턴스 내 확인된 경로
  - `$$selection_succeeded` – 복사가 성공했으면 true
  - `$$selection_cancelled` – 대화상자가 닫혔으면 true
  - `$$failure_reason` – 실패 시 오류 정보

## 채팅 메시지 수신 시
- 일반 플레이어 채팅 메시지가 클라이언트에 표시되면 발동합니다.
- 변수:
  - `$$chat_message_string` – 일반 텍스트 줄
  - `$$chat_message_component` – 전체 JSON 컴포넌트
  - `$$sender_uuid` – 보낸 사람 UUID 또는 ERROR
  - `$$sender_name` – 보낸 사람 이름 또는 ERROR

## 채팅 메시지 전송 시
- 로컬 플레이어가 채팅 메시지를 보내면 발동합니다.
- 변수:
  - `$$chat_message_string` – 일반 텍스트 줄
  - `$$chat_message_component` – 전체 JSON 컴포넌트

## 효과 획득 시
- 플레이어가 상태 효과를 얻으면 발동합니다.
- 변수:
  - `$$effect_key` – 효과 리소스 위치
  - `$$effect_type` – 긍정/부정/중립
  - `$$effect_duration` – 남은 틱 수

## 효과 상실 시
- 플레이어가 상태 효과를 잃으면 발동합니다.
- 변수:
  - `$$effect_key` – 만료된 효과
  - `$$effect_type` – 범주

## 경험치 변경 시
- 플레이어의 총 경험치가 변경될 때마다 발동합니다.
- 변수:
  - `$$new_experience_amount` – 변경 후
  - `$$old_experience_amount` – 변경 전
  - `$$is_level_up` – 레벨이 증가했으면 TRUE

## 피해를 받았을 때
- 플레이어가 피해를 입을 때마다 한 번씩 발동합니다.
- 변수:
  - `$$damage_amount` – 감소한 체력량
  - `$$damage_type` – 피해 유형 리소스 위치
  - `$$is_fatal_damage` – 치명적 피해이면 TRUE
  - `$$damage_source` – 공격자 리소스 위치 또는 NONE

## 얼어붙기 시작 시
- 플레이어가 얼어붙기 시작하면 발동합니다.
- 변수:
  - `$$freezing_intensity` – 0.0은 없음, 1.0은 완전히 얼음

## 얼어붙기 중지 시
- 플레이어가 더 이상 얼어붙지 않을 때 발동합니다.
- 변수:
  - (없음)

## 완전히 얼음 상태가 되었을 때
- 플레이어가 완전히 얼어붙으면 한 번 발동합니다.
- 변수:
  - (없음)

## 블록을 바라보기 시작 시
- 십자선이 처음으로 블록을 가리킬 때 발동합니다(최대 거리 20블록).
- 변수:
  - `$$block_key` – 대상 블록
  - `$$block_pos_x` – 블록 X
  - `$$block_pos_y` – 블록 Y
  - `$$block_pos_z` – 블록 Z
  - `$$distance_to_player` – 눈에서 맞은 위치까지의 거리

## 블록을 바라보기 중지 시
- 십자선이 더 이상 블록을 가리키지 않을 때 발동합니다(마지막 대상 블록 보고, 최대 20블록).
- 변수:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`
  - `$$distance_to_player`

## 엔티티를 바라보기 시작 시
- 십자선이 처음으로 엔티티를 가리킬 때 발동합니다(최대 20블록).
- 변수:
  - `$$entity_key` – 대상 엔티티 유형
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## 엔티티를 바라보기 중지 시
- 십자선이 더 이상 엔티티를 가리키지 않을 때 발동합니다(마지막 대상 엔티티 보고, 최대 20블록).
- 변수:
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## 엔티티 생성 시
- **서버에 FancyMenu가 필요합니다.** 연결된 월드/서버의 어디에서든 엔티티가 생성되면 발동합니다.
- 변수:
  - `$$entity_key`
  - `$$distance_to_player` – 다른 차원이면 -1
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`
  - `$$dimension_key`
  - `$$is_same_dimension_as_player`

## 엔티티 사망 시
- **서버에 FancyMenu가 필요합니다.** 연결된 월드/서버의 어디에서든 엔티티가 죽으면 발동합니다.
- 변수:
  - `$$entity_key`
  - `$$distance_to_player` – 다른 차원이면 -1
  - `$$death_pos_x`
  - `$$death_pos_y`
  - `$$death_pos_z`
  - `$$entity_uuid`
  - `$$dimension_key`
  - `$$damage_type`
  - `$$is_same_dimension_as_player`
  - `$$entity_killed_by_name`
  - `$$entity_killed_by_key`
  - `$$entity_killed_by_uuid`

## 엔티티가 시야에 들어오기 시작 시
- 엔티티가 200블록 내에서 처음 보이기 시작하면 발동합니다.
- 변수:
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## 엔티티가 시야에서 벗어날 때
- 이전에 보이던 엔티티가 시야에서 사라지거나 200블록 밖으로 이동하면 발동합니다.
- 변수:
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## 엔티티와 상호작용 시
- 플레이어가 엔티티와 성공적으로 상호작용하면 발동합니다.
- 변수:
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## 엔티티 탑승 시
- 플레이어가 엔티티에 타기 시작하면 발동합니다.
- 변수:
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## 엔티티 하차 시
- 플레이어가 현재 타고 있는 엔티티에서 내리면 발동합니다.
- 변수:
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## 블록 파괴 시
- 플레이어가 블록을 부술 때 발동합니다.
- 변수:
  - `$$block_key`
  - `$$broke_with_item_key` – 사용한 도구 또는 EMPTY
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## 블록 설치 시
- 플레이어가 블록을 설치할 때 발동합니다.
- 변수:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## 블록과 상호작용 시
- 플레이어가 블록과 성공적으로 상호작용하면 발동합니다.
- 변수:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## 블록 위를 밟을 때
- 플레이어가 블록 위로 올라서면 발동합니다.
- 변수:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## 바이옴 진입 시
- 플레이어가 새로운 바이옴에 들어가면 발동합니다.
- 변수:
  - `$$biome_key` – 들어간 바이옴

## 바이옴 이탈 시
- 플레이어가 현재 바이옴을 벗어나면 발동합니다.
- 변수:
  - `$$biome_key` – 방금 벗어난 바이옴

## 구조물 진입 시
- **서버에 FancyMenu가 필요합니다.** 구조물 영역을 대략적으로 감지합니다. 구조물의 근처/위/아래에서도 발동할 수 있습니다.
- 변수:
  - `$$structure_key` – 들어간 구조물

## 구조물 이탈 시
- **서버에 FancyMenu가 필요합니다.** 대략적인 감지 방식입니다. 구조물 바깥 가장자리 근처에서도 발동할 수 있습니다.
- 변수:
  - `$$structure_key` – 방금 벗어난 구조물

## 구조물 진입 시 (고정밀)
- **서버에 FancyMenu가 필요합니다.** 플레이어가 구조물의 경계 박스 안으로 들어가면 발동합니다.
- 변수:
  - `$$structure_key`

## 구조물 이탈 시 (고정밀)
- **서버에 FancyMenu가 필요합니다.** 플레이어가 구조물의 경계 박스 밖으로 나가면 발동합니다.
- 변수:
  - `$$structure_key`

## 차원 진입 시
- 플레이어가 새로운 차원에 들어가면 발동합니다.
- 변수:
  - `$$dimension_key` – 들어간 차원

## 수영 시작 시
- 플레이어가 수영을 시작하면 발동합니다.
- 변수:
  - `$$fluid_type` – 유체 리소스 위치

## 수영 중지 시
- 플레이어가 수영을 멈추면 발동합니다.
- 변수:
  - `$$fluid_type` – 수영을 멈춘 유체

## 유체 접촉 시작 시
- 플레이어가 어떤 유체에 접촉하기 시작하면 발동합니다.
- 변수:
  - `$$fluid_type` – 접촉한 유체

## 유체 접촉 중지 시
- 플레이어가 더 이상 유체에 접촉하지 않으면 발동합니다.
- 변수:
  - `$$fluid_type` – 더 이상 접촉하지 않는 유체

## 음악 트랙 시작 시
- 새 음악 트랙이 재생되기 시작하면 발동합니다.
- 변수:
  - `$$track_resource_location` – 오디오 파일
  - `$$track_display_name` – 사람이 읽을 수 있는 이름 또는 UNKNOWN
  - `$$track_artist` – 아티스트 또는 UNKNOWN
  - `$$track_duration_ms` – 밀리초(알 수 없으면 0)

## 음악 트랙 중지 시
- 현재 음악 트랙이 끝나거나 다른 곡으로 바뀌면 발동합니다.
- 변수:
  - `$$track_resource_location`
  - `$$track_display_name`
  - `$$track_artist`
  - `$$track_duration_ms`

## 월드 사운드 트리거 시
- 위치가 있는 월드 사운드가 플레이어 근처에서 시작되면 발동합니다.
- 변수:
  - `$$sound_resource_location` – 사운드 파일
  - `$$sound_display_name` – 사용 가능한 경우 자막 이름
  - `$$sound_origin_pos_x`
  - `$$sound_origin_pos_y`
  - `$$sound_origin_pos_z`
  - `$$sound_origin_distance_to_player`
  - `$$sound_origin_direction_from_player` – 바라보는 방향을 기준으로 한 0–360도

## 날씨 변경 시
- 전역 또는 지역 날씨가 바뀌면 발동합니다(바이옴 변경이나 실내 진입으로 다시 발동할 수 있음).
- 변수:
  - `$$weather_type` – clear/rain/thunder
  - `$$weather_can_snow` – 눈이 렌더링되면 TRUE
  - `$$weather_can_rain` – 비가 렌더링되면 TRUE

## 불타기 시작 시
- 플레이어가 불타기 시작하면 발동합니다.
- 변수:
  - (없음)

## 불타기 중지 시
- 플레이어가 더 이상 불타지 않으면 발동합니다.
- 변수:
  - (없음)

## 익사 시작 시
- 플레이어가 익사 피해를 받기 시작하면 발동합니다.
- 변수:
  - (없음)

## 위치 변경 시
- 플레이어의 블록 위치가 변경될 때마다 발동합니다.
- 변수:
  - `$$old_pos_x` – 이전 블록 X
  - `$$old_pos_y` – 이전 블록 Y
  - `$$old_pos_z` – 이전 블록 Z
  - `$$new_pos_x` – 새 블록 X
  - `$$new_pos_y` – 새 블록 Y
  - `$$new_pos_z` – 새 블록 Z

## 달리기 시작 시
- 플레이어가 전력 질주를 시작하면 발동합니다.
- 변수:
  - (없음)

## 달리기 중지 시
- 플레이어가 전력 질주를 멈추면 발동합니다.
- 변수:
  - (없음)

## 점프 시
- 플레이어가 점프할 때마다 발동합니다.
- 변수:
  - (없음)

## 서버 접속 시
- 멀티플레이 서버 접속에 성공한 뒤 발동합니다.
- 변수:
  - `$$server_ip` – 접속한 서버 주소

## 서버 나가기 시
- 멀티플레이 서버 연결이 끊어진 뒤 발동합니다.
- 변수:
  - `$$server_ip` – 나간 서버 주소

## 싱글플레이 월드 진입 시
- 싱글플레이 월드의 로딩이 완료되고 조작이 가능해진 뒤 발동합니다.
- 변수:
  - `$$world_name` – 표시 이름
  - `$$world_save_path` – 절대 저장 폴더 경로
  - `$$world_difficulty` – 난이도 키
  - `$$world_cheats_allowed` – 치트가 활성화되어 있으면 TRUE
  - `$$world_icon_path` – 절대 아이콘 경로
  - `$$world_is_first_join` – 첫 방문이면 TRUE

## 싱글플레이 월드 나가기 시
- 싱글플레이 월드가 닫히고 저장이 완료된 뒤 발동합니다.
- 변수:
  - `$$world_name`
  - `$$world_save_path`
  - `$$world_difficulty`
  - `$$world_cheats_allowed`
  - `$$world_icon_path`

## 다른 플레이어가 월드/서버에 참가 시
- 다른 플레이어가 현재 월드/서버에 들어오면 발동합니다.
- 변수:
  - `$$player_name` – 들어온 플레이어 이름
  - `$$player_uuid` – UUID

## 다른 플레이어가 월드/서버에서 나갈 시
- 다른 플레이어가 현재 월드/서버에서 나가면 발동합니다.
- 변수:
  - `$$player_name`
  - `$$player_uuid`

## 다른 플레이어 사망 시
- 현재 월드의 다른 플레이어가 죽으면 발동합니다.
- 변수:
  - `$$player_name`
  - `$$player_uuid`
  - `$$death_pos_x`
  - `$$death_pos_y`
  - `$$death_pos_z`

## 아이템 주울 때
- 플레이어가 아이템 엔티티를 주우면 발동합니다.
- 변수:
  - `$$item_key` – 주운 아이템의 리소스 위치

## 아이템 버릴 때
- 플레이어가 인벤토리에서 아이템을 버리면 발동합니다.
- 변수:
  - `$$item_key` – 버린 아이템의 리소스 위치

## 아이템 소비 시
- 플레이어가 아이템 소비를 완료하면 발동합니다.
- 변수:
  - `$$item_key` – 소비한 아이템

## 인벤토리에서 아이템에 마우스 오버 시
- 어떤 인벤토리 화면에서든 아이템 위에 마우스를 올리면 발동합니다.
- 변수:
  - `$$item_key` – 마우스를 올린 아이템의 리소스 위치
  - `$$item_display_name_string` – 일반 텍스트 아이템 표시 이름
  - `$$item_display_name_json` – JSON 컴포넌트 아이템 표시 이름

## 아이템 사용 시
- 플레이어가 아이템을 사용하면 발동합니다.
- 변수:
  - `$$item_key` – 사용한 아이템
  - `$$used_on_type` – block/entity/self/none
  - `$$used_on_entity_key` – 대상 엔티티 유형 또는 비어 있음
  - `$$used_on_block_key` – 대상 블록 또는 비어 있음
  - `$$target_pos_x` – 대상 X 또는 -1
  - `$$target_pos_y` – 대상 Y 또는 -1
  - `$$target_pos_z` – 대상 Z 또는 -1

## 아이템 파괴 시
- 플레이어 인벤토리의 아이템이 파괴되면 발동합니다.
- 변수:
  - `$$item_key` – 파괴된 아이템
  - `$$item_type` – 도구/갑옷/기타
