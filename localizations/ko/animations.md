---
title: 애니메이션
description: FancyMenu에서 애니메이션 이미지를 사용하고 만드는 방법입니다.
sourceBlobSha: 76227b0d592e15bf10929c35d6a78e1eea6ee85a
---
# 애니메이션

FancyMenu에서는 이미지를 사용할 수 있는 거의 모든 곳에서 애니메이션 이미지를 재생할 수 있습니다. [이미지 요소](/elements#image), [이미지 메뉴 배경](/menu-backgrounds#image), 버튼 및 슬라이더 텍스처, [게임 인트로](/game-intro) 등에서 사용할 수 있습니다.

애니메이션에는 **APNG** 또는 **GIF** 파일을 사용하세요.

- **APNG**(애니메이션 PNG)는 화질이 더 좋습니다. 일반 PNG의 모든 색상을 지원하고 가장자리가 부드러운 투명도도 제대로 표현합니다. 로고, 배경, 투명도가 필요한 모든 이미지에 가장 적합합니다.
- **GIF**는 더 널리 사용되므로 GIF를 만들고 편집할 수 있는 도구가 더 많습니다. 하지만 GIF는 프레임당 색상이 256개뿐이고, 픽셀이 완전히 투명하거나 전혀 투명하지 않습니다.

> [!NOTE]
> FancyMenu 전용 애니메이션 형식인 FMA와 AFMA는 더 이상 사용되지 않습니다. 기존 파일은 계속 작동하지만, 새 애니메이션에는 APNG 또는 GIF를 사용하세요. [FMA 및 AFMA](#fma-and-afma)를 참고하세요.

# 애니메이션 사용하기

1. 파일을 `<game-directory>/config/fancymenu/assets/`에 넣으면 FancyMenu의 파일 선택기에 표시됩니다. 웹 URL과 리소스 팩 파일도 사용할 수 있습니다. [리소스](/resources)를 참고하세요.
2. 이미지 요소의 **이미지 소스**와 같이 다른 이미지와 동일한 방식으로 파일을 선택하세요.

> [!WARNING]
> APNG 파일의 확장자는 `.apng`여야 합니다. 많은 도구가 APNG를 `.png` 확장자로 저장하므로, 파일 이름을 변경해야 합니다. 그렇지 않으면 FancyMenu에서 정지 이미지로 표시됩니다. 웹 URL도 마찬가지로 `.apng`로 끝나야 합니다.

## 애니메이션 재생 방식

- 애니메이션은 파일에 지정된 횟수만큼 재생된 후 마지막 프레임에서 멈춥니다. 파일을 만들 때 반복 횟수를 설정할 수 있습니다.
- 애니메이션은 화면에 표시되는 동안에만 재생됩니다. 다시 표시되면 멈췄던 지점부터 이어서 재생됩니다.
- **화면을 열 때 애니메이션 텍스처 다시 시작**을 사용하면 화면이 열릴 때마다 이미지 요소와 이미지 메뉴 배경의 애니메이션이 처음부터 재생됩니다.
- **마우스를 올릴 때 애니메이션 텍스처 다시 시작**을 사용하면 마우스가 버튼이나 슬라이더 위로 이동할 때마다 해당 텍스처의 애니메이션이 처음부터 재생됩니다.
- [**애니메이션 텍스처 재생 시작**](/listeners#animated-texture-started-playing) 및 [**애니메이션 텍스처 재생 완료**](/listeners#animated-texture-finished-playing) 리스너는 애니메이션이 시작되거나 끝날 때 동작을 실행합니다.

## 성능

FancyMenu는 APNG와 GIF를 재생하는 동안 디코딩하며, 몇 프레임 앞까지만 미리 처리하므로 애니메이션이 길어도 메모리를 거의 사용하지 않습니다.

하지만 프레임 크기가 크거나 프레임 속도가 높으면 성능에 영향을 줄 수 있습니다. 프레임 크기는 화면에 표시되는 크기에 맞추세요. [텍스처 최적화](/optimizing-textures)를 참고하세요. 소리가 포함된 긴 영상에는 [비디오](/video)를 대신 사용하세요.

# 애니메이션 만들기

다음 무료 도구를 사용하면 개별 프레임이나 동영상으로 APNG와 GIF를 만들 수 있습니다.

- [ScreenToGif](https://www.screentogif.com/) (Windows): **Editor**를 클릭하고 PNG 프레임을 끌어다 놓은 다음, 프레임 지연 시간을 설정하고 APNG 또는 GIF로 저장하세요. 저장 메뉴에서 반복 재생 여부를 설정할 수 있습니다.
- [ezgif](https://ezgif.com/) (온라인, 다운로드 불필요): 이미지로 [GIF](https://ezgif.com/maker) 또는 [APNG](https://ezgif.com/apng-maker)를 만들고, 동영상을 [GIF](https://ezgif.com/video-to-gif) 또는 [APNG](https://ezgif.com/video-to-apng)로 변환하거나, [GIF를 APNG로](https://ezgif.com/gif-to-apng) 및 [APNG를 GIF로](https://ezgif.com/apng-to-gif) 변환할 수 있습니다.
- [FFmpeg](https://ffmpeg.org/download.html) (명령줄): 아래 내용을 참고하세요.

## FFmpeg 사용하기

`frame_0001.png`, `frame_0002.png`처럼 번호가 매겨진 PNG 프레임으로 무한 반복되는 APNG를 만듭니다. `-framerate 20`은 초당 20프레임으로 재생합니다.

```bash
ffmpeg -framerate 20 -i frame_%04d.png -plays 0 animation.apng
```

동영상을 APNG로 변환합니다. `fps=20`은 초당 20프레임을 유지하고, `scale=960:-1`은 너비를 960픽셀로 설정합니다.

```bash
ffmpeg -i trailer.mp4 -vf "fps=20,scale=960:-1" -plays 0 trailer.apng
```

동영상을 무한 반복되는 GIF로 변환합니다. `palettegen` 부분에서 동영상에 가장 적합한 256가지 색상을 선택합니다.

```bash
ffmpeg -i trailer.mp4 -vf "fps=15,scale=640:-1:flags=lanczos,split[a][b];[a]palettegen[p];[b][p]paletteuse" -loop 0 trailer.gif
```

GIF를 APNG로 변환합니다.

```bash
ffmpeg -i logo.gif -plays 0 logo.apng
```

# FMA 및 AFMA

FMA와 AFMA는 FancyMenu 전용 애니메이션 형식입니다. 둘 다 더 이상 사용되지 않습니다. 여전히 재생할 수 있지만, 새 애니메이션에는 APNG와 GIF를 사용하는 것이 더 좋습니다.

그래도 AFMA를 만들려면 다음 단계를 따르세요.

1. 프레임을 PNG 파일로 저장해 하나의 폴더에 넣습니다. 프레임은 `frame_1.png`, `frame_2.png`, ..., `frame_10.png`처럼 파일 이름 순서대로 재생됩니다.
2. **메뉴 바 -> 도구 -> AFMA 생성기**를 엽니다.
3. **메인 프레임 디렉터리**에 해당 폴더를 지정합니다. **인트로 프레임 디렉터리**에 있는 프레임은 메인 프레임보다 먼저 한 번 재생됩니다.
4. **메인 프레임 시간(ms)**과 **반복 횟수**를 설정합니다. 반복 횟수를 `0`으로 설정하면 무한 반복됩니다.
5. **출력 AFMA 파일**을 설정하고 **내보내기**를 클릭합니다.
