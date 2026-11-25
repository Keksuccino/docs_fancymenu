---
title: 브라우저 JavaScript API
description: Browser 요소와 같은 Rinku 기반 모드 기능에서 FancyMenu의 JavaScript API를 사용하는 방법입니다.
sourceBlobSha: 1dff260c0c5337037200dbf9033300a6bba56ca1
---
# FancyMenu JavaScript API

FancyMenu는 [Rinku](https://modrinth.com/mod/rinku)를 기반으로 하는 모든 기능(예: **Browser** 요소)에 JavaScript 브리지를 삽입합니다. 이 브리지를 사용하면 웹 콘텐츠에서 다음 작업을 할 수 있습니다.

- JavaScript에서 FancyMenu [액션](/action-scripts)을 직접 실행
- FancyMenu [플레이스홀더](/placeholders)를 비동기적으로 읽기

API는 다음 두 전역 객체를 통해 사용할 수 있습니다.
- `window.fancymenu` – 기본 네임스페이스
- `window.FancyMenu` – 별칭(`fancymenu`와 완전히 동일한 구조)

브리지를 사용하기 전에 `fancymenu-ready` 이벤트를 이용하거나 기능을 감지해 브리지를 사용할 수 있는지 확인하세요.

## 1. 네임스페이스 및 구조

- `fancymenu.actions` – 브라우저에서 FancyMenu 액션을 실행합니다.
- `fancymenu.placeholders` – FancyMenu 플레이스홀더 값을 비동기적으로 읽습니다.
- `FancyMenu`는 `fancymenu`와 동일한 하위 네임스페이스를 제공합니다.

액션에는 다음 두 가지 헬퍼가 있습니다.
- `fancymenu.actions.execute(actionType, actionValue?)`
- `fancymenu.actions.executeWithCallback(actionType, actionValue?, onSuccess?, onFailure?)`

## 2. 사용 가능 여부

```javascript
if (typeof fancymenu !== 'undefined') {
    // 안전하게 사용할 수 있습니다.
}

window.addEventListener('fancymenu-ready', () => {
    console.log('FancyMenu API를 사용할 수 있습니다');
});
```

콘텐츠를 로컬에서 호스팅할 수도 있습니다. HTML 파일을 `<game-directory>/config/fancymenu/assets/`에 넣고 `file:///config/fancymenu/assets/<name>.html` 형식의 URL로 불러오세요.

## 3. 액션 실행

`fancymenu.actions` 네임스페이스를 사용하세요. 각 호출은 FancyMenu 스크립트에서 사용하는 액션 문자열과 동일한 방식으로 작동합니다.

### 빠른 호출

```javascript
fancymenu.actions.execute('quitgame');                // 값이 없는 액션
fancymenu.actions.execute('opengui', 'title_screen'); // 값이 있는 액션
fancymenu.actions.execute('set_variable', 'hp:20');   // 값은 name:value 형식
```

### 콜백 사용

```javascript
fancymenu.actions.executeWithCallback(
    'opengui',
    'title_screen',
    result => console.log('타이틀 화면을 열었습니다'),
    error  => console.error('열지 못했습니다:', error)
);

// value 매개변수는 선택 사항입니다. 생략할 때는 actionType 바로 뒤에 콜백을 전달하세요.
fancymenu.actions.executeWithCallback(
    'quitgame',
    result => console.log('종료를 시작했습니다'),
    error  => console.error('종료하지 못했습니다:', error)
);
```

레거시 헬퍼인 `fancymenu.execute(...)`와 `fancymenu.executeWithCallback(...)`도 계속 사용할 수 있으며, 내부적으로 `actions` 네임스페이스에 호출을 전달합니다.

### 자주 사용하는 액션 유형

- `quitgame` – 게임을 즉시 종료합니다(값 없음).
- `back_to_last_screen` – 이전 GUI로 돌아갑니다(값 없음).
- `opengui` – FancyMenu 화면 또는 바닐라 화면을 엽니다(값: 화면 식별자).
- `openlink` – 브라우저를 실행합니다(값: URL).
- `sendmessage` – 채팅 메시지를 보냅니다(값: 메시지 텍스트).
- `set_variable` – FancyMenu 변수를 설정합니다(값: `name:value`).
- `joinserver` – 서버에 연결합니다(값: 주소).
- `disconnect_server_or_world` – 연결을 끊고 지정한 화면으로 이동합니다(값: 화면 식별자).

FancyMenu에서 사용할 수 있는 모든 액션을 브리지로 실행할 수 있습니다. 전체 목록은 [액션 스크립트](/action-scripts)를 참조하세요.

## 4. 플레이스홀더 읽기

FancyMenu의 [플레이스홀더](/placeholders) 시스템은 `fancymenu.placeholders`(및 `FancyMenu.placeholders`)를 통해 사용할 수 있습니다. 두 헬퍼 메서드 모두 `Promise<string>`을 반환합니다.

```ts
fancymenu.placeholders.get(identifier: string): Promise<string>
fancymenu.placeholders.getWithVars(identifier: string, ...vars: string[]): Promise<string>
```

### 변수 전달

- 변수는 `name:value` 형식의 문자열입니다. 브리지는 첫 번째 콜론에서만 문자열을 나누므로, 값에 콜론이 더 포함될 수 있습니다.
- 이름과 값의 앞뒤 공백은 제거되며, 이름이 비어 있으면 거부됩니다.
- 플레이스홀더에 필요한 만큼 변수를 전달하세요. 선택적 변수는 생략할 수 있습니다.

### 예제

```javascript
// 변수 없음
fancymenu.placeholders.get('playername')
    .then(name => console.log('플레이어:', name));

// 변수 하나
fancymenu.placeholders.getWithVars('uptime_duration', 'output_as_millis:false')
    .then(seconds => console.log('플레이 시간(초):', seconds));

// 변수 여러 개
fancymenu.placeholders.getWithVars(
    'split_text',
    'input:apple|banana|carrot',
    'regex:\\|',
    'max_parts:-1',
    'split_index:1'
).then(part => console.log('선택한 항목:', part));
```

### 오류 모델

거부된 Promise에는 다음과 같은 구조화된 오류가 포함됩니다.

```ts
interface PlaceholderError {
    code: 'NOT_FOUND' | 'MISSING_VARIABLE' | 'INVALID_VARIABLE' | 'EVALUATION_ERROR' | 'INTERNAL_ERROR';
    message: string;
    details?: unknown;
}
```

오류 처리 예제:

```javascript
fancymenu.placeholders.get('unknown')
    .catch(error => console.warn(error.code, error.message));
```

## 5. 전체 예제

```html
<!DOCTYPE html>
<html>
<head>
    <title>FancyMenu 연동</title>
</head>
<body>
    <h1>게임 제어</h1>
    
    <button onclick="quitGame()">게임 종료</button>
    <button onclick="openTitleScreen()">타이틀 화면</button>
    <button onclick="disconnectFromServer()">연결 끊기</button>
    <button onclick="setVariable()">변수 설정</button>
    <button onclick="loadPlaceholders()">플레이스홀더 불러오기</button>

    <div id="placeholderOutput" style="margin-top:16px;font-family:monospace"></div>
    
    <script>
        function getActions() {
            if (typeof fancymenu === 'undefined') {
                console.warn('FancyMenu API를 아직 사용할 수 없습니다.');
                return null;
            }
            return fancymenu.actions || fancymenu;
        }

        function quitGame() {
            const actions = getActions();
            if (!actions) return;
            actions.execute('quitgame');
        }
        
        function openTitleScreen() {
            const actions = getActions();
            if (!actions) return;
            actions.executeWithCallback(
                'opengui',
                'title_screen',
                () => console.log('타이틀 화면을 열었습니다!'),
                err => console.error('오류:', err)
            );
        }
        
        function disconnectFromServer() {
            const actions = getActions();
            if (!actions) return;
            actions.execute('disconnect_server_or_world', 'title_screen');
        }
        
        function setVariable() {
            const actions = getActions();
            if (!actions) return;
            var varName = prompt('변수 이름:');
            var varValue = prompt('변수 값:');
            if (varName && varValue) {
                actions.execute('set_variable', varName + ':' + varValue);
            }
        }

        function loadPlaceholders() {
            if (typeof fancymenu === 'undefined' || !fancymenu.placeholders) {
                console.warn('FancyMenu 플레이스홀더 API를 아직 사용할 수 없습니다.');
                return;
            }

            Promise.all([
                fancymenu.placeholders.get('playername'),
                fancymenu.placeholders.getWithVars('uptime_duration', 'output_as_millis:false'),
                fancymenu.placeholders.getWithVars(
                    'split_text',
                    'input:apple|banana|carrot',
                    'regex:\\|',
                    'max_parts:-1',
                    'split_index:1'
                )
            ]).then(([playerName, uptimeSeconds, secondFruit]) => {
                document.getElementById('placeholderOutput').textContent =
                    '플레이어: ' + playerName + '\n' +
                    '플레이 시간(초): ' + uptimeSeconds + '\n' +
                    '두 번째 과일: ' + secondFruit;
            }).catch(error => {
                console.error('플레이스홀더 요청 실패:', error);
            });
        }
    </script>
</body>
</html>
```

## 6. 모범 사례 및 참고 사항

- 사용하기 전에 **브리지가 있는지 확인**하거나 `fancymenu-ready` 이벤트를 감지하세요.
- 유용한 피드백을 제공할 수 있도록 **오류를 처리**하세요([액션](/action-scripts)은 콜백, [플레이스홀더](/placeholders)는 `.catch`).
- 액션이나 [플레이스홀더](/placeholders) 변수에 전달하기 전에 **입력값을 검증**하세요.
- **요청 횟수를 제한**하세요. 짧은 간격으로 브리지를 반복 호출하지 마세요(특히 플레이스홀더를 반복해서 새로 고치는 경우).
- **보안:** 브라우저 콘텐츠는 파일, 네트워크, 명령, 클립보드, 리소스 팩, 링크, 종료 액션을 포함해 등록된 FancyMenu 액션을 모두 호출할 수 있습니다. 신뢰할 수 있는 페이지만 불러오고, 웹 콘텐츠에서 받은 모든 데이터를 검증하세요.

## 7. 문제 해결

1. 페이지가 FancyMenu에서 제어하는 Rinku 브라우저에 로드되었는지 확인합니다.
2. 브라우저 콘솔에서 JavaScript 오류를 확인합니다.
3. [플레이스홀더](/placeholders) 식별자 또는 [액션](/action-scripts) 유형이 올바른지, 필요한 값이 전달되었는지 확인합니다.
4. 실행 중 예상치 못한 오류가 발생하면 Minecraft 로그(`latest.log`)에서 FancyMenu 오류 메시지를 확인합니다.
