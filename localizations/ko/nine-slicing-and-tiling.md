---
title: 나인 슬라이싱 및 타일링
description: '테두리가 있는 텍스처를 확대하거나, 끊김 없는 텍스처를 반복합니다.'
---

# 나인 슬라이싱과 타일링

나인 슬라이싱은 텍스처의 모서리와 테두리는 유지하면서 가운데 부분만 늘립니다. 타일링은 텍스처를 늘리는 대신 반복합니다.

<img src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/nine_slicing_example.png" alt="나인 슬라이스 영역" style="max-width:500px;height:auto;" />

# 나인 슬라이싱 지원

| 영역 | 지원 대상 |
|---|---|
| 위젯 | [버튼](./elements#button) 및 [슬라이더](./elements#slider) 텍스처; [전역 버튼 및 슬라이더 스타일](./global-customizations#button-visuals) |
| 이미지 및 패널 | [이미지 요소](./elements#image) |
| 진행 바 | [채우기 및 배경 텍스처](./elements#progress-bar) |
| 툴팁 | [사용자 지정 배경 텍스처](./elements#tooltip) |

# 나인 슬라이싱 설정

1. 대상 텍스처를 설정합니다.
2. **나인 슬라이스** 옵션을 활성화합니다.
3. 원본 텍스처의 고정된 가장자리 영역에 맞게 테두리 크기를 설정합니다.
4. 요소의 크기를 조절하고, 모서리나 가장자리가 왜곡되면 테두리 값을 조정합니다.

버튼과 이미지 설정에는 X/Y 테두리 크기를 사용합니다. 진행 바와 툴팁은 필요한 경우 가장자리별로 별도 값을 제공합니다.

# 타일링 지원

반복 텍스처는 다음에 사용할 수 있습니다:

- [이미지 요소](./elements#image)
- [이미지 메뉴 배경](./menu-backgrounds)
- [스크롤 목록의 헤더 및 푸터 텍스처](./customizing-scrollable-screens)

이미지 요소 또는 이미지 배경에서 **텍스처 반복**을 활성화합니다. 스크롤 가능한 화면의 경우, 헤더/푸터 사용자 지정 메뉴에서 반복 옵션을 사용합니다.

끊김 없는 원본 텍스처를 사용하세요. 가장자리가 맞지 않으면 타일 사이에 눈에 띄는 선이 생깁니다.

나인 슬라이싱과 반복은 서로 다른 모드입니다. 대상에 두 옵션이 모두 표시된다면, 의도한 크기 조절 방식에 맞는 옵션을 선택하세요.
