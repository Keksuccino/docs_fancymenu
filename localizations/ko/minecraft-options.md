---
title: Minecraft 옵션 설정/가져오기
description: '볼륨, FOV, 렌더 거리 등 Minecraft 옵션을 설정하고 가져오는 방법입니다.'
---

# FancyMenu에서 Minecraft 옵션 다루기

FancyMenu를 사용하면 다양한 UI 요소를 통해 Minecraft 게임 설정(옵션)을 가져오고 설정할 수 있습니다. 이 가이드에서는 사용자 지정 메뉴 레이아웃에서 버튼, 슬라이더, 티커를 사용해 Minecraft 옵션을 다루는 방법을 소개합니다.

# Minecraft 옵션 이해하기

Minecraft에는 그래픽 설정부터 사운드 볼륨까지 다양한 요소를 제어하는 내장 옵션이 있습니다. FancyMenu를 사용하면 이러한 옵션을 이름으로 접근할 수 있습니다.

자주 사용하는 옵션 이름은 다음과 같습니다:
- `soundCategory_master` - 전체 볼륨
- `soundCategory_music` - 음악 볼륨
- `soundCategory_ambient` - 주변 소리 볼륨
- `soundCategory_players` - 플레이어 소리 볼륨
- `soundCategory_blocks` - 블록 소리 볼륨
- `fov` - 시야각
- `gamma` - 밝기
- `renderDistance` - 렌더 거리

# 옵션 값 표시하기

특수 플레이스홀더를 사용하면 어떤 Minecraft 옵션의 현재 값이든 표시할 수 있습니다.

플레이스홀더 형식은 다음과 같습니다:
```
{"placeholder":"minecraft_option_value","values":{"name":"option_name"}}
```

`option_name`을 표시하려는 실제 옵션 이름으로 바꾸세요.

# 버튼으로 옵션 설정하기

버튼을 사용하면 Minecraft 옵션에 특정 값을 설정할 수 있습니다.

## 버튼 설정 방법:

1. 새 Button 요소를 생성합니다
2. 버튼 라벨(버튼에 표시될 텍스트)을 설정합니다
3. 액션을 추가합니다: 버튼을 우클릭 → Edit Action Script → Add Action → Set Minecraft Option Value
4. "Set Minecraft Option Value" 창에서:
   - Name: 옵션 이름 입력(예: `renderDistance`)
   - Value: 설정할 값 입력(예: `16`)

## 예시:

렌더 거리를 16 청크로 설정하는 버튼 만들기:
- Option Name: `renderDistance`
- Value: `16`
- Label: "렌더 거리를 16 청크로 설정"

# 슬라이더로 옵션 설정하기

슬라이더는 볼륨 설정이나 밝기처럼 범위가 있는 옵션에 적합합니다.

## 슬라이더 설정 방법:

1. 새 Slider 요소를 생성합니다
2. 슬라이더 유형을 설정합니다:
   - 정수(예: 렌더 거리): "Integer Range" 선택
   - 소수(예: 볼륨): "Decimal Range" 선택
3. 최소값과 최대값을 설정합니다
4. Minecraft 옵션을 설정하는 액션을 추가합니다:
   - 우클릭 → Edit Action Script → Add Action → Set Minecraft Option Value
   - Name: 옵션 이름
   - Value: `$$value` (이 특수 변수에는 현재 슬라이더 값이 들어 있습니다)
5. 현재 옵션 값으로 미리 선택되도록 설정합니다:
   - "Pre-Selected Value"를 `{"placeholder":"minecraft_option_value","values":{"name":"option_name"}}`로 설정합니다

## 예시 슬라이더 라벨 형식:

슬라이더 라벨에 현재 옵션 값을 표시하려면 다음을 사용합니다:
```
볼륨: {"placeholder":"minecraft_option_value","values":{"name":"soundCategory_master"}}
```

퍼센트로 표시하려면(볼륨에 유용):
```
볼륨: {"placeholder":"calc","values":{"expression":"$$value * 100.0","decimal":"false"}}%
```

# 티커로 옵션 설정하기

티커는 보이지 않는 요소로, 일정한 시간표에 따라 옵션을 자동으로 변경할 수 있습니다.

## 티커 설정 방법:

1. 새 Ticker 요소를 생성합니다
2. tick 설정을 구성합니다:
   - Tick Mode: 옵션을 언제 갱신할지 선택
   - Tick Delay: 갱신 주기 설정(밀리초)
3. Minecraft 옵션을 설정하는 액션을 추가합니다:
   - 우클릭 → Edit Action Script → Add Action → Set Minecraft Option Value
   - 옵션 이름과 값을 설정

## 예시:

메뉴가 열릴 때 gamma(밝기)를 최대값으로 설정:
- Tick Mode: On Load Screen
- Name: `gamma`
- Value: `1.0`

# 일반적인 사용 사례

FancyMenu를 사용해 Minecraft 옵션을 설정하고 가져올 때 활용할 수 있는 몇 가지 일반적인 예를 소개합니다.

## 사용자 지정 볼륨 슬라이더 만들기

볼륨 슬라이더는 Minecraft 옵션 연동에서 가장 흔한 용도입니다. 예를 들어 사용자 지정 음악 볼륨 슬라이더를 만드는 방법은 다음과 같습니다:

1. 새 Slider 요소를 생성합니다
2. "Slider Type"을 "Decimal Range"로 설정합니다
3. "Minimum Range Value"를 "0.0"으로 설정합니다
4. "Maximum Range Value"를 "1.0"으로 설정합니다
5. Edit Action Script → Add Action → Set Minecraft Option Value
   - Name을 `soundCategory_music`로 설정
   - Value를 `$$value`로 설정
6. "Pre-Selected Value"를 `{"placeholder":"minecraft_option_value","values":{"name":"soundCategory_music"}}`로 설정
7. 볼륨을 퍼센트로 표시하려면 라벨을 다음과 같이 설정합니다: 
   ```
   Music: {"placeholder":"calc","values":{"expression":"$$value * 100.0","decimal":"false"}}%
   ```

다른 사운드 카테고리에도 비슷한 슬라이더를 만들 수 있습니다:
- Master Volume: `soundCategory_master`
- Music: `soundCategory_music`
- Ambient: `soundCategory_ambient`
- Blocks: `soundCategory_blocks`
- Players: `soundCategory_players`
- Weather: `soundCategory_weather`

## 사용자 지정 FOV 슬라이더 만들기

시야각(FOV)은 게임에서 얼마나 넓게 보이는지를 결정하는 중요한 그래픽 설정입니다. FOV 옵션은 내부적으로 -1.0에서 1.0까지의 값을 사용하지만, UI에서는 30에서 110으로 표시됩니다.

### FOV 값 매핑 이해하기
- 내부 값 범위: -1.0 ~ 1.0
- 표시 값 범위: 30 ~ 110
- 매핑 공식: `(internal_value + 1) * 40 + 30`

### 1단계: FOV 텍스트를 업데이트할 티커 요소 만들기

먼저 현재 FOV 값을 확인하고 적절한 설명을 변수에 설정하는 티커가 필요합니다:

1. 새 Ticker 요소를 생성합니다
2. "Tick Mode"를 "Normal"로 설정합니다(계속 업데이트되도록)
3. "Tick Delay"를 약 "10"(밀리초)으로 설정해 과도한 확인을 방지합니다

이제 FOV 라벨에 대한 액션을 설정해야 합니다. 액션 스크립트 구조는 다음과 같아야 합니다:

```
▶ Action Script
│
├─▶ IF (mapped FOV = 70)
│  └─■ Set Variable Value: fov_text:Normal
│
├─▶ ELSE-IF (mapped FOV = 110)
│  └─■ Set Variable Value: fov_text:Quake Pro
│
└─▶ ELSE
   └─■ Set Variable Value: fov_text:[calculated numeric value]
```

각 부분을 설정해 봅시다:

#### "Normal" FOV 라벨 설정:
1. 우클릭 → Edit Action Script → Add Action
2. "IF Statement"를 클릭해 조건 블록을 추가합니다
3. 요구 조건을 "Is Number"로 설정하고 다음을 입력합니다:
   - Compare Mode: "equals"
   - Number: `{"placeholder":"calc","values":{"decimal":"false","expression":"({"placeholder":"minecraft_option_value","values":{"name":"fov"}} + 1) * 40 + 30"}}`
   - Compare With: "70"
4. 이 IF 블록 안에 "Set Variable Value (FM Variable)" 액션을 추가하고 다음을 설정합니다:
   - Value: `fov_text:Normal`

#### "Quake Pro" FOV 라벨 설정:
1. Action Script 안에 "ELSE-IF Statement"를 추가합니다
2. 요구 조건을 "Is Number"로 설정하고 다음을 입력합니다:
   - Compare Mode: "equals"
   - Number: `{"placeholder":"calc","values":{"decimal":"false","expression":"({"placeholder":"minecraft_option_value","values":{"name":"fov"}} + 1) * 40 + 30"}}`
   - Compare With: "110"
3. 이 ELSE-IF 블록 안에 "Set Variable Value (FM Variable)" 액션을 추가하고 다음을 설정합니다:
   - Value: `fov_text:Quake Pro`

#### 숫자 FOV 라벨 설정:
1. "ELSE Statement" 블록을 추가합니다
2. 이 ELSE 블록 안에 "Set Variable Value (FM Variable)" 액션을 추가하고 다음을 설정합니다:
   - Value: `fov_text:{"placeholder":"calc","values":{"decimal":"false","expression":"({"placeholder":"minecraft_option_value","values":{"name":"fov"}} + 1) * 40 + 30"}}`

<img src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/fov_slider_action_script.png" alt="FOV Slider Action Script" style="max-width: 600px; height: auto;">

### 2단계: FOV 슬라이더 만들기

1. 새 Slider 요소를 생성합니다
2. "Slider Type"을 "Decimal Range"로 설정합니다
3. "Minimum Range Value"를 "-1.0"으로 설정합니다
4. "Maximum Range Value"를 "1.0"으로 설정합니다
5. Edit Action Script → Add Action → Set Minecraft Option Value
   - Name을 `fov`로 설정
   - Value를 `$$value`로 설정
6. "Pre-Selected Value"를 `{"placeholder":"minecraft_option_value","values":{"name":"fov"}}`로 설정

### 3단계: 슬라이더 라벨 설정

슬라이더 라벨은 FOV 텍스트 변수를 단순히 표시하도록 설정합니다:

```
FOV: {"placeholder":"getvariable","values":{"name":"fov_text"}}
```

이 라벨은 다음과 같이 표시됩니다:
- 값이 70일 때 "FOV: Normal"
- 값이 110일 때 "FOV: Quake Pro"  
- 그 외의 모든 값은 "FOV: 85"(또는 다른 숫자)

### FOV 슬라이더 팁

- 내부 슬라이더 값 범위는 -1.0 ~ 1.0이며, 표시를 위해 30 ~ 110으로 매핑해야 합니다
- 변환 공식은 `(internal_value + 1) * 40 + 30` 입니다
- 특수 라벨이 적용되는 값은 70(Normal)과 110(Quake Pro)뿐입니다
- Minecraft의 기본 FOV는 70입니다(내부 값 0.0에 해당)
- `fov_text` 변수에는 자동으로 특수 라벨 또는 숫자 값이 들어갑니다

## 텍스트 요소에서 옵션 값 표시하기

Text 요소에서도 현재 옵션 값을 표시할 수 있습니다:

1. Text 요소를 생성합니다
2. 텍스트 내용으로 다음 플레이스홀더를 사용합니다: `{"placeholder":"minecraft_option_value","values":{"name":"option_name"}}`

예를 들어 현재 렌더 거리를 표시하려면:
```
현재 렌더 거리: {"placeholder":"minecraft_option_value","values":{"name":"renderDistance"}} 청크
```

# 옵션 이름 찾기

사용 가능한 모든 옵션의 이름은 다음 방법으로 찾을 수 있습니다:

  1. 버튼을 생성합니다
  2. 버튼을 우클릭합니다
  3. "Edit Action Script"를 클릭합니다
  4. "Set Minecraft Option Value" 액션을 추가합니다
  5. 액션 값을 편집할 때 "Name" 필드에 입력을 시작하면 드롭다운 제안을 확인할 수 있습니다
  
# 중요한 팁

- **유효한 값**: 모든 옵션이 모든 값을 허용하는 것은 아닙니다. 예를 들어:
  - 볼륨 옵션은 0.0 ~ 1.0 값을 허용합니다
  - 렌더 거리는 일반적으로 2 ~ 32 사이의 정수를 허용합니다
  - `pauseOnLostFocus` 같은 불리언(true/false) 옵션은 "true" 또는 "false"를 허용합니다

- **테스트**: 설정이 예상대로 작동하는지 항상 테스트하세요!

- **시각적 피드백**: 위에서 설명한 플레이스홀더를 사용해 현재 값에 대한 시각적 피드백을 사용자에게 제공하세요.
