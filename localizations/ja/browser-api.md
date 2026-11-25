---
title: ブラウザー JavaScript API
description: Browser 要素など、Rinku ベースの MOD 機能で FancyMenu の JavaScript API を使用する方法。
sourceBlobSha: 1dff260c0c5337037200dbf9033300a6bba56ca1
---
# FancyMenu JavaScript API

FancyMenu は、[Rinku](https://modrinth.com/mod/rinku) を利用するすべての機能（**Browser** 要素など）に JavaScript ブリッジを注入します。このブリッジを使うと、Web コンテンツから次の操作を行えます。

- JavaScript から FancyMenu の任意の [アクション](/action-scripts)を実行する
- FancyMenu の任意の[プレースホルダー](/placeholders)を非同期で読み取る

API は次の 2 つのグローバル変数を通じて公開されます。
- `window.fancymenu` – メインの名前空間
- `window.FancyMenu` – エイリアス（`fancymenu` とまったく同じ構成）

API を呼び出す前に、`fancymenu-ready` イベントまたは機能検出を使って、ブリッジが利用可能であることを確認してください。

## 1. 名前空間と構成

- `fancymenu.actions` – ブラウザーから FancyMenu のアクションを実行します。
- `fancymenu.placeholders` – FancyMenu のプレースホルダー値を非同期で読み取ります。
- `FancyMenu` は `fancymenu` と同じ構成を持ち、同じサブ名前空間を公開します。

アクションには、次の 2 つのヘルパーがあります。
- `fancymenu.actions.execute(actionType, actionValue?)`
- `fancymenu.actions.executeWithCallback(actionType, actionValue?, onSuccess?, onFailure?)`

## 2. 利用可能かどうかの確認

```javascript
if (typeof fancymenu !== 'undefined') {
    // 安全に使用できます
}

window.addEventListener('fancymenu-ready', () => {
    console.log('FancyMenu API の準備ができました');
});
```

コンテンツはローカルでホストすることもできます。HTML ファイルを `<game-directory>/config/fancymenu/assets/` に配置し、`file:///config/fancymenu/assets/<name>.html` 形式の URL で読み込んでください。

## 3. アクションの実行

`fancymenu.actions` 名前空間を使用します。各呼び出しは、FancyMenu スクリプトで使われるアクション文字列に対応しています。

### 簡単な呼び出し

```javascript
fancymenu.actions.execute('quitgame');                // 値なしのアクション
fancymenu.actions.execute('opengui', 'title_screen'); // 値を指定するアクション
fancymenu.actions.execute('set_variable', 'hp:20');   // 値は name:value 形式
```

### コールバックを使う

```javascript
fancymenu.actions.executeWithCallback(
    'opengui',
    'title_screen',
    result => console.log('タイトル画面を開きました'),
    error  => console.error('開けませんでした:', error)
);

// value パラメーターは省略できます。省略する場合は、actionType の直後にコールバックを渡します。
fancymenu.actions.executeWithCallback(
    'quitgame',
    result => console.log('終了を開始しました'),
    error  => console.error('終了できませんでした:', error)
);
```

従来のヘルパー `fancymenu.execute(...)` と `fancymenu.executeWithCallback(...)` も引き続き使用でき、`actions` 名前空間に処理を委譲します。

### よく使われるアクションの種類

- `quitgame` – ゲームを直ちに終了します（値なし）
- `back_to_last_screen` – 前の GUI に戻ります（値なし）
- `opengui` – FancyMenu またはバニラの画面を開きます（値: 画面 ID）
- `openlink` – ブラウザーを起動します（値: URL）
- `sendmessage` – チャットにメッセージを送信します（値: メッセージ本文）
- `set_variable` – FancyMenu の変数を設定します（値: `name:value`）
- `joinserver` – サーバーに接続します（値: アドレス）
- `disconnect_server_or_world` – 接続を切断し、指定した画面に移動します（値: 画面 ID）

FancyMenu で利用できるすべてのアクションを、このブリッジから実行できます。全アクションの一覧は[アクションスクリプト](/action-scripts)を参照してください。

## 4. プレースホルダーの読み取り

FancyMenu の[プレースホルダー](/placeholders)システムは、`fancymenu.placeholders`（および `FancyMenu.placeholders`）から利用できます。どちらのヘルパーメソッドも `Promise<string>` を返します。

```ts
fancymenu.placeholders.get(identifier: string): Promise<string>
fancymenu.placeholders.getWithVars(identifier: string, ...vars: string[]): Promise<string>
```

### 変数の指定

- 変数は `name:value` 形式の文字列です。ブリッジは最初のコロンだけで分割するため、値にはコロンを含められます。
- 名前と値の前後の空白は取り除かれます。名前が空の場合は拒否されます。
- プレースホルダーが必要とする数の変数を指定してください。省略可能な変数は省略できます。

### 例

```javascript
// 変数なし
fancymenu.placeholders.get('playername')
    .then(name => console.log('プレイヤー:', name));

// 変数を 1 つ指定
fancymenu.placeholders.getWithVars('uptime_duration', 'output_as_millis:false')
    .then(seconds => console.log('稼働時間（秒）:', seconds));

// 複数の変数を指定
fancymenu.placeholders.getWithVars(
    'split_text',
    'input:apple|banana|carrot',
    'regex:\\|',
    'max_parts:-1',
    'split_index:1'
).then(part => console.log('選択した要素:', part));
```

### エラーの形式

拒否された Promise には、次の構造化エラーが含まれます。

```ts
interface PlaceholderError {
    code: 'NOT_FOUND' | 'MISSING_VARIABLE' | 'INVALID_VARIABLE' | 'EVALUATION_ERROR' | 'INTERNAL_ERROR';
    message: string;
    details?: unknown;
}
```

処理例:

```javascript
fancymenu.placeholders.get('unknown')
    .catch(error => console.warn(error.code, error.message));
```

## 5. 使用例

```html
<!DOCTYPE html>
<html>
<head>
    <title>FancyMenu 連携</title>
</head>
<body>
    <h1>ゲーム操作</h1>
    
    <button onclick="quitGame()">ゲームを終了</button>
    <button onclick="openTitleScreen()">タイトル画面</button>
    <button onclick="disconnectFromServer()">切断</button>
    <button onclick="setVariable()">変数を設定</button>
    <button onclick="loadPlaceholders()">プレースホルダーを読み込む</button>

    <div id="placeholderOutput" style="margin-top:16px;font-family:monospace"></div>
    
    <script>
        function getActions() {
            if (typeof fancymenu === 'undefined') {
                console.warn('FancyMenu API はまだ利用できません。');
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
                () => console.log('タイトル画面を開きました。'),
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
                console.warn('FancyMenu のプレースホルダー API はまだ利用できません。');
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
                    'プレイヤー: ' + playerName + '\n' +
                    '稼働時間（秒）: ' + uptimeSeconds + '\n' +
                    '2 番目のフルーツ: ' + secondFruit;
            }).catch(error => {
                console.error('プレースホルダーの取得に失敗しました:', error);
            });
        }
    </script>
</body>
</html>
```

## 6. ベストプラクティスと注意事項

- 使用前に**ブリッジを検出する**か、`fancymenu-ready` を待ち受けてください。
- 役立つフィードバックを表示できるよう、**エラーを処理してください**（[アクション](/action-scripts)にはコールバック、[プレースホルダー](/placeholders)には `.catch` を使用）。
- アクションや[プレースホルダー](/placeholders)の変数に渡す前に、**入力を検証してください**。
- **リクエストを制限してください**。ブリッジに短時間で大量の呼び出しを送らないでください（特にプレースホルダーを繰り返し更新するループ）。
- **セキュリティ:** ブラウザーのコンテンツは、ファイル、ネットワーク、コマンド、クリップボード、リソースパック、リンク、終了に関するアクションなど、登録済みの FancyMenu アクションをすべて呼び出せます。信頼できるページだけを読み込み、Web コンテンツから受け取るデータはすべて検証してください。

## 7. トラブルシューティング

1. ページが FancyMenu 管理下の Rinku ブラウザーで読み込まれていることを確認します。
2. ブラウザーのコンソールで JavaScript エラーを確認します。
3. [プレースホルダー](/placeholders)の ID または[アクション](/action-scripts)の種類が正しいこと、および必要な値が指定されていることを確認します。
4. 実行時に予期しない失敗が起きた場合は、Minecraft のログ（`latest.log`）で FancyMenu のエラーメッセージを確認します。
