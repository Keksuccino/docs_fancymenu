---
title: 자주 묻는 질문
description: 자주 묻는 질문입니다.
---
# 자주 묻는 질문

### 문제 해결에 도움이 필요합니다. 어떤 정보를 제공해야 하나요?

최대한 좋은 도움을 받으려면 가능한 한 많은 맥락을 제공해 주세요:
1.  **문제에 대한 명확한 설명:** 무엇을 기대했고, 실제로는 무엇이 일어났나요?
2.  **`latest.log` 파일:** `<game-directory>/logs/latest.log`에서 찾을 수 있습니다. **크래시 로그는 특별히 요청받지 않는 한 보내지 마세요**. 보통 필요한 맥락은 `latest.log`에 있습니다. 게시할 때는 https://gist.github.com 같은 사이트를 사용해 주세요.
3.  **Minecraft 버전:** (예: 1.20.1)
4.  **모드 로더와 버전:** (예: Forge 47.2.0, Fabric 0.15.7)
5.  **FancyMenu 버전:** (예: 3.5.2)
6.  **문제 상황의 스크린샷 또는 영상**도 큰 도움이 됩니다.

### 요소의 레이어 순서를 어떻게 바꾸나요? (무언가를 다른 것 앞이나 뒤로 옮기기)

*   **커스텀 vs. 커스텀:** **Window -> Editor Widgets -> Layers**를 열고 계층 구조에서 요소를 드래그하세요. 요소를 우클릭한 뒤 **Move One Layer Up/Down**을 사용할 수도 있습니다. [Layers and Groups](./layers-and-groups)를 참조하세요.
*   **커스텀 vs. 바닐라:** 모든 커스텀 요소를 모든 바닐라 요소 뒤에 렌더링하려면(예: 기본 버튼 뒤에 배경 이미지를 두려면), **에디터 배경을 우클릭**한 다음 **"Render Custom Elements Behind Vanilla"** 옵션을 켜세요.

### 범용 버튼 템플릿에서 특정 버튼만 제외할 수 있나요?

**아니요. 템플릿 버튼에 커스텀 텍스처가 설정되어 있으면, 이 텍스처는 영향을 받는 모든 요소와 항상 공유됩니다. 개별 버튼만 제외할 수는 없습니다.**

### 버튼을 클릭했을 때 어떤 동작을 하게 하려면 어떻게 하나요?

[**Action Script**](./action-scripts)를 사용하세요.
1.  에디터에서 버튼을 우클릭합니다.
2.  **Edit Action Script**를 선택합니다.
3. **Add Action**을 클릭하고 [**Open Screen or Custom GUI**](./action-scripts#open-screen-or-custom-gui-opengui), [**Join Server**](./action-scripts#join-server-joinserver), [**Set Variable Value**](./action-scripts#set-variable-value-fm-variable-set_variable) 같은 작업을 선택합니다.

### 완전히 새로운 메뉴 화면을 처음부터 만들 수 있나요?

[**Custom GUI**](./custom-guis)를 사용하세요.
1.  메뉴 바에서 **Customization -> Custom GUIs -> Manage Custom GUIs**로 이동합니다.
2. **"New GUI"**를 클릭하고 고유한 식별자를 지정합니다.
3. 그러면 이 새 빈 화면을 열어 원하는 요소를 추가해 레이아웃을 만들 수 있습니다.
4. [**Open Screen or Custom GUI** 작업](./action-scripts#open-screen-or-custom-gui-opengui)으로 Custom GUI를 엽니다.

### 프리로딩을 활성화한 뒤 게임 로드가 너무 오래 걸립니다.

이는 예상되는 동작입니다. 고해상도 애니메이션이나 사운드 같은 큰 리소스를 초기 시작 시 프리로딩하면 게임 로딩 시간이 자연스럽게 늘어납니다.

### FMA 애니메이션이 RAM을 너무 많이 사용합니다!

프레임 수가 많고 고해상도인 경우, 기존 [FMA 애니메이션](./fma)은 많은 메모리를 사용할 수 있습니다. AFMA는 크거나 복잡한 애니메이션 텍스처에 더 적합합니다. 기존 FMA 애니메이션은 짧게 유지하고, 전체 영상 재생에는 [Video](./video)를 사용하세요.

### FancyMenu는 OptiFine과 함께 작동하나요?

아니요. OptiFine은 **호환되지 않으며** FancyMenu를 포함한 많은 모드를 깨뜨리는 것으로 알려져 있습니다. Sodium/Embeddium + Iris/Oculus 같은 최신 대안을 사용하는 것이 강력히 권장됩니다.
[OptiFine Alternatives](./optifine-alternatives)를 참조하세요.

### 게임이 충돌합니다. 모드 충돌인지 어떻게 확인하나요?

모드 충돌을 확인하는 가장 좋은 방법은 **FancyMenu와 그 의존성(Konkrete, Melody)만 설치한 상태로 게임을 실행하는 것**입니다. 더 이상 충돌이 발생하지 않으면, 다른 모드를 작은 묶음으로 다시 추가해 보면서 충돌이 재현될 때까지 확인하면 원인 모드를 찾을 수 있습니다.

### 다른 모드의 버튼이 사라지거나 편집하려고 하면 작동하지 않습니다.

일부 모드는 FancyMenu가 감지하거나 커스터마이즈할 수 없는 방식으로 위젯을 추가합니다. [Vanilla/Mod Elements](./vanilla-elements)와, 목록 기반 화면의 경우 [Customizing Scrollable Screens](./customizing-scrollable-screens)를 확인하세요. 그래도 위젯이 보이지 않는다면, 해당 위젯을 추가하는 모드가 지원되는 화면 위젯으로 노출해야 합니다.

### FancyMenu 레이아웃을 서버에서 사용할 수 있나요?

레이아웃과 시각적 커스터마이즈는 플레이어 클라이언트에 저장되므로, 서버가 설정되지 않은 클라이언트에 이를 강제로 적용할 수는 없습니다. 모드팩의 일부로 배포하세요. [서버 명령](./commands), [FM Data](./fm-data), [서버 측 NBT 접근](./nbt-data-placeholder#server-side-placeholder), gamerule, 구조물, 서버 리스너가 필요할 때는 서버에 FancyMenu를 설치하세요.

### FancyMenu v2(구버전 MC용)와 v3의 차이점은 무엇인가요?

FancyMenu v3는 새로운 기능이 많이 추가된 완전한 재작성 버전으로, 더 안정적인 구조와 더 나은 성능을 제공합니다. v2는 오래되었고 더 이상 지원되지 않으며, 고급 플레이스홀더와 스크립팅 같은 많은 기능이 없습니다. 최신 Minecraft 버전(1.18.2+)에서는 v3 사용이 강력히 권장됩니다. v2 레이아웃은 불러올 때 v3로 자동 변환할 수 있지만, 일부는 수동 수정이 필요할 수 있습니다.

### 미리 만들어진 레이아웃과 템플릿은 어디서 찾을 수 있나요?

FancyMenu 커뮤니티는 공식 Keksuccino's Mods Discord 서버("Kekscord")의 `#layout-templates` 채널에서 레이아웃을 공유합니다.

### Player Entity를 다른 요소 뒤에 렌더링하려면 어떻게 하나요?

일반적으로 [Layers 위젯](./layers-and-groups)을 통해 [Player Entity 요소](./elements#player-entity)를 일반적인 2D 요소 뒤로 강제할 수는 없습니다. 이 렌더러는 일반 GUI 레이어 순서를 무시할 수 있습니다. 레이아웃은 이러한 제한을 고려해 설계하거나, 엄격한 레이어 순서가 필요하면 미리 렌더링된 이미지를 사용하세요.

### 제 Player Entity의 다리가 하나뿐입니다! 무슨 일이죠?

이는 시각적 오류로, 아마도 플레이어 애니메이션이나 모델을 변경하는 다른 모드와의 충돌로 인해 발생했을 가능성이 큽니다. Player Entity의 Pose 설정을 확인해 다리가 실수로 회전되거나 이동되었는지 보세요.

### 스크립트에서 작업 사이에 지연을 넣으려면 어떻게 하나요?

지연된 작업 로직에는 [**Delay** 또는 **Execute Later** 블록](./action-scripts#what-are-statements)을 사용하세요. 반복되는 백그라운드 로직에는 [Schedulers](./schedulers)를 사용합니다.

### Create 모드의 메뉴도 커스터마이즈할 수 있나요?

아니요. Create 화면은 의도적으로 커스터마이즈가 비활성화되어 있습니다. [커스터마이즈가 의도적으로 비활성화된 화면](./incompatibility-list#screens-where-customization-is-intentionally-disabled)을 참조하세요.

### 배경 이미지와 버튼 텍스처에 권장되는 해상도는 무엇인가요?

배경: 표준 1920x1080(1080p) 이미지는 좋은 시작점이며 대부분의 사용자에게 잘 맞게 크기가 조정됩니다.
버튼: 바닐라 버튼의 대부분은 너비 약 150~200픽셀, 높이 20픽셀 정도입니다. 커스텀 텍스처도 이 크기에 맞추면 일관성을 유지하기 좋습니다.

### 플레이어가 인게임 목표(예: 퀘스트)를 완료했을 때 자동으로 메뉴를 열거나 명령을 실행할 수 있나요?
FancyMenu에는 많은 [내장 게임 이벤트 리스너](./listeners)가 있지만, 모든 서드파티 퀘스트 시스템을 위한 범용 리스너는 없습니다. 퀘스트 모드가 명령 보상을 지원한다면, [`/openguiscreen`](./commands#openguiscreen), [`/fmvariable`](./commands#fmvariable) 또는 다른 적절한 [FancyMenu 명령](./commands)을 실행하도록 사용하세요.

### 버튼을 비활성화하거나 "회색으로" 표시하려면 어떻게 하나요?

[Loading Requirements](./conditions)를 사용해 버튼의 활성 상태를 제어할 수 있습니다.
에디터에서 버튼을 우클릭한 뒤 **Control Active State**를 선택하세요.
버튼이 활성화되려면 충족되어야 하는 조건을 추가합니다. 영구적으로 비활성화하려면 [**Is Number**](./conditions#is-number-fancymenu_visibility_requirement_is_number)를 사용해 0이 1과 같은지 확인하세요.
그러면 버튼은 "Inactive Background" 텍스처를 사용하며 클릭할 수 없게 됩니다.

### 스크롤 가능한 화면에서 헤더와 푸터(흙 텍스처 막대)를 어떻게 제거하나요?

레이아웃 편집기에서 **Layout Properties -> Header/Footer Customizations**를 엽니다. 텍스처를 투명하게 설정하세요. 이 옵션은 일부 모드된 화면에서는 사용할 수 없을 수 있습니다.

### "현재 화면용" 레이아웃을 만들 수 없습니다. 버튼이 회색으로 비활성화되어 있습니다.

먼저 해당 화면의 커스터마이즈를 **menu bar -> Customization -> Current Screen Customizations -> Enabled**에서 활성화해야 합니다.

### 에디터에서 화면을 열어도 어떤 요소도 커스터마이즈할 수 없습니다. 그냥 빈 화면입니다.

이것은 [Universal Layout](./universal-layouts)이 아니라 **현재 화면용** 레이아웃을 만들었기 때문일 수 있습니다.

또는 [스크롤 가능한 화면](./customizing-scrollable-screens)일 수도 있는데, FancyMenu는 기본적으로 이를 커스터마이즈할 수 없습니다.

세 번째 가능성은 바닐라 방식이 아닌 방식으로 요소를 추가하는 모드의 화면이라서, FancyMenu가 이러한 요소를 커스터마이즈할 수 없는 경우입니다.

### Text 요소에 이상한 회색 상자가 보입니다.

이 반투명 상자는 렌더링 버그가 아니라 [Text 요소](./elements#text)의 스크롤 그랩버입니다.

이 상자를 보이지 않게 하려면 요소를 우클릭해 스크롤 기능을 완전히 비활성화하거나, 요소는 계속 스크롤 가능하게 유지하면서 그랩버 텍스처만 같은 우클릭 메뉴에서 완전히 투명한 것으로 설정할 수 있습니다.

### 최신 Minecraft 변경 로그를 메뉴에 표시하려면 어떻게 하나요?

Minecraft의 변경 로그를 FancyMenu 호환 Markdown으로 변환해 주는 훌륭한 [GitHub 프로젝트](https://github.com/ClaytonTDM/minecraft-changelogs-markdown)가 있어, 최신 MC 변경 로그를 메뉴에 표시할 수 있습니다! 새 변경 로그를 가져오기 위해 매일 업데이트됩니다.

이를 [Text 요소](./elements#text)에 표시하려면 **Source Mode**를 **Resource**로 설정하고 리소스 소스를 **Web**으로 지정하세요. `https://clay.is-a.dev/minecraft-changelogs-markdown/{"placeholder":"mcversion"}/fancymenu.md`를 사용하세요.

### 어떤 요소든 화면 크기에 맞게 늘리는 가장 쉬운 방법은 무엇인가요?

대부분의 요소는 우클릭 컨텍스트 메뉴에서 가로와 세로로 늘리는 옵션을 제공합니다. 이를 활성화하면 요소가 항상 화면의 전체 너비 및/또는 높이까지 늘어납니다. 가로와 세로 늘리기는 각각 독립적으로 켜고 끌 수 있습니다.

### Text 요소 앞이나 뒤에 있을 때 버튼이나 슬라이더를 클릭할 수 없습니다.

Text 요소는 기본적으로 상호작용 가능하도록 설정되어 있습니다(스크롤 그랩버를 잡거나 Markdown 하이퍼링크를 클릭할 수 있도록 하기 위함). 그래서 마우스 클릭과 스크롤 이벤트를 소비합니다. 가장 좋은 방법은 버튼을 Text 요소 뒤/앞으로 옮기지 않는 것이지만, 피할 수 없다면 **Text 요소를 우클릭**한 뒤 **Interactable**을 **Disabled**로 설정해 상호작용 불가 상태로 만들 수 있습니다. 다만 이렇게 하면 Text 요소는 정적이고 상호작용할 수 없는 텍스트가 되므로 더 이상 스크롤하거나 하이퍼링크를 클릭할 수 없습니다.

### 화살표 키와 Tab 키로 화면을 탐색할 때 버튼과 슬라이더가 더 이상 선택/포커스되지 않게 하려면 어떻게 하나요?

버튼과 슬라이더가 탐색되지 않게 하려면 **우클릭**한 뒤 **Navigable**을 **Disabled**로 설정해야 합니다. 버튼/슬라이더는 여전히 클릭할 수 있지만, 더 이상 Arrow/Tab 탐색으로 포커스를 둘 수 없습니다.

이는 채팅 화면에 버튼/슬라이더를 추가하고 싶을 때도 유용합니다. 이렇게 하면 오래된 메시지를 위쪽 화살표 키로 스크롤하면서 실수로 화면의 버튼/슬라이더를 선택하지 않을 수 있습니다.

### FancyMenu의 컨텍스트 메뉴에 있어야 할 옵션이 보이지 않습니다.

FancyMenu의 컨텍스트 메뉴(어딘가를 우클릭하거나 메뉴 바와 상호작용할 때 열리는 메뉴)는 **스크롤 가능합니다**. 즉, 메뉴 위에 마우스 커서를 둔 상태에서 스크롤 휠을 사용해 위아래로 이동할 수 있으며, 이전에 보이지 않던 더 많은 옵션을 볼 수 있습니다.

### Title 화면을 커스터마이즈할 수 없습니다. 에디터를 나가면 계속 원래 화면이 보입니다.

다른 모드가 원래 `title_screen`을 대체하고 있습니다. 해당 모드 설정에서 커스텀 Title 화면을 비활성화하세요. 그런 옵션이 없다면 FancyMenu는 대체된 화면에 레이아웃을 적용할 수 없습니다.
