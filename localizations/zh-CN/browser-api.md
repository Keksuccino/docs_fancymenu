---
title: 浏览器 JavaScript API
description: 如何在基于 Rinku 的模组功能（例如浏览器元素）中使用 FancyMenu 的 JavaScript API。
---
# FancyMenu JavaScript API

FancyMenu 会向每个由 [Rinku](https://modrinth.com/mod/rinku) 驱动的功能（例如 **浏览器**元素）注入 JavaScript 桥接。该桥接允许网页内容：

- 直接从 JavaScript 运行任意 FancyMenu [操作](./action-scripts)；
- 异步读取任意 FancyMenu [占位符](/placeholders)。

API 通过两个全局对象提供：
- `window.fancymenu` – 主要命名空间
- `window.FancyMenu` – 别名（与 `fancymenu` 的结构完全一致）

请使用 `fancymenu-ready` 事件或功能检测，以确保桥接可用后再调用它。

## 1. 命名空间与结构

- `fancymenu.actions` – 在浏览器中执行 FancyMenu 操作。
- `fancymenu.placeholders` – 异步读取 FancyMenu 占位符值。
- `FancyMenu` 是 `fancymenu` 的镜像，因此两者提供相同的子命名空间。

操作提供两个辅助方法：
- `fancymenu.actions.execute(actionType, actionValue?)`
- `fancymenu.actions.executeWithCallback(actionType, actionValue?, onSuccess?, onFailure?)`

## 2. 可用性

```javascript
if (typeof fancymenu !== 'undefined') {
    // 可以安全使用
}

window.addEventListener('fancymenu-ready', () => {
    console.log('FancyMenu API 已就绪');
});
```

内容也可以托管在本地：将 HTML 文件放入 `<game-directory>/config/fancymenu/assets/`，然后通过以下形式的 URL 加载：`file:///config/fancymenu/assets/<name>.html`。

## 3. 执行操作

使用 `fancymenu.actions` 命名空间。每次调用都对应 FancyMenu 脚本中使用的操作字符串。

### 快速调用

```javascript
fancymenu.actions.execute('quitgame');                // 不带值的操作
fancymenu.actions.execute('opengui', 'title_screen'); // 带值的操作
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

// value 参数是可选的。省略时，可在 actionType 后直接传入回调函数。
fancymenu.actions.executeWithCallback(
    'quitgame',
    result => console.log('已触发退出'),
    error  => console.error('退出失败：', error)
);
```

旧版辅助方法 `fancymenu.execute(...)` 和 `fancymenu.executeWithCallback(...)` 仍会委托给 `actions` 命名空间。

### 常见操作类型

- `quitgame` – 立即退出游戏（无值）
- `back_to_last_screen` – 返回上一个 GUI 界面（无值）
- `opengui` – 打开 FancyMenu 或原版界面（值：界面标识符）
- `openlink` – 启动浏览器（值：URL）
- `sendmessage` – 发送一条聊天消息（值：消息文本）
- `set_variable` – 设置 FancyMenu 变量（值：`name:value`）
- `joinserver` – 连接到服务器（值：地址）
- `disconnect_server_or_world` – 断开连接并转到目标界面（值：界面标识符）

FancyMenu 中存在的每个操作都可以通过该桥接使用；完整目录请参阅[操作脚本](./action-scripts)。

## 4. 读取占位符

FancyMenu 的[占位符](/placeholders)系统通过 `fancymenu.placeholders`（以及 `FancyMenu.placeholders`）提供。两个辅助方法都会返回 `Promise<string>`：

```ts
fancymenu.placeholders.get(identifier: string): Promise<string>
fancymenu.placeholders.getWithVars(identifier: string, ...vars: string[]): Promise<string>
```

### 提供变量

- 变量使用 `name:value` 格式的字符串。桥接只会按**第一个**冒号进行拆分，因此值中可以包含额外的冒号。
- 名称和值都会被去除首尾空格；空名称会被拒绝。
- 请提供占位符所需数量的变量。可选变量可以省略。

### 示例

```javascript
// 无变量
fancymenu.placeholders.get('playername')
    .then(name => console.log('玩家：', name));

// 一个变量
fancymenu.placeholders.getWithVars('uptime_duration', 'output_as_millis:false')
    .then(seconds => console.log('运行时间（秒）：', seconds));

// 多个变量
fancymenu.placeholders.getWithVars(
    'split_text',
    'input:apple|banana|carrot',
    'regex:\\|',
    'max_parts:-1',
    'split_index:1'
).then(part => console.log('选中的部分：', part));
```

### 错误模型

被拒绝的 Promise 包含结构化错误：

```ts
interface PlaceholderError {
    code: 'NOT_FOUND' | 'MISSING_VARIABLE' | 'INVALID_VARIABLE' | 'EVALUATION_ERROR' | 'INTERNAL_ERROR';
    message: string;
    details?: unknown;
}
```

错误处理示例：

```javascript
fancymenu.placeholders.get('unknown')
    .catch(error => console.warn(error.code, error.message));
```

## 5. 完整示例

```html
<!DOCTYPE html>
<html>
<head>
    <title>FancyMenu 集成</title>
</head>
<body>
    <h1>游戏控制</h1>
    
    <button onclick="quitGame()">退出游戏</button>
    <button onclick="openTitleScreen()">标题界面</button>
    <button onclick="disconnectFromServer()">断开连接</button>
    <button onclick="setVariable()">设置变量</button>
    <button onclick="loadPlaceholders()">加载占位符</button>

    <div id="placeholderOutput" style="margin-top:16px;font-family:monospace"></div>
    
    <script>
        function getActions() {
            if (typeof fancymenu === 'undefined') {
                console.warn('FancyMenu API 尚未可用。');
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
                () => console.log('标题界面已打开！'),
                err => console.error('错误：', err)
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
            var varName = prompt('变量名称：');
            var varValue = prompt('变量值：');
            if (varName && varValue) {
                actions.execute('set_variable', varName + ':' + varValue);
            }
        }

        function loadPlaceholders() {
            if (typeof fancymenu === 'undefined' || !fancymenu.placeholders) {
                console.warn('FancyMenu 占位符 API 尚未可用。');
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
                    '玩家：' + playerName + '\n' +
                    '运行时间（秒）：' + uptimeSeconds + '\n' +
                    '第二种水果：' + secondFruit;
            }).catch(error => {
                console.error('占位符请求失败：', error);
            });
        }
    </script>
</body>
</html>
```

## 6. 最佳实践与注意事项

- 使用前**检测桥接**，或监听 `fancymenu-ready` 事件。
- **处理错误**（[操作](/action-scripts)使用回调，[占位符](/placeholders)使用 `.catch`），以提供有用的反馈。
- 在将输入传递给操作或[占位符](/placeholders)变量前，**验证输入**。
- **限制请求频率**；避免快速连续调用桥接（尤其是占位符刷新循环）。
- **安全性：**浏览器内容可以调用所有已注册的 FancyMenu 操作，包括文件、网络、命令、剪贴板、资源包、链接和退出操作。仅加载可信页面，并验证从网页内容接收的所有数据。

## 7. 故障排除

1. 确认页面是在 FancyMenu 控制的 Rinku 浏览器中加载的。
2. 检查浏览器控制台中的 JavaScript 错误。
3. 确认[占位符](/placeholders)标识符或[操作](/action-scripts)类型正确，并且已提供所需的值。
4. 如果执行意外失败，请查看 Minecraft 日志（`latest.log`）中的 FancyMenu 错误消息。
