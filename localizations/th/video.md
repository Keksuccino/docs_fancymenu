---
title: วิดีโอ (MP4)
description: สิ่งที่ควรรู้เกี่ยวกับการใช้วิดีโอใน FancyMenu
sourceBlobSha: 2ec0bfe39528bb93095798f6a2a1cc7cbe17e5eb
---
# วิดีโอ

FancyMenu รองรับการเล่นวิดีโอ MP4 ในรูปแบบ[องค์ประกอบ](./elements#video) [พื้นหลังเมนู](./menu-backgrounds) และเนื้อหา [Game Intro](./game-intro)

[องค์ประกอบ **Video**](./elements#video) แบบเนทีฟและพื้นหลังเมนู **Video** ใช้ Watermedia V3 ส่วนประเภท **Video [Rinku]** แบบเก่าถูกยกเลิกการรองรับแล้ว และควรคงไว้เฉพาะในเลย์เอาต์ที่ยังจำเป็นต้องใช้เท่านั้น

นอกจากนี้ยังมี**การทำงาน**ต่อไปนี้สำหรับควบคุมพื้นหลังและองค์ประกอบวิดีโอ:

- [**Set Video Element Volume**](./action-scripts#set-video-element-volume-set_video_element_volume) ใช้ตั้งค่าระดับเสียงขององค์ประกอบ Video
- [**Set Video Element Play Time**](./action-scripts#set-video-element-play-time-set_video_element_play_time) ใช้เลื่อนไปยังเวลาที่ระบุในหน่วยมิลลิวินาทีขององค์ประกอบ Video
- [**Toggle Video Element Paused State**](./action-scripts#toggle-video-element-paused-state-toggle_video_element_pause_state) ใช้สลับสถานะหยุดชั่วคราวขององค์ประกอบ Video
- [**Set Video Background Volume**](./action-scripts#set-video-background-volume-set_video_menu_background_volume) ใช้ตั้งค่าระดับเสียงของพื้นหลังเมนู Video
- [**Set Video Background Play Time**](./action-scripts#set-video-background-play-time-set_video_menu_background_play_time) ใช้เลื่อนไปยังเวลาที่ระบุในหน่วยมิลลิวินาทีของพื้นหลังเมนู Video
- [**Toggle Video Background Paused State**](./action-scripts#toggle-video-background-paused-state-toggle_video_menu_background_pause_state) ใช้สลับสถานะหยุดชั่วคราวของพื้นหลังเมนู Video

และมี**ตัวแทนค่า**ต่อไปนี้สำหรับรับข้อมูลเกี่ยวกับพื้นหลังและองค์ประกอบวิดีโอ:

- [**Video Element Volume**](./placeholders#video-element-volume-video_element_vol) คืนค่าระดับเสียงขององค์ประกอบ Video
- [**Video Element Duration**](./placeholders#video-element-duration-video_element_duration) คืนค่าความยาวขององค์ประกอบ Video
- [**Video Element Play Time**](./placeholders#video-element-play-time-video_element_playtime) คืนค่าความคืบหน้าปัจจุบันขององค์ประกอบ Video
- [**Video Element Paused State**](./placeholders#video-element-paused-state-video_element_paused_state) คืนค่าว่าองค์ประกอบ Video หยุดชั่วคราวอยู่หรือไม่
- [**Video Background Volume**](./placeholders#video-background-volume-video_background_vol) คืนค่าระดับเสียงของพื้นหลังเมนู Video
- [**Video Background Duration**](./placeholders#video-background-duration-video_background_duration) คืนค่าความยาวของพื้นหลังเมนู Video
- [**Video Background Play Time**](./placeholders#video-background-play-time-video_background_playtime) คืนค่าความคืบหน้าปัจจุบันของพื้นหลังเมนู Video
- [**Video Background Paused State**](./placeholders#video-background-paused-state-video_background_paused_state) คืนค่าว่าพื้นหลังเมนู Video หยุดชั่วคราวอยู่หรือไม่

ตัวแทนค่าความยาวและเวลาเล่นจะแสดงผลเป็น `MM:SS` ตามค่าเริ่มต้น ตั้งค่า `output_as_timestamp` เป็น `true` เมื่อต้องการเวลาในหน่วยมิลลิวินาที ตัวแทนค่าเวลาเล่นยังสามารถใช้ `show_percentage` เพื่อแสดงค่าความคืบหน้า 0-100 ได้

ค่าระดับเสียงและสถานะหยุดชั่วคราวเป็นข้อมูลเมทาดาทาของตัวควบคุมที่เชื่อมโยงกับตัวระบุ ส่วนค่าความยาวและเวลาเล่นจำเป็นต้องมีองค์ประกอบ Video หรือพื้นหลังที่ตรงกันกำลังทำงานและพร้อมใช้งานบนหน้าจอปัจจุบัน

[ตัวรับฟัง **On Video Playback Status Changed**](./listeners#on-video-playback-status-changed-video_playback_status_changed) สามารถตอบสนองต่อสถานะ `PLAYING`, `PAUSED`, `STOPPED` และ `FINISHED` ได้

## ข้อกำหนด

หากต้องการใช้ประเภทองค์ประกอบ Video และพื้นหลังเมนูแบบเนทีฟใหม่ คุณต้องติดตั้ง:

- **Watermedia V3**
- **Watermedia Binaries V3**

ส่วนเสริมเหล่านี้เป็นการพึ่งพาที่ไม่บังคับ ดังนั้นคุณต้องเพิ่มลงในอินสแตนซ์ด้วยตนเองหากต้องการรองรับวิดีโอ

การเล่นวิดีโอแบบเนทีฟยังจำเป็นต้องใช้ตัวเรนเดอร์ OpenGL ด้วย ไม่สามารถใช้การเล่นผ่าน Watermedia ขณะที่ Minecraft ใช้ Vulkan ได้ ให้เปลี่ยนไปใช้ OpenGL เพื่อใช้งานองค์ประกอบ Video พื้นหลังเมนู Video และ [Game Intro ที่เป็นวิดีโอ](./game-intro)

ประเภท **Video [Rinku]** ที่เลิกใช้งานแล้ว ยังคงใช้ [Rinku](https://modrinth.com/mod/rinku) สำหรับเลย์เอาต์ใหม่ ให้ใช้ประเภท Video แบบเนทีฟที่ขับเคลื่อนด้วย Watermedia แทน

## วิดีโอในหน้าจอโหลด

การรองรับวิดีโอไม่ทำงานในหน้าจอโหลด (หน้าจอโหลดเกม/ทรัพยากรและหน้าจอโหลดโลก)

ซึ่งหมายความว่าคุณไม่ควรเพิ่มวิดีโอลงในหน้าจอโหลดเกมผ่าน **Drippy Loading Screen** เนื่องจากในกรณีส่วนใหญ่จะไม่ทำงาน

ให้ใช้[แอนิเมชัน AFMA/FMA](./fma) ที่สั้นและเรียบง่ายในหน้าจอโหลดแทน

## การแก้ไขปัญหา

หากวิดีโอแบบเนทีฟไม่เล่น ให้ตรวจสอบว่า Watermedia V3 และ Watermedia Binaries V3 ตรงกับเวอร์ชัน Minecraft/ม็อดโหลดเดอร์ของคุณ และ Minecraft กำลังใช้ OpenGL แทน Vulkan
