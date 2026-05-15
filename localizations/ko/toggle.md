---
title: 레이아웃의 일부 토글하기
description: 사용자 입력에 따라 레이아웃의 일부를 토글하는 방법입니다.
---

# 레이아웃의 일부 토글하기

때로는 선택권이 있는 게 좋습니다! 어떤 사용자는 배경음악으로 Rick Astley가 계속 나오는 걸 좋아하지 않을 수도 있고, 메뉴 배경으로 다른 귀여운 애니메이션 소녀를 원할 수도 있습니다.

걱정 마세요! 사용자가 레이아웃의 일부를 켜고 끄거나, 해당 부분의 여러 버전을 순환하도록 만들 수 있습니다.

# 켜기/끄기 토글

예를 들어 버튼을 클릭해서 요소의 표시 여부를 토글하려면, 버튼 클릭 시 값이 설정되는 변수를 사용하고, 토글할 요소는 로딩 요구 사항에서 그 변수가 올바른 값을 가지는지 확인하면 됩니다.

## 변수

먼저, 토글할 요소의 표시 상태를 저장할 변수를 만들어야 합니다.

새 변수를 추가하려면 메뉴 바에서 **Customization** 탭으로 이동한 다음 **Variables -> Manage Variables**를 클릭하고, **고유한** 이름의 새 변수를 추가하세요! 이미 사용 중이 아닌 정말 **고유한** 이름을 사용해야 합니다.

변수를 만든 뒤에는 값을 `true`로 설정하세요.

<br>
<img width="494" alt="Screenshot_9" src="https://gist.github.com/assets/35544624/1e29be13-e601-4669-8fa2-d78db945b07f">

## 요소

다음 단계는 켜고 끌 요소를 추가하는 것입니다.

<br>
<img width="270" alt="Screenshot_3" src="https://gist.github.com/assets/35544624/317460fc-310b-4941-ab9a-b56490c5ebb9">

이제 요소를 마우스 오른쪽 버튼으로 클릭한 뒤 **Loading Requirements**를 클릭하세요.
그러면 Manage Requirements 화면이 열립니다. **Add Requirement**를 클릭하세요.

**Is Variable Value** 요구 사항을 검색해 선택한 다음 **Edit Requirement Value**를 클릭하세요.

<br>
<img width="501" alt="Screenshot_1" src="https://gist.github.com/assets/35544624/d0d342f5-617c-415e-b6f7-05087fc204b7">

이제 앞에서 만든 변수의 이름을 입력하고, 요구 사항이 값으로 `true`를 확인하도록 설정하세요.

<br>
<img width="500" alt="Screenshot_2" src="https://gist.github.com/assets/35544624/a1f356e9-7f96-4d8b-87b0-51f05898409a">

이 부분은 여기까지입니다. 이제 변수의 값이 `true`일 때 요소가 표시됩니다.

## 버튼

이제 새로운 Button 요소를 추가해야 합니다.

<br>
<img width="270" alt="Screenshot_4" src="https://gist.github.com/assets/35544624/1bd1b781-0cdb-4b52-80a0-db8f44ead0db">

추가한 뒤 마우스 오른쪽 버튼으로 클릭하고 **Edit Action Script**를 클릭하세요.
그러면 버튼의 Manage Action Script 화면이 열립니다.

**Add IF Statement**를 클릭하고, 여기에 **Is Variable Value** 요구 사항을 추가한 다음 요구 사항 모드를 **OPPOSITE**로 설정하세요.

<br>
<img width="520" alt="Screenshot_5" src="https://gist.github.com/assets/35544624/a024ea21-2244-4ca6-b44b-1a80f7936b8f">

이제 앞에서 요소에 대해 했던 것처럼 **Edit Requirement Value**를 클릭하고, 동일한 변수 이름과 확인할 값을 그대로 입력하세요.

<br>
<img width="500" alt="Screenshot_2" src="https://gist.github.com/assets/35544624/a1f356e9-7f96-4d8b-87b0-51f05898409a">

요구 사항 모드를 **OPPOSITE**로 설정했기 때문에 이제 변수 값이 `true`가 **아닌지** 확인하게 됩니다. 바로 우리가 원하는 동작입니다.

Edit Action Script 화면으로 돌아오면 방금 추가한 IF 문이 보일 것입니다.

<br>
<img width="495" alt="Screenshot_6" src="https://gist.github.com/assets/35544624/6ac8444c-ca15-43ff-a633-df63e76e7433">

이제 **Add Action**을 클릭하고 **Set Variable Value** 동작을 검색해 선택한 다음 **Edit Action Value**를 클릭하세요.

<br>
<img width="494" alt="Screenshot_7" src="https://gist.github.com/assets/35544624/8568e539-b4d0-49bd-89c4-4659ee71754c">

동작 값으로 먼저 변수 이름을 입력하고, 그 뒤에 설정할 값을 입력하세요. 이름과 값은 `:`로 구분합니다.
이 경우에는 값이 나중에 변수 값이 `true`가 **아닐 때** 실행되므로, 값을 `true`로 설정하려고 합니다.

<br>
<img width="496" alt="Screenshot_8" src="https://gist.github.com/assets/35544624/fab440ad-b335-4751-9651-4bb0b65bc968">

이제 IF 문 위로 드래그해서 이동시켜 해당 IF 문에 동작을 추가하세요. 그러면 변수 값이 `true`가 **아닐 때만** 실행됩니다.

<br>
<img width="496" alt="Screenshot_8" src="https://gist.github.com/assets/35544624/d1ac3ea9-44d7-4ad6-a4b2-455b21f6d1c4">

그 다음 IF 문을 선택하고 **Append ELSE Statement**를 클릭하세요.

이제 또 다른 **Set Variable Value** 동작을 추가하되, 변수 값을 `true`로 설정하는 대신 `false`로 설정하세요.

<br>
<img width="494" alt="Screenshot_9" src="https://gist.github.com/assets/35544624/d05400dc-b9b7-4c1a-8657-9e34939ed599">

이제 두 번째 동작을 ELSE 문에 추가하세요. 그러면 변수 값이 `true`일 때 실행됩니다.

<br>
<img width="494" alt="Screenshot_9" src="https://gist.github.com/assets/35544624/3191a1cc-c5c2-4cf1-a620-23bdbe639bf2">

이제 끝입니다! 처음에는 단계가 많아 보이지만, 익숙해지면 사실 꽤 쉽고 빠르게 할 수 있습니다.

이제 레이아웃을 저장하고 편집기를 나간 뒤 버튼을 눌러 제대로 작동하는지 확인하세요!

<br>
<img width="494" alt="Screenshot_9" src="https://gist.github.com/assets/35544624/e9a87aca-ba0f-4ce6-a39e-1e1d3796c9e3">

같은 변수를 다른 요소에도 사용해서 버튼을 누를 때 **여러 요소를 한 번에 토글**할 수도 있습니다.

**Layout-Wide Loading Requirements**를 사용하면 전체 레이아웃도 토글할 수 있습니다. 레이아웃 전체 요구 사항을 설정하려면 편집기 배경을 마우스 오른쪽 버튼으로 클릭하세요. 단, 버튼은 토글하려는 같은 레이아웃이 아니라 다른 레이아웃에 추가해야 한다는 점을 잊지 마세요.

# 순환하기

두 값 사이를 토글하는 것과 달리, 값 순환은 동작 스크립트가 두 개보다 많은 값 사이를 순환할 수 있어야 합니다.

동작 스크립트 로직은 토글에 사용한 것과 매우 비슷하므로 여기서는 간단히만 설명하겠습니다. 토글 부분도 함께 읽어 보세요.

이미지 3개를 추가했습니다. 첫 번째 이미지는 변수 값이 `1`일 때 표시되고, 두 번째 이미지는 값이 `2`일 때, 세 번째 이미지는 값이 `3`일 때 표시됩니다.

<br>
<img width="494" alt="Screenshot_9" src="https://gist.github.com/assets/35544624/731c13cf-6f81-470b-8e1b-cba264ffbe05">

그다음 순환 버튼을 추가하고, 변수 값이 `1` → `2` → `3` → `1`로 순환하도록 설정했습니다.

<br>
<img width="609" alt="Screenshot_1" src="https://gist.github.com/assets/35544624/9f2052b1-8d3d-4a35-884a-4a234e63d5e5">

이제 끝입니다. 레이아웃을 저장하고 편집기를 나가서 순환 버튼이 올바르게 작동하는지 확인하세요.

<br>
<img width="494" alt="Screenshot_9" src="https://gist.github.com/assets/35544624/430c2369-a43f-4d0f-9203-3fdb1b9eae2c">
