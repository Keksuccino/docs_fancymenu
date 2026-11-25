---
title: 리스너
description: '키 입력, 채팅 메시지, 새 도전 과제 달성 등 게임에서 이벤트가 발생할 때 작업 스크립트를 실행합니다.'
sourceBlobSha: b8417f6287ac413d2d44e0fc5c2383c0b0fa6e1e
---

# 리스너

리스너는 게임에서 키 입력, 화면 열기, 도전 과제 달성 등 이벤트가 발생할 때 [작업 스크립트](/action-scripts)를 실행합니다. 모든 메뉴와 게임 플레이 중에 작동하며, 레이아웃에 속하지 않습니다.

대부분의 리스너는 눌린 키의 이름처럼 발생한 이벤트에 관한 변수를 스크립트에 제공합니다.

<img width="800" alt="타이틀 화면에서 키를 누르면 토스트에 누른 키의 이름이 표시됩니다" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/listeners_trigger.gif?raw=true">

> [!CAUTION]
> 메뉴가 열려 있지 않은 상태에서도 리스너가 파일, 네트워크, 명령어, 클립보드, 리소스 팩 및 링크 작업을 실행할 수 있습니다. 신뢰하는 사람의 프로필과 파일에서 가져온 리스너만 사용하세요.

# 리스너 추가하기

<img width="800" alt="리스너 관리 창을 열고, 토스트 표시 작업이 포함된 키보드 키를 눌렀을 때 리스너를 추가한 뒤 H를 눌러 테스트합니다" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/listeners_make.gif?raw=true">

1. **메뉴 바 -> 사용자 지정 -> 리스너 관리**를 엽니다.
2. **리스너 추가**를 클릭합니다.
3. **사용 가능한 리스너**에서 이벤트를 클릭합니다. 검색창에서 이름과 설명으로 리스너를 찾을 수 있습니다.
   - **리스너 설명**에는 리스너의 기능과 제공하는 변수가 표시됩니다.
   - **변수를 클립보드에 복사**를 클릭하면 변수 이름이 복사됩니다.
   - **설명을 별도 창으로 열기**를 클릭하면 설명이 별도 창에 열립니다.
4. **완료**를 클릭하거나 리스너를 더블 클릭합니다. 작업 스크립트 편집기가 열립니다.
5. 실행할 작업을 추가하고 **완료**를 클릭합니다. [작업 스크립트](/action-scripts#making-an-action-script)를 참고하세요.
6. **리스너 관리**에서 **완료**를 클릭해 저장합니다. 리스너가 즉시 작동합니다.

**취소**를 클릭하면 확인 메시지가 표시된 후 **리스너 관리**에서 변경한 내용이 모두 취소됩니다.

# 리스너 관리하기

<img width="800" alt="리스너 다섯 개가 있는 리스너 관리 창. 그중 하나를 선택하면 오른쪽에 해당 작업 스크립트가 표시됩니다" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/listeners_manage.png?raw=true">

- 리스너를 클릭하면 오른쪽에 리스너 유형과 작업 스크립트가 표시됩니다.
- **작업 편집**을 클릭하거나 리스너를 마우스 오른쪽 버튼으로 클릭하면 작업 스크립트가 열립니다.
- 리스너 이름을 더블 클릭하면 `Help Key`처럼 이름을 바꿀 수 있습니다. `Enter`를 누르면 저장하고, `Esc`를 누르면 취소합니다. 이름을 비워 두면 리스너 유형이 다시 표시됩니다.
- **리스너 제거**를 클릭하면 선택한 리스너가 삭제됩니다.
- **AI용으로 내보내기**를 클릭하면 저장하지 않은 변경 사항을 포함해 선택한 리스너 또는 모든 리스너가 [AI 채팅](/export-for-ai)용으로 복사됩니다.

리스너는 `config/fancymenu/listener_instances.txt`에 저장됩니다([데이터 저장 위치](/data-storage-locations) 참고). 각 [프로필](/profiles)에는 별도의 리스너가 있습니다.

# 리스너 변수

리스너 변수는 `$$`로 시작하며 해당 스크립트 어디에서나 사용할 수 있습니다. 모든 작업 값과 [IF 문](/action-scripts#if-else-if-and-else)의 조건에서 사용할 수 있습니다. 대소문자를 구분합니다. 아래 각 리스너에는 사용할 수 있는 변수가 나와 있으며, 리스너 선택 창의 설명에도 표시됩니다.

<img width="800" alt="도전 과제 달성 시 리스너를 선택한 리스너 선택 창. 설명에 변수가 나와 있습니다" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/listeners_choose.png?raw=true">

예를 들어 다음 리스너는 `H` 키를 누르면 도움말 화면을 엽니다.

1. **키보드 키를 눌렀을 때** 리스너를 추가합니다.
2. 스크립트에서 [**텍스트인지 확인**](/conditions#is-text) 조건을 사용하는 **IF 문 추가**를 선택합니다. **비교 모드**를 **같음**으로 설정하고, **텍스트**에는 `$$key_name`을, **비교할 텍스트**에는 `H`를 입력합니다.
3. IF 문 안에 도움말 화면을 지정한 [**화면 또는 사용자 지정 GUI 열기**](/action-scripts#open-screen-or-custom-gui)를 추가합니다.

리스너 변수에 관한 추가 정보:

- 리스너 변수는 항상 텍스트입니다. 리스너가 값을 알아낼 수 없는 경우 `ERROR`, `UNKNOWN`, `NONE`, `EMPTY`, `0`, `-1` 또는 빈 값과 같은 대체값이 설정됩니다.
- 리스너 변수는 [플레이스홀더](/placeholders)보다 먼저 채워지므로 플레이스홀더 안에서도 사용할 수 있습니다.
- 리스너 변수는 해당 스크립트가 실행되는 동안에만 존재합니다. 값을 유지하려면 [**변수 값 설정(FM 변수)**](/action-scripts#set-variable-value-fm-variable)을 사용해 [변수](/variables)에 저장하세요.
- **메뉴 바 -> 사용자 지정 -> 변수 관리**에서 만든 변수도 리스너 스크립트에서 `$$coins`처럼 `$$`와 변수 이름을 함께 사용해 참조할 수 있습니다. 사용자 변수의 이름이 리스너 변수와 같으면 `$$name`은 리스너 변수를 가리킵니다. `key_name_log`처럼 더 긴 이름을 가진 사용자 변수는 계속 사용할 수 있습니다.
- 채팅, 서버, 파일 및 다른 플레이어가 보낸 텍스트는 어떤 내용이든 포함할 수 있습니다. 이 텍스트를 명령어, 파일 경로 또는 링크에 그대로 넣지 마세요.

# 알아두면 좋은 점

- 일부 리스너는 서버에도 FancyMenu가 설치되어 있어야 합니다. 해당 리스너에는 아래에 안내가 표시됩니다. 싱글플레이에서는 항상 작동합니다.
- **화면에서 마우스를 움직였을 때**, **요소를 스크롤했을 때**, **위치가 변경되었을 때**, **월드 사운드가 재생되었을 때**처럼 매우 자주 실행되는 리스너도 있습니다. 스크립트를 짧게 유지하고, 해당 리스너에서 [**FancyMenu 다시 불러오기**](/action-scripts#reload-fancymenu) 같은 느린 작업은 사용하지 마세요.
- **화면이 열렸을 때**를 사용해 화면을 다른 화면으로 바꾸려면 먼저 IF 문으로 `$$screen_identifier`를 확인하세요. 그렇지 않으면 방금 연 화면을 포함해 모든 화면이 다른 화면으로 바뀝니다.

# 모든 리스너

FancyMenu에서 사용할 수 있는 모든 리스너를 반응하는 이벤트별로 정리했습니다.

## 키보드 및 마우스

어떤 키인지 확인하려면 `$$key_name`을 사용하세요. 키의 코드 번호는 Minecraft 버전에 따라 다를 수 있습니다.

### 키보드 키를 눌렀을 때

**식별자:** `keyboard_key_pressed`

메뉴와 게임 플레이 중에 키를 누르면 실행됩니다. 키를 계속 누르고 있으면 반복해서 실행됩니다.

- `$$key_name`: 키 이름(예: `H` 또는 `Left Shift`)
- `$$key_keycode`: 키의 코드 번호
- `$$key_scancode`: 키의 스캔 코드
- `$$key_modifiers`: 동시에 누른 보조 키(예: `Shift`, `Ctrl`)를 나타내는 숫자

### 키보드 키를 놓았을 때

**식별자:** `keyboard_key_released`

메뉴와 게임 플레이 중에 키를 놓으면 실행됩니다.

**키보드 키를 눌렀을 때**와 같은 변수인 `$$key_name`, `$$key_keycode`, `$$key_scancode`, `$$key_modifiers`를 제공합니다.

### 화면에서 키보드 문자를 입력했을 때

**식별자:** `keyboard_char_typed`

화면이 열려 있는 동안 문자를 입력할 때마다 실행됩니다.

- `$$char`: 입력한 문자

### 화면에서 마우스를 움직였을 때

**식별자:** `mouse_moved`

화면이 열려 있는 동안 마우스를 움직일 때마다 실행됩니다.

- `$$mouse_pos_x`, `$$mouse_pos_y`: GUI 픽셀 단위의 마우스 위치
- `$$mouse_move_delta_x`, `$$mouse_move_delta_y`: 직전 위치에서 이동한 거리

### 마우스 버튼을 클릭했을 때

**식별자:** `mouse_button_clicked`

메뉴와 게임 플레이 중에 마우스 버튼을 누르면 한 번 실행됩니다.

- `$$button`: `left`, `right` 또는 `middle`. 다른 버튼은 번호로 표시됩니다.
- `$$mouse_pos_x`, `$$mouse_pos_y`: GUI 픽셀 단위의 마우스 위치

### 마우스 버튼을 놓았을 때

**식별자:** `mouse_button_released`

메뉴와 게임 플레이 중에 마우스 버튼을 놓으면 한 번 실행됩니다.

**마우스 버튼을 클릭했을 때**와 같은 변수인 `$$button`, `$$mouse_pos_x`, `$$mouse_pos_y`를 제공합니다.

### 화면에서 마우스 휠을 굴렸을 때

**식별자:** `mouse_scrolled`

화면이 열려 있는 동안 마우스 휠을 굴리면 실행됩니다.

- `$$scroll_delta_y`: 휠을 굴린 거리. 위로 스크롤하면 `0`보다 크고, 아래로 스크롤하면 `0`보다 작습니다.

## 화면 및 요소

### 화면이 열렸을 때

**식별자:** `screen_open`

화면이 열린 직후 실행됩니다. 스크립트에서 [**화면 또는 사용자 지정 GUI 열기**](/action-scripts#open-screen-or-custom-gui) 작업을 사용해 화면을 다른 화면으로 바꿀 수 있습니다.

- `$$screen_identifier`: 화면의 [식별자](/screen-identifiers)

### 화면이 닫혔을 때

**식별자:** `screen_close`

화면이 닫힌 직후 실행됩니다.

- `$$screen_identifier`: 닫힌 화면의 [식별자](/screen-identifiers)

### 마크다운 텍스트를 클릭했을 때

**식별자:** `text_clicked`

`[규칙 읽기](click:open_rules)`처럼 텍스트의 [클릭 이벤트](/text-formatting#click-and-hover-events)를 클릭하면 실행됩니다.

- `$$text_event_id`: `open_rules`와 같은 이벤트 ID

### 마크다운 텍스트에 마우스를 올렸을 때

**식별자:** `text_hovered`

`[이게 뭐죠?](hover:show_hint)`처럼 텍스트의 [마우스 오버 이벤트](/text-formatting#click-and-hover-events) 위로 마우스를 움직이면 실행됩니다.

- `$$text_event_id`: `show_hint`와 같은 이벤트 ID

### 요소를 스크롤했을 때

**식별자:** `scroll_area_scrolled`

[스크롤 가능 영역](/scrollable-areas) 또는 [텍스트 요소](/text-in-menus)의 콘텐츠가 움직일 때마다 실행됩니다. 콘텐츠가 부드럽게 움직이는 동안에는 매 프레임 실행됩니다. 레이아웃 편집기에서는 실행되지 않습니다.

- `$$element_identifier`: 요소의 [식별자](/element-identifiers)
- `$$scroll_x`: 콘텐츠를 가로로 스크롤한 픽셀 거리
- `$$scroll_y`: 콘텐츠를 아래로 스크롤한 픽셀 거리
- `$$scroll_percent`: 요소의 주 스크롤 방향에서 콘텐츠를 스크롤한 정도(시작 `0`부터 끝 `100`까지)

### 요소를 시작 위치까지 스크롤했을 때

**식별자:** `scroll_area_reached_start`

스크롤 가능 영역 또는 텍스트 요소의 콘텐츠를 시작 위치까지 다시 스크롤하면 실행됩니다.

**요소를 스크롤했을 때**와 같은 변수인 `$$element_identifier`, `$$scroll_x`, `$$scroll_y`, `$$scroll_percent`를 제공합니다.

### 요소를 끝까지 스크롤했을 때

**식별자:** `scroll_area_reached_end`

규칙을 모두 읽기 위해 스크롤하는 경우처럼 스크롤 가능 영역 또는 텍스트 요소의 콘텐츠를 끝까지 스크롤하면 실행됩니다.

**요소를 스크롤했을 때**와 같은 변수인 `$$element_identifier`, `$$scroll_x`, `$$scroll_y`, `$$scroll_percent`를 제공합니다.

### 애니메이션 텍스처 재생이 시작되었을 때

**식별자:** `animated_texture_started_playing`

[애니메이션 텍스처](/animations)(GIF, APNG 또는 FMA)의 재생이 시작될 때와 재생이 처음부터 다시 시작될 때마다 실행됩니다.

- `$$texture_source`: 텍스처 출처(파일 경로, 웹 링크 또는 리소스 위치)
- `$$texture_source_type`: `LOCAL`, `WEB` 또는 `RESOURCE_LOCATION`
- `$$texture_will_restart`: 재생이 끝난 뒤 다시 시작하면 `true`, 그렇지 않으면 `false`

### 애니메이션 텍스처 재생이 끝났을 때

**식별자:** `animated_texture_finished_playing`

애니메이션 텍스처의 한 회 재생이 끝나면 실행됩니다. 반복 재생 중에는 처음부터 다시 시작하기 직전에 실행됩니다.

**애니메이션 텍스처 재생이 시작되었을 때**와 같은 변수인 `$$texture_source`, `$$texture_source_type`, `$$texture_will_restart`를 제공합니다.

### 동영상 재생 상태가 변경되었을 때

**식별자:** `video_playback_status_changed`

[동영상](/video) 요소 또는 메뉴 배경 동영상이 재생, 일시 정지, 정지 또는 종료되면 실행됩니다.

- `$$video_source`: 동영상 출처(파일 경로, 웹 링크 또는 리소스 위치)
- `$$video_source_type`: `LOCAL`, `WEB` 또는 `RESOURCE_LOCATION`
- `$$is_looping`: 동영상이 반복 재생되면 `true`, 그렇지 않으면 `false`
- `$$new_status`:
  - `PLAYING`: 동영상 재생이 시작되었거나 일시 정지가 해제됨
  - `PAUSED`: 동영상이 일시 정지됨
  - `STOPPED`: 동영상이 정지됨
  - `FINISHED`: 동영상이 끝남. 반복 재생 동영상도 다시 시작되기 직전에 이 상태가 됩니다.

## 변수, 파일 및 데이터

### FM 변수가 업데이트되었을 때

**식별자:** `fm_variable_updated`

[변수](/variables)가 설정될 때마다 실행됩니다.

- `$$var_name`: 변수 이름
- `$$old_value`: 이전 값
- `$$new_value`: 새 값

목록 변수의 경우 두 값 모두 `［"Diamonds","Emeralds"］`와 같은 JSON 배열 형식의 전체 목록입니다.

### 작업으로 파일 다운로드가 시작되었을 때

**식별자:** `file_download_started_via_action`

[**게임 디렉터리로 파일 다운로드**](/action-scripts#download-file-to-game-directory) 작업의 다운로드가 시작되고 파일 이름을 확인할 수 있게 되면 실행됩니다. 다운로드가 끝나야 파일이 지정된 경로에 나타나므로, 다운로드가 완료되는 시점을 확인하려면 **작업으로 파일이 다운로드되었을 때**를 사용하세요.

- `$$download_url`: 파일 링크
- `$$target_file_path`: 파일이 저장될 위치

### 작업으로 파일이 다운로드되었을 때

**식별자:** `file_downloaded_via_action`

[**게임 디렉터리로 파일 다운로드**](/action-scripts#download-file-to-game-directory) 작업의 다운로드가 완료되거나 실패하면 실행됩니다.

- `$$download_url`: 파일 링크
- `$$target_file_path`: 파일이 저장된 위치. 다운로드가 실패하면 폴더 경로만 설정될 수 있습니다.
- `$$download_succeeded`: `true` 또는 `false`

### 파일을 선택했을 때

**식별자:** `file_selected_via_action`

[**시스템에서 파일 선택**](/action-scripts#select-file-from-system) 작업이 완료되면 실행됩니다. 파일 복사, 파일 선택기 취소, 작업 실패 중 어떤 경우든 실행됩니다.

- `$$selected_file_path`: 선택한 파일의 전체 경로. 파일 선택기를 취소하면 비어 있습니다.
- `$$target_file_path`: 게임 폴더 내 파일 복사 위치
- `$$selection_succeeded`: 파일이 복사되었으면 `true`
- `$$selection_cancelled`: 파일을 선택하지 않고 파일 선택기를 닫았으면 `true`
- `$$failure_reason`: 실패 원인. 실패하지 않았으면 비어 있습니다.

### 작업으로 ZIP 파일을 압축 해제했을 때

**식별자:** `zip_extracted_via_action`

[**게임 디렉터리에서 ZIP 파일 압축 해제**](/action-scripts#extract-zip-file-in-game-directory) 작업이 완료되면 실행됩니다.

- `$$source_zip_path`: ZIP 파일 경로
- `$$target_folder_path`: 압축 해제된 폴더 경로
- `$$extract_succeeded`: `true` 또는 `false`
- `$$failure_reason`: 실패 원인. 실패하지 않았으면 비어 있습니다.

게임 폴더 내 경로는 `/config/fancymenu/assets/pack.zip`처럼 `/`로 시작합니다. `.minecraft` 폴더 내 경로는 `.minecraft/`로 시작합니다.

### FM 데이터를 받았을 때

**식별자:** `fm_data_received`

서버가 `/fmdata send`를 사용해 이 플레이어에게 데이터를 보내면 실행됩니다. [FM 데이터](/fm-data)를 참고하세요.

- `$$data_identifier`: 데이터를 보낼 때 사용한 식별자
- `$$data`: 데이터 내용
- `$$sent_by`: 서버의 IP 주소. 싱글플레이에서는 `integrated_server`

### 원격 서버에 연결되었을 때

**식별자:** `remote_server_connected`

[원격 서버 연결](/remote-server-communication)이 열리면 실행됩니다.

- `$$request_id`: 연결의 요청 ID
- `$$remote_server_url`: 원격 서버 링크

### 원격 서버에서 데이터를 받았을 때

**식별자:** `remote_server_data_received`

연결된 원격 서버가 텍스트를 보낼 때마다 실행됩니다.

- `$$request_id`: 연결의 요청 ID
- `$$remote_server_url`: 원격 서버 링크
- `$$data`: 서버가 보낸 텍스트

### 원격 서버 연결이 종료되었을 때

**식별자:** `remote_server_connection_closed`

원격 서버 연결이 종료되면 실행됩니다.

- `$$request_id`: 연결의 요청 ID
- `$$remote_server_url`: 원격 서버 링크
- `$$intentionally_closed`: [**원격 서버 연결 종료**](/action-scripts#close-remote-server-connection) 작업으로 연결을 종료했으면 `true`
- `$$crashed`: 연결이 비정상 종료되었으면 `true`
- `$$unknown_close_reason`: 알 수 없는 이유로 연결이 종료되었으면 `true`

## 게임, 월드 및 서버

### Minecraft를 종료할 때

**식별자:** `quit_minecraft`

게임 종료가 시작되면 한 번 실행됩니다.

- `$$timestamp_millis`: 1970년부터 경과한 시간을 밀리초 단위로 표시
- `$$timestamp_iso`: `2026-11-24T18:30:00.123Z`와 같은 ISO-8601 형식의 시간

### 스크린샷을 찍었을 때

**식별자:** `screenshot_taken`

스크린샷 키를 누르는 등의 방법으로 스크린샷을 찍고 저장하면 실행됩니다.

- `$$screenshot_path`: `/screenshots/2026-10-29_14.30.00.png`처럼 게임 폴더 내 스크린샷 경로

### 싱글플레이 월드에 들어갔을 때

**식별자:** `world_entered`

싱글플레이 월드 로딩이 완료되어 움직일 수 있게 되면 실행됩니다.

- `$$world_name`: 월드 이름
- `$$world_save_path`: 월드 저장 폴더의 전체 경로
- `$$world_difficulty`: 월드 난이도
- `$$world_cheats_allowed`: 치트가 활성화되어 있으면 `true`
- `$$world_icon_path`: 월드 아이콘의 전체 경로
- `$$world_is_first_join`: 월드 생성 후 처음 방문한 경우 `true`

### 싱글플레이 월드에서 나왔을 때

**식별자:** `world_left`

싱글플레이 월드가 닫히고 저장되면 실행됩니다.

`$$world_is_first_join`을 제외하고 **싱글플레이 월드에 들어갔을 때**와 같은 변수를 제공합니다. `$$world_name`, `$$world_save_path`, `$$world_difficulty`, `$$world_cheats_allowed`, `$$world_icon_path`를 사용할 수 있습니다.

### 서버 접속을 시작할 때

**식별자:** `start_joining_server`

서버 또는 Realm에 접속을 시작할 때, 접속이 완료되기 전에 실행됩니다. 연결이 실패하거나 취소된 경우에도 실행되므로, 연결 끊김 화면에 재접속 버튼을 표시하는 것처럼 서버 정보를 기억해 둘 수 있습니다.

- `$$server_ip`: 서버 IP 주소

### 서버에 접속했을 때

**식별자:** `server_joined`

멀티플레이어 서버에 접속한 뒤 실행됩니다.

- `$$server_ip`: 서버 IP 주소

### 서버에서 나왔을 때

**식별자:** `server_left`

멀티플레이어 서버에서 나온 뒤 실행됩니다.

- `$$server_ip`: 서버 IP 주소

### 다른 플레이어가 월드/서버에 접속했을 때

**식별자:** `other_player_joined_world`

다른 플레이어가 내 월드나 서버에 접속하면 실행됩니다.

- `$$player_name`: 플레이어 이름
- `$$player_uuid`: 플레이어 UUID

### 다른 플레이어가 월드/서버에서 나갔을 때

**식별자:** `other_player_left_world`

다른 플레이어가 내 월드나 서버에서 나가면 실행됩니다.

- `$$player_name`: 플레이어 이름
- `$$player_uuid`: 플레이어 UUID

### 다른 플레이어가 죽었을 때

**식별자:** `other_player_died`

내 월드에 있는 다른 플레이어가 죽으면 실행됩니다.

- `$$player_name`: 플레이어 이름
- `$$player_uuid`: 플레이어 UUID
- `$$death_pos_x`, `$$death_pos_y`, `$$death_pos_z`: 플레이어가 죽은 위치

## 채팅

### 채팅 메시지를 받았을 때

**식별자:** `chat_message_received`

플레이어의 채팅 메시지가 내 채팅창에 표시되면 실행됩니다.

- `$$chat_message_string`: 일반 텍스트 형식의 메시지
- `$$chat_message_component`: JSON 텍스트 컴포넌트 형식의 메시지
- `$$sender_uuid`: 보낸 사람의 UUID. 알 수 없으면 `ERROR`
- `$$sender_name`: 보낸 사람의 이름. 알 수 없으면 `ERROR`

### 채팅 메시지를 보냈을 때

**식별자:** `chat_message_sent`

채팅 메시지를 보내면 실행됩니다. 명령어는 해당되지 않습니다.

- `$$chat_message_string`: 일반 텍스트 형식의 메시지
- `$$chat_message_component`: JSON 텍스트 컴포넌트 형식의 메시지

### 채팅에서 시스템 메시지를 받았을 때

**식별자:** `system_message_received_in_chat`

명령어 실행 결과처럼 플레이어가 보내지 않은 메시지가 채팅창에 표시되면 실행됩니다.

- `$$system_message_string`: 일반 텍스트 형식의 메시지
- `$$system_message_component`: JSON 텍스트 컴포넌트 형식의 메시지

## 플레이어

### 사망했을 때

**식별자:** `player_death`

사망 화면이 열린 직후 실행됩니다.

- `$$days_survived`: 마지막으로 사망한 뒤 생존한 게임 내 일수. 소수점은 버림 처리됩니다.
- `$$death_reason_string`: 일반 텍스트 형식의 사망 메시지
- `$$death_reason_component`: JSON 텍스트 컴포넌트 형식의 사망 메시지
- `$$death_pos_x`, `$$death_pos_y`, `$$death_pos_z`: 사망한 위치

### 피해를 입었을 때

**식별자:** `damage_taken`

피해를 입을 때마다 한 번 실행됩니다.

- `$$damage_amount`: 피해로 감소한 체력
- `$$damage_type`: 피해 유형(예: `minecraft:fall`)
- `$$is_fatal_damage`: 피해를 입고 사망했으면 `true`
- `$$damage_source`: 피해를 준 엔티티 유형(예: `minecraft:zombie`). 해당하지 않으면 `NONE`

### 효과를 얻었을 때

**식별자:** `effect_gained`

상태 효과를 얻으면 한 번 실행됩니다.

- `$$effect_key`: 효과(예: `minecraft:speed`)
- `$$effect_type`: `positive`, `negative` 또는 `neutral`
- `$$effect_duration`: 효과 지속 시간(틱 단위, 20틱은 1초)

### 효과가 사라졌을 때

**식별자:** `effect_lost`

상태 효과가 끝나면 한 번 실행됩니다.

- `$$effect_key`: 효과(예: `minecraft:speed`)
- `$$effect_type`: `positive`, `negative` 또는 `neutral`

### 경험치가 변경되었을 때

**식별자:** `experience_changed`

경험치가 증가하거나 감소할 때마다 실행됩니다.

- `$$new_experience_amount`: 현재 총 경험치
- `$$old_experience_amount`: 이전 총 경험치
- `$$is_level_up`: 새 레벨을 얻었으면 `true`

### 도전 과제를 달성했을 때

**식별자:** `achievement_unlocked`

도전 과제(발전 과제)를 달성하면 한 번 실행됩니다. 월드에 접속했을 때처럼 이미 완료된 도전 과제는 해당되지 않습니다.

- `$$achievement_key`: 도전 과제(예: `minecraft:story/mine_diamond`)
- `$$achievement_label`: 게임 언어로 표시된 도전 과제 제목
- `$$achievement_description`: 게임 언어로 표시된 도전 과제 설명
- `$$achievement_icon_item_key`: 아이콘에 사용된 아이템(예: `minecraft:diamond`)
- `$$achievement_type`: `advancement`, `goal` 또는 `challenge`

### 점프했을 때

**식별자:** `jump`

점프할 때마다 실행됩니다. 변수는 없습니다.

### 달리기 시작했을 때

**식별자:** `started_running`

전력 질주를 시작하면 한 번 실행됩니다. 변수는 없습니다.

### 달리기를 멈췄을 때

**식별자:** `stopped_running`

전력 질주를 멈추면 한 번 실행됩니다. 변수는 없습니다.

### 위치가 변경되었을 때

**식별자:** `position_changed`

다른 블록으로 이동할 때마다 실행됩니다.

- `$$old_pos_x`, `$$old_pos_y`, `$$old_pos_z`: 이전 블록 위치
- `$$new_pos_x`, `$$new_pos_y`, `$$new_pos_z`: 새 블록 위치

### 불타기 시작했을 때

**식별자:** `started_burning`

불타기 시작하면 한 번 실행됩니다. 변수는 없습니다.

### 불타기를 멈췄을 때

**식별자:** `stopped_burning`

불타기를 멈추면 한 번 실행됩니다. 변수는 없습니다.

### 익사 피해를 받기 시작했을 때

**식별자:** `started_drowning`

익사 피해를 받기 시작하면 한 번 실행됩니다. 변수는 없습니다.

### 얼기 시작했을 때

**식별자:** `started_freezing`

가루눈에 들어갔을 때처럼 얼기 시작하면 한 번 실행됩니다.

- `$$freezing_intensity`: 얼어붙은 정도. `0.0`(전혀 얼지 않음)부터 `1.0`(완전히 얼어붙음)까지 표시됩니다.

### 얼기를 멈췄을 때

**식별자:** `stopped_freezing`

얼기를 멈추면 한 번 실행됩니다. 변수는 없습니다.

### 완전히 얼었을 때

**식별자:** `fully_frozen`

완전히 얼면 한 번 실행됩니다. 변수는 없습니다.

### 수영을 시작했을 때

**식별자:** `start_swimming`

수영을 시작하면 한 번 실행됩니다.

- `$$fluid_type`: 유체 종류(예: `minecraft:water`)

### 수영을 멈췄을 때

**식별자:** `stop_swimming`

수영을 멈추면 한 번 실행됩니다.

- `$$fluid_type`: 유체 종류(예: `minecraft:water`)

### 유체에 닿기 시작했을 때

**식별자:** `start_touching_fluid`

물이나 용암 같은 유체에 닿기 시작하면 한 번 실행됩니다.

- `$$fluid_type`: 유체 종류(예: `minecraft:lava`)

### 유체에서 떨어졌을 때

**식별자:** `stop_touching_fluid`

유체에서 떨어지면 한 번 실행됩니다.

- `$$fluid_type`: 유체 종류(예: `minecraft:lava`)

## 아이템

### 아이템을 주웠을 때

**식별자:** `item_picked_up`

아이템을 주우면 한 번 실행됩니다.

- `$$item_key`: 아이템(예: `minecraft:diamond`)

### 아이템을 버렸을 때

**식별자:** `item_dropped`

인벤토리의 아이템을 버리면 한 번 실행됩니다.

- `$$item_key`: 아이템(예: `minecraft:diamond`)

### 아이템을 소비했을 때

**식별자:** `item_consumed`

아이템을 먹거나 마시는 동작을 마치면 한 번 실행됩니다.

- `$$item_key`: 아이템(예: `minecraft:golden_apple`)

### 아이템을 사용했을 때

**식별자:** `item_used`

아이템을 사용하면 한 번 실행됩니다.

- `$$item_key`: 아이템(예: `minecraft:flint_and_steel`)
- `$$used_on_type`: 사용 대상 유형: `block`, `entity`, `self` 또는 `none`
- `$$used_on_entity_key`: 아이템을 사용한 대상 엔티티 유형. 대상이 없으면 비어 있습니다.
- `$$used_on_block_key`: 아이템을 사용한 대상 블록. 대상이 없으면 비어 있습니다.
- `$$target_pos_x`, `$$target_pos_y`, `$$target_pos_z`: 아이템을 사용한 위치. 대상이 없으면 `-1`

### 아이템이 부서졌을 때

**식별자:** `item_broke`

인벤토리에 있는 아이템이 부서지면 한 번 실행됩니다.

- `$$item_key`: 아이템(예: `minecraft:iron_pickaxe`)
- `$$item_type`: `tool`, `armor` 또는 `other`

### 인벤토리에서 아이템 위에 마우스를 올렸을 때

**식별자:** `item_hovered_in_inventory`

내 인벤토리나 상자처럼 모든 인벤토리에서 아이템 위로 마우스를 움직이면 한 번 실행됩니다.

- `$$item_key`: 아이템(예: `minecraft:diamond_sword`)
- `$$item_display_name_string`: 일반 텍스트 형식의 아이템 이름
- `$$item_display_name_json`: JSON 텍스트 컴포넌트 형식의 아이템 이름

## 블록

### 블록을 바라보기 시작했을 때

**식별자:** `start_looking_at_block`

최대 20블록 떨어진 블록을 십자선으로 처음 가리키면 한 번 실행됩니다.

- `$$block_key`: 블록(예: `minecraft:oak_log`)
- `$$block_pos_x`, `$$block_pos_y`, `$$block_pos_z`: 블록 위치
- `$$distance_to_player`: 눈에서 십자선이 가리키는 지점까지의 거리

### 블록을 더 이상 바라보지 않을 때

**식별자:** `stop_looking_at_block`

십자선으로 블록을 더 이상 가리키지 않으면 한 번 실행됩니다.

이전에 바라보던 블록에 대해 **블록을 바라보기 시작했을 때**와 같은 변수인 `$$block_key`, `$$block_pos_x`, `$$block_pos_y`, `$$block_pos_z`, `$$distance_to_player`를 제공합니다.

### 블록을 부쉈을 때

**식별자:** `block_broke`

블록을 부수면 한 번 실행됩니다.

- `$$block_key`: 블록(예: `minecraft:stone`)
- `$$broke_with_item_key`: 손에 든 아이템(예: `minecraft:iron_pickaxe`). 손에 든 아이템이 없으면 `EMPTY`
- `$$block_pos_x`, `$$block_pos_y`, `$$block_pos_z`: 블록 위치

### 블록을 설치했을 때

**식별자:** `block_placed`

블록을 설치하면 한 번 실행됩니다.

- `$$block_key`: 블록(예: `minecraft:torch`)
- `$$block_pos_x`, `$$block_pos_y`, `$$block_pos_z`: 블록 위치

### 블록과 상호작용했을 때

**식별자:** `interacted_with_block`

상자를 열거나 버튼을 누르는 등 블록을 사용하면 한 번 실행됩니다.

- `$$block_key`: 블록(예: `minecraft:chest`)
- `$$block_pos_x`, `$$block_pos_y`, `$$block_pos_z`: 블록 위치

### 블록 위에 올라섰을 때

**식별자:** `stepping_on_block`

블록 위에 올라서면 한 번 실행됩니다.

- `$$block_key`: 블록(예: `minecraft:grass_block`)
- `$$block_pos_x`, `$$block_pos_y`, `$$block_pos_z`: 블록 위치

## 엔티티

### 엔티티를 바라보기 시작했을 때

**식별자:** `start_looking_at_entity`

최대 20블록 떨어진 엔티티를 십자선으로 처음 가리키면 한 번 실행됩니다.

- `$$entity_key`: 엔티티 유형(예: `minecraft:villager`)
- `$$distance_to_player`: 눈에서 십자선이 가리키는 지점까지의 거리
- `$$entity_pos_x`, `$$entity_pos_y`, `$$entity_pos_z`: 엔티티 위치
- `$$entity_uuid`: 엔티티 UUID

### 엔티티를 더 이상 바라보지 않을 때

**식별자:** `stop_looking_at_entity`

십자선으로 엔티티를 더 이상 가리키지 않으면 한 번 실행됩니다.

이전에 바라보던 엔티티에 대해 **엔티티를 바라보기 시작했을 때**와 같은 변수인 `$$entity_key`, `$$distance_to_player`, `$$entity_pos_x`, `$$entity_pos_y`, `$$entity_pos_z`, `$$entity_uuid`를 제공합니다.

### 엔티티가 시야에 들어왔을 때

**식별자:** `entity_starts_being_in_sight`

최대 200블록 떨어진 엔티티가 화면에 보이게 되면 한 번 실행됩니다.

- `$$entity_key`: 엔티티 유형(예: `minecraft:creeper`)
- `$$distance_to_player`: 눈에서 엔티티까지의 거리
- `$$entity_pos_x`, `$$entity_pos_y`, `$$entity_pos_z`: 엔티티 위치
- `$$entity_uuid`: 엔티티 UUID

### 엔티티가 시야에서 사라졌을 때

**식별자:** `entity_stops_being_in_sight`

화면에 보이던 엔티티가 화면 밖으로 나가거나 200블록보다 멀어지면 한 번 실행됩니다.

**엔티티가 시야에 들어왔을 때**와 같은 변수인 `$$entity_key`, `$$distance_to_player`, `$$entity_pos_x`, `$$entity_pos_y`, `$$entity_pos_z`, `$$entity_uuid`를 제공합니다.

### 엔티티와 상호작용했을 때

**식별자:** `entity_interacted`

주민과 거래하는 것처럼 엔티티를 사용하면 한 번 실행됩니다.

- `$$entity_key`: 엔티티 유형(예: `minecraft:villager`)
- `$$entity_pos_x`, `$$entity_pos_y`, `$$entity_pos_z`: 엔티티 위치
- `$$entity_uuid`: 엔티티 UUID

### 엔티티에 탔을 때

**식별자:** `entity_mounted`

말이나 보트 같은 엔티티를 타기 시작하면 한 번 실행됩니다.

- `$$entity_key`: 엔티티 유형(예: `minecraft:horse`)
- `$$entity_pos_x`, `$$entity_pos_y`, `$$entity_pos_z`: 엔티티 위치
- `$$entity_uuid`: 엔티티 UUID

### 엔티티에서 내렸을 때

**식별자:** `entity_unmounted`

엔티티에서 내리면 한 번 실행됩니다.

- `$$entity_key`: 엔티티 유형(예: `minecraft:horse`)
- `$$entity_pos_x`, `$$entity_pos_y`, `$$entity_pos_z`: 엔티티 위치
- `$$entity_uuid`: 엔티티 UUID

### 엔티티가 생성되었을 때

**식별자:** `entity_spawned`

서버에 FancyMenu가 설치되어 있어야 합니다. 멀리 떨어진 곳이나 다른 차원을 포함해 월드 어디에서든 엔티티가 생성되면 실행됩니다.

- `$$entity_key`: 엔티티 유형(예: `minecraft:zombie`)
- `$$distance_to_player`: 플레이어와의 거리. 다른 차원에 있으면 `-1`
- `$$entity_pos_x`, `$$entity_pos_y`, `$$entity_pos_z`: 생성된 위치
- `$$entity_uuid`: 엔티티 UUID
- `$$dimension_key`: 차원(예: `minecraft:overworld`)
- `$$is_same_dimension_as_player`: 플레이어와 같은 차원에서 생성되었으면 `true`

### 엔티티가 사망했을 때

**식별자:** `entity_died`

서버에 FancyMenu가 설치되어 있어야 합니다. 멀리 떨어진 곳이나 다른 차원을 포함해 월드 어디에서든 엔티티가 사망하면 실행됩니다.

- `$$entity_key`: 엔티티 유형(예: `minecraft:ender_dragon`)
- `$$distance_to_player`: 플레이어와의 거리. 다른 차원에 있으면 `-1`
- `$$death_pos_x`, `$$death_pos_y`, `$$death_pos_z`: 사망 위치
- `$$entity_uuid`: 엔티티 UUID
- `$$dimension_key`: 차원(예: `minecraft:the_end`)
- `$$damage_type`: 엔티티를 죽인 피해 유형(예: `minecraft:player_attack`)
- `$$is_same_dimension_as_player`: 플레이어와 같은 차원에서 사망했으면 `true`
- `$$entity_killed_by_name`: 처치한 사람의 이름. 알 수 없으면 `NONE`
- `$$entity_killed_by_key`: 처치한 사람의 유형(예: `minecraft:player`). 알 수 없으면 `NONE`
- `$$entity_killed_by_uuid`: 처치한 사람의 UUID. 알 수 없으면 `NONE`

## 월드 및 장소

### 생물 군계에 들어갔을 때

**식별자:** `enter_biome`

다른 생물 군계에 들어가면 한 번 실행됩니다.

- `$$biome_key`: 생물 군계(예: `minecraft:cherry_grove`)

### 생물 군계에서 나왔을 때

**식별자:** `leave_biome`

생물 군계에서 나오면 한 번 실행됩니다.

- `$$biome_key`: 나간 생물 군계(예: `minecraft:cherry_grove`)

### 구조물에 들어갔을 때

**식별자:** `enter_structure`

서버에 FancyMenu가 설치되어 있어야 합니다. 구조물 영역에 들어가면 한 번 실행됩니다. 영역의 판정이 대략적이므로 구조물 근처나 위쪽에서도 실행될 수 있습니다. 예를 들어 지하 폐광 위에 있어도 실행될 수 있습니다. 구조물 내부에 있을 때만 실행하려면 **구조물에 들어갔을 때(고정밀)**를 사용하세요.

- `$$structure_key`: 구조물(예: `minecraft:village_plains`)

### 구조물에서 나왔을 때

**식별자:** `leave_structure`

서버에 FancyMenu가 설치되어 있어야 합니다. **구조물에 들어갔을 때**와 마찬가지로 대략적으로 판정되는 구조물 영역에서 나오면 한 번 실행됩니다.

- `$$structure_key`: 나간 구조물

### 구조물에 들어갔을 때(고정밀)

**식별자:** `enter_structure_high_precision`

서버에 FancyMenu가 설치되어 있어야 합니다. 구조물 내부에 들어서면 한 번 실행됩니다.

- `$$structure_key`: 구조물(예: `minecraft:stronghold`)

### 구조물에서 나왔을 때(고정밀)

**식별자:** `leave_structure_high_precision`

서버에 FancyMenu가 설치되어 있어야 합니다. 구조물 밖으로 완전히 나오면 한 번 실행됩니다.

- `$$structure_key`: 나간 구조물

### 차원에 들어갔을 때

**식별자:** `enter_dimension`

다른 차원에 들어가면 한 번 실행됩니다.

- `$$dimension_key`: 차원(예: `minecraft:the_nether`)

### 날씨가 바뀌었을 때

**식별자:** `weather_changed`

날씨가 바뀌면 한 번 실행됩니다. 현재 위치에서 날씨가 달라지는 경우에도 실행됩니다. 비가 오는 중에 사막, 눈 내리는 생물 군계 또는 건물 안으로 들어가는 경우도 해당됩니다.

- `$$weather_type`: `clear`, `rain` 또는 `thunder`
- `$$weather_can_snow`: 현재 위치에 눈이 내릴 수 있으면 `true`
- `$$weather_can_rain`: 현재 위치에 비가 내릴 수 있으면 `true`

### 습격이 시작되었을 때

**식별자:** `raid_started`

서버에 FancyMenu가 설치되어 있어야 합니다. 습격 영역 안에 있을 때 습격이 시작되어 습격 막대가 표시되면 실행됩니다. 변수는 없습니다.

이미 진행 중인 습격 영역에 들어가는 경우에는 실행되지 않습니다. 이 경우에는 **진행 중인 습격 영역에 들어갔을 때**를 사용하세요.

### 진행 중인 습격 영역에 들어갔을 때

**식별자:** `enter_active_raid_area`

서버에 FancyMenu가 설치되어 있어야 합니다. 이미 진행 중인 습격 영역에 들어가 습격 막대가 표시되면 실행됩니다. 변수는 없습니다.

### 진행 중인 습격 영역에서 나왔을 때

**식별자:** `leave_active_raid_area`

서버에 FancyMenu가 설치되어 있어야 합니다. 습격 영역에서 나와 습격 막대가 사라지면 실행됩니다. 해당 영역에서 사망하거나 차원을 변경해도 실행되지만, 습격이 끝나는 경우에는 실행되지 않습니다. 변수는 없습니다.

### 습격이 끝났을 때

**식별자:** `raid_finished`

서버에 FancyMenu가 설치되어 있어야 합니다. 습격 영역 안에 있을 때 습격이 끝나면 실행됩니다.

- `$$raid_result`: `victory` 또는 `defeat`

## 사운드 및 음악

### 음악 트랙 재생이 시작되었을 때

**식별자:** `music_track_started`

음악 트랙 재생이 시작되면 한 번 실행됩니다.

- `$$track_resource_location`: 트랙의 사운드 파일
- `$$track_display_name`: 트랙 이름. 알 수 없으면 `UNKNOWN`
- `$$track_artist`: 트랙 아티스트. 알 수 없으면 `UNKNOWN`
- `$$track_duration_ms`: 트랙 길이(밀리초). 알 수 없으면 `0`

### 음악 트랙 재생이 멈췄을 때

**식별자:** `music_track_stopped`

음악 트랙이 끝나거나 다른 트랙으로 바뀌어 재생이 멈추면 한 번 실행됩니다.

**음악 트랙 재생이 시작되었을 때**와 같은 변수인 `$$track_resource_location`, `$$track_display_name`, `$$track_artist`, `$$track_duration_ms`를 제공합니다.

### 월드 사운드가 재생되었을 때

**식별자:** `world_sound_triggered`

문이나 크리퍼 소리처럼 주변 월드에서 사운드가 재생될 때마다 실행됩니다.

- `$$sound_resource_location`: 사운드 파일
- `$$sound_display_name`: 사운드 자막. 알 수 없으면 `UNKNOWN`
- `$$sound_origin_pos_x`, `$$sound_origin_pos_y`, `$$sound_origin_pos_z`: 사운드가 발생한 위치
- `$$sound_origin_distance_to_player`: 사운드가 발생한 위치까지의 거리
- `$$sound_origin_direction_from_player`: 플레이어가 바라보는 방향을 기준으로 한 사운드 방향(0~360도)
