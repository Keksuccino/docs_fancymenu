---
title: ตำแหน่งจัดเก็บข้อมูล
description: ตำแหน่งที่ FancyMenu จัดเก็บเลย์เอาต์ ทรัพยากร การตั้งค่า และสถานะรันไทม์ถาวร
---

# ตำแหน่งจัดเก็บข้อมูล

`<game-directory>` หมายถึงโฟลเดอร์อินสแตนซ์ Minecraft ที่ใช้งานอยู่ ซึ่งอาจแตกต่างจาก `.minecraft`

โดยปกติไดเรกทอรีและไฟล์จะถูกสร้างขึ้นก็ต่อเมื่อมีการเริ่มต้นหรือใช้งานฟีเจอร์ที่เกี่ยวข้องแล้วเท่านั้น ให้ปิด Minecraft ก่อนแก้ไขไฟล์สถานะที่สร้างขึ้นด้วยตนเอง และควรสำรองข้อมูลไว้เสมอเมื่อย้ายหรือรีเซ็ตข้อมูล

# เลย์เอาต์ ทรัพยากร และการตั้งค่า

บางรายการเป็นการตั้งค่าหรือแอสเซ็ตที่ผู้ใช้สร้างขึ้น ส่วนบางรายการเป็นสถานะที่ FancyMenu อัปเดตขณะรันไทม์

| ระบบ / ฟีเจอร์ | ไฟล์หรือไดเรกทอรี |
| --- | --- |
| หน้าจอที่ปรับแต่งได้ | `<game-directory>/config/fancymenu/customizablemenus.txt` |
| [Custom GUIs](./custom-guis) และกฎการแทนที่หน้าจอ | `<game-directory>/config/fancymenu/custom_gui_screens.txt` |
| เลย์เอาต์ | `<game-directory>/config/fancymenu/customization/` |
| [แอสเซ็ตในเครื่อง](./resources#local-resources) | `<game-directory>/config/fancymenu/assets/` |
| [ไฟล์โลคัลไลเซชันแบบกำหนดเอง](./localization#fancymenu-custom-localization-files) | `<game-directory>/config/fancymenu/custom_locals/` |
| [พาโนรามา](./panoramas) | `<game-directory>/config/fancymenu/panoramas/` |
| [สไลด์โชว์](./slideshows) | `<game-directory>/config/fancymenu/slideshows/` |
| [ตัวแปรของ FancyMenu](./variables) | `<game-directory>/config/fancymenu/user_variables.db` |
| เมตาดาต้าตัวควบคุมของ [องค์ประกอบวิดีโอ](./elements#video) | `<game-directory>/config/fancymenu/video_element_controller_metas.json` |
| เมตาดาต้าตัวควบคุมของ [องค์ประกอบเสียง](./elements#audio) | `<game-directory>/config/fancymenu/audio_element_controller_metas.json` |
| เซิร์ฟเวอร์ลิสเนอร์ของ [FM Data](./fm-data) | `<game-directory>/config/fancymenu/fmdata_server_listeners.json` |
| ข้อมูลต้อนรับของ [FM Data](./fm-data) | `<game-directory>/config/fancymenu/fmdata_welcome_data.json` |
| อินสแตนซ์ของ [Listener](./listeners) และสคริปต์แอ็กชัน | `<game-directory>/config/fancymenu/listener_instances.txt` |
| [Schedulers](./schedulers) | `<game-directory>/config/fancymenu/scheduler_instances.txt` |

`customizablemenus.txt` ถูกจัดการโดยสวิตช์ **Current Screen Customization** และเก็บตัวระบุคลาสของหน้าจอที่เป็นรูปธรรม อย่าเพิ่มตัวระบุ [Universal Layout](./universal-layouts) ลงไป เพราะ FancyMenu จะไม่สนใจเมื่อโหลดไฟล์นี้

บนเซิร์ฟเวอร์แบบ dedicated ไฟล์ FM Data ทั้งสองไฟล์จะอ้างอิงแบบสัมพันธ์กับโฟลเดอร์รากเกมของเซิร์ฟเวอร์นั้น ส่วนการตั้งค่าและทรัพยากรอื่น ๆ ที่เป็นของฝั่งไคลเอนต์จะอยู่ในอินสแตนซ์ของผู้เล่นแต่ละคน

# สถานะรันไทม์ถาวร

FancyMenu จะเก็บสถานะเพิ่มเติมที่สร้างขึ้นต่ออินสแตนซ์ไว้ภายนอก `config/fancymenu/` ให้รวมพาธเหล่านี้ในการสำรองข้อมูลเฉพาะเมื่อคุณต้องการเก็บสถานะของผู้ใช้/รันไทม์ที่เกี่ยวข้องไว้เท่านั้น; สิ่งเหล่านี้ไม่ใช่นิยามเลย์เอาต์หรือแอสเซ็ตต้นฉบับ

| ระบบ / ฟีเจอร์ | ไฟล์หรือไดเรกทอรี |
| --- | --- |
| สถานะ [Checkbox](./elements#checkbox) ที่ไม่ใช่ตัวแปร | `<game-directory>/checkbox_states.json` |
| ตำแหน่ง/เมตาดาต้าขององค์ประกอบ [Dragger](./dragger) | `<game-directory>/fancymenu_data/dragger_metas.json` |
| สถานะโลกล่าสุด | `<game-directory>/fancymenu_data/last_world.fmdata` |
| สถานะของ [Seamless World Loading](./seamless-world-loading) | `<game-directory>/fancymenu_data/seamless_world_loading/` |
| การบันทึกข้อมูลสัตว์เลี้ยง Buddy และการเลเวลอัป | `<game-directory>/fancymenu_data/buddy/` |
| ตำแหน่งและการแสดงผลของวิดเจ็ตในตัวแก้ไขเลย์เอาต์ | `<game-directory>/config/fancymenu/layout_editor/widgets/` |
| เครื่องหมายเริ่มต้นการตั้งค่าขนาด GUI ค่าเริ่มต้น | `<game-directory>/fancymenu_data/default_scale_set.fm` |

Buddy จะเก็บสถานะสัตว์เลี้ยงและสถานะการเลเวลอัป/ความสำเร็จไว้ในไฟล์ JSON แยกกันภายในไดเรกทอรีของมัน แต่ละอินสแตนซ์โอเวอร์เลย์ของ Buddy จะใช้คู่ไฟล์ของตัวเอง

ไฟล์วิดเจ็ตของตัวแก้ไขเลย์เอาต์จะเก็บตำแหน่ง ขนาด การแสดงผล สถานะการขยาย และด้านที่ใช้สแน็ปของวิดเจ็ตแต่ละตัว การลบ `default_scale_set.fm` จะทำให้ FancyMenu ถือว่าขนาด GUI ค่าเริ่มต้นที่ตั้งค่าไว้ยังไม่ได้ถูกใช้งานในการเปิดครั้งถัดไป
