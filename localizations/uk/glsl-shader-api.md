---
title: API GLSL-шейдерів
description: 'Пишіть GLSL-шейдери FancyMenu для фонів, елементів і декоративних накладок.'
---

# FancyMenu GLSL Shader API

Цей документ описує GLSL runtime, який використовує FancyMenu для:

- `GLSL` фону меню
- `GLSL` елемента
- `GLSL` декоративної накладки

Тут розглядаються режими компіляції, багатопрохідне маршрутизування, підтримувані uniform-змінні та практичні підходи до написання шейдерів.

## 1. Огляд runtime

FancyMenu рендерить шейдери через внутрішній OpenGL-пайплайн (`#version 150`) і підтримує:

- однопрохідні шейдери (лише прохід `Image`)
- багатопрохідні шейдери (`Buffer A` / `B` / `C` / `D` + `Image`)
- точки входу в стилі Shadertoy (`mainImage`)
- прямі fragment-точки входу (`main`)

Джерела шейдерів — це вбудовані текстові поля:

- `Shader Source` (прохід `Image`, обов’язковий для рендерингу)
- `Buffer A Source` (необов’язково)
- `Buffer B Source` (необов’язково)
- `Buffer C Source` (необов’язково)
- `Buffer D Source` (необов’язково)

Якщо джерело `Image` порожнє, рендеринг завершується помилкою "no source".

## 2. Режими компіляції

FancyMenu підтримує три режими компіляції:

- `Auto`
- `Direct Fragment`
- `Shadertoy`

### 2.1 Режим Shadertoy

Очікувана точка входу:

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord)
```

FancyMenu обгортає її в `main()` і передає координати локальної області:

```glsl
mainImage(fmColor_FancyMenu, gl_FragCoord.xy - fmAreaOffset);
```

Обгортка множить альфа-канал виходу на `fmOpacity`.

### 2.2 Прямий режим

Очікувана точка входу:

```glsl
void main()
```

Поведінка сумісності:

- пробується сумісний варіант із `gl_FragColor`
- також пробується варіант без сумісності (для сучасних шейдерів із явним `out vec4`)

У прямому режимі `fmOpacity` не застосовується до вашого виходу автоматично. За потреби застосуйте його вручну.

### 2.3 Режим Auto

Auto послідовно пробує сумісні варіанти (Shadertoy/direct) і використовує перший, що успішно компілюється.

## 3. Попередня обробка джерела та вбудовані макроси

Перед компіляцією FancyMenu нормалізує джерело:

- видаляє UTF-8 BOM
- перетворює CRLF/CR на LF
- видаляє рядки `#version ...`
- видаляє рядки `precision ...;`

Преамбула, що додається runtime:

- `#version 150`
- `in vec2 fmUv_FancyMenu` (fullscreen UV у `[0,1]`, початок координат у нижньому лівому куті)
- `#define iGlobalTime iTime`
- `#define texture2D texture`
- `#define textureCube texture`

Примітка:

- Якщо ваш код уже оголошує відому uniform-змінну (наприклад, `iTime`), FancyMenu не вставляє повторне оголошення.
- При цьому FancyMenu все одно намагається передати значення до цієї змінної під час виконання.
- `textureCube` тут є лише макро-аліасом; `iChannel0..3` — це uniforms типу `sampler2D`.

## 4. Система проходів (Image + Buffer A-D)

У FancyMenu є 5 слотів проходів:

- `Buffer A`
- `Buffer B`
- `Buffer C`
- `Buffer D`
- `Image` (кінцевий екранний прохід)

Поведінка:

- buffer-проходи виконуються лише якщо їх джерело не порожнє.
- `Image`-прохід має бути присутнім для виводу результату.
- Buffers рендеряться у floating-point текстури (`GL_RGBA16F`), після чого відбувається ping-pong (обмін читання/запису кожен кадр).

### 4.1 Маршрутизація каналів у кожному проході

Кожен прохід має маршрутизацію для `iChannel0..3`. Для кожного каналу можна обрати:

- `None`
- `Resource 0`
- `Resource 1`
- `Resource 2`
- `Resource 3`
- `Buffer A`
- `Buffer B`
- `Buffer C`
- `Buffer D`

Канали ресурсів беруться з налаштувань `iChannel# Resource`.

За замовчуванням:

- усі маршрутизації `iChannel` мають значення `None`
- жоден buffer-прохід не активний, доки його джерело не стане непорожнім

Важливо:

- Маршрутизація на той самий buffer-прохід (feedback) читає дані з попереднього кадру (ping-pong texture для читання).
- Якщо підключене джерело відсутнє/неактивне, прив’язується fallback-текстура, а `iChannelResolution[n].z` стає `0.0`.

## 5. Семантика координат та області

Шейдери працюють у прямокутній області:

- фон меню: повноекранна область
- GLSL елемент: прямокутник елемента

Конвенції координат:

- Pixel uniforms подаються в локальних пікселях області.
- Початок осі Y для піксельних координат, видимих шейдеру, у нижньому лівому куті.
- Координати миші не обрізаються; значення можуть бути поза областю, якщо курсор знаходиться за її межами.

Спеціальні поля:

- `fmAreaOffset`: позиція нижнього лівого кута області в піксельному просторі екрана
- `fmAreaTopLeft`: позиція верхнього лівого кута області в піксельному просторі екрана
- `fmAreaSize`: розмір області в пікселях

## 6. Довідка по Uniform API

Усі uniform-змінні нижче доступні і для шейдерів фону, і для шейдерів елементів.

## 6.1 Uniform-змінні, сумісні з Shadertoy

| Uniform | Type | Значення |
|---|---|---|
| `iResolution` | `vec3` | `(areaWidthPx, areaHeightPx, 1.0)` |
| `iTime` | `float` | Накопичений час шейдера в секундах |
| `iTimeDelta` | `float` | Дельта часу останнього рендеру, залежить від freeze/time scale |
| `iFrameRate` | `float` | FPS Minecraft або fallback FPS runtime |
| `iFrame` | `int` | Лічильник кадрів для цього runtime |
| `iMouse` | `vec4` | Див. деталі нижче |
| `iDate` | `vec4` | `(year, month, day, secondsOfDayWithFraction)` |
| `iSampleRate` | `float` | Константа `44100.0` |
| `iChannelTime[4]` | `float[4]` | Наразі всі значення встановлені в `iTime` |
| `iChannelResolution[4]` | `vec3[4]` | `(width, height, validFlag)` для кожного каналу |
| `iChannel0..3` | `sampler2D` | Текстурні входи за маршрутизацією |

### Деталі `iMouse`

`iMouse = vec4(x, y, z, w)`

- `x`, `y`: поточна позиція миші в локальних пікселях області, або поведінка утримання/замороження, якщо ввімкнено перемикач
- `z`, `w`: точка початку лівого кліку
  - позитивні, поки ліва кнопка миші утримується
  - негативні після відпускання

Поведінка, керована перемикачем:

- `Update iMouse Position Only While Holding LMB = Off`:
  - `iMouse.xy` оновлюється безперервно
- `... = On`:
  - `iMouse.xy` оновлюється лише поки натиснута ЛКМ, а потім лишається в останній позиції утримання

Значення за замовчуванням:

- `Off` (безперервне оновлення)

## 6.2 Uniform-змінні, специфічні для FancyMenu

| Uniform | Type | Значення |
|---|---|---|
| `fmAreaOffset` | `vec2` | Зсув нижнього лівого кута області в пікселях екрана |
| `fmAreaSize` | `vec2` | Розмір області в пікселях |
| `fmAreaPosition` | `vec2` | Те саме, що `fmAreaOffset` |
| `fmAreaTopLeft` | `vec2` | Зсув верхнього лівого кута області в пікселях екрана |
| `fmScreenSize` | `vec2` | Повний розмір екрана в пікселях |
| `fmGuiScale` | `float` | Поточний масштаб GUI |
| `fmMouse` | `vec4` | `(localPxX, localPxYBottom, localNormX, localNormY)` |
| `fmMouseDelta` | `vec2` | Дельта миші в пікселях області (Y інвертовано до напрямку shader-up) |
| `fmMouseButtons` | `ivec4` | Стан натискання кнопок `0..3` |
| `fmMouseClickCount` | `ivec4` | Накопичена кількість натискань для кнопок `0..3` |
| `fmMouseReleaseCount` | `ivec4` | Накопичена кількість відпускань для кнопок `0..3` |
| `fmMouseScroll` | `vec2` | Дельта скролу відносно попереднього рендеру цього runtime |
| `fmMouseScrollTotal` | `vec2` | Накопичений загальний скрол |
| `fmKeyEvent` | `ivec4` | `(lastKeyCode, lastScanCode, lastModifiers, lastAction)` |
| `fmKeyEventCount` | `int` | Накопичений лічильник подій клавіш |
| `fmCharEvent` | `ivec4` | `(lastCodePoint, lastModifiers, 0, 0)` |
| `fmCharEventCount` | `int` | Накопичений лічильник подій введених символів |
| `fmDateParts` | `ivec4` | `(year, month, day, dayOfWeekIso1To7)` |
| `fmTimeParts` | `ivec4` | `(hour, minute, second, millisecondPart0To999)` |
| `fmDayOfYear` | `int` | День року |
| `fmWeekOfYear` | `int` | ISO-тиждень року |
| `fmUnixTimeSeconds` | `int` | Unix epoch у секундах |
| `fmUnixTimeMilliseconds` | `int` | Мілісекундна частина поточного часу (`0..999`) |
| `fmPartialTick` | `float` | Поточний partial tick |
| `fmGameDeltaTicks` | `float` | Minecraft game delta ticks |
| `fmRealtimeDeltaTicks` | `float` | Minecraft realtime delta ticks |
| `fmInWorld` | `int` | `1`, коли ви у світі, інакше `0` |
| `fmIsPaused` | `int` | `1`, коли гра на паузі, інакше `0` |
| `fmOpacity` | `float` | Ефективний множник прозорості (`0..1`) |
| `fmVariableCount` | `int` | Поточна кількість змінних FancyMenu |

Значення дій клавіші (`fmKeyEvent.w`):

- `0` = відпускання
- `1` = натискання
- `2` = повтор

## 6.3 API uniform-змінних FancyMenu Variables

Змінні FancyMenu доступні напряму як runtime uniforms (для шейдерів фону, елементів і декоративної накладки) без перекомпіляції шейдера, коли значення змінюються.

### Іменування

Для кожної змінної `<name>` FancyMenu надає:

- `fmVarFloat_<name>`
- `fmVarInt_<name>`
- `fmVarBool_<name>`
- `fmVarVec2_<name>`
- `fmVarVec3_<name>`
- `fmVarVec4_<name>`
- `fmVarExists_<name>` (`1` = змінна зараз існує, `0` = відсутня/видалена)

Санітайзинг суфікса uniform-змінної для `<name>`:

- допустимі символи: `[A-Za-z0-9_]`
- усі інші символи замінюються на `_`
- якщо перший символ є цифрою, на початок додається `_`

Приклади:

- змінна `player_hp` -> суфікс `player_hp`
- змінна `player-hp` -> суфікс `player_hp`
- змінна `2nd_phase` -> суфікс `_2nd_phase`

Важливо:

- ці динамічні uniforms змінних **не оголошуються автоматично** у вихідному коді шейдера (оголошуйте потрібні вручну)
- уникайте назв змінних, які після санітайзингу дають однаковий суфікс, бо тоді вони мапляться на одну й ту саму GLSL uniform-змінну

### Перетворення значень

Для текстового значення змінної `v`:

- `fmVarFloat_*`: float після парсингу (`0.0` як fallback)
- `fmVarInt_*`: int після парсингу (`0` як fallback)
- `fmVarBool_*`: логічне/int-тлумачення (`true/yes/on/enabled` => `1`, `false/no/off/disabled` => `0`, інакше числове ненульове => `1`)
- парсинг векторів підтримує роздільники: пробіли, `,`, `;`, `|`
  - `fmVarVec2_*`: перші 2 розібрані компоненти
  - `fmVarVec3_*`: перші 3 розібрані компоненти
  - `fmVarVec4_*`: перші 4 розібрані компоненти
  - якщо компонентів менше, останній розібраний компонент повторюється для відсутніх слотів
  - якщо числових компонентів немає, усі компоненти вектора беруть scalar fallback

Якщо змінну було видалено:

- `fmVarExists_*` стає `0`
- усі відповідні значення `fmVar*_*` скидаються до `0`

### Приклад оголошення та використання

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

## 7. Модель відстеження вводу

FancyMenu глобально відстежує ввід і зберігає знімок стану для кожного рендеру:

- рух/перетягування миші
- натискання/відпускання миші
- скрол
- натискання/відпускання/повтор клавіш
- введені символи

Надійність миші:

- Runtime узгоджує стани кнопок із GLFW polling кожного кадру, щоб запобігти "залипанню" кнопок.

Якщо `Pass Input Events To Shader` вимкнено:

- uniform-змінні вводу скидаються до нейтральних значень кожного кадру
- лічильники та події зануляються в даних, видимих шейдеру

## 8. Деталі текстурного вводу

Канали ресурсів (`iChannel# Resource`) очікують 2D-текстури.

Стан текстури для кожного каналу:

- дійсний ресурс: прив’язана текстура, реальна ширина/висота, `iChannelResolution[n].z = 1.0`
- відсутній/неактивний/None: fallback-текстура, `iChannelResolution[n].xyz = (0,0,0)`

Buffer-текстури:

- внутрішній формат: `RGBA16F` (floating point)
- фільтрація: linear
- wrap: clamp-to-edge

Це підходить для багатопрохідних даних (у тому числі значень поза `[0,1]`).

## 9. Примітки щодо рендерингу та змішування

- Buffer-проходи рендеряться offscreen без blending.
- Кінцевий `Image`-прохід використовує налаштування `Enable Blending` для композитингу.
- Обгортка Shadertoy автоматично застосовує `fmOpacity` до альфи.
- Direct-шейдери мають застосовувати `fmOpacity` вручну, якщо це потрібно.

## 10. Практичні шаблони

## 10.1 Мінімальний шейдер у стилі Shadertoy

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord) {
    vec2 uv = fragCoord / iResolution.xy;
    vec3 col = vec3(uv, 0.5 + 0.5 * sin(iTime));
    fragColor = vec4(col, 1.0);
}
```

## 10.2 Мінімальний direct fragment shader

```glsl
out vec4 FragColor;

void main() {
    vec2 uv = gl_FragCoord.xy - fmAreaOffset;
    uv /= iResolution.xy;

    vec3 col = vec3(uv.x, uv.y, 0.5 + 0.5 * sin(iTime));
    FragColor = vec4(col, fmOpacity);
}
```

## 10.3 Мінімальний feedback multipass

### Джерело Buffer A

Маршрут: `Buffer A iChannel0 Input -> Buffer A`

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord) {
    vec2 uv = fragCoord / iResolution.xy;
    vec4 prev = texture(iChannel0, uv);
    vec4 seed = vec4(uv, 0.0, 1.0);
    fragColor = mix(prev, seed, 0.02);
}
```

### Джерело Image

Маршрут: `Image iChannel0 Input -> Buffer A`

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord) {
    vec2 uv = fragCoord / iResolution.xy;
    fragColor = texture(iChannel0, uv);
}
```

## 11. Чекліст усунення несправностей

- Немає виводу:
  - перевірте, що `Image` source не порожній
  - перевірте, що режим компіляції відповідає вашій точці входу (`mainImage` vs `main`)
- Фіолетові/невалідні текстури:
  - перевірте прив’язки ресурсів і маршрутизацію каналів
  - перевірте `iChannelResolution[n].z` (`0.0` означає недійсний/недоступний ресурс)
- Неправильні координати в direct-шейдері:
  - використовуйте `gl_FragCoord.xy - fmAreaOffset` для локальних координат області
- Неправильна поведінка drag:
  - використовуйте перемикач `Update iMouse Position Only While Holding LMB`
- У direct-шейдері не застосовується прозорість:
  - множте альфа-канал на `fmOpacity` самостійно
