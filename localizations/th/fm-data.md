---
title: การแชร์ข้อมูลระหว่าง Client < - > Server
description: ส่งและรับข้อมูลแบบกำหนดเองระหว่างเซิร์ฟเวอร์และไคลเอนต์ด้วย FancyMenu.
---

# FM Data

ระบบ "FM Data" ช่วยให้คุณส่งข้อมูลข้อความแบบกำหนดเองระหว่างเซิร์ฟเวอร์และไคลเอนต์ได้

ข้อความ FM Data ทุกข้อความจะมี:

1. **ตัวระบุข้อมูล** (บอกว่านี่คือข้อความประเภทใด)
2. **ค่าข้อมูล** (เนื้อหาจริง)

ตัวอย่างแนวคิด:

- ตัวระบุ: `hud.food`
- ข้อมูล: `18/20`

# เริ่มใช้งานอย่างรวดเร็ว

1. เซิร์ฟเวอร์ส่งข้อมูลด้วย `/fmdata send ...`
2. ไคลเอนต์รับด้วย listener ของ FancyMenu **On FM Data Received**
3. ไคลเอนต์สามารถส่งข้อมูลกลับได้ด้วยแอ็กชัน **Send FM Data To Server**
4. เซิร์ฟเวอร์สามารถตอบสนองอัตโนมัติด้วย `/fmdata listener ...`
5. เซิร์ฟเวอร์สามารถส่งข้อมูลอัตโนมัติเมื่อผู้เล่นเข้าร่วมด้วย `/fmdata welcome_data ...`

# เซิร์ฟเวอร์ -> ไคลเอนต์

ใช้:

```mcfunction
/fmdata send <target_player> <data_identifier> <string_data>
```

ตัวอย่าง:

```mcfunction
/fmdata send Player761 hud.food 18/20
/fmdata send @a "food value update" "18 of 20"
```

หมายเหตุ:

- `<target_player>` รองรับตัวเลือกผู้เล่นปกติ เช่น `@a`, `@p`, `@s`
- ใช้เครื่องหมายอัญประกาศสำหรับค่าที่มีช่องว่าง

# ไคลเอนต์: รับข้อมูล

ใช้ listener ของ FancyMenu:

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

# ไคลเอนต์ -> เซิร์ฟเวอร์

ใช้แอ็กชันของ FancyMenu:

- **Send FM Data To Server**

แอ็กชันนี้มีอินพุต 2 ช่อง:

1. Data Identifier
2. Data

จากนั้นเซิร์ฟเวอร์สามารถประมวลผลข้อมูลที่เข้ามาด้วย `/fmdata listener ...`

# Server Listeners

Server listener จะฟังข้อมูลที่เข้ามาจากไคลเอนต์ และสามารถรันหนึ่งคำสั่งหรือหลายคำสั่งเมื่อถูกทริกเกอร์

Server listener จะถูกบันทึกไว้และยังคงทำงานต่อหลังจากรีสตาร์ต

จัดการด้วย:

- `/fmdata listener list`
- `/fmdata listener add ...`
- `/fmdata listener edit ...`
- `/fmdata listener remove ...`

## รูปแบบการเพิ่ม / แก้ไข

```mcfunction
/fmdata listener add <unique_listener_name> <matching_type_identifier> <matching_type_data> <ignore_case_identifier> <ignore_case_data> <fire_for_player> <listen_for_identifier> <listen_for_data> <commands_to_execute_on_fire>
```

```mcfunction
/fmdata listener edit <listener_name> <matching_type_identifier> <matching_type_data> <ignore_case_identifier> <ignore_case_data> <fire_for_player> <listen_for_identifier> <listen_for_data> <commands_to_execute_on_fire>
```

## รูปแบบการลบ

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

- `ignore_case_identifier` และ `ignore_case_data` เป็นสวิตช์ true/false
- `listen_for_identifier` รองรับ wildcard `*` (ตรงเสมอ)
- `listen_for_data` รองรับ wildcard `*` (ตรงเสมอ)
- `fire_for_player` ใช้ตัวเลือกผู้เล่นปกติ (เช่น `@a`, `@p`, `Player761`)

## คำสั่งเมื่อถูกทริกเกอร์

`commands_to_execute_on_fire` เป็นช่องป้อนข้อความเดียว

- แยกหลายคำสั่งด้วย `|||`
- ถ้าต้องการใช้ตัวคั่นจริงแบบตัวอักษร ให้ escape เป็น `\|\|\|`

คุณสามารถใช้ตัวแทนพิเศษ 2 ตัวนี้ ซึ่งจะถูกแทนค่าทันทีก่อนรันคำสั่ง:

- `%fm_sender%` -> ผู้เล่นที่ส่ง FM Data
- `%fm_data%` -> ค่าข้อมูลที่ได้รับจากไคลเอนต์

คำสั่งจะรันในฐานะคำสั่งของเซิร์ฟเวอร์

## ตัวอย่างคำสั่ง

ตอบสนองต่อการกดปุ่มจากผู้เล่นใดก็ได้:

```mcfunction
/fmdata listener add button_ping equals equals false false @a ui.button pressed "tellraw @a {\"text\":\"%fm_sender% pressed the button\"}"
```

รันหลายคำสั่งเมื่อข้อมูลมี `gold`:

```mcfunction
/fmdata listener add reward equals contains false true @a reward "gold" "say Reward from %fm_sender%: %fm_data%|||effect give %fm_sender% minecraft:speed 3 1 true"
```

# Welcome Data

Welcome data จะส่ง FM Data ไปยังผู้เล่นที่ตรงเงื่อนไขเมื่อพวกเขาเข้าร่วม

จัดการรายการด้วย:

- `/fmdata welcome_data list`
- `/fmdata welcome_data add ...`
- `/fmdata welcome_data edit ...`
- `/fmdata welcome_data remove ...`

## รูปแบบการเพิ่ม / แก้ไข

```mcfunction
/fmdata welcome_data add <unique_welcome_data_name> <target_player> <data_identifier> <string_data>
```

```mcfunction
/fmdata welcome_data edit <welcome_data_name> <target_player> <data_identifier> <string_data>
```

## รูปแบบการลบ

```mcfunction
/fmdata welcome_data remove <welcome_data_name>
```

หมายเหตุ:

- `<target_player>` รองรับตัวเลือกปกติ เช่น `@a`, `@p`, `@s`
- ข้อมูลจะถูกส่งให้ผู้เล่นที่ตรงเงื่อนไขเมื่อพวกเขาเข้าร่วม
- รายการจะถูกบันทึกและโหลดอัตโนมัติ

## ตัวอย่างคำสั่ง

ส่ง welcome data ให้ผู้เล่นทุกคนที่เข้าร่วม:

```mcfunction
/fmdata welcome_data add welcome_all @a hud.welcome "Welcome!"
```

ส่ง welcome data ให้ผู้เล่นเพียงคนเดียว:

```mcfunction
/fmdata welcome_data add welcome_vip Player761 hud.vip "VIP perks enabled"
```

# แนวทางปฏิบัติที่ดีที่สุด

1. ใช้ตัวระบุที่ชัดเจน เช่น `hud.food`, `menu.shop.open`, `quest.progress`
2. รักษารูปแบบข้อมูลให้สม่ำเสมอสำหรับตัวระบุแต่ละตัว
3. เริ่มจากสิ่งง่าย ๆ: ทดสอบด้วย `/fmdata send` ก่อนสร้าง listener ที่ซับซ้อน
4. ใช้ `@a` เฉพาะเมื่อคุณต้องการให้มีผลกับทุกคนจริง ๆ
5. ใช้ `/fmdata listener list` และ `/fmdata welcome_data list` เพื่อให้การตั้งค่าดูเป็นระเบียบ
