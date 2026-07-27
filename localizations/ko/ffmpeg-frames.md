---
title: 비디오에서 프레임 가져오기
description: FFmpeg를 사용해 비디오에서 PNG 프레임을 추출합니다.
---

# FFmpeg로 비디오 프레임 추출하기

1. [FFmpeg](https://ffmpeg.org/download.html)를 설치하고 `ffmpeg` 명령을 사용할 수 있는지 확인합니다.
2. 비디오가 들어 있는 디렉터리에서 터미널을 엽니다.
3. 출력 디렉터리를 만듭니다:

   ```bash
   mkdir output_frames
   ```

4. 필요한 프레임에 맞는 명령을 실행합니다. `input.mp4`를 비디오 파일 이름으로 바꾸세요.

## 모든 프레임 추출하기

```bash
ffmpeg -i input.mp4 output_frames/frame_%04d.png
```

## 고정 프레임 속도로 추출하기

이 예제는 초당 10프레임을 생성합니다. 필요에 따라 `10`을 변경하세요.

```bash
ffmpeg -i input.mp4 -vf "fps=10" output_frames/frame_%04d.png
```

## 추출한 프레임 크기 조정하기

이 예제는 모든 프레임의 크기를 `1280×720`으로 조정합니다.

```bash
ffmpeg -i input.mp4 -vf "scale=1280:720" output_frames/frame_%04d.png
```

`output_frames`의 번호가 붙은 PNG 파일들은 [AFMA 또는 클래식 FMA 애니메이션](./fma)을 만드는 데 사용할 수 있습니다. 프레임 수를 줄이고 해상도를 낮추면 파일 크기와 메모리 사용량을 줄일 수 있습니다.
