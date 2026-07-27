---
title: 리소스
description: 'FancyMenu에서 리소스가 작동하는 방식입니다. 리소스 위치, 로컬 리소스 및 웹 리소스를 다룹니다.'
---

# 리소스

리소스 필드는 다음에서 콘텐츠를 불러올 수 있습니다:

- **Minecraft:** Minecraft 또는 리소스 팩이 제공하는 리소스 위치입니다.
- **로컬:** 활성 게임 인스턴스의 파일입니다.
- **웹:** 직접 파일 URL입니다.

대부분의 이미지, 오디오, 비디오, 텍스트 필드는 동일한 리소스 선택기를 사용합니다. 이 선택기에는 Minecraft 및 리소스 팩 콘텐츠를 탐색하는 브라우저가 포함됩니다.

# Minecraft 리소스(리소스 팩)

리소스 위치는 `namespace:path` 형식을 사용합니다. 네임스페이스는 `assets` 바로 아래의 디렉터리이며, 경로는 그 네임스페이스 아래의 모든 것입니다.

예를 들어, `/assets/custom_resources/images/image.png`에 저장된 리소스 팩 이미지를 생각해 보겠습니다.
그 리소스 위치는 `custom_resources:images/image.png`입니다.

> [!NOTE]
> Minecraft의 기본 제공 리소스는 일반적으로 `minecraft` 네임스페이스를 사용합니다.

# 로컬 리소스

로컬 리소스는 `<game-directory>/config/fancymenu/assets/`에 저장합니다. `<game-directory>`는 활성 인스턴스 폴더이며, `.minecraft`와 다를 수 있습니다.

리소스 필드에는 `/config/fancymenu/assets/example.png`와 같은 경로가 표시될 수 있습니다. 이러한 필드에서 앞의 `/`는 여전히 `<game-directory>`를 의미하며, 파일 시스템 루트 경로가 아닙니다.

이 파일들은 config 폴더를 통해 [모드팩에 포함](./modpacks)될 수 있습니다.

FancyMenu의 레이아웃, 리소스, 구성, 생성 상태 경로의 전체 맵은 [데이터 저장 위치](./data-storage-locations)를 참조하세요.

# 웹 리소스

파일의 직접 URL을 사용하세요. 예: `https://example-domain.net/image.png`. 페이지 URL이나 리디렉션 링크는 리소스의 파일명과 확장자로 끝나는 직접 URL보다 느리고 실패할 가능성이 더 높습니다.

# 리소스 소스의 플레이스홀더

선택기 기반 리소스 필드는 로컬 경로, URL, Minecraft 리소스 위치에서 [플레이스홀더](./placeholders)를 사용할 수 있습니다. 소스 필드 옆의 **편집기에서 열기**를 선택해 직접 편집하세요.

> [!WARNING]
> 일반 선택기를 사용하지 않는 리소스 입력은 플레이스홀더나 실시간 소스 업데이트를 지원하지 않을 수 있습니다.
