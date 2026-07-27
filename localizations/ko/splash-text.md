---
title: 스플래시 텍스트
description: FancyMenu에서 사용자 지정 스플래시 텍스트를 만드는 방법입니다.
---

# 사용자 지정 스플래시 텍스트 요소

FancyMenu의 스플래시 텍스트 요소는 Minecraft의 튀어 오르는 타이틀 스플래시를 완전히 사용자 지정할 수 있게 확장한 버전입니다. 익숙한 튀어 오르는 효과는 유지하면서, 무엇이 표시될지, 어떻게 보일지, 언제 갱신될지를 직접 제어할 수 있습니다.

> [!WARNING]
> 제목 화면의 기본 Vanilla 스플래시 텍스트 요소는 사실상 사용자 지정할 수 없으므로, 그것을 **삭제**하고 대신 사용자 지정 스플래시 텍스트 요소를 사용해야 합니다.

## 요소 추가 및 선택하기
- 레이아웃 편집기를 열고 `Splash Text`라는 요소를 추가합니다.
- 한 번 왼쪽 클릭해 선택하고 바운딩 박스를 표시한 다음, 오른쪽 클릭해 컨텍스트 메뉴를 엽니다. 모든 설정 옵션은 그 메뉴 안에 있습니다.

## 스플래시 텍스트의 출처 선택하기
- `Source Mode: Vanilla`는 Minecraft 기본 제공의 클래식 랜덤 스플래시를 그대로 사용합니다.
- `Source Mode: Direct Input`에서는 `Input Splash Text`를 통해 직접 텍스트를 입력할 수 있습니다. 이는 스플래시 텍스트 한 줄만 지원하지만, 그 줄 안에 플레이스홀더를 포함할 수 있습니다.
- `Source Mode: Text File`은 `Set Source Text File`로 선택한 `.txt` 파일에서 무작위 줄 하나를 불러옵니다. 비어 있지 않은 각 줄이 활성 스플래시가 될 수 있습니다.
- 모드를 전환하면 현재 활성 텍스트가 초기화되므로 안심하고 시험해 볼 수 있습니다. 텍스트가 고정된 것처럼 보이면 다른 모드로 바꾸거나 `Refresh On Screen Load: Enabled`를 클릭해 메뉴를 열 때마다 강제로 다시 뽑히게 하세요.

## 예시 텍스트 파일
"Text File" 소스 모드를 사용할 때는 스플래시 목록을 일반 텍스트(UTF-8, BOM 없음)로 저장하세요. 각 줄이 가능한 스플래시가 됩니다:

```
Welcome to FancyMenu!
{"placeholder":"your_placeholder_id_here"}
{"text":"This is gold and bold text.","color":"gold","bold":true}
&6Use &lMinecraft formatting codes!
```

`your_placeholder_id_here`를 런타임에 해석할 플레이스홀더로 바꾸세요. FancyMenu는 스플래시가 갱신될 때마다 비어 있지 않은 줄 중 하나를 무작위로 선택합니다.

## 원하는 모양으로 만들기
- `Set Scale`과 `Set Rotation`으로 크기와 회전 각도를 조절할 수 있습니다.
- `Set Text Color`는 테마에 맞게 16진수 값(예: `#FFFF00`)을 입력할 수 있습니다.
- `Shadow: Enabled`는 Minecraft의 그림자를 추가합니다. 평면 텍스트로 사용하려면 끄세요.
- `Bouncing: Enabled`는 익숙한 흔들림 동작을 유지합니다. 정적인 라벨로 쓰려면 비활성화하세요.
- FancyMenu는 스플래시를 완전한 Minecraft 컴포넌트로 렌더링하므로, 색상 코드와 다른 텍스트 꾸밈도 모두 정상적으로 작동합니다.

## 동적 텍스트 기능
- 플레이스홀더는 렌더링 전에 해석되므로, 스플래시 텍스트 안에서 플레이어 이름, 날짜 또는 기타 지원되는 값을 참조할 수 있습니다.
- 이 요소는 Minecraft의 직렬화된 컴포넌트 JSON을 받아들이므로, 고급 JSON 스니펫을 Direct Input이나 텍스트 파일에 붙여넣을 수 있습니다. 요소가 자동으로 역직렬화하며, 문제가 생기면 일반 텍스트로 되돌아갑니다.

## 문제 해결
- Direct Input의 빈 텍스트는 편집 중에 `< empty splash element >`로 표시됩니다. 경고를 없애려면 아무 내용이나 입력하세요(공백 하나만 넣어도 됨).
- 텍스트 파일에 유효한 줄이 하나도 없으면 요소는 `ERROR: SPLASH FILE IS EMPTY`를 표시합니다. 비어 있지 않은 줄을 적어도 하나 추가한 뒤 화면을 다시 여세요.
- 직렬화된 JSON에 오류가 있으면 일반 텍스트로 대체됩니다. Mojang의 표준 JSON 구조를 사용하거나, 붙여넣기 전에 바닐라 `/tellraw` 명령으로 스니펫을 테스트하세요.
