---
title: 시작하기
description: FancyMenu의 세계가 여러분을 기다립니다! 아름다운 무언가의 시작입니다!
---

# 개발자용

FancyMenu용 애드온을 만들거나 여러분의 모드에 FancyMenu를 통합하고 싶다면, [개발자 문서](https://github.com/Keksuccino/FancyMenu-Dev-Docs/wiki)를 확인해 보세요.

# 시작하기

처음 FancyMenu를 사용할 때는 조금 벅차게 느껴질 수 있지만, 걱정하지 마세요. 실제로는 조금만 익숙해지면 대부분 매우 직관적입니다!

> 이 페이지는 FancyMenu를 처음 접하고 **첫걸음**을 떼는 데 도움을 주기 위한 것임을 **꼭 기억**해 주세요.
FancyMenu의 기능에 대한 더 자세한 정보는 문서의 나머지 부분도 함께 확인해 보시기 바랍니다!
{.is-info}

# 메뉴 바

게임을 시작하면 가장 먼저 눈에 띄는 것 중 하나가 모든 메뉴 상단에 있는 **메뉴 바**입니다.

**메뉴 바**는 **레이아웃 생성**으로 메뉴를 **커스터마이즈**하고, **창 제목과 아이콘**을 바꾸는 등 FancyMenu의 거의 모든 기능으로 들어가는 입구입니다.

> 실수로 어떤 키를 눌러 **메뉴 바가 사라졌다면**, **CTRL + ALT + C**를 눌러 다시 표시할 수 있습니다.
{.is-warning}

<img width="650" alt="menu_bar" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/menu_bar.png?raw=true">

# 첫 번째 레이아웃 만들기

아마 Minecraft의 메뉴를 꾸미고 싶으실 테니, **레이아웃**에 대해 말씀드리겠습니다!

레이아웃은 메뉴를 위한 커스터마이즈 레이어처럼 작동하며, 새로운 요소를 추가하고 기존 요소를 수정할 수 있게 해 줍니다.

**특정 메뉴**에 새 레이아웃을 만들려면:
1. 레이아웃을 만들고 싶은 메뉴를 엽니다(예: 타이틀 화면)
2. **메뉴 바**의 **커스터마이즈** 탭을 엽니다

커스터마이즈는 기본적으로 모든 메뉴에서 비활성화되어 있으며, 수정하려는 각 메뉴마다 활성화해야 합니다. 그러니 먼저 **"현재 화면 커스터마이즈: 비활성화됨"** 항목을 클릭해 토글을 **활성화됨**으로 바꿔 보겠습니다.

<img width="475" alt="toggle_customizations" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/toggle_customizations.png?raw=true">

그다음 **레이아웃 -> 새로 만들기 -> 현재 화면용**을 클릭합니다.

그러면 레이아웃에 요소를 추가하고 바닐라 및 모드 요소(예: 버튼)를 커스터마이즈할 수 있는 **레이아웃 편집기**가 열립니다.

<img width="550" alt="new_layout_current" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/new_layout_current.png?raw=true">

## 레이아웃 편집하기

대부분의 커스터마이즈 옵션은 **편집기 배경을 우클릭**해서 접근할 수 있습니다.
그러면 **메뉴 배경**을 수정하거나 레이아웃에 **요소를 추가**하는 등 다양한 옵션이 있는 컨텍스트 메뉴가 열립니다.

<br>
<img width="350" alt="context_menu" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/context_menu.png?raw=true">

## 레이아웃에 요소 추가하기

레이아웃에 새 요소를 추가하려면 편집기 배경을 **우클릭**하세요.

열리는 컨텍스트 메뉴에서 **새 요소**를 클릭한 다음, 다양한 요소 유형 중 하나를 선택하면 됩니다.

<img width="525" alt="add_element" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/add_element.png?raw=true">

## 요소 커스터마이즈하기

요소를 커스터마이즈하려면 해당 요소를 **우클릭**하면 됩니다. 그러면 그 요소 유형에서 수정할 수 있는 모든 항목이 들어 있는 컨텍스트 메뉴가 열립니다.

추가한 요소뿐 아니라 바닐라 요소도 커스터마이즈할 수 있습니다(다만 경우에 따라 옵션이 더 적을 수 있습니다).

<img width="525" alt="element_customization" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/element_customization.png?raw=true">

> [!IMPORTANT]
> 이와 같은 일부 컨텍스트 메뉴는 **스크롤 가능**합니다!

## 요소 배치하기

FancyMenu의 모든 요소는 **앵커 포인트**에 연결되어 있습니다.

앵커 포인트는 요소의 위치를 계산하는 데 필요하며, 올바르게 사용하면 요소가 서로 겹치거나, 화면 밖으로 나가거나, 창 크기를 조절할 때 엉뚱한 위치로 이동하는 것을 방지할 수 있습니다.

앵커 포인트는 요소의 위치가 계산되기 시작하는 기준점입니다.

기본적으로 요소는 **"화면 중앙"** 앵커 포인트에 연결되어 있으며, 이는 창 크기와 상관없이 화면의 정확한 중앙을 의미합니다.
예를 들어 어떤 요소가 **"화면 중앙"** 앵커에 연결된 상태에서 화면 중앙으로부터 2센티미터 떨어져 있다고 해 봅시다. 이 경우 창 크기와 관계없이 그 요소는 **항상** 화면 중앙에서 2센티미터 떨어져 있게 됩니다.

요소를 드래그하면 그 요소가 연결된 앵커 포인트를 볼 수 있습니다. 기본적으로는 다른 모든 앵커 포인트도 함께 표시됩니다. 요소를 드래그하는 동안 앵커 포인트 위에 마우스를 올리면, 해당 요소의 앵커를 그 포인트로 바꿀 수 있습니다.

다른 요소를 위한 앵커 포인트로 요소 자체를 사용할 수도 있습니다! 다른 요소를 드래그하는 동안 어떤 요소 위에 마우스를 올리면, 드래그 중인 요소의 앵커 포인트가 그 요소로 변경됩니다.

**[요소 배치 방법에 대해 자세히 알아보세요.](/positioning-elements)**

<img width="650" alt="anchor_points" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/anchor_points.png?raw=true">

## 작업 저장하기

멋지게 만든 결과물을 저장하는 걸 잊지 마세요!

저장해야 할 변경 사항이 있으면 편집기 오른쪽 위에 "저장되지 않은 변경 사항" 표시가 나타납니다.

**레이아웃 -> 저장**을 클릭해서 작업을 저장하세요!

<img width="375" alt="save_your_work" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/save_your_work.png?raw=true">

> [!TIP]
> 키보드 단축키 **CTRL + S**를 사용해서도 저장할 수 있습니다.

*축하합니다! 이제 Minecraft의 메뉴를 훨씬 더 아름답게 꾸밀 수 있습니다!*
