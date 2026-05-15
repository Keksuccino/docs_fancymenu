---
title: Minecraft オプションの設定/取得
description: 音量、FOV、描画距離などの Minecraft オプションを設定・取得する方法。
---

# FancyMenu で Minecraft オプションを扱う

FancyMenu では、さまざまな UI 要素を使って Minecraft のゲーム設定（オプション）を取得・設定できます。このガイドでは、カスタムメニューのレイアウトでボタン、スライダー、ティッカーを使って Minecraft オプションを操作する方法を紹介します。

# Minecraft オプションを理解する

Minecraft には、グラフィック設定から音量まで、あらゆるものを制御する多くの組み込みオプションがあります。FancyMenu では、これらのオプションに名前でアクセスできます。

よく使われるオプション名には次のようなものがあります:
- `soundCategory_master` - メイン音量
- `soundCategory_music` - 音楽音量
- `soundCategory_ambient` - 環境音量
- `soundCategory_players` - プレイヤー音量
- `soundCategory_blocks` - ブロック音量
- `fov` - 視野角
- `gamma` - 明るさ
- `renderDistance` - 描画距離

# オプション値を表示する

特別なプレースホルダーを使うことで、任意の Minecraft オプションの現在値を表示できます。

プレースホルダーは次のような形式です:
```
{"placeholder":"minecraft_option_value","values":{"name":"option_name"}}
```

`option_name` を、表示したい実際のオプション名に置き換えてください。

# ボタンでオプションを設定する

ボタンを使って、Minecraft オプションに特定の値を設定できます。

## ボタンの設定方法:

1. 新しい Button 要素を作成する
2. ボタンのラベル（ボタンに表示される文字）を設定する
3. アクションを追加する: ボタンを右クリック → Action Script を編集 → アクションを追加 → Set Minecraft Option Value
4. 「Set Minecraft Option Value」ウィンドウで:
   - Name: オプション名を入力する（例: `renderDistance`）
   - Value: 設定したい値を入力する（例: `16`）

## 例: 

描画距離を 16 チャンクに設定するボタンを作成する場合:
- Option Name: `renderDistance`
- Value: `16`
- Label: "Set Render Distance to 16 chunks"

# スライダーでオプションを設定する

スライダーは、音量設定や明るさのように値の範囲があるオプションに最適です。

## スライダーの設定方法:

1. 新しい Slider 要素を作成する
2. スライダーの種類を設定する:
   - 整数（描画距離など）の場合: "Integer Range" を選ぶ
   - 小数（音量など）の場合: "Decimal Range" を選ぶ
3. 最小値と最大値を設定する
4. Minecraft オプションを設定するアクションを追加する:
   - 右クリック → Action Script を編集 → アクションを追加 → Set Minecraft Option Value
   - Name: オプション名
   - Value: `$$value`（この特別な変数には現在のスライダー値が入ります）
5. 現在のオプション値を初期選択値として設定する:
   - "Pre-Selected Value" を `{"placeholder":"minecraft_option_value","values":{"name":"option_name"}}` に設定する

## スライダーラベルの表示例:

スライダーのラベルに現在のオプション値を表示するには、次を使います:
```
Volume: {"placeholder":"minecraft_option_value","values":{"name":"soundCategory_master"}}
```

パーセンテージで表示する場合（音量に便利）:
```
Volume: {"placeholder":"calc","values":{"expression":"$$value * 100.0","decimal":"false"}}%
```

# ティッカーでオプションを設定する

ティッカーは、スケジュールに従ってオプションを自動的に変更できる非表示要素です。

## ティッカーの設定方法:

1. 新しい Ticker 要素を作成する
2. ティック設定を構成する:
   - Tick Mode: オプションをいつ更新するかを選ぶ
   - Tick Delay: 更新頻度を設定する（ミリ秒）
3. Minecraft オプションを設定するアクションを追加する:
   - 右クリック → Action Script を編集 → アクションを追加 → Set Minecraft Option Value
   - オプション名と値を設定する

## 例:

メニューを読み込んだときに gamma（明るさ）を最大にする:
- Tick Mode: On Load Screen
- Name: `gamma`
- Value: `1.0`

# よくある用途

FancyMenu を使って Minecraft オプションを設定・取得するときの、よくある使い方を紹介します。

## カスタム音量スライダーを作成する

音量スライダーは、Minecraft オプション連携でよく使われます。ここでは、カスタムの音楽音量スライダーの作り方を説明します:

1. 新しい Slider 要素を作成する
2. "Slider Type" を "Decimal Range" に設定する
3. "Minimum Range Value" を "0.0" に設定する
4. "Maximum Range Value" を "1.0" に設定する
5. Action Script を編集 → アクションを追加 → Set Minecraft Option Value
   - Set Name を `soundCategory_music` に設定する
   - Set Value を `$$value` に設定する
6. "Pre-Selected Value" を `{"placeholder":"minecraft_option_value","values":{"name":"soundCategory_music"}}` に設定する
7. 音量をパーセンテージで表示するには、ラベルを次のように設定する: 
   ```
   Music: {"placeholder":"calc","values":{"expression":"$$value * 100.0","decimal":"false"}}%
   ```

同様のスライダーは、ほかのサウンドカテゴリにも作成できます:
- Master Volume: `soundCategory_master`
- Music: `soundCategory_music`
- Ambient: `soundCategory_ambient`
- Blocks: `soundCategory_blocks`
- Players: `soundCategory_players`
- Weather: `soundCategory_weather`

## カスタム FOV スライダーを作成する

視野角（FOV）は、ゲーム内でどれだけ広く視界が見えるかを決める重要なグラフィック設定です。FOV オプションは内部的には -1.0 から 1.0 の値を使いますが、UI では 30 から 110 として表示されます。

### FOV 値の対応を理解する
- 内部値の範囲: -1.0 から 1.0
- 表示値の範囲: 30 から 110
- 変換式: `(internal_value + 1) * 40 + 30`

### ステップ 1: FOV テキストを更新するティッカー要素を作成する

まず、現在の FOV 値を確認し、適切な説明を変数に設定するティッカーが必要です:

1. 新しい Ticker 要素を作成する
2. "Tick Mode" を "Normal" に設定する（継続的に更新するため）
3. "Tick Delay" を 10 前後（ミリ秒）に設定し、過剰なチェックを避ける

次に、FOV ラベル用のアクションを設定します。アクションスクリプトの構成は次のようになります:

```
▶ Action Script
│
├─▶ IF (mapped FOV = 70)
│  └─■ Set Variable Value: fov_text:Normal
│
├─▶ ELSE-IF (mapped FOV = 110)
│  └─■ Set Variable Value: fov_text:Quake Pro
│
└─▶ ELSE
   └─■ Set Variable Value: fov_text:[計算された数値]
```

それぞれを設定しましょう:

#### 「Normal」FOV ラベルの設定:
1. 右クリック → Action Script を編集 → アクションを追加
2. "IF Statement" をクリックして条件ブロックを追加する
3. 条件を "Is Number" に設定し、以下を入力する:
   - Compare Mode: "equals"
   - Number: `{"placeholder":"calc","values":{"decimal":"false","expression":"({"placeholder":"minecraft_option_value","values":{"name":"fov"}} + 1) * 40 + 30"}}`
   - Compare With: "70"
4. この IF ブロック内に "Set Variable Value (FM Variable)" アクションを追加し、以下を設定する:
   - Value: `fov_text:Normal`

#### 「Quake Pro」FOV ラベルの設定:
1. Action Script 内に "ELSE-IF Statement" を追加する
2. 条件を "Is Number" に設定し、以下を入力する:
   - Compare Mode: "equals"
   - Number: `{"placeholder":"calc","values":{"decimal":"false","expression":"({"placeholder":"minecraft_option_value","values":{"name":"fov"}} + 1) * 40 + 30"}}`
   - Compare With: "110"
3. この ELSE-IF ブロック内に "Set Variable Value (FM Variable)" アクションを追加し、以下を設定する:
   - Value: `fov_text:Quake Pro`

#### 数値の FOV ラベルを設定する:
1. "ELSE Statement" ブロックを追加する
2. この ELSE ブロック内に "Set Variable Value (FM Variable)" アクションを追加し、以下を設定する:
   - Value: `fov_text:{"placeholder":"calc","values":{"decimal":"false","expression":"({"placeholder":"minecraft_option_value","values":{"name":"fov"}} + 1) * 40 + 30"}}`

<img src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/fov_slider_action_script.png" alt="FOV Slider Action Script" style="max-width: 600px; height: auto;">

### ステップ 2: FOV スライダーを作成する

1. 新しい Slider 要素を作成する
2. "Slider Type" を "Decimal Range" に設定する
3. "Minimum Range Value" を "-1.0" に設定する
4. "Maximum Range Value" を "1.0" に設定する
5. Action Script を編集 → アクションを追加 → Set Minecraft Option Value
   - Set Name を `fov` に設定する
   - Set Value を `$$value` に設定する
6. "Pre-Selected Value" を `{"placeholder":"minecraft_option_value","values":{"name":"fov"}}` に設定する

### ステップ 3: スライダーラベルを設定する

スライダーラベルには、FOV テキスト変数をそのまま表示するように設定します:

```
FOV: {"placeholder":"getvariable","values":{"name":"fov_text"}}
```

このラベルでは次のように表示されます:
- 値が 70 のときは "FOV: Normal"
- 値が 110 のときは "FOV: Quake Pro"  
- その他の値では "FOV: 85"（または任意の数値）

### FOV スライダーのヒント

- 内部のスライダー値の範囲は -1.0 から 1.0 で、表示用に 30 から 110 に変換する必要があります
- 変換式は `(internal_value + 1) * 40 + 30` です
- 特別なラベルがある値は 2 つだけです: 70（Normal）と 110（Quake Pro）
- Minecraft のデフォルト FOV は 70 です（内部値 0.0 に対応）
- `fov_text` 変数には、特別なラベルまたは数値のどちらかが自動的に入ります

## テキスト要素にオプション値を表示する

Text 要素にも、現在のオプション値を表示できます:

1. Text 要素を作成する
2. テキスト内容に次のプレースホルダーを使用する: `{"placeholder":"minecraft_option_value","values":{"name":"option_name"}}`

たとえば、現在の描画距離を表示するには:
```
Current render distance: {"placeholder":"minecraft_option_value","values":{"name":"renderDistance"}} chunks
```

# オプション名を見つける

利用可能なすべてのオプション名は、次の方法で見つけられます:

  1. ボタンを作成する
  2. それを右クリックする
  3. "Edit Action Script" をクリックする
  4. "Set Minecraft Option Value" アクションを追加する
  5. アクションの値を編集するとき、"Name" フィールドに入力を始めるとドロップダウン候補が表示されます
  
# 重要なヒント

- **有効な値**: すべてのオプションがすべての値を受け付けるわけではありません。たとえば:
  - 音量系オプションは 0.0 から 1.0 の値を受け付けます
  - 描画距離は通常 2 から 32 の整数を受け付けます
  - `pauseOnLostFocus` のような真偽値オプションは "true" または "false" を受け付けます

- **テスト**: 設定が期待どおりに動作するか、必ずテストしてください！

- **視覚的フィードバック**: 上で説明したプレースホルダーを使って、現在値をユーザーに視覚的に伝えましょう。
