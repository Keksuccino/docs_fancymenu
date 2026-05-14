---
title: 브라우저 JavaScript API
description: Browser 요소와 같은 MCEF 기반 모드 기능에서 FancyMenu의 JavaScript API를 사용하는 방법입니다.
---

# FancyMenu JavaScript API

FancyMenu는 MCEF 기반 기능(예: **Browser** 요소)에 JavaScript 브리지를 주입합니다. 이 브리지를 통해 웹 콘텐츠는 다음을 할 수 있습니다.

- JavaScript에서 직접 FancyMenu [action](./action-scripts)을 실행,
- 모든 FancyMenu [placeholder](/placeholders) 값을 비동기적으로 읽기.

다음 두 전역 객체가 API를 제공합니다.
- `window.fancymenu` – 기본 네임스페이스
- `window.FancyMenu` – 별칭(`fancymenu`와 정확히 동일한 구조를 가짐)

호출 전에 브리지가 사용 가능한지 확인하려면 `fancymenu-ready` 이벤트 또는 기능 감지를 사용하세요.

## 1. 네임스페이스 및 구조

- `fancymenu.actions` – 브라우저에서 FancyMenu action 실행
- `fancymenu.placeholders` – FancyMenu placeholder 값을 비동기적으로 읽기
- `FancyMenu`는 `fancymenu`를 그대로 반영하므로, 둘 다 동일한 하위 네임스페이스를 제공합니다.

Action에는 두 가지 헬퍼가 있습니다.
- `fancymenu.actions.execute(actionType, actionValue?)`
- `fancymenu.actions.executeWithCallback(actionType, actionValue?, onSuccess?, onFailure?)`

## 2. 사용 가능 여부

```javascript
if (typeof fancymenu !== 'undefined') {
    // 안전하게 사용 가능
}

window.addEventListener('fancymenu-ready', () => {
    console.log('FancyMenu API가 준비되었습니다');
});
```

콘텐츠는 로컬에서도 호스팅할 수 있습니다. HTML 파일을 `config/fancymenu/assets/`에 넣고 `file:///config/fancymenu/assets/<name>.html` 형식의 URL로 불러오세요.

## 3. Action 실행

`fancymenu.actions` 네임스페이스를 사용하세요. 각 호출은 FancyMenu 스크립트에서 사용하는 action 문자열과 동일합니다.

### 빠른 호출

```javascript
fancymenu.actions.execute('quitgame');                // 값이 없는 action
fancymenu.actions.execute('opengui', 'title_screen'); // 값이 있는 action
fancymenu.actions.execute('set_variable', 'hp:20');   // 값은 name:value 형식 사용
```

### 콜백 사용

```javascript
fancymenu.actions.executeWithCallback(
    'opengui',
    'title_screen',
    result => console.log('타이틀 화면이 열렸습니다'),
    error  => console.error('열기 실패:', error)
);

// value 매개변수는 선택 사항입니다. 생략하면 actionType 뒤에 콜백을 바로 전달하세요.
fancymenu.actions.executeWithCallback(
    'quitgame',
    result => console.log('종료가 트리거되었습니다'),
    error  => console.error('종료 실패:', error)
);

기존 헬퍼인 `fancymenu.execute(...)`와 `fancymenu.executeWithCallback(...)`도 여전히 동작하며 `actions` 네임스페이스로 전달되므로, 기존 콘텐츠를 즉시 변경할 필요는 없습니다.
```

### 일반적인 Action 유형

- `quitgame` – 즉시 게임 종료(값 없음)
- `back_to_last_screen` – 이전 GUI로 돌아가기(값 없음)
- `opengui` – FancyMenu 또는 바닐라 화면 열기(값: 화면 식별자)
- `openlink` – 브라우저 열기(값: URL)
- `sendmessage` – 채팅 메시지 전송(값: 메시지 텍스트)
- `set_variable` – FancyMenu 변수 할당(값: `name:value`)
- `joinserver` – 서버에 연결(값: 주소)
- `disconnect_server_or_world` – 연결을 끊고 대상 화면으로 이동(값: 화면 식별자)

FancyMenu에 존재하는 모든 action은 브리지로 사용할 수 있습니다. 전체 목록은 [action scripts](./action-scripts)를 참조하세요.

## 4. Placeholder 읽기

FancyMenu의 [placeholder](/placeholders) 시스템은 `fancymenu.placeholders`(및 `FancyMenu.placeholders`)를 통해 제공됩니다. 두 헬퍼 메서드 모두 `Promise<string>`를 반환합니다.

```ts
fancymenu.placeholders.get(identifier: string): Promise<string>
fancymenu.placeholders.getWithVars(identifier: string, ...vars: string[]): Promise<string>
```

### 변수 전달

- 변수는 `name:value` 형식의 문자열입니다. 브리지는 첫 번째 콜론만 기준으로 나누므로, 값에는 추가 콜론이 포함될 수 있습니다.
- 이름과 값의 앞뒤 공백은 제거되며, 빈 이름은 허용되지 않습니다.
- placeholder가 요구하는 만큼 변수를 전달하세요. 선택적 변수는 생략할 수 있습니다.

### 예시

```javascript
// 변수 없음
fancymenu.placeholders.get('playername')
    .then(name => console.log('Player:', name));

// 변수 1개
fancymenu.placeholders.getWithVars('uptime_duration', 'output_as_millis:false')
    .then(seconds => console.log('Uptime (s):', seconds));

// 변수 여러 개
fancymenu.placeholders.getWithVars(
    'split_text',
    'input:apple|banana|carrot',
    'regex:\\|',
    'max_parts:-1',
    'split_index:1'
).then(part => console.log('선택된 부분:', part));
```

### 오류 모델

거부된 promise에는 구조화된 오류가 포함됩니다.

```ts
interface PlaceholderError {
    code: 'NOT_FOUND' | 'MISSING_VARIABLE' | 'INVALID_VARIABLE' | 'EVALUATION_ERROR' | 'INTERNAL_ERROR';
    message: string;
    details?: unknown;
}
```

예외 처리 예시:

```javascript
fancymenu.placeholders.get('unknown')
    .catch(error => console.warn(error.code, error.message));
```

## 5. 전체 예제

```html
<!DOCTYPE html>
<html>
<head>
    <title>FancyMenu 통합</title>
</head>
<body>
    <h1>게임 제어</h1>
    
    <button onclick="quitGame()">게임 종료</button>
    <button onclick="openTitleScreen()">타이틀 화면</button>
    <button onclick="disconnectFromServer()">연결 끊기</button>
    <button onclick="setVariable()">변수 설정</button>
    <button onclick="loadPlaceholders()">Placeholder 불러오기</button>

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
                () => console.log('타이틀 화면이 열렸습니다!'),
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
                console.warn('FancyMenu placeholder API를 아직 사용할 수 없습니다.');
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
                    'Player: ' + playerName + '\n' +
                    'Uptime (seconds): ' + uptimeSeconds + '\n' +
                    'Second fruit: ' + secondFruit;
            }).catch(error => {
                console.error('Placeholder 요청 실패:', error);
            });
        }
    </script>
</body>
</html>
```

## 6. 모범 사례 및 참고사항

- 사용하기 전에 **브리지를 감지**하거나 `fancymenu-ready`를 수신하세요.
- 유용한 피드백을 제공할 수 있도록 **오류를 처리**하세요([action](/action-scripts)은 콜백, [placeholders](/placeholders)은 `.catch`).
- action이나 [placeholder](/placeholders) 변수에 전달하기 전에 **입력을 검증**하세요.
- **요청 속도를 조절**하세요. 브리지를 짧은 간격의 호출로 과도하게 사용하지 마세요(특히 placeholder 새로고침 루프).
- **보안**: action은 플레이어의 일반 권한으로 실행됩니다. 인젝션을 피하기 위해 사용자 제공 데이터는 주의해서 다루세요.

## 7. 문제 해결

1. 페이지가 FancyMenu가 제어하는 MCEF 브라우저에서 열렸는지 확인하세요.
2. 브라우저 콘솔에서 JavaScript 오류를 확인하세요.
3. [placeholder](/placeholders) 식별자 또는 [action](/action-scripts) 유형이 올바른지, 그리고 필요한 값이 제공되었는지 확인하세요.
4. 실행이 예상치 못하게 실패하면 Minecraft 로그(`latest.log`)에서 FancyMenu 오류 메시지를 확인하세요.
