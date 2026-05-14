---
title: GLSL 셰이더 API
description: '배경, 요소, 장식 오버레이를 위한 FancyMenu GLSL 셰이더를 작성합니다.'
---

# FancyMenu GLSL 셰이더 API

이 문서는 FancyMenu에서 사용하는 GLSL 런타임을 설명합니다:

- `GLSL` 메뉴 배경
- `GLSL` 요소
- `GLSL` 장식 오버레이

여기에는 컴파일 모드, 멀티패스 라우팅, 지원되는 uniform, 그리고 실용적인 셰이더 작성 패턴이 포함됩니다.

## 1. 런타임 개요

FancyMenu는 내부 OpenGL 파이프라인(`#version 150`)으로 셰이더를 렌더링하며 다음을 지원합니다:

- 단일 패스 셰이더(`Image` 패스만 사용)
- 멀티패스 셰이더(`Buffer A` / `B` / `C` / `D` + `Image`)
- Shadertoy 스타일 진입점(`mainImage`)
- 직접 fragment 진입점(`main`)

셰이더 소스는 인라인 텍스트 필드로 제공됩니다:

- `Shader Source` (`Image` 패스, 렌더링에 필수)
- `Buffer A Source` (선택)
- `Buffer B Source` (선택)
- `Buffer C Source` (선택)
- `Buffer D Source` (선택)

Image 소스가 비어 있으면 렌더링은 "no source" 오류로 실패합니다.

## 2. 컴파일 모드

FancyMenu는 세 가지 컴파일 모드를 지원합니다:

- `Auto`
- `Direct Fragment`
- `Shadertoy`

### 2.1 Shadertoy 모드

예상되는 진입점:

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord)
```

FancyMenu는 이를 `main()`으로 감싸고 로컬 영역 좌표를 전달합니다:

```glsl
mainImage(fmColor_FancyMenu, gl_FragCoord.xy - fmAreaOffset);
```

이 래퍼는 출력 알파에 `fmOpacity`를 곱합니다.

### 2.2 Direct 모드

예상되는 진입점:

```glsl
void main()
```

호환성 동작:

- `gl_FragColor` 호환 버전을 먼저 시도합니다.
- 최신식 명시적 `out vec4` 셰이더용으로 비호환 버전도 시도합니다.

Direct 모드에서는 `fmOpacity`가 출력에 자동 적용되지 않습니다. 필요하면 직접 적용하세요.

### 2.3 Auto 모드

Auto는 호환 가능한 변형들을 순서대로 시도하고(Shadertoy/direct) 먼저 컴파일되는 것을 사용합니다.

## 3. 소스 전처리 및 내장 매크로

컴파일 전에 FancyMenu는 소스를 정규화합니다:

- UTF-8 BOM 제거
- CRLF/CR을 LF로 변환
- `#version ...` 줄 제거
- `precision ...;` 줄 제거

런타임이 주입하는 프리앰블에는 다음이 포함됩니다:

- `#version 150`
- `in vec2 fmUv_FancyMenu` (`[0,1]` 범위의 전체 화면 UV, 좌하단 원점)
- `#define iGlobalTime iTime`
- `#define texture2D texture`
- `#define textureCube texture`

참고:

- 소스에 이미 알려진 uniform 이름(예: `iTime`)이 선언되어 있으면 FancyMenu는 중복 선언을 주입하지 않습니다.
- FancyMenu는 런타임에서 여전히 해당 이름으로 값을 업로드하려고 시도합니다.
- `textureCube`는 여기서 별칭 매크로일 뿐이며; `iChannel0..3`는 `sampler2D` uniform입니다.

## 4. 패스 시스템 (Image + Buffer A-D)

FancyMenu에는 5개의 패스 슬롯이 있습니다:

- `Buffer A`
- `Buffer B`
- `Buffer C`
- `Buffer D`
- `Image` (최종 화면 패스)

동작:

- 버퍼 패스는 소스가 비어 있지 않을 때만 실행됩니다.
- 출력 렌더링을 위해서는 Image 패스가 존재해야 합니다.
- 버퍼는 부동소수점 텍스처(`GL_RGBA16F`)로 렌더링된 뒤 ping-pong(매 프레임 read/write 교체)됩니다.

### 4.1 패스별 채널 라우팅

각 패스는 `iChannel0..3`에 대한 라우팅을 제공합니다. 각 채널마다 다음 중 하나를 선택할 수 있습니다:

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

- 모든 `iChannel` 라우팅은 기본적으로 `None`
- 해당 버퍼 소스가 비어 있지 않기 전까지 버퍼 패스는 비활성 상태

중요:

- 같은 버퍼 패스로 라우팅하는 피드백은 이전 프레임 데이터를 읽습니다(ping-pong read texture).
- 라우팅된 소스가 없거나 비활성 상태이면 대체 텍스처가 바인딩되고 `iChannelResolution[n].z`는 `0.0`이 됩니다.

## 5. 좌표 및 영역 의미

셰이더는 영역 사각형에서 실행됩니다:

- 메뉴 배경: 전체 화면 영역
- GLSL 요소: 요소 사각형

좌표 규칙:

- 픽셀 uniform은 영역 로컬 픽셀 기준입니다.
- 셰이더에 전달되는 픽셀 좌표의 Y 원점은 좌하단입니다.
- 마우스 좌표는 클램프되지 않으며, 커서가 영역 밖에 있으면 값이 영역 밖으로 나갈 수 있습니다.

특수 필드:

- `fmAreaOffset`: 화면 픽셀 공간에서 영역의 좌하단 위치
- `fmAreaTopLeft`: 화면 픽셀 공간에서 영역의 좌상단 위치
- `fmAreaSize`: 픽셀 단위 영역 크기

## 6. Uniform API 참조

아래의 모든 uniform은 배경 및 요소 셰이더에서 사용할 수 있습니다.

## 6.1 Shadertoy 호환 uniform

| Uniform | Type | Meaning |
|---|---|---|
| `iResolution` | `vec3` | `(areaWidthPx, areaHeightPx, 1.0)` |
| `iTime` | `float` | 누적된 셰이더 시간(초) |
| `iTimeDelta` | `float` | 마지막 렌더의 시간 차이, freeze/time scale의 영향을 받음 |
| `iFrameRate` | `float` | Minecraft FPS 대체 런타임 FPS |
| `iFrame` | `int` | 런타임별 프레임 카운터 |
| `iMouse` | `vec4` | 아래 세부 설명 참조 |
| `iDate` | `vec4` | `(year, month, day, secondsOfDayWithFraction)` |
| `iSampleRate` | `float` | 상수 `44100.0` |
| `iChannelTime[4]` | `float[4]` | 현재 모두 `iTime`으로 설정됨 |
| `iChannelResolution[4]` | `vec3[4]` | 채널별 `(width, height, validFlag)` |
| `iChannel0..3` | `sampler2D` | 라우팅된 텍스처 입력 |

### `iMouse` 세부 사항

`iMouse = vec4(x, y, z, w)`

- `x`, `y`: 현재 영역 로컬 마우스 픽셀 위치, 또는 토글이 활성화된 경우 유지/고정 동작
- `z`, `w`: 왼쪽 클릭 원점
  - 왼쪽 마우스 버튼을 누르고 있는 동안 양수
  - 놓은 뒤 음수

토글로 제어되는 동작:

- `Update iMouse Position Only While Holding LMB = Off`:
  - `iMouse.xy`가 계속 업데이트됨
- `... = On`:
  - `iMouse.xy`는 LMB가 눌려 있는 동안에만 업데이트되고, 이후 마지막 유지 위치에 머뭄

기본값:

- `Off`(연속 업데이트)

## 6.2 FancyMenu 전용 uniform

| Uniform | Type | Meaning |
|---|---|---|
| `fmAreaOffset` | `vec2` | 화면 공간에서 영역의 좌하단 픽셀 오프셋 |
| `fmAreaSize` | `vec2` | 픽셀 단위 영역 크기 |
| `fmAreaPosition` | `vec2` | `fmAreaOffset`와 동일 |
| `fmAreaTopLeft` | `vec2` | 화면 공간에서 영역의 좌상단 픽셀 오프셋 |
| `fmScreenSize` | `vec2` | 전체 화면 크기(픽셀) |
| `fmGuiScale` | `float` | 현재 GUI 배율 |
| `fmMouse` | `vec4` | `(localPxX, localPxYBottom, localNormX, localNormY)` |
| `fmMouseDelta` | `vec2` | 영역 픽셀 단위 마우스 델타(Y는 셰이더 기준 위쪽으로 반전됨) |
| `fmMouseButtons` | `ivec4` | 버튼 `0..3`의 눌림 상태 |
| `fmMouseClickCount` | `ivec4` | 버튼 `0..3`의 누적 클릭 수 |
| `fmMouseReleaseCount` | `ivec4` | 버튼 `0..3`의 누적 릴리스 수 |
| `fmMouseScroll` | `vec2` | 이 런타임의 이전 렌더 이후 스크롤 델타 |
| `fmMouseScrollTotal` | `vec2` | 누적 스크롤 총합 |
| `fmKeyEvent` | `ivec4` | `(lastKeyCode, lastScanCode, lastModifiers, lastAction)` |
| `fmKeyEventCount` | `int` | 누적 키 이벤트 카운터 |
| `fmCharEvent` | `ivec4` | `(lastCodePoint, lastModifiers, 0, 0)` |
| `fmCharEventCount` | `int` | 누적 문자 입력 이벤트 카운터 |
| `fmDateParts` | `ivec4` | `(year, month, day, dayOfWeekIso1To7)` |
| `fmTimeParts` | `ivec4` | `(hour, minute, second, millisecondPart0To999)` |
| `fmDayOfYear` | `int` | 1년 중 일수 |
| `fmWeekOfYear` | `int` | ISO 연중 주차 |
| `fmUnixTimeSeconds` | `int` | Unix epoch 초 |
| `fmUnixTimeMilliseconds` | `int` | 현재 시간의 밀리초 부분(`0..999`) |
| `fmPartialTick` | `float` | 현재 partial tick |
| `fmGameDeltaTicks` | `float` | Minecraft 게임 delta ticks |
| `fmRealtimeDeltaTicks` | `float` | Minecraft 실시간 delta ticks |
| `fmInWorld` | `int` | 월드 안에 있으면 `1`, 아니면 `0` |
| `fmIsPaused` | `int` | 일시정지 상태면 `1`, 아니면 `0` |
| `fmOpacity` | `float` | 실제 불투명도 배수(`0..1`) |
| `fmVariableCount` | `int` | 현재 FancyMenu 변수 개수 |

키 동작 값(`fmKeyEvent.w`):

- `0` = release
- `1` = press
- `2` = repeat

## 6.3 FancyMenu 변수 Uniform API

FancyMenu 변수는 값이 변경되어도 셰이더 재컴파일 없이 런타임 uniform으로 직접 노출됩니다(배경, 요소, 장식 오버레이 셰이더 모두 해당).

### 이름 규칙

각 변수 `<name>`에 대해 FancyMenu는 다음을 노출합니다:

- `fmVarFloat_<name>`
- `fmVarInt_<name>`
- `fmVarBool_<name>`
- `fmVarVec2_<name>`
- `fmVarVec3_<name>`
- `fmVarVec4_<name>`
- `fmVarExists_<name>` (`1` = 변수 존재, `0` = 없음/삭제됨)

`<name>`에 대한 uniform 접미사 정리 규칙:

- 허용 문자: `[A-Za-z0-9_]`
- 그 외 문자는 모두 `_`로 변환
- 첫 글자가 숫자면 앞에 `_`를 추가

예시:

- 변수 `player_hp` -> 접미사 `player_hp`
- 변수 `player-hp` -> 접미사 `player_hp`
- 변수 `2nd_phase` -> 접미사 `_2nd_phase`

중요:

- 이러한 동적 변수 uniform은 셰이더 소스에 **자동 선언되지 않습니다**(사용하는 항목은 직접 선언해야 함)
- 같은 접미사로 정리되는 변수명은 같은 GLSL uniform 이름에 매핑되므로 피하세요

### 값 변환

변수 텍스트 값 `v`가 주어지면:

- `fmVarFloat_*`: 파싱된 float(`0.0` 대체)
- `fmVarInt_*`: 파싱된 int(`0` 대체)
- `fmVarBool_*`: 불리언/int 해석(`true/yes/on/enabled` => `1`, `false/no/off/disabled` => `0`, 그 외 숫자 비영(0이 아님) => `1`)
- 벡터 파싱은 다음 구분자를 허용합니다: 공백, `,`, `;`, `|`
  - `fmVarVec2_*`: 처음 2개 파싱된 구성요소
  - `fmVarVec3_*`: 처음 3개 파싱된 구성요소
  - `fmVarVec4_*`: 처음 4개 파싱된 구성요소
  - 구성요소가 부족하면 마지막으로 파싱된 구성요소를 누락된 칸에 반복 사용
  - 숫자 구성요소가 하나도 없으면 모든 벡터 구성요소는 스칼라 대체값을 사용

변수가 삭제되면:

- `fmVarExists_*`는 `0`이 됨
- 대응하는 모든 `fmVar*_*` 값은 `0`으로 초기화됨

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

FancyMenu는 입력을 전역적으로 추적하고 매 렌더마다 스냅샷을 만듭니다:

- 마우스 이동/드래그
- 마우스 누름/놓음
- 스크롤
- 키 누름/놓음/반복
- 문자 입력

마우스 안정성:

- 런타임은 버튼이 눌린 채로 고정되는 상태를 방지하기 위해 매 프레임 GLFW 폴링과 버튼 상태를 대조합니다.

`Pass Input Events To Shader`가 비활성화되어 있으면:

- 입력 uniform은 매 프레임 중립값으로 초기화됩니다
- 셰이더에서 보이는 데이터의 카운터와 이벤트가 0으로 초기화됩니다

## 8. 텍스처 입력 세부 사항

리소스 채널(`iChannel# Resource`)은 2D 텍스처를 기대합니다.

채널별 텍스처 상태:

- 유효한 리소스: 바인딩된 텍스처, 실제 width/height, `iChannelResolution[n].z = 1.0`
- 없음/비활성/None: 대체 텍스처, `iChannelResolution[n].xyz = (0,0,0)`

버퍼 텍스처:

- 내부 포맷: `RGBA16F`(부동소수점)
- 필터링: linear
- wrap: clamp-to-edge

이 방식은 `[0,1]` 밖의 값을 포함한 멀티패스 데이터에 적합합니다.

## 9. 렌더링 및 블렌딩 참고 사항

- 버퍼 패스는 블렌딩 없이 오프스크린으로 렌더링됩니다.
- 최종 Image 패스는 합성을 위해 `Enable Blending` 설정을 사용합니다.
- Shadertoy 래퍼는 `fmOpacity`를 알파에 자동 적용합니다.
- Direct 셰이더는 필요 시 `fmOpacity`를 직접 적용해야 합니다.

## 10. 실용 템플릿

## 10.1 최소 Shadertoy 스타일 셰이더

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord) {
    vec2 uv = fragCoord / iResolution.xy;
    vec3 col = vec3(uv, 0.5 + 0.5 * sin(iTime));
    fragColor = vec4(col, 1.0);
}
```

## 10.2 최소 Direct fragment 셰이더

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

### Buffer A source

Route: `Buffer A iChannel0 Input -> Buffer A`

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord) {
    vec2 uv = fragCoord / iResolution.xy;
    vec4 prev = texture(iChannel0, uv);
    vec4 seed = vec4(uv, 0.0, 1.0);
    fragColor = mix(prev, seed, 0.02);
}
```

### Image source

Route: `Image iChannel0 Input -> Buffer A`

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord) {
    vec2 uv = fragCoord / iResolution.xy;
    fragColor = texture(iChannel0, uv);
}
```

## 11. 문제 해결 체크리스트

- 출력이 없음:
  - Image source가 비어 있지 않은지 확인
  - 컴파일 모드가 진입점(`mainImage` vs `main`)과 일치하는지 확인
- 보라색/유효하지 않은 텍스처:
  - 리소스 바인딩과 채널 라우팅을 확인
  - `iChannelResolution[n].z`를 확인(`0.0`이면 유효하지 않음/사용 불가)
- Direct 셰이더에서 좌표가 잘못됨:
  - 로컬 영역 좌표에는 `gl_FragCoord.xy - fmAreaOffset`를 사용
- 드래그 동작이 이상함:
  - `Update iMouse Position Only While Holding LMB` 토글을 사용
- Direct 셰이더에서 불투명도가 적용되지 않음:
  - 알파에 `fmOpacity`를 직접 곱하기
