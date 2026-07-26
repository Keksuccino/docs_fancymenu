---
title: 데이터 저장 위치
description: 'FancyMenu가 레이아웃, 리소스, 구성, 그리고 영구적인 런타임 상태를 저장하는 위치입니다.'
---

# 데이터 저장 위치

`<game-directory>`는 활성화된 Minecraft 인스턴스 폴더를 의미하며, `.minecraft`와 다를 수 있습니다.

디렉터리와 파일은 일반적으로 관련 기능이 초기화되거나 사용된 뒤에만 생성됩니다. 생성된 상태 파일을 수동으로 편집하기 전에 Minecraft를 종료하고, 데이터를 이전하거나 초기화할 때는 백업을 보관하세요.

# 레이아웃, 리소스, 구성

일부 항목은 작성된 구성이나 에셋이며, 다른 항목은 FancyMenu가 런타임에 업데이트하는 상태입니다.

| 시스템 / 기능 | 파일 또는 디렉터리 |
| --- | --- |
| 사용자 지정 가능한 화면 | `<game-directory>/config/fancymenu/customizablemenus.txt` |
| [사용자 지정 GUI](./custom-guis) 및 화면 재정의 규칙 | `<game-directory>/config/fancymenu/custom_gui_screens.txt` |
| 레이아웃 | `<game-directory>/config/fancymenu/customization/` |
| [로컬 에셋](./resources#local-resources) | `<game-directory>/config/fancymenu/assets/` |
| [사용자 지정 로컬라이제이션 파일](./localization#fancymenu-custom-localization-files) | `<game-directory>/config/fancymenu/custom_locals/` |
| [파노라마](./panoramas) | `<game-directory>/config/fancymenu/panoramas/` |
| [슬라이드쇼](./slideshows) | `<game-directory>/config/fancymenu/slideshows/` |
| [FancyMenu 변수](./variables) | `<game-directory>/config/fancymenu/user_variables.db` |
| [비디오 요소](./elements#video) 컨트롤러 메타데이터 | `<game-directory>/config/fancymenu/video_element_controller_metas.json` |
| [오디오 요소](./elements#audio) 컨트롤러 메타데이터 | `<game-directory>/config/fancymenu/audio_element_controller_metas.json` |
| [FM Data](./fm-data) 서버 리스너 | `<game-directory>/config/fancymenu/fmdata_server_listeners.json` |
| [FM Data](./fm-data) 환영 데이터 | `<game-directory>/config/fancymenu/fmdata_welcome_data.json` |
| [리스너](./listeners) 인스턴스 및 액션 스크립트 | `<game-directory>/config/fancymenu/listener_instances.txt` |
| [스케줄러](./schedulers) | `<game-directory>/config/fancymenu/scheduler_instances.txt` |

`customizablemenus.txt`는 **현재 화면 사용자 지정** 토글에 의해 관리되며, 구체적인 화면 클래스 식별자를 저장합니다. [범용 레이아웃](./universal-layouts) 식별자는 추가하지 마세요. FancyMenu는 파일을 불러올 때 이를 무시합니다.

전용 서버에서는 두 FM Data 파일이 해당 서버의 게임 루트를 기준으로 합니다. 그 밖의 클라이언트 소유 구성과 리소스는 각 플레이어의 인스턴스에 속합니다.

# 영구 런타임 상태

FancyMenu는 `config/fancymenu/` 밖에도 인스턴스별로 생성된 추가 상태를 저장합니다. 관련 사용자/런타임 상태를 보존하려는 경우에만 이 경로들을 백업에 포함하세요. 이들은 레이아웃 정의나 원본 에셋이 아닙니다.

| 시스템 / 기능 | 파일 또는 디렉터리 |
| --- | --- |
| 변수가 아닌 [체크박스](./elements#checkbox) 상태 | `<game-directory>/checkbox_states.json` |
| [드래거](./dragger) 요소 위치/메타데이터 | `<game-directory>/fancymenu_data/dragger_metas.json` |
| 마지막 월드 상태 | `<game-directory>/fancymenu_data/last_world.fmdata` |
| [매끄러운 월드 로딩](./seamless-world-loading) 상태 | `<game-directory>/fancymenu_data/seamless_world_loading/` |
| Buddy 펫 및 레벨링 저장 | `<game-directory>/fancymenu_data/buddy/` |
| 레이아웃 편집기 위젯 위치 및 표시 여부 | `<game-directory>/config/fancymenu/layout_editor/widgets/` |
| 기본 GUI 스케일 초기화 마커 | `<game-directory>/fancymenu_data/default_scale_set.fm` |

Buddy는 펫 상태와 레벨링/업적 상태를 해당 디렉터리 안의 별도 JSON 파일에 저장합니다. 각 Buddy 오버레이 인스턴스는 자체 파일 쌍을 사용합니다.

레이아웃 편집기 위젯 파일에는 각 위젯의 위치, 크기, 표시 여부, 확장 상태, 그리고 스냅되는 측면이 저장됩니다. `default_scale_set.fm`을 삭제하면 다음 실행 시 FancyMenu는 설정된 기본 GUI 스케일이 아직 적용되지 않은 것으로 처리합니다.
