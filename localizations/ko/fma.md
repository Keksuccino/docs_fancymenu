---
title: 애니메이션 (FMA/AFMA)
description: FancyMenu 애니메이션 파일을 만들고 사용하는 방법입니다.
---

# 애니메이션

AFMA 및 FMA 파일은 FancyMenu를 위해 만들어진 애니메이션 텍스처 형식입니다.

# AFMA 파일

**AFMA**(Advanced FancyMenu Animation)는 기존 FMA 파일을 잇는 후속 형식입니다.

AFMA는 ZIP이 아닌 형식을 사용하므로, 기존 FMA보다 파일이 더 작고 메모리 사용량이 낮으며 성능이 더 좋습니다.

대용량이거나 복잡한 애니메이션 텍스처에는 기존 FMA 대신 **AFMA**를 사용하세요.

내장 생성기를 사용해 AFMA 파일을 만들 수 있습니다:

1. FancyMenu의 메뉴 바를 엽니다.
2. **도구 -> AFMA 생성기**로 이동합니다.
3. 생성기에서 프레임을 가져오거나 변환합니다.

> [!IMPORTANT]
> AFMA 파일은 수동으로 압축할 수 없습니다. **도구 -> AFMA 생성기**를 사용하세요.

기존 FMA 파일도 계속 지원되므로, 이미 만든 레이아웃을 즉시 변환할 필요는 없습니다.

# 기존 FMA 파일

## FMA 만들기

기존 FMA 파일은 `.fma` 확장자를 가진 ZIP 아카이브입니다.

### 파일 확장자

아래 파일을 만들거나 이름을 바꾸기 전에 파일 관리자에서 파일 확장자를 표시하도록 설정하세요.

Windows에서는 파일 탐색기를 열고 **보기 -> 파일 확장명**을 활성화하세요.

<br>
<img width="764" alt="Screenshot_9" src="https://gist.github.com/assets/35544624/1f0a0864-1ad8-4f63-be3a-ab18385539e6"> 

### 준비

아카이브 내용물을 담을 `fancymenu_animation`이라는 폴더를 만듭니다.

그 안에 필수 `frames` 디렉터리와 선택 사항인 `intro_frames` 디렉터리를 만듭니다.

같은 폴더에 `metadata.json`을 만듭니다. 파일 확장자가 `.txt`가 아니라 `.json`인지 확인하세요.

이제 폴더에는 `frames/`, `intro_frames/`, `metadata.json`이 있어야 합니다.

<br>
<img width="700" alt="Screenshot_3" src="https://gist.github.com/assets/35544624/e29f6666-ee4a-4d79-b7e2-1b640f40ce78">

### 메타데이터 JSON

텍스트 편집기에서 `metadata.json`을 열고 다음 템플릿을 사용하세요:

```json
{
  "loop_count": 0,
  "frame_time": 41,
  "frame_time_intro": 41,
  "custom_frame_times": {
  },
  "custom_frame_times_intro": {
  }
}
```

필요에 따라 값을 수정하세요.

#### `loop_count`

애니메이션이 몇 번 재생될지 정합니다. `0`을 사용하면 무한 반복합니다. 양수 값을 사용하면 해당 횟수만큼 재생한 뒤 마지막 프레임에서 멈춥니다.

#### `frame_time`

각 일반 프레임이 화면에 유지되는 시간을 밀리초 단위로 설정합니다.

#### `frame_time_intro`

선택 사항인 **인트로** 프레임의 프레임 시간을 설정합니다.

#### `custom_frame_times`

선택적으로 개별 일반 프레임의 지속 시간을 덮어씁니다. 다음 예시는 `0`과 `1` 프레임을 `5000`밀리초 동안 표시하고, 다른 프레임은 `frame_time`을 사용합니다:

```json
{
  "loop_count": 0,
  "frame_time": 41,
  "frame_time_intro": 41,
  "custom_frame_times": {
    "0": 5000,
    "1": 5000
  },
  "custom_frame_times_intro": {
  }
}
```

프레임 인덱스는 0부터 시작합니다. 첫 번째 프레임은 `0`, 두 번째는 `1`입니다.

마지막 항목을 제외한 모든 사용자 지정 프레임 시간 항목 뒤에는 쉼표를 추가하세요.

#### `custom_frame_times_intro`

`custom_frame_times`와 같은 형식을 사용하지만, 선택 사항인 인트로 프레임에 적용됩니다.

`metadata.json`을 저장하세요.

### 프레임

> [!CAUTION]
> 기존 FMA 애니메이션은 200프레임 이하, 1080p 이하로 유지하세요. 길거나 프레임레이트가 높은 콘텐츠에는 [비디오](./video)를 사용하세요.

일반 프레임은 `frames/`에 넣습니다. 파일은 `0.png`, `1.png`, `2.png`처럼 `0.png`부터 순서대로 이름이 지정된 PNG 파일이어야 합니다. 다른 형식과 이름은 지원되지 않습니다.

비디오에서 프레임을 추출하는 방법은 [FFmpeg로 프레임 추출하기](./ffmpeg-frames)를 참조하세요.

<br>
<img width="574" alt="Screenshot_4" src="https://gist.github.com/assets/35544624/eac54695-b57a-4919-8740-4e5c8aad649c">

### 인트로

선택 사항인 인트로 프레임은 `intro_frames/`에 넣습니다. 일반 프레임과 동일한 PNG 이름 규칙을 따르며, 일반 시퀀스가 시작되기 전에 한 번 재생되고 반복되지 않습니다.

### FMA 파일 압축하기

폴더 내용물을 포함한 ZIP 파일을 만듭니다. `metadata.json`, `frames/`, 그리고 선택 사항인 `intro_frames/` 디렉터리는 다른 디렉터리 안이 아니라 ZIP 루트에 있어야 합니다.

Windows에서는 `fancymenu_animation`의 내용을 선택한 뒤, 선택 영역을 마우스 오른쪽 버튼으로 클릭하고 **보내기 -> 압축(zip) 폴더**를 선택하세요.

<br>
<img width="752" alt="Screenshot_6" src="https://gist.github.com/assets/35544624/5b7e7670-5403-410e-943c-283bfe6d585c">

생성된 ZIP 파일을 찾습니다.

<br>
<img width="700" alt="Screenshot_7" src="https://gist.github.com/assets/35544624/987f7989-dff7-43b4-a54c-0898969827f5">

루트 내용은 다음과 같아야 합니다:

<img width="700" alt="Screenshot_8" src="https://gist.github.com/assets/35544624/f1642a39-e14c-47a7-90f6-8a737e8ec75f">

파일 이름을 `fancymenu_animation.fma`로 바꾸어 `.zip` 확장자를 `.fma`로 변경하세요. 기본 파일 이름은 바꿀 수 있지만, `.fma` 확장자는 반드시 필요합니다.

이제 이름이 바뀐 아카이브를 FMA 파일로 사용할 수 있습니다.

# FancyMenu에서 AFMA 및 FMA 파일 사용하기

> [!IMPORTANT]
> AFMA/FMA 파일은 애니메이션 텍스처이므로 [**이미지** 입력](./elements#image)을 통해 추가하세요. 이미지를 허용하는 대부분의 위치는 AFMA 및 FMA 파일도 지원합니다.

[이미지 요소](./elements#image)와 [이미지 메뉴 배경](./menu-backgrounds)을 포함해, 이미지를 받을 수 있는 곳이라면 어디서나 AFMA/FMA 파일을 사용할 수 있습니다.

AFMA/FMA 파일을 `<game-directory>/config/fancymenu/assets/`에 저장하면 FancyMenu의 로컬 리소스 선택기에서 표시됩니다.
