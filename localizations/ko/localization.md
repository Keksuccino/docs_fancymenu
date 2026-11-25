---
title: 레이아웃 현지화
description: 텍스트와 기타 레이아웃 콘텐츠를 현지화합니다.
sourceBlobSha: f4883414b07e0c024de7bef4f131b878ca4f5f37
---

# 레이아웃 현지화

번역 가능한 텍스트에는 [**텍스트 현지화** 플레이스홀더](/placeholders#localize-text)를 사용하세요.

```text
{"placeholder":"local","values":{"key":"modpack.menu.play"}}
```

FancyMenu는 먼저 Minecraft에서 활성화된 언어 데이터를 확인합니다. 해당 데이터에 키가 없으면 FancyMenu의 사용자 지정 현지화 파일을 확인합니다. 두 곳 모두에 키가 없으면 키 자체가 표시됩니다.

# FancyMenu 사용자 지정 현지화 파일

파일을 다음 경로 아래에 배치하세요.

```text
<game-directory>/config/fancymenu/custom_locals/
```

현지화 파일을 넣을 하위 디렉터리를 만드세요.

```text
custom_locals/
└── my_pack/
    └── text.json
```

현지화 파일은 `custom_locals` 아래의 하위 디렉터리에 하나 이상 배치해야 합니다. `custom_locals` 루트에 직접 배치한 파일은 로드되지 않습니다. 여러 단계의 하위 디렉터리도 지원됩니다.

지원되는 UTF-8 형식:

| 확장자 | 형식 |
|---|---|
| `.json` | JSON 객체. 중첩된 객체는 점으로 구분된 키가 됩니다. |
| `.lang` | `key=value` 형식의 줄 |
| `.properties` | Java properties 구문 |

JSON 예시:

```json
{
  "modpack": {
    "menu": {
      "play": "Play"
    }
  }
}
```

이 예시는 `modpack.menu.play`를 정의합니다.

FancyMenu는 이러한 하위 디렉터리의 지원 파일을 하나의 사용자 지정 현지화 사전으로 통합합니다. 각 키는 하나의 파일에서만 사용하세요. 사용자 지정 현지화 파일은 Minecraft에서 선택한 언어에 따라 전환되지 않습니다. 언어를 자동으로 전환해야 하는 경우 아래의 리소스 팩 방식을 사용하세요.

사용자 지정 현지화 파일을 수정한 후에는 클라이언트를 다시 시작하세요.

# 언어별 텍스트

Minecraft에서 선택한 언어에 따라 자동으로 전환하려면 [리소스 팩](/resources#minecraft-resources-resource-packs)을 통해 일반 Minecraft 언어 파일을 제공하세요.

```text
assets/<namespace>/lang/en_us.json
assets/<namespace>/lang/de_de.json
```

각 언어 파일에서 동일한 키를 사용하고 리소스 팩을 활성화한 다음, [**텍스트 현지화** 플레이스홀더](/placeholders#localize-text)로 해당 키를 불러오세요.

# 이미지와 요소 현지화

`en_us`, `de_de`와 같이 언어 코드에 따라 서로 다른 요소나 레이아웃을 표시하려면 [**게임 언어 여부** 조건](/conditions#is-game-language)을 사용하세요.
