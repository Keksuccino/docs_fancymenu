---
title: 플레이어 머리
description: 메뉴에서 플레이어의 머리를 2D 또는 3D 이미지로 표시하는 방법입니다.
---

# 메뉴에서 플레이어 머리 표시하기

Image 요소를 사용해 플레이어의 머리를 2D 또는 3D 이미지로 표시하려면, "Minotar"라는 서드파티 웹 API를 사용할 수 있습니다.

## 2D 이미지

### 1. 이미지 요소 추가

FancyMenu 편집기에서 배경을 마우스 오른쪽 버튼으로 클릭한 다음, "New Element"를 선택하고 "Image"(또는 "Picture")를 선택합니다.

### 2. 웹 소스 설정

Image 요소를 마우스 오른쪽 버튼으로 클릭해 속성을 엽니다. 소스 유형으로 "Web"을 선택합니다.

### 3. 올바른 플레이스홀더로 URL 구성하기

"Source" 필드에는 다음 URL을 입력합니다:
`https://minotar.net/avatar/{"placeholder":"playername"}.png`

FancyMenu는 `{"placeholder":"playername"}`를 사용해 현재 플레이어의 사용자 이름을 URL에 동적으로 삽입합니다. 이를 통해 Image 요소가 Minotar에서 해당 플레이어의 머리를 가져와 표시할 수 있습니다.

## 3D 이미지

이 방법은 2D 버전과 거의 비슷하지만, 여기서는 다른 URL을 사용해야 합니다:

`https://minotar.net/cube/{"placeholder":"playername"}/200.png`

여기서 `200`은 픽셀 크기입니다. 더 작은 버전을 원하면 예를 들어 `100`으로 바꾸고, 더 큰 버전을 원하면 `300` 등으로 바꾸면 됩니다.
