---
title: NBT 데이터 플레이스홀더
description: NBT 데이터 플레이스홀더를 사용하는 방법입니다.
---


# NBT 데이터 가져오기

이 플레이스홀더는 FancyMenu v3.8.0+에서 사용할 수 있습니다.

**Client NBT Data Get** 및 **Server NBT Data Get** 플레이스홀더를 사용하면 Minecraft의 엔티티와 블록에서 `/data get` 명령과 비슷하게 NBT(Named Binary Tag) 데이터를 가져올 수 있습니다. 이는 게임 상태, 플레이어 통계, 월드 조건에 반응하는 동적인 레이아웃을 만드는 데 매우 유용합니다.

> 이 플레이스홀더는 모드가 추가한 엔티티와 플레이어의 사용자 지정 NBT 데이터에 접근할 수 있어, 모드 플레이에서 특히 강력합니다. 마나 시스템을 추가하는 마법 모드, 사용자 지정 스탯이 있는 RPG 모드, 에너지 값이 있는 기술 모드 등 어떤 모드를 사용하든 이러한 모드 값을 UI 레이아웃에 표시할 수 있습니다.
{.is-info}

## 개요

이 플레이스홀더는 NBT 경로를 사용해 NBT 데이터 구조에서 특정 값을 추출합니다. 플레이어 체력, 허기, 인벤토리 아이템, 블록 상태, 마나나 에너지 같은 모드 추가 속성 등 다양한 정보를 가져올 수 있습니다.

클라이언트 측 버전의 가장 큰 장점은 순수하게 클라이언트 측에서 동작하므로 서버에 FancyMenu가 없어도 된다는 점입니다. 하지만 이 때문에 NBT 데이터와 관련된 모든 정보가 항상 모든 클라이언트에 보이는 것은 아니어서 기능이 훨씬 제한됩니다.

서버 측 버전은 서버에 FancyMenu가 설치되어 있어야 하지만, 기본적으로 **NBT로 저장되는 모든 것**에 대해 **완전한 지원**을 제공합니다.

이 페이지에서는 클라이언트 측 버전(`nbt_data_get`)에 중점을 두지만, 서버 측 버전(`nbt_data_get_server`)도 매우 비슷하게 작동합니다.

## 플레이스홀더 문법

```
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Health"}}
```

## 필수 값

| 값 | 설명 | 옵션 |
|-------|-------------|---------|
| `source_type` | 데이터 소스의 유형 | `entity` 또는 `block` |
| `nbt_path` | 조회할 NBT 경로 | 예: `Health`, `foodLevel`, `Pos[0]`, `Inventory[0].id` |

## 조건부 값

`source_type`에 따라 다음 중 하나가 필요합니다.

| 값 | 필요 조건 | 설명 | 형식 |
|-------|--------------|-------------|--------|
| `entity_selector` | source_type이 `entity`일 때 | 어떤 엔티티를 조회할지 선택 | `@s`(자기 자신), `@p`(가장 가까운 플레이어), `@e`(가장 가까운 엔티티), UUID, 또는 엔티티 이름 |
| `block_pos` | source_type이 `block`일 때 | 블록의 좌표 | `x y z` (예: `100 64 -200`) |

## 선택 사항

| 값 | 설명 | 기본값 | 옵션 |
|-------|-------------|---------|---------|
| `scale` | 숫자 값의 배율 | `1.0` | 모든 소수 숫자 |
| `return_type` | 반환된 데이터를 형식화하는 방법 | `value` | `value`(숫자/크기), `string`(텍스트), `snbt`(형식화된 NBT), `json`(JSON 형식) |

## 반환 유형 설명

- **`value`** - 숫자 값 또는 크기를 반환합니다(기본값)
  - 숫자: 숫자 값을 반환합니다(필요 시 스케일 적용)
  - 문자열: 문자열 길이를 반환합니다
  - 목록/배열: 항목 수를 반환합니다
  - 컴파운드: 태그 수를 반환합니다

- **`string`** - NBT 데이터의 실제 문자열 값을 반환합니다

- **`snbt`** - SNBT(Stringified NBT) 형식으로 데이터를 반환합니다

- **`json`** - JSON 형식으로 데이터를 반환합니다(컴파운드 태그에만 해당)

## 예시

### 플레이어 체력 가져오기
```json
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Health"}}
```

### 플레이어 허기 수준 가져오기
```json
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"foodLevel"}}
```

### 플레이어 X 좌표 가져오기
```json
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Pos[0]"}}
```

### 첫 번째 핫바 슬롯의 아이템 가져오기
```json
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Inventory[{Slot:0b}].id","return_type":"string"}}
```

### 특정 위치의 블록 데이터 가져오기
```json
{"placeholder":"nbt_data_get","values":{"source_type":"block","block_pos":"100 64 -200","nbt_path":"Items[0].Count"}}
```

### 스케일된 체력 퍼센트 가져오기 (체력 * 5)
```json
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Health","scale":"5"}}
```

## 사용 가능한 NBT 경로 찾기

### 방법 1: `/data get` 명령 사용하기(권장)

사용 가능한 NBT 경로를 찾는 가장 쉬운 방법은 게임 안에서 경로를 지정하지 않고 `/data get` 명령을 사용하는 것입니다.

1. **엔티티의 경우:** `/data get entity @p`
2. **블록의 경우:** `/data get block <x> <y> <z>`

그러면 해당 대상의 모든 사용 가능한 NBT 데이터가 표시되어, 사용할 수 있는 정확한 경로를 확인할 수 있습니다.

#### 출력 이해하기

`/data get entity @p`를 실행하면 다음과 비슷한 출력이 나타납니다:

```
Player616 has the following entity data: {Brain: {memories: {}}, 
HurtByTimestamp: 0, SleepTimer: 0s, Invulnerable: 0b, FallFlying: 
0b, PortalCooldown: 0, AbsorptionAmount: 0.0f, abilities: 
{invulnerable: 1b, mayfly: 1b, instabuild: 1b, walkSpeed: 0.1f, 
mayBuild: 1b, flying: 1b, flySpeed: 0.05f}, FallDistance: 0.0f, 
recipeBook: {recipes: ["minecraft:crafting_table"]}, 
DeathTime: 0s, XpSeed: -380875747, XpTotal: 0, UUID: [I; 1379890089, -1732753738, 
-2135065633, -718799804], playerGameType: 1, seenCredits: 
0b, Motion: [0.0d, 0.0d, 0.0d], Health: 20.0f, foodSaturationLevel: 
5.0f, ...}
```

이 출력에서 유효한 경로를 추출하려면:

1. **단순 값** - 키 이름을 그대로 사용합니다:
   - `Health: 20.0f` → 경로: `Health`
   - 예시: `{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Health"}}`

2. **중첩 값** - 점 표기법을 사용해 중첩 데이터에 접근합니다:
   - `abilities: {walkSpeed: 0.1f}` → 경로: `abilities.walkSpeed`
   - 예시: `{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"abilities.walkSpeed"}}`

3. **배열 값** - 인덱스 번호를 대괄호로 사용합니다:
   - `Motion: [0.0d, 0.0d, 0.0d]` → Y 모션 경로: `Motion[1]`
   - 예시: `{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Motion[1]"}}`

### 방법 2: NBT Autocomplete 모드

NBT 경로를 더 쉽게 찾으려면 **NBT Autocomplete** 모드 설치를 고려해 보세요:
- Fabric 및 Forge용 제공(Minecraft 1.21.x)
- 명령어를 입력할 때 게임 내 자동완성 제안을 제공
- 사용 가능한 태그 이름과 유형을 표시
- [Modrinth](https://modrinth.com/mod/nbt-autocomplete) | [CurseForge](https://www.curseforge.com/minecraft/mc-mods/nbt-autocomplete)

## 일반적인 NBT 경로

### 플레이어 엔티티
- `Health` - 현재 체력(float)
- `foodLevel` - 허기 수준(int, 0-20)
- `foodSaturationLevel` - 포만도 수준(float)
- `XpLevel` - 경험치 레벨(int)
- `XpP` - 경험치 진행도(float, 0.0-1.0)
- `Pos[0]`, `Pos[1]`, `Pos[2]` - X, Y, Z 좌표
- `Inventory` - 플레이어 인벤토리 배열
- `SelectedItemSlot` - 현재 선택된 핫바 슬롯(int, 0-8)

### 일반적인 블록 NBT
- `Items` - 컨테이너 내용물(상자, 화로 등)
- `CustomName` - 블록의 사용자 지정 이름
- `Lock` - 컨테이너 잠금 문자열

### 일반적인 모드 추가 NBT 예시
- **마법 모드**: 마나는 종종 `playerMana`, `mana.current` 또는 이와 유사한 이름으로 저장됩니다
- **기술 모드**: `energy`, `forgeEnergy`, `energyStorage.energy` 같은 에너지 값
- **RPG 모드**: `customStats.strength`, `rpgAttributes.level` 같은 사용자 지정 스탯

모드 추가 NBT 경로를 찾으려면 모드가 활성화된 상태에서 `/data get entity @p`를 사용하고 모드가 추가한 사용자 지정 태그를 확인하세요.

## 제한 사항

- **클라이언트에서는 저장소 접근 불가** - 저장소 데이터 소스는 클라이언트 측에서 지원되지 않습니다(서버 측 전용)
- **성능** - NBT 데이터에 자주 접근하면 성능에 영향을 줄 수 있습니다
- 경로가 잘못되었거나 데이터에 접근할 수 없으면 빈 문자열을 반환합니다

## 팁

1. 항상 먼저 게임 내에서 `/data get`을 사용해 NBT 경로를 테스트하세요
2. `scale` 매개변수를 사용해 값을 퍼센트나 다른 유용한 형식으로 변환하세요
3. 일부 NBT 데이터는 클라이언트에 동기화되지 않을 수 있다는 점을 기억하세요
4. 엔티티 선택자는 렌더 거리 내의 엔티티로 제한됩니다
5. 모드 콘텐츠의 경우, 모드 문서를 확인하거나 `/data get`을 사용해 사용자 지정 NBT 경로를 찾아보세요
