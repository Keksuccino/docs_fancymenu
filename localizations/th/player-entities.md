---
title: เอนทิตีผู้เล่น
description: >-
  แสดงผู้เล่นในเมนูด้วยองค์ประกอบ Player Entity พร้อมสกิน ชื่อ ท่าทาง ชุดเกราะ
  และอื่น ๆ
sourceBlobSha: b8f8d4340ca3a87e1c55c86f95f36786ab840644
---

# เอนทิตีผู้เล่น

องค์ประกอบ Player Entity แสดงผู้เล่นในรูปแบบ 3 มิติ คล้ายกับตัวละครของผู้เล่นที่อยู่ข้างปุ่มบนหน้าจอไตเติล โดยสามารถจำลองผู้เล่นที่กำลังเล่น แสดงผู้เล่นคนอื่น หรือเป็นตัวละครที่คุณสร้างขึ้นเองพร้อมสกิน ผ้าคลุม และชื่อของตัวเองก็ได้

<img width="800" alt="Player Entity ห้าตัว: ผู้เล่นจริงพร้อมสกินและผ้าคลุม ตัวหนึ่งสวมชุดเกราะเพชรติดมนตร์พร้อมดาบและโล่ ตัวหนึ่งกำลังย่อตัว ตัวหนึ่งกำลังโบกมือ และอีกตัวเป็นเด็ก" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/player_entities_showcase.png?raw=true">

> [!IMPORTANT]
> ใน Minecraft 1.20.1 ขึ้นไป Player Entity ต้องใช้ม็อด Fancy Entity Renderer ([CurseForge](https://www.curseforge.com/minecraft/mc-mods/fancy-entity-renderer), [Modrinth](https://modrinth.com/mod/fancy-entity-renderer)) หากไม่มีม็อดนี้ จะแสดงเป็นกรอบสีแดง หากยังไม่มีเวอร์ชันของม็อดสำหรับ Minecraft เวอร์ชันที่คุณใช้ ก็จะไม่สามารถแสดง Player Entity ได้

# เพิ่ม Player Entity

คลิกขวาที่พื้นหลังของตัวแก้ไข แล้วคลิก **New Element -> Player Entity** ลากจุดจับเพื่อเปลี่ยนขนาด ความสูงขององค์ประกอบจะเป็นตัวกำหนดขนาดของผู้เล่น

การตั้งค่าทั้งหมดด้านล่างอยู่ในเมนูคลิกขวาขององค์ประกอบ

# สิ่งที่จะแสดง

- **Copy Client Player** แสดงผู้เล่นที่กำลังเล่น พร้อมชื่อ สกิน และผ้าคลุม เมื่อเปิดใช้งาน การตั้งค่าชื่อ สกิน และผ้าคลุมจะถูกล็อก
- **Player Name** กำหนดเป็นชื่อใดก็ได้ ไม่จำเป็นต้องเป็นชื่อของผู้เล่นจริง รองรับ [ตัวแปรแทน](/placeholders)
- **Show Player Name** แสดงป้ายชื่อเหนือศีรษะ หากปิด **Nametag Rotation** ป้ายชื่อจะไม่หมุนตามผู้เล่น

## สกินและผ้าคลุม

- **Auto Skin** และ **Auto Cape** โหลดสกินและผ้าคลุมของผู้เล่นที่ระบุไว้ใน **Player Name** ซึ่งต้องเชื่อมต่ออินเทอร์เน็ต
- **Skin Texture** และ **Cape Texture** ใช้ไฟล์สกินและผ้าคลุมของคุณเอง เช่น สกินจาก [ทรัพยากรของคุณ](/resources) สกินต้องเป็นไฟล์สกินมาตรฐานของ Minecraft
- **Slim Skin** ใช้กับสกินที่มีแขนเรียว เช่น Alex ส่วน **Auto Skin** และ **Copy Client Player** จะตรวจหาให้อัตโนมัติ

# ท่าทางและการเคลื่อนไหว

<img width="800" alt="Player Entity สองตัวมองตามตัวชี้เมาส์ที่เคลื่อนที่ไปรอบ ๆ: ตัวซ้ายหันเฉพาะศีรษะ ส่วนตัวขวาหันทั้งศีรษะและลำตัว" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/player_entities_follow_mouse.gif?raw=true">

- **Head Follows Mouse** และ **Body Follows Mouse** ทำให้ผู้เล่นมองตามตัวชี้เมาส์ โดยค่าเริ่มต้นของ Player Entity ใหม่จะเปิดทั้งสองตัวเลือก
- **Pose** ใช้เลือกท่าทางของร่างกาย ได้แก่ **Standing**, **Crouching**, **Sleeping**, **Swimming**, **Dying** หรือ **Spin Attack**
- **Body Movement** ทำให้ท่าทางเคลื่อนไหว

## ท่าทางเอนทิตี

**Entity Pose** เปิดหน้าต่างที่มีการหมุนแกน X, Y และ Z ของ **Head**, **Body**, **Left Arm**, **Right Arm**, **Left Leg** และ **Right Leg** ตั้งแต่ `-180` ถึง `180`

<img width="800" alt="หน้าต่าง Entity Pose พร้อมแถบเลื่อนปรับการหมุนศีรษะและลำตัวของผู้เล่น" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/player_entities_pose_window.png?raw=true">

**Advanced Mode** ที่อยู่ข้างแถบเลื่อนจะเปลี่ยนค่าเป็นช่องข้อความที่รองรับ [ตัวแปรแทน](/placeholders) หากใส่ [ตัวแปร](/variables) เช่น `$$arm_angle` ไว้ในช่องนั้น ก็สามารถใช้ [Scheduler](/schedulers) ทำให้ผู้เล่นเคลื่อนไหวได้ด้วยการเปลี่ยนค่าตัวแปร

# ชุดเกราะ ไอเทม และอื่น ๆ

- **Armor and Tools** ใส่ไอเทมให้ผู้เล่น ได้แก่ **Head Armor**, **Chest Armor**, **Legs Armor**, **Feet Armor**, **Left Hand Tool** และ **Right Hand Tool** กำหนดเป็น ID ของไอเทม เช่น `minecraft:diamond_sword` โดย ID ของไอเทมรองรับตัวแปรแทน ตัวเลือก **Enchant Head Armor** และสวิตช์ Enchant อื่น ๆ จะเพิ่มประกายแวววาวของการร่ายมนตร์
- **Is Baby** ทำให้ผู้เล่นมีขนาดเล็กเหมือนเด็ก
- **Parrot** วางนกแก้วไว้บนไหล่ขวา หรือวางไว้บนไหล่ซ้ายเมื่อเปิด **Parrot On Left Shoulder**

# ข้อควรรู้

- Player Entity ไม่สามารถหมุน เอียง ทำให้จาง หรือทำให้โปร่งใสได้
- หากต้องการแสดงเฉพาะศีรษะของผู้เล่น โปรดดู [หัวผู้เล่น](/player-heads)
- ใน Minecraft 1.19.2 ไม่จำเป็นต้องใช้ Fancy Entity Renderer กับ Player Entity แต่จะมีการตั้งค่าน้อยกว่า ได้แก่ ใช้ **Crouching** แทน **Pose** และไม่มี **Nametag Rotation**, **Body Movement** หรือ **Armor and Tools** ขนาดจะกำหนดจาก **Entity Scale** (ค่าเริ่มต้นคือ `30` ดังนั้น `60` จะมีขนาดใหญ่เป็นสองเท่า) แทนการกำหนดจากขนาดขององค์ประกอบ
