---
title: 변수
description: 변수를 생성하고 사용하는 방법입니다.
sourceBlobSha: dcd1512bc7f20f3ab535205f24a67c6489231e11
---

# FancyMenu의 변수

변수에는 레이아웃, 액션, 플레이스홀더, 요구 사항, 리스너, 스케줄러 및 Custom GUI에서 재사용할 수 있는 텍스트 값이 저장됩니다.

## 변수 생성

FancyMenu에서 변수를 생성하려면 다음 단계를 따르세요.

1. 현재 레이아웃 편집기에 있지 않은지 확인합니다. 
2. 화면 상단의 메뉴 표시줄을 클릭합니다.
3. **Customization -> Variables -> Manage Variables**로 이동합니다.
4. 표시되는 "Manage Variables" 화면에서 **Add Variable** 버튼을 클릭합니다.
5. 새 변수의 이름을 입력하고 **OK**를 클릭합니다.

이제 변수를 사용할 준비가 되었습니다. "Manage Variables" 화면의 목록에서 변수를 확인할 수 있습니다.

Manage Variables 창에서는 마우스 오른쪽 버튼 클릭 컨텍스트 메뉴, 키보드 탐색, 복사/붙여넣기, 실행 취소/다시 실행, 입력을 통한 검색, 삭제를 위한 **Delete**, 저장을 위한 **Ctrl/Command + S**를 지원합니다.

## 변수 값 설정

빈 변수는 그 자체로는 그다지 유용하지 않습니다. 변수를 활용하려면 변수에 데이터를 넣어야 합니다. FancyMenu에서는 이를 "변수 값 설정"이라고 합니다. 

변수 값을 설정하는 주요 방법은 두 가지입니다.

1. "Manage Variables" 화면에서 목록의 변수를 찾아 클릭한 다음 **Set Value**를 클릭합니다. 저장할 데이터를 입력합니다.

2. 메뉴를 사용자 지정하는 동안 [**Set Variable Value** 액션](./action-scripts#set-variable-value-fm-variable-set_variable)을 [Button](./elements#button), [Slider](./elements#slider) 또는 [Ticker](./elements#ticker) 요소에서 사용합니다.

예를 들어 `clicks`라는 변수를 생성하고 버튼에 [**Set Variable Value** 액션](./action-scripts#set-variable-value-fm-variable-set_variable)을 추가합니다.

```
clicks:{"placeholder":"calc","values":{"expression":"{"placeholder":"getvariable","values":{"name":"clicks"}} + 1"}}
```

작동 방식은 다음과 같습니다.
1. [**Get Stored Variable** 플레이스홀더](./placeholders#get-variable-value-fm-variable-getvariable)가 `clicks` 변수의 현재 값을 가져옵니다.
2. [**Calculator** 플레이스홀더](./placeholders#calculator-calc)가 해당 값에 1을 더합니다.
3. [**Set Variable Value** 액션](./action-scripts#set-variable-value-fm-variable-set_variable)을 사용하여 결과를 다시 `clicks`에 저장합니다.

따라서 버튼을 클릭할 때마다 `clicks` 변수가 1씩 증가하여 총 클릭 횟수를 계산하게 됩니다.

## 변수 사용

이제 데이터를 저장하는 변수가 있으므로 메뉴 사용자 지정의 여러 부분에서 해당 데이터를 사용할 수 있습니다.

* [**로딩 요구 사항**](./conditions): 변수 값을 확인하여 요소가 표시되는 시점을 제어합니다. 예를 들어 [**Is Number**](./conditions#is-number-fancymenu_visibility_requirement_is_number)와 [**Get Stored Variable** 플레이스홀더](./placeholders#get-variable-value-fm-variable-getvariable)를 함께 사용하여 `clicks`가 5보다 클 때 요소를 표시할 수 있습니다.

* **플레이스홀더**: [**Get Stored Variable** 플레이스홀더](./placeholders#get-variable-value-fm-variable-getvariable)를 사용하여 텍스트에 변수를 삽입할 수 있습니다. 예: `{"placeholder":"getvariable","values":{"name":"clicks"}}`.

* **중첩 플레이스홀더**: [**Calculator** 플레이스홀더](./placeholders#calculator-calc) 내부에서 [**Get Stored Variable** 플레이스홀더](./placeholders#get-variable-value-fm-variable-getvariable)를 사용할 수 있습니다.

* **액션**: 변수로 동적인 동작을 만들 수 있습니다.
  - [**Is Number**](./conditions#is-number-fancymenu_visibility_requirement_is_number) 및 [**Get Stored Variable** 플레이스홀더](./placeholders#get-variable-value-fm-variable-getvariable)와 함께 [액션 스크립트](./action-scripts#what-are-statements)에서 **IF** 문을 사용합니다.
  - [**Get Stored Variable** 플레이스홀더](./placeholders#get-variable-value-fm-variable-getvariable)를 [**Copy Text to Clipboard**](./action-scripts#copy-text-to-clipboard-copytoclipboard)와 함께 사용합니다.
  - [**Open Screen or Custom GUI**](./action-scripts#open-screen-or-custom-gui-opengui)에서 변수를 사용하여 저장된 진행 상황이나 설정에 따라 화면을 선택합니다.

## 변수 예시

다음은 변수를 활용하는 데 도움이 되는 몇 가지 예시입니다.

1. **최고 점수**: `highscore` 변수를 생성하고, 플레이어의 현재 점수가 기존 값보다 높을 때 현재 점수를 저장하는 버튼을 만듭니다. [**Get Stored Variable** 플레이스홀더](./placeholders#get-variable-value-fm-variable-getvariable)를 사용하여 표시합니다.

2. **난이도 선택기**: `easy`, `medium`, `hard`와 같이 게임 난이도별 변수를 만듭니다. 버튼을 사용하여 난이도 변수의 값을 설정하고, 선택한 난이도에 따라 요소를 표시하거나 숨깁니다.

3. **튜토리얼 진행 상황**: `tutorial_step`과 같이 튜토리얼 진행 상황을 추적하는 변수를 추가합니다. 각 단계를 완료할 때마다 변수 값을 증가시키고, 로딩 요구 사항을 사용하여 메뉴의 더 많은 부분을 점진적으로 표시합니다.

## 저장, 범위 및 데이터 보관

변수는 현재 Minecraft 인스턴스 전체에서 공유됩니다. 레이아웃, 월드, 서버 또는 플레이어별로 분리되지 않습니다.

값은 `<game-directory>/config/fancymenu/user_variables.db`에 즉시 저장되며 게임을 다시 시작해도 유지됩니다.

- **Reset on Launch**는 다음에 게임을 시작할 때 해당 변수를 비웁니다.
- [**Clear All Variables**](./action-scripts#clear-all-variables-fm-variable-clear_variables)는 저장된 모든 변수 값을 삭제합니다.
- 이름은 대소문자를 구분합니다. `tutorial_step`과 같이 간단하고 고유한 이름을 사용하세요.

[**Get Stored Variable** 플레이스홀더](./placeholders#get-variable-value-fm-variable-getvariable)는 지정한 변수가 존재하지 않거나 저장된 값이 비어 있을 때 `0`을 반환합니다. 이 기본값은 비교 및 계산기 표현식에서 중요합니다.

[**Set Variable Value** 액션](./action-scripts#set-variable-value-fm-variable-set_variable)은 `variable_name:variable_value` 형식을 사용하며 첫 번째 콜론에서 분할하므로 값에 콜론을 여러 개 포함할 수 있습니다.

FancyMenu 변수에 비밀번호, 토큰 또는 기타 비밀 정보를 저장하지 마세요. 변수는 읽을 수 있는 구성 데이터입니다.
