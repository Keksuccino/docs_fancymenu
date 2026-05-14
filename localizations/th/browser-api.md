---
title: Browser JavaScript API
description: >-
  วิธีใช้ JavaScript API ของ FancyMenu ในฟีเจอร์ของม็อดที่ใช้ MCEF
  เช่นองค์ประกอบ Browser
---

# FancyMenu JavaScript API

FancyMenu จะฉีด JavaScript bridge เข้าไปในฟีเจอร์ทุกตัวที่ใช้ MCEF (เช่นองค์ประกอบ **Browser**) โดย bridge นี้ช่วยให้เนื้อหาเว็บสามารถ:

- เรียกใช้ [action](./action-scripts) ของ FancyMenu ใดก็ได้โดยตรงจาก JavaScript,
- อ่านค่า [placeholder](/placeholders) ของ FancyMenu ใดก็ได้แบบไม่ซิงก์ (asynchronously)

มี global 2 ตัวที่เปิดให้เข้าถึง API:
- `window.fancymenu` – namespace หลัก
- `window.FancyMenu` – alias (มีโครงสร้างเหมือน `fancymenu` ทุกอย่าง)

ให้ใช้เหตุการณ์ `fancymenu-ready` หรือการตรวจสอบความพร้อมของฟีเจอร์ เพื่อให้แน่ใจว่า bridge พร้อมใช้งานก่อนเรียกใช้

## 1. Namespaces และโครงสร้าง

- `fancymenu.actions` – เรียกใช้ FancyMenu actions จากเบราว์เซอร์
- `fancymenu.placeholders` – อ่านค่า FancyMenu placeholder แบบไม่ซิงก์
- `FancyMenu` จะสะท้อน `fancymenu` ดังนั้นทั้งสองตัวจึงเปิด sub-namespace เดียวกัน

Actions มี helper 2 ตัว:
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

เนื้อหาสามารถโฮสต์แบบโลคัลได้ด้วย: วางไฟล์ HTML ไว้ใน `config/fancymenu/assets/` และโหลดผ่าน URL รูปแบบ `file:///config/fancymenu/assets/<name>.html`

## 3. การเรียกใช้ Actions

ใช้ namespace `fancymenu.actions` โดยแต่ละคำสั่งจะสอดคล้องกับสตริง action ที่ใช้ในสคริปต์ของ FancyMenu

### การเรียกแบบสั้น

```javascript
fancymenu.actions.execute('quitgame');                // action ที่ไม่มีค่า
fancymenu.actions.execute('opengui', 'title_screen'); // action ที่มีค่า
fancymenu.actions.execute('set_variable', 'hp:20');   // ค่าใช้รูปแบบ name:value
```

### การเรียกแบบมี Callback

```javascript
fancymenu.actions.executeWithCallback(
    'opengui',
    'title_screen',
    result => console.log('เปิด title screen แล้ว'),
    error  => console.error('เปิดไม่สำเร็จ:', error)
);

// พารามิเตอร์ value เป็นตัวเลือกได้ หากไม่ใส่ ให้ส่ง callback ต่อจาก actionType ได้เลย
fancymenu.actions.executeWithCallback(
    'quitgame',
    result => console.log('สั่งออกจากเกมแล้ว'),
    error  => console.error('สั่งออกไม่สำเร็จ:', error)
);

helper แบบเดิม `fancymenu.execute(...)` และ `fancymenu.executeWithCallback(...)` ยังใช้งานได้ และจะส่งต่อไปยัง namespace `actions` ดังนั้นเนื้อหาเดิมไม่จำเป็นต้องแก้ทันที
```

### ประเภทของ Action ที่ใช้บ่อย

- `quitgame` – ออกจากเกมทันที (ไม่มีค่า)
- `back_to_last_screen` – กลับไปยัง GUI ก่อนหน้า (ไม่มีค่า)
- `opengui` – เปิดหน้าจอของ FancyMenu หรือ vanilla (ค่า: ตัวระบุหน้าจอ)
- `openlink` – เปิดเบราว์เซอร์ (ค่า: URL)
- `sendmessage` – ส่งข้อความแชต (ค่า: ข้อความ)
- `set_variable` – กำหนดตัวแปรของ FancyMenu (ค่า: `name:value`)
- `joinserver` – เชื่อมต่อกับเซิร์ฟเวอร์ (ค่า: ที่อยู่เซิร์ฟเวอร์)
- `disconnect_server_or_world` – ตัดการเชื่อมต่อและไปยังหน้าจอเป้าหมาย (ค่า: ตัวระบุหน้าจอ)

ทุก action ที่มีอยู่ใน FancyMenu สามารถใช้งานผ่าน bridge นี้ได้ ดู [action scripts](./action-scripts) สำหรับรายการทั้งหมด

## 4. การอ่าน Placeholders

ระบบ [placeholder](/placeholders) ของ FancyMenu เปิดให้ใช้งานผ่าน `fancymenu.placeholders` (และ `FancyMenu.placeholders`) โดยทั้งสอง helper method จะคืนค่า `Promise<string>`:

```ts
fancymenu.placeholders.get(identifier: string): Promise<string>
fancymenu.placeholders.getWithVars(identifier: string, ...vars: string[]): Promise<string>
```

### การส่งตัวแปร

- ตัวแปรต้องเป็นสตริงรูปแบบ `name:value` โดย bridge จะตัดแบ่งด้วยโคลอน **ตัวแรก** เท่านั้น ดังนั้นค่าจึงมีโคลอนเพิ่มเติมได้
- ชื่อและค่าจะถูกตัดช่องว่างหัวท้าย และจะไม่ยอมรับชื่อที่ว่างเปล่า
- ส่งตัวแปรให้ครบตามที่ placeholder ต้องการ และละเว้นตัวที่เป็นตัวเลือกได้

### ตัวอย่าง

```javascript
// ไม่มีตัวแปร
fancymenu.placeholders.get('playername')
    .then(name => console.log('ผู้เล่น:', name));

// หนึ่งตัวแปร
fancymenu.placeholders.getWithVars('uptime_duration', 'output_as_millis:false')
    .then(seconds => console.log('เวลาที่เปิดอยู่ (วินาที):', seconds));

// หลายตัวแปร
fancymenu.placeholders.getWithVars(
    'split_text',
    'input:apple|banana|carrot',
    'regex:\\|',
    'max_parts:-1',
    'split_index:1'
).then(part => console.log('ส่วนที่เลือก:', part));
```

### โมเดลข้อผิดพลาด

Promise ที่ถูก reject จะมี error แบบมีโครงสร้าง:

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

## 5. ตัวอย่างแบบครบถ้วน

```html
<!DOCTYPE html>
<html>
<head>
    <title>FancyMenu Integration</title>
</head>
<body>
    <h1>Game Controls</h1>
    
    <button onclick="quitGame()">Quit Game</button>
    <button onclick="openTitleScreen()">Title Screen</button>
    <button onclick="disconnectFromServer()">Disconnect</button>
    <button onclick="setVariable()">Set Variable</button>
    <button onclick="loadPlaceholders()">Load Placeholders</button>

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
                () => console.log('เปิด title screen แล้ว!'),
                err => console.error('เกิดข้อผิดพลาด:', err)
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
            var varName = prompt('ชื่อ variable:');
            var varValue = prompt('ค่าของ variable:');
            if (varName && varValue) {
                actions.execute('set_variable', varName + ':' + varValue);
            }
        }

        function loadPlaceholders() {
            if (typeof fancymenu === 'undefined' || !fancymenu.placeholders) {
                console.warn('FancyMenu placeholder API ยังไม่พร้อมใช้งาน');
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
                    'เวลาที่เปิดอยู่ (วินาที): ' + uptimeSeconds + '\n' +
                    'ผลไม้ลำดับที่สอง: ' + secondFruit;
            }).catch(error => {
                console.error('การร้องขอ placeholder ไม่สำเร็จ:', error);
            });
        }
    </script>
</body>
</html>
```

## 6. แนวทางปฏิบัติที่ดีและข้อควรระวัง

- **ตรวจหา bridge** ก่อนใช้งาน หรือรอฟัง `fancymenu-ready`
- **จัดการข้อผิดพลาด** (callback สำหรับ [actions](/action-scripts), `.catch` สำหรับ [placeholders](/placeholders)) เพื่อแสดงผลตอบกลับที่เป็นประโยชน์
- **ตรวจสอบอินพุต** ก่อนส่งไปยัง actions หรือค่าตัวแปรของ [placeholder](/placeholders)
- **จำกัดความถี่ของคำขอ**; หลีกเลี่ยงการเรียก bridge ถี่เกินไป (โดยเฉพาะลูปรีเฟรช placeholder)
- **ความปลอดภัย**: actions จะทำงานด้วยสิทธิ์ปกติของผู้เล่น ควรระวังข้อมูลที่มาจากผู้ใช้เพื่อหลีกเลี่ยงการ injection

## 7. การแก้ปัญหา

1. ตรวจสอบว่าหน้านี้ถูกโหลดอยู่ใน MCEF browser ที่ FancyMenu ควบคุม
2. ตรวจสอบคอนโซลของเบราว์เซอร์เพื่อหาข้อผิดพลาด JavaScript
3. ยืนยันว่า [placeholder](/placeholders) identifier หรือชนิด [action](/action-scripts) ถูกต้อง และมีการส่งค่าที่จำเป็นครบ
4. ตรวจสอบ log ของ Minecraft (`latest.log`) เพื่อดูข้อความ error ของ FancyMenu หากการทำงานล้มเหลวโดยไม่คาดคิด
