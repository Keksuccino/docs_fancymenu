---
title: ตัวแทนที่ใช้แทนค่า
description: วิธีใช้งานตัวแทนที่ใช้แทนค่า.
---

# ตัวแทนที่ใช้แทนค่า

ตัวแทนที่ใช้แทนค่า คือค่าที่เปลี่ยนแปลงได้และจะถูกแทนที่ด้วยเนื้อหาจริงเมื่อถูกใช้งาน ใน FancyMenu ตัวแทนที่ใช้แทนค่าช่วยให้คุณแทรกเนื้อหาแบบไดนามิกลงในองค์ประกอบต่างๆ เช่น ข้อความ ปุ่ม และเงื่อนไขการโหลด คิดเสียว่าเป็นตัวแปรที่ถูกประเมินค่าและแทนที่ด้วยค่าจริงเมื่อเลย์เอาต์ของคุณถูกแสดงผล

# ข้อมูลทั่วไป

## ไวยากรณ์พื้นฐาน
ตัวแทนที่ใช้แทนค่าใน FancyMenu ใช้ไวยากรณ์คล้าย JSON:
```
{"placeholder":"modversion","values":{"modid":"fancymenu"}}
```

ตัวอย่างเช่น หากต้องการแสดงชื่อผู้เล่น:
```
{"placeholder":"playername"}
```

## การซ้อนตัวแทนที่ใช้แทนค่า
หนึ่งในฟีเจอร์ที่ทรงพลังที่สุดของระบบตัวแทนที่ใช้แทนค่าใน FancyMenu คือความสามารถในการซ้อนตัวแทนที่ใช้แทนค่าไว้ภายในตัวแทนที่ใช้แทนค่าอื่นๆ ซึ่งหมายความว่าคุณสามารถใช้ผลลัพธ์ของตัวแทนหนึ่งเป็นอินพุตของอีกตัวหนึ่งได้

ตัวอย่างของตัวแทนที่ใช้แทนค่าซ้อนกัน:
```
{"placeholder":"calc","values":{"decimal":"true","expression":"{"placeholder":"maxram"} / 1024"}}
```
ตัวอย่างนี้นำค่าหน่วยความจำ RAM สูงสุดมาหารด้วย 1024 เพื่อแปลงจาก MB เป็น GB

# การใช้งานตัวแทนที่ใช้แทนค่า

องค์ประกอบส่วนใหญ่ที่มีช่องใส่ข้อความรองรับตัวแทนที่ใช้แทนค่าได้ คุณสามารถดูได้ว่าช่องใส่ข้อความรองรับตัวแทนที่ใช้แทนค่าหรือไม่เมื่อกำลังแก้ไข ถ้าเปิด **ตัวแก้ไขข้อความ** แบบเต็มหน้าจอเมื่อแก้ไขข้อความ แสดงว่ามันรองรับตัวแทนที่ใช้แทนค่า

หากต้องการดู **รายการตัวแทนที่ใช้แทนค่าทั้งหมด** เพียงคลิกปุ่ม **Placeholders** ที่ **มุมขวาบน** ของ **ตัวแก้ไขข้อความ**

ด้านบนของรายการตัวแทนที่ใช้แทนค่าจะมี **แถบค้นหา** ให้คุณค้นหาตัวแทนที่ต้องการได้

การคลิกตัวแทนที่ใช้แทนค่าในรายการ จะเป็นการวางมันลงในเนื้อหาข้อความ

# รายละเอียดตัวแทนที่ใช้แทนค่า

รายการนี้มีตัวแทนที่ใช้แทนค่าที่มีอยู่ใน FancyMenu เกือบทั้งหมดหรือทั้งหมด รายการนี้อาจล้าสมัยได้บ้างเป็นครั้งคราวเนื่องจากมีการอัปเดตของม็อด

## ชื่อผู้เล่น (playername)
ส่งกลับชื่อผู้เล่นปัจจุบัน
```
{"placeholder":"playername"}
```
ตัวอย่างผลลัพธ์: `Steve`

## UUID ของผู้เล่น (playeruuid)
ส่งกลับรหัสระบุเฉพาะของผู้เล่น
```
{"placeholder":"playeruuid"}
```
ตัวอย่างผลลัพธ์: `c8cde7fe-7ced-11eb-9439-0242ac130002`

## เวอร์ชัน Minecraft (mcversion)
ส่งกลับเวอร์ชัน Minecraft ปัจจุบัน
```
{"placeholder":"mcversion"}
```
ตัวอย่างผลลัพธ์: `1.19.2`

## เวอร์ชันตัวโหลดม็อด (loaderver)
ส่งกลับเวอร์ชันของตัวโหลดม็อด (Forge/Fabric)
```
{"placeholder":"loaderver"}
```
ตัวอย่างผลลัพธ์: `43.2.0`

## ชื่อตัวโหลดม็อด (loadername)
ส่งกลับชื่อตัวโหลดม็อด
```
{"placeholder":"loadername"}
```
ตัวอย่างผลลัพธ์: `Forge`

## เวอร์ชันม็อด (modversion)
ส่งกลับเวอร์ชันของม็อดที่ระบุ
```
{"placeholder":"modversion","values":{"modid":"fancymenu"}}
```
ตัวอย่างผลลัพธ์: `2.14.9`

## จำนวนม็อดทั้งหมด (totalmods)
ส่งกลับจำนวนม็อดที่ติดตั้งทั้งหมด
```
{"placeholder":"totalmods"}
```
ตัวอย่างผลลัพธ์: `45`

## จำนวนม็อดที่ใช้งานอยู่ (loadedmods)
ส่งกลับจำนวนม็อดที่กำลังโหลดอยู่ในขณะนี้
```
{"placeholder":"loadedmods"}
```
ตัวอย่างผลลัพธ์: `43`

## ความคืบหน้าการโหลดโลก (world_load_progress)
ส่งกลับความคืบหน้าการโหลดโลกปัจจุบันเป็นเปอร์เซ็นต์
```
{"placeholder":"world_load_progress"}
```
ตัวอย่างผลลัพธ์: `75`

## ค่าตัวเลือกของ Minecraft (minecraft_option_value)
ส่งกลับค่าของตัวเลือก Minecraft
```
{"placeholder":"minecraft_option_value","values":{"name":"fov"}}
```
ตัวอย่างผลลัพธ์: `70`

## โลกหรือเซิร์ฟเวอร์ล่าสุด (last_world_server)
ส่งกลับข้อมูลเกี่ยวกับโลกหรือเซิร์ฟเวอร์ล่าสุดที่เข้าถึง
```
{"placeholder":"last_world_server","values":{"type":"both","full_world_path":"true"}}
```
พารามิเตอร์:
- `type`: กำหนดว่าต้องการข้อมูลประเภทใด
  - `"both"`: ส่งกลับโลกหรือเซิร์ฟเวอร์ล่าสุดที่เข้าถึง (ค่าเริ่มต้น)
  - `"server"`: ส่งกลับเฉพาะถ้าล่าสุดที่เข้าถึงคือเซิร์ฟเวอร์
  - `"world"`: ส่งกลับเฉพาะถ้าล่าสุดที่เข้าถึงคือโลก
- `full_world_path`: ควบคุมวิธีแสดงพาธของโลก
  - `"true"`: ส่งกลับพาธเต็มของโลก (ค่าเริ่มต้น)
  - `"false"`: ส่งกลับเฉพาะชื่อโลกโดยไม่รวมพาธ (ไม่มีผลกับเซิร์ฟเวอร์)

ตัวอย่าง:
- เซิร์ฟเวอร์: `mc.hypixel.net`
- โลกแบบมีพาธเต็ม: `saves/New World`
- โลกแบบไม่มีพาธเต็ม: `New World`

## ความกว้างของหน้าจอ (guiwidth)
ส่งกลับความกว้างของหน้าจอปัจจุบัน
```
{"placeholder":"guiwidth"}
```
ตัวอย่างผลลัพธ์: `1920`

## ความสูงของหน้าจอ (guiheight)
ส่งกลับความสูงของหน้าจอปัจจุบัน
```
{"placeholder":"guiheight"}
```
ตัวอย่างผลลัพธ์: `1080`

## ตัวระบุหน้าจอปัจจุบัน (screenid)
ส่งกลับตัวระบุของหน้าจอปัจจุบัน
```
{"placeholder":"screenid"}
```
ตัวอย่างผลลัพธ์: `title_screen`

## ความกว้างขององค์ประกอบ (elementwidth)
ส่งกลับความกว้างขององค์ประกอบที่ระบุ
```
{"placeholder":"elementwidth","values":{"id":"my_button"}}
```
ตัวอย่างผลลัพธ์: `200`

## ความสูงขององค์ประกอบ (elementheight)
ส่งกลับความสูงขององค์ประกอบที่ระบุ
```
{"placeholder":"elementheight","values":{"id":"my_button"}}
```
ตัวอย่างผลลัพธ์: `20`

## ตำแหน่ง X ขององค์ประกอบ (elementposx)
ส่งกลับตำแหน่ง X ขององค์ประกอบที่ระบุ
```
{"placeholder":"elementposx","values":{"id":"my_button"}}
```
ตัวอย่างผลลัพธ์: `150`

## ตำแหน่ง Y ขององค์ประกอบ (elementposy)
ส่งกลับตำแหน่ง Y ขององค์ประกอบที่ระบุ
```
{"placeholder":"elementposy","values":{"id":"my_button"}}
```
ตัวอย่างผลลัพธ์: `100`

## ตำแหน่ง X ของเมาส์ (mouseposx)
ส่งกลับตำแหน่ง X ปัจจุบันของเมาส์
```
{"placeholder":"mouseposx"}
```
ตัวอย่างผลลัพธ์: `960`

## ตำแหน่ง Y ของเมาส์ (mouseposy)
ส่งกลับตำแหน่ง Y ปัจจุบันของเมาส์
```
{"placeholder":"mouseposy"}
```
ตัวอย่างผลลัพธ์: `540`

## จำนวนคลิกต่อวินาที (clicks_per_second)
ส่งกลับจำนวนคลิกต่อวินาทีปัจจุบันของปุ่มเมาส์
```
{"placeholder":"clicks_per_second","values":{"mouse_button":"left"}}
```
พารามิเตอร์:
- `mouse_button`: `left` หรือ `right`

ตัวอย่างผลลัพธ์: `8`

## สเกล GUI (guiscale)
ส่งกลับสเกล GUI ปัจจุบัน
```
{"placeholder":"guiscale"}
```
ตัวอย่างผลลัพธ์: `2`

## ป้ายชื่อ/ข้อความของวิดเจ็ตแบบวานิลลา (vanillabuttonlabel)
ส่งกลับป้ายชื่อ/ข้อความของวิดเจ็ตหรือปุ่มแบบวานิลลา
```
{"placeholder":"vanillabuttonlabel","values":{"locator":"some.menu.identifier:505280"}}
```
ตัวอย่างผลลัพธ์: `Options...`

## ค่าของช่องกรอกข้อความ (text_input_field_value)
ส่งกลับค่าปัจจุบันของช่องกรอกข้อความแบบกำหนดเองหรือแบบวานิลลาตามตัวระบุองค์ประกอบ
```
{"placeholder":"text_input_field_value","values":{"element_identifier":"my_input"}}
```
ตัวอย่างผลลัพธ์: `Hello World`

## พลังชีวิตปัจจุบันของผู้เล่น (current_player_health)
ส่งกลับพลังชีวิตปัจจุบันของผู้เล่น
```
{"placeholder":"current_player_health"}
```
ตัวอย่างผลลัพธ์: `20.0`

## พลังชีวิตสูงสุดของผู้เล่น (max_player_health)
ส่งกลับพลังชีวิตสูงสุดของผู้เล่น
```
{"placeholder":"max_player_health"}
```
ตัวอย่างผลลัพธ์: `20.0`

## พลังชีวิตปัจจุบันของผู้เล่น (เปอร์เซ็นต์) (current_player_health_percent)
ส่งกลับพลังชีวิตของผู้เล่นเป็นเปอร์เซ็นต์
```
{"placeholder":"current_player_health_percent"}
```
ตัวอย่างผลลัพธ์: `100`

## พลังชีวิตดูดซับปัจจุบันของผู้เล่น (current_player_absorption_health)
ส่งกลับพลังชีวิตดูดซับของผู้เล่น (หัวใจทอง)
```
{"placeholder":"current_player_absorption_health"}
```
ตัวอย่างผลลัพธ์: `4.0`

## พลังชีวิตดูดซับสูงสุดของผู้เล่น (max_player_absorption_health)
ส่งกลับพลังชีวิตดูดซับสูงสุด
```
{"placeholder":"max_player_absorption_health"}
```
ตัวอย่างผลลัพธ์: `4.0`

## พลังชีวิตดูดซับปัจจุบันของผู้เล่น (เปอร์เซ็นต์) (current_player_absorption_health_percent)
ส่งกลับพลังชีวิตดูดซับของผู้เล่นเป็นเปอร์เซ็นต์
```
{"placeholder":"current_player_absorption_health_percent"}
```
ตัวอย่างผลลัพธ์: `100`

## ระดับความหิวปัจจุบันของผู้เล่น (current_player_hunger)
ส่งกลับระดับความหิวปัจจุบันของผู้เล่น
```
{"placeholder":"current_player_hunger"}
```
ตัวอย่างผลลัพธ์: `20`

## ระดับความหิวสูงสุดของผู้เล่น (max_player_hunger)
ส่งกลับระดับความหิวสูงสุด
```
{"placeholder":"max_player_hunger"}
```
ตัวอย่างผลลัพธ์: `20`

## ระดับความหิวปัจจุบันของผู้เล่น (เปอร์เซ็นต์) (current_player_hunger_percent)
ส่งกลับความหิวของผู้เล่นเป็นเปอร์เซ็นต์
```
{"placeholder":"current_player_hunger_percent"}
```
ตัวอย่างผลลัพธ์: `100`

## ค่าความอิ่มของผู้เล่น (current_player_hunger_saturation)
ส่งกลับค่าความอิ่มปัจจุบันของผู้เล่น
```
{"placeholder":"current_player_hunger_saturation"}
```
ตัวอย่างผลลัพธ์: `5.0`

## เกราะปัจจุบันของผู้เล่น (current_player_armor)
ส่งกลับค่าเกราะปัจจุบันของผู้เล่น
```
{"placeholder":"current_player_armor"}
```
ตัวอย่างผลลัพธ์: `20`

## ความทนทานเกราะของผู้เล่น (player_armor_toughness)
ส่งกลับค่าความทนทานเกราะรวมของผู้เล่น
```
{"placeholder":"player_armor_toughness"}
```
ตัวอย่างผลลัพธ์: `8.0`

## เกราะสูงสุดของผู้เล่น (max_player_armor)
ส่งกลับค่าเกราะสูงสุด
```
{"placeholder":"max_player_armor"}
```
ตัวอย่างผลลัพธ์: `20`

## เกราะปัจจุบันของผู้เล่น (เปอร์เซ็นต์) (current_player_armor_percent)
ส่งกลับเกราะของผู้เล่นเป็นเปอร์เซ็นต์
```
{"placeholder":"current_player_armor_percent"}
```
ตัวอย่างผลลัพธ์: `100`

## ระดับออกซิเจนปัจจุบันของผู้เล่น (current_player_oxygen)
ส่งกลับระดับออกซิเจนปัจจุบันของผู้เล่น (ฟองอากาศ)
```
{"placeholder":"current_player_oxygen"}
```
ตัวอย่างผลลัพธ์: `300`

## ระดับออกซิเจนสูงสุดของผู้เล่น (max_player_oxygen)
ส่งกลับระดับออกซิเจนสูงสุด
```
{"placeholder":"max_player_oxygen"}
```
ตัวอย่างผลลัพธ์: `300`

## ระดับออกซิเจนปัจจุบันของผู้เล่น (เปอร์เซ็นต์) (current_player_oxygen_percent)
ส่งกลับระดับออกซิเจนของผู้เล่นเป็นเปอร์เซ็นต์
```
{"placeholder":"current_player_oxygen_percent"}
```
ตัวอย่างผลลัพธ์: `100`

## เลเวลปัจจุบันของผู้เล่น (current_player_level)
ส่งกลับเลเวลประสบการณ์ปัจจุบันของผู้เล่น
```
{"placeholder":"current_player_level"}
```
ตัวอย่างผลลัพธ์: `30`

## ค่าประสบการณ์ปัจจุบันของผู้เล่น (current_player_exp)
ส่งกลับค่าประสบการณ์รวมของผู้เล่น
```
{"placeholder":"current_player_exp"}
```
ตัวอย่างผลลัพธ์: `1250`

## ความคืบหน้าประสบการณ์ของผู้เล่น (เปอร์เซ็นต์) (current_player_exp_progress)
ส่งกลับความคืบหน้าประสบการณ์ของผู้เล่นไปยังเลเวลถัดไปเป็นเปอร์เซ็นต์
```
{"placeholder":"current_player_exp_progress"}
```
ตัวอย่างผลลัพธ์: `75`

## พลังโจมตีของผู้เล่น (เปอร์เซ็นต์) (player_attack_strength)
ส่งกลับคูลดาวน์การโจมตีของผู้เล่นเป็นเปอร์เซ็นต์
```
{"placeholder":"player_attack_strength"}
```
ตัวอย่างผลลัพธ์: `100`

## โหมดเกมของผู้เล่น (player_gamemode)
ส่งกลับโหมดเกมปัจจุบันของผู้เล่น
```
{"placeholder":"player_gamemode"}
```
ตัวอย่างผลลัพธ์: `survival`

## ทิศทางที่ผู้เล่นกำลังมอง (player_view_direction)
ส่งกลับทิศทางที่ผู้เล่นหันหน้าอยู่
```
{"placeholder":"player_view_direction"}
```
ตัวอย่างผลลัพธ์: `north`

## พิกัด X ของผู้เล่น (player_x_coordinate)
ส่งกลับตำแหน่ง X ของผู้เล่นในโลก
```
{"placeholder":"player_x_coordinate"}
```
ตัวอย่างผลลัพธ์: `125`

## พิกัด Y ของผู้เล่น (player_y_coordinate)
ส่งกลับตำแหน่ง Y ของผู้เล่นในโลก
```
{"placeholder":"player_y_coordinate"}
```
ตัวอย่างผลลัพธ์: `64`

## พิกัด Z ของผู้เล่น (player_z_coordinate)
ส่งกลับตำแหน่ง Z ของผู้เล่นในโลก
```
{"placeholder":"player_z_coordinate"}
```
ตัวอย่างผลลัพธ์: `-250`

## พลังชีวิตปัจจุบันของพาหนะที่ขี่อยู่ (current_mount_health)
ส่งกลับพลังชีวิตปัจจุบันของเอนทิตีที่ผู้เล่นกำลังขี่อยู่
```
{"placeholder":"current_mount_health"}
```
ตัวอย่างผลลัพธ์: `30.0`

## พลังชีวิตสูงสุดของพาหนะที่ขี่อยู่ (max_mount_health)
ส่งกลับพลังชีวิตสูงสุดของเอนทิตีที่ผู้เล่นกำลังขี่อยู่
```
{"placeholder":"max_mount_health"}
```
ตัวอย่างผลลัพธ์: `30.0`

## พลังชีวิตปัจจุบันของพาหนะที่ขี่อยู่ (เปอร์เซ็นต์) (current_mount_health_percent)
ส่งกลับพลังชีวิตของพาหนะเป็นเปอร์เซ็นต์
```
{"placeholder":"current_mount_health_percent"}
```
ตัวอย่างผลลัพธ์: `100`

## ค่าชาร์จการกระโดดของพาหนะปัจจุบัน (เปอร์เซ็นต์) (current_mount_jump_meter)
ส่งกลับค่ามิเตอร์พลังการกระโดดของพาหนะ
```
{"placeholder":"current_mount_jump_meter"}
```
ตัวอย่างผลลัพธ์: `75`

## พลังชีวิตบอสปัจจุบัน (เปอร์เซ็นต์) (current_boss_health)
ส่งกลับพลังชีวิตของบอสที่กำลังอยู่ในสถานะใช้งาน
```
{"placeholder":"current_boss_health"}
```
ตัวอย่างผลลัพธ์: `150.0`

## ชื่อบอส (boss_name)
ส่งกลับชื่อของบอสที่กำลังใช้งาน
```
{"placeholder":"boss_name","values":{"boss_index":"0","as_json":"false"}}
```
ตัวอย่างผลลัพธ์: `Ender Dragon`

## จำนวนบอส (boss_count)
ส่งกลับจำนวนบอสที่กำลังใช้งาน
```
{"placeholder":"boss_count"}
```
ตัวอย่างผลลัพธ์: `1`

## จำนวนเอฟเฟกต์ที่ใช้งานอยู่ (effects_count)
ส่งกลับจำนวนเอฟเฟกต์ยาที่กำลังใช้งานอยู่
```
{"placeholder":"effects_count"}
```
ตัวอย่างผลลัพธ์: `3`

## เอฟเฟกต์ที่ใช้งานอยู่ (active_effect)
ส่งกลับข้อมูลเกี่ยวกับเอฟเฟกต์ที่ใช้งานอยู่ที่ระบุ
```
{"placeholder":"active_effect","values":{"effect_index":"0"}}
```
ตัวอย่างผลลัพธ์: `minecraft:speed`

## ช่องฮอตบาร์ที่เลือกอยู่ (active_hotbar_slot)
ส่งกลับช่องฮอตบาร์ที่ถูกเลือกอยู่ในขณะนี้ (0-8)
```
{"placeholder":"active_hotbar_slot"}
```
ตัวอย่างผลลัพธ์: `4`

## ไอเทมในช่อง (slot_item)
ส่งกลับข้อมูลเกี่ยวกับไอเทมในช่องอินเวนทอรีที่ระบุ
```
{"placeholder":"slot_item","values":{"slot":"0"}}
```
ตัวอย่างผลลัพธ์: `minecraft:diamond_sword`

## จำนวนไอเทมในช่อง (slot_item_count)
ส่งกลับขนาดสแตกของไอเทมในช่องอินเวนทอรีของผู้เล่นที่ระบุ
```
{"placeholder":"slot_item_count","values":{"slot":"0"}}
```
ตัวอย่างผลลัพธ์: `64`

## ความทนทานของไอเทมในช่อง (slot_item_durability)
ส่งกลับข้อมูลความทนทานของไอเทมในช่องอินเวนทอรีของผู้เล่นที่ระบุ
```
{"placeholder":"slot_item_durability","values":{"slot":"0","format":"percentage"}}
```
พารามิเตอร์:
- `slot`: หมายเลขช่องอินเวนทอรีของผู้เล่น
- `format`: `current`, `remaining`, `max`, `damage`, `percentage`, หรือ `percent`

ตัวอย่างผลลัพธ์: `87`

## ชื่อที่แสดงของไอเทมในช่อง (slot_item_display_name_fm)
ส่งกลับชื่อที่แสดงของไอเทมในช่องที่ระบุในรูปแบบคอมโพเนนต์ข้อความ JSON ในโหมดผู้ชม ช่องฮอตบาร์อาจแสดงชื่อไอเทมเมนูผู้ชมได้ เว้นแต่ `ignore_spectator` จะเป็น `true`
```
{"placeholder":"slot_item_display_name_fm","values":{"slot":"0","ignore_spectator":"false"}}
```
ตัวอย่างผลลัพธ์: `{"text":"Diamond Sword","color":"aqua"}`

## จำนวนไอเทมในอินเวนทอรี (inventory_item_count)
ส่งกลับจำนวนรวมของไอเทมชนิดที่ระบุในอินเวนทอรีของผู้เล่น ถ้า `item` ว่าง จะนับสแตกไอเทมทั้งหมดในอินเวนทอรี
```
{"placeholder":"inventory_item_count","values":{"item":"minecraft:diamond"}}
```
ตัวอย่างผลลัพธ์: `12`

## จำนวนที่ฟื้นฟูความหิวของอาหารในช่องอินเวนทอรี (inventory_slot_food_point_restore_amount)
ส่งกลับคะแนนความหิวที่ฟื้นฟูได้โดยไอเทมอาหารในช่องอินเวนทอรีของผู้เล่นที่ระบุ
```
{"placeholder":"inventory_slot_food_point_restore_amount","values":{"slot":"0"}}
```
ตัวอย่างผลลัพธ์: `4.0`

## ไอเทมในอินเวนทอรีที่ชี้อยู่ (hovered_inventory_item)
ส่งกลับคีย์ไอเทมที่กำลังชี้อยู่ในหน้าจออินเวนทอรี
```
{"placeholder":"hovered_inventory_item"}
```
ตัวอย่างผลลัพธ์: `minecraft:apple`

## เวลาของโลกในเกม (game_time)
ส่งกลับตัวนับ tick ของเวลาในเกมปัจจุบัน
```
{"placeholder":"game_time"}
```
ตัวอย่างผลลัพธ์: `18000`

## เวลากลางวันของโลก (world_daytime)
ส่งกลับเวลาในโลกปัจจุบัน
```
{"placeholder":"world_daytime"}
```
ตัวอย่างผลลัพธ์: `13000`

## ชั่วโมงของเวลากลางวันในโลก (world_daytime_hour)
ส่งกลับองค์ประกอบชั่วโมงของเวลาในโลก โดยปกติจะใช้รูปแบบ 24 ชั่วโมง; ตั้งค่า `twelve_hour_format` เป็น `"true"` หากต้องการรูปแบบ 12 ชั่วโมง
```
{"placeholder":"world_daytime_hour","values":{"twelve_hour_format":"false"}}
```
ตัวอย่างผลลัพธ์: `12`

## นาทีของเวลากลางวันในโลก (world_daytime_minute)
ส่งกลับองค์ประกอบนาทีของเวลาในโลก (00-59)
```
{"placeholder":"world_daytime_minute"}
```
ตัวอย่างผลลัพธ์: `30`

## ความยากของโลก (world_difficulty)
ส่งกลับความยากของโลกปัจจุบัน
```
{"placeholder":"world_difficulty"}
```
ตัวอย่างผลลัพธ์: `normal`

## ซีดโลกปัจจุบัน (current_world_seed)
ส่งกลับซีดของโลกผู้เล่นคนเดียวปัจจุบัน คืนค่าว่างเมื่อไม่สามารถเข้าถึงซีดได้
```
{"placeholder":"current_world_seed"}
```
ตัวอย่างผลลัพธ์: `123456789`

## ไบโอมปัจจุบัน (current_biome)
ส่งกลับไบโอมที่ผู้เล่นอยู่ในขณะนี้ ตั้งค่า `as_key` เป็น `"false"` เพื่อส่งกลับชื่อที่แปลแล้ว/ชื่อที่แสดง หากมี
```
{"placeholder":"current_biome","values":{"as_key":"true"}}
```
ตัวอย่างผลลัพธ์: `minecraft:plains`

## ดิมเมนชันปัจจุบัน (current_dimension)
ส่งกลับดิมเมนชันที่ผู้เล่นอยู่ในขณะนี้ ตั้งค่า `as_key` เป็น `"false"` เพื่อส่งกลับชื่อที่แปลแล้ว/ชื่อที่แสดง หากมี
```
{"placeholder":"current_dimension","values":{"as_key":"true"}}
```
ตัวอย่างผลลัพธ์: `minecraft:overworld`

## ค่ากฎของเกม (gamerule_value)
ส่งกลับค่าปัจจุบันของ gamerule ในโลก/เซิร์ฟเวอร์ที่โหลดอยู่ เซิร์ฟเวอร์จะต้องมี FancyMenu ติดตั้งบนฝั่งเซิร์ฟเวอร์ด้วย
```
{"placeholder":"gamerule_value","values":{"name":"doDaylightCycle"}}
```
ตัวอย่างผลลัพธ์: `true`

## หมวดหมู่ของไอเทม (item_category)
ส่งกลับหมวดหมู่แท็บสร้างสรรค์ของไอเทม ตั้งค่า `as_key` เป็น `"true"` เพื่อส่งกลับคีย์ของหมวดหมู่แทนชื่อที่แสดง
```
{"placeholder":"item_category","values":{"item":"minecraft:diamond_sword","as_key":"false"}}
```
ตัวอย่างผลลัพธ์: `Combat`

## ชื่อ/คำบรรยาย HUD ปัจจุบัน (current_title)
ส่งกลับข้อความชื่อที่แสดงอยู่ในขณะนี้
```
{"placeholder":"current_title","values":{"is_subtitle":"false","as_json":"false"}}
```
ตัวอย่างผลลัพธ์: `Game Over!`

## ข้อความแถบแอ็กชัน (action_bar_message_fm)
ส่งกลับข้อความแถบแอ็กชันวานิลลาปัจจุบันที่แสดงเหนือฮอตบาร์
```
{"placeholder":"action_bar_message_fm"}
```
ตัวอย่างผลลัพธ์: `You may not rest now`

## เวลาของข้อความแถบแอ็กชัน (action_bar_message_time_fm)
ส่งกลับจำนวน tick ที่ข้อความแถบแอ็กชันวานิลลาปัจจุบันจะยังคงแสดงอยู่
```
{"placeholder":"action_bar_message_time_fm"}
```
ตัวอย่างผลลัพธ์: `42`

## การหมุนกล้อง X (camera_rotation_x_fm)
ส่งกลับมุมก้มเงยของกล้องปัจจุบันเป็นองศา
```
{"placeholder":"camera_rotation_x_fm"}
```
ตัวอย่างผลลัพธ์: `12.5`

## การหมุนกล้อง Y (camera_rotation_y_fm)
ส่งกลับมุมหันซ้ายขวาของกล้องปัจจุบันเป็นองศา
```
{"placeholder":"camera_rotation_y_fm"}
```
ตัวอย่างผลลัพธ์: `-90.0`

## การเปลี่ยนแปลงการหมุนกล้อง X (camera_rotation_delta_x_fm)
ส่งกลับการเปลี่ยนแปลงมุมก้มเงยของกล้องต่อหนึ่ง tick
```
{"placeholder":"camera_rotation_delta_x_fm"}
```
ตัวอย่างผลลัพธ์: `0.4`

## การเปลี่ยนแปลงการหมุนกล้อง Y (camera_rotation_delta_y_fm)
ส่งกลับการเปลี่ยนแปลงมุมหันซ้ายขวาของกล้องต่อหนึ่ง tick
```
{"placeholder":"camera_rotation_delta_y_fm"}
```
ตัวอย่างผลลัพธ์: `-1.2`

## เวลาของชื่อไอเทมที่ถูกไฮไลต์ (highlighted_item_time_fm)
ส่งกลับจำนวน tick ที่ชื่อไอเทมที่ถูกไฮไลต์จะยังคงแสดงเหนือฮอตบาร์
```
{"placeholder":"highlighted_item_time_fm"}
```
ตัวอย่างผลลัพธ์: `30`

## ความคืบหน้าการใช้ไอเทมของผู้เล่น (player_item_use_progress_fm)
ส่งกลับความคืบหน้าการใช้ไอเทมปัจจุบันตั้งแต่ `0.0` ถึง `1.0`
```
{"placeholder":"player_item_use_progress_fm"}
```
ตัวอย่างผลลัพธ์: `0.65`

## การเปลี่ยนแปลงตำแหน่งผู้เล่น X (player_position_delta_x_fm)
ส่งกลับการเปลี่ยนแปลงตำแหน่งผู้เล่นตามแกน X ต่อหนึ่ง tick
```
{"placeholder":"player_position_delta_x_fm"}
```
ตัวอย่างผลลัพธ์: `0.0`

## การเปลี่ยนแปลงตำแหน่งผู้เล่น Y (player_position_delta_y_fm)
ส่งกลับการเปลี่ยนแปลงตำแหน่งผู้เล่นตามแกน Y ต่อหนึ่ง tick
```
{"placeholder":"player_position_delta_y_fm"}
```
ตัวอย่างผลลัพธ์: `-0.08`

## การเปลี่ยนแปลงตำแหน่งผู้เล่น Z (player_position_delta_z_fm)
ส่งกลับการเปลี่ยนแปลงตำแหน่งผู้เล่นตามแกน Z ต่อหนึ่ง tick
```
{"placeholder":"player_position_delta_z_fm"}
```
ตัวอย่างผลลัพธ์: `0.12`

## IP เซิร์ฟเวอร์ปัจจุบัน (current_server_ip)
ส่งกลับ IP ของเซิร์ฟเวอร์ที่เชื่อมต่ออยู่
```
{"placeholder":"current_server_ip"}
```
ตัวอย่างผลลัพธ์: `mc.hypixel.net`

## รายชื่อผู้เล่นในโลก (world_players_list)
ส่งกลับรายชื่อผู้เล่นทั้งหมดที่อยู่ในโลกปัจจุบัน
```
{"placeholder":"world_players_list","values":{"separator":", "}}
```
ตัวอย่างผลลัพธ์: `Steve, Alex, Notch`

## MOTD ของเซิร์ฟเวอร์ (servermotd)
ส่งกลับข้อความประจำวันของเซิร์ฟเวอร์
```
{"placeholder":"servermotd","values":{"ip":"mc.hypixel.net","line":"1"}}
```
ตัวอย่างผลลัพธ์: `Welcome to Hypixel!`

## ค่า PING ของเซิร์ฟเวอร์ (serverping)
ส่งกลับค่า ping ไปยังเซิร์ฟเวอร์เป็นมิลลิวินาที
```
{"placeholder":"serverping","values":{"ip":"mc.hypixel.net"}}
```
ตัวอย่างผลลัพธ์: `54`

## จำนวนผู้เล่นบนเซิร์ฟเวอร์ (serverplayercount)
ส่งกลับจำนวนผู้เล่นของเซิร์ฟเวอร์
```
{"placeholder":"serverplayercount","values":{"ip":"mc.hypixel.net"}}
```
ตัวอย่างผลลัพธ์: `25000/30000`

## สถานะเซิร์ฟเวอร์ (serverstatus)
ส่งกลับสถานะออนไลน์/ออฟไลน์ของเซิร์ฟเวอร์
```
{"placeholder":"serverstatus","values":{"ip":"mc.hypixel.net"}}
```
ตัวอย่างผลลัพธ์: `§aOnline` หรือ `§cOffline`

## เวอร์ชันเซิร์ฟเวอร์ (serverversion)
ส่งกลับเวอร์ชัน Minecraft ของเซิร์ฟเวอร์
```
{"placeholder":"serverversion","values":{"ip":"mc.hypixel.net"}}
```
ตัวอย่างผลลัพธ์: `1.19.2`

## ปี (realtimeyear)
ส่งกลับปีปัจจุบัน
```
{"placeholder":"realtimeyear"}
```
ตัวอย่างผลลัพธ์: `2024`

## เดือน (realtimemonth)
ส่งกลับเดือนปัจจุบัน (01-12)
```
{"placeholder":"realtimemonth"}
```
ตัวอย่างผลลัพธ์: `01`

## วัน (realtimeday)
ส่งกลับวันที่ปัจจุบันของเดือน (01-31)
```
{"placeholder":"realtimeday"}
```
ตัวอย่างผลลัพธ์: `27`

## ชั่วโมง (realtimehour)
ส่งกลับชั่วโมงปัจจุบัน โดยปกติจะใช้รูปแบบ 24 ชั่วโมง; ตั้งค่า `twelve_hour_format` เป็น `"true"` หากต้องการรูปแบบ 12 ชั่วโมง
```
{"placeholder":"realtimehour","values":{"twelve_hour_format":"false","timezone":"system"}}
```
ตัวอย่างผลลัพธ์: `14`

## นาที (realtimeminute)
ส่งกลับนาทีปัจจุบัน (00-59)
```
{"placeholder":"realtimeminute"}
```
ตัวอย่างผลลัพธ์: `30`

## วินาที (realtimesecond)
ส่งกลับวินาทีปัจจุบัน (00-59)
```
{"placeholder":"realtimesecond"}
```
ตัวอย่างผลลัพธ์: `45`

## เวลาเป็นมิลลิวินาทีปัจจุบัน (Unix Timestamp) (unix_time)
ส่งกลับ Unix timestamp ปัจจุบันเป็นมิลลิวินาที
```
{"placeholder":"unix_time"}
```
ตัวอย่างผลลัพธ์: `1716552478123`

> ตัวแทนที่ใช้แทนค่าแบบเรียลไทม์ (`realtimeyear`, `realtimemonth`, `realtimeday`, `realtimehour`, `realtimeminute`, `realtimesecond`, และ `unix_time`) รองรับค่า `timezone` ใช้รหัสเขตเวลา Java แบบปกติ เช่น `UTC`, `Europe/Berlin`, หรือ `America/New_York`; หรือไม่ระบุค่า หรือใช้ `system` เพื่อใช้เขตเวลาของระบบ
{.is-info}

## ข้อมูล CPU (cpuinfo)
ส่งกลับข้อมูลเกี่ยวกับ CPU
```
{"placeholder":"cpuinfo"}
```
ตัวอย่างผลลัพธ์: `Intel(R) Core(TM) i7-10700K CPU @ 3.80GHz`

## การใช้งาน CPU (JVM) (jvmcpu)
ส่งกลับการใช้งาน CPU ของ JVM เป็นเปอร์เซ็นต์
```
{"placeholder":"jvmcpu"}
```
ตัวอย่างผลลัพธ์: `25.5`

## การใช้งาน CPU (ระบบปฏิบัติการ) (oscpu)
ส่งกลับการใช้งาน CPU ของระบบปฏิบัติการเป็นเปอร์เซ็นต์
```
{"placeholder":"oscpu"}
```
ตัวอย่างผลลัพธ์: `42.8`

## ข้อมูล GPU (gpuinfo)
ส่งกลับข้อมูลเกี่ยวกับ GPU
```
{"placeholder":"gpuinfo"}
```
ตัวอย่างผลลัพธ์: `NVIDIA GeForce RTX 3080`

## เวอร์ชัน Java (javaver)
ส่งกลับเวอร์ชัน Java
```
{"placeholder":"javaver"}
```
ตัวอย่างผลลัพธ์: `17.0.2`

## เครื่องเสมือน Java (jvmname)
ส่งกลับชื่อของ Java Virtual Machine
```
{"placeholder":"jvmname"}
```
ตัวอย่างผลลัพธ์: `OpenJDK 64-Bit Server VM`

## เวอร์ชัน OpenGL (glver)
ส่งกลับเวอร์ชัน OpenGL
```
{"placeholder":"glver"}
```
ตัวอย่างผลลัพธ์: `4.6.0 NVIDIA 516.94`

## ชื่อระบบปฏิบัติการ (osname)
ส่งกลับชื่อของระบบปฏิบัติการ
```
{"placeholder":"osname"}
```
ตัวอย่างผลลัพธ์: `Windows 10`

## FPS (Frames Per Second) (fps)
ส่งกลับจำนวนเฟรมต่อวินาทีปัจจุบัน
```
{"placeholder":"fps"}
```
ตัวอย่างผลลัพธ์: `120`

## RAM ที่ใช้อยู่ใน MB (usedram)
ส่งกลับปริมาณ RAM ที่กำลังใช้งานอยู่ (MB)
```
{"placeholder":"usedram"}
```
ตัวอย่างผลลัพธ์: `4096`

## RAM สูงสุดใน MB (maxram)
ส่งกลับ RAM สูงสุดที่จัดสรรไว้ (MB)
```
{"placeholder":"maxram"}
```
ตัวอย่างผลลัพธ์: `8192`

## RAM ที่ใช้อยู่ใน %% (percentram)
ส่งกลับเปอร์เซ็นต์ของ RAM ที่กำลังใช้งานอยู่
```
{"placeholder":"percentram"}
```
ตัวอย่างผลลัพธ์: `50`

## ระดับเสียงขององค์ประกอบเสียง (audio_element_vol)
ส่งกลับระดับเสียงขององค์ประกอบเสียง
```
{"placeholder":"audio_element_vol","values":{"element_identifier":"background_music"}}
```
ตัวอย่างผลลัพธ์: `0.5`

## แทร็กเสียงปัจจุบัน (audio_element_current_track)
ส่งกลับชื่อแทร็กขององค์ประกอบเสียง
```
{"placeholder":"audio_element_current_track","values":{"element_identifier":"background_music","display_name_mappings":"track1.ogg=>Cool Track Name"}}
```
ตัวอย่างผลลัพธ์: `Cool Track Name`

## ระยะเวลาของเสียง (audio_duration)
ส่งกลับระยะเวลารวมของแทร็กเสียงในรูปแบบ MM:SS
```
{"placeholder":"audio_duration","values":{"element_identifier":"background_music"}}
```
ตัวอย่างผลลัพธ์: `03:45`

## เวลาที่เล่นเสียงไปแล้ว (audio_playtime)
ส่งกลับเวลาที่เล่นอยู่ปัจจุบันของแทร็กเสียง ตั้งค่า `show_percentage` เป็น `"true"` เพื่อให้ส่งกลับค่า progress แบบ 0-100 แทน `MM:SS`
```
{"placeholder":"audio_playtime","values":{"element_identifier":"background_music","show_percentage":"false"}}
```
ตัวอย่างผลลัพธ์: `01:30` (หรือ `45` เมื่อ `show_percentage` เป็น `"true"`)

## สถานะการเล่นเสียง (audio_playing_state)
ส่งกลับว่าองค์ประกอบเสียงกำลังเล่นอยู่หรือไม่ (true/false)
```
{"placeholder":"audio_playing_state","values":{"element_identifier":"background_music"}}
```
ตัวอย่างผลลัพธ์: `true`

## ระดับเสียงขององค์ประกอบวิดีโอ (video_element_vol)
ส่งกลับระดับเสียงขององค์ประกอบวิดีโอ (0.0 ถึง 1.0)
```
{"placeholder":"video_element_vol","values":{"element_identifier":"my_video_element"}}
```
ตัวอย่างผลลัพธ์: `0.5`

## ระยะเวลาขององค์ประกอบวิดีโอ (video_element_duration)
ส่งกลับระยะเวลารวมขององค์ประกอบวิดีโอในรูปแบบ `MM:SS` ตั้งค่า `output_as_timestamp` เป็น `"true"` หากต้องการส่งกลับเป็น timestamp หน่วยมิลลิวินาที
```
{"placeholder":"video_element_duration","values":{"element_identifier":"my_video_element","output_as_timestamp":"false"}}
```
ตัวอย่างผลลัพธ์: `02:00` (หรือ `120000` เมื่อ `output_as_timestamp` เป็น `"true"`)

## เวลาที่เล่นขององค์ประกอบวิดีโอ (video_element_playtime)
ส่งกลับเวลาการเล่น (progress) ปัจจุบันขององค์ประกอบวิดีโอในรูปแบบ `MM:SS` ตั้งค่า `show_percentage` เป็น `"true"` เพื่อให้ได้ค่า progress แบบ 0-100 หรือ `output_as_timestamp` เป็น `"true"` เพื่อให้ได้หน่วยมิลลิวินาที
```
{"placeholder":"video_element_playtime","values":{"element_identifier":"my_video_element","show_percentage":"false","output_as_timestamp":"false"}}
```
ตัวอย่างผลลัพธ์: `00:45` (หรือ `38` เป็นเปอร์เซ็นต์, หรือ `45200` เป็น timestamp)

## สถานะหยุดชั่วคราวขององค์ประกอบวิดีโอ (video_element_paused_state)
ส่งกลับว่าองค์ประกอบวิดีโอหยุดชั่วคราวอยู่หรือไม่ (true/false)
```
{"placeholder":"video_element_paused_state","values":{"element_identifier":"my_video_element"}}
```
ตัวอย่างผลลัพธ์: `false`

## ระดับเสียงพื้นหลังวิดีโอ (video_background_vol)
ส่งกลับระดับเสียงของพื้นหลังเมนูวิดีโอ (0.0 ถึง 1.0)
```
{"placeholder":"video_background_vol","values":{"background_identifier":"main_menu_video"}}
```
ตัวอย่างผลลัพธ์: `0.7`

## ระยะเวลาพื้นหลังวิดีโอ (video_background_duration)
ส่งกลับระยะเวลารวมของพื้นหลังเมนูวิดีโอในรูปแบบ `MM:SS` ตั้งค่า `output_as_timestamp` เป็น `"true"` หากต้องการส่งกลับเป็น timestamp หน่วยมิลลิวินาที
```
{"placeholder":"video_background_duration","values":{"background_identifier":"main_menu_video","output_as_timestamp":"false"}}
```
ตัวอย่างผลลัพธ์: `03:00` (หรือ `180000` เมื่อ `output_as_timestamp` เป็น `"true"`)

## เวลาที่เล่นของพื้นหลังวิดีโอ (video_background_playtime)
ส่งกลับเวลาการเล่น (progress) ปัจจุบันของพื้นหลังเมนูวิดีโอในรูปแบบ `MM:SS` ตั้งค่า `show_percentage` เป็น `"true"` เพื่อให้ได้ค่า progress แบบ 0-100 หรือ `output_as_timestamp` เป็น `"true"` เพื่อให้ได้หน่วยมิลลิวินาที
```
{"placeholder":"video_background_playtime","values":{"background_identifier":"main_menu_video","show_percentage":"false","output_as_timestamp":"false"}}
```
ตัวอย่างผลลัพธ์: `01:00` (หรือ `33` เป็นเปอร์เซ็นต์, หรือ `60500` เป็น timestamp)

## สถานะหยุดชั่วคราวของพื้นหลังวิดีโอ (video_background_paused_state)
ส่งกลับว่าพื้นหลังเมนูวิดีโอหยุดชั่วคราวอยู่หรือไม่ (true/false)
```
{"placeholder":"video_background_paused_state","values":{"background_identifier":"main_menu_video"}}
```
ตัวอย่างผลลัพธ์: `true`

## เครื่องคิดเลข (calc)
ตัวแทนที่ใช้แทนค่าเครื่องคิดเลขเป็นเครื่องมือที่ทรงพลังซึ่งช่วยให้คุณทำการคำนวณทางคณิตศาสตร์ภายในเลย์เอาต์ได้ รองรับการดำเนินการทางคณิตศาสตร์หลากหลายรูปแบบ และใช้งานได้ทั้งกับเลขทศนิยมและจำนวนเต็ม

### ไวยากรณ์พื้นฐาน
```
{"placeholder":"calc","values":{"decimal":"true/false","expression":"your_expression"}}
```

เครื่องคิดเลขมีพารามิเตอร์หลักสองตัว:
- `decimal`: กำหนดว่าผลลัพธ์ควรมีทศนิยมหรือไม่ (`true`) หรือปัดเป็นจำนวนเต็ม (`false`)
- `expression`: นิพจน์ทางคณิตศาสตร์ที่จะประเมินค่า

### การดำเนินการที่รองรับ
เครื่องคิดเลขรองรับการดำเนินการทางคณิตศาสตร์เหล่านี้:
- การคำนวณพื้นฐาน: `+` (บวก), `-` (ลบ), `*` (คูณ), `/` (หาร)
- วงเล็บ: `( )` สำหรับจัดกลุ่มการคำนวณ
- ยกกำลัง: `^` สำหรับเลขชี้กำลัง
- รากที่สอง: `sqrt()`
- ฟังก์ชันตรีโกณมิติ: `sin()`, `cos()`, `tan()`
- ค่าคงที่ทางคณิตศาสตร์: `pi`, `e`
- ค่าสัมบูรณ์: `abs()`
- ลอการิทึม: `log()`, `ln()`

## สุ่มตัวเลข (random_number)
สร้างตัวเลขแบบสุ่มภายในช่วงที่กำหนด
```
{"placeholder":"random_number","values":{"min":"1","max":"100"}}
```
ตัวอย่างผลลัพธ์: `42`

## ค่าสูงสุด (maxnum)
ส่งกลับค่าที่มากกว่าของตัวเลขสองค่า
```
{"placeholder":"maxnum","values":{"first":"10","second":"20"}}
```
ตัวอย่างผลลัพธ์: `20`

## ค่าต่ำสุด (minnum)
ส่งกลับค่าที่น้อยกว่าของตัวเลขสองค่า
```
{"placeholder":"minnum","values":{"first":"10","second":"20"}}
```
ตัวอย่างผลลัพธ์: `10`

## ค่าสัมบูรณ์ (absnum)
ส่งกลับค่าสัมบูรณ์ของตัวเลข
```
{"placeholder":"absnum","values":{"num":"-10.5"}}
```
ตัวอย่างผลลัพธ์: `10.5`

## เปลี่ยนเครื่องหมายตัวเลข (negnum)
ส่งกลับค่าติดลบของตัวเลข
```
{"placeholder":"negnum","values":{"num":"10.5"}}
```
ตัวอย่างผลลัพธ์: `-10.5`

## *pi* (คณิตศาสตร์) (math_pi)
ส่งกลับค่าของ π
```
{"placeholder":"math_pi"}
```
ตัวอย่างผลลัพธ์: `3.141592653589793`

## ไซน์ตรีโกณมิติ (คณิตศาสตร์) (math_sin)
ส่งกลับค่า sine ของมุม
```
{"placeholder":"math_sin","values":{"angle":"45"}}
```
ตัวอย่างผลลัพธ์: `0.7071067811865476`

## โคไซน์ตรีโกณมิติ (คณิตศาสตร์) (math_cos)
ส่งกลับค่า cosine ของมุม
```
{"placeholder":"math_cos","values":{"angle":"45"}}
```
ตัวอย่างผลลัพธ์: `0.7071067811865476`

## แทนเจนต์ตรีโกณมิติ (คณิตศาสตร์) (math_tan)
ส่งกลับค่า tangent ของมุม
```
{"placeholder":"math_tan","values":{"angle":"45"}}
```
ตัวอย่างผลลัพธ์: `1.0`

## ปัดลง (คณิตศาสตร์) (math_floor)
ปัดตัวเลขลงไปยังจำนวนเต็มที่ใกล้ที่สุด
```
{"placeholder":"math_floor","values":{"num":"3.14"}}
```
ตัวอย่างผลลัพธ์: `3`

## ปัดขึ้น (คณิตศาสตร์) (math_ceil)
ปัดตัวเลขขึ้นไปยังจำนวนเต็มที่ใกล้ที่สุด
```
{"placeholder":"math_ceil","values":{"num":"3.14"}}
```
ตัวอย่างผลลัพธ์: `4`

## ปัดเศษ (คณิตศาสตร์) (math_round)
ปัดตัวเลข โดยปกติจะปัดไปยังจำนวนเต็มที่ใกล้ที่สุด; ตั้งค่า `decimals` เป็นจำนวนที่ไม่ติดลบเพื่อปัดให้ได้จำนวนตำแหน่งทศนิยมตามต้องการ
```
{"placeholder":"math_round","values":{"num":"3.14159","decimals":"2"}}
```
ตัวอย่างผลลัพธ์: `3.14` (เมื่อ `decimals:-1` หรือไม่ได้ระบุ → `3`)

## เครื่องหมาย (คณิตศาสตร์) (math_sign)
ส่งกลับเครื่องหมายของตัวเลข (1 สำหรับบวก, -1 สำหรับลบ, 0 สำหรับศูนย์)
```
{"placeholder":"math_sign","values":{"num":"-3.14"}}
```
ตัวอย่างผลลัพธ์: `-1`

## ไฮเพอร์โบลิกไซน์ (คณิตศาสตร์) (math_sinh)
ส่งกลับค่า hyperbolic sine ของมุม
```
{"placeholder":"math_sinh","values":{"angle":"1"}}
```
ตัวอย่างผลลัพธ์: `1.1752011936438014`

## ไฮเพอร์โบลิกโคไซน์ (คณิตศาสตร์) (math_cosh)
ส่งกลับค่า hyperbolic cosine ของมุม
```
{"placeholder":"math_cosh","values":{"angle":"1"}}
```
ตัวอย่างผลลัพธ์: `1.5430806348152437`

## ไฮเพอร์โบลิกแทนเจนต์ (คณิตศาสตร์) (math_tanh)
ส่งกลับค่า hyperbolic tangent ของมุม
```
{"placeholder":"math_tanh","values":{"angle":"1"}}
```
ตัวอย่างผลลัพธ์: `0.7615941559557649`

## แยกข้อความ (split_text)
แยกข้อความโดยใช้ตัวคั่นที่กำหนด
```
{"placeholder":"split_text","values":{"input":"hello,world","regex":",","max_parts":"2","split_index":"1"}}
```
ตัวอย่างผลลัพธ์: `world`

## ตัดช่องว่างข้อความ (trim_text)
ลบช่องว่างนำหน้าและท้ายข้อความ
```
{"placeholder":"trim_text","values":{"text":"  hello world  "}}
```
ตัวอย่างผลลัพธ์: `hello world`

## ครอบตัดข้อความ (crop_text)
ลบอักขระจากต้นและท้ายข้อความ
```
{"placeholder":"crop_text","values":{"text":"hello world","remove_from_start":"1","remove_from_end":"1"}}
```
ตัวอย่างผลลัพธ์: `ello worl`

## แปลงเป็นสตริง (stringify)
แปลงข้อความเป็นสตริงโดยการ escape อักขระไวยากรณ์ทั้งหมด
```
{"placeholder":"stringify","values":{"text":"text with {special} \"characters\""}}
```
ตัวอย่างผลลัพธ์: `text with \{special\} \"characters\"`

## แปลข้อความตามภาษา (local)
ดึงข้อความที่แปลแล้วสำหรับคีย์ที่กำหนด
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

## ข้อความแบบสุ่ม (randomtext)
ส่งกลับบรรทัดแบบสุ่มจากไฟล์ข้อความ, URL, หรือข้อความธรรมดาโดยตรง ข้อความจะเปลี่ยนตามช่วงเวลาที่กำหนด
```
{"placeholder":"randomtext","values":{"source":"/config/fancymenu/assets/<file_name.txt>","interval":"10"}}
```
พารามิเตอร์:
- `source`: แหล่งที่มาของบรรทัดข้อความ (แทนพารามิเตอร์ `path` แบบเก่า)
  - พาธไฟล์: `/config/fancymenu/assets/quotes.txt`
  - URL: `https://example.com/quotes.txt`
  - ข้อความธรรมดา: `Line 1\nLine 2\nLine 3`
- `interval`: เวลาหน่วยวินาทีระหว่างการเปลี่ยนข้อความ

ตัวแทนที่ใช้แทนค่านี้รองรับแหล่งที่มา 3 ประเภท:
1. **ไฟล์ในเครื่อง**: ไฟล์ข้อความจากไดเรกทอรีเกมของคุณ
   ```
   {"placeholder":"randomtext","values":{"source":"/config/fancymenu/assets/quotes.txt","interval":"10"}}
   ```
2. **URL**: ไฟล์ข้อความจากอินเทอร์เน็ต
   ```
   {"placeholder":"randomtext","values":{"source":"https://example.com/quotes.txt","interval":"10"}}
   ```
3. **ข้อความธรรมดา**: ใส่ข้อความโดยตรง โดยแยกแต่ละบรรทัดด้วย `\n`
   ```
   {"placeholder":"randomtext","values":{"source":"First line\nSecond line\nThird line","interval":"5"}}
   ```

หมายเหตุ: ตัวแทนที่ใช้แทนค่าแบบเก่าที่ใช้ `path` แทน `source` ยังคงใช้งานได้

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

ตัวแทนที่ใช้แทนค่านี้รองรับแหล่งที่มา 3 ประเภท:
1. **ไฟล์ในเครื่อง**: ไฟล์ JSON จากไดเรกทอรีเกมของคุณ
   ```
   {"placeholder":"json","values":{"source":"/config/fancymenu/assets/playerdata.json","json_path":"$.player.name"}}
   ```
2. **URL**: ข้อมูล JSON ระยะไกลจาก API หรือบริการเว็บ
   ```
   {"placeholder":"json","values":{"source":"https://api.minecraft.com/server/status","json_path":"$.online"}}
   ```
3. **JSON โดยตรง**: เนื้อหา JSON แบบ inline
   ```
   {"placeholder":"json","values":{"source":"{"name":"Steve","score":42,"rank":"Diamond"}","json_path":"$.rank"}}
   ```

ตัวอย่าง JSON path:
- `$.name` - ดึงฟิลด์ "name" จากรากข้อมูล
- `$.player.level` - ดึงฟิลด์ "level" ที่ซ้อนอยู่ภายใน "player"
- `$.items[0].id` - ดึงค่า "id" ของไอเทมแรกในอาร์เรย์
- `$.scores.*` - ดึงค่าทั้งหมดจากอ็อบเจ็กต์ "scores"

## พาธไฟล์/โฟลเดอร์แบบสมบูรณ์ (absolute_path)
ส่งกลับพาธแบบสมบูรณ์ของไฟล์
```
{"placeholder":"absolute_path","values":{"short_path":"relative/path/to/file.txt"}}
```
ตัวอย่างผลลัพธ์: `C:/Users/Username/AppData/Roaming/.minecraft/relative/path/to/file.txt`

## จำนวนอักขระของข้อความ (text_character_count)
ส่งกลับจำนวนอักขระในข้อความที่กำหนด
```
{"placeholder":"text_character_count","values":{"text":"Hello World!"}}
```
ตัวอย่างผลลัพธ์: `12`

## ความกว้างของข้อความ (text_width)
ส่งกลับความกว้างเป็นพิกเซลของข้อความที่กำหนดเมื่อแสดงผล
```
{"placeholder":"text_width","values":{"text":"Hello World!"}}
```
ตัวอย่างผลลัพธ์: `66`

## ข้อความตัวพิมพ์ใหญ่ทั้งหมด (uppercase_text)
แปลงข้อความที่รับเข้าเป็นตัวพิมพ์ใหญ่ทั้งหมด
```
{"placeholder":"uppercase_text","values":{"text":"Hello World"}}
```
ตัวอย่างผลลัพธ์: `HELLO WORLD`

## ข้อความตัวพิมพ์เล็กทั้งหมด (lowercase_text)
แปลงข้อความที่รับเข้าเป็นตัวพิมพ์เล็กทั้งหมด
```
{"placeholder":"lowercase_text","values":{"text":"Hello World"}}
```
ตัวอย่างผลลัพธ์: `hello world`

## ข้อความแบบ Title Case (title_case_text)
แปลงข้อความที่รับเข้าเป็นรูปแบบ Title Case
```
{"placeholder":"title_case_text","values":{"text":"hello world"}}
```
ตัวอย่างผลลัพธ์: `Hello World`

## ข้อความแบบ Sentence Case (sentence_case_text)
แปลงข้อความที่รับเข้าเป็นรูปแบบ Sentence Case
```
{"placeholder":"sentence_case_text","values":{"text":"hello world. this is fancymenu!"}}
```
ตัวอย่างผลลัพธ์: `Hello world. This is fancymenu!`

## ข้อความแบบ Snake Case (snake_case_text)
แปลงข้อความที่รับเข้าเป็น `snake_case`
```
{"placeholder":"snake_case_text","values":{"text":"Hello World"}}
```
ตัวอย่างผลลัพธ์: `hello_world`

## ข้อความแบบ Kebab Case (kebab_case_text)
แปลงข้อความที่รับเข้าเป็น `kebab-case`
```
{"placeholder":"kebab_case_text","values":{"text":"Hello World"}}
```
ตัวอย่างผลลัพธ์: `hello-world`

## ข้อความแบบสลับตัวพิมพ์ (alternating_case_text)
แปลงข้อความที่รับเข้าเป็นตัวพิมพ์สลับกัน
```
{"placeholder":"alternating_case_text","values":{"text":"alternating case"}}
```
ตัวอย่างผลลัพธ์: `aLtErNaTiNg CaSe`

## สลับตัวพิมพ์ข้อความ (toggle_case_text)
สลับตัวพิมพ์ของทุกตัวอักษรในข้อความที่รับเข้า
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
ส่งกลับบรรทัดข้อความจากไฟล์หรือ URL สามารถส่งกลับได้ทั้งทุกบรรทัดหรือเฉพาะ X บรรทัดสุดท้าย
```
{"placeholder":"file_text","values":{"path_or_url":"/config/fancymenu/assets/some_file.txt","mode":"all","separator":"\n","last_lines":"1"}}
```
พารามิเตอร์:
- `path_or_url`: พาธไฟล์หรือ URL ที่จะอ่าน
- `mode`: `"all"` (ส่งกลับทุกบรรทัด) หรือ `"last"` (ส่งกลับเฉพาะ X บรรทัดสุดท้าย)
- `separator`: ข้อความที่ใช้เชื่อมบรรทัด (ค่าเริ่มต้น: `"\n"`)
- `last_lines`: จำนวนบรรทัดที่จะส่งกลับเมื่อใช้โหมด `"last"` (ค่าเริ่มต้น: `"1"`)

ตัวอย่างผลลัพธ์: ขึ้นอยู่กับเนื้อหาในไฟล์

## เนื้อหาในคลิปบอร์ด (clipboard_content)
ส่งกลับข้อความปัจจุบันที่เก็บอยู่ในคลิปบอร์ดของระบบ
```
{"placeholder":"clipboard_content"}
```
ตัวอย่างผลลัพธ์: ข้อความใดก็ตามที่อยู่ในคลิปบอร์ดขณะนั้น

## แทนที่ข้อความ (replace_text)
แทนที่ข้อความในสตริงโดยใช้ข้อความตรงตัวหรือนิพจน์ regular expression
```
{"placeholder":"replace_text","values":{"text":"Hello World! This is a test.","search":"World","replacement":"FancyMenu","use_regex":"false","replace_all":"true"}}
```
พารามิเตอร์:
- `text`: ข้อความอินพุตที่ต้องการประมวลผล
- `search`: ข้อความหรือแพตเทิร์น regex ที่จะค้นหา
- `replacement`: ข้อความที่ใช้แทน
- `use_regex`: จะใช้ regex (`"true"`) หรือจับคู่แบบตัวอักษรตรงตัว (`"false"`)
- `replace_all`: แทนที่ทุกตำแหน่ง (`"true"`) หรือเฉพาะครั้งแรก (`"false"`)

ตัวอย่างผลลัพธ์: `Hello FancyMenu! This is a test.`

## สวิตช์เคส (switch_case)
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
ตัวอย่างผลลัพธ์: ขึ้นอยู่กับค่าที่เก็บไว้

## ดึงข้อมูล NBT (nbt_data_get)
ดึงข้อมูล NBT ฝั่งไคลเอนต์ (คล้ายคำสั่ง `/data get`) ใช้ตัวแปรฝั่งเซิร์ฟเวอร์ `nbt_data_get_server` เมื่อต่อกับเซิร์ฟเวอร์และต้องการค่าที่เชื่อถือได้จากฝั่งเซิร์ฟเวอร์
```
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"foodLevel","scale":"1.0","return_type":"value"}}
```
พารามิเตอร์:
- `source_type`: `"entity"` หรือ `"block"`
- `entity_selector`: ตัวเลือกเอนทิตี เช่น `@s`, `@p`, `@e`, หรือ UUID/ชื่อ (สำหรับเอนทิตี)
- `block_pos`: ตำแหน่งบล็อกในรูปแบบ `"x y z"` (สำหรับบล็อก)
- `nbt_path`: พาธ NBT ที่ต้องการดึง
- `scale`: ตัวคูณปรับสเกลสำหรับค่าตัวเลข (ค่าเริ่มต้น: `"1.0"`)
- `return_type`: วิธีส่งกลับข้อมูล:
  - `"value"`: ค่าเริ่มต้น ส่งกลับค่า (และอาจมีการสเกลสำหรับตัวเลข)
  - `"string"`: ส่งกลับข้อมูล NBT จริงในรูปแบบสตริง
  - `"snbt"`: ส่งกลับเป็น SNBT (NBT ที่จัดรูปแบบ)
  - `"json"`: ส่งกลับเป็นคอมโพเนนต์แบบ JSON (สำหรับ compound tags)

ตัวอย่างผลลัพธ์: `20` (สำหรับระดับความหิว)

## ดึงข้อมูล NBT (ฝั่งเซิร์ฟเวอร์) (nbt_data_get_server)
สอบถามข้อมูล NBT ฝั่งเซิร์ฟเวอร์ (ใช้แพ็กเก็ต) และแคชผลลัพธ์ไว้ช่วงสั้นๆ ค่าที่ได้จะสอดคล้องกับตัวแทนฝั่งไคลเอนต์
```
{"placeholder":"nbt_data_get_server","values":{"source_type":"entity","entity_selector":"@s","block_pos":"","storage_id":"minecraft:storage_key","nbt_path":"SelectedItem.id","scale":"1.0","return_type":"value"}}
```
ตัวอย่างผลลัพธ์: `minecraft:diamond_sword`

## ข้อความตายล่าสุด (lastdeathmessage)
ส่งกลับข้อความแสดงการตายล่าสุดที่บันทึกไว้ของผู้เล่นไคลเอนต์ ตั้งค่า `as_json_component` เป็น `"true"` เพื่อรับคอมโพเนนต์ข้อความ JSON แบบดิบ
```
{"placeholder":"lastdeathmessage","values":{"as_json_component":"false"}}
```
ตัวอย่างผลลัพธ์: `Steve was slain by Zombie`

## ระยะเวลาที่เปิดใช้งาน (uptime_duration)
ส่งกลับระยะเวลาที่ FancyMenu ถูกโหลดอยู่ โดยค่าเริ่มต้นจะเป็นวินาที; ตั้งค่า `output_as_millis` เป็น `"true"` หากต้องการหน่วยมิลลิวินาที
```
{"placeholder":"uptime_duration","values":{"output_as_millis":"false"}}
```
ตัวอย่างผลลัพธ์: `742` (วินาทีตั้งแต่โหลด)

## ชื่อเซฟโลก (level_save_names)
แสดงรายชื่อเซฟโลกในเครื่องทั้งหมดโดยเชื่อมด้วยตัวคั่นที่เลือก ทำงานบนเธรดไคลเอนต์
```
{"placeholder":"level_save_names","values":{"separator":", "}}
```
ตัวอย่างผลลัพธ์: `Creative Test, Survival World, Hardcore`

## ข้อมูลเซฟโลก (level_save_data)
ส่งกลับข้อมูล level ที่ซีเรียลไลซ์สำหรับชื่อโลกที่ระบุ (ต้องตรงกับชื่อที่แสดงในรายการเซฟ)
```
{"placeholder":"level_save_data","values":{"level_name":"Survival World"}}
```
ตัวอย่างผลลัพธ์: `{"name":"Survival World","gameMode":"survival",...}`

## แปลงฐานตัวเลข (number_base_convert)
แปลงตัวเลข (จำนวนเต็มหรือเศษส่วน) จากฐานหนึ่งไปยังอีกฐานหนึ่ง (2–36) ค่าเริ่มต้นคือฐานสิบถ้าไม่ได้ระบุฐาน
```
{"placeholder":"number_base_convert","values":{"input":"67.5","from_base":"10","to_base":"16"}}
```
ตัวอย่างผลลัพธ์: `43.8`

## ขนาดไฟล์ (file_size)
ส่งกลับขนาดของไฟล์ในเครื่องเป็นไบต์ อนุญาตเฉพาะพาธในเครื่องเท่านั้น
```
{"placeholder":"file_size","values":{"path":"/config/fancymenu/assets/notes.txt"}}
```
ตัวอย่างผลลัพธ์: `1284`

## MD5 ของไฟล์ (file_md5)
ส่งกลับค่า MD5 hash ของไฟล์ในเครื่องเป็นสตริงเลขฐานสิบหกตัวพิมพ์เล็ก
```
{"placeholder":"file_md5","values":{"path":"/config/fancymenu/assets/notes.txt"}}
```
ตัวอย่างผลลัพธ์: `d41d8cd98f00b204e9800998ecf8427e`

# ตัวอย่างการใช้งานจริง

## สร้างการแสดงผลหน่วยความจำแบบไดนามิก
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

## การคำนวณซับซ้อนด้วยตัวแทนที่ใช้แทนค่าซ้อนกัน
```
{"placeholder":"calc","values":{"decimal":"true","expression":"({"placeholder":"usedram"} / {"placeholder":"maxram"}) * 100"}}
```

## แสดงพิกัดพร้อมการปัดเศษ
```
X: {"placeholder":"math_round","values":{"num":"{"placeholder":"player_x_coordinate"}"}}
Y: {"placeholder":"math_round","values":{"num":"{"placeholder":"player_y_coordinate"}"}}
Z: {"placeholder":"math_round","values":{"num":"{"placeholder":"player_z_coordinate"}"}}
```

# แนวทางปฏิบัติที่ดี

1. **แคชการทำงานที่ใช้ทรัพยากรสูง**: ตัวแทนที่ใช้แทนค่าบางตัว (เช่นตัวที่อ่านข้อมูลระบบ) อาจใช้ทรัพยากรมาก ควรพิจารณาใช้ตัวแปรเพื่อเก็บค่าหากต้องใช้งานหลายครั้ง

2. **ใช้การตั้งค่า decimal ให้เหมาะสม**: เมื่อทำงานกับการคำนวณ ควรใช้พารามิเตอร์ `decimal` ให้เหมาะสม ตั้งค่าเป็น `false` เมื่อต้องการจำนวนเต็ม และ `true` เมื่อต้องการค่าทศนิยมที่แม่นยำ

3. **จัดการค่าที่หายไป**: ควรคำนึงเสมอว่าจะเกิดอะไรขึ้นหากตัวแทนที่ใช้แทนค่าไม่คืนค่า คุณอาจต้องการกำหนดค่าเริ่มต้นในกรณีเหล่านี้

4. **ทดสอบประสิทธิภาพ**: เมื่อใช้ตัวแทนที่ใช้แทนค่าจำนวนมากหรือโครงสร้างซ้อนที่ซับซ้อน ให้ทดสอบผลกระทบต่อประสิทธิภาพ โดยเฉพาะบนเครื่องสเปกต่ำ

5. **ใช้การกำหนดขนาด/ตำแหน่งขั้นสูง**: สำหรับองค์ประกอบ UI แบบไดนามิก ให้ผสมตัวแทนที่ใช้แทนค่ากับการกำหนดขนาดและตำแหน่งขั้นสูงเพื่อสร้างเลย์เอาต์ที่ตอบสนองได้ดี

6. **ใช้ร่วมกับตัวแปร**: ใช้ตัวแทนที่ใช้แทนค่าร่วมกับตัวแปรเพื่อสร้างเนื้อหาแบบไดนามิกยิ่งขึ้น ซึ่งสามารถอัปเดตผ่านแอ็กชันได้

# ปัญหาที่พบบ่อยและวิธีแก้ไข

## ตัวแทนที่ใช้แทนค่าไม่อัปเดต
หากค่าของตัวแทนที่ใช้แทนค่าไม่อัปเดตตามที่คาดไว้ ให้ตรวจสอบ:
- รูปแบบของตัวแทนที่ใช้แทนค่าว่าถูกต้องหรือไม่
- ใช้ตัวพิมพ์ใหญ่/เล็กของรหัสตัวแทนถูกต้องหรือไม่
- ตัวแทนที่ใช้แทนค่านั้นต้องมีเงื่อนไขพิเศษใดๆ เพื่อให้อัปเดตหรือไม่

## ตัวแทนที่ใช้แทนค่าซ้อนไม่ทำงาน
เมื่อซ้อนตัวแทนที่ใช้แทนค่า:
- ตรวจสอบให้แน่ใจว่ามีการ escape เครื่องหมายอัญประกาศอย่างถูกต้อง
- ยืนยันว่าตัวแทนที่ใช้แทนค่าที่ซ้อนแต่ละตัวใช้งานได้ถูกต้องเมื่อใช้เดี่ยวๆ

## ปัญหาด้านประสิทธิภาพ
หากคุณพบปัญหาด้านประสิทธิภาพ:
- ลดจำนวนตัวแทนที่ใช้แทนค่าที่ใช้งาน
- หลีกเลี่ยงการซ้อนที่ไม่จำเป็น
- พิจารณาใช้ตัวแปรสำหรับค่าที่เรียกใช้บ่อย
- ใช้ตัวแทนที่ใช้แทนค่าให้เหมาะกับความต้องการ (เช่น อย่าใช้ตัวแทนแบบเรียลไทม์ถ้าค่าคงที่เพียงพอ)
