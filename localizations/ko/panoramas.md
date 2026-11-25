---
title: 파노라마
description: 'Minecraft 타이틀 화면에 있는 것처럼, 이미지 6장으로 직접 회전하는 파노라마 배경을 만들어 보세요.'
sourceBlobSha: e1f9ab155301f1b88df58dd8414eeee5714cfba6
---

# 파노라마

파노라마는 Minecraft 타이틀 화면에 있는 것처럼 주변을 천천히 회전하는 배경입니다. 보는 사람을 둘러싸는 정육면체를 이루는 이미지 6장으로 만들어집니다.

직접 만든 파노라마를 레이아웃의 [메뉴 배경](/menu-backgrounds)으로 표시하거나, 모든 메뉴에서 Minecraft 파노라마 대신 사용할 수 있습니다.

<img width="800" alt="해 질 무렵 숲속 공터에 있는 통나무집, 정원, 장작 창고와 닭장을 비추며 천천히 회전하는 파노라마 앞에 표시된 타이틀 화면" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/panoramas_title.gif?raw=true">

> [!TIP]
> 이 페이지의 파노라마는 테스트용이나 직접 만든 모드팩에서 자유롭게 사용할 수 있습니다: [forest_homestead.zip](https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/forest_homestead.zip) (4 MB). 압축을 `config/fancymenu/panoramas/`에 풀고 FancyMenu를 다시 불러오세요.

# 파노라마 만들기

1. 게임 디렉터리의 `config/fancymenu/` 안에 있는 `panoramas` 폴더를 엽니다. **메뉴 바 -> Tools -> Open FancyMenu Directory**를 선택하면 `config/fancymenu/`가 열립니다.
2. 그 안에 `forest_homestead`처럼 파노라마용 폴더를 만듭니다. 폴더 이름은 아무거나 사용해도 됩니다.
3. 폴더 안에 `properties.txt`와 [이미지 6장](#이미지-6장)이 들어 있는 `panorama` 폴더를 넣습니다. `overlay.png`는 선택 사항입니다.
4. **메뉴 바 -> Customization -> Reload FancyMenu**를 선택하거나 `Ctrl + Alt + R`(macOS에서는 `Cmd + Alt + R`)을 누르거나, 게임을 다시 시작해 FancyMenu를 불러옵니다.

```text
config/fancymenu/panoramas/
└── forest_homestead/
    ├── properties.txt
    ├── overlay.png
    └── panorama/
        ├── panorama_0.png
        ├── panorama_1.png
        ├── panorama_2.png
        ├── panorama_3.png
        ├── panorama_4.png
        └── panorama_5.png
```

# 이미지 6장

각 이미지는 정육면체의 한 면입니다.

<img width="796" alt="숲속 집 파노라마의 이미지 6장을 펼친 정육면체 형태로 배치한 그림: 맨 위 이미지는 앞면 이미지 위에, 왼쪽·앞면·오른쪽·뒷면 이미지는 한 줄로, 맨 아래 이미지는 앞면 이미지 아래에 배치됨" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/panoramas_cube.png?raw=true">

| 이미지 | 면 |
|---|---|
| `panorama_0.png` | 앞면 |
| `panorama_1.png` | 오른쪽 면 |
| `panorama_2.png` | 뒷면 |
| `panorama_3.png` | 왼쪽 면 |
| `panorama_4.png` | 윗면 |
| `panorama_5.png` | 아랫면 |

- 네 면은 다음 순서로 주변을 둘러쌉니다. 각 이미지의 오른쪽 가장자리는 다음 이미지의 왼쪽 가장자리와 이어지며, `panorama_3.png`의 오른쪽 가장자리는 `panorama_0.png`의 왼쪽 가장자리와 맞닿습니다.
- 윗면 이미지의 아래쪽 가장자리는 앞면 이미지의 위쪽 가장자리에 맞닿습니다. 아랫면 이미지의 위쪽 가장자리는 앞면 이미지의 아래쪽 가장자리에 맞닿습니다.
- 이미지 6장은 모두 크기가 같은 PNG 파일이어야 합니다. 1024 × 1024처럼 정사각형으로 만드세요.
- FancyMenu는 이미지에 부드럽게 보정 처리를 하지 않으므로 픽셀 아트가 선명하게 유지됩니다.

Minecraft 자체 파노라마와 같은 배치이므로 Minecraft용으로 만든 파노라마도 사용할 수 있습니다.

# properties.txt

```text
type = panorama

panorama-meta {
  name = forest_homestead
  speed = 2.0
  fov = 85.0
  angle = 25.0
  start_rotation = 0
}
```

| 설정 | 기능 |
|---|---|
| `name` | 파노라마를 선택할 때 사용할 이름입니다. 파노라마마다 고유한 이름을 지정하세요. |
| `speed` | 회전 속도입니다. `1.0`은 약 4분에 한 바퀴 회전하고, `2.0`은 그 두 배 속도로 회전합니다. `0`으로 설정하면 회전하지 않습니다. `10.0`을 넘겨도 더 빨라지지 않습니다. |
| `fov` | 화면에 표시되는 파노라마의 범위입니다. 화면 위쪽부터 아래쪽까지의 각도로 나타냅니다. 숫자가 작을수록 확대됩니다. |
| `angle` | 아래를 내려다보는 각도입니다. `0`은 수평선을 정면으로 바라보고, 음수는 위를 바라봅니다. |
| `start_rotation` | 회전을 시작할 방향입니다. `0`부터 `360`까지의 각도로 지정합니다. `0`이면 앞면 이미지가 가운데에 온 상태로 시작합니다. |

`name`만 필수입니다. 생략한 설정에는 `speed = 1.0`, `fov = 85.0`, `angle = 25.0`, `start_rotation = 0`이 적용됩니다. `type = panorama`와 `panorama-meta {` 줄은 그대로 두고, 설정은 한 줄에 하나씩 작성하며 `1.5`처럼 소수점에는 마침표를 사용하세요.

# 오버레이

`properties.txt`와 같은 위치에 `overlay.png`를 넣으면 화면 전체에 맞춰 늘어난 이미지가 파노라마 위에 표시됩니다. 오버레이는 파노라마와 함께 회전하지 않으므로 비네트, 프레임, 색조 효과 등에 적합합니다. 투명한 부분으로는 파노라마가 비쳐 보입니다.

# 파노라마 사용하기

## 메뉴 배경으로 사용하기

<img width="800" alt="레이아웃 편집기에서 Menu Backgrounds, Cubic Panorama를 열고 Show Background를 켠 다음 Choose Panorama에서 forest_homestead를 선택하면 타이틀 화면 버튼 뒤에서 파노라마가 회전함" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/panoramas_background.gif?raw=true">

1. [레이아웃 편집기](/layout-editor)에서 배경을 마우스 오른쪽 버튼으로 클릭하고 **Menu Backgrounds -> Cubic Panorama**를 엽니다.
2. **Show Background**를 클릭해 배경을 켭니다.
3. **Panorama Name**을 클릭하고 파노라마를 선택한 다음 **Done**을 클릭합니다. 오른쪽 미리보기에서 파노라마가 회전하는 모습을 볼 수 있습니다.

**Clear Panorama**를 누르면 파노라마가 제거됩니다. 다른 배경과 함께 사용하려면 [메뉴 배경](/menu-backgrounds)을 참고하세요.

## 모든 메뉴에서 사용하기

**메뉴 바 -> Customization -> Global Customizations -> Custom Menu Background Panorama -> Choose Panorama**를 선택하면 타이틀 화면과 월드에 입장하기 전의 모든 메뉴에서 Minecraft 파노라마 대신 선택한 파노라마가 표시됩니다. [전역 사용자 지정](/global-customizations#menu-backgrounds)을 참고하세요.

## 미리 불러오기

용량이 큰 파노라마는 처음 표시될 때 시간이 조금 걸릴 수 있습니다. 게임 시작 중에 불러오려면 **메뉴 바 -> Customization -> Pre-Load Resources**에서 **Add Cubic Panorama**를 사용해 추가하세요. [리소스 미리 불러오기](/preload-layouts#pre-loading-slideshows--panoramas)를 참고하세요.

# 알아두면 좋은 점

- 파노라마는 오른쪽으로 회전합니다. 앞면 이미지는 왼쪽으로 이동하고 오른쪽 이미지가 화면에 들어옵니다.
- 같은 파노라마를 표시하는 모든 메뉴는 회전 상태를 공유하므로 메뉴 사이를 전환해도 부드럽게 회전이 이어집니다. 파노라마를 표시하는 메뉴가 없으면 회전이 일시 정지됩니다.
- FancyMenu를 다시 불러오면 모든 파노라마가 `start_rotation`에서 다시 시작합니다.
- 파노라마는 현재 불러온 [프로필](/profiles)에 속합니다.
- **Choose Panorama**에 표시되지 않는 파노라마는 불러오기에 실패한 것입니다. `logs/latest.log`에서 `name`이나 이미지 누락 등 실패 원인을 확인할 수 있습니다.
- 보라색과 검은색 체크무늬가 표시된다면 파노라마를 아직 선택하지 않았거나, 이미지 6장의 크기가 서로 다르거나, 레이아웃에서 더 이상 존재하지 않는 파노라마 이름을 사용하고 있는 것입니다.
- 두 파노라마의 `name`이 같으면 둘 중 하나만 표시됩니다.
