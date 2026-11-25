---
title: การแชร์ข้อมูลระหว่างไคลเอนต์กับเซิร์ฟเวอร์
description: ส่งและรับข้อมูลที่กำหนดเองระหว่างเซิร์ฟเวอร์กับไคลเอนต์ด้วย FancyMenu
sourceBlobSha: 35ae4605e43ac917f11c24e5d97a5c311c9aa01a
---

# FM Data

ระบบ "FM Data" ช่วยให้คุณส่งข้อความข้อมูลที่กำหนดเองระหว่างเซิร์ฟเวอร์กับไคลเอนต์ได้

คำสั่งย่อย `/fmdata` ทุกคำสั่งต้องใช้ **ระดับสิทธิ์ 2** (Game Master / OP ระดับ 2)

ข้อความ FM Data ทุกข้อความประกอบด้วย:

1. **ตัวระบุข้อมูล** (ข้อความนี้เป็นข้อมูลประเภทใด)
2. **ค่าข้อมูล** (เนื้อหาจริง)

ตัวอย่าง:

- ตัวระบุ: `hud.food`
- ข้อมูล: `18/20`

# เริ่มต้นใช้งานอย่างรวดเร็ว

1. เซิร์ฟเวอร์ส่งข้อมูลด้วย `/fmdata send ...`
2. ไคลเอนต์รับข้อมูลด้วยตัวฟัง FancyMenu **On FM Data Received**
3. ไคลเอนต์ยังส่งข้อมูลกลับได้ด้วยแอ็กชัน **Send FM Data To Server**
4. เซิร์ฟเวอร์ตอบสนองโดยอัตโนมัติได้ด้วย `/fmdata listener ...`
5. เซิร์ฟเวอร์ส่งข้อมูลโดยอัตโนมัติเมื่อผู้เล่นเข้าร่วมได้ด้วย `/fmdata welcome_data ...`

# เซิร์ฟเวอร์ -> ไคลเอนต์

ใช้คำสั่ง:

```mcfunction
/fmdata send <target_players> <data_identifier> <string_data>
```

ตัวอย่าง:

```mcfunction
/fmdata send Player761 hud.food 18/20
/fmdata send @a "food value update" "18 of 20"
```

หมายเหตุ:

- `<target_players>` รองรับชื่อผู้เล่นและตัวเลือก เช่น `@a`, `@p` และ `@s`
- ใช้เครื่องหมายอัญประกาศครอบค่าที่มีช่องว่าง

# ไคลเอนต์: รับข้อมูล

ใช้ตัวฟัง FancyMenu:

- **On FM Data Received**

ตัวแปรที่ใช้ได้:

- `$$data_identifier`
- `$$data`
- `$$sent_by`

ค่า `$$sent_by` คือ:

- IP ของเซิร์ฟเวอร์ในโหมดผู้เล่นหลายคน
- `integrated_server` ในโหมดผู้เล่นคนเดียว

กรณีใช้งานทั่วไป:

- อัปเดตองค์ประกอบข้อความ
- เรียกใช้แอ็กชันของเมนู
- เรียกใช้ตรรกะตามตัวระบุ/ข้อมูลที่ได้รับ

# ไคลเอนต์ -> เซิร์ฟเวอร์

ใช้แอ็กชัน FancyMenu:

- **Send FM Data To Server**

แอ็กชันนี้มีช่องกรอก 2 ช่อง:

1. ตัวระบุข้อมูล
2. ข้อมูล

จากนั้นเซิร์ฟเวอร์จะประมวลผลข้อมูลขาเข้าด้วย `/fmdata listener ...` ได้

# ตัวฟังของเซิร์ฟเวอร์

ตัวฟังของเซิร์ฟเวอร์จะรอฟังข้อมูลขาเข้าจากไคลเอนต์ และสามารถเรียกใช้คำสั่งหนึ่งคำสั่งหรือหลายคำสั่งเมื่อถูกเรียกใช้

ตัวฟังของเซิร์ฟเวอร์จะถูกบันทึกและยังทำงานต่อหลังจากรีสตาร์ต

จัดการตัวฟังด้วยคำสั่ง:

- `/fmdata listener list`
- `/fmdata listener add ...`
- `/fmdata listener edit ...`
- `/fmdata listener remove ...`

## รูปแบบคำสั่ง Add / Edit

```mcfunction
/fmdata listener add <unique_listener_name> <matching_type_identifier> <matching_type_data> <ignore_case_identifier> <ignore_case_data> <fire_for_player> <listen_for_identifier> <listen_for_data> <commands_to_execute_on_fire>
```

```mcfunction
/fmdata listener edit <listener_name> <matching_type_identifier> <matching_type_data> <ignore_case_identifier> <ignore_case_data> <fire_for_player> <listen_for_identifier> <listen_for_data> <commands_to_execute_on_fire>
```

## รูปแบบคำสั่ง Remove

```mcfunction
/fmdata listener remove <listener_name>
```

## ประเภทการจับคู่

`matching_type_identifier` และ `matching_type_data` เลือกได้ดังนี้:

- `equals`
- `contains`
- `starts_with`
- `ends_with`

## กฎการจับคู่

- `ignore_case_identifier` และ `ignore_case_data` เป็นตัวเลือก true/false
- `listen_for_identifier` รองรับอักขระตัวแทน `*` (จับคู่เสมอ)
- `listen_for_data` รองรับอักขระตัวแทน `*` (จับคู่เสมอ)
- `fire_for_player` ใช้ตัวเลือกผู้เล่นตามปกติ (เช่น `@a`, `@p`, `Player761`)

## คำสั่งเมื่อถูกเรียกใช้

`commands_to_execute_on_fire` เป็นช่องข้อความช่องเดียว

- คั่นคำสั่งหลายคำสั่งด้วย `|||`
- ใส่ `\|\|\|` เพื่อใช้ตัวคั่นตามตัวอักษร

คุณสามารถใช้ตัวแทนพิเศษสองตัวนี้ได้ โดยระบบจะแทนค่าก่อนเรียกใช้คำสั่ง:

- `%fm_sender%` -> ผู้เล่นที่ส่ง FM Data
- `%fm_data%` -> ค่าข้อมูลที่ได้รับจากไคลเอนต์

คำสั่งจะทำงานในฐานะคำสั่งของเซิร์ฟเวอร์

## ตัวอย่างคำสั่ง

ตอบสนองเมื่อผู้เล่นคนใดกดปุ่ม:

```mcfunction
/fmdata listener add button_ping equals equals false false @a ui.button pressed "tellraw @a {\"text\":\"%fm_sender% pressed the button\"}"
```

เรียกใช้หลายคำสั่งเมื่อข้อมูลมีคำว่า `gold`:

```mcfunction
/fmdata listener add reward equals contains false true @a reward "gold" "say Reward from %fm_sender%: %fm_data%|||effect give %fm_sender% minecraft:speed 3 1 true"
```

# Welcome Data

Welcome data จะส่ง FM Data ให้ผู้เล่นที่ตรงเงื่อนไขเมื่อเข้าร่วม

จัดการรายการด้วยคำสั่ง:

- `/fmdata welcome_data list`
- `/fmdata welcome_data add ...`
- `/fmdata welcome_data edit ...`
- `/fmdata welcome_data remove ...`

## รูปแบบคำสั่ง Add / Edit

```mcfunction
/fmdata welcome_data add <unique_welcome_data_name> <target_player> <data_identifier> <string_data>
```

```mcfunction
/fmdata welcome_data edit <welcome_data_name> <target_player> <data_identifier> <string_data>
```

## รูปแบบคำสั่ง Remove

```mcfunction
/fmdata welcome_data remove <welcome_data_name>
```

หมายเหตุ:

- `<target_player>` รองรับตัวเลือกทั่วไป เช่น `@a`, `@p`, `@s`
- ระบบจะส่งข้อมูลให้ผู้เล่นที่ตรงเงื่อนไขเมื่อเข้าร่วม
- รายการจะถูกบันทึกและโหลดโดยอัตโนมัติ

## ตัวอย่างคำสั่ง

ส่ง welcome data ให้ผู้เล่นทุกคนที่เข้าร่วม:

```mcfunction
/fmdata welcome_data add welcome_all @a hud.welcome "Welcome!"
```

ส่ง welcome data ให้ผู้เล่นเพียงคนเดียว:

```mcfunction
/fmdata welcome_data add welcome_vip Player761 hud.vip "VIP perks enabled"
```

# ส่งออกสำหรับ AI

หากต้องการขอความช่วยเหลือจาก Alice หรือ AI ตัวอื่น ให้ส่งออกตัวฟังและ welcome data ของเซิร์ฟเวอร์ด้วย [ส่งออกสำหรับ AI](/export-for-ai#servers):

```mcfunction
/fmdata export_for_ai copy
/fmdata export_for_ai file
```

`copy` จะส่งข้อความแชตที่คัดลอกข้อมูลส่งออกได้เมื่อคลิก ส่วน `file` จะบันทึกข้อมูลไว้บนเซิร์ฟเวอร์ใน `fancymenu_data/ai_exports/`

# แนวทางปฏิบัติที่ดี

1. ใช้ตัวระบุที่ชัดเจน เช่น `hud.food`, `menu.shop.open`, `quest.progress`
2. ใช้รูปแบบข้อมูลให้สอดคล้องกันสำหรับตัวระบุแต่ละรายการ
3. เริ่มจากเรื่องง่าย: ทดสอบด้วย `/fmdata send` ก่อนสร้างตัวฟังที่ซับซ้อน
4. ใช้ `@a` เฉพาะเมื่อต้องการให้มีผลกับผู้เล่นทุกคนจริง ๆ
5. ใช้ `/fmdata listener list` และ `/fmdata welcome_data list` เพื่อจัดระเบียบการตั้งค่า
