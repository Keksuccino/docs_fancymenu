---
title: 비디오에서 프레임 가져오기
description: 비디오 파일에서 프레임을 추출하는 방법입니다.
---

# FFmpeg를 사용해 비디오에서 프레임을 추출하는 방법

*이 페이지는 ChatGPT AI에 의해 일부 생성되었습니다.*

FFmpeg는 비디오와 오디오 파일을 다루는 데 도움이 되는 무료 도구입니다. FFmpeg로 할 수 있는 멋진 일 중 하나는 MP4 같은 비디오 파일에서 사진(프레임)을 추출하는 것입니다. 아래에서 단계별로 방법을 알아보세요.

아래 명령어에서는 MP4를 사용하지만, FFmpeg는 AVI, MOV, MKV, MPEG 같은 다른 비디오 형식도 지원합니다.

# 필요한 것

시작하기 전에 다음을 준비하세요:

1. **FFmpeg 설치**:

   - 공식 [FFmpeg 웹사이트](https://ffmpeg.org/download.html)에서 FFmpeg를 다운로드하세요. 반드시 "full" 빌드를 다운로드해야 합니다.
   - 사용 중인 컴퓨터에 맞는 설치 안내를 따라 설정하세요.

2. **명령줄 접근**:

   - FFmpeg 명령어를 실행하려면 터미널(Linux/macOS) 또는 명령 프롬프트(Windows)를 사용하세요.

3. **비디오 파일**:

    - 사용할 MP4, AVI, MOV, MKV 또는 MPEG 비디오 파일을 준비하세요.

# 시작하기 전에

명령어를 실행하기 전에 다음을 준비하세요:

## 파일 확장자 표시 활성화

  - 비디오 파일 이름을 바꿀 때 `.mp4` 또는 `.avi` 같은 파일 확장자를 볼 수 있어야 합니다.

    - **Windows에서**:

      - 파일 탐색기를 엽니다.
      - 상단의 "보기" 탭을 클릭합니다.
      - "파일 이름 확장명" 확인란을 선택합니다.

    - **macOS에서**:

      - Finder를 엽니다.
      - 메뉴 막대에서 "Finder"를 클릭한 다음 "환경설정"을 선택합니다.
      - "고급" 탭으로 이동한 뒤 "모든 파일 이름 확장자 보기" 옵션을 선택합니다.

## 출력 폴더 만들기

- FFmpeg 실행 파일이 있는 디렉터리에 `output_frames`라는 폴더를 만드세요. 추출한 프레임이 여기에 저장됩니다.

## 비디오 파일 준비하기

- 프레임을 추출할 비디오 파일을 FFmpeg 실행 파일과 같은 디렉터리에 넣으세요.
- 비디오 파일 이름을 확장자 앞의 이름이 `input`이 되도록 바꾸세요(예: `input.mp4`, `input.avi` 등). 이렇게 하면 아래 명령어를 수정 없이 사용할 수 있습니다.

<br>
<img width="579" alt="Screenshot_4" src="https://gist.github.com/user-attachments/assets/1cb4ddf9-a17a-4219-b7d4-aa344adaa87c" />

# FFmpeg 여는 방법

FFmpeg를 사용하려면 먼저 명령줄에서 열어야 합니다. Windows와 macOS에서 단계별로 여는 방법은 다음과 같습니다.

## Windows에서:

1. **명령 프롬프트 열기**:
   - `Windows` 키와 `R` 키를 동시에 눌러 실행 창을 엽니다.
   - `cmd`를 입력하고 Enter를 누릅니다. 그러면 명령 프롬프트가 열립니다.

2. **FFmpeg 폴더로 이동하기**:
   - 컴퓨터에 FFmpeg가 어디 있는지 알려줘야 합니다. `cd` 명령을 사용해 FFmpeg를 저장한 폴더로 이동하세요.
   - 예를 들어, 바탕 화면의 `ffmpeg-2024\bin` 폴더에 FFmpeg가 있다면 다음을 입력합니다:
     ```bash
     cd C:\Users\YourUsername\Desktop\ffmpeg-2024\bin
     ```
     ("YourUsername"은 컴퓨터의 실제 사용자 이름으로 바꾸세요.)

3. **FFmpeg가 작동하는지 확인하기**:
   - FFmpeg가 제대로 작동하는지 확인하려면 다음 명령어를 입력합니다:
     ```bash
     ffmpeg -version
     ```
   - 작동 중이라면 화면에 FFmpeg 정보가 표시됩니다.

## macOS에서:

1. **터미널 열기**:
   - `Command`와 `Space`를 동시에 눌러 Spotlight 검색을 엽니다.
   - `Terminal`을 입력하고 Enter를 눌러 엽니다.

2. **FFmpeg 폴더로 이동하기**:
   - `cd` 명령을 사용해 FFmpeg를 저장한 폴더로 이동하세요.
   - 예를 들어, FFmpeg가 `Downloads` 폴더에 있다면 다음을 입력합니다:
     ```bash
     cd ~/Downloads/ffmpeg-2024/bin
     ```

3. **FFmpeg가 작동하는지 확인하기**:
   - FFmpeg가 준비되었는지 확인하려면 다음 명령어를 입력합니다:
     ```bash
     ./ffmpeg -version
     ```
   - FFmpeg가 작동 중이라면 관련 정보가 화면에 표시됩니다.

# 모든 프레임 저장하기

비디오의 모든 프레임을 저장하려면 다음 명령어를 사용하세요:

```bash
ffmpeg -i input.mp4 output_frames/%d.png
```

## 의미:

- `-i input.mp4`: 입력 비디오 파일입니다. FFmpeg 실행 파일과 같은 디렉터리에 있어야 합니다. `input.mp4`를 올바른 파일 이름과 확장자로 바꾸세요.
- `output_frames/frame_%04d.png`: 프레임이 저장되는 방식입니다:
- `output_frames/`: 모든 프레임을 `output_frames`라는 폴더에 저장합니다.
- `%d.png`: 프레임은 `1.png`, `2.png` 같은 숫자 이름으로 저장되어 순서가 유지됩니다.

# 특정 시간 간격으로 프레임 저장하기

모든 프레임이 필요하지 않다면 1초마다(또는 다른 간격으로) 프레임을 저장할 수 있습니다. 다음 명령어를 사용하세요:

```bash
ffmpeg -i input.mp4 -vf "fps=1" output_frames/%d.png
```

## 의미:

- `-i input.mp4`: 입력 비디오 파일입니다. FFmpeg 실행 파일과 같은 디렉터리에 있어야 합니다. `input.mp4`를 올바른 파일 이름과 확장자로 바꾸세요.
- `-vf "fps=1"`: 1초에 1프레임을 저장합니다. 더 자주 또는 덜 자주 저장하고 싶다면 `1`을 다른 숫자로 바꾸세요(예: `fps=0.5`는 2초마다 1프레임을 저장하고, `fps=2`는 1초에 2프레임을 저장합니다).
- `output_frames/%d.png`: `output_frames`라는 폴더에 `1.png`, `2.png` 같은 이름으로 프레임을 저장합니다.

# 프레임의 크기와 품질 변경하기

저장하는 프레임의 크기와 품질도 조정할 수 있습니다. 방법은 다음과 같습니다:

```bash
ffmpeg -i input.mp4 -vf "scale=1280:720" -q:v 2 output_frames/%d.png
```

## 의미:

- `-i input.mp4`: 입력 비디오 파일입니다. FFmpeg 실행 파일과 같은 디렉터리에 있어야 합니다. `input.mp4`를 올바른 파일 이름과 확장자로 바꾸세요.
- `-vf "scale=1280:720"`: 프레임 크기를 1280x720 픽셀로 변경합니다.
- `-q:v 2`: 이미지 품질을 설정합니다(1이 가장 좋고, 숫자가 높을수록 품질은 낮아집니다).
- `output_frames/%d.png`: `output_frames`라는 폴더에 `1.png`, `2.png` 같은 이름으로 프레임을 저장합니다.

# 프레임 저장 팁

1. **공간 절약하기**:

   - 비디오가 길다면 모든 프레임을 저장하는 대신 일정 간격으로 저장하세요. 특히 FancyMenu에서 FMA 애니메이션 프레임으로 사용할 때 유용합니다.

2. **더 알아보기**:

   - 터미널에서 `ffmpeg -h`를 실행하면 FFmpeg가 할 수 있는 다양한 기능을 확인할 수 있습니다.

<br>
이제 FFmpeg를 사용해 비디오에서 프레임을 저장할 준비가 되었습니다!&#x20;

