---
title: 파노라마
description: 여섯 장의 이미지로 만든 큐빅 파노라마를 생성하고 사용합니다.
---

# 큐빅 파노라마

각 파노라마는 아래 경로에 각자의 디렉터리를 가집니다:

```text
<game-directory>/config/fancymenu/panoramas/
```

`<game-directory>`는 현재 활성화된 런처 인스턴스를 의미하며, 일반적인 `.minecraft` 디렉터리와 다를 수 있습니다.

# 디렉터리 구조

```text
<game-directory>/config/fancymenu/panoramas/
└── mypanorama/
    ├── properties.txt
    ├── overlay.png          # 선택 사항
    └── panorama/
        ├── panorama_0.png
        ├── panorama_1.png
        ├── panorama_2.png
        ├── panorama_3.png
        ├── panorama_4.png
        └── panorama_5.png
```

여섯 개의 면 이미지는 위에 표시된 정확한 이름을 가진 PNG 파일이어야 하며, 여섯 장 모두 크기가 완전히 같아야 합니다. 일부 운영체제에서는 파일 이름의 대소문자가 중요할 수 있습니다.

`properties.txt` 옆에 선택 사항인 `overlay.png`를 추가해 비네트나 다른 전체 파노라마 오버레이를 넣을 수 있습니다.

# `properties.txt`

```text
type = panorama

panorama-meta {
  name = name_of_your_panorama
  speed = 1.0
  fov = 85.0
  angle = 25.0
  start_rotation = 0
}
```

| 속성 | 의미 |
|---|---|
| `name` | 필수, 대소문자를 구분하는 런타임 식별자입니다. 고유하게 유지하세요 |
| `speed` | 회전 속도 배율입니다. `1.0`이 기본값입니다 |
| `fov` | 시야각을 도 단위로 지정합니다 |
| `angle` | 수직 시야 각도를 도 단위로 지정합니다 |
| `start_rotation` | 초기 수평 회전 각도를 도 단위로 지정합니다 |

`name`만 필수입니다. 선택 사항 값이 없으면 예시에 표시된 기본값이 사용됩니다. `type = panorama`와 `panorama-meta`는 변경하지 마세요. 한 줄에 `key = value` 형식으로 작성하고, 소수에는 마침표를 사용하세요.

중복된 이름은 거부되지 않으며, 디렉터리 스캔 순서에 따라 어떤 파노라마가 남을지가 결정됩니다. 파노라마 디렉터리 내에서는 이름을 고유하게 유지하세요. 파노라마와 슬라이드쇼 이름은 서로 별도의 목록을 사용합니다.

# 파노라마 사용하기

**Customization -> Reload FancyMenu**를 통해 FancyMenu를 다시 불러오거나, 클라이언트를 재시작하세요. 그런 다음 레이아웃 편집기 배경을 마우스 오른쪽 버튼으로 클릭하고 [**Menu Backgrounds**](./menu-backgrounds) -> **Cubic Panorama**를 선택합니다.
