---
title: การแชร์ข้อมูลระหว่าง Client < - > Server
description: ส่งและรับข้อมูลแบบกำหนดเองระหว่างเซิร์ฟเวอร์และไคลเอนต์ด้วย FancyMenu.
---

# FM Data

ระบบ "FM Data" ช่วยให้คุณส่งข้อมูลข้อความแบบกำหนดเองระหว่างเซิร์ฟเวอร์และไคลเอนต์ได้

ทุกคำสั่งย่อยของ `/fmdata` ต้องใช้ **ระดับสิทธิ์ 2** (Game Master / OP ระดับ 2)

ข้อความ FM Data ทุกข้อความมี:

1. **ตัวระบุข้อมูล** (ข้อความนี้เป็นข้อมูลประเภทไหน)
2. **ค่าข้อมูล** (เนื้อหาจริง)

ตัวอย่างแนวคิด:

- ตัวระบุ: `hud.food`
- ข้อมูล: `18/20`

# เริ่มใช้งานอย่างรวดเร็ว

1. เซิร์ฟเวอร์ส่งข้อมูลด้วย `/fmdata send ...`
2. ไคลเอนต์รับข้อมูลด้วยตัวฟัง FancyMenu **On FM Data Received**
3. ไคลเอนต์สามารถส่งข้อมูลกลับได้ด้วยแอ็กชัน **Send FM Data To Server**
4. เซิร์ฟเวอร์สามารถตอบสนองอัตโนมัติด้วย `/fmdata listener ...`
5. เซิร์ฟเวอร์สามารถส่งข้อมูลต้อนรับอัตโนมัติเมื่อเข้าเกมด้วย `/fmdata welcome_data ...`

# Server -> Client

ใช้:

```mcfunction
/fmdata send <target_players> <data_identifier> <string_data>
```

ตัวอย่าง:

```mcfunction
/fmdata send Player761 hud.food 18/20
/fmdata send @a "food value update" "18 of 20"
```

หมายเหตุ:

- `<target_players>` รองรับชื่อผู้เล่นและตัวเลือก เช่น `@a`, `@p`, และ `@s`
- ใช้เครื่องหมายอัญประกาศกับค่าที่มีช่องว่าง

# Client: รับข้อมูล

ใช้ตัวฟัง FancyMenu:

- **On FM Data Received**

ตัวแปรที่ใช้ได้:

- `$$data_identifier`
- `$$data`
- `$$sent_by`

`$$sent_by` คือ:

- IP ของเซิร์ฟเวอร์ในโหมดผู้เล่นหลายคน
- `integrated_server` ในโหมดผู้เล่นคนเดียว

กรณีใช้งานที่พบบ่อย:

- อัปเดตองค์ประกอบข้อความ
- ทริกเกอร์แอ็กชันของเมนู
- รันตรรกะตามตัวระบุ/ข้อมูลที่เข้ามา

# Client -> Server

ใช้แอ็กชัน FancyMenu:

- **Send FM Data To Server**

แอ็กชันนี้มีอินพุต 2 ช่อง:

1. Data Identifier
2. Data

จากนั้นเซิร์ฟเวอร์สามารถประมวลผลข้อมูลที่เข้ามาด้วย `/fmdata listener ...`

# Server Listeners

Server listeners จะเฝ้าฟังข้อมูลที่ส่งมาจากไคลเอนต์ และสามารถรันคำสั่งหนึ่งคำสั่งหรือหลายคำสั่งเมื่อถูกทริกเกอร์ได้

Server listeners จะถูกบันทึกไว้และยังคงทำงานต่อหลังรีสตาร์ท

จัดการด้วย:

- `/fmdata listener list`
- `/fmdata listener add ...`
- `/fmdata listener edit ...`
- `/fmdata listener remove ...`

## ไวยากรณ์ Add / Edit

```mcfunction
/fmdata listener add <unique_listener_name> <matching_type_identifier> <matching_type_data> <ignore_case_identifier> <ignore_case_data> <fire_for_player> <listen_for_identifier> <listen_for_data> <commands_to_execute_on_fire>
```

```mcfunction
/fmdata listener edit <listener_name> <matching_type_identifier> <matching_type_data> <ignore_case_identifier> <ignore_case_data> <fire_for_player> <listen_for_identifier> <listen_for_data> <commands_to_execute_on_fire>
```

## ไวยากรณ์ Remove

```mcfunction
/fmdata listener remove <listener_name>
```

## ประเภทการจับคู่

`matching_type_identifier` และ `matching_type_data` สามารถเป็น:

- `equals`
- `contains`
- `starts_with`
- `ends_with`

## กฎการจับคู่

- `ignore_case_identifier` และ `ignore_case_data` เป็นตัวเลือกเปิด/ปิดแบบ true/false
- `listen_for_identifier` รองรับไวลด์การ์ด `*` (ตรงเสมอ)
- `listen_for_data` รองรับไวลด์การ์ด `*` (ตรงเสมอ)
- `fire_for_player` ใช้ตัวเลือกผู้เล่นตามปกติ (เช่น `@a`, `@p`, `Player761`)

## Commands On Fire

`commands_to_execute_on_fire` เป็นช่องข้อความเพียงช่องเดียว

- แยกหลายคำสั่งด้วย `|||`
- หากต้องการใช้ตัวคั่นแบบตัวอักษรจริง ให้ escape เป็น `\|\|\|`

คุณสามารถใช้ placeholder พิเศษ 2 ตัวนี้ได้ ซึ่งจะถูกแทนค่าทันทีก่อนรันคำสั่ง:

- `%fm_sender%` -> ผู้เล่นที่ส่ง FM Data
- `%fm_data%` -> ค่าข้อมูลที่ได้รับจากไคลเอนต์

คำสั่งจะถูกรันในฐานะคำสั่งของเซิร์ฟเวอร์

## ตัวอย่างคำสั่ง

ตอบสนองต่อการกดปุ่มจากผู้เล่นใดก็ได้:

```mcfunction
/fmdata listener add button_ping equals equals false false @a ui.button pressed "tellraw @a {\"text\":\"%fm_sender% pressed the button\"}"
```

รันหลายคำสั่งเมื่อข้อมูลมีคำว่า `gold`:

```mcfunction
/fmdata listener add reward equals contains false true @a reward "gold" "say Reward from %fm_sender%: %fm_data%|||effect give %fm_sender% minecraft:speed 3 1 true"
```

# Welcome Data

Welcome data จะส่ง FM Data ไปยังผู้เล่นที่ตรงเงื่อนไขเมื่อพวกเขาเข้าร่วมเกม

จัดการรายการด้วย:

- `/fmdata welcome_data list`
- `/fmdata welcome_data add ...`
- `/fmdata welcome_data edit ...`
- `/fmdata welcome_data remove ...`

## ไวยากรณ์ Add / Edit

```mcfunction
/fmdata welcome_data add <unique_welcome_data_name> <target_player> <data_identifier> <string_data>
```

```mcfunction
/fmdata welcome_data edit <welcome_data_name> <target_player> <data_identifier> <string_data>
```

## ไวยากรณ์ Remove

```mcfunction
/fmdata welcome_data remove <welcome_data_name>
```

หมายเหตุ:

- `<target_player>` รองรับตัวเลือกปกติ เช่น `@a`, `@p`, `@s`
- ข้อมูลจะถูกส่งไปยังผู้เล่นที่ตรงเงื่อนไขเมื่อพวกเขาเข้าร่วม
- รายการจะถูกบันทึกและโหลดอัตโนมัติ

## ตัวอย่างคำสั่ง

ส่ง welcome data ไปยังผู้เล่นทุกคนที่เข้าเกม:

```mcfunction
/fmdata welcome_data add welcome_all @a hud.welcome "Welcome!"
```

ส่ง welcome data ให้เฉพาะผู้เล่นคนเดียว:

```mcfunction
/fmdata welcome_data add welcome_vip Player761 hud.vip "VIP perks enabled"
```

# แนวทางที่ดีที่สุด

1. ใช้ตัวระบุที่ชัดเจน เช่น `hud.food`, `menu.shop.open`, `quest.progress`
2. รักษารูปแบบข้อมูลให้สม่ำเสมอสำหรับตัวระบุแต่ละตัว
3. เริ่มจากแบบง่าย: ทดสอบด้วย `/fmdata send` ก่อนสร้าง listener ที่ซับซ้อน
4. ใช้ `@a` เฉพาะเมื่อคุณต้องการให้มีผลกับทุกคนจริง ๆ
5. ใช้ `/fmdata listener list` และ `/fmdata welcome_data list` เพื่อให้การตั้งค่ามีความเป็นระเบียบ
