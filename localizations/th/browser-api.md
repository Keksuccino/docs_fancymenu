---
title: Browser JavaScript API
description: >-
  วิธีใช้ JavaScript API ของ FancyMenu ในฟีเจอร์ของม็อดที่ใช้ MCEF
  เช่นองค์ประกอบ Browser
---

# FancyMenu JavaScript API

FancyMenu จะฉีด JavaScript bridge เข้าไปในทุกฟีเจอร์ที่ทำงานบน MCEF (เช่นองค์ประกอบ **Browser**) โดย bridge นี้ช่วยให้เนื้อหาเว็บสามารถ:

- เรียกใช้ [action](./action-scripts) ของ FancyMenu ได้โดยตรงจาก JavaScript,
- อ่านค่า [placeholder](/placeholders) ของ FancyMenu แบบอะซิงก์ได้

มี globals สองตัวที่เปิดให้ใช้ API:
- `window.fancymenu` – namespace หลัก
- `window.FancyMenu` – alias (มีโครงสร้างเหมือน `fancymenu` ทุกประการ)

ให้ใช้ event `fancymenu-ready` หรือการตรวจจับความพร้อมของฟีเจอร์ เพื่อให้แน่ใจว่า bridge พร้อมใช้งานก่อนเรียกใช้

## 1. Namespaces & Structure

- `fancymenu.actions` – เรียกใช้ FancyMenu actions จากเบราว์เซอร์
- `fancymenu.placeholders` – อ่านค่าของ FancyMenu placeholders แบบอะซิงก์
- `FancyMenu` จะสะท้อน `fancymenu` ดังนั้นทั้งสองตัวจะเปิด sub-namespace เดียวกัน

Actions มี helper สองตัว:
- `fancymenu.actions.execute(actionType, actionValue?)`
- `fancymenu.actions.executeWithCallback(actionType, actionValue?, onSuccess?, onFailure?)`

## 2. Availability

```javascript
if (typeof fancymenu !== 'undefined') {
    // ใช้งานได้อย่างปลอดภัย
}

window.addEventListener('fancymenu-ready', () => {
    console.log('FancyMenu API is ready');
});
```

เนื้อหาสามารถโฮสต์แบบโลคัลได้ด้วย: วางไฟล์ HTML ไว้ใน `<game-directory>/config/fancymenu/assets/` แล้วโหลดผ่าน URL รูปแบบ `file:///config/fancymenu/assets/<name>.html`

## 3. Executing Actions

ใช้ namespace `fancymenu.actions` โดยการเรียกแต่ละครั้งจะสอดคล้องกับสตริงของ action ที่ใช้ในสคริปต์ของ FancyMenu

### Quick Calls

```javascript
fancymenu.actions.execute('quitgame');                // action แบบไม่มีค่า
fancymenu.actions.execute('opengui', 'title_screen'); // action แบบมีค่า
fancymenu.actions.execute('set_variable', 'hp:20');   // ค่าจะใช้รูปแบบ name:value
```

### With Callbacks

```javascript
fancymenu.actions.executeWithCallback(
    'opengui',
    'title_screen',
    result => console.log('Opened title screen'),
    error  => console.error('Open failed:', error)
);

// พารามิเตอร์ value เป็นตัวเลือก หากไม่ใส่ ให้ส่ง callbacks ต่อจาก actionType ได้เลย
fancymenu.actions.executeWithCallback(
    'quitgame',
    result => console.log('Quit triggered'),
    error  => console.error('Quit failed:', error)
);
```

helper แบบเดิม `fancymenu.execute(...)` และ `fancymenu.executeWithCallback(...)` ยังส่งต่อไปยัง namespace `actions` อยู่เช่นเดิม

### Common Action Types

- `quitgame` – ออกจากเกมทันที (ไม่มีค่า)
- `back_to_last_screen` – กลับไปยัง GUI ก่อนหน้า (ไม่มีค่า)
- `opengui` – เปิด FancyMenu หรือหน้าจอ vanilla (ค่า: ตัวระบุหน้าจอ)
- `openlink` – เปิดเบราว์เซอร์ (ค่า: URL)
- `sendmessage` – ส่งข้อความในแชต (ค่า: ข้อความ)
- `set_variable` – กำหนดค่าให้ตัวแปรของ FancyMenu (ค่า: `name:value`)
- `joinserver` – เชื่อมต่อไปยังเซิร์ฟเวอร์ (ค่า: ที่อยู่)
- `disconnect_server_or_world` – ตัดการเชื่อมต่อและไปยังหน้าจอเป้าหมาย (ค่า: ตัวระบุหน้าจอ)

ทุก action ที่มีอยู่ใน FancyMenu สามารถใช้งานผ่าน bridge ได้ ดูรายการครบถ้วนได้ที่ [action scripts](./action-scripts)

## 4. Reading Placeholders

ระบบ [placeholder](/placeholders) ของ FancyMenu ถูกเปิดให้ใช้งานผ่าน `fancymenu.placeholders` (และ `FancyMenu.placeholders`) โดยทั้งสองเมธอดช่วยเหลือจะคืนค่า `Promise<string>`:

```ts
fancymenu.placeholders.get(identifier: string): Promise<string>
fancymenu.placeholders.getWithVars(identifier: string, ...vars: string[]): Promise<string>
```

### Supplying Variables

- Variables เป็นสตริงในรูปแบบ `name:value` โดย bridge จะแยกเฉพาะที่ **colon ตัวแรก** เท่านั้น ดังนั้น value สามารถมี colon เพิ่มเติมได้
- ชื่อและค่าจะถูก trim; ชื่อว่างจะถูกปฏิเสธ
- ส่ง variables ให้เท่ากับที่ placeholder ต้องการ และละเว้นตัวเลือกที่ไม่จำเป็นได้

### Examples

```javascript
// ไม่มี variables
fancymenu.placeholders.get('playername')
    .then(name => console.log('Player:', name));

// หนึ่ง variable
fancymenu.placeholders.getWithVars('uptime_duration', 'output_as_millis:false')
    .then(seconds => console.log('Uptime (s):', seconds));

// หลาย variables
fancymenu.placeholders.getWithVars(
    'split_text',
    'input:apple|banana|carrot',
    'regex:\\|',
    'max_parts:-1',
    'split_index:1'
).then(part => console.log('Selected part:', part));
```

### Error Model

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

## 5. Complete Example

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
                console.warn('FancyMenu API is not available yet.');
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
                () => console.log('Title screen opened!'),
                err => console.error('Error:', err)
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
            var varName = prompt('Variable name:');
            var varValue = prompt('Variable value:');
            if (varName && varValue) {
                actions.execute('set_variable', varName + ':' + varValue);
            }
        }

        function loadPlaceholders() {
            if (typeof fancymenu === 'undefined' || !fancymenu.placeholders) {
                console.warn('FancyMenu placeholder API is not available yet.');
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
                    'Player: ' + playerName + '\n' +
                    'Uptime (seconds): ' + uptimeSeconds + '\n' +
                    'Second fruit: ' + secondFruit;
            }).catch(error => {
                console.error('Placeholder request failed:', error);
            });
        }
    </script>
</body>
</html>
```

## 6. Best Practices & Notes

- **ตรวจจับ bridge** ก่อนใช้งาน หรือฟัง event `fancymenu-ready`
- **จัดการข้อผิดพลาด** (callbacks สำหรับ [actions](/action-scripts), `.catch` สำหรับ [placeholders](/placeholders)) เพื่อแสดงผลตอบกลับที่เป็นประโยชน์
- **ตรวจสอบอินพุต** ก่อนส่งให้ actions หรือ variables ของ [placeholder](/placeholders)
- **จำกัดอัตราการร้องขอ**; หลีกเลี่ยงการยิง bridge ถี่ ๆ (โดยเฉพาะลูปรีเฟรช placeholders)
- **ความปลอดภัย:** เนื้อหาในเบราว์เซอร์สามารถเรียกใช้ FancyMenu action ที่ลงทะเบียนไว้ได้ทั้งหมด รวมถึง action ที่เกี่ยวกับไฟล์ เครือข่าย คำสั่ง คลิปบอร์ด resource-pack ลิงก์ และออกจากเกม ควรโหลดเฉพาะหน้าเว็บที่เชื่อถือได้ และตรวจสอบข้อมูลทั้งหมดที่รับมาจากเนื้อหาเว็บ

## 7. Troubleshooting

1. ยืนยันว่าเพจถูกโหลดอยู่ใน MCEF browser ที่ FancyMenu ควบคุม
2. ตรวจสอบ JavaScript errors ในคอนโซลของเบราว์เซอร์
3. ตรวจสอบว่า identifier ของ [placeholder](/placeholders) หรือชนิดของ [action](/action-scripts) ถูกต้อง และมีการส่งค่าที่จำเป็นครบถ้วน
4. ตรวจดู Minecraft log (`latest.log`) สำหรับข้อความผิดพลาดของ FancyMenu หากการทำงานล้มเหลวโดยไม่คาดคิด
