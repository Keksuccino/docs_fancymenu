---
title: Заполнители
description: >-
  Показывайте в текстах актуальные значения — например, имя игрока, время или
  количество игроков на сервере — и используйте все заполнители FancyMenu.
sourceBlobSha: 951d7772d640bc6b19d6f4dcc2fef4adcd1f13aa
---

# Заполнители

Заполнители — это короткие коды, которые FancyMenu заменяет актуальными значениями, например именем игрока, временем или количеством игроков на сервере. Они работают в текстах элементов, подписях кнопок, всплывающих подсказках, значениях действий и требований, а также в большинстве других текстовых полей.

<img width="800" alt="Добавление заполнителя Player Name в текстовый элемент в редакторе макета: заполнители в текстовом редакторе, категория Player и текст, обращающийся к игроку по имени" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/placeholders_add.gif?raw=true">

> [!TIP]
> Ваши собственные [переменные](/variables) тоже работают в этих текстах. Используйте `$$` и имя переменной, например `$$coins`.

# Добавление заполнителей

1. Откройте текст в текстовом редакторе, например **Text Content** у [текстового элемента](/text-in-menus). У текстовых полей в окнах, например у значений действий, рядом есть кнопка **Open in Editor**.
2. Щёлкните там, где должен находиться заполнитель.
3. В правом верхнем углу текстового редактора нажмите **Placeholders**.
4. Выберите категорию или выполните поиск по имени, идентификатору или описанию. Кнопка **BACK** возвращает к списку категорий. Заполнители без категории перечислены под категориями.
5. Наведите указатель мыши на заполнитель, чтобы узнать, что он делает, и щёлкните по нему, чтобы добавить его.
6. Замените примерные значения, например ID мода для заполнителя **Mod Version**.

Текстовые поля, в текстовом редакторе которых нет кнопки **Placeholders**, не поддерживают заполнители.

# Как работают заполнители

Заполнитель выглядит так:

```
{"placeholder":"playername"}
```

У заполнителей с настройками они указываются в `values`:

```
{"placeholder":"modversion","values":{"modid":"fancymenu"}}
```

- Идентификатор, например `playername`, чувствителен к регистру. Для каждого заполнителя ниже указаны его идентификатор и значения.
- Порядок значений не имеет значения. Необязательные значения можно не указывать.
- Если FancyMenu не может заменить заполнитель, например из-за опечатки, он остаётся в тексте без изменений.
- Заполнители всегда возвращают текст. Если показывать нечего, они возвращают значение по умолчанию: например `0`, `0.0`, `---` или пустую строку.
- [Коды форматирования](/text-formatting) работают рядом с заполнителями: `&6{"placeholder":"playername"}` выводит имя золотым цветом.

> [!IMPORTANT]
> Заполнители похожи на JSON, но не являются им. Не обрабатывайте их JSON-форматтером или валидатором: заполнители внутри других заполнителей не являются допустимым JSON.

## Заполнители внутри заполнителей

Значения могут содержать другие заполнители и [переменные](/variables#showing-variables-in-text). Сначала FancyMenu заменяет внутренние заполнители. Кавычки внутри значений не нужно экранировать.

Этот пример переводит максимальный объём ОЗУ из МБ в ГБ:

```
{"placeholder":"calc","values":{"decimal":"true","expression":"{"placeholder":"maxram"} / 1024"}}
```

Этот пример выводит переменную `rank` заглавными буквами:

```
{"placeholder":"uppercase_text","values":{"text":"$$rank"}}
```

Если заполнитель возвращает текст, содержащий заполнители, например содержимое файла, прочитанное с помощью [**File Text**](#file-text), FancyMenu заменяет и их.

# Полезно знать

- Заполнители обновляются автоматически. FancyMenu хранит заменённый текст 30 миллисекунд, прежде чем снова заменить в нём заполнители. Изменить это значение можно с помощью **Placeholder Caching Duration [MS]** в **menu bar -> Customization -> Settings**. Значение `0` обновляет их каждый кадр, что требует больше ресурсов.
- Заполнители, которые читают веб-сайты, файлы или серверы, например **Web Text** или **Server Status**, загружают данные в фоновом режиме. Пока загрузка не завершена, они ничего не выводят или показывают значение по умолчанию.
- В [действиях](/action-scripts) заполнители получают актуальное значение в момент выполнения действия.
- Заполнители, связанные с миром, экраном и элементами, работают только в главном потоке игры. В работающем в фоновом режиме (асинхронном) [Ticker](/elements#ticker) FancyMenu вместо этого показывает ошибку.
- **Random Number** генерирует новое число при каждом обновлении текста. Чтобы сохранить его, запишите число в [переменную](/variables) с помощью действия [**Set Variable Value (FM Variable)**](/action-scripts#set-variable-value-fm-variable).

> [!CAUTION]
> Такие заполнители, как **JSON Parser**, **File Text** и **Clipboard Content**, могут читать файлы из папки игры и буфер обмена. В сочетании с действиями, обращающимися к веб-сайтам, макет может отправить эти данные третьим лицам. Используйте только макеты, которым доверяете.

# Примеры

## Панель приветствия

<img width="800" alt="Текстовый элемент приветствует игрока по имени, показывает версию Minecraft, количество модов и время" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/placeholders_welcome.png?raw=true">

```
### С возвращением, {"placeholder":"playername"}!
Minecraft {"placeholder":"mcversion"}, модов: {"placeholder":"loadedmods"}
Сейчас {"placeholder":"realtimehour"}:{"placeholder":"realtimeminute"}
```

## Статус сервера и игроки

```
Выживание: {"placeholder":"serverstatus","values":{"ip":"play.example.net"}}&r, игроков: {"placeholder":"serverplayercount","values":{"ip":"play.example.net"}}
```

## Дата и время

```
{"placeholder":"realtimeday"}.{"placeholder":"realtimemonth"}.{"placeholder":"realtimeyear"}, {"placeholder":"realtimehour"}:{"placeholder":"realtimeminute"}
```

## Использование ОЗУ

```
ОЗУ: {"placeholder":"usedram"} / {"placeholder":"maxram"} МБ ({"placeholder":"percentram"}%)
```

# Все заполнители

Здесь перечислены все заполнители FancyMenu. Большие категории **Advanced** и **World** из меню заполнителей здесь разделены на более мелкие группы.

## Переменные и списки

Эти заполнители находятся в категории **Advanced**. Информацию о создании переменных и списков см. в разделе [«Переменные»](/variables).

### Get Variable Value (FM Variable)

**Идентификатор:** `getvariable`

Значение одной из ваших переменных. Если переменная пуста или не существует, возвращается `0`, поэтому этот заполнитель подходит для чисел. Для списка возвращается массив JSON со всеми его элементами, например `["Steve","Alex"]`.

- `name`: имя переменной без `$$`

```
{"placeholder":"getvariable","values":{"name":"clicks"}}
```

### Get List Entry (FM Variable)

**Идентификатор:** `list_get`

Один элемент переменной-списка.

- `name`: имя списка
- `index`: позиция элемента. Нумерация начинается с `0`; отрицательные числа отсчитываются с конца, поэтому `-1` — последний элемент.
- `fallback` (необязательно): значение, которое возвращается, если элемента с таким индексом нет или список с таким именем не существует. По умолчанию — пустая строка.

```
{"placeholder":"list_get","values":{"name":"tips","index":"0","fallback":"Советов пока нет"}}
```

### List Size (FM Variable)

**Идентификатор:** `list_size`

Количество элементов в списке. Возвращает `0`, если списка с таким именем нет.

- `name`: имя списка

```
{"placeholder":"list_size","values":{"name":"tips"}}
```

### Index of List Entry (FM Variable)

**Идентификатор:** `list_index_of`

Индекс первого элемента, полностью совпадающего с `value`, или `-1`, если такого элемента в списке нет.

- `name`: имя списка
- `value`: искомый элемент
- `ignore_case` (необязательно): при значении `true` строки `Apple` и `apple` считаются совпадающими. По умолчанию — `false`.

```
{"placeholder":"list_index_of","values":{"name":"read_news","value":"news_42","ignore_case":"false"}}
```

### Join List Entries (FM Variable)

**Идентификатор:** `list_join`

Все элементы списка, объединённые в одну строку. Если списка с таким именем нет, возвращается пустая строка.

- `name`: имя списка
- `separator` (необязательно): текст между элементами. `\n` означает перенос строки. По умолчанию используется `, `.

```
{"placeholder":"list_join","values":{"name":"tips","separator":"\n"}}
```

## Математика

Эти заполнители находятся в категории **Advanced**. Для дробных чисел используется точка, например `2.5`.

### Calculator

**Идентификатор:** `calc`

Вычисляет математическое выражение, например `2 + 3 * 4`.

- `expression`: выражение для вычисления
- `decimal` (необязательно): значение `false` округляет результат до целого числа. По умолчанию используется `true`, поэтому результат может выглядеть как `14.0`.

```
{"placeholder":"calc","values":{"decimal":"false","expression":"{"placeholder":"usedram"} * 100 / {"placeholder":"maxram"}"}}
```

| В выражениях | Действие |
|---|---|
| `+` `-` `*` `/` | Сложение, вычитание, умножение, деление |
| `^` | Возведение в степень, например `2 ^ 3` = 8 |
| `%` | Остаток от деления, например `7 % 3` = 1 |
| `( )` | Группировка частей выражения, например `(2 + 3) * 4` |
| `pi`, `e` | Числа π и e |
| `abs(x)` | Модуль числа |
| `sqrt(x)`, `cbrt(x)` | Квадратный и кубический корни |
| `pow(x, y)` | x в степени y |
| `floor(x)`, `ceil(x)` | Округление вниз и вверх |
| `sin(x)`, `cos(x)`, `tan(x)`, `cot(x)` | Тригонометрические функции, угол указывается в радианах |
| `asin(x)`, `acos(x)`, `atan(x)` | Обратные тригонометрические функции |
| `sinh(x)`, `cosh(x)`, `tanh(x)` | Гиперболические функции |
| `log(x)`, `log2(x)`, `log10(x)` | Логарифмы по основаниям e, 2 и 10 |
| `exp(x)` | e в степени x |
| `signum(x)` | `1`, `-1` или `0`, как у [**Sign (Math)**](#sign-math) |

### Random Number

**Идентификатор:** `random_number`

Случайное целое число от `min` до `max`. Меняется при каждом обновлении текста.

- `min`, `max`: наименьшее и наибольшее числа

```
{"placeholder":"random_number","values":{"min":"1","max":"6"}}
```

### Max Number

**Идентификатор:** `maxnum`

Большее из двух чисел.

- `first`, `second`: числа

```
{"placeholder":"maxnum","values":{"first":"$$score","second":"$$best_score"}}
```

### Min Number

**Идентификатор:** `minnum`

Меньшее из двух чисел.

- `first`, `second`: числа

```
{"placeholder":"minnum","values":{"first":"10","second":"15"}}
```

### Absolute Number

**Идентификатор:** `absnum`

Число без знака минус. Например, `-10.5` преобразуется в `10.5`.

- `num`: число

```
{"placeholder":"absnum","values":{"num":"-10.5"}}
```

### Negate Number

**Идентификатор:** `negnum`

Меняет знак положительного числа на отрицательный: например, `10.5` преобразуется в `-10.5`. Ноль и отрицательные числа остаются без изменений.

- `num`: число

```
{"placeholder":"negnum","values":{"num":"10.5"}}
```

### Round (Math)

**Идентификатор:** `math_round`

Округляет число. Значение `2.5` округляется до `3`.

- `num`: число
- `decimals` (необязательно): количество знаков после запятой. Например, значение `2` преобразует `3.14159` в `3.14`. Значения `0`, `-1` или отсутствие параметра округляют до целого числа.

```
{"placeholder":"math_round","values":{"num":"3.14159","decimals":"2"}}
```

### Floor (Math)

**Идентификатор:** `math_floor`

Округляет число вниз до целого: например, `3.7` преобразуется в `3`, а `-3.2` — в `-4`.

- `num`: число

```
{"placeholder":"math_floor","values":{"num":"3.7"}}
```

### Ceiling (Math)

**Идентификатор:** `math_ceil`

Округляет число вверх до целого: например, `3.2` преобразуется в `4`, а `-3.7` — в `-3`.

- `num`: число

```
{"placeholder":"math_ceil","values":{"num":"3.2"}}
```

### Sign (Math)

**Идентификатор:** `math_sign`

Возвращает `1` для положительных чисел, `-1` для отрицательных и `0` для нуля.

- `num`: число

```
{"placeholder":"math_sign","values":{"num":"-3.14"}}
```

### *pi* (Math)

**Идентификатор:** `math_pi`

Число π: `3.141592653589793`.

```
{"placeholder":"math_pi"}
```

### Trigonometric Sine (Math)

**Идентификатор:** `math_sin`

Синус угла, заданного в радианах. Чтобы использовать градусы, сначала умножьте их на π / 180 с помощью Calculator.

- `angle`: угол в радианах

```
{"placeholder":"math_sin","values":{"angle":"1.5707963267948966"}}
```

### Trigonometric Cosine (Math)

**Идентификатор:** `math_cos`

Косинус угла, заданного в радианах.

- `angle`: угол в радианах

```
{"placeholder":"math_cos","values":{"angle":"0"}}
```

### Trigonometric Tangent (Math)

**Идентификатор:** `math_tan`

Тангенс угла, заданного в радианах.

- `angle`: угол в радианах

```
{"placeholder":"math_tan","values":{"angle":"0.7853981633974483"}}
```

### Hyperbolic Sine (Math)

**Идентификатор:** `math_sinh`

Гиперболический синус числа.

- `num`: число

```
{"placeholder":"math_sinh","values":{"num":"1"}}
```

### Hyperbolic Cosine (Math)

**Идентификатор:** `math_cosh`

Гиперболический косинус числа.

- `num`: число

```
{"placeholder":"math_cosh","values":{"num":"1"}}
```

### Hyperbolic Tangent (Math)

**Идентификатор:** `math_tanh`

Гиперболический тангенс числа.

- `num`: число

```
{"placeholder":"math_tanh","values":{"num":"1"}}
```

### Number Base Converter

**Идентификатор:** `number_base_convert`

Преобразует число в другую систему счисления, например из десятичной в двоичную или шестнадцатеричную. Можно преобразовывать и дробные числа: допускается до 16 знаков после точки. Буквы в результате будут заглавными, например `FF`.

- `input`: число
- `from_base` (необязательно): система счисления исходного числа `input`, от `2` до `36`. По умолчанию — `10`.
- `to_base` (необязательно): система счисления результата, от `2` до `36`. По умолчанию — `10`.

```
{"placeholder":"number_base_convert","values":{"input":"255","from_base":"10","to_base":"16"}}
```

## Текст

Эти заполнители находятся в категории **Advanced**.

### Uppercase Text

**Идентификатор:** `uppercase_text`

Преобразует текст в заглавные буквы: `Hello World` станет `HELLO WORLD`. [Коды форматирования](/text-formatting), например `&a`, остаются без изменений.

- `text`: текст

```
{"placeholder":"uppercase_text","values":{"text":"Hello World"}}
```

### Lowercase Text

**Идентификатор:** `lowercase_text`

Преобразует текст в строчные буквы: `HELLO WORLD` станет `hello world`. Коды форматирования остаются без изменений.

- `text`: текст

```
{"placeholder":"lowercase_text","values":{"text":"HELLO WORLD"}}
```

### Title Case Text

**Идентификатор:** `title_case_text`

Каждое слово начинается с заглавной буквы: `hello world` станет `Hello World`. Коды форматирования остаются без изменений.

- `text`: текст

```
{"placeholder":"title_case_text","values":{"text":"hello world"}}
```

### Sentence Case Text

**Идентификатор:** `sentence_case_text`

Каждое предложение начинается с заглавной буквы: `hello world. this is fancymenu!` станет `Hello world. This is fancymenu!`. Коды форматирования остаются без изменений.

- `text`: текст

```
{"placeholder":"sentence_case_text","values":{"text":"hello world. this is fancymenu!"}}
```

### Snake Case Text

**Идентификатор:** `snake_case_text`

Преобразует текст в строчные буквы и разделяет слова символом `_`: `Hello World` станет `hello_world`. Коды форматирования удаляются.

- `text`: текст

```
{"placeholder":"snake_case_text","values":{"text":"Hello World"}}
```

### Kebab Case Text

**Идентификатор:** `kebab_case_text`

Преобразует текст в строчные буквы и разделяет слова символом `-`: `Hello World` станет `hello-world`. Коды форматирования удаляются.

- `text`: текст

```
{"placeholder":"kebab_case_text","values":{"text":"Hello World"}}
```

### Alternating Case Text

**Идентификатор:** `alternating_case_text`

Чередует строчные и заглавные буквы: `alternating case` станет `aLtErNaTiNg CaSe`.

- `text`: текст

```
{"placeholder":"alternating_case_text","values":{"text":"alternating case"}}
```

### Toggle Case Text

**Идентификатор:** `toggle_case_text`

Меняет регистр букв на противоположный: строчные становятся заглавными, а заглавные — строчными. `Toggle Case` станет `tOGGLE cASE`.

- `text`: текст

```
{"placeholder":"toggle_case_text","values":{"text":"Toggle Case"}}
```

### Trim Text

**Идентификатор:** `trim_text`

Удаляет пробелы в начале и конце текста. Пробелы внутри текста остаются.

- `text`: текст

```
{"placeholder":"trim_text","values":{"text":"  Welcome!  "}}
```

### Crop Text

**Идентификатор:** `crop_text`

Удаляет заданное количество символов в начале и конце текста. Если удалить по одному символу с каждой стороны строки `hello world`, получится `ello worl`.

- `text`: текст
- `remove_from_start`: количество символов для удаления в начале
- `remove_from_end`: количество символов для удаления в конце

```
{"placeholder":"crop_text","values":{"text":"hello world","remove_from_start":"1","remove_from_end":"1"}}
```

### Split Text

**Идентификатор:** `split_text`

Разделяет текст и возвращает одну из его частей. Если разделить `Steve,Alex,Notch` по символу `,`, часть с индексом `1` будет `Alex`.

- `input`: текст
- `regex`: разделитель в виде регулярного выражения. Перед такими символами, как `.`, `|` и `?`, нужно ставить `\`, например `\.`.
- `max_parts` (необязательно): максимальное количество частей. Значение `-1` (по умолчанию) разделяет текст при каждом совпадении.
- `split_index`: индекс возвращаемой части. Нумерация начинается с `0`.

```
{"placeholder":"split_text","values":{"input":"Steve,Alex,Notch","regex":",","max_parts":"-1","split_index":"1"}}
```

### Replace Text

**Идентификатор:** `replace_text`

Заменяет части текста. Если в `Hello World!` заменить `World` на `FancyMenu`, получится `Hello FancyMenu!`.

- `text`: текст
- `search`: текст для поиска
- `replacement` (необязательно): текст для подстановки. По умолчанию — пустая строка, то есть найденный текст удаляется.
- `use_regex` (необязательно): значение `true` трактует `search` как регулярное выражение. Тогда `$1`, `$2` и так далее в `replacement` обозначают найденные группы. По умолчанию — `false`.
- `replace_all` (необязательно): значение `false` заменяет только первое совпадение. По умолчанию используется `true`.

```
{"placeholder":"replace_text","values":{"text":"Hello World!","search":"World","replacement":"FancyMenu","use_regex":"false","replace_all":"true"}}
```

### Switch Case

**Идентификатор:** `switch_case`

Возвращает результат для варианта, совпадающего с заданным значением. Если переменная `difficulty_level` равна `2`, пример вернёт `Hard Mode`.

- `value`: проверяемое значение
- `cases`: пары «значение и результат», например `1:Easy Mode,2:Hard Mode`. Значения и результаты не могут содержать `,` или `:`.
- `default` (необязательно): результат, если совпадений нет. Если значение не задано, заполнитель в таком случае остаётся без изменений.

```
{"placeholder":"switch_case","values":{"value":"$$difficulty_level","cases":"1:Easy Mode,2:Hard Mode","default":"Normal Mode"}}
```

### Localize Text

**Идентификатор:** `local`

Текст для ключа локализации на текущем языке игры, например `Singleplayer` для `menu.singleplayer`. Работает с ключами Minecraft, модов и вашими собственными ключами (см. раздел [«Локализация»](/localization)).

- `key`: ключ локализации

```
{"placeholder":"local","values":{"key":"menu.singleplayer"}}
```

### Stringify

**Идентификатор:** `stringify`

Сначала заменяет заполнители в тексте, а затем добавляет `\` перед каждым символом `"`, `{` и `}`. Благодаря этому внешний текст, например полученный с веб-сайта, не может стать заполнителем.

- `text`: текст

```
{"placeholder":"stringify","values":{"text":"{"placeholder":"webtext","values":{"link":"https://example.com/motd.txt"}}"}}
```

## Данные и файлы

Эти заполнители находятся в категории **Advanced**. Локальные пути начинаются от папки игры, например `/config/fancymenu/assets/news.txt`, и не могут выходить за её пределы (см. раздел [«Ресурсы»](/resources#local-resources)).

### JSON Parser

**Идентификатор:** `json`

Читает значение из JSON. Если найдено несколько результатов, каждый выводится на отдельной строке.

- `source`: текст JSON, файл JSON в папке игры или URL файла JSON
- `json_path`: путь к значению, например `$.name` или `$.players[0].name`. Подробнее о путях JSON см. на сайте [json.fancymenu.net](https://json.fancymenu.net).

```
{"placeholder":"json","values":{"source":"https://example.com/server_info.json","json_path":"$.news.title"}}
```

JSON из интернета загружается один раз, а затем повторно при перезагрузке FancyMenu. Изменения в файлах отображаются сразу.

| Путь | Результат |
|---|---|
| `$.name` | Значение `name` на верхнем уровне |
| `$.player.level` | Значение `level` внутри `player` |
| `$.items[0].id` | Значение `id` первого элемента `items` |
| `$.scores.*` | Все значения внутри `scores` |

### File Text

**Идентификатор:** `file_text`

Текст файла или URL. Файлы перечитываются каждую секунду, а URL — каждые 10 секунд. Пока текст загружается или недоступен для чтения, возвращается пустая строка.

- `path_or_url`: файл в папке игры или URL. Пути, начинающиеся с `.minecraft/`, указывают на стандартную папку Minecraft.
- `mode` (необязательно): `all` — весь текст, `last` — последние строки. По умолчанию используется `all`.
- `separator` (необязательно): текст между строками. По умолчанию используется `\n` (перенос строки).
- `last_lines` (необязательно): количество строк, возвращаемых в режиме `last`. По умолчанию — `1`.

```
{"placeholder":"file_text","values":{"path_or_url":"/config/fancymenu/assets/changelog.txt","mode":"all","separator":"\n","last_lines":"1"}}
```

### File Size

**Идентификатор:** `file_size`

Размер файла в байтах. Если файла нет, возвращается `0`. Пути, начинающиеся с `.minecraft/`, указывают на стандартную папку Minecraft.

- `path`: путь к файлу

```
{"placeholder":"file_size","values":{"path":"/config/fancymenu/assets/news.txt"}}
```

### File MD5

**Идентификатор:** `file_md5`

Хеш MD5 файла, например `d41d8cd98f00b204e9800998ecf8427e`. Если файла нет, возвращается пустая строка. Пути, начинающиеся с `.minecraft/`, указывают на стандартную папку Minecraft.

- `path`: путь к файлу

```
{"placeholder":"file_md5","values":{"path":"/config/fancymenu/assets/menu_music.ogg"}}
```

### Encode To Base64

**Идентификатор:** `base64_encode`

Кодирует текст в Base64: `Hello World` преобразуется в `SGVsbG8gV29ybGQ=`.

- `text`: текст

```
{"placeholder":"base64_encode","values":{"text":"Hello World"}}
```

### Decode From Base64

**Идентификатор:** `base64_decode`

Декодирует Base64 в текст: `SGVsbG8gV29ybGQ=` преобразуется в `Hello World`.

- `text`: текст в Base64

```
{"placeholder":"base64_decode","values":{"text":"SGVsbG8gV29ybGQ="}}
```

### Get NBT Data (Client-Side)

**Идентификатор:** `nbt_data_get`

Читает данные NBT, как команда `/data get`, из того, что игре известно о мире. Это работает быстро, но серверы отправляют игрокам не все данные.

- `source_type`: `entity` или `block`
- `entity_selector`: для `entity` — селектор, например `@s` (вы), `@p`, `@e[type=minecraft:horse,limit=1,sort=nearest]`, имя или UUID сущности. Селекторы могут содержать параметры `type`, `name`, `tag`, `limit`, `sort`, `distance`, `x`, `y`, `z`, `dx`, `dy` и `dz`. Используется первое совпадение.
- `block_pos`: для `block` — координаты блока-сущности, например сундука: `120 64 -35`
- `nbt_path`: путь NBT, например `foodLevel` или `Inventory[0].id`
- `scale` (необязательно): множитель для чисел. По умолчанию — `1.0`.
- `return_type` (необязательно): `value` (числа и текст без изменений), `string`, `snbt` или `json`. По умолчанию используется `value`.

```
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"foodLevel","scale":"1.0","return_type":"value"}}
```

### Get NBT Data (Server-Side)

**Идентификатор:** `nbt_data_get_server`

Читает данные NBT с сервера точно так же, как команда `/data get`. Для этого FancyMenu должен быть установлен на сервере. В одиночной игре работает всегда. Пока сервер не ответит, ничего не возвращается; после этого данные обновляются примерно каждые 100 миллисекунд.

- `source_type`: `entity`, `block` или `storage`
- `entity_selector`: для `entity` — любой селектор команды `/data get`, выбирающий одну сущность, например `@s` или `@e[type=minecraft:villager,limit=1,sort=nearest]`
- `block_pos`: для `block` — координаты, например `120 64 -35`, `~ ~-1 ~` или `^ ^ ^1`
- `storage_id`: для `storage` — ID хранилища команд, например `mypack:quests`
- `nbt_path` (необязательно): путь NBT. Если его не указать, возвращаются все данные.
- `scale` (необязательно): множитель для чисел. По умолчанию — `1.0`.
- `return_type` (необязательно): `value`, `string`, `snbt` или `json`. По умолчанию используется `value`.

```
{"placeholder":"nbt_data_get_server","values":{"source_type":"storage","storage_id":"mypack:quests","nbt_path":"completed","return_type":"value"}}
```

## Аудио

Эти заполнители считывают данные [аудиоэлементов](/elements#audio) открытого меню. Чтобы узнать ID аудиоэлемента, щёлкните по нему правой кнопкой мыши в редакторе макета и выберите **Copy Element ID**.

### Audio Element Volume

**Идентификатор:** `audio_element_vol`

Громкость аудиоэлемента от `0.0` (0%) до `1.0` (100%).

- `element_identifier`: ID аудиоэлемента

```
{"placeholder":"audio_element_vol","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Current Audio Track

**Идентификатор:** `audio_element_current_track`

Имя файла текущей дорожки, например `menu_theme.ogg`. Если ничего не воспроизводится, возвращается `---`.

- `element_identifier`: ID аудиоэлемента
- `display_name_mappings` (необязательно): отображаемые вместо имён файлов названия. Имя файла и отображаемое название разделяются с помощью `=>`, пары — с помощью `%:%`.

```
{"placeholder":"audio_element_current_track","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","display_name_mappings":"menu_theme.ogg=>Menu Theme%:%credits.ogg=>Credits Theme"}}
```

### Audio Duration

**Идентификатор:** `audio_duration`

Длительность текущей дорожки, например `03:45`. Во время загрузки возвращается `00:00`.

- `element_identifier`: ID аудиоэлемента

```
{"placeholder":"audio_duration","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Audio Play Time

**Идентификатор:** `audio_playtime`

Текущая позиция воспроизведения дорожки, например `01:30`. Если воспроизведение остановлено, возвращается `00:00` (или `0`).

- `element_identifier`: ID аудиоэлемента
- `show_percentage` (необязательно): значение `true` возвращает процент выполнения от `0` до `100`. По умолчанию — `false`.

```
{"placeholder":"audio_playtime","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","show_percentage":"false"}}
```

### Audio Playing State

**Идентификатор:** `audio_playing_state`

Возвращает `true`, пока аудиоэлемент воспроизводится, и `false`, если он приостановлен или остановлен.

- `element_identifier`: ID аудиоэлемента

```
{"placeholder":"audio_playing_state","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

## Клиент

Эти заполнители относятся к игре и её модам.

### Minecraft Version

**Идентификатор:** `mcversion`

Версия Minecraft, например `1.21.1`.

```
{"placeholder":"mcversion"}
```

### Mod Loader Name

**Идентификатор:** `loadername`

Название загрузчика модов, например `Fabric` или `NeoForge`.

```
{"placeholder":"loadername"}
```

### Mod Loader Version

**Идентификатор:** `loaderver`

Версия загрузчика модов, например `0.16.14`.

```
{"placeholder":"loaderver"}
```

### Mod Version

**Идентификатор:** `modversion`

Версия установленного мода, например `3.11.0`. Если мод не установлен, возвращается `0.0.0`.

- `modid`: ID мода, например `fancymenu`

```
{"placeholder":"modversion","values":{"modid":"fancymenu"}}
```

### Active Mods Count

**Идентификатор:** `loadedmods`

Количество загруженных модов. Библиотеки и моды внутри других модов тоже учитываются, поэтому результат часто превышает количество файлов модов.

```
{"placeholder":"loadedmods"}
```

### Total Mods Count

**Идентификатор:** `totalmods`

Приблизительное количество установленных модов: оно рассчитывается по файлам `.jar` в папке `mods` один раз при запуске игры. Это значение никогда не меньше, чем **Active Mods Count**.

```
{"placeholder":"totalmods"}
```

### World Loading Progress

**Идентификатор:** `world_load_progress`

Прогресс загрузки мира от `0` до `100`, отображаемый на экране загрузки. Подходит для индикаторов загрузки. На всех остальных экранах возвращается `0`.

```
{"placeholder":"world_load_progress"}
```

### Minecraft Option Value

**Идентификатор:** `minecraft_option_value`

Значение параметра Minecraft из файла `options.txt` в папке игры, например `12` для `renderDistance`. Если параметра с таким именем нет, возвращается пустая строка.

- `name`: имя параметра в `options.txt`

```
{"placeholder":"minecraft_option_value","values":{"name":"renderDistance"}}
```

### Keybind Key

**Идентификатор:** `keybind_key`

Клавиша, назначенная на привязку клавиши в данный момент, как на экране управления. Например, для прыжка это может быть `Space`. Если привязки с таким именем нет, возвращается пустая строка.

- `keybind`: имя привязки, например `key.jump` или `key.inventory`. Имена указаны в `options.txt` без начального `key_`: `key_key.jump` здесь означает `key.jump`.

```
Press {"placeholder":"keybind_key","values":{"keybind":"key.inventory"}} to open your inventory!
```

### Last World or Server

**Идентификатор:** `last_world_server`

Мир или сервер, к которому игрок подключался последним. Серверы отображаются в формате `play.example.net:25565`.

- `type`: `both` — миры и серверы, `world` — только миры, `server` — только серверы. При значении `world` или `server`, если последний объект был другого типа, возвращается пустая строка.
- `full_world_path` (необязательно): значение `false` возвращает только имя мира, например `New World`. Значение `true` возвращает путь к его папке. По умолчанию используется `true`.

```
{"placeholder":"last_world_server","values":{"type":"world","full_world_path":"false"}}
```

## Интерфейс

Эти заполнители относятся к открытому экрану и его элементам. В качестве ID элемента указывайте его идентификатор: щёлкните по элементу правой кнопкой мыши в редакторе макета и выберите **Copy Element ID**.

### Screen Width

**Идентификатор:** `guiwidth`

Ширина экрана в пикселях интерфейса. Это размер, используемый элементами, а не разрешение монитора.

```
{"placeholder":"guiwidth"}
```

### Screen Height

**Идентификатор:** `guiheight`

Высота экрана в пикселях интерфейса.

```
{"placeholder":"guiheight"}
```

### GUI Scale

**Идентификатор:** `guiscale`

Масштаб интерфейса игры, например `2`.

```
{"placeholder":"guiscale"}
```

### Current Screen Identifier

**Идентификатор:** `screenid`

[Идентификатор](/screen-identifiers) открытого экрана, например `title_screen`. Если экран не открыт, возвращается пустая строка.

```
{"placeholder":"screenid"}
```

### Element Width

**Идентификатор:** `elementwidth`

Ширина элемента в пикселях интерфейса. Если элемента с таким ID нет, возвращается `1`.

- `id`: ID элемента

```
{"placeholder":"elementwidth","values":{"id":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Element Height

**Идентификатор:** `elementheight`

Высота элемента в пикселях интерфейса. Если элемента с таким ID нет, возвращается `1`.

- `id`: ID элемента

```
{"placeholder":"elementheight","values":{"id":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Element X Position

**Идентификатор:** `elementposx`

Положение левого края элемента в пикселях интерфейса относительно левого края экрана. Если элемента с таким ID нет, возвращается `1`.

- `id`: ID элемента

```
{"placeholder":"elementposx","values":{"id":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Element Y Position

**Идентификатор:** `elementposy`

Положение верхнего края элемента в пикселях интерфейса относительно верхнего края экрана. Если элемента с таким ID нет, возвращается `1`.

- `id`: ID элемента

```
{"placeholder":"elementposy","values":{"id":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Text Element Content Height

**Идентификатор:** `text_element_content_height`

Высота, необходимая [текстовому элементу](/text-in-menus), чтобы отобразить весь текст без прокрутки, в пикселях интерфейса. Учитываются переносы строк, масштаб текста и межстрочный интервал, поэтому заполнитель подходит для фона, размер которого должен соответствовать тексту. Если элемент не является текстовым, возвращается `0`.

- `element_identifier`: ID текстового элемента

```
{"placeholder":"text_element_content_height","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Element Scroll Position

**Идентификатор:** `scroll_area_scroll_position`

Положение прокрутки содержимого [области прокрутки](/scrollable-areas) или текстового элемента в пикселях интерфейса от начала содержимого. Для других элементов возвращается `0`.

- `element_identifier`: ID элемента
- `axis`: `vertical` или `horizontal`. Любое другое значение соответствует направлению прокрутки элемента.

```
{"placeholder":"scroll_area_scroll_position","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","axis":"vertical"}}
```

### Element Scroll Percent

**Идентификатор:** `scroll_area_scroll_percent`

Положение прокрутки содержимого области прокрутки или текстового элемента от `0` (начало) до `100` (конец). Для других элементов и содержимого, которое не нужно прокручивать, возвращается `0`.

- `element_identifier`: ID элемента
- `axis`: `vertical` или `horizontal`. Любое другое значение соответствует направлению прокрутки элемента.

```
{"placeholder":"scroll_area_scroll_percent","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","axis":"vertical"}}
```

### Element Scroll Content Size

**Идентификатор:** `scroll_area_content_size`

Размер содержимого области прокрутки или текстового элемента: высота при значении `vertical`, ширина при `horizontal`. Для других элементов возвращается `0`.

- `element_identifier`: ID элемента
- `axis`: `vertical` или `horizontal`. Любое другое значение соответствует направлению прокрутки элемента.

```
{"placeholder":"scroll_area_content_size","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","axis":"vertical"}}
```

### Text Input Field Value

**Идентификатор:** `text_input_field_value`

Текст, введённый в [поле ввода текста](/elements#text-input-field) или текстовое поле исходного экрана. Если элемент не является текстовым полем, возвращается пустая строка.

- `element_identifier`: ID элемента

```
{"placeholder":"text_input_field_value","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Vanilla Widget Label/Text

**Идентификатор:** `vanillabuttonlabel`

Подпись кнопки или другого виджета исходного экрана, например `Options...`. Чтобы узнать локатор виджета, щёлкните по нему правой кнопкой мыши в редакторе макета и выберите **Copy Widget Locator**.

- `locator`: локатор виджета

```
{"placeholder":"vanillabuttonlabel","values":{"locator":"title_screen:mc_titlescreen_options_button"}}
```

### Mouse X Position

**Идентификатор:** `mouseposx`

Положение мыши в пикселях интерфейса относительно левого края экрана. В редакторе макета всегда равно `10`, чтобы элементы, следующие за мышью, оставались в доступном для редактирования месте.

```
{"placeholder":"mouseposx"}
```

### Mouse Y Position

**Идентификатор:** `mouseposy`

Положение мыши в пикселях интерфейса относительно верхнего края экрана. В редакторе макета всегда равно `10`.

```
{"placeholder":"mouseposy"}
```

### Clicks Per Second

**Идентификатор:** `clicks_per_second`

Количество нажатий кнопки мыши за последнюю секунду.

- `mouse_button` (необязательно): `left` или `right`. По умолчанию — `left`.

```
{"placeholder":"clicks_per_second","values":{"mouse_button":"left"}}
```

## Игрок

### Player Name

**Идентификатор:** `playername`

Имя игрока, например `Steve`.

```
{"placeholder":"playername"}
```

### Player UUID

**Идентификатор:** `playeruuid`

UUID игрока, например `c8cde7fe-7ced-11eb-9439-0242ac130002`.

```
{"placeholder":"playeruuid"}
```

### Last Death Message

**Идентификатор:** `lastdeathmessage`

Последнее сообщение о смерти игрока с момента запуска игры, например `Steve was slain by Zombie`. До первой смерти возвращается пустая строка.

- `as_json_component` (необязательно): значение `true` возвращает сообщение в виде JSON-компонента текста вместе с цветами. По умолчанию — `false`.

```
{"placeholder":"lastdeathmessage","values":{"as_json_component":"false"}}
```

## Реальное время

Эти заполнители относятся к времени на вашем компьютере. Для заполнителей даты и времени можно задать параметр `timezone`: `system` — часовой пояс компьютера (по умолчанию) или идентификатор, например `UTC`, `Europe/Berlin` или `America/New_York`. Список идентификаторов см. на сайте [nodatime.org/TimeZones](https://nodatime.org/TimeZones).

### Realtime Year

**Идентификатор:** `realtimeyear`

Год, например `2026`.

```
{"placeholder":"realtimeyear","values":{"timezone":"system"}}
```

### Realtime Month

**Идентификатор:** `realtimemonth`

Месяц от `01` до `12`.

```
{"placeholder":"realtimemonth","values":{"timezone":"system"}}
```

### Realtime Day

**Идентификатор:** `realtimeday`

День месяца от `01` до `31`.

```
{"placeholder":"realtimeday","values":{"timezone":"system"}}
```

### Realtime Hour

**Идентификатор:** `realtimehour`

Час от `00` до `23`.

- `twelve_hour_format` (необязательно): значение `true` выводит часы от `01` до `12`. По умолчанию — `false`.

```
{"placeholder":"realtimehour","values":{"twelve_hour_format":"false","timezone":"Europe/Berlin"}}
```

### Realtime Minute

**Идентификатор:** `realtimeminute`

Минута от `00` до `59`.

```
{"placeholder":"realtimeminute","values":{"timezone":"system"}}
```

### Realtime Second

**Идентификатор:** `realtimesecond`

Секунда от `00` до `59`.

```
{"placeholder":"realtimesecond","values":{"timezone":"system"}}
```

### Current Time in Millis (Unix Timestamp)

**Идентификатор:** `unix_time`

Количество миллисекунд с 1 января 1970 года (UTC), например `1732456789012`. Подходит для таймеров: сохраните значение в переменной, а затем вычтите его из более позднего значения с помощью Calculator.

```
{"placeholder":"unix_time"}
```

## Сервер

Эти заполнители запрашивают статус сервера, как и список серверов. Пока открыто настроенное меню, FancyMenu отправляет запрос каждые 30 секунд. До первого ответа сервер считается не в сети.

- `ip`: адрес сервера; порт указывается, если он отличается от стандартного, например `play.example.net` или `play.example.net:25566`

### Server Status

**Идентификатор:** `serverstatus`

Статус сервера: `Online` зелёным цветом или `Offline` красным.

```
{"placeholder":"serverstatus","values":{"ip":"play.example.net"}}
```

### Server Player Count

**Идентификатор:** `serverplayercount`

Количество игроков в сети и максимальное количество игроков, например `12/100`. До ответа сервера возвращается `0/0`.

```
{"placeholder":"serverplayercount","values":{"ip":"play.example.net"}}
```

### Server MOTD

**Идентификатор:** `servermotd`

Одна строка сообщения дня сервера.

- `line`: `1` или `2`

```
{"placeholder":"servermotd","values":{"ip":"play.example.net","line":"1"}}
```

### Server PING

**Идентификатор:** `serverping`

Задержка до сервера в миллисекундах, например `54`. Если сервер не в сети, возвращается `-1`.

```
{"placeholder":"serverping","values":{"ip":"play.example.net"}}
```

### Server Version

**Идентификатор:** `serverversion`

Версия Minecraft на сервере, например `1.21.1`. Некоторые серверы показывают здесь собственный текст. До ответа сервера возвращается `---`.

```
{"placeholder":"serverversion","values":{"ip":"play.example.net"}}
```

## Видео

Эти заполнители считывают данные [видеoэлементов и видеофонов меню](/video) открытого меню. Чтобы узнать ID видеоэлемента, щёлкните по нему правой кнопкой мыши в редакторе макета и выберите **Copy Element ID**. Для фона щёлкните правой кнопкой мыши по фону редактора и выберите **Copy Background Identifier**.

### Video Element Volume

**Идентификатор:** `video_element_vol`

Громкость видеоэлемента от `0.0` (0%) до `1.0` (100%).

- `element_identifier`: ID видеоэлемента

```
{"placeholder":"video_element_vol","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Video Element Duration

**Идентификатор:** `video_element_duration`

Длительность видео в видеоэлементе, например `02:00`. Во время загрузки возвращается `00:00` (или `0`).

- `element_identifier`: ID видеоэлемента
- `output_as_timestamp` (необязательно): значение `true` возвращает миллисекунды, например `120000`. По умолчанию — `false`.

```
{"placeholder":"video_element_duration","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","output_as_timestamp":"false"}}
```

### Video Element Play Time

**Идентификатор:** `video_element_playtime`

Текущая позиция воспроизведения видео в видеоэлементе, например `00:45`. Во время загрузки возвращается `00:00` (или `0`).

- `element_identifier`: ID видеоэлемента
- `show_percentage` (необязательно): значение `true` возвращает прогресс от `0` до `100`. По умолчанию — `false`.
- `output_as_timestamp` (необязательно): значение `true` возвращает миллисекунды. Если оба параметра имеют значение `true`, приоритет имеет `show_percentage`. По умолчанию — `false`.

```
{"placeholder":"video_element_playtime","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","show_percentage":"false","output_as_timestamp":"false"}}
```

### Video Element Paused State

**Идентификатор:** `video_element_paused_state`

Возвращает `true`, если видеоэлемент приостановлен, и `false` в противном случае.

- `element_identifier`: ID видеоэлемента

```
{"placeholder":"video_element_paused_state","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Video Background Volume

**Идентификатор:** `video_background_vol`

Громкость видеофона меню от `0.0` (0%) до `1.0` (100%).

- `background_identifier`: идентификатор фона меню

```
{"placeholder":"video_background_vol","values":{"background_identifier":"8c2e4f6a-1b3d-4e5f-8a7b-9c0d1e2f3a4b-1732456789012"}}
```

### Video Background Duration

**Идентификатор:** `video_background_duration`

Длительность видео в качестве фона меню, например `03:00`. Во время загрузки возвращается `00:00` (или `0`).

- `background_identifier`: идентификатор фона меню
- `output_as_timestamp` (необязательно): значение `true` возвращает миллисекунды. По умолчанию — `false`.

```
{"placeholder":"video_background_duration","values":{"background_identifier":"8c2e4f6a-1b3d-4e5f-8a7b-9c0d1e2f3a4b-1732456789012","output_as_timestamp":"false"}}
```

### Video Background Play Time

**Идентификатор:** `video_background_playtime`

Текущая позиция воспроизведения видеофона меню, например `01:00`. Во время загрузки возвращается `00:00` (или `0`).

- `background_identifier`: идентификатор фона меню
- `show_percentage` (необязательно): значение `true` возвращает прогресс от `0` до `100`. По умолчанию — `false`.
- `output_as_timestamp` (необязательно): значение `true` возвращает миллисекунды. Если оба параметра имеют значение `true`, приоритет имеет `show_percentage`. По умолчанию — `false`.

```
{"placeholder":"video_background_playtime","values":{"background_identifier":"8c2e4f6a-1b3d-4e5f-8a7b-9c0d1e2f3a4b-1732456789012","show_percentage":"true","output_as_timestamp":"false"}}
```

### Video Background Paused State

**Идентификатор:** `video_background_paused_state`

Возвращает `true`, если видеофон меню приостановлен, и `false` в противном случае.

- `background_identifier`: идентификатор фона меню

```
{"placeholder":"video_background_paused_state","values":{"background_identifier":"8c2e4f6a-1b3d-4e5f-8a7b-9c0d1e2f3a4b-1732456789012"}}
```

## Мир: характеристики игрока

Категория **World** относится к миру, в котором вы играете. Для работы большинству её заполнителей нужен загруженный мир. Если мир не загружен, они возвращают `0`, `0.0` или пустую строку.

### Current Player Health

**Идентификатор:** `current_player_health`

Здоровье игрока, например `20.0`. Одно сердечко соответствует `2.0`.

```
{"placeholder":"current_player_health"}
```

### Max Player Health

**Идентификатор:** `max_player_health`

Максимальное здоровье игрока, например `20.0`.

```
{"placeholder":"max_player_health"}
```

### Current Player Health (Percent)

**Идентификатор:** `current_player_health_percent`

Здоровье игрока в процентах от `0` до `100`.

```
{"placeholder":"current_player_health_percent"}
```

### Current Player Absorption Health

**Идентификатор:** `current_player_absorption_health`

Запас здоровья от поглощения урона у игрока (золотые сердца), например `4.0`.

```
{"placeholder":"current_player_absorption_health"}
```

### Max Player Absorption Health

**Идентификатор:** `max_player_absorption_health`

Максимальный запас здоровья от поглощения урона, например `4.0`.

```
{"placeholder":"max_player_absorption_health"}
```

### Current Player Absorption Health (Percent)

**Идентификатор:** `current_player_absorption_health_percent`

Запас здоровья от поглощения урона в процентах от `0` до `100`.

```
{"placeholder":"current_player_absorption_health_percent"}
```

### Current Player Food Level

**Идентификатор:** `current_player_hunger`

Уровень сытости игрока от `0.0` до `20.0`.

```
{"placeholder":"current_player_hunger"}
```

### Max Player Food Level

**Идентификатор:** `max_player_hunger`

Максимальный уровень сытости игрока: всегда `20.0`.

```
{"placeholder":"max_player_hunger"}
```

### Current Player Food Level (Percent)

**Идентификатор:** `current_player_hunger_percent`

Уровень сытости игрока в процентах от `0` до `100`.

```
{"placeholder":"current_player_hunger_percent"}
```

### Current Player Hunger Saturation

**Идентификатор:** `current_player_hunger_saturation`

Насыщение игрока, например `5.0`. Уровень сытости начнёт снижаться, только когда насыщение закончится.

```
{"placeholder":"current_player_hunger_saturation"}
```

### Current Player Armor

**Идентификатор:** `current_player_armor`

Очки брони игрока от `0.0` до `20.0`.

```
{"placeholder":"current_player_armor"}
```

### Max Player Armor

**Идентификатор:** `max_player_armor`

Максимальное количество очков брони: всегда `20.0`.

```
{"placeholder":"max_player_armor"}
```

### Current Player Armor (Percent)

**Идентификатор:** `current_player_armor_percent`

Очки брони игрока в процентах от `0` до `100`.

```
{"placeholder":"current_player_armor_percent"}
```

### Player Armor Toughness

**Идентификатор:** `player_armor_toughness`

Прочность брони игрока, например `8.0` при полном комплекте алмазной брони.

```
{"placeholder":"player_armor_toughness"}
```

### Current Player Oxygen Level

**Идентификатор:** `current_player_oxygen`

Запас воздуха игрока под водой от `0.0` до `300.0`.

```
{"placeholder":"current_player_oxygen"}
```

### Max Player Oxygen Level

**Идентификатор:** `max_player_oxygen`

Максимальный запас воздуха игрока, например `300.0`.

```
{"placeholder":"max_player_oxygen"}
```

### Current Player Oxygen Level (Percent)

**Идентификатор:** `current_player_oxygen_percent`

Запас воздуха игрока в процентах от `0` до `100`.

```
{"placeholder":"current_player_oxygen_percent"}
```

### Current Player Level

**Идентификатор:** `current_player_level`

Уровень опыта игрока, например `30`.

```
{"placeholder":"current_player_level"}
```

### Current Player Experience

**Идентификатор:** `current_player_exp`

Общее количество очков опыта игрока, например `1395.0`. Это не уровень.

```
{"placeholder":"current_player_exp"}
```

### Player Experience Progress (Percent)

**Идентификатор:** `current_player_exp_progress`

Заполнение полосы опыта от `0` до `100`.

```
{"placeholder":"current_player_exp_progress"}
```

### Player Attack Strength (Percent)

**Идентификатор:** `player_attack_strength`

Заряд следующей атаки от `0` до `100`, как на индикаторе атаки.

```
{"placeholder":"player_attack_strength"}
```

### Player Game Mode

**Идентификатор:** `player_gamemode`

Режим игры: `survival`, `creative`, `adventure` или `spectator`.

```
{"placeholder":"player_gamemode"}
```

### Player Item Use Progress (FM)

**Идентификатор:** `player_item_use_progress_fm`

Прогресс использования предмета игроком — например, еды, зелья или натягивания лука — от `0.0` до `1.0`.

```
{"placeholder":"player_item_use_progress_fm"}
```

### Current Mount Health

**Идентификатор:** `current_mount_health`

Здоровье существа, на котором едет игрок, например лошади: `30.0`.

```
{"placeholder":"current_mount_health"}
```

### Max Mount Health

**Идентификатор:** `max_mount_health`

Максимальное здоровье существа, на котором едет игрок.

```
{"placeholder":"max_mount_health"}
```

### Current Mount Health (Percent)

**Идентификатор:** `current_mount_health_percent`

Здоровье существа, на котором едет игрок, в процентах от `0` до `100`.

```
{"placeholder":"current_mount_health_percent"}
```

### Current Mount Jump Meter (Percent)

**Идентификатор:** `current_mount_jump_meter`

Заряд прыжка лошади от `0` до `100`.

```
{"placeholder":"current_mount_jump_meter"}
```

### Active Effects Count

**Идентификатор:** `effects_count`

Количество действующих эффектов игрока.

```
{"placeholder":"effects_count"}
```

### Active Effect

**Идентификатор:** `active_effect`

ID эффекта игрока, например `minecraft:speed`. Эффекты перечисляются в порядке значков в правом верхнем углу. Если эффекта с таким индексом нет, возвращается пустая строка.

- `effect_index`: позиция эффекта. Нумерация начинается с `0`.

```
{"placeholder":"active_effect","values":{"effect_index":"0"}}
```

## Мир: инвентарь и предметы

Эти заполнители находятся в категории **World**. Номера слотов: `0`–`8` — панель быстрого доступа, `9`–`35` — остальная часть инвентаря, `36`–`39` — броня от ботинок до шлема, `40` — вторая рука.

### Selected Hotbar Slot

**Идентификатор:** `active_hotbar_slot`

Выбранный слот панели быстрого доступа от `0` до `8`.

```
{"placeholder":"active_hotbar_slot"}
```

### Slot Item

**Идентификатор:** `slot_item`

ID предмета в слоте, например `minecraft:diamond_sword`. Для пустых слотов возвращается `minecraft:air`.

- `slot`: номер слота

```
{"placeholder":"slot_item","values":{"slot":"0"}}
```

### Slot Item Count

**Идентификатор:** `slot_item_count`

Количество предметов в слоте, например `64`.

- `slot`: номер слота

```
{"placeholder":"slot_item_count","values":{"slot":"0"}}
```

### Slot Item Durability

**Идентификатор:** `slot_item_durability`

Прочность предмета в слоте. Для предметов без прочности возвращается `0`.

- `slot`: номер слота
- `format` (необязательно): `current` (оставшаяся прочность), `max` (максимальная прочность), `damage` (израсходованная прочность) или `percentage` (оставшаяся прочность в процентах от `0` до `100`). По умолчанию используется `current`.

```
{"placeholder":"slot_item_durability","values":{"slot":"39","format":"percentage"}}
```

### Slot Item Display Name (FM)

**Идентификатор:** `slot_item_display_name_fm`

Имя предмета в слоте в виде JSON-компонента текста с цветом редкости, например `{"text":"Diamond Sword","color":"aqua"}`. В режиме наблюдателя для слотов панели быстрого доступа возвращаются названия меню наблюдателя.

- `slot`: номер слота
- `ignore_spectator` (необязательно): значение `true` возвращает имена предметов и в режиме наблюдателя. По умолчанию — `false`.

```
{"placeholder":"slot_item_display_name_fm","values":{"slot":"0","ignore_spectator":"false"}}
```

### Inventory Item Count

**Идентификатор:** `inventory_item_count`

Количество предметов, имеющихся у игрока во всём инвентаре.

- `item`: ID предмета, например `minecraft:diamond`. Если значение не задано, учитываются все предметы.

```
{"placeholder":"inventory_item_count","values":{"item":"minecraft:diamond"}}
```

### Inventory Slot Food Point Restore Amount

**Идентификатор:** `inventory_slot_food_point_restore_amount`

Количество очков сытости, восстанавливаемых предметом в слоте при употреблении. Например, яблоко восстанавливает `4.0`. Для несъедобных предметов возвращается `0.0`.

- `slot`: номер слота

```
{"placeholder":"inventory_slot_food_point_restore_amount","values":{"slot":"0"}}
```

### Item Category

**Идентификатор:** `item_category`

Вкладка творческого инвентаря, в которой находится предмет, например `Combat`. Для предметов без вкладки возвращается `UNKNOWN`.

- `item`: ID предмета
- `as_key` (необязательно): значение `true` возвращает ID вкладки, например `minecraft:combat`. По умолчанию — `false`.

```
{"placeholder":"item_category","values":{"item":"minecraft:diamond_sword","as_key":"false"}}
```

### Hovered Inventory Item

**Идентификатор:** `hovered_inventory_item`

ID предмета, на который наведён указатель мыши в окне инвентаря, например `minecraft:apple`. Если такого предмета нет, возвращается пустая строка.

```
{"placeholder":"hovered_inventory_item"}
```

## Мир: HUD и боссы

Эти заполнители находятся в категории **World**. Заполнители рейда считывают данные рейда, индикатор которого отображается вверху экрана; для их работы FancyMenu должен быть установлен на сервере. В одиночной игре они работают всегда. Если рейда нет, возвращается `0` или пустая строка.

### Action Bar Message (FM)

**Идентификатор:** `action_bar_message_fm`

Сообщение над панелью быстрого доступа в виде JSON-компонента текста, например `{"text":"You may not rest now","color":"red"}`. Если сообщения нет, возвращается пустая строка.

```
{"placeholder":"action_bar_message_fm"}
```

### Action Bar Message Time (FM)

**Идентификатор:** `action_bar_message_time_fm`

Количество тиков, в течение которых сообщение над панелью быстрого доступа ещё отображается. 20 тиков равны одной секунде.

```
{"placeholder":"action_bar_message_time_fm"}
```

### Highlighted Item Time (FM)

**Идентификатор:** `highlighted_item_time_fm`

Количество тиков, в течение которых имя выбранного предмета ещё отображается над панелью быстрого доступа.

```
{"placeholder":"highlighted_item_time_fm"}
```

### Current HUD Title/Subtitle

**Идентификатор:** `current_title`

Заголовок или подзаголовок, отображаемый в данный момент, например заданный командой `/title`. Если его нет, возвращается пустая строка.

- `is_subtitle` (необязательно): значение `true` возвращает подзаголовок. По умолчанию — `false`.
- `as_json` (необязательно): значение `true` возвращает его в виде JSON-компонента текста. По умолчанию — `false`.

```
{"placeholder":"current_title","values":{"is_subtitle":"false","as_json":"false"}}
```

### Bosses Count

**Идентификатор:** `boss_count`

Количество отображаемых в данный момент полос здоровья боссов.

```
{"placeholder":"boss_count"}
```

### Boss Name

**Идентификатор:** `boss_name`

Имя босса в полосе здоровья, например `Ender Dragon`. Если полосы с таким индексом нет, возвращается пустая строка.

- `boss_index`: позиция полосы здоровья. Верхняя полоса имеет индекс `0`.
- `as_json` (необязательно): значение `true` возвращает имя в виде JSON-компонента текста. По умолчанию — `false`.

```
{"placeholder":"boss_name","values":{"boss_index":"0","as_json":"false"}}
```

### Current Boss Health (Percent)

**Идентификатор:** `current_boss_health`

Заполнение полосы здоровья босса от `0` до `100`.

- `boss_index`: позиция полосы здоровья. Верхняя полоса имеет индекс `0`.

```
{"placeholder":"current_boss_health","values":{"boss_index":"0"}}
```

### Total Active Raid Waves

**Идентификатор:** `active_raid_total_waves`

Общее количество волн рейда, включая бонусную волну.

```
{"placeholder":"active_raid_total_waves"}
```

### Remaining Active Raid Waves

**Идентификатор:** `active_raid_remaining_waves`

Количество оставшихся волн рейда.

```
{"placeholder":"active_raid_remaining_waves"}
```

### Current Active Raid Wave

**Идентификатор:** `active_raid_current_wave`

Номер последней начавшейся волны: например, во время атаки первой волны возвращается `1`. До начала первой волны возвращается `0`.

```
Волна {"placeholder":"active_raid_current_wave"} из {"placeholder":"active_raid_total_waves"}
```

### Active Raid Alive Raiders Count

**Идентификатор:** `active_raid_alive_raiders_count`

Количество выживших разбойников в рейде.

```
{"placeholder":"active_raid_alive_raiders_count"}
```

### Active Raid Alive Raiders List

**Идентификатор:** `active_raid_alive_raiders_list`

Список всех выживших разбойников через запятую. Каждый элемент содержит ID существа и UUID разбойника, например `minecraft:pillager#0d9a4b2e-5f1c-4a8e-9b3d-6c2f1e7a8b90`.

```
{"placeholder":"active_raid_alive_raiders_list"}
```

## Мир: положение и камера

Эти заполнители находятся в категории **World**.

### Player X Coordinate

**Идентификатор:** `player_x_coordinate`

Координата X блока, в котором стоит игрок, например `125`.

```
{"placeholder":"player_x_coordinate"}
```

### Player Y Coordinate

**Идентификатор:** `player_y_coordinate`

Координата Y блока, в котором стоит игрок, например `64`.

```
{"placeholder":"player_y_coordinate"}
```

### Player Z Coordinate

**Идентификатор:** `player_z_coordinate`

Координата Z блока, в котором стоит игрок, например `-250`.

```
{"placeholder":"player_z_coordinate"}
```

### Player View Direction

**Идентификатор:** `player_view_direction`

Направление взгляда игрока: `north`, `east`, `south` или `west`.

```
{"placeholder":"player_view_direction"}
```

### Player Position Delta X (FM)

**Идентификатор:** `player_position_delta_x_fm`

Расстояние, пройденное игроком по оси X с прошлого тика, в блоках, например `0.12`. При движении в обратном направлении значение отрицательное.

```
{"placeholder":"player_position_delta_x_fm"}
```

### Player Position Delta Y (FM)

**Идентификатор:** `player_position_delta_y_fm`

Расстояние, пройденное игроком по оси Y с прошлого тика, например `-0.08` при падении.

```
{"placeholder":"player_position_delta_y_fm"}
```

### Player Position Delta Z (FM)

**Идентификатор:** `player_position_delta_z_fm`

Расстояние, пройденное игроком по оси Z с прошлого тика.

```
{"placeholder":"player_position_delta_z_fm"}
```

### Camera Rotation X (FM)

**Идентификатор:** `camera_rotation_x_fm`

Угол наклона камеры вверх или вниз в градусах: от `-90.0` (вертикально вверх) до `90.0` (вертикально вниз).

```
{"placeholder":"camera_rotation_x_fm"}
```

### Camera Rotation Y (FM)

**Идентификатор:** `camera_rotation_y_fm`

Направление камеры в градусах от `-180.0` до `180.0`. Значение `0.0` соответствует югу.

```
{"placeholder":"camera_rotation_y_fm"}
```

### Camera Rotation Delta X (FM)

**Идентификатор:** `camera_rotation_delta_x_fm`

Угол, на который камера повернулась вверх или вниз с прошлого тика, в градусах.

```
{"placeholder":"camera_rotation_delta_x_fm"}
```

### Camera Rotation Delta Y (FM)

**Идентификатор:** `camera_rotation_delta_y_fm`

Угол, на который камера повернулась влево или вправо с прошлого тика, в градусах.

```
{"placeholder":"camera_rotation_delta_y_fm"}
```

## Мир: сведения о мире

Эти заполнители находятся в категории **World**.

### World Day Time

**Идентификатор:** `world_daytime`

Время суток в мире, выраженное в тиках. В сутках 24000 тиков; день начинается в 6:00 утра. Счётчик продолжает увеличиваться с каждым днём, поэтому выражение `{"placeholder":"world_daytime"} % 24000` в Calculator возвращает время текущего дня.

```
{"placeholder":"world_daytime"}
```

### World Day Time Hour

**Идентификатор:** `world_daytime_hour`

Час игрового времени от `00` до `23`.

- `twelve_hour_format` (необязательно): значение `true` выводит часы от `01` до `12`. По умолчанию — `false`.

```
{"placeholder":"world_daytime_hour","values":{"twelve_hour_format":"false"}}
```

### World Day Time Minute

**Идентификатор:** `world_daytime_minute`

Минута игрового времени от `00` до `59`.

```
{"placeholder":"world_daytime_hour"}:{"placeholder":"world_daytime_minute"}
```

### World Game Time

**Идентификатор:** `game_time`

Общее количество тиков, прошедших в мире. В отличие от времени суток, команды вроде `/time set` не изменяют это значение.

```
{"placeholder":"game_time"}
```

### World Difficulty

**Идентификатор:** `world_difficulty`

Сложность мира: `peaceful`, `easy`, `normal` или `hard`.

```
{"placeholder":"world_difficulty"}
```

### Current Dimension

**Идентификатор:** `current_dimension`

Измерение, в котором находится игрок, например `minecraft:overworld`.

- `as_key` (необязательно): значение `false` возвращает название, например `Overworld`. Если у измерения нет названия, возвращается его ID. По умолчанию — `true`.

```
{"placeholder":"current_dimension","values":{"as_key":"false"}}
```

### Current Biome

**Идентификатор:** `current_biome`

Биом, в котором находится игрок, например `minecraft:plains`.

- `as_key` (необязательно): значение `false` возвращает название, например `Plains`. По умолчанию — `true`.

```
{"placeholder":"current_biome","values":{"as_key":"false"}}
```

### Current World Seed

**Идентификатор:** `current_world_seed`

Сид мира одиночной игры, например `-4172144997902289642`. На серверах возвращается пустая строка.

```
{"placeholder":"current_world_seed"}
```

### Gamerule Value

**Идентификатор:** `gamerule_value`

Значение игрового правила, например `true` или `3`. В одиночной игре работает всегда. На сервере для работы FancyMenu должен быть установлен и на серверной стороне. Если правила с таким именем нет, возвращается пустая строка.

- `name`: имя игрового правила, например `keep_inventory`. В Minecraft 1.21.10 и более ранних версиях правила называются, например, `keepInventory`; эти старые имена работают и в новых версиях.

```
{"placeholder":"gamerule_value","values":{"name":"keep_inventory"}}
```

### Current Server IP

**Идентификатор:** `current_server_ip`

Адрес сервера, на котором находится игрок, например `play.example.net`. В одиночной игре возвращается пустая строка.

```
{"placeholder":"current_server_ip"}
```

### World Players List

**Идентификатор:** `world_players_list`

Имена игроков в мире, о которых знает игра, отсортированные по алфавиту, например `Alex, Notch, Steve`.

- `separator` (необязательно): текст между именами. По умолчанию используется `, `.

```
{"placeholder":"world_players_list","values":{"separator":", "}}
```

## Мир: сохранения миров

Эти заполнители находятся в категории **World** и работают в любом меню, даже если мир не загружен.

### World Save Count

**Идентификатор:** `level_save_count`

Количество миров одиночной игры.

```
{"placeholder":"level_save_count"}
```

### World Save Names

**Идентификатор:** `level_save_names`

Названия всех миров одиночной игры в том же порядке, что и в списке миров, например `Survival World, Creative Test`.

- `separator` (необязательно): текст между названиями. По умолчанию используется `, `.

```
{"placeholder":"level_save_names","values":{"separator":", "}}
```

### World Save Data

**Идентификатор:** `level_save_data`

Все данные мира одиночной игры в формате JSON, например `{"file_name":"Survival World","game_type":"survival","difficulty":"normal",...}`. Содержатся поля `file_name`, `display_name`, `game_type`, `difficulty`, `allow_commands`, `last_played` (метка времени Unix), `minecraft_version_name` и другие. Чтобы прочитать отдельные значения, используйте [**JSON Parser**](#json-parser).

- `level_name`: имя мира в точности как в списке миров

```
{"placeholder":"json","values":{"source":"{"placeholder":"level_save_data","values":{"level_name":"Survival World"}}","json_path":"$.game_type"}}
```

## Другое

У этих заполнителей нет категории, поэтому в меню заполнителей они перечислены под категориями.

### FPS (Frames Per Second)

**Идентификатор:** `fps`

Количество кадров в секунду, например `120`.

```
{"placeholder":"fps"}
```

### Used RAM in MB

**Идентификатор:** `usedram`

Объём ОЗУ, используемый игрой в данный момент, в МБ, например `4096`.

```
{"placeholder":"usedram"}
```

### Max RAM in MB

**Идентификатор:** `maxram`

Максимальный объём ОЗУ, доступный игре, в МБ, например `8192`.

```
{"placeholder":"maxram"}
```

### Used RAM in %

**Идентификатор:** `percentram`

Используемый игрой объём ОЗУ в процентах от максимального, например `50`.

```
{"placeholder":"percentram"}
```

### CPU Usage (JVM)

**Идентификатор:** `jvmcpu`

Загрузка процессора игрой в процентах, например `25.5`.

```
{"placeholder":"jvmcpu"}
```

### CPU Usage (OS)

**Идентификатор:** `oscpu`

Загрузка процессора всем компьютером в процентах, например `42.8`.

```
{"placeholder":"oscpu"}
```

### CPU Info

**Идентификатор:** `cpuinfo`

Название процессора, например `Intel(R) Core(TM) i7-10700K CPU @ 3.80GHz`.

```
{"placeholder":"cpuinfo"}
```

### GPU Info

**Идентификатор:** `gpuinfo`

Название видеоустройства, используемого игрой, например `NVIDIA GeForce RTX 3080`.

```
{"placeholder":"gpuinfo"}
```

### OpenGL Version

**Идентификатор:** `glver`

Информация о драйвере видеоустройства, используемого игрой, например `4.6.0 NVIDIA 566.36`.

```
{"placeholder":"glver"}
```

### Java Version

**Идентификатор:** `javaver`

Версия Java, на которой работает игра, например `21.0.5`.

```
{"placeholder":"javaver"}
```

### Java Virtual Machine

**Идентификатор:** `jvmname`

Название виртуальной машины Java, например `OpenJDK 64-Bit Server VM`.

```
{"placeholder":"jvmname"}
```

### Operating System Name

**Идентификатор:** `osname`

Название операционной системы, например `Windows 11`.

```
{"placeholder":"osname"}
```

### Uptime Duration

**Идентификатор:** `uptime_duration`

Время работы игры в секундах, например `742`.

- `output_as_millis` (необязательно): значение `true` возвращает миллисекунды. По умолчанию — `false`.

```
{"placeholder":"uptime_duration","values":{"output_as_millis":"false"}}
```

### Random Text

**Идентификатор:** `randomtext`

Случайная строка из текстового файла, с веб-сайта или из введённого вами текста, например случайный совет. Файлы и URL перечитываются каждые 30 секунд.

- `source`: файл `.txt` в папке игры, URL или строки, разделённые символами `\n`, например `Совет 1\nСовет 2\nСовет 3`
- `interval` (необязательно): интервал в секундах между выбором новой строки. Значение `0` выбирает одну строку на игровой сеанс. По умолчанию — `10`.

```
{"placeholder":"randomtext","values":{"source":"/config/fancymenu/assets/tips.txt","interval":"10"}}
```

### Web Text

**Идентификатор:** `webtext`

Первая строка текста веб-страницы, например текстового файла на вашем сайте. Загружается один раз, а затем повторно при перезагрузке FancyMenu. Во время загрузки возвращается пустая строка.

- `link`: URL страницы

```
{"placeholder":"webtext","values":{"link":"https://example.com/motd.txt"}}
```

### Absolute File/Folder Path

**Идентификатор:** `absolute_path`

Полный путь к файлу или папке в папке игры, например `C:/Users/Steve/AppData/Roaming/.minecraft/config/fancymenu`.

- `short_path`: путь внутри папки игры

```
{"placeholder":"absolute_path","values":{"short_path":"config/fancymenu"}}
```

### Text Character Count

**Идентификатор:** `text_character_count`

Количество символов в тексте: в строке `Hello World!` их `12`.

- `text`: текст

```
{"placeholder":"text_character_count","values":{"text":"$$player_nickname"}}
```

### Text Width

**Идентификатор:** `text_width`

Ширина текста в пикселях интерфейса: строка `Hello World!` имеет ширину `57`. Коды форматирования, например `&l`, учитываются так же, как в игре, поэтому жирный текст шире.

- `text`: текст

```
{"placeholder":"text_width","values":{"text":"Hello World!"}}
```

### Text Height

**Идентификатор:** `text_height`

Высота текста в пикселях интерфейса с учётом всех строк. Перенос строки обозначается как `\n`. Чтобы подогнать размер под текстовый элемент, используйте [**Text Element Content Height**](#text-element-content-height): этот заполнитель также учитывает масштаб текста, межстрочный интервал и переносы строк.

- `text`: текст

```
{"placeholder":"text_height","values":{"text":"First line\nSecond line"}}
```

### Clipboard Content

**Идентификатор:** `clipboard_content`

Текст из буфера обмена компьютера. Если буфер обмена пуст, возвращается пустая строка.

```
{"placeholder":"clipboard_content"}
```
