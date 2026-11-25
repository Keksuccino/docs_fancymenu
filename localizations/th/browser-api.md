---
title: JavaScript API ของเบราว์เซอร์
description: >-
  วิธีใช้ JavaScript API ของ FancyMenu ในฟีเจอร์ม็อดที่ใช้ Rinku เช่นองค์ประกอบ
  Browser
sourceBlobSha: 1dff260c0c5337037200dbf9033300a6bba56ca1
---
# JavaScript API ของ FancyMenu

FancyMenu ฉีด JavaScript bridge เข้าไปในทุกฟีเจอร์ที่ทำงานด้วย [Rinku](https://modrinth.com/mod/rinku) (เช่นองค์ประกอบ **Browser**) bridge นี้ช่วยให้เนื้อหาบนเว็บทำสิ่งต่อไปนี้ได้:

- เรียกใช้ [action](/action-scripts) ของ FancyMenu จาก JavaScript ได้โดยตรง
- อ่านค่า [placeholder](/placeholders) ของ FancyMenu แบบอะซิงโครนัส

API นี้เปิดให้ใช้งานผ่าน global สองตัว:
- `window.fancymenu` – namespace หลัก
- `window.FancyMenu` – alias (มีโครงสร้างเหมือนกับ `fancymenu` ทุกประการ)

ใช้ event `fancymenu-ready` หรือตรวจสอบว่ามี API หรือไม่ก่อนเรียกใช้งาน เพื่อให้แน่ใจว่า bridge พร้อมใช้งานแล้ว

## 1. Namespace และโครงสร้าง

- `fancymenu.actions` – เรียกใช้ action ของ FancyMenu จากเบราว์เซอร์
- `fancymenu.placeholders` – อ่านค่าของ placeholder ของ FancyMenu แบบอะซิงโครนัส
- `FancyMenu` มีโครงสร้างเหมือน `fancymenu` ดังนั้นทั้งสองตัวจึงมี namespace ย่อยเหมือนกัน

มี helper สำหรับ action สองตัว:
- `fancymenu.actions.execute(actionType, actionValue?)`
- `fancymenu.actions.executeWithCallback(actionType, actionValue?, onSuccess?, onFailure?)`

## 2. ความพร้อมใช้งาน

```javascript
if (typeof fancymenu !== 'undefined') {
    // ใช้งานได้อย่างปลอดภัย
}

window.addEventListener('fancymenu-ready', () => {
    console.log('FancyMenu API พร้อมใช้งานแล้ว');
});
```

นอกจากนี้ยังสามารถโฮสต์เนื้อหาไว้ในเครื่องได้ โดยวางไฟล์ HTML ไว้ใน `<game-directory>/config/fancymenu/assets/` แล้วโหลดผ่าน URL ในรูปแบบ `file:///config/fancymenu/assets/<name>.html`

## 3. การเรียกใช้ Action

ใช้ namespace `fancymenu.actions` การเรียกแต่ละครั้งจะใช้รูปแบบเดียวกับสตริง action ในสคริปต์ FancyMenu

### เรียกใช้แบบรวดเร็ว

```javascript
fancymenu.actions.execute('quitgame');                // action ที่ไม่มีค่า
fancymenu.actions.execute('opengui', 'title_screen'); // action ที่มีค่า
fancymenu.actions.execute('set_variable', 'hp:20');   // ค่าใช้รูปแบบ name:value
```

### ใช้ Callback

```javascript
fancymenu.actions.executeWithCallback(
    'opengui',
    'title_screen',
    result => console.log('เปิดหน้าจอไตเติลแล้ว'),
    error  => console.error('เปิดไม่สำเร็จ:', error)
);

// พารามิเตอร์ value เป็นตัวเลือก หากไม่ระบุ ให้ส่ง callback ต่อจาก actionType โดยตรง
fancymenu.actions.executeWithCallback(
    'quitgame',
    result => console.log('สั่งออกจากเกมแล้ว'),
    error  => console.error('ออกจากเกมไม่สำเร็จ:', error)
);
```

helper รุ่นเก่า `fancymenu.execute(...)` และ `fancymenu.executeWithCallback(...)` ยังคงใช้งานได้ โดยจะส่งต่อการเรียกไปยัง namespace `actions`

### ประเภท Action ที่ใช้บ่อย

- `quitgame` – ออกจากเกมทันที (ไม่มีค่า)
- `back_to_last_screen` – กลับไปยัง GUI ก่อนหน้า (ไม่มีค่า)
- `opengui` – เปิดหน้าจอของ FancyMenu หรือ vanilla (ค่า: ตัวระบุหน้าจอ)
- `openlink` – เปิดเบราว์เซอร์ (ค่า: URL)
- `sendmessage` – ส่งข้อความในแชต (ค่า: ข้อความ)
- `set_variable` – กำหนดค่าให้ตัวแปร FancyMenu (ค่า: `name:value`)
- `joinserver` – เชื่อมต่อกับเซิร์ฟเวอร์ (ค่า: ที่อยู่)
- `disconnect_server_or_world` – ตัดการเชื่อมต่อและไปยังหน้าจอเป้าหมาย (ค่า: ตัวระบุหน้าจอ)

Action ทุกตัวที่มีอยู่ใน FancyMenu สามารถเรียกใช้ผ่าน bridge นี้ได้ ดู [สคริปต์ action](/action-scripts) เพื่อดูรายการทั้งหมด

## 4. การอ่าน Placeholder

ระบบ [placeholder](/placeholders) ของ FancyMenu เปิดให้ใช้งานผ่าน `fancymenu.placeholders` (และ `FancyMenu.placeholders`) เมธอด helper ทั้งสองตัวจะคืนค่าเป็น `Promise<string>`:

```ts
fancymenu.placeholders.get(identifier: string): Promise<string>
fancymenu.placeholders.getWithVars(identifier: string, ...vars: string[]): Promise<string>
```

### การระบุตัวแปร

- ตัวแปรเป็นสตริงในรูปแบบ `name:value` bridge จะแยกที่เครื่องหมายโคลอนตัว **แรก** เท่านั้น ดังนั้นค่าอาจมีเครื่องหมายโคลอนเพิ่มเติมได้
- ระบบจะตัดช่องว่างหัวท้ายของชื่อและค่า และจะปฏิเสธชื่อที่ว่างเปล่า
- ระบุตัวแปรให้ครบตามที่ placeholder ต้องการ และไม่ต้องระบุตัวแปรที่เป็นตัวเลือก

### ตัวอย่าง

```javascript
// ไม่มีตัวแปร
fancymenu.placeholders.get('playername')
    .then(name => console.log('ผู้เล่น:', name));

// มีตัวแปรหนึ่งตัว
fancymenu.placeholders.getWithVars('uptime_duration', 'output_as_millis:false')
    .then(seconds => console.log('เวลาเล่น (วินาที):', seconds));

// มีตัวแปรหลายตัว
fancymenu.placeholders.getWithVars(
    'split_text',
    'input:apple|banana|carrot',
    'regex:\\|',
    'max_parts:-1',
    'split_index:1'
).then(part => console.log('ส่วนที่เลือก:', part));
```

### รูปแบบข้อผิดพลาด

Promise ที่ถูกปฏิเสธจะมีข้อมูลข้อผิดพลาดแบบมีโครงสร้าง:

```ts
interface PlaceholderError {
    code: 'NOT_FOUND' | 'MISSING_VARIABLE' | 'INVALID_VARIABLE' | 'EVALUATION_ERROR' | 'INTERNAL_ERROR';
    message: string;
    details?: unknown;
}
```

ตัวอย่างการจัดการข้อผิดพลาด:

```javascript
fancymenu.placeholders.get('unknown')
    .catch(error => console.warn(error.code, error.message));
```

## 5. ตัวอย่างฉบับสมบูรณ์

```html
<!DOCTYPE html>
<html>
<head>
    <title>การเชื่อมต่อกับ FancyMenu</title>
</head>
<body>
    <h1>การควบคุมเกม</h1>
    
    <button onclick="quitGame()">ออกจากเกม</button>
    <button onclick="openTitleScreen()">หน้าจอไตเติล</button>
    <button onclick="disconnectFromServer()">ตัดการเชื่อมต่อ</button>
    <button onclick="setVariable()">ตั้งค่าตัวแปร</button>
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
                () => console.log('เปิดหน้าจอไตเติลแล้ว!'),
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
                    'เวลาเล่น (วินาที): ' + uptimeSeconds + '\n' +
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

- **ตรวจสอบ bridge** ก่อนใช้งาน หรือรอฟัง event `fancymenu-ready`
- **จัดการข้อผิดพลาด** (ใช้ callback สำหรับ [action](/action-scripts) และ `.catch` สำหรับ [placeholder](/placeholders)) เพื่อแสดงคำแนะนำที่เป็นประโยชน์
- **ตรวจสอบข้อมูลที่ป้อน** ก่อนส่งให้ action หรือตัวแปรของ [placeholder](/placeholders)
- **จำกัดความถี่ของคำขอ** หลีกเลี่ยงการเรียก bridge ถี่เกินไป (โดยเฉพาะการวนลูปเพื่อรีเฟรช placeholder)
- **ความปลอดภัย:** เนื้อหาในเบราว์เซอร์สามารถเรียกใช้ action ของ FancyMenu ที่ลงทะเบียนไว้ได้ทุกตัว รวมถึง action สำหรับไฟล์ เครือข่าย คำสั่ง คลิปบอร์ด ชุดทรัพยากร ลิงก์ และการออกจากเกม ให้โหลดเฉพาะหน้าที่เชื่อถือได้ และตรวจสอบข้อมูลทั้งหมดที่ได้รับจากเนื้อหาบนเว็บ

## 7. การแก้ไขปัญหา

1. ตรวจสอบว่าหน้านี้โหลดอยู่ในเบราว์เซอร์ Rinku ที่ FancyMenu ควบคุม
2. ตรวจดูข้อผิดพลาด JavaScript ในคอนโซลของเบราว์เซอร์
3. ตรวจสอบว่าตัวระบุ [placeholder](/placeholders) หรือประเภท [action](/action-scripts) ถูกต้อง และระบุค่าที่จำเป็นครบถ้วน
4. หากการทำงานล้มเหลวโดยไม่คาดคิด ให้ตรวจดูข้อความผิดพลาดของ FancyMenu ในบันทึก Minecraft (`latest.log`)
