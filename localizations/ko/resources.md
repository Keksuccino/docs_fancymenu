---
title: 리소스
description: 'FancyMenu에서 리소스가 작동하는 방식입니다. 리소스 위치, 로컬 리소스, 웹 리소스를 다룹니다.'
sourceBlobSha: eb783aaa0098ba295b3ebaf941bb4723e4d08970
---

# 리소스

리소스 필드에서는 다음 위치의 콘텐츠를 불러올 수 있습니다.

- **Minecraft:** Minecraft 또는 리소스 팩에서 제공하는 리소스 위치
- **로컬:** 현재 게임 인스턴스에 있는 파일
- **웹:** 파일의 직접 URL

대부분의 이미지, 오디오, 동영상, 텍스트 필드는 동일한 리소스 선택기를 사용합니다. 선택기에는 Minecraft 및 리소스 팩 콘텐츠를 탐색할 수 있는 브라우저가 포함되어 있습니다.

# Minecraft 리소스(리소스 팩)

리소스 위치는 `namespace:path` 형식을 사용합니다. 네임스페이스는 `assets` 바로 아래에 있는 디렉터리이며, 경로는 해당 네임스페이스 아래의 모든 항목을 가리킵니다.

예를 들어, 리소스 팩 이미지가 `/assets/custom_resources/images/image.png`에 있다고 가정해 보겠습니다.
이 이미지의 리소스 위치는 `custom_resources:images/image.png`입니다.

> [!NOTE]
> Minecraft에 기본 포함된 리소스는 일반적으로 `minecraft` 네임스페이스를 사용합니다.

# 로컬 리소스

로컬 리소스는 `<game-directory>/config/fancymenu/assets/`에 저장하세요. `<game-directory>`는 현재 인스턴스 폴더이며, `.minecraft`와 다를 수 있습니다.

리소스 필드에 `/config/fancymenu/assets/example.png`와 같은 경로가 표시될 수 있습니다. 이러한 필드에서 맨 앞의 `/`는 여전히 `<game-directory>`를 의미하며, 파일 시스템의 루트 경로를 뜻하지 않습니다.

이 파일은 모드팩의 config 폴더를 통해 [모드팩에 포함할 수 있습니다](/modpacks).

FancyMenu의 레이아웃, 리소스, 설정 및 생성된 상태 파일 경로 전체를 확인하려면 [데이터 저장 위치](/data-storage-locations)를 참조하세요.

# 웹 리소스

파일의 직접 URL을 사용하세요. 예: `https://example-domain.net/image.png`. 페이지 URL이나 리디렉션 링크는 리소스의 파일 이름과 확장자로 끝나는 직접 URL보다 로딩이 느리고 실패할 가능성도 높습니다.

# 리소스 소스의 플레이스홀더

선택기를 사용하는 리소스 필드에서는 로컬 경로, URL, Minecraft 리소스 위치에 [플레이스홀더](/placeholders)를 사용할 수 있습니다. 소스 필드 옆의 **편집기에서 열기**를 선택하면 필드를 직접 수정할 수 있습니다.

> [!WARNING]
> 일반 선택기를 사용하지 않는 리소스 입력란은 플레이스홀더나 실시간 소스 업데이트를 지원하지 않을 수 있습니다.
