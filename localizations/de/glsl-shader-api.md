---
title: GLSL-Shader-API
description: >-
  Schreibe ausgefallene FancyMenu-GLSL-Shader für Hintergründe, Elemente und
  Dekorations-Overlays.
---

# FancyMenu GLSL-Shader-API

Dieses Dokument beschreibt die GLSL-Laufzeitumgebung, die von FancyMenus folgenden Bereichen verwendet wird:

- `GLSL`-Menühintergrund
- `GLSL`-Element
- `GLSL`-Dekorations-Overlay

Es behandelt Kompiliermodi, Multipass-Routing, unterstützte Uniforms und praktische Muster zum Schreiben von Shadern.

## 1. Überblick über die Laufzeit

FancyMenu rendert Shader mit einer internen OpenGL-Pipeline (`#version 150`) und unterstützt:

- Ein-Pass-Shader (`Image`-Pass nur)
- Multipass-Shader (`Buffer A` / `B` / `C` / `D` + `Image`)
- Shadertoy-ähnliche Einstiegspunkte (`mainImage`)
- direkte Fragment-Einstiegspunkte (`main`)

Shader-Quellen sind eingebettete Textfelder:

- `Shader Source` (Image-Pass, erforderlich für die Ausgabe)
- `Buffer A Source` (optional)
- `Buffer B Source` (optional)
- `Buffer C Source` (optional)
- `Buffer D Source` (optional)

Wenn die Image-Quelle leer ist, schlägt das Rendering mit einem „no source“-Fehler fehl.

## 2. Kompiliermodi

FancyMenu unterstützt drei Kompiliermodi:

- `Auto`
- `Direct Fragment`
- `Shadertoy`

### 2.1 Shadertoy-Modus

Erwarteter Einstiegspunkt:

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord)
```

FancyMenu wickelt ihn in `main()` ein und übergibt lokale Flächenkoordinaten:

```glsl
mainImage(fmColor_FancyMenu, gl_FragCoord.xy - fmAreaOffset);
```

Der Wrapper multipliziert die Alpha-Ausgabe mit `fmOpacity`.

### 2.2 Direct-Modus

Erwarteter Einstiegspunkt:

```glsl
void main()
```

Kompatibilitätsverhalten:

- Eine kompatible Variante mit `gl_FragColor` wird versucht.
- Zusätzlich wird eine Variante ohne Kompatibilität versucht (für moderne Shader mit explizitem `out vec4`).

Im Direct-Modus wird `fmOpacity` nicht automatisch auf deine Ausgabe angewendet. Wende es bei Bedarf manuell an.

### 2.3 Auto-Modus

Auto versucht kompatible Varianten nacheinander (Shadertoy/Direct) und verwendet die erste, die kompiliert.

## 3. Quellvorverarbeitung und eingebaute Makros

Vor dem Kompilieren normalisiert FancyMenu den Quelltext:

- entfernt UTF-8-BOM
- wandelt CRLF/CR in LF um
- entfernt `#version ...`-Zeilen
- entfernt `precision ...;`-Zeilen

Die zur Laufzeit eingefügte Präambel enthält:

- `#version 150`
- `in vec2 fmUv_FancyMenu` (Fullscreen-UV in `[0,1]`, Ursprung unten links)
- `#define iGlobalTime iTime`
- `#define texture2D texture`
- `#define textureCube texture`

Hinweis:

- Wenn dein Quelltext bereits einen bekannten Uniform-Namen deklariert (z. B. `iTime`), fügt FancyMenu keine doppelte Deklaration ein.
- FancyMenu versucht trotzdem, zur Laufzeit Werte an diesen Namen zu senden.
- `textureCube` ist hier nur ein Alias-Makro; `iChannel0..3` sind `sampler2D`-Uniforms.

## 4. Pass-System (Image + Buffer A-D)

FancyMenu hat 5 Pass-Slots:

- `Buffer A`
- `Buffer B`
- `Buffer C`
- `Buffer D`
- `Image` (finaler On-Screen-Pass)

Verhalten:

- Buffer-Pässe werden nur ausgeführt, wenn ihre Quelle nicht leer ist.
- Der Image-Pass muss vorhanden sein, damit Ausgabe gerendert wird.
- Buffer werden in Floating-Point-Texturen (`GL_RGBA16F`) gerendert und dann per Ping-Pong gewechselt (Lese-/Schreibtausch pro Frame).

### 4.1 Kanal-Routing pro Pass

Jeder Pass bietet Routing für `iChannel0..3`. Pro Kanal kannst du wählen:

- `None`
- `Resource 0`
- `Resource 1`
- `Resource 2`
- `Resource 3`
- `Buffer A`
- `Buffer B`
- `Buffer C`
- `Buffer D`

Ressourcenkanäle stammen aus den Einstellungen `iChannel# Resource`.

Standardwerte:

- alle `iChannel`-Routings stehen standardmäßig auf `None`
- kein Buffer-Pass ist aktiv, bis die entsprechende Buffer-Quelle nicht leer ist

Wichtig:

- Routing auf denselben Buffer-Pass (Feedback) liest die Daten des vorherigen Frames (Ping-Pong-Lesetextur).
- Wenn eine geroutete Quelle fehlt/inaktiv ist, wird eine Fallback-Textur gebunden und `iChannelResolution[n].z` wird `0.0`.

## 5. Koordinaten und Flächen-Semantik

Shader laufen in einem Flächen-Rechteck:

- Menühintergrund: vollständige Bildschirmfläche
- GLSL-Element: Element-Rechteck

Koordinatenkonventionen:

- Pixel-Uniforms sind in lokalen Pixeln der Fläche angegeben.
- Der Y-Ursprung ist für shaderseitige Pixelkoordinaten unten links.
- Mauskoordinaten werden nicht begrenzt; Werte können außerhalb der Fläche liegen, wenn der Cursor außerhalb ist.

Spezielle Felder:

- `fmAreaOffset`: Position der unteren linken Ecke der Fläche im Bildschirm-Pixelraum
- `fmAreaTopLeft`: Position der oberen linken Ecke der Fläche im Bildschirm-Pixelraum
- `fmAreaSize`: Größe der Fläche in Pixeln

## 6. Referenz der Uniform-API

Alle unten aufgeführten Uniforms stehen sowohl für Hintergrund- als auch für Element-Shader zur Verfügung.

## 6.1 Shadertoy-kompatible Uniforms

| Uniform | Typ | Bedeutung |
|---|---|---|
| `iResolution` | `vec3` | `(areaWidthPx, areaHeightPx, 1.0)` |
| `iTime` | `float` | Aufaddierte Shader-Zeit in Sekunden |
| `iTimeDelta` | `float` | Delta-Zeit des letzten Renderns, beeinflusst durch Freeze/Zeit-Skalierung |
| `iFrameRate` | `float` | Fallback-Laufzeit-FPS basierend auf Minecraft-FPS |
| `iFrame` | `int` | Frame-Zähler pro Laufzeit |
| `iMouse` | `vec4` | Siehe Details unten |
| `iDate` | `vec4` | `(year, month, day, secondsOfDayWithFraction)` |
| `iSampleRate` | `float` | Konstante `44100.0` |
| `iChannelTime[4]` | `float[4]` | Derzeit alle auf `iTime` gesetzt |
| `iChannelResolution[4]` | `vec3[4]` | `(width, height, validFlag)` pro Kanal |
| `iChannel0..3` | `sampler2D` | Geroutete Texture-Eingänge |

### Details zu `iMouse`

`iMouse = vec4(x, y, z, w)`

- `x`, `y`: aktuelle Mausposition in Pixeln relativ zur Fläche, oder Hold/Frozen-Verhalten, wenn der Schalter aktiviert ist
- `z`, `w`: Ursprung des linken Klicks
  - positiv, solange die linke Maustaste gedrückt gehalten wird
  - negativ nach dem Loslassen

Schaltergesteuertes Verhalten:

- `Update iMouse Position Only While Holding LMB = Off`:
  - `iMouse.xy` aktualisiert sich fortlaufend
- `... = On`:
  - `iMouse.xy` aktualisiert sich nur, solange LMB gedrückt ist, und bleibt dann an der letzten gehaltenen Position

Standardwert:

- `Off` (fortlaufende Aktualisierung)

## 6.2 FancyMenu-spezifische Uniforms

| Uniform | Typ | Bedeutung |
|---|---|---|
| `fmAreaOffset` | `vec2` | Pixel-Offset der unteren linken Ecke der Fläche im Bildschirmraum |
| `fmAreaSize` | `vec2` | Größe der Fläche in Pixeln |
| `fmAreaPosition` | `vec2` | Dasselbe wie `fmAreaOffset` |
| `fmAreaTopLeft` | `vec2` | Pixel-Offset der oberen linken Ecke der Fläche im Bildschirmraum |
| `fmScreenSize` | `vec2` | Gesamte Bildschirmgröße in Pixeln |
| `fmGuiScale` | `float` | Aktuelle GUI-Skalierung |
| `fmMouse` | `vec4` | `(localPxX, localPxYBottom, localNormX, localNormY)` |
| `fmMouseDelta` | `vec2` | Maus-Delta in Flächenpixeln (Y ist zum Shader-Oben invertiert) |
| `fmMouseButtons` | `ivec4` | Gedrücktzustände für die Tasten `0..3` |
| `fmMouseClickCount` | `ivec4` | Kumulative Drückzähler für die Tasten `0..3` |
| `fmMouseReleaseCount` | `ivec4` | Kumulative Loslasszähler für die Tasten `0..3` |
| `fmMouseScroll` | `vec2` | Scroll-Delta seit dem vorherigen Rendern dieser Laufzeit |
| `fmMouseScrollTotal` | `vec2` | Kumulative Scroll-Gesamtwerte |
| `fmKeyEvent` | `ivec4` | `(lastKeyCode, lastScanCode, lastModifiers, lastAction)` |
| `fmKeyEventCount` | `int` | Kumulativer Zähler für Tastenevents |
| `fmCharEvent` | `ivec4` | `(lastCodePoint, lastModifiers, 0, 0)` |
| `fmCharEventCount` | `int` | Kumulativer Zähler für Zeichen-Eingaben |
| `fmDateParts` | `ivec4` | `(year, month, day, dayOfWeekIso1To7)` |
| `fmTimeParts` | `ivec4` | `(hour, minute, second, millisecondPart0To999)` |
| `fmDayOfYear` | `int` | Tag des Jahres |
| `fmWeekOfYear` | `int` | ISO-Kalenderwoche |
| `fmUnixTimeSeconds` | `int` | Unix-Epochenzeit in Sekunden |
| `fmUnixTimeMilliseconds` | `int` | Millisekundenteil der aktuellen Zeit (`0..999`) |
| `fmPartialTick` | `float` | Aktueller Partial Tick |
| `fmGameDeltaTicks` | `float` | Minecraft-Game-Delta-Ticks |
| `fmRealtimeDeltaTicks` | `float` | Minecraft-Realtime-Delta-Ticks |
| `fmInWorld` | `int` | `1`, wenn in einer Welt, sonst `0` |
| `fmIsPaused` | `int` | `1`, wenn pausiert, sonst `0` |
| `fmOpacity` | `float` | Effektiver Opazitäts-Multiplikator (`0..1`) |
| `fmVariableCount` | `int` | Aktuelle Anzahl von FancyMenu-Variablen |

Werte für Tastenevents (`fmKeyEvent.w`):

- `0` = Loslassen
- `1` = Drücken
- `2` = Wiederholen

## 6.3 FancyMenu Variable Uniform API

FancyMenu-Variablen werden direkt als Laufzeit-Uniforms bereitgestellt (für Hintergrund-, Element- und Dekorations-Overlay-Shader), ohne dass bei Wertänderungen der Shader neu kompiliert werden muss.

### Benennung

Für jede Variable `<name>` stellt FancyMenu bereit:

- `fmVarFloat_<name>`
- `fmVarInt_<name>`
- `fmVarBool_<name>`
- `fmVarVec2_<name>`
- `fmVarVec3_<name>`
- `fmVarVec4_<name>`
- `fmVarExists_<name>` (`1` = Variable existiert aktuell, `0` = nicht vorhanden/entfernt)

Sanitizing des Uniform-Suffixes für `<name>`:

- erlaubte Zeichen sind `[A-Za-z0-9_]`
- alle anderen Zeichen werden zu `_` umgewandelt
- wenn das erste Zeichen eine Ziffer ist, wird `_` vorangestellt

Beispiele:

- Variable `player_hp` -> Suffix `player_hp`
- Variable `player-hp` -> Suffix `player_hp`
- Variable `2nd_phase` -> Suffix `_2nd_phase`

Wichtig:

- diese dynamischen Variablen-Uniforms werden in der Shaderquelle **nicht automatisch deklariert** (deklariere die von dir verwendeten manuell)
- vermeide Variablennamen, die zum selben Suffix sanitizen, da sie auf denselben GLSL-Uniformnamen abgebildet werden

### Wertumwandlung

Für den Variablentextwert `v` gilt:

- `fmVarFloat_*`: geparster Float (`0.0` als Fallback)
- `fmVarInt_*`: geparster Int (`0` als Fallback)
- `fmVarBool_*`: boolesche/int-Interpretation (`true/yes/on/enabled` => `1`, `false/no/off/disabled` => `0`, sonst numerisch ungleich `0` => `1`)
- Vektor-Parsing akzeptiert Trennzeichen: Leerzeichen, `,`, `;`, `|`
  - `fmVarVec2_*`: erste 2 geparste Komponenten
  - `fmVarVec3_*`: erste 3 geparste Komponenten
  - `fmVarVec4_*`: erste 4 geparste Komponenten
  - wenn weniger Komponenten vorhanden sind, wird die zuletzt geparste Komponente für fehlende Plätze wiederholt
  - wenn keine numerischen Komponenten vorhanden sind, verwenden alle Vektorkomponenten den Skalar-Fallback

Wenn eine Variable entfernt wird:

- `fmVarExists_*` wird zu `0`
- alle zugehörigen `fmVar*_*`-Werte werden auf `0` zurückgesetzt

### Beispiel-Deklaration und Verwendung

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

## 7. Modell zur Eingabeverfolgung

FancyMenu verfolgt Eingaben global und speichert sie pro Render-Snapshot:

- Mausbewegung/-ziehen
- Maus drücken/loslassen
- Scrollen
- Taste drücken/loslassen/wiederholen
- Zeichen eingeben

Robustheit der Maus:

- Die Laufzeit gleicht die Tastenzustände jedes Frame mit dem GLFW-Polling ab, um festhängende Button-Zustände zu verhindern.

Wenn `Pass Input Events To Shader` deaktiviert ist:

- Eingabe-Uniforms werden pro Frame auf neutrale Werte zurückgesetzt
- Zähler und Events werden in den shader-sichtbaren Daten auf Null gesetzt

## 8. Details zu Texture-Eingaben

Ressourcenkanäle (`iChannel# Resource`) erwarten 2D-Texturen.

Texturstatus pro Kanal:

- gültige Ressource: gebundene Textur, echte Breite/Höhe, `iChannelResolution[n].z = 1.0`
- fehlt/inaktiv/None: Fallback-Textur, `iChannelResolution[n].xyz = (0,0,0)`

Buffer-Texturen:

- internes Format: `RGBA16F` (Floating Point)
- Filterung: linear
- Wrap: clamp-to-edge

Das ist für Multipass-Daten geeignet (einschließlich Werten außerhalb von `[0,1]`).

## 9. Hinweise zu Rendering und Blending

- Buffer-Pässe rendern offscreen ohne Blending.
- Der finale Image-Pass verwendet die Einstellung `Enable Blending` für das Compositing.
- Der Shadertoy-Wrapper wendet `fmOpacity` automatisch auf Alpha an.
- Direkte Shader sollten `fmOpacity` bei Bedarf manuell anwenden.

## 10. Praktische Vorlagen

## 10.1 Minimaler Shadertoy-ähnlicher Shader

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord) {
    vec2 uv = fragCoord / iResolution.xy;
    vec3 col = vec3(uv, 0.5 + 0.5 * sin(iTime));
    fragColor = vec4(col, 1.0);
}
```

## 10.2 Minimaler direkter Fragment-Shader

```glsl
out vec4 FragColor;

void main() {
    vec2 uv = gl_FragCoord.xy - fmAreaOffset;
    uv /= iResolution.xy;

    vec3 col = vec3(uv.x, uv.y, 0.5 + 0.5 * sin(iTime));
    FragColor = vec4(col, fmOpacity);
}
```

## 10.3 Minimaler Feedback-Multipass

### Quelle von Buffer A

Routing: `Buffer A iChannel0 Input -> Buffer A`

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord) {
    vec2 uv = fragCoord / iResolution.xy;
    vec4 prev = texture(iChannel0, uv);
    vec4 seed = vec4(uv, 0.0, 1.0);
    fragColor = mix(prev, seed, 0.02);
}
```

### Quelle von Image

Routing: `Image iChannel0 Input -> Buffer A`

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord) {
    vec2 uv = fragCoord / iResolution.xy;
    fragColor = texture(iChannel0, uv);
}
```

## 11. Checkliste zur Fehlerbehebung

- Keine Ausgabe:
  - prüfen, ob die Image-Quelle nicht leer ist
  - prüfen, ob der Kompiliermodus zu deinem Einstiegspunkt passt (`mainImage` vs. `main`)
- Violette/ungültige Texturen:
  - Ressourcenbindungen und Kanal-Routing prüfen
  - `iChannelResolution[n].z` prüfen (`0.0` bedeutet ungültig/nicht verfügbar)
- Falsche Koordinaten im Direct-Shader:
  - für lokale Flächenkoordinaten `gl_FragCoord.xy - fmAreaOffset` verwenden
- Drag-Verhalten falsch:
  - den Schalter `Update iMouse Position Only While Holding LMB` verwenden
- Opazität wird im Direct-Shader nicht angewendet:
  - Alpha selbst mit `fmOpacity` multiplizieren
