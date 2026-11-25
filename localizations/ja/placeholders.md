---
title: プレースホルダー
description: テキスト内にプレイヤー名、時刻、サーバーのプレイヤー数などのリアルタイム値や、FancyMenuで使えるすべてのプレースホルダーを表示します。
sourceBlobSha: 951d7772d640bc6b19d6f4dcc2fef4adcd1f13aa
---

# プレースホルダー

プレースホルダーは、FancyMenuがプレイヤー名、時刻、サーバーのプレイヤー数などのリアルタイム値に置き換える短いコードです。要素のテキスト、ボタンラベル、ツールチップ、アクションや要件の値、その他のほとんどの入力可能なテキストで使用できます。

<img width="800" alt="レイアウトエディターでテキスト要素にプレイヤー名プレースホルダーを追加する様子：テキストエディターのプレースホルダー、Playerカテゴリー、プレイヤー名で挨拶するテキスト" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/placeholders_add.gif?raw=true">

> [!TIP]
> 独自の[変数](/variables)も、`$$`と変数名を使って同じテキスト内で利用できます（例：`$$coins`）。

# プレースホルダーの追加

1. [テキスト要素](/text-in-menus)の**Text Content**など、テキストエディターでテキストを開きます。アクションの値など、ウィンドウ内のテキストフィールドには、横に**Open in Editor**ボタンがあります。
2. プレースホルダーを挿入する位置をクリックします。
3. テキストエディターの右上にある**Placeholders**をクリックします。
4. カテゴリーをクリックするか、名前、識別子、説明で検索します。**BACK**をクリックするとカテゴリー一覧に戻ります。カテゴリーのないプレースホルダーは、カテゴリーの下に表示されます。
5. プレースホルダーにマウスを合わせて機能を確認し、クリックして追加します。
6. **Mod Version**のmod IDなど、例として入っている値を置き換えます。

テキストエディターに**Placeholders**ボタンがないテキストでは、プレースホルダーを使用できません。

# プレースホルダーの仕組み

プレースホルダーは次のような形式です。

```
{"placeholder":"playername"}
```

設定値のあるプレースホルダーでは、値を`values`に指定します。

```
{"placeholder":"modversion","values":{"modid":"fancymenu"}}
```

- `playername`のような識別子は大文字と小文字を区別します。以下では各プレースホルダーの識別子と値を記載しています。
- 値の順番は問いません。省略可能と記載されている値は省略できます。
- 誤字のあるものなど、FancyMenuが置き換えられないプレースホルダーは、入力したままテキストに残ります。
- プレースホルダーが返す値は常にテキストです。表示する値がない場合は、`0`、`0.0`、`---`、または空の値など、代替値を返します。
- [書式コード](/text-formatting)はプレースホルダーの前後でも使えます。`&6{"placeholder":"playername"}`なら名前が金色で表示されます。

> [!IMPORTANT]
> プレースホルダーはJSONのように見えますが、JSONではありません。プレースホルダーの中に別のプレースホルダーを含めると有効なJSONにならないため、JSONフォーマッターやバリデーターにかけないでください。

## プレースホルダーの中にプレースホルダーを入れる

値には、別のプレースホルダーや[変数](/variables#showing-variables-in-text)を含められます。FancyMenuは内側のものから先に置き換えます。値の中の引用符をエスケープする必要はありません。

次の例では、最大RAMの単位をMBからGBに変換します。

```
{"placeholder":"calc","values":{"decimal":"true","expression":"{"placeholder":"maxram"} / 1024"}}
```

次の例では、変数`rank`を大文字で表示します。

```
{"placeholder":"uppercase_text","values":{"text":"$$rank"}}
```

[**File Text**](#file-text)で読み込んだファイルのように、プレースホルダーがプレースホルダーを含むテキストを返す場合、FancyMenuはその中のプレースホルダーも置き換えます。

# 知っておくと便利なこと

- プレースホルダーは自動的に更新されます。FancyMenuは置き換え後のテキストを30ミリ秒保持してから、プレースホルダーを再度置き換えます。この値は**menu bar -> Customization -> Settings**の**Placeholder Caching Duration [MS]**で変更できます。`0`にすると毎フレーム置き換えるため、パフォーマンスへの負荷が高くなります。
- **Web Text**や**Server Status**のように、ウェブサイト、ファイル、サーバーを読み取るプレースホルダーはバックグラウンドで読み込みます。読み込みが終わるまでは、空の値か代替値を返します。
- [アクション](/action-scripts)内のプレースホルダーは、アクションの実行時点の値を取得します。
- ワールド、画面、要素に関するプレースホルダーは、ゲームのメインスレッドでのみ動作します。バックグラウンド（非同期）で実行する[Ticker](/elements#ticker)では、代わりにエラーが表示されます。
- **Random Number**はテキストが更新されるたびに新しい数値を返します。値を固定するには、[**Set Variable Value (FM Variable)**](/action-scripts#set-variable-value-fm-variable)で[変数](/variables)に保存します。

> [!CAUTION]
> **JSON Parser**、**File Text**、**Clipboard Content**などのプレースホルダーは、ゲームフォルダー内のファイルやクリップボードを読み取ることができます。ウェブサイトにアクセスするアクションと組み合わせると、レイアウトからデータを外部に送信できてしまいます。信頼できるレイアウトのみを使用してください。

# 例

## ウェルカムパネル

<img width="800" alt="プレイヤー名で挨拶し、Minecraftのバージョン、modの数、時刻を表示するテキスト要素" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/placeholders_welcome.png?raw=true">

```
### おかえりなさい、{"placeholder":"playername"}！
Minecraft {"placeholder":"mcversion"}、{"placeholder":"loadedmods"}個のmod
現在の時刻：{"placeholder":"realtimehour"}:{"placeholder":"realtimeminute"}
```

## サーバーの状態とプレイヤー数

```
サバイバル：{"placeholder":"serverstatus","values":{"ip":"play.example.net"}}&r、プレイヤー数：{"placeholder":"serverplayercount","values":{"ip":"play.example.net"}}
```

## 日付と時刻

```
{"placeholder":"realtimeday"}.{"placeholder":"realtimemonth"}.{"placeholder":"realtimeyear"}、{"placeholder":"realtimehour"}:{"placeholder":"realtimeminute"}
```

## RAM使用量

```
RAM：{"placeholder":"usedram"} / {"placeholder":"maxram"} MB（{"placeholder":"percentram"}%）
```

# すべてのプレースホルダー

FancyMenuで使用できるすべてのプレースホルダーです。プレースホルダーメニューの大きな**Advanced**カテゴリーと**World**カテゴリーは、ここではより小さなグループに分けてあります。

## 変数とリスト

これらは**Advanced**カテゴリーにあります。変数やリストの作成方法については[変数](/variables)を参照してください。

### Get Variable Value (FM Variable)

**識別子：** `getvariable`

変数の値を取得します。変数が空か存在しない場合は`0`を返すため、数値に適しています。リストの場合は、`["Steve","Alex"]`のようなJSON配列形式ですべての項目を返します。

- `name`：変数名（`$$`は付けません）

```
{"placeholder":"getvariable","values":{"name":"clicks"}}
```

### Get List Entry (FM Variable)

**識別子：** `list_get`

リスト変数から項目を1つ取得します。

- `name`：リスト名
- `index`：項目の位置。最初の項目は`0`です。負の数は末尾から数え、`-1`は最後の項目です。
- `fallback`（省略可能）：指定した位置に項目がない場合や、指定した名前のリストがない場合に返す値。既定では空です。

```
{"placeholder":"list_get","values":{"name":"tips","index":"0","fallback":"No tips yet"}}
```

### List Size (FM Variable)

**識別子：** `list_size`

リストの項目数を返します。指定した名前のリストがない場合は`0`です。

- `name`：リスト名

```
{"placeholder":"list_size","values":{"name":"tips"}}
```

### Index of List Entry (FM Variable)

**識別子：** `list_index_of`

リスト全体の中で`value`と一致する最初の項目のインデックスを返します。該当項目がない場合は`-1`です。

- `name`：リスト名
- `value`：検索する項目
- `ignore_case`（省略可能）：`true`にすると`Apple`と`apple`を一致とみなします。既定値は`false`です。

```
{"placeholder":"list_index_of","values":{"name":"read_news","value":"news_42","ignore_case":"false"}}
```

### Join List Entries (FM Variable)

**識別子：** `list_join`

リストのすべての項目を1つのテキストにまとめます。指定した名前のリストがない場合は空です。

- `name`：リスト名
- `separator`（省略可能）：項目間に入れるテキスト。`\n`は改行です。既定値は`, `です。

```
{"placeholder":"list_join","values":{"name":"tips","separator":"\n"}}
```

## 数学

これらは**Advanced**カテゴリーにあります。小数点にはピリオドを使います（例：`2.5`）。

### Calculator

**識別子：** `calc`

`2 + 3 * 4`のような数式を計算します。

- `expression`：計算する数式
- `decimal`（省略可能）：`false`にすると結果を整数に丸めます。既定値は`true`で、`14.0`のような結果を返します。

```
{"placeholder":"calc","values":{"decimal":"false","expression":"{"placeholder":"usedram"} * 100 / {"placeholder":"maxram"}"}}
```

| 式で使うもの | 機能 |
|---|---|
| `+` `-` `*` `/` | 加算、減算、乗算、除算 |
| `^` | べき乗。例：`2 ^ 3`は8 |
| `%` | 剰余。例：`7 % 3`は1 |
| `( )` | 計算順序をグループ化。例：`(2 + 3) * 4` |
| `pi`, `e` | πとeの値 |
| `abs(x)` | xの絶対値 |
| `sqrt(x)`, `cbrt(x)` | 平方根、立方根 |
| `pow(x, y)` | xのy乗 |
| `floor(x)`, `ceil(x)` | 切り捨て、切り上げ |
| `sin(x)`, `cos(x)`, `tan(x)`, `cot(x)` | 三角関数。角度の単位はラジアン |
| `asin(x)`, `acos(x)`, `atan(x)` | 逆三角関数 |
| `sinh(x)`, `cosh(x)`, `tanh(x)` | 双曲線関数 |
| `log(x)`, `log2(x)`, `log10(x)` | 底がe、2、10の対数 |
| `exp(x)` | eのx乗 |
| `signum(x)` | [**Sign (Math)**](#sign-math)と同様に`1`、`-1`、`0`を返します |

### Random Number

**識別子：** `random_number`

`min`から`max`までのランダムな整数を返します。テキストが更新されるたびに値が変わります。

- `min`、`max`：最小値と最大値

```
{"placeholder":"random_number","values":{"min":"1","max":"6"}}
```

### Max Number

**識別子：** `maxnum`

2つの数値のうち、大きい方を返します。

- `first`、`second`：数値

```
{"placeholder":"maxnum","values":{"first":"$$score","second":"$$best_score"}}
```

### Min Number

**識別子：** `minnum`

2つの数値のうち、小さい方を返します。

- `first`、`second`：数値

```
{"placeholder":"minnum","values":{"first":"10","second":"15"}}
```

### Absolute Number

**識別子：** `absnum`

数値の絶対値を返します。たとえば`-10.5`は`10.5`になります。

- `num`：数値

```
{"placeholder":"absnum","values":{"num":"-10.5"}}
```

### Negate Number

**識別子：** `negnum`

正の数を負の数にします。たとえば`10.5`は`-10.5`になります。0と負の数はそのままです。

- `num`：数値

```
{"placeholder":"negnum","values":{"num":"10.5"}}
```

### Round (Math)

**識別子：** `math_round`

数値を四捨五入します。`2.5`は`3`になります。

- `num`：数値
- `decimals`（省略可能）：小数点以下の桁数。たとえば`2`にすると`3.14159`は`3.14`になります。`0`、`-1`、または省略した場合は整数に丸めます。

```
{"placeholder":"math_round","values":{"num":"3.14159","decimals":"2"}}
```

### Floor (Math)

**識別子：** `math_floor`

数値を整数に切り下げます。たとえば`3.7`は`3`、`-3.2`は`-4`になります。

- `num`：数値

```
{"placeholder":"math_floor","values":{"num":"3.7"}}
```

### Ceiling (Math)

**識別子：** `math_ceil`

数値を整数に切り上げます。たとえば`3.2`は`4`、`-3.7`は`-3`になります。

- `num`：数値

```
{"placeholder":"math_ceil","values":{"num":"3.2"}}
```

### Sign (Math)

**識別子：** `math_sign`

正の数には`1`、負の数には`-1`、0には`0`を返します。

- `num`：数値

```
{"placeholder":"math_sign","values":{"num":"-3.14"}}
```

### *pi* (Math)

**識別子：** `math_pi`

円周率πの値`3.141592653589793`を返します。

```
{"placeholder":"math_pi"}
```

### Trigonometric Sine (Math)

**識別子：** `math_sin`

ラジアン単位の角度の正弦を返します。度数法を使う場合は、Calculatorで先にπ / 180を掛けてください。

- `angle`：ラジアン単位の角度

```
{"placeholder":"math_sin","values":{"angle":"1.5707963267948966"}}
```

### Trigonometric Cosine (Math)

**識別子：** `math_cos`

ラジアン単位の角度の余弦を返します。

- `angle`：ラジアン単位の角度

```
{"placeholder":"math_cos","values":{"angle":"0"}}
```

### Trigonometric Tangent (Math)

**識別子：** `math_tan`

ラジアン単位の角度の正接を返します。

- `angle`：ラジアン単位の角度

```
{"placeholder":"math_tan","values":{"angle":"0.7853981633974483"}}
```

### Hyperbolic Sine (Math)

**識別子：** `math_sinh`

数値の双曲線正弦を返します。

- `num`：数値

```
{"placeholder":"math_sinh","values":{"num":"1"}}
```

### Hyperbolic Cosine (Math)

**識別子：** `math_cosh`

数値の双曲線余弦を返します。

- `num`：数値

```
{"placeholder":"math_cosh","values":{"num":"1"}}
```

### Hyperbolic Tangent (Math)

**識別子：** `math_tanh`

数値の双曲線正接を返します。

- `num`：数値

```
{"placeholder":"math_tanh","values":{"num":"1"}}
```

### Number Base Converter

**識別子：** `number_base_convert`

10進数から2進数や16進数など、数値を別の基数に変換します。小数にも対応し、小数点以下は最大16桁です。変換結果の英字は大文字（例：`FF`）になります。

- `input`：数値
- `from_base`（省略可能）：`input`の基数。`2`から`36`まで指定できます。既定値は`10`です。
- `to_base`（省略可能）：変換後の基数。`2`から`36`まで指定できます。既定値は`10`です。

```
{"placeholder":"number_base_convert","values":{"input":"255","from_base":"10","to_base":"16"}}
```

## テキスト

これらは**Advanced**カテゴリーにあります。

### Uppercase Text

**識別子：** `uppercase_text`

テキストをすべて大文字にします。`Hello World`は`HELLO WORLD`になります。`&a`などの[書式コード](/text-formatting)はそのまま残ります。

- `text`：テキスト

```
{"placeholder":"uppercase_text","values":{"text":"Hello World"}}
```

### Lowercase Text

**識別子：** `lowercase_text`

テキストをすべて小文字にします。`HELLO WORLD`は`hello world`になります。書式コードはそのまま残ります。

- `text`：テキスト

```
{"placeholder":"lowercase_text","values":{"text":"HELLO WORLD"}}
```

### Title Case Text

**識別子：** `title_case_text`

各単語の先頭を大文字にします。`hello world`は`Hello World`になります。書式コードはそのまま残ります。

- `text`：テキスト

```
{"placeholder":"title_case_text","values":{"text":"hello world"}}
```

### Sentence Case Text

**識別子：** `sentence_case_text`

各文の先頭を大文字にします。`hello world. this is fancymenu!`は`Hello world. This is fancymenu!`になります。書式コードはそのまま残ります。

- `text`：テキスト

```
{"placeholder":"sentence_case_text","values":{"text":"hello world. this is fancymenu!"}}
```

### Snake Case Text

**識別子：** `snake_case_text`

小文字に変換し、単語の間に`_`を入れます。`Hello World`は`hello_world`になります。書式コードは削除されます。

- `text`：テキスト

```
{"placeholder":"snake_case_text","values":{"text":"Hello World"}}
```

### Kebab Case Text

**識別子：** `kebab_case_text`

小文字に変換し、単語の間に`-`を入れます。`Hello World`は`hello-world`になります。書式コードは削除されます。

- `text`：テキスト

```
{"placeholder":"kebab_case_text","values":{"text":"Hello World"}}
```

### Alternating Case Text

**識別子：** `alternating_case_text`

小文字と大文字を交互にします。`alternating case`は`aLtErNaTiNg CaSe`になります。

- `text`：テキスト

```
{"placeholder":"alternating_case_text","values":{"text":"alternating case"}}
```

### Toggle Case Text

**識別子：** `toggle_case_text`

小文字を大文字に、大文字を小文字に変換します。`Toggle Case`は`tOGGLE cASE`になります。

- `text`：テキスト

```
{"placeholder":"toggle_case_text","values":{"text":"Toggle Case"}}
```

### Trim Text

**識別子：** `trim_text`

テキストの先頭と末尾にある空白を削除します。途中の空白はそのまま残ります。

- `text`：テキスト

```
{"placeholder":"trim_text","values":{"text":"  Welcome!  "}}
```

### Crop Text

**識別子：** `crop_text`

テキストの先頭と末尾から指定した文字数を削除します。`hello world`の両端から1文字ずつ削除すると`ello worl`になります。

- `text`：テキスト
- `remove_from_start`：先頭から削除する文字数
- `remove_from_end`：末尾から削除する文字数

```
{"placeholder":"crop_text","values":{"text":"hello world","remove_from_start":"1","remove_from_end":"1"}}
```

### Split Text

**識別子：** `split_text`

テキストを分割し、その一部を返します。`Steve,Alex,Notch`を`,`で分割すると、パート`1`として`Alex`を取得できます。

- `input`：テキスト
- `regex`：正規表現で指定する分割位置。`.`、`|`、`?`などの文字の前には`\`を付けます（例：`\.`）。
- `max_parts`（省略可能）：分割後のパート数の上限。既定値は`-1`で、すべての一致箇所で分割します。
- `split_index`：取得するパート。最初のパートは`0`です。

```
{"placeholder":"split_text","values":{"input":"Steve,Alex,Notch","regex":",","max_parts":"-1","split_index":"1"}}
```

### Replace Text

**識別子：** `replace_text`

テキストの一部を置き換えます。`Hello World!`の`World`を`FancyMenu`に置き換えると、`Hello FancyMenu!`になります。

- `text`：テキスト
- `search`：検索する文字列
- `replacement`（省略可能）：置き換える文字列。既定値は空で、一致した部分を削除します。
- `use_regex`（省略可能）：`true`にすると、`search`を正規表現として扱います。その場合、`replacement`内の`$1`、`$2`などは一致したグループを表します。既定値は`false`です。
- `replace_all`（省略可能）：`false`にすると最初の一致のみを置き換えます。既定値は`true`です。

```
{"placeholder":"replace_text","values":{"text":"Hello World!","search":"World","replacement":"FancyMenu","use_regex":"false","replace_all":"true"}}
```

### Switch Case

**識別子：** `switch_case`

値に一致するケースの結果を返します。変数`difficulty_level`が`2`の場合、次の例では`Hard Mode`を返します。

- `value`：照合する値
- `cases`：値と結果のペア。例：`1:Easy Mode,2:Hard Mode`。値と結果には`,`または`:`を含められません。
- `default`（省略可能）：どのケースにも一致しない場合の結果。指定しない場合、プレースホルダーはそのまま残ります。

```
{"placeholder":"switch_case","values":{"value":"$$difficulty_level","cases":"1:Easy Mode,2:Hard Mode","default":"Normal Mode"}}
```

### Localize Text

**識別子：** `local`

ゲームの現在の言語におけるローカライズキーのテキストを返します。たとえば、`menu.singleplayer`は`Singleplayer`になります。Minecraftやmodのキーに加え、独自のキーも使用できます（[ローカライズ](/localization)を参照）。

- `key`：ローカライズキー

```
{"placeholder":"local","values":{"key":"menu.singleplayer"}}
```

### Stringify

**識別子：** `stringify`

テキスト内のプレースホルダーを置き換えた後、すべての`"`、`{`、`}`の前に`\`を挿入します。これにより、ウェブサイトなど外部から取得したテキストがプレースホルダーとして解釈されるのを防げます。

- `text`：テキスト

```
{"placeholder":"stringify","values":{"text":"{"placeholder":"webtext","values":{"link":"https://example.com/motd.txt"}}"}}
```

## データとファイル

これらは**Advanced**カテゴリーにあります。ローカルパスは`/config/fancymenu/assets/news.txt`のようにゲームフォルダーを起点とし、ゲームフォルダーの外には移動できません（[リソース](/resources#local-resources)を参照）。

### JSON Parser

**識別子：** `json`

JSONから値を読み取ります。結果が複数ある場合は、1行に1つずつ表示します。

- `source`：JSONテキスト、ゲームフォルダー内のJSONファイル、またはJSONファイルのURL
- `json_path`：`$.name`や`$.players[0].name`のように、値へのパスを指定します。JSONパスの詳細は[json.fancymenu.net](https://json.fancymenu.net)を参照してください。

```
{"placeholder":"json","values":{"source":"https://example.com/server_info.json","json_path":"$.news.title"}}
```

ウェブ上のJSONは一度読み込まれ、FancyMenuの再読み込み時に再度読み込まれます。ファイルの変更はすぐに反映されます。

| パス | 取得する値 |
|---|---|
| `$.name` | 最上位にある`name` |
| `$.player.level` | `player`内の`level` |
| `$.items[0].id` | `items`の最初の項目にある`id` |
| `$.scores.*` | `scores`内のすべての値 |

### File Text

**識別子：** `file_text`

ファイルまたはURLのテキストを取得します。ファイルは1秒ごと、URLは10秒ごとに再読み込みされます。読み込み中、または読み取れない場合は空の値を返します。

- `path_or_url`：ゲームフォルダー内のファイル、またはURL。`.minecraft/`で始まるパスは既定のMinecraftフォルダーを指します。
- `mode`（省略可能）：全文を取得する場合は`all`、末尾の行を取得する場合は`last`。既定値は`all`です。
- `separator`（省略可能）：行の間に入れるテキスト。既定値は改行の`\n`です。
- `last_lines`（省略可能）：`last`で取得する行数。既定値は`1`です。

```
{"placeholder":"file_text","values":{"path_or_url":"/config/fancymenu/assets/changelog.txt","mode":"all","separator":"\n","last_lines":"1"}}
```

### File Size

**識別子：** `file_size`

ファイルサイズをバイト単位で返します。ファイルが存在しない場合は`0`です。`.minecraft/`で始まるパスは既定のMinecraftフォルダーを指します。

- `path`：ファイル

```
{"placeholder":"file_size","values":{"path":"/config/fancymenu/assets/news.txt"}}
```

### File MD5

**識別子：** `file_md5`

ファイルのMD5ハッシュを返します（例：`d41d8cd98f00b204e9800998ecf8427e`）。ファイルが存在しない場合は空です。`.minecraft/`で始まるパスは既定のMinecraftフォルダーを指します。

- `path`：ファイル

```
{"placeholder":"file_md5","values":{"path":"/config/fancymenu/assets/menu_music.ogg"}}
```

### Encode To Base64

**識別子：** `base64_encode`

テキストをBase64に変換します。`Hello World`は`SGVsbG8gV29ybGQ=`になります。

- `text`：テキスト

```
{"placeholder":"base64_encode","values":{"text":"Hello World"}}
```

### Decode From Base64

**識別子：** `base64_decode`

Base64をテキストに戻します。`SGVsbG8gV29ybGQ=`は`Hello World`になります。

- `text`：Base64テキスト

```
{"placeholder":"base64_decode","values":{"text":"SGVsbG8gV29ybGQ="}}
```

### Get NBT Data (Client-Side)

**識別子：** `nbt_data_get`

`/data get`のように、ゲームがワールドについて把握している情報からNBTデータを読み取ります。処理は高速ですが、サーバーはすべての情報をプレイヤーに送信するわけではありません。

- `source_type`：`entity`または`block`
- `entity_selector`：`entity`の場合に使うセレクター。`@s`（自分）、`@p`、`@e[type=minecraft:horse,limit=1,sort=nearest]`、またはエンティティの名前やUUIDを指定します。セレクターでは`type`、`name`、`tag`、`limit`、`sort`、`distance`、`x`、`y`、`z`、`dx`、`dy`、`dz`を使用できます。最初に一致した対象が使われます。
- `block_pos`：`block`の場合に指定するブロックエンティティ（チェストなど）の座標。例：`120 64 -35`
- `nbt_path`：`foodLevel`や`Inventory[0].id`のようなNBTパス
- `scale`（省略可能）：数値に掛ける倍率。既定値は`1.0`です。
- `return_type`（省略可能）：`value`（数値とテキストをそのまま返す）、`string`、`snbt`、`json`のいずれか。既定値は`value`です。

```
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"foodLevel","scale":"1.0","return_type":"value"}}
```

### Get NBT Data (Server-Side)

**識別子：** `nbt_data_get_server`

`/data get`と同じ方法で、サーバーからNBTデータを読み取ります。サーバーにもFancyMenuが必要です。シングルプレイでは常に動作します。サーバーから応答があるまでは空の値を返し、その後は約100ミリ秒ごとに更新されます。

- `source_type`：`entity`、`block`、`storage`のいずれか
- `entity_selector`：`entity`の場合に使うセレクター。`@s`や`@e[type=minecraft:villager,limit=1,sort=nearest]`など、`/data get`でエンティティを1体だけ取得できるものを指定します。
- `block_pos`：`block`の場合に指定する座標。`120 64 -35`、`~ ~-1 ~`、`^ ^ ^1`などを指定できます。
- `storage_id`：`storage`の場合に指定するコマンドストレージのID（例：`mypack:quests`）。
- `nbt_path`（省略可能）：NBTパス。指定しない場合はすべてのデータを取得します。
- `scale`（省略可能）：数値に掛ける倍率。既定値は`1.0`です。
- `return_type`（省略可能）：`value`、`string`、`snbt`、`json`のいずれか。既定値は`value`です。

```
{"placeholder":"nbt_data_get_server","values":{"source_type":"storage","storage_id":"mypack:quests","nbt_path":"completed","return_type":"value"}}
```

## オーディオ

開いているメニューの[Audio要素](/elements#audio)の情報を取得します。レイアウトエディターでAudio要素を右クリックし、**Copy Element ID**をクリックすると、そのIDをコピーできます。

### Audio Element Volume

**識別子：** `audio_element_vol`

Audio要素の音量を返します。範囲は`0.0`（0%）から`1.0`（100%）です。

- `element_identifier`：Audio要素のID

```
{"placeholder":"audio_element_vol","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Current Audio Track

**識別子：** `audio_element_current_track`

現在再生中のトラックのファイル名を返します（例：`menu_theme.ogg`）。トラックが再生されていない場合は`---`です。

- `element_identifier`：Audio要素のID
- `display_name_mappings`（省略可能）：ファイル名の代わりに表示する名前。ファイル名と表示名の間は`=>`、各ペアの間は`%:%`で区切ります。

```
{"placeholder":"audio_element_current_track","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","display_name_mappings":"menu_theme.ogg=>Menu Theme%:%credits.ogg=>Credits Theme"}}
```

### Audio Duration

**識別子：** `audio_duration`

現在のトラックの長さを返します（例：`03:45`）。読み込み中は`00:00`です。

- `element_identifier`：Audio要素のID

```
{"placeholder":"audio_duration","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Audio Play Time

**識別子：** `audio_playtime`

現在のトラックの再生位置を返します（例：`01:30`）。停止中は`00:00`（または`0`）です。

- `element_identifier`：Audio要素のID
- `show_percentage`（省略可能）：`true`にすると、代わりに`0`から`100`までの進捗率を返します。既定値は`false`です。

```
{"placeholder":"audio_playtime","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","show_percentage":"false"}}
```

### Audio Playing State

**識別子：** `audio_playing_state`

Audio要素の再生中は`true`、一時停止中または停止中は`false`を返します。

- `element_identifier`：Audio要素のID

```
{"placeholder":"audio_playing_state","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

## クライアント

ゲームとそのmodに関する情報です。

### Minecraft Version

**識別子：** `mcversion`

Minecraftのバージョンを返します（例：`1.21.1`）。

```
{"placeholder":"mcversion"}
```

### Mod Loader Name

**識別子：** `loadername`

modローダーの名前を返します（例：`Fabric`、`NeoForge`）。

```
{"placeholder":"loadername"}
```

### Mod Loader Version

**識別子：** `loaderver`

modローダーのバージョンを返します（例：`0.16.14`）。

```
{"placeholder":"loaderver"}
```

### Mod Version

**識別子：** `modversion`

インストール済みmodのバージョンを返します（例：`3.11.0`）。modがインストールされていない場合は`0.0.0`です。

- `modid`：modのID（例：`fancymenu`）

```
{"placeholder":"modversion","values":{"modid":"fancymenu"}}
```

### Active Mods Count

**識別子：** `loadedmods`

読み込まれているmodの数を返します。ライブラリや他のmodに含まれるmodも数えるため、modファイルの数より多くなることがあります。

```
{"placeholder":"loadedmods"}
```

### Total Mods Count

**識別子：** `totalmods`

インストールされているmodの概数を返します。ゲーム起動時に`mods`フォルダー内の`.jar`ファイルから数えます。**Active Mods Count**の数より小さくなることはありません。

```
{"placeholder":"totalmods"}
```

### World Loading Progress

**識別子：** `world_load_progress`

ワールドの読み込み中に、読み込み画面が表示されている間の進捗を`0`から`100`で返します。プログレスバーに適しています。それ以外の画面では`0`です。

```
{"placeholder":"world_load_progress"}
```

### Minecraft Option Value

**識別子：** `minecraft_option_value`

ゲームフォルダー内の`options.txt`に保存されているMinecraft設定の値を返します。たとえば`renderDistance`は`12`です。その名前の設定がない場合は空です。

- `name`：`options.txt`内の設定名

```
{"placeholder":"minecraft_option_value","values":{"name":"renderDistance"}}
```

### Keybind Key

**識別子：** `keybind_key`

操作設定画面と同じ形式で、キー割り当てに現在設定されているキーを返します。たとえばジャンプは`Space`です。その名前のキー割り当てがない場合は空です。

- `keybind`：キー割り当て名（例：`key.jump`、`key.inventory`）。名前は`options.txt`に記載されていますが、先頭の`key_`は不要です。`key_key.jump`の場合は`key.jump`を指定します。

```
インベントリを開くには{"placeholder":"keybind_key","values":{"keybind":"key.inventory"}}を押してください！
```

### Last World or Server

**識別子：** `last_world_server`

プレイヤーが最後に参加したワールドまたはサーバーを返します。サーバーは`play.example.net:25565`のように表示されます。

- `type`：ワールドとサーバーの両方を対象にする場合は`both`、ワールドのみなら`world`、サーバーのみなら`server`。`world`または`server`を指定した場合、最後に参加したものが別の種類なら空です。
- `full_world_path`（省略可能）：`false`では`New World`のようなワールド名のみを返します。`true`ではワールドフォルダーのパスを返します。既定値は`true`です。

```
{"placeholder":"last_world_server","values":{"type":"world","full_world_path":"false"}}
```

## GUI

開いている画面とその要素に関する情報です。要素のプレースホルダーには要素IDを指定します。レイアウトエディターで要素を右クリックし、**Copy Element ID**をクリックしてください。

### Screen Width

**識別子：** `guiwidth`

画面のGUIピクセル単位の幅です。モニターのピクセル数ではなく、要素のサイズに使われる値です。

```
{"placeholder":"guiwidth"}
```

### Screen Height

**識別子：** `guiheight`

画面のGUIピクセル単位の高さです。

```
{"placeholder":"guiheight"}
```

### GUI Scale

**識別子：** `guiscale`

ゲームのGUIスケールを返します（例：`2`）。

```
{"placeholder":"guiscale"}
```

### Current Screen Identifier

**識別子：** `screenid`

開いている画面の[識別子](/screen-identifiers)を返します（例：`title_screen`）。画面が開いていない場合は空です。

```
{"placeholder":"screenid"}
```

### Element Width

**識別子：** `elementwidth`

要素のGUIピクセル単位の幅を返します。指定したIDの要素がない場合は`1`です。

- `id`：要素のID

```
{"placeholder":"elementwidth","values":{"id":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Element Height

**識別子：** `elementheight`

要素のGUIピクセル単位の高さを返します。指定したIDの要素がない場合は`1`です。

- `id`：要素のID

```
{"placeholder":"elementheight","values":{"id":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Element X Position

**識別子：** `elementposx`

要素の左端が画面左端からGUIピクセル単位でどの位置にあるかを返します。指定したIDの要素がない場合は`1`です。

- `id`：要素のID

```
{"placeholder":"elementposx","values":{"id":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Element Y Position

**識別子：** `elementposy`

要素の上端が画面上端からGUIピクセル単位でどの位置にあるかを返します。指定したIDの要素がない場合は`1`です。

- `id`：要素のID

```
{"placeholder":"elementposy","values":{"id":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Text Element Content Height

**識別子：** `text_element_content_height`

[テキスト要素](/text-in-menus)のテキスト全体をスクロールせずに表示するために必要な高さを、GUIピクセル単位で返します。折り返された行、テキストの拡大率、行間も計算されるため、テキストに合わせた背景の作成に便利です。対象がテキスト要素でない場合は`0`です。

- `element_identifier`：テキスト要素のID

```
{"placeholder":"text_element_content_height","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Element Scroll Position

**識別子：** `scroll_area_scroll_position`

[スクロール可能エリア](/scrollable-areas)またはテキスト要素のコンテンツが、開始位置からGUIピクセル単位でどれだけスクロールしたかを返します。それ以外の要素では`0`です。

- `element_identifier`：要素のID
- `axis`：`vertical`または`horizontal`。それ以外の値では、要素のスクロール方向を使用します。

```
{"placeholder":"scroll_area_scroll_position","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","axis":"vertical"}}
```

### Element Scroll Percent

**識別子：** `scroll_area_scroll_percent`

スクロール可能エリアまたはテキスト要素のコンテンツが、開始位置の`0`から末尾の`100`までのどこにあるかを返します。それ以外の要素や、スクロールするものがない場合は`0`です。

- `element_identifier`：要素のID
- `axis`：`vertical`または`horizontal`。それ以外の値では、要素のスクロール方向を使用します。

```
{"placeholder":"scroll_area_scroll_percent","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","axis":"vertical"}}
```

### Element Scroll Content Size

**識別子：** `scroll_area_content_size`

スクロール可能エリアまたはテキスト要素のコンテンツサイズを返します。`vertical`の場合は高さ、`horizontal`の場合は幅です。それ以外の要素では`0`です。

- `element_identifier`：要素のID
- `axis`：`vertical`または`horizontal`。それ以外の値では、要素のスクロール方向を使用します。

```
{"placeholder":"scroll_area_content_size","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","axis":"vertical"}}
```

### Text Input Field Value

**識別子：** `text_input_field_value`

[テキスト入力フィールド](/elements#text-input-field)または元の画面のテキストフィールドに入力されている内容を返します。対象の要素がテキストフィールドでない場合は空です。

- `element_identifier`：要素のID

```
{"placeholder":"text_input_field_value","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Vanilla Widget Label/Text

**識別子：** `vanillabuttonlabel`

元の画面にあるボタンなどのウィジェットのラベルを返します（例：`Options...`）。レイアウトエディターでウィジェットを右クリックし、**Copy Widget Locator**をクリックするとロケーターをコピーできます。

- `locator`：ウィジェットのロケーター

```
{"placeholder":"vanillabuttonlabel","values":{"locator":"title_screen:mc_titlescreen_options_button"}}
```

### Mouse X Position

**識別子：** `mouseposx`

マウスカーソルが画面左端からGUIピクセル単位でどの位置にあるかを返します。レイアウトエディターでは常に`10`になり、マウスに追従する要素を編集可能な位置に保ちます。

```
{"placeholder":"mouseposx"}
```

### Mouse Y Position

**識別子：** `mouseposy`

マウスカーソルが画面上端からGUIピクセル単位でどの位置にあるかを返します。レイアウトエディターでは常に`10`です。

```
{"placeholder":"mouseposy"}
```

### Clicks Per Second

**識別子：** `clicks_per_second`

直近1秒間にマウスボタンがクリックされた回数を返します。

- `mouse_button`（省略可能）：`left`または`right`。既定値は`left`です。

```
{"placeholder":"clicks_per_second","values":{"mouse_button":"left"}}
```

## プレイヤー

### Player Name

**識別子：** `playername`

プレイヤー名を返します（例：`Steve`）。

```
{"placeholder":"playername"}
```

### Player UUID

**識別子：** `playeruuid`

プレイヤーのUUIDを返します（例：`c8cde7fe-7ced-11eb-9439-0242ac130002`）。

```
{"placeholder":"playeruuid"}
```

### Last Death Message

**識別子：** `lastdeathmessage`

ゲーム開始後にプレイヤーが最後に死亡したときのメッセージを返します（例：`Steve was slain by Zombie`）。初めて死亡するまでは空です。

- `as_json_component`（省略可能）：`true`にすると、色付きのJSONテキストコンポーネントとして返します。既定値は`false`です。

```
{"placeholder":"lastdeathmessage","values":{"as_json_component":"false"}}
```

## 現在時刻

コンピューターの時刻に関する情報です。日付と時刻のプレースホルダーには省略可能な`timezone`を指定できます。`system`はコンピューターのタイムゾーン（既定値）です。また、`UTC`、`Europe/Berlin`、`America/New_York`などのIDも使えます。すべてのIDは[nodatime.org/TimeZones](https://nodatime.org/TimeZones)を参照してください。

### Realtime Year

**識別子：** `realtimeyear`

年を返します（例：`2026`）。

```
{"placeholder":"realtimeyear","values":{"timezone":"system"}}
```

### Realtime Month

**識別子：** `realtimemonth`

月を`01`から`12`の範囲で返します。

```
{"placeholder":"realtimemonth","values":{"timezone":"system"}}
```

### Realtime Day

**識別子：** `realtimeday`

月の日を`01`から`31`の範囲で返します。

```
{"placeholder":"realtimeday","values":{"timezone":"system"}}
```

### Realtime Hour

**識別子：** `realtimehour`

時を`00`から`23`の範囲で返します。

- `twelve_hour_format`（省略可能）：`true`にすると、代わりに`01`から`12`で返します。既定値は`false`です。

```
{"placeholder":"realtimehour","values":{"twelve_hour_format":"false","timezone":"Europe/Berlin"}}
```

### Realtime Minute

**識別子：** `realtimeminute`

分を`00`から`59`の範囲で返します。

```
{"placeholder":"realtimeminute","values":{"timezone":"system"}}
```

### Realtime Second

**識別子：** `realtimesecond`

秒を`00`から`59`の範囲で返します。

```
{"placeholder":"realtimesecond","values":{"timezone":"system"}}
```

### Current Time in Millis (Unix Timestamp)

**識別子：** `unix_time`

1970年1月1日（UTC）からの経過時間をミリ秒で返します（例：`1732456789012`）。タイマーに便利です。値を変数に保存し、後で取得した値からCalculatorで引き算してください。

```
{"placeholder":"unix_time"}
```

## サーバー

サーバーリストと同じように、サーバーの状態を問い合わせます。カスタマイズされた画面が開いている間、FancyMenuは30秒ごとに問い合わせます。最初の応答があるまでは、サーバーはオフラインとして扱われます。

- `ip`：サーバーのアドレス。ポートが既定値でない場合はポートも指定します（例：`play.example.net`、`play.example.net:25566`）。

### Server Status

**識別子：** `serverstatus`

オンラインなら緑色の`Online`、オフラインなら赤色の`Offline`を返します。

```
{"placeholder":"serverstatus","values":{"ip":"play.example.net"}}
```

### Server Player Count

**識別子：** `serverplayercount`

オンライン中のプレイヤー数と最大プレイヤー数を返します（例：`12/100`）。サーバーから応答があるまでは`0/0`です。

```
{"placeholder":"serverplayercount","values":{"ip":"play.example.net"}}
```

### Server MOTD

**識別子：** `servermotd`

サーバーのMOTD（今日のメッセージ）の1行を返します。

- `line`：`1`または`2`

```
{"placeholder":"servermotd","values":{"ip":"play.example.net","line":"1"}}
```

### Server PING

**識別子：** `serverping`

サーバーへのpingをミリ秒単位で返します（例：`54`）。オフラインの場合は`-1`です。

```
{"placeholder":"serverping","values":{"ip":"play.example.net"}}
```

### Server Version

**識別子：** `serverversion`

サーバーのMinecraftバージョンを返します（例：`1.21.1`）。サーバーによっては独自のテキストが表示されます。サーバーから応答があるまでは`---`です。

```
{"placeholder":"serverversion","values":{"ip":"play.example.net"}}
```

## 動画

開いているメニューの[Video要素と動画メニュー背景](/video)の情報を取得します。Video要素の場合は、レイアウトエディターで要素を右クリックし、**Copy Element ID**をクリックします。背景の場合は、エディターの背景を右クリックし、**Copy Background Identifier**をクリックします。

### Video Element Volume

**識別子：** `video_element_vol`

Video要素の音量を返します。範囲は`0.0`（0%）から`1.0`（100%）です。

- `element_identifier`：Video要素のID

```
{"placeholder":"video_element_vol","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Video Element Duration

**識別子：** `video_element_duration`

Video要素の動画の長さを返します（例：`02:00`）。読み込み中は`00:00`（または`0`）です。

- `element_identifier`：Video要素のID
- `output_as_timestamp`（省略可能）：`true`にすると、代わりに`120000`のようなミリ秒で返します。既定値は`false`です。

```
{"placeholder":"video_element_duration","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","output_as_timestamp":"false"}}
```

### Video Element Play Time

**識別子：** `video_element_playtime`

Video要素の動画の再生位置を返します（例：`00:45`）。読み込み中は`00:00`（または`0`）です。

- `element_identifier`：Video要素のID
- `show_percentage`（省略可能）：`true`にすると、進捗を`0`から`100`で返します。既定値は`false`です。
- `output_as_timestamp`（省略可能）：`true`にするとミリ秒で返します。両方が`true`の場合は`show_percentage`が優先されます。既定値は`false`です。

```
{"placeholder":"video_element_playtime","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","show_percentage":"false","output_as_timestamp":"false"}}
```

### Video Element Paused State

**識別子：** `video_element_paused_state`

Video要素が一時停止中なら`true`、それ以外なら`false`を返します。

- `element_identifier`：Video要素のID

```
{"placeholder":"video_element_paused_state","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Video Background Volume

**識別子：** `video_background_vol`

動画メニュー背景の音量を返します。範囲は`0.0`（0%）から`1.0`（100%）です。

- `background_identifier`：メニュー背景の識別子

```
{"placeholder":"video_background_vol","values":{"background_identifier":"8c2e4f6a-1b3d-4e5f-8a7b-9c0d1e2f3a4b-1732456789012"}}
```

### Video Background Duration

**識別子：** `video_background_duration`

メニュー背景の動画の長さを返します（例：`03:00`）。読み込み中は`00:00`（または`0`）です。

- `background_identifier`：メニュー背景の識別子
- `output_as_timestamp`（省略可能）：`true`にすると、代わりにミリ秒で返します。既定値は`false`です。

```
{"placeholder":"video_background_duration","values":{"background_identifier":"8c2e4f6a-1b3d-4e5f-8a7b-9c0d1e2f3a4b-1732456789012","output_as_timestamp":"false"}}
```

### Video Background Play Time

**識別子：** `video_background_playtime`

メニュー背景の動画の再生位置を返します（例：`01:00`）。読み込み中は`00:00`（または`0`）です。

- `background_identifier`：メニュー背景の識別子
- `show_percentage`（省略可能）：`true`にすると、進捗を`0`から`100`で返します。既定値は`false`です。
- `output_as_timestamp`（省略可能）：`true`にするとミリ秒で返します。両方が`true`の場合は`show_percentage`が優先されます。既定値は`false`です。

```
{"placeholder":"video_background_playtime","values":{"background_identifier":"8c2e4f6a-1b3d-4e5f-8a7b-9c0d1e2f3a4b-1732456789012","show_percentage":"true","output_as_timestamp":"false"}}
```

### Video Background Paused State

**識別子：** `video_background_paused_state`

動画メニュー背景が一時停止中なら`true`、それ以外なら`false`を返します。

- `background_identifier`：メニュー背景の識別子

```
{"placeholder":"video_background_paused_state","values":{"background_identifier":"8c2e4f6a-1b3d-4e5f-8a7b-9c0d1e2f3a4b-1732456789012"}}
```

## ワールド：プレイヤーのステータス

**World**カテゴリーは、プレイ中のワールドに関する情報です。ほとんどのプレースホルダーは読み込み済みのワールドを必要とします。ワールドに入っていない場合は、`0`、`0.0`、または空の値を返します。

### Current Player Health

**識別子：** `current_player_health`

プレイヤーの体力を返します（例：`20.0`）。ハート1個は`2.0`です。

```
{"placeholder":"current_player_health"}
```

### Max Player Health

**識別子：** `max_player_health`

プレイヤーの最大体力を返します（例：`20.0`）。

```
{"placeholder":"max_player_health"}
```

### Current Player Health (Percent)

**識別子：** `current_player_health_percent`

プレイヤーの体力をパーセントで、`0`から`100`の範囲で返します。

```
{"placeholder":"current_player_health_percent"}
```

### Current Player Absorption Health

**識別子：** `current_player_absorption_health`

プレイヤーの吸収体力（金色のハート）を返します（例：`4.0`）。

```
{"placeholder":"current_player_absorption_health"}
```

### Max Player Absorption Health

**識別子：** `max_player_absorption_health`

プレイヤーの最大吸収体力を返します（例：`4.0`）。

```
{"placeholder":"max_player_absorption_health"}
```

### Current Player Absorption Health (Percent)

**識別子：** `current_player_absorption_health_percent`

プレイヤーの吸収体力をパーセントで、`0`から`100`の範囲で返します。

```
{"placeholder":"current_player_absorption_health_percent"}
```

### Current Player Food Level

**識別子：** `current_player_hunger`

プレイヤーの満腹度を`0.0`から`20.0`の範囲で返します。

```
{"placeholder":"current_player_hunger"}
```

### Max Player Food Level

**識別子：** `max_player_hunger`

プレイヤーの最大満腹度を返します。常に`20.0`です。

```
{"placeholder":"max_player_hunger"}
```

### Current Player Food Level (Percent)

**識別子：** `current_player_hunger_percent`

プレイヤーの満腹度をパーセントで、`0`から`100`の範囲で返します。

```
{"placeholder":"current_player_hunger_percent"}
```

### Current Player Hunger Saturation

**識別子：** `current_player_hunger_saturation`

プレイヤーの隠し満腹度を返します（例：`5.0`）。これが消費されてから満腹度が減少します。

```
{"placeholder":"current_player_hunger_saturation"}
```

### Current Player Armor

**識別子：** `current_player_armor`

プレイヤーの防具ポイントを`0.0`から`20.0`の範囲で返します。

```
{"placeholder":"current_player_armor"}
```

### Max Player Armor

**識別子：** `max_player_armor`

防具ゲージの最大防具ポイントを返します。常に`20.0`です。

```
{"placeholder":"max_player_armor"}
```

### Current Player Armor (Percent)

**識別子：** `current_player_armor_percent`

プレイヤーの防具ポイントをパーセントで、`0`から`100`の範囲で返します。

```
{"placeholder":"current_player_armor_percent"}
```

### Player Armor Toughness

**識別子：** `player_armor_toughness`

プレイヤーの防具強度を返します。ダイヤモンド防具一式なら`8.0`です。

```
{"placeholder":"player_armor_toughness"}
```

### Current Player Oxygen Level

**識別子：** `current_player_oxygen`

水中でのプレイヤーの空気量を`0.0`から`300.0`の範囲で返します。

```
{"placeholder":"current_player_oxygen"}
```

### Max Player Oxygen Level

**識別子：** `max_player_oxygen`

プレイヤーの最大空気量を返します（例：`300.0`）。

```
{"placeholder":"max_player_oxygen"}
```

### Current Player Oxygen Level (Percent)

**識別子：** `current_player_oxygen_percent`

プレイヤーの空気量をパーセントで、`0`から`100`の範囲で返します。

```
{"placeholder":"current_player_oxygen_percent"}
```

### Current Player Level

**識別子：** `current_player_level`

プレイヤーの経験値レベルを返します（例：`30`）。

```
{"placeholder":"current_player_level"}
```

### Current Player Experience

**識別子：** `current_player_exp`

プレイヤーの合計経験値ポイントを返します（例：`1395.0`）。レベルではありません。

```
{"placeholder":"current_player_exp"}
```

### Player Experience Progress (Percent)

**識別子：** `current_player_exp_progress`

経験値バーの進捗を`0`から`100`の範囲で返します。

```
{"placeholder":"current_player_exp_progress"}
```

### Player Attack Strength (Percent)

**識別子：** `player_attack_strength`

次の攻撃のチャージ具合を、攻撃インジケーターと同じように`0`から`100`の範囲で返します。

```
{"placeholder":"player_attack_strength"}
```

### Player Game Mode

**識別子：** `player_gamemode`

`survival`、`creative`、`adventure`、`spectator`のいずれかを返します。

```
{"placeholder":"player_gamemode"}
```

### Player Item Use Progress (FM)

**識別子：** `player_item_use_progress_fm`

食べる、飲む、弓を引くなど、アイテム使用の進行度を`0.0`から`1.0`の範囲で返します。

```
{"placeholder":"player_item_use_progress_fm"}
```

### Current Mount Health

**識別子：** `current_mount_health`

プレイヤーが乗っている馬などのMobの体力を返します（例：`30.0`）。

```
{"placeholder":"current_mount_health"}
```

### Max Mount Health

**識別子：** `max_mount_health`

プレイヤーが乗っているMobの最大体力を返します。

```
{"placeholder":"max_mount_health"}
```

### Current Mount Health (Percent)

**識別子：** `current_mount_health_percent`

プレイヤーが乗っているMobの体力をパーセントで、`0`から`100`の範囲で返します。

```
{"placeholder":"current_mount_health_percent"}
```

### Current Mount Jump Meter (Percent)

**識別子：** `current_mount_jump_meter`

馬のジャンプのチャージ具合を`0`から`100`の範囲で返します。

```
{"placeholder":"current_mount_jump_meter"}
```

### Active Effects Count

**識別子：** `effects_count`

プレイヤーに現在付与されているエフェクトの数を返します。

```
{"placeholder":"effects_count"}
```

### Active Effect

**識別子：** `active_effect`

画面右上のエフェクトアイコンの順序に従って、プレイヤーのエフェクトID（例：`minecraft:speed`）を返します。指定した位置にエフェクトがない場合は空です。

- `effect_index`：エフェクトの位置。最初のエフェクトは`0`です。

```
{"placeholder":"active_effect","values":{"effect_index":"0"}}
```

## ワールド：インベントリとアイテム

これらは**World**カテゴリーにあります。スロット番号は、`0`から`8`がホットバー、`9`から`35`が残りのインベントリ、`36`から`39`がブーツからヘルメットまでの防具スロット、`40`がオフハンドです。

### Selected Hotbar Slot

**識別子：** `active_hotbar_slot`

選択中のホットバースロットを`0`から`8`の範囲で返します。

```
{"placeholder":"active_hotbar_slot"}
```

### Slot Item

**識別子：** `slot_item`

スロット内のアイテムIDを返します（例：`minecraft:diamond_sword`）。空のスロットでは`minecraft:air`を返します。

- `slot`：スロット番号

```
{"placeholder":"slot_item","values":{"slot":"0"}}
```

### Slot Item Count

**識別子：** `slot_item_count`

スロット内のアイテム数を返します（例：`64`）。

- `slot`：スロット番号

```
{"placeholder":"slot_item_count","values":{"slot":"0"}}
```

### Slot Item Durability

**識別子：** `slot_item_durability`

スロット内のアイテムの耐久値を返します。耐久値のないアイテムでは`0`です。

- `slot`：スロット番号
- `format`（省略可能）：`current`（残り耐久値）、`max`、`damage`（消耗した耐久値）、`percentage`（残り耐久値の割合、`0`から`100`）のいずれか。既定値は`current`です。

```
{"placeholder":"slot_item_durability","values":{"slot":"39","format":"percentage"}}
```

### Slot Item Display Name (FM)

**識別子：** `slot_item_display_name_fm`

スロット内のアイテム名を、レア度の色を含むJSONテキストコンポーネントで返します（例：`{"text":"Diamond Sword","color":"aqua"}`）。スペクテイターモードでは、ホットバースロットにスペクテイターメニューの項目名を返します。

- `slot`：スロット番号
- `ignore_spectator`（省略可能）：`true`にすると、スペクテイターモードでもアイテム名を返します。既定値は`false`です。

```
{"placeholder":"slot_item_display_name_fm","values":{"slot":"0","ignore_spectator":"false"}}
```

### Inventory Item Count

**識別子：** `inventory_item_count`

プレイヤーのインベントリ全体にある指定アイテムの個数を返します。

- `item`：アイテムID（例：`minecraft:diamond`）。空の場合はすべてのアイテムを数えます。

```
{"placeholder":"inventory_item_count","values":{"item":"minecraft:diamond"}}
```

### Inventory Slot Food Point Restore Amount

**識別子：** `inventory_slot_food_point_restore_amount`

スロット内のアイテムを食べたときに回復する満腹度を返します。リンゴなら`4.0`です。食料でないアイテムは`0.0`です。

- `slot`：スロット番号

```
{"placeholder":"inventory_slot_food_point_restore_amount","values":{"slot":"0"}}
```

### Item Category

**識別子：** `item_category`

アイテムが属するクリエイティブインベントリのタブを返します（例：`Combat`）。タブのないアイテムでは`UNKNOWN`です。

- `item`：アイテムID
- `as_key`（省略可能）：`true`にすると、`minecraft:combat`のようなタブIDを返します。既定値は`false`です。

```
{"placeholder":"item_category","values":{"item":"minecraft:diamond_sword","as_key":"false"}}
```

### Hovered Inventory Item

**識別子：** `hovered_inventory_item`

インベントリ画面でマウスカーソルが重なっているアイテムのIDを返します（例：`minecraft:apple`）。該当するアイテムがない場合は空です。

```
{"placeholder":"hovered_inventory_item"}
```

## ワールド：HUDとボス

これらは**World**カテゴリーにあります。襲撃関連のプレースホルダーは画面上部にバーが表示されている襲撃の情報を取得し、サーバーにもFancyMenuが必要です。シングルプレイでは常に動作します。襲撃がない場合は`0`または空の値を返します。

### Action Bar Message (FM)

**識別子：** `action_bar_message_fm`

ホットバーの上に表示されるメッセージを、JSONテキストコンポーネントで返します（例：`{"text":"You may not rest now","color":"red"}`）。メッセージがない場合は空です。

```
{"placeholder":"action_bar_message_fm"}
```

### Action Bar Message Time (FM)

**識別子：** `action_bar_message_time_fm`

ホットバーの上のメッセージが表示され続ける残りtick数を返します。20 tickは1秒です。

```
{"placeholder":"action_bar_message_time_fm"}
```

### Highlighted Item Time (FM)

**識別子：** `highlighted_item_time_fm`

選択中のアイテム名がホットバーの上に表示され続ける残りtick数を返します。

```
{"placeholder":"highlighted_item_time_fm"}
```

### Current HUD Title/Subtitle

**識別子：** `current_title`

`/title`などで現在表示されているタイトルまたはサブタイトルを返します。表示がない場合は空です。

- `is_subtitle`（省略可能）：`true`にするとサブタイトルを返します。既定値は`false`です。
- `as_json`（省略可能）：`true`にするとJSONテキストコンポーネントとして返します。既定値は`false`です。

```
{"placeholder":"current_title","values":{"is_subtitle":"false","as_json":"false"}}
```

### Bosses Count

**識別子：** `boss_count`

現在表示されているボスバーの数を返します。

```
{"placeholder":"boss_count"}
```

### Boss Name

**識別子：** `boss_name`

ボスバーの名前を返します（例：`Ender Dragon`）。指定した位置にボスバーがない場合は空です。

- `boss_index`：ボスバーの位置。一番上のボスバーは`0`です。
- `as_json`（省略可能）：`true`にするとJSONテキストコンポーネントとして返します。既定値は`false`です。

```
{"placeholder":"boss_name","values":{"boss_index":"0","as_json":"false"}}
```

### Current Boss Health (Percent)

**識別子：** `current_boss_health`

ボスバーの体力の割合を`0`から`100`の範囲で返します。

- `boss_index`：ボスバーの位置。一番上のボスバーは`0`です。

```
{"placeholder":"current_boss_health","values":{"boss_index":"0"}}
```

### Total Active Raid Waves

**識別子：** `active_raid_total_waves`

ボーナスウェーブを含む、襲撃の総ウェーブ数を返します。

```
{"placeholder":"active_raid_total_waves"}
```

### Remaining Active Raid Waves

**識別子：** `active_raid_remaining_waves`

襲撃で残っているウェーブ数を返します。

```
{"placeholder":"active_raid_remaining_waves"}
```

### Current Active Raid Wave

**識別子：** `active_raid_current_wave`

直近のウェーブ番号を返します。最初のウェーブが始まると`1`、始まる前は`0`です。

```
Wave {"placeholder":"active_raid_current_wave"} of {"placeholder":"active_raid_total_waves"}
```

### Active Raid Alive Raiders Count

**識別子：** `active_raid_alive_raiders_count`

襲撃中に生存している襲撃者の数を返します。

```
{"placeholder":"active_raid_alive_raiders_count"}
```

### Active Raid Alive Raiders List

**識別子：** `active_raid_alive_raiders_list`

生存している襲撃者をカンマ区切りで返します。各項目はMob IDと襲撃者のUUIDで、`minecraft:pillager#0d9a4b2e-5f1c-4a8e-9b3d-6c2f1e7a8b90`のような形式です。

```
{"placeholder":"active_raid_alive_raiders_list"}
```

## ワールド：位置とカメラ

これらは**World**カテゴリーにあります。

### Player X Coordinate

**識別子：** `player_x_coordinate`

プレイヤーが立っているブロックのX座標を返します（例：`125`）。

```
{"placeholder":"player_x_coordinate"}
```

### Player Y Coordinate

**識別子：** `player_y_coordinate`

プレイヤーが立っているブロックのY座標を返します（例：`64`）。

```
{"placeholder":"player_y_coordinate"}
```

### Player Z Coordinate

**識別子：** `player_z_coordinate`

プレイヤーが立っているブロックのZ座標を返します（例：`-250`）。

```
{"placeholder":"player_z_coordinate"}
```

### Player View Direction

**識別子：** `player_view_direction`

プレイヤーが向いている方角を返します。`north`、`east`、`south`、`west`のいずれかです。

```
{"placeholder":"player_view_direction"}
```

### Player Position Delta X (FM)

**識別子：** `player_position_delta_x_fm`

前回のtickからX方向に移動した距離をブロック単位で返します（例：`0.12`）。逆方向への移動は負の値になります。

```
{"placeholder":"player_position_delta_x_fm"}
```

### Player Position Delta Y (FM)

**識別子：** `player_position_delta_y_fm`

前回のtickからY方向に移動した距離を返します。落下中は`-0.08`のようになります。

```
{"placeholder":"player_position_delta_y_fm"}
```

### Player Position Delta Z (FM)

**識別子：** `player_position_delta_z_fm`

前回のtickからZ方向に移動した距離を返します。

```
{"placeholder":"player_position_delta_z_fm"}
```

### Camera Rotation X (FM)

**識別子：** `camera_rotation_x_fm`

カメラが上下を向く角度を度数で返します。`-90.0`が真上、`90.0`が真下です。

```
{"placeholder":"camera_rotation_x_fm"}
```

### Camera Rotation Y (FM)

**識別子：** `camera_rotation_y_fm`

カメラが向いている水平方向を、`-180.0`から`180.0`の角度で返します。`0.0`は南です。

```
{"placeholder":"camera_rotation_y_fm"}
```

### Camera Rotation Delta X (FM)

**識別子：** `camera_rotation_delta_x_fm`

前回のtickからカメラが上下に動いた角度を度数で返します。

```
{"placeholder":"camera_rotation_delta_x_fm"}
```

### Camera Rotation Delta Y (FM)

**識別子：** `camera_rotation_delta_y_fm`

前回のtickからカメラが左右に動いた角度を度数で返します。

```
{"placeholder":"camera_rotation_delta_y_fm"}
```

## ワールド：ワールド情報

これらは**World**カテゴリーにあります。

### World Day Time

**識別子：** `world_daytime`

ワールドの時刻をtick数で返します。1日は24000 tickで、朝6時に始まります。日ごとにカウントが続くため、Calculatorで`{"placeholder":"world_daytime"} % 24000`と計算すると、現在の日の時刻を取得できます。

```
{"placeholder":"world_daytime"}
```

### World Day Time Hour

**識別子：** `world_daytime_hour`

ワールド内の時刻の「時」を`00`から`23`の範囲で返します。

- `twelve_hour_format`（省略可能）：`true`にすると、代わりに`01`から`12`で返します。既定値は`false`です。

```
{"placeholder":"world_daytime_hour","values":{"twelve_hour_format":"false"}}
```

### World Day Time Minute

**識別子：** `world_daytime_minute`

ワールド内の時刻の「分」を`00`から`59`の範囲で返します。

```
{"placeholder":"world_daytime_hour"}:{"placeholder":"world_daytime_minute"}
```

### World Game Time

**識別子：** `game_time`

ワールドで経過した合計tick数を返します。時刻とは異なり、`/time set`などのコマンドでは変化しません。

```
{"placeholder":"game_time"}
```

### World Difficulty

**識別子：** `world_difficulty`

`peaceful`、`easy`、`normal`、`hard`のいずれかを返します。

```
{"placeholder":"world_difficulty"}
```

### Current Dimension

**識別子：** `current_dimension`

プレイヤーがいるディメンションを返します（例：`minecraft:overworld`）。

- `as_key`（省略可能）：`false`にすると`Overworld`のような名前を返します。名前のないディメンションではIDを返します。既定値は`true`です。

```
{"placeholder":"current_dimension","values":{"as_key":"false"}}
```

### Current Biome

**識別子：** `current_biome`

プレイヤーがいるバイオームを返します（例：`minecraft:plains`）。

- `as_key`（省略可能）：`false`にすると`Plains`のような名前を返します。既定値は`true`です。

```
{"placeholder":"current_biome","values":{"as_key":"false"}}
```

### Current World Seed

**識別子：** `current_world_seed`

シングルプレイのワールドシードを返します（例：`-4172144997902289642`）。サーバーでは空です。

```
{"placeholder":"current_world_seed"}
```

### Gamerule Value

**識別子：** `gamerule_value`

ゲームルールの値を返します（例：`true`、`3`）。シングルプレイでは常に動作します。サーバーではサーバー側にもFancyMenuが必要です。その名前のゲームルールがない場合は空です。

- `name`：ゲームルール名（例：`keep_inventory`）。Minecraft 1.21.10以前では`keepInventory`のような名前ですが、古い名前も新しいバージョンで使えます。

```
{"placeholder":"gamerule_value","values":{"name":"keep_inventory"}}
```

### Current Server IP

**識別子：** `current_server_ip`

プレイヤーが接続しているサーバーのアドレスを返します（例：`play.example.net`）。シングルプレイでは空です。

```
{"placeholder":"current_server_ip"}
```

### World Players List

**識別子：** `world_players_list`

ゲームが把握しているワールド内のプレイヤー名を、アルファベット順に返します（例：`Alex, Notch, Steve`）。

- `separator`（省略可能）：名前の間に入れるテキスト。既定値は`, `です。

```
{"placeholder":"world_players_list","values":{"separator":", "}}
```

## ワールド：ワールドセーブ

これらは**World**カテゴリーにあり、ワールドが読み込まれていなくても、どのメニューでも動作します。

### World Save Count

**識別子：** `level_save_count`

シングルプレイのワールド数を返します。

```
{"placeholder":"level_save_count"}
```

### World Save Names

**識別子：** `level_save_names`

すべてのシングルプレイのワールド名を、ワールド一覧と同じ順序で返します（例：`Survival World, Creative Test`）。

- `separator`（省略可能）：名前の間に入れるテキスト。既定値は`, `です。

```
{"placeholder":"level_save_names","values":{"separator":", "}}
```

### World Save Data

**識別子：** `level_save_data`

シングルプレイのワールドのすべてのデータをJSON形式で返します（例：`{"file_name":"Survival World","game_type":"survival","difficulty":"normal",...}`）。`file_name`、`display_name`、`game_type`、`difficulty`、`allow_commands`、`last_played`（Unixタイムスタンプ）、`minecraft_version_name`などが含まれます。[**JSON Parser**](#json-parser)で個別の値を読み取れます。

- `level_name`：ワールド一覧に表示される名前と完全に同じワールド名

```
{"placeholder":"json","values":{"source":"{"placeholder":"level_save_data","values":{"level_name":"Survival World"}}","json_path":"$.game_type"}}
```

## その他

これらにはカテゴリーがないため、プレースホルダーメニューではカテゴリー一覧の下に表示されます。

### FPS (Frames Per Second)

**識別子：** `fps`

フレームレートを返します（例：`120`）。

```
{"placeholder":"fps"}
```

### Used RAM in MB

**識別子：** `usedram`

ゲームが現在使用しているRAMをMB単位で返します（例：`4096`）。

```
{"placeholder":"usedram"}
```

### Max RAM in MB

**識別子：** `maxram`

ゲームが使用できる最大RAMをMB単位で返します（例：`8192`）。

```
{"placeholder":"maxram"}
```

### Used RAM in %

**識別子：** `percentram`

ゲームが使用しているRAMの割合を、最大RAMに対するパーセントで返します（例：`50`）。

```
{"placeholder":"percentram"}
```

### CPU Usage (JVM)

**識別子：** `jvmcpu`

ゲームが使用しているCPUの割合をパーセントで返します（例：`25.5`）。

```
{"placeholder":"jvmcpu"}
```

### CPU Usage (OS)

**識別子：** `oscpu`

コンピューター全体のCPU使用率をパーセントで返します（例：`42.8`）。

```
{"placeholder":"oscpu"}
```

### CPU Info

**識別子：** `cpuinfo`

CPU名を返します（例：`Intel(R) Core(TM) i7-10700K CPU @ 3.80GHz`）。

```
{"placeholder":"cpuinfo"}
```

### GPU Info

**識別子：** `gpuinfo`

ゲームが使用しているグラフィックデバイス名を返します（例：`NVIDIA GeForce RTX 3080`）。

```
{"placeholder":"gpuinfo"}
```

### OpenGL Version

**識別子：** `glver`

ゲームが使用しているグラフィックデバイスのドライバー情報を返します（例：`4.6.0 NVIDIA 566.36`）。

```
{"placeholder":"glver"}
```

### Java Version

**識別子：** `javaver`

ゲームの実行に使われているJavaのバージョンを返します（例：`21.0.5`）。

```
{"placeholder":"javaver"}
```

### Java Virtual Machine

**識別子：** `jvmname`

Java仮想マシンの名前を返します（例：`OpenJDK 64-Bit Server VM`）。

```
{"placeholder":"jvmname"}
```

### Operating System Name

**識別子：** `osname`

オペレーティングシステム名を返します（例：`Windows 11`）。

```
{"placeholder":"osname"}
```

### Uptime Duration

**識別子：** `uptime_duration`

ゲームの起動時間を秒単位で返します（例：`742`）。

- `output_as_millis`（省略可能）：`true`にすると、代わりにミリ秒で返します。既定値は`false`です。

```
{"placeholder":"uptime_duration","values":{"output_as_millis":"false"}}
```

### Random Text

**識別子：** `randomtext`

テキストファイル、URL、または入力したテキストから、ランダムな1行を返します。ランダムなヒントなどに使えます。ファイルとURLは30秒ごとに再読み込みされます。

- `source`：ゲームフォルダー内の`.txt`ファイル、URL、または`Tip 1\nTip 2\nTip 3`のように`\n`で区切った複数行のテキスト
- `interval`（省略可能）：新しい行を選ぶまでの秒数。`0`にするとゲームセッション中は同じ行を使用します。既定値は`10`です。

```
{"placeholder":"randomtext","values":{"source":"/config/fancymenu/assets/tips.txt","interval":"10"}}
```

### Web Text

**識別子：** `webtext`

ウェブページのテキスト（ウェブサイト上のテキストファイルなど）の最初の行を返します。一度読み込まれ、FancyMenuの再読み込み時に再度読み込まれます。読み込み中は空です。

- `link`：ページのURL

```
{"placeholder":"webtext","values":{"link":"https://example.com/motd.txt"}}
```

### Absolute File/Folder Path

**識別子：** `absolute_path`

ゲームフォルダー内のファイルまたはフォルダーの絶対パスを返します（例：`C:/Users/Steve/AppData/Roaming/.minecraft/config/fancymenu`）。

- `short_path`：ゲームフォルダー内のパス

```
{"placeholder":"absolute_path","values":{"short_path":"config/fancymenu"}}
```

### Text Character Count

**識別子：** `text_character_count`

テキストの文字数を返します。`Hello World!`は`12`文字です。

- `text`：テキスト

```
{"placeholder":"text_character_count","values":{"text":"$$player_nickname"}}
```

### Text Width

**識別子：** `text_width`

テキストのGUIピクセル単位の幅を返します。`Hello World!`は`57`です。`&l`などの書式コードはゲーム内と同じように反映されるため、太字のテキストは幅が広くなります。

- `text`：テキスト

```
{"placeholder":"text_width","values":{"text":"Hello World!"}}
```

### Text Height

**識別子：** `text_height`

すべての行を含むテキストの高さをGUIピクセル単位で返します。改行には`\n`を使います。テキスト要素に合わせてサイズを調整する場合は、テキストの拡大率、行間、折り返し行数も考慮される[**Text Element Content Height**](#text-element-content-height)を使ってください。

- `text`：テキスト

```
{"placeholder":"text_height","values":{"text":"First line\nSecond line"}}
```

### Clipboard Content

**識別子：** `clipboard_content`

コンピューターのクリップボード内のテキストを返します。クリップボードが空の場合は空です。

```
{"placeholder":"clipboard_content"}
```
