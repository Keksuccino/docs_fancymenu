---
title: 占位符
description: 在文本中显示玩家名称、时间或服务器玩家数等实时值，以及 FancyMenu 提供的所有占位符。
sourceBlobSha: 951d7772d640bc6b19d6f4dcc2fef4adcd1f13aa
---

# 占位符

占位符是一些短代码，FancyMenu 会将它们替换为实时值，例如玩家名称、时间或服务器玩家数。它们可用于元素文本、按钮标签、工具提示、操作和条件的值，以及大多数其他可输入文本的地方。

<img width="800" alt="在布局编辑器的文本元素中添加玩家名称占位符：文本编辑器中的占位符、玩家类别，以及按名称问候玩家的文本" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/placeholders_add.gif?raw=true">

> [!TIP]
> 你自己的[变量](/variables)也可以在相同的文本中使用，写成 `$$` 加变量名称的形式，例如 `$$coins`。

# 添加占位符

1. 在文本编辑器中打开文本，例如[文本元素](/text-in-menus)的**文本内容**。窗口中的文本字段（例如操作的值）旁边有一个**在编辑器中打开**按钮。
2. 点击要插入占位符的位置。
3. 点击文本编辑器右上角的**占位符**。
4. 点击一个类别，或按名称、标识符或说明搜索。点击**返回**可回到类别列表。没有类别的占位符列在类别下方。
5. 将鼠标悬停在占位符上可查看其作用，点击即可添加。
6. 替换占位符中的示例值，例如**模组版本**中的模组 ID。

文本编辑器中没有**占位符**按钮的文本不支持占位符。

# 占位符的工作方式

占位符的格式如下：

```
{"placeholder":"playername"}
```

带设置项的占位符会将设置放在 `values` 中：

```
{"placeholder":"modversion","values":{"modid":"fancymenu"}}
```

- 标识符（例如 `playername`）区分大小写。下方列出的每个占位符都包含其标识符和值。
- 值的顺序无关紧要。标记为可选的值可以省略。
- 如果 FancyMenu 无法替换某个占位符（例如其中有拼写错误），它会保留在文本中，显示为你输入的内容。
- 占位符始终返回文本。如果没有可显示的内容，则会返回备用值，例如 `0`、`0.0`、`---` 或空文本。
- 占位符周围可以使用[格式代码](/text-formatting)：`&6{"placeholder":"playername"}` 会以金色显示名称。

> [!IMPORTANT]
> 占位符看起来像 JSON，但它们并不是 JSON。不要使用 JSON 格式化工具或验证器处理占位符，因为占位符中包含的其他占位符并不是有效的 JSON。

## 占位符中的占位符

值中可以包含其他占位符和[变量](/variables#showing-variables-in-text)。FancyMenu 会先替换内部的占位符。值中的引号无需转义。

以下示例将最大内存从 MB 换算为 GB：

```
{"placeholder":"calc","values":{"decimal":"true","expression":"{"placeholder":"maxram"} / 1024"}}
```

以下示例将变量 `rank` 转换为大写：

```
{"placeholder":"uppercase_text","values":{"text":"$$rank"}}
```

如果占位符返回的文本中包含其他占位符（例如通过[**文件文本**](#file-text)读取的文件内容），FancyMenu 也会替换这些占位符。

# 须知

- 占位符会自动更新。FancyMenu 会保留替换后的文本 30 毫秒，然后再次替换其中的占位符。可以在**菜单栏 -> 自定义 -> 设置**中调整**占位符缓存时长 [MS]**。设置为 `0` 会在每帧替换一次，占用更多性能。
- 读取网站、文件或服务器的占位符（例如**网页文本**或**服务器状态**）会在后台加载。在加载完成前，它们会返回空文本或备用值。
- 在[操作](/action-scripts)中，占位符会在操作运行时获取当前值。
- 关于世界、屏幕和元素的占位符只能在游戏主线程中使用。在后台（异步）运行的[计时器](/elements#ticker)中使用时，FancyMenu 会显示错误。
- **随机数**每次文本更新时都会生成新数字。要保留该数字，可使用[**设置变量值 (FM Variable)**](/action-scripts#set-variable-value-fm-variable)将其保存到[变量](/variables)中。

> [!CAUTION]
> **JSON 解析器**、**文件文本**和**剪贴板内容**等占位符可以读取游戏文件夹中的文件和你的剪贴板。如果与会联系网站的操作配合使用，布局可能会将这些数据发送出去。请只使用你信任的布局。

# 示例

## 欢迎面板

<img width="800" alt="文本元素按玩家名称问候玩家，并显示 Minecraft 版本、模组数量和时间" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/placeholders_welcome.png?raw=true">

```
### 欢迎回来，{"placeholder":"playername"}！
Minecraft {"placeholder":"mcversion"}，已加载 {"placeholder":"loadedmods"} 个模组
现在是 {"placeholder":"realtimehour"}:{"placeholder":"realtimeminute"}
```

## 服务器状态和玩家

```
生存模式：{"placeholder":"serverstatus","values":{"ip":"play.example.net"}}&r，{"placeholder":"serverplayercount","values":{"ip":"play.example.net"}} 名玩家
```

## 日期和时间

```
{"placeholder":"realtimeyear"}年{"placeholder":"realtimemonth"}月{"placeholder":"realtimeday"}日，{"placeholder":"realtimehour"}:{"placeholder":"realtimeminute"}
```

## RAM 使用情况

```
RAM：{"placeholder":"usedram"} / {"placeholder":"maxram"} MB（{"placeholder":"percentram"}%）
```

# 所有占位符

以下是 FancyMenu 提供的所有占位符。占位符菜单中较大的**高级**和**世界**类别在此拆分为更小的组。

## 变量和列表

这些占位符位于**高级**类别中。请参阅[变量](/variables)，了解如何创建变量和列表。

### 获取变量值 (FM Variable)

**标识符：** `getvariable`

获取一个变量的值。变量为空或不存在时返回 `0`，因此适合用于数字。列表会以 JSON 数组的形式返回所有条目，例如 `["Steve","Alex"]`。

- `name`：变量名称，不包含 `$$`

```
{"placeholder":"getvariable","values":{"name":"clicks"}}
```

### 获取列表条目 (FM Variable)

**标识符：** `list_get`

获取列表变量中的一个条目。

- `name`：列表名称
- `index`：条目的位置。第一个条目的索引为 `0`；负数从末尾开始计数，因此 `-1` 表示最后一个条目。
- `fallback`（可选）：指定索引没有条目或不存在该名称的列表时返回的内容。默认为空。

```
{"placeholder":"list_get","values":{"name":"tips","index":"0","fallback":"No tips yet"}}
```

### 列表大小 (FM Variable)

**标识符：** `list_size`

获取列表中的条目数。不存在该名称的列表时返回 `0`。

- `name`：列表名称

```
{"placeholder":"list_size","values":{"name":"tips"}}
```

### 列表条目索引 (FM Variable)

**标识符：** `list_index_of`

获取第一个与整个 `value` 完全匹配的条目的索引。如果列表中没有该条目，则返回 `-1`。

- `name`：列表名称
- `value`：要查找的条目
- `ignore_case`（可选）：设为 `true` 时，`Apple` 和 `apple` 也会匹配。默认为 `false`。

```
{"placeholder":"list_index_of","values":{"name":"read_news","value":"news_42","ignore_case":"false"}}
```

### 合并列表条目 (FM Variable)

**标识符：** `list_join`

将列表中的所有条目合并为一段文本。不存在该名称的列表时返回空文本。

- `name`：列表名称
- `separator`（可选）：条目之间的文本。`\n` 表示换行。默认为 `, `。

```
{"placeholder":"list_join","values":{"name":"tips","separator":"\n"}}
```

## 数学

这些占位符位于**高级**类别中。小数使用点号，例如 `2.5`。

### 计算器

**标识符：** `calc`

计算数学表达式，例如 `2 + 3 * 4`。

- `expression`：要计算的表达式
- `decimal`（可选）：设为 `false` 时将结果四舍五入为整数。默认为 `true`，结果可能类似 `14.0`。

```
{"placeholder":"calc","values":{"decimal":"false","expression":"{"placeholder":"usedram"} * 100 / {"placeholder":"maxram"}"}}
```

| 表达式中的内容 | 作用 |
|---|---|
| `+` `-` `*` `/` | 加、减、乘、除 |
| `^` | 幂运算，例如 `2 ^ 3` 得到 8 |
| `%` | 取余，例如 `7 % 3` 得到 1 |
| `( )` | 对表达式分组，例如 `(2 + 3) * 4` |
| `pi`, `e` | 数字 π 和 e |
| `abs(x)` | 去掉数字的负号 |
| `sqrt(x)`, `cbrt(x)` | 平方根、立方根 |
| `pow(x, y)` | x 的 y 次方 |
| `floor(x)`, `ceil(x)` | 向下取整、向上取整 |
| `sin(x)`, `cos(x)`, `tan(x)`, `cot(x)` | 三角函数，角度使用弧度 |
| `asin(x)`, `acos(x)`, `atan(x)` | 反三角函数 |
| `sinh(x)`, `cosh(x)`, `tanh(x)` | 双曲函数 |
| `log(x)`, `log2(x)`, `log10(x)` | 以 e、2 和 10 为底的对数 |
| `exp(x)` | e 的 x 次方 |
| `signum(x)` | 返回 `1`、`-1` 或 `0`，类似[**符号 (Math)**](#sign-math) |

### 随机数

**标识符：** `random_number`

生成介于 `min` 和 `max` 之间的随机整数。每次文本更新时都会改变。

- `min`、`max`：最小值和最大值

```
{"placeholder":"random_number","values":{"min":"1","max":"6"}}
```

### 最大值

**标识符：** `maxnum`

返回两个数字中较大的一个。

- `first`、`second`：要比较的数字

```
{"placeholder":"maxnum","values":{"first":"$$score","second":"$$best_score"}}
```

### 最小值

**标识符：** `minnum`

返回两个数字中较小的一个。

- `first`、`second`：要比较的数字

```
{"placeholder":"minnum","values":{"first":"10","second":"15"}}
```

### 绝对值

**标识符：** `absnum`

去掉数字的负号，例如 `-10.5` 会得到 `10.5`。

- `num`：要处理的数字

```
{"placeholder":"absnum","values":{"num":"-10.5"}}
```

### 数字取反

**标识符：** `negnum`

将正数变为负数，例如 `10.5` 会得到 `-10.5`。零和负数保持不变。

- `num`：要处理的数字

```
{"placeholder":"negnum","values":{"num":"10.5"}}
```

### 四舍五入 (Math)

**标识符：** `math_round`

对数字进行四舍五入。`2.5` 会向上取整为 `3`。

- `num`：要处理的数字
- `decimals`（可选）：保留的小数位数，例如 `2` 会将 `3.14159` 转换为 `3.14`。设为 `0`、`-1` 或留空时，会取整为整数。

```
{"placeholder":"math_round","values":{"num":"3.14159","decimals":"2"}}
```

### 向下取整 (Math)

**标识符：** `math_floor`

将数字向下取整为整数，例如 `3.7` 得到 `3`，`-3.2` 得到 `-4`。

- `num`：要处理的数字

```
{"placeholder":"math_floor","values":{"num":"3.7"}}
```

### 向上取整 (Math)

**标识符：** `math_ceil`

将数字向上取整为整数，例如 `3.2` 得到 `4`，`-3.7` 得到 `-3`。

- `num`：要处理的数字

```
{"placeholder":"math_ceil","values":{"num":"3.2"}}
```

### 符号 (Math)

**标识符：** `math_sign`

正数返回 `1`，负数返回 `-1`，零返回 `0`。

- `num`：要处理的数字

```
{"placeholder":"math_sign","values":{"num":"-3.14"}}
```

### *pi* (Math)

**标识符：** `math_pi`

数字 π：`3.141592653589793`。

```
{"placeholder":"math_pi"}
```

### 正弦 (Math)

**标识符：** `math_sin`

计算以弧度表示的角度的正弦值。若使用角度制，请先用计算器将角度乘以 π / 180。

- `angle`：以弧度表示的角度

```
{"placeholder":"math_sin","values":{"angle":"1.5707963267948966"}}
```

### 余弦 (Math)

**标识符：** `math_cos`

计算以弧度表示的角度的余弦值。

- `angle`：以弧度表示的角度

```
{"placeholder":"math_cos","values":{"angle":"0"}}
```

### 正切 (Math)

**标识符：** `math_tan`

计算以弧度表示的角度的正切值。

- `angle`：以弧度表示的角度

```
{"placeholder":"math_tan","values":{"angle":"0.7853981633974483"}}
```

### 双曲正弦 (Math)

**标识符：** `math_sinh`

计算数字的双曲正弦值。

- `num`：要处理的数字

```
{"placeholder":"math_sinh","values":{"num":"1"}}
```

### 双曲余弦 (Math)

**标识符：** `math_cosh`

计算数字的双曲余弦值。

- `num`：要处理的数字

```
{"placeholder":"math_cosh","values":{"num":"1"}}
```

### 双曲正切 (Math)

**标识符：** `math_tanh`

计算数字的双曲正切值。

- `num`：要处理的数字

```
{"placeholder":"math_tanh","values":{"num":"1"}}
```

### 数字进制转换

**标识符：** `number_base_convert`

将数字转换为其他进制，例如从十进制转换为二进制或十六进制。也支持小数，小数点后最多 16 位。结果中的字母为大写，例如 `FF`。

- `input`：要转换的数字
- `from_base`（可选）：`input` 的进制，范围为 `2` 到 `36`。默认为 `10`。
- `to_base`（可选）：结果的进制，范围为 `2` 到 `36`。默认为 `10`。

```
{"placeholder":"number_base_convert","values":{"input":"255","from_base":"10","to_base":"16"}}
```

## 文本

这些占位符位于**高级**类别中。

### 转换为大写

**标识符：** `uppercase_text`

将文本转换为大写：`Hello World` 会得到 `HELLO WORLD`。[格式代码](/text-formatting)（例如 `&a`）会保持不变。

- `text`：要处理的文本

```
{"placeholder":"uppercase_text","values":{"text":"Hello World"}}
```

### 转换为小写

**标识符：** `lowercase_text`

将文本转换为小写：`HELLO WORLD` 会得到 `hello world`。格式代码会保持不变。

- `text`：要处理的文本

```
{"placeholder":"lowercase_text","values":{"text":"HELLO WORLD"}}
```

### 转换为标题格式

**标识符：** `title_case_text`

将每个单词的首字母大写：`hello world` 会得到 `Hello World`。格式代码会保持不变。

- `text`：要处理的文本

```
{"placeholder":"title_case_text","values":{"text":"hello world"}}
```

### 转换为句子格式

**标识符：** `sentence_case_text`

将每句话的首字母大写：`hello world. this is fancymenu!` 会得到 `Hello world. This is fancymenu!`。格式代码会保持不变。

- `text`：要处理的文本

```
{"placeholder":"sentence_case_text","values":{"text":"hello world. this is fancymenu!"}}
```

### 转换为蛇形命名

**标识符：** `snake_case_text`

将文本转换为小写，并在单词之间加上 `_`：`Hello World` 会得到 `hello_world`。格式代码会被移除。

- `text`：要处理的文本

```
{"placeholder":"snake_case_text","values":{"text":"Hello World"}}
```

### 转换为烤串命名

**标识符：** `kebab_case_text`

将文本转换为小写，并在单词之间加上 `-`：`Hello World` 会得到 `hello-world`。格式代码会被移除。

- `text`：要处理的文本

```
{"placeholder":"kebab_case_text","values":{"text":"Hello World"}}
```

### 转换为交替大小写

**标识符：** `alternating_case_text`

让大小写字母交替出现：`alternating case` 会得到 `aLtErNaTiNg CaSe`。

- `text`：要处理的文本

```
{"placeholder":"alternating_case_text","values":{"text":"alternating case"}}
```

### 切换大小写

**标识符：** `toggle_case_text`

将小写字母变为大写，将大写字母变为小写：`Toggle Case` 会得到 `tOGGLE cASE`。

- `text`：要处理的文本

```
{"placeholder":"toggle_case_text","values":{"text":"Toggle Case"}}
```

### 去除文本首尾空格

**标识符：** `trim_text`

移除文本开头和末尾的空格。文本中间的空格会保留。

- `text`：要处理的文本

```
{"placeholder":"trim_text","values":{"text":"  Welcome!  "}}
```

### 截取文本

**标识符：** `crop_text`

从文本开头和末尾移除指定数量的字符。例如，`hello world` 两端各移除 1 个字符后会得到 `ello worl`。

- `text`：要处理的文本
- `remove_from_start`：从开头移除的字符数
- `remove_from_end`：从末尾移除的字符数

```
{"placeholder":"crop_text","values":{"text":"hello world","remove_from_start":"1","remove_from_end":"1"}}
```

### 拆分文本

**标识符：** `split_text`

拆分文本并返回其中一部分。`Steve,Alex,Notch` 按 `,` 拆分后，第 `1` 部分为 `Alex`。

- `input`：要拆分的文本
- `regex`：用于拆分的正则表达式。`.`、`|` 和 `?` 等字符前面需要加上 `\`，例如 `\.`。
- `max_parts`（可选）：最多拆分成多少部分。默认值 `-1` 表示在每个匹配处都进行拆分。
- `split_index`：要返回的部分。第一部分的索引为 `0`。

```
{"placeholder":"split_text","values":{"input":"Steve,Alex,Notch","regex":",","max_parts":"-1","split_index":"1"}}
```

### 替换文本

**标识符：** `replace_text`

替换文本中的部分内容：将 `Hello World!` 中的 `World` 替换为 `FancyMenu`，会得到 `Hello FancyMenu!`。

- `text`：要处理的文本
- `search`：要查找的内容
- `replacement`（可选）：用于替换的内容。默认为空，即移除找到的内容。
- `use_regex`（可选）：设为 `true` 时，`search` 会被视为正则表达式。此时，`replacement` 中的 `$1`、`$2` 等表示匹配到的分组。默认为 `false`。
- `replace_all`（可选）：设为 `false` 时只替换第一个匹配项。默认为 `true`。

```
{"placeholder":"replace_text","values":{"text":"Hello World!","search":"World","replacement":"FancyMenu","use_regex":"false","replace_all":"true"}}
```

### 条件分支

**标识符：** `switch_case`

返回与某个值匹配的分支结果。当变量 `difficulty_level` 的值为 `2` 时，以下示例会返回 `Hard Mode`。

- `value`：要检查的值
- `cases`：值与结果组成的配对，例如 `1:Easy Mode,2:Hard Mode`。值和结果中不能包含 `,` 或 `:`。
- `default`（可选）：没有匹配分支时返回的结果。若未指定默认值，此时占位符会原样保留。

```
{"placeholder":"switch_case","values":{"value":"$$difficulty_level","cases":"1:Easy Mode,2:Hard Mode","default":"Normal Mode"}}
```

### 本地化文本

**标识符：** `local`

返回当前游戏语言中某个本地化键对应的文本，例如 `menu.singleplayer` 对应的 `Singleplayer`。支持 Minecraft、模组和你自己创建的键（参见[本地化](/localization)）。

- `key`：本地化键

```
{"placeholder":"local","values":{"key":"menu.singleplayer"}}
```

### 转义为字符串

**标识符：** `stringify`

先替换文本中的占位符，然后在每个 `"`、`{` 和 `}` 前添加 `\`。这样一来，来自外部的文本（例如网站内容）就无法变成占位符。

- `text`：要处理的文本

```
{"placeholder":"stringify","values":{"text":"{"placeholder":"webtext","values":{"link":"https://example.com/motd.txt"}}"}}
```

## 数据和文件

这些占位符位于**高级**类别中。本地路径从游戏文件夹开始，例如 `/config/fancymenu/assets/news.txt`，且不能离开该文件夹（参见[资源](/resources#local-resources)）。

### JSON 解析器

**标识符：** `json`

从 JSON 中读取一个值。若有多个结果，则每个结果单独占一行。

- `source`：JSON 文本、游戏文件夹中的 JSON 文件，或 JSON 文件的 URL
- `json_path`：值的路径，例如 `$.name` 或 `$.players[0].name`。有关 JSON 路径的更多信息，请参阅 [json.fancymenu.net](https://json.fancymenu.net)。

```
{"placeholder":"json","values":{"source":"https://example.com/server_info.json","json_path":"$.news.title"}}
```

网页上的 JSON 只会加载一次，并会在 FancyMenu 重新加载时再次加载。文件发生更改时会立即显示。

| 路径 | 返回内容 |
|---|---|
| `$.name` | 顶层的 `name` 值 |
| `$.player.level` | `player` 中的 `level` 值 |
| `$.items[0].id` | `items` 中第一个条目的 `id` 值 |
| `$.scores.*` | `scores` 中的所有值 |

### 文件文本

**标识符：** `file_text`

读取文件或 URL 的文本。文件每秒重新读取一次，URL 每 10 秒重新加载一次。加载期间或无法读取时返回空文本。

- `path_or_url`：游戏文件夹中的文件或一个 URL。以 `.minecraft/` 开头的路径指向默认的 Minecraft 文件夹。
- `mode`（可选）：`all` 表示读取完整文本，`last` 表示读取最后几行。默认为 `all`。
- `separator`（可选）：行与行之间的文本。默认为 `\n`（换行）。
- `last_lines`（可选）：`last` 模式读取的行数。默认为 `1`。

```
{"placeholder":"file_text","values":{"path_or_url":"/config/fancymenu/assets/changelog.txt","mode":"all","separator":"\n","last_lines":"1"}}
```

### 文件大小

**标识符：** `file_size`

以字节为单位返回文件大小。文件不存在时返回 `0`。以 `.minecraft/` 开头的路径指向默认的 Minecraft 文件夹。

- `path`：文件路径

```
{"placeholder":"file_size","values":{"path":"/config/fancymenu/assets/news.txt"}}
```

### 文件 MD5

**标识符：** `file_md5`

返回文件的 MD5 哈希值，例如 `d41d8cd98f00b204e9800998ecf8427e`。文件不存在时返回空文本。以 `.minecraft/` 开头的路径指向默认的 Minecraft 文件夹。

- `path`：文件路径

```
{"placeholder":"file_md5","values":{"path":"/config/fancymenu/assets/menu_music.ogg"}}
```

### 编码为 Base64

**标识符：** `base64_encode`

将文本转换为 Base64：`Hello World` 会得到 `SGVsbG8gV29ybGQ=`。

- `text`：要处理的文本

```
{"placeholder":"base64_encode","values":{"text":"Hello World"}}
```

### 从 Base64 解码

**标识符：** `base64_decode`

将 Base64 转换回文本：`SGVsbG8gV29ybGQ=` 会得到 `Hello World`。

- `text`：Base64 文本

```
{"placeholder":"base64_decode","values":{"text":"SGVsbG8gV29ybGQ="}}
```

### 获取 NBT 数据（客户端）

**标识符：** `nbt_data_get`

读取游戏客户端已知的世界信息中的 NBT 数据，效果类似 `/data get`。速度很快，但服务器不会向玩家发送所有数据。

- `source_type`：`entity` 或 `block`
- `entity_selector`：当 `source_type` 为 `entity` 时使用的实体选择器，例如 `@s`（你自己）、`@p`、`@e[type=minecraft:horse,limit=1,sort=nearest]`，或者实体名称或 UUID。选择器可以包含 `type`、`name`、`tag`、`limit`、`sort`、`distance`、`x`、`y`、`z`、`dx`、`dy` 和 `dz`。只使用第一个匹配结果。
- `block_pos`：当 `source_type` 为 `block` 时，填写方块实体（例如箱子）的位置：`120 64 -35`
- `nbt_path`：NBT 路径，例如 `foodLevel` 或 `Inventory[0].id`
- `scale`（可选）：数字的乘数。默认为 `1.0`。
- `return_type`（可选）：`value`（数字和文本保持原样）、`string`、`snbt` 或 `json`。默认为 `value`。

```
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"foodLevel","scale":"1.0","return_type":"value"}}
```

### 获取 NBT 数据（服务器）

**标识符：** `nbt_data_get_server`

从服务器读取 NBT 数据，效果与 `/data get` 完全相同。服务器上需要安装 FancyMenu。在单人游戏中始终可用。在服务器响应前返回空文本，之后约每 100 毫秒更新一次。

- `source_type`：`entity`、`block` 或 `storage`
- `entity_selector`：当 `source_type` 为 `entity` 时，填写 `/data get` 可用且能选中一个实体的任意选择器，例如 `@s` 或 `@e[type=minecraft:villager,limit=1,sort=nearest]`
- `block_pos`：当 `source_type` 为 `block` 时，填写位置，例如 `120 64 -35`、`~ ~-1 ~` 或 `^ ^ ^1`
- `storage_id`：当 `source_type` 为 `storage` 时，填写命令存储的 ID，例如 `mypack:quests`
- `nbt_path`（可选）：NBT 路径。不填写时返回所有数据。
- `scale`（可选）：数字的乘数。默认为 `1.0`。
- `return_type`（可选）：`value`、`string`、`snbt` 或 `json`。默认为 `value`。

```
{"placeholder":"nbt_data_get_server","values":{"source_type":"storage","storage_id":"mypack:quests","nbt_path":"completed","return_type":"value"}}
```

## 音频

这些占位符读取已打开菜单中的[音频元素](/elements#audio)。在布局编辑器中右键点击音频元素，然后点击**复制元素 ID**，即可获取其 ID。

### 音频元素音量

**标识符：** `audio_element_vol`

音频元素的音量，范围为 `0.0`（0%）到 `1.0`（100%）。

- `element_identifier`：音频元素的 ID

```
{"placeholder":"audio_element_vol","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### 当前音轨

**标识符：** `audio_element_current_track`

当前播放音轨的文件名，例如 `menu_theme.ogg`。没有音轨播放时返回 `---`。

- `element_identifier`：音频元素的 ID
- `display_name_mappings`（可选）：用于替代文件名显示的名称。文件名和显示名称之间用 `=>` 分隔，不同映射对之间用 `%:%` 分隔。

```
{"placeholder":"audio_element_current_track","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","display_name_mappings":"menu_theme.ogg=>Menu Theme%:%credits.ogg=>Credits Theme"}}
```

### 音频时长

**标识符：** `audio_duration`

当前音轨的时长，例如 `03:45`。加载期间为 `00:00`。

- `element_identifier`：音频元素的 ID

```
{"placeholder":"audio_duration","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### 音频播放进度

**标识符：** `audio_playtime`

当前音轨已播放的时长，例如 `01:30`。停止播放时为 `00:00`（或 `0`）。

- `element_identifier`：音频元素的 ID
- `show_percentage`（可选）：设为 `true` 时，改为返回 `0` 到 `100` 之间的进度。默认为 `false`。

```
{"placeholder":"audio_playtime","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","show_percentage":"false"}}
```

### 音频播放状态

**标识符：** `audio_playing_state`

音频元素正在播放时返回 `true`，暂停或停止时返回 `false`。

- `element_identifier`：音频元素的 ID

```
{"placeholder":"audio_playing_state","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

## 客户端

这些占位符用于获取游戏及其模组的信息。

### Minecraft 版本

**标识符：** `mcversion`

Minecraft 的版本，例如 `1.21.1`。

```
{"placeholder":"mcversion"}
```

### 模组加载器名称

**标识符：** `loadername`

模组加载器的名称，例如 `Fabric` 或 `NeoForge`。

```
{"placeholder":"loadername"}
```

### 模组加载器版本

**标识符：** `loaderver`

模组加载器的版本，例如 `0.16.14`。

```
{"placeholder":"loaderver"}
```

### 模组版本

**标识符：** `modversion`

已安装模组的版本，例如 `3.11.0`。未安装该模组时返回 `0.0.0`。

- `modid`：模组的 ID，例如 `fancymenu`

```
{"placeholder":"modversion","values":{"modid":"fancymenu"}}
```

### 已加载模组数量

**标识符：** `loadedmods`

已加载的模组数量。库和其他模组中包含的模组也会计入，因此通常会多于模组文件的数量。

```
{"placeholder":"loadedmods"}
```

### 模组总数

**标识符：** `totalmods`

根据每次游戏启动时 `mods` 文件夹中的 `.jar` 文件估算已安装的模组数量。该数量不会小于**已加载模组数量**。

```
{"placeholder":"totalmods"}
```

### 世界加载进度

**标识符：** `world_load_progress`

世界加载屏幕显示时，返回世界加载进度，范围为 `0` 到 `100`。适合用于加载进度条。其他屏幕上返回 `0`。

```
{"placeholder":"world_load_progress"}
```

### Minecraft 选项值

**标识符：** `minecraft_option_value`

返回游戏文件夹中 `options.txt` 文件保存的 Minecraft 选项值，例如 `renderDistance` 的值 `12`。不存在该名称的选项时返回空文本。

- `name`：`options.txt` 中的选项名称

```
{"placeholder":"minecraft_option_value","values":{"name":"renderDistance"}}
```

### 按键绑定

**标识符：** `keybind_key`

返回按键绑定当前使用的按键，与控制设置界面中的显示一致，例如跳跃对应的 `Space`。不存在该名称的按键绑定时返回空文本。

- `keybind`：按键绑定的名称，例如 `key.jump` 或 `key.inventory`。名称可在 `options.txt` 中找到，但不包含开头的 `key_`：`key_key.jump` 对应 `key.jump`。

```
按下 {"placeholder":"keybind_key","values":{"keybind":"key.inventory"}} 打开物品栏！
```

### 上一个世界或服务器

**标识符：** `last_world_server`

玩家最近加入的世界或服务器。服务器显示为 `play.example.net:25565`。

- `type`：`both` 表示世界和服务器，`world` 表示仅世界，`server` 表示仅服务器。设为 `world` 或 `server` 时，如果最近加入的是另一种类型，则返回空文本。
- `full_world_path`（可选）：设为 `false` 时仅返回世界名称，例如 `New World`；设为 `true` 时返回世界文件夹的路径。默认为 `true`。

```
{"placeholder":"last_world_server","values":{"type":"world","full_world_path":"false"}}
```

## GUI

这些占位符用于获取当前打开的屏幕及其元素的信息。元素占位符需要元素 ID：在布局编辑器中右键点击该元素，然后点击**复制元素 ID**。

### 屏幕宽度

**标识符：** `guiwidth`

以 GUI 像素为单位的屏幕宽度。这是元素使用的尺寸，并非显示器的像素数。

```
{"placeholder":"guiwidth"}
```

### 屏幕高度

**标识符：** `guiheight`

以 GUI 像素为单位的屏幕高度。

```
{"placeholder":"guiheight"}
```

### GUI 缩放比例

**标识符：** `guiscale`

游戏的 GUI 缩放比例，例如 `2`。

```
{"placeholder":"guiscale"}
```

### 当前屏幕标识符

**标识符：** `screenid`

当前打开屏幕的[标识符](/screen-identifiers)，例如 `title_screen`。没有打开屏幕时返回空文本。

```
{"placeholder":"screenid"}
```

### 元素宽度

**标识符：** `elementwidth`

元素的宽度，以 GUI 像素为单位。不存在该 ID 的元素时返回 `1`。

- `id`：元素的 ID

```
{"placeholder":"elementwidth","values":{"id":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### 元素高度

**标识符：** `elementheight`

元素的高度，以 GUI 像素为单位。不存在该 ID 的元素时返回 `1`。

- `id`：元素的 ID

```
{"placeholder":"elementheight","values":{"id":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### 元素 X 坐标

**标识符：** `elementposx`

元素左边缘相对于屏幕左侧的位置，以 GUI 像素为单位。不存在该 ID 的元素时返回 `1`。

- `id`：元素的 ID

```
{"placeholder":"elementposx","values":{"id":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### 元素 Y 坐标

**标识符：** `elementposy`

元素上边缘相对于屏幕顶部的位置，以 GUI 像素为单位。不存在该 ID 的元素时返回 `1`。

- `id`：元素的 ID

```
{"placeholder":"elementposy","values":{"id":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### 文本元素内容高度

**标识符：** `text_element_content_height`

[文本元素](/text-in-menus)要完整显示所有文本所需的高度，以 GUI 像素为单位。计算时会考虑自动换行、文本缩放和行间距，因此适合用于贴合文本的背景。元素不是文本元素时返回 `0`。

- `element_identifier`：文本元素的 ID

```
{"placeholder":"text_element_content_height","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### 元素滚动位置

**标识符：** `scroll_area_scroll_position`

[可滚动区域](/scrollable-areas)或文本元素的内容相对于起点的滚动距离，以 GUI 像素为单位。用于其他元素时返回 `0`。

- `element_identifier`：元素的 ID
- `axis`：`vertical` 或 `horizontal`。其他值均表示元素的滚动方向。

```
{"placeholder":"scroll_area_scroll_position","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","axis":"vertical"}}
```

### 元素滚动百分比

**标识符：** `scroll_area_scroll_percent`

可滚动区域或文本元素的内容滚动进度，范围为 `0`（起点）到 `100`（终点）。用于其他元素或没有可滚动内容时返回 `0`。

- `element_identifier`：元素的 ID
- `axis`：`vertical` 或 `horizontal`。其他值均表示元素的滚动方向。

```
{"placeholder":"scroll_area_scroll_percent","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","axis":"vertical"}}
```

### 元素滚动内容尺寸

**标识符：** `scroll_area_content_size`

可滚动区域或文本元素的内容尺寸：`vertical` 表示高度，`horizontal` 表示宽度。用于其他元素时返回 `0`。

- `element_identifier`：元素的 ID
- `axis`：`vertical` 或 `horizontal`。其他值均表示元素的滚动方向。

```
{"placeholder":"scroll_area_content_size","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","axis":"vertical"}}
```

### 文本输入框的值

**标识符：** `text_input_field_value`

返回[文本输入框](/elements#text-input-field)或原始屏幕文本字段中输入的内容。元素不是文本字段时返回空文本。

- `element_identifier`：元素的 ID

```
{"placeholder":"text_input_field_value","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### 原版控件标签/文本

**标识符：** `vanillabuttonlabel`

返回原始屏幕中按钮或其他控件的标签，例如 `Options...`。在布局编辑器中右键点击该控件，然后点击**复制控件定位符**即可获取其定位符。

- `locator`：控件的定位符

```
{"placeholder":"vanillabuttonlabel","values":{"locator":"title_screen:mc_titlescreen_options_button"}}
```

### 鼠标 X 坐标

**标识符：** `mouseposx`

鼠标相对于屏幕左侧的位置，以 GUI 像素为单位。在布局编辑器中始终为 `10`，因此跟随鼠标的元素会保持在可编辑的位置。

```
{"placeholder":"mouseposx"}
```

### 鼠标 Y 坐标

**标识符：** `mouseposy`

鼠标相对于屏幕顶部的位置，以 GUI 像素为单位。在布局编辑器中始终为 `10`。

```
{"placeholder":"mouseposy"}
```

### 每秒点击次数

**标识符：** `clicks_per_second`

返回最近一秒内鼠标按钮被点击的次数。

- `mouse_button`（可选）：`left` 或 `right`。默认为 `left`。

```
{"placeholder":"clicks_per_second","values":{"mouse_button":"left"}}
```

## 玩家

### 玩家名称

**标识符：** `playername`

玩家名称，例如 `Steve`。

```
{"placeholder":"playername"}
```

### 玩家 UUID

**标识符：** `playeruuid`

玩家的 UUID，例如 `c8cde7fe-7ced-11eb-9439-0242ac130002`。

```
{"placeholder":"playeruuid"}
```

### 上次死亡消息

**标识符：** `lastdeathmessage`

自游戏启动以来玩家最近一次死亡时的消息，例如 `Steve was slain by Zombie`。首次死亡前返回空文本。

- `as_json_component`（可选）：设为 `true` 时，以带颜色的 JSON 文本组件形式返回。默认为 `false`。

```
{"placeholder":"lastdeathmessage","values":{"as_json_component":"false"}}
```

## 实时时间

这些占位符获取电脑上的时间。日期和时间相关占位符可选设置 `timezone`：`system` 表示电脑的时区（默认值），也可以使用 `UTC`、`Europe/Berlin` 或 `America/New_York` 等 ID。所有 ID 请参阅 [nodatime.org/TimeZones](https://nodatime.org/TimeZones)。

### 实时年份

**标识符：** `realtimeyear`

年份，例如 `2026`。

```
{"placeholder":"realtimeyear","values":{"timezone":"system"}}
```

### 实时月份

**标识符：** `realtimemonth`

月份，范围为 `01` 到 `12`。

```
{"placeholder":"realtimemonth","values":{"timezone":"system"}}
```

### 实时日期

**标识符：** `realtimeday`

一个月中的日期，范围为 `01` 到 `31`。

```
{"placeholder":"realtimeday","values":{"timezone":"system"}}
```

### 实时小时

**标识符：** `realtimehour`

小时，范围为 `00` 到 `23`。

- `twelve_hour_format`（可选）：设为 `true` 时改为返回 `01` 到 `12`。默认为 `false`。

```
{"placeholder":"realtimehour","values":{"twelve_hour_format":"false","timezone":"Europe/Berlin"}}
```

### 实时分钟

**标识符：** `realtimeminute`

分钟，范围为 `00` 到 `59`。

```
{"placeholder":"realtimeminute","values":{"timezone":"system"}}
```

### 实时秒数

**标识符：** `realtimesecond`

秒数，范围为 `00` 到 `59`。

```
{"placeholder":"realtimesecond","values":{"timezone":"system"}}
```

### 当前时间（毫秒，Unix 时间戳）

**标识符：** `unix_time`

自 1970 年 1 月 1 日（UTC）以来经过的毫秒数，例如 `1732456789012`。适合用于计时器：将其保存到变量中，再用计算器从稍后的时间戳中减去该值。

```
{"placeholder":"unix_time"}
```

## 服务器

这些占位符会向服务器查询状态，类似服务器列表的工作方式。自定义屏幕打开期间，FancyMenu 每 30 秒查询一次。服务器首次响应前会被视为离线。

- `ip`：服务器地址。如果端口不是默认端口，也要填写端口，例如 `play.example.net` 或 `play.example.net:25566`

### 服务器状态

**标识符：** `serverstatus`

在线时以绿色显示 `Online`，离线时以红色显示 `Offline`。

```
{"placeholder":"serverstatus","values":{"ip":"play.example.net"}}
```

### 服务器玩家数量

**标识符：** `serverplayercount`

返回在线玩家数和玩家上限，例如 `12/100`。服务器响应前为 `0/0`。

```
{"placeholder":"serverplayercount","values":{"ip":"play.example.net"}}
```

### 服务器 MOTD

**标识符：** `servermotd`

返回服务器每日消息中的一行。

- `line`：`1` 或 `2`

```
{"placeholder":"servermotd","values":{"ip":"play.example.net","line":"1"}}
```

### 服务器延迟

**标识符：** `serverping`

返回到服务器的延迟，单位为毫秒，例如 `54`。服务器离线时为 `-1`。

```
{"placeholder":"serverping","values":{"ip":"play.example.net"}}
```

### 服务器版本

**标识符：** `serverversion`

服务器的 Minecraft 版本，例如 `1.21.1`。有些服务器会在此处显示自定义文本。服务器响应前为 `---`。

```
{"placeholder":"serverversion","values":{"ip":"play.example.net"}}
```

## 视频

这些占位符读取已打开菜单中的[视频元素和视频菜单背景](/video)。对于视频元素，在布局编辑器中右键点击元素，然后点击**复制元素 ID**。对于背景，在编辑器背景上右键点击，然后点击**复制背景标识符**。

### 视频元素音量

**标识符：** `video_element_vol`

视频元素的音量，范围为 `0.0`（0%）到 `1.0`（100%）。

- `element_identifier`：视频元素的 ID

```
{"placeholder":"video_element_vol","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### 视频元素时长

**标识符：** `video_element_duration`

视频元素中视频的时长，例如 `02:00`。加载期间为 `00:00`（或 `0`）。

- `element_identifier`：视频元素的 ID
- `output_as_timestamp`（可选）：设为 `true` 时改为返回毫秒，例如 `120000`。默认为 `false`。

```
{"placeholder":"video_element_duration","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","output_as_timestamp":"false"}}
```

### 视频元素播放进度

**标识符：** `video_element_playtime`

视频元素中视频的播放进度，例如 `00:45`。加载期间为 `00:00`（或 `0`）。

- `element_identifier`：视频元素的 ID
- `show_percentage`（可选）：设为 `true` 时返回 `0` 到 `100` 之间的进度。默认为 `false`。
- `output_as_timestamp`（可选）：设为 `true` 时返回毫秒。如果两者都设为 `true`，则优先使用 `show_percentage`。默认为 `false`。

```
{"placeholder":"video_element_playtime","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","show_percentage":"false","output_as_timestamp":"false"}}
```

### 视频元素暂停状态

**标识符：** `video_element_paused_state`

视频元素暂停时返回 `true`，否则返回 `false`。

- `element_identifier`：视频元素的 ID

```
{"placeholder":"video_element_paused_state","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### 视频背景音量

**标识符：** `video_background_vol`

视频菜单背景的音量，范围为 `0.0`（0%）到 `1.0`（100%）。

- `background_identifier`：菜单背景的标识符

```
{"placeholder":"video_background_vol","values":{"background_identifier":"8c2e4f6a-1b3d-4e5f-8a7b-9c0d1e2f3a4b-1732456789012"}}
```

### 视频背景时长

**标识符：** `video_background_duration`

菜单背景视频的时长，例如 `03:00`。加载期间为 `00:00`（或 `0`）。

- `background_identifier`：菜单背景的标识符
- `output_as_timestamp`（可选）：设为 `true` 时改为返回毫秒。默认为 `false`。

```
{"placeholder":"video_background_duration","values":{"background_identifier":"8c2e4f6a-1b3d-4e5f-8a7b-9c0d1e2f3a4b-1732456789012","output_as_timestamp":"false"}}
```

### 视频背景播放进度

**标识符：** `video_background_playtime`

菜单背景视频的播放进度，例如 `01:00`。加载期间为 `00:00`（或 `0`）。

- `background_identifier`：菜单背景的标识符
- `show_percentage`（可选）：设为 `true` 时返回 `0` 到 `100` 之间的进度。默认为 `false`。
- `output_as_timestamp`（可选）：设为 `true` 时返回毫秒。如果两者都设为 `true`，则优先使用 `show_percentage`。默认为 `false`。

```
{"placeholder":"video_background_playtime","values":{"background_identifier":"8c2e4f6a-1b3d-4e5f-8a7b-9c0d1e2f3a4b-1732456789012","show_percentage":"true","output_as_timestamp":"false"}}
```

### 视频背景暂停状态

**标识符：** `video_background_paused_state`

视频菜单背景暂停时返回 `true`，否则返回 `false`。

- `background_identifier`：菜单背景的标识符

```
{"placeholder":"video_background_paused_state","values":{"background_identifier":"8c2e4f6a-1b3d-4e5f-8a7b-9c0d1e2f3a4b-1732456789012"}}
```

## 世界：玩家属性

**世界**类别中的占位符用于获取你当前游玩的世界信息。大多数占位符需要已加载的世界。在世界之外使用时，它们会返回 `0`、`0.0` 或空文本。

### 当前玩家生命值

**标识符：** `current_player_health`

玩家当前的生命值，例如 `20.0`。每颗心相当于 `2.0`。

```
{"placeholder":"current_player_health"}
```

### 玩家最大生命值

**标识符：** `max_player_health`

玩家的最大生命值，例如 `20.0`。

```
{"placeholder":"max_player_health"}
```

### 当前玩家生命值（百分比）

**标识符：** `current_player_health_percent`

玩家当前生命值的百分比，范围为 `0` 到 `100`。

```
{"placeholder":"current_player_health_percent"}
```

### 当前玩家吸收生命值

**标识符：** `current_player_absorption_health`

玩家当前的吸收生命值（金色心形），例如 `4.0`。

```
{"placeholder":"current_player_absorption_health"}
```

### 玩家最大吸收生命值

**标识符：** `max_player_absorption_health`

玩家的最大吸收生命值，例如 `4.0`。

```
{"placeholder":"max_player_absorption_health"}
```

### 当前玩家吸收生命值（百分比）

**标识符：** `current_player_absorption_health_percent`

玩家当前吸收生命值的百分比，范围为 `0` 到 `100`。

```
{"placeholder":"current_player_absorption_health_percent"}
```

### 当前玩家饥饿值

**标识符：** `current_player_hunger`

玩家当前的饥饿值，范围为 `0.0` 到 `20.0`。

```
{"placeholder":"current_player_hunger"}
```

### 玩家最大饥饿值

**标识符：** `max_player_hunger`

玩家的最大饥饿值，始终为 `20.0`。

```
{"placeholder":"max_player_hunger"}
```

### 当前玩家饥饿值（百分比）

**标识符：** `current_player_hunger_percent`

玩家当前饥饿值的百分比，范围为 `0` 到 `100`。

```
{"placeholder":"current_player_hunger_percent"}
```

### 当前玩家饱和度

**标识符：** `current_player_hunger_saturation`

玩家当前的饱和度，例如 `5.0`。饱和度耗尽后，饥饿值才会开始下降。

```
{"placeholder":"current_player_hunger_saturation"}
```

### 当前玩家护甲值

**标识符：** `current_player_armor`

玩家当前的护甲值，范围为 `0.0` 到 `20.0`。

```
{"placeholder":"current_player_armor"}
```

### 玩家最大护甲值

**标识符：** `max_player_armor`

护甲栏的最大护甲值，始终为 `20.0`。

```
{"placeholder":"max_player_armor"}
```

### 当前玩家护甲值（百分比）

**标识符：** `current_player_armor_percent`

玩家当前护甲值的百分比，范围为 `0` 到 `100`。

```
{"placeholder":"current_player_armor_percent"}
```

### 玩家盔甲韧性

**标识符：** `player_armor_toughness`

玩家的盔甲韧性，例如穿满钻石盔甲时为 `8.0`。

```
{"placeholder":"player_armor_toughness"}
```

### 当前玩家氧气值

**标识符：** `current_player_oxygen`

玩家在水下的空气值，范围为 `0.0` 到 `300.0`。

```
{"placeholder":"current_player_oxygen"}
```

### 玩家最大氧气值

**标识符：** `max_player_oxygen`

玩家的最大空气值，例如 `300.0`。

```
{"placeholder":"max_player_oxygen"}
```

### 当前玩家氧气值（百分比）

**标识符：** `current_player_oxygen_percent`

玩家当前空气值的百分比，范围为 `0` 到 `100`。

```
{"placeholder":"current_player_oxygen_percent"}
```

### 当前玩家等级

**标识符：** `current_player_level`

玩家的经验等级，例如 `30`。

```
{"placeholder":"current_player_level"}
```

### 当前玩家经验值

**标识符：** `current_player_exp`

玩家的经验点数总和，例如 `1395.0`。这不是经验等级。

```
{"placeholder":"current_player_exp"}
```

### 玩家经验进度（百分比）

**标识符：** `current_player_exp_progress`

经验条的填充程度，范围为 `0` 到 `100`。

```
{"placeholder":"current_player_exp_progress"}
```

### 玩家攻击蓄力（百分比）

**标识符：** `player_attack_strength`

下一次攻击的蓄力程度，范围为 `0` 到 `100`，与攻击指示器一致。

```
{"placeholder":"player_attack_strength"}
```

### 玩家游戏模式

**标识符：** `player_gamemode`

返回 `survival`、`creative`、`adventure` 或 `spectator`。

```
{"placeholder":"player_gamemode"}
```

### 玩家物品使用进度 (FM)

**标识符：** `player_item_use_progress_fm`

玩家使用物品（例如吃东西、喝东西或拉弓）的进度，范围为 `0.0` 到 `1.0`。

```
{"placeholder":"player_item_use_progress_fm"}
```

### 当前坐骑生命值

**标识符：** `current_mount_health`

玩家所骑乘生物（例如马）的当前生命值，例如 `30.0`。

```
{"placeholder":"current_mount_health"}
```

### 坐骑最大生命值

**标识符：** `max_mount_health`

玩家所骑乘生物的最大生命值。

```
{"placeholder":"max_mount_health"}
```

### 当前坐骑生命值（百分比）

**标识符：** `current_mount_health_percent`

玩家所骑乘生物当前生命值的百分比，范围为 `0` 到 `100`。

```
{"placeholder":"current_mount_health_percent"}
```

### 当前坐骑跳跃蓄力（百分比）

**标识符：** `current_mount_jump_meter`

马匹的跳跃蓄力程度，范围为 `0` 到 `100`。

```
{"placeholder":"current_mount_jump_meter"}
```

### 活跃效果数量

**标识符：** `effects_count`

玩家当前拥有的效果数量。

```
{"placeholder":"effects_count"}
```

### 活跃效果

**标识符：** `active_effect`

按照屏幕右上角效果图标的顺序，返回玩家某个效果的 ID，例如 `minecraft:speed`。指定索引处没有效果时返回空文本。

- `effect_index`：效果的位置。第一个效果的索引为 `0`。

```
{"placeholder":"active_effect","values":{"effect_index":"0"}}
```

## 世界：物品栏和物品

这些占位符位于**世界**类别中。槽位编号：`0` 到 `8` 为快捷栏，`9` 到 `35` 为物品栏其余部分，`36` 到 `39` 为从靴子到头盔的盔甲槽，`40` 为副手槽。

### 当前快捷栏槽位

**标识符：** `active_hotbar_slot`

当前选中的快捷栏槽位，范围为 `0` 到 `8`。

```
{"placeholder":"active_hotbar_slot"}
```

### 槽位物品

**标识符：** `slot_item`

返回槽位中物品的 ID，例如 `minecraft:diamond_sword`。空槽位返回 `minecraft:air`。

- `slot`：槽位编号

```
{"placeholder":"slot_item","values":{"slot":"0"}}
```

### 槽位物品数量

**标识符：** `slot_item_count`

返回槽位中的物品数量，例如 `64`。

- `slot`：槽位编号

```
{"placeholder":"slot_item_count","values":{"slot":"0"}}
```

### 槽位物品耐久度

**标识符：** `slot_item_durability`

返回槽位中物品的耐久度。没有耐久度的物品返回 `0`。

- `slot`：槽位编号
- `format`（可选）：`current`（剩余耐久度）、`max`、`damage`（已损失的耐久度）或 `percentage`（剩余百分比，范围为 `0` 到 `100`）。默认为 `current`。

```
{"placeholder":"slot_item_durability","values":{"slot":"39","format":"percentage"}}
```

### 槽位物品显示名称 (FM)

**标识符：** `slot_item_display_name_fm`

以带有稀有度颜色的 JSON 文本组件形式返回槽位中物品的名称，例如 `{"text":"Diamond Sword","color":"aqua"}`。旁观模式下，快捷栏槽位返回旁观者菜单的名称。

- `slot`：槽位编号
- `ignore_spectator`（可选）：设为 `true` 时，旁观模式下也返回物品名称。默认为 `false`。

```
{"placeholder":"slot_item_display_name_fm","values":{"slot":"0","ignore_spectator":"false"}}
```

### 物品栏物品数量

**标识符：** `inventory_item_count`

返回玩家整个物品栏中某种物品的数量。

- `item`：物品的 ID，例如 `minecraft:diamond`。留空时统计所有物品。

```
{"placeholder":"inventory_item_count","values":{"item":"minecraft:diamond"}}
```

### 物品栏槽位食物恢复量

**标识符：** `inventory_slot_food_point_restore_amount`

返回槽位中的物品食用后恢复的饥饿值，例如苹果为 `4.0`。非食物物品返回 `0.0`。

- `slot`：槽位编号

```
{"placeholder":"inventory_slot_food_point_restore_amount","values":{"slot":"0"}}
```

### 物品类别

**标识符：** `item_category`

返回物品所属的创造模式物品栏标签页，例如 `Combat`。没有所属标签页的物品返回 `UNKNOWN`。

- `item`：物品的 ID
- `as_key`（可选）：设为 `true` 时返回标签页 ID，例如 `minecraft:combat`。默认为 `false`。

```
{"placeholder":"item_category","values":{"item":"minecraft:diamond_sword","as_key":"false"}}
```

### 鼠标悬停的物品

**标识符：** `hovered_inventory_item`

在物品栏屏幕中，返回鼠标指向物品的 ID，例如 `minecraft:apple`。没有指向物品时返回空文本。

```
{"placeholder":"hovered_inventory_item"}
```

## 世界：HUD 和 Boss

这些占位符位于**世界**类别中。袭击相关占位符读取屏幕顶部显示进度条的袭击，并且需要在服务器上安装 FancyMenu。在单人游戏中始终可用。没有袭击时返回 `0` 或空文本。

### 操作栏消息 (FM)

**标识符：** `action_bar_message_fm`

以 JSON 文本组件形式返回快捷栏上方的消息，例如 `{"text":"You may not rest now","color":"red"}`。没有消息时返回空文本。

```
{"placeholder":"action_bar_message_fm"}
```

### 操作栏消息剩余时间 (FM)

**标识符：** `action_bar_message_time_fm`

返回快捷栏上方的消息还会显示多少刻。20 刻为 1 秒。

```
{"placeholder":"action_bar_message_time_fm"}
```

### 高亮物品显示时间 (FM)

**标识符：** `highlighted_item_time_fm`

返回所选物品的名称还会在快捷栏上方显示多少刻。

```
{"placeholder":"highlighted_item_time_fm"}
```

### 当前 HUD 标题/副标题

**标识符：** `current_title`

返回当前显示的标题或副标题，例如 `/title` 命令显示的内容。没有内容时返回空文本。

- `is_subtitle`（可选）：设为 `true` 时返回副标题。默认为 `false`。
- `as_json`（可选）：设为 `true` 时以 JSON 文本组件形式返回。默认为 `false`。

```
{"placeholder":"current_title","values":{"is_subtitle":"false","as_json":"false"}}
```

### Boss 数量

**标识符：** `boss_count`

当前显示的 Boss 血条数量。

```
{"placeholder":"boss_count"}
```

### Boss 名称

**标识符：** `boss_name`

返回 Boss 血条的名称，例如 `Ender Dragon`。指定索引处没有 Boss 血条时返回空文本。

- `boss_index`：Boss 血条的位置。最上方的血条索引为 `0`。
- `as_json`（可选）：设为 `true` 时以 JSON 文本组件形式返回。默认为 `false`。

```
{"placeholder":"boss_name","values":{"boss_index":"0","as_json":"false"}}
```

### 当前 Boss 生命值（百分比）

**标识符：** `current_boss_health`

Boss 血条的填充程度，范围为 `0` 到 `100`。

- `boss_index`：Boss 血条的位置。最上方的血条索引为 `0`。

```
{"placeholder":"current_boss_health","values":{"boss_index":"0"}}
```

### 袭击总波数

**标识符：** `active_raid_total_waves`

袭击的总波数，包括奖励波次。

```
{"placeholder":"active_raid_total_waves"}
```

### 袭击剩余波数

**标识符：** `active_raid_remaining_waves`

袭击中尚未到来的波数。

```
{"placeholder":"active_raid_remaining_waves"}
```

### 当前袭击波次

**标识符：** `active_raid_current_wave`

返回最近一波的波次编号，例如第一波开始攻击时为 `1`。第一波开始前为 `0`。

```
第 {"placeholder":"active_raid_current_wave"} 波，共 {"placeholder":"active_raid_total_waves"} 波
```

### 袭击中存活的袭击者数量

**标识符：** `active_raid_alive_raiders_count`

当前袭击中仍然存活的袭击者数量。

```
{"placeholder":"active_raid_alive_raiders_count"}
```

### 袭击中存活的袭击者列表

**标识符：** `active_raid_alive_raiders_list`

返回所有仍然存活的袭击者，以逗号分隔。每个条目由生物 ID 和袭击者 UUID 组成，例如 `minecraft:pillager#0d9a4b2e-5f1c-4a8e-9b3d-6c2f1e7a8b90`。

```
{"placeholder":"active_raid_alive_raiders_list"}
```

## 世界：位置和摄像机

这些占位符位于**世界**类别中。

### 玩家 X 坐标

**标识符：** `player_x_coordinate`

玩家所在方块的 X 坐标，例如 `125`。

```
{"placeholder":"player_x_coordinate"}
```

### 玩家 Y 坐标

**标识符：** `player_y_coordinate`

玩家所在方块的 Y 坐标，例如 `64`。

```
{"placeholder":"player_y_coordinate"}
```

### 玩家 Z 坐标

**标识符：** `player_z_coordinate`

玩家所在方块的 Z 坐标，例如 `-250`。

```
{"placeholder":"player_z_coordinate"}
```

### 玩家视线方向

**标识符：** `player_view_direction`

玩家面朝的方向：`north`、`east`、`south` 或 `west`。

```
{"placeholder":"player_view_direction"}
```

### 玩家 X 轴位置变化量 (FM)

**标识符：** `player_position_delta_x_fm`

玩家自上一刻以来沿 X 轴移动的距离，单位为方块，例如 `0.12`。向相反方向移动时为负数。

```
{"placeholder":"player_position_delta_x_fm"}
```

### 玩家 Y 轴位置变化量 (FM)

**标识符：** `player_position_delta_y_fm`

玩家自上一刻以来沿 Y 轴移动的距离，例如下落时为 `-0.08`。

```
{"placeholder":"player_position_delta_y_fm"}
```

### 玩家 Z 轴位置变化量 (FM)

**标识符：** `player_position_delta_z_fm`

玩家自上一刻以来沿 Z 轴移动的距离。

```
{"placeholder":"player_position_delta_z_fm"}
```

### 摄像机 X 轴旋转 (FM)

**标识符：** `camera_rotation_x_fm`

摄像机向上或向下看的角度，单位为度，范围为 `-90.0`（垂直向上）到 `90.0`（垂直向下）。

```
{"placeholder":"camera_rotation_x_fm"}
```

### 摄像机 Y 轴旋转 (FM)

**标识符：** `camera_rotation_y_fm`

摄像机面朝的方向，单位为度，范围为 `-180.0` 到 `180.0`。`0.0` 表示朝南。

```
{"placeholder":"camera_rotation_y_fm"}
```

### 摄像机 X 轴旋转变化量 (FM)

**标识符：** `camera_rotation_delta_x_fm`

摄像机自上一刻以来向上或向下转动的角度，单位为度。

```
{"placeholder":"camera_rotation_delta_x_fm"}
```

### 摄像机 Y 轴旋转变化量 (FM)

**标识符：** `camera_rotation_delta_y_fm`

摄像机自上一刻以来向左或向右转动的角度，单位为度。

```
{"placeholder":"camera_rotation_delta_y_fm"}
```

## 世界：世界信息

这些占位符位于**世界**类别中。

### 世界日间时间

**标识符：** `world_daytime`

以刻为单位返回世界的日间时间。一天有 24000 刻，并从早上 6:00 开始。该值会跨天持续累加，因此在计算器中使用 `{"placeholder":"world_daytime"} % 24000` 可获得当天的时间。

```
{"placeholder":"world_daytime"}
```

### 世界日间小时

**标识符：** `world_daytime_hour`

世界日间时间的小时数，范围为 `00` 到 `23`。

- `twelve_hour_format`（可选）：设为 `true` 时改为返回 `01` 到 `12`。默认为 `false`。

```
{"placeholder":"world_daytime_hour","values":{"twelve_hour_format":"false"}}
```

### 世界日间分钟

**标识符：** `world_daytime_minute`

世界日间时间的分钟数，范围为 `00` 到 `59`。

```
{"placeholder":"world_daytime_hour"}:{"placeholder":"world_daytime_minute"}
```

### 世界游戏时间

**标识符：** `game_time`

世界运行的总刻数。与日间时间不同，`/time set` 等命令不会改变此值。

```
{"placeholder":"game_time"}
```

### 世界难度

**标识符：** `world_difficulty`

返回 `peaceful`、`easy`、`normal` 或 `hard`。

```
{"placeholder":"world_difficulty"}
```

### 当前维度

**标识符：** `current_dimension`

玩家所在的维度，例如 `minecraft:overworld`。

- `as_key`（可选）：设为 `false` 时返回维度名称，例如 `Overworld`。没有名称的维度会返回其 ID。默认为 `true`。

```
{"placeholder":"current_dimension","values":{"as_key":"false"}}
```

### 当前生物群系

**标识符：** `current_biome`

玩家所在的生物群系，例如 `minecraft:plains`。

- `as_key`（可选）：设为 `false` 时返回生物群系名称，例如 `Plains`。默认为 `true`。

```
{"placeholder":"current_biome","values":{"as_key":"false"}}
```

### 当前世界种子

**标识符：** `current_world_seed`

单人游戏世界的种子，例如 `-4172144997902289642`。在服务器中返回空文本。

```
{"placeholder":"current_world_seed"}
```

### 游戏规则值

**标识符：** `gamerule_value`

返回游戏规则的值，例如 `true` 或 `3`。在单人游戏中始终可用。在服务器上需要服务器端安装 FancyMenu。不存在该名称的游戏规则时返回空文本。

- `name`：游戏规则名称，例如 `keep_inventory`。在 Minecraft 1.21.10 及更早版本中，游戏规则名称类似 `keepInventory`；这些旧名称在新版本中也可用。

```
{"placeholder":"gamerule_value","values":{"name":"keep_inventory"}}
```

### 当前服务器 IP

**标识符：** `current_server_ip`

玩家所在服务器的地址，例如 `play.example.net`。在单人游戏中返回空文本。

```
{"placeholder":"current_server_ip"}
```

### 世界玩家列表

**标识符：** `world_players_list`

返回游戏已知的世界中玩家名称，并按字母顺序排列，例如 `Alex, Notch, Steve`。

- `separator`（可选）：名称之间的文本。默认为 `, `。

```
{"placeholder":"world_players_list","values":{"separator":", "}}
```

## 世界：世界存档

这些占位符位于**世界**类别中，在所有菜单中都可用，无需加载世界。

### 世界存档数量

**标识符：** `level_save_count`

单人游戏世界的数量。

```
{"placeholder":"level_save_count"}
```

### 世界存档名称

**标识符：** `level_save_names`

按世界列表中的顺序返回所有单人游戏世界的名称，例如 `Survival World, Creative Test`。

- `separator`（可选）：名称之间的文本。默认为 `, `。

```
{"placeholder":"level_save_names","values":{"separator":", "}}
```

### 世界存档数据

**标识符：** `level_save_data`

以 JSON 形式返回单人游戏世界的所有数据，例如 `{"file_name":"Survival World","game_type":"survival","difficulty":"normal",...}`。数据包含 `file_name`、`display_name`、`game_type`、`difficulty`、`allow_commands`、`last_played`（Unix 时间戳）、`minecraft_version_name` 等。可使用[**JSON 解析器**](#json-parser)读取单个值。

- `level_name`：世界名称，必须与世界列表中的名称完全一致

```
{"placeholder":"json","values":{"source":"{"placeholder":"level_save_data","values":{"level_name":"Survival World"}}","json_path":"$.game_type"}}
```

## 其他

这些占位符没有类别，因此会列在占位符菜单的类别列表下方。

### FPS（每秒帧数）

**标识符：** `fps`

每秒帧数，例如 `120`。

```
{"placeholder":"fps"}
```

### 已用 RAM（MB）

**标识符：** `usedram`

游戏当前使用的 RAM，单位为 MB，例如 `4096`。

```
{"placeholder":"usedram"}
```

### 最大 RAM（MB）

**标识符：** `maxram`

游戏最多可使用的 RAM，单位为 MB，例如 `8192`。

```
{"placeholder":"maxram"}
```

### 已用 RAM（%）

**标识符：** `percentram`

游戏已用 RAM 占最大 RAM 的百分比，例如 `50`。

```
{"placeholder":"percentram"}
```

### CPU 使用率（JVM）

**标识符：** `jvmcpu`

游戏使用的 CPU 百分比，例如 `25.5`。

```
{"placeholder":"jvmcpu"}
```

### CPU 使用率（操作系统）

**标识符：** `oscpu`

整台电脑的 CPU 使用率，例如 `42.8`。

```
{"placeholder":"oscpu"}
```

### CPU 信息

**标识符：** `cpuinfo`

CPU 名称，例如 `Intel(R) Core(TM) i7-10700K CPU @ 3.80GHz`。

```
{"placeholder":"cpuinfo"}
```

### GPU 信息

**标识符：** `gpuinfo`

游戏使用的图形设备名称，例如 `NVIDIA GeForce RTX 3080`。

```
{"placeholder":"gpuinfo"}
```

### OpenGL 版本

**标识符：** `glver`

游戏使用的图形设备驱动信息，例如 `4.6.0 NVIDIA 566.36`。

```
{"placeholder":"glver"}
```

### Java 版本

**标识符：** `javaver`

游戏运行所用的 Java 版本，例如 `21.0.5`。

```
{"placeholder":"javaver"}
```

### Java 虚拟机

**标识符：** `jvmname`

Java 虚拟机名称，例如 `OpenJDK 64-Bit Server VM`。

```
{"placeholder":"jvmname"}
```

### 操作系统名称

**标识符：** `osname`

操作系统名称，例如 `Windows 11`。

```
{"placeholder":"osname"}
```

### 运行时长

**标识符：** `uptime_duration`

游戏已运行的时间，单位为秒，例如 `742`。

- `output_as_millis`（可选）：设为 `true` 时改为返回毫秒。默认为 `false`。

```
{"placeholder":"uptime_duration","values":{"output_as_millis":"false"}}
```

### 随机文本

**标识符：** `randomtext`

从文本文件、URL 或你输入的文本中随机返回一行，例如随机提示。文件和 URL 每 30 秒重新读取一次。

- `source`：游戏文件夹中的 `.txt` 文件、URL，或用 `\n` 分隔的多行文本，例如 `Tip 1\nTip 2\nTip 3`
- `interval`（可选）：选择新行的间隔秒数。设为 `0` 时，每次游戏会话只选择一次。默认为 `10`。

```
{"placeholder":"randomtext","values":{"source":"/config/fancymenu/assets/tips.txt","interval":"10"}}
```

### 网页文本

**标识符：** `webtext`

返回网页文本的第一行，例如网站上的文本文件。只会加载一次，并会在 FancyMenu 重新加载时再次加载。加载期间返回空文本。

- `link`：网页 URL

```
{"placeholder":"webtext","values":{"link":"https://example.com/motd.txt"}}
```

### 文件/文件夹绝对路径

**标识符：** `absolute_path`

返回游戏文件夹中某个文件或文件夹的完整路径，例如 `C:/Users/Steve/AppData/Roaming/.minecraft/config/fancymenu`。

- `short_path`：游戏文件夹中的相对路径

```
{"placeholder":"absolute_path","values":{"short_path":"config/fancymenu"}}
```

### 文本字符数

**标识符：** `text_character_count`

返回文本的字符数：`Hello World!` 包含 `12` 个字符。

- `text`：要处理的文本

```
{"placeholder":"text_character_count","values":{"text":"$$player_nickname"}}
```

### 文本宽度

**标识符：** `text_width`

返回文本的宽度，单位为 GUI 像素：`Hello World!` 的宽度为 `57`。`&l` 等格式代码的计算方式与游戏中相同，因此粗体文本会更宽。

- `text`：要处理的文本

```
{"placeholder":"text_width","values":{"text":"Hello World!"}}
```

### 文本高度

**标识符：** `text_height`

返回文本所有行的总高度，单位为 GUI 像素。换行符为 `\n`。若要让内容适配文本元素，请使用[**文本元素内容高度**](#text-element-content-height)，它还会考虑文本缩放、行间距和自动换行。

- `text`：要处理的文本

```
{"placeholder":"text_height","values":{"text":"First line\nSecond line"}}
```

### 剪贴板内容

**标识符：** `clipboard_content`

返回电脑剪贴板中的文本。剪贴板为空时返回空文本。

```
{"placeholder":"clipboard_content"}
```
