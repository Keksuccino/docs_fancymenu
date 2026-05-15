---
title: ตั้งค่า/ดึงค่าตัวเลือก Minecraft
description: >-
  วิธีตั้งค่าและดึงค่าตัวเลือก Minecraft เช่น ระดับเสียง, FOV, ระยะการเรนเดอร์
  ฯลฯ
---

# การใช้งานตัวเลือก Minecraft ใน FancyMenu

FancyMenu ช่วยให้คุณดึงค่าและตั้งค่าการตั้งค่าเกม Minecraft (options) ได้ด้วยองค์ประกอบ UI หลากหลายชนิด คู่มือนี้จะอธิบายวิธีใช้ปุ่ม, สไลเดอร์ และทิกเกอร์ เพื่อทำงานกับตัวเลือก Minecraft ในเลย์เอาต์เมนูแบบกำหนดเองของคุณ

# ทำความเข้าใจตัวเลือก Minecraft

Minecraft มีตัวเลือกในตัวมากมายที่ควบคุมทุกอย่างตั้งแต่การตั้งค่ากราฟิกไปจนถึงระดับเสียง FancyMenu ช่วยให้คุณเข้าถึงตัวเลือกเหล่านี้ได้ด้วยชื่อของมัน

ตัวเลือกที่พบบ่อย ได้แก่:
- `soundCategory_master` - ระดับเสียงหลัก
- `soundCategory_music` - ระดับเสียงเพลง
- `soundCategory_ambient` - ระดับเสียงบรรยากาศ
- `soundCategory_players` - ระดับเสียงผู้เล่น
- `soundCategory_blocks` - ระดับเสียงบล็อก
- `fov` - มุมมองภาพ
- `gamma` - ความสว่าง
- `renderDistance` - ระยะการเรนเดอร์

# การแสดงค่าตัวเลือก

คุณสามารถแสดงค่าปัจจุบันของตัวเลือก Minecraft ใด ๆ ได้โดยใช้ placeholder พิเศษ

รูปแบบของ placeholder คือ:
```
{"placeholder":"minecraft_option_value","values":{"name":"option_name"}}
```

แทนที่ `option_name` ด้วยชื่อตัวเลือกจริงที่คุณต้องการแสดง

# การตั้งค่าตัวเลือกด้วยปุ่ม

สามารถใช้ปุ่มเพื่อตั้งค่าตัวเลขที่แน่นอนให้กับตัวเลือก Minecraft ได้

## วิธีตั้งค่าปุ่ม:

1. สร้างองค์ประกอบ Button ใหม่
2. ตั้งค่าป้ายกำกับของปุ่ม (ข้อความที่แสดงบนปุ่ม)
3. เพิ่ม action: คลิกขวาที่ปุ่ม → Edit Action Script → Add Action → Set Minecraft Option Value
4. ในหน้าต่าง "Set Minecraft Option Value":
   - Name: ใส่ชื่อตัวเลือก (เช่น `renderDistance`)
   - Value: ใส่ค่าที่ต้องการตั้ง (เช่น `16`)

## ตัวอย่าง: 

การสร้างปุ่มที่ตั้งระยะการเรนเดอร์เป็น 16 ชังก์:
- Option Name: `renderDistance`
- Value: `16`
- Label: "ตั้งระยะการเรนเดอร์เป็น 16 ชังก์"

# การตั้งค่าตัวเลือกด้วยสไลเดอร์

สไลเดอร์เหมาะอย่างยิ่งสำหรับตัวเลือกที่มีช่วงค่า เช่น การตั้งค่าระดับเสียงหรือความสว่าง

## วิธีตั้งค่าสไลเดอร์:

1. สร้างองค์ประกอบ Slider ใหม่
2. ตั้งค่าประเภทของสไลเดอร์:
   - สำหรับจำนวนเต็ม (เช่น ระยะการเรนเดอร์): เลือก "Integer Range"
   - สำหรับทศนิยม (เช่น ระดับเสียง): เลือก "Decimal Range"
3. กำหนดค่าต่ำสุดและค่าสูงสุด
4. เพิ่ม action เพื่อกำหนดค่าตัวเลือก Minecraft:
   - คลิกขวา → Edit Action Script → Add Action → Set Minecraft Option Value
   - Name: ชื่อตัวเลือก
   - Value: `$$value` (ตัวแปรพิเศษนี้มีค่าปัจจุบันของสไลเดอร์)
5. ตั้งค่าเริ่มต้นให้เป็นค่าปัจจุบันของตัวเลือก:
   - ตั้ง "Pre-Selected Value" เป็น `{"placeholder":"minecraft_option_value","values":{"name":"option_name"}}`

## รูปแบบป้ายกำกับตัวอย่างของสไลเดอร์:

หากต้องการแสดงค่าปัจจุบันของตัวเลือกในป้ายกำกับสไลเดอร์ ให้ใช้:
```
Volume: {"placeholder":"minecraft_option_value","values":{"name":"soundCategory_master"}}
```

หากต้องการแสดงเป็นเปอร์เซ็นต์ (เหมาะกับระดับเสียง):
```
Volume: {"placeholder":"calc","values":{"expression":"$$value * 100.0","decimal":"false"}}%
```

# การตั้งค่าตัวเลือกด้วยทิกเกอร์

ทิกเกอร์เป็นองค์ประกอบที่มองไม่เห็น ซึ่งสามารถเปลี่ยนตัวเลือกโดยอัตโนมัติตามกำหนดเวลาได้

## วิธีตั้งค่าทิกเกอร์:

1. สร้างองค์ประกอบ Ticker ใหม่
2. ตั้งค่าการทำงานของทิกเกอร์:
   - Tick Mode: เลือกว่าควรอัปเดตตัวเลือกเมื่อใด
   - Tick Delay: ตั้งความถี่ในการอัปเดต (หน่วยเป็นมิลลิวินาที)
3. เพิ่ม action เพื่อกำหนดค่าตัวเลือก Minecraft:
   - คลิกขวา → Edit Action Script → Add Action → Set Minecraft Option Value
   - ตั้งชื่อตัวเลือกและค่า

## ตัวอย่าง:

การตั้ง gamma (ความสว่าง) ให้สูงสุดเมื่อเมนูโหลด:
- Tick Mode: On Load Screen
- Name: `gamma`
- Value: `1.0`

# กรณีใช้งานทั่วไป

นี่คือตัวอย่างการใช้งานทั่วไปเมื่อใช้ FancyMenu เพื่อกำหนดและดึงค่าตัวเลือก Minecraft

## การสร้างสไลเดอร์ปรับระดับเสียงแบบกำหนดเอง

สไลเดอร์ระดับเสียงเป็นการใช้งานที่พบบ่อยสำหรับการเชื่อมกับตัวเลือก Minecraft นี่คือวิธีสร้างสไลเดอร์ปรับระดับเสียงเพลงแบบกำหนดเอง:

1. สร้างองค์ประกอบ Slider ใหม่
2. ตั้งค่า "Slider Type" เป็น "Decimal Range"
3. ตั้งค่า "Minimum Range Value" เป็น "0.0"
4. ตั้งค่า "Maximum Range Value" เป็น "1.0"
5. Edit Action Script → Add Action → Set Minecraft Option Value
   - Set Name เป็น `soundCategory_music`
   - Set Value เป็น `$$value`
6. ตั้งค่า "Pre-Selected Value" เป็น `{"placeholder":"minecraft_option_value","values":{"name":"soundCategory_music"}}`
7. หากต้องการแสดงระดับเสียงเป็นเปอร์เซ็นต์ ให้ตั้งป้ายกำกับเป็น: 
   ```
   Music: {"placeholder":"calc","values":{"expression":"$$value * 100.0","decimal":"false"}}%
   ```

คุณสามารถสร้างสไลเดอร์ลักษณะเดียวกันสำหรับหมวดเสียงอื่น ๆ ได้:
- Master Volume: `soundCategory_master`
- Music: `soundCategory_music`
- Ambient: `soundCategory_ambient`
- Blocks: `soundCategory_blocks`
- Players: `soundCategory_players`
- Weather: `soundCategory_weather`

## การสร้างสไลเดอร์ FOV แบบกำหนดเอง

มุมมองภาพ (FOV) เป็นการตั้งค่ากราฟิกสำคัญที่กำหนดว่ามุมมองของคุณกว้างแค่ไหนในเกม ตัวเลือก FOV ภายในใช้ค่าตั้งแต่ -1.0 ถึง 1.0 แต่จะแสดงเป็น 30 ถึง 110 ใน UI

### ทำความเข้าใจการแมปค่าของ FOV
- ช่วงค่าภายใน: -1.0 ถึง 1.0
- ช่วงค่าที่แสดงผล: 30 ถึง 110
- สูตรการแมป: `(internal_value + 1) * 40 + 30`

### ขั้นตอนที่ 1: สร้าง Ticker Element เพื่ออัปเดตข้อความ FOV

ก่อนอื่น เราต้องสร้างทิกเกอร์ที่ตรวจสอบค่าปัจจุบันของ FOV และตั้งค่าตัวแปรด้วยคำอธิบายที่เหมาะสม:

1. สร้างองค์ประกอบ Ticker ใหม่
2. ตั้งค่า "Tick Mode" เป็น "Normal" (เพื่อให้อัปเดตตลอดเวลา)
3. ตั้งค่า "Tick Delay" ประมาณ "10" (มิลลิวินาที) เพื่อหลีกเลี่ยงการตรวจสอบบ่อยเกินไป

ตอนนี้เราต้องตั้งค่า action สำหรับป้ายกำกับ FOV โครงสร้างของ action script ควรมีลักษณะดังนี้:

```
▶ Action Script
│
├─▶ IF (mapped FOV = 70)
│  └─■ Set Variable Value: fov_text:Normal
│
├─▶ ELSE-IF (mapped FOV = 110)
│  └─■ Set Variable Value: fov_text:Quake Pro
│
└─▶ ELSE
   └─■ Set Variable Value: fov_text:[calculated numeric value]
```

มาตั้งค่าแต่ละส่วนกัน:

#### ตั้งค่าป้ายกำกับ FOV "Normal":
1. คลิกขวา → Edit Action Script → Add Action
2. คลิก "IF Statement" เพื่อเพิ่มบล็อกเงื่อนไข
3. ตั้งเงื่อนไขเป็น "Is Number" โดยใช้:
   - Compare Mode: "equals"
   - Number: `{"placeholder":"calc","values":{"decimal":"false","expression":"({"placeholder":"minecraft_option_value","values":{"name":"fov"}} + 1) * 40 + 30"}}`
   - Compare With: "70"
4. ภายในบล็อก IF นี้ ให้เพิ่ม action "Set Variable Value (FM Variable)" โดยใช้:
   - Value: `fov_text:Normal`

#### ตั้งค่าป้ายกำกับ FOV "Quake Pro":
1. ภายใน Action Script ให้เพิ่ม "ELSE-IF Statement"
2. ตั้งเงื่อนไขเป็น "Is Number" โดยใช้:
   - Compare Mode: "equals"
   - Number: `{"placeholder":"calc","values":{"decimal":"false","expression":"({"placeholder":"minecraft_option_value","values":{"name":"fov"}} + 1) * 40 + 30"}}`
   - Compare With: "110"
3. ภายในบล็อก ELSE-IF นี้ ให้เพิ่ม action "Set Variable Value (FM Variable)" โดยใช้:
   - Value: `fov_text:Quake Pro`

#### ตั้งค่าป้ายกำกับ FOV แบบตัวเลข:
1. เพิ่มบล็อก "ELSE Statement"
2. ภายในบล็อก ELSE นี้ ให้เพิ่ม action "Set Variable Value (FM Variable)" โดยใช้:
   - Value: `fov_text:{"placeholder":"calc","values":{"decimal":"false","expression":"({"placeholder":"minecraft_option_value","values":{"name":"fov"}} + 1) * 40 + 30"}}`

<img src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/fov_slider_action_script.png" alt="FOV Slider Action Script" style="max-width: 600px; height: auto;">

### ขั้นตอนที่ 2: สร้างสไลเดอร์ FOV

1. สร้างองค์ประกอบ Slider ใหม่
2. ตั้งค่า "Slider Type" เป็น "Decimal Range"
3. ตั้งค่า "Minimum Range Value" เป็น "-1.0"
4. ตั้งค่า "Maximum Range Value" เป็น "1.0"
5. Edit Action Script → Add Action → Set Minecraft Option Value
   - Set Name เป็น `fov`
   - Set Value เป็น `$$value`
6. ตั้งค่า "Pre-Selected Value" เป็น `{"placeholder":"minecraft_option_value","values":{"name":"fov"}}`

### ขั้นตอนที่ 3: ตั้งค่าป้ายกำกับของสไลเดอร์

ตั้งป้ายกำกับสไลเดอร์ให้แสดงตัวแปรข้อความ FOV โดยตรง:

```
FOV: {"placeholder":"getvariable","values":{"name":"fov_text"}}
```

ป้ายกำกับนี้จะแสดง:
- "FOV: Normal" เมื่อค่าเป็น 70
- "FOV: Quake Pro" เมื่อค่าเป็น 110  
- "FOV: 85" (หรือเลขอื่น ๆ) สำหรับค่าอื่นทั้งหมด

### เคล็ดลับสำหรับสไลเดอร์ FOV

- ช่วงค่าภายในของสไลเดอร์คือ -1.0 ถึง 1.0 ซึ่งต้องแมปไปเป็น 30 ถึง 110 เพื่อแสดงผล
- สูตรการแปลงคือ: `(internal_value + 1) * 40 + 30`
- มีเพียงสองค่าที่มีป้ายกำกับพิเศษ: 70 (Normal) และ 110 (Quake Pro)
- FOV เริ่มต้นใน Minecraft คือ 70 (ซึ่งตรงกับค่าภายใน 0.0)
- ตัวแปร `fov_text` จะมีทั้งป้ายกำกับพิเศษหรือค่าตัวเลขโดยอัตโนมัติ

## การแสดงค่าตัวเลือกในองค์ประกอบข้อความ

คุณยังสามารถแสดงค่าปัจจุบันของตัวเลือกในองค์ประกอบ Text ได้ด้วย:

1. สร้างองค์ประกอบ Text ใหม่
2. สำหรับเนื้อหาข้อความ ให้ใช้ placeholder: `{"placeholder":"minecraft_option_value","values":{"name":"option_name"}}`

ตัวอย่างเช่น หากต้องการแสดงระยะการเรนเดอร์ปัจจุบัน:
```
Current render distance: {"placeholder":"minecraft_option_value","values":{"name":"renderDistance"}} chunks
```

# การค้นหาชื่อตัวเลือก

คุณสามารถหาชื่อของตัวเลือกทั้งหมดที่มีได้โดย:

  1. สร้างปุ่ม
  2. คลิกขวาที่ปุ่ม
  3. คลิก "Edit Action Script"
  4. เพิ่ม action "Set Minecraft Option Value"
  5. เมื่อแก้ไขค่าของ action ให้ดูคำแนะนำจากดรอปดาวน์เมื่อคุณเริ่มพิมพ์ในช่อง "Name"
  
# เคล็ดลับสำคัญ

- **ค่าที่ใช้ได้**: ไม่ใช่ทุกตัวเลือกจะยอมรับค่าทุกแบบ ตัวอย่างเช่น:
  - ตัวเลือกระดับเสียงยอมรับค่าตั้งแต่ 0.0 ถึง 1.0
  - ระยะการเรนเดอร์โดยทั่วไปยอมรับจำนวนเต็มตั้งแต่ 2 ถึง 32
  - ตัวเลือกแบบบูลีน (true/false) เช่น `pauseOnLostFocus` ยอมรับ "true" หรือ "false"

- **การทดสอบ**: ควรทดสอบการตั้งค่าของคุณเสมอเพื่อให้แน่ใจว่าทำงานได้ตามที่คาดไว้!

- **การตอบสนองเชิงภาพ**: ควรให้ผู้ใช้เห็นค่าปัจจุบันอย่างชัดเจนด้วย placeholder ที่อธิบายไว้ข้างต้น
