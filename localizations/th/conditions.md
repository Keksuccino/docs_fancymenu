---
title: เงื่อนไข (ข้อกำหนด)
description: วิธีใช้ข้อกำหนดการโหลด
---

# ข้อกำหนด

ข้อกำหนด (เรียกว่า **Loading Requirements** ในบางเมนู) ใช้สำหรับแสดงหรือซ่อนเนื้อหาตามเงื่อนไข เช่น สถานะการชี้เมาส์ ขนาดหน้าต่าง หรือว่ามีการโหลดโลกอยู่หรือไม่

คุณสามารถใช้ได้กับ [องค์ประกอบ](./elements), เลย์เอาต์ทั้งชุด และ [สคริปต์การกระทำ](./action-scripts)

# การเพิ่มข้อกำหนดให้กับองค์ประกอบ

หากต้องการเพิ่มข้อกำหนดให้องค์ประกอบ ให้คลิกขวาที่องค์ประกอบนั้นแล้วเลือก **Loading Requirements**

ระบบจะตรวจสอบข้อกำหนดขณะที่เมนูเปิดอยู่ ดังนั้นองค์ประกอบจะอัปเดตเมื่อเงื่อนไขเปลี่ยนไป

# ข้อกำหนดระดับทั้งเลย์เอาต์

คุณยังสามารถเปลี่ยนการมองเห็นของเลย์เอาต์ทั้งชุดได้ โดยคลิกขวาที่ **พื้นหลังของตัวแก้ไข** แล้วคลิก **Loading Requirements [Layout-Wide]**

เมื่อผลลัพธ์ระดับทั้งเลย์เอาต์เปลี่ยน FancyMenu จะสร้างหน้าจอปัจจุบันใหม่และใช้เลย์เอาต์ที่ข้อกำหนดผ่านตามเงื่อนไขในขณะนั้น

# สคริปต์การกระทำ

ข้อกำหนดยังสามารถใช้ในสคริปต์การกระทำได้ด้วย
คุณสามารถเพิ่มได้ในหน้าจอแก้ไขสคริปต์การกระทำ และใช้เพื่อให้ดำเนินการบางอย่างเฉพาะเมื่อเงื่อนไขของข้อกำหนดเป็นจริงเท่านั้น

# การรวมข้อกำหนด

- ข้อกำหนดที่อยู่นอกกลุ่มใช้แบบ **AND** ดังนั้นทุกข้อจะต้องผ่าน
- ภายในกลุ่ม ให้เลือก **AND** หรือ **OR**
- ใช้ **IF NOT** เพื่อกลับค่าของข้อกำหนดหนึ่งรายการ

กฎเหล่านี้เหมือนกันสำหรับองค์ประกอบ เลย์เอาต์ และสคริปต์การกระทำ

# ค่าของข้อกำหนด

สำหรับข้อกำหนดที่ต้องใช้ค่า ให้ใช้ **Edit Requirement Value** และทำตามคำอธิบายที่แสดงในตัวแก้ไข บางช่องรองรับการเติมด้วย **TAB**

หากข้อกำหนดที่นำเข้าใช้งานไม่ได้หลังจากเปลี่ยน FancyMenu หรือแอดออน ให้แก้ไขในหน้าจอข้อกำหนดและตรวจสอบข้อผิดพลาดใน `logs/latest.log`

ตัวแก้ไขข้อกำหนดรองรับเมนูคลิกขวา การนำทางด้วยแป้นพิมพ์ การค้นหา undo/redo (`Ctrl/Command + Z` / `Ctrl/Command + Y`) และ `Ctrl/Command + S` เพื่อบันทึก

# รายละเอียดข้อกำหนด

ส่วนนี้แสดงรายการข้อกำหนดในตัวของ FancyMenu

## Is Element Hovered (`fancymenu_visibility_requirement_is_element_hovered`)

**Purpose:** ตรวจสอบว่าองค์ประกอบที่ระบุถูกชี้ด้วยเคอร์เซอร์เมาส์อยู่หรือไม่

**Value:** ต้องระบุ — [ตัวระบุขององค์ประกอบ](./element-identifiers) เป้าหมาย (เช่น `some_element_ID`)

## Is Element Focused (`is_element_focused`)

**Purpose:** ตรวจสอบว่าองค์ประกอบที่ระบุตอนนี้มีโฟกัสจากแป้นพิมพ์อยู่หรือไม่ (เช่น ช่องข้อความหรือปุ่มที่มีโฟกัส)

**Value:** ต้องระบุ — Element ID ขององค์ประกอบเป้าหมาย (ID เดียวกับที่แสดงในตัวแก้ไข)

> [!NOTE]
> สถานะ focus และ hover เป็นคนละอย่างกัน องค์ประกอบอาจยังคงแสดงสถานะมีโฟกัสอยู่หลังจากตัวชี้เมาส์เลื่อนออกไป การคลิกหรือการนำทางด้วยคีย์บอร์ดสามารถทำให้มันมีโฟกัสได้

## Is Any Element Hovered (`fancymenu_visibility_requirement_is_any_element_hovered`)

**Purpose:** ตรวจสอบองค์ประกอบที่มองเห็นได้/เรนเดอร์ได้ในเลเยอร์การปรับแต่งที่กำลังใช้งานอยู่ รวมถึงองค์ประกอบที่มาจากเลย์เอาต์ที่ซ้อนกัน

**Value:** ไม่ต้องระบุ

## Is Any Button Hovered (`fancymenu_visibility_requirement_is_any_button_hovered`)

**Purpose:** ตรวจสอบว่ามีปุ่ม vanilla หรือปุ่มกำหนดเองใด ๆ ที่มองเห็นได้/เรนเดอร์ได้ในเลเยอร์การปรับแต่งที่กำลังใช้งานอยู่และกำลังถูกชี้อยู่หรือไม่ รวมถึงปุ่มที่มาจากเลย์เอาต์ที่ซ้อนกัน

**Value:** ไม่ต้องระบุ

## Is Layout Enabled (`fancymenu_visibility_requirement_is_layout_enabled`)

**Purpose:** ตรวจสอบว่าเลย์เอาต์ที่ระบุถูกเปิดใช้งานอยู่หรือไม่

**Value:** ต้องระบุ — ชื่อของเลย์เอาต์ (เช่น `my_cool_main_menu_layout`)

## Is Scheduler Running (`fancymenu_visibility_requirement_is_scheduler_running`)

**Purpose:** ตรวจสอบว่า [scheduler](./schedulers) กำลังทำงานอยู่หรือไม่

**Value:** ต้องระบุ — Scheduler ID (เช่น `my_scheduler`)

## Is GUI Scale (`fancymenu_loading_requirement_is_gui_scale`)

**Purpose:** ตรวจสอบว่า GUI scale ปัจจุบันตรงกับเงื่อนไขบางอย่างหรือไม่

**Value:** ต้องระบุ — ใช้ตัวเลขสำหรับความเท่ากัน, `>` สำหรับมากกว่า, หรือ `<` สำหรับน้อยกว่า

หลายเงื่อนไขที่คั่นด้วยจุลภาคจะถูกเชื่อมด้วย AND เช่น `>1,<4` จะผ่านเมื่อ GUI scale มากกว่า `1` และน้อยกว่า `4` เท่านั้น

## Is Button Active (`fancymenu_visibility_requirement_is_button_active`)

**Purpose:** ตรวจสอบว่าปุ่มที่ระบุใช้งานได้ (คลิกได้) หรือไม่

**Value:** ต้องระบุ — Element ID ของปุ่มเป้าหมาย (เช่น "some_element_ID")

## Is Screen Title (`is_menu_title`)

**Purpose:** ตรวจสอบว่าชื่อที่แสดงของหน้าจอตรงกับข้อความหรือคีย์การแปลที่กำหนดหรือไม่ โดยจะตรวจเฉพาะชื่อที่แสดงของหน้าจอ เช่น "Options" หรือ "Pause" เท่านั้น และจะไม่ตรวจตัวระบุของเมนู/หน้าจอ (เช่น `title_screen`)!

**Value:** ต้องระบุ — ข้อความชื่อหน้าจอหรือคีย์การแปลแบบตรงตัว

## Is Key Pressed (`is_key_pressed`)

**Purpose:** ตรวจสอบว่ามีการกดปุ่มคีย์บอร์ดที่ระบุอยู่ในตอนนี้หรือไม่

**Value:** ต้องระบุ — key code ของปุ่มเป้าหมาย เลือกผ่าน UI เมื่อแก้ไขค่าข้อกำหนด

## Is Any Screen Open (`is_any_screen_open`)

**Purpose:** ตรวจสอบว่ามีหน้าจอ/เมนูใดเปิดอยู่ในตอนนี้หรือไม่ (จะคืนค่า false หากไม่มีหน้าจอแสดงอยู่)

**Value:** ไม่ต้องระบุ

## Is MC Debug Overlay Enabled (`is_debug_overlay_enabled`)

**Purpose:** ตรวจสอบว่า debug overlay ของ F3 แสดงอยู่ในตอนนี้หรือไม่

**Value:** ไม่ต้องระบุ

## Is Active Cursor Type (`is_active_cursor_type`)

**Purpose:** ตรวจสอบว่าชนิดเคอร์เซอร์ที่ใช้งานอยู่ตอนนี้ของ FancyMenu ตรงกับชนิดเคอร์เซอร์มาตรฐานที่กำหนดหรือไม่

**Value:** ต้องระบุ — ประเภทเคอร์เซอร์: `normal`, `writing`, `crosshair`, `pointing_hand`, `resize_horizontal`, `resize_vertical`, `resize_nwse`, `resize_nesw`, `resize_all`, หรือ `not_allowed`

## Is Customization Menu Bar Visible (`is_customization_menu_bar_visible`)

**Purpose:** ตรวจสอบว่าแถบเมนูการปรับแต่งของ FancyMenu แสดงอยู่ในตอนนี้หรือไม่

**Value:** ไม่ต้องระบุ

## Is Modpack Mode Enabled (`is_modpack_mode_enabled`)

**Purpose:** ตรวจสอบว่า Modpack Mode ของ FancyMenu เปิดใช้อยู่หรือไม่

**Value:** ไม่ต้องระบุ

## Mouse Button Is Pressed (`mouse_click`)

**Purpose:** คืนค่า true ขณะที่ปุ่มเมาส์ที่ระบุถูกกดค้างอยู่ นี่ไม่ใช่เหตุการณ์คลิกแบบครั้งเดียว; ให้ใช้ [**On Mouse Button Clicked** listener](./listeners#on-mouse-button-clicked-mouse_button_clicked) เมื่อการกระทำควรถูกเรียกเพียงครั้งเดียวต่อหนึ่งคลิก

**Value:** ต้องระบุ — `left` หรือ `right` เพื่อบอกว่าต้องตรวจปุ่มเมาส์ใด

## Is Fullscreen (`fancymenu_loading_requirement_is_fullscreen`)

**Purpose:** ตรวจสอบว่าเกมอยู่ในโหมดเต็มหน้าจอหรือไม่

**Value:** ไม่ต้องระบุ

## Is Window Width (`fancymenu_loading_requirement_is_window_width`)

**Purpose:** ตรวจสอบว่าความกว้างของหน้าต่างเกมตรงกับค่าที่กำหนดหรือไม่

**Value:** ต้องระบุ — ความกว้างหน้าต่างเป็นพิกเซล (เช่น "1920") สามารถระบุได้หลายค่าโดยคั่นด้วยจุลภาค

## Is Window Height (`fancymenu_loading_requirement_is_window_height`)

**Purpose:** ตรวจสอบว่าความสูงของหน้าต่างเกมตรงกับค่าที่กำหนดหรือไม่

**Value:** ต้องระบุ — ความสูงหน้าต่างเป็นพิกเซล (เช่น "1080") สามารถระบุได้หลายค่าโดยคั่นด้วยจุลภาค

## Is Window Width Bigger Than (`fancymenu_loading_requirement_is_window_width_bigger_than`)

**Purpose:** ตรวจสอบว่าความกว้างของหน้าต่างเกมมากกว่าค่าที่กำหนดหรือไม่

**Value:** ต้องระบุ — ความกว้างหน้าต่างเป็นพิกเซล (เช่น "1920")

## Is Window Height Bigger Than (`fancymenu_loading_requirement_is_window_height_bigger_than`)

**Purpose:** ตรวจสอบว่าความสูงของหน้าต่างเกมมากกว่าค่าที่กำหนดหรือไม่

**Value:** ต้องระบุ — ความสูงหน้าต่างเป็นพิกเซล (เช่น "1080")

## Is Multiplayer (`fancymenu_loading_requirement_is_multiplayer`)

**Purpose:** ตรวจสอบว่าผู้เล่นอยู่ในโลกแบบผู้เล่นหลายคนอยู่ในตอนนี้หรือไม่

**Value:** ไม่ต้องระบุ

## Is Singleplayer (`fancymenu_loading_requirement_is_singpleplayer`)

**Purpose:** ตรวจสอบว่าผู้เล่นอยู่ในโลกแบบผู้เล่นคนเดียวอยู่ในตอนนี้หรือไม่

**Value:** ไม่ต้องระบุ

## Is World Loaded (`fancymenu_loading_requirement_is_world_loaded`)

**Purpose:** ตรวจสอบว่ามีโลกใดถูกโหลดอยู่ในตอนนี้หรือไม่

**Value:** ไม่ต้องระบุ

## Is Adventure (`fancymenu_visibility_requirement_is_adventure`)

**Purpose:** ตรวจสอบว่าผู้เล่นอยู่ในโหมดเกม Adventure อยู่ในตอนนี้หรือไม่

**Value:** ไม่ต้องระบุ

## Is Creative (`fancymenu_visibility_requirement_is_creative`)

**Purpose:** ตรวจสอบว่าผู้เล่นอยู่ในโหมดเกม Creative อยู่ในตอนนี้หรือไม่

**Value:** ไม่ต้องระบุ

## Is Spectator (`fancymenu_visibility_requirement_is_spectator`)

**Purpose:** ตรวจสอบว่าผู้เล่นอยู่ในโหมดเกม Spectator อยู่ในตอนนี้หรือไม่

**Value:** ไม่ต้องระบุ

## Is Survival (`fancymenu_visibility_requirement_is_survival`)

**Purpose:** ตรวจสอบว่าผู้เล่นอยู่ในโหมดเกม Survival อยู่ในตอนนี้หรือไม่

**Value:** ไม่ต้องระบุ

## Is Game Mode (`is_gamemode`)

**Purpose:** ตรวจสอบว่าผู้เล่นอยู่ในโหมดเกมที่ระบุหรือไม่

**Value:** ต้องระบุ — ชื่อโหมดเกม (เช่น "creative", "survival", "adventure", "spectator")

## Is Difficulty (`is_difficulty`)

**Purpose:** ตรวจสอบว่าความยากของเกมปัจจุบันตรงกับค่าที่กำหนดหรือไม่

**Value:** ต้องระบุ — ชื่อความยาก (เช่น "peaceful", "easy", "normal", "hard")

## Is Hardcore (`is_hardcore`)

**Purpose:** ตรวจสอบว่าโลกที่โหลดอยู่ตอนนี้เป็นโหมด hardcore หรือไม่

**Value:** ไม่ต้องระบุ

## Is Camera Perspective (`is_camera_perspective`)

**Purpose:** ตรวจสอบว่ามุมมองกล้องปัจจุบันตรงกับมุมมองที่กำหนดหรือไม่

**Value:** ต้องระบุ — `first_person`, `third_person_back`, หรือ `third_person_front`

## Is Raining (`is_raining`)

**Purpose:** ตรวจสอบว่าตอนนี้กำลังมีฝนตกที่ตำแหน่งของผู้เล่นหรือไม่

**Value:** ไม่ต้องระบุ

## Is Thundering (`is_thundering`)

**Purpose:** ตรวจสอบว่าตอนนี้มีพายุฝนฟ้าคะนองในโลกของผู้เล่นหรือไม่

**Value:** ไม่ต้องระบุ

## Is Clear Weather (`is_clear_weather`)

**Purpose:** ตรวจสอบว่าสภาพอากาศตอนนี้ปลอดโปร่งหรือไม่ (ไม่มีฝนหรือลมฟ้าคะนอง)

**Value:** ไม่ต้องระบุ

## Is Snowing (`is_snowing`)

**Purpose:** ตรวจสอบว่าตอนนี้กำลังมีหิมะตกที่ตำแหน่งของผู้เล่นหรือไม่

**Value:** ไม่ต้องระบุ

## Is Player Running (`is_player_running`)

**Purpose:** ตรวจสอบว่าผู้เล่นกำลังวิ่งเร็วอยู่ในตอนนี้หรือไม่

**Value:** ไม่ต้องระบุ

## Is Player Sneaking (`is_player_sneaking`)

**Purpose:** ตรวจสอบว่าผู้เล่นกำลังก้ม/ย่องอยู่ในตอนนี้หรือไม่

**Value:** ไม่ต้องระบุ

## Is Player Using Item (`is_player_using_item`)

**Purpose:** ตรวจสอบว่าผู้เล่นกำลังใช้งานไอเท็มอยู่ในตอนนี้หรือไม่

**Value:** ไม่ต้องระบุ

## Is Player Swimming (`is_player_swimming`)

**Purpose:** ตรวจสอบว่าผู้เล่นกำลังว่ายน้ำอยู่ในตอนนี้หรือไม่

**Value:** ไม่ต้องระบุ

## Is Player Jumping or Falling (`is_player_jumping`)

**Purpose:** คืนค่า true ขณะที่ผู้เล่นอยู่กลางอากาศในสภาวะกระโดดหรือตกตามปกติ โดยจะไม่รวมการว่ายน้ำ ของเหลว การบินด้วย elytra การนอน สถานะว่ายน้ำแบบภาพ และการคลาน

**Value:** ไม่ต้องระบุ

## Is Player Under Water (`is_player_under_water`)

**Purpose:** ตรวจสอบว่าผู้เล่นอยู่ใต้น้ำทั้งหมดหรือไม่

**Value:** ไม่ต้องระบุ

## Is Player In Water (`is_player_in_water`)

**Purpose:** ตรวจสอบว่าผู้เล่นอยู่ในน้ำหรือไม่ (อาจจมอยู่บางส่วน)

**Value:** ไม่ต้องระบุ

## Is Player In Lava (`is_player_in_lava`)

**Purpose:** ตรวจสอบว่าผู้เล่นอยู่ในลาวาหรือไม่

**Value:** ไม่ต้องระบุ

## Is Player In Fluid (`is_player_in_fluid`)

**Purpose:** ตรวจสอบว่าผู้เล่นอยู่ในของเหลวใด ๆ หรือไม่ (น้ำ ลาวา ฯลฯ)

**Value:** ไม่ต้องระบุ

## Is Player Riding Entity/Vehicle (`is_player_riding_entity`)

**Purpose:** ตรวจสอบว่าผู้เล่นกำลังขี่เอนทิตีใด ๆ อยู่หรือไม่

**Value:** ไม่ต้องระบุ

## Is Player Riding Jumpable Entity (`is_player_riding_jumpable_entity`)

**Purpose:** ตรวจสอบว่าผู้เล่นกำลังขี่เอนทิตีที่กระโดดได้ (เช่น ม้า) อยู่หรือไม่

**Value:** ไม่ต้องระบุ

## Is Player Riding Entity With Health (`is_player_riding_entity_with_health`)

**Purpose:** ตรวจสอบว่าผู้เล่นกำลังขี่เอนทิตีที่มีชีวิตและมีพลังชีวิต (เช่น สัตว์ ไม่ใช่เรือ) อยู่หรือไม่

**Value:** ไม่ต้องระบุ

## Is Player In Powder Snow (`is_player_in_powder_snow`)

**Purpose:** ตรวจสอบว่าผู้เล่นอยู่ในหิมะผงอยู่หรือไม่

**Value:** ไม่ต้องระบุ

## Was Player In Powder Snow (`was_player_in_powder_snow`)

**Purpose:** ตรวจสอบว่าผู้เล่นเคยอยู่ในหิมะผงหรือไม่ (ใช้สำหรับเอฟเฟกต์ที่คงอยู่หลังจากออกมา)

**Value:** ไม่ต้องระบุ

## Is Player Wearing Pumpkin (`is_player_wearing_pumpkin`)

**Purpose:** ตรวจสอบว่าผู้เล่นสวมฟักทองแกะสลักอยู่บนหัวหรือไม่

**Value:** ไม่ต้องระบุ

## Is Player Flying With Elytra (`is_player_flying_with_elytra`)

**Purpose:** ตรวจสอบว่าผู้เล่นกำลังบินด้วย elytra อยู่หรือไม่

**Value:** ไม่ต้องระบุ

## Is Player Creative Flying (`is_player_creative_flying`)

**Purpose:** ตรวจสอบว่าผู้เล่นกำลังบินในโหมด creative อยู่หรือไม่

**Value:** ไม่ต้องระบุ

## Has Player Absorption Hearts (`has_player_absorption_hearts`)

**Purpose:** ตรวจสอบว่าผู้เล่นมีหัวใจเสริมการดูดซับ (หัวใจสีทอง) อยู่หรือไม่

**Value:** ไม่ต้องระบุ

## Is Player Withered (`is_player_withered`)

**Purpose:** ตรวจสอบว่าผู้เล่นได้รับผลของ wither effect หรือไม่

**Value:** ไม่ต้องระบุ

## Is Player Fully Frozen (`is_player_fully_frozen`)

**Purpose:** ตรวจสอบว่าผู้เล่นถูกแช่แข็งจนหมดแล้วหรือไม่ (โดยปกติมาจาก powder snow)

**Value:** ไม่ต้องระบุ

## Is Player Poisoned (`is_player_poisoned`)

**Purpose:** ตรวจสอบว่าผู้เล่นได้รับผลของ poison effect หรือไม่

**Value:** ไม่ต้องระบุ

## Is Player In Biome (`is_player_in_biome`)

**Purpose:** ตรวจสอบว่าผู้เล่นอยู่ในไบโอมที่ระบุหรือไม่

**Value:** ต้องระบุ — ตัวระบุไบโอม (เช่น `minecraft:birch_forest`)

## Is Player In Dimension (`is_player_in_dimension`)

**Purpose:** ตรวจสอบว่าผู้เล่นอยู่ในมิติที่ระบุหรือไม่

**Value:** ต้องระบุ — ตัวระบุมิติ (เช่น `minecraft:overworld`, `minecraft:the_nether`, `minecraft:the_end`)

## Is Player In Structure (`is_player_in_structure`)

**Purpose:** ตรวจสอบว่าผู้เล่นอยู่ภายในโครงสร้างที่ระบุอยู่ในตอนนี้หรือไม่ ต้องมี FancyMenu บนเซิร์ฟเวอร์สำหรับโลกแบบเซิร์ฟเวอร์

**Value:** ต้องระบุ — ตัวระบุโครงสร้าง (เช่น `minecraft:village`)

## Is Entity Nearby (`is_entity_nearby`)

**Purpose:** ตรวจสอบว่าเอนทิตีชนิดที่ระบุอยู่ภายในรัศมีที่กำหนดจากผู้เล่นหรือไม่

**Value:** ต้องระบุ — รูปแบบ: "radius:entity_id" (เช่น `10:minecraft:pig` - ตรวจสอบหมูภายในระยะ 10 บล็อก)

## Is Effect Active (`is_effect_active`)

**Purpose:** ตรวจสอบว่าผู้เล่นมีเอฟเฟกต์ยาใด ๆ กำลังทำงานอยู่หรือไม่

**Value:** ต้องระบุ — ตัวระบุเอฟเฟกต์ (เช่น `minecraft:speed`, `minecraft:strength`)

## Is Any Effect Active (`is_any_effect_active`)

**Purpose:** ตรวจสอบว่าผู้เล่นมีเอฟเฟกต์ยาใด ๆ กำลังทำงานอยู่หรือไม่

**Value:** ไม่ต้องระบุ

## Is Player Left-Handed (`is_left_handed`)

**Purpose:** ตรวจสอบว่าผู้เล่นตั้งค่าเป็นโหมดถนัดซ้ายในตัวเลือกเกมหรือไม่

**Value:** ไม่ต้องระบุ

## Is Inventory Slot Filled (`is_inventory_slot_filled`)

**Purpose:** ตรวจสอบว่าช่องเก็บของที่ระบุมีไอเท็มอยู่หรือไม่

**Value:** ต้องระบุ — หมายเลขช่อง (0-35 สำหรับคลังหลัก, ช่อง 0-8 คือ hotbar)

## Is Item Hovered in Inventory (`is_item_hovered_in_inventory`)

**Purpose:** ตรวจสอบว่าเคอร์เซอร์กำลังชี้ไอเท็มใด ๆ ในหน้าจอคลังอยู่หรือไม่

**Value:** ไม่ต้องระบุ

## Is Cursor Holding Inventory Item (`is_cursor_holding_inventory_item`)

**Purpose:** ตรวจสอบว่าเคอร์เซอร์กำลังถือสแตกไอเท็มจากคลังอยู่หรือไม่

**Value:** ไม่ต้องระบุ

## Is Hotbar Slot Selected (`is_hotbar_slot_active`)

**Purpose:** ตรวจสอบว่าช่อง hotbar ที่ระบุถูกเลือกอยู่หรือไม่

**Value:** ต้องระบุ — หมายเลขช่อง hotbar (0-8)

## Has Player Permission Level (`fancymenu_loading_requirement_has_player_permission_level`)

**Purpose:** ตรวจสอบว่าผู้เล่นมีระดับสิทธิ์/OP อย่างน้อยตามที่ระบุในโลกหรือเซิร์ฟเวอร์ปัจจุบันหรือไม่

**Value:** ต้องระบุ — หมายเลขระดับสิทธิ์ (0-4 โดย 4 คือ server operator)

## Is Attack Strength Weakened (`is_attack_strength_weakened`)

**Purpose:** ตรวจสอบว่าพลังโจมตีของผู้เล่นอ่อนลงอยู่ในตอนนี้หรือไม่ (ยังชาร์จไม่เต็ม)

**Value:** ไม่ต้องระบุ

## Is Real Time Day (`fancymenu_visibility_requirement_is_realtime_day`)

**Purpose:** ตรวจสอบว่าวันที่ของเดือนตามเวลาจริงในโลกจริงตรงกับค่าที่กำหนดหรือไม่

**Value:** ต้องระบุ — หมายเลขวันที่ (1-31) สามารถระบุได้หลายค่าโดยคั่นด้วยจุลภาค

## Is Real Time Hour (`fancymenu_visibility_requirement_is_realtime_hour`)

**Purpose:** ตรวจสอบว่าชั่วโมงตามเวลาจริงในโลกจริงตรงกับค่าที่กำหนดหรือไม่

**Value:** ต้องระบุ — ชั่วโมงในรูปแบบ 24 ชั่วโมง (0-23) สามารถระบุได้หลายค่าโดยคั่นด้วยจุลภาค

## Is Real Time Minute (`fancymenu_visibility_requirement_is_realtime_minute`)

**Purpose:** ตรวจสอบว่านาทีตามเวลาจริงในโลกจริงตรงกับค่าที่กำหนดหรือไม่

**Value:** ต้องระบุ — นาที (0-59) สามารถระบุได้หลายค่าโดยคั่นด้วยจุลภาค

## Is Real Time Month (`fancymenu_visibility_requirement_is_realtime_month`)

**Purpose:** ตรวจสอบว่าเดือนตามเวลาจริงในโลกจริงตรงกับค่าที่กำหนดหรือไม่

**Value:** ต้องระบุ — หมายเลขเดือน (1-12 โดย 1 คือมกราคม) สามารถระบุได้หลายค่าโดยคั่นด้วยจุลภาค

## Is Real Time Second (`fancymenu_visibility_requirement_is_realtime_second`)

**Purpose:** ตรวจสอบว่าวินาทีตามเวลาจริงในโลกจริงตรงกับค่าที่กำหนดหรือไม่

**Value:** ต้องระบุ — วินาที (0-59) สามารถระบุได้หลายค่าโดยคั่นด้วยจุลภาค

## Is Real Time Week Day (`fancymenu_visibility_requirement_is_realtime_week_day`)

**Purpose:** ตรวจสอบว่าวันในสัปดาห์ตามเวลาจริงในโลกจริงตรงกับค่าที่กำหนดหรือไม่

**Value:** ต้องระบุ — วันในสัปดาห์เป็นตัวเลข (1-7 โดย 1 คือวันอาทิตย์) สามารถระบุได้หลายค่าโดยคั่นด้วยจุลภาค

## Is Real Time Year (`fancymenu_visibility_requirement_is_realtime_year`)

**Purpose:** ตรวจสอบว่าปีตามเวลาจริงในโลกจริงตรงกับค่าที่กำหนดหรือไม่

**Value:** ต้องระบุ — ปีแบบเต็ม (เช่น "2023") สามารถระบุได้หลายค่าโดยคั่นด้วยจุลภาค

## File/Folder Exists (`fancymenu_loading_requirement_file_exists`)

**Purpose:** ตรวจสอบว่ามีไฟล์หรือไดเรกทอรีอยู่หรือไม่

**Value:** ต้องระบุ — พาธที่อ้างอิงจากไดเรกทอรีเกมที่ใช้งานอยู่ หรือพาธที่ขึ้นต้นด้วย `.minecraft/` สำหรับไดเรกทอรี Minecraft ตามปกติ ทั้งไฟล์และไดเรกทอรีนับว่า "มีอยู่"

## Is OS Linux (`fancymenu_loading_requirement_is_os_linux`)

**Purpose:** ตรวจสอบว่าแพลตฟอร์มปัจจุบันไม่ใช่ Windows หรือ macOS โดยปกติจะหมายถึงสภาพแวดล้อม Linux

**Value:** ไม่ต้องระบุ

## Is OS macOS (`fancymenu_loading_requirement_is_os_macos`)

**Purpose:** ตรวจสอบว่าระบบปฏิบัติการเป็น macOS หรือไม่

**Value:** ไม่ต้องระบุ

## Is OS Windows (`fancymenu_loading_requirement_is_os_windows`)

**Purpose:** ตรวจสอบว่าระบบปฏิบัติการเป็น Windows หรือไม่

**Value:** ไม่ต้องระบุ

## Is Internet Connection Available (`is_internet_connection_available`)

**Purpose:** ตรวจสอบว่ามีการเชื่อมต่ออินเทอร์เน็ตที่ใช้งานได้อยู่หรือไม่

**Value:** ไม่ต้องระบุ

## Is Game Language (`fancymenu_loading_requirement_is_language`)

**Purpose:** ตรวจสอบว่าภาษาในเกมปัจจุบันตรงกับค่าที่กำหนดหรือไม่

**Value:** ต้องระบุ — รหัสภาษา (เช่น `en_us` สำหรับภาษาอังกฤษ)

## Is Mod Loaded (`fancymenu_loading_requirement_is_mod_loaded`)

**Purpose:** ตรวจสอบว่ามีม็อดที่ระบุถูกโหลดอยู่หรือไม่

**Value:** ต้องระบุ — Mod ID (เช่น `fancymenu`, `jei`) คุณยังสามารถตรวจหา OptiFine ได้ด้วย `optifine` รองรับ Mod ID หลายรายการที่คั่นด้วยจุลภาค โดยม็อดที่ระบุทั้งหมดต้องถูกโหลดอยู่

## Is MCEF Loaded (`is_mcef_loaded`)

**Purpose:** ตรวจสอบว่า MCEF (Minecraft Chromium Embedded Framework) ถูกติดตั้งและเริ่มต้นทำงานแล้วหรือไม่ MCEF จำเป็นสำหรับ [Browser element](./elements#browser) และ [ประเภทวิดีโอที่อาศัย MCEF ซึ่งเลิกใช้แล้ว](./video#requirements); ฟีเจอร์ [Video แบบดั้งเดิม](./video) ใช้ Watermedia

**Value:** ไม่ต้องระบุ

## Is Number (`fancymenu_visibility_requirement_is_number`)

**Purpose:** ให้การเปรียบเทียบตัวเลขขั้นสูงพร้อมโหมดการเปรียบเทียบที่หลากหลาย

**Value:** ต้องระบุ — รูปแบบซับซ้อน: `["mode":"comparison_mode","number":"value1","compare_with":"value2"]$` โดย `comparison_mode` สามารถเป็น `equals`, `bigger-than`, `smaller-than`, `bigger-than-or-equals`, หรือ `smaller-than-or-equals`

## Is Text (`fancymenu_visibility_requirement_is_text`)

**Purpose:** ให้การเปรียบเทียบข้อความขั้นสูงพร้อมโหมดการเปรียบเทียบที่หลากหลาย

**Value:** ต้องระบุ — รูปแบบซับซ้อน: `["mode":"comparison_mode","text":"text1","compare_with":"text2"]$` โดย `comparison_mode` สามารถเป็น `equals`, `contains`, `starts-with`, หรือ `ends-with`

## Is Server IP (`fancymenu_visibility_requirement_is_server_ip`)

**Purpose:** ตรวจสอบว่า IP เซิร์ฟเวอร์ปัจจุบันตรงกับค่าที่กำหนดหรือไม่

**Value:** ต้องระบุ — ที่อยู่ IP ของเซิร์ฟเวอร์ (มีหรือไม่มีพอร์ตก็ได้)

## Is Server Online (`fancymenu_loading_requirement_is_server_online`)

**Purpose:** ตรวจสอบว่าเซิร์ฟเวอร์ที่ระบุออนไลน์และเข้าถึงได้หรือไม่

**Value:** ต้องระบุ — ที่อยู่ IP ของเซิร์ฟเวอร์ (มีหรือไม่มีพอร์ตก็ได้)

## Is Resource Pack Enabled (`is_resource_pack_enabled`)

**Purpose:** ตรวจสอบว่า resource pack ที่ระบุถูกเลือก/เปิดใช้อยู่ในตอนนี้หรือไม่

**Value:** ต้องระบุ — ชื่อ resource pack หรือ pack ID (เช่น `Programmer Art` หรือ ID ของแพ็ก)

## Is Variable Value (FM Variable) (`fancymenu_visibility_requirement_is_variable_value`)

**Purpose:** ตรวจสอบว่า FancyMenu variable มีค่าตามที่กำหนดหรือไม่

**Value:** ต้องระบุ — รูปแบบ: "variable_name:expected_value"

## Only Once Per Session (`once_per_session`)

**Purpose:** แต่ละ instance ที่ตั้งค่าไว้จะคืนค่า true เพียงครั้งเดียวต่อหนึ่งเซสชันของเกม โดยแต่ละ instance จะถูกติดตามแยกกัน

**Value:** ไม่ต้องระบุ
