---
title: GLSL 셰이더 API
description: '배경, 요소 및 장식 오버레이용 FancyMenu GLSL 셰이더를 작성합니다.'
sourceBlobSha: f3da9c3fe83444dab5c59f74f5011e2d6e8cf9e6
---

# FancyMenu GLSL 셰이더 API

이 문서에서는 FancyMenu의 다음 기능에서 사용하는 GLSL 런타임을 설명합니다.

- `GLSL` 메뉴 배경
- `GLSL` 요소
- `GLSL` 장식 오버레이

컴파일 모드, 멀티패스 라우팅, 지원 유니폼 및 실용적인 셰이더 작성 패턴을 다룹니다.

## 1. 런타임 개요

FancyMenu는 내부 OpenGL 파이프라인(`#version 150`)을 사용해 셰이더를 렌더링하며 다음을 지원합니다.

- 단일 패스 셰이더(`Image` 패스만 사용)
- 멀티패스 셰이더(`Buffer A` / `B` / `C` / `D` + `Image`)
- Shadertoy 스타일 진입점(`mainImage`)
- 직접 프래그먼트 진입점(`main`)

셰이더 소스는 인라인 텍스트 필드에 입력합니다.

- `Shader Source` (`Image` 패스, 렌더링에 필수)
- `Buffer A Source` (선택 사항)
- `Buffer B Source` (선택 사항)
- `Buffer C Source` (선택 사항)
- `Buffer D Source` (선택 사항)

Image 소스가 비어 있으면 "no source" 오류가 발생하고 렌더링에 실패합니다.

## 2. 컴파일 모드

FancyMenu는 세 가지 컴파일 모드를 지원합니다.

- `Auto`
- `Direct Fragment`
- `Shadertoy`

### 2.1 Shadertoy 모드

예상 진입점:

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord)
```

FancyMenu는 이를 `main()`으로 감싸고 영역 기준 로컬 좌표를 전달합니다.

```glsl
mainImage(fmColor_FancyMenu, gl_FragCoord.xy - fmAreaOffset);
```

래퍼는 출력 알파에 `fmOpacity`를 곱합니다.

### 2.2 직접 모드

예상 진입점:

```glsl
void main()
```

호환성 동작:

- `gl_FragColor` 호환 변형으로 컴파일을 시도합니다.
- 호환 기능을 사용하지 않는 변형도 시도합니다(최신 명시적 `out vec4` 셰이더용).

직접 모드에서는 `fmOpacity`가 출력에 자동으로 적용되지 않습니다. 필요한 경우 직접 적용하세요.

### 2.3 자동 모드

Auto 모드는 호환 가능한 변형을 순서대로(Shadertoy/직접) 시도하고, 가장 먼저 컴파일에 성공한 변형을 사용합니다.

## 3. 소스 전처리 및 기본 제공 매크로

컴파일 전에 FancyMenu는 소스를 정규화합니다.

- UTF-8 BOM 제거
- CRLF/CR을 LF로 변환
- `#version ...` 줄 제거
- `precision ...;` 줄 제거

런타임에서 삽입하는 프리앰블에는 다음이 포함됩니다.

- `#version 150`
- `in vec2 fmUv_FancyMenu`(`[0,1]` 범위의 전체 화면 UV, 원점은 왼쪽 아래)
- `#define iGlobalTime iTime`
- `#define texture2D texture`
- `#define textureCube texture`

참고:

- 소스에 이미 알려진 유니폼 이름(예: `iTime`)이 선언되어 있으면 FancyMenu는 중복 선언을 삽입하지 않습니다.
- FancyMenu는 런타임에 해당 이름으로 값을 계속 업로드합니다.
- 여기서 `textureCube`는 별칭 매크로일 뿐이며, `iChannel0..3`은 `sampler2D` 유니폼입니다.

## 4. 패스 시스템(Image + Buffer A-D)

FancyMenu에는 5개의 패스 슬롯이 있습니다.

- `Buffer A`
- `Buffer B`
- `Buffer C`
- `Buffer D`
- `Image` (화면에 표시되는 최종 패스)

동작 방식:

- 버퍼 패스는 소스가 비어 있지 않은 경우에만 실행됩니다.
- 출력을 렌더링하려면 Image 패스가 있어야 합니다.
- 버퍼는 부동 소수점 텍스처(`GL_RGBA16F`)로 렌더링된 다음, 매 프레임 읽기/쓰기 대상을 서로 바꾸는 핑퐁 방식으로 처리됩니다.

### 4.1 패스별 채널 라우팅

각 패스는 `iChannel0..3`의 라우팅을 제공합니다. 각 채널에서 다음 항목을 선택할 수 있습니다.

- `None`
- `Resource 0`
- `Resource 1`
- `Resource 2`
- `Resource 3`
- `Buffer A`
- `Buffer B`
- `Buffer C`
- `Buffer D`

리소스 채널은 `iChannel# Resource` 설정에서 가져옵니다.

기본값:

- 모든 `iChannel` 라우팅은 기본적으로 `None`입니다.
- 해당 버퍼의 소스가 비어 있지 않을 때까지 버퍼 패스는 활성화되지 않습니다.

중요:

- 동일한 버퍼 패스로 라우팅하면(피드백) 이전 프레임의 데이터(핑퐁 읽기 텍스처)를 읽습니다.
- 라우팅된 소스가 없거나 비활성 상태이면 대체 텍스처가 바인딩되고 `iChannelResolution[n].z`는 `0.0`이 됩니다.

## 5. 좌표 및 영역 의미

셰이더는 사각형 영역 안에서 실행됩니다.

- 메뉴 배경: 전체 화면 영역
- GLSL 요소: 요소 사각형

좌표 규칙:

- 픽셀 유니폼은 영역 기준 로컬 픽셀 단위입니다.
- 셰이더에서 사용하는 픽셀 좌표의 Y 원점은 왼쪽 아래입니다.
- 마우스 좌표는 영역 안으로 제한되지 않으므로 커서가 영역 밖에 있으면 좌표도 영역 밖의 값이 될 수 있습니다.

특수 필드:

- `fmAreaOffset`: 화면 픽셀 공간에서 영역의 왼쪽 아래 위치
- `fmAreaTopLeft`: 화면 픽셀 공간에서 영역의 왼쪽 위 위치
- `fmAreaSize`: 픽셀 단위 영역 크기

## 6. 유니폼 API 참조

아래 유니폼은 배경 셰이더와 요소 셰이더 모두에서 사용할 수 있습니다.

## 6.1 Shadertoy 호환 유니폼

| 유니폼 | 타입 | 의미 |
|---|---|---|
| `iResolution` | `vec3` | `(areaWidthPx, areaHeightPx, 1.0)` |
| `iTime` | `float` | 누적된 셰이더 실행 시간(초) |
| `iTimeDelta` | `float` | 마지막 렌더링의 시간 간격. 고정 및 시간 배율의 영향을 받습니다. |
| `iFrameRate` | `float` | Minecraft FPS를 대체값으로 사용하는 런타임 FPS |
| `iFrame` | `int` | 런타임별 프레임 카운터 |
| `iMouse` | `vec4` | 아래 세부 정보 참조 |
| `iDate` | `vec4` | `(연도, 월, 일, 소수부가 포함된 하루 경과 초)` |
| `iSampleRate` | `float` | 상수 `44100.0` |
| `iChannelTime[4]` | `float[4]` | 현재 모든 값이 `iTime`으로 설정됩니다. |
| `iChannelResolution[4]` | `vec3[4]` | 채널별 `(너비, 높이, 유효 플래그)` |
| `iChannel0..3` | `sampler2D` | 라우팅된 텍스처 입력 |

### `iMouse` 세부 정보

`iMouse = vec4(x, y, z, w)`

- `x`, `y`: 현재 영역 기준 로컬 마우스 픽셀 위치. 토글이 활성화되면 고정 동작이 적용될 수 있습니다.
- `z`, `w`: 왼쪽 클릭 시작 위치
  - 마우스 왼쪽 버튼을 누르고 있는 동안 양수
  - 버튼을 놓은 뒤에는 음수

토글에 따른 동작:

- `Update iMouse Position Only While Holding LMB = Off`:
  - `iMouse.xy`가 계속 갱신됩니다.
- `... = On`:
  - `iMouse.xy`는 LMB를 누르고 있는 동안에만 갱신된 뒤, 마지막으로 누르고 있던 위치에 고정됩니다.

기본값:

- `Off` (계속 갱신)

## 6.2 FancyMenu 전용 유니폼

| 유니폼 | 타입 | 의미 |
|---|---|---|
| `fmAreaOffset` | `vec2` | 화면 공간에서 영역의 왼쪽 아래 픽셀 오프셋 |
| `fmAreaSize` | `vec2` | 픽셀 단위 영역 크기 |
| `fmAreaPosition` | `vec2` | `fmAreaOffset`과 동일 |
| `fmAreaTopLeft` | `vec2` | 화면 공간에서 영역의 왼쪽 위 픽셀 오프셋 |
| `fmScreenSize` | `vec2` | 픽셀 단위 전체 화면 크기 |
| `fmGuiScale` | `float` | 현재 GUI 배율 |
| `fmMouse` | `vec4` | `(로컬 픽셀 X, 로컬 픽셀 Y(아래 기준), 로컬 정규화 X, 로컬 정규화 Y)` |
| `fmMouseDelta` | `vec2` | 영역 픽셀 단위 마우스 이동량(Y는 셰이더의 위쪽 방향에 맞게 반전됨) |
| `fmMouseButtons` | `ivec4` | 버튼 `0..3`의 누름 상태 |
| `fmMouseClickCount` | `ivec4` | 버튼 `0..3`의 누적 누름 횟수 |
| `fmMouseReleaseCount` | `ivec4` | 버튼 `0..3`의 누적 해제 횟수 |
| `fmMouseScroll` | `vec2` | 이 런타임의 이전 렌더링 이후 발생한 스크롤 변화량 |
| `fmMouseScrollTotal` | `vec2` | 누적 스크롤 합계 |
| `fmKeyEvent` | `ivec4` | `(마지막 키 코드, 마지막 스캔 코드, 마지막 수정자, 마지막 동작)` |
| `fmKeyEventCount` | `int` | 누적 키 이벤트 카운터 |
| `fmCharEvent` | `ivec4` | `(마지막 코드 포인트, 마지막 수정자, 0, 0)` |
| `fmCharEventCount` | `int` | 누적 문자 입력 이벤트 카운터 |
| `fmDateParts` | `ivec4` | `(연도, 월, 일, 요일(ISO 1~7))` |
| `fmTimeParts` | `ivec4` | `(시, 분, 초, 밀리초 부분(0~999))` |
| `fmDayOfYear` | `int` | 연중 일수 |
| `fmWeekOfYear` | `int` | ISO 연중 주차 |
| `fmUnixTimeSeconds` | `int` | Unix epoch 기준 초 |
| `fmUnixTimeMilliseconds` | `int` | 현재 시각의 밀리초 부분(`0..999`) |
| `fmPartialTick` | `float` | 현재 부분 틱 |
| `fmGameDeltaTicks` | `float` | Minecraft 게임 시간 변화 틱 |
| `fmRealtimeDeltaTicks` | `float` | Minecraft 실제 시간 변화 틱 |
| `fmInWorld` | `int` | 월드 안에 있으면 `1`, 아니면 `0` |
| `fmIsPaused` | `int` | 일시 정지 상태이면 `1`, 아니면 `0` |
| `fmOpacity` | `float` | 유효 불투명도 배율(`0..1`) |
| `fmVariableCount` | `int` | 현재 FancyMenu 변수 개수 |

키 동작 값(`fmKeyEvent.w`):

- `0` = 해제
- `1` = 누름
- `2` = 반복

## 6.3 FancyMenu 변수 유니폼 API

FancyMenu 변수는 런타임 유니폼으로 직접 노출되므로(배경, 요소 및 장식 오버레이 셰이더에서 사용 가능), 값이 바뀌어도 셰이더를 다시 컴파일할 필요가 없습니다.

### 이름 지정

각 변수 `<name>`에 대해 FancyMenu는 다음 항목을 제공합니다.

- `fmVarFloat_<name>`
- `fmVarInt_<name>`
- `fmVarBool_<name>`
- `fmVarVec2_<name>`
- `fmVarVec3_<name>`
- `fmVarVec4_<name>`
- `fmVarExists_<name>` (`1` = 변수가 현재 존재함, `0` = 변수 없음/삭제됨)

`<name>`의 유니폼 접미사 정리 규칙:

- 허용 문자: `[A-Za-z0-9_]`
- 그 외의 문자는 모두 `_`로 변환됩니다.
- 첫 문자가 숫자이면 앞에 `_`가 추가됩니다.

예시:

- 변수 `player_hp` -> 접미사 `player_hp`
- 변수 `player-hp` -> 접미사 `player_hp`
- 변수 `2nd_phase` -> 접미사 `_2nd_phase`

중요:

- 동적 변수 유니폼은 셰이더 소스에 **자동으로 선언되지 않습니다**(사용하는 유니폼은 직접 선언하세요).
- 정리된 접미사가 같은 변수 이름은 같은 GLSL 유니폼 이름에 연결되므로 사용하지 마세요.

### 값 변환

변수 텍스트 값이 `v`라고 할 때:

- `fmVarFloat_*`: 파싱된 실수(기본값 `0.0`)
- `fmVarInt_*`: 파싱된 정수(기본값 `0`)
- `fmVarBool_*`: 불리언/정수로 해석(`true/yes/on/enabled` => `1`, `false/no/off/disabled` => `0`, 그 외에는 0이 아닌 숫자 => `1`)
- 벡터 파싱에서 허용되는 구분자: 공백, `,`, `;`, `|`
  - `fmVarVec2_*`: 파싱된 처음 2개 구성 요소
  - `fmVarVec3_*`: 파싱된 처음 3개 구성 요소
  - `fmVarVec4_*`: 파싱된 처음 4개 구성 요소
  - 구성 요소 수가 부족하면, 파싱된 마지막 구성 요소를 누락된 슬롯에 반복해서 사용합니다.
  - 숫자 구성 요소가 하나도 없으면 모든 벡터 구성 요소에 스칼라 기본값을 사용합니다.

[목록 변수](/variables#text-and-list-variables)는 텍스트 대신 항목 수를 반환합니다.

- `fmVarFloat_*` 및 `fmVarInt_*`: 항목 수. 예를 들어 항목이 3개인 목록은 `3`을 반환합니다.
- `fmVarBool_*`: 목록에 항목이 있으면 `1`, 비어 있으면 `0`
- `fmVarVec2_*`, `fmVarVec3_*` 및 `fmVarVec4_*`: 모든 구성 요소에 항목 수를 반환합니다.

변수가 삭제되면:

- `fmVarExists_*`는 `0`이 됩니다.
- 해당하는 모든 `fmVar*_*` 값은 `0`으로 초기화됩니다.

### 선언 및 사용 예시

```glsl
uniform float fmVarFloat_player_hp;
uniform int fmVarBool_is_boss_phase;
uniform vec3 fmVarVec3_theme_color;
uniform int fmVarExists_player_hp;

void mainImage(out vec4 fragColor, in vec2 fragCoord) {
    vec2 uv = fragCoord / iResolution.xy;

    float hp = clamp(fmVarFloat_player_hp / 100.0, 0.0, 1.0);
    vec3 theme = fmVarVec3_theme_color;
    float boss = float(fmVarBool_is_boss_phase);

    vec3 col = mix(theme * 0.25, theme, hp);
    col += vec3(0.2, 0.0, 0.0) * boss;

    if (fmVarExists_player_hp == 0) {
        col = vec3(0.15);
    }

    fragColor = vec4(col, 1.0);
}
```

## 7. 입력 추적 모델

FancyMenu는 입력을 전역에서 추적하고 렌더링할 때마다 입력 상태를 캡처합니다.

- 마우스 이동/드래그
- 마우스 누름/해제
- 스크롤
- 키 누름/해제/반복
- 문자 입력

마우스 안정성:

- 런타임은 버튼이 눌린 채로 남는 현상을 방지하기 위해 매 프레임 GLFW의 상태 조회 결과와 버튼 상태를 대조합니다.

`Pass Input Events To Shader`가 비활성화된 경우:

- 입력 유니폼은 매 프레임 중립값으로 초기화됩니다.
- 셰이더에서 확인할 수 있는 데이터의 카운터와 이벤트는 0으로 설정됩니다.

## 8. 텍스처 입력 세부 정보

리소스 채널(`iChannel# Resource`)은 2D 텍스처를 사용합니다.

채널별 텍스처 상태:

- 유효한 리소스: 텍스처가 바인딩되고 실제 너비/높이를 사용하며, `iChannelResolution[n].z = 1.0`입니다.
- 없음/비활성/None: 대체 텍스처가 바인딩되고 `iChannelResolution[n].xyz = (0,0,0)`입니다.

버퍼 텍스처:

- 내부 형식: `RGBA16F`(부동 소수점)
- 필터링: 선형
- 래핑: 가장자리 고정

이 형식은 `[0,1]` 범위를 벗어나는 값도 포함한 멀티패스 데이터에 적합합니다.

## 9. 렌더링 및 블렌딩 참고 사항

- 버퍼 패스는 블렌딩 없이 오프스크린으로 렌더링됩니다.
- 최종 Image 패스는 합성할 때 `Enable Blending` 설정을 사용합니다.
- Shadertoy 래퍼는 `fmOpacity`를 알파에 자동으로 적용합니다.
- 직접 셰이더에서는 필요한 경우 `fmOpacity`를 직접 적용해야 합니다.

## 10. 실용적인 템플릿

## 10.1 최소 Shadertoy 스타일 셰이더

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord) {
    vec2 uv = fragCoord / iResolution.xy;
    vec3 col = vec3(uv, 0.5 + 0.5 * sin(iTime));
    fragColor = vec4(col, 1.0);
}
```

## 10.2 최소 직접 프래그먼트 셰이더

```glsl
out vec4 FragColor;

void main() {
    vec2 uv = gl_FragCoord.xy - fmAreaOffset;
    uv /= iResolution.xy;

    vec3 col = vec3(uv.x, uv.y, 0.5 + 0.5 * sin(iTime));
    FragColor = vec4(col, fmOpacity);
}
```

## 10.3 최소 피드백 멀티패스

### Buffer A 소스

라우팅: `Buffer A iChannel0 Input -> Buffer A`

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord) {
    vec2 uv = fragCoord / iResolution.xy;
    vec4 prev = texture(iChannel0, uv);
    vec4 seed = vec4(uv, 0.0, 1.0);
    fragColor = mix(prev, seed, 0.02);
}
```

### Image 소스

라우팅: `Image iChannel0 Input -> Buffer A`

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord) {
    vec2 uv = fragCoord / iResolution.xy;
    fragColor = texture(iChannel0, uv);
}
```

## 11. 문제 해결 체크리스트

- 출력이 없음:
  - Image 소스가 비어 있지 않은지 확인합니다.
  - 컴파일 모드가 진입점(`mainImage` 또는 `main`)과 일치하는지 확인합니다.
- 보라색/유효하지 않은 텍스처:
  - 리소스 바인딩과 채널 라우팅을 확인합니다.
  - `iChannelResolution[n].z`를 확인합니다(`0.0`은 유효하지 않거나 사용할 수 없음을 의미합니다).
- 직접 셰이더에서 좌표가 잘못됨:
  - 영역 기준 로컬 좌표에는 `gl_FragCoord.xy - fmAreaOffset`을 사용합니다.
- 드래그 동작이 올바르지 않음:
  - `Update iMouse Position Only While Holding LMB` 토글을 사용합니다.
- 직접 셰이더에 불투명도가 적용되지 않음:
  - 알파에 `fmOpacity`를 직접 곱합니다.
