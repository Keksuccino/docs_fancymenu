---
title: ตัวฟัง
description: วิธีสร้างและใช้งานตัวฟังใน FancyMenu
---

# ตัวฟัง

เริ่มตั้งแต่ FancyMenu v3.8.0 ได้มีฟีเจอร์ใหม่ที่เรียกว่า "ตัวฟัง" (listeners)

ตัวฟังจะรันสคริปต์การกระทำเมื่อเกิดเหตุการณ์ของไคลเอนต์หรือเกมเพลย์ที่กำหนดไว้
และสามารถเปิดเผยตัวแปรให้กับการกระทำ, ตัวแทนพิเศษ (placeholders), และเงื่อนไข (requirements) ที่ซ้อนอยู่ภายในตัวฟังได้

ต่างจากสิ่งส่วนใหญ่ใน FancyMenu ตัวฟังจะไม่ถูกผูกกับหน้าจอหรือโอเวอร์เลย์ใด ๆ มันจะทำงานอยู่เบื้องหลังตลอดเวลา คอยฟังเหตุการณ์ของมันอยู่เสมอ ทันทีที่ตัวฟังถูกเรียกใช้ มันจะรันสคริปต์การกระทำของมัน แม้ในขณะนั้นจะไม่มีหน้าจอใดเปิดอยู่ก็ตาม

# การใช้งานตัวฟัง

หากต้องการสร้างตัวฟังใหม่ที่คอยฟังเหตุการณ์และรันสคริปต์การกระทำ ให้คลิก **menu bar -> Customization -> Manage Listeners** ขณะที่ **ไม่ได้** อยู่ในตัวแก้ไขเลย์เอาต์ ที่นั่นคุณจะพบ UI ที่ใช้งานง่ายสำหรับสร้างและจัดการตัวฟัง

<img src="https://github.com/Keksuccino/FancyMenu/blob/master/assets/docs/manage_listeners.png?raw=true" alt="Manage listeners" style="max-width:800px;width:100%;height:auto;">

# ตัวแปรของตัวฟัง

ตัวฟังมักจะเปิดเผยตัวแปรชนิดพิเศษสำหรับการกระทำ, เงื่อนไข และตัวแทนพิเศษที่ซ้อนอยู่ภายใน
ตัวแปรเหล่านี้สามารถเข้าถึงได้เหมือนตัวแทนพิเศษ (โดยแท้จริงแล้วมันก็คือตัวแทนพิเศษ)

คุณใช้ตัวแปรเหล่านี้ได้ง่าย ๆ โดยใส่ชื่อของมันพร้อมคำนำหน้า `$$` ในช่องป้อนข้อความ คล้ายกับวิธีที่คุณใช้ตัวแทนพิเศษทั่วไป

ตัวอย่างเช่น หากคุณใช้ตัวฟัง **On Keyboard Key Pressed** และต้องการพิมพ์ชื่อปุ่มลงในล็อกผ่านการกระทำ **Print to Log** คุณจะใช้ข้อความประมาณ `Key pressed! The key is: $$key_name` เป็นอินพุตของข้อความที่การกระทำควรพิมพ์ ตัวแทนตัวแปรนี้จะถูกแทนที่ด้วยชื่อของปุ่มจริงในภายหลัง

> แม้จะเรียกว่า "ตัวแปร" แต่พวกมันไม่ได้เกี่ยวข้องกับ [ระบบตัวแปร](/variables) ปกติของ FancyMenu แต่อย่างใด คุณไม่สามารถตั้งค่าตัวแปรเหล่านี้ได้ เพราะมันเป็นแบบ **อ่านอย่างเดียว** คุณยังไม่สามารถใช้การกระทำ, เงื่อนไข และตัวแทนพิเศษที่มีไว้สำหรับระบบตัวแปรของ FancyMenu กับตัวแปรพิเศษของตัวฟังเหล่านี้ได้ ดังนั้นการใช้ **Get Variable Value [FM Variable]**, **Is Variable Value [FM Variable]** หรือ **Set Variable Value [FM Variable]** จะไม่ทำงานกับตัวแปรของตัวฟัง
{.is-warning}

# รายละเอียดของตัวฟัง

รายการนี้ควรมีตัวฟังของ FancyMenu เกือบทั้งหมด หากไม่ใช่ทั้งหมด อาจเป็นไปได้ว่ารายการนี้ไม่ได้อัปเดตล่าสุดเสมอเนื่องจากการอัปเดตของม็อด

## On Markdown Text Clicked
- เรียกใช้เมื่อมีการคลิกข้อความ Markdown ที่มีเหตุการณ์ `click:` เช่น `[Open](click:open_menu)`
- ตัวแปร:
  - `$$text_event_id` – รหัสเหตุการณ์จากลิงก์ Markdown

## On Markdown Text Hovered
- เรียกใช้เมื่อมีการโฮเวอร์ข้อความ Markdown ที่มีเหตุการณ์ `hover:` เช่น `[Hint](hover:show_hint)`
- ตัวแปร:
  - `$$text_event_id` – รหัสเหตุการณ์จากลิงก์ Markdown

## On ZIP Extracted via Action
- เรียกใช้เมื่อการกระทำ **Extract ZIP File In Game Directory** ทำงานเสร็จ
- ตัวแปร:
  - `$$source_zip_path` – พาธต้นทางของ ZIP ที่แก้ไขแล้ว
  - `$$target_folder_path` – พาธปลายทางสำหรับแตกไฟล์ที่แก้ไขแล้ว
  - `$$extract_succeeded` – true/false
  - `$$failure_reason` – ข้อความแสดงข้อผิดพลาดเมื่อแตกไฟล์ไม่สำเร็จ

## On Element Spawned
- เรียกใช้เมื่อมีการสร้าง element ผ่านการกระทำ/โฟลว์การ spawn element แบบสคริปต์
- ตัวแปร:
  - `$$element_type` – ประเภทของ element ที่ถูกสร้าง
  - `$$element_identifier` – ตัวระบุของ element ที่ถูกสร้าง
  - `$$target_screen` – ตัวระบุของหน้าจอเป้าหมาย

## On Animated Texture Started Playing
- เรียกใช้เมื่อ texture แบบเคลื่อนไหวเริ่มเล่น
- ตัวแปร:
  - `$$texture_source` – แหล่งที่มาของ texture
  - `$$texture_source_type` – ประเภทของแหล่งที่มา
  - `$$texture_will_restart` – true/false

## On Animated Texture Finished Playing
- เรียกใช้เมื่อ texture แบบเคลื่อนไหวเล่นจบ
- ตัวแปร:
  - `$$texture_source`
  - `$$texture_source_type`
  - `$$texture_will_restart`

## On Video Playback Status Changed
- เรียกใช้เมื่อ element วิดีโอหรือพื้นหลังเมนูวิดีโอเปลี่ยนสถานะการเล่น
- ตัวแปร:
  - `$$video_source` – แหล่งที่มาของวิดีโอ
  - `$$video_source_type` – ประเภทของแหล่งที่มา
  - `$$is_looping` – true/false
  - `$$new_status` – `PLAYING`, `STOPPED`, `PAUSED`, หรือ `FINISHED`

## On System Message Received in Chat
- เรียกใช้เมื่อไคลเอนต์ได้รับข้อความแชทของระบบ เช่น ข้อความตอบกลับจากคำสั่ง
- ตัวแปร:
  - `$$system_message_string` – ข้อความธรรมดา
  - `$$system_message_component` – JSON component

## On FM Data Received
- เรียกใช้เมื่อเซิร์ฟเวอร์ส่ง FM Data มายังไคลเอนต์นี้ผ่าน `/fmdata send`
- ตัวแปร:
  - `$$data_identifier` – สตริงตัวระบุข้อมูล
  - `$$data` – payload ของข้อมูล
  - `$$sent_by` – IP ของเซิร์ฟเวอร์ หรือ `integrated_server`

## On Remote Server Connected
- เรียกใช้เมื่อ FancyMenu เริ่มต้นการเชื่อมต่อกับเซิร์ฟเวอร์ระยะไกล
- ตัวแปร:
  - `$$request_id` – request ID ที่แคชไว้
  - `$$remote_server_url` – URL ของเซิร์ฟเวอร์ระยะไกล

## On Remote Server Data Received
- เรียกใช้เมื่อได้รับข้อมูลข้อความจากเซิร์ฟเวอร์ระยะไกลที่เชื่อมต่ออยู่
- ตัวแปร:
  - `$$request_id` – request ID
  - `$$remote_server_url` – URL ของเซิร์ฟเวอร์ระยะไกล
  - `$$data` – payload ที่ได้รับ

## On Remote Server Connection Closed
- เรียกใช้เมื่อการเชื่อมต่อกับเซิร์ฟเวอร์ระยะไกลปิดลง
- ตัวแปร:
  - `$$request_id` – request ID
  - `$$remote_server_url` – URL ของเซิร์ฟเวอร์ระยะไกล
  - `$$intentionally_closed` – TRUE หากถูกปิดโดยการกระทำ
  - `$$crashed` – TRUE หากการเชื่อมต่อล่มโดยไม่คาดคิด
  - `$$unknown_close_reason` – TRUE หากไม่มีสาเหตุการปิดที่ทราบ

## On Keyboard Key Pressed
- ทริกเกอร์ทุกครั้งที่มีการกดปุ่ม (จะทำซ้ำขณะกดค้าง; ใช้ได้ทั้งในหน้าจอและในเกม)
- ตัวแปร:
  - `$$key_name` – ชื่อที่แสดงของปุ่ม
  - `$$key_keycode` – รหัสปุ่ม GLFW
  - `$$key_scancode` – รหัสสแกน GLFW
  - `$$key_modifiers` – บิตมาสก์ของตัวปรับที่ใช้งานอยู่

## On Keyboard Key Released
- ทริกเกอร์เมื่อมีการปล่อยปุ่ม (หน้าจอและในเกม)
- ตัวแปร:
  - `$$key_name`
  - `$$key_keycode`
  - `$$key_scancode`
  - `$$key_modifiers`

## On Keyboard Character Typed in Screen
- เรียกใช้เมื่อพิมพ์ตัวอักษรขณะมีหน้าจอเปิดอยู่
- ตัวแปร:
  - `$$char` – ตัวอักษรที่พิมพ์

## On Mouse Moved in Screen
- เรียกใช้ทุกครั้งที่เมาส์เคลื่อนที่ขณะมีหน้าจอเปิดอยู่
- ตัวแปร:
  - `$$mouse_pos_x` – X ปัจจุบัน
  - `$$mouse_pos_y` – Y ปัจจุบัน
  - `$$mouse_move_delta_x` – ค่าการเปลี่ยนแปลงของ X ตั้งแต่เหตุการณ์ล่าสุด
  - `$$mouse_move_delta_y` – ค่าการเปลี่ยนแปลงของ Y ตั้งแต่เหตุการณ์ล่าสุด

## On Mouse Button Clicked
- เรียกใช้เมื่อกดปุ่มเมาส์ (หน้าจอและในเกม)
- ตัวแปร:
  - `$$button` – ซ้าย/ขวา/กลาง
  - `$$mouse_pos_x` – X ปัจจุบัน
  - `$$mouse_pos_y` – Y ปัจจุบัน

## On Mouse Button Released
- เรียกใช้เมื่อปล่อยปุ่มเมาส์ (หน้าจอและในเกม)
- ตัวแปร:
  - `$$button`
  - `$$mouse_pos_x`
  - `$$mouse_pos_y`

## On Mouse Scrolled in Screen
- เรียกใช้เมื่อเลื่อนล้อเมาส์ขณะมีหน้าจอเปิดอยู่
- ตัวแปร:
  - `$$scroll_delta_y` – ปริมาณการเลื่อนในแนวตั้ง

## On Screen Opened
- รันทันทีหลังจากหน้าจอใด ๆ กลายเป็นใช้งานได้; สามารถใช้เพื่อ override มันได้
- ตัวแปร:
  - `$$screen_identifier` – ตัวระบุของหน้าจอที่เปิด

## On Screen Closed
- รันทันทีหลังจากหน้าจอปิด
- ตัวแปร:
  - `$$screen_identifier` – ตัวระบุของหน้าจอที่ปิด

## On Quit Minecraft
- เรียกใช้หนึ่งครั้งเมื่อไคลเอนต์เริ่มปิดตัวลง
- ตัวแปร:
  - `$$timestamp_millis` – ค่า epoch millis ตอนออกจากเกม
  - `$$timestamp_iso` – เวลารูปแบบ ISO-8601 ของช่วงเวลาออกจากเกม

## On Death
- รันเมื่อหน้าจอตายแบบดั้งเดิมเปิดขึ้นสำหรับผู้เล่นในเครื่อง
- ตัวแปร:
  - `$$days_survived` – จำนวนวันนับตั้งแต่ตายครั้งล่าสุด
  - `$$death_reason_string` – สาเหตุแบบข้อความธรรมดา
  - `$$death_reason_component` – สาเหตุแบบ JSON component
  - `$$death_pos_x` – พิกัด X ตอนตาย
  - `$$death_pos_y` – พิกัด Y ตอนตาย
  - `$$death_pos_z` – พิกัด Z ตอนตาย

## On Variable Updated [FM Variable]
- เรียกใช้ทุกครั้งที่มีการตั้งค่า/อัปเดตตัวแปรของ FancyMenu
- ตัวแปร:
  - `$$var_name` – ชื่อตัวแปร
  - `$$old_value` – ค่าก่อนหน้า
  - `$$new_value` – ค่าใหม่

## On File Downloaded via Action
- เรียกใช้หลังจากการกระทำ “Download File to Game Directory” เสร็จสิ้น
- ตัวแปร:
  - `$$download_url` – แหล่งที่มาของการดาวน์โหลด
  - `$$target_file_path` – พาธของไฟล์ที่บันทึก
  - `$$download_succeeded` – true/false

## On File Selected
- เรียกใช้หลังจากการกระทำ “Select File” ทำงานเสร็จ
- ตัวแปร:
  - `$$selected_file_path` – พาธเต็มของไฟล์ที่เลือก หรือว่างหากยกเลิก
  - `$$target_file_path` – พาธที่แก้ไขแล้วภายใน instance
  - `$$selection_succeeded` – true หากคัดลอกสำเร็จ
  - `$$selection_cancelled` – true หากปิดกล่องโต้ตอบ
  - `$$failure_reason` – ข้อมูลข้อผิดพลาดเมื่อไม่สำเร็จ

## On Chat Message Received
- เรียกใช้เมื่อบรรทัดแชทของผู้เล่นทั่วไปปรากฏบนไคลเอนต์
- ตัวแปร:
  - `$$chat_message_string` – บรรทัดข้อความธรรมดา
  - `$$chat_message_component` – component JSON แบบเต็ม
  - `$$sender_uuid` – UUID ของผู้ส่ง หรือ ERROR
  - `$$sender_name` – ชื่อผู้ส่ง หรือ ERROR

## On Chat Message Sent
- เรียกใช้เมื่อผู้เล่นในเครื่องส่งข้อความแชท
- ตัวแปร:
  - `$$chat_message_string` – บรรทัดข้อความธรรมดา
  - `$$chat_message_component` – component JSON แบบเต็ม

## On Effect Gained
- เรียกใช้เมื่อผู้เล่นได้รับเอฟเฟกต์สถานะ
- ตัวแปร:
  - `$$effect_key` – ตำแหน่งทรัพยากรของเอฟเฟกต์
  - `$$effect_type` – positive/negative/neutral
  - `$$effect_duration` – จำนวน ticks ที่เหลือ

## On Effect Lost
- เรียกใช้เมื่อผู้เล่นสูญเสียเอฟเฟกต์สถานะ
- ตัวแปร:
  - `$$effect_key` – เอฟเฟกต์ที่หมดอายุ
  - `$$effect_type` – หมวดหมู่

## On Experience Changed
- เรียกใช้ทุกครั้งที่ XP รวมของผู้เล่นเปลี่ยน
- ตัวแปร:
  - `$$new_experience_amount` – ค่าหลังการเปลี่ยนแปลง
  - `$$old_experience_amount` – ค่าก่อนการเปลี่ยนแปลง
  - `$$is_level_up` – TRUE หากเลเวลเพิ่มขึ้น

## On Damage Taken
- เรียกใช้หนึ่งครั้งต่อการโจมตีเมื่อผู้เล่นได้รับความเสียหาย
- ตัวแปร:
  - `$$damage_amount` – สุขภาพที่ถูกลดลง
  - `$$damage_type` – ตำแหน่งทรัพยากรของชนิดความเสียหาย
  - `$$is_fatal_damage` – TRUE หากถึงตาย
  - `$$damage_source` – ตำแหน่งทรัพยากรของผู้โจมตี หรือ NONE

## On Started Freezing
- เรียกใช้เมื่อผู้เล่นเริ่มถูกแช่แข็ง
- ตัวแปร:
  - `$$freezing_intensity` – 0.0 ไม่มี, 1.0 แช่แข็งเต็มที่

## On Stopped Freezing
- เรียกใช้เมื่อผู้เล่นหยุดถูกแช่แข็ง
- ตัวแปร:
  - (ไม่มี)

## On Fully Frozen
- เรียกใช้หนึ่งครั้งเมื่อผู้เล่นถูกแช่แข็งเต็มที่
- ตัวแปร:
  - (ไม่มี)

## On Start Looking At Block
- เรียกใช้หนึ่งครั้งเมื่อเส้นเล็งชี้ไปที่บล็อกเป็นครั้งแรก (ระยะสูงสุด 20 บล็อก)
- ตัวแปร:
  - `$$block_key` – บล็อกเป้าหมาย
  - `$$block_pos_x` – X ของบล็อก
  - `$$block_pos_y` – Y ของบล็อก
  - `$$block_pos_z` – Z ของบล็อก
  - `$$distance_to_player` – ระยะจากดวงตาถึงจุดกระทบ

## On Stop Looking At Block
- เรียกใช้เมื่อเส้นเล็งหยุดชี้ไปที่บล็อก (รายงานบล็อกเป้าหมายล่าสุด, ระยะสูงสุด 20 บล็อก)
- ตัวแปร:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`
  - `$$distance_to_player`

## On Start Looking At Entity
- เรียกใช้หนึ่งครั้งเมื่อเส้นเล็งชี้ไปที่เอนทิตีเป็นครั้งแรก (ระยะสูงสุด 20 บล็อก)
- ตัวแปร:
  - `$$entity_key` – ประเภทของเอนทิตีเป้าหมาย
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Stop Looking At Entity
- เรียกใช้เมื่อเส้นเล็งหยุดชี้ไปที่เอนทิตี (รายงานเอนทิตีเป้าหมายล่าสุด, ระยะสูงสุด 20 บล็อก)
- ตัวแปร:
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Entity Spawned
- **ต้องมี FancyMenu บนเซิร์ฟเวอร์** เรียกใช้เมื่อเอนทิตีใด ๆ ถูกสร้างขึ้นที่ใดก็ได้ในโลก/เซิร์ฟเวอร์ที่เชื่อมต่ออยู่
- ตัวแปร:
  - `$$entity_key`
  - `$$distance_to_player` – −1 หากอยู่คนละมิติ
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`
  - `$$dimension_key`
  - `$$is_same_dimension_as_player`

## On Entity Died
- **ต้องมี FancyMenu บนเซิร์ฟเวอร์** เรียกใช้เมื่อเอนทิตีใด ๆ ตายบนโลก/เซิร์ฟเวอร์ที่เชื่อมต่ออยู่
- ตัวแปร:
  - `$$entity_key`
  - `$$distance_to_player` – −1 หากอยู่คนละมิติ
  - `$$death_pos_x`
  - `$$death_pos_y`
  - `$$death_pos_z`
  - `$$entity_uuid`
  - `$$dimension_key`
  - `$$damage_type`
  - `$$is_same_dimension_as_player`
  - `$$entity_killed_by_name`
  - `$$entity_killed_by_key`
  - `$$entity_killed_by_uuid`

## On Entity Starts Being In Sight
- เรียกใช้เมื่อเอนทิตีเริ่มมองเห็นได้เป็นครั้งแรกภายในระยะ 200 บล็อก
- ตัวแปร:
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Entity Stops Being In Sight
- เรียกใช้เมื่อเอนทิตีที่เคยเห็นได้ออกจากมุมมองหรือเคลื่อนที่เกิน 200 บล็อก
- ตัวแปร:
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Interacted With Entity
- เรียกใช้เมื่อผู้เล่นโต้ตอบกับเอนทิตีสำเร็จ
- ตัวแปร:
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Entity Mounted
- เรียกใช้เมื่อผู้เล่นเริ่มขี่เอนทิตี
- ตัวแปร:
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Entity Unmounted
- เรียกใช้เมื่อผู้เล่นหยุดขี่เอนทิตีที่ใช้อยู่ปัจจุบัน
- ตัวแปร:
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Block Broke
- เรียกใช้เมื่อผู้เล่นทำลายบล็อก
- ตัวแปร:
  - `$$block_key`
  - `$$broke_with_item_key` – เครื่องมือที่ใช้ หรือ EMPTY
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## On Block Placed
- เรียกใช้เมื่อผู้เล่นวางบล็อก
- ตัวแปร:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## On Interacted With Block
- เรียกใช้เมื่อผู้เล่นโต้ตอบกับบล็อกสำเร็จ
- ตัวแปร:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## On Stepping On Block
- เรียกใช้เมื่อผู้เล่นเหยียบขึ้นไปบนบล็อก
- ตัวแปร:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## On Enter Biome
- เรียกใช้เมื่อผู้เล่นเข้าสู่ไบโอมใหม่
- ตัวแปร:
  - `$$biome_key` – ไบโอมที่เข้าสู่

## On Leave Biome
- เรียกใช้เมื่อผู้เล่นออกจากไบโอมปัจจุบัน
- ตัวแปร:
  - `$$biome_key` – ไบโอมที่เพิ่งออกมา

## On Enter Structure
- **ต้องมี FancyMenu บนเซิร์ฟเวอร์** การตรวจจับพื้นที่โครงสร้างแบบคร่าว ๆ; อาจทริกเกอร์ใกล้ เหนือ หรือใต้โครงสร้าง
- ตัวแปร:
  - `$$structure_key` – โครงสร้างที่เข้าสู่

## On Leave Structure
- **ต้องมี FancyMenu บนเซิร์ฟเวอร์** การตรวจจับแบบคร่าว ๆ; อาจทริกเกอร์ใกล้กับขอบเขตของโครงสร้าง
- ตัวแปร:
  - `$$structure_key` – โครงสร้างที่เพิ่งออกมา

## On Enter Structure (High Precision)
- **ต้องมี FancyMenu บนเซิร์ฟเวอร์** เรียกใช้เมื่อผู้เล่นก้าวเข้าสู่ bounding box ของโครงสร้าง
- ตัวแปร:
  - `$$structure_key`

## On Leave Structure (High Precision)
- **ต้องมี FancyMenu บนเซิร์ฟเวอร์** เรียกใช้หลังจากผู้เล่นออกจาก bounding box ของโครงสร้าง
- ตัวแปร:
  - `$$structure_key`

## On Dimension Entered
- เรียกใช้เมื่อผู้เล่นเข้าสู่มิติใหม่
- ตัวแปร:
  - `$$dimension_key` – มิติที่เข้าสู่

## On Start Swimming
- เรียกใช้เมื่อผู้เล่นเริ่มว่ายน้ำ
- ตัวแปร:
  - `$$fluid_type` – ตำแหน่งทรัพยากรของของเหลว

## On Stop Swimming
- เรียกใช้เมื่อผู้เล่นหยุดว่ายน้ำ
- ตัวแปร:
  - `$$fluid_type` – ของเหลวที่หยุดว่ายใน

## On Start Touching Fluid
- เรียกใช้เมื่อผู้เล่นเริ่มสัมผัสของเหลว
- ตัวแปร:
  - `$$fluid_type` – ของเหลวที่สัมผัส

## On Stop Touching Fluid
- เรียกใช้เมื่อผู้เล่นหยุดสัมผัสของเหลว
- ตัวแปร:
  - `$$fluid_type` – ของเหลวที่ไม่ได้สัมผัสแล้ว

## On Music Track Started
- เรียกใช้เมื่อแทร็กเพลงใหม่เริ่มเล่น
- ตัวแปร:
  - `$$track_resource_location` – ไฟล์เสียง
  - `$$track_display_name` – ชื่อที่อ่านได้ หรือ UNKNOWN
  - `$$track_artist` – ศิลปิน หรือ UNKNOWN
  - `$$track_duration_ms` – มิลลิวินาที (0 หากไม่ทราบ)

## On Music Track Stopped
- เรียกใช้เมื่อแทร็กเพลงปัจจุบันจบหรือถูกแทนที่
- ตัวแปร:
  - `$$track_resource_location`
  - `$$track_display_name`
  - `$$track_artist`
  - `$$track_duration_ms`

## On World Sound Triggered
- เรียกใช้เมื่อเสียงในโลกแบบมีตำแหน่งเริ่มดังใกล้ผู้เล่น
- ตัวแปร:
  - `$$sound_resource_location` – ไฟล์เสียง
  - `$$sound_display_name` – ชื่อคำบรรยายเมื่อมี
  - `$$sound_origin_pos_x`
  - `$$sound_origin_pos_y`
  - `$$sound_origin_pos_z`
  - `$$sound_origin_distance_to_player`
  - `$$sound_origin_direction_from_player` – องศา 0–360 เทียบกับทิศที่หันอยู่

## On Weather Changed
- เรียกใช้เมื่อสภาพอากาศเปลี่ยนทั่วโลกหรือเฉพาะที่ (การเปลี่ยนไบโอมหรือการเข้าไปในอาคารอาจทริกเกอร์ซ้ำ)
- ตัวแปร:
  - `$$weather_type` – clear/rain/thunder
  - `$$weather_can_snow` – TRUE หากมีหิมะปรากฏ
  - `$$weather_can_rain` – TRUE หากมีฝนปรากฏ

## On Started Burning
- เรียกใช้เมื่อผู้เล่นเริ่มติดไฟ
- ตัวแปร:
  - (ไม่มี)

## On Stopped Burning
- เรียกใช้เมื่อผู้เล่นหยุดติดไฟ
- ตัวแปร:
  - (ไม่มี)

## On Started Drowning
- เรียกใช้เมื่อผู้เล่นเริ่มได้รับความเสียหายจากการจมน้ำ
- ตัวแปร:
  - (ไม่มี)

## On Position Changed
- เรียกใช้ทุกครั้งที่ตำแหน่งบล็อกของผู้เล่นเปลี่ยน
- ตัวแปร:
  - `$$old_pos_x` – บล็อก X ก่อนหน้า
  - `$$old_pos_y` – บล็อก Y ก่อนหน้า
  - `$$old_pos_z` – บล็อก Z ก่อนหน้า
  - `$$new_pos_x` – บล็อก X ใหม่
  - `$$new_pos_y` – บล็อก Y ใหม่
  - `$$new_pos_z` – บล็อก Z ใหม่

## On Started Running
- เรียกใช้เมื่อผู้เล่นเริ่มวิ่งเร็ว
- ตัวแปร:
  - (ไม่มี)

## On Stopped Running
- เรียกใช้เมื่อผู้เล่นหยุดวิ่งเร็ว
- ตัวแปร:
  - (ไม่มี)

## On Jump
- เรียกใช้ทุกครั้งที่ผู้เล่นกระโดด
- ตัวแปร:
  - (ไม่มี)

## On Server Joined
- เรียกใช้หลังจากเข้าร่วมเซิร์ฟเวอร์ผู้เล่นหลายคนสำเร็จ
- ตัวแปร:
  - `$$server_ip` – ที่อยู่เซิร์ฟเวอร์ที่เข้าร่วม

## On Server Left
- เรียกใช้หลังจากตัดการเชื่อมต่อจากเซิร์ฟเวอร์ผู้เล่นหลายคน
- ตัวแปร:
  - `$$server_ip` – ที่อยู่เซิร์ฟเวอร์ที่ออกจาก

## Singleplayer World Entered
- เรียกใช้หลังจากโลกผู้เล่นคนเดียวโหลดเสร็จและควบคุมกลับมาให้ผู้เล่น
- ตัวแปร:
  - `$$world_name` – ชื่อที่แสดง
  - `$$world_save_path` – โฟลเดอร์เซฟแบบ absolute
  - `$$world_difficulty` – คีย์ความยาก
  - `$$world_cheats_allowed` – TRUE หากเปิดใช้สูตรโกง
  - `$$world_icon_path` – พาธไอคอนแบบ absolute
  - `$$world_is_first_join` – TRUE ในการเข้าใช้งานครั้งแรกมาก ๆ

## Singleplayer World Left
- เรียกใช้หลังจากโลกผู้เล่นคนเดียวปิดและบันทึกเสร็จ
- ตัวแปร:
  - `$$world_name`
  - `$$world_save_path`
  - `$$world_difficulty`
  - `$$world_cheats_allowed`
  - `$$world_icon_path`

## On Other Player Joined World/Server
- เรียกใช้เมื่อผู้เล่นคนอื่นเข้าร่วมโลก/เซิร์ฟเวอร์ปัจจุบัน
- ตัวแปร:
  - `$$player_name` – ชื่อของผู้เล่นที่เข้ามา
  - `$$player_uuid` – UUID

## On Other Player Left World/Server
- เรียกใช้เมื่อผู้เล่นคนอื่นออกจากโลก/เซิร์ฟเวอร์ปัจจุบัน
- ตัวแปร:
  - `$$player_name`
  - `$$player_uuid`

## On Other Player Died
- เรียกใช้เมื่อผู้เล่นคนอื่นในโลกปัจจุบันตาย
- ตัวแปร:
  - `$$player_name`
  - `$$player_uuid`
  - `$$death_pos_x`
  - `$$death_pos_y`
  - `$$death_pos_z`

## On Item Picked Up
- เรียกใช้เมื่อผู้เล่นเก็บ entity ไอเท็มขึ้นมา
- ตัวแปร:
  - `$$item_key` – ตำแหน่งทรัพยากรของไอเท็มที่เก็บขึ้นมา

## On Item Dropped
- เรียกใช้เมื่อผู้เล่นทิ้งไอเท็มจากอินเวนทอรี
- ตัวแปร:
  - `$$item_key` – ตำแหน่งทรัพยากรของไอเท็มที่ทิ้ง

## On Item Consumed
- เรียกใช้เมื่อผู้เล่นบริโภคไอเท็มจนเสร็จ
- ตัวแปร:
  - `$$item_key` – ไอเท็มที่บริโภค

## On Item Hovered in Inventory
- เรียกใช้เมื่อผู้ใช้โฮเวอร์ไอเท็มในหน้าจออินเวนทอรีใด ๆ
- ตัวแปร:
  - `$$item_key` – ตำแหน่งทรัพยากรของไอเท็มที่โฮเวอร์
  - `$$item_display_name_string` – ชื่อที่แสดงแบบข้อความธรรมดา
  - `$$item_display_name_json` – ชื่อที่แสดงแบบ JSON component

## On Item Used
- เรียกใช้เมื่อผู้เล่นใช้งานไอเท็ม
- ตัวแปร:
  - `$$item_key` – ไอเท็มที่ใช้
  - `$$used_on_type` – block/entity/self/none
  - `$$used_on_entity_key` – ประเภทเอนทิตีเป้าหมาย หรือว่าง
  - `$$used_on_block_key` – บล็อกเป้าหมาย หรือว่าง
  - `$$target_pos_x` – X เป้าหมาย หรือ -1
  - `$$target_pos_y` – Y เป้าหมาย หรือ -1
  - `$$target_pos_z` – Z เป้าหมาย หรือ -1

## On Item Broke
- เรียกใช้เมื่อไอเท็มในอินเวนทอรีของผู้เล่นแตก
- ตัวแปร:
  - `$$item_key` – ไอเท็มที่แตก
  - `$$item_type` – tool/armor/other
