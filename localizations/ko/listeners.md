---
title: 리스너
description: FancyMenu에서 리스너를 만들고 사용하는 방법입니다.
---

# 리스너

리스너는 특정 이벤트가 발생할 때 [액션 스크립트](./action-scripts)를 실행합니다. 열려 있는 화면에 묶여 있지 않으므로, 플레이 중이거나 로딩 중에도 실행될 수 있습니다.

리스너는 눌린 키나 클릭한 마우스 버튼 같은 `$$` 값을 액션과 요구 조건에 전달할 수 있습니다.

> [!CAUTION]
> 리스너는 화면이 열려 있지 않아도 파일, 네트워크, 명령어, 클립보드, 리소스 팩 또는 링크 액션을 실행할 수 있습니다. 신뢰할 수 있는 출처의 리스너만 가져오세요.

# 리스너 사용하기

레이아웃 편집기 밖에서는 **메뉴 바 -> 사용자 지정 -> 리스너 관리**를 열어 리스너를 만들거나 편집할 수 있습니다.

<img src="https://github.com/Keksuccino/FancyMenu/blob/master/assets/docs/manage_listeners.png?raw=true" alt="리스너 관리" style="max-width:800px;width:100%;height:auto;">

# 리스너 변수

리스너는 액션과 요구 조건에 읽기 전용 값을 제공할 수 있습니다. 지원되는 텍스트 필드에서 `$$` 이름을 사용하세요.

예를 들어, [**키보드 키 눌림 시**](#on-keyboard-key-pressed-keyboard_key_pressed)와 [**게임 로그에 출력** 액션](./action-scripts#print-to-game-log-print_to_log)을 함께 사용해 보세요. `Key pressed! The key is: $$key_name` 값을 넣으면 눌린 키의 이름이 삽입됩니다.

> [!WARNING]
> 리스너 변수는 FancyMenu의 [저장 변수](./variables)와 별개입니다. 저장 변수 액션, 요구 조건, 플레이스홀더는 `$$` 값과 함께 작동하지 않습니다.

리스너 변수 이름은 대소문자를 구분하며, 해당 리스너의 스크립트 안에서만 작동합니다.

채팅, 원격 서버, 파일, 사용자 입력에서 온 값은 신뢰할 수 없는 것으로 취급하세요. 경로, URL, 명령어에 직접 삽입하지 마세요.

리스너 변수는 문자열입니다. 정보를 사용할 수 없을 때, 리스너는 `ERROR`, `UNKNOWN`, `NONE`, `EMPTY`, `0`, `-1` 또는 빈 문자열 같은 문서화된 센티널 값을 반환할 수 있습니다. 이러한 값을 경로, 명령어, URL에 넣기 전에 먼저 검사하세요.

# 리스너 상세

이 섹션에는 FancyMenu에 내장된 리스너가 나열되어 있습니다.

## Markdown 텍스트 클릭 시 (`text_clicked`)
- [`click:` 이벤트가 있는 Markdown 텍스트](./text-formatting#click-and-hover-events)를 클릭하면 실행됩니다. 예: `[열기](click:open_menu)`.
- 변수:
  - `$$text_event_id` – Markdown 링크의 이벤트 ID

## Markdown 텍스트에 마우스 올림 시 (`text_hovered`)
- [`hover:` 이벤트가 있는 Markdown 텍스트](./text-formatting#click-and-hover-events)에 마우스를 올리면 실행됩니다. 예: `[힌트](hover:show_hint)`.
- 변수:
  - `$$text_event_id` – Markdown 링크의 이벤트 ID

## 액션을 통해 ZIP 추출 완료 시 (`zip_extracted_via_action`)
- [**게임 디렉터리에 ZIP 파일 추출** 액션](./action-scripts#extract-zip-file-in-game-directory-extract_zip_file_in_game_dir)이 완료되면 실행됩니다.
- 변수:
  - `$$source_zip_path` – 사용자에게 표시하기 위해 정규화된 원본 경로; 게임 디렉터리 경로는 `/...`로, 일반적인 Minecraft 디렉터리 경로는 `.minecraft/...`로 반환될 수 있음
  - `$$target_folder_path` – 같은 경로 형식을 사용하는 정규화된 대상 폴더 경로
  - `$$extract_succeeded` – true/false
  - `$$failure_reason` – 추출 실패 시 오류 텍스트

## 요소 생성 시 (`element_spawned_via_action`)
- 지원되는 FancyMenu 기능 또는 애드온이 요소 인스턴스를 동적으로 생성할 때 실행됩니다.
- 변수:
  - `$$element_type` – 생성된 요소 유형
  - `$$element_identifier` – 생성된 요소 식별자
  - `$$target_screen` – 대상 화면 식별자

## 애니메이션 텍스처 재생 시작 시 (`animated_texture_started_playing`)
- [애니메이션 텍스처](./fma)가 재생을 시작하면 실행됩니다.
- 변수:
  - `$$texture_source` – 텍스처 소스
  - `$$texture_source_type` – 소스 유형
  - `$$texture_will_restart` – true/false

## 애니메이션 텍스처 재생 종료 시 (`animated_texture_finished_playing`)
- 애니메이션 텍스처 재생이 끝나면 실행됩니다.
- 변수:
  - `$$texture_source`
  - `$$texture_source_type`
  - `$$texture_will_restart`

## 비디오 재생 상태 변경 시 (`video_playback_status_changed`)
- [비디오 요소 또는 메뉴 배경](./video)의 재생 상태가 바뀌면 실행됩니다.
- 변수:
  - `$$video_source` – 비디오 소스
  - `$$video_source_type` – 소스 유형
  - `$$is_looping` – true/false
  - `$$new_status` – `PLAYING`, `STOPPED`, `PAUSED`, 또는 `FINISHED`

## 채팅에서 시스템 메시지 수신 시 (`system_message_received_in_chat`)
- 클라이언트가 명령어 피드백 같은 시스템 채팅 메시지를 받으면 실행됩니다.
- 변수:
  - `$$system_message_string` – 일반 텍스트 메시지
  - `$$system_message_component` – JSON 컴포넌트

## FM 데이터 수신 시 (`fm_data_received`)
- 서버가 `/fmdata send`를 통해 이 클라이언트로 [FM 데이터](./fm-data)를 보낼 때 실행됩니다.
- 변수:
  - `$$data_identifier` – 데이터 식별자 문자열
  - `$$data` – 데이터 페이로드
  - `$$sent_by` – 서버 IP 또는 `integrated_server`

## 원격 서버 연결 성공 시 (`remote_server_connected`)
- [원격 서버 연결](./remote-server-communication)이 성공적으로 열리면 실행됩니다.
- 변수:
  - `$$request_id` – 캐시된 요청 ID
  - `$$remote_server_url` – 원격 서버 URL

## 원격 서버 데이터 수신 시 (`remote_server_data_received`)
- 연결된 원격 서버에서 텍스트 데이터가 수신되면 실행됩니다.
- 변수:
  - `$$request_id` – 요청 ID
  - `$$remote_server_url` – 원격 서버 URL
  - `$$data` – 수신된 페이로드

## 원격 서버 연결 종료 시 (`remote_server_connection_closed`)
- 원격 서버 연결이 종료되면 실행됩니다.
- 변수:
  - `$$request_id` – 요청 ID
  - `$$remote_server_url` – 원격 서버 URL
  - `$$intentionally_closed` – 액션으로 닫힌 경우 TRUE
  - `$$crashed` – 연결이 예기치 않게 충돌한 경우 TRUE
  - `$$unknown_close_reason` – 알려진 종료 원인이 없으면 TRUE

## 키보드 키 눌림 시 (`keyboard_key_pressed`)
- 키를 누를 때마다 트리거됩니다(누르고 있는 동안 반복됨; 화면과 게임 내에서 작동).
- 변수:
  - `$$key_name` – 키의 표시 이름
  - `$$key_keycode` – GLFW 키 코드
  - `$$key_scancode` – GLFW 스캔 코드
  - `$$key_modifiers` – 활성 수정자 비트 마스크

## 키보드 키 놓임 시 (`keyboard_key_released`)
- 키를 놓을 때 트리거됩니다(화면과 게임 내에서 작동).
- 변수:
  - `$$key_name`
  - `$$key_keycode`
  - `$$key_scancode`
  - `$$key_modifiers`

## 화면에서 키보드 문자 입력 시 (`keyboard_char_typed`)
- 화면이 열려 있는 동안 문자를 입력하면 실행됩니다.
- 변수:
  - `$$char` – 입력된 문자

## 화면에서 마우스 이동 시 (`mouse_moved`)
- 화면이 열려 있는 동안 마우스가 움직일 때마다 실행됩니다.
- 변수:
  - `$$mouse_pos_x` – 현재 X
  - `$$mouse_pos_y` – 현재 Y
  - `$$mouse_move_delta_x` – 이전 이벤트 이후 X 변화량
  - `$$mouse_move_delta_y` – 이전 이벤트 이후 Y 변화량

## 마우스 버튼 클릭 시 (`mouse_button_clicked`)
- 마우스 버튼을 누르면 실행됩니다(화면과 게임 내에서 작동).
- 변수:
  - `$$button` – 왼쪽/오른쪽/가운데
  - `$$mouse_pos_x` – 현재 X
  - `$$mouse_pos_y` – 현재 Y

## 마우스 버튼 놓임 시 (`mouse_button_released`)
- 마우스 버튼을 놓으면 실행됩니다(화면과 게임 내에서 작동).
- 변수:
  - `$$button`
  - `$$mouse_pos_x`
  - `$$mouse_pos_y`

## 화면에서 마우스 스크롤 시 (`mouse_scrolled`)
- 화면이 열려 있는 동안 마우스 휠을 스크롤하면 실행됩니다.
- 변수:
  - `$$scroll_delta_y` – 세로 스크롤 양

## 화면 열림 시 (`screen_open`)
- 어떤 화면이든 활성화된 직후 실행되며, 이를 덮어쓰는 데 사용할 수 있습니다.
- 변수:
  - `$$screen_identifier` – 열린 화면의 식별자

## 화면 닫힘 시 (`screen_close`)
- 화면이 닫힌 직후 실행됩니다.
- 변수:
  - `$$screen_identifier` – 닫힌 화면의 식별자

## 마인크래프트 종료 시 (`quit_minecraft`)
- 클라이언트가 종료를 시작할 때 한 번 실행됩니다.
- 변수:
  - `$$timestamp_millis` – 종료 시점의 epoch 밀리초
  - `$$timestamp_iso` – 종료 시점의 ISO-8601 타임스탬프

## 사망 시 (`player_death`)
- 로컬 플레이어에게 바닐라 사망 화면이 열릴 때 실행됩니다.
- 변수:
  - `$$days_survived` – 마지막 사망 이후 경과한 일수
  - `$$death_reason_string` – 일반 텍스트 원인
  - `$$death_reason_component` – JSON 컴포넌트 원인
  - `$$death_pos_x` – 사망 X 좌표
  - `$$death_pos_y` – 사망 Y 좌표
  - `$$death_pos_z` – 사망 Z 좌표

## 변수 업데이트 시 [FM 변수] (`fm_variable_updated`)
- [FancyMenu 변수](./variables)가 설정되거나 업데이트될 때마다 실행됩니다.
- 변수:
  - `$$var_name` – 변수 이름
  - `$$old_value` – 이전 값
  - `$$new_value` – 새 값

## 액션을 통해 파일 다운로드 완료 시 (`file_downloaded_via_action`)
- [**게임 디렉터리에 파일 다운로드** 액션](./action-scripts#download-file-to-game-directory-download_file_to_game_dir)이 완료되면 실행됩니다.
- 변수:
  - `$$download_url` – 다운로드 원본
  - `$$target_file_path` – 성공 시 저장된 파일 경로; 실패 시 최종 파일명이 결정되지 않아 대상 디렉터리만 포함할 수 있음
  - `$$download_succeeded` – true/false

## 파일 선택 완료 시 (`file_selected_via_action`)
- [**시스템에서 파일 선택** 액션](./action-scripts#select-file-from-system-select_file_to_game_dir)이 완료된 후 실행됩니다.
- 변수:
  - `$$selected_file_path` – 절대 선택 파일 경로 또는 취소 시 빈 값
  - `$$target_file_path` – 인스턴스 내부에 해결된 경로
  - `$$selection_succeeded` – 복사가 성공하면 true
  - `$$selection_cancelled` – 대화상자가 닫히면 true
  - `$$failure_reason` – 실패 시 오류 정보

## 채팅 메시지 수신 시 (`chat_message_received`)
- 일반 플레이어 채팅 메시지가 클라이언트에 표시되면 실행됩니다.
- 변수:
  - `$$chat_message_string` – 일반 텍스트 줄
  - `$$chat_message_component` – 전체 JSON 컴포넌트
  - `$$sender_uuid` – 발신자 UUID 또는 ERROR
  - `$$sender_name` – 발신자 이름 또는 ERROR

## 채팅 메시지 전송 시 (`chat_message_sent`)
- 로컬 플레이어가 채팅 메시지를 보낼 때 실행됩니다.
- 변수:
  - `$$chat_message_string` – 일반 텍스트 줄
  - `$$chat_message_component` – 전체 JSON 컴포넌트

## 효과 획득 시 (`effect_gained`)
- 플레이어가 상태 효과를 얻을 때 실행됩니다.
- 변수:
  - `$$effect_key` – 효과 리소스 위치
  - `$$effect_type` – 긍정/부정/중립
  - `$$effect_duration` – 남은 틱 수

## 효과 상실 시 (`effect_lost`)
- 플레이어가 상태 효과를 잃을 때 실행됩니다.
- 변수:
  - `$$effect_key` – 만료된 효과
  - `$$effect_type` – 범주

## 경험치 변경 시 (`experience_changed`)
- 플레이어의 총 XP가 바뀔 때마다 실행됩니다.
- 변수:
  - `$$new_experience_amount` – 변경 후
  - `$$old_experience_amount` – 변경 전
  - `$$is_level_up` – 레벨이 증가했으면 TRUE

## 피해 받음 시 (`damage_taken`)
- 플레이어가 피해를 입을 때마다 한 번 실행됩니다.
- 변수:
  - `$$damage_amount` – 감소한 체력
  - `$$damage_type` – 피해 유형 리소스 위치
  - `$$is_fatal_damage` – 치명적이면 TRUE
  - `$$damage_source` – 공격자 리소스 위치 또는 NONE

## 얼어붙기 시작 시 (`started_freezing`)
- 플레이어가 얼어붙기 시작하면 실행됩니다.
- 변수:
  - `$$freezing_intensity` – 0.0은 없음, 1.0은 완전 빙결

## 얼어붙기 중지 시 (`stopped_freezing`)
- 플레이어가 더 이상 얼어붙지 않으면 실행됩니다.
- 변수:
  - (없음)

## 완전히 얼어붙음 시 (`fully_frozen`)
- 플레이어가 완전히 얼어붙을 때 한 번 실행됩니다.
- 변수:
  - (없음)

## 블록을 보기 시작할 때 (`start_looking_at_block`)
- 조준점이 처음 블록을 가리킬 때 한 번 실행됩니다(최대 거리 20블록).
- 변수:
  - `$$block_key` – 대상 블록
  - `$$block_pos_x` – 블록 X
  - `$$block_pos_y` – 블록 Y
  - `$$block_pos_z` – 블록 Z
  - `$$distance_to_player` – 눈에서 충돌 지점까지의 거리

## 블록 보기를 멈출 때 (`stop_looking_at_block`)
- 조준점이 블록을 더 이상 가리키지 않을 때 실행됩니다(마지막으로 대상이었던 블록을 보고, 최대 20블록).
- 변수:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`
  - `$$distance_to_player`

## 엔티티를 보기 시작할 때 (`start_looking_at_entity`)
- 조준점이 처음 엔티티를 가리킬 때 한 번 실행됩니다(최대 20블록).
- 변수:
  - `$$entity_key` – 대상 엔티티 유형
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## 엔티티 보기를 멈출 때 (`stop_looking_at_entity`)
- 조준점이 엔티티를 더 이상 가리키지 않을 때 실행됩니다(마지막으로 대상이었던 엔티티를 보고, 최대 20블록).
- 변수:
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## 엔티티 생성 시 (`entity_spawned`)
- **서버에 FancyMenu가 필요합니다.** 연결된 월드/서버의 어디에서든 엔티티가 생성되면 실행됩니다.
- 변수:
  - `$$entity_key`
  - `$$distance_to_player` – 다른 차원이면 −1
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`
  - `$$dimension_key`
  - `$$is_same_dimension_as_player`

## 엔티티 사망 시 (`entity_died`)
- **서버에 FancyMenu가 필요합니다.** 연결된 월드/서버에서 어떤 엔티티든 죽으면 실행됩니다.
- 변수:
  - `$$entity_key`
  - `$$distance_to_player` – 다른 차원이면 −1
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

## 엔티티가 시야에 들어오기 시작할 때 (`entity_starts_being_in_sight`)
- 엔티티가 200블록 이내에서 처음 보이기 시작하면 실행됩니다.
- 변수:
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## 엔티티가 시야에서 벗어날 때 (`entity_stops_being_in_sight`)
- 이전에 보이던 엔티티가 시야에서 사라지거나 200블록 밖으로 이동하면 실행됩니다.
- 변수:
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## 엔티티와 상호작용했을 때 (`entity_interacted`)
- 플레이어가 엔티티와 성공적으로 상호작용하면 실행됩니다.
- 변수:
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## 엔티티 탑승 시 (`entity_mounted`)
- 플레이어가 엔티티를 타기 시작하면 실행됩니다.
- 변수:
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## 엔티티 하차 시 (`entity_unmounted`)
- 플레이어가 현재 타고 있는 엔티티에서 내리면 실행됩니다.
- 변수:
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## 블록 파괴 시 (`block_broke`)
- 플레이어가 블록을 부술 때 실행됩니다.
- 변수:
  - `$$block_key`
  - `$$broke_with_item_key` – 사용한 도구 또는 EMPTY
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## 블록 설치 시 (`block_placed`)
- 플레이어가 블록을 설치할 때 실행됩니다.
- 변수:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## 블록과 상호작용했을 때 (`interacted_with_block`)
- 플레이어가 블록과 성공적으로 상호작용하면 실행됩니다.
- 변수:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## 블록 위를 밟을 때 (`stepping_on_block`)
- 플레이어가 블록 위로 올라설 때 실행됩니다.
- 변수:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## 생물군계 진입 시 (`enter_biome`)
- 플레이어가 새로운 생물군계에 들어가면 실행됩니다.
- 변수:
  - `$$biome_key` – 진입한 생물군계

## 생물군계 이탈 시 (`leave_biome`)
- 플레이어가 현재 생물군계를 벗어나면 실행됩니다.
- 변수:
  - `$$biome_key` – 방금 떠난 생물군계

## 구조물 진입 시 (`enter_structure`)
- **서버에 FancyMenu가 필요합니다.** 대략적인 구조물 영역 감지; 구조물 근처/위/아래에서도 트리거될 수 있습니다.
- 변수:
  - `$$structure_key` – 진입한 구조물

## 구조물 이탈 시 (`leave_structure`)
- **서버에 FancyMenu가 필요합니다.** 대략적인 감지; 구조물 범위 근처에서 트리거될 수 있습니다.
- 변수:
  - `$$structure_key` – 방금 떠난 구조물

## 구조물 진입 시(고정밀) (`enter_structure_high_precision`)
- **서버에 FancyMenu가 필요합니다.** 플레이어가 구조물의 경계 상자 안으로 들어가면 실행됩니다.
- 변수:
  - `$$structure_key`

## 구조물 이탈 시(고정밀) (`leave_structure_high_precision`)
- **서버에 FancyMenu가 필요합니다.** 플레이어가 구조물의 경계 상자에서 벗어나면 실행됩니다.
- 변수:
  - `$$structure_key`

## 차원 진입 시 (`enter_dimension`)
- 플레이어가 새 차원에 들어가면 실행됩니다.
- 변수:
  - `$$dimension_key` – 진입한 차원

## 수영 시작 시 (`start_swimming`)
- 플레이어가 수영을 시작하면 실행됩니다.
- 변수:
  - `$$fluid_type` – 유체 리소스 위치

## 수영 중지 시 (`stop_swimming`)
- 플레이어가 수영을 멈추면 실행됩니다.
- 변수:
  - `$$fluid_type` – 수영이 멈춘 유체

## 유체 접촉 시작 시 (`start_touching_fluid`)
- 플레이어가 유체에 닿기 시작하면 실행됩니다.
- 변수:
  - `$$fluid_type` – 접촉한 유체

## 유체 접촉 중지 시 (`stop_touching_fluid`)
- 플레이어가 더 이상 유체에 닿지 않으면 실행됩니다.
- 변수:
  - `$$fluid_type` – 더 이상 닿지 않는 유체

## 음악 트랙 시작 시 (`music_track_started`)
- 새 음악 트랙이 시작되면 실행됩니다.
- 변수:
  - `$$track_resource_location` – 오디오 파일
  - `$$track_display_name` – 사람이 읽을 수 있는 이름 또는 UNKNOWN
  - `$$track_artist` – 아티스트 또는 UNKNOWN
  - `$$track_duration_ms` – 밀리초(알 수 없으면 0)

## 음악 트랙 중지 시 (`music_track_stopped`)
- 현재 음악 트랙이 끝나거나 다른 트랙으로 바뀌면 실행됩니다.
- 변수:
  - `$$track_resource_location`
  - `$$track_display_name`
  - `$$track_artist`
  - `$$track_duration_ms`

## 월드 사운드 재생 시 (`world_sound_triggered`)
- 위치 기반 월드 사운드가 플레이어 근처에서 시작되면 실행됩니다.
- 변수:
  - `$$sound_resource_location` – 사운드 파일
  - `$$sound_display_name` – 사용 가능한 경우 자막 이름
  - `$$sound_origin_pos_x`
  - `$$sound_origin_pos_y`
  - `$$sound_origin_pos_z`
  - `$$sound_origin_distance_to_player`
  - `$$sound_origin_direction_from_player` – 바라보는 방향 기준 0~360도

## 날씨 변경 시 (`weather_changed`)
- 날씨가 전역 또는 지역적으로 바뀌면 실행됩니다(생물군계 변경이나 실내 진입으로 다시 트리거될 수 있음).
- 변수:
  - `$$weather_type` – clear/rain/thunder
  - `$$weather_can_snow` – 눈이 렌더링되면 TRUE
  - `$$weather_can_rain` – 비가 렌더링되면 TRUE

## 타기 시작 시 (`started_burning`)
- 플레이어가 타기 시작하면 실행됩니다.
- 변수:
  - (없음)

## 타기 중지 시 (`stopped_burning`)
- 플레이어가 더 이상 타지 않으면 실행됩니다.
- 변수:
  - (없음)

## 익사 시작 시 (`started_drowning`)
- 플레이어가 익사 피해를 받기 시작하면 실행됩니다.
- 변수:
  - (없음)

## 위치 변경 시 (`position_changed`)
- 플레이어의 블록 위치가 바뀔 때마다 실행됩니다.
- 변수:
  - `$$old_pos_x` – 이전 블록 X
  - `$$old_pos_y` – 이전 블록 Y
  - `$$old_pos_z` – 이전 블록 Z
  - `$$new_pos_x` – 새 블록 X
  - `$$new_pos_y` – 새 블록 Y
  - `$$new_pos_z` – 새 블록 Z

## 달리기 시작 시 (`started_running`)
- 플레이어가 전력 달리기를 시작하면 실행됩니다.
- 변수:
  - (없음)

## 달리기 중지 시 (`stopped_running`)
- 플레이어가 전력 달리기를 멈추면 실행됩니다.
- 변수:
  - (없음)

## 점프 시 (`jump`)
- 플레이어가 점프할 때마다 실행됩니다.
- 변수:
  - (없음)

## 서버 접속 시 (`server_joined`)
- 멀티플레이어 서버에 성공적으로 접속한 후 실행됩니다.
- 변수:
  - `$$server_ip` – 접속한 서버 주소

## 서버 이탈 시 (`server_left`)
- 멀티플레이어 서버 연결이 끊긴 후 실행됩니다.
- 변수:
  - `$$server_ip` – 떠난 서버 주소

## 싱글플레이 월드 진입 시 (`world_entered`)
- 싱글플레이 월드 로딩이 끝나고 조작이 반환된 후 실행됩니다.
- 변수:
  - `$$world_name` – 표시 이름
  - `$$world_save_path` – 절대 저장 폴더 경로
  - `$$world_difficulty` – 난이도 키
  - `$$world_cheats_allowed` – 치트가 활성화되면 TRUE
  - `$$world_icon_path` – 절대 아이콘 경로
  - `$$world_is_first_join` – 첫 방문이면 TRUE

## 싱글플레이 월드 이탈 시 (`world_left`)
- 싱글플레이 월드가 닫히고 저장이 끝난 후 실행됩니다.
- 변수:
  - `$$world_name`
  - `$$world_save_path`
  - `$$world_difficulty`
  - `$$world_cheats_allowed`
  - `$$world_icon_path`

## 다른 플레이어가 월드/서버에 접속 시 (`other_player_joined_world`)
- 다른 플레이어가 현재 월드/서버에 들어오면 실행됩니다.
- 변수:
  - `$$player_name` – 접속한 플레이어 이름
  - `$$player_uuid` – UUID

## 다른 플레이어가 월드/서버에서 나갈 때 (`other_player_left_world`)
- 다른 플레이어가 현재 월드/서버를 떠나면 실행됩니다.
- 변수:
  - `$$player_name`
  - `$$player_uuid`

## 다른 플레이어 사망 시 (`other_player_died`)
- 현재 월드의 다른 플레이어가 사망하면 실행됩니다.
- 변수:
  - `$$player_name`
  - `$$player_uuid`
  - `$$death_pos_x`
  - `$$death_pos_y`
  - `$$death_pos_z`

## 아이템 획득 시 (`item_picked_up`)
- 플레이어가 아이템 엔티티를 주울 때 실행됩니다.
- 변수:
  - `$$item_key` – 주운 아이템 리소스 위치

## 아이템 버림 시 (`item_dropped`)
- 플레이어가 인벤토리에서 아이템을 버릴 때 실행됩니다.
- 변수:
  - `$$item_key` – 버린 아이템 리소스 위치

## 아이템 소비 완료 시 (`item_consumed`)
- 플레이어가 아이템 소비를 마치면 실행됩니다.
- 변수:
  - `$$item_key` – 소비한 아이템

## 인벤토리에서 아이템에 마우스를 올릴 때 (`item_hovered_in_inventory`)
- 사용자가 어떤 인벤토리 화면에서든 아이템 위에 마우스를 올리면 실행됩니다.
- 변수:
  - `$$item_key` – 마우스가 올라간 아이템 리소스 위치
  - `$$item_display_name_string` – 일반 텍스트 아이템 표시 이름
  - `$$item_display_name_json` – JSON 컴포넌트 아이템 표시 이름

## 아이템 사용 시 (`item_used`)
- 플레이어가 아이템을 사용할 때 실행됩니다.
- 변수:
  - `$$item_key` – 사용한 아이템
  - `$$used_on_type` – block/entity/self/none
  - `$$used_on_entity_key` – 대상 엔티티 유형 또는 empty
  - `$$used_on_block_key` – 대상 블록 또는 empty
  - `$$target_pos_x` – 대상 X 또는 -1
  - `$$target_pos_y` – 대상 Y 또는 -1
  - `$$target_pos_z` – 대상 Z 또는 -1

## 아이템 파손 시 (`item_broke`)
- 플레이어 인벤토리의 아이템이 부서질 때 실행됩니다.
- 변수:
  - `$$item_key` – 파손된 아이템
  - `$$item_type` – 도구/갑옷/기타
