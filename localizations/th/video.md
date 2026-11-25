---
title: วิดีโอ (MP4)
description: สิ่งที่ควรรู้เกี่ยวกับการใช้วิดีโอใน FancyMenu
sourceBlobSha: bd34c5c21a6c08d6b66a7b2acdaf9bd12739732f
---
# วิดีโอ

FancyMenu รองรับการเล่นวิดีโอ MP4 ในรูปแบบ [องค์ประกอบ](/elements#video), [พื้นหลังเมนู](/menu-backgrounds#video) และเนื้อหา [Game Intro](/game-intro)

องค์ประกอบ [**Video**](/elements#video) และพื้นหลังเมนู **Video** แบบเนทีฟใช้ Watermedia V3 ส่วนประเภท **Video [Rinku]** แบบเก่าถูกเลิกใช้แล้ว และควรเหลือไว้เฉพาะในเลย์เอาต์ที่ยังจำเป็นต้องใช้เท่านั้น

นอกจากนี้ยังมี [การกระทำ](/action-scripts) ต่อไปนี้สำหรับควบคุมพื้นหลังวิดีโอและองค์ประกอบวิดีโอ:

- [**Set Video Element Volume**](/action-scripts#set-video-element-volume) กำหนดระดับเสียงขององค์ประกอบ Video
- [**Set Video Element Play Time**](/action-scripts#set-video-element-play-time) เลื่อนไปยังเวลาในหน่วยมิลลิวินาทีขององค์ประกอบ Video
- [**Toggle Video Element Paused State**](/action-scripts#toggle-video-element-paused-state) สลับสถานะหยุดชั่วคราวขององค์ประกอบ Video
- [**Set Video Background Volume**](/action-scripts#set-video-background-volume) กำหนดระดับเสียงของพื้นหลังเมนู Video
- [**Set Video Background Play Time**](/action-scripts#set-video-background-play-time) เลื่อนไปยังเวลาในหน่วยมิลลิวินาทีของพื้นหลังเมนู Video
- [**Toggle Video Background Paused State**](/action-scripts#toggle-video-background-paused-state) สลับสถานะหยุดชั่วคราวของพื้นหลังเมนู Video

และยังมี [ตัวแทนค่า](/placeholders) ต่อไปนี้สำหรับดูข้อมูลเกี่ยวกับพื้นหลังวิดีโอและองค์ประกอบวิดีโอ:

- [**Video Element Volume**](/placeholders#video-element-volume) แสดงระดับเสียงขององค์ประกอบ Video
- [**Video Element Duration**](/placeholders#video-element-duration) แสดงระยะเวลาขององค์ประกอบ Video
- [**Video Element Play Time**](/placeholders#video-element-play-time) แสดงความคืบหน้าปัจจุบันขององค์ประกอบ Video
- [**Video Element Paused State**](/placeholders#video-element-paused-state) แสดงว่าองค์ประกอบ Video หยุดชั่วคราวอยู่หรือไม่
- [**Video Background Volume**](/placeholders#video-background-volume) แสดงระดับเสียงของพื้นหลังเมนู Video
- [**Video Background Duration**](/placeholders#video-background-duration) แสดงระยะเวลาของพื้นหลังเมนู Video
- [**Video Background Play Time**](/placeholders#video-background-play-time) แสดงความคืบหน้าปัจจุบันของพื้นหลังเมนู Video
- [**Video Background Paused State**](/placeholders#video-background-paused-state) แสดงว่าพื้นหลังเมนู Video หยุดชั่วคราวอยู่หรือไม่

ตัวแทนค่าระยะเวลาและเวลาเล่นจะแสดงผลเป็น `MM:SS` ตามค่าเริ่มต้น หากต้องการเวลาในหน่วยมิลลิวินาที ให้ตั้งค่า `output_as_timestamp` เป็น `true` ส่วนตัวแทนค่าเวลาเล่นยังสามารถใช้ `show_percentage` เพื่อแสดงความคืบหน้าเป็นค่า 0–100 ได้

ค่าระดับเสียงและสถานะหยุดชั่วคราวเป็นข้อมูลเมตาของตัวควบคุมที่เชื่อมโยงกับตัวระบุ ส่วนค่าระยะเวลาและเวลาเล่นต้องใช้องค์ประกอบ Video หรือพื้นหลัง Video ที่ตรงกัน ซึ่งกำลังทำงานและพร้อมใช้งานบนหน้าจอปัจจุบัน

[ตัวรับฟัง **Video Playback Status Changed**](/listeners#video-playback-status-changed) สามารถตอบสนองต่อสถานะ `PLAYING`, `PAUSED`, `STOPPED` และ `FINISHED` ได้

## ข้อกำหนด

หากต้องการใช้องค์ประกอบ Video แบบเนทีฟและประเภทพื้นหลังเมนู คุณต้องติดตั้ง:

- **Watermedia V3**
- **Watermedia Binaries V3**

ส่วนเสริมเหล่านี้เป็นส่วนเสริมที่ไม่บังคับ ดังนั้นหากต้องการรองรับวิดีโอ คุณต้องเพิ่มส่วนเสริมเหล่านี้ในอินสแตนซ์ด้วยตนเอง

การเล่นวิดีโอแบบเนทีฟยังต้องใช้ตัวเรนเดอร์ OpenGL ด้วย Watermedia จะไม่สามารถเล่นวิดีโอได้ขณะที่ Minecraft ใช้ Vulkan ให้เปลี่ยนไปใช้ OpenGL เพื่อใช้องค์ประกอบ Video, พื้นหลังเมนู Video และ [Game Intro ที่เป็นวิดีโอ](/game-intro)

ประเภท **Video [Rinku]** ที่เลิกใช้แล้ว ยังคงใช้ [Rinku](https://modrinth.com/mod/rinku) สำหรับเลย์เอาต์ใหม่ ให้ใช้ประเภท Video แบบเนทีฟที่ขับเคลื่อนด้วย Watermedia แทน

## วิดีโอในหน้าจอโหลด

วิดีโอไม่สามารถใช้งานได้ในหน้าจอโหลด (หน้าจอโหลดเกม/ทรัพยากร และหน้าจอโหลดโลก)

นั่นหมายความว่าคุณไม่ควรเพิ่มวิดีโอลงในหน้าจอโหลดเกมผ่าน **Drippy Loading Screen** เพราะโดยส่วนใหญ่แล้วจะใช้งานไม่ได้

ให้ใช้[แอนิเมชัน](/animations)สั้น ๆ และเรียบง่าย (APNG หรือ GIF) ในหน้าจอโหลดแทน

## การแก้ไขปัญหา

หากวิดีโอแบบเนทีฟไม่เล่น ให้ตรวจสอบว่า Watermedia V3 และ Watermedia Binaries V3 ตรงกับเวอร์ชัน Minecraft/ตัวโหลดม็อดที่คุณใช้ และ Minecraft กำลังใช้ OpenGL แทน Vulkan
