---
title: 슬라이드쇼
description: 이미지 슬라이드쇼를 만들고 사용합니다.
---

# 슬라이드쇼

각 슬라이드쇼는 아래 위치에 자체 디렉터리를 가집니다:

```text
<game-directory>/config/fancymenu/slideshows/
```

`<game-directory>`는 활성 런처 인스턴스를 의미하며, 일반적인 `.minecraft` 디렉터리와 다를 수 있습니다.

# 디렉터리 구조

```text
<game-directory>/config/fancymenu/slideshows/
└── myslideshow/
    ├── properties.txt
    ├── overlay.png          # 선택 사항
    └── images/
        ├── image_01.png
        └── image_02.jpg
```

이미지는 `.png` 또는 `.jpg` 확장자를 사용해야 하며, `.jpeg`를 포함한 다른 확장자는 무시됩니다.

`randomize = false`일 때 이미지는 대소문자를 구분하지 않는 알파벳 순서의 파일 이름 순으로 재생됩니다. `image_01.png`, `image_02.png`, `image_10.png`처럼 0으로 채운 이름을 사용하세요.

# `properties.txt`

```text
type = slideshow

slideshow-meta {
  name = cool_slideshow
  width = 1920
  height = 1080
  x = 0
  y = 0
  duration = 5.0
  fadespeed = 12.0
  randomize = false
}
```

| 속성 | 의미 |
|---|---|
| `name` | 필수이며, 대소문자를 구분하는 런타임 식별자입니다. 고유하게 유지하세요. |
| `width`, `height` | GUI 스케일이 적용된 픽셀 기준의 기본 크기와 원본 종횡비입니다. |
| `x`, `y` | 기본 좌측 상단 위치입니다. 일반 요소와 배경은 각각 자체 위치를 사용하므로, 이 값은 `0`으로 유지하세요. |
| `duration` | 전환 시작 사이의 최소 초 단위 시간입니다. 페이드 시간을 포함하며 `0`보다 커야 합니다. |
| `fadespeed` | 페이드 속도 배수입니다. `1.0`이 기본값이며, 값이 클수록 더 빠르게 페이드되고 `0`보다 커야 합니다. |
| `randomize` | 무작위 선택이면 `true`, 파일 이름 순이면 `false`입니다. |

필수 항목은 `name`뿐입니다. 기본값은 `width = 50`, `height = 50`, `x = 0`, `y = 0`, `duration = 10.0`, `fadespeed = 1.0`, `randomize = false`입니다. `type = slideshow`와 `slideshow-meta`는 변경하지 말고, 한 줄에 하나의 `key = value` 형식으로 작성하며 소수점에는 마침표를 사용하세요.

레이아웃은 디렉터리 이름이 아니라 `name`의 값을 선택합니다. 중복된 이름은 거부되지 않으며, 디렉터리 스캔 순서에 따라 어떤 슬라이드쇼가 남을지가 결정됩니다. 슬라이드쇼 디렉터리 내에서는 이름을 고유하게 유지하세요.

무작위 모드에서는 각 전환마다 독립적으로 항목을 선택하며, 여러 이미지가 있을 때는 바로 이전 이미지가 연속으로 다시 나오지 않도록 합니다. 타이밍은 실제 시간을 사용합니다. 페이드가 `duration`보다 오래 걸리면 다음 전환이 지연되며, 숨겨져 있던 슬라이드쇼로 돌아오면 즉시 다음으로 진행될 수 있습니다.

# 슬라이드쇼 사용하기

**사용자 지정 -> FancyMenu 다시 불러오기**를 통해 FancyMenu를 다시 불러오거나, 클라이언트를 재시작하세요. [**슬라이드쇼** 요소](./elements#slideshow)를 사용하거나, 레이아웃 편집기 배경을 우클릭한 다음 [**메뉴 배경**](./menu-backgrounds) -> **슬라이드쇼**를 선택하세요.
