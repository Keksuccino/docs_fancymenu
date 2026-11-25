---
title: GLSL Shader API
description: >-
  เขียนเชเดอร์ GLSL สำหรับ FancyMenu เพื่อใช้กับพื้นหลัง องค์ประกอบ
  และโอเวอร์เลย์ตกแต่ง
sourceBlobSha: f3da9c3fe83444dab5c59f74f5011e2d6e8cf9e6
---

# GLSL Shader API ของ FancyMenu

เอกสารนี้อธิบายรันไทม์ GLSL ที่ FancyMenu ใช้กับ:

- พื้นหลังเมนู `GLSL`
- องค์ประกอบ `GLSL`
- โอเวอร์เลย์ตกแต่ง `GLSL`

เนื้อหาครอบคลุมโหมดคอมไพล์ การกำหนดเส้นทางแบบหลายพาส ยูนิฟอร์มที่รองรับ และแนวทางเขียนเชเดอร์ที่นำไปใช้ได้จริง

## 1. ภาพรวมรันไทม์

FancyMenu เรนเดอร์เชเดอร์ด้วยไปป์ไลน์ OpenGL ภายใน (`#version 150`) และรองรับ:

- เชเดอร์แบบพาสเดียว (ใช้เฉพาะพาส `Image`)
- เชเดอร์แบบหลายพาส (`Buffer A` / `B` / `C` / `D` + `Image`)
- จุดเริ่มต้นแบบ Shadertoy (`mainImage`)
- จุดเริ่มต้นของ fragment shader โดยตรง (`main`)

ซอร์สเชเดอร์เป็นช่องข้อความแบบอินไลน์:

- `Shader Source` (พาส Image จำเป็นสำหรับการเรนเดอร์)
- `Buffer A Source` (ไม่บังคับ)
- `Buffer B Source` (ไม่บังคับ)
- `Buffer C Source` (ไม่บังคับ)
- `Buffer D Source` (ไม่บังคับ)

หากซอร์ส Image ว่างเปล่า การเรนเดอร์จะล้มเหลวโดยแสดงข้อผิดพลาด "no source"

## 2. โหมดคอมไพล์

FancyMenu รองรับโหมดคอมไพล์สามแบบ:

- `Auto`
- `Direct Fragment`
- `Shadertoy`

### 2.1 โหมด Shadertoy

จุดเริ่มต้นที่คาดไว้:

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord)
```

FancyMenu จะห่อโค้ดนี้ไว้ใน `main()` และส่งพิกัดเฉพาะที่ของพื้นที่ให้:

```glsl
mainImage(fmColor_FancyMenu, gl_FragCoord.xy - fmAreaOffset);
```

ตัวห่อจะคูณค่าแอลฟาของเอาต์พุตด้วย `fmOpacity`

### 2.2 โหมด Direct

จุดเริ่มต้นที่คาดไว้:

```glsl
void main()
```

พฤติกรรมด้านความเข้ากันได้:

- จะลองใช้รูปแบบที่เข้ากันได้กับ `gl_FragColor`
- จะลองใช้รูปแบบที่ไม่มี compatibility ด้วย (สำหรับเชเดอร์สมัยใหม่ที่ประกาศ `out vec4` อย่างชัดเจน)

ในโหมด Direct ระบบจะไม่ใส่ `fmOpacity` ให้เอาต์พุตของคุณโดยอัตโนมัติ หากจำเป็น ให้ปรับใช้ด้วยตนเอง

### 2.3 โหมด Auto

Auto จะลองใช้รูปแบบที่เข้ากันได้ตามลำดับ (Shadertoy/Direct) และเลือกรูปแบบแรกที่คอมไพล์สำเร็จ

## 3. การประมวลผลซอร์สล่วงหน้าและมาโครที่มีมาให้

ก่อนคอมไพล์ FancyMenu จะปรับรูปแบบซอร์สให้เป็นมาตรฐาน:

- ลบ UTF-8 BOM
- แปลง CRLF/CR เป็น LF
- ลบบรรทัด `#version ...`
- ลบบรรทัด `precision ...;`

ส่วนหัวที่รันไทม์แทรกให้ประกอบด้วย:

- `#version 150`
- `in vec2 fmUv_FancyMenu` (UV แบบเต็มหน้าจอในช่วง `[0,1]` โดยมีจุดกำเนิดที่มุมล่างซ้าย)
- `#define iGlobalTime iTime`
- `#define texture2D texture`
- `#define textureCube texture`

หมายเหตุ:

- หากซอร์สของคุณประกาศชื่อยูนิฟอร์มที่รู้จักอยู่แล้ว (เช่น `iTime`) FancyMenu จะไม่แทรกประกาศชื่อซ้ำ
- FancyMenu จะยังคงพยายามอัปโหลดค่าไปยังชื่อนั้นขณะรันไทม์
- `textureCube` เป็นเพียงมาโคร alias ในที่นี้ ส่วน `iChannel0..3` เป็นยูนิฟอร์ม `sampler2D`

## 4. ระบบพาส (Image + Buffer A-D)

FancyMenu มีช่องพาสทั้งหมด 5 ช่อง:

- `Buffer A`
- `Buffer B`
- `Buffer C`
- `Buffer D`
- `Image` (พาสสุดท้ายที่แสดงบนหน้าจอ)

พฤติกรรม:

- พาส Buffer จะทำงานก็ต่อเมื่อมีซอร์สที่ไม่ว่างเปล่า
- ต้องมีพาส Image จึงจะแสดงผลลัพธ์ได้
- Buffer จะเรนเดอร์ลงในเท็กซ์เจอร์ชนิด floating-point (`GL_RGBA16F`) จากนั้นจะสลับ ping-pong (สลับเท็กซ์เจอร์อ่าน/เขียนในแต่ละเฟรม)

### 4.1 การกำหนดเส้นทางแชนเนลในแต่ละพาส

แต่ละพาสสามารถกำหนดเส้นทางให้ `iChannel0..3` ได้ โดยแต่ละแชนเนลเลือกได้จาก:

- `None`
- `Resource 0`
- `Resource 1`
- `Resource 2`
- `Resource 3`
- `Buffer A`
- `Buffer B`
- `Buffer C`
- `Buffer D`

แชนเนล Resource จะดึงข้อมูลจากการตั้งค่า `iChannel# Resource`

ค่าเริ่มต้น:

- การกำหนดเส้นทาง `iChannel` ทั้งหมดตั้งต้นเป็น `None`
- ไม่มีพาส Buffer ทำงานจนกว่าซอร์สของ Buffer นั้นจะไม่ว่างเปล่า

ข้อสำคัญ:

- หากกำหนดเส้นทางกลับไปยังพาส Buffer เดียวกัน (feedback) ระบบจะอ่านข้อมูลจากเฟรมก่อนหน้า (เท็กซ์เจอร์อ่านของ ping-pong)
- หากแหล่งข้อมูลที่กำหนดเส้นทางไว้ไม่มีอยู่หรือไม่ได้ทำงาน ระบบจะผูกเท็กซ์เจอร์สำรอง และ `iChannelResolution[n].z` จะมีค่าเป็น `0.0`

## 5. พิกัดและความหมายของพื้นที่

เชเดอร์ทำงานภายในกรอบพื้นที่:

- พื้นหลังเมนู: พื้นที่เต็มหน้าจอ
- องค์ประกอบ GLSL: กรอบขององค์ประกอบ

รูปแบบพิกัด:

- ยูนิฟอร์มพิกเซลใช้หน่วยพิกเซลเฉพาะที่ของพื้นที่
- จุดกำเนิดแกน Y สำหรับพิกัดพิกเซลที่ส่งให้เชเดอร์อยู่ที่มุมล่างซ้าย
- พิกัดเมาส์ไม่มีการจำกัดค่า หากเคอร์เซอร์อยู่นอกพื้นที่ ค่าก็อาจอยู่นอกพื้นที่ได้

ฟิลด์พิเศษ:

- `fmAreaOffset`: ตำแหน่งมุมล่างซ้ายของพื้นที่ในพิกัดพิกเซลหน้าจอ
- `fmAreaTopLeft`: ตำแหน่งมุมซ้ายบนของพื้นที่ในพิกัดพิกเซลหน้าจอ
- `fmAreaSize`: ขนาดของพื้นที่เป็นพิกเซล

## 6. ข้อมูลอ้างอิง Uniform API

ยูนิฟอร์มทั้งหมดด้านล่างใช้ได้กับทั้งเชเดอร์พื้นหลังและเชเดอร์องค์ประกอบ

## 6.1 ยูนิฟอร์มที่เข้ากันได้กับ Shadertoy

| Uniform | Type | ความหมาย |
|---|---|---|
| `iResolution` | `vec3` | `(areaWidthPx, areaHeightPx, 1.0)` |
| `iTime` | `float` | เวลาสะสมของเชเดอร์ หน่วยเป็นวินาที |
| `iTimeDelta` | `float` | เวลาที่ผ่านไปนับจากการเรนเดอร์ครั้งล่าสุด ซึ่งได้รับผลจากการหยุดและสเกลเวลา |
| `iFrameRate` | `float` | FPS ขณะรัน โดยใช้ Minecraft FPS เป็นค่าสำรอง |
| `iFrame` | `int` | ตัวนับเฟรมของรันไทม์ |
| `iMouse` | `vec4` | ดูรายละเอียดด้านล่าง |
| `iDate` | `vec4` | `(year, month, day, secondsOfDayWithFraction)` |
| `iSampleRate` | `float` | ค่าคงที่ `44100.0` |
| `iChannelTime[4]` | `float[4]` | ปัจจุบันทุกค่าเท่ากับ `iTime` |
| `iChannelResolution[4]` | `vec3[4]` | `(width, height, validFlag)` ของแต่ละแชนเนล |
| `iChannel0..3` | `sampler2D` | อินพุตเท็กซ์เจอร์ตามเส้นทางที่กำหนด |

### รายละเอียด `iMouse`

`iMouse = vec4(x, y, z, w)`

- `x`, `y`: ตำแหน่งพิกเซลของเมาส์ปัจจุบันในพิกัดเฉพาะที่ของพื้นที่ หรือเป็นพฤติกรรมแบบค้าง/หยุดนิ่งหากเปิดตัวเลือกไว้
- `z`, `w`: จุดเริ่มต้นของการคลิกเมาส์ซ้าย
  - เป็นค่าบวกขณะกดปุ่มเมาส์ซ้ายค้างไว้
  - เป็นค่าลบหลังปล่อยปุ่ม

พฤติกรรมที่ควบคุมด้วยตัวเลือก:

- `Update iMouse Position Only While Holding LMB = Off`:
  - `iMouse.xy` อัปเดตอย่างต่อเนื่อง
- `... = On`:
  - `iMouse.xy` อัปเดตเฉพาะขณะที่กด LMB และจะค้างที่ตำแหน่งล่าสุดตอนกดไว้หลังจากปล่อยปุ่ม

ค่าเริ่มต้น:

- `Off` (อัปเดตอย่างต่อเนื่อง)

## 6.2 ยูนิฟอร์มเฉพาะของ FancyMenu

| Uniform | Type | ความหมาย |
|---|---|---|
| `fmAreaOffset` | `vec2` | ออฟเซ็ตพิกเซลของมุมล่างซ้ายของพื้นที่ในพิกัดหน้าจอ |
| `fmAreaSize` | `vec2` | ขนาดของพื้นที่เป็นพิกเซล |
| `fmAreaPosition` | `vec2` | ค่าเดียวกับ `fmAreaOffset` |
| `fmAreaTopLeft` | `vec2` | ออฟเซ็ตพิกเซลของมุมซ้ายบนของพื้นที่ในพิกัดหน้าจอ |
| `fmScreenSize` | `vec2` | ขนาดเต็มหน้าจอเป็นพิกเซล |
| `fmGuiScale` | `float` | สเกล GUI ปัจจุบัน |
| `fmMouse` | `vec4` | `(localPxX, localPxYBottom, localNormX, localNormY)` |
| `fmMouseDelta` | `vec2` | การเปลี่ยนตำแหน่งเมาส์ในพิกเซลของพื้นที่ (แกน Y กลับทิศให้ชี้ขึ้นตามพิกัดของเชเดอร์) |
| `fmMouseButtons` | `ivec4` | สถานะการกดปุ่มสำหรับปุ่ม `0..3` |
| `fmMouseClickCount` | `ivec4` | จำนวนครั้งสะสมที่กดปุ่ม `0..3` |
| `fmMouseReleaseCount` | `ivec4` | จำนวนครั้งสะสมที่ปล่อยปุ่ม `0..3` |
| `fmMouseScroll` | `vec2` | การเปลี่ยนแปลงการเลื่อนนับจากการเรนเดอร์ครั้งก่อนของรันไทม์นี้ |
| `fmMouseScrollTotal` | `vec2` | ยอดรวมการเลื่อนสะสม |
| `fmKeyEvent` | `ivec4` | `(lastKeyCode, lastScanCode, lastModifiers, lastAction)` |
| `fmKeyEventCount` | `int` | ตัวนับเหตุการณ์คีย์สะสม |
| `fmCharEvent` | `ivec4` | `(lastCodePoint, lastModifiers, 0, 0)` |
| `fmCharEventCount` | `int` | ตัวนับเหตุการณ์พิมพ์อักขระสะสม |
| `fmDateParts` | `ivec4` | `(year, month, day, dayOfWeekIso1To7)` |
| `fmTimeParts` | `ivec4` | `(hour, minute, second, millisecondPart0To999)` |
| `fmDayOfYear` | `int` | วันที่ในรอบปี |
| `fmWeekOfYear` | `int` | สัปดาห์ ISO ในรอบปี |
| `fmUnixTimeSeconds` | `int` | วินาที Unix epoch |
| `fmUnixTimeMilliseconds` | `int` | ส่วนมิลลิวินาทีของเวลาปัจจุบัน (`0..999`) |
| `fmPartialTick` | `float` | partial tick ปัจจุบัน |
| `fmGameDeltaTicks` | `float` | game delta ticks ของ Minecraft |
| `fmRealtimeDeltaTicks` | `float` | realtime delta ticks ของ Minecraft |
| `fmInWorld` | `int` | เป็น `1` เมื่ออยู่ในโลก มิฉะนั้นเป็น `0` |
| `fmIsPaused` | `int` | เป็น `1` เมื่อหยุดชั่วคราว มิฉะนั้นเป็น `0` |
| `fmOpacity` | `float` | ตัวคูณความทึบแสงที่มีผลจริง (`0..1`) |
| `fmVariableCount` | `int` | จำนวนตัวแปร FancyMenu ปัจจุบัน |

ค่าการกระทำของคีย์ (`fmKeyEvent.w`):

- `0` = ปล่อยปุ่ม
- `1` = กดปุ่ม
- `2` = กดซ้ำ

## 6.3 Uniform API สำหรับตัวแปร FancyMenu

ตัวแปร FancyMenu จะเปิดให้ใช้งานโดยตรงเป็นยูนิฟอร์มขณะรันไทม์ (สำหรับเชเดอร์พื้นหลัง องค์ประกอบ และโอเวอร์เลย์ตกแต่ง) โดยไม่ต้องคอมไพล์เชเดอร์ใหม่เมื่อค่าเปลี่ยน

### การตั้งชื่อ

สำหรับตัวแปรแต่ละตัว `<name>` FancyMenu จะเปิดให้ใช้:

- `fmVarFloat_<name>`
- `fmVarInt_<name>`
- `fmVarBool_<name>`
- `fmVarVec2_<name>`
- `fmVarVec3_<name>`
- `fmVarVec4_<name>`
- `fmVarExists_<name>` (`1` = ตัวแปรยังมีอยู่, `0` = ไม่มี/ถูกนำออกแล้ว)

การปรับอักขระส่วนต่อท้ายของยูนิฟอร์ม `<name>` ให้ถูกต้อง:

- อักขระที่อนุญาตคือ `[A-Za-z0-9_]`
- อักขระอื่นทั้งหมดจะถูกแปลงเป็น `_`
- หากอักขระตัวแรกเป็นตัวเลข จะเติม `_` ไว้ข้างหน้า

ตัวอย่าง:

- ตัวแปร `player_hp` -> ส่วนต่อท้าย `player_hp`
- ตัวแปร `player-hp` -> ส่วนต่อท้าย `player_hp`
- ตัวแปร `2nd_phase` -> ส่วนต่อท้าย `_2nd_phase`

ข้อสำคัญ:

- ยูนิฟอร์มตัวแปรแบบไดนามิกเหล่านี้ **ไม่ได้ประกาศให้อัตโนมัติ** ในซอร์สเชเดอร์ (ให้ประกาศตัวที่ใช้ด้วยตนเอง)
- หลีกเลี่ยงชื่อตัวแปรที่เมื่อนำมาปรับแล้วได้ส่วนต่อท้ายเดียวกัน เพราะจะจับคู่กับชื่อยูนิฟอร์ม GLSL เดียวกัน

### การแปลงค่า

กำหนดให้ค่าข้อความของตัวแปรเป็น `v`:

- `fmVarFloat_*`: แปลงเป็น float (ใช้ค่า `0.0` หากแปลงไม่ได้)
- `fmVarInt_*`: แปลงเป็น int (ใช้ค่า `0` หากแปลงไม่ได้)
- `fmVarBool_*`: ตีความเป็น boolean/int (`true/yes/on/enabled` => `1`, `false/no/off/disabled` => `0`, กรณีอื่นค่าตัวเลขที่ไม่ใช่ศูนย์ => `1`)
- การแยกวิเคราะห์เวกเตอร์รองรับตัวคั่น ได้แก่ ช่องว่าง `,` `;` และ `|`
  - `fmVarVec2_*`: ใช้ 2 องค์ประกอบแรกที่แปลงได้
  - `fmVarVec3_*`: ใช้ 3 องค์ประกอบแรกที่แปลงได้
  - `fmVarVec4_*`: ใช้ 4 องค์ประกอบแรกที่แปลงได้
  - หากมีองค์ประกอบน้อยกว่าที่ต้องใช้ ระบบจะนำองค์ประกอบสุดท้ายที่แปลงได้มาใช้ซ้ำในตำแหน่งที่ขาด
  - หากไม่มีองค์ประกอบตัวเลขเลย ทุกองค์ประกอบของเวกเตอร์จะใช้ค่าสำรองแบบสเกลาร์

[ตัวแปรแบบรายการ](/variables#text-and-list-variables) จะส่งกลับจำนวนรายการแทนข้อความของตัวแปร:

- `fmVarFloat_*` และ `fmVarInt_*`: จำนวนรายการ เช่น `3` สำหรับรายการที่มี 3 รายการ
- `fmVarBool_*`: `1` หากรายการมีข้อมูล, `0` หากรายการว่าง
- `fmVarVec2_*`, `fmVarVec3_*` และ `fmVarVec4_*`: จำนวนรายการในทุกองค์ประกอบ

หากตัวแปรถูกนำออก:

- `fmVarExists_*` จะกลายเป็น `0`
- ค่า `fmVar*_*` ที่เกี่ยวข้องทั้งหมดจะถูกรีเซ็ตเป็น `0`

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

## 7. รูปแบบการติดตามอินพุต

FancyMenu ติดตามอินพุตทั่วทั้งระบบ แล้วบันทึกสถานะไว้สำหรับการเรนเดอร์แต่ละครั้ง:

- การเลื่อน/ลากเมาส์
- การกด/ปล่อยเมาส์
- การเลื่อนล้อเมาส์
- การกด/ปล่อย/กดซ้ำคีย์
- การพิมพ์อักขระ

ความทนทานของการติดตามเมาส์:

- รันไทม์จะตรวจสอบสถานะปุ่มกับการอ่านสถานะจาก GLFW ในแต่ละเฟรม เพื่อป้องกันปุ่มค้าง

หากปิด `Pass Input Events To Shader`:

- ยูนิฟอร์มอินพุตจะถูกรีเซ็ตเป็นค่ากลางในแต่ละเฟรม
- ตัวนับและเหตุการณ์จะถูกตั้งเป็นศูนย์ในข้อมูลที่เชเดอร์มองเห็น

## 8. รายละเอียดอินพุตเท็กซ์เจอร์

แชนเนล Resource (`iChannel# Resource`) ต้องใช้เท็กซ์เจอร์ 2D

สถานะเท็กซ์เจอร์ของแต่ละแชนเนล:

- Resource ถูกต้อง: ผูกเท็กซ์เจอร์พร้อมความกว้าง/สูงจริง และ `iChannelResolution[n].z = 1.0`
- ไม่มี/ไม่ได้ทำงาน/เป็น None: ใช้เท็กซ์เจอร์สำรอง และ `iChannelResolution[n].xyz = (0,0,0)`

เท็กซ์เจอร์ Buffer:

- รูปแบบภายใน: `RGBA16F` (floating point)
- การกรอง: linear
- การห่อขอบ: clamp-to-edge

เหมาะสำหรับข้อมูลแบบหลายพาส (รวมถึงค่าที่อยู่นอกช่วง `[0,1]`)

## 9. หมายเหตุเกี่ยวกับการเรนเดอร์และการผสมสี

- พาส Buffer จะเรนเดอร์นอกจอโดยไม่ผสมสี
- พาส Image สุดท้ายใช้การตั้งค่า `Enable Blending` เพื่อประกอบภาพ
- ตัวห่อ Shadertoy จะปรับแอลฟาด้วย `fmOpacity` ให้อัตโนมัติ
- เชเดอร์ Direct ควรปรับแอลฟาด้วย `fmOpacity` ด้วยตนเองหากจำเป็น

## 10. ตัวอย่างเทมเพลตที่นำไปใช้ได้จริง

## 10.1 เชเดอร์สไตล์ Shadertoy แบบขั้นต่ำ

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord) {
    vec2 uv = fragCoord / iResolution.xy;
    vec3 col = vec3(uv, 0.5 + 0.5 * sin(iTime));
    fragColor = vec4(col, 1.0);
}
```

## 10.2 Fragment shader แบบ Direct ขั้นต่ำ

```glsl
out vec4 FragColor;

void main() {
    vec2 uv = gl_FragCoord.xy - fmAreaOffset;
    uv /= iResolution.xy;

    vec3 col = vec3(uv.x, uv.y, 0.5 + 0.5 * sin(iTime));
    FragColor = vec4(col, fmOpacity);
}
```

## 10.3 การทำ feedback แบบหลายพาสขั้นพื้นฐาน

### ซอร์ส Buffer A

กำหนดเส้นทาง: `Buffer A iChannel0 Input -> Buffer A`

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord) {
    vec2 uv = fragCoord / iResolution.xy;
    vec4 prev = texture(iChannel0, uv);
    vec4 seed = vec4(uv, 0.0, 1.0);
    fragColor = mix(prev, seed, 0.02);
}
```

### ซอร์ส Image

กำหนดเส้นทาง: `Image iChannel0 Input -> Buffer A`

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord) {
    vec2 uv = fragCoord / iResolution.xy;
    fragColor = texture(iChannel0, uv);
}
```

## 11. รายการตรวจสอบการแก้ปัญหา

- ไม่มีเอาต์พุต:
  - ตรวจสอบว่าซอร์ส Image ไม่ว่างเปล่า
  - ตรวจสอบว่าโหมดคอมไพล์ตรงกับจุดเริ่มต้นของคุณ (`mainImage` หรือ `main`)
- เท็กซ์เจอร์สีม่วง/ไม่ถูกต้อง:
  - ตรวจสอบการผูก Resource และการกำหนดเส้นทางแชนเนล
  - ตรวจสอบ `iChannelResolution[n].z` (`0.0` หมายถึงไม่ถูกต้อง/ไม่พร้อมใช้งาน)
- พิกัดในเชเดอร์ Direct ไม่ถูกต้อง:
  - ใช้ `gl_FragCoord.xy - fmAreaOffset` เพื่อหาพิกัดเฉพาะที่ของพื้นที่
- พฤติกรรมการลากไม่ถูกต้อง:
  - ใช้ตัวเลือก `Update iMouse Position Only While Holding LMB`
- เชเดอร์ Direct ไม่ปรับความทึบแสง:
  - คูณแอลฟาด้วย `fmOpacity` ด้วยตนเอง
