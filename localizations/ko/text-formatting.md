---
title: 텍스트 서식
description: Markdown과 Minecraft의 서식 코드를 사용해 텍스트를 서식 지정하는 방법입니다.
---

# 텍스트 서식

FancyMenu에는 레이아웃의 텍스트 콘텐츠를 더 *멋지게* 만들어 주는 다양한 기능이 있습니다!

텍스트 요소는 몇 가지 멋진 추가 기능과 함께 **Markdown**을 완벽하게 지원하며, 대부분의 다른 텍스트 콘텐츠는 **Minecraft의 텍스트 서식** 시스템을 지원합니다. 또한 버튼 레이블은 **Minecraft 텍스트 컴포넌트**도 지원하므로 사용자 지정 글꼴 등을 사용할 수 있습니다.

# Markdown

FancyMenu의 **텍스트 요소**는 Markdown을 완전히 지원합니다. 즉, 특수 문자를 추가해 텍스트 콘텐츠의 서식을 지정할 수 있습니다.

예를 들어 텍스트를 굵게 보이게 하려면 굵게 만들 텍스트 앞뒤에 `**`를 붙이면 됩니다. `**Some bold text that's very bold.**` 는 다음처럼 표시됩니다:
**Some bold text that's very bold.**

FancyMenu의 Markdown에는 이를 더욱 강력하게 만들어 주는 특별한 기능도 있습니다!

> Markdown은 버튼 레이블 같은 다른 텍스트 기반 요소에는 **작동하지 않습니다**. 이것은 **텍스트 요소**에서만 작동합니다. 그 외의 모든 경우에는 [Minecraft의 서식 코드](/text-formatting#minecraft-text-formatting)를 사용하세요.
{.is-danger}

## 글꼴

텍스트 앞에 `%!!<font_name>%`를 붙이고 텍스트 뒤에 `%!!%`를 붙이면 리소스 팩으로 불러온 사용자 지정 글꼴로 텍스트를 표시할 수 있습니다.

기본 게임에 포함된 유효한 글꼴은 `uniform`입니다. `uniform` 글꼴로 텍스트를 표시하려면 다음과 같이 합니다:
`%!!uniform%this is a custom font%!!%`

그러면 `this is a custom font`가 `uniform` 글꼴로 표시됩니다.

## 텍스트 색상 (HEX)

텍스트 앞에 `%<HEX_color>%`를 붙이고 텍스트 뒤에 `%#%`를 붙이면 특정 HEX 색상으로 텍스트를 표시할 수 있습니다.

초록색의 유효한 HEX 색상은 `#77fc03`이므로, 이 색으로 텍스트를 표시하려면 다음과 같이 합니다:
`%#77fc03%this text is green!%#%`

그러면 `this text is green!`이 `#77fc03`(초록색)으로 표시됩니다.

HEX 색상은 반드시 `#`로 시작해야 합니다!

FancyMenu 3.9.0에서는 이 동일한 색상 서식 코드에서 흔한 HTML 스타일의 색상 이름도 지원합니다:

```
%#red%This text is red!%#%
```

지원되는 이름: `black`, `silver`, `gray`, `grey`, `white`, `maroon`, `red`, `purple`, `fuchsia`, `magenta`, `green`, `lime`, `olive`, `yellow`, `navy`, `blue`, `teal`, `aqua`, `cyan`, `transparent`.

## 텍스트 정렬

특정 정렬 서식 코드로 줄을 시작한 뒤, 아무것도 쓰지 않고, 해당 정렬로 표시할 텍스트 줄들을 작성한 다음, 빈 줄에 다시 그 정렬 코드를 넣으면 텍스트 줄을 정렬할 수 있습니다.

모든 텍스트 콘텐츠는 기본적으로 **왼쪽 정렬**이므로, 서식 코드는 **가운데 정렬**과 **오른쪽 정렬**만 있습니다.

### 가운데 정렬

텍스트 줄을 가운데 정렬하려면 서식 코드 `^^^`를 사용하세요.

예시:
```
This text is not centered.

^^^
This text is centered.
This text is also centered.
^^^

This text is not centered anymore.
```

### 오른쪽 정렬

텍스트 줄을 오른쪽 정렬로 표시하려면 서식 코드 `|||`를 사용하세요.

예시:
```
This text is not right-aligned.

|||
This text is right-aligned.
This text is also right-aligned.
|||

This text is not right-aligned anymore.
```

## 제목

**한 줄의 텍스트**를 제목으로 표시하려면(더 크고 밑줄이 그어짐), 텍스트 줄 앞에 `# `(매우 큼), `## `(큼) 또는 `### `(작음)을 붙이세요.

예시:
`## Big Headline`

## 굵게

텍스트 앞뒤에 `**`를 붙이면 **굵게** 표시됩니다.

예시:
`**bold text content**`

## 기울임꼴

텍스트 앞뒤에 `_` 또는 `*`를 붙이면 *기울임꼴*로 표시됩니다.

예시:
`*italic text content*`

## 취소선

텍스트 앞뒤에 `~`를 붙이면 ~~취소선~~으로 표시됩니다.

예시:
`~strikethrough text content~`

## 하이퍼링크

클릭하면 웹사이트가 열리는 하이퍼링크를 텍스트에 추가할 수 있습니다.

[hyperlink](https://google.com)처럼 보이게 할 텍스트는 `[ ]`로 감싸고, 실제 링크는 `( )`로 감싸야 합니다.

따라서 `example text content`를 클릭 가능하게 만들어 `https://example-website.net`을 열려면 다음과 같이 합니다:
`[example text content](https://example-website.net)`

## 클릭 및 호버 이벤트

FancyMenu 3.9.0에서는 텍스트 요소와 다른 Markdown 텍스트에 대한 Markdown 클릭 및 호버 이벤트가 추가되었습니다.

클릭 이벤트는 `click:` 접두사를 사용합니다:

```
[some clickable text](click:unique_text_click_event_id)
```

호버 이벤트는 `hover:` 접두사를 사용합니다:

```
[some hoverable text](hover:unique_text_hover_event_id)
```

이 이벤트에 반응하려면 **Markdown 텍스트 클릭됨** 및 **Markdown 텍스트 호버됨** 리스너를 사용하세요. 두 리스너 모두 `$$text_event_id`로 이벤트 ID를 제공합니다.

## 이미지

Markdown은 텍스트 콘텐츠에 이미지를 표시하는 것을 지원합니다.

FancyMenu는 Markdown에서 Minecraft 리소스, 로컬 리소스, 웹 리소스를 지원합니다.

이미지를 추가하려면 텍스트 줄을 `![](`로 시작한 뒤, [URL, 리소스 위치 또는 리소스 경로](/resources)를 넣고 `)`로 닫으세요.

따라서 웹 리소스 `https://example-website.net/image.png`를 표시하려면 다음과 같이 합니다:
`![](https://example-website.net/image.png)`

이미지는 전체 이미지 텍스트 줄을 다음처럼 **하이퍼링크**로 감싸서 **하이퍼링크**로 만들 수도 있습니다:
`[![](https://example-website.net/image.png)](https://example-website.net)`

> 로컬 리소스는 `/config/fancymenu/assets/` 안에 있어야 합니다!
{.is-warning}

## 인용문

텍스트를 인용문으로 서식 지정하려면 텍스트 줄을 `> `로 시작하세요.
이렇게 하면 **빈** 줄을 찾을 때까지 뒤따르는 모든 줄이 인용문으로 서식 지정됩니다.

예시:
```
This will not look like a quote.

> This will look like a quote.
This will also look like a quote.

This will not look like a quote anymore.
```

## 글머리 목록

다음과 같은 글머리 목록으로 텍스트를 표시하려면:
- Entry 1
- Entry 2
  - Sub-Entry

줄을 `- `로 시작하면 됩니다.

예시:
```
- Entry 1
- Entry 2
  - Sub-Entry
```

## 구분선

텍스트에 전체 텍스트 줄 너비의 구분선을 추가하려면, 줄을 `---`로 시작하고 그 뒤에는 아무것도 쓰지 마세요.

그러면 다음과 같이 보입니다:

---

## 코드 블록

코드 블록을 사용하면 Markdown이 서식 지정하지 않도록 텍스트를 `일반 텍스트`로 표시하거나, 자동 줄바꿈 없이 코드처럼 보이게 표시할 수 있습니다.

단일 줄 코드 블록(다른 텍스트 사이에 있는 경우)은 \` 로 시작하고 \` 로 끝나는데, Markdown 텍스트에서 이걸 보여주기는 꽤 어렵습니다..

단일 줄 코드 블록이 포함된 한 줄의 텍스트는 다음처럼 보입니다:

![single_line_code_block](https://github.com/Keksuccino/FancyMenu/assets/35544624/e78fd38b-7b1a-4f00-9b11-797d964b3b43)

여러 줄 코드 블록은 여러 줄을 하나의 큰 코드 블록으로 묶으며, `\`\`\``만 있는 줄로 시작한 뒤 텍스트 콘텐츠를 넣고 다시 `\`\`\``로 끝냅니다:

![multi_line_code_block](https://github.com/Keksuccino/FancyMenu/assets/35544624/bf8c77eb-a97e-48cd-9270-8302c2995856) 

## 일반 텍스트

일반 텍스트 서식 코드는 그 안의 다른 모든 서식 코드를 무시합니다.

코드 블록과 비슷하게 작동하지만 코드 블록처럼 서식 지정하지는 않습니다. 대신 일반 텍스트처럼 보이지만 서식은 적용되지 않습니다.

줄 안의 텍스트 일부를 일반 텍스트 서식 코드로 감싸려면, 일반 텍스트로 표시할 부분 앞뒤에 `;;`를 붙이면 됩니다:

```
This is a line of text with ;;**this part**;; showing as unformatted text with visible ** (bold) formatting code and _this part_ as normal formatted italic text.
```

일반 텍스트는 여러 줄을 감싸는 코드로도 사용할 수 있습니다. 전체 줄을 감싸려면, 일반 텍스트로 표시할 줄 앞뒤에 `;;;`를 붙이세요:

```
;;;
This line will show **unformatted** with visible ** (bold) formatting codes.
This line will also show _unformatted_ with visible _ (italic) formatting codes.
;;;

This line will look **normal** again with the "normal" formatted as bold text.
```

# Minecraft 텍스트 서식

Minecraft 자체에도 꽤 좋은 서식 시스템이 있으며, Markdown과 비슷하게 텍스트 콘텐츠에 특수 문자를 추가해 서식을 지정합니다.

Minecraft의 서식 시스템에 대해 더 알아보려면 [이 Minecraft 위키 페이지](https://minecraft.wiki/w/Formatting_codes)를 참고하세요.

> 위키에서는 서식 코드 접두사가 `§`라고 설명하지만, FancyMenu에서는 이를 `&`로 바꿔야 합니다. 나머지는 모두 동일합니다.
{.is-warning}

> **텍스트 요소**는 매우 복잡하며 Markdown을 지원하기 위한 대가로 **Minecraft 바닐라 서식 코드가 깨지도록** 되어 있으므로, 이러한 코드는 텍스트 요소에서 제대로 작동하지 않습니다(서식 코드 뒤의 첫 단어만 서식이 적용되는 등). 대신 텍스트 요소에서는 Markdown 서식 코드를 사용해야 합니다.
{.is-danger}

# Minecraft 텍스트 컴포넌트(원시 컴포넌트 시스템)

Minecraft의 텍스트 컴포넌트 시스템은 **버튼 레이블** 같은 **한 줄** 텍스트 콘텐츠에 매우 강력합니다.

바닐라 Minecraft에서는 `/tellraw` 및 `/title` 명령어(그리고 아마 다른 곳들)에서 사용할 수 있습니다.
서식이 적용된 텍스트를 JSON으로 직렬화한 것이므로, 텍스트 콘텐츠에 서식 속성을 추가할 수 있습니다.

텍스트 컴포넌트에 대해 더 자세히 알아보려면 [이 Minecraft 위키 페이지](https://minecraft.wiki/w/Raw_JSON_text_format)를 참고하세요.
Minecraft의 글꼴에 대해 더 알아보려면 [이 Minecraft 위키 페이지](https://minecraft.wiki/w/Resource_pack#Fonts)를 참고하세요.

FancyMenu가 버튼 레이블을 **텍스트 컴포넌트**로 감지하게 하려면, 레이블에는 직렬화된 컴포넌트 텍스트만 넣으세요. 예를 들면 다음과 같습니다:
`{"text":"Button Label Text","font":"uniform"}`

위 예시는 버튼 레이블 `Button Label Text`를 `uniform` 글꼴로 표시합니다.

> 컴포넌트의 `text` 값 안에서 FancyMenu의 플레이스홀더를 사용할 수 있습니다.
{.is-info}
