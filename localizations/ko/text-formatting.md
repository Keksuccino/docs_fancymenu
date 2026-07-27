---
title: 텍스트 서식
description: Markdown과 Minecraft의 서식 코드를 사용해 텍스트를 서식 지정하는 방법입니다.
---

# 텍스트 서식

[텍스트 요소](./elements#text)는 Markdown을 지원합니다. 다른 텍스트 필드에는 Minecraft 서식을 사용하며, 버튼 레이블에는 Minecraft 텍스트 컴포넌트를 사용할 수 있습니다.

# Markdown

FancyMenu의 **텍스트 요소**는 완전한 Markdown 지원을 제공합니다. 즉, 특수 문자를 추가해 텍스트 내용을 서식 지정할 수 있습니다.

예를 들어 텍스트를 굵게 보이게 하려면 굵게 표시할 텍스트 앞뒤에 `**`를 추가합니다. 그러면 `**Some bold text that's very bold.**`는 다음처럼 표시됩니다:
**Some bold text that's very bold.**

FancyMenu는 아래에 문서화된 확장 기능도 지원합니다.

> [!CAUTION]
> Markdown은 **텍스트 요소**에서만 작동합니다. 버튼 레이블 및 다른 텍스트 필드에서는 [Minecraft의 서식 코드](#minecraft-text-formatting)를 사용하세요.

## 글꼴

텍스트 앞에 `%!!<font_name>%`를, 뒤에 `%!!%`를 추가하면 리소스 팩을 통해 로드된 사용자 지정 글꼴로 텍스트를 표시할 수 있습니다.

기본 게임에 포함된 유효한 글꼴은 `uniform`입니다. 따라서 `uniform` 글꼴로 텍스트를 표시하려면 다음과 같이 합니다:
`%!!uniform%this is a custom font%!!%`

이렇게 하면 `this is a custom font`가 `uniform` 글꼴로 표시됩니다.

## 텍스트 색상(HEX)

텍스트 앞에 `%<HEX_color>%`를, 뒤에 `%#%`를 추가하면 특정 HEX 색상으로 텍스트를 표시할 수 있습니다.

초록색의 유효한 HEX 색상은 `#77fc03`이므로, 이 색상으로 텍스트를 표시하려면 다음과 같이 합니다:
`%#77fc03%this text is green!%#%`

이렇게 하면 `this text is green!`이 `#77fc03`(초록색)으로 표시됩니다.

HEX 색상은 반드시 `#`로 시작해야 합니다!

일반적인 HTML 스타일의 색상 이름도 같은 색상 서식 코드에서 지원됩니다:

```
%#red%This text is red!%#%
```

지원되는 이름: `black`, `silver`, `gray`, `grey`, `white`, `maroon`, `red`, `purple`, `fuchsia`, `magenta`, `green`, `lime`, `olive`, `yellow`, `navy`, `blue`, `teal`, `aqua`, `cyan`, `transparent`.

## 텍스트 정렬

특정 정렬 서식 코드로 줄을 시작하고, 그 다음에는 아무것도 쓰지 않은 뒤, 해당 정렬로 표시할 텍스트 줄들을 작성한 다음, 빈 줄에 다시 같은 정렬 코드를 넣어 텍스트 줄을 정렬할 수 있습니다.

모든 텍스트 내용은 기본적으로 **왼쪽 정렬**되므로, 서식 코드는 **가운데 정렬**과 **오른쪽 정렬**만 있습니다.

### 가운데 정렬

텍스트 줄을 가운데 정렬하려면 서식 코드 `^^^`를 사용하세요.

예시:
```
이 텍스트는 가운데 정렬되지 않습니다.

^^^
이 텍스트는 가운데 정렬됩니다.
이 텍스트도 가운데 정렬됩니다.
^^^

이 텍스트는 더 이상 가운데 정렬되지 않습니다.
```

### 오른쪽 정렬

텍스트 줄을 오른쪽 정렬로 표시하려면 서식 코드 `|||`를 사용하세요.

예시:
```
이 텍스트는 오른쪽 정렬되지 않습니다.

|||
이 텍스트는 오른쪽 정렬됩니다.
이 텍스트도 오른쪽 정렬됩니다.
|||

이 텍스트는 더 이상 오른쪽 정렬되지 않습니다.
```

## 제목

**한 줄 텍스트**를 제목으로(더 크고 밑줄이 있는 형태로) 표시하려면 텍스트 줄 앞에 `# `(매우 큼), `## `(큼) 또는 `### `(작음)을 추가하세요.

예시:
`## 큰 제목`

## 굵게

텍스트 앞뒤에 `**`를 추가하면 **굵게** 표시됩니다.

예시:
`**굵은 텍스트 내용**`

## 이탤릭

텍스트 앞뒤에 `_` 또는 `*`를 추가하면 *기울임꼴*로 표시됩니다.

예시:
`*기울임꼴 텍스트 내용*`

## 취소선

텍스트 앞뒤에 `~`를 추가하면 ~~취소선~~으로 표시됩니다.

예시:
`~취소선 텍스트 내용~`

## 하이퍼링크

클릭하면 웹사이트를 여는 하이퍼링크를 텍스트 내용에 추가할 수 있습니다.

[하이퍼링크](https://google.com)로 표시할 텍스트는 `[ ]`로 감싸고, 실제 링크는 `( )`로 감싸야 합니다.

따라서 `example text content`를 클릭 가능하게 만들고 `https://example-website.net`을 열게 하려면 다음과 같이 합니다:
`[example text content](https://example-website.net)`

## 클릭 및 호버 이벤트

Markdown 클릭 및 호버 이벤트는 [텍스트 요소](./elements#text)와 다른 Markdown 텍스트에서 사용할 수 있습니다. 이를 처리하려면 [**Markdown 텍스트 클릭 시**](./listeners#on-markdown-text-clicked-text_clicked)와 [**Markdown 텍스트 호버 시**](./listeners#on-markdown-text-hovered-text_hovered)를 사용하세요.

클릭 이벤트는 `click:` 접두사를 사용합니다:

```
[some clickable text](click:unique_text_click_event_id)
```

호버 이벤트는 `hover:` 접두사를 사용합니다:

```
[some hoverable text](hover:unique_text_hover_event_id)
```

두 리스너 모두 이벤트 ID를 `$$text_event_id`로 제공합니다.

## 이미지

Markdown은 텍스트 내용 안에 이미지를 표시하는 것을 지원합니다.

FancyMenu는 Markdown에서 Minecraft 리소스, 로컬 리소스, 웹 리소스를 지원합니다.

이미지를 추가하려면 텍스트 줄을 `![](`로 시작한 다음 [URL, 리소스 위치 또는 리소스 경로](./resources)를 적고 `)`로 끝내세요.

예를 들어 웹 리소스 `https://example-website.net/image.png`를 표시하려면 다음과 같이 합니다:
`![](https://example-website.net/image.png)`

이미지는 전체 이미지 텍스트 줄을 아래처럼 **하이퍼링크**로 감싸서 **하이퍼링크**로 만들 수도 있습니다:
`[![](https://example-website.net/image.png)](https://example-website.net)`

> [!WARNING]
> 로컬 리소스는 `<game-directory>/config/fancymenu/assets/` 안에 있어야 합니다!

## 인용문

텍스트를 인용문으로 서식 지정하려면 텍스트 줄을 `> `로 시작하세요.
이렇게 하면 **빈** 줄을 만날 때까지 다음 줄들도 모두 인용문으로 서식 지정됩니다.

예시:
```
이것은 인용문처럼 보이지 않습니다.

> 이것은 인용문처럼 보입니다.
이것도 인용문처럼 보입니다.

이제는 더 이상 인용문처럼 보이지 않습니다.
```

## 글머리 기호 목록

다음과 같은 글머리 기호 목록으로 텍스트를 표시하려면:
- 항목 1
- 항목 2
  - 하위 항목

그저 줄을 `- `로 시작하면 됩니다.

예시:
```
- 항목 1
- 항목 2
  - 하위 항목
```

## 구분선

텍스트 전체 한 줄 너비의 구분선을 추가하려면 줄을 `---`로 시작하고 그 외에는 아무것도 추가하지 마세요.

그러면 대략 다음처럼 표시됩니다:

---

## 코드 블록

코드 블록은 Markdown이 서식을 적용하지 않도록 텍스트를 `일반 텍스트`로 표시하거나, 줄바꿈 자동 적용 없이 코드처럼 보이게 표시할 때 유용합니다.

한 줄 코드 블록(다른 텍스트 사이에 있는)은 \`로 시작하고 \`로 끝나며, Markdown 텍스트에서 이를 보여주기는 사실 꽤 어렵습니다.

한 줄 코드 블록이 포함된 텍스트 줄은 다음처럼 보입니다:

![single_line_code_block](https://github.com/Keksuccino/FancyMenu/assets/35544624/e78fd38b-7b1a-4f00-9b11-797d964b3b43)

여러 줄 코드 블록은 여러 줄을 하나의 큰 코드 블록으로 감싸며, `\`\`\``만 있는 줄로 시작한 다음 텍스트 내용을 적고 다시 `\`\`\``로 끝냅니다:

![multi_line_code_block](https://github.com/Keksuccino/FancyMenu/assets/35544624/bf8c77eb-a97e-48cd-9270-8302c2995856) 

## 일반 텍스트

일반 텍스트 서식 코드는 내부의 다른 모든 서식 코드를 무시합니다.

코드 블록과 비슷하게 작동하지만 코드 블록처럼 서식이 적용되지는 않습니다. 대신 일반 텍스트처럼 보이지만 서식은 적용되지 않습니다.

줄 안의 텍스트 일부를 일반 텍스트 서식 코드로 감싸려면 다음처럼 `;;`를 표시하고 싶은 텍스트 앞뒤에 추가하세요:

```
이것은 한 줄의 텍스트로, ;;**이 부분**;;은 서식이 적용되지 않은 텍스트로 보이며 ** (굵게) 서식 코드가 보이고, _이 부분_은 일반적으로 서식이 적용된 이탤릭 텍스트로 보입니다.
```

일반 텍스트는 여러 줄을 감싸는 코드로도 사용할 수 있습니다. 전체 줄을 감싸려면 다음처럼 표시하고 싶은 줄의 앞뒤에 `;;;`를 추가하세요:

```
;;;
이 줄은 **서식이 적용되지 않은** 상태로 보이며 ** (굵게) 서식 코드가 보입니다.
이 줄도 _서식이 적용되지 않은_ 상태로 보이며 _ (이탤릭) 서식 코드가 보입니다.
;;;

이제 이 줄은 "일반"이 굵게 표시된 상태로 다시 **정상**처럼 보입니다.
```

# Minecraft 텍스트 서식

Minecraft 서식 코드는 FancyMenu 전반에서 지원되는 서식 텍스트 필드에서 작동합니다. Minecraft의 `§` 접두사 대신 `&`를 사용하세요. 예를 들어 `&cWarning`은 빨간색 텍스트를 표시합니다.

사용 가능한 색상과 스타일은 [Minecraft Wiki의 서식 코드 참고](https://minecraft.wiki/w/Formatting_codes)를 확인하세요.

> [!CAUTION]
> **텍스트 요소**는 Markdown을 파싱하므로 Minecraft 서식 코드는 신뢰할 수 없습니다. 대신 위에 설명된 Markdown 서식을 사용하세요.

# Minecraft 텍스트 컴포넌트(원시 컴포넌트 시스템)

Minecraft의 텍스트 컴포넌트 시스템은 **버튼 레이블** 같은 **한 줄** 텍스트 내용에 매우 강력합니다.

바닐라 Minecraft에서는 `/tellraw` 및 `/title` 명령(그리고 아마도 다른 곳)에서 사용할 수 있습니다.
이것은 JSON으로 직렬화된 서식 텍스트이므로 텍스트 내용에 서식 속성을 추가할 수 있습니다.

텍스트 컴포넌트에 대해 더 자세히 알아보려면 [이 Minecraft wiki 페이지](https://minecraft.wiki/w/Raw_JSON_text_format)를 확인하세요.
Minecraft의 글꼴에 대해 더 자세히 알아보려면 [이 Minecraft wiki 페이지](https://minecraft.wiki/w/Resource_pack#Fonts)를 확인하세요.

FancyMenu가 버튼 레이블을 **텍스트 컴포넌트**로 인식하게 하려면 직렬화된 컴포넌트 텍스트만 레이블로 설정하세요. 예를 들면 다음과 같습니다:
`{"text":"Button Label Text","font":"uniform"}`

위 예시는 버튼 레이블 `Button Label Text`를 `uniform` 글꼴로 표시합니다.

> [!NOTE]
> 컴포넌트의 `text` 값 안에서 FancyMenu의 플레이스홀더를 사용할 수 있습니다.
