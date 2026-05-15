---
title: 모드팩
description: 모드팩에 레이아웃을 포함하는 방법.
---

# 모드팩에서의 FancyMenu

FancyMenu 설정을 모드팩에 포함하는 것은 매우 쉽고, 간단한 단계만 거치면 됩니다.

> 이 페이지는 **FancyMenu v3+**에서 완전히 만든 FancyMenu 설정에만 해당합니다. 따라서 레거시 설정(v2에서 만들고 v3로 변환한 설정)을 사용 중이라면 일부 단계가 다를 수 있습니다.
{.is-warning}

# 모드팩에 FancyMenu 설정 포함하기

가장 먼저 해야 할 일은 FancyMenu가 모든 디자인을 저장하는 데 사용하는 특별한 폴더 하나를 복사하는 것입니다.

## 찾아야 할 항목

1. **"Minecraft 인스턴스" 폴더:** 메뉴를 디자인했던 것과 같은 특정 Minecraft 설정의 모든 파일이 저장된, 컴퓨터의 मुख्य 폴더입니다. CurseForge나 Modrinth 같은 런처에서는 이것을 "인스턴스" 또는 "프로필"이라고 부릅니다.
2. **`config` 폴더:** Minecraft 인스턴스 폴더 안에는 보통 `config`라는 이름의 폴더가 있습니다. 많은 모드가 설정을 저장하는 곳입니다.
3. **`fancymenu` 폴더:** 그 `config` 폴더 안에서 FancyMenu는 `fancymenu`라는 자체 폴더를 만듭니다. 바로 우리가 필요한 핵심 폴더입니다!

## 인스턴스 저장 위치 찾는 방법

### CurseForge App을 사용하는 경우

1. CurseForge를 엽니다.
2. 목록에서 Minecraft 프로필/인스턴스를 찾아 엽니다.
3. 점 3개 버튼을 클릭합니다.
4. "Open Folder"를 선택합니다. 그러면 해당 Minecraft 인스턴스의 मुख्य 폴더가 열립니다.

<img width="630" alt="Screenshot_1" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/curseforge_launcher_instance.png">

### Modrinth App을 사용하는 경우

1. Modrinth App을 엽니다.
2. 목록에서 Minecraft 프로필/인스턴스를 찾아 엽니다.
3. 점 3개 버튼을 클릭합니다.
4. "Open Folder"를 선택합니다. 그러면 해당 Minecraft 인스턴스의 मुख्य 폴더가 열립니다.

<img width="630" alt="Screenshot_1" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/modrinth_launcher_instance.png">

### 다른 런처를 사용하는 경우

사용 중인 Minecraft 설정에 대해 비슷한 "Open Folder", "Open Instance Folder", 또는 "View Files" 옵션이 있는지 확인하세요.

## FancyMenu 설정 복사하기

1. MODPACK 인스턴스의 `config` 폴더로 이동합니다. (설정을 복사해 넣을 대상 인스턴스입니다.)
2. 그 안에 `fancymenu` 폴더가 있으면 삭제합니다.
3. SOURCE 인스턴스의 `config` 폴더를 엽니다. (설정을 가져올 원본 인스턴스입니다.)
4. SOURCE 인스턴스의 `config` 폴더 안에 있는 `fancymenu` 폴더를 MODPACK 인스턴스의 `config` 폴더로 복사합니다.
5. 완료입니다. 이제 모드팩 인스턴스를 다시 시작하면 설정이 로드되는 것을 볼 수 있습니다.

> v2에서 만든 오래된 레거시 설정(심지어 v3로 변환된 경우라도)은 레이아웃 에셋을 FancyMenu의 `/config/fancymenu/assets/` 폴더 밖에 저장할 수 있었습니다. 따라서 이 경우 모드팩에 모든 에셋도 함께 포함되도록 해야 합니다.
{.is-danger}

# 메뉴 바와 핫키 비활성화하기

모드팩에서 FancyMenu의 메뉴 바가 계속 보이는 것은 원하지 않을 것입니다. 그러니 이를 비활성화해야 합니다. 하지만 사람들이 핫키를 눌러 다시 보이게 할 수도 있으니, 조금 더 *강하게* 처리해봅시다.

`/config/fancymenu/options.txt`로 이동하여 텍스트 편집기로 파일을 엽니다.

이제 `modpack_mode`를 `true`로 설정하고 파일을 저장하세요.
그러면 모든 오버레이와 핫키가 완전히 비활성화됩니다.

레이아웃을 다시 편집하려면, 설정 옵션을 다시 `false`로 바꾸면 됩니다.

# 환영 화면 비활성화하기

대부분의 경우 필요하지 않지만, 아직 환영 화면(문서를 읽으라고 안내하는 화면)을 닫지 않았다면 `/config/fancymenu/options.txt`에서 `show_welcome_screen`을 `false`로 설정하세요.

이 화면은 한 번만 표시되며 **Open Documentation** 버튼을 클릭하면 자동으로 비활성화되므로, 보통은 수동으로 이 작업을 할 필요가 없습니다.

<br>
<img width="630" alt="Screenshot_1" src="https://github.com/user-attachments/assets/4383b39f-f55a-4eb8-8142-34a425474bb3">
