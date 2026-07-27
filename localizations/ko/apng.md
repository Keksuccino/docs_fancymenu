---
title: APNG
description: FancyMenu 호환 APNG 이미지를 만드는 방법.
---

# 애니메이션 PNG 이미지

> [!NOTE]
> 크거나 복잡한 애니메이션의 경우 [AFMA 파일](./fma)을 사용하는 것이 좋습니다. Watermedia V3와 Watermedia Binaries V3는 사용 가능한 경우 APNG/GIF 디코딩을 가속할 수 있지만, AFMA는 여전히 FancyMenu의 권장 애니메이션 형식입니다.


APNG는 PNG 이미지의 애니메이션 버전으로, GIF와 같은 기능을 완전한 무손실 PNG 품질로 사용할 수 있게 해줍니다!

FancyMenu는 기본적으로 APNG를 지원하지만, 지원되는 APNG의 조건이 조금 까다롭습니다.
**압축되지 않았고** **인터레이스되지 않은** APNG여야 합니다.

# APNG 애니메이션 만들기

특히 압축과 인터레이스를 끄는 옵션이 있는 좋은 APNG 편집기를 찾는 것이 생각보다 어렵다는 걸 알게 될 것입니다.

편집기로는 [ScreenToGif](https://www.screentogif.com/)을 추천합니다. 원래는 화면의 GIF와 APNG를 녹화하는 도구지만, 녹화 과정을 건너뛰고 바로 편집기에 불러와 일반 APNG를 만드는 데도 아주 좋습니다!

## 편집기 열기

[ScreenToGif](https://www.screentogif.com/)을 열면 가장 먼저 이 화면이 보입니다. 여기서 **Editor**를 클릭하세요.

![screentogif_2](https://github.com/Keksuccino/FancyMenu/assets/35544624/a8d34313-b841-4fb6-bf3a-ff02c39792cb)

## 프레임 불러오기

이제 PNG 프레임이 필요합니다. 편집기에 끌어다 놓으세요.

![screentogif_dragndrop](https://github.com/Keksuccino/FancyMenu/assets/35544624/ba4ad4a5-484e-46f1-8efd-90ba764462d8)

## 프레임 지연 시간

프레임 사이의 지연 시간을 설정하려면, 편집할 프레임을 선택한 뒤 **Edit** 탭으로 이동하여 **Delay (Duration)** 섹션에서 **Override**를 클릭하세요.

![screentogif_delay](https://github.com/Keksuccino/FancyMenu/assets/35544624/a5d93139-3192-4090-b243-e5c0fe299963)

## 반복 재생

반복 재생 방식은 **Save As** 메뉴에서 설정할 수 있습니다. 이 메뉴를 여는 방법은 다음 단계에서 확인하세요.

## APNG 내보내기

이제 다시 **File** 탭으로 이동해 **Save As**를 클릭하면 됩니다.

저장 메뉴에서 다음을 확인하세요:
- 파일 형식을 **APNG**로 설정하기 (첫 번째 설정이며, 메뉴 맨 위로 스크롤해야 할 수도 있습니다)
- **Detect Unchanged Pixels** 비활성화하기

> [!NOTE]
> 이 메뉴에서 **반복 재생 방식**도 설정할 수 있습니다! **Looped Apng**를 비활성화하면 APNG가 전혀 반복 재생되지 않으며, 활성화하면 반복 횟수를 지정하거나 무한 반복으로 설정할 수 있습니다.

![screentogif_save](https://github.com/Keksuccino/FancyMenu/assets/35544624/954353da-45ed-4df8-9f06-c78a0a469fc8)

## FancyMenu에서 APNG 사용하기

이제 APNG 파일을 `<game-directory>/config/fancymenu/assets/`에 복사하세요. 그러면 이미지를 허용하는 거의 모든 곳에서 사용할 수 있습니다.

> [!WARNING]
> APNG 파일 이름이 반드시 `.apng`로 끝나야 한다는 점이 **정말 중요합니다**!
> 파일 이름이 `.apng`로 끝나지 않으면 FancyMenu가 해당 이미지를 APNG로 인식할 수 없습니다.

![screentogif_use_apng](https://github.com/Keksuccino/FancyMenu/assets/35544624/2322da62-4013-451e-9a8b-3df0bf92df54)
