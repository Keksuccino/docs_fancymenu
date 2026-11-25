---
title: GLSL-Shader-API
description: >-
  Erstelle FancyMenu-GLSL-Shader für Hintergründe, Elemente und dekorative
  Overlays.
sourceBlobSha: f3da9c3fe83444dab5c59f74f5011e2d6e8cf9e6
---

# FancyMenu-GLSL-Shader-API

Dieses Dokument beschreibt die von FancyMenu verwendete GLSL-Laufzeit für:

- `GLSL`-Menühintergründe
- `GLSL`-Elemente
- `GLSL`-Dekorations-Overlays

Es behandelt Kompilierungsmodi, Multipass-Routing, unterstützte Uniforms und praktische Muster zur Shader-Erstellung.

## 1. Laufzeitübersicht

FancyMenu rendert Shader mit einer internen OpenGL-Pipeline (`#version 150`) und unterstützt:

- Single-Pass-Shader (nur der `Image`-Pass)
- Multipass-Shader (`Buffer A` / `B` / `C` / `D` + `Image`)
- Shadertoy-ähnliche Einstiegspunkte (`mainImage`)
- direkte Fragment-Einstiegspunkte (`main`)

Shader-Quelltexte werden in Textfeldern eingegeben:

- `Shader Source` (Image-Pass, zum Rendern erforderlich)
- `Buffer A Source` (optional)
- `Buffer B Source` (optional)
- `Buffer C Source` (optional)
- `Buffer D Source` (optional)

Ist der Image-Quelltext leer, schlägt das Rendern mit dem Fehler „no source“ fehl.

## 2. Kompilierungsmodi

FancyMenu unterstützt drei Kompilierungsmodi:

- `Auto`
- `Direct Fragment`
- `Shadertoy`

### 2.1 Shadertoy-Modus

Erwarteter Einstiegspunkt:

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord)
```

FancyMenu bindet die Funktion in `main()` ein und übergibt lokale Bereichskoordinaten:

```glsl
mainImage(fmColor_FancyMenu, gl_FragCoord.xy - fmAreaOffset);
```

Der Wrapper multipliziert die Ausgabealpha mit `fmOpacity`.

### 2.2 Direct-Modus

Erwarteter Einstiegspunkt:

```glsl
void main()
```

Kompatibilitätsverhalten:

- Es wird eine kompatible Variante mit `gl_FragColor` ausprobiert.
- Zusätzlich wird eine Variante ohne Kompatibilitätsanpassungen ausprobiert (für moderne Shader mit explizitem `out vec4`).

Im Direct-Modus wird `fmOpacity` nicht automatisch auf deine Ausgabe angewendet. Wende den Wert bei Bedarf manuell an.

### 2.3 Auto-Modus

Auto probiert der Reihe nach kompatible Varianten (Shadertoy/Direct) aus und verwendet die erste, die sich kompilieren lässt.

## 3. Vorverarbeitung des Quelltexts und integrierte Makros

Vor dem Kompilieren normalisiert FancyMenu den Quelltext:

- entfernt eine UTF-8-BOM
- wandelt CRLF/CR in LF um
- entfernt `#version ...`-Zeilen
- entfernt `precision ...;`-Zeilen

Der zur Laufzeit eingefügte Präambeltext enthält:

- `#version 150`
- `in vec2 fmUv_FancyMenu` (Vollbild-UV-Koordinaten im Bereich `[0,1]`, Ursprung unten links)
- `#define iGlobalTime iTime`
- `#define texture2D texture`
- `#define textureCube texture`

Hinweis:

- Deklariert dein Quelltext bereits einen bekannten Uniform-Namen (z. B. `iTime`), vermeidet FancyMenu eine doppelte Deklaration.
- FancyMenu versucht trotzdem, diesem Namen zur Laufzeit Werte zuzuweisen.
- `textureCube` ist hier lediglich ein Alias-Makro; `iChannel0..3` sind `sampler2D`-Uniforms.

## 4. Pass-System (Image + Buffer A–D)

FancyMenu verfügt über fünf Pass-Slots:

- `Buffer A`
- `Buffer B`
- `Buffer C`
- `Buffer D`
- `Image` (der abschließende Pass für die Bildschirmausgabe)

Verhalten:

- Buffer-Pässe werden nur ausgeführt, wenn ihr Quelltext nicht leer ist.
- Zum Rendern einer Ausgabe muss ein Image-Pass vorhanden sein.
- Buffer werden in Fließkomma-Texturen (`GL_RGBA16F`) gerendert und anschließend per Ping-Pong-Verfahren genutzt (Lese-/Schreibtextur werden bei jedem Frame getauscht).

### 4.1 Kanal-Routing pro Pass

Für jeden Pass lässt sich das Routing von `iChannel0..3` festlegen. Pro Kanal kannst du Folgendes auswählen:

- `None`
- `Resource 0`
- `Resource 1`
- `Resource 2`
- `Resource 3`
- `Buffer A`
- `Buffer B`
- `Buffer C`
- `Buffer D`

Ressourcenkanäle beziehen ihre Werte aus den Einstellungen für `iChannel# Resource`.

Standardwerte:

- Für alle `iChannel`-Routings ist `None` voreingestellt.
- Ein Buffer-Pass ist erst aktiv, wenn sein Quelltext nicht leer ist.

Wichtig:

- Wird ein Pass auf denselben Buffer-Pass geroutet (Feedback), werden Daten aus dem vorherigen Frame gelesen (Ping-Pong-Lesetextur).
- Fehlt eine geroutete Quelle oder ist sie inaktiv, wird eine Fallback-Textur gebunden und `iChannelResolution[n].z` auf `0.0` gesetzt.

## 5. Koordinaten und Bereichssemantik

Shader werden innerhalb eines rechteckigen Bereichs ausgeführt:

- Menühintergrund: gesamter Bildschirmbereich
- GLSL-Element: Rechteck des Elements

Koordinatenkonventionen:

- Pixel-Uniforms verwenden lokale Pixelkoordinaten des Bereichs.
- Der Ursprung shaderseitiger Pixelkoordinaten liegt unten links.
- Mauskoordinaten werden nicht begrenzt; befindet sich der Cursor außerhalb des Bereichs, können die Werte außerhalb des Bereichs liegen.

Spezielle Felder:

- `fmAreaOffset`: Position der unteren linken Ecke des Bereichs im Bildschirm-Pixelkoordinatensystem
- `fmAreaTopLeft`: Position der oberen linken Ecke des Bereichs im Bildschirm-Pixelkoordinatensystem
- `fmAreaSize`: Größe des Bereichs in Pixeln

## 6. Referenz der Uniform-API

Alle folgenden Uniforms sind sowohl für Hintergrund- als auch für Element-Shader verfügbar.

## 6.1 Shadertoy-kompatible Uniforms

| Uniform | Typ | Bedeutung |
|---|---|---|
| `iResolution` | `vec3` | `(areaWidthPx, areaHeightPx, 1.0)` |
| `iTime` | `float` | Aufsummierte Shader-Zeit in Sekunden |
| `iTimeDelta` | `float` | Zeitdifferenz seit dem letzten Rendern, beeinflusst durch Einfrieren und Zeitskalierung |
| `iFrameRate` | `float` | Minecraft-FPS; dient als Fallback für die Laufzeit-FPS |
| `iFrame` | `int` | Frame-Zähler pro Laufzeitinstanz |
| `iMouse` | `vec4` | Siehe Details unten |
| `iDate` | `vec4` | `(Jahr, Monat, Tag, Sekunden des Tages mit Nachkommastellen)` |
| `iSampleRate` | `float` | Konstante `44100.0` |
| `iChannelTime[4]` | `float[4]` | Aktuell werden alle auf `iTime` gesetzt |
| `iChannelResolution[4]` | `vec3[4]` | `(Breite, Höhe, Gültigkeitsflag)` für jeden Kanal |
| `iChannel0..3` | `sampler2D` | Geroutete Textur-Eingaben |

### Details zu `iMouse`

`iMouse = vec4(x, y, z, w)`

- `x`, `y`: aktuelle lokale Mausposition im Bereich in Pixeln; abhängig von der Umschaltoption wird sie gehalten bzw. eingefroren
- `z`, `w`: Ursprung des Linksklicks
  - positiv, solange die linke Maustaste gedrückt ist
  - negativ nach dem Loslassen

Verhalten abhängig von der Umschaltoption:

- `Update iMouse Position Only While Holding LMB = Off`:
  - `iMouse.xy` wird kontinuierlich aktualisiert
- `... = On`:
  - `iMouse.xy` wird nur aktualisiert, solange die linke Maustaste gedrückt ist, und bleibt anschließend auf der zuletzt gehaltenen Position

Standardwert:

- `Off` (kontinuierliche Aktualisierung)

## 6.2 FancyMenu-spezifische Uniforms

| Uniform | Typ | Bedeutung |
|---|---|---|
| `fmAreaOffset` | `vec2` | Pixelversatz der unteren linken Ecke des Bereichs im Bildschirmkoordinatensystem |
| `fmAreaSize` | `vec2` | Größe des Bereichs in Pixeln |
| `fmAreaPosition` | `vec2` | Entspricht `fmAreaOffset` |
| `fmAreaTopLeft` | `vec2` | Pixelversatz der oberen linken Ecke des Bereichs im Bildschirmkoordinatensystem |
| `fmScreenSize` | `vec2` | Bildschirmgröße in Pixeln |
| `fmGuiScale` | `float` | Aktuelle GUI-Skalierung |
| `fmMouse` | `vec4` | `(lokalesPxX, lokalesPxYVonUnten, lokalesNormX, lokalesNormY)` |
| `fmMouseDelta` | `vec2` | Mausbewegung in Bereichspixeln (Y ist für die Shader-Achse nach oben invertiert) |
| `fmMouseButtons` | `ivec4` | Gedrückter Zustand der Schaltflächen `0..3` |
| `fmMouseClickCount` | `ivec4` | Kumulierte Anzahl der Tastendrücke für Schaltflächen `0..3` |
| `fmMouseReleaseCount` | `ivec4` | Kumulierte Anzahl der Loslassereignisse für Schaltflächen `0..3` |
| `fmMouseScroll` | `vec2` | Scrollbewegung seit dem vorherigen Rendern dieser Laufzeitinstanz |
| `fmMouseScrollTotal` | `vec2` | Kumulierte Scrollwerte |
| `fmKeyEvent` | `ivec4` | `(letzterKeyCode, letzterScanCode, letzteModifier, letzteAktion)` |
| `fmKeyEventCount` | `int` | Kumulativer Tastaturereignis-Zähler |
| `fmCharEvent` | `ivec4` | `(letzterCodePoint, letzteModifier, 0, 0)` |
| `fmCharEventCount` | `int` | Kumulativer Zähler für eingegebene Zeichenereignisse |
| `fmDateParts` | `ivec4` | `(Jahr, Monat, Tag, Wochentag nach ISO 1 bis 7)` |
| `fmTimeParts` | `ivec4` | `(Stunde, Minute, Sekunde, Millisekundenanteil 0 bis 999)` |
| `fmDayOfYear` | `int` | Tag des Jahres |
| `fmWeekOfYear` | `int` | ISO-Kalenderwoche des Jahres |
| `fmUnixTimeSeconds` | `int` | Sekunden seit der Unix-Epoche |
| `fmUnixTimeMilliseconds` | `int` | Millisekundenanteil der aktuellen Zeit (`0..999`) |
| `fmPartialTick` | `float` | Aktueller Partial Tick |
| `fmGameDeltaTicks` | `float` | Minecraft-Game-Delta-Ticks |
| `fmRealtimeDeltaTicks` | `float` | Minecraft-Realtime-Delta-Ticks |
| `fmInWorld` | `int` | `1`, wenn du dich in einer Welt befindest, andernfalls `0` |
| `fmIsPaused` | `int` | `1`, wenn das Spiel pausiert ist, andernfalls `0` |
| `fmOpacity` | `float` | Effektiver Deckkraftmultiplikator (`0..1`) |
| `fmVariableCount` | `int` | Aktuelle Anzahl der FancyMenu-Variablen |

Werte für Tastaturaktionen (`fmKeyEvent.w`):

- `0` = Loslassen
- `1` = Drücken
- `2` = Wiederholen

## 6.3 Uniform-API für FancyMenu-Variablen

FancyMenu-Variablen werden direkt als Laufzeit-Uniforms bereitgestellt (für Hintergrund-, Element- und Dekorations-Overlay-Shader). Änderungen an ihren Werten erfordern keine Neukompilierung des Shaders.

### Benennung

Für jede Variable `<name>` stellt FancyMenu Folgendes bereit:

- `fmVarFloat_<name>`
- `fmVarInt_<name>`
- `fmVarBool_<name>`
- `fmVarVec2_<name>`
- `fmVarVec3_<name>`
- `fmVarVec4_<name>`
- `fmVarExists_<name>` (`1` = Variable ist vorhanden, `0` = nicht vorhanden/entfernt)

Bereinigung des Uniform-Suffixes für `<name>`:

- Zulässig sind die Zeichen `[A-Za-z0-9_]`.
- Alle anderen Zeichen werden in `_` umgewandelt.
- Beginnt der Name mit einer Ziffer, wird `_` vorangestellt.

Beispiele:

- Variable `player_hp` -> Suffix `player_hp`
- Variable `player-hp` -> Suffix `player_hp`
- Variable `2nd_phase` -> Suffix `_2nd_phase`

Wichtig:

- Diese dynamischen Variablen-Uniforms werden im Shader-Quelltext **nicht automatisch deklariert** (deklariere die verwendeten Uniforms manuell).
- Vermeide Variablennamen, die nach der Bereinigung dasselbe Suffix ergeben, da sie dann demselben GLSL-Uniform-Namen zugeordnet werden.

### Wertumwandlung

Für einen Textwert `v` einer Variable gilt:

- `fmVarFloat_*`: geparster Float-Wert (Fallback: `0.0`)
- `fmVarInt_*`: geparster Int-Wert (Fallback: `0`)
- `fmVarBool_*`: Interpretation als Boolean/Integer (`true/yes/on/enabled` => `1`, `false/no/off/disabled` => `0`, andernfalls numerischer Wert ungleich null => `1`)
- Beim Parsen von Vektoren werden folgende Trennzeichen akzeptiert: Leerzeichen, `,`, `;`, `|`
  - `fmVarVec2_*`: die ersten 2 geparsten Komponenten
  - `fmVarVec3_*`: die ersten 3 geparsten Komponenten
  - `fmVarVec4_*`: die ersten 4 geparsten Komponenten
  - Sind weniger Komponenten vorhanden, wird die letzte geparste Komponente für fehlende Werte wiederholt.
  - Sind keine numerischen Komponenten vorhanden, wird für alle Vektorkomponenten der skalare Fallback-Wert verwendet.

[Listenvariablen](/variables#text-and-list-variables) liefern statt ihres Textwerts die Anzahl ihrer Einträge:

- `fmVarFloat_*` und `fmVarInt_*`: Anzahl der Einträge, z. B. `3` bei einer Liste mit 3 Einträgen
- `fmVarBool_*`: `1`, wenn die Liste Einträge enthält, andernfalls `0`
- `fmVarVec2_*`, `fmVarVec3_*` und `fmVarVec4_*`: Anzahl der Einträge in jeder Komponente

Wird eine Variable entfernt:

- wird `fmVarExists_*` auf `0` gesetzt
- werden alle zugehörigen `fmVar*_*`-Werte auf `0` zurückgesetzt

### Beispiel für Deklaration und Verwendung

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

## 7. Modell zur Eingabeerfassung

FancyMenu erfasst Eingaben global und erstellt für jeden Renderdurchlauf eine Momentaufnahme:

- Mausbewegung/Ziehen
- Maustaste drücken/loslassen
- Scrollen
- Taste drücken/loslassen/wiederholen
- Zeichen eingeben

Zuverlässigkeit der Mauseingaben:

- Die Laufzeit gleicht den Schaltflächenzustand in jedem Frame mit der GLFW-Abfrage ab, um dauerhaft als gedrückt erkannte Schaltflächen zu verhindern.

Wenn `Pass Input Events To Shader` deaktiviert ist:

- werden Eingabe-Uniforms in jedem Frame auf neutrale Werte zurückgesetzt
- werden Zähler und Ereignisse in den für Shader sichtbaren Daten auf null gesetzt

## 8. Details zu Textureingaben

Ressourcenkanäle (`iChannel# Resource`) erwarten 2D-Texturen.

Texturstatus pro Kanal:

- gültige Ressource: gebundene Textur, tatsächliche Breite/Höhe, `iChannelResolution[n].z = 1.0`
- fehlend/inaktiv/None: Fallback-Textur, `iChannelResolution[n].xyz = (0,0,0)`

Buffer-Texturen:

- internes Format: `RGBA16F` (Fließkomma)
- Filterung: linear
- Wrap-Modus: Clamp-to-Edge

Das eignet sich für Multipass-Daten, einschließlich Werten außerhalb von `[0,1]`.

## 9. Hinweise zu Rendering und Blending

- Buffer-Pässe werden ohne Blending außerhalb des Bildschirms gerendert.
- Für das Compositing im abschließenden Image-Pass wird die Einstellung `Enable Blending` verwendet.
- Der Shadertoy-Wrapper wendet `fmOpacity` automatisch auf die Alpha-Komponente an.
- Direct-Shader sollten `fmOpacity` bei Bedarf manuell anwenden.

## 10. Praktische Vorlagen

## 10.1 Minimaler Shader im Shadertoy-Stil

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

## 10.3 Minimales Multipass-Feedback

### Quelltext für Buffer A

Routing: `Buffer A iChannel0 Input -> Buffer A`

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord) {
    vec2 uv = fragCoord / iResolution.xy;
    vec4 prev = texture(iChannel0, uv);
    vec4 seed = vec4(uv, 0.0, 1.0);
    fragColor = mix(prev, seed, 0.02);
}
```

### Image-Quelltext

Routing: `Image iChannel0 Input -> Buffer A`

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord) {
    vec2 uv = fragCoord / iResolution.xy;
    fragColor = texture(iChannel0, uv);
}
```

## 11. Checkliste zur Fehlerbehebung

- Keine Ausgabe:
  - Prüfe, ob der Image-Quelltext nicht leer ist.
  - Prüfe, ob der Kompilierungsmodus zum Einstiegspunkt passt (`mainImage` oder `main`).
- Violette/ungültige Texturen:
  - Prüfe die Ressourcenbindungen und das Kanal-Routing.
  - Prüfe `iChannelResolution[n].z` (`0.0` bedeutet ungültig/nicht verfügbar).
- Falsche Koordinaten im Direct-Shader:
  - Verwende `gl_FragCoord.xy - fmAreaOffset` für lokale Bereichskoordinaten.
- Falsches Verhalten beim Ziehen:
  - Verwende die Umschaltoption `Update iMouse Position Only While Holding LMB`.
- Deckkraft wird im Direct-Shader nicht angewendet:
  - Multipliziere die Alpha-Komponente selbst mit `fmOpacity`.
