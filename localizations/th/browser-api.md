---
title: JavaScript API ของเบราว์เซอร์
description: >-
  วิธีใช้ JavaScript API ของ FancyMenu ในฟีเจอร์ที่ใช้ Rinku เช่น องค์ประกอบ
  Browser
---
# JavaScript API ของ FancyMenu

FancyMenu จะแทรกบริดจ์ JavaScript ลงในฟีเจอร์ทุกอย่างที่ทำงานอยู่บน [Rinku](https://modrinth.com/mod/rinku) (เช่น องค์ประกอบ **Browser**) บริดจ์นี้ช่วยให้เนื้อหาเว็บสามารถ:

- เรียกใช้ [แอ็กชัน](./action-scripts) ของ FancyMenu ได้โดยตรงจาก JavaScript
- อ่านค่า [placeholder](/placeholders) ของ FancyMenu แบบอะซิงโครนัส

ตัวแปรโกลบอลสองตัวใช้เปิดเผย API นี้:
- `window.fancymenu` – เนมสเปซหลัก
- `window.FancyMenu` – ชื่อเรียกแทน (มีโครงสร้างเหมือนกับ `fancymenu` ทุกประการ)

ใช้เหตุการณ์ `fancymenu-ready` หรือตรวจสอบฟีเจอร์เพื่อให้แน่ใจว่าบริดจ์พร้อมใช้งานก่อนเรียกใช้

## 1. เนมสเปซและโครงสร้าง

- `fancymenu.actions` – เรียกใช้แอ็กชันของ FancyMenu จากเบราว์เซอร์
- `fancymenu.placeholders` – อ่านค่าของ placeholder ของ FancyMenu แบบอะซิงโครนัส
- `FancyMenu` เป็นชื่อเรียกแทน `fancymenu` ดังนั้นทั้งสองตัวจึงมีซับเนมสเปซเหมือนกัน

แอ็กชันมีตัวช่วยสองรายการ:
- `fancymenu.actions.execute(actionType, actionValue?)`
- `fancymenu.actions.executeWithCallback(actionType, actionValue?, onSuccess?, onFailure?)`

## 2. ความพร้อมใช้งาน

```javascript
if (typeof fancymenu !== 'undefined') {
    // สามารถใช้งานได้อย่างปลอดภัย
}

window.addEventListener('fancymenu-ready', () => {
    console.log('FancyMenu API พร้อมใช้งานแล้ว');
});
```

นอกจากนี้ยังสามารถโฮสต์เนื้อหาไว้ในเครื่องได้ โดยวางไฟล์ HTML ไว้ใน `<game-directory>/config/fancymenu/assets/` แล้วโหลดผ่าน URL รูปแบบ `file:///config/fancymenu/assets/<name>.html`

## 3. การเรียกใช้แอ็กชัน

ใช้เนมสเปซ `fancymenu.actions` การเรียกใช้แต่ละครั้งจะสอดคล้องกับสตริงแอ็กชันที่ใช้ในสคริปต์ FancyMenu

### การเรียกใช้แบบรวดเร็ว

```javascript
fancymenu.actions.execute('quitgame');                // แอ็กชันที่ไม่มีค่า
fancymenu.actions.execute('opengui', 'title_screen'); // แอ็กชันที่มีค่า
fancymenu.actions.execute('set_variable', 'hp:20');   // ค่าใช้รูปแบบ name:value
```

### การเรียกใช้พร้อม Callback

```javascript
fancymenu.actions.executeWithCallback(
    'opengui',
    'title_screen',
    result => console.log('เปิดหน้าจอชื่อเรื่องแล้ว'),
    error  => console.error('เปิดไม่สำเร็จ:', error)
);

// พารามิเตอร์ value เป็นตัวเลือก เมื่อไม่ระบุ ให้ส่ง callback ต่อจาก actionType ได้โดยตรง
fancymenu.actions.executeWithCallback(
    'quitgame',
    result => console.log('เรียกใช้การออกจากเกมแล้ว'),
    error  => console.error('ออกจากเกมไม่สำเร็จ:', error)
);
```

ตัวช่วยรุ่นเก่า `fancymenu.execute(...)` และ `fancymenu.executeWithCallback(...)` ยังคงทำงานโดยส่งต่อไปยังเนมสเปซ `actions`

### ประเภทแอ็กชันที่ใช้บ่อย

- `quitgame` – ออกจากเกมทันที (ไม่มีค่า)
- `back_to_last_screen` – กลับไปยัง GUI ก่อนหน้า (ไม่มีค่า)
- `opengui` – เปิดหน้าจอของ FancyMenu หรือหน้าจอ vanilla (ค่า: ตัวระบุหน้าจอ)
- `openlink` – เปิดเบราว์เซอร์ (ค่า: URL)
- `sendmessage` – ส่งข้อความแชต (ค่า: ข้อความ)
- `set_variable` – กำหนดตัวแปร FancyMenu (ค่า: `name:value`)
- `joinserver` – เชื่อมต่อกับเซิร์ฟเวอร์ (ค่า: ที่อยู่)
- `disconnect_server_or_world` – ตัดการเชื่อมต่อและไปยังหน้าจอเป้าหมาย (ค่า: ตัวระบุหน้าจอ)

แอ็กชันทุกอย่างที่มีอยู่ใน FancyMenu สามารถเรียกใช้ผ่านบริดจ์นี้ได้ ดู [สคริปต์แอ็กชัน](./action-scripts) สำหรับรายการทั้งหมด

## 4. การอ่าน Placeholder

ระบบ [placeholder](/placeholders) ของ FancyMenu เปิดให้ใช้งานผ่าน `fancymenu.placeholders` (และ `FancyMenu.placeholders`) เมธอดตัวช่วยทั้งสองรายการจะคืนค่าเป็น `Promise<string>`:

```ts
fancymenu.placeholders.get(identifier: string): Promise<string>
fancymenu.placeholders.getWithVars(identifier: string, ...vars: string[]): Promise<string>
```

### การส่งตัวแปร

- ตัวแปรเป็นสตริงในรูปแบบ `name:value` บริดจ์จะแยกที่โคลอนตัวแรกเท่านั้น ดังนั้นค่าจึงสามารถมีโคลอนเพิ่มเติมได้
- ชื่อและค่าจะถูกตัดช่องว่าง ห้ามใช้ชื่อว่าง
- ส่งตัวแปรให้ครบตามที่ placeholder ต้องการ และละเว้นตัวแปรที่เป็นตัวเลือกได้

### ตัวอย่าง

```javascript
// ไม่มีตัวแปร
fancymenu.placeholders.get('playername')
    .then(name => console.log('ผู้เล่น:', name));

// ตัวแปรหนึ่งรายการ
fancymenu.placeholders.getWithVars('uptime_duration', 'output_as_millis:false')
    .then(seconds => console.log('เวลาทำงาน (วินาที):', seconds));

// หลายตัวแปร
fancymenu.placeholders.getWithVars(
    'split_text',
    'input:apple|banana|carrot',
    'regex:\\|',
    'max_parts:-1',
    'split_index:1'
).then(part => console.log('ส่วนที่เลือก:', part));
```

### รูปแบบข้อผิดพลาด

Promise ที่ถูกปฏิเสธจะมีข้อผิดพลาดแบบมีโครงสร้าง:

```ts
interface PlaceholderError {
    code: 'NOT_FOUND' | 'MISSING_VARIABLE' | 'INVALID_VARIABLE' | 'EVALUATION_ERROR' | 'INTERNAL_ERROR';
    message: string;
    details?: unknown;
}
```

ตัวอย่างการจัดการ:

```javascript
fancymenu.placeholders.get('unknown')
    .catch(error => console.warn(error.code, error.message));
```

## 5. ตัวอย่างแบบสมบูรณ์

```html
<!DOCTYPE html>
<html>
<head>
    <title>การเชื่อมต่อกับ FancyMenu</title>
</head>
<body>
    <h1>การควบคุมเกม</h1>
    
    <button onclick="quitGame()">ออกจากเกม</button>
    <button onclick="openTitleScreen()">หน้าจอชื่อเรื่อง</button>
    <button onclick="disconnectFromServer()">ตัดการเชื่อมต่อ</button>
    <button onclick="setVariable()">กำหนดตัวแปร</button>
    <button onclick="loadPlaceholders()">โหลด Placeholder</button>

    <div id="placeholderOutput" style="margin-top:16px;font-family:monospace"></div>
    
    <script>
        function getActions() {
            if (typeof fancymenu === 'undefined') {
                console.warn('FancyMenu API ยังไม่พร้อมใช้งาน');
                return null;
            }
            return fancymenu.actions || fancymenu;
        }

        function quitGame() {
            const actions = getActions();
            if (!actions) return;
            actions.execute('quitgame');
        }
        
        function openTitleScreen() {
            const actions = getActions();
            if (!actions) return;
            actions.executeWithCallback(
                'opengui',
                'title_screen',
                () => console.log('เปิดหน้าจอชื่อเรื่องแล้ว!'),
                err => console.error('ข้อผิดพลาด:', err)
            );
        }
        
        function disconnectFromServer() {
            const actions = getActions();
            if (!actions) return;
            actions.execute('disconnect_server_or_world', 'title_screen');
        }
        
        function setVariable() {
            const actions = getActions();
            if (!actions) return;
            var varName = prompt('ชื่อตัวแปร:');
            var varValue = prompt('ค่าตัวแปร:');
            if (varName && varValue) {
                actions.execute('set_variable', varName + ':' + varValue);
            }
        }

        function loadPlaceholders() {
            if (typeof fancymenu === 'undefined' || !fancymenu.placeholders) {
                console.warn('Placeholder API ของ FancyMenu ยังไม่พร้อมใช้งาน');
                return;
            }

            Promise.all([
                fancymenu.placeholders.get('playername'),
                fancymenu.placeholders.getWithVars('uptime_duration', 'output_as_millis:false'),
                fancymenu.placeholders.getWithVars(
                    'split_text',
                    'input:apple|banana|carrot',
                    'regex:\\|',
                    'max_parts:-1',
                    'split_index:1'
                )
            ]).then(([playerName, uptimeSeconds, secondFruit]) => {
                document.getElementById('placeholderOutput').textContent =
                    'ผู้เล่น: ' + playerName + '\n' +
                    'เวลาทำงาน (วินาที): ' + uptimeSeconds + '\n' +
                    'ผลไม้ลำดับที่สอง: ' + secondFruit;
            }).catch(error => {
                console.error('คำขอ Placeholder ล้มเหลว:', error);
            });
        }
    </script>
</body>
</html>
```

## 6. แนวทางปฏิบัติที่ดีและหมายเหตุ

- **ตรวจสอบบริดจ์** ก่อนใช้งาน หรือรอรับเหตุการณ์ `fancymenu-ready`
- **จัดการข้อผิดพลาด** (ใช้ callback สำหรับ [แอ็กชัน](/action-scripts) และ `.catch` สำหรับ [placeholder](/placeholders)) เพื่อแสดงข้อมูลที่เป็นประโยชน์
- **ตรวจสอบข้อมูลนำเข้า** ก่อนส่งให้แอ็กชันหรือตัวแปรของ [placeholder](/placeholders)
- **จำกัดความถี่ของคำขอ** หลีกเลี่ยงการเรียกใช้บริดจ์ถี่เกินไป โดยเฉพาะลูปรีเฟรช placeholder
- **ความปลอดภัย:** เนื้อหาเบราว์เซอร์สามารถเรียกใช้แอ็กชัน FancyMenu ที่ลงทะเบียนไว้ได้ทุกอย่าง รวมถึงแอ็กชันเกี่ยวกับไฟล์ เครือข่าย คำสั่ง คลิปบอร์ด รีซอร์สแพ็ก ลิงก์ และการออกจากเกม ควรโหลดเฉพาะหน้าที่เชื่อถือได้ และตรวจสอบข้อมูลทั้งหมดที่ได้รับจากเนื้อหาเว็บ

## 7. การแก้ไขปัญหา

1. ตรวจสอบว่าหน้านั้นโหลดอยู่ในเบราว์เซอร์ Rinku ที่ควบคุมโดย FancyMenu
2. ตรวจสอบคอนโซลเบราว์เซอร์เพื่อค้นหาข้อผิดพลาด JavaScript
3. ตรวจสอบว่าตัวระบุ [placeholder](/placeholders) หรือประเภท [แอ็กชัน](/action-scripts) ถูกต้อง และมีการส่งค่าที่จำเป็นครบถ้วน
4. หากการทำงานล้มเหลวโดยไม่คาดคิด ให้ตรวจสอบล็อก Minecraft (`latest.log`) เพื่อค้นหาข้อความข้อผิดพลาดของ FancyMenu
