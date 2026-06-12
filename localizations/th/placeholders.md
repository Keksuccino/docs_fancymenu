---
title: ตัวยึดตำแหน่ง
description: วิธีใช้งานตัวยึดตำแหน่ง
---
# ตัวยึดตำแหน่ง

ตัวยึดตำแหน่งคือค่าที่เปลี่ยนแปลงได้และจะถูกแทนที่ด้วยเนื้อหาจริงเมื่อมีการใช้งาน ใน FancyMenu ตัวยึดตำแหน่งช่วยให้คุณแทรกเนื้อหาแบบไดนามิกลงในองค์ประกอบต่าง ๆ เช่น ข้อความ ปุ่ม และเงื่อนไขการโหลด ลองมองว่ามันเป็นตัวแปรที่ถูกประมวลผลและแทนที่ด้วยค่าจริงเมื่อเลย์เอาต์ของคุณแสดงผล

# ข้อมูลทั่วไป

## ไวยากรณ์พื้นฐาน
ตัวยึดตำแหน่งใน FancyMenu ใช้ไวยากรณ์คล้าย JSON:
```
{"placeholder":"modversion","values":{"modid":"fancymenu"}}
```

ตัวอย่างเช่น หากต้องการแสดงชื่อผู้เล่น:
```
{"placeholder":"playername"}
```

## การซ้อนตัวยึดตำแหน่ง
หนึ่งในฟีเจอร์ที่ทรงพลังที่สุดของระบบตัวยึดตำแหน่งของ FancyMenu คือการซ้อนตัวยึดตำแหน่งไว้ภายในตัวยึดตำแหน่งอื่นได้ ซึ่งหมายความว่าคุณสามารถใช้ผลลัพธ์ของตัวยึดตำแหน่งหนึ่งเป็นอินพุตของอีกตัวหนึ่งได้

ตัวอย่างตัวยึดตำแหน่งแบบซ้อน:
```
{"placeholder":"calc","values":{"decimal":"true","expression":"{"placeholder":"maxram"} / 1024"}}
```
ตัวอย่างนี้นำค่าหน่วยความจำ RAM สูงสุดมาหารด้วย 1024 เพื่อแปลงจาก MB เป็น GB

> [!IMPORTANT]
> ไม่เหมือน JSON จริง ตัวยึดตำแหน่งแบบซ้อนไม่ได้ถูก **escape** ด้วย `\` การละเว้นนี้สำคัญมาก เพราะตัวยึดตำแหน่งจะหยุดทำงานเมื่อถูก escape (ซึ่งก็สมเหตุสมผล) ตัวยึดตำแหน่งใช้เพียงไวยากรณ์ที่คล้าย JSON เท่านั้น มันไม่ใช่ JSON จริง

# การใช้งานตัวยึดตำแหน่ง

องค์ประกอบส่วนใหญ่ที่มีช่องป้อนข้อความรองรับตัวยึดตำแหน่ง คุณสามารถดูได้ว่าช่องป้อนข้อความรองรับตัวยึดตำแหน่งหรือไม่ตอนกำลังแก้ไข ถ้าตัวแก้ไข **ข้อความ** แบบเต็มหน้าจอเปิดขึ้นเมื่อแก้ไขข้อความ แสดงว่ารองรับตัวยึดตำแหน่ง

หากต้องการดู **รายการตัวยึดตำแหน่งทั้งหมด** เพียงคลิกปุ่ม **Placeholders** ที่ **มุมขวาบน** ของ **ตัวแก้ไขข้อความ**

ด้านบนของรายการตัวยึดตำแหน่งจะมี **แถบค้นหา** ให้คุณค้นหาตัวยึดตำแหน่งได้

เมื่อคลิกตัวยึดตำแหน่งในรายการ ระบบจะวางมันลงในเนื้อหาข้อความ

# รายละเอียดตัวยึดตำแหน่ง

รายการนี้ประกอบด้วยตัวยึดตำแหน่งส่วนใหญ่หรือทั้งหมดที่มีใน FancyMenu รายการนี้อาจล้าสมัยได้บ้างเมื่อมีการอัปเดตของม็อด

## ชื่อผู้เล่น (playername)
คืนชื่อผู้ใช้ของผู้เล่นปัจจุบัน
```
{"placeholder":"playername"}
```
ตัวอย่างผลลัพธ์: `Steve`

## UUID ของผู้เล่น (playeruuid)
คืนตัวระบุเฉพาะของผู้เล่น
```
{"placeholder":"playeruuid"}
```
ตัวอย่างผลลัพธ์: `c8cde7fe-7ced-11eb-9439-0242ac130002`

## เวอร์ชัน Minecraft (mcversion)
คืนเวอร์ชัน Minecraft ปัจจุบัน
```
{"placeholder":"mcversion"}
```
ตัวอย่างผลลัพธ์: `1.19.2`

## เวอร์ชันตัวโหลดม็อด (loaderver)
คืนเวอร์ชันของตัวโหลดม็อด (Forge/Fabric)
```
{"placeholder":"loaderver"}
```
ตัวอย่างผลลัพธ์: `43.2.0`

## ชื่อตัวโหลดม็อด (loadername)
คืนชื่อตัวโหลดม็อด
```
{"placeholder":"loadername"}
```
ตัวอย่างผลลัพธ์: `Forge`

## เวอร์ชันม็อด (modversion)
คืนเวอร์ชันของม็อดที่ระบุ
```
{"placeholder":"modversion","values":{"modid":"fancymenu"}}
```
ตัวอย่างผลลัพธ์: `2.14.9`

## จำนวนม็อดทั้งหมด (totalmods)
คืนจำนวนม็อดที่ติดตั้งทั้งหมด
```
{"placeholder":"totalmods"}
```
ตัวอย่างผลลัพธ์: `45`

## จำนวนม็อดที่โหลดอยู่ (loadedmods)
คืนจำนวนม็อดที่กำลังโหลดอยู่
```
{"placeholder":"loadedmods"}
```
ตัวอย่างผลลัพธ์: `43`

## ความคืบหน้าการโหลดโลก (world_load_progress)
คืนความคืบหน้าการโหลดโลกปัจจุบันเป็นเปอร์เซ็นต์
```
{"placeholder":"world_load_progress"}
```
ตัวอย่างผลลัพธ์: `75`

## ค่าตัวเลือก Minecraft (minecraft_option_value)
คืนค่าของตัวเลือก Minecraft
```
{"placeholder":"minecraft_option_value","values":{"name":"fov"}}
```
ตัวอย่างผลลัพธ์: `70`

## โลกหรือเซิร์ฟเวอร์ล่าสุด (last_world_server)
คืนข้อมูลเกี่ยวกับโลกหรือเซิร์ฟเวอร์ล่าสุดที่เข้าถึง
```
{"placeholder":"last_world_server","values":{"type":"both","full_world_path":"true"}}
```
พารามิเตอร์:
- `type`: กำหนดประเภทของข้อมูลที่จะคืน
  - `"both"`: คืนโลกหรือเซิร์ฟเวอร์ล่าสุดที่เข้าถึง (ค่าเริ่มต้น)
  - `"server"`: คืนเฉพาะเมื่อครั้งล่าสุดที่เข้าถึงเป็นเซิร์ฟเวอร์
  - `"world"`: คืนเฉพาะเมื่อครั้งล่าสุดที่เข้าถึงเป็นโลก
- `full_world_path`: ควบคุมการแสดงพาธของโลก
  - `"true"`: คืนพาธเต็มของโลก (ค่าเริ่มต้น)
  - `"false"`: คืนเฉพาะชื่อโลกโดยไม่มีพาธ (ไม่กระทบเซิร์ฟเวอร์)

ตัวอย่าง:
- เซิร์ฟเวอร์: `mc.hypixel.net`
- โลกแบบพาธเต็ม: `saves/New World`
- โลกแบบไม่มีพาธเต็ม: `New World`

## ความกว้างหน้าจอ (guiwidth)
คืนความกว้างหน้าจอปัจจุบัน
```
{"placeholder":"guiwidth"}
```
ตัวอย่างผลลัพธ์: `1920`

## ความสูงหน้าจอ (guiheight)
คืนความสูงหน้าจอปัจจุบัน
```
{"placeholder":"guiheight"}
```
ตัวอย่างผลลัพธ์: `1080`

## ตัวระบุหน้าจอปัจจุบัน (screenid)
คืนตัวระบุของหน้าจอปัจจุบัน
```
{"placeholder":"screenid"}
```
ตัวอย่างผลลัพธ์: `title_screen`

## ความกว้างขององค์ประกอบ (elementwidth)
คืนความกว้างขององค์ประกอบที่ระบุ
```
{"placeholder":"elementwidth","values":{"id":"my_button"}}
```
ตัวอย่างผลลัพธ์: `200`

## ความสูงขององค์ประกอบ (elementheight)
คืนความสูงขององค์ประกอบที่ระบุ
```
{"placeholder":"elementheight","values":{"id":"my_button"}}
```
ตัวอย่างผลลัพธ์: `20`

## ตำแหน่ง X ขององค์ประกอบ (elementposx)
คืนตำแหน่ง X ขององค์ประกอบที่ระบุ
```
{"placeholder":"elementposx","values":{"id":"my_button"}}
```
ตัวอย่างผลลัพธ์: `150`

## ตำแหน่ง Y ขององค์ประกอบ (elementposy)
คืนตำแหน่ง Y ขององค์ประกอบที่ระบุ
```
{"placeholder":"elementposy","values":{"id":"my_button"}}
```
ตัวอย่างผลลัพธ์: `100`

## ตำแหน่ง X ของเมาส์ (mouseposx)
คืนตำแหน่ง X ปัจจุบันของเมาส์
```
{"placeholder":"mouseposx"}
```
ตัวอย่างผลลัพธ์: `960`

## ตำแหน่ง Y ของเมาส์ (mouseposy)
คืนตำแหน่ง Y ปัจจุบันของเมาส์
```
{"placeholder":"mouseposy"}
```
ตัวอย่างผลลัพธ์: `540`

## จำนวนคลิกต่อวินาที (clicks_per_second)
คืนจำนวนคลิกต่อวินาทีปัจจุบันของปุ่มเมาส์
```
{"placeholder":"clicks_per_second","values":{"mouse_button":"left"}}
```
พารามิเตอร์:
- `mouse_button`: `left` หรือ `right`

ตัวอย่างผลลัพธ์: `8`

## สเกล GUI (guiscale)
คืนสเกล GUI ปัจจุบัน
```
{"placeholder":"guiscale"}
```
ตัวอย่างผลลัพธ์: `2`

## ป้ายกำกับ/ข้อความของวิดเจ็ต Vanilla (vanillabuttonlabel)
คืนป้ายกำกับ/ข้อความของวิดเจ็ตหรือปุ่มแบบ vanilla
```
{"placeholder":"vanillabuttonlabel","values":{"locator":"some.menu.identifier:505280"}}
```
ตัวอย่างผลลัพธ์: `Options...`

## ค่าช่องป้อนข้อความ (text_input_field_value)
คืนค่าปัจจุบันของช่องป้อนข้อความแบบกำหนดเองหรือแบบ vanilla โดยใช้ตัวระบุองค์ประกอบ
```
{"placeholder":"text_input_field_value","values":{"element_identifier":"my_input"}}
```
ตัวอย่างผลลัพธ์: `Hello World`

## พลังชีวิตปัจจุบันของผู้เล่น (current_player_health)
คืนค่าพลังชีวิตปัจจุบันของผู้เล่น
```
{"placeholder":"current_player_health"}
```
ตัวอย่างผลลัพธ์: `20.0`

## พลังชีวิตสูงสุดของผู้เล่น (max_player_health)
คืนค่าพลังชีวิตสูงสุดของผู้เล่น
```
{"placeholder":"max_player_health"}
```
ตัวอย่างผลลัพธ์: `20.0`

## พลังชีวิตผู้เล่นปัจจุบัน (เปอร์เซ็นต์) (current_player_health_percent)
คืนพลังชีวิตของผู้เล่นเป็นเปอร์เซ็นต์
```
{"placeholder":"current_player_health_percent"}
```
ตัวอย่างผลลัพธ์: `100`

## พลังดูดซับปัจจุบันของผู้เล่น (current_player_absorption_health)
คืนค่าพลังดูดซับของผู้เล่น (หัวใจสีทอง)
```
{"placeholder":"current_player_absorption_health"}
```
ตัวอย่างผลลัพธ์: `4.0`

## พลังดูดซับสูงสุดของผู้เล่น (max_player_absorption_health)
คืนค่าพลังดูดซับสูงสุด
```
{"placeholder":"max_player_absorption_health"}
```
ตัวอย่างผลลัพธ์: `4.0`

## พลังดูดซับปัจจุบันของผู้เล่น (เปอร์เซ็นต์) (current_player_absorption_health_percent)
คืนพลังดูดซับของผู้เล่นเป็นเปอร์เซ็นต์
```
{"placeholder":"current_player_absorption_health_percent"}
```
ตัวอย่างผลลัพธ์: `100`

## ระดับความหิวปัจจุบันของผู้เล่น (current_player_hunger)
คืนระดับความหิวปัจจุบันของผู้เล่น
```
{"placeholder":"current_player_hunger"}
```
ตัวอย่างผลลัพธ์: `20`

## ระดับความหิวสูงสุดของผู้เล่น (max_player_hunger)
คืนระดับความหิวสูงสุด
```
{"placeholder":"max_player_hunger"}
```
ตัวอย่างผลลัพธ์: `20`

## ระดับความหิวปัจจุบันของผู้เล่น (เปอร์เซ็นต์) (current_player_hunger_percent)
คืนความหิวของผู้เล่นเป็นเปอร์เซ็นต์
```
{"placeholder":"current_player_hunger_percent"}
```
ตัวอย่างผลลัพธ์: `100`

## ค่าความอิ่มของความหิวปัจจุบันของผู้เล่น (current_player_hunger_saturation)
คืนค่าความอิ่มของความหิวปัจจุบันของผู้เล่น
```
{"placeholder":"current_player_hunger_saturation"}
```
ตัวอย่างผลลัพธ์: `5.0`

## พลังป้องกันปัจจุบันของผู้เล่น (current_player_armor)
คืนค่าพลังป้องกันปัจจุบันของผู้เล่น
```
{"placeholder":"current_player_armor"}
```
ตัวอย่างผลลัพธ์: `20`

## ความทนทานเกราะของผู้เล่น (player_armor_toughness)
คืนค่าความทนทานเกราะรวมของผู้เล่น
```
{"placeholder":"player_armor_toughness"}
```
ตัวอย่างผลลัพธ์: `8.0`

## พลังป้องกันสูงสุดของผู้เล่น (max_player_armor)
คืนค่าพลังป้องกันสูงสุด
```
{"placeholder":"max_player_armor"}
```
ตัวอย่างผลลัพธ์: `20`

## พลังป้องกันปัจจุบันของผู้เล่น (เปอร์เซ็นต์) (current_player_armor_percent)
คืนพลังป้องกันของผู้เล่นเป็นเปอร์เซ็นต์
```
{"placeholder":"current_player_armor_percent"}
```
ตัวอย่างผลลัพธ์: `100`

## ระดับออกซิเจนปัจจุบันของผู้เล่น (current_player_oxygen)
คืนระดับออกซิเจนปัจจุบันของผู้เล่น (ฟองอากาศ)
```
{"placeholder":"current_player_oxygen"}
```
ตัวอย่างผลลัพธ์: `300`

## ระดับออกซิเจนสูงสุดของผู้เล่น (max_player_oxygen)
คืนระดับออกซิเจนสูงสุด
```
{"placeholder":"max_player_oxygen"}
```
ตัวอย่างผลลัพธ์: `300`

## ระดับออกซิเจนปัจจุบันของผู้เล่น (เปอร์เซ็นต์) (current_player_oxygen_percent)
คืนระดับออกซิเจนของผู้เล่นเป็นเปอร์เซ็นต์
```
{"placeholder":"current_player_oxygen_percent"}
```
ตัวอย่างผลลัพธ์: `100`

## ระดับเลเวลปัจจุบันของผู้เล่น (current_player_level)
คืนเลเวลประสบการณ์ปัจจุบันของผู้เล่น
```
{"placeholder":"current_player_level"}
```
ตัวอย่างผลลัพธ์: `30`

## ประสบการณ์ปัจจุบันของผู้เล่น (current_player_exp)
คืนค่าประสบการณ์รวมของผู้เล่น
```
{"placeholder":"current_player_exp"}
```
ตัวอย่างผลลัพธ์: `1250`

## ความคืบหน้าประสบการณ์ของผู้เล่น (เปอร์เซ็นต์) (current_player_exp_progress)
คืนความคืบหน้าไปยังเลเวลถัดไปของผู้เล่นเป็นเปอร์เซ็นต์
```
{"placeholder":"current_player_exp_progress"}
```
ตัวอย่างผลลัพธ์: `75`

## พลังโจมตีของผู้เล่น (เปอร์เซ็นต์) (player_attack_strength)
คืนคูลดาวน์การโจมตีของผู้เล่นเป็นเปอร์เซ็นต์
```
{"placeholder":"player_attack_strength"}
```
ตัวอย่างผลลัพธ์: `100`

## โหมดเกมของผู้เล่น (player_gamemode)
คืนโหมดเกมปัจจุบันของผู้เล่น
```
{"placeholder":"player_gamemode"}
```
ตัวอย่างผลลัพธ์: `survival`

## ทิศทางที่ผู้เล่นหันอยู่ (player_view_direction)
คืนทิศทางที่ผู้เล่นกำลังหันหน้าอยู่
```
{"placeholder":"player_view_direction"}
```
ตัวอย่างผลลัพธ์: `north`

## พิกัด X ของผู้เล่น (player_x_coordinate)
คืนตำแหน่ง X ของผู้เล่นในโลก
```
{"placeholder":"player_x_coordinate"}
```
ตัวอย่างผลลัพธ์: `125`

## พิกัด Y ของผู้เล่น (player_y_coordinate)
คืนตำแหน่ง Y ของผู้เล่นในโลก
```
{"placeholder":"player_y_coordinate"}
```
ตัวอย่างผลลัพธ์: `64`

## พิกัด Z ของผู้เล่น (player_z_coordinate)
คืนตำแหน่ง Z ของผู้เล่นในโลก
```
{"placeholder":"player_z_coordinate"}
```
ตัวอย่างผลลัพธ์: `-250`

## พลังชีวิตของพาหนะที่กำลังขี่อยู่ (current_mount_health)
คืนพลังชีวิตปัจจุบันของเอนทิตีที่ผู้เล่นกำลังขี่อยู่
```
{"placeholder":"current_mount_health"}
```
ตัวอย่างผลลัพธ์: `30.0`

## พลังชีวิตสูงสุดของพาหนะที่กำลังขี่อยู่ (max_mount_health)
คืนพลังชีวิตสูงสุดของเอนทิตีที่ผู้เล่นกำลังขี่อยู่
```
{"placeholder":"max_mount_health"}
```
ตัวอย่างผลลัพธ์: `30.0`

## พลังชีวิตของพาหนะที่กำลังขี่อยู่ (เปอร์เซ็นต์) (current_mount_health_percent)
คืนพลังชีวิตของพาหนะเป็นเปอร์เซ็นต์
```
{"placeholder":"current_mount_health_percent"}
```
ตัวอย่างผลลัพธ์: `100`

## แถบกระโดดของพาหนะปัจจุบัน (เปอร์เซ็นต์) (current_mount_jump_meter)
คืนค่ามิเตอร์พลังกระโดดของพาหนะ
```
{"placeholder":"current_mount_jump_meter"}
```
ตัวอย่างผลลัพธ์: `75`

## พลังชีวิตบอสปัจจุบัน (เปอร์เซ็นต์) (current_boss_health)
คืนพลังชีวิตของบอสที่กำลังใช้งานอยู่
```
{"placeholder":"current_boss_health"}
```
ตัวอย่างผลลัพธ์: `150.0`

## ชื่อบอส (boss_name)
คืนชื่อของบอสที่กำลังใช้งานอยู่
```
{"placeholder":"boss_name","values":{"boss_index":"0","as_json":"false"}}
```
ตัวอย่างผลลัพธ์: `Ender Dragon`

## จำนวนบอส (boss_count)
คืนจำนวนบอสที่กำลังใช้งานอยู่
```
{"placeholder":"boss_count"}
```
ตัวอย่างผลลัพธ์: `1`

## จำนวนเอฟเฟกต์ที่ใช้งานอยู่ (effects_count)
คืนจำนวนเอฟเฟกต์ยาที่กำลังใช้งานอยู่
```
{"placeholder":"effects_count"}
```
ตัวอย่างผลลัพธ์: `3`

## เอฟเฟกต์ที่ใช้งานอยู่ (active_effect)
คืนข้อมูลเกี่ยวกับเอฟเฟกต์ที่ใช้งานอยู่ที่ระบุ
```
{"placeholder":"active_effect","values":{"effect_index":"0"}}
```
ตัวอย่างผลลัพธ์: `minecraft:speed`

## ช่องฮอตบาร์ที่เลือกอยู่ (active_hotbar_slot)
คืนช่องฮอตบาร์ที่เลือกอยู่ในขณะนี้ (0-8)
```
{"placeholder":"active_hotbar_slot"}
```
ตัวอย่างผลลัพธ์: `4`

## ไอเท็มในช่อง (slot_item)
คืนข้อมูลเกี่ยวกับไอเท็มในช่องอินเวนทอรีที่ระบุ
```
{"placeholder":"slot_item","values":{"slot":"0"}}
```
ตัวอย่างผลลัพธ์: `minecraft:diamond_sword`

## จำนวนไอเท็มในช่อง (slot_item_count)
คืนจำนวนไอเท็มแบบสแต็กในช่องอินเวนทอรีผู้เล่นที่ระบุ
```
{"placeholder":"slot_item_count","values":{"slot":"0"}}
```
ตัวอย่างผลลัพธ์: `64`

## ความทนทานของไอเท็มในช่อง (slot_item_durability)
คืนข้อมูลความทนทานของไอเท็มในช่องอินเวนทอรีผู้เล่นที่ระบุ
```
{"placeholder":"slot_item_durability","values":{"slot":"0","format":"percentage"}}
```
พารามิเตอร์:
- `slot`: หมายเลขช่องอินเวนทอรีผู้เล่น
- `format`: `current`, `remaining`, `max`, `damage`, `percentage`, หรือ `percent`

ตัวอย่างผลลัพธ์: `87`

## ชื่อแสดงของไอเท็มในช่อง (slot_item_display_name_fm)
คืนชื่อแสดงของไอเท็มในช่องที่ระบุในรูปแบบ JSON text component ในโหมด spectator ช่องฮอตบาร์สามารถแสดงชื่อไอเท็มเมนู spectator ได้ เว้นแต่ `ignore_spectator` จะเป็น `true`
```
{"placeholder":"slot_item_display_name_fm","values":{"slot":"0","ignore_spectator":"false"}}
```
ตัวอย่างผลลัพธ์: `{"text":"Diamond Sword","color":"aqua"}`

## จำนวนไอเท็มในอินเวนทอรี (inventory_item_count)
คืนจำนวนรวมของไอเท็มชนิดหนึ่งในอินเวนทอรีผู้เล่น หาก `item` ว่าง จะนับสแต็กไอเท็มทั้งหมดในอินเวนทอรี
```
{"placeholder":"inventory_item_count","values":{"item":"minecraft:diamond"}}
```
ตัวอย่างผลลัพธ์: `12`

## จำนวนที่ฟื้น Hunger จากอาหารในช่องอินเวนทอรี (inventory_slot_food_point_restore_amount)
คืนค่าความหิวที่ฟื้นจากไอเท็มอาหารในช่องอินเวนทอรีผู้เล่นที่กำหนด
```
{"placeholder":"inventory_slot_food_point_restore_amount","values":{"slot":"0"}}
```
ตัวอย่างผลลัพธ์: `4.0`

## ไอเท็มในอินเวนทอรีที่ชี้อยู่ (hovered_inventory_item)
คืนคีย์ของไอเท็มที่กำลังชี้อยู่ในหน้าจออินเวนทอรี
```
{"placeholder":"hovered_inventory_item"}
```
ตัวอย่างผลลัพธ์: `minecraft:apple`

## เวลาของเกมในโลก (game_time)
คืนตัวนับติ๊กเวลาปัจจุบันในเกม
```
{"placeholder":"game_time"}
```
ตัวอย่างผลลัพธ์: `18000`

## เวลาประจำวันของโลก (world_daytime)
คืนเวลาประจำวันปัจจุบันของโลก
```
{"placeholder":"world_daytime"}
```
ตัวอย่างผลลัพธ์: `13000`

## ชั่วโมงของเวลาประจำวันของโลก (world_daytime_hour)
คืนค่าชั่วโมงของเวลาโลก โดยปกติใช้รูปแบบ 24 ชั่วโมง หากต้องการ 12 ชั่วโมงให้ตั้ง `twelve_hour_format` เป็น `"true"`
```
{"placeholder":"world_daytime_hour","values":{"twelve_hour_format":"false"}}
```
ตัวอย่างผลลัพธ์: `12`

## นาทีของเวลาประจำวันของโลก (world_daytime_minute)
คืนค่านาทีของเวลาโลก (00-59)
```
{"placeholder":"world_daytime_minute"}
```
ตัวอย่างผลลัพธ์: `30`

## ความยากของโลก (world_difficulty)
คืนระดับความยากของโลกปัจจุบัน
```
{"placeholder":"world_difficulty"}
```
ตัวอย่างผลลัพธ์: `normal`

## seed ของโลกปัจจุบัน (current_world_seed)
คืน seed ของโลกผู้เล่นคนเดียวปัจจุบัน คืนค่าว่างเมื่อไม่สามารถอ่าน seed ได้
```
{"placeholder":"current_world_seed"}
```
ตัวอย่างผลลัพธ์: `123456789`

## ไบโอมปัจจุบัน (current_biome)
คืนไบโอมที่ผู้เล่นกำลังอยู่ในขณะนี้ ตั้ง `as_key` เป็น `"false"` เพื่อคืนชื่อที่แปลแล้ว/ชื่อที่แสดงถ้ามี
```
{"placeholder":"current_biome","values":{"as_key":"true"}}
```
ตัวอย่างผลลัพธ์: `minecraft:plains`

## มิติปัจจุบัน (current_dimension)
คืนมิติที่ผู้เล่นกำลังอยู่ในขณะนี้ ตั้ง `as_key` เป็น `"false"` เพื่อคืนชื่อที่แปลแล้ว/ชื่อที่แสดงถ้ามี
```
{"placeholder":"current_dimension","values":{"as_key":"true"}}
```
ตัวอย่างผลลัพธ์: `minecraft:overworld`

## ค่ากฎเกม (gamerule_value)
คืนค่าปัจจุบันของ gamerule ในโลก/เซิร์ฟเวอร์ที่โหลดอยู่ เซิร์ฟเวอร์เวิลด์ต้องมี FancyMenu บนเซิร์ฟเวอร์ด้วย
```
{"placeholder":"gamerule_value","values":{"name":"doDaylightCycle"}}
```
ตัวอย่างผลลัพธ์: `true`

## หมวดหมู่ไอเท็ม (item_category)
คืนหมวดหมู่แท็บสร้างสรรค์ของไอเท็ม ตั้ง `as_key` เป็น `"true"` เพื่อคืนคีย์ของหมวดหมู่แทนชื่อที่แสดง
```
{"placeholder":"item_category","values":{"item":"minecraft:diamond_sword","as_key":"false"}}
```
ตัวอย่างผลลัพธ์: `Combat`

## ชื่อ/คำบรรยาย HUD ปัจจุบัน (current_title)
คืนข้อความชื่อที่กำลังแสดงอยู่ในขณะนี้
```
{"placeholder":"current_title","values":{"is_subtitle":"false","as_json":"false"}}
```
ตัวอย่างผลลัพธ์: `Game Over!`

## ข้อความแถบ Action Bar (action_bar_message_fm)
คืนข้อความ vanilla action bar ปัจจุบันที่อยู่เหนือฮอตบาร์
```
{"placeholder":"action_bar_message_fm"}
```
ตัวอย่างผลลัพธ์: `You may not rest now`

## เวลาของข้อความแถบ Action Bar (action_bar_message_time_fm)
คืนจำนวนติ๊กที่ข้อความ vanilla action bar ปัจจุบันจะยังแสดงอยู่
```
{"placeholder":"action_bar_message_time_fm"}
```
ตัวอย่างผลลัพธ์: `42`

## การหมุนกล้อง X (camera_rotation_x_fm)
คืนมุม pitch ของกล้องปัจจุบันเป็นองศา
```
{"placeholder":"camera_rotation_x_fm"}
```
ตัวอย่างผลลัพธ์: `12.5`

## การหมุนกล้อง Y (camera_rotation_y_fm)
คืนมุม yaw ของกล้องปัจจุบันเป็นองศา
```
{"placeholder":"camera_rotation_y_fm"}
```
ตัวอย่างผลลัพธ์: `-90.0`

## ค่าเปลี่ยนแปลงการหมุนกล้อง X (camera_rotation_delta_x_fm)
คืนค่าการเปลี่ยนแปลง pitch ของกล้องต่อหนึ่งติ๊ก
```
{"placeholder":"camera_rotation_delta_x_fm"}
```
ตัวอย่างผลลัพธ์: `0.4`

## ค่าเปลี่ยนแปลงการหมุนกล้อง Y (camera_rotation_delta_y_fm)
คืนค่าการเปลี่ยนแปลง yaw ของกล้องต่อหนึ่งติ๊ก
```
{"placeholder":"camera_rotation_delta_y_fm"}
```
ตัวอย่างผลลัพธ์: `-1.2`

## เวลาของไอเท็มที่ถูกไฮไลต์ (highlighted_item_time_fm)
คืนจำนวนติ๊กที่ชื่อไอเท็มที่ถูกไฮไลต์จะยังแสดงอยู่เหนือฮอตบาร์
```
{"placeholder":"highlighted_item_time_fm"}
```
ตัวอย่างผลลัพธ์: `30`

## ความคืบหน้าการใช้งานไอเท็มของผู้เล่น (player_item_use_progress_fm)
คืนความคืบหน้าการใช้ไอเท็มปัจจุบันจาก `0.0` ถึง `1.0`
```
{"placeholder":"player_item_use_progress_fm"}
```
ตัวอย่างผลลัพธ์: `0.65`

## ค่าเปลี่ยนแปลงตำแหน่งผู้เล่น X (player_position_delta_x_fm)
คืนการเปลี่ยนแปลงตำแหน่งผู้เล่นตามแกน X ต่อหนึ่งติ๊ก
```
{"placeholder":"player_position_delta_x_fm"}
```
ตัวอย่างผลลัพธ์: `0.0`

## ค่าเปลี่ยนแปลงตำแหน่งผู้เล่น Y (player_position_delta_y_fm)
คืนการเปลี่ยนแปลงตำแหน่งผู้เล่นตามแกน Y ต่อหนึ่งติ๊ก
```
{"placeholder":"player_position_delta_y_fm"}
```
ตัวอย่างผลลัพธ์: `-0.08`

## ค่าเปลี่ยนแปลงตำแหน่งผู้เล่น Z (player_position_delta_z_fm)
คืนการเปลี่ยนแปลงตำแหน่งผู้เล่นตามแกน Z ต่อหนึ่งติ๊ก
```
{"placeholder":"player_position_delta_z_fm"}
```
ตัวอย่างผลลัพธ์: `0.12`

## IP เซิร์ฟเวอร์ปัจจุบัน (current_server_ip)
คืน IP ของเซิร์ฟเวอร์ที่เชื่อมต่ออยู่
```
{"placeholder":"current_server_ip"}
```
ตัวอย่างผลลัพธ์: `mc.hypixel.net`

## รายชื่อผู้เล่นในโลก (world_players_list)
คืนรายชื่อผู้เล่นทั้งหมดที่อยู่ในโลกปัจจุบัน
```
{"placeholder":"world_players_list","values":{"separator":", "}}
```
ตัวอย่างผลลัพธ์: `Steve, Alex, Notch`

## MOTD ของเซิร์ฟเวอร์ (servermotd)
คืนข้อความประจำวันของเซิร์ฟเวอร์
```
{"placeholder":"servermotd","values":{"ip":"mc.hypixel.net","line":"1"}}
```
ตัวอย่างผลลัพธ์: `Welcome to Hypixel!`

## PING ของเซิร์ฟเวอร์ (serverping)
คืนค่า ping ไปยังเซิร์ฟเวอร์เป็นมิลลิวินาที
```
{"placeholder":"serverping","values":{"ip":"mc.hypixel.net"}}
```
ตัวอย่างผลลัพธ์: `54`

## จำนวนผู้เล่นของเซิร์ฟเวอร์ (serverplayercount)
คืนจำนวนผู้เล่นของเซิร์ฟเวอร์
```
{"placeholder":"serverplayercount","values":{"ip":"mc.hypixel.net"}}
```
ตัวอย่างผลลัพธ์: `25000/30000`

## สถานะของเซิร์ฟเวอร์ (serverstatus)
คืนสถานะออนไลน์/ออฟไลน์ของเซิร์ฟเวอร์
```
{"placeholder":"serverstatus","values":{"ip":"mc.hypixel.net"}}
```
ตัวอย่างผลลัพธ์: `§aOnline` หรือ `§cOffline`

## เวอร์ชันของเซิร์ฟเวอร์ (serverversion)
คืนเวอร์ชัน Minecraft ของเซิร์ฟเวอร์
```
{"placeholder":"serverversion","values":{"ip":"mc.hypixel.net"}}
```
ตัวอย่างผลลัพธ์: `1.19.2`

## ปี (realtimeyear)
คืนปีปัจจุบัน
```
{"placeholder":"realtimeyear"}
```
ตัวอย่างผลลัพธ์: `2024`

## เดือน (realtimemonth)
คืนเดือนปัจจุบัน (01-12)
```
{"placeholder":"realtimemonth"}
```
ตัวอย่างผลลัพธ์: `01`

## วัน (realtimeday)
คืนวันของเดือนปัจจุบัน (01-31)
```
{"placeholder":"realtimeday"}
```
ตัวอย่างผลลัพธ์: `27`

## ชั่วโมง (realtimehour)
คืนชั่วโมงปัจจุบัน โดยปกติใช้รูปแบบ 24 ชั่วโมง หากต้องการ 12 ชั่วโมงให้ตั้ง `twelve_hour_format` เป็น `"true"`
```
{"placeholder":"realtimehour","values":{"twelve_hour_format":"false","timezone":"system"}}
```
ตัวอย่างผลลัพธ์: `14`

## นาที (realtimeminute)
คืนค่านาทีปัจจุบัน (00-59)
```
{"placeholder":"realtimeminute"}
```
ตัวอย่างผลลัพธ์: `30`

## วินาที (realtimesecond)
คืนค่าวินาทีปัจจุบัน (00-59)
```
{"placeholder":"realtimesecond"}
```
ตัวอย่างผลลัพธ์: `45`

## เวลาปัจจุบันในหน่วยมิลลิวินาที (Unix Timestamp) (unix_time)
คืน Unix timestamp ปัจจุบันในหน่วยมิลลิวินาที
```
{"placeholder":"unix_time"}
```
ตัวอย่างผลลัพธ์: `1716552478123`

> ตัวยึดตำแหน่งแบบเรียลไทม์ (`realtimeyear`, `realtimemonth`, `realtimeday`, `realtimehour`, `realtimeminute`, `realtimesecond`, และ `unix_time`) รองรับค่า `timezone` ใช้รหัสเขตเวลา Java ปกติ เช่น `UTC`, `Europe/Berlin`, หรือ `America/New_York`; หากไม่ระบุหรือใช้ `system` จะใช้เขตเวลาของระบบ
{.is-info}

## ข้อมูล CPU (cpuinfo)
คืนข้อมูลเกี่ยวกับ CPU
```
{"placeholder":"cpuinfo"}
```
ตัวอย่างผลลัพธ์: `Intel(R) Core(TM) i7-10700K CPU @ 3.80GHz`

## การใช้งาน CPU (JVM) (jvmcpu)
คืนการใช้งาน CPU ของ JVM เป็นเปอร์เซ็นต์
```
{"placeholder":"jvmcpu"}
```
ตัวอย่างผลลัพธ์: `25.5`

## การใช้งาน CPU (OS) (oscpu)
คืนการใช้งาน CPU ของระบบปฏิบัติการเป็นเปอร์เซ็นต์
```
{"placeholder":"oscpu"}
```
ตัวอย่างผลลัพธ์: `42.8`

## ข้อมูล GPU (gpuinfo)
คืนข้อมูลเกี่ยวกับ GPU
```
{"placeholder":"gpuinfo"}
```
ตัวอย่างผลลัพธ์: `NVIDIA GeForce RTX 3080`

## เวอร์ชัน Java (javaver)
คืนเวอร์ชัน Java
```
{"placeholder":"javaver"}
```
ตัวอย่างผลลัพธ์: `17.0.2`

## Java Virtual Machine (jvmname)
คืนชื่อของ Java Virtual Machine
```
{"placeholder":"jvmname"}
```
ตัวอย่างผลลัพธ์: `OpenJDK 64-Bit Server VM`

## เวอร์ชัน OpenGL (glver)
คืนเวอร์ชัน OpenGL
```
{"placeholder":"glver"}
```
ตัวอย่างผลลัพธ์: `4.6.0 NVIDIA 516.94`

## ชื่อระบบปฏิบัติการ (osname)
คืนชื่อระบบปฏิบัติการ
```
{"placeholder":"osname"}
```
ตัวอย่างผลลัพธ์: `Windows 10`

## FPS (Frames Per Second) (fps)
คืนจำนวนเฟรมต่อวินาทีปัจจุบัน
```
{"placeholder":"fps"}
```
ตัวอย่างผลลัพธ์: `120`

## RAM ที่ใช้อยู่ใน MB (usedram)
คืนปริมาณ RAM ที่กำลังใช้อยู่ (MB)
```
{"placeholder":"usedram"}
```
ตัวอย่างผลลัพธ์: `4096`

## RAM สูงสุดใน MB (maxram)
คืน RAM สูงสุดที่จัดสรรไว้ (MB)
```
{"placeholder":"maxram"}
```
ตัวอย่างผลลัพธ์: `8192`

## RAM ที่ใช้อยู่เป็น %% (percentram)
คืนเปอร์เซ็นต์ของ RAM ที่กำลังใช้อยู่
```
{"placeholder":"percentram"}
```
ตัวอย่างผลลัพธ์: `50`

## ระดับเสียงขององค์ประกอบเสียง (audio_element_vol)
คืนระดับเสียงขององค์ประกอบเสียง
```
{"placeholder":"audio_element_vol","values":{"element_identifier":"background_music"}}
```
ตัวอย่างผลลัพธ์: `0.5`

## แทร็กเสียงปัจจุบัน (audio_element_current_track)
คืนชื่อแทร็กขององค์ประกอบเสียง
```
{"placeholder":"audio_element_current_track","values":{"element_identifier":"background_music","display_name_mappings":"track1.ogg=>Cool Track Name"}}
```
ตัวอย่างผลลัพธ์: `Cool Track Name`

## ระยะเวลาเสียง (audio_duration)
คืนระยะเวลารวมของแทร็กเสียงในรูปแบบ MM:SS
```
{"placeholder":"audio_duration","values":{"element_identifier":"background_music"}}
```
ตัวอย่างผลลัพธ์: `03:45`

## เวลาเล่นเสียง (audio_playtime)
คืนเวลาเล่นปัจจุบันของแทร็กเสียง ตั้ง `show_percentage` เป็น `"true"` เพื่อให้ได้ค่า progression 0-100 แทน MM:SS
```
{"placeholder":"audio_playtime","values":{"element_identifier":"background_music","show_percentage":"false"}}
```
ตัวอย่างผลลัพธ์: `01:30` (หรือ `45` เมื่อ `show_percentage` เป็น `"true"`)

## สถานะการเล่นเสียง (audio_playing_state)
คืนว่าองค์ประกอบเสียงกำลังเล่นอยู่หรือไม่ (true/false)
```
{"placeholder":"audio_playing_state","values":{"element_identifier":"background_music"}}
```
ตัวอย่างผลลัพธ์: `true`

## ระดับเสียงขององค์ประกอบวิดีโอ (video_element_vol)
คืนระดับเสียงขององค์ประกอบวิดีโอ (0.0 ถึง 1.0)
```
{"placeholder":"video_element_vol","values":{"element_identifier":"my_video_element"}}
```
ตัวอย่างผลลัพธ์: `0.5`

## ระยะเวลาองค์ประกอบวิดีโอ (video_element_duration)
คืนระยะเวลารวมขององค์ประกอบวิดีโอในรูปแบบ `MM:SS` ตั้ง `output_as_timestamp` เป็น `"true"` เพื่อคืนค่าเป็น timestamp หน่วยมิลลิวินาที
```
{"placeholder":"video_element_duration","values":{"element_identifier":"my_video_element","output_as_timestamp":"false"}}
```
ตัวอย่างผลลัพธ์: `02:00` (หรือ `120000` เมื่อ `output_as_timestamp` เป็น `"true"`)

## เวลาเล่นขององค์ประกอบวิดีโอ (video_element_playtime)
คืนเวลาเล่นปัจจุบัน (progress) ขององค์ประกอบวิดีโอในรูปแบบ `MM:SS` ตั้ง `show_percentage` เป็น `"true"` เพื่อให้ได้ค่า progression 0-100 หรือ `output_as_timestamp` เป็น `"true"` เพื่อให้เป็นมิลลิวินาที
```
{"placeholder":"video_element_playtime","values":{"element_identifier":"my_video_element","show_percentage":"false","output_as_timestamp":"false"}}
```
ตัวอย่างผลลัพธ์: `00:45` (หรือ `38` เป็นเปอร์เซ็นต์ หรือ `45200` เป็น timestamp)

## สถานะหยุดชั่วคราวขององค์ประกอบวิดีโอ (video_element_paused_state)
คืนว่าองค์ประกอบวิดีโอถูกหยุดชั่วคราวหรือไม่ (true/false)
```
{"placeholder":"video_element_paused_state","values":{"element_identifier":"my_video_element"}}
```
ตัวอย่างผลลัพธ์: `false`

## ระดับเสียงพื้นหลังวิดีโอ (video_background_vol)
คืนระดับเสียงของวิดีโอพื้นหลังเมนู (0.0 ถึง 1.0)
```
{"placeholder":"video_background_vol","values":{"background_identifier":"main_menu_video"}}
```
ตัวอย่างผลลัพธ์: `0.7`

## ระยะเวลาพื้นหลังวิดีโอ (video_background_duration)
คืนระยะเวลารวมของพื้นหลังวิดีโอเมนูในรูปแบบ `MM:SS` ตั้ง `output_as_timestamp` เป็น `"true"` เพื่อคืนค่าเป็น timestamp หน่วยมิลลิวินาที
```
{"placeholder":"video_background_duration","values":{"background_identifier":"main_menu_video","output_as_timestamp":"false"}}
```
ตัวอย่างผลลัพธ์: `03:00` (หรือ `180000` เมื่อ `output_as_timestamp` เป็น `"true"`)

## เวลาเล่นของพื้นหลังวิดีโอ (video_background_playtime)
คืนเวลาเล่นปัจจุบัน (progress) ของพื้นหลังวิดีโอเมนูในรูปแบบ `MM:SS` ตั้ง `show_percentage` เป็น `"true"` เพื่อให้ได้ค่า progression 0-100 หรือ `output_as_timestamp` เป็น `"true"` เพื่อให้เป็นมิลลิวินาที
```
{"placeholder":"video_background_playtime","values":{"background_identifier":"main_menu_video","show_percentage":"false","output_as_timestamp":"false"}}
```
ตัวอย่างผลลัพธ์: `01:00` (หรือ `33` เป็นเปอร์เซ็นต์ หรือ `60500` เป็น timestamp)

## สถานะหยุดชั่วคราวของพื้นหลังวิดีโอ (video_background_paused_state)
คืนว่าพื้นหลังวิดีโอของเมนูถูกหยุดชั่วคราวหรือไม่ (true/false)
```
{"placeholder":"video_background_paused_state","values":{"background_identifier":"main_menu_video"}}
```
ตัวอย่างผลลัพธ์: `true`

## เครื่องคิดเลข (calc)
ตัวยึดตำแหน่งเครื่องคิดเลขเป็นเครื่องมือทรงพลังที่ช่วยให้คุณคำนวณทางคณิตศาสตร์ภายในเลย์เอาต์ได้ รองรับการดำเนินการทางคณิตศาสตร์หลากหลายรูปแบบ และใช้งานได้ทั้งกับตัวเลขทศนิยมและจำนวนเต็ม

### ไวยากรณ์พื้นฐาน
```
{"placeholder":"calc","values":{"decimal":"true/false","expression":"your_expression"}}
```

เครื่องคิดเลขมีพารามิเตอร์หลัก 2 ตัว:
- `decimal`: กำหนดว่าผลลัพธ์ควรมีทศนิยมหรือไม่ (`true`) หรือปัดเป็นจำนวนเต็ม (`false`)
- `expression`: นิพจน์ทางคณิตศาสตร์ที่จะคำนวณ

### การดำเนินการที่รองรับ
เครื่องคิดเลขรองรับการดำเนินการทางคณิตศาสตร์ต่อไปนี้:
- คณิตพื้นฐาน: `+` (บวก), `-` (ลบ), `*` (คูณ), `/` (หาร)
- วงเล็บ: `( )` สำหรับจัดกลุ่มการคำนวณ
- ยกกำลัง: `^`
- รากที่สอง: `sqrt()`
- ฟังก์ชันตรีโกณมิติ: `sin()`, `cos()`, `tan()`
- ค่าคงที่ทางคณิตศาสตร์: `pi`, `e`
- ค่าสัมบูรณ์: `abs()`
- ลอการิทึม: `log()`, `ln()`

## สุ่มตัวเลข (random_number)
สร้างตัวเลขสุ่มภายในช่วงที่กำหนด
```
{"placeholder":"random_number","values":{"min":"1","max":"100"}}
```
ตัวอย่างผลลัพธ์: `42`

## ค่าสูงสุดของตัวเลข (maxnum)
คืนค่าที่มากกว่าระหว่างตัวเลขสองตัว
```
{"placeholder":"maxnum","values":{"first":"10","second":"20"}}
```
ตัวอย่างผลลัพธ์: `20`

## ค่าต่ำสุดของตัวเลข (minnum)
คืนค่าที่น้อยกว่าระหว่างตัวเลขสองตัว
```
{"placeholder":"minnum","values":{"first":"10","second":"20"}}
```
ตัวอย่างผลลัพธ์: `10`

## ค่าสัมบูรณ์ของตัวเลข (absnum)
คืนค่าสัมบูรณ์ของตัวเลข
```
{"placeholder":"absnum","values":{"num":"-10.5"}}
```
ตัวอย่างผลลัพธ์: `10.5`

## เปลี่ยนเครื่องหมายของตัวเลข (negnum)
คืนค่าตรงข้ามของตัวเลข
```
{"placeholder":"negnum","values":{"num":"10.5"}}
```
ตัวอย่างผลลัพธ์: `-10.5`

## *pi* (คณิตศาสตร์) (math_pi)
คืนค่าของ π
```
{"placeholder":"math_pi"}
```
ตัวอย่างผลลัพธ์: `3.141592653589793`

## ไซน์ตรีโกณมิติ (คณิตศาสตร์) (math_sin)
คืนค่า sine ของมุม
```
{"placeholder":"math_sin","values":{"angle":"45"}}
```
ตัวอย่างผลลัพธ์: `0.7071067811865476`

## โคไซน์ตรีโกณมิติ (คณิตศาสตร์) (math_cos)
คืนค่า cosine ของมุม
```
{"placeholder":"math_cos","values":{"angle":"45"}}
```
ตัวอย่างผลลัพธ์: `0.7071067811865476`

## แทนเจนต์ตรีโกณมิติ (คณิตศาสตร์) (math_tan)
คืนค่า tangent ของมุม
```
{"placeholder":"math_tan","values":{"angle":"45"}}
```
ตัวอย่างผลลัพธ์: `1.0`

## ปัดลง (คณิตศาสตร์) (math_floor)
ปัดตัวเลขลงเป็นจำนวนเต็มที่ใกล้ที่สุด
```
{"placeholder":"math_floor","values":{"num":"3.14"}}
```
ตัวอย่างผลลัพธ์: `3`

## ปัดขึ้น (คณิตศาสตร์) (math_ceil)
ปัดตัวเลขขึ้นเป็นจำนวนเต็มที่ใกล้ที่สุด
```
{"placeholder":"math_ceil","values":{"num":"3.14"}}
```
ตัวอย่างผลลัพธ์: `4`

## ปัดเศษ (คณิตศาสตร์) (math_round)
ปัดตัวเลข โดยปกติจะปัดเป็นจำนวนเต็มที่ใกล้ที่สุด; ตั้ง `decimals` เป็นจำนวนที่ไม่ติดลบเพื่อปัดเป็นทศนิยมตามจำนวนตำแหน่งที่ระบุ
```
{"placeholder":"math_round","values":{"num":"3.14159","decimals":"2"}}
```
ตัวอย่างผลลัพธ์: `3.14` (เมื่อ `decimals:-1` หรือไม่ได้ระบุ → `3`)

## เครื่องหมาย (คณิตศาสตร์) (math_sign)
คืนเครื่องหมายของตัวเลข (1 สำหรับบวก, -1 สำหรับลบ, 0 สำหรับศูนย์)
```
{"placeholder":"math_sign","values":{"num":"-3.14"}}
```
ตัวอย่างผลลัพธ์: `-1`

## ไซน์ไฮเพอร์โบลิก (คณิตศาสตร์) (math_sinh)
คืนค่า hyperbolic sine ของมุม
```
{"placeholder":"math_sinh","values":{"angle":"1"}}
```
ตัวอย่างผลลัพธ์: `1.1752011936438014`

## โคไซน์ไฮเพอร์โบลิก (คณิตศาสตร์) (math_cosh)
คืนค่า hyperbolic cosine ของมุม
```
{"placeholder":"math_cosh","values":{"angle":"1"}}
```
ตัวอย่างผลลัพธ์: `1.5430806348152437`

## แทนเจนต์ไฮเพอร์โบลิก (คณิตศาสตร์) (math_tanh)
คืนค่า hyperbolic tangent ของมุม
```
{"placeholder":"math_tanh","values":{"angle":"1"}}
```
ตัวอย่างผลลัพธ์: `0.7615941559557649`

## แยกข้อความ (split_text)
แยกข้อความโดยใช้ตัวคั่นที่ระบุ
```
{"placeholder":"split_text","values":{"input":"hello,world","regex":",","max_parts":"2","split_index":"1"}}
```
ตัวอย่างผลลัพธ์: `world`

## ตัดช่องว่างข้อความ (trim_text)
ลบช่องว่างหน้าหลังออก
```
{"placeholder":"trim_text","values":{"text":"  hello world  "}}
```
ตัวอย่างผลลัพธ์: `hello world`

## ตัดข้อความ (crop_text)
ลบอักขระจากจุดเริ่มต้นและจุดสิ้นสุดของข้อความ
```
{"placeholder":"crop_text","values":{"text":"hello world","remove_from_start":"1","remove_from_end":"1"}}
```
ตัวอย่างผลลัพธ์: `ello worl`

## แปลงเป็นข้อความแบบสตริง (stringify)
แปลงข้อความให้เป็นสตริงโดย escape อักขระไวยากรณ์ทั้งหมด
```
{"placeholder":"stringify","values":{"text":"text with {special} \"characters\""}}
```
ตัวอย่างผลลัพธ์: `text with \{special\} \"characters\"`

## แปลข้อความ (local)
ดึงข้อความที่แปลแล้วสำหรับคีย์ที่ระบุ
```
{"placeholder":"local","values":{"key":"menu.singleplayer"}}
```
ตัวอย่างผลลัพธ์: `Singleplayer`

## ข้อความจากเว็บ (webtext)
ดึงเนื้อหาข้อความจาก URL บนเว็บ
```
{"placeholder":"webtext","values":{"link":"http://somewebsite.com/textfile.txt"}}
```
ตัวอย่างผลลัพธ์: เนื้อหาข้อความจาก URL

## ข้อความสุ่ม (randomtext)
คืนบรรทัดแบบสุ่มจากไฟล์ข้อความ, URL, หรือข้อความธรรมดาโดยตรง ข้อความจะเปลี่ยนตามช่วงเวลาที่กำหนด
```
{"placeholder":"randomtext","values":{"source":"/config/fancymenu/assets/<file_name.txt>","interval":"10"}}
```
พารามิเตอร์:
- `source`: แหล่งที่มาของบรรทัดข้อความ (แทนพารามิเตอร์ `path` แบบเก่า)
  - พาธไฟล์: `/config/fancymenu/assets/quotes.txt`
  - URL: `https://example.com/quotes.txt`
  - ข้อความธรรมดา: `Line 1\nLine 2\nLine 3`
- `interval`: เวลาระหว่างการเปลี่ยนข้อความ หน่วยเป็นวินาที

ตอนนี้ตัวยึดตำแหน่งรองรับแหล่งที่มา 3 แบบ:
1. **ไฟล์ในเครื่อง**: ไฟล์ข้อความจากไดเรกทอรีเกมของคุณ
   ```
   {"placeholder":"randomtext","values":{"source":"/config/fancymenu/assets/quotes.txt","interval":"10"}}
   ```
2. **URL**: ไฟล์ข้อความจากอินเทอร์เน็ต
   ```
   {"placeholder":"randomtext","values":{"source":"https://example.com/quotes.txt","interval":"10"}}
   ```
3. **ข้อความธรรมดา**: ป้อนข้อความโดยตรง โดยแยกแต่ละบรรทัดด้วย `\n`
   ```
   {"placeholder":"randomtext","values":{"source":"First line\nSecond line\nThird line","interval":"5"}}
   ```

หมายเหตุ: ตัวยึดตำแหน่งแบบเก่าที่ใช้ `path` แทน `source` จะยังคงใช้งานได้

## ตัวแยกวิเคราะห์ JSON (json)
แยกวิเคราะห์ข้อมูล JSON จากไฟล์, URL, หรือเนื้อหา JSON โดยตรง และดึงค่าด้วยนิพจน์ JSON path
```
{"placeholder":"json","values":{"source":"path_or_link_or_json_content","json_path":"$.some.json.path"}}
```
พารามิเตอร์:
- `source`: แหล่งที่มาของข้อมูล JSON
  - พาธไฟล์: `/config/fancymenu/assets/data.json`
  - URL: `https://api.example.com/data.json`
  - JSON โดยตรง: `{"name":"Steve","level":42}`
- `json_path`: นิพจน์ JSON path สำหรับดึงข้อมูล

ตอนนี้ตัวยึดตำแหน่งรองรับแหล่งที่มา 3 แบบ:
1. **ไฟล์ในเครื่อง**: ไฟล์ JSON จากไดเรกทอรีเกมของคุณ
   ```
   {"placeholder":"json","values":{"source":"/config/fancymenu/assets/playerdata.json","json_path":"$.player.name"}}
   ```
2. **URL**: ข้อมูล JSON จาก API หรือเว็บบริการ
   ```
   {"placeholder":"json","values":{"source":"https://api.minecraft.com/server/status","json_path":"$.online"}}
   ```
3. **JSON โดยตรง**: เนื้อหา JSON แบบ inline
   ```
   {"placeholder":"json","values":{"source":"{"name":"Steve","score":42,"rank":"Diamond"}","json_path":"$.rank"}}
   ```

ตัวอย่าง JSON path:
- `$.name` - ดึงฟิลด์ "name" จาก root
- `$.player.level` - ดึงฟิลด์ "level" ที่ซ้อนอยู่ภายใน "player"
- `$.items[0].id` - ดึงค่า "id" ของไอเท็มตัวแรกในอาร์เรย์
- `$.scores.*` - ดึงค่าทั้งหมดจากอ็อบเจ็กต์ "scores"

## พาธไฟล์/โฟลเดอร์แบบสมบูรณ์ (absolute_path)
คืนพาธแบบสมบูรณ์ของไฟล์
```
{"placeholder":"absolute_path","values":{"short_path":"relative/path/to/file.txt"}}
```
ตัวอย่างผลลัพธ์: `C:/Users/Username/AppData/Roaming/.minecraft/relative/path/to/file.txt`

## จำนวนอักขระของข้อความ (text_character_count)
คืนจำนวนอักขระในข้อความที่กำหนด
```
{"placeholder":"text_character_count","values":{"text":"Hello World!"}}
```
ตัวอย่างผลลัพธ์: `12`

## ความกว้างของข้อความ (text_width)
คืนความกว้างเป็นพิกเซลของข้อความที่กำหนดเมื่อแสดงผล
```
{"placeholder":"text_width","values":{"text":"Hello World!"}}
```
ตัวอย่างผลลัพธ์: `66`

## ข้อความตัวพิมพ์ใหญ่ทั้งหมด (uppercase_text)
แปลงข้อความอินพุตเป็นตัวพิมพ์ใหญ่ทั้งหมด
```
{"placeholder":"uppercase_text","values":{"text":"Hello World"}}
```
ตัวอย่างผลลัพธ์: `HELLO WORLD`

## ข้อความตัวพิมพ์เล็กทั้งหมด (lowercase_text)
แปลงข้อความอินพุตเป็นตัวพิมพ์เล็กทั้งหมด
```
{"placeholder":"lowercase_text","values":{"text":"Hello World"}}
```
ตัวอย่างผลลัพธ์: `hello world`

## ข้อความแบบ Title Case (title_case_text)
แปลงข้อความอินพุตเป็น title case
```
{"placeholder":"title_case_text","values":{"text":"hello world"}}
```
ตัวอย่างผลลัพธ์: `Hello World`

## ข้อความแบบ Sentence Case (sentence_case_text)
แปลงข้อความอินพุตเป็น sentence case
```
{"placeholder":"sentence_case_text","values":{"text":"hello world. this is fancymenu!"}}
```
ตัวอย่างผลลัพธ์: `Hello world. This is fancymenu!`

## ข้อความแบบ Snake Case (snake_case_text)
แปลงข้อความอินพุตเป็น `snake_case`
```
{"placeholder":"snake_case_text","values":{"text":"Hello World"}}
```
ตัวอย่างผลลัพธ์: `hello_world`

## ข้อความแบบ Kebab Case (kebab_case_text)
แปลงข้อความอินพุตเป็น `kebab-case`
```
{"placeholder":"kebab_case_text","values":{"text":"Hello World"}}
```
ตัวอย่างผลลัพธ์: `hello-world`

## ข้อความแบบ Alternating Case (alternating_case_text)
แปลงข้อความอินพุตเป็น alternating case
```
{"placeholder":"alternating_case_text","values":{"text":"alternating case"}}
```
ตัวอย่างผลลัพธ์: `aLtErNaTiNg CaSe`

## สลับตัวพิมพ์ข้อความ (toggle_case_text)
สลับตัวพิมพ์ของทุกตัวอักษรในข้อความอินพุต
```
{"placeholder":"toggle_case_text","values":{"text":"Toggle Case"}}
```
ตัวอย่างผลลัพธ์: `tOGGLE cASE`

## เข้ารหัสเป็น Base64 (base64_encode)
เข้ารหัสข้อความที่กำหนดเป็น Base64
```
{"placeholder":"base64_encode","values":{"text":"Hello World"}}
```
ตัวอย่างผลลัพธ์: `SGVsbG8gV29ybGQ=`

## ถอดรหัสจาก Base64 (base64_decode)
ถอดรหัสสตริง Base64 กลับเป็นข้อความธรรมดา
```
{"placeholder":"base64_decode","values":{"text":"SGVsbG8gV29ybGQ="}}
```
ตัวอย่างผลลัพธ์: `Hello World`

## ข้อความจากไฟล์ (file_text)
คืนบรรทัดข้อความจากไฟล์หรือ URL สามารถคืนได้ทั้งทุกบรรทัดหรือเฉพาะ X บรรทัดล่าสุด
```
{"placeholder":"file_text","values":{"path_or_url":"/config/fancymenu/assets/some_file.txt","mode":"all","separator":"\n","last_lines":"1"}}
```
พารามิเตอร์:
- `path_or_url`: พาธไฟล์หรือ URL ที่จะอ่าน
- `mode`: `"all"` (คืนทุกบรรทัด) หรือ `"last"` (คืนเฉพาะ X บรรทัดล่าสุด)
- `separator`: ข้อความที่ใช้เชื่อมบรรทัด (ค่าเริ่มต้น: `"\n"`)
- `last_lines`: จำนวนบรรทัดที่จะคืนเมื่อ `mode` เป็น `"last"` (ค่าเริ่มต้น: `"1"`)

ตัวอย่างผลลัพธ์: ขึ้นอยู่กับเนื้อหาไฟล์

## เนื้อหาคลิปบอร์ด (clipboard_content)
คืนข้อความที่เก็บอยู่ในคลิปบอร์ดของระบบในขณะนี้
```
{"placeholder":"clipboard_content"}
```
ตัวอย่างผลลัพธ์: ข้อความใดก็ตามที่อยู่ในคลิปบอร์ดตอนนี้

## แทนที่ข้อความ (replace_text)
แทนที่ข้อความในสตริงโดยใช้ข้อความตัวอักษรหรือ regular expressions
```
{"placeholder":"replace_text","values":{"text":"Hello World! This is a test.","search":"World","replacement":"FancyMenu","use_regex":"false","replace_all":"true"}}
```
พารามิเตอร์:
- `text`: ข้อความอินพุตที่ต้องการประมวลผล
- `search`: ข้อความหรือลวดลาย regex ที่ต้องการค้นหา
- `replacement`: ข้อความที่ใช้แทน
- `use_regex`: ใช้ regex หรือไม่ (`"true"`) หรือจับคู่แบบตัวอักษร (`"false"`)
- `replace_all`: แทนที่ทุกตำแหน่ง (`"true"`) หรือเฉพาะครั้งแรก (`"false"`)

ตัวอย่างผลลัพธ์: `Hello FancyMenu! This is a test.`

## สลับตามค่า (switch_case)
ทำงานแบบ switch-case ตามค่าที่กำหนด
```
{"placeholder":"switch_case","values":{"value":"1","cases":"1:first case,2:second case,3:third case","default":"default case"}}
```
ตัวอย่างผลลัพธ์: `first case` (ถ้าค่าเป็น 1)

## รับค่าตัวแปร (FM Variable) (getvariable)
ดึงค่าของตัวแปรที่บันทึกไว้ก่อนหน้านี้
```
{"placeholder":"getvariable","values":{"name":"some_variable"}}
```
ตัวอย่างผลลัพธ์: ขึ้นอยู่กับค่าที่บันทึกไว้

## ดึงข้อมูล NBT (nbt_data_get)
ดึงข้อมูล NBT ฝั่งไคลเอนต์ (คล้ายคำสั่ง `/data get`) ใช้ตัวแปรฝั่งเซิร์ฟเวอร์ `nbt_data_get_server` เมื่อเชื่อมต่อเซิร์ฟเวอร์และต้องการค่าที่ถูกต้องจากฝั่งเซิร์ฟเวอร์
```
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"foodLevel","scale":"1.0","return_type":"value"}}
```
พารามิเตอร์:
- `source_type`: `"entity"` หรือ `"block"`
- `entity_selector`: ตัวเลือกเอนทิตี เช่น `@s`, `@p`, `@e`, หรือ UUID/ชื่อ (สำหรับเอนทิตี)
- `block_pos`: ตำแหน่งบล็อกในรูปแบบ `"x y z"` (สำหรับบล็อก)
- `nbt_path`: เส้นทาง NBT ที่ต้องการดึง
- `scale`: ตัวคูณสเกลสำหรับค่าตัวเลข (ค่าเริ่มต้น: `"1.0"`)
- `return_type`: วิธีคืนข้อมูล:
  - `"value"`: ค่าเริ่มต้น คืนค่าโดยตรง (พร้อมสเกลสำหรับตัวเลขถ้ามี)
  - `"string"`: คืนข้อมูล NBT จริงเป็นสตริง
  - `"snbt"`: คืนเป็น SNBT (NBT แบบจัดรูปแบบ)
  - `"json"`: คืนเป็นคอมโพเนนต์รูปแบบ JSON (สำหรับแท็ก compound)

ตัวอย่างผลลัพธ์: `20` (สำหรับ food level)

## ดึงข้อมูล NBT (ฝั่งเซิร์ฟเวอร์) (nbt_data_get_server)
สอบถามข้อมูล NBT ฝั่งเซิร์ฟเวอร์ (ผ่านแพ็กเก็ต) และแคชผลลัพธ์ไว้ชั่วคราว ค่าเหมือนกับตัวแปรฝั่งไคลเอนต์
```
{"placeholder":"nbt_data_get_server","values":{"source_type":"entity","entity_selector":"@s","block_pos":"","storage_id":"minecraft:storage_key","nbt_path":"SelectedItem.id","scale":"1.0","return_type":"value"}}
```
ตัวอย่างผลลัพธ์: `minecraft:diamond_sword`

## ข้อความการตายครั้งล่าสุด (lastdeathmessage)
คืนข้อความการตายครั้งล่าสุดของผู้เล่นไคลเอนต์ ตั้ง `as_json_component` เป็น `"true"` เพื่อรับคอมโพเนนต์ข้อความ JSON ดิบ
```
{"placeholder":"lastdeathmessage","values":{"as_json_component":"false"}}
```
ตัวอย่างผลลัพธ์: `Steve was slain by Zombie`

## ระยะเวลาการทำงาน (uptime_duration)
คืนระยะเวลาที่ FancyMenu ถูกโหลดอยู่ โดยปกติค่าจะเป็นวินาที; ตั้ง `output_as_millis` เป็น `"true"` เพื่อรับเป็นมิลลิวินาที
```
{"placeholder":"uptime_duration","values":{"output_as_millis":"false"}}
```
ตัวอย่างผลลัพธ์: `742` (วินาทีตั้งแต่โหลด)

## ชื่อเซฟโลก (level_save_names)
แสดงรายชื่อเซฟโลกในเครื่องทั้งหมด โดยเชื่อมด้วยตัวคั่นที่เลือก ใช้บนเธรดไคลเอนต์
```
{"placeholder":"level_save_names","values":{"separator":", "}}
```
ตัวอย่างผลลัพธ์: `Creative Test, Survival World, Hardcore`

## ข้อมูลเซฟโลก (level_save_data)
คืนข้อมูลระดับโลกแบบซีเรียลไลซ์สำหรับชื่อโลกที่กำหนด (ต้องตรงกับชื่อที่แสดงในรายการเซฟ)
```
{"placeholder":"level_save_data","values":{"level_name":"Survival World"}}
```
ตัวอย่างผลลัพธ์: `{"name":"Survival World","gameMode":"survival",...}`

## ตัวแปลงฐานตัวเลข (number_base_convert)
แปลงตัวเลข (จำนวนเต็มหรือทศนิยม) จากฐานหนึ่งไปยังอีกฐานหนึ่ง (2–36) ค่าเริ่มต้นเป็นฐานสิบหากไม่ระบุฐาน
```
{"placeholder":"number_base_convert","values":{"input":"67.5","from_base":"10","to_base":"16"}}
```
ตัวอย่างผลลัพธ์: `43.8`

## ขนาดไฟล์ (file_size)
คืนขนาดของไฟล์ในเครื่องเป็นไบต์ อนุญาตเฉพาะพาธในเครื่องเท่านั้น
```
{"placeholder":"file_size","values":{"path":"/config/fancymenu/assets/notes.txt"}}
```
ตัวอย่างผลลัพธ์: `1284`

## MD5 ของไฟล์ (file_md5)
คืนค่า MD5 hash ของไฟล์ในเครื่องในรูปแบบสตริง hex ตัวพิมพ์เล็ก
```
{"placeholder":"file_md5","values":{"path":"/config/fancymenu/assets/notes.txt"}}
```
ตัวอย่างผลลัพธ์: `d41d8cd98f00b204e9800998ecf8427e`

# ตัวอย่างการใช้งานจริง

## สร้างการแสดงหน่วยความจำแบบไดนามิก
```
Used RAM: {"placeholder":"usedram"}MB / {"placeholder":"maxram"}MB ({"placeholder":"percentram"}%)
```

## สร้างนาฬิกาแบบเรียลไทม์
```
{"placeholder":"realtimehour"}:{"placeholder":"realtimeminute"}:{"placeholder":"realtimesecond"}
```

## สร้างการแสดงข้อมูลระบบ
```
OS: {"placeholder":"osname"}
CPU: {"placeholder":"cpuinfo"}
GPU: {"placeholder":"gpuinfo"}
Java: {"placeholder":"javaver"}
```

## HUD สถานะผู้เล่น
```
Health: {"placeholder":"current_player_health"} / {"placeholder":"max_player_health"} ({"placeholder":"current_player_health_percent"}%)
Armor: {"placeholder":"current_player_armor"} / {"placeholder":"max_player_armor"}
XP Level: {"placeholder":"current_player_level"}
```

## การคำนวณซับซ้อนด้วยตัวยึดตำแหน่งแบบซ้อน
```
{"placeholder":"calc","values":{"decimal":"true","expression":"({"placeholder":"usedram"} / {"placeholder":"maxram"}) * 100"}}
```

## การแสดงพิกัดพร้อมการปัดเศษ
```
X: {"placeholder":"math_round","values":{"num":"{"placeholder":"player_x_coordinate"}"}}
Y: {"placeholder":"math_round","values":{"num":"{"placeholder":"player_y_coordinate"}"}}
Z: {"placeholder":"math_round","values":{"num":"{"placeholder":"player_z_coordinate"}"}}
```

# แนวทางปฏิบัติที่ดีที่สุด

1. **แคชการทำงานที่หนัก**: ตัวยึดตำแหน่งบางตัว (เช่นตัวที่อ่านข้อมูลระบบ) อาจใช้ทรัพยากรสูง ควรพิจารณาใช้ตัวแปรเก็บค่าหากต้องใช้หลายครั้ง

2. **ใช้ค่าทศนิยมให้เหมาะสม**: เมื่อทำการคำนวณ ให้ใช้พารามิเตอร์ `decimal` อย่างเหมาะสม ตั้งเป็น `false` เมื่อคุณต้องการจำนวนเต็ม และเป็น `true` เมื่อคุณต้องการค่าทศนิยมที่แม่นยำ

3. **จัดการค่าที่หายไป**: ควรคิดไว้เสมอว่าจะเกิดอะไรขึ้นหากตัวยึดตำแหน่งไม่คืนค่า คุณอาจต้องกำหนดค่าเริ่มต้นในกรณีดังกล่าว

4. **ทดสอบประสิทธิภาพ**: เมื่อใช้ตัวยึดตำแหน่งจำนวนมากหรือโครงสร้างซ้อนที่ซับซ้อน ควรทดสอบผลกระทบต่อประสิทธิภาพ โดยเฉพาะบนเครื่องสเปกต่ำ

5. **ใช้การปรับขนาด/จัดตำแหน่งขั้นสูง**: สำหรับองค์ประกอบ UI แบบไดนามิก ให้ผสานตัวยึดตำแหน่งเข้ากับการปรับขนาดและการจัดตำแหน่งขั้นสูงเพื่อสร้างเลย์เอาต์ที่ตอบสนองได้

6. **ใช้ร่วมกับตัวแปร**: ใช้ตัวยึดตำแหน่งร่วมกับตัวแปรเพื่อให้ได้เนื้อหาที่ไดนามิกยิ่งขึ้น และสามารถอัปเดตผ่านการกระทำได้

# ปัญหาที่พบบ่อยและวิธีแก้

## ตัวยึดตำแหน่งไม่อัปเดต
หากค่าของตัวยึดตำแหน่งไม่อัปเดตตามที่คาดไว้ ให้ตรวจสอบ:
- รูปแบบของตัวยึดตำแหน่งถูกต้องหรือไม่
- ใช้ตัวพิมพ์ถูกต้องสำหรับรหัสของตัวยึดตำแหน่งหรือไม่
- ตัวยึดตำแหน่งนั้นต้องมีเงื่อนไขเฉพาะเพื่ออัปเดตหรือไม่

## ตัวยึดตำแหน่งแบบซ้อนไม่ทำงาน
เมื่อซ้อนตัวยึดตำแหน่ง:
- ตรวจสอบให้แน่ใจว่ามีการ escape เครื่องหมายคำพูดอย่างถูกต้อง
- ยืนยันว่าตัวยึดตำแหน่งที่ซ้อนแต่ละตัวถูกต้องเมื่อใช้งานแยกเดี่ยว

## ปัญหาประสิทธิภาพ
หากคุณสังเกตเห็นปัญหาประสิทธิภาพ:
- ลดจำนวนตัวยึดตำแหน่งที่ใช้
- หลีกเลี่ยงการซ้อนที่ไม่จำเป็น
- พิจารณาใช้ตัวแปรสำหรับค่าที่เรียกใช้บ่อย
- ใช้ตัวยึดตำแหน่งที่เหมาะกับความต้องการของคุณ (เช่น อย่าใช้ตัวยึดตำแหน่งแบบเรียลไทม์เมื่อค่าคงที่ก็เพียงพอ)
