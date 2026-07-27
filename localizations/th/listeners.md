---
title: ตัวฟัง
description: วิธีสร้างและใช้งานตัวฟังใน FancyMenu
---

# ตัวฟัง

ตัวฟังจะรัน [สคริปต์การกระทำ](./action-scripts) เมื่อเกิดเหตุการณ์เฉพาะต่าง ๆ พวกมันไม่ได้ผูกกับหน้าจอที่เปิดอยู่ ดังนั้นจึงสามารถทำงานได้ขณะกำลังเล่นหรือกำลังโหลดเกม

ตัวฟังสามารถส่งค่า `$$` เช่น ปุ่มคีย์ที่กดหรือปุ่มเมาส์ที่คลิก ไปยังการกระทำและเงื่อนไขที่เกี่ยวข้องได้

> [!CAUTION]
> ตัวฟังสามารถรันการกระทำเกี่ยวกับไฟล์ เครือข่าย คำสั่ง คลิปบอร์ด resource-pack หรือการเปิดลิงก์ได้โดยไม่ต้องมีหน้าจอเปิดอยู่ ให้นำเข้าตัวฟังจากแหล่งที่คุณเชื่อถือเท่านั้น

# การใช้งานตัวฟัง

นอกเหนือจาก Layout Editor ให้เปิด **menu bar -> Customization -> Manage Listeners** เพื่อสร้างหรือแก้ไขตัวฟัง

<img src="https://github.com/Keksuccino/FancyMenu/blob/master/assets/docs/manage_listeners.png?raw=true" alt="จัดการตัวฟัง" style="max-width:800px;width:100%;height:auto;">

# ตัวแปรของตัวฟัง

ตัวฟังสามารถส่งค่าที่อ่านได้อย่างเดียวไปยังการกระทำและเงื่อนไข ใช้ชื่อ `$$` ของพวกมันในช่องข้อความที่รองรับ

ตัวอย่างเช่น ใช้ [**On Keyboard Key Pressed**](#on-keyboard-key-pressed-keyboard_key_pressed) ร่วมกับ [**Print to Game Log** action](./action-scripts#print-to-game-log-print_to_log) ค่า `Key pressed! The key is: $$key_name` จะใส่ชื่อของปุ่มที่กด

> [!WARNING]
> ตัวแปรของตัวฟังแยกจาก [ตัวแปรที่เก็บไว้](./variables) ของ FancyMenu การกระทำ เงื่อนไข และตัวแทนของตัวแปรที่เก็บไว้จะไม่ทำงานกับค่า `$$`

ชื่อตัวแปรของตัวฟังคำนึงถึงตัวพิมพ์เล็ก/ใหญ่ และจะใช้ได้เฉพาะภายในสคริปต์ของตัวฟังนั้นเท่านั้น

ให้ถือว่าค่าที่มาจากแชต เซิร์ฟเวอร์ระยะไกล ไฟล์ และข้อมูลจากผู้ใช้ว่าไม่น่าเชื่อถือ อย่าใส่ค่าพวกนี้ลงในพาธ URL หรือคำสั่งโดยตรง

ตัวแปรของตัวฟังเป็นสตริง เมื่อไม่สามารถระบุข้อมูลได้ ตัวฟังอาจส่งค่าคงที่ที่ระบุไว้ในเอกสาร เช่น `ERROR`, `UNKNOWN`, `NONE`, `EMPTY`, `0`, `-1` หรือสตริงว่าง โปรดทดสอบค่าพวกนี้ก่อนนำข้อมูลของตัวฟังไปใส่ในพาธ คำสั่ง หรือ URL

# รายละเอียดตัวฟัง

ส่วนนี้แสดงรายการตัวฟังในตัวของ FancyMenu

## เมื่อคลิกข้อความ Markdown (`text_clicked`)
- ทำงานเมื่อมีการคลิก [ข้อความ Markdown ที่มีเหตุการณ์ `click:`](./text-formatting#click-and-hover-events) เช่น `[Open](click:open_menu)`
- ตัวแปร:
  - `$$text_event_id` – รหัสเหตุการณ์จากลิงก์ Markdown

## เมื่อเอาเมาส์ชี้ข้อความ Markdown (`text_hovered`)
- ทำงานเมื่อมีการชี้ [ข้อความ Markdown ที่มีเหตุการณ์ `hover:`](./text-formatting#click-and-hover-events) เช่น `[Hint](hover:show_hint)`
- ตัวแปร:
  - `$$text_event_id` – รหัสเหตุการณ์จากลิงก์ Markdown

## เมื่อแตกไฟล์ ZIP ผ่านการกระทำ (`zip_extracted_via_action`)
- ทำงานเมื่อ [**Extract ZIP File In Game Directory** action](./action-scripts#extract-zip-file-in-game-directory-extract_zip_file_in_game_dir) ทำงานเสร็จ
- ตัวแปร:
  - `$$source_zip_path` – พาธต้นทางที่ปรับให้อยู่ในรูปแบบมาตรฐานสำหรับผู้ใช้; พาธใน game-directory อาจถูกส่งกลับเป็น `/...` ในขณะที่พาธแบบทั่วไปของ Minecraft directory อาจใช้ `.minecraft/...`
  - `$$target_folder_path` – พาธโฟลเดอร์ปลายทางที่ปรับให้อยู่ในรูปแบบมาตรฐานเดียวกัน
  - `$$extract_succeeded` – true/false
  - `$$failure_reason` – ข้อความแสดงข้อผิดพลาดเมื่อการแตกไฟล์ล้มเหลว

## เมื่อมีเอลิเมนต์ถูกสร้างขึ้น (`element_spawned_via_action`)
- ทำงานเมื่อฟีเจอร์หรือแอดออนที่รองรับของ FancyMenu สร้างอินสแตนซ์ของเอลิเมนต์แบบไดนามิก
- ตัวแปร:
  - `$$element_type` – ประเภทของเอลิเมนต์ที่ถูกสร้าง
  - `$$element_identifier` – ตัวระบุของเอลิเมนต์ที่ถูกสร้าง
  - `$$target_screen` – ตัวระบุของหน้าจอเป้าหมาย

## เมื่อแอนิเมชันเท็กซ์เจอร์เริ่มเล่น (`animated_texture_started_playing`)
- ทำงานเมื่อ [animated texture](./fma) เริ่มเล่น
- ตัวแปร:
  - `$$texture_source` – แหล่งที่มาของเท็กซ์เจอร์
  - `$$texture_source_type` – ประเภทแหล่งที่มา
  - `$$texture_will_restart` – true/false

## เมื่อแอนิเมชันเท็กซ์เจอร์เล่นจบ (`animated_texture_finished_playing`)
- ทำงานเมื่อ animated texture เล่นจบ
- ตัวแปร:
  - `$$texture_source`
  - `$$texture_source_type`
  - `$$texture_will_restart`

## เมื่อสถานะการเล่นวิดีโอเปลี่ยน (`video_playback_status_changed`)
- ทำงานเมื่อ [วิดีโอเอลิเมนต์หรือพื้นหลังเมนู](./video) เปลี่ยนสถานะการเล่น
- ตัวแปร:
  - `$$video_source` – แหล่งที่มาของวิดีโอ
  - `$$video_source_type` – ประเภทแหล่งที่มา
  - `$$is_looping` – true/false
  - `$$new_status` – `PLAYING`, `STOPPED`, `PAUSED`, หรือ `FINISHED`

## เมื่อได้รับข้อความระบบในแชต (`system_message_received_in_chat`)
- ทำงานเมื่อไคลเอนต์ได้รับข้อความแชตของระบบ เช่น ผลตอบกลับจากคำสั่ง
- ตัวแปร:
  - `$$system_message_string` – ข้อความแบบข้อความธรรมดา
  - `$$system_message_component` – คอมโพเนนต์ JSON

## เมื่อได้รับ FM Data (`fm_data_received`)
- ทำงานเมื่อเซิร์ฟเวอร์ส่ง [FM Data](./fm-data) มายังไคลเอนต์นี้ผ่าน `/fmdata send`
- ตัวแปร:
  - `$$data_identifier` – สตริงตัวระบุข้อมูล
  - `$$data` – เพย์โหลดข้อมูล
  - `$$sent_by` – IP ของเซิร์ฟเวอร์หรือ `integrated_server`

## เมื่อเชื่อมต่อเซิร์ฟเวอร์ระยะไกล (`remote_server_connected`)
- ทำงานหลังจาก [การเชื่อมต่อเซิร์ฟเวอร์ระยะไกล](./remote-server-communication) เปิดสำเร็จ
- ตัวแปร:
  - `$$request_id` – รหัสคำขอที่แคชไว้
  - `$$remote_server_url` – URL ของเซิร์ฟเวอร์ระยะไกล

## เมื่อได้รับข้อมูลจากเซิร์ฟเวอร์ระยะไกล (`remote_server_data_received`)
- ทำงานเมื่อได้รับข้อมูลข้อความจากเซิร์ฟเวอร์ระยะไกลที่เชื่อมต่ออยู่
- ตัวแปร:
  - `$$request_id` – รหัสคำขอ
  - `$$remote_server_url` – URL ของเซิร์ฟเวอร์ระยะไกล
  - `$$data` – เพย์โหลดที่ได้รับ

## เมื่อการเชื่อมต่อเซิร์ฟเวอร์ระยะไกลปิดลง (`remote_server_connection_closed`)
- ทำงานเมื่อการเชื่อมต่อเซิร์ฟเวอร์ระยะไกลปิดลง
- ตัวแปร:
  - `$$request_id` – รหัสคำขอ
  - `$$remote_server_url` – URL ของเซิร์ฟเวอร์ระยะไกล
  - `$$intentionally_closed` – TRUE หากปิดโดยการกระทำ
  - `$$crashed` – TRUE หากการเชื่อมต่อล่มโดยไม่คาดคิด
  - `$$unknown_close_reason` – TRUE หากไม่มีเหตุผลการปิดที่ทราบได้

## เมื่อกดปุ่มคีย์บอร์ด (`keyboard_key_pressed`)
- ทริกเกอร์ทุกครั้งที่มีการกดปุ่ม (จะเกิดซ้ำเมื่อกดค้าง; ใช้ได้ทั้งในหน้าจอและในเกม)
- ตัวแปร:
  - `$$key_name` – ชื่อที่แสดงของปุ่ม
  - `$$key_keycode` – GLFW key code
  - `$$key_scancode` – GLFW scan code
  - `$$key_modifiers` – บิตมาสก์ตัวปรับที่ใช้งานอยู่

## เมื่อปล่อยปุ่มคีย์บอร์ด (`keyboard_key_released`)
- ทริกเกอร์เมื่อปล่อยปุ่ม (ทั้งในหน้าจอและในเกม)
- ตัวแปร:
  - `$$key_name`
  - `$$key_keycode`
  - `$$key_scancode`
  - `$$key_modifiers`

## เมื่อพิมพ์อักขระคีย์บอร์ดในหน้าจอ (`keyboard_char_typed`)
- ทำงานเมื่อพิมพ์อักขระขณะมีหน้าจอเปิดอยู่
- ตัวแปร:
  - `$$char` – อักขระที่พิมพ์

## เมื่อเมาส์เคลื่อนที่ในหน้าจอ (`mouse_moved`)
- ทำงานทุกครั้งที่เมาส์เคลื่อนที่ขณะมีหน้าจอเปิดอยู่
- ตัวแปร:
  - `$$mouse_pos_x` – X ปัจจุบัน
  - `$$mouse_pos_y` – Y ปัจจุบัน
  - `$$mouse_move_delta_x` – ค่าการเปลี่ยนแปลง X จากเหตุการณ์ก่อนหน้า
  - `$$mouse_move_delta_y` – ค่าการเปลี่ยนแปลง Y จากเหตุการณ์ก่อนหน้า

## เมื่อคลิกปุ่มเมาส์ (`mouse_button_clicked`)
- ทำงานเมื่อมีการกดปุ่มเมาส์ (ทั้งในหน้าจอและในเกม)
- ตัวแปร:
  - `$$button` – ซ้าย/ขวา/กลาง
  - `$$mouse_pos_x` – X ปัจจุบัน
  - `$$mouse_pos_y` – Y ปัจจุบัน

## เมื่อปล่อยปุ่มเมาส์ (`mouse_button_released`)
- ทำงานเมื่อปล่อยปุ่มเมาส์ (ทั้งในหน้าจอและในเกม)
- ตัวแปร:
  - `$$button`
  - `$$mouse_pos_x`
  - `$$mouse_pos_y`

## เมื่อเลื่อนล้อเมาส์ในหน้าจอ (`mouse_scrolled`)
- ทำงานเมื่อเลื่อนล้อเมาส์ขณะมีหน้าจอเปิดอยู่
- ตัวแปร:
  - `$$scroll_delta_y` – ปริมาณการเลื่อนในแนวตั้ง

## เมื่อเปิดหน้าจอ (`screen_open`)
- ทำงานทันทีหลังจากหน้าจอใด ๆ กลายเป็นใช้งานได้; ใช้เพื่อแทนที่หน้าจอนั้นได้
- ตัวแปร:
  - `$$screen_identifier` – ตัวระบุของหน้าจอที่เปิด

## เมื่อปิดหน้าจอ (`screen_close`)
- ทำงานทันทีหลังจากหน้าจอปิด
- ตัวแปร:
  - `$$screen_identifier` – ตัวระบุของหน้าจอที่ปิด

## เมื่อออกจาก Minecraft (`quit_minecraft`)
- ทำงานหนึ่งครั้งเมื่อไคลเอนต์เริ่มปิดตัว
- ตัวแปร:
  - `$$timestamp_millis` – epoch millis ณ เวลาที่ออกจากเกม
  - `$$timestamp_iso` – เวลารูปแบบ ISO-8601 ของช่วงที่ออกจากเกม

## เมื่อเสียชีวิต (`player_death`)
- ทำงานเมื่อหน้าจอความตายแบบ vanilla เปิดขึ้นสำหรับผู้เล่นในเครื่อง
- ตัวแปร:
  - `$$days_survived` – จำนวนวันนับตั้งแต่ตายครั้งล่าสุด
  - `$$death_reason_string` – สาเหตุแบบข้อความธรรมดา
  - `$$death_reason_component` – สาเหตุแบบคอมโพเนนต์ JSON
  - `$$death_pos_x` – พิกัด X ตอนตาย
  - `$$death_pos_y` – พิกัด Y ตอนตาย
  - `$$death_pos_z` – พิกัด Z ตอนตาย

## เมื่ออัปเดตตัวแปร [FM Variable] (`fm_variable_updated`)
- ทำงานทุกครั้งที่มีการตั้งค่าหรืออัปเดต [ตัวแปรของ FancyMenu](./variables)
- ตัวแปร:
  - `$$var_name` – ชื่อตัวแปร
  - `$$old_value` – ค่าก่อนหน้า
  - `$$new_value` – ค่าใหม่

## เมื่อดาวน์โหลดไฟล์ผ่านการกระทำ (`file_downloaded_via_action`)
- ทำงานหลังจาก [**Download File to Game Directory** action](./action-scripts#download-file-to-game-directory-download_file_to_game_dir) ทำงานเสร็จ
- ตัวแปร:
  - `$$download_url` – แหล่งที่มาของการดาวน์โหลด
  - `$$target_file_path` – พาธไฟล์ที่บันทึกเมื่อสำเร็จ; หากล้มเหลว ค่านี้อาจมีเพียงไดเรกทอรีปลายทาง เพราะไม่สามารถระบุชื่อไฟล์สุดท้ายได้
  - `$$download_succeeded` – true/false

## เมื่อเลือกไฟล์ (`file_selected_via_action`)
- ทำงานหลังจาก [**Select File from System** action](./action-scripts#select-file-from-system-select_file_to_game_dir) เสร็จสิ้น
- ตัวแปร:
  - `$$selected_file_path` – พาธแบบสัมบูรณ์ของไฟล์ที่เลือก หรือว่างหากยกเลิก
  - `$$target_file_path` – พาธที่แก้ไขแล้วภายในอินสแตนซ์
  - `$$selection_succeeded` – true หากคัดลอกสำเร็จ
  - `$$selection_cancelled` – true หากปิดกล่องโต้ตอบ
  - `$$failure_reason` – ข้อมูลข้อผิดพลาดเมื่อเกิดความล้มเหลว

## เมื่อได้รับข้อความแชต (`chat_message_received`)
- ทำงานเมื่อมีข้อความแชตของผู้เล่นปกติปรากฏบนไคลเอนต์
- ตัวแปร:
  - `$$chat_message_string` – ข้อความแบบข้อความธรรมดา
  - `$$chat_message_component` – คอมโพเนนต์ JSON แบบเต็ม
  - `$$sender_uuid` – UUID ของผู้ส่งหรือ ERROR
  - `$$sender_name` – ชื่อผู้ส่งหรือ ERROR

## เมื่อส่งข้อความแชต (`chat_message_sent`)
- ทำงานเมื่อผู้เล่นในเครื่องส่งข้อความแชต
- ตัวแปร:
  - `$$chat_message_string` – ข้อความแบบข้อความธรรมดา
  - `$$chat_message_component` – คอมโพเนนต์ JSON แบบเต็ม

## เมื่อได้รับเอฟเฟกต์ (`effect_gained`)
- ทำงานเมื่อผู้เล่นได้รับสถานะเอฟเฟกต์
- ตัวแปร:
  - `$$effect_key` – ตำแหน่งทรัพยากรของเอฟเฟกต์
  - `$$effect_type` – positive/negative/neutral
  - `$$effect_duration` – จำนวน tick ที่เหลือ

## เมื่อเอฟเฟกต์หมด (`effect_lost`)
- ทำงานเมื่อผู้เล่นสูญเสียสถานะเอฟเฟกต์
- ตัวแปร:
  - `$$effect_key` – เอฟเฟกต์ที่หมดอายุ
  - `$$effect_type` – หมวดหมู่

## เมื่อค่าประสบการณ์เปลี่ยน (`experience_changed`)
- ทำงานทุกครั้งที่ XP รวมของผู้เล่นเปลี่ยนแปลง
- ตัวแปร:
  - `$$new_experience_amount` – หลังจากเปลี่ยน
  - `$$old_experience_amount` – ก่อนเปลี่ยน
  - `$$is_level_up` – TRUE หากเลเวลเพิ่มขึ้น

## เมื่อได้รับความเสียหาย (`damage_taken`)
- ทำงานหนึ่งครั้งต่อการโดนโจมตีเมื่อผู้เล่นได้รับความเสียหาย
- ตัวแปร:
  - `$$damage_amount` – พลังชีวิตที่ลดลง
  - `$$damage_type` – ตำแหน่งทรัพยากรของประเภทความเสียหาย
  - `$$is_fatal_damage` – TRUE หากถึงตาย
  - `$$damage_source` – ตำแหน่งทรัพยากรของผู้โจมตีหรือ NONE

## เมื่อเริ่มแข็งตัวจากความเย็น (`started_freezing`)
- ทำงานเมื่อผู้เล่นเริ่มแข็งตัวจากความเย็น
- ตัวแปร:
  - `$$freezing_intensity` – 0.0 คือไม่แข็งตัว, 1.0 คือแข็งตัวเต็มที่

## เมื่อหยุดแข็งตัวจากความเย็น (`stopped_freezing`)
- ทำงานเมื่อผู้เล่นหยุดแข็งตัวจากความเย็น
- ตัวแปร:
  - (ไม่มี)

## เมื่อแข็งตัวเต็มที่ (`fully_frozen`)
- ทำงานหนึ่งครั้งเมื่อผู้เล่นแข็งตัวเต็มที่
- ตัวแปร:
  - (ไม่มี)

## เมื่อเริ่มมองไปที่บล็อก (`start_looking_at_block`)
- ทำงานหนึ่งครั้งเมื่อกากบาทเล็งไปที่บล็อกเป็นครั้งแรก (ระยะสูงสุด 20 บล็อก)
- ตัวแปร:
  - `$$block_key` – บล็อกที่เล็งอยู่
  - `$$block_pos_x` – X ของบล็อก
  - `$$block_pos_y` – Y ของบล็อก
  - `$$block_pos_z` – Z ของบล็อก
  - `$$distance_to_player` – ระยะจากดวงตาถึงจุดปะทะ

## เมื่อหยุดมองไปที่บล็อก (`stop_looking_at_block`)
- ทำงานเมื่อกากบาทเล็งไม่ชี้ไปที่บล็อกแล้ว (รายงานบล็อกที่เล็งล่าสุด, ระยะสูงสุด 20 บล็อก)
- ตัวแปร:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`
  - `$$distance_to_player`

## เมื่อเริ่มมองไปที่เอนทิตี (`start_looking_at_entity`)
- ทำงานหนึ่งครั้งเมื่อกากบาทเล็งไปที่เอนทิตีเป็นครั้งแรก (ระยะสูงสุด 20 บล็อก)
- ตัวแปร:
  - `$$entity_key` – ประเภทเอนทิตีที่เล็งอยู่
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## เมื่อหยุดมองไปที่เอนทิตี (`stop_looking_at_entity`)
- ทำงานเมื่อกากบาทเล็งไม่ชี้ไปที่เอนทิตีแล้ว (รายงานเอนทิตีที่เล็งล่าสุด, ระยะสูงสุด 20 บล็อก)
- ตัวแปร:
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## เมื่อเอนทิตีเกิดขึ้น (`entity_spawned`)
- **ต้องมี FancyMenu บนเซิร์ฟเวอร์** ทำงานเมื่อเอนทิตีใด ๆ เกิดขึ้นในโลก/เซิร์ฟเวอร์ที่เชื่อมต่ออยู่
- ตัวแปร:
  - `$$entity_key`
  - `$$distance_to_player` – −1 หากอยู่คนละมิติ
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`
  - `$$dimension_key`
  - `$$is_same_dimension_as_player`

## เมื่อเอนทิตีตาย (`entity_died`)
- **ต้องมี FancyMenu บนเซิร์ฟเวอร์** ทำงานเมื่อเอนทิตีใด ๆ ตายในโลก/เซิร์ฟเวอร์ที่เชื่อมต่ออยู่
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

## เมื่อเอนทิตีเริ่มอยู่ในระยะสายตา (`entity_starts_being_in_sight`)
- ทำงานเมื่อเอนทิตีปรากฏให้เห็นเป็นครั้งแรกภายในระยะ 200 บล็อก
- ตัวแปร:
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## เมื่อเอนทิตีหลุดออกจากระยะสายตา (`entity_stops_being_in_sight`)
- ทำงานเมื่อเอนทิตีที่เคยเห็นได้ออกจากมุมมองหรือเคลื่อนเกิน 200 บล็อก
- ตัวแปร:
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## เมื่อโต้ตอบกับเอนทิตี (`entity_interacted`)
- ทำงานเมื่อผู้เล่นโต้ตอบกับเอนทิตีสำเร็จ
- ตัวแปร:
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## เมื่อขึ้นขี่เอนทิตี (`entity_mounted`)
- ทำงานเมื่อผู้เล่นเริ่มขี่เอนทิตี
- ตัวแปร:
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## เมื่อลงจากเอนทิตี (`entity_unmounted`)
- ทำงานเมื่อผู้เล่นหยุดขี่เอนทิตีปัจจุบัน
- ตัวแปร:
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## เมื่อทำลายบล็อก (`block_broke`)
- ทำงานเมื่อผู้เล่นทำลายบล็อก
- ตัวแปร:
  - `$$block_key`
  - `$$broke_with_item_key` – เครื่องมือที่ใช้หรือ EMPTY
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## เมื่อวางบล็อก (`block_placed`)
- ทำงานเมื่อผู้เล่นวางบล็อก
- ตัวแปร:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## เมื่อโต้ตอบกับบล็อก (`interacted_with_block`)
- ทำงานเมื่อผู้เล่นโต้ตอบกับบล็อกสำเร็จ
- ตัวแปร:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## เมื่อเหยียบลงบนบล็อก (`stepping_on_block`)
- ทำงานเมื่อผู้เล่นก้าวขึ้นไปบนบล็อก
- ตัวแปร:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## เมื่อเข้าสู่ไบโอม (`enter_biome`)
- ทำงานเมื่อผู้เล่นเข้าสู่ไบโอมใหม่
- ตัวแปร:
  - `$$biome_key` – ไบโอมที่เข้าไป

## เมื่อออกจากไบโอม (`leave_biome`)
- ทำงานเมื่อผู้เล่นออกจากไบโอมปัจจุบัน
- ตัวแปร:
  - `$$biome_key` – ไบโอมที่เพิ่งออกมา

## เมื่อเข้าสู่โครงสร้าง (`enter_structure`)
- **ต้องมี FancyMenu บนเซิร์ฟเวอร์** การตรวจจับพื้นที่โครงสร้างแบบหยาบ; อาจทริกเกอร์ใกล้ เหนือ หรือใต้โครงสร้าง
- ตัวแปร:
  - `$$structure_key` – โครงสร้างที่เข้าไป

## เมื่อออกจากโครงสร้าง (`leave_structure`)
- **ต้องมี FancyMenu บนเซิร์ฟเวอร์** การตรวจจับแบบหยาบ; อาจทริกเกอร์ใกล้ขอบเขตของโครงสร้าง
- ตัวแปร:
  - `$$structure_key` – โครงสร้างที่เพิ่งออกมา

## เมื่อเข้าสู่โครงสร้าง (ความแม่นยำสูง) (`enter_structure_high_precision`)
- **ต้องมี FancyMenu บนเซิร์ฟเวอร์** ทำงานเมื่อผู้เล่นก้าวเข้าสู่ bounding boxes ของโครงสร้าง
- ตัวแปร:
  - `$$structure_key`

## เมื่อออกจากโครงสร้าง (ความแม่นยำสูง) (`leave_structure_high_precision`)
- **ต้องมี FancyMenu บนเซิร์ฟเวอร์** ทำงานหลังจากผู้เล่นออกจาก bounding boxes ของโครงสร้าง
- ตัวแปร:
  - `$$structure_key`

## เมื่อเข้าสู่มิติ (`enter_dimension`)
- ทำงานเมื่อผู้เล่นเข้าสู่มิติใหม่
- ตัวแปร:
  - `$$dimension_key` – มิติที่เข้าไป

## เมื่อเริ่มว่ายน้ำ (`start_swimming`)
- ทำงานเมื่อผู้เล่นเริ่มว่ายน้ำ
- ตัวแปร:
  - `$$fluid_type` – ตำแหน่งทรัพยากรของของเหลว

## เมื่อหยุดว่ายน้ำ (`stop_swimming`)
- ทำงานเมื่อผู้เล่นหยุดว่ายน้ำ
- ตัวแปร:
  - `$$fluid_type` – ของเหลวที่หยุดว่ายในนั้น

## เมื่อเริ่มสัมผัสของเหลว (`start_touching_fluid`)
- ทำงานเมื่อผู้เล่นเริ่มสัมผัสของเหลว
- ตัวแปร:
  - `$$fluid_type` – ของเหลวที่สัมผัส

## เมื่อหยุดสัมผัสของเหลว (`stop_touching_fluid`)
- ทำงานเมื่อผู้เล่นหยุดสัมผัสของเหลว
- ตัวแปร:
  - `$$fluid_type` – ของเหลวที่ไม่ได้สัมผัสแล้ว

## เมื่อแทร็กเพลงเริ่มเล่น (`music_track_started`)
- ทำงานเมื่อเพลงแทร็กใหม่เริ่มเล่น
- ตัวแปร:
  - `$$track_resource_location` – ไฟล์เสียง
  - `$$track_display_name` – ชื่อที่อ่านได้หรือ UNKNOWN
  - `$$track_artist` – ศิลปินหรือ UNKNOWN
  - `$$track_duration_ms` – มิลลิวินาที (0 หากไม่ทราบ)

## เมื่อแทร็กเพลงหยุดเล่น (`music_track_stopped`)
- ทำงานเมื่อเพลงแทร็กปัจจุบันจบลงหรือถูกแทนที่
- ตัวแปร:
  - `$$track_resource_location`
  - `$$track_display_name`
  - `$$track_artist`
  - `$$track_duration_ms`

## เมื่อมีการทริกเกอร์เสียงในโลก (`world_sound_triggered`)
- ทำงานเมื่อเสียงแบบมีตำแหน่งในโลกเริ่มเล่นใกล้ผู้เล่น
- ตัวแปร:
  - `$$sound_resource_location` – ไฟล์เสียง
  - `$$sound_display_name` – ชื่อซับไตเติลเมื่อมีให้ใช้
  - `$$sound_origin_pos_x`
  - `$$sound_origin_pos_y`
  - `$$sound_origin_pos_z`
  - `$$sound_origin_distance_to_player`
  - `$$sound_origin_direction_from_player` – องศา 0–360 เทียบกับทิศที่หันอยู่

## เมื่อสภาพอากาศเปลี่ยน (`weather_changed`)
- ทำงานเมื่อสภาพอากาศเปลี่ยนทั่วโลกหรือเฉพาะพื้นที่ (การเปลี่ยนไบโอมหรือเข้าไปในอาคารอาจทริกเกอร์ซ้ำ)
- ตัวแปร:
  - `$$weather_type` – clear/rain/thunder
  - `$$weather_can_snow` – TRUE หากมีการแสดงหิมะ
  - `$$weather_can_rain` – TRUE หากมีการแสดงฝน

## เมื่อเริ่มติดไฟ (`started_burning`)
- ทำงานเมื่อผู้เล่นเริ่มติดไฟ
- ตัวแปร:
  - (ไม่มี)

## เมื่อหยุดติดไฟ (`stopped_burning`)
- ทำงานเมื่อผู้เล่นหยุดติดไฟ
- ตัวแปร:
  - (ไม่มี)

## เมื่อเริ่มจมน้ำ (`started_drowning`)
- ทำงานเมื่อผู้เล่นเริ่มได้รับความเสียหายจากการจมน้ำ
- ตัวแปร:
  - (ไม่มี)

## เมื่อพิกัดเปลี่ยน (`position_changed`)
- ทำงานทุกครั้งที่พิกัดบล็อกของผู้เล่นเปลี่ยน
- ตัวแปร:
  - `$$old_pos_x` – X ของบล็อกก่อนหน้า
  - `$$old_pos_y` – Y ของบล็อกก่อนหน้า
  - `$$old_pos_z` – Z ของบล็อกก่อนหน้า
  - `$$new_pos_x` – X ของบล็อกใหม่
  - `$$new_pos_y` – Y ของบล็อกใหม่
  - `$$new_pos_z` – Z ของบล็อกใหม่

## เมื่อเริ่มวิ่ง (`started_running`)
- ทำงานเมื่อผู้เล่นเริ่มสปรินต์
- ตัวแปร:
  - (ไม่มี)

## เมื่อหยุดวิ่ง (`stopped_running`)
- ทำงานเมื่อผู้เล่นหยุดสปรินต์
- ตัวแปร:
  - (ไม่มี)

## เมื่อกระโดด (`jump`)
- ทำงานทุกครั้งที่ผู้เล่นกระโดด
- ตัวแปร:
  - (ไม่มี)

## เมื่อเข้าร่วมเซิร์ฟเวอร์ (`server_joined`)
- ทำงานหลังจากเข้าร่วมเซิร์ฟเวอร์ผู้เล่นหลายคนสำเร็จ
- ตัวแปร:
  - `$$server_ip` – ที่อยู่เซิร์ฟเวอร์ที่เข้าร่วม

## เมื่อออกจากเซิร์ฟเวอร์ (`server_left`)
- ทำงานหลังจากตัดการเชื่อมต่อจากเซิร์ฟเวอร์ผู้เล่นหลายคน
- ตัวแปร:
  - `$$server_ip` – ที่อยู่เซิร์ฟเวอร์ที่ออกมา

## เมื่อเข้าโลกโหมดผู้เล่นคนเดียว (`world_entered`)
- ทำงานหลังจากโลกโหมดผู้เล่นคนเดียวโหลดเสร็จและควบคุมกลับมา
- ตัวแปร:
  - `$$world_name` – ชื่อที่แสดง
  - `$$world_save_path` – โฟลเดอร์บันทึกแบบสัมบูรณ์
  - `$$world_difficulty` – คีย์ความยาก
  - `$$world_cheats_allowed` – TRUE หากเปิดใช้สูตรโกง
  - `$$world_icon_path` – พาธไอคอนแบบสัมบูรณ์
  - `$$world_is_first_join` – TRUE ในการเข้าใช้งานครั้งแรกจริง ๆ

## เมื่อออกจากโลกโหมดผู้เล่นคนเดียว (`world_left`)
- ทำงานหลังจากโลกโหมดผู้เล่นคนเดียวปิดและบันทึกเสร็จ
- ตัวแปร:
  - `$$world_name`
  - `$$world_save_path`
  - `$$world_difficulty`
  - `$$world_cheats_allowed`
  - `$$world_icon_path`

## เมื่อผู้เล่นคนอื่นเข้าร่วมโลก/เซิร์ฟเวอร์ (`other_player_joined_world`)
- ทำงานเมื่อผู้เล่นคนอื่นเข้าร่วมโลก/เซิร์ฟเวอร์ปัจจุบัน
- ตัวแปร:
  - `$$player_name` – ชื่อของผู้เล่นที่เข้าร่วม
  - `$$player_uuid` – UUID

## เมื่อผู้เล่นคนอื่นออกจากโลก/เซิร์ฟเวอร์ (`other_player_left_world`)
- ทำงานเมื่อผู้เล่นคนอื่นออกจากโลก/เซิร์ฟเวอร์ปัจจุบัน
- ตัวแปร:
  - `$$player_name`
  - `$$player_uuid`

## เมื่อผู้เล่นคนอื่นตาย (`other_player_died`)
- ทำงานเมื่อผู้เล่นคนอื่นในโลกปัจจุบันตาย
- ตัวแปร:
  - `$$player_name`
  - `$$player_uuid`
  - `$$death_pos_x`
  - `$$death_pos_y`
  - `$$death_pos_z`

## เมื่อเก็บไอเท็ม (`item_picked_up`)
- ทำงานเมื่อผู้เล่นเก็บเอนทิตีไอเท็ม
- ตัวแปร:
  - `$$item_key` – ตำแหน่งทรัพยากรของไอเท็มที่เก็บ

## เมื่อทิ้งไอเท็ม (`item_dropped`)
- ทำงานเมื่อผู้เล่นทิ้งไอเท็มจากอินเวนทอรี
- ตัวแปร:
  - `$$item_key` – ตำแหน่งทรัพยากรของไอเท็มที่ทิ้ง

## เมื่อใช้ไอเท็มจนหมด (`item_consumed`)
- ทำงานเมื่อผู้เล่นใช้ไอเท็มจนเสร็จสิ้น
- ตัวแปร:
  - `$$item_key` – ไอเท็มที่ใช้หมด

## เมื่อชี้ที่ไอเท็มในอินเวนทอรี (`item_hovered_in_inventory`)
- ทำงานเมื่อผู้ใช้ชี้ไปที่ไอเท็มในหน้าจออินเวนทอรีใด ๆ
- ตัวแปร:
  - `$$item_key` – ตำแหน่งทรัพยากรของไอเท็มที่ชี้
  - `$$item_display_name_string` – ชื่อแสดงผลแบบข้อความธรรมดา
  - `$$item_display_name_json` – ชื่อแสดงผลของไอเท็มแบบคอมโพเนนต์ JSON

## เมื่อใช้ไอเท็ม (`item_used`)
- ทำงานเมื่อผู้เล่นใช้งานไอเท็ม
- ตัวแปร:
  - `$$item_key` – ไอเท็มที่ใช้
  - `$$used_on_type` – block/entity/self/none
  - `$$used_on_entity_key` – ประเภทเอนทิตีเป้าหมายหรือว่าง
  - `$$used_on_block_key` – บล็อกเป้าหมายหรือว่าง
  - `$$target_pos_x` – X เป้าหมายหรือ -1
  - `$$target_pos_y` – Y เป้าหมายหรือ -1
  - `$$target_pos_z` – Z เป้าหมายหรือ -1

## เมื่อไอเท็มแตก (`item_broke`)
- ทำงานเมื่อไอเท็มในอินเวนทอรีของผู้เล่นแตก
- ตัวแปร:
  - `$$item_key` – ไอเท็มที่แตก
  - `$$item_type` – tool/armor/other
