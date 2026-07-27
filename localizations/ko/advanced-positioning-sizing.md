---
title: 고급 위치 지정 및 크기 조정
description: 요소의 고급 위치 지정과 크기 조정을 사용하는 방법입니다.
---
# 고급 위치 지정 및 크기 조정

고급 위치 지정과 크기 조정은 요소의 좌표와 크기를 직접 제어할 수 있게 해줍니다.

> [!WARNING]
> GUI 스케일에 맞춰 조정하려면 먼저 레이아웃 전체의 **자동 스케일링**을 사용해 보세요. 편집기 배경을 마우스 오른쪽 버튼으로 클릭한 뒤 GUI 스케일을 강제로 설정하고, 같은 메뉴에서 **자동 스케일링**을 활성화하세요.


# 고급 위치 지정/크기 조정 모드 전환

요소에 대해 고급 위치 지정 또는 고급 크기 조정을 사용하려면, **마우스 오른쪽 버튼으로 클릭**한 뒤 **고급 위치 지정** 또는 **고급 크기 조정**을 선택하세요.
고급 위치 값이나 크기 값을 설정하면 요소는 자동으로 고급 모드로 전환됩니다.

일반 위치 지정/크기 조정으로 **비활성화**하려면 **모든 위치 지정/크기 값**을 지우세요.

> [!WARNING]
> 요소가 고급 크기 조정/위치 지정 모드에 있는 동안에는 요소 크기 조정 및/또는 이동이 비활성화되거나 제한될 수 있습니다.

# 위치/크기 계산하기

고급 위치 및 크기 값은 [placeholders](./placeholders)를 지원합니다.

이를 통해 [**Calculator**](./placeholders#calculator-calc) 플레이스홀더를 [**Screen Width**](./placeholders#screen-width-guiwidth), [**GUI Scale**](./placeholders#gui-scale-guiscale), [**Element Width**](./placeholders#element-width-elementwidth) 같은 GUI 플레이스홀더와 함께 사용할 수 있습니다.

> [!NOTE]
> 텍스트 편집기 오른쪽 상단의 **Placeholders** 버튼을 클릭하여 플레이스홀더를 추가할 수 있습니다. 이 버튼이 보이지 않는다면, 편집하려는 콘텐츠는 플레이스홀더를 **지원하지 않습니다**.

[**Calculator placeholder**](./placeholders#calculator-calc)를 사용해 값을 계산하려면 예제 식을 원하는 식으로 바꾸세요. 중첩된 플레이스홀더를 사용하면 화면 또는 요소 크기를 제공할 수 있습니다.

이 예시는 `2`를 반환합니다:

`{"placeholder":"calc","values":{"expression":"1 + 1","decimal":"false"}}`

정수 픽셀 단위의 위치 및 크기 계산에는 `decimal` 값을 `false`로 유지하세요.

다음 계산식은 [**Screen Width** 플레이스홀더](./placeholders#screen-width-guiwidth)를 사용해 2로 나눕니다:

`{"placeholder":"calc","values":{"expression":"{"placeholder":"guiwidth"} / 2","decimal":"false"}}`

> [!IMPORTANT]
> **고급 위치 지정**은 요소 앵커를 무시하고 화면의 왼쪽 위 모서리(`X0 Y0`)를 원점으로 사용합니다. **화면 안에 유지**는 계속 적용됩니다.
