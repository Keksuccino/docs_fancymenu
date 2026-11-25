---
title: GLSLシェーダーAPI
description: 背景、要素、装飾オーバーレイ用のFancyMenu GLSLシェーダーを作成します。
sourceBlobSha: f3da9c3fe83444dab5c59f74f5011e2d6e8cf9e6
---

# FancyMenu GLSLシェーダーAPI

このドキュメントでは、FancyMenuで使用される次のGLSLランタイムについて説明します。

- `GLSL`メニュー背景
- `GLSL`要素
- `GLSL`装飾オーバーレイ

コンパイルモード、マルチパスのルーティング、サポートされているユニフォーム、実用的なシェーダー作成パターンを解説します。

## 1. ランタイムの概要

FancyMenuは内部のOpenGLパイプライン（`#version 150`）でシェーダーを描画し、次の機能をサポートします。

- シングルパスシェーダー（`Image`パスのみ）
- マルチパスシェーダー（`Buffer A` / `B` / `C` / `D` + `Image`）
- Shadertoy形式のエントリーポイント（`mainImage`）
- フラグメントシェーダーの直接エントリーポイント（`main`）

シェーダーソースは、インラインのテキストフィールドに記述します。

- `Shader Source`（Imageパス。描画に必須）
- `Buffer A Source`（任意）
- `Buffer B Source`（任意）
- `Buffer C Source`（任意）
- `Buffer D Source`（任意）

Imageソースが空の場合、「ソースなし」エラーが発生し、描画に失敗します。

## 2. コンパイルモード

FancyMenuは次の3つのコンパイルモードをサポートします。

- `Auto`
- `Direct Fragment`
- `Shadertoy`

### 2.1 Shadertoyモード

次のエントリーポイントが必要です。

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord)
```

FancyMenuはこれを`main()`でラップし、エリア内のローカル座標を渡します。

```glsl
mainImage(fmColor_FancyMenu, gl_FragCoord.xy - fmAreaOffset);
```

ラッパーは出力アルファに`fmOpacity`を乗算します。

### 2.2 Directモード

次のエントリーポイントが必要です。

```glsl
void main()
```

互換性に関する動作：

- `gl_FragColor`互換のバリアントを試します。
- 互換性処理なしのバリアントも試します（最新の明示的な`out vec4`シェーダー向け）。

Directモードでは、出力に`fmOpacity`は自動適用されません。必要に応じて手動で適用してください。

### 2.3 Autoモード

Autoは互換性のあるバリアント（Shadertoy/direct）を順番に試し、最初にコンパイルできたものを使用します。

## 3. ソースの前処理と組み込みマクロ

コンパイル前に、FancyMenuはソースを正規化します。

- UTF-8 BOMを削除
- CRLF/CRをLFに変換
- `#version ...`行を削除
- `precision ...;`行を削除

ランタイムが挿入する前置コードには、次のものが含まれます。

- `#version 150`
- `in vec2 fmUv_FancyMenu`（`[0,1]`の全画面UV。原点は左下）
- `#define iGlobalTime iTime`
- `#define texture2D texture`
- `#define textureCube texture`

注意：

- ソース内ですでに既知のユニフォーム名（例：`iTime`）が宣言されている場合、FancyMenuは重複した宣言を挿入しません。
- その名前への値のアップロードは、引き続きランタイムで試行されます。
- ここでの`textureCube`は別名マクロにすぎません。`iChannel0..3`は`sampler2D`ユニフォームです。

## 4. パスシステム（Image + Buffer A-D）

FancyMenuには5つのパススロットがあります。

- `Buffer A`
- `Buffer B`
- `Buffer C`
- `Buffer D`
- `Image`（画面に最終出力するパス）

動作：

- Bufferパスは、ソースが空でない場合にのみ実行されます。
- 出力を描画するにはImageパスが必要です。
- バッファーは浮動小数点テクスチャ（`GL_RGBA16F`）に描画され、その後、各フレームで読み取り用と書き込み用を入れ替えるピンポン方式で処理されます。

### 4.1 パスごとのチャンネルルーティング

各パスでは、`iChannel0..3`のルーティングを設定できます。各チャンネルで次のいずれかを選択できます。

- `None`
- `Resource 0`
- `Resource 1`
- `Resource 2`
- `Resource 3`
- `Buffer A`
- `Buffer B`
- `Buffer C`
- `Buffer D`

Resourceチャンネルは、`iChannel# Resource`設定から取得されます。

デフォルト：

- すべての`iChannel`ルーティングは`None`
- Bufferソースが空でない場合を除き、Bufferパスは有効になりません

重要：

- 同じBufferパスへのルーティング（フィードバック）では、前フレームのデータ（ピンポン方式の読み取りテクスチャ）を読み取ります。
- ルーティング先のソースがない、または無効な場合はフォールバックテクスチャがバインドされ、`iChannelResolution[n].z`は`0.0`になります。

## 5. 座標とエリアの仕様

シェーダーは矩形エリア内で実行されます。

- メニュー背景：画面全体のエリア
- GLSL要素：要素の矩形エリア

座標の規則：

- ピクセル単位のユニフォームは、エリア内のローカル座標です。
- シェーダーに渡されるピクセル座標のY軸の原点は左下です。
- マウス座標は範囲に制限されません。カーソルがエリア外にある場合、値もエリア外になることがあります。

専用フィールド：

- `fmAreaOffset`：画面のピクセル座標におけるエリアの左下位置
- `fmAreaTopLeft`：画面のピクセル座標におけるエリアの左上位置
- `fmAreaSize`：エリアのピクセルサイズ

## 6. ユニフォームAPIリファレンス

以下のすべてのユニフォームは、背景シェーダーと要素シェーダーの両方で使用できます。

## 6.1 Shadertoy互換ユニフォーム

| ユニフォーム | 型 | 説明 |
|---|---|---|
| `iResolution` | `vec3` | `(areaWidthPx, areaHeightPx, 1.0)` |
| `iTime` | `float` | シェーダーの累積時間（秒） |
| `iTimeDelta` | `float` | 直近の描画からの経過時間。フリーズや時間スケールの影響を受けます |
| `iFrameRate` | `float` | MinecraftのFPS。取得できない場合はランタイムのFPSを使用します |
| `iFrame` | `int` | ランタイムごとのフレームカウンター |
| `iMouse` | `vec4` | 詳細は以下を参照 |
| `iDate` | `vec4` | `(年, 月, 日, 小数部を含む1日の経過秒数)` |
| `iSampleRate` | `float` | 定数`44100.0` |
| `iChannelTime[4]` | `float[4]` | 現在はすべて`iTime`に設定されます |
| `iChannelResolution[4]` | `vec3[4]` | チャンネルごとの`(幅, 高さ, 有効フラグ)` |
| `iChannel0..3` | `sampler2D` | ルーティングされたテクスチャ入力 |

### `iMouse`の詳細

`iMouse = vec4(x, y, z, w)`

- `x`、`y`：エリア内の現在のローカルマウスピクセル位置。切り替えが有効な場合は、押下中の位置を保持する、または固定された値になります
- `z`、`w`：左クリック開始位置
  - マウスの左ボタンを押している間は正の値
  - ボタンを離した後は負の値

切り替えによる動作：

- `Update iMouse Position Only While Holding LMB = Off`：
  - `iMouse.xy`が継続的に更新されます
- `... = On`：
  - `iMouse.xy`はLMBを押している間のみ更新され、その後は最後に押下していた位置に留まります

デフォルト値：

- `Off`（継続的に更新）

## 6.2 FancyMenu固有のユニフォーム

| ユニフォーム | 型 | 説明 |
|---|---|---|
| `fmAreaOffset` | `vec2` | 画面座標におけるエリア左下のピクセルオフセット |
| `fmAreaSize` | `vec2` | エリアのピクセルサイズ |
| `fmAreaPosition` | `vec2` | `fmAreaOffset`と同じ |
| `fmAreaTopLeft` | `vec2` | 画面座標におけるエリア左上のピクセルオフセット |
| `fmScreenSize` | `vec2` | 画面全体のピクセルサイズ |
| `fmGuiScale` | `float` | 現在のGUIスケール |
| `fmMouse` | `vec4` | `(ローカルPxX, ローカルPxY下端基準, ローカルNormX, ローカルNormY)` |
| `fmMouseDelta` | `vec2` | エリア内のマウス移動量（Y軸はシェーダーの上方向に反転） |
| `fmMouseButtons` | `ivec4` | ボタン`0..3`の押下状態 |
| `fmMouseClickCount` | `ivec4` | ボタン`0..3`の累積押下回数 |
| `fmMouseReleaseCount` | `ivec4` | ボタン`0..3`の累積リリース回数 |
| `fmMouseScroll` | `vec2` | このランタイムの前回描画以降のスクロール量 |
| `fmMouseScrollTotal` | `vec2` | 累積スクロール量 |
| `fmKeyEvent` | `ivec4` | `(最後のキーコード, 最後のスキャンコード, 最後の修飾キー, 最後のアクション)` |
| `fmKeyEventCount` | `int` | キーイベントの累積カウンター |
| `fmCharEvent` | `ivec4` | `(最後のコードポイント, 最後の修飾キー, 0, 0)` |
| `fmCharEventCount` | `int` | 文字入力イベントの累積カウンター |
| `fmDateParts` | `ivec4` | `(年, 月, 日, 曜日（ISO 1～7）)` |
| `fmTimeParts` | `ivec4` | `(時, 分, 秒, ミリ秒部分（0～999）)` |
| `fmDayOfYear` | `int` | 年間通算日 |
| `fmWeekOfYear` | `int` | 年のISO週番号 |
| `fmUnixTimeSeconds` | `int` | Unixエポックからの経過秒数 |
| `fmUnixTimeMilliseconds` | `int` | 現在時刻のミリ秒部分（`0..999`） |
| `fmPartialTick` | `float` | 現在の部分ティック |
| `fmGameDeltaTicks` | `float` | Minecraftのゲームデルタティック |
| `fmRealtimeDeltaTicks` | `float` | Minecraftのリアルタイムデルタティック |
| `fmInWorld` | `int` | ワールド内では`1`、それ以外では`0` |
| `fmIsPaused` | `int` | 一時停止中は`1`、それ以外では`0` |
| `fmOpacity` | `float` | 実効不透明度の乗数（`0..1`） |
| `fmVariableCount` | `int` | 現在のFancyMenu変数の数 |

キーアクションの値（`fmKeyEvent.w`）：

- `0` = リリース
- `1` = 押下
- `2` = リピート

## 6.3 FancyMenu変数のユニフォームAPI

FancyMenu変数は、値が変わってもシェーダーを再コンパイルすることなく、ランタイムユニフォームとして直接公開されます（背景、要素、装飾オーバーレイの各シェーダーで使用可能）。

### 命名規則

各変数`<name>`に対して、FancyMenuは次のユニフォームを公開します。

- `fmVarFloat_<name>`
- `fmVarInt_<name>`
- `fmVarBool_<name>`
- `fmVarVec2_<name>`
- `fmVarVec3_<name>`
- `fmVarVec4_<name>`
- `fmVarExists_<name>`（`1` = 変数が現在存在する、`0` = 存在しない／削除済み）

`<name>`のユニフォーム接尾辞は、次のように整形されます。

- 使用できる文字は`[A-Za-z0-9_]`
- それ以外の文字はすべて`_`に変換されます
- 先頭が数字の場合は、先頭に`_`が追加されます

例：

- 変数`player_hp` -> 接尾辞`player_hp`
- 変数`player-hp` -> 接尾辞`player_hp`
- 変数`2nd_phase` -> 接尾辞`_2nd_phase`

重要：

- これらの動的な変数ユニフォームは、シェーダーソース内で**自動宣言されません**（使用するものは手動で宣言してください）
- 同じ接尾辞に整形される変数名は避けてください。同じGLSLユニフォーム名に割り当てられます

### 値の変換

変数のテキスト値を`v`とした場合：

- `fmVarFloat_*`：解析されたfloat（解析できない場合は`0.0`）
- `fmVarInt_*`：解析されたint（解析できない場合は`0`）
- `fmVarBool_*`：ブール値／整数として解釈（`true/yes/on/enabled` => `1`、`false/no/off/disabled` => `0`、それ以外は数値が0以外なら`1`）
- ベクトルの解析には、空白、`,`, `;`, `|`を区切り文字として使用できます
  - `fmVarVec2_*`：解析された先頭2つの成分
  - `fmVarVec3_*`：解析された先頭3つの成分
  - `fmVarVec4_*`：解析された先頭4つの成分
  - 成分数が足りない場合、不足分には最後に解析された成分が繰り返し使われます
  - 数値成分がない場合、すべてのベクトル成分にスカラーのフォールバック値が使われます

[リスト変数](/variables#text-and-list-variables)では、テキストの代わりにエントリー数が返されます。

- `fmVarFloat_*`と`fmVarInt_*`：エントリー数。たとえば、3件のエントリーを持つリストでは`3`
- `fmVarBool_*`：リストにエントリーがあれば`1`、空なら`0`
- `fmVarVec2_*`、`fmVarVec3_*`、`fmVarVec4_*`：すべての成分にリストのエントリー数が設定されます

変数が削除された場合：

- `fmVarExists_*`は`0`になります
- 対応するすべての`fmVar*_*`の値が`0`にリセットされます

### 宣言と使用例

```glsl
uniform float fmVarFloat_player_hp;
uniform int fmVarBool_is_boss_phase;
uniform vec3 fmVarVec3_theme_color;
uniform int fmVarExists_player_hp;

void mainImage(out vec4 fragColor, in vec2 fragCoord) {
    vec2 uv = fragCoord / iResolution.xy;

    float hp = clamp(fmVarFloat_player_hp / 100.0, 0.0, 1.0);
    vec3 theme = fmVarVec3_theme_color;
    float boss = float(fmVarBool_is_boss_phase);

    vec3 col = mix(theme * 0.25, theme, hp);
    col += vec3(0.2, 0.0, 0.0) * boss;

    if (fmVarExists_player_hp == 0) {
        col = vec3(0.15);
    }

    fragColor = vec4(col, 1.0);
}
```

## 7. 入力の追跡モデル

FancyMenuは入力をグローバルに追跡し、描画ごとにその状態をスナップショットとして取得します。

- マウス移動／ドラッグ
- マウス押下／リリース
- スクロール
- キー押下／リリース／リピート
- 文字入力

マウス入力の堅牢性：

- ランタイムは各フレームでGLFWのポーリング結果とボタン状態を照合し、ボタンが押されたままになる状態を防ぎます。

`Pass Input Events To Shader`が無効の場合：

- 入力ユニフォームは毎フレーム中立値にリセットされます
- シェーダーから参照できるデータ内のカウンターとイベントはゼロになります

## 8. テクスチャ入力の詳細

Resourceチャンネル（`iChannel# Resource`）では、2Dテクスチャを指定します。

チャンネルごとのテクスチャ状態：

- 有効なリソース：テクスチャがバインドされ、実際の幅／高さが設定され、`iChannelResolution[n].z = 1.0`
- 存在しない／無効／None：フォールバックテクスチャがバインドされ、`iChannelResolution[n].xyz = (0,0,0)`

バッファーテクスチャ：

- 内部フォーマット：`RGBA16F`（浮動小数点）
- フィルタリング：リニア
- ラップ：クランプ・トゥ・エッジ

これは、`[0,1]`の範囲外の値を含むマルチパスデータに適しています。

## 9. 描画とブレンドに関する注意

- Bufferパスはブレンドなしでオフスクリーンに描画されます。
- 最終のImageパスでは、合成に`Enable Blending`設定が使用されます。
- Shadertoyラッパーはアルファに`fmOpacity`を自動適用します。
- 必要に応じて、Directシェーダーでは`fmOpacity`を手動で適用してください。

## 10. 実用的なテンプレート

## 10.1 最小限のShadertoy形式シェーダー

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord) {
    vec2 uv = fragCoord / iResolution.xy;
    vec3 col = vec3(uv, 0.5 + 0.5 * sin(iTime));
    fragColor = vec4(col, 1.0);
}
```

## 10.2 最小限のDirectフラグメントシェーダー

```glsl
out vec4 FragColor;

void main() {
    vec2 uv = gl_FragCoord.xy - fmAreaOffset;
    uv /= iResolution.xy;

    vec3 col = vec3(uv.x, uv.y, 0.5 + 0.5 * sin(iTime));
    FragColor = vec4(col, fmOpacity);
}
```

## 10.3 最小限のフィードバック付きマルチパス

### Buffer Aソース

ルート：`Buffer A iChannel0 Input -> Buffer A`

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord) {
    vec2 uv = fragCoord / iResolution.xy;
    vec4 prev = texture(iChannel0, uv);
    vec4 seed = vec4(uv, 0.0, 1.0);
    fragColor = mix(prev, seed, 0.02);
}
```

### Imageソース

ルート：`Image iChannel0 Input -> Buffer A`

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord) {
    vec2 uv = fragCoord / iResolution.xy;
    fragColor = texture(iChannel0, uv);
}
```

## 11. トラブルシューティングチェックリスト

- 出力がない：
  - Imageソースが空でないことを確認する
  - コンパイルモードがエントリーポイント（`mainImage`または`main`）に合っていることを確認する
- 紫色になる／テクスチャが無効：
  - リソースのバインドとチャンネルのルーティングを確認する
  - `iChannelResolution[n].z`を確認する（`0.0`は無効または利用不可を意味します）
- Directシェーダーで座標がずれる：
  - エリア内のローカル座標には`gl_FragCoord.xy - fmAreaOffset`を使用する
- ドラッグの動作がおかしい：
  - `Update iMouse Position Only While Holding LMB`の切り替えを使用する
- Directシェーダーで不透明度が適用されない：
  - アルファに`fmOpacity`を自分で乗算する
