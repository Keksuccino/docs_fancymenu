---
title: APNG
description: FancyMenu와 호환되는 APNG 이미지를 만드는 방법입니다.
---

# 애니메이션 PNG 이미지

> 새롭고 크거나 복잡한 애니메이션에는 [AFMA/FMA 파일](/fma)을 사용하는 것이 좋습니다. FancyMenu 3.9.0은 사용 가능한 경우 Watermedia V3 + Watermedia Binaries V3를 사용해 APNG/GIF 디코딩을 더 빠르게 처리할 수 있지만, 그래도 AFMA가 FancyMenu에서 권장되는 애니메이션 형식입니다.
{.is-info}


APNG는 PNG 이미지의 애니메이션 버전으로, GIF와 같은 기능을 유지하면서도 완전한 무손실 PNG 품질을 사용할 수 있게 해줍니다!

FancyMenu에는 기본 APNG 지원이 있지만, 지원되는 APNG에 대해서는 조금 까다롭습니다.
**압축되지 않은** APNG이며 **인터레이스되지 않은** 파일이어야 합니다.

# APNG 애니메이션 만들기

좋은 APNG 편집기를 찾는 것이 얼마나 어려운지 놀랄 수 있습니다. 특히 압축과 인터레이스를 비활성화할 수 있는 옵션이 있는 편집기는 더 그렇습니다.

편집기로는 [ScreenToGif](https://www.screentogif.com/)를 추천합니다. 이 도구는 원래 화면의 GIF와 APNG를 녹화하는 프로그램이지만, 녹화 과정을 건너뛰고 편집기에 직접 불러와서 일반 APNG를 만드는 데도 매우 유용합니다!

## 편집기 열기

[ScreenToGif](https://www.screentogif.com/)을 열고 처음 보게 되는 화면은 아래와 같습니다. 여기서 **Editor**를 클릭하세요.

![screentogif_2](https://github.com/Keksuccino/FancyMenu/assets/35544624/a8d34313-b841-4fb6-bf3a-ff02c39792cb)

## 프레임 불러오기

이제 PNG 프레임이 필요합니다. 편집기에 Drag-&-Drop 하세요.

![screentogif_dragndrop](https://github.com/Keksuccino/FancyMenu/assets/35544624/ba4ad4a5-484e-46f1-8efd-90ba764462d8)

## 프레임 지연 시간

프레임 사이의 지연 시간을 설정하려면, 편집하려는 프레임을 선택한 뒤 **Edit** 탭으로 이동하고 **Delay (Duration)** 섹션에서 **Override**를 클릭하세요.

![screentogif_delay](https://github.com/Keksuccino/FancyMenu/assets/35544624/a5d93139-3192-4090-b243-e5c0fe299963)

## 반복 재생

반복 재생 동작은 **Save As** 메뉴에서 설정할 수 있습니다. 이 메뉴를 여는 방법은 다음 단계에서 확인하세요.

## APNG 내보내기

이제 다시 **File** 탭으로 이동해 **Save As**를 클릭하면 됩니다.

저장 메뉴에서 다음을 확인하세요:
- 파일 형식을 **APNG**로 설정하기 (첫 번째 설정이며, 메뉴 맨 위로 스크롤해야 할 수도 있습니다)
- **Detect Unchanged Pixels** 비활성화하기

> 이 메뉴에서 **반복 재생 동작**도 설정할 수 있습니다! **Looped Apng**를 비활성화하면 APNG가 전혀 반복되지 않으며, 활성화하면 지정 횟수 반복 또는 무한 반복 중에서 선택할 수 있습니다.
{.is-info}

![screentogif_save](https://github.com/Keksuccino/FancyMenu/assets/35544624/954353da-45ed-4df8-9f06-c78a0a469fc8)

## FancyMenu에서 APNG 사용하기

이제 APNG 파일을 `/config/fancymenu/assets/`로 복사하면 됩니다. 그러면 이미지를 허용하는 거의 모든 곳에서 사용할 수 있습니다.

> APNG 파일 이름이 반드시 `.apng`로 끝나야 한다는 점이 **매우 중요합니다**!
> `.apng`로 끝나지 않으면 FancyMenu가 해당 이미지를 APNG로 인식할 수 없습니다.
{.is-warning}

![screentogif_use_apng](https://github.com/Keksuccino/FancyMenu/assets/35544624/2322da62-4013-451e-9a8b-3df0bf92df54)
