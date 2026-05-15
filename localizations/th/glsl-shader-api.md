---
title: GLSL Shader API
description: >-
  เขียนเชดเดอร์ GLSL สุดล้ำสำหรับ FancyMenu สำหรับพื้นหลัง องค์ประกอบ
  และโอเวอร์เลย์ตกแต่ง
---

# FancyMenu GLSL Shader API

เอกสารนี้อธิบายรันไทม์ GLSL ที่ FancyMenu ใช้สำหรับ:

- พื้นหลังเมนู `GLSL`
- องค์ประกอบ `GLSL`
- โอเวอร์เลย์ตกแต่ง `GLSL`

ครอบคลุมโหมดการคอมไพล์ การทำงานแบบหลายพาส ยูนิฟอร์มที่รองรับ และรูปแบบการเขียนเชดเดอร์ที่ใช้งานได้จริง

## 1. ภาพรวมรันไทม์

FancyMenu เรนเดอร์เชดเดอร์ด้วยไปป์ไลน์ OpenGL ภายใน (`#version 150`) และรองรับ:

- เชดเดอร์แบบพาสเดียว (`Image` pass เท่านั้น)
- เชดเดอร์แบบหลายพาส (`Buffer A` / `B` / `C` / `D` + `Image`)
- จุดเริ่มต้นสไตล์ Shadertoy (`mainImage`)
- จุดเริ่มต้นแบบ fragment โดยตรง (`main`)

ซอร์สเชดเดอร์เป็นฟิลด์ข้อความแบบ inline:

- `Shader Source` (พาส Image, จำเป็นต่อการแสดงผล)
- `Buffer A Source` (ไม่บังคับ)
- `Buffer B Source` (ไม่บังคับ)
- `Buffer C Source` (ไม่บังคับ)
- `Buffer D Source` (ไม่บังคับ)

หากซอร์สของ Image ว่าง การเรนเดอร์จะล้มเหลวด้วยข้อผิดพลาด "no source"

## 2. โหมดการคอมไพล์

FancyMenu รองรับ 3 โหมดการคอมไพล์:

- `Auto`
- `Direct Fragment`
- `Shadertoy`

### 2.1 โหมด Shadertoy

จุดเริ่มต้นที่คาดไว้:

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord)
```

FancyMenu จะห่อมันเป็น `main()` และส่งพิกัดของพื้นที่ภายใน:

```glsl
mainImage(fmColor_FancyMenu, gl_FragCoord.xy - fmAreaOffset);
```

ตัวห่อจะคูณค่า alpha ของผลลัพธ์ด้วย `fmOpacity`

### 2.2 โหมด Direct

จุดเริ่มต้นที่คาดไว้:

```glsl
void main()
```

พฤติกรรมความเข้ากันได้:

- จะลองใช้ตัวแปรความเข้ากันได้แบบ `gl_FragColor`
- และจะลองแบบไม่ใช้ compatibility ด้วย (สำหรับเชดเดอร์สมัยใหม่ที่ประกาศ `out vec4` ชัดเจน)

ในโหมด direct, `fmOpacity` จะไม่ถูกนำไปใช้กับผลลัพธ์ของคุณโดยอัตโนมัติ หากต้องการให้ใช้ ให้คูณเอง

### 2.3 โหมด Auto

Auto จะลองเวอร์ชันที่เข้ากันได้ตามลำดับ (Shadertoy/direct) และใช้ตัวแรกที่คอมไพล์ผ่าน

## 3. การประมวลผลซอร์สและมาโครในตัว

ก่อนคอมไพล์ FancyMenu จะปรับซอร์สให้เป็นมาตรฐาน:

- ลบ UTF-8 BOM
- แปลง CRLF/CR เป็น LF
- ลบบรรทัด `#version ...`
- ลบบรรทัด `precision ...;`

ส่วนหัวที่ระบบฉีดเข้าไปขณะรันไทม์ประกอบด้วย:

- `#version 150`
- `in vec2 fmUv_FancyMenu` (UV เต็มจอในช่วง `[0,1]`, จุดกำเนิดอยู่มุมล่างซ้าย)
- `#define iGlobalTime iTime`
- `#define texture2D texture`
- `#define textureCube texture`

หมายเหตุ:

- หากซอร์สของคุณประกาศชื่อยูนิฟอร์มที่รู้จักอยู่แล้ว (เช่น `iTime`) FancyMenu จะหลีกเลี่ยงการฉีดประกาศซ้ำ
- FancyMenu ยังพยายามอัปโหลดค่าลงชื่อนั้นขณะรันไทม์
- `textureCube` ที่นี่เป็นเพียงมาโคร alias; `iChannel0..3` เป็นยูนิฟอร์ม `sampler2D`

## 4. ระบบพาส (Image + Buffer A-D)

FancyMenu มีช่องพาส 5 ช่อง:

- `Buffer A`
- `Buffer B`
- `Buffer C`
- `Buffer D`
- `Image` (พาสสุดท้ายบนหน้าจอ)

พฤติกรรม:

- พาสของ Buffer จะทำงานก็ต่อเมื่อซอร์สของมันไม่ว่าง
- พาส Image ต้องมีอยู่เพื่อให้แสดงผลลัพธ์
- Buffer จะถูกเรนเดอร์ลงเท็กซ์เจอร์แบบ floating-point (`GL_RGBA16F`) แล้วทำ ping-pong (สลับอ่าน/เขียนทุกเฟรม)

### 4.1 การกำหนดเส้นทางช่องของแต่ละพาส

แต่ละพาสเปิดให้กำหนดเส้นทางสำหรับ `iChannel0..3` ได้ ต่อหนึ่งช่องเลือกได้จาก:

- `None`
- `Resource 0`
- `Resource 1`
- `Resource 2`
- `Resource 3`
- `Buffer A`
- `Buffer B`
- `Buffer C`
- `Buffer D`

ช่อง Resource มาจากการตั้งค่า `iChannel# Resource`

ค่าเริ่มต้น:

- การกำหนดเส้นทาง `iChannel` ทุกช่องเริ่มที่ `None`
- ไม่มีพาส Buffer ใดทำงานจนกว่าซอร์สของบัฟเฟอร์นั้นจะไม่ว่าง

สำคัญ:

- การกำหนดเส้นทางไปยังพาสบัฟเฟอร์เดียวกัน (feedback) จะอ่านข้อมูลจากเฟรมก่อนหน้า (เท็กซ์เจอร์อ่านแบบ ping-pong)
- หากแหล่งที่ถูกกำหนดเส้นทางหายไป/ไม่ทำงาน จะผูก fallback texture แทน และ `iChannelResolution[n].z` จะเป็น `0.0`

## 5. ความหมายของพิกัดและพื้นที่

เชดเดอร์ทำงานภายในพื้นที่สี่เหลี่ยม:

- พื้นหลังเมนู: พื้นที่เต็มหน้าจอ
- องค์ประกอบ GLSL: พื้นที่สี่เหลี่ยมขององค์ประกอบ

รูปแบบพิกัด:

- ยูนิฟอร์มพิกเซลเป็นพิกเซลแบบ local ของพื้นที่
- จุดกำเนิดแกน Y อยู่มุมล่างซ้ายสำหรับพิกเซลที่ส่งให้เชดเดอร์
- พิกัดเมาส์ไม่ถูกจำกัดค่า; ค่าจะอยู่นอกพื้นที่ได้หากเคอร์เซอร์อยู่นอกพื้นที่

ฟิลด์พิเศษ:

- `fmAreaOffset`: ตำแหน่งมุมล่างซ้ายของพื้นที่ในพิกัดพิกเซลของหน้าจอ
- `fmAreaTopLeft`: ตำแหน่งมุมบนซ้ายของพื้นที่ในพิกัดพิกเซลของหน้าจอ
- `fmAreaSize`: ขนาดพื้นที่เป็นพิกเซล

## 6. เอกสารอ้างอิง API ของยูนิฟอร์ม

ยูนิฟอร์มทั้งหมดด้านล่างพร้อมใช้งานทั้งสำหรับเชดเดอร์พื้นหลังและเชดเดอร์องค์ประกอบ

## 6.1 ยูนิฟอร์มที่เข้ากันได้กับ Shadertoy

| Uniform | Type | ความหมาย |
|---|---|---|
| `iResolution` | `vec3` | `(areaWidthPx, areaHeightPx, 1.0)` |
| `iTime` | `float` | เวลาเชดเดอร์สะสม หน่วยวินาที |
| `iTimeDelta` | `float` | เดลตาไทม์ของการเรนเดอร์ครั้งล่าสุด ได้รับผลจากการ freeze/time scale |
| `iFrameRate` | `float` | FPS fallback ของ runtime เทียบกับ Minecraft FPS |
| `iFrame` | `int` | ตัวนับเฟรมของรันไทม์นั้น |
| `iMouse` | `vec4` | ดูรายละเอียดด้านล่าง |
| `iDate` | `vec4` | `(year, month, day, secondsOfDayWithFraction)` |
| `iSampleRate` | `float` | ค่าคงที่ `44100.0` |
| `iChannelTime[4]` | `float[4]` | ปัจจุบันตั้งค่าเป็น `iTime` ทั้งหมด |
| `iChannelResolution[4]` | `vec3[4]` | `(width, height, validFlag)` ต่อหนึ่งช่อง |
| `iChannel0..3` | `sampler2D` | อินพุตเท็กซ์เจอร์ที่ถูกกำหนดเส้นทาง |

### รายละเอียด `iMouse`

`iMouse = vec4(x, y, z, w)`

- `x`, `y`: ตำแหน่งเมาส์แบบพิกเซลภายในพื้นที่ปัจจุบัน หรือพฤติกรรมแบบค้าง/หยุดตาม toggle หากเปิดใช้งาน
- `z`, `w`: จุดเริ่มต้นของการคลิกซ้าย
  - เป็นค่าบวกขณะกดปุ่มเมาส์ซ้ายค้างอยู่
  - เป็นค่าลบหลังปล่อย

พฤติกรรมที่ควบคุมด้วย toggle:

- `Update iMouse Position Only While Holding LMB = Off`:
  - `iMouse.xy` อัปเดตต่อเนื่อง
- `... = On`:
  - `iMouse.xy` อัปเดตเฉพาะตอนกด LMB ค้าง แล้วจะค้างอยู่ที่ตำแหน่งล่าสุดตอนกด

ค่าเริ่มต้น:

- `Off` (อัปเดตต่อเนื่อง)

## 6.2 ยูนิฟอร์มเฉพาะของ FancyMenu

| Uniform | Type | ความหมาย |
|---|---|---|
| `fmAreaOffset` | `vec2` | ออฟเซ็ตพิกเซลมุมล่างซ้ายของพื้นที่ในพิกัดหน้าจอ |
| `fmAreaSize` | `vec2` | ขนาดพื้นที่เป็นพิกเซล |
| `fmAreaPosition` | `vec2` | เหมือน `fmAreaOffset` |
| `fmAreaTopLeft` | `vec2` | ออฟเซ็ตพิกเซลมุมบนซ้ายของพื้นที่ในพิกัดหน้าจอ |
| `fmScreenSize` | `vec2` | ขนาดหน้าจอเต็มเป็นพิกเซล |
| `fmGuiScale` | `float` | สเกล GUI ปัจจุบัน |
| `fmMouse` | `vec4` | `(localPxX, localPxYBottom, localNormX, localNormY)` |
| `fmMouseDelta` | `vec2` | เดลตาเมาส์ในพิกเซลของพื้นที่ (แกน Y ถูกกลับให้เป็นทิศขึ้นของเชดเดอร์) |
| `fmMouseButtons` | `ivec4` | สถานะกดค้างของปุ่ม `0..3` |
| `fmMouseClickCount` | `ivec4` | จำนวนครั้งที่กดสะสมของปุ่ม `0..3` |
| `fmMouseReleaseCount` | `ivec4` | จำนวนครั้งที่ปล่อยสะสมของปุ่ม `0..3` |
| `fmMouseScroll` | `vec2` | เดลตาสกรอลจากการเรนเดอร์ครั้งก่อนของรันไทม์นี้ |
| `fmMouseScrollTotal` | `vec2` | ค่าสกรอลสะสมทั้งหมด |
| `fmKeyEvent` | `ivec4` | `(lastKeyCode, lastScanCode, lastModifiers, lastAction)` |
| `fmKeyEventCount` | `int` | ตัวนับอีเวนต์คีย์สะสม |
| `fmCharEvent` | `ivec4` | `(lastCodePoint, lastModifiers, 0, 0)` |
| `fmCharEventCount` | `int` | ตัวนับอีเวนต์ตัวอักษรที่พิมพ์สะสม |
| `fmDateParts` | `ivec4` | `(year, month, day, dayOfWeekIso1To7)` |
| `fmTimeParts` | `ivec4` | `(hour, minute, second, millisecondPart0To999)` |
| `fmDayOfYear` | `int` | วันลำดับที่ของปี |
| `fmWeekOfYear` | `int` | สัปดาห์แบบ ISO ของปี |
| `fmUnixTimeSeconds` | `int` | วินาทีตาม Unix epoch |
| `fmUnixTimeMilliseconds` | `int` | ส่วนมิลลิวินาทีของเวลาปัจจุบัน (`0..999`) |
| `fmPartialTick` | `float` | partial tick ปัจจุบัน |
| `fmGameDeltaTicks` | `float` | game delta ticks ของ Minecraft |
| `fmRealtimeDeltaTicks` | `float` | realtime delta ticks ของ Minecraft |
| `fmInWorld` | `int` | `1` เมื่ออยู่ในโลกเกม มิฉะนั้น `0` |
| `fmIsPaused` | `int` | `1` เมื่อเกมหยุดชั่วคราว มิฉะนั้น `0` |
| `fmOpacity` | `float` | ตัวคูณความทึบที่มีผลจริง (`0..1`) |
| `fmVariableCount` | `int` | จำนวนตัวแปร FancyMenu ปัจจุบัน |

ค่าการกระทำของคีย์ (`fmKeyEvent.w`):

- `0` = ปล่อย
- `1` = กด
- `2` = กดซ้ำ

## 6.3 API ยูนิฟอร์มตัวแปรของ FancyMenu

ตัวแปรของ FancyMenu ถูกเปิดเผยโดยตรงเป็นยูนิฟอร์มขณะรันไทม์ (สำหรับเชดเดอร์พื้นหลัง องค์ประกอบ และโอเวอร์เลย์ตกแต่ง) โดยไม่ต้องคอมไพล์เชดเดอร์ใหม่เมื่อค่ามีการเปลี่ยน

### การตั้งชื่อ

สำหรับตัวแปรแต่ละตัว `<name>`, FancyMenu จะเปิดเผย:

- `fmVarFloat_<name>`
- `fmVarInt_<name>`
- `fmVarBool_<name>`
- `fmVarVec2_<name>`
- `fmVarVec3_<name>`
- `fmVarVec4_<name>`
- `fmVarExists_<name>` (`1` = ตัวแปรมีอยู่ในตอนนี้, `0` = ไม่มี/ถูกลบ)

การทำความสะอาด suffix ของยูนิฟอร์มสำหรับ `<name>`:

- อักขระที่อนุญาตคือ `[A-Za-z0-9_]`
- อักขระอื่นทั้งหมดจะถูกแปลงเป็น `_`
- หากอักขระตัวแรกเป็นตัวเลข จะเติม `_` นำหน้า

ตัวอย่าง:

- ตัวแปร `player_hp` -> suffix `player_hp`
- ตัวแปร `player-hp` -> suffix `player_hp`
- ตัวแปร `2nd_phase` -> suffix `_2nd_phase`

สำคัญ:

- ยูนิฟอร์มตัวแปรแบบไดนามิกเหล่านี้ **จะไม่ถูกประกาศให้อัตโนมัติ** ในซอร์สเชดเดอร์ (ให้ประกาศตัวที่ใช้งานเองด้วยมือ)
- หลีกเลี่ยงชื่อตัวแปรที่ถูกทำความสะอาดแล้วกลายเป็น suffix เดียวกัน เพราะจะ map ไปยังชื่อยูนิฟอร์ม GLSL เดียวกัน

### การแปลงค่า

เมื่อมีค่าข้อความของตัวแปร `v`:

- `fmVarFloat_*`: แปลงเป็น float (`0.0` ถ้าใช้ไม่ได้)
- `fmVarInt_*`: แปลงเป็น int (`0` ถ้าใช้ไม่ได้)
- `fmVarBool_*`: ตีความแบบ boolean/int (`true/yes/on/enabled` => `1`, `false/no/off/disabled` => `0`, อื่น ๆ ถ้าเป็นตัวเลขที่ไม่เป็นศูนย์ => `1`)
- การแปลงเวกเตอร์ยอมรับตัวคั่น: ช่องว่าง, `,`, `;`, `|`
  - `fmVarVec2_*`: ใช้ 2 ค่าที่แปลงได้แรก
  - `fmVarVec3_*`: ใช้ 3 ค่าที่แปลงได้แรก
  - `fmVarVec4_*`: ใช้ 4 ค่าที่แปลงได้แรก
  - หากมีค่าน้อยกว่านั้น จะใช้ค่าที่แปลงได้ล่าสุดซ้ำในช่องที่ขาด
  - หากไม่มีค่าตัวเลขเลย จะใช้ค่า fallback แบบ scalar สำหรับทุกองค์ประกอบของเวกเตอร์

หากตัวแปรถูกลบออก:

- `fmVarExists_*` จะกลายเป็น `0`
- ค่าของ `fmVar*_*` ที่เกี่ยวข้องทั้งหมดจะถูกรีเซ็ตเป็น `0`

### ตัวอย่างการประกาศและการใช้งาน

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

## 7. โมเดลการติดตามอินพุต

FancyMenu ติดตามอินพุตแบบทั่วโลกและเก็บภาพรวมสถานะของมันในแต่ละการเรนเดอร์:

- การเคลื่อนที่/ลากเมาส์
- กด/ปล่อยเมาส์
- สกรอล
- กด/ปล่อย/กดซ้ำคีย์
- พิมพ์ตัวอักษร

ความทนทานของเมาส์:

- รันไทม์จะตรวจสอบสถานะปุ่มกับการ polling ของ GLFW ทุกเฟรม เพื่อป้องกันสถานะปุ่มค้าง

หาก `Pass Input Events To Shader` ถูกปิด:

- ยูนิฟอร์มอินพุตจะถูกรีเซ็ตเป็นค่าเป็นกลางทุกเฟรม
- ตัวนับและอีเวนต์จะถูกตั้งเป็นศูนย์ในข้อมูลที่เชดเดอร์มองเห็น

## 8. รายละเอียดอินพุตเท็กซ์เจอร์

ช่อง Resource (`iChannel# Resource`) คาดหวังเท็กซ์เจอร์แบบ 2D

สถานะเท็กซ์เจอร์ต่อช่อง:

- resource ที่ใช้ได้: ผูกเท็กซ์เจอร์จริง, ความกว้าง/สูงจริง, `iChannelResolution[n].z = 1.0`
- ไม่มี/ไม่ทำงาน/None: fallback texture, `iChannelResolution[n].xyz = (0,0,0)`

เท็กซ์เจอร์ของ Buffer:

- internal format: `RGBA16F` (floating point)
- filtering: linear
- wrap: clamp-to-edge

เหมาะสำหรับข้อมูลแบบหลายพาส (รวมถึงค่าที่อยู่นอกช่วง `[0,1]`)

## 9. หมายเหตุเกี่ยวกับการเรนเดอร์และการผสมภาพ

- พาส Buffer เรนเดอร์นอกหน้าจอโดยไม่มี blending
- พาส Image สุดท้ายใช้การตั้งค่า `Enable Blending` สำหรับการประกอบภาพ
- ตัวห่อแบบ Shadertoy จะใช้ `fmOpacity` กับ alpha อัตโนมัติ
- เชดเดอร์แบบ direct ควรใช้ `fmOpacity` ด้วยตัวเองหากจำเป็น

## 10. เทมเพลตใช้งานจริง

## 10.1 เชดเดอร์สไตล์ Shadertoy แบบขั้นต่ำ

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord) {
    vec2 uv = fragCoord / iResolution.xy;
    vec3 col = vec3(uv, 0.5 + 0.5 * sin(iTime));
    fragColor = vec4(col, 1.0);
}
```

## 10.2 เชดเดอร์ fragment แบบ direct ขั้นต่ำ

```glsl
out vec4 FragColor;

void main() {
    vec2 uv = gl_FragCoord.xy - fmAreaOffset;
    uv /= iResolution.xy;

    vec3 col = vec3(uv.x, uv.y, 0.5 + 0.5 * sin(iTime));
    FragColor = vec4(col, fmOpacity);
}
```

## 10.3 Multipass แบบ feedback ขั้นต่ำ

### ซอร์ส Buffer A

Route: `Buffer A iChannel0 Input -> Buffer A`

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord) {
    vec2 uv = fragCoord / iResolution.xy;
    vec4 prev = texture(iChannel0, uv);
    vec4 seed = vec4(uv, 0.0, 1.0);
    fragColor = mix(prev, seed, 0.02);
}
```

### ซอร์ส Image

Route: `Image iChannel0 Input -> Buffer A`

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord) {
    vec2 uv = fragCoord / iResolution.xy;
    fragColor = texture(iChannel0, uv);
}
```

## 11. รายการตรวจสอบการแก้ปัญหา

- ไม่มีผลลัพธ์:
  - ตรวจสอบว่า Image source ไม่ว่าง
  - ตรวจสอบว่า compile mode ตรงกับ entry point ของคุณ (`mainImage` vs `main`)
- เท็กซ์เจอร์สีม่วง/ไม่ถูกต้อง:
  - ตรวจสอบการผูก resource และการกำหนดเส้นทางช่อง
  - ตรวจสอบ `iChannelResolution[n].z` (`0.0` หมายถึงไม่ถูกต้อง/ไม่พร้อมใช้งาน)
- พิกัดผิดใน direct shader:
  - ใช้ `gl_FragCoord.xy - fmAreaOffset` สำหรับพิกัดพื้นที่แบบ local
- พฤติกรรมการลากไม่ถูกต้อง:
  - ใช้ toggle `Update iMouse Position Only While Holding LMB`
- ความทึบไม่ถูกใช้ใน direct shader:
  - คูณ alpha ด้วย `fmOpacity` เอง
