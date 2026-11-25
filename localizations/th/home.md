---
title: เริ่มต้นใช้งาน
description: >-
  เริ่มต้นใช้งาน FancyMenu ทำความรู้จักแถบเมนู สร้างเลย์เอาต์แรกตั้งแต่ต้นจนจบ
  และดูว่าควรไปต่อที่ไหน
sourceBlobSha: 0a9f8343e6964d75860fb6143e9b6fdecb6cf0ea
---

# เริ่มต้นใช้งาน

FancyMenu ให้คุณเปลี่ยนเมนูทุกหน้าใน Minecraft ได้ ไม่ว่าจะเป็นหน้าจอชื่อเกม เมนูหยุดเกมชั่วคราว หรือเมนูของม็อดอื่น ๆ คุณสามารถกำหนดพื้นหลัง โลโก้ ปุ่ม ข้อความ เสียง และภาพเคลื่อนไหวได้ตามต้องการ ย้ายหรือซ่อนสิ่งที่มีอยู่ เปลี่ยนการทำงานของปุ่ม หรือสร้างเมนูใหม่ทั้งหน้า ทุกอย่างทำได้ในเกมโดยไม่ต้องเขียนโค้ด

<img width="800" alt="หน้าจอชื่อเกมของม็อดแพ็กชื่อ Wildwood ที่สร้างด้วย FancyMenu: หุบเขาพิกเซลอาร์ตยามพลบค่ำพร้อมกระท่อม ทะเลสาบ และดวงอาทิตย์ที่กำลังลับขอบฟ้า โดยเลเยอร์จะขยับตามเมาส์ มีโลโก้สีทอง ปุ่มไม้ที่เรืองแสงเมื่อเลื่อนเมาส์ไปชี้ และหิ่งห้อย" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/getting_started_hero.gif?raw=true">

หน้านี้จะแนะนำพื้นฐานทีละขั้น ระหว่างทางคุณจะได้สร้างหน้าจอชื่อเกมเวอร์ชันที่เรียบง่ายขึ้น ส่วน [วิธีสร้างตัวอย่างนี้](#how-the-example-is-made) จะอธิบายว่าหน้าจอฉบับเต็มเพิ่มอะไรเข้ามาบ้าง

> [!TIP]
> ดาวน์โหลดหน้าจอชื่อเกมนี้ไปใช้ในเกมของคุณได้ที่ [wildwood_title_screen.fmp](https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/wildwood_title_screen.fmp?raw=true) จากนั้น [นำเข้า](/profiles#importing) และ [โหลด](/profiles#loading-a-profile) ใน **menu bar -> Customization -> Profiles** ใช้ได้ฟรีทุกกรณี ไม่ว่าจะลองใช้ FancyMenu เรียนรู้จากตัวอย่าง หรือนำไปใช้กับม็อดแพ็ก จะดัดแปลงหรือไม่ก็ได้ และไม่จำเป็นต้องให้เครดิต

# แถบเมนู

แถบเมนูที่ด้านบนของทุกเมนูเป็นที่รวมฟีเจอร์ทั้งหมดของ FancyMenu

<img width="800" alt="แถบเมนูที่ด้านบนของหน้าจอชื่อเกม โดยเปิดเมนู Customization อยู่" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/getting_started_menu_bar.png?raw=true">

- **Customization**: เลย์เอาต์ของเมนูที่คุณกำลังใช้งาน และการตั้งค่าทั้งหมดของชุดปรับแต่ง เช่น [Global Customizations](/global-customizations), [Custom GUIs](/custom-guis), [Variables](/variables), [Listeners](/listeners), [Schedulers](/schedulers), [Profiles](/profiles) และการตั้งค่าของ FancyMenu
- **Tools**: เครื่องมือช่วยต่าง ๆ เช่น [Dummy Screen Instances](/dummy-screen-instances), [AFMA Creator](/animations#fma-and-afma), **Browse Game Resources** และ **Open FancyMenu Directory** ซึ่งเปิดโฟลเดอร์ชุดปรับแต่งของคุณ (ดู [ตำแหน่งจัดเก็บข้อมูล](/data-storage-locations))
- **Help**: เอกสารนี้ เซิร์ฟเวอร์ Discord **Report a Bug** และ [Export for AI](/export-for-ai)
- ไอคอนประตูทางขวาสุดใช้ปิดเมนูที่เปิดอยู่ สำหรับเมนูที่ไม่มีทางออก
- ลูกศรคู่ทางขวาสุดใช้ย่อแถบเมนูให้เหลือปุ่มเล็ก ๆ และขยายกลับมา

ผู้เล่นม็อดแพ็กของคุณไม่จำเป็นต้องใช้แถบเมนู ดูวิธีปิดได้ที่ [ม็อดแพ็ก](/modpacks#disabling-the-menu-bar-and-hotkeys)

## คีย์ลัดแถบเมนู

คีย์ลัดเหล่านี้ใช้ได้ในทุกเมนู ยกเว้นในตัวแก้ไขเลย์เอาต์และขณะที่เปิด Modpack Mode อยู่ บน macOS ให้ใช้ `Cmd + Option` แทน `Ctrl + Alt`

| คีย์ลัด | การทำงาน |
|---|---|
| `Ctrl + Alt + C` | แสดงหรือซ่อนแถบเมนู หากแถบเมนูหายไปกะทันหัน ให้กดคีย์ลัดนี้เพื่อเรียกกลับมา |
| `Ctrl + Alt + R` | โหลด FancyMenu ใหม่ เหมือนกับ **menu bar -> Customization -> Reload FancyMenu** |
| `Ctrl + Alt + D` | แสดงหรือซ่อน **Debug Overlay** ซึ่งแสดง [ตัวระบุ](/screen-identifiers) ของเมนูและข้อมูลอื่น ๆ |
| `Ctrl + Alt + L` | เปิด [ตัวแก้ไขเลย์เอาต์](/layout-editor) พร้อมเลย์เอาต์ที่คุณแก้ไขล่าสุด |

# สร้างเลย์เอาต์แรก

เลย์เอาต์เก็บการเปลี่ยนแปลงที่คุณทำกับเมนู เช่น พื้นหลัง องค์ประกอบที่เพิ่มเข้ามา และสิ่งที่คุณเปลี่ยนในปุ่มกับข้อความที่มีอยู่แล้ว เมนูหนึ่งสามารถมีหลายเลย์เอาต์ และคุณสามารถเปิดหรือปิดแต่ละเลย์เอาต์ได้

## สร้างเลย์เอาต์

<img width="800" alt="เปิด Customization จากแถบเมนูบนหน้าจอชื่อเกม เปิด Current Screen Customization เปิด Customization อีกครั้งแล้วคลิก Layouts, New, For Current Screen เพื่อเปิดตัวแก้ไขเลย์เอาต์" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/getting_started_new_layout.gif?raw=true">

1. เปิดเมนูที่ต้องการเปลี่ยน เช่น หน้าจอชื่อเกม
2. คลิก **menu bar -> Customization -> Current Screen Customization** จนแสดง **Enabled** FancyMenu จะเปลี่ยนเฉพาะเมนูที่เปิดใช้งานตัวเลือกนี้
3. คลิก **menu bar -> Customization -> Layouts -> New -> For Current Screen**

ตัวแก้ไขเลย์เอาต์จะเปิดขึ้น โดยจะแสดงเมนูในแบบที่ผู้เล่นเห็น คุณจึงเห็นการเปลี่ยนแปลงได้ทันที ดูรายละเอียดเพิ่มเติมเกี่ยวกับตัวแก้ไข เช่น การย้าย ปรับขนาด และคัดลอกองค์ประกอบ ได้ที่ [ตัวแก้ไขเลย์เอาต์](/layout-editor)

ตัวเลือก **For All Screens [Universal]** จะสร้าง [เลย์เอาต์สากล](/universal-layouts) ซึ่งจะแสดงในทุกเมนูแทน

## ตั้งค่าพื้นหลัง

ก่อนอื่น ให้วางรูปภาพไว้ในโฟลเดอร์ `config/fancymenu/assets` ของเกม คลิก **menu bar -> Tools -> Open FancyMenu Directory** เพื่อเปิด `config/fancymenu`

<img width="800" alt="คลิกขวาที่พื้นหลังของตัวแก้ไข เปิด Menu Backgrounds, Image เปิด Show Background แล้วคลิก Choose Image เปลี่ยน Source Type เป็น Local และเลือก background.png จากโฟลเดอร์ wildwood จากนั้นหุบเขาจะปรากฏอยู่ด้านหลังปุ่ม" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/getting_started_background.gif?raw=true">

1. คลิกขวาที่พื้นหลังของตัวแก้ไข แล้วเปิด **Menu Backgrounds -> Image**
2. คลิก **Show Background** จนแสดง **Enabled**
3. คลิก **Choose Image** ตั้งค่า **Source Type** เป็น **Local** แล้วคลิก **Choose Local Resource File**
4. คลิกรูปภาพที่ต้องการ แล้วคลิก **OK** ดับเบิลคลิกเพื่อเปิดโฟลเดอร์

พื้นหลังยังสามารถเป็นภาพพาโนรามา สไลด์โชว์ วิดีโอ สี และอื่น ๆ ได้ ดูรายละเอียดที่ [พื้นหลังเมนู](/menu-backgrounds)

## เพิ่มโลโก้

<img width="800" alt="ลบโลโก้ Minecraft และข้อความ Splash แล้วเพิ่มองค์ประกอบ Image ผ่าน Element, New, Image จากนั้นเลือก logo.png เป็น Image Source ทำให้โลโก้ถูกบีบให้เป็นรูปสี่เหลี่ยมจัตุรัส" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/getting_started_logo_add.gif?raw=true">

1. คลิกโลโก้ Minecraft แล้วกด `Delete` ทำแบบเดียวกันกับข้อความสีเหลือง
2. ที่แถบเมนูของตัวแก้ไข คลิก **Element -> New -> Image**
3. คลิกขวาที่องค์ประกอบใหม่ คลิก **Image Source** แล้วเลือกรูปโลโก้เหมือนกับตอนเลือกพื้นหลัง

องค์ประกอบวานิลลาที่ลบไปจะถูกซ่อนไว้เท่านั้น คลิก **Element -> Deleted Vanilla Elements** เพื่อนำกลับมา

<img width="800" alt="คลิก Restore Aspect Ratio ในเมนูคลิกขวาของโลโก้ เพื่อคืนความกว้างตามจริง จากนั้นกด Esc เพื่อปิดเมนู แล้วลากโลโก้ Wildwood ไปไว้เหนือปุ่ม" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/getting_started_logo_place.gif?raw=true">

4. คลิกขวาที่โลโก้อีกครั้ง แล้วคลิก **Restore Aspect Ratio** เพื่อไม่ให้ภาพถูกบีบ กด `Esc` เพื่อปิดเมนู
5. ลากโลโก้ไปยังตำแหน่งที่ต้องการ

คุณยังเพิ่มสิ่งต่าง ๆ ได้อีกมาก เช่น ปุ่ม ข้อความ วิดีโอ และผู้เล่น ดูรายละเอียดที่ [องค์ประกอบ](/elements)

## เปลี่ยนปุ่ม

<img width="800" alt="คลิกปุ่ม Singleplayer แล้วกด Ctrl ค้างไว้เพื่อคลิกปุ่มอีกสี่ปุ่ม จากนั้นใช้ Button Textures, Set, Normal Background กำหนดพื้นผิวไม้ให้ปุ่มทั้งห้าพร้อมกัน" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/getting_started_buttons_normal.gif?raw=true">

1. คลิกปุ่มแรก จากนั้นกด `Ctrl` ค้างไว้ (`Cmd` บน macOS) แล้วคลิกปุ่มอื่น ๆ เพื่อเลือกปุ่มทั้งหมด คลิกขวาที่ปุ่มใดปุ่มหนึ่งเพื่อเปลี่ยนปุ่มที่เลือกทั้งหมดพร้อมกัน
2. คลิกขวาที่ปุ่มใดปุ่มหนึ่ง คลิก **Button Textures -> Set -> Normal Background** แล้วเลือกพื้นผิวที่ต้องการเหมือนกับตอนเลือกพื้นหลัง

<img width="800" alt="กำหนดพื้นผิวเรืองแสงด้วย Button Textures, Set, Hover Background เปิด Nine-Slice Custom Background เพื่อให้ขอบไม้คมชัด แล้วเลื่อนเมาส์ไปชี้ปุ่ม Multiplayer ซึ่งจะเรืองแสงขึ้นมา" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/getting_started_buttons_hover.gif?raw=true">

3. ทำแบบเดียวกันกับ **Hover Background** ซึ่งเป็นพื้นผิวที่แสดงเมื่อเลื่อนเมาส์ไปชี้ปุ่ม
4. คลิก **Button Textures -> Nine-Slice Custom Background** จนแสดง **Enabled** วิธีนี้ช่วยให้ขอบพื้นผิวคมชัดบนปุ่มที่มีความกว้างทุกขนาด ดูรายละเอียดที่ [Nine-Slicing](/nine-slicing-and-tiling)

เมนูคลิกขวาขององค์ประกอบหลายรายการจะแสดงเฉพาะการตั้งค่าที่องค์ประกอบเหล่านั้นมีร่วมกัน ดังนั้นให้เลือกเฉพาะปุ่ม คลิกขวาที่ปุ่มเดียวเพื่อดูการตั้งค่าทั้งหมด เช่น ป้ายชื่อ เสียง การทำงานเมื่อคลิก ([Action Scripts](/action-scripts)) และเงื่อนไขการแสดง ([Element Visibility](/element-visibility)) ดูรายละเอียดที่ [องค์ประกอบวานิลลา/ม็อด](/vanilla-elements)

## บันทึก

<img width="800" alt="กด Ctrl + S คลิก Save ในหน้าต่าง Save File ปิดตัวแก้ไขด้วยปุ่ม X แล้วแสดงหน้าจอชื่อเกมที่เสร็จสมบูรณ์ พร้อมหุบเขา โลโก้ Wildwood และปุ่มไม้" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/getting_started_save.gif?raw=true">

1. กด `Ctrl + S` (`Cmd + S` บน macOS) หรือคลิก **Layout -> Save**
2. เมื่อบันทึกครั้งแรก FancyMenu จะถามชื่อไฟล์ คุณจะใช้ชื่อเดิมหรือพิมพ์ชื่อใหม่ก็ได้ จากนั้นคลิก **Save**
3. ปิดตัวแก้ไขโดยคลิก X ทางขวาของแถบเมนู

เมนูจะแสดงเลย์เอาต์ของคุณทันที หากต้องการเปลี่ยนในภายหลัง ให้วางเมาส์เหนือเลย์เอาต์ใน **menu bar -> Customization -> Layouts** แล้วคลิก **Edit Layout** หรือกด `Ctrl + Alt + L`

# วิธีสร้างตัวอย่างนี้

หน้าจอชื่อเกมที่ด้านบนของหน้านี้เพิ่มสิ่งต่าง ๆ จากหน้าจอที่คุณสร้างไว้ดังนี้

- ท้องฟ้า เนินเขา และต้นไม้เป็นรูปภาพสามภาพที่ขยับตามเมาส์ โดยต้นไม้จะขยับมากที่สุด ดูรายละเอียดที่ [เอฟเฟกต์พารัลแลกซ์](/parallax)
- เนินเขาและต้นไม้เป็นองค์ประกอบ Image ที่มีขนาดเท่าหน้าจอ จึงอยู่หลังปุ่มและข้อความ โดยเปิด **Custom Elements Behind Vanilla** ในเมนูคลิกขวาของพื้นหลังตัวแก้ไข
- หิ่งห้อยสร้างด้วย [Decoration Overlay](/decoration-overlays#fireflies)
- ขนาดของเนินเขา ต้นไม้ และโลโก้จะปรับตามขนาดหน้าจอด้วย [Advanced Positioning & Sizing](/advanced-positioning-sizing) และตัวแทนค่า ทำให้เมนูพอดีกับหน้าต่างทุกขนาด โลโก้จะเล็กลงเมื่อหน้าจอเตี้ย เพื่อไม่ให้บังปุ่ม

หากต้องการดูองค์ประกอบทั้งหมดนี้ในตัวแก้ไขเลย์เอาต์ ให้โหลด [โปรไฟล์ตัวอย่าง](#getting-started) แล้วแก้ไขเลย์เอาต์

# อ่านต่อที่ไหนดี

**ทำให้เมนูสวยงาม**

- [องค์ประกอบ](/elements): ทุกสิ่งที่เพิ่มลงในเมนูได้
- [การจัดตำแหน่งองค์ประกอบ](/positioning-elements): จัดองค์ประกอบให้อยู่ในตำแหน่งเดิมบนหน้าต่างทุกขนาด
- [พื้นหลังเมนู](/menu-backgrounds), [ภาพเคลื่อนไหว](/animations), [วิดีโอ](/video), [Decoration Overlays](/decoration-overlays) และ [เพลงพื้นหลัง](/background-music)

**กำหนดการทำงาน**

- [Action Scripts](/action-scripts): กำหนดการทำงานของปุ่มและองค์ประกอบอื่น ๆ
- [การแสดงองค์ประกอบ](/element-visibility) และ [เงื่อนไข](/conditions): แสดงสิ่งต่าง ๆ เฉพาะบางเวลา
- [ตัวแทนค่า](/placeholders): แสดงข้อมูลสดในข้อความ เช่น ชื่อผู้เล่น
- [Variables](/variables), [Listeners](/listeners) และ [Schedulers](/schedulers): จดจำข้อมูล ตอบสนองต่อเกม และทำงานตามเวลาที่กำหนด

**สร้างเพิ่มเติม**

- [Custom GUIs](/custom-guis): สร้างเมนูใหม่ทั้งหน้า
- [เลย์เอาต์สากล](/universal-layouts): ปรับเปลี่ยนเมนูทุกหน้า
- [Global Customizations](/global-customizations): ปรับแต่งทั้งเกม เช่น ชื่อหน้าต่าง
- [หน้าจอโหลด](/loading-screen) และ [บทนำเกม](/game-intro)

**แบ่งปันผลงาน**

- [ม็อดแพ็ก](/modpacks): นำชุดปรับแต่งของคุณไปใส่ในม็อดแพ็ก
- [โปรไฟล์](/profiles): สลับระหว่างชุดปรับแต่งและส่งออกชุดเหล่านั้น

# ขอความช่วยเหลือ

- ดูคำตอบของคำถามที่พบบ่อยได้ที่ [FAQ](/faq)
- คลิก **menu bar -> Help -> Join the Discord** เพื่อเข้าร่วมเซิร์ฟเวอร์ Discord ของ FancyMenu
- [Export for AI](/export-for-ai) จะแปลงชุดปรับแต่งของคุณเป็นข้อความสำหรับใช้ในแชต AI เช่น บอตช่วยเหลือในเซิร์ฟเวอร์ Discord
- คลิก **menu bar -> Help -> Report a Bug** หากมีบางอย่างทำงานไม่ถูกต้อง

# สำหรับนักพัฒนา

หากต้องการสร้างส่วนเสริมสำหรับ FancyMenu หรือนำไปใช้ในม็อดของคุณ ดูได้ที่ [เอกสารสำหรับนักพัฒนา](https://github.com/Keksuccino/FancyMenu-Dev-Docs/wiki)
