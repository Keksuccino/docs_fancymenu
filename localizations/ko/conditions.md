---
title: 조건(요구 사항)
description: 로딩 요구 사항을 사용하는 방법입니다.
---
# 요구 사항

요구 사항(일부 메뉴에서는 **로딩 요구 사항**이라고도 함)은 호버 상태, 창 크기, 월드 로드 여부와 같은 조건에 따라 콘텐츠를 표시하거나 숨깁니다.

이 기능은 [요소](./elements), 전체 레이아웃, 그리고 [액션 스크립트](./action-scripts)에 사용할 수 있습니다.

# 요소에 요구 사항 추가하기

요소에 요구 사항을 추가하려면 요소를 마우스 오른쪽 버튼으로 클릭한 다음 **로딩 요구 사항**을 선택하세요.

요구 사항은 메뉴가 열려 있는 동안 검사되므로, 조건이 바뀌면 요소도 함께 업데이트됩니다.

# 레이아웃 전체 요구 사항

**편집기 배경**을 마우스 오른쪽 버튼으로 클릭한 다음 **로딩 요구 사항 [레이아웃 전체]**를 클릭하여 전체 레이아웃의 표시 여부도 변경할 수 있습니다.

레이아웃 전체 결과가 변경되면 FancyMenu가 현재 화면을 다시 구성하고, 이제 요구 사항을 만족하는 레이아웃을 적용합니다.

# 액션 스크립트

요구 사항은 액션 스크립트에서도 사용할 수 있습니다.
액션 스크립트 편집기 화면에서 추가할 수 있으며, 요구 사항의 조건이 충족될 때만 특정 동작이 실행되도록 설정할 수 있습니다.

# 요구 사항 결합하기

- 그룹 밖의 요구 사항은 **AND**로 처리되므로 모두 충족되어야 합니다.
- 그룹 내부에서는 **AND** 또는 **OR**를 선택할 수 있습니다.
- **IF NOT**을 사용해 하나의 요구 사항을 반전할 수 있습니다.

이 규칙은 요소, 레이아웃, 액션 스크립트 모두에 동일하게 적용됩니다.

# 요구 사항 값

값이 필요한 요구 사항은 **요구 사항 값 편집**을 사용하고 편집기에 표시된 설명을 따르세요. 일부 필드는 **TAB** 자동 완성을 지원합니다.

가져온 요구 사항이 FancyMenu 또는 애드온을 변경한 뒤 더 이상 작동하지 않는다면, 요구 사항 화면에서 편집한 후 `logs/latest.log`에서 오류를 확인하세요.

요구 사항 편집기는 마우스 오른쪽 버튼 컨텍스트 메뉴, 키보드 탐색, 검색, 실행 취소/다시 실행(`Ctrl/Command + Z` / `Ctrl/Command + Y`), 그리고 저장을 위한 `Ctrl/Command + S`를 지원합니다.

# 요구 사항 자세히 보기

이 섹션에는 FancyMenu의 기본 제공 요구 사항이 나열되어 있습니다.

## 요소가 호버됨 (`fancymenu_visibility_requirement_is_element_hovered`)

**목적:** 특정 요소 위에 마우스 커서가 올라가 있는지 확인합니다.

**값:** 필요함 — 대상 요소의 [요소 식별자](./element-identifiers) (예: `some_element_ID`)

## 요소에 포커스됨 (`is_element_focused`)

**목적:** 특정 요소가 현재 키보드 포커스를 가지고 있는지 확인합니다(예: 텍스트 필드나 포커스된 버튼).

**값:** 필요함 — 대상 요소의 요소 ID(편집기에 표시되는 동일한 ID)

> [!NOTE]
> 포커스와 호버는 서로 다른 상태입니다. 포인터가 요소를 벗어나도 요소가 포커스된 외형을 유지할 수 있으며, 클릭이나 키보드 탐색으로 포커스가 부여될 수 있습니다.

## 아무 요소나 호버됨 (`fancymenu_visibility_requirement_is_any_element_hovered`)

**목적:** 스택된 레이아웃에서 제공되는 요소를 포함하여, 현재 활성 커스터마이징 레이어에서 보이거나 렌더링 가능한 요소를 확인합니다.

**값:** 필요 없음

## 아무 버튼이나 호버됨 (`fancymenu_visibility_requirement_is_any_button_hovered`)

**목적:** 스택된 레이아웃에서 제공되는 버튼을 포함하여, 현재 활성 커스터마이징 레이어에서 보이거나 렌더링 가능한 바닐라 또는 커스텀 버튼이 호버 중인지 확인합니다.

**값:** 필요 없음

## 레이아웃 활성화됨 (`fancymenu_visibility_requirement_is_layout_enabled`)

**목적:** 특정 레이아웃이 현재 활성화되어 있는지 확인합니다.

**값:** 필요함 — 레이아웃 이름 (예: `my_cool_main_menu_layout`)

## 스케줄러 실행 중 (`fancymenu_visibility_requirement_is_scheduler_running`)

**목적:** [스케줄러](./schedulers)가 현재 실행 중인지 확인합니다.

**값:** 필요함 — 스케줄러 ID (예: `my_scheduler`)

## GUI 배율 (`fancymenu_loading_requirement_is_gui_scale`)

**목적:** 현재 GUI 배율이 특정 조건과 일치하는지 확인합니다.

**값:** 필요함 — 같음을 의미하는 숫자, 큼을 의미하는 `>`, 작음을 의미하는 `<`를 사용합니다.

쉼표로 구분된 여러 조건은 AND로 결합됩니다. 예를 들어 `>1,<4`는 GUI 배율이 `1`보다 크고 `4`보다 작을 때만 통과합니다.

## 버튼 활성화됨 (`fancymenu_visibility_requirement_is_button_active`)

**목적:** 특정 버튼이 활성 상태인지(클릭 가능한지) 확인합니다.

**값:** 필요함 — 대상 버튼의 요소 ID (예: "some_element_ID")

## 화면 제목 (`is_menu_title`)

**목적:** 화면의 표시 제목이 특정 텍스트 또는 지역화 키와 일치하는지 확인합니다. 이 항목은 "옵션"이나 "일시정지" 같은 화면의 표시 이름/제목만 확인하며, 메뉴/화면 식별자(예: `title_screen`)는 확인하지 않습니다!

**값:** 필요함 — 화면의 정확한 제목 텍스트 또는 지역화 키

## 키가 눌림 (`is_key_pressed`)

**목적:** 특정 키보드 키가 현재 눌려 있는지 확인합니다.

**값:** 필요함 — 대상 키의 키 코드. 요구 사항 값을 편집할 때 UI에서 선택합니다.

## 아무 화면이나 열림 (`is_any_screen_open`)

**목적:** 현재 어떤 화면/메뉴라도 열려 있는지 확인합니다(화면이 없으면 false 반환).

**값:** 필요 없음

## MC 디버그 오버레이 활성화됨 (`is_debug_overlay_enabled`)

**목적:** F3 디버그 오버레이가 현재 보이는지 확인합니다.

**값:** 필요 없음

## 활성 커서 유형 (`is_active_cursor_type`)

**목적:** FancyMenu의 현재 활성 커서 유형이 특정 표준 커서 유형과 일치하는지 확인합니다.

**값:** 필요함 — 커서 유형: `normal`, `writing`, `crosshair`, `pointing_hand`, `resize_horizontal`, `resize_vertical`, `resize_nwse`, `resize_nesw`, `resize_all`, 또는 `not_allowed`

## 커스터마이징 메뉴 바 표시됨 (`is_customization_menu_bar_visible`)

**목적:** FancyMenu의 커스터마이징 메뉴 바가 현재 보이는지 확인합니다.

**값:** 필요 없음

## 모드팩 모드 활성화됨 (`is_modpack_mode_enabled`)

**목적:** FancyMenu의 모드팩 모드가 활성화되어 있는지 확인합니다.

**값:** 필요 없음

## 마우스 버튼이 눌림 (`mouse_click`)

**목적:** 특정 마우스 버튼이 눌려 있는 동안 true를 반환합니다. 이는 일회성 클릭 이벤트가 아니므로, 동작을 클릭당 한 번만 실행해야 할 때는 [**마우스 버튼 클릭 시** 리스너](./listeners#on-mouse-button-clicked-mouse_button_clicked)를 사용하세요.

**값:** 필요함 — 확인할 마우스 버튼을 나타내는 `left` 또는 `right`

## 전체화면 (`fancymenu_loading_requirement_is_fullscreen`)

**목적:** 게임이 현재 전체화면 모드인지 확인합니다.

**값:** 필요 없음

## 창 너비 (`fancymenu_loading_requirement_is_window_width`)

**목적:** 게임 창 너비가 특정 값과 일치하는지 확인합니다.

**값:** 필요함 — 픽셀 단위 창 너비 (예: "1920"). 쉼표로 구분해 여러 값을 입력할 수 있습니다.

## 창 높이 (`fancymenu_loading_requirement_is_window_height`)

**목적:** 게임 창 높이가 특정 값과 일치하는지 확인합니다.

**값:** 필요함 — 픽셀 단위 창 높이 (예: "1080"). 쉼표로 구분해 여러 값을 입력할 수 있습니다.

## 창 너비가 더 큼 (`fancymenu_loading_requirement_is_window_width_bigger_than`)

**목적:** 게임 창 너비가 특정 값보다 큰지 확인합니다.

**값:** 필요함 — 픽셀 단위 창 너비 (예: "1920")

## 창 높이가 더 큼 (`fancymenu_loading_requirement_is_window_height_bigger_than`)

**목적:** 게임 창 높이가 특정 값보다 큰지 확인합니다.

**값:** 필요함 — 픽셀 단위 창 높이 (예: "1080")

## 멀티플레이어 (`fancymenu_loading_requirement_is_multiplayer`)

**목적:** 플레이어가 현재 멀티플레이어 월드에 있는지 확인합니다.

**값:** 필요 없음

## 싱글플레이어 (`fancymenu_loading_requirement_is_singpleplayer`)

**목적:** 플레이어가 현재 싱글플레이어 월드에 있는지 확인합니다.

**값:** 필요 없음

## 월드 로드됨 (`fancymenu_loading_requirement_is_world_loaded`)

**목적:** 현재 어떤 월드라도 로드되어 있는지 확인합니다.

**값:** 필요 없음

## 모험 모드 (`fancymenu_visibility_requirement_is_adventure`)

**목적:** 플레이어가 현재 모험 모드인지 확인합니다.

**값:** 필요 없음

## 창작 모드 (`fancymenu_visibility_requirement_is_creative`)

**목적:** 플레이어가 현재 창작 모드인지 확인합니다.

**값:** 필요 없음

## 관전자 모드 (`fancymenu_visibility_requirement_is_spectator`)

**목적:** 플레이어가 현재 관전자 모드인지 확인합니다.

**값:** 필요 없음

## 생존 모드 (`fancymenu_visibility_requirement_is_survival`)

**목적:** 플레이어가 현재 생존 모드인지 확인합니다.

**값:** 필요 없음

## 게임 모드 (`is_gamemode`)

**목적:** 플레이어가 특정 게임 모드인지 확인합니다.

**값:** 필요함 — 게임 모드 이름 (예: "creative", "survival", "adventure", "spectator")

## 난이도 (`is_difficulty`)

**목적:** 현재 게임 난이도가 특정 값과 일치하는지 확인합니다.

**값:** 필요함 — 난이도 이름 (예: "peaceful", "easy", "normal", "hard")

## 하드코어 (`is_hardcore`)

**목적:** 현재 로드된 월드가 하드코어 모드인지 확인합니다.

**값:** 필요 없음

## 카메라 시점 (`is_camera_perspective`)

**목적:** 현재 카메라 시점이 특정 시점과 일치하는지 확인합니다.

**값:** 필요함 — `first_person`, `third_person_back`, 또는 `third_person_front`

## 비가 옴 (`is_raining`)

**목적:** 현재 플레이어 위치에 비가 오는지 확인합니다.

**값:** 필요 없음

## 천둥이 침 (`is_thundering`)

**목적:** 현재 플레이어의 월드에 천둥번개가 치는지 확인합니다.

**값:** 필요 없음

## 맑은 날씨 (`is_clear_weather`)

**목적:** 현재 날씨가 맑은지(비나 천둥이 없는지) 확인합니다.

**값:** 필요 없음

## 눈이 옴 (`is_snowing`)

**목적:** 현재 플레이어 위치에 눈이 오는지 확인합니다.

**값:** 필요 없음

## 플레이어 달리기 중 (`is_player_running`)

**목적:** 플레이어가 현재 전력 질주 중인지 확인합니다.

**값:** 필요 없음

## 플레이어 웅크리기 중 (`is_player_sneaking`)

**목적:** 플레이어가 현재 웅크리기/앉기 상태인지 확인합니다.

**값:** 필요 없음

## 플레이어가 아이템 사용 중 (`is_player_using_item`)

**목적:** 플레이어가 현재 아이템을 사용 중인지 확인합니다.

**값:** 필요 없음

## 플레이어 수영 중 (`is_player_swimming`)

**목적:** 플레이어가 현재 수영 중인지 확인합니다.

**값:** 필요 없음

## 플레이어 점프 또는 낙하 중 (`is_player_jumping`)

**목적:** 플레이어가 일반적인 점프 또는 낙하 상태로 공중에 있을 때 true를 반환합니다. 수영, 유체, 엘리트라 비행, 수면, 시각적 수영, 기어가기 상태는 제외됩니다.

**값:** 필요 없음

## 플레이어가 물속에 완전히 잠김 (`is_player_under_water`)

**목적:** 플레이어가 물속에 완전히 잠겨 있는지 확인합니다.

**값:** 필요 없음

## 플레이어가 물속에 있음 (`is_player_in_water`)

**목적:** 플레이어가 물속에 있는지 확인합니다(일부만 잠겨 있어도 됨).

**값:** 필요 없음

## 플레이어가 용암 속에 있음 (`is_player_in_lava`)

**목적:** 플레이어가 용암 속에 있는지 확인합니다.

**값:** 필요 없음

## 플레이어가 유체 속에 있음 (`is_player_in_fluid`)

**목적:** 플레이어가 어떤 유체(물, 용암 등) 안에 있는지 확인합니다.

**값:** 필요 없음

## 플레이어가 엔티티/탈것을 탐 (`is_player_riding_entity`)

**목적:** 플레이어가 어떤 엔티티든 타고 있는지 확인합니다.

**값:** 필요 없음

## 플레이어가 점프 가능한 엔티티를 탐 (`is_player_riding_jumpable_entity`)

**목적:** 플레이어가 말처럼 점프할 수 있는 엔티티를 타고 있는지 확인합니다.

**값:** 필요 없음

## 플레이어가 체력이 있는 엔티티를 탐 (`is_player_riding_entity_with_health`)

**목적:** 플레이어가 보트가 아닌, 동물처럼 체력이 있는 생명체를 타고 있는지 확인합니다.

**값:** 필요 없음

## 플레이어가 가루눈 속에 있음 (`is_player_in_powder_snow`)

**목적:** 플레이어가 현재 가루눈 속에 있는지 확인합니다.

**값:** 필요 없음

## 플레이어가 가루눈에 있었음 (`was_player_in_powder_snow`)

**목적:** 플레이어가 가루눈에 있었는지 확인합니다(떠난 뒤에도 지속되는 효과에 사용).

**값:** 필요 없음

## 플레이어가 호박을 쓰고 있음 (`is_player_wearing_pumpkin`)

**목적:** 플레이어가 머리에 깎은 호박을 쓰고 있는지 확인합니다.

**값:** 필요 없음

## 플레이어가 엘리트라로 비행 중 (`is_player_flying_with_elytra`)

**목적:** 플레이어가 현재 엘리트라로 비행 중인지 확인합니다.

**값:** 필요 없음

## 플레이어 창작 비행 중 (`is_player_creative_flying`)

**목적:** 플레이어가 창작 모드에서 비행 중인지 확인합니다.

**값:** 필요 없음

## 플레이어가 흡수 하트를 가짐 (`has_player_absorption_hearts`)

**목적:** 플레이어가 흡수 하트(황금 하트)를 가지고 있는지 확인합니다.

**값:** 필요 없음

## 플레이어가 위더 효과를 받음 (`is_player_withered`)

**목적:** 플레이어가 위더 효과의 영향을 받고 있는지 확인합니다.

**값:** 필요 없음

## 플레이어가 완전히 얼어붙음 (`is_player_fully_frozen`)

**목적:** 플레이어가 완전히 얼어붙었는지 확인합니다(보통 가루눈에서 발생).

**값:** 필요 없음

## 플레이어가 중독됨 (`is_player_poisoned`)

**목적:** 플레이어가 독 효과의 영향을 받고 있는지 확인합니다.

**값:** 필요 없음

## 플레이어가 바이옴 안에 있음 (`is_player_in_biome`)

**목적:** 플레이어가 특정 바이옴에 있는지 확인합니다.

**값:** 필요함 — 바이옴 식별자 (예: `minecraft:birch_forest`)

## 플레이어가 차원에 있음 (`is_player_in_dimension`)

**목적:** 플레이어가 특정 차원에 있는지 확인합니다.

**값:** 필요함 — 차원 식별자 (예: `minecraft:overworld`, `minecraft:the_nether`, `minecraft:the_end`)

## 플레이어가 구조물 안에 있음 (`is_player_in_structure`)

**목적:** 플레이어가 현재 특정 구조물 내부에 있는지 확인합니다. 서버 월드에서는 서버에 FancyMenu가 필요합니다.

**값:** 필요함 — 구조물 식별자 (예: `minecraft:village`)

## 엔티티가 근처에 있음 (`is_entity_nearby`)

**목적:** 특정 엔티티 유형이 플레이어 주변의 일정 반경 내에 있는지 확인합니다.

**값:** 필요함 — 형식: "radius:entity_id" (예: `10:minecraft:pig` - 10블록 내의 돼지를 확인)

## 효과 활성화됨 (`is_effect_active`)

**목적:** 특정 물약 효과가 플레이어에게 활성화되어 있는지 확인합니다.

**값:** 필요함 — 효과 식별자 (예: `minecraft:speed`, `minecraft:strength`)

## 아무 효과나 활성화됨 (`is_any_effect_active`)

**목적:** 플레이어에게 어떤 물약 효과라도 활성화되어 있는지 확인합니다.

**값:** 필요 없음

## 플레이어가 왼손잡이임 (`is_left_handed`)

**목적:** 플레이어가 게임 옵션에서 왼손잡이로 설정되어 있는지 확인합니다.

**값:** 필요 없음

## 인벤토리 슬롯이 채워짐 (`is_inventory_slot_filled`)

**목적:** 특정 인벤토리 슬롯에 아이템이 들어 있는지 확인합니다.

**값:** 필요함 — 슬롯 번호 (일반 인벤토리는 0-35, 0-8은 핫바)

## 인벤토리에서 아이템이 호버됨 (`is_item_hovered_in_inventory`)

**목적:** 커서가 인벤토리 화면의 어떤 아이템 위에 올라가 있는지 확인합니다.

**값:** 필요 없음

## 커서가 인벤토리 아이템을 들고 있음 (`is_cursor_holding_inventory_item`)

**목적:** 커서가 현재 인벤토리 아이템 스택을 들고 있는지 확인합니다.

**값:** 필요 없음

## 핫바 슬롯이 선택됨 (`is_hotbar_slot_active`)

**목적:** 특정 핫바 슬롯이 현재 선택되어 있는지 확인합니다.

**값:** 필요함 — 핫바 슬롯 번호 (0-8)

## 플레이어 권한 레벨 보유 (`fancymenu_loading_requirement_has_player_permission_level`)

**목적:** 플레이어가 현재 월드 또는 서버에서 지정된 권한/OP 레벨 이상인지 확인합니다.

**값:** 필요함 — 권한 레벨 숫자 (0-4, 4는 서버 관리자)

## 공격 강도가 약화됨 (`is_attack_strength_weakened`)

**목적:** 플레이어의 공격 강도가 현재 약화되어 있는지(완전히 충전되지 않았는지) 확인합니다.

**값:** 필요 없음

## 실시간 날짜 (`fancymenu_visibility_requirement_is_realtime_day`)

**목적:** 현재 현실 세계의 날짜가 특정 값과 일치하는지 확인합니다.

**값:** 필요함 — 날짜 숫자 (1-31). 쉼표로 구분해 여러 값을 입력할 수 있습니다.

## 실시간 시간 (`fancymenu_visibility_requirement_is_realtime_hour`)

**목적:** 현재 현실 세계의 시간이 특정 값과 일치하는지 확인합니다.

**값:** 필요함 — 24시간 형식의 시간 (0-23). 쉼표로 구분해 여러 값을 입력할 수 있습니다.

## 실시간 분 (`fancymenu_visibility_requirement_is_realtime_minute`)

**목적:** 현재 현실 세계의 분이 특정 값과 일치하는지 확인합니다.

**값:** 필요함 — 분 (0-59). 쉼표로 구분해 여러 값을 입력할 수 있습니다.

## 실시간 월 (`fancymenu_visibility_requirement_is_realtime_month`)

**목적:** 현재 현실 세계의 월이 특정 값과 일치하는지 확인합니다.

**값:** 필요함 — 월 숫자 (1-12, 1은 1월). 쉼표로 구분해 여러 값을 입력할 수 있습니다.

## 실시간 초 (`fancymenu_visibility_requirement_is_realtime_second`)

**목적:** 현재 현실 세계의 초가 특정 값과 일치하는지 확인합니다.

**값:** 필요함 — 초 (0-59). 쉼표로 구분해 여러 값을 입력할 수 있습니다.

## 실시간 요일 (`fancymenu_visibility_requirement_is_realtime_week_day`)

**목적:** 현재 현실 세계의 요일이 특정 값과 일치하는지 확인합니다.

**값:** 필요함 — 숫자로 된 요일 (1-7, 1은 일요일). 쉼표로 구분해 여러 값을 입력할 수 있습니다.

## 실시간 연도 (`fancymenu_visibility_requirement_is_realtime_year`)

**목적:** 현재 현실 세계의 연도가 특정 값과 일치하는지 확인합니다.

**값:** 필요함 — 전체 연도 (예: "2023"). 쉼표로 구분해 여러 값을 입력할 수 있습니다.

## 파일/폴더 존재 (`fancymenu_loading_requirement_file_exists`)

**목적:** 파일 또는 디렉터리가 존재하는지 확인합니다.

**값:** 필요함 — 활성 게임 디렉터리를 기준으로 한 경로, 또는 일반적인 Minecraft 디렉터리를 위한 `.minecraft/`로 시작하는 경로. 파일과 디렉터리 모두 존재하는 것으로 간주됩니다.

## OS가 Linux임 (`fancymenu_loading_requirement_is_os_linux`)

**목적:** 현재 플랫폼이 Windows도 macOS도 아닌지 확인합니다. 일반적으로 Linux 환경에 해당합니다.

**값:** 필요 없음

## OS가 macOS임 (`fancymenu_loading_requirement_is_os_macos`)

**목적:** 운영체제가 macOS인지 확인합니다.

**값:** 필요 없음

## OS가 Windows임 (`fancymenu_loading_requirement_is_os_windows`)

**목적:** 운영체제가 Windows인지 확인합니다.

**값:** 필요 없음

## 인터넷 연결 가능 (`is_internet_connection_available`)

**목적:** 활성 인터넷 연결이 가능한지 확인합니다.

**값:** 필요 없음

## 게임 언어 (`fancymenu_loading_requirement_is_language`)

**목적:** 현재 게임 언어가 특정 값과 일치하는지 확인합니다.

**값:** 필요함 — 언어 코드 (예: 영어의 경우 `en_us`)

## 모드 로드됨 (`fancymenu_loading_requirement_is_mod_loaded`)

**목적:** 특정 모드가 로드되어 있는지 확인합니다.

**값:** 필요함 — 모드 ID (예: `fancymenu`, `jei`). `optifine`으로 OptiFine도 확인할 수 있습니다. 쉼표로 구분된 여러 모드 ID를 지원하며, 나열된 모든 모드가 로드되어 있어야 합니다.

## Rinku 로드됨 (`is_rinku_loaded`)

**목적:** [Rinku](https://modrinth.com/mod/rinku)가 설치되어 초기화되었는지 확인합니다. [Rinku](https://modrinth.com/mod/rinku)는 [Browser 요소](./elements#browser)와 [더 이상 사용되지 않는 Rinku 기반 비디오 유형](./video#requirements)에 필요하며, [기본 Video 기능](./video)은 Watermedia를 사용합니다.

**값:** 필요 없음

## 숫자 (`fancymenu_visibility_requirement_is_number`)

**목적:** 다양한 비교 모드를 사용한 고급 숫자 비교를 제공합니다.

**값:** 필요함 — 복합 형식: `["mode":"comparison_mode","number":"value1","compare_with":"value2"]$` 여기서 `comparison_mode`는 `equals`, `bigger-than`, `smaller-than`, `bigger-than-or-equals`, `smaller-than-or-equals` 중 하나일 수 있습니다.

## 텍스트 (`fancymenu_visibility_requirement_is_text`)

**목적:** 다양한 비교 모드를 사용한 고급 텍스트 비교를 제공합니다.

**값:** 필요함 — 복합 형식: `["mode":"comparison_mode","text":"text1","compare_with":"text2"]$` 여기서 `comparison_mode`는 `equals`, `contains`, `starts-with`, `ends-with` 중 하나일 수 있습니다.

## 서버 IP (`fancymenu_visibility_requirement_is_server_ip`)

**목적:** 현재 서버 IP가 특정 값과 일치하는지 확인합니다.

**값:** 필요함 — 서버 IP 주소(포트 포함 또는 미포함)

## 서버 온라인 (`fancymenu_loading_requirement_is_server_online`)

**목적:** 특정 서버가 온라인 상태이며 연결 가능한지 확인합니다.

**값:** 필요함 — 서버 IP 주소(포트 포함 또는 미포함)

## 리소스 팩 활성화됨 (`is_resource_pack_enabled`)

**목적:** 특정 리소스 팩이 현재 선택/활성화되어 있는지 확인합니다.

**값:** 필요함 — 리소스 팩 제목 또는 팩 ID (예: `Programmer Art` 또는 해당 팩의 ID)

## 변수 값이 일치함 (FM Variable) (`fancymenu_visibility_requirement_is_variable_value`)

**목적:** FancyMenu 변수가 특정 값을 가지고 있는지 확인합니다.

**값:** 필요함 — 형식: "variable_name:expected_value"

## 세션당 한 번만 (`once_per_session`)

**목적:** 구성된 각 인스턴스는 게임 세션당 한 번만 true를 반환합니다. 서로 다른 인스턴스는 독립적으로 추적됩니다.

**값:** 필요 없음
