---
title: 浏览器 JavaScript API
description: 如何在基于 MCEF 的模组功能（例如 Browser 元素）中使用 FancyMenu 的 JavaScript API。
---
# FancyMenu JavaScript API

FancyMenu 会向每个基于 MCEF 的功能（例如 **Browser** 元素）注入一个 JavaScript 桥接。这个桥接允许网页内容：

- 直接从 JavaScript 运行任意 FancyMenu [动作](./action-scripts)，
- 异步读取任意 FancyMenu [占位符](/placeholders)。

有两个全局对象暴露了该 API：
- `window.fancymenu` – 主命名空间
- `window.FancyMenu` – 别名（与 `fancymenu` 的结构完全一致）

在调用前，请使用 `fancymenu-ready` 事件或功能检测，确保桥接已可用。

## 1. 命名空间与结构

- `fancymenu.actions` – 从浏览器中执行 FancyMenu 动作。
- `fancymenu.placeholders` – 异步读取 FancyMenu 占位符值。
- `FancyMenu` 与 `fancymenu` 完全一致，因此二者都暴露相同的子命名空间。

动作提供两个辅助方法：
- `fancymenu.actions.execute(actionType, actionValue?)`
- `fancymenu.actions.executeWithCallback(actionType, actionValue?, onSuccess?, onFailure?)`

## 2. 可用性

```javascript
if (typeof fancymenu !== 'undefined') {
    // 可以安全使用
}

window.addEventListener('fancymenu-ready', () => {
    console.log('FancyMenu API is ready');
});
```

内容也可以从本地加载：将 HTML 文件放入 `<game-directory>/config/fancymenu/assets/`，并通过如下格式的 URL 加载：`file:///config/fancymenu/assets/<name>.html`。

## 3. 执行动作

使用 `fancymenu.actions` 命名空间。每次调用都对应 FancyMenu 脚本中使用的动作字符串。

### 快速调用

```javascript
fancymenu.actions.execute('quitgame');                // 不带值的动作
fancymenu.actions.execute('opengui', 'title_screen'); // 带值的动作
fancymenu.actions.execute('set_variable', 'hp:20');   // 值使用 name:value 格式
```

### 使用回调

```javascript
fancymenu.actions.executeWithCallback(
    'opengui',
    'title_screen',
    result => console.log('已打开标题界面'),
    error  => console.error('打开失败：', error)
);

// value 参数是可选的。省略时，请将回调直接放在 actionType 后面。
fancymenu.actions.executeWithCallback(
    'quitgame',
    result => console.log('已触发退出'),
    error  => console.error('退出失败：', error)
);
```

旧版辅助方法 `fancymenu.execute(...)` 和 `fancymenu.executeWithCallback(...)` 仍会转发到 `actions` 命名空间。

### 常见动作类型

- `quitgame` – 立即退出游戏（无值）
- `back_to_last_screen` – 返回上一个 GUI（无值）
- `opengui` – 打开 FancyMenu 或原版界面（值：界面标识符）
- `openlink` – 启动浏览器（值：URL）
- `sendmessage` – 发送聊天消息（值：消息文本）
- `set_variable` – 赋值给 FancyMenu 变量（值：`name:value`）
- `joinserver` – 连接到服务器（值：地址）
- `disconnect_server_or_world` – 断开连接并切换到目标界面（值：界面标识符）

FancyMenu 中存在的每一种动作都可以通过该桥接使用；完整目录请参见 [action scripts](./action-scripts)。

## 4. 读取占位符

FancyMenu 的 [占位符](/placeholders) 系统通过 `fancymenu.placeholders`（以及 `FancyMenu.placeholders`）暴露。两个辅助方法都返回 `Promise<string>`：

```ts
fancymenu.placeholders.get(identifier: string): Promise<string>
fancymenu.placeholders.getWithVars(identifier: string, ...vars: string[]): Promise<string>
```

### 提供变量

- 变量必须是 `name:value` 形式的字符串。桥接只会在**第一个**冒号处分割，因此值中可以包含其他冒号。
- 名称和值都会被去除首尾空白；空名称会被拒绝。
- 请根据占位符需要提供相应数量的变量。可选变量可省略。

### 示例

```javascript
// 无变量
fancymenu.placeholders.get('playername')
    .then(name => console.log('Player:', name));

// 一个变量
fancymenu.placeholders.getWithVars('uptime_duration', 'output_as_millis:false')
    .then(seconds => console.log('Uptime (s):', seconds));

// 多个变量
fancymenu.placeholders.getWithVars(
    'split_text',
    'input:apple|banana|carrot',
    'regex:\\|',
    'max_parts:-1',
    'split_index:1'
).then(part => console.log('Selected part:', part));
```

### 错误模型

被拒绝的 Promise 会包含结构化错误：

```ts
interface PlaceholderError {
    code: 'NOT_FOUND' | 'MISSING_VARIABLE' | 'INVALID_VARIABLE' | 'EVALUATION_ERROR' | 'INTERNAL_ERROR';
    message: string;
    details?: unknown;
}
```

示例处理：

```javascript
fancymenu.placeholders.get('unknown')
    .catch(error => console.warn(error.code, error.message));
```

## 5. 完整示例

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

## 6. 最佳实践与注意事项

- **在使用前检测桥接**，或监听 `fancymenu-ready`。
- **处理错误**（[动作](/action-scripts) 使用回调，[占位符](/placeholders) 使用 `.catch`），以便提供有用的反馈。
- **验证输入** 后再将其传给动作或 [占位符](/placeholders) 变量。
- **限制请求频率**；避免用高频调用刷桥接（尤其是占位符刷新循环）。
- **安全性：** 浏览器内容可以调用任何已注册的 FancyMenu 动作，包括文件、网络、命令、剪贴板、资源包、链接和退出动作。仅加载受信任的页面，并验证从网页内容接收的所有数据。

## 7. 故障排查

1. 确认页面是在 FancyMenu 控制的 MCEF 浏览器中加载的。
2. 检查浏览器控制台中的 JavaScript 错误。
3. 验证 [占位符](/placeholders) 标识符或 [动作](/action-scripts) 类型是否正确，并且已提供所需值。
4. 如果执行意外失败，请查看 Minecraft 日志（`latest.log`）中的 FancyMenu 错误消息。
