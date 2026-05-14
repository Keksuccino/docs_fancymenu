---
title: 명령어
description: FancyMenu의 명령어와 사용 방법입니다.
---

# 명령어

FancyMenu는 FTB Quests 같은 다른 모드와 함께 사용할 때 매우 유용할 수 있는 몇 가지 명령어를 게임에 추가합니다.

> 멀티플레이어에서 명령어를 사용하려면 FancyMenu가 **서버**(및 클라이언트)에 설치되어 있어야 합니다!
{.is-warning}

## /openguiscreen

`/openguiscreen` 명령어를 사용하면 GUI(바닐라/모드 및 사용자 지정 GUI)를 열 수 있습니다.
FancyMenu가 서버와 클라이언트 모두에 설치되어 있다면 다른 플레이어의 GUI를 원격으로 열 수도 있습니다.

이 명령어에 대한 더 자세한 설명은 [명령어로 GUI 열기](/opengui-command) 페이지를 참고하세요.

이 명령어는 모든 화면에서 작동하지는 않으며, 특히 모드 화면에서는 그렇습니다. 명령어로 화면을 열지 못하면 오류가 표시됩니다. 이런 경우에는 할 수 있는 일이 많지 않은데, 아마도 FancyMenu가 자동으로 열기에는 너무 복잡한 화면이기 때문입니다.

또한 앞으로는 모드 화면에 대한 호환성을 수동으로 추가하지 않을 예정입니다. 모든 모드에 대해 호환성을 추가하려면 너무 오래 걸리기 때문에 양해 부탁드립니다.

**사용법:** `/openguiscreen <screen_identifier> <target_player>`

## /closeguiscreen

`/closeguiscreen` 명령어를 사용하면 현재 GUI를 닫을 수 있습니다.

뭐라고요? 완전히 쓸모없다고요?
음, 맞기도 하지만 사실은 그렇지 않습니다.

이 명령어는 특정 동작에 대해 명령어를 실행하는 모드를 사용할 때 유용합니다.
즉, 다른 모드 없이 이 명령어만 사용하면 사실상 쓸모없지만, 적절한 모드가 설치되어 있다면 매우 유용할 수 있습니다!

**사용법:** `/closeguiscreen <target_player>`

## /fmvariable

`/fmvariable` 명령어를 사용하면 FancyMenu 변수를 설정하거나 가져올 수 있습니다.

서버에서 다른 플레이어로 이 명령어를 실행하려면 바닐라의 `/execute as` 명령어를 사용할 수 있습니다.
예를 들어 `ExamplePlayer` 플레이어로 `/fmvariable` 명령어를 실행하고 싶다면, 다음과 같이 입력하면 됩니다:
`/execute as ExamplePlayer run fmvariable...`.

**사용법:** `/fmvariable <get_or_set> <variable_name> [<set_to_value>] [<send_chat_feedback>]`

### 가져오기
변수 값을 **가져오려면** 다음과 같이 `get` 하위 명령어를 사용하세요:
`/fmvariable get some_variable`

그러면 이 변수의 값이 채팅에 출력됩니다.

### 설정
변수를 **설정하려면** 다음과 같이 `set` 하위 명령어를 사용하세요:
`/fmvariable set some_variable new_value true`

여기서 마지막 인자는 채팅 피드백을 받을지, 즉 이 명령어가 채팅에 메시지를 출력할지 여부를 설정합니다.
