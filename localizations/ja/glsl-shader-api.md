---
title: GLSL シェーダー API
description: FancyMenu の背景、要素、装飾オーバーレイ向けに GLSL シェーダーを記述します。
---

# FancyMenu GLSL シェーダー API

このドキュメントでは、FancyMenu が使用する GLSL ランタイムについて説明します。

- `GLSL` メニュー背景
- `GLSL` 要素
- `GLSL` 装飾オーバーレイ

ここでは、コンパイルモード、マルチパスのルーティング、対応ユニフォーム、実践的なシェーダー作成パターンを扱います。

## 1. ランタイム概要

FancyMenu は内部 OpenGL パイプライン（`#version 150`）でシェーダーを描画し、次をサポートします。

- シングルパスシェーダー（`Image` パスのみ）
- マルチパスシェーダー（`Buffer A` / `B` / `C` / `D` + `Image`）
- Shadertoy 風のエントリーポイント（`mainImage`）
- 直接フラグメントのエントリーポイント（`main`）

シェーダーソースはインラインのテキスト欄です。

- `Shader Source`（Image パス、描画に必須）
- `Buffer A Source`（任意）
- `Buffer B Source`（任意）
- `Buffer C Source`（任意）
- `Buffer D Source`（任意）

Image ソースが空の場合、描画は "no source" エラーで失敗します。

## 2. コンパイルモード

FancyMenu は 3 つのコンパイルモードをサポートします。

- `Auto`
- `Direct Fragment`
- `Shadertoy`

### 2.1 Shadertoy モード

期待されるエントリーポイント:

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord)
```

FancyMenu はこれを `main()` にラップし、ローカル領域座標を渡します。

```glsl
mainImage(fmColor_FancyMenu, gl_FragCoord.xy - fmAreaOffset);
```

このラッパーは、出力アルファに `fmOpacity` を掛けます。

### 2.2 Direct モード

期待されるエントリーポイント:

```glsl
void main()
```

互換動作:

- `gl_FragColor` 互換版を試行します。
- モダンな明示的 `out vec4` シェーダー向けに、非互換版も試行します。

Direct モードでは、`fmOpacity` は出力に自動適用されません。必要であれば手動で適用してください。

### 2.3 Auto モード

Auto は互換バリアント（Shadertoy/direct）を順に試し、最初にコンパイル成功したものを使用します。

## 3. ソースの前処理と組み込みマクロ

コンパイル前に、FancyMenu はソースを正規化します。

- UTF-8 BOM を削除
- CRLF/CR を LF に変換
- `#version ...` 行を削除
- `precision ...;` 行を削除

ランタイム注入のプレアンブルには次が含まれます。

- `#version 150`
- `in vec2 fmUv_FancyMenu`（全画面 UV、`[0,1]`、左下原点）
- `#define iGlobalTime iTime`
- `#define texture2D texture`
- `#define textureCube texture`

注意:

- ソース内に既知のユニフォーム名（例: `iTime`）がすでに宣言されている場合、FancyMenu は重複宣言を注入しません。
- それでも FancyMenu は実行時にその名前へ値を送信しようとします。
- `textureCube` はここではエイリアスマクロのみです。`iChannel0..3` は `sampler2D` ユニフォームです。

## 4. パスシステム（Image + Buffer A-D）

FancyMenu には 5 つのパススロットがあります。

- `Buffer A`
- `Buffer B`
- `Buffer C`
- `Buffer D`
- `Image`（最終的な画面描画パス）

挙動:

- Buffer パスは、ソースが空でない場合のみ実行されます。
- Image パスは、出力を描画するために必須です。
- Buffer は浮動小数点テクスチャ（`GL_RGBA16F`）に描画され、ピンポンされます（各フレームで read/write をスワップ）。

### 4.1 パスごとのチャネルルーティング

各パスは `iChannel0..3` のルーティングを公開します。各チャネルで選択できるのは次のいずれかです。

- `None`
- `Resource 0`
- `Resource 1`
- `Resource 2`
- `Resource 3`
- `Buffer A`
- `Buffer B`
- `Buffer C`
- `Buffer D`

Resource チャネルは `iChannel# Resource` 設定から取得されます。

デフォルト:

- すべての `iChannel` ルーティングは `None`
- どの Buffer パスも、その Buffer ソースが空でない限り有効になりません

重要:

- 同じ Buffer パスへのルーティング（フィードバック）は、前フレームのデータ（ピンポン read テクスチャ）を読みます。
- ルーティング先が欠落/無効の場合、フォールバックテクスチャがバインドされ、`iChannelResolution[n].z` は `0.0` になります。

## 5. 座標と領域セマンティクス

シェーダーは領域の矩形内で実行されます。

- メニュー背景: 画面全体領域
- GLSL 要素: 要素の矩形

座標規約:

- ピクセル系ユニフォームは、領域ローカルのピクセル単位です。
- シェーダー側のピクセル座標の Y 原点は左下です。
- マウス座標はクランプされません。カーソルが領域外にある場合、値も領域外になり得ます。

特別なフィールド:

- `fmAreaOffset`: 画面ピクセル空間における領域左下位置
- `fmAreaTopLeft`: 画面ピクセル空間における領域左上位置
- `fmAreaSize`: ピクセル単位の領域サイズ

## 6. ユニフォーム API リファレンス

以下のユニフォームはすべて、背景シェーダーと要素シェーダーの両方で利用できます。

## 6.1 Shadertoy 互換ユニフォーム

| Uniform | Type | 意味 |
|---|---|---|
| `iResolution` | `vec3` | `(areaWidthPx, areaHeightPx, 1.0)` |
| `iTime` | `float` | 累積シェーダー時間（秒） |
| `iTimeDelta` | `float` | 直近描画のデルタ時間。フリーズ/時間スケールの影響を受けます |
| `iFrameRate` | `float` | Minecraft FPS のフォールバック実行時 FPS |
| `iFrame` | `int` | ランタイムごとのフレームカウンター |
| `iMouse` | `vec4` | 詳細は下記参照 |
| `iDate` | `vec4` | `(year, month, day, secondsOfDayWithFraction)` |
| `iSampleRate` | `float` | 定数 `44100.0` |
| `iChannelTime[4]` | `float[4]` | 現在はすべて `iTime` に設定されます |
| `iChannelResolution[4]` | `vec3[4]` | チャネルごとの `(width, height, validFlag)` |
| `iChannel0..3` | `sampler2D` | ルーティングされたテクスチャ入力 |

### `iMouse` の詳細

`iMouse = vec4(x, y, z, w)`

- `x`, `y`: 現在の領域ローカルマウスピクセル位置、またはトグルが有効な場合はホールド/フリーズ動作
- `z`, `w`: 左クリックの起点
  - 左マウスボタン押下中は正
  - 離した後は負

トグルで制御される動作:

- `Update iMouse Position Only While Holding LMB = Off`:
  - `iMouse.xy` は継続的に更新されます
- `... = On`:
  - `iMouse.xy` は LMB 押下中のみ更新され、その後は最後にホールドした位置のまま保持されます

デフォルト値:

- `Off`（継続更新）

## 6.2 FancyMenu 固有のユニフォーム

| Uniform | Type | 意味 |
|---|---|---|
| `fmAreaOffset` | `vec2` | 画面空間における領域左下ピクセルオフセット |
| `fmAreaSize` | `vec2` | ピクセル単位の領域サイズ |
| `fmAreaPosition` | `vec2` | `fmAreaOffset` と同じ |
| `fmAreaTopLeft` | `vec2` | 画面空間における領域左上ピクセルオフセット |
| `fmScreenSize` | `vec2` | 画面全体のピクセルサイズ |
| `fmGuiScale` | `float` | 現在の GUI スケール |
| `fmMouse` | `vec4` | `(localPxX, localPxYBottom, localNormX, localNormY)` |
| `fmMouseDelta` | `vec2` | 領域ピクセル単位のマウス差分（Y はシェーダー上方向に反転済み） |
| `fmMouseButtons` | `ivec4` | ボタン `0..3` の押下状態 |
| `fmMouseClickCount` | `ivec4` | ボタン `0..3` の累積押下回数 |
| `fmMouseReleaseCount` | `ivec4` | ボタン `0..3` の累積リリース回数 |
| `fmMouseScroll` | `vec2` | このランタイムの前回描画以降のスクロール差分 |
| `fmMouseScrollTotal` | `vec2` | 累積スクロール量 |
| `fmKeyEvent` | `ivec4` | `(lastKeyCode, lastScanCode, lastModifiers, lastAction)` |
| `fmKeyEventCount` | `int` | 累積キーイベントカウンター |
| `fmCharEvent` | `ivec4` | `(lastCodePoint, lastModifiers, 0, 0)` |
| `fmCharEventCount` | `int` | 累積文字入力イベントカウンター |
| `fmDateParts` | `ivec4` | `(year, month, day, dayOfWeekIso1To7)` |
| `fmTimeParts` | `ivec4` | `(hour, minute, second, millisecondPart0To999)` |
| `fmDayOfYear` | `int` | 年内通算日 |
| `fmWeekOfYear` | `int` | ISO 週番号 |
| `fmUnixTimeSeconds` | `int` | Unix エポック秒 |
| `fmUnixTimeMilliseconds` | `int` | 現在時刻のミリ秒部分（`0..999`） |
| `fmPartialTick` | `float` | 現在の部分ティック |
| `fmGameDeltaTicks` | `float` | Minecraft のゲーム側デルタティック |
| `fmRealtimeDeltaTicks` | `float` | Minecraft のリアルタイム側デルタティック |
| `fmInWorld` | `int` | ワールド内なら `1`、それ以外は `0` |
| `fmIsPaused` | `int` | 一時停止中なら `1`、それ以外は `0` |
| `fmOpacity` | `float` | 実効不透明度マルチプライヤー（`0..1`） |
| `fmVariableCount` | `int` | 現在の FancyMenu 変数数 |

キーアクション値（`fmKeyEvent.w`）:

- `0` = release
- `1` = press
- `2` = repeat

## 6.3 FancyMenu 変数ユニフォーム API

FancyMenu 変数は、値が変わってもシェーダー再コンパイルなしで、ランタイムユニフォームとして直接公開されます（背景、要素、装飾オーバーレイ シェーダー向け）。

### 命名

各変数 `<name>` について、FancyMenu は次を公開します。

- `fmVarFloat_<name>`
- `fmVarInt_<name>`
- `fmVarBool_<name>`
- `fmVarVec2_<name>`
- `fmVarVec3_<name>`
- `fmVarVec4_<name>`
- `fmVarExists_<name>`（`1` = 現在その変数が存在する、`0` = 存在しない/削除済み）

`<name>` のユニフォーム接尾辞のサニタイズ:

- 使用可能文字は `[A-Za-z0-9_]`
- それ以外の文字はすべて `_` に変換されます
- 先頭文字が数字の場合は、`_` が前置されます

例:

- 変数 `player_hp` -> 接尾辞 `player_hp`
- 変数 `player-hp` -> 接尾辞 `player_hp`
- 変数 `2nd_phase` -> 接尾辞 `_2nd_phase`

重要:

- これらの動的変数ユニフォームは、シェーダーソース内で **自動宣言されません**（使用するものは手動で宣言してください）
- 同じ接尾辞にサニタイズされる変数名は避けてください。GLSL ユニフォーム名が同一になるためです

### 値の変換

変数のテキスト値 `v` に対して:

- `fmVarFloat_*`: float として解析（失敗時は `0.0`）
- `fmVarInt_*`: int として解析（失敗時は `0`）
- `fmVarBool_*`: 真偽/int 解釈（`true/yes/on/enabled` => `1`、`false/no/off/disabled` => `0`、それ以外は数値の非ゼロ => `1`）
- ベクトル解析が受け付ける区切り: 空白、`,`、`;`、`|`
  - `fmVarVec2_*`: 先頭 2 成分
  - `fmVarVec3_*`: 先頭 3 成分
  - `fmVarVec4_*`: 先頭 4 成分
  - 成分が不足する場合は、最後に解析された成分を欠損スロットへ繰り返します
  - 数値成分が 1 つもない場合は、すべてのベクトル成分にスカラーフォールバックを使用します

変数が削除された場合:

- `fmVarExists_*` は `0` になります
- 対応するすべての `fmVar*_*` 値は `0` にリセットされます

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

## 7. 入力追跡モデル

FancyMenu は入力をグローバルに追跡し、各描画ごとにスナップショットを取ります。

- マウス移動/ドラッグ
- マウス押下/解放
- スクロール
- キー押下/解放/リピート
- 文字入力

マウスの堅牢性:

- ランタイムは、ボタンが押しっぱなしのまま固まるのを防ぐため、各フレームで GLFW のポーリングとボタン状態を照合します。

`Pass Input Events To Shader` が無効の場合:

- 入力ユニフォームは毎フレーム中立値にリセットされます
- カウンターとイベントはシェーダーから見えるデータ内で 0 にされます

## 8. テクスチャ入力の詳細

Resource チャネル（`iChannel# Resource`）は 2D テクスチャを想定します。

チャネルごとのテクスチャ状態:

- 有効な resource: バインド済みテクスチャ、実際の幅/高さ、`iChannelResolution[n].z = 1.0`
- 欠落/無効/None: フォールバックテクスチャ、`iChannelResolution[n].xyz = (0,0,0)`

Buffer テクスチャ:

- 内部フォーマット: `RGBA16F`（浮動小数点）
- フィルタリング: linear
- wrap: clamp-to-edge

これは、`[0,1]` の外側の値も含むマルチパスデータに適しています。

## 9. レンダリングとブレンドに関する注意

- Buffer パスはブレンドなしでオフスクリーン描画されます。
- 最終 Image パスは合成のために `Enable Blending` 設定を使用します。
- Shadertoy ラッパーは、`fmOpacity` を自動的にアルファへ適用します。
- Direct シェーダーでは、必要に応じて `fmOpacity` を手動で適用してください。

## 10. 実用テンプレート

## 10.1 最小の Shadertoy 風シェーダー

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord) {
    vec2 uv = fragCoord / iResolution.xy;
    vec3 col = vec3(uv, 0.5 + 0.5 * sin(iTime));
    fragColor = vec4(col, 1.0);
}
```

## 10.2 最小の直接フラグメントシェーダー

```glsl
out vec4 FragColor;

void main() {
    vec2 uv = gl_FragCoord.xy - fmAreaOffset;
    uv /= iResolution.xy;

    vec3 col = vec3(uv.x, uv.y, 0.5 + 0.5 * sin(iTime));
    FragColor = vec4(col, fmOpacity);
}
```

## 10.3 最小のフィードバック・マルチパス

### Buffer A ソース

ルート: `Buffer A iChannel0 Input -> Buffer A`

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord) {
    vec2 uv = fragCoord / iResolution.xy;
    vec4 prev = texture(iChannel0, uv);
    vec4 seed = vec4(uv, 0.0, 1.0);
    fragColor = mix(prev, seed, 0.02);
}
```

### Image ソース

ルート: `Image iChannel0 Input -> Buffer A`

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord) {
    vec2 uv = fragCoord / iResolution.xy;
    fragColor = texture(iChannel0, uv);
}
```

## 11. トラブルシューティング チェックリスト

- 出力がない:
  - Image ソースが空でないか確認する
  - コンパイルモードがエントリーポイント（`mainImage` vs `main`）と一致しているか確認する
- 紫色/無効なテクスチャ:
  - resource バインディングとチャネルルーティングを確認する
  - `iChannelResolution[n].z` を確認する（`0.0` は無効/利用不可を意味します）
- Direct シェーダーで座標がおかしい:
  - ローカル領域座標には `gl_FragCoord.xy - fmAreaOffset` を使う
- ドラッグ挙動がおかしい:
  - `Update iMouse Position Only While Holding LMB` トグルを使う
- Direct シェーダーで不透明度が適用されない:
  - `fmOpacity` を自分でアルファに掛ける
