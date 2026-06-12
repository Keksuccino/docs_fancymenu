---
title: 플레이스홀더
description: 플레이스홀더를 사용하는 방법입니다.
---
# 플레이스홀더

플레이스홀더는 사용될 때 실제 콘텐츠로 대체되는 동적 값입니다. FancyMenu에서 플레이스홀더를 사용하면 텍스트, 버튼, 로딩 조건 같은 다양한 요소에 동적 콘텐츠를 삽입할 수 있습니다. 레이아웃이 표시될 때 평가되어 실제 값으로 바뀌는 변수처럼 생각하면 됩니다.

# 일반 정보

## 기본 구문
FancyMenu의 플레이스홀더는 JSON과 비슷한 구문을 사용합니다:
```
{"placeholder":"modversion","values":{"modid":"fancymenu"}}
```

예를 들어 플레이어 이름을 표시하려면:
```
{"placeholder":"playername"}
```

## 플레이스홀더 중첩
FancyMenu 플레이스홀더 시스템의 가장 강력한 기능 중 하나는 다른 플레이스홀더 안에 플레이스홀더를 중첩할 수 있다는 점입니다. 즉, 하나의 플레이스홀더 출력값을 다른 플레이스홀더의 입력값으로 사용할 수 있습니다.

중첩 플레이스홀더 예시:
```
{"placeholder":"calc","values":{"decimal":"true","expression":"{"placeholder":"maxram"} / 1024"}}
```
이 예시는 최대 RAM 값을 가져와 1024로 나누어 MB를 GB로 변환합니다.

> [!IMPORTANT]
> 실제 JSON과 달리, 중첩된 플레이스홀더는 `\\`를 사용해 **이스케이프되지 않습니다**. 플레이스홀더를 이스케이프하면(당연히) 작동이 멈추기 때문에 매우 중요합니다. 플레이스홀더는 JSON과 비슷한 구문만 사용할 뿐, 실제 JSON은 아닙니다.

# 플레이스홀더 사용하기

텍스트 입력을 지원하는 대부분의 요소는 플레이스홀더를 지원합니다. 편집할 때 해당 텍스트 입력이 플레이스홀더를 지원하는지 확인할 수 있습니다. 텍스트를 편집할 때 전체 화면 **텍스트 편집기**가 열리면 플레이스홀더를 지원하는 것입니다. 

**모든 플레이스홀더 목록**을 보려면 **텍스트 편집기**의 **오른쪽 상단**에 있는 **플레이스홀더** 버튼을 클릭하세요.

플레이스홀더 목록 상단에는 플레이스홀더를 검색할 수 있는 **검색창**이 있습니다.

플레이스홀더 목록에서 항목을 클릭하면 해당 플레이스홀더가 텍스트 내용에 붙여넣어집니다.

# 플레이스홀더 상세

이 목록에는 FancyMenu에서 사용할 수 있는 대부분, 혹은 전부의 플레이스홀더가 포함되어 있습니다. 모드 업데이트로 인해 목록이 다소 오래되었을 수 있습니다.

## 플레이어 이름 (playername)
현재 플레이어의 사용자 이름을 반환합니다.
```
{"placeholder":"playername"}
```
출력 예시: `Steve`

## 플레이어 UUID (playeruuid)
플레이어의 고유 식별자를 반환합니다.
```
{"placeholder":"playeruuid"}
```
출력 예시: `c8cde7fe-7ced-11eb-9439-0242ac130002`

## 마인크래프트 버전 (mcversion)
현재 Minecraft 버전을 반환합니다.
```
{"placeholder":"mcversion"}
```
출력 예시: `1.19.2`

## 모드 로더 버전 (loaderver)
모드 로더(Forge/Fabric)의 버전을 반환합니다.
```
{"placeholder":"loaderver"}
```
출력 예시: `43.2.0`

## 모드 로더 이름 (loadername)
모드 로더의 이름을 반환합니다.
```
{"placeholder":"loadername"}
```
출력 예시: `Forge`

## 모드 버전 (modversion)
특정 모드의 버전을 반환합니다.
```
{"placeholder":"modversion","values":{"modid":"fancymenu"}}
```
출력 예시: `2.14.9`

## 전체 모드 개수 (totalmods)
설치된 전체 모드 수를 반환합니다.
```
{"placeholder":"totalmods"}
```
출력 예시: `45`

## 활성 모드 개수 (loadedmods)
현재 로드된 모드 수를 반환합니다.
```
{"placeholder":"loadedmods"}
```
출력 예시: `43`

## 월드 로딩 진행률 (world_load_progress)
현재 월드 로딩 진행률을 백분율로 반환합니다.
```
{"placeholder":"world_load_progress"}
```
출력 예시: `75`

## 마인크래프트 옵션 값 (minecraft_option_value)
Minecraft 옵션의 값을 반환합니다.
```
{"placeholder":"minecraft_option_value","values":{"name":"fov"}}
```
출력 예시: `70`

## 마지막 월드 또는 서버 (last_world_server)
마지막으로 접근한 월드 또는 서버에 대한 정보를 반환합니다.
```
{"placeholder":"last_world_server","values":{"type":"both","full_world_path":"true"}}
```
매개변수:
- `type`: 반환할 정보의 유형을 지정합니다
  - `"both"`: 마지막으로 접근한 월드 또는 서버를 반환합니다(기본값)
  - `"server"`: 마지막으로 접근한 대상이 서버였을 때만 반환합니다
  - `"world"`: 마지막으로 접근한 대상이 월드였을 때만 반환합니다
- `full_world_path`: 월드 경로 표시 방식을 제어합니다
  - `"true"`: 전체 월드 경로를 반환합니다(기본값)
  - `"false"`: 경로 없이 월드 이름만 반환합니다(서버에는 영향 없음)

예시:
- 서버: `mc.hypixel.net`
- 전체 경로가 포함된 월드: `saves/New World`
- 전체 경로가 없는 월드: `New World`

## 화면 너비 (guiwidth)
현재 화면 너비를 반환합니다.
```
{"placeholder":"guiwidth"}
```
출력 예시: `1920`

## 화면 높이 (guiheight)
현재 화면 높이를 반환합니다.
```
{"placeholder":"guiheight"}
```
출력 예시: `1080`

## 현재 화면 식별자 (screenid)
현재 화면의 식별자를 반환합니다.
```
{"placeholder":"screenid"}
```
출력 예시: `title_screen`

## 요소 너비 (elementwidth)
특정 요소의 너비를 반환합니다.
```
{"placeholder":"elementwidth","values":{"id":"my_button"}}
```
출력 예시: `200`

## 요소 높이 (elementheight)
특정 요소의 높이를 반환합니다.
```
{"placeholder":"elementheight","values":{"id":"my_button"}}
```
출력 예시: `20`

## 요소 X 위치 (elementposx)
특정 요소의 X 좌표를 반환합니다.
```
{"placeholder":"elementposx","values":{"id":"my_button"}}
```
출력 예시: `150`

## 요소 Y 위치 (elementposy)
특정 요소의 Y 좌표를 반환합니다.
```
{"placeholder":"elementposy","values":{"id":"my_button"}}
```
출력 예시: `100`

## 마우스 X 위치 (mouseposx)
현재 마우스의 X 위치를 반환합니다.
```
{"placeholder":"mouseposx"}
```
출력 예시: `960`

## 마우스 Y 위치 (mouseposy)
현재 마우스의 Y 위치를 반환합니다.
```
{"placeholder":"mouseposy"}
```
출력 예시: `540`

## 초당 클릭 수 (clicks_per_second)
마우스 버튼의 현재 초당 클릭 수를 반환합니다.
```
{"placeholder":"clicks_per_second","values":{"mouse_button":"left"}}
```
매개변수:
- `mouse_button`: `left` 또는 `right`

출력 예시: `8`

## GUI 스케일 (guiscale)
현재 GUI 스케일을 반환합니다.
```
{"placeholder":"guiscale"}
```
출력 예시: `2`

## 바닐라 위젯 라벨/텍스트 (vanillabuttonlabel)
바닐라 위젯/버튼의 라벨/텍스트를 반환합니다.
```
{"placeholder":"vanillabuttonlabel","values":{"locator":"some.menu.identifier:505280"}}
```
출력 예시: `Options...`

## 텍스트 입력 필드 값 (text_input_field_value)
요소 식별자를 통해 커스텀 또는 바닐라 텍스트 입력 필드의 현재 값을 반환합니다.
```
{"placeholder":"text_input_field_value","values":{"element_identifier":"my_input"}}
```
출력 예시: `Hello World`

## 현재 플레이어 체력 (current_player_health)
플레이어의 현재 체력을 반환합니다.
```
{"placeholder":"current_player_health"}
```
출력 예시: `20.0`

## 최대 플레이어 체력 (max_player_health)
플레이어의 최대 체력을 반환합니다.
```
{"placeholder":"max_player_health"}
```
출력 예시: `20.0`

## 현재 플레이어 체력(퍼센트) (current_player_health_percent)
플레이어의 체력을 백분율로 반환합니다.
```
{"placeholder":"current_player_health_percent"}
```
출력 예시: `100`

## 현재 플레이어 흡수 체력 (current_player_absorption_health)
플레이어의 흡수 체력(황금 하트)을 반환합니다.
```
{"placeholder":"current_player_absorption_health"}
```
출력 예시: `4.0`

## 최대 플레이어 흡수 체력 (max_player_absorption_health)
최대 흡수 체력을 반환합니다.
```
{"placeholder":"max_player_absorption_health"}
```
출력 예시: `4.0`

## 현재 플레이어 흡수 체력(퍼센트) (current_player_absorption_health_percent)
플레이어의 흡수 체력을 백분율로 반환합니다.
```
{"placeholder":"current_player_absorption_health_percent"}
```
출력 예시: `100`

## 현재 플레이어 허기 수치 (current_player_hunger)
플레이어의 현재 허기 수치를 반환합니다.
```
{"placeholder":"current_player_hunger"}
```
출력 예시: `20`

## 최대 플레이어 허기 수치 (max_player_hunger)
최대 허기 수치를 반환합니다.
```
{"placeholder":"max_player_hunger"}
```
출력 예시: `20`

## 현재 플레이어 허기 수치(퍼센트) (current_player_hunger_percent)
플레이어의 허기를 백분율로 반환합니다.
```
{"placeholder":"current_player_hunger_percent"}
```
출력 예시: `100`

## 현재 플레이어 포만도 (current_player_hunger_saturation)
플레이어의 현재 포만도 값을 반환합니다.
```
{"placeholder":"current_player_hunger_saturation"}
```
출력 예시: `5.0`

## 현재 플레이어 방어력 (current_player_armor)
플레이어의 현재 방어력 값을 반환합니다.
```
{"placeholder":"current_player_armor"}
```
출력 예시: `20`

## 플레이어 방어구 강인함 (player_armor_toughness)
플레이어의 총 방어구 강인함 값을 반환합니다.
```
{"placeholder":"player_armor_toughness"}
```
출력 예시: `8.0`

## 최대 플레이어 방어력 (max_player_armor)
최대 방어력 값을 반환합니다.
```
{"placeholder":"max_player_armor"}
```
출력 예시: `20`

## 현재 플레이어 방어력(퍼센트) (current_player_armor_percent)
플레이어의 방어력을 백분율로 반환합니다.
```
{"placeholder":"current_player_armor_percent"}
```
출력 예시: `100`

## 현재 플레이어 산소량 (current_player_oxygen)
플레이어의 현재 산소량(공기 방울)을 반환합니다.
```
{"placeholder":"current_player_oxygen"}
```
출력 예시: `300`

## 최대 플레이어 산소량 (max_player_oxygen)
최대 산소량을 반환합니다.
```
{"placeholder":"max_player_oxygen"}
```
출력 예시: `300`

## 현재 플레이어 산소량(퍼센트) (current_player_oxygen_percent)
플레이어의 산소량을 백분율로 반환합니다.
```
{"placeholder":"current_player_oxygen_percent"}
```
출력 예시: `100`

## 현재 플레이어 레벨 (current_player_level)
플레이어의 현재 경험치 레벨을 반환합니다.
```
{"placeholder":"current_player_level"}
```
출력 예시: `30`

## 현재 플레이어 경험치 (current_player_exp)
플레이어의 총 경험치를 반환합니다.
```
{"placeholder":"current_player_exp"}
```
출력 예시: `1250`

## 플레이어 경험치 진행률(퍼센트) (current_player_exp_progress)
다음 레벨까지의 플레이어 경험치 진행률을 백분율로 반환합니다.
```
{"placeholder":"current_player_exp_progress"}
```
출력 예시: `75`

## 플레이어 공격 강도(퍼센트) (player_attack_strength)
플레이어의 공격 쿨다운을 백분율로 반환합니다.
```
{"placeholder":"player_attack_strength"}
```
출력 예시: `100`

## 플레이어 게임 모드 (player_gamemode)
플레이어의 현재 게임 모드를 반환합니다.
```
{"placeholder":"player_gamemode"}
```
출력 예시: `survival`

## 플레이어 시선 방향 (player_view_direction)
플레이어가 바라보고 있는 방향을 반환합니다.
```
{"placeholder":"player_view_direction"}
```
출력 예시: `north`

## 플레이어 X 좌표 (player_x_coordinate)
월드에서 플레이어의 X 위치를 반환합니다.
```
{"placeholder":"player_x_coordinate"}
```
출력 예시: `125`

## 플레이어 Y 좌표 (player_y_coordinate)
월드에서 플레이어의 Y 위치를 반환합니다.
```
{"placeholder":"player_y_coordinate"}
```
출력 예시: `64`

## 플레이어 Z 좌표 (player_z_coordinate)
월드에서 플레이어의 Z 위치를 반환합니다.
```
{"placeholder":"player_z_coordinate"}
```
출력 예시: `-250`

## 현재 탑승체 체력 (current_mount_health)
플레이어가 타고 있는 엔티티의 현재 체력을 반환합니다.
```
{"placeholder":"current_mount_health"}
```
출력 예시: `30.0`

## 최대 탑승체 체력 (max_mount_health)
플레이어가 타고 있는 엔티티의 최대 체력을 반환합니다.
```
{"placeholder":"max_mount_health"}
```
출력 예시: `30.0`

## 현재 탑승체 체력(퍼센트) (current_mount_health_percent)
탑승체의 체력을 백분율로 반환합니다.
```
{"placeholder":"current_mount_health_percent"}
```
출력 예시: `100`

## 현재 탑승체 점프 게이지 (퍼센트) (current_mount_jump_meter)
탑승체의 점프 파워 게이지 값을 반환합니다.
```
{"placeholder":"current_mount_jump_meter"}
```
출력 예시: `75`

## 현재 보스 체력 (퍼센트) (current_boss_health)
활성 보스의 체력을 반환합니다.
```
{"placeholder":"current_boss_health"}
```
출력 예시: `150.0`

## 보스 이름 (boss_name)
활성 보스의 이름을 반환합니다.
```
{"placeholder":"boss_name","values":{"boss_index":"0","as_json":"false"}}
```
출력 예시: `Ender Dragon`

## 보스 개수 (boss_count)
활성 보스의 수를 반환합니다.
```
{"placeholder":"boss_count"}
```
출력 예시: `1`

## 활성 효과 개수 (effects_count)
활성 포션 효과의 수를 반환합니다.
```
{"placeholder":"effects_count"}
```
출력 예시: `3`

## 활성 효과 (active_effect)
특정 활성 효과에 대한 정보를 반환합니다.
```
{"placeholder":"active_effect","values":{"effect_index":"0"}}
```
출력 예시: `minecraft:speed`

## 선택된 핫바 슬롯 (active_hotbar_slot)
현재 선택된 핫바 슬롯(0-8)을 반환합니다.
```
{"placeholder":"active_hotbar_slot"}
```
출력 예시: `4`

## 슬롯 아이템 (slot_item)
특정 인벤토리 슬롯의 아이템 정보를 반환합니다.
```
{"placeholder":"slot_item","values":{"slot":"0"}}
```
출력 예시: `minecraft:diamond_sword`

## 슬롯 아이템 개수 (slot_item_count)
특정 플레이어 인벤토리 슬롯의 아이템 스택 수를 반환합니다.
```
{"placeholder":"slot_item_count","values":{"slot":"0"}}
```
출력 예시: `64`

## 슬롯 아이템 내구도 (slot_item_durability)
특정 플레이어 인벤토리 슬롯의 아이템 내구도 정보를 반환합니다.
```
{"placeholder":"slot_item_durability","values":{"slot":"0","format":"percentage"}}
```
매개변수:
- `slot`: 플레이어 인벤토리 슬롯 번호입니다.
- `format`: `current`, `remaining`, `max`, `damage`, `percentage`, 또는 `percent`.

출력 예시: `87`

## 슬롯 아이템 표시 이름 (slot_item_display_name_fm)
특정 슬롯의 아이템 표시 이름을 JSON 텍스트 컴포넌트로 반환합니다. 관전자 모드에서는 `ignore_spectator`가 `true`가 아닌 경우 핫바 슬롯이 관전자 메뉴 아이템 이름으로 해석될 수 있습니다.
```
{"placeholder":"slot_item_display_name_fm","values":{"slot":"0","ignore_spectator":"false"}}
```
출력 예시: `{"text":"Diamond Sword","color":"aqua"}`

## 인벤토리 아이템 개수 (inventory_item_count)
플레이어 인벤토리 내 특정 아이템 유형의 총 개수를 반환합니다. `item`이 비어 있으면 인벤토리의 모든 아이템 스택 수를 셉니다.
```
{"placeholder":"inventory_item_count","values":{"item":"minecraft:diamond"}}
```
출력 예시: `12`

## 인벤토리 슬롯 음식 회복량 (inventory_slot_food_point_restore_amount)
지정한 플레이어 인벤토리 슬롯의 음식 아이템이 회복하는 허기 수치를 반환합니다.
```
{"placeholder":"inventory_slot_food_point_restore_amount","values":{"slot":"0"}}
```
출력 예시: `4.0`

## 마우스오버된 인벤토리 아이템 (hovered_inventory_item)
인벤토리 화면에서 현재 마우스오버 중인 아이템의 아이템 키를 반환합니다.
```
{"placeholder":"hovered_inventory_item"}
```
출력 예시: `minecraft:apple`

## 월드 게임 시간 (game_time)
현재 게임 내 시간 틱 카운터를 반환합니다.
```
{"placeholder":"game_time"}
```
출력 예시: `18000`

## 월드 낮 시간 (world_daytime)
현재 월드 낮 시간을 반환합니다.
```
{"placeholder":"world_daytime"}
```
출력 예시: `13000`

## 월드 낮 시간 시 (world_daytime_hour)
월드 시간의 시(hour) 부분을 반환합니다. 기본적으로 24시간 형식을 사용하며, 12시간 형식을 원하면 `twelve_hour_format`을 `"true"`로 설정하세요.
```
{"placeholder":"world_daytime_hour","values":{"twelve_hour_format":"false"}}
```
출력 예시: `12`

## 월드 낮 시간 분 (world_daytime_minute)
월드 시간의 분(minute) 부분(00-59)을 반환합니다.
```
{"placeholder":"world_daytime_minute"}
```
출력 예시: `30`

## 월드 난이도 (world_difficulty)
현재 월드 난이도를 반환합니다.
```
{"placeholder":"world_difficulty"}
```
출력 예시: `normal`

## 현재 월드 시드 (current_world_seed)
현재 싱글플레이 월드의 시드를 반환합니다. 시드를 사용할 수 없으면 빈 값을 반환합니다.
```
{"placeholder":"current_world_seed"}
```
출력 예시: `123456789`

## 현재 바이옴 (current_biome)
플레이어가 현재 있는 바이옴을 반환합니다. `as_key`를 `"false"`로 설정하면 가능한 경우 번역/표시 이름을 반환합니다.
```
{"placeholder":"current_biome","values":{"as_key":"true"}}
```
출력 예시: `minecraft:plains`

## 현재 차원 (current_dimension)
플레이어가 현재 있는 차원을 반환합니다. `as_key`를 `"false"`로 설정하면 가능한 경우 번역/표시 이름을 반환합니다.
```
{"placeholder":"current_dimension","values":{"as_key":"true"}}
```
출력 예시: `minecraft:overworld`

## 게임 규칙 값 (gamerule_value)
로드된 월드/서버에서 게임 규칙의 현재 값을 반환합니다. 서버 월드는 서버에 FancyMenu가 필요합니다.
```
{"placeholder":"gamerule_value","values":{"name":"doDaylightCycle"}}
```
출력 예시: `true`

## 아이템 카테고리 (item_category)
아이템의 크리에이티브 탭 카테고리를 반환합니다. 표시 이름 대신 카테고리 키를 반환하려면 `as_key`를 `"true"`로 설정하세요.
```
{"placeholder":"item_category","values":{"item":"minecraft:diamond_sword","as_key":"false"}}
```
출력 예시: `Combat`

## 현재 HUD 제목/부제목 (current_title)
현재 표시 중인 제목 텍스트를 반환합니다.
```
{"placeholder":"current_title","values":{"is_subtitle":"false","as_json":"false"}}
```
출력 예시: `Game Over!`

## 액션바 메시지 (action_bar_message_fm)
핫바 위에 표시되는 현재 바닐라 액션바 메시지를 반환합니다.
```
{"placeholder":"action_bar_message_fm"}
```
출력 예시: `You may not rest now`

## 액션바 메시지 시간 (action_bar_message_time_fm)
현재 바닐라 액션바 메시지가 앞으로 몇 틱 동안 더 표시될지 반환합니다.
```
{"placeholder":"action_bar_message_time_fm"}
```
출력 예시: `42`

## 카메라 회전 X (camera_rotation_x_fm)
현재 카메라 피치(pitch)를 도 단위로 반환합니다.
```
{"placeholder":"camera_rotation_x_fm"}
```
출력 예시: `12.5`

## 카메라 회전 Y (camera_rotation_y_fm)
현재 카메라 요(yaw)를 도 단위로 반환합니다.
```
{"placeholder":"camera_rotation_y_fm"}
```
출력 예시: `-90.0`

## 카메라 회전 변화량 X (camera_rotation_delta_x_fm)
틱당 카메라 피치의 변화를 반환합니다.
```
{"placeholder":"camera_rotation_delta_x_fm"}
```
출력 예시: `0.4`

## 카메라 회전 변화량 Y (camera_rotation_delta_y_fm)
틱당 카메라 요의 변화를 반환합니다.
```
{"placeholder":"camera_rotation_delta_y_fm"}
```
출력 예시: `-1.2`

## 강조된 아이템 표시 시간 (highlighted_item_time_fm)
핫바 위에 강조된 아이템 이름이 앞으로 몇 틱 더 표시될지 반환합니다.
```
{"placeholder":"highlighted_item_time_fm"}
```
출력 예시: `30`

## 플레이어 아이템 사용 진행률 (player_item_use_progress_fm)
현재 아이템 사용 진행률을 `0.0`에서 `1.0` 사이 값으로 반환합니다.
```
{"placeholder":"player_item_use_progress_fm"}
```
출력 예시: `0.65`

## 플레이어 위치 변화량 X (player_position_delta_x_fm)
틱당 플레이어 위치의 X축 변화량을 반환합니다.
```
{"placeholder":"player_position_delta_x_fm"}
```
출력 예시: `0.0`

## 플레이어 위치 변화량 Y (player_position_delta_y_fm)
틱당 플레이어 위치의 Y축 변화량을 반환합니다.
```
{"placeholder":"player_position_delta_y_fm"}
```
출력 예시: `-0.08`

## 플레이어 위치 변화량 Z (player_position_delta_z_fm)
틱당 플레이어 위치의 Z축 변화량을 반환합니다.
```
{"placeholder":"player_position_delta_z_fm"}
```
출력 예시: `0.12`

## 현재 서버 IP (current_server_ip)
연결된 서버의 IP를 반환합니다.
```
{"placeholder":"current_server_ip"}
```
출력 예시: `mc.hypixel.net`

## 월드 플레이어 목록 (world_players_list)
현재 월드에 있는 모든 플레이어의 목록을 반환합니다.
```
{"placeholder":"world_players_list","values":{"separator":", "}}
```
출력 예시: `Steve, Alex, Notch`

## 서버 MOTD (servermotd)
서버의 오늘의 메시지(Message of the Day)를 반환합니다.
```
{"placeholder":"servermotd","values":{"ip":"mc.hypixel.net","line":"1"}}
```
출력 예시: `Welcome to Hypixel!`

## 서버 핑 (serverping)
서버까지의 핑을 밀리초 단위로 반환합니다.
```
{"placeholder":"serverping","values":{"ip":"mc.hypixel.net"}}
```
출력 예시: `54`

## 서버 플레이어 수 (serverplayercount)
서버의 플레이어 수를 반환합니다.
```
{"placeholder":"serverplayercount","values":{"ip":"mc.hypixel.net"}}
```
출력 예시: `25000/30000`

## 서버 상태 (serverstatus)
서버의 온라인/오프라인 상태를 반환합니다.
```
{"placeholder":"serverstatus","values":{"ip":"mc.hypixel.net"}}
```
출력 예시: `§aOnline` 또는 `§cOffline`

## 서버 버전 (serverversion)
서버의 Minecraft 버전을 반환합니다.
```
{"placeholder":"serverversion","values":{"ip":"mc.hypixel.net"}}
```
출력 예시: `1.19.2`

## 연도 (realtimeyear)
현재 연도를 반환합니다.
```
{"placeholder":"realtimeyear"}
```
출력 예시: `2024`

## 월 (realtimemonth)
현재 월을 반환합니다(01-12).
```
{"placeholder":"realtimemonth"}
```
출력 예시: `01`

## 일 (realtimeday)
현재 날짜를 반환합니다(01-31).
```
{"placeholder":"realtimeday"}
```
출력 예시: `27`

## 시 (realtimehour)
현재 시간을 반환합니다. 기본적으로 24시간 형식을 사용하며, 12시간 형식을 원하면 `twelve_hour_format`을 `"true"`로 설정하세요.
```
{"placeholder":"realtimehour","values":{"twelve_hour_format":"false","timezone":"system"}}
```
출력 예시: `14`

## 분 (realtimeminute)
현재 분을 반환합니다(00-59).
```
{"placeholder":"realtimeminute"}
```
출력 예시: `30`

## 초 (realtimesecond)
현재 초를 반환합니다(00-59).
```
{"placeholder":"realtimesecond"}
```
출력 예시: `45`

## 현재 시간 밀리초(유닉스 타임스탬프) (unix_time)
현재 유닉스 타임스탬프를 밀리초 단위로 반환합니다.
```
{"placeholder":"unix_time"}
```
출력 예시: `1716552478123`

> 실시간 플레이스홀더(`realtimeyear`, `realtimemonth`, `realtimeday`, `realtimehour`, `realtimeminute`, `realtimesecond`, `unix_time`)는 `timezone` 값을 지원합니다. `UTC`, `Europe/Berlin`, `America/New_York` 같은 일반적인 Java 시간대 ID를 사용하세요. 시스템 시간대를 사용하려면 생략하거나 `system`을 사용하세요.
{.is-info}

## CPU 정보 (cpuinfo)
CPU에 대한 정보를 반환합니다.
```
{"placeholder":"cpuinfo"}
```
출력 예시: `Intel(R) Core(TM) i7-10700K CPU @ 3.80GHz`

## CPU 사용률 (JVM) (jvmcpu)
JVM의 CPU 사용률을 백분율로 반환합니다.
```
{"placeholder":"jvmcpu"}
```
출력 예시: `25.5`

## CPU 사용률 (OS) (oscpu)
OS의 CPU 사용률을 백분율로 반환합니다.
```
{"placeholder":"oscpu"}
```
출력 예시: `42.8`

## GPU 정보 (gpuinfo)
GPU에 대한 정보를 반환합니다.
```
{"placeholder":"gpuinfo"}
```
출력 예시: `NVIDIA GeForce RTX 3080`

## Java 버전 (javaver)
Java 버전을 반환합니다.
```
{"placeholder":"javaver"}
```
출력 예시: `17.0.2`

## Java 가상 머신 (jvmname)
Java 가상 머신의 이름을 반환합니다.
```
{"placeholder":"jvmname"}
```
출력 예시: `OpenJDK 64-Bit Server VM`

## OpenGL 버전 (glver)
OpenGL 버전을 반환합니다.
```
{"placeholder":"glver"}
```
출력 예시: `4.6.0 NVIDIA 516.94`

## 운영 체제 이름 (osname)
운영 체제 이름을 반환합니다.
```
{"placeholder":"osname"}
```
출력 예시: `Windows 10`

## FPS(초당 프레임 수) (fps)
현재 초당 프레임 수를 반환합니다.
```
{"placeholder":"fps"}
```
출력 예시: `120`

## 사용 중인 RAM(MB) (usedram)
현재 사용 중인 RAM 양(MB)을 반환합니다.
```
{"placeholder":"usedram"}
```
출력 예시: `4096`

## 최대 RAM(MB) (maxram)
현재 할당된 최대 RAM(MB)을 반환합니다.
```
{"placeholder":"maxram"}
```
출력 예시: `8192`

## 사용 중인 RAM(%%) (percentram)
현재 사용 중인 RAM의 비율을 반환합니다.
```
{"placeholder":"percentram"}
```
출력 예시: `50`

## 오디오 요소 볼륨 (audio_element_vol)
오디오 요소의 볼륨을 반환합니다.
```
{"placeholder":"audio_element_vol","values":{"element_identifier":"background_music"}}
```
출력 예시: `0.5`

## 현재 오디오 트랙 (audio_element_current_track)
오디오 요소의 트랙 이름을 반환합니다.
```
{"placeholder":"audio_element_current_track","values":{"element_identifier":"background_music","display_name_mappings":"track1.ogg=>Cool Track Name"}}
```
출력 예시: `Cool Track Name`

## 오디오 길이 (audio_duration)
오디오 트랙의 전체 길이를 MM:SS 형식으로 반환합니다.
```
{"placeholder":"audio_duration","values":{"element_identifier":"background_music"}}
```
출력 예시: `03:45`

## 오디오 재생 시간 (audio_playtime)
오디오 트랙의 현재 재생 시간을 반환합니다. `show_percentage`를 `"true"`로 설정하면 `MM:SS` 대신 0-100 진행률 값을 반환합니다.
```
{"placeholder":"audio_playtime","values":{"element_identifier":"background_music","show_percentage":"false"}}
```
출력 예시: `01:30` (또는 `show_percentage`가 `"true"`일 때 `45`)

## 오디오 재생 상태 (audio_playing_state)
오디오 요소가 재생 중인지(true/false) 반환합니다.
```
{"placeholder":"audio_playing_state","values":{"element_identifier":"background_music"}}
```
출력 예시: `true`

## 비디오 요소 볼륨 (video_element_vol)
비디오 요소의 볼륨 수준(0.0~1.0)을 반환합니다.
```
{"placeholder":"video_element_vol","values":{"element_identifier":"my_video_element"}}
```
출력 예시: `0.5`

## 비디오 요소 길이 (video_element_duration)
비디오 요소의 전체 길이를 `MM:SS` 형식으로 반환합니다. 밀리초 타임스탬프로 반환하려면 `output_as_timestamp`를 `"true"`로 설정하세요.
```
{"placeholder":"video_element_duration","values":{"element_identifier":"my_video_element","output_as_timestamp":"false"}}
```
출력 예시: `02:00` (또는 `output_as_timestamp`가 `"true"`일 때 `120000`)

## 비디오 요소 재생 시간 (video_element_playtime)
비디오 요소의 현재 재생 시간(진행률)을 `MM:SS` 형식으로 반환합니다. 0-100 진행률 값을 원하면 `show_percentage`를 `"true"`로, 밀리초 값을 원하면 `output_as_timestamp`를 `"true"`로 설정하세요.
```
{"placeholder":"video_element_playtime","values":{"element_identifier":"my_video_element","show_percentage":"false","output_as_timestamp":"false"}}
```
출력 예시: `00:45` (또는 백분율로 `38`, 타임스탬프로 `45200`)

## 비디오 요소 일시정지 상태 (video_element_paused_state)
비디오 요소가 일시정지 상태인지(true/false) 반환합니다.
```
{"placeholder":"video_element_paused_state","values":{"element_identifier":"my_video_element"}}
```
출력 예시: `false`

## 비디오 배경 볼륨 (video_background_vol)
비디오 메뉴 배경의 볼륨 수준(0.0~1.0)을 반환합니다.
```
{"placeholder":"video_background_vol","values":{"background_identifier":"main_menu_video"}}
```
출력 예시: `0.7`

## 비디오 배경 길이 (video_background_duration)
비디오 메뉴 배경의 전체 길이를 `MM:SS` 형식으로 반환합니다. 밀리초 타임스탬프로 반환하려면 `output_as_timestamp`를 `"true"`로 설정하세요.
```
{"placeholder":"video_background_duration","values":{"background_identifier":"main_menu_video","output_as_timestamp":"false"}}
```
출력 예시: `03:00` (또는 `output_as_timestamp`가 `"true"`일 때 `180000`)

## 비디오 배경 재생 시간 (video_background_playtime)
비디오 메뉴 배경의 현재 재생 시간(진행률)을 `MM:SS` 형식으로 반환합니다. 0-100 진행률 값을 원하면 `show_percentage`를 `"true"`로, 밀리초 값을 원하면 `output_as_timestamp`를 `"true"`로 설정하세요.
```
{"placeholder":"video_background_playtime","values":{"background_identifier":"main_menu_video","show_percentage":"false","output_as_timestamp":"false"}}
```
출력 예시: `01:00` (또는 백분율로 `33`, 타임스탬프로 `60500`)

## 비디오 배경 일시정지 상태 (video_background_paused_state)
비디오 메뉴 배경이 일시정지 상태인지(true/false) 반환합니다.
```
{"placeholder":"video_background_paused_state","values":{"background_identifier":"main_menu_video"}}
```
출력 예시: `true`

## 계산기 (calc)
계산기 플레이스홀더는 레이아웃 내에서 수학 계산을 수행할 수 있게 해주는 강력한 도구입니다. 다양한 수학 연산을 지원하며 소수와 정수 모두 다룰 수 있습니다.

### 기본 구문
```
{"placeholder":"calc","values":{"decimal":"true/false","expression":"your_expression"}}
```

계산기에는 두 가지 주요 매개변수가 있습니다:
- `decimal`: 결과에 소수점이 포함될지(`true`) 아니면 정수로 반올림될지(`false`)를 결정합니다
- `expression`: 평가할 수학식입니다

### 지원되는 연산
계산기는 다음 수학 연산을 지원합니다:
- 기본 사칙연산: `+`(덧셈), `-`(뺄셈), `*`(곱셈), `/`(나눗셈)
- 괄호: 연산 그룹화를 위한 `( )`
- 거듭제곱: 지수를 위한 `^`
- 제곱근: `sqrt()`
- 삼각 함수: `sin()`, `cos()`, `tan()`
- 수학 상수: `pi`, `e`
- 절댓값: `abs()`
- 로그: `log()`, `ln()`

## 난수 (random_number)
지정한 범위 내에서 난수를 생성합니다.
```
{"placeholder":"random_number","values":{"min":"1","max":"100"}}
```
출력 예시: `42`

## 최대값 (maxnum)
두 수 중 더 큰 값을 반환합니다.
```
{"placeholder":"maxnum","values":{"first":"10","second":"20"}}
```
출력 예시: `20`

## 최소값 (minnum)
두 수 중 더 작은 값을 반환합니다.
```
{"placeholder":"minnum","values":{"first":"10","second":"20"}}
```
출력 예시: `10`

## 절댓값 (absnum)
숫자의 절댓값을 반환합니다.
```
{"placeholder":"absnum","values":{"num":"-10.5"}}
```
출력 예시: `10.5`

## 음수화 (negnum)
숫자의 부호를 반전한 값을 반환합니다.
```
{"placeholder":"negnum","values":{"num":"10.5"}}
```
출력 예시: `-10.5`

## *pi* (수학) (math_pi)
π 값을 반환합니다.
```
{"placeholder":"math_pi"}
```
출력 예시: `3.141592653589793`

## 삼각함수 사인 (수학) (math_sin)
각도의 사인 값을 반환합니다.
```
{"placeholder":"math_sin","values":{"angle":"45"}}
```
출력 예시: `0.7071067811865476`

## 삼각함수 코사인 (수학) (math_cos)
각도의 코사인 값을 반환합니다.
```
{"placeholder":"math_cos","values":{"angle":"45"}}
```
출력 예시: `0.7071067811865476`

## 삼각함수 탄젠트 (수학) (math_tan)
각도의 탄젠트 값을 반환합니다.
```
{"placeholder":"math_tan","values":{"angle":"45"}}
```
출력 예시: `1.0`

## 내림 (수학) (math_floor)
숫자를 가장 가까운 아래 정수로 내립니다.
```
{"placeholder":"math_floor","values":{"num":"3.14"}}
```
출력 예시: `3`

## 올림 (수학) (math_ceil)
숫자를 가장 가까운 위 정수로 올립니다.
```
{"placeholder":"math_ceil","values":{"num":"3.14"}}
```
출력 예시: `4`

## 반올림 (수학) (math_round)
숫자를 반올림합니다. 기본적으로 가장 가까운 정수로 반올림하며, `decimals`를 0 이상의 숫자로 설정하면 그 자리수까지 반올림합니다.
```
{"placeholder":"math_round","values":{"num":"3.14159","decimals":"2"}}
```
출력 예시: `3.14` (`decimals:-1`이거나 생략 시 → `3`)

## 부호 (수학) (math_sign)
숫자의 부호를 반환합니다(양수는 1, 음수는 -1, 0은 0).
```
{"placeholder":"math_sign","values":{"num":"-3.14"}}
```
출력 예시: `-1`

## 쌍곡선 사인 (수학) (math_sinh)
각도의 쌍곡선 사인 값을 반환합니다.
```
{"placeholder":"math_sinh","values":{"angle":"1"}}
```
출력 예시: `1.1752011936438014`

## 쌍곡선 코사인 (수학) (math_cosh)
각도의 쌍곡선 코사인 값을 반환합니다.
```
{"placeholder":"math_cosh","values":{"angle":"1"}}
```
출력 예시: `1.5430806348152437`

## 쌍곡선 탄젠트 (수학) (math_tanh)
각도의 쌍곡선 탄젠트 값을 반환합니다.
```
{"placeholder":"math_tanh","values":{"angle":"1"}}
```
출력 예시: `0.7615941559557649`

## 텍스트 분할 (split_text)
지정한 구분자로 텍스트를 분할합니다.
```
{"placeholder":"split_text","values":{"input":"hello,world","regex":",","max_parts":"2","split_index":"1"}}
```
출력 예시: `world`

## 텍스트 공백 제거 (trim_text)
앞뒤 공백을 제거합니다.
```
{"placeholder":"trim_text","values":{"text":"  hello world  "}}
```
출력 예시: `hello world`

## 텍스트 자르기 (crop_text)
텍스트의 시작과 끝에서 문자를 제거합니다.
```
{"placeholder":"crop_text","values":{"text":"hello world","remove_from_start":"1","remove_from_end":"1"}}
```
출력 예시: `ello worl`

## 문자열화 (stringify)
모든 구문 문자를 이스케이프하여 텍스트를 문자열화합니다.
```
{"placeholder":"stringify","values":{"text":"text with {special} \"characters\""}}
```
출력 예시: `text with \{special\} \"characters\"`

## 텍스트 현지화 (local)
키에 해당하는 현지화된 텍스트를 가져옵니다.
```
{"placeholder":"local","values":{"key":"menu.singleplayer"}}
```
출력 예시: `Singleplayer`

## 웹 텍스트 (webtext)
웹 URL에서 텍스트 내용을 가져옵니다.
```
{"placeholder":"webtext","values":{"link":"http://somewebsite.com/textfile.txt"}}
```
출력 예시: URL의 텍스트 내용

## 랜덤 텍스트 (randomtext)
텍스트 파일, URL 또는 직접 입력한 일반 텍스트에서 무작위 줄 하나를 반환합니다. 텍스트는 지정된 간격마다 바뀝니다.
```
{"placeholder":"randomtext","values":{"source":"/config/fancymenu/assets/<file_name.txt>","interval":"10"}}
```
매개변수:
- `source`: 텍스트 줄의 원본(기존 `path` 매개변수를 대체함)
  - 파일 경로: `/config/fancymenu/assets/quotes.txt`
  - URL: `https://example.com/quotes.txt`
  - 일반 텍스트: `Line 1\nLine 2\nLine 3`
- `interval`: 텍스트가 바뀌는 간격(초)

이 플레이스홀더는 이제 세 가지 원본 유형을 지원합니다:
1. **로컬 파일**: 게임 디렉터리의 텍스트 파일
   ```
   {"placeholder":"randomtext","values":{"source":"/config/fancymenu/assets/quotes.txt","interval":"10"}}
   ```
2. **URL**: 인터넷의 원격 텍스트 파일
   ```
   {"placeholder":"randomtext","values":{"source":"https://example.com/quotes.txt","interval":"10"}}
   ```
3. **일반 텍스트**: `\n`으로 줄을 구분한 직접 텍스트 입력
   ```
   {"placeholder":"randomtext","values":{"source":"First line\nSecond line\nThird line","interval":"5"}}
   ```

참고: `source` 대신 `path`를 사용한 기존 플레이스홀더도 계속 작동합니다.

## JSON 파서 (json)
파일, URL 또는 직접 입력한 JSON 콘텐츠에서 JSON 데이터를 파싱하고 JSON 경로 표현식을 사용해 값을 추출합니다.
```
{"placeholder":"json","values":{"source":"path_or_link_or_json_content","json_path":"$.some.json.path"}}
```
매개변수:
- `source`: JSON 데이터의 원본
  - 파일 경로: `/config/fancymenu/assets/data.json`
  - URL: `https://api.example.com/data.json`
  - 직접 JSON: `{"name":"Steve","level":42}`
- `json_path`: 데이터를 추출할 JSON 경로 표현식

이 플레이스홀더는 이제 세 가지 원본 유형을 지원합니다:
1. **로컬 파일**: 게임 디렉터리의 JSON 파일
   ```
   {"placeholder":"json","values":{"source":"/config/fancymenu/assets/playerdata.json","json_path":"$.player.name"}}
   ```
2. **URL**: API 또는 웹 서비스의 원격 JSON 데이터
   ```
   {"placeholder":"json","values":{"source":"https://api.minecraft.com/server/status","json_path":"$.online"}}
   ```
3. **직접 JSON**: 인라인 JSON 콘텐츠
   ```
   {"placeholder":"json","values":{"source":"{"name":"Steve","score":42,"rank":"Diamond"}","json_path":"$.rank"}}
   ```

예시 JSON 경로:
- `$.name` - 루트에서 "name" 필드를 가져옵니다
- `$.player.level` - "player" 안의 중첩된 "level" 필드를 가져옵니다
- `$.items[0].id` - 배열의 첫 번째 항목의 "id"를 가져옵니다
- `$.scores.*` - "scores" 객체의 모든 값을 가져옵니다

## 절대 파일/폴더 경로 (absolute_path)
파일의 절대 경로를 반환합니다.
```
{"placeholder":"absolute_path","values":{"short_path":"relative/path/to/file.txt"}}
```
출력 예시: `C:/Users/Username/AppData/Roaming/.minecraft/relative/path/to/file.txt`

## 텍스트 문자 수 (text_character_count)
주어진 텍스트의 문자 수를 반환합니다.
```
{"placeholder":"text_character_count","values":{"text":"Hello World!"}}
```
출력 예시: `12`

## 텍스트 너비 (text_width)
렌더링했을 때 주어진 텍스트의 너비를 픽셀 단위로 반환합니다.
```
{"placeholder":"text_width","values":{"text":"Hello World!"}}
```
출력 예시: `66`

## 대문자 텍스트 (uppercase_text)
입력 텍스트를 모두 대문자로 변환합니다.
```
{"placeholder":"uppercase_text","values":{"text":"Hello World"}}
```
출력 예시: `HELLO WORLD`

## 소문자 텍스트 (lowercase_text)
입력 텍스트를 모두 소문자로 변환합니다.
```
{"placeholder":"lowercase_text","values":{"text":"Hello World"}}
```
출력 예시: `hello world`

## 제목형 텍스트 (title_case_text)
입력 텍스트를 제목형으로 변환합니다.
```
{"placeholder":"title_case_text","values":{"text":"hello world"}}
```
출력 예시: `Hello World`

## 문장형 텍스트 (sentence_case_text)
입력 텍스트를 문장형으로 변환합니다.
```
{"placeholder":"sentence_case_text","values":{"text":"hello world. this is fancymenu!"}}
```
출력 예시: `Hello world. This is fancymenu!`

## 스네이크 케이스 텍스트 (snake_case_text)
입력 텍스트를 `snake_case`로 변환합니다.
```
{"placeholder":"snake_case_text","values":{"text":"Hello World"}}
```
출력 예시: `hello_world`

## 케밥 케이스 텍스트 (kebab_case_text)
입력 텍스트를 `kebab-case`로 변환합니다.
```
{"placeholder":"kebab_case_text","values":{"text":"Hello World"}}
```
출력 예시: `hello-world`

## 교대 대소문자 텍스트 (alternating_case_text)
입력 텍스트를 교대 대소문자로 변환합니다.
```
{"placeholder":"alternating_case_text","values":{"text":"alternating case"}}
```
출력 예시: `aLtErNaTiNg CaSe`

## 대소문자 뒤집기 텍스트 (toggle_case_text)
입력 텍스트의 모든 글자 대소문자를 뒤집습니다.
```
{"placeholder":"toggle_case_text","values":{"text":"Toggle Case"}}
```
출력 예시: `tOGGLE cASE`

## Base64로 인코딩 (base64_encode)
주어진 텍스트를 Base64로 인코딩합니다.
```
{"placeholder":"base64_encode","values":{"text":"Hello World"}}
```
출력 예시: `SGVsbG8gV29ybGQ=`

## Base64에서 디코딩 (base64_decode)
Base64 문자열을 일반 텍스트로 디코딩합니다.
```
{"placeholder":"base64_decode","values":{"text":"SGVsbG8gV29ybGQ="}}
```
출력 예시: `Hello World`

## 파일 텍스트 (file_text)
파일 또는 URL에서 텍스트 줄을 반환합니다. 모든 줄 또는 마지막 X줄만 반환할 수 있습니다.
```
{"placeholder":"file_text","values":{"path_or_url":"/config/fancymenu/assets/some_file.txt","mode":"all","separator":"\n","last_lines":"1"}}
```
매개변수:
- `path_or_url`: 읽어올 파일 경로나 URL
- `mode`: `"all"`(모든 줄 반환) 또는 `"last"`(마지막 X줄만 반환)
- `separator`: 줄을 합칠 때 사용할 텍스트(기본값: `"\n"`)
- `last_lines`: `mode`가 `"last"`일 때 반환할 줄 수(기본값: `"1"`)

출력 예시: 파일 내용에 따라 다름

## 클립보드 내용 (clipboard_content)
시스템 클립보드에 저장된 현재 텍스트 내용을 반환합니다.
```
{"placeholder":"clipboard_content"}
```
출력 예시: 현재 클립보드에 있는 텍스트

## 텍스트 바꾸기 (replace_text)
리터럴 텍스트 또는 정규식을 사용해 문자열의 텍스트를 바꿉니다.
```
{"placeholder":"replace_text","values":{"text":"Hello World! This is a test.","search":"World","replacement":"FancyMenu","use_regex":"false","replace_all":"true"}}
```
매개변수:
- `text`: 처리할 입력 텍스트
- `search`: 검색할 텍스트 또는 정규식 패턴
- `replacement`: 대체 텍스트
- `use_regex`: 정규식 사용 여부(`"true"`) 또는 리터럴 일치 여부(`"false"`)
- `replace_all`: 모든 항목을 바꿀지(`"true"`) 아니면 첫 번째 것만 바꿀지(`"false"`)

출력 예시: `Hello FancyMenu! This is a test.`

## 조건 분기 (switch_case)
값을 기준으로 switch-case 동작을 수행합니다.
```
{"placeholder":"switch_case","values":{"value":"1","cases":"1:first case,2:second case,3:third case","default":"default case"}}
```
출력 예시: `first case` (값이 1인 경우)

## 변수 값 가져오기 (FM 변수) (getvariable)
이전에 저장된 변수의 값을 가져옵니다.
```
{"placeholder":"getvariable","values":{"name":"some_variable"}}
```
출력 예시: 저장된 값에 따라 다름

## NBT 데이터 가져오기 (nbt_data_get)
클라이언트에서 NBT 데이터를 가져옵니다(`/data get` 명령과 유사함). 서버에 연결되어 있고 서버 측의 정확한 값이 필요하면 서버 변형인 `nbt_data_get_server`를 사용하세요.
```
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"foodLevel","scale":"1.0","return_type":"value"}}
```
매개변수:
- `source_type`: `"entity"` 또는 `"block"`
- `entity_selector`: 엔티티용 셀렉터(`@s`, `@p`, `@e`) 또는 UUID/이름
- `block_pos`: 블록용 위치 형식 `"x y z"`
- `nbt_path`: 가져올 NBT 경로
- `scale`: 숫자 값에 적용할 선택적 배율(기본값: `"1.0"`)
- `return_type`: 데이터를 반환하는 방식:
  - `"value"`: 기본값, 값 자체를 반환합니다(숫자에는 선택적 배율 적용)
  - `"string"`: 실제 NBT 데이터를 문자열로 반환합니다
  - `"snbt"`: SNBT(형식화된 NBT)로 반환합니다
  - `"json"`: JSON 형식의 컴포넌트로 반환합니다(복합 태그용)

출력 예시: `20`(허기 수치의 경우)

## NBT 데이터 가져오기(서버 측) (nbt_data_get_server)
패킷을 사용해 서버 측 NBT 데이터를 조회하고 결과를 잠시 캐시합니다. 반환값은 클라이언트 측 플레이스홀더와 동일합니다.
```
{"placeholder":"nbt_data_get_server","values":{"source_type":"entity","entity_selector":"@s","block_pos":"","storage_id":"minecraft:storage_key","nbt_path":"SelectedItem.id","scale":"1.0","return_type":"value"}}
```
출력 예시: `minecraft:diamond_sword`

## 마지막 사망 메시지 (lastdeathmessage)
클라이언트 플레이어의 마지막으로 기록된 사망 메시지를 반환합니다. 원시 JSON 텍스트 컴포넌트를 받으려면 `as_json_component`를 `"true"`로 설정하세요.
```
{"placeholder":"lastdeathmessage","values":{"as_json_component":"false"}}
```
출력 예시: `Steve was slain by Zombie`

## 실행 시간 (uptime_duration)
FancyMenu가 로드된 후 경과 시간을 반환합니다. 기본값은 초 단위이며, 밀리초를 받으려면 `output_as_millis`를 `"true"`로 설정하세요.
```
{"placeholder":"uptime_duration","values":{"output_as_millis":"false"}}
```
출력 예시: `742`(로드 이후 초)

## 월드 저장 이름 (level_save_names)
선택한 구분자로 연결된 모든 로컬 월드 저장 이름을 나열합니다. 클라이언트 스레드에서 실행됩니다.
```
{"placeholder":"level_save_names","values":{"separator":", "}}
```
출력 예시: `Creative Test, Survival World, Hardcore`

## 월드 저장 데이터 (level_save_data)
지정한 월드 이름의 직렬화된 레벨 데이터를 반환합니다(저장 목록에 표시되는 이름과 정확히 일치해야 함).
```
{"placeholder":"level_save_data","values":{"level_name":"Survival World"}}
```
출력 예시: `{"name":"Survival World","gameMode":"survival",...}`

## 진법 변환기 (number_base_convert)
숫자(정수 또는 소수)를 한 진법에서 다른 진법으로 변환합니다(2~36). 진법이 지정되지 않으면 10진법을 기본으로 사용합니다.
```
{"placeholder":"number_base_convert","values":{"input":"67.5","from_base":"10","to_base":"16"}}
```
출력 예시: `43.8`

## 파일 크기 (file_size)
로컬 파일의 크기를 바이트 단위로 반환합니다. 로컬 경로만 허용됩니다.
```
{"placeholder":"file_size","values":{"path":"/config/fancymenu/assets/notes.txt"}}
```
출력 예시: `1284`

## 파일 MD5 (file_md5)
로컬 파일의 MD5 해시를 소문자 16진 문자열로 반환합니다.
```
{"placeholder":"file_md5","values":{"path":"/config/fancymenu/assets/notes.txt"}}
```
출력 예시: `d41d8cd98f00b204e9800998ecf8427e`

# 실용 예시

## 동적 메모리 표시 만들기
```
사용 중인 RAM: {"placeholder":"usedram"}MB / {"placeholder":"maxram"}MB ({"placeholder":"percentram"}%)
```

## 실시간 시계 만들기
```
{"placeholder":"realtimehour"}:{"placeholder":"realtimeminute"}:{"placeholder":"realtimesecond"}
```

## 시스템 정보 표시 만들기
```
OS: {"placeholder":"osname"}
CPU: {"placeholder":"cpuinfo"}
GPU: {"placeholder":"gpuinfo"}
Java: {"placeholder":"javaver"}
```

## 플레이어 상태 HUD
```
체력: {"placeholder":"current_player_health"} / {"placeholder":"max_player_health"} ({"placeholder":"current_player_health_percent"}%)
방어력: {"placeholder":"current_player_armor"} / {"placeholder":"max_player_armor"}
XP 레벨: {"placeholder":"current_player_level"}
```

## 중첩 플레이스홀더를 사용한 복잡한 계산
```
{"placeholder":"calc","values":{"decimal":"true","expression":"({"placeholder":"usedram"} / {"placeholder":"maxram"}) * 100"}}
```

## 반올림이 포함된 좌표 표시
```
X: {"placeholder":"math_round","values":{"num":"{"placeholder":"player_x_coordinate"}"}}
Y: {"placeholder":"math_round","values":{"num":"{"placeholder":"player_y_coordinate"}"}}
Z: {"placeholder":"math_round","values":{"num":"{"placeholder":"player_z_coordinate"}"}}
```

# 모범 사례

1. **비용이 큰 작업은 캐시하기**: 일부 플레이스홀더(예: 시스템 정보를 읽는 것)는 리소스를 많이 사용할 수 있습니다. 여러 번 사용해야 한다면 변수에 저장하는 것을 고려하세요.

2. **적절한 소수점 설정 사용**: 계산을 다룰 때는 `decimal` 매개변수를 적절히 사용하세요. 정수가 필요하면 `false`로, 정확한 소수 값이 필요하면 `true`로 설정하세요.

3. **값이 없을 때 처리하기**: 플레이스홀더가 값을 반환하지 않을 경우 어떻게 할지 항상 고려하세요. 이런 경우 기본값을 제공하고 싶을 수 있습니다.

4. **성능 테스트하기**: 많은 플레이스홀더나 복잡한 중첩 구조를 사용할 때는, 특히 저사양 시스템에서 성능 영향을 테스트하세요.

5. **고급 크기 조정/배치 사용**: 동적 UI 요소의 경우 플레이스홀더를 고급 크기 조정 및 배치와 결합해 반응형 레이아웃을 만드세요.

6. **변수와 함께 사용하기**: 변수와 플레이스홀더를 함께 사용하면 액션을 통해 갱신할 수 있는 더 동적인 콘텐츠를 만들 수 있습니다.

# 일반적인 문제와 해결 방법

## 플레이스홀더가 업데이트되지 않음
플레이스홀더 값이 예상대로 업데이트되지 않으면 다음을 확인하세요:
- 플레이스홀더 형식이 올바른지
- 플레이스홀더 ID의 대소문자가 올바른지
- 플레이스홀더가 업데이트되기 위한 특정 조건이 필요한지

## 중첩 플레이스홀더가 작동하지 않음
플레이스홀더를 중첩할 때는:
- 따옴표 이스케이프가 올바른지 확인하세요
- 각 중첩 플레이스홀더가 개별적으로도 유효한지 확인하세요

## 성능 문제
성능 문제가 보인다면:
- 사용 중인 플레이스홀더 수를 줄이세요
- 불필요한 중첩을 피하세요
- 자주 접근하는 값은 변수를 사용하는 것을 고려하세요
- 필요에 맞는 적절한 플레이스홀더를 사용하세요(예: 정적 값으로 충분한데 실시간 플레이스홀더를 사용하지 않기)
