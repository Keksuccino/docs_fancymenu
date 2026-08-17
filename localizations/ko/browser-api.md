---
title: 브라우저 JavaScript API
description: Browser 요소와 같은 Rinku 기반 모드 기능에서 FancyMenu의 JavaScript API를 사용하는 방법입니다.
---
# FancyMenu JavaScript API

FancyMenu는 모든 [Rinku](https://modrinth.com/mod/rinku) 기반 기능(예: **Browser** 요소)에 JavaScript 브리지를 주입합니다. 이 브리지를 사용하면 웹 콘텐츠에서 다음 작업을 수행할 수 있습니다.

- 모든 FancyMenu [액션](./action-scripts)을 JavaScript에서 직접 실행
- 모든 FancyMenu [플레이스홀더](/placeholders)를 비동기적으로 읽기

두 개의 전역 객체를 통해 API에 접근할 수 있습니다.
- `window.fancymenu` – 기본 네임스페이스
- `window.FancyMenu` – 별칭(`fancymenu`와 완전히 동일한 구조)

호출하기 전에 브리지를 사용할 수 있는지 확인하려면 `fancymenu-ready` 이벤트 또는 기능 감지를 사용하세요.

## 1. 네임스페이스 및 구조

- `fancymenu.actions` – 브라우저에서 FancyMenu 액션을 실행합니다.
- `fancymenu.placeholders` – FancyMenu 플레이스홀더 값을 비동기적으로 읽습니다.
- `FancyMenu`는 `fancymenu`를 그대로 반영하므로 두 객체 모두 동일한 하위 네임스페이스를 제공합니다.

액션은 다음 두 가지 헬퍼를 제공합니다.
- `fancymenu.actions.execute(actionType, actionValue?)`
- `fancymenu.actions.executeWithCallback(actionType, actionValue?, onSuccess?, onFailure?)`

## 2. 사용 가능 여부

```javascript
if (typeof fancymenu !== 'undefined') {
    // 안전하게 사용할 수 있음
}

window.addEventListener('fancymenu-ready', () => {
    console.log('FancyMenu API is ready');
});
```

콘텐츠는 로컬에서 호스팅할 수도 있습니다. HTML 파일을 `<game-directory>/config/fancymenu/assets/`에 넣고 `file:///config/fancymenu/assets/<name>.html` 형식의 URL을 통해 불러오세요.

## 3. 액션 실행

`fancymenu.actions` 네임스페이스를 사용하세요. 각 호출은 FancyMenu 스크립트에서 사용하는 액션 문자열과 동일한 방식으로 동작합니다.

### 간단한 호출

```javascript
fancymenu.actions.execute('quitgame');                // 값이 없는 액션
fancymenu.actions.execute('opengui', 'title_screen'); // 값이 있는 액션
fancymenu.actions.execute('set_variable', 'hp:20');   // 값은 name:value 형식 사용
```

### 콜백 사용

```javascript
fancymenu.actions.executeWithCallback(
    'opengui',
    'title_screen',
    result => console.log('Opened title screen'),
    error  => console.error('Open failed:', error)
);

// value 매개변수는 선택 사항입니다. 생략할 경우 actionType 바로 뒤에 콜백을 전달하세요.
fancymenu.actions.executeWithCallback(
    'quitgame',
    result => console.log('Quit triggered'),
    error  => console.error('Quit failed:', error)
);
```

기존 헬퍼인 `fancymenu.execute(...)` 및 `fancymenu.executeWithCallback(...)`도 계속 사용할 수 있으며, `actions` 네임스페이스로 위임됩니다.

### 일반적인 액션 유형

- `quitgame` – 게임을 즉시 종료합니다(값 없음).
- `back_to_last_screen` – 이전 GUI로 돌아갑니다(값 없음).
- `opengui` – FancyMenu 또는 바닐라 화면을 엽니다(값: 화면 식별자).
- `openlink` – 브라우저를 실행합니다(값: URL).
- `sendmessage` – 채팅 메시지를 보냅니다(값: 메시지 텍스트).
- `set_variable` – FancyMenu 변수를 설정합니다(값: `name:value`).
- `joinserver` – 서버에 연결합니다(값: 주소).
- `disconnect_server_or_world` – 연결을 끊고 대상 화면으로 이동합니다(값: 화면 식별자).

FancyMenu에 존재하는 모든 액션을 브리지를 통해 사용할 수 있습니다. 전체 목록은 [액션 스크립트](./action-scripts)를 참조하세요.

## 4. 플레이스홀더 읽기

FancyMenu의 [플레이스홀더](/placeholders) 시스템은 `fancymenu.placeholders`(`FancyMenu.placeholders`도 동일)를 통해 사용할 수 있습니다. 두 헬퍼 메서드는 모두 `Promise<string>`을 반환합니다.

```ts
fancymenu.placeholders.get(identifier: string): Promise<string>
fancymenu.placeholders.getWithVars(identifier: string, ...vars: string[]): Promise<string>
```

### 변수 전달

- 변수는 `name:value` 형식의 문자열입니다. 브리지는 첫 번째 콜론에서만 분리하므로 값에 추가 콜론을 포함할 수 있습니다.
- 이름과 값의 앞뒤 공백은 제거되며, 빈 이름은 허용되지 않습니다.
- 플레이스홀더에 필요한 만큼 변수를 전달하세요. 선택적 변수는 생략할 수 있습니다.

### 예시

```javascript
// 변수 없음
fancymenu.placeholders.get('playername')
    .then(name => console.log('Player:', name));

// 변수 하나
fancymenu.placeholders.getWithVars('uptime_duration', 'output_as_millis:false')
    .then(seconds => console.log('Uptime (s):', seconds));

// 여러 변수
fancymenu.placeholders.getWithVars(
    'split_text',
    'input:apple|banana|carrot',
    'regex:\\|',
    'max_parts:-1',
    'split_index:1'
).then(part => console.log('Selected part:', part));
```

### 오류 모델

거부된 프로미스에는 구조화된 오류가 포함됩니다.

```ts
interface PlaceholderError {
    code: 'NOT_FOUND' | 'MISSING_VARIABLE' | 'INVALID_VARIABLE' | 'EVALUATION_ERROR' | 'INTERNAL_ERROR';
    message: string;
    details?: unknown;
}
```

처리 예시:

```javascript
fancymenu.placeholders.get('unknown')
    .catch(error => console.warn(error.code, error.message));
```

## 5. 전체 예시

```html
<!DOCTYPE html>
<html>
<head>
    <title>FancyMenu Integration</title>
</head>
<body>
    <h1>Game Controls</h1>
    
    <button onclick="quitGame()">Quit Game</button>
    <button onclick="openTitleScreen()">Title Screen</button>
    <button onclick="disconnectFromServer()">Disconnect</button>
    <button onclick="setVariable()">Set Variable</button>
    <button onclick="loadPlaceholders()">Load Placeholders</button>

    <div id="placeholderOutput" style="margin-top:16px;font-family:monospace"></div>
    
    <script>
        function getActions() {
            if (typeof fancymenu === 'undefined') {
                console.warn('FancyMenu API is not available yet.');
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
                () => console.log('Title screen opened!'),
                err => console.error('Error:', err)
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
            var varName = prompt('Variable name:');
            var varValue = prompt('Variable value:');
            if (varName && varValue) {
                actions.execute('set_variable', varName + ':' + varValue);
            }
        }

        function loadPlaceholders() {
            if (typeof fancymenu === 'undefined' || !fancymenu.placeholders) {
                console.warn('FancyMenu placeholder API is not available yet.');
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
                console.error('Placeholder request failed:', error);
            });
        }
    </script>
</body>
</html>
```

## 6. 권장 사항 및 참고

- 사용하기 전에 **브리지를 감지**하거나 `fancymenu-ready` 이벤트를 수신하세요.
- 유용한 피드백을 제공할 수 있도록 **오류를 처리**하세요([액션](/action-scripts)은 콜백, [플레이스홀더](/placeholders)는 `.catch` 사용).
- 액션 또는 [플레이스홀더](/placeholders) 변수에 전달하기 전에 **입력을 검증**하세요.
- **요청을 제한**하세요. 브리지에 빠른 호출을 반복해서 보내지 마세요(특히 플레이스홀더 새로 고침 루프).
- **보안:** 브라우저 콘텐츠는 파일, 네트워크, 명령, 클립보드, 리소스 팩, 링크 및 종료 액션을 포함해 등록된 모든 FancyMenu 액션을 호출할 수 있습니다. 신뢰할 수 있는 페이지만 불러오고 웹 콘텐츠에서 수신한 모든 데이터를 검증하세요.

## 7. 문제 해결

1. 페이지가 FancyMenu가 제어하는 Rinku 브라우저에서 로드되었는지 확인하세요.
2. 브라우저 콘솔에서 JavaScript 오류를 확인하세요.
3. [플레이스홀더](/placeholders) 식별자 또는 [액션](/action-scripts) 유형이 올바르고 필요한 값이 전달되었는지 확인하세요.
4. 예기치 않게 실행에 실패하면 Minecraft 로그(`latest.log`)에서 FancyMenu 오류 메시지를 확인하세요.
