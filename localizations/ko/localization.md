---
title: 레이아웃 현지화
description: 레이아웃 콘텐츠를 현지화하는 방법입니다.
---

# 레이아웃 현지화

FancyMenu를 사용하면 텍스트 콘텐츠는 물론, 전체 요소나 레이아웃까지 현지화할 수 있습니다!

# 텍스트 콘텐츠

FancyMenu에서는 게임에 직접 사용자 지정 현지화를 추가할 수 있습니다.
이후 **텍스트 현지화(Localize Text)** 플레이스홀더를 사용해 현재 게임 언어에 맞게 텍스트를 현지화할 수 있습니다.

## 바닐라 Minecraft 현지화 키 사용하기

사용자 지정 현지화를 만들기 전에, 기존 Minecraft 현지화 키를 사용하는 것이 좋을 수 있습니다. 이렇게 하면 시간을 절약할 수 있고 바닐라 Minecraft 텍스트와의 일관성도 유지할 수 있습니다.

### 바닐라 현지화 키 찾기

Minecraft의 현지화 키를 찾는 가장 쉬운 방법은 게임의 에셋 파일을 온라인에서 찾아보는 것입니다:

1. **MCAsset.cloud 방문:**  
   [https://mcasset.cloud/](https://mcasset.cloud/)로 이동하세요. 이 웹사이트에서는 게임에서 파일을 추출하지 않고도 Minecraft의 에셋을 둘러볼 수 있습니다.

2. **언어 파일로 이동:**  
   - 드롭다운에서 사용 중인 Minecraft 버전을 선택합니다.
   - 다음 경로로 이동합니다: `assets` → `minecraft` → `lang`
   - `en_us.json`을 열어 모든 영어 현지화 항목을 확인합니다.

3. **필요한 키 찾기:**  
   - 브라우저 검색 기능(Ctrl+F 또는 Cmd+F)을 사용해 원하는 텍스트를 찾습니다.
   - 형식은 `"key": "text"`이며, 콜론(`:`) 앞의 따옴표 안 첫 번째 부분이 키입니다.
   - 예를 들어: `"menu.singleplayer": "Singleplayer"`에서 키는 `menu.singleplayer`입니다.

### 모드 현지화 키 사용하기

다른 모드가 설치되어 있다면, 해당 모드의 현지화 키도 사용할 수 있습니다:

1. 사용 가능한 키는 모드 문서를 확인합니다.
2. 오픈 소스라면 모드의 언어 파일을 살펴봅니다.

## 사용자 지정 현지화 파일

현지화 파일은 여러 언어에서 사용할 수 있는 모든 텍스트 콘텐츠를 담는 텍스트 파일입니다. 번역 가능한 각 텍스트에는 고유한 키가 있으며, Minecraft는 이 키를 사용해 현지화 파일에서 올바른 번역 텍스트를 찾습니다.

- **기본 파일 (en_us.json):**  
  영어(미국)입니다. 다른 언어 파일이 선택되지 않았을 때 이 파일이 사용됩니다. 백업 언어 파일 역할을 합니다.

- **다른 언어 파일:**  
  예를 들어, 독일어를 사용하는 플레이어를 위해 `de_de.json`이라는 독일어 파일을 만들 수 있습니다.

### 사용자 지정 현지화 파일 만들기

반드시 `en_us.json` 파일이 필요합니다! 이 파일이 없으면 게임은 문제가 생기거나 지원되지 않는 언어가 설정되었을 때 사용할 대체 언어가 없습니다.

1. **텍스트 편집기 열기:**  
   메모장(Windows), TextEdit(Mac) 또는 간단한 텍스트 편집기를 사용하세요.

2. **JSON 코드 작성하기:**  
   사용자 지정 키로 파일을 만듭니다. 키는 Minecraft가 텍스트를 찾을 때 사용하는 고유한 이름입니다. 예를 들면:
   
   ```json
   {
     "modpack_name.custom.localization.key": "여기에 사용자 지정 텍스트를 입력하세요",
     "modpack_name.another.key": "또 다른 메시지"
   }
   ```

3. **파일 저장하기:**  
   기본 영어 텍스트용으로 파일을 `en_us.json`으로 저장합니다.

이제 독일어처럼 번역된 버전을 추가하고 싶다면, `en_us.json` 파일의 내용을 새 파일로 복사한 뒤 실제 텍스트만 번역하고, 키는 번역하지 마세요! 키는 게임이 텍스트를 계속 찾을 수 있도록 그대로 유지해야 합니다.

독일어의 경우 파일 이름은 `de_de.json`으로 저장하면 됩니다. 다른 언어의 경우, 해당 언어의 올바른 언어 코드는 [이 Minecraft 위키 페이지](https://minecraft.wiki/w/Language)에서 확인하고 그 코드에 맞춰 파일 이름을 지정하세요. 해당 언어의 **"in-game locale code"**를 찾으면 됩니다.

## MC 1.21.4용 Minecraft 리소스 팩 만들기

이제 현지화 파일이 준비되었으니, Minecraft에서 이를 불러올 방법이 필요합니다. 이를 위해 리소스 팩을 사용합니다. 이 팩은 기본적으로 활성화되도록 만들 수 있으며, 모드팩 사용자가 임의로 건드리지 못하도록 숨길 수도 있습니다.

**리소스 팩**은 게임의 외형과 느낌을 바꾸는 파일들을 담은 ZIP 파일입니다.

### 리소스 팩 만드는 단계

1. **새 폴더 만들기:**  
   사용자 지정 현지화 파일을 넣을 `my_custom_pack` 같은 이름의 폴더를 만듭니다.

2. **팩 파일 만들기 (`pack.mcmeta`):**  
   폴더 안에 `pack.mcmeta`라는 파일을 만들고 다음 내용을 넣습니다:
   
   ```json
   {
     "pack": {
       "pack_format": 16,
       "description": "현지화가 포함된 내 사용자 지정 팩"
     }
   }
   ```
   
   *참고: `pack_format` 16은 Minecraft 1.21.4용입니다.*

3. **현지화 파일 추가하기:**  
   리소스 팩 폴더 안에 다음 폴더 구조를 만듭니다:
   
   ```
   my_custom_pack/
   ├── assets/
   │   └── minecraft/
   │       └── lang/
   │           ├── en_us.json
   │           └── de_de.json
   └── pack.mcmeta
   ```
   
   사용자 지정 `en_us.json`(및 `de_de.json` 같은 다른 언어 파일)을 `lang` 폴더에 넣습니다.

4. **리소스 팩을 ZIP으로 압축하기:**  
   폴더가 준비되면 **전체 폴더를 ZIP 파일로 압축**합니다. ZIP 파일 이름은 **my_custom_pack.zip**으로 지정하세요. 이 이름은 이 가이드 전반에서 사용되는 예시 이름입니다.

## 리소스 팩을 어디에 넣어야 하나요

**my_custom_pack.zip** 파일을 **Minecraft Resourcepacks 폴더**에 넣으세요. 이 폴더는 보통 다음 위치에 있습니다:

- **Windows:** `%appdata%\.minecraft\resourcepacks`
- **Mac:** `~/Library/Application Support/minecraft/resourcepacks`
- **Linux:** `~/.minecraft/resourcepacks`

> 모드팩의 경우 `resourcepacks` 폴더는 해당 팩의 인스턴스 디렉터리에 있습니다.
{.is-warning}

## "Resource Pack Overrides"로 팩 자동 로드하기

**Resource Pack Overrides** 모드를 사용하면 리소스 팩을 기본으로 활성화할 수 있습니다.

### 팩 자동 로드 단계

1. **모드 설치하기:**  
   [CurseForge](https://www.curseforge.com/minecraft/mc-mods/resource-pack-overrides) 또는 [Modrinth](https://modrinth.com/mod/resource-pack-overrides)에서 모드를 다운로드해 설치합니다.

2. **설정 파일 찾기:**  
   `.minecraft/config/resourcepackoverrides.json` 파일을 찾습니다.  
   *파일이 없다면 수동으로 생성하세요.*

3. **설정 파일 편집하기:**  
   파일을 열고 파일 이름을 사용해 리소스 팩을 `default_packs` 목록에 추가합니다:
   
   ```json
   {
     "schema_version": 2,
     "default_packs": [
       "file/my_custom_pack.zip"
     ]
   }
   ```
   
   이렇게 하면 게임을 시작할 때 Minecraft가 리소스 팩을 자동으로 불러옵니다.

   **`file/` 접두사를 꼭 추가해야 합니다!**


*참고: 목록에 있는 리소스 팩은 역순으로 적용됩니다. 즉, 목록 맨 위의 팩은 게임의 리소스 팩 메뉴에서 다른 팩들 아래에 표시됩니다.*

## 선택 화면에서 리소스 팩 숨기기

플레이어가 리소스 팩 선택 화면에서 보지 못하도록 리소스 팩을 숨길 수 있습니다.

### 숨기는 방법

1. **설정 파일을 다시 편집하기:**  
   같은 파일 `.minecraft/config/resourcepackoverrides.json`에서 해당 팩에 대한 오버라이드를 추가합니다:
   
   ```json
   {
     "schema_version": 2,
     "default_packs": [
       "file/my_custom_pack.zip"
     ],
     "pack_overrides": {
       "file/my_custom_pack.zip": {
         "hidden": true
       }
     }
   }
   ```
   
   이 설정은 **my_custom_pack.zip**을 선택 화면에서 숨기면서도 자동으로 로드되게 합니다.

## 새 현지화 키를 FancyMenu에서 사용하기

이제 사용자 지정 현지화 파일이 로드되었으므로, FancyMenu 레이아웃에서 새 키를 사용할 수 있습니다.

1. **텍스트 기반 요소 편집하기:**  
   FancyMenu를 열고 Button이나 Text 같은 요소를 선택합니다.

2. **플레이스홀더 버튼 클릭하기:**  
   텍스트 편집기 오른쪽 상단에서 Placeholders 버튼을 찾습니다. (보이지 않는다면 해당 요소가 플레이스홀더를 지원하지 않을 수 있습니다.)

3. **텍스트 현지화 플레이스홀더 삽입하기:**  
   Localize Text 플레이스홀더는 JSON 스니펫 형태로 표시됩니다. 예시는 다음과 같습니다:
   
   ```json
   {"placeholder":"local","values":{"key":"localization.key"}}
   ```
   
   `localization.key`를 사용자 지정 키로 바꾸세요. 예를 들어, 현지화 파일에 있는 키를 사용하려면 다음처럼 변경합니다:
   
   ```json
   {"placeholder":"local","values":{"key":"modpack_name.custom.localization.key"}}
   ```

이제 거의 끝입니다! 텍스트 편집기에서 편집 중이 아닐 때, 플레이스홀더는 실제 현지화된 콘텐츠로 바뀌어 표시됩니다.

플레이스홀더는 항상 현재 게임 언어에 맞게 텍스트 콘텐츠를 현지화한다는 점을 기억하세요.

# 텍스트가 아닌 콘텐츠(이미지 등)

FancyMenu에서는 이미지뿐 아니라 사실상 원하는 모든 요소를 현지화할 수 있습니다.

이를 위해서는 **로딩 요구 사항(loading requirements)**을 사용해야 합니다.
보다 정확히는 **Is Game Language** 요구 사항을 사용합니다.

**Is Game Language** 요구 사항을 사용하면 특정 게임 언어가 설정되었을 때만 요소나 레이아웃을 표시할 수 있습니다. 예를 들어, 일본어가 설정되었을 때 일본어 텍스트가 들어간 이미지 버전과 영어가 설정되었을 때 영어 텍스트가 들어간 이미지 버전을 각각 만들어 이미지도 현지화할 수 있습니다.

요소에 로딩 요구 사항을 설정하려면 요소를 마우스 오른쪽 버튼으로 클릭한 뒤 **Loading Requirements**를 클릭합니다.

전체 레이아웃에 로딩 요구 사항을 설정하려면 레이아웃 편집기 배경을 마우스 오른쪽 버튼으로 클릭한 뒤 **Loading Requirements [Layout-Wide]**를 클릭합니다.
