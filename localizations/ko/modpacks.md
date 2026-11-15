---
title: 모드팩
description: 모드팩에 레이아웃을 포함하는 방법입니다.
sourceBlobSha: deb3c58e9536e0fe085820a2b9e463f5faaa7819
---

# 모드팩에서 FancyMenu 사용하기

모드팩에 FancyMenu 설정을 포함하는 방법은 매우 간단하며, 몇 가지 단계만 거치면 됩니다.

> [!CAUTION]
> FancyMenu 설정은 작업을 실행할 수 있습니다. 신뢰할 수 있는 출처의 설정만 가져오세요.

> [!WARNING]
> 이 페이지는 **FancyMenu v3 이상에서 완전히 새로 만들어진** FancyMenu 설정만을 위한 것입니다. 따라서 레거시 설정(v2에서 만들어져 v3으로 변환된 설정)을 사용한다면 일부 단계가 다를 수 있습니다.

# 모드팩에 설정 가져오기

설정을 만든 인스턴스에서 모드팩 인스턴스로 설정을 옮기는 가장 쉬운 방법은 [프로필](./profiles)을 사용하는 것입니다.

1. 설정이 있는 인스턴스에서 **메뉴 바 -> 사용자 지정 -> 프로필**을 열고, 설정을 선택한 다음 [내보내기](./profiles#exporting)를 사용해 `.fmp` 파일로 내보냅니다.
2. 모드팩 인스턴스에서 프로필 창을 열고 `.fmp` 파일을 [가져옵니다](./profiles#importing). 예를 들어 파일을 창으로 끌어다 놓으면 됩니다.
3. 가져온 프로필을 선택하고 **프로필 불러오기**를 클릭합니다.

모드팩 인스턴스에 기존에 있던 FancyMenu 설정은 사라지지 않습니다. 해당 설정은 별도의 프로필로 계속 사용할 수 있으므로 언제든지 다시 전환할 수 있습니다.

# 모드팩에 설정 포함하기

불러온 프로필은 `<game-directory>/config/fancymenu/`의 내용이므로, 다른 모드의 설정 파일과 마찬가지로 모드팩의 `config` 폴더에 포함됩니다.

인스턴스의 다른 모든 프로필은 `<game-directory>/config/fancymenu/profiles/`에 저장됩니다. 모드팩을 내보내기 전에 플레이어에게 제공하지 않을 프로필을 삭제하거나, 모드팩 내보내기에서 `profiles` 폴더를 제외하세요.

> [!CAUTION]
> FancyMenu v2에서 만들어진 오래된 레거시 설정은 v3으로 변환했더라도 레이아웃 에셋을 FancyMenu의 `<game-directory>/config/fancymenu/assets/` 폴더 외부에 저장할 수 있었습니다. 프로필에는 FancyMenu의 config 폴더만 포함되므로, 이 경우 모든 에셋도 모드팩에 포함해야 합니다.

## 인스턴스 폴더 찾기

인스턴스 폴더는 특정 Minecraft 설정의 모든 파일이 저장되는 컴퓨터의 기본 폴더입니다. CurseForge 및 Modrinth와 같은 런처에서는 이를 "인스턴스" 또는 "프로필"이라고 부릅니다(FancyMenu의 프로필과 혼동하지 마세요).

### CurseForge 앱을 사용하는 경우

1. CurseForge를 엽니다.
2. 목록에서 Minecraft 프로필/인스턴스를 찾아 엽니다.
3. 점 3개 아이콘을 클릭합니다.
4. "폴더 열기"를 선택합니다. 그러면 해당 Minecraft 인스턴스의 기본 폴더가 열립니다.

<img width="630" alt="Screenshot_1" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/curseforge_launcher_instance.png">

### Modrinth 앱을 사용하는 경우

1. Modrinth 앱을 엽니다.
2. 목록에서 Minecraft 프로필/인스턴스를 찾아 엽니다.
3. 점 3개 아이콘을 클릭합니다.
4. "폴더 열기"를 선택합니다. 그러면 해당 Minecraft 인스턴스의 기본 폴더가 열립니다.

<img width="630" alt="Screenshot_1" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/modrinth_launcher_instance.png">

### 다른 런처를 사용하는 경우

사용 중인 Minecraft 설정에서 "폴더 열기", "인스턴스 폴더 열기" 또는 "파일 보기"와 비슷한 옵션을 찾아보세요.

# 메뉴 바 및 단축키 비활성화

모드팩에서 FancyMenu의 메뉴 바가 계속 표시되기를 원하지 않을 것이므로 이를 비활성화해야 합니다. 하지만 사용자가 단축키를 눌러 메뉴 바를 다시 표시할 수 있으므로, 조금 더 *강력한* 방법을 사용해 보겠습니다.

`<game-directory>/config/fancymenu/options.txt`로 이동해 텍스트 편집기로 파일을 엽니다.

이제 `modpack_mode`를 `true`로 설정하고 파일을 저장합니다.
이렇게 하면 모든 오버레이와 단축키가 완전히 비활성화됩니다.

레이아웃을 다시 편집하려면 이 설정을 `false`로 되돌리세요.

# 시작 화면 비활성화

대부분의 경우 이 작업은 필요하지 않지만, 아직 시작 화면(문서를 읽으라는 안내가 표시되는 화면)을 닫지 않았다면 `<game-directory>/config/fancymenu/options.txt`에서 `show_welcome_screen`을 `false`로 설정하세요.

이 화면은 한 번만 표시되며 **문서 열기** 버튼을 클릭하면 자동으로 비활성화됩니다. 따라서 대부분의 경우 이 작업을 수동으로 수행할 필요는 없습니다.

<br>
<img width="630" alt="Screenshot_1" src="https://github.com/user-attachments/assets/4383b39f-f55a-4eb8-8142-34a425474bb3">
