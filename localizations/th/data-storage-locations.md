---
title: ตำแหน่งจัดเก็บข้อมูล
description: >-
  FancyMenu บันทึกเลย์เอาต์ แอสเซ็ต การตั้งค่า และข้อมูลอื่น ๆ ไว้ที่ใด
  รวมถึงไฟล์ใดบ้างที่เป็นของโปรไฟล์
sourceBlobSha: 30dd81ed90e08184e3063892870e3325d7d7c5cb
---

# ตำแหน่งจัดเก็บข้อมูล

FancyMenu บันทึกทุกอย่างไว้ในโฟลเดอร์สองแห่งภายในไดเรกทอรีเกมของคุณ ซึ่งก็คือโฟลเดอร์อินสแตนซ์ของ Launcher ที่คุณใช้ ซึ่งอาจเป็นคนละโฟลเดอร์กับ `.minecraft`

- `config/fancymenu/` เก็บการตั้งค่าของคุณ ได้แก่ เลย์เอาต์ แอสเซ็ต ตัวแปร การตั้งค่า และอื่น ๆ โฟลเดอร์นี้คือ[โปรไฟล์](/profiles)ที่โหลดอยู่ จึงมีการรวมโฟลเดอร์นี้ไว้ในม็อดแพ็ก
- `fancymenu_data/` เก็บข้อมูลของอินสแตนซ์เกมนี้ เช่น ตำแหน่งของ Dragger และไฟล์ดาวน์โหลด ข้อมูลในโฟลเดอร์นี้จะเหมือนกันในทุกโปรไฟล์

**แถบเมนู -> เครื่องมือ -> เปิดไดเรกทอรี FancyMenu** จะเปิด `config/fancymenu/`

ไฟล์และโฟลเดอร์ส่วนใหญ่จะปรากฏขึ้นเมื่อคุณใช้ฟีเจอร์ที่เกี่ยวข้องเท่านั้น ปิดเกมก่อนแก้ไขหรือลบไฟล์ในโฟลเดอร์เหล่านี้

> [!TIP]
> หากต้องการแชร์โฟลเดอร์เหล่านี้ระหว่างอินสแตนซ์ คุณสามารถย้ายโฟลเดอร์ไปไว้ที่อื่น แล้วสร้างลิงก์สัญลักษณ์ (หรือ junction บน Windows) ไว้ในตำแหน่งเดิมได้

# การตั้งค่าของคุณ

ทุกอย่างใน `<game-directory>/config/fancymenu/` เป็นของ[โปรไฟล์](/profiles)ที่โหลดอยู่

| รายการ | ตำแหน่ง |
| --- | --- |
| เลย์เอาต์ในรูปแบบไฟล์ `.txt` รวมถึงไฟล์ในโฟลเดอร์ย่อย | `customization/` |
| [แอสเซ็ตในเครื่อง](/resources#local-resources) เช่น รูปภาพและเสียง | `assets/` |
| การตั้งค่าของ FancyMenu | `options.txt` |
| หน้าจอที่เปิดใช้ **การปรับแต่งหน้าจอปัจจุบัน** | `customizablemenus.txt` |
| [GUI แบบกำหนดเอง](/custom-guis) และหน้าจอที่ถูกแทนที่ | `custom_gui_screens.txt` |
| [ตัวแปร](/variables) | `user_variables.db` |
| [Listener](/listeners) | `listener_instances.txt` |
| [Scheduler](/schedulers) | `scheduler_instances.txt` |
| [พาโนรามา](/panoramas) | `panoramas/` |
| [สไลด์โชว์](/slideshows) | `slideshows/` |
| [ไฟล์ภาษาในเครื่องแบบกำหนดเอง](/localization#fancymenu-custom-localization-files) | `custom_locals/` |
| ธีมของ UI ในตัว FancyMenu (**แถบเมนู -> การปรับแต่ง -> การตั้งค่า -> UI ของ FancyMenu -> ธีม UI**) | `ui_themes/` |
| สถานะของ[องค์ประกอบ Checkbox](/elements#checkbox) ที่ไม่ได้ใช้ตัวแปร | `checkbox_states.json` |
| ระดับเสียงและสถานะหยุดชั่วคราวที่แอ็กชันกำหนดให้กับ[องค์ประกอบวิดีโอ](/video) | `video_element_controller_metas.json` |
| ระดับเสียงที่แอ็กชันกำหนดให้กับ[องค์ประกอบเสียง](/elements#audio) | `audio_element_controller_metas.json` |
| สถานะเปิดและปิดที่แอ็กชันกำหนดให้กับ [Element Animator](/element-animator) | `animation_controller_states.json` |
| หน้าจอที่เปิดใช้ **เปิดเผยเนื้อหาพื้นที่เลื่อนของหน้าจอปัจจุบัน** (ดู[การปรับแต่งหน้าจอที่เลื่อนได้](/customizing-scrollable-screens)) | `normalized_scroll_screens.json` |
| Listener ของเซิร์ฟเวอร์ [FM Data](/fm-data) | `fmdata_server_listeners.json` |
| ข้อมูลต้อนรับของ [FM Data](/fm-data) | `fmdata_welcome_data.json` |
| ตำแหน่ง ขนาด และการแสดงผลของวิดเจ็ตในตัวแก้ไขเลย์เอาต์ | `layout_editor/widgets/` |
| ชื่อ ไอคอน และรายละเอียดของโปรไฟล์ที่โหลดอยู่ | `profile.json` และ `profile_icon.png` |
| [โปรไฟล์](/profiles#where-profiles-are-stored) อื่น ๆ ทั้งหมด | `profiles/` |
| รายการอัปเดตไฟล์เก่าที่ FancyMenu ดำเนินการไปแล้ว | `legacy_checklist.txt` |

`customizablemenus.txt` จะแสดงรายการหน้าจอโดยใช้ชื่อคลาส Java ส่วน[ตัวระบุหน้าจอ](/screen-identifiers)แบบสั้น เช่น `title_screen` จะไม่อยู่ในรายการนี้

บนเซิร์ฟเวอร์เฉพาะ FancyMenu จะใช้เฉพาะไฟล์ [FM Data](/fm-data) สองไฟล์ในโฟลเดอร์ `config/fancymenu/` ของเซิร์ฟเวอร์เท่านั้น

# ข้อมูลอินสแตนซ์

ทุกอย่างใน `<game-directory>/fancymenu_data/` ไม่ได้เป็นส่วนหนึ่งของโปรไฟล์ จึงยังคงอยู่เมื่อคุณสลับโปรไฟล์

| รายการ | ตำแหน่ง |
| --- | --- |
| ตำแหน่งของ[องค์ประกอบ Dragger](/dragger) | `dragger_metas.json` |
| โลกหรือเซิร์ฟเวอร์ล่าสุด สำหรับแอ็กชัน **เข้าสู่/เข้าร่วมโลก/เซิร์ฟเวอร์ล่าสุด** และตัวแทนข้อความ **โลกหรือเซิร์ฟเวอร์ล่าสุด** | `last_world.fmdata` |
| ภาพหน้าจอของ[การโหลดโลกอย่างไร้รอยต่อ](/seamless-world-loading) | `seamless_world_loading/` |
| ไฟล์บันทึกของ [Buddy](/decoration-overlays#buddy) โดยมีสองไฟล์ต่อ Buddy overlay หนึ่งรายการ | `buddy/` |
| ไฟล์ของ[ส่งออกสำหรับ AI](/export-for-ai) | `ai_exports/` |
| แอ็กชันโปรดของคุณในตัวเลือกแอ็กชัน | `action_favorites.json` |
| ระดับเสียงของตัวอย่างเสียงและวิดีโอในตัวเลือกไฟล์ | `browser_audio_settings.json` และ `browser_video_settings.json` |
| เฟรมที่[พื้นหลังวิดีโอ](/video)แสดงขณะหยุดชั่วคราว | `video_thumbnails/` |
| FFmpeg ซึ่ง FancyMenu ดาวน์โหลดให้กับ[ตัวสร้าง AFMA](/animations#fma-and-afma) | `ffmpeg_cache/` |
| หมายเหตุที่ระบุว่า FancyMenu ตั้งค่า[**สเกล GUI เริ่มต้น**](/global-customizations)แล้ว | `default_scale_set.fm` |
| ไฟล์ชั่วคราว ซึ่งจะถูกลบทุกครั้งที่เริ่มเกม | `fancymenu_temp/` |

- FancyMenu จะตั้งค่า **สเกล GUI เริ่มต้น** เพียงครั้งเดียว ลบ `default_scale_set.fm` เพื่อให้ตั้งค่าสเกลอีกครั้งเมื่อเริ่มเกมครั้งถัดไป
- ภาพหน้าจอจากการโหลดโลกอย่างไร้รอยต่อจะแสดงทุกอย่างที่อยู่บนหน้าจอในโลกนั้น หากไม่ต้องการเก็บภาพเหล่านี้ไว้ ให้ลบเมื่อปิดเกมแล้ว

# ไฟล์จากเวอร์ชันเก่า

FancyMenu เวอร์ชันเก่าบางรุ่นบันทึกไฟล์บางส่วนไว้ในตำแหน่งอื่น FancyMenu จะย้ายไฟล์เหล่านั้นมาไว้ในตำแหน่งที่ถูกต้องเมื่อเริ่มเกมครั้งถัดไป:

- ย้าย `checkbox_states.json` และ `normalized_scroll_screens.json` จากไดเรกทอรีเกมไปยัง `config/fancymenu/`
- ย้าย `dragger_metas.json` จาก `config/fancymenu/` ไปยัง `fancymenu_data/`
