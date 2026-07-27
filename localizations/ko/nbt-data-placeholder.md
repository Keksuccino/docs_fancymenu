---
title: NBT 데이터 플레이스홀더
description: '엔티티, 블록, 저장소 NBT 데이터를 읽습니다.'
---

# NBT 데이터 플레이스홀더

FancyMenu는 두 가지 NBT 플레이스홀더를 제공합니다:

| 플레이스홀더 | 실행 위치 | 사용 가능한 데이터 |
|---|---|---|
| `nbt_data_get` | 클라이언트 | 클라이언트에서 보이는 엔티티 및 블록 엔티티 |
| `nbt_data_get_server` | 서버 | 바닐라 `/data get` 대상; 서버에 FancyMenu가 필요함 |

# 클라이언트 측 플레이스홀더

```text
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Health"}}
```

## 값

| 값 | 필요 여부 | 설명 |
|---|---|---|
| `source_type` | 예 | `entity` 또는 `block` |
| `entity_selector` | 엔티티용 | 클라이언트 측 셀렉터, UUID, 또는 정확한 엔티티 이름 |
| `block_pos` | 블록용 | 예: `100 64 -200` 같은 세 개의 절대 정수 좌표 |
| `nbt_path` | 예 | `Health`, `Pos[0]`, `Inventory[0].id` 같은 NBT 경로 |
| `scale` | 아니요 | 숫자 `value` 결과에 곱해짐; 기본값 `1.0` |
| `return_type` | 아니요 | `value`, `string`, `snbt`, 또는 `json`; 기본값 `value` |

클라이언트 측 블록 위치는 `~` 또는 `^` 좌표를 지원하지 않습니다.

## 클라이언트 엔티티 셀렉터

| 셀렉터 | 초기 대상 | 기본 순서 |
|---|---|---|
| `@s` | 로컬 플레이어 | 자기 자신 |
| `@p` | 플레이어 | 가장 가까운 대상 |
| `@a` | 플레이어 | 클라이언트 반복 순서 |
| `@r` | 플레이어 | 무작위 |
| `@e` | 모든 클라이언트에서 보이는 엔티티 | 클라이언트 반복 순서 |

`@e`는 `sort=nearest`를 추가하지 않으면 가장 가까운 엔티티를 선택하지 않습니다. 직접 UUID와 정확한 엔티티 이름 조회도 지원됩니다.

지원되는 셀렉터 옵션:

| 옵션 | 설명 |
|---|---|
| `type` | 엔티티 ID; 제외하려면 `!`를 접두사로 사용 |
| `name` | 정확한 표시 이름; 제외하려면 `!`를 접두사로 사용 |
| `tag` | 엔티티 태그; 제외하려면 `!`를 접두사로 사용 |
| `limit` | 양수 결과 제한 |
| `sort` | `nearest`, `furthest`, `random`, 또는 `arbitrary` |
| `distance` | `..10` 또는 `5..20` 같은 바닐라 거리 범위 |
| `x`, `y`, `z` | 검색 기준점; 절대값과 `~` 오프셋을 지원 |
| `dx`, `dy`, `dz` | 기준점에서의 검색 박스 크기 |

로컬 `^` 좌표와 다른 바닐라 셀렉터 옵션은 클라이언트 플레이스홀더에서 지원되지 않습니다.

예시:

```text
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@e[type=minecraft:zombie,sort=nearest,limit=1,distance=..20]","nbt_path":"Health"}}
```

## 반환 유형

| 유형 | 결과 |
|---|---|
| `value` | 숫자 태그는 숫자 형식으로 표시되고 `scale`이 적용됩니다. 문자열 태그는 해당 텍스트를 반환하며, 다른 태그는 SNBT와 유사한 텍스트를 반환합니다 |
| `string` | 태그의 문자열 값을 반환하며, 문자열 값이 없으면 빈 문자열을 반환합니다 |
| `snbt` | 태그의 SNBT 표현을 반환합니다 |
| `json` | 복합 태그에만 해당: 예쁘게 정렬된 NBT 출력을 포함한 직렬화된 Minecraft 텍스트 컴포넌트를 반환합니다 |

클라이언트 측 `json` 모드는 NBT를 JSON으로 직접 변환하는 것이 아닙니다.

## 예시

플레이어 배고픔:

```text
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"foodLevel"}}
```

첫 번째 핫바 아이템 ID:

```text
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Inventory[{Slot:0b}].id","return_type":"string"}}
```

블록 엔티티 아이템 수:

```text
{"placeholder":"nbt_data_get","values":{"source_type":"block","block_pos":"100 64 -200","nbt_path":"Items[0].count"}}
```

# 서버 측 플레이스홀더

`nbt_data_get_server`는 서버의 `/data get` 동작을 따르며 다음을 지원합니다:

- 완전한 서버 측 엔티티 셀렉터.
- 절대 좌표, 상대 좌표(`~`), 또는 로컬 좌표(`^`)를 사용하는 블록 대상.
- `source_type:"storage"`를 통한 명령 저장소.

```text
{"placeholder":"nbt_data_get_server","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Health","return_type":"value"}}
```

이 플레이스홀더는 서버 응답이 도착할 때까지 빈 값을 반환합니다. 과도한 요청을 피하기 위해 응답은 잠시 캐시됩니다.

# NBT 경로 찾기

사용 가능한 데이터를 확인하려면 NBT 경로 없이 대응하는 명령을 사용하세요:

```text
/data get entity @s
/data get block 100 64 -200
```

클라이언트 측 결과는 클라이언트에 동기화된 데이터로 제한됩니다. 잘못된 대상이나 경로는 빈 문자열을 반환하며, 세부 정보는 `logs/latest.log`에 기록됩니다.
