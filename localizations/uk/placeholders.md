---
title: Заповнювачі
description: >-
  Відображайте у своїх текстах актуальні значення, як-от ім’я гравця, час або
  кількість гравців на сервері, а також будь-які заповнювачі FancyMenu.
sourceBlobSha: 951d7772d640bc6b19d6f4dcc2fef4adcd1f13aa
---

# Заповнювачі

Заповнювачі — це короткі коди, які FancyMenu замінює актуальними значеннями, як-от ім’ям гравця, часом або кількістю гравців на сервері. Вони працюють у тексті елементів, написах кнопок, підказках, значеннях дій і вимог, а також у більшості інших текстових полів.

<img width="800" alt="Додавання заповнювача Player Name до текстового елемента в редакторі макета: заповнювачі в текстовому редакторі, категорія Player і текст із привітанням гравця на ім’я" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/placeholders_add.gif?raw=true">

> [!TIP]
> Ваші власні [змінні](/variables) працюють у тих самих текстах: використовуйте `$$` і назву змінної, наприклад `$$coins`.

# Додавання заповнювачів

1. Відкрийте текст у текстовому редакторі, наприклад **Text Content** текстового [елемента](/text-in-menus). Біля текстових полів у вікнах, наприклад полів зі значеннями дій, є кнопка **Open in Editor**.
2. Клацніть місце, де має бути заповнювач.
3. Клацніть **Placeholders** у верхньому правому куті текстового редактора.
4. Клацніть категорію або знайдіть заповнювач за назвою, ідентифікатором чи описом. Кнопка **BACK** повертає до списку категорій. Заповнювачі без категорії наведено під категоріями.
5. Наведіть курсор на заповнювач, щоб побачити його призначення, і клацніть його, щоб додати.
6. Замініть приклади значень, наприклад ID мода для **Mod Version**.

Текстові поля, у редакторі яких немає кнопки **Placeholders**, не підтримують заповнювачі.

# Як працюють заповнювачі

Заповнювач має такий вигляд:

```
{"placeholder":"playername"}
```

Заповнювачі з параметрами містять їх у `values`:

```
{"placeholder":"modversion","values":{"modid":"fancymenu"}}
```

- Ідентифікатор, наприклад `playername`, чутливий до регістру. Нижче для кожного заповнювача наведено його ідентифікатор і значення.
- Порядок значень не має значення. Необов’язкові значення можна не вказувати.
- Якщо FancyMenu не може замінити заповнювач, наприклад через помилку в написанні, він залишиться в тексті без змін.
- Заповнювачі завжди повертають текст. Якщо показувати нічого, вони повертають значення за замовчуванням, наприклад `0`, `0.0`, `---` або порожній рядок.
- [Коди форматування](/text-formatting) працюють із заповнювачами: `&6{"placeholder":"playername"}` відображає ім’я золотим кольором.

> [!IMPORTANT]
> Заповнювачі схожі на JSON, але це не JSON. Не обробляйте їх форматувальником або валідатором JSON, адже заповнювачі всередині інших заповнювачів не є коректним JSON.

## Заповнювачі всередині заповнювачів

Значення можуть містити інші заповнювачі та [змінні](/variables#showing-variables-in-text). Спочатку FancyMenu замінює внутрішні заповнювачі. Екранувати лапки у значеннях не потрібно.

Цей приклад перетворює максимальний обсяг RAM із МБ у ГБ:

```
{"placeholder":"calc","values":{"decimal":"true","expression":"{"placeholder":"maxram"} / 1024"}}
```

Цей приклад показує змінну `rank` великими літерами:

```
{"placeholder":"uppercase_text","values":{"text":"$$rank"}}
```

Якщо заповнювач повертає текст із заповнювачами, наприклад прочитаний із файла за допомогою [**File Text**](#file-text), FancyMenu замінює і їх.

# Корисно знати

- Заповнювачі оновлюються автоматично. Після заміни FancyMenu зберігає текст протягом 30 мілісекунд, перш ніж знову замінити в ньому заповнювачі. Змініть це значення за допомогою **Placeholder Caching Duration [MS]** у **menu bar -> Customization -> Settings**. Значення `0` означає заміну щокадру, що потребує більше ресурсів.
- Заповнювачі, які читають дані із сайтів, файлів або серверів, як-от **Web Text** чи **Server Status**, завантажують їх у фоновому режимі. Поки завантаження не завершено, вони нічого не повертають або показують значення за замовчуванням.
- У [діях](/action-scripts) заповнювачі отримують актуальне значення саме під час виконання дії.
- Заповнювачі, пов’язані зі світом, екраном та елементами, працюють лише в основному потоці гри. У [Ticker](/elements#ticker), що працює у фоновому (асинхронному) режимі, FancyMenu натомість покаже помилку.
- **Random Number** генерує нове число щоразу, коли оновлюється текст. Щоб зберегти число, запишіть його у [змінну](/variables) за допомогою [**Set Variable Value (FM Variable)**](/action-scripts#set-variable-value-fm-variable).

> [!CAUTION]
> Заповнювачі, як-от **JSON Parser**, **File Text** і **Clipboard Content**, можуть читати файли з теки гри та вміст буфера обміну. У поєднанні з діями, що підключаються до вебсайтів, макет може передати ці дані назовні. Використовуйте лише макети, яким довіряєте.

# Приклади

## Панель привітання

<img width="800" alt="Текстовий елемент вітає гравця на ім’я та показує версію Minecraft, кількість модів і час" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/placeholders_welcome.png?raw=true">

```
### З поверненням, {"placeholder":"playername"}!
Minecraft {"placeholder":"mcversion"} із модами: {"placeholder":"loadedmods"}
Зараз {"placeholder":"realtimehour"}:{"placeholder":"realtimeminute"}
```

## Стан сервера та кількість гравців

```
Виживання: {"placeholder":"serverstatus","values":{"ip":"play.example.net"}}&r, гравців: {"placeholder":"serverplayercount","values":{"ip":"play.example.net"}}
```

## Дата й час

```
{"placeholder":"realtimeday"}.{"placeholder":"realtimemonth"}.{"placeholder":"realtimeyear"}, {"placeholder":"realtimehour"}:{"placeholder":"realtimeminute"}
```

## Використання RAM

```
RAM: {"placeholder":"usedram"} / {"placeholder":"maxram"} МБ ({"placeholder":"percentram"}%)
```

# Усі заповнювачі

Нижче наведено всі заповнювачі FancyMenu. Великі категорії **Advanced** і **World** у меню заповнювачів тут поділено на менші групи.

## Змінні та списки

Ці заповнювачі належать до категорії **Advanced**. Інформацію про створення змінних і списків див. у розділі [Змінні](/variables).

### Get Variable Value (FM Variable)

**Ідентифікатор:** `getvariable`

Значення однієї з ваших змінних. Якщо змінна порожня або не існує, повертається `0`, тож це зручно для чисел. Список повертає всі свої елементи у вигляді JSON-масиву, наприклад `["Steve","Alex"]`.

- `name`: назва змінної без `$$`

```
{"placeholder":"getvariable","values":{"name":"clicks"}}
```

### Get List Entry (FM Variable)

**Ідентифікатор:** `list_get`

Один елемент змінної-списку.

- `name`: назва списку
- `index`: позиція елемента. Перший елемент має індекс `0`, а від’ємні числа рахуються з кінця, тож `-1` — останній елемент.
- `fallback` (необов’язково): значення, яке повертається, якщо за таким індексом немає елемента або списку з такою назвою. Типово — порожній рядок.

```
{"placeholder":"list_get","values":{"name":"tips","index":"0","fallback":"No tips yet"}}
```

### List Size (FM Variable)

**Ідентифікатор:** `list_size`

Кількість елементів у списку. Якщо списку з такою назвою немає, повертається `0`.

- `name`: назва списку

```
{"placeholder":"list_size","values":{"name":"tips"}}
```

### Index of List Entry (FM Variable)

**Ідентифікатор:** `list_index_of`

Індекс першого елемента, що повністю збігається з `value`, або `-1`, якщо такого елемента немає у списку.

- `name`: назва списку
- `value`: елемент, який потрібно знайти
- `ignore_case` (необов’язково): значення `true` дає змогу вважати `Apple` і `apple` однаковими. Типово — `false`.

```
{"placeholder":"list_index_of","values":{"name":"read_news","value":"news_42","ignore_case":"false"}}
```

### Join List Entries (FM Variable)

**Ідентифікатор:** `list_join`

Усі елементи списку в одному текстовому рядку. Якщо списку з такою назвою немає, повертається порожній рядок.

- `name`: назва списку
- `separator` (необов’язково): текст між елементами. `\n` означає розрив рядка. Типово — `, `.

```
{"placeholder":"list_join","values":{"name":"tips","separator":"\n"}}
```

## Математика

Ці заповнювачі належать до категорії **Advanced**. Для десяткових дробів використовуйте крапку, наприклад `2.5`.

### Calculator

**Ідентифікатор:** `calc`

Обчислює математичний вираз, наприклад `2 + 3 * 4`.

- `expression`: вираз для обчислення
- `decimal` (необов’язково): `false` округлює результат до цілого числа. Типове значення — `true`, тому результат може виглядати як `14.0`.

```
{"placeholder":"calc","values":{"decimal":"false","expression":"{"placeholder":"usedram"} * 100 / {"placeholder":"maxram"}"}}
```

| У виразах | Дія |
|---|---|
| `+` `-` `*` `/` | Додавання, віднімання, множення, ділення |
| `^` | Піднесення до степеня, наприклад `2 ^ 3` дорівнює 8 |
| `%` | Остача від ділення, наприклад `7 % 3` дорівнює 1 |
| `( )` | Групування частин виразу, наприклад `(2 + 3) * 4` |
| `pi`, `e` | Числа π та e |
| `abs(x)` | Число без знака мінус |
| `sqrt(x)`, `cbrt(x)` | Квадратний і кубічний корені |
| `pow(x, y)` | x у степені y |
| `floor(x)`, `ceil(x)` | Округлення вниз і вгору |
| `sin(x)`, `cos(x)`, `tan(x)`, `cot(x)` | Тригонометричні функції; кути задаються в радіанах |
| `asin(x)`, `acos(x)`, `atan(x)` | Обернені тригонометричні функції |
| `sinh(x)`, `cosh(x)`, `tanh(x)` | Гіперболічні функції |
| `log(x)`, `log2(x)`, `log10(x)` | Логарифми за основами e, 2 і 10 |
| `exp(x)` | e у степені x |
| `signum(x)` | `1`, `-1` або `0`, як у [**Sign (Math)**](#sign-math) |

### Random Number

**Ідентифікатор:** `random_number`

Випадкове ціле число від `min` до `max`. Воно змінюється під час кожного оновлення тексту.

- `min`, `max`: найменше й найбільше числа

```
{"placeholder":"random_number","values":{"min":"1","max":"6"}}
```

### Max Number

**Ідентифікатор:** `maxnum`

Більше з двох чисел.

- `first`, `second`: числа

```
{"placeholder":"maxnum","values":{"first":"$$score","second":"$$best_score"}}
```

### Min Number

**Ідентифікатор:** `minnum`

Менше з двох чисел.

- `first`, `second`: числа

```
{"placeholder":"minnum","values":{"first":"10","second":"15"}}
```

### Absolute Number

**Ідентифікатор:** `absnum`

Число без знака мінус: наприклад, `-10.5` перетворюється на `10.5`.

- `num`: число

```
{"placeholder":"absnum","values":{"num":"-10.5"}}
```

### Negate Number

**Ідентифікатор:** `negnum`

Перетворює додатне число на від’ємне: наприклад, `10.5` перетворюється на `-10.5`. Нуль і від’ємні числа не змінюються.

- `num`: число

```
{"placeholder":"negnum","values":{"num":"10.5"}}
```

### Round (Math)

**Ідентифікатор:** `math_round`

Округлює число. `2.5` округлюється до `3`.

- `num`: число
- `decimals` (необов’язково): кількість десяткових знаків. Наприклад, `2` перетворює `3.14159` на `3.14`. Значення `0`, `-1` або відсутність параметра округлює до цілого числа.

```
{"placeholder":"math_round","values":{"num":"3.14159","decimals":"2"}}
```

### Floor (Math)

**Ідентифікатор:** `math_floor`

Округлює число вниз до цілого: `3.7` перетворюється на `3`, а `-3.2` — на `-4`.

- `num`: число

```
{"placeholder":"math_floor","values":{"num":"3.7"}}
```

### Ceiling (Math)

**Ідентифікатор:** `math_ceil`

Округлює число вгору до цілого: `3.2` перетворюється на `4`, а `-3.7` — на `-3`.

- `num`: число

```
{"placeholder":"math_ceil","values":{"num":"3.2"}}
```

### Sign (Math)

**Ідентифікатор:** `math_sign`

Повертає `1` для додатних чисел, `-1` для від’ємних і `0` для нуля.

- `num`: число

```
{"placeholder":"math_sign","values":{"num":"-3.14"}}
```

### *pi* (Math)

**Ідентифікатор:** `math_pi`

Число π: `3.141592653589793`.

```
{"placeholder":"math_pi"}
```

### Trigonometric Sine (Math)

**Ідентифікатор:** `math_sin`

Синус кута в радіанах. Щоб використати градуси, спочатку помножте їх на π / 180 за допомогою Calculator.

- `angle`: кут у радіанах

```
{"placeholder":"math_sin","values":{"angle":"1.5707963267948966"}}
```

### Trigonometric Cosine (Math)

**Ідентифікатор:** `math_cos`

Косинус кута в радіанах.

- `angle`: кут у радіанах

```
{"placeholder":"math_cos","values":{"angle":"0"}}
```

### Trigonometric Tangent (Math)

**Ідентифікатор:** `math_tan`

Тангенс кута в радіанах.

- `angle`: кут у радіанах

```
{"placeholder":"math_tan","values":{"angle":"0.7853981633974483"}}
```

### Hyperbolic Sine (Math)

**Ідентифікатор:** `math_sinh`

Гіперболічний синус числа.

- `num`: число

```
{"placeholder":"math_sinh","values":{"num":"1"}}
```

### Hyperbolic Cosine (Math)

**Ідентифікатор:** `math_cosh`

Гіперболічний косинус числа.

- `num`: число

```
{"placeholder":"math_cosh","values":{"num":"1"}}
```

### Hyperbolic Tangent (Math)

**Ідентифікатор:** `math_tanh`

Гіперболічний тангенс числа.

- `num`: число

```
{"placeholder":"math_tanh","values":{"num":"1"}}
```

### Number Base Converter

**Ідентифікатор:** `number_base_convert`

Перетворює число в іншу систему числення, наприклад із десяткової у двійкову або шістнадцяткову. Підтримуються й дробові числа — до 16 цифр після крапки. Літери у результаті будуть великими, наприклад `FF`.

- `input`: число
- `from_base` (необов’язково): система числення для `input`, від `2` до `36`. Типово — `10`.
- `to_base` (необов’язково): система числення результату, від `2` до `36`. Типово — `10`.

```
{"placeholder":"number_base_convert","values":{"input":"255","from_base":"10","to_base":"16"}}
```

## Текст

Ці заповнювачі належать до категорії **Advanced**.

### Uppercase Text

**Ідентифікатор:** `uppercase_text`

Перетворює текст на великі літери: `Hello World` стає `HELLO WORLD`. [Коди форматування](/text-formatting), як-от `&a`, не змінюються.

- `text`: текст

```
{"placeholder":"uppercase_text","values":{"text":"Hello World"}}
```

### Lowercase Text

**Ідентифікатор:** `lowercase_text`

Перетворює текст на малі літери: `HELLO WORLD` стає `hello world`. Коди форматування не змінюються.

- `text`: текст

```
{"placeholder":"lowercase_text","values":{"text":"HELLO WORLD"}}
```

### Title Case Text

**Ідентифікатор:** `title_case_text`

Кожне слово починається з великої літери: `hello world` стає `Hello World`. Коди форматування не змінюються.

- `text`: текст

```
{"placeholder":"title_case_text","values":{"text":"hello world"}}
```

### Sentence Case Text

**Ідентифікатор:** `sentence_case_text`

Кожне речення починається з великої літери: `hello world. this is fancymenu!` стає `Hello world. This is fancymenu!`. Коди форматування не змінюються.

- `text`: текст

```
{"placeholder":"sentence_case_text","values":{"text":"hello world. this is fancymenu!"}}
```

### Snake Case Text

**Ідентифікатор:** `snake_case_text`

Перетворює текст на малі літери й додає `_` між словами: `Hello World` стає `hello_world`. Коди форматування видаляються.

- `text`: текст

```
{"placeholder":"snake_case_text","values":{"text":"Hello World"}}
```

### Kebab Case Text

**Ідентифікатор:** `kebab_case_text`

Перетворює текст на малі літери й додає `-` між словами: `Hello World` стає `hello-world`. Коди форматування видаляються.

- `text`: текст

```
{"placeholder":"kebab_case_text","values":{"text":"Hello World"}}
```

### Alternating Case Text

**Ідентифікатор:** `alternating_case_text`

Чергування малих і великих літер: `alternating case` стає `aLtErNaTiNg CaSe`.

- `text`: текст

```
{"placeholder":"alternating_case_text","values":{"text":"alternating case"}}
```

### Toggle Case Text

**Ідентифікатор:** `toggle_case_text`

Замінює малі літери на великі, а великі — на малі: `Toggle Case` стає `tOGGLE cASE`.

- `text`: текст

```
{"placeholder":"toggle_case_text","values":{"text":"Toggle Case"}}
```

### Trim Text

**Ідентифікатор:** `trim_text`

Видаляє пробіли на початку й у кінці тексту. Пробіли всередині залишаються.

- `text`: текст

```
{"placeholder":"trim_text","values":{"text":"  Welcome!  "}}
```

### Crop Text

**Ідентифікатор:** `crop_text`

Видаляє вказану кількість символів на початку й у кінці тексту. Якщо прибрати по одному символу з кожного краю `hello world`, отримаємо `ello worl`.

- `text`: текст
- `remove_from_start`: кількість символів, які потрібно видалити на початку
- `remove_from_end`: кількість символів, які потрібно видалити в кінці

```
{"placeholder":"crop_text","values":{"text":"hello world","remove_from_start":"1","remove_from_end":"1"}}
```

### Split Text

**Ідентифікатор:** `split_text`

Розділяє текст і повертає одну з його частин. Якщо розділити `Steve,Alex,Notch` за `,`, частиною `1` буде `Alex`.

- `input`: текст
- `regex`: роздільник у вигляді регулярного виразу. Перед такими символами, як `.`, `|` і `?`, потрібно ставити `\`, наприклад `\.`.
- `max_parts` (необов’язково): максимальна кількість частин. Типове значення `-1` означає розділення за кожним збігом.
- `split_index`: номер частини, яку потрібно повернути. Перша частина має індекс `0`.

```
{"placeholder":"split_text","values":{"input":"Steve,Alex,Notch","regex":",","max_parts":"-1","split_index":"1"}}
```

### Replace Text

**Ідентифікатор:** `replace_text`

Замінює частини тексту: якщо у `Hello World!` замінити `World` на `FancyMenu`, отримаємо `Hello FancyMenu!`.

- `text`: текст
- `search`: що потрібно знайти
- `replacement` (необов’язково): текст для заміни. Типово — порожній рядок, тож знайдене буде видалено.
- `use_regex` (необов’язково): значення `true` трактує `search` як регулярний вираз. Тоді `$1`, `$2` тощо в `replacement` позначають знайдені групи. Типово — `false`.
- `replace_all` (необов’язково): `false` замінює лише перший збіг. Типово — `true`.

```
{"placeholder":"replace_text","values":{"text":"Hello World!","search":"World","replacement":"FancyMenu","use_regex":"false","replace_all":"true"}}
```

### Switch Case

**Ідентифікатор:** `switch_case`

Повертає результат для випадку, що відповідає значенню. Якщо змінна `difficulty_level` дорівнює `2`, приклад поверне `Hard Mode`.

- `value`: значення для перевірки
- `cases`: пари значень і результатів, наприклад `1:Easy Mode,2:Hard Mode`. Значення й результати не можуть містити `,` або `:`.
- `default` (необов’язково): результат, якщо відповідного випадку немає. Якщо значення не вказано, заповнювач залишиться без змін.

```
{"placeholder":"switch_case","values":{"value":"$$difficulty_level","cases":"1:Easy Mode,2:Hard Mode","default":"Normal Mode"}}
```

### Localize Text

**Ідентифікатор:** `local`

Текст для ключа локалізації мовою гри, наприклад `Singleplayer` для `menu.singleplayer`. Працює з ключами Minecraft, модів і вашими власними ключами (див. [Локалізація](/localization)).

- `key`: ключ локалізації

```
{"placeholder":"local","values":{"key":"menu.singleplayer"}}
```

### Stringify

**Ідентифікатор:** `stringify`

Спочатку замінює заповнювачі в тексті, а потім ставить `\` перед кожним символом `"`, `{` і `}`. Так текст із зовнішнього джерела, наприклад із вебсайту, не зможе перетворитися на заповнювачі.

- `text`: текст

```
{"placeholder":"stringify","values":{"text":"{"placeholder":"webtext","values":{"link":"https://example.com/motd.txt"}}"}}
```

## Дані та файли

Ці заповнювачі належать до категорії **Advanced**. Локальні шляхи починаються в теці гри, наприклад `/config/fancymenu/assets/news.txt`, і не можуть виходити за її межі (див. [Ресурси](/resources#local-resources)).

### JSON Parser

**Ідентифікатор:** `json`

Читає значення з JSON. Якщо результатів кілька, кожен показується в окремому рядку.

- `source`: текст JSON, JSON-файл у теці гри або URL JSON-файлу
- `json_path`: шлях до значення, наприклад `$.name` або `$.players[0].name`. Докладніше про шляхи JSON див. на [json.fancymenu.net](https://json.fancymenu.net).

```
{"placeholder":"json","values":{"source":"https://example.com/server_info.json","json_path":"$.news.title"}}
```

JSON із вебу завантажується один раз і повторно — після перезавантаження FancyMenu. Зміни у файлах відображаються відразу.

| Шлях | Результат |
|---|---|
| `$.name` | Значення `name` на верхньому рівні |
| `$.player.level` | Значення `level` усередині `player` |
| `$.items[0].id` | Значення `id` першого елемента `items` |
| `$.scores.*` | Усі значення всередині `scores` |

### File Text

**Ідентифікатор:** `file_text`

Текст файла або URL. Файли перечитуються щосекунди, URL — кожні 10 секунд. Поки текст завантажується або його не вдається прочитати, повертається порожній рядок.

- `path_or_url`: файл у теці гри або URL. Шляхи, що починаються з `.minecraft/`, вказують на стандартну теку Minecraft.
- `mode` (необов’язково): `all` для всього тексту або `last` для останніх рядків. Типово — `all`.
- `separator` (необов’язково): текст між рядками. Типово — `\n` (розрив рядка).
- `last_lines` (необов’язково): кількість рядків, яку повертає режим `last`. Типово — `1`.

```
{"placeholder":"file_text","values":{"path_or_url":"/config/fancymenu/assets/changelog.txt","mode":"all","separator":"\n","last_lines":"1"}}
```

### File Size

**Ідентифікатор:** `file_size`

Розмір файла в байтах. Якщо файла немає, повертається `0`. Шляхи, що починаються з `.minecraft/`, вказують на стандартну теку Minecraft.

- `path`: файл

```
{"placeholder":"file_size","values":{"path":"/config/fancymenu/assets/news.txt"}}
```

### File MD5

**Ідентифікатор:** `file_md5`

Хеш MD5 файла, наприклад `d41d8cd98f00b204e9800998ecf8427e`. Якщо файла немає, повертається порожній рядок. Шляхи, що починаються з `.minecraft/`, вказують на стандартну теку Minecraft.

- `path`: файл

```
{"placeholder":"file_md5","values":{"path":"/config/fancymenu/assets/menu_music.ogg"}}
```

### Encode To Base64

**Ідентифікатор:** `base64_encode`

Кодує текст у Base64: `Hello World` перетворюється на `SGVsbG8gV29ybGQ=`.

- `text`: текст

```
{"placeholder":"base64_encode","values":{"text":"Hello World"}}
```

### Decode From Base64

**Ідентифікатор:** `base64_decode`

Декодує Base64 у текст: `SGVsbG8gV29ybGQ=` перетворюється на `Hello World`.

- `text`: текст у Base64

```
{"placeholder":"base64_decode","values":{"text":"SGVsbG8gV29ybGQ="}}
```

### Get NBT Data (Client-Side)

**Ідентифікатор:** `nbt_data_get`

Читає дані NBT, як команда `/data get`, із того, що гра знає про світ. Це швидко, але сервери не надсилають гравцям усі дані.

- `source_type`: `entity` або `block`
- `entity_selector`: для `entity` — селектор, наприклад `@s` (ви), `@p`, `@e[type=minecraft:horse,limit=1,sort=nearest]`, або ім’я чи UUID сутності. Селектори можуть містити `type`, `name`, `tag`, `limit`, `sort`, `distance`, `x`, `y`, `z`, `dx`, `dy` і `dz`. Використовується перший збіг.
- `block_pos`: для `block` — позиція блочної сутності, наприклад скрині: `120 64 -35`
- `nbt_path`: шлях NBT, наприклад `foodLevel` або `Inventory[0].id`
- `scale` (необов’язково): множник для чисел. Типово — `1.0`.
- `return_type` (необов’язково): `value` (числа й текст без змін), `string`, `snbt` або `json`. Типово — `value`.

```
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"foodLevel","scale":"1.0","return_type":"value"}}
```

### Get NBT Data (Server-Side)

**Ідентифікатор:** `nbt_data_get_server`

Читає дані NBT із сервера, точно як команда `/data get`. Для цього FancyMenu має бути встановлено на сервері. В одиночній грі заповнювач працює завжди. Поки сервер не відповів, повертається порожній рядок; після відповіді дані оновлюються приблизно кожні 100 мілісекунд.

- `source_type`: `entity`, `block` або `storage`
- `entity_selector`: для `entity` — будь-який селектор команди `/data get`, що знаходить одну сутність, наприклад `@s` або `@e[type=minecraft:villager,limit=1,sort=nearest]`
- `block_pos`: для `block` — позиція, наприклад `120 64 -35`, `~ ~-1 ~` або `^ ^ ^1`
- `storage_id`: для `storage` — ID сховища команд, наприклад `mypack:quests`
- `nbt_path` (необов’язково): шлях NBT. Якщо його не вказати, повернуться всі дані.
- `scale` (необов’язково): множник для чисел. Типово — `1.0`.
- `return_type` (необов’язково): `value`, `string`, `snbt` або `json`. Типово — `value`.

```
{"placeholder":"nbt_data_get_server","values":{"source_type":"storage","storage_id":"mypack:quests","nbt_path":"completed","return_type":"value"}}
```

## Аудіо

Ці заповнювачі читають дані [аудіоелементів](/elements#audio) відкритого меню. Щоб скопіювати ID аудіоелемента, клацніть його правою кнопкою миші в редакторі макета й виберіть **Copy Element ID**.

### Audio Element Volume

**Ідентифікатор:** `audio_element_vol`

Гучність аудіоелемента: від `0.0` (0%) до `1.0` (100%).

- `element_identifier`: ID аудіоелемента

```
{"placeholder":"audio_element_vol","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Current Audio Track

**Ідентифікатор:** `audio_element_current_track`

Назва файла поточної доріжки, наприклад `menu_theme.ogg`. Якщо відтворення не триває, повертається `---`.

- `element_identifier`: ID аудіоелемента
- `display_name_mappings` (необов’язково): назви, які показуватимуться замість назв файлів. Між назвою файла й назвою для показу ставте `=>`, а між парами — `%:%`.

```
{"placeholder":"audio_element_current_track","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","display_name_mappings":"menu_theme.ogg=>Menu Theme%:%credits.ogg=>Credits Theme"}}
```

### Audio Duration

**Ідентифікатор:** `audio_duration`

Тривалість поточної доріжки, наприклад `03:45`. Поки вона завантажується, повертається `00:00`.

- `element_identifier`: ID аудіоелемента

```
{"placeholder":"audio_duration","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Audio Play Time

**Ідентифікатор:** `audio_playtime`

Час від початку відтворення поточної доріжки, наприклад `01:30`. Якщо відтворення зупинено, повертається `00:00` (або `0`).

- `element_identifier`: ID аудіоелемента
- `show_percentage` (необов’язково): значення `true` повертає натомість прогрес від `0` до `100`. Типово — `false`.

```
{"placeholder":"audio_playtime","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","show_percentage":"false"}}
```

### Audio Playing State

**Ідентифікатор:** `audio_playing_state`

Повертає `true`, коли аудіоелемент відтворюється, і `false`, коли його призупинено або зупинено.

- `element_identifier`: ID аудіоелемента

```
{"placeholder":"audio_playing_state","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

## Клієнт

Ці заповнювачі стосуються гри та її модів.

### Minecraft Version

**Ідентифікатор:** `mcversion`

Версія Minecraft, наприклад `1.21.1`.

```
{"placeholder":"mcversion"}
```

### Mod Loader Name

**Ідентифікатор:** `loadername`

Назва завантажувача модів, наприклад `Fabric` або `NeoForge`.

```
{"placeholder":"loadername"}
```

### Mod Loader Version

**Ідентифікатор:** `loaderver`

Версія завантажувача модів, наприклад `0.16.14`.

```
{"placeholder":"loaderver"}
```

### Mod Version

**Ідентифікатор:** `modversion`

Версія встановленого мода, наприклад `3.11.0`. Якщо мод не встановлено, повертається `0.0.0`.

- `modid`: ID мода, наприклад `fancymenu`

```
{"placeholder":"modversion","values":{"modid":"fancymenu"}}
```

### Active Mods Count

**Ідентифікатор:** `loadedmods`

Кількість завантажених модів. Бібліотеки та моди всередині інших модів теж враховуються, тому результат часто перевищує кількість файлів модів.

```
{"placeholder":"loadedmods"}
```

### Total Mods Count

**Ідентифікатор:** `totalmods`

Приблизна кількість встановлених модів, яку обчислено за файлами `.jar` у теці `mods` під час кожного запуску гри. Значення ніколи не менше за **Active Mods Count**.

```
{"placeholder":"totalmods"}
```

### World Loading Progress

**Ідентифікатор:** `world_load_progress`

Прогрес завантаження світу від `0` до `100`, який відображається на екрані завантаження. Зручно використовувати для індикаторів завантаження. На всіх інших екранах повертається `0`.

```
{"placeholder":"world_load_progress"}
```

### Minecraft Option Value

**Ідентифікатор:** `minecraft_option_value`

Значення параметра Minecraft, збережене у файлі `options.txt` у теці гри, наприклад `12` для `renderDistance`. Якщо параметра з такою назвою немає, повертається порожній рядок.

- `name`: назва параметра у `options.txt`

```
{"placeholder":"minecraft_option_value","values":{"name":"renderDistance"}}
```

### Keybind Key

**Ідентифікатор:** `keybind_key`

Клавіша, призначена для дії, як на екрані керування: наприклад, для стрибка — `Space`. Якщо дії з такою назвою немає, повертається порожній рядок.

- `keybind`: назва дії, наприклад `key.jump` або `key.inventory`. Назви зберігаються у `options.txt` без початкового `key_`: `key_key.jump` — це `key.jump`.

```
Натисніть {"placeholder":"keybind_key","values":{"keybind":"key.inventory"}}, щоб відкрити інвентар!
```

### Last World or Server

**Ідентифікатор:** `last_world_server`

Світ або сервер, до якого гравець востаннє приєднувався. Сервери показуються у форматі `play.example.net:25565`.

- `type`: `both` — світи й сервери, `world` — лише світи, `server` — лише сервери. Якщо вибрати `world` або `server`, а останній сеанс був іншого типу, повернеться порожній рядок.
- `full_world_path` (необов’язково): `false` повертає лише назву світу, наприклад `New World`. `true` повертає шлях до його теки. Типово — `true`.

```
{"placeholder":"last_world_server","values":{"type":"world","full_world_path":"false"}}
```

## Графічний інтерфейс

Ці заповнювачі стосуються відкритого екрана та його елементів. Для заповнювачів елементів потрібен їхній ID: клацніть елемент правою кнопкою миші в редакторі макета й виберіть **Copy Element ID**.

### Screen Width

**Ідентифікатор:** `guiwidth`

Ширина екрана в пікселях інтерфейсу. Це розмір, яким оперують елементи, а не кількість пікселів монітора.

```
{"placeholder":"guiwidth"}
```

### Screen Height

**Ідентифікатор:** `guiheight`

Висота екрана в пікселях інтерфейсу.

```
{"placeholder":"guiheight"}
```

### GUI Scale

**Ідентифікатор:** `guiscale`

Масштаб інтерфейсу гри, наприклад `2`.

```
{"placeholder":"guiscale"}
```

### Current Screen Identifier

**Ідентифікатор:** `screenid`

[Ідентифікатор](/screen-identifiers) відкритого екрана, наприклад `title_screen`. Якщо екран не відкрито, повертається порожній рядок.

```
{"placeholder":"screenid"}
```

### Element Width

**Ідентифікатор:** `elementwidth`

Ширина елемента в пікселях інтерфейсу. Якщо елемента з таким ID немає, повертається `1`.

- `id`: ID елемента

```
{"placeholder":"elementwidth","values":{"id":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Element Height

**Ідентифікатор:** `elementheight`

Висота елемента в пікселях інтерфейсу. Якщо елемента з таким ID немає, повертається `1`.

- `id`: ID елемента

```
{"placeholder":"elementheight","values":{"id":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Element X Position

**Ідентифікатор:** `elementposx`

Координата лівого краю елемента в пікселях інтерфейсу від лівого краю екрана. Якщо елемента з таким ID немає, повертається `1`.

- `id`: ID елемента

```
{"placeholder":"elementposx","values":{"id":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Element Y Position

**Ідентифікатор:** `elementposy`

Координата верхнього краю елемента в пікселях інтерфейсу від верхнього краю екрана. Якщо елемента з таким ID немає, повертається `1`.

- `id`: ID елемента

```
{"placeholder":"elementposy","values":{"id":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Text Element Content Height

**Ідентифікатор:** `text_element_content_height`

Висота, потрібна [текстовому елементу](/text-in-menus), щоб показати весь текст без прокручування, у пікселях інтерфейсу. Враховуються перенесені рядки, масштаб тексту та міжрядковий інтервал, тож цей заповнювач зручно використовувати для тла, що підлаштовується під текст. Якщо елемент не є текстовим, повертається `0`.

- `element_identifier`: ID текстового елемента

```
{"placeholder":"text_element_content_height","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Element Scroll Position

**Ідентифікатор:** `scroll_area_scroll_position`

Поточна позиція прокручування вмісту [прокручуваної області](/scrollable-areas) або текстового елемента, у пікселях інтерфейсу від початку вмісту. Для інших елементів повертається `0`.

- `element_identifier`: ID елемента
- `axis`: `vertical` або `horizontal`. Будь-яке інше значення використовує напрямок прокручування елемента.

```
{"placeholder":"scroll_area_scroll_position","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","axis":"vertical"}}
```

### Element Scroll Percent

**Ідентифікатор:** `scroll_area_scroll_percent`

Прогрес прокручування вмісту прокручуваної області або текстового елемента від `0` (початок) до `100` (кінець). Для інших елементів, а також якщо прокручувати нічого, повертається `0`.

- `element_identifier`: ID елемента
- `axis`: `vertical` або `horizontal`. Будь-яке інше значення використовує напрямок прокручування елемента.

```
{"placeholder":"scroll_area_scroll_percent","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","axis":"vertical"}}
```

### Element Scroll Content Size

**Ідентифікатор:** `scroll_area_content_size`

Розмір вмісту прокручуваної області або текстового елемента: висота для `vertical` і ширина для `horizontal`. Для інших елементів повертається `0`.

- `element_identifier`: ID елемента
- `axis`: `vertical` або `horizontal`. Будь-яке інше значення використовує напрямок прокручування елемента.

```
{"placeholder":"scroll_area_content_size","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","axis":"vertical"}}
```

### Text Input Field Value

**Ідентифікатор:** `text_input_field_value`

Текст, введений у [поле введення тексту](/elements#text-input-field) або текстове поле початкового екрана. Якщо елемент не є текстовим полем, повертається порожній рядок.

- `element_identifier`: ID елемента

```
{"placeholder":"text_input_field_value","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Vanilla Widget Label/Text

**Ідентифікатор:** `vanillabuttonlabel`

Напис кнопки або іншого віджета початкового екрана, наприклад `Options...`. Щоб скопіювати локатор віджета, клацніть його правою кнопкою миші в редакторі макета й виберіть **Copy Widget Locator**.

- `locator`: локатор віджета

```
{"placeholder":"vanillabuttonlabel","values":{"locator":"title_screen:mc_titlescreen_options_button"}}
```

### Mouse X Position

**Ідентифікатор:** `mouseposx`

Позиція курсора миші в пікселях інтерфейсу від лівого краю екрана. У редакторі макета завжди дорівнює `10`, щоб елементи, прив’язані до курсора, залишалися на місці й їх можна було редагувати.

```
{"placeholder":"mouseposx"}
```

### Mouse Y Position

**Ідентифікатор:** `mouseposy`

Позиція курсора миші в пікселях інтерфейсу від верхнього краю екрана. У редакторі макета завжди дорівнює `10`.

```
{"placeholder":"mouseposy"}
```

### Clicks Per Second

**Ідентифікатор:** `clicks_per_second`

Кількість натискань кнопки миші за останню секунду.

- `mouse_button` (необов’язково): `left` або `right`. Типово — `left`.

```
{"placeholder":"clicks_per_second","values":{"mouse_button":"left"}}
```

## Гравець

### Player Name

**Ідентифікатор:** `playername`

Ім’я гравця, наприклад `Steve`.

```
{"placeholder":"playername"}
```

### Player UUID

**Ідентифікатор:** `playeruuid`

UUID гравця, наприклад `c8cde7fe-7ced-11eb-9439-0242ac130002`.

```
{"placeholder":"playeruuid"}
```

### Last Death Message

**Ідентифікатор:** `lastdeathmessage`

Останнє повідомлення про смерть гравця від початку гри, наприклад `Steve was slain by Zombie`. До першої смерті повертається порожній рядок.

- `as_json_component` (необов’язково): `true` повертає повідомлення як текстовий JSON-компонент із кольорами. Типово — `false`.

```
{"placeholder":"lastdeathmessage","values":{"as_json_component":"false"}}
```

## Реальний час

Ці заповнювачі стосуються часу на вашому комп’ютері. Для дати й часу можна вказати необов’язковий параметр `timezone`: `system` — часовий пояс комп’ютера (типове значення) або ID, наприклад `UTC`, `Europe/Berlin` чи `America/New_York`. Повний список ID див. на [nodatime.org/TimeZones](https://nodatime.org/TimeZones).

### Realtime Year

**Ідентифікатор:** `realtimeyear`

Рік, наприклад `2026`.

```
{"placeholder":"realtimeyear","values":{"timezone":"system"}}
```

### Realtime Month

**Ідентифікатор:** `realtimemonth`

Місяць від `01` до `12`.

```
{"placeholder":"realtimemonth","values":{"timezone":"system"}}
```

### Realtime Day

**Ідентифікатор:** `realtimeday`

День місяця від `01` до `31`.

```
{"placeholder":"realtimeday","values":{"timezone":"system"}}
```

### Realtime Hour

**Ідентифікатор:** `realtimehour`

Година від `00` до `23`.

- `twelve_hour_format` (необов’язково): `true` повертає значення від `01` до `12`. Типово — `false`.

```
{"placeholder":"realtimehour","values":{"twelve_hour_format":"false","timezone":"Europe/Berlin"}}
```

### Realtime Minute

**Ідентифікатор:** `realtimeminute`

Хвилина від `00` до `59`.

```
{"placeholder":"realtimeminute","values":{"timezone":"system"}}
```

### Realtime Second

**Ідентифікатор:** `realtimesecond`

Секунда від `00` до `59`.

```
{"placeholder":"realtimesecond","values":{"timezone":"system"}}
```

### Current Time in Millis (Unix Timestamp)

**Ідентифікатор:** `unix_time`

Кількість мілісекунд від 1 січня 1970 року (UTC), наприклад `1732456789012`. Зручно для таймерів: збережіть значення у змінній, а потім відніміть його від пізнішого значення за допомогою Calculator.

```
{"placeholder":"unix_time"}
```

## Сервер

Ці заповнювачі запитують стан сервера, як і список серверів. Коли відкрито налаштований екран, FancyMenu надсилає запит кожні 30 секунд. До першої відповіді сервер вважається офлайн.

- `ip`: адреса сервера; порт указуйте, якщо він відрізняється від стандартного, наприклад `play.example.net` або `play.example.net:25566`

### Server Status

**Ідентифікатор:** `serverstatus`

Повертає `Online` зеленим кольором або `Offline` червоним.

```
{"placeholder":"serverstatus","values":{"ip":"play.example.net"}}
```

### Server Player Count

**Ідентифікатор:** `serverplayercount`

Кількість гравців онлайн і максимальна кількість гравців, наприклад `12/100`. До відповіді сервера повертається `0/0`.

```
{"placeholder":"serverplayercount","values":{"ip":"play.example.net"}}
```

### Server MOTD

**Ідентифікатор:** `servermotd`

Один рядок повідомлення дня сервера.

- `line`: `1` або `2`

```
{"placeholder":"servermotd","values":{"ip":"play.example.net","line":"1"}}
```

### Server PING

**Ідентифікатор:** `serverping`

Пінг до сервера в мілісекундах, наприклад `54`. Якщо сервер офлайн, повертається `-1`.

```
{"placeholder":"serverping","values":{"ip":"play.example.net"}}
```

### Server Version

**Ідентифікатор:** `serverversion`

Версія Minecraft на сервері, наприклад `1.21.1`. Деякі сервери показують тут власний текст. До відповіді сервера повертається `---`.

```
{"placeholder":"serverversion","values":{"ip":"play.example.net"}}
```

## Відео

Ці заповнювачі читають дані [відеоелементів і відеотла меню](/video) відкритого меню. Щоб скопіювати ID відеоелемента, клацніть його правою кнопкою миші в редакторі макета й виберіть **Copy Element ID**. Для тла клацніть правою кнопкою миші тло редактора й виберіть **Copy Background Identifier**.

### Video Element Volume

**Ідентифікатор:** `video_element_vol`

Гучність відеоелемента: від `0.0` (0%) до `1.0` (100%).

- `element_identifier`: ID відеоелемента

```
{"placeholder":"video_element_vol","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Video Element Duration

**Ідентифікатор:** `video_element_duration`

Тривалість відео у відеоелементі, наприклад `02:00`. Поки воно завантажується, повертається `00:00` (або `0`).

- `element_identifier`: ID відеоелемента
- `output_as_timestamp` (необов’язково): `true` повертає тривалість у мілісекундах, наприклад `120000`. Типово — `false`.

```
{"placeholder":"video_element_duration","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","output_as_timestamp":"false"}}
```

### Video Element Play Time

**Ідентифікатор:** `video_element_playtime`

Час від початку відео у відеоелементі, наприклад `00:45`. Поки воно завантажується, повертається `00:00` (або `0`).

- `element_identifier`: ID відеоелемента
- `show_percentage` (необов’язково): `true` повертає прогрес від `0` до `100`. Типово — `false`.
- `output_as_timestamp` (необов’язково): `true` повертає значення в мілісекундах. Якщо обидва параметри мають значення `true`, перевагу має `show_percentage`. Типово — `false`.

```
{"placeholder":"video_element_playtime","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","show_percentage":"false","output_as_timestamp":"false"}}
```

### Video Element Paused State

**Ідентифікатор:** `video_element_paused_state`

Повертає `true`, якщо відеоелемент призупинено, інакше — `false`.

- `element_identifier`: ID відеоелемента

```
{"placeholder":"video_element_paused_state","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Video Background Volume

**Ідентифікатор:** `video_background_vol`

Гучність відеотла меню: від `0.0` (0%) до `1.0` (100%).

- `background_identifier`: ідентифікатор тла меню

```
{"placeholder":"video_background_vol","values":{"background_identifier":"8c2e4f6a-1b3d-4e5f-8a7b-9c0d1e2f3a4b-1732456789012"}}
```

### Video Background Duration

**Ідентифікатор:** `video_background_duration`

Тривалість відео у тлі меню, наприклад `03:00`. Поки воно завантажується, повертається `00:00` (або `0`).

- `background_identifier`: ідентифікатор тла меню
- `output_as_timestamp` (необов’язково): `true` повертає значення в мілісекундах. Типово — `false`.

```
{"placeholder":"video_background_duration","values":{"background_identifier":"8c2e4f6a-1b3d-4e5f-8a7b-9c0d1e2f3a4b-1732456789012","output_as_timestamp":"false"}}
```

### Video Background Play Time

**Ідентифікатор:** `video_background_playtime`

Час від початку відео у тлі меню, наприклад `01:00`. Поки воно завантажується, повертається `00:00` (або `0`).

- `background_identifier`: ідентифікатор тла меню
- `show_percentage` (необов’язково): `true` повертає прогрес від `0` до `100`. Типово — `false`.
- `output_as_timestamp` (необов’язково): `true` повертає значення в мілісекундах. Якщо обидва параметри мають значення `true`, перевагу має `show_percentage`. Типово — `false`.

```
{"placeholder":"video_background_playtime","values":{"background_identifier":"8c2e4f6a-1b3d-4e5f-8a7b-9c0d1e2f3a4b-1732456789012","show_percentage":"true","output_as_timestamp":"false"}}
```

### Video Background Paused State

**Ідентифікатор:** `video_background_paused_state`

Повертає `true`, якщо відеотло меню призупинено, інакше — `false`.

- `background_identifier`: ідентифікатор тла меню

```
{"placeholder":"video_background_paused_state","values":{"background_identifier":"8c2e4f6a-1b3d-4e5f-8a7b-9c0d1e2f3a4b-1732456789012"}}
```

## Світ: характеристики гравця

Категорія **World** стосується світу, у якому ви граєте. Для більшості її заповнювачів потрібен завантажений світ. Поза світом вони повертають `0`, `0.0` або порожній рядок.

### Current Player Health

**Ідентифікатор:** `current_player_health`

Здоров’я гравця, наприклад `20.0`. Одне серце дорівнює `2.0`.

```
{"placeholder":"current_player_health"}
```

### Max Player Health

**Ідентифікатор:** `max_player_health`

Максимальне здоров’я гравця, наприклад `20.0`.

```
{"placeholder":"max_player_health"}
```

### Current Player Health (Percent)

**Ідентифікатор:** `current_player_health_percent`

Здоров’я гравця у відсотках, від `0` до `100`.

```
{"placeholder":"current_player_health_percent"}
```

### Current Player Absorption Health

**Ідентифікатор:** `current_player_absorption_health`

Поглинальне здоров’я гравця (золоті серця), наприклад `4.0`.

```
{"placeholder":"current_player_absorption_health"}
```

### Max Player Absorption Health

**Ідентифікатор:** `max_player_absorption_health`

Максимальне поглинальне здоров’я гравця, наприклад `4.0`.

```
{"placeholder":"max_player_absorption_health"}
```

### Current Player Absorption Health (Percent)

**Ідентифікатор:** `current_player_absorption_health_percent`

Поглинальне здоров’я гравця у відсотках, від `0` до `100`.

```
{"placeholder":"current_player_absorption_health_percent"}
```

### Current Player Food Level

**Ідентифікатор:** `current_player_hunger`

Рівень ситості гравця від `0.0` до `20.0`.

```
{"placeholder":"current_player_hunger"}
```

### Max Player Food Level

**Ідентифікатор:** `max_player_hunger`

Максимальний рівень ситості гравця — завжди `20.0`.

```
{"placeholder":"max_player_hunger"}
```

### Current Player Food Level (Percent)

**Ідентифікатор:** `current_player_hunger_percent`

Рівень ситості гравця у відсотках, від `0` до `100`.

```
{"placeholder":"current_player_hunger_percent"}
```

### Current Player Hunger Saturation

**Ідентифікатор:** `current_player_hunger_saturation`

Насичення гравця, наприклад `5.0`. Ситість починає зменшуватися лише після вичерпання насичення.

```
{"placeholder":"current_player_hunger_saturation"}
```

### Current Player Armor

**Ідентифікатор:** `current_player_armor`

Очки броні гравця від `0.0` до `20.0`.

```
{"placeholder":"current_player_armor"}
```

### Max Player Armor

**Ідентифікатор:** `max_player_armor`

Максимальна кількість очок броні на шкалі — завжди `20.0`.

```
{"placeholder":"max_player_armor"}
```

### Current Player Armor (Percent)

**Ідентифікатор:** `current_player_armor_percent`

Очки броні гравця у відсотках, від `0` до `100`.

```
{"placeholder":"current_player_armor_percent"}
```

### Player Armor Toughness

**Ідентифікатор:** `player_armor_toughness`

Міцність броні гравця, наприклад `8.0` у повному діамантовому обладунку.

```
{"placeholder":"player_armor_toughness"}
```

### Current Player Oxygen Level

**Ідентифікатор:** `current_player_oxygen`

Запас повітря гравця під водою від `0.0` до `300.0`.

```
{"placeholder":"current_player_oxygen"}
```

### Max Player Oxygen Level

**Ідентифікатор:** `max_player_oxygen`

Максимальний запас повітря гравця, наприклад `300.0`.

```
{"placeholder":"max_player_oxygen"}
```

### Current Player Oxygen Level (Percent)

**Ідентифікатор:** `current_player_oxygen_percent`

Запас повітря гравця у відсотках, від `0` до `100`.

```
{"placeholder":"current_player_oxygen_percent"}
```

### Current Player Level

**Ідентифікатор:** `current_player_level`

Рівень досвіду гравця, наприклад `30`.

```
{"placeholder":"current_player_level"}
```

### Current Player Experience

**Ідентифікатор:** `current_player_exp`

Загальна кількість очок досвіду гравця, наприклад `1395.0`. Це не рівень.

```
{"placeholder":"current_player_exp"}
```

### Player Experience Progress (Percent)

**Ідентифікатор:** `current_player_exp_progress`

Наскільки заповнена шкала досвіду, від `0` до `100`.

```
{"placeholder":"current_player_exp_progress"}
```

### Player Attack Strength (Percent)

**Ідентифікатор:** `player_attack_strength`

Наскільки заряджена наступна атака, від `0` до `100`, як на індикаторі атаки.

```
{"placeholder":"player_attack_strength"}
```

### Player Game Mode

**Ідентифікатор:** `player_gamemode`

`survival`, `creative`, `adventure` або `spectator`.

```
{"placeholder":"player_gamemode"}
```

### Player Item Use Progress (FM)

**Ідентифікатор:** `player_item_use_progress_fm`

Прогрес використання предмета гравцем — наприклад, їжі, зілля або натягування лука — від `0.0` до `1.0`.

```
{"placeholder":"player_item_use_progress_fm"}
```

### Current Mount Health

**Ідентифікатор:** `current_mount_health`

Здоров’я істоти, на якій їде гравець, наприклад коня: `30.0`.

```
{"placeholder":"current_mount_health"}
```

### Max Mount Health

**Ідентифікатор:** `max_mount_health`

Максимальне здоров’я істоти, на якій їде гравець.

```
{"placeholder":"max_mount_health"}
```

### Current Mount Health (Percent)

**Ідентифікатор:** `current_mount_health_percent`

Здоров’я істоти, на якій їде гравець, у відсотках від `0` до `100`.

```
{"placeholder":"current_mount_health_percent"}
```

### Current Mount Jump Meter (Percent)

**Ідентифікатор:** `current_mount_jump_meter`

Наскільки заряджений стрибок коня, від `0` до `100`.

```
{"placeholder":"current_mount_jump_meter"}
```

### Active Effects Count

**Ідентифікатор:** `effects_count`

Кількість ефектів, що діють на гравця зараз.

```
{"placeholder":"effects_count"}
```

### Active Effect

**Ідентифікатор:** `active_effect`

ID ефекту гравця, наприклад `minecraft:speed`, у порядку значків ефектів у верхньому правому куті. Якщо за таким індексом ефекту немає, повертається порожній рядок.

- `effect_index`: позиція ефекту. Перший має індекс `0`.

```
{"placeholder":"active_effect","values":{"effect_index":"0"}}
```

## Світ: інвентар і предмети

Ці заповнювачі належать до категорії **World**. Номери слотів: `0`–`8` — панель швидкого доступу, `9`–`35` — решта інвентарю, `36`–`39` — обладунок від чобіт до шолома, `40` — друга рука.

### Selected Hotbar Slot

**Ідентифікатор:** `active_hotbar_slot`

Вибраний слот панелі швидкого доступу від `0` до `8`.

```
{"placeholder":"active_hotbar_slot"}
```

### Slot Item

**Ідентифікатор:** `slot_item`

ID предмета у слоті, наприклад `minecraft:diamond_sword`. Для порожніх слотів повертається `minecraft:air`.

- `slot`: номер слота

```
{"placeholder":"slot_item","values":{"slot":"0"}}
```

### Slot Item Count

**Ідентифікатор:** `slot_item_count`

Кількість предметів у слоті, наприклад `64`.

- `slot`: номер слота

```
{"placeholder":"slot_item_count","values":{"slot":"0"}}
```

### Slot Item Durability

**Ідентифікатор:** `slot_item_durability`

Міцність предмета у слоті. Для предметів без міцності повертається `0`.

- `slot`: номер слота
- `format` (необов’язково): `current` (залишок міцності), `max`, `damage` (втрачена міцність) або `percentage` (залишок у відсотках від `0` до `100`). Типово — `current`.

```
{"placeholder":"slot_item_durability","values":{"slot":"39","format":"percentage"}}
```

### Slot Item Display Name (FM)

**Ідентифікатор:** `slot_item_display_name_fm`

Назва предмета у слоті як текстовий JSON-компонент із кольором рідкісності, наприклад `{"text":"Diamond Sword","color":"aqua"}`. У режимі спостерігача слоти панелі швидкого доступу повертають назви меню спостерігача.

- `slot`: номер слота
- `ignore_spectator` (необов’язково): `true` також повертає назви предметів у режимі спостерігача. Типово — `false`.

```
{"placeholder":"slot_item_display_name_fm","values":{"slot":"0","ignore_spectator":"false"}}
```

### Inventory Item Count

**Ідентифікатор:** `inventory_item_count`

Кількість предметів певного типу в усьому інвентарі гравця.

- `item`: ID предмета, наприклад `minecraft:diamond`. Якщо значення порожнє, підраховуються всі предмети.

```
{"placeholder":"inventory_item_count","values":{"item":"minecraft:diamond"}}
```

### Inventory Slot Food Point Restore Amount

**Ідентифікатор:** `inventory_slot_food_point_restore_amount`

Кількість очок ситості, яку відновить предмет у слоті, якщо його з’їсти, наприклад `4.0` для яблука. Для предметів, які не є їжею, повертається `0.0`.

- `slot`: номер слота

```
{"placeholder":"inventory_slot_food_point_restore_amount","values":{"slot":"0"}}
```

### Item Category

**Ідентифікатор:** `item_category`

Вкладка творчого інвентарю, у якій розташовано предмет, наприклад `Combat`. Для предметів без вкладки повертається `UNKNOWN`.

- `item`: ID предмета
- `as_key` (необов’язково): `true` повертає ID вкладки, наприклад `minecraft:combat`. Типово — `false`.

```
{"placeholder":"item_category","values":{"item":"minecraft:diamond_sword","as_key":"false"}}
```

### Hovered Inventory Item

**Ідентифікатор:** `hovered_inventory_item`

ID предмета в інвентарі, на який наведено курсор, наприклад `minecraft:apple`. Якщо такого предмета немає, повертається порожній рядок.

```
{"placeholder":"hovered_inventory_item"}
```

## Світ: HUD і боси

Ці заповнювачі належать до категорії **World**. Заповнювачі рейду зчитують дані рейду, смужка якого відображається вгорі екрана; для цього FancyMenu має бути встановлено на сервері. В одиночній грі вони працюють завжди. Якщо рейду немає, повертається `0` або порожній рядок.

### Action Bar Message (FM)

**Ідентифікатор:** `action_bar_message_fm`

Повідомлення над панеллю швидкого доступу як текстовий JSON-компонент, наприклад `{"text":"You may not rest now","color":"red"}`. Якщо повідомлення немає, повертається порожній рядок.

```
{"placeholder":"action_bar_message_fm"}
```

### Action Bar Message Time (FM)

**Ідентифікатор:** `action_bar_message_time_fm`

Кількість тіків, протягом яких повідомлення над панеллю швидкого доступу ще відображатиметься. 20 тіків дорівнюють одній секунді.

```
{"placeholder":"action_bar_message_time_fm"}
```

### Highlighted Item Time (FM)

**Ідентифікатор:** `highlighted_item_time_fm`

Кількість тіків, протягом яких назва вибраного предмета ще відображатиметься над панеллю швидкого доступу.

```
{"placeholder":"highlighted_item_time_fm"}
```

### Current HUD Title/Subtitle

**Ідентифікатор:** `current_title`

Заголовок або підзаголовок, який відображається зараз, наприклад після команди `/title`. Якщо його немає, повертається порожній рядок.

- `is_subtitle` (необов’язково): `true` повертає підзаголовок. Типово — `false`.
- `as_json` (необов’язково): `true` повертає значення як текстовий JSON-компонент. Типово — `false`.

```
{"placeholder":"current_title","values":{"is_subtitle":"false","as_json":"false"}}
```

### Bosses Count

**Ідентифікатор:** `boss_count`

Кількість смужок босів, що відображаються зараз.

```
{"placeholder":"boss_count"}
```

### Boss Name

**Ідентифікатор:** `boss_name`

Назва смужки боса, наприклад `Ender Dragon`. Якщо за вказаним індексом смужки боса немає, повертається порожній рядок.

- `boss_index`: позиція смужки боса. Верхня має індекс `0`.
- `as_json` (необов’язково): `true` повертає назву як текстовий JSON-компонент. Типово — `false`.

```
{"placeholder":"boss_name","values":{"boss_index":"0","as_json":"false"}}
```

### Current Boss Health (Percent)

**Ідентифікатор:** `current_boss_health`

Наскільки заповнена смужка боса, від `0` до `100`.

- `boss_index`: позиція смужки боса. Верхня має індекс `0`.

```
{"placeholder":"current_boss_health","values":{"boss_index":"0"}}
```

### Total Active Raid Waves

**Ідентифікатор:** `active_raid_total_waves`

Загальна кількість хвиль рейду разом із бонусною хвилею.

```
{"placeholder":"active_raid_total_waves"}
```

### Remaining Active Raid Waves

**Ідентифікатор:** `active_raid_remaining_waves`

Кількість хвиль рейду, які ще мають відбутися.

```
{"placeholder":"active_raid_remaining_waves"}
```

### Current Active Raid Wave

**Ідентифікатор:** `active_raid_current_wave`

Номер останньої хвилі: під час атаки першої хвилі повертається `1`, до її початку — `0`.

```
Хвиля {"placeholder":"active_raid_current_wave"} із {"placeholder":"active_raid_total_waves"}
```

### Active Raid Alive Raiders Count

**Ідентифікатор:** `active_raid_alive_raiders_count`

Кількість живих розбійників у рейді.

```
{"placeholder":"active_raid_alive_raiders_count"}
```

### Active Raid Alive Raiders List

**Ідентифікатор:** `active_raid_alive_raiders_list`

Список усіх живих розбійників через кому. Кожен елемент містить ID істоти та UUID розбійника, наприклад `minecraft:pillager#0d9a4b2e-5f1c-4a8e-9b3d-6c2f1e7a8b90`.

```
{"placeholder":"active_raid_alive_raiders_list"}
```

## Світ: позиція та камера

Ці заповнювачі належать до категорії **World**.

### Player X Coordinate

**Ідентифікатор:** `player_x_coordinate`

Координата X блока, у якому стоїть гравець, наприклад `125`.

```
{"placeholder":"player_x_coordinate"}
```

### Player Y Coordinate

**Ідентифікатор:** `player_y_coordinate`

Координата Y блока, у якому стоїть гравець, наприклад `64`.

```
{"placeholder":"player_y_coordinate"}
```

### Player Z Coordinate

**Ідентифікатор:** `player_z_coordinate`

Координата Z блока, у якому стоїть гравець, наприклад `-250`.

```
{"placeholder":"player_z_coordinate"}
```

### Player View Direction

**Ідентифікатор:** `player_view_direction`

Напрямок погляду гравця: `north`, `east`, `south` або `west`.

```
{"placeholder":"player_view_direction"}
```

### Player Position Delta X (FM)

**Ідентифікатор:** `player_position_delta_x_fm`

Відстань, на яку гравець перемістився вздовж осі X від попереднього тіку, у блоках, наприклад `0.12`. Від’ємне значення означає рух у протилежному напрямку.

```
{"placeholder":"player_position_delta_x_fm"}
```

### Player Position Delta Y (FM)

**Ідентифікатор:** `player_position_delta_y_fm`

Відстань, на яку гравець перемістився вздовж осі Y від попереднього тіку, наприклад `-0.08` під час падіння.

```
{"placeholder":"player_position_delta_y_fm"}
```

### Player Position Delta Z (FM)

**Ідентифікатор:** `player_position_delta_z_fm`

Відстань, на яку гравець перемістився вздовж осі Z від попереднього тіку.

```
{"placeholder":"player_position_delta_z_fm"}
```

### Camera Rotation X (FM)

**Ідентифікатор:** `camera_rotation_x_fm`

Нахил камери вгору або вниз у градусах: від `-90.0` (прямо вгору) до `90.0` (прямо вниз).

```
{"placeholder":"camera_rotation_x_fm"}
```

### Camera Rotation Y (FM)

**Ідентифікатор:** `camera_rotation_y_fm`

Напрямок камери у градусах від `-180.0` до `180.0`. Значення `0.0` відповідає півдню.

```
{"placeholder":"camera_rotation_y_fm"}
```

### Camera Rotation Delta X (FM)

**Ідентифікатор:** `camera_rotation_delta_x_fm`

На скільки градусів камера повернулася вгору або вниз від попереднього тіку.

```
{"placeholder":"camera_rotation_delta_x_fm"}
```

### Camera Rotation Delta Y (FM)

**Ідентифікатор:** `camera_rotation_delta_y_fm`

На скільки градусів камера повернулася ліворуч або праворуч від попереднього тіку.

```
{"placeholder":"camera_rotation_delta_y_fm"}
```

## Світ: інформація про світ

Ці заповнювачі належать до категорії **World**.

### World Day Time

**Ідентифікатор:** `world_daytime`

Час доби у світі в тіках. Доба триває 24000 тіків і починається о 6:00 ранку. Лічильник продовжує зростати з дня на день, тож вираз `{"placeholder":"world_daytime"} % 24000` у Calculator повертає час поточної доби.

```
{"placeholder":"world_daytime"}
```

### World Day Time Hour

**Ідентифікатор:** `world_daytime_hour`

Година доби у світі від `00` до `23`.

- `twelve_hour_format` (необов’язково): `true` повертає значення від `01` до `12`. Типово — `false`.

```
{"placeholder":"world_daytime_hour","values":{"twelve_hour_format":"false"}}
```

### World Day Time Minute

**Ідентифікатор:** `world_daytime_minute`

Хвилина часу доби у світі від `00` до `59`.

```
{"placeholder":"world_daytime_hour"}:{"placeholder":"world_daytime_minute"}
```

### World Game Time

**Ідентифікатор:** `game_time`

Загальна кількість тіків, що минули у світі. На відміну від часу доби, команди на кшталт `/time set` не змінюють це значення.

```
{"placeholder":"game_time"}
```

### World Difficulty

**Ідентифікатор:** `world_difficulty`

`peaceful`, `easy`, `normal` або `hard`.

```
{"placeholder":"world_difficulty"}
```

### Current Dimension

**Ідентифікатор:** `current_dimension`

Вимір, у якому перебуває гравець, наприклад `minecraft:overworld`.

- `as_key` (необов’язково): `false` повертає назву, наприклад `Overworld`. Для вимірів без назви повертається ID. Типово — `true`.

```
{"placeholder":"current_dimension","values":{"as_key":"false"}}
```

### Current Biome

**Ідентифікатор:** `current_biome`

Біом, у якому перебуває гравець, наприклад `minecraft:plains`.

- `as_key` (необов’язково): `false` повертає назву, наприклад `Plains`. Типово — `true`.

```
{"placeholder":"current_biome","values":{"as_key":"false"}}
```

### Current World Seed

**Ідентифікатор:** `current_world_seed`

Сід світу одиночної гри, наприклад `-4172144997902289642`. На серверах повертається порожній рядок.

```
{"placeholder":"current_world_seed"}
```

### Gamerule Value

**Ідентифікатор:** `gamerule_value`

Значення правила гри, наприклад `true` або `3`. В одиночній грі заповнювач працює завжди. На серверах для нього потрібен FancyMenu на сервері. Якщо правила з такою назвою немає, повертається порожній рядок.

- `name`: назва правила гри, наприклад `keep_inventory`. У Minecraft 1.21.10 і старіших версіях правила мають назви на кшталт `keepInventory`; ці старі назви також працюють у новіших версіях.

```
{"placeholder":"gamerule_value","values":{"name":"keep_inventory"}}
```

### Current Server IP

**Ідентифікатор:** `current_server_ip`

Адреса сервера, на якому перебуває гравець, наприклад `play.example.net`. В одиночній грі повертається порожній рядок.

```
{"placeholder":"current_server_ip"}
```

### World Players List

**Ідентифікатор:** `world_players_list`

Імена гравців у світі, про яких знає гра, у алфавітному порядку, наприклад `Alex, Notch, Steve`.

- `separator` (необов’язково): текст між іменами. Типово — `, `.

```
{"placeholder":"world_players_list","values":{"separator":", "}}
```

## Світ: збережені світи

Ці заповнювачі належать до категорії **World** і працюють у будь-якому меню, навіть якщо світ не завантажено.

### World Save Count

**Ідентифікатор:** `level_save_count`

Кількість світів одиночної гри.

```
{"placeholder":"level_save_count"}
```

### World Save Names

**Ідентифікатор:** `level_save_names`

Назви всіх світів одиночної гри в порядку зі списку світів, наприклад `Survival World, Creative Test`.

- `separator` (необов’язково): текст між назвами. Типово — `, `.

```
{"placeholder":"level_save_names","values":{"separator":", "}}
```

### World Save Data

**Ідентифікатор:** `level_save_data`

Усі дані світу одиночної гри у форматі JSON, наприклад `{"file_name":"Survival World","game_type":"survival","difficulty":"normal",...}`. Серед полів є `file_name`, `display_name`, `game_type`, `difficulty`, `allow_commands`, `last_played` (мітка часу Unix), `minecraft_version_name` та інші. Окремі значення можна прочитати за допомогою [**JSON Parser**](#json-parser).

- `level_name`: назва світу точно так, як у списку світів

```
{"placeholder":"json","values":{"source":"{"placeholder":"level_save_data","values":{"level_name":"Survival World"}}","json_path":"$.game_type"}}
```

## Інше

Ці заповнювачі не належать до категорій, тому меню заповнювачів показує їх під списком категорій.

### FPS (Frames Per Second)

**Ідентифікатор:** `fps`

Кількість кадрів за секунду, наприклад `120`.

```
{"placeholder":"fps"}
```

### Used RAM in MB

**Ідентифікатор:** `usedram`

Обсяг RAM, який гра використовує зараз, у МБ, наприклад `4096`.

```
{"placeholder":"usedram"}
```

### Max RAM in MB

**Ідентифікатор:** `maxram`

Максимальний обсяг RAM, який може використовувати гра, у МБ, наприклад `8192`.

```
{"placeholder":"maxram"}
```

### Used RAM in %

**Ідентифікатор:** `percentram`

Використаний грою обсяг RAM у відсотках від максимального, наприклад `50`.

```
{"placeholder":"percentram"}
```

### CPU Usage (JVM)

**Ідентифікатор:** `jvmcpu`

Завантаження процесора грою у відсотках, наприклад `25.5`.

```
{"placeholder":"jvmcpu"}
```

### CPU Usage (OS)

**Ідентифікатор:** `oscpu`

Загальне завантаження процесора комп’ютера у відсотках, наприклад `42.8`.

```
{"placeholder":"oscpu"}
```

### CPU Info

**Ідентифікатор:** `cpuinfo`

Назва процесора, наприклад `Intel(R) Core(TM) i7-10700K CPU @ 3.80GHz`.

```
{"placeholder":"cpuinfo"}
```

### GPU Info

**Ідентифікатор:** `gpuinfo`

Назва графічного пристрою, який використовує гра, наприклад `NVIDIA GeForce RTX 3080`.

```
{"placeholder":"gpuinfo"}
```

### OpenGL Version

**Ідентифікатор:** `glver`

Інформація про драйвер графічного пристрою, який використовує гра, наприклад `4.6.0 NVIDIA 566.36`.

```
{"placeholder":"glver"}
```

### Java Version

**Ідентифікатор:** `javaver`

Версія Java, на якій працює гра, наприклад `21.0.5`.

```
{"placeholder":"javaver"}
```

### Java Virtual Machine

**Ідентифікатор:** `jvmname`

Назва віртуальної машини Java, наприклад `OpenJDK 64-Bit Server VM`.

```
{"placeholder":"jvmname"}
```

### Operating System Name

**Ідентифікатор:** `osname`

Назва операційної системи, наприклад `Windows 11`.

```
{"placeholder":"osname"}
```

### Uptime Duration

**Ідентифікатор:** `uptime_duration`

Тривалість роботи гри в секундах, наприклад `742`.

- `output_as_millis` (необов’язково): `true` повертає значення в мілісекундах. Типово — `false`.

```
{"placeholder":"uptime_duration","values":{"output_as_millis":"false"}}
```

### Random Text

**Ідентифікатор:** `randomtext`

Випадковий рядок із текстового файла, URL або тексту, який ви ввели, наприклад випадкова порада. Файли й URL перечитуються кожні 30 секунд.

- `source`: файл `.txt` у теці гри, URL або рядки, розділені `\n`, наприклад `Tip 1\nTip 2\nTip 3`
- `interval` (необов’язково): інтервал у секундах між вибором нового рядка. `0` вибирає один рядок на сеанс гри. Типово — `10`.

```
{"placeholder":"randomtext","values":{"source":"/config/fancymenu/assets/tips.txt","interval":"10"}}
```

### Web Text

**Ідентифікатор:** `webtext`

Перший рядок тексту вебсторінки, наприклад текстового файла на вашому сайті. Він завантажується один раз, а потім повторно — після перезавантаження FancyMenu. Поки текст завантажується, повертається порожній рядок.

- `link`: URL сторінки

```
{"placeholder":"webtext","values":{"link":"https://example.com/motd.txt"}}
```

### Absolute File/Folder Path

**Ідентифікатор:** `absolute_path`

Повний шлях до файла або теки в теці гри, наприклад `C:/Users/Steve/AppData/Roaming/.minecraft/config/fancymenu`.

- `short_path`: шлях усередині теки гри

```
{"placeholder":"absolute_path","values":{"short_path":"config/fancymenu"}}
```

### Text Character Count

**Ідентифікатор:** `text_character_count`

Кількість символів у тексті: `Hello World!` містить `12` символів.

- `text`: текст

```
{"placeholder":"text_character_count","values":{"text":"$$player_nickname"}}
```

### Text Width

**Ідентифікатор:** `text_width`

Ширина тексту в пікселях інтерфейсу: `Hello World!` має ширину `57`. Коди форматування, як-от `&l`, враховуються так само, як у грі, тому жирний текст ширший.

- `text`: текст

```
{"placeholder":"text_width","values":{"text":"Hello World!"}}
```

### Text Height

**Ідентифікатор:** `text_height`

Висота тексту в пікселях інтерфейсу з урахуванням усіх рядків. Для розриву рядка використовуйте `\n`. Щоб підлаштувати розмір під текстовий елемент, використовуйте [**Text Element Content Height**](#text-element-content-height): цей заповнювач також враховує масштаб тексту, міжрядковий інтервал і перенесені рядки.

- `text`: текст

```
{"placeholder":"text_height","values":{"text":"First line\nSecond line"}}
```

### Clipboard Content

**Ідентифікатор:** `clipboard_content`

Текст у буфері обміну комп’ютера. Якщо буфер порожній, повертається порожній рядок.

```
{"placeholder":"clipboard_content"}
```
