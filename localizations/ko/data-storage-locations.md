---
title: 데이터 저장 위치
description: 'FancyMenu가 레이아웃, 에셋, 설정 및 기타 모든 항목을 저장하는 위치와 프로필에 포함되는 파일을 설명합니다.'
sourceBlobSha: 30dd81ed90e08184e3063892870e3325d7d7c5cb
---

# 데이터 저장 위치

FancyMenu는 게임 디렉터리의 두 폴더에 모든 항목을 저장합니다. 여기서 게임 디렉터리는 런처의 인스턴스 폴더를 의미하며, `.minecraft`와 다른 폴더일 수 있습니다.

- `config/fancymenu/`에는 레이아웃, 에셋, 변수, 설정 등 구성 항목이 저장됩니다. 현재 불러온 [프로필](/profiles)에 해당하므로 모드팩에도 이 폴더가 포함됩니다.
- `fancymenu_data/`에는 Dragger 위치와 다운로드 파일처럼 이 게임 인스턴스에 속하는 데이터가 저장됩니다. 모든 프로필에서 동일하게 유지됩니다.

**메뉴 바 -> Tools -> Open FancyMenu Directory**를 선택하면 `config/fancymenu/`가 열립니다.

대부분의 파일과 폴더는 해당 기능을 사용한 뒤에야 나타납니다. 파일을 수정하거나 삭제하기 전에 게임을 종료하세요.

> [!TIP]
> 여러 인스턴스에서 이 폴더를 공유하려면 다른 위치로 옮긴 다음, 원래 위치에 심볼릭 링크(Windows에서는 디렉터리 연결)를 만들어 두면 됩니다.

# 구성 항목

`<game-directory>/config/fancymenu/`에 있는 모든 항목입니다. 전부 현재 불러온 [프로필](/profiles)에 속합니다.

| 항목 | 위치 |
| --- | --- |
| 하위 폴더에 있는 파일을 포함한 `.txt` 형식의 레이아웃 | `customization/` |
| 이미지와 사운드 등의 [로컬 에셋](/resources#local-resources) | `assets/` |
| FancyMenu 설정 | `options.txt` |
| **Current Screen Customization**이 켜진 화면 | `customizablemenus.txt` |
| [사용자 지정 GUI](/custom-guis) 및 이를 대체하는 화면 | `custom_gui_screens.txt` |
| [변수](/variables) | `user_variables.db` |
| [리스너](/listeners) | `listener_instances.txt` |
| [스케줄러](/schedulers) | `scheduler_instances.txt` |
| [파노라마](/panoramas) | `panoramas/` |
| [슬라이드쇼](/slideshows) | `slideshows/` |
| [사용자 지정 로컬라이제이션](/localization#fancymenu-custom-localization-files) | `custom_locals/` |
| FancyMenu 자체 UI의 테마 (**메뉴 바 -> Customization -> Settings -> FancyMenu's UI -> UI Theme**) | `ui_themes/` |
| 변수를 사용하지 않는 [체크박스 요소](/elements#checkbox)의 상태 | `checkbox_states.json` |
| 동작이 [비디오 요소](/video)에 설정한 볼륨 및 일시 정지 상태 | `video_element_controller_metas.json` |
| 동작이 [오디오 요소](/elements#audio)에 설정한 볼륨 | `audio_element_controller_metas.json` |
| 동작이 [요소 애니메이터](/element-animator)에 설정한 켜짐/꺼짐 상태 | `animation_controller_states.json` |
| **Expose Scroll Area Content Of Current Screen**이 켜진 화면([스크롤 가능한 화면 사용자 지정](/customizing-scrollable-screens) 참고) | `normalized_scroll_screens.json` |
| [FM Data](/fm-data) 서버 리스너 | `fmdata_server_listeners.json` |
| [FM Data](/fm-data) 시작 데이터 | `fmdata_welcome_data.json` |
| 레이아웃 편집기 위젯의 위치, 크기 및 표시 여부 | `layout_editor/widgets/` |
| 현재 불러온 프로필의 이름, 아이콘 및 세부 정보 | `profile.json` 및 `profile_icon.png` |
| 그 밖의 모든 [프로필](/profiles#where-profiles-are-stored) | `profiles/` |
| FancyMenu가 이전 파일을 업데이트했는지 여부 | `legacy_checklist.txt` |

`customizablemenus.txt`에는 화면이 Java 클래스 이름으로 나열됩니다. `title_screen`과 같은 짧은 [화면 식별자](/screen-identifiers)는 이 파일에서 제외됩니다.

전용 서버에서 FancyMenu는 서버의 `config/fancymenu/` 폴더에 있는 [FM Data](/fm-data) 파일 두 개만 사용합니다.

# 인스턴스 데이터

`<game-directory>/fancymenu_data/`에 있는 모든 항목입니다. 프로필에 포함되지 않으므로 프로필을 전환해도 유지됩니다.

| 항목 | 위치 |
| --- | --- |
| [Dragger 요소](/dragger)의 위치 | `dragger_metas.json` |
| **Enter/Join Last World/Server** 동작과 **Last World or Server** 자리 표시자에 사용되는 마지막 월드 또는 서버 | `last_world.fmdata` |
| [Seamless World Loading](/seamless-world-loading)의 스크린샷 | `seamless_world_loading/` |
| [Buddy](/decoration-overlays#buddy) 저장 데이터(각 Buddy 오버레이당 파일 두 개) | `buddy/` |
| [Export for AI](/export-for-ai) 파일 | `ai_exports/` |
| 동작 선택기에서 즐겨찾기에 추가한 동작 | `action_favorites.json` |
| 파일 선택기에서 오디오 및 비디오 미리 보기에 사용하는 볼륨 | `browser_audio_settings.json` 및 `browser_video_settings.json` |
| 일시 정지 중 [비디오 배경](/video)에 표시되는 프레임 | `video_thumbnails/` |
| FancyMenu가 [AFMA Creator](/animations#fma-and-afma)용으로 다운로드하는 FFmpeg | `ffmpeg_cache/` |
| FancyMenu가 이미 [**기본 GUI 크기**](/global-customizations)를 설정했음을 나타내는 기록 | `default_scale_set.fm` |
| 임시 파일(게임을 시작할 때마다 삭제됨) | `fancymenu_temp/` |

- FancyMenu는 **기본 GUI 크기**를 한 번만 설정합니다. 다음에 게임을 시작할 때 크기를 다시 설정하려면 `default_scale_set.fm`을 삭제하세요.
- Seamless World Loading 스크린샷에는 월드 화면에 표시된 모든 내용이 담깁니다. 보관하고 싶지 않다면 게임을 종료한 상태에서 삭제하세요.

# 이전 버전의 파일

이전 버전의 FancyMenu는 일부 파일을 다른 위치에 저장했습니다. FancyMenu는 다음에 게임을 시작할 때 해당 파일을 새 위치로 옮깁니다.

- 게임 디렉터리의 `checkbox_states.json` 및 `normalized_scroll_screens.json`을 `config/fancymenu/`로 옮깁니다.
- `config/fancymenu/`의 `dragger_metas.json`을 `fancymenu_data/`로 옮깁니다.
