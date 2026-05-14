---
title: API Shadera GLSL
description: >-
  Twórz efektowne shadery GLSL FancyMenu dla tła, elementów i nakładek
  dekoracyjnych.
---

# API Shadera GLSL FancyMenu

Ten dokument opisuje środowisko wykonawcze GLSL używane przez:

- `GLSL` tło menu
- `GLSL` element
- `GLSL` nakładkę dekoracyjną

Omawia tryby kompilacji, routing wieloprzebiegowy, obsługiwane uniformy oraz praktyczne wzorce tworzenia shaderów.

## 1. Przegląd środowiska wykonawczego

FancyMenu renderuje shadery za pomocą wewnętrznego potoku OpenGL (`#version 150`) i obsługuje:

- shadery jednoprzejściowe (`Image` only)
- shadery wieloprzebiegowe (`Buffer A` / `B` / `C` / `D` + `Image`)
- punkty wejścia w stylu Shadertoya (`mainImage`)
- bezpośrednie punkty wejścia fragmentów (`main`)

Źródła shaderów są wprowadzane jako pola tekstowe inline:

- `Shader Source` (przejście Image, wymagane do renderowania)
- `Buffer A Source` (opcjonalne)
- `Buffer B Source` (opcjonalne)
- `Buffer C Source` (opcjonalne)
- `Buffer D Source` (opcjonalne)

Jeśli źródło Image jest puste, renderowanie kończy się błędem „no source”.

## 2. Tryby kompilacji

FancyMenu obsługuje trzy tryby kompilacji:

- `Auto`
- `Direct Fragment`
- `Shadertoy`

### 2.1 Tryb Shadertoy

Oczekiwany punkt wejścia:

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord)
```

FancyMenu opakowuje go w `main()` i przekazuje współrzędne lokalnego obszaru:

```glsl
mainImage(fmColor_FancyMenu, gl_FragCoord.xy - fmAreaOffset);
```

Wrapper mnoży kanał alpha wyniku przez `fmOpacity`.

### 2.2 Tryb Direct

Oczekiwany punkt wejścia:

```glsl
void main()
```

Zachowanie zgodności:

- Próbowana jest kompatybilna wersja z `gl_FragColor`.
- Próbowana jest też wersja bez kompatybilności (dla nowoczesnych shaderów z jawnie zadeklarowanym `out vec4`).

W trybie direct `fmOpacity` nie jest automatycznie stosowane do wyniku. W razie potrzeby zastosuj je ręcznie.

### 2.3 Tryb Auto

Auto próbuje kolejno zgodne warianty (Shadertoy/direct) i używa pierwszego, który się skompiluje.

## 3. Preprocessing źródła i wbudowane makra

Przed kompilacją FancyMenu normalizuje źródło:

- usuwa BOM UTF-8
- konwertuje CRLF/CR do LF
- usuwa linie `#version ...`
- usuwa linie `precision ...;`

Wstrzykiwany na starcie kod środowiska zawiera:

- `#version 150`
- `in vec2 fmUv_FancyMenu` (pełnoekranowe UV w `[0,1]`, początek w lewym dolnym rogu)
- `#define iGlobalTime iTime`
- `#define texture2D texture`
- `#define textureCube texture`

Uwaga:

- Jeśli źródło już deklaruje znaną nazwę uniformu (np. `iTime`), FancyMenu nie wstrzykuje jej duplikatu.
- FancyMenu nadal próbuje przesyłać wartości do tej nazwy w czasie działania.
- `textureCube` jest tutaj tylko makrem aliasu; `iChannel0..3` są uniformami `sampler2D`.

## 4. System przejść (Image + Buffer A-D)

FancyMenu ma 5 slotów przejść:

- `Buffer A`
- `Buffer B`
- `Buffer C`
- `Buffer D`
- `Image` (końcowy przejściowy etap na ekran)

Zachowanie:

- Przejścia bufferów uruchamiają się tylko wtedy, gdy ich źródło nie jest puste.
- Przejście Image musi być obecne, aby renderować wynik.
- Bufory są renderowane do tekstur zmiennoprzecinkowych (`GL_RGBA16F`), a następnie ping-pongowane (zamiana odczyt/zapis co klatkę).

### 4.1 Routing kanałów dla każdego przejścia

Każde przejście udostępnia routing dla `iChannel0..3`. Dla każdego kanału możesz wybrać:

- `None`
- `Resource 0`
- `Resource 1`
- `Resource 2`
- `Resource 3`
- `Buffer A`
- `Buffer B`
- `Buffer C`
- `Buffer D`

Kanały zasobów pochodzą z ustawień `iChannel# Resource`.

Domyślne wartości:

- wszystkie routingi `iChannel` domyślnie mają wartość `None`
- żadne przejście bufora nie jest aktywne, dopóki źródło tego bufora nie będzie niepuste

Ważne:

- Routing do tego samego przejścia bufora (feedback) odczytuje dane z poprzedniej klatki (ping-pong read texture).
- Jeśli routowane źródło jest brakujące/nieaktywne, podłączana jest tekstura zapasowa, a `iChannelResolution[n].z` ma wartość `0.0`.

## 5. Współrzędne i semantyka obszaru

Shadery działają w prostokątnym obszarze:

- Tło menu: pełny ekran
- Element GLSL: prostokąt elementu

Konwencje współrzędnych:

- Uniformy pikselowe są w pikselach lokalnych obszaru.
- Początek osi Y jest w lewym dolnym rogu dla pikselowych współrzędnych widocznych po stronie shaderów.
- Współrzędne myszy nie są przycinane; wartości mogą być poza obszarem, jeśli kursor znajduje się poza nim.

Pola specjalne:

- `fmAreaOffset`: pozycja lewego dolnego rogu obszaru w przestrzeni pikselowej ekranu
- `fmAreaTopLeft`: pozycja lewego górnego rogu obszaru w przestrzeni pikselowej ekranu
- `fmAreaSize`: rozmiar obszaru w pikselach

## 6. Dokumentacja API uniformów

Wszystkie poniższe uniformy są dostępne zarówno dla shaderów tła, jak i shaderów elementów.

## 6.1 Uniformy zgodne z Shadertoy

| Uniform | Typ | Znaczenie |
|---|---|---|
| `iResolution` | `vec3` | `(areaWidthPx, areaHeightPx, 1.0)` |
| `iTime` | `float` | Skumulowany czas działania shaderu w sekundach |
| `iTimeDelta` | `float` | Delta czasu ostatniego renderu, zależna od freeze/skalowania czasu |
| `iFrameRate` | `float` | Awaryjna liczba FPS z Minecrafta lub runtime FPS |
| `iFrame` | `int` | Licznik klatek dla tego runtime'u |
| `iMouse` | `vec4` | Zobacz szczegóły poniżej |
| `iDate` | `vec4` | `(year, month, day, secondsOfDayWithFraction)` |
| `iSampleRate` | `float` | Stała `44100.0` |
| `iChannelTime[4]` | `float[4]` | Obecnie wszystkie ustawione na `iTime` |
| `iChannelResolution[4]` | `vec3[4]` | `(width, height, validFlag)` dla każdego kanału |
| `iChannel0..3` | `sampler2D` | Przekierowane wejścia teksturowe |

### Szczegóły `iMouse`

`iMouse = vec4(x, y, z, w)`

- `x`, `y`: bieżąca pozycja myszy w pikselach lokalnych obszaru albo zachowanie hold/frozen, jeśli włączono przełącznik
- `z`, `w`: początek lewego kliknięcia
  - dodatnie podczas trzymania lewego przycisku myszy
  - ujemne po zwolnieniu

Zachowanie sterowane przełącznikiem:

- `Update iMouse Position Only While Holding LMB = Off`:
  - `iMouse.xy` aktualizuje się ciągle
- `... = On`:
  - `iMouse.xy` aktualizuje się tylko podczas trzymania LMB, a potem pozostaje na ostatniej pozycji z momentu trzymania

Wartość domyślna:

- `Off` (ciągłe aktualizacje)

## 6.2 Uniformy specyficzne dla FancyMenu

| Uniform | Typ | Znaczenie |
|---|---|---|
| `fmAreaOffset` | `vec2` | Przesunięcie lewego dolnego rogu obszaru w pikselach w przestrzeni ekranu |
| `fmAreaSize` | `vec2` | Rozmiar obszaru w pikselach |
| `fmAreaPosition` | `vec2` | To samo co `fmAreaOffset` |
| `fmAreaTopLeft` | `vec2` | Przesunięcie lewego górnego rogu obszaru w pikselach w przestrzeni ekranu |
| `fmScreenSize` | `vec2` | Pełny rozmiar ekranu w pikselach |
| `fmGuiScale` | `float` | Aktualna skala GUI |
| `fmMouse` | `vec4` | `(localPxX, localPxYBottom, localNormX, localNormY)` |
| `fmMouseDelta` | `vec2` | Różnica ruchu myszy w pikselach obszaru (Y jest odwrócone do shaderowego up) |
| `fmMouseButtons` | `ivec4` | Stany wciśnięcia przycisków `0..3` |
| `fmMouseClickCount` | `ivec4` | Skumulowane liczby naciśnięć dla przycisków `0..3` |
| `fmMouseReleaseCount` | `ivec4` | Skumulowane liczby zwolnień dla przycisków `0..3` |
| `fmMouseScroll` | `vec2` | Zmiana scrolla od poprzedniego renderu tego runtime'u |
| `fmMouseScrollTotal` | `vec2` | Skumulowane sumy scrolla |
| `fmKeyEvent` | `ivec4` | `(lastKeyCode, lastScanCode, lastModifiers, lastAction)` |
| `fmKeyEventCount` | `int` | Skumulowany licznik zdarzeń klawiatury |
| `fmCharEvent` | `ivec4` | `(lastCodePoint, lastModifiers, 0, 0)` |
| `fmCharEventCount` | `int` | Skumulowany licznik zdarzeń wpisanych znaków |
| `fmDateParts` | `ivec4` | `(year, month, day, dayOfWeekIso1To7)` |
| `fmTimeParts` | `ivec4` | `(hour, minute, second, millisecondPart0To999)` |
| `fmDayOfYear` | `int` | Dzień roku |
| `fmWeekOfYear` | `int` | Tydzień roku ISO |
| `fmUnixTimeSeconds` | `int` | Sekundy epoki Unix |
| `fmUnixTimeMilliseconds` | `int` | Część milisekundowa bieżącego czasu (`0..999`) |
| `fmPartialTick` | `float` | Bieżący partial tick |
| `fmGameDeltaTicks` | `float` | Game delta ticks Minecrafta |
| `fmRealtimeDeltaTicks` | `float` | Realtime delta ticks Minecrafta |
| `fmInWorld` | `int` | `1`, gdy jesteś w świecie, w przeciwnym razie `0` |
| `fmIsPaused` | `int` | `1`, gdy gra jest wstrzymana, w przeciwnym razie `0` |
| `fmOpacity` | `float` | Efektywny mnożnik przezroczystości (`0..1`) |
| `fmVariableCount` | `int` | Aktualna liczba zmiennych FancyMenu |

Wartości akcji klawiszy (`fmKeyEvent.w`):

- `0` = zwolnienie
- `1` = naciśnięcie
- `2` = powtórzenie

## 6.3 API uniformów zmiennych FancyMenu

Zmienne FancyMenu są udostępniane bezpośrednio jako uniformy runtime'u (dla shaderów tła, elementów i nakładek dekoracyjnych) bez rekompilacji shaderów przy zmianie wartości.

### Nazewnictwo

Dla każdej zmiennej `<name>` FancyMenu udostępnia:

- `fmVarFloat_<name>`
- `fmVarInt_<name>`
- `fmVarBool_<name>`
- `fmVarVec2_<name>`
- `fmVarVec3_<name>`
- `fmVarVec4_<name>`
- `fmVarExists_<name>` (`1` = zmienna aktualnie istnieje, `0` = nie istnieje/usunięta)

Sanityzacja sufiksu uniformu dla `<name>`:

- dozwolone znaki to `[A-Za-z0-9_]`
- wszystkie pozostałe znaki są zamieniane na `_`
- jeśli pierwszy znak jest cyfrą, dodawany jest prefiks `_`

Przykłady:

- zmienna `player_hp` -> sufiks `player_hp`
- zmienna `player-hp` -> sufiks `player_hp`
- zmienna `2nd_phase` -> sufiks `_2nd_phase`

Ważne:

- te dynamiczne uniformy zmiennych **nie są automatycznie deklarowane** w źródle shaderów (zadeklaruj ręcznie te, których używasz)
- unikaj nazw zmiennych, które po sanityzacji dają ten sam sufiks, ponieważ mapują się na tę samą nazwę uniformu GLSL

### Konwersja wartości

Dla tekstowej wartości zmiennej `v`:

- `fmVarFloat_*`: sparsowany float (fallback `0.0`)
- `fmVarInt_*`: sparsowany int (fallback `0`)
- `fmVarBool_*`: interpretacja logiczna/liczbowa (`true/yes/on/enabled` => `1`, `false/no/off/disabled` => `0`, w przeciwnym razie liczba różna od zera => `1`)
- parsowanie wektorów akceptuje separatory: białe znaki, `,`, `;`, `|`
  - `fmVarVec2_*`: pierwsze 2 sparsowane składowe
  - `fmVarVec3_*`: pierwsze 3 sparsowane składowe
  - `fmVarVec4_*`: pierwsze 4 sparsowane składowe
  - jeśli jest mniej składowych, ostatnia sparsowana składowa jest powtarzana dla brakujących pozycji
  - jeśli nie ma żadnych numerycznych składowych, wszystkie składowe wektora korzystają z fallbacku skalarnego

Jeśli zmienna zostanie usunięta:

- `fmVarExists_*` przyjmuje wartość `0`
- wszystkie odpowiadające wartości `fmVar*_*` są resetowane do `0`

### Przykład deklaracji i użycia

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

## 7. Model śledzenia wejścia

FancyMenu śledzi wejście globalnie i zapisuje jego stan dla każdego renderu:

- ruch/przeciąganie myszy
- naciśnięcie/zwolnienie myszy
- scroll
- naciśnięcie/zwolnienie/powtórzenie klawisza
- wpisany znak

Odporność myszy:

- Runtime porównuje stany przycisków z pollingiem GLFW każdej klatki, aby zapobiec stanom zablokowanego przycisku.

Jeśli `Pass Input Events To Shader` jest wyłączone:

- uniformy wejścia są resetowane do wartości neutralnych w każdej klatce
- liczniki i zdarzenia są zerowane w danych widocznych dla shaderów

## 8. Szczegóły wejścia tekstur

Kanały zasobów (`iChannel# Resource`) oczekują tekstur 2D.

Stan tekstury dla każdego kanału:

- prawidłowy zasób: podłączona tekstura, rzeczywista szerokość/wysokość, `iChannelResolution[n].z = 1.0`
- brakujący/nieaktywny/None: tekstura zapasowa, `iChannelResolution[n].xyz = (0,0,0)`

Tekstury buforów:

- format wewnętrzny: `RGBA16F` (zmiennoprzecinkowy)
- filtrowanie: liniowe
- wrap: clamp-to-edge

Nadaje się to do danych wieloprzebiegowych (w tym wartości poza `[0,1]`).

## 9. Uwagi dotyczące renderowania i mieszania

- Przejścia buforów renderują poza ekranem bez mieszania.
- Końcowy przejściowy etap Image używa ustawienia `Enable Blending` do kompozycji.
- Wrapper Shadertoy automatycznie stosuje `fmOpacity` do alpha.
- Shadery direct powinny w razie potrzeby zastosować `fmOpacity` ręcznie.

## 10. Praktyczne szablony

## 10.1 Minimalny shader w stylu Shadertoy

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord) {
    vec2 uv = fragCoord / iResolution.xy;
    vec3 col = vec3(uv, 0.5 + 0.5 * sin(iTime));
    fragColor = vec4(col, 1.0);
}
```

## 10.2 Minimalny bezpośredni shader fragmentów

```glsl
out vec4 FragColor;

void main() {
    vec2 uv = gl_FragCoord.xy - fmAreaOffset;
    uv /= iResolution.xy;

    vec3 col = vec3(uv.x, uv.y, 0.5 + 0.5 * sin(iTime));
    FragColor = vec4(col, fmOpacity);
}
```

## 10.3 Minimalny multipass z feedbackiem

### Źródło Buffer A

Routing: `Buffer A iChannel0 Input -> Buffer A`

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord) {
    vec2 uv = fragCoord / iResolution.xy;
    vec4 prev = texture(iChannel0, uv);
    vec4 seed = vec4(uv, 0.0, 1.0);
    fragColor = mix(prev, seed, 0.02);
}
```

### Źródło Image

Routing: `Image iChannel0 Input -> Buffer A`

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord) {
    vec2 uv = fragCoord / iResolution.xy;
    fragColor = texture(iChannel0, uv);
}
```

## 11. Lista kontrolna rozwiązywania problemów

- Brak wyjścia:
  - sprawdź, czy źródło Image nie jest puste
  - sprawdź, czy tryb kompilacji odpowiada punktowi wejścia (`mainImage` vs `main`)
- Fioletowe/nieprawidłowe tekstury:
  - sprawdź powiązania zasobów i routing kanałów
  - sprawdź `iChannelResolution[n].z` (`0.0` oznacza nieprawidłowe/niedostępne)
- Nieprawidłowe współrzędne w shaderze direct:
  - użyj `gl_FragCoord.xy - fmAreaOffset` dla lokalnych współrzędnych obszaru
- Nieprawidłowe zachowanie przeciągania:
  - użyj przełącznika `Update iMouse Position Only While Holding LMB`
- Opacity nie jest stosowane w shaderze direct:
  - pomnóż alpha przez `fmOpacity` samodzielnie
