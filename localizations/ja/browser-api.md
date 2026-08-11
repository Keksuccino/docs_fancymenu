---
title: ブラウザ JavaScript API
description: Browser 要素のような Rinku ベースの MOD 機能で FancyMenu の JavaScript API を使う方法。
---
# FancyMenu JavaScript API

FancyMenu は、[Rinku](https://modrinth.com/mod/rinku) ベースのすべての機能（たとえば **Browser** 要素）に JavaScript ブリッジを注入します。このブリッジにより、Web コンテンツは次のことができます。

- FancyMenu の [アクション](./action-scripts) を JavaScript から直接実行する
- FancyMenu の [プレースホルダー](/placeholders) を非同期に読み取る

次の 2 つのグローバル変数から API を利用できます。
- `window.fancymenu` – 主要な名前空間
- `window.FancyMenu` – エイリアス（`fancymenu` とまったく同じ構造を持ちます）

呼び出し前にブリッジが利用可能か確認するには、`fancymenu-ready` イベント、または機能検出を使用してください。

## 1. 名前空間と構造

- `fancymenu.actions` – ブラウザから FancyMenu のアクションを実行します。
- `fancymenu.placeholders` – FancyMenu のプレースホルダー値を非同期に読み取ります。
- `FancyMenu` は `fancymenu` をミラーしているため、どちらも同じサブ名前空間を公開します。

アクションには 2 つのヘルパーがあります。
- `fancymenu.actions.execute(actionType, actionValue?)`
- `fancymenu.actions.executeWithCallback(actionType, actionValue?, onSuccess?, onFailure?)`

## 2. 利用可能かの確認

```javascript
if (typeof fancymenu !== 'undefined') {
    // 安全に使用できます
}

window.addEventListener('fancymenu-ready', () => {
    console.log('FancyMenu API is ready');
});
```

コンテンツはローカルに配置することもできます。HTML ファイルを `<game-directory>/config/fancymenu/assets/` に置き、`file:///config/fancymenu/assets/<name>.html` 形式の URL で読み込みます。

## 3. アクションの実行

`fancymenu.actions` 名前空間を使用します。各呼び出しは、FancyMenu スクリプトで使われるアクション文字列に対応しています。

### 簡単な呼び出し

```javascript
fancymenu.actions.execute('quitgame');                // 値なしのアクション
fancymenu.actions.execute('opengui', 'title_screen'); // 値ありのアクション
fancymenu.actions.execute('set_variable', 'hp:20');   // 値は name:value 形式
```

### コールバック付き

```javascript
fancymenu.actions.executeWithCallback(
    'opengui',
    'title_screen',
    result => console.log('タイトル画面を開きました'),
    error  => console.error('開けませんでした:', error)
);

// value パラメータは省略可能です。省略する場合は、actionType の直後にコールバックを渡します。
fancymenu.actions.executeWithCallback(
    'quitgame',
    result => console.log('終了が実行されました'),
    error  => console.error('終了に失敗しました:', error)
);
```

旧式のヘルパー `fancymenu.execute(...)` と `fancymenu.executeWithCallback(...)` も、引き続き `actions` 名前空間に委譲されます。

### よく使うアクションタイプ

- `quitgame` – 直ちにゲームを終了します（値なし）
- `back_to_last_screen` – 直前の GUI に戻ります（値なし）
- `opengui` – FancyMenu またはバニラの画面を開きます（値: 画面識別子）
- `openlink` – ブラウザを起動します（値: URL）
- `sendmessage` – チャットにメッセージを送信します（値: メッセージ本文）
- `set_variable` – FancyMenu の変数を代入します（値: `name:value`）
- `joinserver` – サーバーに接続します（値: アドレス）
- `disconnect_server_or_world` – 切断して指定画面へ移動します（値: 画面識別子）

FancyMenu に存在するすべてのアクションは、このブリッジ経由で利用できます。完全な一覧は [action scripts](./action-scripts) を参照してください。

## 4. プレースホルダーの読み取り

FancyMenu の [プレースホルダー](/placeholders) システムは `fancymenu.placeholders`（および `FancyMenu.placeholders`）を通じて公開されています。どちらのヘルパーも `Promise<string>` を返します。

```ts
fancymenu.placeholders.get(identifier: string): Promise<string>
fancymenu.placeholders.getWithVars(identifier: string, ...vars: string[]): Promise<string>
```

### 変数の渡し方

- 変数は `name:value` 形式の文字列です。ブリッジは **最初の** コロンでのみ分割するため、値にコロンを追加で含めることができます。
- 名前と値はトリムされ、空の名前は拒否されます。
- プレースホルダーが必要とする数だけ変数を渡してください。任意の変数は省略できます。

### 例

```javascript
// 変数なし
fancymenu.placeholders.get('playername')
    .then(name => console.log('Player:', name));

// 変数 1 つ
fancymenu.placeholders.getWithVars('uptime_duration', 'output_as_millis:false')
    .then(seconds => console.log('Uptime (s):', seconds));

// 複数の変数
fancymenu.placeholders.getWithVars(
    'split_text',
    'input:apple|banana|carrot',
    'regex:\\|',
    'max_parts:-1',
    'split_index:1'
).then(part => console.log('Selected part:', part));
```

### エラーモデル

拒否された Promise には、構造化されたエラーが含まれます。

```ts
interface PlaceholderError {
    code: 'NOT_FOUND' | 'MISSING_VARIABLE' | 'INVALID_VARIABLE' | 'EVALUATION_ERROR' | 'INTERNAL_ERROR';
    message: string;
    details?: unknown;
}
```

ハンドリング例:

```javascript
fancymenu.placeholders.get('unknown')
    .catch(error => console.warn(error.code, error.message));
```

## 5. 完全な例

```html
<!DOCTYPE html>
<html>
<head>
    <title>FancyMenu Integration</title>
</head>
<body>
    <h1>ゲーム操作</h1>
    
    <button onclick="quitGame()">ゲームを終了</button>
    <button onclick="openTitleScreen()">タイトル画面</button>
    <button onclick="disconnectFromServer()">切断</button>
    <button onclick="setVariable()">変数を設定</button>
    <button onclick="loadPlaceholders()">プレースホルダーを読み込み</button>

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
                () => console.log('タイトル画面を開きました!'),
                err => console.error('エラー:', err)
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
            var varName = prompt('変数名:');
            var varValue = prompt('変数の値:');
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

## 6. ベストプラクティスと注意点

- 使用前に **ブリッジを検出** するか、`fancymenu-ready` を監視してください。
- [アクション](/action-scripts) にはコールバック、[プレースホルダー](/placeholders) には `.catch` を使って **エラーを処理** し、わかりやすいフィードバックを表示してください。
- アクションや [プレースホルダー](/placeholders) の変数に渡す前に **入力を検証** してください。
- **リクエストを抑制** し、ブリッジへの連続呼び出しを乱発しないでください（特にプレースホルダー更新ループ）。
- **セキュリティ:** ブラウザコンテンツは、ファイル・ネットワーク・コマンド・クリップボード・リソースパック・リンク・終了アクションを含む、登録済みの FancyMenu アクションを任意に呼び出せます。信頼できるページのみを読み込み、Web コンテンツから受け取るすべてのデータを検証してください。

## 7. トラブルシューティング

1. ページが FancyMenu に制御された Rinku ブラウザ内で読み込まれていることを確認します。
2. ブラウザのコンソールで JavaScript エラーを確認します。
3. [プレースホルダー](/placeholders) の識別子または [アクション](/action-scripts) の種類が正しいこと、必要な値が渡されていることを確認します。
4. 予期せず実行に失敗する場合は、Minecraft のログ（`latest.log`）で FancyMenu のエラーメッセージを確認してください。
