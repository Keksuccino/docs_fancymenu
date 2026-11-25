---
title: API shaderów GLSL
description: 'Twórz shadery GLSL FancyMenu do tła, elementów i nakładek dekoracyjnych.'
sourceBlobSha: f3da9c3fe83444dab5c59f74f5011e2d6e8cf9e6
---

# API shaderów GLSL FancyMenu

Ten dokument opisuje środowisko uruchomieniowe GLSL używane przez FancyMenu w:

- tle menu `GLSL`
- elemencie `GLSL`
- nakładce dekoracyjnej `GLSL`

Obejmuje tryby kompilacji, obsługę wielu przebiegów, obsługiwane uniformy oraz praktyczne wskazówki dotyczące tworzenia shaderów.

## 1. Omówienie środowiska uruchomieniowego

FancyMenu renderuje shadery za pomocą wewnętrznego potoku OpenGL (`#version 150`) i obsługuje:

- shadery jednoprzebiegowe (tylko przebieg `Image`)
- shadery wieloprzebiegowe (`Buffer A` / `B` / `C` / `D` + `Image`)
- punkty wejścia w stylu Shadertoy (`mainImage`)
- bezpośrednie punkty wejścia fragmentów (`main`)

Źródła shaderów są wprowadzane jako tekst:

- `Shader Source` (przebieg Image; wymagany do renderowania)
- `Buffer A Source` (opcjonalny)
- `Buffer B Source` (opcjonalny)
- `Buffer C Source` (opcjonalny)
- `Buffer D Source` (opcjonalny)

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

FancyMenu opakowuje go w `main()` i przekazuje współrzędne lokalne względem obszaru:

```glsl
mainImage(fmColor_FancyMenu, gl_FragCoord.xy - fmAreaOffset);
```

Wrapper mnoży alfę wyjściową przez `fmOpacity`.

### 2.2 Tryb Direct

Oczekiwany punkt wejścia:

```glsl
void main()
```

Zgodność wsteczna:

- Podejmowana jest próba użycia wariantu zgodnego z `gl_FragColor`.
- Podejmowana jest również próba użycia wariantu bez tej zgodności (dla nowoczesnych shaderów z jawnym `out vec4`).

W trybie Direct `fmOpacity` nie jest automatycznie stosowane do wyniku. W razie potrzeby zastosuj je ręcznie.

### 2.3 Tryb Auto

Tryb Auto kolejno wypróbowuje zgodne warianty (Shadertoy/Direct) i używa pierwszego, który się skompiluje.

## 3. Przetwarzanie źródła i wbudowane makra

Przed kompilacją FancyMenu normalizuje źródło:

- usuwa BOM UTF-8
- zamienia CRLF/CR na LF
- usuwa wiersze `#version ...`
- usuwa wiersze `precision ...;`

Preambuła wstrzykiwana przez środowisko uruchomieniowe zawiera:

- `#version 150`
- `in vec2 fmUv_FancyMenu` (UV dla pełnego ekranu w zakresie `[0,1]`, początek układu współrzędnych w lewym dolnym rogu)
- `#define iGlobalTime iTime`
- `#define texture2D texture`
- `#define textureCube texture`

Uwaga:

- Jeśli źródło zawiera już deklarację znanej nazwy uniformu (np. `iTime`), FancyMenu nie wstrzykuje jej ponownie.
- FancyMenu nadal próbuje przesyłać wartości do tej nazwy w czasie działania.
- `textureCube` jest tu tylko makrem aliasującym; `iChannel0..3` to uniformy typu `sampler2D`.

## 4. System przebiegów (Image + Buffer A-D)

FancyMenu ma 5 slotów przebiegów:

- `Buffer A`
- `Buffer B`
- `Buffer C`
- `Buffer D`
- `Image` (końcowy przebieg wyświetlany na ekranie)

Zasady działania:

- Przebiegi Buffer uruchamiają się tylko wtedy, gdy ich źródło nie jest puste.
- Aby wyrenderować wynik, przebieg Image musi być obecny.
- Buffery są renderowane do tekstur zmiennoprzecinkowych (`GL_RGBA16F`), a następnie używane w trybie ping-pong (zamiana tekstur odczytu i zapisu przy każdej klatce).

### 4.1 Przypisywanie kanałów w poszczególnych przebiegach

Każdy przebieg udostępnia przypisywanie wejść dla `iChannel0..3`. Dla każdego kanału można wybrać:

- `None`
- `Resource 0`
- `Resource 1`
- `Resource 2`
- `Resource 3`
- `Buffer A`
- `Buffer B`
- `Buffer C`
- `Buffer D`

Kanały Resource korzystają z ustawień `iChannel# Resource`.

Wartości domyślne:

- wszystkie przypisania `iChannel` domyślnie mają wartość `None`
- żaden przebieg Buffer nie jest aktywny, dopóki jego źródło nie będzie niepuste

Ważne:

- Przypisanie wejścia do tego samego przebiegu Buffer (sprzężenie zwrotne) odczytuje dane z poprzedniej klatki (teksturę odczytu w trybie ping-pong).
- Jeśli przypisane źródło nie istnieje lub jest nieaktywne, używana jest tekstura zastępcza, a `iChannelResolution[n].z` przyjmuje wartość `0.0`.

## 5. Współrzędne i semantyka obszaru

Shadery działają w prostokątnym obszarze:

- tło menu: obszar obejmujący cały ekran
- element GLSL: prostokąt elementu

Konwencje współrzędnych:

- Unity pikselowe podają wartości w pikselach lokalnych względem obszaru.
- Początek układu współrzędnych pikseli przekazywanych shaderowi znajduje się w lewym dolnym rogu.
- Współrzędne myszy nie są ograniczane; mogą wykraczać poza obszar, jeśli kursor znajduje się poza nim.

Pola specjalne:

- `fmAreaOffset`: pozycja lewego dolnego rogu obszaru w ekranowym układzie współrzędnych pikseli
- `fmAreaTopLeft`: pozycja lewego górnego rogu obszaru w ekranowym układzie współrzędnych pikseli
- `fmAreaSize`: rozmiar obszaru w pikselach

## 6. Opis API uniformów

Wszystkie poniższe uniformy są dostępne zarówno dla shaderów tła, jak i elementów.

## 6.1 Uniformy zgodne z Shadertoy

| Uniform | Typ | Znaczenie |
|---|---|---|
| `iResolution` | `vec3` | `(areaWidthPx, areaHeightPx, 1.0)` |
| `iTime` | `float` | Skumulowany czas działania shadera w sekundach |
| `iTimeDelta` | `float` | Czas od poprzedniego renderowania, zależny od zamrożenia/czynnika skali czasu |
| `iFrameRate` | `float` | FPS w czasie działania; w razie potrzeby używa FPS Minecrafta jako wartości zastępczej |
| `iFrame` | `int` | Licznik klatek dla danego środowiska uruchomieniowego |
| `iMouse` | `vec4` | Szczegóły poniżej |
| `iDate` | `vec4` | `(rok, miesiąc, dzień, sekundy dnia z ułamkiem)` |
| `iSampleRate` | `float` | Stała wartość `44100.0` |
| `iChannelTime[4]` | `float[4]` | Obecnie wszystkie mają wartość `iTime` |
| `iChannelResolution[4]` | `vec3[4]` | `(szerokość, wysokość, flagaPoprawności)` dla każdego kanału |
| `iChannel0..3` | `sampler2D` | Przypisane tekstury wejściowe |

### Szczegóły `iMouse`

`iMouse = vec4(x, y, z, w)`

- `x`, `y`: bieżąca pozycja myszy w pikselach lokalnych względem obszaru albo pozycja zatrzymana/zamrożona, jeśli włączono tę opcję
- `z`, `w`: pozycja kliknięcia lewym przyciskiem
  - wartości dodatnie, gdy lewy przycisk myszy jest wciśnięty
  - wartości ujemne po jego zwolnieniu

Działanie kontrolowane przełącznikiem:

- `Update iMouse Position Only While Holding LMB = Off`:
  - `iMouse.xy` aktualizuje się na bieżąco
- `... = On`:
  - `iMouse.xy` aktualizuje się tylko wtedy, gdy lewy przycisk myszy jest wciśnięty; po jego zwolnieniu pozostaje na ostatniej pozycji z czasu przytrzymania

Wartość domyślna:

- `Off` (ciągłe aktualizacje)

## 6.2 Uniformy specyficzne dla FancyMenu

| Uniform | Typ | Znaczenie |
|---|---|---|
| `fmAreaOffset` | `vec2` | Przesunięcie lewego dolnego rogu obszaru w pikselach, w ekranowym układzie współrzędnych |
| `fmAreaSize` | `vec2` | Rozmiar obszaru w pikselach |
| `fmAreaPosition` | `vec2` | To samo co `fmAreaOffset` |
| `fmAreaTopLeft` | `vec2` | Przesunięcie lewego górnego rogu obszaru w pikselach, w ekranowym układzie współrzędnych |
| `fmScreenSize` | `vec2` | Rozmiar całego ekranu w pikselach |
| `fmGuiScale` | `float` | Bieżąca skala GUI |
| `fmMouse` | `vec4` | `(localPxX, localPxYBottom, localNormX, localNormY)` |
| `fmMouseDelta` | `vec2` | Zmiana położenia myszy w pikselach obszaru (oś Y jest odwrócona, aby wskazywała w górę w układzie shadera) |
| `fmMouseButtons` | `ivec4` | Stan wciśnięcia przycisków `0..3` |
| `fmMouseClickCount` | `ivec4` | Łączna liczba naciśnięć przycisków `0..3` |
| `fmMouseReleaseCount` | `ivec4` | Łączna liczba zwolnień przycisków `0..3` |
| `fmMouseScroll` | `vec2` | Zmiana przewijania od poprzedniego renderowania tego środowiska uruchomieniowego |
| `fmMouseScrollTotal` | `vec2` | Łączna wartość przewijania |
| `fmKeyEvent` | `ivec4` | `(ostatniKodKlawisza, ostatniKodSkanowania, ostatnieModyfikatory, ostatniaAkcja)` |
| `fmKeyEventCount` | `int` | Łączny licznik zdarzeń klawiatury |
| `fmCharEvent` | `ivec4` | `(ostatniPunktKodowy, ostatnieModyfikatory, 0, 0)` |
| `fmCharEventCount` | `int` | Łączny licznik zdarzeń wpisania znaków |
| `fmDateParts` | `ivec4` | `(rok, miesiąc, dzień, dzieńTygodniaISO1Do7)` |
| `fmTimeParts` | `ivec4` | `(godzina, minuta, sekunda, częśćMilisekundowa0Do999)` |
| `fmDayOfYear` | `int` | Dzień roku |
| `fmWeekOfYear` | `int` | Numer tygodnia roku według ISO |
| `fmUnixTimeSeconds` | `int` | Sekundy od epoki uniksowej |
| `fmUnixTimeMilliseconds` | `int` | Część milisekundowa bieżącego czasu (`0..999`) |
| `fmPartialTick` | `float` | Bieżący ułamek ticka |
| `fmGameDeltaTicks` | `float` | Zmiana liczby ticków gry Minecraft |
| `fmRealtimeDeltaTicks` | `float` | Zmiana liczby ticków czasu rzeczywistego Minecrafta |
| `fmInWorld` | `int` | `1`, gdy gracz jest w świecie; w przeciwnym razie `0` |
| `fmIsPaused` | `int` | `1`, gdy gra jest wstrzymana; w przeciwnym razie `0` |
| `fmOpacity` | `float` | Efektywny mnożnik krycia (`0..1`) |
| `fmVariableCount` | `int` | Bieżąca liczba zmiennych FancyMenu |

Wartości akcji klawisza (`fmKeyEvent.w`):

- `0` = zwolnienie
- `1` = naciśnięcie
- `2` = powtórzenie

## 6.3 API uniformów zmiennych FancyMenu

Zmienne FancyMenu są udostępniane bezpośrednio jako uniformy środowiska uruchomieniowego (dla shaderów tła, elementów i nakładek dekoracyjnych), bez ponownej kompilacji shaderów po zmianie wartości.

### Nazewnictwo

Dla każdej zmiennej `<name>` FancyMenu udostępnia:

- `fmVarFloat_<name>`
- `fmVarInt_<name>`
- `fmVarBool_<name>`
- `fmVarVec2_<name>`
- `fmVarVec3_<name>`
- `fmVarVec4_<name>`
- `fmVarExists_<name>` (`1` = zmienna istnieje, `0` = nie istnieje/została usunięta)

Oczyszczanie sufiksu uniformu `<name>`:

- dozwolone znaki to `[A-Za-z0-9_]`
- wszystkie pozostałe znaki są zamieniane na `_`
- jeśli pierwszy znak jest cyfrą, na początku dodawany jest `_`

Przykłady:

- zmienna `player_hp` -> sufiks `player_hp`
- zmienna `player-hp` -> sufiks `player_hp`
- zmienna `2nd_phase` -> sufiks `_2nd_phase`

Ważne:

- te dynamiczne uniformy zmiennych **nie są deklarowane automatycznie** w źródle shadera (zadeklaruj ręcznie te, których używasz)
- unikaj nazw zmiennych, które po oczyszczeniu dają ten sam sufiks, ponieważ będą wskazywać tę samą nazwę uniformu GLSL

### Konwersja wartości

Dla tekstowej wartości zmiennej `v`:

- `fmVarFloat_*`: sparsowana liczba zmiennoprzecinkowa (wartość zastępcza `0.0`)
- `fmVarInt_*`: sparsowana liczba całkowita (wartość zastępcza `0`)
- `fmVarBool_*`: interpretacja jako wartość logiczna/liczba całkowita (`true/yes/on/enabled` => `1`, `false/no/off/disabled` => `0`, w pozostałych przypadkach wartość liczbowa różna od zera => `1`)
- podczas parsowania wektorów akceptowane są separatory: białe znaki, `,`, `;`, `|`
  - `fmVarVec2_*`: pierwsze 2 sparsowane składowe
  - `fmVarVec3_*`: pierwsze 3 sparsowane składowe
  - `fmVarVec4_*`: pierwsze 4 sparsowane składowe
  - jeśli składowych jest mniej, ostatnia sparsowana składowa jest powielana w brakujących miejscach
  - jeśli nie ma żadnych składowych liczbowych, dla wszystkich składowych wektora używana jest skalarna wartość zastępcza

[Zmienne listowe](/variables#text-and-list-variables) zwracają liczbę wpisów zamiast tekstu:

- `fmVarFloat_*` i `fmVarInt_*`: liczba wpisów, np. `3` dla listy zawierającej 3 wpisy
- `fmVarBool_*`: `1`, jeśli lista zawiera wpisy; `0`, jeśli jest pusta
- `fmVarVec2_*`, `fmVarVec3_*` i `fmVarVec4_*`: liczba wpisów w każdej składowej

Po usunięciu zmiennej:

- `fmVarExists_*` przyjmuje wartość `0`
- wszystkie odpowiadające jej wartości `fmVar*_*` są resetowane do `0`

### Przykładowa deklaracja i użycie

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

FancyMenu śledzi wejście globalnie i zapisuje jego stan dla każdego renderowania:

- ruch/przeciąganie myszy
- naciśnięcie/zwolnienie przycisku myszy
- przewijanie
- naciśnięcie/zwolnienie/powtórzenie klawisza
- wpisanie znaku

Stabilność obsługi myszy:

- Środowisko uruchomieniowe co klatkę uzgadnia stany przycisków z odczytem GLFW, aby zapobiec zawieszeniu stanu wciśnięcia przycisku.

Jeśli opcja `Pass Input Events To Shader` jest wyłączona:

- uniformy wejściowe są co klatkę resetowane do neutralnych wartości
- liczniki i zdarzenia widoczne dla shadera są zerowane

## 8. Szczegóły wejść tekstur

Kanały Resource (`iChannel# Resource`) oczekują tekstur 2D.

Stan tekstury dla każdego kanału:

- prawidłowy zasób: przypisana tekstura, rzeczywista szerokość/wysokość, `iChannelResolution[n].z = 1.0`
- brakujący/nieaktywny/None: tekstura zastępcza, `iChannelResolution[n].xyz = (0,0,0)`

Tekstury Buffer:

- format wewnętrzny: `RGBA16F` (zmiennoprzecinkowy)
- filtrowanie: liniowe
- zawijanie: ograniczenie do krawędzi

Nadaje się to do danych wieloprzebiegowych (w tym wartości spoza zakresu `[0,1]`).

## 9. Uwagi dotyczące renderowania i mieszania

- Przebiegi Buffer są renderowane poza ekranem, bez mieszania.
- Końcowy przebieg Image używa ustawienia `Enable Blending` do kompozycji.
- Wrapper Shadertoy automatycznie stosuje `fmOpacity` do alfy.
- W razie potrzeby shadery Direct powinny ręcznie stosować `fmOpacity`.

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

## 10.3 Minimalne sprzężenie zwrotne w wielu przebiegach

### Źródło Buffer A

Przypisanie: `Buffer A iChannel0 Input -> Buffer A`

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord) {
    vec2 uv = fragCoord / iResolution.xy;
    vec4 prev = texture(iChannel0, uv);
    vec4 seed = vec4(uv, 0.0, 1.0);
    fragColor = mix(prev, seed, 0.02);
}
```

### Źródło Image

Przypisanie: `Image iChannel0 Input -> Buffer A`

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord) {
    vec2 uv = fragCoord / iResolution.xy;
    fragColor = texture(iChannel0, uv);
}
```

## 11. Lista kontrolna rozwiązywania problemów

- Brak obrazu:
  - upewnij się, że źródło Image nie jest puste
  - upewnij się, że tryb kompilacji odpowiada punktowi wejścia (`mainImage` lub `main`)
- Fioletowe/nieprawidłowe tekstury:
  - sprawdź przypisania zasobów i kanałów
  - sprawdź `iChannelResolution[n].z` (`0.0` oznacza, że tekstura jest nieprawidłowa lub niedostępna)
- Nieprawidłowe współrzędne w shaderze Direct:
  - użyj `gl_FragCoord.xy - fmAreaOffset`, aby uzyskać współrzędne lokalne względem obszaru
- Nieprawidłowe działanie przeciągania:
  - użyj przełącznika `Update iMouse Position Only While Holding LMB`
- Krycie nie jest stosowane w shaderze Direct:
  - samodzielnie pomnóż alfę przez `fmOpacity`
