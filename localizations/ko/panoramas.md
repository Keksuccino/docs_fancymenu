---
title: 파노라마
description: 사용자 지정 배경 파노라마를 만들고 사용하는 방법입니다.
---

# 입방형 파노라마

FancyMenu는 메뉴 배경으로 사용할 수 있는 사용자 지정 6이미지 파노라마 큐브를 지원합니다.

이 파노라마는 Minecraft가 타이틀 화면의 배경으로 사용하는 특수한 입방형 파노라마 형식이며, 6개의 이미지(면)로 구성되어 큐브(정확히는 스카이박스)처럼 렌더링됩니다.

> **중요**: Windows를 사용 중이라면 [파일 확장자](https://cdn.discordapp.com/attachments/795308330746511390/801561308012347482/unknown.png)를 켜는 것을 잊지 마세요. 그렇지 않으면 나중에 파일 이름의 중요한 부분을 볼 수 없습니다!
{.is-warning}

# 파노라마 만들기

Minecraft가 배경 파노라마를 어떻게 처리하는지, 그리고 이를 어떻게 만드는지 잘 모르겠다면 [이 영상](https://www.youtube.com/watch?v=F7jMd3zsjZQ&t)을 확인해 보세요.
Minecraft의 파노라마가 어떻게 작동하는지, 그리고 어떻게 만드는지 아주 잘 이해할 수 있을 것입니다!

영상을 보고 나면 이런 파노라마를 만드는 데 시간이 꽤 걸릴 수 있다는 것을 알게 될 것입니다.
시간을 조금 절약하고 싶다면, 대신 파노라마를 자동으로 만들어 주는 모드를 사용하는 것도 생각해 보세요.
`minecraft panorama mod`로 검색하면 몇 가지를 찾을 수 있지만, 그중 하나는 [Panoramica](https://www.curseforge.com/minecraft/mc-mods/panoramica)입니다(제가 만들었습니다).

# 파노라마 준비하기

파노라마 이미지 6개를 준비했다면, 이제 올바른 위치로 옮겨야 합니다!

FancyMenu의 파노라마 디렉터리는 `.minecraft/config/fancymenu/panoramas`에 있습니다.
이곳은 모드에서 사용하고 싶은 모든 파노라마를 넣는 디렉터리입니다.

## 파노라마 폴더

각 파노라마는 자신만의 폴더를 가집니다.
새 파노라마를 추가하려면 `.minecraft/config/fancymenu/panoramas` 안에 새 폴더를 만들어야 합니다.
이 예시에서는 폴더 이름을 `mypanorama`로 하겠습니다.

![1](https://user-images.githubusercontent.com/35544624/100791916-2802d380-341a-11eb-8e32-f9913e93a38c.png)

## 폴더 내용

폴더를 만들었다면 이제 내용을 채워야 합니다.

### Properties 파일
모든 파노라마는 작동하려면 properties 파일이 필요합니다.
이 파일의 이름은 항상 `properties.txt`여야 하며, 여기에 몇 가지 중요한 내용이 들어 있어야 합니다.

파노라마 properties 파일의 내용은 항상 다음과 같아야 합니다:
```
type = panorama

panorama-meta {
  name = name_of_your_panorama
  speed = 1.0
  fov = 85.0
  angle = 25.0
  start_rotation = 0
}
```
`panorama-meta` 섹션 안의 변수만 변경할 수 있습니다!

#### name
파노라마의 **고유한** 이름이어야 합니다.
같은 이름의 파노라마 두 개를 불러오는 것은 불가능합니다!
나중에 이 이름으로 파노라마를 식별하게 됩니다.

#### speed
파노라마가 회전하는 속도입니다.
이 값은 속도 배수입니다. 예를 들어 `1.0`은 기본 속도, `2.0`은 속도를 두 배로, `0.5`는 절반으로 만듭니다.
음수는 지원되지 않으며, 속도를 늦추려면 소수 값을 사용하세요.

#### fov
시야각입니다.
기본 FOV는 `85.0`입니다.
여기서 너무 크거나 작은 값을 사용하면 파노라마가 깨질 수 있습니다. 원하는 FOV를 찾을 때까지 조금씩 조정해 보세요.

#### angle
파노라마가 보이는 수직 각도입니다.
기본 각도는 `25.0`입니다.

#### start_rotation
파노라마가 시작될 회전 각도(수평)입니다. 값은 0에서 360 사이여야 합니다.

<br>

### 파노라마 이미지 폴더

파노라마 폴더에 필요한 두 번째 필수 요소는 실제 파노라마 이미지를 담는 이미지 폴더입니다.

이 폴더의 이름은 `panorama`여야 합니다.

모든 파노라마 이미지를 여기에 넣되, 위의 [영상](https://www.youtube.com/watch?v=F7jMd3zsjZQ&t)에서 보여 준 것처럼 이름을 올바르게 지정하는 것을 잊지 마세요!

![3](https://user-images.githubusercontent.com/35544624/100791922-29340080-341a-11eb-8174-874a180d0485.png)

> 파노라마 이미지로는 PNG만 지원됩니다!
{.is-warning}

### 파노라마 오버레이

마지막 단계는 **선택 사항**이며, 파노라마 위에 오버레이를 원하지 않는다면 건너뛸 수 있습니다.

파노라마에 비네트나 다른 종류의 오버레이를 추가하고 싶다면, `'overlay.png'`라는 이름의 파일을 추가하면 됩니다.
오버레이도 PNG만 지원되며, 파일 이름은 항상 `'overlay.png'`여야 한다는 점을 기억하세요!

### 다시 한 번 확인하기

이제 `.minecraft/config/fancymenu/panoramas`에 `properties.txt` 파일, `panorama`라는 이름의 또 다른 폴더, 그리고 필요하다면 `overlay.png`라는 오버레이가 들어 있는 폴더가 있어야 합니다.

![2](https://user-images.githubusercontent.com/35544624/100791920-29340080-341a-11eb-8e26-98a7fd2ad7eb.png)

# 파노라마 사용하기

게임을 다시 시작하거나 **Customization -> Reload FancyMenu**를 통해 FancyMenu를 다시 불러오면, 이제 파노라마를 메뉴 배경으로 설정할 수 있어야 합니다. 이를 위해 레이아웃 편집기 배경을 마우스 오른쪽 버튼으로 클릭한 다음 **Menu Background**를 클릭하세요.
