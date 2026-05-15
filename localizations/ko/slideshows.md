---
title: 슬라이드쇼
description: 슬라이드쇼를 만들고 사용하는 방법.
---

# 슬라이드쇼

FancyMenu를 사용하면 슬라이드쇼를 추가하고, 메뉴 안이나 메뉴 배경으로 표시할 수 있습니다.

> **중요**: Windows를 사용 중이라면 [파일 확장자 표시](https://vtcri.kayako.com/article/296-view-file-extensions-windows-10)를 켜는 것을 잊지 마세요. 그렇지 않으면 나중에 파일 이름의 중요한 부분을 볼 수 없습니다!
{.is-warning}

# 슬라이드쇼 만들기

모든 슬라이드쇼는 `/config/fancymenu/slideshows/`에 있는 slideshows 디렉터리 **안**에 각각 별도의 폴더로 있어야 합니다.

![1](https://user-images.githubusercontent.com/35544624/105209961-b823e600-5b4a-11eb-8ed2-1016d3b05815.png)

시스템이 슬라이드쇼를 슬라이드쇼로 인식하려면 슬라이드쇼 폴더 안에 properties 파일이 있어야 합니다. 예를 들어 슬라이드쇼 폴더 이름을 `myslideshow`로 지었다면, properties 파일은 `/config/fancymenu/slideshows/myslideshow/properties.txt`에 있어야 합니다.

**이 파일의 이름은 항상 `properties.txt`여야 합니다!**
지금은 **빈** properties 파일만 만들고 다음 단계로 넘어가세요.

![2](https://user-images.githubusercontent.com/35544624/105210016-cbcf4c80-5b4a-11eb-84ad-9aa735340287.png)

## 이미지 추가하기

슬라이드쇼에는 이미지가 필요하므로(당연하죠), 몇 장 추가해 봅시다!

> 슬라이드쇼 이미지는 반드시 **PNG** 파일이어야 합니다! JPEG, GIF, APNG 또는 FMA는 사용할 수 없습니다!
{.is-danger}

슬라이드쇼의 모든 이미지는 슬라이드쇼 폴더(`위 예시의 `myslideshow`) **안**에 있는 추가 폴더로 들어갑니다.
이 폴더의 이름은 `images`여야 합니다.

![3](https://user-images.githubusercontent.com/35544624/105210833-d9d19d00-5b4b-11eb-8ae7-528ad156e27a.png)

이제 슬라이드쇼 이미지들을 `images` 폴더에 넣으세요.
이미지들은 알파벳 순서로 정렬되며(숫자도 반영됨), 따라서 `image_1.png`, `image_2.png` 같은 이름으로 지으면 됩니다.
이 예시에서는 `image_1.png`가 먼저 표시되고, 그다음 `image_2.png`가 표시됩니다.

<br>
<img width="548" alt="Screenshot_2" src="https://github.com/user-attachments/assets/f58ecbfa-affa-4071-8a84-18ed27a6cfee">

## properties 파일에 내용 추가하기

처음에 슬라이드쇼 폴더 안에 빈 `properties.txt` 파일을 만들었습니다.
이제 이 파일에 중요한 내용을 채워 넣어야 합니다.

모든 슬라이드쇼의 properties 파일은 다음과 같아야 합니다.

```
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
`slideshow-meta` 섹션 안의 변수만 변경할 수 있습니다!

### name

슬라이드쇼의 이름, 더 정확히는 식별자입니다.
슬라이드쇼 이름은 **고유**해야 하므로, 같은 이름의 슬라이드쇼를 두 개 만들 수 없습니다!

### width | height

슬라이드쇼의 기준 `width`와 `height`입니다.
FancyMenu가 화면 비율을 계산하는 데 사용합니다.

### x | y

슬라이드쇼의 `x` 및 `y` 위치입니다.
주로 디버깅 용도이므로 둘 다 `0`으로 설정하면 됩니다.

### duration

각 이미지가 다음 이미지로 넘어가기 전까지 표시되는 시간(초)입니다.
소수 값을 지원합니다!

### fadespeed

다음 이미지로 전환될 때의 페이드 애니메이션 속도입니다.
이 값은 속도 배수입니다. 예를 들어 `1.0`은 기본 속도, `2.0`은 속도를 두 배로, `0.5`는 기본보다 절반 속도로 만듭니다.
음수 값은 지원되지 않습니다.

### randomize

슬라이드쇼 이미지를 무작위 순서로 재생할지(`true`), 아니면 그렇지 않을지(`false`)를 지정합니다.

# 슬라이드쇼 사용하기

이제 중요한 단계는 모두 끝났고 슬라이드쇼를 사용할 준비가 되었습니다. 테스트해 봅시다!

새로 만들었거나 수정한 슬라이드쇼를 FancyMenu에 불러오려면 **Customization -> Reload FancyMenu**를 통해 모드를 다시 불러오세요.

이제 **Slideshow** 요소에서 슬라이드쇼를 사용하거나 메뉴 배경으로 사용할 수 있습니다(레이아웃 편집기 배경을 우클릭 -> **Menu Background**).
